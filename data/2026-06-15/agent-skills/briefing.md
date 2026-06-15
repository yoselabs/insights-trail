# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-15
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Bluesky, Reddit, Web (engine + supplemental)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 1 thread | N/A upvotes, N/A comments | Only r/ClaudeAI surfaced; ScrapeCreators 402'd |
| X/Twitter | 14 posts | 559 likes, 67 reposts | Strong signal from @ClaudeCodeLog changelog account |
| YouTube | 0 videos | — | yt-dlp and SC both returned 0; SC 402 |
| Hacker News | 29 stories | 3,915 points, 1,989 comments | Richest source; "Daily Driver" post 451 pts |
| TikTok | 0 videos | — | SC 402; no results |
| Instagram | 0 reels | — | SC v2 reels endpoint 500'd on multi-token query |
| Bluesky | 12 posts | 92 likes, 6 reposts | Playful practitioner commentary |
| Polymarket | 0 markets | — | No prediction markets on this topic |
| Web | 28 pages | — | 19 engine (GitHub, dev.to, claude.com) + 9 supplemental |

---

## Synthesized Findings

### 1. The Official Marketplace Landed — Quietly and With Some Hype Around It

Anthropic launched `anthropics/claude-plugins-official` in May 2026 with no press release - just a `/plugin` command that started working. Per [x/@chenzeling4](https://x.com/chenzeling4/status/2059394913326993574): "Anthropic quietly launched an official plugin directory for Claude Code and it changes how you extend your AI workflow. One command installs community-built MCP servers, slash commands, and agent skills — no config file hacking required." By June 1, the top install counts were staggering: Frontend Design at 829,316 installs, Superpowers at 752,120, Context7 at 348,660, per [Pasquale Pillitteri's May 2026 release notes](https://pasqualepillitteri.it/en/news/2223/claude-code-may-2026-release-notes-radio-plugin-marketplace). The official marketplace source is available at [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) and searchable via [claude.com/plugins](https://code.claude.com/docs/en/discover-plugins). Platforms active: X, HN, Bluesky, Web.

### 2. Skills, MCP, Plugins — Three Different Things Developers Keep Conflating

A recurring HN and dev.to theme this month is clarifying the taxonomy. [DEV Community (alexcloudstar)](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) put it plainly: "Skills equal procedural knowledge (30-50 tokens each, loaded on-demand). MCP equals external tool connections (can use 50k+ tokens). Plugins are shareable bundles of everything." Skills are markdown SKILL.md files discoverable by the agent; MCP servers connect to external APIs and databases; plugins bundle both plus hooks and slash commands. The [Engineering Playbook on Skills](https://engineering-playbook.vercel.app/claude-code/skills) defines a skill as "a packaged workflow that Claude Code can invoke either by user request or by intent-matching." The SKILL.md open standard is now cross-platform: Claude Code, Cursor, Codex CLI, and Gemini CLI all load the same files, per [Agensi's marketplace landscape coverage](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026). Platforms: HN, Web, Bluesky.

### 3. Claude Code CLI Is Getting Rapid Plugin Infrastructure Updates

[@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2059451400338223550) has been tracking a wave of plugin-focused changelog updates: v2.1.152 added `/reload-skills` to re-scan skill directories without restarting, added `pluginSuggestionMarketplaces` managed setting for org admins to allowlist specific marketplaces. [v2.1.153](https://x.com/ClaudeCodeLog/status/2059802891607589286) added `skipLfs` option to github/git plugin marketplace sources and fixed stateful MCP server SSE reconnect-looping. [v2.1.157](https://x.com/ClaudeCodeLog/status/2060460312457810182) added `claude plugin init <name>` to scaffold new plugins in `.claude/skills` plus autocomplete for `/plugin` arguments (subcommands, installed plugin names, plugins from known marketplaces). The cadence - three changelogs across three days in late May - signals plugin infrastructure is a current development priority. Platforms: X.

### 4. Eight Marketplace Competitors Emerged in Six Months

The ecosystem exploded from one skill registry in December 2025 to eight major competing marketplaces by Q2 2026, per [Agensi's comprehensive breakdown](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). The major players: **Skills.sh** (Vercel-backed, January 2026, npm-style package manager for skills), **Agensi** (curated with automated security scans, 80/20 revenue split for creators), **ClaudeSkills.info** (free community-vetted), **SkillsMP** (800K+ skills scraped from public GitHub, large catalog minimal curation), **ClawHub** (20K+ registered skills, richer metadata), **skills.2389.ai** (open source from [2389 Research](https://skills.2389.ai/), installable via `npx skills add`), **claudemarketplaces.com** (daily-updated community directory with 21,600+ skills and 9,900+ MCP servers listed). [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) and [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) both covered the landscape shift. Platforms: Web, X.

### 5. MCP Became the Universal Standard — But Production Scaling Hurts

MCP hit 97 million monthly SDK downloads with over 10,000 servers indexed across public registries, moved governance to the Linux Foundation, and now has native support in Claude, ChatGPT, Gemini, Copilot, and Cursor, per [Context Studios Blog](https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us). Per [@NewsTongueX](https://x.com/NewsTongueX/status/2066220600650043864): "Four major agent communication protocols published in 18 months - Model Context Protocol from Anthropic (late 2024), Agent2Agent from Google (April 2025), Agent Communication Protocol from IBM Research (March 2025), and Agent Network Protocol from an independent working group — MCP has dominated tool-calling with Linux Foundation confirming 10,000+ servers." The problem: [The New Stack](https://thenewstack.io/model-context-protocol-roadmap-2026/) reports production scaling is painful - "stateful sessions fight with load balancers, horizontal scaling requires workarounds, and there's no standard way for a registry or crawler to learn what a server does without connecting to it." The upcoming [RC 2026-07-28](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) addresses this with a stateless core, MCP Apps (server-rendered UIs), and a Tasks extension. A [QVeris registry guide](https://try.qveris.ai/mcp-registry/) reports the official MCP Registry now hosts nearly 2,000 servers in preview. HN's ["Bad MCP design costs your agent 5x more tokens"](https://news.ycombinator.com/item?id=48407391) (15 pts) shows practitioners are learning this the hard way. Platforms: X, HN, Web.

### 6. Security Is the Elephant in the Room

[@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) (8 likes, 6 RT) surfaced the NVIDIA security scanner story with the most-read framing this month: "Skills are the new plugins. Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins. Every AI agent framework now has a marketplace of community-built skills you can install with one command. One command. That skill now runs inside your AI agent. With access to everything your agent can do." [JFrog's blog post](https://jfrog.com/blog/agent-skills-new-ai-packages/) makes the same argument from the enterprise side: "Agent Skills are the New Packages of AI" - arguing that skills need the same trust model as npm packages, and referencing incidents named ToxicSkills and ClawHavoc that prompted security scanning as a marketplace differentiator. [Agensi](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) noted security scanning has become a "selling point" as buyers ask about it before installing. The [AI specialist registry coverage](https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm) highlighted a new verified skill registry explicitly built around this need. Platforms: X, Web.

### 7. Hype and Misinformation Are Already Circulating

[@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385) called out the BS directly: "$40,000/month from Claude skills - no proof, no screenshot, no client, nothing. Half the install commands don't even work. /plugin marketplace add isn't real Claude Code syntax. Skills are real. MCP servers are real. The $40K is a number he typed to get follows." [@artyomx](https://x.com/artyomx/status/2065925946717168096) (8 likes) actually inspected the official marketplace files: "I checked the actual marketplace manifest and plugin source on your machine. What's TRUE: The marketplace is real and official → anthropics/claude-plugins-official. What's FALSE / hype: 'Then sets everything up step-by-step for you' - this is the lie. The skill is explicitly, in-bold, read-only. 'Turns Claude Code into an actual AI dev environment' / 'feels completely different' - pure marketing. Under the hood it's literally one SKILL.md + 5 reference markdown files." The gap between promise and implementation is a recurring theme across X and Bluesky. Platforms: X, Bluesky.

### 8. Practitioners Are Shipping Real Things With Plugins

Bluesky practitioner [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) (35 likes): "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." In a follow-up (11 likes): "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." [@coolhand.bsky.social](https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y) (12 likes): "I made three large kits for that specific problem... I built plugins anyway for Claude and OpenClaw and the rest." Third-party partnerships are flowing through the official marketplace: [@appwrite](https://x.com/appwrite/status/2064273389158903850) (10 likes): "The Appwrite plugin is now available in the official Claude marketplace. Claude Code can work with Appwrite using built-in agent skills and MCP servers." 42Crunch per [Bluesky/@brunopedro.com](https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z) announced "dedicated AI coding plugins that unlock an autonomous, end-to-end Agentic DevSecOps model for the enterprise." Platforms: Bluesky, X.

### 9. Dynamic Workflows — Claude Writing Its Own Agent Harness

Anthropic's "Dynamic Workflows in Claude Code" post ([claude.com](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code), [HN 200 pts 135 cmt](https://news.ycombinator.com/item?id=48311705)) shipped May 28. Claude can now write and orchestrate its own multi-agent harness on the fly. The companion blog post at [claude.com/blog/a-harness-for-every-task](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) covers the patterns. "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs" by arps18 ([HN 451 pts 254 cmt](https://arps18.github.io/posts/claude-code-mastery/)) is the community's most-upvoted synthesis of how all the pieces fit together. Third-party tooling is emerging fast: Ruflo (per [Bluesky/@github-trending-js](https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b)) extends Claude Code with "100+ cooperative agents, self-learning memory, zero-trust federation." Platforms: HN, Bluesky.

### 10. Cross-Agent Config Sync Is a Real Pain Point

[r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) (the only Reddit result captured): "We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines." The team behind `gaal` built it because: "Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules." Multiple config files for the same project across agents is a growing friction point. The [agent-skill-registry project](https://github.com/linny006/agent-skill-registry) ("discover, version, and install across any coding agent") and [pakx](https://github.com/pakxdev/pakx) ("package manager for AI agent components - skills, MCP servers, subagents, prompts, commands, hooks") are both responding to this. [skill-hub by CassianFlorin](https://github.com/CassianFlorin/skill-hub) describes itself as "The package manager for AI agent skills. Install, update, sync, and govern skills across coding agents." Platforms: Reddit, Web.

---

## Cross-Source Patterns

### Pattern 1: Skills = The New npm Packages (Security Debt Incoming)
- **Signal:** Appears on X, HN, Web, JFrog blog
- **Platforms:** X, HN, Web
- Per [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728): "Skills are the new plugins... one command. That skill now runs inside your AI agent."
- Per [JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/): same lifecycle as npm means the same supply chain risks
- ToxicSkills and ClawHavoc incidents already named as historical precedents
- Security scanning is now a marketplace differentiator (Agensi's key pitch)

### Pattern 2: MCP Won Tool-Calling, But Protocol Proliferation Continues
- **Signal:** X, HN, Web
- [@NewsTongueX](https://x.com/NewsTongueX/status/2066220600650043864): 4 protocols in 18 months, "HTTP transport gap remains unsolved"
- MCP has 97M monthly downloads and Linux Foundation backing
- [@dongwukeji](https://x.com/dongwukeji/status/2066279732715663441): "landmark standardization of MCP and A2A by Agentic AI Foundation"
- HN "Bad MCP design costs your agent 5x more tokens" (15 pts): token efficiency is a live concern

### Pattern 3: Marketplace Explosion + Hype Backlash
- **Signal:** X, Bluesky, Web
- 8 marketplaces in 6 months; SkillsMP alone claims 800K+ skills scraped from GitHub
- [@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385): "$40K/month claims are fake"
- [@artyomx](https://x.com/artyomx/status/2065925946717168096): "Under the hood it's literally one SKILL.md + 5 markdown files"
- Signal-to-noise problem: large catalogs with minimal curation vs. small curated paid marketplaces

### Pattern 4: Cross-Agent Compatibility Gap
- **Signal:** Reddit, Web, Bluesky
- CLAUDE.md vs AGENTS.md vs .cursorrules: same project, three config files
- Multiple projects (gaal, skill-hub, pakx, agent-skill-registry) building cross-agent sync tools
- SKILL.md open standard is the community's best answer - works on Claude Code, Cursor, Codex CLI, Gemini CLI

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | N/A | N/A | "Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules" | https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @ClaudeCodeLog | CLI 2.1.152: /reload-skills added; pluginSuggestionMarketplaces setting | 27 | 0 | https://x.com/ClaudeCodeLog/status/2059451400338223550 |
| @ClaudeCodeLog | CLI 2.1.157: claude plugin init + plugin autocomplete added | 19 | 0 | https://x.com/ClaudeCodeLog/status/2060460312457810182 |
| @ClaudeCodeLog | CLI 2.1.153: skipLfs for plugin marketplace sources; MCP SSE fix | 14 | 0 | https://x.com/ClaudeCodeLog/status/2059802891607589286 |
| @JackWoth98 | 30 days of using Antigravity CLI… | 422 | 53 | https://x.com/JackWoth98/status/2065529819685871690 |
| @appwrite | Appwrite plugin now in official Claude marketplace | 10 | 1 | https://x.com/appwrite/status/2064273389158903850 |
| @RituWithAI | NVIDIA security scanner for AI agent skills — almost nobody using it | 8 | 6 | https://x.com/RituWithAI/status/2065656659842842728 |
| @artyomx | Fact-checked official marketplace: skill is read-only SKILL.md + 5 markdown files | 8 | 1 | https://x.com/artyomx/status/2065925946717168096 |
| @swarminged | Agent-3D web component ships: memory, emotion, voice, on-chain identity | 33 | 5 | https://x.com/swarminged/status/2066308024382497061 |
| @turnkeyhq | Architecting secure onchain workflows with AI Skills and MCP Servers | 14 | 1 | https://x.com/turnkeyhq/status/2065069029375541667 |
| @chenzeling4 | Anthropic quietly launched official plugin directory — one command install | 2 | 1 | https://x.com/chenzeling4/status/2059394913326993574 |
| @NewsTongueX | 4 agent protocols in 18 months; HTTP transport gap unsolved | 1 | 0 | https://x.com/NewsTongueX/status/2066220600650043864 |
| @dongwukeji | MCP + A2A standardized; Agentic Inference Layer is the new battlefield | 0 | 0 | https://x.com/dongwukeji/status/2066279732715663441 |
| @makecrypto4304 | "$40K/month from Claude skills" — fake claim, install commands don't even work | 0 | 0 | https://x.com/makecrypto4304/status/2065266100858708385 |
| @Coiniseasy | Squid MCP | 1 | 0 | https://x.com/Coiniseasy/status/2066461008802308456 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| mellosouls | AI agent bankrupted their operator while trying to scan DN42 | 1457 | 531 | — | https://lantian.pub/en/article/fun/ai-agent-bankrupted-their-operator-scan-dn42lantian.lantian/ |
| tanelpoder | AI agent runs amok in Fedora and elsewhere | 549 | 244 | — | https://lwn.net/SubscriberLink/1077035/c7e7c14fbd60fae9/ |
| tvissers | A €0.01 bank transfer could compromise a banking AI agent | 208 | 202 | — | https://blue41.com/blog/how-we-helped-bunq-secure-their-financial-ai-assistant/ |
| anhldbk | Apache Burr: Build reliable AI agents and applications | 248 | 115 | — | https://burr.apache.org/ |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| wapasta | Robinhood now lets your AI agents trade stocks | 112 | 181 | — | https://techcrunch.com/2026/05/27/robinhood-now-lets-your-ai-agents-trade-stocks/ |
| ruxudev | Build a Basic AI Agent from Scratch: Long Task Planning | 141 | 53 | — | https://medium.com/@rogi23696/build-a-basic-ai-agent-from-scratch-long-task-planning-14e803f9bd6d |
| julienreszka | Now AI agents need what RSS does | 85 | 65 | — | https://julienreszka.com/blog/rss-is-back-ai-agents-are-reading-it/ |
| timshell | CAPTCHAs can still detect AI agents | 84 | 72 | — | https://research.roundtable.ai/captchas-detect-ai/ |
| nab | Show HN: Boxes.dev: ditch localhost; run Claude Code and Codex in the cloud | 104 | 79 | — | https://boxes.dev |
| finnworks | Show HN: skills-for-humanity – 171 structured reasoning skills for Claude Code | 28 | 7 | — | https://github.com/human-avatar/skills-for-humanity |
| JohnnyZhang483 | Bad MCP design costs your agent 5x more tokens | 15 | 1 | — | https://news.ycombinator.com/item?id=48407391 |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | https://codeguilds.dev |
| davidvgilmore | Show HN: Rayline routes Claude Code subagents to on-device and cheaper models | 11 | 9 | — | https://rayline.ai/ |
| 6stringmerc | The AI Agent in the Billing Department of Verizon Is a Mentally Handicapped Thug | 28 | 9 | — | https://samhenrycliff.medium.com/the-ai-agent-in-the-billing-department-of-verizon-wireless-is-a-mentally-handicapped-thug-99890a389ff5 |
| sermakarevich | Show HN: Generate Claude Code Workflows using Spec Driven Development approach | 5 | 0 | — | https://news.ycombinator.com/item?id=48306730 |
| lodar | Show HN: 5dive – Run a Team of Claude Code Agents from Telegram | 3 | 0 | — | https://github.com/5dive-com/5dive |
| softie123 | Show HN: A police department for your Claude Code agents | 11 | 8 | — | https://github.com/varmabudharaju/agent-pd/blob/master/README.md |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | 0 | — | https://github.com/OpenYabby/OpenYabby |
| StanAngeloff | Teaching tmux to babysit my Claude Code agents | 3 | 0 | — | https://blog.angeloff.name/post/2026/05/29/teaching-tmux-to-babysit-my-claude-code-agents/ |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | 0 | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| Reebz | Show HN: My custom Statusline for Claude Code (Python wrapper around claudeline) | 3 | 4 | — | https://gist.github.com/Reebz/741c5647c860fe0b5214f39d9d887240 |
| honeylabs | Show HN: HoneyLabs – Public honeypot threat Intel feed and MCP server | 4 | 2 | — | https://honeylabs.net |
| tangxinzhi158 | Show HN: I gave my AI video generator 86 MCP tools so Claude Code can drive it | 3 | 1 | — | https://github.com/openclaw-easy/ViralMint |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |
| tortilla | Lua.ex: Sandboxed Lua 5.3 on the Beam, Built for AI Agents | 61 | 0 | — | https://deflua.com/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion" | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | "I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @camilleroux.com | "Top 13 skills et plugins Claude Code qui ont marqué 2026: celui qui coupe 63% des tokens..." | 8 | https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p |
| @viriditax.bsky.social | "making VST plugins was the first thing I tried to do with Claude Code to flex it" | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @github-trending-js.bsky.social | "Ruflo: multi-agent AI framework extending Claude Code with 100+ cooperative agents, self-learning memory, zero-trust federation" | 1 | https://bsky.app/profile/github-trending-js.bsky.social/post/3mnayumied42b |
| @brunopedro.com | "42Crunch: dedicated AI coding plugins that unlock autonomous Agentic DevSecOps for the enterprise" | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills into Claude Code, Cursor, Codex — MIT-licensed" | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @humancoders.com | "Top 13 skills et plugins Claude Code: audit de dette technique, réduction de tokens, best practices en prod…" | 5 | https://bsky.app/profile/humancoders.com/post/3mm7iqnotmy2p |
| @hackernewsbot.bsky.social | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs - Discussion | 1 | https://bsky.app/profile/hackernewsbot.bsky.social/post/3mmswongo5z2p |
| @mengli512.bsky.social | "Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression" | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |
| @toyinariyo.bsky.social | "Many Godot AI plugins can be used with Claude Code and Codex" | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Official Plugin Docs | https://code.claude.com/docs/en/discover-plugins | Official docs on discovering and installing plugins through marketplaces |
| anthropics/claude-plugins-official (GitHub) | https://github.com/anthropics/claude-plugins-official | Official Anthropic-managed plugin directory; marketplace.json defines curated catalog |
| anthropics/claude-plugins-official marketplace.json | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Raw marketplace manifest, verified as source of truth |
| Claude Help Center - What are skills? | https://support.claude.com/en/articles/12512176-what-are-skills | Official definition: skills are user-invocable packaged workflows |
| Claude Release Notes | https://support.claude.com/en/articles/12138966-release-notes | Official changelog for all Claude Code updates |
| Dynamic Workflows blog post (claude.com) | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Anthropic's announcement of Claude writing its own multi-agent harness |
| A harness for every task (claude.com) | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | How dynamic workflows work and patterns for getting the most out of them |
| DEV Community - Skills/MCP/Plugins fit together | https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532 | Practitioner guide clarifying the taxonomy; first plugin transformed a frontend workflow |
| DEV Community - How Skills System Actually Works | https://dev.to/arihantdeva/how-claude-codes-skills-system-actually-works-3d81 | Engineering deep-dive: skills as discoverable assets with structured discovery |
| DEV Community - Build Your Own Marketplace | https://dev.to/nagell/build-your-own-claude-code-marketplace-scaffold-structure-and-auto-updates-4n3f | Guide: Claude Code marketplace is a GitHub repo with a specific folder structure |
| Engineering Playbook - Skills | https://engineering-playbook.vercel.app/claude-code/skills | Skills = packaged workflow invocable by user request or intent-matching |
| MCP Official Roadmap | https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/ | 2026 priorities: stateless HTTP, Server Cards, enhanced agent communication |
| MCP RC 2026-07-28 | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | Largest MCP revision since launch: stateless core, MCP Apps, Tasks extension |
| The New Stack - MCP Production Pain | https://thenewstack.io/model-context-protocol-roadmap-2026/ | Stateful sessions, load balancer conflicts, no server discovery without connecting |
| Context Studios - MCP Ecosystem 2026 | https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us | 97M monthly SDK downloads, Linux Foundation governance, 10K+ servers |
| QVeris MCP Registry Guide | https://try.qveris.ai/mcp-registry/ | Official MCP Registry hosting ~2,000 servers; sub-registries add capability routing |
| Clarista - MCP & Plugins Guide | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | "MCP is USB for AI: one protocol, many tools, many clients" |
| Agent Patterns Catalog - MCP | https://www.agentpatternscatalog.org/patterns/mcp/ | MCP's role in Tool Discovery pattern; agent discovers tools at runtime |
| Agensi - Best Skill Marketplaces 2026 | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 8 major marketplaces by Q2 2026; Skills.sh, Agensi, SkillsMP, ClawHub compared |
| Agensi - Marketplace Landscape 2026 | https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 | SKILL.md cross-platform standard enables write-once-run-anywhere skills |
| Agensi - Claude Code Plugin Guide | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Step-by-step guide to the official Claude Code plugin marketplace |
| Agensi - How Skill Marketplaces Work | https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work | Developer's guide to marketplace mechanics and install flows |
| digitalapplied - Marketplaces Discovery | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | Discovery and distribution patterns for agent skill marketplaces 2026 |
| KDnuggets - Top 5 Skill Marketplaces | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Ranked breakdown of top agent skill marketplaces with use-case guidance |
| JFrog - Agent Skills Security | https://jfrog.com/blog/agent-skills-new-ai-packages/ | "Agent Skills are the New Packages of AI" - ToxicSkills and ClawHavoc incidents |
| AIToolly - Secure Skill Registry | https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm | agent-skills: new verified skill registry with security scanning |
| knightli.com - Marketplace Guide | https://knightli.com/en/2026/05/23/claude-plugins-official-claude-code-plugin-directory/ | Consumer guide: what you can install, how to install it, what to watch out for |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community-curated directory: 21,600+ skills, 9,900+ MCP servers, 2,500+ marketplaces |
| Composio - Best Plugins 2026 | https://composio.dev/content/top-claude-code-plugins | Official, MCP, LSP, Design, and Workflow picks for Claude Code plugins |
| ice-ice-bear.github.io | https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/ | Early deep-dive on the Claude Code plugin marketplace architecture (April 3) |
| Pasquale Pillitteri - May 2026 Release Notes | https://pasqualepillitteri.it/en/news/2223/claude-code-may-2026-release-notes-radio-plugin-marketplace | Comprehensive coverage of the May 2026 Claude Code release including plugin marketplace |
| claudepluginhub.com | https://www.claudepluginhub.com/marketplaces/anthropics-claude-plugins-official | Community tracking page for the official Anthropic plugin marketplace |
| 2389 Research Plugin Marketplace | https://skills.2389.ai/ | Open-source plugin marketplace: npx skills add or /plugin marketplace add |
| rdmgator12/awesome-claude-plugins (GitHub) | https://github.com/rdmgator12/awesome-claude-plugins | Community-maintained directory of 132 plugin bundles; not affiliated with Anthropic |
| chirag2653/public-claude-code-plugins (GitHub) | https://github.com/chirag2653/public-claude-code-plugins | Shareable Claude Code plugin marketplace with skills, hooks, and MCP servers |
| CassianFlorin/skill-hub (GitHub) | https://github.com/CassianFlorin/skill-hub | "The package manager for AI agent skills. Install, update, sync, and govern skills across coding agents." |
| pakxdev/pakx (GitHub) | https://github.com/pakxdev/pakx | Package manager for AI agent components: skills, MCP servers, subagents, prompts, commands, hooks |
| linny006/agent-skill-registry (GitHub) | https://github.com/linny006/agent-skill-registry | "A package registry for AI agent skills — discover, version, and install across any coding agent" |
| nikships/skills-registry (GitHub) | https://github.com/anand-92/skills-registry | Personal GitHub registry for AI Agent Skills; one repo, every agent, every device |
| openmodelsrun/mcp (GitHub) | https://github.com/openmodelsrun/mcp | Open-source registry of MCP servers with structured metadata and install configs |
| zavora-ai/mcp-registry (GitHub) | https://github.com/zavora-ai/mcp-registry | MCP Registry for ADK-Rust Enterprise: server registration, tool discovery, allow-lists, health, audit |
| skills-for-humanity (GitHub) | https://github.com/human-avatar/skills-for-humanity | 171 structured reasoning skills for Claude Code (Show HN, 28 pts) |

---

## Stats Block

```
├─ 🟠 Reddit: 1 thread
├─ 🔵 X: 14 posts │ 559 likes │ 67 reposts
├─ 🟡 HN: 29 stories │ 3,915 points │ 1,989 comments
├─ 🦋 Bluesky: 12 posts │ 92 likes │ 6 reposts
├─ 🌐 Web: 28 pages (19 engine + 9 supplemental)
└─ 🗣️ Top voices: @ClaudeCodeLog, @RituWithAI, @appwrite, @jefferyharrell.bsky.social │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 results** - yt-dlp returned 0 on the full query string; ScrapeCreators returned HTTP 402. Topic likely has video content under shorter queries like "claude code plugins" but was not captured. Approximate coverage loss: significant for tutorial/demo content.
- **TikTok: 0 results** - ScrapeCreators 402 across all subqueries. No TikTok coverage.
- **Instagram: 0 reels** - ScrapeCreators v2 reels endpoint 500'd on multi-token query (documented issue per engine output).
- **Reddit: 1 thread only** - Public Reddit API returned 403 for the full query string. ScrapeCreators backup also 402'd. Subreddit RSS feeds returned 0 hits. Only one post captured via global search fallback. True Reddit coverage for r/ClaudeAI, r/ChatGPTCoding, r/LocalLLaMA on this topic is likely 10x+ what was captured.
- **Polymarket: 0 markets** - No prediction markets on plugin ecosystems or MCP adoption.
- **GitHub: 0 results** - No GitHub token available and `gh` CLI not authenticated. GitHub data came through web grounding results only.
- **Noise:** Several HN items (AI agent bankrupting operator, CAPTCHA detection, Verizon billing agent) are general AI agent stories unrelated to the skill/plugin ecosystem specifically. Included in HN table for completeness per spec.
- **Freshness:** Engine noted only 26 of 75 dated items are from the last 7 days; majority of items from May 2026. Estimated coverage: ~60-70% of available signal given Reddit/YouTube/TikTok gaps.

---

## Key Quotes

> "Skills are the new plugins. Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins. Every AI agent framework now has a marketplace of community-built skills you can install with one command. One command. That skill now runs inside your AI agent. With access to everything your agent can do." — [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) on X

> "The marketplace is real and official → anthropics/claude-plugins-official. Under the hood it's literally one SKILL.md + 5 reference markdown files." — [@artyomx](https://x.com/artyomx/status/2065925946717168096) on X

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "Claude Code wants CLAUDE.md. Codex wants AGENTS.md. Cursor wants .cursorrules." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) on Reddit

> "$40,000/month from Claude skills — no proof, no screenshot, no client, nothing. Half the install commands don't even work. Skills are real. MCP servers are real. The $40K is a number he typed to get follows." — [@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385) on X

> "Four major agent communication protocols published in 18 months — MCP has dominated tool-calling: Linux Foundation confirmed 10,000+ servers." — [@NewsTongueX](https://x.com/NewsTongueX/status/2066220600650043864) on X

> "I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky

> "Agent Skills are the New Packages of AI: It's Time to Manage Them Securely." — [JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/)
