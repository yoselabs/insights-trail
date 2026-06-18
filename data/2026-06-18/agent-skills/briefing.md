# Agent Skills & Claude Code Plugin Ecosystem — Daily Briefing
**Date:** 2026-06-18
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 3 threads | — upvotes, — comments | All r/ClaudeAI; no upvote data available |
| X/Twitter | 52 posts | 1,500 likes, 265 reposts | ~30 off-topic crypto/finance posts in corpus |
| Bluesky | 12 posts | 93 likes, 7 reposts | Developer-heavy; strong signal |
| GitHub | 5 items | 38 reactions, 18 comments | Issues + PRs across opencode, vercel-labs, cherry-studio |
| Web | 19 pages + 31 supplemental | — | Engine (19) + WebSearch supplements (31) |

---

## Synthesized Findings

### 1. The Extension Taxonomy Confusion: Which Layer to Use When

The single loudest conversation this month is a taxonomy problem: developers can't reliably distinguish when to reach for a Skill versus an MCP server versus a Hook versus a Plugin versus a Subagent. Multiple detailed explainers published in June 2026 signal that the confusion has hit critical mass. [Hidekazu Konishi's Extension Layer Decision Guide](https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html) (June 11) frames the layers as a deliberate stack: CLAUDE.md for context, Skills for repeatable procedures, MCP for external system access, Hooks for deterministic enforcement, Subagents for parallel/isolated work, and Plugins as the distribution wrapper. [Tygart Media's Skills vs MCP vs Connectors vs Plugins guide](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) (June 13) offers the simplest reduction: "Skills teach Claude how to do something. MCP gives Claude access to something." [DEV Community's "lightest first" piece](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) (June 8) adds a cost lens: start with a CLI, escalate to Skill if reusable, to MCP if cross-session, to Plugin only if distributing.

