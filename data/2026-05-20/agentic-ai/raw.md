# Agentic AI — Raw Research Output
**Date:** 2026-05-20
**Topic slug:** agentic-ai
**Pipeline:** plan → retrieve → normalize → fuse → rerank → cluster → render

---

## PLATFORM: Web / News / Blogs

### Source 1 — Anthropic Code with Claude 2026 (Multiple Sources)

**URLs:**
- https://simonwillison.net/2026/May/6/code-w-claude-2026/
- https://www.infoq.com/news/2026/05/code-with-claude/
- https://every.to/chain-of-thought/inside-anthropic-s-2026-developer-conference
- https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features
- https://www.aiexpertmagazine.com/anthropic-code-with-claude-2026-everything-you-need-to-know/
- https://letsdatascience.com/blog/anthropic-dreaming-claude-managed-agents-self-improving-may-6

**Summary:**
Code with Claude San Francisco ran on May 6, 2026, as the first stop on a developer-conference tour (London: May 19-21, Tokyo: June 5-6). Major announcements:

1. **Claude Managed Agents — Three Features:**
   - **Multi-agent orchestration** (public beta): A lead agent fans jobs out to specialist subagents running in parallel
   - **Outcomes** (public beta): Developers specify desired results; a grading agent scores and reruns tasks. Wisedocs reported 50% faster reviews. Benchmark showed 10.1% improvement in PowerPoint generation quality.
   - **Dreaming** (research preview): Background process reviews recent sessions, identifies recurring mistakes, converged workflows, and emergent preferences. Harvey reported 6x jump in task completion rates. Requires developer access request.

2. **Claude Code Updates:**
   - Rate limits doubled for Pro, Max, Enterprise
   - Peak-hour limits removed for Pro and Max
   - API volume increased 17x year-on-year
   - Remote Agents: control laptop via smartphone
   - CI auto-fix for automatic PR corrections
   - Auto Mode: classifiers screen for destructive actions before execution
   - Worktrees: Claude creates isolated git branches independently
   - Routines: execute on cron schedules, GitHub webhooks, or API endpoints
   - Redesigned desktop GUI with split views and pinnable assistant messages
   - Background Agents, Agent Teams (research preview)

3. **SpaceX/Colossus Deal:** Anthropic secured exclusive access to SpaceX's Colossus supercluster addressing capacity constraints.

4. **Revenue/Scale:** CEO Dario Amodei — Q1 2026 revenue grew 80x vs planned 10x; annualized sales reached $30B by early April.

5. **Enterprise partners:**
   - Mercado Libre (23,000 engineers): targeting 90% autonomous coding by Q3 2026
   - GitHub: cache hit rates above 94% as foundational metric — "like high frequency trading"
   - Vercel: Opus tokens = 23% of usage but >70% of spending; V0 credit spending doubled
   - Harvey: 6x task completion rate jump
   - Spiral: deployed Managed Agent within an afternoon

6. **Strategic insight:** Boris Cherny — asynchronous code development patterns; developers managing multiple concurrent Claude sessions. Routines = "higher-order prompts" enabling automated PR generation. Creator of Claude Code: "literally no manually written code anywhere in Anthropic anymore."

**Key Quote (Simon Willison live blog):**
> "The advisor strategy demonstrates Sonnet calling Opus for guidance achieves frontier model quality at 5x lower cost."

---

### Source 2 — Claude Code Release Notes (May 2026)

**URL:** https://releasebot.io/updates/anthropic/claude-code

**Version 2.1.145** (May 20, 2026):
- JSON session listing via `claude agents --json`
- Plugin discovery with command, agent, skill, hook previews
- `agent_id` and `parent_agent_id` OTEL span attributes
- Fixed permission-prompt bypass in Bash variable assignments
- Read tool shows partial views instead of hard errors

**Version 2.1.144** (May 19, 2026):
- Background session resume support (`bg` marking)
- Fixed startup hangs up to 75s when api.anthropic.com unreachable
- Fixed MCP server pagination for tools/list responses
- Fixed macOS background sessions crashing in Full Disk Access folders

**Version 2.1.143** (May 15, 2026):
- Plugin dependency enforcement with disable-chain hints
- Projected context cost estimates to marketplace browser
- `worktree.bgIsolation: "none"` for direct working-copy edits

**Version 2.1.142** (May 14, 2026):
- Fast mode updated to Opus 4.7 (previously 4.6)
- Configuration flags for dispatched background sessions
- Fixed background sessions disappearing after macOS sleep/wake

