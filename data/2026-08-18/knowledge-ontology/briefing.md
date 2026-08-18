# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-08-18
**Query type:** GENERAL
**Sources:** Hacker News, arXiv, Web (Global), Web (Japan), Web (China), Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 new threads | 381 pts (OpenKnowledge) | HN:48675435, HN:49272286, HN:49319814 |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; no on-topic signal |
| Web (global) | 55 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita ×3, Zenn ×2, note.com ×1, jisaku.com ×1 |
| Web (China) | 10 pages | — | 🇨🇳 Zhihu ×2, CSDN ×1, Tencent Cloud ×2, 53AI ×1, aibase ×2, pedaily ×1, 36kr ×1 |

---

## Synthesized Findings

### 1. [new] MemoraX AI — "Endogenous Memory" Paradigm, 3 Rounds in 5 Months (Aug 12, 2026)
🇨🇳 China

**Claim:** Chinese memory-infrastructure startup MemoraX AI completed a Seed++ round (>100M CNY total across 3 rounds, 5 months) on Aug 12, led by former Huawei Noah's Ark Lab director; its "endogenous memory" thesis — build memory directly into the model via Agentic RL, not external RAG — proposes a paradigm distinct from all currently shipping memory systems.
**Evidence:**
- **Rounds:** April seed ($10M USD); May Seed+; Aug 12 Seed++ (hundreds of millions CNY)
- **Lead investors (Aug):** Beiyang Begonia Fund, Shangshi Capital, Ren'ai Capital; existing investors continuing
- **Founder:** Hao Jianye — director Huawei Noah's Ark Lab / Decision Reasoning Lab; now Tianjin University professor
- **Core algorithm:** ReMix (ICLR 2026 accepted) — AI autonomously decides retain/forget/recall
- **Endogenous memory:** Agentic RL trains the model to manage its own memory internally; contrasts with Mem0/Zep/Graphiti style (external KG + vector retrieval)
- **Market framing (Zhihu):** "AI失忆症" (AI amnesia syndrome) = hundred-billion-level market; 3 rounds / 5 months signals high investor confidence
- **URLs:** https://news.pedaily.cn/202608/567590.shtml, https://news.qq.com/rain/a/20260812A04CHV00, https://eu.36kr.com/en/p/3785834045583875, https://news.aibase.com/news/28163, https://zhuanlan.zhihu.com/p/2035765768013468400

### 2. [new] MemTools — Interoperable Agent Memory Research Framework (arXiv:2607.21404, July 23, 2026)
🌐 Global (CAS/BAAI, China)

**Claim:** Chinese Academy of Sciences + Beijing Academy of Artificial Intelligence release MemTools, a research framework that decouples memory components from deployment environments, enabling interchangeable assembly across heterogeneous memory systems — addressing architectural fragmentation that makes comparing memory approaches impossible.
**Evidence:**
- **Authors:** Zhao, Chen, Liang, He, Wang, Zhao, Liu (CAS/UCAS/BAAI/Zhongguancun Institute)
- **Problem diagnosed:** Implementations couple different lifecycle stages; evaluation logic entangled with specific datasets; no interoperability between symbolic/neural/multimodal memory types
- **Solution:** Standardizes memory lifecycle via declarative data contracts; separates benchmark datasets from execution protocols; unified interface for all memory types
- **Significance:** First framework proposing a "memory interoperability layer" — analogous to what MCP does for tool access, but for memory components
- **URLs:** https://arxiv.org/abs/2607.21404, https://arxiv.org/html/2607.21404v1

### 3. [new] arXiv:2607.26520 — Graph-Native Bitemporal Memory Store (July 29, 2026)
🌐 Global

**Claim:** Neo4j researchers propose a graph-native bitemporal memory store that enables point-in-time retrieval for conversational agents without overwriting history, using immutable identity nodes + versioned content + HNSW vector indexes.
**Evidence:**
- **Authors:** Alp Niksarli, Gopesh Baheti (Neo4j)
- **Architecture:** Neo4j property graph + HNSW vector indexes + full bitemporal model (valid_time + transaction_time per edge)
- **Design:** Immutable identity nodes link to versioned content nodes; semantic edges auto-maintained via cosine similarity on 1024-dim embeddings; agent-local (no external cloud dependency)
- **Benchmarks (LongMemEval, 60 samples):**
  - Current-state semantic search: 46.7% R@10 overall; 80% R@10 on knowledge-update questions
  - Time-travel path: 80% R@10 on knowledge-update; 37.5% on temporal-reasoning
  - Post-filter dilution noted as limitation
- **URL:** https://arxiv.org/abs/2607.26520v1

