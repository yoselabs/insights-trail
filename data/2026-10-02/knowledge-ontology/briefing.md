# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-10-02
**Query type:** GENERAL
**Sources:** HackerNews, WebSearch, WebFetch, arXiv, Qiita, Zenn, CSDN, 53AI, Juejin, Zhihu, Tencent Cloud, Neo4j Blog, SiliconAngle, Graphwise, Wasita.net

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 threads | 297 pts / 79 comments (turbopuffer #8 Oct 2); ~2 older threads | 🌐 |
| Web (global) | 38 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 7 pages | — | 🇯🇵 Qiita, Zenn |
| Web (China) | 8 pages | — | 🇨🇳 53AI, Juejin, Zhihu, CSDN, Tencent Cloud |
| arXiv | 1 new paper | — | 🌐 arXiv:2609.15779 |

---

## Synthesized Findings

### 1. [new] EvoOntology: self-evolving ontology as MCP server (+17.8 pts DDR-Bench, −20% tokens) 🌐

**Claim:** EvoOntology (arXiv:2609.15779, Sep 14 2026, Renmin University) gives data agents a self-evolving ontology layer served as an MCP server; builder agent autonomously constructs it, self-evolution loop refines it post-task; outperforms direct raw-data exploration and existing semantic-layer approaches.
**Evidence:**
- **Authors:** Meiduo Chong, Shaolei Zhang, Ju Fan, Xiaoyong Du (RUC); code: [ruc-datalab/EvoOntology](https://github.com/ruc-datalab/EvoOntology)
- **Architecture:** MCP server with 3 layers: (1) schema layer, (2) content layer — 4-node graph: Term/Mapping/Constraint/Evidence nodes, (3) tool layer — `browse` (retrieval by query) + `resolve` (complete semantic neighborhoods)
- **Builder agent:** autonomously constructs ontology from heterogeneous tables/files/databases (agent-data gap problem)
- **Self-evolution loop:** diagnosis → attribution-guided typed edits → backbone-conditional paired evaluation; rejected solutions archived to prevent redundant attempts
- **Active query:** agents query relevant portions of ontology at runtime, not full graph in prompt
- **Results on 3 benchmarks, 4 LLM backbones:**
  - DDR-Bench: avg +17.8 pts; GPT-4o reaches 90.9% (+26.7 pts)
  - BIRD Benchmark: +7.4 pp (exact match), +8.6 pp (valid execution)
  - Task rounds: 14.6 → 8.4; total tokens −20% despite improved accuracy
  - Removing quality gates: −11.2 pp drop (gates are critical)
- **CN coverage:** 53AI framed it "the graph isn't manually drawn — it grows from data" (Sep 26 2026)
- Sources: [arXiv:2609.15779](https://arxiv.org/abs/2609.15779), [GitHub](https://github.com/ruc-datalab/EvoOntology), [53AI](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html), [hyper.ai](https://hyper.ai/en/papers/2609.15779), [learnagentic substack](https://learnagentic.substack.com/p/what-is-evoontology-why-your-agents)

### 2. [new] turbopuffer v3 retires ANN-primary architecture — HN #8 today (297 pts) 🌐

**Claim:** turbopuffer v3 (Sep 30 2026, Dan Harrison) removes ANN indexes as the foundational data structure after identifying 3 structural flaws; decouples document storage from vector indices; on HN top-30 Oct 2 at #8.
**Evidence:**
- **3 structural flaws in ANN-primary:**
  1. Storage amplification: multi-vector documents (ColPali, late-interaction) duplicate all non-vector data per vector
  2. Write amplification: document update triggers full content + every inverted index to rebalance
  3. Structural mismatch with hybrid queries
- **v3 redesign:** decoupled document storage / vector index layout, write path, and query path
- CI status: 100% passes on v3 as of Sep 5 2026; batched reads implemented → ~9× perf improvement
- **HN engagement:** Oct 2 #8 story, 297 pts, 79 comments
- Significance for knowledge ontology: supports hybrid search as first-class, not bolt-on; affects all memory systems using vector-primary retrieval (mem0, Cognee, Hindsight at architectural level)
- Sources: [turbopuffer blog](https://turbopuffer.com/blog/rip-vector-database), [v3 technical](https://turbopuffer.com/v3), [HN Oct 2 digest](https://github.com/meixger/hackernews-daily/issues/1481)

### 3. [update] Fabric IQ Ontology V2 preview: virtual semantic layer, keyless entities, Ontology Copilot — public preview week of Oct 2 🌐

**Claim:** Sep 25 briefing revealed V2 features not yet public-documented; virtual semantic layer answering questions before graph exists; Ontology Copilot for authoring; public preview targeted this week (Oct 2); GA ~November Ignite.
**Evidence:**
- **V2 new features (previewed, not yet in MS Learn):**
  - Virtual semantic layer: federated queries to native source engine when no physical graph exists
  - Keyless entity types: entities without primary keys
  - Cross-source relationships: bind entities to different data sources
  - Inheritance: polymorphic query support within ontologies
  - Power BI TMDL extension: DAX measures remain executable by DAX engine (not transcoded)
  - Built-in Ontology Copilot: assist authoring lifecycle
  - Versioning and restoration
- **Currently GA:** Fabric IQ (general availability); Ontology itself still in Preview
- **Caution from fact-check:** "A fluent answer is not enough. The engine routing must be correct." — evaluate structural accuracy, semantic validation, query performance, security behavior, schema-drift handling before treating as production-ready
- Sources: [Wasita fact-check](https://wasita.net/blog/fabric-iq-ontology-what-is-real/), [MS Learn](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview), [MCP for Fabric IQ Ontology](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology), [Community blog](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/fabric-iq-the-shared-context-layer-for-ai-agents-and-real-time-applications/5191678)

### 4. [new] AgentMemory for .NET: 178/178 POLE+O graph memory for .NET agent frameworks 🌐

**Claim:** José L. Latorre's community project (blog Jul 25 2026; Sep 30 Neo4j livestream) delivers full POLE+O 3-layer graph memory natively for .NET 8/9/10; passes 178/178 Neo4j Test Compatibility Kit scenarios.
**Evidence:**
- **Creator:** José L. Latorre (independent; not official Neo4j product); Demo at Sep 30 Neo4j livestream
- **3-layer memory:** short-term (conversations) / long-term (POLE+O entities+facts+preferences) / reasoning (agent steps+tool calls)
- **Integrations:** Microsoft Agent Framework + Semantic Kernel; direct Neo4j Bolt (self-hosted or Aura)
- **Enterprise features:** OpenTelemetry; bitemporal knowledge; provenance tracking; access auditing; decay mechanisms
- **Test verification:** 178/178 against Neo4j TCK (Bronze/Silver/Gold compatibility levels)
- NAMS (Neo4j Agent Memory Service) backend support in development
- Closes the .NET gap in graph-native agent memory (Python/TypeScript SDKs have been available)
- Sources: [Neo4j blog](https://neo4j.com/blog/developer/agentmemory-for-net-a-native-sibling-to-neo4j-agent-memory/), [livestream](https://neo4j.com/videos/neo4j-live-agentmemory-for-net-persistent-ai-agent-memory-engine/), [GitHub](https://github.com/joslat/agent-memory-dotnet/blob/main/docs/architecture.md)

### 5. [new] Blitzy: $200M autonomous coding platform uses Neo4j KG to ground agents in codebase truth 🌐

**Claim:** Blitzy (Sep 28 2026, $200M raised $1.4B valuation) reverse-engineers enterprise codebases into live Neo4j graphs; SWE-Bench Pro 84.95%; Cypher semantics prevent hallucinated results ("malformed queries return nothing").
**Evidence:**
- **Funding:** $200M at $1.4B valuation (May 2026, Novera Ventures + others)
- **Architecture:** thousands of parallel coding agents + Neo4j graph built from codebase reverse-engineering; integrates with GitHub/GitLab; updates automatically when code changes
- **Problem graph solves:** agents max out at 200K–300K tokens (~20K–30K LOC) with vector search; graph enables precision traversal of 100M-line codebases
- **Grounding mechanism:** Cypher query language — malformed queries return nothing, not hallucinated data
- **SWE-Bench Pro:** 84.95% (June 2026)
- Sources: [SiliconAngle Sep 28](https://siliconangle.com/2026/09/28/knowledge-graphs-give-blitzy-s-coding-agents-codebase-context-neo4jgraphsummit)

### 6. [update] Graphwise AI Summit Oct 7–8 starts in 5 days: Roche RTiS, 90% CIO budgets, confirmed sessions 🌐

**Claim:** AI Summit lineup confirmed — Day 1: Roche introduces RTiS (Roche Terminology and Interoperability System) for Minimal Viable Ontologies; Day 2: AstraZeneca, S&P Global, Avalara; new stat: ~90% of CIOs increasing budgets.
**Evidence:**
- Day 1 confirmed speakers: Enterprise Knowledge, Roche (Martin Romacker: "Harmonizing Centralized and Federated Governance: How to Build FAIR Minimal Viable Ontologies"), Accenture
- Roche RTiS: system for building domain-specific Minimal Viable Ontologies
- Day 2: Avalara, AstraZeneca, S&P Global, Cognizone, BitBang; Graphwise Playground Kickoff
- Stat: "Nearly 90% of CIOs are increasing budgets"; "27% of enterprise apps actually integrated, avg company running ~1,000 disconnected systems"
- Semantic Layer Symposium Vienna: Oct 14–15, Palais Coburg (Graphwise + Roche)
- Sources: [Summit blog](https://graphwise.ai/blog/the-graphwise-ai-summit-2026-one-connected-story-about-what-it-takes-to-get-the-enterprise-ai-right/), [Summit page](https://graphwise.ai/event/graphwise-ai-summit-2026/), [SLS Vienna](https://graphwise.ai/event/semantic-layer-symposium-2026/), [Industrial SIS](https://graphwise.ai/event/industrial-semantic-interoperability-summit-2026/)

### 7. [update] EKAW 2026 concluded Oct 1 — proceedings not yet published 🌐

**Claim:** EKAW 2026 (25th conference, Sep 29–Oct 1, Torino) concluded yesterday; proceedings not yet available on site as of Oct 2.
**Evidence:**
- Conference ran Sep 29–Oct 1 as planned
- Official site sections for "Accepted Contributions" and "Program Overview" exist but remain unpopulated
- Proceedings publisher logos visible but no links yet
- Workshops: X-TAIL (long-tail KG with LLMs), KM4LAW, PwM3
- Sources: [EKAW 2026](https://ekaw2026.di.unito.it/), [WikiCFP](http://www.wikicfp.com/cfp/servlet/event.showcfp?eventid=192424), [Torino listing](https://turismotorino.org/en/visit/events/ekaw-2026-25th-international-conference-on-knowledge-engineering-and-knowledge-management)

### 8. [update] Neo4j Road to NODES: 5 monthly workshops started Oct 1, NODES Nov 12 🌐

**Claim:** Free 2-hour workshops started Oct 1 (Workshop 1: KG + embeddings + vector indexes); 5 workshops through Oct covering GraphRAG, semantic layers, cloud warehouse federation, and agent memory stacks; NODES Nov 12.
**Evidence:**
- Oct 1: KG from unstructured docs + embeddings + vector indexes
- Oct 8: 5 research techniques (GraphRAG + semantic tool selection + EVC swarms + neurosymbolic guardrails + agent steering)
- Oct 15: Lightweight knowledge layer (Trees+Communities+Semantic Layer) over SQL/docs
- Oct 22: Cypher against cloud warehouses (Snowflake/Databricks/BigQuery) via Virtual Graph
- Oct 29: Full graph-based agent memory stack (context graphs + retrieval playbooks + dynamic composition)
- NODES 2026: Nov 12, free 24-hour global virtual event, 100+ speakers
- Sources: [Community post](https://community.neo4j.com/t/register-road-to-nodes-2026-hands-on-workshops-start-october-1/81216), [NODES main](https://neo4j.com/nodes/), [TWIN4j blog](https://neo4j.com/blog/twin4j/this-week-in-neo4j-nodes-agentmemory-graphrag-knowledgelayer-and-more/)

### 9. [update] JP: GraphRAG × Ontology measured improvements — entity unification 72%→94% 🇯🇵

**Claim:** Qiita/@hisaho documents measurable gains from 3-phase GraphRAG + ontology integration in AI-for-Science paper search; +22pp entity unification; +23pp relationship accuracy; 23% additional connections invisible without ontology.
**Evidence:**
- 3-phase approach: (1) CSV synonym dicts (1-2 weeks) → (2) OWL class hierarchies + typed relationships (1-2 months) → (3) inference engines (3-6 months)
- Entity unification: 72% → 94% (+22pp)
- Relationship classification accuracy: 65% → 88% (+23pp)
- Ontology-based reasoning reveals 23% more connections invisible to GraphRAG alone
- Typed relationships (developedBy, usesMethod, extends) vs generic (related_to) dramatically changes reasoning quality
- Transitive inference: "Method A extends B, B extends C → A extends C" (zero-cost derived facts)
- Sources: [Qiita @hisaho](https://qiita.com/hisaho/items/175ca3f80f35abf195f0)

### 10. [new] HN: "We built a structured entity graph for an AI agent. Then we removed most of it" — temporal misalignment warning 🌐

**Claim:** Getcassis (~Aug 26 2026, HN) documents that over-structured knowledge graphs fail in practice; top-voted insight: memories, current state, handoff bills, and source of truth should NOT use the same ontology; agents can wake believing they are in the present when they are actually in the past.
**Evidence:**
- Top comment (v1b3_x0r): "memories, current state, handoff bills and source of truth should not use the same ontology"
- Core problem: "perfect retrieval accuracy doesn't solve the fundamental problem that the agent may still wake up believing it is in the present when it is actually in the past"
- Recommended fix (Matthieu_bl): maintenance loop that tracks code diffs + schema updates + failed queries + user corrections
- Pattern: practitioners reducing graph complexity after initial over-engineering; simpler approaches often outperform
- Sources: [HN:49432253](https://news.ycombinator.com/item?id=49432253)

---

**Still true** (ongoing threads, no new facts this run):
- memory-portability-model-upgrade: KG-fixed ±0.0020 across model swaps (arXiv:2609.05339)
- moosedev-nesy2026-ontology-coding-memory: 0.98–1.00 recall on supersession/negation (arXiv:2608.13662)
- industrial-kg-unification-287-mcp-tools: 287 MCP tools; blocking 24 cross-system → recall 1.00→0.31 (arXiv:2608.24918)
- evograph-mem-failure-aware-editable: append-only insufficient for long-horizon tasks (arXiv:2608.11248)
- llm-guided-ontology-kg-construction-ijckg2026: schema-guided prompting + quantized 7B-32B LLMs (arXiv:2609.31663)
- trikedb-cyberagent-lightweight-ontology-yaml: 88.7% WebQSP at 250-triple budget (CyberAgent)
- aml-agent-memory-leaderboard: Cycle 2 open, Oct 31 deadline; no new results yet
- hindsight-v0100-multimodal-memory: Cloud 0.10.0 (Sep 21); Hermes plugin migration (Sep 23)
- cognee-1-0-four-verb-api: v1.6.0 keyless; BEAM 79%@100K; no Oct release
- zep-ce-retired-graphiti-open-source: v0.30.2; external stores removed from OSS
- letta-pro-cloud-tier: MemFS v0.32.11 (Sep 15); no Oct release
- benchmark-proliferation-memory: 7+ benchmarks; AML Cycle 2 open
- okf-v02-provenance-trust: still at v0.2; no v0.3
- okf-v01-structural-interoperability: structural (not semantic) interoperability; semantic gap acknowledged
- mem0-v2-token-efficiency: 61K+ stars; mem0-strands; OSS v3 algorithm
- graphwise-oakley-semantic-layer-pe: Oakley Capital PE investment (Aug 19)
- databricks-genie-ontology: free through Jan 31 2027; OntoRank; 84.5% first-attempt accuracy
- databricks-context-engineer-cert: GA Jul 29; only context engineering cert; $200/90min
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1; Seed++; Gen 3 RL endogenous memory
- benchmark-vendor-inflation-measured: Mnemoverse Q3 confirms 20pp vendor inflation
- hindsight-memory-benchmark-leader: 94.6% LME; SDE-bench; 57-65% fewer corrections
- parametric-kg-storage-retrieval-gap: LoRA parametric KG stores +0.243 EM but retrieval at chance
- selective-forgetting-kg-vs-flat: KG F1=0.417 underperforms flat baseline 0.468 on LME
- megamem-ultra-large-context-retrieval: 650M+ tokens; EnterpriseRAG-Bench 68.22→82.26
- graph-personalized-memory-survey-ickg2026: lifecycle-oriented survey ICKG 2026
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview
- jp-ontology-to-tool-mechanical-generation: 12-obj/34-action YAML → 58 tools (Zenn/@mk0bayashi)
- mem0-strands-osv3-algorithm: native AWS Strands; single-pass ADD-only; 186M quarterly API calls
- msock-intellect-enterprise-spatial-graph: 21-dimensional Enterprise Spatial Graph
- heimdall-trust-verified-kg-coding: trust-verified cross-repo KG (CPU-only, zero tokens)
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction (DeusData)
- jp-ontology-driven-graphrag-construction: PARTIALLY UPDATED by Finding #9 above
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference irreversibly
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale
- jp-two-layer-memory-write-gate: hot/cold two-layer memory (Zenn/@proper_willet)
- ontologx-autonomous-log-kg: cybersecurity log→ontology KG (Wiley AISY 2026)
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory paradigm; vector+KG hybrid breakthrough
- cn-china-agent-government-regulation: first government bounding AI agent authority (May 2026)
- magg-governed-kg-construction: +47% strict F1 SciERC (arXiv:2608.28642)
- metaphactory-6-ontopic-virtual-kg: Digital Science/Ontopic acquisition; metaphactory 5.9
- memorax-code-coding-plugin: npm @memorax/memorax-code; 4 memory types; 1.2K stars
- jp-zenn-kg-memory-entity-resolution: entity resolution = primary KG engineering barrier
- jp-note-semantic-layer-vs-ontology-failure: 60% projects fail without SL first; Gartner
- memos-memory-os-proactive-scheduling: 3-tier Memory OS; Memory Cube; Memory Marketplace
- openkg-spg-kag-skillnet-dynamic-eval: Claude 4.5 at 37.65% on dynamic eval
- jp-coa-deployment-53pct-variance: COA eliminates 53% answer variance
- jedify-context-graph-benchmark: 75% token savings, 87% SQL accuracy
- memverge-memorybox-memory-sovereignty: cross-platform 记忆主权 closed beta
- graphon-ai-seed-relational-memory: $8.3M seed; graph-native multimodal relational memory
- hn-shared-public-memory-experiment: adversarial degradation; team-level use more viable
- neo4j-create-context-graph-cli: POLE+O CLI scaffolding <5 minutes
- layerx-memory-scaling-failure: dreaming collapses at 4,552 memories; 228% context overflow
- palantir-superrepo-ontology-as-code: TypeScript ontology-as-code + signed Marketplace bundle
- ozbrain-shared-cross-agent-knowledge: shared MCP knowledge store cross-tool
- onton-ontology-1-neurosymbolic-trust: P@10 0.630 vs Google 0.543
- neo4j-meta-knowledge-graph-self-improving: self-improving memory layer; LLM distills learnings
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG
- apache-ossie-semantic-interchange: Kyvos joined; Databricks member; no Oct updates
- semantica-graph-native-provenance: v0.6.0; W3C PROV-O; GDPR/EU AI Act/HIPAA
- starling-universal-cognitive-architecture: UCA open standard; semantic coordinate retrieval
- neo4j-labs-agent-memory-nams: v0.5.0 Python+TS SDKs; POLE+O; NAMS
- ontocast-ontology-assisted-kg: v0.3.0; SHACL; RDF 1.2 provenance; entity disambiguation
- memtools-interoperable-framework: unified research framework; declarative contracts
- graph-native-bitemporal-neo4j: Neo4j bitemporal; 80% R@10 on update questions
- memtool-dynamic-tool-context: 90-94% tool-removal efficiency on ScaleMCP
- hn-openknowledge-ai-notes: 381pts; AI-first Obsidian alternative
- jp-qiita-ontology-department-alignment: missing ontology = not model quality (Qiita/@M_Ozu)
- aws-context-ontology-accelerator: months→days; OWL 2+HermiT; MCP server
- crystalmem-elastic-memory: 50% memory budget matches full baseline
- shared-org-memory-coding-agents: contributor-approved Q&A memory for coding agents
- mcp-memory-okf-sqlite: OKF v0.2 + SQLite FTS5; first OKF implementation
- tencentdb-agent-memory-v2: team-level memory hub; PersonaMem 48%→76%
- coevokg-self-evolving-search: +11.2pp on 6 QA benchmarks
- mragent-reconstructed-memory: Cue-Tag-Content graph; active reconstruction (ICLR 2026)
- magma-multi-graph-memory: 4-graph decoupled architecture; transparent reasoning
- hage-rl-graph-evolution: RL-driven weighted graph evolution
- mage-multi-agent-coevolving-kg: 4-subgraph co-evolutionary KG (UNSW)
- bosun-memory-graph-cleaner: LoRA Qwen3-Reranker for graph curation; WarrantBench open
- hyphaedb-living-topology: gossip-protocol vector topology multi-agent fabric
- cloudflare-agent-memory-beta: 5-channel parallel retrieval; Workers+Durable Objects
- mnemoverse-hebbian-memory: Hebbian + Rescorla-Wagner; 20pp vendor inflation confirmed
- gene-ontology-kb-2026: 768 new terms; Functionome v2.0; AI-assisted curation standard
- neo4j-constant-cost-semantic-memory: semvec constant-cost memory; NICD 29%→66%
- memgraphrag-kdd-2026: 3-layer ontological memory; 59.25% avg; 0.061s retrieval (KDD 2026)
- sap-knowledge-graph-autonomous-enterprise: 452K tables; 50+ Joule Assistants
- experience-graphs-trellis-meta: 10× speedup, 52% lower token cost (Meta, KernelEvolve)
- stardog-bedrock-agentcore-semantic-layer: KG semantic layer + MCP ref arch (AWS)
- ai-km-6-6-1-agentic-ontology-tooling: agentic skill framework + ontology-driven KM (SoftwareX)
- reagan-node-as-agent-graph: each graph node = agent with PAMT (Rutgers)
- mandol-agglomerative-memory: 92.21%/88.40% LoCoMo/LME SOTA (CAS+MSFT)
- toki-bitemporal-contradiction-algebra: 3 write anomalies; every existing system admits ≥1
- agent-native-memory-readiness-survey: 12 systems, 11 datasets; no single architecture dominates
- oracle-ai-agent-memory-26-6: 93.8% LME; 10.7× token reduction
- memory-agent-bench-four-competencies: four-competency framework; all methods fall short (ICLR 2026)
- memora-microsoft-icml-2026: 98% token reduction; 86.3% LoCoMo; 87.4% LME (ICML 2026)
- fabric-iq-ontology-mcp: PARTIALLY UPDATED by Finding #3 above
- mcp-ontology-integration-protocol: MCP 2026-07-28 final spec; all major tools MCP-native
- ontology-as-reliability-infrastructure: EN/JP/CN independently frame ontology as reliability layer
- evomembench-no-single-memory-form: no single form works consistently (15-system study)
- napmem-active-memory-navigation-rl: RL active memory navigation
- placemem-compute-aware-memory-plane: versioned capsules for cross-agent sharing
- agento-owl-rdf-agentic-ontology: OWL/RDF ontology for agentic AI workflows (ESWC 2026)
- always-on-agents-survey: 435-paper governance survey + AOEP-v0
- ontobricks-open-ontologies-mcp: Rust MCP server; OWL2-DL+SHACL+SPARQL (no JVM)
- eticas-ai-risk-taxonomy-v2: SKOS/JSON-LD; 76 subcategories; 18 framework mappings
- hn-5-mistakes-kg-memory: POLE+O practitioner baseline; schema decides everything
- memdelta-benchmark-nonportability: embedding model swaps flip rankings by 6.2pp
- eywa-evidence-before-belief: provenance-grounded memory SOTA on long-horizon benchmarks
- ember-budgeted-evidence-retention: 0.3017 F1; fixed-budget write-side control
- projectmem-memory-as-governance: Memory-as-Governance; 14 MCP tools
- cn-ontology-strategic-return: PARTIALLY UPDATED by EvoOntology CN coverage (53AI Sep 26)
- tencent-tbox-abox-framing: TBox (LLM generates) / ABox (human validates) epistemological framing
- ontology-interoperability-lifecycle-framework: three-phase ontology lifecycle (arXiv:2507.12311)
- trust-certificates-pre-deployment: formal ontology-backed pre-deployment certification
- vector-db-market-growth: $3.47B KG market; $3.2B vector DB market; $28.5B semantic data mesh
- memanto-typed-semantic-memory: 13 typed categories; <90ms; 89.8% LME / 87.1% LoCoMo
- plugmem-icml-2026-microsoft: task-agnostic knowledge-centric memory graph (ICML 2026)
- t-mem-anticipatory-retrieval: 'associative' vs 'descriptive' recall gap; anticipatory retrieval
- architecture-beats-model-scale: retrieval architecture quality dominates model scale
- ontology-guardrails-framing: ontology as AI correctness guardrails; 36-46% multi-hop gains
- cn-llms-reshape-ontology-engineering: TBox generation by LLM; human validates ABox
- jp-layered-implementation-path: SL (2-6mo) → Lightweight Ontology → MCP
- context-files-no-measurable-impact: context files ≤10-15pp correctness improvement
- neo4j-thin-agents-graphsummit: ZS Associates "Why We Killed Our Multi-Agent Pipeline"; 29%→66%
- jp-ontology-vs-dbt-semantic-layer-integration (ongoing)
- semantics-2026-ghent (concluded Sep 17)
- hindsight-16-agents-mcp-surface-enterprise (ongoing)
- cognee-v1-4-0-dataset-overview (merged into cognee ongoing above)
- hindsight-v090-knowledge-pages (merged into hindsight above)
- benchmark-proliferation-memory-dup (placeholder, no content)

---

## Cross-Source Patterns

**1. Ontology moving from static artifact to active runtime component** 🌐
- Pattern: EvoOntology, Fabric IQ V2's virtual semantic layer, turbopuffer v3 hybrid-first, and Blitzy's Cypher grounding all point to ontology/structured knowledge as something agents actively query at runtime, not something pre-loaded into prompts
- Platforms: arXiv (EvoOntology), HN (turbopuffer), Neo4j (Blitzy), Microsoft (Fabric V2)
- Quote: "Agent从「被动看图」变成「主动查图」" ("Agent shifts from passive graph-reading to active graph-querying") — 53AI on EvoOntology ([link](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html))

**2. Ontology complexity curve: over-engineering then pruning** 🌐
- Pattern: getcassis HN, LayerX scaling failure, and EvoOntology's archived-rejected-solutions mechanism all reflect the same lifecycle: build too much → discover temporal/scope mismatch → simplify
- Platforms: HN:49432253, LayerX tech blog, arXiv:2609.15779
- Quote: "memories, current state, handoff bills and source of truth should not use the same ontology" — v1b3_x0r, HN:49432253 ([link](https://news.ycombinator.com/item?id=49432253))

**3. Enterprise events this week confirm semantic layer as strategic** 🌐 🇯🇵
- Pattern: EKAW concluded, Graphwise AI Summit in 5 days, NODES workshops started Oct 1, Fabric IQ V2 preview this week — biggest concentration of enterprise knowledge engineering events since the SEMANTiCS/EKAW cluster in Sep
- Platforms: EKAW 2026, Graphwise, Neo4j, Microsoft
- Quote: "Nearly 90% of CIOs are increasing budgets" — Graphwise AI Summit blog ([link](https://graphwise.ai/blog/the-graphwise-ai-summit-2026-one-connected-story-about-what-it-takes-to-get-the-enterprise-ai-right/))

**4. ANN-primary architecture under pressure** 🌐
- Pattern: turbopuffer v3 abandoning ANN-primary; Cognee/Hindsight/mem0 all moving to hybrid (graph + vector + BM25); MOOSEDev showing 6–27% vs 98–100% advantage for structured vs vector memory on specific query types
- Platforms: turbopuffer (HN), Cognee, Hindsight, arXiv
- Quote: "turbopuffer is redesigning its own storage architecture to stop treating vector search as the foundational organizing structure" — turbopuffer blog ([link](https://turbopuffer.com/blog/rip-vector-database))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| turbopuffer | RIP, vector database | 297 | 79 | "redesigning to stop treating vector search as foundational structure" | [link](https://turbopuffer.com/blog/rip-vector-database) |
| getcassis | We built a structured entity graph for an AI agent. Then we removed most of it | ~est. | ~est. | "memories, current state, handoff bills and source of truth should not use the same ontology" | [link](https://news.ycombinator.com/item?id=49432253) |
| (various) | I reverse-engineered the three biggest agent-memory tools | — | — | — | [link](https://news.ycombinator.com/item?id=48919162) |

**Web (global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv:2609.15779 | [EvoOntology](https://arxiv.org/abs/2609.15779) | Self-evolving ontology MCP server; +17.8 DDR-Bench; −20% tokens |
| 🌐 | turbopuffer blog | [RIP vector DB](https://turbopuffer.com/blog/rip-vector-database) | v3 removes ANN-primary; storage+write amplification fixed |
| 🌐 | turbopuffer v3 | [v3](https://turbopuffer.com/v3) | Technical v3 specification |
| 🌐 | wasita.net | [Fabric IQ V2 fact-check](https://wasita.net/blog/fabric-iq-ontology-what-is-real/) | V2 features previewed; timeline; caution on routing correctness |
| 🌐 | MS Learn | [Fabric IQ Ontology](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview) | Current Ontology (Preview) documentation |
| 🌐 | MS Copilot Studio | [MCP for Fabric IQ](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology) | MCP endpoint for Fabric IQ Ontology |
| 🌐 | Neo4j blog | [AgentMemory .NET](https://neo4j.com/blog/developer/agentmemory-for-net-a-native-sibling-to-neo4j-agent-memory/) | 178/178 TCK; POLE+O; .NET 8/9/10 |
| 🌐 | Neo4j video | [Livestream Sep 30](https://neo4j.com/videos/neo4j-live-agentmemory-for-net-persistent-ai-agent-memory-engine/) | AgentMemory .NET demo by José Latorre |
| 🌐 | SiliconAngle | [Blitzy Sep 28](https://siliconangle.com/2026/09/28/knowledge-graphs-give-blitzy-s-coding-agents-codebase-context-neo4jgraphsummit) | $200M; SWE-Bench 84.95%; Cypher grounding |
| 🌐 | Graphwise blog | [Summit blog](https://graphwise.ai/blog/the-graphwise-ai-summit-2026-one-connected-story-about-what-it-takes-to-get-the-enterprise-ai-right/) | Roche RTiS; 90% CIO budgets up; Day 1-2 content |
| 🌐 | Graphwise | [AI Summit](https://graphwise.ai/event/graphwise-ai-summit-2026/) | Oct 7-8 virtual free |
| 🌐 | Graphwise | [SLS Vienna](https://graphwise.ai/event/semantic-layer-symposium-2026/) | Oct 14-15 Vienna |
| 🌐 | Graphwise | [Industrial SIS](https://graphwise.ai/event/industrial-semantic-interoperability-summit-2026/) | Industrial Semantic Interoperability Summit |
| 🌐 | EKAW 2026 | [site](https://ekaw2026.di.unito.it/) | Concluded Oct 1; proceedings pending |
| 🌐 | Neo4j Community | [Road to NODES](https://community.neo4j.com/t/register-road-to-nodes-2026-hands-on-workshops-start-october-1/81216) | Oct workshops start Oct 1 |
| 🌐 | Neo4j nodes | [NODES 2026](https://neo4j.com/nodes/) | Nov 12, 100+ speakers |
| 🌐 | Neo4j TWIN4j | [Sep 29 blog](https://neo4j.com/blog/twin4j/this-week-in-neo4j-nodes-agentmemory-graphrag-knowledgelayer-and-more/) | NICD 29→66%; AgentMemory .NET; NODES schedule |
| 🌐 | antoinebuteau.com | [Sep 30 digest](https://antoinebuteau.com/daily-digest-2026-09-30) | Monaco Markdown memory; Ars Umbris typed schemas |
| 🌐 | ruc-datalab GitHub | [EvoOntology repo](https://github.com/ruc-datalab/EvoOntology) | Code for arXiv:2609.15779 |
| 🌐 | learnagentic substack | [EvoOntology explainer](https://learnagentic.substack.com/p/what-is-evoontology-why-your-agents) | Why ontology behind a tool not in prompt |
| 🌐 | Ontoforce blog | [Gartner SL](https://www.ontoforce.com/blog/gartners-2026-predictions-confirm-the-semantic-layer-is-no-longer-optional) | Gartner 2026: SL no longer optional |
| 🌐 | MS Community | [Fabric IQ blog](https://community.fabric.microsoft.com/blog/fbc_fabricupdatesblogs/fabric-iq-the-shared-context-layer-for-ai-agents-and-real-time-applications/5191678) | Fabric IQ shared context layer for agents |
| 🌐 | Year of the Graph | [Spring 2026](https://yearofthegraph.xyz/newsletter/2026/03/beyond-context-graphs-how-ontology-semantics-and-knowledge-graphs-define-context-the-year-of-the-graph-newsletter-vol-30-spring-2026/) | Beyond context graphs: how ontology defines context |
| 🌐 | Year of the Graph | [Summer 2026](https://yearofthegraph.xyz/newsletter/2026/06/layers-of-meaning-context-graphs-graph-memory-and-ontologies-for-ai-the-year-of-the-graph-newsletter-vol-31-summer-2026/) | Layers of meaning: context graphs + ontologies for AI |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita/@hisaho | [GraphRAG × Ontology](https://qiita.com/hisaho/items/175ca3f80f35abf195f0) | Entity unification 72→94%; relationship accuracy 65→88%; +23% connections |
| 🇯🇵 | Qiita/@taka_yayoi | [Databricks Genie Ontology](https://qiita.com/taka_yayoi/items/35e4b28280290c131ee3) | OntoRank; snippets vs metric views distinction |
| 🇯🇵 | Qiita/@keiichik_kk | [Ontology as AI agent textbook](https://qiita.com/keiichik_kk/items/b227e6ac89105e8c5512) | "questions within well-organized SL achieve ~100% accuracy" |
| 🇯🇵 | Qiita/@yushibats | [AI-era data infra terms](https://qiita.com/yushibats/items/d4e3e0186f4d8eb83874) | Accessible overview of ontology/KG terminology |
| 🇯🇵 | Zenn/@kimkiyong | [Semantic Layer/KG/Temporal KG](https://zenn.dev/kimkiyong/articles/27c5e2a6f3ac08) | SL vs KG comparison; Universal Semantic Layer convergence |
| 🇯🇵 | Speaker Deck | [生成AI×知識グラフ](https://speakerdeck.com/koujikozaki/sheng-cheng-aitozhi-shi-gurahunoxiang-hu-li-yong-niji-dukuwen-shu-jie-xi) | Document analysis via generative AI + KG |
| 🇯🇵 | GitHub PR | [awesome-copilot-jp](https://github.com/ougotti/awesome-copilot-jp/pull/217) | Comparison of GBrain/Mem0/Graphiti/Letta for JP developers |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | 53AI | [EvoOntology coverage](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html) | Sep 26 2026 — first CN article on EvoOntology; active-query framing |
| 🇨🇳 | 53AI | [Three pillars](https://www.53ai.com/news/knowledgegraph/2026062428391.html) | Taxonomy + Ontology + KG enterprise AI framework |
| 🇨🇳 | 53AI | [LLM Wiki + Ontology](https://www.53ai.com/news/zhishiguanli/2026072634512.html) | From retrievable to actionable knowledge |
| 🇨🇳 | 53AI | [Palantir Ontology warning](https://www.53ai.com/news/Palantir/2026072295761.html) | Don't treat Palantir Ontology as KG-V2 |
| 🇨🇳 | Tencent Cloud | [RAG→GraphRAG](https://developer.cloud.tencent.com/article/2707853?policyId=1004) | RAG ceiling 45% → GraphRAG 89% enterprise accuracy |
| 🇨🇳 | Zhihu | [记忆三大核心范式](https://zhuanlan.zhihu.com/p/2008623544230225425) | Three memory paradigms; 2026 KG breakthrough |
| 🇨🇳 | CSDN | [Ontology suddenly popular](https://blog.csdn.net/qq_40374604/article/details/163716694) | LLMs fluent but can't resolve knowledge logic |
| 🇨🇳 | 声网/Shengwang | [RAG已死/Context Engineering](https://www.shengwang.cn/blog/blogdetail/rag-to-context-engineering/) | KG as "semantic skeleton"; context engineering rise |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct access)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 threads │ 297 pts (turbopuffer, #8 today) │ 79 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no direct content this run)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 38 pages │ 🇯🇵 7 │ 🇨🇳 8
└─ 🗣️ Top voices: José Latorre (Neo4j community), Dan Harrison (turbopuffer), Neeraj Deshmukh (Blitzy), @hisaho (Qiita) │ Neo4j, Graphwise, 53AI, arXiv
```

---

## Out of Scope but Notable

- **Cloudflare Clef: Open-weight decision models + new RL fine-tuning platform** (Oct 2, HN #3, 464pts): Cloudflare releasing open-weight decision models; has implications for in-agent decision-making without proprietary LLM calls; could affect how agents use structured knowledge for routing — [Cloudflare blog](https://blog.cloudflare.com/clef). Caught eye because decision models + ontology guardrails are two solutions to the same problem (constrained agent reasoning).
- **Context Language Models** (Oct 2, HN #26, 129pts, arXiv): context-aware language model paradigm getting traction; unclear scope — may relate to context engineering topic rather than knowledge ontology — [arXiv](https://arxiv.org).

---

## Data Gaps

- **Reddit:** No direct access; r/KnowledgeGraphs, r/MachineLearning content not captured
- **/last30days skill:** Not available in this run; English sweep done manually via WebSearch + WebFetch; social platform coverage (TikTok, Instagram, X/Twitter) absent
- **Bluesky:** No substantive knowledge ontology posts found in direct searches; @semantics-conf.bsky.social (SEMANTiCS) not checked for EKAW cross-posting
- **EKAW 2026 proceedings:** Conference concluded Oct 1; proceedings not yet published; full paper list unavailable
- **AML Cycle 2 results:** Deadline Oct 31; no results published yet
- **SOURCE HEALTH:** No backends reported DOWN for this run; bluesky=OK but minimal data retrieved
- **Estimated coverage:** ~70% — strong coverage of releases (arXiv, tooling, product updates), JP/CN hubs, HN; weaker on social engagement, Reddit, and EKAW proceedings

---

## Key Quotes

> "Agent从「被动看图」变成「主动查图」" ("Agent shifts from passive graph-reading to active graph-querying") — 53AI on EvoOntology ([link](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html))

> "memories, current state, handoff bills and source of truth should not use the same ontology" — v1b3_x0r, HN:49432253 ([link](https://news.ycombinator.com/item?id=49432253))

> "A fluent answer is not enough. The engine routing must be correct." — Andreas Wasita on Fabric IQ Ontology V2 ([link](https://wasita.net/blog/fabric-iq-ontology-what-is-real/))

> "Malformed Cypher queries return nothing — keeps agents grounded in truth of what's in the knowledge graph" — Blitzy / Neeraj Deshmukh, SiliconAngle ([link](https://siliconangle.com/2026/09/28/knowledge-graphs-give-blitzy-s-coding-agents-codebase-context-neo4jgraphsummit))

> "意味の層がきちんと整備された範囲の質問については、正答率がほぼ100%に達した" ("questions within well-organized semantic layers achieve nearly 100% accuracy") — Qiita/@keiichik_kk ([link](https://qiita.com/keiichik_kk/items/b227e6ac89105e8c5512))

> "turbopuffer is redesigning its own storage architecture to stop treating vector search as the foundational organizing structure" — Dan Harrison, turbopuffer ([link](https://turbopuffer.com/blog/rip-vector-database))

> "Nearly 90% of CIOs are increasing budgets; average company running close to 1,000 disconnected systems" — Graphwise AI Summit blog ([link](https://graphwise.ai/blog/the-graphwise-ai-summit-2026-one-connected-story-about-what-it-takes-to-get-the-enterprise-ai-right/))

> "EvoOntology is the first self-evolving ontology layer for data agents, aiming to bridge the agent-data gap over heterogeneous tables, files, and databases" — arXiv:2609.15779 ([link](https://arxiv.org/abs/2609.15779))
