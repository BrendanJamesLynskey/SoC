# ⬡ Modern SoC Design Presentation Series

Interactive slide decks covering modern System-on-Chip design end-to-end — from advanced packaging and chiplet architectures through memory hierarchies, on-chip interconnects, and silicon implementation.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/SoC/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory).
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
|---|-------|--------|--------|
| 01 | Modern SoC Packaging | 18 | ✅ Complete |
| 02 | On-Chip Interconnect & NoC Design | 20 | ✅ Complete |
| 03 | Memory Hierarchy in ML Accelerator SoCs | 23 | ✅ Complete |
| 04 | High-Speed SerDes & I/O | 23 | ✅ Complete |
| 05 | AI / ML Accelerator Architectures | 22 | ✅ Complete |
| 06 | SoCs for ML Inference | 24 | ✅ Complete |
| 07 | Security in SoC Design | 22 | ✅ Complete |
| 08 | CXL in ML Accelerator SoCs | — | Planned |
| 09 | Modern ML Accelerator SoC Power Delivery | — | Planned |
| 10 | Modern SoC Verification | — | Planned |
| 11 | Power Management in ML Accelerator SoCs | — | Planned |
| 12 | Thermal Management in ML Accelerator SoCs | — | Planned |
| 13 | Clocks and Resets in ML Accelerator SoCs | — | Planned |

---

## Presentation 01: Modern SoC Packaging

18 interactive slides covering:

**Fundamentals** — Evolution from DIP through QFP, BGA, and flip-chip to modern fan-out wafer-level packaging. Wire bond vs flip-chip architecture comparison. TSMC InFO family (WLP, PoP, L, M) and the redistribution layer (RDL) innovation.

**2.5D Integration** — Silicon interposers, RDL interposers, and embedded bridge architectures. Deep dive into TSMC CoWoS family (CoWoS-S, CoWoS-R, CoWoS-L) with capacity projections and Local Silicon Interconnect (LSI) technology. Intel EMIB embedded bridge approach with CoWoS comparison. Samsung I-Cube, ASE FOCoS, and Amkor competitive landscape.

**3D Stacking** — Die-on-die stacking with μ-bumps, Cu pillars, and hybrid bonding. TSMC SoIC (SoIC-X face-to-face, SoIC-P face-to-back) and Intel Foveros family (S, R, B, Direct). Bonding density comparison from ~400/mm² (μ-bump) to 1M/mm² (hybrid bond).

**Chiplets & Standards** — Chiplet disaggregation rationale (yield, cost, IP reuse). UCIe 1.0/2.0/3.0 protocol stack and specifications. AMD CCD reuse across product families as proof point.

**Thermal & Power** — Power delivery challenges at 700W+ TDP. eDTC, PIVR, BSPDN, and IVR solutions. TSMC direct-to-silicon liquid cooling (0.055 °C/W at 2.6 kW). SiC interposer exploration.

**Case Studies** — NVIDIA Blackwell B200 (dual-chiplet CoWoS-L, 10 TB/s NV-HBI). AMD MI300X (3.5D: SoIC + CoWoS-S, 153B transistors). Apple M2 Ultra (UltraFusion bridge). Intel Ponte Vecchio (47 tiles, 5 nodes).

**Future Directions** — Fan-Out Panel-Level Packaging (FoPLP), co-packaged optics (CPO), System-on-Wafer (SoW), glass substrates, and Chip-on-Panel-on-Substrate (CoPoS).

---

## Presentation 02: On-Chip Interconnect & NoC Design

20 interactive slides covering:

**Interconnect Evolution** — Shared bus (AHB/APB) limitations, crossbar switch architecture (NIC-400, DesignWare), and the transition to packet-switched Networks-on-Chip. Bus vs crossbar vs NoC trade-off analysis.

**NoC Topologies** — 2D Mesh, Torus, Ring, Fat Tree, and hierarchical topologies with diameter, bisection bandwidth, and layout comparisons. Why 2D mesh dominates commercial implementations. Arm CMN-700 mesh deep dive: 12×12 scalability, distributed SLC, snoop filters, CCIX/CXL support.

**AMBA Protocol Suite** — Complete evolution from AMBA 1 (1996) through AMBA 5 (2024): APB → AHB → AXI3 → AXI4 → ACE → CHI. AXI five-channel architecture with handshake timing, burst modes, OoO completion, QoS, and protection signals. AXI waveform walkthrough.

**Cache Coherency** — MOESI state machine, snoop-based vs directory-based coherency, snoop filter sizing, Arm CHI node types (RN-F, HN-F, SN-F), and step-by-step coherency transaction flow for a ReadShared with dirty-line transfer.

