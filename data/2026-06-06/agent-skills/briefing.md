# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-06-06
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 7 threads | — | r/ClaudeAI, r/AiBuilders, r/ClaudeWorkflows, r/SaaS, r/claude, r/AIAgentsInAction |
| X/Twitter | 8 posts | 980 likes, 221 reposts | |
| Hacker News | 21 stories | 2,034 points, 1,212 comments | Top story: 528pts |
| Bluesky | 12 posts | 81 likes, 5 reposts | |
| Web | 20 pages | — | 9 engine results + 11 WebSearch supplements |

---

## Synthesized Findings

### 1. The Extension Taxonomy Has Crystallized — And Developers Are Internalizing It

The six-layer Claude Code extension model is now well-understood by the practitioner community. The canonical mental model: CLAUDE.md handles always-on context (rules and facts active every session), Skills handle on-demand workflows (SKILL.md files in `.claude/skills/` invoked with slash commands), MCP servers handle external service connections (GitHub, Postgres, Linear, Sentry), Subagents handle isolation (their own context window, preventing main session bloat), Hooks enforce lifecycle automation architecturally (cannot be reasoned around by the model), and Plugins bundle all of the above into versioned installable units for reuse and distribution.

The highest-engagement HN story in the window — [Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs](https://arps18.github.io/posts/claude-code-mastery/) (449pts, 254cmt, May 27) — is the community's canonical taxonomy reference. [claudefolio.com](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) frames the core distinction precisely: "Skills are for codifying your own workflows in language the model reads; MCP servers give Claude access to systems it can't otherwise reach." [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp) adds the production rule: "Prefer MCP tools over Bash when the integration will be used across sessions."

Platforms discussing this theme: Hacker News, Web, Reddit (r/ClaudeWorkflows), Bluesky.

---

### 2. Marketplace Explosion — Eight Registries in Six Months

The agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. The players diverge on economics, curation, and distribution model:

- **Skills.sh** (Vercel-backed, launched January 2026) — positioned as the npm-style package manager for skills, with a CLI install flow.
- **Agensi** (agensi.io) — security-reviewed paid skills, 8-point checklist before publishing, creators earn 80% of revenue. The solo founder [posted in r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) documenting 1.54M impressions, 12.9K clicks, 1,000+ daily active users, and 1,500+ registered users in 3 months — running the entire SEO operation with Claude.
- **CodeGuilds** ([codeguilds.dev](https://codeguilds.dev)) — community registry for Claude Code skills, agents, and MCP servers, launched June 1, 2026 on HN (3pts, very fresh).
- **Claude Marketplaces** (claudemarketplaces.com) — community-curated directory updated daily from GitHub, cataloging 20,300+ skills, 2,500+ marketplaces, 9,900+ MCP servers.
- **Anthropic official** (anthropics/claude-plugins-official on GitHub) — Anthropic's own curated directory of high-quality Claude Code Plugins.

The distribution strategy emerging from [agensi.io/learn](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026): "Agencies getting traction publish the same capability as a Skill, a GPT, an MCP server, and a Hugging Face Space with platform-specific tuning."

Platforms discussing this theme: Reddit, Web, Hacker News.

---

### 3. The Hackathon Winner Open-Sourced a Reference Architecture — 153K Stars

The highest-signal community endorsement of the week came from a [r/AIAgentsInAction post](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/): a solo developer won the Anthropic hackathon in 8 hours using Claude Code, took the $15,000 prize, then open-sourced the entire stack. The repo — "Everything Claude Code" (ECC) — reached 153,000+ stars on GitHub. It packages 38 specialized agents, 156 skills, 72 commands, and a security scanner with 1,282 tests. Install path: `/plugin marketplace add affaan-m/everything-claude-code`. This is the clearest evidence that the skills/plugin distribution model can produce community-validated canonical tooling at scale.

Platforms discussing this theme: Reddit.

---

### 4. MCP Is Massive — But Security Is Emerging As the Critical Issue

The MCP ecosystem crossed 10,000+ public servers, with [mcp.so, Smithery, and PulseMCP](https://www.truefoundry.com/blog/best-mcp-registries) as the top community registries. Enterprise players are entering: AWS launched the Agent Registry (in Amazon Bedrock AgentCore, now in Preview), and Kong offers a governed MCP Registry with OAuth authentication and auditable tool access.

The most quotable warning came from [@stackzz on X](https://x.com/stackzz/status/2056026387597885457) (75 likes, 12 replies): "MCP tourists are about to get rinsed by their own integrations. The Model Context Protocol pitch is clean... But the bad operator move is connecting servers like they are Chrome extensions. Every MCP server is a permission surface: what can it read? what can it write? can it touch money, keys, deploys, or customer data?" A macOS security audit tool surfaced on X ([@Dinosn, May 14](https://x.com/Dinosn/status/2054907764015591675), 26 likes) giving single-command visibility into all MCP servers, extensions, plugins, connectors, and permissions installed on a machine.

Platforms discussing this theme: X/Twitter, Web, Hacker News.

---

### 5. Cross-Agent Portability Is Becoming a First-Class Goal

A pattern emerging across multiple repos and posts: developers want skills and MCP configs that work across Claude Code, OpenAI Codex CLI, and Gemini CLI without rewriting. The [juftin/skills](https://github.com/juftin/skills) repo (launched May 28-29, 2026) is a "cross-platform agent skills directory - compatible with Claude Code, OpenAI Codex CLI, Gemini CLI, and any tool." [anand-92/skills-registry](https://github.com/anand-92/skills-registry) bills itself as "Your personal GitHub registry for AI Agent Skills. One repo. EVERY agent. EVERY device. Loaded on demand - Zero startup bloat."

The r/AiBuilders thread [We built a tool to keep our coding agents' skills and MCP servers in sync across machines](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/) articulates the pain point: "One of us wrote a naming skill and used it to name a couple of real projects. Then came the tax of copying it onto three machines, into Claude Code, then Cursor, then Codex."

[@oliviacraft.bsky.social](https://bsky.app/profile/oliviacraft.bsky.social/post/3mn65jzmz2o2r) on Bluesky (3 likes) goes deeper: "Claude Code AND Cursor in the same project? You need two files: CLAUDE.md (workflow rules for Claude Code) and .cursor/rules/*.mdc (code patterns for Cursor agent mode). They must agree, not contradict."

Platforms discussing this theme: Reddit, Web, Bluesky.

---

### 6. Anthropic Shipped Vertical Agent Templates — The Plugin Model Going Upstream

Anthropic shipped 10 finance agent templates as plugins (per [r/claude, May 9](https://www.reddit.com/r/claude/comments/1t7xjvs/anthropic_shipped_10_finance_agent_templates_and/)). The post argues the implication is broader than finance: "Each template bundles skills, data connectors, and MCP server configs. Pitch builder, meeting preparer, earnings reviewer — these are full vertical agents delivered as installable plugins." This is the first major example of Anthropic itself using the plugin format as a distribution mechanism for first-party agent capabilities.

Platforms discussing this theme: Reddit.

---

### 7. Workflow Architecture Philosophy — Portability and Decoupling

A quieter but persistent signal: experienced Claude Code users are thinking about long-term architectural portability. [@frankfor.you on Bluesky](https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n) (7 likes): "Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable. Step orchestration, state machines, backoff logic - those should work with any LLM backend."

[@build2launch-ai.bsky.social](https://bsky.app/profile/build2launch-ai.bsky.social/post/3mnaebv74f72j) (6 likes) offers the four-level framework: "task: do it once — workflow: runs every time — app: hand to someone — agent: runs without you. Stop at the level that solves the problem." The r/ClaudeAI "Claude Orchestra" thread ([May 21](https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/)) describes an open-source orchestration layer for managing skills, agents, and MCP servers — scored 90/100 workflow value by the community.

Claude Code Routines ([@papoo7.bsky.social](https://bsky.app/profile/papoo7.bsky.social/post/3mnkqokufxt2g), Jun 5) is a new feature putting agents "on autopilot" — scheduled recurring skill execution.

Platforms discussing this theme: Bluesky, Reddit, Hacker News.

---

### 8. Microsoft Exit and Platform Dynamics

The most-commented HN story in the window: [Microsoft starts canceling Claude Code licenses](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) (493pts, 466cmt, May 22). Microsoft discontinued its Claude Code integration. Simultaneously, [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) (32 likes, most-liked Bluesky post): "Microsoft just launched an OpenClaw-style agent in Microsoft Teams. I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers and Microsoft just got a big leg up in this race." The implication: Microsoft exited as a Claude Code licensee to build its own competing agent product using the same architectural ideas (skills, tools, agent orchestration).

Platforms discussing this theme: Hacker News, Bluesky.

---

## Cross-Source Patterns

**Pattern 1: Skills as the new unit of reusable developer knowledge**
Appearing on: Hacker News (449pts Daily Driver post), Reddit (r/AiBuilders cross-machine sync, r/ClaudeWorkflows Orchestra), Web (claudefolio.com, llmbestpractices.com, boringbot.substack.com), Bluesky (@oliviacraft portability). The skill format (SKILL.md + optional scripts) has become the atomic unit for sharing reusable agent procedures - analogous to npm packages but for agent workflows.

**Pattern 2: Security as the next growth barrier for MCP adoption**
Appearing on: X (@stackzz MCP tourists warning, @Dinosn audit tool), Web (truefoundry.com MCP registries comparison, konghq.com governed registry, aws.amazon.com Agent Registry). The jump from 1 to 10,000+ MCP servers happened with minimal governance; enterprise and security tooling is now racing to catch up. Key quote from [@stackzz](https://x.com/stackzz/status/2056026387597885457): "connecting servers like they are Chrome extensions" is the failure mode.

**Pattern 3: The marketplace is fragmenting before converging**
Appearing on: Web (agensi.io, digitalapplied.com, truefoundry.com), Reddit (r/SaaS Agensi founder post), HN (CodeGuilds). Eight marketplaces in six months is too many to sustain; the developer community is not yet converging on a canonical registry. The Vercel/npm-style Skills.sh is the closest to a gravity-well player but hasn't achieved lock-in.

**Pattern 4: Everything is getting an Anthropic-backed certificate now**
Appearing on: X ([@ds_serena_](https://x.com/ds_serena_/status/2060985378723500048) advertising Claude Code certification for hooks/MCP/SDK), Web (multiple guide sites). Certification programs are emerging around the Claude Code extension ecosystem, signaling maturation and enterprise interest.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/SaaS | 1.5M impressions, 12.9K clicks in 3 months. My entire SEO team is Claude. | — | — | "I'm a solo non-technical founder running a marketplace for AI agent skills." | https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/ |
| r/ClaudeWorkflows | [Workflow] Claude Orchestra: An Open-Source System to Organize and Manage Claude Code Skills, Agents, and MCP Servers | — | — | "Workflow value: 90/100 Status: active" | https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/ |
| r/AiBuilders | We built a tool to keep our coding agents' skills and MCP servers in sync across machines | — | — | "Then came the tax of copying it onto three machines, into Claude Code, then Cursor, then Codex" | https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/ |
| r/ClaudeAI | After a year in Claude Code, the thing slowing me down turned out to be me | — | — | "I kept assuming the way to get faster was a better model or a sharper prompt. It was neither." | https://www.reddit.com/r/ClaudeAI/comments/1ti8cwr/after_a_year_in_claude_code_the_thing_slowing_me/ |
| r/ClaudeAI | 100 Tips & Tricks for Building Your Own Personal AI Agent | — | — | "Everything I learned the hard way — 6 weeks, no sleep, two environments, one agent that actually works." | https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/ |
| r/claude | Anthropic shipped 10 finance agent templates and implication go way beyond finance | — | — | "Each template bundles skills, data connectors, and MCP server configs." | https://www.reddit.com/r/claude/comments/1t7xjvs/anthropic_shipped_10_finance_agent_templates_and/ |
| r/AIAgentsInAction | This guy Won the Anthropic Hackathon Solo. Then He Open-Sourced the Stack | — | — | "38 Agents, 156 Skills, 1,282 Security Tests. 153,000+ GitHub stars." | https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @HeyZaraKhan | 20 Claude GitHub Repos that can completely change your life: Awesome Claude Code, Awesome MCP Servers, SuperClaude Framework... | 668 | 161 | https://x.com/HeyZaraKhan/status/2056422617351959030 |
| @shushant_l | 25 claude code commands — session control, context/memory, code operations, /plugin, /hooks, /doctor | 160 | 35 | https://x.com/shushant_l/status/2056268599648780673 |
| @stackzz | MCP tourists are about to get rinsed by their own integrations. Every MCP server is a permission surface. | 75 | 1 | https://x.com/stackzz/status/2056026387597885457 |
| @Dinosn | Security audit tool for Claude Desktop and Claude Code on macOS — single-command visibility into MCP servers, extensions, plugins | 26 | 4 | https://x.com/Dinosn/status/2054907764015591675 |
| @mimu_ai1 | 15 Claude GitHub Repos that can completely change your life | 26 | 16 | https://x.com/mimu_ai1/status/2056998596072063023 |
| @ds_serena_ | Master Claude Code: hooks, MCP servers & SDK extensions. Earn an Anthropic-backed certificate for your LinkedIn | 6 | 4 | https://x.com/ds_serena_/status/2060985378723500048 |
| @MetaEraCN | Skill 经济：AI Agent 时代被低估的基础设施战争 (Skill Economy: The undervalued infrastructure war in the AI Agent era) | 1 | 0 | https://x.com/MetaEraCN/status/2062434779283534304 |
| @krishdotdev | Top 50 MCP Servers for claude code — Repositories, IDE Integrations, Usage Monitors, Orchestrators | 18 | 0 | https://x.com/krishdotdev/status/2053516887716421859 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| trq212/pretext | Using Claude Code: The unreasonable effectiveness of HTML | 528 | 274 | — | https://twitter.com/trq212/status/2052809885763747935 |
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad |
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 449 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | https://github.com/DrCatHicks/learning-opportunities |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| sabahattink | Show HN: Full Stack HQ – Claude.md and Agent Stack for Claude Code | 10 | 0 | — | https://github.com/sabahattink/antigravity-fullstack-hq |
| ij23 | LiteLLM Agent Platform: Run Claude Code/Codex On-Prem Sandboxes and Vaults | 3 | 0 | — | https://github.com/BerriAI/litellm-agent-platform |
| pretext | Agent View in Claude Code | 5 | 0 | — | https://claude.com/blog/agent-view-in-claude-code |
| jsingh2525 | Arch-Decision – A multi-agent architecture tool for Claude Code | 3 | 1 | — | https://github.com/jsingh6/arch-decision |
| StanAngeloff | Teaching tmux to babysit my Claude Code agents | 3 | 0 | — | https://blog.angeloff.name/post/2026/05/29/teaching-tmux-to-babysit-my-claude-code-agents/ |
| deathmonger5000 | Show HN: Circus Chief – Claude Code, Codex, and Gemini from Your Phone | 4 | 0 | — | https://github.com/ferrislucas/Circus-Chief |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |
| cionut | Show HN: MCP for the ChatGPT Ads API – Query ChatGPT Ads from Claude and Codex | 3 | 1 | — | https://github.com/HYPD-AI/openai-ads-mcp |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | https://codeguilds.dev |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| chaandannn | I built an MCP server so you can ask Claude about your cloud/software bill | 4 | 0 | — | https://getnable.com/ |
| nmfisher | Claude Code and Blender MCP | 3 | 2 | — | https://hydroxide.dev/articles/blender-mcp-claude-code/ |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | https://github.com/openclaw-easy/ViralMint |
| fdarian | agent-dash: TUI for managing Claude Code and OpenCode in tmux | 3 | 0 | — | https://news.ycombinator.com/item?id=48118041 |
| enrique_goudet | Agent CRM: Headless CRM for Claude and Codex | 3 | 0 | — | https://github.com/cluster-software/agent-crm |
| river_otter | Show HN: Train Claude Code's replacement (ds4 and pi and aoe) | 3 | 0 | — | https://github.com/njbrake/dotpi/tree/main |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @carnage4life.bsky.social | Microsoft just launched an OpenClaw-style agent in Microsoft Teams. The combination of Claude Code & OpenClaw style products will be transformational for knowledge workers. | 32 | https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q |
| @bootstrapyouragent.bsky.social | OpenClaw is free. Claude Code is free (with Claude Max). The Mac Mini you probably already own. The only thing between you and a 24/7 AI agent is knowing how to set it up. | 12 | https://bsky.app/profile/bootstrapyouragent.bsky.social/post/3mnbw5b5yew2n |
| @frankfor.you | Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable. | 7 | https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n |
| @llms.activitypub.awakari | With Claude: Less Coding, More Testing. I write a lot less code, but I spend more time under... | 5 | https://bsky.app/profile/llms.activitypub.awakari.com.ap.brid.gy/post/3mn5dz65xfvu2 |
| @jcorvinus.bsky.social | Going over the API or an agent sdk harness/Claude Code? The default web/mobile apps are cognitive war zones; other routes have less of that. | 5 | https://bsky.app/profile/jcorvinus.bsky.social/post/3mnbw5mvlac2r |
| @build2launch-ai.bsky.social | Most people open claude code and think they need to build an app. Wrong starting point. Four levels: task, workflow, app, agent. Stop at the level that solves the problem. | 6 | https://bsky.app/profile/build2launch-ai.bsky.social/post/3mnaebv74f72j |
| @papoo7.bsky.social | Claude Code Routines Put the Agent on Autopilot | 2 | https://bsky.app/profile/papoo7.bsky.social/post/3mnkqokufxt2g |
| @papoo7.bsky.social | Your AI Agents Are Aging: Why Agent Lifespan Matters. If you build with Claude or Claude Code, the idea of "agent aging" should immed… | 2 | https://bsky.app/profile/papoo7.bsky.social/post/3mncvulhkle2e |
| @oliviacraft.bsky.social | Claude Code AND Cursor in the same project? You need two files: CLAUDE.md (workflow rules for Claude Code) and .cursor/rules/*.mdc (code patterns for Cursor agent mode). | 3 | https://bsky.app/profile/oliviacraft.bsky.social/post/3mn65jzmz2o2r |
| @marcus-schuler.com | Supabase $10.5B valuation hinges on Claude Code driving 60%+ of new database creation. Problem: agent-built databases are mostly disposable. | 3 | https://bsky.app/profile/marcus-schuler.com/post/3mnjcmgnda523 |
| @cadaeic.space | Claude Code instance had its own "oh my god agents" moment when it spun up a Gemini agent and the Gemini agent started crawling the folder and breaking into the private GM tools | 2 | https://bsky.app/profile/cadaeic.space/post/3mnchsivz4s2u |
| @githubprojects.bsky.social | Works with Claude Code, Claude Desktop, Codex, OpenCode, and any agent reading from ~/.agents/ — ships with five .example companion files for multilingual deployment | 2 | https://bsky.app/profile/githubprojects.bsky.social/post/3mn7y422a672y |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| arps18.github.io | https://arps18.github.io/posts/claude-code-mastery/ | Canonical daily-driver guide: CLAUDE.md, Skills, Subagents, Plugins, MCPs (449 HN pts) |
| ai-trove.com | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Comprehensive plugin taxonomy with security context |
| claudefolio.com | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Skills vs MCP distinction, slash command mechanics |
| llmbestpractices.com | https://llmbestpractices.com/ai-agents/claude-code-mcp | Production MCP integration patterns and rule: prefer MCP over Bash for recurring integrations |
| llmbestpractices.com | https://llmbestpractices.com/howto/set-up-an-mcp-claude-code-skill | Step-by-step MCP skill setup guide |
| developertoolkit.ai | https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/ | 400+ tutorials, MCP setup in production context |
| github.com/juftin/skills | https://github.com/juftin/skills | Cross-platform skills directory for Claude Code, Codex CLI, Gemini CLI |
| github.com/anand-92/skills-registry | https://github.com/anand-92/skills-registry | Personal GitHub registry for AI Agent Skills, on-demand loading |
| github.com/heyimcarlos/agent-skills | https://github.com/heyimcarlos/agent-skills | Agent skills, subagents, and slash commands for Claude Code, Gemini CLI, Codex CLI |
| github.com/xotong/claude-marketplace | https://github.com/xotong/claude-marketplace | Central plugin marketplace — one URL to configure all team/platform skills |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | Complete 2026 guide: ecosystem taxonomy, production patterns |
| codersera.com | https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/ | Practitioner's guide to Skills and MCP Servers 2026 |
| nimbalyst.com | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | Ranked list of best MCP servers for production |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Every AI skill marketplace and directory 2026 |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | AI agent marketplace discovery and distribution dynamics |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | MCP registries compared: mcp.so, Smithery, PulseMCP, Kong, AWS |
| aws.amazon.com | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry in Amazon Bedrock AgentCore (Preview) |
| code.claude.com | https://code.claude.com/docs/en/features-overview | Official Claude Code "Extend Claude Code" documentation |
| pub.towardsai.net | https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff | All six extension types explained, Agent Teams launch context |
| boringbot.substack.com | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Production multi-agent workflow patterns, plugin bundling |
| claudefa.st | https://claudefa.st/blog/tools/hooks/hooks-guide | Complete guide to all 12 Claude Code lifecycle hook events |

---

## Stats Block

```
├─ 🟠 Reddit: 7 threads
├─ 🔵 X: 8 posts │ 980 likes │ 221 reposts
├─ 🟡 HN: 21 stories │ 2,034 points │ 1,212 comments
├─ 🦋 Bluesky: 12 posts │ 81 likes │ 5 reposts
├─ 🌐 Web: 20 pages (9 engine + 11 WebSearch)
└─ 🗣️ Top voices: @HeyZaraKhan (668L), @stackzz (75L), @carnage4life.bsky.social (32L) │ r/ClaudeAI, r/AiBuilders, r/ClaudeWorkflows
```

---

## Data Gaps

- **YouTube: 0 results** — YouTube search returned 0 items (yt-dlp returned empty results; ScrapeCreators returned HTTP 402 Payment Required). Tutorial and walkthrough content exists but was not captured.
- **TikTok: 0 results** — ScrapeCreators HTTP 402. Short-form video coverage completely absent.
- **Instagram: 0 results** — SC v2 reels endpoint issues with multi-token queries.
- **GitHub: 0 items from engine** — No GitHub token configured; engine fell back to keyword search which returned nothing. The repository data in raw.md (juftin/skills, anand-92/skills-registry, etc.) came from WebSearch grounding, not the GitHub API.
- **Reddit engagement numbers** — Reddit returned 7 threads but no upvote counts; the RSS tier was used due to 403 on the public search API.
- **Freshness warning from engine** — Only 23 of 57 dated items from the last 7 days; roughly 40% of items are from the 2-4 week range.
- **Approximate coverage:** 5/5 core text sources active (Reddit, X, HN, Bluesky, Web). Visual/video sources (YouTube, TikTok, Instagram) = 0%. GitHub project-mode data = 0% (no token). Overall coverage estimate: ~55% of potential signal captured.

---

## Key Quotes

> "MCP tourists are about to get rinsed by their own integrations. Every MCP server is a permission surface: what can it read? what can it write? can it touch money, keys, deploys, or customer data?" — [@stackzz](https://x.com/stackzz/status/2056026387597885457) on X

> "Then came the tax of copying it onto three machines, into Claude Code, then Cursor, then Codex." — [r/AiBuilders](https://www.reddit.com/r/AiBuilders/comments/1tqx770/title_we_built_a_tool_to_keep_our_coding_agents/) on the cross-machine skill sync problem

> "Workflows that decouple from the specific agent architecture are underrated. Claude Code is great for the reasoning component but you want the plumbing to be portable." — [@frankfor.you](https://bsky.app/profile/frankfor.you/post/3mnahck37lx2n) on Bluesky

> "I'm a solo non-technical founder running a marketplace for AI agent skills. No engineering team, no marketing team, no SEO agency. Just me and Claude. 1.54M impressions in 3 months." — [r/SaaS](https://www.reddit.com/r/SaaS/comments/1tukbxt/15m_impressions_129k_clicks_in_3_months_my_entire/) (Agensi founder)

> "Most people open claude code and think they need to build an app. Wrong starting point. Stop at the level that solves the problem." — [@build2launch-ai.bsky.social](https://bsky.app/profile/build2launch-ai.bsky.social/post/3mnaebv74f72j) on Bluesky

> "Microsoft just launched an OpenClaw-style agent in Microsoft Teams. I believe the combination of Claude Code & OpenClaw style products will be transformational for knowledge workers." — [@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mndr2fnsvs2q) on Bluesky

> "Connecting servers like they are Chrome extensions" — [@stackzz](https://x.com/stackzz/status/2056026387597885457) on the MCP security anti-pattern

> "38 specialized agents, 156 skills, 72 commands, and a security scanner with 1,282 tests. 153,000+ GitHub stars." — [r/AIAgentsInAction](https://www.reddit.com/r/AIAgentsInAction/comments/1t84rlc/this_guy_won_the_anthropic_hackathon_solo_then_he/) on the Anthropic hackathon winner's open-sourced stack
