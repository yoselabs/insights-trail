# Agentic AI — Raw Research Data
**Date:** 2026-05-25
**Topic:** AI agents, agentic coding, multi-agent orchestration, MCP protocol, Claude Code, Anthropic Claude updates, agent frameworks (LangGraph, CrewAI, AutoGen), agent-to-agent communication, tool use patterns, self-improving agents, production deployments, developer experience

---

## HACKER NEWS

### Thread 1: Claude Managed Agents
- **URL:** https://news.ycombinator.com/item?id=47693047
- **Score:** 169 points
- **Comments:** 87
- **Key Themes:**
  - Vendor lock-in concerns: "locking in to a framework is a losing proposition for anyone trying to stay competitive"
  - "Framework is simply way too rigid for a non-deterministic technology"
  - Comparisons to AWS expanding strategy — Anthropic competing with SaaS instead of just being a model supplier
  - Self-hosted alternatives estimated at $6–10k/month vs enterprise platform pricing
  - "governance-of-output problem is wide open"
  - Multi-model flexibility preferred over single-provider lock-in

### Thread 2: What is agentic engineering?
- **URL:** https://news.ycombinator.com/item?id=47393908
- **Score:** 165 points
- **Comments:** 94
- **Key Themes:**
  - Simon Willison defines it as "the practice of developing software with the assistance of coding agents"
  - Distinction from "vibe coding": "the moment you start paying attention to the code it's not vibe coding anymore"
  - Critics: dropping "software" from "software engineer" reflects ego rather than meaningful distinction
  - Amazon coding incidents cited as evidence of real-world risks
  - Willison: "automated tests and linting and clear documentation and CI and CD and cleanly factored code" help agents produce better results

### Thread 3: Ask HN: What are the biggest limitations of agentic AI in real-world workflows?
- **URL:** https://news.ycombinator.com/item?id=47039354
- **Score:** Unknown (429 rate limit)
- **Key Themes (from search summary):**
  - Reliability over long action chains
  - Tool integration challenges
  - Cost unpredictability
  - State management failures
  - Latency and observability gaps

### Thread 4: Software factories and the agentic moment
- **URL:** https://news.ycombinator.com/item?id=46924426
- **Score:** 304 points
- **Comments:** 459
- **Key Themes:**
  - Claim of "$1,000 on tokens today per human engineer" sparked economic viability debates
  - "you can't 100% trust the LLM to infer your intent with accuracy"
  - Rust code quality concerns: anti-patterns including improper error handling, unnecessary cloning
  - Testing & Verification: debate on whether LLMs can reliably test their own outputs
  - Comparisons between $1,000/day token costs vs. hiring engineers in lower-cost regions

### Thread 5: Agentic Coding Recommendations
- **URL:** https://news.ycombinator.com/item?id=44255608
- **Score:** 296 points
- **Comments:** 203
- **Key Themes:**
  - Go recommended for agentic coding due to explicit context passing
  - Claude Code cited as superior but expensive ($20–200/month)
  - Aider discussed as cheaper alternative
  - "Simpler, more readable code demonstrably improves agent performance"
  - Well-documented codebases with AI-specific guidelines outperform minimal documentation
  - Multiple commenters report disappointing results despite following "best practices"

### Thread 6: Claude Code and the Great Productivity Panic of 2026
- **URL:** https://news.ycombinator.com/item?id=47467922
- **Score:** 46 points
- **Comments:** 16
- **Source:** Bloomberg
- **Key Themes:**
  - AI-assisted coding creates "thin, jittery, frayed sort of weariness" vs. satisfying deep work
  - Managing "6 or 7 agents" forces constant context-switching
  - "They made everyone more productive. But that also means everyone has to do more to keep up."
  - Quality vs. speed trade-off: structured workflows beat improvised agent prompts
  - Cloud software remains buggy despite developer acceleration

