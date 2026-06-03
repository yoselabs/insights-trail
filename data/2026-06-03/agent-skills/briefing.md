# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-03
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 4 threads | — | r/ClaudeAI, r/ClaudeCode |
| X/Twitter | 14 posts | 252 likes, 32 reposts | Top voices: @automate_archit, @RodmanAi, @Atenov_D |
| Hacker News | 22 stories | 2,325 points, 1,364 comments | High-signal developer discussion |
| Bluesky | 13 posts | 48 likes, 2 reposts | Active MCP/skills discussion |
| Web | 12 pages | — | via WebSearch supplements |

---

## Synthesized Findings

### 1. The Official Claude Code Plugin Ecosystem Has Arrived and Is Growing Fast

Anthropic launched an official Claude Code plugin directory in early 2026, transforming the terminal AI coding assistant into a comprehensively extensible platform. The ecosystem has scaled rapidly: the community-curated [claudemarketplaces.com](https://claudemarketplaces.com/) now indexes 6,700+ skills, 2,500+ marketplaces, and 11,200+ MCP servers. The Agent Skills Marketplace separately catalogs 65,000+ skills organized into Tools (22,506), Development (19,370), Data & AI (12,997), and Business categories. On X, [@RodmanAi](https://x.com/RodmanAi/status/2061513772435718581) captured the moment: "CLAUDE CODE JUST GOT A MASSIVE UPGRADE. Most people are using it wrong. A hidden official plugin scans your project and automatically recommends: MCP servers, Subagents, Skills, Hooks, Automations. One install turns Claude Code into a full AI development environment." (71 likes)

The officially published taxonomy, synthesized across [ai-trove.com](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins), [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers), and the HN post "[Claude Code as a Daily Driver](https://arps18.github.io/posts/claude-code-mastery/)" (447 pts, 252 comments), distinguishes five extension layers: CLAUDE.md for project rules, hooks for lifecycle automation, skills for reusable markdown instructions, plugins for bundled distribution, and MCP servers for external tool connections. On Bluesky, [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) summarized the counterintuitive reality: "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers - le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (switching to Opus matters less than activating these 5 layers on Sonnet).

Discussed on: X/Twitter, Hacker News, Bluesky, Web

### 2. MCP Servers Are Becoming the Dominant Integration Primitive

The Model Context Protocol has crossed a tipping point. The official [modelcontextprotocol.io registry](https://registry.modelcontextprotocol.io/) now lists 800+ verified servers, while the wider community tracks 13,000+. [mcp.so](https://roxyapi.com/blogs/mcp-registries-where-to-list-your-server-2026) lists 20,222. Major cloud providers are fully committed: Google Cloud announced 50+ Google-managed MCP servers in GA/preview, and AWS launched its Agent Registry (Bedrock AgentCore) for private, governed MCP catalogs within organizations.

[@automate_archit](https://x.com/automate_archit/status/2062011593274372454) on X made the boldest claim: "NOBODY IS TALKING ABOUT THIS, BUT MCP JUST KILLED 90% OF SAAS INTEGRATIONS. Last week I replaced 6 internal tools at a client with 1 Claude Code agent + 4 MCP servers. Cost: $200/mo. Saved: $4,800/mo." Their follow-up thread ([part 2](https://x.com/automate_archit/status/2062011597586149598)) detailed wiring Gmail, Postgres, Stripe, and an internal CRM into one agent running 24/7. The community consensus from [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) and practitioners: MCP servers are for persistent integrations, while Bash is for one-off commands - per [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp): "prefer MCP tools over Bash when the integration will be used across sessions."

Practical MCP adoption stories proliferating on Bluesky include [@yobyot](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c) ("Using #Claude Code with the new #AWS #MCP server has changed my life. Writing #CloudFormation templates has never been more fun") and [@grafana](https://bsky.app/profile/grafana.bsky.social/post/3mmwmo4wufs2u) calling their Grafana Assistant MCP a "dream come true" for observability. Creative applications are also emerging: an [Ableton Live MCP bridge for music production](https://bsky.app/profile/papoo7.bsky.social/post/3mn424xy72k2d), a [Blender MCP on HN](https://hydroxide.dev/articles/blender-mcp-claude-code/), and a developer who [gave an AI video generator 86 MCP tools](https://github.com/openclaw-easy/ViralMint) so Claude Code could drive it.

Discussed on: X/Twitter, Bluesky, Hacker News, Web

### 3. Community Registries and Marketplaces Are Fragmenting (and Consolidating)

The registry landscape is crowded. On HN, a new [CodeGuilds community registry](https://codeguilds.dev) for Claude Code skills, agents, and MCP servers launched June 1 (3 pts). Third-party marketplaces multiply: [claudemarketplaces.com](https://claudemarketplaces.com/), [awesome-skills.com](https://awesome-skills.com/), [claudskills.com](https://claudskills.com/learn/claude-code-plugins/), [tonsofskills.com](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) (425 plugins, 2,810 skills, 200 agents with a ccpi CLI package manager). Cross-agent portability is becoming a design priority: [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) uses the open agentskills.io standard, portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ other agents.

On X, [@dani_avila7](https://x.com/dani_avila7/status/2013799393581842636) noted "The Skills ecosystem is growing fast, and new marketplaces/registries are already emerging. Here are 3 places where you can distribute your Skills today." The [MCP registry comparison at TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries) identifies mcp.so, smithery.ai, glama.ai/mcp, and the official modelcontextprotocol.io registry as the four that matter in 2026. Enterprise infrastructure is emerging: [Kong MCP Registry](https://konghq.com/products/mcp-registry) and [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) for governed, OAuth-secured tool access.

MCP Server Cards - a new standard for exposing server metadata via .well-known URLs enabling programmatic discovery - are positioned as the answer to fragmentation, per [RoxyAPI](https://roxyapi.com/blogs/mcp-registries-where-to-list-your-server-2026).

Discussed on: X/Twitter, Hacker News, Web

### 4. The Extension Taxonomy Is Confusing Practitioners

The most upvoted community question on [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) captures the confusion: "Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md in Claude Code? I keep seeing these terms thrown around in tutorials and videos, but I've never seen anyone give a concrete example that makes the difference actually click." Anthropic responded with official documentation and launched 13+ free AI courses including Agentic AI and Claude Code, per [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tjpfh8/anthropic_officially_launched_13_free_ai_courses/).

The community has filled the gap: [ai-trove.com](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) distinguishes skills (markdown instruction files, 30-50 tokens each, loaded on-demand) from MCP servers (external tool connections, can use 50k+ tokens). [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) explains: "skills are markdown files in your repo that become custom slash commands the tool can run, and MCP servers are external services that connect to the tool over a standard protocol and expose new tools the model can call." The HN post "[Dynamic Workflows in Claude Code](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code)" (199 pts, 134 comments, May 28) from Anthropic directly addresses advanced composition patterns. Hooks now come in three types per [claudefa.st](https://claudefa.st/blog/tools/hooks/hooks-guide): shell command hooks, agent hooks (spawn a subagent that can read files and run commands), and http hooks (POST to external endpoints).

Discussed on: Reddit, Hacker News, Bluesky, Web

### 5. Tooling Around the Ecosystem Is Maturing: Config Management, MCP Toggling, Sandboxing

Peripheral tooling is proliferating to address real pain points. [@BIGBULLapp](https://x.com/BIGBULLapp/status/2061551007683764682) announced `SaladDay/cc-switch-cli`, which unifies provider settings for Claude Code, Codex, Gemini, OpenCode, Hermes, and OpenClaw "into one place, handling MCP servers, prompts, and local proxy routes without making you edit dotfiles across three directories." On Bluesky, [@everydevai](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) highlighted a real cost: "Every enabled MCP server eats context window tokens on every message, even when you're not using it. Vibedock lets you toggle MCP servers per project from the macOS menu bar, no JSON editing." HN featured [SafeSandbox](https://github.com/Baukaalm/safesandbox) ("infinite undo for AI coding agents"), [agent-dash](https://news.ycombinator.com/item?id=48118041) (TUI for managing Claude Code/OpenCode in tmux), and [Teaching tmux to babysit Claude Code agents](https://blog.angeloff.name/post/2026/05/29/teaching-tmux-to-babysit-my-claude-code-agents/). The [Semble tool](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) (11 likes on Bluesky) offers MCP-compatible code search consuming ~98% fewer tokens than grep+read.

Permission security is also surfacing as a theme. [@jungleskellam](https://x.com/jungleskellam/status/2061981297271349695) wrote: "Permission is not a mood. It is a scoped capability. Claude Code has `deny`, `ask`, and `allow`, with deny winning first. MCP roots are `file://` boundaries the client exposes to servers... stop writing 'agent may deploy'. Write the exact gate. Tool, path, secret, reviewer, expiry. Everything else is permission theatre."

Discussed on: X/Twitter, Bluesky, Hacker News

### 6. Practitioners Are Building Real Production Automation with Claude Code + MCP

The "orchestration > model power" thesis is winning. [@automate_archit](https://x.com/automate_archit/status/2062013383449489788) stated: "Hard agree. Orchestration > raw model power in 2026. Claude Code + MCP makes multi-agent setups trivial - wire up Gmail/Stripe/Postgres servers, define handoffs, ship. The isolated 'chatbot' era is dead." [@Atenov_D](https://x.com/Atenov_D/status/2061807438098043249) (87 likes) gave a practical take: "5,000+ MCP servers exist. Most are useless. These five do everything that matters: Tavily (search for AI agents), Playwright (browser automation), [and three more]." Solo developers are shipping MCP plugins on the side: [@_itsjustshubh](https://x.com/_itsjustshubh/status/2061954000728080542) described building "mcp servers for calendar, events, socials automation. shipping every couple weeks."

HN's highest-signal content included "[Claude Code as a Daily Driver](https://arps18.github.io/posts/claude-code-mastery/)" (447 pts), "[How Claude Code works in large codebases](https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start)" (248 pts), and "[Academic Research Skills for Claude Code](https://github.com/Imbad0202/academic-research-skills)" (82 pts). The [boringbot Substack](https://boringbot.substack.com/p/claude-code-skills-subagents-hooks) put it together: "Claude Code: Skills, Subagents, Hooks, Plugins, and Harnesses for Production Multi-Agent Workflows." On Bluesky, [@happy-homhom](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmnuzr36cx2q) shared "Claude Code Routines for Financial Monitoring: A Practical Test Case."

Discussed on: X/Twitter, Hacker News, Bluesky

---

## Cross-Source Patterns

**Pattern 1: MCP-as-SaaS-replacement narrative is spreading**
- Platforms: X/Twitter (strongest), Bluesky, HN
- Signal: Multiple independent practitioners claiming MCP + Claude Code replaced multiple internal tools. [@automate_archit](https://x.com/automate_archit/status/2062011593274372454): "replaced 6 internal tools at a client with 1 Claude Code agent + 4 MCP servers. Cost: $200/mo. Saved: $4,800/mo." [@dancolta](https://x.com/dancolta/status/2061776458024894602): "once the server is wired up the diff review loop gets surprisingly fast."

**Pattern 2: Taxonomy confusion driving documentation demand**
- Platforms: Reddit, HN, Web
- Signal: The r/ClaudeCode thread asking for a concrete difference between Hooks/Skills/Plugins/SKILL.md/CLAUDE.md/agents.md reflects widespread confusion. Multiple documentation sites (ai-trove.com, claudefolio.com, claudskills.com, llmbestpractices.com) launched explainer guides in May 2026.

**Pattern 3: Ecosystem fragmentation with consolidation attempts**
- Platforms: HN, Web, X/Twitter
- Signal: Dozens of competing skill marketplaces (claudemarketplaces.com, codeguilds.dev, tonsofskills.com, agentskills.io). The MCP registry landscape has four dominant options (mcp.so, smithery.ai, glama.ai/mcp, official registry). Enterprise vendors (Kong, AWS, Google Cloud) entering with governed alternatives.

**Pattern 4: "5 layers" mental model gaining traction**
- Platforms: Bluesky, HN
- Signal: [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) articulated the widely-shared mental model: CLAUDE.md → hooks → skills → plugins → MCP servers. The counterintuitive finding: activating these 5 layers on Sonnet beats upgrading to Opus without them.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md? | — | — | "I keep seeing these terms thrown around in tutorials and videos, but I've never seen anyone give a concrete example that makes the difference actually click." | [link](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) |
| r/ClaudeAI | Anthropic officially launched 13+ FREE AI courses with certificates (Including Agentic AI and Claude Code!) | — | — | "Anthropic quietly dropped a massive library of completely free, official training modules." | [link](https://www.reddit.com/r/ClaudeAI/comments/1tjpfh8/anthropic_officially_launched_13_free_ai_courses/) |
| r/ClaudeAI | Hugging Face co-founder says Qwen 3.6 27B on airplane mode is close to latest Opus in Claude Code | — | — | — | [link](https://www.reddit.com/r/ClaudeAI/comments/1t8v7z0/hugging_face_cofounder_says_qwen_36_27b_running/) |
| r/ClaudeAI | If the EU had built Claude | — | — | "There's also a 55% tokens tax for every prompt." | [link](https://www.reddit.com/r/ClaudeAI/comments/1t6c26a/if_the_eu_had_built_claude/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @RodmanAi | "A hidden official plugin scans your project and automatically recommends: MCP servers, Subagents, Skills, Hooks, Automations" | 71 | 9 | [link](https://x.com/RodmanAi/status/2061513772435718581) |
| @Atenov_D | "5,000+ MCP servers exist. Most are useless. These five do everything that matters. Tavily... Playwright..." | 87 | 6 | [link](https://x.com/Atenov_D/status/2061807438098043249) |
| @automate_archit | "replaced 6 internal tools at a client with 1 Claude Code agent + 4 MCP servers. Cost: $200/mo. Saved: $4,800/mo." | 2 | 0 | [link](https://x.com/automate_archit/status/2062011593274372454) |
| @automate_archit | "Orchestration > raw model power in 2026. Claude Code + MCP makes multi-agent setups trivial." | 1 | 0 | [link](https://x.com/automate_archit/status/2062013383449489788) |
| @automate_archit | "Client had 6 disconnected tools + a VA doing manual data entry. I built ONE Claude Code agent with MCP servers for Gmail, Postgres, Stripe, their internal CRM." | 0 | 0 | [link](https://x.com/automate_archit/status/2062011597586149598) |
| @BIGBULLapp | "SaladDay/cc-switch-cli unifies provider settings for Claude Code, Codex, Gemini, OpenCode, Hermes, and OpenClaw into one place." | 2 | 1 | [link](https://x.com/BIGBULLapp/status/2061551007683764682) |
| @jungleskellam | "Permission is not a mood. It is a scoped capability... Everything else is permission theatre." | 2 | 0 | [link](https://x.com/jungleskellam/status/2061981297271349695) |
| @_itsjustshubh | "building claude code plugins under brainrot creations. mcp servers for calendar, events, socials automation. shipping every couple weeks" | 2 | 0 | [link](https://x.com/_itsjustshubh/status/2061954000728080542) |
| @_itsjustshubh | "building MCP servers and Claude Code plugins on the side, full-time SWE at big tech." | 0 | 0 | [link](https://x.com/_itsjustshubh/status/2061640555763839216) |
| @JustJerry121 | "MCP servers + Claude Code plugins is a solid corner of agent infra." | 0 | 0 | [link](https://x.com/JustJerry121/status/2061710694844862569) |
| @mtnleonardi | "dos cuentas de claude code completamente separadas en la misma compu, cada una con sus logins, historial, skills y mcp servers propios" | 1 | 0 | [link](https://x.com/mtnleonardi/status/2061626972527026389) |
| @dancolta | "tried mcp servers with claude code for a few internal builds, the change management angle is the part i keep underestimating" | 2 | 0 | [link](https://x.com/dancolta/status/2061776458024894602) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| pretext | Using Claude Code: The unreasonable effectiveness of HTML | 528 | 274 | — | [link](https://twitter.com/trq212/status/2052809885763747935) |
| robertkarl | Microsoft starts canceling Claude Code licenses | 492 | 466 | — | [link](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) |
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 447 | 252 | — | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | [link](https://github.com/DrCatHicks/learning-opportunities) |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | [link](https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start) |
| mil22 | Dynamic Workflows in Claude Code | 199 | 134 | — | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| arnon | Academic Research Skills for Claude Code | 82 | 25 | — | [link](https://github.com/Imbad0202/academic-research-skills) |
| marvinkr | Show HN: Better Design – 28 Shadcn design systems (OSS, MCP: Cursor/Claude Code) | 13 | 0 | — | [link](https://github.com/marvkr/better-design) |
| anideshp | Show HN: Agent FM – local, open-source radio for Claude Code and Codex agents | 9 | 0 | — | [link](https://github.com/agentfm-ai/agent-fm) |
| sabahattink | Show HN: Full Stack HQ – Claude.md and Agent Stack for Claude Code | 10 | 0 | — | [link](https://github.com/sabahattink/antigravity-fullstack-hq) |
| pretext | Agent View in Claude Code | 5 | 2 | — | [link](https://claude.com/blog/agent-view-in-claude-code) |
| nmfisher | Claude Code and Blender MCP | 3 | 0 | — | [link](https://hydroxide.dev/articles/blender-mcp-claude-code/) |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | [link](https://codeguilds.dev) |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | [link](https://github.com/openclaw-easy/ViralMint) |
| StanAngeloff | Teaching tmux to babysit my Claude Code agents | 3 | 0 | — | [link](https://blog.angeloff.name/post/2026/05/29/teaching-tmux-to-babysit-my-claude-code-agents/) |
| chaandannn | I built an MCP server so you can ask Claude about your cloud/software bill | 4 | 0 | — | [link](https://getnable.com/) |
| detente18 | Show HN: Lite-Harness – Self-Hosted Cursor Agents (Use Claude Code/OpenCode) | 6 | 0 | — | [link](https://github.com/LiteLLM-Labs/lite-harness) |
| jsingh2525 | Arch-Decision – A multi-agent architecture tool for Claude Code | 3 | 0 | — | [link](https://github.com/jsingh6/arch-decision) |
| baursha | SafeSandbox – infinite undo for AI coding agents (Cursor, Claude Code, Codex) | 3 | 0 | — | [link](https://github.com/Baukaalm/safesandbox) |
| ij23 | LiteLLM Agent Platform: Run Claude Code/Codex On-Prem Sandboxes and Vaults | 3 | 0 | — | [link](https://github.com/BerriAI/litellm-agent-platform) |
| fdarian | agent-dash: TUI for managing Claude Code and OpenCode in tmux | 3 | 0 | — | [link](https://news.ycombinator.com/item?id=48118041) |
| baursha | SafeSandbox – infinite undo for AI coding agents | 3 | 0 | — | [link](https://github.com/Baukaalm/safesandbox) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @papoo7.bsky.social | Why This "MCP Is Dead" Take Matters for Claude Code Users | 3 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c) |
| @camilleroux.com | Semble: MCP code search ~98% fewer tokens than grep+read, works with Claude Code/Cursor/Codex | 11 | [link](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) |
| @alternativeto.net | A new free Slack alternative for teams with Claude Code built into every channel, MCP support, 2,000+ integrations | 6 | [link](https://bsky.app/profile/alternativeto.net/post/3mndqzjlg6p2s) |
| @jamiedavenport.bsky.social | Claude Code MCP server is amazing - working directly from issues on Plain | 6 | [link](https://bsky.app/profile/jamiedavenport.bsky.social/post/3mn3ggi4m7s2e) |
| @llms.activitypub | Anatomy of Claude Code: context layers for agents (CLAUDE.md, hooks, skills, plugins, MCP) | 5 | [link](https://bsky.app/profile/llms.activitypub.awakari.com.ap.brid.gy/post/3mmwdaeacg5j2) |
| @everydevai.bsky.social | Every enabled MCP server eats context window tokens - Vibedock toggles per project | 3 | [link](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) |
| @happy-homhom.bsky.social | An MCP Server That Lets Claude Code Work Inside Dev Containers | 3 | [link](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmuot5cnlw2b) |
| @happy-homhom.bsky.social | Claude Code Routines for Financial Monitoring: A Practical Test Case | 3 | [link](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmnuzr36cx2q) |
| @franckparienti.bsky.social | le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers | 1 | [link](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) |
| @papoo7.bsky.social | Claude Code Meets Ableton Live: An MCP Bridge for Music Production | 2 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn424xy72k2d) |
| @render87.bsky.social | intodns-mcp: MCP server for DNS + email security, 37 tools for Claude Code/Cursor/Windsurf | 2 | [link](https://bsky.app/profile/render87.bsky.social/post/3mmtgqvjuan2g) |
| @grafana.bsky.social | Grafana Assistant MCP in Claude Code: "dream come true" for observability | 2 | [link](https://bsky.app/profile/grafana.bsky.social/post/3mmwmo4wufs2u) |
| @yobyot.bsky.air11.social | Using #Claude Code with the new #AWS #MCP server has changed my life. Writing CloudFormation templates. | 1 | [link](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community hub: 6,700+ skills, 2,500+ marketplaces, 11,200+ MCP servers indexed |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Authoritative taxonomy: skills vs plugins vs MCP vs hooks vs agents explained |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | "Skills are markdown files in your repo that become custom slash commands; MCP servers expose new tools the model can call" |
| claudefa.st | https://claudefa.st/blog/tools/hooks/hooks-guide | Complete guide to all 12 Claude Code lifecycle hook events; 3 hook types (shell, agent, http) |
| llmbestpractices.com | https://llmbestpractices.com/ai-agents/claude-code-mcp | MCP integration guide; "prefer MCP tools over Bash when the integration will be used across sessions" |
| llmbestpractices.com | https://llmbestpractices.com/howto/set-up-an-mcp-claude-code-skill | Step-by-step MCP skill setup for Claude Code |
| developertoolkit.ai | https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/ | MCP setup guide: connecting external tools from production bug triage to database queries |
| claudskills.com | https://claudskills.com/learn/claude-code-plugins/ | "Claude Code does not have a formal plugin system in the way VS Code has extensions — there is no central marketplace" (honest caveat) |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Plugin distribution patterns: personal to org rollout |
| github.com/juftin/skills | https://github.com/juftin/skills | Cross-platform agent skills directory compatible with Claude Code, Codex, Gemini CLI |
| groundy.com | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Anthropic official plugin ecosystem explained; 55+ curated official plugins |
| boringbot.substack.com | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Production multi-agent workflows with skills, subagents, hooks, plugins, and harnesses |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP Registries 2026: mcp.so, smithery.ai, glama.ai/mcp, official registry compared |
| roxyapi.com | https://roxyapi.com/blogs/mcp-registries-where-to-list-your-server-2026 | MCP Server Cards standard for .well-known discovery; registry landscape overview |
| aws.amazon.com | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry (Bedrock AgentCore Preview): private governed catalog for agents, tools, MCP servers |
| cloud.google.com | https://cloud.google.com/blog/products/ai-machine-learning/google-managed-mcp-servers-are-available-for-everyone | Google-managed MCP servers: 50+ across GA and preview |
| github.com/netresearch | https://github.com/netresearch/claude-code-marketplace | Open agentskills.io standard: portable skills across Claude Code, Cursor, Copilot, Codex, Gemini CLI, 30+ agents |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code Skills to Try in 2026 |
| agentic-community | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP Gateway: OAuth auth, dynamic tool discovery, governed access |

---

## Stats Block

```
├─ 🟠 Reddit: 4 threads
├─ 🔵 X: 14 posts │ 252 likes │ 32 reposts
├─ 🟡 HN: 22 stories │ 2,325 points │ 1,364 comments
├─ 🦋 Bluesky: 13 posts │ 48 likes │ 2 reposts
├─ 🌐 Web: 12 pages
└─ 🗣️ Top voices: @automate_archit, @RodmanAi, @Atenov_D │ r/ClaudeAI, r/ClaudeCode │ @papoo7.bsky.social, @camilleroux.com
```

---

## Data Gaps

- **YouTube:** 0 results. YouTube search returned empty; ScrapeCreators YouTube returned HTTP 402 (payment required). Likely high-value tutorials and demos exist but were not captured.
- **TikTok:** 0 results. No TikTok coverage captured.
- **Instagram:** 0 results. SC v2 reels endpoint returned empty for multi-token query.
- **GitHub:** 0 results. No GitHub token configured; project-mode search unavailable.
- **Reddit:** Only 4 threads returned (RSS tier only; public Reddit API returned 403). Reddit is likely much more active on this topic than captured; r/ClaudeCode and r/LocalLLaMA in particular likely have substantial discussion.
- **Coverage estimate:** ~40-50% of actual social discussion captured. Hacker News and Bluesky are well-represented. X capture is partial. Reddit, YouTube, and TikTok are significantly underrepresented.
- **MCP "Is Dead" controversy:** Bluesky referenced a "MCP Is Dead" take ([papoo.work link](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c)) but the full article was not fetched; unclear what the argument is and how the community responded.
- **Noise:** One X item (@protonnz on XPR Network blockchain agents) was off-topic and excluded from synthesis.

---

## Key Quotes

> "CLAUDE CODE JUST GOT A MASSIVE UPGRADE. Most people are using it wrong. A hidden official plugin scans your project and automatically recommends: MCP servers, Subagents, Skills, Hooks, Automations." - [@RodmanAi](https://x.com/RodmanAi/status/2061513772435718581) on X (71 likes)

> "NOBODY IS TALKING ABOUT THIS, BUT MCP JUST KILLED 90% OF SAAS INTEGRATIONS. Last week I replaced 6 internal tools at a client with 1 Claude Code agent + 4 MCP servers. Cost: $200/mo. Saved: $4,800/mo." - [@automate_archit](https://x.com/automate_archit/status/2062011593274372454) on X

> "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet." - [@franckparienti](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky [The Claude Code harness has 5 layers. Counterintuitively: switching from Sonnet to Opus matters less than activating these 5 layers on Sonnet.]

> "Permission is not a mood. It is a scoped capability. Claude Code has `deny`, `ask`, and `allow`, with deny winning first. MCP roots are `file://` boundaries the client exposes to servers... stop writing 'agent may deploy'. Write the exact gate. Everything else is permission theatre." - [@jungleskellam](https://x.com/jungleskellam/status/2061981297271349695) on X

> "Orchestration > raw model power in 2026. Claude Code + MCP makes multi-agent setups trivial - wire up Gmail/Stripe/Postgres servers, define handoffs, ship. The isolated 'chatbot' era is dead." - [@automate_archit](https://x.com/automate_archit/status/2062013383449489788) on X

> "Every enabled MCP server eats context window tokens on every message, even when you're not using it." - [@everydevai](https://bsky.app/profile/everydevai.bsky.social/post/3mmoscm2i7w2v) on Bluesky

> "Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md in Claude Code? I keep seeing these terms thrown around in tutorials and videos, but I've never seen anyone give a concrete example that makes the difference actually click." - [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/)

> "The two big extension surfaces in Claude Code are skills, which are markdown files in your repo that become custom slash commands the tool can run, and MCP servers, which are external services that connect to the tool over a standard protocol and expose new tools the model can call." - [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers)
