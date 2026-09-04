# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-09-04
**Query type:** GENERAL
**Sources:** WebSearch (English, Japanese, Chinese), WebFetch (Hindsight, arXiv, metaphacts/Ontopic, note.com, Qiita, Zenn, InfoQ, 53AI, Tencent Cloud, Graphwise), Hacker News, GitHub, arXiv, PRNewswire

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 thread | 3 pts, 2 comments | 🌐 HN:49383353 (low engagement) |
| Bluesky | 0 posts | — | 🌐 Backend OK; no topical posts surfaced |
| Web (global) | 38 pages | — | 🌐 WebSearch + WebFetch; arXiv, GitHub, PRNewswire, Hindsight, metaphacts, Graphwise, Atlan, Sourcegraph |
| Web (Japan) | 7 pages | — | 🇯🇵 Zenn, note.com, Qiita, ai-souken.com |
| Web (China) | 7 pages | — | 🇨🇳 InfoQ, 53AI, Tencent Cloud, CSDN, Zhihu, AI-Insight |

---

## Synthesized Findings

### 1. [new] MAGG: Multi-Agent Governed KG Construction — +47% F1, Beats MS GraphRAG

🌐 **Claim:** MAGG (arXiv:2608.28642, Aug 12, 2026) — multi-agent framework integrating governance into KG construction; each candidate triple assigned to a domain owner, validated against evidence, admitted through formal governance, stored with audit metadata.
- **Authors:** Bykampadi et al. (Agrawala lab)
- **Key innovation:** domain classifier auto-induces entity/relation types from source docs — no predefined schemas; works in open-world settings
- **Results — SciERC:** +47% strict triple F1; +51% mapped triple F1 vs standard extraction
- **Results — MuSiQue:** +9.0 exact-match, +11.2 token-F1 vs Microsoft GraphRAG
- **Governance architecture:** blinded review; governance-filtered triples show stronger source alignment than non-reviewed entries
- **Gap addressed:** most KGs are "flat stores of extracted triples" with no ownership, justification, or usage guidelines — MAGG adds all three
- **Source:** https://arxiv.org/abs/2608.28642

---

### 2. [new] Metaphactory 6.0 + Digital Science/Ontopic Acquisition — Virtual KG Access to Snowflake/Databricks/BigQuery/Redshift

🌐 **Claim:** Digital Science acquired Ontopic (March 2026; Ontop VKG/OBDA framework pioneer, Free Univ. of Bozen-Bolzano spin-off); integrated into metaphactory 6.0 (July 2026) — first enterprise ontology platform with virtual KG access to data warehouses without ETL.
- **Ontopic:** Ontop = leading open-source Virtual Knowledge Graph (VKG) / Ontology-Based Data Access (OBDA) framework
- **Metaphactory 6.0 features:**
  - Model → Map → Access workflow: define semantics, map to data, expose to AI
  - Virtual access: Snowflake, Databricks, BigQuery, Redshift (no ETL required)
  - AI co-author in Visual Ontology Editor (shared session, human + AI)
  - Native RDF + SPARQL 1.2 (W3C standards)
  - Semantic document annotation (beta)
- **Prior versions:** 5.9 (Oct 2025): Semantic Modeling Assistant + Search & Discovery Agent; 5.10 (Jan 2026): AI search + modular ontology management
- **SEMANTiCS 2026:** metaphacts exhibiting Sep 15-17, Ghent
- **Why it matters:** closes gap between enterprise data (warehouse) and semantic layer (ontology) without data movement; first tool to combine OBDA virtualization + collaborative AI ontology modeling
- **Sources:** https://www.digital-science.com/press-releases/digital-science-acquires-ontopic/, https://metaphacts.com/digital-science-acquires-ontopic-to-accelerate-the-customer-journey-for-enterprise-knowledge-graphs, https://metaphacts.com/metaphactory

---

### 3. [update] Hindsight: 16 Coding Agents, Knowledge Base as MCP Surface, Enterprise Security — Sep 1-2 Releases

🌐 **Claim:** Hindsight released Cloud June–August recap (Sep 1) + hindsight-coding-agents 0.5.0 (Sep 2) adding 4 new agents (pi, Qwen Code, DeepAgents Dcode, opencode 2) → 16 total; Knowledge Base is now a first-class MCP surface.
- **What's new since Sep 1 briefing:**
  - v0.9.2 (Aug 24): Knowledge Base as MCP surface (7 agent-facing operations); caller-supplied temporal_window (saves ~1.3s on large queries); GitHub Copilot provider; asymmetric embeddings; memory budget (385MB → 9.6MB peak); selective vector indexing
  - Sep 1 recap blog: OIDC/SAML SSO; org-wide MFA (TOTP/WebAuthn/SMS/email); queryable audit logs; Memory Defense Enterprise (prompt injection + 220+ secret pattern detection + LLM screening); 33% cheaper Retain operations
  - Sep 2 (coding-agents 0.5.0): pi (Earendil Works), Qwen Code, DeepAgents Dcode (LangChain), opencode 2 added; single `install all` command; shared bank named `coding-agent::{gitProject}` lets developers switch agents without losing context
- **Ongoing facts:** Knowledge Pages + SDE-bench public; 57-65% fewer corrections; prior v0.9.0 Aug 7
- **Sources:** https://hindsight.vectorize.io/blog/2026/09/01/hindsight-cloud-june-august-updates, https://hindsight.vectorize.io/blog/2026/09/02/coding-agents-050-four-new-harnesses, https://hindsight.vectorize.io/blog/2026/08/24/version-0-9-2

---

### 4. [new] SEMANTiCS 2026 (Sep 15-17, Ghent, Belgium) — Semantic Systems Conference This Month

