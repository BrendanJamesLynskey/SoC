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
| 01 | Modern SoC Packaging | 30 | ✅ Complete |
| 02 | On-Chip Interconnect & NoC Design | 31 | ✅ Complete |
| 03 | Memory Hierarchy in ML Accelerator SoCs | 23 | ✅ Complete |
| 04 | High-Speed SerDes & I/O | 23 | ✅ Complete |
| 05 | AI / ML Accelerator Architectures | 22 | ✅ Complete |
| 06 | SoCs for ML Inference | 24 | ✅ Complete |
| 07 | Security in SoC Design | 22 | ✅ Complete |
| 08 | CXL in ML Accelerator SoCs | 22 | ✅ Complete |
| 09 | Modern ML Accelerator SoC Power Delivery | 22 | ✅ Complete |
| 10 | Modern SoC Verification | 23 | ✅ Complete |
| 11 | Power Management in ML Accelerator SoCs | 23 | ✅ Complete |
| 12 | Thermal Management in ML Accelerator SoCs | 23 | ✅ Complete |
| 13 | Clocks and Resets in ML Accelerator SoCs | 23 | ✅ Complete |
| 14 | Modern Trends in FPGA Technology | 23 | ✅ Complete |
| 15 | AMD / Xilinx FPGA Technology & Products | 23 | ✅ Complete |
| 16 | FPGAs in Finance | 23 | ✅ Complete |

---

## Presentation 01: Modern SoC Packaging

30 interactive slides covering:

**Fundamentals** — Evolution from DIP through QFP, BGA, and flip-chip to modern fan-out wafer-level packaging. Wire bond vs flip-chip architecture comparison. TSMC InFO family (WLP, PoP, L, M) and the redistribution layer (RDL) innovation.

**2.5D Integration** — Silicon interposers, RDL interposers, and embedded bridge architectures. Deep dive into TSMC CoWoS family (CoWoS-S, CoWoS-R, CoWoS-L) with capacity projections and Local Silicon Interconnect (LSI) technology. Intel EMIB embedded bridge approach with CoWoS comparison. Samsung I-Cube, ASE FOCoS, and Amkor competitive landscape.

**3D Stacking** — Die-on-die stacking with μ-bumps, Cu pillars, and hybrid bonding. TSMC SoIC (SoIC-X face-to-face, SoIC-P face-to-back) and Intel Foveros family (S, R, B, Direct). Bonding density comparison from ~400/mm² (μ-bump) to 1M/mm² (hybrid bond).

**Chiplets & Standards** — Chiplet disaggregation rationale (yield, cost, IP reuse). UCIe 1.0/2.0/3.0 protocol stack and specifications. AMD CCD reuse across product families as proof point.

**Thermal & Power** — Power delivery challenges at 700W+ TDP. eDTC, PIVR, BSPDN, and IVR solutions. TSMC direct-to-silicon liquid cooling (0.055 °C/W at 2.6 kW). SiC interposer exploration.

**Case Studies** — NVIDIA Blackwell B200 (dual-chiplet CoWoS-L, 10 TB/s NV-HBI). AMD MI300X (3.5D: SoIC + CoWoS-S, 153B transistors). Apple M2 Ultra (UltraFusion bridge). Intel Ponte Vecchio (47 tiles, 5 nodes).

**Future Directions** — Fan-Out Panel-Level Packaging (FoPLP), co-packaged optics (CPO), System-on-Wafer (SoW), glass substrates, and Chip-on-Panel-on-Substrate (CoPoS).

---

## Presentation 02: On-Chip Interconnect & NoC Design

31 interactive slides covering:

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

## Presentation 08: CXL in ML Accelerator SoCs

22 interactive slides covering:

**CXL Protocol Foundation** — CXL protocol stack: CXL.io (PCIe-based discovery/enumeration), CXL.cache (host-managed device cache coherency, D2H/H2D snoop flows), CXL.mem (device-attached memory, M2S/S2M channels, HDM decoders, bias modes). ARB/MUX flex bus multiplexing. 68B vs 256B flit formats.

**CXL Evolution** — CXL 1.0/1.1 (PCIe 5.0, 64 GB/s), CXL 2.0 (switching, pooling, Type 3 devices), CXL 3.0 (PCIe 6.0 PAM4, 128 GB/s, multi-level switching, back-invalidation, GFA), CXL 3.1 (port-based routing, extended PBR, TSP security). Per-version feature and bandwidth comparison.

