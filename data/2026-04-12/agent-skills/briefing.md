# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-12
**Query type:** GENERAL
**Sources:** X/Twitter, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 16 posts | 457 likes, 88 reposts | 14 posts April 2026, 2 posts March 2026 |
| Web | 55 pages | — | 8 via research script + 47 supplementary WebSearch |

---

## Synthesized Findings

### 1. The Ecosystem Has Exploded — 54+ Tools, 2,500+ Marketplaces

The Claude Code extension ecosystem hit a scale milestone this week that's drawing attention across X. Two "Resource Bible" posts went viral in quick succession: @Suryanshti777's April 10 thread (250 likes, 51 reposts) and @PrakashS720's April 11 version (39 likes, 11 reposts) both catalogued 54 tools across agents, MCP servers, skills, and automation workflows — framing awareness of this stack as a competitive edge. The Chinese-language reply from @defi88888888 captured the practitioner view: "MCP servers → connect external data sources. Skills → one-word triggers for repeated workflows. Multiplexers (cmux/gmux) → multi-agent parallel development. This thread has a save/like ratio of 1.7x — it's genuinely useful."

By the numbers (per web sources): 2,400+ published skills, 2,500+ listed marketplaces, 10,000+ public MCP servers, and 8,600+ across all public registries (per skillsindex.dev and use-apify.com). The claude-code-plugins-plus-skills repo on GitHub tracks 340 plugins + 1,367 agent skills with a CCPI package manager. The Claudify project seeking listing in awesome-claude-code claims 1,727 skills, 9 agents, and 21 commands as a single installable bundle. The pace is fast enough that claudemarketplaces.com serves as a meta-directory for 2,500+ individual marketplaces.

