# ⬡ Modern SoC Design Presentation Series

Interactive slide decks covering modern System-on-Chip design end-to-end — from advanced packaging and chiplet architectures through memory hierarchies, on-chip interconnects, and silicon implementation.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/SoC/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory), then replace `OWNER` and `REPO` in the link above with your GitHub username and repository name.
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
| 07 | Security in SoC Design | — | Planned |
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

**The Memory Wall** — Why ML accelerators are memory-bandwidth-bound rather than compute-bound. Compute vs memory bandwidth scaling gap. LLM inference arithmetic intensity analysis. Roofline model visualisation.

**On-Chip SRAM** — 6T, 8T, HD, and LP bitcell architectures. Area and bandwidth tradeoffs. Voltage scaling challenges at N3/N5: read/write assist circuits (negative bitline, wordline boost, virtual VSS). SRAM compilers, multi-port cuts, and Monte Carlo yield characterisation.

**Cache Design** — Set-associativity, replacement policies, write-back vs write-through. ML workload cache behaviour: streaming weights, activation locality, KV-cache spill. Hardware cache vs software-managed scratchpad tradeoffs — why ML NPUs (Google TPU, Qualcomm, Apple ANE) favour scratchpad + DMA.

**The Memory Pyramid** — Five-level hierarchy from register file to CXL/NVMe. Capacity, bandwidth, and latency at each level. ML data mapping: hot activations → SPM, weight tiles → L2/LLC, full models → HBM, long-context KV → CXL.

**DRAM Architecture & Timing** — 1T1C bitcell, destructive read, refresh. Bank organisation, row buffer locality, bank-group parallelism. Key timing parameters (tRCD, CL, tRP, tRAS, tFAW, tREFI). ML memory controller scheduling policies.

**DDR5 & LPDDR5/6** — DDR5 sub-channel architecture, on-die ECC, DFE equalisation, 4800–8800 MT/s data rates. LPDDR5X/6 for edge AI (Apple M-series, Qualcomm Snapdragon). CAMM2 form factor, deep power-down modes. Why DDR falls short for large ML SoCs.

**GDDR7** — PAM4 signalling, 36 Gbps/pin, JEDEC JESD239. GDDR7 vs GDDR6X comparison. NVIDIA RTX 5090 1.79 TB/s configuration. Cost vs capacity tradeoff against HBM.

**HBM3 / HBM3E / HBM4** — 3D DRAM stacking via TSV, 1024-bit interface, pseudo-channel architecture. H100 (HBM3, 3.35 TB/s), H200 (HBM3E, 4.8 TB/s), AMD MI300X (HBM3, 5.2 TB/s, 192 GB). Thermal challenges, CoWoS-S/L interposer packaging. HBM4: 2048-bit interface, hybrid bonding, sub-1 pJ/bit target.

**CXL Memory** — CXL.mem protocol, Host-managed Device Memory. Type 2/3 device taxonomy. Memory disaggregation for TB-scale LLM deployment. CXL 3.1 fabric switches and peer-to-peer coherency. Linux NUMA integration and tiered memory (TPP).

**Roofline Model** — Arithmetic intensity, memory-bound vs compute-bound regimes, ridge point. Operating points for GEMM, GEMV, attention (prefill vs decode), elementwise ops. FlashAttention's roofline improvement. Batching as the mechanism to escape the memory-bound regime.

**Production Case Studies** — NVIDIA H100/H200, AMD MI300X 3.5D stacking, Google TPU v5p, Apple M3 Ultra unified memory architecture.

**Optimisation Techniques** — Quantisation (INT8/INT4), FlashAttention, KV-cache compression, paged attention, tensor parallelism, weight streaming, hardware prefetch, double buffering, near-memory compute, 2:4 structured sparsity.

---

## Presentation 04: High-Speed SerDes & I/O

23 interactive slides covering:

**The I/O Bandwidth Problem** — Why interconnect fabric is the dominant performance and power constraint in ML clusters. 26× HBM-to-PCIe bandwidth gap in the H100. The trajectory: 2–4× bandwidth per generation at constant pin count and falling pJ/bit.

