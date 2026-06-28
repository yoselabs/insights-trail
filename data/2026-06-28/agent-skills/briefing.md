# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-28
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 17 threads | 1,963 upvotes, 388 comments | r/ClaudeAI, r/ChatGPT |
| X/Twitter | 70 posts | 37,144 likes, 3,781 reposts | High noise from crypto accounts; ~20 on-topic posts |
| Hacker News | 27 stories | 4,532 points, 1,972 comments | Strong signal: Show HN tooling, security research |
| Bluesky | 11 posts | 83 likes, 6 reposts | Developer community, plugin builders |
| GitHub | 8 items | 23 reactions, 88 comments | PRs/issues from anthropics/claude-code, PostHog, community |
| Web | 27 pages | — | 16 via engine (Exa); 11 via WebSearch supplement |
| YouTube | 0 videos | — | 402 errors; ScrapeCreators exhausted |
| TikTok | 0 videos | — | 402 errors |
| Instagram | 0 reels | — | 402 errors |
| Polymarket | 0 markets | — | No prediction markets on this topic |

---

## Synthesized Findings

### 1. The `claude-code-setup` Plugin Is the Talk of the Week

Anthropic's official `claude-code-setup` plugin dominated X/Twitter this week (clustered Jun 27-28) with three separate viral threads all pushing the same message: most Claude Code installs are running at a fraction of their capacity. The plugin scans your actual codebase and tells you exactly which hooks, skills, MCP servers, and subagents to activate - then configures itself automatically. Per [@rushu888](https://x.com/rushu888/status/2070847111009391029): "Claude Code without setup is half of what it can be... You no longer have to guess anything. You just run the command and the setup configures itself. `/plugin install claude-code-setup@claude-plugins-official`"

