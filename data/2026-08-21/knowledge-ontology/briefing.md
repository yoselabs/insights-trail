# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-08-21
**Query type:** GENERAL
**Sources:** Hacker News, arXiv, Web (Global), Web (Japan), Web (China), Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 ongoing thread | — | HN:44423406 (OntoCast); prior HN threads still active |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; no on-topic signal |
| Web (global) | 90 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 10 pages | — | 🇯🇵 Qiita ×4, Zenn ×3, LayerX blog ×1, jisaku.com ×1, other JP ×1 |
| Web (China) | 12 pages | — | 🇨🇳 Zhihu ×4, CSDN ×3, 36kr ×2, itbear ×2, 53AI ×1 |

---

## Synthesized Findings

### 1. [new] Semantica v0.6.0 — Graph-Native Provenance Layer for AI Agents (July 21, 2026)
🌐 Global

**Claim:** Semantica (semantica-agi/semantica, MIT, 3,435 stars as of Aug 10, 2026) is a graph-native context and provenance layer that runs deterministic reasoning via forward chaining/Rete/Datalog/SPARQL without LLMs, with W3C PROV-O audit trails on every fact; targets regulated industries where "the decision needs an answer that survives scrutiny."
**Evidence:**
- **License/install:** MIT; `pip install semantica`; GitHub: https://github.com/semantica-agi/semantica
- **Core:** Deterministic reasoning (no LLM required for graph construction or provenance) — contrasts with all LLM-in-the-loop KG approaches
- **Provenance:** W3C PROV-O on every fact; audit trails exportable as JSON, CSV, or RDF
- **Storage:** RDF backends (Oxigraph, Blazegraph, Jena, RDF4J) AND property graphs (Neo4j, FalkorDB, Neptune) AND Databricks/Snowflake connectors
- **Interfaces:** MCP server + REST API + CLI
- **Positioning:** "Open-source Palantir for AI agents"; sectors: finance, healthcare, government; GDPR/EU AI Act/HIPAA compliance context
- **Coverage:** https://moclaw.ai/blog/what-is-semantica, https://themenonlab.blog/blog/semantica-open-source-palantir-alternative-ai-agents

### 2. [new] Starling Memory Works — Universal Cognitive Architecture (UCA) Open Standard
🌐 Global

**Claim:** Starling Memory Works (Princeton-based) published Universal Cognitive Architecture, a Creative Commons open standard defining "Domain Language Model" class systems — retrieval by fixed semantic coordinate (not vector search) — alongside beta Starling MX platform; MCP-compatible.
**Evidence:**
- **Standard:** UCA — organizations store knowledge at fixed semantic addresses; any AI model can read by coordinate; org retains control
- **License:** Permanently free (Creative Commons)
- **Integration:** Works alongside MCP; compatible with existing LLM stacks; retrieval by coordinate means zero-drift access (vs nearest-neighbor approximation)
- **Platform:** Starling MX beta; $99/mo first seat + usage
- **Coverage:** https://itbrief.asia/story/starling-open-sources-ai-memory-standard-for-organisations, https://www.research-live.com/article/news/starling-mx-launches-open-standard-for-working-with-ai-models/id/5151987

### 3. [new] Neo4j Labs agent-memory / NAMS — v0.5.0 (May 30, 2026)
🌐 Global

**Claim:** Neo4j Labs released neo4j-agent-memory library (Python+TypeScript SDKs, NAMS hosted service) with POLE+O ontology model, 3-tier memory (conversation/entities/reasoning), and v0.5.0 first-class ontology surface with versioning; unreleased main: ontology import/diff/migrate operations.
**Evidence:**
- **GitHub:** https://github.com/neo4j-labs/agent-memory; **PyPI:** https://pypi.org/project/neo4j-agent-memory/
- **v0.5.0 (May 30, 2026):** NAMS alignment; first-class ontology surface with versioning; Google ADK Neo4jMemoryService compatibility; workspace addressing for NAMS deployments
- **v0.4.0 (May 17):** NAMS hosted backend (alternative to bolt-to-Neo4j); REST API with retry; Platinum-tier methods (feedback, history, entity provenance)
- **POLE+O model:** Person, Object, Location, Event, Organization (from intelligence analysis); optional subtypes (OBJECT:VEHICLE, LOCATION:ADDRESS); SAME_AS deduplication
- **Architecture:** 3 memory tiers (short-term conversation → long-term typed entities → reasoning traces); Python + TypeScript SDKs interoperate on same graph
- **Unreleased (main):** Ontology import/diff/migrate; API-key management; Strands SessionManager for AWS agents; extraction status tracking
- **Microsoft Agent Framework:** Featured as launch partner at v1.0 (April 2026)
- **Docs:** https://neo4j.com/labs/agent-memory/, https://neo4j.com/labs/agent-memory/explanation/poleo-model/

