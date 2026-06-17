# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-17
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 14 threads | — | r/ClaudeCode, r/PromptEngineering dominant |
| X/Twitter | 18 posts | 127 likes, 11 reposts | @ClaudeCodeLog changelog posts, @hasantoxr NVIDIA story |
| Bluesky | 12 posts | 313 likes, 9 reposts | Strong dev community signal |
| Web | 10 pages | — | via WebSearch + engine grounding |
| YouTube | 0 videos | — | No results (yt-dlp returned 0) |
| TikTok | 0 videos | — | SC API 402 error |
| Instagram | 0 reels | — | SC API 402 error |
| Hacker News | 0 stories | — | No results |
| Polymarket | 0 markets | — | No prediction markets on this topic |

---

## Synthesized Findings

### 1. Security Crisis: 1 in 4 Agent Skills Has a Vulnerability

The biggest story in the agent skills ecosystem this month is not a new marketplace launch — it's a security audit. NVIDIA open-sourced [SkillSpector](https://github.com/nvidia/skillspector), a CLI scanner for AI agent skills, and the research underlying it is alarming. Across 42,447 skills pulled from major marketplaces, NVIDIA found **26.1% contain at least one vulnerability** and **5.2% show likely malicious intent**. [@hasantoxr](https://x.com/hasantoxr/status/2065664402301575438) put it plainly on X (42 likes, 7 reposts): "NVIDIA open-sourced a security scanner for AI agent skills and the research behind it is more alarming than the tool itself."

