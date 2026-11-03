# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-11-03
**Query type:** GENERAL
**Sources:** WebSearch (EN/JP/CN multi-query), WebFetch (GitHub, blogs, Zenn, Qiita, Juejin, CSDN, 53AI, Sina), Bluesky, Hacker News

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 4 threads (standing) | Active | 🌐 HN:49581240, 48337689, 48919162, 45329322 — no new threads Nov 1–3 |
| Bluesky | 3 accounts/posts | — | 🦋 @iswc-conf, @larry.bsky.social (RDF 1.2 reifier note), liel single-file graph memory |
| Web (global) | 47 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 11 pages | — | 🇯🇵 Qiita, Zenn, AIDB, AlphaXiv, Uravation |
| Web (China) | 12 pages | — | 🇨🇳 53AI, Juejin, CSDN, OceanBase, Zhihu, Sina, SegmentFault |
| GitHub | 5 repos | — | 🌐 NVIDIA/auto-ontology, vectorize-io/hindsight, ViktorAxelsen/MemSkill, FalkorDB/GraphRAG-SDK, letta-ai/letta-code |
| arXiv | 1 accepted NeurIPS paper | — | 🌐 2602.02474 (MemSkill) |

---

## Synthesized Findings

### 1. [new] NVIDIA Auto Ontology Open-Sourced (Nov 1, 2026) 🌐

**Claim:** NVIDIA released Auto Ontology on Nov 1 under Apache 2.0 — a Python framework building semantic, graph-based reasoning layers over enterprise data; 90% ontology build time reduction claimed; 2.4K stars in 2 days.
**Evidence:**
- **Repo:** https://github.com/NVIDIA/auto-ontology (Apache 2.0; 2.4K stars; "not accepting contributions" — finished internal product)
- **5-step pipeline:** Discover (generate ontologies from metadata catalogs) → Ground (give agents trusted business meanings for metrics/entities) → Validate (check queries against certified definitions+lineage, return provenance) → Expose (MCP / CLI / REST API) → Learn (fold certified corrections back into ontology)
- **Stack:** FastAPI + Python 3.12+, Next.js 16 + React 19, Postgres + pgvector; inference via NVIDIA NIM; deploy via Docker Compose or Kubernetes Helm
- **MCP integration:** Cursor and Claude Desktop can query via Auto Ontology's MCP server
- **Governance critique:** SilverOwl (Nov 2) flagged "still needs a business sign-off" — automated ontology generation lacks domain authority validation
- **Sources:** https://github.com/NVIDIA/auto-ontology · https://emergent.sh/news/nvidia-auto-ontology-open-semantic-layer-ai · https://www.marktechpost.com/2026/11/01/nvidia-auto-ontology-open-source-semantic-layer-ai-agents/ · https://silverowl.si/blog/daily-2026-11-02-nvidia-auto-ontology · https://alphasignal.ai/news/nvidia-s-auto-ontology-stops-ai-agents-from-querying-the-wrong-data · https://grafy.ai/news/nvidia-releases-auto-ontology-to-ground-ai-agent-sql-queries
- **Platforms:** Web (global)

---

### 2. [new] Hindsight v1.2.0: Proprietary Models + 2.5x Cheaper Memory (Nov 3, 2026) 🌐

**Claim:** Hindsight v1.2.0 ships three purpose-built memory models — `hs-rerank-1` (new default multilingual reranker), `hs-decide-1-flash`, `hs-embed-1` — claiming "2.5x cheaper and 2x faster, with better answers"; also adds recall pruning/dedup and provider-agnostic reflect.
**Evidence:**
- **hs-rerank-1:** now default reranker; trained specifically for Hindsight recall; multilingual
- **Recall decision model:** can now prune irrelevant memories and dedup repeats; gains access to memory timestamps for time-sensitive query ranking
- **Reflect reliability:** tool calls now use response schemas (not native tool calling) → same behavior on every provider including self-hosted models
- **Visual evidence:** knowledge pages show images from retained observations
- **Breaking changes:** OpenAI-compatible servers must support response schemas; 3 deprecated config params removed
- **Infrastructure:** Helm support — startup probes, deployment strategies, service account token control
- **Sources:** https://hindsight.vectorize.io/blog/2026/11/03/version-1-2-0 · https://github.com/vectorize-io/hindsight/releases
- **Platforms:** Web (global), GitHub