### 4. [new] MemTool — Dynamic Tool-Context Memory for Multi-Turn Agents (ECIR 2026)
🌐 Global

**Claim:** MemTool (ECIR 2026, arXiv:2507.21428) solves the fixed-context-window bottleneck for multi-turn tool-using agents; reasoning LLMs achieve 90-94% tool-removal efficiency on ScaleMCP benchmark.
**Evidence:**
- **Problem:** Fixed context windows limit agents needing repeated, independent tool usage across multi-turn conversations
- **Solution:** Dynamic retrieval and management of tools / MCP server contexts across turns; 3 modes: Autonomous, Workflow, Hybrid
- **Benchmarks:** 13+ LLMs on ScaleMCP (100 consecutive interactions); reasoning LLMs: 90-94% tool-removal efficiency; medium-sized models: 0-60%
- **Publication:** ECIR 2026 proceedings (Springer); Advances in Information Retrieval
- **URLs:** https://arxiv.org/abs/2507.21428, https://link.springer.com/chapter/10.1007/978-3-032-21300-6_15

### 5. [new] HN: OpenKnowledge — AI-first Obsidian/Notion Alternative (HN:48675435, ~June 27, 2026)
🌐 Global

**Claim:** Show HN: OpenKnowledge (381 pts, 173 comments) proposes an AI-native knowledge management system with built-in MCP/Skills integration — the highest-engagement HN submission on knowledge tooling this cycle.
**Evidence:**
- **URL:** https://news.ycombinator.com/item?id=48675435
- **User:** engomez | **Points:** 381 | **Comments:** 173
- **Features:** WYSIWYG markdown editor; MCP/Skills integrations; AI-native workflows
- **Community gaps flagged:** No local LLM support; no Dataview-equivalent; macOS-first (Web/CLI for Linux/Windows); 1s load time for 10-line file
- **Positive signal:** MCP/Skills integration + markdown = validated design pattern

### 6. [new] HN: I benchmarked my memory graph against Memora — 0.831 vs 0.801 (HN:49272286)
🌐 Global

**Claim:** Developer built a custom KG memory system outperforming Memora (existing MCP persistent memory server) on memory accuracy benchmark (0.831 vs 0.801).
**Evidence:**
- **URL:** https://news.ycombinator.com/item?id=49272286
- **Quote:** "I wanted an agent to remember what was needed when needed with minimal effort, talk architecture, file everything away, and remember it when writing stories for software being built"
- **Pattern:** Another entry in the practitioner-built-and-benchmarked-their-own-memory series (cf. HN:48337689 from prior run)

### 7. [new] HN: A public AI whose memory is shared across all users (HN:49319814)
🌐 Global

**Claim:** Experimental project: single AI agent whose memory is shared/visible across ALL users — raises first-in-kind design questions about collective memory, privacy, and shared agent knowledge stores.
**Evidence:**
- **URL:** https://news.ycombinator.com/item?id=49319814
- **Significance:** Inverts the dominant model (per-user private memory) toward collective/public memory topology

### 8. [update] Graphiti v0.29.3 — Combined Extraction, Saga Abstraction, FalkorDB Fixes (July 27, 2026)
🌐 Global

**New fact:** v0.29.3 ships combined entity+edge extraction (single LLM call replaces two), a new saga abstraction for multi-episode narrative rollup (summarize_saga API), and FalkorDB backend stability fixes.
**Evidence:**
- **URL:** https://github.com/getzep/graphiti/releases
- **Combined extraction:** Single LLM call covers what previously took two; covers 6 classes of low-quality entity precision targets
- **Saga abstraction:** summarize_saga(saga_id) + SagaNode + refreshed prompt; first-class API for multi-episode narrative rollup
- **FalkorDB fixes:** Short-circuit fulltext queries when all tokens are stopwords; backtick handling; graph routing for single group_id searches
- **Cross-encoder:** Providers can now configure cross-encoders instead of hardcoded OpenAI
- **8 new contributors** this release
- Note: Graphiti (28K+ stars) = open-source core; Zep Cloud = managed product on top

### 9. [update] Letta Agents SDK — MemFS + Dreaming + Native Channels (August 2026)
🌐 Global