Sources: X (@Suryanshti777 https://x.com/Suryanshti777/status/2042612597036593231, @PrakashS720 https://x.com/PrakashS720/status/2042894316687798676, @defi88888888 https://x.com/defi88888888/status/2042893902848627015), Web (https://claudemarketplaces.com/, https://skillsindex.dev/blog/complete-guide-mcp-servers-2026/, https://use-apify.com/blog/mcp-server-handbook-2026, https://github.com/jeremylongshore/claude-code-plugins-plus-skills, https://github.com/hesreallyhim/awesome-claude-code/issues/1089)

---

### 2. The Three-Tier Taxonomy Is Crystallizing: Skills vs MCP vs Plugins

The community has largely converged on a three-tier taxonomy, articulated cleanly by morphllm.com: **"A skill is a cheat sheet, a plugin is a toolkit, and an MCP server is a bridge to another application."** This framing — repeated across multiple independent guides published this cycle — explains why the distinction matters in practice:

- **Skills** are markdown files that teach Claude repeatable workflows, invocable as slash commands. "Think of skills like macros. Instead of pasting the same 200-word prompt every time you want a code review, you write a SKILL.md once, and call /review-component forever." (blakecrosley.com)
- **MCP Servers** connect Claude to external services at runtime. Best used when "the same external service appears across multiple tasks" — per @dirkkok: "I run X API and documentation lookup as MCP servers because both appear in both research and content tasks; the setup overhead amortises across sessions. If a service only shows up once, plain tool calls stay simpler."
- **Plugins** bundle skills + MCP configs + hooks into a single installable unit distributed through marketplaces.
- **Hooks** are shell scripts at lifecycle points (tool execution, session boundaries, compaction) — fully deterministic, no LLM involved.
- **Subagents** run isolated contexts and return summaries, used to delegate work that doesn't need the full conversation context.

@PrakashS720 framed the power-user view: "Most people use Claude Code like a chat. Power users use it like an operating system. Claude Code isn't just prompting — it's sessions, agents, skills, hooks, MCP servers, and workflows."

Sources: X (@PrakashS720 https://x.com/PrakashS720/status/2042598062846284251, @dirkkok https://x.com/dirkkok/status/2042941327847952772), Web (https://www.morphllm.com/claude-code-skills-mcp-plugins, https://blakecrosley.com/guides/claude-code, https://alexop.dev/posts/understanding-claude-code-full-stack/, https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff, https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k, https://www.morphllm.com/claude-code-extensions, https://code.claude.com/docs/en/plugins, https://code.claude.com/docs/en/skills, https://code.claude.com/docs/en/features-overview)

---

### 3. Marketplace Infrastructure: Discovery Is Still the Hard Part

Several community-built marketplaces launched or updated this cycle, each taking a different approach to the discovery problem:

- **claudemarketplaces.com** — Meta-directory of 2,500+ marketplaces, sorted by installs and GitHub stars. Largest aggregator.
- **AgentHub** (announced by @kranirudha, April 10) — "Open source community plugin marketplace for claude code. 299 plugins from 73 authors so far and growing... All browsable and installable with a single command. skills. agents. hooks. MCP servers. all in one place."
- **LobeHub Skills Marketplace** (lobehub.com/skills) — 75K users, cross-platform (Claude, Codex, and more). Positioned as a neutral skills layer across agent platforms.
- **claudepluginhub.com** — Community directory with trust signals: stars, install counts, author reputation.
- **buildwithclaude.com** — Official-adjacent plugin listing maintained by community.
- **Claude Code Marketplaces** updated April 9 to add category browsing (per @mertduzgun): "you can now browse skills, mcp servers, and plugins by what they actually do — frontend, backend, testing, seo, design, ai & agent building."
- **girofu/skill-fetch** (GitHub, 21 stars) — CLI tool that searches 9 skill registries simultaneously, scoring and paginating results with security labels. The multi-registry problem in one tool.
- **OpalServe** (announced by @adityaaidev, April 12) — "open-source control plane for engineering teams using AI coding tools. Lets your team share MCP servers, knowledge bases, and usage analytics across Claude Code, Cursor, Codex, and Windsurf."

The fragmentation problem is real: TrueFoundry's analysis (truefoundry.com) counted ~15 independent agent registries, "each with their own listing format. Some expose REST APIs, some use agents.txt files, a couple have MCP server endpoints. Querying across all of them in real time is its own engineering problem."

Sources: X (@mertduzgun https://x.com/mertduzgun/status/2042283912643154383, @kranirudha https://x.com/kranirudha/status/2042506431493214325, @adityaaidev https://x.com/adityaaidev/status/2043131436010738114), Web (https://claudemarketplaces.com/, https://lobehub.com/skills, https://www.claudepluginhub.com/, https://buildwithclaude.com/, https://github.com/girofu/skill-fetch, https://www.truefoundry.com/blog/best-mcp-registries, https://code.claude.com/docs/en/discover-plugins, https://www.aitmpl.com/plugins/)

---

### 4. Cross-Platform Portability: The Agent Skills Standard Emerges

The most structurally significant development this cycle is cross-platform portability. Multiple sources confirm that the **agentskills.io standard** has been adopted by both Claude Code and OpenAI Codex, creating a shared format for agent skills. "Plugins built to this standard can work across different agent platforms, reducing vendor lock-in and expanding the potential audience for plugin developers." (skillsindex.dev)

Evidence of this trend:
- **microsoft/skills** (GitHub) — Microsoft published a repository of "Skills, MCP servers, Custom Agents, Agents.md for SDKs to ground Coding Agents," treating skills as a cross-platform primitive.
- **ToolHive April 2026 update** (docs.stacklok.com) — "Reusable agent skills across CLI and Registry" — skills are now portable bundles deployable across CLI and registry contexts.
- **@Young_X_Keep** is curating "AI agent skills for vulnerability detection & security research. Skills, workflows, MCP servers & tooling — for Claude Code, OpenClaw, Codex, Cursor, Gemini CLI, and more." — treating skills as platform-agnostic from the start.
- **agentic-community/mcp-gateway-registry** (GitHub) — Enterprise MCP Gateway & Registry with OAuth authentication, dynamic tool discovery, and unified access for "both autonomous AI agents and AI coding assistants." Supports Keycloak/Entra integration.

LobeHub (75K users) is arguably the most visible cross-platform skills marketplace, supporting Claude, Codex, and other coding agents under one interface.

Sources: X (@Young_X_Keep https://x.com/Young_X_Keep/status/2042936423599194289), Web (https://docs.stacklok.com/toolhive/updates/2026/04/06/updates, https://github.com/microsoft/skills, https://github.com/agentic-community/mcp-gateway-registry, https://lobehub.com/skills, https://dev.to/blackgirlbytes/my-predictions-for-mcp-and-ai-assisted-coding-in-2026-16bm, https://skillsindex.dev/blog/complete-guide-mcp-servers-2026/, https://nevo.systems/blogs/nevo-journal/what-are-ai-agent-plugins, https://www.pulsemcp.com/servers/mrsimpson-agent-skills, https://www.pulsemcp.com/servers/skills-mcp-skills, https://mcpservers.org/agent-skills, https://mcpmarket.com/tools/skills/claude-code-extension-reference)

---

### 5. Security: The $10K Mistake Nobody Talks About

The most-engaged security post this cycle came from @alphabatcher (59 likes, 5 reposts, 21 replies — the highest reply count of any post this week): "Security settings most Claude Code users never touch: Enable sandbox / Block credential access / Block .env files separately / Disable outbound commands / Auto-approve safe commands / Disable auto-loading MCP servers / Update monthly. Most people ignore all of this and take losses of $10k in a single night."

The specific callout of "Disable auto-loading MCP servers" is notable — it suggests that the default behavior of auto-loading installed MCP servers is a real attack surface. Anthropic's own engineering post (anthropic.com/engineering/claude-code-sandboxing) documents OS-level isolation via Linux bubblewrap and macOS seatbelt, but the @alphabatcher thread implies most users never enable it.

TrueFoundry's MCP authentication guide (truefoundry.com) covers OAuth flows and token management for MCP servers. The claudefa.st sandbox guide provides step-by-step configuration. The GitHub feature request issue #41068 on the anthropics/claude-code repo proposes "Skill-Driven On-Demand MCP & Tool Loading" — essentially lazy-loading MCP servers only when a relevant skill triggers them, which would reduce the idle attack surface.

Sources: X (@alphabatcher https://x.com/alphabatcher/status/2042225554036793578), Web (https://www.anthropic.com/engineering/claude-code-sandboxing, https://claudefa.st/blog/guide/sandboxing-guide, https://www.truefoundry.com/blog/mcp-authentication-in-claude-code, https://github.com/anthropics/claude-code/issues/41068, https://code.claude.com/docs/en/settings, https://github.com/shanraisshan/claude-code-best-practice, https://www.thecaio.ai/blog/claude-code-settings-guide)

---

### 6. Notable Open-Source Collections

A cluster of GitHub repositories are serving as the de facto skill distribution layer while formal marketplaces mature:

- **hesreallyhim/awesome-claude-code** — Curated list of skills, hooks, slash-commands, agent orchestrators, applications, and plugins. Reached issue #1,000 on March 12, 2026. April 6 update added new resources.
- **jeremylongshore/claude-code-plugins-plus-skills** — 340 plugins + 1,367 agent skills with a CCPI package manager and interactive tutorials.
- **alirezarezvani/claude-skills** — 232+ skills spanning engineering, marketing, product, compliance, and C-level advisory use cases.
- **levnikolaevich/claude-code-skills** — Plugin suite with bundled MCP servers: hex-line (hash-verified editing), hex-graph (code knowledge graph), hex-ssh (remote SSH). Full Agile delivery lifecycle pipeline.
- **athola/claude-night-market** — 19 production-ready plugins covering git workflows, code review, spec-driven development, multi-LLM delegation.
- **quemsah/awesome-claude-plugins** — Automated plugin adoption metrics via n8n workflows.

The @iamsupersocks post (20 likes) revealed that Claude Code's own client-side architecture — "1,884 TypeScript/TSX files: the terminal interactive shell (based on a custom Ink fork)" — was reverse-engineered by Claude itself in March 2026. The anthropics/claude-code repo sits at 110K GitHub stars. The official marketplace.json lives at `anthropics/claude-code/.claude-plugin/marketplace.json`.

Sources: X (@iamsupersocks https://x.com/iamsupersocks/status/2038912628681048369, @Andrey__HQ https://x.com/Andrey__HQ/status/2036507034862883192), Web (https://github.com/hesreallyhim/awesome-claude-code, https://github.com/jeremylongshore/claude-code-plugins-plus-skills, https://github.com/alirezarezvani/claude-skills, https://github.com/levnikolaevich/claude-code-skills, https://github.com/athola/claude-night-market, https://github.com/quemsah/awesome-claude-plugins, https://github.com/wshobson/agents, https://github.com/anthropics/claude-code/blob/main/.claude-plugin/marketplace.json, https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4, https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review, https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers)

---

### 7. Best-in-Class MCP Servers (Practitioner Consensus)

The most-cited MCP servers across guides and directories this cycle: **Figma** (read designs, extract design tokens, generate code from Figma files), **Playwright** (browser automation, E2E testing, screenshot capture), **Vercel** (deploy, check logs, manage projects from Claude Code), **PostgreSQL** (query databases, inspect schemas, run migrations), and **GitHub** (create PRs, review issues, manage repos). claudefa.st's setup guide promises "6 lines of JSON to connect Claude Code to GitHub, databases, and external APIs — production-ready copy-paste configs included."

Sources: Web (https://claudefa.st/blog/tools, https://claudefa.st/blog/tools/mcp-extensions/best-addons, https://thepromptshelf.dev/blog/claude-code-mcp-setup-guide/, https://docs.bswen.com/blog/2026-03-22-claude-code-mcp-skills-setup, https://docs.bswen.com/blog/2026-04-09-subagents-skills-claude-code/, https://www.scriptbyai.com/claude-code-commands-cheat-sheet/, https://htdocs.dev/posts/how-to-use-claude-code/, https://dev.to/jangwook_kim_e31e7291ad98/claude-code-advanced-workflow-subagents-commands-multi-session-50hl, https://www.trensee.com/en/blog/explainer-claude-code-skills-fork-subagents-2026-03-31, https://releasebot.io/updates/anthropic/claude-code)

---

## Cross-Source Patterns

**1. "Resource Bible" curation format — high engagement signal**
Two near-identical "Resource Bible" posts appeared on X within 24 hours (April 10–11), together accumulating 289 likes and 62 reposts. Both pointed to the same set of 54 tools and directories. The format (numbered tools, color-coded sections) spread from @Suryanshti777 to @PrakashS720 and triggered a Chinese-language engagement thread from @defi88888888. Appeared on: X.

**2. "Operating system" metaphor for Claude Code**
The framing that Claude Code is an OS — not a chat tool — appeared independently on X (@PrakashS720) and across multiple web guides (blakecrosley.com, morphllm.com, alexop.dev). All converge on the same insight: skills are shell scripts, MCP servers are device drivers, hooks are cron jobs. Appeared on: X, Web.

**3. Security as an afterthought, with real financial consequences**
@alphabatcher's post warning about $10K losses from ignoring security settings was the highest-engagement reply-magnet of the cycle (21 replies). The specific risk flagged — "Disable auto-loading MCP servers" — is corroborated by Anthropic's own sandboxing engineering post and TrueFoundry's MCP authentication guide. Appeared on: X, Web.

**4. Skills = macros / MCP = bridges — stable taxonomy across all sources**
This distinction is now articulated nearly identically across DEV.to, Medium, alexop.dev, morphllm.com, official docs, and X threads. No significant disagreement was found. The taxonomy has hardened into conventional wisdom. Appeared on: X, Web.

**5. Cross-platform portability emerging as a strategic priority**
Multiple signals point to a push for skills that work across Claude Code, Codex, Gemini CLI, and Cursor — from @Young_X_Keep's cross-platform skill curation to Microsoft/skills to ToolHive's CLI/registry portability to LobeHub's multi-platform marketplace. Appeared on: X, Web.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Suryanshti777 | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack. That's your edge." | 250 | 51 | https://x.com/Suryanshti777/status/2042612597036593231 |
| @alphabatcher | "Security settings most Claude Code users never touch: Enable sandbox, Block credential access, Disable auto-loading MCP servers... Most people ignore all of this and take losses of $10k in a single night" | 59 | 5 | https://x.com/alphabatcher/status/2042225554036793578 |
| @PrakashS720 | "Most people use Claude Code like a chat. Power users use it like an operating system. This cheatsheet is basically the difference." | 23 | 12 | https://x.com/PrakashS720/status/2042598062846284251 |
| @PrakashS720 | "Claude Code Resource Bible (Curated) 54 tools • Agents • MCP servers • Skills • Automation" | 39 | 11 | https://x.com/PrakashS720/status/2042894316687798676 |
| @iamsupersocks | "Claude Code reverse-engineered par Claude lui-même. Quelle époque. 1884 TypeScript/TSX files..." | 20 | 3 | https://x.com/iamsupersocks/status/2038912628681048369 |
| @Andrey__HQ | "Thank you Claude for an incredible run in 2026: Agent teams, Skills & Plugins, /loop, 1M context, Subagents..." | 18 | 1 | https://x.com/Andrey__HQ/status/2036507034862883192 |
| @mertduzgun | "just added categories to claude code marketplaces — browse skills, mcp servers, and plugins by what they actually do" | 3 | 0 | https://x.com/mertduzgun/status/2042283912643154383 |
| @Young_X_Keep | "Curating AI agent skills for vulnerability detection & security research. For Claude Code, OpenClaw, Codex, Cursor, Gemini CLI, and more." | 3 | 0 | https://x.com/Young_X_Keep/status/2042936423599194289 |
| @dirkkok | "MCP makes sense when the same external service appears across multiple tasks... the setup overhead amortises across sessions." | 1 | 0 | https://x.com/dirkkok/status/2042941327847952772 |
| @adityaaidev | "I built OpalServe — open-source control plane for sharing MCP servers, knowledge bases, and usage analytics across Claude Code, Cursor, Codex, and Windsurf." | 1 | 0 | https://x.com/adityaaidev/status/2043131436010738114 |
| @sourabhkapure | "Agent skills, MCP servers in broader stack: claude-code, OpenClaw, Hermes Agent, perplexity/computer, Chinese models..." | 1 | 1 | https://x.com/sourabhkapure/status/2042571185335275889 |
| @kranirudha | "Meet AgentHub — open source community plugin marketplace for claude code. 299 plugins from 73 authors." | 0 | 0 | https://x.com/kranirudha/status/2042506431493214325 |
| @BalvinderKalon | "the plugins ecosystem is where claude code starts pulling away from other ai coding tools. once your workflow has custom mcp servers wired in, going back to vanilla autocomplete feels painful." | 0 | 0 | https://x.com/BalvinderKalon/status/2042804952972558835 |
| @defi88888888 | "Claude Code ecosystem: 54 tools. MCP servers → connect external data. Skills → one-word workflow triggers. Multiplexers → multi-agent parallel development." | 0 | 0 | https://x.com/defi88888888/status/2042893902848627015 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Meta-directory of 2,500+ Claude Code marketplaces, sorted by installs and stars |
| LobeHub | https://lobehub.com/skills | Cross-platform Agent Skills Marketplace, 75K users |
| claudefa.st | https://claudefa.st/blog/tools | MCP Setup Guide: 6 lines of JSON, Code Kit v5.0 |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP Servers for Claude Code 2026 |
| claudefa.st | https://claudefa.st/blog/guide/sandboxing-guide | Claude Code Sandbox Guide: Setup, Config & Security 2026 |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Canonical taxonomy: skill = cheat sheet, plugin = toolkit, MCP = bridge |
| morphllm.com | https://www.morphllm.com/claude-code-extensions | MCP, Skills, Agents & Hooks Guide 2026 |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full-stack Claude Code architecture explained |
| muneebsa.medium.com | https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff | Extensions explained: Skills, MCP, Hooks, Subagents, Agent Teams & Plugins (March 2026) |
| blakecrosley.com | https://blakecrosley.com/guides/claude-code | CLI Guide & Reference 2026 — Hooks, MCP, Subagents |
| dev.to (raxxostudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best Claude Code Skills & Plugins (2026 Guide) |
| dev.to (williamwangai) | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP Servers — What to Use, How to Install 2026 |
| dev.to (blackgirlbytes) | https://dev.to/blackgirlbytes/my-predictions-for-mcp-and-ai-assisted-coding-in-2026-16bm | Predictions for MCP and AI-Assisted Coding 2026 |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Claude Code Plugins, Skills & MCP Servers 2026 |
| buildtolaunch.substack.com | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | 10 Tested, 4 Worth Keeping — honest plugin ratings |
| claudepluginhub.com | https://www.claudepluginhub.com/ | Community directory with trust signals |
| buildwithclaude.com | https://buildwithclaude.com/ | Build with Claude Plugin Marketplace |
| aitmpl.com | https://www.aitmpl.com/plugins/ | Claude Code Plugins & Marketplaces aggregator |
| skillsindex.dev | https://skillsindex.dev/blog/complete-guide-mcp-servers-2026/ | Complete Guide to MCP Servers 2026; 4,133 indexed, 8,600+ total |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP Registries 2026: 15 registries compared |
| truefoundry.com | https://www.truefoundry.com/blog/mcp-authentication-in-claude-code | MCP Authentication in Claude Code 2026 |
| use-apify.com | https://use-apify.com/blog/mcp-server-handbook-2026 | Complete MCP Server Handbook April 2026; 10,000+ public servers |
| pulsemcp.com | https://www.pulsemcp.com/servers/mrsimpson-agent-skills | Agent Skills MCP Server on PulseMCP |
| pulsemcp.com | https://www.pulsemcp.com/servers/skills-mcp-skills | Skills MCP Server on PulseMCP |
| mcpmarket.com | https://mcpmarket.com/tools/skills/claude-code-extension-reference | Claude Code Extension Reference on MCPmarket |
| mcpservers.org | https://mcpservers.org/agent-skills | Agent Skills Library on MCP Servers index |
| docs.stacklok.com | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | ToolHive April 2026: reusable agent skills across CLI and Registry |
| nevo.systems | https://nevo.systems/blogs/nevo-journal/what-are-ai-agent-plugins | What Are AI Agent Plugins? Complete Guide 2026 |
| anthropic.com | https://www.anthropic.com/engineering/claude-code-sandboxing | Claude Code Sandboxing — OS-level via bubblewrap/seatbelt |
| releasebot.io | https://releasebot.io/updates/anthropic/claude-code | Claude Code Release Notes April 2026 |
| thepromptshelf.dev | https://thepromptshelf.dev/blog/claude-code-mcp-setup-guide/ | Complete MCP Setup Guide for 2026 |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-commands-cheat-sheet/ | Claude Code Commands Cheat Sheet 2026 |
| thecaio.ai | https://www.thecaio.ai/blog/claude-code-settings-guide | How to Configure Claude Code Settings 2026 |
| htdocs.dev | https://htdocs.dev/posts/how-to-use-claude-code/ | How to use Claude Code — beginner guide |
| trensee.com | https://www.trensee.com/en/blog/explainer-claude-code-skills-fork-subagents-2026-03-31 | Claude Code Advanced Patterns: Skills, Fork, Subagents |
| docs.bswen.com | https://docs.bswen.com/blog/2026-03-22-claude-code-mcp-skills-setup | How to Make Claude Code Work Better With Skills and MCP Servers |
| docs.bswen.com | https://docs.bswen.com/blog/2026-04-09-subagents-skills-claude-code/ | How to Use Subagents and Skills in Claude Code (April 9, 2026) |
| dev.to (jangwook_kim) | https://dev.to/jangwook_kim_e31e7291ad98/claude-code-advanced-workflow-subagents-commands-multi-session-50hl | Advanced Workflow: Subagents, Commands & Multi-Session |
| code.claude.com | https://code.claude.com/docs/en/plugins | Official: Create plugins |
| code.claude.com | https://code.claude.com/docs/en/discover-plugins | Official: Discover and install prebuilt plugins |
| code.claude.com | https://code.claude.com/docs/en/skills | Official: Extend Claude with skills |
| code.claude.com | https://code.claude.com/docs/en/features-overview | Official: Extend Claude Code overview |
| code.claude.com | https://code.claude.com/docs/en/settings | Official: Claude Code settings |
| github.com | https://github.com/anthropics/claude-code/issues/41068 | FEATURE: Skill-Driven On-Demand MCP & Tool Loading (issue #41068) |
| github.com | https://github.com/anthropics/claude-code/blob/main/.claude-plugin/marketplace.json | Official built-in marketplace.json |
| github.com | https://github.com/hesreallyhim/awesome-claude-code | awesome-claude-code: skills, hooks, slash-commands, plugins |
| github.com | https://github.com/hesreallyhim/awesome-claude-code/issues/1089 | Issue #1089: Add Claudify (1,727 skills, 9 agents, 21 commands) |
| github.com | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 agent skills with CCPI package manager |
| github.com | https://github.com/levnikolaevich/claude-code-skills | Plugin suite + bundled MCP servers (hex-line, hex-graph, hex-ssh) |
| github.com | https://github.com/alirezarezvani/claude-skills | 232+ skills: engineering, marketing, product, compliance |
| github.com | https://github.com/wshobson/agents | Intelligent automation and multi-agent orchestration |
| github.com | https://github.com/quemsah/awesome-claude-plugins | Plugin adoption metrics via n8n workflows |
| github.com | https://github.com/athola/claude-night-market | 19 production-ready plugins: git, code review, multi-LLM delegation |
| github.com | https://github.com/microsoft/skills | Microsoft: Skills, MCP servers, Agents.md for coding agents |
| github.com | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway & Registry: OAuth, Keycloak/Entra |
| github.com | https://github.com/girofu/skill-fetch | skill-fetch: multi-registry skill discovery CLI |
| github.com | https://github.com/shanraisshan/claude-code-best-practice | Claude Code best practice settings |

---

## Stats Block

```
├─ 🔵 X: 16 posts │ 457 likes │ 88 reposts
├─ 🌐 Web: 55 pages — claudemarketplaces.com, morphllm.com, skillsindex.dev, claudefa.st, LobeHub, use-apify.com, truefoundry.com, GitHub
└─ 🗣️ Top voices: @Suryanshti777 (250 likes), @alphabatcher (59 likes), @PrakashS720 (62 likes combined) │ claudemarketplaces.com, lobehub.com
```

---

## Data Gaps

- **Reddit: 0 results** — All subreddit searches returned HTTP 403 (public JSON blocked) and HTTP 402 (payment required). This is a significant gap; r/ClaudeAI, r/MachineLearning, and r/LocalLLaMA are active communities for this topic.
- **YouTube: 0 results** — yt-dlp searches returned no results for all query variants; ScrapeCreators YouTube also returned HTTP 402 errors. YouTube likely has active tutorial content on skills/MCP setup that's missing from this briefing.
- **Hacker News: 0 results** — HN search returned no matching stories from the past 30 days. Possible that discussion is happening under different framings.
- **TikTok / Instagram / Bluesky / Polymarket: 0 results** — No configured sources or no relevant markets.
- **X concentration risk** — All social signal came from X. The 16 posts skew toward power users and tool builders; no consumer or beginner perspective is captured.
- **Coverage estimate: ~35%** — X + Web only. Missing Reddit (the highest-signal discussion platform for this topic), YouTube, and HN means the briefing over-indexes on announcement/promotional content vs. practitioner problem-solving discussions.

---

## Key Quotes

> "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack. That's your edge." — @Suryanshti777 on X ([link](https://x.com/Suryanshti777/status/2042612597036593231))

> "Most people use Claude Code like a chat. Power users use it like an operating system." — @PrakashS720 on X ([link](https://x.com/PrakashS720/status/2042598062846284251))

> "Most people ignore all of this and take losses of $10k in a single night." — @alphabatcher on X, on Claude Code security settings ([link](https://x.com/alphabatcher/status/2042225554036793578))

> "once your workflow has custom mcp servers wired in, going back to vanilla autocomplete feels painful." — @BalvinderKalon on X ([link](https://x.com/BalvinderKalon/status/2042804952972558835))

> "MCP makes sense when the same external service appears across multiple tasks... the setup overhead amortises across sessions. If a service only shows up once, plain tool calls stay simpler." — @dirkkok on X ([link](https://x.com/dirkkok/status/2042941327847952772))

> "A skill is a cheat sheet, a plugin is a toolkit, and an MCP server is a bridge to another application." — morphllm.com ([link](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "Claude Code disappointed me at first. I installed it, tried to use it, and got generic, often incorrect suggestions. After adding skills and MCP servers: night-and-day difference." — docs.bswen.com ([link](https://docs.bswen.com/blog/2026-03-22-claude-code-mcp-skills-setup))

> "Claude Code reverse-engineered par Claude lui-même. Quelle époque." — @iamsupersocks on X ([link](https://x.com/iamsupersocks/status/2038912628681048369))

> "There are now around 15 independent agent registries, each with their own listing format. Querying across all of them in real time is its own engineering problem." — truefoundry.com ([link](https://www.truefoundry.com/blog/best-mcp-registries))
