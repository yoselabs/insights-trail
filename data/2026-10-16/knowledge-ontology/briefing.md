# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-10-16
**Query type:** GENERAL
**Sources:** WebSearch (multi-query), WebFetch (targeted), arXiv, Zep/GitHub, Letta/GitHub, Graphiti/GitHub, Semantica/GitHub, Neo4j, Hackernoon, DuckDuckGo HTML (CAPTCHA), WebSearch-JP, WebSearch-CN, daoyuly.cn, Zenn/Qiita, CSDN/53AI, Mnemoverse

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 0 new submissions | — | 🌐 No new on-topic HN items found this run |
| Bluesky | 0 posts | — | 🦋 Health=OK; @kgconference.bsky.social found; no on-topic posts Oct 14-16 |
| Web (global) | 42 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 4 pages | — | 🇯🇵 Zenn/mbk_digital (Apr), Qiita/keiichik_kk (Aug), plus carried-forward pages |
| Web (China) | 8 pages | — | 🇨🇳 daoyuly.cn Oct 9, TencentDB articles, 53AI, CSDN |
| arXiv | 4 papers | — | 🌐 2610.02945, 2610.15292, 2610.10071, 2610.10507 |
| GitHub | 4 repos | — | 🌐 Graphiti, Letta, Semantica, TencentDB |

---

## Synthesized Findings

### 1. [new] Zep v4: "Context API for Agents" with Hyperedges — Sub-200ms, 90% Fewer Tokens 🌐

