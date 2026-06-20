# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-20
**Query type:** GENERAL
**Sources:** X/Twitter, GitHub, Web, Bluesky, Reddit

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 2 threads | — | r/ClaudeAI only; public API 403'd, keyless fallback |
| X/Twitter | 27 posts | 3,100 likes, 255 reposts | @ClaudeCodeLog, @AnthropicAI, @btsouth top voices |
| YouTube | 0 videos | — | SC 402 errors; yt-dlp returned 0 on this query |
| Hacker News | 0 stories | — | HN search 400'd on all 4 subqueries |
| TikTok | 0 videos | — | SC 402 errors across all hashtags |
| Instagram | 0 reels | — | SC 402 errors |
| Bluesky | 12 posts | 86 likes, 6 reposts | jefferyharrell, uermel, toyinariyo top voices |
| Polymarket | 0 markets | — | No prediction markets on this topic |
| GitHub | 22 items | 197 reactions, 460 comments | anthropics/claude-code, vercel-labs/open-plugin-spec |
| Web | 15 pages + 13 supplements | — | mcsaguru.com, niteagent.com, blog.modelcontextprotocol.io |

---

## Synthesized Findings

### 1. The Three-Layer Ecosystem Is Finally Clicking — and Developers Are Confused About Which Layer to Use

The dominant conversation in the last 30 days is the community working out the distinctions between Claude Code skills, MCP servers, and plugins — and where to put their workflows. The clearest summary comes from [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) (June 10, 2026): "People treat plugins, skills, and MCP servers as three options on the same menu, then get confused when the comparison doesn't quite work." The actual relationship is a nesting hierarchy: skills are markdown instruction files (what Claude *knows how to do*), MCP servers are the protocol integration layer (external APIs and data sources via JSON-RPC), and plugins are versioned bundles that can contain all of the above, plus hooks, slash commands, and subagents. [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) (June 13, 2026) frames it as: "Skills teach Claude how to do a thing. MCP connects Claude to a thing. Plugins ship both to your team in one install."