🌐 **Claim:** SEMANTiCS 2026 (22nd annual International Conference on Semantic Systems, Ghent, Belgium, Sep 15-17) is the main European venue for knowledge graphs, semantic technologies, and AI integration — happening in 11 days.
- **Location:** Music Center de Bijloke, Ghent, Belgium
- **Keynotes:** Juan Sequeda (ServiceNow, Principal Data Strategist); Alessandra Mileo (Dublin City University); Daniel Garijo (Universidad Politécnica de Madrid)
- **Tracks:** KG/ontology construction, neuro-symbolic AI, LLMs+NLP, data modeling, semantic reasoning, product ontologies, linked data, data governance
- **Exhibitors:** metaphacts, Graphwise (+ Roche session on semantic layer)
- **Sources:** https://www.digital-science.com/events/semantics-2026/, https://graphwise.ai/event/semantics-2026/

---

### 5. [update] Graphwise Events: AI Summit (Oct 7-8) + Semantic Layer Symposium Vienna (Oct 14-15)

🌐 **Claim:** Post-Oakley investment, Graphwise announced free virtual AI Summit (Oct 7–8) and will present at Semantic Layer Symposium Vienna (Oct 14–15) with Roche.
- **AI Summit (Oct 7-8):** free, fully virtual, recorded; speakers from Roche, Accenture, AstraZeneca, S&P Global, Avalara, Cognizone
  - Day 1: ROI & Trust (business cases, governance, explainability, auditability)
  - Day 2: Infrastructure & Implementation (AI-ready data, KG, GraphRAG, semantic infrastructure)
- **Vienna (Oct 14-15):** Graphwise + Roche presenting: "semantic layer built on ontologies, FAIR vocabularies, and RDF infrastructure makes enterprise data AI-ready"
- **Industrial Semantic Interoperability Summit 2026** also upcoming
- **Sources:** https://www.prnewswire.com/news-releases/unlock-trust-and-roi-graphwise-announces-free-virtual-summit-to-help-leaders-secure-real-value-from-enterprise-ai-302828574.html, https://graphwise.ai/events/

---

### 6. [new] MemoraX Code: Coding Memory Plugin for 6 AI Agents

🌐 **Claim:** MemoraX released memorax-code (npm: @memorax/memorax-code), a background coding memory plugin supporting 6 AI coding agents with 4 specialized memory types.
- **Stars:** 1.2K; 57 forks; 381 commits; Node.js 20+; MIT
- **Memory types:** Coding Memory + Repo Memory + Personal Memory + Procedure Memory
- **Agents:** Claude Code, Codex, WorkBuddy, DeepSeek Harness, OpenCode, Trae
- **Feature:** background memory extraction from completed tasks; local trace records; cloud-backed via MemoraX platform
- **Context:** MemoraX remains AML #1 (58.02); second cycle opens Sep 20
- **Source:** https://github.com/memorax-ai/memorax-code

---

### 7. [new] JP: Semantic Layer vs Ontology — note.com Implementation Path (60% Failure Rate Without Semantic Layer)

🇯🇵 **Claim:** Japanese practitioners documenting a layered implementation path where skipping semantic layer before ontology leads to 60% project failure rates (Gartner); Gartner also warns 60% of MCP-only analytics will fail without semantic layer foundations by 2028.
- **Core distinction (JP):** 「セマンティックレイヤーは「収益はいくらか」を教え、オントロジーは「顧客とは何か」を教える」
  - English: "A semantic layer tells you what your revenue is. An ontology tells you what a customer is."
- **Semantic Layer:** predefined metrics, YAML/SQL/LookML/DAX, 2-6 months, deterministic
- **Ontology:** logical inference, RDF/OWL/SPARQL, 6-18 months, derives implicit facts
- **Critical warning:** 40% of agentic AI projects will cease by 2027 (Gartner); 60% MCP-only analytics fail by 2028 without semantic layer (Garcia-Rodeja); 63% of data leaders lack AI-ready data governance
- **Recommended path:** Semantic Layer (2-6mo) → Lightweight Ontology/Business Glossary (3-6mo) → Governance + Trust → MCP exposure to AI agents
- **Source:** https://note.com/_kihonushi/n/nad1b98d60300

---

### 8. [new] JP: Zenn KG Memory Design — Entity Resolution as First-Class Problem

🇯🇵 **Claim:** Zenn/@knowledge_graph articulates entity resolution (not schema design) as the primary engineering barrier in KG-as-agent-memory; unresolved ambiguity must route to review queues, not forced merges.
- **Quote (JP):** 「スキーマが良くても、ソースデータが「Acme」「acme」「ACME」と揺れていれば名寄せの精度は落ちます」
  - English: "Even with excellent schema design, entity resolution degrades when source data shows naming inconsistencies."
- **Three matching strategies:** Deterministic (exact domain match) / Fuzzy (similarity scoring) / Composite (multiple attributes)
- **Incremental approach:** start with 3-5 nodes + minimal edges in Mermaid; expand based on actual agent usage patterns
- **Core principle:** focus on "ドメインの意味構造をどう表現するか" (domain meaning structures) not data storage
- **Source:** https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design

---

### 9. [new] CN: MemOS Framework — Proactive Memory Scheduling + Memory Marketplace Vision

