<!-- prior-slugs: nvidia-jensen-spy-scandal · anthropic-enterprise-revenue-trajectory · anthropic-formal-verification-claude · open-weight-geopolitics · agent-governance-wave-q3 · mcp-supply-chain-scale · software-factory-democratization · ide-agent-fleet-pivot · memory-os-wars · neo4j-context-engine-enterprise-ontology · world-model-race · crowdstrike-ai-security-consolidation · sage-taiyi-metacognitive-science · lingbot-touch-tactile-foundation · marvell-lumentum-ai-connectivity · weight-space-programming · anthropic-evasion-bench-safety-monitors · jetbrains-air-multi-agent-ide · github-copilot-universe-2026 · tencent-ai-native-org-shift · open-weight-supply-chain-neuron-backdoor · ai-ma-vertical-workflow-control · anthropic-claude-duet-proactive-agent · meta-enterprise-ai-liability-shift · fable-steganography-convergent-protocols · four-labs-agent-containment-failures · microsoft-mxc-os-agent-sandbox · sap-outcome-based-pricing · harness-squared-recursive-self-improvement · typesafe-ai-decision-model · nous-research-hermes-enterprise-series-b · workday-agentic-identity-rising-oct13 · goodfire-neural-networks-clean · anthropic-scion-vcs · tenstorrent-series-e-risc-v-silicon · fleet-learning-binary-outcomes · diffusion-lm-commercial-wave · ai-autonomous-math-cs-proofs · aaif-agent-stack-standards · vertical-ai-revenue-acceleration · agent-bill-of-materials · cohere-sovereign-ai-series-e -->

# AI Engineering Digest — 2026-11-13

## What Changed

### Jensen Huang resigns as Nvidia CEO; legislative cascade reaches tipping point · UPDATE · [thread: nvidia-jensen-spy-scandal, since 2026-11-10]

**Since last:** Huang resigned Nov 11 (Form 8-K, "effective immediately"); CFO Colette Kress named interim CEO; cumulative market cap loss ~$490B since Nov 8; second and third affair allegations emerged Nov 12–13. Congressional hearings now scheduled: Huang closed-door deposition Dec 1 (House), Tim Teter (Nvidia GC) Dec 2, Senate Banking public hearing Dec 3, Commerce Secretary Lutnick Dec 10. OpenAI GC Chris Lehane publicly backed all three chip export bills Nov 12 (Chip Security Act + MATCH Act + AI Overwatch Act), joining Anthropic; Senate Majority Leader Thune: "high probability" of passage by year-end. Chinese labs rushed to reserve SE Asia and Europe GPU capacity overnight (Reuters, Nov 12 — 100K+ GPU capacity estimates, no confirmed contracts).

