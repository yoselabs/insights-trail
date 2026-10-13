# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-10-13
**Query type:** GENERAL
**Sources:** WebSearch (multi-query), WebFetch (targeted), Hindsight/Vectorize, Letta GitHub, TextQL, arXiv, EKAW 2026/Springer, DevelopersIO/Classmethod (JP), Zenn/cybernetics (JP), 53AI (CN), Neo4j, ISWC 2026, AML Leaderboard

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 submission (OntoCast) | — (HN 429 on fetch) | 🌐 Show HN: OntoCast semantic triple extractor |
| Web (global) | 45+ pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 10 pages | — | 🇯🇵 DevelopersIO (Classmethod), Zenn/cybernetics; DDG blocked |
| Web (China) | 7 pages | — | 🇨🇳 53AI Sep 23, Juejin, Zhihu; DDG + 36kr blocked |
| arXiv | 3 papers | — | 🌐 arXiv:2610.11768 new Oct paper |
| GitHub | 4 repos | — | 🌐 Letta, Hindsight, OntoCast, Skan AOW |

---

## Synthesized Findings

### 1. [new] Hindsight Memlake: Object-Storage-Native Memory Engine at 100M+ Scale 🌐

**Claim:** Hindsight (Vectorize) announced Memlake today (Oct 13) — object-storage-native agent memory (S3/GCS) with no database, no consensus cluster, delivering 10–56× Postgres recall throughput and 26× cost reduction at 10K-employee scale.
**Evidence:**
- **Architecture:** S3/GCS/S3-compatible bucket = sole source of truth; servers are disposable caches; written in Rust for GC-free memory path; components: immutable log → indexers → segments → manifest (conditional writes)
- **Performance vs Postgres (same workload, same cluster):**
  - Small bank: 207 vs 19 recalls/sec (10.8×)
  - Large bank (210K memories): 113 recalls/sec at 113ms p99 vs 2 recalls/sec at 5.3s p99 (56× recall throughput; 47× latency)
  - Sustained write: 1,200–1,500 memories/sec vs Postgres ceiling of 55–80/sec
  - 3M-memory bank at steady state: 71ms p50, 90ms p99
- **Cost (12-month cluster, excl. LLM/GPU):**
  - 1K employees (68M memories): $3.2K Memlake vs $4.6K Postgres
  - 10K employees (680M): $15.1K vs $58.4K (3.9×)
  - 1K autonomous agents (4.9B memories): $94K vs $2.46M (26×)
  - Storage: ~4–5 KB/memory; 1 employee/year ≈ 350 MB ≈ <$0.01/mo on S3