SkillSpector scans across 64 vulnerability patterns in 16 categories — prompt injection, data exfiltration, privilege escalation, supply chain attacks, memory poisoning, tool misuse, and MCP-specific risks (tool poisoning, least-privilege violations). It accepts Git repos, URLs, zip files, and single files and outputs a 0-100 risk score. Per [NVIDIA's technical blog](https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/), every skill entering NVIDIA's verified catalog must pass SkillSpector as part of the publication validation pipeline.

The supply chain anxiety extends beyond NVIDIA. On Bluesky, [@fpl9000.bsky.social](https://bsky.app/profile/fpl9000.bsky.social/post/3moayr5qg5c2v) (18 likes) asked: "I'm considering installing the Pi agent (pi.dev), which is written in TypeScript and installs with npm. Given recent news about npm-based supply chain attacks, I asked Claude about the risk of malware." This reflects a broader developer wariness: the same ecosystem convenience that made npm so powerful is now a threat vector for agent skills distributed as npm packages.

Platforms discussed: X/Twitter, Bluesky, Web

### 2. Marketplace Explosion and the Discovery Fragmentation Problem

The agent skills marketplace landscape went from **one registry in December 2025 to eight major marketplaces by Q2 2026**, per [Agensi.io's directory](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). This has created an obvious second-order problem: developers spend more time comparing marketplaces than finding the skill they need.

Key players in the current landscape:

- **[Claude Marketplaces](https://claudemarketplaces.com/)** - The largest community-curated directory, updated daily from GitHub, indexing 21,600+ skills, 2,500+ marketplaces, and 12,500+ MCP servers.
- **[Skills.sh](https://claudemarketplaces.com/)** - Vercel-backed, launched January 2026, positioned as the npm-style package manager for skills with a one-command CLI installer spanning Claude Code, Codex CLI, Cursor, and OpenClaw.
- **SkillsMP** - 800,000+ skills scraped from public GitHub repos; large catalog, minimal curation, filters on 2+ GitHub stars.
- **ClaudeSkills.info** - 658+ free community-contributed skills, including official Anthropic skills, no paid tier.
- **[MCP Market](https://mcpmarket.com/tools/skills/plugin-marketplace-management)** - Primarily MCP directory that added skill discovery, useful for skills connecting to MCP servers specifically.

The official Anthropic-managed marketplace (as documented by [Groundy](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/)) ships 101 vetted plugins plus 68 partner plugins from GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase as of March 2026. The plugin marketplace itself launched in February 2026, roughly one month after the January 30 plugins announcement that, per multiple sources, wiped $285 billion off software stocks on announcement day.

The MCP server side of the ecosystem is even larger: [QCode.cc's ecosystem guide](https://www.qcode.cc/mcp-servers-ecosystem-2026) counts 13,000+ public MCP servers. Anthropic donated the MCP protocol to the new Agentic AI Foundation; it is now implemented by OpenAI Agents SDK, Cursor, Cloudflare Agents, and Microsoft alongside Anthropic.

Platforms discussed: X/Twitter, Web, Reddit

### 3. Plugin Architecture: Skills vs Plugins vs MCPs — The Three-Layer Model

The community has converged on a clear mental model for the Claude Code extension stack, documented well by [Nevo Systems](https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp) and [Clarista](https://www.clarista.io/blog/claude-code-mcp-plugins-guide):

- **Skills** - Prompt-based markdown directories that load contextually, modifying agent behavior without any code. The instruction layer.
- **Plugins** - Distributable packages bundling skills, hooks, subagents, and MCP configs into a single installable unit. The distribution layer.
- **MCP servers** - Running processes exposing tools and data sources through the Model Context Protocol. The integration layer.

The winning 2026 pattern, per [Codersera's practitioner guide](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/): "pin one MCP per external system (GitHub, Postgres, Linear, Sentry), then write thin Skills that orchestrate them."

Claude Code CLI is iterating rapidly on plugin scaffolding. [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2060460312457810182) documented version 2.1.157 (May 29): new `claude plugin init <name>` to scaffold a plugin directly into `.claude/skills`, autocomplete for `/plugin` arguments including installed plugin names and plugins from known marketplaces, and a "Workflow keyword trigger" setting in `/config`. Version 2.1.152 (May 27) added `/reload-skills` to re-scan skill directories without restarting, and `pluginSuggestionMarketplaces` as a managed setting for org admins to allowlist approved marketplaces.

The [claudefa.st plugin distribution guide](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution) frames the org rollout pattern: "Plugins turn your personal Claude Code setup into a shareable bundle. Skills, hooks, MCPs in one install."

Platforms discussed: X/Twitter, Web, Reddit

### 4. /workflows Ships and Changes Multi-Agent Architecture

On [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tkjy4u/claude_code_dropped_workflows/), the most substantive technical thread of the month covered Anthropic quietly shipping `/workflows` in Claude Code 2.1.147. The post describes it as "the biggest shift in how we build multi-agent systems yet." The pre-/workflows pattern forced every sub-agent result back into the orchestrator's context window - a compounding problem as agent teams grow. /workflows breaks that coupling.

[The New Stack on Bluesky](https://bsky.app/profile/thenewstack.io/post/3mo7yf7mjvo2v) (3 likes) tested Anthropic's dynamic workflows - parallel subagent execution in Claude Code - against a single agent to see if they beat the hype. A Japanese developer [@takara-infra-ai.bsky.social](https://bsky.app/profile/takara-infra-ai.bsky.social/post/3mo57n5yguf2s) reports parallel agent execution in Claude Code reduces processing time "to 1/3-1/5" of sequential runs.

The heterogeneous agent team pattern is getting community traction. [@hikikomorphism.bsky.social](https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d) (52 likes on Bluesky): "The trick here is heterogenous agent teams, like yes mythos/fable as planner, but there's no need to burn opus tokens on medium sized tasks when you can just have mythos manage a team of deepseek/Gemini agents. I suspect this is not a feature Claude Code will offer native support for." This signals developer demand for cross-model orchestration that the native tool doesn't yet address.

Platforms discussed: Reddit, Bluesky, X/Twitter

### 5. Claude Code's Market Dominance and the Category Explosion

The category of "terminal AI coding agent" now has a name and a crowded field. [@ssp.sh on Bluesky](https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q): "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category. Claude Code, OpenCode, Amp, Crush, Pi, aichat, Deer-flow. Each one is an agent harness that runs mostly autonomously in the terminal, against your repo, with permission rails you set."

Despite the crowded field, Claude Code's practical dominance is blunt. [@moomanibe.bsky.social](https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226) (24 likes): "people keep asking me this question and my answer is that it is functionally irrelevant because no one is doing this and absolutely everyone is using claude code and midjourney. like there's zero nuance in the actual practical expression here."

Platform integrations accelerated this month: Snap added agentic development support for Claude Code, Codex, and Cursor via developer preview ([@peesamac on X](https://x.com/peesamac/status/2067218962602189084)). Microsoft launched an OpenClaw-style agent in Microsoft Teams, with [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) (32 likes) noting the combination of Claude Code and OpenClaw-style products "will be transformational for knowledge workers."

Custom skill creation is democratizing domain knowledge. [@Zev_ee on X](https://x.com/Zev_ee/status/2067218119056351499) highlighted a developer who packaged traditional Chinese Bazi fortune-telling into a native Claude Code skill (`bazi-skill`) - an example of specialized knowledge being distributed via the skill ecosystem. [@problogger on X](https://x.com/problogger/status/2067217581002629578) is building a Claude Code command that takes a Sunday sermon video, transcribes it, suggests clips, reframes vertically, and adds branded captions - custom workflow automation via skill composition.

The [r/ClaudeCode VibeKeys thread](https://www.reddit.com/r/ClaudeCode/comments/1tq5odl/i_actually_built_the_vibe_coding_keyboard_its_not/) shows the cultural depth: someone built dedicated hardware (VibeKeys) for Claude Code with one-click accept/reject/retry, a rotary knob, voice input, and an LED status display. 50 days, 3 prototypes. Claude Code has become the platform that people build hardware for.

Platforms discussed: Bluesky, X/Twitter, Reddit, Web

### 6. Agent Evaluation and Ecosystem Tooling Maturing

The ecosystem around agent skills is adding evaluation infrastructure. [Agent-EvalKit](https://bsky.app/profile/feed.igeek.gamer-geek-news.com.ap.brid.gy/post/3mnzlovjwrhs2) (5 likes on Bluesky) is an open-source Apache 2.0 toolkit for systematically evaluating AI agents, integrating with Claude Code, Kiro CLI, and Kilo Code. The presence of evaluation tooling signals a maturing ecosystem moving beyond "does it work" toward "how well does it work."

A Japanese developer published [IDD](https://bsky.app/profile/yatmita.bsky.social/post/3mo7kltlqfo2j) - a project-scoped Claude Code agent harness that integrates GitHub issues, milestones, PRs, semantic versioning, Conventional Commits, changelogs, and releases into a harness, with TDD, Composed Method, SRP, and Immutability rules to shape the LLM's behavior.

The [modelcontextprotocol/modelcontextprotocol GitHub discussions #2316](https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2316) - "Skills Over MCP Interest Group - Feb 26th 2026 Office Hours Notes" - captures the ongoing community debate about when each extension type is appropriate.

Platforms discussed: Bluesky, Web

---

## Cross-Source Patterns

### Pattern 1: Security Anxiety is Peaking Alongside Ecosystem Growth

Present on X/Twitter (NVIDIA SkillSpector post, 42 likes) and Bluesky (npm supply chain concern, 18 likes). The fastest-growing ecosystem in AI tooling is also the one that least secure by measured metrics. The NVIDIA finding that 1 in 4 skills has a vulnerability is appearing across developer communities and is likely to become a governance story as enterprises adopt skill-based automation. No Reddit threads yet, but the X post shows early signal.

Key quote: "NVIDIA says research found 26.1% of agent skills contain vulnerabilities, and 5.2% show likely malicious intent. This is from a study of 42,447 skills pulled from major marketplaces." - [@hasantoxr](https://x.com/hasantoxr/status/2065664402301575438)

### Pattern 2: Claude Code CLI is Shipping Plugin Infrastructure Weekly

Present on X/Twitter (@ClaudeCodeLog changelog posts) and Reddit (r/ClaudeCode /workflows thread). Two significant CLI releases in the engine's 30-day window (2.1.152 and 2.1.157) both focused on plugin scaffolding, skill reloading, and marketplace management. The velocity of plugin infrastructure work signals Anthropic is treating skills/plugins as a primary product surface, not a side feature.

Key quote: "Added claude plugin init <name> to scaffold a new plugin in .claude/skills • Added autocomplete for /plugin arguments" - [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2060460312457810182)

### Pattern 3: Multi-Agent Orchestration is the Frontier Use Case

Present on Bluesky (heterogeneous teams, 52 likes; parallel execution, Japanese developer), Reddit (r/ClaudeCode /workflows thread), and Web (The New Stack on dynamic workflows). The /workflows feature and parallel subagent patterns are where the most technically sophisticated discussion is happening. The community is ahead of the tooling - developers want cross-model teams (Claude + DeepSeek + Gemini), which isn't natively supported yet.

Key quote: "The trick here is heterogenous agent teams, like yes mythos/fable as planner, but there's no need to burn opus tokens on medium sized tasks when you can just have mythos manage a team of deepseek/Gemini agents." - [@hikikomorphism.bsky.social](https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d)

### Pattern 4: Enterprise and Platform Integrations Accelerating

Present on X/Twitter (Snap developer preview, @peesamac), Bluesky (Microsoft Teams + OpenClaw, @carnage4life.bsky.social, 32 likes), and Web (AWS MCP GA, Meta Ads MCP, official partner plugins). Major cloud providers and enterprise platforms are publishing first-party MCP servers and plugin integrations at increasing pace. The MCP ecosystem reaching 13,000+ public servers reflects this push.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | Claude Code dropped /workflows | — | — | "Anthropic quietly shipped /workflows in Claude Code 2.1.147 and it might be the biggest shift in how we build multi-agent systems yet" | https://www.reddit.com/r/ClaudeCode/comments/1tkjy4u/claude_code_dropped_workflows/ |
| r/ClaudeCode | I actually built the vibe coding keyboard | — | — | "50 days. 3 prototypes. Real hardware." | https://www.reddit.com/r/ClaudeCode/comments/1tq5odl/i_actually_built_the_vibe_coding_keyboard_its_not/ |
| r/PromptEngineering | 9 Free Chinese AI Tools Most People Don't Know | — | — | "While most people are still defaulting to ChatGPT and Claude, the Chinese labs have been shipping aggressively" | https://www.reddit.com/r/PromptEngineering/comments/1u7vwkj/9_free_chinese_ai_tools_most_people_dont_know/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @hasantoxr | "NVIDIA open-sourced a security scanner for AI agent skills and the research behind it is more alarming than the tool itself. 26.1% vulnerable, 5.2% malicious." | 42 | 7 | https://x.com/hasantoxr/status/2065664402301575438 |
| @ClaudeCodeLog | "Claude Code CLI 2.1.157: Added claude plugin init to scaffold a new plugin in .claude/skills; autocomplete for /plugin arguments" | 19 | 1 | https://x.com/ClaudeCodeLog/status/2060460312457810182 |
| @ClaudeCodeLog | "Claude Code CLI 2.1.152: Added /reload-skills command to re-scan skill directories without restarting the session" | 27 | 1 | https://x.com/ClaudeCodeLog/status/2059451400338223550 |
| @problogger | "Tonight's AI experiment: to create a command for Claude Code that: 1. Takes a full Sunday sermon video 2. Transcribes..." | 1 | 0 | https://x.com/problogger/status/2067217581002629578 |
| @Zev_ee | "A developer turned traditional Chinese Bazi into a native Claude Code skill called bazi-skill" | — | — | https://x.com/Zev_ee/status/2067218119056351499 |
| @TopherNOW | "REsimplifi: an MCP that drops nationwide CRE listing data straight into Claude, ChatGPT, and Perplexity" | 16 | 2 | https://x.com/TopherNOW/status/2064439643571974274 |
| @anjela_petkova | "The Complete Guide to Claude Plugins, Skills & MCP Servers (2026)" | 3 | 0 | https://x.com/anjela_petkova/status/2057008955906556306 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @hikikomorphism.bsky.social | "The trick here is heterogenous agent teams, like yes mythos/fable as planner, but there's no need to burn opus tokens on medium sized tasks" | 52 | https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d |
| @moomanibe.bsky.social | "people keep asking me this question and my answer is that it is functionally irrelevant because no one is doing this and absolutely everyone is using claude code and midjourney" | 24 | https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226 |
| @fpl9000.bsky.social | "I'm considering installing the Pi agent (pi.dev)...Given recent news about npm-based supply chain attacks, I asked Claude about the risk of malware." | 18 | https://bsky.app/profile/fpl9000.bsky.social/post/3moayr5qg5c2v |
| @carnage4life.bsky.social | "Microsoft just launched an OpenClaw-style agent in Microsoft Teams...the combination of Claude Code & OpenClaw style products will be transformational" | 32 | https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q |
| @why.bsky.team | "Making an agent based procedural city sim...Claude is a lot of fun." | 153 | https://bsky.app/profile/why.bsky.team/post/3mnxaspuefk22 |
| @ssp.sh | "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category. Claude Code, OpenCode, Amp, Crush, Pi, aichat, Deer-flow." | 5 | https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q |
| @thenewstack.io | "Anthropic's dynamic workflows in Claude Code let Claude run parallel subagents. We tested them against a single agent to see if they beat the hype." | 3 | https://bsky.app/profile/thenewstack.io/post/3mo7yf7mjvo2v |
| @hexacode.bsky.social | "Claude Code vs Cursor vs Copilot vs Codex - which AI coding agent is best in 2026? Real-world comparison, benchmarks & practical advice" | 14 | https://bsky.app/profile/hexacode.bsky.social/post/3mnv76mjbtk2f |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Largest community-curated directory: 21,600+ skills, 12,500+ MCP servers |
| NVIDIA Technical Blog | https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/ | NVIDIA Verified Agent Skills + SkillSpector scanner pipeline |
| GitHub / NVIDIA SkillSpector | https://github.com/nvidia/skillspector | Open-source CLI for scanning agent skills across 64 vulnerability patterns |
| AWS News Blog | https://aws.amazon.com/blogs/aws/the-aws-mcp-server-is-now-generally-available/ | AWS MCP Server now generally available |
| dev.to / alexcloudstar | https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532 | How skills, MCP servers, and plugins fit together in 2026 |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Plugin distribution guide: personal to org rollout patterns |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | MCP as "USB for AI" — complete guide to MCP + plugins |
| toolbrain.net | https://toolbrain.net/blog/guide-building-ai-powered-development-workflows-with-mcp-and-agentic-pipelines/ | Building AI-powered dev workflows with MCP and agentic pipelines |
| mcsaguru.com | https://mcsaguru.com/install-claude-code-plugins-marketplace-guide | Step-by-step: install Claude Code plugins and add a marketplace |
| QCode.cc | https://www.qcode.cc/mcp-servers-ecosystem-2026 | MCP ecosystem: 13,000+ servers, protocol donated to Agentic AI Foundation |
| Groundy | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Official Anthropic marketplace: 101 vetted + 68 partner plugins |
| GitHub / modelcontextprotocol discussions | https://github.com/modelcontextprotocol/modelcontextprotocol/discussions/2316 | "Skills Over MCP Interest Group" office hours notes |

---

## Stats Block

```
├─ 🟠 Reddit: 14 threads
├─ 🔵 X: 18 posts │ 127 likes │ 11 reposts
├─ 🦋 Bluesky: 12 posts │ 313 likes │ 9 reposts
├─ 🌐 Web: 10 pages (engine) + 13 pages (WebSearch supplements)
└─ 🗣️ Top voices: @ClaudeCodeLog, @hasantoxr, @hikikomorphism.bsky.social │ r/ClaudeCode, r/PromptEngineering
```

---

## Data Gaps

- **YouTube: 0 results** - yt-dlp returned no results for this topic despite multiple query attempts. The topic may be too new or too specific for YouTube's indexing. Tutorial content about skills/plugins/MCP servers exists (confirmed via WebSearch) but wasn't surfaced by the engine. Coverage loss is significant for this topic since YouTube is where installation walkthroughs live.
- **TikTok and Instagram: 0 results** - ScrapeCreators API returned HTTP 402 (payment required) on all attempts. No TikTok or Instagram coverage for this window.
- **Hacker News: 0 results** - Despite this being a developer-heavy topic, the HN search returned nothing. The topic string may have been too long for the deterministic fallback planner to construct effective queries. Note: the `--plan` flag passed a file path that was read as empty (likely a race condition with the mktemp cleanup trap), so the engine fell back to deterministic planning with an overly literal long topic string rather than the curated subqueries. A retry with a shorter topic string ("Claude Code skills MCP plugins") would likely surface HN content.
- **Plan injection failure** - The engine log shows "Invalid --plan JSON: Expecting value: line 1 column 1 (char 0)" - the plan file was not read correctly. The engine fell back to deterministic planning. This accounts for some coverage loss and the overly literal query strings used in source searches.
- **Approximate coverage:** ~65% given the Reddit 403s requiring RSS fallback, YouTube 0 results, TikTok/Instagram 402 errors, and HN 0 results. The X/Twitter and Bluesky coverage appears solid. Reddit RSS returned 14 threads which is reasonable.
- **Noise:** Several X posts in the raw evidence are low-signal (general mentions of Claude Code in Japanese, French, Thai, an unrelated real estate MCP use case) and were filtered from synthesis.

---

## Key Quotes

> "NVIDIA open-sourced a security scanner for AI agent skills and the research behind it is more alarming than the tool itself. 26.1% of agent skills contain vulnerabilities, and 5.2% show likely malicious intent. This is from a study of 42,447 skills pulled from major marketplaces." - [@hasantoxr](https://x.com/hasantoxr/status/2065664402301575438) on X

> "I'm considering installing the Pi agent (pi.dev), which is written in TypeScript and installs with npm. Given recent news about npm-based supply chain attacks, I asked Claude about the risk of malware." - [@fpl9000.bsky.social](https://bsky.app/profile/fpl9000.bsky.social/post/3moayr5qg5c2v) on Bluesky

> "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category. Claude Code, OpenCode, Amp, Crush, Pi, aichat, Deer-flow. Each one is an agent harness that runs mostly autonomously in the terminal, against your repo, with permission rails you set." - [@ssp.sh](https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q) on Bluesky

> "The trick here is heterogenous agent teams, like yes mythos/fable as planner, but there's no need to burn opus tokens on medium sized tasks when you can just have mythos manage a team of deepseek/Gemini agents. I suspect this is not a feature Claude Code will offer native support for." - [@hikikomorphism.bsky.social](https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d) on Bluesky (52 likes)

> "people keep asking me this question and my answer is that it is functionally irrelevant because no one is doing this and absolutely everyone is using claude code and midjourney. like there's zero nuance in the actual practical expression here." - [@moomanibe.bsky.social](https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226) on Bluesky (24 likes)

> "Anthropic quietly shipped /workflows in Claude Code 2.1.147 and it might be the biggest shift in how we build multi-agent systems yet." - [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tkjy4u/claude_code_dropped_workflows/)

> "Added claude plugin init <name> to scaffold a new plugin in .claude/skills • Added autocomplete for /plugin arguments: subcommands, installed plugin names, and plugins from known marketplaces" - [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2060460312457810182) on X (19 likes)

> "Microsoft just launched an OpenClaw-style agent in Microsoft Teams. I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers." - [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) on Bluesky (32 likes)
