# Agent Skills & MCP Ecosystem — Daily Briefing
**Date:** 2026-06-09
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 11 threads | — | r/ClaudeCode, r/LovingOpenSourceAI, r/AiBuilders |
| X/Twitter | 13 posts | 289 likes, 41 reposts | @Bell_QuoLu, @hasantoxr, @Suryanshti777 top voices |
| Hacker News | 18 stories | 1,783 points, 1,099 comments | "Daily Driver" post dominated (451 pts) |
| Bluesky | 13 posts | 72 likes, 6 reposts | @carnage4life most engaged (32 likes) |
| Web | 16 pages | — | 9 engine + 7 WebSearch supplements |

---

## Synthesized Findings

### 1. The Five-Layer Claude Code Harness - Most Developers Are Only Using Layer One

The Claude Code extension stack has a clear architecture that most users never reach. As [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) put it on Bluesky: "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (the counter-intuitive insight: upgrading from Sonnet to Opus gives less value than activating all 5 layers on Sonnet). This is the same signal driving [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/)'s most-upvoted confusion thread - "Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md?" ([direct thread](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/)) - and the [X thread from @Suryanshti777](https://x.com/Suryanshti777/status/2064213381557678493) framing it starkly: "The average developer uses Claude Code like ChatGPT. The top 1% use it like an engineering team." The community-curated guide at [mcp.directory](https://mcp.directory/blog/claude-code-skills-vs-subagents-vs-plugins-vs-hooks-2026) and [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) are the canonical go-tos for understanding the distinction: skills are markdown files in `.claude/skills/` that become slash commands; plugins bundle multiple skills + MCP servers + commands into versioned, distributable packages.

