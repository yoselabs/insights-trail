# Knowledge Ontology & Agent Memory — Daily Briefing
**Date:** 2026-11-10
**Query type:** GENERAL
**Sources:** last30days (HN, Reddit, X, GitHub, Web), WebSearch (EN/JP/CN), WebFetch (Neo4j, Salesforce, PhoenixAI, Anthropic coverage, GitHub)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 12 stories | 996 pts, 451 comments | 🌐 Thinker (Show HN Nov 5); OpenRecall; KG/ontology threads |
| Reddit | 3 threads (partial) | 115 upvotes, 22 comments | ⚠ HTTP 403 after 3 items; r/OntologyEngineering adjudication layer |
| X/Twitter | 3 posts | 5 likes, 8 reposts | 🌐 @Connected_Data, @smobilefactory |
| GitHub | 12 items | 6 comments | 🌐 OpenRecall, NornicDB, Thinker, MELD |
| Web (global) | 25 pages | — | 🌐 Anthropic, Neo4j, Salesforce, PhoenixAI, NODES 2026 sessions |
| Web (Japan) | 4 pages | — | 🇯🇵 Qiita (Tomcat-zhou Nov 8), note.com (hirokaji) |
| Web (China) | 7 pages | — | 🇨🇳 Juejin (JitKnow 4.8), CSDN, 53AI, Zhihu |

---

## Synthesized Findings

### 1. [new] Anthropic "Components of Agent Memory" (Nov 6, 2026): Dreaming Triples Performance; Fixed Rules Backfire 🌐

**Claim:** Anthropic published the first formal empirical study of their own agent memory architecture — a 4-layer stack (transcripts → notes → representations → injected context). Key results: offline "dreaming" lifts CL-Bench on a 25-question wiki task from 13% to 48%; prescriptive save-rules cost Opus 4.7 and Opus 5 "much of their gain"; 9 organized files outperform 413 scattered files.
**Evidence:**
- **CL-Bench:** Opus 5.5 goes 0.655 → 0.838 with memory; dreaming (2→128 sessions) lifts wiki-only from 13% → 48%
- **Rules backfire:** "record only failures" directive caused both Opus 4.7 and Opus 5 to lose most gains from memory access alone; write purpose, not constraints
- **File count:** Pokémon Red task — Sonnet 3.7 creates 413 files, earns 1 badge; Fable 5 uses 9 organized files, earns 4 badges
- **Wiki + search:** 61% vs 53% search-only; saves ~20K tokens/question
- **Parallel agents:** single shared table retains 72% of facts; topic-separated files → 100%
- **Always-loaded layer:** Claude Code reads only first 200 lines / 25KB of MEMORY.md; keep small
- **Author:** Lance Martin
- **JP uptake:** Qiita/Tomcat-zhou (Nov 8) translated to 7 concrete measures; Sonnet 4.6 improves 0.330 → 0.641 when prompted to test memory vs findings
- **Sources:** https://ai-tldr.dev/releases/anthropic-components-of-agent-memory/ · https://dev.to/piekwerk/anthropics-agent-memory-study-fixed-save-rules-cost-claude-its-gains-and-9-files-beat-413-3m9m · https://qiita.com/Tomcat-zhou/items/32c085c83e173d115468 · https://aipolix.com/en-us/news/anthropic-components-of-agent-memory-dreaming
- **Platforms:** Web (global), Web (Japan)

---

### 2. [new] Neo4j Ontology Graph Specification (Nov 5, 2026): Open YAML/JSON Standard for Domain Ontologies 🌐

**Claim:** Neo4j published an open-source YAML/JSON specification for domain ontologies under Apache 2.0 — third vendor in one week (after NVIDIA Auto Ontology Nov 1 and Snowflake Business Ontology) converging on the same conclusion: ground agents in formal semantic layers, not bigger prompts.
**Evidence:**
- **Format:** YAML or JSON, validated against published JSON schema; semantic versioning
- **Defines:** nodes/relationships with stable IDs, descriptions, aliases, full Neo4j type system (temporal, spatial, vector), cardinality constraints, integrity rules, external standard references
- **SDKs:** JVM, JavaScript/TypeScript, Go
- **AI-first rationale:** "An agent querying a graph needs to know that 'Account' could mean a bank account or a payment account"
- **Authors:** Jesús Barrasa and Oskar Hane, published Nov 5
- **Three-vendor convergence:** NVIDIA Auto Ontology (Nov 1) + Snowflake Business Ontology (Expedition 2026) + Neo4j Ontology Graph Spec (Nov 5) — independent vendors within 1 week
- **Sources:** https://neo4j.com/blog/developer/the-neo4j-ontology-graph-specification-a-pragmatic-open-ai-first-approach/ · https://github.com/neo4j/ontology-graph-spec · https://neo4j.com/docs/ontology-graph-spec/format/getting-started/
- **Platforms:** Web (global)

