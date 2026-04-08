# Agent Skills & Claude Code Plugin Ecosystem — Daily Briefing
**Date:** 2026-04-08
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 28 posts | 587 likes, 97 reposts | Top signal: @injective 334 likes |
| Hacker News | 4 stories | 235 points, 107 comments | Cq reached 225 pts |
| Web | 48 pages | — | via WebSearch — 6 queries |

*Reddit: ScrapeCreators API returned HTTP 402; Bluesky: HTTP 403 Forbidden; YouTube/TikTok/Instagram/Polymarket: 0 results this cycle.*

---

## Synthesized Findings

### 1. The Claude Code Extension Taxonomy Crystallizes: Skills vs. MCP vs. Plugins

A clear conceptual framework has consolidated in the community over the last 30 days. Claude Code now has five distinct extension types, each with a different role: **CLAUDE.md** (always-on context injected into every session), **skills** (on-demand workflows and slash commands loaded from markdown files), **MCP servers** (live connections to external tools and APIs), **subagents** (isolated task executors Claude can spawn), and **hooks** (event-triggered automation firing on code changes, commits, etc.).

The distinction between skills and MCP servers comes up repeatedly. Per [Morph's guide](https://www.morphllm.com/claude-code-skills-mcp-plugins): skills teach Claude *how* to do things (workflows, conventions, slash commands), while MCP servers give Claude *access to* external systems. A plugin bundles all of the above into a single installable unit.

As of March 2026, the main community directory lists 150+ skills. One open-source GitHub repo — [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) — has catalogued 340 plugins and 1,367 agent skills with its own CCPI package manager, interactive tutorials, and production orchestration patterns.

Power user @elCholoCat captures where this is heading: *"we're running 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier, and a review gate that fires on every code change. claude code is basically a second brain at this point."* ([link](https://x.com/elCholoCat/status/2041581965619404880))

**Sources:** X, Web (Morph, DEV Community, Claude Code Docs, Composio, SkillsPlayground, TurboDocx)

---

### 2. MCP Protocol Reaches 400+ Servers — Faster Than Any Dev Tool in Recent Memory

MCP adoption is the defining infrastructure story. Per @DasNripanka: *"MCP hit 400+ servers on GitHub in under a year. Twelve months ago: zero. Today: the protocol every agent stack needs to be compatible with. Hermes Agent and Claude Code both shipped MCP support in Q1."* ([link](https://x.com/DasNripanka/status/2040852306170888431))

Practitioners are running multi-server stacks as a matter of course. @ModernGrindTech: *"the MCP server pattern is where everything converges. I run chrome devtools, neon postgres, notion, and discord all as MCP servers wired into Claude Code. the agent can browse, query databases, read docs, and send messages — no switching between tools."* ([link](https://x.com/ModernGrindTech/status/2039006687491703263))

The composability argument is the core value prop, per @mylifcc: *"Been using MCP servers in Claude Code for months. The key win is composability — each server handles one domain, and the agent picks the right tools per task."* ([link](https://x.com/mylifcc/status/2038540273320632807))

Claude Code's **MCP Tool Search** feature — enabling lazy loading — reduces context usage by up to 95%, removing the previous constraint of needing to choose between running many servers and burning context budget. Separately, [steipete's claude-code-mcp](https://github.com/steipete/claude-code-mcp) enables Claude Code to *be* an MCP server itself, opening a "agent in your agent" pattern. Clify ([Show HN](https://news.ycombinator.com/item?id=47682217)) takes this further: generate a CLI from any API docs and expose it as agent tooling.

@satapathy9 frames the strategic implication: *"The real alpha most people miss: Claude Code + MCP servers + CLAUDE.md files. Once you teach the agent YOUR codebase conventions, it stops being a generic autocomplete and becomes a team member that actually knows your stack."* ([link](https://x.com/satapathy9/status/2039959153456861377))

VS Code's AI Toolkit added a new **Tool Catalog** in March 2026 for building and discovering MCP servers directly from the IDE ([Visual Studio Magazine](https://visualstudiomagazine.com/articles/2026/03/10/building-an-mcp-server-in-new-vs-codes-new-tool-catalog-in-ai-toolkit-extension.aspx)).

**Sources:** X, HN, Web (GitHub, Visual Studio Magazine, DeepWiki, EvoMap, Bannerbear, DEV Community)

---

### 3. Marketplace Explosion — Competing Directories, Millions of Skills

The skill discovery landscape has fragmented into competing registries, each with dramatically different counts:

| Marketplace | Skills/Plugins | Notes |
|-------------|----------------|-------|
| SkillsMP | 425,000+ | Largest; open SKILL.md standard |
| LobeHub Skills | 169,739 | Fast-growing |
| agentskill.sh | 110,000+ | Multi-tool: Claude Code, Cursor, Copilot, Windsurf, Zed |
| skills.sh (Vercel) | 87,000+ | Open leaderboard |
| awesome-agent-skills (VoltAgent) | 1,000+ *curated* | Official skills from Anthropic, Google Labs, Vercel, Stripe, Cloudflare, Netlify, Trail of Bits, Sentry, Expo, HuggingFace, Figma |

The divergence is significant: high-count registries (87K–425K) index any SKILL.md file they can find; curated directories like [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) focus on real-world skills published by actual engineering teams. @haileyhmt celebrated 3.7k GitHub stars and 30+ contributors on awesome-agent-skills ([link](https://x.com/haileyhmt/status/2041637820385608189)).

Other curated community collections: [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code), [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills), [heilcheng/awesome-agent-skills](https://github.com/heilcheng/awesome-agent-skills), [gmh5225/awesome-skills](https://github.com/gmh5225/awesome-skills), and [BehiSecc/awesome-claude-skills](https://github.com/BehiSecc/awesome-claude-skills). The [awesome-skills.com](https://awesome-skills.com/) and [awesomeskills.dev](https://www.awesomeskills.dev/en) sites aggregate these.

The **SKILL.md open standard** is notable: it's shared across Claude Code, Cursor, Copilot, Windsurf, Zed, Codex, Gemini CLI, Antigravity, and OpenCode — one file works everywhere. Anthropic's official marketplace at `claude.ai/settings/plugins` lists reviewed, curated plugins for those preferring vetted options.

Danube, an AI Tools Marketplace ([Show HN](https://news.ycombinator.com/item?id=47501216)), surfaced on HN in March — a commenter noted they'd just submitted gitrama-mcp, a remote MCP server with 17 Git intelligence tools. The broader "Stack Overflow for AI coding agents" concept also gained traction via Cq ([Show HN](https://news.ycombinator.com/item?id=47491466), 225 pts, 104 comments) — institutional knowledge for agent stacks.

@grok's summary of the "Claude Code Resource Bible" — a curated list of 54 tools, MCP servers, skills, and agent frameworks — picked up engagement as a practical entry point ([link](https://x.com/grok/status/2041383051519778935)), as did @DAIEvolutionHub's pointer to a comprehensive GitHub playbook (208 likes, [link](https://x.com/DAIEvolutionHub/status/2039764114936148477)).

**Sources:** X, HN, Web (SkillsMP, LobeHub, GitHub repos, KDnuggets, Medium, Morph, Chris Ayers, DeepWiki)

---

### 4. ClawHavoc: Supply Chain Attack Compromised ~20% of a Major Skill Registry

The biggest security event of the quarter for the agent skills ecosystem: **ClawHavoc**, a coordinated supply chain attack on OpenClaw's **ClawHub** registry. The campaign started January 27, 2026, surged January 31, and involved 335 malicious skills traced to a single threat actor. Antiy CERT confirmed 1,184 total illicit skills across ClawHub — an estimated 20% of the registry at peak.

The payload was **Atomic macOS Stealer (AMOS)**: a commodity infostealer harvesting browser credentials, keychain passwords, cryptocurrency wallets, SSH keys, and Telegram session data. Attack vectors were sophisticated: some skills embedded reverse shell backdoors that triggered during *normal use*, not installation. Others silently exfiltrated credentials from `~/.clawdbot/.env` to external webhook services.

Snyk's accompanying research ([From SKILL.md to Shell Access in Three Lines of Markdown](https://snyk.io/articles/skill-md-shell-access/)) is now essential reading for anyone installing skills from public registries: a malicious SKILL.md can achieve remote code execution in three lines without triggering obvious red flags.

[SkillRisk.org](https://skillrisk.org/) launched as a free scanner specifically for AI agent skills and MCP servers in response. FrankTsaiii built a similar capability directly into Claude Code: an open-source agent that auto-discovers new MCP servers and tools, scores them, and runs security checks before install ([link](https://x.com/FrankTsaiii/status/2040458327826788525)).

Coverage: [eSecurity Planet](https://www.esecurityplanet.com/threats/hundreds-of-malicious-skills-found-in-openclaws-clawhub/), [Repello AI](https://repello.ai/blog/clawhavoc-supply-chain-attack), [CyberPress](https://cyberpress.org/clawhavoc-poisons-openclaws-clawhub-with-1184-malicious-skills/), [Termdock](https://www.termdock.com/en/blog/clawhub-malicious-skills-incident), [Conscia](https://conscia.com/blog/the-openclaw-security-crisis/), [PointGuard AI](https://www.pointguardai.com/ai-security-incidents/openclaw-clawhub-malicious-skills-supply-chain-attack), [Rock Cyber Musings](https://www.rockcybermusings.com/p/agent-supply-chain-attacks-scanner-switched-sides), [CyberDesserts](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/).

**Sources:** Web (multiple security outlets)

---

### 5. Cross-Platform Skills — Same SKILL.md, Every Agent

The cross-compatibility of the SKILL.md standard is increasingly emphasized. @drdmohssine describes the mechanism: *"AST parsing turns messy, language-specific code into clean, portable skill modules that can flow across Claude Code, MCP servers, and agent frameworks without rewriting."* ([link](https://x.com/drdmohssine/status/2038954604784680986))

Goose (from Jack Dorsey's company) entered the conversation as a free, open-source alternative to Claude Code with MCP/skill support — @_vmlops noted the cost contrast: Claude Code at $200/month vs. GitHub Copilot at $19/month vs. Goose at $0 ([link](https://x.com/_vmlops/status/2041767186663186483)). The tooling ecosystem is now cross-tool: VoltAgent/awesome-agent-skills explicitly targets Claude Code, Codex, Antigravity, Gemini CLI, Cursor, Copilot, OpenCode, Windsurf simultaneously.

Microsoft's .NET team joined this trend, publishing guidance on extending coding agents with .NET Skills ([.NET Blog](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/)).

API scorecard work by @jun_liang_sf tracks which products support Agent Skills, CLI, llms.txt, MCP servers, and Context7 — positioning skills/MCP support as a formal compatibility dimension for developer tools ([link](https://x.com/jun_liang_sf/status/2041480877314805918)).

**Sources:** X, Web (Microsoft .NET Blog, GitHub repos, Cirrius Solutions, O-Mega, ByteBridge)

---

### 6. Vertical Skills: Injective AI Toolkit Brings Agent Skills to Blockchain Trading

The most-engaged X post in the research (334 likes): Injective shipped an **AI Toolkit** combining MCP servers with seven modular agent skills for blockchain trading — account analysis, portfolio monitoring, session-based auto-signing, cross-chain bridging (Arbitrum/Base/Polygon/BSC), real-time market data with oracle prices and funding rates, staking management, and token metadata resolution.

The **Trading Autosign skill** stands out architecturally: scoped, time-limited delegation allowing an AI agent to place and close perpetual trades without a wallet popup for each order. @Altcoinbuzzio: *"AI AGENTS ON INJECTIVE CAN NOW TRADE, BRIDGE, MANAGE WALLETS, AND DEPLOY CONTRACTS. AUTONOMOUSLY."* ([link](https://x.com/Altcoinbuzzio/status/2038875189694668971))

Compatible with Claude Code, Codex, OpenCode, Cursor, Roo, Cline, and Claude Desktop. Coverage: [CryptoWisser](https://www.cryptowisser.com/news/injective-releases-the-new-injective-ai-toolkit), [MCPServers.org](https://mcpservers.org/agent-skills), [PulseMCP](https://www.pulsemcp.com/servers/skills-mcp-skills).

**Sources:** X, Web

---

## Cross-Source Patterns

**1. MCP as the universal integration layer** — appeared on X (15+ posts), HN (multiple submissions), and across all web sources. Every new agent tool (Goose, Hermes, VS Code AI Toolkit, Injective) ships MCP support as table stakes. The protocol achieved critical mass in Q1 2026.
> "MCP hit 400+ servers on GitHub in under a year. Twelve months ago: zero." — @DasNripanka ([link](https://x.com/DasNripanka/status/2040852306170888431))

**2. Skill security is an unsolved problem** — appeared across web (ClawHavoc coverage from 8+ outlets), X (FrankTsaiii's security scanner), and HN. The SKILL.md attack surface is novel: three lines of markdown can achieve shell access, and registries grew faster than review processes.
> "From SKILL.md to Shell Access in Three Lines of Markdown" — Snyk ([link](https://snyk.io/articles/skill-md-shell-access/))

**3. Curated vs. volume directories splitting the ecosystem** — appeared on X (multiple posts sharing awesome-* lists) and web (SkillsMP at 425K vs. awesome-agent-skills at 1K curated). Community is bifurcating between "find anything" registries and "trust this" curated collections.
> "Grateful for 3.7k stars, multiple citations, and 30+ contributors on awesome-agent-skills" — @haileyhmt ([link](https://x.com/haileyhmt/status/2041637820385608189))

**4. Production Claude Code stacks are multi-server, multi-skill** — appeared on X (elCholoCat, ModernGrindTech, satapathy9) and web (DEV Community production guides). The average power user is no longer running one MCP server — they're running 4–6 with routing, review gates, and memory.
> "we're running 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier, and a review gate that fires on every code change" — @elCholoCat ([link](https://x.com/elCholoCat/status/2041581965619404880))

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @injective | AI agents on Injective can now trade perps...MCP servers, seven modular agent skills, works with Claude | 334 | 55 | https://x.com/injective/status/2038592582498840832 |
| @DAIEvolutionHub | This GitHub repo is basically the Claude Code cheat code: Commands, Sub-Agents, Skills, MCP Servers, Memory, Hooks | 208 | 36 | https://x.com/DAIEvolutionHub/status/2039764114936148477 |
| @Altcoinbuzzio | AI AGENTS ON INJECTIVE CAN NOW TRADE...MCP servers. Seven modular agent skills | 25 | 4 | https://x.com/Altcoinbuzzio/status/2038875189694668971 |
| @_vmlops | claude code costs $200/month...goose is a free, open source ai agent | 13 | 1 | https://x.com/_vmlops/status/2041767186663186483 |
| @haileyhmt | Grateful for 3.7k stars on awesome-agent-skills, now live as a directory | 5 | 1 | https://x.com/haileyhmt/status/2041637820385608189 |
| @TheFutureBits | This Claude Code resource list is absolute gold. 54 tools, MCP servers, skills | 2 | — | https://x.com/TheFutureBits/status/2041457942575108535 |
| @FrankTsaiii | built open source agent that auto-discovers MCP servers, scores them, runs security checks | — | — | https://x.com/FrankTsaiii/status/2040458327826788525 |
| @grok | "Claude Code Resource Bible" — 50+ tools, MCP servers, docs, frameworks | — | — | https://x.com/grok/status/2041383051519778935 |
| @elCholoCat | 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier, review gate | — | — | https://x.com/elCholoCat/status/2041581965619404880 |
| @jun_liang_sf | Scoring Claude Code on Agent Skills, CLI support, llms.txt, MCP servers, Context7 | — | — | https://x.com/jun_liang_sf/status/2041480877314805918 |
| @DasNripanka | MCP hit 400+ servers on GitHub in under a year | — | — | https://x.com/DasNripanka/status/2040852306170888431 |
| @drdmohssine | AST parsing turns code into portable skill modules across Claude Code, MCP servers | — | — | https://x.com/drdmohssine/status/2038954604784680986 |
| @ModernGrindTech | chrome devtools, neon postgres, notion, discord all as MCP servers wired into Claude Code | — | — | https://x.com/ModernGrindTech/status/2039006687491703263 |
| @mylifcc | key win: composability — each MCP server handles one domain, agent picks right tools per task | — | — | https://x.com/mylifcc/status/2038540273320632807 |
| @satapathy9 | Claude Code + MCP servers + CLAUDE.md = team member that knows your stack | — | — | https://x.com/satapathy9/status/2039959153456861377 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| peteski22 | Show HN: Cq – Stack Overflow for AI coding agents | 225 | 104 | "actually a good idea, especially when implemented on company-level" | https://news.ycombinator.com/item?id=47491466 |
| jimbursch1 | Show HN: MemoTrader – a marketplace for AI-Human messaging | 4 | 2 | "I like the idea of agents reaching humans with minimal setup" | https://news.ycombinator.com/item?id=47327172 |
| preston25 | Show HN: Danube – AI Tools Marketplace | 3 | 1 | "Just submitted gitrama-mcp — 17 Git intelligence tools, remote MCP server live at mcp.gitrama.ai" | https://news.ycombinator.com/item?id=47501216 |
| dko | Show HN: Clify – generate a CLI from any API docs, use it as agent tooling | 3 | 0 | — | https://news.ycombinator.com/item?id=47682217 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs | https://code.claude.com/docs/en/features-overview | Official extension type taxonomy |
| Claude Code Subagents Docs | https://code.claude.com/docs/en/sub-agents | Subagent creation guide |
| Claude Agent SDK MCP Docs | https://platform.claude.com/docs/en/agent-sdk/mcp | MCP integration with Agent SDK |
| ClaudeFA.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP Servers list |
| Claude Marketplaces | https://claudemarketplaces.com/ | Community marketplace aggregator |
| Morph (Extensions Guide) | https://www.morphllm.com/claude-code-extensions | Claude Code Extensions guide 2026 |
| Morph (Skills vs MCP) | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins comparison |
| DEV Community (RaxxoStudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best Skills & Plugins 2026 |
| DEV Community (lizechengnet) | https://dev.to/lizechengnet/how-to-structure-claude-code-for-production-mcp-servers-subagents-and-claudemd-2026-guide-4gjn | Production structure guide |
| DEV Community (shinpr) | https://dev.to/shinpr/bringing-claude-codes-sub-agents-to-any-mcp-compatible-tool-1hb9 | Subagents to MCP-compatible tools |
| GitHub: jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 agent skills, CCPI manager |
| TurboDocx | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Plugins & MCP Servers roundup |
| SkillsPlayground | https://skillsplayground.com/guides/claude-code-plugins/ | Complete plugins guide |
| Composio | https://composio.dev/content/top-claude-code-plugins | Top 10 Claude Code plugins |
| Chris Ayers | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Agent Skills & Marketplace guide |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces |
| DeepWiki (MS agent-skills) | https://deepwiki.com/microsoft/agent-skills/4-plugins | Microsoft agent-skills plugin docs |
| Skywork.ai | https://skywork.ai/skypage/en/clawhub-openclaw-skill-registry/2038573559848898560 | ClawHub OpenClaw registry guide |
| Microsoft .NET Blog | https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/ | .NET Skills for coding agents |
| SkillsMP | https://skillsmp.com/ | 425,000+ skills marketplace |
| DeepWiki (anthropics/skills) | https://deepwiki.com/anthropics/skills/2.3-marketplace-and-plugin-system | Anthropic skills marketplace system |
| DeepWiki (claude-code plugins) | https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery | Plugin marketplace & discovery |
| DeepWiki (claude-code MCP) | https://deepwiki.com/anthropics/claude-code/3.5-mcp-server-integration | MCP server integration |
| Medium (markchen69) | https://medium.com/@markchen69/claude-code-has-a-skills-marketplace-now-a-beginner-friendly-walkthrough-8adeb67cdc89 | Skills marketplace walkthrough |
| Medium (frulouis) | https://medium.com/@frulouis/25-top-claude-agent-skills-registries-community-collections-you-should-know-2025-52aab45c877d | 25+ registries & community collections |
| GitHub: steipete/claude-code-mcp | https://github.com/steipete/claude-code-mcp | Claude Code as one-shot MCP server |
| ksred.com | https://www.ksred.com/claude-code-as-an-mcp-server-an-interesting-capability-worth-understanding/ | Claude Code as MCP server analysis |
| EvoMap | https://evomap.ai/blog/best-mcp-servers-for-claude-code-2026 | Best MCP Servers 2026 |
| Bannerbear | https://www.bannerbear.com/blog/8-best-mcp-servers-for-claude-code-developers-in-2026/ | 8 Best MCP Servers |
| Medium (unicodeveloper) | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills for Claude 2026 |
| GitHub: travisvn/awesome-claude-skills | https://github.com/travisvn/awesome-claude-skills | Curated Claude Skills list |
| GitHub: VoltAgent/awesome-agent-skills | https://github.com/VoltAgent/awesome-agent-skills | 1,000+ official + community skills |
| GitHub: hesreallyhim/awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | Skills, agents, plugins, hooks for Claude Code |
| Awesome-Skills.com | https://awesome-skills.com/ | Curated skills & plugins directory |
| GitHub: heilcheng/awesome-agent-skills | https://github.com/heilcheng/awesome-agent-skills | Tutorials, guides, skill directories |
| GitHub: BehiSecc/awesome-claude-skills | https://github.com/BehiSecc/awesome-claude-skills | Curated Claude skills |
| GitHub: gmh5225/awesome-skills | https://github.com/gmh5225/awesome-skills | Agent Skills for Claude Code, Codex, Gemini CLI, Copilot |
| AwesomeSkills.dev | https://www.awesomeskills.dev/en | Agent Skills directory (Claude, Codex, Cursor) |
| ScriptByAI | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate Claude Code Resource List 2026 |
| eSecurity Planet | https://www.esecurityplanet.com/threats/hundreds-of-malicious-skills-found-in-openclaws-clawhub/ | ClawHavoc: hundreds of malicious skills |
| Repello AI | https://repello.ai/blog/clawhavoc-supply-chain-attack | ClawHavoc: inside the supply chain attack |
| CyberDesserts | https://blog.cyberdesserts.com/openclaw-malicious-skills-security/ | OpenClaw security risks |
| Rock Cyber Musings | https://www.rockcybermusings.com/p/agent-supply-chain-attacks-scanner-switched-sides | Agent supply chain attacks analysis |
| CyberPress | https://cyberpress.org/clawhavoc-poisons-openclaws-clawhub-with-1184-malicious-skills/ | 1,184 malicious skills confirmed |
| Termdock | https://www.termdock.com/en/blog/clawhub-malicious-skills-incident | ClawHub incident details |
| Snyk | https://snyk.io/articles/skill-md-shell-access/ | SKILL.md → shell access in 3 lines |
| Conscia | https://conscia.com/blog/the-openclaw-security-crisis/ | OpenClaw security crisis analysis |
| SkillRisk.org | https://skillrisk.org/ | Free AI agent skill security scanner |
| PointGuard AI | https://www.pointguardai.com/ai-security-incidents/openclaw-clawhub-malicious-skills-supply-chain-attack | Incident database entry |
| CryptoWisser | https://www.cryptowisser.com/news/injective-releases-the-new-injective-ai-toolkit | Injective AI Toolkit announcement |
| MCPServers.org | https://mcpservers.org/agent-skills | Agent Skills Library |
| Medium (devops-ai-decoded) | https://medium.com/devops-ai-decoded/top-10-mcp-servers-for-ai-agent-orchestration-in-2026-78cdb38e9fba | Top 10 MCP Servers for Orchestration |
| cra.mr | https://cra.mr/mcp-skills-and-agents/ | MCP, Skills, and Agents conceptual overview |
| PulseMCP | https://www.pulsemcp.com/servers/skills-mcp-skills | Skills MCP Server listing |
| ByteBridge (MCP + Skills) | https://bytebridge.medium.com/model-context-protocol-mcp-and-agent-skills-empowering-ai-agents-with-tools-and-expertise-bd4dbe3f2f00 | MCP and Agent Skills deep dive |
| O-Mega | https://o-mega.ai/articles/top-10-ai-agent-skills-for-2026-an-in-depth-guide | Top 10 AI Agent Skills for 2026 |
| Cirrius Solutions | https://cirriussolutions.com/agent-vs-mcp-vs-skills/ | Agent vs MCP vs Skills comparison |
| ByteBridge (MCP Gateways) | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | MCP Gateways 2026 guide |
| Visual Studio Magazine | https://visualstudiomagazine.com/articles/2026/03/10/building-an-mcp-server-in-new-vs-codes-new-tool-catalog-in-ai-toolkit-extension.aspx | VS Code AI Toolkit Tool Catalog |

---

## Stats Block

```
├─ 🔵 X: 28 posts │ 587 likes │ 97 reposts
├─ 🟢 HN: 4 stories │ 235 points │ 107 comments
├─ 🌐 Web: 62 pages — Snyk, Repello AI, eSecurity Planet, Morph, KDnuggets, DEV Community, Microsoft .NET Blog, Visual Studio Magazine, GitHub (VoltAgent/awesome-agent-skills), ScriptByAI, CryptoWisser, SkillRisk
└─ 🗣️ Top voices: @injective (334 likes), @DAIEvolutionHub (208 likes), @Altcoinbuzzio (25 likes) │ hn/peteski22 (225 pts)
```

---

## Data Gaps

- **Reddit: 0 threads** — ScrapeCreators API returned HTTP 402 Payment Required for both queries. This is a significant gap; Reddit (r/ClaudeAI, r/LocalLLaMA, r/MachineLearning) likely has active MCP/skills discussion not captured here.
- **Bluesky: error** — HTTP 403 Forbidden on both runs.
- **YouTube: 0 videos** — yt-dlp search returned 0 results for both query strings. Tutorial content on Claude Code skills/MCP is likely substantial on YouTube but not captured.
- **TikTok/Instagram: 0** — No relevant results in the tech/dev space for this topic.
- **X relevance threshold**: Run 1 (long query) had all posts below 0.3 relevance — the query string was too long. Run 2 with shorter query resolved this.
- **Approximate coverage:** ~55% — X and HN well covered; Reddit, YouTube, Bluesky missing entirely.
- **ClawHavoc data note:** The attack targeted OpenClaw/ClawHub specifically, not the Claude Code official plugin store. Attribution across "agent skills ecosystems" should distinguish between OpenClaw's registry and Anthropic's marketplace.

---

## Key Quotes

> "MCP hit 400+ servers on GitHub in under a year. Twelve months ago: zero. Today: the protocol every agent stack needs to be compatible with." — @DasNripanka on X ([link](https://x.com/DasNripanka/status/2040852306170888431))

> "we're running 50+ custom skills, 6 MCP servers, auto-memory, agent routing by model tier, and a review gate that fires on every code change. claude code is basically a second brain at this point." — @elCholoCat on X ([link](https://x.com/elCholoCat/status/2041581965619404880))

> "The real alpha most people miss: Claude Code + MCP servers + CLAUDE.md files. Once you teach the agent YOUR codebase conventions, it stops being a generic autocomplete and becomes a team member that actually knows your stack." — @satapathy9 on X ([link](https://x.com/satapathy9/status/2039959153456861377))

> "the MCP server pattern is where everything converges. I run chrome devtools, neon postgres, notion, and discord all as MCP servers wired into Claude Code. the agent can browse, query databases, read docs, and send messages — no switching between tools." — @ModernGrindTech on X ([link](https://x.com/ModernGrindTech/status/2039006687491703263))

> "AST parsing turns messy, language-specific code into clean, portable skill modules that can flow across Claude Code, MCP servers, and agent frameworks without rewriting." — @drdmohssine on X ([link](https://x.com/drdmohssine/status/2038954604784680986))

> "From SKILL.md to Shell Access in Three Lines of Markdown" — Snyk research ([link](https://snyk.io/articles/skill-md-shell-access/))

> "I was skeptical at first, but now I think it's actually a good idea, especially when implemented on company-level" — HN comment on Cq (Stack Overflow for AI coding agents) ([link](https://news.ycombinator.com/item?id=47491466))

> "Grateful for 3.7k stars, multiple citations, and 30+ contributors on awesome-agent-skills, now live as a directory" — @haileyhmt on X ([link](https://x.com/haileyhmt/status/2041637820385608189))