---

### Source 3 — Claude Opus 4.7 Release (April 16, 2026)

**URLs:**
- https://www.buildfastwithai.com/blogs/claude-opus-4-7-review-benchmarks-2026
- https://thenextweb.com/news/anthropic-claude-opus-4-7-coding-agentic-benchmarks-release
- https://llm-stats.com/blog/research/claude-opus-4-7-launch
- https://www.vellum.ai/blog/claude-opus-4-7-benchmarks-explained

**Key metrics:**
- SWE-bench Verified: 87.6% (up from 80.8% on Opus 4.6)
- SWE-bench Pro: 64.3% (industry high; +10.9 points over Opus 4.6; +6.6 points over GPT-5.4 at 57.7%)
- Multi-step agentic reasoning: 14% improvement with 1/3 the tool errors
- Image resolution: 3x higher (3.75MP)
- Context window: 1M tokens
- First Claude model to pass "implicit-need tests" (inferring required tools without being told)
- Rakuten benchmark: 3x more production task resolutions vs. Opus 4.6
- Fast mode updated to Opus 4.7 (May 14, 2026)

---

### Source 4 — MCP Protocol Developments

**URLs:**
- https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/
- https://thenewstack.io/model-context-protocol-roadmap-2026/
- https://www.digitalapplied.com/blog/mcp-97-million-downloads-model-context-protocol-mainstream
- https://callsphere.ai/blog/model-context-protocol-mcp-2026-roadmap-scalability-enterprise-auth

**Key facts:**
- 97M monthly SDK downloads (March 2026), up from ~2M at launch (Nov 2024)
- 500+ public MCP servers; 18,000+ community-indexed servers
- v1.4 RC (April 2026) with breaking changes
- December 2025: Anthropic donated MCP to Agentic AI Foundation (AAIF) under Linux Foundation, co-founded with Block and OpenAI
- April 2026: AAIF MCP Dev Summit North America, NYC — ~1,200 attendees
- Supported by Anthropic, OpenAI, Google DeepMind
- 2026 roadmap priorities: transport scalability (Streamable HTTP), enterprise readiness (SSO, audit trails, gateway behavior), agent communication

---

### Source 5 — A2A Protocol (Agent-to-Agent)

**URLs:**
- https://zylos.ai/research/2026-03-26-agent-interoperability-protocols-mcp-a2a-acp-convergence
- https://www.digitalapplied.com/blog/ai-agent-protocol-ecosystem-map-2026-mcp-a2a-acp-ucp
- https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era
- https://www.ibm.com/think/topics/agent2agent-protocol
- https://blockeden.xyz/blog/2026/04/19/google-a2a-anthropic-mcp-web3-agent-protocol-war/

**Key facts:**
- Google's A2A protocol v1.0: in production at 150+ organizations
- A2A joined MCP under AAIF (December 2025)
- Complementary stack: MCP = agent↔tool, A2A = agent↔agent
- Supporting partners: Google, Microsoft, AWS, Salesforce, SAP, ServiceNow, Workday, IBM, Cisco, PayPal, LangChain, MongoDB, Cohere
- Joint MCP+A2A interoperability spec anticipated from AAIF

---

### Source 6 — Agent Frameworks Landscape

**URLs:**
- https://medium.com/@atnoforgenai/10-ai-agent-frameworks-you-should-know-in-2026-langgraph-crewai-autogen-more-2e0be4055556
- https://pecollective.com/blog/ai-agent-frameworks-compared/
- https://pooya.blog/blog/ai-agents-frameworks-local-llm-2026/
- https://www.turing.com/resources/ai-agent-frameworks
- https://github.com/agno-agi/agno

**LangGraph:**
- Surpassed CrewAI in GitHub stars (early 2026)
- Graph-based architecture; best for production/enterprise (audit trails, rollback)
- Medium learning curve; highest production readiness
- LangSmith observability, checkpointing, streaming

**CrewAI:**
- Role-based agent teams; lowest learning curve (20 lines to start)
- Removed LangChain dependency
- Growing ecosystem; limited checkpointing

**AutoGen (AG2):**
- Conversational agent interaction; model-agnostic

**Agno:**
- Rebranded early 2026; 39,000 GitHub stars, 400+ contributors
- Supports Claude Agent SDK, LangGraph, DSPy via AgentProtocol
- New: agno.context API, AgentFactory/TeamFactory/WorkflowFactory
- Added workspace tools with human-in-loop gating for destructive ops
- Background SSE resume/reconnect

