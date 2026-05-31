Step 2.5 complete. Now synthesizing the full output per the LAWs and voice contract.

Pre-synthesis self-check:
- Badge on line 1: YES
- No `##` section headers in body: YES (will use bold-lead-in paragraphs)
- No em-dashes: YES (will use ` - ` only)
- No trailing Sources block: YES (LAW 1 override)
- Engine footer pass-through verbatim: YES (LAW 5)
- Inline markdown links for all citations: YES (LAW 8)
- No raw evidence clusters in body: YES (LAW 6)

---

🌐 last30days v3.3.1 · synced 2026-05-31

What I learned:

**Dynamic Workflows just shipped and it is the biggest Claude Code moment in months** - On May 28, 2026, Anthropic opened dynamic workflows in research preview alongside Claude Opus 4.8 - Claude now writes orchestration scripts that fan work to up to 1,000 parallel subagents (max 16 concurrent), with only the final answer landing in Claude's context instead of every intermediate result. The [Hacker News thread](https://news.ycombinator.com/item?id=44127000) on the [official announcement](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) pulled 439 points and 251 comments in under 48 hours. The key conceptual shift people keep citing: with a skill, Claude follows a Markdown file but still acts as the orchestrator turn-by-turn; with a workflow, the plan lives in code and Claude's context holds only the output.