### Thread 7: Agentic Coding in real-world (various HN items)
- Beyond agentic coding: https://news.ycombinator.com/item?id=46930565 (429 rate limit)
- Agentic Frameworks in 2026: https://news.ycombinator.com/item?id=46509130 (429 rate limit)
- Coding is one topic but agentic AI is the big one: https://news.ycombinator.com/item?id=47519972 (429 rate limit)
- Orchestrate teams of Claude Code sessions: https://news.ycombinator.com/item?id=46902368
- Show HN: Almanac MCP, turn Claude Code into a Deep Research agent: https://news.ycombinator.com/item?id=47855284
- Show HN: Klaus – Claude Code native delegating agentic harness: https://news.ycombinator.com/item?id=46760506
- Agent Skills catalog: https://news.ycombinator.com/item?id=46692865
- Best Practices for Building Agentic AI Systems: https://news.ycombinator.com/item?id=44919647
- The current hype around autonomous agents: https://news.ycombinator.com/item?id=44623207
- Ask HN: Agentic coding workflows for complex features: https://news.ycombinator.com/item?id=45480764
- Anthropic blocks third-party use of Claude Code subscriptions: https://news.ycombinator.com/item?id=46549823
- Anthropic made a mistake in cutting off third-party clients: https://news.ycombinator.com/item?id=46586766
- Anthropic is protecting its huge asset (Claude Code value chain): https://news.ycombinator.com/item?id=46588899
- Anthropic says OpenClaw-style Claude CLI usage is allowed again: https://news.ycombinator.com/item?id=47844269
- How I use every Claude Code feature: https://news.ycombinator.com/item?id=45786738

---

## REDDIT

### r/ClaudeAI
1. **"I asked Claude to investigate its own token burn. The receipts go back six months."**
   - Score: +238
   - URL: https://reddit.com/r/ClaudeAI/comments/1t4gchn/
   - Key: Exposing hidden operational costs — cache rebuilds, resume penalties, orientation-loop waste

2. **"The creator of Claude Code notes on the current Caching Issue"**
   - Score: ~280
   - Date: April 13, 2026
   - Key: Creator-level transparency on caching problems causing session performance issues

3. **"Read through Anthropic's 2026 agentic coding report, a few numbers that stuck with me"**
   - Score: ~153
   - Date: April 16, 2026
   - Key: Multi-agent setups gaining practical attention; memory identified as live pain point

4. **"Let two Claude Code instances hand off tasks: encrypted, async, as a skill"**
   - Score: +1
   - URL: https://reddit.com/r/ClaudeAI/comments/1sub770/
   - Key: Agent-to-agent handoff with inbox model and async workflows

5. **"I built a directory of 5000+ Claude Code / AI agent skills"**
   - Score: +1
   - URL: https://reddit.com/r/ClaudeAI/comments/1sgds2v/
   - Key: Emergence of searchable skills discovery layer; market maturing toward reusable components

### r/AI_Agents
6. **"25+ agents built. Here's the uncomfortable truth nobody wants to post about."**
   - Score: +364
   - URL: https://reddit.com/r/AI_Agents/comments/1s1o0k6/
   - Key: Working agents favor simplicity: "email-to-CRM, FAQ support, resume parsing, moderation"

7. **"State of AI Agents in corporates in mid-2026?"**
   - Score: ~2
   - Date: May 2, 2026
   - URL: https://reddit.com/r/AI_Agents/comments/1t25omv/
   - Key: Enterprise deployments favor structured workflows with exception handling over full autonomy

8. **"Agentic AI Architecture in 2026 — What do you know about MCP, A2A and how enterprise systems are actually built?"**
   - Score: ~5
   - Date: April 30, 2026
   - Key: Shift from model comparison to MCP, A2A, LangGraph, observability, governance

9. **"At what point do AI agents become a governance problem?"**
   - Score: ~9
   - Date: April 15, 2026
   - Key: Governance discussions surpassing raw capability debates

10. **"Has anyone run an agent longer than a week? What broke first?"**
    - URL: https://reddit.com/r/AI_Agents/comments/1skur2q/
    - Key: Long-term autonomy failures center on "memory loss, cold boots, and poor sub-agent briefing"

