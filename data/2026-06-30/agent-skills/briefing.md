# Agent Skills & Claude Code Extension Ecosystem — Daily Briefing
**Date:** 2026-06-30
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 8 threads | 74 upvotes, 116 comments | All from r/ClaudeAI |
| X/Twitter | 75 posts | 7,088 likes, 723 reposts | Key voices: @alexalbert__, @ClaudeCodeLog, @tetsuoai |
| Hacker News | 31 stories | 4,896 points, 2,548 comments | Highest-engagement source |
| Bluesky | 9 posts | 67 likes, 6 reposts | — |
| GitHub | 32 items | 2,180 reactions, 977 comments | anthropics/claude-code (133K stars) |
| Web | 14 pages + 12 supplements | — | via engine + WebSearch |

---

## Synthesized Findings

### 1. The Extension Architecture Is Maturing — Five Distinct Layers, Each with a Job

The Claude Code extension stack has converged on five primitives: **CLAUDE.md** (always-on context, the repo "constitution"), **Skills** (on-demand SKILL.md files that load only when invoked, saving tokens), **MCP Servers** (external system connectors), **Subagents** (isolated context windows for bounded tasks), and **Hooks** (lifecycle automation). The community has started calling the wrong-layer mistake by name. As [@ranjankumar put it](https://x.com/ranjankumar/status/2071830751528771821): "You add a subagent to fix Claude's tool choices. Now you have a subagent managing which code tool to use, and Claude still defaults wrong half the time because the subagent only fires when invoked, not on every session. You needed one line in CLAUDE.md. This is the core failure mode: reaching for the wrong layer."

The practitioner guide on [codersera.com](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/) and the official [Anthropic blog post on dynamic workflows](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) both converge on the same pattern: pin one MCP per external system, write thin Skills that orchestrate them, use CLAUDE.md for always-on rules. The SKILL.md format is now an open standard adopted across Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, and GitHub Copilot — per [codersera.com](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/).

Discussed on: X, Web, Reddit, HN

### 2. MCP Servers Had a Massive Week — X Platform Launches Official Hosted Servers

The biggest MCP news this week: X (Twitter) launched hosted MCP servers letting any MCP client connect directly to the platform. [@tetsuoai](https://x.com/tetsuoai/status/2071775282420445427) (701 likes, 90 reposts) broke it down: "X MCP (`httpx://api.x.com/mcp`) — search posts, manage bookmarks, fetch trends/news, and draft/publish Articles with your account permissions. Docs MCP (`httpx://docs.x.com/mcp`) — instantly search and read X API docs inside your workflow." This follows the broader platform MCP adoption trend: AWS releasing official MCP servers, skills, and plugins per [probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f).

On the production side, [@deenaik](https://x.com/deenaik/status/2071895596861153619) shared a real-world benchmark: "Traditional VAPT takes days. We built an autonomous AI security team at Digite Inc. that slashes it to <6 hours. Using Claude Code, 14 MCP servers & 7 parallel agents, we automated everything with 0 false positives."

[@lukashanren1](https://x.com/lukashanren1/status/2071900526564831679) captured the integration pitch plainly: "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code — unless you use MCP."

Discussed on: X, Bluesky, HN

### 3. The Marketplace Explosion — Eight Registries in Six Months, Discovery Now the Problem

The agent skills marketplace ecosystem went from one registry in December 2025 to eight major marketplaces by Q2 2026, per [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). [claudemarketplaces.com](https://claudemarketplaces.com/) tracks 21,600+ skills, 2,500+ marketplaces, and 12,500+ MCP servers. [skillselion.com](https://skillselion.com/state-of-ai-agent-skills-2026) puts total tracked AI coding-agent tools at 84,373 (65,629 agent skills, 7,842 MCP servers, 8,517 marketplaces) with 116M combined installs.

On the MCP registry side, the three leaders are mcp.so (20,222 servers), Smithery (7,000+ servers, described as the closest equivalent to Docker Hub), and PulseMCP — per [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries). The [2026 MCP retrospective at digitalapplied.com](https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points) notes the spec crossed 9,400 distinct servers by mid-April 2026.

The irony flagged by [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026): "developers now spend more time comparing marketplaces than they spend finding skills." Emerging solutions include the MCP Server Cards proposal (`.well-known` URLs for capability discovery) and tools like MCP Compass (natural-language-driven server discovery).

Show HN submissions on HN this month surfaced multiple registry experiments: [CodeGuilds](https://codeguilds.dev) (community registry for Claude Code skills, agents, MCP servers — 3pts, Jun 1), [ai-capability-registry](https://github.com/Friz-zy/ai-capability-registry) (GitOps-style registry for Workflows, Skills, and MCP servers — 4pts), and [Web Speed](https://www.getwebspeed.io/) (shared web-map registry for AI agents via MCP — 7pts).

Discussed on: HN, Web, X, Bluesky

### 4. Token Waste from Bloated Context Is a Real Production Problem

One of the highest-engagement Reddit threads this month: [r/ClaudeAI — "Using Claude Code? You're probably wasting ~8k tokens per session on unused skills."](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) (3pts, 21 comments). The author found 187 items loading at session start with only 4 actively used, wasting ~8,000 tokens per session on dead weight "hurting the prompt cache hit rate and adding latency." They built a CLI to fix it. This is a practical gap in how plugins and skills are currently loaded — everything loads eagerly regardless of relevance.

The problem is real enough that GitHub issue [#66032 on anthropics/claude-code](https://github.com/anthropics/claude-code/issues/66032) explicitly requests making Workflow scripts (`.claude/workflows/*.js`) a distributable plugin component — acknowledging that current workflow distribution is an unsolved packaging problem.

Discussed on: Reddit, GitHub

### 5. Claude Code v2.1.196 Drops — MCP Security Change and Org Controls

[Claude Code 2.1.196](https://x.com/ClaudeCodeLog/status/2071742057517850717) ([@ClaudeCodeLog](https://x.com/ClaudeCodeLog), 270 likes) shipped with 27 CLI changes. The MCP-relevant ones: `mcp list/get` no longer auto-starts repo-local servers — untrusted workspaces now show a "Pending approval" gate. This is a direct response to MCP server trust/security concerns. Also: org admins can now set a default model at the console level, and Grep is now the officially recommended search tool over find/ls.

The security angle extends beyond this release. HN this month surfaced multiple agent security discussions: [A €0.01 bank transfer could compromise a banking AI agent](https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/) (208pts, 202 comments), [AI agent runs amok in Fedora](https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/) (552pts, 245 comments), and [Show HN: Diplomat-agent scan Python MCP servers for unguarded tool calls](https://github.com/Diplomat-ai/diplomat-agent) — all pointing to MCP surface area as the primary attack vector for production agents.

Discussed on: X, HN

### 6. Skills for Testing, Evals, and Methodological Rigor

From [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u6f7cr/what_i_learned_writing_an_eval_harness_for_my_own/) (3pts, 3 comments): "I spent two months writing a Claude Code skill pack that enforces methodological rigor on RAG, agent, and MCP server work. Last week I built a test harness for it. The harness caught two real bugs. One was in the skill that's supposed to enforce the most important methodology gate I'd written. The skill failed its own gate." This thread captures an emerging best practice: SKILL.md files themselves need unit tests, and building eval harnesses for skills is now considered production-grade engineering.

HN's [My Agent Skill for Test-Driven Development](https://www.saturnci.com/my-agent-skill-for-test-driven-development.html) (251pts, 109 comments, Jun 4) was one of the highest-engagement HN posts on the topic this month, reinforcing that TDD-as-skill is a pattern the community actively wants.

Discussed on: Reddit, HN

### 7. Subagents Are About Memory, Not Just Speed

From r/ClaudeAI: ["Subagents in Claude Code aren't a speed trick. They're a memory trick"](https://www.reddit.com/r/ClaudeAI/comments/1u71d27/subagents_in_claude_code_arent_a_speed_trick/) (16 comments) — "Most subagent posts sell parallelism: fan out five agents, get your answer five times faster. That's real, but it isn't why they matter... The thing a subagent actually buys you is a clean main context." This reframes the extension-type taxonomy: subagents aren't a performance primitive, they're a context-isolation primitive.

[@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (558 likes) echoed the "team" framing: "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." And on Fable: "Rework your skills and CLAUDE.mds. Instructions written for prior models anchor Fable to stale patterns, let it use its own judgment first."

Discussed on: Reddit, X

### 8. Plugin Packaging and Distribution — The Missing Developer Workflow

[Bluesky user @jefferyharrell](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes, 2 reposts): "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." Same user a few hours later: "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

The community registry [tech-leads-club/agent-skills](https://github.com/tech-leads-club/agent-skills) (4,773 GitHub stars) describes itself as "the secure, validated skill registry for professional AI coding agents. Extend Antigravity, Claude Code, Cursor, Copilot and more with absolute confidence." [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) offers 425 plugins, 2,810 skills, 200 agents with a ccpi CLI package manager at tonsofskills.com.

The production MCP complexity problem was captured most directly in r/ClaudeAI's ["I ship AI agents in production. The mess is MCP."](https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/) (64pts, 38 comments): "The day-to-day is mess. One specific kind of mess: MCP servers in production." The thread covers auth, versioning, and orchestration challenges.

Discussed on: Bluesky, Reddit, GitHub, Web

---

## Cross-Source Patterns

**Pattern 1: "Which layer?" is the dominant confusion** — X, Web, Reddit, and HN all converge on developers picking the wrong Claude Code extension type (subagent when they needed CLAUDE.md, MCP when they needed a skill). Multiple explainer posts this month (mcsaguru.com, claudskills.com, maketocreate.com, tygartmedia.com, dev.to) exist solely to answer this question. Signal on Reddit, X, and HN is consistent: the 5-layer taxonomy (CLAUDE.md / Skills / MCP / Subagents / Hooks) is now the canonical mental model, but many devs are still learning it.

**Pattern 2: MCP security is the emerging production concern** — HN (A €0.01 bank transfer compromised a banking agent, 208pts; AI agent runs amok in Fedora, 552pts) + Claude Code v2.1.196 (mcp list/get no longer auto-starts repo-local servers) + Diplomat-agent (MCP security scanner) + sooyoon_eth reply to @alexalbert__ ("delegating to a model directly in slack is incredible for velocity, but also lowkey terrifying if it has ambient access to internal tools") — all pointing to MCP attack surface as the production trust problem.

**Pattern 3: Marketplace fragmentation is the discovery problem** — Web (8 major marketplaces by Q2 2026), HN (multiple Show HN registry experiments), X (agent skills roundups) — the problem has shifted from "where do I find skills?" to "how do I evaluate skills across 8 different registries?" MCP Server Cards and MCP Compass are early standardization responses.

**Pattern 4: Token waste from eager skill loading** — Reddit (8k tokens wasted per session), GitHub (#66032 feature request for distributable workflows), community CLI tools to fix it — a real production friction point with no official solution yet.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I ship AI agents in production. The mess is MCP. | 64 | 38 | "Three months ago a client asked me to wire Claude Code into their internal workflow... The day-to-day is mess." | https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/ |
| r/ClaudeAI | Using Claude Code? You're probably wasting ~8k tokens per session on unused skills. | 3 | 21 | "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight" | https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/ |
| r/ClaudeAI | What I learned writing an eval harness for my own SKILL.md files (it caught two real bugs) | 3 | 3 | "The skill `rag-eval-harness` is supposed to refuse single-source evaluations. The skill failed its own gate." | https://www.reddit.com/r/ClaudeAI/comments/1u6f7cr/what_i_learned_writing_an_eval_harness_for_my_own/ |
| r/ClaudeAI | Subagents in Claude Code aren't a speed trick. They're a memory trick | — | 16 | "The thing a subagent actually buys you is a clean main context." | https://www.reddit.com/r/ClaudeAI/comments/1u71d27/subagents_in_claude_code_arent_a_speed_trick/ |
| r/ClaudeAI | Going back to work after a break. Where do I start with Claude Code? | 2 | 11 | "My team has switched to using Claude Code for almost all of their tasks. This is a drastically different landscape." | https://www.reddit.com/r/ClaudeAI/comments/1ufu1hj/going_back_to_work_after_a_break_where_do_i_start/ |
| r/ClaudeAI | As a solo builder I created a multi tenant B2B SaaS in 2 months using Claude code | 1 | 11 | Business admin background, no formal SE background. Built agentic AI SaaS from scratch. | https://www.reddit.com/r/ClaudeAI/comments/1ueiwxi/as_a_solo_builder_i_created_a_multi_tenant_b2b/ |
| r/ClaudeAI | Claude x Codex combination is slow but time + money saving | 1 | 7 | "Even with latest models like Opus 4.8 it tries to take shortcuts" | https://www.reddit.com/r/ClaudeAI/comments/1txal2l/claude_x_codex_combination_is_slow_but_time_money/ |
| r/ClaudeAI | I built a free practice exam for the Claude Certified Architect cert | — | 9 | 60 scenario questions across research pipelines, extraction, customer support, agent architecture | https://www.reddit.com/r/ClaudeAI/comments/1ucvi19/i_built_a_free_practice_exam_for_the_claude/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @tetsuoai | X just launched hosted MCP servers so AI tools can connect directly to the platform... | 701 | 90 | https://x.com/tetsuoai/status/2071775282420445427 |
| @alexalbert__ | We've reset usage limits across our products! For those just starting to test Fable... Rework your skills and CLAUDE.mds. Instructions written for prior models anchor Fable to stale patterns... | 2,957 | 171 | https://x.com/alexalbert__/status/2064467657483829441 |
| @alexalbert__ | This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team. | 558 | 15 | https://x.com/alexalbert__/status/2069470389391241314 |
| @alexalbert__ | Fable feels superhuman at working over long agentic conversations, sometimes to the point where I can't keep up with what it's telling me 😅 | 1,039 | 30 | https://x.com/alexalbert__/status/2065493229760565758 |
| @ClaudeCodeLog | Claude Code 2.1.196 has been released. 27 CLI changes... mcp list/get no longer auto-starts repo-local servers; untrusted workspaces show ⏸ Pending approval | 270 | 7 | https://x.com/ClaudeCodeLog/status/2071742057517850717 |
| @OlivercrestAI | Claude Code just dropped version 2.1.196. 27 CLI changes. Grep is now the officially recommended search tool... | 8 | 3 | https://x.com/OlivercrestAI/status/2071895983428972606 |
| @Tech_Rose1 | Claude is offering 18 official AI courses with certificates... 5 - Introduction to Agent Skills. | 112 | 52 | https://x.com/Tech_Rose1/status/2071781383551500353 |
| @deenaik | Traditional VAPT takes days. We built an autonomous AI security team using Claude Code, 14 MCP servers & 7 parallel agents, 0 false positives | 1 | 1 | https://x.com/deenaik/status/2071895596861153619 |
| @gabrielgtapps | 1. claude-code-setup - I run it as a weekly routine. It looks at the stack, structure, package.json, layout, and recommends the highest-value Claude Code automations: skills hooks MCP servers subagents slash commands | 2 | 1 | https://x.com/gabrielgtapps/status/2071698549490724897 |
| @lukashanren1 | Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code — unless you use MCP. | — | — | https://x.com/lukashanren1/status/2071900526564831679 |
| @ranjankumar | Which Claude Code Layer Solves Your Problem? A Diagnostic Guide for AI Engineers... You needed one line in CLAUDE.md. This is the core failure mode: reaching for the wrong layer. | — | — | https://x.com/ranjankumar/status/2071830751528771821 |
| @sooyoon_eth | @alexalbert__ delegating to a model directly in slack is incredible for velocity, but also lowkey terrifying if it has ambient access to internal tools. how are teams currently isolating authority? | — | — | https://x.com/sooyoon_eth/status/2071829177469399338 |
| @appsicle_ | experiencing 5 hour window usage limits draining faster... modified caveman plugin to reduce verbosity - rtk ai for tool calls - playwright cli to replace computer use mcp servers... | 8 | — | https://x.com/appsicle_/status/2071652668427084025 |
| @github_update | AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking | 8 | 2 | https://x.com/github_update/status/2067259115777507386 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| xiaoyu2006 | AI agent bankrupted their operator while trying to scan DN42 | 1,467 | 535 | Security failure from autonomous agent with tool access | https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/ |
| tanelpoder | AI agent runs amok in Fedora and elsewhere | 552 | 245 | LWN coverage of agent permission/security failures | https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/ |
| kkm | How to setup a local coding agent on macOS | 507 | 127 | Practical guide for local Claude Code deployment | https://ikyle.me/blog/2026/how-to-setup-a-local-coding-agent-on-macos/ |
| engmarketer | I used Claude Code to get a second opinion on my MRI | 554 | 688 | Medical use case showing agentic capabilities | https://antoine.fi/mri-analysis-using-claude-code-opus |
| pjungwir | My Claude Code Setup | 507 | 127 | Personal setup guide with Claude Code | https://illuminatedcomputing.com/posts/2026/06/my-claude-code-setup/ |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | "Extended thinking output is not authentic" — critique of thinking token transparency | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| laxmena | My Agent Skill for Test-Driven Development | 251 | 109 | TDD as a reusable agent skill pattern | https://www.saturnci.com/my-agent-skill-for-test-driven-development.html |
| tvissers | A €0.01 bank transfer could compromise a banking AI agent | 208 | 202 | Security analysis of MCP tool call injection | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |
| EvanZhouDev | Microsoft announces Scout, an autonomous AI agent built on OpenClaw | 94 | 87 | Enterprise agent platform built on open frameworks | https://www.computerworld.com/article/4180103/microsoft-unveils-scout-an-autonomous-ai-agent-built-on-openclaw.html |
| prakashqwerty | AI Agent Guidelines for CS336 at Stanford | 503 | 153 | CLAUDE.md from Stanford CS336; academia adopting skills format | https://github.com/stanford-cs336/assignment1-basics/blob/main/CLAUDE.md |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 36 | 12 | Pricing pause after community pushback | https://news.ycombinator.com/item?id=48546618 |
| har-ki | Running Claude Code Offline on an M3 Pro with Qwen3.6 | 18 | 10 | Air-gapped / offline Claude Code deployment | https://har-ki.github.io/claude-code-sre-handbook/handbook/06-air-gapped/ |
| jguarnelli | Show HN: Diplomat-agent scan Python MCP servers for unguarded tool calls | 3 | — | Security scanner for MCP servers | https://github.com/Diplomat-ai/diplomat-agent |
| nrengan | Show HN: A readiness scorer for MCP servers, checked against emerging standards | 4 | 1 | MCP server compliance checker | https://isyourmcpready.com |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | Version-controlled skill/workflow registry | https://github.com/Friz-zy/ai-capability-registry |
| prakashqwerty | CodeGuilds — community registry for Claude Code (skills, agents, MCP servers) | 3 | — | Community registry; Show HN | https://codeguilds.dev |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods. I wanna spend six hours meticulously curating a mod list... | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @probbrain.bsky.social | GitHub Trending: AWS releases official MCP servers, skills, and plugins enabling AI agents to build... | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |
| @github-trending-js.bsky.social | Ruflo is a multi-agent AI orchestration framework that extends Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation, and a suite of plugins and tools (MCP, memory, GOAP planning, Web UI) | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @brunopedro.com | 42Crunch announced a breakthrough integration with Claude Code, introducing dedicated AI coding plugins for autonomous Agentic DevSecOps | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @viriditax.bsky.social | when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @toyinariyo.bsky.social | There are also many Godot AI plugins that can be used with Claude Code and Codex | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |
| @mikaelbuilds.bsky.social | Claude Code "still running" is not one bug. I built a no-secret packet for v2.1.179-style remote failures: status, remote vs shell, WSL2, sandbox globs, plugins, background-task state | 1 | https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Largest community directory; 21,600+ skills, 12,500+ MCP servers |
| skillselion.com | https://skillselion.com/state-of-ai-agent-skills-2026 | 84,373 tools tracked, 116M combined installs as of 2026 |
| tech-leads-club/agent-skills (GitHub) | https://github.com/tech-leads-club/agent-skills | 4,773 stars; validated skill registry for Claude Code, Cursor, Copilot, Antigravity |
| jeremylongshore/claude-code-plugins-plus-skills (GitHub) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; ccpi CLI package manager |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Eight major marketplaces by Q2 2026; discovery fragmentation analysis |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries comparison; mcp.so (20,222 servers), Smithery (7,000+), PulseMCP |
| digitalapplied.com | https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points | MCP H1 2026 retrospective; 9,400 servers by mid-April |
| anthropics/claude-code GitHub issue #66032 | https://github.com/anthropics/claude-code/issues/66032 | Feature request: make Workflow scripts distributable plugin components |
| claude.com/blog | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Anthropic on dynamic workflows — Claude writes its own multi-agent harness |
| maketocreate.com | https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/ | Practitioner decision guide: Skills vs MCP |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Open SKILL.md registry; extension surface comparison |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Plugins vs Skills vs MCP layer explanation |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills vs MCP vs Connectors vs Plugins taxonomy |
| dev.to (rapls) | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Lightest-first extension selection heuristic |
| dev.to (thlandgraf) | https://dev.to/thlandgraf/claude-code-workflows-the-plan-moves-out-of-claudes-head-and-into-a-script-you-can-edit-3k4b | Claude Code Workflows: plan as code rather than in-context |
| codersera.com | https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/ | Practitioner's guide; SKILL.md as cross-agent open standard |
| skillavatars.com | https://www.skillavatars.com/articles/mcp-registry-navigator-ad6e | mcp-registry-navigator Claude Skill for MCP discovery |
| boringbot.substack.com | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Skills, Subagents, Hooks, Plugins, and Harnesses for production multi-agent workflows |
| docs.cloud.google.com | https://docs.cloud.google.com/agent-registry/concepts | Google Cloud Agent Registry key concepts |

---

## Stats Block

```
├─ 🟠 Reddit: 8 threads │ 74 upvotes │ 116 comments
├─ 🔵 X: 75 posts │ 7,088 likes │ 723 reposts
├─ 🟢 HN: 31 stories │ 4,896 points │ 2,548 comments
├─ 🦋 Bluesky: 9 posts │ 67 likes │ 6 reposts
├─ 🐙 GitHub: 32 items │ 2,180 reactions │ 977 comments
├─ 🌐 Web: 14 engine pages + 12 WebSearch supplements
└─ 🗣️ Top voices: @alexalbert__, @ClaudeCodeLog, @tetsuoai │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 results** — ScrapeCreators HTTP 402 (quota exceeded), yt-dlp returned no results for this query. YouTube likely has significant tutorial/review content on Claude Code skills and MCP that is missing from this briefing.
- **TikTok: 0 results** — ScrapeCreators HTTP 402 across all hashtag attempts (#claudecode, #mcpserver, #aiagent, #aicoding, #mcp). TikTok creator content on Claude Code workflows is unrepresented.
- **Instagram: 0 results** — ScrapeCreators HTTP 402. Likely limited signal for this developer-focused topic.
- **Reddit: thin coverage** — Only 8 threads returned, all from r/ClaudeAI. The dedicated r/ClaudeCode subreddit returned 0 posts via the dedicated lane (RSS feed failures). r/ChatGPTCoding, r/LocalLLaMA, and r/artificial returned 0 on-topic results. Reddit is the highest-signal gap.
- **Polymarket: 0 markets** — No prediction markets on Claude Code ecosystem topics. Expected.
- **Noise in X** — Significant Concordium (blockchain) and MPP Layer (Solana DeFi) posts were captured via related handle searches but filtered out of the synthesis. The @Dpw_Jules and @getmpplayer X voices in the engine stats are largely off-topic (crypto/DeFi noise).
- **Coverage estimate:** Core developer discussion well-represented via HN (31 stories, 4,896pts) and X (75 posts); Reddit and YouTube represent the main gaps. Estimated ~65% coverage of available signal.

---

## Key Quotes

> "You add a subagent to fix Claude's tool choices. Now you have a subagent managing which code tool to use, and Claude still defaults wrong half the time because the subagent only fires when invoked, not on every session. You needed one line in CLAUDE.md. This is the core failure mode: reaching for the wrong layer." — [@ranjankumar](https://x.com/ranjankumar/status/2071830751528771821) on X

> "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate and adding latency." — [u/r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) on the context bloat problem

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "The thing a subagent actually buys you is a clean main context. Anthropic's own docs put it plainly: a subagent 'does that work in its own context and returns only the result.'" — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u71d27/subagents_in_claude_code_arent_a_speed_trick/)

> "Traditional VAPT takes days. We built an autonomous AI security team at Digite Inc. that slashes it to <6 hours. Using Claude Code, 14 MCP servers & 7 parallel agents, we automated everything with 0 false positives." — [@deenaik](https://x.com/deenaik/status/2071895596861153619) on X

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314), Claude Code lead at Anthropic

> "The skill `rag-eval-harness` is supposed to refuse single-source evaluations. The skill failed its own gate. The bug was in the skill that's supposed to enforce the most important methodology gate I'd written." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u6f7cr/what_i_learned_writing_an_eval_harness_for_my_own/) on why SKILL.md files need their own test harnesses

> "X just launched hosted MCP servers so AI tools can connect directly to the platform. Connect Grok Build, Cursor, Claude, VS Code, or any MCP client to two official servers." — [@tetsuoai](https://x.com/tetsuoai/status/2071775282420445427) (701 likes), breaking X's MCP launch

> "Rework your skills and CLAUDE.mds. Instructions written for prior models anchor Fable to stale patterns, let it use its own judgment first. Move from providing tasks to providing outcomes." — [@alexalbert__](https://x.com/alexalbert__/status/2064467657483829441) on adapting to Fable (2,957 likes)

> "Delegating to a model directly in slack is incredible for velocity, but also lowkey terrifying if it has ambient access to internal tools. How are teams currently isolating authority in these collaborative agent spaces so one compromised prompt doesn't nuke prod?" — [@sooyoon_eth](https://x.com/sooyoon_eth/status/2071829177469399338) replying to @alexalbert__
