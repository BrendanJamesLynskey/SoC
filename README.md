# 🔐 Modern Cryptography Presentation Series

Interactive slide decks covering modern cryptographic systems end-to-end — from the underlying mathematics through NIST standards to SystemVerilog RTL and Python implementations.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/Cryptography/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory), then replace `OWNER` and `REPO` in the link above with your GitHub username and repository name.
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
| --- | --- | --- | --- |
| 01 | Finite Field Arithmetic for Cryptography | 16 | ✅ Complete |
| 02 | Elliptic Curve Cryptography (ECC) | 38 | ✅ Complete |
| 03 | AES — Design & Implementation | 28 | ✅ Complete |
| 06 | Digital Signatures (ECDSA, EdDSA, Schnorr) | 25 | ✅ Complete |
| 07 | Post-Quantum Cryptography | 21 | ✅ Complete |
| 09 | Side-Channel Attacks & Countermeasures | 22 | ✅ Complete |
| 10 | Crypto Hardware Accelerator Design | 38 | ✅ Complete |



---

## Presentation 01: Finite Field Arithmetic

16 interactive slides covering:

**Theory** — Group → Ring → Field → Finite Field progression. GF(p) prime fields with GF(7) worked examples. GF(2ⁿ) binary extension fields with AES polynomial arithmetic.

**Standards** — Which fields are used in AES, AES-GCM, NIST P-256, Curve25519, Curve448, and SM2 — and the engineering reasons behind each choice.

**Hardware** — SoC/ASIC composite field decomposition, FPGA LUT and Canright S-box designs, Montgomery multiplication with four architecture variants (bit-serial through full-parallel systolic array).

**Code** — Complete SystemVerilog GF(2⁸) multiplier, parameterized modular add/subtract modules, Python GF(2⁸) and GF(p) classes with Fermat inverse.

**Performance** — Throughput comparison from 3.2 Gbps (OpenSSL) to 53 Gbps (45nm ASIC), with area/speed/side-channel trade-off analysis.

---

## Presentation 02: Elliptic Curve Cryptography

38 interactive slides covering:

**Foundations** — Elliptic curves over ℝ with geometric intuition: the chord-and-tangent group law for point addition and doubling. Algebraic addition formulas with detailed derivation. The point at infinity as identity element. Non-singularity condition and discriminant.

**Curves over Finite Fields** — Transition from ℝ to 𝔽ₚ with Hasse's theorem bounding group order. The Elliptic Curve Discrete Logarithm Problem (ECDLP) and why it provides a trapdoor. Security level analysis: 256-bit curve → 128-bit security via Pollard's ρ.

**Scalar Multiplication** — Binary double-and-add (left-to-right), Non-Adjacent Form (NAF) with density 1/3, windowed w-NAF with precomputation. The Montgomery ladder for constant-time, SPA-resistant computation using x-only differential addition.

**Curve Forms** — Short Weierstrass (y² = x³ + ax + b): NIST P-curves, Jacobian/projective coordinates, a = −3 optimization, incomplete addition formulas and the Renes-Costello-Batina 2016 complete formulas. Montgomery curves (Bv² = u³ + Au² + u): x-only arithmetic, differential addition, Curve25519 and Curve448. Twisted Edwards curves (ax² + y² = 1 + dx²y²): complete addition law when d is non-square, unified add/double, extended coordinates, edwards25519. Birational equivalence maps between all three forms.

**Coordinate Systems** — Six systems compared: affine, projective, Jacobian, extended Edwards, Montgomery x-only, Co-Z. Operation counts (M, S, I) for each. Strategy: projective throughout, single final inversion.

**Standards** — NIST P-256/P-384/P-521, Curve25519/Curve448, edwards25519/edwards448, secp256k1, BrainpoolP256r1. NIST SP 800-186 (2023), FIPS 186-5, RFC 7748, RFC 8032. Curve25519 design rationale: prime shape (2²⁵⁵ − 19), scalar clamping, twist security, minimal A = 486662.

