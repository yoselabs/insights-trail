# Agent Skills & Claude Code Plugin Ecosystem — Daily Briefing
**Date:** 2026-06-21
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 7 threads | — | r/ClaudeWorkflows, r/artificial |
| X/Twitter | 23 posts | 20,401 likes, 1,508 reposts | @claudeai, @regent0x_, @ClaudeCodeLog |
| Bluesky | 12 posts | 86 likes, 6 reposts | @jefferyharrell.bsky.social, @uermel.bsky.social |
| GitHub | 15 items | 660 reactions, 163 comments | anthropics/claude-code, PostHog/posthog, openai/codex |
| Web | 31 pages | — | Engine (18) + WebSearch supplements (13) |

---

## Synthesized Findings

### 1. Claude Code Artifacts Launch — Skills and Plugins Get a Sharing Surface

The biggest signal of the period is Anthropic's June 18 Artifacts launch. [@claudeai](https://x.com/claudeai/status/2067671912038240487) announced Artifacts with 17,774 likes and 1,274 reposts: "Interactive pages built from your session, like a PR walkthrough or a living project dashboard, shared with your team at a private link." A follow-up post (544 likes) drove home the key message: ["Artifacts draw on the full context of your session: codebase, plugins, skills, connected tools."](https://x.com/claudeai/status/2067671914533863585) This positions the skill/plugin layer as the source of Artifact richness — teams with deeper plugin stacks can generate richer shared docs. Available in beta on Team and Enterprise plans. The community also noted Claude Code 2.1.152's addition of the `/reload-skills` command (per [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2059451400338223550)) — skills now live-reload without restarting a session, and admins can allowlist org marketplaces for context-aware plugin suggestions.

### 2. The Taxonomy War — Skills vs MCP vs Plugins vs Connectors vs Hooks