The playbook gap is now a product category. [@hasantoxr](https://x.com/hasantoxr/status/2064095401888940091) surfaced a visual guide called "Claude How To" covering slash commands, memory, hooks, MCP servers, subagents, skills, plugins, and advanced workflows with Mermaid diagrams and copy-paste templates - drawing 113 likes in 24 hours. The [HN "Daily Driver" post](https://arps18.github.io/posts/claude-code-mastery/) (451 pts, 254 cmts) on the same theme remains the highest-engagement technical post of the month.

**Sources:** X, Reddit, Bluesky, HN, Web

---

### 2. v2.1.169 Ships --safe-mode - The Plugin Debugging Feature Everyone Needed

The most talked-about release this week is Claude Code v2.1.169, published June 8. The headline feature is `--safe-mode` / `CLAUDE_CODE_SAFE_MODE`, which disables all customizations at startup - CLAUDE.md, plugins, skills, hooks, MCP servers, custom commands, output styles, workflows, custom themes, and keybindings - for clean-slate troubleshooting. [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2064108732393324569) documented the full changelog (16 likes). [@Bell_QuoLu](https://x.com/Bell_QuoLu/status/2064256386188636652) framed the use case: "it's easier to separate 'is this the model's behavior?' from 'is this coming from the environment config?'" The flag is getting immediate real-world traction: [@TambaClan](https://x.com/TambaClan/status/2064225258971045930) publicly requested a `--safe-mode` demonstration at the "Code with Claude Tokyo" event (June 10), arguing that behavioral bugs reproduced in clean state can't be attributed to user-side customization layers.

The release also adds `disableBundledSkills` / `CLAUDE_CODE_DISABLE_BUNDLED_SKILLS` to hide built-in skills and slash commands from the model entirely - a signal that the bundled skill footprint has grown large enough to warrant its own kill switch. Full release notes at the [official changelog](https://code.claude.com/docs/en/changelog) and [claude-code/CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md). Note: `~/.claude/settings.json` flags are NOT disabled by `--safe-mode` per [@masaakiotadev](https://x.com/masaakiotadev/status/2064189250820788280).

**Sources:** X, Web

---

### 3. The Marketplace Ecosystem Has Stratified Into Three Tiers

Three distribution layers have crystallized for Claude Code extensions:

**Tier 1 - Official Anthropic Marketplace** ([github.com/anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)): 101 plugins as of March 2026, 33 built by Anthropic. Auto-available at startup. The community layer ([claude-plugins-community](https://claudemarketplaces.com/)) hosts third-party plugins that have cleared Anthropic's automated validation and safety screening. Fresh entrant: the [Appwrite plugin](https://x.com/appwrite/status/2064273389158903850), which landed this week with built-in agent skills and MCP servers for the Appwrite API.

**Tier 2 - Community Aggregators**: [tonsofskills.com](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) (425 plugins, 2,810 skills, 200 agents, installable via the `ccpi` CLI); [CodeGuilds](https://codeguilds.dev) (community registry for skills, agents, MCP servers - launched on HN June 1); [claudemarketplaces.com](https://claudemarketplaces.com/) (daily-updated directory). The canonical reference list is [hesreallyhim/awesome-claude-code](https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/) at ~36.8k stars.

**Tier 3 - Cross-Agent Skill Format**: The [Agent Skills format](https://explainx.ai/blog/what-are-agent-skills-complete-guide) (separate from Claude Code's native skill format) works across 40+ agents - Claude Code, Cursor, Codex, Windsurf, Copilot, and others. GreenSock published [official GSAP skills](https://www.reddit.com/r/LovingOpenSourceAI/comments/1tr29t6/official_ai_skills_for_gsap_greensock_animation/) in this format; Microsoft published a [skills repo](https://github.com/microsoft/skills) for SDKs to ground coding agents; [academic-research-skills](https://github.com/Imbad0202/academic-research-skills) hit 82 HN points.

**Sources:** X, Reddit, HN, Web

---

### 4. MCP Registry Ecosystem: From Chaos to Governed Infrastructure

The MCP server landscape has industrialized. Per [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries), four registries dominate discovery: [mcp.so](https://mcp.so) (20,222 servers listed), [smithery.ai](https://smithery.ai) (~7,000 servers, positioned as "Docker Hub for MCP"), [glama.ai/mcp](https://glama.ai/mcp), and [punkpeye/awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers). The 2026 roadmap includes MCP Server Cards - a proposed standard for `.well-known` URL discovery so browsers, crawlers, and registries can surface capabilities without connecting.

Enterprise governance is the new growth surface. [Boomi MCP](https://boomi.com/platform/mcp/) offers a single platform to expose, govern, and activate every MCP tool agents need. [Kong MCP Registry](https://konghq.com/products/mcp-registry) centralizes AI tools with OAuth authentication and dynamic tool discovery. [AWS Agent Registry](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) is now in preview as a private governed catalog for agents, tools, skills, and MCP servers. [Azure SRE Agent](https://sre.azure.com/docs/capabilities/plugin-marketplace) ships a plugin marketplace with SHA-256 content hashing for upstream skill change detection.

Show HN projects are filling the runtime gaps: [Aquifer](https://github.com/rjpruitt16/aquifer) handles spiky agent tool traffic; [Sub-Agent MCP](https://github.com/stormaref/Sub-Agent-MCP) adds LLM delegation via MCP; [ai-capability-registry](https://github.com/Friz-zy/ai-capability-registry) takes a GitOps-style approach; [zavora-ai/mcp-registry](https://github.com/zavora-ai/mcp-registry) offers central control plane with allow-lists and audit in Rust.

**Sources:** HN, Web

---

### 5. Skill Distribution Tooling: The Multi-Agent Sync Problem Goes Mainstream

The friction of managing skills and MCP server configs across multiple agents and machines has spawned dedicated tooling. Two community projects launched within days of each other on [r/AiBuilders](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/) and [r/coolgithubprojects](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/): `gaal`, a Go CLI where one `gaal.yaml` declares your MCP server and skill setup, and `gaal sync` writes the correct config for Claude Code, Cursor, and Codex on every machine. The described pain is universal: "every time we added an MCP server or wrote a skill, we had to copy it into each agent's config, in each agent's format, on each machine. They drifted constantly."

[Stacklok ToolHive](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) goes further with full lifecycle management for agent skills - discovery through distribution via ToolHive Registry Server, OCI registries, or Git repositories. [SkillForge](https://github.com/munnmajithia/skillforge) bills itself as an open-source MCP skill pack ecosystem for AI coding agents.

**Sources:** Reddit, Web

---

### 6. Token Hygiene Crisis: MCP Servers Are Eating Your Context Budget

Boris Cherny (Claude Code's creator) gave a talk covering 125 Claude settings, and the token waste data from idle plugins is striking. Per [@Dubibubiii](https://x.com/Dubibubiii/status/2064059729639244122): "Idle plugins and MCP servers chewing through 25K to 40K tokens per session. Most people are paying $100/month and using maybe 30% of Claude's actual capability." [@danielderedev](https://x.com/danielderedev/status/2064035813516578864) traced a session: "40% of the context was tool definitions I never used. 20% was git history the agent re-read every turn. 15% was MCP server docs for servers I hadn't touched in two weeks." The HN piece ["Bad MCP design costs your agent 5x more tokens"](https://news.ycombinator.com/item?id=48407391) (15 pts) reinforces this. The `disableBundledSkills` flag in v2.1.169 is a direct response.

One practitioner framing from [@mhalle.bsky.social](https://bsky.app/profile/mhalle.bsky.social/post/3mnlcs2o33s26): "The equivalent inside of Claude Code (to avoid charged API usage) is to ask to write a skill that a sub-agent can use. The skill is code, docs, and data." This pattern - skills as cost-bounded sub-agent wrappers - is gaining traction as a counter to runaway MCP context bloat.

**Sources:** X, Bluesky, HN

---

### 7. Dynamic Workflows and the Sub-Agent Orchestration Layer

Anthropic's [Dynamic Workflows announcement](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) (200 pts, 135 cmts on HN, May 28) marks a shift from static skill execution to runtime-adaptive agent behavior. The [Bluesky post from @carnage4life](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) connects this to Microsoft's concurrent launch of an OpenClaw-style agent in Teams: "I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers." The emergent pattern from [r/mcp](https://www.reddit.com/r/mcp/comments/1tacsse/can_mcp_servers_bundle_agent_skills_so_any_mcp/) thread: bundling agent skills inside MCP servers so any MCP host loads both the skill instructions and the server tools simultaneously.

Sub-agent orchestration is getting its own infrastructure: [Sub-Agent MCP](https://github.com/stormaref/Sub-Agent-MCP) adds LLM delegation via MCP protocol; a developer [gave an AI video generator 86 MCP tools](https://github.com/openclaw-easy/ViralMint) so Claude Code can drive it autonomously. The cadaeic.space Bluesky observation captures the cultural moment: ["for an LLM, the tool surface is their umwelt"](https://bsky.app/profile/cadaeic.space/post/3mneiendmu224) - MCP servers are becoming cognitive environment, not just API connectors.

**Sources:** HN, X, Bluesky, Reddit

---

### 8. Vertical Skill Packs: Libraries and Frameworks Publishing Their Own AI Skills

A new distribution pattern: library maintainers shipping official AI skills as part of their documentation. GreenSock published [official GSAP skills](https://github.com/greensock/gsap-skills) teaching agents correct GSAP API usage across React/Vue/Svelte and vanilla JS. [Academic Research Skills for Claude Code](https://github.com/Imbad0202/academic-research-skills) (82 pts on HN) provides a skill set for academic workflows. [ktx](https://www.reddit.com/r/LovingOpenSourceAI/comments/1trwna2/ktx_ktx_is_an_executable_context_layer_for_data/) ships an MCP context layer with embedded skills for data analytics agents querying warehouses. A developer built an app compliance auditor as both a Claude skill (`ipaship-audit`) and an MCP connector for iOS/Android submission safety hooks.

The [WorkOS explainer](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) frames this as the distinction between MCP servers (raw tools) and agent skills (the knowledge layer of when/why/how to use those tools). Skills sit above MCP in the comprehension stack.

**Sources:** Reddit, HN, Web

---

## Cross-Source Patterns

### Pattern 1: Most Users Are Stuck at Layer 1 (Prompting)

Appears on X, HN, Reddit, Bluesky. The consistent signal: the majority of Claude Code users interact only via prompts, never activating skills, hooks, plugins, or MCP servers. The French Bluesky quote (upgrading to Opus < activating 5 layers) and the @Suryanshti777 "top 1%" framing are the same observation from different angles. The "Daily Driver" HN post (451 pts) and the confusion-taxonomy Reddit thread are response artifacts of the same gap.

- X: [@Suryanshti777](https://x.com/Suryanshti777/status/2064213381557678493), [@hasantoxr](https://x.com/hasantoxr/status/2064095401888940091)
- HN: [arps18.github.io/posts/claude-code-mastery/](https://arps18.github.io/posts/claude-code-mastery/)
- Reddit: [r/ClaudeCode confusion thread](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/)
- Bluesky: [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o)

---

### Pattern 2: Token/Context Hygiene Is the New "Best Practice" Conversation

Appears on X, HN, Bluesky. The conversation has shifted from "how do I add more MCP servers" to "how do I stop my MCP servers from degrading performance." Boris Cherny's 125 settings talk, the traced-session post (40% waste), and the "Bad MCP design" HN piece are three independently-sourced versions of the same finding: idle MCP tooling is a context tax, not just a config overhead.

- X: [@Dubibubiii](https://x.com/Dubibubiii/status/2064059729639244122), [@danielderedev](https://x.com/danielderedev/status/2064035813516578864)
- HN: [Bad MCP design (48407391)](https://news.ycombinator.com/item?id=48407391)
- Bluesky: [@mhalle.bsky.social](https://bsky.app/profile/mhalle.bsky.social/post/3mnlcs2o33s26)

---

### Pattern 3: Cross-Agent Skill Portability Is a Real Demand

Appears on Reddit, HN, Web, X. Two independent sync tools (gaal, ToolHive) launched the same week. GSAP, Microsoft, and academic-research-skills all published agent skills in a format targeting 40+ tools. The r/mcp question about MCP servers bundling skills is essentially the same portability concern in architectural form.

- Reddit: [gaal r/coolgithubprojects](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/), [r/AiBuilders sync tool](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/)
- HN: [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills), [Deliberate Skill Development](https://github.com/DrCatHicks/learning-opportunities)
- Web: [Stacklok ToolHive](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates)
- X: [GSAP skills (via r/LovingOpenSourceAI)](https://www.reddit.com/r/LovingOpenSourceAI/comments/1tr29t6/official_ai_skills_for_gsap_greensock_animation/)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md? | — | — | "Everyone says 'just create a skill for that' but the explanations are always vague" | https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/ |
| r/coolgithubprojects | Built a free, open-source Go CLI to stop hand-copying MCP servers and skills between every coding agent | — | — | "every time we added an MCP server or wrote a skill, we had to copy it into each agent's config... They drifted constantly" | https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/ |
| r/AiBuilders | We built a tool to keep our coding agents' skills and MCP servers in sync across machines | — | — | "the tax of copying it onto three machines, into Claude Code, then Cursor, then Codex" | https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/ |
| r/ClaudeWorkflows | SR PM's Claude Code Toolkit: Automating PRDs, Interviews, and Todo Lists with Skills, Agents, and MCP | — | — | "Workflow value: 85/100" | https://www.reddit.com/r/ClaudeWorkflows/comments/1tsirqf/workflow_sr_pms_claude_code_toolkit_automating/ |
| r/LovingOpenSourceAI | Official AI skills for GSAP — works with 40+ agents | — | — | "Agent Skills format; works with skills CLI (Cursor, Claude Code, Codex, Windsurf, Copilot, 40+ agents)" | https://www.reddit.com/r/LovingOpenSourceAI/comments/1tr29t6/official_ai_skills_for_gsap_greensock_animation/ |
| r/LovingOpenSourceAI | ktx — executable context layer for data agents via MCP with skills and semantic layer | — | — | "Allow Claude Code, Codex, and any AI agent to query data accurately through MCP with skills, memory" | https://www.reddit.com/r/LovingOpenSourceAI/comments/1trwna2/ktx_ktx_is_an_executable_context_layer_for_data/ |
| r/mcp | Can MCP servers bundle Agent Skills? | — | — | "Instead of exposing many MCP tools directly, the server exposes only one generic tool: execute_tool()" | https://www.reddit.com/r/mcp/comments/1tacsse/can_mcp_servers_bundle_agent_skills_so_any_mcp/ |
| r/opencode | Security hooks in MCP or Claude skill for app compliance | — | — | "I built an app compliance auditor as a Claude skill and a MCP connector" | https://www.reddit.com/r/opencode/comments/1tlft0z/is_it_useful_if_you_can_get_secure_code/ |
| r/ClaudeCode | Vibe-coding quick-start + awesome-claude-code (~36.8k stars) | — | — | "hesreallyhim/awesome-claude-code — The hand-curated, canonical big list of skills, hooks, slash commands" | https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/ |
| r/ClaudeCode | Built a Cowork plugin for WordPress editing — 5 months learnings | — | — | "The Cowork plugin format is genuinely a different abstraction from raw MCP" | https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/ |
| r/Ytqaz2019 | Can someone explain the real difference between Hooks, Skills, Plugins? (cross-post) | — | — | — | https://www.reddit.com/r/Ytqaz2019/comments/1tnslcx/can_someone_explain_the_real_difference_between/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @hasantoxr | "I found the Claude Code playbook... Slash commands - Memory - Hooks - MCP servers - Subagents - Skills - Plugins" | 113 | 19 | https://x.com/hasantoxr/status/2064095401888940091 |
| @cyrilXBT | "One GitHub repo. 50 MCP servers. Every superpower your agent needs... Works with Claude Code, Gemini, Codex, and Cursor" | 95 | 13 | https://x.com/cyrilXBT/status/2063946654206877823 |
| @usr_bin_roygbiv | "I have had several 2 hour long meetings I didn't go to regarding training on skills and mcp servers in claude code" | 23 | 0 | https://x.com/usr_bin_roygbiv/status/2064139974103212247 |
| @Suryanshti777 | "The average developer uses Claude Code like ChatGPT. The top 1% use it like an engineering team." | 17 | 3 | https://x.com/Suryanshti777/status/2064213381557678493 |
| @ClaudeCodeLog | "Claude Code CLI 2.1.169 changelog: Added --safe-mode flag... Added disableBundledSkills setting" | 16 | 0 | https://x.com/ClaudeCodeLog/status/2064108732393324569 |
| @Dubibubiii | "Idle plugins and MCP servers chewing through 25K to 40K tokens per session" | 1 | 0 | https://x.com/Dubibubiii/status/2064059729639244122 |
| @danielderedev | "40% of the context was tool definitions I never used. 15% was MCP server docs for servers I hadn't touched in two weeks" | 6 | 0 | https://x.com/danielderedev/status/2064035813516578864 |
| @Bell_QuoLu | "--safe-mode can disable CLAUDE.md, plugins, skills, hooks, and MCP servers all together at startup" | 0 | 0 | https://x.com/Bell_QuoLu/status/2064256386188636652 |
| @TambaClan | "I have publicly requested a Claude Code --safe-mode demonstration [at Code with Claude Tokyo]" | 0 | 0 | https://x.com/TambaClan/status/2064225258971045930 |
| @appwrite | "The Appwrite plugin is now available in the official Claude marketplace... built-in agent skills and MCP servers" | 6 | 0 | https://x.com/appwrite/status/2064273389158903850 |
| @Bell_QuoLu | "Claude Code v2.1.169 Japanese commentary on --safe-mode and /cd command" | 0 | 0 | https://x.com/Bell_QuoLu/status/2064182024580247700 |
| @masaakiotadev | "Claude Codeに追加された--safe-mode / ~/.claude/settings.jsonのフラグは無効化されないので注意" | 1 | 0 | https://x.com/masaakiotadev/status/2064189250820788280 |
| @flareforward | "MCP Payment Rail — AI agents doing real work need a safe way to pay each other. No standard exists yet. We're building it." | 11 | 6 | https://x.com/flareforward/status/2059276620435710084 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad |
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | https://github.com/DrCatHicks/learning-opportunities |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| arnon | Academic Research Skills for Claude Code | 82 | 25 | — | https://github.com/Imbad0202/academic-research-skills |
| JohnnyZhang483 | Bad MCP design costs your agent 5x more tokens | 15 | 1 | — | https://news.ycombinator.com/item?id=48407391 |
| avestura | Show HN: Sub-Agent MCP: LLM delegation and sub-agent orchestration via MCP | 6 | 1 | — | https://github.com/stormaref/Sub-Agent-MCP |
| rjpruitt16 | Show HN: Aquifer – an MCP runtime for spiky agent tool traffic | 3 | 0 | — | https://github.com/rjpruitt16/aquifer |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | https://codeguilds.dev |
| pmkelly4444 | Skills vs. MCP vs. prompts: which agent setup works best? | 3 | 1 | — | https://www.agentvoyagerproject.com/captains-log/1 |
| nmfisher | Claude Code and Blender MCP | 3 | 0 | — | https://hydroxide.dev/articles/blender-mcp-claude-code/ |
| doener | Agent Bazaar: Enabling Economic Alignment in Multi-Agent Marketplaces | 4 | 0 | — | https://www.chatpaper.ai/dashboard/paper/80941351-e4d5-4566-a458-aa93c4f7dbff |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | https://github.com/openclaw-easy/ViralMint |
| umbertotancorre | Show HN: YouTube MCP, give any AI agent access to YouTube | 5 | 3 | — | https://github.com/umbertotancorre/youtube-mcp |
| chaandannn | I built an MCP server so you can ask Claude about your cloud/software bill | 4 | 0 | — | https://getnable.com/ |
| cionut | Show HN: MCP for the ChatGPT Ads API – Query ChatGPT Ads from Claude and Codex | 3 | 1 | — | https://github.com/HYPD-AI/openai-ads-mcp |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @carnage4life.bsky.social | "Microsoft just launched an OpenClaw-style agent in Microsoft Teams... Claude Code & OpenClaw style products will be transformational for knowledge workers" | 32 | https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q |
| @bootstrapyouragent.bsky.social | "OpenClaw is free. Claude Code is free (with Claude Max). The Mac Mini you probably already own." | 12 | https://bsky.app/profile/bootstrapyouragent.bsky.social/post/3mnbw5b5yew2n |
| @hacker.at.thenote.app | "The TechBeat: Claude Code Works Better When You Let Sessions Die (6/6/2026)" | 3 | https://bsky.app/profile/hacker.at.thenote.app/post/3mnq3okljik2h |
| @jefferyharrell.bsky.social | "I'm using a Claude Code agent for this now. I paste in a picture and it gives me back alt text." | 3 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnry6vyyhl2t |
| @mhalle.bsky.social | "The equivalent inside of Claude Code (to avoid charged API usage) is to ask to write a skill that a sub-agent can use. The skill is code, docs, and data." | 3 | https://bsky.app/profile/mhalle.bsky.social/post/3mnlcs2o33s26 |
| @david-cornelson.bsky.social | "I use Claude code for writing software... absolutely is not with the swarm agent methodology." | 4 | https://bsky.app/profile/david-cornelson.bsky.social/post/3mnisshj4dk2w |
| @oliviacraft.bsky.social | "Claude Code AND Cursor in the same project? You need two files: CLAUDE.md + .cursor/rules/*.mdc" | 3 | https://bsky.app/profile/oliviacraft.bsky.social/post/3mn65jzmz2o2r |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers" | 1 | https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o |
| @cadaeic.space | "claude code agent just said to me 'for an LLM, the tool surface is their umwelt'" | 2 | https://bsky.app/profile/cadaeic.space/post/3mneiendmu224 |
| @morinaga2222.bsky.social | "Five things that caught my attention this week: Claude Code Agent View, ZAYA1-8B on AMD hardware, Harness productivity data" | 2 | https://bsky.app/profile/morinaga2222.bsky.social/post/3mntccx6sfo2j |
| @papoo7.bsky.social | "Your AI Agents Are Aging: Why Agent Lifespan Matters" | 2 | https://bsky.app/profile/papoo7.bsky.social/post/3mncvulhkle2e |
| @ollamabot.bsky.social | "Gemma 4 12B available across: Claude Code, Hermes Agent, OpenClaw" | 2 | https://bsky.app/profile/ollamabot.bsky.social/post/3mnitok3lsh23 |
| @jefferyharrell.bsky.social | "Claude Code lets you change the system prompt in a few ways. I use custom agent definitions which replace it." | 3 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mn6bpmbicd2o |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Official marketplace stats: 101 plugins (33 Anthropic); tonsofskills.com: 425 plugins, 2,810 skills, 200 agents |
| anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | Official Anthropic-managed plugin directory with automated validation |
| mcp.directory | https://mcp.directory/blog/claude-code-skills-vs-subagents-vs-plugins-vs-hooks-2026 | Decision tree: skills vs subagents vs plugins vs hooks with 12-section guide |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Two-surface explanation: skills (markdown → slash commands) vs MCP servers (external tools protocol) |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Claude Code plugins architecture: skills, agents, hooks, MCP, and LSP explained |
| polyskill.ai | https://polyskill.ai/blog/claude-code-mcp | MCP add/configure guide: `claude mcp add`, `/mcp` management |
| rotecodefraktion.de | https://www.rotecodefraktion.de/en/blog/agentic-07-mcp/ | Agentic Coding series: MCP solves library documentation staleness problem |
| boomi.com | https://boomi.com/platform/mcp/ | Enterprise MCP governance: expose, govern, and activate every tool agents need |
| github.com/zavora-ai/mcp-registry | https://github.com/zavora-ai/mcp-registry | MCP Registry control plane: registration, discovery, allow-lists, health, audit (Rust) |
| github.com/munnmajithia/skillforge | https://github.com/munnmajithia/skillforge | Open-source MCP skill pack ecosystem for AI coding agents |
| sre.azure.com | https://sre.azure.com/docs/capabilities/plugin-marketplace | Azure SRE Agent plugin marketplace: one-click skill import, SHA-256 change detection |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Top 4 MCP registries: mcp.so (20,222 servers), smithery.ai (7,000+), glama.ai, punkpeye/awesome-mcp-servers |
| explainx.ai | https://explainx.ai/blog/what-are-agent-skills-complete-guide | Skills vs MCP: skills = knowledge layer (when/why/how); MCP = raw tool access |
| docs.stacklok.com | https://docs.stacklok.com/toolhive/updates/2026/04/06/updates | ToolHive: reusable agent skills registry with OCI and Git sources |
| aws.amazon.com | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry in preview: governed catalog for agents, tools, skills, MCP servers |
| code.claude.com | https://code.claude.com/docs/en/changelog | Official Claude Code changelog with v2.1.169 --safe-mode documentation |

---

## Stats Block

```
├─ 🟠 Reddit: 11 threads
├─ 🔵 X: 13 posts │ 289 likes │ 41 reposts
├─ 🟢 HN: 18 stories │ 1,783 points │ 1,099 comments
├─ 🦋 Bluesky: 13 posts │ 72 likes │ 6 reposts
├─ 🌐 Web: 16 pages
└─ 🗣️ Top voices: @Bell_QuoLu, @hasantoxr, @carnage4life.bsky.social │ r/ClaudeCode, r/LovingOpenSourceAI, r/AiBuilders
```

---

## Data Gaps

- **YouTube/TikTok/Instagram: 0 results** - The skill scan returned zero video content. YouTube search returned 0 results on multiple attempts (likely query length + yt-dlp availability). ScrapeCreators returned HTTP 402 (Payment Required) for YouTube, TikTok, and Instagram. Video content about Claude Code skills/MCP is likely active but was not captured in this run.
- **GitHub: 0 items** - No GitHub token configured (GITHUB_TOKEN not set, gh CLI not authenticated). The modelcontextprotocol/servers and anthropics/claude-code repos were targeted but could not be queried directly for issues, PRs, or star activity.
- **X engagement data** - X token auth was present but entity-miss demotion affected most posts (all scored 0-16 with "fallback-local-score" reason). Top posts may be underrepresented.
- **Polymarket: 0 markets** - No prediction markets on Claude Code skills/MCP ecosystem topics found.
- **Evidence concentration warning** - The engine flagged "top evidence is highly concentrated in one source" - HN dominated by item count and engagement weight.
- **Coverage estimate:** ~65% - Reddit, X, HN, Bluesky, and Web are captured; YouTube (likely 15-20 high-view videos exist), GitHub stars/issues, and TikTok/Instagram creator content are missing.

---

## Key Quotes

> "The average developer uses Claude Code like ChatGPT. The top 1% use it like an engineering team." — [@Suryanshti777](https://x.com/Suryanshti777/status/2064213381557678493) on X

> "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" — [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "Idle plugins and MCP servers chewing through 25K to 40K tokens per session. Most people are paying $100/month and using maybe 30% of Claude's actual capability." — [@Dubibubiii](https://x.com/Dubibubiii/status/2064059729639244122) on X (Boris Cherny's talk)

> "40% of the context was tool definitions I never used. 20% was git history the agent re-read every turn. 15% was MCP server docs for servers I hadn't touched in two weeks. The model should have been working on my bug. Instead it was swimming through a room full of furniture." — [@danielderedev](https://x.com/danielderedev/status/2064035813516578864) on X

> "for an LLM, the tool surface is their umwelt" — [@cadaeic.space](https://bsky.app/profile/cadaeic.space/post/3mneiendmu224) on Bluesky (quoting a Claude Code agent)

> "The equivalent inside of Claude Code (to avoid charged API usage) is to ask to write a skill that a sub-agent can use. The skill is code, docs, and data." — [@mhalle.bsky.social](https://bsky.app/profile/mhalle.bsky.social/post/3mnlcs2o33s26) on Bluesky

> "every time we added an MCP server or wrote a skill, we had to copy it into each agent's config, in each agent's format, on each machine. They drifted constantly." — r/coolgithubprojects ([gaal CLI post](https://www.reddit.com/r/coolgithubprojects/comments/1tq4xc0/built_a_free_opensource_go_cli_to_stop/))

> "I have had several 2 hour long meetings I didn't go to regarding training on skills and mcp servers in claude code. This was a week ago." — [@usr_bin_roygbiv](https://x.com/usr_bin_roygbiv/status/2064139974103212247) on X

> "The Cowork plugin format is genuinely a different abstraction from raw MCP." — r/ClaudeCode ([WordPress plugin post](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/))

> "I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers and Microsoft just got a big leg up in this race." — [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) on Bluesky
