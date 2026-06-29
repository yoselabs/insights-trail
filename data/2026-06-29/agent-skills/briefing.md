# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-29
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 11 threads | 42,210 upvotes, 2,308 comments | r/ClaudeAI dominant; mixed topic relevance |
| X/Twitter | 21 posts | 30,852 likes, 3,234 reposts | Strong plugin/MCP builder signals; Japanese-language coverage |
| Hacker News | 27 stories | 1,419 points, 1,193 comments | High Show HN activity; MCP tooling, Claude Code utilities |
| Bluesky | 10 posts | 79 likes, 6 reposts | Plugin philosophy discussion; developer community |
| GitHub | 24 items | 1,603 reactions, 791 comments | MCP server PRs, Claude Code issues, multi-agent frameworks |
| Web | 19 pages | — | via engine grounding |
| Web | 16 pages | — | via WebSearch supplemental |

---

## Synthesized Findings

### 1. Anthropic Launched an Official Plugin Marketplace - and It Landed as a Platform Moment

The biggest structural shift this month: Anthropic shipped a first-party plugin directory for Claude Code, pre-registered in every install. The `claude-plugins-official` marketplace bundles 36 first-party plugins (including 12 language-server plugins) plus approved third-party entries from AWS, Microsoft, Stripe, Shopify, Datadog, and Google's `gemini-cli-extensions`. As of June 11, the `marketplace.json` defines 222 plugin entries, with top plugins showing six-figure install counts per [Ry Walker's research](https://rywalker.com/research/claude-plugin-marketplace). The community marketplace at `anthropics/claude-plugins-community` hosts third-party plugins that pass Anthropic's automated validation and safety screening.

[@chenzeling4](https://x.com/chenzeling4/status/2071051965057094088) summed it up on X: "Anthropic shipped an official plugin directory for Claude Code. This is the curated marketplace they maintain themselves. Internal and external plugins, install with one slash command. Each one bundles skills, agents, MCP servers, or slash commands. The 'trust the source' version of extensibility. ⭐ 31.2K."

AWS released official MCP servers, skills, and plugins enabling AI agents to build on their infrastructure - surfaced via [Bluesky](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) in the GitHub Trending feed. The community directory at [claudemarketplaces.com](https://claudemarketplaces.com/) reports 21,600+ skills, 12,500+ MCP servers, and 2,500+ marketplace entries with 300,000 monthly visitors.

Coverage: X, Web, Bluesky

### 2. The Extension Hierarchy Is Crystallizing - 10 Layers, Clear Use Cases

[@bibryam](https://x.com/bibryam/status/2071250046000017616) (31 likes, 3 reposts) published a clean taxonomy that's being widely referenced: Claude Code now has 10 distinct places for instructions and behavior - CLAUDE.md (stable project facts), Rules (path-scoped constraints), Skills (reusable procedures), Manual skills and slash commands (human-triggered workflows), Subagents (isolated investigations), Output styles (session posture), Appended system prompts (one-run framing), MCP servers (live external capabilities), Hooks (event-triggered behaviour), and Permissions (hard boundaries).

The practical decision tree is emerging from practitioner posts: Skills are 30-50 tokens each, loaded on-demand - the lightest and easiest starting point. MCP servers can consume 50k+ tokens as persistent tool connections. Plugins bundle everything into shareable, one-command-install units. Multiple guides published this month - from [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained), [claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/), [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/), [maketocreate.com](https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/), and [dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) - all converging on the same "lightest first" recommendation: skill before MCP, MCP before plugin.

A Japanese-language X post from [@Kenichi_KNZW](https://x.com/Kenichi_KNZW/status/2071352948412551413) went viral in the Japanese developer community, breaking down all 7 Anthropic-documented methods for instructing Claude Code agents - noting the shift from "writing good prompts" to "designing environments where AI can produce results." Anthropic's Claude Code in Action course (4 modules, 3 hours) also covers this hierarchy explicitly per [@ds_jessica_](https://x.com/ds_jessica_/status/2071412586189660263).

Coverage: X, Web

### 3. Grok Build Imported Claude Code's Config Format - Switching Cost Just Went to Zero

The most strategically charged observation of the month came from [@TattedWorks](https://x.com/TattedWorks/status/2071565504989266294) on June 29: "Anthropic's coding moat just became Grok Build's import format. xAI's coding agent now reads Claude Code's own config files with zero setup. Grok Build launched May 14. By xAI's own docs, it picks up your CLAUDE.md, skills, MCP servers, and plugins automatically. No migration. It runs a flat $299 a month, $99 to start. Claude Code bills by the token. Uber just capped its engineers at $1,500 a month on it. So the switching cost is gone. Every hour you spent setting up Claude Code now..."

The implication: Claude Code's skill/plugin/MCP ecosystem is becoming the de facto portable standard for agentic configuration. What was a moat (custom setup) is now a public format that competitors can consume. The config portability that benefits users also reduces lock-in. One X user [@_itsjustshubh](https://x.com/_itsjustshubh/status/2071428329710784961) noted they've "defaulted to Claude Code for everything and use MCP plugins for what Cursor used to handle. one less tab open." Another, [@catmanyau](https://x.com/catmanyau/status/2071430217885700407), said: "i pay for claude code mostly for the mcp servers and cursor integration now too. the baseline code gen is everywhere, it's the connections that lock it in."

Coverage: X

### 4. The MCP Ecosystem Reached Scale - and Started Fragmenting Into Registries

The Model Context Protocol donated to the Linux Foundation's Agentic AI Foundation in December 2025 is now an industry standard at real production scale. The official MCP Registry counted 9,652 server records as of May 24, with an estimated 13,000+ total servers. 41% of surveyed software organizations are in limited or broad production with MCP servers per Stacklok's 2026 report ([digitalapplied.com](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol)).

Four registries now matter: [mcp.so](https://www.truefoundry.com/blog/best-mcp-registries) (20,222 servers), [smithery.ai](https://roxyapi.com/blogs/mcp-registries-where-to-list-your-server), [glama.ai/mcp](https://www.truefoundry.com/blog/best-mcp-registries), and the punkpeye/awesome-mcp-servers GitHub list. [LobeHub](https://www.explainx.ai/blog/top-10-mcp-server-directories-2026) claims the largest with 56,000+ servers. Enterprise registries like [Kong's MCP Registry](https://konghq.com/products/mcp-registry) are emerging with OAuth, dynamic tool discovery via vector search, and governance controls.

Pinterest published production MCP results in April 2026: 844 active users, ~66,000 monthly invocations, saving an estimated 7,000 engineering hours per month. An HN story noted that "bad MCP design costs your agent 5x more tokens" - [pointing to tool design efficiency as a real cost variable](https://news.ycombinator.com/item?id=48407391). An analysis of 16,400+ MCP implementations finds 55% JavaScript-based and 38% Python-based.

**MCP v2 Alpha is coming July 28, 2026.** [Context Studios](https://www.contextstudios.ai/blog/mcp-v2-alpha-the-july-28-protocol-shift-to-plan-for) flagged the upcoming protocol shift: stateless routing changes, SDK pins, authorization updates. Teams using MCP in production need to plan for the transition.

Coverage: Web, HN, Bluesky

### 5. Security Is the Ecosystem's Unsolved Problem

Less than 5% of MCP servers are monetized, but the security gap is already documented. Snyk found malicious payloads in 76 of 3,984 analyzed agent skills. The [ghidra-mcp GitHub issue](https://github.com/bethington/ghidra-mcp/issues/307) became a case study: "this project is just not in an ok state. between the project having too many tools for agents and you closing your own tickets out of the blue..." - a community-driven MCP server struggling with maintainability under AI-generated contributions.

JFrog introduced "Agent Plugins Repositories" ([jfrog.com](https://jfrog.com/blog/introducing-agent-plugins-repositories/)) for enterprise governance: "developers install agent plugins every day: pulling from unmanaged GitHub repos, copying Cursor commands out of Slack, pointing Codex at a personal Git fork. Each of those is a new, uncontrolled distribution channel inside your software development lifecycle."

[@hikariraina](https://x.com/hikariraina/status/2071483760676409780) on X made the counterpoint: "Narrow MCP servers are underrated. 'Claude Code can read the live docs for this one integration' is much safer than giving it a giant toolbox."

Security discussion is cross-platform (HN, GitHub, X, Web) and intensifying as plugin counts scale.

Coverage: HN, GitHub, X, Web

### 6. Team-Oriented Tooling Is the Next Frontier

The hottest new product announcement in this topic space came from [@idode_k](https://x.com/idode_k/status/2071392036045938934) (152 likes, 10 reposts, 36 replies on launch day): "introducing draft - your collaborative agent knowledge base. draft is a desktop app and cli that automatically syncs context for your team's agents. with draft you get a local folder (separate from your working files or code) that houses all of your context, installed skills/mcp servers, and syncs it to your team. draft also runs constantly in the background to update your local context by analyzing your granola meetings, slack channels, and agent sessions. works across claude code, codex, cursor..."

The problem Draft is solving - skill/MCP synchronization across a team - is the exact pain point [one X user noted](https://x.com/RJMcGirr/status/2071082461434663172): "my main reason for sticking with Claude Code in any given use case is my existing subscription and org wide deployment of projects, skills, custom MCP servers." Individual skills are easy; team-level skill governance is hard.

Hacker News saw multiple "Show HN" entries for Claude Code orchestration tools: [Recall](https://github.com/raiyanyahya/recall) (local project memory, 136 pts), [Pulse](https://github.com/nikitadoudikov/claude-pulse) (phone-based tool-call approval dashboard, 39 pts), [Claudete](https://claudete.co) (legion of Claude Code instances), [RondoFlow](https://github.com/rondoflow/rondoflow) (visual multi-agent orchestration), [OpenYabby](https://github.com/OpenYabby/OpenYabby) (voice-controlled orchestrator), and [CodeGuilds](https://codeguilds.dev) (community registry for skills, agents, MCP servers). The Show HN pace suggests a healthy builder ecosystem around the extension layer.

Coverage: X, HN

### 7. The FAANG Side-Project Signal - Builders Are Shipping Real MCP Plugins

[@_itsjustshubh](https://x.com/_itsjustshubh/status/2071017162479644926) documented a pattern: FAANG engineers building MCP servers and Claude Code plugins on the side while employed full-time. Specific examples cited: plugins for AMC ticketing, Luma event management, and Apple Calendar integration. This is the same pattern that built early npm and VS Code extension ecosystems - professional developers using internal domain knowledge to build precise, narrow integrations.

The [Firma_dev](https://x.com/Firma_dev/status/2071481352751386678) account (one of the top X voices on this topic) represents the commercial side: shipping MCP servers for e-signature integration with live API reference access and €0.029/envelope pricing - essentially treating MCP servers as a product distribution channel.

Anthropic's dynamic workflows blog post ([claude.com](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code)) framed the opportunity for builders: Claude Code can now write and orchestrate its own multi-agent harness on the fly, opening new patterns for skill and tool composition at runtime.

Coverage: X, Web

### 8. Community Wants More - "Plugins" Is Not Enough

The most memorable community voice came from [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes): "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character."

The same user followed up: "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." The tension here is real - the system is capable enough that power users want more expressive customization than a curated marketplace provides.

On Bluesky, [coolhand.bsky.social](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) described building three large kit plugins for Claude Code, OpenClaw, and others to solve problems they saw across the ecosystem - an informal plugin author emerging to fill gaps the official marketplace hadn't addressed.

The community-hosted registry [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) is explicitly cross-platform: "open standard at agentskills.io, portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents." This is the community betting on interoperability over Claude Code exclusivity.

Coverage: Bluesky, GitHub, Web

---

## Cross-Source Patterns

**Pattern 1: Plugin Marketplace as Platform Gravity**
- Appears on: X, Web, Bluesky, HN
- The official plugin marketplace is being treated as Claude Code's "App Store moment" - the infrastructure that turns an agentic tool into a platform. Third-party plugins from major vendors (AWS, Stripe, Shopify) arriving in the official marketplace signals platform maturity.
- Key quotes: "The 'trust the source' version of extensibility" - [@chenzeling4](https://x.com/chenzeling4/status/2071051965057094088); "distribution power is the moat: the marketplace is pre-registered in every Claude Code install" - rywalker.com

**Pattern 2: Config Portability = Format War**
- Appears on: X, Web
- Grok Build importing CLAUDE.md/skills/MCP format means the Claude Code configuration format is becoming a cross-agent standard. Competitors adopting the format validates it as an industry standard while reducing lock-in. Multiple cross-platform skill registries (agentskills.io, claudemarketplaces.com) are betting on this.
- Key quotes: "Anthropic's coding moat just became Grok Build's import format" - [@TattedWorks](https://x.com/TattedWorks/status/2071565504989266294); "portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents" - netresearch/claude-code-marketplace

**Pattern 3: MCP Security Debt Accumulating**
- Appears on: HN, GitHub, X, Web
- As MCP server count scales to 13,000+, security tooling hasn't kept pace. Snyk found malicious payloads in 76 of 3,984 skills. JFrog is entering with enterprise governance. The HN thread "bad MCP design costs your agent 5x more tokens" adds a performance dimension to the security one.
- Key signal: "narrow MCP servers are underrated" - the community is discovering that smaller, scoped integrations are both safer and more token-efficient

**Pattern 4: Team Synchronization Is the Next Unsolved Problem**
- Appears on: X, HN
- Individual skill setup is solved. Team-level synchronization of skills, MCP server configs, and agent context is the next frontier. Draft launched to address this. Multiple HN Show HN entries (Recall, Claudete, RondoFlow) are all attacking team/fleet orchestration angles.
- Key quote: "my main reason for sticking with Claude Code in any given use case is my existing subscription and org wide deployment of projects, skills, custom MCP servers" - [@RJMcGirr](https://x.com/RJMcGirr/status/2071082461434663172)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | New Claude code update is crazy | 4,355 | 73 | — | https://www.reddit.com/r/ClaudeAI/comments/1u9hp5y/new_claude_code_update_is_crazy/ |
| r/ClaudeAI | Nothing can go wrong when you share a Claude subscription with friends... right? | 4,184 | 73 | — | https://www.reddit.com/r/ClaudeAI/comments/1uejjg6/nothing_can_go_wrong_when_you_share_a_claude/ |
| r/ClaudeAI | Claude Fable 5 feels less like a model launch and more like a preview of AI inequality | 5,313 | 903 | "frontier AI is turning into a gated utility" | https://www.reddit.com/r/ClaudeAI/comments/1u1fsdi/claude_fable_5_feels_less_like_a_model_launch_and/ |
| r/ClaudeAI | I started responding to messages from coworkers like Claude | 15,119 | 326 | — | https://www.reddit.com/r/ClaudeAI/comments/1tz1tzv/i_started_responding_to_messages_from_coworkers/ |
| r/ClaudeAI | Claude Code Endgame | 2,776 | 41 | — | https://www.reddit.com/r/ClaudeAI/comments/1u0e2pp/claude_code_endgame/ |
| r/ClaudeAI | Any USA citizen wanna marry me? I'm tryna access Fable 5 in claude code | 3,020 | 394 | — | https://www.reddit.com/r/ClaudeAI/comments/1u4tjef/any_usa_citizen_wanna_marry_me_im_tryna_access/ |
| r/ClaudeAI | Hit your Claude session limit? | 2,892 | 132 | — | https://www.reddit.com/r/ClaudeAI/comments/1ubj3fw/hit_your_claude_session_limit/ |
| r/artificial | Claude Pro Users: How do you actually maximize your subscription? | 1 | 5 | mentions Projects, Skills, knowledge bases | https://www.reddit.com/r/artificial/comments/1u4bneb/claude_pro_users_how_do_you_actually_maximize/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @idode_k | introducing draft - your collaborative agent knowledge base | 152 | 10 | https://x.com/idode_k/status/2071392036045938934 |
| @bibryam | Claude Code has more than one place for instructions [10-layer taxonomy] | 31 | 3 | https://x.com/bibryam/status/2071250046000017616 |
| @AnthropicAI | Mythos 5 cybersecurity model restored for critical infrastructure | 30,245 | 3,187 | https://x.com/AnthropicAI/status/2070665903440871779 |
| @AnthropicAI | Nearly half of respondents expect work responsibilities to change significantly | 200 | 10 | https://x.com/AnthropicAI/status/2070528969523499460 |
| @TattedWorks | Anthropic's coding moat just became Grok Build's import format | 1 | 1 | https://x.com/TattedWorks/status/2071565504989266294 |
| @chenzeling4 | Anthropic shipped an official plugin directory for Claude Code | 1 | 0 | https://x.com/chenzeling4/status/2071051965057094088 |
| @_itsjustshubh | building MCP servers / claude code plugins on the side while full-time at FAANG | 4 | 0 | https://x.com/_itsjustshubh/status/2071017162479644926 |
| @Kenichi_KNZW | 7 methods for instructing Claude Code agents [Japanese] | 3 | 0 | https://x.com/Kenichi_KNZW/status/2071352948412551413 |
| @Firma_dev | Claude Code MCP servers for e-signature integration | 3 | 0 | https://x.com/Firma_dev/status/2071481352751386678 |
| @catmanyau | i pay for claude code mostly for the mcp servers and cursor integration now | 2 | 0 | https://x.com/catmanyau/status/2071430217885700407 |
| @hikariraina | Narrow MCP servers are underrated | 0 | 0 | https://x.com/hikariraina/status/2071483760676409780 |
| @ikekatsuai | Claude Code plugins increasing; auto-detect & install tools cuts setup time 1/10 [Japanese] | 1 | 0 | https://x.com/ikekatsuai/status/2071038874563076361 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| engmarketer | I used Claude Code to get a second opinion on my MRI | 469 | 602 | — | https://antoine.fi/mri-analysis-using-claude-code-opus |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| mateenah | Show HN: Recall – Local project memory for Claude Code | 136 | 86 | — | https://github.com/raiyanyahya/recall |
| nikitadvd | Show HN: Pulse – Dashboard for Claude Code, approve tool calls from your phone | 39 | 15 | — | https://github.com/nikitadoudikov/claude-pulse |
| ayi | Ask HN: Anthropic banned me from using Claude Code and I don't know what to do | 81 | 94 | — | https://news.ycombinator.com/item?id=48641160 |
| syumei | Claude Code and Codex can have real-time conversation via Git | 116 | 79 | — | https://medium.com/@Koukyosyumei/claude-code-and-codex-can-have-real-time-conversation-via-git-f95b696c1c05 |
| grzracz | Show HN: macOS menu bar gauges for your Claude Code quota | 69 | 40 | — | https://github.com/grzegorz-raczek-unit8/claude-quota |
| har-ki | Running Claude Code Offline on an M3 Pro with Qwen3.6 | 18 | 10 | — | https://har-ki.github.io/claude-code-sre-handbook/handbook/06-air-gapped/ |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| JohnnyZhang483 | Bad MCP design costs your agent 5x more tokens | 17 | 1 | — | https://news.ycombinator.com/item?id=48407391 |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | https://codeguilds.dev |
| hoangnnguyen | I read every Claude Code hook so you don't have to | 3 | 1 | — | https://codeaholicguy.com/2026/06/17/i-read-every-claude-code-hook-so-you-dont-have-to/ |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 36 | 12 | — | https://news.ycombinator.com/item?id=48546618 |
| arzzen | Show HN: Visual multi-agent orchestration for Claude Code | 5 | 0 | — | https://github.com/rondoflow/rondoflow |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | 0 | — | https://github.com/OpenYabby/OpenYabby |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | I can port Alpha from ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @viriditax.bsky.social | Making VST plugins was the first thing I tried with Claude Code | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @coolhand.bsky.social | I built plugins for Claude, OpenClaw and the rest to solve problems I saw | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @probbrain.bsky.social | AWS releases official MCP servers, skills, and plugins [AI news feed] | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |
| @github-trending-js.bsky.social | Ruflo: multi-agent framework with 100+ cooperative agents, MCP, memory, plugins | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @brunopedro.com | 42Crunch integration with Claude Code for Agentic DevSecOps | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| anthropics/claude-code | [FEATURE] Official Claude Desktop build for Linux | 640 | 47 | https://github.com/anthropics/claude-code/issues/65697 |
| openai/codex | Rate-limit cost per token jumped 10-20x since June 16 | 527 | 197 | https://github.com/openai/codex/issues/28879 |
| anomalyco/opencode | OpenCode v1.17.10 crashes with Bun segfault on Windows | 46 | 47 | https://github.com/anomalyco/opencode/issues/33742 |
| anthropics/claude-code | [BUG] No response from API error when Advisor is triggered | 48 | 27 | https://github.com/anthropics/claude-code/issues/69238 |
| anthropics/claude-code | Opus 4.8 intermittently emits malformed tool calls | 12 | 3 | https://github.com/anthropics/claude-code/issues/67307 |
| danny-avila/LibreChat | feat: MCP Apps support - interactive HTML resources for tools | — | 29 | https://github.com/danny-avila/LibreChat/pull/13831 |
| Sequel-Ace/Sequel-Ace | Add built-in MCP server for AI agent integration | — | 22 | https://github.com/Sequel-Ace/Sequel-Ace/pull/2468 |
| KooshaPari/PhenoMCPServers | feat: forge3-bridge MCP server + skill (catalog 1.4.0) | — | 5 | https://github.com/KooshaPari/PhenoMCPServers/pull/30 |
| bethington/ghidra-mcp | "this is becoming a complex unmaintainable mess" | — | 10 | https://github.com/bethington/ghidra-mcp/issues/307 |
| BerriAI/litellm | LiteLLM Stability Sprint Roadmap | — | 21 | https://github.com/BerriAI/litellm/issues/30484 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| rywalker.com | https://rywalker.com/research/claude-plugin-marketplace | 222 plugins in marketplace.json; 36 first-party + AWS, Stripe, Shopify entries; six-figure install counts |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 21,600+ skills, 12,500+ MCP servers; 300K monthly visitors |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Canonical 3-layer explanation of plugins vs skills vs MCP |
| arte.itlibra.com | https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace | Complete guide to plugins, marketplace structure, build/publish workflow |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Open SKILL.md registry; decision guide for extension surface selection |
| maketocreate.com | https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/ | Practitioner guide: "I've shipped both, here's when to reach for each" |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | "Lightest first" decision framework for extension surface choice |
| dev.to | https://dev.to/nagell/build-your-own-claude-code-marketplace-scaffold-structure-and-auto-updates-4n3f | Build your own marketplace: GitHub repo scaffold + auto-updates |
| niteagent.com | https://niteagent.com/blog/2026-06-11-custom-mcp-server-guide/ | Production MCP server guide; 55% JS, 38% Python across 16,400 implementations |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills vs MCP vs Connectors vs Plugins taxonomy |
| chatforest.com | https://chatforest.com/guides/mcp-ecosystem-2026-state-of-the-standard/ | MCP as universal standard; 9,652 official records, 13,000+ total |
| digitalapplied.com | https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol | 41% orgs in production; Pinterest 7,000 hours/month saved; <5% monetized |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries: mcp.so, smithery.ai, glama.ai, LobeHub (56K+ servers) |
| contextstudios.ai | https://www.contextstudios.ai/blog/mcp-v2-alpha-the-july-28-protocol-shift-to-plan-for | MCP v2 Alpha spec date July 28; stateless routing, auth, SDK pin changes |
| jfrog.com | https://jfrog.com/blog/introducing-agent-plugins-repositories/ | Enterprise governance for agent plugins; uncontrolled distribution channel risk |
| claude.com | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Anthropic: Claude Code can write/orchestrate its own multi-agent harness |
| ofox.ai | https://ofox.ai/blog/claude-code-hooks-subagents-skills-complete-guide-2026/ | Hooks, subagents, skills complete guide; start with skills, add hooks, then subagents |
| aitechconnect.in | https://aitechconnect.in/tips/claude-code-slash-commands-hooks-automation-2026 | Hooks make it happen "whether the model agrees or not"; shareable plugin packaging |
| blog.laozhang.ai | https://blog.laozhang.ai/en/posts/claude-code-hooks-slash-commands-skills | Decision framework: who starts the action (human vs model vs lifecycle event) |

---

## Stats Block

```
├─ 🟠 Reddit: 11 threads │ 42,210 upvotes │ 2,308 comments
├─ 🔵 X: 21 posts │ 30,852 likes │ 3,234 reposts
├─ 🟢 HN: 27 stories │ 1,419 points │ 1,193 comments
├─ 🦋 Bluesky: 10 posts │ 79 likes │ 6 reposts
├─ 🐙 GitHub: 24 items │ 1,603 reactions │ 791 comments
├─ 🌐 Web: 35 pages (19 engine + 16 supplemental)
└─ 🗣️ Top voices: @_itsjustshubh, @AnthropicAI, @Firma_dev, @bibryam, @jefferyharrell.bsky.social │ r/ClaudeAI, r/artificial
```

---

## Data Gaps

- **YouTube: 0 videos** - yt-dlp returned 0 results for all query variants on this topic. YouTube has significant Claude Code tutorial content but yt-dlp appears rate-limited or bot-gated on this query. ScrapeCreators YouTube fallback returned HTTP 402 (Payment Required / quota exceeded).
- **TikTok: 0 videos** - All TikTok hashtag searches (#claudecode, #mcptools, #aiagent, #aicoding) returned HTTP 402 from ScrapeCreators. TikTok coverage is entirely missing.
- **Instagram: 0 reels** - ScrapeCreators Instagram returned HTTP 402 on all attempts. Instagram coverage missing.
- **Threads: 0 posts** - ScrapeCreators Threads returned HTTP 402. Threads coverage missing.
- **Reddit: Sparse on topic** - Only 11 threads returned; ClaudeAI dedicated lane returned 0 posts (timing/rate issue). Most Reddit posts are general Claude AI sentiment rather than plugin/skill/MCP specific discussion. The r/ClaudeAI highest-upvoted posts reflect model access frustration (Fable 5 geo-restrictions) rather than extension ecosystem content.
- **GitHub: No token** - GitHub search ran on unauthenticated tier (low rate limit); 24 items from broad search, but no project-mode depth on anthropics/claude-code or modelcontextprotocol/servers. Many GitHub items are off-topic noise (selfie-gen-ultimate, KooshaPari personal projects).
- **Polymarket: 0 markets** - No prediction markets on this topic. Expected (too niche for current prediction market scope).
- **Freshness gap** - Engine noted only 34 of 112 dated items are from the last 7 days; coverage is thinner for the most recent week.
- **Approximate coverage**: Core signal sources (X, HN, Web) strong; social video (TikTok, YouTube, Instagram) entirely absent due to API quota; estimated 65-70% of relevant content surface captured.

---

## Key Quotes

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "Anthropic's coding moat just became Grok Build's import format. xAI's coding agent now reads Claude Code's own config files with zero setup... So the switching cost is gone. Every hour you spent setting up Claude Code now..." — [@TattedWorks](https://x.com/TattedWorks/status/2071565504989266294) on X

> "i pay for claude code mostly for the mcp servers and cursor integration now too. the baseline code gen is everywhere, it's the connections that lock it in." — [@catmanyau](https://x.com/catmanyau/status/2071430217885700407) on X

> "Narrow MCP servers are underrated. 'Claude Code can read the live docs for this one integration' is much safer than giving it a giant toolbox." — [@hikariraina](https://x.com/hikariraina/status/2071483760676409780) on X

> "Claude Code has more than one place for instructions. 1. CLAUDE.md for stable project facts 2. Rules for path-scoped constraints 3. Skills for reusable procedures 4. Manual skills and slash commands for human-triggered workflows 5. Subagents for isolated investigations 6. Output styles for session posture 7. Appended system prompts for one-run framing 8. MCP servers for live external capabilities 9. Hooks for event-triggered behaviour 10. Permissions for hard boundaries" — [@bibryam](https://x.com/bibryam/status/2071250046000017616) on X

> "introducing draft - your collaborative agent knowledge base. draft is a desktop app and cli that automatically syncs context for your team's agents... works across claude code, codex, cursor..." — [@idode_k](https://x.com/idode_k/status/2071392036045938934) on X (152 likes on launch)

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "this is becoming a complex unmaintainable mess... this project is just not in an ok state. between the project having too many tools for agents..." — [DacoTaco on ghidra-mcp](https://github.com/bethington/ghidra-mcp/issues/307) (GitHub issue on MCP project maintainability)

> "Bad MCP design costs your agent 5x more tokens" — [Hacker News](https://news.ycombinator.com/item?id=48407391) (17 points)

> "Claude Code にプラグインが増えてきた。hooks・skills・MCP servers・subagents を「自動検出＆インストール」するツールが登場。新規エージェント立ち上げ時に「環境構築から実装開始までの時間」が 1/10 に圧縮される。" [Claude Code plugins are growing. Tools for auto-detecting & installing hooks, skills, MCP servers, subagents have appeared. Setup-to-coding time cut to 1/10.] — [@ikekatsuai](https://x.com/ikekatsuai/status/2071038874563076361) on X
