# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-11
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 18 posts | 2,196 likes, 239 reposts | Top voice: @claudeai (1,154 likes), @cyrilXBT (634 likes across posts) |
| Hacker News | 1 story | 76 points, 36 comments | Agent-skills-eval benchmark tool |
| Web | 35 pages | — | 8 engine-crawled + 27 via WebSearch supplements |
| Reddit | 0 threads | — | 403/402 errors on all 7 subreddits (API gating) |
| YouTube | 0 videos | — | No results returned |
| TikTok | 0 videos | — | No results returned |
| Bluesky | 0 posts | — | Not configured |
| Polymarket | 0 markets | — | No relevant markets found |

---

## Synthesized Findings

### 1. Taxonomy Wars: Skills vs MCP vs Plugins vs Hooks

The single most-discussed educational need in this space is definitional clarity. Multiple guides published in April-May 2026 converge on the same framework, confirming this is the top onboarding friction:

- **Skills** are markdown instruction files - behavioral templates Claude reads and follows. They cost 30-50 tokens each and are loaded on demand. They teach Claude *how to do things*.
- **MCP servers** are separate processes exposing typed tools via the Model Context Protocol. They can consume 50K+ tokens and connect external systems (databases, APIs, design files, cloud services). They give Claude *access to things*.
- **Plugins** are full bundles - code-level packages that can include skills, agents, hooks, MCP servers, LSP servers, and monitors. They are the distributable unit.
- **Hooks** are event-triggered actions that fire on specific lifecycle events (pre-commit, post-tool-call, session-start, etc.).

[claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers/) puts it cleanly: "A skill is a packet of natural-language instructions Claude reads and follows. An MCP server is a separate process exposing typed tools Claude can call via the Model Context Protocol." [claudecodeguides.com](https://claudecodeguides.com/mcp-vs-skills-vs-hooks-claude-code-extensions/) and [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins) published similar explainers in the same window, suggesting genuine ecosystem-wide confusion driving the content demand.

[@hypingai](https://x.com/hypingai/status/2053492750264508682) captures the practical unlock: "The underrated move is combining Claude Code with MCP servers - once you connect it to your actual tools (databases, APIs, design files), it stops being a chatbot and starts being a legitimate engineering partner."

[@mylifcc](https://x.com/mylifcc/status/2053265352176644286) adds the key nuance for practitioners: "Skills lifted from Claude Code - leverage is files and CLI, not prompts. If Grok iOS opens to MCP servers day one, that's a tell about platform direction."

**Cross-platform signal:** Web (multiple guides), X (multiple explanatory threads)

---

### 2. Scale Numbers: The Ecosystem Is Larger Than Most Users Know

The Claude Code plugin ecosystem is now substantially larger than most users realize, which explains the viral "Resource Bible" posts flooding X on May 10-11:

Per [dev.to/raxxostudios](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) and [skillsplayground.com](https://skillsplayground.com/guides/claude-code-plugins/): the Claude plugin ecosystem has **32,018 active plugins** and **282,356 total components**, broken down as:
- 161,541 skills
- 58,116 commands
- 48,047 agents
- 7,159 MCP servers

[claudemarketplaces.com](https://claudemarketplaces.com/) reports 4,200+ skills, 770+ MCP servers, and 140,000+ monthly visitors. OpenClaw's marketplace (tracked by [@cyrilXBT](https://x.com/cyrilXBT/status/2051507710739521633)) separately lists **13,700+ skills**.

On May 10, [@cyrilXBT](https://x.com/cyrilXBT/status/2053360889592705473) posted "THE CLAUDE CODE RESOURCE BIBLE JUST DROPPED. 54 tools. Agents. MCP servers. Skills. Automation. Most people have never seen this stack. That is your edge." - it got 571 likes and 90 reposts. The same thread format was republished by [@Dharmikpawar31](https://x.com/Dharmikpawar31/status/2053418519816216760) (95 likes) and [@smratitiwa86867](https://x.com/smratitiwa86867/status/2053702989874110755) (15 likes) within 24 hours, suggesting a coordinated amplification pattern or viral meme around "stack awareness."

[@krishdotdev](https://x.com/krishdotdev/status/2053516887716421859) published a curated "Top 50 MCP Servers for Claude Code" thread listing awesome-claude-code, awesome-mcp-servers, Glama directory, claude-code.nvim, Claude Flow, and more.

**Cross-platform signal:** X (viral posts), Web (directory sites)

---

### 3. MCP Becomes a Linux Foundation Standard

The Model Context Protocol, originally announced by Anthropic in November 2024, underwent a significant governance shift in December 2025: Anthropic donated MCP to the **Agentic AI Foundation (AAIF)**, a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI.

Per [workos.com](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) and [wikipedia.org/wiki/Model_Context_Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol): as of early 2026, 500+ public MCP servers are available and the protocol is supported by Anthropic, OpenAI, and Google DeepMind.

A major January 2026 extension - **MCP Apps** (formalized under SEP-1865) - standardizes delivery of interactive UIs (React dashboards, forms, data visualizations) from MCP servers to host applications. [The Register](https://www.theregister.com/2026/01/26/claude_mcp_apps_arrives/) covered the launch as "Claude supports MCP Apps, presents UI within chat window." The [MCP Blog](https://blog.modelcontextprotocol.io/posts/2026-01-26-mcp-apps/) announced it as MCP Apps (formerly mcp-ui).

In parallel, Claude Code now supports **remote MCP servers** with no local setup required (per [@AnthropicAI](https://x.com/AnthropicAI/status/1935367951542280239)) and **Desktop Extensions (.dxt files)** for one-click local server installation (per [@AnthropicAI](https://x.com/AnthropicAI/status/1938272883618312670)).

[workos.com](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) and [sureprompts.com](https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026) both confirm this makes MCP the de facto inter-agent protocol layer.

**Cross-platform signal:** Web (official docs + news coverage), X (announcements)

---

### 4. Agent Skills as a Cross-Vendor Open Standard

A quieter but structurally significant development: in December 2025, Anthropic released the **Agent Skills specification as an open standard**, which OpenAI then adopted for Codex CLI and ChatGPT. Per [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/):

- The SKILL.md format (markdown instruction files with frontmatter) is now cross-compatible with Claude Code, OpenAI's Codex CLI, and ChatGPT.
- [Codex CLI v0.121](https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/) shipped a Marketplace CLI, Agent Identity system, and the infrastructure for plugin distribution.
- Microsoft has a [microsoft/agent-skills](https://deepwiki.com/microsoft/agent-skills/3.5-skills-catalog) repository with a skills catalog and plugin documentation.
- [devblogs.microsoft.com](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) published "Extend your coding agent with .NET Skills," showing the pattern spreading to the .NET ecosystem.
- The npm package [@olegkoval/agent-skills](https://registry.npmjs.org/@olegkoval/agent-skills) (v1.0.1, published April 26, 2026) describes itself as "Agent-agnostic skill catalog for Codex, Claude, Cursor, and other skill-aware tools" - 282.2KB, MIT licensed, available at [github.com/oleg-koval/agent-skills](https://github.com/oleg-koval/agent-skills).

The [.well-known proposal](https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/) (my2cents.ai, April 17) proposes standardized `/.well-known/agent-skills/` paths for skill auto-discovery, allowing any website to advertise compatible skills that agents can discover and install automatically. The piece covers the SKILL.md format, Claude Code Plugin Marketplace architecture, and the discovery mechanism in detail.

[luongnv89/agent-skill-manager](https://github.com/luongnv89/agent-skill-manager/pull/149) (257 stars, TypeScript) merged PR #149 on April 12 adding plugin marketplace skill discovery - a universal skill manager for AI coding agents.

**Cross-platform signal:** Web (blog posts, npm, GitHub), HN (agent-skills-eval)

---

### 5. Evaluating Agent Skills: Do They Actually Work?

On May 7, HN user **darkrishabh** submitted [Show HN: Agent-skills-eval - Test whether Agent Skills improve outputs](https://github.com/darkrishabh/agent-skills-eval), which reached **76 points and 36 comments** - the top-scoring item in this research window.

The framing is notable: rather than assuming skills improve outputs, the tool actually tests whether they do. This represents a maturation signal - the ecosystem has grown large enough that evaluation and benchmarking tools are now needed.

The 36-comment thread (not captured in raw content but signaled by engagement) likely covers questions about which skill types show the most consistent improvement, how to measure skill quality, and what failure modes emerge from poorly-written skills.

This connects to a broader pattern across the web: [duet.so/guides/claude-code-skills-complete-guide](https://duet.so/guides/claude-code-skills-complete-guide) published a 32-minute "Claude Code Skills Complete Guide" on May 2 covering SKILL.md format, MCP, Subagents, and Teams - suggesting demand for rigorous skill-writing practices, not just installation guides.

**Cross-platform signal:** Hacker News (primary), Web (guide content)

---

### 6. Marketplace Discovery: The Bottleneck Nobody Has Solved

Eight major marketplaces now compete in this space per [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution): Claude Skills, GPT Store, MCP Hubs, Hugging Face Spaces, Replit Agent Market, LangChain Hub, Vercel Agent Gallery, and Cloudflare AI Marketplace. Each serves a different audience with different discovery mechanics.

But the key tension is curation vs. scale:
- **[SkillsMP](https://skillsmp.com/)** indexes 800,000+ skills scraped from public GitHub repositories, filtering for those with at least 2 GitHub stars. Massive catalog, minimal curation.
- **[Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)** is a curated, security-scanned marketplace with creator payments and MCP live access. Smaller catalog but every skill reviewed before listing.
- **[claudemarketplaces.com](https://claudemarketplaces.com/)** is community-curated with voting and ratings, crossing 150 listed skills in March 2026.
- **[ClawHub](https://pypi.org/project/clawhub/)** (PyPI) serves as an agent skill registry specifically for OpenClaw skills.

[digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) identifies the core pain point: "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction."

[@RoyAmal](https://x.com/RoyAmal/status/2053533291295437219) published a curated resource list on X: Main repo, Claude Code docs, MCP docs, Anthropic Skills repo, Awesome MCP Servers, Smithery, MCP Registry, SkillHub, Claude Cookbook, ECC Tools - pointing to fragmentation that still requires manual navigation.

The [.well-known proposal](https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/) attempts to solve this with HTTP-based auto-discovery, but per the piece's "Current State" section it remains experimental.

**Cross-platform signal:** Web (multiple marketplace comparison posts), X (resource curation threads)

---

### 7. Claude Code as Professional Standard Tool

[@claudeai](https://x.com/claudeai/status/2051679630856249406) posted on May 5 (1,154 likes, 66 reposts - the highest-engagement post in the data): "Each agent ships with the connectors, skills, and subagents the task needs, ready to use as-is or adapt to your firm's own standards." This was in the context of Anthropic's financial services agent launch with pre-built MCP connectors for financial data providers.

[@ds_bun_](https://x.com/ds_bun_/status/2053733594800025953) observes the labor market signal: "Job posts now want AI-assisted dev skills - Teams expect CLI fluency + AI leverage - Claude Code = standard tool now - No experience = passed over."

Industry-specific plugin marketplaces are emerging: [@AIDailyGems](https://x.com/AIDailyGems/status/2053659305593770412) highlighted "Claude Code plugin marketplace for Shopware development. Provides MCP servers, skills, agents, hooks, and commands to integrate." Per [agent-drop.com](https://agent-drop.com/claude-code-mcp), Claude Code was one of the first hosts to ship MCP support out of the box.

[@alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/) notes that most Claude Code users are still running vanilla without skills, plugins, or MCP servers - suggesting the ecosystem's growth is currently ahead of mainstream adoption.

[@per_arneng](https://x.com/per_arneng/status/2053593519927783733) on practical use: "Or, you could use Claude Code to manage your whole network with skills and/or MCP servers. I have a default main network and an IoT network. The IoT network is for untrustworthy devices. Super easy to setup even with AI."

**Cross-platform signal:** X (professional use cases), Web (industry-specific guides)

---

### 8. Agent Identity, Trust, and the Crypto Marketplace Layer

[@BlockLayerPod](https://x.com/BlockLayerPod/status/2044857384355438822) (147 likes, 18 replies, April 16) identifies an emerging gap in trusted agent marketplaces: "Agent legitimacy verification is still the big gap - ERC-8004 fixes that. Zyfai (a leading yield agent integrating the standard) says ERC-8004 launches this Friday, bringing onchain identity + reputation for trusted agent marketplaces. x402 handles how agents pay - ERC-8004 handles whether they should."

A follow-up [@BlockLayerPod](https://x.com/BlockLayerPod/status/2045953206358806868) post (103 likes, April 19) covers OpenClaw going viral as ERC-8004 launched on mainnet: "Agents finally have the identity, reputation, and payment infrastructure they need to operate autonomously."

This represents a distinct strand of the agent skills ecosystem: not just capability distribution (marketplaces), but trust establishment for autonomous agent-to-agent interactions - particularly relevant as agents are expected to transact and use skills without human oversight.

**Cross-platform signal:** X (BlockLayerPod analysis threads)

---

## Cross-Source Patterns

### Pattern 1: Skills taxonomy confusion drives content demand
- **Signal:** Three independent web guides (morphllm.com, claudecodeguides.com, claudskills.com) published within a 3-week window all explaining the same Skills vs MCP vs Plugins distinction. Multiple X threads also explain the same taxonomy.
- **Platforms:** Web (multiple), X
- **Key quote:** [@hypingai](https://x.com/hypingai/status/2053492750264508682): "The underrated move is combining Claude Code with MCP servers - once you connect it to your actual tools (databases, APIs, design files), it stops being a chatbot and starts being a legitimate engineering partner."

### Pattern 2: "Resource Bible" viral format as ecosystem wayfinding
- **Signal:** Three separate X accounts posted nearly identical "Resource Bible / Playbook" threads on May 10-11 listing 54 tools, MCP servers, skills, and automation resources. High engagement (571 + 95 + 15 likes) suggests real demand for curated discovery.
- **Platforms:** X
- **Key quote:** [@cyrilXBT](https://x.com/cyrilXBT/status/2053360889592705473): "Most people have never seen this stack. That is your edge."

### Pattern 3: Cross-vendor skill portability is real but underreported
- **Signal:** Agent Skills spec adopted by Anthropic (Claude), OpenAI (Codex/ChatGPT), and Microsoft (.NET); @olegkoval/agent-skills npm package explicitly targets "Codex, Claude, Cursor, and other skill-aware tools."
- **Platforms:** Web (blog posts, npm, GitHub), X (announcements)
- **Key quote:** [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/): "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT."

### Pattern 4: Discovery bottleneck is the shared unsolved problem
- **Signal:** Both the web analysis (digitalapplied.com) and X curation threads (RoyAmal, cyrilXBT, krishdotdev) converge on the same problem: there are too many skills/servers/tools and no good way to find the right ones.
- **Platforms:** Web, X
- **Key quote:** [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution): "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction."

---

## Per-Platform Tables

### X/Twitter

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | "Each agent ships with the connectors, skills, and subagents the task needs, ready to use as-is or adapt to your firm's own standards." | 1,154 | 66 | [link](https://x.com/claudeai/status/2051679630856249406) |
| @cyrilXBT | "THE CLAUDE CODE RESOURCE BIBLE JUST DROPPED. 54 tools. Agents. MCP servers. Skills. Automation. Most people have never seen this stack." | 571 | 90 | [link](https://x.com/cyrilXBT/status/2053360889592705473) |
| @BlockLayerPod | "ERC-8004 launches...bringing onchain identity + reputation for trusted agent marketplaces. x402 handles how agents pay - ERC-8004 handles whether they should." | 147 | 8 | [link](https://x.com/BlockLayerPod/status/2044857384355438822) |
| @BlockLayerPod | "OpenClaw, an open-source agent framework, went viral in late Jan. as ERC-8004 launched on mainnet. Agents finally have the identity, reputation, and payment infrastructure..." | 103 | 9 | [link](https://x.com/BlockLayerPod/status/2045953206358806868) |
| @Dharmikpawar31 | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack." | 95 | 45 | [link](https://x.com/Dharmikpawar31/status/2053418519816216760) |
| @cyrilXBT | "OpenClaw just shipped its biggest release yet. 13,700+ skills in the marketplace. Per-agent model selection." | 46 | 7 | [link](https://x.com/cyrilXBT/status/2051507710739521633) |
| @smratitiwa86867 | "THE CLAUDE CODE PLAYBOOK JUST EXPANDED. 54+ tools. MCP servers. Agent frameworks. Automation stacks. Most developers are still using AI like a chatbot." | 15 | 6 | [link](https://x.com/smratitiwa86867/status/2053702989874110755) |
| @krishdotdev | "Top 50 MCP Servers for claude code" (lists awesome-claude-code, awesome-mcp-servers, Glama directory, claude-code.nvim, Cursor, Cline...) | 15 | 0 | [link](https://x.com/krishdotdev/status/2053516887716421859) |
| @cyrilXBT | "Everyone wants their own AI agent. Almost no one wants to spin up a server, manage updates, and babysit deploys. MyClaw fixed that." | 19 | 1 | [link](https://x.com/cyrilXBT/status/2051507739097264315) |
| @ds_nana_ | "Still copying tutorial code that breaks in prod? Claude Code Masterclass: CLI AI that reads files, runs commands, edits code. Custom commands, MCP servers, GitHub" | 5 | 5 | [link](https://x.com/ds_nana_/status/2053340756409233807) |
| @hypingai | "The underrated move is combining Claude Code with MCP servers - once you connect it to your actual tools, it stops being a chatbot and starts being a legitimate engineering partner." | 3 | 0 | [link](https://x.com/hypingai/status/2053492750264508682) |
| @ds_bun_ | "Job posts now want AI-assisted dev skills. Teams expect CLI fluency + AI leverage. Claude Code = standard tool now. No experience = passed over." | 2 | 0 | [link](https://x.com/ds_bun_/status/2053733594800025953) |
| @per_arneng | "You could use Claude Code to manage your whole network with skills and/or MCP servers...Super easy to setup even with AI." | 2 | 0 | [link](https://x.com/per_arneng/status/2053593519927783733) |
| @AIDailyGems | "Claude Code plugin marketplace for Shopware development. Provides MCP servers, skills, agents, hooks, and commands to integrate" | 1 | 0 | [link](https://x.com/AIDailyGems/status/2053659305593770412) |
| @RoyAmal | "Worth Exploring on repo: Main Repo, Claude Code Docs, MCP Docs, Anthropic Skills Repo, Awesome MCP Servers, Smithery, MCP Registry, SkillHub..." | 1 | 0 | [link](https://x.com/RoyAmal/status/2053533291295437219) |
| @mylifcc | "Skills lifted from Claude Code - leverage is files and CLI, not prompts. If Grok iOS opens to MCP servers day one, that's a tell about platform direction." | 0 | 0 | [link](https://x.com/mylifcc/status/2053265352176644286) |
| @MoreClaudeNews | "If you havent noticed yet, Claude Code has now MCP Servers." | 0 | 0 | [link](https://x.com/MoreClaudeNews/status/2053392300206682437) |
| @cyrilXBT | "The builders who have a personal AI agent running 24/7 right now are not smarter. They just stopped waiting for setup to feel easy." | 17 | 2 | [link](https://x.com/cyrilXBT/status/2051507782017528154) |

### Hacker News

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| darkrishabh | Show HN: Agent-skills-eval - Test whether Agent Skills improve outputs | 76 | 36 | (Title is the framing: skills are assumed good; this tool actually tests if they are) | [github.com/darkrishabh/agent-skills-eval](https://github.com/darkrishabh/agent-skills-eval) |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudskills.com | [claude-code-skills-vs-mcp-servers](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers/) | Canonical skills vs MCP explainer; skills = natural-language instructions, MCP = typed tools over protocol |
| claudepluginhub.com | [mcp-server-plugins-for-claude-code](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code) | Developer's guide to memory, automation, and documentation MCP plugins |
| agent-drop.com | [claude-code-mcp](https://agent-drop.com/claude-code-mcp) | MCP setup guide; "Claude Code is one of the first hosts to ship MCP support out of the box" |
| claudecodeguides.com | [mcp-vs-skills-vs-hooks](https://claudecodeguides.com/mcp-vs-skills-vs-hooks-claude-code-extensions/) | Three-way extension guide: MCP connects data/APIs, Skills define behavior templates, Hooks trigger on events |
| duet.so | [claude-code-skills-complete-guide](https://duet.so/guides/claude-code-skills-complete-guide) | 32-minute comprehensive SKILL.md, MCP, Subagents, and Teams guide (updated May 2, 2026) |
| my2cents.ai | [agentic-registries-skills-discovery](https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/) | The Agent Skills .well-known proposal; three layers, SKILL.md format, plugin marketplace architecture, discovery mechanism |
| registry.npmjs.org | [@olegkoval/agent-skills](https://registry.npmjs.org/@olegkoval/agent-skills) | Agent-agnostic skill catalog npm package targeting Codex, Claude, Cursor; v1.0.1 published Apr 26, 2026 |
| github.com | [luongnv89/agent-skill-manager #149](https://github.com/luongnv89/agent-skill-manager/pull/149) | Universal skill manager (257 stars, TypeScript); PR #149 adds plugin marketplace skill discovery |
| nimbalyst.com | [claude-code-plugins-guide](https://nimbalyst.com/blog/claude-code-plugins-guide/) | 2026 guide: plugins bundle skills, agents, hooks, MCP servers; centralized discovery, version pinning, auto-updates |
| morphllm.com | [claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Definitional guide 2026: Skills=markdown, Plugins=code, MCP=standard protocol |
| code.claude.com | [plugins-reference](https://code.claude.com/docs/en/plugins-reference) | Official plugin reference; alwaysLoad field, requires Claude Code v2.1.121+ |
| dev.to | [best-claude-code-skills-plugins-2026](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | 32,018 active plugins, 282,356 components (161,541 skills, 58,116 commands, 48,047 agents, 7,159 MCP servers) |
| firecrawl.dev | [best-claude-code-skills](https://www.firecrawl.dev/blog/best-claude-code-skills) | Top skills 2026; Figma, Playwright, Vercel, PostgreSQL, GitHub MCP servers (5-10 min setup) |
| skillsplayground.com | [claude-code-plugins](https://skillsplayground.com/guides/claude-code-plugins/) | Extension type guide; MCP is fourth-largest component type by count |
| alexop.dev | [understanding-claude-code-full-stack](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Most users still running vanilla - ecosystem growth ahead of mainstream adoption |
| mcpmarket.com | [ecosystem-guide](https://mcpmarket.com/tools/skills/ecosystem-guide) | claudemarketplaces.com crossed 150 skills in March 2026 |
| pypi.org | [clawhub](https://pypi.org/project/clawhub/) | Agent skill registry and marketplace plugin for CMDOP; OpenClaw skill discovery |
| chris-ayers.com | [agent-skills-plugins-marketplace](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Anthropic released Agent Skills spec as open standard Dec 2025; OpenAI adopted for Codex CLI + ChatGPT |
| skillsmp.com | [skillsmp.com](https://skillsmp.com/) | 800,000+ skills scraped from GitHub; filters for 2+ stars |
| digitalapplied.com | [ai-agent-marketplaces-2026](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | Eight marketplaces; discovery is the real bottleneck |
| deepwiki.com | [microsoft/agent-skills plugins](https://deepwiki.com/microsoft/agent-skills/4-plugins) | Microsoft agent-skills plugin catalog documentation |
| deepwiki.com | [microsoft/agent-skills catalog](https://deepwiki.com/microsoft/agent-skills/3.5-skills-catalog) | Microsoft agent-skills skill catalog documentation |
| devblogs.microsoft.com | [extend-coding-agent-dotnet-skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | .NET Skills for coding agents; skills pattern spreading beyond Anthropic |
| agensi.io | [marketplace-comparison-2026](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026) | Curated vs scraped marketplace comparison; Agensi vs SkillsMP |
| agensi.io | [best-marketplaces-2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Best agent skills marketplaces 2026 with honest comparison |
| codex.danielvaughan.com | [codex-cli-v0121](https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/) | Codex CLI v0.121: Marketplace CLI, Agent Identity, Plugin Distribution - OpenAI's parallel marketplace trajectory |
| anthropic.com | [model-context-protocol](https://www.anthropic.com/news/model-context-protocol) | Original MCP announcement (Nov 2024); donated to AAIF/Linux Foundation Dec 2025 |
| blog.modelcontextprotocol.io | [mcp-apps](https://blog.modelcontextprotocol.io/posts/2026-01-26-mcp-apps/) | MCP Apps extension (SEP-1865): standardizes React UI delivery from MCP servers to hosts |
| theregister.com | [claude_mcp_apps_arrives](https://www.theregister.com/2026/01/26/claude_mcp_apps_arrives/) | The Register coverage of MCP Apps launch: "Claude supports MCP Apps, presents UI within chat window" |
| sureprompts.com | [mcp-complete-guide-2026](https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026) | 500+ public MCP servers, supported by Anthropic, OpenAI, and Google DeepMind |
| workos.com | [everything-about-mcp-2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) | Team guide: MCP governance (Linux Foundation), ecosystem growth, implementation guide |
| anthropic.com | [code-execution-with-mcp](https://www.anthropic.com/engineering/code-execution-with-mcp) | Engineering post: code execution with MCP for building efficient AI agents |
| code.claude.com | [mcp docs](https://code.claude.com/docs/en/mcp) | Official MCP documentation for Claude Code; alwaysLoad, remote MCP server support |
| wikipedia.org | [Model_Context_Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol) | MCP Wikipedia entry: open standard, November 2024 origin, Linux Foundation governance |
| nimbalyst.com | [claude-code-mcp-setup](https://nimbalyst.com/blog/claude-code-mcp-setup/) | Practical 2026 MCP setup guide for Claude Code |

---

## Stats Block

```
├─ 🔵 X: 18 posts │ 2,196 likes │ 239 reposts
├─ 🟡 HN: 1 story │ 76 points │ 36 comments
├─ 🌐 Web: 35 pages - claudskills.com, claudepluginhub.com, agent-drop.com, claudecodeguides.com, duet.so, my2cents.ai, registry.npmjs.org, GitHub, nimbalyst.com, morphllm.com, code.claude.com, dev.to, firecrawl.dev, skillsplayground.com, alexop.dev, mcpmarket.com, pypi.org, chris-ayers.com, skillsmp.com, digitalapplied.com, deepwiki.com, devblogs.microsoft.com, agensi.io, codex.danielvaughan.com, anthropic.com, blog.modelcontextprotocol.io, theregister.com, sureprompts.com, workos.com, wikipedia.org, and more
└─ 🗣️ Top voices: @claudeai, @cyrilXBT, @BlockLayerPod, @Dharmikpawar31
```

---

## Data Gaps

- **Reddit: 0 results** - All 7 targeted subreddits (r/ClaudeAI, r/LocalLLaMA, r/ChatGPTCoding, r/singularity, r/PromptEngineering, r/artificial, r/MachineLearning) returned HTTP 403 (public API) and HTTP 402 Payment Required (ScrapeCreators API). Reddit is likely the highest-signal community for this topic; absence is a significant coverage gap. The r/ClaudeAI and r/LocalLLaMA communities are active and almost certainly have relevant threads.
- **YouTube: 0 results** - No YouTube results returned by any search method (yt-dlp or ScrapeCreators). Tutorial and walkthrough videos for Claude Code skills and MCP setup almost certainly exist and were missed.
- **TikTok: 0 results** - ScrapeCreators returned HTTP 402; hashtags #claudecode, #mcpserver were not searched.
- **Bluesky: 0 results** - Not configured (no BSKY credentials).
- **GitHub: 0 results** - No GitHub token available; several highly relevant repos (anthropics/claude-code, modelcontextprotocol, luongnv89/asm, oleg-koval/agent-skills) were surfaced via web but not via direct API.
- **Polymarket: 0 markets** - No prediction markets on agent skill ecosystem topics.
- **Approximate coverage:** ~40% of ideal. X and Web coverage is solid. Reddit + YouTube absence is the biggest gap for community sentiment and practical tutorials.
- **Noise note:** Several X posts (@cyrilXBT, @smratitiwa86867, @Dharmikpawar31) appear to be part of a coordinated content amplification campaign around the same "Claude Code Resource Bible" thread format. Engagement counts are real but the content is derivative of the same curated link list.

---

## Key Quotes

> "The underrated move is combining Claude Code with MCP servers - once you connect it to your actual tools (databases, APIs, design files), it stops being a chatbot and starts being a legitimate engineering partner." - [@hypingai](https://x.com/hypingai/status/2053492750264508682) on X

> "Each agent ships with the connectors, skills, and subagents the task needs, ready to use as-is or adapt to your firm's own standards." - [@claudeai](https://x.com/claudeai/status/2051679630856249406) on X (1,154 likes)

> "Skills lifted from Claude Code - leverage is files and CLI, not prompts. If Grok iOS opens to MCP servers day one, that's a tell about platform direction." - [@mylifcc](https://x.com/mylifcc/status/2053265352176644286) on X

> "Job posts now want AI-assisted dev skills. Teams expect CLI fluency + AI leverage. Claude Code = standard tool now. No experience = passed over." - [@ds_bun_](https://x.com/ds_bun_/status/2053733594800025953) on X

> "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." - [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

> "ERC-8004 launches this Friday, bringing onchain identity + reputation for trusted agent marketplaces. x402 handles how agents pay - ERC-8004 handles whether they should." - [@BlockLayerPod](https://x.com/BlockLayerPod/status/2044857384355438822) on X (147 likes)

> "THE CLAUDE CODE RESOURCE BIBLE JUST DROPPED. 54 tools. Agents. MCP servers. Skills. Automation. Most people have never seen this stack. That is your edge." - [@cyrilXBT](https://x.com/cyrilXBT/status/2053360889592705473) on X (571 likes)

> "A skill is a packet of natural-language instructions Claude reads and follows. An MCP server is a separate process exposing typed tools Claude can call via the Model Context Protocol." - [claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers/)

> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." - [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)
