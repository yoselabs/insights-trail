# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-19
**Query type:** GENERAL
**Sources:** X, Bluesky, GitHub, Reddit, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 2 threads | low (RSS-only, no upvote data) | r/ClaudeAI, r/artificial |
| X/Twitter | 16 posts | 2,359 likes, 193 reposts | @AnthropicAI dominant |
| Bluesky | 12 posts | 86 likes, 6 reposts | Developer community active |
| GitHub | 18 items | 133 reactions, 213 comments | anthropics/claude-code, openclaw/openclaw |
| Web | 28 pages | — | 15 engine + 13 supplemental WebSearch |
| YouTube | 0 videos | — | yt-dlp returned zero; SC 402 error |
| Hacker News | 0 stories | — | HN API 400 errors on all queries |
| TikTok | 0 videos | — | SC API 402 Payment Required |
| Instagram | 0 reels | — | SC API 402 Payment Required |
| Polymarket | 0 markets | — | No markets on this topic |

---

## Synthesized Findings

### 1. The Layered Extension Architecture: Skills vs MCP vs Plugins

The most-discussed concept in the last 30 days is how Claude Code's extension stack works - and most developers are confused. Multiple explainer articles published in June 2026 indicate the market is still learning the distinctions. The clearest framing comes from [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) (June 10): "Plugins, skills, and MCP servers sit at different layers in Claude Code. What each is, how they nest, and a clear guide to which one you actually need." [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) (June 13) offers the cleanest summary: "Skills teach Claude how to do a [thing]. MCP servers give Claude access to external tools and data. Plugins bundle both into distributable packages."

Anthropic published a first-party guide on June 18 - [Steering Claude Code: CLAUDE.md files, skills, hooks, rules, subagents and more](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) - listing seven distinct behavioral configuration methods, signaling the ecosystem complexity is now official-doc-worthy. [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) (May 22) describes the two "big extension surfaces": skills are markdown files that become custom slash commands Claude can run, while MCP servers are external services Claude can call over protocol.

[dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) (June 8) frames the choice as a "lightest first" principle: reach for a skill before an MCP server, reach for an MCP server before a plugin. [@HeyAnjula](https://x.com/HeyAnjula/status/2067617186034917833) on X articulates where this leads: "Claude Code isn't becoming a coding assistant. It's becoming an AI operating system for software development. One command: /plugin install claude-code-setup@claude-plugins-official. And Claude starts analyzing your project to recommend hooks for everything."

Platforms: X, Web, Bluesky, Reddit

### 2. Marketplace Explosion: Three Competing Distribution Channels

The Claude Code skill/plugin marketplace has fragmented into several competing surfaces, each serving different audiences. [claudemarketplaces.com](https://claudemarketplaces.com/) is currently the largest community-curated aggregator, claiming 21,600+ skills, 2,500+ marketplaces, and 12,500+ MCP servers updated daily from GitHub. [tonsofskills.com](https://tonsofskills.com/) is the open-source alternative, with 425 plugins, 2,810 skills, and 200 agents for Claude Code, distributed via a `ccpi` CLI package manager. On the official side, [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) ships 101 vetted plugins plus 68 partner plugins from GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase.

The [PostHog PR on GitHub](https://github.com/PostHog/posthog/pull/64385) (June 17) reveals how teams are using skills internally: "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams." This is skills-as-internal-knowledge-base - a different use case than public marketplaces. [@github_update](https://x.com/github_update/status/2067259115777507386) (June 17) rounds up "20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking" - the proliferation is now a curation problem.

[@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) captures the developer zeitgeist: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." In a follow-up he says: "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

Cross-client context: [Azure SRE Agent](https://sre.azure.com/docs/capabilities/plugin-marketplace) now runs its own plugin marketplace using the same SKILL.md format, browsable from the GUI with SHA-256 content hashing for update detection - signaling the format is spreading beyond Claude Code itself.

Platforms: X, Bluesky, GitHub, Web

### 3. The MCP Ecosystem Has Won (And Is Now a Governance Problem)

MCP has crossed from developer experiment to multi-company open standard in 2026. Per [WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026): MCP is now a Linux Foundation project, with AWS, Cloudflare, and Google all publishing production commitments. The numbers are significant: 9,652 servers in the [official MCP Registry](https://registry.modelcontextprotocol.io/), 20,222+ on [mcp.so](https://mcp.so), 7,000+ on [smithery.ai](https://smithery.ai), and 97 million monthly SDK downloads per [Digital Applied](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol). Per [Stacklok's 2026 software report](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol), 41% of surveyed software organizations are in limited or broad MCP production. The MCP specification release candidate was published July 28 (future date per source), with stateless transport as the top H2 2026 roadmap item.

The maturity gap is in distribution: per [Digital Applied](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution), less than 5% of MCP servers are monetized. The market resembles the early iOS App Store - lots of free offerings, monetization wave still pending. The fragmentation is real: [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries) identifies four main registries that "matter," none of them universally dominant.

[@OGstdioh](https://x.com/OGstdioh/status/2067597176855830574) on X frames the adoption pitch clearly: "Claude Code isn't 'smart' by default - it's smart about what you connect to it. Add MCP servers for the tools you actually use (DBs, APIs, automation, docs) and it goes from generic helper to teammate that knows your stack. The setup is the superpower." [@Obots_ai](https://x.com/Obots_ai/status/2067593353978364050) announced Obot Platform v0.23.0 with an `obot mcp search` command for finding MCP servers from the terminal, plus an LLM Gateway that coding agents like Claude Code or Codex can point at directly - signaling infrastructure-layer tooling for MCP server discovery is maturing.

A [GitHub issue on openai/codex](https://github.com/openai/codex/issues/25750) (June 2) calls for "MCP Server Registry Discovery: connect Codex to an enterprise MCP server catalog with a single command" - confirming that enterprise MCP registry connectivity is an open problem across all coding agents, not just Claude Code.

Platforms: X, GitHub, Web

### 4. AI Coding Tools as an Autonomy Layer Stack

[@_bemax](https://x.com/_bemax/status/2067525222106857858) on X (June 18) posted the most-shared conceptual framing of the month: "Since AI started blowing up, there's been a new hype layer every few months: 1. Chat: ChatGPT, Claude, Perplexity. 2. Connectors / MCP servers. 3. Local runtimes & skills: Claude Code, Codex, Cursor. 4. Agents & bots: OpenClaw, NanoBot, Hermes. Each one wraps the last in more autonomy. Each one burns more tokens. What's the next layer? What am I missing?" This received 4 likes and 1 reply - small engagement, but high conceptual signal.

[@MaryamMiradi](https://x.com/MaryamMiradi/status/2067695864022278598) (June 18) shares a "9 feature roadmap from CLAUDE.md to MCP Server": CLAUDE.md rules first ("Write this before any code. Not after setup. Before."), then skills, then MCP server as the final extension surface. This structured progression is becoming canonical practitioner advice.

[@Bluesky @webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) (May 29) highlights the commoditization angle: "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." Free bundled alternatives are competing against individual paid plugins.

[@girlinAI](https://x.com/girlinAI/status/2067773562392637545) on X (June 19) distills the stacking guidance: "You don't need all 10. Pick 2-3 based on your workflow: heavy terminal output? RTK. Huge codebase? code-review-graph + Token Savior. Lots of MCP servers? Context Mode. Want a quick win? Caveman Claude + claude-token-efficient."

Platforms: X, Bluesky

### 5. Security Scanning for the Skills Ecosystem

The growth of third-party skills and MCP servers has created a trust problem. [@ThatNaman](https://x.com/ThatNaman/status/2067621718219497559) (June 18) announced a tool to "scan and surface risks in unknown skills, MCP servers, AGENT.md/CLAUDE.md files, agent configs and more across your favorite AI tools - claude code, codex, cowork, cursor, antigravity and many more!" This is the first dedicated security scanner for the Claude Code ecosystem seen in the data.

On GitHub, there are two active bug reports on [anthropics/claude-code](https://github.com/anthropics/claude-code/issues/61015) regarding MCP tool calls failing with "requires approval" in scheduled routines - a regression from ~2026-05-20. Issue #61015 has 52 reactions and 40 comments; issue #61027 has 33 reactions and 18 comments. These are the highest-engagement GitHub items in the corpus, showing that MCP permission management in automated contexts is a hot pain point.

[42Crunch announced](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) a Claude Code integration with "dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise" - security tooling is arriving at the enterprise layer.

Platforms: X, GitHub, Bluesky

### 6. Quality vs Quantity: The Single-Skill Thesis

The community is starting to push back on skill overload. [@jordanfjf02](https://x.com/jordanfjf02/status/2067670075205636274) (June 18, in Spanish): "One skill. Just one. Install it once. And every time you ask Claude Code for something: it expands your prompt into a complete spec, asks what it was going to guess, builds from a complete brief. THAT skill is worth more than 50 MCP servers. What's your favorite skill?" This counter-maximalism framing was shared and resonated.

[@girlinAI](https://x.com/girlinAI/status/2067773562392637545)'s "pick 2-3" approach and [@OGstdioh](https://x.com/OGstdioh/status/2067597176855830574)'s "add MCP servers for tools you actually use" both reinforce the same pattern: the ecosystem is large enough that curation is now the skill.

The community is also using Claude Code to write plugins for other tools. [@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o): "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting. Most likely older plugins could be ported over that way relatively easily." [@viriditax.bsky.social](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227): "When newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it to flex it - promptly made a bass octaver combined with an autopan."

Platforms: X, Bluesky

### 7. Anthropic's Official Moves This Week

[@AnthropicAI](https://x.com/AnthropicAI/status/2067651699486200091) (June 18, 1,804 likes) announced Phase 2 of Project Fetch - testing how well Claude can program a robodog - not directly skills/plugins, but signaling Anthropic is actively dog-fooding agentic Claude Code for non-coding tasks. The robodog use case demonstrates Claude Code + MCP as a robotics control interface.

The Anthropic blog published ["A harness for every task: dynamic workflows in Claude Code"](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) on June 2, explaining how Claude Code can "write and orchestrate its own multi-agent harness on the fly" - shifting the narrative from "install skills" to "Claude generates its own workflow tools."

Claude Code itself was updated to version 2.1.181 (from 2.1.97) in the last 30 days per the [lrittel/claude-code-nix PR](https://github.com/lrittel/claude-code-nix/pull/62) - rapid cadence. The [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u9e4gs/new_in_claude_code_artifacts/) thread for "New in Claude Code: Artifacts" (June 18) discusses interactive pages built from your session - PR walkthroughs, living project dashboards - available in beta on Team and Enterprise plans, and notably drawing on "the full context of your session: codebase, plugins, skills."

Platforms: X, GitHub, Reddit, Web

---

## Cross-Source Patterns

### Pattern 1: The Extension Taxonomy Confusion Is Now a Genre

Three or more explainer articles/posts on X and Bluesky are clarifying the skill/MCP/plugin distinction in the same 30-day window. This suggests the ecosystem launched faster than the mental models. Appeared on: Web (mcsaguru.com, tygartmedia.com, dev.to, ai-trove.com, claudefolio.com, hidekazu-konishi.com), X (@HeyAnjula, @MaryamMiradi), Bluesky (@hackernewsbot.bsky.social citing an HN thread). The volume of "which layer do I use?" content is a leading indicator that the ecosystem is approaching an inflection point between early adopters and mainstream developers.

Key quote: "People treat plugins, skills, and MCP servers as three options on the same menu, then get confused when the comparison doesn't quite work." - [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained)

### Pattern 2: Cross-Client MCP Is Normalizing

MCP is now the connecting tissue between Claude Code, Codex, Cursor, and OpenClaw. Every practitioner post this month frames MCP servers as cross-client assets, not Claude-exclusive. Appeared on: X (@_bemax's layer chart, @Obots_ai's LLM Gateway, @alphabatcher's vibecoding servers), Bluesky (@toyinariyo, @mengli512.bsky.social), GitHub (openai/codex MCP Registry issue, openclaw competitive analysis), Web (totalum.app's cross-client picks, agensi.io, clarista.io).

Key quote: "Claude Code isn't 'smart' by default - it's smart about what you connect to it. Add MCP servers for the tools you actually use." - [@OGstdioh](https://x.com/OGstdioh/status/2067597176855830574) on X

### Pattern 3: "Claude Code as AI OS" Narrative

Multiple voices independently describe Claude Code's extension ecosystem as making it an "AI operating system" rather than a coding assistant. Appeared on: X (@HeyAnjula explicitly, @_bemax's autonomy layer framing), Bluesky (@jefferyharrell.bsky.social's "mods" post), Web (Anthropic's own "harness for every task" post, claude.com "steering" post).

Key quote: "Claude Code isn't becoming a coding assistant. It's becoming an AI operating system for software development." - [@HeyAnjula](https://x.com/HeyAnjula/status/2067617186034917833) on X

### Pattern 4: Security and Trust as Growth Blocker

As the skill/MCP ecosystem grows, trust and security are emerging as friction points. Two separate signals on separate platforms: a new security scanner from [@ThatNaman](https://x.com/ThatNaman/status/2067621718219497559) on X and two high-engagement GitHub bug reports about MCP permission regressions in Claude Code. Third signal: 42Crunch's enterprise DevSecOps plugin announcement on Bluesky. The ecosystem is large enough to need security tooling.

Appeared on: X, GitHub, Bluesky

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | New in Claude Code: Artifacts | n/a (RSS) | n/a | "Interactive pages built from your session, like a PR walkthrough or a living project dashboard, shared with your team at a private link. Artifacts draw on the full context of your session: codebase, plugins, skills." | https://www.reddit.com/r/ClaudeAI/comments/1u9e4gs/new_in_claude_code_artifacts/ |
| r/artificial | mlx-code - A Coding Agent That Speaks Git Natively | n/a (RSS) | n/a | — | https://www.reddit.com/r/artificial/comments/1u9urrk/mlxcode_a_coding_agent_that_speaks_git_natively/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @AnthropicAI | New Frontier Red Team blog: Phase 2 of Project Fetch, where we test how well Claude can program a robodog. Opus 4.7, on its own, was ~20x faster... | 1,804 | 145 | https://x.com/AnthropicAI/status/2067651699486200091 |
| @AnthropicAI | Watch the robodogs in action in our first Project Fetch experiment | 184 | 12 | https://x.com/AnthropicAI/status/2067651700757086553 |
| @AnthropicAI | These and other measures will allow us to track consequential shifts in the nature of work... | 252 | 21 | https://x.com/AnthropicAI/status/2066969542010806561 |
| @alphabatcher | top 11 MCP servers for vibecoding (links inside) | 83 | 9 | https://x.com/alphabatcher/status/2067545100872249527 |
| @MaryamMiradi | How to Build AI Agents with Claude Code. 9 feature roadmap from CLAUDE.md to MCP Server. Feature 1: CLAUDE.md. Write this before any code. Not after setup. | 14 | 1 | https://x.com/MaryamMiradi/status/2067695864022278598 |
| @Anushkaa1407 | The How-to Claude Guide | 7 | 4 | https://x.com/Anushkaa1407/status/2067551219133104236 |
| @github_update | AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking | 6 | 1 | https://x.com/github_update/status/2067259115777507386 |
| @_bemax | Since AI started blowing up there's been a new hype layer every few months: 1. Chat 2. Connectors/MCP servers 3. Local runtimes & skills 4. Agents & bots | 4 | 0 | https://x.com/_bemax/status/2067525222106857858 |
| @ThatNaman | Scan and surface risks in unknown skills, MCP servers, AGENT.md/CLAUDE.md files, agent configs | 2 | 0 | https://x.com/ThatNaman/status/2067621718219497559 |
| @HeyAnjula | Most developers think Claude Code's superpower is the model. It's not... Claude Code is becoming an AI operating system for software development. | 2 | 0 | https://x.com/HeyAnjula/status/2067617186034917833 |
| @OGstdioh | Claude Code isn't "smart" by default - it's smart about what you connect to it. Add MCP servers for the tools you actually use. The setup is the superpower. | 0 | 0 | https://x.com/OGstdioh/status/2067597176855830574 |
| @Obots_ai | Obot Platform v0.23.0 - LLM Gateway for coding agents, obot mcp search command, reworked UI | 1 | 0 | https://x.com/Obots_ai/status/2067593353978364050 |
| @jordanfjf02 | Un skill. Uno solo. Lo instalas una vez. ESE skill vale mas que 50 MCP servers. | 0 | 0 | https://x.com/jordanfjf02/status/2067670075205636274 |
| @girlinAI | HOW TO STACK THEM. You don't need all 10. Pick 2-3 based on your workflow. | 0 | 0 | https://x.com/girlinAI/status/2067773562392637545 |
| @0xCrash_ | ai coding tools made the wrong thing weirdly comfortable: building polished software before you have pain, distribution, or a buyer | 0 | 0 | https://x.com/0xCrash_/status/2067565769672601748 |
| @getYankee | Yankee is a social platform with an integrated IDE powered by Claude Code and MCP | 0 | 0 | https://x.com/getYankee/status/2067811607862743093 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods. I wanna spend six hours meticulously curating a mod list... | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @coolhand.bsky.social | I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @viriditax.bsky.social | when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried... promptly made a bass octaver | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @webuyhousesusa.bsky.social | ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - free MIT-licensed system | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @jefferyharrell.bsky.social | I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @github-trending-js.bsky.social | Today's GitHub trend: anthropics/knowledge-work-plugins - plugins that turn Claude into a specialist for specific roles/companies | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @brunopedro.com | 42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins for Agentic DevSecOps | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @toyinariyo.bsky.social | There are also many Godot AI plugins that can be used with Claude Code and Codex | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |
| @mengli512.bsky.social | Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |
| @hackernewsbot.bsky.social | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | Discussion | 1 | https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p |
| @dailygithubtrends.bsky.social | anthropics/knowledge-work-plugins trending - plugins that turn Claude into a specialist for specific roles | 1 | https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mmlwuhsu732c |

**GitHub:**
| User/Repo | Title | Reactions | Comments | Notable Quote | URL |
|-----------|-------|-----------|----------|--------------|-----|
| anthropics/claude-code | [BUG] Scheduled routines fail every MCP tool call with "requires approval" (regression ~2026-05-20) | 52 | 40 | Critical MCP permission regression for automated workflows | https://github.com/anthropics/claude-code/issues/61015 |
| anthropics/claude-code | [BUG] Routines: MCP connector tool calls fail with "requires approval" despite connectors being added | 33 | 18 | Second report of same bug class | https://github.com/anthropics/claude-code/issues/61027 |
| PostHog/posthog | feat(skills): Claude Code & Codex plugin marketplace + zip export | — | 7 | "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams." | https://github.com/PostHog/posthog/pull/64385 |
| zaheerops/agent-mem | chore: agent-mem rebrand - initial plugin distribution | — | 9 | Ships v13.5.5 plugin runtime: Claude/Codex/Cursor manifests, hooks, worker/MCP scripts, skills, modes | https://github.com/zaheerops/agent-mem/pull/1 |
| openclaw/openclaw | TUI Competitive Analysis: 15 Gaps to Close vs Claude Code, Aider, Codex CLI, Kimi CLI, Goose | — | 3 | OpenClaw's key differentiator is its TUI; skills ecosystem comparison underway | https://github.com/openclaw/openclaw/issues/86534 |
| openclaw/openclaw | RFC: Skills Dependency Visualizer - understand skill interdependencies visually | — | 5 | "As the OpenClaw Skills ecosystem grows (800+ skills on ClawHub), understanding which skills depend on which becomes critical." | https://github.com/openclaw/openclaw/issues/88173 |
| openai/codex | MCP Server Registry Discovery: connect Codex to an enterprise MCP server catalog with a single command | 1 | — | Cross-client MCP registry discovery is an open feature request | https://github.com/openai/codex/issues/25750 |
| anomalyco/opencode | [FEATURE]: Plugin/Agent/Skills/etc marketplace | — | 4 | "Master issue for a unified OpenCode marketplace / registry / package distribution system" | https://github.com/anomalyco/opencode/issues/28696 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claude.com (Anthropic) | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | Official June 18 guide: seven behavioral config methods in Claude Code |
| claude.com (Anthropic) | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | June 2 post on dynamic multi-agent harnesses Claude Code can self-generate |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | June 10 taxonomy explainer: plugins/skills/MCP as layers, not alternatives |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | June 13 practitioner guide; clearest single-sentence distinctions |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | June 8 "lightest first" decision heuristic |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | May 24 deep-dive; AI/ML + security author Paul Irolla |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | May 22 explainer on the two main extension surfaces |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html | June 11 decision guide for all 7 extension layers |
| blog.laozhang.ai | https://blog.laozhang.ai/en/posts/claude-code-hooks-slash-commands-skills | June 1 guide: "who starts the action" as the deciding question |
| devencyclopedia.com | https://devencyclopedia.com/blog/claude-code-cheatsheet | June 6 complete reference: every slash command, keyboard shortcut, hook, subagent, CLAUDE.md tip |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | May 27: from personal plugin to org standard rollout pattern |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 21,600+ skills, 2,500+ marketplaces, 12,500+ MCP servers - largest aggregator |
| tonsofskills.com | https://tonsofskills.com/ | 425 plugins, 2,810 skills, 200 agents; ccpi CLI package manager |
| github.com/jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | Open-source marketplace source repo |
| github.com/rohitg00 | https://github.com/rohitg00/awesome-claude-code-toolkit | 135 agents, 35 skills, 176+ plugins, 14 MCP configs, comprehensive toolkit |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Four key MCP registries compared: mcp.so, smithery.ai, glama.ai/mcp, awesome-mcp-servers |
| digitalapplied.com | https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol | 41% of orgs in MCP production; 97M monthly SDK downloads |
| medium.com/@adnanmasood | https://medium.com/@adnanmasood/inside-the-fractured-world-of-ai-agent-marketplaces-da80e7e03dd0 | Five distribution channel types; less than 5% of MCP servers monetized |
| workos.com | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | MCP now Linux Foundation standard; AWS/Cloudflare/Google production commitments |
| registry.modelcontextprotocol.io | https://registry.modelcontextprotocol.io/ | Official MCP registry: 9,652 servers |
| github.com/agentic-community | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway with OAuth, tool discovery, Keycloak/Entra integration |
| sre.azure.com | https://sre.azure.com/docs/capabilities/plugin-marketplace | Azure SRE Agent plugin marketplace using SKILL.md format with SHA-256 verification |
| agensi.io | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Plugin marketplace creation guide |
| workos.com | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | MCP enterprise overview |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | 101 official plugins + 68 partner plugins from Supabase, Figma, Vercel, Linear, Sentry, Stripe |
| github.com/api-evangelist | https://github.com/api-evangelist/smithery-ai | Smithery profiled: MCP registry + hosting, 7,000+ servers |
| github.com/zavora-ai | https://github.com/zavora-ai/mcp-registry | Enterprise MCP registry for ADK-Rust with tool discovery, allow-lists, health, audit |
| docs.litellm.ai | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | LiteLLM Claude Code Plugin Marketplace tutorial for enterprise deployment |

---

## Stats Block

```
├─ 🟠 Reddit: 2 threads │ n/a upvotes (RSS-only) │ n/a comments
├─ 🔵 X: 16 posts │ 2,359 likes │ 193 reposts
├─ 🦋 Bluesky: 12 posts │ 86 likes │ 6 reposts
├─ 🐙 GitHub: 18 items │ 133 reactions │ 213 comments
├─ 🌐 Web: 28 pages (15 engine + 13 supplemental)
└─ 🗣️ Top voices: @AnthropicAI, @jefferyharrell.bsky.social, @_bemax │ r/ClaudeAI, r/artificial
```

---

## Data Gaps

- **Reddit (significant gap):** The public Reddit API returned 403 errors on all direct search calls, and ScrapeCreators returned 402 (Payment Required). Only 2 threads were retrieved via RSS fallback with no upvote/comment data. r/ClaudeAI is a highly active community on this topic; this is the biggest coverage hole.
- **Hacker News (complete gap):** All HN searches returned HTTP 400 Bad Request errors. HN has active Claude Code discussions (evidence: Bluesky @hackernewsbot.bsky.social linked one). Zero data retrieved.
- **YouTube (complete gap):** yt-dlp returned zero results on all 8 query variants; ScrapeCreators YouTube returned 402. Multiple YouTube tutorials on Claude Code skills/MCP exist but none reached the corpus.
- **TikTok/Instagram (complete gap):** ScrapeCreators returned 402 Payment Required on all calls. No social video content retrieved.
- **Polymarket:** No markets related to Claude Code skills, MCP adoption, or plugin ecosystem found. Not unexpected for a developer tool topic.
- **Recent freshness note:** Engine flagged that only 27 of 63 dated items are from the last 7 days. Roughly 57% of evidence is from May 20 - June 11, 43% from June 12-19.
- **Approximate coverage:** X and Bluesky developer conversations well covered (~70%); Reddit community discussion severely underrepresented (~10%); YouTube and TikTok at 0%; HN at 0%. Overall estimated coverage of available social signal: ~40%.

---

## Key Quotes

> "Since AI started blowing up, there's been a new hype layer every few months: 1. Chat 2. Connectors/MCP servers 3. Local runtimes & skills: Claude Code, Codex, Cursor 4. Agents & bots: OpenClaw, NanoBot, Hermes. Each one wraps the last in more autonomy. Each one burns more tokens. What's the next layer?" — [@_bemax](https://x.com/_bemax/status/2067525222106857858) on X

> "Claude Code isn't becoming a coding assistant. It's becoming an AI operating system for software development. One command: /plugin install claude-code-setup@claude-plugins-official. And Claude starts analyzing your project to recommend hooks for everything." — [@HeyAnjula](https://x.com/HeyAnjula/status/2067617186034917833) on X

> "Claude Code isn't 'smart' by default - it's smart about what you connect to it. Add MCP servers for the tools you actually use (DBs, APIs, automation, docs) and it goes from generic helper to teammate that knows your stack. The setup is the superpower." — [@OGstdioh](https://x.com/OGstdioh/status/2067597176855830574) on X

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "One skill. Just one. Install it once. Every time you ask Claude Code for something: it expands your prompt into a complete spec. THAT skill is worth more than 50 MCP servers." — [@jordanfjf02](https://x.com/jordanfjf02/status/2067670075205636274) on X (translated from Spanish)

> "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams. When teams have good skills, they're more likely to be successful when building agents." — [PostHog GitHub PR](https://github.com/PostHog/posthog/pull/64385) internal team rationale

> "People treat plugins, skills, and MCP servers as three options on the same menu, then get confused when the comparison doesn't quite work." — [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained)

> "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." — [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) on Bluesky

> "As the OpenClaw Skills ecosystem grows (800+ skills on ClawHub), understanding which skills depend on which becomes critical. Currently, there's no visual way to map SKILL.md 'use' dependencies across skills." — [openclaw/openclaw RFC](https://github.com/openclaw/openclaw/issues/88173) on GitHub

> "ai coding tools made the wrong thing weirdly comfortable: building polished software before you have pain, distribution, or a buyer. That used to be expensive enough to stop most people. Now you can burn a weekend with Codex, Claude Code, Cursor, MCP servers... and a cute demo that still has exactly $0 MRR." — [@0xCrash_](https://x.com/0xCrash_/status/2067565769672601748) on X