### r/ClaudeCode
11. **"Output Tokens Are the Real Cost of Coding Agents"**
    - Score: ~18
    - Date: April 29, 2026
    - Key: Token overhead and caching efficiency now drive adoption decisions

12. **"Token 'Optimizers' for AI Coding Agents Are Silently Dangerous, And Nobody Is Talking About It"**
    - Score: ~11
    - Date: April 19, 2026
    - Key: Hidden risks in token optimization tools for coding agents

### r/LocalLLaMA
13. **"Your coding agent sessions are sitting on your machine right now. Big labs use this data internally."**
    - Score: +81
    - URL: https://reddit.com/r/LocalLLaMA/comments/1re6fud/
    - Key: Privacy and telemetry concerns about coding agent session data

14. **"Coding agents vs. manual coding"**
    - Score: +13
    - URL: https://reddit.com/r/LocalLLaMA/comments/1sat8a4/
    - Key: Comparative productivity analysis

### r/LLMStudio
15. **"Local AI for agentic coding is not easy as promoted by many - Here is my experience"**
    - Score: +14
    - URL: https://reddit.com/r/LLMStudio/comments/1t14sk6/
    - Key: Gap between local AI marketing claims and actual agentic coding experience

### r/buildinpublic
16. **"Built an AI agent marketplace to 12K+ active users in 2 months. $0 ad spend."**
    - Score: +27
    - Date: May 5, 2026
    - URL: https://reddit.com/r/buildinpublic/comments/1t49rww/
    - Key: Market shifting toward reusable workflow artifact distribution

### r/codex
17. **"Codex ships ~15k tokens of overhead per request. Claude Code ships 27k. Pi ships 2.6k."**
    - Score: ~25
    - Date: April 17, 2026
    - Key: "Harness tax" comparison across coding agent platforms; token efficiency becoming major differentiator

### r/developersIndia
18. **"Claude Code re-learns my project for 4 minutes. What's your actual fix?"**
    - Score: ~9
    - Date: May 6, 2026
    - Key: Context re-learning across sessions representing measurable productivity cost

---

## POLYMARKET

### Market: "Which company has the best AI model end of May?"
- **URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-may
- **Volume:** $10,891,166
- **Resolution:** May 31, 2026 at 12:00 PM ET
- **Resolution Criterion:** Chatbot Arena LLM Leaderboard "Text Arena | Overall" category
- **Odds:**
  - Anthropic: 98.4% ($0.984)
  - Google: <1% ($0.007)
  - OpenAI: <1% ($0.005)
  - ByteDance: <1%
  - Moonshot: <1%
  - Meta: <1%
  - xAI: <1%
  - Others (Alibaba, Z.ai, DeepSeek, Baidu, Amazon, Mistral, Meituan, Microsoft): <1%

### Additional Polymarket AI Markets
- https://polymarket.com/predictions/ai — 20+ live AI prediction markets
- https://polymarket.com/predictions/artificial-intelligence — 107+ AI markets
- https://polymarket.com/event/which-company-has-best-ai-model-end-of-june — June model competition

---

## WEB / BLOG SOURCES

### Anthropic Announcements

**Claude 4 Release (May 22, 2025)**
- URL: https://www.anthropic.com/news/claude-4
- Opus 4: 72.5% SWE-bench, world's best coding model at time of release
- Sonnet 4: 72.7% SWE-bench
- Claude Code GA with VS Code and JetBrains extensions, GitHub Actions integration

**Introducing Claude Opus 4.6 (February 2026)**
- URL: https://www.anthropic.com/news/claude-opus-4-6
- New agent teams capabilities
- TechCrunch coverage: https://techcrunch.com/2026/02/05/anthropic-releases-opus-4-6-with-new-agent-teams/