---

### 3. [new] Salesforce Agentforce Memory: 1.8x Explicit Facts, 2.2x Time-Varying Facts via Policy Change Alone (Nov 3, 2026) 🌐

**Claim:** Salesforce published Agentforce Memory update (Nov 3) showing 1.8x improvement in explicitly stated facts and 2.2x in time-varying facts recalled — achieved by policy change alone, with no architecture changes, evaluated on the public ConvoMem benchmark.
**Evidence:**
- **1.8x explicit facts:** updated policy retains more of what customers say directly
- **2.2x time-varying facts:** treats updates as corrections to existing knowledge, not new parallel entries
- **Architecture unchanged:** "Agentforce Memory still runs on the architecture it launched with"
- **Benchmark:** ConvoMem (public); tests run in live production environments
- **GA date:** September 2026
- **Significance:** demonstrates that memory policy design drives large gains without infrastructure changes
- **Sources:** https://www.salesforce.com/blog/agentforce-memory-update/ · https://dev.to/aml-/your-agent-remembers-the-old-fact-can-it-use-the-update-4l56
- **Platforms:** Web (global)

---

### 4. [new] PhoenixAI Contextbase (Nov 4, 2026): Five-Type Unified Context Infrastructure for Agents 🌐

**Claim:** PhoenixAI (StarRocks creators) launched Contextbase — the first unified context infrastructure that co-locates Semantics, Knowledge, Memory, Traces, and Evaluations in one database alongside business data, eliminating cross-system context assembly.
**Evidence:**
- **Five types:** Semantics (Semantic SQL entity/metric definitions), Knowledge (versioned specs, playbooks), Memory (agent-written from prior work), Traces (model+tool call records with tokens/cost), Evaluations (test scores + live traffic)
- **Co-location:** same cluster as business data; one query, one permission set
- **Availability:** private preview Nov 4; free trial at phoenixdata.ai
- **Quote:** "An agent is only as good as its context, and today it has to glue that context together from separate systems on every turn" — James Li, CEO
- **Also:** Dash0 observability (November changelog) added Agent0 memory across Chat/Slack/Linear/MCP — observability tools now shipping native agent memory
- **Sources:** https://www.prnewswire.com/news-releases/phoenixai-launches-contextbase-the-context-infrastructure-for-ai-agents-302929251.html · https://www.hpcwire.com/bigdatawire/this-just-in/phoenixai-launches-as-the-agentic-ai-database-and-names-rick-underwood-president/ · https://www.dash0.com/changelog/archive/2026/11
- **Platforms:** Web (global)

---

### 5. [new] OpenRecall v0.3.0 (Nov 4) + Thinker (Nov 5): Zero-Knowledge Memory and Dependency-Keyed Context Cache 🌐

**Claim:** Two new agent memory tools launched via Show HN on Nov 3-5: OpenRecall (end-to-end encrypted ZK memory, v0.3.0) and Thinker (dependency-keyed knowledge cache over MCP, 7-14% wall time cut).
**Evidence:**

**OpenRecall:**
- End-to-end encrypted; server stores only ciphertext; self-hostable
- MCP server; shared memory across Claude Code, Zero, OpenClaude, Cursor, Codex, Gemini CLI
- v0.2.1 (Nov 3): organized shared vs project memory; v0.3.0 (Nov 4): latest
- Sources: https://github.com/Twigpine/openrecall · https://github.com/Twigpine/openrecall/releases/tag/v0.2.1

**Thinker:**
- Dependency-keyed notes served over MCP; cache maintained under daily token cap
- Stale detection: code change → note flagged → re-verify every 4 hours max
- **Metrics:** 7-14% wall time reduction; 18-21% input token reduction on real tasks
- With Claude Fable: cut wall time, lowered token usage, raised correctness
- Sources: https://thinker.sh/how-it-works · https://github.com/yoavshmariahu/thinker · https://i.buzzing.cc/en/showhn/posts/2026/45/en_hn_2026_11_05__50383228/

---

### 6. [new] NODES 2026 Sessions Published: "Missing Layer" = Human AI Reasoning Traces; MemMachine OSS 🌐