- **Scale test:** 100M memories across 20 banks on 4 servers (6 vCPU each)
- **Deployment:** (1) Hindsight Cloud managed, (2) Dedicated cloud, (3) Your cloud (AWS/GCP, your bucket), (4) On-premises (S3-compatible)
- **Hindsight 1.0:** simultaneously announced as stable open-source release (Postgres backend); 49,000+ GitHub stars
- Sources: [Memlake blog](https://hindsight.vectorize.io/blog/2026/10/13/memlake) · [Memlake product](https://vectorize.io/memlake) · [Technical whitepaper](https://vectorize.io/memlake/whitepaper) · [Enterprise page](https://hindsight.vectorize.io/cloud-enterprise/enterprise)

---

### 2. [new] arXiv:2610.11768 "Narrow and Deep" — Domain Ontology Lifts 9B Model to 750B Level 🌐

**Claim:** Oct 8, 2026 arXiv paper (Joo & Kim, cs.SY/2610.11768): a narrow-and-deep domain ontology for a single industrial equipment system raised a 9B-parameter model to match a 750B model's performance, and improved error avoidance by ~20pp.
**Evidence:**
- **"Narrow and Deep" principle:** instead of broad cross-domain ontology, go deep on one equipment system; knowledge nodes deepened via (1) physical-relation-derived quantities (from measured points), (2) operating journal lessons embedded as knowledge nodes
- **Results:**
  - ~20pp improvement in avoiding the most plausible misjudgment per task
  - 9B-parameter model matches 750B model overall task score
  - Live runs: 12/14 successful (controlled variable within target band via invariant safety layer)
- **Key operational finding:** lessons most effective when embedded directly in ontology or prompt, NOT retrieved as separate search tool results; search-tool retrieval was less effective
- **Implications:** depth beats breadth for domain-specific industrial AI; operational history → ontology structure beats RAG over raw logs
- Sources: [arXiv:2610.11768](https://arxiv.org/abs/2610.11768) · [HTML full text](https://arxiv.org/html/2610.11768v1)

---

### 3. [new] TextQL Ontology GA (Oct 1): File-System Business KG, 12% Faster Agent Runs 🌐

**Claim:** TextQL shipped Ontology to general availability Oct 1, 2026: a Git-backed file-system approach to business knowledge that reduces agent playbook run duration by 12% and tool calls by 7%.
**Evidence:**
- **What it captures:** business definitions, data documentation, analytical methods, reusable .tql queries, operating procedures, institutional knowledge — things not derivable from database schemas alone
- **Structure:** Git-compatible directory; .md documentation, .tql queries, .py/.sql code coexist; bidirectional Git sync; changes reviewed as diffs before becoming shared knowledge
- **Performance across 45 playbooks:**
  - 12% median reduction in run duration
  - 7% median reduction in tool calls per run
  - High-adoption cohort (30 workflows): 12% faster, 9% fewer tool calls; 70% ran faster overall
- **Framing:** "Context, not capability" — Ontology is the substrate making institutional knowledge accessible to agents, not raw model improvement
- Sources: [Ontology GA blog](https://textql.com/blog/ontology-ga) · [Ontology 3.0 launch](https://textql.com/blog/ontology-v3) · [TextQL changelog](https://docs.textql.com/product/changelog) · [Analysis: context not capability](https://fourweekmba.com/ai-textql-ontology-ga-context-not-capability/)

---

### 4. [new] JP DevelopersIO 2026 Sapporo: 4-Layer Context Stack + AWS COA Demo 🇯🇵

**Claim:** Classmethod's Satoru Ishikawa presented a 4-layer context stack (Catalog → Semantic Layer → KG → Ontology) at DevelopersIO 2026 Sapporo (Oct 9); live AWS Context Ontology Accelerator demo illustrated the unstated-business-rule problem.
**Evidence:**
- **Core problem demonstrated:** "regional sales revenue" query → Kanto 1,172,500 (correct: 902,500); included wrong regions; SQL was syntactically correct but violated unstated business rule "revenue = shipped orders only"
- **4-layer stack:**
  | Layer | Purpose |
  |-------|---------|
  | Catalog | Locates data assets |
  | Semantic Layer | Defines calculations |
  | Knowledge Graph | Maps entity relationships |
  | Ontology | Enforces rules via formal logic |
- **AWS COA demo timings:** Scan=50 sec (3 tables, 18 columns); Model=2 sec; Response Tier1=1.8s, Tier2=8.9s, Tier3=36.2s
- **JP Quote:** 「データに隠れた意味を機械が読める形で渡す必要がある」("The meaning hidden in data must be conveyed to machines in machine-readable form") — Ishikawa, DevIO 2026
- Sources: [dev.classmethod.jp](https://dev.classmethod.jp/articles/20261009-devio2026-ontology/) · [Speaker Deck slides](https://speakerdeck.com/ishikawa_satoru/developersio-2026-chishiki-no-chizu-o-egaku-toha-nani-ka)

---

### 5. [new] JP Zenn/cybernetics: Counter-Argument — When Semantic Layer Makes Ontology Unnecessary 🇯🇵

**Claim:** HELLO_CYBERNETICS (Zenn, Sep 26, 2026) argues formal ontologies are unnecessary when semantic layers with adequate metadata already exist — the first substantive JP counterpoint to the ontology-as-default narrative.
**Evidence:**
- **Thesis:** "If definitions for analysis facts and meanings are complete, you can manage without adding formal ontologies or separate graph databases"
- **Concrete case:** star schema SQL JOIN answers "polyethylene samples measured at 25°C" without graph DB; ontologies add value only when: (1) sharing inference rules across orgs, (2) domain-specific classification, (3) cross-party consistent reasoning
- **Supporting research cited:** Gloaguen et al. (arXiv:2602.11988v2): static context files → no statistically significant improvement in agent success; +20-23% additional computation cost; human-written > LLM-generated explanations
- **JP Quote:** 「セマンティックレイヤーが持つ分析上の問いへの回答に必要なものは、そのツールがすでに持っている」("What the semantic layer already provides is sufficient for analysis questions it can answer")
- **Significance:** First practitioner pushback published in JP hubs on whether ontology is universally needed; complements the ongoing JP practitioner maturation away from "should we use it?" to "when is it necessary?"
- Sources: [Zenn/cybernetics](https://zenn.dev/cybernetics/articles/a3f4adf33265ce)

---

### 6. [new] CN 53AI Sep 23: POLE+O + MongoDB Unified Agent Memory Architecture 🇨🇳

**Claim:** 53AI (Sep 23, 2026) published a POLE+O + MongoDB + FastMCP architecture for building unified agent memory from scratch; 160+ mid-to-large enterprises using this pattern.
**Evidence:**
- **4-module pipeline:** ontology standardization → dual normalization/graph pipelines → unified MongoDB storage → FastMCP service layer
- **Entity model:** POLE+O (Person, Object, Location, Event, Organization) with version management via valid_from/valid_until timestamps
- **3 retrieval modes:** standard (2-hop expansion), deep (3-hop + local caching), LLM-generated MongoDB queries
- **Scale guidance:** switch MongoDB → Neo4j when queries consistently exceed 4-hop depth OR vector scale reaches billions
- **Test case:** 5 documents → 17 entity types, 34 relationship types; 1024-dimensional Voyage-3.5 embeddings
- **CN Quote:** 「本体论是读写操作之间的基础契约」("Ontology is the foundational contract between write and read operations")
- Sources: [53AI Sep 23](https://www.53ai.com/news/knowledgegraph/2026092380729.html)

---

### 7. [new] Skan AI Agentic Ontology of Work (AOW) v2.0 — Previously Uncaptured 🌐

**Claim:** Skan AI launched AOW v1.0 (Feb 10, 2026) and released v2.0: an open semantic framework defining 25 classes + 33 relationships across 4 layers as a standard vocabulary for human-AI agent coordination; OWL/JSON-LD/SHACL.
**Evidence:**
- **8 canonical entities in v1.0:** Agents, Skills, Intents, Contexts, Policies, Memory, Confidence, Outcomes
- **AOW 2.0:** 25 classes, 33 relationships, 4 organizational layers
- **Formats:** OWL, JSON-LD, SHACL, JSON Schema; platform-agnostic
- **Integration:** Skan's O2A (Observation-to-Agent) Platform for agent orchestration, telemetry, governance, learning loops
- **Framing:** "shared language that lets agents understand context, respect policies, and learn continuously"
- **Available:** GitHub, Hugging Face dataset
- Sources: [Skan press release](https://www.skan.ai/in-the-news/skan-ai-launches-the-agentic-ontology-of-work) · [GitHub repo](https://github.com/Skandotai/agentic-ontology-of-work) · [HuggingFace dataset](https://huggingface.co/datasets/skandotai/agentic-ontology-of-work)

---

### 8. [new] OntoCast — Agentic Ontology-Building from Unstructured Docs (Show HN) 🌐

**Claim:** OntoCast (Show HN, item:44423406) is an open-source framework that agentically extracts semantic triples, auto-selects or creates an ontology, and iteratively refines it from PDFs/JSON/Markdown.
**Evidence:**
- **Key innovation:** LLM-driven agentic workflow (OpenAI or Ollama) auto-selects or creates relevant ontology, then refines iteratively — addressing the "who designs the ontology?" barrier
- **Backends:** Jena Fuseki + Neo4j for KG storage
- **Use cases:** scientific papers, financial reports, clinical trial documents
- **License:** Apache
- Sources: [HN item:44423406](https://news.ycombinator.com/item?id=44423406) · [GitHub](https://github.com/growgraph/ontocast) · [Docs](https://growgraph.github.io/ontocast)

---

### 9. [update] Letta v0.34.5 (Oct 8): Vault Redaction, Workflow MCP Tools, Deep Background Subagents 🌐

**Claim:** Letta released v0.34.5 (Oct 8, 2026), adding always-on vault secret redaction, workflow scripts that invoke agent MCP tools directly, and background subagent execution at every depth level.
**Evidence:**
- **Vault secret redaction:** always-on in tool returns and user messages — memory systems no longer leak secrets through agent outputs
- **Workflow MCP invocation:** scripts can now directly call agent MCP tools, unlocking ontology/memory tool chains in automated workflows
- **Background subagents:** execute at every depth level (not just top-level), enabling deeply nested memory hierarchies
- **MEMORY.md seeding:** local agents consistently initialize on palace layout
- **Parent inheritance:** workflows inherit parent tool set and permission modes
- Sources: [v0.34.5 release](https://github.com/letta-ai/letta-code/releases/tag/v0.34.5)

---

### 10. [update] EKAW 2026 Proceedings Now Published — Springer LNAI 978-3-032-25159-6 🌐

**Claim:** EKAW 2026 (Sep 29–Oct 1, Torino) Springer LNAI proceedings are now live; previously noted as unpublished as of Oct 9.
**Evidence:**
- ISBN confirmed: 978-3-032-25159-6 (confirmed by live Springer chapter links)
- Bench4KE chapter live: https://link.springer.com/chapter/10.1007/978-3-032-25159-6_12
- AgentO chapter live: http://eprints.cs.univie.ac.at/8749/1/978-3-032-25159-6_16
- AgentO: ontology for modeling agentic AI systems (formal vocabulary for agent architectures)
- KG Re-engineering Along Ontological Continuum paper accepted (extended version: arXiv:2605.22093)
- Sources: [EKAW 2026](https://ekaw2026.di.unito.it/) · [Springer Bench4KE](https://link.springer.com/chapter/10.1007/978-3-032-25159-6_12)

---

**Still true** (ongoing threads, no new facts this run):
- fabric-iq-ontology-mcp: V2 still default; GA still Preview; retirement Jan 31, 2027 — no new Oct updates
- iswc-2026-knowledge-graph-conference: Oct 25-29 Bari, still upcoming; IBM paper + GLOW 14 papers confirmed
- ibm-iswc-2026-agentic-memory-kg: IBM "Transparent, Traceable, Deterministic" still scheduled Oct 25
- inspired-production-ontology-engineering: Oct 7 "vibe ontology" critique; no new content
- active-ontology-atlan-2026: Atlan 95% pilots failing; 38% SQL gain; no new updates
- jp-zenn-netflix-e2e-kg-autosre: Netflix AutoSRE ontology — no new content
- jp-zenn-bare64-ontology-practice: Protégé vs Fabric IQ evaluation — no new content
- cn-ccks-2026: CCKS 2026 concluded Aug; WAIE Oct 23 Shenzhen still upcoming (not yet occurred)
- cn-53ai-ontology-kg-world-model-path: Three-phase path still canonical
- dell-ai-platform-kg-semantic-layer: H1 2027 roadmap; no new updates
- okf-agent-memory-hn-bm25: OKF v0.4.4; BM25 61% vs 37%; no v0.5 found
- graphify-codebase-kg-no-vector: v0.9.53; 124K stars; no new release
- ob-caie-ontology-ai-evaluation: arXiv:2610.00529 still current
- jp-ontology-for-data-engineers-zenn: SL+ontology complementary
- jp-lightweight-ontology-fixed-queries-bigquery: fixed queries not generative; BigQuery Graph
- jp-graph-infra-ai-agents-index-free: index-free adjacency; 4 RAG types
- evoontology-self-evolving-mcp-server: arXiv:2609.15779; no new updates
- turbopuffer-v3-ann-primary-retired: v3 live; ANN-primary removed
- agentmemory-dotnet-pole-plus-o: POLE+O for .NET; 178/178 Neo4j TCK
- blitzy-coding-agents-neo4j-graph: $200M; SWE-Bench 84.95%; no new news
- hn-getcassis-entity-graph-complexity: memories/state/handoff must NOT share ontology
- memory-portability-model-upgrade: KG ±0.0020 vs NOTES ±13pp (arXiv:2609.05339)
- moosedev-nesy2026-ontology-coding-memory: 0.98–1.00 recall vs 6–27% vector
- industrial-kg-unification-287-mcp-tools: recall 1.00→0.31 without cross-system tools
- evograph-mem-failure-aware-editable: append-only insufficient for long-horizon tasks
- llm-guided-ontology-kg-construction-ijckg2026: quantized 7B–32B + schema-guided prompting (IJCKG 2026 Nov)
- trikedb-cyberagent-lightweight-ontology-yaml: 88.7% WebQSP at 250-triple budget
- aml-agent-memory-leaderboard: Cycle 2 open; Oct 31 deadline; no results yet
- hindsight-v0100-multimodal-memory: v0.10.3 (Oct 8); Memlake announced today (see §1)
- cognee-1-0-four-verb-api: v1.6.1 (Sep 24); no Oct release found
- zep-ce-retired-graphiti-open-source: Graphiti still v0.30.2; no Oct release found
- graphwise-events-oct-2026: SLS Vienna Oct 14-15 starts tomorrow; no coverage yet
- benchmark-proliferation-memory: AML Cycle 2 Oct 31 deadline; no new results
- okf-v02-provenance-trust: OKF v0.4.4 current; no v0.5 found
- okf-v01-structural-interoperability: structural interoperability; semantic gap still future work
- mem0-v2-token-efficiency: 66.6K stars; no new Oct algorithmic changes
- graphwise-oakley-semantic-layer-pe: Oakley Capital; 30%+ ARR; no new news
- semantics-2026-ghent: concluded Sep 17; no new Oct news
- databricks-genie-ontology: no new October updates
- databricks-context-engineer-cert: $200/90min; GA Jul 29; no new updates
- memorax-ai-endogenous-memory-funding: AML Cycle 1 #1; no new Oct updates
- benchmark-vendor-inflation-measured: Mnemoverse Q3 20pp vendor inflation; confirmed standing
- hindsight-memory-benchmark-leader: 94.6% LME; Memlake enterprise tier now announced (§1)
- parametric-kg-storage-retrieval-gap: LoRA parametric KG stores +0.243 EM but retrieval at chance
- selective-forgetting-kg-vs-flat: KG F1=0.417 vs flat 0.468 on LME
- megamem-ultra-large-context-retrieval: 650M+ tokens; 68.22→82.26 EnterpriseRAG-Bench
- graph-personalized-memory-survey-ickg2026: lifecycle-oriented ICKG 2026 survey
- google-knowledge-catalog-context-graph: BigQuery Graph still Preview
- jp-ontology-to-tool-mechanical-generation: 12-obj/34-action YAML → 58 tools
- mem0-strands-osv3-algorithm: native AWS Strands; single-pass ADD-only
- msock-intellect-enterprise-spatial-graph: 21-dimensional Enterprise Spatial Graph
- heimdall-trust-verified-kg-coding: cross-repo KG; CPU-only; 12,800 nodes
- codebase-memory-mcp-tree-sitter-kg: ~120x token reduction; 11,860 stars
- jp-ontology-driven-graphrag-construction: entity unification 72→94%; +23pp
- jp-ontology-vs-dbt-semantic-layer-integration: OWL→dbt loses inference irreversibly
- jp-kg-vs-rag-five-query-types: KG 5/5 vs RAG 0-3/5 at scale
- jp-two-layer-memory-write-gate: hot/cold two-layer + write-gate
- ontologx-autonomous-log-kg: cybersecurity log→ontology KG (Wiley AISY)
- cn-agent-memory-os-paradigm-shift: OS-level virtual memory; vector+KG hybrid
- cn-china-agent-government-regulation: first government bounding agent authority (May 2026)
- magg-governed-kg-construction: +47% strict F1 SciERC; no predefined schema
- metaphactory-6-ontopic-virtual-kg: Ontopic acquired; metaphactory 5.9 VKG/OBDA
- memorax-code-coding-plugin: 4 memory types; Claude Code/Codex/WorkBuddy
- jp-zenn-kg-memory-entity-resolution: entity resolution = primary engineering barrier
- jp-note-semantic-layer-vs-ontology-failure: 60% projects fail without SL
- memos-memory-os-proactive-scheduling: 3-tier Memory OS; Memory Cube; Memory Marketplace
- openkg-spg-kag-skillnet-dynamic-eval: Claude 4.5 at 37.65% on dynamic eval
- jp-coa-deployment-53pct-variance: COA eliminates 53% answer variance
- aws-context-ontology-accelerator: months→days; OWL 2+HermiT; Apache 2.0
- mnemoverse-hebbian-memory: Hebbian + Rescorla-Wagner; 6 MCP tools
- neo4j-constant-cost-semantic-memory: Oct 15 workshop upcoming; NODES Nov 12
- sap-knowledge-graph-autonomous-enterprise: 452K tables; 50+ Joule Assistants
- neo4j-labs-agent-memory-nams: POLE+O; 178/178 TCK; NAMS hosted service
- jp-acro-engineering-graphrag-vs-okf-benchmark: OKF 1/26th token cost vs GraphRAG
- apache-ossie-semantic-interchange: Kyvos+Databricks; no Oct updates
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
- benchmark-proliferation-memory-dup: placeholder; no content; carries forward

---

## Cross-Source Patterns

**1. Storage-Layer Rethinking: Memory Outgrows Postgres** 🌐
- Hindsight Memlake (Oct 13): object storage replaces Postgres; 26× cheaper at agent scale; "no database" principle
- 53AI Sep 23: MongoDB → Neo4j switch guidance at 4-hop/billion-vector thresholds; no permanent lock-in
- turbopuffer v3 (prior): ANN removed as primary index after 3 structural flaws identified
- Platforms: Hindsight blog, 53AI, turbopuffer
- Quote: "Object storage is the only source of truth for memory. Memlake itself has no database, no consensus cluster, no second stateful system beside the bucket." — Hindsight Memlake whitepaper ([link](https://vectorize.io/memlake/whitepaper))

**2. Depth Over Breadth in Domain Ontologies** 🌐🇯🇵
- arXiv:2610.11768 (Oct 8): narrow+deep industrial ontology → 9B model matches 750B; lessons embedded in ontology beat search-retrieved lessons
- JP DevelopersIO 2026: 4-layer stack with ontology as formal-logic enforcement layer at top
- Inspired.org Oct 7 (prior): "vibe ontology" critique; production requires formal engineering
- Platforms: arXiv, DevelopersIO (JP), Inspired.org
- Pattern: domain-specific depth consistently outperforms broad horizontal ontologies for production agent tasks

**3. JP Community Moves to "When Is Ontology Necessary?" Debate** 🇯🇵
- Zenn/cybernetics (Sep 26): counter-thesis — semantic layer sufficient when metadata complete; +20-23% compute cost without benefit
- DevIO 2026 (Oct 9): pro-ontology: 4-layer stack, ontology = top enforcement layer, measured COA speedup
- Prior JP consensus was "always needed" — this is the first substantive disagreement entering the discourse
- Platforms: Zenn (cybernetics publication), dev.classmethod.jp

**4. POLE+O as Cross-Region Implementation Baseline** 🌐🇨🇳
- 53AI Sep 23 (CN): POLE+O + MongoDB at 160+ enterprises
- AgentMemory .NET (prior, EN): POLE+O + .NET 8/9/10; 178/178 Neo4j TCK
- HN:48337689 (prior, EN): POLE+O as practitioner starting point; "schema decides everything"
- Platforms: 53AI (CN), Neo4j blog (EN), HN (EN)
- Pattern: POLE+O (Person/Object/Location/Event/Organization) has become the de facto entity model for cross-cultural agent memory deployments in 2026

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| growgraph | Show HN: OntoCast | — (HN 429 on fetch) | — | Auto-selects and iteratively refines ontology from unstructured docs | [link](https://news.ycombinator.com/item?id=44423406) |

**Web (global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Hindsight/Vectorize | [Memlake blog](https://hindsight.vectorize.io/blog/2026/10/13/memlake) | **NEW** Oct 13 object-storage memory engine; 26× cheaper at scale |
| 🌐 | Vectorize | [Memlake product](https://vectorize.io/memlake) | Product page; "a billion memories and beyond" |
| 🌐 | Vectorize | [Memlake whitepaper](https://vectorize.io/memlake/whitepaper) | Full technical architecture |
| 🌐 | Hindsight | [Enterprise page](https://hindsight.vectorize.io/cloud-enterprise/enterprise) | Enterprise tiers; BYOC |
| 🌐 | Hindsight | [Changelog](https://hindsight.vectorize.io/changelog) | v0.10.3 (Oct 8); v1.0 stable |
| 🌐 | TextQL | [Ontology GA blog](https://textql.com/blog/ontology-ga) | **NEW** Oct 1 GA; 12% faster runs; 7% fewer tool calls |
| 🌐 | TextQL | [Ontology 3.0](https://textql.com/blog/ontology-v3) | Ontology 3.0 launched with GA |
| 🌐 | TextQL | [Changelog](https://docs.textql.com/product/changelog) | Official changelog |
| 🌐 | FourWeekMBA | [TextQL analysis](https://fourweekmba.com/ai-textql-ontology-ga-context-not-capability/) | Context not capability framing |
| 🌐 | arXiv | [2610.11768](https://arxiv.org/abs/2610.11768) | **NEW** Oct 8 narrow+deep ontology; 9B = 750B with domain ontology |
| 🌐 | arXiv | [2610.11768 HTML](https://arxiv.org/html/2610.11768v1) | Full text |
| 🌐 | Letta GitHub | [v0.34.5](https://github.com/letta-ai/letta-code/releases/tag/v0.34.5) | **UPDATE** Oct 8: vault redaction, workflow MCP, deep subagents |
| 🌐 | GitHub | [OntoCast](https://github.com/growgraph/ontocast) | **NEW** Show HN: agentic ontology extraction + refinement |
| 🌐 | OntoCast | [Docs](https://growgraph.github.io/ontocast) | OntoCast documentation |
| 🌐 | Skan AI | [AOW announcement](https://www.skan.ai/in-the-news/skan-ai-launches-the-agentic-ontology-of-work) | **NEW (prev uncaptured)** AOW v1.0/2.0; 25 classes, 33 relationships |
| 🌐 | GitHub | [AOW repo](https://github.com/Skandotai/agentic-ontology-of-work) | OWL/JSON-LD/SHACL AOW standard |
| 🌐 | HuggingFace | [AOW dataset](https://huggingface.co/datasets/skandotai/agentic-ontology-of-work) | Downloadable AOW definitions |
| 🌐 | EKAW 2026 | [Conference site](https://ekaw2026.di.unito.it/) | **UPDATE** proceedings now published |
| 🌐 | Springer | [Bench4KE chapter](https://link.springer.com/chapter/10.1007/978-3-032-25159-6_12) | Confirms LNAI 978-3-032-25159-6 live |
| 🌐 | UVienna eprints | [AgentO chapter](http://eprints.cs.univie.ac.at/8749/1/978-3-032-25159-6_16) | AgentO ontology for agentic systems |
| 🌐 | arXiv | [2605.22093 KG re-engineering](https://arxiv.org/html/2605.22093) | KG Re-engineering Along Ontological Continuum (EKAW 2026) |
| 🌐 | ISWC 2026 | [Site](https://iswc2026.semanticweb.org/) | Oct 25-29 Bari; IBM, GLOW, DMKG, ELMKE, NLP4KGC |
| 🌐 | Graphwise | [ISWC event](https://graphwise.ai/event/international-semantic-web-conference-2026/) | Graphwise at ISWC |
| 🌐 | SLS official | [semanticlayersymposium.com](https://semanticlayersymposium.com/) | Oct 14-15 Vienna; starts tomorrow |
| 🌐 | Graphwise | [SLS event](https://graphwise.ai/event/semantic-layer-symposium-2026/) | Graphwise presenting at SLS |
| 🌐 | Neo4j | [NODES 2026](https://neo4j.com/nodes/) | Nov 12; Road to NODES Oct 15 upcoming |
| 🌐 | Neo4j | [Multi-agent shared memory session](https://neo4j.com/nodes-ai/agenda/multi-agent-shared-graph-memory-building-collective-knowledge-for-agents/) | NODES session on collective KG memory |
| 🌐 | AML | [Leaderboard](https://agentmemoryleaderboard.ai/) | Cycle 2 open; Oct 31 deadline; no results |
| 🌐 | Mnemoverse | [Q3 2026 comparison](https://mnemoverse.com/docs/library/ai-memory-solutions-2026-q3) | Letta 52.2%, Mem0 50.0%, Zep/Graphiti 37.0% |
| 🌐 | arXiv | [2609.25607 ArticleMiner](https://arxiv.org/abs/2609.25607v1) | Ontology-guided KG construction from scientific publications; Sci-K@ISWC 2026 |
| 🌐 | arXiv | [2609.24971 DolphinBench](https://arxiv.org/pdf/2609.24971) | Pareto frontier of agent memory capability vs cost |
| 🌐 | ScienceDirect | [AI-KM v6.6.1](https://www.sciencedirect.com/science/article/pii/S235271102600347X) | AI-KM platform: agentic skills + ontology-driven knowledge modeling |
| 🌐 | Atlan | [Memory frameworks 2026](https://atlan.com/know/best-ai-agent-memory-frameworks-2026/) | Mem0/Zep/Letta/LangMem/Cognee comparison |
| 🌐 | AI Agent Store | [Oct 11 news](https://aiagentstore.ai/ai-agent-news/this-week) | Week of Oct 11 agent news index |
| 🌐 | Graphify | [graphify.com](https://graphify.com/) | v0.9.53; 124K stars; codebase KG |
| 🌐 | Graphiti | [GitHub releases](https://github.com/getzep/graphiti/releases) | Still v0.30.2; no Oct release |
| 🌐 | Cognee | [Changelog](https://www.cognee.ai/changelog) | v1.6.1 (Sep 24); no Oct release |
| 🌐 | Letta | [Memory Models blog](https://www.letta.com/blog/towards-agents-that-learn/) | Agents that learn via meta-RL + memory models |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | dev.classmethod.jp | [DevIO 2026 Sapporo](https://dev.classmethod.jp/articles/20261009-devio2026-ontology/) | **NEW** Oct 11; 4-layer context stack; AWS COA demo; unstated-rule problem |
| 🇯🇵 | Speaker Deck | [DevIO slides](https://speakerdeck.com/ishikawa_satoru/developersio-2026-chishiki-no-chizu-o-egaku-toha-nani-ka) | Slide deck for DevIO 2026 Sapporo |
| 🇯🇵 | Zenn/cybernetics | [Ontology necessary?](https://zenn.dev/cybernetics/articles/a3f4adf33265ce) | **NEW** Sep 26; counter-thesis: SL sufficient when metadata complete |
| 🇯🇵 | Zenn/knowledge_graph | [Netflix QCon](https://zenn.dev/knowledge_graph/articles/netflix-qcon-e2e-knowledge-graph) | E2EGraph unified observability ontology; AutoSRE |
| 🇯🇵 | Zenn/bare64 | [Protégé vs Fabric IQ](https://zenn.dev/bare64/articles/ontology-data-platform-practice) | Lightweight vs heavyweight ontology evaluation |
| 🇯🇵 | Zenn/bare64 | [Data engineer ontology intro](https://zenn.dev/bare64/articles/ecac1bbf510ce4) | SL+ontology complementary; Fabric/Neo4j/Palantir |
| 🇯🇵 | Zenn/mbk_digital | [Lightweight ontology BigQuery](https://zenn.dev/mbk_digital/articles/next-tokyo-2026-ontology) | Fixed SQL, not generative; BigQuery Graph |
| 🇯🇵 | Qiita/yohei1126 | [Graph infra AI agents](https://qiita.com/yohei1126/items/19ecb7f37ac7ef9c3c80) | Index-free adjacency; 4 RAG types |
| 🇯🇵 | CyberAgent | [trikedb](https://developers.cyberagent.co.jp/blog/archives/65814/) | YAML/RDF; Oxigraph; model2vec; MCP; 88.7% WebQSP |
| 🇯🇵 | Qiita/hisaho | [GraphRAG × Ontology](https://qiita.com/hisaho/items/175ca3f80f35abf195f0) | Entity unification 72→94%; +23pp accuracy |
| 🇯🇵 | Zenn/aws_japan | [COA deployment](https://zenn.dev/aws_japan/articles/context-ontology-accelerator-deploy) | 53% answer variance eliminated |
| 🇯🇵 | note/_kihonushi | [SL before ontology](https://note.com/_kihonushi/n/nad1b98d60300) | 60% failure without SL (Gartner) |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | 53AI | [POLE+O unified memory Sep 23](https://www.53ai.com/news/knowledgegraph/2026092380729.html) | **NEW** Sep 23; POLE+O + MongoDB + FastMCP; 160+ enterprises |
| 🇨🇳 | 53AI | [Three-phase path Jul 28](https://www.53ai.com/news/knowledgegraph/2026072804689.html) | Ontology → KG → World Model path |
| 🇨🇳 | 53AI | [Practical guide Aug 6](https://www.53ai.com/news/knowledgegraph/2026080686240.html) | Minimum viable ontology (8 types); 5 mistakes |
| 🇨🇳 | 53AI | [EvoOntology Sep 26](https://www.53ai.com/news/zhinenghuagaizao/2026092626145.html) | "Graph的尽头是自进化Ontology" |
| 🇨🇳 | Juejin | [KG in Agent era](https://juejin.cn/post/7659258669087211554) | 4 strategic roles; self-evolving schema |
| 🇨🇳 | Juejin | [China agent regulation](https://juejin.cn/post/7662583562122166310) | First government bounding agent authority |
| 🇨🇳 | Zhihu | [Agent memory survey](https://zhuanlan.zhihu.com/p/2021713241647096178) | 3-layer architecture; vector+KG hybrid |
| 🇨🇳 | Tencent Cloud | [TBox/ABox](https://cloud.tencent.com/developer/article/2540120) | TBox (LLM) / ABox (human validates) |
| 🇨🇳 | CSDN | [LLMs reshape ontology engineering](https://blog.csdn.net/xianggll/article/details/157021978) | TBox generation by LLM; human validates ABox |
| 🇨🇳 | CCKS 2026 | [sigkg.cn/ccks2026](https://sigkg.cn/ccks2026/) | 20th national KG + semantic computing (Aug 21-23) |
| 🇨🇳 | CSDN | [WAIE 2026 Oct 23](https://www.csdn.net/article/2026-09-29/166842145) | China AI Agent benchmarks bluebook (Oct 23 Shenzhen) |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no direct access)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 0 videos (not searched directly)
├─ 🟢 HN: 1 submission (OntoCast, item:44423406) │ — pts (HN 429) │ — comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (Bluesky=OK per health; minimal on-topic posts found)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 45+ pages │ 🇯🇵 12 │ 🇨🇳 11
└─ 🗣️ Top voices: Younghwan Joo & Sung-il Kim (arXiv:2610.11768), Satoru Ishikawa (DevIO Classmethod) │ Zenn/cybernetics, 53AI, Hindsight/Vectorize
```

---

## Out of Scope but Notable

- **Letta "Memory Models: Towards Agents That Learn" (Jun 2026):** Proposes meta-RL–optimized memory models specialized for context generation and curation — treating memory itself as a learnable model, not just a store. Crosses into agent-harnesses territory but the framing (memory as a trained model) is a distinct paradigm from structured KG memory. [Letta blog](https://www.letta.com/blog/towards-agents-that-learn/)
- **AI Weekly Oct 1 (Wh1isper's Blog):** [blog.wh1isper.top/2026/10/04/ai-weekly-2026-10-04/] — covers OpenAI dots (resident agents with cloud computers, persistent execution), Gemini 4 Argon — both push persistent agent infrastructure that intersects with knowledge/memory systems but belong in agent-harnesses / open-models-geopolitics topics.

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked for both JP and CN queries (same as Oct 9 run). Fell back to native-language WebSearch.
- **Reddit:** No direct access (r/KnowledgeGraphs, r/MachineLearning, r/LocalLLaMA absent)
- **Bluesky:** Health=OK per SOURCE HEALTH; Bluesky posts found were not on-topic
- **HN (OntoCast):** HTTP 429 on direct fetch; submission data partial (no score/comment count confirmed)
- **36kr (CN):** Blocked by ByteDance/Volcano Engine security gate; article on "2026 AI Memory Inaugural Year" could not be fetched
- **ISWC 2026 proceedings:** Conference Oct 25-29, not yet occurred; IBM paper, GLOW 14 papers — content previewed, not yet delivered
- **SLS Vienna (Oct 14-15):** Starts tomorrow; no coverage yet
- **AML Cycle 2:** Deadline Oct 31; no submission results
- **WAIE 2026 (Oct 23, Shenzhen):** Not yet occurred; China AI Agent benchmarks bluebook not yet published
- **EKAW proceedings:** Now confirmed published (Springer LNAI live) but full paper list not enumerated this run
- **Coverage estimate:** ~75% — strong on tool releases (Memlake, Letta v0.34.5, TextQL Ontology GA), new arXiv paper, JP/CN hub coverage; weaker on social engagement, Reddit, upcoming-conference content; no Graphiti/Zep October release found

---

## Key Quotes

> "Object storage is the only source of truth for memory. Memlake itself has no database, no consensus cluster, no second stateful system beside the bucket." — Hindsight Memlake whitepaper ([link](https://vectorize.io/memlake/whitepaper))

> "Operating lessons proved most effective when integrated directly into the ontology or included in prompts, rather than accessed via search tools." — arXiv:2610.11768 (Joo & Kim) ([link](https://arxiv.org/abs/2610.11768))

> "The meaning hidden in data must be conveyed to machines in machine-readable form" — 「データに隠れた意味を機械が読める形で渡す必要がある」 — Satoru Ishikawa, DevelopersIO 2026 Sapporo ([link](https://dev.classmethod.jp/articles/20261009-devio2026-ontology/))

> "If definitions for analysis facts and meanings are complete, you can manage without adding formal ontologies or separate graph databases." — HELLO_CYBERNETICS, Zenn/cybernetics, Sep 26, 2026 ([link](https://zenn.dev/cybernetics/articles/a3f4adf33265ce))

> "Ontology is the foundational contract between write and read operations." — 「本体论是读写操作之间的基础契约」 — 53AI Sep 23, 2026 ([link](https://www.53ai.com/news/knowledgegraph/2026092380729.html))

> "Context, not capability — the Ontology is what makes institutional knowledge accessible to agents." — FourWeekMBA on TextQL Ontology GA ([link](https://fourweekmba.com/ai-textql-ontology-ga-context-not-capability/))

> "An agent that books, approves, reorders or escalates acts on what it believes, at machine speed, and nobody reads the reasoning first." — Graham McLeod, Inspired.org (Oct 7, prior run) ([link](https://www.inspired.org/news/2026/10/7/from-shared-meaning-to-reliable-agents-engineering-an-ontology-you-can-trust-in-production))