**Code with Claude 2026 Developer Event (May 6, 2026, San Francisco)**
- URL: https://www.infoq.com/news/2026/05/code-with-claude/
- Anthropic annualized revenue: $30 billion (80x growth trajectory)
- SpaceX partnership announced for compute
- Dario Amodei quote: "a one-person billion-dollar company would emerge in 2026"
- SWE-bench Verified improved to 87% with Opus 4.7
- 5 new features shipped: Dreaming, Outcomes, Multiagent Orchestration, Claude Finance (10 pre-built agents), Add-ins
- Agent View launched May 11, 2026 — CLI dashboard for parallel sessions
- GitHub CPO Mario Rodriguez: "Just 1% efficiency means millions overall" (cache hit rates above 94% as foundational)
- Partners: Vercel, GitHub, Datadog, Bun
- "Infrastructure, rather than intelligence, is now the bottleneck for production agents"
- TELUS teams using Claude Code: 30% faster, 500,000+ hours saved

**Claude Managed Agents — Dreaming, Outcomes, Multiagent Orchestration (May 7, 2026)**
- URL: https://9to5mac.com/2026/05/07/anthropic-updates-claude-managed-agents-with-three-new-features/
- VentureBeat: https://venturebeat.com/technology/anthropic-introduces-dreaming-a-system-that-lets-ai-agents-learn-from-their-own-mistakes
- The New Stack: https://thenewstack.io/anthropic-managed-agents-dreaming-outcomes/
- **Dreaming:** Reviews past sessions, extracts patterns, curates memories for self-improvement; stayed in research preview
- **Outcomes:** Grader agent evaluates output against user-defined criteria; public beta
- **Multiagent Orchestration:** Lead agent delegates to up to 20 specialists; public beta
- Real-world results:
  - Harvey (legal AI): task completion rates increased ~6x after implementing dreaming
  - Wisedocs (medical docs): document review time cut 50% using outcomes
  - Netflix: processing logs from hundreds of builds simultaneously using multi-agent orchestration

**Claude Managed Agents — Privacy/Security Features (May 19, 2026)**
- URL: https://9to5mac.com/2026/05/19/anthropic-enhances-claude-managed-agents-with-two-new-privacy-and-security-features/
- MCP tunnels: route services through private network
- Self-hosted sandboxes

**Multiagent Sessions Documentation**
- URL: https://platform.claude.com/docs/en/managed-agents/multi-agent

**Agent Teams Documentation**
- URL: https://code.claude.com/docs/en/agent-teams

**New in Claude Managed Agents: dreaming, outcomes, multiagent**
- URL: https://claude.com/blog/new-in-claude-managed-agents

### MCP (Model Context Protocol)

**2026 MCP Roadmap (Published March 9, 2026)**
- URL: https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/
- Four priority areas: Transport Evolution (stateless), Agent Communication (Tasks primitive), Governance Maturation (contributor ladder), Enterprise Readiness
- Moved to working group-based model
- `.well-known` metadata format for server discovery

**MCP Spec Release Candidate (Locked May 21, 2026)**
- URL: https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/
- Stateless protocol core, Extensions framework, Tasks, MCP Apps, authorization hardening
- Final spec publication: July 28, 2026
- Headline change: MCP stateless at protocol layer (six SEPs working together)

**MCP Growing Pains**
- URL: https://thenewstack.io/model-context-protocol-roadmap-2026/
- MCP is everywhere; existing APIs remain relevant for enterprise integration
- Official MCP servers: GitHub, GitLab, Google Drive, Slack, PostgreSQL, SQLite, Puppeteer, Brave Search, Filesystem, Fetch, Memory, Sentry, AWS KB Retrieval, Cloudflare

**MCP Overview**
- URL: https://decodethefuture.org/en/what-is-mcp-model-context-protocol/
- As of 2026, OpenAI, Google, Microsoft, Block, PwC adopt alongside Anthropic — de facto standard

### Google A2A Protocol

**A2A One-Year Milestone (April 9, 2026)**
- URL: https://www.linuxfoundation.org/press/a2a-protocol-surpasses-150-organizations-lands-in-major-cloud-platforms-and-sees-enterprise-production-use-in-first-year
- 150+ organizations supporting the standard
- Google, Microsoft, AWS, Salesforce, SAP, ServiceNow, Workday, IBM, Cisco, PayPal, LangChain, MongoDB, Cohere as supporters
- Donated to Linux Foundation June 23, 2025
- v1.2 (March 2026) = current stable release
- Protocol: HTTP with JSON-RPC 2.0