🇨🇳 **Claim:** 记忆张量 (Memory Tensor) CTO Li Zhiyu published MemOS framework architecture on InfoQ, positioning proactive memory scheduling (not reactive retrieval) as the next frontier after context engineering.
- **Three-tier stratification:** Parametric memory (weights) + Activated memory (KV Cache) + Explicit memory (external storage)
- **Proactive scheduling (CN):** 「最恰当的时刻，把最匹配的记忆放到最恰当的位置」("at the optimal moment, place the most matching memory in the optimal location") — pre-warms during user idle time
- **Memory Cube:** minimal memory unit for asynchronous parallel preparation
- **Trigger-Scheduler-Retriever architecture:** event-driven memory coordination (not always-retrieve)
- **Chain of Memory (CoT):** active analysis what merits retention
- **Hybrid graph+vector:** avoids cost-prohibitive traditional KG while capturing relationship efficiency
- **Insight (CN):** 「模型决定上限，应用夯实下限」("models determine ceiling, applications establish floor")
- **Memory Marketplace:** vision for installable domain memory packages (analogous to app stores)
- **MemOS 1.0:** Memory-as-a-Service + Memory+Inference-as-a-Service; OpenMem community for standardization
- **Source:** https://www.infoq.cn/article/AIVoC9eKfZhW199IQkwB

---

### 10. [new] CN: OpenKG Annual Review — SkillNet (200K+ Skills) + Dynamic Eval Shows All Models Far Below Adequate

🇨🇳 **Claim:** OpenKG 2025-2026 annual review (53AI) reveals: LLM-generated synthetic data now exceeds human-annotated baselines when structured through ontologies; dynamic evaluation shows even Claude 4.5 at only 37.65% — all top models far below adequate.
- **OneGraph:** 36.79M triples, 86% accuracy; synthetic data via ontologies exceeds human annotation (+59.7% explicit logic transformations); (CN): 「合成数据不再是'低质'代名词」("Synthetic data no longer means low quality")
- **SPG+KAG:** framework-based reasoning (OpenSPG) + internalized reasoning (KAG-Thinker) co-exist; addresses "logical discontinuity" in agent planning; (CN): 「框架化推理与内化推理互补共生」("coexist symbiotically")
- **SkillNet:** 200,000+ skill reservoirs; 139,685 curated skills; 5-dimension eval (safety, completeness, executability, maintainability, cost-awareness); "how to do" not "what is"
- **OneEval (dynamic):** error analysis → dual-perspective synthesis → multi-model consensus; Claude 4.5: 37.65% — all top models far below satisfactory; static rankings mislead
- **Cognitive era framing (Tencent Cloud, CN):** 「AI发展正经历从模型时代向智能体时代再向认知时代的跃迁」("AI is transitioning from model era through agent era toward cognitive era")
- **Sources:** https://www.53ai.com/news/knowledgegraph/2026022019635.html, https://cloud.tencent.com/developer/article/2665379

---

### 11. [new] JP: AWS COA Deployment — 53% Answer Variance Without Ontology; 100% AI-Inferred FK Accuracy

🇯🇵 **Claim:** Zenn/aws_japan practitioners deploying AWS Context Ontology Accelerator documented 53% answer variance on the same "sales" question without ontology; COA's AI inference achieved 100% accuracy (5/5) on inferring foreign key relationships missing from Glue Data Catalog.
- **Concrete example:** same "sales" query → 5.6M (LLM SQL) vs 8.6M (predefined metrics) = 53% variance; ontology removes ambiguity
- **Three-tier resolution:** Tier 1: predefined metrics (deterministic); Tier 2: ontology-based SPARQL/SQL with relationship inference; Tier 3: document knowledge via graph traversal
- **FK inference:** 100% accuracy (5/5); confidence scores; distinguishes AI-derived from deterministic via provenance
- **Quote (JP):** 「間違えるより黙る」("better to stay silent than err") — returns "cannot determine" rather than hallucinated answers
- **Quote (JP):** 「グラフを辿ってアドホック分析要求に応える表現力」("ability to traverse graphs and address ad hoc analysis requests")
- **Source:** https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy

---

**Still true** (ongoing threads, no new fact this run):