---

### 3. [new] FalkorDB GraphRAG SDK v1.6.0: Agentic GraphRAG with 8-Tool MCP Server (Nov 2, 2026) 🌐

**Claim:** FalkorDB shipped GraphRAG SDK v1.6.0 on Nov 2 adding agentic retrieval (graph-walk + MultiPath router + skills) and an MCP server with 8 tools — making GraphRAG framework-neutral and tool-callable.
**Evidence:**
- **MCP server:** 8 tools; stdio/SSE transport; skill library: entity comparison, impact analysis, contradiction detection, gap analysis, timeline reconstruction
- **MultiPath path router:** runs only retrieval paths a question needs; PageRank-weighted traversal + beam search
- **Agentic ingestion:** per-document strategy selection during ingestion
- **Framework neutral:** pydantic-ai, LangGraph, CrewAI, MCP all supported
- **Note:** MS GraphRAG v3.1.0 (May 2026) now in maintenance mode (no new features); FalkorDB taking the agentic graphrag lead
- **Sources:** https://github.com/FalkorDB/GraphRAG-SDK/releases/tag/v1.6.0 · https://github.com/FalkorDB/GraphRAG-SDK/issues/389
- **Platforms:** Web (global), GitHub

---

### 4. [new] MemSkill (NeurIPS 2026): Memory Operations as Learnable Skills — 70% Token Reduction 🌐

**Claim:** MemSkill (arXiv:2602.02474, NeurIPS 2026 accepted) frames memory operations themselves as learnable, evolvable skills — reducing tokens/calls ~70% vs LightMem and transferring zero-shot from LoCoMo to HotpotQA.
**Evidence:**
- **Architecture:** Controller (selects relevant skills) → Executor (produces skill-guided memories) → Designer (mines failures, refines+expands skill bank)
- **Skills:** structured reusable routines for extract/consolidate/prune — "meta-memory" (strategies for *how* to remember, not what to remember)
- **Results:** Highest L-J scores on LoCoMo+ALFWorld across LLaMA and Qwen; 70% token+call reduction vs LightMem; HotpotQA 200-doc context: 67.97 L-J (with 7 selected skills); zero-shot transfer LoCoMo → HotpotQA
- **Team:** Haozhen Zhang (NTU) + UIUC, Tsinghua collaborators
- **CN coverage:** Sina Finance Nov 2 https://finance.sina.com.cn/tech/roll/2026-11-02/doc-inixkeur0370303.shtml
- **Sources:** https://arxiv.org/abs/2602.02474 · https://github.com/ViktorAxelsen/MemSkill · https://paperswithcode.co/paper/2602.02474
- **Platforms:** Web (global), CN (Sina)

---

### 5. [new] Letta Code v0.34.37–39: Subagent JSONL Event Logging + Session Keepalive (Nov 2, 2026) 🌐

**Claim:** Letta Code shipped three releases on Nov 2 adding full JSONL event logging for subagent tasks, streaming subagent progress to task output files, and keeping Claude Code sessions alive during background tasks.
**Evidence:**
- **v0.34.38:** Full JSONL event log for every subagent task (including remote workers); streaming subagent progress into task output file
- **v0.34.37:** Keep Claude Code sessions open while background tasks run; improved personality settings handling; enhanced remote worker reliability
- **v0.34.39:** Fixed conversation addressing by ID; improved listener recovery; corrected destination agent selection from enqueue receipts
- **Context:** `read_subagent_events` skill pages durable JSONL log (256 MiB cap); ~1 release/day cadence maintained
- **Sources:** https://github.com/letta-ai/letta-code/releases · https://github.com/letta-ai/letta-code/releases/tag/v0.34.38
- **Platforms:** Web (global), GitHub