On X, [@AndrewK404 put it concisely](https://x.com/AndrewK404/status/2059732591222096368): "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." [AI Trove's explainer](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) goes deeper, covering LSP servers alongside the standard extension types. [Dogan Ucar's cheat sheet](https://dogan-ucar.de/en/claude-code-cheat-sheet-hooks-skills-plugins-claude-md-skill-md-agents-md-explained/) covers the full file hierarchy: CLAUDE.md, SKILL.md, AGENTS.md, settings.json, and how they interact. [AgentWay's MCP primer](https://agentway.dev/en/claudecode/mcp) uses the "USB for AI" frame that's gaining traction as a shorthand for the protocol.

Cross-platform: Web + X + Reddit + Bluesky all discussing this. The taxonomy clarity problem is the top signal in the corpus.

### 2. Token Overhead Backlash: The MCP Context Bloat Problem

The highest-engagement authentic signal in the corpus is a counter-narrative against plugin/MCP maximalism, driven primarily by [@regent0x_](https://x.com/regent0x_) who has turned MCP context overhead into a running critique. His [raspberry pi post](https://x.com/regent0x_/status/2059559047888507213) (125 likes, 21 reposts) is the most explicit: "$50 raspberry pi running AI in the palm of his hand - no plugins, no MCP servers, no 62,000 tokens of overhead - just ollama and a terminal - this guy saw that video and deleted everything from his $4,000 macbook." A follow-up [Macintosh Plus post](https://x.com/regent0x_/status/2058079320405332047) (49 likes) makes it generational: "his dad built a $2M company on a 1986 macintosh plus - no drivers, no plugins, no setup - just worked - 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free." His [Stop Installing Plugins guide](https://x.com/regent0x_/status/2057419591618302029) (315 likes, 43 reposts) is the single highest-liked on-topic post in the entire corpus.

Reddit backs this up with hard numbers. From [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/): "I checked my session transcripts: 187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate." The same subreddit has a [9-MCP-server confession](https://www.reddit.com/r/ClaudeAI/comments/1thmpoq/configured_9_mcp_servers_in_claude_code_over_4/): "Total tools across all of them: 142. What nobody warns you about: every one of those tool definitions lands in your context window before any user prompt has been sent." A [free CLI called gaal](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) was built specifically to sync CLAUDE.md, slash commands, MCP servers, and skills across machines - suggesting real friction in current tooling.

[@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550) (52 likes) offers the nuanced take, quoting MCP co-creator David Soria Parra of Anthropic: "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together."

Cross-platform: X + Reddit. Token bloat is the dominant practitioner concern.

### 3. MCP Server Ecosystem Explosion: 13,000+ Servers, GitHub as the Anchor

The MCP server ecosystem has scaled to a point where curation is the challenge, not availability. [QCode's ecosystem overview](https://www.qcode.cc/mcp-servers-ecosystem-2026) puts the count at 13,000+ servers. [Clarista's 2026 guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) and [Nimbalyst's rankings](https://nimbalyst.com/blog/best-claude-code-mcp-servers/) converge on the GitHub MCP as the highest-impact install for most developers ("turning Claude Code from a code generator into a participant in the issue and PR workflow"). The [official Anthropic MCP docs](https://code.claude.com/docs/en/mcp) remain the authoritative technical source.

The practitioner consensus documented in [Totalum's best-of-2026 list](https://www.totalum.app/blog/best-mcp-servers-2026) and [Septimlabs' configuration gist](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1): three to six servers is the sweet spot, with GitHub plus one or two project-specific servers as the day-one stack. [LLM Best Practices](https://llmbestpractices.com/ai-agents/claude-code-mcp) adds the session-vs-one-off heuristic: "prefer MCP tools over Bash when the integration will be used across sessions." [Developer Toolkit's MCP setup guide](https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/) (from mid-June) and [ComputingForGeeks](https://computingforgeeks.com/claude-code-mcp-servers-setup/) both show the four-tool triage pattern: check Sentry, look at the GitHub PR, query the database, update Jira - from one Claude Code session.

Enterprise MCPs are accelerating: Shopify (April 9), Meta (April 29), Higgsfield (April 30), and [42Crunch's enterprise DevSecOps plugin](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) for Claude Code were all announced within a tight window. Azure SRE Agent added a [plugin marketplace](https://sre.azure.com/docs/capabilities/plugin-marketplace) with SHA-256 content hashing for upstream skill verification.

Cross-platform: Web + Bluesky + Reddit.

### 4. Marketplace and Distribution Wars: 8 Marketplaces, SKILL.md as the Cross-Platform Standard

The marketplace layer has fragmented fast. [Agensi's full landscape breakdown](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026) counts eight major marketplaces competing in Q2 2026: Anthropic's Claude Skills directory (first-party, free), GPT Store (OpenAI, revenue share), community MCP Hubs, Hugging Face Spaces, and platform-specific registries (Replit, Vercel, Cloudflare). The [Rapid Claw guide](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026) calls out the fragmentation bluntly: "each has different economics, reviewing rules, and distribution dynamics that determine whether your agent ever gets used."

The format converging across all of them is SKILL.md - [Digital Applied confirms](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) it works across Claude Code, Codex CLI, Cursor, and Gemini CLI. Vercel is pushing a vendor-neutral step further with [open-plugin-spec](https://github.com/vercel-labs/open-plugin-spec/issues/5): "the convergence of .claude-plugin/ and .cursor-plugin/ into a vendor-neutral .plugin/plugin.json feels like exactly the right structural move." OpenCode (the open-source Claude alternative) has a [master issue for a unified marketplace](https://github.com/anomalyco/opencode/issues/28696) with 21 reactions.

Security is a real concern. [Zylos Research](https://zylos.ai/en/research/2026-03-09-ai-agent-marketplaces-distribution-channels/) found 1,184 malicious skills (~1 in 5 packages) in one major registry, alongside 135,000 instances exposed with insecure defaults. [Agensi's paid tier](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026) runs an 8-point security checklist before listing. [Navos Agent's comparison](https://www.navosagent.ai/en/blog/best-agent-skills-marketplaces) covers the seven leading marketplaces' security postures.

Discovery is called out as the primary failure mode. [Agensi's "Skills Marketplace: The New App Store" piece](https://www.agensi.io/learn/skills-marketplace-ai-agents): "shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction."

Community-built alternatives are appearing: [swissmarley/SkillsForAgents](https://github.com/swissmarley/SkillsForAgents) (MIT, one-line installer for Claude Code + Codex CLI + OpenCode), [CassianFlorin/skill-hub](https://github.com/CassianFlorin/skill-hub) (Go-based package manager for AI agent skills), and [linny006/agent-skill-registry](https://github.com/linny006/agent-skill-registry) (package registry with v0.1.0 release). [Jeremylongshore's 425-plugin repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) claims 425 plugins, 2,810 skills, and a ccpi CLI package manager.

Cross-platform: GitHub + Web + Bluesky.

### 5. Hooks for Deterministic Enforcement: The Production Pattern

Hooks are emerging as the production-grade answer to the question "how do I make Claude Code reliably do X every time?" The [official hooks guide](https://code.claude.com/docs/en/hooks-guide) covers the four lifecycle events (PreToolUse, PostToolUse, UserPromptSubmit, Stop/SubagentStop). [ClaudeFA.ST's complete guide](https://claudefa.st/blog/tools/hooks/hooks-guide) expands this to 12 lifecycle events. [Morph LLM's hooks reference](https://www.morphllm.com/claude-code-hooks) provides the full SDK surface.

The design rule stated across [Ofox](https://ofox.ai/blog/claude-code-hooks-subagents-skills-complete-guide-2026/), [Boring Bot](https://boringbot.substack.com/p/claude-code-skills-subagents-hooks), and [Developers Digest](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026): "add hooks when you need deterministic enforcement, use subagents when parallel work or context isolation matters." Concrete use cases: running tests before stopping, blocking edits to generated files, checking lint before a commit, requiring an issue ID in branch names, security scan after dependency changes. [SmartScope's advanced guide](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) covers 11 production patterns. [Build MVP Fast](https://buildmvpfast.com/blog/claude-dynamic-workflows-orchestration-subagents-2026) and [Mervin Praison's harness comparison](https://mer.vin/2026/05/agent-harnesses-compared-claude-code-workflows-pi-subagents-and-atomic/) evaluate Claude Code Workflows, Pi Subagents, and Atomic against each other.

[Munder Difflin's hive guide](https://munderdiffl.in/blog/mcp-and-skills-in-a-hive/) covers multi-agent MCP inheritance: "each agent is a real claude session in your project, it inherits exactly what a normal session would."

### 6. Real-world Plugin Creation: Domain Specialists Adopting the Model

Practitioners in non-obvious domains are discovering Claude Code's plugin authoring capabilities. [@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) (4 likes): "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting... Most likely older plugins could be ported over that way relatively easily." [@toyinariyo.bsky.social](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) points to Godot AI plugins compatible with Claude Code and Codex. [@viriditax.bsky.social](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227) built a VST audio plugin (bass octaver + autopan) on Christmas Day 2025 as a Claude Code demo.

[@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) (11 likes) is consolidating ad-hoc Claude Code work into a plugin: "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." In a [separate post](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes) he captures the community's deeper desire: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character."

[@coolhand.bsky.social](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) (12 likes) built plugin kits for both Claude and OpenClaw. [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) promotes the ECC bundle: "63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together."

A [GitHub bug report](https://github.com/anthropics/claude-code/issues/61491) on the official anthropics/claude-code repo shows a real rough edge: Claude Code hallucinated a "fan out subagents" slash command that doesn't exist, based on documentation describing the pattern abstractly.

### 7. Skill Discovery, Learning Resources, and Community Ecosystem

Multiple high-engagement X posts are Chinese-language "20 GitHub repos to master Claude" threads. [@0xluffy_eth](https://x.com/0xluffy_eth/status/2057719369137037793) (144 likes, 74 replies) and [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2065225329573327356) (37 likes) both circulate the same canonical list: Claude Code, Claude Cookbooks, Claude Quickstarts, Claude Desktop Extensions, Awesome Claude Code, Awesome MCP Servers, SuperClaude Framework, Claude Code Router, Claude Task Master, Claude Engineer. [@ChrisSlacker](https://x.com/ChrisSlacker/status/2057655698688029139) (40 likes) and [@mimu_ai1](https://x.com/mimu_ai1/status/2056998596072063023) (25 likes) run similar lists. These represent the global developer learning pathway into the ecosystem.

The French tech community is also engaged: [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) (Bluesky) curated "Top 13 skills et plugins Claude Code qui ont marqué 2026" - including a skill that cuts 63% of output tokens, one that replays sessions like a video, and one that turns a codebase into an explorable graph. [@humancoders.com](https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p) amplified the list. The Hacker News bot on Bluesky logged a [discussion thread](https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p) titled "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs."

On certification: [@ds_serena_](https://x.com/ds_serena_/status/2060985378723500048) promotes an Anthropic-backed certificate program specifically covering Claude Code hooks, MCP servers, and SDK extensions.

Key learning resources surfaced via WebSearch: [ClaudeKit's Skills vs Custom Slash Commands guide](https://getclaudekit.com/blog/guide/mechanics/custom-skills-vs-commands) (custom slash commands have merged into skills in v2.1.128+), [Hidekazu Konishi's Skills Complete Guide](https://hidekazu-konishi.com/entry/claude_code_skills_complete_guide.html) (June 14), [AI Architects' plugin explainer](https://theaiarchitects.com/blog/claude-plugins), [Groundy's official ecosystem explainer](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/), and [Claude's official plugin discovery docs](https://code.claude.com/docs/en/discover-plugins).

---

## Cross-Source Patterns

### Pattern 1: Token Overhead is the #1 Practitioner Pain Point
- **Platforms:** X (125-like raspberry pi post, 315-like "stop installing plugins"), Reddit (9-MCP confession, 8k token waste thread)
- X from [@regent0x_](https://x.com/regent0x_/status/2059559047888507213): "no plugins, no MCP servers, no 62,000 tokens of overhead - just ollama and a terminal"
- Reddit from [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/): "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted"

### Pattern 2: "Which Extension to Use When" is the #1 Knowledge Gap
- **Platforms:** Web (6+ explainer guides published in May-June), Reddit (r/ClaudeAI), X, Bluesky
- Multiple independent content creators published the same explainer in the same month - a reliable signal that confusion has hit critical mass
- Key quote from [Tygart Media](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/): "Skills teach Claude how to do something; MCP gives Claude access to something"

### Pattern 3: Plugins as Consolidation Layer
- **Platforms:** Bluesky + GitHub
- [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22): "I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."
- [Vercel open-plugin-spec GitHub issue](https://github.com/vercel-labs/open-plugin-spec/issues/5): push for vendor-neutral .plugin/plugin.json as the canonical format

### Pattern 4: Minimalist vs Maximalist Setup Tension
- **Platforms:** X + Reddit + Bluesky
- Counter-movement: $50 Raspberry Pi running local ollama vs $4,000 MacBook with 23 plugins, 8 skills, 5 MCP servers
- Reaction from [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thmpoq/configured_9_mcp_servers_in_claude_code_over_4/): heavy MCP setup led to 142 tools in context before first prompt

### Pattern 5: Chinese Developer Community Driving Ecosystem Discovery
- **Platforms:** X (3 separate high-engagement threads listing 15-20 Claude GitHub repos)
- [@0xluffy_eth](https://x.com/0xluffy_eth/status/2057719369137037793) (144 likes), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2065225329573327356) (37 likes), [@ChrisSlacker](https://x.com/ChrisSlacker/status/2057655698688029139) (40 likes)
- These are the highest-engagement organic skill discovery posts in the corpus

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | — | — | "if you use Claude Code alongside any other coding agent, same project means different rules filename per agent" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) |
| r/ClaudeAI | Using Claude Code? You're probably wasting ~8k tokens per session on unused skills. I built a CLI to fix it. | — | — | "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) |
| r/ClaudeAI | Configured 9 MCP servers in Claude Code over 4 months. Here's the truth nobody tells you about MCP context bloat. | — | — | "Total tools across all of them: 142. What nobody warns you about: every one of those tool definitions lands in your context window" | [link](https://www.reddit.com/r/ClaudeAI/comments/1thmpoq/configured_9_mcp_servers_in_claude_code_over_4/) |

**X/Twitter** (on-topic posts):
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @regent0x_ | "Stop Installing Plugins on Claude Code - The Ultimate Guide" | 315 | 43 | [link](https://x.com/regent0x_/status/2057419591618302029) |
| @regent0x_ | "$50 raspberry pi... no plugins, no MCP servers, no 62,000 tokens of overhead - just ollama and a terminal" | 125 | 21 | [link](https://x.com/regent0x_/status/2059559047888507213) |
| @0xluffy_eth | "20 GitHub repos to learn Claude... Claude Code, Claude Cookbooks, Awesome MCP Servers, SuperClaude Framework..." | 144 | 53 | [link](https://x.com/0xluffy_eth/status/2057719369137037793) |
| @pauliusztin_ | "The best agents use all of it - skills, CLI, MCP - together" (quoting Anthropic MCP co-creator) | 52 | 7 | [link](https://x.com/pauliusztin_/status/2063236967987298550) |
| @regent0x_ | "his dad built a $2M company on a 1986 macintosh plus - no drivers, no setup... 40 years later his son needs 5 MCP servers" | 49 | 2 | [link](https://x.com/regent0x_/status/2058079320405332047) |
| @ChrisSlacker | "20 Claude GitHub repos that can completely change your life" | 40 | 14 | [link](https://x.com/ChrisSlacker/status/2057655698688029139) |
| @Crypto_QianXun | 20 GitHub repos for learning Claude (Chinese) | 37 | 12 | [link](https://x.com/Crypto_QianXun/status/2065225329573327356) |
| @ds_serena_ | "Master Claude Code: the CLI assistant changing dev workflows... Learn hooks, MCP servers & SDK extensions... Anthropic-backed certificate" | 6 | 4 | [link](https://x.com/ds_serena_/status/2060985378723500048) |
| @mimu_ai1 | "15 Claude GitHub Repos that can completely change your life" | 25 | 15 | [link](https://x.com/mimu_ai1/status/2056998596072063023) |
| @AndrewK404 | "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." | 2 | 1 | [link](https://x.com/AndrewK404/status/2059732591222096368) |
| @StevenMatison | Day 1: Claude Code | 1 | 1 | [link](https://x.com/StevenMatison/status/2066925481044099322) |

Off-topic / noise X posts also captured (entity-miss; included for URL completeness):
[@swarminged](https://x.com/swarminged/status/2066308024382497061) (3D agents/crypto), [@JackWoth98](https://x.com/JackWoth98/status/2065529819685871690) (Antigravity CLI), [@regent0x_](https://x.com/regent0x_/status/2066932423732887879) (local AI hardware business), [@regent0x_](https://x.com/regent0x_/status/2067271303057334620) (AMD/hardware), [@regent0x_](https://x.com/regent0x_/status/2067175584556351609) (hardware/cloud), [@regent0x_](https://x.com/regent0x_/status/2066514562342588421) (AMD CES hardware), [@regent0x_](https://x.com/regent0x_/status/2066473861516808674), [@regent0x_](https://x.com/regent0x_/status/2066473724111467003), [@regent0x_](https://x.com/regent0x_/status/2066473499162509527), [@regent0x_](https://x.com/regent0x_/status/2066473072345919938), [@regent0x_](https://x.com/regent0x_/status/2067365227088547870) (bro replies), [@frankhatfrei](https://x.com/frankhatfrei/status/2067353287574036789), [@saen_dev](https://x.com/saen_dev/status/2067302957347979332), [@saen_dev](https://x.com/saen_dev/status/2067517977415565472), [@DBigger60129](https://x.com/DBigger60129/status/2067399790804271144), [@swarminged](https://x.com/swarminged/status/2067402281247789366), [@swarminged](https://x.com/swarminged/status/2067398111803343250), [@swarminged](https://x.com/swarminged/status/2067399864679591937), [@swarminged](https://x.com/swarminged/status/2067402067669557652), [@swarminged](https://x.com/swarminged/status/2067397977266848140), [@swarminged](https://x.com/swarminged/status/2067398662616125736), [@swarminged](https://x.com/swarminged/status/2067408517200495047), [@swarminged](https://x.com/swarminged/status/2067459864679591937), [@SmartyCrypto195](https://x.com/SmartyCrypto195/status/2067452486785355847), [@John90133251](https://x.com/John90133251/status/2067399914988978224), [@John90133251](https://x.com/John90133251/status/2067399564143870064), [@swarminged](https://x.com/swarminged/status/2067398866828460332), [@HumanBeing1099](https://x.com/HumanBeing1099/status/2067460542705643626), [@nelsonnets](https://x.com/nelsonnets/status/2067488839854157936), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067505100663497169), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067431625676476551), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067431627253600281), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067468039898223079), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067467653883789768), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067472404117631109), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067469288408309883), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067472646644855052), [@Crypto_QianXun](https://x.com/Crypto_QianXun/status/2067472851725124063), [@zippy257](https://x.com/zippy257/status/2067365227088547870), [@rantingemilio](https://x.com/rantingemilio/status/2067390403339252207), [@GabrielVicto8](https://x.com/GabrielVicto8/status/2067367212965355625)

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." | 35 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) |
| @jefferyharrell.bsky.social | "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) |
| @coolhand.bsky.social | "I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" | 12 | [link](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) |
| @camilleroux.com | "Top 13 skills et plugins Claude Code qui ont marqué 2026 : celui qui coupe 63% des tokens de sortie, celui qui rejoue tes sessions comme une vidéo..." | 8 | [link](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) |
| @viriditax.bsky.social | "when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it" | 9 | [link](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227) |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 4 | [link](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — free, MIT-licensed" | 4 | [link](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | [link](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) |
| @brunopedro.com | "42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise." | 1 | [link](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) |
| @github-trending-js.bsky.social | "Ruflo is a multi-agent AI orchestration framework that extends Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation" | 1 | [link](https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b) |
| @hackernewsbot.bsky.social | "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | Discussion" | 1 | [link](https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p) |
| @humancoders.com | "Top 13 skills et plugins Claude Code qui ont marqué 2026 : audit de dette technique, réduction de tokens, best practices en prod" | 5 | [link](https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p) |

**GitHub:**
| Repo | Title | Reactions | Comments | Notable Quote | URL |
|------|-------|-----------|----------|--------------|-----|
| anomalyco/opencode | [FEATURE]: Plugin/Agent/Skills/etc marketplace | 21 | 4 | "Master issue for a unified OpenCode marketplace / registry / package distribution system" | [link](https://github.com/anomalyco/opencode/issues/28696) |
| vercel-labs/open-plugin-spec | Proposal: treat skill-only packages as plugins - .plugin/plugin.json as the single source of truth | 1 | 2 | "convergence of .claude-plugin/ and .cursor-plugin/ into a vendor-neutral .plugin/plugin.json feels like exactly the right structural move" | [link](https://github.com/vercel-labs/open-plugin-spec/issues/5) |
| CherryHQ/cherry-studio | [Feature]: Cherry CLI — Terminal Tool with Full GUI Feature Parity (V2) | 4 | 0 | "60+ providers, agent creation, knowledge bases, MCP servers... Manual configuration through the GUI is the dominant onboarding cost" | [link](https://github.com/CherryHQ/cherry-studio/issues/15244) |
| KooshaPari/portage | chore(portage): workflow hygiene — ubuntu-24.04, permissions | 0 | 5 | "Generated with Claude Code" (Claude Code generating its own CI workflow PRs) | [link](https://github.com/KooshaPari/portage/pull/428) |
| anthropics/claude-code | Claude Code suggests non-existent "fan out subagents" command | 0 | 7 | "No such slash command exists. The phrase appears to be a hallucinated command name based on the real 'fan-out subagents' pattern described in Anthropic's docs" | [link](https://github.com/anthropics/claude-code/issues/61491) |

**Web** (engine results):
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| hidekazu-konishi.com | [Extension Layer Decision Guide](https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html) | Definitive taxonomy: CLAUDE.md, Skills, Subagents, Hooks, MCP, Plugins as a layered stack |
| tygartmedia.com | [Claude Skills vs MCP vs Connectors vs Plugins](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) | Plain-English distinction: Skills = teach Claude HOW; MCP = give Claude ACCESS |
| dev.to | [Skill, MCP, Plugin, or CLI — lightest first](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) | Cost-based escalation framework: CLI < Skill < MCP < Plugin |
| munderdiffl.in | [MCP Servers and Skills Into a Hive of Agents](https://munderdiffl.in/blog/mcp-and-skills-in-a-hive/) | MCP inheritance in multi-agent harnesses |
| hidekazu-konishi.com | [Claude Code Skills Complete Guide](https://hidekazu-konishi.com/entry/claude_code_skills_complete_guide.html) | Creating, testing, and distributing agent skills |
| getclaudekit.com | [Skills vs Custom Slash Commands](https://getclaudekit.com/blog/guide/mechanics/custom-skills-vs-commands) | Custom slash commands merged into skills in v2.1.128 |
| sre.azure.com | [Plugin Marketplace - Azure SRE Agent](https://sre.azure.com/docs/capabilities/plugin-marketplace) | Enterprise marketplace: SHA-256 content hashing, one-click skill import |
| dogan-ucar.de | [Claude Code Cheat Sheet](https://dogan-ucar.de/en/claude-code-cheat-sheet-hooks-skills-plugins-claude-md-skill-md-agents-md-explained/) | Full file hierarchy: CLAUDE.md, SKILL.md, AGENTS.md, settings.json |
| agentway.dev | [Model Context Protocol](https://agentway.dev/en/claudecode/mcp) | "USB for AI" framing |
| ai-trove.com | [What are Claude Code plugins](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) | Covers LSP servers alongside standard extension types |
| llmbestpractices.com | [Claude Code MCP Integration](https://llmbestpractices.com/ai-agents/claude-code-mcp) | "prefer MCP tools over Bash when the integration will be used across sessions" |
| developertoolkit.ai | [MCP Setup: Connecting External Tools](https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/) | Four-tool triage pattern (Sentry + GitHub PR + DB + Jira from one session) |
| computingforgeeks.com | [Claude Code MCP Setup: Add Any Server](https://computingforgeeks.com/claude-code-mcp-servers-setup/) | Full setup guide: local, remote, scopes, tokens |
| theaiarchitects.com | [Claude Plugins Explained: Install, Create, and Distribute](https://theaiarchitects.com/blog/claude-plugins) | Plugin bundles skills, agents, hooks, and MCP servers into one installable package |
| github.com/swissmarley | [swissmarley/SkillsForAgents](https://github.com/swissmarley/SkillsForAgents) | Distributable marketplace for Claude Code + Codex CLI + OpenCode + Hermes |
| github.com/CassianFlorin | [CassianFlorin/skill-hub](https://github.com/CassianFlorin/skill-hub) | Go-based package manager for AI agent skills |
| github.com/linny006 | [linny006/agent-skill-registry](https://github.com/linny006/agent-skill-registry) | Package registry for AI agent skills — v0.1.0 released May 2026 |
| claudefa.st | [Claude Code Hooks: Complete Guide to All 12 Lifecycle Events](https://claudefa.st/blog/tools/hooks/hooks-guide) | 12 lifecycle hook events documented |
| support.claude.com | [Use plugins in Claude](https://support.claude.com/en/articles/13837440-use-plugins-in-claude) | Official Anthropic support article on Claude plugins |

**Web** (WebSearch supplements):
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| clarista.io | [Claude Code MCP Plugins: Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Comprehensive MCP guide; "USB for AI" framing |
| nimbalyst.com | [Best Claude Code MCP Servers 2026](https://nimbalyst.com/blog/best-claude-code-mcp-servers/) | Rankings: GitHub MCP as #1 impact install |
| code.claude.com | [MCP Docs](https://code.claude.com/docs/en/mcp) | Official MCP documentation |
| totalum.app | [Best MCP Servers 2026](https://www.totalum.app/blog/best-mcp-servers-2026) | 3-6 server sweet spot; GitHub + 1-2 project-specific recommended |
| gist.github.com | [5 MCP servers every Claude Code user should know](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) | Config examples + debugging tips |
| qcode.cc | [MCP Server Ecosystem 2026](https://www.qcode.cc/mcp-servers-ecosystem-2026) | 13,000+ servers counted; selection and gateway guide |
| codersera.com | [Claude Skills and MCP Servers: Practitioner's Guide](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/) | Thin-skill + MCP orchestration pattern |
| groundy.com | [Claude Code Plugins: Official Ecosystem Explained](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | 55+ official + 72+ community plugins |
| hidekazu-konishi.com | [Claude Code Plugins Complete Guide](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html) | Bundling skills, hooks, agents, MCP for team distribution |
| buildtolaunch.substack.com | [Best Claude Code Plugins 2026: 11 Tested, 4 Worth Keeping](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) | Practical review; curated down from 11 to 4 recommendations |
| rapidclaw.dev | [AI Agent Marketplace Guide 2026](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026) | 8 marketplaces in Q2 2026; economics and reviewing rules |
| digitalapplied.com | [AI Agent Marketplaces 2026: Discovery and Distribution](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | SKILL.md as cross-platform standard (CC, Codex, Cursor, Gemini CLI) |
| agensi.io | [AI Agent Skills Marketplace Comparison 2026](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026) | Side-by-side comparison of paid vs free vs security-reviewed tiers |
| zylos.ai | [AI Agent Marketplaces and Distribution Channels](https://zylos.ai/en/research/2026-03-09-ai-agent-marketplaces-distribution-channels/) | Security research: 1,184 malicious skills (~1 in 5) in one major registry |
| agensi.io | [Best AI Agent Skills Marketplaces 2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Complete marketplace directory |
| agensi.io | [AI Agent Marketplace Landscape 2026](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026) | Full breakdown of all 8 marketplaces |
| navosagent.ai | [Best 7 Agent Skills Marketplaces 2026](https://www.navosagent.ai/en/blog/best-agent-skills-marketplaces) | Security posture comparison across leading marketplaces |
| agensi.io | [Skills Marketplace: The New App Store for AI Agents](https://www.agensi.io/learn/skills-marketplace-ai-agents) | Discovery bottleneck analysis; "shipping is solved, surfacing is not" |
| code.claude.com | [Hooks Guide](https://code.claude.com/docs/en/hooks-guide) | Official hooks documentation: PreToolUse, PostToolUse, UserPromptSubmit, Stop |
| developersdigest.tech | [Claude Code Agent Teams, Subagents, and MCP: The 2026 Playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) | Subagent teams: each has own context window, prompt, and tool permissions |
| ofox.ai | [Claude Code: Hooks, Subagents & Skills Complete Guide](https://ofox.ai/blog/claude-code-hooks-subagents-skills-complete-guide-2026/) | "Add hooks for deterministic enforcement, subagents for parallel/isolation" |
| boringbot.substack.com | [Skills, Subagents, Hooks, Plugins, and Harnesses](https://boringbot.substack.com/p/claude-code-skills-subagents-hooks) | Production multi-agent workflow patterns |
| mer.vin | [Agent Harnesses Compared](https://mer.vin/2026/05/agent-harnesses-compared-claude-code-workflows-pi-subagents-and-atomic/) | Claude Code Workflows vs Pi Subagents vs Atomic comparison |
| smartscope.blog | [Claude Code Advanced Best Practices 2026](https://smartscope.blog/en/generative-ai/claude/claude-code-best-practices-advanced-2026/) | 11 practical techniques for hooks, subagents, and context management |
| morphllm.com | [Claude Code & Agent SDK Hooks Reference](https://www.morphllm.com/claude-code-hooks) | Complete hook event reference |
| buildmvpfast.com | [Claude Dynamic Workflows Guide](https://www.buildmvpfast.com/blog/claude-dynamic-workflows-orchestration-subagents-2026) | Subagent orchestration patterns |
| code.claude.com | [Discover Plugins](https://code.claude.com/docs/en/discover-plugins) | Official docs for plugin marketplace discovery |
| claudepluginhub.com | [claude-code-skills Marketplace](https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills) | Community skill collection listing |
| claudemarketplaces.com | [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/) | Community-curated daily-updated directory |
| scriptbyai.com | [Ultimate Claude Code Resource List 2026](https://www.scriptbyai.com/claude-code-resource-list/) | Comprehensive agents, skills, plugins, and more |
| firecrawl.dev | [Best Claude Code Skills to Try in 2026](https://www.firecrawl.dev/blog/best-claude-code-skills) | Curated recommendations |

---

## Stats Block

```
├─ 🟠 Reddit: 3 threads │ — upvotes │ — comments
├─ 🔵 X: 52 posts │ 1,500 likes │ 265 reposts
├─ 🦋 Bluesky: 12 posts │ 93 likes │ 7 reposts
├─ 🐙 GitHub: 5 items │ 38 reactions │ 18 comments
├─ 🌐 Web: 19 pages (engine) + 31 pages (WebSearch) = 50 total
└─ 🗣️ Top voices: @regent0x_, @Crypto_QianXun, @jefferyharrell.bsky.social │ r/ClaudeAI
```

---

## Data Gaps

- **Reddit (403 blocked):** The ScrapeCreators backup also failed (HTTP 402). Reddit results came via keyless RSS tier only, yielding 3 threads from r/ClaudeAI. Full subreddit search across r/ChatGPTCoding, r/LocalLLaMA, r/singularity, r/MachineLearning was blocked. Estimated coverage: ~15% of available Reddit content on this topic.
- **YouTube (0 results):** Both yt-dlp and ScrapeCreators YouTube returned zero results across all four subqueries. There is certainly YouTube content on Claude Code MCP and skills, but it was not accessible in this run. ScrapeCreators returned HTTP 402 (payment required). Missing YouTube transcripts is a significant gap for this topic.
- **TikTok (0 results):** ScrapeCreators hashtag search returned HTTP 402 for all hashtags (#claudecode, #mcpserver, #aiagent, #aicoding). No TikTok coverage.
- **Hacker News (0 results):** HN Algolia API returned HTTP 400 on all four subqueries (query strings too long). HN has been active on Claude Code - this is a tooling gap, not a coverage gap. The Bluesky HN bot logged one HN discussion thread.
- **Instagram (0 results):** ScrapeCreators HTTP 402. No coverage.
- **X noise:** ~30 of 52 captured X posts were off-topic crypto/finance discussions from @swarminged (crypto token), @regent0x_ (local AI hardware for law firms), and @Crypto_QianXun (stock investment prompts). On-topic signal: ~22 posts.
- **Approximate coverage:** 5 of 9 planned sources returned results. Core developer discussion on Reddit/HN/YouTube is under-represented. Web and X are well-covered.

---

## Key Quotes

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "$50 raspberry pi running AI in the palm of his hand - no plugins, no MCP servers, no 62,000 tokens of overhead - just ollama and a terminal" - [@regent0x_](https://x.com/regent0x_/status/2059559047888507213) on X

> "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate." - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) on Reddit

> "Total tools across all of them: 142. What nobody warns you about: every one of those tool definitions lands in your context window before any user prompt has been sent." - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thmpoq/configured_9_mcp_servers_in_claude_code_over_4/) on Reddit

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." - [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368) on X

> "his dad built a $2M company on a 1986 macintosh plus - no drivers, no plugins, no setup - just worked - 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead" - [@regent0x_](https://x.com/regent0x_/status/2058079320405332047) on X

> "the convergence of .claude-plugin/ and .cursor-plugin/ into a vendor-neutral .plugin/plugin.json feels like exactly the right structural move" - [vercel-labs/open-plugin-spec #5](https://github.com/vercel-labs/open-plugin-spec/issues/5) on GitHub

> "The best agents use all of it - skills, CLI, MCP - together." - [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550) on X (quoting David Soria Parra, Anthropic MCP co-creator)

> "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." - [Agensi](https://www.agensi.io/learn/skills-marketplace-ai-agents) on Web
