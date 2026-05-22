# Agentic AI — Raw Research Output
**Date:** 2026-05-22
**Topic:** AI agents, agentic coding, multi-agent orchestration, MCP protocol, Claude Code, Anthropic Claude updates and releases, agent frameworks (LangGraph, CrewAI, AutoGen, Agno), agent-to-agent communication, tool use patterns, self-improving agents, production agent deployments, developer experience, community reactions

---

## PLATFORM: Hacker News

### HN Item: Claude Managed Agents
- URL: https://news.ycombinator.com/item?id=47693047
- Points: 169 | Comments: 87
- Top commenters:
  - **jameslk**: "We're in the early days of agentic frameworks, like the pre-PHP web." Argues constant reinvention makes locking in a poor strategy.
  - **dmix**: Agrees with the pre-PHP analogy; notes fragmentation across vector DBs and model vendors.
  - **gck1**: Contends frameworks are "fundamentally incompatible with non-deterministic LLM technology."
  - **cedws**: "Anthropic aims to control the platform for IPO positioning rather than remaining 'just a token pipeline.'"
  - **spwa4**: Defends custom harnesses for superior control; notes they enable cost optimization through context limiting.
- Themes: vendor lock-in, multi-model orchestration, infrastructure management burden, output quality governance.

### HN Item: Claude Managed Agents Overview
- URL: https://news.ycombinator.com/item?id=47697641
- Points: 40
- Notable comments:
  - **bad_haircut72**: "Their harness sucks" — argues Anthropic should let community build agents instead.
  - **bob1029**: "Custom agents using the low level completion APIs tend to outperform these generic tools, especially when you are working with complex problems."
  - **steve_adams_86**: Company prioritizes speed over perfection in a competitive market.
  - **potsandpans**: Anthropic releases "dozens of products every three months" while Claude Code becomes increasingly complex and buggy.
  - **danieldisu**: Real strategy is vendor lock-in for enterprise clients to prevent switching.

### HN Item: An update on recent Claude Code quality reports
- URL: https://news.ycombinator.com/item?id=47878905
- Points: 942 | Comments: 732
- Source: anthropic.com
- Core: Anthropic shipped a bug on March 26 that caused Claude to clear older thinking from idle sessions (>1 hour) every turn instead of once, making the model appear forgetful. Fixed April 10.
- Key quote from **bcherny** (Anthropic engineer): "when you let a session idle for >1 hour...that would be >900k tokens written to cache all at once, which would eat up a significant % of your rate limits."
- User concerns: silent degradation, loss of reasoning, cost opacity, broken long-session expectations.

### HN Item: Ask HN: Is it just me or is Claude Code getting worse?
- URL: https://news.ycombinator.com/item?id=47936579
- Points: 32 | Comments: 24
- Representative quotes:
  - "Claude Code itself is complete trash...OpenAI lets you use whatever harness you want and its a beast."
  - "These days Claude Code can barely even remember its CLAUDE.MD instructions."
  - "Latest version of CC feels lobotomized."

### HN Item: Claude Code and the Great Productivity Panic of 2026
- URL: https://news.ycombinator.com/item?id=47467922
- Points: 46 | Comments: 16 | Posted ~April 4, 2026
- Original article: https://www.bloomberg.com/news/articles/2026-02-26/ai-coding-agents-like-claude-code-are-fueling-a-productivity-panic-in-tech
- Top comments:
  - **PeterStuer**: "After a 3 hour frantic agentic coding stint, you are just mentally exhausted from the sheer speed and volume of actions and decisions taken."
  - **npilk**: "spending time working with Claude Code leaves me feeling...a thin, jittery, frayed sort of weariness."
  - **master_crab**: "everyone has to do more to keep up with said productivity."

### HN Item: Show HN: Almanac MCP, turn Claude Code into a Deep Research agent
- URL: https://news.ycombinator.com/item?id=47855284

