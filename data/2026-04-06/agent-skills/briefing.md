# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-06
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 31 posts | 163+ likes, 9+ reposts | Many posts had no visible engagement data |
| Hacker News | 23 stories | 143+ points, 52+ comments | 15 stories with full detail in compact output |
| Web | 40 pages | — | via 4 WebSearch queries |

---

## Synthesized Findings

### 1. The Skills Ecosystem Has Exploded — SKILL.md Is the New Unit of Agent Knowledge

The last 30 days mark a tipping point: "skills" (SKILL.md instruction files) have rapidly become the dominant primitive for extending AI coding agents. In December 2025, Anthropic released the Agent Skills specification as an open standard; OpenAI adopted the same format for Codex CLI and ChatGPT, Google integrated it into Gemini/Antigravity by January 2026, and Vercel launched skills.sh as the ecosystem's first dedicated package manager on January 20, 2026.

The scale of growth is striking. In January 2026 there were tens of thousands of skills; by early March 2026 the count topped 351,000. SkillsMP now indexes 700,000+ skills searchable by occupation, author, and popularity. LobeHub Skills has 169,739 indexed; agentskill.sh supports 110,000+ across 20+ AI tools. The HN discussion "Skills are quietly becoming the unit of agent knowledge" (9 pts, 13 comments) captured the moment — with top comments asking "Will skills replace MCP servers eventually?" and "What do you think about checking skills directly into the repo where they are useful?"

Skills work across Claude Code, Cursor, GitHub Copilot, Aider, OpenCode, Codex CLI, and 30+ other agents out of the box, per the VoltAgent/awesome-agent-skills repo. Unlike slash commands that require explicit triggers, skills activate automatically when the agent detects relevant context.

**Sources:** https://news.ycombinator.com/item?id=47475832, https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/, https://www.marktechpost.com/2026/01/18/vercel-releases-agent-skills-a-package-manager-for-ai-coding-agents-with-10-years-of-react-and-next-js-optimisation-rules/, https://skillsmp.com/, https://github.com/VoltAgent/awesome-agent-skills

### 2. Skills vs. MCP vs. Plugins — Three Distinct Layers, Complementary Not Competing

A key clarification repeatedly surfacing across HN, blogs, and X: these three things are *not* the same. Per the Nevo Systems breakdown and a dedicated DEV Community post ("MCP vs Agent Skills: Why They're Different, Not Competing"):

- **Skills** = prompt-based instruction files (SKILL.md) that modify agent behavior without code
- **Plugins** = distributable packages bundling skills + hooks + subagents + commands + configs
- **MCP servers** = standardized connections to external tools/data via Model Context Protocol

MCP had already reached 97 million monthly SDK downloads with 10,000+ active servers deployed by early 2026. Anthropic applied progressive discovery to MCP so each tool costs only 20–50 tokens in context — similar to Skills. The "Ink – Deploy full-stack apps from AI agents via MCP or Skills" HN post (32 pts, 6 comments) demonstrated both being used together in practice. Qualys published "MCP Servers: The New Shadow IT for AI in 2026," flagging that enterprise MCP adoption is outpacing governance — a pattern increasingly mirrored in skills.

**Sources:** https://dev.to/phil-whittaker/mcp-vs-agent-skills-why-theyre-different-not-competing-2bc1, https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp, https://news.ycombinator.com/item?id=47337028, https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026, https://gofastmcp.com/servers/providers/skills, https://mcpservers.org/agent-skills

### 3. Security Is the Biggest Open Problem in the Skills Ecosystem

The highest-engagement HN story this period was "Agent Skills – Open Security Database" (36 pts, 9 comments, 2026-03-16). A new public database launched to track security risks introduced by AI agent skills — the capabilities increasingly defining how modern AI agents operate.

A Snyk study scanning 3,984 skills found 13.4% contained critical security issues. Responses ranged: "this whole concept of insecure skills is so dumb to me, if your engineers are installing and running random 'skills' found online it's the same as if you had engineers installing and running random npm packages found online" — but others noted this was exactly why tooling was needed.