**Claim:** Zep shipped v4 Oct 14 as "The Context API for Agents," introducing hyperedges that keep multi-entity facts intact — fixing a structural flaw in all prior KG-based context systems.
**Evidence:**
- **Hyperedges (Oct 15):** Traditional KGs split multi-entity facts into binary pairs at storage; agents retrieve only fragments. Hyperedges preserve the full fact across 3+ entities → complete context, fewer hallucinations on complex relational questions
- **Performance:** Sub-200ms context retrieval; up to 90% fewer tokens vs traditional tool-calling
- **Graph navigation:** agents can traverse connections; stable error codes for action handling
- **Oct 16:** "Everything we shipped in the Zep Context API" recap post published
- **Backward compat:** v3 still supported during migration
- Sources: [getzep.com](https://www.getzep.com/) · [agent-memory](https://www.getzep.com/product/agent-memory/)

---

### 2. [new] Ansatz: Terence Tao's Graph Memory Agent Solves Open Mathematical Problems 🌐

**Claim:** arXiv:2610.02945 (Oct 2, 2026) — 17-author paper incl. Terence Tao — demonstrates continual graph memory enabling an AI agent to independently solve previously open mathematical problems.
**Evidence:**
- **Architecture:** unified graph representation capturing facts, plans, and counterexamples with explicit relationship edges; dependency-aware retrieval extracts targeted context; evidence-sensitive curator manages research frontier; scoped recall prevents uncritical knowledge reuse
- **Results:** Solved ALL 10 First Proof Second Batch problems; independently solved Jamison caterpillar conjecture; solved Erdős Problems 289, 348, 488; partial progress on additional open problems
- **Significance:** First demonstration that graph-based continual memory enables frontier mathematical discovery — not just task completion; validates architecture-over-scale thesis at its extreme limit
- Sources: [arXiv:2610.02945](https://arxiv.org/abs/2610.02945)

---

### 3. [new] Semantica v0.7.0: OSS Graph-Native Context Layer (MIT, 4× Lighter) 🌐

**Claim:** Semantica v0.7.0 (Sep 22, 2026) is the most complete OSS graph-native context layer available — MIT license, 4× lighter core, Community GraphRAG, schema-guided extraction, trust tiers, and MCP retrieval tools in one package.
**Evidence:**
- **Dependencies:** 44→22 packages (4× lighter core install)
- **Hierarchical Community GraphRAG:** multi-level Louvain/Leiden community detection + LLM-summarized community reports + global Map-Reduce + DRIFT hybrid search
- **6 new connectors:** BigQuery, Amazon Redshift, Power BI, Apache Airflow, line-delimited JSON
- **Schema-guided extraction:** SchemaValidator + source-aware truth maintenance with trust tiers
- **MCP semantic retrieval tools:** built-in
- **Persistent SQLite backend:** ExtractionCache survives process restart
- **40+ correctness bugs fixed**
- **Prior releases:** v0.6.8 (Sep 5) added cryptographic signing via Sigstore + deterministic ontology quality gates; v0.6.7 (Aug 28) LangChain + SHACL public API; v0.6.5 (Aug 11) embedded Oxigraph + PROV-O trust
- Sources: [GitHub](https://github.com/semantica-agi/semantica/releases) · [getsemantica.ai](https://getsemantica.ai/)

---

### 4. [new] TencentDB Agent Memory v2.0: Team Memory Hub with PersonaMem 48%→76% 🇨🇳

**Claim:** Tencent's MIT-licensed TencentDB Agent Memory (v2.0, Aug 2026; 27,800+ GitHub stars) is the leading team-focused agent memory system, lifting PersonaMem accuracy 48%→76%.
**Evidence:**
- **4-tier pyramid:** L0 Conversation → L1 Atom → L2 Scenario → L3 Persona
- **4 memory types:** Chat Memory, Skills, Wiki, CodeGraph
- **Team hub:** human-controlled Memory Hub with ACLs and Agent loadouts — governs memory as team asset not private chat dump
- **PersonaMem lift:** 48% → 76% with team memory enabled
- **27,800 stars** (CN GitHub, as of Oct 9 digest); #1 most-starred CN agent memory project in current period
- **Open-sourced:** May 23, 2026; v2.0 Aug 2026
- Sources: [MarkTechPost announcement](https://www.marktechpost.com/2026/05/23/tencent-open-sources-tencentdb-agent-memory-a-4-tier-local-memory-pipeline-for-ai-agents/) · [v2.0 details](https://explainx.ai/blog/tencentdb-agent-memory-v2-team-hub-august-2026)

---

### 5. [new] arXiv:2610.10071 HGP: On-Device Hybrid Graph Memory with Episodic/Semantic/Procedural Types 🌐

**Claim:** HGP (Oct 2026) introduces a three-type hybrid graph memory system for on-device personalized agents, beating the strongest baseline by ~7 points on PAL-Set.
**Evidence:**
- **Three memory types:** episodic (interaction history), semantic (user preferences/facts), procedural (task workflows) — organized as hybrid graph
- **Lightweight self-enhancement classifier:** routes memory type without LLM calls → enables edge/on-device deployment
- **Results:** PAL-Set S-score 35.58 (~+7pp vs strongest baseline)
- **Problem:** LLM agents struggle with heterogeneous long-term user data on-device
- Code publicly available
- Sources: [arXiv:2610.10071](https://arxiv.org/abs/2610.10071)

---

### 6. [new] arXiv:2610.15292 OntoAR-HAR: Ontology-Guided Agentic RAG + Personalized Memory for Activity Recognition 🌐

**Claim:** OntoAR-HAR (Oct 11, 2026) combines a hierarchical activity ontology with agentic RAG and user-specific memory, solving the "semantic inclusion problem" in HAR — achieving SOTA across multiple LLM backbones.
**Evidence:**
- **Hierarchical tree-structured activity ontology:** decomposes classification into local decisions among semantically related activities; avoids comparing unrelated activity candidates
- **Two knowledge sources:** static population-level knowledge (constrained examples via RAG) + personalized user observations (offline-discovered signal features)
- **"Semantic inclusion problem":** long-overlooked issue where related activity labels are treated as independent categories — ontology hierarchy fixes this explicitly
- **Results:** SOTA cross-subject and heterogeneous-sensing performance across multiple LLM backbones
- Sources: [arXiv:2610.15292](https://arxiv.org/abs/2610.15292)

---

### 7. [update] Graphiti v0.31.0 / v0.31.1: October Release Found — MCP SDK 2.x + LLMRuntime 🌐

**Claim:** Graphiti shipped v0.31.0 (Oct 14) and v0.31.1 (Oct 15) — October release found after prior state noted "no October release as of Oct 13." Key: MCP SDK upgrade to 2.x and new LLMRuntime abstraction.
**New facts since Oct 13:**
- **v0.31.0 (Oct 14):** Default OpenAI model → gpt-6-luna (prompt caching off); MCP SDK upgraded to 2.x; LLMRuntime introduced for prompt and model routing; FalkorDB v6.x fulltext fix; security updates (pyjwt, urllib3, etc.); C2 prompt as default combined extraction
- **v0.31.1 (Oct 15):** Minor core library versioning fix
- **Prior:** v0.30.2 was Sep 8; ~31,265 stars; Apache-2.0
- Sources: [Graphiti releases](https://github.com/getzep/graphiti/releases)

---

### 8. [update] Letta v0.34.12–v0.34.15: 4 Releases in 4 Days — Connected Computers + Webhooks 🌐

**Claim:** Letta shipped 4 point releases in 4 days (Oct 12-15), adding Claude Code + Codex execution on connected computers, webhook management, and JSONL streaming for large transcripts.
**New facts since v0.34.5 (Oct 8):**
- **v0.34.12 (Oct 12):** Claude Code + Codex execute on connected computers; live progress visualization; workflow foreground wait + listTools/describeTool
- **v0.34.13 (Oct 13):** Agent webhook management; OpenCode coding worker support; sign-in with agent-issued connect token
- **v0.34.14 (Oct 14):** Subagent permissions for Claude Code/Codex; JSONL transcript streaming (avoids max string length); MCP improvements
- **v0.34.15 (Oct 15):** Workflow workers get mod-registered tools; skip unreadable agent records
- Sources: [Letta releases](https://github.com/letta-ai/letta-code/releases)

---

### 9. [update] SLS Vienna Oct 14-15: Completed — Tacit Query Knowledge, Enterprise AI Enablement 🌐

**Claim:** The Semantic Layer Symposium Vienna (Oct 14-15) has concluded. New fact: confirmed key topics include tacit query knowledge and enterprise AI enablement via SL, with Roche and Adobe as production case studies.
**New facts since Oct 13:**
- **Completed:** 3rd edition Enterprise Knowledge's SLS at Palais Coburg, Vienna
- **Presentation topics:** role of tacit query knowledge in the AI era; semantic layer as enablement layer for AI-enabled enterprises
- **Case studies:** Roche and Adobe enterprise SL implementations
- **Training:** exclusive one-day "Semantic Layer by Design" immersive course
- **Context:** Graphwise was presenting semantic layers on ontologies + FAIR vocabularies at this event
- Sources: [semanticlayersymposium.com](https://semanticlayersymposium.com/) · [eventbrite](https://www.eventbrite.com/e/semantic-layer-symposium-2026-tickets-1981367928812)

---

### 10. [update] Road to NODES Oct 15: Alessandro Negro (GraphAware) — Execution Traces as Graph 🌐

**Claim:** The Road to NODES workshop on Oct 15 was delivered by Alessandro Negro (GraphAware), focused on encoding agent execution traces as reusable graph structures for long-term memory.
**New facts since Oct 13:**
- **Speaker confirmed:** Alessandro Negro, GraphAware
- **Core contribution:** capture full execution traces — tool selections, reasoning steps, retrieved context — as interconnected graph components; agents build domain-specific orchestration patterns via RL + human feedback
- **Live hands-on:** NAMS (Neo4j Agent Memory Service) instance; all 4 memory layers (short-term, long-term POLE+O, reasoning traces)
- **NODES AI 2026 videos:** pre-recorded sessions already posted including "Multi-Agent Shared Graph Memory" and "The AI Agent Memory Landscape"
- Sources: [Road to NODES video](https://neo4j.com/videos/road-to-nodes-ai-graph-based-long-term-memory-how-agentic-workflows-adapt-through-experience/) · [NODES 2026](https://neo4j.com/nodes/)

---

**Still true** (ongoing threads, no new facts this run):
- hindsight-memlake-object-storage: Memlake launched Oct 13, no new Oct 16 update
- narrow-deep-ontology-tower-industrial: arXiv:2610.11768 still current
- textql-ontology-ga: Oct 1 GA; no new Oct update
- jp-devio2026-4-layer-context-stack: Oct 9/11 presentation; no new content
- jp-cybernetics-ontology-unnecessary-counterargument: Sep 26 counter-thesis still standing
- cn-53ai-pole-plus-o-mongodb-agent-memory: Sep 23 architecture; no new CN update
- skan-ai-aow-agentic-ontology-of-work: AOW v1.0/v2.0 still current
- ontocast-hn-agentic-ontology-extraction: Show HN; no new activity found
- letta-pro-cloud-tier: → see §8 above (update)
- hindsight-v0100-multimodal-memory: v0.10.3 current; Memlake enterprise tier live
- ekaw-2026-knowledge-engineering-conference: Proceedings confirmed published; no new chapters found
- fabric-iq-ontology-mcp: V2 still default; Preview; retires Jan 31 2027; no new update
- iswc-2026-knowledge-graph-conference: Oct 25-29 Bari still upcoming (9 days away)
- ibm-iswc-2026-agentic-memory-kg: Still scheduled Oct 25; open-sourced
- inspired-production-ontology-engineering: Oct 7 "vibe ontology" critique; no new update
- active-ontology-atlan-2026: 95% pilots failing; 38% SQL gain; Gartner 50%+ on context graphs by 2028 (new data point from Anadiotis Oct 14 — not new enough to warrant update tag but worth noting)
- jp-zenn-netflix-e2e-kg-autosre: Netflix AutoSRE; no new content
- jp-zenn-bare64-ontology-practice: Protégé vs Fabric IQ; no new content
- cn-ccks-2026: CCKS concluded; WAIE Oct 23 not yet occurred
- cn-53ai-ontology-kg-world-model-path: Three-phase path still canonical
- dell-ai-platform-kg-semantic-layer: H1 2027 roadmap; no update
- okf-agent-memory-hn-bm25: OKF v0.4.4; no v0.5 found
- graphify-codebase-kg-no-vector: v0.9.53; no new release
- ob-caie-ontology-ai-evaluation: Still current
- jp-ontology-for-data-engineers-zenn: SL+ontology complementary
- jp-lightweight-ontology-fixed-queries-bigquery: Fixed SQL not generative; BigQuery Graph
- jp-graph-infra-ai-agents-index-free: Index-free adjacency; 4 RAG types
- evoontology-self-evolving-mcp-server: arXiv:2609.15779; no new update
- turbopuffer-v3-ann-primary-retired: v3 live; ANN-primary removed
- agentmemory-dotnet-pole-plus-o: POLE+O .NET; 178/178 Neo4j TCK
- blitzy-coding-agents-neo4j-graph: $200M; SWE-Bench 84.95%; no new news
- hn-getcassis-entity-graph-complexity: memories/state/handoff must NOT share ontology
- memory-portability-model-upgrade: KG ±0.0020 vs NOTES ±13pp
- moosedev-nesy2026-ontology-coding-memory: 0.98–1.00 recall vs 6–27% vector
- industrial-kg-unification-287-mcp-tools: recall 1.00→0.31 without cross-system tools
- evograph-mem-failure-aware-editable: append-only insufficient for long-horizon tasks
- llm-guided-ontology-kg-construction-ijckg2026: IJCKG 2026 Nov Bangkok
- trikedb-cyberagent-lightweight-ontology-yaml: 88.7% WebQSP at 250-triple budget
- aml-agent-memory-leaderboard: Cycle 2 open; Oct 31 deadline; no results yet
- cognee-1-0-four-verb-api: v1.6.1 Sep 24; no Oct release found
- zep-ce-retired-graphiti-open-source: → see §7 above (update, Graphiti v0.31)
- graphwise-events-oct-2026: → see §9 above (SLS Vienna completed)
- benchmark-proliferation-memory: AML Oct 31 deadline; no new results
- okf-v02-provenance-trust: OKF v0.4.4; no v0.5 found
- okf-v01-structural-interoperability: Structural interoperability; semantic gap still future work
- mem0-v2-token-efficiency: 66.6K stars; no new Oct algorithmic changes
- graphwise-oakley-semantic-layer-pe: Oakley Capital; 30%+ ARR; no new news
- semantics-2026-ghent: Concluded Sep 17; no new Oct news
- databricks-genie-ontology: No new October updates
- databricks-context-engineer-cert: GA Jul 29; no new updates
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1; no new Oct updates
- benchmark-vendor-inflation-measured: Mnemoverse Q3 20pp vendor inflation; confirmed standing
- hindsight-memory-benchmark-leader: 94.6% LME; Memlake enterprise tier; no new Oct benchmark
- parametric-kg-storage-retrieval-gap: LoRA parametric KG stores but retrieval at chance
- selective-forgetting-kg-vs-flat: KG F1=0.417 vs flat 0.468 on LME
- megamem-ultra-large-context-retrieval: 650M+ tokens; 68.22→82.26 EnterpriseRAG-Bench
- graph-personalized-memory-survey-ickg2026: Lifecycle-oriented ICKG 2026 survey
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview
- jp-ontology-to-tool-mechanical-generation: 12-obj/34-action YAML → 58 tools
- mem0-strands-osv3-algorithm: Native AWS Strands; single-pass ADD-only
- msock-intellect-enterprise-spatial-graph: 21-dimensional Enterprise Spatial Graph
- heimdall-trust-verified-kg-coding: Cross-repo KG; CPU-only; 12,800 nodes
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction; 11,860 stars
- jp-ontology-driven-graphrag-construction: Entity unification 72→94%; +23pp
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference irreversibly
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale
- jp-two-layer-memory-write-gate: Hot/cold two-layer + write-gate
- ontologx-autonomous-log-kg: Cybersecurity log→ontology KG
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory; MemOS 11.7K stars (Oct 9 digest confirms active)
- cn-china-agent-government-regulation: First government bounding agent authority (May 2026)
- magg-governed-kg-construction: +47% strict F1 SciERC; no predefined schema
- metaphactory-6-ontopic-virtual-kg: Ontopic acquired; metaphactory 5.9 VKG/OBDA
- memorax-code-coding-plugin: 4 memory types; Claude Code/Codex/WorkBuddy
- jp-zenn-kg-memory-entity-resolution: Entity resolution = primary engineering barrier
- jp-note-semantic-layer-vs-ontology-failure: 60% projects fail without SL
- memos-memory-os-proactive-scheduling: 3-tier Memory OS; Memory Cube; MemOS 11.7K stars confirmed
- openkg-spg-kag-skillnet-dynamic-eval: Claude 4.5 at 37.65% on dynamic eval
- jp-coa-deployment-53pct-variance: COA eliminates 53% answer variance
- aws-context-ontology-accelerator: months→days; OWL 2+HermiT; Apache 2.0
- mnemoverse-hebbian-memory: Hebbian + Rescorla-Wagner; 6 MCP tools
- neo4j-constant-cost-semantic-memory: → see §10 above (Oct 15 workshop completed)
- sap-knowledge-graph-autonomous-enterprise: 452K tables; 50+ Joule Assistants
- neo4j-labs-agent-memory-nams: POLE+O; 178/178 TCK; NAMS hosted service
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG
- apache-ossie-semantic-interchange: Kyvos+Databricks; no Oct updates
- mcp-ontology-integration-protocol: MCP 2026-07-28 final spec; all major tools MCP-native
- ontology-as-reliability-infrastructure: EN/JP/CN independently frame ontology as correctness layer
- hn-5-mistakes-kg-memory: POLE+O practitioner baseline; schema decides everything
- cn-ontology-strategic-return: Strategic return confirmed; ongoing
- tencent-tbox-abox-framing: TBox (LLM) / ABox (human validates)
- vector-db-market-growth: KG market $3.47B in 2026; Anadiotis Oct 14 projects $19.16B by 2035 (30.8% CAGR — different analyst/scope)
- architecture-beats-model-scale: Retrieval architecture dominates model scale; Ansatz (§2) further confirms at extreme limit
- ontology-guardrails-framing: Guardrails framing; 36-46% multi-hop gains; confirmed in Anadiotis Oct 14
- cn-llms-reshape-ontology-engineering: TBox generation by LLM; human validates ABox
- jp-layered-implementation-path: SL (2-6mo) → Lightweight Ontology → MCP
- jp-qiita-ontology-department-alignment: Root cause = missing ontology, not model quality
- benchmark-proliferation-memory-dup: Placeholder; no content; carries forward

---

## Cross-Source Patterns

**1. Hyperedge / Multi-Entity Fact Preservation as the New KG Battleground** 🌐
- Zep v4 (Oct 14): "hyperedges keep full facts intact" across 3+ entities; positions this as key differentiator
- arXiv:2610.15292 OntoAR-HAR (Oct 11): "semantic inclusion problem" — same issue in activity recognition; hierarchical ontology fixes it
- Prior: arXiv:2608.28978 showed KG graph decomposition loses surface-form info (F1=0.417 vs flat 0.468)
- Pattern: industry and research independently converging on fact-splitting as a core failure mode in KG-based memory
- Platforms: Zep product, arXiv

**2. Graph Memory Enabling Long-Horizon Autonomous Tasks — Proof Points Maturing** 🌐
- Ansatz (Oct 2): graph memory → solved open mathematical problems + all FPSB; landmark proof of architecture-beats-scale at the frontier
- HGP (Oct 2026): 3-type graph memory → on-device personalized agents; practical edge deployment
- Road to NODES Oct 15 (Alessandro Negro): execution traces as graph → agents build autonomous decision playbooks via RL
- Prior: MOOSEDev (NeSy 2026) 0.98–1.00 recall; EvoGraph-Mem failure-aware editing; Hindsight Memlake 26× cost reduction
- Platforms: arXiv, Neo4j, HackerNoon

**3. OSS Graph Context Tools Proliferating — Oct 14-16 Three-Day Window Had 4 Releases** 🌐
- Graphiti v0.31.0/v0.31.1 (Oct 14/15): MCP SDK 2.x, LLMRuntime
- Zep v4 + hyperedges (Oct 14/15)
- Letta v0.34.12-v0.34.15 (Oct 12-15): 4 releases in 4 days
- Semantica v0.7.0 (Sep 22): 4× lighter, community GraphRAG
- Pattern: framework layer maturing rapidly; MCP is the universal delivery layer across all tools
- Platforms: GitHub, HackerNoon, Mnemoverse

**4. Enterprise KG Adoption: Market Projection Upgrade** 🌐
- HackerNoon Oct 14 (Anadiotis): KG market $1.34B (2025) → $19.16B (2035) at 30.8% CAGR
- Gartner (cited Anadiotis + Atlan): 50%+ AI agent systems on context graphs by 2028; context engineering in 80% of AI-building tools by 2028
- Prior thread: $3.47B in 2026 (different analyst / scope definition)
- Graph-enhanced RAG: ~80% improvement in truthfulness vs vector systems (cited Anadiotis)
- Platforms: HackerNoon, Atlan

---

## Per-Platform Tables

**Web (global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Zep | [getzep.com](https://www.getzep.com/) | **NEW** Oct 14-16: v4 Context API; hyperedges; sub-200ms |
| 🌐 | Zep | [agent-memory](https://www.getzep.com/product/agent-memory/) | Graph navigation; stable error codes; v4 features |
| 🌐 | Graphiti | [releases](https://github.com/getzep/graphiti/releases) | **UPDATE** Oct 14: v0.31.0 MCP SDK 2.x + LLMRuntime |
| 🌐 | Letta | [releases](https://github.com/letta-ai/letta-code/releases) | **UPDATE** Oct 12-15: v0.34.12-v0.34.15; connected computers, webhooks |
| 🌐 | Semantica | [GitHub](https://github.com/semantica-agi/semantica/releases) | **NEW** Sep 22: v0.7.0; 4× lighter; community GraphRAG; MCP retrieval |
| 🌐 | Semantica | [getsemantica.ai](https://getsemantica.ai/) | Product site; governed context + semantic layer |
| 🌐 | arXiv | [2610.02945](https://arxiv.org/abs/2610.02945) | **NEW** Oct 2: Ansatz; Terence Tao+; solved open math problems with graph memory |
| 🌐 | arXiv | [2610.15292](https://arxiv.org/abs/2610.15292) | **NEW** Oct 11: OntoAR-HAR; hierarchical activity ontology; semantic inclusion problem |
| 🌐 | arXiv | [2610.10071](https://arxiv.org/abs/2610.10071) | **NEW** Oct 2026: HGP; on-device hybrid graph; 3 memory types; +7pp S-score |
| 🌐 | arXiv | [2610.10507](https://arxiv.org/pdf/2610.10507) | Oct 2026: RECAST; adaptive evidence routing for context |
| 🌐 | Neo4j | [Road to NODES Oct 15](https://neo4j.com/videos/road-to-nodes-ai-graph-based-long-term-memory-how-agentic-workflows-adapt-through-experience/) | **UPDATE** Oct 15: Alessandro Negro; execution traces as graph; RL playbook |
| 🌐 | Neo4j | [NODES 2026](https://neo4j.com/nodes/) | Nov 12 event; pre-recorded sessions posted |
| 🌐 | Neo4j | [NODES Multi-Agent Memory](https://neo4j.com/videos/nodes-ai-2026-multi-agent-shared-graph-memory-building-collective-knowledge-for-agents/) | Pre-recorded: collective KG memory for multi-agent systems |
| 🌐 | Neo4j | [NODES Memory Landscape](https://neo4j.com/videos/nodes-ai-2026-the-ai-agent-memory-landscape/) | Pre-recorded: AI agent memory landscape overview |
| 🌐 | SLS Vienna | [semanticlayersymposium.com](https://semanticlayersymposium.com/) | **UPDATE** Oct 14-15 completed; Roche/Adobe; tacit query knowledge |
| 🌐 | HackerNoon | [KG Comeback Oct 14](https://hackernoon.com/why-knowledge-graphs-and-ontologies-are-making-a-comeback-in-the-age-of-ai) | Oct 14; Anadiotis; KG market $19.16B/2035; Gartner 50%+ by 2028 |
| 🌐 | HackerNoon | [Architecture Decision Oct 12](https://hackernoon.com/agent-memory-is-an-architecture-decision-from-mcp-servers-to-stateful-agents) | Oct 12: Cognee V1 dynamic memory graph; MCP to stateful agents |
| 🌐 | HackerNoon | [Lock-in Problem Jul 28](https://hackernoon.com/agent-memory-has-a-lock-in-problem-open-formats-are-how-we-fix-it) | Jul 28: OKF as portable standard; Memanto implementation |
| 🌐 | Atlan | [Gartner Context Graphs](https://atlan.com/know/gartner-context-graphs/) | Context engineering in 80% of AI tools by 2028; 30%+ accuracy lift |
| 🌐 | Atlan | [Context Layer Tools](https://atlan.com/know/ai-agent/agent-context-layer-tools/) | 7-category tool taxonomy for context engineering |
| 🌐 | Mnemoverse | [Q3 comparison](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3) | Letta 52.2%, Mem0 50.0%, Zep/Graphiti 37.0% (Mnemoverse harness) |
| 🌐 | IBM Research | [ISWC 2026 paper](https://research.ibm.com/publications/transparent-traceable-deterministic-agentic-memory-via-knowledge-graphs) | Oct 25 ISWC; imperative+generative KG memory; open-sourced |
| 🌐 | ISWC 2026 | [iswc2026.semanticweb.org](https://iswc2026.semanticweb.org/) | Oct 25-29 Bari; 9 days away |
| 🌐 | ScienceDirect | [LaMAS4PD](https://www.sciencedirect.com/science/article/pii/S2212827126008334) | Jan 2026; multi-agent LLM for ontology-driven Industry 4.0 engineering |
| 🌐 | CSDN/MarkTechPost | [TencentDB](https://www.marktechpost.com/2026/05/23/tencent-open-sources-tencentdb-agent-memory-a-4-tier-local-memory-pipeline-for-ai-agents/) | May 2026: original open-source announcement; 4-tier local memory |
| 🌐 | daoyuly.cn | [Oct 9 digest](https://www.daoyuly.cn/2026/2026-10-09-agent-memory-daily/) | RECAST/HGP; MemOS 11.7K; TencentDB 27.8K; deer-flow 83.5K |
| 🌐 | TencentDB v2 | [explainx.ai](https://explainx.ai/blog/tencentdb-agent-memory-v2-team-hub-august-2026) | Aug 2026: v2.0 details; L0-L3 pyramid; PersonaMem 48%→76% |
| 🌐 | contextandchaos | [Ontologies Context Graphs](https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic) | Three-layer ontological framework for enterprise agents |
| 🌐 | akkonrad.medium | [KG as Memory Layer](https://akkonrad.medium.com/knowledge-graphs-arent-databases-anymore-they-re-the-memory-layer-for-ai-agents-d090c03eb58c) | Four shifts: static→self-evolving; similarity→multi-signal |
| 🌐 | arXiv | [2604.00555](https://arxiv.org/pdf/2604.00555) | Ontology-constrained neural reasoning; three-layer Role/Domain/Interaction framework |
| 🌐 | GraphAcademy | [Agent Memory Workshop](https://graphacademy.neo4j.com/courses/workshop-agent-memory) | Self-paced course; NAMS; POLE+O hands-on |
| 🌐 | Neo4j community | [Road to NODES announcement](https://community.neo4j.com/t/register-road-to-nodes-2026-hands-on-workshops-start-october-1/81216) | Workshop series Oct 1+ |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Zenn/mbk_digital | [SL Dead? Apr 13](https://zenn.dev/mbk_digital/articles/61cb47b23dcb03) | **NEW TO INDEX** Apr 2026; Furuhata; SL+ontology sequential not competing |
| 🇯🇵 | Qiita/keiichik_kk | [Ontology Revival Aug 18](https://qiita.com/keiichik_kk/items/b227e6ac89105e8c5512) | **NEW TO INDEX** Aug 2026; Kuroda; accuracy → ~100% in well-defined semantic domains |
| 🇯🇵 | dev.classmethod.jp | [DevIO 2026 Sapporo](https://dev.classmethod.jp/articles/20261009-devio2026-ontology/) | 4-layer context stack; COA demo (carried from Oct 13) |
| 🇯🇵 | Zenn/cybernetics | [Ontology unnecessary?](https://zenn.dev/cybernetics/articles/a3f4adf33265ce) | Counter-thesis: SL sufficient when metadata complete (carried) |
| 🇯🇵 | Zenn/aws_japan | [COA deployment](https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy) | 53% answer variance eliminated (carried) |
| 🇯🇵 | Speaker Deck | [DevIO slides](https://speakerdeck.com/ishikawa_satoru/developersio-2026-chishiki-no-chizu-o-egaku-toha-nani-ka) | DevIO 2026 slide deck (carried) |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | daoyuly.cn | [Oct 9 digest](https://www.daoyuly.cn/2026/2026-10-09-agent-memory-daily/) | **NEW** Oct 9: RECAST/HGP papers + open source stars roundup |
| 🇨🇳 | explainx.ai | [TencentDB v2](https://explainx.ai/blog/tencentdb-agent-memory-v2-team-hub-august-2026) | **NEW TO INDEX** Aug 2026: v2.0 team hub; L0-L3; PersonaMem |
| 🇨🇳 | MarkTechPost | [TencentDB OSS](https://www.marktechpost.com/2026/05/23/tencent-open-sources-tencentdb-agent-memory-a-4-tier-local-memory-pipeline-for-ai-agents/) | **NEW TO INDEX** May 2026: original open-source announcement |
| 🇨🇳 | 53AI | [POLE+O Sep 23](https://www.53ai.com/news/knowledgegraph/2026092380729.html) | POLE+O + MongoDB; 160+ enterprises (carried) |
| 🇨🇳 | 53AI | [Jul 28 path](https://www.53ai.com/news/knowledgegraph/2026072804689.html) | Ontology → KG → World Model path (carried) |
| 🇨🇳 | Zhihu | [Agent memory survey](https://zhuanlan.zhihu.com/p/1986213905320661415) | 3-layer architecture; vector+KG hybrid (carried) |
| 🇨🇳 | CSDN | [KG conceptual remap](https://blog.csdn.net/hyc010110/article/details/149312134) | From symbolic logic to cognitive AI; ontology as KG skeleton |
| 🇨🇳 | CCKS 2026 | [sigkg.cn/ccks2026](https://sigkg.cn/ccks2026/) | 20th national KG conference (carried) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct access)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not searched directly)
├─ 🟢 HN: 0 submissions (no new on-topic HN items this run)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (health=OK; @kgconference.bsky.social found; no on-topic Oct 14-16 posts)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 42 pages │ 🇯🇵 6 │ 🇨🇳 8
└─ 🗣️ Top voices: Terence Tao (arXiv:2610.02945), Alessandro Negro/GraphAware (Road to NODES Oct 15), George Anadiotis (HackerNoon Oct 14) │ daoyuly.cn (CN digest), Zenn/mbk_digital (JP SL debate)
```

---

## Out of Scope but Notable

- **Ansatz (arXiv:2610.02945) — solved Erdős Problems**: Technically IN scope (graph memory), but the PARADIGM shift is bigger: a 17-person team incl. Terence Tao has produced the first AI system capable of advancing frontier mathematics through autonomous long-horizon graph-memory reasoning. The fact that Erdős Problems fell to continual graph memory suggests the architecture has crossed a threshold beyond "AI aids humans" into "AI discovers with humans." This crosses the boundary into open-models-geopolitics / AI-capabilities debate territory.
- **bytedance/deer-flow (83,500 GitHub stars)**: SuperAgent framework with persistent memory, sandboxes, sub-agent orchestration. Primarily an agent-harnesses topic, but the 83.5K star count makes it the most-starred agent framework in the CN ecosystem — a data point the agent-harnesses topic should track.
- **Gartner: 50%+ of AI agent systems will run on context graphs by 2028**: Cited in the George Anadiotis Hackernoon piece (Oct 14) and Atlan. This Gartner projection is a major enterprise forecast that belongs in the knowledge-ontology topic but also signals a market-structure shift relevant to the broader AI-business topic.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (same as prior run). Fell back to native-language WebSearch for both passes.
- **Reddit:** No direct access (r/KnowledgeGraphs, r/SemanticWeb, r/MachineLearning absent)
- **Bluesky:** Health=OK; minimal on-topic posts found in this period
- **HN:** No new on-topic HN submissions found Oct 13-16
- **ISWC 2026:** Conference Oct 25-29, not yet occurred; IBM paper + GLOW papers confirmed but content not yet delivered
- **WAIE 2026 (Oct 23, Shenzhen):** Not yet occurred; China AI Agent benchmarks bluebook not yet published
- **AML Cycle 2:** Deadline Oct 31; no submission results yet
- **CSDN Oct 9 article:** HTTP 521 on fetch; content not retrieved
- **OceanBase blog:** Returned header only on fetch; content not retrieved
- **SLS Vienna details:** Only high-level summary available; no full session recordings or detailed content yet
- **Coverage estimate:** ~75% — strong on tool releases (Zep v4, Graphiti v0.31, Letta, Semantica, TencentDB), new arXiv papers (Ansatz, OntoAR-HAR, HGP), JP/CN passes via WebSearch; weaker on social engagement, Reddit, upcoming-conference content (ISWC, WAIE)

---

## Key Quotes

> "Hyperedges keep full facts together when a fact has multiple entities... traditional systems split multi-entity facts into pairs, risking incomplete retrieval." — Zep v4 product announcement ([link](https://www.getzep.com/product/agent-memory/))

> "Ontology has never been more hyped or cheaper to fake — yet validation remains expensive, making trust the actual bottleneck in knowledge system deployment." — George Anadiotis, HackerNoon Oct 14, 2026 ([link](https://hackernoon.com/why-knowledge-graphs-and-ontologies-are-making-a-comeback-in-the-age-of-ai))

> "LLMは『賢い』けど『あなたの会社を知らない'" — ("LLMs are intelligent, but they don't know your company") — Keiichi Kuroda, Qiita Aug 18, 2026 ([link](https://qiita.com/keiichik_kk/items/b227e6ac89105e8c5512))

> "The semantic layer and ontology are not competing approaches but sequential stages of organizational data maturity." — Kazuki Furuhata, Zenn/mbk_digital Apr 13, 2026 ([link](https://zenn.dev/mbk_digital/articles/61cb47b23dcb03))

> "Agents build domain-specific orchestration patterns that transfer across contexts — essentially a dynamic playbook refined through reinforcement learning and human feedback." — Alessandro Negro (GraphAware), Road to NODES Oct 15, 2026 ([link](https://neo4j.com/videos/road-to-nodes-ai-graph-based-long-term-memory-how-agentic-workflows-adapt-through-experience/))

> "More than 50% of AI agent systems will run on context graphs by 2028, and context engineering will be embedded in 80% of AI-building tools." — Gartner (cited in Atlan + HackerNoon, October 2026) ([link](https://atlan.com/know/gartner-context-graphs/))

> "Knowledge graph market: $1.34 billion in 2025 → $19.16 billion by 2035 at 30.8% CAGR." — George Anadiotis, HackerNoon Oct 14, 2026 ([link](https://hackernoon.com/why-knowledge-graphs-and-ontologies-are-making-a-comeback-in-the-age-of-ai))
