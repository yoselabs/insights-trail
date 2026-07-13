# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-13
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 3 threads | 83 upvotes, 15 comments | Partial — SC backup also failed |
| X/Twitter | 17 posts | 2,110 likes, 100 reposts | Full coverage via Bird auth |
| Hacker News | 6 stories | 228 points, 96 comments | |
| Bluesky | 4 posts | 24 likes, 5 reposts | |
| GitHub | 14 items | 812 reactions, 439 comments | No token; unauthenticated tier |
| Web | 20 pages | — | 10 engine + 10 WebSearch supplemental |
| YouTube | 0 videos | — | HTTP 402 error |
| TikTok | 0 videos | — | HTTP 402 error |
| Instagram | 0 reels | — | HTTP 402 error |
| Polymarket | 0 markets | — | No relevant markets found |

---

## Synthesized Findings

### 1. MCP Has Won the Protocol War — Now It's About the Plumbing

The Model Context Protocol landed in November 2024 and has since become the de facto standard for connecting AI agents to external tools. By mid-2026, Glama alone indexed close to 20,000 MCP servers and the MCP SDKs were pulling ~97 million downloads per month. Every major coding editor (Cursor, VS Code, Zed, JetBrains) ships a native MCP client; every major agent framework (LangGraph, OpenAI Agents SDK, Anthropic's own Agent SDK) speaks MCP natively. [OrbMarket on X](https://x.com/orbserv/status/2069439656039682105) framed the moment well: "More services. More opportunities. A stronger agent economy."

[@TechWithTimm](https://x.com/TechWithTimm/status/2076311802695299204) (69 likes) put it bluntly: "MCP is becoming one of the most important skills for AI developers. So let me show you how to build an MCP server in Python, connect it to Claude Code, add OAuth authentication, and store user-specific data in a database." The conceptual framing keeping this alive on X: [@automatedmarktr](https://x.com/automatedmarktr/status/2076351476662768110) summed it up as: "Here's the thing people miss about Claude Code: it's not smart because of the model, it's smart because of what it's connected to. MCP servers are the bridge between Claude and the real world. Without it, Claude only knows what you paste in. With it, Claude can see, read, write, and act."

The [official MCP Registry](https://registry.modelcontextprotocol.io/) is now live, but it's competing with a fragmented layer of discovery infrastructure: Smithery, Glama, mcp.so, MCPTotal, and LobeHub all compete as registry/marketplace plumbing. Less than 5% of MCP servers are monetized, per [Tool Directory AI](https://tooldirectory.ai/blog/state-of-mcp-servers-2026). The next convergence point is auth — Google's mid-2026 remote MCP server for Gemini uses OAuth 2.0 and IAM with audit logging, and that pattern is becoming the template.

Cross-platform: Reddit, X, HN, Bluesky, Web, GitHub all discussed this theme.

---

### 2. awesome-mcp-servers: 90K Stars in 8 Months Is the Community Signal

The most concrete engagement spike in the research window: [@ArchiveExplorer](https://x.com/ArchiveExplorer/status/2076418069828616605) (36 likes) with a thread that reads like a war cry — "YOUR CLAUDE CAN NOW USE HUNDREDS OF EXTERNAL TOOLS. ONE PASTE. FREE. Glama-ai founder built the de-facto directory every MCP tool ends up on. no vendor lock-in, no signup gates. It's called awesome-mcp-servers. Frank Fiegel launched it November 2024. 90K stars in 8 months." The community's excitement is specifically about the zero-friction install pattern: browse the list, pick a server, paste the config into `~/.claude.json`.

[VoltAgent's awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) curates 1,000+ agent skills compatible with Claude Code, Codex, Gemini CLI, Cursor, and more. [rohitg00's awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) now lists 135 agents, 35 curated skills, 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, and 26 companion apps. The curator arms race is real.

A DevOps-specific version surfaced in [r/sre](https://www.reddit.com/r/sre/comments/1utcfbl/built_a_curated_list_of_official_devops_cloud_sre/) (54 upvotes, 10 comments): "Built a curated list of official DevOps / Cloud / SRE MCP servers and agent skills — organizing official MCP servers, agent skills, and agent toolkits for DevOps, cloud, platform engineering, SRE, security, IaC, observability, and diagramming workflows."

Cross-platform: X, Reddit, GitHub, Web.

---

### 3. Claude Code Plugin Architecture Is Crystallizing Around a Four-Part Bundle

The community has converged on a plugin model with four components: skills (SKILL.md instruction files), agents (subagent configurations), hooks (event handlers), and MCP servers — bundled into a versioned, installable unit. [UX Planet](https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda) laid it out flat in July 2026: the four parts of a Claude Code plugin are Skills, Agents, Hooks, and MCP servers, with use cases including code review, frontend coding, release and QA automation, and team onboarding.

[@erikdarling.com on Bluesky](https://bsky.app/profile/erikdarling.com/post/3mqc5npb36l2m) (10 likes, 4 reposts) demonstrated the install flow in practice: "built a claude code plugin that reads sql server execution plans and tells you what's wrong. `/plugin marketplace add erikdarlingdata/claude-plugins` `/plugin install sqlserver-query-plans@erikdarling` then run `/reload-plugins` and just point it at a .sqlplan file." The `/plugin marketplace add owner/repo` command pattern is the current distribution primitive.

[hidekazu-konishi.com](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html) documented the team distribution path: "Most Claude Code customization starts as a private habit" and describes how skills + hooks + agents get packaged into shareable plugin bundles. [Warp terminal's GitHub issue](https://github.com/warpdotdev/warp/issues/12868) shows demand spreading: requesting "Plugin/marketplace packaging: bundle skills + commands + hooks + MCP into installable units (Claude-Code/Codex-compatible)" — Warp already ships skills but wants the full plugin distribution path.

Cross-platform: X, Bluesky, GitHub, Reddit, Web.

---

### 4. Vercel skills.sh Is the npm Moment for Agent Skills

On June 5, 2026, Vercel's skills.sh went GA with 600,000 open-source skills distributed via Vercel OIDC. The install mechanic: `npx skills add <package>`. Per [Vercel's changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem), skills.sh is positioned as a discovery and distribution layer compatible with Claude Code, Codex, Cursor, GitHub Copilot, and 69+ other agents — the npm-for-agent-skills pitch.

[Totalum Blog](https://www.totalum.app/blog/agent-skills-marketplaces-2026) mapped the competitive landscape: five marketplaces that matter in 2026 are Anthropic (Claude Code plugins), Vercel (skills.sh), OpenAI (Codex plugins), Cline (CLI 3.0.16 with bundling), and the MCP ecosystem (Smithery, Glama, LobeHub, SkillsMP). Meanwhile [claudemarketplaces.com](https://claudemarketplaces.com/) has 2,500+ GitHub-based community marketplaces registered, "with quality ranging from excellent to abandoned."

[r/WebAfterAI](https://www.reddit.com/r/WebAfterAI/comments/1uuk5fm/10_claude_code_skill_repos_for_solo_founders/) (solo-founder weekend post, July 12) distilled the skill format to its core: "A skill is a folder with a SKILL.md file that teaches your coding agent how to do one thing well, and you install it into `.claude/skills/`. For a solo founder trying to ship by Sunday, the right stack turns one person plus Claude Code into something that scaffolds, builds, tests, reviews, and launches."

Cross-platform: Reddit, X, Web.

---

### 5. Zero-Auth MCP Servers Are Winning Against Configuration Hell

The top-scored X cluster was about Zambo MCP — [@CripdoeCrypto](https://x.com/CripdoeCrypto/status/2076389085720072421) (7 likes, 2 reposts): "why people actually pick Zambo MCP over everything else: 1/ one URL. Zero auth. 50+ tools. other MCP servers want OAuth, API keys, config hell. Zambo is one paste: `{"mcpServers":{"zambo":{"url":"..."}}}` 30 seconds and Claude has 50+ new capabilities." The thread lists specific tools: live web search, contractor leads, document analysis — things that actually matter to practitioners.

In the same vein, a second [@CripdoeCrypto post](https://x.com/CripdoeCrypto/status/2076472729939652735) pitched an MCP infrastructure layer giving Claude, Cursor, and Windsurf "65+ live tools — web search, on-chain data, lead gen, agent coordination, and AI strategy — for free, no API key required." The zero-friction install pattern is the strongest current demand signal in the MCP space: auth is a barrier, and the tools removing it are getting traction.

HN's Show HN entries corroborate the appetite for purpose-specific MCP servers: [Tilion MCP](https://github.com/tiliondev/fortress/tree/main/mcp) (6 pts) stops Claude Code from being blocked on the web; [TS Compiler Graph MCP](https://github.com/samchon/ttsc/tree/master/packages/graph) (3 pts) claims 10x fewer tokens for TypeScript-heavy work; [Pulse](https://github.com/nikitadoudikov/claude-pulse) (39 pts, 15 comments) lets you approve Claude tool calls from your phone.

Cross-platform: X, HN.

---

### 6. Context Budget Pressure Is Creating Operational Skill Management

A new operational concern is crystallizing: unused MCP servers and skills silently consume context budget. [@4Ndr3w10000 on X](https://x.com/4Ndr3w10000/status/2076275885582569874): "Claude Code /doctor is no longer a read-only report. It now diagnoses issues and fixes them. It also flags unused skills, MCP servers, and plugins against their context cost. Run it when your setup feels heavy. Dead MCP servers quietly eat your context budget."

This is a natural consequence of the ecosystem maturing — developers accumulate plugins and then need tooling to audit what they're paying for in context. The `/doctor` command now serving as a plugin health audit is a meaningful product signal from Anthropic.

[startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) crystallized the decision framework: "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." That framework is exactly what developers with a growing plugin inventory need.

The anthropics/claude-ai-mcp GitHub repo shows ongoing friction: [tools not surfaced to the model in claude.ai web](https://github.com/anthropics/claude-ai-mcp/issues/476) (11 reactions, 21 comments) and [inability to remove the Claude Code remote connector](https://github.com/anthropics/claude-ai-mcp/issues/509) (9 reactions, 12 comments) are the top pain points.

Cross-platform: X, GitHub, Web.

---

### 7. Google's Stitch Agent Skills, "The Log Is the Agent," and the Ecosystem Spreading Beyond Claude

The ecosystem is visibly spreading. [@0x_Missy22](https://x.com/0x_Missy22/status/2076231166492049711): "GitHub trending rn is wild — Claude Code templates, Google's Stitch agent skills, MCP servers with terminal control. All in the same day. The AI coding tooling layer went from zero to an entire ecosystem and nobody noticed until it was everywhere."

HN's top story in the window — [The Log Is the Agent](https://arxiv.org/abs/2605.21997) (114 pts, 50 comments) — is the key conceptual paper arguing that structured execution logs are the canonical state representation for autonomous agents. It provides theoretical grounding for the skill/plugin approach: skills encode behavior, logs encode state, and the combination is what makes long-horizon agent work tractable.

[Gentle-AI](https://x.com/N0V4Dev/status/2076473717358502170) (Go-based ecosystem configurator) "works with 15 different agents like Claude Code, OpenCode, and Cursor. It adds curated coding skills and MCP servers to your setup. You can even switch AI providers easily within your workflow." Spree Commerce 5.5 shipped Agent Skills for e-commerce. Storybook is building [Claude Code + Codex plugins](https://bsky.app/profile/storybook.js.org/post/3mqaesef2dk2u) for agentic frontend review. [Obra's Superpowers](https://bsky.app/profile/foursignalsdev.bsky.social/post/3mqemgrmm2o2j) — a spec-plan-execute-review cycle to cut hallucinations — shipped plugins for Claude Code, Cursor, and Copilot CLI.

Cross-platform: X, Bluesky, HN, Reddit.

---

### 8. alexalbert__ and "Managing a Team" — The Mental Model Shift

[@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (557 likes, 44 replies, June 23) with the highest-resonance quote in the corpus: "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." No product name, no link — just the mental model shift. It landed because the plugin/skill ecosystem is what makes that feeling possible: you're not prompting a model, you're orchestrating a configured agent with persistent capabilities.

The [Making of Claude Code](https://www.anthropic.com/features/making-of-claude-code) (HN: 61 pts, 31 comments, July 7) surfaced in the same window — Anthropic's behind-the-scenes look at how Claude Code was built, which generated significant community discussion about the design choices that enabled the plugin architecture.

Cross-platform: X, HN.

---

## Cross-Source Patterns

**Pattern 1: Zero-friction install as the primary competitive axis for MCP servers**
The community's strongest approval signal goes to MCP servers that require zero auth and a single paste. Zambo (one URL, 50+ tools), awesome-mcp-servers (browse + copy config), Glama (no signup gate), Zambo MCP's infrastructure competitor (65+ tools, no API key). The friction of OAuth and credential management is explicitly named as the reason people pick alternatives.
- X: [@CripdoeCrypto](https://x.com/CripdoeCrypto/status/2076389085720072421), [@ArchiveExplorer](https://x.com/ArchiveExplorer/status/2076418069828616605)
- HN: Tilion, TS Compiler Graph, Pulse

**Pattern 2: Skill/plugin format is converging on SKILL.md + four-component bundle**
Independently across Reddit, Bluesky, Web, and GitHub: the description of what a plugin is keeps converging on the same four parts (skills, agents, hooks, MCP). The install CLI command `/plugin marketplace add owner/repo` is the emerging primitive.
- Reddit: [r/WebAfterAI](https://www.reddit.com/r/WebAfterAI/comments/1uuk5fm/10_claude_code_skill_repos_for_solo_founders/)
- Bluesky: [@erikdarling.com](https://bsky.app/profile/erikdarling.com/post/3mqc5npb36l2m)
- GitHub: [warpdotdev/warp#12868](https://github.com/warpdotdev/warp/issues/12868)
- Web: [hidekazu-konishi.com](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html), [uxplanet.org](https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda)

**Pattern 3: Context budget pressure from plugin sprawl**
Emerging operational concern across X and GitHub: developers accumulating plugins and paying a context tax for unused ones. Anthropic's /doctor update (flags plugins against context cost) and GitHub issues about connector management both reflect this.
- X: [@4Ndr3w10000](https://x.com/4Ndr3w10000/status/2076275885582569874)
- GitHub: [claude-ai-mcp#509](https://github.com/anthropics/claude-ai-mcp/issues/509), [claude-ai-mcp#476](https://github.com/anthropics/claude-ai-mcp/issues/476)

**Pattern 4: "MCP is the most important new dev skill" narrative**
Multiple unaffiliated voices (X, HN, Web tutorials) describing MCP server building as a high-value developer skill, not just a configuration task. Python MCP tutorials, "The Log Is the Agent" paper, and practitioner threads all reinforce this.
- X: [@TechWithTimm](https://x.com/TechWithTimm/status/2076311802695299204) (69 likes), [@KirkDBorne](https://x.com/KirkDBorne/status/2076503036789223675)
- HN: [The Log Is the Agent](https://arxiv.org/abs/2605.21997) (114 pts)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/WebAfterAI | 10 Claude Code skill repos for solo founders shipping this weekend | 1 | — | "A skill is a folder with a SKILL.md file that teaches your coding agent how to do one thing well" | [link](https://www.reddit.com/r/WebAfterAI/comments/1uuk5fm/10_claude_code_skill_repos_for_solo_founders/) |
| r/sre | Built a curated list of official DevOps / Cloud / SRE MCP servers and agent skills | 54 | 10 | "organizing official MCP servers, agent skills, and agent toolkits for DevOps, cloud, platform engineering" | [link](https://www.reddit.com/r/sre/comments/1utcfbl/built_a_curated_list_of_official_devops_cloud_sre/) |
| r/rails | Spree 5.5 with Admin API, new CLI and Agent Skills released! | 28 | 5 | "a release built around two themes: a faster, smoother developer experience for both developers and AI agents" | [link](https://www.reddit.com/r/rails/comments/1u98a6a/spree_55_with_admin_api_new_cli_and_agent_skills/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 557 | 15 | [link](https://x.com/alexalbert__/status/2069470389391241314) |
| @alexalbert__ | "More Fable!" | 677 | 8 | [link](https://x.com/alexalbert__/status/2075285305096343583) |
| @alexalbert__ | "Welcome back to the world Fable!!" | 593 | 10 | [link](https://x.com/alexalbert__/status/2072404717490360727) |
| @abir35627 | "🚀 The ultimate Claude resource collection is here!" | 58 | 22 | [link](https://x.com/abir35627/status/2076241018450784751) |
| @TechWithTimm | "MCP is becoming one of the most important skills for AI developers" | 69 | 9 | [link](https://x.com/TechWithTimm/status/2076311802695299204) |
| @ArchiveExplorer | "YOUR CLAUDE CAN NOW USE HUNDREDS OF EXTERNAL TOOLS. ONE PASTE. FREE... awesome-mcp-servers. 90K stars in 8 months." | 36 | 2 | [link](https://x.com/ArchiveExplorer/status/2076418069828616605) |
| @abir35627 | "Claude Code Resource Bible — 54 powerful tools, MCP servers, Skills & automation" | 14 | 7 | [link](https://x.com/abir35627/status/2076605147984359877) |
| @xxwessentials | "Agent Zero" | 29 | 9 | [link](https://x.com/xxwessentials/status/2072347979768381673) |
| @orbserv | OrbMarket welcoming @xona_agent — "More services. A stronger agent economy." | 44 | 10 | [link](https://x.com/orbserv/status/2069439656039682105) |
| @suraj_sharma14 | "Everything you need to master in 2026: Claude Code + OpenClaw workflows, Hermes Agent, MCP servers..." | 11 | 0 | [link](https://x.com/suraj_sharma14/status/2076592477276922070) |
| @CripdoeCrypto | "why people actually pick Zambo MCP over everything else: 1/ one URL. Zero auth. 50+ tools." | 7 | 2 | [link](https://x.com/CripdoeCrypto/status/2076389085720072421) |
| @CripdoeCrypto | "MCP infrastructure layer...65+ live tools...for free, no API key required" | 5 | 3 | [link](https://x.com/CripdoeCrypto/status/2076472729939652735) |
| @4Ndr3w10000 | "Dead MCP servers quietly eat your context budget." | — | — | [link](https://x.com/4Ndr3w10000/status/2076275885582569874) |
| @0x_Missy22 | "GitHub trending rn is wild — Claude Code templates, Google's Stitch agent skills, MCP servers with terminal control." | — | — | [link](https://x.com/0x_Missy22/status/2076231166492049711) |
| @KirkDBorne | "Learn Model Context Protocol [MCP] with Python — the new standard for AI Capabilities" | 8 | 3 | [link](https://x.com/KirkDBorne/status/2076503036789223675) |
| @automatedmarktr | "Here's the thing people miss about Claude Code: it's not smart because of the model, it's smart because of what it's connected to." | 2 | 0 | [link](https://x.com/automatedmarktr/status/2076351476662768110) |
| @N0V4Dev | "Gentle-AI is an ecosystem configurator for AI coding agents...works with 15 different agents like Claude Code, OpenCode, Cursor." | — | 0 | [link](https://x.com/N0V4Dev/status/2076473717358502170) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| iacguy | The Log is the Agent | 114 | 50 | Structured logs as canonical state representation for autonomous agents | [link](https://arxiv.org/abs/2605.21997) |
| kanamekun | The Making of Claude Code | 61 | 31 | Anthropic's design story behind Claude Code's extensible architecture | [link](https://www.anthropic.com/features/making-of-claude-code) |
| nikitadvd | Show HN: Pulse – Dashboard for Claude Code, approve tool calls from your phone | 39 | 15 | Mobile approval UI for Claude tool calls | [link](https://github.com/nikitadoudikov/claude-pulse) |
| arhamshahrier | Show HN: Tilion – MCP for Claude Code to stop it getting blocked on the web | 6 | — | Anti-blocking MCP layer | [link](https://github.com/tiliondev/fortress/tree/main/mcp) |
| piotrgrudzien | Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | — | Expose any agent as an MCP server | [link](https://quickchat.ai/post/expose-ai-agent-as-mcp-server) |
| autobe | Show HN: I Made TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | — | TypeScript-aware MCP for token efficiency | [link](https://github.com/samchon/ttsc/tree/master/packages/graph) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @erikdarling.com | "built a claude code plugin that reads sql server execution plans and tells you what's wrong. /plugin marketplace add erikdarlingdata/claude-plugins" | 10 | [link](https://bsky.app/profile/erikdarling.com/post/3mqc5npb36l2m) |
| @storybook.js.org | "The frontend bottleneck is no longer code generation. It's now reviewing the output of an agent. Storybook is working on: Claude Code + Codex plugins" | 8 | [link](https://bsky.app/profile/storybook.js.org/post/3mqaesef2dk2u) |
| @kjaanson.eurosky.social | "Does Claude Code and other mainstream harnesses without plugins etc handle cache nicely?" | 5 | [link](https://bsky.app/profile/kjaanson.eurosky.social/post/3mqel6rljbs2v) |
| @foursignalsdev.bsky.social | "Obra's Superpowers...spec-plan-execute-review cycle to cut hallucinations. Now plugins for Claude Code, Cursor, Copilot CLI." | 1 | [link](https://bsky.app/profile/foursignalsdev.bsky.social/post/3mqemgrmm2o2j) |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| anthropics/claude-code | [BUG] No response from API error when Advisor is triggered | 83 | 47 | [link](https://github.com/anthropics/claude-code/issues/69238) |
| openai/codex | Rate-limit cost per token jumped ~10-20x since June 16 | 550 | 206 | [link](https://github.com/openai/codex/issues/28879) |
| anomalyco/opencode | OpenCode v1.17.10 crashes with Bun segfault on Windows | 47 | 52 | [link](https://github.com/anomalyco/opencode/issues/33742) |
| anthropics/claude-ai-mcp | Custom remote MCP connector: tools never surfaced to model in claude.ai web | 11 | 21 | [link](https://github.com/anthropics/claude-ai-mcp/issues/476) |
| anthropics/claude-code | [Bug] Potential session/cache leakage between workspace instances | 49 | 18 | [link](https://github.com/anthropics/claude-code/issues/74066) |
| anthropics/claude-ai-mcp | Cannot remove claude code remote custom connector | 9 | 12 | [link](https://github.com/anthropics/claude-ai-mcp/issues/509) |
| kirodotdev/Kiro | MCP stdio servers spawn visible CMD windows on Windows | 13 | 31 | [link](https://github.com/kirodotdev/Kiro/issues/9713) |
| warpdotdev/warp | Plugin/marketplace packaging: bundle skills + commands + hooks + MCP into installable units | 1 | 3 | [link](https://github.com/warpdotdev/warp/issues/12868) |
| PostHog/posthog | feat(skills): Claude Code & Codex plugin marketplace + zip export | — | 7 | [link](https://github.com/PostHog/posthog/pull/64385) |
| frankxai/agentic-creator-os | v12: Open-Core Reset — 100+ skills, ~70 commands, ~65 agents, 459 unique cloners | — | 1 | [link](https://github.com/frankxai/agentic-creator-os/pull/32) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| UX Planet | [link](https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda) | Four-part plugin anatomy: Skills + Agents + Hooks + MCP; practical use cases |
| Start Debugging | [link](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) | Decision framework: skill=behavior, subagent=context, MCP=external system access |
| Design Revision | [link](https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents) | Claude Code Skills vs Plugins vs Agents vs MCP comparison guide |
| hidekazu-konishi.com | [link](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html) | Team distribution guide: bundling skills + hooks + agents + MCP for orgs |
| DeepWiki | [link](https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery) | Plugin marketplace and discovery architecture (last indexed July 1) |
| MCP Registry | [link](https://registry.modelcontextprotocol.io/) | Official Anthropic MCP server registry |
| Vercel Changelog | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh GA announcement: 600K OSS skills, `npx skills add`, 69+ agents |
| Totalum Blog | [link](https://www.totalum.app/blog/agent-skills-marketplaces-2026) | Marketplace comparison: Anthropic vs Vercel vs OpenAI vs Cline vs MCP registries |
| VoltAgent GitHub | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ curated agent skills across Claude Code, Codex, Gemini CLI, Cursor |
| Awesome Claude Code Toolkit | [link](https://github.com/rohitg00/awesome-claude-code-toolkit) | 135 agents, 35 skills, 176+ plugins, 14 MCP configs comprehensive collection |
| alexop.dev | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Technical explainer: MCP vs skills vs subagents vs hooks full stack |
| SaaS Rise | [link](https://www.saasrise.com/blog/ai-coding-using-claude-skills-mcp-servers-and-sub-agents/) | Practitioner synthesis on extension type selection |
| WorkOS Blog | [link](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) | Enterprise MCP guide; registry fragmentation landscape |
| Tool Directory AI | [link](https://tooldirectory.ai/blog/state-of-mcp-servers-2026) | State of MCP 2026: <5% monetized; auth is next convergence point |
| ChatForest | [link](https://chatforest.com/guides/mcp-ecosystem-2026-state-of-the-standard/) | MCP as universal standard; every major editor and agent SDK natively compatible |

---

## Stats Block

```
├─ 🟠 Reddit: 3 threads │ 83 upvotes │ 15 comments  ⚠ partial (SC backup failed)
├─ 🔵 X: 17 posts │ 2,110 likes │ 100 reposts
├─ 🟢 HN: 6 stories │ 228 points │ 96 comments
├─ 🦋 Bluesky: 4 posts │ 24 likes │ 5 reposts
├─ 🐙 GitHub: 14 items │ 812 reactions │ 439 comments
├─ 🌐 Web: 20 pages (10 engine + 10 supplemental)
└─ 🗣️ Top voices: @alexalbert__, @abir35627, @CripdoeCrypto, @TechWithTimm │ r/sre, r/WebAfterAI
```

---

## Data Gaps

- **YouTube**: HTTP 402 error — all three YouTube search paths (yt-dlp, ScrapeCreators, SC backup) returned 402. No video content available this run. Given the topic (MCP tutorials, Claude Code workflows), YouTube likely has significant relevant content — tutorials from developers building MCP servers. The @TechWithTimm post referencing a 1-hour YouTube video on advanced MCP server building suggests active video content that was missed.
- **TikTok**: HTTP 402 — ScrapeCreators quota exhausted. No short-form video coverage.
- **Instagram**: HTTP 402 — same quota issue.
- **Reddit**: Partial — only 3 threads returned. ScrapeCreators backup also failed (402). The actual Reddit community discussion around r/ClaudeAI, r/LocalLLaMA, and r/AI_Agents was not reached. Coverage is likely 15-20% of actual Reddit discussion.
- **Evidence concentration**: 17 of 54 items came from X, and the top-scored cluster was single-source (X only). Multi-source confirmation is thin — most findings are X-primary, web-secondary.
- **Polymarket**: No relevant prediction markets found — the topic does not have active betting markets.
- **Estimated coverage**: ~55-65% given Reddit partial and total loss of YouTube/TikTok/Instagram. X, HN, Bluesky, GitHub, and web coverage appear complete.

---

## Key Quotes

> "MCP is becoming one of the most important skills for AI developers." — [@TechWithTimm](https://x.com/TechWithTimm/status/2076311802695299204) on X

> "Here's the thing people miss about Claude Code: it's not smart because of the model, it's smart because of what it's connected to. MCP servers are the bridge between Claude and the real world." — [@automatedmarktr](https://x.com/automatedmarktr/status/2076351476662768110) on X

> "Dead MCP servers quietly eat your context budget." — [@4Ndr3w10000](https://x.com/4Ndr3w10000/status/2076275885582569874) on X

> "YOUR CLAUDE CAN NOW USE HUNDREDS OF EXTERNAL TOOLS. ONE PASTE. FREE. awesome-mcp-servers. Frank Fiegel launched it November 2024. 90K stars in 8 months." — [@ArchiveExplorer](https://x.com/ArchiveExplorer/status/2076418069828616605) on X

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) on X (557 likes)

> "built a claude code plugin that reads sql server execution plans and tells you what's wrong. /plugin marketplace add erikdarlingdata/claude-plugins" — [@erikdarling.com](https://bsky.app/profile/erikdarling.com/post/3mqc5npb36l2m) on Bluesky

> "A skill is a folder with a SKILL.md file that teaches your coding agent how to do one thing well, and you install it into .claude/skills/" — [r/WebAfterAI](https://www.reddit.com/r/WebAfterAI/comments/1uuk5fm/10_claude_code_skill_repos_for_solo_founders/) on Reddit

> "GitHub trending rn is wild — Claude Code templates, Google's Stitch agent skills, MCP servers with terminal control. All in the same day. The AI coding tooling layer went from zero to an entire ecosystem and nobody noticed until it was everywhere." — [@0x_Missy22](https://x.com/0x_Missy22/status/2076231166492049711) on X

> "The frontend bottleneck is no longer code generation. It's now reviewing the output of an agent." — [@storybook.js.org](https://bsky.app/profile/storybook.js.org/post/3mqaesef2dk2u) on Bluesky
