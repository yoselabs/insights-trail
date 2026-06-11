# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-11
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 12 threads | — | r/ClaudeAI, r/ClaudeWorkflows, r/SaaS primary |
| X/Twitter | 13 posts | 1,515 likes, 339 reposts | @regent0x_, @polsia, @AndrewK404 top voices |
| Hacker News | 39 stories | 4,980 points, 2,483 comments | Highest engagement source |
| Bluesky | 12 posts | 92 likes, 6 reposts | @jefferyharrell.bsky.social dominant |
| Web | 26 pages | — | Engine (19) + WebSearch supplements (7) |

---

## Synthesized Findings

### 1. The Plugin/Skill Taxonomy Is Still Being Figured Out — and That's Causing Real Confusion

The most practically-useful content this month is the community's effort to nail down what "skill," "plugin," "MCP server," and "hook" actually mean in Claude Code. [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368) cut through it cleanly on May 27: "A skill is a focused instruction pack for one repeatable workflow — e.g. code review rules or Postgres SQL generation. A plugin is an installable bundle that can include skills, agents, hooks, MCP/LSP servers, and other extensions. Skill = teach Claude one workflow. Plugin = package and share a broader toolkit."

A [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/) post from May 25 formalized this as a hierarchy: CLAUDE.md → Skills → Hooks → Plugins → AGENTS.md, rating the guide 85/100 for intermediate users. [dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) (June 8) offered a decision heuristic — "lightest first": use a CLI flag → then a skill → then an MCP server → then a full plugin, only escalating when the lighter option can't handle the task.

**Platforms:** Reddit, X, Web (HN discussion threads)

### 2. Dynamic Workflows Is the Biggest Anthropic Feature Drop of the Month

Anthropic's ["Introducing dynamic workflows in Claude Code"](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) (May 28) landed 200 HN points and 135 comments. The official ["A harness for every task"](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) follow-up (June 2) explained the model: Claude writes a JavaScript orchestration script for your task, then a runtime executes it across up to 1,000 parallel subagents in the background — resumable and rerunnable. Use cases: codebase-wide audits, large migrations, research that needs cross-checking.