- *graphwise-oakley-semantic-layer-pe* — Oakley majority stake Aug 19; 200+ clients; 30%+ ARR; Gartner +80%/-60% by 2027 (events added above)
- *jedify-context-graph-benchmark* — 75% token cost reduction; 87% SQL accuracy; $33M funding
- *memverge-memorybox-memory-sovereignty* — 記忆主权; cross-platform beta; closed beta ongoing
- *graphon-ai-seed-relational-memory* — $8.3M seed; graph-native multimodal memory
- *hn-shared-public-memory-experiment* — HN:49319814; adversarial degradation; personality drift
- *neo4j-create-context-graph-cli* — POLE+O CLI; Apache 2.0; <5min to working app
- *layerx-memory-scaling-failure* — dreaming collapses at 4,552; 228% context overflow; 11.3% graph linking
- *ekaw-2026-knowledge-engineering-conference* — Sep 29-Oct 1 Torino; "New Frontiers in Knowledge Engineering" (coming soon)
- *memorax-ai-endogenous-memory-funding* — AML #1 (58.02); second cycle opens Sep 20 (not yet released)
- *aml-agent-memory-leaderboard* — 136 teams; 200K+ clicks; second cycle opens Sep 20 — no new results
- *palantir-superrepo-ontology-as-code* — Beta Aug 3; TypeScript monorepo; cryptographically signed bundles
- *ozbrain-shared-cross-agent-knowledge* — HN:49394827; MCP knowledge store; provenance + conflict detection
- *onton-ontology-1-neurosymbolic-trust* — P@10 0.630 vs Google 0.543; wins 52/90 queries
- *neo4j-meta-knowledge-graph-self-improving* — lifecycle hooks + LLM extraction loop; Claude Code+Codex
- *jp-acro-engineering-graphrag-vs-okf-benchmark* — OKF 100%/43.9% vs GraphRAG 78.9%/16.9%; 1/26th token cost
- *cognee-v1-4-0-dataset-overview* — Sep 2026 changelog: lexical-chunk retriever, temporal fixes, ontology resolver, weighted nodes/edges, DuckDB vector adapter, graph embeddings in paid plans
- *hindsight-v090-knowledge-pages* — updated above (0.5.0 Sep 2, 16 agents)
- *apache-ossie-semantic-interchange* — 50+ orgs; Kyvos Aug 12; native import/export expected year-end
- *databricks-genie-ontology* — snippets all customers Aug 13; Genie Code as Lakeflow Job; cert beta results expected mid-Sep 2026
- *mem0-v2-token-efficiency* — 61K+ stars; 186M quarterly API calls; v0.2.11 editor plugin
- *semantica-graph-native-provenance* — v0.6.0; MCP server; GDPR/HIPAA
- *starling-universal-cognitive-architecture* — UCA open standard; semantic coordinate retrieval; $99/mo
- *neo4j-labs-agent-memory-nams* — v0.5.0 NAMS; POLE+O; 3-tier memory
- *ontocast-ontology-assisted-kg* — v0.3.0; SHACL validation; RDF 1.2 provenance
- *memtools-interoperable-framework* — arXiv:2607.21404; CAS/BAAI; declarative contracts
- *graph-native-bitemporal-neo4j* — arXiv:2607.26520; HNSW+valid_time; 80% R@10
- *memtool-dynamic-tool-context* — arXiv:2507.21428; ECIR 2026; 90-94% tool-removal
- *hn-openknowledge-ai-notes* — HN:48675435; 381pts; AI-first Obsidian alt
- *jp-qiita-ontology-department-alignment* — departments get different numbers = missing ontology
- *aws-context-ontology-accelerator* — GA Jul 31; OWL 2+HermiT; months→days (COA deployment details added above)
- *crystalmem-elastic-memory* — arXiv:2608.00303; 50% memory budget match
- *shared-org-memory-coding-agents* — arXiv:2608.00122; enterprise Q&A memories for DSLs
- *mcp-memory-okf-sqlite* — OKF v0.2-backed MCP; SQLite FTS5; 5 MCP tools
- *tencentdb-agent-memory-v2* — v2.0 Aug 3; 4 assets; PersonaMem 48%→76%
- *coevokg-self-evolving-search* — arXiv:2608.01904; KG+RL; +11.2pp on 6 QA benchmarks
- *benchmark-vendor-inflation-measured* — Mem0 94.4% LME = 73.8% under Maximem (−20.6pp)
- *mragent-reconstructed-memory* — arXiv:2606.06036; ICLR 2026; active reconstruction
- *magma-multi-graph-memory* — arXiv:2601.03236; 4-graph decoupled
- *hage-rl-graph-evolution* — arXiv:2605.09942; RL-driven weighted graph evolution
- *mage-multi-agent-coevolving-kg* — arXiv:2605.10064; 4-subgraph co-evolutionary KG
- *bosun-memory-graph-cleaner* — HN:48493954; LoRA Qwen3-Reranker; WarrantBench
- *hyphaedb-living-topology* — arXiv:2606.28781; gossip-protocol vector topology
- *cloudflare-agent-memory-beta* — Apr 17; 5-channel parallel retrieval; RRF+HyDE
- *mnemoverse-hebbian-memory* — Hebbian+Rescorla-Wagner; 6 MCP tools
- *gene-ontology-kb-2026* — NAR 2026; 768 new terms; Functionome v2.0
- *neo4j-constant-cost-semantic-memory* — semvec; constant token cost per turn
- *memgraphrag-kdd-2026* — KDD 2026 Jeju; 59.25% avg; 0.061s retrieval
- *sap-knowledge-graph-autonomous-enterprise* — Sapphire 2026; 452K tables; 7.3M data fields
- *experience-graphs-trellis-meta* — arXiv:2606.29823; Meta; 10× speedup; 52% lower token cost
- *hindsight-memory-benchmark-leader* — updated (16 agents, v0.9.2)
- *longmemeval-v2-web-agent-experience* — arXiv:2605.12493; 451 questions; 115M token trajectories
- *stardog-bedrock-agentcore-semantic-layer* — AWS Blog Jul 10; SPARQL or MCP Gateway
- *ai-km-6-6-1-agentic-ontology-tooling* — ScienceDirect SoftwareX Jul
- *reagan-node-as-agent-graph* — arXiv:2508.00429; each node is an agent
- *databricks-context-engineer-cert* — GA Jul 29; beta results expected mid-Sep (not yet)
- *mandol-agglomerative-memory* — arXiv:2606.29778; CAS+MSFT; 92.21%/88.40% LoCoMo/LME
- *toki-bitemporal-contradiction-algebra* — arXiv:2606.06240; 3 write anomalies
- *agent-native-memory-readiness-survey* — arXiv:2606.24775; 12 memory systems; no single dominates
- *oracle-ai-agent-memory-26-6* — 93.8% LME; BEAM 0.680; 10.7× token reduction
- *redis-context-engine* — GA May 18; 3-component MCP-native
- *evermind-everos-self-evolving* — v1.1.1; HyperMem hypergraph; 93%+ retrieval
- *moss-auditable-relational-memory* — arXiv:2607.04391; SQL retrieval; 569 concepts
- *sage-graph-self-evolving-engine* — arXiv:2605.12061; reader-writer loop; 82.5/91.6 NQ Recall
- *kgermar-dynamic-kg-inference* — arXiv:2606.14047; 3 memory banks; 8.5% lower perplexity
- *mcp-spec-2026-07-28-rc* — stateless HTTP core; all hyperscalers aligned
- *selfmem-beam-sota-july-2026* — arXiv:2607.03726; KAUST; best BEAM 100K/500K/1M
- *automem-cognitive-skill* — arXiv:2607.01224; KAUST; 2-4× long-horizon games
- *self-gc-context-lifecycle* — arXiv:2607.00692; 43.95% token pruning
- *memrefine-budget-compression* — arXiv:2606.13177; LLM-guided factual budgeted compression
- *minio-aistor-memory* — Jul 29; unified memory (object+vector+secrets)
- *skan-aow-v1-agent-ontology* — Feb 10; 8 canonical entities; O2A Platform
- *agentic-context-management-lifecycle* — arXiv:2607.21503; 5 primitives; Maximem 92% LME
- *context-files-no-measurable-impact* — arXiv:2607.27250; 288 runs; ≤10-15pp impact
- *mem0-openmemory-mcp-local* — local Docker; 4 MCP tools; Chrome extension
- *smoothagent-lookahead-context* — arXiv:2607.00151; 11.9× TTFT reduction
- *memguard-role-typed-memory* — arXiv:2605.28009; +28.27% reliability; 5.8× fewer tokens
- *neo4j-thin-agents-graphsummit* — ZS Associates case study; 'formal ontology as logical guardrail'
- *less-context-better-agents* — arXiv:2606.10209; last-5 pruning → 91.6% vs 71%
- *context-graphs-proactive-enterprise* — arXiv:2607.07721; Delta Detection Engine; 47min→30s
- *exabase-m1-beam-sota* — Jul 28; 76.9/75.0/68.0% BEAM; 96.4% LME
- *okf-v02-provenance-trust* — v0.2 Jul 25; provenance+trust tiers; WitsCode validator
- *memanto-typed-semantic-memory* — arXiv:2604.22085; 13 types; <90ms; 89.8% LME
- *plugmem-icml-2026-microsoft* — arXiv:2603.03296; task-agnostic KG; outperforms task-specific
- *t-mem-anticipatory-retrieval* — arXiv:2606.15405; anticipatory retrieval
- *neuro-symbolic-tkg-meta-policy* — arXiv:2607.18368; best PORL results
- *netflix-e2e-kg-shared-ontology* — QCon London 2026; shared ontology AutoSRE agents
- *iso-23726-3-fdis* — FDIS Jun 3; OWL DL industrial automation
- *allegrograph-85-neuro-symbolic* — Mar 17 2026; expanded MCP support
- *memgraph-atomic-graphrag* — Feb 2026; Atomic GraphRAG single Cypher query
- *surrealdb-3-unified-agent-memory* — $44M; 8 data models; Spectron context layer
- *architecture-beats-model-scale* — benchmark convergence: memory architecture > model scale
- *engram-bi-temporal-memory-engine* — arXiv:2606.09900; 83.6% LME_S; 8× fewer tokens
- *sage-write-side-novelty-gate* — arXiv:2605.30711; vMF gate; 3.4× API cost vs Mem0
- *tokenpilot-cache-efficient-context* — arXiv:2606.17016; 61-87% context cost reduction
- *agenticts-bounded-memory-testbed* — arXiv:2607.02255; 5 per-decision slots; Slay the Spire 2
- *mempalace-zero-api-spatial-memory* — 56K GitHub stars; 96.6% Recall@5; spatial KG
- *ontology-dilution-problem* — Year of Graph Vol.31; 'ontology' escaped technical meaning
- *selective-ontology-injection-best-practice* — selective confidence-aware > always-on injection
- *ontology-guardrails-framing* — Jul 30 Latent Space; 36-46% multi-hop gains
- *cn-llms-reshape-ontology-engineering* — LLMs → dynamic generative ontology; TBox by LLM
- *jp-layered-implementation-path* — Semantic Layer → Ontology → MCP; 40% fail by 2027
- *okf-v01-structural-interoperability* — OKF v0.1 Jun 18; v0.2 Jul 25; no v0.3
- *memory-agent-bench-four-competencies* — ICLR 2026; 4-competency; all methods fall short
- *letta-pro-cloud-tier* — SDK Aug 2026; MemFS+dreaming; mods; $20/mo
- *zep-ce-retired-graphiti-open-source* — v0.29.3 Jul 27; saga abstraction; MCP 1.0; 63.8% LME
- *memora-microsoft-icml-2026* — 98% token reduction; highest LoCoMo/LME
- *fabric-iq-ontology-mcp* — Fabric IQ Ontology public MCP endpoints (Preview)
- *mcp-ontology-integration-protocol* — MCP 2026-07-28 final; all hyperscalers; all major tools MCP-native
- *ontology-as-reliability-infrastructure* — EN/JP/CN: ontology = correctness/reliability layer
- *benchmark-proliferation-memory* — 7+ active benchmarks; AML second cycle opens Sep 20
- *evomembench-no-single-memory-form* — arXiv:2605.18421; no single form consistently works
- *napmem-active-memory-navigation-rl* — arXiv:2607.05794; RL-based active memory navigation
- *placemem-compute-aware-memory-plane* — arXiv:2607.04089; versioned capsules cross-agent
- *agento-owl-rdf-agentic-ontology* — ESWC 2026; OWL/RDF for agentic workflows
- *always-on-agents-survey* — arXiv:2606.30306; 435 papers; AOEP-v0
- *ontobricks-open-ontologies-mcp* — Rust MCP server; Oxigraph+OWL2-DL+SHACL+SPARQL
- *eticas-ai-risk-taxonomy-v2* — arXiv:2607.02201; SKOS/JSON-LD; 76 subcategories
- *hn-5-mistakes-kg-memory* — HN:48337689; POLE+O practitioner baseline
- *neo4j-pole-o-hallucination-reduction* — 36-46% multi-hop gains; 40%+ hallucination reduction
- *memdelta-benchmark-nonportability* — arXiv:2606.29914; embedding swaps flip rankings by 6.2pp
- *eywa-evidence-before-belief* — arXiv:2605.30771; provenance-grounded SOTA long-horizon
- *ember-budgeted-evidence-retention* — arXiv:2606.05894; 0.3017 F1; fixed-budget write-side
- *projectmem-memory-as-governance* — Memory-as-Governance; 14 MCP tools; MIT
- *cn-ontology-strategic-return* — CN: 2026 KG strategic return; property graphs preferred
- *tencent-tbox-abox-framing* — TBox (schema/LLM) + ABox (instances/human)
- *ontology-interoperability-lifecycle-framework* — arXiv:2507.12311; ODPs → Matching/Versioning → Validation
- *trust-certificates-pre-deployment* — arXiv:2606.04037; ontology-backed pre-deployment certification
- *vector-db-market-growth* — $3.2B (2025) → $8.95B (2030) at 27.5% CAGR

