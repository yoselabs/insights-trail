# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-11-13
**Query type:** GENERAL
**Sources:** WebSearch (EN/JP/CN), WebFetch (Neo4j, Databricks, RAGFlow, InfoQ, Qiita, 53AI, arXiv, GitHub)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 2 stories | ~12 pts, ~6 comments | 🌐 Ask HN Nov 2026; no major new viral story Nov 11-13 |
| Reddit | 0 | — | Not searched this run; ongoing coverage from prior |
| X/Twitter | 0 posts | — | Not retrieved this run |
| YouTube | 0 videos | — | NODES 2026 sessions are Neo4j-hosted, not YouTube-primary |
| Bluesky | 0 posts | — | SOURCE HEALTH: OK; no results retrieved this pass |
| Web (global) | 32 pages | — | 🌐 Neo4j, Databricks, RAGFlow, InfoQ, arXiv, GitHub |
| Web (Japan) | 3 pages | — | 🇯🇵 Qiita (taka_yayoi Nov 12), Zenn (knowledge_graph, dragon1208) |
| Web (China) | 4 pages | — | 🇨🇳 53AI (Nov 10), Juejin, CSDN, Aliyun |

---

## Synthesized Findings

### 1. [new] Neo4j Relate (Nov 11, 2026): Rust-Based Embedded Graph DB for AI Agents, Apache 2.0 🌐

**Claim:** Neo4j launched Relate, an AI-native open-source embedded graph database built in Rust for in-process agent deployment, days before or coinciding with NODES 2026.
**Evidence:**
- **Stack:** Rust; in-memory + optional fsync'd WAL for durable stores; starts in milliseconds; sub-ms reads
- **Query:** 100% openCypher + 97%+ GQL compliant; single Cypher statement can combine vector similarity + graph traversal
- **Agent-specific features:** auto-detects agent harnesses; structured errors with explicit retryable flags; context protection via row caps + in-band truncation markers to prevent context saturation
- **MCP server built-in**; Bolt/HTTP Query API v2; CLI; runs in Jupyter notebooks, browsers, containers, edge devices
- **License:** Apache 2.0; install at relatedb.ai
- **Hackathon:** Nov 11–Dec 11, 2026 ("Context, Connected: agents that understand how your data connects"); prizes Mac Studio/Mac mini; winners Dec 17
- **Coverage:** HPCwire/BigDATAwire, TechIntelpro, varindia, CIO&Leader, German IT press (schlaunews.de, it-management.today) — broad day-1 pickup
- **Sources:** https://neo4j.com/press-releases/announcing-relate-by-neo4j/ · https://www.hpcwire.com/bigdatawire/this-just-in/neo4j-releases-relate-open-source-database-for-ai-agents/ · https://relate.devpost.com/ · https://neo4j.com/blog/news/meet-relate-by-neo4j-an-embedded-database-for-ai-agents/
- **Platforms:** Web (global)

---

### 2. [new] Netflix Operational Knowledge Graph (Nov 13, 2026): RDF/OWL/SHACL in Production at Billion-Request Scale 🌐

**Claim:** InfoQ deep-dive (Nov 13) confirms Netflix runs an ontology-driven KG at scale using W3C semantic web stack + homegrown Rust-based RDF quad store, underpinning a multi-agent root-cause analysis system.
**Evidence:**
- **Scale:** 2 billion daily requests; 38 million real-time logging events/second; 13 signal types (logs, metrics, traces, alerts, deployments, code changes)
- **Observability Ontology:** RDF, OWL, SHACL, SPARQL — defines applications, incidents, deployments, teams, signals as typed entities with relationships
- **QuipuDB:** Netflix's homegrown distributed RDF quad store; built on Rust's redb storage engine; arXiv:2608.16813 (Quipu: A Governed Bitemporal Knowledge Graph Store)
- **Enrichers:** consume operational signals → subject-predicate-object triples; both deterministic and LLM-based; SHACL validation gates
- **Knowledge flywheel:** Observe → Enrich → Infer → Adapt
- **AutoRCA:** multi-agent system; specialist agents (metrics/Atlas, alerts/Radar, experiments/ABlaze, client platforms, deployments) use the shared ontology as a common interface without knowing each other's internal implementations
- **Impact:** typical 4-hour application regression investigation time reduced
- **Why significant:** largest-scale production deployment of W3C semantic web stack for agentic AI found in this window; validates RDF/OWL beyond academia
- **AllegroGraph:** published commentary "Netflix's Ontology-Driven AI Architecture Validates the Need for Context Graph"
- **JP context:** Zenn/knowledge_graph has covered the QCon London 2026 presentation; InfoQ Nov 13 article adds production depth
- **Sources:** https://www.infoq.com/news/2026/11/netflix-ai-driven-observability/ · https://allegrograph.com/netflixs-ontology-driven-ai-architecture-validates-the-need-for-context-graph/ · https://arxiv.org/pdf/2608.16813 · https://www.zenml.io/llmops-database/ontology-driven-observability-for-agentic-root-cause-analysis
- **Platforms:** Web (global), Web (Japan — Zenn ongoing)