---

### 6. [new] 53AI Ontology Context Engineering: 98.6% Object Recall in Telecom (Oct 30, 2026) 🇨🇳

**Claim:** 53AI published a framework for large-scale ontology-driven agent context engineering across 150 real telecom tasks, achieving 98.6% object recall, 4.2s latency, 83.5% SQL first-pass success.
**Evidence:**
- **4-stage method:** Task Understanding → Knowledge Localization (objects + attributes as retrieval entry points) → Relationship Completion (bridge entities not in user request) → Work Set Delivery (with documented dependencies)
- **Quote:** "企业智能体的能力建设，需要把'面向任务组织知识'作为一项独立的系统能力" ("Enterprise agent capability development requires 'task-oriented knowledge organization' as a distinct system function")
- **Frame shift:** ontology transitions from "one-time project deliverable" to "production pipeline continuously outputting agent task capabilities"
- **Results:** 98.6% object recall; 4.2s avg retrieval latency; 83.5% SQL first-pass; validated on 150 telecom data tasks
- **Sources:** https://www.53ai.com/news/knowledgegraph/2026103076501.html
- **Platforms:** CN (53AI)

---

### 7. [update] AML Cycle 2: Submission Closed Oct 31, Eval Closes Nov 4, Results Mid-November 🌐

**Claim:** AML Cycle 2 submission portal closed Oct 31 (on schedule); formal evaluation ends Nov 4 (23:59 Beijing); official leaderboard release expected mid-November 2026.
**Evidence:**
- All three tracks (Textual / Coding / Multimodal Memory) now in evaluation phase
- Open-source Methods + Commercial Products divisions each
- Prior Cycle 1: 136 teams registered, 69 systems completed evaluation (Aug 12, 2026)
- **Sources:** https://agentmemoryleaderboard.ai/ · https://agentmemoryleaderboard.ai/leaderboard/academic/textual · https://www.globenewswire.com/news-release/2026/09/28/3369903/0/en/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory.html
- **Platforms:** Web (global)

---

### 8. [update] NODES 2026: Nov 12 Agenda Live — Andrew Ng + Emil Eifrem Keynotes 🌐

**Claim:** NODES 2026 (Nov 12, free 24h) published agenda with Andrew Ng (DeepLearning.AI) and Emil Eifrem (Neo4j CEO) as keynotes; selected sessions confirm context graphs + multi-agent memory as the conference's dominant theme.
**Evidence:**
- **Keynotes:** Andrew Ng (DeepLearning.AI), Emil Eifrem "Exploring Context Graphs: From Data to Decisions"
- **Selected sessions:** "Meta Knowledge Graph: A Self-Learning Agentic System"; "Multi-Agent Shared Graph Memory: Building Collective Knowledge for Agents"; "Agentic GraphRAG: Autonomous KG Construction and Adaptive Retrieval"; "Building an Explainable GraphRAG System: From Clinical Notes to KGs with Neo4j"
- Road-to-NODES Nov 2 live workshop: full graph-based agent memory stack (hierarchical context graphs + retrieval+answer playbooks)
- **Sources:** https://neo4j.com/nodes/ · https://neo4j.com/nodes/agenda/ · https://www.meetup.com/neo4j-online-meetup/events/314349586/ · https://neo4j.com/videos/road-to-nodes-2026-actionable-knowledge-with-context-graphs-agent-memory/
- **Platforms:** Web (global)

---

### 9. [update] IJCKG 2026 (Nov 19–21, Bangkok): LLM-Guided Ontology KG Paper Confirmed 🌐