**SerDes Architecture** — Complete TX/RX signal chain: fractional-N PLL, N:1 MUX serialiser, CML driver, channel, CTLE/DFE receiver, CDR, 1:N DEMUX deserialiser. Block diagram with signal flow. 112G PAM4 as state-of-art. Jitter budget: <3 ps rms at 1 UI = 9 ps.

**NRZ vs PAM4** — 1 bit/symbol NRZ vs 2 bits/symbol PAM4. Halved baud rate, 9.5 dB SNR penalty, one-third eye height. Gray coding for burst error limitation. FEC mandatory at PCIe 5+ for BER <10⁻¹². Eye diagram comparison.

**Equalisation** — Channel impairments: insertion loss (skin/dielectric), ISI, NEXT/FEXT crosstalk, reflections, deterministic + random jitter. TX FIR pre-emphasis (11-tap, PCIe 5), de-emphasis variants. CTLE: analogue high-pass, programmable peaking. DFE: post-cursor ISI cancellation, unrolled speculative H1, 8–16 taps for 112G PAM4. LMS/MMSE adaptation.

**Clock & Data Recovery** — PLL CDR vs Phase Interpolator CDR. Bang-bang phase detector: limit cycling, loop filter coefficients. Digital CDR for ADC-based PAM4 receivers. CDR loop block diagram.

**PCIe 5 & 6** — Full protocol stack: Transaction Layer (TLP types, AtomicOps), Data Link Layer (flow control credits, Ack/Nak), PHY logical (128b/130b → FLIT), PHY electrical. PCIe 6 FLIT mode: 256-byte fixed FLIT, RS FEC + CRC-6, BER <10⁻¹⁸, 128 GB/s ×16. Generation table (PCIe 3 through 7). LTSSM: Detect → Polling → Config → L0 → power states → Recovery. EQ Phase 1/2/3. ASPM L0s/L1 power management.

**UCIe** — Open die-to-die standard. Standard package (55 µm bump, 16 GT/s) vs advanced package (25 µm bump, 32 GT/s). 64-bit bus, forwarded clock, optional FEC. Bandwidth density: advanced ~10 Tb/s/mm — 20× denser than off-package PCIe 5. PCIe/CXL TLP tunnelled unchanged over D2D adapter. UCIe 2.0 additions.

**400G / 800G / 1.6T Ethernet** — PAM4 lane rate ladder. RS(544,514) KP4 FEC: 50–200 ns latency. RoCEv2 RDMA for GPU collective operations (NCCL all-reduce). SmartNIC/DPU offload (BlueField-3, Intel IPU). AI cluster scale-out: NVIDIA Quantum-X800, Google Jupiter fabric.

**Signal Integrity** — Loss budget breakdown: PCB trace (FR4 vs Megtron 7), via back-drilling at 56G+, connector, package. PCIe 5 budget ≤36 dB at 16 GHz Nyquist. S-parameters: S21, S11, NEXT/FEXT. COM (Channel Operating Margin) ≥3 dB. Jitter decomposition: TJ = DJ + Q×RJ; BERT bathtub curve; PRBS31/7 patterns. SI closure flow: pre-layout → post-layout EM extraction → IBIS-AMI co-simulation → VNA + BERT.

**Co-Packaged Optics (CPO)** — Pluggable module power overhead at 400G+. Silicon photonics PIC: MZM modulators, Ge photodetectors, WDM multiplexing. EIC flip-chipped on PIC at 50–100 µm bump pitch. Power comparison: pluggable 400G ~12 W vs CPO 400G ~3 W (~4× saving). CPO architecture diagram. Roadmap: 800G CPO 2025–26, 1.6T CPO 2027.

**Other I/O Standards** — NVLink 4 (900 GB/s, 18 links, NVSwitch 3.0 for 256-GPU fabrics). NVLink-C2C: Grace-Hopper 25 µm die-to-die. AMD xGMI3 / Infinity Fabric. USB4 v2.0 / Thunderbolt 5 (80 Gbps PAM4). CXL PHY on PCIe lanes.