---

## Cross-Source Patterns

**Pattern 1: Governance as the Missing Layer in KG/Memory (🌐 arXiv + JP practice + CN OpenKG)**
- MAGG (arXiv:2608.28642): KGs are "flat stores" — no ownership, justification, or usage guidelines; MAGG adds governance per triple
- Hindsight Memory Defense Enterprise: prompt injection detection + secret scanning per bank
- MAGG +47% F1; +9.0 EM vs MS GraphRAG — governance quality wins over volume
- OpenKG OneEval: static benchmarks "comparative"; dynamic eval shows 37.65% top model — ranking methodology itself under critique
- Pattern: governance (audit trails, domain ownership, evidence validation) shifting from nice-to-have to core architectural requirement for production KG/memory systems
- Sources: https://arxiv.org/abs/2608.28642, https://hindsight.vectorize.io/blog/2026/09/01/hindsight-cloud-june-august-updates, https://www.53ai.com/news/knowledgegraph/2026022019635.html

**Pattern 2: Virtual KG Closes the Semantic-Data Gap Without ETL (🌐 metaphacts + JP COA)**
- Metaphactory 6.0 + Ontopic: VKG access to Snowflake/Databricks/BigQuery/Redshift — no data movement
- JP: AWS COA deployment — 53% answer variance removed; 100% AI-inferred FK accuracy; three-tier resolution
- Pattern: semantic layers and ontologies can now be applied directly on top of existing data warehouses without requiring a separate KG ETL pipeline
- JP insight: reversing Semantic Layer → Ontology order leads to 60% project failure (note.com/@_kihonushi)
- Sources: https://metaphacts.com/metaphactory, https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy, https://note.com/_kihonushi/n/nad1b98d60300

