# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-05
**Query type:** GENERAL
**Sources:** X/Twitter, Web (Claude Code Docs, GitHub, DevOps.com, MindStudio, MCP Blog, Linux Foundation, InfoQ, JetBrains, Microsoft, Google, Medium, DEV Community, Composio, Firecrawl, StackGen, UX Planet, Builder.io, AgentPatch, SkillsMP)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 3 posts | low (all below relevance 0.3) | Japanese-language posts; Reddit API unavailable (402) |
| Web | 47 pages | — | via WebSearch — primary data source this cycle |

---

## Synthesized Findings

### 1. The Claude Code Skill/Plugin Ecosystem Has Reached Scale

The Claude Code extensibility ecosystem matured rapidly through early 2026. As of this cycle, **2,300+ skills and 770+ MCP servers** are available across community registries. The architecture draws a clear three-layer distinction:

- **Skills** — filesystem-based markdown instruction files (SKILL.md) that teach Claude domain-specific behavior. They are model-invoked: Claude decides when to use them based on context, not explicit user commands.
- **Plugins** — packaged skills bundled with supporting scripts, config, and hooks; shareable across projects and teams.
- **MCP Servers** — running services that connect Claude to external tools (Figma, Playwright, Vercel, PostgreSQL, GitHub).

Official documentation lives at [code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins) and [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview). The [official Anthropic plugin README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) is the canonical reference.