### 4. [new] OntoCast v0.3.0 — Ontology-Assisted KG Extraction (March 10, 2026)
🌐 Global

**Claim:** OntoCast (GrowGraph, Apache-2.0) is an agentic framework that co-evolves domain ontologies and KG fact-graphs simultaneously in a parallel map/reduce pipeline, with SHACL validation, RDF 1.2 provenance, and entity disambiguation — first HN attention June 2025, v0.3.0 shipping March 2026.
**Evidence:**
- **GitHub:** https://github.com/growgraph/ontocast; **HN:** https://news.ycombinator.com/item?id=44423406
- **v0.3.0:** GraphUpdate patches (insert/delete instead of regenerating whole graphs); SHACL validation with LLM-free autofix; lighter install (embeddable without Docling/gRPC/ONNX)
- **Core loop:** per-chunk render → critic → merge; ontology and instance data co-evolve
- **Output:** RDF/Turtle against standard vocabularies; provenance-grounded (passage-linked)
- **Deployment:** REST service, batch CLI, embedded in LangChain/LangGraph agent
- **PyPI:** https://pypi.org/project/ontocast/

### 5. [update] MemoraX AI — Huawei Cloud Strategic Cooperation (August 2026)
🇨🇳 China

**New fact:** MemoraX AI signed strategic cooperation agreement with Huawei Cloud; described as **the only** partner in Huawei Cloud's large model ecosystem focused on long-term memory — elevating it from VC-funded startup to hyperscaler-aligned infrastructure company.
**Evidence:**
- **Source:** https://www.itbear.com.cn/html/2026-08/1495089.html, https://m.sohu.com/a/1061900704_100032554
- **CN quote:** "华为云合作厂商中唯一聚焦长期记忆的企业" (= "The only entity among Huawei Cloud partners focused on the long-term memory track")
- **Prior facts still true:** Seed++ (Aug 12, >100M CNY total, 3 rounds/5 months); Founder: Hao Jianye (ex-Huawei Noah's Ark Lab director, Tianjin University professor); ReMix (ICLR 2026): Agentic RL trains endogenous memory INTO model, not external RAG
- **36kr Seed++ URL:** https://www.36kr.com/p/3935938639107720, https://eu.36kr.com/en/p/3785834045583875

### 6. [update] Cognee v1.5.0.dev5 — Dataset Overview Index (August 20, 2026)
🌐 Global

**New fact:** Cognee v1.5.0.dev5 (Aug 20, 2026) ships a new optional dataset overview index — topical clustering that groups documents and creates short overviews to give searches broader cross-dataset context.
**Evidence:**
- **URLs:** https://www.cognee.ai/changelog, https://github.com/topoteretes/cognee/releases, https://docs.cognee.ai/changelog
- **dev5 (Aug 20):** Dataset overview index (optional; groups by topic; improves retrieval relevance); faster/more reliable ingestion for large files; improved search ranking
- **dev2 (Aug 15):** Ladybug graph adapter performance improvements; migration pipeline reliability for large-scale dataset migrations; LLM tuning options (temperature + seed)
- **Prior features still active:** Neptune integration, n8n Cloud, self-improving graph (feedback → edge weights), graph embeddings, Berkeley Xcelerator (July 13)

### 7. [update] Mem0 Editor Plugin v0.2.11 — Project/Global Scopes + Antigravity Support
🌐 Global

**New fact:** Mem0 shared editor plugin v0.2.11 adds project and global memory scopes (project-scoped default; `global_search` enables team-wide recall across users/app scopes) and expands coverage to Antigravity; auto-capture now includes file reads, bash errors, session resume, startup timelines.
**Evidence:**
- **URL:** https://releasebot.io/updates/mem0, https://github.com/mem0ai/mem0
- **v0.2.11 changes:** Automatic context injection; project scope (default) + global scope (team recall); background coding taxonomy; reliable capture/compaction; Claude Code/Cursor/Codex/Antigravity with correct editor telemetry
- **Prior facts still true:** 61K+ GitHub stars; 14M downloads; 186M quarterly API calls; OpenMemory MCP Server (local Docker); free-tier tripled July 19; graph-store drivers removed in SDK v2.0.0

---

**Still true** (ongoing threads, no new facts this run):
- `memorax-ai-endogenous-memory-funding` — now updated above
- `memtools-interoperable-framework` — arXiv:2607.21404; CAS/BAAI; declarative contracts for memory interoperability
- `graph-native-bitemporal-neo4j` — arXiv:2607.26520; 80% R@10 on knowledge-update questions
- `memtool-dynamic-tool-context` — ECIR 2026; 90-94% tool-removal on ScaleMCP benchmark
- `hn-openknowledge-ai-notes` — HN:48675435; 381 pts; AI-native Obsidian/Notion alternative with MCP
- `jp-qiita-ontology-department-alignment` — @M_Ozu Aug 13; "smarter model won't fix this discrepancy"
- `aws-context-ontology-accelerator` — GA July 31; Apache 2.0; OWL 2+HermiT+MCP; months→days authoring
- `hindsight-v090-knowledge-pages` — v0.9.0 Aug 7; Knowledge Pages + unified plugin; 57-65% fewer corrections
- `crystalmem-elastic-memory` — arXiv:2608.00303; 4-fidelity; matches full baseline at 50% budget
- `shared-org-memory-coding-agents` — arXiv:2608.00122; contributor-approved Q&A; production enterprise
- `mcp-memory-okf-sqlite` — fellowgeek; OKF v0.2 + SQLite FTS5; local-first; 5 MCP tools
- `tencentdb-agent-memory-v2` — v2.0 Aug 3; team-level hub; PersonaMem 48%→76%
- `coevokg-self-evolving-search` — arXiv:2608.01904; KG+RL co-evolution; +11.2pp QA
- `benchmark-vendor-inflation-measured` — Mnemoverse Q3; Mem0 −20.6pp under Maximem harness
- `mragent-reconstructed-memory` — ICLR 2026; Cue-Tag-Content graph; active reconstruction
- `magma-multi-graph-memory` — 4-graph decoupled; best LoCoMo 0.7
- `hage-rl-graph-evolution` — RL-optimized edge weights; UT Dallas/UF/UC Davis
- `mage-multi-agent-coevolving-kg` — UNSW; 4-subgraph co-evolutionary KG
- `bosun-memory-graph-cleaner` — LoRA Qwen3-Reranker; WarrantBench dataset
- `hyphaedb-living-topology` — gossip-protocol vector topology; emergent contradiction detection
- `cloudflare-agent-memory-beta` — 5-channel RRF+HyDE; still private beta
- `mnemoverse-hebbian-memory` — Hebbian+Rescorla-Wagner; 6 MCP tools
- `gene-ontology-kb-2026` — NAR; 768 new terms; AI-assisted curation standard
- `neo4j-constant-cost-semantic-memory` — semvec; constant token cost per turn; 3-line Python API
- `memgraphrag-kdd-2026` — KDD 2026; 3-layer ontological; 59.25% avg accuracy; 0.061s retrieval
- `sap-knowledge-graph-autonomous-enterprise` — Sapphire 2026; 50yr ERP semantics; 200+ agents
- `experience-graphs-trellis-meta` — arXiv:2606.29823; 10× speedup; 52% token reduction
- `hindsight-memory-benchmark-leader` — v0.9.0 Aug 7; SDE-bench 57-65%; prior 94.6% LME
- `longmemeval-v2-web-agent-experience` — 451 questions; 5 competencies; 115M token trajectories
- `stardog-bedrock-agentcore-semantic-layer` — KG semantic layer + MCP; federated Aurora+Redshift
- `ai-km-6-6-1-agentic-ontology-tooling` — agentic skill framework + ontology-driven modeling
- `reagan-node-as-agent-graph` — each node is an agent with PAMT; RAG for global retrieval
- `cognee-v1-4-0-dataset-overview` — now updated above (v1.5.0.dev5)
- `databricks-context-engineer-cert` — GA July 29; $200; beta results expected mid-September
- `databricks-genie-ontology` — Aug 6 enabled by default; Aug 13 snippets to all customers; OntoRank
- `mandol-agglomerative-memory` — CAS+MSFT; 92.21%/88.40% LoCoMo/LME
- `toki-bitemporal-contradiction-algebra` — 3 write anomalies; 4 soundness theorems
- `agent-native-memory-readiness-survey` — CAS/Tsinghua; 12 systems; no dominant architecture
- `oracle-ai-agent-memory-26-6` — 93.8% LME; BEAM 1M 0.680; 10.7× token reduction; DB-native
- `redis-context-engine` — GA May 18; 3-component MCP-native context layer
- `evermind-everos-self-evolving` — v1.1.1 July 7; HyperMem hypergraph; mRAG; <500ms p95
- `moss-auditable-relational-memory` — SQL retrieval; 569 concepts; 44M-token deployment
- `sage-graph-self-evolving-engine` — reader-writer feedback; best multi-hop QA
- `kgermar-dynamic-kg-inference` — 3 memory banks; 8.5% lower perplexity
- `mcp-spec-2026-07-28-rc` — final spec; stateless HTTP; all hyperscalers aligned
- `apache-ossie-semantic-interchange` — incubating; no August update since July 10
- `selfmem-beam-sota-july-2026` — KAUST; best BEAM 100K/500K/1M scales
- `automem-cognitive-skill` — KAUST; metamemory skill; 2-4× long-horizon improvement
- `self-gc-context-lifecycle` — 43.95% pruning; 91-95% no-impact in 332 sessions
- `memrefine-budget-compression` — LLM-guided factual budgeted compression
- `minio-aistor-memory` — July 29; unified enterprise memory (object+vector+secrets); no GA date
- `skan-aow-v1-agent-ontology` — 8 canonical entities (Agents/Skills/Intents/Contexts/Policies/Memory/Confidence/Outcomes)
- `agentic-context-management-lifecycle` — ACM 5 primitives; Maximem Synap 92% LME
- `context-files-no-measurable-impact` — 2 agents, 17 repos, 288 runs; ≤10-15pp gain
- `mem0-openmemory-mcp-local` — local Docker; Chrome ext; async default
- `smoothagent-lookahead-context` — 11.9× TTFT reduction; segment-decomposable
- `memguard-role-typed-memory` — +28.27% reliability; 5.8× fewer tokens; UIUC/Columbia
- `less-context-better-agents` — last-5 pruning+summarize; 91.6% vs 71%; 2.8× cheaper
- `context-graphs-proactive-enterprise` — 47min→30s; Precision@5 0.83
- `mem0-v2-token-efficiency` — now updated above (editor plugin v0.2.11)
- `exabase-m1-beam-sota` — dual SOTA BEAM+LME; 4-6× cheaper via Gemini 3 Flash
- `okf-v02-provenance-trust` — v0.2 current; no v0.3; reference impls published
- `memanto-typed-semantic-memory` — 13 categories; <90ms; 89.8% LME; zero ingestion cost
- `plugmem-icml-2026-microsoft` — task-agnostic; outperforms task-specific designs
- `t-mem-anticipatory-retrieval` — anticipatory retrieval predicts needed memories before explicit query
- `neuro-symbolic-tkg-meta-policy` — step-level traceability; best PORL results
- `netflix-e2e-kg-shared-ontology` — shared ontology coordinator+specialist AutoSRE
- `iso-23726-3-fdis` — FDIS stage; industrial automation OWL DL ontology nearing ISO publication
- `allegrograph-85-neuro-symbolic` — v8.5; expanded MCP; Prometheus/Grafana; KG+vector+neuro-symbolic
- `memgraph-atomic-graphrag` — single Cypher GraphRAG; Agentic GraphRAG + Skills + MCP
- `surrealdb-3-unified-agent-memory` — Rust engine; Spectron; Verizon/Tencent/Samsung
- `architecture-beats-model-scale` — 2026 convergence: architecture > model size
- `engram-bi-temporal-memory-engine` — 83.6% LME_S vs 73.2% full-context; 8× fewer tokens
- `sage-write-side-novelty-gate` — vMF gate; 3.4× API cost / 2.5× latency vs Mem0
- `tokenpilot-cache-efficient-context` — 61-87% cost cut; KV cache stable
- `agenticts-bounded-memory-testbed` — Slay the Spire 2; 298 trajectories; 5 per-decision slots
- `mempalace-zero-api-spatial-memory` — 56K stars; 96.6% Recall@5; 36 MCP tools; no API calls
- `ontology-dilution-problem` — "ontology escaped technical meaning into marketing" (Year of Graph Vol.31)
- `selective-ontology-injection-best-practice` — selective > always-on; full ontological context displaces parametric
- `ontology-guardrails-framing` — Latent Space July 30; Coyle/Eifrem/Idehen; 36-46% multi-hop gains
- `cn-llms-reshape-ontology-engineering` — TBox by LLM; ABox human-validated; CSDN
- `jp-layered-implementation-path` — Semantic Layer → Lightweight Ontology → MCP; Gartner 40% failure
- `okf-v01-structural-interoperability` — v0.1 June 12; v0.2 July 25; mcp-memory implements
- `memory-agent-bench-four-competencies` — ICLR 2026; 4 competencies; all methods fall short
- `letta-pro-cloud-tier` — Agents SDK Aug 2026; MemFS+dreaming; $20/mo Pro; Letta Code #1
- `zep-ce-retired-graphiti-open-source` — 30K+ stars; still at v0.29.3 (July 27); no new stable release
- `memora-microsoft-icml-2026` — 98% token reduction; 86.3%/87.4% LoCoMo/LME
- `fabric-iq-ontology-mcp` — public MCP endpoints Preview; external agents ground via MCP
- `mcp-ontology-integration-protocol` — all hyperscalers aligned; 10+ tools MCP-native
- `ontology-as-reliability-infrastructure` — EN/JP/CN independent convergence on ontology-as-reliability
- `benchmark-proliferation-memory` — 6+ benchmarks; vendor scores inflate 20pp; non-portable
- `evomembench-no-single-memory-form` — 15-system study; no dominant memory form
- `napmem-active-memory-navigation-rl` — RL active navigation; agents learn which memory to consult
- `placemem-compute-aware-memory-plane` — versioned capsules; cross-agent sharing
- `agento-owl-rdf-agentic-ontology` — ESWC 2026; 66 workflows; 4 frameworks; OWL/RDF
- `always-on-agents-survey` — 435-paper; AOEP-v0 protocol
- `ontobricks-open-ontologies-mcp` — Rust MCP server; Oxigraph+OWL2-DL+SHACL+SPARQL
- `eticas-ai-risk-taxonomy-v2` — SKOS/JSON-LD; 76 subcategories; 18 framework mappings
- `hn-5-mistakes-kg-memory` — POLE+O; schema decides everything; invalidation unsolved
- `neo4j-pole-o-hallucination-reduction` — 36-46% accuracy gains; 40%+ hallucination reduction
- `memdelta-benchmark-nonportability` — embedding swap flips rankings 6.2pp
- `eywa-evidence-before-belief` — provenance-grounded; SOTA long-horizon benchmarks
- `ember-budgeted-evidence-retention` — fixed-budget write-side control
- `projectmem-memory-as-governance` — 14 MCP tools; MIT
- `cn-ontology-strategic-return` — property graphs over OWL/RDF; KG as grounding not inference
- `tencent-tbox-abox-framing` — TBox/ABox two-stage; LLM generates TBox, human validates ABox
- `ontology-interoperability-lifecycle-framework` — 3-phase: ODPs + Matching + Validation
- `trust-certificates-pre-deployment` — formal ontology-backed certification; no production pilots
- `vector-db-market-growth` — $3.2B→$8.95B at 27.5% CAGR; Qdrant $50M Series B
- `neo4j-thin-agents-graphsummit` — ZS case study; Eifrem "Thinner Agents on Smarter Substrate"

---

## Cross-Source Patterns

### Pattern 1: Deterministic + Provenance as Enterprise Differentiator (🌐 Global)
- Semantica [new]: deterministic reasoning (Rete/Datalog/SPARQL, no LLM); W3C PROV-O on every fact → audit that survives regulatory scrutiny
- Starling UCA [new]: retrieval by coordinate (fixed semantic address, not nearest-neighbor) → zero approximation in regulated domains
- Oracle AI Agent Memory 26.6: 10.7× token reduction; auditable metadata inheritance [ongoing]
- MOSS (arXiv:2607.04391): symbolic SQL memory replacing embedding search; fully auditable [ongoing]
- **Pattern:** A distinct enterprise tier is forming around deterministic reasoning + provenance — not better accuracy, but auditable accuracy. EU AI Act/GDPR/HIPAA are driving it.

### Pattern 2: MemoraX AI Becoming the CN "Standard Bearer" for LTM Infrastructure (🇨🇳 CN)
- Huawei Cloud strategic cooperation [update]: only LTM-focused partner in Huawei Cloud ecosystem
- 3 rounds / 5 months (Apr→May→Aug 12); hundreds of millions CNY
- Coverage expanding: Tencent News, 36kr, ITBear, sohu, ifeng — mainstream Chinese tech press
- Endogenous memory (ReMix ICLR 2026) contrasts structurally with all shipping retrieval-based systems
- **Pattern:** MemoraX is not just well-funded — Huawei Cloud alignment signals it may become the default long-term memory layer for CN hyperscaler deployments, similar to how AWS COA is playing for the enterprise ontology space in the West.

### Pattern 3: Catalog Indexing as the Next Memory Scaling Wall (🇯🇵 JP, 🌐 Global)
- LayerX Engineering Blog (June 3, 2026): catalog metadata alone = 228% of 200k context window at scale; only 11.3% of LLM-generated memory files have `related` connections
- Self-GC (arXiv:2607.00692): 43.95% token pruning needed just for lifecycle management [ongoing]
- MemTool (arXiv:2507.21428): dynamic tool-context management needed when fixed windows can't hold all tool contexts [ongoing]
- Hindsight v0.9.0 Knowledge Pages: wiki-shaped index over memory-shaped engine [ongoing]
- **Pattern:** The industry's next memory problem is not retrieval accuracy — it's that the INDEX of what you have stored overflows the context window before retrieval even begins.

### Pattern 4: Neo4j Building Full Enterprise Memory Stack (🌐 Global)
- neo4j-labs/agent-memory NAMS [new]: POLE+O ontology, 3-tier memory, Python+TypeScript, hosted service, ontology import/diff/migrate
- arXiv:2607.26520: graph-native bitemporal store [ongoing]
- semvec blog (Aug 4): constant token cost per turn [ongoing]
- TWIN4J: ZS case study, "Thinner Agents on Smarter Substrate" framing [ongoing]
- **Pattern:** Neo4j is assembling a complete enterprise agent memory stack — from research papers to Labs products to hosted services — positioning the graph as the canonical substrate for agent state.

### Pattern 5: Two-Layer Ontology Split Emerging as Industry Consensus (🌐 Global)
- contextandchaos (August 2026): "canonical ontology that changes slowly (governed like a product) + task-local ephemeral ontology (constructed on the fly from traces)"
- Databricks Genie Ontology: automated ontology extraction from tables/queries/dashboards [ongoing]
- AWS COA: Scan→Model→Serve pipeline; domain experts validate [ongoing]
- Starling UCA [new]: fixed semantic addresses for canonical knowledge
- OntoCast [new]: co-evolves ontology and facts simultaneously (addresses the ephemeral layer)
- **Pattern:** Enterprise canonical ontology (slow, governed, auditable) + task-local ephemeral ontology (fast, agent-generated, trace-derived) — the same clean/dirty separation that Databricks applied to data lakes.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| growgraph | Show HN: OntoCast – ontology-assisted KG generation | — | — | "co-evolves domain ontologies and fact graphs in parallel map/reduce pipeline" | https://news.ycombinator.com/item?id=44423406 |
| engomez | Show HN: OpenKnowledge – open source AI-first alternative to Obsidian/Notion | 381 | 173 | "WYSIWYG markdown + built-in MCP/Skills integrations" | https://news.ycombinator.com/item?id=48675435 |
| fellowgeek | Show HN: MCP Memory – Fast Agent Memory Using Google's OKF and SQLite FTS5 | — | — | First OKF v0.2 MCP memory implementation | https://news.ycombinator.com/item?id=49286073 |
| (unknown) | Show HN: A public AI whose memory is shared across all users | — | — | Inverts per-user private memory topology | https://news.ycombinator.com/item?id=49319814 |

**Web (Global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Semantica GitHub | https://github.com/semantica-agi/semantica | NEW: graph-native provenance layer; W3C PROV-O; deterministic; MIT |
| 🌐 | MoClaw/Semantica blog | https://moclaw.ai/blog/what-is-semantica | Semantica deep-dive; Aug 10, 2026 coverage |
| 🌐 | Starling itbrief.asia | https://itbrief.asia/story/starling-open-sources-ai-memory-standard-for-organisations | NEW: UCA open standard; retrieval by coordinate; CC license |
| 🌐 | Starling research-live | https://www.research-live.com/article/news/starling-mx-launches-open-standard-for-working-with-ai-models/id/5151987 | Starling MX beta launch; $99/mo |
| 🌐 | Neo4j Labs agent-memory | https://neo4j.com/labs/agent-memory/ | NEW: NAMS hosted service; POLE+O; 3-tier memory |
| 🌐 | Neo4j agent-memory CHANGELOG | https://github.com/neo4j-labs/agent-memory/blob/main/CHANGELOG.md | v0.5.0 May 30: first-class ontology surface; unreleased: ontology import/diff/migrate |
| 🌐 | OntoCast GitHub | https://github.com/growgraph/ontocast | NEW: ontology-assisted KG extraction; v0.3.0 March 10, 2026 |
| 🌐 | OntoCast HN | https://news.ycombinator.com/item?id=44423406 | Show HN (June 2025); still active project |
| 🌐 | Graphiti releases | https://github.com/getzep/graphiti/releases | Still at v0.29.3 (July 27); no new stable release |
| 🌐 | Letta Next Phase | https://www.letta.com/blog/our-next-phase/ | Agents SDK Aug 2026; MemFS+dreaming+mods |
| 🌐 | Letta MemFS docs | https://docs.letta.com/concepts/memfs | MemFS specification; git-backed memory |
| 🌐 | Letta Context Repos | https://www.letta.com/blog/context-repositories/ | Context Repositories as git-backed MemFS |
| 🌐 | Cognee changelog | https://www.cognee.ai/changelog | v1.5.0.dev5 Aug 20; dev2 Aug 15; dataset overview index |
| 🌐 | Hindsight v0.9.0 | https://hindsight.vectorize.io/blog/2026/08/06/hindsight-0-9-0 | Knowledge Pages; unified plugin for 10 agents |
| 🌐 | Mem0 releases | https://releasebot.io/updates/mem0 | Editor plugin v0.2.11; project/global scopes; Antigravity |
| 🌐 | Databricks Aug notes | https://docs.databricks.com/aws/en/ai-bi/release-notes/2026 | Aug 6: ontology by default; Aug 13: snippets all customers |
| 🌐 | OKF spec GitHub | https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md | v0.2 still current; no v0.3 |
| 🌐 | Apache Ossie | https://ossie.apache.org/updates/ | No update since July 10 |
| 🌐 | AWS COA | https://github.com/aws/context-ontology-accelerator | No August update; GA July 31 |
| 🌐 | contextandchaos | https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic | Two-layer ontology split thesis |
| 🌐 | Ken Huang substack | https://kenhuangus.substack.com/p/why-ontology-matters-for-agentic | Ontology as governance layer (Aug 2026) |
| 🌐 | KGC 2026 Notes | https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5 | "Production failures are representation failures" |
| 🌐 | Enterprise Knowledge | https://enterprise-knowledge.com/ontology-and-knowledge-graph-in-the-age-of-ai-and-agents/ | Ontology and KG in age of AI agents |
| 🌐 | Mnemoverse Q3 | https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3 | Vendor benchmark inflation; Mem0 −20.6pp |
| 🌐 | Vectorize Mem0 vs Zep | https://vectorize.io/articles/mem0-vs-zep | Graphiti 63.8% vs Mem0 49.0% LongMemEval |
| 🌐 | Atlan (multiple) | https://atlan.com/know/ai-agent/knowledge-graph-for-ai-agents/ | KG for AI agents guide |
| 🌐 | Neo4j Lenny's Memory | https://neo4j.com/blog/developer/meet-lennys-memory-building-context-graphs-for-ai-agents/ | Context graphs for AI agents |
| 🌐 | OxfordSemantic (Feb 2026) | https://www.oxfordsemantic.tech/blog/what-is-knowledge-based-ai-what-can-owl-ontological-reasoning-do-how-can-datalog-reason-with-filters-aggregates-negations-and-binds | OWL/Datalog for knowledge-based AI |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita/@cvusk | https://qiita.com/cvusk/items/78e1f144069f04a5702e | Feb 22: graph-based agent memory design patterns; 5 architecture types |
| 🇯🇵 | Qiita/@hisaho | https://qiita.com/hisaho/items/175ca3f80f35abf195f0 | Jan 22: AI for Science + GraphRAG × ontology engineering |
| 🇯🇵 | Qiita/@M_Ozu | https://qiita.com/M_Ozu/items/346f6c8ab4b662a08f3e | Aug 13: "different dept answers = missing ontology" |
| 🇯🇵 | Qiita/@ariefwara | https://qiita.com/ariefwara/items/ffe85f2802c8b4f6464a | Context layer design to solve agent forgetting |
| 🇯🇵 | Zenn/colorfulwave | https://zenn.dev/colorfulwave/articles/eb6d5dfead5ae3 | Apr 9: SharedMemoryServer MCP; blackboard architecture for multi-agent |
| 🇯🇵 | Zenn/proper_willet | https://zenn.dev/proper_willet/articles/1925e7ebcb81db | Selective memory + bi-layer hot/cold design |
| 🇯🇵 | Zenn/knowledgework | https://zenn.dev/knowledgework/articles/intro-context-engineering-on-dev-ai-coding-agent | Context engineering intro for coding agents |
| 🇯🇵 | LayerX blog | https://tech.layerx.co.jp/entry/ai-agent-long-term-memory-simulation | Jun 3: 4,552 memories simulation; catalog = 228% of context |
| 🇯🇵 | jisaku.com | https://jisaku.com/posts/ai-agent-memory-rag-guide | Updated Aug 18; Qdrant/Milvus/Weaviate stack |
| 🇯🇵 | product.hiway.app | https://product.hiway.app/blog/ontology/ | Ontology as meaning design for AI-native CRM |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | 36kr | https://www.36kr.com/p/3935938639107720 | MemoraX Seed++ Aug 12; hundreds of millions CNY |
| 🇨🇳 | 36kr (EN) | https://eu.36kr.com/en/p/3785834045583875 | "Endogenous memory" paradigm coverage |
| 🇨🇳 | itbear.com.cn | https://www.itbear.com.cn/html/2026-08/1495089.html | Huawei Cloud + MemoraX cooperation: only LTM partner |
| 🇨🇳 | itbear.com.cn | https://www.itbear.com.cn/html/2026-08/1495495.html | MemoraX 3 rounds / 5 months — market framing |
| 🇨🇳 | sohu.com | https://m.sohu.com/a/1061900704_100032554 | Former Huawei Chief Expert leads MemoraX Seed++ |
| 🇨🇳 | qq.com | https://news.qq.com/rain/a/20260812A04HY300 | He Jianye: 3 rounds / 6 months (Tencent News) |
| 🇨🇳 | aibase.com | https://news.aibase.com/news/28163 | MemoraX Seed+; ReMix ICLR 2026 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1986863263875625084 | Ontology as core engineering tool; deep analysis |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2020154230825074757 | TBox/ABox epistemological framing (KG modeling) |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1986213905320661415 | 10,000-word agent memory survey (PKU/Fudan/NUS) |
| 🇨🇳 | CSDN/techforward | https://blog.csdn.net/techforward/article/details/163702573 | MemoraX multi-scenario deployment |
| 🇨🇳 | 53AI | https://www.53ai.com/news/knowledgegraph/2026022019635.html | OpenKG: SPG+KAG, SkillNet, OneGraph |
| 🇨🇳 | pengjiyuan.github.io | https://pengjiyuan.github.io/articles/agent-memory-persistence-2026/ | Agent memory: from "goldfish" to "old partner" |
| 🇨🇳 | ai-insight.org | https://www.ai-insight.org/reports/agent-memory-2026 | Memory: from context concatenation → OS-level virtual memory |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ (not accessible)
├─ 🔵 X: 0 posts │ (excluded per spec)
├─ 🔴 YouTube: 0 videos │ (not searched this pass)
├─ 🟢 HN: 4 threads │ 381+ pts (OpenKnowledge)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ (no on-topic signal; bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 90 pages │ 🇯🇵 10 │ 🇨🇳 14
└─ 🗣️ Top voices: He Jianye (MemoraX/Huawei), @cvusk (Qiita), @ayato (Zenn), GrowGraph team (OntoCast), Starling Memory Works
```

---

## Out of Scope but Notable

- **Cognee Two-Layer Architecture (v1.5.0):** Dataset overview index as "macro-ontology" over documents — if this pattern generalizes, it solves the catalog-overflow problem LayerX found (JP, June 2026). Potentially relevant to paradigm-watch: metadata index as a new type of memory tier.
- **Starling UCA "retrieval by coordinate":** Fundamentally different retrieval primitive from vector similarity or graph traversal — semantic addresses are deterministic. If it gains adoption, it could end the vector-vs-graph retrieval debate by sidestepping it. Worth watching.
- **contextandchaos "Two-Layer Ontology Split" thesis:** Canonical ontology (slow/governed) + ephemeral ontology (fast/trace-derived) matches how modern data platforms split curated warehouse from landing zone. Could become the dominant enterprise agent architecture framing.

---

## Data Gaps

- **Reddit:** Not accessible (400/403 errors); r/MachineLearning, r/KnowledgeGraph likely have active threads
- **X/Twitter:** Excluded per spec
- **YouTube:** Not searched this pass
- **Bluesky:** Searched; no on-topic signal; bluesky=OK — low Bluesky presence for this niche
- **DuckDuckGo HTML endpoint (JP/CN):** Returned CAPTCHA challenges for both Japanese and Chinese queries; fell back to WebSearch with native-language terms
- **CSDN August 19, 2026 article:** URL returned 521 error; content not accessible
- **TWIN4J (Neo4j weekly) Aug 18-21 edition:** URL returned 403; most recent confirmed TWIN4J content from Aug 7
- **Graphiti v0.30:** Still in pre-release; v0.29.3 is latest stable (July 27); no new stable release
- **Starling UCA announcement date:** Coverage confirmed but exact publication date unclear; treat as pre-Aug-21 2026
- **Coverage estimate:** ~73-76% of ideal full-platform run (missing Reddit, YouTube; partial Zhihu; TWIN4J latest blocked)

---

## Key Quotes

> "The catalog metadata alone occupied 228% of the 200k context window." — LayerX AI Workforce team, on their 4,552-memory agent simulation ([link](https://tech.layerx.co.jp/entry/ai-agent-long-term-memory-simulation)) 🇯🇵

> "Months later, when someone asks why the system decided what it decided, you need an answer that survives scrutiny." — MoClaw/Semantica, on W3C PROV-O audit trails ([link](https://moclaw.ai/blog/what-is-semantica)) 🌐

> "华为云合作厂商中唯一聚焦长期记忆的企业" ("The only entity among Huawei Cloud partners focused on the long-term memory track.") — ITBear coverage of MemoraX AI + Huawei Cloud cooperation ([link](https://www.itbear.com.cn/html/2026-08/1495089.html)) 🇨🇳

> "Most production failures attributed to 'model limitations' or 'prompt engineering' are actually representation failures — knowledge graphs are the substrate on which production AI stands." — Notes from KGC 2026, Giuseppe Futia ([link](https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5)) 🌐

> "2026 is likely to be the year ontology splits into two layers: an enterprise canonical ontology that changes slowly and is governed like a product, and a task-local ephemeral ontology constructed on the fly from traces." — contextandchaos substack ([link](https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic)) 🌐

> "モデルをより賢いものに替えても、この食い違いは直りません。" ("Replacing the model with a smarter one won't fix this discrepancy.") — @M_Ozu on Qiita, August 13, 2026 ([link](https://qiita.com/M_Ozu/items/346f6c8ab4b662a08f3e)) 🇯🇵

> "Ontology snippets in the Genie Ontology are now available to all customers. Customers no longer need to request access." — Databricks release notes, August 13, 2026 ([link](https://docs.databricks.com/aws/en/ai-bi/release-notes/2026)) 🌐

> "Only 11.3% of files contained `related` field connections — knowledge graphs are extremely sparse in practice when relying on LLM generation alone." — LayerX AI Workforce team ([link](https://tech.layerx.co.jp/entry/ai-agent-long-term-memory-simulation)) 🇯🇵