**QoS & Arbitration** — Traffic classification, AxQOS priority, urgency escalation, bandwidth regulation, virtual channels, TDM scheduling. Arbitration schemes (round-robin, weighted, fixed priority, age-based). Flow control: credit-based (CHI), wormhole, virtual cut-through. Routing algorithms (XY deterministic, adaptive) and deadlock avoidance via VCs and turn models.

**Commercial NoC & Case Studies** — Arm CMN-700/S3, Arteris FlexNoC/Ncore, Synopsys/Cadence NoC IP. AMD Infinity Fabric architecture (intra-CCD, CCD↔IOD, xGMI). Intel ring-to-mesh transition (Sandy Bridge through Granite Rapids) with latency analysis.

**Advanced Topics** — CXL 3.1 (CXL.io/cache/mem), UCIe D2D chiplet interconnect, NoC power management (clock/power gating, DVFS, GALS), and functional safety (AMBA parity, data poisoning, TDM, lockstep routers, ISO 26262 certified NoC IP).

---

## Presentation 03: Memory Hierarchy in ML Accelerator SoCs

23 interactive slides covering:

**SRAM Fundamentals** — 6T bitcell operation, SNM and access margins, FinFET and GAAFET bitcell evolution, SRAM compiler parameters, and the role of SRAM as on-chip scratchpad and cache storage in NPUs.

**Cache Architecture** — Direct-mapped, set-associative, and fully-associative organisations. VIPT and PIPT indexing. Inclusive vs exclusive vs non-inclusive hierarchies. Last-level cache design in ML accelerators; victim caches and prefetching.

**DRAM Fundamentals** — DRAM cell operation, row/column access, refresh, timing parameters (tRCD, tCL, tRP). DDR5: on-die ECC, sub-channel architecture, 6400–8400 MT/s roadmap.

**LPDDR5/6** — LPDDR5X features, WCK clock architecture, link ECC, data-copy/initialization commands. LPDDR6 targets (≥14.4 GT/s per pin), lower voltage, and AI mobile SoC integration.

**GDDR7** — PAM4 signalling at 36 Gbps/pin, 4-bank groups, per-pin training, graphics and HPC use cases.

**HBM3/3E/4** — 3D-stacked DRAM architecture, TSV interconnect, HBM3 (6.4 GT/s, 1.2 TB/s per stack), HBM3E (9.6 GT/s), HBM4 targets (12.8+ GT/s, wider interfaces). Integration with CoWoS and SoIC.

**CXL Memory** — CXL.mem type-3 device, memory expansion beyond package, latency characteristics vs local DRAM, and CXL memory pooling for ML inference farms.

---

## Presentation 04: High-Speed SerDes & I/O

23 interactive slides covering:

**SerDes Fundamentals** — Parallel-to-serial conversion, differential signalling, PRBS test patterns, BER and eye diagrams. NRZ vs PAM4 signalling: SNR penalty, DSP requirements, and when to transition.

**PCIe 5.0 / 6.0** — PCIe 5.0 at 32 GT/s: FBER encoding, FEC. PCIe 6.0 at 64 GT/s: PAM4, FLIT mode, L0p power state, forward error correction architectures. PCIe topology: root complex, switches, endpoints, bifurcation.

**UCIe Die-to-Die PHY** — UCIe 1.0/2.0/3.0: standard vs advanced package parameters. Bump pitch, lane width, link training, FDI/RDI interfaces. Comparison with proprietary D2D interfaces (NV-HBI, IF, BoW).

**CDR Architectures** — Bang-bang PLL CDR, Alexander phase detector, loop bandwidth optimisation, jitter transfer and jitter peaking. Fractional-N PLL for reference-less CDR.

**Equalization** — CTLE continuous-time linear equalisation, DFE decision-feedback equalisation, FFE feed-forward equalisation. Adaptation algorithms: LMS, sign-sign LMS. Combined TX/RX equalisation budgeting.

**Co-Packaged Optics (CPO)** — Motivation: SerDes power wall at high lane counts. Silicon photonics integration: grating couplers, ring modulators, Ge photodetectors. 1.6 Tb/s CPO implementations for AI switch fabrics.

---

## Presentation 05: AI / ML Accelerator Architectures

22 interactive slides covering:

**Roofline Model** — Compute-bound vs memory-bound analysis, arithmetic intensity, roofline construction for TOPS/bandwidth ratios of modern ML hardware, and how operation types (GEMM vs elementwise) map to roofline.