### HN Item: Claude Code Best Practices for Agentic Coding
- URL: https://news.ycombinator.com/item?id=43735550

### HN Item: Claude Code SDK
- URL: https://news.ycombinator.com/item?id=44032777

### HN Item: Agentic Coding Recommendations
- URL: https://news.ycombinator.com/item?id=44255608

---

## PLATFORM: Reddit

### Trending Reddit Posts About AI Agents (May 2026)
- Source: https://gist.github.com/heiba-wk/990804e51dc01b1b8804d1bad25ca01a (404)
- Per aggregators: discussions centered on "autonomous agents and their real-world dangers, particularly regarding production access" — hundreds of upvotes, 1,000+ comments.
- r/ClaudeCode: 4,200+ weekly contributors as of late 2025
- r/ChatGPTCoding: dominant multi-tool subreddit; 2,500+ weekly contributors
- r/Codex: 1,200+ weekly contributors
- r/vibecoding: 89,000 total members
- Notable September 2025 thread: "Claude Is Dead" (r/Anthropic, 841 upvotes) triggered by usage caps

### Community Sentiment on Claude Code (Reddit)
- Source: https://www.aitooldiscovery.com/guides/claude-code-reddit
- 65.3% of surveyed developers preferred Codex directly; Claude Code generated 4x more discussion volume.
- "Claude Code is the current standard all others are measured against." — gorjusborg, HN
- "Claude Code is used 80% of the time with Codex the other 20%." — extr, HN/Reddit

---

## PLATFORM: X / Twitter

### Boris Cherny (Anthropic engineer) viral post
- URL: https://x.com/simonw/status/2052055655230706032 (Simon Willison live blog tweet)
- In January 2026, Boris Cherny shared his agentic setup on X; single post accumulated 104,000 saves and 8.1 million views.
- Revealed running "a few thousand" AI coding agents overnight from his phone.

### Andrej Karpathy joining Anthropic
- URL: https://x.com/karpathy/status/2056753169888334312
- "Personal update: I've joined Anthropic. I think the next few years at the frontier of LLMs will be especially formative. I am very excited to join the team here and get back to R&D."

### Simon Willison live blog tweet
- "I'm at the Claude w/ Code event in San Francisco, and I'll be live blogging the keynote here"

---

## PLATFORM: Web / News

### Code with Claude 2026 — Live Blog (Simon Willison)
- URL: https://simonwillison.net/2026/May/6/code-w-claude-2026/
- Event: May 6, 2026, San Francisco (London May 19, Tokyo June 10)
- Key announcements:
  - Doubled Claude Code five-hour limit for Pro, Max, Enterprise
  - SpaceX Colossus data center partnership (Memphis)
  - API volume up 17x year-on-year
  - Multi-agent orchestration (public beta) — agent fleets for complex tasks
  - Outcomes — set success criteria for independent iteration (public beta)
  - Dreaming — agents inspect previous sessions to self-improve overnight (research preview)
  - Code Review tool; CI auto-fix; Security Reviews; Remote Agents; Desktop app
  - Advisor strategy: smaller models consulting Opus for better results at lower cost
  - Mercado Libre aiming for "90% autonomous coding by Q3 this year"
- Key quotes: "Today is about how we are making our products work better for you." — Ami Vora

