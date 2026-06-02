# Claude Code Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-06-02
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 11 threads | upvote data unavailable | r/ClaudeCode, r/ClaudeAI, r/AIAgentsInAction, r/ClaudeWorkflows |
| X/Twitter | 13 posts | 269 likes, 35 reposts | @_vmlops top post (202 likes) |
| Hacker News | 17 stories | 2,710 points, 1,566 comments | Strong engagement on daily-driver and dynamic-workflows posts |
| Bluesky | 13 posts | 48 likes, 2 reposts | |
| Web | 20 pages | — | 10 engine results + 10 supplemental |

---

## Synthesized Findings

### 1. The claude-code-setup Moment: Anthropic's Official Setup Plugin Goes Viral

The biggest signal this period is the viral spread of `claude-code-setup`, an official Anthropic plugin that scans a project and recommends (not configures) MCP servers, skills, hooks, subagents, and slash commands. [@_vmlops](https://x.com/_vmlops/status/2061008862971658528) kicked it off on May 31 with "Anthropic quietly shipped an official plugin for Claude Code" collecting 202 likes and 22 reposts - the highest engagement X post in the corpus. [@RodmanAi](https://x.com/RodmanAi/status/2061513772435718581), [@Radha_AI](https://x.com/Radha_AI/status/2061350828133568970), and [@NeuroAgentX](https://x.com/NeuroAgentX/status/2060689736742695246) amplified with progressively hyperbolic framing ("MASSIVE UPGRADE", "SECRET WEAPON", "completely different"). Install: `/plugin install claude-code-setup@claude-plugins-official`.

The most important correction came from [@MartinSzerment](https://x.com/MartinSzerment/status/2061030144802693283): "It doesn't. It scans your project and recommends what's worth enabling, but it touches nothing. It runs read-only. And that's the point. The value isn't automation, it's that it shows you what you're not using. Most people really are sitting on 20 percent of what Claude Code can do. This tool is a map, not an autopilot." [@riyazmd774](https://x.com/riyazmd774/status/2061457938557087951) confirmed: "Read-only mode. Does not modify your files." Discussed on X and Bluesky; broader analysis at [Groundy](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) and the [official plugin page](https://claude.com/plugins/claude-code-setup).

### 2. The Discovery Problem: "There's an npm-Shaped Hole in the AI Tooling Stack"

The most-cited friction point is skill discovery and distribution. An [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/) post crystallized the pattern: "We've been hitting the same operational pattern at every engineering team using AI tooling: one person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup." An [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) community builder created a searchable directory specifically because "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos."

The race to solve this produced [CodeGuilds](https://codeguilds.dev) (new community registry, launched June 1 on HN), [claudemarketplaces.com](https://claudemarketplaces.com/), [claudskills.com](https://claudskills.com/learn/claude-code-extensions/) (67,000+ indexed extensions), and [AgentSkillsHub](https://agentskillshub.dev/) (1,213+ verified skills). [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) tracked the growth: the ecosystem went from 1 registry in December 2025 to 8 major marketplaces by Q2 2026. The emerging pattern is MCP-based discovery: an agent connects to a marketplace's MCP server once and can search the full live catalog on demand.

### 3. Ecosystem Scale: 1,200+ MCP Servers, 400+ Plugins, 25+ Agent Frameworks

The scale of the Claude extension ecosystem is now documented. An [r/AIAgentsInAction](https://www.reddit.com/r/AIAgentsInAction/comments/1tb3yoe/the_full_claude_ecosystem_1200_mcp_servers_400/) thread published six reference files covering the full Claude ecosystem verified April 2026: 1,200+ MCP servers, 400+ plugins, 25+ agent frameworks. The official Anthropic marketplace ([anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)) ships 101 vetted plugins plus 68 partner plugins (GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, Firebase). [Claudskills.com](https://claudskills.com/learn/claude-code-extensions/) claims 67,000+ indexed extensions and 200,000+ monthly developer visits.

The hackathon validation: per [r/AIAgentsInAction](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/), a solo dev won the Anthropic hackathon ($15,000 prize) by shipping with Claude Code in eight hours, then open-sourced 38 specialized agents, 156 skills, 72 commands, and a 1,282-test security scanner. The repo sits at 153,000+ GitHub stars. [SkillsMP](https://skillsmp.com/) claims 1.5M+ agent skills compatible with Claude Code, Codex CLI, and ChatGPT.

### 4. Architecture Crystallizing: The 5-Layer Harness

The mental model for Claude Code configuration is hardening across platforms. [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky described it as "5 layers: CLAUDE.md → hooks → skills → plugins → MCP servers" with a counterintuitive insight: "switching from Sonnet to Opus adds less value than enabling these 5 layers on Sonnet." HN's highest-engagement Claude Code post this period - ["Claude Code as a Daily Driver"](https://arps18.github.io/posts/claude-code-mastery/) (446 points, 252 comments, May 27) - covers the same stack: Claude.md, Skills, Subagents, Plugins, and MCPs. Anthropic's own blog post ["Dynamic Workflows in Claude Code"](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) hit 198 points and 133 comments (May 28). ["Claude Code - Everything you can configure that the docs don't tell you"](https://buildingbetter.tech/p/i-read-the-claude-code-source-code) earned 326 points (May 29).

Key architectural guidance from [Codersera](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/) and [Refactix](https://refactix.com/ai-development-engineering/claude-code-plugins-packaging-integrations-distribution): skills cost ~30-50 tokens of context until invoked; a 5-server MCP setup costs 50k+ tokens upfront. The working pattern in 2026: pin one MCP per external system, write thin skills to orchestrate them.

### 5. MCP Pain Points: Context Tax, Process Explosion, "MCP Is Dead" Debate

The context overhead of MCP servers is generating real pushback. [@everydevai](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) on Bluesky: "Every enabled MCP server eats context window tokens on every message, even when you're not using it." Solution: Vibedock, which toggles MCP servers per project from the macOS menu bar without JSON editing. More severe: [@ygbr](https://x.com/ygbr/status/2061448670533292098) reported that 11 configured MCP servers caused Claude Desktop to spawn ~300 processes, pin 24GB of swap on a 32GB M2 Max, and produce 4 kernel panics in four days. Root cause: "the full MCP set is spawned per Cowork/agent session and never reaped."

[Bluesky/papoo7](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c) linked a "Why This 'MCP Is Dead' Take Matters for Claude Code Users" piece, keeping the ongoing debate alive. Anthropic's Tool Search feature is cited as reducing MCP context overhead by 85% via on-demand tool discovery.

### 6. Long-Tail MCP Builders: Niche Tools Flooding the Ecosystem

Individual builders are shipping highly specialized MCPs. [@render87](https://bsky.app/profile/render87.bsky.social/post/3mmtgqvjuan2g) built a DNS + email security MCP with 37 tools for Claude Code, Cursor, and Windsurf. [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) shipped Semble, a code search MCP running entirely on local CPU using 98% fewer tokens than grep+read. [@happy-homhom](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmuot5cnlw2b) highlighted an MCP that lets Claude Code work inside dev containers. HN surfaced a [Blender MCP integration](https://hydroxide.dev/articles/blender-mcp-claude-code/), an [Ableton Live MCP bridge for music production](https://bsky.app/profile/papoo7.bsky.social/post/3mn424xy72k2d), [86 MCP tools for an AI video generator](https://github.com/openclaw-easy/ViralMint), and [28 Shadcn design systems via MCP](https://github.com/marvkr/better-design). [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) landed 82pts on HN. The ecosystem is clearly moving beyond dev tooling into domain-specific agents.

[@gjuggler](https://x.com/gjuggler/status/2061150245048946801) named the formula for effective domain MCPs: "(1) a good MCP server, (2) thoughtful skills describing best practices & gotchas to avoid, and (3) an easy way to install that doesn't require forking a repo."

### 7. Supply Chain Security: VS Code Extension Breach as Warning Shot

[@caneallesta](https://x.com/caneallesta/status/2057174918224134456) flagged a significant supply chain incident: "One GitHub employee installed a VS Code extension. TeamPCP walked out with 3,800 internal repositories. GitHub confirmed it. A poisoned VS Code extension on a single employee's device gave attackers full access to internal private repositories." This context makes the security posture of agent skill marketplaces directly relevant. [AgentSkillsHub](https://agentskillshub.dev/) and [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) both emphasize security scanning as a differentiator; Agensi scans every skill before listing.

### 8. Cross-Ecosystem Builders: MCP as a Universal Protocol

The MCP protocol is increasingly multi-platform. [@developer.chrome.com](https://bsky.app/profile/developer.chrome.com/post/3mmciy2rd5k2w) announced the `chrome-devtools-mcp` package for coding agents including Claude Code, enabling real-time browser debugging. The [Grafana Assistant MCP](https://bsky.app/profile/grafana.bsky.social/post/3mmwmo4wufs2u) is being described as "a dream come true" for observability workflows. The [Cowork WordPress plugin](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/) author noted it expanded from Claude Desktop to Claude Code to Cursor to Codex CLI - confirming MCP as a write-once, run-everywhere protocol across competing AI coding tools. [Microsoft's cancellation of Claude Code licenses](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) (492pts, 466 comments) may reflect competitive positioning around this same protocol layer.

---

## Cross-Source Patterns

**Pattern 1: "20% utilization" framing dominates X conversation**
Multiple X posts ([@_vmlops](https://x.com/_vmlops/status/2061008862971658528), [@NeuroAgentX](https://x.com/NeuroAgentX/status/2060689736742695246), [@Radha_AI](https://x.com/Radha_AI/status/2061350828133568970)) frame claude-code-setup around the claim that "most people are only using Claude Code at 20% of its real power." This framing spread without attribution and was not sourced to any official Anthropic statement. [@MartinSzerment](https://x.com/MartinSzerment/status/2061030144802693283) on X provided the corrective.

**Pattern 2: Discovery/findability as the core unsolved problem**
Appeared on Reddit ([r/ClaudeCode npm-shaped hole](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/), [r/ClaudeAI directory builder](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/)), HN ([CodeGuilds launch](https://codeguilds.dev)), and supplemental web research (8 competing marketplace directories). Every platform surfaces this as an open problem.

**Pattern 3: MCP context overhead is real and growing**
Appeared on Bluesky ([@everydevai Vibedock](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v), [papoo7 "MCP Is Dead" debate](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c)), X ([@ygbr kernel panics](https://x.com/ygbr/status/2061448670533292098)), and practitioner guides ([Codersera](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/)). The performance cost of "always-on" MCPs is a design pressure across tools.

**Pattern 4: Skills-as-cheap-orchestration vs MCPs-as-expensive-gateways**
- Key quote: [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o): "switching from Sonnet to Opus adds less value than enabling these 5 layers on Sonnet"
- Corroborated by [Codersera](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/): "skills cost ~30-50 tokens; 5-server MCP setup costs 50k+ tokens upfront"
- Appeared on Bluesky, HN, and practitioner guides

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | There's an npm-shaped hole in the AI tooling stack | N/A | N/A | "one person builds up a vault...that 10x their output, and the rest of the team can't replicate the setup" | [link](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/) |
| r/ClaudeAI | I built a searchable directory for Claude Code plugins | N/A | N/A | "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) |
| r/AIAgentsInAction | The Full Claude Ecosystem: 1,200+ MCP Servers, 400+ Plugins, 25+ Agent Frameworks | N/A | N/A | Full ecosystem in six reference files, verified April 2026 | [link](https://www.reddit.com/r/AIAgentsInAction/comments/1tb3yoe/the_full_claude_ecosystem_1200_mcp_servers_400/) |
| r/AIAgentsInAction | This guy Won the Anthropic Hackathon Solo. Then He Open-Sourced the Stack | N/A | N/A | "38 Agents, 156 Skills, 1,282 Security Tests — 153,000+ stars" | [link](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/) |
| r/ClaudeWorkflows | [Workflow] Advanced Claude Code: Git-based Plugin Marketplace with Hooks | N/A | N/A | "Workflow value: 88/100 — Quality Control, Context & Memory, CLAUDE.md, Hooks, Skills, MCP, Subagents" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1t5w9db/workflow_advanced_claude_code_gitbased_plugin/) |
| r/ClaudeAI | Built five free Claude Code skills for video editing | N/A | N/A | "We open-sourced five Claude Code skills that run entirely on your machine" | [link](https://www.reddit.com/r/ClaudeAI/comments/1t3wmr9/built_five_free_claude_code_skills_for_video/) |
| r/ClaudeCode | I let Claude Code run my Instagram + TikTok marketing. Here's the plugin | N/A | N/A | "Wonda...generates content across ~40 models, then posts or schedules directly" | [link](https://www.reddit.com/r/ClaudeCode/comments/1te0jzb/i_let_claude_code_run_my_instagram_tiktok/) |
| r/ClaudeCode | Built a Cowork plugin for WordPress editing | N/A | N/A | "Started as Claude Desktop, expanded to Claude Code, Cursor, Codex CLI" | [link](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/) |
| r/ClaudeWorkflows | Raysense: Local MCP Server for Structural Codebase Memory | N/A | N/A | "Workflow value: 95/100 — prevents breakages during refactoring" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1t5w0ga/workflow_raysense_local_mcp_server_for_structural/) |
| r/ClaudeCode | Claude Code is powerful... but hard to "see" what's going on | N/A | N/A | "Built cc-manager — browser-based interface to visualize and manage your Claude Code setup" | [link](https://www.reddit.com/r/ClaudeCode/comments/1t40ead/claude_code_is_powerful_but_hard_to_see_whats/) |
| r/ClaudeCode | Just a Quick-start guide for anyone "Vibe-Coding" | N/A | N/A | "hesreallyhim/awesome-claude-code (~36.8k stars) — The canonical big list of skills, hooks, slash commands" | [link](https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @_vmlops | "Anthropic quietly shipped an official plugin for Claude Code. One click and it can analyze your project, set up hooks, skills, MCP servers, subagents & automate workflows" | 202 | 22 | [link](https://x.com/_vmlops/status/2061008862971658528) |
| @RodmanAi | "CLAUDE CODE JUST GOT A MASSIVE UPGRADE. A hidden official plugin scans your project and automatically recommends MCP servers → Subagents → Skills → Hooks → Automations" | 36 | 8 | [link](https://x.com/RodmanAi/status/2061513772435718581) |
| @Radha_AI | "Claude Code feels completely different once you install this... scans your entire project and automatically recommends MCP servers → hooks → subagents → skills → automations" | 13 | 4 | [link](https://x.com/Radha_AI/status/2061350828133568970) |
| @riyazmd774 | "claude-code-setup plugin...scans your codebase and recommends automations across five categories...Read-only mode. Does not modify your files." | 13 | 0 | [link](https://x.com/riyazmd774/status/2061457938557087951) |
| @MartinSzerment | "It doesn't. It scans your project and recommends what's worth enabling, but it touches nothing. It runs read-only...This tool is a map, not an autopilot." | 0 | 0 | [link](https://x.com/MartinSzerment/status/2061030144802693283) |
| @NeuroAgentX | "ANTHROPIC JUST DROPPED A SECRET WEAPON...Most people are only using Claude Code at 20% of its real power. This plugin changes everything." | 0 | 0 | [link](https://x.com/NeuroAgentX/status/2060689736742695246) |
| @gjuggler | "For literature search in mainstream agents to be really effective, you need (1) a good MCP server, (2) thoughtful skills describing best practices & gotchas to avoid..." | 2 | 1 | [link](https://x.com/gjuggler/status/2061150245048946801) |
| @ConneqtmeAI | "Claude Code is moving from AI coding assistant to AI engineering stack. Skills, MCP Servers, Hooks, Plugins, and Agents help teams connect tools, automate workflows" | 1 | 0 | [link](https://x.com/ConneqtmeAI/status/2061357499362521096) |
| @ygbr | "With only 11 configured MCP servers, Claude Desktop spawns ~300 MCP server processes and pins ~24 GB of swap...4 kernel panics in four days" | 1 | 0 | [link](https://x.com/ygbr/status/2061448670533292098) |
| @SimoneAtzori_ | "Anthropic has quietly released an official plugin for Claude Code: It scans your project and configures hooks, skills, MCP servers, subagents" | 0 | 0 | [link](https://x.com/SimoneAtzori_/status/2060818663066759612) |
| @_itsjustshubh | "building MCP servers and Claude Code plugins on the side, full-time SWE at big tech. would love to connect with anyone deep in AI tooling or agent infra" | 0 | 0 | [link](https://x.com/_itsjustshubh/status/2061640555763839216) |
| @JustJerry121 | "MCP servers + Claude Code plugins is a solid corner of agent infra. Glad to connect - what kind of plugin are you building first?" | 0 | 0 | [link](https://x.com/JustJerry121/status/2061710694844862569) |
| @caneallesta | "One GitHub employee installed a VS Code extension. TeamPCP walked out with 3,800 internal repositories...A poisoned VS Code extension on a single employee's device" | 1 | 0 | [link](https://x.com/caneallesta/status/2057174918224134456) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 446 | 252 | "mastery of Claude Code" | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| alattaran | DeepClaude – Claude Code agent loop with DeepSeek V4 Pro | 678 | 281 | Highest-point post of period | [link](https://github.com/aattaran/deepclaude) |
| sermakarevich | Microsoft starts canceling Claude Code licenses | 492 | 466 | Competitive repositioning signal | [link](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) |
| ankitg12 | Claude Code – Everything you can configure that the docs don't tell you | 326 | 65 | Deep config guide | [link](https://buildingbetter.tech/p/i-read-the-claude-code-source-code) |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | Official Anthropic best practices | [link](https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start) |
| mil22 | Dynamic Workflows in Claude Code | 198 | 133 | Anthropic blog on dynamic workflows | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| adamthegoalie | Show HN: adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | Multi-agent workflow for PR review | [link](https://github.com/adamjgmiller/adamsreview) |
| arnon | Academic Research Skills for Claude Code | 82 | 25 | Domain-specific skills gaining traction | [link](https://github.com/Imbad0202/academic-research-skills) |
| rajveerb | Why Ctrl+V won't paste images in Claude Code on WSL, with a fix | 55 | 90 | High engagement on UI friction | [link](https://rajveerbachkaniwala.com/blog/2026/05/24/on-the-difficulty-of-pasting-a-picture/) |
| finnworks | Show HN: skills-for-humanity – 171 structured reasoning skills for Claude Code | 28 | 7 | Reasoning skill library | [link](https://github.com/human-avatar/skills-for-humanity) |
| sermakarevich | Show HN: Spec-Driven Development Workflow for Claude Code | 20 | 12 | Workflow methodology | [link](https://news.ycombinator.com/item?id=48231575) |
| ankitg12 | Python utility package for building Claude Code hooks | 18 | 2 | Hook builder utility | [link](https://github.com/RasmusGodske/claude-hook-utils) |
| ex-aws-dude | Ask HN: Does Claude Code remove the need for so many front-end frameworks? | 12 | 17 | Philosophical debate | [link](https://news.ycombinator.com/item?id=48315680) |
| marvinkr | Show HN: Better Design – 28 Shadcn design systems (OSS, MCP: Cursor/Claude Code) | 13 | 0 | Design systems via MCP | [link](https://github.com/marvkr/better-design) |
| nmfisher | Claude Code and Blender MCP | 3 | 0 | Creative tool MCP integration | [link](https://hydroxide.dev/articles/blender-mcp-claude-code/) |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | New community registry launch | [link](https://codeguilds.dev) |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | 86-tool MCP integration | [link](https://github.com/openclaw-easy/ViralMint) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @papoo7.bsky.social | "Why This 'MCP Is Dead' Take Matters for Claude Code Users" | 3 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c) |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches : CLAUDE.md → hooks → skills → plugins → MCP servers...passer de sonnet à opus apporte moins que d'activer ces 5 couches" | 1 | [link](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) |
| @camilleroux.com | "Semble : un outil de recherche de code...~98% moins de tokens que grep+read, tourne entièrement en local sur CPU, et s'intègre comme serveur MCP" | 11 | [link](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) |
| @llms.activitypub.awakari.com.ap.brid.gy | "Анатомия Claude Code. Первичный анализ и наполнение контекста" (Claude Code anatomy: primary analysis, context enrichment, MCP) | 5 | [link](https://bsky.app/profile/llms.activitypub.awakari.com.ap.brid.gy/post/3mmwdaeacg5j2) |
| @jamiedavenport.bsky.social | "So many cool new features shipped in the past 24 hours but the MCP server is amazing. Claude Code working directly from issues on Plain." | 6 | [link](https://bsky.app/profile/jamiedavenport.bsky.social/post/3mn3ggi4m7s2e) |
| @papoo7.bsky.social | "Claude Code Meets Ableton Live: An MCP Bridge for Music Production" | 2 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn424xy72k2d) |
| @render87.bsky.social | "With 37 tools integrated, intodns-mcp saves time by providing exact zone-file edits in under 3 seconds...DNS + email security MCP" | 2 | [link](https://bsky.app/profile/render87.bsky.social/post/3mmtgqvjuan2g) |
| @happy-homhom.bsky.social | "An MCP Server That Lets Claude Code Work Inside Dev Containers" | 3 | [link](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmuot5cnlw2b) |
| @grafana.bsky.social | "Grafana Assistant is a 'dream come true'...Watch how he uses it with our MCP in Claude Code" | 2 | [link](https://bsky.app/profile/grafana.bsky.social/post/3mmwmo4wufs2u) |
| @everydevai.bsky.social | "Every enabled MCP server eats context window tokens on every message, even when you're not using it. Vibedock lets you toggle MCP servers per project" | 3 | [link](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) |
| @happy-homhom.bsky.social | "Claude Code Routines for Financial Monitoring: A Practical Test Case" | 3 | [link](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmnuzr36cx2q) |
| @goclaw.bsky.social | "Claude Code và Model Context Protocol mở ra kỷ nguyên mới cho lập trình tự động" (Claude Code and MCP opening new era for automated programming) | 1 | [link](https://bsky.app/profile/goclaw.bsky.social/post/3mml3lygcot2y) |
| @developer.chrome.com | "Let your coding agent control and inspect a live browser using Chrome DevTools for agents. With the chrome-devtools-mcp package, equip coding agents like...Claude Code" | 6 | [link](https://bsky.app/profile/developer.chrome.com/post/3mmciy2rd5k2w) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| DEV Community (alexcloudstar) | [link](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) | How skills, MCP servers, and plugins fit together in 2026 from a practitioner |
| ClaudSkills | [link](https://claudskills.com/learn/claude-code-extensions/) | 67,000+ indexed extensions; disambiguation table for skills/hooks/plugins/MCP |
| ClaudSkills | [link](https://claudskills.com/learn/claude-code-mcp-servers/) | 200+ tool MCP server directory |
| Skywork.ai | [link](https://skywork.ai/blog/claude-code-skills-market-ultimate-guide/) | Skills market overview with enterprise governance patterns |
| ai-trove.com | [link](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) | Skills, agents, hooks, MCP, and LSP explained by security/ML expert |
| Developer Toolkit | [link](https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/) | MCP setup guide: Sentry + GitHub + database + Jira from one session |
| ClaudeFolio | [link](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) | Skills vs MCP servers: different layers solving different problems |
| llmbestpractices.com | [link](https://llmbestpractices.com/howto/set-up-an-mcp-claude-code-skill) | Step-by-step MCP skill setup guide |
| Skywork.ai | [link](https://skywork.ai/blog/ai-bot/claude-code-skill-marketplace-ultimate-guide/) | Skill marketplace enterprise guide with orchestration patterns |
| Refactix | [link](https://refactix.com/ai-development-engineering/claude-code-plugins-packaging-integrations-distribution) | Plugin packaging and distribution for teams; solves the "dotfile sync" problem |
| Codersera | [link](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/) | Token cost analysis: skills (30-50 tokens) vs MCP (50k+ upfront) |
| Clarista | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Complete guide to official marketplace with partner plugin list |
| Groundy | [link](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | How Anthropic's official plugin ecosystem works and how to navigate it |
| Composio | [link](https://composio.dev/content/top-claude-code-plugins) | Best Claude Code plugins in 2026 across official/MCP/LSP/design/workflow categories |
| Claude Docs (official) | [link](https://code.claude.com/docs/en/skills) | Official skills documentation |
| GitHub - claude-plugins-official | [link](https://github.com/anthropics/claude-plugins-official) | Anthropic's official plugin registry source |
| claude-code-setup plugin | [link](https://claude.com/plugins/claude-code-setup) | Official claude-code-setup plugin page |
| Agensi | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 8 major marketplaces documented; security-scanning as differentiator |
| AgentSkillsHub | [link](https://agentskillshub.dev/) | 1,213+ verified skills with security analysis |
| SkillsMP | [link](https://skillsmp.com/) | 1.5M+ agent skills across Claude Code, Codex CLI, ChatGPT |

---

## Stats Block

```
├─ 🟠 Reddit: 11 threads │ upvotes N/A │ N/A comments
├─ 🔵 X: 13 posts │ 269 likes │ 35 reposts
├─ 🟢 HN: 17 stories │ 2,710 points │ 1,566 comments
├─ 🦋 Bluesky: 13 posts │ 48 likes │ 2 reposts
├─ 🌐 Web: 20 pages - claudskills.com, dev.to, skywork.ai, refactix.com, codersera.com, groundy.com, composio.dev, agensi.io, agentskillshub.dev, skillsmp.com
└─ 🗣️ Top voices: @_vmlops, @RodmanAi, @gjuggler, @MartinSzerment │ r/ClaudeCode, r/AIAgentsInAction, r/ClaudeAI
```

---

## Data Gaps

- **YouTube returned 0 results** - ScrapeCreators returned HTTP 402; yt-dlp returned no results for these queries. Video walkthroughs of Claude Code skill/plugin setup likely exist but were not captured.
- **TikTok and Instagram returned 0 results** - No MCP/skills content surfaced on these platforms in the search window; either the topic is too developer-specific or search terms don't match creator vocabulary.
- **Reddit upvote/comment counts unavailable** - Reddit API returning 403 during run; posts were retrieved via RSS fallback without engagement metrics.
- **GitHub returned 0 items** - No GitHub token configured; repo-level data (star counts, README content, issue discussions) not captured.
- **Bluesky engagement is sparse** - Highest post had 11 likes; platform skews toward developers sharing links rather than high-engagement discussion.
- **"MCP Is Dead" debate** - Referenced in Bluesky post but the underlying piece (papoo.work) was not fully fetched. The argument's substance is missing from this corpus.
- **Approximate coverage:** 70% - strong on X viral content, HN technical discussion, and web explainers; weak on video, TikTok practitioner demos, and Reddit engagement signals.

---

## Key Quotes

> "There's an npm-shaped hole in the AI tooling stack. One person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup." — [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/)

> "It doesn't. It scans your project and recommends what's worth enabling, but it touches nothing. It runs read-only. And that's the point. The value isn't automation, it's that it shows you what you're not using. Most people really are sitting on 20 percent of what Claude Code can do. This tool is a map, not an autopilot." — [@MartinSzerment](https://x.com/MartinSzerment/status/2061030144802693283) on X

> "le harness de claude code en 5 couches : CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (the counterintuitive: switching from Sonnet to Opus adds less value than enabling these 5 layers on Sonnet) — [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "Every enabled MCP server eats context window tokens on every message, even when you're not using it." — [@everydevai.bsky.social](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) on Bluesky

> "With only 11 configured MCP servers, Claude Desktop spawns ~300 MCP server processes and pins ~24 GB of swap for 5+ hours, repeatedly driving a 32 GB M2 Max into total memory starvation. 4 kernel panics in four days." — [@ygbr](https://x.com/ygbr/status/2061448670533292098) on X

> "For literature search in mainstream agents to be really effective, you need (1) a good MCP server, (2) thoughtful skills describing best practices & gotchas to avoid, and (3) an easy way to install that doesn't require forking a repo." — [@gjuggler](https://x.com/gjuggler/status/2061150245048946801) on X

> "I kept running into the same problem with Claude Code plugins: discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer the questions I actually cared about: Is this maintained? What does it install? Does it use hooks or MCP servers?" — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/)

> "Claude Code is moving from AI coding assistant to AI engineering stack. Skills, MCP Servers, Hooks, Plugins, and Agents help teams connect tools, automate workflows, and scale development." — [@ConneqtmeAI](https://x.com/ConneqtmeAI/status/2061357499362521096) on X

> "One GitHub employee installed a VS Code extension. TeamPCP walked out with 3,800 internal repositories. A poisoned VS Code extension on a single employee's device gave attackers full access to internal private repositories." — [@caneallesta](https://x.com/caneallesta/status/2057174918224134456) on X (supply chain risk warning)
