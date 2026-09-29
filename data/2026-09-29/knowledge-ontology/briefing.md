# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-09-29
**Query type:** GENERAL
**Sources:** WebSearch, WebFetch, Zenn, Qiita, CSDN, Juejin, Zhihu, Sina Finance, arXiv, GlobeNewswire, Neo4j Blog, Cognee, Hindsight, Graphiti, Letta, CyberAgent Dev Blog, Bluesky (partial)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 thread | low engagement | Sep "What are you working on?" — Tenjin/Socratix noted |
| Bluesky | 1 account | — | 🦋 SEMANTiCS conference account; ORKG award |
| Web (global) | 42 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Zenn, CyberAgent Dev Blog, LayerX, Acroquest |
| Web (China) | 9 pages | — | 🇨🇳 Juejin, Zhihu, CSDN, Sina, 163.com |
| arXiv | 5 papers | — | 🌐 Sep 4–15 2026 submissions |

---

## Synthesized Findings

### 1. [update] AML Cycle 2 opens with Coding + Multimodal tracks

**Claim:** AML Cycle 2 launched Sep 28 2026 — expands from 1 track to 3, adding Coding Memory and Multimodal Memory evaluation alongside Textual Memory; $22K+ open-source prize pool, deadline Oct 31.
**Evidence:**
- 3 tracks: Textual Memory, Coding Memory, Multimodal Memory
- Two divisions: Open-source Methods + Commercial Products; $3K per-track first-place
- Application deadline: Oct 31, evaluation closes Nov 4, results mid-November
- Cycle 1 context: 100+ teams, 300K+ website visits, MemoraX commercial #1 at 58.02 AML score
- Platform: participants provide Add + Search APIs; harness handles Answer + Evaluation + leaderboard
- Sources: [GlobeNewswire](https://www.globenewswire.com/news-release/2026/09/28/3369903/0/en/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory.html), [AML](https://agentmemoryleaderboard.ai/), [Manila Times](https://www.manilatimes.net/2026/09/28/tmt-newswire/globenewswire/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory/2434197)

### 2. [new] KG-fixed format is the only memory type that survives model upgrades intact

**Claim:** arXiv:2609.05339 (Sep 4 2026) shows fixed-schema knowledge graphs change accuracy by only ±0.0020 following a model writer swap; compressed NOTES shift by +9.91 or −13.28pp depending on migration direction.
**Evidence:**
- 48 synthetic test histories, 4 formats: LC-RAW, RAG, NOTES, KG-fixed; 2 open-weight models (<10B)
- KG-fixed: ±0.0020 accuracy change — effectively model-agnostic
- NOTES: asymmetric degradation (+9.91 / −13.28pp) — "a new model may interpret old notes differently"
- RAG: partial embedding migrations recover only 4.96 of 11.90pp potential improvement; 34/48 cases recoverable if raw source histories retained
- Practical implication: memory portability requires "direction-specific migration testing, strict embedding space isolation, and retention of source histories"
- Sources: [arXiv:2609.05339](https://arxiv.org/abs/2609.05339), [aiweekly.co](https://aiweekly.co/alerts/study-knowledge-graphs-beat-notes-when-agents-change-models)

### 3. [new] MOOSEDev: ontology-grounded project memory achieves 0.98–1.00 recall on negation/supersession queries

**Claim:** MOOSEDev (arXiv:2608.13662, NeSy 2026 Industry Track) gives coding agents typed project KG via MCP; supersession and negation queries: 0.98–1.00 recall vs 6–27% for vector-memory baseline.
**Evidence:**
- System: MOOSE neurosymbolic engine; 2 small ontologies (software-engineering + software-architecture vocabularies)
- Captures: architectural decisions, constraints, rationales, lessons, anti-patterns with supersession links and provenance
- Eval: 835 typed records from neutral public corpus
- Supersession/negation: **0.98–1.00 recall** vs 6–27% vector baseline
- Set-completeness: **0.98–1.00** — vector baseline cannot answer "list all X" reliably
- Relevance and token cost: equivalent to vector baseline
- Exposed via MCP: 4 tool groups (typed capture, context retrieval/NL query/SPARQL, lifecycle, integrity)
- Sources: [arXiv:2608.13662](https://arxiv.org/abs/2608.13662), [GitHub](https://github.com/Trivyn/moosedev), [awesomepapers.io](https://awesomepapers.io/ai-agents/papers/2608.13662)

### 4. [update] Hindsight Cloud 0.10.0: screenshot memory + Hermes plugin separation

**Claim:** Hindsight Cloud 0.10.0 (Sep 21 2026) adds screenshots as first-class memory with attachment provenance; Sep 23 Hermes plugin migration moves Hindsight out of Hermes core into own maintainer repo.
**Evidence:**
- Screenshot memory: images read inline with text; "a fact cites an image only when it could not have been stated without looking at it"
- Prompt preview endpoint: examines exact prompt before token spend — zero cost (no model call, no DB write)
- Fuzzy tag matching: trigram similarity resolves `typescropt`→`typescript`; no predefined vocabulary needed
- KB portability: whole-bank exports now include synthesized knowledge pages and mental models
- Hermes migration (Sep 23): install now via `hermes plugins install hindsight`; `hermes memory setup` required (not `hermes plugins enable`)
- 503 capacity refusals now possible on synchronous retain during peak load; retry guidance included
- Sources: [cloud 0.10.0 blog](https://hindsight.vectorize.io/blog/2026/09/21/hindsight-cloud-0-10-0), [Hermes catalog blog](https://hindsight.vectorize.io/blog/2026/09/25/hindsight-hermes-plugin-catalog)

### 5. [update] Cognee v1.6.0: keyless local workflows + BEAM benchmark leadership (79%@100K)

**Claim:** Cognee v1.6.0 (Sep 18 2026) enables keyless workflows (local model, no cloud LLM key); BEAM scores 79%@100K / 67%@10M vs prior best 73.4%/64.1%; entire stack runs on single Postgres instance.
**Evidence:**
- v1.6.0 (59 PRs): local model download on first use; LLM-dependent stages skip when no key configured; pipeline recovery preserves completed docs after crashes; dataset embedding model tracked to prevent mismatches
- Four-verb API: remember/recall/improve/forget — "improve" re-weights memory from actual agent usage
- BEAM: 79%@100K / 67%@10M (previous best 73.4%/64.1%); token usage stays flat as data grows
- Postgres-native: graph + vectors + sessions + usage data in single Postgres (no separate graph DB)
- Rust core: on-device and edge deployment; TypeScript SDK
- Migration paths from Mem0, Zep, Graphiti, Letta
- Sources: [Cognee 1.0 newsroom](https://www.cognee.ai/newsroom/cognee-1-0-is-live), [changelog](https://www.cognee.ai/changelog), [PyPI](https://pypi.org/project/cognee/1.6.1/)

### 6. [update] Graphiti v0.30.2: external graph stores removed from OSS

**Claim:** Graphiti (Zep, v0.30.2, Sep 2026) removes external graph store integrations (Neo4j/Memgraph/Kuzu/Apache AGE/Neptune) from OSS SDKs; entities now linked at write time and boosted at search time natively.
**Evidence:**
- ~30,800 GitHub stars; Apache-2.0; P95 300ms hybrid search (semantic+BM25+graph)
- MCP 1.0 server stable; Klaviyo released `graphiti_mcp` on top
- Temporal knowledge graph: every fact is an edge with validity window; newer fact closes older one
- External stores removed: simplifies OSS deployment — no Neo4j/Memgraph cluster required; commercial Zep offering built on top retains these integrations
- Sources: [GitHub releases](https://github.com/getzep/graphiti/releases), [Graphiti vs Mem0](https://renezander.com/guides/graphiti-vs-mem0/), [Klaviyo graphiti_mcp](https://github.com/klaviyo/graphiti_mcp)

### 7. [update] EKAW 2026 starts today — first day in Torino

**Claim:** EKAW 2026 (25th edition, Sep 29–Oct 1, Torino) OPENS TODAY; theme "New Frontiers in Knowledge Engineering" covering GenAI + neuro-symbolic + agentic AI + EU AI Act.
**Evidence:**
- Pre-conference workshops today: X-TAIL (long-tail KG with LLMs), KM4LAW, PwM3 (semantics for games)
- Accepted paper: arXiv:2605.22093 KG Re-engineering Along Ontological Continuum; 5 open research challenges for KG/neuro-symbolic integration
- Venue: University of Torino; turismotorino.org confirms event
- Sources: [ekaw2026.di.unito.it](https://ekaw2026.di.unito.it/), [call for papers](https://ekaw2026.di.unito.it/calls/call-for-papers)

### 8. [new] Industrial KG unification: 287 MCP tools expose 27K-triple SPARQL graph; 69% of signals require cross-system joins

**Claim:** arXiv:2608.24918 unifies 11 heterogeneous manufacturing systems via ontology-driven RDF KG; exposes 287 MCP tools; blocking 24 cross-system tools drops recall from 1.00 to 0.31.
**Evidence:**
- 78 RDFS classes, 108 object properties, 243 data properties; standards: ISA-95, OPC UA, eClass, AAS, RAMI 4.0
- Unified graph: ~27,800 RDF triples (2,200 TBox + 25,600 ABox) generated in ~5.2s on commodity hardware
- 287 MCP tools as SPARQL-native semantic layer for LLM agents
- **Ablation:** blocking 24 cross-system tools → recall drops 1.00→0.31; "69% of discoverable signals require cross-system graph joins unavailable to single-source analysis"
- 5 industry templates: aerospace, CPG, pharma, medical devices, turbine blades
- Sources: [arXiv:2608.24918](https://arxiv.org/abs/2608.24918)

### 9. [new] EvoGraph-Mem: Failure-aware editable graph memory addresses memory pollution

**Claim:** EvoGraph-Mem (arXiv:2608.11248, Aug 3 2026) tracks positive/negative evidence + activation state per insight node; outperforms append-only memory baselines; "append-only memory is insufficient for long-horizon tasks."
**Evidence:**
- Problem: previously distilled insights become outdated/over-generalized/harmful under new task contexts → memory pollution
- 3 components per node: positive evidence, negative evidence, activation state
- Graph controller: post-task updates — retention, archiving, revision, integration of new insights
- Utility-aware retrieval: selective access based on reliability signals
- Consistently outperforms representative memory-based agent baselines across backbone models
- Sources: [arXiv:2608.11248](https://arxiv.org/abs/2608.11248)

### 10. [new] LLM-guided ontology KG construction for industrial text (IJCKG 2026)

**Claim:** arXiv:2609.31663 (Sep 15 2026) shows schema-guided prompting significantly improves ontology-driven KG extraction; quantized 7B–32B models provide practical compute efficiency for domain-specific industrial documents.
**Evidence:**
- Authors: Abdelhadi Belfadel et al.; venue: IJCKG 2026 (Nov, Bangkok)
- Pipeline: entity/relation extraction → RDF triple generation → OWL ontology construction → external KB enrichment → quality assessment → KG population
- Test: 80 manually annotated private reports from French power-grid incident documentation
- Key finding: schema-guided prompting "significantly improves extraction quality"; quantized models "effective trade-off between performance and computational cost"
- Enables local OSS deployment without cloud LLM dependencies
- Sources: [arXiv:2609.31663](https://arxiv.org/abs/2609.31663)

### 11. [new] trikedb (CyberAgent): org ontology as lightweight YAML/RDF with Claude MCP — 88.7% accuracy 🇯🇵

**Claim:** trikedb (Sep 4 2026, CyberAgent) stores organizational policies and ontologies as single YAML files with RDF backing + Oxigraph SPARQL + MCP server; 88.7% accuracy on WebQSP at <3K document scale.
**Evidence:**
- Author: Ryuto Yoda (CyberAgent Data Visualization Team)
- Problem: markdown business rules go stale; KG format enforces declared predicates only
- 5 query methods: vector search, pattern matching, SPARQL 1.1, semantic find (search+filter), ontology inspection
- model2vec 256-dim multilingual static embeddings (no API dependency)
- Inferred facts materialized with `inferred: true` tag for auditability
- MCP server for Claude; HTTP + OAuth 2.1 for team sharing; UI as single self-contained HTML with browser SPARQL
- WebQSP (300 questions, 250-triple context): semantic search **88.7%**; + entity filtering **89.3%**
- Performance ceiling: ~3,000 embedded documents
- Sources: [CyberAgent blog](https://developers.cyberagent.co.jp/blog/archives/65814/)

### 12. [update] Letta MemFS: agent memory blocks now git-versioned

**Claim:** Letta v0.32.11 (Sep 15 2026) ships Memory Filesystem (experimental) — agent memory blocks sync to `.letta/memory/` local files and are git-versioned; `/memory-repository set git@github.com:...` syncs to own repo.
**Evidence:**
- MemFS versions entire context including memory blocks via git
- `/sleeptime` configures periodic consolidation (dreaming); `/palace` shows memory contents
- Agents programmatically rewrite own system prompt via memory blocks; learn skills from experience
- Letta Code updated Sep 20 2026
- Sources: [changelog](https://docs.letta.com/letta-agent/changelog/), [Letta docs](https://docs.letta.com/concepts/memfs)

---

**Still true** (ongoing threads, no new facts this run):
- hindsight-memory-benchmark-leader: Hindsight leads SDE-bench; prior v0.10.0 (Sep 14) already logged
- mem0-v2-token-efficiency: mem0 61K+ stars, OSS v3 algorithm, mem0-strands for AWS; no Sep 29 release
- okf-v02-provenance-trust: OKF still at v0.2, no v0.3; mcp-memory and WitsCode implementations active
- cognee-1-0-four-verb-api: merged into thread #5 above
- parametric-kg-storage-retrieval-gap: arXiv:2608.25489 retrieval failure at chance (ongoing)
- selective-forgetting-kg-vs-flat: graph memory F1=0.417 < flat baseline 0.468 on LongMemEval (ongoing)
- megamem-ultra-large-context-retrieval: EnterpriseRAG-Bench 68.22→82.26 (ongoing)
- graph-personalized-memory-survey-ickg2026: ICKG 2026 lifecycle survey (ongoing)
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview (ongoing)
- jp-ontology-to-tool-mechanical-generation: Zenn/@mk0bayashi 58-tool generation from YAML ontology (ongoing)
- mem0-strands-osv3-algorithm: single-pass ADD-only extraction, hybrid search (ongoing)
- graphwise-events-oct-2026: AI Summit Oct 7-8 + SLS Vienna Oct 14-15 — upcoming
- graphwise-oakley-semantic-layer-pe: Oakley Capital PE investment (ongoing)
- semantics-2026-ghent: SEMANTiCS 2026 (Sep 15-17 Ghent) — concluded
- jedify-context-graph-benchmark: 75% token savings, 87% SQL accuracy (ongoing)
- memverge-memorybox-memory-sovereignty: 记忆主权 closed beta (ongoing)
- neo4j-create-context-graph-cli: POLE+O CLI scaffolding (ongoing)
- layerx-memory-scaling-failure: dreaming collapses at 4,552 memories (ongoing)
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1, Cycle 2 open now
- palantir-superrepo-ontology-as-code: TypeScript ontology-as-code (ongoing)
- ozbrain-shared-cross-agent-knowledge: shared MCP knowledge store (ongoing)
- onton-ontology-1-neurosymbolic-trust: P@10 0.630 vs Google 0.543 (ongoing)
- metaphactory-6-ontopic-virtual-kg: Digital Science / Ontopic; metaphactory 5.9 Semantic Modeling Assistant (ongoing)
- magg-governed-kg-construction: multi-agent governed KG +47% F1 (ongoing)
- benchmark-vendor-inflation-measured: Mnemoverse Q3 confirms 20pp inflation (ongoing)
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference (ongoing)
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale (ongoing)
- jp-two-layer-memory-write-gate: hot/cold two-layer memory (ongoing)
- jp-note-semantic-layer-vs-ontology-failure: 60% failure without SL (ongoing)
- ontologx-autonomous-log-kg: autonomous log→ontology KG (ongoing)
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory paradigm (ongoing)
- databricks-genie-ontology: free through Jan 31 2027, 84.5% accuracy (ongoing)
- jp-coa-deployment-53pct-variance: COA 53% variance elimination (ongoing)
- cn-ontology-strategic-return: KG/ontology strategic return framing (ongoing)
- ontology-guardrails-framing: ontology as AI correctness guardrails (ongoing)
- zep-ce-retired-graphiti-open-source: Graphiti OSS stable, external stores removed (update noted above)
- heimdall-trust-verified-kg-coding: trust-verified cross-repo KG (ongoing)
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction (ongoing)
- msock-intellect-enterprise-spatial-graph: 21-dimensional Enterprise Spatial Graph (ongoing)
- aws-context-ontology-accelerator: months→days ontology authoring (ongoing)
- mnemoverse-hebbian-memory: Hebbian associations across coding agents (ongoing)
- apache-ossie-semantic-interchange: Kyvos joined; Databricks member; no Sep updates (ongoing)
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG (ongoing)
- stardog-bedrock-agentcore-semantic-layer: KG semantic layer + MCP ref arch (ongoing)
- mcp-ontology-integration-protocol: MCP 2026-07-28 final spec (ongoing)
- benchmark-proliferation-memory: 7+ active benchmarks, AML Cycle 2 adds 2 new tracks (ongoing)
- architecture-beats-model-scale: retrieval architecture dominates model scale (ongoing)
- vector-db-market-growth: $3.47B KG market, $3.2B vector DB market (ongoing)
- ontology-as-reliability-infrastructure: EN/JP/CN independently frame ontology as reliability layer (ongoing)
- okf-v01-structural-interoperability: OKF structural (not semantic) interoperability (ongoing)
- sap-knowledge-graph-autonomous-enterprise: 452K tables, 50+ Joule Assistants (ongoing)
- jp-layered-implementation-path: SL→Ontology→MCP path (ongoing)
- jp-qiita-ontology-department-alignment: missing ontology = model quality problem (ongoing)
- jp-zenn-kg-memory-entity-resolution: entity resolution primary barrier (ongoing)
- cn-llms-reshape-ontology-engineering: TBox generative paradigm (ongoing)
- fabric-iq-ontology-mcp: Microsoft Fabric IQ Ontology MCP (ongoing)

---

## Cross-Source Patterns

**1. Model upgrades break memory — KG-fixed uniquely survives (🌐 global)**
- Pattern: Memory format portability has become an explicit engineering concern as model upgrades accelerate
- Platforms: arXiv:2609.05339, aiweekly.co, renezander.com guides
- Quote: "Fixed-schema knowledge graphs transfer reliably — accuracy ±0.0020 following a writer swap" — arXiv:2609.05339 ([link](https://arxiv.org/abs/2609.05339))

**2. Ontology for structured recall: 0.98–1.00 recall on queries vector cannot answer (🌐 global)**
- Pattern: KG + ontology grounding achieves near-perfect recall on set-completeness, negation, and supersession queries where vector memory fails (6–27%)
- Platforms: MOOSEDev arXiv:2608.13662, trikedb (JP), Industrial KG arXiv:2608.24918
- Quote: "Supersession & negation queries: 0.98–1.00 recall vs 6–27% for vector-memory baseline" — MOOSEDev paper ([link](https://arxiv.org/abs/2608.13662))

**3. Memory benchmarks expanding coverage: Coding + Multimodal tracks now official (🌐 global)**
- Pattern: AML Cycle 2 adds Coding Memory and Multimodal Memory as first-class benchmarks; industry acknowledges gap in code/image memory evaluation
- Platforms: AML, Hindsight, Cognee (all competing), Dev.to AML article
- Quote: "The second Agent Memory Challenge…evaluates Agent Memory across Textual Memory, Coding Memory, and Multimodal Memory" — GlobeNewswire ([link](https://www.globenewswire.com/news-release/2026/09/28/3369903/0/en/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory.html))

**4. Lightweight ontology tooling: YAML/RDF over heavy triple-stores (🇯🇵 JP + 🌐 global)**
- Pattern: trikedb (CyberAgent), OntoCast, mcp-memory all demonstrate appetite for sub-3K-document ontology stores that version in git and deploy without JVM/Fuseki
- Platforms: CyberAgent blog, Zenn developer community
- Quote: "データの鮮度が保証される唯一の方法は、知識をクエリ可能なグラフとして保持することだ" ("the only way to guarantee data freshness is to store knowledge as a queryable graph") — Ryuto Yoda, CyberAgent ([link](https://developers.cyberagent.co.jp/blog/archives/65814/))

**5. Append-only memory fails at scale — editable graph memory needed (🌐 global)**
- Pattern: EvoGraph-Mem joins MOOSEDev, MAGG, Cognee's "improve" verb in establishing consensus that append-only stores accumulate stale/harmful insights
- Platforms: arXiv:2608.11248, Cognee v1.6.0 docs
- Quote: "Append-only memory is insufficient for long-horizon tasks" — EvoGraph-Mem ([link](https://arxiv.org/abs/2608.11248))

---

## Per-Platform Tables

**Web (global/English):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | GlobeNewswire | [AML Cycle 2](https://www.globenewswire.com/news-release/2026/09/28/3369903/0/en/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory.html) | AML Cycle 2 opens: 3 tracks, $22K, Oct 31 deadline |
| 🌐 | arXiv:2609.05339 | [link](https://arxiv.org/abs/2609.05339) | KG-fixed ±0.0020 accuracy across model swaps |
| 🌐 | arXiv:2608.13662 | [link](https://arxiv.org/abs/2608.13662) | MOOSEDev: 0.98–1.00 recall on supersession/negation |
| 🌐 | arXiv:2608.24918 | [link](https://arxiv.org/abs/2608.24918) | 287 MCP tools for industrial KG; 69% cross-system loss |
| 🌐 | arXiv:2608.11248 | [link](https://arxiv.org/abs/2608.11248) | EvoGraph-Mem: failure-aware editable graph memory |
| 🌐 | arXiv:2609.31663 | [link](https://arxiv.org/abs/2609.31663) | Schema-guided prompting for ontology KG (IJCKG 2026) |
| 🌐 | Hindsight blog | [cloud 0.10.0](https://hindsight.vectorize.io/blog/2026/09/21/hindsight-cloud-0-10-0) | Screenshot memory, prompt preview, fuzzy tags |
| 🌐 | Hindsight blog | [Hermes catalog](https://hindsight.vectorize.io/blog/2026/09/25/hindsight-hermes-plugin-catalog) | Plugin separation; `hermes plugins install hindsight` |
| 🌐 | Cognee newsroom | [1.0 live](https://www.cognee.ai/newsroom/cognee-1-0-is-live) | BEAM 79%@100K; single Postgres; Rust SDK |
| 🌐 | Cognee changelog | [changelog](https://www.cognee.ai/changelog) | v1.6.0 keyless + pipeline recovery |
| 🌐 | Graphiti GitHub | [releases](https://github.com/getzep/graphiti/releases) | v0.30.2: external stores removed from OSS |
| 🌐 | Letta changelog | [link](https://docs.letta.com/letta-agent/changelog/) | MemFS experimental: git-versioned memory blocks |
| 🌐 | EKAW 2026 | [site](https://ekaw2026.di.unito.it/) | Starts today; 25th conf; neuro-symbolic + agentic |
| 🌐 | Neo4j TWIN4j | [blog](https://neo4j.com/blog/twin4j/this-week-in-neo4j-nodes-agentmemory-graphrag-knowledgelayer-and-more/) | NODES 2026 Nov 12; AgentMemory .NET; NICD 29→66% |
| 🌐 | Graphwise events | [AI Summit](https://graphwise.ai/event/graphwise-ai-summit-2026/) | Oct 7-8 free virtual |
| 🌐 | Graphwise events | [SLS Vienna](https://graphwise.ai/event/semantic-layer-symposium-2026/) | Oct 14-15 Vienna |
| 🌐 | Zenodo AgentKG | [link](https://zenodo.org/records/22682633) | Conversational memory as live queryable KG + MCP |
| 🌐 | Zenodo IAO | [link](https://zenodo.org/records/22956871) | IAO metadata v2026-09-25 maintenance release |
| 🌐 | AML GitHub | [link](https://github.com/AML-memory/agent-memory-leaderboard) | Cycle 2 open, multimodal + coding tracks |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | CyberAgent Dev Blog | [trikedb](https://developers.cyberagent.co.jp/blog/archives/65814/) | Lightweight KG-as-ontology YAML/RDF + MCP; 88.7% WebQSP |
| 🇯🇵 | Zenn/@yasuhito | [AI memory compare](https://zenn.dev/yasuhito/articles/ai-memory-projects-2026) | 6-system comparison; SimpleMem 43.24% F1 at 480s |
| 🇯🇵 | Zenn/@proper_willet | [memory design](https://zenn.dev/proper_willet/articles/1925e7ebcb81db) | Hot/cold two-layer memory with write gates |
| 🇯🇵 | Zenn/knowledge_graph | [KG memory](https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design) | Entity resolution as primary KG barrier |
| 🇯🇵 | Zenn/@deskrex | [MoatになりうるAIエージェントのメモリ](https://zenn.dev/deskrex/articles/9ee6c17f4a420b) | Composer-Reconciler architecture; Devin/Cursor patterns |
| 🇯🇵 | alphaxiv.org | [JP KG taxonomy](https://www.alphaxiv.org/ja/abs/2602.05665) | JP translation of graph-based agent memory taxonomy |
| 🇯🇵 | Acroquest Tech | [OKF vs GraphRAG](https://acro-engineer.hatenablog.com/entry/2026/08/25/120000) | OKF: 100% coverage, 1/26th cost vs GraphRAG |
| 🇯🇵 | note.com/_kihonushi | [semantic layer](https://note.com/_kihonushi/n/nad1b98d60300) | 60% projects fail without semantic layer first |
| 🇯🇵 | Zenn/aws_japan | [COA deploy](https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy) | 53% variance eliminated by ontology |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Juejin | [本体论与KG战略回归](https://juejin.cn/post/7656270771611140123) | Ontology/KG framed as 2026 strategic return |
| 🇨🇳 | Zhihu | [本体论 vs 语义层](https://zhuanlan.zhihu.com/p/2043381232004814555) | Distinguishes ontology vs semantic layer for AI |
| 🇨🇳 | CSDN | [记忆技术演进](https://agent.csdn.net/6a2a6b08662f9a54cb7d0dd2.html) | 4-dimension memory + vector+KG hybrid arch |
| 🇨🇳 | Zhihu | [万字长文](https://zhuanlan.zhihu.com/p/1986213905320661415) | 3-tier memory model; 2026 vector+KG breakthrough |
| 🇨🇳 | Baidu Dev | [五层记忆](https://developer.baidu.com/article/detail.html?id=7220204) | 5-tier memory model for agentic systems |
| 🇨🇳 | Sina Finance | [OceanStor M900](https://finance.sina.com.cn/jjxw/2026-09-21/doc-inisqzxx9238313.shtml) | Huawei M900: 60μs latency, 40TB/s, Sep 17 launch |
| 🇨🇳 | GitHub agents-radar | [ArXiv日报 Sep 23](https://github.com/duanyytop/agents-radar/issues/3433) | Sep 23 ArXiv roundup: agent-centric + reasoning+memory |
| 🇨🇳 | 163.com | [AI记忆元年](https://c.m.163.com/news/a/KKA4PSE005118DFD.html) | 2026 as "first year of AI memory" |
| 🇨🇳 | 163.com | [2026 AI Memory综述](https://www.163.com/dy/article/KJO68UG10511DPVD.html) | 21 frameworks, 20 vector stores survey |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @semantics-conf.bsky.social | SEMANTiCS 2026 conference account; ORKG award announcements | — | [profile](https://bsky.app/profile/semantics-conf.bsky.social) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct Reddit access this run)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 1 thread (Ask HN September 2026 - Tenjin/Socratix mentions)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 1 account (SEMANTiCS conf)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 42 pages │ 🇯🇵 9 │ 🇨🇳 9
└─ 🗣️ Top voices: @yasuhito (Zenn), @deskrex (Zenn), Ryuto Yoda (CyberAgent) │ cognee.ai, hindsight.vectorize.io
```

---

## Out of Scope but Notable

- **Huawei OceanStor M900** (Sep 17 2026): AI-specific hardware storage with 60 microsecond latency (vs milliseconds), 40TB/s aggregate bandwidth, "3+1" architecture targeting agentic AI inference bottleneck; framed as enabling infrastructure for knowledge systems at scale — [Sina Finance](https://finance.sina.com.cn/jjxw/2026-09-21/doc-inisqzxx9238313.shtml). Notable: first hyperscale-vendor hardware explicitly architected around agentic AI memory needs (KV cache library + knowledge base tier).

---

## Data Gaps

- **Reddit:** No direct Reddit access; search queries did not surface recent r/MachineLearning or r/KnowledgeGraphs threads
- **/last30days skill:** Unavailable in this run; English sweep done manually via WebSearch + WebFetch; social platform coverage (TikTok, Instagram) and X/Twitter timeline data therefore absent
- **Bluesky:** Limited direct post content extraction; SEMANTiCS conference Bluesky account found but post content not accessible via WebFetch
- **Medium articles:** Several relevant articles found (Wasowski comparison, KG as memory layer posts) but full content not fetched; summaries only from search results
- **SOURCE HEALTH:** No backends reported DOWN for this run
- **Estimated coverage:** ~65% — good coverage of releases, arXiv papers, JP/CN hubs, and tooling; weaker on social engagement metrics, Reddit, and live conference proceedings from EKAW 2026 (just started today)

---

## Key Quotes

> "Fixed-schema structures transfer reliably — accuracy changing by only ±0.0020 following a writer swap." — arXiv:2609.05339 ([link](https://arxiv.org/abs/2609.05339))

> "Supersession & negation queries: 0.98–1.00 recall vs 6–27% for vector-memory baseline." — MOOSEDev / arXiv:2608.13662 ([link](https://arxiv.org/abs/2608.13662))

> "Blocking 24 cross-system tools reduces recall from 1.00 to 0.31 — 69% of discoverable signals require cross-system graph joins unavailable to single-source analysis." — arXiv:2608.24918 ([link](https://arxiv.org/abs/2608.24918))

> "Append-only memory is insufficient for long-horizon tasks." — EvoGraph-Mem / arXiv:2608.11248 ([link](https://arxiv.org/abs/2608.11248))

> "A fact cites an image only when it could not have been stated without looking at it." — Hindsight Cloud 0.10.0 blog ([link](https://hindsight.vectorize.io/blog/2026/09/21/hindsight-cloud-0-10-0))

> "The core contradiction has shifted from 'can we train it' to 'is inference fast/accurate/affordable enough'." (「核心矛盾已从'能不能训练'转向'推理够不够快/准/省'」) — Yang Wendao, Huawei, Sina Finance ([link](https://finance.sina.com.cn/jjxw/2026-09-21/doc-inisqzxx9238313.shtml))

> "The only way to guarantee data freshness is to store knowledge as a queryable graph." (「データの鮮度が保証される唯一の方法は、知識をクエリ可能なグラフとして保持することだ」) — Ryuto Yoda, CyberAgent ([link](https://developers.cyberagent.co.jp/blog/archives/65814/))

> "Token usage stays flat as your data grows." — Cognee 1.0 newsroom ([link](https://www.cognee.ai/newsroom/cognee-1-0-is-live))

> "Lightweight graph structures can push multi-hop question accuracy from 29% to nearly 66% compared to vector-only approaches." — Neo4j NICD research, TWIN4j ([link](https://neo4j.com/blog/twin4j/this-week-in-neo4j-nodes-agentmemory-graphrag-knowledgelayer-and-more/))