**Emerging stacks:** LangGraph + MCP = "default production stack"; Mastra (TypeScript), PydanticAI (type-safe, FastAPI-style)

---

### Source 7 — OpenCode (Open-Source Alternative)

**URLs:**
- https://opencode.ai/
- https://nimbalyst.com/blog/claude-code-vs-codex-vs-opencode-definitive-comparison/
- https://www.infoq.com/news/2026/02/opencode-coding-agent/

**Key facts:**
- 150K+ (now 160K+) GitHub stars; 6.5-7.5M monthly active developers; 850-900 contributors
- MIT license; by anomaly team (SST/Serverless Stack creators)
- Written in Go; rich TUI (Bubble Tea)
- 75+ LLM provider support including local models (Ollama)
- Native MCP integration
- v1.2.0: SQLite session storage for multi-session stability
- GitHub Copilot official partnership (Jan 2026): Copilot subscribers authenticate at no extra cost

---

### Source 8 — Karpathy's CLAUDE.md Viral Phenomenon

**URLs:**
- https://pasqualepillitteri.it/en/news/1872/karpathy-claude-md-trending-github-llm-coding
- http://www.techtimes.com/articles/316798/20260518/karpathy-inspired-claudemd-passes-220000-combined-github-stars-four-rules-that-stop-ai-breaking.htm
- https://miraflow.ai/blog/karpathy-claude-md-100k-github-stars-ai-coding-2026

**Key facts:**
- 70-line CLAUDE.md file distilled from Andrej Karpathy's Jan 26, 2026 X observations
- 110K+ stars; #1 weekly GitHub Trending for 28 consecutive days; #94 all-time by stars
- 220,000+ combined stars across mirrors
- Karpathy's shift: from 80/20 manual/AI to 0/100 within weeks
- Four failure patterns: silent assumptions, code hypertrophy, collateral changes, no verifiable success criteria
- Four principles: Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution

**Quotes:**
> "Programming's Demise? Claude Code Father's Bombshell Quotes in Conversation with Karpathy" — 36kr.com

---

### Source 9 — Developer Burnout & Skepticism

**URLs:**
- https://www.axios.com/2026/04/04/ai-agents-burnout-addiction-claude-code-openclaw
- https://explainx.ai/blog/agentic-fatigue-vibe-coding-ai-developer-productivity-paradox
- https://dev.to/tanishka_karsulkar_ec9e58/the-trust-gap-paradox-why-massive-ai-adoption-in-2026-is-breeding-widespread-developer-skepticism-3dnb
- https://news.ycombinator.com/item?id=48002442 (HN: "Agentic Coding Is a Trap")

**Key findings:**
- Stack Overflow Developer Survey 2025: 84% use or plan to use AI tools (up from 76%); positive sentiment dropped to 60% (from 70%+); trust in AI accuracy: 29-33%; 46% actively distrust output
- "Brain fry" (BCG/UC Riverside): mental exhaustion from excessive AI oversight → increased errors, decision fatigue, turnover
- Double bind: longer hours to justify tool costs → burnout → degraded review quality → more rework → more tokens
- Axios (April 4, 2026): "They operate like slot machines" — Quentin Rousseau, Rootly CTO

**Notable quotes:**
- Andrej Karpathy: "state of AI psychosis" — describes 0/100 human/AI code ratio
- Simon Willison: "There is a limit on human cognition, in how much you can hold in your head at one time. And it's very easy to pop that stack."
- Armin Ronacher: "Many of us got hit by the agent coding addiction. It feels good, we barely sleep, we build amazing things."

---

### Source 10 — Hacker News: "Agentic Coding Is a Trap" Thread

**URL:** https://news.ycombinator.com/item?id=48002442

**Top comments:**
- **fnordpiglet** (463 points, 16 days ago): "They enthusiastically make mistakes but take feedback - at least up front" / "Learning more about systems in recent years than in 35 years of traditional programming"
- **byzantinegene**: juniors "overrely on agentic coding and do not know what they don't know"
- **keyle**: "cognitive debt" — personal knowledge gaps about their own agent-written code
- **larsfaye** (author): "Thinking in code is a form of thinking that is distinctly different...they are...interdependent"

**Discussion themes:** skill development, code quality, organizational knowledge loss, future of engineering

---

### Source 11 — MCP Security Vulnerabilities

**URLs:**
- https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/
- https://www.securityweek.com/claude-code-oauth-tokens-can-be-stolen-through-stealthy-mcp-hijacking/
- https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/
- https://thehackernews.com/2026/05/why-agentic-ai-is-securitys-next-blind.html

