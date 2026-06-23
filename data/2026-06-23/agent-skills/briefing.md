# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-23
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 6 threads | ~0 upvotes captured, multiple comments | r/ClaudeAI, r/artificial |
| X/Twitter | 20 posts | 19,800 likes, 1,374 reposts, 815 replies | @ClaudeCodeLog dominant voice |
| YouTube | 0 videos | — | Not indexed for this query |
| Hacker News | 19 stories | 74 points, 24 comments | Mostly Show HN submissions |
| TikTok | 0 videos | — | ScrapeCreators 402 (quota) |
| Instagram | 0 reels | — | ScrapeCreators 402 (quota) |
| Bluesky | 12 posts | 230 likes, 25 reposts, 49 replies | Security and agent discussion |
| Polymarket | 0 markets | — | No prediction markets on topic |
| Web | 9 pages + 15 supplemental | — | via engine + WebSearch |
| GitHub | 11 items | 197 reactions, 134 comments | Issues, PRs, repos |

---

## Synthesized Findings

### 1. The Extension Taxonomy War: Skills vs MCP vs Plugins vs Hooks

The single most discussed topic this month is how these four extension primitives differ - and the community is actively writing guides to clarify the confusion. The consensus that has crystallized:

- **Skills** (SKILL.md files) teach Claude how to perform a repeatable task; they load only when invoked.
- **MCP servers** implement the Model Context Protocol - Anthropic's open "USB for AI" standard - and give Claude real-time access to external systems (databases, APIs, services).
- **Plugins** are distributable bundles that can contain skills, hooks, MCP servers, slash commands, and subagent definitions.
- **CLAUDE.md** is persistent project context, always loaded, unlike skills which load on-demand.
- **Hooks** fire at lifecycle events (session start, tool call, file save) regardless of what Claude decides.

Multiple practitioner guides published in the last 30 days - from [ClaudSkills](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/), [MCSA Guru](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained), [Tygart Media](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/), and [saad.sh](https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained) - all converge on: "these are not competing options, they sit at different layers." The r/ClaudeAI user behind the "searchable directory for Claude Code plugins" noted the core pain: ["Even when I found something useful, it was hard to answer the questions I actually cared about: Is this maintained? What does it install? Does it use hooks or MCP servers? Are people actually using it?"](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/)

Cross-platform discussion: X/Twitter, Reddit, Hacker News, Bluesky, Web.

### 2. Marketplace Proliferation and the Discovery Problem

A cluster of community-built registries and directories launched in the last 30 days, signaling that the ecosystem has hit a discovery-problem inflection point:

- **[CodeGuilds](https://codeguilds.dev)** - community registry for Claude Code skills, agents, and MCP servers (HN: 3 points).
- **[claudemarketplaces.com](https://claudemarketplaces.com/)** - claims 21,600+ skills, 2,500+ marketplaces, 12,500+ MCP servers updated daily from GitHub.
- **[SkillsForAgents](https://github.com/swissmarley/SkillsForAgents)** - distributable agent-skill marketplace for Claude Code, Codex CLI, OpenCode, Hermes with a one-line installer.
- **[SkillHub](https://github.com/ROV639/SkillHub)** - curated skill registry for AI coding agents.
- **[juftin/skills](https://github.com/juftin/skills)** - cross-platform agent skills directory and Claude Code marketplace, compatible with Claude Code, Codex CLI, Gemini CLI.
- **[agensi.io](https://www.agensi.io/learn/claude-code-plugins-extensions-skills-2026)** - curated catalog of skills organized by category with install-in-seconds flow; as of May 20 (W21), includes Kobiton's mobile testing plugin.

The [@HeyShruti7](https://x.com/HeyShruti7/status/2069066617301196875) "Resource Bible" thread (63 likes, 22 reposts) compiled 54 tools across official docs, MCP servers, skills, and automation into a single guide, framing the information asymmetry as a competitive edge: "Most people still haven't discovered this stack. That's your edge."

Cross-platform discussion: X/Twitter, Reddit, Hacker News, Web.

### 3. Claude Code 2.1.186 Ships MCP CLI Auth + Skills Tab

[@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2069162080393973775) (385 likes, the highest-engagement technical post) announced version 2.1.186 on June 22 with 33 CLI changes. The ecosystem-relevant highlights:

- `claude mcp login <name>` and `claude mcp logout <name>` - authenticate MCP servers from the CLI without the interactive `/mcp` menu; `--no-browser` flag for SSH workflows.
- Added a "Skills" section to the `/plugin Installed` tab.
- Named subagent spawns now enforce `Agent(type)` deny and `Agent(x,y)` allowed-types, blocking unauthorized agents.
- `!` shell commands now trigger automatic replies to command output.
- `pluginSuggestionMarketplaces` managed setting - admins can allowlist org marketplaces whose plugins get surfaced via context-aware tips (enterprise distribution).
- `/reload-skills` command (added in 2.1.152 per an earlier changelog) to re-scan skill directories without restarting.

A previous notable feature from the window: [Artifacts](https://x.com/claudeai/status/2067671912038240487) (17,940 likes - the most-engaged post in the corpus) - interactive pages built from Claude Code sessions (PR walkthroughs, living project dashboards) shared as private links inside organizations. "Artifacts draw on the full context of your session: codebase, plugins, skills, connected tools."

Cross-platform discussion: X/Twitter, Bluesky.

### 4. Enterprise MCP Adoption: Adobe Goes GA Inside Claude Enterprise

A significant enterprise signal this month: [Adobe's CX skills and MCP servers went generally available inside Anthropic's Claude Enterprise and Microsoft 365 Copilot](https://x.com/allday_stocks/status/2069016144808144930). Adobe announced strategic agentic AI partnerships with Accenture, Omnicom, WPP, and Stagwell's Code and Theory, deploying Adobe CX Enterprise and CX Enterprise Coworker for personalized customer experiences at scale. This is the first major enterprise software vendor shipping MCP-packaged capabilities directly into Claude's extension surface as a GA product.

The Shopify AI Toolkit (open-sourced April 9, MIT license) was another milestone earlier in the window - bundling the official Shopify MCP server stack, agent skills, and a Claude Code plugin into a single namespace.

Cross-platform discussion: X/Twitter, Web.

### 5. MCP Security Crisis: 43% Vulnerable, Malicious Skills in the Wild

Security is becoming the ecosystem's biggest systemic risk. The findings this month are striking:

- **[43% of MCP servers vulnerable to command execution](https://gentic.news/article/mcp-security-crisis-43-of-servers)** and 341 malicious skills found on marketplaces (BlueRock Security analysis of 7,000+ servers).
- **40+ CVEs** against MCP implementations in Python, TypeScript, Java, and Rust SDKs between January-April 2026 alone.
- **341 malicious skills** on publicly accessible marketplaces; researchers separately found 800+ malicious skills out of ~4,000 on another registry (20% malicious rate) delivering Atomic macOS Stealer.
- **Tenet Security (June 17)** documented a "TrustFall" vector: a public Sentry API key is enough to hijack Claude Code, Cursor, and Codex via MCP, enabling auto-run of attacker code with one click per [pondero-ai.bsky.social](https://bsky.app/profile/pondero-ai.bsky.social/post/3mom7pgh3u42b) and [cloud-native.activitypub.awakari.com.ap.brid.gy](https://bsky.app/profile/cloud-native.activitypub.awakari.com.ap.brid.gy/post/3moswcszo54h2).
- **NVIDIA open-sourced a security scanner** for AI agent skills; Cisco shipped a scanner with YARA rules and LLM-as-judge running against connected servers. [@danielswilfred2](https://x.com/danielswilfred2/status/2069317409912307978): "the mcp ecosystem is shipping servers way faster than anyone is auditing them."
- **Tool poisoning** as the primary attack: manipulating MCP tool descriptions/metadata to cause agents to invoke compromised tools.
- **Cross-server hijacking**: malicious MCP server injects descriptions overriding trusted servers' tools.

Cross-platform discussion: Bluesky, X/Twitter, Web.

### 6. Orchestration Layer Maturing: Dynamic Workflows, Subagents, Agent Teams

Anthropic shipped **Dynamic Workflows** in research preview on May 28, 2026 - moving orchestration logic out of the context window and into code. Hard limits: 16 concurrent agents, 1,000 agents per run. The community framing on [bsky.app/ssp.sh](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w) (13 likes, 6 replies): "Data engineering spent fifteen years building orchestrators - Airflow, Dagster, Prefect, Kestra. We are now doing the same thing for AI agents."

Community-built orchestration tools that shipped this month:
- **[OpenYabby](https://github.com/OpenYabby/OpenYabby)** - voice-controlled multi-agent orchestrator for Claude Code (HN: 8 points).
- **[Rayline](https://rayline.ai/)** - routes Claude Code subagents to on-device and cheaper models (HN: 11 points, 9 comments).
- **[5dive](https://github.com/5dive-com/5dive)** - run a team of Claude Code agents from Telegram (HN: 3 points).
- **[agent-pd](https://github.com/varmabudharaju/agent-pd/)** - "a police department for your Claude Code agents" (HN: 11 points, 8 comments).
- **[Omnigent](https://github.com/omnigent-ai/omnigent)** - Meta-Harness for Coding Agents (Claude Code, Codex, Cursor, Pi) from Databricks.
- **[barkain/claude-code-workflow-orchestration](https://github.com/barkain/claude-code-workflow-orchestration)** - automatic task decomposition, parallel agent execution, and plan mode integration.

[@justintsugranes.bsky.social](https://bsky.app/profile/justintsugranes.bsky.social/post/3mowgp6um3x24): "Claude Code is an agent SDK with the workspace abstraction solved. Reaching for the Anthropic SDK to build a coding agent means rebuilding context-loading and tool plumbing from scratch."

Cross-platform discussion: Bluesky, Hacker News, Web.

### 7. Token Bloat from Skills and Plugins

One practical pain surfacing prominently: skills and plugins add significant context overhead. The [r/ClaudeAI thread](https://www.reddit.com/r/ClaudeAI/comments/1tqw1cq/reduced_the_input_token_by_claudecode_to_812k/) "Reduced the input token by claude-code to ~8-12k less tokens, just optimizing skills and plugins" describes a user who discovered their first message was consuming 33-36k tokens after installing popular skills. Fix: a Claude Code workflow that scans skill and plugin usage over 60 days and audits which to keep, name-only, or remove.

[@martindotnet.bsky.social](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i) (8 likes, 3 replies) captured the meta-irony: "I find it hilarious that engineers will spend days, weeks even, curating their token dashboard for their claude code session, when they'll spend practically zero time adding telemetry to their apps to make it better. Claude Code: heres 72 graphs and dashboards. Production: install agent, go home."

Cross-platform discussion: Reddit, Bluesky.

### 8. Cross-Agent Config Sync: gaal CLI

A pain point with multi-agent setups: each agent expects a different config file (Claude Code wants `CLAUDE.md`, Codex wants `AGENTS.md`, Cursor wants `.cursorrules`). [gaal](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) - "a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines" - was built by a three-person team to solve this cross-agent config drift problem. Built in Go, open source.

This pattern - cross-agent portability of skills and configurations - is emerging as a distinct product category (see also juftin/skills and SkillsForAgents, both explicitly cross-platform).

Cross-platform discussion: Reddit, Web.

### 9. Indie MCP Builder Culture

[@_itsjustshubh](https://x.com/_itsjustshubh/status/2069330391920517365) is building "claude code plugins under brainrot creations - MCP servers for AMC showtimes, Luma event discovery, social scheduling, calendar automation. all designed to make the AI assistant feel less like a toy." This captures a broader indie builder wave: MCP servers are now accessible enough to build in evenings, for personal daily-life use cases rather than dev tooling.

Specific MCP servers that shipped this month on HN:
- [Seekstone](https://seekstone.dev/) - filesystem-direct Obsidian MCP server for Claude.
- [mcp-osascript](https://github.com/m0rvayne/mcp-osascript) - MCP server that lets Claude click menus on Mac.
- [claudenews.online](https://claudenews.online) - MCP server for Claude to read Claude/Anthropic news and RAG.
- [Co-Invest](https://www.liquid.trade/coinvest) - MCP server for Claude and ChatGPT to execute real trades.
- [openai-ads-mcp](https://github.com/HYPD-AI/openai-ads-mcp) - MCP for the ChatGPT Ads API.
- [niptao Telegram+Linear MCP](https://niptao.com/blog/an-engineer-you-manage-from-a-group-chat/) - auto-complete Linear tickets from Telegram via Claude Code loop.

Cross-platform discussion: X/Twitter, Hacker News.

### 10. Competition and Alternative Agent Harnesses

Not everyone is committed to Claude Code as the primary runtime. [@scoiattolo.mountainherder.xyz](https://bsky.app/profile/scoiattolo.mountainherder.xyz/post/3mork4bgzfs2w) (30 likes, the highest-engagement Bluesky post): "I finally set up polytoken with GLM 5.2 and it just did what I asked it to do without really any setup. As far as I'm concerned this is the best agent harness out there right now. I can't really see myself missing Claude Code at all."

[@timkellogg.me](https://bsky.app/profile/timkellogg.me/post/3moqlkzx3qc2p) on an MQTT-based event architecture (19 likes): "you can use it as a replacement for open-strix or hermes agent, but you can also simply run regular codex or claude code on it. everything is an event, published over MQTT. So if one subagent modifies a file that another is relying on, they can navigate that dynamically."

[@hadley.nz](https://bsky.app/profile/hadley.nz/post/3monqpsznms2j) (90 likes, 16 reposts - highest-engagement Bluesky post excluding security): "Coding agents like Claude Code feel like magic but they're really a bunch of tools in a trenchcoat. This week I build a working coding agent in R, starting from just three tools."

Cross-platform discussion: Bluesky.

---

## Cross-Source Patterns

**1. Discovery friction is the top ecosystem pain** - appears on Reddit (dedicated directory builder), HN (CodeGuilds, multiple Show HN submissions), X (Resource Bible thread), and Web (6 separate guide articles). The ecosystem grew faster than discovery mechanisms; every platform is independently building catalogs.

- Reddit: ["discovery is scattered across GitHub, Discord threads, blog posts, and individual repos"](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/)
- X: [@HeyShruti7](https://x.com/HeyShruti7/status/2069066617301196875) "Most people still haven't discovered this stack"
- HN: CodeGuilds, claudemarketplaces.com, multiple Show HN registry submissions

**2. Security is lagging the ecosystem's growth rate** - appears on Bluesky (Tenet Security/Sentry vector, NVIDIA scanner), X (Cisco scanner, MCP auditing gaps), and Web (43% vulnerable stat, 40+ CVEs, 341 malicious skills). The consensus: "the mcp ecosystem is shipping servers way faster than anyone is auditing them."

- X: [@danielswilfred2](https://x.com/danielswilfred2/status/2069317409912307978)
- Bluesky: [@pondero-ai.bsky.social](https://bsky.app/profile/pondero-ai.bsky.social/post/3mom7pgh3u42b), [@cloud-native](https://bsky.app/profile/cloud-native.activitypub.awakari.com.ap.brid.gy/post/3moswcszo54h2)
- Web: gentic.news, practical-devsecops.com, nimblebrain.ai

**3. Cross-agent portability is an emerging product category** - Skills, configs, and MCP servers are being built for Claude Code but users want them to work with Codex, Cursor, Gemini CLI, Windsurf. Multiple open-source projects (gaal, juftin/skills, SkillsForAgents, SkillHub) position cross-platform compatibility as their primary differentiator.

- Reddit: [gaal CLI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/)
- Web: juftin/skills, SkillsForAgents READMEs

**4. Context overhead from plugins is a real operational concern** - appears on Reddit (token optimization post) and Bluesky (ironic token dashboard observation). The instinct to install everything useful conflicts with performance.

- Reddit: [r/ClaudeAI token thread](https://www.reddit.com/r/ClaudeAI/comments/1tqw1cq/reduced_the_input_token_by_claudecode_to_812k/)
- Bluesky: [@martindotnet](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | — | — | "same project means different rules filename per agent" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) |
| r/ClaudeAI | I built a searchable directory for Claude Code plugins | — | — | "discovery is scattered across GitHub, Discord threads, blog posts" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) |
| r/ClaudeAI | Reduced the input token by claude-code to ~8-12k less tokens, just optimizing skills and plugins | — | — | "my input usage has increased to more than 33-36k tokens for the first message itself" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tqw1cq/reduced_the_input_token_by_claudecode_to_812k/) |
| r/artificial | Claude is completely unusable now | — | — | "Claude does everything it can to get out of work" | [link](https://www.reddit.com/r/artificial/comments/1twn3m7/claude_is_completely_unusable_now/) |
| r/artificial | Claude Fable made me realize I don't need a better model | — | — | "new LLM releases don't really change much for me anymore" | [link](https://www.reddit.com/r/artificial/comments/1u3acx4/claude_fable_made_me_realize_i_dont_need_a_better/) |
| r/artificial | Mystery company accidentally blew $500 million on Claude AI in a single month | — | — | "forgot to set usage limits for Claude licenses for employees" | [link](https://www.reddit.com/r/artificial/comments/1trmvgh/mystery_company_accidentally_blew_500_million_on/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | New in Claude Code: Artifacts. Interactive pages built from your session... | 17,940 | 1,282 | [link](https://x.com/claudeai/status/2067671912038240487) |
| @claudeai | Artifacts draw on the full context of your session: codebase, plugins, skills, connected tools. | 606 | 14 | [link](https://x.com/claudeai/status/2067671913418063892) |
| @claudeai | As your session keeps working, the artifact refreshes... | 566 | 28 | [link](https://x.com/claudeai/status/2067671914533863585) |
| @ClaudeCodeLog | Claude Code 2.1.186 has been released. 33 CLI changes. Highlights: mcp login/logout... | 385 | 20 | [link](https://x.com/ClaudeCodeLog/status/2069162080393973775) |
| @ClaudeCodeLog | Claude Code 2.1.186 is about to be released #cccnext | 128 | 2 | [link](https://x.com/ClaudeCodeLog/status/2069121643302010922) |
| @ClaudeCodeLog | CLI 2.1.152: Added /reload-skills, MessageDisplay hook, pluginSuggestionMarketplaces... | 28 | 1 | [link](https://x.com/ClaudeCodeLog/status/2059451400338223550) |
| @HeyShruti7 | This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. | 63 | 22 | [link](https://x.com/HeyShruti7/status/2069066617301196875) |
| @ClaudeCodeLog | Claude Code CLI 2.1.186 changelog (detailed thread) | 22 | 1 | [link](https://x.com/ClaudeCodeLog/status/2069162091370467615) |
| @Oluwaphilemon1 | Someone built the perfect GUI for Claude Code. Browse sessions, custom agents, MCP servers... | 12 | 3 | [link](https://x.com/Oluwaphilemon1/status/2069073525785133180) |
| @HelloVyom | The real advantage starts below the surface. MCP servers, custom prompts, agents.md, subagents... | 15 | 0 | [link](https://x.com/HelloVyom/status/2069029267682496993) |
| @xieike | IF YOU'RE NEW TO CLAUDE CODE - they're using 20% of what it can actually do | 3 | 0 | [link](https://x.com/xieike/status/2069340684142714930) |
| @_itsjustshubh | claude code plugins under brainrot creations - MCP servers for AMC, Luma events, social scheduling | 2 | 0 | [link](https://x.com/_itsjustshubh/status/2069330391920517365) |
| @danielswilfred2 | I keep connecting to random MCP servers and never check if they're safe. Cisco just shipped a scanner... | 1 | 1 | [link](https://x.com/danielswilfred2/status/2069317409912307978) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| gagewoodard | Norrin - Git/ diff control in Claude Code | 4 | 1 | — | [link](https://news.ycombinator.com/item?id=48619320) |
| davidvgilmore | Rayline routes Claude Code subagents to on-device and cheaper models | 11 | 9 | — | [link](https://rayline.ai/) |
| simplybychris | Open-source Antigravity plugin for Claude Code | 2 | 0 | — | [link](https://simplybychris.github.io/antigravity-plugin-cc/) |
| softie123 | A police department for your Claude Code agents | 11 | 8 | — | [link](https://github.com/varmabudharaju/agent-pd/blob/master/README.md) |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | 0 | — | [link](https://github.com/OpenYabby/OpenYabby) |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | [link](https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over) |
| davidvgilmore | Show HN: 5dive - Run a Team of Claude Code Agents from Telegram | 3 | 0 | — | [link](https://github.com/5dive-com/5dive) |
| haimm | CodeGuilds - community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | [link](https://codeguilds.dev) |
| imaxxs | Gemini CLI vs. Claude Code: Why agent capabilities matter more than prompts | 3 | 0 | — | [link](https://imaxxs.com/behavioral-induction-capabilities-shape-execution) |
| BaguettePwnM | I made a free MCP server so your Claude can read Claude/Anthropic news and RAG | 3 | 0 | — | [link](https://claudenews.online) |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 3 | 3 | — | [link](https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over) |
| fzysingularity | Omnigent: Meta-Harness for Coding Agents (Claude Code, Codex, Cursor, Pi) | 2 | 0 | — | [link](https://github.com/omnigent-ai/omnigent) |
| m0rvayne | MCP server that lets Claude click menus on your Mac and fix its own mistakes | 2 | 0 | — | [link](https://github.com/m0rvayne/mcp-osascript) |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | [link](https://ai-specialists.vercel.app) |
| singlas | Auto complete tickets using Claude Code loop on telegram with linear MCP | 1 | 1 | — | [link](https://niptao.com/blog/an-engineer-you-manage-from-a-group-chat/) |
| FayzanMalik | Visual composer for Claude Code multi-agent workflows | 2 | 0 | — | [link](https://github.com/fayzan123/claude-workflow-composer) |
| miwooyork | Co-Invest - an MCP server that lets Claude and ChatGPT execute real trades | 2 | 0 | — | [link](https://www.liquid.trade/coinvest) |
| manelrv | CCTV - See which Claude Code agent needs you, from the menu bar | 2 | 0 | — | [link](https://github.com/manelrv/CCTV) |
| cionut | Show HN: MCP for the ChatGPT Ads API | 3 | 1 | — | [link](https://github.com/HYPD-AI/openai-ads-mcp) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @hadley.nz | Coding agents like Claude Code feel like magic but they're really a bunch of tools in a trenchcoat. Built a working coding agent in R from just three tools. | 90 | [link](https://bsky.app/profile/hadley.nz/post/3monqpsznms2j) |
| @scoiattolo.mountainherder.xyz | I finally set up polytoken with GLM 5.2... As far as I'm concerned this is the best agent harness out there right now. | 30 | [link](https://bsky.app/profile/scoiattolo.mountainherder.xyz/post/3mork4bgzfs2w) |
| @simonwillison.net | My parallel agent side-project: having Claude Code port the Moebius image pinpointing model to ONNX to run entirely in the browser. | 38 | [link](https://bsky.app/profile/simonwillison.net/post/3mow3ec7ycc2s) |
| @timkellogg.me | can use it as a replacement for open-strix or hermes agent... everything is an event, published over MQTT. | 19 | [link](https://bsky.app/profile/timkellogg.me/post/3moqlkzx3qc2p) |
| @ssp.sh | Data engineering spent fifteen years building orchestrators - Airflow, Dagster, Prefect, Kestra. We are now doing the same thing for AI agents. | 13 | [link](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w) |
| @sungkim.bsky.social | How to make your AI coding agent (Claude Code and Codex) dumb instantly - /compact. | 14 | [link](https://bsky.app/profile/sungkim.bsky.social/post/3mou777yayc27) |
| @martindotnet.bsky.social | I find it hilarious that engineers will spend days curating their token dashboard when they'll spend zero time adding telemetry. Claude Code: 72 graphs. Production: install agent, go home. | 8 | [link](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i) |
| @pondero-ai.bsky.social | That fake Sentry report vector is exactly why the trust prompt is so dangerous. One click and Claude Code or Cursor can auto-run attacker code via MCP. | 3 | [link](https://bsky.app/profile/pondero-ai.bsky.social/post/3mom7pgh3u42b) |
| @cloud-native.activitypub | A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex. | 4 | [link](https://bsky.app/profile/cloud-native.activitypub.awakari.com.ap.brid.gy/post/3moswcszo54h2) |
| @undercode.bsky.social | NVIDIA Just Open-Sourced a Security Scanner for AI Agent Skills. | 2 | [link](https://bsky.app/profile/undercode.bsky.social/post/3mov3vufebg2u) |
| @justintsugranes.bsky.social | Claude Code is an agent SDK with the workspace abstraction solved. | 3 | [link](https://bsky.app/profile/justintsugranes.bsky.social/post/3mowgp6um3x24) |
| @stealthdevtools.bsky.social | Your AI agent burns tokens reading files blindly. 25x lower model cost on RepoQA benchmarks, 45% fewer tokens. Works with Claude Code, Cursor, Codex, Windsurf + 30 more. | 6 | [link](https://bsky.app/profile/stealthdevtools.bsky.social/post/3mo4lsfmch227) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Directory: 21,600+ skills, 12,500+ MCP servers, updated daily |
| ClaudSkills | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Canonical skills vs MCP vs plugins explainer; open SKILL.md registry |
| ClaudSkills | https://claudskills.com/learn/claude-code-plugins/ | Plugin definition and discovery guide |
| MCSA Guru | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Layer-by-layer technical breakdown |
| Tygart Media | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Practitioner guide from autonomous agent operator |
| saad.sh | https://saad.sh/posts/claude-code-hooks-skills-mcp-plugins-explained | All 6 extension surfaces explained (Hooks, Skills, MCP, Plugins, CLAUDE.md, AGENTS.md) |
| Claude Docs | https://code.claude.com/docs/en/skills | Official "Extend Claude with skills" documentation |
| Claude Docs | https://support.claude.com/en/articles/13837440-use-plugins-in-claude | Official "Use plugins in Claude" help article |
| juftin/skills | https://github.com/juftin/skills | Cross-platform agent skills directory and marketplace (Shell, v1.1.0) |
| SkillsForAgents | https://github.com/swissmarley/SkillsForAgents | Distributable marketplace for Claude Code, Codex, OpenCode, Hermes |
| SkillHub | https://github.com/ROV639/SkillHub | Curated skill registry for AI coding agents |
| agensi.io | https://www.agensi.io/learn/claude-code-plugins-extensions-skills-2026 | Curated catalog with instant install |
| Nimbalyst | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Tested plugin guide |
| Nimbalyst | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | Ranked MCP servers guide |
| MindStudio | https://mindstudio.ai/blog/code-with-claude-2026-new-agent-features | 5 new agent features: Dynamic Workflows, subagents, Agent Teams |
| Shipyard | https://shipyard.build/blog/claude-code-multi-agent/ | Multi-agent orchestration patterns |
| alexop.dev | https://alexop.dev/posts/claude-code-workflows-deterministic-orchestration/ | Deterministic multi-agent workflow guide |
| Developers Digest | https://developersdigest.tech/blog/claude-code-agent-teams-subagents-2026 | Agent Teams and subagents playbook |
| Gentic News | https://gentic.news/article/mcp-security-crisis-43-of-servers | 43% vulnerable stat, 341 malicious skills found |
| Practical DevSecOps | https://practical-devsecops.com/mcp-security-vulnerabilities/ | Tool poisoning and cross-server hijacking attacks |
| DEV Community | https://dev.to/piiiico/mcp-security-vulnerabilities-in-2026-40-cves-and-counting-4pco | 40+ CVEs against MCP SDKs |
| NimbleBrain | https://nimblebrain.ai/mcp/mcp-security/state-of-mcp-security/ | State of MCP security 2026 |
| Pondero AI | https://pondero.ai/security/guides/trustfall-ai-coding-agent-rce-june-2026/ | TrustFall: Sentry key vector breakdown |

---

## Stats Block

```
├─ 🟠 Reddit: 6 threads │ — upvotes │ — comments
├─ 🔵 X: 20 posts │ 19,800 likes │ 1,374 reposts
├─ 🟢 HN: 19 stories │ 74 points │ 24 comments
├─ 🦋 Bluesky: 12 posts │ 230 likes │ 25 reposts
├─ 🐙 GitHub: 11 items │ 197 reactions │ 134 comments
├─ 🌐 Web: 24 pages (9 engine + 15 WebSearch)
└─ 🗣️ Top voices: @ClaudeCodeLog, @claudeai, @HeyShruti7 │ r/ClaudeAI, r/artificial
```

---

## Data Gaps

- **Reddit returned 0 upvote data** - Reddit's public JSON API returned 403 on search; the RSS tier recovered 6 threads but without vote counts.
- **YouTube: 0 results** - yt-dlp search returned empty for this query; there is almost certainly YouTube content on Claude Code skills/MCP (tutorials, reviews) that was not captured.
- **TikTok and Instagram: 0 results** - ScrapeCreators returned HTTP 402 (quota limit); TikTok content on #claudecode exists but was not retrieved.
- **Polymarket: 0 markets** - no active prediction markets on this topic.
- **Reddit coverage is thin** - 6 threads is a small sample; r/ClaudeAI has substantial ongoing discussion not captured due to API 403s.
- **Evidence is X-heavy** - 20 X posts vs 6 Reddit threads creates platform concentration; social sentiment may skew toward the most engaged X users rather than the broader practitioner base.
- **Approximate coverage:** ~60% (missing YouTube, TikTok, Instagram, and bulk Reddit).
- **The `r/artificial` threads** (Claude model quality, $500M overspend) are adjacent noise, not directly on-topic for the skills/plugins ecosystem; included for completeness.

---

## Key Quotes

> "Most people still haven't discovered this stack. That's your edge." - [@HeyShruti7](https://x.com/HeyShruti7/status/2069066617301196875) on X

> "I find it hilarious that engineers will spend days, weeks even, curating their token dashboard for their claude code session, when they'll spend practically zero time adding telemetry to their apps to make it better. Claude Code: heres 72 graphs and dashboards. Production: install agent, go home." - [@martindotnet.bsky.social](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i) on Bluesky

> "I finally set up polytoken with GLM 5.2 and it just did what I asked it to do without really any setup. As far as I'm concerned this is the best agent harness out there right now. I can't really see myself missing Claude Code at all." - [@scoiattolo.mountainherder.xyz](https://bsky.app/profile/scoiattolo.mountainherder.xyz/post/3mork4bgzfs2w) on Bluesky

> "the mcp ecosystem is shipping servers way faster than anyone is auditing them. this is the first real security tool for it." - [@danielswilfred2](https://x.com/danielswilfred2/status/2069317409912307978) on X

> "Claude Code is an agent SDK with the workspace abstraction solved. Reaching for the Anthropic SDK to build a coding agent means rebuilding context-loading and tool plumbing from scratch." - [@justintsugranes.bsky.social](https://bsky.app/profile/justintsugranes.bsky.social/post/3mowgp6um3x24) on Bluesky

> "Data engineering spent fifteen years building orchestrators - Airflow, Dagster, Prefect, Kestra. We are now doing the same thing for AI agents." - [@ssp.sh](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w) on Bluesky

> "MCP servers for AMC, Luma events, social scheduling, calendar automation. all designed to make the AI assistant feel less like a toy." - [@_itsjustshubh](https://x.com/_itsjustshubh/status/2069330391920517365) on X

> "Coding agents like Claude Code feel like magic but they're really a bunch of tools in a trenchcoat." - [@hadley.nz](https://bsky.app/profile/hadley.nz/post/3monqpsznms2j) on Bluesky

> "discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer the questions I actually cared about: Is this maintained? What does it install?" - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) on Reddit