The deeper concern driving the attention: context bloat. [@EvanLuthra](https://x.com/EvanLuthra/status/2070797128289710544) (88 likes, 35 replies) stated it plainly - "Every MCP server you add loads its full tool list into your context window the second your session starts. Stack too many and you're burning context before you type a word. So the move was never 'add more.' It's 'add the right ones.'" This reframes the entire skills/MCP conversation from feature-counting to curation discipline. The thread drew 35 replies, many developers describing bloated setups they'd built over months.

[@chenzeling4](https://x.com/chenzeling4/status/2071051965057094088) confirmed Anthropic's official plugin directory had hit 31.2K GitHub stars: "This is the curated marketplace they maintain themselves. Internal and external plugins, install with one slash command. Each one bundles skills, agents, MCP servers, or slash commands."

### 2. Affaan Mustafa's Hackathon Build Becomes a Reference Architecture

A GitHub repo from Affaan Mustafa - winner of an Anthropic hackathon - is spreading as a template for what a "pro Claude Code setup" looks like. Per [@ArchiveExplorer](https://x.com/ArchiveExplorer/status/2070836753326383205) (39 likes, 4 reposts): "He won Anthropic's own hackathon with it - then gave the whole thing away for free. It turns Claude Code from one assistant into a full engineering team: → 28 specialized subagents → 119 reusable skills → 60 slash commands → 14 MCP servers → 20+ automated hooks... 99,000 stars. MIT. one-line install."

[@0_x_Bender](https://x.com/0_x_Bender/status/2070982230399484020) added: "~200K stars. Built inside an Anthropic hackathon. 119 skills. 60 slash commands. 14 MCP servers. An AgentShield layer running 1,282 security tests on its own config." This specific build demonstrates how the primitives (skills, MCP servers, subagents, hooks) compound - the individual pieces are modest, but the assembled harness is viral-worthy. It also signals that the "full engineering team" framing is sticking.

[@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (Alex Albert, head of Claude Code at Anthropic) captured the gestalt with 557 likes: "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team."

### 3. The Marketplace Ecosystem Exploded to 84,000+ Catalogued Tools

The [Skillselion state-of-skills 2026 report](https://skillselion.com/state-of-ai-agent-skills-2026) tracks 84,232 curated tools: 65,787 agent skills, 7,787 MCP servers, and 8,273 marketplaces, with 108M combined installs. The agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. Major platforms:

- **[skills.sh](https://skillselion.com/state-of-ai-agent-skills-2026)** (Vercel-backed, Jan 2026): npm-style CLI installer (`npx skills add`) working across 40+ agents - Claude Code, Codex CLI, Cursor, OpenClaw. ~2,000 skills catalogued.
- **[Smithery](https://smithery.ai/docs/concepts/cli)**: Docker Hub equivalent for MCP ecosystem, 7,000+ servers; install locally or run as hosted remote servers.
- **[SkillsMP](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)**: 800,000+ skills (largest catalog but quality varies widely).
- **Anthropic official** ([anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json)): 101 vetted plugins + 68 partner plugins (GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, Firebase).
- **[CodeGuilds](https://codeguilds.dev)**: community registry for Claude Code (skills, agents, MCP servers) - [appeared on HN](https://news.ycombinator.com/item?id=48357494) June 1.
- **[MCP Registry (NPM-style)](https://mcp-registry-dh5.pages.dev)**: Show HN submission - NPM-style install for MCP servers.
- **AWS official**: AWS released official MCP servers, skills, and plugins for cloud tasks (CloudFormation, CDK, Lambda) working with Claude Code, Codex, Cursor, and Kiro.

### 4. The Three-Layer Confusion Problem: Skills vs MCP vs Plugins

The single most-produced content category this month is "explain the difference." Multiple independent guides emerged trying to resolve the same confusion: per [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) - "People treat plugins, skills, and MCP servers as three options on the same menu, then get confused when the comparison doesn't quite work."

The [dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) practitioner guide put it most practically: "I put off Claude Code skills for six months because the docs made them sound like a framework. Then I opened one and it was a markdown file." Per [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-plugins-2026) and [claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/), the canonical distinction is: **Skills teach Claude how** (procedure, markdown instructions), **MCP gives Claude tools** (running process, external services), **plugins bundle both** (distribution format). [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) adds connectors as a fourth layer for enterprise (Okta-provisioned, zero-touch).

The practical rule emerging from [dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon): pick the lightest abstraction that solves the problem - plain CLI script first, then skill, then MCP server, then full plugin. This "lightest first" heuristic is gaining traction as an antidote to over-engineering.

Anthropic's [official blog post](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) covers dynamic workflows - Claude Code can now write and orchestrate its own multi-agent harness on the fly - adding a fourth dimension to the existing three-layer model.

### 5. Production MCP Pain: Auth Loops, Context Bloat, Integration Tax

The most-replied X thread this week wasn't about features - it was a complaint. [@Shpigford](https://x.com/Shpigford/status/2070951057358807246) (50 likes, 20 replies): "am i taking crazy pills or did MCP servers in @claudeai code start having constant auth issues? i'm basically having to re-auth 3-5 times a day for multiple MCPs. claude itself is saying i AM taking crazy pills and it's always been this way." The replies confirmed widespread experience with auth instability.

The [r/ClaudeAI production MCP thread](https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/) (64 pts, 38 comments) from a developer shipping agents across logistics and fintech documented the harder reality: "The day-to-day is mess. One specific kind of mess: MCP servers in production." Persistent auth, rate limits, and inconsistent behavior under load were cited as the main failure modes.

[@_itsjustshubh](https://x.com/_itsjustshubh/status/2071069613270483366) framed the systemic issue: "integration is exactly it. the model is the easy part. getting it to talk to your actual data sources reliably is where most agent projects actually die." This matches the [HN "AI agent bankrupted their operator" thread](https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/) (1,467 pts, 535 comments) and [AI agent runs amok in Fedora](https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/) (552 pts, 245 comments) - the combination of real tool access and poor guard rails producing runaway actions.

A [GitHub bug on anthropics/claude-code](https://github.com/anthropics/claude-code/issues/63966) (9 reactions, 7 comments) documents tool-call results arriving empty in the live UI and flushing late/out-of-order in parallel batches - a direct MCP reliability issue at the platform level. [@alexalbert__](https://x.com/alexalbert__/status/2065494053379293447) acknowledged the underlying problem: "We're working on a few potential fixes for this in the prompt and in future models. This is more of a stopgap until those land."

### 6. Security: Supply Chain Risk Is Now the Top Industry Concern

The security picture darkened this month. Per [Snyk ToxicSkills research](https://snyk.io/articles/top-claude-skills-cybersecurity-hacking-vulnerability-scanning/) (cited in WebSearch supplements): prompt injection in 36% of skills tested, 1,467 malicious payloads found across the ecosystem. [SentinelOne's analysis](https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/) documents the attack vector: "Malicious skills can redirect library installations to attacker-controlled sources, ensuring trojanized versions are pulled into projects, with malicious code embedded capable of exfiltrating secrets, monitoring traffic, or lying dormant until triggered."

[Datadog Security Labs](https://securitylabs.datadoghq.com/articles/malicious-skills-supply-chain-risks-in-coding-agents-with-dynamic-context/) documented that "once enabled, marketplace plugin skills remain available across sessions and continue to shape how the agent behaves in the future" - the persistence is the threat. A cloned repo can bring skills into a trusted Claude Code session even if the developer never installed a marketplace skill.

[Prompt Security's analysis](https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code) covers the dependency hijack vector specifically for Claude Code. In February 2026, 1,184 malicious skills poisoned an agent marketplace - the first supply chain risk designation of an American AI company by its own government, per earlier reporting in WebSearch.

In response, [Trail of Bits](https://github.com/trailofbits/skills) released Claude Code skills for security research, vulnerability detection, and audit workflows. [latiotech/secure-supply-chain-skills](https://github.com/latiotech/secure-supply-chain-skills) provides a supply chain security plugin for Claude Code. The [MCP Dev Summit 2026](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/) (April 2-3, NYC, 1,200 attendees) had security as the single most-represented theme with 23 dedicated sessions.

### 7. Enterprise: MCP Dev Summit and the Registry-as-Control-Plane Pattern

The [MCP Dev Summit North America 2026](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/) (AAIF, April 2-3) drew 1,200 attendees and 95 sessions marking MCP's shift from developer toy to enterprise infrastructure. Key data point: Uber reported 5,000+ engineers, 10,000+ internal services, 1,500+ monthly active agents, 60,000+ agent executions per week connecting Claude to Salesforce, Jira, wikis, and Snowflake daily.

The enterprise pattern crystallizing per [chatforest.com](https://chatforest.com/guides/mcp-dev-summit-2026-guide/): "Organizations deploying MCP at scale converged on the same conclusion: they need a centralized gateway paired with a registry as the control plane for all agent interactions." The registry provides both discovery and security - scanning agent configurations for dangerous combinations.

Anthropic's own enterprise rollout: Claude Managed Agents with sandboxed execution and private MCP servers, plus Okta-integrated connector provisioning (zero-touch for users). [LawNext](https://www.lawnext.com/2026/05/anthropic-goes-all-in-on-legal-releasing-more-than-20-connectors-and-12-practice-area-plugins-for-claude.html) covered May 2026's legal sector push - 20+ MCP connectors + 12 practice-area plugins. The [2026 MCP roadmap](https://tedt.org/MCPs-2026-Roadmap/) prioritizes: transport evolution for stateless HTTP scaling, agent communication, governance/audit trails, and SSO-integrated auth.

### 8. Cross-Agent Portability: Skills as the Lingua Franca

The most interesting trend in the background: skills escaping Claude Code-only lock-in. The [gaal CLI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) (r/ClaudeAI, 3 pts, 5 comments) addresses the multi-agent syncing problem - "If you use Claude Code alongside any other coding agent (Cursor, Codex, Windsurf), same project means different rules filename per agent. Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules..." Their CLI keeps all in sync across machines.

[skills.sh](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) is explicitly cross-agent - one installer for 40+ runtimes. [Bluesky](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) surfaced ECC: "63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together."

The [ArXiv Skilldex paper](https://arxiv.org/html/2604.16911v1) formalizes this with hierarchical scope-based distribution for agent skill packages - suggesting the community is starting to build theoretical foundations under what has been ad-hoc practice.

### 9. Community Tooling: The Meta-Layer Builders

A cluster of community tools aim to improve the Claude Code developer experience itself, separate from extending what it can do:

- **[Pulse](https://github.com/nikitadoudikov/claude-pulse)** (HN, 39 pts): Dashboard for Claude Code - approve tool calls from your phone. The insight: in agentic mode, the bottleneck shifts from writing code to approving it. [@_itsjustshubh](https://x.com/_itsjustshubh/status/2071069389009428701): "the review queue problem is real and nobody talks about it. 10x output means 10x the surface area you have to hold in your head to approve."
- **[Recall](https://github.com/raiyanyahya/recall)** (HN, 136 pts, 86 comments): Local project memory for Claude Code.
- **[Ponytail](https://github.com/DietrichGebert/ponytail)** (HN, 98 pts; r/ClaudeAI, 609 pts, 87 comments): "Make your AI agent think like the laziest senior dev in the room." The skill intercepts over-delivery - "Ask for email validation and you get a 27-line EmailValidator class with a wrapper and a regex that's somehow still wrong" - channeling the 'long ponytail, oval glasses, seen it all' developer archetype.
- **[/app-it](https://www.reddit.com/r/ClaudeAI/comments/1tsx85s/i_made_a_plugin_that_turns_your_projects_into/)** (r/ClaudeAI, 1,102 pts): Plugin turning projects into clickable dock apps - one click instead of `npm install && npm run dev`.
- **[Claude Code for Visual Studio](https://github.com/firish/claude_code_vs)** (HN, 20 pts): Native diff with accept/reject.
- **[Claude Code Issue management for VS Code](https://www.forq.ink/)** (HN, 9 pts): Extension for managing issues from within VS Code.
- **[macOS quota gauges](https://github.com/grzegorz-raczek-unit8/claude-quota)** (HN, 69 pts): Menu bar gauges for Claude Code quota usage.

[jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes) had the week's most quoted observation: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character."

---

## Cross-Source Patterns

**Pattern 1: "Add the right ones, not more" - Context discipline emerging**
Appeared on X (EvanLuthra 88 likes, cyrilXBT 91 likes, rushu888 65 likes), Reddit (r/ClaudeAI production MCP thread), and Bluesky (jefferyharrell's "what it really needs is mods" - curation framing). The consensus is shifting from "how many extensions can I add" to "which ones actually help vs. burn context." The claude-code-setup plugin's value proposition is entirely built around this thesis.

**Pattern 2: Tool as team, not assistant**
Multiple platforms coalesced on the "managing a team" metaphor. @alexalbert__ (X, 557 likes): "feels less like using a tool and more like managing a team." @ArchiveExplorer (X): "turns Claude Code from one assistant into a full engineering team." r/ClaudeAI (multiple threads): developers describing 28-agent setups. HN: "My Agent Skill for Test-Driven Development" (251 pts) - skills as team member specializations.

**Pattern 3: Security gap in marketplace trust**
Appeared on X (implicit in security plugin discussions), HN (AI agent bankrupted / runs amok stories, 1,467 + 552 pts), GitHub (anthropics/claude-code MCP bug), and Web (SentinelOne, Datadog, Prompt Security). The skill/plugin ecosystem grew faster than the trust infrastructure. 36% prompt injection rate and 1,467 malicious payloads are the numbers crystallizing this concern.

**Pattern 4: Cross-agent portability pressure**
Bluesky (ECC: Claude Code + Cursor + Codex), Reddit (gaal CLI for multi-agent sync), Web (skills.sh 40+ agents), ArXiv (Skilldex formal model). SKILL.md is becoming the lingua franca - same format, different runtimes. Developers are refusing to maintain separate knowledge files per tool.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I gave Claude Code a "lazy senior dev" mode and it writes like 6x less code | 609 | 87 | "I built Ponytail. It channels the senior dev everyone knows. Long ponytail, oval glasses, seen it all." | https://www.reddit.com/r/ClaudeAI/comments/1u3k2ed/ |
| r/ClaudeAI | I made a plugin that turns your projects into clickable dock apps | 1,102 | 76 | "Instead of running npm install, npm run build... you just click an icon and the app opens." | https://www.reddit.com/r/ClaudeAI/comments/1tsx85s/ |
| r/ClaudeAI | I ship AI agents in production. The mess is MCP. | 64 | 38 | "The day-to-day is mess. One specific kind of mess: MCP servers in production." | https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/ |
| r/ClaudeAI | tested Claude Fable 5 and Opus 4.8 across 917 coding-agent scenarios. Fable won by 0.9 points. | 103 | 94 | "The tasks came from skills in tessl.io/registry and were evaluated both with and without the relevant skill loaded." | https://www.reddit.com/r/ClaudeAI/comments/1u3vyk7/ |
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | 3 | 5 | "Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules..." | https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/ |
| r/ClaudeAI | Going back to work after a break. Where do I start with Claude Code? | 2 | 11 | "My team has switched to using Claude Code for almost all of their tasks." | https://www.reddit.com/r/ClaudeAI/comments/1ufu1hj/ |
| r/ClaudeAI | All you'll need is an AI model; all other "tools" will become obsolete. | — | 19 | "Skills, hooks, MCP, connectors, harness engineering... is said that by utilizing these tools appropriately, AI can perform at its best." | https://www.reddit.com/r/ClaudeAI/comments/1u74v0d/ |
| r/ClaudeAI | Every agent tool I tried dumps all the agents into one workspace | 4 | 5 | "The problem with one workspace is that it forces very different kinds of things to live in the same place." | https://www.reddit.com/r/ClaudeAI/comments/1ubrkmg/ |
| r/ClaudeAI | Plug Claude into whatever you are working on | 39 | 17 | "BugBuster - an open-source, open-hardware bench instrument... enables AI agents to interface directly with HW closing the loop." | https://www.reddit.com/r/ClaudeAI/comments/1u0oigm/ |
| r/ClaudeAI | Understand what Claude did, instantly | 26 | 7 | "Now that everyone is shipping 10 times faster with their own team of agents, we have become the bottleneck." | https://www.reddit.com/r/ClaudeAI/comments/1uct6vf/ |
| r/ChatGPT | Consolidate ecommerce exports into actionable reorder alerts. Skill included. | — | 1 | "I built this as a portable AI-agent Skill - a single SKILL.md with reusable instructions you can adapt to your agent setup." | https://www.reddit.com/r/ChatGPT/comments/1ufaw09/ |
| r/ChatGPT | Standardize retail purchase approvals across stores. Skill included. | 1 | 3 | "I built this as a Claude Skill - a single SKILL.md you can drop into a Claude Code or Claude Agent SDK project." | https://www.reddit.com/r/ChatGPT/comments/1ts10qm/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 557 | 15 | https://x.com/alexalbert__/status/2069470389391241314 |
| @cyrilXBT | "UNLEASH WHAT CLAUDE CODE WAS MEANT TO DO • Suggests and auto-installs the right hooks, skills, MCP servers, and subagents" | 91 | 12 | https://x.com/cyrilXBT/status/2070796831320351010 |
| @EvanLuthra | "Your Claude Code setup is probably bloated... Stack too many and you're burning context before you type a word." | 88 | 2 | https://x.com/EvanLuthra/status/2070797128289710544 |
| @rushu888 | "Claude Code without setup is half of what it can be. Until you install claude-code-setup - Anthropic's official plugin" | 65 | 17 | https://x.com/rushu888/status/2070847111009391029 |
| @Shpigford | "am i taking crazy pills or did MCP servers in @claudeai code start having constant auth issues? i'm basically having to re-auth 3-5 times a day" | 50 | 1 | https://x.com/Shpigford/status/2070951057358807246 |
| @ArchiveExplorer | "He won Anthropic's own hackathon with it - then gave the whole thing away for free. 28 subagents, 119 skills, 60 slash commands, 14 MCP servers" | 39 | 4 | https://x.com/ArchiveExplorer/status/2070836753326383205 |
| @0_x_Bender | "~200K stars. Built inside an Anthropic hackathon. 119 skills. 60 slash commands. 14 MCP servers. An AgentShield layer running 1,282 security tests" | 32 | 12 | https://x.com/0_x_Bender/status/2070982230399484020 |
| @alexalbert__ | "Pulled this from our prompting guide which has many more tips for working with Fable" | 109 | 5 | https://x.com/alexalbert__/status/2065493242158924031 |
| @alexalbert__ | "@NeroHSN We're working on a few potential fixes for this in the prompt and in future models. This is more of a stopgap until those land" | 27 | — | https://x.com/alexalbert__/status/2065494053379293447 |
| @N0V4Dev | "AWS just released an official toolkit... It provides MCP servers and plugins that give these agents the specific knowledge and guardrails they need for cloud tasks" | 3 | 2 | https://x.com/N0V4Dev/status/2070816988423700702 |
| @chenzeling4 | "Anthropic shipped an official plugin directory for Claude Code. This is the curated marketplace they maintain themselves. ⭐ 31.2K" | 1 | — | https://x.com/chenzeling4/status/2071051965057094088 |
| @RJMcGirr | "my main reason for sticking with Claude code... my existing subscription and org wide deployment of projects, skills, custom MCP servers" | 2 | 1 | https://x.com/RJMcGirr/status/2071082461434663172 |
| @_itsjustshubh | "building MCP servers / claude code plugins on the side while full-time at FAANG in NYC" | 4 | — | https://x.com/_itsjustshubh/status/2071017162479644926 |
| @_itsjustshubh | "integration is exactly it. the model is the easy part. getting it to talk to your actual data sources reliably is where most agent projects actually die" | — | — | https://x.com/_itsjustshubh/status/2071069613270483366 |
| @_itsjustshubh | "the review queue problem is real and nobody talks about it. 10x output means 10x the surface area you have to hold in your head to approve" | — | — | https://x.com/_itsjustshubh/status/2071069389009428701 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| xiaoyu2006 | AI agent bankrupted their operator while trying to scan DN42 | 1,467 | 535 | — | https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/ |
| tanelpoder | AI agent runs amok in Fedora and elsewhere | 552 | 245 | — | https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/ |
| kkm | How to setup a local coding agent on macOS | 507 | 127 | — | https://ikyle.me/blog/2026/how-to-setup-a-local-coding-agent-on-macos |
| prakashqwerty | AI Agent Guidelines for CS336 at Stanford | 503 | 153 | — | https://github.com/stanford-cs336/assignment1-basics/blob/main/CLAUDE.md |
| laxmena | My Agent Skill for Test-Driven Development | 251 | 109 | — | https://www.saturnci.com/my-agent-skill-for-test-driven-development.html |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| tvissers | A €0.01 bank transfer could compromise a banking AI agent | 208 | 202 | — | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |
| ruxudev | Build a Basic AI Agent from Scratch: Long Task Planning | 142 | 53 | — | https://medium.com/@rogi23696/build-a-basic-ai-agent-from-scratch-long-task-planning-14e803f9bd6d |
| mateenah | Show HN: Recall – Local project memory for Claude Code | 136 | 86 | — | https://github.com/raiyanyahya/recall |
| mellosouls | Ponytail – make your AI agent think like the laziest senior dev in the room | 98 | 17 | — | https://github.com/DietrichGebert/ponytail |
| grzracz | Show HN: macOS menu bar gauges for your Claude Code quota | 69 | 40 | — | https://github.com/grzegorz-raczek-unit8/claude-quota |
| nikitadvd | Show HN: Pulse – Dashboard for Claude Code, approve tool calls from your phone | 39 | 15 | — | https://github.com/nikitadoudikov/claude-pulse |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 36 | 12 | — | https://news.ycombinator.com/item?id=48546618 |
| firish | Show HN: Claude Code for Visual Studio (native diff with accept/reject) | 20 | 8 | — | https://github.com/firish/claude_code_vs |
| fabianlindfors | Show HN: Claude Code for Visual Studio (native diff with accept/reject) | 15 | 2 | — | https://twitter.com/andrewmccalip/status/2065049432652189933 |
| kabirgoel | Kickbacks: An ad marketplace for coding agent spinners | 15 | 2 | — | https://twitter.com/andrewmccalip/status/2065049432652189933 |
| tvissers | How to build and serve MCP servers without effort | 15 | — | — | https://flama.dev/blog/building_an_mcp_server_with_flama/ |
| ayi | Ask HN: Anthropic banned me from using Claude Code and I don't know what to do | 81 | 93 | — | https://news.ycombinator.com/item?id=48641160 |
| hbarka | Show HN: Web Speed – A shared web-map registry for AI agents (MCP, open source) | 7 | 4 | — | https://www.getwebspeed.io/ |
| Dominic_P | Show HN: Web Speed – A shared web-map registry for AI agents (MCP, open source) | 7 | 4 | — | https://www.getwebspeed.io/ |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| PengSpirit | Show HN: MCP Registry – NPM-style install for MCP servers | 3 | — | — | https://mcp-registry-dh5.pages.dev |
| JohnDSDev | Ask HN: Do you use Claude Code, Codex, or something else? | 9 | 23 | — | https://news.ycombinator.com/item?id=48612758 |
| hbarka | Ask HN: What technique do you use to make Claude Code deterministic? | 8 | 11 | — | https://news.ycombinator.com/item?id=48610280 |
| barakolshe | Claude Code Issue management extension for VS Code | 3 | 1 | — | https://www.forq.ink/ |
| pjungwir | My Claude Code Setup | 11 | 1 | — | https://illuminatedcomputing.com/posts/2026/06/my-claude-code-setup/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list..." | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | "I use my own local tools, not Claude code, but I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @viriditax.bsky.social | "when newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried to do with it to flex it" | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — a free, MIT-licensed system" | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @brunopedro.com | "42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise." | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @github-trending-js.bsky.social | "Ruflo is a multi-agent AI orchestration framework that extends Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation" | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @probbrain.bsky.social | "GitHub Trending: AWS releases official MCP servers, skills, and plugins enabling AI agents to build cloud infrastructure" | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |
| @mikaelbuilds.bsky.social | "Claude Code 'still running' is not one bug. I built a no-secret packet for v2.1.179-style remote failures" | 1 | https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| anthropics/claude-code | [BUG] Tool-call results empty in live UI then flush late/out-of-order (Bash, Read, MCP, advisor) - macOS, Opus 4.8 | 9 | 7 | https://github.com/anthropics/claude-code/issues/63966 |
| PostHog/posthog | feat(agent_platform): kernel skills + MCP builder playbooks | — | 8 | https://github.com/PostHog/posthog/pull/66211 |
| rjmurillo/ai-agents | feat(cli): add --pack flag for optional skill packs (Fixes #2509) | — | 3 | https://github.com/rjmurillo/ai-agents/pull/2601 |
| emirhankudun-ux/SEIS | Add CLAUDE.md: operating instructions + test improvement roadmap | 4 | 29 | https://github.com/emirhankudun-ux/SEIS/pull/11 |
| emirhankudun-ux/SEIS | feat: package SEIS ultimate demo for GitHub review | 1 | 12 | https://github.com/emirhankudun-ux/SEIS/pull/54 |
| Trancendos/Tranc3 | feat(compliance+townhall): integrate Magna-Carta framework | — | 17 | https://github.com/Trancendos/Tranc3/pull/121 |
| NoMoneyDaddy/One_Botton_Done_Project | feat: plugin/marketplace readiness, skill crystallization, agent manifest | — | 3 | https://github.com/NoMoneyDaddy/One_Botton_Done_Project/pull/2 |
| GlacierEQ/kilocode | sync to main (Kilo fork) | — | 9 | https://github.com/GlacierEQ/kilocode/pull/2 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Skillselion | https://skillselion.com/state-of-ai-agent-skills-2026 | State of AI Agent Skills 2026: 84,232 tools catalogued, 65,787 skills, 7,787 MCP servers, 8,273 marketplaces, 108M installs |
| claude.com/blog | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Anthropic's official blog: Claude Code can now write/orchestrate its own multi-agent harness dynamically |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Practitioner's "lightest first" decision guide: CLI → skill → MCP → plugin |
| dev.to | https://dev.to/malik_chohra/how-to-write-a-claude-code-skill-and-the-gotchas-the-docs-skip-3gn5 | From-scratch SKILL.md guide with undocumented gotchas |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Three-layer explanation: skills (procedure/markdown), MCP (tools/process), plugins (bundle format) |
| mcsaguru.com | https://mcsaguru.com/how-to-write-a-claude-code-skill | Build-your-own SKILL.md guide: description trigger, instructions, scripts, testing, sharing |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | "Should I write a skill or set up an MCP server?" answered definitionally |
| claudskills.com | https://claudskills.com/learn/writing-a-skill-md-file/ | Practical SKILL.md walkthrough for first-time builders |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Four-way comparison including connectors (enterprise provisioning layer) |
| maketocreate.com | https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/ | Opinionated skills-vs-MCP guide from a practitioner who built both in production |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries comparison: mcp.so, Smithery, PulseMCP; Anthropic does not operate canonical registry |
| truefoundry.com | https://www.truefoundry.com/blog/claude-mcp-registry | Claude MCP Registry complete guide for developers and enterprise teams |
| firecrawl.dev | https://www.firecrawl.dev/blog/claude-code-skill | How to create a Claude Code skill: web scraping example |
| agentscamp.com | https://agentscamp.com/guides/mcp/claude-code-mcp-setup | Adding MCP servers: local, remote, project-scoped; commit .mcp.json for team sharing |
| computingforgeeks.com | https://computingforgeeks.com/claude-code-mcp-servers-setup/ | Complete MCP server setup guide: local, remote HTTP, scopes, tokens, troubleshooting |
| toolchew.com | https://toolchew.com/en/how-to-use-mcp-with-claude-code/ | Custom MCP server in TypeScript + .mcp.json registration tutorial |
| github.com/guangzibodong/skillhub | https://github.com/guangzibodong/skillhub | SkillHub: universal skill registry and runtime layer for AI agents (new project, Jun 2026) |
| Agensi | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Comprehensive marketplace landscape: 8 major marketplaces by Q2 2026; Skills.sh, Smithery, SkillsMP comparison |
| Smithery | https://smithery.ai/docs/concepts/cli | Smithery CLI documentation: 7,000+ MCP servers, hosted remote server option |
| AAIF | https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/ | MCP Dev Summit NA 2026 recap: 1,200 attendees, Uber 60K+ executions/week, security 23 sessions |
| Digital Applied | https://www.digitalapplied.com/blog/mcp-dev-summit-2026-readout-protocol-roadmap-analysis | MCP 2026 roadmap: transport evolution, governance, audit trails, SSO auth |
| SentinelOne | https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/ | Dependency hijack via marketplace skills: persistent threat across sessions |
| Datadog Security Labs | https://securitylabs.datadoghq.com/articles/malicious-skills-supply-chain-risks-in-coding-agents-with-dynamic-context/ | Malicious skills supply chain risk: credential exfiltration, ClawHub/OpenClaw ecosystem |
| Prompt Security | https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code | Dependency hijack analysis: cloned repos bring untrusted skills into trusted sessions |
| LawNext | https://www.lawnext.com/2026/05/anthropic-goes-all-in-on-legal-releasing-more-than-20-connectors-and-12-practice-area-plugins-for-claude.html | Anthropic legal sector expansion: 20+ MCP connectors, 12 practice-area plugins (May 2026) |
| Chatforest | https://chatforest.com/guides/mcp-dev-summit-2026-guide/ | MCP Dev Summit: centralized gateway + registry as enterprise control plane pattern |
| ArXiv | https://arxiv.org/html/2604.16911v1 | Skilldex: formal hierarchical scope-based distribution model for agent skill packages |

---

## Stats Block

```
├─ 🟠 Reddit: 17 threads │ 1,963 upvotes │ 388 comments
├─ 🔵 X: 70 posts │ 37,144 likes │ 3,781 reposts
├─ 🟢 HN: 27 stories │ 4,532 points │ 1,972 comments
├─ 🦋 Bluesky: 11 posts │ 83 likes │ 6 reposts
├─ 🐙 GitHub: 8 items │ 23 reactions │ 88 comments
├─ 🌐 Web: 27 pages
└─ 🗣️ Top voices: @alexalbert__, @EvanLuthra, @Shpigford, @ArchiveExplorer │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 videos** - yt-dlp returned 0 results across all 4 query variants; ScrapeCreators returned HTTP 402 (quota exhausted). Significant gap: YouTube likely has substantial Claude Code skills/plugin tutorial content. Retry with ScrapeCreators quota reset.
- **TikTok: 0 videos** - ScrapeCreators HTTP 402. Short-form skill demos would likely surface on TikTok.
- **Instagram: 0 reels** - ScrapeCreators HTTP 402. Lower expected relevance for dev tooling.
- **Polymarket: 0 markets** - No prediction markets found on Claude Code skills/plugin topics; expected for a developer tooling topic.
- **X noise level: ~60-70%** - Approximately 40-50 of the 70 X posts were off-topic (crypto accounts @aze_gen and @trythreews generated high volume but zero relevance; included in engine counts but excluded from analysis). Signal/noise ratio for relevant X posts is high on the ~20 on-topic posts.
- **Reddit coverage: adequate but sparse** - r/ClaudeAI returned 17 threads but the dedicated subreddit search returned 0 from the dedicated-subreddit lane (RSS feed failures). Community likely has more activity on MCP production pain points.
- **GitHub: no token** - Engine used unauthenticated GitHub REST tier (low rate limit). `anthropics/claude-plugins-official` and `modelcontextprotocol/servers` project-mode searches were skipped due to no GitHub token. Full star counts, release notes, and README content unavailable for official repos.
- **Estimated coverage:** ~75-80% of available signal. Main gaps are YouTube (tutorials), deeper GitHub project data, and full X corpus (crypto noise inflated total count).

---

## Key Quotes

> "Your Claude Code setup is probably bloated and you don't even know it. Every MCP server you add loads its full tool list into your context window the second your session starts. Stack too many and you're burning context before you type a word. So the move was never 'add more.' It's 'add the right ones.'" — [@EvanLuthra](https://x.com/EvanLuthra/status/2070797128289710544) on X (88 likes)

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) on X (557 likes)

> "am i taking crazy pills or did MCP servers in @claudeai code start having constant auth issues? i'm basically having to re-auth 3-5 times a day for multiple MCPs." — [@Shpigford](https://x.com/Shpigford/status/2070951057358807246) on X (50 likes, 20 replies)

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky (35 likes)

> "I put off Claude Code skills for six months because the docs made them sound like a framework. Then I opened one and it was a markdown file." — [dev.to](https://dev.to/malik_chohra/how-to-write-a-claude-code-skill-and-the-gotchas-the-docs-skip-3gn5)

> "integration is exactly it. the model is the easy part. getting it to talk to your actual data sources reliably is where most agent projects actually die" — [@_itsjustshubh](https://x.com/_itsjustshubh/status/2071069613270483366) on X

> "He won Anthropic's own hackathon with it - then gave the whole thing away for free. 28 specialized subagents, 119 reusable skills, 60 slash commands, 14 MCP servers, 20+ automated hooks. 99,000 stars. MIT. one-line install." — [@ArchiveExplorer](https://x.com/ArchiveExplorer/status/2070836753326383205) on X (39 likes)

> "The day-to-day is mess. One specific kind of mess: MCP servers in production." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tuqqpn/i_ship_ai_agents_in_production_the_mess_is_mcp/) (64 upvotes)

> "the review queue problem is real and nobody talks about it. 10x output means 10x the surface area you have to hold in your head to approve" — [@_itsjustshubh](https://x.com/_itsjustshubh/status/2071069389009428701) on X

> "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." — [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) on Bluesky
