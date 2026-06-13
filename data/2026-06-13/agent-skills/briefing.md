# Agent Skills, MCP Servers & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-13
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 24 threads | — upvotes, — comments | Dominated by Fable 5 govt pullback; limited on-topic coverage |
| X/Twitter | 23 posts | 1,330 likes, 250 reposts | Top voice @Suryanshti777 (347 likes on claude-code-setup post) |
| Hacker News | 25 stories | 2,637 points, 1,491 comments | Richest on-topic signal; multiple Show HN skill/plugin/registry posts |
| Bluesky | 13 posts | 93 likes, 6 reposts | French dev community + indie builders; @jefferyharrell.bsky.social active |
| Web | 26 pages | — | 17 from engine (simoncarter.ai, claudefa.st, dev.to, github.com) + 9 WebSearch supplements |

---

## Synthesized Findings

### 1. Anthropic's Official Plugin System Matures: Bundles, Auto-Load, and a Setup Wizard

The biggest structural shift in the last 30 days is that Claude Code's plugin system crossed from "interesting experiment" to "recommended default." Anthropic's official [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) directory now has 130K GitHub stars and catalogs 55+ first-party plugins, with the broader community ecosystem adding 72+ more via third-party marketplaces. A plugin bundles skills, agents, hooks, MCP servers, LSP servers, and monitors into a single installable package - per [AI Trove](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins)'s explainer (May 24): "Claude Code plugins official is built on a well-specified plugin system that lets any developer package, version, and distribute extensions."