**Key disclosures:**
- CVE-2025-59536 & CVE-2026-21852: RCE and API key exfiltration via malicious CLAUDE.md project files (Check Point Research, Feb 25, 2026)
- MCP hijacking: MitM attack steals OAuth tokens via redirected MCP traffic
- mcp-remote RCE affecting 437,000+ installations
- SANDWORM_MODE worm compromising CI/CD pipelines
- OWASP Top 10 for Agentic Applications 2026: Agent Goal Hijacking (ASI01) = #1 risk
- MCP "design flaw": The Register, April 16, 2026 — 200K servers at risk

---

### Source 12 — Agentic IDE Landscape (Cursor 3.0, Windsurf 2.0)

**URLs:**
- https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/
- https://www.vibecodingacademy.ai/blog/windsurf-vs-cursor
- https://www.codecademy.com/article/agentic-ide-comparison-cursor-vs-windsurf-vs-antigravity

**Key facts:**
- JetBrains Jan 2026 survey: GitHub Copilot 29% workplace adoption; Cursor 18% (tied with Claude Code); Windsurf 8%
- Cursor 3 (April 2026): Agents Window, Design Mode, Composer 2 (200+ tok/s), cloud-to-local handoff
- Windsurf 2.0 (Cognition/Devin): SWE-1.5 at 950 tok/s (Cerebras), Cascade Hooks, free parallel agents; $20/mo Pro, $200/mo Max
- Cursor 3.0: $20/mo Pro; 7M+ MAU; $20B ARR
- Cursor 3.0 repositioned: "from IDE-with-AI to agent coordination platform"
- Windsurf owned by Cognition AI (Devin team)

---

### Source 13 — Multi-Agent Production Context

**URLs:**
- https://aetherlink.ai/en/blog/agentic-ai-multi-agent-orchestration-enterprise-guide-2026
- https://www.flowhunt.io/blog/multi-agent-ai-system/
- https://atlan.com/know/multi-agent-system-orchestration/
- https://medium.com/@angelosorte1/multi-agent-orchestration-in-2026-when-ai-systems-start-talking-to-each-other-and-things-can-04e55269a69a

**Key findings:**
- Context inconsistency (not pattern choice) = primary reason multi-agent orchestration fails in production
- Gartner: 1,445% surge in multi-agent system inquiries from Q1 2024 to Q2 2025
- Gartner Hype Cycle 2026: Agentic AI at Peak of Inflated Expectations; only 17% orgs deployed; 60%+ expect to within 2 years
- April 2026 described as "moment where AI stopped being experimental and started being infrastructure"
- Hermes Agent (Feb 2026): primary alternative to OpenClaw for "compound through use" agents
- Meta REA, Cognition/Devin, Karpathy's autoresearch loop: self-improvement already generating revenue

---

### Source 14 — Polymarket + AI Agent Trading

**URLs:**
- https://polymarket.com/predictions/ai
- https://finbold.com/claude-ai-powered-trading-bot-turns-1-into-3-3-million-on-polymarket/
- https://phemex.com/news/article/ai-trading-agent-claude-achieves-1322-return-on-polymarket-65634
- https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi

**Key facts:**
- Claude AI trading bot: $1 → $3.3M since Aug 2025 (sports arbitrage strategy)
- Another case: $313 → $438K by Jan 6, 2026; 98% win rate across 6,615 predictions
- Wallet: 1,322% return in 48 hours
- 92.4% of Polymarket wallets lose money overall
- Average arbitrage window: compressed from 12.3s (2024) to 2.7s (2026)
- SimpleFunctions MCP: 29 tools, 9,706+ active contracts on Kalshi + Polymarket
- Active Claude AI markets on Polymarket at https://polymarket.com/predictions/claude

---

### Source 15 — Self-Improving Agents

**URLs:**
- https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
- https://dev.to/aibughunter/ai-agents-in-april-2026-from-research-to-production-whats-actually-happening-55oc

**Key facts:**
- Evolutionary approaches: AlphaEvolve, ShinkaEvolve
- RL methods: SWE-RL, SAGE
- Memory systems: Mem0, MemOS, SimpleMem
- Production revenue generators: Meta REA, Cognition/Devin, Karpathy's autoresearch loop
- Hermes Agent (Feb 2026): "compounds through use rather than staying static"
- PydanticAI: type-safe framework with FastAPI-style developer experience

---