**Claim:** NODES 2026 (Nov 12) video content already published reveals two notable systems: Luminaria Memo (captures human AI sessions into Neo4j KG via MCP, arguing human reasoning traces are the missing layer) and MemMachine (open-source provider-independent memory layer backed by Neo4j + PostgreSQL).
**Evidence:**

**Luminaria Memo (Doriana Negruț):**
- Captures every Claude session (Code, Desktop, claude.ai) into private Neo4j KG in EU
- 12 MCP tools; hybrid search: semantic (cosine+recency weighted) + keyword + multi-parameter
- Multi-hop traversal across sessions via shared tags — finds connections "isolated chunks can't"
- Quote: "the richest knowledge — the reasoning traces of humans working with AI — disappears after every session"
- URL: https://luminaria.so/ · https://neo4j.com/videos/live-from-nodes-2026-the-missing-layer-why-ai-memory-should-start-with-humans-not-agents/

**MemMachine (Christian Kniep, open source):**
- Episodic memory (graph, Neo4j), profile memory (SQL), working memory (short-term)
- Provider-agnostic: OpenAI, AWS Bedrock, Ollama, any OpenAI-compatible
- arXiv:2604.04853 — "Ground-Truth-Preserving Memory System for Personalized AI Agents"
- URL: https://github.com/MemMachine/MemMachine · https://neo4j.com/videos/nodes-ai-2026-memmachine-agents-that-learn-memory-that-lasts/ · https://memmachine.ai/

**Multi-Agent Shared Graph Memory:**
- Conflict resolution, versioning, provenance; belief updates as first-class nodes
- Practical Cypher demonstrations; real-world RAG + agent applications
- URL: https://neo4j.com/videos/nodes-ai-2026-multi-agent-shared-graph-memory-building-collective-knowledge-for-agents/

**Additional:** neo4j-labs/meta-knowledge-graph: self-improving KG memory layer, harness-agnostic; lifecycle hooks capture sessions; LLM extraction loop distills learnings
- URL: https://github.com/neo4j-labs/meta-knowledge-graph

---

### 7. [new] JitKnow 4.8 (CN, Nov 3, Juejin): Enterprise KB Upgrades from Pure Vector to Ontology+KG Retrieval 🇨🇳

**Claim:** JitKnow (CN enterprise KB platform) v4.8 upgrades its retrieval from pure vector search to "ontology-driven + knowledge graph enhancement" — the first named CN enterprise product to ship this upgrade in a minor version release.
**Evidence:**
- **Entity Unification (实体归一):** AI reads all documents, identifies synonymous entity names, merges into standard canonical entity; administrators correct standard names and manage aliases
- **Controllable extraction:** replaces black-box AI-auto extraction; administrators explicitly define entity types and relationship schemas before extraction
- **Headline claim:** "AI answers no longer confidently making things up" (一本正经地胡说八道)
- **Market context:** CSDN 2026 AI Agent engineer roadmap now includes ontology literacy as baseline requirement in CN enterprise job market
- **Sources:** https://juejin.cn/post/7703743273756475419 · https://know.jitword.com/ · https://blog.csdn.net/qq_17859117/article/details/163308287
- **Platforms:** CN (Juejin, CSDN)

---

### 8. [new] MELD Protocol (arXiv:2608.16357): Federated Agent Memory Without Silent Overwrite 🌐

**Claim:** MELD (arXiv:2608.16357, Lovén et al.) defines a state-synchronization protocol where contradictions in distributed agent memories are preserved for adjudication, never silently overwritten — directly answering the r/OntologyEngineering thread asking "what if ontologies couldn't be silently overwritten?"
**Evidence:**
- **Protocol:** PROV-style evidence on every Claim; semantic (not textual) merge; canonical trust hierarchy
- **Core rule:** contradiction detected → preserved for later adjudication, never silently resolved
- **Quote:** "No existing protocol allows two agents' memories to reconcile facts phrased differently, link related facts held separately, or reconcile contradictory knowledge without silently discarding claims"
- **Related:** Reddit r/OntologyEngineering (Oct 29): community independently designing adjudication layers for agent ontologies (11 pts, 7 comments)
- **Also:** StateFuse — deterministic conflict-preserving memory with immutable history; TOKI — bitemporal operator algebra for contradiction resolution (arXiv:2606.06240)
- **Sources:** https://arxiv.org/abs/2608.16357 · https://github.com/Future-Computing-Group/meld-experiments · https://www.reddit.com/r/OntologyEngineering/comments/1xi521v/what_if_ontologies_couldnt_be_silently/
- **Platforms:** Web (global), Reddit

---

### 9. [new] NornicDB: Graph+Vector DB with 3-Tier Cognitive Memory Decay (7/69/693 days) 🌐

