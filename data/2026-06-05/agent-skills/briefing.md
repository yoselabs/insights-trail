# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-05
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 16 threads | N/A upvotes (403 errors), comments vary | r/ClaudeAI, r/ClaudeWorkflows, r/SaaS dominant |
| X/Twitter | 14 posts | 707 likes, 64 reposts | High-signal posts from @hnshah, @hikariraina |
| Hacker News | 11 stories | 770 points, 443 comments | 2 high-engagement stories (448pts, 199pts) |
| Bluesky | 11 posts | 189 likes, 6 reposts | Practitioner sentiment strong |
| Web | 8 pages | — | via grounding; clarista.io, dev.to, toolbrain.net |
| Web (supplements) | 11 pages | — | via WebSearch; agensi.io, claudemarketplaces.com, morphllm.com |

---

## Synthesized Findings

### 1. The Taxonomy Is Finally Settled: Skills vs MCP Servers vs Plugins

The community spent May 2026 arriving at a consensus definition. The canonical split, from [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins): "A skill is instructions that tells the agent what to do, while an MCP server is tools that gives it new things it can do." Plugins are the packaging layer that bundles both into a single installable unit. On Hacker News, the post ["Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs"](https://arps18.github.io/posts/claude-code-mastery/) (448 pts, 253 comments) became the definitive field guide for the May-June window, earning the second-highest engagement of any HN story in the dataset. [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows) produced a cluster of structured workflow guides on the same topic - a "Practical Guide to Claude Code Components" rated 85/100 in workflow value, and "Claude Orchestra: An Open-Source System to Organize and Manage Claude Code Skills, Agents, and MCP Servers" rated 90/100. The practitioner consensus from [codersera.com](https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/): pin one MCP per external system (GitHub, Postgres, Linear, Sentry), then write thin Skills that orchestrate them - skills cost only 30-50 tokens of context until invoked, while a five-server MCP setup can cost 50k+ tokens upfront.

**Platforms:** Hacker News, Reddit, Web

### 2. The Marketplace Explosion: From 1 Registry to 8+ in Six Months

The community notes the agent skills ecosystem grew from a single registry in December 2025 to eight major marketplaces by Q2 2026. [claudemarketplaces.com](https://claudemarketplaces.com/) aggregates 20,400+ skills, 9,900+ MCP servers, and 2,500+ marketplaces. [LobeHub](https://lobehub.com/skills) has 169,739 skills indexed. [skills.sh](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) has tracked 87,000+ unique skills since launch. Anthropic launched its official managed directory in May 2026 and hit GitHub Trending the same day - flagged by [@probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mm77jqufje2c). The official directory ships 101 vetted plugins + 68 partner plugins from GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase. [buildwithclaude.com](https://buildwithclaude.com/) catalogs 515+ practical extensions. [agensi.io](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/)'s solo founder reported 1.54M impressions, 12.9K clicks in 3 months, built entirely with Claude doing all SEO, marketing, and development.

**Platforms:** Reddit, X/Twitter, Bluesky, Web

### 3. Anthropic Shipped Dynamic Workflows and Finance Templates

Two official Anthropic releases dominated the "what's new" signal. ["Dynamic Workflows in Claude Code"](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) hit HN with 199 points and 135 comments - the official blog post describing a workflow-generation feature inside Claude Code. Separately, Anthropic released 10 finance agent templates as plugins for Claude Cowork and Claude Code. Per [r/claude](https://www.reddit.com/r/claude/comments/1t7xjvs/anthropic_shipped_10_finance_agent_templates_and/): "They released ten ready to run agent templates that work as plugins in cowork and claude code which are pitch builder, meeting preparer, earnings reviewer etc etc, each template bundles skills, data connectors, and custom hooks into a single installable unit." The community note: implications extend well beyond finance - any domain can bundle skill sets the same way. Anthropic's Knowledge Work Plugins (noted by [@everydevai.bsky.social](https://bsky.app/profile/everydevai.bsky.social/post/3mmwdi4dw6a2s)) give Claude "role-specific skills for sales, finance, legal, data, and more via plain markdown and JSON files. No code, no infra."

**Platforms:** Hacker News, Reddit, Bluesky

### 4. MCP as "USB for AI" - Cross-Client Adoption Accelerating

[clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide)'s framing stuck: "Think of MCP as USB for AI: one protocol, many tools, many clients." The [official MCP registry](https://modelcontextprotocol.io/docs/getting-started/intro) hit 9,400+ servers in 2026, with the protocol now supported by OpenAI, Google, Cursor, and the majority of IDEs. Blender MCP integration appeared on HN ([hydroxide.dev](https://hydroxide.dev/articles/blender-mcp-claude-code/)). Snyk + Claude Code real-time security scanning. Community-maintained servers cover databases (Postgres, MySQL, SQLite), file storage (Google Drive, Box), Slack, Jira, Asana, Supabase, n8n, Figma. Crucially, xAI's Grok shipped the same skills/plugins/marketplaces architecture in May 2026 - per [docs.x.ai](https://docs.x.ai/build/features/skills-plugins-marketplaces), Grok discovers skills from `./.grok/skills/`, `~/.grok/skills/`, and any enabled plugin's `skills/` directory. The architecture is becoming cross-agent standard.

**Platforms:** Hacker News, Web, Bluesky

### 5. Security Scrutiny Arrives as Plugin Count Scales

The first signs of organized security thinking around the ecosystem appeared this period. [@hikariraina](https://x.com/hikariraina/status/2054021469559246907) published a Japanese-language X thread that got X traction: "What you should be looking at in Claude Code Plugins/Marketplaces is not 'extensions have increased' but how to review the distributed permission sets." The five-point pre-install checklist: (1) what skills/agents/hooks/MCP are included, (2) whether there are mutation tools, (3) how auto-updates are handled, (4) local cache and rollback, (5) which marketplaces are approved for your team. The key insight: "Plugin installation is not just adding prompts - it is adding operational components." On the supply side, [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) scans every skill against an 8-point checklist before going live: prompt injection, data exfiltration, secret detection, dangerous commands, obfuscation, external fetches, credential access, privilege escalation.

**Platforms:** X/Twitter, Web

### 6. Community-Built Extensions Fill Gaps the Official Directory Doesn't

The practitioner community is shipping fast. On [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tsx85s/i_made_a_plugin_that_turns_your_projects_into/), a developer shipped `/app-it` - a skill that turns any project into a clickable dock app, eliminating the `npm install && npm run build && npm run dev` loop. [adamsreview](https://github.com/adamjgmiller/adamsreview) (Show HN: 85pts, 55cmt) provides better multi-agent PR reviews for Claude Code. [CodeGuilds](https://codeguilds.dev) launched as a community registry specifically for Claude Code skills, agents, and MCP servers. [@_vmlops](https://x.com/_vmlops/status/2062852830109769921) shipped "compound engineering" - a plugin for Claude Code, Codex, and Cursor built on the idea that every unit of engineering work should make the next one easier: `/ce-brainstorm` → `/ce-plan` → `/ce-work` → `/ce-code-review` → `/ce-compound` (document learnings). On Bluesky, [@camilleroux.com](https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p) listed 13 notable 2026 skills including one that cuts 63% of output tokens, one that replays sessions like video, and one that transforms a codebase into an explorable graph.

**Platforms:** Reddit, Hacker News, Bluesky, X/Twitter

### 7. Multi-Agent + Shared Skill Sets: The Advanced Pattern

Power users are running multi-agent setups sharing skill and MCP infrastructure. [@hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v) (115 likes on Bluesky, the highest single-post engagement in the Bluesky set): "im pretty much now at the place where i can confidently run five to six simultaneous claude sessions across two repos each chugging on a separate task and reliably not actually writing code. i don't think i've opened neovim at all in the past two weeks. thanks to @ed3d.net's plugins/skills." [@agentic_james](https://x.com/agentic_james/status/2062853847777734710) described running Claude Code and Codex as agents in a single system "messaging each other, sharing a task board, running 24/7 in a daemon I control from Telegram" - calling it cortextOS. [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1t5x2v2/workflow_atomic_agent_design_for_robust_claude/) published "Atomic Agent Design for Robust Claude Code Skills and Plugins" (value 75/100, advanced level): breaking complex tasks into atomic skill units to prevent agent state corruption.

**Platforms:** Bluesky, X/Twitter, Reddit

### 8. The Boardroom Framing: Skill Libraries as Company AI Strategy

[@hnshah](https://x.com/hnshah/status/2062647149582750101)'s post "Every Company's First AI Strategy Should Be a Skill Library" earned 701 likes and 59 reposts on X - the highest single-item engagement across the entire X dataset. This signals the discourse moving from individual developer tooling to enterprise AI strategy framing. The logic: instead of buying model access and hoping for magic, companies should invest in curated skill libraries that encode institutional knowledge into reusable agent capabilities. This framing appeared the same week Anthropic's Knowledge Work Plugins shipped role-specific skills for sales, finance, legal, and data teams.

**Platforms:** X/Twitter, Bluesky, Reddit

### 9. Pain Points: Persona Switching and Plugin Distribution

Two friction points dominated complaints. [@TeeArAich](https://x.com/TeeArAich/status/2062853125233393875): "switching claude code 'personas' is a mess. providers, prompts, skills, hooks — all separate toggles that don't move together. tried cc-switch. it swaps the provider and soul but leaves the rest behind." Building a fix in public. On the distribution side, [refactix.com](https://refactix.com/ai-development-engineering/claude-code-plugins-packaging-integrations-distribution) named the real problem: "The hard part is not building those pieces. The hard part is getting them onto every engineer's laptop, in sync, without each person hand-editing dotfiles." A harness regression (v2.1.154-2.1.158) in late May caused widespread tool channel corruption - [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1tskdus/psa_if_claude_has_been_acting_up_this_week_its_a/) documented "garbled tool calls causing mass hallucination" and noted the workaround costs Opus 4.8 access.

**Platforms:** X/Twitter, Reddit, Web

---

## Cross-Source Patterns

**Pattern 1: Skills/MCP/Plugin taxonomy coalescing across platforms**
The three-layer model (Skills = instructions, MCP = tools, Plugins = packaging) is now cited consistently across Hacker News (448pt post), Reddit (r/ClaudeWorkflows guides), and Web (morphllm.com, codersera.com, clarista.io). One month ago this was contested; today it is consensus.
- Key quote: "A skill is instructions that tells the agent what to do, while an MCP server is tools that gives it new things it can do." - [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)

**Pattern 2: Security scrutiny as the ecosystem scales**
Security review before installing plugins appeared on X (@hikariraina's 5-point checklist), on marketplace supply side (Agensi's 8-point scan), and in practitioner web guides. This pattern tracks the maturation arc of any plugin ecosystem (npm, VSCode extensions) - security consciousness arrives when the catalog becomes too large to evaluate individually.
- Key quote: "Plugin installation is not just adding prompts, it is adding operational components." - [@hikariraina](https://x.com/hikariraina/status/2054021469559246907)

**Pattern 3: "Skill library as enterprise AI strategy" framing going mainstream**
@hnshah's 701-like X post, Anthropic's Knowledge Work Plugins for role-specific teams, and the r/SaaS posts about using Claude to run entire departments (SEO, marketing) as solo founders all converge on the same idea: organizational knowledge encoded as skills is the durable AI investment.
- Key quote: "Every Company's First AI Strategy Should Be a Skill Library" - [@hnshah](https://x.com/hnshah/status/2062647149582750101) (701 likes)

**Pattern 4: Cross-agent architecture as the advanced pattern**
Multi-agent with shared skill sets appeared on Bluesky (@hailey.at running 5-6 sessions), X (@agentic_james' cortextOS), and Reddit (Claude Orchestra, Atomic Agent Design). The pattern: orchestrate multiple Claude (and non-Claude) agents sharing a single skill and MCP layer.
- Key quote: "im pretty much now at the place where i can confidently run five to six simultaneous claude sessions across two repos... thanks to @ed3d.net's plugins/skills." - [@hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v) (115 likes)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeWorkflows | [Workflow] Claude Orchestra: Open-Source System to Organize Claude Code Skills, Agents, MCP Servers | N/A | N/A | "Workflow value: 90/100. Level: advanced." | https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/ |
| r/ClaudeWorkflows | [Workflow] Practical Guide: CLAUDE.md, Skills, Hooks, Plugins, and AGENTS.md Hierarchy | N/A | N/A | "Workflow value: 85/100. Status: active." | https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/ |
| r/ClaudeWorkflows | [Workflow] Atomic Agent Design for Robust Claude Code Skills and Plugins | N/A | N/A | "Level: advanced. Building robust agents by breaking down complex tasks." | https://www.reddit.com/r/ClaudeWorkflows/comments/1t5x2v2/workflow_atomic_agent_design_for_robust_claude/ |
| r/ClaudeAI | I made a plugin that turns your projects into clickable dock apps | N/A | N/A | "It's called /app-it. I built it because I make a lot of small apps, tools, and weird AI-assisted experiments." | https://www.reddit.com/r/ClaudeAI/comments/1tsx85s/i_made_a_plugin_that_turns_your_projects_into/ |
| r/SaaS | 1.5M impressions, 12.9K clicks in 3 months. My entire SEO team is Claude. | N/A | N/A | "I'm a solo non-technical founder running a marketplace for AI agent skills." | https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/ |
| r/claude | Anthropic shipped 10 finance agent templates and implications go way beyond finance | N/A | N/A | "Each template bundles skills, data connectors, and custom hooks into a single installable unit." | https://www.reddit.com/r/claude/comments/1t7xjvs/anthropic_shipped_10_finance_agent_templates_and/ |
| r/ClaudeCode | PSA: harness regression 2.1.154–2.1.158, not the model | N/A | N/A | "Everything traces back to tool channel corruption." | https://www.reddit.com/r/ClaudeCode/comments/1tskdus/psa_if_claude_has_been_acting_up_this_week_its_a/ |
| r/ClaudeAI | 100 Tips & Tricks for Building Your Own Personal AI Agent | N/A | N/A | "Everything I learned the hard way — 6 weeks, no sleep." | https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/ |
| r/ClaudeAI | After a year in Claude Code, the thing slowing me down turned out to be me | N/A | N/A | "I kept assuming the way to get faster was a better model or a sharper prompt. It was neither." | https://www.reddit.com/r/ClaudeAI/comments/1ti8cwr/after_a_year_in_claude_code_the_thing_slowing_me/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @hnshah | Every Company's First AI Strategy Should Be a Skill Library | 701 | 59 | https://x.com/hnshah/status/2062647149582750101 |
| @hikariraina | What you should be looking at in Claude Code Plugins/Marketplaces is not 'extensions have increased' but how to review the distributed permission sets. | N/A | N/A | https://x.com/hikariraina/status/2054021469559246907 |
| @_vmlops | compound engineering — it's a plugin for claude code, codex, cursor: /ce-brainstorm → /ce-plan → /ce-work → /ce-code-review → /ce-compound | N/A | N/A | https://x.com/_vmlops/status/2062852830109769921 |
| @TeeArAich | switching claude code "personas" is a mess. providers, prompts, skills, hooks — all separate toggles that don't move together. | N/A | N/A | https://x.com/TeeArAich/status/2062853125233393875 |
| @agentic_james | I found the best way to run Claude Code and Codex together... agents messaging each other, sharing a task board, running 24/7. This is cortextOS. | N/A | N/A | https://x.com/agentic_james/status/2062853847777734710 |
| @thebitig | Claude Code Keşfedilince 1.800 Dolarlık Landing Page Maliyeti Ortadan Kalktı (entrepreneur saved $1,800/landing page with Claude Code) | 6 | 5 | https://x.com/thebitig/status/2062852854902141055 |
| @hasanfr_0rg | Switch to Claude Code or Cursor with flat-rate plans. Audit your agentic workflows — they're the biggest cost driver. | N/A | N/A | https://x.com/hasanfr_0rg/status/2062853030622687235 |
| @JulianGoldieSEO | The most powerful AI coding tool on the planet is actually free to run. Claude Code isn't autocomplete. It works at the project level. | N/A | N/A | https://x.com/JulianGoldieSEO/status/2062852521186734270 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 448 | 253 | (Definitive field guide for the stack) | https://arps18.github.io/posts/claude-code-mastery/ |
| mil22 | Dynamic Workflows in Claude Code | 199 | 135 | (Official Anthropic blog; new feature release) | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| adamthegoalie | Show HN: adamsreview – better multi-agent PR reviews for Claude Code | 85 | 55 | (Multi-agent PR review tool) | https://github.com/adamjgmiller/adamsreview |
| anideshp | Show HN: Agent FM – local, open-source radio for Claude Code and Codex agents | 9 | N/A | (Ambient audio layer for agent sessions) | https://github.com/agentfm-ai/agent-fm |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | N/A | (Internal architecture deep-dive) | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| sermakarevich | Show HN: Generate Claude Code Workflows using Spec Driven Development | 5 | N/A | (Spec-driven workflow generation) | https://news.ycombinator.com/item?id=48306730 |
| nmfisher | Claude Code and Blender MCP | 3 | N/A | (3D design tool + MCP integration) | https://hydroxide.dev/articles/blender-mcp-claude-code/ |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | N/A | (Community-built alternative registry) | https://codeguilds.dev |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @hailey.at | "im pretty much now at the place where i can confidently run five to six simultaneous claude sessions... thanks to @ed3d.net's plugins/skills." | 115 | https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v |
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours curating a mod list for a Game of Thrones-themed total conversion..." | 34 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @camilleroux.com | "Mon top 13 des skills et plugins Claude Code qui ont marqué 2026: celui qui coupe 63% des tokens de sortie, celui qui rejoue tes sessions comme une vidéo..." | 8 | https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p |
| @jefferyharrell.bsky.social | "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 10 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @humancoders.com | "Top 13 skills et plugins Claude Code qui ont marqué 2026: audit de dette technique, réduction de tokens, best practices en prod..." | 5 | https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p |
| @everydevai.bsky.social | "Knowledge Work Plugins by @AnthropicAI gives Claude role-specific skills for sales, finance, legal, data, and more via plain markdown and JSON files. No code, no infra." | 3 | https://bsky.app/profile/everydevai.bsky.social/post/3mmwdi4dw6a2s |
| @viriditax.bsky.social | "when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it" | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @probbrain.bsky.social | "GitHub Trending: Anthropic launched an official managed directory of high-quality Claude Code Plugins." | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mm77jqufje2c |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| dev.to (alexcloudstar) | https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532 | How Skills, MCP Servers, and Plugins actually fit together; frontend-design skill real-world demo |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Comprehensive plugin taxonomy: skills, agents, hooks, MCP, LSP explained by AI/security veteran |
| refactix.com | https://refactix.com/ai-development-engineering/claude-code-plugins-packaging-integrations-distribution | Plugin distribution problem: "The hard part is getting them onto every engineer's laptop, in sync" |
| buildwithclaude.com | https://buildwithclaude.com/ | 515+ practical extensions across Claude.ai, Claude Code, and Claude API |
| toolbrain.net | https://toolbrain.net/blog/guide-building-ai-powered-development-workflows-with-mcp-and-agentic-pipelines/ | "The winning setup in 2026 pairs Claude Code with MCP servers inside a CI/CD pipeline that runs agents as first-class build steps" |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | MCP as "USB for AI" canonical framing; installation patterns |
| docs.x.ai | https://docs.x.ai/build/features/skills-plugins-marketplaces | xAI/Grok adopting same skills/plugins/marketplaces architecture — cross-agent standardization |
| dev.to (wonderlab) | https://dev.to/wonderlab/one-open-source-project-a-day-no-70-claude-plugins-official-a-complete-tour-of-anthropics-4lgo | Tour of Anthropic's official open-source plugin registry |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | "A skill is instructions that tells the agent what to do, while an MCP server is tools that gives it new things it can do." |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Marketplace landscape survey; Agensi's 8-point security checklist |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregator: 20,400+ skills, 9,900+ MCP servers, 2,500+ marketplaces |
| lobehub.com | https://lobehub.com/skills | 169,739 skills for Claude, Codex & ChatGPT |
| modelcontextprotocol.io | https://modelcontextprotocol.io/docs/getting-started/intro | Official MCP docs; 9,400+ servers in registry as of 2026 |
| codersera.com | https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/ | Token economics: skills ~30-50 tokens until invoked; 5-server MCP = 50k+ tokens upfront |
| sitepoint.com | https://www.sitepoint.com/model-context-protocol-mcp/ | MCP cross-client adoption: OpenAI, Google, Cursor, majority of IDEs |
| agentskillshub.dev | https://agentskillshub.dev/ | Secure marketplace for AI agents |
| kdnuggets.com | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 Agent Skill Marketplaces overview |
| agence-scroll.com | https://agence-scroll.com/en/blog/mcp-claude-guide-2026 | MCP complete guide: Claude, Cursor, n8n workflows |

---

## Stats Block

```
├─ 🟠 Reddit: 16 threads │ N/A upvotes (403 errors) │ N/A comments
├─ 🔵 X: 14 posts │ 707 likes │ 64 reposts
├─ 🟢 HN: 11 stories │ 770 points │ 443 comments
├─ 🦋 Bluesky: 11 posts │ 189 likes │ 6 reposts
├─ 🌐 Web: 19 pages (8 grounded + 11 supplemental)
└─ 🗣️ Top voices: @hnshah, @hikariraina, @hailey.at, @jefferyharrell.bsky.social │ r/ClaudeWorkflows, r/ClaudeAI, r/SaaS
```

---

## Data Gaps

- **YouTube: 0 results.** yt-dlp search returned nothing on the full topic string; SC YouTube returned HTTP 402. Significant gap - this topic almost certainly has tutorial/demo content on YouTube that was not captured.
- **TikTok: 0 results.** ScrapeCreators API returned no TikTok results; the topic may have limited TikTok presence or hashtag resolution was insufficient.
- **Instagram: 0 results.** SC's v2 reels endpoint frequently 500s on multi-token queries.
- **Reddit upvote data: unavailable.** Public Reddit API returned 403 for all search queries; engagement counts for Reddit threads are missing from this briefing. Community size is inferred from thread relevance and curator notes in r/ClaudeWorkflows.
- **GitHub: 0 results.** No GitHub token configured; anthropics/claude-code and modelcontextprotocol/servers data not pulled directly.
- **Planner: deterministic fallback.** The query plan file was not read by the engine (empty file error); the engine fell back to its deterministic internal planner. This may have slightly reduced targeting precision vs. the manually-crafted plan.
- **Coverage estimate: ~65%.** Strong signal from HN, Bluesky, X; Reddit present but without engagement metrics; YouTube/TikTok/Instagram absent entirely.

---

## Key Quotes

> "Every Company's First AI Strategy Should Be a Skill Library" — [@hnshah](https://x.com/hnshah/status/2062647149582750101) on X (701 likes)

> "im pretty much now at the place where i can confidently run five to six simultaneous claude sessions across two repos each chugging on a separate task and reliably not actually writing code. i don't think i've opened neovim at all in the past two weeks. thanks to @ed3d.net's plugins/skills." — [@hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v) on Bluesky (115 likes)

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky (34 likes)

> "A skill is instructions that tells the agent what to do, while an MCP server is tools that gives it new things it can do." — [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)

> "What you should be looking at in Claude Code Plugins/Marketplaces is not 'extensions have increased' but how to review the distributed permission sets. Plugin installation is not just adding prompts — it is adding operational components." — [@hikariraina](https://x.com/hikariraina/status/2054021469559246907) on X

> "The hard part is not building those pieces. The hard part is getting them onto every engineer's laptop, in sync, without each person hand-editing dotfiles." — [refactix.com](https://refactix.com/ai-development-engineering/claude-code-plugins-packaging-integrations-distribution)

> "Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky (10 likes)

> "I found the best way to run Claude Code and Codex together. Not two tools side by side, but agents in one system messaging each other, sharing a task board, running 24/7 in a daemon I control from Telegram." — [@agentic_james](https://x.com/agentic_james/status/2062853847777734710) on X

> "I'm a solo non-technical founder running a marketplace for AI agent skills. No engineering team, no marketing team, no SEO agency. Just me and Claude." — [r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) (Agensi founder, 1.54M impressions)

> "Think of MCP as USB for AI: one protocol, many tools, many clients." — [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide)
