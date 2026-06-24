# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-24
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Reddit, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 4 threads | — | r/ClaudeWorkflows only; public API 403'd |
| X/Twitter | 31 posts | 4,449 likes, 476 reposts | @ClaudeCodeLog dominant voice |
| Hacker News | 38 stories | 2,064 points, 864 comments | Highest volume source |
| Bluesky | 11 posts | 83 likes, 6 reposts | Developer discussion |
| GitHub | 14 items | 234 reactions, 101 comments | PR/issue signal |
| Web | 18 pages | — | Guides, registries, official docs |

---

## Synthesized Findings

### 1. Anthropic's Official Plugin Registry Hit 30,759 Stars - And It's "Just a List"

The biggest signal this week: `claude-plugins-official` - Anthropic's own curated directory of vetted Claude Code plugins - crossed 30,759 GitHub stars, making it one of the fastest-growing repos in the ecosystem. The reaction from [@chenzeling4](https://x.com/chenzeling4/status/2069494704589418744) captured the community mood perfectly: "30,759 stars and it's literally just a list." The directory standardizes the structure for MCP servers, slash commands, agent definitions, and skills so that a single install command handles all of them. Per the [official plugin marketplace docs](https://code.claude.com/docs/en/plugin-marketplaces), plugins are versioned bundles - MCP servers + slash commands + skills - distributed via marketplaces and installable with `npx skills add`. As of March 2026 the official Anthropic marketplace ships 101 vetted plugins plus 68 partner plugins from Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase, per [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review).