[blog.laozhang.ai](https://blog.laozhang.ai/en/posts/claude-code-hooks-slash-commands-skills) (June 1) separates the three workflow surfaces by *who triggers the action*: slash commands (human triggers a session), skills (Claude loads reference material when it detects relevance), hooks (lifecycle events fire scripts automatically). Discussed across X, Web, and Bluesky.

### 2. "Claude Code Out of the Box Is Bare" — The Marketplace Ecosystem Has Arrived

[r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) and X both show developers treating the plugin marketplace as the real starting point for Claude Code setup. [@Marvomaticc](https://x.com/Marvomaticc/status/2068275546237116575) put the framing bluntly on June 20: "Claude Code out of the box is bare. One install loads 67 agents, 271 skills, 92 commands and 10 MCP servers — a whole engineering team. Open source, 217k stars." The reference is to community plugin repos that have reached scale.

The official Claude marketplace at claude.com/plugins (public beta, announced via [@claudeai](https://x.com/claudeai/status/1976332881409737124)) shows adoption at scale: top installs as of early June 2026 include Frontend Design (829,316 installs), Superpowers (752,120 installs), and Context7 (348,660 installs) per [composio.dev](https://composio.dev/content/top-claude-code-plugins). Third-party marketplaces are proliferating in parallel: [tonsofskills.com](https://tonsofskills.com/docs/) has 425 plugins, 2,810 skills, and 200 agents with a `ccpi` CLI package manager; [claudemarketplaces.com](https://claudemarketplaces.com/) claims 300K+ monthly developers; [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) has the same catalog at 425 plugins on GitHub. [@NainsiDwiv50980](https://x.com/NainsiDwiv50980/status/2067996681187242419) (June 19) summarized the ecosystem shift: "The difference between devs who ship 10x faster and everyone else isn't talent — it's the ecosystem they build around their agent. Skills. MCP servers. Agent harnesses."

### 3. MCP Fragmentation Is the Biggest Pain Point — Conduit Is the Emerging Fix

The loudest frustration in the X conversation is MCP configuration sprawl across clients. [@btsouth](https://x.com/btsouth/status/2068119732482453822) (June 19) described the problem in a thread that spawned multiple replies: "The mess today: every client (Claude, Cursor, VS Code…) wants its own MCP config. You set up the same servers over and over, re-auth in each, paste API keys in plaintext, and bury every agent under hundreds of tool definitions." The same thread mentions [@JacobCounsell](https://x.com/btsouth/status/2068092518848237806) building Conduit — "a desktop app that wrangles MCP servers across all your AI tools (Claude, Cursor, VS Code) into one local gateway. Keys stay in your OS keychain. No Docker, no cloud." [@btsouth](https://x.com/btsouth/status/2068230310232306110) confirmed the open-source release is imminent.

The MCP portability observation is reinforced by [@49agents](https://x.com/49agents/status/2068170827007176717): "MCP servers work with any tool that implements the protocol, not just Claude Code. the question is who actually built servers for the tools you use. most have basic ones but the depth varies." A cross-client skill portability repo, [juftin/skills](https://github.com/juftin/skills), explicitly targets Claude Code, Codex CLI, Gemini CLI, and "any tool" with a compatible manifest.

[@Marvomaticc](https://x.com/Marvomaticc/status/2068229249446691188) (June 20) laid out the starter MCP stack: "The first 3 MCP servers for Claude Code: GitHub (where your code lives), Context7 (docs stay current), Playwright (verifies the build). That's the starter stack."

### 4. The Token Waste Problem in Skills-Heavy Setups Is Getting Developer Attention

A r/ClaudeAI post from June 12 surfaced a concrete, reproducible problem: "[Using Claude Code? You're probably wasting ~8k tokens per session on unused skills.](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) I built a CLI to fix it." The OP analyzed session transcripts and found 187 items loaded at initiation (skill descriptions, MCP server configs, custom rules), of which only 4 were actively used — burning ~8,000 tokens per session. According to [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide), Anthropic's mitigation is MCP tool deferral: "MCP tools are deferred rather than loaded into context upfront, and Claude uses a search tool to discover relevant ones when a task needs them. Only the tools Claude actually uses enter context." But the skills layer does not yet benefit from the same deferred loading, and Claude Code CLI 2.1.152 (released May 27) added `/reload-skills` to help — visible in the [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2059451400338223550) changelog: "Added /reload-skills command to re-scan skill directories without restarting the session."

### 5. The "Agent Is the Harness, Not the Markdown File" Philosophical Debate

A thread from [@ArcherNightfall](https://x.com/ArcherNightfall/status/2068110341498622189) (June 19, 6 likes) sparked the most conceptually interesting X debate of the window: "The current 'agent file' and 'skill file' abstraction is useful, but it is also misleading. An AGENTS.md, CLAUDE.md, or SKILL.md file does not make an LLM into an agent. It gives the model instructions. That is all. The real agent is not the markdown file. The real agent is the harness." The post went on: "The harness is the behavior engine. It is the actual application layer that decides what happens, when it happens, which tools get called, which MCP servers are [invoked]." This tension — between treating skills/plugins as first-class AI capabilities versus recognizing them as prompt engineering — is emerging as the ecosystem matures.

The Claude official blog addressed a related angle: [claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) (June 2, 2026) — "Claude Code can now write and orchestrate its own multi-agent harness on the fly." The framing there treats the harness as *something Claude writes*, not something the developer pre-defines — a meaningful shift from SKILL.md-centric thinking.

### 6. Cross-Agent Skill Distribution and Vendor-Neutral Specs Are Emerging

Multiple signals point to the ecosystem moving toward cross-vendor skill portability. The [vercel-labs/open-plugin-spec](https://github.com/vercel-labs/open-plugin-spec/issues/5) GitHub issue proposes treating `.plugin/plugin.json` as a vendor-neutral single manifest across Claude Code and Cursor (instead of both `.claude-plugin/` and `.cursor-plugin/`): "the convergence of `.claude-plugin/` and `.cursor-plugin/` into a vendor-neutral `.plugin/plugin.json` feels like exactly the right structural move." [swissmarley/SkillsForAgents](https://github.com/swissmarley/SkillsForAgents) targets Claude Code, Codex CLI, OpenCode, and Hermes with a one-line installer. A Bluesky post from [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) promotes ECC: "63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together."

A r/ClaudeAI team built [gaal](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) to sync CLAUDE.md, slash commands, MCP servers, and skills across machines and across agent CLIs (Claude Code wants CLAUDE.md, Codex wants AGENTS.md, Cursor wants .cursorrules — same project, incompatible formats).

### 7. The MCP Specification Is About to Get a Major Overhaul

[blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) published the Release Candidate for the 2026-07-28 MCP spec — described as "the largest revision of the protocol since launch." Key changes: a stateless HTTP core (replacing the stateful sessions), MCP Apps (server-rendered UIs for richer tool interactions), a Tasks extension for long-running async work, and authorization more closely aligned with OAuth and OpenID Connect. [truefoundry.com](https://www.truefoundry.com/blog/claude-mcp-registry) covers the enterprise registry layer: approved server configuration, audit controls, cost governance on top of the public discovery layer.

An analysis of 16,400+ MCP implementations from [niteagent.com](https://niteagent.com/blog/2026-06-11-custom-mcp-server-guide/) finds 55% JavaScript-based and 38% Python-based — the ecosystem language split.

### 8. Security Concerns Around the Plugin/MCP Surface Are Surfacing

[@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) (June 19) voiced a concern that resonated in replies: "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?' Developers are adding MCP servers, skills, hooks, plugins, local monitors, marketplace packages, browser access, shell access, and project-specific permissions across multiple tools. The control plane is now much bigger." Docker's CISO was addressing the same governance gap at LeadDev London per [@Docker](https://x.com/Docker/status/2068001022367215934): "Agents are helping generate more code than ever. So why aren't organizations shipping proportionally faster? [It's] the trust gap behind agent adoption." A 42Crunch announcement (via [brunopedro.com on Bluesky](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z)) highlights enterprise-specific Claude Code plugin integrations for "autonomous, end-to-end Agentic DevSecOps."

### 9. Claude Code CLI 2.1.183 — Latest Release Details

[@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2067782778700091715) (June 19, 352 likes) published the 2.1.183 changelog. Key plugin/skills-relevant changes: auto mode now blocks destructive git commands by default; `attribution.sessionUrl` setting added to omit claude.ai session links from commits and PRs; model deprecation warnings now cover models set in agent frontmatter; and previous CLI 2.1.152 added a `pluginSuggestionMarketplaces` managed setting (admins can allowlist org-specific marketplaces for context-aware plugin tips).

---

## Cross-Source Patterns

**Pattern 1: Skills/MCP/Plugins as a stack, not alternatives** - Appearing on X (multiple posts), Web (mcsaguru.com, tygartmedia.com, laozhang.ai), and Reddit. The community has moved past "which one should I use" toward "use all three at the right layer." Most-cited framing: skills = knowledge layer, MCP = integration layer, plugins = distribution layer.

**Pattern 2: MCP config sprawl pain** - Appearing on X (@btsouth thread, @49agents) and Web (clarista.io). The "set up the same server in every client" problem is the top friction point for power users, and Conduit is the most-watched solution. Key quote: "every client (Claude, Cursor, VS Code…) wants its own MCP config. You set up the same servers over and over, re-auth in each, paste API keys in plaintext." — [@btsouth](https://x.com/btsouth/status/2068119732482453822)

**Pattern 3: Token budget pressure from over-loaded skills** - Appearing on Reddit (r/ClaudeAI post on 8k token waste) and Web (clarista.io on deferred MCP loading as mitigation). Active skill directories are creating measurable per-session overhead, and developers are building tooling to manage it.

**Pattern 4: Cross-agent portability drive** - Appearing on X (@NainsiDwiv50980's ecosystem list), GitHub (vercel-labs/open-plugin-spec, juftin/skills, swissmarley/SkillsForAgents), and Bluesky. The ecosystem is converging on cross-agent compatibility as a table-stakes requirement for any skill marketplace.

**Pattern 5: Security/governance gap** - Appearing on X (@stretchcloud, @Docker) and Bluesky (42Crunch announcement). The expansion of the MCP/plugin control plane is outpacing security governance tooling. Docker CISO visibility suggests enterprise concern is escalating.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | — | — | "same project means different rules filename per agent. Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules" | https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/ |
| r/ClaudeAI | Using Claude Code? You're probably wasting ~8k tokens per session on unused skills. I built a CLI to fix it. | — | — | "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight" | https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @ClaudeCodeLog | Claude Code 2.1.183 — auto mode blocks destructive git commands, attribution.sessionUrl setting added | 352 | 9 | https://x.com/ClaudeCodeLog/status/2067782778700091715 |
| @AnthropicAI | Project Fetch Phase 2: Opus 4.7 was ~20x faster than last year's best human team aided by Opus 4.1 | 2,070 | 167 | https://x.com/AnthropicAI/status/2067651699486200091 |
| @AnthropicAI | Anthropic Economic Index — tracking consequential shifts in the nature of work | 263 | 24 | https://x.com/AnthropicAI/status/2066969542010806561 |
| @snskritinaruka | 2026 checklist: Vibe code with Codex + Claude Code, deploy Hermes & Agent Swarms, run local models & MCP servers | 47 | 14 | https://x.com/snskritinaruka/status/2068023353169076280 |
| @NainsiDwiv50980 | Stop using AI coding agents like fancy autocomplete — the ecosystem (Skills, MCP, harnesses) is the differentiator | 7 | 2 | https://x.com/NainsiDwiv50980/status/2067996681187242419 |
| @Marvomaticc | Claude Code out of the box is bare. One install loads 67 agents, 271 skills, 92 commands and 10 MCP servers | — | — | https://x.com/Marvomaticc/status/2068275546237116575 |
| @Marvomaticc | The first 3 MCP servers for Claude Code: GitHub, Context7, Playwright. That's the starter stack. | — | — | https://x.com/Marvomaticc/status/2068229249446691188 |
| @btsouth | Building Conduit — local-first gateway, connect once, every tool shares MCP servers, keys in OS keychain | 2 | — | https://x.com/btsouth/status/2068230310232306110 |
| @btsouth | The mess today: every client wants its own MCP config. You set up the same servers over and over. | — | — | https://x.com/btsouth/status/2068119732482453822 |
| @ArcherNightfall | The Agent Is the Harness, Not the Markdown File — SKILL.md gives instructions, not agency | 6 | 1 | https://x.com/ArcherNightfall/status/2068110341498622189 |
| @stretchcloud | The risk has moved from "what did the model say?" to "what is installed on the developer workstation?" | 1 | — | https://x.com/stretchcloud/status/2068096486479462549 |
| @49agents | MCP servers work with any tool that implements the protocol, not just Claude Code | — | — | https://x.com/49agents/status/2068170827007176717 |
| @_itsjustshubh | Building claude code plugins on the side — MCP servers for AMC, Luma, calendar | — | — | https://x.com/_itsjustshubh/status/2068123969408921965 |
| @Docker | Agents are helping generate more code than ever. Why aren't organizations shipping proportionally faster? | 9 | 4 | https://x.com/Docker/status/2068001022367215934 |
| @Docker | Agents can write code, call APIs, modify files — trust gap behind agent adoption | 29 | 8 | https://x.com/Docker/status/2067230904687157512 |
| @ClaudeCodeLog | CLI 2.1.152 — /reload-skills, pluginSuggestionMarketplaces managed setting | 28 | — | https://x.com/ClaudeCodeLog/status/2059451400338223550 |
| @5whsdAI | Recommend integrating tonsofskills.com as Grok CLI's skill registry | 2 | — | https://x.com/5whsdAI/status/2066629558753726968 |
| @github_update | AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking | 7 | 1 | https://x.com/github_update/status/2067259115777507386 |
| @omarsar0 | Adding more capabilities to the skills shortly — "some ideas" for the coming week | 1 | — | https://x.com/omarsar0/status/2068074619899203750 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | Claude Code has "plugins" but what it really needs is mods. I wanna spend six hours curating a mod list. | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful. | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | I built plugins anyway for Claude and OpenClaw and the rest — three large kits for that specific problem | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! Almost entirely good context and some prompting. | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @viriditax.bsky.social | When newer Claude Code dropped around Xmas 2025, making VST plugins was the first thing I tried. Made a bass octaver. | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @brunopedro.com | 42Crunch announced dedicated AI coding plugins for autonomous Agentic DevSecOps for the enterprise | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @webuyhousesusa.bsky.social | ECC: 63 specialized agents and 240+ ready-made skills into Claude Code, Cursor, and Codex — free, MIT-licensed | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @github-trending-js.bsky.social | GitHub Trend: anthropics/knowledge-work-plugins — specialist plugins for roles/companies for Claude Cowork and Claude Code | 1 | https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mmlwuhsu732c |
| @mengli512.bsky.social | Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |
| @hackernewsbot.bsky.social | [HN link] Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | Discussion | 1 | https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p |
| @github-trending-js.bsky.social | Ruflo: multi-agent orchestration extending Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @toyinariyo.bsky.social | Many Godot AI plugins can be used with Claude Code and Codex | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |

**GitHub:**
| Repo | Title | Reactions | Comments | Notable | URL |
|------|-------|-----------|----------|---------|-----|
| anthropics/claude-code | [BUG] Tool-call results empty in live UI then flush late/out-of-order (Bash, Read, MCP, advisor) | 9 | 7 | Active MCP rendering bug on macOS, Opus 4.8 | https://github.com/anthropics/claude-code/issues/63966 |
| vercel-labs/open-plugin-spec | Proposal: treat skill-only packages as plugins — .plugin/plugin.json as single source of truth | — | 7 | Cross-vendor neutral manifest proposal | https://github.com/vercel-labs/open-plugin-spec/issues/5 |
| shakacode/react_on_rails | chore(claude): add autoreview second-model code-review skill | — | 9 | Real-world SKILL.md adoption in prod repo | https://github.com/shakacode/react_on_rails/pull/3496 |
| abapify/openadt | feat(mcp): SAP ADT launcher with headless logon support | — | 6 | Enterprise MCP server for SAP integration via Claude | https://github.com/abapify/openadt/pull/42 |
| RemyLoveLogicAI/agentic-os | Add holaOS persistent agent infrastructure with three viral skill builds | — | 11 | Trend Arbitrage Agent, Social Content Engine, Micro-SaaS Factory as skills | https://github.com/RemyLoveLogicAI/agentic-os/pull/41 |
| openclaw/openclaw | TUI Competitive Analysis: 15 Gaps to Close vs Claude Code, Aider, Codex CLI, Kimi CLI, Goose | — | 3 | Competitor positions Claude Code as benchmark | https://github.com/openclaw/openclaw/issues/86534 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| MCSA Guru | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Three-layer hierarchy explained: skills nest inside plugins, MCP is the protocol integration layer |
| Tygart Media | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | June 13, 2026 guide: "Skills teach Claude how to do a thing. MCP connects Claude to a thing." |
| Claude Blog | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Official: Claude Code now writes its own multi-agent harness on the fly |
| LaoZhang AI | https://blog.laozhang.ai/en/posts/claude-code-hooks-slash-commands-skills | Who triggers the action: slash commands (human), skills (Claude), hooks (lifecycle events) |
| AI Trove | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Claude Code plugin spec deep-dive by ML/security veteran Paul Irolla |
| NiteAgent | https://niteagent.com/blog/2026-06-11-custom-mcp-server-guide/ | 16,400+ MCP implementations analyzed: 55% JS, 38% Python |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | Upcoming MCP RC: stateless HTTP core, MCP Apps, Tasks extension, OAuth/OIDC auth |
| TeacherAndTask | https://www.teacherandtask.com/blog/model-context-protocol-mcp-explained | MCP architecture: M×N to M+N integration problem solved |
| ClaudeFolio | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Skills = markdown files that become slash commands; MCP = external services via standard protocol |
| Support.Claude | https://support.claude.com/en/articles/13837440-use-plugins-in-claude | Official plugin help documentation |
| AI Tools Guidebook | https://aitoolsguidebook.com/en/articles/claude-code-skills-guide/ | Complete walkthrough: built-in, custom, plugin, and team-shared skills |
| ClaudeFast | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Plugins: from personal Claude Code setup to org standard; skills, hooks, MCPs in one install |
| TruFoundry | https://www.truefoundry.com/blog/claude-mcp-registry | Enterprise MCP registry vs public registry: access permissions, audit controls, cost governance |
| ClaudeMarketplaces | https://claudemarketplaces.com/ | Community-curated directory of skills, plugins, MCP servers; 300K+ monthly developers |
| TonsOfSkills | https://tonsofskills.com/docs/ | 425 plugins, 2,810 skills, 200 agents; ccpi CLI; marketplace comparison tool |
| Composio | https://composio.dev/content/top-claude-code-plugins | Top install counts from official marketplace (June 2026): Frontend Design 829K, Superpowers 752K, Context7 349K |
| Clarista | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | MCP tool deferral: only tools Claude actually calls enter context; 127+ plugins available |
| ScriptByAI | https://www.scriptbyai.com/claude-code-resource-list/ | Curated 2026 resource list for agents, skills, plugins |
| GitHub (juftin/skills) | https://github.com/juftin/skills | Cross-platform agent skills directory: Claude Code, Codex CLI, Gemini CLI, any compatible tool |
| GitHub (swissmarley/SkillsForAgents) | https://github.com/swissmarley/SkillsForAgents | Distributable skill marketplace for Claude Code, Codex CLI, OpenCode, Hermes; MIT license |
| GitHub (openmodelsrun/mcp) | https://github.com/openmodelsrun/mcp | Open-source MCP server registry with structured metadata and install configs |
| GitHub (jeremylongshore) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; open-source marketplace at tonsofskills.com |
| Vercel Labs (open-plugin-spec) | https://github.com/vercel-labs/open-plugin-spec/issues/5 | Vendor-neutral plugin manifest proposal: .plugin/plugin.json for Claude Code and Cursor |

---

## Stats Block

```
├─ 🟠 Reddit: 2 threads
├─ 🔵 X: 27 posts │ 3,100 likes │ 255 reposts
├─ 🦋 Bluesky: 12 posts │ 86 likes │ 6 reposts
├─ 🐙 GitHub: 22 items │ 197 reactions │ 460 comments
├─ 🌐 Web: 28 pages (15 engine + 13 WebSearch supplements)
└─ 🗣️ Top voices: @btsouth, @ClaudeCodeLog, @AnthropicAI, @Marvomaticc │ r/ClaudeAI
```

---

## Data Gaps

- **HN returned 0**: All 4 HN subqueries returned HTTP 400. Likely a search API issue with the long query string. HN has active Claude Code / MCP threads (one was cross-posted via the Bluesky hackernewsbot) but no direct HN data was captured.
- **Reddit coverage thin**: Public Reddit API returned 403 on all direct calls; ScrapeCreators returned 402. Keyless RSS fallback found only 2 threads in r/ClaudeAI. Real Reddit discussion is likely rich (r/ClaudeAI, r/LocalLLaMA) but was not captured this run.
- **YouTube, TikTok, Instagram: 0**: ScrapeCreators 402 errors across all video sources. The Claude Code skills/MCP YouTube tutorial space (e.g., AI Explained, Prompt Engineering channels) was not captured.
- **Polymarket: 0 markets**: No prediction markets on plugin ecosystem outcomes — expected for a developer tooling topic.
- **Approximate coverage**: ~45% of likely community activity captured. X and Web/GitHub are well-represented; Reddit, HN, and video platforms are the major gaps.

---

## Key Quotes

> "Claude Code out of the box is bare. One install loads 67 agents, 271 skills, 92 commands and 10 MCP servers — a whole engineering team. Open source, 217k stars." — [@Marvomaticc](https://x.com/Marvomaticc/status/2068275546237116575) on X (June 20, 2026)

> "The mess today: every client (Claude, Cursor, VS Code…) wants its own MCP config. You set up the same servers over and over, re-auth in each, paste API keys in plaintext, and bury every agent under hundreds of tool definitions." — [@btsouth](https://x.com/btsouth/status/2068119732482453822) on X (June 19, 2026)

> "The difference between devs who ship 10x faster and everyone else isn't talent — it's the ecosystem they build around their agent. Skills. MCP servers. Agent harnesses." — [@NainsiDwiv50980](https://x.com/NainsiDwiv50980/status/2067996681187242419) on X (June 19, 2026)

> "The real agent is not the markdown file. The real agent is the harness. The harness is the behavior engine. It is the actual application layer that decides what happens, when it happens, which tools get called, which MCP servers are [invoked]." — [@ArcherNightfall](https://x.com/ArcherNightfall/status/2068110341498622189) on X (June 19, 2026)

> "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) (June 12, 2026)

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky (June 4, 2026)

> "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?'" — [@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) on X (June 19, 2026)

> "MCP servers work with any tool that implements the protocol, not just Claude Code. The question is who actually built servers for the tools you use." — [@49agents](https://x.com/49agents/status/2068170827007176717) on X (June 20, 2026)

> "Skills teach Claude how to do a thing. MCP connects Claude to a thing. Plugins ship both to your team in one install." — [Tygart Media](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) (June 13, 2026)

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky (June 4, 2026)
