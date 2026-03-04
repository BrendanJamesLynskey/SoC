# ⬡ Modern SoC Design Presentation Series

Interactive slide decks covering modern System-on-Chip design end-to-end — from advanced packaging and chiplet architectures through memory hierarchies, on-chip interconnects, and silicon implementation.

## ▶ [Open the Series Landing Page](https://brendanjameslynskey.github.io/SoC/)

> **Setup:** Enable GitHub Pages (Settings → Pages → Deploy from `main` branch, `/ (root)` directory).
>
> Alternatively, open `index.html` locally in any browser — all presentations work offline after first load.

---

## Presentations

| # | Topic | Slides | Status |
| --- | --- | --- | --- |
| 01 | Modern SoC Packaging | 18 | ✅ Complete |
| 02 | On-Chip Interconnect & NoC Design | 20 | ✅ Complete |
| 03 | Memory Hierarchy in ML Accelerator SoCs | 23 | ✅ Complete |
| 04 | High-Speed SerDes & I/O | 23 | ✅ Complete |
| 05 | AI / ML Accelerator Architectures | — | Planned |
| 06 | SoCs for ML Inference | — | Planned |
| 07 | Security in SoC Design | — | Planned |
| 08 | CXL in ML Accelerator SoCs | — | Planned |
| 09 | Modern ML Accelerator SoC Power Delivery | — | Planned |
| 10 | Modern SoC Verification | — | Planned |
| 11 | Power Management in ML Accelerator SoCs | — | Planned |
| 12 | Thermal Management in ML Accelerator SoCs | — | Planned |
| 13 | Clocks and Resets in ML Accelerator SoCs | — | Planned |

---

## Presentation 04: High-Speed SerDes & I/O

23 interactive slides covering:

**The I/O Bandwidth Problem** — Why interconnect is the dominant bottleneck in ML clusters. 26× HBM-to-PCIe bandwidth gap in the H100. The historical trajectory: 2–4× bandwidth per generation at constant pin count and falling pJ/bit.

**SerDes Architecture** — Complete TX/RX signal chain: fractional-N PLL, N:1 MUX serialiser, CML driver, channel, CTLE/DFE receiver, CDR, 1:N DEMUX. 112G PAM4 as state-of-art. Jitter budget at 1 UI = 9 ps.

**NRZ vs PAM4** — 1 bit/symbol vs 2 bits/symbol. Halved baud rate, 9.5 dB SNR penalty, one-third eye height. Gray coding, mandatory FEC at PCIe 5+. SVG eye diagram comparison.

**Equalisation** — Channel impairments: insertion loss, ISI, crosstalk, jitter. TX FIR pre-emphasis (11 taps, PCIe 5). CTLE analogue high-pass peaking. DFE: unrolled speculative H1, 8–16 taps for 112G PAM4. LMS/MMSE adaptation.

**Clock & Data Recovery** — PLL CDR vs Phase Interpolator CDR. Bang-bang phase detector, limit cycling, loop filter. Digital CDR for ADC-based PAM4. CDR loop block diagram.

**PCIe 5 & 6** — Full protocol stack: TL (TLP types, AtomicOp), DLL (credits, Ack/Nak), PHY logical (128b/130b → FLIT), PHY electrical. PCIe 6 FLIT mode: 256-byte FLIT, RS FEC + CRC-6, BER <10⁻¹⁸, 128 GB/s ×16. LTSSM with EQ phases and ASPM power states.

**UCIe** — Open die-to-die standard. Standard (55 µm bump) vs advanced (25 µm bump) packages. 10+ Tb/s/mm bandwidth density — 20× denser than PCIe 5 off-package. PCIe/CXL TLP tunnelled unchanged. UCIe 2.0 additions.

**400G / 800G / 1.6T Ethernet** — PAM4 lane rates, KP4 FEC, RoCEv2 RDMA for NCCL all-reduce, SmartNIC/DPU offload, AI cluster networking (Quantum-X800, Google Jupiter).

**Signal Integrity** — Loss budget (PCB, via, connector, package). PCIe 5 ≤36 dB limit at 16 GHz. S-parameters, COM metric. Jitter decomposition (TJ = DJ + Q×RJ). SI closure flow: pre-layout → EM extraction → IBIS-AMI → VNA + BERT.

**Co-Packaged Optics** — Pluggable module power problem at 400G+. Silicon photonics PIC: MZM, Ge PD, WDM. EIC flip-chipped on PIC. 4× power saving vs pluggable. Roadmap: 800G CPO 2025–26, 1.6T CPO 2027.

**Other I/O** — NVLink 4 (900 GB/s), NVLink-C2C, AMD xGMI3, USB4 v2.0 / Thunderbolt 5, CXL PHY on PCIe lanes.

**SerDes Power & Trends** — 56G NRZ 5–8 pJ/bit → 112G PAM4 3–5 pJ/bit → UCIe 0.5–1 pJ/bit. 224G PAM4 R&D. Node scaling for mixed-signal design. Optical roadmap.

---

## Presentation 03: Memory Hierarchy in ML Accelerator SoCs

23 slides — SRAM bitcells · Cache design · DRAM fundamentals · DDR5 · LPDDR5/6 · GDDR7 · HBM3/3E/4 · CXL memory · Roofline model

## Presentation 02: On-Chip Interconnect & NoC Design

20 slides — Bus vs crossbar · AXI/ACE · CHI · NoC topologies · Cache coherency · QoS & arbitration · AMD Infinity Fabric · Intel mesh

## Presentation 01: Modern SoC Packaging

18 slides — Wire bond · Flip-chip · Fan-out · CoWoS · EMIB · 3D stacking (SoIC/Foveros) · Chiplets · UCIe · Thermal & power delivery · Case studies

---

```
├── index.html                     ← Landing page
├── README.md                      ← This file
├── 01-soc-packaging/index.html
├── 02-on-chip-interconnect/index.html
├── 03-memory-hierarchy/index.html
└── 04-serdes-io/index.html
```

Each presentation is a single self-contained `index.html`. No build step — CDN-hosted Reveal.js and Google Fonts.

## Slide Controls

| Action | Key |
| --- | --- |
| Next / Previous | `→` `←` or swipe |
| Overview | `Esc` |
| Fullscreen | `F` |
| Export to PDF | append `?print-pdf` to URL |

## Technology

[Reveal.js 4.6](https://revealjs.com) · highlight.js (Monokai) · Playfair Display + DM Sans + JetBrains Mono

## License

Educational use. Standards references are to publicly available PCI-SIG, JEDEC, IEEE, UCIe Consortium, and industry documents.