### AI Weekly: Google Reshapes the Coding Stack (Week of May 13-20, 2026)
- URL: https://dev.to/alexmercedcoder/ai-weekly-google-reshapes-the-coding-stack-claude-pulls-ahead-and-the-agent-protocol-stack-17co
- Claude Code: 46% highest "most loved" rating among 906 engineers (Pragmatic Engineer survey, Feb 2026)
- ~4% of public GitHub commits from Claude Code as of March; projected 20% by year-end
- Codex: 3 million weekly active users (March 2026)
- GitHub Copilot most adopted at 29% workplace usage; Claude Code and Cursor tied at 18%
- First time more US businesses paid for Claude than ChatGPT (April 2026, Ramp AI Index)
- SemiAnalysis estimated Claude Code at $2.5B annualized run rate (Feb 2026)
- Anthropic: ~80x annualized growth in single quarter (per CEO Dario Amodei, May 5)
- Stainless acquisition (May 18); KPMG alliance (May 19, 276,000+ employees); Gates Foundation $200M (May 14)
- Andrej Karpathy joined Anthropic pretraining team (May 19)
- WebMCP proposed W3C standard (Google/Microsoft): `navigator.modelContext` in browser
- A2A v1.2 at 150 organizations in production; governed by Linux Foundation AAIF
- Google Antigravity 2.0 launched May 19; free tier ends June 18
- June 15: Anthropic separates programmatic usage into credit pools

### Claude Code Source Leak (March 31, 2026)
- URLs: 
  - https://www.infoq.com/news/2026/04/claude-code-source-leak/
  - https://venturebeat.com/technology/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know
  - https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html
  - https://www.zscaler.com/blogs/security-research/anthropic-claude-code-leak
- 59.8 MB JavaScript source map in @anthropic-ai/claude-code v2.1.88
- ~513,000 lines of TypeScript, 1,906 files
- Coincided with Axios npm supply chain attack (March 31)
- Security concerns: CVE-2025-59536, CVE-2026-21852 (RCE, API key exfiltration via malicious MCP servers, hooks)
- Anthropic: "No sensitive customer data or credentials were involved or exposed"

### MCP Protocol State
- URL: https://thenewstack.io/model-context-protocol-roadmap-2026/
- URL: https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026
- URL: https://explore.n1n.ai/blog/mcp-tools-2026-model-context-protocol-guide-2026-05-12
- Anthropic donated MCP to Linux Foundation AAIF in December 2025
- MCP Dev Summit North America (New York, April 2026): ~1,200 attendees
- Community servers for GitHub, Slack, PostgreSQL, Stripe, Figma, Docker, Kubernetes, and 200+ tools
- 2026 roadmap priorities: transport scalability, agent-to-agent communication, governance, enterprise readiness (audit trails, SSO)
- Gartner: 40% of enterprise apps will include task-specific AI agents by end of 2026

### Agent-to-Agent (A2A) Protocol
- URL: https://atlan.com/know/google-a2a-protocol/
- URL: https://www.programming-helper.com/tech/agent-to-agent-protocol-2026-google-a2a-standard
- URL: https://onereach.ai/blog/what-is-a2a-agent-to-agent-protocol/
- URL: https://www.digitalapplied.com/blog/ai-agent-protocol-ecosystem-map-2026-mcp-a2a-acp-ucp
- URL: https://explore.n1n.ai/blog/google-adk-1-0-a2a-protocol-multi-agent-standard-2026-05-04
- 150+ organizations in production
- Agent Card: describes name, description, version, endpoint, modalities, auth, capability flags
- Seven task states: submitted, working, input-required, completed, failed, canceled, rejected
- v1.2 includes cryptographically signed agent cards
- Pillar architecture: MCP (tool calls) + A2A (inter-agent) + ADK (orchestration SDK)

### Google I/O 2026 Agent Announcements
- URLs:
  - https://cloud.google.com/blog/topics/developers-practitioners/io26-news-for-agent-developers-on-google-cloud
  - https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era
  - https://developers.googleblog.com/agents-adk-agent-engine-a2a-enhancements-google-io/
  - https://virtualizationreview.com/articles/2026/05/19/google-io-26-fills-out-enterprise-agent-stack-with-managed-agents-adk-2,-d-,0.aspx
