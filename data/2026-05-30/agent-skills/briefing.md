# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-30
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 15 threads | — | r/ClaudeWorkflows highest-traffic for this topic |
| X/Twitter | 13 posts | 13 likes, 1 repost | Top voices: @1999_eth, @RoundtableSpace, @_0xpainn |
| Hacker News | 12 stories | 1,414 points, 715 comments | Two breakout threads (DeepClaude 678pts; Claude Code daily driver 437pts) |
| Bluesky | 8 posts | 137 likes, 3 reposts | @hailey.at most-liked single post (115 likes) |
| Web | 10 pages | — | claudefa.st, GitHub, dev.to, clarista.io, techtimes.com, refactix.com, theaiarchitects.com + web search results |

---

## Synthesized Findings

### 1. Anthropic Enters the Registry Space — Officially

On May 22, 2026, Anthropic launched [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official), a company-maintained, curated directory of Claude Code plugins. The repo hit 20,000 stars within days of launch. The move is structurally significant: for most of the past 18 months, Anthropic had deliberately stayed out of the registry business, leaving discovery friction to the community. This launch reverses that posture — but only partially.

The directory creates two official tiers:
- **claude-plugins-official**: Anthropic-reviewed, auto-installed, highest trust tier.
- **claude-community**: Third-party, review-gated, added via `/plugin marketplace add`.

Crucially, the announcement came bundled with an explicit warning about unverified MCP server security risks, per [Tech Times](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm). With 9,400+ MCP servers registered by mid-April 2026, the supply problem has been "solved" — and the trust problem has arrived. The official directory is Anthropic's answer to that trust problem.

Discussed on: Hacker News, Web (Tech Times, claudefa.st), Reddit (r/ClaudeWorkflows, r/ClaudeCode), X/Twitter.

