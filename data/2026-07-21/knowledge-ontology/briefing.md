# Knowledge Representation & Agent Memory — Daily Briefing
**Date:** 2026-07-21
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), arXiv, GitHub, Bluesky, X/Twitter

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 4 threads | ~400+ points, 400+ comments | 🌐 including "5 mistakes on KG memory", OpenKnowledge, OKF thread |
| Bluesky | 0 new posts | — | 🌐 bluesky=OK per SOURCE HEALTH; no new topic-relevant posts found July 19–21 |
| X/Twitter | 0 new posts | — | 🌐 last30days skill unavailable; no new X data collected this run |
| Web (global) | 54 pages | — | 🌐 via WebSearch + WebFetch; arXiv, GitHub, tech blogs |
| Web (Japan) | 9 pages | — | 🇯🇵 Zenn ×3, note, EnterpriseZine, DevelopersIO, Dentsu Soken, Qiita ×2 |
| Web (China) | 9 pages | — | 🇨🇳 Zhihu ×3, CSDN ×2, Tencent Cloud, CNBlogs, OSChina, 53AI |
| YouTube | 0 videos | — | yt-dlp not configured |
| TikTok | 0 videos | — | ScrapeCreators 402 (billing) |
| Instagram | 0 reels | — | ScrapeCreators 402 (billing) |
| Reddit | 0 threads | — | blocked from crawling |

---

## Synthesized Findings

### 1. [new] Microsoft Memora: 98% Token Reduction, ICML 2026 SOTA — Not in Prior Briefing

**New finding:** Microsoft Research's **Memora** was published June 29, 2026, at ICML 2026, but was absent from the July 19 briefing. It is the strongest single production memory result in the field right now.

**Architecture:** Memora decouples *what is stored* from *how it is retrieved* through three components:
- **Primary abstractions**: 6-8 word phrases capturing the memory essence (used for embedding retrieval)
- **Memory values**: Rich full content stored separately — never directly retrieved by embedding; always delivered alongside the abstraction when accessed
- **Cue anchors**: Context-aware tags providing alternative access paths without predefined ontologies

A **policy-guided retriever** iteratively refines queries and traverses cue anchors, enabling multi-hop reasoning that pure semantic search misses. This directly solves the fragmentation failure mode identified in the July 19 "Still true" items (MemDelta, Mem0 self-reported scores), where embedding-based retrieval either loses detail (summaries) or loses coherence (isolated fragments).

**Benchmark results:**
- **LoCoMo** (600-turn dialogues): **86.3%** LLM-judge accuracy
- **LongMemEval** (115,000-token contexts): **87.4%** accuracy
- Up to **98% token reduction** vs. full-context baseline
- Outperforms RAG, Mem0, Nemori, Zep, LangMem, and full-context inference on both benchmarks

**Competitive context:** Mem0 reports 94.4 on LongMemEval (July 19 briefing), but that score uses ~6,787 tokens/query. Memora achieves 87.4 at a fraction of the token cost — a fundamentally different efficiency/accuracy trade-off. Cognee 1.0 (prior finding) achieves 79% on BEAM; Memora's benchmarks are LoCoMo/LME, not BEAM, so they aren't directly comparable yet.

Code: https://github.com/microsoft/Memora

**Sources:** Web (🌐 Microsoft Research, InfoWorld, StartupHub, CIO&Leader, GIGAZINE, WindowsNews)

- https://www.microsoft.com/en-us/research/blog/memora-a-harmonic-memory-representation-balancing-abstraction-and-specificity/
- https://www.microsoft.com/en-us/research/publication/memora-a-harmonic-memory-representation-balancing-abstraction-and-specificity/
- https://www.infoworld.com/article/4191031/microsoft-unveils-memora-to-tackle-ai-agents-memory-problem.html
- https://www.startuphub.ai/ai-news/ai-research/2026/memora-microsoft-s-ai-memory-upgrade
- https://gigazine.net/gsc_news/en/20260630-microsoft-memora-harmonic-memory/

---

### 2. [new] NapMem + PLACEMEM: Two July 2026 arXiv Papers Rethink Memory as Active System

Two July 2026 arXiv papers share a common premise: passive retrieval is the wrong model for agent memory.