**SerDes Power & Trends** — 56G NRZ: 5–8 pJ/bit; 112G PAM4: 3–5 pJ/bit; UCIe short-reach: 0.5–1 pJ/bit; CPO: 4–8 pJ/bit. 224G PAM4 in R&D. Process node scaling for mixed-signal design. Optical roadmap to 2027.

---

## Presentation 05: AI / ML Accelerator Architectures

22 interactive slides covering:

**Motivation** — End of Dennard scaling; ML workload characteristics (regularity, data reuse, sparsity, low-precision tolerance). Why DSAs deliver 10–1000× efficiency over CPUs.

**Roofline Model** — Arithmetic intensity (FLOP/byte); ridge point calculation for H100 SXM; positioning GEMM, convolution, attention, and GEMV on the roofline; design strategy for shifting workloads into the compute-bound regime.

**Compute Primitives** — Scalar MAC → SIMD/vector → tensor/matrix units. GEMM tiling strategy for fitting the memory hierarchy; output-stationary, weight-stationary, and K-dimension tiling.

**Systolic Arrays** — 2D PE mesh operating principle; weight-stationary, output-stationary, and row-stationary (TPU) dataflows. Google TPU v1 MXU deep dive: 256×256, INT8, 92 TOPS, 700 MHz. Illustrated 4×4 systolic array with data-flow annotations.

**Dataflow Architectures** — Control-flow vs dataflow execution model; spatial dataflow engines (Cerebras WSE-3, Groq LPU, SambaNova SN40L, Tenstorrent Blackhole); compiler-as-hardware paradigm.

**Mixed Precision** — Full numeric format table: FP64 through FP4/NF4/INT8. NVIDIA Tensor Core evolution (Volta → Ampere → Hopper → Blackwell). Automatic Mixed Precision (AMP) training with loss scaling and FP32 master weights.

**Sparsity** — Activation sparsity (ReLU), weight pruning, NVIDIA 2:4 structured sparsity with hardware decompression, sparse storage formats (CSR/BSR/COO), Flash Attention O(N) sparsity. Mixture-of-Experts as architecture-level sparsity (Mixtral 8×7B).

**Memory Hierarchy** — Register file → L1 SRAM → unified buffer → HBM → NVLink pool pyramid with bandwidth figures. On-chip SRAM sizing (6T SRAM density, area cost). Flash Attention algorithm-hardware co-design: O(N²) → O(N) HBM reads.

**Transformer Accelerators** — Prefill vs decode bottleneck analysis; KV cache sizing at scale; Multi-Query/Grouped Query Attention; PagedAttention (vLLM); NVIDIA Transformer Engine (FP8, WGMMA, TMA); prefill/decode disaggregated serving.

**Quantisation** — PTQ (symmetric/asymmetric/per-channel/per-group), QAT, GPTQ/AWQ INT4, QLoRA + NF4. Hardware support table across NVIDIA H100/B200, Google TPU v5, Apple ANE, Qualcomm HTP.

**GPU Architecture (H100)** — 80B transistors, 132 SMs, 4th-gen Tensor Cores, FP8 3,958 TFLOPS, HBM3 3.35 TB/s, 700W. Hopper innovations: Transformer Engine, WGMMA, TMA, DPX, NVLink Switch NVL72, Confidential Computing.

**Google TPU** — Full generation timeline TPU v1 → v6 Trillium; ICI 3D torus topology; OCS optical reconfigurable interconnect; SparseCore for embedding workloads.

**NPU SoC Integration** — Block diagram of NPU micro-architecture (DMA, MAC array, unified SRAM, activation unit). Flagship mobile NPU comparison table (Apple A18, Qualcomm SD Elite, Samsung Exynos 2500, MediaTek D9400, Google Tensor G4). Datacenter SoC NPUs: Intel Gaudi 3, AMD MI300X, AWS Trainium2, Microsoft Maia 100.

**Parallelism** — Data parallelism (DDP, ZeRO), Tensor parallelism (Megatron-LM column/row sharding), Pipeline parallelism (1F1B interleaved), Expert parallelism (MoE all-to-all), 3D parallelism combination.