- Antigravity 2.0 (standalone coding agent desktop app); ADK 2.0 with graph-based workflows; Managed Agents API
- Project Mariner: 83.5% on WebVoyager benchmark; handles 10 concurrent tasks
- Skill Registry (public preview); Workspace Studio (no-code); 200+ models in Model Garden
- ADK: Python, Go, Java (stable 1.0); TypeScript available; Kotlin beta for mobile
- Quote: "Pick the rung that fits the project. Bring whatever coding agent your team prefers."
- Google rebrand: Vertex AI → Gemini Enterprise Agent Platform

### Agent Framework Landscape 2026
- URLs:
  - https://pecollective.com/blog/ai-agent-frameworks-compared/
  - https://pooya.blog/blog/ai-agents-frameworks-local-llm-2026/
  - https://dev.to/emperorakashi20/crewai-vs-langgraph-vs-autogen-which-multi-agent-framework-should-you-use-in-2026-5h2f
  - https://medium.com/@atnoforgenai/10-ai-agent-frameworks-you-should-know-in-2026-langgraph-crewai-autogen-more-2e0be4055556
- LangGraph v0.4 (April 2026): improved state persistence and human-in-the-loop checkpoints; used by Klarna, LinkedIn, Uber
- CrewAI: enterprise-grade observability, scheduling for multi-agent coordination
- AutoGen: reached 1.0 GA; v2 API as default; Microsoft shifted focus to broader Agent Framework
- LangGraph surpassed CrewAI in GitHub stars (early 2026); owned production/enterprise tier
- Market positioning: LangGraph (production), Smolagents (HuggingFace/research), CrewAI/AutoGen (accessible middle)

### Anthropic Agentic Coding Trends Report 2026
- URLs:
  - https://getbeam.dev/blog/anthropic-agentic-coding-trends-2026.html
  - https://pathmode.io/blog/orchestration-era-needs-intent
- 78% of Claude Code sessions involve multi-file edits (Q1 2026), up from 34% (Q1 2025)
- Average session length: 4 min (2025) → 23 min (2026)
- ~47 tool calls per session
- 89% acceptance when agents provide diff summaries; 62% for raw output
- 40% fewer errors with well-maintained context files; 55% faster completion
- Coding phase: 60-70% faster; testing 50-60%; code review 30-40%
- Key shift: "context engineering" has replaced "prompt engineering" as critical skill
- Quote: "The era of the single AI assistant is ending. The future is a team of specialized agents."

### Claude Code Changelog (May 2026)
- Source: https://raw.githubusercontent.com/anthropics/claude-code/refs/heads/main/CHANGELOG.md
- v2.1.147 (May 22): Pinned background sessions, /code-review command, improved auto-updater
- v2.1.145 (May 20): `claude agents --json`, status line GitHub repo/PR info
- v2.1.144 (May 19): /resume for background sessions, MCP startup 2s faster
- v2.1.143 (May 15): Plugin dependency enforcement, context cost estimates in marketplace
- v2.1.142 (May 14): Fast mode upgraded to Opus 4.7 (from 4.6), new `claude agents` dispatch flags
- v2.1.141 (May 13): `CLAUDE_CODE_SESSION_ID` env var, Rewind "Summarize up to here"
- v2.1.140 (May 11): Improved agent matching, updated agent color palette
- v2.1.139 (May 11): Agent view (Research Preview), `/goal` command, `/scroll-speed`
- v2.1.136 (May 9): `settings.autoMode.hard_deny`, enterprise feedback via OpenTelemetry
- v2.1.133 (May 7): `worktree.baseRef`, custom sandbox paths
- v2.1.132 (May 6): `CLAUDE_CODE_SESSION_ID` for Bash subprocess

### Claude Model Releases
- URLs:
  - https://releasebot.io/updates/anthropic/claude-code
  - https://support.claude.com/en/articles/12138966-release-notes
  - https://www.365i.co.uk/news/2026/02/18/claude-sonnet-4-6-release-near-flagship-ai/
