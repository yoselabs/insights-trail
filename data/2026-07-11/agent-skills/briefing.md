# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-11
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 4 threads | 28 upvotes, 44 comments | r/PromptEngineering, r/ChatGPTCoding |
| X/Twitter | 25 posts | 13,047 likes, 804 reposts | @claudeai, @alexalbert__, @agentguardsco |
| Hacker News | 17 stories | 3,699 points, 1,810 comments | Agent security, tooling, harnesses |
| Bluesky | 2 posts | 7 likes | Simplicity vs. complexity debate |
| GitHub | 11 items | 724 reactions, 412 comments | anthropics/claude-code, MCP issues |
| Web | 8 pages + 8 supplemental | — | uxplanet.org, startdebugging.net, skillselion.com, smithery.ai |

---

## Synthesized Findings

### 1. The SKILL.md Standard Has Become Cross-Agent Infrastructure

The biggest structural story of the past 30 days is that Anthropic's SKILL.md format — originally a Claude Code-specific feature — has been adopted as the de-facto open standard across virtually every major AI coding agent. Claude Code, Codex CLI (OpenAI), Gemini CLI (Google), GitHub Copilot, Cursor, Windsurf, and 12+ other agents all read the same SKILL.md files. A developer can write a skill once and install it across the entire ecosystem via `npx skills add owner/repo`.