**New fact:** Letta releases Agents SDK in August 2026; stateful, persistent agents across models/machines; adds dreaming (background memory consolidation), self-modifying harness extensions (mods), and native Slack/Telegram channel integrations; legacy core_memory_replace tools deprecated in favor of MemFS filesystem operations.
**Evidence:**
- **URL:** https://www.letta.com/blog/our-next-phase/, https://github.com/letta-ai/letta/releases, https://docs.letta.com/concepts/memfs
- **MemFS:** git-backed; agents self-edit; dreaming consolidates memory in background
- **Mods:** Self-modifying harness extensions — agents can modify own tools/behavior
- **Channels:** Native Slack, Telegram, others integrated
- **Migration:** Legacy server memory tools (core_memory_replace) deprecated → MemFS filesystem operations
- **Letta Code:** Model-agnostic agent harness; #1 on Terminal-Bench; $20/mo Pro tier unchanged

### 10. [update] Qiita (Aug 13, 2026): "When AI Returns Different Numbers by Department"
🇯🇵 Japan

**New fact:** Qiita article (M_Ozu, Aug 13, 2026) frames the ontology problem not as a data problem but as an undocumented-meaning problem: when different departments get different AI answers for the same question, the fix is organizational ontology, not smarter models.
**Evidence:**
- **URL:** https://qiita.com/M_Ozu/items/346f6c8ab4b662a08f3e
- **Key claim:** "モデルをより賢いものに替えても、この食い違いは直りません" → "Replacing the model with a smarter one won't fix this discrepancy"
- **Root cause:** Definitions were never explicitly documented; different business purposes use different meanings for same term
- **Ontology resurgence traced to Palantir (2003):** Maintained semantic focus long before generative AI
- **LLM role:** LLMs reduce documentation cost barrier, making ontology authoring viable now
- **Framing:** Ontology as organizational contract, not just technical spec