**Device Taxonomy** — Type 1 (CXL.io + CXL.cache — SmartNICs, accelerators without own memory), Type 2 (all three protocols — GPUs, FPGAs with coherent host memory access), Type 3 (CXL.io + CXL.mem — memory expanders). Detailed per-type protocol usage, examples, and ML integration scenarios.

**CXL Fabric & Pooling** — Single-level and multi-level switching, Fabric Manager API, dynamic capacity devices (DCD). Memory pooling: shared CXL DRAM across multiple hosts, dynamic allocation, multi-headed memory. ML inference cluster pooling economics.

**CXL for ML Workloads** — KV-cache expansion (tiered HBM/CXL DDR5/CXL PMem for LLM serving, latency-hiding prefetch). Memory-bandwidth-bound inference (pooled model sharding, CXL vs RDMA). CXL SoC integration: PHY IP, controller IP, CHI-CXL bridge, latency budget breakdown.

**Case Studies** — Intel Sapphire Rapids CXL 1.1, AMD Genoa CXL 2.0, Samsung CMM-D/CMM-H CXL memory modules, SK hynix CMS, Astera Labs Leo fabric switches, Micron CZ120 memory expander.

---

## Presentation 09: Modern ML Accelerator SoC Power Delivery

22 interactive slides covering:

**PDN Fundamentals** — Power delivery network from VRM through PCB, package, and die. Impedance at each stage. Target impedance (Z_target = V_ripple / I_transient) and frequency-domain analysis. Anti-resonance mitigation.

**Decoupling Hierarchy** — Bulk capacitors, MLCCs, package MIM caps, on-die MOS caps, and embedded deep trench capacitors (eDTC). ESL/ESR analysis at each level. TSMC eDTC capacitance density roadmap.

