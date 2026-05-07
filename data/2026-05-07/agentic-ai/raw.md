# Agentic AI — Raw Research Output
**Date:** 2026-05-07
**Topic:** AI agents, agentic coding, multi-agent orchestration, MCP protocol, Claude Code, Anthropic Claude updates and releases, agent frameworks (LangGraph, CrewAI, AutoGen, Agno), agent-to-agent communication, tool use patterns, self-improving agents, production agent deployments, developer experience, community reactions

---

## PLATFORM: Hacker News

### Story 1: "Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex"
- URL: https://news.ycombinator.com/item?id=45374908
- Points: 2
- Submitted: ~7 months ago (October 2025)
- Summary: Developer mahdiyar built Roundtable MCP, a system coordinating multiple AI coding assistants (Claude Code, Cursor, Gemini, Codex) through the Model Context Protocol. Zero config, runs agents in parallel via existing CLI tools.
- Architecture: IDE → MCP Server → Multiple AI CLIs with shared project context
- Install: `pip install roundtable-ai`
- Use cases: Parallel code review (Gemini handles React performance, Codex reviews code quality, Cursor checks accessibility, Claude examines business logic), sequential delegation, specialized debugging (reduces manual coordination from 20+ minutes to 2–5 minutes)
- Top comment: User tested on legal document drafting through multiple subagents: "The final version was shocking" in catching overlooked flaws.

### Story 2: "24 Simultaneous Claude Code Agents on Local Hardware"
- URL: https://news.ycombinator.com/item?id=47099597
- Submitted: February 21, 2026
- Author: Shmungus
- Summary: Running 24 concurrent Claude Code agents on consumer hardware, surpassing the previous record of 16 set by Anthropic's own engineering team.
- Infrastructure: Tokio-native LLM orchestration pipeline in Rust routing inference through local Mistral 7B model on an RTX 4070
- Coordination mechanism: Agents coordinate indirectly via governance documentation files (CLAUDE.md, AGENTS.md) specifying module ownership and testing requirements — asynchronous, reduces conflicts
- Performance: 683 tests with zero failures; test-to-production ratio of 1.53:1 enforced via pre-commit hooks; 9-stage deduplication pipeline with circuit breakers; sub-millisecond pipeline overhead (inference ~3.6 sec on Mistral 7B)
- Notable: The orchestration system was built using the same multi-agent workflow it enables — recursive, self-demonstrating.
- GitHub: https://github.com/Mattbusel/tokio-prompt-orchestrator

### Story 3: "Show HN: Agents Council – Connect Claude, Codex, and Local Agents via MCP"
- URL: https://news.ycombinator.com/item?id=46517090
- Summary: Lightweight MCP server inspired by Andrej Karpathy's "LLM Council" concept — lets different AI agents communicate with each other locally.
- Rate limited during fetch (HTTP 429)

### Story 4: "Show HN: Representing Agents as MCP Servers"
- URL: https://news.ycombinator.com/item?id=44053754
- Summary: Proposal/implementation showing how agents can be MCP servers themselves, allowing any MCP client to invoke, coordinate and orchestrate agents the same way it does with other MCP servers.

### Story 5: "Show HN: Almanac MCP, turn Claude Code into a Deep Research agent"
- URL: https://news.ycombinator.com/item?id=47855284
- Submitted: ~2 weeks before 2026-05-07 (approx. April 23, 2026)
- Summary: MCP tool installable into coding agents to provide proper web access and deep research capabilities.
- Rate limited during fetch (HTTP 429)

### Story 6: "Show HN: MCP plugin that lets Claude autonomously pay for APIs via Lightning"
- URL: https://news.ycombinator.com/item?id=47669920
- Summary: MCP plugin enabling Claude to autonomously pay for external API access via Lightning Network micropayments.

### Story 7: "Remote MCP Support in Claude Code"
- URL: https://news.ycombinator.com/item?id=44312363
- Summary: HN discussion of Anthropic adding remote MCP server support to Claude Code. HTTP servers now the recommended transport for cloud-based services.
- Rate limited during fetch (HTTP 429)