**CNN Accelerators** — 7-loop nest tiling space; im2col, Winograd, FFT-based and depthwise-separable transforms. Line buffers, double buffering, kernel fusion. Edge ASIC comparison: Hailo-8, Kneron, Rockchip NPU, Arm Ethos-U85.

**Compiler Stack** — Framework → graph IR (torch.compile, XLA, MLIR) → optimisation passes (fusion, layout, quantisation, tiling) → backend codegen → runtime. MLIR dialect system. CUDA ecosystem: cuDNN, cuBLAS, CUTLASS, Triton, TensorRT. Inference runtimes: vLLM, SGLang, ONNX Runtime, llama.cpp.

**Power Efficiency** — TOPS/W comparison table (Ethos-U85 ~50 TOPS/W → H100 ~2.8 TOPS/W). Power breakdown in ML ASICs (MAC arrays 40–60%, SRAM 25–35%, HBM PHY 15–25%). Energy-reduction techniques: clock/power gating, DVFS, near-threshold computing, zero-skipping, data compression.

**Case Study: Blackwell B200** — 208B transistors, 2×462 mm² NV-HBI chiplet, FP4 native Tensor Cores (~18 PFLOPS sparse), HBM3e 192 GB / 8 TB/s, NVLink 5 1.8 TB/s, 1000W TDP. NVL72 rack: 72 B200 + 36 Grace CPUs; 1.4 exaFLOPS FP4.

**Case Study: Apple ANE** — Unified Memory Architecture; TOPS evolution A11 (0.6) → M4/A18 (38); CoreML stateful KV cache; MLX framework; on-device Apple Intelligence stack; speculative decoding on ANE.

**Emerging Directions** — Processing-in-Memory (Samsung HBM-PIM, SK Hynix AiM); analog in-memory compute (PCM, ReRAM — IBM 85 TOPS/W demo); photonic MAC (Lightmatter Passage); neuromorphic (Intel Loihi 2); Cerebras wafer-scale; 3D SRAM-on-logic stacking (TSMC SoIC, >100 TB/s bandwidth).

---

## Presentation 06: SoCs for ML Inference

24 interactive slides covering:

**Training vs Inference** — Fundamental differences in hardware requirements: forward-only pass, INT8/FP8 precision, KV-cache dominance, latency constraints, and continuous batching vs training's throughput focus. Why inference TOPS/W and memory bandwidth matter more than raw FLOPS.

**Deployment Landscape** — Four tiers: cloud/hyperscale (H100, MI300X, TPU v5p), on-premise workstation (RTX 4090, L40S), edge/endpoint (Apple M4, Snapdragon X Elite, Tensor G4), and MCU/TinyML (STM32, nRF, RP2350). Binding constraints at each tier.

**Quantisation Fundamentals** — Symmetric vs asymmetric, per-tensor vs per-channel vs per-group scaling. PTQ (GPTQ, AWQ, SmoothQuant) vs QAT. Precision format table: FP32 through FP4/NF4/INT8. NVIDIA Tensor Core evolution (Volta → Blackwell). Accuracy vs efficiency trade-offs.

**INT8 & INT4 Hardware Pipelines** — W8A8 MAC pipeline: INT8 × INT8 → INT32 accumulate → dequant to FP16. INT4 weight-only (W4A16): GPTQ second-order Hessian rounding, AWQ activation-aware scaling. 2× bandwidth saving at INT4. NVIDIA Tensor Core TOPS by format.

**LLM Inference Pipeline** — Prefill vs decode phases: prefill is compute-bound GEMM, decode is memory-bound GEMV. KV-cache sizing formula and worked examples (Llama 3.1 8B to 70B at various context lengths). GQA 8× reduction, MQA, PagedAttention, KV quantisation, Streaming LLM. Prefill/decode disaggregation.

**Memory Bandwidth — The Dominant Bottleneck** — Arithmetic intensity of inference operations: GEMV at 1–4 FLOP/B vs H100 ridge point 295 FLOP/B. Practical GPU utilisation in decode less than 5%. Escape strategies: batching, speculative decoding, INT4 weight compression, GQA, near-memory compute.