**Still true** (ongoing threads, no new facts this run):
- `aws-context-ontology-accelerator` — GA July 31; Apache 2.0; OWL 2+HermiT+MCP; months→days authoring
- `hindsight-v090-knowledge-pages` — v0.9.0 Aug 6; Knowledge Pages + unified plugin; 57-65% fewer corrections
- `crystalmem-elastic-memory` — arXiv:2608.00303; 4-fidelity; matches full baseline at 50% budget
- `shared-org-memory-coding-agents` — arXiv:2608.00122; production enterprise contributor-approved Q&A memory
- `mcp-memory-okf-sqlite` — fellowgeek; OKF v0.2 + SQLite FTS5; local-first; 5 MCP tools
- `tencentdb-agent-memory-v2` — v2.0 Aug 3; MIT; PersonaMem 48%→76%
- `coevokg-self-evolving-search` — arXiv:2608.01904; KG+RL co-evolution; +11.2pp QA
- `benchmark-vendor-inflation-measured` — Mnemoverse; Mem0 -20.6pp under Maximem harness
- `mragent-reconstructed-memory` — ICLR 2026; active reconstruction; Cue-Tag-Content graph
- `magma-multi-graph-memory` — 4-graph decoupled; policy-guided traversal; best LoCoMo 0.7
- `hage-rl-graph-evolution` — UT Dallas/UF/UC Davis; RL-optimized edge weights
- `mage-multi-agent-coevolving-kg` — UNSW; 4-subgraph co-evolutionary KG
- `bosun-memory-graph-cleaner` — LoRA Qwen3-Reranker; WarrantBench dataset
- `hyphaedb-living-topology` — gossip-protocol vector topology; emergent contradiction detection
- `cloudflare-agent-memory-beta` — 5-channel RRF+HyDE; still private beta
- `mnemoverse-hebbian-memory` — Hebbian+Rescorla-Wagner; 6 MCP tools
- `gene-ontology-kb-2026` — NAR; 768 new terms; AI-assisted curation standard
- `neo4j-constant-cost-semantic-memory` — semvec; constant token cost per turn; 3-line Python API
- `memgraphrag-kdd-2026` — KDD 2026 (Aug 9-13 Jeju); 3-layer ontological; 59.25% avg accuracy
- `sap-knowledge-graph-autonomous-enterprise` — Sapphire 2026; 50yr ERP semantics; 200+ agents
- `experience-graphs-trellis-meta` — arXiv:2606.29823; 10× speedup; 52% token reduction
- `databricks-context-engineer-cert` — GA July 29; $200; beta results expected mid-September 2026
- `databricks-genie-ontology` — Ontology Snippets all customers Aug 13; enabled by default
- `mandol-agglomerative-memory` — CAS+MSFT; 92.21%/88.40% LoCoMo/LME
- `toki-bitemporal-contradiction-algebra` — 3 write anomalies; 4 soundness theorems
- `agent-native-memory-readiness-survey` — CAS/Tsinghua; 12 systems; no single dominant
- `oracle-ai-agent-memory-26-6` — DB-native; 93.8% LME; 10.7× token reduction
- `redis-context-engine` — GA May 18; 3-component MCP-native
- `evermind-everos-self-evolving` — v1.1.1 July 7; HyperMem hypergraph; mRAG
- `moss-auditable-relational-memory` — SQL retrieval; 569 concepts; auditable
- `sage-graph-self-evolving-engine` — reader-writer feedback; best rank multi-hop QA
- `kgermar-dynamic-kg-inference` — 3 memory banks; 8.5% lower perplexity
- `mcp-spec-2026-07-28-rc` — final spec; stateless HTTP; all hyperscalers aligned
- `apache-ossie-semantic-interchange` — incubating July 10; 50+ orgs; no August update
- `selfmem-beam-sota-july-2026` — KAUST; best BEAM 100K/500K/1M
- `automem-cognitive-skill` — KAUST; metamemory skill; 2-4× long-horizon
- `self-gc-context-lifecycle` — 43.95% pruning; 91-95% no-impact in 332 sessions
- `memrefine-budget-compression` — LLM-guided factual budgeted compression
- `minio-aistor-memory` — July 29; unified enterprise memory; no GA date
- `skan-aow-v1-agent-ontology` — 8 canonical entities (Agents/Skills/Intents/Contexts/Policies/Memory/Confidence/Outcomes)
- `agentic-context-management-lifecycle` — ACM 5 primitives; Maximem Synap 92% LME
- `context-files-no-measurable-impact` — 2 agents, 17 repos, 288 runs; ≤10-15pp gain
- `mem0-openmemory-mcp-local` — local Docker; Chrome ext; async default
- `smoothagent-lookahead-context` — 11.9× TTFT reduction; segment-decomposable transforms
- `memguard-role-typed-memory` — +28.27% reliability; 5.8× fewer tokens; UIUC/Columbia
- `less-context-better-agents` — last-5 pruning+summarize; 91.6% vs 71%; 2.8× cheaper
- `context-graphs-proactive-enterprise` — 47min→30s; Precision@5 0.83
- `mem0-v2-token-efficiency` — 61K+ stars; 186M quarterly API calls; free-tier tripled July
- `exabase-m1-beam-sota` — dual SOTA BEAM+LME; Gemini 3 Flash; 4-6× cheaper
- `okf-v02-provenance-trust` — v0.2 current as of Aug 12; no v0.3; OKF reference impls published
- `memanto-typed-semantic-memory` — 13 categories; <90ms; 89.8% LME
- `plugmem-icml-2026-microsoft` — task-agnostic; outperforms task-specific; 3 benchmark classes
- `t-mem-anticipatory-retrieval` — associative vs descriptive gap; anticipatory retrieval
- `neuro-symbolic-tkg-meta-policy` — step-level traceability; best PORL
- `netflix-e2e-kg-shared-ontology` — shared ontology coordinator+specialist AutoSRE
- `iso-23726-3-fdis` — OWL DL industrial automation ontology; FDIS stage; nearing ISO pub
- `allegrograph-85-neuro-symbolic` — v8.5 March 17; expanded MCP; Prometheus/Grafana
- `memgraph-atomic-graphrag` — single Cypher GraphRAG; Agentic GraphRAG + Skills + MCP
- `surrealdb-3-unified-agent-memory` — Rust engine; Spectron; Verizon/Tencent/Samsung
- `architecture-beats-model-scale` — 2026 convergence confirmed; architecture > model size
- `engram-bi-temporal-memory-engine` — 83.6% LME_S vs 73.2% full-context; 8× fewer tokens
- `sage-write-side-novelty-gate` — vMF gate; 3.4× API cost / 2.5× latency reduction vs Mem0
- `tokenpilot-cache-efficient-context` — 61-87% cost cut; KV cache stable
- `agenticts-bounded-memory-testbed` — Slay the Spire 2; 298 trajectories; 5 per-decision slots
- `mempalace-zero-api-spatial-memory` — 56K stars; 96.6% Recall@5; 36 MCP tools
- `ontology-dilution-problem` — "ontology escaped technical meaning into marketing" (Year of the Graph Vol.31)
- `selective-ontology-injection-best-practice` — selective > always-on; full ontological context displaces parametric
- `ontology-guardrails-framing` — Latent Space July 30; Coyle/Eifrem/Idehen; 36-46% multi-hop gains
- `cn-llms-reshape-ontology-engineering` — TBox by LLM; ABox human-validated; CSDN
- `jp-layered-implementation-path` — Semantic Layer → Lightweight Ontology → MCP; Gartner 40% failure
- `okf-v01-structural-interoperability` — v0.1 June 12; v0.2 July 25; mcp-memory implements
- `memory-agent-bench-four-competencies` — ICLR 2026; 4 competencies; all methods fall short
- `letta-pro-cloud-tier` — Agents SDK Aug 2026; MemFS+dreaming; $20/mo Pro; Letta Code #1 Terminal-Bench
- `zep-ce-retired-graphiti-open-source` — 28.9K+ stars; v0.29.3 July 27; saga abstraction
- `memora-microsoft-icml-2026` — 98% token reduction; 86.3%/87.4% LoCoMo/LME
- `fabric-iq-ontology-mcp` — public MCP endpoints Preview
- `mcp-ontology-integration-protocol` — all hyperscalers aligned; 10+ tools MCP-native
- `ontology-as-reliability-infrastructure` — EN/JP/CN independent convergence
- `benchmark-proliferation-memory` — 6+ benchmarks; vendor scores inflate 20pp; non-portable
- `evomembench-no-single-memory-form` — 15-system; no dominant form
- `napmem-active-memory-navigation-rl` — RL active navigation; agents learn which memory to consult
- `placemem-compute-aware-memory-plane` — versioned capsules; cross-agent sharing
- `agento-owl-rdf-agentic-ontology` — ESWC 2026; 66 workflows; 4 frameworks
- `always-on-agents-survey` — 435-paper; AOEP-v0 protocol
- `ontobricks-open-ontologies-mcp` — Rust MCP server; Oxigraph+OWL2-DL+SHACL+SPARQL
- `eticas-ai-risk-taxonomy-v2` — SKOS/JSON-LD; 76 subcategories; 18 framework mappings
- `hn-5-mistakes-kg-memory` — POLE+O; schema decides everything; invalidation unsolved
- `neo4j-pole-o-hallucination-reduction` — 36-46% accuracy gains; 40%+ hallucination reduction
- `memdelta-benchmark-nonportability` — embedding swap flips rankings 6.2pp
- `eywa-evidence-before-belief` — provenance-grounded; SOTA long-horizon
- `ember-budgeted-evidence-retention` — fixed-budget write-side control
- `projectmem-memory-as-governance` — 14 MCP tools; MIT
- `cn-ontology-strategic-return` — property graphs over OWL/RDF; KG as grounding/reliability layer
- `tencent-tbox-abox-framing` — TBox/ABox two-stage; LLM generates TBox
- `ontology-interoperability-lifecycle-framework` — 3-phase lifecycle; ODPs+Matching+Validation
- `trust-certificates-pre-deployment` — formal ontology-backed certification; no production pilots
- `vector-db-market-growth` — $3.2B→$8.95B at 27.5% CAGR; Qdrant $50M Series B
- `neo4j-thin-agents-graphsummit` — ZS case study; Eifrem "Thinner Agents on Smarter Substrate"