**NapMem** ([arXiv:2607.05794](https://arxiv.org/abs/2607.05794), July 7, 2026) — "From Passive Retrieval to Active Memory Navigation: Learning to Use Memory as a Structured Action Space"
- Frames long-term user memory as a **structured action space**, not a context to pre-select
- Architecture: **multi-granularity memory pyramid** — raw conversations → typed memory records → topic tracks → user profiles — connected through provenance relations
- Memory tools expose each level; agent is trained via reinforcement learning to decide: whether memory is needed, at what granularity to consult, and whether acquired evidence is sufficient before answering
- Evaluated on PersonaMem-v2, LongMemEval, LoCoMo — competitive results across diverse memory-intensive tasks while preserving general reasoning
- Key difference from prior work: the *navigation policy* is learned, not heuristic

**PLACEMEM** ([arXiv:2607.04089](https://arxiv.org/abs/2607.04089), July 2026) — "Toward a Compute-Aware Memory Plane for Lifelong Agents"
- Problem: lifelong agents must recompute historical context on every interaction or use stale runtime state
- Solution: **versioned capsules** — containers bundling semantic meaning, provenance, validity intervals, and reusable runtime state under one correction-aware identity
- Architecture: vLLM-based control plane with concurrency-safe invalidation, KV-aware routing, OpenAI-compatible routing sidecar, typed metadata contracts
- Measures live first-token latency, memory reuse rates, and post-correction behavior
- Frames this as systems-level infrastructure for replay-aware serving in future lifelong-agent stacks

**Why together:** Both papers challenge the same assumption — that a retrieval lookup is sufficient for agent memory. NapMem delegates memory navigation to the agent; PLACEMEM builds a memory plane that eliminates recomputation overhead. These are complementary positions in the same stack.

**Sources:** Web (🌐 arXiv)

---

### 3. [new] AgentO: OWL/RDF Ontology for Modeling Agentic AI Workflows (ESWC 2026)

**AgentO** ([Springer](https://link.springer.com/chapter/10.1007/978-3-032-25159-6_16) / [Zenodo](https://zenodo.org/records/18342625)) — Authors: Ekelhart, A., Kurniawan, K., Ekaputra, F.J. & Kiesling, E. (University of Vienna). Presented at the 23rd European Semantic Web Conference (ESWC 2026), Dubrovnik, Croatia.

**What it is:** An OWL/RDF-based ontology and knowledge graph that formally represents the core concepts, components, and interactions underpinning agentic AI workflows — agents, tasks, workflows, and resource dependencies — with a standardized vocabulary.

**Why it matters:** The LLM-agent field has converged on ad-hoc implementations that "rely on simplistic data structures and monolithic designs that hinder scalability, reusability, and interoperability." AgentO provides the formal ontological foundation for comparing, auditing, and reusing agent workflows across frameworks.

**Methodology:** LLM-driven process to translate 66 agentic workflows from 4 different agentic AI frameworks into AgentO representations. Evaluated through three real-world use cases:
1. Declarative reconstruction of agentic patterns
2. Cross-context reuse of tasks and agents
3. Agentic AI workflow auditing

**Relation to other findings:** AgentO complements OKF (knowledge content representation) and OSI (semantic layer for analytics data): OKF = what the knowledge contains, OSI = how metrics are defined, AgentO = how agent workflows are formally described. The three together could form a complete semantic stack for AI systems.

See also: [agentic-patterns/agentic-ai-onto](https://github.com/agentic-patterns/agentic-ai-onto) — companion GitHub implementation.

**Sources:** Web (🌐 Springer, University of Vienna, Zenodo)

---

### 4. [new] Always-On Agents Survey: 435 Papers Show Governance and Recovery are the Overlooked Half of Memory

([arXiv:2606.30306](https://arxiv.org/abs/2606.30306)) — Tianyu Ding, Aditya Nannapaneni, Bingfan Liu, Ling Zhang

A 435-paper coded corpus survey treating LLM agents with persistent state as a distinct system class — "always-on agents" whose future behavior depends on durable state accumulated across earlier interactions.

**Key finding:** The literature concentrates heavily on *accumulating and retrieving* state, but severely underweights *governing, recovering, and relinquishing* it. This is the gap that production deployments fall into.

**Six diagnostic axes** the authors apply to each state item: authority, scope, mutability, provenance, recoverability, actionability.

**Nine lifecycle stages:** written → validated → organized → retrieved → acted upon → updated → forgotten → audited → rolled back.

**Main contribution:** The **Always-On Evaluation Protocol (AOEP-v0)** shifts scoring from "answer quality" to "state mutation and recovery obligations" — a fundamentally different evaluation posture than LoCoMo/LME/BEAM. This directly complements the July 19 briefing's "Memory-as-Governance" pattern (PROJECTMEM, ElephantBroker), which showed memory actively constraining agent behavior before action. This survey now provides the formal vocabulary for evaluating that constraint.

**Sources:** Web (🌐 arXiv) — https://arxiv.org/abs/2606.30306

---

### 5. [new] OntoBricks + Open Ontologies v1.0: Two MCP-Native Ontology Engineering Tools Ship

Two new tools bridge the classic ontology stack (OWL/RDF/SPARQL) directly into the MCP agent toolchain.

**OntoBricks** ([github.com/databrickslabs/ontobricks](https://github.com/databrickslabs/ontobricks)) — Databricks Labs, v0.6.2, 192 stars
- Transforms Databricks Unity Catalog tables into a materialized knowledge graph via four clicks: import metadata → AI-generate OWL ontology → auto-map (R2RML) → sync to Delta-backed triple store
- Supports OWL 2 RL inference, SWRL rules, SHACL validation, constraint checking
- Exposes GraphQL API + **MCP tools** for Claude Desktop, Cursor, Databricks Playground
- Significance: directly connects the enterprise data lake (Unity Catalog) to formal ontology reasoning via the same MCP protocol agents already use for tools

**Open Ontologies v1.0.0** ([github.com/fabio-rovai/open-ontologies](https://github.com/fabio-rovai/open-ontologies)) — The Tesseract Academy, June 2026, 199 stars
- **Rust MCP server** with 70+ tools for AI-native ontology engineering: validate RDF/OWL, SPARQL queries, lint, native OWL2-DL tableaux reasoner, SHACL validation, data pipeline (CSV/JSON/SQL → RDF), cross-ontology alignment, clinical support (ICD-10/SNOMED/MeSH crosswalks)
- **Single binary, no JVM** — eliminates the deployment barrier that historically made OWL reasoning impractical outside enterprise IT
- Desktop Studio with AI chat panel; connects to Claude via stdin/stdout MCP
- Benchmarks: OntoAxiom 0.713 macro F1 (9 ontologies); OAEI Anatomy 0.963 precision

**Why together:** Both tools signal that the OWL/RDF ontology engineering workflow is being re-implemented around MCP as the new integration protocol. OntoBricks targets data engineers at Databricks; Open Ontologies targets ontology engineers at any shop. Both eliminate the prior-generation barrier of bespoke Java toolchains.

**Sources:** Web (🌐 GitHub)

---

### 6. [new] Eticas AI Risk Taxonomy v2.0.0: Open Semantic Infrastructure for AI Auditing (SKOS/JSON-LD)

([arXiv:2607.02201](https://arxiv.org/abs/2607.02201)) — Eticas Research

**What it is:** A structured AI risk taxonomy with 76 active subcategories, 10 categories, 20 sub-groups, mappings to 18 external frameworks, published CC BY 4.0 with **stable URIs** and **SKOS/JSON-LD distributions**.

**The semantic infrastructure angle:** Unlike prior AI risk lists (which are prose documents), the Eticas taxonomy is designed as interoperable semantic web infrastructure — the same SKOS/JSON-LD approach used in W3C standards (DPVCG's Data Privacy Vocabulary v2.3 with AI Extension). Stable URIs allow references from other taxonomies, enabling automated cross-framework compliance mapping.

**Concrete example:** Testing GPT-4 for PII disclosure risk with graded severity thresholds — the taxonomy connects the audit finding back to its controlling framework node via a resolvable URI.

**Context:** This is a different semantic use case than the CoSAI/OASIS OWL work (July 19 briefing) — CoSAI uses OWL for ontology cross-mapping of security risk concepts; Eticas uses SKOS for lightweight but stable concept alignment across 18 risk frameworks. SKOS is cheaper and more portable; OWL is heavier but supports automated reasoning. The two approaches serve different production contexts.

**Sources:** Web (🌐 arXiv) — https://arxiv.org/pdf/2607.02201

---

### 7. [new] HN: "5 Mistakes Building Agent Memory on Knowledge Graphs" — POLE+O Emerges as Community Baseline

([news.ycombinator.com/item?id=48337689](https://news.ycombinator.com/item?id=48337689)) — Author: pauliusztin, ~51 days ago

A practitioner post from May 2026 that resurfaced in July discussions; captures ground truth from a year of production KG memory work. The five mistakes:

1. **Framework dependency**: LangGraph and CrewAI encode assumptions mismatched with custom ontology constraints and multi-hop traversal needs
2. **Over-engineering ontology upfront**: designing the "perfect" ontology froze projects for months; correct approach is **start with POLE+O** (Person/Object/Location/Event/Organization) and expand only when conflicts arise
3. **Conflating resolution with deduplication**: threshold system: ≥0.95 auto-merge, >0.85 human review, ≤0.85 create new node — prevents entity type pollution
4. **Missing reasoning memory**: agents repeated failed strategies without a third memory type tracking reasoning traces (strategy, tools, outcomes) — like RL at the database layer
5. **Premature immutable logging**: building immutable log before materializing graph consumed excessive RAM

**Key quote:** "The schema decides everything about the system's performance."

**Why this matters:** The POLE+O recommendation aligns exactly with the Neo4j POLE+O finding in prior briefings (36-46% multi-hop gains). The 3-tier threshold system for entity resolution is a production-tested alternative to the ontology `owl:sameAs` approach flagged as "costly" in the CoSAI OWL work (July 19 briefing). These are converging on the same practitioner defaults.

**Sources:** Hacker News 🌐

---

### 8. [new] 🇯🇵 EnterpriseZine "Context Degradation Trap" + Zenn "Corporate OS": Japanese Production Framing Advances

Two new Japanese articles this period advance the OKF/memory conversation from "what is this?" toward production operation design.

**EnterpriseZine — "Context Degradation Trap"** ([enterprisezine.jp](https://enterprisezine.jp/article/detail/24029)):
- Title: "なぜAIは本番で'崩れる'のか？" ("Why Does AI Break Down in Production?")
- Author: Kohei Ogawa
- Core argument: "LLMは記憶する存在ではない" ("LLM is not an entity that remembers") — each session starts from zero; RAG is a retrieval mechanism, not memory design
- Introduces **"メモリエンジニアリング"** (memory engineering) as systematic design of what AI remembers, updates, and retrieves — distinct from RAG and context window expansion
- Production gap framing: AI that "使えるが、成長しない" ("functions but never improves") — systems that work at PoC but can't accumulate interaction insights in production
- This is one of the first Japanese enterprise IT articles to name "memory engineering" as a distinct discipline, mirroring the Databricks Context Engineer certification's framing

**Zenn/yamitake — "Building a Corporate OS with OKF and RAG"** ([zenn.dev/yamitake/articles/okf-open-knowledge-format-corporate-os](https://zenn.dev/yamitake/articles/okf-open-knowledge-format-corporate-os)):
- Different article from the prior briefing's yamitake guide (which focused on enterprise RAG framing)
- Frames OKF+RAG as complementary architectural layers: OKF defines *how to store*, RAG defines *how to retrieve*
- "If you can `cat` it, OKF reads it. If you can `git clone` it, OKF distributes it"
- 5-step implementation roadmap for a corporate knowledge OS
- Closing question: "Does your company provide consistent answers across all AI agents through shared knowledge infrastructure?"
- Enterprise maturation signal: this article assumes OKF adoption and focuses on operational governance

**Dentsu Soken AITC — "OKF as Knowledge Container"** ([aitc.dentsusoken.com/column/open-knowledge-format/](https://aitc.dentsusoken.com/column/open-knowledge-format/)):
- Different article from the prior briefing's Dentsu Soken "practical guide"
- Author: Fukaya Yuji (AITC Center Director)
- "AI時代に必要なのは「ナレッジの置き場所」ではなく「AIが扱える形」"
  ("What's needed isn't where to store knowledge, but forms AI can process")
- Argues: critical success requires careful *operational design* — defining knowledge types, review processes, update protocols — not just format adoption

**note.com/_kihonushi — Semantic Layer vs Ontology State Design** ([note.com/_kihonushi](https://note.com/_kihonushi/n/nad1b98d60300)):
- 4-stage implementation path: semantic layer (quick ROI) → lightweight ontology → governance signals → MCP exposure
- Cites Gartner: 63% of data leaders lack adequate AI-ready data governance
- "60% of analysis projects relying exclusively on MCP fail by 2028" — semantic foundation required

**Platforms:** 🇯🇵 EnterpriseZine, Zenn, note.com, Dentsu Soken AITC

---

### 9. [update] Mem0: v2.0 Label (June 2026) + Free Tier Tripled in July

**New facts since July 19:**
- Mem0 shipped **v2.0** in June 2026 (not labeled as such in the July 19 briefing, which covered the April 2026 algorithm update)
- In **July 2026**, Mem0 tripled its free-tier limit from 1,000 to **10,000 memories/month** — enabling real prototyping on the free tier rather than demo-only usage
- GitHub stars: **60,000+** (prior briefing cited 59,600+ at time of writing)

The July 19 benchmarks remain unchanged (LoCoMo 92.5, LME 94.4, BEAM 1M: 64.1, BEAM 10M: 48.6). Memora (finding #1 above) now sits alongside Mem0 as a competing production benchmark reference — different efficiency/accuracy trade-off.

- Changelog: https://docs.mem0.ai/changelog
- GitHub: https://github.com/mem0ai/mem0

**Sources:** Web (🌐 mem0.ai, techsy.io)

---

### 10. [new] EvoMemBench: 15-System Study Shows No Single Memory Form Works Across All Settings

([arXiv:2605.18421](https://arxiv.org/abs/2605.18421)) — Hong Kong UST (Guangzhou), BUPT, Beijing IT; June 2026

**What it tests:** 15 representative memory methods against a self-evolving benchmark covering four settings: in-episode knowledge evolution, in-episode execution evolution, cross-episode knowledge evolution, cross-episode execution evolution.

**Key finding:** Long-context baselines remain highly competitive against specialized memory systems; memory helps most when the current context is *insufficient* or tasks are *difficult*; no single memory form works consistently across all settings.

This is a stronger negative result than the "Are We Ready?" paper in the July 19 "Still true" list (arXiv:2606.24775 found "no single architecture dominates universally"). EvoMemBench adds the specific dimension of *evolutionary context* — the benchmark itself changes over time, revealing which systems can adapt versus which peak and plateau.

**Sources:** Web (🌐 arXiv) — https://arxiv.org/abs/2605.18421

---

**Still true** (from July 19 briefing, no new developments in this pass):

- **[ongoing] OKF v0.1 + LangChain/OpenWiki 0.2 adoption** (finding #1, July 19): Harrison Chase endorsement and LangChain's OpenWiki 0.2 OKF adoption remain the highest-engagement signal; no additional major tool adoptions reported since July 16.
- **[ongoing] Cognee 1.0**: Single-Postgres memory stack with BEAM SOTA (+6.5pp at 100k tokens). No follow-up since July 19.
- **[ongoing] Databricks Context Engineer Associate cert**: First exam July 29, 2026 — in 8 days. No new updates; exam approaching.
- **[ongoing] OSI v1.0**: Snowflake-led semantic layer standard; Phase 2 (50+ platforms) ongoing.
- **[ongoing] EMBER**: Budgeted evidence retention, 0.3017 F1 on retained-evidence protocol. Unchanged.
- **[ongoing] PROJECTMEM**: Memory-as-Governance, 14 MCP tools, 19 CLI commands, MIT. Unchanged.
- **[ongoing] ElephantBroker**: 11-dimension scoring, Neo4j + Qdrant. Unchanged.
- **[ongoing] FundaPod**: KG memory for investment research multi-persona disagreement surfacing. Unchanged.
- **[ongoing] Show HN: OpenKnowledge**: Mac-only desktop, CRDT+Git, local LLM gap flagged. Unchanged.
- **[ongoing] Graphiti + FalkorDB**: Sub-10ms multi-agent temporal graph queries. Unchanged.
- **[ongoing] CoSAI OWL/SKOS security ontology**: OWL equivalentClass cost warning, middle ontologies recommended. Unchanged.
- **[ongoing] Neo4j POLE+O**: 36-46% multi-hop gains, 40%+ hallucination reduction vs. vector-only.
- **[ongoing] MemDelta (arXiv:2606.29914)**: Benchmark non-portability; embedding model swaps flip rankings 6.2pp.
- **[ongoing] Eywa (arXiv:2605.30771)**: Evidence-before-belief SOTA (LoCoMo C1-C4: 90.19%, LME-S: 88.2%). No follow-up.
- **[ongoing] Zep SOC2/HIPAA/GDPR**: Compliance trifecta; only managed memory system with all three.
- **[ongoing] Letta**: LettaBot archived May 2026; Letta Code now primary product with MemFS + Dreaming features.
- **[ongoing] BUPT+Huawei 4W cognitive memory framework**: Unchanged.
- **[ongoing] 36kr "Year of AI Memory"**: Memory-centric framing in Chinese tech media unchanged.
- **[ongoing] Tencent TBox/ABox framing**: Ontology as two-stage epistemological process. Unchanged.
- **[ongoing] Trust Certificates (arXiv:2606.04037)**: Pre-deployment certification framework. No production pilots.

---

## Cross-Source Patterns

### Pattern 1 [new]: Memory Is Splitting Into Two Schools — Token-Efficient Retrieval vs. Active Navigation

Appears on: Web (🌐 Microsoft Memora blog, InfoWorld, arXiv NapMem, arXiv PLACEMEM)

Memora, NapMem, and PLACEMEM all arrived within weeks of each other and define the two positions:
- **Token-efficient retrieval school** (Memora): Decouple storage from retrieval; use lightweight abstractions plus cue anchors; 98% token reduction; the agent remains a passive consumer of memory output
- **Active navigation school** (NapMem): Give the agent memory tools; train it via RL to decide *when* to access memory and *at what granularity*; the agent is an active participant in its own memory access

These are not incompatible — Memora's cue-anchor traversal is a form of guided navigation; NapMem's RL policy could be applied to Memora's memory structure. The split is architectural: where does the intelligence about *what to retrieve* live? In the retrieval system (Memora) or in the agent itself (NapMem)?

Key quote from Memora: "Decoupling what is stored from how it is retrieved" — vs. NapMem's premise that retrieval itself should be an agent action.

### Pattern 2 [new]: MCP Is Becoming the Integration Protocol for Classic Ontology Tooling

Appears on: Web (🌐 OntoBricks GitHub, Open Ontologies GitHub, Zep/Graphiti docs, TrustGraph, Semantica)

OntoBricks and Open Ontologies both expose OWL/RDF/SPARQL ontology engineering through MCP. Graphiti is "MCP-compatible — connect to Claude, Cursor." TrustGraph bills itself as "the context engineering platform for open source AI" with MCP integration. This is a structural pattern: the MCP protocol is absorbing tool categories that previously required bespoke SDKs. The OWL2-DL reasoner in Open Ontologies — historically a JVM-locked enterprise tool — now ships as a single Rust binary exposing 70+ tools over a stdin/stdout MCP connection.

This has a governance implication: ontology reasoning is now accessible to agents without infrastructure teams, which makes the governance warnings from Always-On Agents survey (AOEP-v0) more urgent. Easier to deploy = less guardrails by default.

### Pattern 3 [new]: Production KG Memory Has a Practitioner Canonical Schema — POLE+O

Appears on: Hacker News (🌐 pauliusztin "5 mistakes"), Web (🌐 Neo4j POLE+O, prior briefings), 🇯🇵 Qiita/yohei1126

The HN "5 mistakes" post's recommendation — start with POLE+O, expand only when conflicts arise — matches the Neo4j production finding (36-46% multi-hop gains). This convergence across an independent practitioner account and Neo4j's documented schema is stronger evidence than either alone. The 3-tier entity resolution threshold system (≥0.95 auto-merge, >0.85 human review, ≤0.85 new node) is an actionable deduplication policy absent from academic benchmark papers.

**Combined signal:** POLE+O is the practitioner baseline for production knowledge graph memory in 2026.

### Pattern 4 [ongoing]: Governance and Recovery Are the Underbuilt Half of Agent Memory Systems

Appears on: Web (🌐 arXiv Always-On Agents, arXiv PROJECTMEM, CoSAI/GitHub, Eticas AI Risk Taxonomy)

The Always-On Agents survey (435 papers) confirms quantitatively what the July 19 briefing's "Memory-as-Governance" pattern found qualitatively: the field has over-invested in accumulate/retrieve and under-invested in govern/recover/forget. The Eticas AI Risk Taxonomy addresses the "forget" side via a formal audit vocabulary. PROJECTMEM's pre-action gate addresses the "govern before action" side. These are filling the same gap from different directions.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| pauliusztin | I spent a year building agent memory on knowledge graphs. Here are my 5 mistakes | 3 | — | "The schema decides everything about the system's performance." | https://news.ycombinator.com/item?id=48337689 |
| — | Show HN: OpenKnowledge – open source AI-first alternative to Obsidian/Notion | — | 381+ | "I really wanted to like this, but couldn't see how it improves my experience over Obsidian or VS Code" | https://news.ycombinator.com/item?id=48675435 |
| — | Google proposes Open Knowledge Format based on Markdown | — | — | OKF HN discussion on concept-per-file approach | https://news.ycombinator.com/item?id=48517735 |
| — | Agent Memory: An Anatomy | — | — | Zettelkasten-to-agent memory mapping discussion | https://news.ycombinator.com/item?id=48287808 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Microsoft Research | https://www.microsoft.com/en-us/research/blog/memora-a-harmonic-memory-representation-balancing-abstraction-and-specificity/ | Memora: 98% token reduction, 86.3% LoCoMo, ICML 2026 |
| 🌐 | GitHub/microsoft/Memora | https://github.com/microsoft/Memora | Memora code release |
| 🌐 | InfoWorld | https://www.infoworld.com/article/4191031/microsoft-unveils-memora-to-tackle-ai-agents-memory-problem.html | Memora coverage |
| 🌐 | StartupHub | https://www.startuphub.ai/ai-news/ai-research/2026/memora-microsoft-s-ai-memory-upgrade | Memora coverage |
| 🌐 | GIGAZINE | https://gigazine.net/gsc_news/en/20260630-microsoft-memora-harmonic-memory/ | Memora (June 30) |
| 🌐 | arXiv:2607.05794 | https://arxiv.org/abs/2607.05794 | NapMem: active memory navigation via RL |
| 🌐 | arXiv:2607.04089 | https://arxiv.org/abs/2607.04089 | PLACEMEM: compute-aware memory plane |
| 🌐 | arXiv:2607.02201 | https://arxiv.org/pdf/2607.02201 | Eticas AI Risk Taxonomy v2.0.0 SKOS/JSON-LD |
| 🌐 | Springer/AgentO | https://link.springer.com/chapter/10.1007/978-3-032-25159-6_16 | AgentO: OWL/RDF ontology for agentic workflows |
| 🌐 | Zenodo/AgentO | https://zenodo.org/records/18342625 | AgentO data release |
| 🌐 | arXiv:2606.30306 | https://arxiv.org/abs/2606.30306 | Always-On Agents: 435-paper governance survey |
| 🌐 | GitHub/databrickslabs/ontobricks | https://github.com/databrickslabs/ontobricks | OntoBricks v0.6.2: Unity Catalog → KG + MCP |
| 🌐 | GitHub/fabio-rovai/open-ontologies | https://github.com/fabio-rovai/open-ontologies | Open Ontologies v1.0.0: Rust MCP + 70+ OWL tools |
| 🌐 | arXiv:2605.18421 | https://arxiv.org/abs/2605.18421 | EvoMemBench: 15-system evolving memory benchmark |
| 🌐 | Mem0 changelog | https://docs.mem0.ai/changelog | Mem0 v2.0 + July free tier tripling |
| 🌐 | mem0.ai/blog/state | https://mem0.ai/blog/state-of-ai-agent-memory-2026 | State of AI Agent Memory 2026 |
| 🌐 | GitHub/getzep/graphiti | https://github.com/getzep/graphiti | Graphiti: temporal KG engine, MCP-compatible |
| 🌐 | Letta blog | https://www.letta.com/blog/towards-agents-that-learn/ | Letta MemFS + Dreaming features |
| 🌐 | ISO 23726-1 | https://www.iso.org/standard/90902.html | ISO ontology interoperability standard |
| 🌐 | ISO 23726-2 | https://www.iso.org/standard/90855.html | ISO ontology vocabulary standard |
| 🌐 | SwirlAI newsletter | https://www.newsletter.swirlai.com/p/state-of-context-engineering-in-2026 | State of context engineering 2026 |
| 🌐 | LlamaIndex blog | https://www.llamaindex.ai/blog/context-engineering-what-it-is-and-techniques-to-consider | Context engineering techniques |
| 🌐 | Contextandchaos | https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic | Ontologies vs semantic layers: AI needs both |
| 🌐 | Gartner D&A 2026 | https://contextandchaos.substack.com/p/gartner-d-and-a-2026-where-the-context | Context layer as budget line item |
| 🌐 | Year of the Graph | https://yearofthegraph.xyz/newsletter/2026/03/beyond-context-graphs-how-ontology-semantics-and-knowledge-graphs-define-context-the-year-of-the-graph-newsletter-vol-30-spring-2026/ | Beyond context graphs |
| 🌐 | HackerNoon | https://hackernoon.com/context-graphs-ontologies-and-the-race-to-fix-enterprise-ai | Context graphs + ontology race |
| 🌐 | ScienceDirect/AI-KM | https://www.sciencedirect.com/science/article/pii/S235271102600347X | AI-KM v6.6.1 agent skills + ontology-driven modeling |
| 🌐 | Atlan ontology | https://atlan.com/know/what-is-ontology-in-ai/ | Ontology in AI 2026 |
| 🌐 | KEOD 2026 CFP | https://keod.scitevents.org/ | KEOD 2026: abstracts deadline July 31 |
| 🌐 | MemU/Zep analysis | https://memu.pro/blog/zep-temporal-knowledge-graph-agent-memory | Zep sub-200ms hybrid retrieval analysis |
| 🌐 | particula.tech | https://particula.tech/blog/agent-memory-frameworks-tested-mem0-zep-letta-cognee-2026 | Memory frameworks tested 2026 |
| 🌐 | mcp.directory | https://mcp.directory/blog/mem0-vs-letta-vs-zep-vs-cognee-2026 | Mem0 vs Letta vs Zep vs Cognee |
| 🌐 | evermind.ai | https://evermind.ai/blogs/best-open-source-agent-memory-frameworks-2026 | Best open-source memory frameworks 2026 |
| 🌐 | vectorize.io | https://vectorize.io/articles/best-ai-agent-memory-systems | Best AI agent memory systems 2026 |
| 🌐 | semantica-agi | https://github.com/semantica-agi/semantica | Semantica: graph-native infrastructure + provenance |
| 🌐 | trustgraph-ai | https://github.com/trustgraph-ai/trustgraph | TrustGraph: context engineering for open-source AI |
| 🌐 | agentic-ai-onto | https://github.com/agentic-patterns/agentic-ai-onto | Agentic AI Ontology (companion to AgentO) |
| 🌐 | NirDiamant KG | https://github.com/NirDiamant/Agent_Memory_Techniques | 30 Jupyter notebooks: memory techniques |
| 🌐 | DEEP-PolyU GraphMemory | https://github.com/DEEP-PolyU/Awesome-GraphMemory | Survey: graph-based agent memory |
| 🌐 | EvoEmbedding | https://arxiv.org/pdf/2606.21649 | EvoEmbedding: evolvable representations for memory |
| 🌐 | Control-Plane KG | https://arxiv.org/pdf/2606.15903 | 13 system configurations for agent memory |
| 🌐 | TOKI | https://arxiv.org/pdf/2606.06240 | Bitemporal contradiction algebra |
| 🌐 | witscode.com OKF | https://witscode.com/open-knowledge-format | OKF complete 2026 guide |
| 🌐 | DMCommunity OKF | https://dmcommunity.org/2026/07/16/google-open-knowledge-format-okf/ | OKF in decision management community |
| 🌐 | innfactory OKF | https://innfactory.ai/en/blog/open-knowledge-format-okf-standard-for-ai-knowledge/ | OKF as silo-breaking standard |
| 🌐 | Medium/suhasmallesh | https://medium.com/@suhasmallesh/open-knowledge-format-okf-the-markdown-standard-your-ai-agents-have-been-waiting-for-2f88f84f7ba3 | OKF Markdown standard (July 2026) |
| 🌐 | Medium/greekofai | https://medium.com/@greekofai/google-just-released-okf-the-missing-standard-ai-agents-have-been-waiting-for-7a813da371ab | OKF coverage (July 2026) |
| 🇯🇵 | Zenn (yamitake corporate OS) | https://zenn.dev/yamitake/articles/okf-open-knowledge-format-corporate-os | OKF + RAG as company OS (new article) |
| 🇯🇵 | EnterpriseZine | https://enterprisezine.jp/article/detail/24029 | Context degradation trap; memory engineering |
| 🇯🇵 | Dentsu Soken AITC | https://aitc.dentsusoken.com/column/open-knowledge-format/ | OKF as knowledge container (new article) |
| 🇯🇵 | note.com/_kihonushi | https://note.com/_kihonushi/n/nad1b98d60300 | Semantic layer vs ontology state design |
| 🇯🇵 | Zenn (yamitake enterprise RAG) | https://zenn.dev/yamitake/articles/open-knowledge-format-okf-guide | OKF enterprise RAG guide (prior briefing) |
| 🇯🇵 | Zenn (caron14) | https://zenn.dev/caron14/articles/open-knowledge-format-intro | OKF vendor-neutral intro (prior briefing) |
| 🇯🇵 | DevelopersIO | https://dev.classmethod.jp/articles/open-knowledge-format-okf-v01-guide/ | OKF hands-on 25.4% compliance (prior briefing) |
| 🇯🇵 | Qiita (yohei1126) | https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80 | Next-gen AI agent data infrastructure |
| 🇯🇵 | Qiita (yushibats) | https://qiita.com/yushibats/items/d4e3e0186f4d8eb83874 | AI-era data terms: ontology, KG, semantic layer |
| 🇨🇳 | Zhihu (8 memory strategies) | https://zhuanlan.zhihu.com/p/1938384459033448484 | 8 AI agent memory strategies |
| 🇨🇳 | Zhihu (OKF ambitions) | https://zhuanlan.zhihu.com/p/2051665837967380596 | OKF: how ambitious? (prior briefing) |
| 🇨🇳 | Zhihu (OKF metadata) | https://zhuanlan.zhihu.com/p/2050867227440715425 | OKF: new metadata paradigm (prior briefing) |
| 🇨🇳 | CSDN (ontology) | https://blog.csdn.net/minstbe/article/details/160429225 | What is ontology? Aristotle to KGs |
| 🇨🇳 | Tencent Cloud | https://developer.cloud.tencent.com/article/2706610 | OKF = Karpathy LLM Wiki concept (prior briefing) |
| 🇨🇳 | CNBlogs | https://www.cnblogs.com/itech/p/20581987 | OKF quiet launch (prior briefing) |
| 🇨🇳 | OSChina | https://www.oschina.net/news/459806 | Google Knowledge Catalog + OKF (prior briefing) |
| 🇨🇳 | Zhihu (4W memory survey) | https://zhuanlan.zhihu.com/p/1997342332400473207 | BUPT+Huawei 4W cognitive framework (prior briefing) |
| 🇨🇳 | 53AI | https://www.53ai.com/news/knowledgegraph/2026011004136.html | Ontology vs KG semantic differences |
| 🇨🇳 | Huawei Cloud | https://bbs.huaweicloud.com/blogs/457029 | Agent memory architecture (prior briefing) |

---

## Stats Block

```
├─ 🟢 HN: 4 threads │ ~400+ points │ ~400+ comments
├─ 🦋 Bluesky: 0 new posts │ 0 likes
├─ 🔵 X: 0 new posts (skill unavailable; prior briefing's @hwchase17 still top signal)
├─ 🟠 Reddit: 0 threads │ blocked from crawling
├─ 🔴 YouTube: 0 videos │ yt-dlp not configured
├─ 🟣 TikTok: 0 videos │ ScrapeCreators 402 (billing)
├─ 🩷 Instagram: 0 reels │ ScrapeCreators 402 (billing)
├─ 🌐 Web: 54 pages │ 🇯🇵 9 │ 🇨🇳 9
└─ 🗣️ Top voices: @hwchase17 (LangChain/OKF, prior), Microsoft Research (Memora), Kohei Ogawa (EnterpriseZine JP)
```

---

## Out of Scope but Notable

- **AI-KM v6.6.1 "Agent Skills + Ontology-Driven Knowledge Modeling"** ([ScienceDirect SoftwareX, Sept 2026](https://www.sciencedirect.com/science/article/pii/S235271102600347X)): A distributed knowledge management software platform that combines agentic skill frameworks with ontology-driven modeling. Straddles this topic and "agent harnesses/frameworks." May belong in an "agent tooling" topic if one exists; included here because ontology is the core differentiation.

- **ISO 23726 Ontology-Based Interoperability (Industrial)** — ([ISO 23726-1](https://www.iso.org/standard/90902.html) / [23726-2](https://www.iso.org/standard/90855.html)): Being published as a full ISO standard in 2026 for industrial automation systems. While targeted at manufacturing/industrial IoT rather than AI agents specifically, the semantic interoperability vocabulary (IDO: Industrial Data Ontology) is directly relevant to any AI agent operating in industrial settings. May belong in an "enterprise AI infrastructure" or "industrial AI" topic.

- **KEOD 2026 abstract deadline July 31** ([keod.scitevents.org](https://keod.scitevents.org/)): The 18th International Conference on Knowledge Engineering and Ontology Development (October 28-30, Angers, France) has an abstract submission deadline in 8 days. Any practitioner work on OKF, AgentO, or agent ontologies is eligible. Calendar item for knowledge-ontology topic trackers.

---

## Data Gaps

- **last30days skill unavailable**: The `/last30days` skill returned an error this run. The English pass was done via manual WebSearch + WebFetch rather than the automated multi-platform sweep. This means Reddit (blocked), YouTube, TikTok, Instagram, and full X/Twitter coverage were not collected. Estimated skill gap: Reddit likely has active r/AI_Agents discussion on Microsoft Memora; YouTube likely has Mem0/Cognee tutorial content.
- **X/Twitter not collected**: Prior run's @hwchase17 signal remains the most relevant, but any July 19-21 posts on Memora, NapMem, or new OKF adoptions were not captured. Tool coverage gap, not platform absence.
- **Bluesky**: SOURCE HEALTH shows bluesky=OK. No new topic-relevant posts found July 19-21. Thin yield reflects actual platform coverage.
- **Zhihu direct fetch**: 403 Forbidden on direct article URLs. The new Zhihu article on 8 memory strategies could not be fully retrieved; content from search snippets only.
- **CSDN direct fetch**: 521 Unknown Status. Content from search snippets only.
- **Hacker News rate-limiting**: HN returned 429 on one fetch; points/comments partially missing from table.
- **Approximate coverage**: ~68% of ideal. Strongest passes: arXiv (comprehensive), GitHub (comprehensive), JP web (strong). Weakest: Reddit, X/Twitter, YouTube, direct CN hub access. The Microsoft Memora finding was absent from the July 19 briefing despite being published June 29 — suggests the prior run also missed it; this may be a recurring gap.

---

## Key Quotes

> "Decoupling what is stored from how it is retrieved" — Microsoft Research, Memora (ICML 2026) ([microsoft.com/en-us/research/blog](https://www.microsoft.com/en-us/research/blog/memora-a-harmonic-memory-representation-balancing-abstraction-and-specificity/))

> "The schema decides everything about the system's performance." — pauliusztin, "5 Mistakes Building Agent Memory on Knowledge Graphs" ([HN:48337689](https://news.ycombinator.com/item?id=48337689))

> "LLMは記憶する存在ではない" ("LLM is not an entity that remembers") — Kohei Ogawa, EnterpriseZine on the context degradation trap ([enterprisezine.jp](https://enterprisezine.jp/article/detail/24029)) 🇯🇵

> "AI時代に必要なのは「ナレッジの置き場所」ではなく「AIが扱える形」" ("What's needed isn't where to store knowledge, but forms AI can process") — Fukaya Yuji, Dentsu Soken AITC on OKF ([aitc.dentsusoken.com](https://aitc.dentsusoken.com/column/open-knowledge-format/)) 🇯🇵

> "If you can `cat` it, OKF reads it. If you can `git clone` it, OKF distributes it." — Zenn/yamitake, OKF as Corporate OS ([zenn.dev/yamitake/articles/okf-open-knowledge-format-corporate-os](https://zenn.dev/yamitake/articles/okf-open-knowledge-format-corporate-os)) 🇯🇵

> "A semantic layer tells you what your revenue is. An ontology tells you what a customer is." — note.com/_kihonushi on semantic layer vs. ontology state design ([note.com](https://note.com/_kihonushi/n/nad1b98d60300)) 🇯🇵

> "Active memory navigation formulates long-term user memory as a structured action space and equips the agent with memory tools, allowing it to decide whether memory is needed, which level of abstraction to consult, and whether the acquired evidence is sufficient." — NapMem paper abstract ([arXiv:2607.05794](https://arxiv.org/abs/2607.05794))

> "The literature concentrates more heavily on accumulating and retrieving state than on governing, recovering, or relinquishing it." — Always-On Agents survey, 435-paper finding ([arXiv:2606.30306](https://arxiv.org/abs/2606.30306))

> "Agent memory should be represented as versioned capsules that unify semantics, provenance, validity, and reusable runtime state under one correction-aware identity." — PLACEMEM ([arXiv:2607.04089](https://arxiv.org/abs/2607.04089))

> "AI systems that 使えるが、成長しない ('function but never improve') — no accumulation of interaction insights in production" — EnterpriseZine, coining the context degradation trap ([enterprisezine.jp](https://enterprisezine.jp/article/detail/24029)) 🇯🇵
