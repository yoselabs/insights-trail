# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-03
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 1 thread | 2,485 upvotes, 501 comments | r/ClaudeCode only |
| X/Twitter | 23 posts | 7,115 likes, 332 reposts | Heavy MCP server coverage |
| Hacker News | 20 stories | 102 points, 11 comments | Many Show HN Claude Code tools |
| Bluesky | 13 posts | 81 likes, 1 repost | Active Claude Code discussion |
| GitHub | 12 items | 2,839 reactions, 836 comments | anthropics/claude-code, openai/codex |
| Web | 25 pages | — | 9 engine + 16 WebSearch supplements |
| TikTok | 0 videos | — | SC 402 errors |
| Instagram | 0 reels | — | SC 402 errors |
| YouTube | 0 videos | — | No results returned |
| Polymarket | 0 markets | — | No relevant markets |

---

## Synthesized Findings

### 1. X Launched a Hosted MCP Server on June 30 - the Biggest Platform Move Yet

The dominant story of the past week: X (formerly Twitter) launched an official hosted MCP server on June 30, 2026, becoming the first major social platform to expose its API layer through Anthropic's Model Context Protocol. The server covers 200+ endpoints - search, timelines, trends, bookmarks, profiles, likes, replies, and retweets - accessible to Claude Desktop, Cursor, Grok Build, and any MCP-compatible agent via OAuth and the xurl CLI. [@InfiniStrategy](https://x.com/InfiniStrategy/status/2072724427662569724) described it as "the connective tissue of the next layer of AI tooling." [@ShinkaIoT](https://x.com/ShinkaIoT/status/2072930159242747934) put the friction reduction starkly: "Until today, getting live data from X meant building a custom server, wiring the API, and babysitting connection tokens. Hours of coding for 5 minutes of utility. X just nuked that friction."

The technical implementation uses FastMCP to auto-convert X's OpenAPI specification into MCP tools - the same approach GitHub used, per [Cyberpress](https://cyberpress.org/x-launches-mcp-servers/). [TechCrunch](https://techcrunch.com/2026/06/30/x-now-offers-an-mcp-server-to-make-its-platform-easier-for-ai-tools-to-use/) confirmed documentation lives at docs.x.com/tools/mcp. [Startup Fortune](https://startupfortune.com/x-launches-an-official-mcp-server-and-every-social-platform-will-need-to-follow/) argues this sets a precedent forcing other major platforms to follow. One constraint: Write API and streaming endpoints are excluded, per [TechBuzz AI](https://www.techbuzz.ai/articles/x-launches-mcp-server-to-bridge-ai-apps-and-platform-api/), limiting the server to read-heavy and interactive flows.