**Claim:** NornicDB is a new open-source graph+vector database implementing policy-based cognitive memory decay inspired by human memory science: episodic (7-day half-life), semantic (69-day), procedural (693-day).
**Evidence:**
- **Three tiers:** episodic = chat context/sessions (7d half-life), semantic = facts/decisions (69d), procedural = skills/patterns (693d)
- **Tech:** Neo4j Bolt/Cypher compatible; GPU acceleration; tritemporal MVCC; sub-ms HNSW vector search
- **Features:** Auto-TLP, policy-based decay, MCP server
- **Use cases:** KG-RAG, canonical truth stores, agent memory, knowledge systems
- **Sources:** https://github.com/orneryd/NornicDB
- **Platforms:** Web (global), GitHub

---

### 10. [update] Connected Data London 2026 (Nov 11-12): CDL Knowledge Graph Released as Open Community Resource 🌐

**Claim:** New fact since Nov 6 — the Connected Data Knowledge Graph has been released as an open KG representing collective knowledge of ~300 KG/ontology experts, available to the community. Conference starts tomorrow (Nov 11).
**Evidence:**
- **CDL KG:** curated open knowledge graph from ~300 expert contributors; available as community resource
- **Ontology Engineering & Practice Track:** dedicated track; Jessica Talisman presenting "Context Graphs, Context Layers, and the Semantic Renaissance"
- **Also:** @Connected_Data (Nov 9): "Everyone is talking about agent memory and enterprise knowledge graphs, but very few people have noticed they're turning into the same thing" — framing CDL 2026 as the place this convergence becomes explicit
- **Sources:** https://2026.connected-data.london/ · https://www.connected-data.london/post/cdl-2026-announcement · https://2026.connected-data.london/stage/ontology-engineering-practice-track/ · https://x.com/Connected_Data/status/2119882273637933094
- **Platforms:** Web (global), X

---

**Still true** (no new fact since last run):