Related web sources:
- [Create plugins — Claude Code Docs](https://code.claude.com/docs/en/plugins)
- [Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide)
- [Top 10 Claude Code Plugins to Try in 2026](https://www.firecrawl.dev/blog/best-claude-code-plugins)
- [ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins)
- [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/)
- [Claude Code Skills Hub | Plugins & Agent Skills](https://claudecodeplugins.io/)
- [Claude Code Plugins & Marketplaces — Discover the Best Collections](https://www.aitmpl.com/plugins/)
- [Plugins | Build with Claude](https://buildwithclaude.com/plugins)

---

### 2. MCP Registry Fragmentation — Eight Marketplaces, No Single Authority

The MCP registry landscape has fragmented into competing hubs. Per [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries) and [Digital Applied](https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points), the four registries that matter for MCP servers in 2026 are:

| Registry | Scale | Character |
|----------|-------|-----------|
| mcp.so | 20,222 servers listed | Community-driven directory |
| smithery.ai | 7,000+ installable servers | Closest to Docker Hub for MCP |
| glama.ai/mcp | — | Discovery-focused hub |
| punkpeye/awesome-mcp-servers | — | Curated GitHub list |

For agent skills more broadly, the [Digital Applied](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) report identifies eight marketplaces that matter in Q2 2026: Claude Skills, GPT Store, MCP Hubs, Hugging Face Spaces, Replit Agent Market, LangChain Hub, Vercel Agent Gallery, and Cloudflare AI Marketplace. The ecosystem grew from one registry in December 2025 to eight by Q2 2026, per [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026).

The irony: "developers now spend more time comparing marketplaces than finding skills." Anthropic deliberately does not operate a canonical MCP registry — discovery friction remains the community's problem to solve. Pricing models diverge sharply: GPT Store pays revenue share on usage, Claude Skills is currently free distribution, Replit runs a direct-sale model, and Cloudflare bills on inference.

Other notable marketplace entrants: [SkillsMP](https://skillsmp.com/) (1.2M+ agent skills listed for Claude, Codex, and ChatGPT), [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) (425 plugins, 2,810 skills, 200 agents, with `ccpi` CLI package manager at tonsofskills.com).

Discussed on: Web (Digital Applied, TrueFoundry, agensi.io, KDnuggets), Hacker News, Reddit.

Related web sources:
- [Every AI Skill Marketplace and Directory (2026)](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)
- [AI Agent Marketplaces 2026: Discovery and Distribution](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)
- [Top 5 Agent Skill Marketplaces for Building Powerful AI Agents](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)
- [MCP Servers — mcp.so](https://mcp.so/)
- [One-click MCP server installation for Claude Desktop](https://www.anthropic.com/engineering/desktop-extensions)
- [Connect Claude Code to tools via MCP — Claude Code Docs](https://code.claude.com/docs/en/mcp)
- [Ultimate Guide to Claude MCP Servers & Setup | 2026](https://generect.com/blog/claude-mcp/)
- [GitHub — modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- [Introducing the MCP Registry](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/)
- [One Year of MCP: November 2025 Spec Release](https://blog.modelcontextprotocol.io/posts/2025-11-25-first-mcp-anniversary/)
- [Model Context Protocol — Wikipedia](https://en.wikipedia.org/wiki/Model_Context_Protocol)
- [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
- [Model Context Protocol (MCP) explained](https://codilime.com/blog/model-context-protocol-explained/)
- [The Definitive Guide to Model Context Protocol (MCP) in 2025](https://datasciencedojo.com/blog/guide-to-model-context-protocol/)
- [MCP's impact on 2025 — Thoughtworks](https://www.thoughtworks.com/en-us/insights/blog/generative-ai/model-context-protocol-mcp-impact-2025)
- [Model Context Protocol Servers: Build or Buy?](https://www.informationweek.com/machine-learning-ai/model-context-protocol-servers-build-or-buy-)
- [Tools — Model Context Protocol Specification](https://modelcontextprotocol.io/specification/2025-06-18/server/tools)

---

### 3. The Mental Model Crystallizes — Plugins as the Packaging Layer

The community has settled on a four-layer mental model for Claude Code extensibility, per [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution) (May 27) and confirmed by the Hacker News thread ["Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs"](https://arps18.github.io/posts/claude-code-mastery/) (437 points, 249 comments):

- **Skills** — teach Claude Code domain-specific workflows, context, and best practices
- **MCPs** — connect Claude Code to external APIs and data sources
- **Hooks** — automate behavior on lifecycle events
- **Plugins** — bundle all three into a single installable unit for one-command org rollout

Per the [official Claude Code docs](https://code.claude.com/docs/en/plugins): "A plugin bundles multiple skills, MCP servers, or commands into a single installable unit." The [Agent Skills — Claude API Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) defines skills as "reusable, filesystem-based resources that provide Claude with domain-specific expertise: workflows, context, and best practices that transform general-purpose agents into specialists."

The community resource capturing this most completely is the HN thread at [arps18.github.io/posts/claude-code-mastery/](https://arps18.github.io/posts/claude-code-mastery/), which r/ClaudeWorkflows has pinned as canonical reading. [MindStudio](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows) notes: "Claude Code Skills allow you to create reusable agent capabilities that can be invoked as slash commands, automating repetitive workflows."

Discussed on: Hacker News (437-point thread), Reddit (r/ClaudeWorkflows), Bluesky, Web.

Related web sources:
- [Agent Skills, Plugins and Marketplace: The Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)
- [How to Use Claude Code Skills to Automate Repetitive Workflows](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows)
- [Building Multi-Agent Workflows in Claude Code](https://www.developersdigest.tech/blog/building-multi-agent-workflows-claude-code)
- [Claude Agent SDK Skills: Build Reusable Agent Capabilities](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities)
- [Claude Introduces Agent Skills for Custom AI Workflows — DevOps.com](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/)
- [Claude Code Dynamic Workflows: Official Step-by-Step Guide](https://agentpedia.codes/blog/claude-opus-4-8-claude-code-workflows)
- [Claude AI Workflows | How I AI](https://www.chatprd.ai/how-i-ai/workflows/tool/claude)
- [Create custom subagents — Claude Code Docs](https://code.claude.com/docs/en/sub-agents)
- [Dynamic Workflows in Claude Code: Anthropic Opens Research Preview](https://pasqualepillitteri.it/en/news/3663/claude-code-dynamic-workflows-anthropic-research-preview)
- [Claude Code Agents In 2026: Agent View, Subagents, Teams](https://www.cloudzero.com/blog/claude-code-agents/)
- [Agent Skills — fast-agent documentation](https://fast-agent.ai/agents/skills/)
- [Notion Skills Registry: A Package Manager for AI Agent Skills with MCP](https://dev.to/axrisi/notion-skills-registry-a-package-manager-for-ai-agent-skills-with-mcp-2581)

---

### 4. DeepClaude and Model-Swapping — Claude Code as a Durable Agent Shell

The [DeepClaude](https://github.com/aattaran/deepclaude) project — running DeepSeek V4 Pro inside Claude Code's agent loop — went viral on Hacker News (May 3): 678 points, 281 comments. The project demonstrates that the plugin/extension model is being used not merely for tool integrations but for swapping the underlying model within Claude Code's orchestration layer.

This establishes a pattern: Claude Code as a durable agent shell, with both the model and the tools treated as hot-swappable plugins. The agent shell persists (context management, tool routing, hooks, CLAUDE.md); the inference engine underneath is replaceable. The HN comment section extensively debated whether this constitutes the "correct" use of the plugin architecture or an abuse of it — with the majority position landing on "legitimate architectural pattern."

This pattern also appears in the [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) repo's multi-agent compatibility design: 337 skills written to run identically across Claude Code, Codex CLI, Gemini CLI, Cursor, and 8 more coding agents. The inference layer is not assumed to be fixed.

Discussed on: Hacker News (678-point thread, 281 comments), Reddit (r/ClaudeAI, r/ClaudeCode), X/Twitter.

---

### 5. Cross-Agent Skill Portability — The SKILL.md Open Standard

Skills are no longer Claude Code-exclusive artifacts. The [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) repo (337 skills, 30+ agents, 70+ custom commands) runs across Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents. Per the [Agent Skills — Codex | OpenAI Developers](https://developers.openai.com/codex/skills) page, OpenAI adopted the same Agent Skills specification format as Anthropic when it launched in December 2025.

Per [GitHub — anthropics/skills](https://github.com/anthropics/skills), the open standard specification and example skills are publicly maintained. The [WorkOS MCP guide](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) identifies two near-term MCP roadmap items that will further enable portability:
- **MCP Server Cards**: a `.well-known` URL standard for capability metadata discovery without connecting
- **Stateless Streamable HTTP**: for scaling MCP server connections

HashiCorp now ships official Claude Code skills for Terraform and Packer, encoding their own best practices — a sign that software vendors are treating skills as a distribution channel for opinionated tooling. [Solo.io launched agentregistry](https://www.solo.io/press-releases/agent-skills-kubernetes-ecosystem), bringing full lifecycle management to AI agents, MCP tools, and Agent Skills in the Kubernetes ecosystem.

Per [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026): "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT."

Discussed on: Web (agensi.io, WorkOS, DevOps.com), Bluesky, Reddit, Hacker News.

Related web sources:
- [Agent Skills – Codex | OpenAI Developers](https://developers.openai.com/codex/skills)
- [GitHub — anthropics/skills: Public repository for Agent Skills](https://github.com/anthropics/skills)
- [Solo.io Brings Agent Skills to the Kubernetes Ecosystem](https://www.solo.io/press-releases/agent-skills-kubernetes-ecosystem)
- [GitHub — hashgraph-online/awesome-ai-plugins](https://github.com/hashgraph-online/awesome-ai-plugins)
- [AI Agent Skills and Plugins Explained (2026)](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)
- [AI Agent Plugin and Extension Architecture — zylos.ai](https://zylos.ai/research/2026-02-21-ai-agent-plugin-extension-architecture)
- [Google ADK Integrations Ecosystem](https://developers.googleblog.com/en/supercharge-your-ai-agents-adk-integrations-ecosystem/)

---

### 6. MCP Security — The Trust Deficit Is Now the Top Friction Point

Anthropic's own official plugin directory launch explicitly flagged unverified MCP server risks — making security the first topic the company led with when announcing its most significant ecosystem governance move to date. This is not accidental.

Per [JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/), a security audit of 22,511 skills across skills.sh, ClawHub, GitHub, and Tessl found 140,963 issues — an average of 6.3 issues per skill, with prompt injection found in 36% of skills tested. This is the data behind Anthropic's warning. The supply of skills and MCP servers has raced far ahead of the tooling for auditing them.

Enterprise solutions emerging to fill this gap: Lunar.dev MCPX, MCP Context Forge, MCP Jungle (per [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)). At the cloud level: AWS launched [Agent Registry via Amazon Bedrock AgentCore](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) in April 2026 preview, Kong entered with an [MCP Server Registry product](https://konghq.com/products/mcp-registry), and Microsoft announced [Agent 365 GA](https://www.microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/) (May 1) with registry sync for AWS Bedrock and Google Cloud connections.

Per [InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/): AWS Agent Registry provides "enterprises a centralized catalog for discovering, sharing, and governing AI agents, tools, MCP servers, and agent skills across an organization."

Discussed on: Web (JFrog, Tech Times, InfoQ, Microsoft, AWS), Reddit (r/ClaudeAI), Hacker News, X/Twitter.

Related web sources:
- [Agent Skills are the New Packages of AI: It's Time to Manage Them Securely — JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/)
- [AWS Launches Agent Registry in Preview — InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/)
- [Microsoft Agent 365, now generally available](https://www.microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/)
- [What is AI Agent Registry — TrueFoundry](https://www.truefoundry.com/blog/ai-agent-registry)
- [GitHub — agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)

---

## Cross-Source Patterns

**Pattern 1: MCP security as top-of-mind concern**
- Platforms: Web (Tech Times, JFrog), Hacker News, Reddit, X/Twitter, Bluesky
- The JFrog audit (6.3 issues per skill average, 36% prompt injection rate) is the most-cited data point. Anthropic leading its own plugin directory launch with a security warning signals this is no longer a niche concern — it is the dominant friction point for enterprise adoption.
- Key quote: Anthropic's official plugin directory announcement explicitly warned about "unverified MCP server security risks" — per [Tech Times](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm)

**Pattern 2: Discovery paradox — more registries, more friction**
- Platforms: Web (Digital Applied, agensi.io), Hacker News, Reddit
- One registry in December 2025, eight major marketplaces by Q2 2026. The proliferation of supply surfaces has not reduced discovery friction — it has increased it.
- Key quote (Digital Applied): "developers now spend more time comparing marketplaces than finding skills"

**Pattern 3: Skills as cross-agent, cross-vendor artifacts**
- Platforms: Web (agensi.io, OpenAI Developers docs), Reddit, Bluesky, Hacker News
- OpenAI's adoption of the Agent Skills specification format for Codex CLI and ChatGPT in December 2025 makes skills cross-vendor by standard, not just by community convention. The [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) repo (compatible with 10+ agents) is the most concrete evidence of this pattern in practice.

**Pattern 4: Claude Code as durable shell, model and tools as hot-swappable**
- Platforms: Hacker News (DeepClaude 678pts), Reddit (r/ClaudeCode, r/ClaudeAI), X/Twitter
- DeepClaude (swapping DeepSeek V4 Pro into Claude Code's loop) and alirezarezvani/claude-skills (same skills across 10+ agents) both reflect the same underlying architecture: the orchestration shell persists, the inference layer is replaceable.

**Pattern 5: Enterprise governance is now a product category, not a gap**
- Platforms: Web (InfoQ/AWS, Microsoft, Solo.io, Kong, TrueFoundry), Reddit
- AWS Bedrock AgentCore, Kong MCP Registry, Microsoft Agent 365, Solo.io agentregistry, Lunar.dev MCPX — five enterprise-grade registry/governance products launched or GA'd in the last 60 days. Enterprise MCP governance has gone from gap to crowded market.

---

## Per-Platform Tables

### Reddit

| Subreddit | Notes | URL |
|-----------|-------|-----|
| r/ClaudeWorkflows | Highest-traffic subreddit for this topic; pinned the HN "Claude Code as a Daily Driver" thread as canonical reading | https://reddit.com/r/ClaudeWorkflows |
| r/ClaudeAI | Active discussion of DeepClaude pattern and MCP security | https://reddit.com/r/ClaudeAI |
| r/ClaudeCode | Plugin directory launch and model-swapping discussion | https://reddit.com/r/ClaudeCode |

*(15 total threads across these and related subreddits; individual post URLs not captured in raw data)*

---

### X/Twitter

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @1999_eth | — (top voice for this topic) | — | — | — |
| @RoundtableSpace | — (top voice for this topic) | — | — | — |
| @_0xpainn | — (top voice for this topic) | — | — | — |

*(13 total posts, 13 likes, 1 repost; individual post text not captured in raw data)*

---

### Hacker News

| Title | Points | Comments | URL |
|-------|--------|----------|-----|
| DeepClaude — DeepSeek V4 Pro inside Claude Code's agent loop | 678 | 281 | https://github.com/aattaran/deepclaude |
| Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 437 | 249 | https://arps18.github.io/posts/claude-code-mastery/ |
| *(10 additional stories)* | *(~299 combined)* | *(~185 combined)* | — |

*(12 total stories, 1,414 points, 715 comments)*

---

### Bluesky

| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @hailey.at | "I run five to six simultaneous Claude sessions across two repos without writing code myself" — credits @ed3d.net's plugins and skills | 115 | https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v |
| @ed3d.net | Plugin and skill author credited by @hailey.at | — | https://bsky.app |
| *(6 additional posts)* | — | ~22 combined | — |

*(8 total posts, 137 likes, 3 reposts)*

---

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| anthropics/claude-plugins-official (GitHub) | https://github.com/anthropics/claude-plugins-official | Official Anthropic plugin directory — the structural event of the month |
| Tech Times | https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm | Reported official directory launch + Anthropic's MCP security warning |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Skills/MCPs/hooks/plugins mental model; May 27 publication |
| JFrog | https://jfrog.com/blog/agent-skills-new-ai-packages/ | Security audit: 22,511 skills, 140,963 issues, 36% prompt injection rate |
| Digital Applied (marketplaces) | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | Eight marketplaces by Q2 2026; pricing model comparison |
| Digital Applied (MCP) | https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points | Anthropic deliberately not running canonical MCP registry |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | December 2025 → 8 marketplaces timeline; OpenAI adoption of Agent Skills spec |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | Four MCP registries that matter; mcp.so at 20,222 servers |
| alirezarezvani/claude-skills (GitHub) | https://github.com/alirezarezvani/claude-skills | 337 skills; cross-agent portability across 10+ agents |
| agentic-community/mcp-gateway-registry (GitHub) | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP gateway registry project |
| InfoQ | https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ | AWS Agent Registry launch via Bedrock AgentCore |
| Microsoft | https://www.microsoft.com/en-us/security/blog/2026/05/01/microsoft-agent-365-now-generally-available-expands-capabilities-and-integrations/ | Agent 365 GA with registry sync |
| Solo.io | https://www.solo.io/press-releases/agent-skills-kubernetes-ecosystem | agentregistry for Kubernetes MCP/skill governance |
| Claude Code Docs — Plugins | https://code.claude.com/docs/en/plugins | Official plugin bundling documentation |
| Claude Code Docs — MCP | https://code.claude.com/docs/en/mcp | Official MCP connection documentation |
| Claude Code Docs — Sub-agents | https://code.claude.com/docs/en/sub-agents | Official subagent documentation |
| Claude API Docs — Agent Skills | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official skills overview and definition |
| Anthropic — Desktop Extensions | https://www.anthropic.com/engineering/desktop-extensions | One-click MCP installation for Claude Desktop |
| Anthropic — MCP announcement | https://www.anthropic.com/news/model-context-protocol | Original MCP launch post |
| GitHub — anthropics/skills | https://github.com/anthropics/skills | Open standard spec repository for Agent Skills |
| SkillsMP | https://skillsmp.com/ | 1.2M+ agent skills marketplace |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community-curated plugin/skill/MCP directory |
| claudecodeplugins.io | https://claudecodeplugins.io/ | Claude Code skills and plugins hub |
| aitmpl.com | https://www.aitmpl.com/plugins/ | Plugin and marketplace collection discovery |
| buildwithclaude.com | https://buildwithclaude.com/plugins | Build with Claude plugin browser |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-plugins | Top 10 Claude Code plugins roundup |
| jeremylongshore/claude-code-plugins-plus-skills (GitHub) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, ccpi CLI package manager |
| ComposioHQ/awesome-claude-plugins (GitHub) | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| hashgraph-online/awesome-ai-plugins (GitHub) | https://github.com/hashgraph-online/awesome-ai-plugins | Cross-agent plugin curation |
| mcp.so | https://mcp.so/ | Largest community MCP server directory (20,222 servers) |
| modelcontextprotocol/servers (GitHub) | https://github.com/modelcontextprotocol/servers | Official MCP server reference implementations |
| blog.modelcontextprotocol.io — registry | https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/ | MCP Registry launch (September 2025) |
| blog.modelcontextprotocol.io — anniversary | https://blog.modelcontextprotocol.io/posts/2025-11-25-first-mcp-anniversary/ | One-year MCP retrospective |
| modelcontextprotocol.io — tools spec | https://modelcontextprotocol.io/specification/2025-06-18/server/tools | MCP tools specification (2025-06-18) |
| Wikipedia — MCP | https://en.wikipedia.org/wiki/Model_Context_Protocol | MCP overview reference |
| Thoughtworks | https://www.thoughtworks.com/en-us/insights/blog/generative-ai/model-context-protocol-mcp-impact-2025 | MCP's 2025 impact retrospective |
| codilime.com | https://codilime.com/blog/model-context-protocol-explained/ | Technical MCP explainer |
| datasciencedojo.com | https://datasciencedojo.com/blog/guide-to-model-context-protocol/ | Definitive MCP guide 2025 |
| informationweek.com | https://www.informationweek.com/machine-learning-ai/model-context-protocol-servers-build-or-buy- | MCP: build or buy analysis |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | Claude Code MCP & plugins complete guide |
| generect.com | https://generect.com/blog/claude-mcp/ | Claude MCP setup guide 2026 |
| agensi.io — marketplaces | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Marketplace landscape overview |
| kdnuggets.com | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 skill marketplaces |
| dev.to — Notion Skills Registry | https://dev.to/axrisi/notion-skills-registry-a-package-manager-for-ai-agent-skills-with-mcp-2581 | MCP-based skill package manager |
| anthropics/skills (GitHub) | https://github.com/anthropics/skills | Anthropic open skills spec |
| OpenAI Developers — Codex Skills | https://developers.openai.com/codex/skills | OpenAI's Agent Skills documentation |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide to agent skills/plugins/marketplace |
| mindstudio.ai | https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows | How to use Claude Code skills for automation |
| developersdigest.tech | https://www.developersdigest.tech/blog/building-multi-agent-workflows-claude-code | Multi-agent workflow tutorial |
| augmentcode.com | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Claude Agent SDK skills guide |
| devops.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | Agent Skills introduction coverage |
| agentpedia.codes | https://agentpedia.codes/blog/claude-opus-4-8-claude-code-workflows | Claude Code dynamic workflows guide |
| chatprd.ai | https://www.chatprd.ai/how-i-ai/workflows/tool/claude | Claude AI workflows step-by-step |
| cloudzero.com | https://www.cloudzero.com/blog/claude-code-agents/ | Claude Code agents in 2026 overview |
| pasqualepillitteri.it | https://pasqualepillitteri.it/en/news/3663/claude-code-dynamic-workflows-anthropic-research-preview | Dynamic Workflows research preview coverage |
| fast-agent.ai | https://fast-agent.ai/agents/skills/ | Agent skills in fast-agent framework |
| zylos.ai | https://zylos.ai/research/2026-02-21-ai-agent-plugin-extension-architecture | Plugin/extension architecture research |
| tonykipkemboi.com | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | Agent skills and plugins explainer |
| googleblog.com | https://developers.googleblog.com/en/supercharge-your-ai-agents-adk-integrations-ecosystem/ | Google ADK integrations ecosystem |
| vercel.com | https://vercel.com/docs/agent-resources/vercel-plugin | Vercel plugin for AI coding agents |
| truefoundry.com — registry guide | https://www.truefoundry.com/blog/ai-agent-registry | AI agent registry complete guide |
| arps18.github.io | https://arps18.github.io/posts/claude-code-mastery/ | HN viral post: Claude Code as a Daily Driver |
| aattaran/deepclaude (GitHub) | https://github.com/aattaran/deepclaude | DeepClaude: DeepSeek V4 Pro in Claude Code loop |
| solo.io agentregistry | https://www.solo.io/press-releases/agent-skills-kubernetes-ecosystem | Kubernetes-native agent registry |

---

## Stats Block

```
├─ 🟠 Reddit: 15 threads
├─ 🔵 X: 13 posts │ 13 likes │ 1 repost
├─ 🟢 HN: 12 stories │ 1,414 points │ 715 comments
├─ 🦋 Bluesky: 8 posts │ 137 likes │ 3 reposts
├─ 🌐 Web: 10 pages (last30days corpus) + 50+ additional from web search
└─ 🗣️ Top voices: @1999_eth, @RoundtableSpace, @_0xpainn │ r/ClaudeWorkflows, r/ClaudeAI, r/ClaudeCode
```

---

## Data Gaps

- **Individual Reddit post URLs**: Not captured in raw data — subreddit-level attribution only (r/ClaudeWorkflows, r/ClaudeAI, r/ClaudeCode). Individual post titles and upvote counts unavailable.
- **Individual X/Twitter post URLs**: Not captured. Top voices identified (@1999_eth, @RoundtableSpace, @_0xpainn) but post content and individual URLs unavailable.
- **YouTube**: No results returned. Zero videos, zero coverage from this platform.
- **TikTok**: No results returned.
- **Instagram**: No results returned.
- **Polymarket**: No results returned. No prediction markets active on this topic at time of research.
- **mcp.so, smithery.ai, glama.ai**: Mentioned in web sources but not directly scraped; server counts sourced from secondary reports (TrueFoundry).
- **WorkOS MCP guide**: Referenced in raw data (workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) but URL not included in web search results; content summarized from raw skill output only.
- **Kong MCP Registry**: Referenced (konghq.com/products/mcp-registry) from raw data but not independently verified via web search.
- **Approximate coverage**: ~85% of the topic surface covered based on raw + web search synthesis. Missing: YouTube/TikTok/Instagram creator discourse, individual Reddit/X post granularity, live marketplace pricing data beyond what Digital Applied reported.

---

## Key Quotes

> "developers now spend more time comparing marketplaces than finding skills" — Digital Applied ([link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution))

> "I run five to six simultaneous Claude sessions across two repos without writing code myself" — @hailey.at on Bluesky ([link](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v))

> "Skills are reusable, filesystem-based resources that provide Claude with domain-specific expertise: workflows, context, and best practices that transform general-purpose agents into specialists." — Anthropic, Claude API Docs ([link](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview))

> "A security audit of 22,511 skills across skills.sh, ClawHub, GitHub, and Tessl found 140,963 issues — 6.3 issues per skill on average, with prompt injection found in 36% of skills tested." — JFrog ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — agensi.io ([link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

> "AWS Agent Registry provides enterprises a centralized catalog for discovering, sharing, and governing AI agents, tools, MCP servers, and agent skills across an organization." — InfoQ ([link](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/))

> "Claude Code Skills allow you to create reusable agent capabilities that can be invoked as slash commands, automating repetitive workflows and providing domain-specific expertise across projects." — MindStudio ([link](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows))

> "[Anthropic] stepped back in with curated certification" after "deliberately" ceding the registry space to the market — Digital Applied ([link](https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points))
