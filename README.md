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
| 03 | Memory Hierarchy — SRAM to HBM | — | Planned |
| 04 | Power Management & Clocking | — | Planned |
| 05 | High-Speed SerDes & I/O | — | Planned |
| 06 | AI / ML Accelerator Architectures | — | Planned |
| 07 | Process Technology — FinFET to GAA | — | Planned |
| 08 | SoC Verification & Physical Design | — | Planned |
| 09 | Security in SoC Design | — | Planned |
| 10 | SoC Design for Automotive & Edge AI | — | Planned |
| 11 | CXL — Compute Express Link | — | Planned |

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

## Presentation 11: CXL — Compute Express Link *(Planned)*

Planned coverage:

**Fundamentals** — CXL motivation and market drivers. PCIe PHY reuse. CXL 1.1 → 2.0 → 3.0 → 3.1 specification evolution. Relationship to PCIe Gen5/Gen6.

**Protocol Sub-Protocols** — CXL.io (discovery, configuration, non-coherent DMA). CXL.cache (device-to-host coherency, snoop-based). CXL.mem (host-managed device memory, HDM-H/HDM-D). Protocol multiplexing over shared PHY.

**Device Types** — Type 1 (accelerator, CXL.cache only), Type 2 (accelerator + memory, CXL.cache + CXL.mem), Type 3 (memory expander, CXL.mem only). Use cases and design trade-offs for each.

**Memory Pooling & Fabric** — CXL 3.0+ fabric switches, Global Fabric Attached Memory (GFAM), peer-to-peer communication, back-invalidation snooping. Multi-host memory sharing and dynamic capacity provisioning.

**SoC Integration** — CXL controller IP integration with on-chip NoC (Arm CMN CXS bridge, custom implementations). Coherency domain boundaries. NUMA implications and OS/firmware support.

**Hardware Ecosystem** — CXL memory modules, CXL switches (Microchip, XConn), CXL-enabled CPUs (Intel Sapphire/Granite Rapids, AMD Genoa/Turin). Test and validation infrastructure.

---

```
├── index.html                     ← Landing page (links to all presentations)
├── README.md                      ← This file
├── 01-soc-packaging/
│   └── index.html                 ← Reveal.js interactive slide deck
└── 02-on-chip-interconnect/
    └── index.html                 ← Reveal.js interactive slide deck
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

TSMC 3DFabric (CoWoS, InFO, SoIC) · Intel Packaging Technology (EMIB, Foveros, Glass Substrates) · UCIe Consortium Specifications (1.0–3.0) · Yole Group, "State of Advanced Packaging 2024" · IEEE ECTC 2025 Proceedings · JEDEC HBM3/HBM3E Standards (JESD238) · AMD MI300X Architecture White Paper · NVIDIA Blackwell Architecture Overview · Lau, J.H., *Semiconductor Advanced Packaging*, Springer, 2021 · Vivet, P. et al., "Chiplet-based architecture for edge AI computing," IEEE JSSC, 2023

## License

Educational use. Code examples provided as-is. Standards references are to publicly available NIST, IEEE, JEDEC, and industry documents.