- **Memory Tax (arXiv:2610.34073):** 90/99 conditions plain RAG beats dedicated memory; 5.2–232M token overhead; source-augmented retrieval mitigates — `memory-tax-rag-outperforms-memory`
- **Route to Remember (arXiv:2611.05636, NeurIPS PALM):** OPSD hybrid weight+text memory — `route-to-remember-opsd-hybrid-memory`
- **RAGFlow v1.0.0-rc3 + ontology PR #21413 (Oct 30):** evidence sufficiency + ontology compilation pending merge — `ragflow-ontology-service-v1-rc3`
- **Oracle AI Agent Memory 26.8:** graph-aware retrieval with supersedes/contradicts tagging; image memory — `oracle-ai-agent-memory-26-8`
- **PuppyGraph Zero-ETL (53AI Nov 3):** 6-hop queries across billions of edges ≤3s — `puppygraph-zero-etl-six-hop`
- **OKF Agent Memory v0.8.0 (Nov 5):** scope isolation + write protection + conflict fork hardening; still latest — `okf-agent-memory-hn-bm25`, `okf-v02-provenance-trust`, `okf-v01-structural-interoperability`
- **NVIDIA Auto Ontology (Nov 1):** Apache 2.0; 2.4K+ stars; 5-step pipeline; 90% ontology build time reduction — `nvidia-auto-ontology-open-source`
- **Hindsight v1.2.0 (Nov 3):** hs-rerank-1 default; 2.5x cheaper/2x faster — `hindsight-v120-proprietary-models`, `hindsight-memory-benchmark-leader`
- **FalkorDB GraphRAG SDK v1.6.0 (Nov 2):** agentic retrieval + 8-tool MCP server — `falkordb-graphrag-sdk-v160-agentic`
- **MemSkill (NeurIPS 2026):** learnable memory ops; 70% token reduction vs LightMem — `memskill-neurips-2026-learnable-memory-skills`
- **Letta Code v0.34.37-39 (Nov 2):** JSONL logging + session keepalive — `letta-code-v03437-v03439-nov2`
- **53AI telecom ontology-driven context (Oct 30):** 98.6% recall, 83.5% SQL first-pass — `cn-53ai-ontology-context-engineering-telecom`
- **AML Cycle 2:** eval closed Nov 4; official results still expected mid-November — `aml-agent-memory-leaderboard`
- **NODES 2026 (Nov 12):** 2 days away; Andrew Ng + Eifrem keynotes — `nodes-2026-conference`
- **BM25 60.5% beats all commercial memory (Mem0 25-36%, Zep 25-44%) at 1/100th cost — `bm25-beats-commercial-memory`
- **past.dev #1 BEAM+DolphinBench truth-tracking — `past-dev-beam-dolphinbench`
- **MAGMA 4-graph architecture (arXiv:2601.03236): 0.700 LoCoMo — `magma-multi-graph-agent-memory`
- **Zep CE discontinued; Graphiti sole OSS; v0.31.2 (Oct 20) still latest; Nov 9 non-release commit — `zep-ce-retired-graphiti-open-source`
- **Zep v4 Context API; hyperedges — `zep-v4-context-api-hyperedges`
- **Mem0 graph memory locked to $249/mo Pro; OSS entity linking only — `mem0-graph-memory-oss-removed`, `mem0-v2-token-efficiency`
- **Semantica v0.7.0 (14.5K stars); PROV-O; BigQuery/Redshift — `semantica-oss-graph-native-context`
- **Letta Pro: MemFS + dreaming cloud tier — `letta-pro-cloud-tier`
- **Neo4j Context Engine private preview; NAMS POLE+O 178/178 TCK — `neo4j-context-engine-launch`, `neo4j-labs-agent-memory-nams`
- **AgentKG v0.14.0: MCP-integrated conversational KG memory — `agentkg-v0130-conversational-memory-kg`
- **AllegroGraph 9.1 + GraphTalker 2.0: KMWorld 2026 — `allegrograph-graphtalker-2-context-management`
- **Grafana Knowledge Graph GA in all Grafana Cloud stacks — `grafana-knowledge-graph-ga`
- **Microsoft Fabric IQ + MCP ontology agent (public preview) — `fabric-iq-ontology-mcp`
- **Graphwise: Oakley Capital; Adobe AEM + eval tools; CDL 2026 attending — `graphwise-events-oct-2026`
- **Forrester Q4 2026 Context Layer Landscape; Q1 2027 Wave scoped — `forrester-context-layer-landscape`
- **Context graph convergence: AlphaSense, Google, Day AI, ZoomInfo, Neo4j, NVIDIA, Grafana, Snowflake — `context-graph-convergence-enterprise`
- **ISWC 2026 proceedings (96 papers, LNCS 17126-17128) standing — `iswc-2026-knowledge-graph-conference`, `iswc-2026-main-track-papers`
- **IBM ISWC 2026: agentic memory via KGs (open sourced) — `ibm-iswc-2026-agentic-memory-kg`
- **Dell AI Platform KG + Semantic Layer H1 2027 — `dell-ai-platform-kg-semantic-layer`
- **LangChain context rot + 5 techniques — `langchain-context-rot-deep-agents`
- **IJCKG 2026 (Nov 19-21, Bangkok): 9 days away — `llm-guided-ontology-kg-construction-ijckg2026`
- **JP: COA 53% variance elimination; entity resolution at integration time; SL→ontology→MCP path — `jp-devio2026-4-layer-context-stack`, `jp-coa-deployment-53pct-variance`
- **CN: ontology+KG strategic return; TBox/ABox split; MemOS 11.7K stars; 53AI three-phase path — `cn-ontology-strategic-return`, `cn-53ai-ontology-kg-world-model-path`
- **JP: two graphs for agents (note.com/hirokaji): execution graph + semantic graph — newly surfaced but conceptually matches existing JP coverage
- **Mnemoverse 20pp vendor inflation confirmed; Mnemoverse Hebbian memory — `benchmark-vendor-inflation-measured`

---

## Cross-Source Patterns

### Pattern 1: Formal Architecture Studies Arrive — Not Just Principles 🌐
Appearing across: Web (global), JP (Qiita), X, HN
- Anthropic (Nov 6): first empirical CL-Bench study of agent memory with specific numbers (0.655→0.838; 13%→48%)
- Salesforce (Nov 3): first vendor-published memory policy A/B results with ConvoMem benchmark (1.8x, 2.2x)
- These convert "memory matters" principle-talk into falsifiable numbers
- Quote (dev.to/piekwerk): "9 files yielding stronger performance versus 413 files with minimal results — a stark illustration of how structure beats volume"
- JP Qiita/Tomcat-zhou (Nov 8): fastest non-English interpretation, 7 concrete measures extracted within 48 hours of Anthropic publication