Community registries include:
- **[claudemarketplaces.com](https://claudemarketplaces.com/)** — 150+ skills with ratings (March 2026)
- **[jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)** — 340 plugins + 1,367 agent skills with CCPI package manager
- **[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)** — 220+ skills spanning Claude Code, Codex, Gemini CLI, Cursor, and 8+ more coding agents
- **[ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins)** — curated list of commands, agents, hooks, MCP servers
- **[hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)** — skills, hooks, slash-commands, agent orchestrators
- **[quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins)** — automated adoption metrics tracker

A dedicated article by Nick Babich on UX Planet ([Top 7 Claude Code Plugins, March 2026](https://uxplanet.org/top-7-claude-code-plugins-2f97c2fbb1be)) highlights: Claude-Mem (long-term memory), Superpowers (structured lifecycle planning), Local-Review (parallel code reviews), and Plannotator (clearer planning). Composio covers [10 top plugins](https://composio.dev/content/top-claude-code-plugins) and [hosted MCP platforms](https://composio.dev/content/hosted-mcp-platforms). DEV Community hosts a [2026 guide to best skills & plugins](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4).

---

### 2. The CCPI Package Manager: npm-style Distribution for Claude Skills

The open-source [claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) repo introduced the **CCPI CLI** — a package manager for Claude Code skills analogous to npm or brew:

```
pnpm add -g @intentsolutionsio/ccpi
ccpi install devops-automation-pack
ccpi update
```

Skills use a **2026 Schema** frontmatter for validation and cross-agent compatibility. The same SKILL.md format is shared across:
- Claude Code: `~/.claude/skills/` (personal) or `.claude/skills/` (project)
- OpenAI Codex CLI: `~/.codex/skills/`
- ChatGPT (adopted in December 2025 after Anthropic released the spec as an open standard)

This interoperability is significant: a skill built for Claude works in Codex. **[SkillsMP.com](https://skillsmp.com/)** launched as a cross-platform marketplace explicitly covering Claude, Codex, and ChatGPT skills. A March 2026 [Medium post](https://medium.com/product-powerhouse/33-claude-skills-for-pms-are-now-in-the-claude-code-marketplace-heres-how-to-install-them-7968ab6bb1e1) highlighted 33 PM-specific skills now in the Claude Code marketplace — a signal that vertical-specific skill packs are proliferating beyond engineering use cases.

---

### 3. How Skill Discovery and Chaining Actually Work

Per [platform.claude.com agent skills docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) and the [Claude Code Handbook](https://nikiforovall.blog/claude-code-rules/fundamentals/agent-skills/):

- Claude **loads skill metadata at startup** and includes it in the system prompt (lightweight — minimal context overhead)
- Skills activate **silently** — you do not type `/skill-name`; Claude determines when context calls for a skill
- Skills are discovered automatically from the filesystem

For multi-step workflows, skills are **chained** via an orchestrator pattern (per [MindStudio's deep dive](https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows)):

> Orchestrator reads a shared state file → determines which skill runs next → invokes it → updates state with output → loops until workflow completes

Each skill writes structured output consumed by the next. This makes skills independently testable and composable — the [CodeSignal course on visualization skills](https://codesignal.com/learn/courses/customizing-claude-code-for-reusable-visualization-workflows/lessons/modular-visualization-skills) uses this pattern explicitly.

VS Code now also natively supports agent skills via [code.visualstudio.com/docs/copilot/customization/agent-skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills). A [first-principles deep dive](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/) and [fazm.ai workflow guide](https://fazm.ai/t/custom-claude-code-skills-workflow) cover custom skill construction from scratch.

DevOps.com's [coverage of agent skills](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/) characterizes the system as transforming "general-purpose agents into specialists" — domain expertise packaged and reusable.

---

### 4. MCP Becomes the Universal Tool Standard — Now Under Linux Foundation

**Model Context Protocol (MCP)** is the infrastructure layer underneath all of this. On **December 9, 2025**, Anthropic donated MCP to the **Linux Foundation's Agentic AI Foundation (AAIF)** ([official announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), [LF press release](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation)):

- Founding contributions: **Anthropic's MCP**, **Block's goose**, **OpenAI's AGENTS.md**
- AAIF Platinum members: **AWS, Anthropic, Block, Bloomberg, Cloudflare, Google, Microsoft, OpenAI**
- Goal: neutral, open foundation for agentic AI standards

Metrics as of early 2026 ([MCP Blog](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/), [GitHub Blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation)):
- **97 million monthly SDK downloads** (Python + TypeScript)
- **10,000 active servers**
- **75+ connectors in Claude alone**
- First-class support: ChatGPT, Claude, Cursor, Gemini, Microsoft Copilot, VS Code

Solo.io analyzed the implications in [Why the AAIF Changes Everything for MCP](https://www.solo.io/blog/aaif-announcement-agentgateway). OpenAI's statement on co-founding is at [openai.com/index/agentic-ai-foundation](https://openai.com/index/agentic-ai-foundation).

The **MCP Dev Summit North America 2026** (April 2-3, NYC) convened 95+ sessions from MCP co-founders, maintainers, and production users ([LF events schedule](https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/), [LF press](https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule), [Yahoo Finance](https://finance.yahoo.com/news/agentic-ai-foundation-unveils-140000965)).

Multiple MCP server directories have emerged: [mcpmarket.com](https://mcpmarket.com/), [agentpatch.ai](https://agentpatch.ai/blog/best-mcp-servers-2026/), [firecrawl.dev](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers), [builder.io](https://www.builder.io/blog/best-mcp-servers-2026), [stackgen.com](https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026), [dev.to top-15 list](https://dev.to/jangwook_kim_e31e7291ad98/top-15-mcp-servers-every-developer-should-install-in-2026-n1h), [bytebridge on MCP Gateways](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a), and [databar.ai for sales teams](https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026). Microsoft Learn covers [local MCP tools in the agent framework](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools).

---

### 5. Agent Registries, Governance, and Enterprise Adoption

The ecosystem is maturing past individual tools into infrastructure:

**JetBrains ACP Agent Registry** (January 2026, [blog.jetbrains.com](https://blog.jetbrains.com/ai/2026/01/acp-agent-registry/)): The Agent Client Protocol (ACP) Registry launched as a directory of AI coding agents integrated directly into JetBrains IDE v2025.3+ and Zed. Also surfaced in [DataSpell 2026.1 release](https://blog.jetbrains.com/dataspell/2026/03/dataspell-2026-1-ai-agents-ecosystem-export-notebooks-to-pdf-editor-improvements/).

**Pinterest MCP at Production Scale** (April 2026, [InfoQ](https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/)): Pinterest engineering deployed a full internal MCP ecosystem — production MCP servers, a **central registry**, and agent integrations across developer tools. Replaces ad hoc integrations with a standardized, secure substrate. This is one of the first documented production-scale internal agent registries.

**Microsoft Agent Governance Toolkit** (April 2, 2026, [Microsoft Open Source Blog](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit)): Open-source runtime security for AI agents — a signal that enterprise governance of plugin/skill ecosystems is now an active concern.

**Google ADK Integrations Ecosystem** ([Google Developers Blog](https://developers.googleblog.com/supercharge-your-ai-agents-adk-integrations-ecosystem/)): Google announced a new integrations ecosystem for the Agent Development Kit.

Agent discovery and governance is now a category: [arthur.ai covers enterprise solutions](https://www.arthur.ai/column/agent-discovery-governance-landscape); [aiagentsdirectory.com](https://aiagentsdirectory.com/landscape) maps the full March 2026 landscape; [stackone.com](https://www.stackone.com/blog/ai-agent-tools-landscape-2026/) catalogued 120+ agentic tools across 11 categories; [agentica.wiki](https://agentica.wiki/articles/agent-ecosystems) theorizes agent ecosystem design.

---

### 6. Japanese Developer Community: MCP Context Awareness on X

The only confirmed social signal this cycle came from Japanese developers on X (all April 5, 2026):

- **@deep_verdure** explained how MCP tools occupy Claude Code's context window differently from CLAUDE.md memory files, and noted that IDE integration automatically starts MCP servers and connects them — a practical friction point for heavy MCP users ([x.com/deep_verdure/status/2040693035969958326](https://x.com/deep_verdure/status/2040693035969958326))
- **@noworkig** noted subscribing to Claude Code Max ([x.com/noworkig/status/2040693071390847153](https://x.com/noworkig/status/2040693071390847153))
- **@riteshpatel1884** mentioned Claude Code in conversation ([x.com/riteshpatel1884/status/2040692886329831689](https://x.com/riteshpatel1884/status/2040692886329831689))

The MCP context window concern raised by @deep_verdure is a real design issue: MCP servers auto-connecting on IDE launch can silently consume context before a conversation begins, reducing effective workspace for code and chat.

---

## Cross-Source Patterns

**Pattern 1: Open standardization of skill/plugin formats is converging**
- Platforms: Web (multiple official docs, GitHub repos)
- Anthropic released SKILL.md as an open standard (Dec 2025), OpenAI adopted it for Codex and ChatGPT. The same format now works across Claude Code, Codex CLI, and ChatGPT. SkillsMP.com and the CCPI package manager capitalize on this cross-platform compatibility.

**Pattern 2: MCP is now the dominant tool-connectivity layer — not Anthropic-specific**
- Platforms: Web (Linux Foundation, GitHub Blog, Microsoft, Google, Pinterest, OpenAI, JetBrains)
- 97M monthly downloads, 10K servers, AAIF co-founded by all major AI players. Pinterest's production deployment, AWS's specialized servers, and Microsoft's MCP tool integration all confirm this is infrastructure, not a feature.

**Pattern 3: Skill/plugin discovery is being solved at the ecosystem level (not just per-agent)**
- Platforms: Web (claudemarketplaces.com, mcpmarket.com, skillsmp.com, agentpatch.ai, JetBrains ACP Registry, Arthur.ai governance)
- Multiple distinct registry types have emerged: community curated (claudemarketplaces.com), package manager (CCPI), cross-platform marketplace (skillsmp.com), IDE-integrated (JetBrains ACP), and enterprise governance (arthur.ai, Microsoft AGT).

**Pattern 4: MCP context window management is an emerging pain point**
- Platforms: X (Japanese developer @deep_verdure)
- Auto-connecting MCP servers on IDE launch silently consume context before any conversation begins. As MCP usage scales, context budgeting becomes a skill/plugin design concern.

**Pattern 5: Vertical skill packs are proliferating beyond engineering**
- Platforms: Web (Medium PM skills article, alirezarezvani multi-domain skills repo)
- PM-specific, marketing, compliance, C-level advisory skills are now in the marketplace. The skill ecosystem is expanding from developer tooling to business function domains.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @deep_verdure | MCP tools context in Claude Code IDE integration — auto-connect on IDE launch, CLAUDE.md memory context vs MCP context visualization | — | — | https://x.com/deep_verdure/status/2040693035969958326 |
| @noworkig | Subscribed to Claude Code Max | — | — | https://x.com/noworkig/status/2040693071390847153 |
| @riteshpatel1884 | Claude Code mention (@isha_singh06) | — | — | https://x.com/riteshpatel1884/status/2040692886329831689 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs (Anthropic) | https://code.claude.com/docs/en/plugins | Official plugin architecture: skills, agents, hooks, MCP |
| Claude Code Docs — Sub-agents | https://code.claude.com/docs/en/sub-agents | Custom subagent creation |
| Claude API Docs — Agent Skills | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Canonical agent skills spec |
| Anthropic News | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | MCP donation to Linux Foundation |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | MCP joins AAIF announcement |
| Linux Foundation | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | AAIF formation press release |
| PR Newswire | https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agentsmd-302636897.html | AAIF formation full release |
| OpenAI | https://openai.com/index/agentic-ai-foundation/ | OpenAI co-founds AAIF |
| GitHub Blog | https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation | Developer perspective on MCP → LF |
| LF Events — MCP Dev Summit | https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/ | MCP Dev Summit NA 2026 (Apr 2-3, NYC) |
| LF Press — MCP Dev Summit | https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule | Summit schedule press release |
| Yahoo Finance | https://finance.yahoo.com/news/agentic-ai-foundation-unveils-140000965 | Summit coverage |
| Solo.io | https://www.solo.io/blog/aaif-announcement-agentgateway | AAIF implications for MCP / AgentGateway |
| InfoQ | https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/ | Pinterest production MCP deployment |
| Microsoft Open Source Blog | https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit | Agent Governance Toolkit launch |
| Microsoft Learn | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Local MCP tools in agent framework |
| JetBrains AI Blog | https://blog.jetbrains.com/ai/2026/01/acp-agent-registry/ | ACP Agent Registry launch (Jan 2026) |
| JetBrains DataSpell | https://blog.jetbrains.com/dataspell/2026/03/dataspell-2026-1-ai-agents-ecosystem-export-notebooks-to-pdf-editor-improvements/ | AI agents ecosystem in DataSpell 2026.1 |
| Google Developers Blog | https://developers.googleblog.com/supercharge-your-ai-agents-adk-integrations-ecosystem/ | Google ADK integrations ecosystem |
| VS Code Docs | https://code.visualstudio.com/docs/copilot/customization/agent-skills | Agent skills in VS Code Copilot |
| Anthropic GitHub — plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Official plugin reference |
| github/jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 skills + CCPI |
| github/jeremylongshore (CONTRIBUTING) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/CONTRIBUTING.md | Contribution guide |
| github/alirezarezvani | https://github.com/alirezarezvani/claude-skills | 220+ multi-agent skills |
| github/ComposioHQ | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| github/quemsah | https://github.com/quemsah/awesome-claude-plugins | Adoption metrics tracker |
| github/hesreallyhim | https://github.com/hesreallyhim/awesome-claude-code | Skills, hooks, orchestrators |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community marketplace — 150+ skills |
| skillsmp.com | https://skillsmp.com/ | Cross-platform skills marketplace (Claude, Codex, ChatGPT) |
| mcpmarket.com | https://mcpmarket.com/ | MCP server/client directory |
| DevOps.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | Agent skills for custom workflows |
| MindStudio | https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows | Skill chaining into end-to-end workflows |
| Lee Hanchung (blog) | https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/ | First-principles deep dive on Claude skills |
| Claude Code Handbook | https://nikiforovall.blog/claude-code-rules/fundamentals/agent-skills/ | Use custom agent skills guide |
| fazm.ai | https://fazm.ai/t/custom-claude-code-skills-workflow | Building custom skills from one-shot to reliable |
| CodeSignal | https://codesignal.com/learn/courses/customizing-claude-code-for-reusable-visualization-workflows/lessons/modular-visualization-skills | Packaging visualization expertise into skills |
| Composio — top plugins | https://composio.dev/content/top-claude-code-plugins | 10 top Claude Code plugins 2026 |
| Composio — hosted MCP | https://composio.dev/content/hosted-mcp-platforms | 4 best hosted MCP platforms |
| Builder.io | https://www.builder.io/blog/best-mcp-servers-2026 | Best MCP servers for developers |
| AgentPatch | https://agentpatch.ai/blog/best-mcp-servers-2026/ | Best MCP servers 2026 |
| DEV Community — MCP servers | https://dev.to/jangwook_kim_e31e7291ad98/top-15-mcp-servers-every-developer-should-install-in-2026-n1h | Top 15 MCP servers |
| ByteBridge Medium | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | MCP Gateways top 10 |
| Firecrawl | https://www.firecrawl.dev/blog/best-mcp-servers-for-developers | 10 best MCP servers |
| StackGen | https://stackgen.com/blog/the-10-best-mcp-servers-for-platform-engineers-in-2026 | MCP servers for platform engineers |
| Databar.ai | https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 | MCP servers for sales teams |
| UX Planet | https://uxplanet.org/top-7-claude-code-plugins-2f97c2fbb1be | Top 7 Claude Code plugins (Nick Babich) |
| DEV Community — skills guide | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills & plugins 2026 guide |
| Medium — PM skills | https://medium.com/product-powerhouse/33-claude-skills-for-pms-are-now-in-the-claude-code-marketplace-heres-how-to-install-them-7968ab6bb1e1 | 33 PM skills in marketplace (March 2026) |
| StackOne | https://www.stackone.com/blog/ai-agent-tools-landscape-2026/ | 120+ agentic tools mapped |
| Arthur.ai | https://www.arthur.ai/column/agent-discovery-governance-landscape | Enterprise agent discovery & governance |
| AI Agents Directory | https://aiagentsdirectory.com/landscape | March 2026 landscape map |
| Agentica | https://agentica.wiki/articles/agent-ecosystems | Agent ecosystems theory |

---

## Stats Block

```
├─ 🔵 X: 3 posts │ — likes │ — reposts
├─ 🌐 Web: 47 pages — Claude Code Docs, Linux Foundation, GitHub, InfoQ, JetBrains, Microsoft, DevOps.com, MindStudio, MCP Blog, Composio, Builder.io, AgentPatch, SkillsMP, Firecrawl, StackGen, UX Planet, Medium
└─ 🗣️ Top voices: @deep_verdure (MCP context management) │ claudemarketplaces.com, skillsmp.com, mcpmarket.com
```

---

## Data Gaps

- **Reddit:** API returned HTTP 402 Payment Required — zero Reddit data this cycle. This is a significant gap given that developer subreddits (r/ClaudeAI, r/LocalLLaMA, r/MachineLearning) likely have active discussions about MCP and plugin workflows.
- **YouTube:** Script returned 0 videos — no transcripts available. Developer tutorial channels likely have relevant content not captured here.
- **TikTok / Instagram:** Not applicable for this developer-focused topic; no relevant content expected.
- **Hacker News:** Script returned 0 stories for the query — possible keyword mismatch or timing. MCP and Claude Code are regular HN topics; a direct HN search would likely surface threads.
- **X/Twitter:** All 3 posts scored below relevance threshold (0.3). The query was too broad; topic-specific searches (e.g., "MCP marketplace", "Claude Code skills") would yield higher-quality results.
- **Social signal quality:** The X posts captured are low-engagement Japanese-language posts — not representative of the English-language developer community on this topic.
- **Approximate coverage:** Web sources ~85% comprehensive; Social/community signal ~10% (near-zero). True community sentiment (Reddit, HN, X developer discourse) is missing this cycle.

---

## Key Quotes

> "Skills are reusable, filesystem-based resources that provide Claude with domain-specific expertise: workflows, context, and best practices that transform general-purpose agents into specialists." — [platform.claude.com](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

> "You do not type /skill-name to activate a Skill. Claude decides to use it based on what you are asking. This means Skills work silently in the background, bringing domain expertise into the conversation exactly when it is needed." — [Claude Code Handbook](https://nikiforovall.blog/claude-code-rules/fundamentals/agent-skills/)

> "MCP is the universal standard protocol for connecting AI models to tools, data and applications. In one year, MCP has become one of the fastest-growing and widely-adopted open-source projects in AI." — [MCP Blog](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/)

> "青：MCP tools ⇒MCPサーバで占有しているコンテキスト。⇒Claude CodeがIDE連携した際に、自動でMCPサーバが立ち上がって接続される場合がある。茶：Memory files ⇒CLAUDE.mdが占有しているコンテキスト。" [MCP tools take up context; IDE integration auto-starts MCP servers; CLAUDE.md occupies memory context] — @deep_verdure on X ([link](https://x.com/deep_verdure/status/2040693035969958326))

> "Pinterest engineering deployed a full internal MCP ecosystem — production MCP servers, a central registry, and agent integrations across developer tools, replacing ad hoc integrations with a standardized, secure, and scalable AI tool-calling substrate." — [InfoQ](https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/)

> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)

> "The MCP ecosystem is maturing, and the best approach in 2026 is to start with a marketplace like AgentPatch that bundles the most common tools, then add specialized servers for niche use cases." — [AgentPatch](https://agentpatch.ai/blog/best-mcp-servers-2026/)

> "Each skill in the chain is independently testable and reusable. Composability is the design goal." — [MindStudio](https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows)
