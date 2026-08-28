# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-08-28
**Query type:** GENERAL
**Sources:** WebSearch (English, Japanese, Chinese), WebFetch (Hatena/Zenn/163.com/Manila Times/Databricks/Apache Ossie), Hacker News, GitHub releases, arXiv

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 2 threads | 85 pts, 50 comments (OzBrain) | 🌐 OzBrain Show HN Aug 21; mcp-memory ongoing |
| Web (global) | 55 pages | — | 🌐 via WebSearch + WebFetch; blogs, news, GitHub, arXiv |
| Web (Japan) | 7 pages | — | 🇯🇵 Zenn, Hatena, Qiita, CodeZine, note |
| Web (China) | 14 pages | — | 🇨🇳 36Kr, Zhihu, 163.com, Tencent News, CSDN, Juejin, 53AI, AIBase |
| Bluesky | 0 posts | — | 🌐 Backend OK; no topical posts surfaced |
| YouTube | 0 | — | Not searched this run |
| Reddit | 0 | — | Excluded per instructions |
| X/Twitter | 0 | — | Excluded per instructions |

---

## Synthesized Findings

### 1. [update] MemoraX AI: AML #1 + Seed++ + Huawei Cloud Strategic Partnership

🇨🇳 **Claim:** MemoraX AI ranked #1 on inaugural Agent Memory Leaderboard (AML) commercial text track (Aug 17), scored 58.02 across all 7 capability dimensions; also completed Seed++ (hundreds of millions RMB) on Aug 12, 2026.
- **What's new since Aug 21:** AML announced Aug 17 (leaderboard launched July 29 by 30+ institutions including Oxford/Tsinghua/PKU); 136 teams; 200K+ website clicks; HuggingFace weekly trending top 3
- **AML score breakdown:**
  - Overall: 58.02 (commercial text #1)
  - LoCoMo-Refined: 82.65 (30% ahead of #2)
  - ScriptMem: 60.3% accuracy (40% ahead)
  - SWE-context-bench: 45% task resolution (50% ahead)
  - Multimodal: #1 on Mem-Gallery + ATM-Bench (30% token reduction)
- **Competitors beaten:** Mem0 (#2, significant gap), Vectorize, Supermemory; Tencent (NTES-MEMORY-SMART), NetEase APIs
- **Technology (Gen 3 "native memory"):** learnable memory policy engine (RL) + specialized memory foundation models (long-context + temporal) + self-evolving Agent Harness; end-to-end RL trained — model independently manages write/compress/forget/retrieve
- **Funding:** April (seed/tens of millions USD) → May (seed+/tens of millions RMB) → Aug 12 (seed++/hundreds of millions RMB) — 3 rounds in ~4 months; 100M+ CNY cumulative
- **Strategic:** Huawei Cloud sole LTM-focused strategic partner in HW Cloud ecosystem
- **Research:** 10 papers at ICML 2026; Chinese Institute of Electronics Natural Science First Prize
- **Founder:** Hao Jianye — ex-Huawei Noah's Ark Lab, Decision Reasoning Lab, LLM Algorithm Lab director
- **Sources:** https://www.globenewswire.com/news-release/2026/08/17/3346129/0/en/memorax-ai-ranks-1-on-agent-memory-leaderboard-signaling-a-new-phase-for-long-term-ai-memory.html, https://www.manilatimes.net/2026/08/17/tmt-newswire/globenewswire/memorax-ai-ranks-1-on-agent-memory-leaderboard-signaling-a-new-phase-for-long-term-ai-memory/2406858, https://news.qq.com/rain/a/20260812A04HY300, https://www.163.com/dy/article/L4KD1QQR05119734.html, https://www.aibase.com/news/28163, https://github.com/AML-memory/agent-memory-leaderboard, https://agentmemorybenchmark.ai/, https://memorax.net/

---

### 2. [new] Palantir SuperRepo Beta: Ontology-as-Code in TypeScript

🌐 **Claim:** Palantir launched SuperRepo in beta (week of Aug 3, 2026) — a monorepo that combines Ontology definitions, Functions, and React apps into a single versioned artifact, enabling ontology-as-code via TypeScript.
- **Architecture:** declare object types, links, interfaces, actions in TypeScript; Foundry CLI runs locally; single edit-and-preview cycle across Ontology + function + frontend
- **Deployment:** compiles to Marketplace product (self-contained, cryptographically signed bundle); supports Palantir CI or GitHub Actions/CircleCI
- **Significance:** first pro-code path to evolve the Palantir Ontology without separate "publish ontology" steps; unifies software engineering workflow with ontology management
- **Status:** Beta; not available on all enrollments
- **Sources:** https://www.palantir.com/docs/foundry/announcements/2026-08, https://www.palantir.com/docs/foundry/superrepo/overview, https://releasebot.io/updates/palantir

---

### 3. [new] OzBrain: Shared Cross-Agent Knowledge Layer on Show HN

🌐 **Claim:** OzBrain (Show HN Aug 21, 2026, HN:49394827, 85pts/50 comments) — shared structured knowledge store that Claude, ChatGPT, Cursor, and coding agents all read and write via MCP.
- **Architecture:** structured articles with provenance, freshness, links; staged writes, routing, conflict detection, audit logs; MCP connectors
- **Problem solved:** AI knowledge fragmentation — each tool maintains separate memory; OzBrain creates single provenance-tracked shared layer
- **Team knowledge use case:** record where an answer came from + whether it still needs checking; AI-generated knowledge accumulates faster than orgs can organize or trust it
- **Sources:** https://news.ycombinator.com/item?id=49394827, https://ozbrain.com/, https://enterprisedna.co/resources/ai-pulse/ai-pulse-2026-08-23-a-shared-cross-agent-memory-layer-launches-on-show-hn/

---

### 4. [new] Onton Ontology 1: Neurosymbolic Search for Agentic Commerce Trust

🌐 **Claim:** Onton released Ontology 1 (July 29/Aug 2, 2026), a neurosymbolic model that beats Google Shopping and Amazon on product search accuracy while indexing ~1% of their catalogs.
- **Benchmark (Subtext-Decor-90, 90 queries, 3 independent LLM judges):** Onton P@10 0.630 vs Google Shopping 0.543 vs Amazon 0.469; wins 52/90 queries outright
- **Novel framing:** trust and authenticity model for the agentic web — judges veracity of product information, not just what a product is; designed for AI shopping agents making purchasing decisions on behalf of users
- **Capabilities:** combined text+image search; reads intent behind stated preferences; multimodal
- **Sources:** https://www.globenewswire.com/news-release/2026/07/29/3335254/0/en/onton-debuts-groundbreaking-ai-model-for-trustworthy-product-discovery.html, https://www.marktechpost.com/2026/08/02/onton-releases-ontology-1-a-neurosymbolic-search-model/, https://onton.com/research/ontology-1

---

### 5. [new] Neo4j meta-knowledge-graph: Self-Improving Harness-Agnostic Agent Memory

🌐 **Claim:** neo4j-labs/meta-knowledge-graph (new GitHub repo) — lifecycle hooks + LLM extraction loop that distills durable learnings from every session and evolves the agent's system prompt, running on Claude Code and Codex today.
- **Architecture:** lifecycle hooks capture every session → MCP tools recall project memory → LLM extraction loop distills learnings → evolves agent system prompt
- **Hooks write to same graph MCP tools read from:** each new session starts with most relevant prior learnings injected
- **Requirements:** Neo4j 2026.02+ (SEARCH clause / filtered vector search)
- **Status:** running on Claude Code + Codex; other harnesses planned
- **Sources:** https://github.com/neo4j-labs/meta-knowledge-graph

---

### 6. [new] Acro Engineering Benchmark: OKF 100% Coverage vs GraphRAG's 78.9% at 1/26th Token Cost

🇯🇵 **Claim:** Acroquest Technology (Aug 25, 2026, Hatena Blog) ran head-to-head benchmark of GraphRAG vs OKF-style knowledge management on 285 Wikipedia DB articles (~740K characters); OKF wins on all metrics except raw automation.
- **Results:**
  | Metric | GraphRAG | OKF |
  |--------|----------|-----|
  | Pages Generated | 13,683 | 285 |
  | Concept Coverage | 78.9% | 100% |
  | Relationship Accuracy | 16.9% | 43.9% |
  | Concept Fragmentation | 65 entity splits | 0 |
  | Token Consumption | ~32.5M | ~1.25M (1/26th) |
  - MS-GraphRAG: ~370× more tokens than standard RAG at query time
- **Root cause of GraphRAG failure:** label proliferation + entity resolution failures (same concept across multiple nodes: "MSDE", "MS SQL", "SQL SERVER")
- **OKF advantage:** pre-existing system structure as concept identifiers → zero fragmentation
- **Recommendation:** GraphRAG only for multi-hop queries; OKF for structured knowledge with existing foundations
- **Remaining challenges:** organizational definition management, update maintenance costs, absent ROI standards
- **EN translation of key quote:** "GraphRAG's automatic extraction produces label proliferation and entity resolution failures... OKF's approach eliminated fragmentation entirely"
- **(「GraphRAGの自動抽出はラベルの増殖とエンティティ解決の失敗を引き起こします...OKFのアプローチはフラグメンテーションを完全に排除しました」)**
- **Source:** https://acro-engineer.hatenablog.com/entry/2026/08/25/120000

---

### 7. [update] Apache Ossie: Kyvos Joins, 50+ Members, Native Import/Export Not Yet Shipped

🌐 **Claim:** Apache Ossie added Kyvos as member on Aug 12, 2026 (50+ total organizations), and Databricks is now a member; 4 semantic layer tools have OSI converters but none yet ship native import/export (expected by year end).
- **Kyvos's contribution:** enterprise-speed semantic layer; governed business context for AI agents at scale
- **Kyvos COO Rajesh Murthy:** "Enterprise AI needs two things from the data foundation: the right context and the ability to access enterprise data at the speed of enterprise"
- **Ossie state:** Specification live at open-semantic-interchange.org under Apache 2.0; Financial Services WG active; 4 converter tools exist; no native product import/export yet
- **Prior state (Jul 10):** entered Apache incubator with 50+ orgs; Databricks joined (notable given LTAP)
- **Sources:** https://www.prnewswire.com/news-releases/kyvos-joins-apache-ossie-ecosystem-bringing-speed-and-context-to-enterprise-ai-302849755.html, https://ossie.apache.org/updates/, https://github.com/apache/ossie, https://open-semantic-interchange.org/updates/

---

### 8. [update] Hindsight v0.9.0 + DeepSeek Harness Integration; SDE-bench Results Public

🌐 **Claim:** Hindsight added DeepSeek Harness (dsh) support on Aug 14, 2026 (dsh open-sourced same day); SDE-bench dataset now public on GitHub + Hugging Face; results land at agentmemorybenchmark.ai.
- **DeepSeek Harness:** coding agent on Cordis plugin framework, open-sourced Aug 14, 2026; previously amnesiac between sessions
- **Hindsight+dsh integration:** one command install (`npx @vectorize-io/hindsight-coding-agents install dsh`); native Cordis plugin (no MCP server to run); fully automatic memory (git history + conversations); builds+reads Knowledge Pages (self-healing wiki of architecture/conventions)
- **Knowledge Pages clarification:** projected view over processed memory (not raw files); like a database view over the underlying memory bank; hierarchical filesystem interface
- **SDE-bench public:** github.com/vectorize-io/sde-bench (load_dataset()-ready on HuggingFace); confirms 57% fewer corrections (Claude Code), 65% (Codex CLI)
- **Now 10 coding agents covered:** Claude Code, Codex CLI, Cursor CLI, opencode, GitHub Copilot CLI, Cline, Kilo, Grok Build, Antigravity, Devin, plus new dsh
- **Sources:** https://hindsight.vectorize.io/blog/2026/08/14/deepseek-harness-persistent-memory, https://hindsight.vectorize.io/blog/2026/08/06/hindsight-0-9-0, https://github.com/vectorize-io/hindsight, https://agentmemorybenchmark.ai/

---

### 9. [update] Cognee v1.5.0 (Aug 15, 2026): Migration Reliability + Dataset Overview Index

🌐 **Claim:** Cognee released v1.5.0 on Aug 15, 2026, with large-scale migration reliability fixes, Ladybug adapter speedup, and new optional dataset overview index for broader search context.
- **Ladybug adapter:** set-based fork re-key, chunked queries, batched rekey/restore, migration reliability+speed
- **Dataset overview index:** topical clustering for broader context during search; improves relevance without restructuring
- **v1.5.0.dev5 (Aug 20):** further community plugin documentation + LLM tuning options
- **Prior:** Neptune integration, n8n Cloud, self-improving graph, graph embeddings, Berkeley Xcelerator (Jul 13)
- **Sources:** https://www.cognee.ai/changelog, https://github.com/topoteretes/cognee/releases

---

### 10. [update] Databricks Genie Ontology: Snippets to ALL Customers (Aug 13); Genie Code as Lakeflow Job

🌐 **Claim:** Databricks Genie Ontology snippets became available to ALL customers Aug 13 (previously required account team request); new: Genie Code runs as Lakeflow Job task.
- **Aug 6:** Genie Ontology enabled by default (Public Preview) — "unified context layer giving Genie a business-aware map of your organization"
- **Aug 13:** Ontology snippets to all customers — no access request required
- **New Aug 2026:** Genie Code runs prompts autonomously as Lakeflow Job task; reads upstream task outputs; calls tools; returns Genie Code conversation link
- **Free usage:** extended through Jan 31, 2027 (previously ending Jul 31, 2026)
- **Sources:** https://docs.databricks.com/aws/en/ai-bi/release-notes/2026, https://www.databricks.com/blog/introducing-genie-one-genie-ontology-and-genie-agents, https://datapao.com/genie-ontology-explained/

---

### 11. [update] Mem0 Editor Plugin v0.2.11: Auto-Context Injection; Tripled Free Tier

🌐 **Claim:** Mem0 editor plugin v0.2.11 adds automatic context injection on file reads/bash errors/session resume, project+global memory scopes, background coding taxonomy (17 categories), and Antigravity support.
- **Key changes:** auto-capture + compaction summaries + session summaries; project-scoped memories as default; global_search for team-wide recall; Claude Code/Cursor/Codex/Antigravity telemetry separately tracked
- **Free tier:** tripled limits July 2026
- **State of AI Memory 2026 report:** 186M quarterly API calls; 61K+ GitHub stars
- **Sources:** https://releasebot.io/updates/mem0, https://docs.mem0.ai/changelog/highlights, https://github.com/mem0ai/mem0

---

**Still true** (ongoing threads, no new fact this run):

- *semantica-graph-native-provenance* — v0.6.0 Jul 21, 2026; 3,435 stars; MIT; MCP server; no Aug release
- *starling-universal-cognitive-architecture* — UCA open standard (CC-free); Starling MX beta $99/mo; no update
- *neo4j-labs-agent-memory-nams* — v0.5.0 NAMS; POLE+O ontology; ontology import/diff/migrate unreleased
- *ontocast-ontology-assisted-kg* — v0.3.0 Mar 10; Apache-2.0; GrowGraph; no update
- *memtools-interoperable-framework* — arXiv:2607.21404; CAS/BAAI; unified declarative contracts
- *graph-native-bitemporal-neo4j* — arXiv:2607.26520; Neo4j+HNSW; 80% R@10
- *memtool-dynamic-tool-context* — arXiv:2507.21428; ECIR 2026; 90-94% tool-removal efficiency
- *hn-openknowledge-ai-notes* — HN:48675435; 381pts/173 comments; AI-first Obsidian alt
- *jp-qiita-ontology-department-alignment* — Qiita/@M_Ozu Aug 13; departments get different numbers = missing ontology
- *aws-context-ontology-accelerator* — GA Jul 31; OWL 2+HermiT; Neptune+OpenSearch+Bedrock; months→days
- *hindsight-v090-knowledge-pages* — covered as update above (#8)
- *crystalmem-elastic-memory* — arXiv:2608.00303; 4-fidelity crystallization; 50% memory budget match
- *shared-org-memory-coding-agents* — arXiv:2608.00122; production enterprise Q&A memory DSLs
- *mcp-memory-okf-sqlite* — HN:49286073; OKF v0.2-backed MCP server; SQLite FTS5; 5 MCP tools
- *tencentdb-agent-memory-v2* — v2.0 Aug 3; 4 assets; governance layer; PersonaMem 48%→76%
- *coevokg-self-evolving-search* — arXiv:2608.01904; KG+RL; +11.2pp on 6 QA benchmarks
- *benchmark-vendor-inflation-measured* — Mnemoverse Q3: Mem0 94.4% LME = 73.8% Maximem harness (−20.6pp)
- *mragent-reconstructed-memory* — arXiv:2606.06036; ICLR 2026; Cue–Tag–Content graph; active reconstruction
- *magma-multi-graph-memory* — arXiv:2601.03236; 4-graph decoupled; LoCoMo 0.7 best early 2026
- *hage-rl-graph-evolution* — arXiv:2605.09942; RL-driven weighted graph evolution
- *mage-multi-agent-coevolving-kg* — arXiv:2605.10064; UNSW; 4-subgraph co-evolutionary KG
- *bosun-memory-graph-cleaner* — HN:48493954; LoRA fine-tune Qwen3-Reranker; WarrantBench
- *hyphaedb-living-topology* — arXiv:2606.28781; gossip-protocol vector topology; energy-based attenuation
- *cloudflare-agent-memory-beta* — Apr 17; 5-channel parallel retrieval; RRF+HyDE; Workers+Durable Objects
- *mnemoverse-hebbian-memory* — Hebbian+Rescorla-Wagner; 6 MCP tools; one memory across all major editors
- *gene-ontology-kb-2026* — NAR 2026; 768 new terms; Functionome v2.0; AI-assisted curation standard
- *neo4j-constant-cost-semantic-memory* — Neo4j blog Aug 4; semvec; constant token cost per turn
- *memgraphrag-kdd-2026* — KDD 2026; arXiv:2606.00610; 59.25% avg accuracy; 0.061s retrieval
- *sap-knowledge-graph-autonomous-enterprise* — Sapphire 2026 May; 452K tables, 7.3M fields; Joule Assistants
- *experience-graphs-trellis-meta* — arXiv:2606.29823; Meta; 10× speedup, 52% lower token cost
- *hindsight-memory-benchmark-leader* — benchmark leader; SDE-bench now public (see #8 update)
- *longmemeval-v2-web-agent-experience* — arXiv:2605.12493; 451 questions; 115M token trajectories
- *stardog-bedrock-agentcore-semantic-layer* — AWS Blog Jul 10; SPARQL or MCP Gateway
- *ai-km-6-6-1-agentic-ontology-tooling* — ScienceDirect SoftwareX Jul 2026; agentic skill framework
- *reagan-node-as-agent-graph* — arXiv:2508.00429; Rutgers; each node is an agent
- *databricks-context-engineer-cert* — GA Jul 29; beta results expected mid-Sep 2026; $200/120min
- *mandol-agglomerative-memory* — arXiv:2606.29778; CAS+MSFT; 92.21%/88.40% LoCoMo/LME SOTA
- *toki-bitemporal-contradiction-algebra* — arXiv:2606.06240; 3 write anomalies; 4 soundness theorems
- *agent-native-memory-readiness-survey* — arXiv:2606.24775; CAS/Tsinghua; 12 memory systems
- *oracle-ai-agent-memory-26-6* — 93.8% LME; BEAM 0.680; 10.7× token reduction
- *redis-context-engine* — GA May 18; 3-component MCP-native context layer
- *evermind-everos-self-evolving* — v1.1.1; HyperMem hypergraph; mRAG multimodal; 93%+ retrieval
- *moss-auditable-relational-memory* — arXiv:2607.04391; SQL retrieval; 569 concepts; 44M-token deployment
- *sage-graph-self-evolving-engine* — arXiv:2605.12061; reader-writer feedback loop; 82.5/91.6 NQ Recall
- *kgermar-dynamic-kg-inference* — arXiv:2606.14047; 3 memory banks; 8.5% lower perplexity
- *mcp-spec-2026-07-28-rc* — stateless HTTP core; Extensions+Tasks+MCP Apps; auth hardening
- *selfmem-beam-sota-july-2026* — arXiv:2607.03726; KAUST; best BEAM at 100K/500K/1M scales
- *automem-cognitive-skill* — arXiv:2607.01224; KAUST; 2–4× improvement long-horizon games
- *self-gc-context-lifecycle* — arXiv:2607.00692; 43.95% token pruning; 91-95% no-impact
- *memrefine-budget-compression* — arXiv:2606.13177; LLM-guided factual budgeted compression
- *minio-aistor-memory* — Jul 29; enterprise unified memory (object+vector+secrets); 77% Fortune 100
- *skan-aow-v1-agent-ontology* — Feb 10; 8 canonical entities; integrated O2A Platform
- *agentic-context-management-lifecycle* — arXiv:2607.21503; 5 primitives; Maximem Synap 92% LME
- *context-files-no-measurable-impact* — arXiv:2607.27250; 288 runs; context files ≤10-15pp impact
- *mem0-openmemory-mcp-local* — Jul 23/31; local Docker; 4 MCP tools; Chrome extension
- *smoothagent-lookahead-context* — arXiv:2607.00151; 11.9× TTFT reduction
- *memguard-role-typed-memory* — arXiv:2605.28009; +28.27% reliability; 5.8× fewer tokens
- *neo4j-thin-agents-graphsummit* — TWIN4J; ZS Associates case study; 'formal ontology as logical guardrail outside the model'
- *less-context-better-agents* — arXiv:2606.10209; last-5 pruning → 91.6% vs 71% full history
- *context-graphs-proactive-enterprise* — arXiv:2607.07721; Delta Detection Engine; 47min→30s insight surface
- *exabase-m1-beam-sota* — Jul 28; 76.9/75.0/68.0% BEAM; 96.4% LME; Gemini 3 Flash 4-6× cheaper
- *okf-v02-provenance-trust* — Jul 25; provenance+trust tiers; Google reference impls; WitsCode validator/okf-graph.mjs; early-practitioner adoption
- *memanto-typed-semantic-memory* — arXiv:2604.22085; 13 types; <90ms; 89.8% LME / 87.1% LoCoMo
- *plugmem-icml-2026-microsoft* — arXiv:2603.03296; task-agnostic KG; outperforms task-specific across 3 benchmark classes
- *t-mem-anticipatory-retrieval* — arXiv:2606.15405; anticipatory retrieval; 'associative' vs 'descriptive' recall
- *neuro-symbolic-tkg-meta-policy* — arXiv:2607.18368; step-level traceability; best PORL
- *netflix-e2e-kg-shared-ontology* — QCon London 2026; shared ontology across AutoSRE agents
- *iso-23726-3-fdis* — FDIS Jun 3 2026; OWL DL for industrial automation; nearing full ISO publication
- *allegrograph-85-neuro-symbolic* — Mar 17 2026; KG+vector+neuro-symbolic; expanded MCP support
- *memgraph-atomic-graphrag* — Feb 2026; Atomic GraphRAG as single Cypher query; 10x code reduction
- *surrealdb-3-unified-agent-memory* — $44M; 8 data models; Spectron context layer; Verizon/Tencent/Samsung Ads
- *architecture-beats-model-scale* — convergence: memory/retrieval architecture quality > model scale
- *engram-bi-temporal-memory-engine* — arXiv:2606.09900; 83.6% LME_S vs 73.2% full-context at 8× fewer tokens
- *sage-write-side-novelty-gate* — arXiv:2605.30711; vMF gate; 3.4× API cost reduction vs Mem0
- *tokenpilot-cache-efficient-context* — arXiv:2606.17016; dual-granularity; 61-87% context cost reduction
- *agenticts-bounded-memory-testbed* — arXiv:2607.02255; 5 per-decision slots; 298-trajectory Slay the Spire 2
- *mempalace-zero-api-spatial-memory* — 56K GitHub stars; 96.6% Recall@5; 170-token startup; spatial KG
- *ontology-dilution-problem* — Year of the Graph Vol.31; 'ontology' escaped technical meaning into marketing
- *selective-ontology-injection-best-practice* — selective confidence-aware injection > always-on; full ontological context displaces parametric knowledge
- *ontology-guardrails-framing* — ontology as correctness guardrail; Jul 30 Latent Space; Emil Eifrem; 36-46% multi-hop gains
- *cn-llms-reshape-ontology-engineering* — CSDN; LLMs shifting from static rule-driven to dynamic generative; TBox by LLM, ABox by human
- *jp-layered-implementation-path* — Semantic Layer (2-6mo) → Lightweight Ontology → MCP; 40% projects to fail by 2027 (Gartner)
- *okf-v01-structural-interoperability* — OKF v0.1 Jun 18 2026; structural not semantic interop; v0.2 Jul 25 adds trust/provenance
- *memory-agent-bench-four-competencies* — ICLR 2026; 4-competency framework; all current methods fall short
- *letta-pro-cloud-tier* — August 2026 SDK; MemFS+dreaming; mods; Slack/Telegram; $20/mo Pro; Letta Code #1 Terminal-Bench
- *zep-ce-retired-graphiti-open-source* — v0.29.3 Jul 27; saga abstraction; FalkorDB fixes; MCP 1.0; 63.8% LME GPT-4o
- *memora-microsoft-icml-2026* — 98% token reduction; 86.3% LoCoMo; 87.4% LME; highest on benchmarks
- *fabric-iq-ontology-mcp* — Microsoft Fabric IQ Ontology; public MCP endpoints (Preview)
- *mcp-ontology-integration-protocol* — MCP 2026-07-28 final; all hyperscalers aligned; all major ontology tools MCP-native
- *ontology-as-reliability-infrastructure* — English/JP/CN communities independently frame ontology as correctness/reliability layer
- *benchmark-proliferation-memory* — 6+ active benchmarks; rankings not portable; Aug 17 AML adds #7 independent leaderboard
- *evomembench-no-single-memory-form* — arXiv:2605.18421; no single form consistently works; 15-system study
- *napmem-active-memory-navigation-rl* — arXiv:2607.05794; RL-based active memory navigation
- *placemem-compute-aware-memory-plane* — arXiv:2607.04089; versioned capsules for cross-agent memory sharing
- *agento-owl-rdf-agentic-ontology* — ESWC 2026; OWL/RDF for agentic workflows; 66 workflows
- *always-on-agents-survey* — arXiv:2606.30306; 435 papers; AOEP-v0 protocol
- *ontobricks-open-ontologies-mcp* — Rust MCP server; Oxigraph+OWL2-DL+SHACL+SPARQL; no JVM
- *eticas-ai-risk-taxonomy-v2* — arXiv:2607.02201; SKOS/JSON-LD; 76 subcategories; 18 framework mappings
- *hn-5-mistakes-kg-memory* — HN:48337689; POLE+O practitioner baseline; schema decides everything
- *neo4j-pole-o-hallucination-reduction* — 36-46% multi-hop gains; 40%+ hallucination reduction vs vector-only
- *memdelta-benchmark-nonportability* — arXiv:2606.29914; embedding model swaps flip rankings by 6.2pp
- *eywa-evidence-before-belief* — arXiv:2605.30771; provenance-grounded; evidence-before-belief SOTA
- *ember-budgeted-evidence-retention* — arXiv:2606.05894; 0.3017 F1; fixed-budget write-side control
- *projectmem-memory-as-governance* — Memory-as-Governance; 14 MCP tools; MIT
- *cn-ontology-strategic-return* — CN framing: 2026 KG strategic return as grounding layer; property graphs preferred over OWL/RDF; RAG→context engineering debate
- *tencent-tbox-abox-framing* — TBox (schema/LLM) + ABox (instances/human); two-stage epistemological process
- *ontology-interoperability-lifecycle-framework* — arXiv:2507.12311; ODPs → Ontology Matching/Versioning → Validation
- *trust-certificates-pre-deployment* — arXiv:2606.04037; pre-deployment certification using formal ontology-backed verification
- *vector-db-market-growth* — $3.2B (2025) → $8.95B (2030) at 27.5% CAGR; Turbopuffer $50M; Qdrant $50M Series B

---

## Cross-Source Patterns

**Pattern 1: AML Leaderboard as Market Arbiter (🌐 Web + 🇨🇳 CN)**
- AML (July 29, 2026) is the first independent open leaderboard for memory systems; 30+ institutions; 136 teams
- MemoraX (🇨🇳) takes commercial #1; Chinese startup beats Western incumbents (Mem0, Vectorize)
- Pattern: CN memory startups leveraging RL "endogenous" approach vs Western embedding/KG approaches; first time Chinese memory entrant tops independent international leaderboard
- Sources: AML GitHub, GlobeNewswire, 163.com, agentmemorybenchmark.ai

**Pattern 2: Ontology-as-Code / Ontology as Developer Workflow (🌐 Web + 🇯🇵 JP)**
- Palantir SuperRepo: TypeScript ontology declarations in monorepo
- OKF: markdown-file ontology bundles with validators and agent skills
- JP benchmark (Hatena Aug 25): OKF at 1/26th GraphRAG token cost + 100% concept coverage
- GraphRAG's automation ceiling visible: entity resolution fails at 78.9% concept coverage with 65 fragmentation events
- Pattern: structured human-curated knowledge outperforms automated graph extraction on all metrics except raw scale

**Pattern 3: Cross-Agent Shared Memory Layer (🌐 Web)**
- OzBrain: shared MCP knowledge store Claude+ChatGPT+Cursor+coding agents
- neo4j meta-knowledge-graph: harness-agnostic lifecycle hooks + MCP read/write
- Hindsight+dsh: now 10+ coding agents with unified memory interface
- Pattern: memory is moving from per-agent to shared organizational/team layer; MCP as interop mechanism

**Pattern 4: Gen 3 "Native/Endogenous" Memory vs Gen 1 RAG / Gen 2 KG (🌐 🇨🇳)**
- MemoraX, MemoraX-ReMix (ICLR 2026): end-to-end RL, model manages own memory lifecycle
- CN community explicitly labeling three generations; Gen 3 seen as paradigm shift
- AML leaderboard result validates Gen 3 performance at commercial scale
- Sources: MemoraX announcements, 163.com, 36Kr, CSDN

**Pattern 5: Benchmark Proliferation + Independent Leaderboard (🌐 All)**
- Now 7 major benchmarks: LoCoMo, LME, BEAM 1M/10M, SDE-bench, MemoryAgentBench, AML (new)
- AML adds institutional credibility (30+ universities); attacks vendor-inflation problem (Mnemoverse −20.6pp gap)
- JP/CN community covering AML as accountability mechanism for Chinese AI memory market
- Sources: AML, Mnemoverse, agentmemorybenchmark.ai, mem0 benchmarks blog

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Show HN: OzBrain, a shared brain for knowledge between agents and your team | 85 | 50 | "Businesses are accumulating AI-generated knowledge faster than they can organise or trust it" | https://news.ycombinator.com/item?id=49394827 |
| — | Show HN: MCP Memory – Fast Agent Memory Using Google's OKF and SQLite FTS5 | — | — | OKF v0.2 as persistent memory, not export format | https://news.ycombinator.com/item?id=49286073 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | GlobeNewswire (MemoraX AML) | https://www.globenewswire.com/news-release/2026/08/17/3346129/0/en/memorax-ai-ranks-1-on-agent-memory-leaderboard-signaling-a-new-phase-for-long-term-ai-memory.html | AML #1 announcement, 58.02, Seed++ |
| 🌐 | Palantir Foundry Announcements Aug 2026 | https://www.palantir.com/docs/foundry/announcements/2026-08 | SuperRepo Beta: ontology-as-code TypeScript |
| 🌐 | Palantir SuperRepo Overview | https://www.palantir.com/docs/foundry/superrepo/overview | Monorepo = Ontology + Functions + React |
| 🌐 | PRNewswire (Kyvos + Apache Ossie) | https://www.prnewswire.com/news-releases/kyvos-joins-apache-ossie-ecosystem-bringing-speed-and-context-to-enterprise-ai-302849755.html | Kyvos Aug 12 join; enterprise speed for semantic layer |
| 🌐 | Apache Ossie Updates | https://ossie.apache.org/updates/ | Aug 12 Kyvos; 50+ orgs; 4 converters; no native import/export |
| 🌐 | Onton Ontology 1 (GlobeNewswire) | https://www.globenewswire.com/news-release/2026/07/29/3335254/0/en/onton-debuts-groundbreaking-ai-model-for-trustworthy-product-discovery.html | Neurosymbolic; P@10 0.630 vs Google 0.543 vs Amazon 0.469 |
| 🌐 | MarkTechPost — Onton | https://www.marktechpost.com/2026/08/02/onton-releases-ontology-1-a-neurosymbolic-search-model/ | 2.7× more accurate than Google Shopping |
| 🌐 | Onton Research | https://onton.com/research/ontology-1 | Architecture details |
| 🌐 | Hindsight — DeepSeek Harness | https://hindsight.vectorize.io/blog/2026/08/14/deepseek-harness-persistent-memory | dsh + Knowledge Pages Aug 14 |
| 🌐 | Hindsight 0.9.0 | https://hindsight.vectorize.io/blog/2026/08/06/hindsight-0-9-0 | 10 coding agents unified; SDE-bench public |
| 🌐 | Neo4j meta-knowledge-graph | https://github.com/neo4j-labs/meta-knowledge-graph | Self-improving harness-agnostic agent memory |
| 🌐 | Databricks release notes | https://docs.databricks.com/aws/en/ai-bi/release-notes/2026 | Aug 6 default; Aug 13 all customers; Genie Code as Lakeflow |
| 🌐 | Mem0 ReleaseBot | https://releasebot.io/updates/mem0 | v0.2.11 auto-inject; 17-category taxonomy; tripled free tier |
| 🌐 | Cognee Changelog | https://www.cognee.ai/changelog | v1.5.0 Aug 15; Ladybug speed; dataset overview index |
| 🌐 | Letta Next Phase | https://www.letta.com/blog/our-next-phase/ | MemFS + dreaming + mods + $20/mo Pro |
| 🌐 | OKF v0.2 Google Cloud blog | https://cloud.google.com/blog/products/data-analytics/okf-v0-2-adds-trust-signals | Jul 25; provenance + trust tiers |
| 🌐 | OKF SPEC | https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md | Current canonical spec v0.2 |
| 🌐 | WitsCode OKF | https://witscode.com/open-knowledge-format | Validator + okf-graph.mjs visualization |
| 🌐 | openknowledgeformat.com | https://openknowledgeformat.com/ | Validator + computation contracts |
| 🌐 | AML GitHub | https://github.com/AML-memory/agent-memory-leaderboard | Open evaluation platform; 30+ institutions |
| 🌐 | AML leaderboard site | https://agentmemorybenchmark.ai/ | Commercial+academic tracks; SDE-bench results |
| 🌐 | Graphiti releases | https://github.com/getzep/graphiti/releases | v0.29.3 Jul 27; saga abstraction; MCP 1.0 |
| 🌐 | KGC 2026 Notes (Medium) | https://medium.com/@giuseppefutia/notes-from-kgc-2026-c9b4ac8569e5 | May 4-8; representation failures; production gap |
| 🌐 | OzBrain site | https://ozbrain.com/ | Shared brain; routing+conflict detection+audit |
| 🌐 | Enterprise DNA OzBrain | https://enterprisedna.co/resources/ai-pulse/ai-pulse-2026-08-23-a-shared-cross-agent-memory-layer-launches-on-show-hn/ | Show HN coverage Aug 23 |
| 🌐 | MemoraX AML Manila Times | https://www.manilatimes.net/2026/08/17/tmt-newswire/globenewswire/memorax-ai-ranks-1-on-agent-memory-leaderboard-signaling-a-new-phase-for-long-term-ai-memory/2406858 | Full AML score breakdown |
| 🌐 | Atlan agent interop protocols | https://atlan.com/know/agent-interoperability-protocols/ | MCP/A2A/OSI explained |
| 🌐 | Hackernoon memory lock-in | https://hackernoon.com/agent-memory-has-a-lock-in-problem-open-formats-are-how-we-fix-it | Lock-in problem; open formats |
| 🌐 | Hackernoon context graphs | https://hackernoon.com/context-graphs-ontologies-and-the-race-to-fix-enterprise-ai | Enterprise AI failing where semantics should live |
| 🌐 | Year of the Graph Vol 31 | https://yearofthegraph.xyz/newsletter/2026/06/layers-of-meaning-context-graphs-graph-memory-and-ontologies-for-ai-the-year-of-the-graph-newsletter-vol-31-summer-2026/ | 'Ontology' dilution; context graphs vs ontologies |
| 🌐 | Ken Huang Substack | https://kenhuangus.substack.com/p/why-ontology-matters-for-agentic | World models → governable decisions |
| 🌐 | Enterprise Knowledge | https://enterprise-knowledge.com/ontology-and-knowledge-graph-in-the-age-of-ai-and-agents/ | Formal ontology; KG as grounding layer |
| 🌐 | Mnemoverse Q3 benchmark | https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3 | Aug 6 update; vendor inflation −20.6pp confirmed |
| 🌐 | Latent Space Ontologies Are So Back | https://www.latent.space/p/ontologies-agentic-systems | Jul 30; semantic web revival; guardrails |
| 🌐 | Databricks Genie intro blog | https://www.databricks.com/blog/introducing-genie-one-genie-ontology-and-genie-agents | DAIS 2026; OntoRank; 84.5% first-attempt accuracy |
| 🌐 | Databricks Genie explained | https://datapao.com/genie-ontology-explained/ | Ontology = business-aware map |
| 🌐 | Open Semantic Interchange updates | https://open-semantic-interchange.org/updates/ | OSI spec live; Kyvos Aug 12 |
| 🌐 | Stardog/AWS Bedrock AgentCore | https://aws.amazon.com/blogs/machine-learning/build-a-semantic-layer-for-agentic-ai-on-aws-with-stardog-and-amazon-bedrock-agentcore/ | KG semantic layer + MCP; federated Aurora+Redshift |
| 🌐 | AWS AgentCore Web Search blog | https://aws.amazon.com/blogs/machine-learning/introducing-web-search-on-amazon-bedrock-agentcore/ | GA Jun 17; MCP-compatible; Amazon KG + semantic snippets |
| 🌐 | Mem0 State of AI Memory 2026 | https://mem0.ai/blog/state-of-ai-agent-memory-2026 | 186M quarterly API calls; 61K+ stars |
| 🌐 | Hindsight benchmarks | https://benchmarks.hindsight.vectorize.io/ | 94.6% LME, 92% LoCoMo; SDE-bench confirmed |
| 🌐 | Graphiti Neo4j blog | https://neo4j.com/blog/developer/graphiti-knowledge-graph-memory/ | Graphiti = graph-native memory for agentic world |
| 🌐 | Atlan Genie Ontology guide | https://atlan.com/know/ai-agent/databricks/genie-ontology/ | OntoRank; Pages; snippets |
| 🌐 | Mnemoverse product | https://mnemoverse.com/ | Hebbian+Rescorla-Wagner; 6 MCP tools |
| 🌐 | Neo4j Labs Agent Memory | https://neo4j.com/labs/agent-memory/ | NAMS; POLE+O; 3-tier memory |
| 🌐 | Mem0 benchmarks blog | https://mem0.ai/blog/ai-memory-benchmarks-in-2026 | LoCoMo/LME/BEAM overview |
| 🌐 | Evermind blog | https://evermind.ai/blogs/top-ai-memory-systems-benchmarked-in-2026 | Top systems 2026 benchmarked |
| 🌐 | Letta context repositories | https://www.letta.com/blog/context-repositories/ | MemFS context repositories concept |
| 🌐 | Letta docs memory | https://docs.letta.com/letta-agent/memory | Dreaming = background subagent consolidation |
| 🌐 | FalkorDB Graphiti | https://www.falkordb.com/blog/building-temporal-knowledge-graphs-graphiti/ | Temporal KG; validity window per fact |
| 🌐 | arXiv:2601.10436 | https://arxiv.org/abs/2601.10436 | LLM-assisted ontological KB development |
| 🌐 | Atlan semantic layer guide | https://atlan.com/know/ai-agent/semantic-layer-for-ai-agents/ | Complete 2026 guide |
| 🌐 | Magemetrics semantic layer | https://www.magemetrics.com/blog/best-semantic-layer-tools-for-2026-open-source-to-enterprise | Self-configuring semantic layer; MCP server fall 2026 |
| 🇯🇵 | Hatena — Acro Engineering GraphRAG vs OKF | https://acro-engineer.hatenablog.com/entry/2026/08/25/120000 | Aug 25 benchmark; OKF 100% vs GraphRAG 78.9%; 1/26th token cost |
| 🇯🇵 | Zenn — KG Agent Ontology Design | https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design | Entity resolution at integration time, not inference time |
| 🇯🇵 | Qiita — AI Agent Next-Gen Data Foundation | https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80 | Why graphs for knowledge representation |
| 🇯🇵 | Qiita — Ontology/KG AI Terms | https://qiita.com/yushibats/items/d4e3e0186f4d8eb83874 | Terminology guide for practitioners |
| 🇯🇵 | Zenn — Context Engineering Intro (updated Aug 2026) | https://zenn.dev/suwash/articles/context_engineering_20250719 | Long-context task management added Aug 2026 |
| 🇯🇵 | note — OKF v0.2 Trust Signals | https://note.com/masa_cloud/n/n9ab01e885523 | OKF v0.2 trust for enterprise knowledge governance |
| 🇯🇵 | note — Semantic Layer vs Ontology design | https://note.com/_kihonushi/n/nad1b98d60300 | State layer design for AI agents |
| 🇨🇳 | 36Kr — 2026 AI Memory Epoch | https://36kr.com/p/3657440584688519 | 2026 = AI记忆元年; model+memory PMF |
| 🇨🇳 | 36Kr — Graph Engineering | https://36kr.com/p/3919317152722567 | Graph Engineering Knowledge 3.0 |
| 🇨🇳 | 36Kr — MemoraX Seed++ | https://eu.36kr.com/en/p/3816270549377289 | Seed++ completion; AML #1 |
| 🇨🇳 | Tencent News — MemoraX funding | https://news.qq.com/rain/a/20260812A04HY300 | 3 rounds in 6 months |
| 🇨🇳 | 163.com — AI agent memory technical | https://www.163.com/dy/article/L4KD1QQR05119734.html | AML rankings; Gen 3 native memory; AML 136 teams, 200K clicks |
| 🇨🇳 | AIBase — MemoraX Seed++ | https://www.aibase.com/news/28163 | 100M+ CNY cumulative |
| 🇨🇳 | Zhihu — MemoraX founder coverage | https://zhuanlan.zhihu.com/p/2070856096290444458 | Hao Jianye bio; Huawei Noah's Ark Lab |
| 🇨🇳 | Tencent Cloud Dev — RAG to GraphRAG | https://developer.cloud.tencent.com/article/2707853 | Memory revolution; RAG covers <60% real needs |
| 🇨🇳 | 53AI — Ontology vs KG | https://www.53ai.com/news/knowledgegraph/2026060363059.html | Formula: Ontology + Data = Knowledge Graph |
| 🇨🇳 | 53AI — Ontology + AI Agent Factory | https://www.53ai.com/news/LargeLanguageModel/2026063075103.html | End-to-end agent delivery platform |
| 🇨🇳 | Zhihu — GraphRAG Tutorial | https://zhuanlan.zhihu.com/p/2053852182978597536 | Comprehensive GraphRAG guide 2026 |
| 🇨🇳 | 53AI — RAG 2026 Analysis | https://www.53ai.com/news/RAG/2026011591504.html | RAG full analysis 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 (excluded)
├─ 🔵 X/Twitter: 0 (excluded)
├─ 🔴 YouTube: 0 (not searched)
├─ 🟢 HN: 2 threads │ 85+ pts │ 50+ comments
├─ 🟣 TikTok: 0 (not searched)
├─ 🩷 Instagram: 0 (not searched)
├─ 🦋 Bluesky: 0 posts │ 0 likes (backend OK, no topical posts)
├─ 📊 Polymarket: 0
├─ 🌐 Web: ~55 pages │ 🇯🇵 7 │ 🇨🇳 14
└─ 🗣️ Top voices: @masa_cloud (note.com), Ssk1029Takashi/YAMALEX (Hatena), Rajesh Murthy/Kyvos, Hao Jianye/MemoraX, Emil Eifrem/Neo4j
```

---

## Out of Scope but Notable

- **Onton Ontology 1** is on the boundary of this topic (neurosymbolic meets ontology), but its use case (e-commerce agentic web trust) is sufficiently distinct from the main knowledge-representation-for-agents framing that future digests may want a commerce-AI-agent topic. Link: https://onton.com/research/ontology-1
- **arXiv:2607.16848 "Beyond Memory Leaderboards: Evaluating Scientific Memory as Budgeted Context Restoration"** — proposes treating memory evaluation as context restoration under a fixed token budget, an alternative to ranking accuracy; may be paradigm-shifting for how memory benchmarks are designed. Link: https://arxiv.org/html/2607.16848v1

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** blocked by CAPTCHA for JP/CN passes; switched to native-language WebSearch — full coverage maintained
- **Bluesky:** backend OK; no topical posts surfaced via web search — likely exists but not indexed
- **YouTube:** not searched this run; likely tutorial videos for new releases (OzBrain, Palantir SuperRepo, AML)
- **TikTok/Instagram/Reddit:** excluded per instructions
- **CSDN/Juejin direct fetch:** HTTP 521/403 errors; content captured via search snippets and 163.com mirrors
- **Zhihu biweekly intelligence (Aug 1-16):** HTTP 403; content captured via search summary
- **Noise:** high volume of "best AI memory tools 2026" listicles and comparison articles — filtered to extract novel facts only
- **Coverage estimate:** ~82% — major new items captured (AML, MemoraX AML rank, Palantir SuperRepo, OzBrain, Onton, Hindsight+dsh, Cognee 1.5.0, Apache Ossie Kyvos, Databricks Genie Code as Lakeflow, neo4j meta-kg); potential gaps in YouTube tutorials, TikTok, Reddit, full Bluesky coverage, paywalled academic papers

---

## Key Quotes

> "Enterprise AI needs two things from the data foundation: the right context and the ability to access enterprise data at the speed of enterprise" — Rajesh Murthy, COO of Kyvos, on joining Apache Ossie ([link](https://www.prnewswire.com/news-releases/kyvos-joins-apache-ossie-ecosystem-bringing-speed-and-context-to-enterprise-ai-302849755.html))

> "GraphRAG's automatic extraction produces label proliferation and entity resolution failures... OKF's approach—using pre-existing system structure as concept identifiers—eliminated fragmentation entirely." — Ssk1029Takashi, Acroquest Technology (「GraphRAGの自動抽出はラベルの増殖とエンティティ解決の失敗を引き起こします...OKFのアプローチはフラグメンテーションを完全に排除しました」) ([link](https://acro-engineer.hatenablog.com/entry/2026/08/25/120000))

> "MemoraX achieved the #1 position on the inaugural Agent Memory Leaderboard... leading across all seven evaluated memory capabilities" with a score of 58.02, "ahead of international memory platforms including Mem0, Vectorize and Supermemory" — GlobeNewswire ([link](https://www.globenewswire.com/news-release/2026/08/17/3346129/0/en/memorax-ai-ranks-1-on-agent-memory-leaderboard-signaling-a-new-phase-for-long-term-ai-memory.html))

> "Businesses are accumulating AI-generated knowledge faster than they can organise or trust it" — OzBrain Show HN description ([link](https://news.ycombinator.com/item?id=49394827))

> "Determining identical entities is a problem to solve during data integration, not during inference." — Takanorisuzuki on Zenn (「同一エンティティの判定は、データ統合時に解決すべき問題であり、推論時に解決するものではありません」) ([link](https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design))

> "2026: Entering the AI Memory Epoch" (2026，进入AI记忆元年) — 36Kr ([link](https://36kr.com/p/3657440584688519))

> "Traditional vector retrieval RAG addresses less than 60% of real needs" — Tencent Cloud Developer ([link](https://developer.cloud.tencent.com/article/2707853))

> "A SuperRepo is a single monorepo that holds your Ontology definitions, your functions, and your React application together, so you can develop, build, and deploy them as one versioned artifact." — Palantir Foundry Docs ([link](https://www.palantir.com/docs/foundry/superrepo/overview))