**The skills-vs-plugins-vs-MCP distinction has finally crystallized** - A year of confusion is resolving: skills are on-demand Markdown instruction files (~100 tokens to scan, ~5k tokens to load), plugins are the distribution format that bundles skills + hooks + MCP configs into a single installable package, and MCP servers are external tool connections that can consume 50k+ tokens. The [llmbestpractices.com guide](https://llmbestpractices.com/ai-agents/claude-code-mcp) frames the practical rule as "prefer MCP tools over Bash when the integration will be used across sessions." The community on [r/ClaudeAI](https://reddit.com/r/ClaudeAI) and [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows) has been actively debugging these boundaries - the most-upvoted threads this month are the ones asking "when do I use a skill vs a plugin vs an MCP?"

**The official marketplace and a fragmented third-party ecosystem are now both live** - [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) ships with Claude Code automatically and catalogs 55+ curated plugins. Third-party directories ([claudemarketplaces.com](https://claudemarketplaces.com/), [awesome-skills.com](https://awesome-skills.com/), [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons)) each track 100-150+ plugins with separate install counts. The ecosystem reportedly grew from one registry in December 2025 to eight major marketplaces by Q2 2026 per [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). Cross-compatibility is the sleeper story: the Agent Skills spec is now adopted by Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, and GitHub Copilot - skills you write once run on all five without modification.

**Claude Orchestra is the open-source answer to skill sprawl** - [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/) surfaced an open-source system called Claude Orchestra this month (workflow value rated 90/100 by the community) for organizing and managing Claude Code skills, agents, and MCP servers at scale - targeting the "I have 30 skills and can't remember what any of them do" problem that multi-skill power users are hitting.

**Power users are running 5-6 parallel Claude sessions and barely writing code** - The most striking behavioral signal this month comes from [Bluesky user @hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v), whose post about running "five to six simultaneous claude sessions across two repos each chugging on a separate task" and "not opening neovim at all in the past two weeks" landed 115 likes. She credits [@ed3d.net](https://bsky.app)'s plugins and skills setup. A separate 100-tip megapost on [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/) detailing six weeks of building a persistent personal AI agent generated significant engagement - the kind of long-form field report that captures what the actual workflows look like in practice.

**MCP server overload is an emerging anti-pattern** - The consistent warning across [agensi.io's MCP ranking guide](https://www.agensi.io/learn/best-mcp-servers-2026), [nimbalyst.com](https://nimbalyst.com/blog/best-claude-code-mcp-servers/), and community discussion: keep active MCP servers to 5-7 maximum. More than that and tool bloat degrades agent performance; Cursor reportedly has a soft ceiling of ~40 active tools across all connected MCP servers before it starts silently dropping access. The recommended core stack for most developers: GitHub MCP + filesystem MCP + one domain-specific server (Postgres, Playwright, Slack, Notion - pick one).

**[@HeyZaraKhan](https://x.com/HeyZaraKhan/status/2056422617351959030)'s "20 Claude GitHub repos that can change your life" list went viral** - 670 likes and 161 reposts on a thread enumerating Claude Code, Claude Cookbooks, Claude Quickstarts, Claude Desktop Extensions, Awesome Claude Code, Awesome MCP Servers, and a dozen more. It functions as an informal registry and a snapshot of what the community considers the canonical starting points in May 2026.

KEY PATTERNS from the research:
1. Skills are content, plugins are packaging - the split that was confusing in late 2025 has settled into a clear mental model per [r/ClaudeCode](https://reddit.com/r/ClaudeCode) and [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp)
2. Cross-agent portability is the under-reported story - Agent Skills spec compatibility across Claude Code, Codex CLI, Cursor, Gemini CLI, and Copilot means the skill-writing investment pays off across five tools per [augmentcode.com](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities)
3. Dynamic workflows vs skills: who holds the plan - workflows put orchestration in code (parallelizable, reusable, context-light); skills put it in Markdown (simpler, Claude-driven, context-heavier) per the [official Claude blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code)
4. MCP server fatigue is real - "start with 2-3, add only what your daily workflow demands" is the community consensus per [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-mcp-servers-claude-code) and [agensi.io](https://www.agensi.io/learn/best-mcp-servers-2026)
5. The marketplace fragmentation problem is unsolved - eight marketplaces, no unified search, per [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows) and [claudemarketplaces.com](https://claudemarketplaces.com/)

---
✅ All agents reported back!
├─ 🟠 Reddit: 17 threads
├─ 🔵 X: 10 posts │ 978 likes │ 219 reposts
├─ 🟡 HN: 26 storys │ 2,034 points │ 1,053 comments
├─ 🦋 Bluesky: 9 posts │ 138 likes │ 3 reposts
├─ 🌐 Web: 15 pages - aitoolsguidebook.com, llmbestpractices.com, career.leverx.com, claudefolio.com, augmentcode.com, amitray.com, blog.vibecoder.me, theaiarchitects.com
├─ 🗣️ Top voices: @ds_serena_, @HeyZaraKhan, @mimu_ai1 │ r/ClaudeAI, r/ClaudeWorkflows, r/ClaudeCode
└─ 📎 Raw results saved to ~/Documents/Last30Days/claude-code-skills-and-plugins-agent-skill-marketplaces-mcp-servers-and-tools-claude-code-extensions-reusable-agent-capabilities-skill-discovery-and-distribution-plugin-ecosystems-agent-tool-registries-custom-claude-code-workflows-raw-v3.md
---

I'm now an expert on Claude Code skills, plugins, MCP servers, and the agent tool ecosystem. Some things I can help with:
- What's the practical decision tree for when to use a skill vs a plugin vs an MCP server vs a dynamic workflow?
- Which MCP servers are actually worth installing for a TypeScript/Python developer right now?
- Break down how Claude Orchestra manages skill sprawl and whether it's production-ready
- Deep dive on the cross-agent portability story - which Agent Skills actually work across Cursor and Codex CLI today

I have all the links to the 77 items across the 17 Reddit threads, 10 X posts, 26 HN stories, 9 Bluesky posts, and 15 web pages I pulled from. Just ask.

result: Ran /last30days skill on Claude Code skills, plugins, MCP servers, agent marketplaces, and custom workflows - returned 77 items across Reddit, X, HN, Bluesky, and Web with full synthesis covering the May 28 dynamic workflows launch, the skills-vs-plugins-vs-MCP taxonomy, the 8-marketplace fragmentation, cross-agent portability, and MCP overload anti-patterns.

WEB SEARCH RESULTS 1 (Claude Code Skills):
Here is a consolidated set of results organized by category, drawing from all search findings:

---

## Claude Code Skills and Plugins — Recent Findings (Last 30 Days / May 2026)

---

### Official Anthropic Announcements (anthropic.com)

**1. "Customize Claude Code with plugins"**
URL: https://www.anthropic.com/news/claude-code-plugins
Date: Recent (2026)
Claude Code now supports plugins — custom collections of slash commands, subagents, MCP servers, and hooks installable with a single `/plugin` command, now in public beta. Use cases include code review enforcement, debugging pipelines, deployment workflows, and connecting external tools via MCP servers.

**2. "Introducing Agent Skills"**
URL: https://www.anthropic.com/news/skills
Date: Recent (2026)
Anthropic introduced Agent Skills: organized folders of instructions, scripts, and resources that agents discover and load dynamically to specialize their behavior. Skills install via plugins from the `anthropics/skills` marketplace and load automatically when relevant to a task.

**3. "Equipping agents for the real world with Agent Skills"**
URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
Date: Recent (2026)
An engineering deep-dive into how Agent Skills extend Claude's capabilities by packaging domain expertise into composable, filesystem-based resources. Covers the architecture behind dynamic skill discovery and loading in agentic workflows.

**4. "Enabling Claude Code to work more autonomously"**
URL: https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously
Date: Recent (2026)
Discusses expanded autonomous operation modes for Claude Code, including tighter integration with skills and hooks to reduce human intervention in long-running development tasks.

**5. "Code execution with MCP: building more efficient AI agents"**
URL: https://www.anthropic.com/engineering/code-execution-with-mcp
Date: Recent (2026)
Anthropic engineering post on how MCP-based code execution unlocks more reliable and efficient agent loops, covering sandboxing, tool call patterns, and integration with Claude Code's skill system.

---

### Official Anthropic GitHub Repositories (github.com)

**6. anthropics/skills — Public repository for Agent Skills**
URL: https://github.com/anthropics/skills
Date: Active/ongoing
Anthropic's official public repo for Agent Skills, with a `marketplace.json` catalog that Claude Code uses to browse and install skills. Skills here are Anthropic-vetted and load directly into Claude Code's `/plugin` discovery tab.

**7. anthropics/claude-plugins-official — Official plugin directory**
URL: https://github.com/anthropics/claude-plugins-official
Date: Active/ongoing
Anthropic's managed directory of high-quality, approved Claude Code plugins. Third-party partners submit plugins here for inclusion, with quality and security review before listing in the default marketplace tab.

**8. anthropics/claude-code — plugins/README.md**
URL: https://github.com/anthropics/claude-code/blob/main/plugins/README.md
Date: Active/ongoing
The canonical plugin format documentation in the main Claude Code repo, specifying plugin structure: metadata, MCP server configs, slash commands, agent definitions, and skill definitions — the reference for building compliant plugins.

---

### Community GitHub Marketplaces (github.com)

**9. netresearch/claude-code-marketplace**
URL: https://github.com/netresearch/claude-code-marketplace
Date: Active (2026)
A curated Agent Skills collection for AI-assisted development following the open `agentskills.io` standard, designed to be portable across Claude Code, Cursor, Copilot, Codex CLI, Gemini CLI, and 30+ other agents. Skills are fetched directly from their source repos at install time.

**10. wshobson/agents — Multi-harness agentic plugin marketplace**
URL: https://github.com/wshobson/agents
Date: Active (2026)
Contains 83 plugins, 191 agents, 155 skills, and 102 commands built for Claude Code and natively consumed by OpenAI Codex CLI, Cursor, OpenCode, and Gemini CLI from a single Markdown source — a notable cross-agent portability approach.

**11. alirezarezvani/claude-skills — 337 skills, 30+ agents**
URL: https://github.com/alirezarezvani/claude-skills
Date: Active (2026)
Large community collection of 337 Claude Code skills spanning engineering, marketing, product, compliance, C-level advisory, research, and business operations domains. Installable via `/plugin marketplace add` and `/plugin install` commands across multiple coding agents.

**12. jeremylongshore/claude-code-plugins-plus-skills**
URL: https://github.com/jeremylongshore/claude-code-plugins-plus-skills
Date: Active (2026)
Open-source marketplace offering 425 plugins, 2,810 skills, and 200 agents for Claude Code, paired with the `ccpi` CLI package manager and a directory site at tonsofskills.com.

**13. ComposioHQ/awesome-claude-skills**
URL: https://github.com/ComposioHQ/awesome-claude-skills
Date: Active (2026)
Curated "awesome list" of Claude Skills, resources, and tools for customizing Claude AI workflows, maintained by Composio. Useful as a discovery index for the broader skills ecosystem.

---

### MCP Ecosystem News (May 2026)

**14. "The AWS MCP Server is now generally available"**
URL: https://aws.amazon.com/about-aws/whats-new/2026/05/aws-mcp-server/
Date: May 6, 2026
AWS announced GA of the AWS MCP Server, giving AI coding agents (including Claude Code) secure, auditable access to AWS services via MCP. Represents a major enterprise infrastructure milestone for the protocol.

**15. "MCP Tunnels and Self-Hosted Sandboxes launch" (AAIF / Code with Claude London)**
URL: https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/
Date: May 19, 2026
MCP Tunnels entered research preview — outbound-only encrypted connections letting agents reach customer data without inbound firewall rules. Self-hosted sandboxes also entered public beta with Cloudflare, Daytona, Modal, and Vercel as providers.

**16. "What's New in Splunk AI 2026: MCP Server & Hosted Models"**
URL: https://community.splunk.com/t5/Product-News-Announcements/What-s-New-in-Splunk-AI-Vol-01-MCP-Hosted-Models-amp-SPL-AI/ba-p/758587
Date: 2026
Splunk launched an MCP server enabling AI agents (including Claude Code) to query and act on Splunk data, alongside hosted model support and SPL AI integrations.

**17. "MCP's biggest growing pains for production use will soon be solved"**
URL: https://thenewstack.io/model-context-protocol-roadmap-2026/
Date: 2026
The New Stack covers the MCP 2026 roadmap: stateless HTTP core, OAuth 2.1 alignment, server-rendered UIs via MCP Apps, and a Tasks extension for long-running work — addressing the main production deployment friction points.

---

### Scale Context

- As of May 24, 2026: ~9,652 servers in the official MCP Registry; ~15,926 GitHub repos tagged `mcp-server`
- MCP SDK downloads exceeded 97M/month (Python + TypeScript combined)
- 41% of surveyed software organizations have MCP servers in limited or broad production (Stacklok 2026 report)
- 200,000+ developers/month visiting skill/plugin marketplace directories

---

Sources:
- [Customize Claude Code with plugins | Claude](https://www.anthropic.com/news/claude-code-plugins)
- [Introducing Agent Skills | Claude](https://www.anthropic.com/news/skills)
- [Equipping agents for the real world with Agent Skills](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)
- [Enabling Claude Code to work more autonomously](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously)
- [Code execution with MCP | Anthropic Engineering](https://www.anthropic.com/engineering/code-execution-with-mcp)
- [anthropics/skills](https://github.com/anthropics/skills)
- [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
- [claude-code plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md)
- [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace)
- [wshobson/agents](https://github.com/wshobson/agents)
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)
- [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)
- [AWS MCP Server GA](https://aws.amazon.com/about-aws/whats-new/2026/05/aws-mcp-server/)
- [MCP Dev Summit North America 2026 | AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)
- [What's New in Splunk AI 2026](https://community.splunk.com/t5/Product-News-Announcements/What-s-New-in-Splunk-AI-Vol-01-MCP-Hosted-Models-amp-SPL-AI/ba-p/758587)
- [MCP roadmap 2026 | The New Stack](https://thenewstack.io/model-context-protocol-roadmap-2026/)
- [MCP Adoption Statistics 2026](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)

result: Compiled 17 recent results (May 2026) covering Claude Code plugins/skills official announcements on anthropic.com, official and community GitHub skill marketplaces, and MCP ecosystem news including AWS GA, MCP Tunnels preview, and protocol roadmap updates.

WEB SEARCH RESULTS 2 (MCP Ecosystem):
Here are the findings across all three searches, covering MCP server marketplaces, registries, and agent tool discovery developments from the last 30 days and recent months:

---

## MCP Registry & Official Infrastructure

**Title:** Introducing the MCP Registry
**URL:** https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/
**Date:** September 8, 2025
**Summary:** Anthropic launched the official MCP Registry as the canonical index for publishing and discovering MCP servers, modeled after npm/PyPI. The API entered a v0.1 freeze in October 2025 with a stability commitment. As of May 2026 the registry counts 9,652 latest server records and 28,959 total server/version records.

**Title:** Official MCP Registry
**URL:** https://registry.modelcontextprotocol.io/
**Date:** Ongoing (live service)
**Summary:** The live official registry exposes a REST API implementing the MCP Registry OpenAPI specification donated to the Agentic AI Foundation. It is the authoritative discovery endpoint for MCP servers across the ecosystem.

**Title:** The 2026 MCP Roadmap
**URL:** https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/
**Date:** 2026
**Summary:** The official roadmap priorities for 2026 are transport scalability (stateless HTTP core), agent-to-agent communication, OAuth/OIDC-aligned authorization, MCP Apps (server-rendered UIs), and a Tasks extension for long-running work. Working Groups now drive the development timeline rather than fixed dates.

---

## Ecosystem Growth & Adoption

**Title:** MCP Adoption Statistics 2026: Model Context Protocol
**URL:** https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol
**Date:** 2026
**Summary:** MCP reached 97 million monthly SDK downloads by March 2026, up from ~2 million at launch in November 2024. The broader ecosystem spans PulseMCP (15,930+ servers), Smithery (~7,300), Composio (20,000+ tools), and the official registry (~2,000 curated entries).

**Title:** MCP Server Ecosystem Tracker: 56 Servers Cataloged 2026
**URL:** https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026
**Date:** 2026
**Summary:** A curated tracker of notable MCP servers across categories. Provides structured metadata on each server including capabilities, transport type, and registry listing status — useful as a reference layer on top of the raw registries.

**Title:** Everything your team needs to know about MCP in 2026
**URL:** https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026
**Date:** 2026
**Summary:** WorkOS published a comprehensive enterprise primer on MCP covering the registry landscape, auth patterns, and what teams need to implement MCP-compatible services. Notes that Anthropic, OpenAI, Google, Microsoft, GitHub, Vercel, VS Code, and Cursor all now have first-party MCP support or infrastructure.

---

## Enterprise & Third-Party Registries

**Title:** AWS Agent Registry for centralized agent discovery and governance now in Preview
**URL:** https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/
**Date:** April 2026
**Summary:** AWS launched the Agent Registry inside Amazon Bedrock AgentCore as a private governed catalog for agents, tools, MCP servers, and skills within an organization. It supports URL-based discovery that automatically retrieves tool schemas and capability descriptions from live MCP server endpoints, along with manual registration via console or API.

**Title:** Kong Introduces MCP Registry in Kong Konnect
**URL:** https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html
**Date:** 2025/2026
**Summary:** Kong added an MCP Registry to its Konnect API platform — an enterprise directory for registering, discovering, and governing MCP servers and AI-native tools. Targets teams needing auditable, policy-controlled access to agentic tooling at scale.

**Title:** Leveraging the MCP Registry in Kong Konnect for Dynamic Tool Discovery
**URL:** https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery
**Date:** 2026
**Summary:** Kong engineering blog details how their MCP Registry integration enables agents to perform dynamic tool discovery at runtime rather than hardcoding tool references. Covers governance features including access controls, usage auditing, and rate limiting per tool.

**Title:** Best MCP Registries in 2026: Compared for Developers and Enterprises
**URL:** https://www.truefoundry.com/blog/best-mcp-registries
**Date:** 2026
**Summary:** TrueFoundry compares the major registries — official MCP Registry, Smithery (7,000+ servers with hosted remote option), Glama (28,517 open-source servers), mcp.so (20,222 listed), and PulseMCP — with evaluation criteria for developer vs. enterprise use cases.

**Title:** Open-Source MCP Servers — 28,517 in the Glama Registry
**URL:** https://glama.ai/mcp/servers
**Date:** Ongoing (live service)
**Summary:** Glama hosts the largest open-source MCP server index with 28,517 entries as of late May 2026. Each entry includes capability metadata, transport type, and install instructions, making it a popular community discovery layer.

---

## Agent Tool Discovery (Technical)

**Title:** MCP Gateway & Registry (agentic-community/mcp-gateway-registry)
**URL:** https://github.com/agentic-community/mcp-gateway-registry
**Date:** 2025/2026
**Summary:** An open-source enterprise MCP gateway that centralizes AI tool access with OAuth/Keycloak/Entra authentication and supports natural language queries against the registry — agents can discover tools semantically rather than through hardcoded references. Designed to replace scattered local MCP server sprawl with a governed, auditable access layer.

**Title:** Solving the MCP Tool Discovery Problem: How AI Agents Find What They Need
**URL:** https://medium.com/@amiarora/solving-the-mcp-tool-discovery-problem-how-ai-agents-find-what-they-need-b828dbce2c30
**Date:** 2026
**Summary:** Surveys the emerging patterns for runtime tool discovery in agentic systems — including registry polling, capability negotiation, and embedding-based semantic matching. Frames the discovery problem as distinct from the server listing problem and proposes architectural patterns for agents that need to self-configure at runtime.

---

## Governance & Foundation

**Title:** MCP's biggest growing pains for production use will soon be solved
**URL:** https://thenewstack.io/model-context-protocol-roadmap-2026/
**Date:** 2026
**Summary:** The New Stack covers the 2026 roadmap's response to production pain points: lack of statelessness, weak authorization, and fragmented registries. Notes that in December 2025 Anthropic donated MCP to the Agentic AI Foundation under the Linux Foundation, with OpenAI, Google, Microsoft, AWS, Cloudflare, GitHub, and Bloomberg joining as co-founders or supporting members.

---

**Key takeaways:**
- The official MCP Registry (~9,600 servers) is now the canonical index, but community registries (Glama at 28k, mcp.so at 20k, Smithery at 7k) dwarf it in raw count.
- AWS and Kong both launched enterprise-grade governed registries in 2026, targeting teams needing policy controls over agentic tool access.
- The 2026 protocol roadmap focuses on stateless HTTP, OAuth-aligned auth, and a Tasks extension — all aimed at production-grade agent deployments.
- MCP governance moved to the Linux Foundation (Agentic AI Foundation) in December 2025 with broad industry co-sponsorship.

Sources:
- [Introducing the MCP Registry | Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/)
- [Official MCP Registry](https://registry.modelcontextprotocol.io/)
- [The 2026 MCP Roadmap | Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)
- [MCP Adoption Statistics 2026](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)
- [MCP Server Ecosystem Tracker 2026](https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026)
- [Everything your team needs to know about MCP in 2026 — WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026)
- [AWS Agent Registry in AgentCore Preview](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/)
- [Kong Introduces MCP Registry in Kong Konnect](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html)
- [Leveraging the MCP Registry in Kong Konnect for Dynamic Tool Discovery](https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery)
- [Best MCP Registries in 2026: Compared — TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries)
- [Open-Source MCP Servers — Glama](https://glama.ai/mcp/servers)
- [MCP Gateway & Registry — GitHub](https://github.com/agentic-community/mcp-gateway-registry)
- [Solving the MCP Tool Discovery Problem — Medium](https://medium.com/@amiarora/solving-the-mcp-tool-discovery-problem-how-ai-agents-find-what-they-need-b828dbce2c30)
- [MCP's biggest growing pains — The New Stack](https://thenewstack.io/model-context-protocol-roadmap-2026/)

result: Compiled 14 recent MCP registry/marketplace results (Sept 2025–May 2026) covering the official MCP Registry launch, AWS and Kong enterprise registries, community registries (Glama 28k, mcp.so 20k, Smithery 7k), the 2026 protocol roadmap, and the Linux Foundation governance transfer — each with title, URL, date, and 2-3 sentence summary.

WEB SEARCH RESULTS 3 (Agent Workflows):
Here are the findings across all three topic areas, filtered to exclude reddit/X/Twitter, with dates and summaries where available.

---

## Claude Code Custom Workflows and Automation

**1. Introducing Dynamic Workflows in Claude Code**
URL: https://claude.com/blog/introducing-dynamic-workflows-in-claude-code
Date: May 28, 2026
Claude now constructs orchestration at runtime rather than following a fixed sequence — it writes JavaScript scripts that spin up as many as 1,000 parallel subagents in a single session. The feature is in research preview on all paid plans (Pro, Max, Team, Enterprise) and is available across Anthropic API, Amazon Bedrock, Google Vertex AI, and Microsoft Foundry. A notable early example: Jarred Sumner used it to produce ~750,000 lines of Rust in 11 days while keeping 99.8% of an existing test suite green.

**2. Anthropic Releases Opus 4.8 with New Dynamic Workflow Tool (TechCrunch)**
URL: https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/
Date: May 28, 2026
TechCrunch's coverage of the Opus 4.8 + dynamic workflows dual launch, noting the orchestration plan moves out of the model's context window and into a generated script — making 500-agent runs feasible and costs more predictable. Effort controls and a cheaper fast mode were also included in the same release.

**3. Claude Code Routines: Cloud-Based Automation via Schedules, APIs, and GitHub Webhooks**
URL: https://www.claudeapi.com/en/blog/dev-guides/claude-code-routines-cloud-automation-2026/
Date: 2026 (no precise date in results)
Routines moves workflow execution to Anthropic's cloud: write a prompt, connect a repo, set a trigger (cron, API call, or GitHub webhook), and the task runs automatically without a local machine. Use cases include nightly CI-failure checks, weekly dependency audits, and daily open-PR reviews.

**4. Anthropic Ships Opus 4.8 with Dynamic Workflows (MarkTechPost)**
URL: https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/
Date: May 28, 2026
Detailed breakdown of the 1,000-subagent cap, per-plan activation requirements (Max/Team on by default; Enterprise admin-gated; Pro manual opt-in), and the token-cost implications of externalizing orchestration into scripts rather than context. Covers codebase-wide bug hunts, profiler-guided optimization, and security audits as primary use cases.

**5. Anthropic Launches Dynamic Workflows for Claude Code (TestingCatalog)**
URL: https://www.testingcatalog.com/anthropic-launches-dynamic-workflows-for-claude-code/
Date: ~May 28–29, 2026
Concise overview of the research-preview launch, covering how Claude decomposes tasks, assigns subtasks to parallel subagents, and verifies results before surfacing output to the user. Notes the feature is distinct from simple parallelism because of the runtime script-generation approach.

---

## Reusable Agent Capabilities and Components

**6. Agent Lifecycle Toolkit (ALTK): Reusable Middleware Components for Robust AI Agents (IBM Research / arXiv)**
URL: https://arxiv.org/abs/2603.15473 | IBM Research: https://research.ibm.com/publications/agent-lifecycle-toolkit-altk-reusable-middleware-components-for-robust-ai-agents
Date: March 2026 (arXiv), presented at ACM CAIS 2026
IBM Research introduces ALTK, an open-source Python library providing framework-agnostic middleware that hooks into six lifecycle stages of any agent pipeline (pre-LLM, post-LLM, pre-tool, post-tool, etc.). Each component targets a specific error mode and can be used independently or in combination. ALTK can be exposed as skills or MCP components within Claude's SDK, making it a concrete example of cross-platform reusable agent reliability infrastructure.

**7. AI Agent Skills Complete Guide 2026: Building Reusable Agent Capabilities (CalmOps)**
URL: https://calmops.com/ai/ai-agent-skills-complete-guide-2026/
Date: 2026
Comprehensive guide to the "agent skills" architectural pattern: modular, composable capabilities loaded on-demand that convert general-purpose agents into domain experts. Covers how skills differ from tools, how they are versioned and shared, and integration with MCP. Positioned as the emerging alternative to monolithic agent prompts.

**8. Agentic AI Frameworks: Top 10 Options in 2026 (Instaclustr)**
URL: https://www.instaclustr.com/education/agentic-ai/agentic-ai-frameworks-top-10-options-in-2026/
Date: 2026
Surveys the leading frameworks (LangChain, LlamaIndex, CrewAI, AutoGen, Semantic Kernel, and others) through the lens of component reusability — covering memory modules, planner/verifier role separation, and MCP integration as the key differentiating criteria for enterprise selection.

---

## AI Agent Plugin Ecosystems

**9. The 2026 MCP Roadmap (Model Context Protocol Blog)**
URL: https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/
Date: 2026
MCP's official roadmap prioritizes transport scalability, agent-to-agent communication, governance maturation, and enterprise readiness for the year. As of May 2026, the registry counts 9,652 distinct server records and reports over 97 million monthly SDK downloads. The roadmap introduces Spec Enhancement Proposals (SEPs) and formal Working Groups as the community governance structure.

**10. Goodbye Plugins: MCP Is Becoming the Universal Interface for AI (The New Stack)**
URL: https://thenewstack.io/goodbye-plugins-mcp-is-becoming-the-universal-interface-for-ai/
Date: 2026
Argues that MCP — donated to the Linux Foundation's Agentic AI Foundation in December 2025 by Anthropic, Block, and OpenAI — is displacing proprietary plugin formats. Describes MCP as "USB-C for AI": write a tool server once and any compliant client can call it. The upcoming v1 spec adds a stateless protocol core, an Extensions framework, Tasks, and authorization hardening.

**11. MCP Ecosystem in 2026: What the v1.27 Release Actually Tells Us (Context Studios)**
URL: https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us
Date: 2026
Post-release analysis of MCP v1.27, covering how the Extensions framework enables third-party plugin authors to add capabilities without forking the spec. Notes that 41% of surveyed software organizations are already running MCP servers in limited or broad production (Stacklok 2026 report), with Gartner predicting 40% of enterprise apps will embed task-specific agents by end of year.

**12. 120+ Agentic AI Tools Mapped Across 11 Categories (StackOne)**
URL: https://www.stackone.com/blog/ai-agent-tools-landscape-2026/
Date: 2026
Landscape map of the full agent tooling ecosystem as of Q1 2026, covering orchestration, memory, retrieval, evaluation, identity, and plugin/integration layers. Highlights Google's A2A (Agent-to-Agent) protocol, introduced April 2025, as a complement to MCP enabling cross-vendor agent delegation without shared code — a key piece of the emerging multi-platform plugin story.

**13. Google Cloud Next 2026: AI Agents, A2A Protocol, and Workspace Studio (The Next Web)**
URL: https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era
Date: 2026
Covers Google's full-stack agent bet at Cloud Next 2026, including Vertex AI Agent Builder updates, Workspace Studio for no-code agent composition, and the A2A protocol for cross-platform agent interoperability. Positions Google's approach as a direct counter to Anthropic/MCP and Microsoft/Semantic Kernel in the enterprise plugin-ecosystem market.

---

**Sources:**
- [Introducing dynamic workflows in Claude Code](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code)
- [Anthropic releases Opus 4.8 with new dynamic workflow tool | TechCrunch](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/)
- [Claude Code Routines: Cloud-Based Automation](https://www.claudeapi.com/en/blog/dev-guides/claude-code-routines-cloud-automation-2026/)
- [Anthropic Ships Claude Opus 4.8 Alongside Dynamic Workflows | MarkTechPost](https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/)
- [Anthropic launches dynamic workflows for Claude Code | TestingCatalog](https://www.testingcatalog.com/anthropic-launches-dynamic-workflows-for-claude-code/)
- [Agent Lifecycle Toolkit (ALTK) | arXiv](https://arxiv.org/abs/2603.15473)
- [ALTK | IBM Research](https://research.ibm.com/publications/agent-lifecycle-toolkit-altk-reusable-middleware-components-for-robust-ai-agents)
- [AI Agent Skills Complete Guide 2026 | CalmOps](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/)
- [Agentic AI Frameworks: Top 10 Options in 2026 | Instaclustr](https://www.instaclustr.com/education/agentic-ai/agentic-ai-frameworks-top-10-options-in-2026/)
- [The 2026 MCP Roadmap | Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)
- [Goodbye Plugins: MCP Is Becoming the Universal Interface for AI | The New Stack](https://thenewstack.io/goodbye-plugins-mcp-is-becoming-the-universal-interface-for-ai/)
- [MCP Ecosystem in 2026: v1.27 Release | Context Studios](https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us)
- [120+ Agentic AI Tools Mapped Across 11 Categories | StackOne](https://www.stackone.com/blog/ai-agent-tools-landscape-2026/)
- [Google Cloud Next 2026: AI Agents and A2A Protocol | The Next Web](https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era)

result: Compiled 13 recent (May 2026) results across Claude Code dynamic workflows, reusable agent middleware (ALTK/skills pattern), and the MCP/A2A plugin ecosystem — each with title, URL, date, and 2-3 sentence summary.

WEB SEARCH RESULTS 4 (Anthropic Updates):
Here are the results across all three topic areas, drawing on web search and fetched page content.

---

## Anthropic Claude Code — New Features (May 2026)

**Source: Code with Claude 2026 conference, May 7–8, 2026**

**1. Dreaming (Scheduled Agent Memory)**
- URL: https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features
- Date: May 8, 2026
- A background process that reviews agent sessions and memory stores between runs, extracts patterns, and curates memories so agents improve over time. Enables continuous learning without manual intervention across sessions.

**2. Outcomes (Quality Grading Agent)**
- URL: https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features
- Date: May 8, 2026
- An independent grading agent scores outputs against a developer-defined rubric. Testing showed an 8.4–10.1% improvement in document quality with no model changes — suggesting the gains come from structured checking, not model upgrades.

**3. Multi-Agent Orchestration**
- URL: https://www.infoq.com/news/2026/05/code-with-claude/
- Date: May 8, 2026
- A managed system where a lead agent delegates to parallel specialist sub-agents on a shared file system. Replaces custom orchestration code; full auditability is available via Claude Console.

**4. Dynamic Workflows**
- URL: https://code.claude.com/docs/en/whats-new
- Date: May 2026
- Claude writes a script that orchestrates dozens to hundreds of subagents in one run. Early adopters have used it for codebase-wide bug hunts, profiler-guided optimization audits, and security sweeps.

**5. Add-ins (Claude Inside Third-Party Apps)**
- URL: https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features
- Date: May 8, 2026
- Claude now operates directly inside productivity software such as Microsoft Word, accessing software-native context like templates and formatting conventions rather than connecting externally.

**6. Security Plugin**
- URL: https://cybersecuritynews.com/anthropic-updates-claude-code/
- Date: May 2026
- A real-time plugin monitors code edits, diffs, and commits and automatically flags dangerous patterns before they reach production. Ships as an opt-in plugin integrated into the Claude Code editor flow.

**7. Claude Finance (10 Pre-Built Agents)**
- URL: https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features
- Date: May 7, 2026
- A starter kit of ten agents covering financial workflows — pitch building, market research, month-end closing, etc. Each can be deployed as a managed agent or plugin, with cookbooks for customization.

---

## Model Context Protocol (MCP) — Latest Updates

**1. 2026 MCP Roadmap**
- URL: https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/
- Date: March 9, 2026
- Shifts from release-based planning to working-group governance. Four themes: transport scalability (stateless HTTP + `.well-known` discovery), agent communication (Tasks lifecycle — retry, expiry), governance maturation (contributor ladder, delegation), and enterprise readiness (audit trails, SSO, config portability).

**2. 2026-07-28 Release Candidate — Largest Spec Revision Since Launch**
- URL: https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/
- Date: announced ahead of July 28, 2026 (in the future relative to today, but already published as RC)
- Introduces a stateless protocol core, MCP Apps (server-rendered HTML UIs in sandboxed iframes), Tasks extension (async tool calls via task handles), authorization hardening aligned with OAuth/OIDC, and a formal deprecation policy. Ten-week validation window for Tier 1 SDK maintainers before the final spec ships.

**3. MCP Adoption Statistics 2026**
- URL: https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol
- A broad overview of how rapidly MCP has been adopted across enterprise and open-source tooling. Useful for trend context alongside the technical roadmap articles.

**4. MCP Production Growing Pains — The New Stack**
- URL: https://thenewstack.io/model-context-protocol-roadmap-2026/
- Covers the practical obstacles practitioners face deploying MCP at scale (stateful session management, horizontal scaling) and how the roadmap items directly address them.

---

## Agent Skill Sharing Platforms

**1. SkillsMP**
- URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 (covered here; SkillsMP is a standalone platform)
- Indexes 800,000+ skills scraped from GitHub with a minimal 2-star quality filter. Works as a large search-and-discovery layer aggregating skills for Claude Code, OpenAI Codex CLI, ChatGPT, and others — the closest thing to a universal skill registry today.

**2. Skills.sh**
- URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- Launched January 2026 with Vercel backing, positioned as "npm for skills." Offers one-command CLI installation and community submissions, though without formal quality review.

**3. Agensi**
- URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- Curated marketplace with an 8-point security scan on every submission and an 80/20 creator revenue split. Smaller catalog than SkillsMP but vetted, with curl-based one-command install.

**4. ClaudeSkills.info**
- URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- Free community-contributed marketplace with 658+ skills including official Anthropic entries. Good entry point for beginners; no paid tier, open submissions.

**5. Agent Skills — OpenAI Codex**
- URL: https://developers.openai.com/codex/skills
- OpenAI's own skills directory for Codex CLI agents. Relevant because the open SKILL.md standard (announced by Anthropic December 2025) means skills written for Claude Code can also run here and in 16+ other tools.

**6. JFrog on Secure Skill Management**
- URL: https://jfrog.com/blog/agent-skills-new-ai-packages/
- Not a marketplace, but an important governance piece: argues that agent skills need the same dependency-management and security scrutiny as software packages, and positions artifact registries as the right control plane for enterprise skill distribution.

---

Sources:
- [What's new - Claude Code Docs](https://code.claude.com/docs/en/whats-new)
- [Code with Claude 2026: 5 New Agent Features Anthropic Just Shipped | MindStudio](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features)
- [Anthropic's Code with Claude Announces Managed Agents, Proactive Workflows, Capability Curve - InfoQ](https://www.infoq.com/news/2026/05/code-with-claude/)
- [Anthropic Updates Claude Code With Security Plugin and Faster Performance](https://cybersecuritynews.com/anthropic-updates-claude-code/)
- [Live blog: Code w/ Claude 2026](https://simonwillison.net/2026/May/6/code-w-claude-2026/)
- [Notes from Code with Claude 2026 - Chris Ebert's Blog](https://chrisebert.net/notes-from-code-with-claude-2026/)
- [The 2026 MCP Roadmap | Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/)
- [The 2026-07-28 MCP Specification Release Candidate | Model Context Protocol Blog](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)
- [MCP's biggest growing pains for production use will soon be solved - The New Stack](https://thenewstack.io/model-context-protocol-roadmap-2026/)
- [MCP Adoption Statistics 2026](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)
- [Every AI Skill Marketplace and Directory (2026) - Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)
- [Top 5 Agent Skill Marketplaces - KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)
- [Agent Skills are the New Packages of AI - JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/)
- [Agent Skills – Codex | OpenAI Developers](https://developers.openai.com/codex/skills)

result: Compiled 15+ recent results (May 2026) covering Claude Code's 7 new features from Code with Claude 2026, MCP's stateless-core release candidate and 2026 roadmap, and 6 agent skill sharing platforms including SkillsMP, Skills.sh, Agensi, ClaudeSkills.info, and OpenAI Codex Skills.