**Systolic Arrays** — Weight-stationary, output-stationary, and row-stationary dataflows. 2D systolic array operation for matrix multiplication. Google TPU v1 256×256 MXU case study. Utilisation challenges with small batch sizes.

**Dataflow Engines** — Streaming vs memory-hierarchy architectures. Graphcore IPU: bulk-synchronous parallel execution, in-processor memory model. Cerebras WSE: wafer-scale SRAM, no DRAM. SambaNova RDU: reconfigurable dataflow.

**Sparsity Exploitation** — Structured vs unstructured sparsity. NVIDIA 2:4 sparsity (Ampere Sparse Tensor Core): 2× TOPS multiplier. Activation sparsity harvesting in ReLU networks. Sparse matrix formats (CSR, CSC, bitmap).

**Mixed Precision** — FP32, TF32, BF16, FP16, FP8 (E4M3/E5M2), INT8, INT4. NVIDIA Hopper Transformer Engine: per-tensor FP8 scaling. Quantisation-aware training vs post-training quantisation.

**NPU Integration** — Heterogeneous SoC: CPU + GPU + NPU + DSP. AMBA AXI4 integration, DMA scheduling, compiler-managed SRAM. Apple Neural Engine, Qualcomm Hexagon, MediaTek APU architectures.

**Case Studies** — NVIDIA H100 SXM: 989 TFLOPS FP16, 3.9 TB/s HBM3. Google TPUv4: 275 TFLOPS BF16, ICI interconnect, 4096-chip pod. Graphcore Bow IPU: 1.47 PFLOPS FP16 bulk-sync, 900 MB SRAM on-die.

---

## Presentation 06: SoCs for ML Inference

24 interactive slides covering:

**Training vs Inference** — Computational profiles, batch size 1 vs large batch, FLOP/byte ratios, latency vs throughput objectives, and why inference hardware diverges from training hardware.

**Quantisation** — INT8 symmetric/asymmetric quantisation, scale factor computation, per-tensor vs per-channel calibration, INT4 weight-only quantisation for LLM memory bandwidth reduction, FP8 (E4M3/E5M2) for activation quantisation.

**KV-Cache** — Multi-head attention memory footprint: 2 × L × H × D × batch × dtype bytes. Paged attention (vLLM) reducing fragmentation. KV-cache compression: grouped-query attention (GQA), multi-query attention (MQA), quantised KV-cache.

**NPU Micro-architecture** — Tile-based execution, DMA-prefetch double-buffering, compiler-managed SRAM, hardware-software co-design for kernel fusion. Zero-overhead loop control and systolic reuse in weight-stationary NPUs.

**On-Device LLMs** — Memory bandwidth as the bottleneck: arithmetic intensity ~1 FLOP/byte for single-token decode. Apple M3 unified memory bandwidth (100 GB/s) vs model parameter size. Llama 3 8B INT4: ~4 GB, fits in mobile SoC LPDDR5.

**Speculative Decoding** — Draft model generates k tokens; verifier accepts/rejects in single forward pass. 2–4× throughput improvement with well-matched draft model. Hardware implications: two models in SRAM simultaneously.

**TinyML** — MCU-class inference: CMSIS-NN for Cortex-M, TFLite Micro, ONNX Runtime Mobile. INT4/INT2 weights for <1 MB model footprint. Keyword spotting and anomaly detection always-on use cases.

**Case Studies** — Groq LPU: deterministic compiler-scheduled SRAM, no caches, 750 tokens/s/chip. NVIDIA H100: NVLink 900 GB/s for tensor parallel LLM inference. Apple M3 Max: 400 GB/s unified memory bandwidth, Neural Engine 38 TOPS.

---

## Presentation 07: Security in SoC Design

22 interactive slides covering:

**Threat Landscape** — Why software security requires a hardware trust anchor. Cold-boot attacks, DMA attacks, Spectre/Meltdown microarchitectural side-channels, and the hardware/firmware attack surface. Regulatory drivers: PSA Certified, FIPS 140-3, EU Cyber Resilience Act.

**Security Architecture** — Concentric rings of trust: silicon → HRoT → secure firmware → TEE → application layer. NS-bit propagation on AXI. Security lifecycle states (TEST → PROVISIONING → PRODUCTION → EOL).

**Hardware Root of Trust (HRoT)** — Boot ROM, OTP/eFuse arrays, TRNG, crypto engine, secure key vault, and tamper detection sensors. Lifecycle state machine. Commercial HRoT IPs: Arm CryptoIsland/RSS, Rambus RT-630, Synopsys tRoot, Google Titan M2, Apple Secure Enclave, Microsoft Pluton.