[dev.to](https://dev.to/thlandgraf/claude-code-workflows-the-plan-moves-out-of-claudes-head-and-into-a-script-you-can-edit-3k4b) (June 6) described the core shift: "Subagents, skills, and agent teams all keep the plan in one place: Claude's head. Dynamic workflows move the plan out of Claude's head and into a script you can edit." The [claudelab.net](https://claudelab.net/en/articles/claude-code/claude-code-dynamic-workflow-authoring) guide (May 30) documents the `phase / agent / pipeline` primitives, calling it "reusable research pipelines."

**Platforms:** HN, Web (multiple guides and tutorials)

### 3. The Marketplace Explosion — and the Fragmentation Problem

The skill/plugin marketplace space has exploded. [claudemarketplaces.com](https://claudemarketplaces.com/) indexes 20,300+ skills, 2,500+ marketplaces, and 9,900+ MCP servers. [Agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) documents eight major marketplaces by Q2 2026, up from one in December 2025. [@polsia](https://x.com/polsia/status/2064450681856200753) (June 9) built an open directory for Claude Code, Cursor, and Windsurf extensions — 2,000+ skills, MCP servers, and rules ranked by stars — noting "the space is getting crowded."

On HN, [CodeGuilds](https://codeguilds.dev) (June 1, 3pts) launched as a community registry specifically for Claude Code skills, agents, and MCP servers. A [Show HN](https://github.com/Friz-zy/ai-capability-registry) on June 4 proposed a GitOps-style registry for AI agent workflows, skills, and MCP servers. The official Anthropic direction is [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) plus the community-managed `claude-plugins-community` repo.

Key tension from [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries): no central registry with quality signals, widely varying documentation standards, and entire categories (knowledge bases) with no community solution despite clear demand. [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) notes Skills.sh (Vercel-backed, Jan 2026) is positioning as "npm for skills" with a one-command CLI installer across Claude Code, Codex CLI, Cursor, and OpenClaw.

**Platforms:** X, HN, Web

### 4. MCP in Production Is a Mess — and a Security Surface

The most upvoted Reddit thread in the corpus is from [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/) (June 2): "I ship AI agents in production. The mess is MCP." A developer building agents for logistics and fintech clients documented the real-world friction of MCP servers in production. The frustration found cultural resonance: [@regent0x_](https://x.com/regent0x_/status/2058079320405332047) (May 23, 49 likes) posted a viral contrast — "his dad built a $2M company on a 1986 Macintosh Plus, no drivers, no setup — just worked. 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free."

Security concerns are multiplying. [@stackzz](https://x.com/stackzz/status/2056026387597885457) (May 17, 71 likes) warned: "MCP tourists are about to get rinsed by their own integrations. Every MCP server is a permission surface: what can it read? what can it write? can it touch money, keys, deploys, or customer data?" HN saw a cluster of security tools: [MCPSafe](https://mcpsafe.io) (5-LLM consensus scanner), [MCP-safeguard](https://github.com/SyedAnas01/mcp-safeguard) (open-source scanner), [Mcpaudit](https://github.com/allenwu-blip/mcpaudit) (static scanner), and [AgentSploit](https://github.com/agentsploit/agentsploit) ("Burp Suite for AI agents and MCP servers"). A June 2 HN post from [Bindfort](https://bindfort.com/research/mcp-supply-chain-scan) reported that official MCP servers ship known-vulnerable dependencies at install time.

**Platforms:** Reddit, X, HN

### 5. The "Daily Driver" Article: Highest HN Engagement of the Month

["Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs"](https://arps18.github.io/posts/claude-code-mastery/) hit 451 HN points and 254 comments on May 27 — the highest-engagement story in the corpus. It consolidated the full extension hierarchy into a single guide and became the de facto community reference.

[@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (June 4, 35 Bluesky likes) captured the power-user aspiration: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." Then two posts later: "I'm pretty confident I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

**Platforms:** HN, Bluesky

### 6. Multi-Harness / Cross-Agent Portability Is Becoming a Design Goal

Multiple repos and tools explicitly target portability across agents, not just Claude Code. [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) uses the `agentskills.io` open standard and works across Claude Code, Cursor, Copilot, Codex CLI, Gemini CLI, and 30+ more. [juftin/skills](https://github.com/juftin/skills) bills itself as "a cross-platform agent skills directory and Claude Code marketplace." [wshobson/agents](https://github.com/wshobson/agents) has 84 plugins, 192 agents, 156 skills, 102 commands "built for Claude Code and consumed natively by OpenAI Codex CLI, Cursor, OpenCode, Gemini CLI, and GitHub Copilot."

[@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550) (June 6, 50 likes) cited MCP co-creator David Soria Parra: "Connectivity is not one thing. The best agents use all of it — skills, CLI, MCP — together."

**Platforms:** X, HN, Web

### 7. The Counter-Signal: Complexity Backlash and the "Just a Terminal" Aesthetic

A vocal counter-movement questions whether all this ecosystem complexity is necessary. [@regent0x_](https://x.com/regent0x_/status/2059559047888507213) (May 27, 129 likes) posted the most-liked X thread in the corpus: "$50 Raspberry Pi running AI in the palm of his hand — no plugins, no MCP servers, no 62,000 tokens of overhead, just ollama and a terminal. This guy saw that video and deleted everything from his $4,000 MacBook." The post contrasted a stripped setup against a documented "23 plugins, 8 skills, 5 MCP servers" Claude Code install.

[@regent0x_](https://x.com/regent0x_/status/2057419591618302029)'s earlier post (May 21, 315 likes) — "Stop Installing Plugins on Claude Code - The Ultimate Guide" — was the highest-engagement X post in the corpus overall.

A [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1ti8cwr/after_a_year_in_claude_code_the_thing_slowing_me/) thread (May 20) by a year-long daily user concluded the bottleneck wasn't the model or prompts — it was accumulated configuration debt.

**Platforms:** X, Reddit

### 8. Paid Prebuilt Agent Marketplaces Are Testing Willingness-to-Pay

A June 3 HN Show HN — ["Would you pay once (no subscription) for prebuilt Claude Code agents?"](https://ai-specialists.vercel.app) — directly probed the market. The [Agensi.io](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) founder (r/SaaS, June 2) reported 1.54M impressions and 12.9K clicks in 3 months running an AI agent skills marketplace with Claude as the entire marketing team — 1,500+ registered users, domain rating 43.

Free/MIT alternatives are also emerging: [ECC (everything-claude-code)](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) drops 63 specialized agents and 240+ skills into Claude Code, Cursor, and Codex — explicitly "free, MIT-licensed, replaces the pile of paid plugins developers duct-tape together."

**Platforms:** HN, Reddit, Bluesky

---

## Cross-Source Patterns

### Pattern 1: MCP complexity/overhead is the dominant practitioner complaint
- Platforms: Reddit (r/ClaudeAI "mess is MCP"), X (@regent0x_ "5 MCP servers and 14,000 tokens of overhead"), X (@stackzz security warning)
- Quote: "The day-to-day is mess. One specific kind of mess: MCP servers in production." — r/ClaudeAI
- Quote: "MCP tourists are about to get rinsed by their own integrations. Every MCP server is a permission surface." — [@stackzz](https://x.com/stackzz/status/2056026387597885457)

### Pattern 2: Ecosystem fragmentation — registries proliferating with no quality standard
- Platforms: HN (CodeGuilds, GitOps registry, NPM-style registry launches), Web (TrueFoundry registry comparison, claudemarketplaces.com)
- Quote: "The space is getting crowded. Time to stand out." — [@polsia](https://x.com/polsia/status/2064450681856200753)
- Signal: 8 major skill marketplaces by Q2 2026; no single source of truth for quality

### Pattern 3: Skills/plugin taxonomy confusion is an onboarding barrier
- Platforms: Reddit (practical guide), X (@AndrewK404 definitional thread), Web (dev.to "lightest first" decision tree)
- Quote: "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." — [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368)

### Pattern 4: Dynamic workflows (Claude-authored orchestration scripts) is the feature getting most developer attention
- Platforms: HN (200 pts + 135 cmts), Web (multiple guides on claudelab.net, dev.to, qcode.cc)
- Signal: Anthropic published two official blog posts + multiple third-party tutorials within 2 weeks

### Pattern 5: Cross-agent portability as a competitive moat for skill distributors
- Platforms: X (@pauliusztin_ architecture post), Web (netresearch marketplace, juftin/skills, wshobson/agents)
- Quote: "The best agents use all of it — skills, CLI, MCP — together." — David Soria Parra (MCP co-creator), cited by [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I ship AI agents in production. The mess is MCP. | — | — | "The day-to-day is mess. One specific kind of mess: MCP servers in production." | https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/ |
| r/ClaudeWorkflows | Practical Guide to Claude Code Components: CLAUDE.md, Skills, Hooks, Plugins | — | — | Workflow value: 85/100, Level: intermediate | https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/ |
| r/ClaudeWorkflows | Claude Orchestra: Open-Source System to Manage Claude Code Skills, Agents, and MCP Servers | — | — | Workflow value: 90/100, Level: advanced | https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/ |
| r/SaaS | 1.5M impressions, 12.9K clicks in 3 months. My entire SEO team is Claude. | — | — | "I'm a solo non-technical founder running a marketplace for AI agent skills." | https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/ |
| r/ClaudeAI | After a year in Claude Code, the thing slowing me down turned out to be me | — | — | "I kept assuming the way to get faster was a better model or a sharper prompt. It was neither." | https://www.reddit.com/r/ClaudeAI/comments/1ti8cwr/after_a_year_in_claude_code_the_thing_slowing_me/ |
| r/ClaudeAI | 100 Tips & Tricks for Building Your Own Personal AI Agent | — | — | "6 weeks, no sleep, two environments, one agent that actually works." | https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @regent0x_ | Stop Installing Plugins on Claude Code - The Ultimate Guide | 315 | 43 | https://x.com/regent0x_/status/2057419591618302029 |
| @HeyZaraKhan | 20 Claude GitHub Repos that can completely change your life (save this) — includes Claude Code, Awesome MCP Servers, SuperClaude Framework | 667 | 163 | https://x.com/HeyZaraKhan/status/2056422617351959030 |
| @regent0x_ | $50 raspberry pi running AI in the palm of his hand — no plugins, no MCP servers, no 62,000 tokens of overhead | 129 | 21 | https://x.com/regent0x_/status/2059559047888507213 |
| @0xluffy_eth | 想系统学习 Claude — 20 GitHub repos list (Claude Code, MCP Servers, SuperClaude) | 144 | 54 | https://x.com/0xluffy_eth/status/2057719369137037793 |
| @stackzz | MCP tourists are about to get rinsed by their own integrations | 71 | 1 | https://x.com/stackzz/status/2056026387597885457 |
| @pauliusztin_ | New way of building software powered by AI — skills, CLI, MCP used together | 50 | 7 | https://x.com/pauliusztin_/status/2063236967987298550 |
| @regent0x_ | his dad built a $2M company on a 1986 macintosh plus — no drivers, no setup | 49 | 4 | https://x.com/regent0x_/status/2058079320405332047 |
| @polsia | Built the open directory for Claude Code, Cursor, and Windsurf extensions. 2,000+ skills, MCP servers | — | — | https://x.com/polsia/status/2064450681856200753 |
| @AndrewK404 | Skill = teach Claude one workflow. Plugin = package and share a broader toolkit. | 2 | 1 | https://x.com/AndrewK404/status/2059732591222096368 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| pramodbiligiri | Harness engineering: Leveraging Codex in an agent-first world | 296 | 206 | — | https://openai.com/index/harness-engineering/ |
| Alifatisk | DeepSeek reasonix, DeepSeek native coding agent with high caching and low cost | 729 | 288 | — | https://esengine.github.io/DeepSeek-Reasonix/ |
| kevinsimper | Qwen3.7-Max: The Agent Frontier | 721 | 290 | — | https://qwen.ai/blog?id=qwen3.7 |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| prakashqwerty | AI Agent Guidelines for CS336 at Stanford | 502 | 153 | — | https://github.com/stanford-cs336/assignment1-basics/blob/main/CLAUDE.md |
| tanelpoder | AI agent runs amok in Fedora and elsewhere | 439 | 183 | — | https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/ |
| laxmena | My Agent Skill for Test-Driven Development | 251 | 109 | — | https://www.saturnci.com/my-agent-skill-for-test-driven-development.html |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| StanAngeloff | Zot – Yet another coding agent harness | 107 | 82 | — | https://www.zot.sh |
| EvanZhouDev | Microsoft announces Scout, autonomous AI agent built on OpenClaw | 94 | 87 | — | https://www.computerworld.com/article/4180103/microsoft-unveils-scout-an-autonomous-ai-agent-built-on-openclaw.html |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| Bindfort | Official MCP servers ship known-vulnerable dependencies at install time | 3 | — | — | https://bindfort.com/research/mcp-supply-chain-scan |
| PengSpirit | Show HN: MCP Registry – NPM-style install for MCP servers | 3 | — | — | https://mcp-registry-dh5.pages.dev |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |
| sermakarevich | Show HN: Generate Claude Code Workflows using Spec Driven Development approach | 5 | — | — | https://news.ycombinator.com/item?id=48306730 |
| bengal | Show HN: OAuth 2.0 framework for MCP servers | 3 | — | — | https://github.com/brooksmcmillin/mcp-authflow |
| nhattruongadm | Show HN: MCPSafe – Free security scanner for MCP servers using 5-LLM consensus | 3 | — | — | https://mcpsafe.io |
| allenwu06 | Show HN: Mcpaudit – static security scanner for MCP servers | 3 | — | — | https://github.com/allenwu-blip/mcpaudit |
| Anon84 | AgentSploit – Burp Suite for AI Agents and MCP Servers | 3 | — | — | https://github.com/agentsploit/agentsploit |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | — | — | https://github.com/OpenYabby/OpenYabby |
| nmfisher | Claude Code and Blender MCP | 3 | — | — | https://hydroxide.dev/articles/blender-mcp-claude-code/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | I'm pretty confident I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | I use my own local tools, not Claude Code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @camilleroux.com | Mon top 13 des skills et plugins Claude Code qui ont marqué 2026: celui qui coupe 63% des tokens de sortie, celui qui rejoue tes sessions comme une vidéo... | 8 | https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p |
| @brunopedro.com | 42Crunch announced integration with Anthropic's Claude Code, dedicated AI coding plugins for autonomous end-to-end Agentic DevSecOps | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @webuyhousesusa.bsky.social | ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — free, MIT-licensed | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @github-trending-js.bsky.social | Ruflo: multi-agent AI orchestration framework extending Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @mengli512.bsky.social | Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression. Have you tried them yet? | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |
| @viriditax.bsky.social | When newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it to flex it | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @toyinariyo.bsky.social | There are also many Godot AI plugins that can be used with Claude Code and Codex. Here's one of them | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claude.com | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Official dynamic workflows announcement; parallel subagents, background execution |
| claude.com | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Full dynamic workflows guide with phase/agent/pipeline primitives |
| arps18.github.io | https://arps18.github.io/posts/claude-code-mastery/ | Highest-engagement community guide: Claude.md, Skills, Subagents, Plugins, MCPs |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Decision heuristic: CLI → Skill → MCP → Plugin, lightest first |
| dev.to | https://dev.to/thlandgraf/claude-code-workflows-the-plan-moves-out-of-claudes-head-and-into-a-script-you-can-edit-3k4b | Dynamic workflows: plan moves out of Claude's head into editable script |
| claudelab.net | https://claudelab.net/en/articles/claude-code/claude-code-dynamic-workflow-authoring | Dynamic workflow authoring with phase/agent/pipeline primitives |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Taxonomy: skills, agents, hooks, MCP, LSP explained |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Skills as markdown slash commands vs MCP servers as external services |
| alexcloudstar.com | https://www.alexcloudstar.com/blog/claude-code-plugin-marketplace-skills-2026/ | Plugin marketplace guide: how skills, MCP, and plugins fit together in 2026 |
| llmbestpractices.com | https://llmbestpractices.com/howto/set-up-an-mcp-claude-code-skill | How to set up an MCP skill for Claude Code (practical setup guide) |
| alatirok.com | https://alatirok.com/mcp-server-discovery/ | MCP server discovery via .well-known files; two competing SEPs, neither merged |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_subagents_and_orchestration_guide.html | Multi-agent orchestration: delegation, parallel fan-out, custom agent definitions |
| qcode.cc | https://qcode.cc/en/claude-code-dynamic-workflows-guide | Dynamic workflows guide; practical ceiling 5-7 MCP servers before perf degradation |
| medium.com | https://medium.com/neuralnotions/the-plugin-layer-packaging-versioning-and-distributing-ai-agent-capabilities-at-scale-e0f41eccd123 | Plugin layer: packaging, versioning, distributing AI agent capabilities at scale |
| bindfort.com | https://bindfort.com/research/mcp-supply-chain-scan | Official MCP servers ship known-vulnerable dependencies at install time |
| saturnci.com | https://www.saturnci.com/my-agent-skill-for-test-driven-development.html | Agent skill for TDD (251 HN pts); real-world skill authoring example |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 20,300+ skills, 2,500+ marketplaces, 9,900+ MCP servers indexed |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 8 major skill marketplaces by Q2 2026; Skills.sh as npm for skills |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries compared; fragmentation as #1 friction |
| aaif.io | https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/ | MCP Dev Summit 2026: OAuth 2.1, RFC 8707, enterprise adoption |
| releasebot.io | https://releasebot.io/updates/anthropic/claude-code | Claude Code June 2026 changelog: /plugin list, dynamic workflows, Opus 4.8 default |
| github.com | https://github.com/anthropics/claude-plugins-official | Official Anthropic-managed directory of high quality Claude Code Plugins |
| github.com | https://github.com/netresearch/claude-code-marketplace | Cross-agent skills (agentskills.io open standard); 30+ agents supported |
| github.com | https://github.com/Friz-zy/ai-capability-registry | GitOps-style registry for AI agent workflows, skills, and MCP servers |
| github.com | https://github.com/modelcontextprotocol/registry | Official MCP Registry v1.7.9; app store for MCP servers |
| pkg.go.dev | https://pkg.go.dev/github.com/modelcontextprotocol/registry | Official MCP Registry Go module; v1.7.9 |
| openmodels.run | https://github.com/openmodelsrun/mcp | Open-source registry of MCP servers with structured metadata and install configs |
| sre.azure.com | https://sre.azure.com/docs/capabilities/plugin-marketplace | Azure SRE Agent plugin marketplace: browse/install skills from GitHub-hosted marketplaces |
| support.claude.com | https://support.claude.com/en/articles/13837440-use-plugins-in-claude | Official Claude Help Center: using plugins in Claude |

---

## Stats Block

```
├─ 🟠 Reddit: 12 threads
├─ 🔵 X: 13 posts │ 1,515 likes │ 339 reposts
├─ 🟢 HN: 39 stories │ 4,980 points │ 2,483 comments
├─ 🦋 Bluesky: 12 posts │ 92 likes │ 6 reposts
├─ 🌐 Web: 26 pages (19 engine + 7 WebSearch) - claudelab.net, dev.to, claude.com, claudemarketplaces.com, agensi.io, truefoundry.com, aaif.io
└─ 🗣️ Top voices: @regent0x_, @polsia, @AndrewK404 │ r/ClaudeAI, r/ClaudeWorkflows
```

---

## Data Gaps

- **YouTube: 0 results** — yt-dlp search returned nothing; ScrapeCreators returned HTTP 402. No video coverage of Claude Code skills/plugin ecosystem despite likely existing content.
- **TikTok: 0 results** — ScrapeCreators returned HTTP 402 for TikTok search.
- **Instagram: 0 results** — SC v2 reels endpoint errored; multi-token query likely too broad.
- **Polymarket: 0 markets** — No prediction markets on this topic, as expected for a developer tooling topic.
- **GitHub: 0 results** — No GitHub token configured; `gh` CLI not authenticated. Several key repos (claude-plugins-official, netresearch/claude-code-marketplace) were found via WebSearch instead.
- **Reddit keyless fallback** — Reddit returned 403 on direct API queries; RSS tier returned 25 posts but 0 scored; ScrapeCreators served Reddit results instead. Some highly-engaged threads (e.g., the "mess is MCP" post) appear in corpus but without upvote counts.
- **X engagement gaps** — Several X posts have engagement data (likes/reposts) but many cluster-demoted posts show 0 scores due to entity-miss demotion from the long multi-term query string.
- **Coverage estimate: ~65%** of relevant activity captured. Missing: YouTube tutorials (likely 20+ relevant videos), TikTok demos, private Discord/Slack discussions, and deeper Reddit threads from niche subreddits (r/ClaudeCode, r/LocalLLaMA activity on MCP).

---

## Key Quotes

> "The day-to-day is mess. One specific kind of mess: MCP servers in production." — r/ClaudeAI ([link](https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/))

> "$50 raspberry pi running AI in the palm of his hand — no plugins, no MCP servers, no 62,000 tokens of overhead — just ollama and a terminal. This guy saw that video and deleted everything from his $4,000 MacBook." — [@regent0x_](https://x.com/regent0x_/status/2059559047888507213) on X

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." — [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368) on X

> "MCP tourists are about to get rinsed by their own integrations. Every MCP server is a permission surface: what can it read? what can it write? can it touch money, keys, deploys, or customer data?" — [@stackzz](https://x.com/stackzz/status/2056026387597885457) on X

> "Connectivity is not one thing. The best agents use all of it — skills, CLI, MCP — together." — David Soria Parra (MCP co-creator), cited by [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550) on X

> "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." — [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) on Bluesky

> "Subagents, skills, and agent teams all keep the plan in one place: Claude's head. Dynamic workflows move the plan out of Claude's head and into a script you can edit." — [dev.to](https://dev.to/thlandgraf/claude-code-workflows-the-plan-moves-out-of-claudes-head-and-into-a-script-you-can-edit-3k4b)

> "I'm pretty confident I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "The space is getting crowded. Time to stand out." — [@polsia](https://x.com/polsia/status/2064450681856200753) on X, announcing an open directory for Claude Code, Cursor, and Windsurf extensions