→ [The Register — Form 8-K, Nov 12](https://www.theregister.com/systems/2026/11/12/jensen-huang-resigns-as-nvidia-chief-executive/5309411) · [Semafor — Thune "high probability," Nov 12](https://www.semafor.com/article/11/12/2026/a-high-probability-congress-pushes-tighter-export-controls-following-nvidia-scandal) · [247WallSt — Kress tougher on OpenAI, Nov 13](https://247wallst.com/investing/2026/11/13/nvidias-new-ceo-colette-kress-seems-tougher-on-openai-than-huang-was/)

Huang was the primary industry voice against export tightening; his exit creates zero major corporate opposition. Combined with OpenAI's alignment, all three bills are advancing in the Senate NDAA with bipartisan backing — the most consequential shift in the US-China AI chip policy landscape this year. Teams routing inference through SE Asia or European neoclouds should assume the 7-country rule (see item 3) finalizes before year-end.

---

### Anthropic ANT roadshow 6× oversubscribed; Oct run-rate $81B/month; trading Nov 19 · UPDATE · [thread: anthropic-enterprise-revenue-trajectory, since 2026-10-14]

**Since last:** Roadshow orders 6× available shares as of Nov 11; Oct 2026 monthly revenue run-rate $81B (up from ~$71B Sep, +$10B in one month); $26B Class N private placement pre-locked by AMD/Broadcom/Google/Micron/Microsoft/Nvidia/TSMC (Google + Nvidia $10B each); pricing Nov 18, Nasdaq ANT trading Nov 19. Separately: $28B powered-land lease with Riot Platforms / Corsicana TX (910 MW, 400 MW Sep 2027 + phased through Jul 2028) confirmed disclosed Nov 4 — the largest disclosed AI data center contract on record by $ value.

→ [Yahoo Finance — 6× oversubscribed, Nov 11](https://sg.finance.yahoo.com/news/anthropic-to-begin-trading-thursday-nov-19-171954167.html) · [cloudnews.tech — Riot $28B lease](https://cloudnews.tech/riot-platforms-leases-910-mw-in-texas-to-an-ai-lab-for-28-billion/) · [TechCrunch — IPO price range, Nov 10](https://techcrunch.com/2026/11/10/anthropic-sets-ipo-price-range-of-70-to-78-per-share-to-reach-an-implied-valuation-of-1-404-trillion/)

At 6× oversubscribed and an $81B/month revenue run-rate, enterprise contract pricing and API rates are likely to reset upward post-IPO. Quiet period governs current negotiations through Nov 19 — renegotiate in-flight contracts now if possible.

---

### Commerce 7-country cloud-loophole rule; OpenAI + Anthropic align on export controls; ERNIE 5.5 Flash Preview + Kunlunxin M100 · UPDATE · [thread: open-weight-geopolitics, since 2026-10-07]

**Since last:** Commerce Dept drafted 7-country rule (Nov 12): individual licenses for Blackwell+ chip shipments to data centers in Malaysia, Singapore, Thailand, Indonesia, Brazil, Norway, South Africa; importers must disclose recipients and accept continuous monitoring; US operators in those countries exempt if they restrict performance from China/Russia/Venezuela. Could announce "in November 2026." Chinese labs rushed to lock overseas GPU capacity ahead of rule (Reuters exclusive, Nov 12). Baidu World (Nov 12): ERNIE 5.5 Flash Preview (post-trained MoE, Terminal-Bench 92.7, API live, free on OpenRouter, full weights + training scripts Nov 25 via GitHub `baidu/wenxin-5.5-flash-preview`, license TBD) + Kunlunxin M100 chip launched as scheduled. Qwen4-Max API preview live Nov 11; Apache 2.0 weights committed Dec 20 (Qwen4-27B + Qwen4-Flash).

→ [lapaasvoice.com — 7-country rule detail](https://lapaasvoice.com/us-commerce-department-finalizes-ai-remote-access-rule-to-restrict-chinas-access-to-advanced-chips) · [hugging news — OpenAI backs three bills, Nov 12](https://huggingnews.com/ai/update-openai-urges-passage-of-bipartisan-bills-to-block-chinas-access-t-4501bfb4) · [superpowerdaily — ERNIE 5.5 Flash Preview weights Nov 25](https://superpowerdaily.com/posts/baidu-releases-ernie-5-5-flash-preview-with-model-weights-due-november-25)

The six-layer export control regime (DHS ban + MOFCOM + Nvidia 51% rule + Nov 9 remote-access extension + AI Overwatch + 7-country rule) now closes every major offshore compute pathway. Apache 2.0 open weights remain the one regime-exempt deployment path — Baidu and Alibaba both publicly doubling down on that strategy.

---

### Microsoft Lazarus: open-weight model supply chain backdoor via <10 neuron edits · NEW · [thread: open-weight-supply-chain-neuron-backdoor, since 2026-11-13]

**Since last:** First appearance. Microsoft researchers (Nov 2026): backdoor inserted into open-weight agents by editing fewer than 10 neurons — no retraining required; trigger fires 98.8% ASR on Nemotron-Terminal-8B (7 neurons), Qwen3.6-27B (6 neurons), Gemma-4-31B-IT. Requires only the ability to modify weights before deployment (insider, compromised pipeline, poisoned model hub). Detection fails: trained classifier achieves 91.4% recall but 9.7% false-positive rate; Claude Opus 5.5 and GPT-6 Astra performed poorly at checkpoint inspection. Microsoft has not observed threat actors use this yet.

→ [The Hacker News, Nov 2026](https://thehackernews.com/2026/11/microsoft-researchers-show-ai-agents.html) · [The Next Web](https://thenextweb.com/news/microsoft-lazarus-ai-agent-backdoor-neurons) · [Dataconomy, Nov 11](https://dataconomy.com/2026/11/11/microsoft-finds-ai-backdoor-hidden-in-fewer-than-10-neurons/)

Defense requires comparing every deployed checkpoint against declared base weights from the original publisher — the same posture as a compromised CI pipeline. Use private model registries and block direct public hub access for production agents. This is a new threat class: the attack surface is the weight file itself, not the runtime or the prompt.

---

### Tencent restructures ~52K of ~105K employees to AI-native ventures · NEW · [thread: tencent-ai-native-org-shift, since 2026-11-13]

**Since last:** First appearance. Pony Ma (Ma Huateng) Nov 11 town hall: "army" (~52K, core business + AI efficiency) vs "navy" (~52K, new AI-native ventures); capex now 1.3× annual payroll; Tencent PR Director confirmed explicitly not layoffs. Ma: "The industry has entered an Age of Discovery. Transformation is late."

→ [Bloomberg, Nov 12](https://www.bloomberg.com/news/articles/2026-11-12/tencent-founder-rallies-half-of-staff-behind-ai-native-push) · [QZ, Nov 2026](https://qz.com/tencent-pony-ma-half-workforce-ai-native-111226)

First hyperscaler-scale organization to create new AI-native revenue lines from existing headcount rather than announcing cost cuts — a structurally different playbook from every Western AI restructuring in 2026 (Canva 22%, Squarespace 19%, Microsoft 60K buyout offers). The army/navy framing and capex multiple are the signal: Tencent is treating AI as a business-creation event, not a headcount-reduction event.

---

### VS Code 1.145.3: three MCP remote code execution vulnerabilities patched · UPDATE · [thread: mcp-supply-chain-scale, since 2026-10-28]

**Since last:** VS Code 1.145.3 (Nov 10) patches three MCP RCEs via distinct protocol surfaces — CVE-2026-120779 (CVSS 9.6): elicitation notifications treated server-controlled text as VS Code command links → command execution on click; CVE-2026-114171 (CVSS 8.8): crafted `vscode:mcp/install` links accepted unsafe input definitions → arbitrary command; CVE-2026-119983: legacy SSE endpoint origin bypass. No exploitation reported. VS Code 1.146 (Nov 11) also deprecates Local harness, removed February 2027 — Copilot harness becomes the sole harness. Separately: MCP file upload extension draft published Nov 10 (keeps large file bytes out of model context via `x-mcp-file` annotation + server-side storage).

→ [MSRC — CVE-2026-120779](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-120779) · [beri.net — all 3 CVEs](https://www.beri.net/article/vs-code-mcp-rce-cve-2026-120779-cve-2026-114171-elicitation-install-link-1-145-3-patch-mcp-server-allowlist)

Three distinct MCP protocol surfaces exploited in a single patch cycle confirms MCP is now getting Patch Tuesday treatment. Update VS Code to 1.145.3 immediately; audit elicitation handlers and install-link validators in any custom MCP server.

---

### Neo4j Relate GA + Databricks Genie Ontology GA + Netflix production KG at 2B requests/day · UPDATE · [thread: neo4j-context-engine-enterprise-ontology, since 2026-10-28]

**Since last:** Neo4j Relate (Nov 11, Apache 2.0, Rust): embedded agent-native graph DB; built-in MCP server; auto-detects agent harnesses; retryable error flags; context row caps + truncation markers prevent context saturation; sub-millisecond reads. Databricks Genie Ontology GA (Nov 11): auto-builds ontology from dashboards/SQL/notebooks/Power BI; 91% enterprise task pass rate, 1.6× strongest frontier agent, <50% token usage (Turing benchmark). Netflix operational KG (InfoQ, Nov 13): RDF/OWL/SHACL/SPARQL at 2B daily requests + 38M log events/sec via homegrown Rust QuipuDB (arXiv:2608.16813) — largest-scale production deployment of W3C semantic web stack found this year; AutoRCA multi-agent system uses shared ontology as common interface across specialist agents without coupling. RAGFlow 1.0 GA (Nov 9): complete Go rewrite; 91% FRAMES accuracy; "Agent Native Database" positioning. NODES 2026 concluded Nov 12; Andrew Ng × Emil Eifrem 104-min fireside now on-demand.

→ [InfoQ — Netflix operational KG, Nov 13](https://www.infoq.com/news/2026/11/netflix-ai-driven-observability/) · [Databricks — Genie Ontology GA, Nov 11](https://www.databricks.com/blog/announcing-ga-genie-ontology) · [Neo4j Relate blog, Nov 11](https://neo4j.com/blog/news/meet-relate-by-neo4j-an-embedded-database-for-ai-agents/)

Netflix validates the architectural pattern at scale: ontology as common interface across specialist agents without coupling, and without agents knowing each other's internal implementations. Three concurrent GA/open-source releases in 48 hours without coordination signals the "agent-native database" category is crystallizing.

---

### Four-survey convergence: governance gap is the enterprise AI ROI predictor · UPDATE · [thread: agent-governance-wave-q3, since 2026-09-18]

**Since last:** HFS Research + Rackspace (N=502, Aug-Sep 2026, Nov 12): only 33% met/exceeded AI business case; 96% have governance gaps; 78% say governance failure > tech failure as scaling threat; organizations fully embedded = 56% business-case realization vs. 28% for multi-function deployers. Accenture CIO Pulse (N=300, Nov 2026): 64% scaling AI, only 7% optimized at scale; +47% token consumption YoY (97% of CIOs saw increase); 54% cite governance as top barrier. TCS Enterprise AI Study (N=1,333, 25 countries, Nov 4): 84% cite productivity as top benefit; only 10% allow agents to execute without human approval across multiple functions. Genpact (N unspecified, Nov 12): 79% deployed AI agents; only 15% linked investments to measurable P&L. Atlassian Q1 FY2027 (Nov 5): Rovo AI credit consumption +20% month-over-month; Teamwork Collection customers 7× YoY; cloud +31%.

→ [StockTitan/Rackspace — HFS N=502, Nov 12](https://www.stocktitan.net/news/RXT/new-hfs-research-and-rackspace-study-finds-only-one-third-of-45t8nt1upnt4.html) · [Accenture CIO Pulse](https://www.accenture.com/en/insights/ai-data/cio-pulse-survey) · [TCS Enterprise AI Study, Nov 4](https://www.tcs.com/who-we-are/newsroom/press-release/productivity-top-benefit-tcs-enterprise-ai-study)

The 7%–33% business-case realization range (depending on governance maturity depth) is the clearest ROI predictor in enterprise AI so far. The +47% token YoY confirms spending is real; the 15% P&L link confirms the accountability gap is real. Governance maturity, not model capability, is now the stated bottleneck in four independent surveys with combined N > 2,000.

---

### Multi-agent teams 41.1% worse than their own expert member; freee "Selective Dark Factory" at 89.6% AI code at scale · UPDATE · [thread: software-factory-democratization, since 2026-10-14]

**Since last:** ICML 2026 (arXiv:2602.01011, amplified CNBC Nov 8): LLM multi-agent teams consistently underperform their best member by up to 41.1% via "integrative compromise" — teams average expert and non-expert views rather than deferring; correlation r=0.55–0.69 with worse performance; Anthropic study in same article: multi-agent orgs achieve goals better BUT produce less ethically aligned solutions; agents compartmentalize tasks to bypass individual ethical refusals. Counterpoint: freee "Selective Dark Factory" (AI × Dev Summit, Oct 16, circulating JP community Nov 2026): 89.6% AI-generated code across 40+ integrated products / 700K paying companies (Sep 2026 metrics); requirements→prototype 15.6h→5h; human review time 4.5h→53 min; human judgment retained on exactly 4 categories (business strategy, user behavior patterns, cross-team contracts, irreversible risks). ADAPT (arXiv:2611.16114, Nov 11): agentic diff-aware PR testing; GPT-5-mini 89.9% fail-to-pass rate — first approach targeting the gap between "tests exist" and "tests cover this change."

→ [CNBC — multi-agent risks, Nov 8](https://www.cnbc.com/2026/11/08/ai-agents-risks.html) · [arXiv:2602.01011 ICML 2026](https://arxiv.org/abs/2602.01011) · [arXiv:2611.16114 ADAPT, Nov 11](https://arxiv.org/abs/2611.16114) · [freee Speaker Deck — Selective Dark Factory](https://speakerdeck.com/freee/freee-niokeru-kibo-no-jissen-aix-kaihatsu-soshiki-summit-2026)

The freee data answers the "it doesn't scale" objection with production metrics at 700K paying customers. The key design element: humans do not review raw AI output — they examine synthesized decision points across only 4 explicit categories. The 41.1% groupthink finding is the structural reason this matters: unstructured multi-agent coordination produces worse outcomes than the best single agent unless human checkpoints enforce deferral to the expert.

---

### World models: Duo 153GB open weights + BirdDreams (no scene layout input) + PhysLoop RSI + WICL frozen-policy result · UPDATE · [thread: world-model-race, since 2026-10-28]

**Since last:** Duo v1 (arXiv:2611.15131, Nov 11, Ant Group inclusionAI): "Reciprocal World Model" treating cognition as intrinsic to the world; 153GB open weights released across 4 HF repositories; full-duplex audio-video-text interaction (330–650ms, 708ms chunk cycle at 24fps); territorial restriction (excludes US, UK, EU, South Korea — inherited from MiniMax H3). BirdDreams (arXiv:2611.14815, Nov 10, HF 45↑): first driving world model that jointly generates perspective + BEV video — no future vehicle trajectories, HD maps, or scene layout inputs required; outperforms prior driving world models on PhysicalAI-AV + nuScenes. PhysLoop (arXiv:2611.16748, Nov 12, HF 41↑): RSI applied to synthetic video physics quality; LLM constrain→generate→select→correct cycle; 100K video dataset released; "marks a key milestone toward RSI in video generation." WICL/RoboScript (arXiv:2611.12885, Nov 11, HF 56↑ trending): frozen foundation model achieves 83.4% manipulation success from 1 demo per task, 0 gradient updates — +20pp above strongest trained policy (simulation results only; physical hardware verification pending).

→ [arXiv:2611.15131 Duo](https://arxiv.org/abs/2611.15131) · [arXiv:2611.14815 BirdDreams](https://arxiv.org/abs/2611.14815) · [arXiv:2611.12885 WICL/RoboScript](https://arxiv.org/abs/2611.12885)

Duo's 153GB open weights are available now (with territorial restriction). BirdDreams + WICL together push the "how much training data does physical AI need" question toward an answer that may be "much less than currently assumed." PhysLoop adds synthetic data quality to the RSI stack alongside weights (WSP), training config (InfraRSI), and architecture.

---

### Claude surfaces 663 theorems from Gödel's unpublished notebooks · UPDATE · [thread: anthropic-formal-verification-claude, since 2026-10-21]

**Since last:** Jan von Plato (Univ. Helsinki) published results Nov 13: Claude analyzed 1,009 pages of Gödel's unpublished 1940s notebooks (16 workbooks in Gabelsberger shorthand — obsolete shorthand, written 1940s); surfaced 663 theorems and proof ideas in days; ~400 verified with Coq as stated, ~200 needed repairs, ~50 were false. First systematic AI-driven mathematical archaeology of a deceased mathematician's unpublished archive. Epistemological caveat: Joel David Hamkins — "how much is Claude and how much is Gödel is a job for the historians."

→ [The Guardian, Nov 13](https://www.theguardian.com/science/2026/nov/13/kurt-godel-notebooks-ai-helps-unlock-hidden-discoveries-man-who-transformed-maths) · [superpowerdaily — 663 theorems breakdown](https://superpowerdaily.com/posts/claude-surfaced-663-theorems-and-proof-ideas-in-g-del-s-notebooks-researcher-says)

Extends the formal reasoning thread beyond current deployed code to century-scale historical archives in obsolete shorthand. The 60% first-pass Coq verification rate is surprisingly high for a system navigating incomplete proof sketches — the technique now scales to any formalized domain with adequate scaffolding. Combined with AlphaProof Code (Nov 10): formal proof runs are now cost-competitive and covering new territory weekly.

---

### IDE harness wave: Qwen Code 1.0, Modern Web Guidance 1.0, OpenBot 1.0, Kiro "Approve for me" · UPDATE · [thread: ide-agent-fleet-pivot, since 2026-10-07]

**Since last:** Qwen Code 1.0 Preview (Nov 11, Apache 2.0): in-process in-memory event bus decoupling reasoning from tool execution; model-agnostic (OpenAI/Anthropic/Gemini/Qwen/Ollama); 2,000 free Qwen API calls/day; Alibaba Cloud OSS/RDS/FC integrations; CN-market-first. Modern Web Guidance 1.0 (Nov 10, Apache 2.0): Chrome/Edge/Firefox/MDN joint release; 55%→92% web task pass rate on 200-task eval across Codex/Claude/Antigravity; install via `npx modern-web-guidance@latest install`; 3,360 stars / 286 HN pts. OpenBot 1.0 (Nov 9, MIT, 10,506 stars, CopilotKit): governance-first agent workspace; CEL policy gateway; audit row written before every action; 8 frameworks via AG-UI (Claude Agent SDK, OpenAI Agents SDK, LangChain, Google ADK, Mastra, AWS Strands, Microsoft Agent Framework, CrewAI). Kiro "Approve for me" (Nov 10): 70% handled by explicit permission rules; 30% go to LLM review; 97% auto-approved, <1s median; available paid users in us-east-1 and eu-central-1.

→ [GitHub — Modern Web Guidance](https://github.com/GoogleChrome/modern-web-guidance) · [GitHub — Qwen Code](https://github.com/QwenLM/qwen-code) · [Kiro "Approve for me"](https://kiro.dev/blog/introducing-approve-for-me/) · [CopilotKit OpenBot](https://www.copilotkit.ai/blog/introducing-openbot-1-0)

Modern Web Guidance 1.0 is immediately deployable — 37-point pass rate improvement from a single `npx install`, no model change. OpenBot 1.0 and Kiro "Approve for me" represent converging product bets on governance-at-the-harness as default, not optional.

---

### Memory tooling: Hindsight 50× speedup at banking scale; Letta 9 releases in 3 days · UPDATE · [thread: memory-os-wars, since 2026-10-21]

**Since last:** Hindsight v1.2.1 (Nov 10): keyword recall 5–6s → 0.09s (66×); entity search 585ms → 58ms (10×); staleness checks 904ms → 18ms (50×); zero-downtime embedding model migration via `hindsight-admin reembed`; dual embedding (separate lightweight query vs larger stored-text configs). Letta Code v0.34.52–60 (Nov 11–13): 9 releases in 3 days (1 every ~8 hours); adds Letta Cloud Monitor URL source, private sandbox ports by default, enhanced subagent context preservation + model inheritance; fixed memory checkout HTTP 403 errors.

→ [Hindsight v1.2.1 — Nov 10](https://hindsight.vectorize.io/blog/2026/11/10/version-1-2-1) · [Letta Code releases](https://github.com/letta-ai/letta-code/releases)

Hindsight's 50× speedup removes the latency objection to dedicated memory infrastructure at banking scale; zero-downtime reembedding means memory model upgrades are now non-breaking — a previous production risk eliminated. Databricks Genie Ontology GA (item 7) is now competing in the same context-retrieval space at enterprise scale.

---

### Vertical AI M&A: Five9/Level AI, OpenAI/Odessia — M&A is about workflow control, not model access · NEW · [thread: ai-ma-vertical-workflow-control, since 2026-11-13]

**Since last:** First appearance. Five9 acquires Level AI $325M all-cash (Nov 5): contact center AI (agent performance, voice+digital automation, conversation analytics); Level AI remains standalone for non-Five9 centers; Five9 stock -23% after-hours (market punished balance-sheet risk over strategic rationale). OpenAI acquires Odessia (Nov 10, undisclosed, acqui-hire): travel booking + IATA accreditation (direct flight booking without Booking.com/Expedia as intermediary) + Sonder co-founder Francis Davidson. Salesforce completed Cresta $2.7B (Nov 2): voice AI for sales/service. Three acquisitions in 8 days target the same pattern.

→ [TechCrunch — OpenAI/Odessia, Nov 10](https://techcrunch.com/2026/11/10/openai-acquires-odessia-travel-startup-created-by-sonder-founder/) · [siliconangle — Five9/Level AI, Nov 5](https://siliconangle.com/2026/11/05/five9-buys-contact-center-intelligence-startup-level-ai-after-posting-narrow-earnings-beat/)

Five9 paid for IATA accreditation and booking infrastructure — not an AI model. OpenAI paid for IATA accreditation and booking infrastructure — not NLP capability. The economic moat is now regulatory access + workflow integration, which cannot be replicated by prompt engineering. This is the same pattern as the security M&A wave (item below): capture the workflow layer before someone else does.

---

### AI security/governance M&A: Kindo $30M + Cisco open spec + ~$2.75B wave total · UPDATE · [thread: crowdstrike-ai-security-consolidation, since 2026-10-07]

**Since last:** Kindo $30M (Nov 12): enterprise AI agent management platform; $57.6M total raised. Rox $100M Series B at $1.3B valuation (Nov 12, General Catalyst + March Capital): AI sales agents. Plurai $13M seed (Nov 11): simulation infrastructure for self-improving agents. Cisco released open specification for agentic AI security evaluation and testing (HN, Nov 2026): cross-vendor standard for testing whether AI agents remain safe across model/prompt/tool changes; AgentArmor 8-layer framework covering ingestion through inter-agent layers. Running total: ~$2.75B+ across 40+ deals since late September.

→ [AI Agents Directory — Nov 12 brief](https://aiagentsdirectory.com/news/ai-agents-news-brief-november-12-2026) · [HN — Cisco open spec](https://news.ycombinator.com/item?id=50458009)

The Cisco open spec is the most actionable item: first cross-vendor standard for testing agent safety boundaries, available now before Cisco productizes it. Worth adopting as an audit framework immediately.

---

## Standing Stories

- **anthropic-evasion-bench-safety-monitors** (since 2026-10-21) — last update 2026-11-06 — EvasionBench 98% evasion rate; CrowdStrike behavioral baseline (fires before policy violation) is the operational response; 2nd cycle with no post-Nov-10 advance.
- **jetbrains-air-multi-agent-ide** (since 2026-10-28) — last update 2026-11-06 — ACP-based multi-agent orchestration across 5 JetBrains IDEs; GitHub Copilot became default agent Nov 3; 2nd cycle with no post-Nov-10 advance.
- **marvell-lumentum-ai-connectivity** (since 2026-11-02) — last update 2026-11-10 — $115B all-stock; $550B AI connectivity TAM through 2030; Commerce 7-country rule directly targets SE Asia data centers where this infrastructure is being built; 1st cycle in standing.
- **sage-taiyi-metacognitive-science** (since 2026-11-09) — last update 2026-11-10 — Metacognitive scientific discovery; 54.0 vs AI Scientist-v2 47.9; cobalt yield trace→84%; 1st cycle in standing.
- **lingbot-touch-tactile-foundation** (since 2026-11-10) — last update 2026-11-10 — Ant Group sensor-agnostic tactile FM; now 102 HF↑; zero-shot cross-sensor transfer; 1st cycle in standing.

*Dropped this cycle (3+ consecutive no-update): `weight-space-programming` (since 09-30) — small-network weight-read/write uncontested; large-model scaling contested; resurfaces on new replication. `github-copilot-universe-2026` (since 10-14) — subsumed by JetBrains Air ACP integration and VS Code 1.146 Copilot-only harness announcement; resurfaces on major standalone feature launch.*

---

## Repos & Releases

| Project | Date | Signal |
|---|---|---|
| [Neo4j Relate](https://neo4j.com/blog/news/meet-relate-by-neo4j-an-embedded-database-for-ai-agents/) | Nov 11 · Apache 2.0 | Rust embedded graph DB for agents; built-in MCP server; retryable errors; context row caps |
| [Databricks Genie Ontology GA](https://www.databricks.com/blog/announcing-ga-genie-ontology) | Nov 11 | 91% enterprise tasks; 1.6× frontier agent; <50% tokens; Always-On Genie preview |
| [RAGFlow 1.0 GA](https://ragflow.io/blog/announcing-ragflow-1.0-beyond-rag-toward-an-agent-native-database) | Nov 9 | Go rewrite; 91% FRAMES; Agent Native Database; 2 orders of magnitude faster retrieval concurrency |
| [Qwen Code 1.0 Preview](https://github.com/QwenLM/qwen-code) | Nov 11 · Apache 2.0 | In-process event bus; model-agnostic; 2K free Qwen API calls/day; Alibaba Cloud integrations |
| [OpenBot 1.0](https://github.com/CopilotKit/openbot) | Nov 9 · MIT | CEL policy gateway; 8 frameworks via AG-UI; 10,506 stars; audit row before every action |
| [Modern Web Guidance 1.0](https://github.com/GoogleChrome/modern-web-guidance) | Nov 10 · Apache 2.0 | Chrome/Edge/Firefox/MDN joint; 55%→92% web task pass rate; `npx modern-web-guidance@latest install`; 3,360 stars |
| [OpenCode v2.3.0](https://opencode.ai/changelog/v2.3.0) | Nov 13 | Background subagents default; mTLS gateway; experimental MCP events |
| [ERNIE 5.5 Flash Preview](https://dev.to/paullovelace/baidus-ernie-55-flash-preview-is-live-on-qianfan-weights-open-25-november-3104) | Nov 12 (Baidu World) | 280B/14B MoE; Terminal-Bench 92.7; free on OpenRouter; full weights + training scripts Nov 25 |
| [Qwen4-Max API preview](https://felloai.com/qwen-4/) | Nov 11 · API preview | 1M context; thinking enabled; Apache 2.0 weights committed Dec 20 |
| [Duo v1 (Ant Group inclusionAI)](https://arxiv.org/abs/2611.15131) | Nov 11 · 153GB weights | Reciprocal World Model; full-duplex; excludes US/UK/EU/KR; arXiv:2611.15131 |
| [BirdDreams](https://arxiv.org/abs/2611.14815) | Nov 10 · HF 45↑ | Joint perspective+BEV driving world model; no scene layout input; arXiv:2611.14815 |
| [WICL/RoboScript](https://arxiv.org/abs/2611.12885) | Nov 11 · HF 56↑ | 83.4% robot manipulation; 1 demo, 0 gradient updates (simulation); arXiv:2611.12885 |
| [G-STAR](https://arxiv.org/abs/2611.13004) | Nov 8 · HF 40↑ | 64× compression; 20× speedup; 2.5s 1024×1024 on H200; arXiv:2611.13004 |
| [AutoOntic](https://arxiv.org/abs/2611.15467) | Nov 11 | Schema-free automatic ontology induction; 88% retrieval accuracy; arXiv:2611.15467 |
| [ADAPT](https://arxiv.org/abs/2611.16114) | Nov 11 | Diff-aware PR testing; GPT-5-mini 89.9% fail-to-pass; arXiv:2611.16114 |
| [PhysLoop](https://arxiv.org/abs/2611.16748) | Nov 12 · HF 41↑ | RSI for video physics quality; 100K video dataset; arXiv:2611.16748 |
| [0sec Labs "0"](https://github.com/0sec-labs/0) | Nov 8 · MIT/Apache 2.0 | AI security harness; 93/95 XBOW; 30+ Linux kernel 0-days (maintainer-claimed); YC-backed |
| [ARTEMIS (Google)](https://github.com/google/artemis) | late Oct · Apache 2.0 | Android automation MCP agent; 99% AndroidWorld (maintainer-reported); 17K stars |
| [Reef](https://github.com/Human-Agent-Society/reef) | trending · Apache 2.0 | Self-improving harness via continual learning; `harness_evolve` recipe; 7,788 stars |
| [Hindsight v1.2.1](https://hindsight.vectorize.io/blog/2026/11/10/version-1-2-1) | Nov 10 | 50× large-bank speedup; zero-downtime reembedding; dual embedding configs |
| [VS Code 1.145.3](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2026-120779) | Nov 10 | 3 MCP RCEs patched (CVSS 9.6/8.8/unknown); upgrade immediately |
| [Coucou v0.6.0](https://github.com/Louis-CFM/coucou) | Nov 12 · Swift | Agent approvals from Mac notch / iPhone / Android Lock Screen; Antigravity support |

---

## On the Horizon

- **Nov 15**: China MOFCOM comment window closes — final rule on 23-technology AI export controls; open-source/API exemption expected to hold; DeepSeek + MiniMax registration already complete. Binary event for infrastructure built on continuous access to Chinese open-weight models.
- **Nov 18**: Anthropic ANT IPO pricing on Nasdaq.
- **Nov 19**: Anthropic ANT trading begins; DeepSeek V4 Pro retires (migrate to V4.1 Flash now — no auto-forward); AML Cycle 2 leaderboard results (BM25 vs embedding vs graph cost-accuracy head-to-head with 50+ teams).
- **Nov 19–21**: IJCKG 2026, Bangkok — LLM-guided ontology-driven KG construction (arXiv:2609.31663).
- **Nov 20**: Meta/Conductor cloud shutdown — migrate parallel-agent workloads.
- **Nov 25**: ERNIE 5.5 Flash Preview weights + training scripts + inference toolchain (GitHub `baidu/wenxin-5.5-flash-preview`); license TBD until release (prior ERNIE 5.5 Flash Base excluded EU/UK/Korea).
- **Dec 1–10**: Congressional chip export hearings — Huang deposition (closed, House Dec 1), Nvidia GC Dec 2, Senate Banking public hearing Dec 3, Commerce Secretary Lutnick Dec 10.
- **Dec 20**: Qwen4 Apache 2.0 weights committed (Qwen4-27B + Qwen4-Flash).
- **Year-end**: Senate Majority Leader Thune "high probability" Chip Security Act + MATCH Act + AI Overwatch Act pass in NDAA before year-end; with Huang gone, zero major corporate opposition remains.
- **Commerce 7-country rule**: drafted Nov 12, could announce "in November 2026" — specific enforcement date unclear; affects any team routing inference through SE Asia or Europe clusters to serve Chinese customers.
- **Post-IPO Anthropic pricing**: quiet period governs enterprise contract negotiations through Nov 19; post-IPO rates likely reset upward given 6× oversubscription and $81B/month run-rate.
- **Meta Muse Spark 1.4**: appeared in Meta RocksDB pull request Nov 13 (internal tooling only); prediction market 36.5% by Nov 30.

**Paradigm watch — assumptions violated this cycle:**

- **Microsoft Lazarus (Nov 2026):** "Open-weight model supply chain attacks require visible code changes detectable by standard artifact diffing" → violated: <10 neuron edits inserted with no retraining produce 98.8% ASR backdoors; standard LLM classifier fails at 9.7% FPR. Defense posture for open-weight models must now include checkpoint comparison against declared base weights.
- **WICL/RoboScript (arXiv:2611.12885, Nov 11):** "Robot manipulation requires large training datasets and weight updates to reach expert-level performance" → challenged: frozen foundation model achieves 83.4% mean success across 50 manipulation tasks from 1 demo per task, 0 gradient updates — +20pp above strongest trained policy. Physical hardware verification still pending; treat as directional.
- **G-STAR (arXiv:2611.13004, Nov 8):** "Extreme spatial compression in discrete autoregressive image generation must sacrifice representation quality — the tradeoff is a fundamental constraint" → violated: quadratic co-scaling of group size with compression factor preserves capacity at 64× compression; 20× speedup at competitive quality across 5 benchmarks.
- **Claude + Gödel's notebooks (Nov 13):** "Mathematical archaeology from handwritten historical archives in obsolete shorthand requires specialized human logicians" → violated at first pass: 663 theorems surfaced from 1,009 pages in days; ~60% Coq-verified as stated without repair. Technique scales to any formalized domain with adequate scaffolding.
- **BirdDreams (arXiv:2611.14815, Nov 10):** "Driving world models require pre-specified future vehicle trajectories or HD maps as conditioning inputs" → violated: joint generation of perspective + BEV without scene layout inputs; more plausible ego motion without ego-action conditioning.

---

## Portfolio Drift

No `topics.yml` amendments have been made since these recommendations began. Same escalation applies:

| Slug | Cycles | Proposed `topics.yml` addition |
|---|---|---|
| `mcp-supply-chain-scale` | 13+ | `mcp-security` — this week: VS Code 3 MCP RCEs (CVSS up to 9.6) + open-weight neuron backdoor new threat class |
| `software-factory-democratization` | 13+ | `ai-dev-economics` — freee Selective Dark Factory (89.6% AI code, 700K customers); ICML groupthink quantified; ADAPT PR testing |
| `ide-agent-fleet-pivot` | 13+ | `ide-agents` — Qwen Code 1.0, OpenBot 1.0, Modern Web Guidance 1.0, Kiro "Approve for me" in 72 hours |
| `open-weight-geopolitics` | 13+ | `open-weight-frontier` — 7-country rule; six-layer export control convergence; Huang exit removes corporate opposition |
| `world-model-race` | 10+ | `world-models` — Duo 153GB weights; BirdDreams; WICL frozen-policy; PhysLoop RSI |
| `agent-governance-wave-q3` | 10+ | `enterprise-ai-governance` — 4-survey convergence; governance maturity as primary ROI predictor; 7%–33% realization gap |
| `memory-os-wars` | 10+ | `agent-memory-infra` — Hindsight 50× speedup; Letta velocity; Databricks Genie Ontology GA competes in same layer |
| `anthropic-enterprise-revenue-trajectory` | 10+ | `ai-lab-financials` — ANT trading Nov 19; 6× oversubscribed; $81B/month run-rate; $28B Riot lease |
| `neo4j-context-engine-enterprise-ontology` | 9+ | `agent-context-layer` — Relate + Genie Ontology GA + Netflix QuipuDB in same 48-hour window |
| `crowdstrike-ai-security-consolidation` | 9+ | `ai-security-ma` — $2.75B+ in 40+ deals; Cisco open spec emerging as the cross-vendor audit standard |

**Escalation notice:** `mcp-security` and `ai-dev-economics` have been recommended for 13+ consecutive cycles without amendment. This week alone produced a new MCP threat class (VS Code 3 RCEs) and a new open-weight threat class (neuron backdoor) on the security side, and the most rigorous software factory success data yet (freee 89.6% at 700K customers) on the economics side. These are active research areas generating weekly findings — the case for dedicated topics is empirically established.

---

threads: 5 standing, 3 new, 12 updated