The loudest editorial signal is practitioners trying to make sense of five overlapping extension surfaces. [Tygart Media](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) (June 13), [AgentWay](https://agentway.dev/en/claudecode/skills) (June 21), [ai-trove.com](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins), and [hidekazu-konishi.com](https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html) all published decision guides within the same week. The canonical split per [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368): "A skill is a focused instruction pack for one repeatable workflow — e.g. code review rules or Postgres SQL generation. A plugin is an installable bundle that can include skills, agents, hooks, MCP/LSP servers, and other extensions. Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." The practitioner heuristic from [Clarista](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) and [DEV Community](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon): start with the lightest primitive (CLI → skill → MCP → plugin) and add weight only when needed. MCP servers cost 50K+ tokens of context upfront; skills cost ~30-50 tokens until invoked.

The MCP architecture principle from [Anthropic's co-creator David Soria Parra](https://x.com/pauliusztin_/status/2063236967987298550), cited by practitioners: "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together."

### 3. Marketplace Explosion — From One Registry to Eight in Six Months

The ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026, per [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). Major marketplaces now include:
- **[claudemarketplaces.com](https://claudemarketplaces.com/)** — largest community directory, 300K+ monthly developers, 21,600+ skills, 12,500+ MCP servers
- **[Skills.sh](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)** — Vercel-backed, launched January 2026, npm-style `npx skills add` CLI, cross-client (Claude Code, Codex, Cursor, OpenClaw)
- **[jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)** — 425 plugins, 2,810 skills, 200 agents at tonsofskills.com
- **[sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills)** — 1,600+ agentic skills, multi-client, MIT-licensed
- **[Agensi](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide)** — security-reviewed paid skills with 8-point checklist (prompt injection, exfiltration, secret detection, dangerous commands, obfuscation, external fetches, credential access, privilege escalation)

The npm publishing path is now formalized via [neovateai/agent-skill-npm-boilerplate](https://github.com/neovateai/agent-skill-npm-boilerplate) — fork, edit SKILL.md, `npm publish`, globally discoverable. Individual developers are also shipping personal plugin repos: [chirag2653/public-claude-code-plugins](https://github.com/chirag2653/public-claude-code-plugins), [Lizo-RoadTown/claude-skills-marketplace](https://github.com/Lizo-RoadTown/claude-skills-marketplace), [juftin/skills](https://github.com/juftin/skills).

Meanwhile, [openai/codex](https://github.com/openai/codex/issues/27831) has an open feature request (June 12) to support npm package sources in marketplace.json — the Claude Code plugin marketplace format is being adopted as a de facto cross-agent standard.

### 4. Specific High-Value MCPs: bhived for Memory, archex for Tokens, CVE for Security

The most technically actionable Reddit posts this period come from [r/ClaudeWorkflows](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/), showcasing purpose-built MCP-plus-skill combos:

**bhived MCP** (Workflow value: 85/100, Confidence: 0.90, June 16) — solves the "agents repeatedly start from scratch" problem by giving Claude Code agents shared memory and autonomous skill discovery across sessions and subagents. Categories: Quality Control, Context & Memory, Debugging, Skills, MCP, Multi-Agent.

**[archex MCP](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/)** (Workflow value: 85/100, Confidence: 0.95, June 15) — solves token-hungry code context retrieval by pairing an MCP server with a skill for intelligent, selective context loading. Categories: Token Saving, Context & Memory, Debugging.

**CVE MCP Server** (per [@techlatest.bsky.social](https://bsky.app/profile/techlatest.bsky.social/post/3mnafczcoi224)) — gives Claude access to 27 security tools across 21 data sources through MCP, letting security teams triage vulnerabilities without switching between NVD, EPSS, CISA KEV, and GitHub.

**42Crunch DevSecOps plugin** (per [@brunopedro.com on Bluesky](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z)) — enterprise-targeted, unlocking "an autonomous, end-to-end Agentic DevSecOps model."

Of 16,400+ surveyed MCP implementations ([NiteAgent](https://niteagent.com/blog/2026-06-11-custom-mcp-server-guide/)), 55% are JavaScript-based and 38% Python-based.

### 5. The Overhead Backlash — MCP Token Cost as a Design Critique

The period's most-engaged community voice isn't enthusiastic — [@regent0x_](https://x.com/regent0x_/status/2059559047888507213) went viral (118 likes, 21 reposts) with a meditation on complexity: "$50 raspberry pi running AI in the palm of his hand / no plugins, no MCP servers, no 62,000 tokens of overhead / just ollama and a terminal / this guy saw that video and deleted everything from his $4,000 macbook." The follow-up (49 likes) pressed the generational point: "his dad built a $2M company on a 1986 macintosh plus / no drivers, no plugins, no setup - just worked / 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free."

This isn't anti-MCP sentiment so much as a design-cost signal: practitioners weigh token overhead against capability gains. The practitioner consensus (per [Clarista](https://www.clarista.io/blog/claude-code-mcp-plugins-guide)) is "limit active servers to around 5-6, since each one starts a subprocess. More than that and things can feel sluggish."

### 6. Security: The Risk Has Moved to the Control Plane

[@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) (June 19, 6 replies) identified a shift that's gaining traction: "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?' Developers are adding MCP servers, skills, hooks, plugins, local monitors, marketplace packages, browser access, shell access, and project-specific permissions." A year ago AI coding risk meant hallucinated code. The new risk surface is what's in the plugin stack.

The [Perplexity Bumblebee scanner](https://x.com/alex_prompter/status/2059548217285713933) (95 likes, 19 reposts) emerged specifically for this: "It scans your machine for compromised packages, malicious browser extensions, infected editor extensions (VS Code, Cursor, Windsurf), and MCP server configs." Timed against the May 11 attack that injected malicious code into 160+ software packages. Agensi's security-reviewed paid skill marketplace is targeting this gap with an 8-point pre-publication checklist.

### 7. Cross-Client Standardization — Skills as a Multi-Agent Primitive

A quiet architectural shift: the agent skills format is becoming cross-client. [@0xluffy_eth](https://x.com/0xluffy_eth/status/2057719369137037793) (144 likes, 53 reposts) and [@ChrisSlacker](https://x.com/ChrisSlacker/status/2057655698688029139) (40 likes) both circulated lists of 20 GitHub repos covering the Claude ecosystem — lists that include cross-client tools like SuperClaude Framework alongside Claude-specific ones. [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) explicitly covers Claude Code, Cursor, Codex CLI, Gemini CLI, and more in one repo. [Skills.sh](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) installs to "Claude Code, Codex CLI, Cursor, and OpenClaw" via the same one-command CLI. [openclaw/openclaw issue #85674](https://github.com/openclaw/openclaw/issues/85674) requests conditional skill loading via `paths:` frontmatter specifically matching the Claude Code skill discovery pattern.

The [PostHog/posthog PR](https://github.com/PostHog/posthog/pull/64385) (June 17) shows a major product company building internal skill infrastructure: "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams."

Anthropic also published [anthropics/knowledge-work-plugins](https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mmlwuhsu732c) (GitHub trending, May 24) — "Plugins that make Claude a specialist for specific roles or companies," covering Claude Cowork and Claude Code with role-specific skills and connectors.

### 8. Community Creativity — From VST Plugins to Domain-Specific Extensions

Claude Code's plugin authoring capability is attracting novel use cases beyond enterprise DevOps. [@viriditax.bsky.social](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227) used Claude Code to build VST audio plugins ("a bass octaver combined with an autopan"). [@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) built ChimeraX molecular visualization plugins: "Claude Code is pretty good at writing ChimeraX plugins! Most likely older plugins could be ported over that way relatively easily." [@toyinariyo.bsky.social](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) surfaced Godot AI plugins compatible with both Claude Code and Codex.

[@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes) offered the most quotable community take on the plugin experience: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." The follow-up (11 likes): "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful."

---

## Cross-Source Patterns

**Pattern 1: Skills-and-MCP as complementary layers, not alternatives** — Appeared on Reddit (r/ClaudeWorkflows), X ([@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368), @pauliusztin_), Web (Clarista, AgentWay, hidekazu-konishi.com). Consistent framing: MCP for external system connectivity, skills for repeatable procedural knowledge. "Write MCP once, many clients use it; write skills to orchestrate what those MCP servers expose."

**Pattern 2: Marketplace proliferation raising discovery/trust problems** — Appeared on X (@stretchcloud security concern), Web (Agensi's 8-point security checklist, buildtolaunch.substack 11-tested-4-kept review). The ecosystem grew fast; quality and security signal are lagging. Security-reviewed and practitioner-tested tiers are emerging to address this.

**Pattern 3: Cross-client standardization of the agentskills format** — Appeared on X (@0xluffy_eth, @ChrisSlacker), GitHub (openclaw/openclaw issue, openai/codex feature request), Web (Skills.sh, sickn33/antigravity-awesome-skills, juftin/skills). Skills are becoming an interoperability format, not a Claude-only primitive.

**Pattern 4: Token overhead as a real design constraint** — Appeared on X (@regent0x_ 118+49 likes), Web (Clarista "limit to 5-6 servers"), Reddit (bhived+archex MCPs explicitly framed as token-saving solutions). Token cost of MCP is shaping architectural choices at the individual developer level.

**Pattern 5: Anthropic shipping fast on the extension surface** — Appeared on X (@claudeai Artifacts, @ClaudeCodeLog /reload-skills + pluginSuggestionMarketplaces), Web (Anthropic engineering blog on MCP code execution, knowledge-work-plugins GitHub trending). Anthropic is actively building out the distribution and admin infrastructure around skills and plugins, not just the runtime.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP | — | — | "Agents repeatedly start from scratch" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/) |
| r/ClaudeWorkflows | Improve Claude Code Agent Token Efficiency with archex MCP Server and Skill | — | — | "Token-hungry code context retrieval" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/) |
| r/ClaudeWorkflows | Practical Guide to Claude Code Components: CLAUDE.md, Skills, Hooks, Plugins, and AGENTS.md Hierarchy | — | — | — | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1tmvvqk/workflow_practical_guide_to_claude_code/) |
| r/artificial | Claude Fable made me realize I don't need a better model | — | — | — | [link](https://www.reddit.com/r/artificial/comments/1u3acx4/claude_fable_made_me_realize_i_dont_need_a_better/) |
| r/artificial | Mystery company accidentally blew $500 million on Claude AI in a single month | — | — | — | [link](https://www.reddit.com/r/artificial/comments/1trmvgh/mystery_company_accidentally_blew_500_million_on/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | New in Claude Code: Artifacts. Interactive pages built from your session... | 17,774 | 1,274 | [link](https://x.com/claudeai/status/2067671912038240487) |
| @claudeai | As your session keeps working, the artifact refreshes... | 570 | 14 | [link](https://x.com/claudeai/status/2067671913418063892) |
| @claudeai | Artifacts draw on the full context of your session: codebase, plugins, skills, connected tools | 544 | 28 | [link](https://x.com/claudeai/status/2067671914533863585) |
| @regent0x_ | $50 raspberry pi... no plugins, no MCP servers, no 62,000 tokens of overhead | 118 | 21 | [link](https://x.com/regent0x_/status/2059559047888507213) |
| @alex_prompter | Perplexity just open-sourced their internal security scanner [Bumblebee for MCP configs] | 95 | 19 | [link](https://x.com/alex_prompter/status/2059548217285713933) |
| @pauliusztin_ | MCP co-creator: "Connectivity is not one thing. Best agents use all of it - skills, CLI, MCP - together." | 52 | 7 | [link](https://x.com/pauliusztin_/status/2063236967987298550) |
| @JackWoth98 | 30 days of using Antigravity CLI… | 423 | 53 | [link](https://x.com/JackWoth98/status/2065529819685871690) |
| @0xluffy_eth | 20 GitHub repos for Claude [ecosystem list incl. Awesome MCP Servers, SuperClaude Framework] | 144 | 53 | [link](https://x.com/0xluffy_eth/status/2057719369137037793) |
| @ChrisSlacker | 20个Claude GitHub仓库 [same list, Chinese] | 40 | 14 | [link](https://x.com/ChrisSlacker/status/2057655698688029139) |
| @Crypto_QianXun | 想系统学习 Claude [20 GitHub repos for Claude learning] | 37 | 12 | [link](https://x.com/Crypto_QianXun/status/2065225329573327356) |
| @ClaudeCodeLog | Claude Code 2.1.152 changelog: /reload-skills + pluginSuggestionMarketplaces | 28 | — | [link](https://x.com/ClaudeCodeLog/status/2059451400338223550) |
| @AndrewK404 | Skill vs plugin distinction explained | 2 | 1 | [link](https://x.com/AndrewK404/status/2059732591222096368) |
| @stretchcloud | Risk has moved from "what did the model say?" to "what is installed on the developer workstation?" | 2 | — | [link](https://x.com/stretchcloud/status/2068096486479462549) |
| @regent0x_ | His dad built a $2M company on a 1986 Mac Plus, no plugins, no setup | 49 | 2 | [link](https://x.com/regent0x_/status/2058079320405332047) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods" | 35 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) |
| @coolhand.bsky.social | I built plugins anyway for Claude and OpenClaw and the rest | 12 | [link](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) |
| @jefferyharrell.bsky.social | I can port Alpha from Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | [link](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) |
| @viriditax.bsky.social | Newer Claude Code — making VST plugins was the first thing I tried | 9 | [link](https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227) |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! | 6 | [link](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) |
| @webuyhousesusa.bsky.social | ECC drops 63 specialized agents and 240+ ready-made skills into Claude Code, Cursor, and Codex | 4 | [link](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) |
| @brunopedro.com | 42Crunch announced Claude Code plugins for autonomous Agentic DevSecOps | 1 | [link](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) |
| @github-trending-js.bsky.social | anthropics/knowledge-work-plugins trending — specialist plugins for roles/companies | 1 | [link](https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mmlwuhsu732c) |
| @toyinariyo.bsky.social | Godot AI plugins usable with Claude Code and Codex | 2 | [link](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) |
| @techlatest.bsky.social | CVE MCP Server gives Claude access to 27 security tools across 21 data sources | 3 | [link](https://bsky.app/profile/techlatest.bsky.social/post/3mnafczcoi224) |

**GitHub:**
| Repo | Title | Reactions | Comments | Notable Quote | URL |
|------|-------|-----------|----------|--------------|-----|
| anthropics/claude-code | [FEATURE] Official Claude Desktop build for Linux | 602 | 43 | — | [link](https://github.com/anthropics/claude-code/issues/65697) |
| anthropics/claude-code | [BUG] Claude Desktop: extension install fully broken | 8 | 7 | — | [link](https://github.com/anthropics/claude-code/issues/68002) |
| anthropics/claude-code | [FEATURE] Support user-level .agents/skills/ discovery | — | — | "cross-agent single-source-of-truth workflows" | [link](https://github.com/anthropics/claude-code/issues/66352) |
| PostHog/posthog | feat(skills): Claude Code & Codex plugin marketplace + zip export | — | 7 | "Skills are the core of agent performance" | [link](https://github.com/PostHog/posthog/pull/64385) |
| openai/codex | Support npm package sources in marketplace.json | — | — | "Claude Code marketplace format that .agents/plugins/marketplace.json mirrors" | [link](https://github.com/openai/codex/issues/27831) |
| openclaw/openclaw | Skills: support conditional loading via paths: frontmatter | — | — | "skills discovered at startup but only injected when a matching file is touched" | [link](https://github.com/openclaw/openclaw/issues/85674) |
| KooshaPari/PhenoMCPServers | feat: forge3-bridge MCP server + skill (catalog 1.4.0) | 4 | 5 | — | [link](https://github.com/KooshaPari/PhenoMCPServers/pull/30) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| hidekazu-konishi.com | [Extension Layer Decision Guide](https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html) | Definitive decision tree for Skills vs Subagents vs Hooks vs Plugins |
| hidekazu-konishi.com | [Skills Complete Guide](https://hidekazu-konishi.com/entry/claude_code_skills_complete_guide.html) | Deep dive on skill creation, testing, and distribution |
| tygartmedia.com | [Skills vs MCP vs Connectors vs Plugins](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) | June 13 explainer; "simplest way to keep these straight" |
| claude.com | [Steering Claude Code blog](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) | Official June 18 overview of 7 customization methods |
| agentway.dev | [Skills reference](https://agentway.dev/en/claudecode/skills) | "Modular capability packages — loaded only when task matches description" |
| dev.to | [Skills System internals](https://dev.to/arihantdeva/how-claude-codes-skills-system-actually-works-3d81) | Engineering explanation of discoverable-asset mechanism |
| dev.to | [Skill/MCP/Plugin decision flow](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) | "lightest first" practitioner heuristic |
| ai-trove.com | [What are Claude Code plugins](https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins) | Security researcher perspective on plugin architecture |
| claudemarketplaces.com | [Directory](https://claudemarketplaces.com/) | 21,600+ skills, 12,500+ MCP servers, 300K+ monthly devs |
| agensi.io | [Marketplace guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Marketplace grew 1→8 registries Dec 2025 → Q2 2026 |
| agensi.io | [All AI Agent Skills Marketplaces](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Security-reviewed paid skills with 8-point checklist |
| clarista.io | [MCP Plugins Complete Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Five-layer stack architecture; limit to 5-6 MCP servers |
| niteagent.com | [Custom MCP Servers guide](https://niteagent.com/blog/2026-06-11-custom-mcp-server-guide/) | 16,400+ MCP implementations analyzed: 55% JS, 38% Python |
| anthropic.com | [Code execution with MCP](https://www.anthropic.com/engineering/code-execution-with-mcp) | Official engineering blog on MCP execution patterns |
| buildtolaunch.substack.com | [Best Claude Code Plugins](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) | "11 Tested, 4 Worth Keeping" — independent practitioner review |
| dev.to | [I Tried 100 Claude Skills](https://dev.to/suraj_khaitan_f893c243958/i-tried-100-claude-skills-these-are-the-best-1m4a) | Practitioner review of community skill quality |
| support.claude.com | [Use plugins in Claude](https://support.claude.com/en/articles/13837440-use-plugins-in-claude) | Official help documentation |
| skills.2389.ai | [2389 Research Marketplace](https://skills.2389.ai/) | Open-source plugins installable via npx skills or /plugin marketplace add |
| github.com | [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2,810 skills, 200 agents |
| github.com | [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) | 1,600+ cross-client skills |
| github.com | [neovateai/agent-skill-npm-boilerplate](https://github.com/neovateai/agent-skill-npm-boilerplate) | npm-publish template for skills |
| github.com | [swissmarley/SkillsForAgents](https://github.com/swissmarley/SkillsForAgents) | Distributable marketplace compatible with Claude Code, Codex, OpenCode, Hermes |
| github.com | [Kamalnrf/claude-plugins](https://github.com/Kamalnrf/claude-plugins) | Lightweight registry for discovering and managing all public Claude plugins |
| chris-ayers.com | [Agent Skills, Plugins and Marketplace](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Complete architectural guide |
| claude-plugins.dev | [Skills discovery](https://claude-plugins.dev/skills) | Cross-client skill discovery built on agentskills spec |
| okhlopkov.com | [My Claude Code Setup](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | Practitioner setup guide — MCP, hooks, skills, agents in one personal stack |
| techsy.io | [Build an MCP Server](https://techsy.io/en/blog/how-to-build-an-mcp-server) | Step-by-step Python & TypeScript MCP server tutorial |
| hidekazu-konishi.com | [Plugins Complete Guide](https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html) | Bundling skills, hooks, agents, MCP servers for team distribution |

---

## Stats Block

```
├─ 🟠 Reddit: 7 threads
├─ 🔵 X: 23 posts │ 20,401 likes │ 1,508 reposts
├─ 🦋 Bluesky: 12 posts │ 86 likes │ 6 reposts
├─ 🐙 GitHub: 15 items │ 660 reactions │ 163 comments
├─ 🌐 Web: 31 pages (engine 18 + supplements 13)
└─ 🗣️ Top voices: @claudeai, @regent0x_, @ClaudeCodeLog │ r/ClaudeWorkflows, r/artificial
```

---

## Data Gaps

- **YouTube: 0 videos** — ScrapeCreators returned HTTP 402 (payment required) across all attempts; YouTube search via yt-dlp also returned 0 results for these queries. Tutorial and walkthrough content for Claude Code skills/MCP likely exists but was not captured this run.
- **TikTok: 0 videos** — ScrapeCreators HTTP 402 on all hashtag and keyword attempts (#claudecode, #mcpserver, #aiagent). Short-form demo content uncaptured.
- **Instagram: 0 reels** — ScrapeCreators HTTP 402. Likely sparse on this topic regardless.
- **Hacker News: 0 stories** — HN Algolia search returned HTTP 400 (Bad Request) for all four queries; a known HN API edge case with long compound queries. HN discussion on this topic exists (one HN thread linked via Bluesky: "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs") but comment-level data was not retrieved.
- **Reddit: sparse (7 threads)** — Reddit public API returned 403 Forbidden; ScrapeCreators backup also HTTP 402. Reddit coverage relies on RSS which yielded limited signal. Community discussion on r/ClaudeAI and r/LocalLLaMA almost certainly exists but was not fully captured.
- **Polymarket: 0 markets** — No prediction markets on this topic, expected given its technical niche.
- **Coverage estimate:** ~55-65% of available signal captured. X, Web, GitHub, and Bluesky are well-covered. Reddit, YouTube, TikTok, and HN are gaps. The Reddit gap is the most significant given r/ClaudeAI's size and activity level on this topic.

---

## Key Quotes

> "New in Claude Code: Artifacts. Interactive pages built from your session, like a PR walkthrough or a living project dashboard, shared with your team at a private link." — [@claudeai](https://x.com/claudeai/status/2067671912038240487) on X (17,774 likes)

> "$50 raspberry pi running AI in the palm of his hand / no plugins, no MCP servers, no 62,000 tokens of overhead / just ollama and a terminal" — [@regent0x_](https://x.com/regent0x_/status/2059559047888507213) on X (118 likes)

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky (35 likes)

> "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." — [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368) on X

> "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?'" — [@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) on X

> "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together." — David Soria Parra (@AnthropicAI, MCP co-creator), cited by [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550)

> "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams." — [PostHog/posthog PR #64385](https://github.com/PostHog/posthog/pull/64385)

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky (11 likes)

> "Claude Code is pretty good at writing ChimeraX plugins! Most likely older plugins could be ported over that way relatively easily." — [@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) on Bluesky

> "His dad built a $2M company on a 1986 macintosh plus / no drivers, no plugins, no setup - just worked / 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free" — [@regent0x_](https://x.com/regent0x_/status/2058079320405332047) on X (49 likes)