This cross-platform adoption accelerated after Anthropic open-sourced the Agent Skills specification in December 2025. The [r/PromptEngineering](https://www.reddit.com/r/PromptEngineering/comments/1uggx0r/claude_code_has_a_skills_system_most_people_dont/) thread "Claude Code has a Skills system most people don't know about" (June 26) broke the pattern for many: "A Skill is a SKILL.md file you drop into ~/.claude/skills/<skill-name>/SKILL.md. Claude Code picks it up automatically — no restart, no config." The thread sparked 7 follow-up comments and appears to be genuinely news to a large share of active Claude Code users even 6+ months after the feature launched. [designrevision.com](https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents) and [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) published explainers in the same window specifically to address the confusion between Skills, Plugins, Hooks, MCP Servers, and Agents as distinct extension primitives.

**Discussed on:** Reddit, Web, X

### 2. The Marketplace Triarchy: Smithery vs. Agensi vs. skills.sh

Three distinct distribution models are fighting for the agent tooling ecosystem, and they are not converging — they serve different needs:

- **[Smithery](https://smithery.ai)** is a public directory/registry that has grown from ~10 servers at launch to 6,000-7,000+ MCP servers listed and hosted, with tens of thousands of tool calls per day. Its new "Toolbox" feature is a single meta-MCP server that routes agents to the right servers at runtime — discovery as a runtime service, not a pre-install decision. The CLI now includes `smithery skill search` and `smithery skill add` commands.

- **[skills.sh](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem)** (Vercel) launched in January 2026 and went GA June 5, 2026 with ~670,000 open-source skills distributed via Vercel OIDC. The top skill (vercel-labs/find-skills) has 2M installs; Anthropic's own frontend-design skill has 531.8K. It's a leaderboard-and-install surface, not a curated quality gate.

- **[Agensi](https://agensi.io)** is the only curated marketplace with end-to-end security scanning, creator payments at 70% revenue share, and one-command install. It trades breadth for trust — a hand-selected catalog vs. Smithery's open directory or skills.sh's GitHub-scale OSS flood.

The scale contrast is stark: [Skillselion](https://skillselion.com/state-of-ai-agent-skills-2026)'s State of AI Agent Skills 2026 report tracks 81,864 AI coding-agent tools — 60,788 agent skills, 8,427 MCP servers, and 10,264 marketplaces — with 125 million combined installs as of June 2026. The Skillselion MCP itself now provides runtime skill loading without any installation step.

**Discussed on:** Web, X

### 3. Anthropic's Enterprise Push: Private MCPs, Tunnels, and Zero-Touch Auth

The most consequential Anthropic announcements this month for enterprise practitioners came at Code with Claude Tokyo (June 10-11) and in subsequent public beta releases. Two features stand out:

**MCP Tunnels** let agents reach MCP servers inside private networks without exposing them to the public internet. A lightweight gateway deploys a single outbound connection — no inbound firewall rules, no public endpoints, end-to-end encrypted. This directly addresses the "how do I connect Claude to my internal systems without a VPN punch-through" problem that has been a blocker for enterprise deployments. Per [the-decoder.com](https://the-decoder.com/anthropic-adds-self-hosted-sandboxes-and-mcp-tunnels-to-claude-managed-agents/) and [infoq.com](https://www.infoq.com/news/2026/05/claude-mcp-tunnels/), MCP tunnels are in research preview; self-hosted sandboxes are public beta.

**Enterprise Zero-Touch MCP Auth** via Okta: admins provision MCP connectors once and users get access on first login across Claude chat, Claude Code, and Cowork for Team/Enterprise plans. Per [explainx.ai](https://explainx.ai/blog/anthropic-claude-enterprise-managed-auth-mcp-okta-2026), this is a significant workflow unlock — previously, every developer had to configure MCP credentials individually.

The [anthropics/claude-ai-mcp](https://github.com/anthropics/claude-ai-mcp/issues/476) GitHub issue thread (11 reactions, 18 comments) surfaced a sharp friction point: custom remote MCP connectors that complete the full OAuth handshake and show as Connected in settings still have their tools silently never handed to the model in claude.ai web. The bug is confirmed across ChatGPT + Claude Code implementations of the same server, suggesting the issue is specific to the claude.ai web client's tool injection path.

**Discussed on:** Web, GitHub, X

### 4. The Plugin Architecture Clarification Moment

July 2026 marks a clarification peak for "what is a plugin vs. skill vs. MCP server" — a question that has been generating noise for months. [UX Planet](https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda) (July 8), [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) (July 5), and [designrevision.com](https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents) (July 7) all published explainers in a tight 3-day window. The consensus framing that is crystallizing:

- **Skills** = SKILL.md instruction files that change how Claude behaves (no restart required, pure markdown, works across agents)
- **Plugins** = bundled packages combining skills + hooks + subagent configs + MCP server configs for team distribution
- **MCP Servers** = external process connections that reach systems Claude cannot otherwise touch (databases, APIs, file systems)
- **Hooks** = shell commands that fire on events (tool calls, session start/stop) for automation and enforcement

[hidekazu-konishi.com](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html)'s complete guide (June 14) framed it well: "Most Claude Code customization starts as a private habit. You add a slash command, drop a SKILL.md into .claude/skills/, wire a formatting hook into settings.json — and your own setup becomes a plugin when you package those private habits for team distribution."

**Discussed on:** Web, Reddit

### 5. Security Is Now a First-Class Plugin Concern

[SAIL 2.0](https://x.com/agentguardsco/status/2075505326112325859) (Pillar Security), announced July 10 with 50,000+ downloads on v1, explicitly names coding agents and MCP servers as systems requiring sandboxing, zero-trust isolation, and runtime guardrails — not just red-teaming before deployment but active protection during execution. [@agentguardsco](https://x.com/agentguardsco/status/2075505326112325859) highlighted: the "Operate" phase of SAIL is about intercepting tool calls from coding agents (Claude Code, Copilot, Cursor) during live operation.

Microsoft Defender in Agent 365 has now expanded to discover local agents and MCP servers across managed Windows and macOS devices, supporting 35+ known agent types in preview ([per @0x534c](https://x.com/0x534c/status/2075806202978771346)). This is enterprise MDM for agent tooling — a category that didn't exist a year ago.

The [GitLost HN thread](https://noma.security/blog/gitlost-how-we-tricked-githubs-ai-agent-into-leaking-private-repos/) (538 points, 204 comments, July 8) — "We Tricked GitHub's AI Agent into Leaking Private Repos" — dominated HN this week and illustrates why the security layer matters: MCP servers and agent tool access patterns create new attack surfaces that don't map to traditional app security models.

**Discussed on:** X, Hacker News, Web

### 6. The "Just Use Claude Code" vs. Complex Stack Debate

A low-key but persistent tension is visible: some practitioners pushing back on the complexity spiral. [@schcrt.bsky.social](https://bsky.app/profile/schcrt.bsky.social/post/3mq32hclbk22b) on Bluesky: "Just use Claude Code. There's no reason for complex agent setups like that. Terminal + Claude Code is hard to beat." — 5 likes, 1 reply, framed as a response to someone building elaborate multi-agent orchestration.

[@suraj_sharma14](https://x.com/suraj_sharma14/status/2075799744937652301) represents the opposite pole — a comprehensive "AI engineering stack" post enumerating: Claude Code + Codex handoffs, OpenClaw/Hermes workflows, context engineering, agentic loops, MCP servers connected to everything, local open models, production RAG, multi-agent orchestration, vLLM inference, n8n automation, and self-hosted infrastructure. This post got 11 likes and 6 replies, with the replies largely positive — suggesting there IS a real market for complex multi-tool agent stacks, not just hobbyist experimentation.

[@kamilkwapiszpl](https://x.com/kamilkwapiszpl/status/2075290645405610068) noted the client-demand angle: "We're so flooded with videos like 'I built the perfect tool for the XYZ industry with an AI agent'... my clients now want exactly that. And it genuinely is a great solution."

**Discussed on:** X, Bluesky

### 7. Hacker News: Agent Infrastructure as a Developer Category

HN this month shows a distinct cluster of developers building agent infrastructure tooling — not AI companies, but individual devs shipping open-source harnesses and utilities:

- [Herdr](https://github.com/ogulcancelik/herdr) (166 pts, 110 comments, June 29) — Agent multiplexer that lives in your terminal
- [OpenWiki](https://github.com/langchain-ai/openwiki) (96 pts, 31 comments, July 1) — CLI that writes and maintains agent documentation for your codebase
- [peerd](https://github.com/NotASithLord/peerd) (75 pts, 23 comments, June 23) — AI agent harness that runs entirely in your browser
- [Shipwright Harness](https://github.com/app-vitals/shipwright) (3 pts, June 30) — open-source autonomous delivery agent for Claude Code (MIT)
- [Lupen](https://github.com/momoraul/Lupen) (3 pts, June 24) — "Which Claude Code turn or sub-agent ran up your bill"
- [Ponytail](https://github.com/DietrichGebert/ponytail) (98 pts, 17 comments, June 14) — "Make your AI agent think like the laziest senior dev in the room"

The [Zuckerberg/Reuters HN thread](https://www.reuters.com/business/zuckerberg-says-ai-agent-development-going-slower-than-expected-2026-07-02/) (340 pts, 617 comments, July 2) — "Zuckerberg says AI agent development going slower than expected" — was the most-commented agent story of the month, suggesting genuine HN skepticism about the timeline hype even as tooling ships rapidly.

**Discussed on:** Hacker News

### 8. Community Complaints: MCP Reliability and Skill Discovery

The top GitHub friction points are consistent with what you'd expect at this ecosystem maturity level:

- **Tool injection failures**: [anthropics/claude-ai-mcp #476](https://github.com/anthropics/claude-ai-mcp/issues/476) — MCP connector shows Connected but tools never surface to the model in claude.ai web (11 reactions, 18 comments)
- **Windows MCP spawn issues**: [kirodotdev/Kiro #9713](https://github.com/kirodotdev/Kiro/issues/9713) — MCP stdio servers spawn visible CMD windows on Windows (13 reactions, 31 comments)
- **Session leakage**: [anthropics/claude-code #74066](https://github.com/anthropics/claude-code/issues/74066) — Apparent session leakage between Enterprise ZDR workspace instances (49 reactions, 17 comments)
- **Skill discovery gap**: The r/PromptEngineering thread reveals many developers still haven't discovered the Skills system at all — not a reliability issue but a documentation/discoverability failure

The [r/PromptEngineering Socratic skill generator](https://www.reddit.com/r/PromptEngineering/comments/1u7j03b/i_built_a_free_socratic_generator_for_aiagent/) post (20 upvotes, 21 comments, June 16) gets at the quality problem: most SKILL.md files agents receive are vague ("write clean code") and end up skimmed or ignored. The developer built PromptMentor to run a Socratic interrogation pass — "what's the actual failure mode? what must never happen? what's the trigger?" — before generating a tight, gated skill file.

**Discussed on:** GitHub, Reddit

---

## Cross-Source Patterns

**Pattern 1: The SKILL.md standard is quietly unifying the agent ecosystem**
Every major AI coding agent now reads the same SKILL.md format. This cross-platform convergence was not publicly announced by any one company — it emerged through independent adoption. Visible on: Web (multiple comparison guides), Reddit (discovery thread), X (stack posts referencing Claude Code + Codex + Cursor together).

**Pattern 2: Security is becoming a first-class infrastructure layer**
SAIL 2.0, Microsoft Defender for local agents, the GitLost attack, and Anthropic's MCP tunnels all point to the same trend: agent tool ecosystems need security primitives equivalent to what enterprise software has had for decades. Visible on: X (SAIL 2.0 announcement), Hacker News (GitLost 538pts), X (Agent 365 update).

**Pattern 3: Marketplace fragmentation vs. consolidation**
Three distinct distribution models (Smithery directory, skills.sh OSS scale, Agensi curated) are not converging. Developers are choosing based on trust/quality needs (Agensi) vs. discovery (Smithery) vs. install scale (skills.sh). Key quote from [@kamilkwapiszpl](https://x.com/kamilkwapiszpl/status/2075290645405610068): "We're so flooded with videos... my clients now want exactly that." Visible on: Web, X.

**Pattern 4: Simplicity vs. complexity stack tension**
"Just use Claude Code, terminal + Claude Code is hard to beat" vs. 12-item AI engineering stack posts. Both positions are getting engagement. The tension is real and unresolved. Visible on: Bluesky, X.

**Pattern 5: HN builder community emerging around agent infrastructure**
Individual developers shipping open-source agent harnesses and utilities (Herdr, peerd, Ponytail, Lupen, Shipwright) suggests the agent-tooling layer is mature enough to support a secondary ecosystem of tooling-for-tooling. Visible on: Hacker News (multiple Show HN threads).

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/PromptEngineering | Claude Code has a Skills system most people don't know about | n/a | 7 | "A Skill is a SKILL.md file you drop into ~/.claude/skills/ — no restart, no config" | https://www.reddit.com/r/PromptEngineering/comments/1uggx0r/claude_code_has_a_skills_system_most_people_dont/ |
| r/PromptEngineering | I built a free Socratic generator for AI-agent skills | 20 | 21 | "Most skill files agents get are vague and end up skimmed and ignored" | https://www.reddit.com/r/PromptEngineering/comments/1u7j03b/i_built_a_free_socratic_generator_for_aiagent/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | "Now in beta on Free, Pro, and Max plans..." (memory feature) | 537 | 22 | https://x.com/claudeai/status/2075225960916369551 |
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 557 | 15 | https://x.com/alexalbert__/status/2069470389391241314 |
| @alexalbert__ | "Welcome back to the world Fable!!" | 593 | 10 | https://x.com/alexalbert__/status/2072404717490360727 |
| @suraj_sharma14 | "If you have: Claude Code + Codex handoffs / OpenClaw or Hermes agent workflows / MCP servers connected to everything..." | 11 | 1 | https://x.com/suraj_sharma14/status/2075799744937652301 |
| @MaryamMiradi | "7-Step roadmap from blinking cursor to agentic engineering" | 11 | 1 | https://x.com/MaryamMiradi/status/2075654335938056206 |
| @agentguardsco | "SAIL 2.0 just launched — MCP servers as systems that need sandboxing, zero-trust isolation, and runtime guardrails" | 1 | 1 | https://x.com/agentguardsco/status/2075505326112325859 |
| @vinod97035598 | "Curated + scored catalog of official DevOps/SRE MCP servers and Agent Skills" | n/a | n/a | https://x.com/vinod97035598/status/2075822943049842978 |
| @kamilkwapiszpl | "We're so flooded with videos like 'I built the perfect tool for the XYZ industry with an AI agent'" | 1 | 0 | https://x.com/kamilkwapiszpl/status/2075290645405610068 |
| @0x534c | "Microsoft Defender in Agent 365: discovery of local agents and MCP servers across managed devices" | 9 | 0 | https://x.com/0x534c/status/2075806202978771346 |
| @aibullss | "Complete AI Trading Stack: Claude Code + TradingView MCP + ..." | 3 | 1 | https://x.com/aibullss/status/2075841632025661638 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| ColinEberhardt | GitLost: We Tricked GitHub's AI Agent into Leaking Private Repos | 538 | 204 | MCP tool access creates new attack surfaces | https://noma.security/blog/gitlost-how-we-tricked-githubs-ai-agent-into-leaking-private-repos/ |
| cwwc | Zuckerberg says AI agent development going slower than expected | 340 | 617 | Reuters/Reuters | https://www.reuters.com/business/zuckerberg-says-ai-agent-development-going-slower-than-expected-2026-07-02/ |
| mellosouls | Ponytail – make your AI agent think like the laziest senior dev | 98 | 17 | — | https://github.com/DietrichGebert/ponytail |
| handfuloflight | OpenWiki: CLI that writes and maintains agent documentation | 96 | 31 | — | https://github.com/langchain-ai/openwiki |
| showmypost | We built a persistent agent memory layer on Elasticsearch | 116 | 40 | "0.89 recall" | https://www.elastic.co/search-labs/blog/agent-memory-elasticsearch |
| kkm | How to setup a local coding agent on macOS | 507 | 127 | — | https://ikyle.me/blog/2026/how-to-setup-a-local-coding-agent-on-macos |
| iacguy | The Log is the Agent (arxiv) | 114 | 50 | — | https://arxiv.org/abs/2605.21997 |
| matt_d | Micro-Agent: Beat Frontier Models with Collaboration Inside Model API | 81 | 22 | — | https://vllm.ai/blog/2026-06-29-micro-agent-frontier-models |
| pancomplex | Show HN: Reverse-engineering web apps into agent tools | 81 | 34 | — | https://news.ycombinator.com/item?id=48847834 |
| mzehrer | Herdr: Agent multiplexer that lives in your terminal | 166 | 110 | — | https://github.com/ogulcancelik/herdr |
| piotrgrudzien | Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | 0 | — | https://quickchat.ai/post/expose-ai-agent-as-mcp-server |
| arhamshahrier | Show HN: Tilion – MCP for Claude Code to stop it getting blocked | 6 | 0 | — | https://github.com/tiliondev/fortress/tree/main/mcp |
| momoraul | Show HN: Lupen – which Claude Code turn or sub-agent ran up your bill | 3 | 0 | — | https://github.com/momoraul/Lupen |
| NotASithLord | Show HN: peerd – AI agent harness in your browser | 75 | 23 | — | https://github.com/NotASithLord/peerd |
| xiaoyu2006 | AI agent bankrupted their operator trying to scan DN42 | 1,467 | 535 | — | https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/ |
| dodizzle | Shipwright Harness – autonomous delivery agent for Claude Code (MIT) | 3 | 0 | — | https://github.com/app-vitals/shipwright |
| imaxxs | Gemini CLI vs. Claude Code: Why agent capabilities matter more than prompts | 3 | 0 | — | https://imaxxs.com/behavioral-induction-capabilities-shape-execution |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @schcrt.bsky.social | "Just use Claude Code. There's no reason for complex agent setups like that. Terminal + Claude Code is hard to beat." | 5 | https://bsky.app/profile/schcrt.bsky.social/post/3mq32hclbk22b |
| @trynoguard.bsky.social | "Aether CLI: an uncensored AI coding agent for your terminal (Claude Code alternative)" | 2 | https://bsky.app/profile/trynoguard.bsky.social/post/3mq64mozmj42p |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| anthropics/claude-code | [Bug] Potential session/cache leakage between workspace instances | 49 | 17 | https://github.com/anthropics/claude-code/issues/74066 |
| anthropics/claude-ai-mcp | Custom remote MCP connector: tools never surfaced to model in claude.ai web | 11 | 18 | https://github.com/anthropics/claude-ai-mcp/issues/476 |
| kirodotdev/Kiro | MCP stdio servers spawn visible CMD windows on Windows | 13 | 31 | https://github.com/kirodotdev/Kiro/issues/9713 |
| openai/codex | Rate-limit cost per token jumped 10-20x since June 16 | 547 | 204 | https://github.com/openai/codex/issues/28879 |
| danny-avila/LibreChat | feat: MCP Apps support (inline HTML tool rendering) | 8 | 35 | https://github.com/danny-avila/LibreChat/pull/13831 |
| BerriAI/litellm | LiteLLM Stability Sprint Roadmap | 8 | 22 | https://github.com/BerriAI/litellm/issues/30484 |
| bethington/ghidra-mcp | "this is becoming a complex unmaintainable mess" (too many tools for agents) | 11 | 15 | https://github.com/bethington/ghidra-mcp/issues/307 |
| getpaseo/paseo | feat: Pre-launch environment hook for agents (worktree.env) | 9 | 5 | https://github.com/getpaseo/paseo/issues/1628 |
| anomalyco/opencode | OpenCode v1.17.10 crashes with Bun segfault on Windows | 47 | 52 | https://github.com/anomalyco/opencode/issues/33742 |
| zed-industries/zed | Git status markers don't update immediately from terminal | 21 | 13 | https://github.com/zed-industries/zed/issues/60102 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| UX Planet (Nick Babich) | https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda | Definitive breakdown: Skills + Agents + Hooks + MCP Servers as the 4 parts of a Claude Code plugin |
| Start Debugging | https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/ | Decision guide: skill = change behavior, subagent = protect context, MCP = reach external system |
| DesignRevision | https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents | Most-shared explainer differentiating all 4 extension types |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html | Complete guide to bundling Claude Code customizations into distributable plugins |
| Tygart Media | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | "Skills teach Claude how to do a thing; MCP lets Claude reach a system; connectors authenticate" |
| Skillselion | https://skillselion.com/state-of-ai-agent-skills-2026 | State of AI Agent Skills 2026: 81,864 tools, 125M installs tracked |
| Bloome | https://bloome.im/features/agent-skill-marketplace | Open library marketplace: install via skill card, URL, or zip |
| Ry Walker Research | https://rywalker.com/research/skills-sh | skills.sh analysis: ~670K skills, top skill at 2M installs, Anthropic's at 531.8K |
| Smithery | https://smithery.ai/docs/concepts/cli | CLI commands for skill search and install; Toolbox meta-MCP |
| Vercel | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | Official skills.sh GA announcement (June 5, 2026) |
| Totalum Blog | https://www.totalum.app/blog/agent-skills-marketplaces-2026 | Marketplace comparison: Anthropic vs Vercel vs OpenAI vs Cline vs MCP |
| InfoQ | https://www.infoq.com/news/2026/05/claude-mcp-tunnels/ | Anthropic MCP Tunnels announcement coverage |
| The Decoder | https://the-decoder.com/anthropic-adds-self-hosted-sandboxes-and-mcp-tunnels-to-claude-managed-agents/ | Self-hosted sandboxes + MCP tunnels technical breakdown |
| ExplainX | https://explainx.ai/blog/anthropic-claude-enterprise-managed-auth-mcp-okta-2026 | Enterprise zero-touch MCP auth via Okta |
| Agensi | https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 | Full marketplace landscape 2026 breakdown |
| Agensi | https://www.agensi.io/learn/complete-list-ai-agent-skill-directories-2026 | Complete list of 10,000+ skill directories |

---

## Stats Block

```
├─ 🟠 Reddit: 4 threads │ 28 upvotes │ 44 comments
├─ 🔵 X: 25 posts │ 13,047 likes │ 804 reposts
├─ 🟢 HN: 17 stories │ 3,699 points │ 1,810 comments
├─ 🦋 Bluesky: 2 posts │ 7 likes
├─ 🐙 GitHub: 11 items │ 724 reactions │ 412 comments
├─ 🌐 Web: 16 pages (8 engine + 8 supplemental)
└─ 🗣️ Top voices: @claudeai, @alexalbert__, @agentguardsco │ r/PromptEngineering, r/ChatGPTCoding
```

---

## Data Gaps

- **YouTube: 0 results** — YouTube search returned nothing for this topic despite multiple retry attempts with ScrapeCreators. The topic is primarily text/developer-community focused; the tutorial videos that exist (Claude Code skills walkthroughs) appear to predate the 30-day window or weren't indexed in time.
- **TikTok/Instagram: 0 results** — ScrapeCreators returned HTTP 402 (Payment Required) for TikTok hashtag searches (#claudecode, #mcpserver, #aiagent, #aicoding) and Instagram; likely credit exhaustion on the account. No TikTok or Instagram coverage.
- **Reddit: sparse (4 threads)** — Reddit RSS feeds partially failed; arctic-shift backfill recovered some scores but the dedicated r/ClaudeAI lane returned 0 posts. More relevant threads likely exist but weren't surfaced. The 4 items recovered are high-quality signal.
- **Polymarket: 0 markets** — No prediction markets on agent skills or MCP ecosystems found; not surprising for a technical tooling topic.
- **Approximate coverage:** ~70% (strong on HN/X/Web/GitHub; Reddit and TikTok/Instagram meaningfully underrepresented)

---

## Key Quotes

> "Just use Claude Code. There's no reason for complex agent setups like that. Terminal + Claude Code is hard to beat." — @schcrt.bsky.social on Bluesky ([link](https://bsky.app/profile/schcrt.bsky.social/post/3mq32hclbk22b))

> "A Skill is a SKILL.md file you drop into ~/.claude/skills/<skill-name>/SKILL.md. Claude Code picks it up automatically — no restart, no config." — r/PromptEngineering ([link](https://www.reddit.com/r/PromptEngineering/comments/1uggx0r/claude_code_has_a_skills_system_most_people_dont/))

> "Most skill files agents get are vague ('write clean code') and end up skimmed and ignored." — r/PromptEngineering, PromptMentor builder ([link](https://www.reddit.com/r/PromptEngineering/comments/1u7j03b/i_built_a_free_socratic_generator_for_aiagent/))

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — @alexalbert__ on X ([link](https://x.com/alexalbert__/status/2069470389391241314))

> "MCP servers as systems that need sandboxing, zero-trust isolation, and runtime guardrails — not just red-teaming before deployment, but active protection while the agent is running." — @agentguardsco on X ([link](https://x.com/agentguardsco/status/2075505326112325859))

> "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." — startdebugging.net ([link](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/))

> "As of 2026, the Skillselion catalog tracks 81,864 AI coding-agent tools — 60,788 agent skills, 8,427 MCP servers and 10,264 marketplaces — with 125M combined installs." — Skillselion ([link](https://skillselion.com/state-of-ai-agent-skills-2026))

> "Most Claude Code customization starts as a private habit. Your own setup becomes a plugin when you package those private habits for team distribution." — hidekazu-konishi.com ([link](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html))

> "We're so flooded with videos like 'I built the perfect tool for the XYZ industry with an AI agent' that a lot of my clients now want exactly that." — @kamilkwapiszpl on X ([link](https://x.com/kamilkwapiszpl/status/2075290645405610068))

> "this is becoming a complex unmaintainable mess... too many tools for agents" — GitHub issue on ghidra-mcp ([link](https://github.com/bethington/ghidra-mcp/issues/307))
