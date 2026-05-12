# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-12
**Query type:** GENERAL
**Sources:** X/Twitter, Web (grounding), WebSearch (supplementary)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 13 posts | 33 likes, 1 repost, 10 replies | Mostly Japanese-language Claude Code users; @ClaudeCodeLog changelog posts |
| Web | 12 pages | — | claudepluginhub.com, nimbalyst.com, venturecrane.com, GitHub, agensi.io |
| Web (supplementary) | 30+ pages | — | via WebSearch: morphllm.com, truefoundry.com, solobusinesshub.com, claudemarketplaces.com, dev.to, etc. |
| Reddit | 0 threads | — | HTTP 402 errors on all queries |
| YouTube | 0 videos | — | HTTP 402 errors |
| Hacker News | 0 stories | — | No results |
| GitHub | 0 repos | — | No GitHub token configured |
| TikTok | 0 videos | — | No results |
| Bluesky | 0 posts | — | No results |
| Polymarket | 0 markets | — | No results |

---

## Synthesized Findings

### 1. The Claude Code Plugin Architecture: Skills, Agents, Hooks, MCP Servers

Claude Code's extensibility model has matured into a four-layer stack, each serving a distinct role. **Skills** are lightweight Markdown-based instruction files (30–50 tokens at load time, full instructions load on-demand) that teach Claude repeatable workflows—slash commands that invoke domain expertise. **Agents/Subagents** are packaged prompt-and-tooling configurations that run as autonomous sub-processes; Claude spawns them with focused task scopes to reduce token overhead in the parent context. **Hooks** are deterministic shell commands wired to specific moments in the agent lifecycle (PreToolUse, PermissionRequest, etc.)—they enforce actions that *must* happen rather than *should* happen. **MCP servers** connect Claude to external systems—databases, APIs, browsers, home automation, communication platforms—via the open Model Context Protocol standard.

**Plugins** are the distribution unit that bundles all four components into an installable, shareable package. A plugin directory contains `.claude-plugin/`, `commands/`, `agents/`, `skills/`, `hooks/`, `.mcp.json`, and a `README.md`. The Anthropic official plugin marketplace is at `claude.ai/settings/plugins`; the wider community ecosystem on GitHub holds thousands more.

Key distinction per morphllm.com: "Skills are for guidance that *should* be followed. Hooks are for actions that *must* happen." A typical 5-MCP-server setup requires approximately 55,000 tokens before any conversation starts; skills cost just 30–50 tokens. Anthropic's Tool Search feature (deferred tool loading) reduces MCP overhead by ~85%.