The community-side numbers dwarf the official count. [claudemarketplaces.com](https://claudemarketplaces.com/) indexes 21,600+ skills, 2,500+ marketplaces, and 12,500+ MCP servers, drawing 300,000+ developer visits per month. The community repo [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) alone ships 425 plugins, 2,810 skills, and 200 agents, with a `ccpi` CLI package manager and an open storefront at tonsofskills.com (2,409 GitHub stars). [CodeGuilds](https://codeguilds.dev), which debuted on [Hacker News](https://news.ycombinator.com/item?id=48357494) on June 1, is another community registry covering skills, agents, and MCP servers.

### 2. Claude Code 2.1.186 and 2.1.187: CLI-First MCP Authentication and Security

Two back-to-back Claude Code releases this week (2.1.186 and 2.1.187) both tightened the MCP story. Per [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2069162080393973775) (482 likes, the top-engagement post this period):

- **2.1.186** added `claude mcp login <name>` and `claude mcp logout <name>` to authenticate MCP servers directly from the CLI without opening the interactive `/mcp` menu, with `--no-browser` stdin redirect support for completing over SSH. The same release added a "Skills" section to the `/plugin Installed` tab, giving skills first-class UI surface inside Claude Code.
- **2.1.187** added `sandbox.credentials` to stop sandboxed commands from reading credential and secret env vars, and changed remote MCP tool calls to abort after 5 minutes instead of hanging indefinitely.

The changelog details are at [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2069162091370467615). The `claude mcp login` command is particularly notable: it means third-party MCP servers can now have authenticated, named identities at the CLI layer rather than relying on ambient credentials.

### 3. The Three-Layer Architecture Is Becoming Consensus

The developer community is converging on a clear mental model of Claude Code's extension surface. [saad.sh](https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained) and [claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/) both articulate it the same way: **Skills** are markdown instruction files that teach Claude how to do a task (30-50 tokens each, loaded on demand, live inside a plugin or skill folder); **MCP servers** connect external tools and data (can consume 50k+ tokens, expose tools/resources/prompts via JSON-RPC); **plugins** are versioned bundles that wrap skills, MCP configs, hooks, subagents, and slash commands into one installable unit.

[@_vmlops](https://x.com/_vmlops/status/2069040280385507494) summarized the Anthropic design choice: "intelligence does not equal expertise - it can reason, write code, call APIs but it doesn't know YOUR processes, YOUR tools, YOUR domain. So Anthropic stopped building a new agent for every use case; they built one general agent + a skill system instead." The [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/) community published a practical guide to all five layers: CLAUDE.md (persistent context), hooks (lifecycle enforcement), skills (invocable instructions), MCP (external tools), and plugins (distribution bundles).

[@dkare1009](https://x.com/dkare1009/status/2069200550684488140) captured the adoption gap neatly (58 likes): "Most teams use 10% of Claude Code. The rest is where the real control sits." 

### 4. Dynamic Workflows: Claude Can Now Write Its Own Harness

The highest-engagement Hacker News story in this window (200 pts, 135 comments) was [Dynamic Workflows in Claude Code](https://news.ycombinator.com/item?id=48311705), tied to Anthropic's official blog post [A harness for every task](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code). The core idea: Claude Code can now write and orchestrate its own multi-agent harness on the fly, custom-built for the task rather than always running in the same default harness. The harness decides how work gets split, which subagents spawn, what tools each gets, how output is verified, which model handles which step, and when the job is done. Per the [official docs](https://code.claude.com/docs/en/workflows), workflows can be checked into `~/.claude/workflows` or distributed via a skill - making dynamic workflows themselves a first-class distributable artifact.

Community tools are following: [CWC (Claude Workflow Composer)](https://github.com/fayzan123/claude-workflow-composer) scans Claude Code history and auto-builds agent workflows (surfaced on [HN](https://news.ycombinator.com/item?id=48602418)). [Swarm](https://github.com/miopea/swarm) is an open-source control center for Claude Code, Gemini, and Codex agents. [Ruflo](https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b) extends Claude Code with 100+ cooperative agents, self-learning memory, and zero-trust federation.

### 5. Security Is the Ecosystem's Unacknowledged Problem

The ecosystem is shipping MCP servers faster than anyone is auditing them, and the community is starting to notice. [@dane_works](https://x.com/dane_works/status/2069317409912307978) put it plainly: "I keep connecting to random MCP servers and never check if they're safe." Cisco shipped an MCP scanner this week using YARA rules, an LLM-as-judge, and their own defense API - and it integrates as a Claude Code plugin so you can audit tools directly from your agent session.

The supply-chain risk is real: [@cytexsmb](https://x.com/cytexsmb/status/2064347184384905728) reported the Shai-Hulud supply chain campaign added 23 new malicious PyPI packages specifically targeting bioinformatics and MCP developers, bringing the campaign total to 471 artifacts across npm and PyPI. On the auth side, a [GitHub bug report](https://github.com/anthropics/claude-code/issues/62556) documented all claude.ai-hosted MCP connectors (Gmail, Google Drive, Google Calendar) failing in Cowork on macOS because the desktop OAuth token lacked the `user:mcp_servers` scope.

The discovery problem compounds the security problem. [alatirok.com](https://alatirok.com/mcp-server-discovery/) documents that two competing SEPs for MCP server discovery via `.well-known` endpoints exist but neither has been merged into the core spec. [sunpeak.ai](https://sunpeak.ai/blogs/mcp-app-discovery-server-cards/) covers the MCP App Discovery design: server cards, manifests, and `.well-known` metadata.

### 6. MCP is Now Infrastructure-Scale: 9,208 Servers, Linux Foundation Standard

The MCP ecosystem is no longer experimental. [The Agent Almanac](https://agentalmanac.org/mcp) live health tracker shows 9,208 total MCP servers registered at registry.modelcontextprotocol.io, 9,178 active, with 97M+ monthly SDK installs. [@ai_zona](https://x.com/ai_zona/status/2064814953035702637) announced "MCP is now a Linux Foundation standard" - confirmed by the [MCP 2026 roadmap](https://a2a-mcp.org/blog/mcp-2026-roadmap) which shows Anthropic donating the protocol to the new Agentic AI Foundation. The protocol is now implemented by Anthropic, OpenAI Agents SDK, Cursor, Cloudflare Agents, and Microsoft. Streamable HTTP replaced the older HTTP+SSE transport in the current spec.

[@Lemmebuyit_](https://x.com/Lemmebuyit_/status/2064751043305775431) announced their shopping MCP is now live across "every major Model Context Protocol registry" (Anthropic's official MCP Registry, Smithery, Glama) with 262M+ products across 86+ US retailers. [@KrackedDevs](https://x.com/KrackedDevs/status/2067531171584491649) covered Unreal Engine's experimental MCP server embedded directly inside the Unreal Editor, letting Claude Code and Cursor drive 3D worlds over local HTTP.

The HN community is building MCP tooling: [Bad MCP design costs your agent 5x more tokens](https://news.ycombinator.com/item?id=48407391) (17 pts) - design pattern critique; [Ctx](https://github.com/stevesolun/ctx) - save tokens by loading only relevant tools; [Spanly](https://spanly.com/) - see what AI agents do inside your MCP server; [Lumen](https://github.com/GonzaloMonzonC/lumen-protocol/) - binary alternative to JSON-RPC for MCP.

### 7. Autonomous Skill Discovery and the bhived MCP Pattern

The most interesting emerging pattern in [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/) this period is **autonomous skill discovery** via the `bhived` MCP: agents that repeatedly start from scratch because they have no shared memory get a shared memory layer via bhived, then use that memory for autonomous skill discovery - discovering and reusing skills across sessions without re-learning from scratch. A companion workflow, [archex MCP](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/), addresses token efficiency by loading only relevant context for each retrieval.

[@KrackedDevs](https://x.com/KrackedDevs/status/2069710247229276481) reported that Hermes Agent shipped a new skills system with a `/learn` command that points the agent at real workflows, docs, or directories to auto-generate SKILL.md files that follow house standards - no manual authoring. Skills load progressively so the agent only pulls full content when needed.

### 8. Community Skepticism: "Most Stuff Beyond Skills/Hooks Is Useless"

Not everyone is bullish on the complexity. [@neue_w](https://x.com/neue_w/status/2069410981227515925) offered the contrarian read this week: "self improvement loops sounds like total bullshit. orchestrating agents is wasteful if the sub agent is just another opus clone. maybe it could make sense through MCP servers. but i heard even that is too brittle. most of the stuff beyond the claude code/skills/hooks is useless."

On Bluesky, [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes, the top Bluesky post) articulated what power users actually want: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." And from the same account: "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

The [Ask HN: Has anyone replaced Claude/GPT with a local model for daily coding?](https://news.ycombinator.com/item?id=48542100) thread (1,311 pts, 562 comments - highest engagement in the window) reflects the ongoing tension: the ecosystem is deep but the cost and complexity drive some developers toward simpler alternatives.

---

## Cross-Source Patterns

**Pattern 1: "One install command" as the new UX bar** - The most-shared X posts all led with how simple a tool is to install. @chenzeling4's 30K-star post, @CripdoeCrypto's zambo.io post ("add this to your claude config: {...} that's it. you now have 28 tools"), and @HeyShruti7's "Resource Bible" thread all frame tool discovery as a friction problem being solved. Appeared on X, Reddit, Web.

**Pattern 2: Security debt accumulating faster than tooling** - The Cisco scanner launch, the Shai-Hulud PyPI campaign, and the MCP OAuth bug all landed in the same week. The community is aware it is installing unaudited code from strangers. Appeared on X, GitHub.

**Pattern 3: Skills as the "light" extension layer, MCP as the "heavy" one** - Every guide published this month uses the same frame: skills for procedural knowledge (load cheap, markdown-based), MCP for external state (load expensive, JSON-RPC). Appeared on Reddit, Web, X, Bluesky.

**Pattern 4: Workflow distribution via skills** - Anthropic's dynamic workflows post, the codeguilds.dev registry, and the r/ClaudeWorkflows posts all point toward workflows-as-skills as the distribution primitive. Appeared on HN, Reddit, Web, X.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP | — | — | "Agents repeatedly start from scratch, relearning tasks... bhived solves this with shared memory + skill discovery" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/ |
| r/ClaudeWorkflows | Improve Claude Code Agent Token Efficiency with `archex` MCP Server | — | — | "Inefficient token-hungry code context retrieval fixed by loading only relevant context" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/ |
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory (bhived MCP) for Skill and Knowledge Discovery | — | — | "Confidence: 0.90 · Level: intermediate · Categories: Skills, MCP, Multi-Agent" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2j9/ |
| r/ClaudeWorkflows | Practical Guide to Claude Code Components: CLAUDE.md, Skills, Hooks, Plugins, and AGENTS.md Hierarchy | — | — | "Confusion regarding the different extension points and when to use each one" | https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @ClaudeCodeLog | Claude Code 2.1.186 has been released — added claude mcp login/logout from CLI | 482 | 28 | https://x.com/ClaudeCodeLog/status/2069162080393973775 |
| @ClaudeCodeLog | Claude Code 2.1.187 — sandbox.credentials, remote MCP calls abort after 5min | 295 | 12 | https://x.com/ClaudeCodeLog/status/2069531604951687542 |
| @HeyShruti7 | Claude Code Resource Bible: 54 tools, agents, MCP servers, skills | 63 | 22 | https://x.com/HeyShruti7/status/2069066617301196875 |
| @spandan_madan | The Tool Architecture of Claude Code | 427 | 110 | https://x.com/spandan_madan/status/2067320100911493454 |
| @dkare1009 | Most teams use 10% of Claude Code — 5 layers explained | 58 | 13 | https://x.com/dkare1009/status/2069200550684488140 |
| @Krishnasagrawal | 4-step power user setup: CLAUDE.md, slash commands, subagents, skills | 49 | 5 | https://x.com/Krishnasagrawal/status/2068946696185471351 |
| @chenzeling4 | 30,759 stars and it's literally just a list (claude-plugins-official) | 1 | — | https://x.com/chenzeling4/status/2069494704589418744 |
| @dane_works | Cisco shipped MCP scanner: YARA rules, LLM as judge | 3 | — | https://x.com/dane_works/status/2069317409912307978 |
| @neue_w | "most of the stuff beyond claude code/skills/hooks is useless" | — | — | https://x.com/neue_w/status/2069410981227515925 |
| @CripdoeCrypto | One JSON line = 28 tools via zambo.io MCP | 6 | 2 | https://x.com/CripdoeCrypto/status/2068809787706626251 |
| @99_Bollish | Zambo listed on Anthropic's official MCP Registry, Smithery, Glama | — | — | https://x.com/99_Bollish/status/2067036607652544652 |
| @KrackedDevs | Unreal Engine embeds MCP server directly in editor for AI agent control | 2 | 1 | https://x.com/KrackedDevs/status/2067531171584491649 |
| @ai_zona | MCP is now a Linux Foundation standard | 2 | 1 | https://x.com/ai_zona/status/2064814953035702637 |
| @cytexsmb | Shai-Hulud campaign: 23 new malicious PyPI packages targeting MCP devs | 3 | 1 | https://x.com/cytexsmb/status/2064347184384905728 |
| @KrackedDevs | Hermes skills system: /learn auto-generates SKILL.md files | 2 | — | https://x.com/KrackedDevs/status/2069710247229276481 |
| @_vmlops | Anthropic built one general agent + skill system instead of per-use-case agents | 25 | 2 | https://x.com/_vmlops/status/2069040280385507494 |
| @Lemmebuyit_ | LemmeBuyIt MCP live on every major MCP registry (262M+ products) | 21 | 2 | https://x.com/Lemmebuyit_/status/2064751043305775431 |
| @AnthropicAI | Project Fetch: Opus 4.7 was 20x faster than human team with Opus 4.1 | 2,221 | 188 | https://x.com/AnthropicAI/status/2067651699486200091 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| cloudking | Ask HN: Has anyone replaced Claude/GPT with a local model for daily coding? | 1311 | 562 | Highest engagement story in window | https://news.ycombinator.com/item?id=48542100 |
| ankitg12 | Claude Code – Everything you can configure that the docs don't tell you | 326 | 65 | Source-code-level config audit | https://buildingbetter.tech/p/i-read-the-claude-code-source-code |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | Official Anthropic launch post | https://news.ycombinator.com/item?id=48311705 |
| nab | Show HN: Boxes.dev: ditch localhost; run Claude Code and Codex in the cloud | 105 | 79 | Cloud-hosted agent execution | https://boxes.dev |
| JohnnyZhang483 | Bad MCP design costs your agent 5x more tokens | 17 | 1 | MCP design patterns critique | https://news.ycombinator.com/item?id=48407391 |
| mpgirro | Nudge – a collaborative memory layer for Claude Code and Codex CLI hooks | 2 | — | Memory layer for hooks | https://github.com/attunehq/nudge |
| stevesolun | Show HN: Ctx, save tokens by loading only the relevant tools | 8 | 2 | Token-efficient tool loading | https://github.com/stevesolun/ctx |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | Community registry launch | https://codeguilds.dev |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | Agent loop architecture deep dive | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| manelrv | CCTV – See which Claude Code agent needs you, from the menu bar | 2 | — | Multi-agent monitoring | https://github.com/manelrv/CCTV |
| timq | Show HN: Spanly - See what AI agents do inside your MCP server | 1 | 2 | MCP observability | https://spanly.com/ |
| GonzaloMonzonC | Lumen – A Binary Alternative to JSON-RPC for MCP | 4 | — | Protocol efficiency | https://github.com/GonzaloMonzonC/lumen-protocol/ |
| FayzanMalik | Show HN: CWC scans your Claude Code history and auto-builds agent workflows | 2 | 1 | Workflow auto-generation | https://github.com/fayzan123/claude-workflow-composer |
| barakolshe | Claude Code Issue management extension for VS Code | 3 | 1 | VS Code integration | https://www.forq.ink/ |
| miopea | Swarm – open-source control center for Claude Code / Gemini / Codex agents | 4 | — | Multi-agent orchestration | https://github.com/miopea/swarm |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list..." | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @coolhand.bsky.social | "I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @webuyhousesusa.bsky.social | ECC drops 63 specialized agents and 240+ ready-made skills — free MIT-licensed, replaces paid plugins | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @brunopedro.com | 42Crunch + Claude Code: autonomous Agentic DevSecOps model for enterprise | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @github-trending-js.bsky.social | Ruflo: multi-agent framework with 100+ cooperative agents, self-learning memory, zero-trust federation | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |

**GitHub:**
| Repo | PR/Issue | Reactions | Comments | Notable | URL |
|------|----------|-----------|----------|---------|-----|
| hashgraph-online/hol-guard | feat(guard): add z.ai ZCode harness adapter | 3 | 2 | Claude-Code-shaped layout for ZCode: mcp.servers, plugins.enabledPlugins, hooks | https://github.com/hashgraph-online/hol-guard/pull/924 |
| binbashar/le-tf-infra-aws | feat(claude): adopt shared bb-ai-marketplace IaC plugins | — | 5 | Registers extraKnownMarketplaces in .claude/settings.json | https://github.com/binbashar/le-tf-infra-aws/pull/1087 |
| manaflow-ai/cmux | Add built-in OpenCode sidebar status integration | — | 4 | OpenCode hooks auto-installed via cmux session plugin | https://github.com/manaflow-ai/cmux/pull/4797 |
| manaflow-ai/cmux | Add native Kiro CLI hook integration | — | 5 | Bridges Kiro lifecycle events into cmux status and approval cards | https://github.com/manaflow-ai/cmux/pull/4831 |
| anthropics/claude-code | [BUG] Cowork macOS: all claude.ai-hosted MCP connectors fail | 2 | 11 | OAuth token missing user:mcp_servers scope | https://github.com/anthropics/claude-code/issues/62556 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| agentalmanac.org | https://agentalmanac.org/mcp | Live MCP Registry health tracker: 9,208 total servers, 9,178 active, 97M+ monthly SDK installs |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Open SKILL.md registry; best explanation of the three-layer model |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills teach Claude HOW; MCP gives Claude ACCESS; plugins BUNDLE and DISTRIBUTE |
| github.com | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; open-source marketplace tonsofskills.com |
| dev.to | https://dev.to/nagell/build-your-own-claude-code-marketplace-scaffold-structure-and-auto-updates-4n3f | Scaffold your own Claude Code marketplace from zero; auto-versioning CI pre-wired |
| skills.2389.ai | https://skills.2389.ai/ | 2389 Research marketplace: 14+ development plugins (CSS, Firebase, etc.) |
| deepwiki.com | https://deepwiki.com/anthropics/skills/2.3-marketplace-and-plugin-system | Anthropics/skills marketplace internals: marketplace.json, strict resolution mode |
| sunpeak.ai | https://sunpeak.ai/blogs/mcp-app-discovery-server-cards/ | MCP App Discovery: server cards, manifests, .well-known metadata design |
| jsmanifest.com | https://jsmanifest.com/claude-code-plugin-packaging-guide | Plugin packaging guide: treat plugins as bundles not isolated skills |
| claude.com | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Official: Claude Code can write and orchestrate its own multi-agent harness |
| computingforgeeks.com | https://computingforgeeks.com/claude-code-hooks-guide/ | Complete Claude Code hooks guide with production patterns |
| saad.sh | https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained | Best single-source explanation of all extension surfaces and their differences |
| alatirok.com | https://alatirok.com/mcp-server-discovery/ | Two competing SEPs for .well-known MCP discovery; neither merged yet |
| infoq.com | https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/ | News coverage of dynamic workflows launch |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Largest community-curated directory; 21,600+ skills indexed daily from GitHub |
| modelcontextprotocol.io | https://modelcontextprotocol.io/community/working-groups/skills-over-mcp | Skills Over MCP Working Group - 2026 roadmap priority for skill discovery via MCP |
| a2a-mcp.org | https://a2a-mcp.org/blog/mcp-2026-roadmap | MCP 2026 roadmap: Skills primitive, registry, Agentic AI Foundation stewardship |
| webdeveloper.com | https://webdeveloper.com/learn/guides/building-mcp-servers/ | When to choose MCP vs tool calls vs CLI; multi-client use case is the key signal |

---

## Stats Block

```
├─ 🟠 Reddit: 4 threads
├─ 🔵 X: 31 posts │ 4,449 likes │ 476 reposts
├─ 🟡 HN: 38 stories │ 2,064 points │ 864 comments
├─ 🦋 Bluesky: 11 posts │ 83 likes │ 6 reposts
├─ 🐙 GitHub: 14 items │ 234 reactions │ 101 comments
├─ 🌐 Web: 18 pages + 14 WebSearch supplements
└─ 🗣️ Top voices: @ClaudeCodeLog, @spandan_madan, @HeyShruti7 │ r/ClaudeWorkflows
```

---

## Data Gaps

- **Reddit**: Public API returned 403 on all direct searches; only r/ClaudeWorkflows posts surfaced via RSS. r/ClaudeAI, r/LocalLLaMA, r/ChatGPTCoding had zero items this run. Reddit coverage is ~10% of expected signal.
- **YouTube**: Zero videos returned across all four subquery passes, including ScrapeCreators fallback (402 Payment Required). This is a real gap - YouTube likely has tutorials and walkthrough content on this topic.
- **TikTok / Instagram**: ScrapeCreators returned 402 on all hashtag and search attempts. No short-form video coverage.
- **Bluesky**: 11 posts found but searches returned 0 on MCP/skill-specific queries; only the broader Claude Code query produced results.
- **GitHub**: No GitHub token configured; using unauthenticated REST tier with low rate limits. modelcontextprotocol/servers and anthropics/claude-ai-mcp repos not directly searched.
- **Coverage estimate**: ~65% - strong on X and HN, weak on Reddit, absent on video platforms.

---

## Key Quotes

> "30,759 stars and it's literally just a list." - [@chenzeling4](https://x.com/chenzeling4/status/2069494704589418744) on X, describing claude-plugins-official

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "self improvement loops sounds like total bullshit. orchestrating agents is wasteful if the sub agent is just another opus clone. maybe it could make sense through MCP servers. but i heard even that is too brittle. most of the stuff beyond the claude code/skills/hooks is useless" - [@neue_w](https://x.com/neue_w/status/2069410981227515925) on X

> "I keep connecting to random MCP servers and never check if they're safe. Cisco just shipped a scanner that does exactly this: YARA rules, LLM as judge, and their own defense api all running against your connected servers. The mcp ecosystem is shipping servers way faster than anyone is auditing them." - [@dane_works](https://x.com/dane_works/status/2069317409912307978) on X

> "intelligence does not equal expertise — it can reason, write code, call APIs but it doesn't know YOUR processes, YOUR tools, YOUR domain. So Anthropic stopped building a new agent for every use case; they built one general agent + a skill system instead." - [@_vmlops](https://x.com/_vmlops/status/2069040280385507494) on X

> "Most teams use 10% of Claude Code. The rest is where the real control sits." - [@dkare1009](https://x.com/dkare1009/status/2069200550684488140) on X

> "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "add this to your claude config: {"mcpServers":{"zambo":{"url":"..."}}} — that's it. you now have 28 tools. most MCP servers have like 3 tools and take 20 minutes to set up. this one has 28, it's free to start." - [@CripdoeCrypto](https://x.com/CripdoeCrypto/status/2068809787706626251) on X