**A2A Guide**
- URL: https://rapidclaw.dev/blog/a2a-protocol-complete-guide-2026
- URL: https://stellagent.ai/insights/a2a-protocol-google-agent-to-agent
- URL: https://atlan.com/know/google-a2a-protocol/
- URL: https://www.programming-helper.com/tech/agent-to-agent-protocol-2026-google-a2a-standard

### Agent Frameworks

**Framework Comparisons 2026**
- Medium/ATNO: https://medium.com/@atnoforgenai/10-ai-agent-frameworks-you-should-know-in-2026-langgraph-crewai-autogen-more-2e0be4055556
- PEC Collective: https://pecollective.com/blog/ai-agent-frameworks-compared/
- QubitTool showdown: https://qubittool.com/blog/ai-agent-framework-comparison-2026
- Uvik: https://uvik.net/blog/python-ai-agent-frameworks/
- Alice Labs production ranking: https://alicelabs.ai/en/insights/best-ai-agent-frameworks-2026
- Apify pipeline focus: https://use-apify.com/blog/ai-agent-frameworks-2026-langgraph-autogen-crewai
- LumiChats guide: https://www.lumichats.com/blog/ai-agents-langgraph-autogen-crewai-complete-guide-2026
- Pharos production guide: https://pharosproduction.com/insights/engineering/ai-agent-frameworks-comparison-2026/
- Gurusup: https://gurusup.com/blog/best-multi-agent-frameworks-2026

**Key Framework Facts:**
- LangGraph surpassed CrewAI in GitHub stars (early 2026); enterprise tier leader
- Simple ReAct agent: 40 lines in Smolagents vs. 120 in LangGraph
- AutoGen: excels at offline, quality-sensitive workflows; expensive for high-volume real-time
- CrewAI: lowest learning curve; role-playing pattern immediately understandable
- 57% of organizations now have AI agents in production (up from 51%)
- Another 30% actively developing agents

### Self-Improving Agents

**HyperAgents (Meta, UBC, Oxford, NYU — March 19, 2026)**
- URL: https://venturebeat.com/orchestration/meta-researchers-introduce-hyperagents-to-unlock-self-improving-ai-for-non-coding-tasks
- imp@50 = 0.630 on Olympiad math grading
- Transfer of self-improvement strategies across domains

**ICLR 2026 Workshop on AI with Recursive Self-Improvement**
- URL: https://iclr.cc/virtual/2026/workshop/10000796

**Self-Evolving Agents**
- URL: https://evoailabs.medium.com/self-evolving-agents-open-source-projects-redefining-ai-in-2026-be2c60513e97
- EvoScientist: multi-agent AI scientist with persistent memory and self-evolution

**Task Length Doubling**
- URL: https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide
- Agent task length doubling every 7 months for six years; accelerated to every 4 months in 2024–25
- 50% reliability horizon: ~50 minutes for frontier models
- Frontier labs automating large fractions of research operations

### GitHub Trending

**Top Frameworks by GitHub Stars**
- URL: https://fungies.io/top-github-repositories-ai-agent-frameworks-2026/
- URL: https://blog.bytebytego.com/p/top-ai-github-repositories-in-2026
- OpenClaw: 9,000 → 210,000+ stars (breakout star 2026); self-hosted, writes own skills
- Langflow: 146k stars (visual builder)
- Dify: 136k stars (visual builder)
- Flowise: 51k stars (visual builder)
- Gartner: 40% of enterprise applications will feature task-specific AI agents by end of 2026 (up from <5% in 2025)
- Awesome AI Agents 2026: https://github.com/ARUNAGIRINATHAN-K/awesome-ai-agents-2026
- Awesome AI Agents (curated): https://github.com/caramaschiHG/awesome-ai-agents-2026

### Security