---

## Cross-Source Patterns

### Pattern 1: "Endogenous Memory" vs "External Retrieval" — New Architectural Split (🇨🇳 CN)
- MemoraX AI (Aug 12): Agentic RL trains memory INTO the model, not bolted on via RAG/KG
- Contrasts directly with all shipping memory systems (Mem0, Zep/Graphiti, Letta, Hindsight) which are external retrieval
- ICLR 2026 ReMix algorithm: the first production-grade implementation of this paradigm
- Investor signal: 3 rounds in 5 months at >100M CNY = highest-velocity memory startup globally this cycle
- **Significance:** If ReMix scales, every retrieval-based memory system faces architectural disruption

### Pattern 2: Memory Interoperability Becomes Research Priority (🌐 Global, CAS)
- MemTools (arXiv:2607.21404, CAS/BAAI, July 23): proposes decoupled declarative contracts for memory components
- MemTool (ECIR 2026, arXiv:2507.21428): dynamic tool-context management for multi-turn agents
- HN:49272286: developer benchmarks custom memory graph vs Memora — practitioner-level fragmentation problem
- **Pattern:** Research institutions and practitioners independently identifying the same fragmentation problem; standardization pressure building
- Similar to MCP's effect on tool interoperability — memory interoperability is the next layer

### Pattern 3: Graph Memory Infrastructure Maturing (🌐 Global, 🇯🇵 JP)
- Graphiti v0.29.3: combined extraction, saga abstraction, FalkorDB support (July 27)
- arXiv:2607.26520 (Neo4j): graph-native bitemporal store with agent-local design (July 29)
- jisaku.com JP guide (updated Aug 18): Qdrant/Milvus/Weaviate recommendations for GraphRAG stack
- Neo4j benchmark: Text-to-SQL token usage −10× with semantic layer; confirmed ongoing
- **Pattern:** Both academic (arXiv:2607.26520) and practitioner (Graphiti v0.29.3) graph memory is getting more precise — bitemporal, saga-level narrative, combined extraction