### Story 8: "Hacking Your Own AI Coding Assistant with Claude Pro and MCP"
- URL: https://news.ycombinator.com/item?id=43410866

### Story 9: "MCP Specification – version 2025-06-18 changes"
- URL: https://news.ycombinator.com/item?id=44314289
- Summary: HN thread discussing the June 2025 MCP spec revision.

### Story 10: "Ask HN: How do you manage multiple MCP servers in Claude Code?"
- URL: https://news.ycombinator.com/item?id=45114196
- Summary: Community discussion on managing multiple MCP servers in Claude Code workflows.

### Story 11: "Show HN: Agent Context – let your AI coding tools see your reference projects"
- URL: https://news.ycombinator.com/item?id=47919538
- Submitted: ~1 week before 2026-05-07 (approx. April 30, 2026)
- Summary: Tool for letting AI coding agents see reference projects for better context on new codebases.

---

## PLATFORM: GitHub (Notable Repositories)

### Hermes Agent (Nous Research)
- URL: https://github.com/nousresearch/hermes-agent
- Stars: 95,600+ at 7 weeks post-launch; 103,000+ as of May 2026
- First released: February 25, 2026
- Description: Open-source self-improving AI agent using GEPA (Genetic-Pareto) mechanism — ICLR 2026 Oral
- Self-improvement: Agents with 20+ self-generated skills are 40% faster on repeated tasks
- v0.10.0 (April 16, 2026): 118 skills, three-layer memory, six messaging integrations
- Self-evolution repo: https://github.com/NousResearch/hermes-agent-self-evolution (DSPy + GEPA)
- Awesome list: https://github.com/0xNyk/awesome-hermes-agent

### tokio-prompt-orchestrator
- URL: https://github.com/Mattbusel/tokio-prompt-orchestrator
- Description: Rust-based orchestrator for 24 simultaneous Claude Code agents

### A2A Protocol
- URL: https://github.com/a2aproject/A2A
- Description: Agent2Agent open protocol for cross-framework, cross-org agent communication
- Contributed by Google, hosted under Linux Foundation
- Samples: https://github.com/a2aproject/a2a-samples
- awesome-a2a: https://github.com/ai-boost/awesome-a2a
- LangGraph A2A integration: https://github.com/mifune-dev/a2a-langgraph

### GitHub MCP Server
- URL: https://github.com/github/github-mcp-server
- Description: GitHub's official MCP server; remote version in public preview since June 2025

### VILA-Lab / Dive-into-Claude-Code
- URL: https://github.com/VILA-Lab/Dive-into-Claude-Code
- Description: Systematic academic analysis of Claude Code's design for AI agent systems
- Paper: https://arxiv.org/html/2604.14228v1

### claude-code-mcp (steipete)
- URL: https://github.com/steipete/claude-code-mcp
- Description: Claude Code as a one-shot MCP server (agent inside an agent)

### claude-context (zilliztech)
- URL: https://github.com/zilliztech/claude-context
- Description: Code search MCP for Claude Code; makes entire codebase context for any coding agent

---

## PLATFORM: Web — Anthropic / Official Sources

### Code w/ Claude 2026 Conference (May 6, 2026)
- Live blog: https://simonwillison.net/2026/May/6/code-w-claude-2026/
- Conference page: https://pasqualepillitteri.it/en/news/1727/code-with-claude-2026-anthropic-developer-conference
- Locations: San Francisco (May 6), London (May 19), Tokyo (June 10)

Key announcements:
1. **Rate limits doubled**: Claude Code five-hour limit doubled for Pro, Max, Enterprise
2. **Claude Managed Agents** (3 new features):
   - Multi-agent orchestration for complex tasks
   - Outcomes: define success criteria per run
   - "Dreaming": self-improvement via session inspection (research preview)
3. **Claude Code enhancements**:
   - Code Review (20 min avg, 84% of PRs >1000 lines generate findings, $15–25/PR)
   - CI Auto-fix: automatic PR fixes
   - Security Reviews
   - Remote Agents: laptop control via phone
   - Desktop app: full-screen GUI + preview panels