**Claim:** IJCKG 2026 (15th edition, Nov 19–21, Bangkok) will present arXiv:2609.31663 on LLM-guided ontology-driven KG construction from unstructured text — the first major KG conference after ISWC 2026's conclusions.
**Evidence:**
- Host: NECTEC Thailand + AI Association of Thailand
- arXiv:2609.31663 (Sep 15): ontology learning pipeline combining compact open-source LLMs, reusable prompting strategies, and open knowledge bases for extracting/structuring knowledge from text — confirmed IJCKG 2026 presentation
- **Sources:** https://ijckg2026.aiat.or.th · https://arxiv.org/abs/2609.31663 · https://easychair.org/cfp/IJCKG-26
- **Platforms:** Web (global)

---

**Still true** (no new fact since Oct 30):
- OKF v0.7.2 (Oct 28) still latest; no Nov releases — `okf-agent-memory-hn-bm25`, `okf-v02-provenance-trust`, `okf-v01-structural-interoperability`
- AllegroGraph 9.1 + GraphTalker 2.0 KMWorld product 2026 standing — `allegrograph-graphtalker-2-context-management`
- Grafana Knowledge Graph GA in all Grafana Cloud stacks — `grafana-knowledge-graph-ga`
- AgentKG v0.14.0 (Oct 26) still latest — `agentkg-v0130-conversational-memory-kg`
- arXiv:2610.32725 ontology-guided KG from climate pubs (133,990 nodes) — `arxiv-2610-32725-ontology-kg-climate`
- ISWC 2026 proceedings (96 papers, Springer LNCS 17126-17128) published and standing — `iswc-2026-knowledge-graph-conference`, `iswc-2026-main-track-papers`, `rage-kg-2026-keynote-abstraction`
- IBM ISWC 2026 agentic memory via KGs open sourced — `ibm-iswc-2026-agentic-memory-kg`
- Forrester Q4 2026 Context Layer Landscape; Q1 2027 Wave scoped — `forrester-context-layer-landscape`
- Neo4j Context Engine private preview (launched Oct 20); Nov 12 NODES likely update — `neo4j-context-engine-launch`, `neo4j-constant-cost-semantic-memory`
- Graphiti v0.31.2 (Oct 20); Zep CE discontinued; no Nov releases — `zep-ce-retired-graphiti-open-source`, `zep-v4-context-api-hyperedges`
- Microsoft Fabric IQ + MCP ontology agent (public preview from FabCon) — `fabric-iq-ontology-mcp`
- Graphwise: Adobe AEM + eval tools; Oakley Capital; ongoing — `graphwise-events-oct-2026`, `graphwise-ontology-powered-data-products`, `graphwise-oakley-semantic-layer-pe`
- QEMem relevance-sufficiency gap (arXiv:2610.22668) — `qemem-relevance-sufficiency-gap`
- DKGI KG-as-files (arXiv:2610.18616) — `dkgi-kg-as-files`
- past.dev #1 BEAM+DolphinBench truth-tracking — `past-dev-beam-dolphinbench`
- BM25 60.5% beats all commercial memory; 1/100th cost — `bm25-beats-commercial-memory`
- Hindsight v1.1.0+Memlake standing as prior milestone — `hindsight-cloud-v10-api-stability`, `hindsight-memlake-object-storage`, `hindsight-v0100-multimodal-memory`, `hindsight-50k-stars`, `hindsight-memory-benchmark-leader`
- Letta Pro MemFS + dreaming standing — `letta-pro-cloud-tier`
- ZoomInfo Workbounce semantic KG — `zoominfo-workbounce-semantic-kg`
- Mem0 graph memory removed from OSS; $249/mo Pro — `mem0-graph-memory-oss-removed`, `mem0-v2-token-efficiency`
- AgentOnto self-updating ontology loop (arXiv:2610.23317) — `agentonto-enterprise-analytics`
- Context graph convergence multi-vendor (AlphaSense, Google, Day AI, ZoomInfo, Neo4j, etc.) — `context-graph-convergence-enterprise`
- Cognee v1.6.5 (Oct 16) semantics-first; no Nov release — `cognee-releases`
- Hindsight 50K stars — `hindsight-50k-stars`
- Subgoal-aware Memory Graph GUI agents (arXiv:2610.31307) — `subgoal-memory-graph-gui-agents`
- ScopeMem latent prefix-vector memory (arXiv:2610.26503) — `scopemem-latent-memory-frozen-gui`
- CN 3-layer agent memory architecture (Juejin, Oct 13) — `cn-3-layer-agent-memory-architecture`
- CN agent memory failure root causes (Juejin, Oct 21) — `cn-agent-memory-failure-root-causes`
- Graphwise ontology-powered data products workshop (Oct 29) — `graphwise-ontology-powered-data-products`
- NVIDIA AKF Auto-Ontology cuts creation time 90% from GTC Berlin (Oct 21) — `nvidia-agent-knowledge-foundation` (note: Auto Ontology is distinct open-source release from the AKF announcement)
- LangChain context rot + 5 techniques — `langchain-context-rot-deep-agents`
- Dell AI Platform KG + Semantic Layer H1 2027 roadmap — `dell-ai-platform-kg-semantic-layer`
- Blitzy $200M coding agents Neo4j KG — `blitzy-coding-agents-neo4j-graph`
- MooseDev NeSy 2026 ontology coding memory — `moosedev-nesy2026-ontology-coding-memory`
- Industrial KG unification 287 MCP tools — `industrial-kg-unification-287-mcp-tools`
- JP standing: COA 53% variance elimination, 4-layer context stack, Netflix E2EGraph, lightweight ontology BigQuery, KG 5/5 vs RAG, SL→ontology→MCP path, YAML→58 tools, entity resolution barrier
- CN standing: 53AI POLE+O+MongoDB 160+ enterprises, TBox/ABox split, strategic return of ontology+KG, China government spec, MemOS 11.7K stars OS paradigm, OpenKG SPG+KAG+SkillNet

