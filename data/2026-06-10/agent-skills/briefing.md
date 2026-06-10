# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-10
**Query type:** GENERAL
**Sources:** Reddit, X, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 7 threads | — | r/ClaudeCode, r/ClaudeAI, r/ClaudeWorkflows |
| X/Twitter | 15 posts | 1,125 likes, 176 reposts | Top voice: @_vmlops (592 likes) |
| Hacker News | 27 stories | 2,874 points, 1,579 comments | Highest engagement source |
| Bluesky | 14 posts | 94 likes, 6 reposts | French-language coverage notable |
| Web | 14 pages | — | via WebSearch; github.com, tonsofskills.com, buildwithclaude.com |

---

## Synthesized Findings

### 1. The 5-Layer Architecture Has Become the Canonical Mental Model

The community has converged on a clear conceptual stack for extending Claude Code: CLAUDE.md → hooks → skills → plugins → MCP servers. French developer [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) captured the counterintuitive key insight: "le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (switching from Sonnet to Opus gives less improvement than activating these 5 layers on Sonnet). This mental model was codified in two high-engagement pieces: [arps18's "Claude Code as a Daily Driver"](https://arps18.github.io/posts/claude-code-mastery/) (451 pts, 254 cmt on HN) and [r/ClaudeWorkflows' Practical Guide](https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/) (rated workflow value 85/100). The official [Claude Code docs](https://code.claude.com/docs/en/plugins) define plugins as the packaging layer - bundling skills, agents, hooks, MCP servers, LSP servers, and monitors into single-installable units.

### 2. MCP Has Reached Infrastructure Scale - and Microsoft Is All In