4. **Advisor strategy**: Sonnet calls Opus as consultant → "frontier model quality at 5x lower cost"
5. **Routines**: async automations ("higher-order prompts" per Boris Cherny)
6. **Infrastructure**: Partnership with SpaceX/Colossus; API volume up 17x year-on-year
7. **Quotes**:
   - "Today is about how we are making our products work better for you." — Ami Vora
   - "The model intelligence has got strong enough to support all of this." — Dianne Na Penn
   - "Routines are higher-order prompts." — Boris Cherny

### MCP Donated to Linux Foundation / Agentic AI Foundation
- URL: https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation
- Announced: December 9, 2025
- AAIF (Agentic AI Foundation) co-founded by Anthropic, Block, OpenAI under Linux Foundation
- Supporters: Google, Microsoft, AWS, Cloudflare, Bloomberg
- MCP stats at time of donation: 10,000+ active public MCP servers; 97M+ monthly SDK downloads; integrated in ChatGPT, Cursor, Gemini, Microsoft Copilot, VS Code
- Joining AAIF: Block's goose, OpenAI's AGENTS.md as founding projects

### Finance Agents Launch (May 5, 2026)
- URL: https://www.anthropic.com/news/finance-agents
- Fortune article: https://fortune.com/2026/05/05/anthropic-wall-street-financial-services-agents-jamie-dimon/
- The Register: https://www.theregister.com/software/2026/05/05/anthropic-unleashes-finance-agents-for-claude/5225868
- 10 pre-built agent templates: pitchbooks, earnings analysis, credit memos, underwriting, KYC, month-end close, statement audits, insurance claims
- Claude Opus 4.7: 64.4% on Vals AI Finance Agent benchmark
- Partners: Moody's (full platform embedded in Claude), Verisk, Dun & Bradstreet, Experian, Zoom
- Microsoft 365 integration: Claude now in Excel, PowerPoint, Word, Outlook
- $1.5B joint venture with Blackstone, Hellman & Friedman, Goldman Sachs, Apollo, General Atlantic, GIC, Sequoia
- Jamie Dimon quote: "it created a huge dashboard...with all the backup, and all the research, and it was very accurate."
- Dario Amodei: Anthropic saw "annualized growth of roughly 80x in one quarter"

### Anthropic Eight Trends Blog
- URL: https://claude.com/blog/eight-trends-defining-how-software-gets-built-in-2026
- Key stats: 60% of developer work now involves AI; only 0–20% fully delegatable
- Case studies: Rakuten (99.9% numerical accuracy on vLLM, 7 hours), TELUS (13,000+ custom AI solutions, 30% faster shipping, 500,000+ hours saved), Zapier (89% AI adoption, 800+ internal agents)
- Core thesis: transformation requires "active collaboration" — engineers shift to architecture/strategy

### Claude Code Updates (May 2026)
- URL: https://releasebot.io/updates/anthropic/claude-code
- Adds Bedrock service tier selection; improves /resume PR search and MCP handling; expands OpenTelemetry logging
- Claude Code agent-based Code Review (research preview, Team/Enterprise only)
- InfoQ coverage: https://www.infoq.com/news/2026/04/claude-code-review/
  - Multi-agent parallel PR analysis; scales agent count to PR size
  - Before: 16% of PRs had substantive review comments → After: 54%
  - Accuracy: <1% of findings marked incorrect by engineers

### 2026 Agentic Coding Trends Report (Anthropic)
- URL: https://resources.anthropic.com/hubfs/2026%20Agentic%20Coding%20Trends%20Report.pdf

---

## PLATFORM: Web — Agent Frameworks