### Pattern 4: Ontology as Organizational Problem, Not Technical Problem (🌐 Global, 🇯🇵 JP)
- Qiita/M_Ozu (Aug 13): "When AI returns different numbers by department" — root cause is undocumented business meaning
- Databricks Genie Ontology (Aug 13, all customers): Ontology Snippets to all customers; semantic alignment as product
- Atlan (ongoing): "Semantic layer tells you what your revenue is. Ontology tells you what a customer is."
- Frank Coyle (Aug 7, neo4j): "Ontology is a logical guardrail sitting outside the model"
- **Pattern:** The "organizational alignment" framing of ontology is strengthening — it's positioned as solving a business problem (different departments get different answers), not a technical one

### Pattern 5: Practitioner Builders Benchmarking Their Own Memory (🌐 HN)
- HN:49272286: 0.831 vs Memora's 0.801 — custom graph beats existing tool
- HN:49319814: Shared public memory experiment — inverting per-user private model
- HN:48675435: OpenKnowledge — AI-native note-taking with MCP, 381 pts
- HN:48337689 (prior, still referenced): "5 mistakes in a year of KG memory"
- **Pattern:** High-engagement HN posts are practitioner-built systems benchmarking against established tools, not just discussions — memory is a real engineering problem being solved bottom-up

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| engomez | Show HN: OpenKnowledge – open source AI-first alternative to Obsidian/Notion | 381 | 173 | "WYSIWYG markdown + built-in MCP/Skills integrations" | https://news.ycombinator.com/item?id=48675435 |
| (unknown) | Show HN: I benchmarked my memory graph against Memora (0.831 vs. 0.801) | — | — | "file everything away, remember it when writing stories for software" | https://news.ycombinator.com/item?id=49272286 |
| (unknown) | Show HN: A public AI whose memory is shared across all users | — | — | Inverts per-user private memory model | https://news.ycombinator.com/item?id=49319814 |