@PixelFamiliar on X put it sharply: "Inference costs eating 50%+ of revenue is exactly why the agent skills supply chain matters. Every third-party skill you install = more compute, more attack surface, and zero visibility into what it's doing." Vercel has partnered with Snyk to bake security scanning into Skills.sh; Anthropic is developing a trust framework for skill publishing.

The HN story "What Claude Code Leak Teaches Us About Agent Skills" (5 pts, 2026-04-01) reflected continued scrutiny of how Claude Code's own internal skill architecture informs the broader ecosystem.

**Sources:** https://news.ycombinator.com/item?id=47402118, https://news.ycombinator.com/item?id=47605341, https://x.com/PixelFamiliar/status/2041066232770609484, https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026

### 4. Package Managers for Skills Are Emerging as Critical Infrastructure

Multiple parallel efforts to build npm-equivalent infrastructure for agent skills are underway:

- **Vercel skills.sh** (launched Jan 20, 2026): Top skills accumulated 26,000+ installs within weeks
- **HN6 ("I built a package manager for agent skills")**: Community-built package manager, 3 pts, 1 comment (2026-03-23)
- **CCPI** (Claude Code Plugin Index): Referenced in the jeremylongshore/claude-code-plugins-plus-skills repo (340 plugins + 1367 skills)
- **SkillsMP**: 700,000+ skills, cross-platform search
- **KDnuggets** listed "Top 5 Agent Skill Marketplaces" as a distinct emerging category

Claude Code's plugin system went into public beta in early 2026, enabling installation, versioning, updating, and sharing of entire workflow packages through plugin marketplaces. Over 9,000 plugins are available as of February 2026. The quemsah/awesome-claude-plugins repo tracks plugin adoption metrics via n8n.

The "Agent Skills Are the New npm" framing has become a recurring meme — reflecting both the analogy's accuracy (distributed package ecosystem, versioning, security risks) and its cautionary dimension.

**Sources:** https://news.ycombinator.com/item?id=47489570, https://github.com/jeremylongshore/claude-code-plugins-plus-skills, https://vercel.com/docs/agent-resources/vercel-plugin, https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents, https://github.com/quemsah/awesome-claude-plugins, https://code.claude.com/docs/en/discover-plugins

### 5. Solana Foundation Launches Official Agent Skills — Blockchain-Native Skill Distribution

Prominent X activity today centered on the Solana Foundation's release of "Solana Agent Skills" — prebuilt skill packages for AI agents that interact with the Solana blockchain, installable via a single command line call. @Solana_zh (2 likes, 1 repost) and @SuperteamJapan (2 likes) announced the release in Chinese and Japanese respectively.

Per @marinonchain: "Solana AI Agent Skills can already help you with: Making money, improving your onchain user experience, managing your portfolio." Official Foundation skills cover error handling, security checklists, private transfers, and version compatibility. The community has contributed 60+ additional skills covering DeFi, payments, and infrastructure.

The Helius MCP server gives AI tools (Claude Code, Claude Desktop, Cursor, VS Code, Windsurf) direct access to 60+ Helius API tools for Solana. The Solana Developer MCP at mcp.solana.com is maintained by the Foundation directly. @pieverse_io announced integration of OKX Wallet's "Onchain OS Skills" into the Purr-Fect Claw ecosystem (127 likes — highest X engagement in this batch).

This is a notable pattern: blockchain/Web3 ecosystems are early adopters of the agent skills distribution model, using skills to package domain-specific expertise (chain interactions, wallet operations, DeFi protocols) into installable units for general-purpose coding agents.

**Sources:** https://x.com/Solana_zh/status/2041063362918764795, https://x.com/SuperteamJapan/status/2041066616449085875, https://x.com/marinonchain/status/2041063916995063896, https://x.com/pieverse_io/status/2041052133827674488, https://www.helius.dev/blog/helius-for-agents, https://mcp.solana.com/, https://github.com/solana-foundation/awesome-solana-ai, https://github.com/sendaifun/solana-mcp