---

## Cross-Source Patterns

### Pattern 1: First-Party Semantic Layer Tools Now Shipping
Appearing across: Web (global), CN, GitHub
- NVIDIA Auto Ontology (Nov 1): semantic layer as open-source Apache 2.0 product, not just academic concept
- FalkorDB GraphRAG SDK v1.6.0 (Nov 2): MCP-native agentic retrieval from knowledge graphs
- 53AI CN engineering: 98.6% object recall validates ontology-driven pipelines at production scale
- Quote: "It enables deterministic query generation, better context retrieval, and more explainable AI" — NVIDIA/auto-ontology GitHub description

### Pattern 2: Memory Layer Productization Accelerating — 2.5x Cost/Speed Claims
Appearing across: Web (global), GitHub, CN
- Hindsight v1.2.0: custom models (hs-rerank-1, hs-decide-1-flash, hs-embed-1) targeting 2.5x cheaper, 2x faster
- MemSkill NeurIPS 2026: 70% token+call reduction vs LightMem through learnable skill abstractions
- Both represent moving from generic LLM calls to domain-specialized memory operators

### Pattern 3: Knowledge Graph Conference Cycle Continues — IJCKG Next
Appearing across: Web (global)
- ISWC 2026 concluded Oct 29 (96 papers, Bari)
- NODES 2026 Nov 12 (100+ sessions, Andrew Ng keynote)
- IJCKG 2026 Nov 19–21 (Bangkok) — next major KG venue
- Quote: "knowledge graphs aren't databases anymore — they're the memory layer for AI agents" — Medium, recurring framing across sources https://akkonrad.medium.com/knowledge-graphs-arent-databases-anymore-they-re-the-memory-layer-for-ai-agents-d090c03eb58c

### Pattern 4: JP/CN Practitioner Alignment: KG stores facts, ontology defines rules
Appearing across: JP (Zenn, Qiita), CN (53AI, CSDN, Juejin)
- JP: "エンティティ間の関係性をノードとエッジで表現" — entity resolution solved at integration time, not per-inference
- CN: "知识图谱装事实，本体论定规矩" (KG stores facts, ontology defines rules — confusing order = project failure)
- Both regions independently framing ontology as reliability/correctness infrastructure, not just schema

---