### Pattern 2: Ontology Standardization Week — Three Vendors, One Conclusion 🌐
Appearing across: Web (global), CN (53AI)
- NVIDIA Auto Ontology (Nov 1): open-source, MCP+CLI+API
- Snowflake Business Ontology (Expedition 2026, ~Nov 3): ontology for structured data agents
- Neo4j Ontology Graph Spec (Nov 5): YAML/JSON, Apache 2.0, SDKs for 3 languages
- Three independent vendors converge on semantic-layer-first in one week — no coordination
- CN 53AI quote: 「知识图谱装事实，本体论定规矩，搞反顺序就白干」 ("KG stores facts, ontology defines rules — reverse the order and it's wasted work")
- @Connected_Data (Nov 9): "everyone is talking about agent memory and enterprise KGs, but very few people have noticed they're turning into the same thing"

### Pattern 3: Memory Conflict Resolution as Emerging Infrastructure Layer 🌐
Appearing across: Web (global), Reddit, HN, GitHub
- MELD protocol (arXiv:2608.16357): "preserved for adjudication, never silently resolved"
- Reddit r/OntologyEngineering (Oct 29): independent design of adjudication layers
- StateFuse: deterministic conflict-preserving memory contracts
- OKF v0.8.0 (Nov 5): Conflict Fork Hardening for multi-device sync
- TOKI (arXiv:2606.06240): bitemporal algebra for contradiction resolution
- Multiple independent teams building explicit conflict governance into memory systems

### Pattern 4: "Human Reasoning Traces as the Missing Layer" 🌐🇯🇵
Appearing across: Web (global — NODES 2026), JP (note.com)
- Luminaria Memo (NODES 2026): "richest knowledge — reasoning traces of humans working with AI — disappears after every session"
- JP note.com/hirokaji: semantic graph + Context Compiler extracts task-specific subsets; wikis are derived representations
- Anthropic: dreaming = replay human transcripts offline to extract durable lessons
- Common thread: human → machine knowledge transfer, not just machine → machine

---

