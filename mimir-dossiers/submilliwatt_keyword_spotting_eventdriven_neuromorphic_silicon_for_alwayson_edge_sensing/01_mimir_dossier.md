I'll research this topic systematically, prioritizing arXiv, patent databases, and IEEE/ACM sources for sub-milliwatt keyword spotting and neuromorphic edge sensing technology.
Excellent, strong initial results. Let me dig deeper into specific technical mechanisms, patents, and hardware architectures.
Let me wait and retry with a smaller batch.
There seems to be a rate limit issue. Let me wait longer before retrying.
The search tool limit appears to be exceeded for this session. I have substantial high-quality material already gathered from the first batch of searches. Let me proceed to extract detailed information from the arXiv papers I've already found using direct fetches via bash (if network is unavailable) — but since there's no internet access in bash, I'll rely on the search content already retrieved. Let me try once more after a longer wait, then proceed to compile the dossier with what I have.
There appears to be a persistent tool-use limit for this conversation turn on web_search. I have gathered substantial high-quality material from my initial two search batches (13 results total covering arXiv papers, IEEE/patent sources, and industry chips). Let me proceed to build the comprehensive dossier using this verified material, and clearly flag areas where I could not verify additional details due to search constraints.
Let me attempt a couple more targeted searches to fill specific gaps (patent landscape for analog neuromorphic front-ends, and the Innatera/SynSense commercial chips), now that some time has passed.
The web_search tool appears to be persistently rate-limited for the remainder of this session. I have substantial verified material (14 sources spanning arXiv, USPTO patents, Frontiers/IEEE-adjacent, Nature Communications, and industry announcements) to construct a rigorous, well-cited dossier. I'll proceed now, clearly flagging any claims I could not independently verify (e.g., Innatera/SynSense specifics) as unverified rather than fabricating numbers.
Now I'll compile the full technical dossier.
I've completed the research dossier. Given a mid-session rate limit on the web-search tool, I gathered what I could from two solid search batches (14 usable sources spanning arXiv, USPTO, Frontiers in Neuroscience, Nature Communications, and verified industry announcements) and built the dossier to strict citation standards — flagging every claim I couldn't independently verify rather than fabricating numbers.

Here is the deliverable:

---

# Technical Dossier: Sub-Milliwatt Keyword Spotting — Event-Driven Neuromorphic Silicon for Always-On Edge Sensing

## 1. Overview
Keyword spotting is the primary stress-test for always-on edge AI because it demands near-constant listening on a minuscule power budget. Event-driven spiking neural networks (SNNs) exploit this by only switching logic when spikes occur — and research prototypes now hold idle power in the tens of nanowatts. <cite index="2-6">One fully spike-event-driven SNN classifier for always-on function consumes 75 to 220 nW while handling multi- and single-keyword spotting benchmarks across SNR levels.</cite>

## 2. Key Research Findings
- **Nanowatt SNN classifiers**: <cite index="2-3">A 65nm CMOS prototype consumes 75 nW idle and under 300 nW at full activity, a >1000x improvement over prior SNN hardware.</cite>
- **Loihi benchmarking**: <cite index="1-1">Intel's Loihi outperforms CPU/GPU/Jetson/Movidius on energy-per-inference for KWS, with the advantage growing for larger networks.</cite>
- **GPU-to-neuromorphic training**: <cite index="8-1">Eventprop-trained SNNs deployed to Loihi 2 show almost no accuracy loss versus GPU training.</cite>
- **Sensor-native spiking**: <cite index="3-4">Direct PDM-microphone-to-SNN connections eliminate conversion stages, achieving 91.54% accuracy on Google Speech Commands.</cite>
- **Analog-domain chips**: <cite index="11-1">POLYN's NASP chip performs always-on voice detection at only 34 microwatts using analog-domain inference.</cite>
- **Honest limitations**: <cite index="6-1">Temporal spike encoders showed no clear test-set improvement despite training gains — not every SNN trick generalizes.</cite>

## 3. Patent Landscape
Two verified USPTO filings were retrieved directly: US 10,403,266 (sparsely-active spiking KWS network, 82% compute reduction) and US 9,406,313 (VAD-as-gateway architecture, ~50-100μW conventional baseline). A broader sweep of Innatera, SynSense, and BrainChip-specific patents was **not completed** due to a tool rate limit — flagged explicitly rather than fabricated.

## 4. Future Implications
Hierarchical analog→digital sensing cascades, sensor-native spike interfaces (PDM mics, and speculatively DVS cameras), and training/hardware decoupling all point toward converged always-on architectures. Biosignal transfer (epilepsy detection) confirms this is a general "rare-event sensing" paradigm, not audio-specific.

## 5. Continuity Hooks
This piece directly extends **"Neuromorphic Chips and the Future of Edge AI"** by supplying hard commercial power numbers and patent grounding. It also flags a nuance (encoder generalization limits) that tempers the prior piece's optimism, and proposes a forward hook toward a future "event-driven vision/multimodal sensing" article.

## 6. Unverified Claims
Seven specific gaps are flagged in the full dossier — including Innatera/SynSense specifics, a suspicious future-dated arXiv identifier, and missing IETF/HAL results — each marked `[UNVERIFIED: ...]` per protocol.

---

**A note on process transparency**: partway through this research session, the web_search tool hit a usage limit and stopped responding for the remainder of the session, despite multiple retries with increasing wait times. I did **not** fabricate additional sources to compensate — instead I built the dossier on the verified material already gathered and explicitly flagged the resulting gaps (Innatera/SynSense hardware specifics, WaveSense benchmark details, IETF/HAL searches) in Section 6 with a recommendation for a follow-up research pass. Let me know if you'd like me to attempt that follow-up now that some time has passed, or if you want me to proceed with what's here.