- Claude Opus 4.7 (April 16, 2026): SWE-bench Verified 80.8% → 87.6%; 3x image resolution (2,576px); xhigh effort level; verifies own outputs
- Claude Sonnet 4.6 (February 17, 2026): flagship-level performance at 1/5 the price
- No Claude Sonnet 4.7 confirmed; next Sonnet is 4.8 (per leaked Claude Code source)
- Advisor strategy: Sonnet + Opus advisor improved BrowseComp and Terminal-Bench 2.0 scores at lower cost

### Self-Improving Agents
- URLs:
  - https://arxiv.org/pdf/2603.19461 (HyperAgents)
  - https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
  - https://github.com/facebookresearch/Hyperagents
- HyperAgents (Meta/UBC/Oxford/NYU, March 23, 2026): DGM-Hyperagents transfers self-improvement strategies across domains (robotics → Olympiad math grading)
- AI agents doubling task completion capacity every 7 months over 6 years; rate accelerated to every 4 months in 2024-2025
- Current frontier: 50% reliability time horizon ~50 minutes (vs <15 minutes a year ago)

### Developer Experience & Burnout
- URLs:
  - https://leaddev.com/ai/addictive-agentic-coding-has-developers-losing-sleep
  - https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
  - https://siddhantkhare.com/writing/ai-fatigue-is-real
- 19.6% rise in out-of-hours commits (Multitudes study, 500+ engineers)
- 46% increase in Saturday productive hours; 58% increase in Sunday productive hours (ActivTrak, 163,638 employees)
- Steve Yegge: "The better you get at it, the more you want to use it...It doles out dopamine and adrenaline shots like they're on a fire sale."
- Eren Celebi (WPP): "I'm coding into later hours of the day not because I'm told to do so, but because I can't get myself to get up from the computer."
- "Code slop" — AI-generated code measurably has more vulnerabilities; but security agents integrated into workflow reduce vulnerability rates below human-only teams

### Codex vs Claude Code Comparison
- URLs:
  - https://www.morphllm.com/comparisons/codex-vs-claude-code
  - https://composio.dev/content/claude-code-vs-openai-codex
  - https://www.mindstudio.ai/blog/codex-vs-claude-code-2026
- Claude Code: Opus 4.7, 1M-token context, 87.6% SWE-bench Verified
- Codex: GPT-5.4, 272K default context, leads Terminal-Bench 2.0 at 77.3%
- 65% preferred Codex day-to-day; blind code reviews rated Claude Code cleaner 67% of the time
- Claude Code used 4x more tokens than Codex on identical tasks
- Common pattern: Claude Code for planning/architecture, Codex for tightly scoped follow-up tasks

### Bluesky / Social
- URLs:
  - https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/
  - https://futurism.com/artificial-intelligence/bluesky-users-disgust-new-ai
  - https://futurumgroup.com/insights/blueskys-attie-backlash/
- Bluesky unveiled Attie (March 2026): first "agentic" app for atproto using Claude under the hood; vibe-code custom feeds
- Users blocked Attie en masse; major backlash about AI manipulation of feeds
- 45% of organizations cite data privacy as top AI adoption concern (Futurum 1H 2026 survey)

### Polymarket
- URLs:
  - https://polymarket.com/predictions/ai
  - https://polymarket.com/event/openai-announces-it-has-achieved-agi-before-2027
  - https://polymarket.com/predictions/agi
  - https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading
  - https://predik.io/en/blog/nvidia-agi-mercados-prediccion-2026-jensen-huang-en
  - https://github.com/Polymarket/agents
- 101 live AGI prediction markets; 20+ live AI prediction markets
- OpenAI AGI before 2027: 85.5% implied probability "No"
- Jensen Huang (NVIDIA) declared AGI achieved (April 2026) → Polymarket AGI-before-2027 surged to ~23%
- Polystrat AI agent (Olas, launched Feb 2026): 4,200+ trades in a month, up to 376% returns
- 30%+ of Polymarket wallets using AI agents