**Claude Code Sandbox Bypass (May 20, 2026)**
- URL: https://www.theregister.com/security/2026/05/20/even-claude-agrees-hole-in-its-sandbox-was-real-and-dangerous/5243662
- SOCKS5 hostname null-byte injection vulnerability
- Second silent fix in five months without CVE or security advisory
- "can send anything inside the sandbox - credentials, source code - to any server on the internet"

**Claude Code One-Click RCE (May 7, 2026)**
- URL: https://www.theregister.com/security/2026/05/07/claude-code-trust-prompt-can-trigger-one-click-rce/5235319

**Claude Code Flaws (February 2026)**
- URL: https://thehackernews.com/2026/02/claude-code-flaws-allow-remote-code.html
- Remote code execution and API key exfiltration vulnerabilities

**Claude Extension XSS (March 2026)**
- URL: https://thehackernews.com/2026/03/claude-extension-flaw-enabled-zero.html

**Claude Code Safety Rule Bypass**
- URL: https://www.theregister.com/2026/04/01/claude_code_rule_cap_raises/
- Hard cap of 50 security subcommands; bypassed by AI-generated 50+ subcommand pipelines from malicious CLAUDE.md

**Claude Code Source Leaked (April 2026)**
- URL: https://thehackernews.com/2026/04/claude-code-tleaked-via-npm-packaging.html

**Why Agentic AI Is Security's Next Blind Spot (May 2026)**
- URL: https://thehackernews.com/2026/05/why-agentic-ai-is-securitys-next-blind.html

### Developer Experience / Trends

**5 Key Trends Shaping Agentic Development in 2026 — The New Stack**
- URL: https://thenewstack.io/5-key-trends-shaping-agentic-development-in-2026/
- MCP management, parallel running, CLI vs. desktop tools, VS Code fork challenges
- IBM Bob: 80,000 developers, 45% productivity gains
- "AI won't speed up software delivery — nothing has"
- 40% of AI projects may be canceled by 2027 without proper connectivity platforms

**7 Agentic AI Trends to Watch in 2026 — MachineLearningMastery**
- URL: https://machinelearningmastery.com/7-agentic-ai-trends-to-watch-in-2026/
- Nearly two-thirds of organizations experimenting; fewer than 1 in 4 scaled to production

**Beyond the Vibes: A Rigorous Guide to AI Coding Assistants — Ted Shutes**
- URL: https://blog.tedivm.com/guides/2026/03/beyond-the-vibes-coding-assistants-and-agents/

**Agentic Coding Tools Q2 2026 — Digital Applied**
- URL: https://www.digitalapplied.com/blog/agentic-coding-tools-q2-2026-20-platform-matrix
- 20-platform matrix: async cloud agents, browser-first tools, terminal-first tools, enterprise solutions

**120+ Agentic AI Tools Landscape — StackOne**
- URL: https://www.stackone.com/blog/ai-agent-tools-landscape-2026/

**Firecrawl Top 11 Agentic AI Trends**
- URL: https://www.firecrawl.dev/blog/agentic-ai-trends
- TELUS: Claude Code shipped engineering code 30% faster, saved 500,000+ hours

**Claude Code Agent Teams 2026 Playbook — Developers Digest**
- URL: https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026

**What Hacker News Gets Right About AI Coding Agents — Developers Digest**
- URL: https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026

**Shipyard Multi-Agent Orchestration for Claude Code**
- URL: https://shipyard.build/blog/claude-code-multi-agent/

**MindStudio: 5 New Agent Features**
- URL: https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features

**Ruflo Ships Multi-Agent Orchestration — Augment Code**
- URL: https://www.augmentcode.com/blog/ruflo-claude-code-multi-agent-orchestration

**Agent View Guide — BuildFastWithAI**
- URL: https://www.buildfastwithai.com/blogs/claude-code-agent-view-guide

**Code with Claude: 5 Biggest Updates — Lenny's Newsletter**
- URL: https://www.lennysnewsletter.com/p/code-with-claude-the-5-biggest-updates

**InfoQ Code with Claude Coverage**
- URL: https://www.infoq.com/news/2026/05/code-with-claude/