**Secure Boot & Chain of Trust** — BootROM → BL1/BL2 → BL31 (EL3) → BL32 (OP-TEE) → BL33 (U-Boot/UEFI). ECDSA signature verification at each stage. Verified boot vs measured boot; rollback protection via OTP monotonic counter.

**Arm TrustZone & RME** — Secure World / Normal World hardware isolation; NS-bit on AXI; TZASC and TZPC. OP-TEE Trusted Applications. Armv9 Realm Management Extension: 4th security state, Realm VMs isolated from hypervisor (Arm CCA).

**Physical Unclonable Functions (PUFs)** — Challenge-response mechanism; SRAM PUF, Ring Oscillator PUF, Arbiter PUF, Butterfly PUF, Oxide Breakdown PUF. Error correction with BCH/polar codes. ML modelling attack vulnerability. Applications: key derivation, anti-counterfeiting, FPGA bitstream protection.

**TRNG** — Entropy sources: thermal noise, ring oscillator jitter, metastability harvesting. NIST SP 800-90A/B/C compliant architecture: entropy source → health tests → conditioner → DRBG. BSI AIS 20/31 PTG.2/PTG.3 classes. FIPS 140-3 self-test requirements.

**Crypto Accelerators** — AES-256-GCM/XTS pipelined engine (100 Gbps+ in N5). SHA-2/3, HMAC engines. PKA: RSA 2048–8192, ECC P-256/384, Ed25519. Post-quantum: ML-KEM (FIPS 203), ML-DSA (FIPS 204), SLH-DSA (FIPS 205); shared NTT accelerator.

**Side-Channel Attack Taxonomy** — SPA, DPA, CPA, template attacks on power traces. DEMA with local EM probe. Timing attacks (RSA square-and-multiply), cache-timing (Flush+Reload, Prime+Probe). Fault injection: voltage glitching, clock glitching, laser FI, EMFI. DFA on AES from one-byte fault.

**Side-Channel Countermeasures** — Masking: (d+1)-share secret splitting. Hiding: random pre-charge, dual-rail WDDL/SABL logic. PDN filtering. EM shielding with active mesh. Constant-time implementations. Voltage/frequency monitors for fault injection detection. Temporal/spatial redundancy; infective computation.

**Secure Storage & Key Management** — Key hierarchy: RK → DIK → CEK → session keys. AES-256-KeyWrap, HKDF. Anti-fuse OTP vs eFuse provisioning. DRAM inline encryption (AES-XTS-256). Merkle tree integrity over DRAM. AMD SME/SEV-SNP, Intel TME/TDX. Zeroisation circuits.

**Debug Security** — JTAG as attack vector: halt-and-modify, scan chain exposure. Arm CoreSight authentication signals (DBGEN, NIDEN, SPIDEN, SPNIDEN). Challenge-response Secure Debug Protocol (SDP). Lifecycle-gated JTAG; one-time debug fuses with OTP logging.

**DMA Security & SMMU** — DMA bypass of CPU MMU. Rogue PCIe device cold-boot DRAM access. Arm SMMUv3.2: Stage-1/Stage-2 translation, StreamID per peripheral, PCIe ATS/PRI, SVA. PCIe ACS peer-to-peer isolation. CXL.mem security extensions.

**Memory Encryption & Integrity** — Inline AES-XTS between controller and PHY. AMD SME/SEV/SEV-SNP with RMP table. Intel TDX Trust Domains. HBM inline encryption. MAC tags + Merkle counter-tree for replay protection. NVMe TCG Opal 2.0; eMMC RPMB; FTL transparent encryption.

**Remote Attestation & DICE** — DICE: UDS → CDI chain bound to firmware measurements → alias certificate hierarchy. TPM 2.0/fTPM: PCR extend-only registers, sealed storage, AIK-signed quotes. AMD SEV-SNP VCEK attestation. Intel TDX DCAP. Arm CCA Realm attestation token. IETF RATS architecture.

**Supply Chain Security** — Hardware Trojans: RTL/synthesis/mask insertion, rare-trigger activation. Counterfeit ICs: recycled, remarked, cloned. IP theft, overproduction, FPGA bitstream cloning. Trojan detection: netlist verification, side-channel fingerprinting, formal verification, BIST. PUF authentication at incoming inspection. Logic locking; layout camouflage; split manufacturing.