### Framework Landscape Overview
- Sources: https://gurusup.com/blog/best-multi-agent-frameworks-2026
         https://softmaxdata.com/blog/definitive-guide-to-agentic-frameworks-in-2026-langgraph-crewai-ag2-openai-and-more/
         https://dev.to/emperorakashi20/crewai-vs-langgraph-vs-autogen-which-multi-agent-framework-should-you-use-in-2026-5h2f
         https://composio.dev/content/claude-agents-sdk-vs-openai-agents-sdk-vs-google-adk
         https://openagents.org/blog/posts/2026-02-23-open-source-ai-agent-frameworks-compared
         https://dasroot.net/posts/2026/04/llm-agent-frameworks-langchain-crewai-autogen-comparison/
         https://medium.com/@atnoforgenai/10-ai-agent-frameworks-you-should-know-in-2026-langgraph-crewai-autogen-more-2e0be4055556
         https://www.turing.com/resources/ai-agent-frameworks
         https://pratikpathak.com/langgraph-vs-crewai-vs-autogen-2026/
         https://www.intuz.com/blog/top-5-ai-agent-frameworks-2025

**LangGraph**: Surpassed CrewAI in GitHub stars in early 2026. v1.1.3 with deep agent templates and distributed runtime support. v0.3.0 stable: stateful graph orchestration with DAGs, conditional branching, parallel execution, durable state management. Positioned to own production/enterprise tier.

**CrewAI**: Added Flows (event-driven pipeline mode, production-oriented). Added A2A support (Agent-to-Agent protocol). Open source. https://crewai.com/open-source

**AutoGen/AG2**: Effectively in maintenance mode. Microsoft shifted focus to broader Agent Framework. Major feature development stopped.

**OpenAI Agents SDK**: Released March 2025. Core abstraction: handoffs between agents. Clean, opinionated API. Supports only OpenAI models.

**Google ADK**: Released April 2026. GA across Python, Go, Java, TypeScript. v2.0 alpha has graph-based workflows. Native A2A protocol support (v0.2, March 2026 update). Best for cross-framework interoperability and multimodal. https://google.github.io/adk-docs/a2a/

**Anthropic Claude Agent SDK**: Released alongside Claude 4.6. Deepest MCP integration. https://code.claude.com/docs/en/agent-sdk/overview

**Smolagents** (HuggingFace): Positioned to dominate HuggingFace ecosystem and research community.

**OpenAgents**: Only framework with native support for both MCP and A2A. https://openagents.org/

**New entrants**: Pydantic (type-safe agent layer), Mastra, Agno

### A2A Protocol Details
- URL: https://a2aproject.github.io/A2A/v0.2.5/
- Official spec: https://a2a-protocol.org/latest/
- JSON-RPC 2.0 over HTTP(S); supports synchronous, streaming (SSE), async push notifications
- Complementarity with MCP: MCP = agent-to-tool; A2A = agent-to-agent
- Google ADK A2A guide: https://google.github.io/adk-docs/a2a/
- Google ADK 1.0 + A2A blog: https://explore.n1n.ai/blog/google-adk-1-0-a2a-protocol-multi-agent-standard-2026-05-04

---

## PLATFORM: Web — Self-Improving Agents

### Hermes Agent
- Main: https://www.innobu.com/en/articles/hermes-agent-self-improvement-open-source-2026.html
- Review/stars: https://tokenmix.ai/blog/hermes-agent-review-self-improving-open-source-2026
- AI.cc: https://www.ai.cc/blogs/hermes-agent-2026-self-improving-open-source-ai-agent-vs-openclaw-guide/
- DEV.to: https://dev.to/max_quimby/hermes-agent-is-self-improving-ai-a-real-category-56mj
- Kingy AI: https://kingy.ai/news/hermes-ai-agent-explained-self-improving-ai/
- Benchmark guide: https://www.armalo.ai/blog/hermes-agent-benchmark-the-complete-guide
- vs OpenClaw: https://www.contextstudios.ai/blog/hermes-agent-vs-openclaw-the-self-improving-ai-race

Key facts:
- Released: February 25, 2026 (by Nous Research)
- 95,600 GitHub stars at 7 weeks; 103,000+ by May 2026
- GEPA (Genetic-Pareto): ICLR 2026 Oral — reads complete execution traces (errors, profiling, reasoning) and proposes targeted prompt improvements
- 40% faster on repeated tasks (for agents with 20+ self-generated skills)
- v0.10.0 (April 16, 2026): 118 skills, 3-layer memory, 6 messaging integrations
- MIT license; self-hosting starts at €5/month on European infrastructure
- Competitor: OpenClaw