### 6. Claude-Specific Tooling: BrowserHawk, Skills Manager, Claude Code Courses

Several Claude Code–specific skill developments are active:

- **BrowserHawk** (HN9, 3 pts): Open-source autonomous QA agent skill for Claude Code — https://news.ycombinator.com/item?id=47574095
- **Skills Manager** (HN4, 3 pts, 9 comments): Manages agent skills across Claude, Cursor, Copilot — https://news.ycombinator.com/item?id=47423910
- **Skales** (HN16, 12 pts, 6 comments): Desktop AI agent "a 6-year-old can use," built around skills primitives — https://news.ycombinator.com/item?id=47613527
- **alirezarezvani/claude-skills**: 220+ Claude Code skills & agent plugins for Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents — https://github.com/alirezarezvani/claude-skills

On the educational front, @aigoldrushh's post about Anthropic's 13 free AI courses (24 likes, 5 reposts) generated discussion specifically about the "Agent Skills" course being "clutch for anyone building on-chain" (per @Chaborzdu667) and should include "building a bot that handles a real-world scenario" (per @MichaelAluya3).

Scott Spence published a blog post on organizing Claude Code skills into plugin marketplaces, reflecting practitioner interest in governance patterns. The dev.to/raxxostudios guide "Best Claude Code Skills & Plugins (2026 Guide)" appeared as a reference post.

**Sources:** https://news.ycombinator.com/item?id=47574095, https://news.ycombinator.com/item?id=47423910, https://news.ycombinator.com/item?id=47613527, https://github.com/alirezarezvani/claude-skills, https://x.com/aigoldrushh/status/2041042260712726937, https://x.com/Chaborzdu667/status/2041050400766230954, https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces, https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4

### 7. Practical Skill Use Cases Proliferating: PySpark, n8n, Golang, Affiliate Marketing

The HN activity shows rapid proliferation of domain-specific skills:

- **One-Shot PySpark from the CLI** (22 pts, 4 comments): "agent 'build me a churn model from this data' = YES PLEASE" — https://news.ycombinator.com/item?id=47534936
- **35 Golang Agent Skills** collection by hn/samber — https://news.ycombinator.com/item?id=47487741
- **n8n workflows → OpenClaw agent skills** converter — https://news.ycombinator.com/item?id=47561083
- **AI agent skills for affiliate marketing** (Markdown, any LLM) — https://news.ycombinator.com/item?id=47632530
- **Orca – Executable skills for AI agent workflows** — https://news.ycombinator.com/item?id=47584819
- **Production-ready Agent Skills, 17 agents, orchestration protocol** — https://news.ycombinator.com/item?id=47363984
- **App that ships with AI agent skills to extend and audit itself** — https://news.ycombinator.com/item?id=47442521

The halallens.no "Agentic Coding 2026: Complete Guide to Plugins, Multi-Model Orchestration, and AI Agent Teams" and the Microsoft/skills GitHub repo (Skills, MCP servers, Custom Agents, Agents.md for SDKs) reflect that enterprise/production-grade skill patterns are solidifying. Duende Software published a blog post on adding expertise via Agent Skills + MCP Server, exemplifying the pattern of domain-specific software vendors packaging their knowledge as installable agent capabilities.

**Sources:** https://news.ycombinator.com/item?id=47534936, https://news.ycombinator.com/item?id=47487741, https://news.ycombinator.com/item?id=47561083, https://news.ycombinator.com/item?id=47632530, https://halallens.no/en/blog/agentic-coding-in-2026-the-complete-guide-to-plugins-multi-model-orchestration-and-ai-agent-teams, https://github.com/microsoft/skills, https://duendesoftware.com/blog/20260402-give-your-ai-coding-assistant-duende-expertise-with-agent-skills-and-mcp-server

---

## Cross-Source Patterns