**ML Model Security** — Weight encryption with AES-256-XTS; CEK from device-unique PUF-derived key. Signed model manifest (SHA-3 + ECDSA). DRAM integrity tree against weight poisoning. Model extraction, membership inference, adversarial inputs, prompt injection countermeasures. Apple Private Cloud Compute TEE-hosted inference model.

**Security Standards & Certification** — FIPS 140-3 levels 1–4, NVLAP CMVP testing. Common Criteria EAL 1–7; PP-0084/0117, PP-0035. Arm PSA Certified L1–L3. ISO/SAE 21434 (automotive), IEC 62443 (industrial), DO-326A (avionics), SESIP, EU Cyber Resilience Act.

**Case Studies** — Apple Secure Enclave: dedicated ART core, UID fuse, Effaceable Storage, Face ID/Touch ID biometric isolation. AMD EPYC SEV-SNP: PSP Cortex-A5, SME full-DRAM encryption, RMP integrity, VCEK attestation. Google Titan M2: RISC-V security chip, Strongbox Keymaster, FIPS 140-2 L2. NVIDIA H100 Confidential Computing: encrypted PCIe/NVLink, GPU attestation via NVIDIA RIM, GSP RoT, SEV-SNP/TDX integration.

**Interactive Demo** — Live DPA (Differential Power Analysis) attack simulator: adjustable trace count (10–500), key byte hypothesis slider, real-time correlation trace with peak detection showing key recovery at sufficient trace count.

---

## Repository Structure

```
├── index.html                          ← Landing page (links to all presentations)
├── README.md                           ← This file
├── 01-soc-packaging/
│   └── index.html                      ← Reveal.js interactive slide deck
├── 02-on-chip-interconnect/
│   └── index.html
├── 03-memory-hierarchy/
│   └── index.html
├── 04-serdes-io/
│   └── index.html
├── 05-ai-ml-accelerator-architectures/
│   └── index.html
├── 06-socs-for-ml-inference/
│   └── index.html
└── 07-security-in-soc-design/
    └── index.html
```

Each presentation is a single self-contained `index.html`. No build step, no npm — just HTML/CSS/JS with CDN-hosted Reveal.js and Google Fonts.

## Slide Controls

| Action | Key |
|--------|-----|
| Next / Previous | `→` `←` or swipe |
| Overview | `Esc` |
| Fullscreen | `F` |
| Export to PDF | append `?print-pdf` to URL |

## Technology

[Reveal.js 4.6](https://revealjs.com) · [highlight.js](https://highlightjs.org) (Monokai) · Playfair Display + DM Sans + JetBrains Mono

## References

**Packaging:** TSMC 3DFabric (CoWoS, InFO, SoIC) · Intel Packaging Technology (EMIB, Foveros) · UCIe Consortium Specifications 1.0–3.0 · Yole Group, "State of Advanced Packaging 2024" · IEEE ECTC 2025

**Interconnect:** Arm AMBA Specifications (AXI4, ACE, CHI) · Arm CMN-700 Technical Reference Manual · AMD Infinity Fabric Architecture White Paper · IEEE Micro, "A Decade of Network-on-Chip Research"

**Memory:** JEDEC HBM3/HBM3E Standards (JESD238) · JEDEC LPDDR5/6 (JESD209-5/6) · JEDEC DDR5 (JESD79-5) · GDDR7 Standard (JESD232)

**SerDes:** PCI-SIG PCIe 5.0/6.0 Specifications · UCIe 2.0 Specification · IEEE 802.3cd (100G/50G/25G)

**ML Accelerators:** NVIDIA H100/Hopper Architecture White Paper · Google TPUv4 Architecture Paper (ISCA 2023) · Cerebras CS-2 Architecture · Graphcore Bow IPU White Paper

**ML Inference:** Groq LPU Architecture · AMD MI300X Architecture White Paper · Apple M-series Architecture Overview · vLLM Paged Attention (SOSP 2023)

**Security:** NIST SP 800-90A/B/C (DRBG, Entropy Sources) · NIST FIPS 203/204/205 (ML-KEM, ML-DSA, SLH-DSA) · TCG DICE Architecture Specification · Arm TrustZone / CCA Architecture Reference · AMD SEV-SNP Architecture Guide · Kocher et al., "Differential Power Analysis," CRYPTO 1999 · Mangard, Oswald & Popp, *Power Analysis Attacks*, Springer 2007 · Rührmair et al., "PUF Modelling Attacks," ACM CCS 2010 · SEMI T20 Supply Chain Integrity Standard · IPC-1782 Traceability Standard

## License

Educational use. Code examples provided as-is. Standards references are to publicly available NIST, IEEE, JEDEC, TCG, and industry documents.
