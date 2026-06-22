# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-22
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Reddit, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 5 threads | — | r/ClaudeAI, r/PromptEngineering |
| X/Twitter | 33 posts | 4,221 likes, 657 reposts | Top voices: @AnthropicAI, @ClaudeCodeLog, @omarsar0 |
| Hacker News | 29 stories | 127 points, 23 comments | Show HN projects dominant |
| Bluesky | 11 posts | 83 likes, 6 reposts | Developer commentary |
| GitHub | 8 items | 31 reactions, 68 comments | anthropics/claude-code, openai/codex |
| Web | 31 pages | — | Engine (18) + WebSearch supplements (13) |

---

## Synthesized Findings

### 1. The Three-Layer Architecture Is Clicking Into Place

**Skills vs MCP vs Plugins — the taxonomy confusion is clearing up.** A wave of explainer content in late May - early June 2026 signals that developers are finally internalizing how Claude Code's extension surfaces nest: CLAUDE.md is persistent context, skills load on-demand with staged tiering to minimize tokens, MCP is the open protocol for external tool access, and plugins are the distributable packaging layer that bundles all of the above. [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) published a definitive breakdown on June 10 titled "Claude Code Plugins vs Skills vs MCP: The Layers Explained." [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) extended it to cover Connectors. [saad.sh](https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained) went deepest, covering all six extension surfaces including Hooks vs AGENTS.md. Discussion spans X, HN, Reddit, and Bluesky.