**Pattern 3: September Conference Cluster — Semantic Systems Going Mainstream (🌐 SEMANTiCS + EKAW)**
- SEMANTiCS 2026 (Sep 15-17, Ghent): 22nd annual; keynotes from ServiceNow, DCU, UPM Madrid; semantic tech enters standard enterprise AI track
- EKAW 2026 (Sep 29-Oct 1, Torino): "New Frontiers in Knowledge Engineering"; knowledge engineering conference post-LLM era
- Graphwise AI Summit (Oct 7-8, free virtual); Semantic Layer Symposium Vienna (Oct 14-15)
- Pattern: September 2026 = densest cluster of semantic tech events ever — signal of mainstream enterprise adoption
- Sources: https://www.digital-science.com/events/semantics-2026/, https://ekaw2026.di.unito.it/, https://graphwise.ai/events/

**Pattern 4: Memory-as-Infrastructure Expands to Coding Agents (🌐 Hindsight + MemoraX Code)**
- Hindsight coding-agents 0.5.0: 16 agents; shared bank per git project; agents share context across tool switches
- MemoraX Code: 6 AI agents; 4 memory types; background extraction
- Pattern: "shared memory per project" is becoming standard infrastructure expectation for coding agents — 2026 equivalent of shared git history
- Sources: https://hindsight.vectorize.io/blog/2026/09/02/coding-agents-050-four-new-harnesses, https://github.com/memorax-ai/memorax-code

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Show HN: An autonomous AI agent running one project for two months in public | 3 | 2 | "Sad and yet so funny at the same time" — Marvin-the-Paranoid-Android vibes | https://news.ycombinator.com/item?id=49383353 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | arXiv:2608.28642 (MAGG) | https://arxiv.org/abs/2608.28642 | Multi-agent governed KG; +47% F1; +9.0 EM vs MS GraphRAG |
| 🌐 | metaphacts (6.0) | https://metaphacts.com/metaphactory | Unified semantic layer; VKG; AI co-author; no ETL |
| 🌐 | Digital Science/Ontopic | https://www.digital-science.com/press-releases/digital-science-acquires-ontopic/ | March 2026 VKG acquisition |
| 🌐 | Hindsight Cloud recap | https://hindsight.vectorize.io/blog/2026/09/01/hindsight-cloud-june-august-updates | SSO/MFA/audit; 33% cheaper Retain; Memory Defense Enterprise |
| 🌐 | Hindsight coding-agents 0.5.0 | https://hindsight.vectorize.io/blog/2026/09/02/coding-agents-050-four-new-harnesses | 16 agents total; pi/QwenCode/Dcode/opencode2 |
| 🌐 | Hindsight v0.9.2 | https://hindsight.vectorize.io/blog/2026/08/24/version-0-9-2 | Knowledge Base as MCP surface; temporal_window; Copilot provider |
| 🌐 | SEMANTiCS 2026 | https://www.digital-science.com/events/semantics-2026/ | Sep 15-17 Ghent; keynotes: Sequeda/Mileo/Garijo |
| 🌐 | Graphwise AI Summit | https://www.prnewswire.com/news-releases/unlock-trust-and-roi-graphwise-announces-free-virtual-summit-to-help-leaders-secure-real-value-from-enterprise-ai-302828574.html | Oct 7-8 free virtual; Roche/Accenture/AstraZeneca/S&P Global |
| 🌐 | Graphwise events | https://graphwise.ai/events/ | AI Summit + Semantic Layer Symposium Vienna Oct 14-15 |
| 🌐 | MemoraX Code | https://github.com/memorax-ai/memorax-code | @memorax/memorax-code; 1.2K stars; 4 memory types; 6 agents |
| 🌐 | KGC 2026 (Futia Medium) | https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5 | "failures are representation failures"; May 4-8 NYC |
| 🌐 | Graphwise AI (taxonomy advisor) | https://www.hpcwire.com/bigdatawire/this-just-in/graphwise-introduces-graphrag-platform-grounded-in-enterprise-knowledge-graphs/ | Taxonomy Advisor (LLM + human oversight) |
| 🌐 | Sourcegraph context engineering | https://sourcegraph.com/blog/context-engineering | "Prompt writing is a tiny fraction of the work" |
| 🌐 | Mnemoverse Q3 | https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3 | Mem0 94.4% LME = 73.8% under Maximem (−20.6pp gap) |
| 🌐 | Fountaincity (8 systems) | https://fountaincity.tech/resources/blog/agent-memory-knowledge-systems-compared/ | 2026 consensus: hybrid vector+KG |
| 🌐 | FeatherDB landscape | https://www.getfeather.store/theory/ai-agent-memory-frameworks-landscape-2026 | 2026 AI agent memory framework landscape |
| 🌐 | DevGenius comparison | https://blog.devgenius.io/ai-agent-memory-systems-in-2026-mem0-zep-hindsight-memvid-and-everything-in-between-compared-96e35b818da8 | Production comparison Mem0/Zep/Hindsight/Memvid |
| 🌐 | Mem0 state of memory | https://mem0.ai/blog/state-of-ai-agent-memory-2026 | 21 frameworks, 20 vector stores, 3 hosting models |
| 🌐 | Mem0 context engineering | https://mem0.ai/blog/context-engineering-ai-agents-guide | Meta Context Engineering: 89.1% SWE-bench |
| 🌐 | agentmemoryleaderboard.ai | https://agentmemoryleaderboard.ai/ | First cycle closed; second cycle opens Sep 20 |
| 🌐 | VoltAgent awesome papers | https://github.com/VoltAgent/awesome-ai-agent-papers | Curated 2026 agent research |
| 🌐 | KGC Knowledge Graph Training | https://www.knowledgegraph.tech/ | 9-week cohort opening Sep 2026 |
| 🌐 | IEEE ComSoc telecoms ontology | https://techblog.comsoc.org/2026/04/03/for-telecoms-will-2026-be-the-year-of-the-ai-ontology/ | 2026 year of AI ontology for telecoms |
| 🌐 | contextandchaos substack | https://contextandchaos.substack.com/p/ontologies-context-graphs-and-semantic | "semantic layer = lookup; ontology = context+reasoning" |
| 🌐 | NomadX (Zep/Graphiti) | https://nomadx.ae/blog/advanced-agent-memory-knowledge-graphs-zep-graphiti-2026/ | Bitemporal validity windows; production deployment |
| 🌐 | Codepointer (memory systems) | https://codepointer.substack.com/p/agent-memory-systems-and-knowledge | Letta/Mem0/Graphiti/Cognee analysis |
| 🌐 | Kenhuang substack | https://kenhuangus.substack.com/p/why-ontology-matters-for-agentic | Ontology as governable decision framework |
| 🌐 | Neo4j blog (semantic layer) | https://neo4j.com/blog/genai/the-payload-the-semantic-layer-memory-and-the-loop-that-fills-it/ | Semantic layer + memory + fill loop |
| 🇯🇵 | Zenn/@knowledge_graph | https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design | Entity resolution as first-class problem; incremental KG design |
| 🇯🇵 | note.com/@_kihonushi | https://note.com/_kihonushi/n/nad1b98d60300 | Semantic Layer vs Ontology; 60% failure without SL first; 40% agentic AI ceases by 2027 |
| 🇯🇵 | Qiita/@yohei1126 | https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80 | KG for multi-hop traversal; why vectors and RDB+SL fail |
| 🇯🇵 | Zenn/aws_japan (COA) | https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy | 53% answer variance without ontology; 100% AI-inferred FK |
| 🇯🇵 | Qiita/@yushibats | https://qiita.com/yushibats/items/d4e3e0186f4d8eb83874 | Ontology+KG+Semantic Layer = Context Layer for AI |
| 🇯🇵 | ai-souken.com (semantic layer) | https://www.ai-souken.com/article/what-is-semantic-layer | Semantic layer as foundation for correct LLM numbers |
| 🇨🇳 | InfoQ (MemOS/记忆张量) | https://www.infoq.cn/article/AIVoC9eKfZhW199IQkwB | MemOS: proactive scheduling + Memory Cube + Chain of Memory |
| 🇨🇳 | 53AI (OpenKG review) | https://www.53ai.com/news/knowledgegraph/2026022019635.html | OneGraph/SPG+KAG/SkillNet/OneEval; Claude 4.5 at 37.65% dynamic eval |
| 🇨🇳 | Tencent Cloud (era framing) | https://cloud.tencent.com/developer/article/2665379 | Model→Agent→Cognitive era transition |
| 🇨🇳 | CSDN (memory evolution) | https://agent.csdn.net/6a2a6b08662f9a54cb7d0dd2.html | Three generations: vector→structured→memory-as-infrastructure |
| 🇨🇳 | Zhihu (PKU/Fudan/NUS) | https://zhuanlan.zhihu.com/p/1986213905320661415 | Joint survey: KG taking over from pure vector DB |
| 🇨🇳 | 53AI (Ontology+KG) | https://www.53ai.com/news/knowledgegraph/2026011004136.html | Ontology + Data = KG; LLM generates TBox; human validates ABox |
| 🇨🇳 | AI-Insight.org | https://www.ai-insight.org/reports/agent-memory | MemGPT→A-MEM evolution; four-layer memory architecture |