## Per-Platform Tables

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic memory study (dev.to) | https://dev.to/piekwerk/anthropics-agent-memory-study-fixed-save-rules-cost-claude-its-gains-and-9-files-beat-413-3m9m | CL-Bench 0.655→0.838; dreaming 13%→48%; 9 vs 413 files |
| 🌐 | Anthropic summary (ai-tldr) | https://ai-tldr.dev/releases/anthropic-components-of-agent-memory/ | 4-layer stack overview |
| 🌐 | Anthropic (aipolix) | https://aipolix.com/en-us/news/anthropic-components-of-agent-memory-dreaming | Dreaming focus |
| 🌐 | Neo4j Ontology Graph Spec | https://neo4j.com/blog/developer/the-neo4j-ontology-graph-specification-a-pragmatic-open-ai-first-approach/ | YAML/JSON open ontology standard, Nov 5 |
| 🌐 | Neo4j spec GitHub | https://github.com/neo4j/ontology-graph-spec | Apache 2.0 SDKs (JVM/JS/Go) |
| 🌐 | Salesforce Agentforce memory update | https://www.salesforce.com/blog/agentforce-memory-update/ | 1.8x explicit, 2.2x time-varying facts |
| 🌐 | PhoenixAI Contextbase PR | https://www.prnewswire.com/news-releases/phoenixai-launches-contextbase-the-context-infrastructure-for-ai-agents-302929251.html | Five-type unified context, Nov 4 |
| 🌐 | PhoenixAI (hpcwire) | https://www.hpcwire.com/bigdatawire/this-just-in/phoenixai-launches-as-the-agentic-ai-database-and-names-rick-underwood-president/ | StarRocks creators; Rick Underwood president |
| 🌐 | NODES 2026: multi-agent shared memory | https://neo4j.com/videos/nodes-ai-2026-multi-agent-shared-graph-memory-building-collective-knowledge-for-agents/ | Conflict resolution + versioning in shared graph |
| 🌐 | NODES 2026: MemMachine | https://neo4j.com/videos/nodes-ai-2026-memmachine-agents-that-learn-memory-that-lasts/ | Open-source provider-independent memory layer |
| 🌐 | NODES 2026: Missing Layer | https://neo4j.com/videos/live-from-nodes-2026-the-missing-layer-why-ai-memory-should-start-with-humans-not-agents/ | Human AI session → KG via MCP; Luminaria Memo |
| 🌐 | Luminaria Memo | https://luminaria.so/ | Sovereign AI memory for Claude on Neo4j |
| 🌐 | MemMachine GitHub | https://github.com/MemMachine/MemMachine | Open-source memory layer; arXiv:2604.04853 |
| 🌐 | CDL 2026 | https://2026.connected-data.london/ | Nov 11-12; CDL Knowledge Graph released as open KG |
| 🌐 | CDL ontology track | https://2026.connected-data.london/stage/ontology-engineering-practice-track/ | Dedicated ontology engineering track |
| 🌐 | CDL KG announcement | https://www.connected-data.london/post/cdl-2026-announcement | Community KG from ~300 experts released |
| 🌐 | OpenRecall GitHub | https://github.com/Twigpine/openrecall | ZK end-to-end encrypted memory MCP; v0.3.0 |
| 🌐 | Thinker | https://thinker.sh/how-it-works | Dependency-keyed context cache; 7-14% wall time cut |
| 🌐 | Thinker GitHub | https://github.com/yoavshmariahu/thinker | MCP-served; stale detection |
| 🌐 | MELD arXiv | https://arxiv.org/abs/2608.16357 | Federated memory merge protocol; no silent overwrite |
| 🌐 | MELD GitHub | https://github.com/Future-Computing-Group/meld-experiments | Reference implementation + merge engine |
| 🌐 | NornicDB GitHub | https://github.com/orneryd/NornicDB | 3-tier cognitive decay; Neo4j-compatible |
| 🌐 | Dash0 changelog Nov | https://www.dash0.com/changelog/archive/2026/11 | Agent0 memory across Chat/Slack/Linear/MCP |
| 🌐 | NODES 2026 meta-KG | https://github.com/neo4j-labs/meta-knowledge-graph | Self-improving harness-agnostic memory layer |
| 🌐 | Lenny's Memory (Neo4j blog) | https://neo4j.com/blog/developer/meet-lennys-memory-building-context-graphs-for-ai-agents/ | Context graphs for AI agents pattern |
| 🇯🇵 | Qiita Tomcat-zhou | https://qiita.com/Tomcat-zhou/items/32c085c83e173d115468 | 7 concrete measures from Anthropic memory study; Nov 8 |
| 🇯🇵 | note.com hirokaji | https://note.com/tasty_dunlin998/n/n758be099b22a | Two-graph thesis: execution + semantic graph |
| 🇨🇳 | Juejin JitKnow 4.8 | https://juejin.cn/post/7703743273756475419 | Ontology+KG retrieval upgrade; entity unification |
| 🇨🇳 | CSDN AI engineer roadmap | https://blog.csdn.net/qq_17859117/article/details/163308287 | Ontology as baseline CN enterprise AI job requirement |
| 🇨🇳 | 53AI Nov 3 | https://www.53ai.com/news/knowledgegraph/2026110369780.html | KG stores facts, ontology defines rules (ongoing) |
| 🇨🇳 | Juejin RAG retrieval (CN Anthropic) | https://juejin.cn/post/7705240185218891811 | Contextual retrieval −49% retrieval failure; Nov 8 |
| 🇨🇳 | Zhihu 3D memory framework | https://zhuanlan.zhihu.com/p/1986213905320661415 | Morphology-Function-Dynamics framework survey |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| yoavshmariahu | Show HN: Thinker – Trim context and cache knowledge to extend agent usage limits | 4 | 2 | "dependency-keyed notes served over MCP" | https://thinker.sh/how-it-works |
| — | Openrecall: unified zero knowledge proof memory for SI agents | 3 | 4 | "end-to-end encrypted, server stores only ciphertext" | https://github.com/Twigpine/openrecall |
| — | Verification Is Not Knowledge: Science needs more than answers | 245 | 142 | "verification ≠ knowledge" | https://blog.cosmos-institute.org/p/verification-is-not-knowledge |
| — | Knowledge Is Not Experience | 5 | 4 | — | https://graybeard.ing/knowledge-is-not-experience/ |
| — | Google Antigravity for Knowledge Work | 5 | — | — | https://antigravity.google/blog/antigravity-for-knowledge-work/ |

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/OntologyEngineering | What if ontologies couldn't be silently overwritten? | 11 | 7 | "All three collapse the distinction between what was recorded and what is current" | https://www.reddit.com/r/OntologyEngineering/comments/1xi521v/ |
| r/BestGitHubRepos | (agent memory tool, partial) | — | — | — | — |
| r/LangChain | (partial) | — | — | — | — |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Connected_Data | "Everyone is talking about agent memory and enterprise KGs, but very few people have noticed they're turning into the same thing" | 4 | 4 | https://x.com/Connected_Data/status/2119882273637933094 |
| @smobilefactory | "@Connected_Data Agent memory and knowledge graphs merging makes so much sense. Fun space to watch" | 1 | — | https://x.com/smobilefactory/status/2119949828725903599 |

---

## Stats Block