**"Skills are domain knowledge, MCP is tool surface"** - the practitioner mental model is consolidating. [@laytoun](https://x.com/laytoun/status/2068692118659367067) on X described their current agentic loop setup: "starting with a PRD to define Done before the loop starts, skills for domain knowledge, few MCP servers for the tool surface, and worktrees for task isolation. I am using both Claude Code (most of the time) and Codex." This framing - skills for knowing, MCP for doing - recurred across sources.

### 2. The Marketplace Is Real and Growing Fast

**21,600+ community skills, 101 official plugins, 300K+ monthly developers.** As of June 2026, the Claude Code plugin ecosystem has hit meaningful scale. [claudemarketplaces.com](https://claudemarketplaces.com/) aggregates 21,600+ skills, 2,500+ marketplace sources, and 12,500+ MCP servers searchable with a single install command. The official Anthropic-managed marketplace ([claude-plugins-official on GitHub](https://github.com/anthropics/claude-plugins-official)) covers 101 plugins including GitHub, GitLab, Linear, Notion, Vercel, Slack, and Sentry. Top install counts per [Composio](https://composio.dev/content/top-claude-code-plugins): Frontend Design (829K installs), Superpowers (752K), Context7 (349K). May 2026 brought real-time type-to-filter in `/plugin` and `/skills` prompts.

**Community registries are also proliferating.** [CodeGuilds](https://codeguilds.dev) launched in June 2026 as a community registry for skills, agents, and MCP servers - surfaced on Hacker News ([HN thread](https://news.ycombinator.com/item?id=48619320), 3pts). Third-party plugin URLs are now accepted via `--plugin-url` flag since v2.1.108. [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky summed up the community energy with 35 likes: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character."

### 3. MCP Is Becoming Cross-Platform Infrastructure

**Adobe's CX skills and MCP servers going GA inside Claude Enterprise.** The biggest MCP news on June 22 was Adobe going enterprise-wide: [@wallstengine](https://x.com/wallstengine/status/2068999882682274267) reported (45 likes): "Adobe's CX skills and MCP servers are now generally available inside Anthropic's Claude Enterprise and Microsoft 365 Copilot." This signals MCP's evolution from developer plumbing to enterprise-grade, multi-vendor integration standard - available inside both Claude and Microsoft's ecosystem simultaneously.

**The official MCP Registry is approaching 2,000 server entries.** The [registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io/) launched in September 2025 preview and has grown to nearly 2,000 registered server entries with ~10K GitHub ecosystem signals. MCP has been adopted by OpenAI, Google DeepMind, and Microsoft, making it the de facto AI tool integration standard per [WorkOS's 2026 overview](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026). The [2026-07-28 release candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) - the largest spec revision since launch - delivers a stateless core that scales on HTTP, MCP Apps extension, a Tasks extension for long-running work, and OAuth/OIDC-aligned auth.

**MCP is plumbing for multi-client capability sharing.** [webdeveloper.com](https://webdeveloper.com/learn/guides/building-mcp-servers/) published a guide framing when MCP is the right choice: "The capability is consumed by multiple clients (your IDE agent, your chat product, a Slack bot)." A browser MCP server enabling both Codex and Claude sessions to drive the same browser also shipped in a GitHub PR at [manaflow-ai/cmux](https://github.com/manaflow-ai/cmux/pull/5232).

### 4. Skills Are the New Competitive Edge

**"The models are good enough now - what separates people is workflow mastery."** The most-quoted insight on [r/PromptEngineering](https://www.reddit.com/r/PromptEngineering/comments/1u5zljl/i_spent_a_full_day_watching_every_major_ai_agent/) (a June 14 thread distilling 6+ hours of agent tutorials) was: "The gap between Opus 4.6 and GPT 5.4 is nearly irrelevant. What actually separates people is workflow mastery: skills, MCP routing, and agentic loops." This positioned skills as the durable competitive moat - not model choice.

**[@omarsar0](https://x.com/omarsar0/status/1979242073372164306) built a skill that optimizes MCP tools.** Elvis's X post is widely cited: "Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code. I built a skill inside of Claude Code that automatically builds, tests, and optimizes MCP tools. It runs in a loop, loading context and tools." This recursive pattern - skills building better MCP tools - points toward self-improving agent capability stacks.

**[@HelloVyom](https://x.com/HelloVyom/status/2069029267682496993) on June 22 framed the new competitive layer:** "Most people think AI coding ends at: 'Build me an app.' The real advantage starts below the surface. As AI coding evolves, the difference is no longer who can generate code. It's who can provide the best context. MCP servers, custom prompts, agents.md, skills."

### 5. Distribution Is Still Fragmented - New Tooling Emerging

**Cross-agent sync is an unsolved pain point.** The top r/ClaudeAI post in the window came from the [gaal team](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/): "We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines." The motivation: "If you use Claude Code alongside any other coding agent (Cursor, Codex, Windsurf), same project means different rules filename per agent." The Codex community has independently noted this - an [openai/codex GitHub issue](https://github.com/openai/codex/issues/27831) requests npm package support in marketplace.json specifically because "the Claude Code marketplace format that `.agents/plugins/marketplace.json` mirrors" doesn't support npm sources yet.

**Organization-wide managed skills provisioning now live.** Per [morphllm.com's May 2026 guide](https://www.morphllm.com/claude-code-marketplace), enterprise admins can now provision skills organization-wide from the admin console by uploading a zip under Organization settings. [hidekazu-konishi.com](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html) published a complete guide to plugin packaging for team distribution. The three distribution scopes are: project-level (.claude/skills/ committed to repo), plugin-level (skills/ in a plugin bundle), and managed/organization-wide.

### 6. HN Builder Community Is Shipping Extensions Fast

**Hacker News has become the de facto launch pad for Claude Code extensions.** The June window saw a cluster of Show HN posts: [Norrin](https://news.ycombinator.com/item?id=48619320) (git/diff control plugin, 4pts), [Antigravity plugin](https://simplybychris.github.io/antigravity-plugin-cc/) for Claude Code (2pts), [CCTV](https://github.com/manelrv/CCTV) (menu bar agent monitor, 2pts), [5dive](https://github.com/5dive-com/5dive) (Telegram → team of Claude Code agents, 3pts), and ["a police department for your Claude Code agents"](https://github.com/varmabudharaju/agent-pd/blob/master/README.md) (11pts, 8 comments - the most engaged Show HN of the window). Also surfaced: a [visual composer for Claude Code multi-agent workflows](https://github.com/fayzan123/claude-workflow-composer), an [MCP server for Mac GUI automation via AppleScript](https://github.com/m0rvayne/mcp-osascript), and a [MCP for the ChatGPT Ads API](https://github.com/HYPD-AI/openai-ads-mcp) - using Claude to query a competitor's ad data.

**[@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) is using Claude Code to write ChimeraX scientific visualization plugins.** A Bluesky post with 6 likes noted: "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting... Most likely older plugins could be ported over that way relatively easily." This illustrates Claude Code + skills as a meta-tool for extending OTHER applications' plugin ecosystems.

---

## Cross-Source Patterns

**Pattern 1: Skills as the new minimum viable setup** - The "skills + few MCP servers + worktrees" stack [@laytoun](https://x.com/laytoun/status/2068692118659367067) described on X echoes the [r/PromptEngineering practitioner thread](https://www.reddit.com/r/PromptEngineering/comments/1u5zljl/i_spent_a_full_day_watching_every_major_ai_agent/) and [@omarsar0's](https://x.com/omarsar0/status/1979242073372164306) "don't sleep on skills" post. Appearing on X, Reddit, HN, and Bluesky.

**Pattern 2: Multi-agent/cross-agent compatibility pressure** - The gaal CLI post on Reddit, the openai/codex npm marketplace GitHub issue, and the [HN debate on Gemini CLI vs Claude Code agent capabilities](https://imaxxs.com/behavioral-induction-capabilities-shape-execution) all point to a multi-agent world where skills and MCP servers need to work portably across agents. Appearing on Reddit, GitHub, HN.

**Pattern 3: MCP as enterprise-grade cross-vendor standard** - Adobe's MCP GA announcement, the WorkOS enterprise guide, and the 2026-07-28 MCP spec release candidate all point to MCP graduating from developer toy to production infrastructure. Appearing on X, Web, official docs.

**Pattern 4: "Mods not plugins" desire** - [@jefferyharrell's](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) Bluesky post about wanting "mods" (deep, composable, community-curated customizations) vs. "plugins" (discrete add-ons) resonated (35 likes). His follow-up: "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." This tension between power-user mod culture and the current plugin model appears on Bluesky and HN.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/PromptEngineering | I spent a full day watching every major AI agent tutorial in 2026 | — | — | "The models are good enough now. What actually separates people is workflow mastery: skills, MCP routing, and agentic loops." | https://www.reddit.com/r/PromptEngineering/comments/1u5zljl/i_spent_a_full_day_watching_every_major_ai_agent/ |
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | — | — | "If you use Claude Code alongside any other coding agent, same project means different rules filename per agent." | https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @AnthropicAI | "New Frontier Red Team blog: Phase 2 of Project Fetch...Opus 4.7, on its own, was ~20x faster than last year's best human team aided by Opus 4.1." | 2,160 | 181 | https://x.com/AnthropicAI/status/2067651699486200091 |
| @ClaudeCodeLog | "Claude Code 2.1.185 has been released. Stream-stall hint now shows 'Waiting for API response · will retry', waits 20s (was 10s)" | 535 | 26 | https://x.com/ClaudeCodeLog/status/2068440518514626599 |
| @wallstengine | "$ADBE...Adobe's CX skills and MCP servers are now generally available inside Anthropic's Claude Enterprise and Microsoft..." | 45 | 5 | https://x.com/wallstengine/status/2068999882682274267 |
| @omarsar0 | "Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code. I built a skill inside of Claude Code that automatically builds, tests, and optimizes MCP tools." | — | — | https://x.com/omarsar0/status/1979242073372164306 |
| @HelloVyom | "The real advantage starts below the surface...It's who can provide the best context. MCP servers, custom prompts, agents.md, skills." | 2 | — | https://x.com/HelloVyom/status/2069029267682496993 |
| @laytoun | "skills for domain knowledge, few MCP servers for the tool surface, and worktrees for task isolation" | 1 | 1 | https://x.com/laytoun/status/2068692118659367067 |
| @nasim_haiderQ | "54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack." | — | — | https://x.com/nasim_haiderQ/status/2069015756931846562 |
| @avthars | "Claude Code crash course: Plugins - let you easily use best practices and customizations from other developers" | — | — | https://x.com/avthars/status/1990411824928264532 |
| @claudeai | "Today we're introducing Claude Code Plugins in public beta...curated collections of slash commands, agents, MCP servers, and hooks" | — | — | https://x.com/claudeai/status/1976332881409737124 |
| @zxkane | "aws-skills: Claude Code plugins for AWS development — CDK best practices, cost optimization, serverless guidance, MCP server integration" | — | — | https://x.com/zxkane/status/1980884940968399139 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| varmabudharaju | Show HN: A police department for your Claude Code agents | 11 | 8 | — | https://github.com/varmabudharaju/agent-pd/blob/master/README.md |
| (hn) | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| (hn) | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| (hn) | Norrin – Git/ diff control in Claude Code | 4 | 1 | — | https://news.ycombinator.com/item?id=48619320 |
| (hn) | Gemini CLI vs. Claude Code: Why agent capabilities matter more than prompts | 3 | — | — | https://imaxxs.com/behavioral-induction-capabilities-shape-execution |
| (hn) | Show HN: 5dive – Run a Team of Claude Code Agents from Telegram | 3 | — | — | https://github.com/5dive-com/5dive |
| (hn) | Show HN: Open-source Antigravity plugin for Claude Code | 2 | — | — | https://simplybychris.github.io/antigravity-plugin-cc/ |
| (hn) | MCP server that lets Claude click menus on your Mac and fix its own mistakes | 2 | — | — | https://github.com/m0rvayne/mcp-osascript |
| (hn) | Auto complete tickets using Claude Code loop on telegram with linear MCP | 1 | 1 | — | https://niptao.com/blog/an-engineer-you-manage-from-a-group-chat/ |
| (hn) | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |
| (hn) | CCTV – See which Claude Code agent needs you, from the menu bar | 2 | — | — | https://github.com/manelrv/CCTV |
| (hn) | Show HN: Visual composer for Claude Code multi-agent workflows | 2 | 1 | — | https://github.com/fayzan123/claude-workflow-composer |
| (hn) | Show HN: MCP for the ChatGPT Ads API – Query ChatGPT Ads from Claude and Codex | 3 | 1 | — | https://github.com/HYPD-AI/openai-ads-mcp |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list..." | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | "I made three large kits for that specific problem...I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Authoritative layer comparison: plugins > skills > MCP; explains nesting |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Extends taxonomy to include Connectors; AI strategy use cases |
| saad.sh | https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained | Most comprehensive: all 6 surfaces (Hooks, Skills, MCP, Plugins, CLAUDE.md, AGENTS.md) |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Open SKILL.md registry; explains which extension surface to pick |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html | Plugin packaging for team distribution; plugin.json spec details |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Official plugin system overview by AI/ML engineer |
| deepwiki.com | https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery | Indexed plugin marketplace architecture from claude-code repo |
| webdeveloper.com | https://webdeveloper.com/learn/guides/building-mcp-servers/ | When to use MCP vs tool calls; TypeScript/streamable HTTP production guide |
| code.claude.com | https://code.claude.com/docs/en/discover-plugins | Official plugin discovery docs; /plugin type-to-filter |
| registry.modelcontextprotocol.io | https://registry.modelcontextprotocol.io/ | Official MCP server registry; ~2,000 entries |
| workos.com | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | Enterprise MCP adoption guide; cross-vendor standard status |
| blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | MCP spec 2026-07-28 RC; stateless core, MCP Apps, Tasks extension |
| codeguilds.dev | https://codeguilds.dev | Community registry for Claude Code skills, agents, MCP servers |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregator: 21,600+ skills, 12,500+ MCP servers |
| composio.dev | https://composio.dev/content/top-claude-code-plugins | Plugin install counts; top plugins by popularity |
| morphllm.com | https://www.morphllm.com/claude-code-marketplace | Org-wide managed skills; --plugin-url flag docs |
| levelup.gitconnected.com | https://levelup.gitconnected.com/a-mental-model-for-claude-code-skills-subagents-and-plugins-3dea9924bf05 | Mental model: skills/subagents/plugins; staged loading explained |
| github.com/anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | Official Anthropic-managed plugin directory |
| github.com/anthropics/skills | https://github.com/anthropics/skills | Public repository for Agent Skills |
| github.com/jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; tonsofskills.com CLI |
| github.com/alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 337 skills across 8 coding agents (Claude Code, Codex, Gemini CLI, Cursor...) |
| github.com/daymade/claude-code-skills | https://github.com/daymade/claude-code-skills | Professional skills marketplace; production-ready skill workflows |
| dev.to | https://dev.to/suraj_khaitan_f893c243958/i-tried-100-claude-skills-these-are-the-best-1m4a | Practitioner review of 100 community skills |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-skills | "Best Claude Code Skills to Try in 2026" curated list |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Resource bible: 54 tools, agents, MCP servers, skills, workflows |

---

## Stats Block

```
├─ 🔵 X: 33 posts │ 4,221 likes │ 657 reposts
├─ 🟢 HN: 29 stories │ 127 points │ 23 comments
├─ 🦋 Bluesky: 11 posts │ 83 likes │ 6 reposts
├─ 🐙 GitHub: 8 items │ 31 reactions │ 68 comments
├─ 🟠 Reddit: 5 threads │ r/ClaudeAI, r/PromptEngineering
├─ 🌐 Web: 31 pages (engine 18 + supplements 13)
└─ 🗣️ Top voices: @AnthropicAI, @ClaudeCodeLog, @omarsar0 │ r/ClaudeAI, r/PromptEngineering
```

---

## Data Gaps

- **YouTube: 0 results** - YouTube search returned zero items despite multiple retry attempts; ScrapeCreators key hit 402 Payment Required; significant gap given the tutorial/walkthrough content that likely exists on YouTube for Claude Code skills/plugins.
- **TikTok: 0 results** - ScrapeCreators API returned 402 Payment Required for all hashtag searches (#claudecode, #mcpservers, #aiagent, #aicoding); no short-form video coverage.
- **Instagram: 0 results** - ScrapeCreators API 402 errors; no creator/influencer coverage.
- **Reddit coverage thin (5 threads)** - Public Reddit API returning 403 for some queries; ScrapeCreators backup also 402. Only 5 threads surfaced from r/ClaudeAI and r/PromptEngineering.
- **Freshness note** - Only 47 of 104 dated engine items are from the last 7 days; the topic skews toward evergreen documentation and ecosystem-building content rather than breaking news.
- **GitHub: no token** - GitHub search ran unauthenticated (low rate limit); likely missed additional relevant repos and PRs.
- **Estimated coverage:** ~65% - good X, HN, Bluesky, and web coverage; missing YouTube/TikTok/Instagram entirely and Reddit partially.

---

## Key Quotes

> "Don't sleep on Skills. Skills is easily one of the most effective ways to steer Claude Code. I built a skill inside of Claude Code that automatically builds, tests, and optimizes MCP tools. It runs in a loop, loading context and tools." — [@omarsar0](https://x.com/omarsar0/status/1979242073372164306) on X

> "The models are good enough now. The gap between Opus 4.6 and GPT 5.4 is nearly irrelevant. What actually separates people is workflow mastery: skills, MCP routing, and agentic loops." — [r/PromptEngineering](https://www.reddit.com/r/PromptEngineering/comments/1u5zljl/i_spent_a_full_day_watching_every_major_ai_agent/)

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "Starting with a PRD to define Done before the loop starts, skills for domain knowledge, few MCP servers for the tool surface, and worktrees for task isolation." — [@laytoun](https://x.com/laytoun/status/2068692118659367067) on X

> "The real advantage starts below the surface. As AI coding evolves, the difference is no longer who can generate code. It's who can provide the best context. MCP servers, custom prompts, agents.md, skills." — [@HelloVyom](https://x.com/HelloVyom/status/2069029267682496993) on X

> "We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines...If you use Claude Code alongside any other coding agent (Cursor, Codex, Windsurf), same project means different rules filename per agent." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/)

> "Adobe's CX skills and MCP servers are now generally available inside Anthropic's Claude Enterprise and Microsoft 365 Copilot." — [@wallstengine](https://x.com/wallstengine/status/2068999882682274267) on X

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky
