# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-04
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 12 threads | upvotes N/A (public API 403) | r/ClaudeCode, r/ClaudeAI, r/AIAgentsInAction, r/ClaudeWorkflows |
| X/Twitter | 17 posts | 1,026 likes, 280 reposts | Viral resource-list threads dominating |
| Hacker News | 20 stories | 1,140 points, 523 comments | Top story: "Claude Code as a Daily Driver" (447pts) |
| Bluesky | 13 posts | 49 likes, 2 reposts | MCP news aggregators + dev build-in-public |
| Web | 29 pages | — | Engine (9) + WebSearch supplements (20) |

---

## Synthesized Findings

### 1. The Five-Layer Claude Code Architecture Is Finally Clicking for Developers

The mental model crystallizing across Reddit, Bluesky, and HN this month is a five-layer stack: CLAUDE.md → hooks → skills → plugins → MCP servers. [François Parienti on Bluesky](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) put it most succinctly: "le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" - switching from Sonnet to Opus brings less than activating all 5 layers on Sonnet. The [r/ClaudeCode confusion thread](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) from May 24 asking "Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md?" hit a nerve - it reflects genuine developer confusion that multiple guides now attempt to resolve. The canonical answer per [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins): skills = instructions (what to do), plugins = distribution format (how to ship skills), MCP = connectivity (how to reach external systems). A Spanish post by [@josesilesdata](https://x.com/josesilesdata/status/2062464172063957485) went viral (June 4) making the same point: "La mayoría usa Claude como si fuera ChatGPT" - most people use Claude like ChatGPT and never reach layers 3-5.

The Anthropic blog post ["Dynamic Workflows in Claude Code"](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) (HN: 199 pts, 135 comments) and ["Claude Code as a Daily Driver"](https://arps18.github.io/posts/claude-code-mastery/) (HN: 447 pts, 252 comments) are the two highest-engagement pieces driving this architecture understanding. The daily-driver post covers CLAUDE.md, skills, subagents, plugins, and MCPs as one coherent system. [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp) further cements the pattern: "prefer MCP tools over Bash when the integration will be used across sessions."

**Platforms:** Reddit, Bluesky, Hacker News, X, Web

---

### 2. The npm-shaped Hole in AI Tooling Discovery

The most-discussed structural problem in the ecosystem right now is skill discovery and team sharing. The [r/ClaudeCode thread "There's an npm-shaped hole in the AI tooling stack"](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/) from May 15 captures the problem precisely: "one person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup." Git + CLAUDE.md helps for single repos; Claude Code plugins and vendor marketplaces solve vendor-specific distribution but not cross-team, cross-repo sharing of custom configurations.

Several competing solutions have emerged this month. [CodeGuilds](https://codeguilds.dev) launched on Hacker News (June 1, 3pts) as a community registry specifically for Claude Code (skills, agents, MCP servers). A developer on [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) (May 26) shipped their own searchable plugin directory because "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos." Vercel Labs' [`npx skills`](https://dev.to/toyama0919/managing-ai-agent-skills-with-npx-skills-a-practical-guide-2an8) package manager uses GitHub as its registry (npm-style but for agent behaviors). [termdock.com](https://www.termdock.com/en/blog/cross-agent-skills-new-npm) declared "Cross-Agent Skills: Why They're the New npm" - framing SKILL.md as the `package.json` analog for agent capabilities. By March 2026, the ecosystem crossed 351,000 published skills across three competing marketplaces.

**Platforms:** Reddit, Hacker News, Web

---

### 3. Official Marketplace Explosion - Numbers Are Staggering

Anthropic's official Claude Code plugin directory ([anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)) hit 29,000 GitHub stars in under 7 months per [@digitalbrain01](https://x.com/digitalbrain01/status/2062309821634715732) (June 3). The official directory now catalogs 55+ curated plugins. Beyond official channels, the community ecosystem has scaled dramatically: [claudemarketplaces.com](https://claudemarketplaces.com/) tracks 20,400+ skills, 2,500+ marketplaces, and 11,000+ MCP servers, updated daily from GitHub. [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) aggregates 425 plugins, 2,810 skills, and 200 agents with a `ccpi` CLI package manager. [hesreallyhim/awesome-claude-code](https://reddit.com/r/ClaudeCode) has accumulated ~36.8k stars as the canonical hand-curated master index.

The standout story from this window: a solo developer won the Anthropic hackathon ($15,000 prize) and open-sourced his stack, which the [r/AIAgentsInAction thread](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/) reports hit 153,000+ GitHub stars. The repo (Everything Claude Code / ECC) includes 38 specialized agents, 156 skills, 72 commands, and a 1,282-test security scanner. [@Dharmikpawar31](https://x.com/Dharmikpawar31/status/2053418519816216760) captured the attention economy around this: "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack. That's your edge." (95 likes, 41 reposts). Multiple nearly-identical "20/100 Claude Repos that will change your life" threads went viral on X this month from [@HeyZaraKhan](https://x.com/HeyZaraKhan/status/2057161326548377891) (217 likes), [@Dharmikpawar31](https://x.com/Dharmikpawar31/status/2057015766847995938) (144 likes), and others - a recurring content pattern.

**Platforms:** X/Twitter, Reddit, Hacker News, Web

---

### 4. MCP Ecosystem Matures at Scale - 13,000+ Servers, 97M Downloads

The MCP server ecosystem is past the early-adopter phase. [QCode.cc](https://www.qcode.cc/mcp-servers-ecosystem-2026) reports 13,000+ total community servers with the official registry at 800+; tracked server count crossed 9,400 by mid-April 2026, up from 6,800 at year-end 2025 (+38% in four months). The Python and TypeScript SDKs see 97 million monthly downloads per [Digital Applied's H1 2026 retrospective](https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points). Anthropic donated MCP to the Linux Foundation under the Agentic AI Foundation in December 2025, making it vendor-neutral.

Developer commentary on Bluesky reflects real workflow integration: [@yobyot.bsky.air11.social](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c) declared "Using Claude Code with the new AWS MCP server has changed my life. Writing CloudFormation templates has never been more fun." [@jamiedavenport.bsky.social](https://bsky.app/profile/jamiedavenport.bsky.social/post/3mn3ggi4m7s2e) reported shipping a full Claude Code + Plain MCP integration within 24 hours. [Bluesky's papoo7](https://bsky.app/profile/papoo7.bsky.social/post/3mmuot5cnlw2b) highlighted an MCP server enabling Claude Code to work inside dev containers. [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) shared Semble - a code search MCP tool consuming ~98% fewer tokens than grep+read, integrating with Claude Code, Cursor, Codex, and OpenCode as an MCP server. [@exploraX_](https://x.com/exploraX_/status/2062448236439155173) curated "50 MCP Servers That Give Claude, Codex & Gemini Superpowers" (21 likes). HN saw a [Show HN for an 86-tool MCP server](https://github.com/openclaw-easy/ViralMint) driving an AI video generator and a [Blender MCP integration](https://hydroxide.dev/articles/blender-mcp-claude-code/). [@render87.bsky.social](https://bsky.app/profile/render87.bsky.social/post/3mmtgqvjuan2g) shipped a 37-tool DNS + email security MCP server.

A credibility-challenging signal on Bluesky: [papoo7's "Why This 'MCP Is Dead' Take Matters for Claude Code Users"](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c) (May 31) linked to a [papoo.work doc](https://papoo.work/doc/b222f7b5bcd0702c) arguing the "MCP Is Dead" narrative matters even if wrong. Given 97M downloads/month, the "dead" argument is contrarian positioning rather than data-backed.

**Platforms:** Bluesky, X/Twitter, Hacker News, Web

---

### 5. Cross-Agent Portability - SKILL.md as Universal Standard

The most structurally significant shift this month is the convergence around SKILL.md as a cross-agent skill format. [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) publishes skills under the [agentskills.io](https://agentskills.io) open standard explicitly designed to be "portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents." [awesome-skills.com](https://awesome-skills.com/) lists 1,234+ skills working across Claude Code, Cursor, Gemini CLI, Codex CLI, and Antigravity IDE. [claude-plugins.dev](https://claude-plugins.dev/skills) aggregates skills with cross-agent compatibility filters.

Grok Build (X's new terminal agent) listed MCP server support in its feature set per [@rammcodes](https://x.com/rammcodes/status/2062456080878436650): "similar to Claude Code and Codex CLI... supports MCP servers." The [modelcontextprotocol.io official docs](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills) now covers building with agent skills and the MCPB bundling format (combining an MCP server config + skill files as an alternative to the plugin model). The [tech-leads-club/agent-skills](https://github.com/tech-leads-club/agent-skills) registry positions itself explicitly as vendor-neutral: "extend Antigravity, Claude Code, Cursor, Copilot and more."

The r/ClaudeCode vibe-coding guide mentioned [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) (~36.8k stars) and [jqueryscript/awesome-claude-code](https://github.com/jqueryscript/awesome-claude-code) as the "yellow pages" - master indexes pointing at everything else. The [r/AIAgentsInAction full ecosystem thread](https://www.reddit.com/r/AIAgentsInAction/comments/1tb3yoe/the_full_claude_ecosystem_1200_mcp_servers_400/) published six GitHub reference files covering 1,200+ MCP servers, 400+ plugins, 25+ agent frameworks.

**Platforms:** Reddit, X/Twitter, Web, Hacker News

---

### 6. Security Risks Are Real and Growing

The ecosystem's growth is attracting adversarial attention. [@lyrie_ai on X](https://x.com/lyrie_ai/status/2061723592446910921) (June 2) reported: "February 2026 demonstrated this at scale: 1,184 malicious skills were found poisoning an AI agent marketplace before detection. Claude Code was separately disclosed as vulnerable to RCE via poisoned repository configuration files." [@verialabs on X](https://x.com/verialabs/status/1970519527646716346) disclosed critical RCE vulnerabilities in popular AI coding tools including Claude Code and Gemini CLI related to OAuth MCP authentication - the tools don't validate authorization URLs from servers. The [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) project positions itself as a solution: enterprise MCP governance with OAuth, dynamic tool discovery, Keycloak/Entra integration. [tech-leads-club/agent-skills](https://github.com/tech-leads-club/agent-skills) markets itself as the "secure, validated skill registry" in direct contrast to unvetted community repositories.

**Platforms:** X/Twitter, Web

---

### 7. Builders Sharing Architecture Hard-Won Lessons

The community is moving from "how do I install X" to "how did you architect Y." A r/ClaudeCode developer shared [5 months of plugin-architecture learnings](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/) from building a WordPress MCP server: started with Claude Desktop, expanded to Claude Code, then Cursor and Codex CLI, ultimately shipped a Cowork plugin to Anthropic's marketplace. The key lesson: "the Cowork plugin format is genuinely underrated for multi-editor compatibility." HN's ["A Claude Code and Codex Skill for Deliberate Skill Development"](https://github.com/DrCatHicks/learning-opportunities) (253 pts, 50 comments) takes a meta-learning angle - building skills that improve how you build other skills. The [r/ClaudeWorkflows Advanced workflow thread](https://www.reddit.com/r/ClaudeWorkflows/comments/1t5w9db/workflow_advanced_claude_code_gitbased_plugin/) describes a git-based plugin marketplace with context-aware codebase mapper and hooks (rated 88/100 workflow value). HN's ["adamsreview"](https://github.com/adamjgmiller/adamsreview) Show HN (85 pts, 55 comments) demonstrates a multi-agent PR review skill.

A freelancer perspective: [@automate_archit](https://x.com/automate_archit/status/2062375337724699133) noted "Closed 6 client projects last quarter using just Claude Code + MCP servers. No certs asked, only outcomes. Market rewards results over credentials in this cycle." The [Academic Research Skills for Claude Code](https://github.com/Imbad0202/academic-research-skills) HN post (82 pts, 25 comments) showed skills being adapted for non-coding domains.

**Platforms:** Reddit, Hacker News, X/Twitter

---

## Cross-Source Patterns

**Pattern 1: Discovery Is Broken - Everyone Is Building Their Own Index**
- Signal: Multiple independent developers shipping searchable directories, curated lists, "resource bibles" in the same 30-day window
- Platforms: Reddit (r/ClaudeAI directory thread, r/ClaudeCode vibe-coding guide), X (viral "X repos that will change your life" posts), Hacker News (CodeGuilds, adamsreview)
- Key quotes: "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos" - r/ClaudeAI; "Most people still haven't discovered this stack" - [@Dharmikpawar31](https://x.com/Dharmikpawar31/status/2053418519816216760)

**Pattern 2: Skills/MCP/Plugins Taxonomy Confusion Is Universal**
- Signal: Confusion thread on r/ClaudeCode is the second-highest discussion; multiple explainer posts across all platforms; official docs frequently cited
- Platforms: Reddit, Bluesky (5-layer framework post), Web (morphllm.com, explainx.ai, claudefolio.com guides)
- Key quotes: "le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" - [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o)

**Pattern 3: MCP Servers as the Real Productivity Unlock**
- Signal: Specific tool integrations (AWS, Ableton, dev containers, DNS, Plain, Semble) shipping in this window and generating organic community posts - not hype posts but concrete use cases
- Platforms: Bluesky, X, HN (86-tool video gen, Blender MCP, Better Design 28 Shadcn systems)
- Key quotes: "Using Claude Code with the new AWS MCP server has changed my life" - [@yobyot.bsky.air11.social](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c)

**Pattern 4: Security Is the Ecosystem's Achilles Heel**
- Signal: 1,184 malicious skills in marketplace (Feb 2026), RCE via OAuth MCP auth, targeted repos raising flags
- Platforms: X (lyrie_ai, verialabs), Web (agentic-community/mcp-gateway-registry)
- Key quotes: "1,184 malicious skills were found poisoning an AI agent marketplace before detection" - [@lyrie_ai](https://x.com/lyrie_ai/status/2061723592446910921)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | There's an npm-shaped hole in the AI tooling stack | N/A | N/A | "one person builds up a vault of skills...the rest of the team can't replicate the setup" | [link](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/) |
| r/ClaudeAI | I built a searchable directory for Claude Code plugins | N/A | N/A | "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) |
| r/ClaudeCode | Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md and agents.md? | N/A | N/A | "Everyone says: just create a skill for that — but when I dig deeper, the explanations are vague" | [link](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) |
| r/AIAgentsInAction | The Full Claude Ecosystem: 1,200+ MCP Servers, 400+ Plugins, 25+ Agent Frameworks | N/A | N/A | "six reference files on GitHub, verified April 2026" | [link](https://www.reddit.com/r/AIAgentsInAction/comments/1tb3yoe/the_full_claude_ecosystem_1200_mcp_servers_400/) |
| r/AIAgentsInAction | This guy Won the Anthropic Hackathon Solo — 38 Agents, 156 Skills, 1,282 Security Tests | N/A | N/A | "Install selectively: /plugin marketplace add affaan-m/everything-claude-code" | [link](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/) |
| r/ClaudeCode | Built a Cowork plugin for WordPress editing — 5 months of plugin-architecture learnings | N/A | N/A | "the Cowork plugin format is genuinely underrated for multi-editor compatibility" | [link](https://www.reddit.com/r/ClaudeCode/comments/1t99kbt/built_a_cowork_plugin_for_wordpress_editing_this/) |
| r/ClaudeCode | New in Claude Code: agent view | N/A | N/A | "Run claude agents to start dispatching multiple sessions at once" | [link](https://www.reddit.com/r/ClaudeCode/comments/1tag1kv/new_in_claude_code_agent_view/) |
| r/ClaudeCode | I let Claude Code run my Instagram + TikTok marketing. Here's the plugin | N/A | N/A | "The whole loop in one session: scrape what's actually working...generate content...post or schedule" | [link](https://www.reddit.com/r/ClaudeCode/comments/1te0jzb/i_let_claude_code_run_my_instagram_tiktok/) |
| r/ClaudeWorkflows | Advanced Claude Code: Git-based Plugin Marketplace with Context-Aware Codebase Mapper and Hooks | N/A | N/A | "Workflow value: 88/100 — managing and reusing custom AI tools" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1t5w9db/workflow_advanced_claude_code_gitbased_plugin/) |
| r/ClaudeCode | Just a Quick-start guide for anyone "Vibe-Coding" | N/A | N/A | "hesreallyhim/awesome-claude-code (~36.8k stars) — The hand-curated, canonical big list" | [link](https://www.reddit.com/r/ClaudeCode/comments/1thaxok/just_a_quickstart_guide_for_anyone_vibecoding_im/) |
| r/OpenaiCodex | I tried to recreate Claude Dynamic Workflows for Codex | N/A | N/A | "ports the idea of Claude Code Dynamic Workflows" | [link](https://www.reddit.com/r/OpenaiCodex/comments/1tv0ice/i_tried_to_recreate_claude_dynamic_workflows_for/) |
| r/LLM_Infographics | Claude Code Agent Development Kit | N/A | N/A | — | [link](https://www.reddit.com/r/LLM_Infographics/comments/1t6f2in/claude_code_agent_development_kit/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Dharmikpawar31 | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack." | 95 | 41 | [link](https://x.com/Dharmikpawar31/status/2053418519816216760) |
| @HeyZaraKhan | "100 Claude Repos that will completely change your life: 1. Terminal AI coding agent 2. Ready-to-use starter apps 3. Official agent skills 4. Plugin marketplace..." | 217 | 39 | [link](https://x.com/HeyZaraKhan/status/2057161326548377891) |
| @Dharmikpawar31 | "20 Claude Repos that can completely change your life: 3. Official agent skills 4. Plugin marketplace 5. Full ecosystem..." | 144 | 60 | [link](https://x.com/Dharmikpawar31/status/2057015766847995938) |
| @InduTripat82427 | "10 GitHub repositories so good they shouldn't be free. 1. TradingAgents — A full team of AI analysts..." | 425 | 109 | [link](https://x.com/InduTripat82427/status/2062136258030350758) |
| @lyrie_ai | "1,184 malicious skills were found poisoning an AI agent marketplace before detection. Claude Code was separately disclosed as vulnerable to RCE via poisoned repository configuration files." | N/A | N/A | [link](https://x.com/lyrie_ai/status/2061723592446910921) |
| @digitalbrain01 | "Anthropic's official Claude Code plugin directory hits 29,000 GitHub stars in under 7 months — open marketplace for slash commands, agents, skills and MCP servers" | 1 | 1 | [link](https://x.com/digitalbrain01/status/2062309821634715732) |
| @exploraX_ | "50 MCP Servers That Give Claude, Codex & Gemini Superpowers (Free Guide)" | 21 | 3 | [link](https://x.com/exploraX_/status/2062448236439155173) |
| @josesilesdata | "La mayoría usa Claude como si fuera ChatGPT... Pero Claude tiene varias capas: 1. Chat 2. Cowork 3. Skills + plugins 4. Código + computadora" | 4 | 1 | [link](https://x.com/josesilesdata/status/2062464172063957485) |
| @automate_archit | "Closed 6 client projects last quarter using just Claude Code + MCP servers. No certs asked, only outcomes." | 1 | 0 | [link](https://x.com/automate_archit/status/2062375337724699133) |
| @rammcodes | "Grok Build is a coding agent that runs directly inside your terminal, similar to Claude Code and Codex CLI... supports MCP servers → spawns parallel subagents" | 4 | 1 | [link](https://x.com/rammcodes/status/2062456080878436650) |
| @Techjunkie_Aman | "LibreChat is starting to feel less like an AI chatbot and more like a full open-source AI ecosystem... MCP tools... agent marketplace" | 33 | 5 | [link](https://x.com/Techjunkie_Aman/status/2055361267788054693) |
| @smratitiwa86867 | "20 Claude Repos that can completely change your life" | 56 | 16 | [link](https://x.com/smratitiwa86867/status/2056207065564303712) |
| @unbeatenkid | "If you're serious about AI agents in 2026, this rabbit hole is worth exploring. 20 Claude & AI repos" | 2 | 0 | [link](https://x.com/unbeatenkid/status/2056812133892141212) |
| @_itsjustshubh | "@mcbaldwin311 building claude code plugins and MCP servers while full-time at Big Tech. always up to connect with people actually shipping things" | 1 | 0 | [link](https://x.com/_itsjustshubh/status/2062313325812170827) |
| @Jolliai | "Step 2: Wire up your MCP servers so Claude Code has real context. I prompted: 'scaffold an Expo app from my Stitch design and connect Supabase.'" | 0 | 0 | [link](https://x.com/Jolliai/status/2062158038791008608) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 447 | 252 | — | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| — | Dynamic Workflows in Claude Code (Anthropic blog) | 199 | 135 | — | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| DrCatHicks | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | [link](https://github.com/DrCatHicks/learning-opportunities) |
| adamjgmiller | Show HN: adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | — | [link](https://github.com/adamjgmiller/adamsreview) |
| Imbad0202 | Academic Research Skills for Claude Code | 82 | 25 | — | [link](https://github.com/Imbad0202/academic-research-skills) |
| — | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | [link](https://codeguilds.dev) |
| openclaw-easy | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | [link](https://github.com/openclaw-easy/ViralMint) |
| marvkr | Show HN: Better Design – 28 Shadcn design systems (OSS, MCP: Cursor/Claude Code) | 13 | 0 | — | [link](https://github.com/marvkr/better-design) |
| — | Claude Code and Blender MCP | 3 | 0 | — | [link](https://hydroxide.dev/articles/blender-mcp-claude-code/) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @papoo7.bsky.social | "Why This 'MCP Is Dead' Take Matters for Claude Code Users" | 3 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn67zkunm72c) |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches : CLAUDE.md → hooks → skills → plugins → MCP servers — le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" | 1 | [link](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) |
| @camilleroux.com | "Semble : un outil de recherche de code pour les agents IA qui consomme ~98% moins de tokens que grep+read... s'intègre comme serveur MCP dans Claude Code, Cursor, Codex ou OpenCode" | 11 | [link](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) |
| @happy-homhom.bsky.social | "An MCP Server That Lets Claude Code Work Inside Dev Containers" | 3 | [link](https://bsky.app/profile/happy-homhom.bsky.social/post/3mmuot5cnlw2b) |
| @jamiedavenport.bsky.social | "So many cool new features shipped in the past 24 hours but the MCP server is amazing. Here's a preview of Claude Code working directly from issues on Plain." | 6 | [link](https://bsky.app/profile/jamiedavenport.bsky.social/post/3mn3ggi4m7s2e) |
| @papoo7.bsky.social | "Claude Code Meets Ableton Live: An MCP Bridge for Music Production" | 2 | [link](https://bsky.app/profile/papoo7.bsky.social/post/3mn424xy72k2d) |
| @render87.bsky.social | "With 37 tools integrated, intodns-mcp saves time by providing exact zone-file edits in under 3 seconds. I built an MCP server for DNS + email security" | 2 | [link](https://bsky.app/profile/render87.bsky.social/post/3mmtgqvjuan2g) |
| @yobyot.bsky.air11.social | "Using #Claude Code with the new #AWS #MCP server has changed my life. Writing #CloudFormation templates has never been more fun." | 1 | [link](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c) |
| @alternativeto.net | "A new free Slack alternative for teams, with Claude Code built into every channel... Local-first sync, terminal commands, MCP support, and 2,000+ integrations" | 7 | [link](https://bsky.app/profile/alternativeto.net/post/3mndqzjlg6p2s) |
| @llms.activitypub.awakari.com | "Анатомия Claude Code... #claude-code #ai-агенты #llm #prompt-engineering #mcp" | 5 | [link](https://bsky.app/profile/llms.activitypub.awakari.com.ap.brid.gy/post/3mmwdaeacg5j2) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | 20,400+ skills, 2,500+ marketplaces, 11,000+ MCP servers directory; lists skills.sh (Vercel) as canonical discovery tool |
| code.claude.com (Discover Plugins) | https://code.claude.com/docs/en/discover-plugins | Official Anthropic docs for plugin discovery and /plugin install workflow |
| code.claude.com (MCP Quickstart) | https://code.claude.com/docs/en/mcp-quickstart | Official MCP setup guide for Claude Code |
| code.claude.com (Skills) | https://code.claude.com/docs/en/skills | Official skills extension documentation |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | "Claude Code Skills vs MCP vs Plugins: Complete Guide 2026" — canonical taxonomy |
| llmbestpractices.com (MCP skill setup) | https://llmbestpractices.com/howto/set-up-an-mcp-claude-code-skill | Step-by-step guide for registering local/remote MCP server in Claude Code |
| llmbestpractices.com (MCP integration) | https://llmbestpractices.com/ai-agents/claude-code-mcp | "Prefer MCP tools over Bash when the integration will be used across sessions" |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Skills/agents/hooks/MCP/LSP explainer by ML/security researcher |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Practical Claude Code skills and custom slash commands guide |
| qcode.cc | https://www.qcode.cc/mcp-servers-ecosystem-2026 | MCP server ecosystem scale data: 13,000+ servers, 9,400 tracked by April 2026 |
| digitalapplied.com | https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points | H1 2026 MCP adoption retrospective: 97M monthly downloads, Linux Foundation donation |
| explainx.ai | https://explainx.ai/blog/what-are-agent-skills-complete-guide | Layered architecture explanation: tools/MCP/skills for Claude Code, Cursor & MCP |
| modelcontextprotocol.io (Build with Agent Skills) | https://modelcontextprotocol.io/docs/develop/build-with-agent-skills | Official MCP docs on agent skills and MCPB bundling format |
| modelcontextprotocol/discussions #2316 | https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2316 | "Skills Over MCP Interest Group" Feb 2026 office hours — technical debate on skills vs MCP architecture |
| termdock.com | https://www.termdock.com/en/blog/cross-agent-skills-new-npm | "Cross-Agent Skills: Why They're the New npm" — SKILL.md as universal agent primitive |
| dev.to/toyama0919 | https://dev.to/toyama0919/managing-ai-agent-skills-with-npx-skills-a-practical-guide-2an8 | Guide to `npx skills` (Vercel Labs) package manager for agent behaviors |
| netresearch/claude-code-marketplace | https://github.com/netresearch/claude-code-marketplace | Cross-agent skills via agentskills.io open standard |
| tech-leads-club/agent-skills | https://github.com/tech-leads-club/agent-skills | Secure, validated skill registry across Claude Code, Cursor, Antigravity, Copilot |
| agentic-community/mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Enterprise MCP gateway with OAuth, dynamic discovery, Keycloak/Entra integration |
| awesome-skills.com | https://awesome-skills.com/ | 1,234+ cross-agent skills library for Claude Code, Cursor, Gemini CLI, Codex CLI |
| scottspence.com | https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces | Developer walkthrough on skills-to-plugin organization |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents with ccpi CLI at tonsofskills.com |
| groundy.com | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Anthropic official plugin ecosystem deep-dive |
| agensi.io | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Claude Code plugin marketplace practical guide 2026 |
| papoo.work (MCP Is Dead) | https://papoo.work/doc/b222f7b5bcd0702c | "Why This 'MCP Is Dead' Take Matters for Claude Code Users" |
| papoo.work (Dev Containers) | https://papoo.work/doc/c7f86193d8eca529 | MCP server enabling Claude Code inside dev containers |
| papoo.work (Ableton) | https://papoo.work/doc/ca9090acb1419c80 | Claude Code + Ableton Live MCP bridge for music production |
| dev.to/sahil_kat | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | MCP ecosystem integration layer analysis with key vendor list |
| hydroxide.dev | https://hydroxide.dev/articles/blender-mcp-claude-code/ | Claude Code and Blender MCP integration |

---

## Stats Block

```
├─ 🟠 Reddit: 12 threads │ upvotes N/A │ communities: r/ClaudeCode, r/ClaudeAI, r/AIAgentsInAction, r/ClaudeWorkflows
├─ 🔵 X: 17 posts │ 1,026 likes │ 280 reposts
├─ 🟢 HN: 20 stories │ 1,140 points │ 523 comments
├─ 🦋 Bluesky: 13 posts │ 49 likes │ 2 reposts
├─ 🌐 Web: 29 pages (9 engine + 20 supplemental)
└─ 🗣️ Top voices: @Dharmikpawar31, @HeyZaraKhan, @lyrie_ai │ r/ClaudeCode, r/AIAgentsInAction, r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 results** - YouTube search returned zero results (yt-dlp search and ScrapeCreators both failed for this query). This is a significant gap; Claude Code tutorial/walkthrough content is heavily represented on YouTube and likely includes skill setup and MCP configuration videos. Recommend a targeted YouTube search for "Claude Code skills plugins MCP tutorial 2026" to fill.
- **TikTok/Instagram: 0 results** - ScrapeCreators returned HTTP 402 (Payment Required) for both platforms. Likely has some creator content given the viral X posts.
- **Reddit upvotes N/A** - Reddit public API returned 403 for direct search; keyless RSS tier provided threads without engagement scores.
- **GitHub: 0 results** - No GitHub token available; project-mode search for anthropics/claude-code and anthropics/claude-plugins-official did not execute. Commit velocity, issue trends, and live star counts are missing.
- **Recency skew** - Only 29 of 71 dated items from last 7 days; the topic is mature enough that evergreen content from 2-4 weeks ago dominates. Most recent breaking signals are the CodeGuilds HN launch and the @lyrie_ai security warning.
- **"MCP Is Dead" narrative** - Bluesky linked to the papoo.work doc but the doc itself was not fully crawled. The counterargument basis is not fully documented here.
- **Approximate coverage**: 65-70% of likely discussion volume given the Reddit and YouTube gaps. High-quality signal on the HN and X vectors; lower coverage for video tutorials and community Discord threads.

---

## Key Quotes

> "There's an npm-shaped hole in the AI tooling stack... one person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup." — r/ClaudeCode ([link](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/))

> "le harness de claude code en 5 couches : CLAUDE.md → hooks → skills → plugins → MCP servers — le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" — [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "1,184 malicious skills were found poisoning an AI agent marketplace before detection. Claude Code was separately disclosed as vulnerable to RCE via poisoned repository configuration files." — [@lyrie_ai](https://x.com/lyrie_ai/status/2061723592446910921) on X

> "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack. That's your edge." — [@Dharmikpawar31](https://x.com/Dharmikpawar31/status/2053418519816216760) on X

> "Using #Claude Code with the new #AWS #MCP server has changed my life. Writing #CloudFormation templates has never been more fun." — [@yobyot.bsky.air11.social](https://bsky.app/profile/yobyot.bsky.air11.social/post/3mncxjphspc2c) on Bluesky

> "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer the questions I actually cared about: Is this maintained? What does it install? Are people actually using it?" — r/ClaudeAI ([link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/))

> "Real cert is shipping. Closed 6 client projects last quarter using just Claude Code + MCP servers. No certs asked, only outcomes. Market rewards results over credentials in this cycle." — [@automate_archit](https://x.com/automate_archit/status/2062375337724699133) on X

> "Cross-Agent Skills: Why They're the New npm" — [termdock.com](https://www.termdock.com/en/blog/cross-agent-skills-new-npm)

> "La mayoría usa Claude como si fuera ChatGPT: 'Dame 10 ideas rápido.' Y ya. Pero Claude tiene varias capas... 3. Skills + plugins. 4. Código + computadora. La diferencia no está en 'usar IA'." — [@josesilesdata](https://x.com/josesilesdata/status/2062464172063957485) on X

> "Semble consomme ~98% moins de tokens que grep+read, tourne entièrement en local sur CPU, et s'intègre comme serveur MCP dans Claude Code, Cursor, Codex ou OpenCode." — [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mmyvskxwo425) on Bluesky