---

### 3. [new] Databricks Genie Ontology GA + Always-On Genie Preview (Nov 11, 2026) 🌐🇯🇵

**Claim:** Databricks made Genie Ontology generally available and previewed Always-On Genie; Genie Ontology auto-builds from organizational work artifacts and achieves 91% enterprise task completion (1.6× frontier agents, <0.5× tokens).
**Evidence:**
- **Genie Ontology GA:** Ontology Snippets automatically learned from dashboards, SQL queries, notebooks, Power BI semantic models; Workday org directories for team/reporting relationships
- **Ontology Manager** (Beta): visual curation; OntoRank authority-aware algorithm
- **Unity Catalog Domains/Subdomains and Pages** now GA (organizational governance)
- **Benchmark (Turing):** 91% enterprise task pass rate; 1.6× strongest frontier agent; <50% token usage
- **Always-On Genie** (Preview): operates continuously in background; shadows office workers; handles multi-step tasks without supervision; "autonomous AI for complex enterprise work"
- **Integrations:** ChatGPT, Claude, Microsoft Copilot Cowork, Grok Bot via MCP server or native plugins
- **Governance:** Unity Catalog manages permissions/lineage/definitions; Unity Gateway controls connections/usage limits/guardrails/auditing; audit trails as DB tables
- **JP coverage:** Qiita/taka_yayoi published analysis Nov 12 within 24 hours (https://qiita.com/taka_yayoi/items/49129c0d657364f3bd04)
- **Sources:** https://www.databricks.com/blog/announcing-ga-genie-ontology · https://www.databricks.com/blog/genie-genie-ontology-delivers-16-accuracy-less-half-tokens · https://www.databricks.com/blog/new-genie-autonomous-ai-complex-enterprise-work · https://qiita.com/taka_yayoi/items/49129c0d657364f3bd04
- **Platforms:** Web (global), Web (Japan)

---

### 4. [update] RAGFlow 1.0 GA (Nov 6/9, 2026): Complete Go Rewrite, 91% FRAMES, "Agent Native Database" 🌐

**New fact since prior briefing:** RAGFlow 1.0.0 is now GA — previously tracked as rc3 (Oct 30). Complete Go rewrite ships; 91% FRAMES accuracy; officially positions as "Agent Native Database."
**Evidence:**
- **Go rewrite:** from Python; container image "nearly an order of magnitude" smaller; startup latency down "order of magnitude"; retrieval concurrency up "over two orders of magnitude"
- **Knowledge Compilation templates:** tree navigation, evidence chains, graph exploration, timelines, LLM Wikis
- **Retrieval Harness:** configurable tool sets, step limits, time budgets
- **GraphRAG:** KG dynamically built on entire dataset, auto-updated on new uploads
- **Benchmarks:** 91% FRAMES with BM25+Grep+MiniMax-M3; 30-40% average token savings; 43% hit rate on FRAMES with GLM-4-Flash
- **Nov 11 nightly:** Agentic Chat mode + Jev decision model for evidence sufficiency; chat history stores prompts/token usage/execution time
- **Ontology service (PR #21413):** "on the way" per release notes — not yet merged
- **Sources:** https://ragflow.io/blog/announcing-ragflow-1.0-beyond-rag-toward-an-agent-native-database · https://github.com/infiniflow/ragflow/releases/tag/v1.0.0 · https://ragflow.io/changelog
- **Platforms:** Web (global)

---

### 5. [update] NODES 2026 CONCLUDED (Nov 12, 2026): Andrew Ng Fireside Chat On-Demand; Relate Launched 🌐

**New fact since prior briefing:** Conference concluded. Andrew Ng × Emil Eifrem fireside chat (104 min) now on-demand. Relate database launched day-of.
**Evidence:**
- **Andrew Ng fireside chat:** "Building complex agentic systems requires more than connecting AI models — it takes new approaches to engineering, context, and data"
- **Opening keynote:** "Exploring Context Graphs: From Data to Decisions" (panel: Philip Rathle, Will Lyon, Animesh Koratana, Lasse Andresen, Emil Eifrem)
- **Session highlights:** multi-agent shared memory, Semiont (graph-native AI wiki/annotator), neurosymbolic architecture in production, agentic GraphRAG (autonomous KG construction + adaptive retrieval), agentic personas with persistent evolving memory, AI agent memory landscape overview
- **Relate:** launched Nov 11-12 at/before NODES; hackathon announced
- **Sources:** https://neo4j.com/videos/nodes-2026/ · https://neo4j.com/videos/live-from-nodes-2026-fireside-chat-with-andrew-ng-and-emil-eifrem-amer/ · https://neo4j.com/videos/nodes-ai-2026-opening-keynote-exploring-context-graphs-from-data-to-decisions/ · https://neo4j.com/videos/nodes-ai-2026-build-intelligent-ai-agents-with-context-engineering/
- **Platforms:** Web (global)

---

### 6. [new] AutoOntic (arXiv:2611.15467, Nov 11, 2026): Schema-Free Automatic Ontology Induction Pipeline 🌐

**Claim:** AutoOntic turns a schema-free textual corpus into a typed, hierarchically organized knowledge graph by automatically inducing an ontology — removing the ontology-design bottleneck from KG construction.
**Evidence:**
- **Six stages:** typed triplet extraction → relation canonicalization → entity-type canonicalization → hierarchy induction → entity canonicalization/class assignment → domain/range constraint mining
- **Hierarchy induction:** corpus-derived relation-argument profiles + local LLM-adjudicated parent/child checks; newly added types can trigger reorganization of existing relationships
- **Results:** 90%+ induced endpoint types semantically aligned on Wikidata-TekGen/DBpedia-WebNLG; ~50% exact matches; 88% retrieval accuracy on MINE dataset
- **Significance:** removes the human ontologist bottleneck; pairs with NVIDIA Auto Ontology (Nov 1) and Neo4j Ontology Graph Spec (Nov 5) in the ontology-automation wave
- **Code:** https://github.com/screemix/AutoOntic
- **Sources:** https://arxiv.org/abs/2611.15467
- **Platforms:** Web (global)

---

### 7. [update] Hindsight v1.2.1 (Nov 10, 2026): 50x Large-Bank Speedup, Zero-Downtime Re-embedding 🌐

**New fact since prior briefing (v1.2.0 Nov 3):** v1.2.1 ships 50x performance for large bank operations; zero-downtime embedding model migration.
**Evidence:**
- **Performance:** keyword recall 5-6s → 0.09s (66×); staleness checks 904ms → 18ms (50×); entity search 585ms → 58ms (10×)
- **Zero-downtime re-embedding:** `hindsight-admin reembed` migrates embedding model while servers keep serving
- **Dual embedding:** separate configs for query (lightweight) vs. passage (larger stored text)
- **Pages rename:** "Knowledge Pages" → "Pages" throughout API/SDKs/CLI; old names deprecated until v2.x
- **Reranker fallback:** when decision models fail, automatic reranker ranking
- **Custom LLM provider:** `HINDSIGHT_API_LLM_PROVIDER=mypackage.llm:MyLLM` via import path
- **Sources:** https://hindsight.vectorize.io/blog/2026/11/10/version-1-2-1
- **Platforms:** Web (global)

---

### 8. [update] Letta Code v0.34.52–60 (Nov 11-13, 2026): 9 Releases in 3 Days, Letta Cloud Monitor Integration 🌐

**New fact since prior briefing (v0.34.39):** 21 additional releases in 11 days (v0.34.40–60); Letta Cloud URL source added to Monitor; sandbox ports now private by default.
**Evidence:**
- **v0.34.52–60** (Nov 11-13): Letta Cloud URL source in Monitor; improved worker handoffs; enhanced subagent context preservation + model inheritance; sandbox port now private by default; fixed memory checkout HTTP 403 errors; fixed conversation ancestry preservation
- **Cadence:** 9 releases in 3 days = one every ~8 hours
- **Sources:** https://github.com/letta-ai/letta-code/releases
- **Platforms:** Web (global)

---

### 9. [update] Connected Data London 2026 CONCLUDED (Nov 11-12) 🌐

**New fact since prior briefing:** CDL 2026 concluded. 10th anniversary conference complete; recordings to be published online.
**Evidence:**
- Nov 11: Masterclasses + Technical Workshops (incl. Graphwise ontology engineering session)
- Nov 12: Keynotes + main tracks; William Tunstall-Pedoe keynote; Juan Sequeda (ServiceNow); Jessica Talisman (The Ontology Pipeline — context graphs session)
- CDL Knowledge Graph (open KG, ~300 experts) published as community resource
- 45+ expert presentations on KGs, semantic tech, ontology, graph AI
- **Sources:** https://2026.connected-data.london/ · https://www.connected-data.london/post/cdl-2026-announcement
- **Platforms:** Web (global)

---

### 10. [new] 53AI Ontology Decision Structuring in Production (Nov 10, 2026) 🇨🇳

**Claim:** CN practitioner publishes blueprint for 4-layer ontology model enabling fully autonomous agent task execution via structured decision cycles, validated on 120+ production tasks over 3 months.
**Evidence:**
- **4 layers:** Business Ontology (what) → System Ontology (where) → Delivery Ontology (gates) → Governance Ontology (audit)
- **Cycle:** Observe → Decide → Act → Verify → Next; decision functions mandate required slots before proceeding
- **Aliases system:** business jargon auto-resolves to canonical objects
- **120+ completed tasks** over 3 months in production (Dify, Neo4j, Alibaba Cloud stack)
- **Quote (CN):** 「先 Observe，再 Decide，再 Act，再 Verify，最后 Next」
- **Sources:** https://www.53ai.com/news/knowledgegraph/2026111024381.html
- **Platforms:** Web (China)

---

### 11. [update] AML Cycle 2 Leaderboard: Results Confirmed November 19 🌐

**New fact since prior briefing ("mid-November"):** official release date confirmed as November 19, 2026.
**Evidence:**
- Formal evaluation closed Nov 4; prize pool RMB 150,000; 50+ teams registered
- Tracks: Textual, Coding, Multimodal Memory
- **Sources:** https://agentmemoryleaderboard.ai/

---

**Still true** (no new fact since prior briefing):
- **Memory Tax (arXiv:2610.34073):** 90/99 conditions plain RAG beats dedicated memory; source-augmented retrieval mitigates — `memory-tax-rag-outperforms-memory`
- **Route to Remember (arXiv:2611.05636, NeurIPS PALM):** OPSD hybrid weight+text memory — `route-to-remember-opsd-hybrid-memory`
- **OKF v0.8.0 (Nov 5):** scope isolation + write protection + conflict fork hardening; still latest — `okf-agent-memory-hn-bm25`, `okf-v02-provenance-trust`, `okf-v01-structural-interoperability`
- **NVIDIA Auto Ontology (Nov 1):** Apache 2.0; 2.4K+ stars; 90% build time reduction — `nvidia-auto-ontology-open-source`
- **Anthropic "Components of Agent Memory" (Nov 6):** dreaming 13%→48%; 9 files > 413 — `anthropic-agent-memory-components`
- **Salesforce Agentforce Memory (Nov 3):** 1.8x explicit facts, 2.2x time-varying via policy alone — `salesforce-agentforce-memory-policy`
- **Neo4j Ontology Graph Spec (Nov 5):** YAML/JSON open ontology standard, Apache 2.0 — `neo4j-ontology-graph-spec`
- **PhoenixAI Contextbase (Nov 4):** five-type unified context in StarRocks — `phoenixai-contextbase-unified-context`
- **OpenRecall v0.3.0 (Nov 4):** ZK memory MCP — `openrecall-zk-mcp-memory`
- **Thinker (Nov 5):** dependency-keyed cache; 7-14% wall time cut — `thinker-dependency-keyed-context-cache`
- **MemMachine (NODES 2026 OSS):** provider-independent memory layer (concluded) — `nodes-2026-memmachine-oss`
- **Luminaria Memo (NODES 2026):** human AI sessions → KG; "missing layer" — `luminaria-memo-human-session-kg`
- **MELD (arXiv:2608.16357):** federated memory; no silent overwrite — `meld-distributed-memory-protocol`
- **NornicDB:** 3-tier cognitive decay; Neo4j-compatible — `nornicdb-cognitive-graph-decay`
- **JitKnow 4.8 (CN):** ontology+KG retrieval; entity unification — `jitknow-48-ontology-kg-retrieval`
- **FalkorDB GraphRAG SDK v1.6.0 (Nov 2):** agentic retrieval + 8-tool MCP — `falkordb-graphrag-sdk-v160-agentic`
- **MemSkill (NeurIPS 2026):** learnable memory ops; 70% token reduction — `memskill-neurips-2026-learnable-memory-skills`
- **Letta Code v0.34.37-39 (Nov 2):** JSONL logging + session keepalive (now updated above) — `letta-code-v03437-v03439-nov2`
- **53AI telecom ontology-driven context (Oct 30):** 98.6% recall, 83.5% SQL first-pass — `cn-53ai-ontology-context-engineering-telecom`
- **BM25 60.5% beats all commercial memory at 1/100th cost — `bm25-beats-commercial-memory`
- **past.dev #1 BEAM+DolphinBench truth-tracking — `past-dev-beam-dolphinbench`
- **MAGMA 4-graph architecture (arXiv:2601.03236): 0.700 LoCoMo — `magma-multi-graph-agent-memory`
- **Zep CE discontinued; Graphiti sole OSS; v0.31.2 still latest (Nov 11 non-release update) — `zep-ce-retired-graphiti-open-source`
- **Zep v4 Context API; hyperedges — `zep-v4-context-api-hyperedges`
- **Mem0 graph memory locked to $249/mo Pro; OSS entity linking only — `mem0-graph-memory-oss-removed`
- **Semantica v0.7.0 (14.5K stars) — `semantica-oss-graph-native-context`
- **Letta Pro: MemFS + dreaming cloud tier — `letta-pro-cloud-tier`
- **Neo4j Context Engine private preview; NAMS POLE+O 178/178 TCK — `neo4j-context-engine-launch`, `neo4j-labs-agent-memory-nams`
- **AgentKG v0.14.0: MCP-integrated conversational KG memory — `agentkg-v0130-conversational-memory-kg`
- **AllegroGraph 9.1 + GraphTalker 2.0 — `allegrograph-graphtalker-2-context-management`
- **Grafana Knowledge Graph GA — `grafana-knowledge-graph-ga`
- **Microsoft Fabric IQ + MCP ontology agent — `fabric-iq-ontology-mcp`
- **Graphwise: Oakley Capital; CDL 2026 attended — `graphwise-events-oct-2026`
- **Forrester Q4 2026 Context Layer Landscape — `forrester-context-layer-landscape`
- **Context graph convergence (AlphaSense, Google, Day AI, ZoomInfo, Neo4j, NVIDIA, Grafana, Snowflake) — `context-graph-convergence-enterprise`
- **ISWC 2026 proceedings (96 papers); IBM ISWC; RAGE-KG — `iswc-2026-knowledge-graph-conference`
- **Dell AI Platform KG + Semantic Layer H1 2027 — `dell-ai-platform-kg-semantic-layer`
- **LangChain context rot + 5 techniques — `langchain-context-rot-deep-agents`
- **IJCKG 2026 (Nov 19-21, Bangkok): 6 days away — `llm-guided-ontology-kg-construction-ijckg2026`
- **JP: COA 53% variance elimination; entity resolution at integration time — `jp-devio2026-4-layer-context-stack`
- **CN: ontology+KG strategic return; TBox/ABox split; MemOS 11.7K stars — `cn-ontology-strategic-return`
- **Benchmark proliferation: AML Cycle 2 results Nov 19 — `benchmark-proliferation-memory`
- **Architecture beats model scale: past.dev + Memory Tax — `architecture-beats-model-scale`
- **Oracle AI Agent Memory 26.8: graph-aware retrieval — `oracle-ai-agent-memory-26-8`
- **PuppyGraph Zero-ETL: 6-hop queries ≤3s — `puppygraph-zero-etl-six-hop`
- **Mnemoverse 20pp vendor inflation confirmed — `benchmark-vendor-inflation-measured`
- **dense-mem v2.6.6-rc.26: evidence provenance, conflict detection — `dense-mem-mcp-evidence-provenance`
- **MAGMA, wazootech/worlds-sdk-ts SPARQL self-improving harness — `wazootech-sparql-self-improving-harness`
- **AgentMemory .NET (NODES 2026 — concluded); NICD 66% complex multi-hop — `neo4j-agentmemory-dotnet`

---

## Cross-Source Patterns

### Pattern 1: "Agent-Native" as the New Architecture Category 🌐
**Platforms:** Web (global — Neo4j, RAGFlow, PhoenixAI, InfoQ)
- Three products now explicitly self-label as "agent-native" in one week: RAGFlow 1.0 ("Agent Native Database"), Relate by Neo4j ("AI-native embedded database"), PhoenixAI Contextbase ("context infrastructure for AI agents")
- Each positions itself as a new category: not a database agents use, but a database built *for* agent execution loops (retryable errors, context protection, evidence compilation)
- Quote (RAGFlow): "The Harness orchestrates, RAGFlow supplies" — context supply layer as independent product
- Quote (Relate): "natively auto-detects agent harnesses and returns structured errors equipped with explicit retryable flags"
- Netflix AutoRCA validates the same architecture independently: ontology as common interface across specialist agents without coupling

### Pattern 2: W3C Semantic Web Stack Vindicated in Production 🌐🇯🇵
**Platforms:** Web (global), Web (Japan — Zenn/knowledge_graph)
- Netflix QuipuDB + AutoRCA: RDF/OWL/SHACL/SPARQL at 2B requests/day — largest-scale production deployment
- AllegroGraph explicitly frames this as "validation"; ZenML cites it in LLMOps database
- AutoOntic (arXiv:2611.15467): automatic ontology induction; 90%+ type alignment on Wikidata/DBpedia reference ontologies
- CDL 2026 concluded with Jessica Talisman ("The Ontology Pipeline") keynote on context graphs
- Cross-regional convergence: EN/JP/CN communities all acknowledging semantic web stack revival

### Pattern 3: Enterprise Agentic Ontology Week — Three GA Announcements in 48 Hours 🌐🇯🇵
**Platforms:** Web (global), Web (Japan)
- Nov 11: Databricks Genie Ontology GA (91% enterprise tasks, 1.6× frontier)
- Nov 11: Neo4j Relate open-sourced (embedded graph for agent loops)
- Nov 11-12: NODES 2026 concluded (Andrew Ng fireside chat on context engineering)
- Three independent major announcements in <48 hours; no coordination
- JP Qiita/taka_yayoi: within 24 hours of Genie GA, published Japanese analysis
- CN not yet covered these Nov 11-12 releases in the Nov 11-13 window (1-3 day lag typical)

### Pattern 4: Neurosymbolic AI as CN 2026 Engineering Thesis 🇨🇳
**Platforms:** Web (China — 53AI, Juejin, CSDN)
- CN community framing 2026 as "the year neurosymbolic AI transitioned from academic concept to engineering practice" (yibie/X, widely reshared)
- Core framing: LLM (System 1 fast/probabilistic) + ontology/KG (System 2 slow/verifiable)
- Palantir's "Ontology" methodology credited as trigger; ACL 2026 papers (OntoGuard, EvoMemKG) cited as validation
- 53AI Nov 10 article gives CN practitioners 4-layer ontology deployment blueprint
- Quote (53AI Nov 3): 「知识图谱装事实，本体论定规矩，搞反顺序就白干」 ("KG stores facts, ontology defines rules — reverse the order and it's wasted work")

---

## Per-Platform Tables

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Neo4j Relate press release | https://neo4j.com/press-releases/announcing-relate-by-neo4j/ | AI-native Rust in-memory graph DB; MCP built-in; Nov 11 |
| 🌐 | HPCwire Relate | https://www.hpcwire.com/bigdatawire/this-just-in/neo4j-releases-relate-open-source-database-for-ai-agents/ | Relate: context protection, retryable errors, Apache 2.0 |
| 🌐 | Relate Neo4j blog | https://neo4j.com/blog/news/meet-relate-by-neo4j-an-embedded-database-for-ai-agents/ | Official blog post |
| 🌐 | Relate hackathon | https://relate.devpost.com/ | Nov 11–Dec 11; "Context, Connected" theme |
| 🌐 | RAGFlow 1.0 blog | https://ragflow.io/blog/announcing-ragflow-1.0-beyond-rag-toward-an-agent-native-database | Agent Native Database; Go rewrite; 91% FRAMES |
| 🌐 | RAGFlow v1.0.0 release | https://github.com/infiniflow/ragflow/releases/tag/v1.0.0 | GA release tag |
| 🌐 | RAGFlow changelog | https://ragflow.io/changelog | Nov 11 nightly: Agentic Chat + Jev decision model |
| 🌐 | Databricks Genie Ontology GA | https://www.databricks.com/blog/announcing-ga-genie-ontology | GA Nov 11; OntoRank, Ontology Manager, Workday |
| 🌐 | Databricks Genie benchmark | https://www.databricks.com/blog/genie-genie-ontology-delivers-16-accuracy-less-half-tokens | 91% enterprise, 1.6× frontier, <50% tokens |
| 🌐 | Always-On Genie | https://www.databricks.com/blog/new-genie-autonomous-ai-complex-enterprise-work | Always-On Genie preview; autonomous background operation |
| 🌐 | InfoQ Netflix KG | https://www.infoq.com/news/2026/11/netflix-ai-driven-observability/ | Nov 13; QuipuDB, AutoRCA; 2B reqs/day; 38M events/s |
| 🌐 | AllegroGraph on Netflix | https://allegrograph.com/netflixs-ontology-driven-ai-architecture-validates-the-need-for-context-graph/ | "Validates the need for context graph" |
| 🌐 | ZenML Netflix | https://www.zenml.io/llmops-database/ontology-driven-observability-for-agentic-root-cause-analysis | Agentic root-cause analysis via ontology |
| 🌐 | Netflix news.lavx | https://news.lavx.hu/article/netflix-builds-an-operational-knowledge-graph-for-ai-driven-observability | Netflix operational KG summary |
| 🌐 | AutoOntic arXiv | https://arxiv.org/abs/2611.15467 | Automatic ontology induction; 88% MINE; Nov 11 |
| 🌐 | AutoOntic code | https://github.com/screemix/AutoOntic | Pipeline code |
| 🌐 | Hindsight v1.2.1 | https://hindsight.vectorize.io/blog/2026/11/10/version-1-2-1 | 50x large-bank speedup; zero-downtime reembed |
| 🌐 | Letta Code releases | https://github.com/letta-ai/letta-code/releases | v0.34.52-60; 9 releases Nov 11-13 |
| 🌐 | NODES 2026 videos | https://neo4j.com/videos/nodes-2026/ | Full session library post-conference |
| 🌐 | NODES Ng fireside | https://neo4j.com/videos/live-from-nodes-2026-fireside-chat-with-andrew-ng-and-emil-eifrem-amer/ | 104-min Andrew Ng × Emil Eifrem |
| 🌐 | NODES opening keynote | https://neo4j.com/videos/nodes-ai-2026-opening-keynote-exploring-context-graphs-from-data-to-decisions/ | Context Graphs: From Data to Decisions |
| 🌐 | CDL 2026 | https://2026.connected-data.london/ | Concluded Nov 11-12; recordings coming |
| 🌐 | CDL KG announcement | https://www.connected-data.london/post/cdl-2026-announcement | Community KG released |
| 🌐 | AML leaderboard | https://agentmemoryleaderboard.ai/ | Nov 19 results confirmed |
| 🌐 | IJCKG 2026 | https://ijckg2026.aiat.or.th/ | Nov 19-21 Bangkok; 6 days |
| 🌐 | Databricks press release | https://www.databricks.com/company/newsroom/press-releases/databricks-launches-new-always-genie-autonomous-ai-complex | Always-On Genie press release |
| 🌐 | Solutions Review Nov 13 | https://solutionsreview.com/business-intelligence/analytics-and-data-science-news-for-the-week-of-november-13-updates-from-alteryx-databricks-edelbyte-more/ | Week of Nov 13 roundup |
| 🌐 | OntoGuard ACL 2026 | https://aclanthology.org/2026.findings-acl.1051/ | KG constraint checker; ScienceWorld/VirtualHome |
| 🌐 | EvoMemKG ACL 2026 | https://aclanthology.org/2026.findings-acl.1587/ | Dual-layer memory for multi-hop KG reasoning |
| 🌐 | MemGuard EMNLP 2026 | https://aclanthology.org/2026.emnlp-main.423/ | Verifier signals for memory governance |
| 🌐 | OKF v0.8.0 releases | https://github.com/okf-memory/okf-agent-memory/releases | Still latest (Nov 5) |
| 🌐 | Graphiti releases | https://github.com/getzep/graphiti/releases | v0.31.2 still latest; Nov 11 non-release update |
| 🇯🇵 | Qiita taka_yayoi | https://qiita.com/taka_yayoi/items/49129c0d657364f3bd04 | Databricks Genie Ontology GA analysis, Nov 12 |
| 🇯🇵 | Zenn Netflix QCon | https://zenn.dev/knowledge_graph/articles/netflix-qcon-e2e-knowledge-graph | Netflix E2E KG; ongoing JP coverage |
| 🇯🇵 | Zenn context management | https://zenn.dev/dragon1208/scraps/4739416b249548 | Context graph evolution; MCP memory externalization |
| 🇨🇳 | 53AI Nov 10 | https://www.53ai.com/news/knowledgegraph/2026111024381.html | 4-layer ontology blueprint; 120+ tasks; Nov 10 |
| 🇨🇳 | 53AI Nov 3 | https://www.53ai.com/news/knowledgegraph/2026110369780.html | KG stores facts, ontology defines rules (ongoing) |
| 🇨🇳 | CSDN AI engineer roadmap | https://blog.csdn.net/qq_17859117/article/details/163308287 | Ontology as CN enterprise job baseline requirement |
| 🇨🇳 | Juejin KG × LLM | https://juejin.cn/post/7621125079791714314 | KG+LLM 2026 fusion; OntoGuard/EvoMemKG citations |

---

## Stats Block

```
├─ 🟠 Reddit: 0 (not searched this run; ongoing from prior)
├─ 🔵 X: 0 posts retrieved
├─ 🔴 YouTube: 0 videos
├─ 🟡 HN: 2 stories │ ~12 pts │ ~6 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ SOURCE HEALTH: OK
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 32 pages │ 🇯🇵 3 │ 🇨🇳 4
└─ 🗣️ Top voices: qiita/taka_yayoi (JP) │ 53AI (CN) │ Neo4j, Databricks, RAGFlow (global)
```

---

## Out of Scope but Notable

- **Databricks Always-On Genie** (Nov 11, 2026): The Always-On Genie preview (operates continuously, shadows workers, multi-step tasks without supervision) edges into agent orchestration territory beyond knowledge/ontology — worth watching as it may cannibalize/subsume ontology-focused products. URL: https://www.databricks.com/blog/new-genie-autonomous-ai-complex-enterprise-work

- **QuipuDB (arXiv:2608.16813):** Netflix's homegrown Rust-based bitemporal RDF quad store. A production-grade governed bitemporal KG store paper alongside a live deployment — could become a standalone open-source project. URL: https://arxiv.org/pdf/2608.16813

---

## Data Gaps

- **Bluesky:** 0 results this run (SOURCE HEALTH: OK); timing gap, not outage
- **Reddit:** not retrieved this run (prior run partial HTTP 403); ongoing coverage exists
- **X/Twitter:** not retrieved this run
- **DuckDuckGo HTML endpoint (JP/CN passes):** blocked by CAPTCHA; replaced with WebSearch — equivalent coverage achieved
- **NODES 2026 keynote transcript:** 104-min Andrew Ng fireside not transcribed; only described from metadata
- **CDL 2026 recordings:** not yet published post-event
- **RAGFlow ontology service (PR #21413):** "on the way" per release notes; not yet merged; prior finding not updated
- **AML Cycle 2 results:** official leaderboard November 19 — still pending
- **IJCKG 2026 (Nov 19-21):** papers not yet presented; upcoming
- **CN response to Nov 11-12 releases:** 1-3 day lag; likely Juejin/CSDN coverage will appear Nov 14-16
- **TikTok/Instagram:** not searched; low expected relevance
- **Polymarket:** no active markets on this topic
- **Approximate coverage:** ~82% — strong EN pass with all major releases; selective JP/CN; weak social

---

## Key Quotes

> "Building complex agentic systems requires more than connecting AI models — it takes new approaches to engineering, context, and data." — Dr. Andrew Ng, NODES 2026 fireside chat with Emil Eifrem ([link](https://neo4j.com/videos/live-from-nodes-2026-fireside-chat-with-andrew-ng-and-emil-eifrem-amer/))

> "Relate natively auto-detects agent harnesses and returns structured errors equipped with explicit retryable flags, which enable agents to handle exceptions and self-correct without custom parsing logic." — Neo4j Relate announcement ([link](https://neo4j.com/press-releases/announcing-relate-by-neo4j/))

> "The Harness orchestrates, RAGFlow supplies. Only when the supply layer becomes an independent product can the Agent focus on orchestration and reasoning, and enterprises can govern context as data rather than assembling it into Prompts." — RAGFlow 1.0 announcement ([link](https://ragflow.io/blog/announcing-ragflow-1.0-beyond-rag-toward-an-agent-native-database))

> "Rather than having specialist agents exchange loosely structured findings, they use the ontology as a common interface, allowing agents analyzing traces, logs or deployments to contribute information about the same operational entities without needing to understand each other's internal implementations." — Netflix / InfoQ, Nov 13 ([link](https://www.infoq.com/news/2026/11/netflix-ai-driven-observability/))

> "知识图谱装事实，本体论定规矩，搞反顺序就白干" ("KG stores facts, ontology defines rules — reverse the order and it's wasted work") — 53AI Nov 3 ([link](https://www.53ai.com/news/knowledgegraph/2026110369780.html))

> "Genie Ontology passed 91% of enterprise task runs, 1.6× the rate of the strongest frontier agent, while using less than half the tokens." — Databricks, Nov 11 ([link](https://www.databricks.com/blog/genie-genie-ontology-delivers-16-accuracy-less-half-tokens))

> "Schema-free LLM-based extraction pipelines typically produce flat graphs. AutoOntic addresses this by automatically inducing a typed, hierarchically organized ontology." — arXiv:2611.15467 ([link](https://arxiv.org/abs/2611.15467))

> "2026年は神経記号的AIが学術概念からエンジニアリングの実践へと移行した年" ("2026 is the year neurosymbolic AI transitioned from academic concept to engineering practice") — Qiita/taka_yayoi analysis of Genie Ontology GA, Nov 12 ([link](https://qiita.com/taka_yayoi/items/49129c0d657364f3bd04))
