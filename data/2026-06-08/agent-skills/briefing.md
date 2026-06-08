# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-08
**Query type:** GENERAL
**Sources:** Reddit, X, Hacker News, Bluesky, Polymarket, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 20 threads | — | r/ClaudeAI (13), r/ClaudeCode (5), r/SaaS (1), r/AIAgentsInAction (1) |
| X/Twitter | 13 posts | 108 likes, 17 reposts | @igortr_, @cyrilXBT, @suni_code top voices |
| Hacker News | 25 stories | 2,433 points, 1,487 comments | Strong engagement on mastery post, MS cancellation, dynamic workflows |
| Bluesky | 13 posts | 77 likes, 6 reposts | @carnage4life.bsky.social most engaged |
| Polymarket | 6 markets | — | Claude Commits and model-release markets |
| Web | 9 pages | — | via WebSearch |

---

## Synthesized Findings

### 1. Discovery Is the #1 Pain — A Marketplace Tooling Race Has Begun

The single loudest complaint across [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) and X is that plugin and skill discovery remains fragmented: "scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer: Is this maintained? Does it use hooks or MCP servers? Are people actually using it?" That thread prompted a developer to ship a dedicated searchable directory for Claude Code plugins.

[@igortr_](https://x.com/igortr_/status/2063456699705397630) summed up the problem bluntly: "skills and plugins accumulate faster than you can track them. Found a minimalist app literally called Skills that finally makes this manageable. Want all your Claude Code skills? One click. MCP servers for Cursor? One click. Works across Cursor, Claude Code, Codex, Hermes, Pi, and OpenCode."

Multiple community registries launched in the past 30 days to fill this gap: [CodeGuilds](https://codeguilds.dev) (community registry for skills, agents, MCP servers, 3 pts on HN June 1), a GitOps-style registry for [AI agent Workflows, Skills and MCP servers](https://github.com/Friz-zy/ai-capability-registry) (Show HN, June 4), and the [claudemarketplaces.com](https://claudemarketplaces.com/) directory now indexing 20,300+ skills, 2,500+ marketplaces, and 9,900+ MCP servers updated daily from GitHub.

**Platforms:** Reddit, X, Hacker News, Web

---

### 2. Ecosystem Scale: Skills Crossed From Hobby to Infrastructure

The scale numbers are striking. Per the supplementary web research: the official Anthropic marketplace ([anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)) shipped 101 vetted plugins as of March 2026 plus 68 partner plugins. Third-party community repos dwarf it: [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) (425 plugins, 2,810 skills, 200 agents), [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) (135 agents, 35 curated skills, 176+ plugins). [aitoolanalysis.com](https://aitoolanalysis.com/claude-code-plugins/) puts the total plugin count at 9,000+.

In [r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) a solo non-technical founder described running a marketplace for AI agent skills as their entire business: "1.54M impressions in 3 months, 12.9K clicks, 1,000+ daily active users, Domain rating 43, 1,500+ registered users." The product is Agensi.io, a marketplace where developers find plug-and-play skills and MCP integrations.

**Platforms:** Reddit, Web

---

### 3. The 5-Layer Claude Code Harness Is the Practitioner's Mental Model

The practitioner community has converged on a clean mental model for Claude Code extension. [Franck Parienti on Bluesky](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) stated it most concisely: "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. Le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (the harness has 5 layers; the unintuitive insight: upgrading from Sonnet to Opus gains you less than activating all 5 layers on Sonnet).

[r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/can_someone_explain_the_real_difference_between/) is full of confusion about the vocabulary: "I keep seeing Hooks, Skills, Plugins, SKILL.md, CLAUDE.md, and agents.md thrown around and I've never seen anyone give a concrete example." [mcp.directory](https://mcp.directory/blog/claude-code-skills-vs-subagents-vs-plugins-vs-hooks-2026) published a 12-section reference guide with TL;DR + decision tree that became a frequently-cited answer.

[RoyAmal on X](https://x.com/RoyAmal/status/2063633871875494259) put it more sharply: "Most developers use Claude Code like ChatGPT. That's why they're only getting 10% of the value. The real power starts when you stop prompting and start orchestrating. Skills. Memory. Hooks. Subagents. MCP servers. Not individually. As a system."

**Platforms:** Bluesky, Reddit, X, Web

---

### 4. MCP Server Ecosystem Reaches Critical Mass — And Starts Fragmenting

The MCP registries are proliferating as fast as the servers themselves. Per supplementary research via [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries): PulseMCP hosts 15,930+, Smithery ~7,300 (with hosted-run option, the "Docker Hub" of MCP), Composio 1,000+ toolkits / 20,000+ tools, official MCP Registry ~2,000 — total estimated 13,000+ servers running. Monthly SDK downloads passed 97 million in March 2026.

The infrastructure concern is real. Perplexity CTO Denis Yarats called out two problems at scale: "1) MCP tool descriptions consume 40-50% of context windows before agents do real work; 2) auth flows across many services are unmanageable." The community response is the MCP Gateway pattern — an aggregation layer that centralizes auth and lazy-loads tool descriptions, dropping context usage to 5-15%. Claude Code's own MCP Tool Search feature reduces context by up to 95% via lazy loading, per [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons).

[@cyrilXBT](https://x.com/cyrilXBT/status/2063946654206877823) (62 likes) pointed to a single GitHub repo with 50 MCP servers: "Every superpower your agent needs. Web browsing, file management, app control, workflow automation. Works with Claude Code, Gemini, Codex, and Cursor. 5 categories, MIT licensed."

The most strategically significant MCP event: per [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thkkrb/anthropic_just_bought_the_company_that_generates/), Anthropic acquired Stainless for $300M+. "Stainless was one of the first vendors to extend their compiler to produce MCP servers" alongside the official Python and Node SDKs for OpenAI, Google, Meta, and Anthropic.

**Platforms:** Reddit, X, HN, Web

---

### 5. Dynamic Workflows + Agent View: Claude Code Adds Native Orchestration Primitives

Two official Anthropic posts hit Hacker News with significant engagement this month. "Dynamic Workflows in Claude Code" ([claude.com/blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code)) earned 200 pts and 135 comments (May 28). "Agent View in Claude Code" ([claude.com/blog](https://claude.com/blog/agent-view-in-claude-code)) appeared May 12. These signal Anthropic shipping primitives into the harness itself rather than leaving orchestration entirely to community plugins.

[@zhong19890303](https://x.com/zhong19890303/status/2063826951488606533) shipped Agent Deck in response: "a local-first control center for Claude Code, Codex & Antigravity. Usage, quota, MCP servers, agent skills, chat history & project git — all in one window. No servers. No telemetry. Your tokens never leave your machine. Free & open source."

[Hacker News #48289950](https://arps18.github.io/posts/claude-code-mastery/) — "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs" — earned 450 pts and 254 comments on May 27, the highest-engagement practitioner deep-dive of the month.

**Platforms:** HN, X, Web

---

### 6. Context Bloat From Skills Is a Real Operational Problem

As skills accumulate, context costs spike. From [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tqw1cq/reduced_the_input_token_by_claudecode_to_812k/): "My input usage increased to more than 33-36k tokens for the first message because I was downloading all the skills plugins I heard were useful. I fixed it with a workflow using Opus that scans skill usage in the past 60 days and asks if you want to delete dead ones or keep name-only for middling ones — reduced input tokens by 8-12k."

This matches the broader MCP context problem: more tools = larger system prompt. The community is converging on lazy-loading (Claude Code's MCP Tool Search), cleanup automation, and tiered loading (load skills by task context, not all at once) as the answers.

**Platforms:** Reddit

---

### 7. Skills Go Cross-Tool and Cross-Platform

The ecosystem is visibly de-coupling from any single agent harness. [juftin/skills](https://github.com/juftin/skills) is a "cross-platform agent skills directory compatible with Claude Code, OpenAI Codex CLI, Gemini CLI, and any tool..." [wshobson/agents](https://github.com/wshobson/agents) is a "multi-harness agentic plugin marketplace for Claude Code, Codex CLI, Cursor, OpenCode, and Gemini CLI."

[@igortr_'s](https://x.com/igortr_/status/2063456699705397630) Skills app works "across Cursor, Claude Code, Codex, Hermes, Pi, and OpenCode... create a new skill and deploy it to all your tools at once. No more copying the same thing manually into five different places."

There is also an npm-shaped gap being identified: from [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/theres_an_npmshaped_hole_in_the_ai_tooling_stack/): "One person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup. Claude Code plugins and vendor marketplaces help for sharing inside one vendor's ecosystem but don't cross harness boundaries."

**Platforms:** Reddit, X, Web

---

### 8. Non-Code Use Cases Emerge for Claude Code + MCP

[@Oki10com](https://x.com/Oki10com/status/2063701238315622852): "6 agencias de marketing. 1 iPhone. $30,000 por mes. Todo desde Claude Code con MCP servers. El que dice que Claude Code es solo para código, no lo está usando." (6 marketing agencies. 1 iPhone. $30,000/month. All from Claude Code with MCP servers. Anyone who says Claude Code is only for code isn't using it right.)

[Salesforce launched hosted MCP servers](https://x.com/Sally_ElGhoul/status/2063725486979600474) with a "talk to your Salesforce org in plain English. No code, no UI" pitch. Microsoft open-sourced an MCP playbook (11 modules, Python/TypeScript/Java/Rust/C#/JavaScript, OAuth2, Azure integration) per [@_vmlops](https://x.com/_vmlops/status/2063916937055494571) (11 likes).

Anthropic launched a free course on Agent Skills at [DeepLearning.ai](https://bsky.app/profile/midu.dev/post/3mnmpkxdqsu2i): "Agent Skills step by step from zero. Differences between Skills, Tools and MCP. For Claude Code and VS Code. 2 hours of content, 10 videos." Posted June 6 on Bluesky.

**Platforms:** X, Bluesky

---

### 9. Polymarket on Claude Code Commits and Model Releases

Polymarket has active markets on Claude Code's growth: [Claude Code Commits hit 350k by June 30](https://polymarket.com/event/claude-code-commits-hit-by-june-30) is at 78% (down 14% this week). [Claude Code Commits 650k-700k by end of June](https://polymarket.com/event/claude-code-commits-end-of-june) at 41%. These are the most topically relevant markets; the model-release markets (Claude Mythos at 86%, FrontierMath 57%) reflect broader Anthropic model ambitions rather than the skills ecosystem specifically.

**Platforms:** Polymarket

---

## Cross-Source Patterns

**Pattern 1: Discovery fragmentation drives tooling startups**
Multiple independent builders shipped discovery/management tools this month: a searchable plugin directory (r/ClaudeAI), the "Skills" cross-tool manager app (X/@igortr_), CodeGuilds community registry (HN), and a GitOps-style AI capability registry (HN). All cite the same root cause: skills/MCP servers scatter across GitHub/Discord/blogs with no unified index.

**Pattern 2: "Stop prompting, start orchestrating" is the breakout mental model**
Appeared on X (@RoyAmal), Bluesky (@franckparienti), Reddit (r/ClaudeCode mastery post 450pts), and multiple web tutorials. The 5-layer stack (CLAUDE.md → hooks → skills → plugins → MCP) is the concrete formulation. Boris Cherny's quote circulating on X: "The difference between a mediocre AI engineer and a great one is context management."

**Pattern 3: Context bloat from plugin accumulation is an underappreciated cost**
Reddit (skills optimization -8-12k tokens), MCP ecosystem analysis (40-50% context eaten by tool descriptions), HN discussion of MCP Gateway pattern. Appeared across Reddit, X, and Web sources. The tactical fix is lazy loading; the strategic fix is curated skill stacks over downloading everything.

**Pattern 4: Ecosystem going cross-harness**
Cross-tool skills and cross-harness marketplaces appeared on Reddit (r/ClaudeCode), X (@igortr_), and multiple GitHub repos (juftin/skills, wshobson/agents). Skills written for Claude Code are increasingly expected to work on Codex CLI, Cursor, OpenCode, and Gemini CLI.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | All the AWS Bedrock AgentCore best practices in one Claude Code skill | — | — | "Building on AgentCore normally means the agent crawls across dozens of AWS docs or figures things out by trial and error" | https://www.reddit.com/r/ClaudeAI/comments/1tvqktf/ |
| r/ClaudeAI | I built a searchable directory for Claude Code plugins | — | — | "Discovery is scattered across GitHub, Discord threads, blog posts, and individual repos" | https://www.reddit.com/r/ClaudeAI/comments/1tognh0/ |
| r/ClaudeAI | Reduced input tokens by 8-12k just optimizing skills and plugins | — | — | "My input usage had increased to 33-36k tokens for the first message just downloading all the skills I heard were useful" | https://www.reddit.com/r/ClaudeAI/comments/1tqw1cq/ |
| r/ClaudeAI | We open-sourced a Four-Leaf MCP server + Claude Skill for job search | — | — | "Works with Claude Desktop and Code, Cursor, ChatGPT, Cline, Continue, Windsurf, Perplexity" | https://www.reddit.com/r/ClaudeAI/comments/1tvqbj2/ |
| r/ClaudeAI | Anthropic just bought the company that generates most production MCP servers | — | — | "Stainless was one of the first vendors to extend their compiler to produce MCP servers" | https://www.reddit.com/r/ClaudeAI/comments/1thkkrb/ |
| r/ClaudeAI | I built a 127-skill framework with localhost dashboard and 3-agent orchestration | — | — | "127 skills that auto-load based on your task (say 'deploy to Railway' and the deployment skill loads)" | https://www.reddit.com/r/ClaudeAI/comments/1tixps7/ |
| r/ClaudeCode | Can someone explain the real difference between Hooks, Skills, Plugins, SKILL.md, CLAUDE.md | — | — | "The explanations are always vague or too theoretical" | https://www.reddit.com/r/ClaudeCode/comments/1tmq9kz/ |
| r/ClaudeCode | There's an npm-shaped hole in the AI tooling stack | — | — | "One person builds a vault of skills that 10x their output, and the rest of the team can't replicate it" | https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/ |
| r/ClaudeCode | Share your Setup — skills, subagents, workflows | — | — | "I'd love to see all the /slash commands and loops, skills, subagents, workflows, etc that everyone has built" | https://www.reddit.com/r/ClaudeCode/comments/1tzv5nm/ |
| r/SaaS | 1.5M impressions, 12.9K clicks in 3 months. My entire SEO team is Claude. | — | — | "Running a marketplace for AI agent skills. No engineering team, no marketing team, no SEO agency." | https://www.reddit.com/r/SaaS/comments/1tukbxt/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @igortr_ | "skills and plugins accumulate faster than you can track them. found a minimalist app literally called Skills..." | 2 | 1 | https://x.com/igortr_/status/2063456699705397630 |
| @cyrilXBT | "One GitHub repo. 50 MCP servers. Every superpower your agent needs. Works with Claude Code, Gemini, Codex, and Cursor." | 62 | 9 | https://x.com/cyrilXBT/status/2063946654206877823 |
| @suni_code | "Boris Cherny: 'The difference between a mediocre AI engineer and a great one is context management.'" | 28 | 4 | https://x.com/suni_code/status/2063584980228542543 |
| @RoyAmal | "Most developers use Claude Code like ChatGPT. That's why they're only getting 10% of the value... Skills. Memory. Hooks. Subagents. MCP servers. Not individually. As a system." | — | — | https://x.com/RoyAmal/status/2063633871875494259 |
| @zhong19890303 | "I built Agent Deck — a local-first control center for Claude Code, Codex & Antigravity. No servers. No telemetry." | — | — | https://x.com/zhong19890303/status/2063826951488606533 |
| @Oki10com | "6 agencias de marketing. 1 iPhone. $30,000 por mes. Todo desde Claude Code con MCP servers." | — | — | https://x.com/Oki10com/status/2063701238315622852 |
| @_vmlops | "MICROSOFT OPEN-SOURCED THE COMPLETE MCP PLAYBOOK. Every ai engineer needs to understand model context protocol in 2026" | 11 | 3 | https://x.com/_vmlops/status/2063916937055494571 |
| @m_stefanczyk | "Best upgrade to my Claude Code workflow: dev-browser by Sawyer Hood. It's a plugin that gives Claude real eyes - it drives the browser" | 3 | — | https://x.com/m_stefanczyk/status/2054969718264533016 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 450 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | https://github.com/DrCatHicks/learning-opportunities |
| adamthegoalie | Show HN: adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | — | https://github.com/adamjgmiller/adamsreview |
| nmfisher | Show HN: I threw away my analytics dashboard and replaced it with 42 MCP tools | 5 | 4 | — | https://news.ycombinator.com/item?id=48233125 |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| Friz-zy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| nab | Show HN: Boxes.dev: ditch localhost; run Claude Code and Codex in the cloud | 103 | 77 | — | https://boxes.dev |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @carnage4life.bsky.social | "Microsoft just launched an OpenClaw-style agent in Microsoft Teams. I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers" | 32 | https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" | 1 | https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o |
| @midu.dev | "Nuevo curso gratuito de Anthropic! Agent Skills paso a paso... Para Claude Code y Visual Studio Code. 2 horas de contenido, 10 videos → deeplearning.ai/short-courses/agent-skills-with-anthropic/" | 5 | https://bsky.app/profile/midu.dev/post/3mnmpkxdqsu2i |
| @papoo7.bsky.social | "Your AI Agents Are Aging: Why Agent Lifespan Matters. If you build with Claude or Claude Code, the idea of 'agent aging' should be on your radar." | 2 | https://bsky.app/profile/papoo7.bsky.social/post/3mncvulhkle2e |
| @epicvibecoder.bsky.social | "ECC (everything claude code) drops a full agent harness into claude code, codex, cursor and opencode: skills, memory, instincts, security. MIT, free." | 2 | https://bsky.app/profile/epicvibecoder.bsky.social/post/3mnolsyre5f2k |
| @webchick.bsky.social | "Nothing like completing a code review and updating an agent skill whilst getting shit done." | 2 | https://bsky.app/profile/webchick.bsky.social/post/3mnqkbj3xbs2r |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Claude Code Commits hit 350k by June 30? | 78% (down 14% this week) | — | https://polymarket.com/event/claude-code-commits-hit-by-june-30 |
| Claude Code Commits 650k-700k end of June? | 41% | — | https://polymarket.com/event/claude-code-commits-end-of-june |
| Claude Mythos released by June 30? | 86% | — | https://polymarket.com/event/claude-mythos-released-by |
| Claude score on Humanity's Last Exam by June 30? | 41% (up 23.5% this month) | — | https://polymarket.com/event/anthropic-claude-score-on-humanitys-last-exam-by-june-30 |
| Any Claude model score 50%+ on FrontierMath? | 57% | — | https://polymarket.com/event/anthropic-claude-score-on-frontiermath-benchmark-by-june-30 |
| Will Claude go down 3-5 days in June? | 46% | — | https://polymarket.com/event/will-claude-go-down-on-days-in-june |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| code.claude.com | https://code.claude.com/docs/en/discover-plugins | Official docs: discover and install plugins through marketplaces; plugin creation reference |
| mcp.directory | https://mcp.directory/blog/claude-code-skills-vs-subagents-vs-plugins-vs-hooks-2026 | 12-section guide with decision tree: when to use Skill vs Plugin vs Hook vs Subagent |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community-curated directory: 20,300+ skills, 2,500+ marketplaces, 9,900+ MCP servers |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | MCP registries comparison: PulseMCP 15,930+, Smithery 7,300+, Composio 20,000+ tools |
| aaif.io | https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/ | MCP Dev Summit recap; official registry 800+ servers April 2026; MCP tunnels announced May 19 |
| dev.to/sahil_kat | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | MCP ecosystem overview: Gateway pattern cuts context 5-15%; 97M SDK downloads/month |
| jsmanifest.com | https://jsmanifest.com/claude-code-plugin-packaging-guide | Plugin packaging guide: bundling skills, hooks, subagents, MCP servers into distributable plugins |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Taxonomy explainer: plugins, skills, agents, hooks, MCP, LSP — by 12yr AI/ML practitioner |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official Agent Skills API docs and SDK plugins reference |

---

## Stats Block

```
├─ 🟠 Reddit: 20 threads
├─ 🔵 X: 13 posts │ 108 likes │ 17 reposts
├─ 🟢 HN: 25 stories │ 2,433 points │ 1,487 comments
├─ 🦋 Bluesky: 13 posts │ 77 likes │ 6 reposts
├─ 📊 Polymarket: 6 markets │ Claude Commits 350k: 78% | Claude Mythos: 86%
├─ 🌐 Web: 9 pages
└─ 🗣️ Top voices: @igortr_, @cyrilXBT, @suni_code, @carnage4life.bsky.social │ r/ClaudeAI, r/ClaudeCode
```

---

## Data Gaps

- **YouTube**: 0 results. yt-dlp returned 0 hits for this query; SC YouTube returned HTTP 402. Tutorial and walkthrough videos for Claude Code skills/MCP are certainly being published but were not captured.
- **TikTok / Instagram**: 0 results. SC API returned 0 on TikTok hashtag search (sc key configured but no results surfaced).
- **GitHub**: 0 direct items. No GitHub token available; GitHub API search was skipped. The ecosystem's primary artifact is GitHub repos, so this is a significant gap — many relevant repos appear only via web references.
- **Reddit public API**: 403 errors on initial query; engine fell back to RSS + ScrapeCreators backup, yielding 20 threads. Some high-signal threads may have been missed.
- **Freshness**: Only 44 of 95 dated items are from the last 7 days. The plugin ecosystem is moving fast; some news from late May may now be outdated.
- **Coverage estimate**: ~65%. Social discussion and HN well-covered. YouTube tutorial content, GitHub repo activity, and TikTok creator coverage are the main gaps.

---

## Key Quotes

> "skills and plugins accumulate faster than you can track them. found a minimalist app literally called Skills that finally makes this manageable." — [@igortr_](https://x.com/igortr_/status/2063456699705397630) on X

> "Discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer: Is this maintained? Does it use hooks or MCP servers?" — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/) on plugin discovery

> "le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet" (the unintuitive insight: upgrading Sonnet to Opus gains you less than activating all 5 harness layers on Sonnet) — [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "Most developers use Claude Code like ChatGPT. That's why they're only getting 10% of the value. The real power starts when you stop prompting and start orchestrating." — [@RoyAmal](https://x.com/RoyAmal/status/2063633871875494259) on X

> "The difference between a mediocre AI engineer and a great one is context management." — Boris Cherny (Claude Code creator), quoted by [@suni_code](https://x.com/suni_code/status/2063584980228542543)

> "One person builds up a vault of skills, MCP configs, slash commands, and rule files that 10x their output, and the rest of the team can't replicate the setup. There's an npm-shaped hole in the AI tooling stack." — [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1te2lmk/)

> "6 agencias de marketing. 1 iPhone. $30,000 por mes. Todo desde Claude Code con MCP servers. El que dice que Claude Code es solo para código, no lo está usando." — [@Oki10com](https://x.com/Oki10com/status/2063701238315622852) on X

> "Stainless was one of the first vendors to extend their compiler to produce MCP servers — that's the part of the $300M Anthropic acquisition that matters." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thkkrb/) on the Stainless deal