```
├─ 🟠 Reddit: 3 threads │ 115 upvotes │ 22 comments │ ⚠ partial (HTTP 403)
├─ 🔵 X: 3 posts │ 5 likes │ 8 reposts
├─ 🔴 YouTube: 0 videos
├─ 🟡 HN: 12 stories │ 996 pts │ 451 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no results this run)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 25 pages │ 🇯🇵 4 │ 🇨🇳 7
└─ 🗣️ Top voices: @Connected_Data, @smobilefactory │ r/OntologyEngineering
```

---

## Out of Scope but Notable

- **Google Antigravity for Knowledge Work (Nov 10, HN):** Google launched "Antigravity" at https://antigravity.google/blog/antigravity-for-knowledge-work/ — an AI-first knowledge work product. Title suggests radical productivity repositioning; details unclear from title alone. Worth watching — it's Google's first explicit "knowledge work" branding move. (via HN: https://thinker.sh/how-it-works context; URL: https://antigravity.google/blog/antigravity-for-knowledge-work/)

- **"Verification Is Not Knowledge" (Cosmos Institute, HN 245 pts, 142 comments, Nov 4):** Blog argues science has confused verification with understanding — generating correct answers ≠ knowing why they're correct. Highest-engagement non-topic HN thread this window. KR-adjacent epistemology, but belongs to AI safety/alignment topic. (https://blog.cosmos-institute.org/p/verification-is-not-knowledge)

---

## Data Gaps

- **DuckDuckGo HTML endpoint:** CAPTCHA blocked on both JP and CN queries; replaced with native WebSearch — equivalent coverage achieved
- **Reddit:** partial (HTTP 403 after 3 items); r/MachineLearning, r/semanticweb, r/LocalLLaMA content not retrieved
- **Bluesky:** 0 results this run (SOURCE HEALTH: OK; prior run had 11 posts); likely timing gap, not outage
- **YouTube:** no search performed this run
- **TikTok/Instagram:** not searched; low expected relevance for this topic
- **Polymarket:** no active markets
- **AML Cycle 2 results:** eval closed Nov 4; official leaderboard still pending mid-November
- **NODES 2026:** occurs Nov 12 (2 days); session videos already published as pre-event; full keynote content (Andrew Ng, Emil Eifrem) not yet available
- **CDL 2026:** starts Nov 11 tomorrow; live announcements not yet available
- **JitKnow 4.8 full content:** Juejin page loaded JavaScript-only; details from search snippets only
- **Letta Code releases:** no new Letta Code releases Nov 7-10 detected (v0.34.37-39 from Nov 2 still latest)
- **Approximate coverage:** ~82% — strong EN + selective JP + CN; weak on social and Reddit

---

## Key Quotes

> "The richest knowledge — the reasoning traces of humans working with AI — disappears after every session." — Doriana Negruț, NODES 2026 "The Missing Layer" ([link](https://neo4j.com/videos/live-from-nodes-2026-the-missing-layer-why-ai-memory-should-start-with-humans-not-agents/))

> "9 files yielding stronger performance versus 413 files with minimal results — a stark illustration of how structure beats volume." — dev.to/piekwerk on Anthropic memory study ([link](https://dev.to/piekwerk/anthropics-agent-memory-study-fixed-save-rules-cost-claude-its-gains-and-9-files-beat-413-3m9m))

> "An agent is only as good as its context, and today it has to glue that context together from separate systems on every turn." — James Li, PhoenixAI CEO ([link](https://www.prnewswire.com/news-releases/phoenixai-launches-contextbase-the-context-infrastructure-for-ai-agents-302929251.html))

> "Everyone is talking about agent memory and enterprise knowledge graphs, but very few people have noticed they're turning into the same thing." — @Connected_Data, Nov 9 ([link](https://x.com/Connected_Data/status/2119882273637933094))

> "An agent querying a graph needs to know that 'Account' could mean a bank account or a payment account." — Neo4j Ontology Graph Spec blog, Barrasa/Hane ([link](https://neo4j.com/blog/developer/the-neo4j-ontology-graph-specification-a-pragmatic-open-ai-first-approach/))

> "MELD does not adjudicate truth; a detected contradiction is preserved for later adjudication, never silently resolved." — arXiv:2608.16357 ([link](https://arxiv.org/abs/2608.16357))

> "AI answers no longer confidently making things up." (AI回答不再一本正经地胡说八道) — JitKnow 4.8 release, Juejin ([link](https://juejin.cn/post/7703743273756475419))

> "知识图谱装事实，本体论定规矩，搞反顺序就白干" — "KG stores facts, ontology defines rules — reverse the order and it's wasted work." — 53AI, Nov 3 ([link](https://www.53ai.com/news/knowledgegraph/2026110369780.html))