### Security Concerns
- URLs:
  - https://thehackernews.com/2026/05/why-agentic-ai-is-securitys-next-blind.html
  - https://thehackernews.com/2026/05/your-ai-agents-are-already-inside.html
  - https://www.securityweek.com/claude-code-oauth-tokens-can-be-stolen-through-stealthy-mcp-hijacking/
  - https://github.blog/security/hack-the-ai-agent-build-agentic-ai-security-skills-with-the-github-secure-code-game/
  - https://www.securityweek.com/ai-coding-agents-could-fuel-next-supply-chain-crisis/
- Claude Code OAuth tokens vulnerable to MCP hijacking
- AI coding agents could fuel next supply chain crisis
- GitHub built "immune system" for AI coding agents running on MCP (May 7, 2026)

### Additional Web Sources
- https://addyosmani.com/blog/code-agent-orchestra/ — multi-agent coding orchestration patterns by Addy Osmani
- https://shipyard.build/blog/claude-code-multi-agent/ — practical orchestration setup guide
- https://devtoolpicks.com/blog/anthropic-self-hosted-claude-agents-mcp-tunnels-indie-hackers-2026 — self-hosted sandboxes + MCP tunnels
- https://9to5mac.com/2026/05/07/anthropic-updates-claude-managed-agents-with-three-new-features/ — Dreaming, Outcomes, Multi-agent
- https://9to5mac.com/2026/05/19/anthropic-enhances-claude-managed-agents-with-two-new-privacy-and-security-features/ — MCP tunnels, self-hosted sandboxes
- https://theaiinsider.tech/2026/05/20/google-i-o-2026-how-the-search-giant-is-rebuilding-itself-around-agentic-ai/
- https://techcrunch.com/2026/05/19/openai-co-founder-andrej-karpathy-joins-anthropics-pre-training-team/
- https://palma.ai/blog/claude-code-source-leak-what-it-means-for-mcp — source leak analysis
- https://dev.to/hiroki-ii-ai/ai-daily-digest-may-20-2026-agentic-workflows-coding-agents-embodied-ai-481
- https://earezki.com/ai-news/weekly-summary-2026-05-17/

---

## PLATFORM: YouTube

### Video: Introducing multi-agent orchestration - Claude Code, Codex...
- URL: https://www.youtube.com/watch?v=RWT3sh68PWE
- Published ~May 19, 2026 (3 days before research date)

### Video: Claude AI Full Tutorial: From Basics to Agentic AI (2026)
- URL: https://www.youtube.com/watch?v=XTWb5oEfqdY
- Published April 12, 2026

### Video: Claude Code: Build Your First AI Agent
- URL: https://www.youtube.com/watch?v=gHB4JFG9i3k
- Published March 23, 2026

### Video: Build Your Own Claude Code | Full AI Coding Agent Tutorial
- URL: https://www.youtube.com/watch?v=k_D_C3ExypU
- Published ~May 19, 2026

### Video: Multitasking With Agents: My 2026 Workflow
- URL: https://www.youtube.com/watch?v=eFf2NszosQo
- Published ~3 weeks before research date

### Video: Claude Agent SDK: Build Your First AI Agent in 30 Minutes
- URL: https://www.youtube.com/watch?v=sCIS05Qt79Y

---

## PLATFORM: GitHub

### Repos
- https://github.com/facebookresearch/Hyperagents — HyperAgents (March 23, 2026 paper)
- https://github.com/wshobson/agents — multi-agent orchestration for Claude Code
- https://github.com/ARUNAGIRINATHAN-K/awesome-ai-agents-2026 — 300+ agents, frameworks
- https://github.com/caramaschiHG/awesome-ai-agents-2026 — comprehensive agent list
- https://github.com/EvoAgentX/Awesome-Self-Evolving-Agents — self-evolving agent survey
- https://github.com/Polymarket/agents — Polymarket AI trading agents
- https://github.com/google/skills — Google Skill Registry
- https://github.com/google/agents-cli — Google Agents CLI
