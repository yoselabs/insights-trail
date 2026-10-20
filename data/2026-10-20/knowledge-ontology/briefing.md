# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-10-20
**Query type:** GENERAL
**Sources:** WebSearch (multi-query EN/JP/CN), WebFetch (targeted), arXiv, GitHub, Neo4j, Zep/Graphiti, Letta, Cognee, Hindsight, past.dev, ZoomInfo, Microsoft, Tencent Cloud, Qiita, Zenn, CSDN, Zhihu, Mnemoverse

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 thread | 2 pts | 🌐 HN:48919162 reverse-engineering agent-memory tools; no high-traffic new threads this period |
| Bluesky | 0 posts | — | 🦋 Health=OK; no on-topic posts found Oct 16-20 |
| Web (global) | 45 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 5 pages | — | 🇯🇵 Qiita, Zenn, deflag, Sansan, issoh.co.jp |
| Web (China) | 7 pages | — | 🇨🇳 Tencent Cloud, Zhihu, 53AI, Juejin, CSDN, Tenten.co |
| arXiv | 4 papers | — | 🌐 2610.22668, 2610.23317, 2610.18616, 2610.05945 |
| GitHub | 5 repos | — | 🌐 letta-code, graphiti, hindsight, cognee, DKGI |

---

## Synthesized Findings

### 1. [new] Neo4j Context Engine: 6-Layer Business Ontology + Context Studio — Private Preview Launch 🌐