### Source 16 — GitHub Trending & Community Projects

**URLs:**
- https://www.askglitch.com/blog/top-5-trending-ai-github-repos-may-2026
- https://github.com/hesreallyhim/awesome-claude-code
- https://github.com/VILA-Lab/Dive-into-Claude-Code
- https://github.com/Zijian-Ni/awesome-ai-agents-2026
- https://github.com/agno-agi/agno
- https://github.com/quemsah/awesome-claude-plugins

**Key projects (May 2026):**
- Karpathy CLAUDE.md: 110K+ stars; #1 weekly trending for 28 days
- awesome-claude-code (hesreallyhim): curated skills, hooks, slash-commands, plugins
- awesome-ai-agents-2026 (Zijian-Ni): 300+ resources, 20+ categories
- VILA-Lab/Dive-into-Claude-Code: systematic analysis of Claude Code agent architecture
- OpenCode: 150K-160K stars, 6.5-7.5M MAU
- Claude Code: 82K GitHub stars

---

### Source 17 — Bluesky Integration

**URL:** https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/

- Bluesky's Attie: agentic social app on AT Protocol; natural language feed building powered by Claude
- Bluesky MCP server: enables profile queries, post search, timelines from AI assistants
- Automated Bluesky tech digest tool using Claude + MCP (Liz the Grey)

---

### Source 18 — Additional News Sources

**URLs:**
- https://dev.to/hiroki-ii-ai/ai-daily-digest-may-20-2026-agentic-workflows-coding-agents-embodied-ai-481
- https://www.cio.com/article/4107315/agentic-ai-in-2026-more-mixed-than-mainstream.html
- https://cloud.google.com/resources/content/ai-agent-trends-2026
- https://www.gartner.com/en/articles/hype-cycle-for-agentic-ai
- https://www.shashi.co/2026/05/anthropics-platform-bet-code-with.html
- https://arxiv.org/html/2604.14228v1 (VILA-Lab Dive into Claude Code paper)

**May 20, 2026 AI Daily Digest highlights:**
- Cursor 3.0: 7M+ MAU, $20B ARR; Agents Window for parallel agent management
- Pelican-Unified 1.0: first unified embodied AI model (66.03 WorldArena, 93.5 RoboTwin)
- Claude Code: Task Budgets, Background Agents, Agent Teams (research preview)
- LangGraph + MCP: emerging default production stack

---

## PLATFORM: Hacker News

### Threads identified:

| HN ID | Title | URL |
|-------|-------|-----|
| 47693047 | Claude Managed Agents | https://news.ycombinator.com/item?id=47693047 |
| 48002442 | Agentic Coding Is a Trap | https://news.ycombinator.com/item?id=48002442 |
| 47855284 | Show HN: Almanac MCP, turn Claude Code into Deep Research agent | https://news.ycombinator.com/item?id=47855284 |
| 44571730 | Ask HN: OpenAI Agents SDK vs. LangGraph, CrewAI, etc. | https://news.ycombinator.com/item?id=44571730 |
| 43491351 | Ask HN: Which agentic framework/tool do you prefer and why? | https://news.ycombinator.com/item?id=43491351 |
| 46733406 | LangChain, AutoGen, CrewAI, Temporal: What breaks when you need governance? | https://news.ycombinator.com/item?id=46733406 |
| 43468435 | We chose LangGraph to build our coding agent | https://news.ycombinator.com/item?id=43468435 |
| 44594835 | Show HN: RunAgent; Multi-Framework Agent Deployment | https://news.ycombinator.com/item?id=44594835 |
| 47180745 | Show HN: Crewship – Deploy AI agents to production in one command | https://news.ycombinator.com/item?id=47180745 |

**HN themes (from dev.to synthesis):**
- Hacker News keeps arguing about Claude Code, Codex, skills, MCP, and orchestration
- Four recurring truths: workflows matter more than demos, verification is the bottleneck, skills beat prompts, orchestration matters more than raw autonomy
- Focus shift: from whether tools work → how to make them reliable, trustworthy, and economically practical