The Model Context Protocol ecosystem has grown from a 2024 Anthropic proposal to what practitioners now call "USB for AI." [@_vmlops](https://x.com/_vmlops/status/2063916937055494571) (592 likes, 120 reposts) announced Microsoft open-sourced a complete MCP course: "11 modules from zero to production, hands-on labs in python, typescript, java, rust, c# and javascript, covers mcp servers, clients, security, oauth2, azure integration, a 13-lab capstone with real postgresql + vector search." The [MCP server count](https://www.qcode.cc/mcp-servers-ecosystem-2026) hit 800+ in the official registry in April 2026, with estimates of 13,000+ total servers running including community and private deployments. Key adopters now include Anthropic, OpenAI, Google DeepMind, Microsoft, Salesforce, Block, Cloudflare, and Replit. Claude Code, Codex, Cursor, and Gemini CLI all support MCP natively. The consensus "essential trio" for developers: GitHub, Brave Search, and Playwright MCP servers.

### 3. Marketplace Fragmentation: At Least 7 Competing Registries

The plugin/skill distribution layer is fragmenting fast. Active marketplaces as of June 2026:

- **[tonsofskills.com](https://tonsofskills.com/)** - 2,753 skills across 430 plugins, 53,237 downloads, npm-based ccpi CLI
- **[buildwithclaude.com](https://buildwithclaude.com/)** - 515+ extensions across Claude.ai, Claude Code, and Claude API
- **[claudemarketplaces.com](https://claudemarketplaces.com/)** - community-curated directory updated daily from GitHub
- **[skills.2389.ai](https://skills.2389.ai/)** - 2389 Research open-source plugins, installable via `npx skills add`
- **AITMPL** ([@Oluwaphilemon1](https://x.com/Oluwaphilemon1/status/2064345893441097767), 85 likes) - 600+ AI agents, skills, commands, hooks, MCPs in one command
- **[CodeGuilds](https://codeguilds.dev)** - community registry launched June 1
- **[Capafy](https://x.com/Capafyai/status/2064626305279328371)** - skill-based marketplace where skills earn per-run revenue

[@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) (11 likes) noted the consolidation potential: "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

Anthropic's official plugin directory launched in March 2026 as part of a rapid product cadence. Per [@olly_Emmanuel](https://x.com/olly_Emmanuel/status/2064618870350983431): "Feb: model upgrades + PC + Office integrations + plugins; Mar: Memory, marketplace, 1M context; Apr: Opus 4.7, Managed Agents, Routines; May: Dynamic workflows, Agent View; Jun: Claude Fable 5, Mythos 5."

### 4. Security Is the Ecosystem's Emerging Crisis

As skills gain code execution capabilities, security warnings are escalating. [@CertiK](https://x.com/CertiK/status/2064610594074800308) (27 likes, 6 reposts, June 10): "Claude Skills can execute code with access to files, networks, and environment variables, making pre-execution security checks increasingly important." A Bindfort supply chain scan found ["Official MCP servers ship known-vulnerable dependencies at install time"](https://bindfort.com/research/mcp-supply-chain-scan). The community has responded with multiple security tooling launches in May-June 2026:

- [mcpaudit](https://github.com/allenwu-blip/mcpaudit) - static security scanner for MCP servers
- [mcp-safeguard](https://github.com/SyedAnas01/mcp-safeguard) - open-source security scanner
- [AgentSploit](https://github.com/agentsploit/agentsploit) - described as "Burp Suite for AI Agents and MCP Servers"
- [skill-flare-discover](https://github.com/Edward0l1/skill-flare-discover) - skill finder with security labels and prompt injection scanning
- CertiK's Skill Security Check API with marketplace review gates

The [Azure SRE Agent Plugin Marketplace](https://sre.azure.com/docs/capabilities/plugin-marketplace) uses SHA-256 content hashing to detect upstream skill changes - a pattern likely to spread.

### 5. Dynamic Workflows Launch + Microsoft License Controversy

Anthropic's ["Dynamic Workflows in Claude Code"](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) (200 pts, 135 cmt on HN, May 28) was a significant product announcement. The same week brought the biggest controversy of the period: [Microsoft started canceling Claude Code licenses](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) (493 pts, 466 cmt on HN, May 22) - the highest-engagement story in this research window. Simultaneously, Microsoft announced Scout, an autonomous AI agent built on OpenClaw (94 pts, 87 cmt), and open-sourced the complete MCP playbook. The Microsoft-Anthropic relationship appears simultaneously competitive and collaborative.

### 6. Specialized Skill Niches Are Proliferating

Community skill development has moved past generic productivity into specialized verticals:

- **Reasoning skills**: [@DanKornas](https://x.com/DanKornas/status/2064452712436048140) (92 likes) launched "Claude Code Thinking Skills" - 39 mental-model and critical-thinking skills using thinking-model-router plus named frameworks (first principles, Bayesian reasoning, systems thinking)
- **Deliberate skill development**: [DrCatHicks/learning-opportunities](https://github.com/DrCatHicks/learning-opportunities) (253 pts, 50 cmt HN, May 14) - a skill for teaching itself to improve
- **Multi-agent orchestration**: [Claude Orchestra](https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/) (workflow value 90/100, r/ClaudeWorkflows) - open-source system for organizing Claude Code Skills, Agents, and MCP Servers
- **DevSecOps**: 42Crunch integration for "autonomous, end-to-end Agentic DevSecOps" (per [@brunopedro.com](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z))
- **Token efficiency**: French blogger [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) (8 likes) highlights a skill that "cuts 63% of output tokens"
- **Monetization via skills**: [@adiix_official](https://x.com/adiix_official/status/2064017905730167077) (289 likes): "HOW THREE MCP SERVERS MAKE ME $3,800 A WEEK"

### 7. Cross-Agent Portability Is Normalizing

Skills are no longer Claude-only. The [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) repository targets 13 coding agents: Claude Code, Codex, Gemini CLI, Cursor, and 8 more. [tonsofskills.com](https://tonsofskills.com/) notes Cowork compatibility. Skill management tools like [skillforge](https://github.com/yvzhou1111/skillforge) and [skills-router](https://github.com/the-long-ride/skill-forge) explicitly support "any AI coding agent." The [Agent Skills API on platform.claude.com](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) and the [agentskills.io standard](https://github.com/anthropics/skills) are pushing toward an interoperable skill ecosystem that works across harnesses.

### 8. Real-World Practitioner Testimony Is Accumulating

First-person adoption stories are hitting with increasing specificity. A [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tvpu5p/a_year_building_real_client_sites_with_claude/) poster building production client sites: "I ignored agents and skills until a couple months ago. Big mistake." A [solo SaaS founder on r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) running agensi.io (an AI agent skills marketplace) achieved 1.5M impressions and 12.9K clicks in 3 months with Claude as their entire team. [@KudbeeX](https://x.com/KudbeeX/status/2064646859696611698) is using skill packages to turn coding agents into "10-person dev teams with strict shift handoffs."

---

## Cross-Source Patterns

**Pattern 1: Plugin/skill distribution is converging on git-repo-backed registries**
- Appeared on: HN (multiple Show HN posts), X, Reddit, Web
- The plugin marketplace format (a git repo with marketplace.json that Claude Code subscribes to via `/plugin marketplace add owner/repo`) is becoming the standard distribution unit. Multiple independent launches this month: CodeGuilds, GitOps-style registry, Web Speed registry, NPM-style MCP Registry. Key quote from [Azure SRE docs](https://sre.azure.com/docs/capabilities/plugin-marketplace): "MCP plugins auto-configure as connectors with pre-filled settings."

**Pattern 2: Security tooling is lagging the ecosystem by 6-12 months**
- Appeared on: X (@CertiK), HN (bindfort, mcpaudit, mcp-safeguard, agentsploit), Bluesky
- Five distinct security tools launched in the research window specifically for skill/MCP security. The problem is structural: skills execute code and MCP servers ship vulnerable deps. CertiK is trying to build a marketplace-integrated security gate. No major registry has adopted mandatory security scanning yet.

**Pattern 3: French developer community is an early-adopter signal**
- Appeared on: Bluesky (multiple French posts), no other platform
- [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) and [@humancoders.com](https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p) both published "top 13 skills of 2026" breakdowns in French, suggesting the ecosystem is reaching an internationally active practitioner base.

**Pattern 4: Skill monetization models are being attempted**
- Appeared on: X (@Capafyai, @adiix_official), Reddit (agensi.io case study)
- Multiple monetization models: per-run fees (Capafy), MCP server income claims (@adiix_official, 289 likes), skills marketplace with 1,500+ registered users (agensi.io). None are proven at scale yet but the thesis is being tested publicly.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | A year+ building real client sites with Claude Code | — | — | "I ignored agents and skills until a couple months ago. Big mistake." | https://www.reddit.com/r/ClaudeCode/comments/1tvpu5p/a_year_building_real_client_sites_with_claude/ |
| r/ClaudeWorkflows | Claude Orchestra: Open-Source System to Organize Claude Code Skills, Agents, and MCP Servers | — | — | Workflow value: 90/100 | https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/ |
| r/ClaudeWorkflows | Practical Guide to Claude Code Components: CLAUDE.md, Skills, Hooks, Plugins, and AGENTS.md | — | — | Workflow value: 85/100, confidence 0.95 | https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/ |
| r/ClaudeAI | I made a plugin that turns your projects into clickable dock apps | — | — | "just click an icon and the app opens" | https://www.reddit.com/r/ClaudeAI/comments/1tsx85s/i_made_a_plugin_that_turns_your_projects_into/ |
| r/ClaudeAI | 100 Tips & Tricks for Building Your Own Personal AI Agent | — | — | "6 weeks, no sleep, two environments, one agent that actually works" | https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/ |
| r/SaaS | 1.5M impressions, 12.9K clicks in 3 months. My entire SEO team is Claude. | — | — | "I'm a solo non-technical founder running a marketplace for AI agent skills" | https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @_vmlops | MICROSOFT OPEN-SOURCED THE COMPLETE MCP PLAYBOOK. Every ai engineer needs to understand model context protocol in 2026 | 592 | 120 | https://x.com/_vmlops/status/2063916937055494571 |
| @adiix_official | HOW THREE MCP SERVERS MAKE ME $3,800 A WEEK | 289 | 19 | https://x.com/adiix_official/status/2064017905730167077 |
| @DanKornas | Claude Code Thinking Skills is a library of 39 mental-model and critical-thinking skills | 92 | 18 | https://x.com/DanKornas/status/2064452712436048140 |
| @Oluwaphilemon1 | Claude Code now has its own open-source template marketplace. AITMPL gives developers instant access to 600+ AI agents, skills | 85 | 9 | https://x.com/Oluwaphilemon1/status/2064345893441097767 |
| @CertiK | Claude Skills can execute code with access to files, networks, and environment variables, making pre-execution security checks increasingly important | 27 | 6 | https://x.com/CertiK/status/2064610594074800308 |
| @Hive_Intel | Give Claude Access to Every Blockchain (MCP Guide) | 11 | — | https://x.com/Hive_Intel/status/2063929092702146815 |
| @appwrite | The Appwrite plugin is now available in the official Claude marketplace | 10 | 1 | https://x.com/appwrite/status/2064273389158903850 |
| @Capafyai | Capafy is the Skill-based Agent Marketplace — where your Skill runs online as a product and earns every time someone uses it | 3 | 2 | https://x.com/Capafyai/status/2064626305279328371 |
| @Gitbank_io | Gitbank MCP is Now Live in Cursor | 5 | 1 | https://x.com/Gitbank_io/status/2064660730339869149 |
| @olly_Emmanuel | GM sr, every new Claude launch since the beginning of 2026 | 0 | — | https://x.com/olly_Emmanuel/status/2064618870350983431 |
| @KudbeeX | skill packages I'm using: Claude Code → /plugin marketplace add anthropics/skills then install crewAI skills | 0 | — | https://x.com/KudbeeX/status/2064646859696611698 |
| @SomebodyHadSay | Anthropic Academy launched March 2026. 17 courses including MCP Servers | 0 | — | https://x.com/SomebodyHadSay/status/2064396459672264801 |
| @ChatgptAIskill | /plugin marketplace add anthropics/skills; /plugin install example-skills@anthropic-agent-skills | 1 | — | https://x.com/ChatgptAIskill/status/2064633930473738431 |
| @HeyAmit_ | Introduction to Model Context Protocol (MCP): connect Claude to external tools | 6 | — | https://x.com/HeyAmit_/status/2063950510575804692 |
| @nagarjuncreates | Master Claude Code: The Complete Guide for Everyone | 4 | — | https://x.com/nagarjuncreates/status/2063781636940914750 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad |
| prakashqwerty | AI Agent Guidelines for CS336 at Stanford | 502 | 153 | — | https://github.com/stanford-cs336/assignment1-basics/blob/main/CLAUDE.md |
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| Wirbelwind | Continue? Y/N: 60-second game about AI agent permission fatigue | 386 | 162 | — | https://llmgame.scalex.dev |
| adamthegoalie | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | https://github.com/DrCatHicks/learning-opportunities |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| EvanZhouDev | Microsoft announces Scout, an autonomous AI agent built on OpenClaw | 94 | 87 | — | https://www.computerworld.com/article/4180103/microsoft-unveils-scout-an-autonomous-ai-agent-built-on-openclaw.html |
| adamthegoalie | adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | — | https://github.com/adamjgmiller/adamsreview |
| martinald | New Claude Code programmatic usage restrictions | 52 | 42 | — | https://twitter.com/i/status/2054610152817619388 |
| finnworks | skills-for-humanity – 171 structured reasoning skills for Claude Code | 28 | 7 | — | https://github.com/human-avatar/skills-for-humanity |
| samuelstros | AgentCRM – Headless CRM for Claude Code | 17 | — | — | https://github.com/cluster-software/agent-crm |
| Dominic_P | Web Speed – shared web-map registry for AI agents (MCP) | 7 | 4 | — | https://www.getwebspeed.io/ |
| frizzy | GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| realsarm | Using MCP servers with Nouswise as a cited research layer | 4 | — | — | https://nouswise.com/blog/8-knowledge-management-best-practices-for-2026 |
| PengSpirit | MCP Registry – NPM-style install for MCP servers | 3 | — | — | https://mcp-registry-dh5.pages.dev |
| Bindfort | Official MCP servers ship known-vulnerable dependencies at install time | 3 | — | — | https://bindfort.com/research/mcp-supply-chain-scan |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| bengal | OAuth 2.0 framework for MCP servers | 3 | — | — | https://github.com/brooksmcmillin/mcp-authflow |
| di_desle | AgentSploit – Burp Suite for AI Agents and MCP Servers | 3 | — | — | https://github.com/agentsploit/agentsploit |
| Beko2210 | Claude Code MIT Dashboard | 9 | 2 | — | https://github.com/BEKO2210/My_Dash |
| allenwu06 | Mcpaudit – static security scanner for MCP servers | 3 | — | — | https://github.com/allenwu-blip/mcpaudit |
| Anas1371 | MCP-safeguard: open-source security scanner | 3 | — | — | https://github.com/SyedAnas01/mcp-safeguard |
| chaandannn | MCP server for cloud/software bill | 3 | — | — | https://getnable.com/ |
| sabahattink | Full Stack HQ – Claude.md and Agent Stack for Claude Code | 10 | — | — | https://github.com/sabahattink/antigravity-fullstack-hq |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character. | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @viriditax.bsky.social | when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @coolhand.bsky.social | I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @camilleroux.com | Mon top 13 des skills et plugins Claude Code qui ont marqué 2026 : → celui qui coupe 63 % des tokens de sortie | 8 | https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p |
| @jefferyharrell.bsky.social | I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @humancoders.com | Top 13 skills et plugins Claude Code qui ont marqué 2026 : audit de dette technique, réduction de tokens, best practices en prod | 5 | https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p |
| @webuyhousesusa.bsky.social | ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — free, MIT-licensed | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @brunopedro.com | 42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @mengli512.bsky.social | Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |
| @franckparienti.bsky.social | le harness de claude code en 5 couches : CLAUDE.md → hooks → skills → plugins → MCP servers; passer de sonnet à opus apporte moins que d'activer ces 5 couches | 1 | https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o |
| @github-trending-js.bsky.social | Ruflo is a multi-agent AI orchestration framework that extends Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @jcalloway.bsky.social | Claude Code MCP Server Setup Guide 2026 (With Best Tools) | 3 | https://bsky.app/profile/jcalloway.bsky.social/post/3mm5dzlxy3z2v |
| @hackernewsbot.bsky.social | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs (HN discussion) | 1 | https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| tonsofskills.com | https://tonsofskills.com/ | 2,753 skills across 430 plugins, 53,237 downloads, ccpi CLI |
| buildwithclaude.com | https://buildwithclaude.com/ | 515+ plugin extensions across Claude products |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community-curated directory, 20,300+ skills, 9,900+ MCP servers |
| skills.2389.ai | https://skills.2389.ai/ | 2389 Research open-source plugins, npx install |
| developertoolkit.ai | https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/ | MCP setup guide, Sentry/GitHub/DB/Jira from single session |
| sre.azure.com | https://sre.azure.com/docs/capabilities/plugin-marketplace | Azure SRE Agent marketplace with SHA-256 skill hashing |
| qcode.cc | https://www.qcode.cc/mcp-servers-ecosystem-2026 | 13,000+ MCP servers, 800+ official registry, adoption map |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Agent Skills official API docs |
| code.claude.com | https://code.claude.com/docs/en/plugins | Official plugin system docs |
| code.claude.com | https://code.claude.com/docs/en/discover-plugins | Plugin discovery and marketplace docs |
| bindfort.com | https://bindfort.com/research/mcp-supply-chain-scan | MCP supply chain vulnerability scan |
| github.com/Edward0l1 | https://github.com/Edward0l1/skill-flare-discover | Multi-registry skill finder with security labels |
| github.com/yvzhou1111 | https://github.com/yvzhou1111/skillforge | Skill dependency butler for any coding agent |
| github.com/anand-92 | https://github.com/anand-92/skills-registry | Personal GitHub registry for AI agent skills |

---

## Stats Block

```
├─ 🟠 Reddit: 7 threads
├─ 🔵 X: 15 posts │ 1,125 likes │ 176 reposts
├─ 🟡 HN: 27 stories │ 2,874 points │ 1,579 comments
├─ 🦋 Bluesky: 14 posts │ 94 likes │ 6 reposts
├─ 🌐 Web: 14 pages - developertoolkit.ai, skills.2389.ai, GitHub, tonsofskills.com, buildwithclaude.com, sre.azure.com
└─ 🗣️ Top voices: @_vmlops, @adiix_official, @DanKornas │ r/ClaudeAI, r/ClaudeWorkflows, r/ClaudeCode
```

---

## Data Gaps

- **YouTube: 0 results** - The search query was too long for yt-dlp to resolve; SC YouTube returned HTTP 402. YouTube likely has significant tutorial/review content for MCP and Claude Code plugins that is missing from this briefing.
- **TikTok: 0 results** - SC key returned 0 results for this topic (likely hashtag or query format issue). Missing viral/demo content.
- **Instagram: 0 results** - SC Instagram returned 0 despite key being configured; multi-token query issue noted in engine output.
- **GitHub: 0 results** - No GitHub token configured; project-mode and user-mode searches unavailable. Star counts cited in the briefing come from WebSearch results, not live API data.
- **Reddit: low coverage (7 threads)** - Reddit public API returned 403. Only scraped via RSS and ScrapeCreators fallback; many r/ClaudeCode and r/LocalLLaMA threads likely missed.
- **Estimated coverage**: ~55% of likely available signal. HN and X are well-covered; YouTube, TikTok, Reddit main feeds, and GitHub are missing.

---

## Key Quotes

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "le contre-intuitif : passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (switching from Sonnet to Opus gives less improvement than activating the 5 architecture layers on Sonnet) - [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "I ignored agents and skills until a couple months ago. Big mistake." - [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tvpu5p/a_year_building_real_client_sites_with_claude/) practitioner with 1+ year of production use

> "MICROSOFT OPEN-SOURCED THE COMPLETE MCP PLAYBOOK. Every ai engineer needs to understand model context protocol in 2026." - [@_vmlops](https://x.com/_vmlops/status/2063916937055494571) on X (592 likes)

> "Claude Skills can execute code with access to files, networks, and environment variables, making pre-execution security checks increasingly important." - [@CertiK](https://x.com/CertiK/status/2064610594074800308) on X

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "Official MCP servers ship known-vulnerable dependencies at install time." - [Bindfort research](https://bindfort.com/research/mcp-supply-chain-scan) on HN

> "I'm a solo non-technical founder running a marketplace for AI agent skills. No engineering team, no marketing team, no SEO agency. Just me and Claude. 1.54M impressions in 3 months." - [r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) agensi.io founder
