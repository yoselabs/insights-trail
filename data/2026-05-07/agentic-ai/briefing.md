# Agentic AI — Daily Briefing
**Date:** 2026-05-07
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web (news, blogs, official announcements, developer community)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 11 stories | varied points/comments | Rate limits prevented full comment extraction on 3 threads |
| GitHub | 10+ repos | 103K+ stars (Hermes Agent alone) | Key repos: hermes-agent, A2A, tokio-prompt-orchestrator, claude-code-mcp |
| Web | 50+ pages | — | News, blogs, official docs, dev community (Dev.to, Medium, InfoQ, MIT Tech Review, Fortune, The Register) |
| Reddit | 0 | — | Domain blocked by search agent |
| X/Twitter | 0 | — | Excluded per research instructions |
| YouTube | 0 | — | No video-level data returned |
| TikTok | 0 | — | No data found |
| Instagram | 0 | — | No data found |
| Bluesky | 0 | — | No platform-specific posts returned |
| Polymarket | 0 | — | No relevant prediction markets found |

---

## Synthesized Findings

### 1. Anthropic's "Code with Claude 2026" Conference Redraws the Agentic Map

On May 6, Anthropic held its first-ever developer conference — Code with Claude 2026 — in San Francisco (London May 19, Tokyo June 10). Simon Willison's live blog ([simonwillison.net](https://simonwillison.net/2026/May/6/code-w-claude-2026/)) captured the most consequential Claude Code and Managed Agents announcements of the year so far.

**Key product launches:**
- **Claude Managed Agents** now ships three headline features: multi-agent orchestration for complex task delegation, an "Outcomes" feature to define success criteria, and **"Dreaming"** — a self-improvement research preview in which agents inspect their own session histories to improve future performance.
- **CI Auto-fix**: Claude Code can now automatically submit PR fixes on CI failures.
- **Security Reviews**: integrated security scanning within the agentic coding pipeline.
- **Remote Agents**: control your laptop Claude agent via phone.
- **Desktop app**: full-screen GUI with preview panels.
- **Advisor strategy**: Sonnet can call Opus as a consultant, achieving "frontier model quality at 5x lower cost."
- **Routines**: described by product engineer Boris Cherny as "higher-order prompts" — async automations that let developers wake up to completed PRs.
- **Infrastructure flex**: SpaceX Colossus data center partnership; Anthropic API volume up **17x year-on-year**.
- The five-hour rate limit for Pro, Max, and Enterprise was doubled.

Quotes from the stage:
> "Today is about how we are making our products work better for you." — Ami Vora

> "The model intelligence has got strong enough to support all of this." — Dianne Na Penn

> "Routines are higher-order prompts." — Boris Cherny

**Cross-platform resonance**: HN, web dev blogs, InfoQ

---

### 2. MCP Protocol Donated to Linux Foundation — Becomes the TCP/IP of Agents

Anthropic officially donated the Model Context Protocol to the **Agentic AI Foundation (AAIF)**, a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI — with Google, Microsoft, AWS, Cloudflare, and Bloomberg as supporting members ([full announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)).

By the time of the donation (December 9, 2025), MCP had achieved:
- **10,000+** active public MCP servers
- **97 million+** monthly SDK downloads (Python + TypeScript)
- Integration in ChatGPT, Cursor, Gemini, Microsoft Copilot, VS Code

Block's Goose and OpenAI's AGENTS.md joined MCP as founding AAIF projects. The A2A (Agent-to-Agent) protocol, separately contributed by Google to the Linux Foundation, was positioned as MCP's complement: **MCP = agent-to-tool; A2A = agent-to-agent**.

HN community interest in MCP multiplied across the last 30 days — threads on remote MCP support, MCP spec version 2025-06-18 changes, and how to manage multiple MCP servers reflect practitioner-level adoption:
- [Remote MCP Support in Claude Code (HN)](https://news.ycombinator.com/item?id=44312363)
- [MCP Specification – version 2025-06-18 changes (HN)](https://news.ycombinator.com/item?id=44314289)
- [Ask HN: How do you manage multiple MCP servers in Claude Code?](https://news.ycombinator.com/item?id=45114196)
- [Show HN: Representing Agents as MCP Servers](https://news.ycombinator.com/item?id=44053754)
- [Show HN: MCP plugin that lets Claude autonomously pay for APIs via Lightning](https://news.ycombinator.com/item?id=47669920)
- [GitHub MCP Server](https://github.com/github/github-mcp-server)
- [claude-code-mcp (agent inside an agent)](https://github.com/steipete/claude-code-mcp)

**Cross-platform resonance**: HN, GitHub, official announcements, developer blogs

---

### 3. Anthropic Charges into Wall Street — Finance Agents + Claude Opus 4.7

On May 5, Anthropic held an invite-only financial services briefing in New York with JPMorgan Chase CEO Jamie Dimon on stage alongside Dario Amodei — their first shared public appearance. The company launched:

- **10 pre-built Claude agent templates** for financial workflows: pitchbooks, earnings analysis, credit memos, underwriting, KYC/KYB, month-end close, statement audits, insurance claims — available as Claude Cowork plugins, Claude Code plugins, and Claude Managed Agent cookbooks.
- **Claude Opus 4.7** scored **64.4%** on Vals AI's Finance Agent benchmark ([Vals AI](https://www.vals.ai/benchmarks/finance_agent)).
- **Microsoft 365 integration**: Claude now operates across Excel, PowerPoint, Word, and Outlook.
- **Moody's** embedded its full analytics platform inside Claude via MCP. Verisk, Dun & Bradstreet, Experian, and Zoom also launched MCP connectors.
- **$1.5B joint venture** announced the prior day: Anthropic, Blackstone, Hellman & Friedman (~$300M each), Goldman Sachs ($150M), Apollo, General Atlantic, GIC, Sequoia.

> "It created a huge dashboard...with all the backup, and all the research, and it was very accurate." — Jamie Dimon on using Claude Code

> Dario Amodei cited "annualized growth of roughly 80x in one quarter."

Sources: [Fortune](https://fortune.com/2026/05/05/anthropic-wall-street-financial-services-agents-jamie-dimon/) | [The Register](https://www.theregister.com/software/2026/05/05/anthropic-unleashes-finance-agents-for-claude/5225868) | [Anthropic finance agents page](https://www.anthropic.com/news/finance-agents) | [Claude Opus 4.7 benchmarks](https://llm-stats.com/blog/research/claude-opus-4-7-launch) | [Dun & Bradstreet](https://www.prnewswire.com/news-releases/dun--bradstreet-brings-risk--compliance-workflows-to-anthropics-claude-302762851.html) | [Verisk](https://www.verisk.com/company/newsroom/verisk-brings-its-trusted-analytics-and-generative-ai-capabilities-directly-into-anthropics-claude/)

**Cross-platform resonance**: Financial press, official announcements, enterprise partner announcements

---

### 4. Multi-Agent Orchestration: From Experiments to Production Infrastructure

MIT Technology Review ([April 21, 2026](https://www.technologyreview.com/2026/04/21/1135654/agent-orchestration-ai-artificial-intelligence/)) declared coordination "the new scale frontier" — and the community demonstrations from the past 30 days back it up.

**The 24-agent benchmark**: A developer named Shmungus ran 24 concurrent Claude Code agents on consumer hardware (RTX 4070), beating Anthropic's own record of 16, using a Tokio/Rust orchestrator routing through local Mistral 7B ([HN thread](https://news.ycombinator.com/item?id=47099597), [GitHub](https://github.com/Mattbusel/tokio-prompt-orchestrator)). Key innovation: agents coordinate *indirectly* via CLAUDE.md/AGENTS.md governance files rather than direct agent-to-agent calls. Results: 683 tests, zero failures; 1.53:1 test/production ratio enforced via pre-commit hooks.

**Roundtable MCP**: Orchestrates Claude Code, Cursor, Gemini, and Codex in parallel through the MCP protocol for specialized analysis (Gemini on React performance, Codex on code quality, Cursor on accessibility, Claude on business logic). Reduces multi-agent coordination from 20+ to 2–5 minutes ([HN](https://news.ycombinator.com/item?id=45374908)).

**Agents Council**: Lightweight MCP server for local agent-to-agent communication, inspired by Andrej Karpathy's "LLM Council" concept ([HN](https://news.ycombinator.com/item?id=46517090)).

**Almanac MCP**: Turns Claude Code into a Deep Research agent via web access ([HN](https://news.ycombinator.com/item?id=47855284)).

**Production patterns** crystallizing from enterprise deployments:
- Manager agent + specialist subagents as the dominant architecture
- Multi-agent incident response: **100% actionable recommendation rate** vs. 1.7% for single-agent (per [MindStudio](https://www.mindstudio.ai/blog/multi-agent-orchestration-patterns))
- LLM for reasoning, deterministic code for execution ("let AI do the thinking, code do the doing")
- Human-in-the-Loop is table stakes, not optional

Sources: [MIT Tech Review](https://www.technologyreview.com/2026/04/21/1135654/agent-orchestration-ai-artificial-intelligence/) | [Codebridge guide](https://www.codebridge.tech/articles/mastering-multi-agent-orchestration-coordination-is-the-new-scale-frontier) | [47billion blog](https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/) | [Kanerika](https://kanerika.com/blogs/ai-agent-orchestration/) | [Multi-agent complete guide](https://letusassume.com/multi-agent-ai-orchestration/)

**Cross-platform resonance**: HN, GitHub, enterprise tech press, dev blogs

---

### 5. Framework Wars 2026: LangGraph Leads, Google ADK Surprises, AutoGen Fades

The agent framework landscape exploded. Key shifts:

| Framework | Status | Key 2026 Move |
|---|---|---|
| **LangGraph** | Leader, enterprise tier | Surpassed CrewAI in stars; v1.1.3; DAGs + distributed runtime |
| **CrewAI** | Strong, mid-market | Added Flows (event-driven) + native A2A support |
| **AutoGen/AG2** | Maintenance mode | Microsoft shifted focus; no major features |
| **OpenAI Agents SDK** | Polished, OpenAI-only | Core handoff abstraction; low learning curve |
| **Google ADK** | Fast riser | GA in Python/Go/Java/TypeScript; v2 graph workflows; native A2A |
| **Claude Agent SDK** | Deepest MCP integration | Released with Claude 4.6 |
| **Smolagents** (HuggingFace) | Research community favorite | Lightweight, HF ecosystem |
| **OpenAgents** | Niche but notable | Only framework with native MCP + A2A |

MCP support is now nearly universal across frameworks. The A2A protocol (v0.2, March 2026 update) makes Google ADK the clear choice for cross-framework interoperability. OpenAgents uniquely supports both natively ([openagents.org](https://openagents.org/blog/posts/2026-02-23-open-source-ai-agent-frameworks-compared)).

Sources: [Best frameworks 2026 (gurusup)](https://gurusup.com/blog/best-multi-agent-frameworks-2026) | [Definitive guide (softmaxdata)](https://softmaxdata.com/blog/definitive-guide-to-agentic-frameworks-in-2026-langgraph-crewai-ag2-openai-and-more/) | [CrewAI vs LangGraph vs AutoGen (DEV)](https://dev.to/emperorakashi20/crewai-vs-langgraph-vs-autogen-which-multi-agent-framework-should-you-use-in-2026-5h2f) | [Claude vs OpenAI vs Google ADK (Composio)](https://composio.dev/content/claude-agents-sdk-vs-openai-agents-sdk-vs-google-adk) | [A2A Protocol](https://a2a-protocol.org/latest/) | [Google ADK 1.0 + A2A](https://explore.n1n.ai/blog/google-adk-1-0-a2a-protocol-multi-agent-standard-2026-05-04) | [OpenAI Agents SDK multi-agent](https://openai.github.io/openai-agents-python/multi_agent/) | [Google ADK A2A docs](https://google.github.io/adk-docs/a2a/) | [A2A GitHub](https://github.com/a2aproject/A2A) | [awesome-a2a](https://github.com/ai-boost/awesome-a2a) | [LangGraph A2A](https://github.com/mifune-dev/a2a-langgraph) | [LangGraph](https://www.langchain.com/langgraph) | [LangChain State of Agent Engineering](https://www.langchain.com/state-of-agent-engineering)

**Cross-platform resonance**: Web blogs, developer community, GitHub

---

### 6. Self-Improving Agents Arrive: Hermes Agent Hits 103K GitHub Stars

The biggest open-source agent story of the past 30 days is **Hermes Agent** by Nous Research, which reached 103,000 GitHub stars — up from zero on February 25, 2026, and past 95,600 at just 7 weeks post-launch.

Its core differentiator is **GEPA** (Genetic-Pareto), an ICLR 2026 Oral paper — not a scalar reward but a full execution trace reader (errors, profiling data, reasoning chains) that proposes targeted prompt improvements. Agents with 20+ self-generated skills run **40% faster** on repeated domain tasks.

- v0.10.0 (April 16, 2026): 118 built-in skills, three-layer memory, six messaging integrations
- MIT license; self-hosting starts at €5/month
- Competitor: OpenClaw
- Separate self-evolution repo: [hermes-agent-self-evolution](https://github.com/NousResearch/hermes-agent-self-evolution) (DSPy + GEPA)

Separately, Anthropic's "Dreaming" feature (unveiled at Code w/ Claude 2026) represents the enterprise path to the same concept — agents that learn from session inspection.

Sources: [Hermes Agent GitHub](https://github.com/nousresearch/hermes-agent) | [Hermes innobu review](https://www.innobu.com/en/articles/hermes-agent-self-improvement-open-source-2026.html) | [Token mix review/stars](https://tokenmix.ai/blog/hermes-agent-review-self-improving-open-source-2026) | [DEV.to: Is self-improving AI a real category?](https://dev.to/max_quimby/hermes-agent-is-self-improving-ai-a-real-category-56mj) | [Kingy AI explainer](https://kingy.ai/news/hermes-ai-agent-explained-self-improving-ai/) | [Hermes vs OpenClaw](https://www.contextstudios.ai/blog/hermes-agent-vs-openclaw-the-self-improving-ai-race) | [Benchmark guide](https://www.armalo.ai/blog/hermes-agent-benchmark-the-complete-guide) | [awesome-hermes-agent](https://github.com/0xNyk/awesome-hermes-agent) | [o-mega self-improving guide](https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide)

**Cross-platform resonance**: GitHub, developer blogs, AI news

---

### 7. Claude Code Developer Experience: Dominant but Expensive

Claude Code went from zero to the #1 agentic coding tool in 8 months. Community sentiment in April–May 2026:

**Positives:**
- **46%** "most loved" rating (Cursor 19%, GitHub Copilot 9%)
- **70%** of developers prefer Claude for coding tasks (citing multi-file handling, accurate refactoring, fewer hallucinated API calls)
- Enterprise case studies: Stripe (1,370 engineers; 10K-line Scala→Java migration in 4 days = ~10 engineer-weeks); Shopify and Mercado Libre (23K engineers) targeting **90% autonomous coding by Q3 2026**; Rakuten (99.9% numerical accuracy on vLLM in 7 hours); TELUS (500K+ hours saved); Zapier (800+ internal agents, 89% AI adoption)

**Negatives:**
- **Quality regression** in March–April 2026: Anthropic published an engineering postmortem April 23 tracing failures to three overlapping changes — lowered reasoning effort (March 4, reverted April 7), session-clearing bug (March 26, fixed April 10), verbosity-reduction system prompt (April 16, reverted April 20)
- **Code Review pricing** ($15–25/PR, 20-min reviews) generates concern from smaller teams
- Usage quota friction cited as top operational pain point even for satisfied users

**Agent-based Code Review** (research preview, Team/Enterprise):
- Multi-agent parallel PR analysis; agent count scales with PR size
- Before: 16% of PRs had substantive review comments → After: 54%
- Accuracy: <1% of findings marked incorrect by engineers
- Safety concern raised: Claude both writing and reviewing its own code

Sources: [InfoQ code review](https://www.infoq.com/news/2026/04/claude-code-review/) | [Eight trends (Anthropic)](https://claude.com/blog/eight-trends-defining-how-software-gets-built-in-2026) | [Medium: Claude Code changed everything](https://medium.com/@amaro.barros/claude-code-just-changed-everything-again-heres-what-developers-need-to-know-in-2026-776f4bc20c43) | [Medium: most popular agent](https://medium.com/lab7ai-insights/anthropics-claude-code-becomes-the-most-popular-coding-agent-of-2026-b838043be1f2) | [DEV: best agentic dev 2026](https://dev.to/chand1012/the-best-way-to-do-agentic-development-in-2026-14mn) | [Claude Code vs Cursor vs Copilot](https://dev.to/alexcloudstar/claude-code-vs-cursor-vs-github-copilot-the-2026-ai-coding-tool-showdown-53n4) | [OpenCode vs Claude Code](https://dev.to/tech_croc_f32fbb6ea8ed4/opencode-vs-claude-code-which-ai-cli-coding-agent-wins-in-2026-45md) | [Codex vs Claude Code (MindStudio)](https://www.mindstudio.ai/blog/codex-vs-claude-code-2026) | [AutoBE vs Claude Code review](https://dev.to/samchon/autobe-vs-claude-code-3rd-gen-coding-agent-developers-review-of-the-leaked-source-code-313b) | [Economics of quota (Medium)](https://medium.com/@william.couturier/claude-code-in-march-2026-the-economics-of-the-quota-792449b63edb) | [Claude reshaping coding skills (DEV)](https://dev.to/pooyagolchian/claude-and-the-new-developer-how-ai-is-reshaping-coding-skills-in-2026-3mdb) | [Claude Code 101 (DEV)](https://dev.to/rsicarelli/claude-code-101-introduction-to-agentic-programming-3p83) | [Dive into Claude Code (arXiv)](https://arxiv.org/html/2604.14228v1) | [VILA-Lab GitHub](https://github.com/VILA-Lab/Dive-into-Claude-Code) | [Anthropic product page](https://www.anthropic.com/product/claude-code) | [Agentic Coding Trends Report PDF](https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf) | [Claude changing how we build (Medium)](https://medium.com/techtrends-digest/claude-code-is-changing-how-we-build-software-in-2026-cba4a800297e) | [HN dev reactions analysis](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

**Cross-platform resonance**: HN, dev blogs, enterprise press, academic

---

### 8. Production Deployment: The 3:1 Scale Gap and What Actually Works

Less than 1 in 4 organizations have successfully scaled AI agents to production, despite 2 in 3 experimenting. LangChain's State of Agent Engineering survey (1,300+ professionals) found:
- **89%** have implemented observability for agents
- Only **52%** use evals — a dangerous gap
- Gartner: 40% of enterprise apps will have task-specific agents by end of 2026 (up from <5% in 2025)

**What's killing production agents:**
1. Tool call errors swallowed silently — add structured verification after each tool call
2. Poorly defined tool schemas → wrong tool selected → context bloat + redundant LLM calls
3. Infrastructure harness failures that only surface under real load
4. Missing HITL checkpoints — not optional for trustworthy systems

**Amazon's lessons** from internal agentic deployments: defined cross-org standards for tool schema and description formalization — uniform interface specs, parameter definitions, capability descriptions, usage constraints.

**The winning production pattern**: Reserve LLM strictly for reasoning and intent extraction → capture output as rigid JSON → hand to deterministic Python/SQL for execution.

Sources: [AWS/Amazon lessons](https://aws.amazon.com/blogs/machine-learning/evaluating-ai-agents-real-world-lessons-from-building-agentic-systems-at-amazon/) | [Harness Engineering lessons](https://harness-engineering.ai/blog/lessons-learned-from-deploying-ai-agents-in-production/) | [47billion production patterns](https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/) | [Computer Weekly: innovation theatre to production](https://www.computerweekly.com/feature/Moving-agentic-AI-from-innovation-theatre-to-enterprise-production) | [Google Cloud dev guide](https://cloud.google.com/blog/products/ai-machine-learning/a-devs-guide-to-production-ready-ai-agents) | [Hypertrends architecture patterns](https://www.hypertrends.com/2026/04/production-ai-agent-architecture-patterns/) | [CIO autonomous workforce 2026](https://www.cio.com/article/4064998/taming-ai-agents-the-autonomous-workforce-of-2026.html) | [NVIDIA/ServiceNow enterprise agents](https://blogs.nvidia.com/blog/servicenow-autonomous-ai-agents-enterprises/) | [Automation Atlas guide](https://automationatlas.io/guides/ai-agents-in-automation-2026/)

**Cross-platform resonance**: Enterprise press, cloud provider blogs, dev community

---

### 9. Security: Agentic Code Is Redefining the Attack Surface

AI coding agents autonomously executing code, calling external APIs, and submitting PRs are creating new supply chain and security concerns. Two notable pieces from the week of May 5:
- "AI Coding Agents Are Redefining Cyber Risk" ([Latest Hacking News, May 4](https://latesthackingnews.com/2026/05/04/ai-coding-agents-are-redefining-cyber-risk-is-your-exposure-strategy-ready/))
- "2026: The Year of AI-Assisted Attacks" ([The Hacker News, May 2026](https://thehackernews.com/2026/05/2026-year-of-ai-assisted-attacks.html))

InfoQ commenters specifically raised the concern of Claude writing *and* reviewing its own code in the Code Review feature — a circular validation problem. The Code with Claude 2026 conference added "Security Reviews" as a dedicated Claude Code capability, suggesting Anthropic is aware of the exposure.

---

## Cross-Source Patterns

### Pattern 1: MCP is becoming the universal integration layer for agents
- **Platforms**: HN (11 threads), GitHub (10+ repos), official announcements, developer blogs
- The MCP-to-Linux-Foundation donation accelerated adoption. Now every major framework (LangGraph, CrewAI, OpenAI SDK, Google ADK, Claude Agent SDK) supports it. HN community has moved from "what is MCP?" to operational questions ("how do I manage multiple MCP servers in Claude Code?").
- > "MCP provides agent-to-tool communication...A2A provides agent-to-agent communication and acts as the public internet that allows AI agents to interoperate." — A2A Protocol docs ([a2aproject.github.io](https://a2aproject.github.io/A2A/v0.2.5/))

### Pattern 2: Self-improvement is the hot new axis of competition
- **Platforms**: GitHub, developer blogs, HN
- Hermes Agent's 103K-star trajectory and Anthropic's "Dreaming" feature arrived in the same week. The definition of "self-improvement" varies: GEPA (Hermes) = prompt evolution via trace analysis; Dreaming (Anthropic) = session inspection for behavioral updates.
- > "Agents with 20 or more self-generated skills are 40 percent faster on repeated tasks in the same domain." — Hermes Agent GEPA benchmark ([tokenmix.ai](https://tokenmix.ai/blog/hermes-agent-review-self-improving-open-source-2026))

### Pattern 3: Production reality gap — most orgs can't ship agents at scale
- **Platforms**: Enterprise press, cloud blogs, developer community
- Consistent across AWS, Harness Engineering, Computer Weekly, and LangChain's survey: experimenting is easy, scaling is hard. The core fix is consistently the same: observability first, evals second, HITL always.
- > "The infrastructure wrapping the model — the harness — wasn't built to handle the edge cases that only appear under real load." — Harness Engineering ([harness-engineering.ai](https://harness-engineering.ai/blog/lessons-learned-from-deploying-ai-agents-in-production/))

### Pattern 4: Claude Code dominates developer love but generates pricing friction
- **Platforms**: Dev.to, Medium, HN, InfoQ, enterprise press
- 46% "most loved" and 70% coding preference, but the $15–25/PR code review and quota limits are the top complaints. The March–April quality regression (now postmortemed and fixed) generated significant community distrust that the May conference was partly designed to rebuild.
- > "Claude Code is objectively the most capable tool in its category, yet simultaneously the one whose usage constraints generate the most operational friction." — developer blog ([dev.to](https://dev.to/chand1012/the-best-way-to-do-agentic-development-in-2026-14mn))

### Pattern 5: The enterprise agent land-grab is accelerating
- **Platforms**: Financial press, official announcements, enterprise tech
- Anthropic's finance agents + Microsoft 365 integration + $1.5B JV are the most visible moves, but Shopify and Mercado Libre's "90% autonomous coding by Q3" target and Zapier's 800 internal agents signal that every major enterprise category now has an agent play.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| mahdiyar | Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex | 2 | several | "The final version was shocking" (user testing legal drafting) | https://news.ycombinator.com/item?id=45374908 |
| Shmungus | 24 Simultaneous Claude Code agents on local hardware | — | — | 683 tests, zero failures; beat Anthropic's own record of 16 | https://news.ycombinator.com/item?id=47099597 |
| (unknown) | Show HN: Agents Council – Connect Claude, Codex, and Local Agents via MCP | — | — | Inspired by Karpathy's "LLM Council" | https://news.ycombinator.com/item?id=46517090 |
| (unknown) | Show HN: Representing Agents as MCP Servers | — | — | Any MCP client can invoke agents as servers | https://news.ycombinator.com/item?id=44053754 |
| (unknown) | Show HN: Almanac MCP, turn Claude Code into a Deep Research agent | — | — | Proper web access for coding agents | https://news.ycombinator.com/item?id=47855284 |
| (unknown) | Show HN: MCP plugin that lets Claude autonomously pay for APIs via Lightning | — | — | Autonomous micropayment for API access | https://news.ycombinator.com/item?id=47669920 |
| (unknown) | Remote MCP Support in Claude Code | — | — | HTTP now recommended transport | https://news.ycombinator.com/item?id=44312363 |
| (unknown) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | — | — | https://news.ycombinator.com/item?id=43410866 |
| (unknown) | MCP Specification – version 2025-06-18 changes | — | — | — | https://news.ycombinator.com/item?id=44314289 |
| (unknown) | Ask HN: How do you manage multiple MCP servers in Claude Code? | — | — | Practitioner adoption signal | https://news.ycombinator.com/item?id=45114196 |
| (unknown) | Show HN: Agent Context – let your AI coding tools see your reference projects | — | — | Reference project context for coding agents | https://news.ycombinator.com/item?id=47919538 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Simon Willison (live blog) | https://simonwillison.net/2026/May/6/code-w-claude-2026/ | Complete Code w/ Claude 2026 conference coverage; Managed Agents, Dreams, Routines |
| Anthropic (MCP/AAIF) | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | MCP donation to Linux Foundation details |
| Anthropic (finance agents) | https://www.anthropic.com/news/finance-agents | 10 finance agent templates launch |
| Fortune | https://fortune.com/2026/05/05/anthropic-wall-street-financial-services-agents-jamie-dimon/ | Dimon+Amodei finance push; $1.5B JV |
| The Register | https://www.theregister.com/software/2026/05/05/anthropic-unleashes-finance-agents-for-claude/5225868 | Finance agents critical coverage |
| InfoQ | https://www.infoq.com/news/2026/04/claude-code-review/ | Claude Code agent-based code review details; $15-25/PR |
| MIT Technology Review | https://www.technologyreview.com/2026/04/21/1135654/agent-orchestration-ai-artificial-intelligence/ | "Coordination is the new scale frontier" |
| Anthropic (8 trends) | https://claude.com/blog/eight-trends-defining-how-software-gets-built-in-2026 | Enterprise case studies; 60% AI work adoption stat |
| Hermes Agent (GitHub) | https://github.com/nousresearch/hermes-agent | 103K+ star self-improving agent |
| Hermes Agent (innobu) | https://www.innobu.com/en/articles/hermes-agent-self-improvement-open-source-2026.html | GEPA details, self-improvement mechanics |
| tokenmix review | https://tokenmix.ai/blog/hermes-agent-review-self-improving-open-source-2026 | 95.6K stars milestone analysis |
| tokio-prompt-orchestrator | https://github.com/Mattbusel/tokio-prompt-orchestrator | 24-agent Rust orchestrator code |
| A2A Protocol (GitHub) | https://github.com/a2aproject/A2A | Agent2Agent open protocol |
| A2A Protocol (spec) | https://a2a-protocol.org/latest/ | Formal A2A specification |
| A2A samples | https://github.com/a2aproject/a2a-samples | A2A implementation examples |
| awesome-a2a | https://github.com/ai-boost/awesome-a2a | Curated A2A resource list |
| LangGraph A2A | https://github.com/mifune-dev/a2a-langgraph | A2A built on LangGraph |
| Google ADK A2A | https://google.github.io/adk-docs/a2a/ | Google ADK A2A documentation |
| Google ADK 1.0 blog | https://explore.n1n.ai/blog/google-adk-1-0-a2a-protocol-multi-agent-standard-2026-05-04 | ADK 1.0 GA + A2A context |
| AWS lessons | https://aws.amazon.com/blogs/machine-learning/evaluating-ai-agents-real-world-lessons-from-building-agentic-systems-at-amazon/ | Real-world Amazon agent learnings |
| Harness Engineering | https://harness-engineering.ai/blog/lessons-learned-from-deploying-ai-agents-in-production/ | Production failure root causes |
| 47billion | https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/ | What actually works in production |
| LangChain State of Agent Engineering | https://www.langchain.com/state-of-agent-engineering | Survey: 89% observability, 52% evals |
| Computer Weekly | https://www.computerweekly.com/feature/Moving-agentic-AI-from-innovation-theatre-to-enterprise-production | Innovation theatre to production |
| Google Cloud guide | https://cloud.google.com/blog/products/ai-machine-learning/a-devs-guide-to-production-ready-ai-agents | Production-ready AI agent guide |
| Gurusup frameworks | https://gurusup.com/blog/best-multi-agent-frameworks-2026 | Framework comparison 2026 |
| Softmaxdata definitive guide | https://softmaxdata.com/blog/definitive-guide-to-agentic-frameworks-in-2026-langgraph-crewai-ag2-openai-and-more/ | Definitive framework guide |
| DEV (CrewAI vs LangGraph) | https://dev.to/emperorakashi20/crewai-vs-langgraph-vs-autogen-which-multi-agent-framework-should-you-use-in-2026-5h2f | Framework decision guide |
| OpenAgents comparison | https://openagents.org/blog/posts/2026-02-23-open-source-ai-agent-frameworks-compared | Only MCP+A2A native framework |
| Composio SDK comparison | https://composio.dev/content/claude-agents-sdk-vs-openai-agents-sdk-vs-google-adk | Claude vs OpenAI vs Google ADK |
| Medium (Claude changed everything) | https://medium.com/@amaro.barros/claude-code-just-changed-everything-again-heres-what-developers-need-to-know-in-2026-776f4bc20c43 | Developer community sentiment |
| Medium (most popular coding agent) | https://medium.com/lab7ai-insights/anthropics-claude-code-becomes-the-most-popular-coding-agent-of-2026-b838043be1f2 | 46% most loved stat |
| DEV (best agentic dev) | https://dev.to/chand1012/the-best-way-to-do-agentic-development-in-2026-14mn | Workflow fit discussion |
| DEV (Claude Code vs Cursor vs Copilot) | https://dev.to/alexcloudstar/claude-code-vs-cursor-vs-github-copilot-the-2026-ai-coding-tool-showdown-53n4 | Tooling showdown |
| DEV (OpenCode vs Claude Code) | https://dev.to/tech_croc_f32fbb6ea8ed4/opencode-vs-claude-code-which-ai-cli-coding-agent-wins-in-2026-45md | CLI agent comparison |
| Codex vs Claude Code (MindStudio) | https://www.mindstudio.ai/blog/codex-vs-claude-code-2026 | Codex vs Claude comparison |
| arXiv (Dive into Claude Code) | https://arxiv.org/html/2604.14228v1 | Academic analysis of Claude Code design |
| VILA-Lab (GitHub) | https://github.com/VILA-Lab/Dive-into-Claude-Code | Systematic Claude Code analysis |
| Releasebot (Claude Code May) | https://releasebot.io/updates/anthropic/claude-code | May 2026 Claude Code changelog |
| Releasebot (Anthropic) | https://releasebot.io/updates/anthropic | Anthropic release history |
| GitHub MCP server | https://github.com/github/github-mcp-server | Official GitHub MCP server |
| GitHub remote MCP changelog | https://github.blog/changelog/2025-06-12-remote-github-mcp-server-is-now-available-in-public-preview/ | Remote MCP public preview |
| claude-code-mcp | https://github.com/steipete/claude-code-mcp | Agent inside agent via MCP |
| claude-context | https://github.com/zilliztech/claude-context | Full codebase context for coding agents |
| Vals AI Finance benchmark | https://www.vals.ai/benchmarks/finance_agent | Claude Opus 4.7 64.4% finance score |
| Claude Opus 4.7 stats | https://llm-stats.com/blog/research/claude-opus-4-7-launch | Model benchmarks |
| DEV (AutoBE vs Claude Code) | https://dev.to/samchon/autobe-vs-claude-code-3rd-gen-coding-agent-developers-review-of-the-leaked-source-code-313b | 3rd-gen coding agent review |
| Medium (economics of quota) | https://medium.com/@william.couturier/claude-code-in-march-2026-the-economics-of-the-quota-792449b63edb | Pricing/quota friction analysis |
| DEV (Claude and new developer) | https://dev.to/pooyagolchian/claude-and-the-new-developer-how-ai-is-reshaping-coding-skills-in-2026-3mdb | Developer skills reshaping |
| DEV (Claude Code 101) | https://dev.to/rsicarelli/claude-code-101-introduction-to-agentic-programming-3p83 | Intro to agentic programming |
| Medium (Claude changing software) | https://medium.com/techtrends-digest/claude-code-is-changing-how-we-build-software-in-2026-cba4a800297e | Community blog |
| HN developer reactions | https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 | HN sentiment analysis |
| Latest Hacking News | https://latesthackingnews.com/2026/05/04/ai-coding-agents-are-redefining-cyber-risk-is-your-exposure-strategy-ready/ | Security risk from coding agents |
| The Hacker News | https://thehackernews.com/2026/05/2026-year-of-ai-assisted-attacks.html | AI-assisted attack vectors |
| hermes-agent-self-evolution | https://github.com/NousResearch/hermes-agent-self-evolution | DSPy+GEPA self-improvement |
| awesome-hermes-agent | https://github.com/0xNyk/awesome-hermes-agent | Curated Hermes resources |
| o-mega self-improving guide | https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide | Self-improving agents guide |
| Hermes vs OpenClaw | https://www.contextstudios.ai/blog/hermes-agent-vs-openclaw-the-self-improving-ai-race | Competitive self-improving landscape |
| Hermes benchmark guide | https://www.armalo.ai/blog/hermes-agent-benchmark-the-complete-guide | Hermes benchmarks |
| Hermes AI.cc guide | https://www.ai.cc/blogs/hermes-agent-2026-self-improving-open-source-ai-agent-vs-openclaw-guide/ | Hermes agent explainer |
| Kingy AI Hermes | https://kingy.ai/news/hermes-ai-agent-explained-self-improving-ai/ | Self-improving AI explained |
| DEV (is self-improving AI real?) | https://dev.to/max_quimby/hermes-agent-is-self-improving-ai-a-real-category-56mj | Skeptical community take |
| MindStudio orchestration patterns | https://www.mindstudio.ai/blog/multi-agent-orchestration-patterns | 100% vs 1.7% actionable recs stat |
| OpenAI Agents SDK multi-agent | https://openai.github.io/openai-agents-python/multi_agent/ | Handoff pattern documentation |
| Codebridge orchestration guide | https://www.codebridge.tech/articles/mastering-multi-agent-orchestration-coordination-is-the-new-scale-frontier | Coordination as scale frontier |
| Multi-agent complete guide | https://letusassume.com/multi-agent-ai-orchestration/ | Complete orchestration guide |
| Medium (beginner deep dive) | https://medium.com/@vasanthancomrads/orchestrating-multi-agent-ai-systems-a-beginner-friendly-deep-dive-1486e5b51acc | Beginner orchestration guide |
| Kanerika enterprise orchestration | https://kanerika.com/blogs/ai-agent-orchestration/ | Enterprise orchestration patterns |
| Automation Atlas | https://automationatlas.io/guides/ai-agents-in-automation-2026/ | AI agents in automation |
| CIO autonomous workforce | https://www.cio.com/article/4064998/taming-ai-agents-the-autonomous-workforce-of-2026.html | Enterprise agent adoption |
| NVIDIA/ServiceNow | https://blogs.nvidia.com/blog/servicenow-autonomous-ai-agents-enterprises/ | Enterprise autonomous agents |
| Dun & Bradstreet MCP | https://www.prnewswire.com/news-releases/dun--bradstreet-brings-risk--compliance-workflows-to-anthropics-claude-302762851.html | D&B KYC workflows via MCP |
| Verisk MCP | https://www.verisk.com/company/newsroom/verisk-brings-its-trusted-analytics-and-generative-ai-capabilities-directly-into-anthropics-claude/ | Insurance analytics via MCP |
| Anthropic product (Claude Code) | https://www.anthropic.com/product/claude-code | Official Claude Code product page |
| Anthropic (Claude agents solutions) | https://claude.com/solutions/agents | Agent solutions page |
| Agentic Coding Trends Report | https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf | Anthropic's official trends report |
| Code with Claude conference info | https://pasqualepillitteri.it/en/news/1727/code-with-claude-2026-anthropic-developer-conference | Conference dates/locations |
| Claude Managed Agents docs | https://platform.claude.com/docs/en/managed-agents/overview | Managed Agents documentation |
| Dreams docs | https://platform.claude.com/docs/en/managed-agents/dreams | Dreams feature documentation |
| Agent SDK docs | https://code.claude.com/docs/en/agent-sdk/overview | Claude Agent SDK |
| Routines docs | https://code.claude.com/docs/en/routines | Routines documentation |
| MCP Claude Code docs | https://code.claude.com/docs/en/mcp | MCP integration docs |
| Juheapi financial services | https://www.juheapi.com/blog/anthropic-financial-services-agents | Finance agents overview |
| CrewAI open source | https://crewai.com/open-source | CrewAI open source project |
| OpenAgents blog | https://openagents.org/blog/posts/2026-02-23-open-source-ai-agent-frameworks-compared | OpenAgents framework blog |
| dasroot frameworks comparison | https://dasroot.net/posts/2026/04/llm-agent-frameworks-langchain-crewai-autogen-comparison/ | April 2026 framework comparison |
| Medium (10 AI agent frameworks) | https://medium.com/@atnoforgenai/10-ai-agent-frameworks-you-should-know-in-2026-langgraph-crewai-autogen-more-2e0be4055556 | Top frameworks overview |
| Turing AI frameworks | https://www.turing.com/resources/ai-agent-frameworks | Detailed framework comparison |
| Pratik Pathak frameworks | https://pratikpathak.com/langgraph-vs-crewai-vs-autogen-2026/ | LangGraph vs CrewAI vs AutoGen |
| Intuz top frameworks | https://www.intuz.com/blog/top-5-ai-agent-frameworks-2025 | Top 5 agent frameworks |
| DEV (CrewAI vs AutoGen vs LangGraph) | https://dev.to/agdex_ai/crewai-vs-autogen-vs-langgraph-which-multi-agent-framework-in-2026-51m6 | Framework decision |
| Hypertrends architecture | https://www.hypertrends.com/2026/04/production-ai-agent-architecture-patterns/ | Production architecture patterns |
| DeepClaude DEV | https://dev.to/onsen/deepclaude-claude-code-deepseek-v3-pro-agent-loop-26je | DeepClaude agent loop |
| Medium (10 must-have Claude skills) | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | Claude skills guide |
| Medium (AI agent dev guide) | https://medium.com/@contact.noukha/ai-agent-development-in-2026-use-cases-architecture-tools-and-deployment-guide-b7b45f23848d | Agent dev guide |
| Morphllm framework article | https://www.morphllm.com/ai-agent-framework | 8 SDKs comparison |
| Paperclipped tier list | https://www.paperclipped.de/en/blog/ai-agent-frameworks-tier-list-2026/ | Framework tier list |
| Chanl blog what ships | https://www.channel.tel/blog/ai-agent-frameworks-compared-2026-what-ships | Which frameworks ship |
| xpay technical comparison | https://www.xpay.sh/blog/article/top-ai-agent-frameworks/ | Technical builder comparison |
| AI makers landscape | https://www.aimakers.co/blog/ai-agents-landscape-2026/ | 2026 agent landscape |
| Turion complete guide | https://turion.ai/blog/complete-guide-ai-agent-frameworks-2026/ | Complete framework guide |
| Toolradar expert guide | https://toolradar.com/guides/best-ai-agent-frameworks | Expert agent frameworks guide |
| Google Developers agent bake-off | https://developers.googleblog.com/build-better-ai-agents-5-developer-tips-from-the-agent-bake-off/ | Google agent tips |
| Google Codelabs multi-agent | https://codelabs.developers.google.com/codelabs/production-ready-ai-roadshow/1-building-a-multi-agent-system/building-a-multi-agent-system | Google multi-agent codelab |
| ADK A2A discussion | https://github.com/google/adk-python/discussions/3743 | A2A user context propagation |
| openclaw A2A issue | https://github.com/openclaw/openclaw/issues/12401 | Native A2A support request |
| MightBot coding agents 2026 | https://mightybot.ai/blog/coding-ai-agents-for-accelerating-engineering-workflows/ | Best coding agents ranked |
| Hermes Beam AI | https://www.communicationsquare.com/news/autonomous-ai-agents-in-2026/ | Autonomous agents in 2026 |
| MachineLearningMastery 7 trends | https://machinelearningmastery.com/7-agentic-ai-trends-to-watch-in-2026/ | 7 agentic AI trends |
| HN Ask April 2026 | https://news.ycombinator.com/item?id=47600204 | What are you working on? (April 2026) |
| HN Ask Jan 2026 | https://news.ycombinator.com/item?id=46482268 | What are you working on? (Jan 2026) |
| claude-context (zilliztech) | https://github.com/zilliztech/claude-context | Code search MCP tool |
| ezyang codemcp | https://github.com/ezyang/codemcp | Coding assistant MCP for Claude Desktop |
| Composio GitHub+Claude Code | https://composio.dev/toolkits/github/framework/claude-code | GitHub MCP + Claude Code integration |
| GitHub MCP install guide | https://github.com/github/github-mcp-server/blob/main/docs/installation-guides/install-claude.md | Claude install guide for GitHub MCP |
| Gist: remote MCP guide | https://gist.github.com/juno/471a73f0abfe00779b87725fba8ba48b | Remote MCP setup guide |
| Resultsense finance agents | https://www.resultsense.com/news/2026-05-06-anthropic-finance-agent-templates/ | Finance agent templates summary |
| ts2.tech finance agents | https://ts2.tech/en/anthropic-launches-claude-ai-finance-agents-to-take-on-wall-streets-grunt-work/ | Finance agents launch coverage |
| StartupHub finance agents | https://www.startuphub.ai/ai-news/artificial-intelligence/2026/anthropic-unleashes-finance-ai-agents | Finance agents startup angle |
| AIbars library | https://www.aibars.net/en/library/ai-news/details/839792394223357952 | Finance agent templates detail |
| Cryptobriefing Anthropic | https://cryptobriefing.com/claude-finance-integration-microsoft-365/ | Claude + Microsoft 365 integration |
| LinkedIn Claude Code 4 course | https://www.linkedin.com/learning/claude-code-4-agentic-coding-for-professional-developers | Claude Code 4 learning course |
| Tech-insider ChatGPT vs Claude | https://tech-insider.org/claude-vs-chatgpt-2026/ | Claude vs ChatGPT 2026 comparison |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked
├─ 🔵 X: 0 posts │ excluded per instructions
├─ 🔴 YouTube: 0 videos │ no video-level data
├─ 🟢 HN: 11 stories │ varied points │ rate limits on 3 threads
├─ 🟣 TikTok: 0 videos │ no data
├─ 🩷 Instagram: 0 reels │ no data
├─ 🦋 Bluesky: 0 posts │ no platform-specific data
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 90+ pages
└─ 🗣️ Top voices: simonwillison.net, Dario Amodei (Anthropic), Jamie Dimon (JPMorgan), Shmungus (HN), Nous Research (Hermes), Boris Cherny (Anthropic), Ami Vora (Anthropic) │ n/a (subreddits blocked)
```

---

## Data Gaps

- **Reddit**: Completely inaccessible — domain blocked by the search agent. This is a significant gap; Reddit communities like r/ClaudeAI, r/LocalLLaMA, r/MachineLearning, and r/programming would contain substantial grassroots developer reactions.
- **X/Twitter**: Excluded per research instructions. X is a primary channel for real-time AI developer discourse.
- **YouTube**: General searches returned article URLs, not video-specific data (channel names, view counts, transcript content). Tutorial/demo content for LangGraph, CrewAI, Claude Code, and Hermes Agent is likely substantial but uncaptured.
- **TikTok/Instagram**: No relevant content returned. May exist in form of short-form AI explainer content but not indexed in web search.
- **Bluesky**: No platform-specific posts retrieved. Simon Willison and other noted AI commentators are active on Bluesky; direct API access would improve coverage.
- **Polymarket**: No active prediction markets found for agentic AI topics (agent adoption timelines, Claude vs GPT market share, etc.).
- **HN point/comment counts**: Rate limiting (HTTP 429) on 3 of 11 HN threads prevented full engagement data retrieval. Points and top comment text missing for Agents Council, MCP Lightning plugin, and Remote MCP Support threads.
- **Approximate coverage**: Web/news ~85% comprehensive; HN ~75%; GitHub ~60% (repos found but star/fork counts are estimates); Reddit 0%; X 0%; YouTube 0%. Overall topic coverage ~55–60%.

---

## Key Quotes

> "The model intelligence has got strong enough to support all of this." — Dianne Na Penn, Anthropic at Code w/ Claude 2026 ([simonwillison.net](https://simonwillison.net/2026/May/6/code-w-claude-2026/))

> "Routines are higher-order prompts." — Boris Cherny, Anthropic at Code w/ Claude 2026 ([simonwillison.net](https://simonwillison.net/2026/May/6/code-w-claude-2026/))

> "It created a huge dashboard...with all the backup, and all the research, and it was very accurate." — Jamie Dimon on Claude Code ([Fortune](https://fortune.com/2026/05/05/anthropic-wall-street-financial-services-agents-jamie-dimon/))

> "Agents with 20 or more self-generated skills are 40 percent faster on repeated tasks in the same domain." — Hermes Agent GEPA benchmark ([tokenmix.ai](https://tokenmix.ai/blog/hermes-agent-review-self-improving-open-source-2026))

> "The infrastructure wrapping the model — the harness — wasn't built to handle the edge cases that only appear under real load, with real users, on real tasks." — Harness Engineering ([harness-engineering.ai](https://harness-engineering.ai/blog/lessons-learned-from-deploying-ai-agents-in-production/))

> "Claude Code is objectively the most capable tool in its category, yet simultaneously the one whose usage constraints generate the most operational friction." — developer community ([dev.to](https://dev.to/chand1012/the-best-way-to-do-agentic-development-in-2026-14mn))

> "MCP provides agent-to-tool communication...A2A provides agent-to-agent communication and acts as the public internet that allows AI agents to interoperate." — A2A Protocol documentation ([a2aproject.github.io](https://a2aproject.github.io/A2A/v0.2.5/))

> "Shopify and Mercado Libre targeting 90% autonomous coding by Q3 2026." — Anthropic eight trends blog ([claude.com](https://claude.com/blog/eight-trends-defining-how-software-gets-built-in-2026))

> "Annualized growth of roughly 80x in one quarter." — Dario Amodei ([Fortune](https://fortune.com/2026/05/05/anthropic-wall-street-financial-services-agents-jamie-dimon/))

> "The final version was shocking [in catching overlooked flaws]." — HN user testing Roundtable MCP for legal document drafting ([news.ycombinator.com](https://news.ycombinator.com/item?id=45374908))