**NPU Micro-Architecture** — Block diagram: DMA engine, unified SRAM scratchpad, MAC array, activation unit, command processor. Scratchpad vs cache trade-offs. Double-buffering for DMA/compute overlap. Weight-stationary and output-stationary dataflows. Operator fusion pipeline.

**Sparsity Exploitation** — Activation sparsity (ReLU 50–80%), NVIDIA 2:4 structured sparsity with hardware decompression (2× TOPS), MoE architecture-level sparsity (Mixtral, DeepSeek-V3), FlashAttention block-sparse O(N) attention. Speculative decoding as temporal sparsity.

**On-Device LLM SoC Architecture** — Apple M-series unified memory blueprint: CPU + GPU + NPU share LPDDR5X with zero-copy coherence. Heterogeneous dispatch strategy per operation type. Apple Intelligence stateful KV-cache on ANE. MLX framework.

**Mobile & Edge NPU Comparison** — Detailed table: Apple A18 Pro / M4 (38 TOPS ANE), Qualcomm SD X Elite (75 TOPS Hexagon), SD 8 Gen 3, Samsung Exynos 2500, MediaTek D9400, Google Tensor G4. Memory bandwidth as the binding constraint for model size selection. INT4 as the practical edge sweet spot.

**Power Management for Inference** — NPU power breakdown: MAC array ~55%, SRAM ~25%, DMA/fabric ~12%. DVFS strategy: max frequency for compute-bound ops, reduced for memory-bound. Clock/power gating. Thermal management: TDP envelopes, throttling, PPEM scheduling. Energy minimisation: zero-skipping, data compression, near-threshold compute.

**Inference Compiler & Runtime Stack** — Full stack: PyTorch checkpoint → graph IR → optimisation passes → backend codegen → runtime. Key passes: operator fusion, layout transformation, constant folding, tiling & scheduling, kernel auto-selection. Inference runtimes compared: TensorRT, vLLM, SGLang, llama.cpp, CoreML, ONNX Runtime. Triton / OpenAI DSL.

**TinyML — MCU Inference** — Constraints: 256 KB SRAM, under 100 mW, years on coin cell. Architectures: MobileNetV3-tiny, DS-CNN, MCUNet, XNOR-Net. Arm Cortex-M55 + Ethos-U55/U65: 8 mW, continuous keyword spotting at under 0.1 mW. STM32N6, TFLite Micro, Edge Impulse.

**CNN Inference Optimisation** — im2col transform and implicit GEMM. Winograd convolution F(2,3): 9→4 MACs for 3×3 conv. Depthwise-separable convolution (MobileNetV2 8–9× reduction). 7-loop nest tiling, output-stationary and row-stationary dataflows, Halide/TVM/MLIR.

**Serving Systems & Batching** — Static vs continuous (iteration-level) batching: 2–3× utilisation improvement. PagedAttention: virtual KV pages, copy-on-write prefix sharing, 3× more concurrent requests. SGLang RadixAttention prefix caching. Latency vs throughput trade-off; disaggregated prefill/decode routing.

**Distributed Inference** — Tensor parallelism (Megatron-LM column/row): one all-reduce per transformer block. Pipeline parallelism: GPipe micro-batching, 1F1B interleaved, zero bubble for inference-only. Expert parallelism: MoE all-to-all dispatch. 3D parallelism at hyperscale.

**Case Study: NVIDIA H100 / H200** — H100 SXM5: 80B transistors, FP8 3,958 TOPS, HBM3 3.35 TB/s, 700 W TDP. Hopper innovations: Transformer Engine FP8, WGMMA, TMA, MIG. H200: 141 GB HBM3E, 4.8 TB/s, ~1.9× decode speedup. Llama 3.1 70B inference benchmarks.

**Case Study: Qualcomm Cloud AI 100 Ultra** — 870 INT8 TOPS, 128 MB on-chip SRAM, 136 GB LPDDR5X, 2.2 TB/s, 150 W. Inference-first architecture: no FP64 paths, compiler-driven static scheduling. LPDDR vs HBM trade-off analysis. Competitive comparison vs H100.

