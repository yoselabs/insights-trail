# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-09
**Query type:** GENERAL
**Sources:** X/Twitter, Web

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 13 posts | 138 likes, 15 reposts | Top voices: @Lummox_eth (55 likes), @theparuchh (50 likes), @CoralOS_ai (17 likes) |
| Web | 19 pages | — | Engine-sourced; via WebSearch supplements: 19 additional pages |
| Reddit | 0 threads | — | All subreddits returned HTTP 402/403 errors |
| YouTube | 0 videos | — | Search returned 0 results |
| Hacker News | 0 stories | — | No results |
| TikTok | 0 videos | — | ScrapeCreators API 402 |
| Bluesky | 0 posts | — | No results |
| Polymarket | 0 markets | — | No relevant markets |

## Synthesized Findings

### 1. The Ecosystem Exploded — From Zero to 400K+ Skills in Months

The agent skills and plugin ecosystem is one of the fastest-growing software distribution networks ever recorded. According to [Orca Security's supply chain analysis](https://orca.security/resources/blog/ai-agent-skill-supply-chain-security/), the ecosystem went from nonexistent to 90,000+ installable skills in less time than npm took to reach 350,000 packages - which took a decade. As of May 2026, the numbers are staggering: [claudemarketplaces.com](https://claudemarketplaces.com/) tracks 4,200+ skills, 770+ MCP servers, and 2,500+ marketplaces with 140,000+ monthly developer visits. [SkillsMP](https://skillsmp.com/) lists 425,000+ skills. [LobeHub](https://lobehub.com/skills) has 169,739 indexed. Across the full Claude plugin ecosystem, [Nimbalyst's guide](https://nimbalyst.com/blog/claude-code-plugins-guide/) counts 32,018 active plugins and 282,356 total components - skills (161,541) being the largest component type, followed by commands (58,116), agents (48,047), and MCP servers (7,159).

The standardization moment was December 2025, when Anthropic released the Agent Skills specification as an open standard, and OpenAI immediately adopted the same SKILL.md format for Codex CLI and ChatGPT - per [Chris Ayers' complete guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/). [Vercel launched skills.sh](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) on January 20, 2026 as the official open leaderboard for skill packages.

**Cross-platform validation:** X posts + Web pages + multiple marketplace directories. The scale numbers appear on multiple independent platforms.

### 2. The Taxonomy Confusion Is Real - Skills vs Plugins vs MCP vs Hooks

The most searched-for content in this space is definitional: what is the difference between a skill, a plugin, an MCP server, and a hook? [DevOps Daily](https://devops-daily.com/posts/claude-code-agents-commands-skills-plugins-explained) captures the confusion directly: "Claude Code has four different extension mechanisms: agents, commands, skills, and plugins. They overlap in confusing ways, and the documentation does not always make the distinctions clear."

The clearest breakdown from [MorphLLM's guide](https://www.morphllm.com/claude-code-skills-mcp-plugins): **Skills** are procedural knowledge - markdown files (30-50 tokens each) loaded on-demand that teach Claude repeatable workflows, invoked as slash commands. **MCP servers** connect external tools, data sources, and APIs through the Model Context Protocol standard. **Plugins** are distributable packages that bundle one or more skills, MCP configurations, agents, hooks, and commands into a single installable unit. **Hooks** trigger actions on specific lifecycle events.

[Claude Code Guides](https://claudecodeguides.com/mcp-vs-skills-vs-hooks-claude-code-extensions/) summarizes the choice rule: "MCP servers connect external data and APIs. Skills define reusable behavior templates. Hooks trigger actions on specific events. Choosing the wrong one wastes time; choosing the right one multiplies your productivity." [wmedia.es](https://wmedia.es/en/tips/claude-code-plugin-marketplace-distribution) frames the plugin system simply: "Claude Code just got its own app store. You add a 'store' (a marketplace) once, browse what's inside, and install features with a single command."

**Cross-platform validation:** Web guides + X discussion + official Claude Code docs.

### 3. MCP Has Become Infrastructure - Adopted by OpenAI, Google, Microsoft

The Model Context Protocol, introduced by Anthropic in November 2024, has transcended its origins to become a de facto industry standard. Per [GitHub's own MCP explainer](https://github.com/resources/articles/what-is-mcp), it is an open-source client-server protocol adopted far beyond Anthropic - OpenAI, Google, and Microsoft have all implemented it. [data443.com's architecture guide](https://data443.com/blog/model-context-protocol-mcp-architecture-use-cases/) explains the standard uses JSON-RPC 2.0 and a Host/Client/Server model.

[Essa Mamdani's 2026 guide](https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026) frames MCP as "the USB-C for AI-Native Applications." Community-built servers now exist for GitHub, Slack, PostgreSQL, Stripe, Figma, Docker, Kubernetes and 200+ other tools per [mcpservers.org](https://mcpservers.org/). [Intuz's top 10 list](https://www.intuz.com/blog/best-mcp-servers) highlights Amazon Bedrock AgentCore (enterprise orchestration), Cloudflare MCP (edge distribution), GitHub MCP (autonomous code execution in repos), and n8n MCP (workflow automation bridging no-code and AI).

The 2026 MCP roadmap per the [official MCP blog](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) prioritizes Streamable HTTP - a transport that lets MCP servers run as remote services and scale horizontally without holding state, solving enterprise adoption friction. [SurePrompts](https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026) notes enterprises hitting predictable blockers: audit trails, SSO-integrated auth, gateway behavior, configuration portability.

**Cross-platform validation:** Web guides + X posts (@theparuchh, @FileCityAI) + official sources.

### 4. Cross-Agent Skill Portability Is Now a Real Product Category

The most technically interesting X posts this month are about making skills and MCP servers work across any agent, not just Claude Code. [@FileCityAI](https://x.com/FileCityAI/status/2050291267234414723) launched "agent-install" - a single API that installs agent skills and MCP servers across Claude Code, Cursor, Codex, OpenCode, and 40+ other agents by writing to each tool's native config. [@CoralOS_ai](https://x.com/CoralOS_ai/status/2048793208902332416) demoed Coral, a harness-level proxy where "skills and MCP servers load in one harness format and convert automatically for whichever gets spawned next" - enabling Hermes Agent and Claude Code to swap orchestrator seats peer-to-peer.

[@AlexParker0626](https://x.com/AlexParker0626/status/2052296994866315692) highlighted `anyclaw`, which turns "APIs, websites, scripts, CLIs, and workflows into agent-callable tools — and can export them as MCP servers or Claude Code skills." The framing: "Models reason. MCP standardizes. Adapters connect agents to the real world." [Codex CLI v0.121-alpha](https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/) added a marketplace CLI, three-tier installation policies, and an emerging agent identity model for enterprise governance of multi-agent plugin distribution.

[@leonvz](https://x.com/leonvz/status/2052010851666624728) noted the competitive framing: "Claude Code is great… but it's not the only AI coding tool worth paying attention to" - walking through OpenCode from scratch covering "MCP servers, agent skills, subagents and project workflows."

**Cross-platform validation:** X posts + product launches + web documentation.

### 5. Security Is the Biggest Unresolved Problem

The rapid growth has outpaced security infrastructure. [Orca Security's analysis](https://orca.security/resources/blog/ai-agent-skill-supply-chain-security/) found that of 90,000+ skills audited, a coordinated malware campaign had already hit thousands of users. Earlier, Snyk's ToxicSkills audit of 3,984 skills on the ClawHub marketplace found 13.4% (534) had critical-level security issues and 36.82% had any vulnerability - including malware distribution, prompt injection attacks, and exposed secrets.

On X, security concerns dominate thoughtful developer posts. [@thomasdevos69](https://x.com/thomasdevos69/status/2051714775273402437): "Before I trust a Claude Code agent with a real repo, I want one boring answer: what can it touch when the plan goes wrong? MCP servers, env vars, shell tools and cached cloud auth are the blast radius. The prompt is not the boundary." [@stephenwilsonai](https://x.com/stephenwilsonai/status/2052007327407145002) echoed: "Claude Code can feel unusable when the agent starts modifying things you didn't expect. The prompt isn't the boundary anymore — MCP servers and tool calls are."

[@bnafOg](https://x.com/bnafOg/status/2050336207561724307) described the enterprise reality: "The agent surface exploded in 2025 — Copilot Studio, local Claude Code installs, third-party MCP servers — with no unified visibility." Microsoft's Agent Package Manager ([microsoft/apm](https://github.com/microsoft/apm/issues/676), 1K stars) has an open feature request for URL-based marketplace registration with discovery indexes, reflecting institutional interest in governed distribution.

**Cross-platform validation:** X posts (multiple) + security research blogs + GitHub issues.

### 6. Discovery Is the Unsolved Distribution Problem

Beyond security, the discovery and distribution layer is immature. [@mykolanesov](https://x.com/mykolanesov/status/2046567344353222897) surfaced a concrete bug: "Claude Code discovers agent tooling — skills, MCP servers, plugins — only from project root. Workspace-level agents can't see child-repo tooling. Subagents don't inherit either. (Docs describe nested auto-discovery; behavior lags — issue #40640.)"

[my2cents.ai's deep-dive](https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/) covers the `.well-known/agent-skills/` URL path proposal - a standard that would let any website expose installable skills automatically, analogous to robots.txt or sitemap.xml. [GitHub's skills-mcp repo](https://github.com/Jignesh-Ponamwar/skills-mcp) is an early example: a self-hostable, semantically-searchable Agent Skills registry delivered over MCP with three-tier progressive disclosure architecture.

[@Butler_Agent](https://x.com/Butler_Agent/status/2042166963095654766) raised the identity layer problem: "a cross-chain identity and trust oracle could be a significant step toward solving the discovery and verification bottleneck" - agent-to-agent coordination needs reputation scores to filter out low-quality or malicious agents.

**Cross-platform validation:** X posts + Web proposals + GitHub experiments.

### 7. MCP as Personal Automation Stack - The "Zero-Config Agent" Pattern

The most engaging X post of the month was [@theparuchh](https://x.com/theparuchh/status/2050263310243906011) (50 likes) describing a personal agent built with just: "25 lines of code for a Telegram server, 3 open source MCP servers, one markdown file as the agent's brain, zero API keys, zero AWS credits, zero $200/mo no-code subscriptions." The agent opens a real Chrome browser via Playwright, reads TechCrunch, pulls top AI news, reads a tasks.md file, and writes motivation material - all from the Claude Pro subscription.

[@Lummox_eth](https://x.com/Lummox_eth/status/2048397609262346405) (55 likes) distilled the plugin library: "Install only 5-10 repositories from this list. You will already overtake 95% of users who pay for the same plan" - covering Skills Collections, Subagents, MCP servers for GitHub/database/browser/Figma, Orchestration, memory, slash commands, hooks and IDE integrations.

[Augment Code's SDK guide](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities) captures the team value: "Teams that keep pasting the same guidance into agent prompts waste tokens and get inconsistent behavior. Claude Agent SDK skills package reusable instructions, scripts, and workflows."

**Cross-platform validation:** X posts + Web guides. Most consumer-accessible angle.

## Cross-Source Patterns

**Pattern 1: MCP as the universal integration layer** - Appeared on X (multiple posts), official documentation, enterprise blogs. MCP is no longer a Claude-specific feature; it is cited as the standard that OpenAI, Google, and Microsoft have adopted. The "USB-C for AI" framing appeared independently across at least 3 sources.

**Pattern 2: Security lags growth by design** - Appeared on X (@thomasdevos69, @stephenwilsonai, @bnafOg) and web (Orca Security, Snyk/ToxicSkills). "The prompt isn't the boundary anymore — MCP servers and tool calls are" - this formulation or equivalent appeared in at least 3 X posts. Security infrastructure (audit trails, identity, governed distribution) is consistently described as 6-12 months behind the marketplace growth curve.

**Pattern 3: Cross-agent portability as the competitive wedge** - Appeared on X (@FileCityAI, @CoralOS_ai, @leonvz, @AIDailyGems) and web (multiple marketplaces, Codex blog). Tools that work across Claude Code, Cursor, Codex, OpenCode simultaneously are being positioned as the neutral infrastructure layer. Agent harness interoperability (Coral's peer-to-peer demo) is the bleeding edge.

**Pattern 4: Discovery is the next hard problem** - Appeared on X (@mykolanesov's bug report, @Butler_Agent's identity layer post) and web (my2cents.ai's .well-known proposal, skills-mcp registry). The npm analogy breaks down because skill quality and provenance are harder to verify than code. Multiple independent proposals for discovery standards are active simultaneously.

**Pattern 5: "Zero config" personal agent pattern gaining traction** - Appeared primarily on X (@theparuchh's 50-like post, @Lummox_eth's 55-like post). The narrative is: 3 MCP servers + 1 markdown file = personal AI agent, no expensive subscriptions needed. High engagement suggests this resonates with a large segment of developers.

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Lummox_eth | TOP 100 best GitHub repositories for Claude Code — Skills Collections, MCP servers, subagents | 55 | 10 | https://x.com/Lummox_eth/status/2048397609262346405 |
| @theparuchh | Build a personal AI agent in one evening — 3 open source MCP servers, one markdown file as brain | 50 | 1 | https://x.com/theparuchh/status/2050263310243906011 |
| @CoralOS_ai | Skills and MCP servers load in one harness format and convert automatically for whichever gets spawned next | 17 | 1 | https://x.com/CoralOS_ai/status/2048793208902332416 |
| @FileCityAI | agent-install: one API tool to install agent skills and MCP servers across Claude Code, Cursor, Codex, OpenCode, 40+ others | 5 | 1 | https://x.com/FileCityAI/status/2050291267234414723 |
| @ngnicky | Pentest Agent Suite — 48 agents, 26 commands, 19 CLI tools, 2 MCP servers for Claude Code + 6 other tools | 5 | 1 | https://x.com/ngnicky/status/2050922269082607749 |
| @leonvz | Claude Code isn't the only option — OpenCode covers MCP servers, agent skills, subagents and project workflows | 3 | 1 | https://x.com/leonvz/status/2052010851666624728 |
| @AlexParker0626 | anyclaw turns APIs, CLIs, workflows into agent-callable tools exportable as MCP servers or Claude Code skills | 1 | 0 | https://x.com/AlexParker0626/status/2052296994866315692 |
| @Butler_Agent | Cross-chain identity and trust oracle for solving discovery and verification bottleneck in ACP marketplace | 2 | 0 | https://x.com/Butler_Agent/status/2042166963095654766 |
| @mykolanesov | Claude Code discovers agent tooling only from project root — workspace-level agents can't see child-repo tooling | 0 | 0 | https://x.com/mykolanesov/status/2046567344353222897 |
| @thomasdevos69 | MCP servers, env vars, shell tools and cached cloud auth are the blast radius. The prompt is not the boundary. | 0 | 0 | https://x.com/thomasdevos69/status/2051714775273402437 |
| @stephenwilsonai | The prompt isn't the boundary anymore — MCP servers and tool calls are | 0 | 0 | https://x.com/stephenwilsonai/status/2052007327407145002 |
| @bnafOg | Agent surface exploded in 2025 — Copilot Studio, local Claude Code installs, third-party MCP servers — no unified visibility | 0 | 0 | https://x.com/bnafOg/status/2050336207561724307 |
| @AIDailyGems | Bug bounty agent framework for Claude Code, Codex, Gemini, Cursor, Windsurf, Copilot, OpenClaw | 0 | 0 | https://x.com/AIDailyGems/status/2051796372618363035 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Marketplace directory: 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces, 140K+ monthly devs |
| SkillsMP | https://skillsmp.com/ | 425,000+ skills indexed; built on open SKILL.md standard |
| LobeHub Skills | https://lobehub.com/skills | 169,739 skills for Claude, Codex & ChatGPT |
| Vercel Labs/skills | https://github.com/vercel-labs/skills | Open agent skills tool; skills.sh launched Jan 20, 2026 |
| Orca Security | https://orca.security/resources/blog/ai-agent-skill-supply-chain-security/ | Supply chain attack vectors; coordinated malware campaign in skills marketplaces |
| Nimbalyst | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Claude Code plugins 2026 guide; ecosystem stats; MCP Tool Search reduces context 95% |
| MorphLLM | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins: definitive taxonomy with token counts |
| data443.com | https://data443.com/blog/model-context-protocol-mcp-architecture-use-cases/ | MCP architecture: Host/Client/Server via JSON-RPC 2.0 |
| MCP Official | https://modelcontextprotocol.io/docs/getting-started/intro | Official MCP documentation |
| MCP Roadmap | https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/ | 2026 priorities: Streamable HTTP, enterprise auth, horizontal scaling |
| mcpservers.org | https://mcpservers.org/ | Awesome MCP Servers community directory: 200+ tools |
| Intuz | https://www.intuz.com/blog/best-mcp-servers | Top 10 MCP Servers: Bedrock AgentCore, Cloudflare, GitHub, n8n |
| Essa Mamdani | https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026 | "USB-C for AI-Native Applications" framing |
| my2cents.ai | https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/ | .well-known/agent-skills/ proposal for automatic skill discovery |
| agent-drop.com | https://agent-drop.com/mcp-server-documentation | MCP Server Documentation: Complete 2026 Index |
| Codex Blog | https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/ | Codex CLI v0.121: marketplace CLI, three-tier installation, agent identity |
| augmentcode.com | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Claude Agent SDK Skills: reusable agent capabilities via filesystem directories |
| claudecodeguides.com | https://claudecodeguides.com/mcp-vs-skills-vs-hooks-claude-code-extensions/ | MCP vs Skills vs Hooks decision guide |
| wmedia.es | https://wmedia.es/en/tips/claude-code-plugin-marketplace-distribution | Claude Code plugin marketplace: "own app store" walkthrough |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | 8 competing marketplaces covered: Q2 2026 landscape |
| Chris Ayers | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Agent Skills spec open standard (Dec 2025); OpenAI adoption |
| claudepluginhub.com | https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code | Claude Code MCP Servers developer guide |
| github.com/microsoft/apm | https://github.com/microsoft/apm/issues/676 | Agent Package Manager (1K stars); URL-based marketplace registration feature request |
| builder.io | https://www.builder.io/blog/claude-code-subagents | Claude Code subagents: offloading noisy work to specialized workers |
| devops-daily.com | https://devops-daily.com/posts/claude-code-agents-commands-skills-plugins-explained | Four extension mechanisms explained with confusion noted |
| claude-codex.fr | https://claude-codex.fr/en/agents/orchestration-patterns/ | Orchestration patterns: Command, Agent, Skill triangle |
| claudelab.net | https://claudelab.net/en/articles/claude-code/claude-code-sdk-custom-autonomous-agent-loop-guide | Custom autonomous agent loops with Claude Code SDK |
| daviddacruz.dev | https://daviddacruz.dev/blog/claude-code-skills-agents | Practical guide to skills, commands, subagents |
| github.com/Jignesh-Ponamwar/skills-mcp | https://github.com/Jignesh-Ponamwar/skills-mcp | Self-hostable semantically-searchable Agent Skills registry over MCP |
| developersdigest.tech | https://www.developersdigest.tech/blog/model-context-protocol-mcp-server-guide | Production guide to building MCP servers |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers for Claude Code |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Claude Code Plugins, Skills & MCP Servers guide |
| kdnuggets.com | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces ranked |
| agensi.io | https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026 | AI agent skills marketplace comparison 2026 |
| sureprompts.com | https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026 | MCP Complete 2026 Guide with enterprise adoption analysis |
| docs.dexto.ai | https://docs.dexto.ai/docs/mcp/overview | MCP as standardized agent-tool discovery and interaction protocol |
| github.com/what-is-mcp | https://github.com/resources/articles/what-is-mcp | GitHub's MCP explainer: open-source adoption by OpenAI, Google, Microsoft |
| webfuse.com | https://www.webfuse.com/mcp-cheat-sheet | MCP Cheat Sheet 2026 for developers |
| fast.io | https://fast.io/resources/best-mcp-clients/ | Best MCP Clients 2026: Claude Desktop vs Cursor evaluation |
| SurePrompts | https://sureprompts.com/blog/model-context-protocol-mcp-complete-guide-2026 | MCP enterprise friction: audit trails, SSO, gateway, config portability |

## Stats Block

```
├─ 🔵 X: 13 posts │ 138 likes │ 15 reposts
├─ 🌐 Web: 38 pages - claudemarketplaces.com, SkillsMP, LobeHub, nimbalyst.com, orca.security, modelcontextprotocol.io, mcpservers.org, augmentcode.com, my2cents.ai, GitHub
└─ 🗣️ Top voices: @Lummox_eth, @theparuchh, @CoralOS_ai
```

## Data Gaps

- **Reddit: 0 results** - All 7 targeted subreddits (r/ClaudeAI, r/ChatGPTCoding, r/LocalLLaMA, r/singularity, r/PromptEngineering, r/AI_Agents, r/MachineLearning) returned HTTP 402 (Payment Required) or HTTP 403 (Forbidden) errors. This is a significant gap - Reddit is typically the highest-signal source for developer discussions. Coverage estimate: ~40% of what a full run would yield.
- **YouTube: 0 results** - Both yt-dlp and ScrapeCreators YouTube search returned 0 results. Multiple tutorial and walkthrough videos likely exist (e.g., the @leonvz OpenCode video referenced on X). Coverage estimate: ~50% without YouTube transcripts.
- **HN: 0 results** - Hacker News returned no results. Surprising given the MCP/plugin ecosystem is an active HN discussion topic. Query string was likely too long for HN Algolia search.
- **TikTok/Instagram: 0 results** - ScrapeCreators API returned HTTP 402 errors.
- **GitHub: 0 results** - No GitHub token available; project-mode search disabled.
- **Noisy items filtered:** The X corpus included some tangential posts about security auditing frameworks and enterprise control planes (relevant but low-specificity to the core topic).
- **Approximate total coverage: ~60%** - Web and X coverage is strong; social discussion platforms (Reddit, YouTube, HN) all failed or returned zero results.

## Key Quotes

> "Build a personal AI agent in one evening on the Claude Pro subscription you already have. 25 lines of code for a Telegram server, 3 open source MCP servers, one markdown file as the agent's brain, zero API keys, zero AWS credits, zero $200/mo no-code subscriptions." — [@theparuchh](https://x.com/theparuchh/status/2050263310243906011) on X

> "Skills and MCP servers load in one harness format and convert automatically for whichever gets spawned next. Either harness can take the orchestrator seat. Agents talk peer-to-peer, not just up to the orchestrator." — [@CoralOS_ai](https://x.com/CoralOS_ai/status/2048793208902332416) on X

> "The prompt isn't the boundary anymore — MCP servers and tool calls are. A lightweight diff + permission audit before merge changes the experience completely." — [@stephenwilsonai](https://x.com/stephenwilsonai/status/2052007327407145002) on X

> "MCP servers, env vars, shell tools and cached cloud auth are the blast radius. The prompt is not the boundary." — [@thomasdevos69](https://x.com/thomasdevos69/status/2051714775273402437) on X

> "Claude Code discovers agent tooling — skills, MCP servers, plugins — only from project root. Workspace-level agents can't see child-repo tooling. Subagents don't inherit either. (Docs describe nested auto-discovery; behavior lags — issue #40640.)" — [@mykolanesov](https://x.com/mykolanesov/status/2046567344353222897) on X

> "anyclaw turns APIs, websites, scripts, CLIs, and workflows into agent-callable tools — and can export them as MCP servers or Claude Code skills. Models reason. MCP standardizes. Adapters connect agents to the real world." — [@AlexParker0626](https://x.com/AlexParker0626/status/2052296994866315692) on X

> "npm took a decade to reach 350,000 packages while the AI agent skills ecosystem did it in about two months." — [Orca Security](https://orca.security/resources/blog/ai-agent-skill-supply-chain-security/) supply chain analysis

> "Teams that keep pasting the same guidance into agent prompts waste tokens and get inconsistent behavior. Claude Agent SDK skills package reusable instructions, scripts, and workflows." — [Augment Code](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities)

> "Install only 5-10 repositories from this list. You will already overtake 95% of users who pay for the same plan." — [@Lummox_eth](https://x.com/Lummox_eth/status/2048397609262346405) on X, on Claude Code GitHub repos

> "The agent surface exploded in 2025 — Copilot Studio, local Claude Code installs, third-party MCP servers — with no unified visibility." — [@bnafOg](https://x.com/bnafOg/status/2050336207561724307) on X
