# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-10-09
**Query type:** GENERAL
**Sources:** WebSearch (multi-query), WebFetch (targeted), Zenn, Qiita, Juejin, 53AI, CSDN, arXiv, IBM Research, GitHub, Neo4j, Atlan, Microsoft Learn, Inspired.org

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 thread (prior) | 81 pts, 32 comments (HN:49581240) | 🌐 OKF Agent Memory; no new HN thread Oct 9 |
| Web (global) | 60+ pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 12 pages | — | 🇯🇵 Qiita, Zenn, CyberAgent; 2 new articles |
| Web (China) | 8 pages | — | 🇨🇳 53AI, Juejin, CSDN, CCKS 2026 |
| arXiv | 5 papers | — | 🌐 ISWC 2026 batch + IBM Research |
| GitHub | 3 repos | — | 🌐 Letta, Graphiti, MemPalace |

---

## Synthesized Findings

### 1. [update] Fabric IQ Ontology V2 Now the Default — Old Experience Retires Jan 31, 2027 🌐

**Claim:** Microsoft switched the NEW Fabric IQ Ontology experience (V2) to the DEFAULT for all new ontology items as of early October 2026; creation of old-experience items via the UI is no longer possible; retirement Jan 31, 2027.
**Evidence:**
- **V2 is default now:** MS Learn docs (updated 2026-10-06): "The new ontology experience is the default experience for new ontology items. You can't create new instances of the old ontology experience through the ontology interface in Fabric"
- **Migration banner:** in-product prompt to "create a copy in the new experience" shown to existing old-experience users
- **V2 feature set live (preview):** keyless entity types (no primary key required), inheritance, namespaces, shared properties, version history, optional graph execution (materialization NOT automatic — opt-in), RDF/Turtle/OWL import-export, DAX measures from Power BI preserved as "metrics"
- **Virtual semantic layer:** ontology defines entities/relationships/rules without copying data; queries execute against live bound sources (semantic models, lakehouses, eventhouses, warehouses, SQL DBs, mirrored DBs)
- **Ontology Agent (AI-assisted, preview):** generates definitions from connected Fabric sources; proposes changes for review; proposal-first model
- **MCP integration:** agents connect to Fabric IQ Ontology via MCP in Copilot Studio / Azure Foundry
- **GA target:** still Preview; expected GA ~November Ignite
- **Old experience retires:** Jan 31, 2027
- Sources: [MS Learn overview (updated Oct 6)](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview) · [IQ GA vs Ontology Preview post](https://community.fabric.microsoft.com/blog/fiq_comm_blog/fabric-iq-is-ga-your-ontology-isnt-heres-what-that-actually-means-/5364087) · [Wasita fact-check](https://wasita.net/blog/fabric-iq-ontology-what-is-real/) · [Azure Foundry Fabric IQ tool](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/fabric-iq) · [Copilot Studio MCP Fabric IQ](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology) · [Emergent Software explainer](https://www.emergentsoftware.net/resources/insights/fabric-iq-explained-connecting-data-semantics-and-ai-across-the-enterprise/) · [Acuvate guide](https://acuvate.com/blog/microsoft-fabric-iq-ontology-enterprise-ai/)

---

### 2. [update] Letta v0.34.x: Memory Palace Skill + Read-Only MemFS + MCP Inheritance (Sep 30 – Oct 4) 🌐

**Claim:** Letta released v0.34.0–0.34.4 (Sep 30–Oct 4, 2026); key additions: Memory Palace (structured palace/ folder, Cloud-only), read-only file policy for MemFS, MCP server inheritance for subagents.
**Evidence:**
- **v0.34.0 (Sep 30):** Memory Palace skill made source of truth for palace rules + Cloud-only; async user questions; persists conversation client preferences
- **v0.34.1 (Sep 30):** Windows large-memory repo commit fixes; Claude Sonnet 5.5 support
- **v0.34.2 (Oct 2):** Stream completion, tokens, phase progress in workflows; memory commit fixes
- **v0.34.3 (Oct 4):** Read-only file policy for MemFS; nested subagent messaging; **MCP server inheritance for subagents** (auto-passes parent's MCP servers to child agents)
- **v0.34.4 (Oct 4):** Reverts auto-reply relay from core channels; memory subagents write own scratchpad
- **Memory Palace pattern:** palace/ folder rendered as MEMORY.md-first structured palace in Desktop; enables LETTA_MEMORY_PALACE=1 experiment; Cloud-only bundled skill teaches agents palace maintenance
- Sources: [v0.34.0](https://github.com/letta-ai/letta-code/releases/tag/v0.34.0) · [v0.34.2](https://github.com/letta-ai/letta-code/releases/tag/v0.34.2) · [v0.34.4](https://github.com/letta-ai/letta-code/releases/tag/v0.34.4) · [Memory Palace PR #4754](https://github.com/letta-ai/letta-code/pull/4754) · [Memory Palace Cloud-only PR #4866](https://github.com/letta-ai/letta-code/pull/4866)

---

### 3. [new] ISWC 2026 (Oct 25-29, Bari): IBM Research Open-Sources KG Agentic Memory; GLOW Workshop 14 Papers 🌐

**Claim:** International Semantic Web Conference 2026 (Oct 25-29, Bari) opens with IBM Research's first open-sourced production-grade agentic memory KG system; GLOW workshop (Graph-enhanced LLMs) has 14 accepted papers.
**Evidence:**
- **IBM Research paper (Oct 25):** "Transparent, Traceable, Deterministic: Agentic Memory via Knowledge Graphs" (Anna Lisa Gentile, Sungeun An, Chad Deluca)
  - Problem: managing personal data acquired through agent conversations
  - Approach: structured KG representations for conversational memory; combines imperative + generative computing
  - Claims: transparent operation, traceable answers, more deterministic responses grounded in explicitly stored info
  - Status: fully implemented, piloted in internal enterprise settings, **released as open source**
- **IBM ESWC 2026 (related):** "Personal Agents and Conversational Memory" — KG captures agentic conversational memory; trustworthy + traceable responses
- **Semmtech paper:** "Ontology-Based Enterprise Knowledge Management" (Utku Sivacilar, Wouter Lubbers, with Arcadis engineering firm)
- **GLOW@ISWC'26:** 14 papers on Graph-enhanced LLMs for trustworthy Web data management (47% acceptance rate)
- **arXiv:2507.12311v9:** "An Ecosystem for Ontology Interoperability" — presented at ISWC 2026
- Sources: [IBM ISWC 2026](https://research.ibm.com/publications/transparent-traceable-deterministic-agentic-memory-via-knowledge-graphs) · [IBM ESWC 2026](https://research.ibm.com/publications/personal-agents-and-conversational-memory) · [ISWC 2026 site](https://iswc2026.semanticweb.org/) · [Semmtech ISWC](https://semmtech.com/event/semmtech-x-iswc-26/) · [GLOW workshop](https://glow-workshop.github.io/iswc2026/) · [arXiv:2507.12311](https://arxiv.org/html/2507.12311v9)

---

### 4. [new] Inspired.org Oct 7: "Vibe Ontology" Critique — 8 Engineering Capabilities for Production-Grade Ontologies 🌐

**Claim:** Graham McLeod (Oct 7, 2026) defines a production ontology engineering discipline, coining "vibe ontology" (LLM-generated, plausible but unverified) as the failure mode to avoid; eight distinct engineering capabilities required.
**Evidence:**
- **Core problem:** "An agent that books, approves, reorders or escalates acts on what it believes, at machine speed, and nobody reads the reasoning first" — agents at machine speed require formally verified ontologies
- **"Vibe ontology" definition:** plausible, fluent, LLM-generated result that has NOT passed formal tests; "nothing reaches production that has not passed the tests"
- **8 capabilities:** formalization, analysis/proof, rule enforcement, graph building, serving/acting, scaling/security, agent grounding — each with specific technologies and standards
- **Rule governance principle:** "A rule copied into five applications will drift. A rule referenced from one governed source will not."
- **Four foundational requirements:** model correctness/completeness, demonstrable consistency, enforced business rules across systems, scalable secure infrastructure
- Source: [Inspired.org Oct 7, 2026](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production)

---

### 5. [new] Atlan: "Active Ontology" as 2026 Default — 95% of GenAI Pilots Failing; 38% SQL Accuracy Gain 🌐

**Claim:** Atlan's "Active Ontology" framing (2026) positions static ontologies as production-unsuitable and cites strong evidence: 95% of generative AI pilots failing, 40% of agentic projects to be canceled by 2027, 38% SQL accuracy improvement with semantic metadata.
**Evidence:**
- **95%** of generative AI pilot programs failing (MIT NANDA Report via Fortune)
- **40%+** of agentic AI projects will be canceled by end of 2027 due to inadequate risk controls (Gartner)
- **38%** relative improvement in AI-generated SQL accuracy with rich semantic metadata (Atlan internal, p < 0.0001)
- **50%+** of enterprise AI agent systems will incorporate context graphs for guardrailing/observability by 2028
- Only **27%** of organizations had KGs in production as of late 2025 (Google Cloud survey)
- **CME Group:** cataloged 18 million data assets + 1,300+ glossary terms in first year
- **Core claim:** active ontology stays synchronized with live data/lineage/governance; agents querying stale model "invent answers"
- Source: [Atlan Active Ontology](https://atlan.com/know/what-is-active-ontology/)

---

### 6. [new] JP: Netflix E2E Knowledge Graph — Ontology-Driven AutoSRE for Full-Stack Observability 🇯🇵

**Claim:** Zenn/knowledge_graph (Mar 21, 2026) covered Netflix's QCon London 2026 talk: Netflix uses a unified observability ontology (E2EGraph) to connect user clients to infrastructure, powering an AutoSRE agentic system.
**Evidence:**
- **Core innovation:** E2EGraph unifies observability data via formal ontology types (User Session, API Call, Deployment Event, QoE Regression) — normalizes across heterogeneous data sources
- **AutoSRE:** coordinator agent decomposes NL questions → specialized agents (metrics, alerts, experiments, deployments) via shared ontology → root-cause synthesis
- **Key problem solved:** traditional observability tools cannot answer "which business capability does this API serve?" or "how does this failure impact UX?"
- **Distinct from IT-focused observability:** extends to business metrics (QoE, experimentation outcomes) within same semantic layer
- **Future planned:** predictive pattern analysis + self-healing automation (rollbacks, traffic shifts, config changes)
- JP quote: "観測用に**統一オントロジー**へ正規化するデータエンジニアリング上の課題" (Data engineering challenge: normalizing into unified observability ontology)
- Source: [Zenn/knowledge_graph Netflix QCon](https://zenn.dev/knowledge_graph/articles/netflix-qcon-e2e-knowledge-graph)

---

### 7. [new] JP: Protégé vs Fabric IQ — Data Engineer Evaluates Lightweight vs Heavyweight Ontology 🇯🇵

**Claim:** Zenn/bare64 (May 4, 2026) — dbt Labs PSA evaluates Protégé vs Fabric IQ for ontology, finding: lightweight delivers AI compatibility, heavyweight delivers logical rigor; neither is universally correct; recommends graduated adoption by domain complexity.
**Evidence:**
- **Fabric IQ (lightweight):** graph-based concepts, entity types/properties/relationships, multi-source OneLake, limited inference
- **Protégé (heavyweight):** OWL foundation, automatic classification, inconsistency detection — requires formal logic/description logic knowledge
- **Critical finding:** lightweight tools lack integrity safeguards; inconsistencies remain undetected; heavyweight demands significant CS expertise
- **Graduated recommendation:** simple domains → Semantic Layer + documentation; complex domains → start lightweight, escalate rigor
- JP quote: "軽い側は AI エージェントとの相性とドメインの記述力を、重い側はそれらに加えて推論による厳密性を、それぞれもたらしてくれ" (Lightweight: AI compatibility + domain expressiveness; heavyweight: adds logical rigor)
- Source: [Zenn/bare64 ontology practice](https://zenn.dev/bare64/articles/ontology-data-platform-practice)

---

### 8. [new] CN: CCKS 2026 (Aug 21-23, Xi'an) — 20th National KG + Semantic Computing Conference 🇨🇳

**Claim:** CCKS 2026 (Aug 21-23, Xi'an Jiaotong University) concluded as China's flagship KG + LLM academic conference; 8 evaluation tasks focused on KG-LLM integration and agent architecture.
**Evidence:**
- 20th National Conference on Knowledge Graph and Semantic Computing (全国知识图谱与语义计算大会)
- Host: Xi'an Jiaotong University; organizer: CIPS Professional Committee on Language and Knowledge Computing
- **8 evaluation tasks** on KG-related topics including: KG-enhanced large models, agent architecture, knowledge representation, reasoning
- Focus topics: knowledge graph + large model agents; interpretability; ethics; KG-enhanced large model architectures
- **WAIE 2026 upcoming (Oct 23, Shenzhen):** 10th World AI Industry Conference releasing 《2026 中国智能体 AI 产业应用标杆案例蓝皮书》 (2026 China AI Agent Industry Application Benchmark Bluebook)
- Sources: [CCKS 2026 official](https://sigkg.cn/ccks2026/) · [KMedu Hub CCKS](https://kmeducationhub.de/china-conference-on-knowledge-graph-and-semantic-computing-ccks/) · [CSDN WAIE 2026](https://www.csdn.net/article/2026-09-29/166842145)

---

### 9. [new] CN: 53AI Three-Phase Enterprise Path — Ontology → KG → World Models 🇨🇳

**Claim:** 53AI founder Yang Fangxian (Jul-Aug 2026) articulates a three-phase enterprise path for semantic AI infrastructure: unified language (ontology) → fact connection (KG) → consequence simulation (world models).
**Evidence:**
- **Phase 1 (Ontology):** "本体论解决的是概念边界和业务口径问题" — establishes clear definitions for business objects before data collection
- **Phase 2 (KG):** entity-relationship networks answering "what exists" and "what relationships connect these entities"
- **Phase 3 (World Model):** state transitions, predictive reasoning ("what happens if"), consequence simulation
- **Warning:** don't skip foundational work to pursue advanced capabilities
- **Practical guide (Aug 6):** minimum viable ontology = 8 entity types; four-question test (node vs attribute); start with one problem ("complaint root cause" not comprehensive coverage); five common mistakes
- Sources: [53AI Jul 28](https://www.53ai.com/news/knowledgegraph/2026072804689.html) · [53AI Aug 6](https://www.53ai.com/news/knowledgegraph/2026080686240.html) · [53AI Jul 24](https://www.53ai.com/news/knowledgegraph/2026072435167.html)

---

**Still true** (ongoing threads, no new facts this run):
- dell-ai-platform-kg-semantic-layer: Dell KG + Semantic Layer H1 2027 roadmap unchanged
- okf-agent-memory-hn-bm25: OKF v0.4.4 still current; BM25 61% vs semantic 37% result unchanged
- graphify-codebase-kg-no-vector: v0.9.53; 124K stars; no new release
- ob-caie-ontology-ai-evaluation: arXiv:2610.00529 still current
- evoontology-self-evolving-mcp-server: arXiv:2609.15779; no new updates
- turbopuffer-v3-ann-primary-retired: v3 live; ANN-primary removed; no new changes
- agentmemory-dotnet-pole-plus-o: 178/178 Neo4j TCK; POLE+O for .NET
- blitzy-coding-agents-neo4j-graph: $200M; SWE-Bench 84.95%
- hn-getcassis-entity-graph-complexity: memories/state/handoff must NOT share ontology
- memory-portability-model-upgrade: KG ±0.0020 vs NOTES ±13pp (arXiv:2609.05339)
- moosedev-nesy2026-ontology-coding-memory: 0.98–1.00 recall vs 6–27% vector
- industrial-kg-unification-287-mcp-tools: 287 MCP tools; recall 1.00→0.31 without cross-system
- evograph-mem-failure-aware-editable: append-only insufficient for long-horizon tasks
- llm-guided-ontology-kg-construction-ijckg2026: quantized 7B–32B + schema-guided prompting (IJCKG 2026 Nov)
- trikedb-cyberagent-lightweight-ontology-yaml: 88.7% WebQSP at 250-triple budget
- aml-agent-memory-leaderboard: Cycle 2 open; Oct 31 deadline; no results
- hindsight-v0100-multimodal-memory: Cloud 0.10.0 (Sep 21); Hermes plugin; no new Oct release
- cognee-1-0-four-verb-api: v1.6.1 (Sep 24); BEAM 79%@100K; no Oct release
- zep-ce-retired-graphiti-open-source: Graphiti v0.30.2; no new release found
- ekaw-2026-knowledge-engineering-conference: concluded Oct 1; proceedings still unpublished
- graphwise-events-oct-2026: SLS Vienna Oct 14-15 still upcoming
- benchmark-proliferation-memory: 7+ benchmarks; AML Cycle 2 open
- okf-v02-provenance-trust: OKF v0.2/v0.4.4; no v0.5
- okf-v01-structural-interoperability: structural interoperability; semantic gap future work
- mem0-v2-token-efficiency: 66.6K stars; no new Oct algorithmic changes
- graphwise-oakley-semantic-layer-pe: Oakley Capital; 30%+ ARR; no new news
- semantics-2026-ghent: concluded Sep 17; ORKG award; no new Oct news
- databricks-genie-ontology: no new October updates
- databricks-context-engineer-cert: $200/90min; GA Jul 29; only context cert in industry
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1; no new October updates
- benchmark-vendor-inflation-measured: Mnemoverse Q3 confirms 20pp vendor inflation
- hindsight-memory-benchmark-leader: 94.6% LME; 92% LoCoMo; no new benchmark changes
- parametric-kg-storage-retrieval-gap: LoRA parametric KG stores +0.243 EM but retrieval at chance
- selective-forgetting-kg-vs-flat: KG F1=0.417 vs flat 0.468 on LME (arXiv:2608.28978)
- megamem-ultra-large-context-retrieval: 650M+ tokens; EnterpriseRAG-Bench 68.22→82.26
- graph-personalized-memory-survey-ickg2026: lifecycle-oriented ICKG 2026 survey
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview
- jp-ontology-to-tool-mechanical-generation: 12-obj/34-action YAML → 58 tools
- mem0-strands-osv3-algorithm: native AWS Strands; single-pass ADD-only
- msock-intellect-enterprise-spatial-graph: 21-dimensional Enterprise Spatial Graph; banking
- heimdall-trust-verified-kg-coding: cross-repo KG; CPU-only; 12,800 nodes
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction; 11,860 stars (DeusData)
- jp-ontology-driven-graphrag-construction: entity unification 72→94%; +23pp (Qiita/@hisaho)
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference irreversibly
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale
- jp-two-layer-memory-write-gate: hot/cold two-layer + write-gate
- ontologx-autonomous-log-kg: cybersecurity log→ontology KG (Wiley AISY)
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory; vector+KG hybrid
- cn-china-agent-government-regulation: first government bounding agent authority (May 2026)
- magg-governed-kg-construction: +47% strict F1 SciERC; no predefined schema
- metaphactory-6-ontopic-virtual-kg: Ontopic acquired; metaphactory 5.9 VKG/OBDA
- memorax-code-coding-plugin: 4 memory types; Claude Code/Codex/WorkBuddy
- jp-zenn-kg-memory-entity-resolution: entity resolution = primary KG engineering barrier
- jp-note-semantic-layer-vs-ontology-failure: 60% projects fail without SL (Gartner)
- memos-memory-os-proactive-scheduling: 3-tier Memory OS; Memory Cube; Memory Marketplace
- openkg-spg-kag-skillnet-dynamic-eval: Claude 4.5 at 37.65% on dynamic eval
- jp-coa-deployment-53pct-variance: COA eliminates 53% answer variance
- aws-context-ontology-accelerator: months→days; OWL 2+HermiT; Apache 2.0
- mnemoverse-hebbian-memory: Hebbian + Rescorla-Wagner; 20pp vendor inflation confirmed
- neo4j-constant-cost-semantic-memory: Oct 15 workshop upcoming; NODES Nov 12
- sap-knowledge-graph-autonomous-enterprise: 452K tables; 50+ Joule Assistants
- neo4j-labs-agent-memory-nams: POLE+O; 178/178 TCK; NAMS hosted service
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG
- apache-ossie-semantic-interchange: Kyvos+Databricks members; no Oct updates
- mcp-ontology-integration-protocol: MCP 2026-07-28 final spec; all major tools MCP-native
- ontology-as-reliability-infrastructure: EN/JP/CN independently frame ontology as correctness layer
- hn-5-mistakes-kg-memory: POLE+O practitioner baseline; schema decides everything
- cn-ontology-strategic-return: strategic return confirmed; ongoing
- tencent-tbox-abox-framing: TBox (LLM) / ABox (human validates)
- vector-db-market-growth: $3.47B KG market 2026; ongoing
- architecture-beats-model-scale: retrieval architecture dominates model scale
- ontology-guardrails-framing: ontology as correctness guardrails; 36-46% multi-hop gains
- cn-llms-reshape-ontology-engineering: TBox generation by LLM; human validates ABox
- jp-layered-implementation-path: SL (2-6mo) → Lightweight Ontology → MCP
- jp-qiita-ontology-department-alignment: root cause = missing ontology, not model quality
- benchmark-proliferation-memory-dup: placeholder — no content; carries forward
- jp-ontology-for-data-engineers-zenn: Zenn/bare64 (first article); SL+ontology both needed
- jp-lightweight-ontology-fixed-queries-bigquery: Zenn/mbk_digital; fixed queries not generative
- jp-graph-infra-ai-agents-index-free: Qiita/yohei1126; index-free adjacency
- cn-ontology-strategic-return: ongoing

---

## Cross-Source Patterns

**1. Formal ontology verification becomes non-negotiable as agents operate at machine speed** 🌐
- Inspired.org (Oct 7): 8 engineering capabilities; "vibe ontology" critique; Fabric IQ V2 adds proposal-review model; IBM Research ISWC paper: imperative + generative for traceable answers
- Platforms: Inspired.org (EN), IBM Research (EN), Microsoft (EN), Atlan (EN)
- Quote: "An agent that books, approves, reorders or escalates acts on what it believes, at machine speed, and nobody reads the reasoning first." — Graham McLeod, Inspired.org ([link](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production))

**2. Memory structure converging: palace/room metaphors and hierarchical MemFS** 🌐
- Letta v0.34 introduces "Memory Palace" (palace/ folder as structured MEMORY.md-first, Cloud-only); MemPalace OSS (43K stars Apr 2026) uses palace/wing/room hierarchy; both move away from flat append-only storage
- Platforms: Letta GitHub, MemPalace GitHub, ossinsight.io
- Quote: "Moving from specialized memory tools that edit memory in a database to generalized computer use tools like bash that operate over memory projected into git-backed files" — Letta MemFS docs ([link](https://docs.letta.com/letta-code/memfs))

**3. JP community maturing from "should we use ontology?" to "how do we build production-grade ones?"** 🇯🇵
- Netflix E2E KG (ontology for observability + AutoSRE); Zenn/bare64 evaluates Protégé vs Fabric IQ tradeoffs; Zenn/knowledge_graph domestic case studies
- Shift: from conceptual articles to engineering practice comparisons
- Quote: "軽い側は AI エージェントとの相性とドメインの記述力を、重い側はそれらに加えて推論による厳密性を、それぞれもたらしてくれ" (Lightweight: AI compat + domain expressiveness; heavyweight: logical rigor) — Zenn/bare64 ([link](https://zenn.dev/bare64/articles/ontology-data-platform-practice))

**4. CN community articulates ontology→KG→world model as three-phase progression** 🇨🇳
- 53AI Jul-Aug 2026: explicit three-phase enterprise path; CCKS 2026: KG + LLM integration now has 8 formal evaluation tasks; WAIE 2026 upcoming: official China AI agent benchmarks
- Platforms: 53AI, CCKS 2026 (Xi'an), WAIE 2026 (Shenzhen)
- Quote: "先选一个切口，例如'投诉根因定位'或'流失预警'。不要一开始就试图覆盖全电信业务场景" (Choose one entry point—don't attempt full coverage initially) — 53AI Aug 6 ([link](https://www.53ai.com/news/knowledgegraph/2026080686240.html))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| okf_memory | OKF Agent Memory – Git-native persistent memory | 81 | 32 | "BM25 basically ties embeddings here at 1/100th the cost" | [link](https://news.ycombinator.com/item?id=49581240) |
| (prior) | I spent a year building agent memory on KGs — 5 mistakes | — | — | "Schema decides everything" | [link](https://news.ycombinator.com/item?id=48337689) |
| (Sep 2025) | Everyone's trying vectors and graphs for AI memory. We went back to SQL | 136 | 63 | "reinvents vector embeddings" (critic); "LLMs excel at SQL" (proponent) | [link](https://news.ycombinator.com/item?id=45329322) |

**Web (global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | MS Learn (updated Oct 6) | [Fabric IQ Ontology overview](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview) | V2 now DEFAULT; old retires Jan 31, 2027; keyless entities, inheritance, optional graph |
| 🌐 | MS Learn | [Azure Foundry Fabric IQ](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/fabric-iq) | Connect agents to Fabric IQ via MCP |
| 🌐 | MS Learn | [Copilot Studio MCP Fabric IQ](https://learn.microsoft.com/en-us/microsoft-copilot-studio/mcp-fabric-iq-ontology) | MCP integration for ontology agents |
| 🌐 | Wasita | [V2 fact-check](https://wasita.net/blog/fabric-iq-ontology-what-is-real/) | V2 features confirmed; Sep 25 briefing; preview week targeted |
| 🌐 | Fabric Community | [IQ GA vs Ontology Preview](https://community.fabric.microsoft.com/blog/fiq_comm_blog/fabric-iq-is-ga-your-ontology-isnt-heres-what-that-actually-means-/5364087) | GA vs Preview distinction |
| 🌐 | Emergent Software | [Fabric IQ explained](https://www.emergentsoftware.net/resources/insights/fabric-iq-explained-connecting-data-semantics-and-ai-across-the-enterprise/) | Semantic models + ontology layering |
| 🌐 | Acuvate | [Fabric IQ enterprise](https://acuvate.com/blog/microsoft-fabric-iq-ontology-enterprise-ai/) | Implementation guidance |
| 🌐 | Atlan | [Fabric IQ definition](https://atlan.com/know/microsoft-fabric/what-is-fabric-iq/) | 2026 scope definition |
| 🌐 | Letta GitHub | [v0.34.0](https://github.com/letta-ai/letta-code/releases/tag/v0.34.0) | Memory Palace + async user questions |
| 🌐 | Letta GitHub | [v0.34.2](https://github.com/letta-ai/letta-code/releases/tag/v0.34.2) | Stream completion; workflow fixes |
| 🌐 | Letta GitHub | [v0.34.4](https://github.com/letta-ai/letta-code/releases/tag/v0.34.4) | Read-only MemFS; scratchpad for subagents |
| 🌐 | Letta GitHub PR | [Memory Palace experiment #4754](https://github.com/letta-ai/letta-code/pull/4754) | Memory Palace implementation |
| 🌐 | Letta GitHub PR | [Memory Palace Cloud-only #4866](https://github.com/letta-ai/letta-code/pull/4866) | Cloud-only restriction |
| 🌐 | IBM Research | [Transparent Traceable Deterministic ISWC 2026](https://research.ibm.com/publications/transparent-traceable-deterministic-agentic-memory-via-knowledge-graphs) | IBM agentic memory KG; open-sourced; Oct 25 |
| 🌐 | IBM Research | [Personal Agents Conversational Memory ESWC 2026](https://research.ibm.com/publications/personal-agents-and-conversational-memory) | Related ESWC 2026 paper |
| 🌐 | ISWC 2026 | [iswc2026.semanticweb.org](https://iswc2026.semanticweb.org/) | Oct 25-29 Bari conference site |
| 🌐 | GLOW workshop | [glow-workshop.github.io/iswc2026](https://glow-workshop.github.io/iswc2026/) | 14 papers on graph + LLMs |
| 🌐 | Semmtech | [ISWC paper](https://semmtech.com/event/semmtech-x-iswc-26/) | Ontology-based enterprise KM with Arcadis |
| 🌐 | arXiv | [2507.12311 Ontology Interoperability Ecosystem](https://arxiv.org/html/2507.12311v9) | ISWC 2026 paper |
| 🌐 | Inspired.org | [Oct 7 production ontology](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production) | "Vibe ontology" critique; 8 capabilities |
| 🌐 | Atlan | [Active Ontology](https://atlan.com/know/what-is-active-ontology/) | 95% pilots failing; 40% projects canceled; 38% SQL gain |
| 🌐 | Atlan | [Context layer for AI agents](https://atlan.com/know/context-layer-for-ai-agents/) | Enterprise context layer guide |
| 🌐 | Atlan | [Ontology vs Semantic Layer](https://atlan.com/know/ontology-vs-semantic-layer/) | Differences and how to choose |
| 🌐 | Atlan | [Ontology in AI](https://atlan.com/know/what-is-ontology-in-ai/) | Components, standards, agent applications |
| 🌐 | Atlan | [Fabric MCP servers](https://atlan.com/know/microsoft-fabric/fabric-mcp-servers/) | Fabric MCP server types |
| 🌐 | Zenodo | [AgentKG v0.12.1](https://zenodo.org/records/22837491) | Conversational memory as queryable KG; MCP |
| 🌐 | Neo4j | [TWIN4j Oct 2026](https://neo4j.com/blog/twin4j/this-week-in-neo4j-nodes-agentmemory-graphrag-knowledgelayer-and-more/) | NODES 2026, Agent Memory, GraphRAG weekly |
| 🌐 | Neo4j | [NODES AI: Agentic GraphRAG video](https://neo4j.com/videos/nodes-ai-2026-agentic-graphrag-autonomous-knowledge-graph-construction-and-adaptive-retrieval-2/) | Autonomous KG construction + adaptive retrieval |
| 🌐 | Neo4j | [NODES AI: Context Engineering video](https://neo4j.com/videos/nodes-ai-2026-build-intelligent-ai-agents-with-context-engineering/) | Building agents with context engineering |
| 🌐 | Neo4j | [NODES AI: Graph World Models video](https://neo4j.com/videos/nodes-ai-2026-agent-reasoning-with-graph-world-models/) | Agent reasoning with graph world models |
| 🌐 | Neo4j | [NODES agenda](https://neo4j.com/nodes-ai/agenda/from-data-to-knowledge-to-action-the-graph-intelligence-platform/) | Vector RAG to GraphRAG session |
| 🌐 | Graphiti | [Releases](https://github.com/getzep/graphiti/releases) | Still v0.30.2; no Oct release |
| 🌐 | MemPalace | [GitHub](https://github.com/mempalace/mempalace) | 43K stars April 2026; palace metaphor memory |
| 🌐 | OSSInsight | [Agent memory race](https://ossinsight.io/blog/agent-memory-race-2026) | 5 repos, 4 architectures, 1 unsolved problem |
| 🌐 | Mnemoverse | [Q3 2026 comparison](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3) | Letta 52.2%, Mem0 50.0%, Zep/Graphiti 37.0% |
| 🌐 | Cognee | [Changelog](https://www.cognee.ai/changelog) | v1.6.1 Sep 24; Google account integration |
| 🌐 | Memgraph | [Cognee integration](https://memgraph.com/blog/from-rag-to-graphs-cognee-ai-memory) | Cognee + Memgraph alternative to Neo4j |
| 🌐 | AML | [agentmemoryleaderboard.ai](https://agentmemoryleaderboard.ai/) | Cycle 2 open; Oct 31 deadline |
| 🌐 | Graphwise | [SLS Vienna Oct 14-15](https://graphwise.ai/event/semantic-layer-symposium-2026/) | Upcoming |
| 🌐 | SLS official | [semanticlayersymposium.com](https://semanticlayersymposium.com/) | Official SLS site |
| 🌐 | EKAW 2026 | [ekaw2026.di.unito.it](https://ekaw2026.di.unito.it/) | Concluded Oct 1; proceedings still pending |
| 🌐 | arXiv | [2604.11364 Missing Knowledge Layer](https://arxiv.org/pdf/2604.11364) | Cognitive architectures for AI agents need KL |
| 🌐 | arXiv | [2606.30306 Always-On Agents](https://arxiv.org/pdf/2606.30306) | Survey of persistent memory, state, governance |
| 🌐 | arXiv | [2607.21503 Agentic Context Management](https://arxiv.org/pdf/2607.21503) | Agent memory as lifecycle + architecture problem |
| 🌐 | arXiv | [2507.20643 Ontology-Enhanced KG Completion](https://arxiv.org/html/2507.20643v2) | LLMs for ontology-enhanced KG completion |
| 🌐 | arXiv | [2510.20345 LLM-empowered KG survey](https://arxiv.org/abs/2510.20345) | LLM KG construction survey (Oct 2025) |
| 🌐 | kenhuangus Substack | [Why Ontology Matters 2026](https://kenhuangus.substack.com/p/why-ontology-matters-for-agentic) | From world models to governable decisions |
| 🌐 | Hacknoon | [Context Graphs Enterprise AI race](https://hackernoon.com/context-graphs-ontologies-and-the-race-to-fix-enterprise-ai) | Context graphs + enterprise AI |
| 🌐 | OvalEdge | [Ontology in AI agents](https://www.ovaledge.com/blog/ontology-in-ai) | Agents reason on enterprise data |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Zenn/knowledge_graph | [Netflix QCon E2E KG](https://zenn.dev/knowledge_graph/articles/netflix-qcon-e2e-knowledge-graph) | **NEW** AutoSRE + unified observability ontology (Mar 21, 2026) |
| 🇯🇵 | Zenn/bare64 | [Ontology practice](https://zenn.dev/bare64/articles/ontology-data-platform-practice) | **NEW** Protégé vs Fabric IQ; lightweight vs heavyweight (May 4, 2026) |
| 🇯🇵 | Zenn/bare64 | [Ontology for data engineers (first)](https://zenn.dev/bare64/articles/ecac1bbf510ce4) | SL+ontology complementary; Fabric/Neo4j/Palantir |
| 🇯🇵 | Zenn/mbk_digital | [Lightweight ontology next-tokyo-2026](https://zenn.dev/mbk_digital/articles/next-tokyo-2026-ontology) | Fixed queries not generative; BigQuery Graph |
| 🇯🇵 | Qiita/yohei1126 | [Next-gen data infra for AI agents](https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80) | Index-free adjacency; 4 RAG types |
| 🇯🇵 | Zenn/komlock_lab | [What is Ontology](https://zenn.dev/komlock_lab/articles/ontology-for-ai-engineering) | Ontology as "業務OS" (business OS) |
| 🇯🇵 | Zenn/knowledge_graph | [KG domestic case studies](https://zenn.dev/knowledge_graph/articles/kg-japan-case-studies) | Japan company KG + causal inference |
| 🇯🇵 | Qiita/taka_yayoi | [Databricks Genie Ontology](https://qiita.com/taka_yayoi/items/35e4b28280290c131ee3) | OntoRank; snippets vs metric views |
| 🇯🇵 | CyberAgent | [trikedb lightweight ontology](https://developers.cyberagent.co.jp/blog/archives/65814/) | YAML/RDF; Oxigraph; model2vec; MCP |
| 🇯🇵 | Qiita/hisaho | [GraphRAG × Ontology](https://qiita.com/hisaho/items/175ca3f80f35abf195f0) | Entity unification 72→94%; +23pp accuracy |
| 🇯🇵 | Zenn/aws_japan | [COA deployment](https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy) | 53% answer variance eliminated |
| 🇯🇵 | note/_kihonushi | [SL before ontology](https://note.com/_kihonushi/n/nad1b98d60300) | 60% failure without SL (Gartner) |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | CCKS 2026 | [sigkg.cn/ccks2026](https://sigkg.cn/ccks2026/) | **NEW** 20th national KG + semantic computing conference (Aug 21-23, Xi'an) |
| 🇨🇳 | CSDN | [WAIE 2026 Oct 23](https://www.csdn.net/article/2026-09-29/166842145) | **NEW** China AI Agent Industry Conference + 2026 China AI Agent benchmarks bluebook |
| 🇨🇳 | 53AI | [Ontology/KG/World Models Jul 28](https://www.53ai.com/news/knowledgegraph/2026072804689.html) | **NEW** Three-phase enterprise path: Ontology → KG → World Model |
| 🇨🇳 | 53AI | [Practical KG from Ontology Aug 6](https://www.53ai.com/news/knowledgegraph/2026080686240.html) | **NEW** Minimum viable ontology (8 types); four-question test; 5 mistakes |
| 🇨🇳 | 53AI | [Ontology overlooked knowledge infra Jul 24](https://www.53ai.com/news/knowledgegraph/2026072435167.html) | Ontology as core AI infrastructure |
| 🇨🇳 | 53AI | [Enterprise KG inflection Jun 26](https://www.53ai.com/news/knowledgegraph/2026062632790.html) | Ontology + LLM + MCP = KG inflection |
| 🇨🇳 | Juejin | [KG in Agent era](https://juejin.cn/post/7659258669087211554) | 4 strategic roles; self-evolving schema |
| 🇨🇳 | Zhihu | [Agent memory panoramic survey](https://zhuanlan.zhihu.com/p/2021713241647096178) | 3-layer architecture; vector+KG hybrid |
| 🇨🇳 | Juejin | [Agent memory engineering](https://juejin.cn/post/7674574367977160767) | 6 core mechanisms; ontology prevents inconsistency |
| 🇨🇳 | Tencent Cloud | [TBox/ABox framing](https://cloud.tencent.com/developer/article/2540120) | TBox (LLM generates) / ABox (human validates) |
| 🇨🇳 | 53AI | [EvoOntology active](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html) | "Graph的尽头是自进化Ontology" |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct access)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not searched directly)
├─ 🟢 HN: 1 thread (prior, HN:49581240) │ 81 pts │ 32 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (Bluesky=OK per health; minimal on-topic posts found)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 60+ pages │ 🇯🇵 12 │ 🇨🇳 11
└─ 🗣️ Top voices: Graham McLeod (Inspired.org), Anna Lisa Gentile (IBM/ISWC), Yang Fangxian (53AI) │ Zenn/knowledge_graph, Zenn/bare64, 53AI
```

---

## Out of Scope but Notable

- **MemPalace (43K stars, April 2026; Milla Jovovich creator):** Chronicle of fastest-growing developer memory tool — a cultural/viral signal for how agent memory moved mainstream. Architecture (ChromaDB palace metaphor, "store everything verbatim") contrasts sharply with ontology-grounded approaches. Benchmark controversy (96.6% claim partially retracted) illustrates ongoing vendor inflation problem. Possibly relevant to agent-harnesses topic. [GitHub](https://github.com/mempalace/mempalace) · [ossinsight analysis](https://ossinsight.io/blog/agent-memory-race-2026)
- **AgentKG v0.12.1 (Zenodo, Sep 18, 2026):** Conversational memory as live queryable KG; semantic search + topic clustering + entity tracking + MCP. Small independent project but represents growing bottom-up KG memory ecosystem alongside commercial players. [Zenodo](https://zenodo.org/records/22837491)
- **Context Engineering 2.0 (arXiv:2510.26493, Oct 2025):** Reframes context engineering as entropy reduction discipline across four eras; era 2.0 = current; era 4.0 = machines proactively construct context. Adjacent to this topic but belongs more in agent-harnesses or context-engineering. [arXiv](https://arxiv.org/pdf/2510.26493)

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** Returned CAPTCHA challenges for both JP and CN queries — no hub results via DDG. Fell back to native-language WebSearch, which reached Zenn/Qiita/53AI/Juejin through indexed content. Coverage of JP/CN likely ~75% of what DDG pass would have yielded
- **Reddit:** No direct access; r/KnowledgeGraphs, r/MachineLearning, r/LocalLLaMA absent
- **Bluesky:** Bluesky=OK per SOURCE HEALTH; Bluesky search returned profile links (TGDK journal, GRAPHIA project) but no high-engagement on-topic posts
- **EKAW 2026 proceedings:** Still unpublished (conference concluded Oct 1)
- **AML Cycle 2 results:** Deadline Oct 31; no submissions data yet
- **SLS Vienna (Oct 14-15):** Not yet occurred; no coverage available
- **Graphiti/Zep:** No new October release; Graphiti still v0.30.2 (no v0.31 found)
- **Hindsight, MemoraX:** No new October updates found
- **CCKS 2026 proceedings:** SSL certificate expired on sigkg.cn; could not fetch detailed paper list
- **WAIE 2026:** Occurs Oct 23 (upcoming); no content yet
- **Coverage estimate:** ~73% — strong on enterprise releases (Fabric IQ V2 default, Letta v0.34.x), ISWC 2026, JP/CN hubs; moderate on memory tool releases (Graphiti/Zep/Hindsight no Oct updates found); weaker on social engagement, Reddit, upcoming conferences

---

## Key Quotes

> "An agent that books, approves, reorders or escalates acts on what it believes, at machine speed, and nobody reads the reasoning first." — Graham McLeod, Inspired.org, Oct 7, 2026 ([link](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production))

> "A rule copied into five applications will drift. A rule referenced from one governed source will not." — Graham McLeod, Inspired.org ([link](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production))

> "Agents querying a stale model invent answers." — Atlan Active Ontology ([link](https://atlan.com/know/what-is-active-ontology/))

> "Nothing reaches production that has not passed the tests." — Graham McLeod on the "vibe ontology" failure mode ([link](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production))

> "観測用に**統一オントロジー**へ正規化するデータエンジニアリング上の課題" ("Data engineering challenge: normalizing diverse data into a unified observability ontology") — Zenn/knowledge_graph on Netflix E2EGraph ([link](https://zenn.dev/knowledge_graph/articles/netflix-qcon-e2e-knowledge-graph))

> "軽い側は AI エージェントとの相性とドメインの記述力を、重い側はそれらに加えて推論による厳密性を、それぞれもたらしてくれ" ("Lightweight delivers AI compatibility and domain expressiveness; heavyweight adds logical rigor") — Zenn/bare64 ([link](https://zenn.dev/bare64/articles/ontology-data-platform-practice))

> "先選一个切口，例如'投诉根因定位'或'流失预警'。不要一开始就试图覆盖全电信业务场景" ("Choose one entry point such as complaint root cause analysis—don't attempt full coverage initially") — 53AI Aug 6, 2026 ([link](https://www.53ai.com/news/knowledgegraph/2026080686240.html))

> "本体论解决的是概念边界和业务口径问题" ("Ontology addresses conceptual boundaries and business terminology standardization") — Yang Fangxian, 53AI founder ([link](https://www.53ai.com/news/knowledgegraph/2026072804689.html))