**IR Drop** — Static vs dynamic IR drop analysis. Current density maps, electromigration reliability (Black's equation). Signoff criteria and margin budgets.

**Voltage Regulation** — Multi-phase buck VRM topologies, DrMOS, 48V direct-to-load conversion. Package-integrated voltage regulators (PIVR/Intel FIVR) for per-core DVFS. On-die LDO and integrated voltage regulators (IVR): digital LDOs, switched-capacitor converters, area/efficiency trade-offs.

**Advanced PDN Technologies** — Backside Power Delivery Network (BSPDN): Intel PowerVia, TSMC N2P/A16 backside power, routing and IR-drop benefits. eDTC integration. TSV power delivery for 2.5D/3D packages.

**ML Accelerator Challenges** — 700W+ AI GPU power architecture (NVIDIA Blackwell 48V path). di/dt management for GEMM↔communication switching transients. Power integrity simulation tools and signoff. Chiplet power delivery and per-chiplet regulation.

**Case Studies** — NVIDIA B200 power architecture, AMD MI300X power delivery, Intel Ponte Vecchio FIVR, Apple M2 Ultra unified memory power.

---

## Presentation 10: Modern SoC Verification

23 interactive slides covering:

**Simulation-Based Verification** — RTL simulation: event-driven simulation, 4-state logic, VCS/Xcelium/Questa/Verilator tool comparison. UVM architecture: agent, driver, monitor, scoreboard, sequencer, constrained-random stimulus, coverage-driven methodology. SystemVerilog Assertions (SVA): immediate vs concurrent assertions, property/sequence syntax examples.

**Coverage-Driven Verification** — Functional coverage, code coverage (line/branch/toggle/FSM), cross-coverage. Covergroup examples. Coverage closure process and signoff targets.

**Formal & Static Methods** — Model checking: bounded vs unbounded proofs, property types, Jasper/VC Formal/Questa Formal. Formal apps: connectivity checking, register verification, deadlock/livelock detection, security path verification, X-propagation. Static analysis: lint (Spyglass/Ascent), CDC, RDC, power-aware checks (UPF/CPF).

**Hardware-Assisted Verification** — Emulation: Palladium/Veloce/ZeBu architectures, ~1–10 MHz speed, ICE/SCE modes. FPGA prototyping: HAPS/Protium, ~50–200 MHz, partitioning challenges, early software development.

**SoC-Level Verification** — Integration verification: connectivity, interrupt routing, address map, power domain testing. DFT: scan insertion, ATPG, Logic BIST, Memory BIST, JTAG boundary scan. Performance verification: traffic generators, NoC validation, memory subsystem verification.

**Modern Challenges** — AI/ML SoC verification: systolic arrays, FP8/INT4 datapath precision, DMA engines, multi-clock NPUs, end-to-end inference validation. Verification signoff: regression management, bug rate curves, tape-out checklist.

**Tools Landscape** — Synopsys VCS/Verdi/ZeBu, Cadence Xcelium/Jasper/Palladium, Siemens Questa/Veloce, open-source (Verilator, cocotb, CHISEL).

---

## Presentation 11: Power Management in ML Accelerator SoCs

23 interactive slides covering:

**Power Domain Architecture** — Domain partitioning: always-on, switchable, retention domains. Isolation cells, level shifters, retention registers. Power gating: header/footer switches, rush current control, 7-step gating sequence (save→isolate→clamp→gate→ungate→de-isolate→restore), wake-up latency. UPF/CPF (IEEE 1801) power intent specification and power-aware verification.

**DVFS** — P = αCV²f fundamentals, operating point tables, voltage-frequency curves, adaptive voltage scaling (AVS), guardband reduction. DVFS implementation: on-die droop detectors, PLL/FLL relock, firmware governors. Per-domain DVFS in ML SoCs: independent NPU/GPU/CPU/memory controller domains.

**Voltage Regulation** — PMIC architecture: multi-rail design, I²C/SPI/SVID control, sequencing, fault protection. LDO vs switching regulators: efficiency, noise, area trade-offs. On-die regulation: digital LDOs, Intel FIVR/PIVR, granular voltage islands.

**ML Workload Optimization** — Dark silicon and utilization: spatial/temporal power scheduling, chiplet budgeting. Clock gating: ICG cells, fine vs coarse-grained, ML-specific gating (sparsity, operand-aware). Workload-aware power management: training phases, inference batching, dynamic power capping, RAPL/NVML/HSMP. Low-power design: multi-Vt libraries, gate-length biasing, power-aware synthesis, leakage at advanced nodes.

**System-Level** — Thermal-power co-management (DTPM), feedback loops, edge thermal constraints.

**Case Studies** — NVIDIA H100 power management, Apple M3 Ultra DVFS, AMD MI300X power domains, Google TPU v5p power architecture, Qualcomm Hexagon DSP power states.

---

## Presentation 12: Thermal Management in ML Accelerator SoCs

23 interactive slides covering:

**Thermal Fundamentals** — Heat transfer mechanisms (conduction, convection, radiation). Thermal resistance networks (Rjc, Rcs, Rsa). Thermal RC models. TDP definition vs real power dissipation. Junction temperature limits and worst-case workloads.

**Thermal Interface Materials** — TIM1 (die-to-IHS) and TIM2 (IHS-to-heatsink). Thermal conductivity comparison: paste, pad, liquid metal, graphite, solder TIM. Pump-out and dry-out degradation mechanisms.

**Air Cooling** — Heatsink design: fin geometry, baseplate spreading, heat pipe integration. Vapour chambers: operating principle (evaporation→transport→condensation→wick return), thermal spreading performance. Fan and airflow: CFD-optimized designs, push-pull configurations, acoustic constraints, server rack airflow management.

**Liquid Cooling** — Cold plate designs: direct-to-chip, microchannel geometries, coolant selection, flow rate vs pressure drop. Direct liquid cooling: TSMC direct-to-silicon (0.055 °C/W at 2.6 kW). Immersion cooling: single-phase vs two-phase, dielectric fluids (3M Novec), data center deployment, PUE impact.

**On-Die Thermal Management** — Hotspot mitigation: non-uniform power maps, on-die thermal sensors, dynamic workload migration, HBM/logic thermal coupling in 2.5D/3D. Thermal throttling: PROCHOT, hardware frequency/voltage reduction, firmware control loops. 3D stacking thermal challenges: inter-die resistance, TSV thermal paths, HBM stack limits.

**System & Data Center** — Rack-level cooling (42–100+ kW per rack), hot/cold aisle containment, ASHRAE guidelines. AI supercomputer cooling: NVIDIA DGX SuperPOD, Google TPU pods, Meta Grand Teton, Microsoft Maia.

**Case Studies** — NVIDIA H100/B200 thermal solutions, AMD MI300X vapour chamber, Intel Ponte Vecchio liquid cooling, TSMC direct-to-silicon cooling roadmap.

---

## Presentation 13: Clocks and Resets in ML Accelerator SoCs

23 interactive slides covering:

**Clock Generation** — Charge-pump PLL architecture (PFD→CP→LPF→VCO→divider), loop bandwidth, lock time, phase noise. Advanced PLL types: ADPLL (all-digital), fractional-N, bang-bang PLL for SerDes CDR, sub-picosecond jitter PLLs. PLL specification comparison: period jitter, cycle-to-cycle jitter, phase noise (dBc/Hz), lock time, tuning range, power.

**Clock Distribution** — Clock tree synthesis: H-tree, mesh, fishbone topologies; skew minimisation, insertion delay, useful skew, OCV/AOCV. Clock mesh and spine: global low-skew distribution, grid shielding, capacitive loading analysis. Clock gating: ICG cells (latch-based), hierarchical gating, efficiency metrics.

**Clock Domain Crossing** — Metastability theory and MTBF calculation. Synchroniser design (2-FF, 3-FF). CDC data transfer: toggle synchroniser, gray-code FIFO, MUX recirculation, handshake protocols. Async FIFO design with gray-code pointers. CDC verification: Spyglass CDC, Meridian CDC, Questa CDC, reconvergence and glitch detection. GALS: mesochronous, plesiochronous, heterochronous interfaces; pausable clocking; GALS wrappers.

**Reset Architecture** — Synchronous vs asynchronous reset. Async-assert/sync-deassert pattern with Verilog examples. Reset tree distribution. Reset sequencing: multi-domain ordering, POR, brown-out detection, watchdog timer, warm vs cold reset, SoC reset state machine.

**ML Accelerator Specifics** — Multi-domain clock architecture (NPU core, SRAM, NoC, HBM PHY, PCIe, management processor) with independent DVFS. Jitter budgets: HBM PHY allocation, SerDes reference clock requirements, DDR/LPDDR specs, PLL cascading jitter accumulation (RSS).

**Case Studies** — NVIDIA GPU GPC boost clocking, AMD MI300X Infinity Fabric clocking, Apple SoC clock domains, Intel Ponte Vecchio multi-tile clocking.

---

## Presentation 14: Modern Trends in FPGA Technology

23 interactive slides covering:

**Architecture Foundations** — LUT-based FPGA architecture recap, CLBs, island-style interconnect fabric, I/O blocks, and the evolution from simple PLDs to modern adaptive compute platforms.

**Process Node Migration** — FPGAs moving to 7nm, 5nm, and 3nm nodes. FPGA-specific challenges vs ASICs at advanced nodes: routing dominance, configuration cell density, cost implications, and why trailing-edge nodes remain viable for many applications.

**Modern Fabric Innovations** — Adaptive Logic Modules (ALMs), fracturable LUTs, MLAB vs M20K vs UltraRAM memory hierarchy, DSP block evolution from simple multipliers to AI-optimized tensor blocks with INT8/INT4 packing.

**Hard IP & Heterogeneous Integration** — PCIe Gen5, 100G/400G Ethernet MACs, DDR5/HBM memory controllers, crypto engines, and Network-on-Chip (NoC) integration. Heterogeneous FPGA SoCs: hard ARM/RISC-V cores with FPGA fabric, AMD Versal model (scalar + adaptable + AI engines), Intel Agilex HPS.

**Chiplets & HBM** — EMIB, Foveros, and chiplet-based FPGA approaches. Why FPGAs benefit from chiplets (yield, mixed-node integration). HBM2E integration in FPGAs, bandwidth vs capacity tradeoffs.

**High-Speed Transceivers** — Modern FPGA SerDes at 116 Gbps+, PAM4 signalling, 800G Ethernet support, co-packaged optics trends.

**AI/ML on FPGAs** — INT8/INT4 inference, AI tensor blocks, where FPGAs fit vs GPU/ASIC for inference workloads. Data center and cloud FPGA deployments: SmartNICs, DPUs, infrastructure offload, AWS F1 and Azure NP instances.

**Design Methodology** — HLS adoption, OpenCL/SYCL/oneAPI flows, Python-to-FPGA tools, RTL still dominant for performance-critical paths. Partial reconfiguration and Dynamic Function Exchange (DFX) for runtime reconfiguration and multi-tenant cloud FPGAs.

**Verification, Security & Power** — FPGA-specific verification and debug (SignalTap/ILA, formal verification), bitstream encryption, PUFs, secure boot. Power budgets at advanced nodes, dynamic power management, thermal solutions for high-end FPGAs.

**FPGA vs ASIC** — Decision framework: NRE costs, time-to-market, volume crossover points. FPGA prototyping and emulation for ASIC development (Synopsys HAPS, Cadence Protium).

**Ecosystem & Future** — Open-source FPGA toolchains (Yosys, nextpnr, F4PGA). Market dynamics: AMD/Xilinx vs Intel/Altera vs Lattice vs Microchip. Future directions: photonic FPGAs, 3D-stacked FPGA+memory, compute-in-memory, neuromorphic fabric, RISC-V softcores.

---

## Presentation 15: AMD / Xilinx FPGA Technology & Products

23 interactive slides covering:

**Heritage & Acquisition** — Xilinx history from the invention of the FPGA through Virtex, Spartan, and UltraScale families. AMD's $49B acquisition in 2022, strategic rationale, and integration into the Adaptive Computing Division.

**UltraScale+ Families** — Virtex UltraScale+ architecture deep dive: CLB structure, UltraRAM, DSP48E2 slices, GTY/GTM transceivers, HBM variants. Kintex UltraScale+ mid-range and Artix cost-optimized families: target applications, key specifications, device comparison.

**Zynq Platform** — Zynq UltraScale+ MPSoC: quad-core A53 + dual R5F + FPGA fabric, PS-PL interfaces, TrustZone security, PMU, APU/RPU isolation. Zynq RFSoC: integrated RF-ADC/DAC, direct RF sampling for 5G/radar/EW, Gen 1/2/3/DFE evolution.

**Versal ACAP** — Versal architecture overview: Scalar Engines (ARM A72/R5), Adaptable Engines (FPGA fabric), Intelligent Engines (AI Engines), integrated NoC, platform management controller. AI Core series: AI Engine tile architecture (VLIW + SIMD vector core), cascade dataflow, INT8/INT4 throughput. AI Edge series: power-efficient inference for automotive ADAS, robotics, surveillance. Premium series: 112G PAM4 transceivers, 600G Ethernet, multi-100G crypto, PCIe Gen5. HBM series: HBM2e integration, 820 GB/s bandwidth. Gen 2 roadmap and next-generation migration path.

**Software Ecosystem** — Vivado Design Suite: synthesis, implementation, timing closure, IP Integrator, block design flows. Vitis Unified Software Platform: HLS, AI Engine compiler, Vitis libraries, XRT runtime. Vitis AI: DPU IP, quantization tools, model zoo, ONNX/TensorFlow/PyTorch support.

**Market Applications** — Data center: Alveo accelerator cards (U25N, U55C, V70, V80), SmartNIC, cloud deployments. 5G & communications: O-RAN, massive MIMO, beamforming, RFSoC in radio access networks. Automotive: XA family, ADAS sensor fusion, ISO 26262 functional safety. Aerospace & defense: radiation-tolerant and space-grade variants, SOSA standard, anti-tamper.

**Competitive Positioning & Direction** — AMD vs Intel Agilex vs Lattice Nexus comparison. AMD's adaptive computing roadmap: chiplet strategy, CPU/GPU convergence, AI-everywhere thesis.

---

## Presentation 16: FPGAs in Finance

23 interactive slides covering:

**The Latency Imperative** — Why FPGAs dominate ultra-low latency trading: deterministic execution, wire-speed processing, nanosecond-level response. Comparison vs CPU, kernel bypass, GPU, and ASIC approaches. History of FPGA adoption in finance from ~2007 through modern full-pipeline implementations.

**Market Data & Order Books** — Parsing exchange protocols (ITCH, OUCH, FIX, OPRA, SBE) at wire speed. FPGA-based order book construction: BRAM-based price-level storage, incremental updates, top-of-book extraction. Tick-to-trade pipeline architecture with sub-microsecond latency budgets.

**FPGA Network Infrastructure** — Hardware TCP/UDP offload, 10G/25G/100G Ethernet MAC, PTP timestamping (IEEE 1588), cut-through switching. Colocation facilities, cross-connects, microwave/laser networks, and where FPGAs sit in the rack topology.

**Trading Strategies in Hardware** — Market making: pricing engines, quoting strategies, Greeks calculation in fabric. Statistical arbitrage: EWMA, correlation engines, multi-asset scanning. Options pricing: Black-Scholes pipeline, binomial/trinomial trees, implied volatility solvers, fixed-point vs floating-point tradeoffs.

**Risk & Analytics** — Real-time pre-trade risk checks in hardware. VaR calculation, Monte Carlo acceleration, portfolio margining. Cryptocurrency and digital asset trading: exchange infrastructure, DeFi/MEV applications.

**Platforms & Development** — Key FPGA platforms for finance: Xilinx Alveo, Intel Agilex, Solarflare/Xilinx SmartNICs. FPGA development in finance: dedicated teams in banks/HFT firms vs specialist vendors (Exegy, Enyx, Fixnetix). Development workflow: SystemVerilog dominance, limited HLS adoption, simulation and regression testing, commercial IP ecosystem.

**Challenges** — Development complexity: long build cycles, specialist talent shortage, debugging difficulty. Regulatory and compliance: MiFID II, Reg NMS, audit trails, determinism as a compliance feature. Latency measurement and benchmarking methodology.

**Future Directions** — AI/ML inference on trading FPGAs, PCIe Gen5/CXL integration, 400G/800G Ethernet, cloud FPGA trading, FPGA vs SmartNIC vs DPU convergence, industry consolidation trends.

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
├── 07-security-in-soc-design/
│   └── index.html
├── 08-cxl-in-ml-accelerator-socs/
│   └── index.html
├── 09-power-delivery/
│   └── index.html
├── 10-soc-verification/
│   └── index.html
├── 11-power-management/
│   └── index.html
├── 12-thermal-management/
│   └── index.html
├── 13-clocks-and-resets/
│   └── index.html
├── 14-modern-fpga-trends/
│   └── index.html
├── 15-amd-xilinx-fpgas/
│   └── index.html
└── 16-fpgas-in-finance/
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

**CXL:** CXL Consortium Specifications 1.0–3.1 · Sharma et al., "An Introduction to the Compute Express Link," IEEE Micro 2022 · Pond et al., "CXL Memory Pooling for ML Inference," ASPLOS 2023 · Linux CXL Subsystem Documentation

**Power Delivery:** Swaminathan & Engin, *Power Integrity Modeling and Design for Semiconductors and Systems*, Prentice Hall · Intel PowerVia Technology White Paper · TSMC N2P/A16 Backside Power Delivery · Jakushokas et al., "Power Distribution Networks with On-Chip Decoupling Capacitors," Springer 2011

**Verification:** Spear, *SystemVerilog for Verification*, Springer · IEEE 1800-2017 (SystemVerilog) · Accellera UVM 1.2 Reference Guide · Cadence Jasper Formal Verification · Synopsys ZeBu Architecture White Paper · Foster et al., *Assertion-Based Design*, Springer

**Power Management:** IEEE 1801 (UPF) · Rabaey et al., *Digital Integrated Circuits*, Prentice Hall · Brooks & Martonosi, "Dynamic Thermal Management for High-Performance Microprocessors," HPCA 2001 · NVIDIA NVML/DCGM Documentation · Intel RAPL Specification

**Thermal:** ASHRAE TC 9.9, *Thermal Guidelines for Data Processing Environments* · Bar-Cohen & Iyengar, *Design and Optimization of Thermal Systems*, Wiley · TSMC Direct-to-Silicon Liquid Cooling Technology · Kandlikar et al., "Review of Heat Transfer Enhancement in Microchannels," ASME 2005

**Clocks & Resets:** Razavi, *Design of Analog CMOS Integrated Circuits* (PLL chapters) · Kundert, *The Designer's Guide to Spice and Spectre* · Ginosar, "Metastability and Synchronizers: A Tutorial," IEEE Design & Test 2011 · Cummings, "Simulation and Synthesis Techniques for Asynchronous FIFO Design," SNUG 2002

**FPGAs:** AMD/Xilinx Versal ACAP Architecture Manual · AMD/Xilinx UltraScale+ Architecture Reference · Intel Agilex 7/9 Device Overview · Lattice Nexus Platform White Paper · Trimberger, "Three Ages of FPGAs," ISSCC 2015 · Kuon & Rose, "Measuring the Gap Between FPGAs and ASICs," IEEE TCAD 2007 · Yosys Open Synthesis Suite Documentation · Project F4PGA (formerly SymbiFlow) · AMD Vitis AI User Guide · AMD Alveo Data Center Accelerator Card Specifications

**FPGAs in Finance:** Lockwood et al., "Low Latency Trading with FPGAs," IEEE Micro 2012 · Morris et al., "FPGA Accelerated Market Data Feed Handling," ACM FPGA 2014 · Sadoghi et al., "Multi-query Stream Processing on FPGAs," ICDE 2012 · Enyx FPGA Trading Solutions White Paper · Exegy Market Data Architecture · IEEE 1588 Precision Time Protocol Specification · MiFID II Regulatory Technical Standards · Celoxica/Fixnetix Historical White Papers

## License

Educational use. Code examples provided as-is. Standards references are to publicly available NIST, IEEE, JEDEC, TCG, and industry documents.