Sources: [morphllm.com Skills vs MCP vs Plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [Anthropic plugin README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) · [Anthropic Skills docs](https://code.claude.com/docs/en/skills) · [Agent SDK Plugins docs](https://platform.claude.com/docs/en/agent-sdk/plugins) · [alexop.dev full stack explainer](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [youngleaders.tech taxonomy](https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins)

---

### 2. Ecosystem Scale: 4,200+ Skills, 770+ MCP Servers, 304,608 Total Components

The scale of the Claude Code extension ecosystem as of May 2026 is striking. claudepluginhub.com's directory catalogs **304,608 total components**: 178,848 skills (59%), 49,907 agents (16%), 33,537 plugins, and assorted hooks, commands, and MCP configs. claudemarketplaces.com reports 4,200+ skills, 770+ MCP servers, and tracks 2,500+ marketplace sources, attracting 140,000+ monthly visitors.

Top skills by install count on claudemarketplaces.com:
- **find-skills**: 1.1M+ installs (skill discovery tooling)
- **agent-browser**: 186.7K+ installs
- **caveman**: 48.3K+ installs (achieves 75% token reduction via surgical edits)

Notable GitHub repositories tracking the space:
- `rohitg00/awesome-claude-code-toolkit`: 135 agents, 35 curated skills (+400,000 via SkillKit), 42 commands, 176+ plugins, 20 hooks
- `jeremylongshore/claude-code-plugins-plus-skills`: 425 plugins, 2,810 skills, 200 agents; open-source marketplace at tonsofskills.com with `ccpi` CLI package manager
- `quemsah/awesome-claude-plugins`: automated adoption metrics tracker; 16,467 total repositories indexed as of May 11, 2026
- `ComposioHQ/awesome-claude-skills`: 1,000+ production-ready skills for Claude Code, Codex, Cursor, Gemini CLI

The Anthropic official plugin registry is at: `github.com/anthropics/claude-plugins-official` with `marketplace.json` as the canonical manifest.

Sources: [claudepluginhub.com agents guide](https://www.claudepluginhub.com/blog/claude-code-agents-examples-and-use-cases) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [awesome-claude-plugins (quemsah)](https://github.com/quemsah/awesome-claude-plugins) · [awesome-claude-plugins (ComposioHQ)](https://github.com/ComposioHQ/awesome-claude-plugins) · [awesome-claude-skills (ComposioHQ)](https://github.com/ComposioHQ/awesome-claude-skills) · [awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) · [claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json) · [claudepluginhub.com MCP guide](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code)

---

### 3. The Agent Skills Open Standard: Cross-Platform Convergence

Agent Skills originated with Anthropic's Claude in late 2025 and have rapidly become an industry-wide open standard. The format—just Markdown files plus optional scripts—proved simple enough that GitHub Copilot adopted it in December 2025 (generating 184,000+ community discussions), OpenAI integrated it across ChatGPT and Codex (with GPT-5.2-Codex optimized for agentic coding), and Vercel launched **skills.sh** in January 2026 as an "npm for Agent Skills," reaching 20,000+ installs across 16+ agents (Claude Code, Cursor, Copilot, Codex, etc.).

The standard operates in three stages:
1. **Discovery**: At agent startup, only skill names and descriptions load (~30-50 tokens per skill)
2. **Activation**: When a task matches, the full SKILL.md loads into context
3. **Execution**: The agent follows the instructions, optionally loading referenced files or running bundled scripts

Claude Code extends the base standard with invocation control (user-triggered vs. model-triggered vs. automatic), subagent execution, and dynamic context injection. VS Code Copilot stores project skills in `.github/skills/`; Claude Code uses `.claude/skills/` or bundles them in plugin packages.

The open standard `agentskills.io` tracks cross-platform compatibility. Solopreneurs using agent skills report 70–90% time savings on routine work.

Sources: [agentskills.io](https://agentskills.io/home) · [solobusinesshub.com skills boom](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/) · [VS Code agent skills docs](https://code.visualstudio.com/docs/copilot/customization/agent-skills) · [OpenAI Codex skills](https://developers.openai.com/codex/skills) · [Spring AI agent skills](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/) · [calmops.com skills guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) · [getaiperks.com Codex skills](https://www.getaiperks.com/en/articles/codex-skills) · [jeffbailey.us on agent skills](https://jeffbailey.us/blog/2026/01/24/what-are-agent-skills/) · [Anthropic agent skills API docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

---

### 4. MCP Server Ecosystem: Discovery Remains the Bottleneck

The MCP ecosystem has matured dramatically: Smithery alone hosts 7,000+ servers; MCP.so lists 19,000+ community-submitted servers; MCP Market catalogs 10,000+ across 23+ categories. Production-ready MCP servers exist for most common developer tooling categories. Infrastructure providers are embedding MCP support natively—Home Assistant (home automation), OpenBSP (WhatsApp as first-class feature), and Daytona (persistent cloud environments for agents) all ship with built-in MCP layers.

The discourse has shifted from "can agents access tools?" to "which MCP server should I use?"—signaling genuine adoption. But the bottleneck is now **discovery**: "There is no central registry with quality signals" (dev.to/sahil_kat). Developers must navigate GitHub searches, subreddits, and changelogs to find and evaluate servers.

**The registry landscape** is fragmented across tiers:
- **Official**: `registry.modelcontextprotocol.io` — backed by Anthropic, GitHub, PulseMCP, Microsoft; metadata-only, no hosting
- **Community discovery**: Smithery (7,000+), MCP.so (19,000+), Glama (community metaregistry), MCP Market (10,000+)
- **Enterprise governance**: TrueFoundry (VPC-native, RBAC, full audit logging, versioning), agentic-community/mcp-gateway-registry (OAuth, dynamic discovery, Keycloak/Entra integration), ServiceNow MCP Registry (governed enterprise catalog)

Key challenges beyond discovery: trust boundaries (tool responses operate on an honor system without cryptographic attestation), documentation inconsistency, and maintenance burden (unmaintained servers break when upstream APIs change). Knowledge base integrations (UpNote, niche tools) represent the largest unmet demand.

Sources: [dev.to MCP ecosystem 2026](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln) · [truefoundry MCP registries](https://www.truefoundry.com/blog/best-mcp-registries) · [codeongrass MCP ecosystem](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/) · [mcpmarket.com](https://mcpmarket.com/) · [mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) · [ServiceNow MCP Registry](https://store.servicenow.com/store/app/2d463d6787608354669040c8dabb3530) · [Azure SRE Agent plugin marketplace](https://learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace) · [yournextstore MCP for ecommerce](https://yournextstore.com/blog/mcp-servers-for-ecommerce) · [MCP.so](https://mcpmarket.com/)

---

### 5. Codex CLI Plugin Distribution: A Competing Model

Codex CLI v0.121 (released April 13, 2026) introduced a marketplace CLI with the `codex marketplace add` command, establishing a three-tier installation policy and an emerging agent identity model. This positions Codex as a genuinely distributable plugin ecosystem that parallels Claude Code's plugin system.

Per the Codex blog: "Skills are the authoring format for reusable workflows, with Plugins serving as the installable distribution unit for reusable skills and apps in Codex." This mirrors the Claude Code nomenclature almost exactly—suggesting the two ecosystems are converging toward a shared vocabulary even while maintaining separate distribution channels.

The agent identity model is notable: it gives plugins a trust identity, enabling governance policies across enterprise deployments—addressing a gap that community MCP registries have struggled with.

Sources: [Codex CLI v0.121 announcement](https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/)

---

### 6. Claude Code Feature Velocity: CLI Updates and New Capabilities

@ClaudeCodeLog tracks the official changelog. Claude Code CLI 2.1.116 (April 21, 2026) was a polish release: fixed Devanagari/Indic script column alignment in terminal, fixed Ctrl+- undo in Kitty keyboard protocol terminals (iTerm2, Ghostty, kitty, WezTerm, Windows Terminal), and fixed Cmd+Left/Right for line navigation. The focus on internationalization signals growing non-English user adoption.

On X, the emergent workflow pattern dominating discussion is the `/goal` skill: "Set the goal, walk away, come back to a finished task. Combined with Agent View, you can run 5 goals in parallel and just check results. This is how coding agents should work." (@LukaMagic1236, quoting @dani_avila7) — the move toward fire-and-forget async agent orchestration.

A Japanese-language thread (@ClaudeCode_love, 2026-05-12) advocates for HTML-over-Markdown output as Claude Code's sophistication grows: "長い計画書は読みにくい。仕様書は伝わりにくい"—long plan documents are hard to read in plain Markdown; HTML enables figures, color-coding, tabs, and buttons. The thread cites Anthropic team members as having internally advocated for this pattern.

A comparative framing (@kenn): "Claude Code: Widen / Codex: Tighten"—suggesting Claude Code's philosophy is to expand agent surface area while Codex prioritizes constraint and focus.

Sources: [ClaudeCodeLog changelog](https://x.com/ClaudeCodeLog/status/2046404260091273354) · [LukaMagic1236 /goal thread](https://x.com/LukaMagic1236/status/2054138144598139253) · [ClaudeCode_love HTML output](https://x.com/ClaudeCode_love/status/2054138026717282769) · [kenn comparison](https://x.com/kenn/status/2054138679409668560) · [Anthropic Claude Code docs reference](https://code.claude.com/docs/en/plugins-reference)

---

### 7. Production Patterns: Token Optimization, Multi-Agent Orchestration

The dominant production concern in agent skill design is **token efficiency**. The `caveman` plugin achieves 75% token reduction through "surgical edits and tightly-scoped delegation"—it spawns narrowly-scoped subagents rather than expanding the parent context. `everything-claude-code` orchestrates across five component types for multi-agent workflows spanning multiple languages.

The recommended production architecture (per community consensus and Anthropic docs):
- 2–3 essential MCP servers (not 5+, which costs ~55,000 tokens upfront)
- Use Anthropic's Tool Search to load MCP tools on-demand (85% token reduction)
- A few custom skills for domain workflows (30-50 tokens each)
- Plugins only for standardized team distribution

Design pattern for agents: narrow single-responsibility scopes; combine agents with commands, skills, hooks, and MCP servers; structured outputs for agent composition. The `gsd-build` pattern (spec-driven development with autonomous planning + execution phases) is gaining adoption.

Sources: [claudepluginhub.com agents guide](https://www.claudepluginhub.com/blog/claude-code-agents-examples-and-use-cases) · [morphllm.com extensions guide](https://www.morphllm.com/claude-code-extensions) · [producttalk.org Claude Code guide](https://www.producttalk.org/how-to-use-claude-code-features/) · [everything-claude-code](https://github.com/affaan-m/everything-claude-code) · [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) · [turbodocx.com best plugins](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) · [agensi.io plugins vs skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [claudefa.st MCP extensions](https://claudefa.st/blog/tools/mcp-extensions/best-addons)

---

## Cross-Source Patterns

**Pattern 1: Discovery is the universal bottleneck**
Appearing on: Web (dev.to, truefoundry.com, claudemarketplaces.com), X (implicit in /find-skills being the #1 installed skill at 1.1M+ installs)
"There is no central registry with quality signals" (dev.to). The most-installed skill in the ecosystem is literally called `find-skills`—the community has self-organized around a tooling gap in discovery. Every major registry article frames its primary value proposition as solving discoverability.

**Pattern 2: Token economics drive architecture decisions**
Appearing on: Web (morphllm.com, claudepluginhub.com, boringbot substack), X (caveman plugin mentions)
The gap between skills (30-50 tokens) and MCP (55,000 tokens for 5 servers) is reshaping plugin design. Lazy loading (Tool Search), surgical agents (caveman), and scoped delegation are production-grade responses to context window economics.

**Pattern 3: Cross-platform convergence on the open skills standard**
Appearing on: Web (agentskills.io, solobusinesshub.com, VS Code docs, OpenAI docs, Spring AI docs)
GitHub Copilot, OpenAI Codex, Vercel, Spring AI, and VS Code all adopted compatible skill formats within 6 months of each other (Dec 2025–May 2026). The terminology is stabilizing: "Skills" = authoring unit, "Plugins" = distribution unit.

**Pattern 4: Enterprise governance demand growing**
Appearing on: Web (truefoundry.com, agentic-community/mcp-gateway-registry, ServiceNow, Microsoft Azure SRE)
Community registries (Smithery, MCP.so) are adequate for experimentation; enterprises are building separate governance layers with RBAC, audit logs, OAuth, and versioning—signaling that MCP is moving from developer toy to production infrastructure.

**Pattern 5: Fire-and-forget async orchestration becoming the norm**
Appearing on: X (@LukaMagic1236, @ClaudeCode_love), Web (producttalk.org, boringbot)
The `/goal` skill pattern and Agent View (running 5 goals in parallel) represent a UX shift from synchronous babysitting to async agentic delegation. "This is how coding agents should work."

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @ClaudeCodeLog | Claude Code CLI 2.1.116 changelog: Fixes: Devanagari script alignment, Kitty keyboard protocol undo, Cmd+Left/Right line navigation | 25 | 1 | https://x.com/ClaudeCodeLog/status/2046404260091273354 |
| @ClaudeCode_love | 【本日19:30公開】HTML output strategy for Claude Code — Markdown is hitting its limits for complex deliverables | 4 | 0 | https://x.com/ClaudeCode_love/status/2054138026717282769 |
| @LukaMagic1236 | /goal is what Claude Code was missing. Set the goal, walk away, come back to a finished task. Run 5 goals in parallel with Agent View. | 1 | 0 | https://x.com/LukaMagic1236/status/2054138144598139253 |
| @kenn | Claude Code: Widen / Codex: Tighten | 1 | 0 | https://x.com/kenn/status/2054138679409668560 |
| @24shi_web | EvenG2からClaude Code、Codexが使える！！ | 1 | 0 | https://x.com/24shi_web/status/2054137583412842800 |
| @hana_diversity | Obsidian is free; Claude Code requires a paid plan | 1 | 0 | https://x.com/hana_diversity/status/2054137867128250493 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudepluginhub.com | https://www.claudepluginhub.com/blog/claude-code-agents-examples-and-use-cases | 304,608 total components; 178,848 skills; 49,907 agents; caveman 75% token reduction |
| claudepluginhub.com | https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code | MCP server guide: memory, automation, documentation plugins |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills 30-50 tokens vs MCP 55k tokens; Tool Search 85% reduction |
| morphllm.com | https://www.morphllm.com/claude-code-extensions | Claude Code extensions full guide |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces, 140k/mo visitors |
| dev.to/sahil_kat | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | MCP ecosystem state; discovery gap; no central registry |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | MCP registry comparison: Smithery 7k, MCP.so 19k, enterprise options |
| solobusinesshub.com | https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/ | Skills open standard history; 70-90% time savings; Vercel skills.sh 20k installs |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Claude Code plugins guide |
| agentskills.io | https://agentskills.io/home | Cross-platform agent skills standard |
| codex.danielvaughan.com | https://codex.danielvaughan.com/2026/04/13/codex-cli-v0121-marketplace-agent-identity-plugin-distribution/ | Codex CLI v0.121 marketplace CLI + agent identity |
| groundy.com | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Anthropic official plugin ecosystem explainer |
| codeongrass.com | https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/ | MCP ecosystem as AI agent integration layer |
| mcpmarket.com | https://mcpmarket.com/ | MCP server discovery marketplace |
| github.com/agentic-community | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway: OAuth, dynamic discovery, Keycloak/Entra |
| github.com/anthropics | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Official Claude Code plugin structure docs |
| github.com/anthropics | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Official plugin manifest |
| github.com/ComposioHQ | https://github.com/ComposioHQ/awesome-claude-plugins | Curated claude plugins list |
| github.com/ComposioHQ | https://github.com/ComposioHQ/awesome-claude-skills | 1,000+ production-ready skills |
| github.com/travisvn | https://github.com/travisvn/awesome-claude-skills | Curated Claude skills |
| github.com/Chat2AnyLLM | https://github.com/Chat2AnyLLM/awesome-claude-plugins | Curated marketplaces and plugins |
| github.com/hesreallyhim | https://github.com/hesreallyhim/awesome-claude-code | Skills, hooks, commands, agents, plugins curated list |
| github.com/rohitg00 | https://github.com/rohitg00/awesome-claude-code-toolkit | 135 agents, 35 skills, 42 commands, 176+ plugins, 20 hooks |
| github.com/jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; ccpi CLI |
| github.com/quemsah | https://github.com/quemsah/awesome-claude-plugins | 16,467 repos indexed; automated adoption metrics |
| github.com/affaan-m | https://github.com/affaan-m/everything-claude-code | Multi-component orchestration; skills, instincts, memory, security |
| awesome-skills.com | https://awesome-skills.com/ | Curated skills and plugins directory |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Claude Code full stack: MCP, skills, subagents, hooks |
| youngleaders.tech | https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins | Skills vs commands vs subagents vs plugins taxonomy |
| producttalk.org | https://www.producttalk.org/how-to-use-claude-code-features/ | How to use Claude Code slash commands, agents, skills, plugins |
| boringbot.substack.com | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Production multi-agent workflows with skills + subagents + hooks |
| agensi.io | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Plugins vs skills explained |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best skills, plugins, MCP servers roundup |
| spring.io | https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/ | Spring AI adopts agent skills standard |
| developers.openai.com | https://developers.openai.com/codex/skills | OpenAI Codex skills docs |
| calmops.com | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI agent skills complete guide |
| code.visualstudio.com | https://code.visualstudio.com/docs/copilot/customization/agent-skills | VS Code Copilot agent skills |
| jeffbailey.us | https://jeffbailey.us/blog/2026/01/24/what-are-agent-skills/ | What are agent skills explainer |
| getaiperks.com | https://www.getaiperks.com/en/articles/codex-skills | Codex skills guide |
| mightybot.ai | https://mightybot.ai/blog/coding-ai-agents-for-accelerating-engineering-workflows/ | AI coding agents 2026 ranked |
| analyticsvidhya.com | https://www.analyticsvidhya.com/blog/2026/03/ai-coding-assistants/ | Top AI coding assistants 2026 |
| learn.microsoft.com | https://learn.microsoft.com/en-us/azure/sre-agent/plugin-marketplace | Azure SRE Agent plugin marketplace |
| yournextstore.com | https://yournextstore.com/blog/mcp-servers-for-ecommerce | MCP servers for ecommerce |
| store.servicenow.com | https://store.servicenow.com/store/app/2d463d6787608354669040c8dabb3530 | ServiceNow MCP Registry |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers 2026 |
| code.claude.com | https://code.claude.com/docs/en/plugins-reference | Official Claude Code plugins reference |
| code.claude.com | https://code.claude.com/docs/en/skills | Official Claude Code skills docs |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Agent Skills API overview |
| platform.claude.com | https://platform.claude.com/docs/en/agent-sdk/plugins | Plugin SDK docs |

---

## Stats Block

```
├─ 🔵 X: 13 posts │ 33 likes │ 1 reposts
├─ 🟠 Reddit: 0 threads │ 0 upvotes │ 0 comments  (HTTP 402 errors)
├─ 🔴 YouTube: 0 videos │ 0 views  (HTTP 402 errors)
├─ 🟢 HN: 0 stories │ 0 points │ 0 comments
├─ 🟣 TikTok: 0 videos │ 0 views
├─ 🩷 Instagram: 0 reels │ 0 views
├─ 🦋 Bluesky: 0 posts │ 0 likes
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 12 pages (skill grounding) + 40+ pages (WebSearch supplementary)
└─ 🗣️ Top voices: @ClaudeCodeLog, @ClaudeCode_love, @kenn │ claudepluginhub.com, claudemarketplaces.com, morphllm.com
```

---

## Data Gaps

- **Reddit**: All queries returned HTTP 402 (Payment Required) — zero Reddit data. This is a significant gap as r/ClaudeAI, r/LocalLLaMA, and r/ChatGPTCoding are likely active on these topics.
- **YouTube**: HTTP 402 errors; zero video data. Tutorial content on MCP setup and plugin installation is presumably active on YouTube.
- **GitHub**: No GITHUB_TOKEN configured — zero repository data from the skill's native GitHub search. Supplementary WebSearch partially compensates.
- **HN**: No Hacker News results — unusual given MCP is a frequent HN topic; possible query length caused no-match.
- **X/Twitter signal concentration**: 13 posts with low engagement (33 total likes); 6 were Japanese-language Claude Code general usage posts unrelated to the core plugin/skills topic. Topical signal is thin.
- **Coverage estimate**: Web supplementary research is high quality (~90% coverage of public blog/news layer). Social signal layer (Reddit, YouTube, HN) is ~0% coverage due to API failures. Overall: ~45–50% of total possible source coverage.
- **Query length issue**: The full multi-topic query string was very long; the skill's planner noted it was using deterministic fallback rather than LLM planning, which likely degraded query quality for niche sub-topics (skill marketplaces, registries).

---

## Key Quotes

> "There is no central registry with quality signals." — dev.to/sahil_kat on the MCP ecosystem ([link](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln))

> "Skills are for guidance that *should* be followed. Hooks are for actions that *must* happen." — morphllm.com Skills vs MCP vs Plugins guide ([link](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "/goal is what Claude Code was missing. Before this you had to babysit every turn. Set the goal, walk away, come back to a finished task." — @LukaMagic1236 on X ([link](https://x.com/LukaMagic1236/status/2054138144598139253))

> "A typical five-server setup with 58 tools requires approximately 55,000 tokens before any conversation starts." — morphllm.com on MCP token cost ([link](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "Claude Code: Widen / Codex: Tighten" — @kenn on X ([link](https://x.com/kenn/status/2054138679409668560))

> "Community-based MCP registries are appropriate for experimentation but fall short for production environments requiring compliance, governance, and data residency controls." — truefoundry.com ([link](https://www.truefoundry.com/blog/best-mcp-registries))

> "Solopreneurs report 70-90% time savings on routine work" using agent skills — solobusinesshub.com ([link](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/))

> "caveman achieves 75% token reduction through surgical edits and tightly-scoped delegation" — claudepluginhub.com ([link](https://www.claudepluginhub.com/blog/claude-code-agents-examples-and-use-cases))