**Case Study: Groq LPU** — Tensor Streaming Processor: 230 MB on-chip SRAM, 80 TB/s SRAM bandwidth, no external memory, compiler-as-hardware paradigm. 750 tok/s batch=1 Llama 3 8B — 15× faster decode than H100 via SRAM residency. Trade-offs: model size ceiling, no dynamic shapes.

**Security in Inference SoCs** — Weight encryption (AES-256), secure boot, Secure Enclave. NVIDIA Confidential Computing / AMD SEV-SNP for cloud TEE inference. Inference-time attacks: prompt injection, model extraction, side-channel timing, data poisoning mitigations. On-device privacy and Apple Private Cloud Compute.

**Emerging Inference Techniques** — Speculative decoding deep dive: rejection sampling, Medusa/Eagle self-speculative heads, 2–3× speedup, roofline transformation. State Space Models (Mamba, Jamba): O(1) decode memory, no KV-cache. Analog in-memory compute (IBM PCM: 85 TOPS/W), photonic MAC (Lightmatter), 3D SRAM-on-logic.

**Power-Performance Trade-off Summary** — Comparison table across Ethos-U65 (~60 TOPS/W) through Groq TSP, AI 100 Ultra, H100/H200, MI300X, TPU v5p. Selection criteria: model size, latency, throughput, and TCO.

---

## Repository Structure

```
├── index.html                              ← Landing page (links to all presentations)
├── README.md                               ← This file
├── 01-soc-packaging/
│   └── index.html                          ← Reveal.js interactive slide deck
├── 02-on-chip-interconnect/
│   └── index.html                          ← Reveal.js interactive slide deck
├── 03-memory-hierarchy/
│   └── index.html                          ← Reveal.js interactive slide deck
├── 04-serdes-io/
│   └── index.html                          ← Reveal.js interactive slide deck
├── 05-ai-ml-accelerator-architectures/
│   └── index.html                          ← Reveal.js interactive slide deck
└── 06-socs-for-ml-inference/
    └── index.html                          ← Reveal.js interactive slide deck
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

TSMC 3DFabric (CoWoS, InFO, SoIC) · Intel Packaging Technology (EMIB, Foveros, Glass Substrates) · UCIe Consortium Specifications (1.0–3.0) · Yole Group, "State of Advanced Packaging 2024" · IEEE ECTC 2025 Proceedings · JEDEC HBM3/HBM3E Standards (JESD238) · JEDEC JESD239 (GDDR7) · AMD MI300X Architecture White Paper · NVIDIA Blackwell / H100 / H200 Architecture Overviews · PCI-SIG PCIe 5.0 / 6.0 Base Specifications · IEEE 802.3 (400G / 800G / 1.6T Ethernet) · CXL Consortium CXL 3.1 Specification · Lau, J.H., *Semiconductor Advanced Packaging*, Springer, 2021 · Patterson & Hennessy, *Computer Architecture*, 6th ed. · Razavi, B., *Design of Analog CMOS Integrated Circuits*, 2nd ed. · Dally & Poulton, *Digital Systems Engineering*, Cambridge · Williams et al., "Roofline," CACM 2009 · Jouppi, N. et al., "In-Datacenter Performance Analysis of a Tensor Processing Unit," ISCA 2017 · Chen, Y.-H. et al., "Eyeriss: An Energy-Efficient Reconfigurable Accelerator for DNNs," IEEE JSSC 2017 · Dao, T. et al., "FlashAttention-2," ICLR 2024 · Kwon, W. et al., "Efficient Memory Management for LLM Serving with PagedAttention," SOSP 2023 · Frantar, E. et al., "GPTQ: Accurate Post-Training Quantization for GPTs," ICLR 2023 · Dettmers, T. et al., "QLoRA: Efficient Finetuning of Quantized LLMs," NeurIPS 2023 · Vivet, P. et al., "Chiplet-based architecture for edge AI computing," IEEE JSSC, 2023

## License

Educational use. Code examples provided as-is. Standards references are to publicly available NIST, IEEE, JEDEC, PCI-SIG, and industry documents.