**HN "Agentic Coding Is a Trap" highlights (HN #48002442):**
- fnordpiglet (463 pts): "They enthusiastically make mistakes but take feedback"
- byzantinegene: overreliance concern for junior devs
- keyle: "cognitive debt" — "Felt unprepared in a meeting about code they wrote using LLMs"
- larsfaye (author): "Thinking in code is a form of thinking that is distinctly different...interdependent"

---

## PLATFORM: Reddit

**Note:** Direct Reddit post retrieval was not available through web search. No specific Reddit thread URLs were indexed/returned. The following represents what's known from secondary references:

- Communities: r/ClaudeAI, r/LocalLLaMA, r/MachineLearning, r/singularity active for these topics
- No specific post URLs retrieved this run

---

## PLATFORM: X/Twitter (secondary references from news articles)

**Noted handles and quotes (sourced from news articles):**

| Handle | Quote/Context | Source |
|--------|--------------|--------|
| @karpathy (Andrej Karpathy) | "state of AI psychosis"; moved to 0/100 human/AI code ratio; "I moved in just a few weeks from 80% of code written manually" | Axios, Jan 26 2026 X post |
| @simonw (Simon Willison) | "There is a limit on human cognition...very easy to pop that stack" | Axios |
| @mitsuhiko (Armin Ronacher) | "Many of us got hit by the agent coding addiction. It feels good, we barely sleep, we build amazing things." | Axios |
| @dario_amodei | Revenue 80x Q1 2026 (via conference) | Multiple sources |
| Boris Cherny (Anthropic) | Async code dev patterns, routines as "higher-order prompts" | SimonWillison liveblog |

---

## PLATFORM: YouTube

**URLs found:**
- https://www.youtube.com/watch?v=EsTrWCV0Ph4 — "AI Agents Full Course 2026: Master Agentic AI (2 Hours)"
- https://www.youtube.com/watch?v=eooxQPZQUEM — "Agentic AI Full Course for Beginners 2026 | Intellipaat"
- https://www.youtube.com/watch?v=-rUKr8JDits — "Agentic AI Full Course 2026 | Edureka"
- https://www.youtube.com/watch?v=RPoGqy_mv3s — "AI Agents Full Course 2026 | Edureka Live"
- https://www.youtube.com/watch?v=wDs2egmmjFU — "Agentic AI Full Course for Free 2026 | Intellipaat"
- https://www.youtube.com/watch?v=X_0a2BlptIc — "Agentic AI Course Free 2026 | Intellipaat"
- https://www.youtube.com/watch?v=MyLyDSlc_7Y — "AI Agent Full Course For Beginners 2026 | Edureka Live"

**Channels dominant:** Intellipaat, Edureka, Maker School — covering full courses for beginners

---

## PLATFORM: TikTok

**Limited data:** Search returned general TikTok discover pages. No specific viral video URLs with engagement metrics retrieved. OpenClaw creator Peter Steinberger went viral showing what an agent can actually do beyond chatting; subsequently hired by OpenAI.

---

## PLATFORM: GitHub (Trending)

| Repo | Stars | Notes | URL |
|------|-------|-------|-----|
| Karpathy CLAUDE.md (Forrest Chang) | 110K+ (220K+ combined) | #1 weekly trending, 28 days | (see Karpathy section) |
| OpenCode | 150K-160K | 6.5-7.5M MAU, Go, MCP-native | https://opencode.ai/ |
| Claude Code (Anthropic) | 82K | CLI agent | https://code.claude.com |
| agno-agi/agno | 39K | Python multi-agent framework | https://github.com/agno-agi/agno |
| awesome-ai-agents-2026 | 300+ resources | curated list | https://github.com/Zijian-Ni/awesome-ai-agents-2026 |
| VILA-Lab/Dive-into-Claude-Code | — | academic analysis | https://github.com/VILA-Lab/Dive-into-Claude-Code |
| hesreallyhim/awesome-claude-code | — | Claude Code plugins/skills | https://github.com/hesreallyhim/awesome-claude-code |

---

## PLATFORM: Polymarket

**Active AI prediction markets:**
- https://polymarket.com/predictions/ai
- https://polymarket.com/predictions/claude
- Claude AI trading bots active on platform; performance range: $1 → $3.3M (extreme case); 1,322% in 48 hrs (reported)
- No specific open market with odds/volume retrieved this run

---

## RAW STATS SUMMARY

- Web sources indexed: 40+ URLs
- Hacker News threads: 9 identified
- YouTube videos: 7 found
- GitHub repos: 7 notable
- Reddit: 0 direct posts retrieved
- X/Twitter: 5 handle quotes from secondary sources
- Bluesky: 1 major news item (Attie app)
- TikTok: 0 direct video URLs retrieved
- Polymarket: 2 market URLs, multiple performance reports

---

*Raw output generated: 2026-05-20. Pipeline: plan → retrieve → normalize → fuse → rerank → cluster → render.*