### o-mega self-improving agents guide
- URL: https://o-mega.ai/articles/self-improving-ai-agents-the-2026-guide

---

## PLATFORM: Web — Production Deployment Lessons

### Key Sources
- AWS/Amazon lessons: https://aws.amazon.com/blogs/machine-learning/evaluating-ai-agents-real-world-lessons-from-building-agentic-systems-at-amazon/
- Harness Engineering: https://harness-engineering.ai/blog/lessons-learned-from-deploying-ai-agents-in-production/
- 47billion blog: https://47billion.com/blog/ai-agents-in-production-frameworks-protocols-and-what-actually-works-in-2026/
- Computer Weekly: https://www.computerweekly.com/feature/Moving-agentic-AI-from-innovation-theatre-to-enterprise-production
- Hypertrends: https://www.hypertrends.com/2026/04/production-ai-agent-architecture-patterns/
- Google Cloud guide: https://cloud.google.com/blog/products/ai-machine-learning/a-devs-guide-to-production-ready-ai-agents
- LangChain State of Agent Engineering: https://www.langchain.com/state-of-agent-engineering
- Kanerika: https://kanerika.com/blogs/ai-agent-orchestration/
- MindStudio multi-agent patterns: https://www.mindstudio.ai/blog/multi-agent-orchestration-patterns
- Automation Atlas: https://automationatlas.io/guides/ai-agents-in-automation-2026/

Key findings:
- Only 1 in 4 orgs have scaled agents to production (vs. 2/3 experimenting)
- Gartner: 40% of enterprise apps will feature task-specific agents by end of 2026 (up from <5% in 2025)
- LangChain survey: 89% have implemented observability; only 52% use evals
- Common failure: tool call errors swallowed silently — add structured verification after each tool call
- Winning pattern: LLM for reasoning/intent, deterministic Python/SQL for execution ("let AI do the thinking, code do the doing")
- HITL (Human in the Loop) is a requirement for trustworthy production systems, not a limitation
- Amazon: defined cross-org standards for tool schema and description formalization
- Multi-agent incident response: 100% actionable recommendation rate (vs. 1.7% for single-agent)
- NVIDIA/ServiceNow autonomous agents for enterprises: https://blogs.nvidia.com/blog/servicenow-autonomous-ai-agents-enterprises/

---

## PLATFORM: Web — Developer Experience & Community Reactions

### Key Sources
- Simon Willison live blog: https://simonwillison.net/2026/May/6/code-w-claude-2026/
- DEV.to: Best agentic development: https://dev.to/chand1012/the-best-way-to-do-agentic-development-in-2026-14mn
- Medium: Claude Code changed everything: https://medium.com/@amaro.barros/claude-code-just-changed-everything-again-heres-what-developers-need-to-know-in-2026-776f4bc20c43
- Medium: Claude Code most popular: https://medium.com/lab7ai-insights/anthropics-claude-code-becomes-the-most-popular-coding-agent-of-2026-b838043be1f2
- DEV.to: OpenCode vs Claude Code: https://dev.to/tech_croc_f32fbb6ea8ed4/opencode-vs-claude-code-which-ai-cli-coding-agent-wins-in-2026-45md
- DEV.to: Claude Code vs Cursor vs Copilot: https://dev.to/alexcloudstar/claude-code-vs-cursor-vs-github-copilot-the-2026-ai-coding-tool-showdown-53n4
- Medium: AutoBE vs Claude Code dev review: https://dev.to/samchon/autobe-vs-claude-code-3rd-gen-coding-agent-developers-review-of-the-leaked-source-code-313b
- Medium: Economics of the quota (March 2026): https://medium.com/@william.couturier/claude-code-in-march-2026-the-economics-of-the-quota-792449b63edb
- Medium: Changing how we build software: https://medium.com/techtrends-digest/claude-code-is-changing-how-we-build-software-in-2026-cba4a800297e
- InfoQ Code Review: https://www.infoq.com/news/2026/04/claude-code-review/
- MindStudio Codex vs Claude Code: https://www.mindstudio.ai/blog/codex-vs-claude-code-2026
- DEV.to: Claude and the New Developer: https://dev.to/pooyagolchian/claude-and-the-new-developer-how-ai-is-reshaping-coding-skills-in-2026-3mdb
- DEV.to: Claude Code 101: https://dev.to/rsicarelli/claude-code-101-introduction-to-agentic-programming-3p83
- ArXiv paper: https://arxiv.org/html/2604.14228v1
- Developers Digest on HN reactions: https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- Hacking News on cyber risk from coding agents: https://latesthackingnews.com/2026/05/04/ai-coding-agents-are-redefining-cyber-risk-is-your-exposure-strategy-ready/