## Per-Platform Tables

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | GitHub/NVIDIA | https://github.com/NVIDIA/auto-ontology | Auto Ontology framework (2.4K stars, Apache 2.0) |
| 🌐 | Emergent.sh | https://emergent.sh/news/nvidia-auto-ontology-open-semantic-layer-ai | Nov 1 launch coverage, MCP/CLI/API |
| 🌐 | SilverOwl | https://silverowl.si/blog/daily-2026-11-02-nvidia-auto-ontology | Governance critique: needs business sign-off |
| 🌐 | Hindsight Blog | https://hindsight.vectorize.io/blog/2026/11/03/version-1-2-0 | v1.2.0 release: models, 2.5x cheaper/2x faster |
| 🌐 | GitHub/Hindsight | https://github.com/vectorize-io/hindsight/releases | v1.2.0, v1.1.0, v1.0.0 release history |
| 🌐 | FalkorDB GitHub | https://github.com/FalkorDB/GraphRAG-SDK/releases/tag/v1.6.0 | GraphRAG SDK v1.6.0: agentic + MCP server |
| 🌐 | Letta GitHub | https://github.com/letta-ai/letta-code/releases | v0.34.37-39: JSONL logging, subagent progress |
| 🌐 | arXiv MemSkill | https://arxiv.org/abs/2602.02474 | NeurIPS 2026: learnable memory skills, 70% token reduction |
| 🌐 | MemSkill GitHub | https://github.com/ViktorAxelsen/MemSkill | Code + benchmarks for MemSkill |
| 🌐 | AML Leaderboard | https://agentmemoryleaderboard.ai/ | Cycle 2 in evaluation; results mid-November |
| 🌐 | GlobeNewswire | https://www.globenewswire.com/news-release/2026/09/28/3369903/0/en/agent-memory-challenge-cycle-2-opens-globally-inviting-more-teams-to-benchmark-the-future-of-ai-memory.html | Cycle 2 launch announcement |
| 🌐 | Neo4j NODES | https://neo4j.com/nodes/ | Nov 12 conference; Andrew Ng + Eifrem keynotes |
| 🌐 | Neo4j Agenda | https://neo4j.com/nodes/agenda/ | 100+ sessions; meta-KG, multi-agent shared graph memory |
| 🌐 | IJCKG 2026 | https://ijckg2026.aiat.or.th | Nov 19–21, Bangkok |
| 🌐 | arXiv:2609.31663 | https://arxiv.org/abs/2609.31663 | LLM-guided ontology-driven KG construction (IJCKG) |
| 🌐 | ISO 23726-1 | https://www.iso.org/standard/90902.html | Ontology-based interoperability standard series |
| 🌐 | ISO 23726-3 | https://www.iso.org/standard/87560.html | Industrial Data Ontology (OWL) — FDIS stage |
| 🌐 | Hackernoon KG | https://hackernoon.com/context-graphs-ontologies-and-the-race-to-fix-enterprise-ai | Context graphs+ontologies race to fix enterprise AI |
| 🌐 | Atlan SL/Ontology | https://atlan.com/know/ontology-vs-semantic-layer/ | SL vs ontology tradeoff analysis |
| 🌐 | ContextAndChaos | https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic | Ontologies+context graphs+SL: what AI needs |
| 🌐 | Mnemoverse Q3 | https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3 | Mem0 vs Zep vs Letta comparison, vendor inflation metrics |
| 🌐 | PaperswithCode | https://paperswithcode.co/paper/2602.02474 | MemSkill benchmark results |
| 🌐 | AlphaSignal | https://alphasignal.ai/news/nvidia-s-auto-ontology-stops-ai-agents-from-querying-the-wrong-data | NVIDIA Auto Ontology coverage |
| 🌐 | Grafy.ai | https://grafy.ai/news/nvidia-releases-auto-ontology-to-ground-ai-agent-sql-queries | NVIDIA Auto Ontology |
| 🇯🇵 | Zenn KG design | https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design | KG as agent memory: entity resolution at integration time |
| 🇯🇵 | Qiita cvusk | https://qiita.com/cvusk/items/78e1f144069f04a5702e | 5 graph patterns; MAGMA dual-stream consolidation |
| 🇯🇵 | AIDB cost study | https://ai-data-base.com/paper/2609-23315 | Graph DB engine cost comparison (ingestion bottleneck) |
| 🇯🇵 | AlphaXiv JP | https://www.alphaxiv.org/ja/abs/2602.05665 | Graph-based agent memory survey in Japanese |
| 🇯🇵 | Qiita yohei1126 | https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80 | Cypher query agents; memory-first architecture |
| 🇯🇵 | Qiita Mem0/Zep | https://qiita.com/agdexai/items/ba7326bd6039b7458010 | Memory tools comparison 2026 |
| 🇯🇵 | Uravation guide | https://uravation.com/media/ai-agent-memory-complete-guide-2026/ | Three-way Mem0/Zep/Letta; Palantir/Fabric/NTT positioning |
| 🇯🇵 | it-acads tips | https://it-acads.com/blog/ai-agent-memory-management-tips | 7 memory management approaches |
| 🇯🇵 | asi.tokyo | https://asi.tokyo/2026/08/26/エージェントループを超える人工知能：グラフエンジニアリングの台頭/ | Graph engineering beyond agent loops |
| 🇨🇳 | Sina Finance | https://finance.sina.com.cn/tech/roll/2026-11-02/doc-inixkeur0370303.shtml | MemSkill NeurIPS 2026 CN coverage |
| 🇨🇳 | 53AI Nov 3 | https://www.53ai.com/news/knowledgegraph/2026110369780.html | KG stores facts, ontology defines rules — PuppyGraph |
| 🇨🇳 | 53AI Oct 30 | https://www.53ai.com/news/knowledgegraph/2026103076501.html | Ontology-driven context engineering; 98.6% object recall |
| 🇨🇳 | OceanBase Blog | https://open.oceanbase.com/blog/25796261152 | Three agent memory paradigms 2026 |
| 🇨🇳 | CSDN Tech Map | https://blog.csdn.net/qq_17859117/article/details/163308287 | AI Agent engineer full tech map; ontology basics |
| 🇨🇳 | Juejin Strategic | https://juejin.cn/post/7656270771611140123 | Strategic return of ontology+KG in 2026 AI |
| 🇨🇳 | Zhihu Survey | https://zhuanlan.zhihu.com/p/2008623544230225425 | 3-paradigm agent memory survey |
| 🇨🇳 | SegmentFault | https://segmentfault.com/a/1190000047750730 | Agent memory system selection guide |
| 🇨🇳 | 163/Netease | https://www.163.com/dy/article/KJO68UG10511DPVD.html | 2026 AI Memory comprehensive survey; 4W classification |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | OKF Agent Memory (BM25 1/100th cost) | 81+ pts | Active | "BM25 60.5% beats Mem0 25-44%, Zep 25-44%" | https://news.ycombinator.com/item?id=49581240 |
| — | 5 mistakes building KG agent memory | Active | Active | "schema decides everything; POLE+O as baseline" | https://news.ycombinator.com/item?id=48337689 |
| getcassis | Reverse-engineer 3 memory tools | Active | Active | "memories, state, handoff must NOT share ontology" | https://news.ycombinator.com/item?id=48919162 |
| — | SQL for AI memory (vs vectors+graphs) | Active | Active | "relational tables for short/long-term memory" | https://news.ycombinator.com/item?id=45329322 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @iswc-conf.bsky.social | ISWC 2026 concluded (Bari, Oct 25-29); advancing KG+AI community | — | https://bsky.app/profile/iswc-conf.bsky.social |
| @larry.bsky.social | "generate meaning first as an ontology, let everything — agents, APIs, KGs — flow from that"; RDF 1.2 reifier for provenance/confidence on individual graph relationships | — | https://bsky.app/profile/larry.bsky.social |
| @daimon-ai.bsky.social | stale agent memory undoes value of remembering; local-first liel single-file graph memory | — | https://bsky.app/profile/daimon-ai.bsky.social |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded)
├─ 🔵 X: 0 posts (excluded)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 4 threads │ 81+ pts │ active comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 3 posts │ ISWC conf, Larry Swanson, Daimon AI
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 24 pages │ 🇯🇵 11 │ 🇨🇳 12
└─ 🗣️ Top voices: @larry.bsky.social, @iswc-conf.bsky.social │ HN:getcassis
```

---

## Out of Scope but Notable

- **RDF 1.2 reifier** (Bluesky @larry.bsky.social): W3C RDF 1.2 introduces the reifier — lets you annotate individual graph relationships with provenance, confidence, and source. Relevant to the standards track but potentially paradigm-level for interoperability: provenance-annotated triples could address the governance gap that SilverOwl flagged in NVIDIA Auto Ontology.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** both JP and CN DDG HTML queries returned CAPTCHA; replaced with native WebSearch in JP/CN — equivalent coverage, different mechanism
- **Reddit/X/Twitter:** excluded per instruction
- **YouTube:** no search performed; no KV reported
- **TikTok/Instagram:** no relevant content expected; not searched
- **Polymarket:** no active markets on this topic
- **Bluesky:** OK per SOURCE HEALTH; 3 relevant accounts found; no high-engagement posts on specific releases this week
- **AgentKG v0.14.0+:** no new releases detected for Nov 1–3
- **Cognee:** v1.6.5 still latest; no Nov release
- **Graphiti/Zep:** v0.31.2 still latest; no Nov release
- **OKF:** v0.7.2 still latest; no Nov release
- **MemOS:** v2.0.35 (Sep 17) still latest; no Oct/Nov release
- **NVIDIA AKF (GTC Berlin, Oct 21):** ongoing; note that Nov 1 Auto Ontology is a separate Apache 2.0 standalone release distinct from the AKF platform
- **Approximate coverage:** ~82% — strong on EN releases and CN/JP hubs; weak on YouTube/TikTok/social

---

## Key Quotes

> "memory 2.5x cheaper and 2x faster, with better answers" — Hindsight v1.2.0 release blog on hs-rerank-1 default model ([link](https://hindsight.vectorize.io/blog/2026/11/03/version-1-2-0))

> "企業智能体の能力建設，需要把'面向任务组织知识'作为一项独立的系统能力" — "Enterprise agent capability development requires 'task-oriented knowledge organization' as a distinct system function" — 53AI, Oct 30 ([link](https://www.53ai.com/news/knowledgegraph/2026103076501.html))

> "知识图谱装事实，本体论定规矩，搞反顺序就白干" — "KG stores facts, ontology defines rules — reverse the order and it's wasted work" — 53AI, Nov 3 ([link](https://www.53ai.com/news/knowledgegraph/2026110369780.html))

> "generate meaning first as an ontology, and let everything else — agents, APIs, knowledge graphs — flow from that" — @larry.bsky.social on Bluesky ([link](https://bsky.app/profile/larry.bsky.social))

> "名寄せは推論のたびに解決する問題ではなく、データを統合するときに一度解決しておく問題です" — "Entity resolution should be solved at data integration time, not per-inference cycle" — Zenn KG agent design article ([link](https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design))

> "NVIDIA's Ontology Still Needs a Business Sign-Off" — SilverOwl critique of Auto Ontology (Nov 2) ([link](https://silverowl.si/blog/daily-2026-11-02-nvidia-auto-ontology))

> "MemSkill reframes memory operations as learnable and evolvable memory skills — structured and reusable routines for extracting, consolidating, and pruning" — MemSkill NeurIPS 2026 paper ([link](https://arxiv.org/abs/2602.02474))

> "memories, state, and handoff must NOT share ontology; distinct concerns require separate schemas" — @getcassis on HN:48919162 ([link](https://news.ycombinator.com/item?id=48919162))