**Protocols** — ECDH key agreement with worked Alice–Bob flow for both X25519 (RFC 7748) and NIST P-256 (with validation requirements). ECDSA signing and verification with full mathematical walkthrough, nonce criticality, and RFC 6979 deterministic variant. EdDSA/Ed25519 (RFC 8032): deterministic Schnorr-type signatures, cofactored verification, comparison table vs ECDSA across 8 properties.

**Attacks & Security** — Eight attack classes: Baby-Step Giant-Step, Pollard's ρ, Pohlig-Hellman (smooth order), MOV/Frey-Rück (low embedding degree), Smart's anomalous attack (#E = p), invalid curve attacks, small subgroup attacks, Shor's quantum algorithm. SafeCurves criteria (Bernstein & Lange). Real-world failures: Sony PS3 nonce reuse (2010), Android Bitcoin wallet RNG (2013), Minerva timing (2019), Dual_EC_DRBG NSA backdoor (2013).

**Hardware** — Three-level accelerator hierarchy (scalar mult → point ops → modular arithmetic → big-integer). Montgomery modular multiplication algorithm and four hardware variants (bit-serial to full-parallel). FPGA results: P-256 from 5.26 ms (Virtex-5) to 0.56 ms (Virtex-7, 23.7k LUTs). ASIC results: unified Curve25519+Curve448 at 28nm (1096 kGE, 0.43 ms), low-power Curve25519 at 65nm (49 kGE). Side-channel countermeasure table: scalar blinding, point blinding, projective coordinate randomization, constant-time operations, fault detection.

**Code** — SystemVerilog Montgomery modular multiplier (parameterized N-bit). Jacobian point addition scheduler with FSM and parallel multiplier scheduling. Python ECDH on a toy curve (y² = x³ + 2x + 3 mod 97) with complete point arithmetic.

**Interactive** — Canvas-based point visualizer for E(𝔽₉₇) with click-to-select addition and doubling. Scalar multiplication kG slider showing trail of intermediate points with binary decomposition. Animated group law illustration cycling through addition, doubling, and inversion. All 100 curve points enumerated.

**Deployment** — ECC in TLS 1.3 (X25519 key exchange + Ed25519 signatures), SSH, Bitcoin/Ethereum (secp256k1), Signal/WhatsApp, WireGuard, FIDO2/Passkeys, Tor, smart cards, IoT. ECC vs RSA performance comparison at 128-bit security. Quantum threat: Shor's algorithm resource estimates, CNSA 2.0 timeline, hybrid X25519+ML-KEM-768 transition.

---

## Presentation 03: AES — Design & Implementation

28 interactive slides covering:

**Theory** — GF(2⁸) arithmetic recap with xtime(). S-box two-step construction (multiplicative inverse + affine transformation over GF(2)). Complete 16×16 S-box lookup table. ShiftRows with visual before/after state grids. MixColumns MDS matrix with branch number = 5 analysis. AddRoundKey.

**Standards** — Historical context from DES through the AES competition to FIPS 197. Key schedule for all three variants (128/192/256-bit) with RotWord, SubWord, and Rcon. Round structure pseudocode. Decryption via equivalent inverse cipher.

**Implementation** — T-table optimisation fusing SubBytes + ShiftRows + MixColumns into four 256-entry 32-bit tables. AES-NI hardware instruction set (AESENC, AESDEC, AESKEYGENASSIST). Python AES-128 reference implementation. SystemVerilog AES round module with 16 parallel S-box instances.

**Hardware** — Three architecture tiers: basic iterative (3–5 kGE), inner-round pipelined (8–15 kGE), fully unrolled + pipelined (50–170 kGE). Composite-field S-box via GF((2⁴)²) tower decomposition (Canright's 92 GE design). FPGA vs ASIC comparison. Performance from 80 Mbps (8-bit serial) to 53 Gbps (45nm ASIC).

**Security** — Side-channel attack taxonomy: timing (Bernstein 2005), DPA/CPA (Kocher 1999), differential fault analysis. Countermeasures: Boolean masking (d+1 shares), shuffling, bitslicing, dual-rail logic, threshold implementations, TMR. Cryptanalysis status: biclique (2¹²⁶·¹), related-key, Square attacks. Post-quantum: Grover's algorithm and CNSA 2.0 AES-256 mandate.

**Deployment** — Modes of operation (ECB, CBC, CTR, GCM, XTS, CCM, SIV). Real-world usage: TLS 1.3, IPsec, BitLocker, FileVault, WPA3, Intel AES-NI, ARM Crypto Extensions, RISC-V Zkn.

---

## Presentation 06: Digital Signatures

25 interactive slides covering:

**Theory** — Hash-then-sign paradigm, authentication/integrity/non-repudiation properties. The ElGamal → DSA → ECDSA → Schnorr → EdDSA family tree. Full mathematical walkthroughs of ECDSA signing/verification with correctness proofs.

**Schemes** — ECDSA deep dive (key generation, signing, verification, deterministic RFC 6979 variant). Schnorr signatures with linearity and batch verification. EdDSA/Ed25519 with deterministic nonces and twisted Edwards curve parameters. Side-by-side comparison table across all three schemes.

**Advanced Protocols** — MuSig2 (n-of-n) and FROST (t-of-n) threshold signatures. Blind and ring signatures overview.

**Standards** — FIPS 186-5 (2023), RFC 8032 (Ed25519/Ed448), RFC 6979 (deterministic ECDSA), BIP 340 (Schnorr for Bitcoin Taproot), FIPS 204 (ML-DSA), FIPS 205 (SLH-DSA). Real-world deployment map: TLS 1.3, blockchain, SSH, mobile/IoT, code signing, PKI.

**Hardware** — ECDSA/EdDSA FPGA accelerator block diagrams and synthesis results (Virtex-5, Alveo U250). ASIC 45nm implementation data (0.257 mm², 532 MHz). Side-channel attack taxonomy (SPA, DPA, EM, fault injection) and countermeasures (Montgomery ladder, scalar blinding, coordinate randomization).

**Post-Quantum** — ML-DSA (CRYSTALS-Dilithium) and SLH-DSA (SPHINCS+) parameter sets, size comparisons, hardware accelerator results. Hybrid transition strategies.

**Code** — Python Ed25519 and ECDSA P-256 implementations. SystemVerilog modular inverse module (Fermat's little theorem via Montgomery exponentiation). ECDSA sign top-level RTL with FSM controller.

**Interactive** — Live ECDSA signing simulator on a toy elliptic curve with sign, verify, and tamper-detection demonstrations.

**Attacks** — Sony PS3 nonce-reuse (2010), Android Bitcoin wallet RNG failure (2013), ROCA TPM vulnerability (2017), Minerva timing side-channel (2019).

---

## Presentation 07: Post-Quantum Cryptography

21 interactive slides covering:

**The Quantum Threat** — Shor's algorithm breaking RSA/ECC/DH in polynomial time. Grover's quadratic speedup against symmetric ciphers. The "Harvest Now, Decrypt Later" attack model. CRQC timeline estimates and CNSA 2.0 mandates.

**Lattice Mathematics** — Interactive 2D lattice visualisation with Closest Vector Problem demo. SVP, CVP, SIVP, GapSVP hard problems. Learning With Errors (LWE): search vs. decision variants, worst-case to average-case reductions (Regev 2005). Ring-LWE and Module-LWE structured variants. Interactive noise parameter demo showing why error makes LWE hard.

**NIST PQC Standards (Aug 2024)** — FIPS 203 (ML-KEM), FIPS 204 (ML-DSA), FIPS 205 (SLH-DSA). Upcoming: FIPS 206 (FN-DSA/FALCON), HQC (code-based KEM backup). NIST IR 8547 deprecation timeline (2035).

**ML-KEM Deep Dive** — Module-LWE construction: K-PKE → Fujisaki-Okamoto transform → IND-CCA2. Full protocol flow diagram (Alice/Bob key exchange). NTT butterfly architecture and ℤ₃₃₂₉ arithmetic. Parameter sets: ML-KEM-512/-768/-1024 with key/ciphertext sizes.

**ML-DSA Deep Dive** — Fiat-Shamir with Aborts paradigm (Lyubashevsky). Module-LWE + Module-SIS security basis. Parameter sets and abort loop mechanics.

**SLH-DSA (SPHINCS+)** — Hypertree architecture: WOTS+ → XMSS → FORS layers. 12 parameter sets across SHA-2/SHAKE, small/fast modes. Conservative hash-only security assumptions.

**Interactive Comparisons** — Switchable bar charts comparing public key, secret key, and ciphertext/signature sizes across all PQC and classical algorithms. Performance benchmarks: ML-KEM vs. X25519 vs. RSA-2048; ML-DSA vs. Ed25519.

**Hardware** — NTT butterfly architectures for ML-KEM/ML-DSA: iterative, pipelined, mixed-radix. Keccak/SHA-3 core integration. FPGA and ASIC implementation results with area-time product comparisons. PQC + RISC-V integration strategies.

**Migration** — Hybrid key exchange (X25519 + ML-KEM-768 in TLS 1.3). Certificate chain impacts. CNSA 2.0 timeline and backward compatibility challenges.

---

## Presentation 09: Side-Channel Attacks & Countermeasures

22 interactive slides covering:

**Timing Attacks** — Kocher's 1996 timing attack fundamentals. Vulnerable vs. constant-time string comparison in C. Constant-time conditional select with branchless bitwise arithmetic. Rules for constant-time cryptographic code. The compiler optimisation problem and verification tools (ct-verif, dudect, timecop, Binsec/Rel).

**Power Analysis** — CMOS dynamic power and the Hamming weight/distance models. Simple Power Analysis (SPA) with interactive RSA square-and-multiply trace visualisation. Differential Power Analysis (DPA) and Correlation Power Analysis (CPA) with animated correlation convergence demo. Template attacks and deep-learning SCA extensions (X-DeepSCA, cross-device single-trace attacks).

**Electromagnetic Emanations** — Near-field EM probes, SEMA/DEMA/CEMA techniques. STELLAR countermeasure for lower-metal routing and current-domain signature attenuation (CDSA). Advantages over power analysis: spatial resolution, non-contact measurement, bypass of decoupling capacitors.

**Cache & Microarchitectural Attacks** — AES T-table cache timing (Bernstein 2005). Flush+Reload, Prime+Probe, Evict+Time techniques. Spectre (Variant 1 bounds-check bypass, Variant 2 branch-target injection) and Meltdown (out-of-order execution, delayed exception handling). KPTI, retpoline, IBRS/IBPB, and DAWG mitigations.

**Fault Injection** — Voltage glitching, clock glitching, EM fault injection, laser FI, and RowHammer with cost/practicality comparison. Differential Fault Analysis (DFA) on AES (Piret-Quisquater, 4 faults for full key) and RSA-CRT (Bellcore attack, single faulty signature). Software and hardware countermeasures including redundant computation, infection, and environmental sensors.

**Countermeasures** — Boolean and arithmetic masking with Python masked-SubBytes example. Threshold Implementations (TI) with SystemVerilog AND-gate example and correctness/non-completeness/uniformity properties. DOM, HPC2/PINI, and AGEMA evolution. Hiding techniques: dual-rail logic (WDDL, SABL), shuffling, random delays, physical shielding with active mesh. Constant-time programming in practice (libsodium, BoringSSL, AES-NI). TVLA methodology with interactive t-test visualisation. RSA blinding, ECC scalar/point/projective coordinate blinding. Hardware-level SAH, on-die voltage regulators, active shield mesh, environmental sensors.

**Cost of Protection** — Area (gate equivalents), throughput, randomness per encryption, and traces-to-break comparison table for unprotected vs. TI vs. DOM vs. shuffling+mask vs. SAH AES-128 implementations.

**Case Studies** — EMV smart cards (DPA on DES/3DES), OpenSSL RSA cache timing (Bernstein/Percival 2005), TEMPEST/Van Eck phreaking, Spectre/Meltdown (2018), Plundervolt/VoltPillager (2019–21), ROCA Infineon TPM (2017). Defense-in-depth layered protection strategy across algorithm, software, hardware, and physical layers.

**Interactive Demos** — SPA power trace canvas showing RSA key bit recovery from square/multiply amplitude patterns. Animated CPA correlation convergence showing correct key hypothesis separating from wrong guesses as trace count increases. TVLA t-test visualisation with ±4.5 threshold lines and leakage spike detection.

---

## Presentation 10: Crypto Hardware Accelerator Design

38 interactive slides covering:

**Symmetric Engines** — AES round architecture from iterative (2,645 GE, 94 Mbps) to fully pipelined (742 Gbps multi-core FPGA). S-Box implementation via composite field tower decomposition (Canright), Boyar-Peralta logic minimization, and threshold implementation for DPA resistance. AES-GCM authenticated encryption with GF(2¹²⁸) GHASH unit architectures. SHA-3/Keccak hardware achieving 36.4 Gbps on Virtex-7 with unrolled round optimization.

**Asymmetric / PKC Engines** — RSA Montgomery multiplication hardware in four variants: bit-serial, word-serial (DSP48E1), systolic array, and full-parallel. ECC scalar multiplication hierarchy from modular arithmetic through point operations to full scalar multiply. Edwards25519 FPGA implementation with unified point add/double achieving 1.4 ms per operation.

**Post-Quantum Hardware** — NIST PQC standards (FIPS 203/204/205) and their hardware bottlenecks. NTT butterfly architecture deep dive covering Cooley-Tukey and Gentleman-Sande formulations. NTT hardware architectures: iterative, Multi-Delay Commutator (MDC), Single-path Delay Feedback (SDF), and mixed-radix. Unified Kyber+Dilithium accelerators sharing NTT and Keccak datapaths. PQC SoC integration with RISC-V via bus-attached accelerators and instruction set extensions.

**Side-Channel Defense** — Taxonomy of power analysis (SPA/DPA/CPA/HO-DPA), electromagnetic, timing, and fault-injection attacks. Hardware countermeasures: Boolean masking, threshold implementation (TI) with correctness/non-completeness/uniformity properties, dual-rail logic (WDDL), random shuffling, blinding, EM shielding, and voltage/clock monitors. TVLA validation methodology — Rambus DPA-resistant cores validated to 100M+ traces.

**RTL Examples** — Complete SystemVerilog implementations of AES round logic with 16 parallel composite-field S-Boxes, the Canright tower-field S-Box decomposition (GF(2⁸) → GF(((2²)²)²)), NTT Cooley-Tukey butterfly for ML-KEM, and multiplier-less Montgomery reduction exploiting Kyber's q=3329 structure.

**Implementation Platforms** — ASIC vs. FPGA trade-off analysis across performance, area, power, flexibility, and certification. Crypto instruction set extensions (x86 AES-NI, AArch64, RISC-V Zkn/Zks). Protocol-level offload engines for IPsec, MACsec, and TLS. Complete design flow from algorithm analysis through FIPS 140-3 / Common Criteria certification.

**Performance Benchmarks** — Comparative tables spanning AES implementations (2,645 GE to 742 Gbps), PQC NTT accelerators with area-time product improvements up to 82%, and FALCON ASIC achieving 5.2K signatures/sec at 28 nm.

**Future Directions** — Crypto agility for PQC migration, FHE accelerators (FAB: 456× CPU speedup), ZK-proof hardware, and the convergence of NTT as shared IP across PQC/FHE/ZK applications.

---

## Repository Structure

```
├── index.html                                    ← Landing page (links to all presentations)
├── README.md                                     ← This file
├── 01-finite-field-arithmetic/
│   └── index.html                                ← Reveal.js interactive slide deck
├── 02-elliptic-curve-cryptography/
│   └── index.html                                ← Reveal.js interactive slide deck
├── 03-aes-design-implementation/
│   └── index.html                                ← Reveal.js interactive slide deck
├── 06-digital-signatures/
│   └── index.html                                ← Reveal.js interactive slide deck
├── 07-post-quantum-cryptography/
│   └── index.html                                ← Reveal.js interactive slide deck
├── 09-side-channel-attacks/
│   └── index.html                                ← Reveal.js interactive slide deck
└── 10-crypto-hardware-accelerator-design/
    └── index.html                                ← Reveal.js interactive slide deck
```

Each presentation is a single self-contained `index.html`. No build step, no npm — just HTML/CSS/JS with CDN-hosted Reveal.js and Google Fonts.

## Slide Controls

| Action | Key |
| --- | --- |
| Next / Previous | `→` `←` or swipe |
| Overview | `Esc` |
| Fullscreen | `F` |
| Export to PDF | append `?print-pdf` to URL |

## Technology

[Reveal.js 4.6](https://revealjs.com) · [highlight.js](https://highlightjs.org) (Monokai) · Playfair Display + DM Sans + JetBrains Mono

## References

**Presentation 01:** FIPS 197 (AES) · NIST SP 800-186 (ECC Curves) · RFC 7748 (Curve25519/448) · FIPS 186-5 (DSS) · Canright, "A Very Compact Rijndael S-box" (2005) · Kleppmann, "Implementing Curve25519/X25519" (2020) · Koç et al., "Finite Field Arithmetic for Cryptography," IEEE (2010)

**Presentation 02:** FIPS 186-5 (DSS) · NIST SP 800-186 (ECC Curves, 2023) · RFC 7748 (X25519/X448) · RFC 8032 (EdDSA) · RFC 6979 (Deterministic ECDSA) · SEC 2 (SECG Curves) · RFC 5639 (Brainpool) · Koblitz, "Elliptic Curve Cryptosystems" (1987) · Miller, "Use of Elliptic Curves in Cryptography" (CRYPTO 1985) · Montgomery, "Speeding the Pollard and EC Methods of Factorization" (1987) · Edwards, "A Normal Form for Elliptic Curves" (2007) · Bernstein, "Curve25519: New Diffie-Hellman Speed Records" (2006) · Bernstein & Lange, "Faster Addition and Doubling on Elliptic Curves" (ASIACRYPT 2007) · Renes, Costello, Batina, "Complete Addition Formulas for Prime Order Elliptic Curves" (2016) · Bernstein & Lange, "Montgomery Curves and the Montgomery Ladder" (2017) · Hankerson, Menezes, Vanstone, "Guide to Elliptic Curve Cryptography" (Springer, 2004) · Pohlig & Hellman (1978) · Pollard, "Monte Carlo Methods for Index Computation" (1978) · Smart, "The Discrete Logarithm Problem on Elliptic Curves of Trace One" (1999) · Menezes, Okamoto, Vanstone, "Reducing ECDLP to DLP over Extension Fields" (1993)

**Presentation 03:** FIPS 197 (AES) · Daemen & Rijmen, "The Design of Rijndael" (Springer, 2002) · Canright, "A Very Compact Rijndael S-box" (CHES 2005) · Mathew et al., "53 Gbps AES in 45nm" IEEE JSSC (2011) · Bogdanov et al., "Biclique Cryptanalysis of AES" (ASIACRYPT 2011) · Biryukov & Khovratovich, "Related-Key Attacks on AES-256" (CRYPTO 2009) · Bernstein, "Cache-Timing Attacks on AES" (2005) · Kocher, Jaffe & Jun, "Differential Power Analysis" (CRYPTO 1999) · Gaj & Chodowiec, "FPGA and ASIC Implementations of AES" (2009) · NIST SP 800-38A (Modes of Operation) · NIST SP 800-38D (GCM) · Intel AES-NI White Paper (2010)

**Presentation 06:** FIPS 186-5 (DSS) · FIPS 204 (ML-DSA) · FIPS 205 (SLH-DSA) · NIST SP 800-186 (ECC Curves) · RFC 6979 (Deterministic ECDSA) · RFC 8032 (EdDSA) · BIP 340 (Schnorr) · Johnson, Menezes, Vanstone, "The ECDSA" (2001) · Bernstein et al., "High-speed high-security signatures" (2011)

**Presentation 07:** FIPS 203 (ML-KEM) · FIPS 204 (ML-DSA) · FIPS 205 (SLH-DSA) · NIST IR 8547 (PQC Transition) · SP 800-208 (LMS/XMSS) · Shor, "Polynomial-Time Algorithms for Prime Factorization" (1994) · Regev, "On Lattices, Learning with Errors" (2005) · Lyubashevsky, Peikert, Regev, "On Ideal Lattices and RLWE" (2010) · Bos et al., "CRYSTALS-Kyber" (2018) · Ducas et al., "CRYSTALS-Dilithium" (2018) · Bernstein et al., "The SPHINCS+ Signature Framework" (2019)

**Presentation 09:** Kocher, "Timing Attacks on Implementations of DH, RSA, DSS" (1996) · Kocher, Jaffe & Jun, "Differential Power Analysis" (CRYPTO 1999) · Chari, Rao & Rohatgi, "Template Attacks" (CHES 2002) · Biham & Shamir, "Differential Fault Analysis" (1997) · Boneh, DeMillo & Lipton, "On the Importance of Checking Cryptographic Protocols for Faults" (1997) · Piret & Quisquater, "A DFA Technique Against SPN Structures" (2003) · Bernstein, "Cache-Timing Attacks on AES" (2005) · Kocher et al., "Spectre Attacks" (2018) · Lipp et al., "Meltdown" (2018) · Nikova, Rechberger & Rijmen, "Threshold Implementations" (2006) · ISW, "Private Circuits: Securing Hardware Against Probing Attacks" (2003) · Das & Sen, "EM and Power SCA: Advanced Attacks and Low-Overhead Countermeasures" (2020) · Schneider, Moradi & Güneysu, "Arithmetic Addition over Boolean Masking" (2015) · Goodwill et al., "TVLA — A Testing Methodology for SCA Resistance" (2011) · NIST SP 800-90B · FIPS 140-3 · Common Criteria ISO/IEC 15408

**Presentation 10:** FIPS 197 (AES) · FIPS 202 (SHA-3) · FIPS 203 (ML-KEM) · FIPS 204 (ML-DSA) · FIPS 205 (SLH-DSA) · FIPS 140-3 (Crypto Module Security) · Canright, "A Very Compact Rijndael S-box" (CHES 2005) · Boyar & Peralta, "New Logic Minimization Techniques" (2010) · Kocher, Jaffe & Jun, "Differential Power Analysis" (CRYPTO 1999) · Montgomery, "Modular Multiplication Without Trial Division" (1985) · Hasan, "53 Gbps Composite-Field AES" (JSSC 2011) · Ouyang et al., "FalconSign" (TCHES 2025)

## License

Educational use. Code examples provided as-is. Standards references are to publicly available NIST, IETF, and ISO documents.
