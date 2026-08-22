I'll research this topic thoroughly, focusing on the mandatory technical sources. Let me start with parallel searches across arXiv, patents, and IEEE for FeFET logic-in-memory architectures.
Excellent starting point. Let me dig deeper into specific areas: patent landscape, majority gate/reconfigurable logic details, energy benchmarks, non-Boolean applications (HDC, CIM crossbars, security/PUFs), and reliability/scaling challenges.
Hitting a rate limit. Let me wait and retry with a single query at a time.
The code execution tool works; the search tool itself hit a limit. Let me wait a moment before retrying.
Let me try using the web_search tool directly at the top level instead of through code_execution, since the limit may be specific to nested tool calls within code execution.
The code_execution web_search seems to have hit a hard cap for this session. Let me use the standalone web_search tool call instead.
I've reached the search limit for this turn. Let me consolidate what I've already gathered — it's substantial and covers the core landscape well — and proceed to build the dossier, flagging areas where I'd want additional verification as unverified/needing follow-up rather than fabricating further citations.
Let me try one more targeted search to fill critical gaps (patent landscape specifics and the Nature Communications crossbar paper referenced in the HDC paper's bibliography), since the limit may reset.
Confirmed the search limit is exhausted for this turn. I have gathered substantial, high-quality material from mandatory sources (arXiv, IEEE Xplore, USPTO, ACM DL, plus ACS/Nature-affiliated venues). I'll now compile the dossier, being rigorous about citations and clearly flagging anything I could not verify (like the exact publication years for a few IEEE entries, and the crossbar paper only seen via secondary bibliography reference).
---

# Technical Dossier: Ferroelectric FET (FeFET) Memory as a Non-Volatile Logic-in-Memory Substrate

**Prepared for:** Project Isocline / Brian
**Classification:** Deep-dive technical research — pre-draft intelligence package
**Prior linked article:** *Ferroelectric HfO2 Memory: FeFET as a CMOS-Compatible Path to Embedded Non-Volatile Compute*

---

## 1. Overview

The prior Isocline piece established FeFETs as one member of a trio of HfO2-based non-volatile ferroelectric memory candidates (alongside FeRAM and ferroelectric tunnel junctions), distinguished by their CMOS compatibility and role in embedded non-volatile compute. This dossier extends that foundation into the specific architectural niche of **logic-in-memory (LiM)** — using the FeFET not merely as a *storage* element, but as the substrate on which Boolean and arithmetic logic is physically executed and non-volatilely retained, in situ, without invoking a separate ALU or shuttling data across a bus.

The core physical mechanism remains the same as previously covered: a ferroelectric layer (commonly doped HfO2 or Hf0.5Zr0.5O2, "HZO") integrated into the transistor gate stack exhibits remnant polarization that shifts the device's threshold voltage. 
Unlike conventional charge-based memory devices, FeFETs leverage the intrinsic polarization switching of ferroelectric materials integrated into the transistor gate stack to achieve non-volatile data storage.
 What the logic-in-memory research community has done is weaponize this bistability as a computational primitive: the polarization state doubles as both a stored bit and an operand in a logic evaluation, and the *result* of that evaluation is written back into the same physical ferroelectric domain — collapsing the traditional separation between "compute" and "store."

[SOURCE: Design of Ferroelectric Field-Effect Transistor (FeFET)-Based Computing-in-Memory Architecture with Energy-Efficient and Low Latency for Edge AI Computing | https://www.mdpi.com/2079-9292/15/4/841 | 2026]

This matters strategically because it directly attacks the von Neumann bottleneck at the device level rather than the architecture level. 
Emerging non-volatile memories are getting new interest in the system design community and are used to design logic-in-memory circuits and propose alternatives to von-Neuman architectures.
 
Hafnium oxide-based ferroelectric memory technology, fully compatible with CMOS technologies, is particularly interesting for logic-in-memory designs because this compatibility leads to various possibilities for fine-grain logic-in-memory applications where the memory-capable element is tightly integrated with the transistors in the system.


[SOURCE: FeFET based Logic-in-Memory: an overview | https://ieeexplore.ieee.org/document/9505078/ | IEEE Xplore]

---

## 2. Key Research Findings

### 2.1 Device-Level Foundations for Logic-Compatible FeFETs

Recent BEOL (back-end-of-line) integration work demonstrates that FeFETs can be fabricated at logic-compatible thermal budgets while retaining strong memory characteristics. 
Researchers fabricated IL-free FeFETs with 28nm channel length and 126nm width under a thermal budget below 400°C by integrating a 5nm thick Hf0.5Zr0.5O2 gate stack with an amorphous Indium Tungsten Oxide (IWO) semiconductor channel
, achieving 
a 1.2V memory window, a read current window of 10^5 for program and erase, write latency of 20ns, and read-after-write latency under 200ns
. This positions the device as viable BEOL-compatible embedded memory rather than a purely front-end concept — a prerequisite for monolithic 3D logic-in-memory stacking.

[SOURCE: Logic Compatible High-Performance Ferroelectric Transistor Memory | https://arxiv.org/abs/2105.11078 | 2021]

Retention remains a first-order physics challenge that any logic-in-memory design must engineer around. Foundational analysis identified that 
a memory FET based on the metal-ferroelectric-semiconductor gate stack could in principle be the building block of an ideal memory technology offering random access, high speed, low power, high density and nonvolatility, but in practice none of the reported ferroelectric memory transistors had achieved a retention time of more than a few days
, with the two dominant degradation mechanisms being depolarization field and finite gate leakage current. This is a direct continuity point with the prior article's framing of FeFET "merits and specific application boundaries" — logic-in-memory designs must be evaluated against this same retention ceiling, not a re-derived one.

[SOURCE: Why is nonvolatile ferroelectric memory field-effect transistor still elusive? | IEEE Xplore | Undated — flagged for year verification]

### 2.2 Boolean Logic Realized Natively in the FeFET

Multiple independent groups have now demonstrated complete Boolean logic families (AND/OR/NAND/NOR/XOR/XNOR) using the FeFET's polarization state as the logic variable itself, rather than as a passive lookup table entry read by external CMOS logic.

A 2024 HfO2-FeFET implementation achieved remarkably low switching energy: 
the fast switching speed and low power consumption of a HfO2-based FeFET enable the execution of Boolean logics with an ultralow energy of lower than 8 attojoules, representing a significant milestone in achieving aJ-level computing energy consumption
, with 
exceptional reliability, computing endurance exceeding 10^8 cycles and retention properties exceeding 1000 seconds
. Critically, this design stores the logic result *in situ* during computation — the definitional feature of logic-in-memory as opposed to a memory-adjacent ALU.

[SOURCE: Reconfigurable aJ-Level Ferroelectric Transistor-Based Boolean Logic for Logic-in-Memory | https://pubs.acs.org/doi/10.1021/acs.nanolett.4c02873 | 2024]

A complementary hybrid approach pairs the FeFET with RRAM to separate the roles of computation and reconfiguration: 
a novel 1FeFET-1RRAM design for logic-in-memory applications integrates FeFET and RRAM together, with FeFET performing non-volatile logic operations and RRAM handling logic reconfiguration; complete Boolean logic functions have been demonstrated with this unit and cascade circuits, exhibiting excellent speed and reliability performance
, making it 
a promising LiM solution for its superiority in area efficiency, power consumption, process simplicity, speed, reliability, and field reconfigurability
.

[SOURCE: Complete Reconfigurable Boolean Logic Gates Based on One FeFET-One RRAM Technology | https://www.researchgate.net/publication/374399689 | 2023]

Ferroelectric capacitor (FeCap) variants pursue a charge-domain route to the same end: 
a 1T2C FeCAP-based in-situ bitwise X(N)OR logic based on a charge-sharing function uses a 1T2C structure and a two-step write-back circuit to realize nondestructive reading with less complexity than prior work
. This confirms that the logic-in-memory concept generalizes across the ferroelectric device family (FeFET, FeCap, FTJ) referenced in the earlier Isocline article — each trades off area, energy, and cascadability differently.

[SOURCE: A 1T2C FeCAP-Based In-Situ Bitwise X(N)OR Logic Operation with Two-Step Write-Back Circuit for Accelerating Compute-In-Memory | https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8065609/ | Undated]

### 2.3 Sequential and Majority Logic — Beyond Combinational Gates

Beyond static Boolean gates, researchers have pushed FeFETs into sequential logic-in-memory territory. A van der Waals FeFET implementation shows area and power advantages over CMOS baselines: 
compared with conventional CMOS technology, which requires at least four transistors for AND or OR circuits, the proposed vdW FeFET-based S-LiM unit significantly reduces circuit complexity, minimizes static power dissipation, and uses fewer transistors
, and the devices are 
reconfigurable, allowing dynamic switching between logic functions such as AND and OR based on processing needs, suitable for edge computing and IoT applications like filtering and pattern recognition
.

[SOURCE: Reconfigurable Sequential-Logic-in-Memory Implementation Utilizing Ferroelectric Field-Effect Transistors | https://pubs.acs.org/doi/10.1021/acsnano.4c14062 | 2024]

Majority-gate logic — of particular interest because 3-input majority gates are a universal building block for adder/threshold logic and are difficult to implement compactly in standard CMOS — has been demonstrated directly using the FeFET's own program/erase asymmetry. 
A single-FDSOI FeFET-based 3-input majority gate leverages the drain-erase mechanism
, exploiting the fact that 
application of a positive voltage to the drain and source terminals can inhibit the gate program while application of a positive gate voltage can inhibit the drain erase scheme, thereby preserving the inherent polarization state of the FeFET
. This device-level asymmetry is what enables compact single-transistor majority logic rather than requiring multiple gates per majority function.

[SOURCE: Ferroelectric FET-based Logic-in-Memory Encoder for Hyperdimensional Computing | https://arxiv.org/abs/2512.20302 | 2025]

### 2.4 System-Level Applications: Hyperdimensional Computing

The most novel and forward-looking application uncovered in this research pass is FeFET LiM as an **encoder substrate for hyperdimensional (HD) computing**, an emerging brain-inspired computing paradigm well suited to non-volatile, massively parallel bitwise logic. 
Hyperdimensional computing encodes baseline information into large hypervectors via repeated Boolean operations, and while prior studies focused mostly on accelerating the HD search operation using TCAMs based on emerging non-volatile memories, this work proposes energy- and area-efficient single FDSOI FeFET-based logic-in-memory implementations of XOR and 3-input majority gates for N-gram HD encoders
. In a proof-of-concept spam-filtering accelerator, 
the proposed FeFET-based encoder outperforms prior emerging non-volatile memory-based implementations in terms of area and energy-efficiency while exhibiting a high classification accuracy of 91.38% on the SMS Spam Collection dataset
. This is a direct, citable bridge from raw device physics to an edge-AI-relevant system demonstration — valuable narrative material for a blog piece aiming to connect transistor-level innovation to real workloads.

[SOURCE: Ferroelectric FET-based Logic-in-Memory Encoder for Hyperdimensional Computing | https://arxiv.org/abs/2512.20302 | 2025]

An earlier related design generalized the FeFET CiM array beyond pure logic into a hybrid memory/compute fabric: 
this paper introduces a CiM architecture based on ferroelectric field effect transistors where the design can serve as a general purpose random access memory and can also perform Boolean operations (N)AND, (N)OR, X(N)OR, INV, as well as addition (ADD) between words in memory
.

[SOURCE: FeFET Based In-Memory Hyperdimensional Encoding Design | https://www.researchgate.net/publication/369074746 | 2023]

### 2.5 ADC-Free Architectures for Edge AI

A significant architectural finding addresses one of the biggest overhead sources in analog compute-in-memory: the ADC/DAC periphery. 
The von Neumann architecture faces severe bottlenecks in energy efficiency; Computing-in-Memory addresses this by performing computations within memory arrays, yet analog CiM solutions suffer from precision loss and high overhead from analog-to-digital and digital-to-analog converters
. The proposed FeFET digital-logic alternative 
is a novel ADC-free CiM architecture based on FeFETs, with NOR, NAND, and XNOR logic circuits storing weight vectors within FeFETs; compared with analog CiM circuits, the FeFETs-CiM circuits can reduce power consumption by 901.1 times and latency by 272.7 times
, extending to 
an application-specific FeFETs-CiM subtractor for k-nearest-neighbor distance calculation with energy consumption as low as 85.02 fJ/OP
. This is a strong quantitative data point for the blog's "why now" argument regarding edge AI economics.

[SOURCE: Design of Ferroelectric Field-Effect Transistor (FeFET)-Based Computing-in-Memory Architecture with Energy-Efficient and Low Latency for Edge AI Computing | https://www.mdpi.com/2079-9292/15/4/841 | 2026]

### 2.6 Beyond HfO2: 2D/vdW Reconfigurable FeFETs

While the prior article and much of the mainstream FeFET literature center on HfO2/HZO for CMOS-fab compatibility, an important complementary research vector uses van der Waals heterostructures for reconfigurable, multifunctional logic devices. 
2D van der Waals Re-FeFET devices exhibit groundbreaking potential for both More-than-Moore and beyond-Moore future electronics, particularly for energy-efficient in-memory computing and machine learning hardware, due to their multifunctionality and design compactness
. A specific implementation combines 
a homojunction of a 2D tungsten diselenide (WSe2) layer with independently controlled split-gate electrodes made of a ferroelectric 2D copper indium thiophosphate (CuInP2S6) layer, where controlling the state encoded in the Program Gate enables switching between p, n and ambipolar FeFET operating modes
. This is architecturally distinct from the HZO/silicon path and should be flagged in the blog as a parallel, non-CMOS-native research track rather than conflated with the mainline HfO2 story.

[SOURCE: Reconfigurable Multifunctional van der Waals Ferroelectric Devices and Logic Circuits | https://arxiv.org/abs/2310.14648 | 2023]
[SOURCE: Ferroelectric FETs-Based Nonvolatile Logic-in-Memory Circuits | https://www.researchgate.net/publication/328081773 | 2018]

Separately, alpha-In2Se3 ferroelectric-semiconductor channel devices have demonstrated multi-functional logic entirely within a single transistor: 
2D metal-oxide-semiconductor FETs with ferroelectric semiconducting alpha-In2Se3 as the channel can achieve logic, in-memory computing, and optoelectrical logic and non-volatile computing functionalities in a single device
, with 
AND and OR logic operations reaching current on/off ratios of about 5 orders of magnitude on two pre-set states, and non-volatile NOR/NAND operations with 3-4 orders of magnitude after removing voltage input
, plus 
fast operating speed of 10 microseconds and stable logic states after 1000 operation cycles
, and even 
optoelectrical logic OR and non-volatile implication (IMP) operations using voltage and photo as two input signals
.

[SOURCE: Logic and in-memory computing achieved in a single ferroelectric semiconductor transistor | https://www.sciencedirect.com/science/article/abs/pii/S2095927321004606 | 2021]

Samsung's stacked LG-FeFET work extends this into a genuine 3D in-memory computing array: 
a stacked ferroelectric memory array is comprised of laterally gated ferroelectric field-effect transistors, where the interlocking effect of alpha-In2Se3 is utilized to regulate channel conductance
, achieving 
a notably wide memory window, effective ferroelectric switching, long retention time over 3×10^4 seconds, and high endurance over 10^5 cycles
, and the team 
devised a 3D stacked structure and verified feasibility by performing multiply-accumulate operations in a two-tier stacked memory configuration
.

[SOURCE: Laterally gated ferroelectric field effect transistor (LG-FeFET) using alpha-In2Se3 for stacked in-memory computing array | https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10600126/ | 2023]

### 2.7 Materials Reliability Context

A 2025 review situates the whole field's device engineering trajectory: 
Hafnium oxide-based ferroelectric field-effect transistors are redefining non-volatile memory by enabling low-power, high-speed, and compatibility with advanced CMOS nodes, exploiting polarization-induced threshold voltage shifts in ultra-scaled gate stacks to achieve sub-5V write voltages and sub-10ns switching
, driven by 
recent advances in orthorhombic phase stabilization via dopant engineering, interfacial optimization, and defect dynamics that dictate performance variability
. This directly complements the prior article's material-platform framing and should be cited when discussing why HfO2 specifically (versus PZT or vdW ferroelectrics) remains the dominant industrial candidate.

[SOURCE: Hafnium oxide-based ferroelectric field effect transistors: From materials and reliability to applications in storage-class memory and in-memory computing | https://pubs.aip.org/aip/jap/article/138/1/010701 | 2025]

---

## 3. Patent Landscape

Patent coverage in this space splits into (a) foundational device patents predating the LiM application focus, and (b) application-specific circuit/architecture patents for in-memory processing.

**Foundational device patent:**

The present invention provides techniques for forming a ferroelectric gate field-effect transistor device and a non-volatile memory architecture employing such devices, where a semiconductor device comprises a field-effect transistor formed on a silicon substrate, including a drain region and a source region, and a ferroelectric gate field-effect transistor for storing a logical state of the semiconductor device.


[SOURCE: Non-volatile memory using ferroelectric gate field-effect transistors | USPTO Patent Full-Text Database (image-ppubs.uspto.gov/dirsearch-public) | Filing year unverified]

**Compute-in-memory circuit patent:**

Techniques are provided for using ferroelectric field-effect transistors as capacitive processing units for in-memory computing; an exemplary electronic circuit includes word lines, bit lines intersecting at grid points, and in-memory processing cells located at those grid points, each including switches coupling word and bit lines to a non-volatile tunable capacitor.
 The described method involves 
charging non-volatile tunable capacitors by turning on first switches coupling their electrodes to word lines held at voltages corresponding to a voltage vector, then discharging through second switches coupling to bit lines, integrating total charge with corresponding integrators
 — effectively a patented analog MAC (multiply-accumulate) primitive built on FeFET capacitive behavior.

[SOURCE: Using ferroelectric field-effect transistors (FeFETs) as capacitive processing units for in-memory computing | USPTO Patent Full-Text Database (image-ppubs.uspto.gov/dirsearch-public/print/downloadPdf/11688457) | Grant/publication year unverified — patent number 11,688,457]

**Commercial licensing structure:** The industrial patent picture is anchored by Ferroelectric Memory Company (FMC), a TU Dresden spinout. 
FMC acquired the patents and got the exclusive license of the two fundamental patents for FeFET applications from Technische Universität Dresden, and in 2017 licensed this to GlobalFoundries, with whom the company worked to develop the technology.
 
The company's FeFET technology addresses both embedded and standalone memory for compute and storage
, and per the CEO, 
the market's goal is to place the technology as close as possible to the CMOS logic node.
 This is directly relevant continuity material since the prior article's CMOS-compatibility argument is exactly what underlies FMC's commercialization thesis and GlobalFoundries partnership.

[SOURCE: FeFET Memory Startup gets $20m to Turn Logic into Memory Cells | https://www.eetimes.com/fefet-memory-startup-gets-20m-to-turn-logic-into-memory-cells/ | 2020]

**Note on patent landscape depth:** Time/tool constraints in this research pass limited full Google Patents / USPTO full-text searching to the two patents surfaced above. A dedicated follow-up patent-landscape pass (recommended before publication) should search Google Patents directly for assignees GlobalFoundries, Samsung, SK Hynix, Kioxia, Namlab/Ferroelectric Memory Company, and Purdue/Kaushik Roy-affiliated filings, using classification codes for ferroelectric memory (H01L 29/78391, G11C 11/22 family) to build a more exhaustive claim map.

[UNVERIFIED: Comprehensive patent count/claim landscape beyond the two patents cited above — flagged for dedicated patent-search follow-up]

---

## 4. Future Implications (Fact-Based Speculation)

Building on verified findings above, several strategic trajectories merit speculative-but-grounded discussion in the blog piece:

- **Sub-10-attojoule logic as a power wall solution for edge AI.** The demonstrated <8aJ Boolean logic energy [ACS Nano Letters, 2024, cited above] suggests FeFET LiM could target always-on edge inference tiers (wearables, implantables) where every picojoule of energy budget is contested — a natural complement to the embedded NVM narrative from the prior article, now extended from "storage that survives power loss" to "computation that survives power loss."

- **Hybrid FeFET-RRAM logic fabrics as a reconfigurability bridge.** The 1FeFET-1RRAM approach [ResearchGate, 2023, cited above] hints at a broader pattern: pairing a fast, low-energy, but harder-to-reconfigure ferroelectric logic element with a slower, more re-programmable resistive element for field reconfiguration. This modular pairing pattern could plausibly extend to FeFET+PCM or FeFET+MRAM hybrids, though no direct source was found confirming such hybrids in production research — this remains speculative.
  [UNVERIFIED: FeFET+PCM or FeFET+MRAM hybrid logic-in-memory hybrids as an extrapolated future pairing — no direct source found]

- **Hyperdimensional computing as a killer app for non-volatile bitwise logic.** Given that HD computing's core operations are Boolean and highly parallel, and FeFET LiM has already shown competitive results in this exact domain [arXiv 2512.20302, cited above], it is reasonable to speculate that FeFET-based HD accelerators could become a leading commercial use case for LiM before general-purpose CPU-replacement logic matures, since HD computing's error tolerance is more forgiving of FeFET variability than precision arithmetic would be.

- **3D monolithic stacking unlocking density-driven advantage.** The demonstrated BEOL compatibility [arXiv 2105.11078] combined with the stacked LG-FeFET array work [Nature Communications-associated, PMC10600126] together imply a plausible convergence path toward monolithic 3D logic-in-memory tiles where multiple FeFET logic/memory layers sit directly above CMOS logic — directly extending the "beyond von Neumann" thesis flagged as a why-it-matters continuity hook from the previous article.

- **Reliability engineering remains the gating factor.** The persistent retention/depolarization-field challenge identified in classic literature [IEEE, "Why is nonvolatile FeFET still elusive?"] has not been fully solved even in the most recent 2024-2025 demonstrations (retention figures cited above top out around 1000s–3×10^4s in lab devices, well short of the archetypal 10-year NVM requirement). Any blog claim of FeFET LiM being "production-ready" for long-term non-volatile logic storage should be qualified against this gap.

---

## 5. Continuity Hooks

**Backward link to prior article** (*Ferroelectric HfO2 Memory: FeFET as a CMOS-Compatible Path to Embedded Non-Volatile Compute*):
- The prior piece's framing of FeRAM/FeFET/FTJ as differentiated members of one material family is directly extended here: this dossier shows FeFETs specifically diverging toward *logic* execution, while FeCaps (closer to FeRAM's capacitor-based mechanism) pursue charge-domain logic-in-memory [PMC8065609], and FTJs remain comparatively absent from the LiM literature surfaced in this pass — a gap worth flagging explicitly in the new article as an open research question.
- The CMOS-compatibility thesis from the prior piece is the direct enabler of the commercial patent/licensing story here (FMC → GlobalFoundries) [EE Times, 2020].
- 
The materials-reliability review's framing of FeFETs "redefining non-volatile memory by enabling low-power, high-speed, and compatibility with advanced CMOS nodes"
 should be used as a bridging sentence between the two articles.

**Forward hooks for future Isocline articles:**
1. **Ferroelectric Tunnel Junctions (FTJs) for logic-in-memory** — notably underrepresented in this research pass; a dedicated FTJ-LiM deep dive would fill the gap left by FeFET/FeCap dominance here.
2. **Patent landscape deep-dive** — the abbreviated patent section above (Section 3) should be expanded into its own dedicated dossier given the commercial stakes (FMC/GlobalFoundries, Samsung's LG-FeFET, Purdue's FeCap/FeFET ML work).
3. **Hyperdimensional Computing as an architecture paradigm** — the HD computing use case surfaced here [arXiv 2512.20302] is substantial enough to warrant its own explainer article, independent of the device technology, examining why HD computing pairs unusually well with emerging non-volatile logic substrates (this dossier's FeFET findings plus prior TCAM-based approaches).
4. **The ADC/DAC overhead problem in analog CiM** — the 901.1x power reduction figure from digital FeFET-CiM [MDPI 2026] versus analog CiM opens a natural comparative article: "Analog vs. Digital Compute-in-Memory: Why the Periphery Matters More Than the Cell."
5. **2D/vdW ferroelectric devices as a parallel research track** — Section 2.6 material (WSe2/CuInP2S6, alpha-In2Se3) is substantial enough to support a dedicated "Beyond HfO2" article contrasting silicon-native and van der Waals ferroelectric approaches.

---

## 6. Unverified Claims

The following claims/data points were surfaced but could **not** be independently verified within this research pass and should either be excluded from the final article or explicitly caveated:

- `[UNVERIFIED: Exact publication/grant years for IEEE Xplore document 9505078 ("FeFET based Logic-in-Memory: an overview") and document 10332270 ("Ferro-Electronics: From Memory to Computing") — page metadata did not return clear year]`
- `[UNVERIFIED: Exact publication year for IEEE document 9936668 ("Logic and Memory Ferroelectric Field-Effect-Transistor Using Reversible and Irreversible Domain Wall Polarization")]`
- `[UNVERIFIED: USPTO patent 11,688,457 exact grant date — only PDF content retrieved, not the bibliographic filing/grant metadata]`
- `[UNVERIFIED: Foundational FeGFET patent (USPTO downloadPdf/6744087) filing/grant year and assignee]`
- `[UNVERIFIED: FMC's cited "$150 billion total available market in 2025" figure for embedded and standalone memory — this is a company/CEO market claim from an EE Times interview, not an independently audited market research figure, and should be attributed as such if used]`
- `[UNVERIFIED: Comprehensive patent landscape/claim count across major assignees (Samsung, SK Hynix, Kioxia, GlobalFoundries) — only two patents were directly retrieved in this pass; a dedicated Google Patents/USPTO full-text search is recommended before publication]`
- `[UNVERIFIED: The Nature Communications paper "First demonstration of in-memory computing crossbar using multi-level cell FeFET" (Soliman et al., 2023) was seen only as a bibliography citation within another paper's reference list, not accessed directly — claims about it should not be used until the primary source is retrieved]`
- `[UNVERIFIED: Speculative FeFET+PCM or FeFET+MRAM hybrid logic-in-memory pairings mentioned in Section 4 — this is forward-looking synthesis, not a claim found in any retrieved source]`

---

**Research methodology note:** This dossier prioritized arXiv, IEEE Xplore, ACM Digital Library, USPTO, and Nature-family sources per the mandatory source list. Web search tool access was rate-limited partway through this research session, which constrained the depth of the patent-landscape search (Section 3) and prevented verification of several bibliographic details (Section 6). A follow-up research pass focused specifically on Google Patents full-text search and IEEE Xplore's advanced search (for precise publication years) is recommended before this dossier is finalized into blog copy.