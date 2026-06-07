# Agent Skills & Claude Code Plugin Ecosystem — Daily Briefing
**Date:** 2026-06-07
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web (engine) + WebSearch supplements

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 8 threads | — | r/ClaudeCode, r/LovingOpenSourceAI, r/coolgithubprojects, r/mcp |
| X/Twitter | 7 posts | 65 likes, 6 reposts | @ClaudeCodeLog, @VivekIntel, @digitalbrain01 |
| Hacker News | 15 stories | 1,039 points, 498 comments | High-signal; "Daily Driver" post topped at 449 pts |
| Bluesky | 13 posts | 76 likes, 6 reposts | @carnage4life, @midu.dev, @papoo7 |
| Web | 7 pages | — | skills.2389.ai, claudskills.com, dev.to, ai-trove.com, GitHub, buildwithclaude.com |
| Web (supplements) | 10 pages | — | via WebSearch (blogs/news) |

---

## Synthesized Findings

### 1. Dynamic Workflows: The Biggest Claude Code Launch of the Month

Anthropic shipped Dynamic Workflows on May 28, 2026 in research preview, and it dominated the conversation - 200 points and 135 comments on HN ([HN](https://news.ycombinator.com/item?id=48311705)), and widespread coverage across Bluesky and developer blogs. Dynamic Workflows let Claude write and execute JavaScript orchestration scripts that fan work across up to 1,000 subagents running 16 in parallel, while your main session stays responsive. The real-world proof point: Jarred Sumner used them to port Bun from Zig to Rust - 750,000 lines of Rust, 11 days, 99.8% of the existing test suite passing ([Anthropic blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code), [Medium/ILLUMINATION](https://medium.com/illumination/claude-codes-dynamic-workflows-the-ai-agent-architecture-that-just-rewrote-750-000-lines-of-code-d605a1d9b6d4)). Workflows are available on Max, Team, and Enterprise plans across CLI, Desktop, VS Code, and also on Amazon Bedrock, Vertex AI, and Microsoft Foundry ([InfoQ](https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/)). Community plugins like claude-code-workflow-orchestration operate at the hook level inside the turn paradigm; Dynamic Workflows replace Claude as orchestrator entirely with a separate runtime.

### 2. Marketplace Explosion: From One Registry to Eight in Six Months

The skills and plugin marketplace ecosystem has grown from a single community registry in December 2025 to eight major marketplaces by Q2 2026, with 20,300+ skills, 2,500+ marketplaces, and 9,900+ MCP servers now listed ([claudemarketplaces.com](https://claudemarketplaces.com/)). Anthropic's official Claude Code plugin directory crossed 29,000 GitHub stars in under 7 months, per [@digitalbrain01](https://x.com/digitalbrain01/status/2062309821634715732). [@chenzeling4](https://x.com/chenzeling4/status/2059394913326993574) captured the shift: "The marketplace model means quality actually gets curated instead of every half-baked GitHub gist ending up in your .claude directory." Key platforms now include:

- **Official Anthropic marketplace** - 55+ curated plugins, baked into Claude Code; command: `/plugin marketplace add`
- **Skills.sh** (Vercel-backed, launched Jan 2026) - npm-style package manager for skills; `npx skills add`
- **Agensi** (agensi.io) - security-reviewed, paid skills; every skill scanned against 8-point checklist; creators earn 80% ([agensi.io](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide))
- **ClaudeSkills.info** - 658+ free community-contributed skills
- **BuildWithClaude** (buildwithclaude.com) - 515+ practical extensions across Claude.ai, Claude Code, and Claude API ([buildwithclaude.com](https://buildwithclaude.com/))
- **2389 Research** (skills.2389.ai) - open-source plugins and MCP servers; install via `/plugin marketplace add 2389-research/claude-plugins` ([skills.2389.ai](https://skills.2389.ai/))
- **CodeGuilds** (codeguilds.dev) - community registry for skills, agents, MCP servers; debuted on HN Jun 1, 2026 ([HN](https://codeguilds.dev))
- **MCP Market** (mcpmarket.com) - best integration between MCP servers and skills that use them

### 3. Cross-Agent Skill Portability Is the New Pain Point

The strongest Reddit signal this month was tooling built to solve drift: developers using Claude Code, Cursor, and Codex CLI across multiple machines were hand-copying MCP configs and skills every time they changed something. Two separate open-source projects launched to address this:

- **gaal** (r/coolgithubprojects, [Reddit](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/)) - a Go CLI that lets you declare one `gaal.yaml` and run `gaal sync` to write each agent's config in its own format across machines. "We got tired of the same chore: every time we added an MCP server or wrote a skill, we had to copy it into each agent's config, in each agent's format, on each machine. They drifted constantly."
- **Multi-machine sync tool** (r/AiBuilders, [Reddit](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/)) - specifically for keeping skills and MCP servers in sync; "the tax of copying [a skill] onto three machines, into Claude Code, then Cursor, then Codex" was the stated pain.

The Agent Skills format itself is increasingly cross-agent: GSAP (GreenSock Animation Platform) shipped official AI skills ([Reddit](https://www.reddit.com/r/LovingOpenSourceAI/comments/1tr29t6/official_ai_skills_for_gsap_greensock_animation/)) that work with "Claude Code, Codex, Windsurf, Copilot, 40+ agents." [@frankfor.you on Bluesky](https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n) put it clearly: "Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable."

### 4. Terminology Confusion Is Real and Widespread

The single most-upvoted question in [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) this month: "Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md in Claude Code?" The community's answer: **Skills** are markdown-based directories (a SKILL.md file with YAML frontmatter) that load contextually for specific tasks. **Plugins** are containers that bundle multiple skills, MCP servers, slash commands, and hooks into a distributable package. **MCP servers** are running processes that expose external tools and data sources. **Hooks** are shell commands that fire on lifecycle events (tool calls, session start/stop, etc). This taxonomy confusion is slowing onboarding - the [ai-trove.com explainer](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) by Paul Irolla (12+ years AI/ML) was widely linked. [@VivekIntel on X](https://x.com/VivekIntel/status/2058028999646028087) summarized: "Plugins are containers for distributing and organizing (possibly several) skills as part of a larger toolkit. Skills focus on providing specialized knowledge or procedures for tasks."

### 5. Anthropic Ships Official Agent Skills Course and First-Party Skills

On June 6, [@midu.dev on Bluesky](https://bsky.app/profile/midu.dev/post/3mnmpkxdqsu2i) flagged a new free Anthropic course on deeplearning.ai: "Agent Skills paso a paso y desde cero" (Agent Skills step by step from scratch) - 2 hours, 10 videos, covering skill creation, best practices, differences between Skills and MCP, and compatibility with Claude Code and VS Code. Separately, [SkillKit.io reported](https://skillkit.io/blog/what-changed-in-claude-skills-april-2026) that Anthropic quietly released three first-party skills under the anthropics/skills repository in April 2026, with vendors working toward a shared cross-platform Skills format targeted for May or June. The "Claude Code as a Daily Driver" guide covering CLAUDE.md, Skills, Subagents, Plugins, and MCPs earned 449 HN points and 254 comments ([arps18.github.io](https://arps18.github.io/posts/claude-code-mastery/)) - the highest-signal single item in the research window.

### 6. MCP Ecosystem: Enterprise Vendors Ship, Developers Experiment at Scale

Three enterprise vendors shipped official MCPs in a 21-day window in April: Shopify (April 9), Meta on April 29 ([Meta Ads AI Connectors, 29 tools](https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026)), and Higgsfield (April 30). The public MCP ecosystem now counts over 10,000 servers ([claudeskills.com directory](https://claudskills.com/learn/claude-code-mcp-servers/)). A Show HN post ([HN](https://github.com/openclaw-easy/ViralMint)) demonstrated giving an AI video generator 86 MCP tools so Claude Code can drive it. The r/mcp community is debating whether MCP servers should be able to bundle Agent Skills, so any MCP host loads both the tool server and the skill instructions simultaneously ([Reddit](https://www.reddit.com/r/mcp/comments/1tacsse/can_mcp_servers_bundle_agent_skills_so_any_mcp/)). A Claude Code CLI update (v2.1.153, [X/@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2059802891607589286)) fixed a regression where stateful MCP servers without SSE were reconnect-looping on `tools/list`. MCP Tool Search (lazy loading) now reduces context usage by up to 95%.

### 7. Community-Built Agent Harnesses and Registries Proliferating

Beyond the marketplaces, a wave of individual developer-built harnesses and tools appeared this month:

- **ECC (Everything Claude Code)** - drops a full agent harness into Claude Code, Codex, Cursor, and OpenCode with skills, memory, instincts, and security; MIT licensed; "your agent goes from autocomplete to self-improving operator" ([Bluesky](https://bsky.app/profile/epicvibecoder.bsky.social/post/3mnolsyre5f2k))
- **adamsreview** - better multi-agent PR reviews for Claude Code; 85 HN points, 55 comments ([GitHub](https://github.com/adamjgmiller/adamsreview))
- **Learning Opportunities** - a Claude Code and Codex skill for deliberate skill development; 253 HN points, 50 comments ([GitHub](https://github.com/DrCatHicks/learning-opportunities))
- **ktx** - executable context layer for data/analytics agents allowing Claude Code, Codex, and any agent to query data accurately through MCP with skills, memory, and a semantic layer ([Reddit](https://www.reddit.com/r/LovingOpenSourceAI/comments/1trwna2/ktx_ktx_is_an_executable_context_layer_for_data/))
- **awesome-claude-code** (hesreallyhim/awesome-claude-code, ~36.8K stars) - hand-curated "master index" of skills, hooks, slash commands, agent orchestrators, apps, and plugins ([Reddit/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/))
- **Agent FM** - local, open-source radio for Claude Code and Codex agents ([GitHub](https://github.com/agentfm-ai/agent-fm))

### 8. Skills as an Unlocking Mechanism for Model Capability

[@alexalbert__ framed skills](https://x.com/alexalbert__/status/1979577547575951616) as something deeper than tooling: "Skills are a glimpse into how much capability is already inside current models, just waiting to be unlocked by better prompts. Claude made these PDF visuals entirely through code using the canvas-design skill - I had no clue this was possible before." The [DEV Community article](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) showed the same pattern with the `frontend-design` skill: "I added it, asked Claude to build a landing page, and watched it ignore every default React-and-Tailwind cliché it usually reaches for." Skills aren't just configuration - they elicit qualitatively different behavior.

---

## Cross-Source Patterns

**Pattern 1: Cross-agent portability as the dominant pain point**
- Appeared on: Reddit (2 separate tool launches), Bluesky (@frankfor.you), Web (juftin/skills cross-platform agent directory)
- Key quote: "every time we added an MCP server or wrote a skill, we had to copy it into each agent's config, in each agent's format, on each machine. They drifted constantly." - r/coolgithubprojects ([link](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/))

**Pattern 2: Marketplace quality curation as differentiator**
- Appeared on: X (@chenzeling4, @VivekIntel), Web (agensi.io, groundy.com, composio.dev)
- Key quote: "The marketplace model means quality actually gets curated instead of every half-baked GitHub gist ending up in your .claude directory." - [@chenzeling4](https://x.com/chenzeling4/status/2059394913326993574)

**Pattern 3: Dynamic Workflows as architecture shift, not just a feature**
- Appeared on: HN (200 pts, 135 comments), Bluesky, Web (InfoQ, MarkTechPost, Medium, buildtolaunch.substack)
- Key quote: "Community plugins operate at the hook level and delegate to specialized subagents, staying within the turn-by-turn paradigm, while official Dynamic Workflows replace Claude as the orchestrator with a separate runtime." - [claudefa.st](https://claudefa.st/blog/guide/development/dynamic-workflows)

**Pattern 4: Terminology confusion slowing adoption**
- Appeared on: Reddit (r/ClaudeCode thread), X (@VivekIntel, @claude_code community), Web (ai-trove.com, dev.to)
- Key quote: "I keep seeing these terms thrown around in tutorials and videos, but I've never seen anyone give a concrete example that makes the difference actually click." - r/ClaudeCode ([link](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/))

**Pattern 5: Skills as model capability unlock, not just workflow shortcut**
- Appeared on: X (@alexalbert__), Web (dev.to, firecrawl.dev, groundy.com)
- Key quote: "Skills are a glimpse into how much capability is already inside current models, just waiting to be unlocked by better prompts." - [@alexalbert__](https://x.com/alexalbert__/status/1979577547575951616)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md? | — | — | "I've never seen anyone give a concrete example that makes the difference actually click" | [link](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) |
| r/coolgithubprojects | Built a free, open-source Go CLI to stop hand-copying MCP servers and skills | — | — | "They drifted constantly. So we built gaal" | [link](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/) |
| r/AiBuilders | We built a tool to keep coding agents' skills and MCP servers in sync across machines | — | — | "the tax of copying it onto three machines" | [link](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/) |
| r/LovingOpenSourceAI | Official AI skills for GSAP — works with 40+ agents | — | — | "Agent Skills format; works with skills CLI (Cursor, Claude Code, Codex, Windsurf, Copilot, 40+ agents)" | [link](https://www.reddit.com/r/LovingOpenSourceAI/comments/1tr29t6/official_ai_skills_for_gsap_greensock_animation/) |
| r/LovingOpenSourceAI | ktx — executable context layer for data agents via MCP with skills and memory | — | — | "Allow Claude Code, Codex, and any AI agent to query data accurately through MCP" | [link](https://www.reddit.com/r/LovingOpenSourceAI/comments/1trwna2/ktx_ktx_is_an_executable_context_layer_for_data/) |
| r/mcp | Can MCP servers bundle Agent Skills? | — | — | "Instead of exposing many MCP tools directly, the MCP server exposes only one generic tool: execute_tool" | [link](https://www.reddit.com/r/mcp/comments/1tacsse/can_mcp_servers_bundle_agent_skills_so_any_mcp/) |
| r/ClaudeCode | Built a Cowork plugin for WordPress editing — 5 months of plugin-architecture learnings | — | — | "Shipped a Cowork plugin to Anthropic's marketplace. The Cowork plugin format is genuinely different" | [link](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/) |
| r/ClaudeCode | Quick-start guide for Vibe-Coding (includes awesome-claude-code ~36.8K stars) | — | — | "hesreallyhim/awesome-claude-code — The hand-curated, canonical big list of skills, hooks, slash commands, agent orchestrators, apps, and plugins" | [link](https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @VivekIntel | "🔌 Claude Code Plugins Directory — Curated marketplace of plugins, MCP servers, agents & skills for Claude Code" | 23 | 1 | [link](https://x.com/VivekIntel/status/2058028999646028087) |
| @digitalbrain01 | "Anthropic's official Claude Code plugin directory hits 29,000 GitHub stars in under 7 months" | 1 | 1 | [link](https://x.com/digitalbrain01/status/2062309821634715732) |
| @chenzeling4 | "Anthropic quietly launched an official plugin directory... One command installs community-built MCP servers, slash commands, and agent skills — no config file hacking required" | 2 | 0 | [link](https://x.com/chenzeling4/status/2059394913326993574) |
| @ClaudeCodeLog | "Claude Code CLI 2.1.153: Added skipLfs option to github/git plugin marketplace; Fixed stateful MCP servers reconnect-looping" | 14 | 0 | [link](https://x.com/ClaudeCodeLog/status/2059802891607589286) |
| @ClaudeCodeLog | "Claude Code CLI 2.1.136: Added settings.autoMode.hard_deny for auto mode; Fixed MCP servers disappearing after /clear in VS Code extension" | 14 | 1 | [link](https://x.com/ClaudeCodeLog/status/2052823737498575068) |
| @coder_surya | "MCP + SKILLS — best 6 skills of 100+, MCP intro + advanced, best practices guide" | 10 | 3 | [link](https://x.com/coder_surya/status/2053316137308549322) |
| @MetaEraCN | "Skill 经济：AI Agent 时代被低估的基础设施战争" (Skill economy: the underestimated infrastructure war of the AI Agent era) | 1 | 0 | [link](https://x.com/MetaEraCN/status/2062434779283534304) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 449 | 254 | — | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | [link](https://github.com/DrCatHicks/learning-opportunities) |
| adamthegoalie | Show HN: adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | — | [link](https://github.com/adamjgmiller/adamsreview) |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | [link](https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over) |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | [link](https://codeguilds.dev) |
| nmfisher | Claude Code and Blender MCP | 3 | 0 | — | [link](https://hydroxide.dev/articles/blender-mcp-claude-code/) |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | [link](https://github.com/openclaw-easy/ViralMint) |
| StanAngeloff | Teaching tmux to babysit my Claude Code agents | 3 | 0 | — | [link](https://blog.angeloff.name/post/2026/05/29/teaching-tmux-to-babysit-my-claude-code-agents/) |
| jsingh2525 | Arch-Decision – A multi-agent architecture tool for Claude Code | 3 | 1 | — | [link](https://github.com/jsingh6/arch-decision) |
| ij23 | LiteLLM Agent Platform: Run Claude Code/Codex On-Prem Sandboxes and Vaults | 3 | 0 | — | [link](https://github.com/BerriAI/litellm-agent-platform) |
| pretext | Agent View in Claude Code | 5 | 2 | — | [link](https://claude.com/blog/agent-view-in-claude-code) |
| anideshp | Show HN: Agent FM – local, open-source radio for Claude Code and Codex agents | 9 | 0 | — | [link](https://github.com/agentfm-ai/agent-fm) |
| sabahattink | Show HN: Full Stack HQ – Claude.md and Agent Stack for Claude Code | 10 | 0 | — | [link](https://github.com/sabahattink/antigravity-fullstack-hq) |
| fdarian | agent-dash: TUI for managing Claude Code and OpenCode in tmux | 3 | 0 | — | [link](https://news.ycombinator.com/item?id=48118041) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @carnage4life.bsky.social | "I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers" | 32 | [link](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) |
| @bootstrapyouragent.bsky.social | "OpenClaw is free. Claude Code is free (with Claude Max). The Mac Mini you probably already own. The only thing between you and a 24/7 AI agent is knowing how to set it up." | 12 | [link](https://bsky.app/profile/bootstrapyouragent.bsky.social/post/3mnbw5b5yew2n) |
| @frankfor.you | "Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable." | 7 | [link](https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n) |
| @build2launch-ai.bsky.social | "most people open claude code and think they need to build an app. wrong starting point... stop at the level that solves the problem." | 6 | [link](https://bsky.app/profile/build2launch-ai.bsky.social/post/3mnaebv74f72j) |
| @jcorvinus.bsky.social | "Going over the API or an agent sdk harness/Claude Code? That probably explains a large portion of it. The default web/mobile apps for the frontier providers are cognitive war zones" | 5 | [link](https://bsky.app/profile/jcorvinus.bsky.social/post/3mnbw5mvlac2r) |
| @marcus-schuler.com | "Supabase $10.5B valuation hinges on Claude Code driving 60%+ of new database creation." | 3 | [link](https://bsky.app/profile/marcus-schuler.com/post/3mnjcmgnda523) |
| @papoo7.bsky.social | "Claude Code Routines Put the Agent on Autopilot" | 2 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mnkqokufxt2g) |
| @papoo7.bsky.social | "Your AI Agents Are Aging: Why Agent Lifespan Matters" | 2 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mncvulhkle2e) |
| @midu.dev | "¡Nuevo curso gratuito de Anthropic! Agent Skills paso a paso y desde cero — deeplearning.ai/short-courses/agent-skills-with-anthropic/" | 2 | [link](https://bsky.app/profile/midu.dev/post/3mnmpkxdqsu2i) |
| @githubprojects.bsky.social | "Works with Claude Code, Claude Desktop, Codex, OpenCode, and any agent reading from ~/.agents/" | 2 | [link](https://bsky.app/profile/githubprojects.bsky.social/post/3mn7y422a672y) |
| @cadaeic.space | "instance of claude code just had its own 'oh my god agents' moment when it spun up a gemini agent for a test for the multi-LLM wargame" | 2 | [link](https://bsky.app/profile/cadaeic.space/post/3mnchsivz4s2u) |
| @epicvibecoder.bsky.social | "ECC (everything claude code) drops a full agent harness... MIT, free. your agent goes from autocomplete to self-improving operator." | 1 | [link](https://bsky.app/profile/epicvibecoder.bsky.social/post/3mnolsyre5f2k) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| skills.2389.ai | https://skills.2389.ai/ | Open source Claude Code plugins and MCP servers from 2389 Research; install via `npx skills add` or `/plugin marketplace add` |
| claudskills.com | https://claudskills.com/learn/claude-code-mcp-servers/ | 200+ MCP server directory; MCP open-sourced by Anthropic late 2024 |
| dev.to (alexcloudstar) | https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532 | Practitioner walkthrough of how Skills, MCP Servers, and Plugins fit together |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Definitional explainer: skills, agents, hooks, MCP, LSP by 12yr AI/ML veteran |
| buildwithclaude.com | https://buildwithclaude.com/ | 515+ practical extensions across Claude.ai, Claude Code, and the Claude API |
| github.com/jasonm4130/claude-skills | https://github.com/jasonm4130/claude-skills | Personal skills repo: adversarial-agents and deep-research (DAG-orchestrated multi-source synthesis) |
| github.com/juftin/skills | https://github.com/juftin/skills | Cross-platform agent skills directory compatible with Claude Code, Codex CLI, Gemini CLI |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code skills overview; thousands of skills now exist |
| skillkit.io | https://skillkit.io/blog/what-changed-in-claude-skills-april-2026 | April 2026 ecosystem changes; 3 Anthropic first-party skills released; portable format coming |
| claude.com/blog | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Official Dynamic Workflows announcement; up to 1,000 subagents |
| infoq.com | https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/ | Dynamic Workflows launch coverage; availability details |
| marktechpost.com | https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/ | Shipped alongside Claude Opus 4.8; workflow limits and pricing context |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Marketplace landscape overview; 8 major marketplaces by Q2 2026 |
| composio.dev | https://composio.dev/content/top-claude-code-plugins | Category breakdown of best Claude Code plugins |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregated directory: 20,300+ skills, 9,900+ MCP servers |

---

## Stats Block

```
├─ 🟠 Reddit: 8 threads
├─ 🔵 X: 7 posts │ 65 likes │ 6 reposts
├─ 🟡 HN: 15 stories │ 1,039 points │ 498 comments
├─ 🦋 Bluesky: 13 posts │ 76 likes │ 6 reposts
├─ 🌐 Web: 7 pages (engine) + 10 pages (WebSearch supplements)
└─ 🗣️ Top voices: @ClaudeCodeLog, @VivekIntel, @digitalbrain01, @carnage4life │ r/ClaudeCode, r/LovingOpenSourceAI, r/coolgithubprojects
```

---

## Data Gaps

- **YouTube: 0 results** - yt-dlp returned 0 results for this topic. SC YouTube API returned HTTP 402 (Payment Required). Given the topic's popularity, there are almost certainly tutorial videos on YouTube about Claude Code skills and MCP — they simply weren't captured.
- **TikTok/Instagram: 0 results** - SC API returned nothing; topic may lack short-form video coverage or hashtag vocabulary doesn't match. The #claudecode hashtag exists on TikTok but wasn't surfaced.
- **Reddit: limited** - Reddit public API returned 403 for direct search; only RSS-tier (25 posts) was available. r/ClaudeCode likely has substantially more discussion than the 8 threads captured.
- **X: thin** - 7 posts is a small sample; the @alexalbert__ "new skills in Claude Code" post (https://x.com/alexalbert__/status/2028586246419996846) was referenced in pre-flight but not in engine results.
- **Freshness skew**: only 17 of 50 dated items are from the last 7 days; coverage is stronger for late May than early June.
- **Approximate coverage**: ~55-65% of likely available signal given Reddit/YouTube/TikTok gaps.

---

## Key Quotes

> "Skills are a glimpse into how much capability is already inside current models, just waiting to be unlocked by better prompts." — [@alexalbert__](https://x.com/alexalbert__/status/1979577547575951616) on X

> "The marketplace model means quality actually gets curated instead of every half-baked GitHub gist ending up in your .claude directory." — [@chenzeling4](https://x.com/chenzeling4/status/2059394913326993574) on X

> "Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable. Step orchestration, state machines, backoff logic - those should work with any LLM backend." — [@frankfor.you](https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n) on Bluesky

> "most people open claude code and think they need to build an app. wrong starting point. every friction point is a build... stop at the level that solves the problem." — [@build2launch-ai.bsky.social](https://bsky.app/profile/build2launch-ai.bsky.social/post/3mnaebv74f72j) on Bluesky

> "I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers and Microsoft just got a big leg up in this race." — [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) on Bluesky

> "We got tired of the same chore: every time we added an MCP server or wrote a skill, we had to copy it into each agent's config, in each agent's format, on each machine. They drifted constantly." — [r/coolgithubprojects](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/) on Reddit

> "I keep seeing these terms thrown around in tutorials and videos, but I've never seen anyone give a concrete example that makes the difference actually click." — [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) on Reddit (Hooks vs Skills vs Plugins vs CLAUDE.md confusion)

> "ECC (everything claude code) drops a full agent harness into claude code, codex, cursor and opencode: skills, memory, instincts, security. MIT, free. your agent goes from autocomplete to self-improving operator." — [@epicvibecoder.bsky.social](https://bsky.app/profile/epicvibecoder.bsky.social/post/3mnolsyre5f2k) on Bluesky