**Web (Global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv:2607.26520 | https://arxiv.org/abs/2607.26520v1 | Graph-native bitemporal memory store (Neo4j authors, July 29) |
| 🌐 | arXiv:2607.21404 | https://arxiv.org/abs/2607.21404 | MemTools: interoperable agent memory framework (CAS/BAAI, July 23) |
| 🌐 | arXiv:2507.21428 | https://arxiv.org/abs/2507.21428 | MemTool: dynamic tool-context memory (ECIR 2026) |
| 🌐 | Graphiti releases | https://github.com/getzep/graphiti/releases | v0.29.3 July 27: combined extraction, saga abstraction |
| 🌐 | Letta blog | https://www.letta.com/blog/our-next-phase/ | Agents SDK Aug 2026: MemFS+dreaming+mods+channels |
| 🌐 | Letta MemFS docs | https://docs.letta.com/concepts/memfs | MemFS specification |
| 🌐 | Mnemoverse Q3 | https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3 | Vendor benchmark inflation; Mem0 -20.6pp |
| 🌐 | OKF v0.2 confirmed | https://cloud.google.com/blog/products/data-analytics/okf-v0-2-adds-trust-signals | Still current; reference impls published |
| 🌐 | Apache Ossie | https://ossie.apache.org/updates/ | No August update; last entry July 10 |
| 🌐 | Google ADK blog | https://developers.googleblog.com/architecting-efficient-context-aware-multi-agent-framework-for-production/ | Tiered context (Session/Memory/Artifacts) |
| 🌐 | Cognee changelog | https://www.cognee.ai/changelog | No August changelog entry; last July 13 (Berkeley Xcelerator) |
| 🌐 | Atlan | https://atlan.com/know/ontology-vs-semantic-layer/ | "Semantic layer = revenue; Ontology = customer" |
| 🌐 | neo4j TWIN4J Aug 7 | https://neo4j.com/blog/twin4j/this-week-in-neo4j-ontology-agent-memory-graphrag-visualisation-and-more/ | ZS case study; Coyle "logical guardrail" |
| 🌐 | HackerNoon | https://hackernoon.com/agent-memory-has-a-lock-in-problem-open-formats-are-how-we-fix-it | Agent memory lock-in problem; open formats |
| 🌐 | HackerNoon | https://hackernoon.com/context-graphs-ontologies-and-the-race-to-fix-enterprise-ai | Context graphs + ontologies race |
| 🌐 | ecorpit.com | https://ecorpit.com/ai-agent-memory-mem0-zep-letta-cloudflare-comparison-2026/ | Mem0 vs Zep vs Letta vs Cloudflare Aug 2026 |
| 🌐 | particula.tech | https://particula.tech/blog/agent-memory-frameworks-tested-mem0-zep-letta-cognee-2026 | Four-framework comparison |
| 🌐 | Databricks cert | https://www.databricks.com/learn/certification/context-engineer-associate | Beta results mid-Sep expected |
| 🌐 | ontoforce.com | https://www.ontoforce.com/blog/gartners-2026-predictions-confirm-the-semantic-layer-is-no-longer-optional | Gartner: semantic layer mandatory |
| 🌐 | RSC Digital Discovery | https://pubs.rsc.org/en/content/articlelanding/2026/dd/d5dd00275c | Scientific KG+ontology generation via open LLMs |
| 🌐 | syntes.ai | https://syntes.ai/knowledge-graph-architecture-the-blueprint-for-enterprise-agentic-ai-in-2026/ | KG architecture blueprint for enterprise agentic AI |
| 🌐 | contextandchaos | https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic | 3-layer disambiguation |
| 🌐 | vectorize.io | https://vectorize.io/articles/mem0-vs-zep | Zep (Graphiti) 63.8% vs Mem0 49.0% LongMemEval |
| 🌐 | falkordb.com | https://www.falkordb.com/blog/building-temporal-knowledge-graphs-graphiti/ | Graphiti + FalkorDB temporal KG |
| 🌐 | yearofthegraph.xyz | https://yearofthegraph.xyz/newsletter/2026/06/layers-of-meaning-context-graphs-graph-memory-and-ontologies-for-ai-the-year-of-the-graph-newsletter-vol-31-summer-2026/ | "Ontology escaped technical meaning into marketing" |
| 🌐 | medium/giuseppefutia | https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5 | KGC 2026: "production failures are representation failures" |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita/@M_Ozu | https://qiita.com/M_Ozu/items/346f6c8ab4b662a08f3e | Aug 13: "Why departments get different AI answers" = missing ontology |
| 🇯🇵 | Qiita/@taka_yayoi | https://qiita.com/taka_yayoi/items/35e4b28280290c131ee3 | Databricks Genie Ontology: self-improving context layer |
| 🇯🇵 | Qiita/@yohei1126 | https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80 | Why graphs for agent knowledge representation |
| 🇯🇵 | Qiita/@yohei1126 | https://qiita.com/yohei1126/items/2359c10d6c37be7f4fb3 | Graph DB change management for agent infra |
| 🇯🇵 | Zenn/proper_willet | https://zenn.dev/proper_willet/articles/1925e7ebcb81db | Selective memory + bi-layer hot/cold design 2026 |
| 🇯🇵 | jisaku.com | https://jisaku.com/posts/ai-agent-memory-rag-guide | AI agent memory+RAG guide; updated Aug 18, 2026; Qdrant/Milvus/Weaviate stack |
| 🇯🇵 | uravation.com | https://uravation.com/media/ai-agent-memory-complete-guide-2026/ | Big Three (Mem0/Zep/Letta) production-ready guide; updated Aug 4 |
| 🇯🇵 | since2020.jp | https://since2020.jp/media/ontology-semantic-ai-databricks-stardog/ | Ontology as hallucination prevention (Stardog framing) |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | pedaily.cn | https://news.pedaily.cn/202608/567590.shtml | MemoraX AI Seed++ Aug 12, >100M CNY total |
| 🇨🇳 | qq.com/Tencent News | https://news.qq.com/rain/a/20260812A04CHV00 | MemoraX: 3 rounds / 5 months; funding timeline |
| 🇨🇳 | 36kr.com | https://eu.36kr.com/en/p/3785834045583875 | "Endogenous memory" paradigm for large models |
| 🇨🇳 | aibase.com | https://news.aibase.com/news/28163 | MemoraX Seed+ round; ReMix ICLR 2026 |
| 🇨🇳 | aibase.com | https://news.aibase.com/news/27522 | MemoraX seed round Apr 2026 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2035765768013468400 | "AI失忆症" — AI amnesia = hundred-billion market |
| 🇨🇳 | shengwang.cn | https://www.shengwang.cn/blog/blogdetail/rag-to-context-engineering/ | "RAG已死?" → context engineering + semantic layer |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2649862 | RAG 2026 latest progress |
| 🇨🇳 | 53AI | https://www.53ai.com/news/RAG/2026051412734.html | Five-generation RAG → Agentic RAG guide |
| 🇨🇳 | CSDN | https://blog.csdn.net/Honmaple/article/details/161646585 | Five-system CN comparison: Mem0, Zep, Letta, EverMind, Cognee |
| 🇨🇳 | 53AI | https://www.53ai.com/news/knowledgegraph/2026022019635.html | OpenKG: SPG+KAG, SkillNet, OneGraph — CN KG 2026 |
| 🇨🇳 | Tencent Cloud Developer | https://developer.cloud.tencent.com/article/2724385 | 85% cognitive amnesia; 5 iron laws; Redis/Chroma/Neo4j stack |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ (not accessible)
├─ 🔵 X: 0 posts │ (excluded per spec)
├─ 🔴 YouTube: 0 videos │ (not searched)
├─ 🟢 HN: 3 threads │ 381+ pts
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ (no on-topic signal; bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 55 pages │ 🇯🇵 7 │ 🇨🇳 12
└─ 🗣️ Top voices: Hao Jianye (MemoraX/Huawei), @M_Ozu (Qiita), Frank Coyle (Neo4j track), Emil Eifrem (Neo4j)
```

---

## Out of Scope but Notable

- **HN:49319814 "A public AI whose memory is shared across all users"** — collective/public memory topology (vs private per-user). If this design gains traction, it's a paradigm shift in how agent memory is scoped. Potentially relevant to paradigm-watch.
- **ReMix algorithm (ICLR 2026, MemoraX)** — endogenous memory built into LLM via Agentic RL. If validated, this challenges the entire external-retrieval memory stack; could belong equally in open-models or ai-infrastructure topics.
- **MemTools (arXiv:2607.21404)** — "memory interoperability layer" as research concern. Analogous to what MCP provides for tools but applied to memory backends. This could develop into a standards initiative.

---

## Data Gaps

- **Reddit:** Not accessible (400/403 errors); expected: r/MachineLearning, r/KnowledgeGraph likely have active threads
- **X/Twitter:** Excluded per spec
- **YouTube:** Not searched this pass
- **Bluesky:** Searched; no on-topic posts found; bluesky=OK — niche topic with low Bluesky signal
- **Zhihu:** Direct WebFetch returned 403 on multiple article URLs; content reconstructed from search snippets
- **Neo4j TWIN4J Aug 11 or Aug 18:** Not found; last confirmed Aug 7 (blocked on Aug 11/18 Neo4j pages)
- **Cognee August changelog:** No entries found; last July 13 (Berkeley Xcelerator)
- **Graphiti post-v0.29.3:** No releases after July 27 found
- **Apache Ossie August:** No updates since July 10 incubation announcement
- **MemoraX AI technical paper:** ReMix ICLR 2026 paper not directly accessed; described from press coverage
- **Coverage estimate:** ~75-78% of ideal full-platform run (missing Reddit, YouTube, some Zhihu content behind login)

---

## Key Quotes

> "モデルをより賢いものに替えても、この食い違いは直りません。" ("Replacing the model with a smarter one won't fix this discrepancy.") — @M_Ozu on Qiita, August 13, 2026 ([link](https://qiita.com/M_Ozu/items/346f6c8ab4b662a08f3e)) 🇯🇵

> "Agentic systems fail without a formal ontology sitting outside the model as a logical guardrail." — Frank Coyle, AI Engineer World's Fair / Neo4j track ([link](https://neo4j.com/blog/twin4j/this-week-in-neo4j-ontology-agent-memory-graphrag-visualisation-and-more/))

> "AI失忆症 (AI amnesia syndrome): 85% of enterprise agents experience critical information loss on cross-week/month tasks — a hundred-billion-level market." — Zhihu analysis ([link](https://zhuanlan.zhihu.com/p/2035765768013468400)) 🇨🇳

> "单なるトークン履歴を保存するだけでは不十分" ("Simply storing token histories proves insufficient") — jisaku.com JP AI agent memory guide, updated August 18, 2026 ([link](https://jisaku.com/posts/ai-agent-memory-rag-guide)) 🇯🇵

> "Most production failures attributed to 'model limitations' or 'prompt engineering' are actually representation failures — knowledge graphs are the substrate on which production AI stands." — Notes from KGC 2026 ([link](https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5))

> "Semantic layer tells you what your revenue is. Ontology tells you what a customer is." — Atlan, Ontology vs Semantic Layer 2026 ([link](https://atlan.com/know/ontology-vs-semantic-layer/))

> "Memory interoperability: MemTools decouples memory system components from deployment environments, enabling interchangeable assembly across different systems." — MemTools paper, CAS/BAAI, arXiv:2607.21404 ([link](https://arxiv.org/abs/2607.21404))