Key findings:
- 46% "most loved" dev tool rating for Claude Code (Cursor 19%, Copilot 9%)
- 70% of developers prefer Claude for coding tasks
- Claude Code went from 0 → #1 tool in 8 months
- Quality regression in March–April 2026: Anthropic postmortem (April 23) traced to 3 changes: lowered reasoning effort (March 4, reverted April 7), session-clearing bug (March 26, fixed April 10), verbosity-reduction system prompt (April 16, reverted April 20)
- Code Review pricing ($15–25/PR) concerns from smaller teams
- Stripe: 1,370 engineers, 10,000-line Scala-to-Java migration in 4 days (est. 10 engineer-weeks)
- Shopify and Mercado Libre (23,000 engineers) targeting 90% autonomous coding by Q3 2026
- Criticism: cost-performance concerns; usage quota friction

---

## PLATFORM: Web — Multi-Agent Orchestration

### Key Sources
- MIT Technology Review on agent orchestration: https://www.technologyreview.com/2026/04/21/1135654/agent-orchestration-ai-artificial-intelligence/
- CodeBridge guide: https://www.codebridge.tech/articles/mastering-multi-agent-orchestration-coordination-is-the-new-scale-frontier
- Multi-agent orchestration complete guide: https://letusassume.com/multi-agent-ai-orchestration/
- Medium orchestrating multi-agent systems: https://medium.com/@vasanthancomrads/orchestrating-multi-agent-ai-systems-a-beginner-friendly-deep-dive-1486e5b51acc
- AI Agent Orchestration for enterprises (Kanerika): https://kanerika.com/blogs/ai-agent-orchestration/
- MindStudio orchestration patterns: https://www.mindstudio.ai/blog/multi-agent-orchestration-patterns
- OpenAI Agents SDK multi-agent: https://openai.github.io/openai-agents-python/multi_agent/

Key findings:
- Multi-agent orchestration has moved past "peak of inflated expectations" into practical production reality
- MIT Tech Review (April 21, 2026): "coordination is the new scale frontier"
- Multi-agent incident response: 100% actionable recommendation rate vs. 1.7% for single-agent
- Manager agent + specialist subagents is dominant production pattern
- Claude Code's own multi-agent mode: launch and coordinate several coding agents concurrently

---

## PLATFORM: Web — Security Concerns

### Key Sources
- Latest Hacking News: https://latesthackingnews.com/2026/05/04/ai-coding-agents-are-redefining-cyber-risk-is-your-exposure-strategy-ready/
- The Hacker News (security): https://thehackernews.com/2026/05/2026-year-of-ai-assisted-attacks.html

Key findings:
- AI coding agents are redefining cyber risk — concern about supply chain, code review, and autonomous execution
- InfoQ commenters questioned safety of Claude both writing and reviewing its own code
- 2026 flagged as "Year of AI-Assisted Attacks" due to agent capabilities

---

## DATA NOTES

- Reddit: Not accessible (domain blocked by web agent)
- X/Twitter: Excluded per research instructions
- YouTube: No specific video-level data retrieved (general YouTube searches returned article results, not specific video URLs/view counts)
- TikTok: No data retrieved
- Instagram: No data retrieved
- Bluesky: No specific Bluesky posts retrieved (Bluesky-specific searches returned general web results)
- Polymarket: No AI agent prediction markets found in this search pass
- HN: Rate limiting on some threads (429 errors) — partial data on stories 3, 6, 7