### Pattern 1: "Skills as the New npm" — Distributed Package Ecosystem Analogy
- **Platforms:** HN, Web (multiple blogs)
- HN: "I built a package manager for agent skills" (HN6), community package manager emerging
- Web: buildmvpfast.com explicitly titled "Agent Skills Are the New npm: AI Package Manager Marketplace 2026"
- Context: both the excitement (massive distribution, community-driven) and the concern (supply chain security, 13.4% critical issues per Snyk) track the npm analogy closely

### Pattern 2: Security Concerns Are Under-Addressed Relative to Growth
- **Platforms:** HN, X
- HN1 (36 pts — top story): Agent Skills Open Security Database launch; "engineers installing random skills = engineers installing random npm packages"
- @PixelFamiliar (X): "every third-party skill you install = more compute, more attack surface, and zero visibility"
- Qualys (Web): "MCP Servers: The New Shadow IT for AI in 2026"
- Snyk scan of 3,984 skills: 13.4% critical issues

### Pattern 3: Cross-Agent Portability Is a Selling Point
- **Platforms:** X, Web, HN
- Skills are repeatedly described as working across Claude Code, Cursor, Copilot, Codex, Gemini, Aider, 30+ tools
- @RayChris91 (X): "there's now something called agent skills, basically the effect is similar... but the knowledge poured into skills is indeed what can't always be made public"
- VoltAgent/awesome-agent-skills: explicitly highlights cross-agent compatibility as primary feature
- Skills Manager (HN4): manages skills across Claude, Cursor, Copilot — cross-agent management as a product category