---

## Stats Block

```
├─ 🟠 Reddit: 0 (excluded per instructions)
├─ 🔵 X/Twitter: 0 (excluded per instructions)
├─ 🔴 YouTube: 0 (not searched)
├─ 🟢 HN: 1 thread │ 3 pts │ 2 comments
├─ 🟣 TikTok: 0 (not searched)
├─ 🩷 Instagram: 0 (not searched)
├─ 🦋 Bluesky: 0 posts │ 0 likes (backend OK; no topical posts surfaced)
├─ 📊 Polymarket: 0
├─ 🌐 Web: ~38 pages │ 🇯🇵 7 │ 🇨🇳 7
└─ 🗣️ Top voices: Li Zhiyu/记忆张量, Giuseppe Futia/KGC, @knowledge_graph/Zenn, @_kihonushi/note.com │ Hindsight/Vectorize team
```

---

## Out of Scope but Notable

- **Cognee September 2026 update:** ontology resolver with matching strategies + time-graph options; DuckDB vector adapter; graph embeddings (paid); weighted nodes/edges for recency/importance. Technically in-scope (Cognee is an agent memory system), but the release was a "Launch Month" and the changelog reflects incremental rather than paradigm-shifting changes; filed here to flag completeness. URL: https://www.cognee.ai/changelog