**The Deep View: Multi-Agent Upgrade**
- URL: https://www.thedeepview.com/articles/anthropic-gives-claude-code-a-multi-agent-upgrade

**Claude Code Agent Teams — Developers Digest**
- URL: https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026

**Anthropic Release Notes May 2026 — Releasebot**
- URL: https://releasebot.io/updates/anthropic/claude
- URL: https://releasebot.io/updates/anthropic/claude-code

**DEV.to: AI Agents Have Entered Their Operations Era (Reddit roundup)**
- URL: https://dev.to/nance_craft_6cffbc0c3a042/ten-reddit-threads-showing-ai-agents-have-entered-their-operations-era-3gak

**DEV.to: What the AI-Agent Crowd on Reddit Is Arguing About in Early May 2026**
- URL: https://dev.to/liv_melendez_4be3c47ea998/what-the-ai-agent-crowd-on-reddit-is-arguing-about-in-early-may-2026-4j7e

**MCP Complete Developer Guide — DEV Community**
- URL: https://dev.to/monuminu/model-context-protocol-mcp-the-complete-developer-guide-to-building-production-grade-ai-agents-ah3

**AI Agents Rewriting Prediction Market Trading — CoinDesk**
- URL: https://www.coindesk.com/tech/2026/03/15/ai-agents-are-quietly-rewriting-prediction-market-trading

**Polymarket Toolkit for AI Agents**
- URL: https://www.blog.brightcoding.dev/2026/05/22/polymarket-toolkit-the-secret-weapon-top-ai-agents-use-for-prediction-market-alpha

---

## YOUTUBE

**Claude AI Full Tutorial: From Basics to Agentic AI (2026)**
- URL: https://www.youtube.com/watch?v=XTWb5oEfqdY

**Claude Code and the Evolution of Agentic Coding — Boris Cherny (AI Engineer World's Fair)**
- URL: https://www.classcentral.com/course/youtube-claude-code-the-evolution-of-agentic-coding-boris-cherny-anthropic-465473
- 18-minute conference talk by Claude Code creator

**DeepLearning.AI: Claude Code: A Highly Agentic Coding Assistant**
- URL: https://learn.deeplearning.ai/courses/claude-code-a-highly-agentic-coding-assistant/lesson/66b35/introduction

**Notable Channels:**
- Cole Medin (200K+ subscribers): AI agents, n8n workflows, LangGraph, end-to-end builds
- LangChain official: idiomatic patterns for retrieval, multi-step agents, LangGraph state-machine
- Mervin Praison: side-by-side comparison of CrewAI, AutoGen, LangGraph, OpenAI Agents SDK

---

## RESEARCH / ACADEMIC

**ICLR 2026 Workshop on AI with Recursive Self-Improvement**
- URL: https://openreview.net/pdf?id=OsPQ6zTQXV

**HyperAgents Paper (Meta/UBC/Oxford/NYU, March 19, 2026)**
- URL: https://venturebeat.com/orchestration/meta-researchers-introduce-hyperagents-to-unlock-self-improving-ai-for-non-coding-tasks

---

## KEY STATISTICS SUMMARY

- Anthropic annualized revenue: $30 billion (April 2026)
- SWE-bench Verified: 87% (Opus 4.7 at Code with Claude event)
- 57% of organizations have AI agents in production
- Gartner: 40% of enterprise apps will feature task-specific agents by end of 2026 (up from <5% in 2025)
- OpenClaw GitHub: 9,000 → 210,000+ stars
- A2A protocol: 150+ organizations
- MCP: stateless spec RC locked May 21, 2026
- Polymarket: $10.8M volume, Anthropic 98.4% odds for best AI model end of May
- AI agents in prediction markets: 30%+ of Polymarket wallets use AI agents
- Task length doubling rate: every 4 months (2024–25)
- Harvey (legal AI): 6x task completion improvement with Dreaming
- TELUS: 30% faster coding, 500K+ hours saved with Claude Code
- Nearly two-thirds of orgs experimenting; fewer than 1 in 4 scaled to production