Two UX moves define this cycle. First, plugins now auto-load from `.claude/skills` directories - no marketplace step required - per [Simon Carter](https://simoncarter.ai/posts/claude-code-now-auto-loads-plugins-from-local-directories-no-marketplace-require/) (June 3): "A cluster of updates removes the marketplace dependency for loading plugins, adds a scaffolding command to get started quickly, brings autocomplete to the `/plugin` command, and lets you reload skills mid-session without restarting anything." Second, Anthropic quietly released `claude-code-setup`, an official plugin that scans your project and recommends hooks, skills, MCP servers, subagents, and automations. [@Suryanshti777](https://x.com/Suryanshti777/status/2065473893817848266) (347 likes, the highest-engagement X post in the dataset): "Claude Code feels completely different once you install this... Most people are using Claude Code completely vanilla… which is why their experience feels messy. The real power comes from the ecosystem."

Top plugins by install count as of June 1, per [KnightLi](https://knightli.com/en/2026/05/23/claude-plugins-official-claude-code-plugin-directory/): Frontend Design (829,316 installs), Superpowers (752,120 installs), Context7 (348,660 installs). The official directory is browsable at claude.com/plugins.

*Discussed across: X, Hacker News, Web, Bluesky.*

### 2. MCP Servers: 13,000+ and Counting, Less Than 5% Monetized

The Model Context Protocol ecosystem scaled dramatically in 2026. [ChatForest](https://chatforest.com/guides/mcp-ecosystem-2026-state-of-the-standard/)'s state-of-the-standard guide reports 13,000+ total MCP servers (2,000+ on the official modelcontextprotocol.io registry which crossed 800 servers in April 2026, 5,000+ tracked by community registries, with the remainder on private/enterprise deployments). Described as "USB for AI: one protocol, many tools, many clients."

The practical developer experience: MCP lets Claude Code connect to databases, GitHub, Slack, and custom services through a single protocol. [@TheoWtmn](https://x.com/TheoWtmn/status/2065399769036476835) captured the power user pattern: "My setup runs Claude Code with different MCP configs per project. Swap servers with a toggle instead of editing JSON every time." Per [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp): "Prefer MCP tools over Bash when the integration will be used across sessions."

The Show HN wave on HN validates practitioner adoption: "I gave my AI video generator 86 MCP tools so Claude Code can drive it" ([ViralMint](https://github.com/openclaw-easy/ViralMint)), "I built an MCP server so you can ask Claude about your cloud/software bill" ([getnable.com](https://getnable.com/)), "Show HN: macOS menu bar gauges for your Claude Code quota" ([claude-quota](https://github.com/grzegorz-raczek-unit8/claude-quota), 66 pts, 40 cmt), "Stop returning raw JSON from MCP servers, build rich inline UIs" ([Medium/TAI](https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3), 11 pts).

Economic reality: per [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries), less than 5% of MCP servers are monetized. The [Smithery](https://www.truefoundry.com/blog/best-mcp-registries) registry holds the largest catalog, functioning as a directory rather than a marketplace.

*Discussed across: Hacker News, X, Web.*

### 3. The Skill Marketplace Race: 8 Competitors, No Clear Winner

The agent skills marketplace landscape went from one player to eight in roughly six months. [Agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)'s full breakdown of Q2 2026:

- **Skills.sh** (Vercel-backed, launched January 2026) - npm-style package manager for skills; one-command CLI installs across Claude Code, Codex CLI, Cursor, and OpenClaw - positioned as the cross-platform standard
- **SkillsMP** - 800,000+ skills scraped from public GitHub repos; large catalog, minimal curation
- **ClaudeSkills.info** - 658+ free skills, no paid tier, includes official Anthropic skills and community submissions
- **claudemarketplaces.com** - claims 21,600+ skills, 9,900+ MCP servers, 2,500+ marketplaces
- **CodeGuilds** ([codeguilds.dev](https://codeguilds.dev)) - community registry for Claude Code (skills, agents, MCP servers); debuted on Hacker News June 1 (3 pts)
- **AgentSkillsHub** ([agentskillshub.dev](https://agentskillshub.dev)) - "The Secure Marketplace for AI Agents"
- **GitHub** - still the de facto distribution layer for most community skills

The fragmentation is real: per [Agensi's landscape breakdown](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026), each marketplace has different economics, reviewing rules, and distribution dynamics. The winner-take-most pattern from npm/PyPI hasn't emerged yet.

The HN community is also building its own registries: "Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers" ([ai-capability-registry](https://github.com/Friz-zy/ai-capability-registry)) and a personal GitHub-based registry ([skills-registry](https://github.com/anand-92/skills-registry)) with the description: "Your personal GitHub registry for AI Agent Skills. One repo. EVERY agent. EVERY device. Loaded on demand - Zero startup bloat."

*Discussed across: Hacker News, Web, X.*

### 4. CC-Switch Hits 100k+ GitHub Stars: Multi-Agent Skills Unification

The most visible community signal this week: [CC-Switch](https://x.com/kodemarket01/status/2065731905064964138) is trending on GitHub with 100k+ stars. It is a cross-platform desktop assistant that wraps Claude Code, Codex, OpenCode, OpenClaw, Gemini CLI, and Hermes Agent under one panel with "Unified MCP & Skills Management: One panel to manage MCP servers and Skills with bidirectional sync." The project reflects a genuine developer need: as skills proliferate across agent frameworks, managing configs per agent is growing friction.

This connects to the cross-agent skills pattern visible throughout the dataset: [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) offers 337 Claude Code skills for 10+ coding agents; ECC drops 63 specialized agents and 240+ skills for Claude Code, Cursor, and Codex in a free MIT-licensed package (per [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c)). The Ruflo framework (per [@github-trending-js.bsky.social](https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b)) extends Claude Code with "100+ cooperative agents, self-learning memory, zero-trust federation, and a suite of plugins and tools (MCP, memory, GOAP planning, and a Web UI)."

*Discussed across: X, Bluesky.*

### 5. Security Gap: NVIDIA Scanner, 13% Critical Flaws, Nobody Paying Attention

The security picture is alarming. [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) called it directly: "Skills are the new plugins. Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins. Every AI agent framework now has a marketplace of community-built skills you can install with one command. One command. That skill now runs inside your AI agent. With access to everything your agent can access." NVIDIA built a security scanner for AI agent skills that "almost nobody is using yet."

Background: a February 2026 Snyk audit found that 13% of agent-skills packages contain critical security flaws (none from the official claude-plugins-official listings). The [TechTimes](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm) report (May 23) noted Anthropic itself flagged unverified MCP risks in its official directory launch. The HN community responded with tooling: "Show HN: A police department for your Claude Code agents" ([agent-pd](https://github.com/varmabudharaju/agent-pd/blob/master/README.md), 10 pts, 8 cmt) and the Holster Pro security preflight tool for "builders using Codex, Cursor, Claude Code, MCP servers, local wrappers" (per [@NautaAI](https://x.com/NautaAI/status/2065414218883481991)).

Enterprise response: 42Crunch announced "dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise" (per [@brunopedro.com](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) on Bluesky). Akto's Claude Compliance API tracks MCP servers, skill usage, and data leakage ([@Aktodotio](https://x.com/Aktodotio/status/2065479277680992570)). [DevOps Daily](https://devops-daily.com/posts/best-claude-code-plugins-devops-2026) recommends the security-guidance plugin which "runs a fast pattern check on each edit, a model review at the end of each turn, and a deeper agentic review on commit or push."

*Discussed across: X, Bluesky, Web, Hacker News.*

### 6. Hacker News Is the Primary Practitioner Hub for Skills Discussion

HN delivered the richest on-topic signal in this dataset: 2,637 points and 1,491 comments across 25 stories. The standout posts:

- **"Claude Code as a Daily Driver"** ([arps18.github.io](https://arps18.github.io/posts/claude-code-mastery/)) - 451 pts, 254 comments - covers Claude.md, Skills, Subagents, Plugins, and MCPs as an integrated system
- **"My Agent Skill for Test-Driven Development"** ([saturnci.com](https://www.saturnci.com/my-agent-skill-for-test-driven-development.html)) - 251 pts, 109 comments
- **"A Claude Code and Codex Skill for Deliberate Skill Development"** ([github.com/DrCatHicks](https://github.com/DrCatHicks/learning-opportunities)) - 253 pts, 50 comments
- **"Claude Code - Everything you can configure that the docs don't tell you"** ([buildingbetter.tech](https://buildingbetter.tech/p/i-read-the-claude-code-source-code)) - 326 pts, 65 comments
- **"Dynamic Workflows in Claude Code"** ([claude.com/blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code)) - 200 pts, 135 comments (official Anthropic)
- **"Claude Code and Codex can have real-time conversation via Git"** ([Medium](https://medium.com/@Koukyosyumei/claude-code-and-codex-can-have-real-time-conversation-via-git-f95b696c1c05)) - 116 pts, 79 comments
- **"Show HN: skills-for-humanity - 171 structured reasoning skills"** ([github.com](https://github.com/human-avatar/skills-for-humanity)) - 28 pts, 7 comments

*Discussed across: Hacker News, Bluesky (HN bot reposts).*

### 7. The 5-Layer Harness Pattern: Beats Upgrading Models

A key practitioner insight crystallized this cycle: activating Claude Code's full extensibility stack outperforms paying for a larger model. [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) stated it plainly: "le harness de claude code en 5 couches : CLAUDE.md -> hooks -> skills -> plugins -> MCP servers. le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet." (Upgrading from Sonnet to Opus brings less than activating these 5 layers on Sonnet.)

[Firecrawl](https://www.firecrawl.dev/blog/best-claude-code-skills) frames the core value: "Instead of re-explaining preferences and workflows every session, developers define them once in a skill file and Claude picks them up automatically." [ClaudeFolio](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) distinguishes the two main extension surfaces: "skills, which are markdown files in your repo that become custom slash commands, and MCP servers, which are external services that connect to the tool over a standard protocol and expose new tools the model can call. They sit at different layers and solve different problems."

Practical proof: [@LaireLaFlare](https://x.com/LaireLaFlare/status/2065502673378349069) shipping an embeddable market widget product solo: "still solo, still claude code + a stack of mcp servers doing the deploys. wild what one person can ship now."

From a [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) explainer: skills are for "codifying your own workflows in language the model reads directly from the repo," while MCP servers are for "external integrations that persist across every project."

*Discussed across: Bluesky, X, Web.*

---

## Cross-Source Patterns

**1. "Skills are the new plugins" - terminology standardizing across frameworks**
- Appearing on: X, Web, HN
- [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) explicitly lists: "Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins." CC-Switch uses "Skills" as the unified label across 6 agent frameworks. The word "skill" is displacing "plugin" as the canonical term for reusable agent capabilities.

**2. Security anxiety scaling with ecosystem growth**
- Appearing on: X, Web, HN, Bluesky
- Snyk audit (13% critical flaws), NVIDIA scanner (unused), Anthropic's unverified-MCP warning, HN's "police department for agents" post, Holster Pro preflight tool, 42Crunch DevSecOps plugin, Akto compliance API - all landed in the last 30 days. The gap between install convenience ("one command") and security awareness is widening.

**3. Cross-agent compatibility becoming table stakes**
- Appearing on: X, Bluesky, Web
- Skills designed to work across Claude Code + Codex + Cursor + Gemini CLI are becoming the standard. CC-Switch (100k+ stars), [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (337 skills for 10+ agents), ECC (MIT-licensed multi-agent skills). "Claude Code only" skill packages are losing interest versus "works everywhere" packages.

**4. HN as primary practitioner community, Reddit noise-dominated**
- Appearing on: HN (2,637 pts), Bluesky
- The highest-engagement skills/plugins/MCPs discussions are on Hacker News. Reddit (r/ClaudeAI) was completely dominated by Fable 5 government export control news on the data collection date (June 13), making it nearly useless for this topic today.

**5. Plugins as organizational infrastructure: Personal -> Team -> Org**
- Appearing on: Web, X
- Multiple guides targeting team/org plugin rollout: [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution)'s "From Personal to Org" guide, [pondero.ai](https://pondero.ai/coding/guides/claude-code-plugins-marketplace-may-2026/)'s "Find, Install, and Scope Them for Your Team," [Azure SRE Agent](https://sre.azure.com/docs/capabilities/plugin-marketplace)'s Plugin Marketplace with "SHA-256 content hashing lets you check for upstream skill changes with one click." Enterprise adoption is formalizing the deployment pattern.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | The reason your 5-hour window evaporates in minutes | — | — | "the useless rule is the first thing claude drops when the context gets too heavy... a few turns later it's inventing APIs" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u4gct9/the_reason_your_5hour_window_evaporates_in/) |
| r/ClaudeAI | Employee of the Month: June 1st – June 22nd, 2026 (RIP) | — | — | "Claude Code carried my entire indie studio on his pixelated orange back, and his reward is being sunset faster than the milk in my fridge expires" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3wflg/employee_of_the_month_june_1st_june_22nd_2026_rip/) |
| r/ClaudeAI | The state of things: Claude Fable | — | — | Fable 5/Mythos 5 suspended by US export control directive | [link](https://www.reddit.com/r/ClaudeAI/comments/1u4gh16/the_state_of_things_claude_fable/) |
| r/ClaudeAI | I had Claude Fable 5 build Minecraft from scratch | — | — | "About 45,000 lines of Swift, 82 files, zero external dependencies" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u4g6y5/i_had_claude_fable_5_build_minecraft_from_scratch/) |
| r/ClaudeAI | Blame the US govt for losing access to Fable 5 not Anthropic | — | — | — | [link](https://www.reddit.com/r/ClaudeAI/comments/1u4gtm9/blame_the_us_govt_for_losing_access_to_fable_5/) |
| r/ClaudeAI | Fable 5's Last response. | — | — | "Curious to see what you were all working on before we got rugpulled" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u4epty/fable_5s_last_response/) |
| r/artificial | Claude Fable made me realize I don't need a better model | — | — | — | [link](https://www.reddit.com/r/artificial/comments/1u3acx4/claude_fable_made_me_realize_i_dont_need_a_better/) |
| r/artificial | Claude is completely unusable now | — | — | "Claude does everything it can to get out of work" | [link](https://www.reddit.com/r/artificial/comments/1twn3m7/claude_is_completely_unusable_now/) |

*Note: Reddit corpus dominated by Fable 5 government export control news (June 13). On-topic skills/plugin threads not surfaced.*

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Suryanshti777 | "Anthropic quietly released claude-code-setup...scans your project and recommends hooks, skills, MCP servers, subagents, automations" | 347 | 31 | [link](https://x.com/Suryanshti777/status/2065473893817848266) |
| @WY_mask | Visual guide to Claude Code: orchestrate agents, hooks, skills and MCP servers (Chinese tutorial, Fable 5 reference) | 35 | 8 | [link](https://x.com/WY_mask/status/2065469929025872175) |
| @kodemarket01 | "CC-Switch trending on GitHub: Unified MCP & Skills Management - 100k+ stars" | — | — | [link](https://x.com/kodemarket01/status/2065731905064964138) |
| @RituWithAI | "NVIDIA just built the security scanner that every developer installing AI agent skills desperately needs. And almost nobody is using it yet." | 7 | 5 | [link](https://x.com/RituWithAI/status/2065656659842842728) |
| @LaireLaFlare | "still solo, still claude code + a stack of mcp servers doing the deploys. wild what one person can ship now." | 1 | — | [link](https://x.com/LaireLaFlare/status/2065502673378349069) |
| @TheoWtmn | "My setup runs Claude Code with different MCP configs per project. Swap servers with a toggle instead of editing JSON every time." | 2 | — | [link](https://x.com/TheoWtmn/status/2065399769036476835) |
| @ds_jessica_ | "Claude Code is changing how I write software...You extend it with MCP servers and hooks" | — | — | [link](https://x.com/ds_jessica_/status/2065583678038650910) |
| @Aktodotio | "Track MCP servers and Skill usage -> Detect data leakage and guardrail violations -> Govern AI agents" | 1 | — | [link](https://x.com/Aktodotio/status/2065479277680992570) |
| @NautaAI | "Holster Pro is for builders using Codex, Cursor, Claude Code, MCP servers...Find the boundary problem before it spreads." | — | — | [link](https://x.com/NautaAI/status/2065414218883481991) |
| @iammukeshm | "Most people use Claude Code like a fancy autocomplete. The setup is where the real speed is." | 3 | — | [link](https://x.com/iammukeshm/status/2065675640108351652) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | [link](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) |
| ankitg12 | Claude Code - Everything you can configure that the docs don't tell you | 326 | 65 | — | [link](https://buildingbetter.tech/p/i-read-the-claude-code-source-code) |
| laxmena | My Agent Skill for Test-Driven Development | 251 | 109 | — | [link](https://www.saturnci.com/my-agent-skill-for-test-driven-development.html) |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | [link](https://github.com/DrCatHicks/learning-opportunities) |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | [link](https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start) |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| syumei | Claude Code and Codex can have real-time conversation via Git | 116 | 79 | — | [link](https://medium.com/@Koukyosyumei/claude-code-and-codex-can-have-real-time-conversation-via-git-f95b696c1c05) |
| nab | Show HN: Boxes.dev - ditch localhost; run Claude Code and Codex in the cloud | 104 | 79 | — | [link](https://boxes.dev) |
| ankitg12 | Claude Code - Everything you can configure that the docs don't tell you | 326 | 65 | — | [link](https://buildingbetter.tech/p/i-read-the-claude-code-source-code) |
| grzracz | Show HN: macOS menu bar gauges for your Claude Code quota | 66 | 40 | — | [link](https://github.com/grzegorz-raczek-unit8/claude-quota) |
| finnworks | Show HN: skills-for-humanity - 171 structured reasoning skills for Claude Code | 28 | 7 | — | [link](https://github.com/human-avatar/skills-for-humanity) |
| sermakarevich | Show HN: Lessons learned from running Claude Code swarms at scale | 10 | 6 | — | [link](https://news.ycombinator.com/item?id=48407998) |
| softie123 | Show HN: A police department for your Claude Code agents | 10 | 8 | — | [link](https://github.com/varmabudharaju/agent-pd/blob/master/README.md) |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | — | — | [link](https://github.com/Friz-zy/ai-capability-registry) |
| haimm | CodeGuilds - community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | [link](https://codeguilds.dev) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." | 35 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) |
| @jefferyharrell.bsky.social | "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) |
| @coolhand.bsky.social | "I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" | 12 | [link](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) |
| @camilleroux.com | "Mon top 13 des skills et plugins Claude Code qui ont marque 2026 : celui qui coupe 63 % des tokens de sortie, celui qui rejoue tes sessions comme une video, celui qui transforme une codebase en graphe explorable" | 8 | [link](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches : CLAUDE.md -> hooks -> skills -> plugins -> MCP servers. passer de sonnet a opus apporte moins que d'activer ces 5 couches sur sonnet" | 1 | [link](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together" | 4 | [link](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) |
| @brunopedro.com | "42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise" | 1 | [link](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) |
| @github-trending-js.bsky.social | "Ruflo is a multi-agent AI orchestration framework that extends Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation, and a suite of plugins and tools" | 1 | [link](https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b) |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | [link](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) |
| @viriditax.bsky.social | "when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it to flex it" | 9 | [link](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227) |
| @mengli512.bsky.social | "Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression." | 3 | [link](https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Simon Carter | [simoncarter.ai](https://simoncarter.ai/posts/claude-code-now-auto-loads-plugins-from-local-directories-no-marketplace-require/) | Auto-load from local dirs update; no marketplace required; `/plugin` autocomplete; mid-session skill reload |
| Claudefa.st | [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution) | Plugins: Personal to Org deployment patterns; Code Kit v5.3 smarter Sub-Agent defaults |
| DEV Community | [dev.to](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) | How skills, MCP servers, and plugins fit together in 2026 |
| AI Trove | [ai-trove.com](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) | Plugin anatomy: skills, agents, hooks, MCP, LSP - full taxonomy |
| ClaudeFolio | [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) | Skills (markdown files) vs MCP servers (external services) - different layers |
| PolySkill | [polyskill.ai](https://polyskill.ai/blog/claude-code-mcp) | `claude mcp add` flow; 3 transport types (stdio, sse, http); scope flags (user/project/local) |
| AI Tools Guidebook | [aitoolsguidebook.com](https://aitoolsguidebook.com/en/articles/claude-code-mcp-tutorial/) | Concrete MCP setup guide; avoid installing 5 servers at once |
| LLM Best Practices | [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp) | "Prefer MCP tools over Bash when the integration will be used across sessions" |
| AI Architects | [theaiarchitects.com](https://theaiarchitects.com/blog/claude-plugins) | Install, create, and distribute plugins; keyword volume data |
| Developer Toolkit | [developertoolkit.ai](https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/) | 400+ tutorials; MCP integrates Sentry/GitHub/Jira/database in one session |
| Pondero.ai | [pondero.ai](https://pondero.ai/coding/guides/claude-code-plugins-marketplace-may-2026/) | Directory crossed 19.8K stars; 35 first-party plugins; team scoping guide |
| Azure SRE Agent | [sre.azure.com](https://sre.azure.com/docs/capabilities/plugin-marketplace) | Browse/install agent skills from GitHub marketplaces; SHA-256 content hashing |
| GitHub Issue #63174 | [github.com/anthropics/claude-code](https://github.com/anthropics/claude-code/issues/63174) | Multi-plugin marketplace bug: only first plugin loads from installed_plugins.json |
| GitHub/alirezarezvani | [github.com](https://github.com/alirezarezvani/claude-skills) | 337 skills for 10+ coding agents (Claude Code, Codex, Gemini CLI, Cursor, etc.) |
| TechTimes | [techtimes.com](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm) | Official directory launch; Anthropic flags unverified MCP risks; Snyk 13% flaw stat |
| Clarista | [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Complete 2026 MCP + plugins guide; 2,000+ official registry, 5,000+ community |
| Groundy | [groundy.com](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | Official plugin ecosystem explained; bundles skills/agents/hooks/MCPs/LSPs |
| KnightLi | [knightli.com](https://knightli.com/en/2026/05/23/claude-plugins-official-claude-code-plugin-directory/) | Top plugins by install count June 1: Frontend Design (829k), Superpowers (752k), Context7 (348k) |
| Agensi | [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 8 marketplace landscape breakdown; Skills.sh as npm equivalent; SkillsMP at 800k+ |
| ChatForest | [chatforest.com](https://chatforest.com/guides/mcp-ecosystem-2026-state-of-the-standard/) | MCP ecosystem: 13,000+ servers total, official registry 800+ in April, <5% monetized |
| TrueFoundry | [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries) | MCP registries comparison for devs and enterprises; Smithery largest catalog |
| Firecrawl | [firecrawl.dev](https://www.firecrawl.dev/blog/best-claude-code-skills) | Skills make Claude reusable across sessions; .claude/skills auto-loads; plugin init command |
| DevOps Daily | [devops-daily.com](https://devops-daily.com/posts/best-claude-code-plugins-devops-2026) | Security-guidance plugin: pattern check each edit + model review per turn + agentic review on commit |

---

## Stats Block

```
├─ 🟠 Reddit: 24 threads │ — upvotes │ — comments
├─ 🔵 X: 23 posts │ 1,330 likes │ 250 reposts
├─ 🟢 HN: 25 stories │ 2,637 points │ 1,491 comments
├─ 🦋 Bluesky: 13 posts │ 93 likes │ 6 reposts
├─ 🌐 Web: 26 pages
└─ 🗣️ Top voices: @Suryanshti777, @RituWithAI, @jefferyharrell.bsky.social │ r/ClaudeAI, r/artificial
```

---

## Data Gaps

- **Reddit dominated by Fable 5 pullback** (US government export control directive, June 13): 18 of 24 threads were about Fable 5/Mythos 5 suspension. Reddit public API returned 403 errors initially; ScrapeCreators returned HTTP 402. On-topic skills/plugin coverage from Reddit: ~25%. Reddit engagement metrics (upvotes/comments) unavailable.
- **YouTube: 0 results** - yt-dlp returned 0 results on the full query string; ScrapeCreators YouTube endpoint returned HTTP 402. Significant gap - YouTube almost certainly has tutorial/review content on Claude Code plugins/skills.
- **TikTok: 0 results** - ScrapeCreators returned HTTP 402. No TikTok coverage.
- **Instagram: 0 results** - ScrapeCreators returned HTTP 402. No Instagram coverage.
- **GitHub: 0 results from engine** - No GitHub token configured; no `gh` CLI authenticated. Several community repos surfaced via Web sources instead.
- **X/Twitter signal noise**: ~30% of X posts in corpus were about unrelated topics (crypto agent marketplaces, 3D AI avatars, RWA tokenization, blockchain). Filtered from synthesis.
- **Overall on-topic coverage**: approximately 60-65% due to Reddit noise, missing YouTube/TikTok/GitHub. HN and Web sources provided strong on-topic signal.

---

## Key Quotes

> "Skills are the new plugins. Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins. Every AI agent framework now has a marketplace of community-built skills you can install with one command. One command. That skill now runs inside your AI agent. With access to everything your agent can access." - [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) on X

> "Claude Code feels completely different once you install this. Anthropic quietly released an official plugin called claude-code-setup and it basically turns Claude Code from 'pretty good' into an actual AI dev environment." - [@Suryanshti777](https://x.com/Suryanshti777/status/2065473893817848266) on X (347 likes)

> "le harness de claude code en 5 couches : CLAUDE.md -> hooks -> skills -> plugins -> MCP servers. le contre-intuitif : passer de sonnet a opus apporte moins que d'activer ces 5 couches sur sonnet." - [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky (35 likes)

> "still solo, still claude code + a stack of mcp servers doing the deploys. wild what one person can ship now." - [@LaireLaFlare](https://x.com/LaireLaFlare/status/2065502673378349069) on X

> "My setup runs Claude Code with different MCP configs per project. Swap servers with a toggle instead of editing JSON every time." - [@TheoWtmn](https://x.com/TheoWtmn/status/2065399769036476835) on X

> "I made three large kits for that specific problem. I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" - [@coolhand.bsky.social](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) on Bluesky

> "Plugins Now Auto-Load from Local Directories - No Marketplace Required" - [Simon Carter](https://simoncarter.ai/posts/claude-code-now-auto-loads-plugins-from-local-directories-no-marketplace-require/) (simoncarter.ai, June 3)

> "CC-Switch: Unified MCP & Skills Management: One panel to manage MCP servers and Skills with bidirectional sync. Stars: 100k+" - [@kodemarket01](https://x.com/kodemarket01/status/2065731905064964138) on X