- **KGC Knowledge Graph Training Program (Sep 2026 cohort):** 9-week, 20-seat capped live cohort on full-stack KG implementation for agentic memory. Could be its own thread (education/certification category). URL: https://www.knowledgegraph.tech/

- **MemOS Memory Marketplace vision** (记忆张量): planned mid-2025, enabling packaged domain knowledge as installable memory assets — analogous to an app store but for domain memory. If it ships, it would be a significant new distribution model for knowledge representation that doesn't fit today's KG/ontology categories cleanly.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for JP/CN passes (same as Sep 1 run); switched to native-language WebSearch — no hub content blocked, just slightly different reach
- **Bluesky:** backend OK; no topical posts surfaced
- **YouTube:** not searched; likely tutorial content on metaphactory 6.0, Hindsight 0.5.0, COA
- **TikTok/Instagram/Reddit:** excluded per instructions
- **HN engagement:** only 1 thread with very low points (3); most active HN threads from this topic are from prior weeks
- **Databricks Context Engineer beta results:** expected mid-September — not yet available
- **AML second cycle results:** cycle opens Sep 20, 2026 — not yet available
- **SEMANTiCS 2026 proceedings:** conference not yet started (Sep 15-17); no papers available yet
- **EKAW 2026 full program:** conference Sep 29-Oct 1; papers listed but full program not yet published
- **MemoraX Code star count/release date:** confirmed 1.2K stars but exact launch date not found
- **Coverage estimate:** ~80% — major new items captured (MAGG, metaphactory 6.0/Ontopic, Hindsight updates, SEMANTiCS, MemoraX Code, JP/CN hub perspectives); gaps in YouTube, Bluesky, conference proceedings

---

## Key Quotes

> "Most production failures attributed to model limitations or prompt engineering are actually representation failures. Once you encode the right structure — supersession, identity, version chains — the LLM stops needing to be a wizard." — Notes from KGC 2026 ([link](https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5))

> "A semantic layer tells you what your revenue is. An ontology tells you what a customer is." — note.com/@_kihonushi, Semantic Layer vs Ontology design guide ([link](https://note.com/_kihonushi/n/nad1b98d60300))

> "Even with excellent schema design, entity resolution degrades when source data shows naming inconsistencies like 'Acme', 'acme', 'ACME'." (「スキーマが良くても、ソースデータが「Acme」「acme」「ACME」と揺れていれば名寄せの精度は落ちます」) — Zenn/@knowledge_graph ([link](https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design))

> "間違えるより黙る" ("Better to stay silent than err") — Zenn/aws_japan, AWS COA deployment experience ([link](https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy))

> "最恰当的时刻，把最匹配的记忆放到最恰当的位置" ("At the optimal moment, place the most matching memory in the optimal location") — Li Zhiyu, 记忆张量 CTO, MemOS framework on InfoQ ([link](https://www.infoq.cn/article/AIVoC9eKfZhW199IQkwB))

> "Synthetic data no longer means low quality." (「合成数据不再是'低质'代名词」) — OpenKG OneGraph, 2025-2026 Annual Review ([link](https://www.53ai.com/news/knowledgegraph/2026022019635.html))

> "模型决定上限，应用夯实下限" ("Models determine ceiling, applications establish floor") — Li Zhiyu, InfoQ ([link](https://www.infoq.cn/article/AIVoC9eKfZhW199IQkwB))

> "Knowledge graphs are no longer databases — they're the memory layer for AI agents." — Konrad Kaliciński, Medium ([link](https://akkonrad.medium.com/knowledge-graphs-arent-databases-anymore-they-re-the-memory-layer-for-ai-agents-d090c03eb58c))