**Claim:** Neo4j launched the Context Engine today (Oct 20) — a shared knowledge layer for enterprise AI agents with a predefined 6-layer Business Ontology and a visual Context Studio; the first major product to ship a pre-built enterprise ontology model as the primary agent grounding substrate.
**Evidence:**
- **Business Ontology:** predefined 6-layer graph model maps organization, business processes, data, and AI assets; connects physical data sources directly to business logic
- **Context Build + Runtime:** constructs semantic layer from Databricks/Snowflake; headless/CLI/Python; built-in GraphRAG retrievers
- **Context Studio:** unified control plane for ontology management, workflow builder, AI agent configuration
- **Memory + Learning:** tracks agent decisions, distills knowledge from past interactions, improves reasoning via graph algorithms
- **Availability:** private preview; contact for "designer partner" access
- **Quote (Sanjeev Mohan):** "Context is not just more data, it's really about relationships... why and how. That is exactly what graphs model natively."
- **Sources:** [Neo4j PR](https://neo4j.com/press-releases/neo4j-context-engine/) · [FinancialContent](https://www.financialcontent.com/article/bizwire-2026-10-20-neo4j-context-engine-launches-to-create-ai-knowledge-layer-and-enhance-agent-performance)

---

### 2. [new] QEMem (arXiv:2610.22668): "Relevance-Sufficiency Gap" — 91.43% LoCoMo +7.6pp 🌐

**Claim:** QEMem (Oct 15) identifies a fundamental design flaw in retrieval-based agent memory systems — retrieving relevant memories ≠ providing sufficient evidence — and fixes it without modifying memory formation, reaching 91.43% on LoCoMo.
**Evidence:**
- **Core problem:** "relevance-sufficiency gap" — essential information may be fragmented across records, obscured by abstraction, or disconnected from reasoning relations
- **QEMem (3 mechanisms):** (1) query-guided discovery (multi-granularity evidence retrieval), (2) source-grounded reification (ViewCards with evidential roles + source references), (3) sufficiency-guided refinement (selective missing-info recovery)
- **Result:** 91.43% LLM-judge accuracy on LoCoMo with Claude Opus 4.5; +7.6pp over MemR³ (strongest baseline)
- **Key property:** works on ANY existing memory store without modifying memory formation — drop-in improvement
- **Authors:** Shixuan Li, Wei Yang, Peiyu Zhang, et al. (10 authors)
- **Source:** [arXiv:2610.22668](https://arxiv.org/abs/2610.22668)

---

### 3. [new] past.dev: #1 BEAM (Oct 6) + #1 DolphinBench — Tracks "What Is Still True" 🌐

**Claim:** past.dev has taken top positions on both BEAM (Oct 6) and DolphinBench (before Oct 20), outperforming all prior incumbents by substantial margins, using a truth-tracking approach instead of similarity search.
**Evidence:**
- **BEAM scores (Oct 6):** 100K=92.08% (prev 86.2%), 500K=89.63% (prev 80.1%), 1M=90.65% (prev 79.1%), 10M=85.03% (prev 68.0%)
- **DolphinBench:** 81.7% (490/600 tasks) with Hermes Agent + GPT 5.6 Luna; comparisons: Mem0 70.7%, Hindsight 69.5%, Honcho 68.5%
- **Architecture:** tracks (1) what facts are currently true, (2) what they replaced, (3) dated sources; respects access controls
- **CEO Mehdi Djabri:** "Search finds what looks similar, not what's still true."
- **Certifications:** SOC 2 Type II, ISO 27001/27701; MCP integration; enterprise hosting
- **Sources:** [BEAM PR](https://www.prnewswire.com/news-releases/pastdev-introduces-frontier-memory-for-ai-agents-1-on-beam-the-largest-public-memory-benchmark-302899770.html) · [DolphinBench PR](https://www.prnewswire.com/news-releases/memory-for-ai-agents-gets-more-accurate-pastdev-reports-the-highest-score-yet-on-dolphinbench-302914085.html)

---

### 4. [new] AgentOnto (arXiv:2610.23317): Ontology as Self-Updating Enterprise Analytics Layer 🌐

**Claim:** AgentOnto (Oct 16) closes the loop on ontology as a live feedback substrate — the ontology updates when analysis confirms or refutes it, making it a self-reinforcing enterprise knowledge representation, not just a static guide.
**Evidence:**
- **Problem:** enterprise analytics agents fail because knowledge is distributed across DBs, docs, and examples with no explicit representation
- **Components:** Ontology Construction (integrates from all sources) → Ontology-Guided Analysis (guides plan + execution) → Ontology Updating (confirmed feedback → targeted ontology changes)
- **Iterative Ontology Preparation:** self-generated analysis tasks improve ontology proactively
- **Results:** substantially outperforms representative baselines; real-world enterprise deployment confirmed
- **Authors:** Dayan Pan et al. (5 authors); CS.AI + CS.DB classification
- **Source:** [arXiv:2610.23317](https://arxiv.org/abs/2610.23317)

---

### 5. [new] DKGI (arXiv:2610.18616): Knowledge Graphs as Files — Tool Creation and Use Co-Evolve 🌐

**Claim:** DKGI (Oct 13) shows that giving agents raw node/edge files and letting them write graph access code produces better results than predefined tool APIs — because tools co-evolve with the task, not the other way around.
**Evidence:**
- **Direct Knowledge Graph Interaction (DKGI):** agents create Python graph access tools over complete node+edge files; write code to traverse relations, combine node sets, select text evidence; interleave with shell search
- **Key insight:** tools evolve during a task through revising graph-access code using execution feedback — task-adaptive, not preset
- **Results:** ≥6.7 Hit@1 points over strongest published baseline across all 3 tested graph domains; training-free
- **Authors:** Yuyang Bai, Yu Wang, Yu Zhang; code at [GitHub](https://github.com/leopoldwhite/DKGI)
- **Source:** [arXiv:2610.18616](https://arxiv.org/abs/2610.18616)

---

### 6. [new] ZoomInfo Workbounce: Semantic Knowledge Layer in GTM Context Graph (Oct 14) 🌐

**Claim:** ZoomInfo activated the Workbounce acquisition by adding a governed semantic knowledge layer to its GTM Context Graph — the first enterprise CRM-class system to formally merge external market data with internal unstructured knowledge under ontology governance.
**Evidence:**
- **Workbounce integration:** semantic knowledge layer ingests call transcripts, emails, presentations, product docs, account notes, Slack, Google Drive, Notion
- **Governance:** lineage, confidence, permission, entitlement controls — same governance as ZoomInfo's verified market data
- **Use cases:** answer+asset retrieval, reduced seller admin, next-best-action recommendations, collaborative customer spaces
- **Context:** ZoomInfo acquired Workbounce in 2024; fully integrated Oct 14, 2026
- **Sources:** [DestinationCRM](https://www.destinationcrm.com/Articles/CRM-News/CRM-Across-the-Wire/ZoomInfo-Brings-Enterprise-Knowledge-into-the-GTM-Context-Graph-177045.aspx) · [VentureBeat](https://venturebeat.com/business/zoominfo-brings-enterprise-knowledge-into-the-gtm-context-graph-through-workbounce-acquisition/)

---

### 7. [new] BM25 Beats All Commercial Memory Products on MemoryAgentBench (Ajay Kumar Analysis) 🌐

**Claim:** A comprehensive Oct 2026 analysis finds that plain BM25 retrieval (60.5%) outperforms every commercial memory product on MemoryAgentBench (Mem0 25-36%, Zep 25-44%), and a plain filesystem scored 74 on LoCoMo — reframing agent memory as a database architecture problem, not a product problem.
**Evidence:**
- **MemoryAgentBench:** BM25 60.5% avg beats all commercial products; Mem0 25-36%, Zep 25-44%
- **LoCoMo (mixed conditions):** Letta filesystem (no memory product) 74.0%; full-context 72.9%; Mem0 managed 92.5% — but "not like for like" (different answer models, judges, ingestion)
- **Economics:** Claude Sonnet 5.5 cache costs $0.023/turn vs Mem0 ~$0.014 retrieved tokens; memory only beats cache when session expires (5min) or users return weekly
- **Security:** MINJA paper (Feb 2026) — read-only attackers can plant records retrieved by future users → persistent prompt injection; requires provenance tracking + per-tenant isolation
- **Recommendation:** Postgres + pgvector, customer-owned; benchmark against BM25 + cached full context first
- **Source:** [Ajay Kumar blog](https://www.ajayk.sh/blog/agent-memory-systems-2026/)

---

### 8. [new] Mem0 Removes Graph Memory from OSS (April 2026 — First Capture) 🌐

**Claim:** Mem0 silently removed all external graph store integrations (~4,000 lines of code: Neo4j, Memgraph, Kuzu, Apache AGE, Neptune) from its OSS SDK in April 2026, locking graph memory to the Pro paid tier at $249/mo — a significant architectural fork between OSS and commercial versions.
**Evidence:**
- **PR #4805 (Apr 14, 2026):** removed all external graph store drivers from Python and TypeScript SDKs
- **Replacement (OSS):** entity linking at write time + entity boosting at search time in parallel `{collection}_entities` collection; no graph traversal
- **Platform graph memory:** built-in, always-on, no external DB; $249/mo Pro tier
- **Docs gap:** AGENTS.md still documented graph memory after removal (GitHub issue #6591)
- **Sources:** [migration docs](https://docs.mem0.ai/migration/oss-v2-to-v3) · [GitHub issue #6591](https://github.com/mem0ai/mem0/issues/6591)

---

### 9. [update] Letta Code v0.34.16–v0.34.18: Memory Skills, CodeMode, Subagent Control (Oct 16–19) 🌐

**Claim:** Letta shipped 3 more releases (Oct 16-19), adding two new memory management skills, CodeMode for lightweight tool scripts, and full lifecycle control of remote coding subagents — 7 total releases in 11 days (v0.34.12–v0.34.18).
**New facts since v0.34.15 (Oct 15):**
- **v0.34.16 (Oct 16):** steer/resume/stop remote Claude Code + Codex subagents; teleportation (keeps monitored conversations on original computers)
- **v0.34.17 (Oct 18):** CodeMode (simple tool scripts); music-generation Cloud skill; local compaction + listener heartbeat fixes
- **v0.34.18 (Oct 19):** `maintaining-core-memory` + `maintaining-deferred-memory` skills; `skills` option for `agent()` function; workflow journal + subagent stop fixes
- **Sources:** [Letta Code releases](https://github.com/letta-ai/letta-code/releases)

---

### 10. [update] Cognee v1.6.5: Raw Cypher Off, Triplets Removed, Memory Auth (Oct 16) 🌐

**Claim:** Cognee v1.6.5 makes a significant architecture shift: raw Cypher search is now off by default, triplet embedding removed, `memify` deprecated — converging on a less graph-explicit, more semantics-first memory model with typed authorization.
**New facts since v1.6.1 (Sep 24):**
- **v1.6.5 (Oct 16):** raw Cypher search off by default; removes triplet embedding; deprecates `memify` → `improve()`; BROAD search (whole-dataset questions); opt-in fact-conflict review; Google Calendar connector; memory authorization (typed entries check dataset_id + write grant)
- **v1.6.4 (Oct 13):** LanceDB worker process fix; vector search efficiency fix; Turso error handling
- **Source:** [Cognee changelog](https://docs.cognee.ai/changelog)

---

### 11. [update] Hindsight Reaches 50K GitHub Stars; v1.0 Stable (Oct 15) 🌐

**Claim:** Hindsight crossed 50K GitHub stars in 350 days (Oct 15), simultaneously stabilizing v1.0 API and launching Memlake enterprise storage — the fastest OSS agent-memory project to this milestone.
**New facts since Oct 13 (Memlake launch):**
- **50K stars:** reached Oct 15, 2026; 350 days from initial release; 6,077 forks, 288 contributors, 3,042 merged PRs, 73 releases; MIT
- **Commitment:** architecture and API are stable going forward; commitment to remain open source and free
- **Source:** [50K blog post](https://hindsight.vectorize.io/blog/2026/10/15/hindsight-50k-stars)

---

### 12. [update] Fabric IQ: Unified Semantic Modeling + MCP Endpoints in Preview (Oct 8, FabCon) 🌐

**Claim:** FabCon Barcelona (Oct 8) added "Unified Semantic Modeling" to public preview — reuse of Power BI DAX measures, REST APIs, SDKs, MCP endpoints, and a proposal-first AI ontology agent — expanding Fabric IQ from ontology definition to full ontology-as-code infrastructure.
**New facts since Oct 9 (prior capture):**
- **Unified Semantic Modeling:** reuse existing Power BI DAX measures and calculated columns without copying metadata
- **AI-powered ontology agent:** natural-language → entity/relationship proposals; proposal-first (human review before any application)
- **New modeling:** keyless bindings, complex relationships, inheritance, namespaces (entity hierarchies in newest version)
- **Developer:** REST APIs, SDKs, MCP endpoints; Git/CI-CD workflow integration
- **Gartner note:** "Microsoft's Fabric IQ Updates Make Ontologies Operational" — confirmed as notable product milestone
- **Sources:** [James Serra FabCon blog](https://www.jamesserra.com/archive/2026/10/announcements-from-the-microsoft-fabric-community-conference-barcelona-2026/) · [Fabric IQ docs](https://learn.microsoft.com/en-us/fabric/iq/ontology/overview) · [Gartner](https://www.gartner.com/en/insights/gartner-first-takes/microsoft-fabric-iq)

---

### 13. [update] NODES 2026: Two More Workshops Upcoming + Full Agenda Live (Oct 22, Oct 29) 🌐

**Claim:** Road to NODES workshops continue with two more memory-focused sessions (Oct 22, Oct 29), and the Nov 12 NODES 2026 agenda is now live with "The Memory Graph: How Knowledge Graphs Power Sovereign AI" as a featured session.
**New facts since Oct 15 (Alessandro Negro workshop):**
- **Oct 22:** Graph Reasoning with Neo4j Virtual Graph — Cypher queries directly against cloud data warehouses
- **Oct 29:** Build full graph-based agent memory stack — hierarchical context graphs, retrieval + answer playbooks, dynamic playbook composition
- **Nov 12 NODES 2026:** 100+ speakers; featured sessions: "The Memory Graph: How KGs Power Sovereign AI", "Meta Knowledge Graph: A Self Learning Agentic System", "Beyond Vector Memory: Temporal Graph Memory"
- **Sources:** [NODES agenda](https://neo4j.com/nodes/agenda/) · [Workshop announcement](https://community.neo4j.com/t/register-road-to-nodes-2026-hands-on-workshops-start-october-1/81216)

---

### 14. [update] Graphiti v0.31.0 / v0.31.1: Publish Fix Confirmed; v0.32.0 Not Yet Released 🌐

**Claim:** Graphiti v0.31.0 (Oct 14) failed to publish to PyPI due to a pyproject.toml version mismatch (said 0.32.0); v0.31.1 (Oct 15) fixed the publishing; v0.32.0 not yet released as of Oct 20.
**Source:** [Graphiti releases](https://github.com/getzep/graphiti/releases)

---

### 15. [update] "Everyone Is Building a Context Graph" — AlphaSense, Google Workspace, Day AI (Oct 14) 🌐

**Claim:** As of Oct 14, every major enterprise productivity/intelligence vendor has independently converged on a "context graph" framing — with AlphaSense, Google, and Day AI each using the same architecture pattern for different domains (financial research, workspace, GTM).
**Evidence:**
- **AlphaSense SuperAnalyst (Jun 2026):** "Context Graph" extracts timestamped facts from documents/filings; always-on research agent
- **Google Workspace Intelligence:** converts scattered emails/chats/files into cohesive knowledge graph
- **Day AI:** "Customer Memory" ingests team email/calendar/meetings/Slack with approval workflows
- **ZoomInfo GTM.AI:** as in §6 above
- **42% of institutional knowledge siloed** with individuals (Panopto research); author Jeff Reynar frames context graphs as the solution to "knowledge trapped in email threads"
- **Source:** [this+that.chat blog](https://www.thisandthat.chat/blog/everyone-is-building-a-context-graph)

---

### 16. [update] ISWC 2026 (Oct 25–29, Bari): OntoInk Demo + IBM Paper Confirmed; Upcoming 🌐

**Claim:** ISWC 2026 (5 days away) has two confirmed knowledge-memory contributions: OntoInk (documentation-as-code ontology tooling) and IBM's agentic KG memory paper (already open-sourced).
**Evidence:**
- **OntoInk (arXiv:2610.05945):** ISWC 2026 demo paper; MkDocs plugin unifying documentation + SHACL validation + OWL DL reasoning + inline Turtle editing in one pipeline; SHACL constraint cardinality badges on graph diagrams; visual SHACL shape editor; live at [ontoink demo](https://ise-fizkarlsruhe.github.io/ontoink/); PyPI [ontoink](https://pypi.org/project/ontoink/0.7.9/)
- **IBM paper (Oct 25):** "Transparent, Traceable, Deterministic: Agentic Memory via Knowledge Graphs" — imperative+generative computing; enterprise-piloted; open-sourced
- **GLOW workshop:** 14 papers on KG + LLMs
- **Sources:** [ISWC 2026](https://iswc2026.semanticweb.org/) · [IBM Research](https://research.ibm.com/publications/transparent-traceable-deterministic-agentic-memory-via-knowledge-graphs) · [arXiv:2610.05945](https://arxiv.org/abs/2610.05945) · [GLOW](https://glow-workshop.github.io/iswc2026/)

---

**Still true** (ongoing threads, no new facts this run):
- zep-v4-context-api-hyperedges: v4 Context API live; API docs found (each search scope has own v4 method); no post-Oct 16 new release
- ansatz-continual-graph-memory-math: arXiv:2610.02945; no new coverage found
- semantica-oss-graph-native-context: v0.7.0 still current; no new release found
- tencentdb-agent-memory-team-hub: 27.8K stars (prior); no new Oct update
- hgp-on-device-hybrid-graph-memory: arXiv:2610.10071 still current
- ontoar-har-ontology-guided-rag: arXiv:2610.15292 still current
- hindsight-memlake-object-storage: Oct 13 launch; no new Oct 16-20 technical update
- narrow-deep-ontology-tower-industrial: arXiv:2610.11768 still current
- textql-ontology-ga: Oct 1 GA; no new Oct 16-20 update
- jp-devio2026-4-layer-context-stack: Oct 9/11 presentation; no new content
- jp-cybernetics-ontology-unnecessary-counterargument: Sep 26 counter-thesis still standing
- cn-53ai-pole-plus-o-mongodb-agent-memory: Sep 23 architecture; no new CN update this run
- skan-ai-aow-agentic-ontology-of-work: AOW v1.0/v2.0 still current
- ontocast-hn-agentic-ontology-extraction: no new activity
- hindsight-v0100-multimodal-memory: v0.10.3 current; v1.0 stable + 50K stars (→ see §11)
- ekaw-2026-knowledge-engineering-conference: Proceedings published; no new chapters
- fabric-iq-ontology-mcp: → see §12 above (update)
- iswc-2026-knowledge-graph-conference: → see §16 above (5 days away)
- ibm-iswc-2026-agentic-memory-kg: → see §16 above
- inspired-production-ontology-engineering: Oct 7 critique still current
- active-ontology-atlan-2026: Gartner 50%+ by 2028; 38% SQL gain; ongoing
- jp-zenn-netflix-e2e-kg-autosre: Netflix AutoSRE; no new content
- jp-zenn-bare64-ontology-practice: Protégé vs Fabric IQ; no new content
- cn-ccks-2026: Concluded; WAIE Oct 23 not yet occurred (bluebook not published)
- cn-53ai-ontology-kg-world-model-path: Three-phase path still canonical
- dell-ai-platform-kg-semantic-layer: H1 2027 roadmap; no new Oct update
- okf-agent-memory-hn-bm25: OKF v0.4.4; no v0.5 found
- graphify-codebase-kg-no-vector: v0.9.53; no new release
- ob-caie-ontology-ai-evaluation: arXiv:2610.00529 still current
- jp-ontology-for-data-engineers-zenn: SL+ontology complementary
- jp-lightweight-ontology-fixed-queries-bigquery: Fixed SQL not generative; BigQuery Graph
- jp-graph-infra-ai-agents-index-free: Index-free adjacency; 4 RAG types
- evoontology-self-evolving-mcp-server: arXiv:2609.15779; no new update
- turbopuffer-v3-ann-primary-retired: v3 live; ANN-primary removed
- agentmemory-dotnet-pole-plus-o: POLE+O .NET; 178/178 TCK
- blitzy-coding-agents-neo4j-graph: $200M; SWE-Bench 84.95%; no new news
- hn-getcassis-entity-graph-complexity: memories/state/handoff must NOT share ontology
- memory-portability-model-upgrade: KG ±0.0020 vs NOTES ±13pp
- moosedev-nesy2026-ontology-coding-memory: 0.98–1.00 recall vs 6–27% vector
- industrial-kg-unification-287-mcp-tools: recall 1.00→0.31 without cross-system tools
- evograph-mem-failure-aware-editable: append-only insufficient
- llm-guided-ontology-kg-construction-ijckg2026: IJCKG 2026 Nov Bangkok; still upcoming
- trikedb-cyberagent-lightweight-ontology-yaml: 88.7% WebQSP at 250-triple budget
- aml-agent-memory-leaderboard: Cycle 2 open; Oct 31 deadline; results mid-November
- cognee-1-0-four-verb-api: → see §10 above (v1.6.5 update)
- zep-ce-retired-graphiti-open-source: Graphiti v0.31.1 current; v0.32.0 not yet released
- graphwise-events-oct-2026: SLS Vienna completed; ISWC upcoming Oct 25
- benchmark-proliferation-memory: AML Oct 31 deadline; past.dev now top on BEAM+DolphinBench (→ §3)
- okf-v02-provenance-trust: OKF v0.4.4; no v0.5 found
- okf-v01-structural-interoperability: Structural interoperability; semantic gap future work
- mem0-v2-token-efficiency: 66.6K stars; graph memory removed from OSS (→ §8)
- graphwise-oakley-semantic-layer-pe: Oakley Capital; 30%+ ARR; no new Oct news
- semantics-2026-ghent: Concluded Sep 17; no new Oct news
- databricks-genie-ontology: No new October updates; Context Engineer cert still GA
- databricks-context-engineer-cert: GA Jul 29; no new updates
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1; no new Oct updates
- benchmark-vendor-inflation-measured: Mnemoverse Q3 20pp vendor inflation confirmed standing
- hindsight-memory-benchmark-leader: → see §11 above (50K stars); no new benchmark update
- parametric-kg-storage-retrieval-gap: LoRA parametric KG stores but retrieval at chance
- selective-forgetting-kg-vs-flat: KG F1=0.417 vs flat 0.468 on LME
- megamem-ultra-large-context-retrieval: 650M+ tokens; 68.22→82.26 EnterpriseRAG-Bench
- graph-personalized-memory-survey-ickg2026: ICKG 2026 survey still current
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview
- jp-ontology-to-tool-mechanical-generation: 12-obj/34-action YAML → 58 tools
- mem0-strands-osv3-algorithm: Native AWS Strands; single-pass ADD-only; ongoing
- msock-intellect-enterprise-spatial-graph: 21-dimensional ESG; no new news
- heimdall-trust-verified-kg-coding: Cross-repo KG; CPU-only; no new news
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction; no new release
- jp-ontology-driven-graphrag-construction: Entity unification 72→94%; no new content
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference; ongoing
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale; ongoing
- jp-two-layer-memory-write-gate: Hot/cold two-layer; ongoing
- ontologx-autonomous-log-kg: Cybersecurity log→ontology KG; ongoing
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory; MemOS ongoing
- cn-china-agent-government-regulation: May 2026 government bounding regulation; ongoing
- magg-governed-kg-construction: +47% strict F1 SciERC; ongoing
- metaphactory-6-ontopic-virtual-kg: Ontopic acquired; metaphactory 5.9; ongoing
- memorax-code-coding-plugin: 4 memory types; Claude Code/Codex/WorkBuddy; ongoing
- jp-zenn-kg-memory-entity-resolution: Entity resolution = primary engineering barrier
- jp-note-semantic-layer-vs-ontology-failure: 60% projects fail without SL
- memos-memory-os-proactive-scheduling: MemOS 11.7K stars; ongoing
- openkg-spg-kag-skillnet-dynamic-eval: Claude 4.5 at 37.65% on dynamic eval
- jp-coa-deployment-53pct-variance: COA eliminates 53% answer variance
- aws-context-ontology-accelerator: months→days; OWL 2+HermiT; Apache 2.0
- mnemoverse-hebbian-memory: Hebbian + Rescorla-Wagner; 6 MCP tools; ongoing
- neo4j-constant-cost-semantic-memory: Road to NODES Oct 15 completed; Oct 22+29 upcoming (→ §13)
- sap-knowledge-graph-autonomous-enterprise: 452K tables; 50+ Joule Assistants; ongoing
- neo4j-labs-agent-memory-nams: POLE+O; 178/178 TCK; NAMS; ongoing
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG
- apache-ossie-semantic-interchange: Kyvos+Databricks; no Oct updates
- mcp-ontology-integration-protocol: MCP 2026-07-28 final spec; all major tools MCP-native
- ontology-as-reliability-infrastructure: EN/JP/CN independently frame ontology as correctness layer
- hn-5-mistakes-kg-memory: POLE+O practitioner baseline; schema decides everything
- cn-ontology-strategic-return: Strategic return confirmed; Tencent Cloud reinforces
- tencent-tbox-abox-framing: TBox (LLM) / ABox (human validates); ongoing
- vector-db-market-growth: $3.47B in 2026; KG $19.16B by 2035 (Anadiotis)
- architecture-beats-model-scale: past.dev #1 BEAM+DolphinBench (→ §3) further confirms
- ontology-guardrails-framing: Guardrails framing; ongoing
- cn-llms-reshape-ontology-engineering: TBox generation by LLM; human validates ABox
- jp-layered-implementation-path: SL → Lightweight Ontology → MCP
- jp-qiita-ontology-department-alignment: Root cause = missing ontology, not model quality
- benchmark-proliferation-memory-dup: Placeholder; carries forward

---

## Cross-Source Patterns

**1. "Truth-tracking" vs "similarity-search" as the new memory dichotomy** 🌐
- past.dev (Oct 6-20): explicit "tracks what's still true, what it replaced, and dated sources" — positions as anti-similarity
- QEMem (Oct 15): frames "relevance-sufficiency gap" — relevance ≠ sufficient evidence; needs evidence construction not just retrieval
- Ajay Kumar blog: BM25 60.5% beats all commercial products on MemoryAgentBench — similarity-based commercial products losing to simpler baselines
- Zep v4 hyperedges: "agents find one pair of a fact and miss the rest" — same failure mode from the graph side
- Platforms: arXiv, PR Newswire, blogs

**2. Ontology-as-code and MCP as universal delivery layer consolidating** 🌐
- Fabric IQ: REST APIs, SDKs, MCP endpoints, Git/CI-CD — ontology becomes code artifact managed in version control
- Neo4j Context Engine: predefined ontology model shipped as product; Context Studio = ontology management plane
- Graphiti: MCP SDK upgraded to 2.x (Oct 14); Zep CE ended to focus on Graphiti OSS
- OntoInk: documentation-as-code pipeline for ontology (SHACL + OWL + visualization)
- Platforms: GitHub, Microsoft, Neo4j, arXiv

**3. Convergence on "context graph" branding across enterprise verticals** 🌐
- Neo4j Context Engine (Oct 20): "shared context layer for enterprise AI"
- ZoomInfo GTM Context Graph (Oct 14): CRM/GTM domain
- AlphaSense SuperAnalyst (Jun 2026): financial research Context Graph
- Google Workspace Intelligence: general productivity KG
- Day AI: Customer Memory from communications
- Pattern: diverse enterprise vendors using identical "context graph" framing without coordination; architectural convergence underway
- Platforms: multiple press releases, TechCrunch, VentureBeat

**4. Memory benchmarks fragmenting: new challengers, contested scores** 🌐
- past.dev: #1 BEAM + #1 DolphinBench; substantial margin over prior leaders
- Ajay Kumar: LoCoMo scores "not like for like" (different answer models, judges, ingestion) — warns against direct comparison
- AML Cycle 2: Oct 31 deadline, results mid-November; Coding Memory + Multimodal Memory tracks added
- MINJA (Feb 2026): memory systems have security attack surface (planted records) — no product has mitigated this publicly
- Platforms: PR Newswire, arXiv, blog analysis

---

## Per-Platform Tables

**Web (global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Neo4j | [Context Engine PR](https://neo4j.com/press-releases/neo4j-context-engine/) | **NEW** Oct 20: 6-layer Business Ontology; Context Studio; private preview |
| 🌐 | arXiv | [QEMem 2610.22668](https://arxiv.org/abs/2610.22668) | **NEW** Oct 15: relevance-sufficiency gap; 91.43% LoCoMo +7.6pp |
| 🌐 | arXiv | [AgentOnto 2610.23317](https://arxiv.org/abs/2610.23317) | **NEW** Oct 16: ontology-guided enterprise analytics; self-updating |
| 🌐 | arXiv | [DKGI 2610.18616](https://arxiv.org/abs/2610.18616) | **NEW** Oct 13: KG as files; tool creation+use co-evolve; +6.7 Hit@1 |
| 🌐 | past.dev | [BEAM PR](https://www.prnewswire.com/news-releases/pastdev-introduces-frontier-memory-for-ai-agents-1-on-beam-the-largest-public-memory-benchmark-302899770.html) | **NEW** Oct 6: BEAM #1 across all sizes |
| 🌐 | past.dev | [DolphinBench PR](https://www.prnewswire.com/news-releases/memory-for-ai-agents-gets-more-accurate-pastdev-reports-the-highest-score-yet-on-dolphinbench-302914085.html) | **NEW**: DolphinBench #1 (81.7%) |
| 🌐 | ZoomInfo | [DestinationCRM](https://www.destinationcrm.com/Articles/CRM-News/CRM-Across-the-Wire/ZoomInfo-Brings-Enterprise-Knowledge-into-the-GTM-Context-Graph-177045.aspx) | **NEW** Oct 14: Workbounce semantic KL in GTM graph |
| 🌐 | Ajay Kumar | [blog](https://www.ajayk.sh/blog/agent-memory-systems-2026/) | **NEW**: BM25 beats all commercial; economics; MINJA security |
| 🌐 | Mem0 docs | [migration](https://docs.mem0.ai/migration/oss-v2-to-v3) | **NEW capture** Apr 14: graph memory removed from OSS; ~4K lines deleted |
| 🌐 | Letta Code | [releases](https://github.com/letta-ai/letta-code/releases) | **UPDATE** Oct 16-19: v0.34.16-18; memory skills; CodeMode |
| 🌐 | Cognee | [changelog](https://docs.cognee.ai/changelog) | **UPDATE** Oct 13-16: v1.6.4-5; Cypher off; triplets removed |
| 🌐 | Hindsight | [50K blog](https://hindsight.vectorize.io/blog/2026/10/15/hindsight-50k-stars) | **UPDATE** Oct 15: 50K stars; 350 days; v1.0 stable commitment |
| 🌐 | FabCon | [James Serra blog](https://www.jamesserra.com/archive/2026/10/announcements-from-the-microsoft-fabric-community-conference-barcelona-2026/) | **UPDATE** Oct 8: Unified Semantic Modeling; MCP endpoints; proposal-first ontology agent |
| 🌐 | Graphiti | [releases](https://github.com/getzep/graphiti/releases) | ONGOING v0.31.1 Oct 15; v0.32.0 not yet released |
| 🌐 | this+that | [context graph](https://www.thisandthat.chat/blog/everyone-is-building-a-context-graph) | **UPDATE** Oct 14: AlphaSense+Google+Day AI all building context graphs |
| 🌐 | Neo4j | [NODES agenda](https://neo4j.com/nodes/agenda/) | **UPDATE**: Oct 22 + Oct 29 workshops upcoming; Nov 12 NODES 2026 |
| 🌐 | arXiv | [OntoInk 2610.05945](https://arxiv.org/abs/2610.05945) | ONGOING: ISWC demo; docs-as-code ontology tooling |
| 🌐 | IBM | [ISWC paper](https://research.ibm.com/publications/transparent-traceable-deterministic-agentic-memory-via-knowledge-graphs) | ONGOING: Oct 25 ISWC presentation; already open-sourced |
| 🌐 | HN | [48919162](https://news.ycombinator.com/item?id=48919162) | ONGOING: reverse-engineering Cognee/Graphiti/Neo4j AM; KG "overkill" for personal scale |
| 🌐 | Mnemoverse | [Q3 comparison](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3) | ONGOING: Letta 52.2%, Mem0 50.0%, Zep/Graphiti 37.0% (Mnemoverse harness) |
| 🌐 | AML | [leaderboard](https://agentmemoryleaderboard.ai/) | ONGOING: Cycle 2; Oct 31 deadline; results mid-November |
| 🌐 | Gartner | [Fabric IQ](https://www.gartner.com/en/insights/gartner-first-takes/microsoft-fabric-iq) | ONGOING: "Fabric IQ Updates Make Ontologies Operational" |
| 🌐 | VentureBeat | [ZoomInfo Workbounce](https://venturebeat.com/business/zoominfo-brings-enterprise-knowledge-into-the-gtm-context-graph-through-workbounce-acquisition/) | NEW: ZoomInfo enterprise KG convergence |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | Qiita/cvusk | [graph-based AM](https://qiita.com/cvusk/items/78e1f144069f04a5702e) | 5 structural patterns; MAGMA 0.700 LoCoMo; Feb 2026 |
| 🇯🇵 | Qiita/agdexai | [memory guide](https://qiita.com/agdexai/items/ba7326bd6039b7458010) | Memory tool comparison 2026 |
| 🇯🇵 | deflag.net | [SL explainer](https://deflag.net/articles/tDIT3x03) | SL = defines what; context layer = company context |
| 🇯🇵 | deflag.net | [context layer](https://deflag.net/articles/Sz4KCRDF) | Context layer explainer for AI agents |
| 🇯🇵 | Sansan Tech Blog | [SL article](https://buildersbox.corp-sansan.com/entry/2026/01/29/110000) | Incremental SL growth for AI agents; Jan 2026 |
| 🇯🇵 | Zenn/knowledge_graph | [KG memory design](https://zenn.dev/knowledge_graph/articles/kg-agent-ontology-design) | Memory-first architecture; ontology as semantic structure |
| 🇯🇵 | CyberAgent | [trikedb](https://developers.cyberagent.co.jp/blog/archives/65814/) | Lightweight YAML/RDF ontology; 88.7% WebQSP (carried) |
| 🇯🇵 | Zenn/mbk_digital | [SL article](https://zenn.dev/mbk_digital/articles/61cb47b23dcb03) | SL+ontology sequential stages (carried) |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Tencent Cloud | [SL+KG rise](https://cloud.tencent.com/developer/article/2616559) | Knowledge engineers as emerging profession; MCP to Linux Foundation |
| 🇨🇳 | Zhihu | [memory series](https://zhuanlan.zhihu.com/p/2061153471890568460) | 5 memory representation strategies incl. graph |
| 🇨🇳 | Zhihu | [cognee best](https://zhuanlan.zhihu.com/p/1943451926181164200) | Cognee rated best CN agent memory layer |
| 🇨🇳 | 53AI | [ontology memory](https://www.53ai.com/news/knowledgegraph/2026071347906.html) | Ontology as AI-era memory system (not knowledge base) |
| 🇨🇳 | Tenten.co | [selection guide](https://university.tenten.co/t/ai-agent-graphiti-zep-mem0-agentmemory-everos/2328) | Graphiti/Zep/Mem0/EverOS technical selection guide |
| 🇨🇳 | Juejin | [strategic return](https://juejin.cn/post/7656270771611140123) | Ontology+KG strategic return framing 2026 |
| 🇨🇳 | CSDN | [frameworks comparison](https://blog.csdn.net/RMSXY/article/details/159800698) | Mem0/Zep/LangMem/MemOS/TiMem deep comparison (HTTP 521) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (anon) | I reverse-engineered the three biggest agent-memory tools | 2 | 4 | "at personal or small scale, KG is overkill" | https://news.ycombinator.com/item?id=48919162 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct access)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not searched directly)
├─ 🟢 HN: 1 thread │ 2 pts │ 4 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (health=OK; no on-topic posts Oct 16-20)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 45 pages │ 🇯🇵 8 │ 🇨🇳 7
└─ 🗣️ Top voices: Shixuan Li et al. (QEMem arXiv:2610.22668), Mehdi Djabri/past.dev (BEAM #1), Jeff Reynar (context graph convergence), Dayan Pan et al. (AgentOnto) │ Qiita/cvusk (JP graph memory patterns), Tencent Cloud (CN knowledge engineer framing)
```

---

## Out of Scope but Notable

- **Letta MemFS "dreaming" sleep-time subagents:** git-backed agent memory with concurrent background subagents writing lessons during sleep steps; configured via DreamSettings with triggerable cadences. Technically in scope but the "dreaming" framing (agents processing memory offline like biological sleep cycles) represents a paradigm shift from storage to maintenance-as-loop that deserves separate tracking in agent-harnesses topic. Source: https://docs.letta.com/concepts/memfs

- **past.dev truth-tracking architecture:** tracks "what is currently true, what it replaced, dated sources" — a temporal ontology in disguise, not a memory product. CEO Mehdi Djabri's "search finds similar, not still true" framing suggests the dominant agent-memory companies may converge on temporal KG architectures under different names (see also Zep bi-temporal, QEMem ViewCards). This architectural convergence is tracked within this topic but worth flagging for the AI-capabilities / paradigm-watch digest.

---

## Data Gaps

- **DuckDuckGo HTML:** CAPTCHA-blocked for both JP and CN queries; fell back to native-language WebSearch for both passes
- **Reddit:** no direct access (r/KnowledgeGraphs, r/SemanticWeb absent)
- **Bluesky:** health=OK; no on-topic posts found Oct 16-20
- **HN:** only 1 low-engagement thread found Oct 16-20 on topic
- **ISWC 2026:** conference Oct 25-29, not yet occurred; content not yet delivered
- **WAIE 2026 (Oct 23, Shenzhen):** not yet occurred; China AI Agent benchmarks bluebook not published
- **AML Cycle 2:** deadline Oct 31; no results yet
- **CSDN Oct article:** HTTP 521 — could not fetch
- **Juejin article:** "Please wait..." loading page — content not retrieved
- **ZoomInfo IR:** HTTP 403 — covered via secondary sources
- **OKF v0.5:** not found; confirmed still at v0.4.4
- **Coverage estimate:** ~78% — strong on tool releases (Neo4j Context Engine, Letta, Cognee, Hindsight, Graphiti, past.dev), new arXiv papers (QEMem, AgentOnto, DKGI), JP/CN passes via WebSearch; weaker on social engagement, Reddit, upcoming-conference content

---

## Key Quotes

> "Context is not just more data, it's really about relationships... why and how. That is exactly what graphs model natively." — Sanjeev Mohan, quoted in Neo4j Context Engine launch ([link](https://neo4j.com/press-releases/neo4j-context-engine/))

> "Search finds what looks similar, not what's still true." — Mehdi Djabri, CEO past.dev, on their #1 BEAM + DolphinBench approach ([link](https://www.prnewswire.com/news-releases/pastdev-introduces-frontier-memory-for-ai-agents-1-on-beam-the-largest-public-memory-benchmark-302899770.html))

> "Retrieving relevant memories does not necessarily provide sufficient evidence for answering a query — essential information may remain fragmented across memory records, obscured by abstraction, or disconnected from the relations required for reasoning." — QEMem, arXiv:2610.22668 ([link](https://arxiv.org/abs/2610.22668))

> "Tool creation and tool use co-evolve during graph search — tools evolve during a task through revising graph-access code using execution feedback rather than a fixed tool API." — DKGI, arXiv:2610.18616 ([link](https://arxiv.org/abs/2610.18616))

> "Knowledge engineers" are the emerging critical profession of the AI era — combining data architecture, ontology expertise, and domain knowledge to bridge technology and business understanding. — Tencent Cloud developer article, 2026 ([link](https://cloud.tencent.com/developer/article/2616559))

> "Without an explicit representation of [enterprise] knowledge, an agent may produce incorrect analytical results and cannot reliably incorporate feedback." — AgentOnto, arXiv:2610.23317 ([link](https://arxiv.org/abs/2610.23317))

> "At personal or small scale, KG-based agent memory is overkill — enterprise-scale deployments warrant robust solutions, but individual users benefit from lightweight document-based approaches." — HN:48919162 ([link](https://news.ycombinator.com/item?id=48919162))

> "42% of institutional knowledge remains siloed with individuals — context graphs need to not just store but actively route changes to relevant parties." — Jeff Reynar, this+that.chat ([link](https://www.thisandthat.chat/blog/everyone-is-building-a-context-graph))