Also in the MCP hardware race: Apple released a Safari MCP server on July 3, giving AI agents (Claude, Codex, and other MCP clients) direct access to the live Safari DOM, network data, screenshots, and console through 16 local tools. Per [@PiunikaWeb](https://x.com/PiunikaWeb/status/2072620660786950150): "instead of relying on screenshots or lengthy explanations." Comfy MCP also landed, automating image/video generation via ComfyUI through Claude Code agents - reported by [@gigazine.net](https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22).

### 2. The MCP Protocol Itself Is Undergoing Its Biggest Revision Since Launch

Behind the platform adoption wave, the MCP spec is evolving fast. The [MCP blog](https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/) published beta SDKs for the 2026-07-28 Release Candidate on June 29 - the biggest protocol change since launch. The `initialize` handshake and protocol-level session are being removed; MCP goes fully stateless on standard HTTP, eliminating sticky routing requirements. The ecosystem now has 15,926+ GitHub repos tagged `mcp-server` as of late May 2026. A GitHub MCP Registry has launched for centralized discovery. Per [@SurKopu](https://x.com/SurKopu/status/2072977691910021372): "Think of it as USB-C for AI tools. Build or connect a server once, and Claude can talk to it."

An entry-level example of what this unlocks: a community-built [Namecom-CLI](https://github.com/hypersocialinc/namecom-cli) (HN, 4 pts) is an agent skill letting Claude Code and Codex handle DNS management autonomously. SonicJS v3.0.0-beta.24 added an MCP Server plugin to expose CMS content as AI agent tools. Ethereum developer [HolgerD77](https://x.com/HolgerD77/status/2072715828970082574) announced an MCP server letting AI agents simulate future Ethereum protocol behaviors. The pattern is broadening fast across domains.

### 3. Claude Code's Extension Model Has Three Layers - and Most People Only Know One

The month's most instructive thread of dev.to posts clarifies the three-tier Claude Code extension model that many developers are still conflating. Per the [Anthropic blog post on June 18](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) and community documentation:

- **Skills** = Markdown files dropped into `.claude/commands/` (or namespaced as slash-skills). Anthropic's authoring guide says skills under 2,000 tokens perform best. Lightest-weight option; version-controlled with the project. Per [dev.to/rapls](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon): "a procedure, so it just works."
- **MCP Servers** = standalone protocol-based programs accessed via JSON-RPC/HTTP. For persistent external integrations (databases, internal wikis, deployment pipelines). Per [@lukashanren1](https://x.com/lukashanren1/status/2071900526564831679): "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code - unless you use MCP."
- **Plugins** = bundles combining skills + hooks + subagents + MCP servers into one namespaced installable. Per [dev.to/raxxostudios](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) and [jsmanifest.com](https://jsmanifest.com/claude-code-plugin-packaging-guide): "Most plugin packaging failures stem from treating skills as standalone units." The MCP server registry now lists 400+ community-built servers with top 50 averaging 12,000+ monthly installs, per [dev.to/composiodev](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6).

Claude Code v2.1.199 shipped on July 3 with a significant fix: stacked slash-skills now correctly load all leading skills (previously only the final skill in a stack was loaded). Per [@lukashanren1](https://x.com/lukashanren1/status/2072892044419174704): "Massive reliability & multi-agent fixes."

### 4. The Skills Marketplace Landscape Has Exploded from 1 Registry to 8 in 6 Months

The [agentskills.io](https://agentskills.io/home) open standard - originally from Anthropic, now shared across ~40 products including Claude Code, Codex CLI, Cursor, OpenClaw, Gemini CLI, Goose/Block, Windsurf, and Roo Code - has spawned a marketplace ecosystem in weeks. Per the [Agentman AI ecosystem report](https://agentman.ai/blog/agent-skills-ecosystem-report-2026):

- **Skills.sh** (Vercel-backed, January 2026) - 600,000+ skills, npm-style distribution
- **SkillsMP** - 1.9 million indexed, scraped from public GitHub
- **LobeHub** - 169,000+ skills aggregated
- **claudemarketplace.com** - 150+ curated as of March 2026

The [Agensi complete list](https://www.agensi.io/learn/complete-list-ai-agent-skill-directories-2026) catalogs all eight directories. [wondelai/skills](https://github.com/wondelai/skills) is a primary cross-platform distribution point. SkillsBench analysis of 47,150 public skills found an average quality score of 6.2/12. The one-command CLI installer from agentskills.io works across Claude Code, Codex CLI, Cursor, and OpenClaw, per [codex.danielvaughan.com](https://codex.danielvaughan.com/2026/03/27/codex-cli-skills-ecosystem/).

### 5. Security Is the Coming Crisis for the Skills Ecosystem

The scale comes with a shadow: multiple audits have flagged a significant percentage of publicly available skills as compromised. Snyk's ToxicSkills research (per [agentman.ai](https://agentman.ai/blog/agent-skills-ecosystem-report-2026)) detected prompt injection in **36% of tested skills** from at least one public marketplace. A separate community audit found **140,963 issues across 22,511 skills**, per [rywalker.com](https://rywalker.com/research/agentic-skills-frameworks). The Agentman report predicts H2 2026 competition will shift from catalog size to trust infrastructure, verification, and governance. [dev.to/rapls](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) covers nested tool logic and security pitfalls in practical detail. The [anthropics/claude-code GitHub](https://github.com/anthropics/claude-code/issues/73125) had a high-engagement bug report (297 reactions, 87 comments) about AskUserQuestion timeouts - a sign of how heavily the community stresses the agent interaction layer.

### 6. Power Users Are Running Multi-Agent Setups and New Commands Are Shipping Fast

The "power user" divide is sharpening. [@kashish3097](https://x.com/kashish3097/status/2066393462463942931) (87 likes, 28 reposts) laid out 26 essential Claude Code commands "every developer, builder, and AI workflow operator should know" - framing it as the gap between basic AI assistant usage and workflow mastery. [@dennisdoomen.com](https://bsky.app/profile/dennisdoomen.com/post/3mp6bc7s7yk2x) on Bluesky: "These days it's not uncommon for me to have 3-5 agent sessions running in parallel in JetBrains Junie, Claude Code and GitHub Copilot."

New commands are landing fast. [@richholman.com](https://bsky.app/profile/richholman.com/post/3mpl7meypoc2x) (10 likes) spotted a new `/design-sync` command: "'/design-sync converts a JS/React design system...so the claude.ai/design agent can render it live.'" Cross-tool memory is also emerging as a pain point: LoreConvo ([labyrinthanalyticsconsulting.com](https://bsky.app/profile/labyrinthanalyticsconsulting.com/post/3mpnkwhlgax2p)) is pitching cross-agent context persistence: "Every tool walls off your memory by machine. LoreConvo follows you across Claude Code, Codex, Cursor, and Hermes Agent."

The [one most-upvoted Reddit thread](https://www.reddit.com/r/ClaudeCode/comments/1u1b207/introducing_claude_fable_5/) (r/ClaudeCode, 2,485 pts, 501 comments) is the Anthropic announcement of Claude Fable 5 - a "Mythos-class model" positioned as state-of-the-art on benchmarks. [@cursor_ai](https://x.com/cursor_ai/status/2072403323844428217) confirmed it's back in Cursor with 5,465 likes: "It leads all models on CursorBench, but is the most expensive per task."

### 7. The Cost Reality Is Sobering People Up

[@wenchangyue.bsky.social](https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i) posted a candid cost check that landed widely: "On just this one [Mac]: 5 working days of AI coding (Claude Code + a Codex agent) = ~1 billion tokens, about $1,400 at API list price. More than a US postdoc earns in a week." The Japanese Bluesky post from [@mel-echosphere.bsky.social](https://bsky.app/profile/mel-echosphere.bsky.social/post/3mpldllgso524) reinforced this: Cursor Pro is $20/month, Bugbot is usage-based, and Claude Code requires a subscription or Console. The community is also building cost-attribution tooling: [Lupen](https://github.com/momoraul/Lupen) (HN, 3 pts) shows which specific Claude Code turn or sub-agent ran up your bill.

HN saw a wave of community-built tools this month: [Shipwright Harness](https://github.com/app-vitals/shipwright) (autonomous delivery agent, MIT), [Rondoflow](https://github.com/rondoflow/rondoflow) (visual multi-agent orchestration), [Maccha](https://github.com/KarelTestSpecial/real-agent-setup) (Cross Agent Brain for Antigravity/Claude Code/OpenCode), and [Norrin](https://news.ycombinator.com/item?id=48619320) (Git/diff control). NixOS added [AGENTS.md and CLAUDE.md](https://github.com/NixOS/nixpkgs/pull/534657) to direct LLM agents to its contribution policy. Microsoft VS Code [fixed a Claude agent model picker bug](https://github.com/microsoft/vscode/pull/320294) that was showing only Haiku 4.5.

---

## Cross-Source Patterns

**1. MCP is becoming the universal integration layer for AI agents**
- Platforms: X/Twitter (23 posts), Bluesky (multiple posts), HN (4+ stories), Web (15+ articles)
- The X MCP server launch, Safari MCP launch, Comfy MCP, and growing third-party servers signal that MCP is winning the "AI plugin protocol" race. The upcoming July 28 stateless spec makes it even more deployable.
- Key quote: [@SurKopu](https://x.com/SurKopu/status/2072977691910021372): "Think of it as USB-C for AI tools. Build or connect a server once, and Claude can talk to it."

**2. Skills/plugin ecosystem scaling faster than security can follow**
- Platforms: Web (agentman.ai, rywalker.com), HN
- 36% prompt injection rate (Snyk), 140,963 issues in 22,511 skills, and ~1.9M total indexed skills. The ecosystem scaled from 1 registry to 8 in 6 months.
- Key quote: agentman.ai report: "the second half of 2026 will shift competition from catalog size to trust infrastructure, verification, and governance"

**3. Power-user gap is widening between basic and mastery usage**
- Platforms: X (kashish3097 26 commands thread), Bluesky, Web (claude.com blog)
- The official Anthropic blog post on "Steering Claude Code: skills, hooks, subagents and more" (June 18) and community guides all frame Claude Code as a programmable system most users treat as a chatbot.
- Key quote: [@kashish3097](https://x.com/kashish3097/status/2066393462463942931): "Most people use Claude Code like a basic AI assistant. But power users know the real advantage comes from mastering the commands behind the workflow."

**4. Token cost anxiety is real and driving tooling**
- Platforms: Bluesky (1B tokens/$1,400 post), HN (Lupen cost attribution tool, Codex rate limit bug)
- OpenAI Codex's [rate limit cost surge](https://github.com/openai/codex/issues/28879) (10-20x jump in mid-June, 535 reactions) and [SQLite logging consuming 640 TB/year](https://github.com/openai/codex/issues/28224) (578 reactions) are the highest-engagement GitHub issues in the corpus.
- Key quote: [@wenchangyue.bsky.social](https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i): "5 working days of AI coding = ~1 billion tokens, about $1,400 at API list price. More than a US postdoc earns in a week."

**5. Cross-platform portability is the differentiator for the agentskills.io standard**
- Platforms: Web (agentskills.io, codex.danielvaughan.com, wondelai/skills), HN (Namecom-CLI framed as "agent skill so Claude Code/Codex can do your DNS")
- The one-command installer and ~40-product compatibility is the skills ecosystem's main pitch vs. proprietary plugin systems.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | Introducing Claude Fable 5 | 2,485 | 501 | "a Mythos-class model that we've made safe for general use. Its capabilities exceed those of any model we've ever made generally available" | https://www.reddit.com/r/ClaudeCode/comments/1u1b207/introducing_claude_fable_5/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @cursor_ai | "Claude Fable 5 is available again in Cursor. It leads all models on CursorBench, but is the most expensive per task." | 5,465 | 235 | https://x.com/cursor_ai/status/2072403323844428217 |
| @kashish3097 | "Most people use Claude Code like a basic AI assistant. But power users know the real advantage comes from mastering the commands..." | 87 | 28 | https://x.com/kashish3097/status/2066393462463942931 |
| @kashish3097 | "I wrote 17 free guides that teach [Claude] in hours: Claude 101, Claude Code, Claude Skills, Claude Design..." | 66 | 25 | https://x.com/kashish3097/status/2071831445841256485 |
| @ShinkaIoT | "X AI MCP server is available and it is a real game changer for your agents. AI agents are blind to what's happening right now. Until today..." | 6 | 1 | https://x.com/ShinkaIoT/status/2072930159242747934 |
| @PiunikaWeb | "Apple is making it easier for AI coding assistants to understand what is happening inside Safari... a new Model Context Protocol server" | 4 | 1 | https://x.com/PiunikaWeb/status/2072620660786950150 |
| @lukashanren1 | "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code - unless you use MCP." | 3 | 0 | https://x.com/lukashanren1/status/2071900526564831679 |
| @lukashanren1 | "Every Claude Code conversation is written to disk as it happens - not summarized, not compressed, but as a precise line-by-line JSONL transcript." | 3 | 0 | https://x.com/lukashanren1/status/2072622596193968605 |
| @lukashanren1 | "Claude Code v2.1.199! Massive reliability & multi-agent fixes. Stacked slash-skills now load all leading skills" | 0 | 0 | https://x.com/lukashanren1/status/2072892044419174704 |
| @InfiniStrategy | "X launched hosted MCP servers on June 30, becoming the first major platform to expose over 200 API endpoints through Anthropic's Model Context Protocol." | 2 | 1 | https://x.com/InfiniStrategy/status/2072724427662569724 |
| @SurKopu | "MCP stands for Model Context Protocol. An open standard Anthropic released in November 2024...Think of it as USB-C for AI tools." | 1 | 0 | https://x.com/SurKopu/status/2072977691910021372 |
| @Onose980 | "With the launch of @pacifica_fi MCP, AI agents can now analyze markets, understand users account and execute trades using nothing more than natural language." | 19 | 0 | https://x.com/Onose980/status/2072740932404031964 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| HN | Show HN: Visual multi-agent orchestration for Claude Code | 5 | 0 | — | https://github.com/rondoflow/rondoflow |
| HN | Show HN: Maccha – Cross Agent Brain for Antigravity, Claude Code, OpenCode etc. | 5 | 2 | — | https://github.com/KarelTestSpecial/real-agent-setup |
| HN | Norrin – Git/diff control in Claude Code | 4 | 1 | — | https://news.ycombinator.com/item?id=48619320 |
| HN | Show HN: Namecom-CLI – CLI and agent skill so Claude Code/Codex can do your DNS | 4 | 0 | — | https://github.com/hypersocialinc/namecom-cli |
| HN | Lumen – A Binary Alternative to JSON-RPC for Model Context Protocol (MCP) | 4 | 0 | — | https://github.com/GonzaloMonzonC/lumen-protocol/ |
| HN | Shipwright Harness – open-source autonomous delivery agent for Claude Code (MIT) | 3 | 0 | — | https://github.com/app-vitals/shipwright |
| HN | Show HN: Lupen – which Claude Code turn or sub-agent ran up your bill | 3 | 0 | — | https://github.com/momoraul/Lupen |
| HN | Gemini CLI vs. Claude Code: Why agent capabilities matter more than prompts | 3 | 0 | — | https://imaxxs.com/behavioral-induction-capabilities-shape-execution |
| HN | Claude Code Issue management extension for VS Code | 3 | 1 | — | https://www.forq.ink/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @sexabolition.blog | "One of my favourite things about Claude Code is that the user experience really reinvents the Hacker man scrolling source code experience..." | 27 | https://bsky.app/profile/sexabolition.blog/post/3mpjtnp4azc2k |
| @gigazine.net | "Comfy MCP登場、ComfyUIを使った画像・動画生成の自動化がClaude Codeで可能に" | 7 | https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22 |
| @richholman.com | "Claude Code/Design now have a sync command: '/design-sync converts a JS/React design system...so the claude.ai/design agent can render it live'" | 10 | https://bsky.app/profile/richholman.com/post/3mpl7meypoc2x |
| @wenchangyue.bsky.social | "5 working days of AI coding (Claude Code + a Codex agent) = ~1 billion tokens, about $1,400 at API list price. More than a US postdoc earns in a week." | 3 | https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i |
| @dennisdoomen.com | "These days it's not uncommon for me to have 3-5 agent sessions running in parallel in JetBrains Junie, Claude Code and GitHub Copilot." | 2 | https://bsky.app/profile/dennisdoomen.com/post/3mp6bc7s7yk2x |
| @labyrinthanalyticsconsulting.com | "Every tool walls off your memory by machine. LoreConvo follows you across Claude Code, Codex, Cursor, and Hermes Agent -- the same context, everywhere you work." | 1 | https://bsky.app/profile/labyrinthanalyticsconsulting.com/post/3mpnkwhlgax2p |
| @web-standards.dev | "Introducing the Safari MCP server for web developers. Saron Yitbarek presents a Model Context Protocol server giving AI agents access to the DOM..." | 0 | https://bsky.app/profile/web-standards.dev/post/3mpqbyjpz4v27 |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| anthropics/claude-code | [FEATURE] Official Claude Desktop build for Linux (Ubuntu LTS / Debian) | 651 | 50 | https://github.com/anthropics/claude-code/issues/65697 |
| openai/codex | Codex SQLite feedback logs can write ~640 TB/year and rapidly consume SSD endurance | 578 | 129 | https://github.com/openai/codex/issues/28224 |
| openai/codex | Codex (gpt-5.5, Plus plan) — rate-limit cost per token jumped ~10-20x since June 16 | 535 | 197 | https://github.com/openai/codex/issues/28879 |
| anthropics/claude-code | [BUG] AskUserQuestion: "No response after 60s — continued without an answer" | 297 | 87 | https://github.com/anthropics/claude-code/issues/73125 |
| caezium/Burrow | Please remove mole.fit references and original UI design from this project | 308 | 46 | https://github.com/caezium/Burrow/issues/36 |
| NixOS/nixpkgs | docs: add AGENTS.md and symlink CLAUDE.md | 49 | 20 | https://github.com/NixOS/nixpkgs/pull/534657 |
| microsoft/vscode | agentHost: fix Claude agent window showing only Haiku 4.5 in model picker | 6 | 4 | https://github.com/microsoft/vscode/pull/320294 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| TechCrunch | https://techcrunch.com/2026/06/30/x-now-offers-an-mcp-server-to-make-its-platform-easier-for-ai-tools-to-use/ | X MCP server launch: 200+ endpoints, OAuth/xurl, docs.x.com/tools/mcp |
| The Next Web | https://thenextweb.com/news/x-hosted-mcp-server-ai-tools-api | Hosted server means no developer infra required; dual-server architecture |
| Cyberpress | https://cyberpress.org/x-launches-mcp-servers/ | FastMCP auto-converts OpenAPI spec; same approach as GitHub's MCP server |
| Startup Fortune | https://startupfortune.com/x-launches-an-official-mcp-server-and-every-social-platform-will-need-to-follow/ | Sets precedent for all platforms; positions X as early mover |
| TechBuzz AI | https://www.techbuzz.ai/articles/x-launches-mcp-server-to-bridge-ai-apps-and-platform-api | Write API excluded; scoped to read-heavy and interactive use cases |
| Anthropic (claude.com) | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | Official blog: CLAUDE.md, skills, hooks, rules, subagents model (June 18) |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/sdk-betas-2026-07-28/ | Beta SDKs for July 28 RC: stateless protocol, no initialize handshake |
| DEV (rapls) | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Decision framework: skill vs MCP vs plugin vs CLI, lightest-first |
| DEV (promptmaster) | https://dev.to/promptmaster/the-claude-code-configuration-stack-beyond-claudemd-4i08 | Claude Code as fully programmable system with multi-layer config stack |
| jsmanifest | https://jsmanifest.com/claude-code-plugin-packaging-guide | Plugin packaging: bundling skills + hooks + subagents + MCP into plugins |
| Octavius AI | https://octavius.ai/ai-automation/claude-code-skills-vs-plugins-2/ | Skills vs Plugins vs Subagents: when to use each (9 months experience) |
| Agentman AI | https://agentman.ai/blog/agent-skills-ecosystem-report-2026 | Ecosystem report: 8 marketplaces, 1.9M skills, 36% prompt injection rate |
| Agent Skills IO | https://agentskills.io/home | Open standard spec: 40+ products, cross-platform portability |
| Agensi | https://www.agensi.io/learn/complete-list-ai-agent-skill-directories-2026 | Complete list of all 8 skills marketplaces and directories |
| RY Walker | https://rywalker.com/research/agentic-skills-frameworks | Security audit: 140,963 issues in 22,511 skills across community audit |
| DEV (williamwangai) | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP guide; skills best under 2,000 tokens per Anthropic |
| DEV (raxxostudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills & plugins 2026; claudemarketplace.com has 150+ skills |
| DEV (composiodev) | https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 | 10 top plugins; registry 400+ servers, top 50 average 12K monthly installs |
| DEV (contrite42) | https://dev.to/contrite42/claude-code-as-a-daily-driver-claudemd-skills-subagents-plugins-and-mcp-nnf | Claude Code as "AI OS": full extension ecosystem walkthrough |
| DEV (axitslab) | https://dev.to/axitslab/our-claude-code-setup-30-skills-mcps-and-self-learning-hooks-5gje | Production setup: 30 custom skills + MCPs + self-learning hooks |
| Wondelai (GitHub) | https://github.com/wondelai/skills | Cross-platform skills repo (Claude Code, Codex CLI, Cursor, OpenClaw, Hermes) |
| Daniel Vaughan | https://codex.danielvaughan.com/2026/03/27/codex-cli-skills-ecosystem/ | Codex CLI + agentskills.io in practice; one-command cross-tool installer |
| niteagent.com | https://niteagent.com | Agent tooling coverage (engine-returned) |
| ayautomate.com | https://ayautomate.com | Agent automation coverage (engine-returned) |
| shawnmayzes.com | https://shawnmayzes.com | Claude Code workflow coverage (engine-returned) |

---

## Stats Block

```
├─ 🟠 Reddit: 1 thread │ 2,485 upvotes │ 501 comments
├─ 🔵 X: 23 posts │ 7,115 likes │ 332 reposts
├─ 🟢 HN: 20 stories │ 102 points │ 11 comments
├─ 🦋 Bluesky: 13 posts │ 81 likes │ 1 repost
├─ 🐙 GitHub: 12 items │ 2,839 reactions │ 836 comments
├─ 🌐 Web: 25 pages
└─ 🗣️ Top voices: @cursor_ai, @kashish3097, @lukashanren1 │ r/ClaudeCode
```

---

## Data Gaps

- **YouTube: 0 videos** - Multiple search attempts failed (yt-dlp returned 0 results, ScrapeCreators returned 402 errors). This is a real gap; YouTube has substantial Claude Code tutorial content not captured here.
- **TikTok: 0 videos** - ScrapeCreators returned HTTP 402 Payment Required errors on all hashtag searches. TikTok coverage is absent.
- **Instagram: 0 reels** - Same 402 errors. Instagram coverage is absent.
- **Reddit: very thin** - Only 1 thread captured despite targeting r/ClaudeCode, r/ClaudeAI, r/ChatGPTCoding, r/LocalLLaMA, r/singularity. The dedicated-subreddit lanes returned 0 posts, suggesting a Reddit scraping limitation. This is a material gap - r/ClaudeAI and r/LocalLLaMA likely have dozens of relevant threads.
- **Freshness**: Only 36 of 78 dated engine items are from the past 7 days; the other 42 are from the June 3-26 window. The week of June 30 - July 3 is better covered via X and Bluesky than the earlier part of the 30-day window.
- **Coverage estimate**: ~60-65% of the topic's actual community discussion, given Reddit and YouTube gaps. The MCP server and skills marketplace themes are well-covered; the "power user workflows" thread is thin without Reddit depth.

---

## Key Quotes

> "Think of it as USB-C for AI tools. Build or connect a server once, and Claude can talk to it." — [@SurKopu](https://x.com/SurKopu/status/2072977691910021372) on X

> "Until today, getting live data from X meant building a custom server, wiring the API, and babysitting connection tokens. Hours of coding for 5 minutes of utility. X just nuked that friction." — [@ShinkaIoT](https://x.com/ShinkaIoT/status/2072930159242747934) on X

> "Most people use Claude Code like a basic AI assistant. But power users know the real advantage comes from mastering the commands behind the workflow." — [@kashish3097](https://x.com/kashish3097/status/2066393462463942931) on X

> "5 working days of AI coding (Claude Code + a Codex agent) = ~1 billion tokens, about $1,400 at API list price. More than a US postdoc earns in a week." — [@wenchangyue.bsky.social](https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i) on Bluesky

> "Every tool walls off your memory by machine. LoreConvo follows you across Claude Code, Codex, Cursor, and Hermes Agent -- the same context, everywhere you work." — [@labyrinthanalyticsconsulting.com](https://bsky.app/profile/labyrinthanalyticsconsulting.com/post/3mpnkwhlgax2p) on Bluesky

> "One of my favourite things about Claude Code is that the user experience really reinvents the Hacker man scrolling source code experience for people who imagine that's what technical work entails." — [@sexabolition.blog](https://bsky.app/profile/sexabolition.blog/post/3mpjtnp4azc2k) on Bluesky

> "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code - unless you use MCP." — [@lukashanren1](https://x.com/lukashanren1/status/2071900526564831679) on X

> "the second half of 2026 will shift competition from catalog size to trust infrastructure, verification, and governance" — [Agentman AI ecosystem report](https://agentman.ai/blog/agent-skills-ecosystem-report-2026) on agent skills marketplaces

> "Stacked slash-skills now load all leading skills" — [@lukashanren1](https://x.com/lukashanren1/status/2072892044419174704) on Claude Code v2.1.199 release notes

> "Claude Fable 5 is available again in Cursor. It leads all models on CursorBench, but is the most expensive per task." — [@cursor_ai](https://x.com/cursor_ai/status/2072403323844428217) on X (5,465 likes)