### Pattern 4: Blockchain/Web3 Ecosystems as Early Adopters
- **Platforms:** X (multiple), Web
- Solana Foundation released official Agent Skills (today)
- OKX Wallet "Onchain OS Skills" packaged for Purr-Fect Claw ecosystem (127 likes)
- Helius packaging RPC/API expertise as both MCP server and Skills
- @Chaborzdu667: "the agent skills one is gonna be clutch for anyone building on-chain"
- The Web3 space is treating skills as domain expertise packaging for chain-specific knowledge

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @pieverse_io | Pieverse is bringing Onchain OS Skills from @okx into the Purr-Fect Claw ecosystem... | 127 | 2 | https://x.com/pieverse_io/status/2041052133827674488 |
| @aigoldrushh | Claude just dropped 13 completely FREE AI courses + certificates... | 24 | 5 | https://x.com/aigoldrushh/status/2041042260712726937 |
| @marinonchain | Solana AI Agent Skills can already help you with: Making money, improving your onchain UX... | 8 | — | https://x.com/marinonchain/status/2041063916995063896 |
| @Solana_zh | Solana 推出 Agent Skills，这是一组预构建技能，可直接接入 AI 工具... [Solana launches Agent Skills] | 2 | 1 | https://x.com/Solana_zh/status/2041063362918764795 |
| @SuperteamJapan | Solanaのスキルが、AIツールに直接インストールできる時代へ... [Solana Agent Skills published] | 2 | — | https://x.com/SuperteamJapan/status/2041066616449085875 |
| @PixelFamiliar | Inference costs eating 50%+ of revenue is exactly why the agent skills supply chain matters... | — | — | https://x.com/PixelFamiliar/status/2041066232770609484 |
| @Chaborzdu667 | the agent skills one is gonna be clutch for anyone building on-chain... | — | — | https://x.com/Chaborzdu667/status/2041050400766230954 |
| @MichaelAluya3 | Take the Agent Skills course, then try to build a bot that handles a real-world scenario... | — | — | https://x.com/MichaelAluya3/status/2041056486437126281 |
| @RayChris91 | sekarang ada yang namanya agent skills, basically efeknya serupa... [now there's agent skills, basically similar effect] | — | — | https://x.com/RayChris91/status/2041063878084423795 |
| @nafzztech | You can now generate any QR code offline using Google's new Gemma AI... go to "Agent Skills," select "Generate QR Code" | — | — | https://x.com/nafzztech/status/2041044912448348339 |
| @shanielcreation | Select the mode: Agent Skills / AI Chat / Ask Image / Audio Scribe... [Google AI app with Agent Skills mode] | — | — | https://x.com/shanielcreation/status/2041070661594960255 |
| @sodawhite_dev | 脚本，Agent，skills，到底改怎么使用？[Scripts, Agent, skills — how to use each? What scenario?] | — | — | https://x.com/sodawhite_dev/status/2041061747365445760 |
| @_0xJuggernaut | Must-start courses: Claude 101, AI Fluency, Claude Code in Action — Supercharge your dev workflow | — | — | https://x.com/_0xJuggernaut/status/2041050834142720103 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| hn/4ppsec | Agent Skills – Open Security Database | 36 | 9 | "installing random 'skills' found online it's the same as if you had engineers installing random npm packages" | https://news.ycombinator.com/item?id=47402118 |
| hn/chenxi9649 | Agent Skills: One-Shot PySpark from the CLI | 22 | 4 | "agent 'build me a churn model from this data' = YES PLEASE" | https://news.ycombinator.com/item?id=47534936 |
| hn/august- | Show HN: Ink – Deploy full-stack apps from AI agents via MCP or Skills | 32 | 6 | "Is Okta supported for auth, and how does bring your own cloud work?" | https://news.ycombinator.com/item?id=47337028 |
| hn/latand6 | Skills are quietly becoming the unit of agent knowledge | 9 | 13 | "Will skills replace MCP servers eventually?" | https://news.ycombinator.com/item?id=47475832 |
| hn/marioskales | Show HN: Skales – I built a desktop AI agent a 6-year-old can use | 12 | 6 | — | https://news.ycombinator.com/item?id=47613527 |
| hn/dev_chad | What Claude Code Leak Teaches Us About Agent Skills | 5 | 0 | — | https://news.ycombinator.com/item?id=47605341 |
| hn/evergreenxx | Skills Manager – manage AI agent skills across Claude, Cursor, Copilot | 3 | 9 | — | https://news.ycombinator.com/item?id=47423910 |
| hn/sonpiaz | Show HN: AI agent skills for affiliate marketing (Markdown, works with any LLM) | 3 | 0 | — | https://news.ycombinator.com/item?id=47632530 |
| hn/samber | A collection of 35 Golang Agent Skills | 3 | 2 | — | https://news.ycombinator.com/item?id=47487741 |
| hn/eterer | I built a package manager for agent skills | 3 | 1 | — | https://news.ycombinator.com/item?id=47489570 |
| hn/just-claw-it | Show HN: Built tool to turn n8n workflows into OpenClaw-compatible agent skills | 3 | 0 | — | https://news.ycombinator.com/item?id=47561083 |
| hn/gfernandf | Orca – Executable skills and capabilities for AI agent workflows | 3 | 1 | — | https://news.ycombinator.com/item?id=47584819 |
| hn/jungard | Production-ready Agent Skills, 17 agents, and a orchestration protocol | 3 | 1 | — | https://news.ycombinator.com/item?id=47363984 |
| hn/JakubKontra | BrowserHawk – Open-source autonomous QA agent skill for Claude Code | 3 | 0 | — | https://news.ycombinator.com/item?id=47574095 |
| hn/tadwork | Show HN: A small app that ships with AI agent skills to extend and audit it | 3 | 0 | — | https://news.ycombinator.com/item?id=47442521 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs | https://code.claude.com/docs/en/discover-plugins | Official plugin discovery documentation |
| Anthropic Platform Docs | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official Agent Skills specification overview |
| GitHub: alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 220+ Claude Code skills for 8+ coding agents |
| GitHub: jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1367 skills; CCPI package manager |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community directory; 150+ skills (March 2026) |
| SkillsMP | https://skillsmp.com/ | 700,000+ skills marketplace, cross-platform |
| liteLLM Docs | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Claude Code Plugin Marketplace tutorial |
| Scott Spence (Blog) | https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces | Practitioner guide to organizing skills |
| DEV Community (quemsah) | https://github.com/quemsah/awesome-claude-plugins | Automated plugin adoption metrics via n8n |
| DEV Community (raxxostudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best Claude Code Skills & Plugins 2026 guide |
| PulseMCP | https://www.pulsemcp.com/servers/mrsimpson-agent-skills | Agent Skills MCP Server listing |
| DEV Community (phil-whittaker) | https://dev.to/phil-whittaker/mcp-vs-agent-skills-why-theyre-different-not-competing-2bc1 | MCP vs Agent Skills: Not Competing |
| FastMCP | https://gofastmcp.com/servers/providers/skills | Skills Provider in FastMCP |
| Awesome MCP Servers | https://mcpservers.org/agent-skills | Agent Skills Library on MCP directory |
| GitHub: microsoft/skills | https://github.com/microsoft/skills | MS Skills, MCP servers, Agents.md for SDKs |
| Qualys Blog | https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026 | MCP as Shadow IT in enterprises 2026 |
| Nevo Systems | https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp | Skills vs Plugins vs MCPs taxonomy |
| MCP Directory | https://mcp.directory/skills/skill-share | skill-share listing |
| BuildMVPFast | https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026 | Agent Skills Are the New npm |
| Duende Software | https://duendesoftware.com/blog/20260402-give-your-ai-coding-assistant-duende-expertise-with-agent-skills-and-mcp-server | Domain skills packaging via Agent Skills + MCP |
| johnoct.github.io | https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/ | Skills.sh: Missing Package Manager |
| OpenAI Developers | https://developers.openai.com/codex/skills | Codex Agent Skills official docs |
| MarkTechPost | https://www.marktechpost.com/2026/01/18/vercel-releases-agent-skills-a-package-manager-for-ai-coding-agents-with-10-years-of-react-and-next-js-optimisation-rules/ | Vercel Agent Skills launch (Jan 2026) |
| itecsonline.com | https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 | Codex CLI Agent Skills guide |
| GitHub: heilcheng/awesome-agent-skills | https://github.com/heilcheng/awesome-agent-skills | Tutorials, Guides, Directories |
| Halallens (Blog) | https://halallens.no/en/blog/agentic-coding-in-2026-the-complete-guide-to-plugins-multi-model-orchestration-and-ai-agent-teams | Agentic Coding 2026 complete guide |
| Vercel Docs | https://vercel.com/docs/agent-resources/vercel-plugin | Vercel Plugin for AI Coding Agents |
| GitHub: VoltAgent/awesome-agent-skills | https://github.com/VoltAgent/awesome-agent-skills | 1000+ skills, Claude/Codex/Gemini/Cursor compat |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 Agent Skill Marketplaces |
| Solana Foundation (GitHub) | https://github.com/solana-foundation/awesome-solana-ai | Public AI tooling for Solana |
| Helius Docs | https://www.helius.dev/docs/agents/mcp | Helius MCP Server docs (60+ tools) |
| GitHub: sendaifun/solana-mcp | https://github.com/sendaifun/solana-mcp | Solana MCP Server (open source) |
| AGNXI | https://agnxi.com/sendaifun/skills/solana-agent-kit | solana-agent-kit on AGNXI directory |
| Helius Blog | https://www.helius.dev/blog/helius-for-agents | Helius for Agents: Claude Plugin, MCP, Skills |
| Solana Developer MCP | https://mcp.solana.com/ | Official Foundation MCP for Solana |
| Alchemy Blog | https://www.alchemy.com/blog/how-to-build-solana-ai-agents-in-2026 | How to Build Solana AI Agents 2026 |
| Skywork.ai | https://skywork.ai/skypage/en/solana-mcp-server-on-chain-ai/1980846654002753536 | Solana MCP Server guide |
| MCP Market | https://mcpmarket.com/es/server/solana-agent-kit-2 | Solana Agent Kit on MCP Market |
| GlobeNewswire | https://www.globenewswire.com/news-release/2026/03/25/3261972/0/en/Solo-io-Introduces-the-agentevals-Open-Source-Project-to-Bridge-the-Production-Reliability-Gap-for-Agentic-AI.html | Solo.io agentevals: production reliability for agentic AI |

---

## Stats Block

```
├─ 🔵 X: 31 posts │ 163+ likes │ 9+ reposts
├─ 🟢 HN: 23 stories │ 143+ points │ 52+ comments
├─ 🌐 Web: 40 pages — SkillsMP, Vercel, MarkTechPost, Qualys, KDnuggets, Helius, Nevo Systems, BuildMVPFast, Alchemy, Microsoft
└─ 🗣️ Top voices: @pieverse_io (127 likes), @aigoldrushh (24 likes), @marinonchain (8 likes) │ HN: hn/4ppsec, hn/august-, hn/chenxi9649
```

---

## Data Gaps

- **Reddit:** 0 threads returned — ScrapeCreators API returned HTTP 402 (Payment Required / quota exhausted). This is a significant gap: r/ClaudeAI, r/LocalLLaMA, r/MachineLearning, and r/programming likely have substantive discussions about skills and MCP that are not represented here.
- **YouTube:** 0 videos returned — yt-dlp search returned no results for "agent-skills" as a query. Broader queries like "Claude Code skills tutorial" or "MCP server setup 2026" would likely surface video content; these were not pursued in this run.
- **Bluesky:** HTTP 403 Forbidden error — credentials may have expired. Bluesky has active developer communities discussing Claude Code and MCP.
- **TikTok / Instagram:** Not triggered for this query type/depth setting.
- **Polymarket:** 0 markets — no prediction markets currently active on AI agent skill topics.
- **X noise:** Several X posts (e.g., @StaceyDvm29557, @DianaSmith4105) used "secret agent skills" colloquially with no relation to AI tooling; these were filtered out of synthesis.
- **Coverage estimate:** Approximately 55-65% — strong HN and web coverage, but Reddit and YouTube gaps are material.

---

## Key Quotes

> "Inference costs eating 50%+ of revenue is exactly why the agent skills supply chain matters. Every third-party skill you install = more compute, more attack surface, and zero visibility into what it's doing." — @PixelFamiliar on X ([link](https://x.com/PixelFamiliar/status/2041066232770609484))

> "Despite the obvious self promotion, this whole concept of insecure skills is so dumb to me, if your engineers are installing and running random 'skills' found online it's the same as if you had engineers installing and running random npm packages found online" — hn comment on Agent Skills – Open Security Database ([link](https://news.ycombinator.com/item?id=47402118))

> "Will skills replace MCP servers eventually?" — hn/latand6 discussion, Skills are quietly becoming the unit of agent knowledge ([link](https://news.ycombinator.com/item?id=47475832))

> "agent 'build me a churn model from this data' = YES PLEASE" — hn comment on Agent Skills: One-Shot PySpark from the CLI ([link](https://news.ycombinator.com/item?id=47534936))

> "the agent skills one is gonna be clutch for anyone building on-chain. actually learning how to structure agent behavior beats reading theory all day." — @Chaborzdu667 on X ([link](https://x.com/Chaborzdu667/status/2041050400766230954))

> "Skills are quietly becoming the unit of agent knowledge" — hn/latand6, HN ([link](https://news.ycombinator.com/item?id=47475832))

> "What do you think about checking the skills directly into the repo where they are useful?" — hn comment on skills-as-unit-of-knowledge ([link](https://news.ycombinator.com/item?id=47475832))

> "Solana 推出 Agent Skills，这是一组预构建技能，可直接接入 AI 工具，用于与 @solana 进行交互。一行命令即可安装" [Solana launches Agent Skills — prebuilt skills installable directly into AI tools. One-line install.] — @Solana_zh on X ([link](https://x.com/Solana_zh/status/2041063362918764795))
