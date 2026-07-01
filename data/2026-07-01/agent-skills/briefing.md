# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-01
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 5 threads | 5 upvotes, 2 comments | All from r/ClaudeAI |
| X/Twitter | 18 posts | 1,745 likes, 257 reposts | Top voices: @zeuuss_01, @crptAtlas, @Suryanshti777 |
| Hacker News | 10 stories | 3,362 points, 1,699 comments | |
| Bluesky | 13 posts | 38 likes, 6 reposts | Mix of developer builders and security researchers |
| GitHub | 20 items | 1,375 reactions, 618 comments | Issues/PRs from anthropics/claude-code, anthropics/claude-ai-mcp |
| Web | 26 pages | — | 9 via engine (Exa), 17 via WebSearch supplement |

---

## Synthesized Findings

### 1. The `claude-code-setup` Plugin: Anthropic's Biggest Viral Moment This Week

The highest-engagement signal in the corpus is a wave of X posts promoting `claude-code-setup`, described as an official Anthropic plugin that auto-scans a project and recommends hooks, skills, MCP servers, subagents, and automations - then sets them up step-by-step. [@crptAtlas](https://x.com/crptAtlas/status/2072030454505726286) (84 likes, 11 reposts) framed it as "You're running Claude Code at half its power" with the install command `/plugin install claude-code-setup@claude-plugins-official`. [@Suryanshti777](https://x.com/Suryanshti777/status/2072207964975591573) (81 likes, 24 reposts) called it the moment Claude Code goes "from 'pretty good' into an actual AI dev environment." The narrative landing on both X and Bluesky is consistent: most users run Claude Code vanilla and are leaving significant capability on the table.

Cross-source: X, Bluesky ([@adtmag.bsky.social](https://bsky.app/profile/adtmag.bsky.social/post/3mpj64gc2lh2o) covered Spring Tools 5.2.0's embedded MCP plugin with a similar "just plug in" message)

### 2. Skills as Durable IP Across Swappable Agents

The most analytically sharp post in the corpus is [@closermethod](https://x.com/closermethod/status/2072084641272807449): "the leverage isn't claude code or cursor or codex. those swap out every few months. it's the skills and files you write once that make any of them work like they already know your context. i built dozens of sites and a stack of mcp servers this way with no cs background." [@AdelDeveloperX](https://x.com/AdelDeveloperX/status/2072034395272208884) echoed this: "The real upgrade isn't Claude Code itself - it's the ecosystem around it. Once you have plugins, MCP servers, hooks, and specialized agents working together, your workflow becomes far more scalable."

This framing is confirmed by independent web content. [Netresearch's claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) explicitly targets the portable-skills use case: skills described as "open standard at agentskills.io - portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents." The [Skillselion State of AI Agent Skills 2026](https://skillselion.com/state-of-ai-agent-skills-2026) report counts 84,373 coding-agent tools (65,629 agent skills, 7,842 MCP servers, 8,517 marketplaces) with 116M combined installs - the ecosystem is no longer speculative.

Cross-source: X, Web (Skillselion, Netresearch), Bluesky

### 3. Taxonomy Confusion Is the #1 Developer Pain Point

A cluster of blog posts published in June 2026 all tackle the same problem: developers don't know when to use a skill vs. a plugin vs. an MCP server vs. a connector. [MCSA Guru](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) summarizes the layering: "Skills teach Claude how to do something. MCP servers give Claude access to something. Plugins bundle both." [Tygart Media](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) and [maketocreate.com](https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/) both note that existing explainer content leaves readers knowing what each thing is but still unable to decide what to actually build. The [DEV Community post by rapls](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) provides a practical decision framework: "lightest first" (skill > CLI > plugin > MCP server), touching on context budget and security tradeoffs.

Cross-source: Web, X

### 4. MCP Marketplace Explosion and Registry Wars

The MCP server ecosystem grew from an official registry of ~800 servers in April 2026 to an estimated 13,000+ servers counting community and private deployments. The [TrueFoundry registry comparison](https://www.truefoundry.com/blog/best-mcp-registries) identifies four key players: mcp.so (20,222 listed), smithery.ai (7,000+ with CLI installer and hosted remote option), glama.ai/mcp, and punkpeye/awesome-mcp-servers. [ExplainX.ai counts 56,000+ servers on LobeHub](https://www.explainx.ai/blog/top-10-mcp-server-directories-2026). The official Anthropic/GitHub/Microsoft-backed registry reached 8,400+ verified servers by May 2026.

For Claude Code specifically, [claudemarketplaces.com](https://claudemarketplaces.com/) tracks 21,600+ skills, 2,500+ marketplaces, and 12,500+ MCP servers, updated daily. [jeremylongshore's open-source marketplace](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) aggregates 425 plugins, 2,810 skills, and 200 agents with a `ccpi` CLI package manager. On HN, [CodeGuilds](https://codeguilds.dev) was submitted as a community registry for skills, agents, and MCP servers targeting Claude Code specifically.

[@nidhisinghattri](https://x.com/nidhisinghattri/status/2072190325410636141) (26 likes) offered a practitioner's pick: "here are the 4 mcp servers that i highly recommend - github, context7, obsidian, searxng - these would work with any agent: codex, claude code, cursor etc."

Cross-source: X, HN, Web, Bluesky

### 5. X (Twitter) Ships Hosted MCP Servers - Walled Garden Opens

A notable development on June 30: X/Twitter launched native hosted MCP servers (api.x.com/mcp and docs.x.com/mcp), giving any MCP client direct access to post search, user lookups, trends, bookmarks, and drafting. [@Vladic_ETH](https://x.com/Vladic_ETH/status/2071974904665157682) (15 likes): "X shipped a hosted MCP. The wall around X just came down for agents. Until now an agent could search the web, but X stayed closed." [@TraffAlex](https://x.com/TraffAlex/status/2071981949741142119) provided a copy-paste setup guide (JSON config + one browser login). [@Millionareum](https://x.com/Millionareum/status/2072144912133595261) noted that Grok Build, Cursor, Claude, and VS Code can now connect natively.

Also notable per Bluesky trending: AWS released official MCP servers, skills, and plugins enabling AI agents to integrate with cloud infrastructure, per [@probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f).

Cross-source: X, Bluesky

### 6. MCP Security Is the Ecosystem's Unsolved Problem

The security thread is the most active cluster on Bluesky and drew 5+ reposts and replies. [@elizabethfue12.bsky.social](https://bsky.app/profile/elizabethfue12.bsky.social/post/3mpbvulvgc32j) (4 likes, 5 replies): "A fake bug report can hijack your coding agent. A public Sentry key lets someone plant a fake error. Your agent reads it via MCP and runs the attacker's command. Claude Code, Cursor, Codex. 85% success." [@pondero-ai.bsky.social](https://bsky.app/profile/pondero-ai.bsky.social/post/3mom7pgh3u42b) (4 likes, 9 replies) confirmed the vector: "One click and Claude Code or Cursor can auto-run attacker code via MCP, no further interaction needed." The [@ryandaaldo.bsky.social v0.2.0 mcpfrisk tool](https://bsky.app/profile/ryandaaldo.bsky.social/post/3mpfmsogaof2s) (2 likes, 1 repost) directly responds: it scans all installed MCP servers across Claude Desktop/Cursor/VS Code at once, adds --check to catch rug-pulls, and gates CI with a GitHub Action.

The biggest HN story in the corpus ([2,101 pts, 608 comments](https://thereallo.dev/blog/claude-code-prompt-steganography)) was about Claude Code steganographically marking requests - not directly MCP-related, but fits the broader "hidden manipulation in agent infrastructure" anxiety.

Version pinning is the unsexy companion problem. [@TheoWtmn](https://x.com/TheoWtmn/status/2071944565058068683): "MCP servers update frequently. Your project A uses v2.1, project B uses v1.8. Claude Code just runs whatever the config file points at. No version pinning, no visibility into what changed."

Cross-source: Bluesky, X, HN

### 7. Academic Infrastructure: Skilldex and Formal Skill Package Management

An April 2026 arXiv paper ([Skilldex, 2604.16911](https://arxiv.org/abs/2604.16911)) proposes a formal package manager and registry for agent skill packages with hierarchical scope-based distribution (global, shared, project scopes). Key contributions: compiler-style format conformance scoring against Anthropic's skill spec (line-level diagnostics on description specificity, frontmatter validity, structural adherence) and a "skillset" abstraction for bundling related skills with shared context. Implemented as a TypeScript CLI (`skillpm`/`spm`) with Hono/Supabase backend. Live at [skilldex-web.vercel.app](https://skilldex-web.vercel.app/). The [DataArcTech survey](https://github.com/DataArcTech/Awesome-Agent-Skill-Papers) tracks the broader agent skills research landscape.

This represents formalization pressure: the ecosystem is big enough that academia is now proposing npm-grade tooling for skill governance.

Cross-source: Web (arXiv), GitHub

### 8. Enterprise Governance Enters the MCP Stack

Enterprise players are building control-plane layers above the raw MCP protocol. [JFrog's MCP Registry](https://jfrog.com/ai-catalog/mcp-registry/) positions as a "single source of truth for all your MCP servers" with governance and auditability. [Kong's MCP Server Registry](https://konghq.com/products/mcp-registry) adds dynamic tool discovery and access control. [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) is an open-source enterprise gateway with OAuth, Keycloak/Entra integration. [Microsoft Learn](https://learn.microsoft.com/en-us/azure/foundry/mcp/build-your-own-mcp-server) published a guide for building and registering MCP servers in Azure Foundry.

The [SkillHub fork (csxchls/skillhub)](https://github.com/csxchls/skillhub) demonstrates self-hosted enterprise skill registries with RBAC, audit logs, and on-premise deployment (Docker/Kubernetes).

Cross-source: Web, GitHub

### 9. Skills as Content Pipelines: The @zeuuss_01 Use Case

The highest-engagement creator in the X corpus is [@zeuuss_01](https://x.com/zeuuss_01) (215 + 951 + 181 likes across three posts), who documents Claude Code being used as a content pipeline for faceless YouTube/gaming channels. The agentic angle is skill-stacking: "THESE 5 SKILLS TURN HERMES AGENT INTO A SELF-RUNNING POWERHOUSE" (181 likes) walks through specific community skills from the ecosystem (ANTHROPIC-CYBERSECURITY-SKILLS with 4K stars, etc.) dropped into `~/.hermes/skills/`. This use case - skills as productized, community-curated capabilities for non-developer operators - is the clearest consumer-facing signal in the corpus.

Cross-source: X

### 10. Comfy MCP and Domain-Specific Integrations

[Bluesky coverage from Gigazine](https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22) (7 likes) highlights "Comfy MCP" - an MCP server enabling Claude Code agents to drive ComfyUI image and video generation via Comfy Cloud. This pattern (domain-specific MCP adapters bridging AI coding agents to creative/hardware tools) also appears in [@panroboticsxyz](https://x.com/panroboticsxyz/status/2071935908610216374): embedding MCP servers in Raspberry Pis and Nvidia Jetsons to give AI agents real-time access to robot joints, sensors, and navigation controllers. Both extend the MCP-as-universal-adapter concept to physical and creative infrastructure.

Cross-source: Bluesky, X

---

## Cross-Source Patterns

**Pattern 1: "The ecosystem is the real product"**
- Appeared on: X, Bluesky, Web
- Signal: Multiple independent voices converge on the same insight - Claude Code (and Cursor, Codex, etc.) are becoming interchangeable; the durable value is in the skills and MCP server stack you assemble around them.
- Key quotes: @closermethod: "the tools were interchangeable. the files i kept were not." / @AdelDeveloperX: "The real upgrade isn't Claude Code itself - it's the ecosystem around it."

**Pattern 2: MCP prompt injection as the ecosystem's shadow threat**
- Appeared on: Bluesky, X, HN
- Signal: Three independent researchers documented the same attack vector (fake error/bug report planting in public integrations → MCP-mediated code execution). 85% success rate cited. Community-built audit tooling (mcpfrisk) already responding.
- Key quotes: @elizabethfue12.bsky.social: "Claude Code, Cursor, Codex. 85% success." / @pondero-ai.bsky.social: "One click and Claude Code or Cursor can auto-run attacker code via MCP, no further interaction needed."

**Pattern 3: Marketplace fragmentation is a solvable problem (and multiple parties are solving it)**
- Appeared on: HN, Web, GitHub
- Signal: CodeGuilds (community registry), jeremylongshore/claude-code-plugins-plus-skills (CLI package manager), Skilldex (academic package manager spec), tonyhumansai/skill-registry (index.json catalog pattern) all launched in June 2026 within weeks of each other.
- No single registry has won. The npm-for-skills race is active.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | Introducing Claude Sonnet 5, our most agentic Sonnet yet | 1 | 0 | "close to Opus 4.8, at lower prices" | https://www.reddit.com/r/ClaudeAI/comments/1ujwggp/ |
| r/ClaudeAI | Anthropic embedded spyware in Claude Code | 1 | 0 | "covertly transmits whether you are in China...Anthropic attempted to obfuscate this code" | https://www.reddit.com/r/ClaudeAI/comments/1ujila1/ |
| r/ClaudeAI | Claude Mythos 5/Fable 5 export restrictions lifted | 1 | 1 | — | https://www.reddit.com/r/ClaudeAI/comments/1uk5ihe/ |
| r/ClaudeAI | Introducing Claude Sonnet 5 | 1 | 1 | — | https://www.reddit.com/r/ClaudeAI/comments/1ujwgqz/ |
| r/ClaudeAI | Claude thinks he's funny | 1 | 0 | — | https://www.reddit.com/r/ClaudeAI/comments/1uk45b4/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @zeuuss_01 | "A WEB STUDIO CHARGES $35,000 FOR AN ANIMATED SITE. THE SAME BUILD NOW COSTS $12 - CLAUDE CODE WRITES, HIGGSFIELD RENDERS" | 951 | 111 | https://x.com/zeuuss_01/status/2071277843141579246 |
| @zeuuss_01 | "A FACELESS GAMING CHANNEL...ONE OPERATOR NOW SHIPS 4-5 [VIDEOS] - AND HITS 100K IN 90 DAYS WITH CLAUDE CODE" | 215 | 30 | https://x.com/zeuuss_01/status/2071846858620633337 |
| @zeuuss_01 | "THESE 5 SKILLS TURN HERMES AGENT INTO A SELF-RUNNING POWERHOUSE" | 181 | 17 | https://x.com/zeuuss_01/status/2067432401005912575 |
| @crptAtlas | "You're running Claude Code at half its power - there's an official Anthropic plugin that fixes that" | 84 | 11 | https://x.com/crptAtlas/status/2072030454505726286 |
| @Suryanshti777 | "Claude Code feels completely different once you install this [claude-code-setup]" | 81 | 24 | https://x.com/Suryanshti777/status/2072207964975591573 |
| @Tanaypawar27 | "Claude is offering 18 official AI courses with certificates. And it's 100% free" | 73 | 41 | https://x.com/Tanaypawar27/status/2072174941089464730 |
| @Suryanshti777 | "Anthropic in the last 72 hours: launched Claude Tag, shipped Azure collab, dropped Claude Science, launched Sonnet 5" | 21 | 9 | https://x.com/Suryanshti777/status/2072194305389981752 |
| @Vladic_ETH | "X shipped a hosted MCP. The wall around X just came down for agents." | 15 | 0 | https://x.com/Vladic_ETH/status/2071974904665157682 |
| @TraffAlex | "X just opened MCP servers. Any AI agent can now directly search posts, read timelines, manage bookmarks" | 7 | 1 | https://x.com/TraffAlex/status/2071981949741142119 |
| @panroboticsxyz | "We've been exploring embedding MCP servers in hardware like Raspberry Pis and Nvidia Jetsons" | 6 | 1 | https://x.com/panroboticsxyz/status/2071935908610216374 |
| @nidhisinghattri | "here are the 4 mcp servers that i highly recommend - github, context7, obsidian, searxng" | 26 | 2 | https://x.com/nidhisinghattri/status/2072190325410636141 |
| @closermethod | "the leverage isn't claude code or cursor or codex. those swap out every few months. it's the skills and files you write once" | 1 | 0 | https://x.com/closermethod/status/2072084641272807449 |
| @AdelDeveloperX | "The real upgrade isn't Claude Code itself - it's the ecosystem around it" | 0 | 0 | https://x.com/AdelDeveloperX/status/2072034395272208884 |
| @github_update | "AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking" | 8 | 2 | https://x.com/github_update/status/2067259115777507386 |
| @AZERDSQ0329 | "every AI client wants MCP servers configured differently. Different files, different formats. I was copy-pasting JSON between 4 configs" | 1 | 0 | https://x.com/AZERDSQ0329/status/2072206595132444715 |
| @TheoWtmn | "MCP servers update frequently...No version pinning, no visibility into what changed" | 2 | 0 | https://x.com/TheoWtmn/status/2071944565058068683 |
| @Millionareum | "X HANDED OVER ITS OWN KEY TO AI AGENTS. X has launched its hosted MCP servers" | 0 | 0 | https://x.com/Millionareum/status/2072144912133595261 |
| @zeuuss_01 | "AI Builder 101: agent skills, repos, and marketplaces" | 73 | 8 | https://x.com/zeuuss_01/status/2070997719787635066 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kirushik | Claude Code is steganographically marking requests | 2,101 | 608 | — | https://thereallo.dev/blog/claude-code-prompt-steganography |
| engmarketer | I used Claude Code to get a second opinion on my MRI | 559 | 699 | — | https://antoine.fi/mri-analysis-using-claude-code-opus |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| laxmena | My Agent Skill for Test-Driven Development | 251 | 109 | — | https://www.saturnci.com/my-agent-skill-for-test-driven-development.html |
| vincent_s | Claude Code Just Got 5x More Expensive | 51 | 7 | — | https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/ |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 36 | 12 | — | https://news.ycombinator.com/item?id=48546618 |
| ojura | Beware, Claude Code deletes >30 day old transcripts. Anthropic won't fix it | 29 | 38 | — | https://github.com/anthropics/claude-code/issues/62476 |
| BaguettePwnM | I made a free MCP server so your Claude can read Claude/Anthropic news and RAG | 3 | 0 | — | https://claudenews.online |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | 0 | — | https://codeguilds.dev |
| cionut | Show HN: MCP for the ChatGPT Ads API – Query ChatGPT Ads from Claude and Codex | 3 | 1 | — | https://github.com/HYPD-AI/openai-ads-mcp |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @gigazine.net | "Comfy MCP" enables ComfyUI image/video generation automation from Claude Code agents via Comfy Cloud | 7 | https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22 |
| @elizabethfue12.bsky.social | "A fake bug report can hijack your coding agent. A public Sentry key lets someone plant a fake error. Claude Code, Cursor, Codex. 85% success." | 4 | https://bsky.app/profile/elizabethfue12.bsky.social/post/3mpbvulvgc32j |
| @pondero-ai.bsky.social | "That fake Sentry report vector is exactly why the trust prompt is so dangerous. One click and Claude Code or Cursor can auto-run attacker code via MCP" | 4 | https://bsky.app/profile/pondero-ai.bsky.social/post/3mom7pgh3u42b |
| @castropodcasts.bsky.social | "We added an MCP server to castro.fm/mcp - give Claude Code a Castro backup file, then have it graph your listening usage" | 4 | https://bsky.app/profile/castropodcasts.bsky.social/post/3mpgo6l5e6k2h |
| @adtmag.bsky.social | "Spring Tools 5.2.0 adds an experimental Claude Code plugin that gives AI coding assistants live Spring project context through an embedded MCP server" | 3 | https://bsky.app/profile/adtmag.bsky.social/post/3mpj64gc2lh2o |
| @probbrain.bsky.social | "GitHub Trending: AWS releases official MCP servers, skills, and plugins enabling AI agents to build..." | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |
| @ryandaaldo.bsky.social | "v0.2.0: --config scans every MCP server you already have installed (Claude Desktop/Cursor/VS Code), --check catches rug-pulls, GitHub Action gates CI" | 2 | https://bsky.app/profile/ryandaaldo.bsky.social/post/3mpfmsogaof2s |
| @arathunku.com | "MCP works out of the box with opencode/claude code, easier to integrate [memory banks]" | 2 | https://bsky.app/profile/arathunku.com/post/3mpgaz7x46s27 |
| @beckitrue.com | "hooked OpenClaw up to Discord and used Weftly's MCP server from a team channel to get clips from a video. This works from Claude Code, Gemini, LiteLLM, Discord" | 3 | https://bsky.app/profile/beckitrue.com/post/3mp6yolbzfc2m |
| @cloud-native.activitypub.awakari.com | "A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex" | 4 | https://bsky.app/profile/cloud-native.activitypub.awakari.com.ap.brid.gy/post/3moswcszo54h2 |
| @edmundwhite.bsky.social | "I started thinking about how I can write MCP servers for my own data to help with Claude Code: knowledge base, credential store, task manager" | 1 | https://bsky.app/profile/edmundwhite.bsky.social/post/3mpbkkgv3rs2v |
| @firmadev.bsky.social | "Two ways to ask AI about the Firma.dev API: on-site chat or MCP server - connect to Claude, Cursor, or VS Code" | 2 | https://bsky.app/profile/firmadev.bsky.social/post/3mov5ssd4yi2l |
| @everydevai.bsky.social | "Read-only MCP server exposing get_artifact, search_artifacts, get_related, get_summary tools + Claude Code setup details" | 1 | https://bsky.app/profile/everydevai.bsky.social/post/3mpkeoddyln2a |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Skillselion | https://skillselion.com/state-of-ai-agent-skills-2026 | Scale report: 84,373 tools tracked (65,629 skills, 7,842 MCP servers, 8,517 marketplaces), 116M installs |
| ClaudeMarketplaces.com | https://claudemarketplaces.com/ | Directory of 21,600+ skills, 2,500+ marketplaces, 12,500+ MCP servers for Claude Code specifically |
| MCSA Guru | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Taxonomy clarification: skills teach, MCP servers connect, plugins bundle both |
| maketocreate.com | https://maketocreate.com/claude-skills-vs-mcp-servers-when-to-use-each-2026/ | Practitioner guide with opinion on when to use each layer |
| Tygart Media | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Four-way taxonomy: skills, MCP, connectors, plugins |
| DEV Community (rapls) | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | "Lightest first" decision framework for extension type |
| MCSA Guru | https://mcsaguru.com/mcp-vs-plugins-which-to-use-claude-code | MCP server vs plugin decision guide |
| Bloome | https://bloome.im/features/agent-skill-marketplace | Open SKILL.md library: forward a skill card, paste URL, or upload zip to install capabilities |
| Skilldex (arXiv) | https://arxiv.org/abs/2604.16911 | Formal package manager + registry spec: hierarchical scopes, format conformance scoring, skillset bundles |
| Skilldex Web | https://skilldex-web.vercel.app/ | TypeScript CLI implementation with Hono/Supabase backend and MCP server exposing all operations |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; tonsofskills.com with ccpi CLI |
| Netresearch claude-code-marketplace | https://github.com/netresearch/claude-code-marketplace | Cross-agent portable skills, agentskills.io open standard |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | MCP registry landscape: mcp.so (20K+), smithery.ai (7K+), glama.ai, punkpeye list |
| ExplainX.ai | https://www.explainx.ai/blog/top-10-mcp-server-directories-2026 | Top 10 MCP directories; LobeHub largest at 56,000+ servers |
| WorkOS | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | Official registry at 8,400+ verified servers (Anthropic/GitHub/Microsoft backed); 340% YoY MCP growth |
| JFrog MCP Registry | https://jfrog.com/ai-catalog/mcp-registry/ | Enterprise governance plane for MCP server management |
| Kong MCP Registry | https://konghq.com/products/mcp-registry | Enterprise dynamic tool discovery and access control |
| agentic-community/mcp-gateway-registry | https://github.com/agentic-community/mcp-gateway-registry | Open-source enterprise gateway with OAuth + Keycloak/Entra |
| Microsoft Learn | https://learn.microsoft.com/en-us/azure/foundry/mcp/build-your-own-mcp-server | Official guide for building and registering MCP servers in Azure Foundry |
| Agensi.io | https://www.agensi.io/learn/claude-code-plugins-extensions-skills-2026 | Ecosystem overview; 300,000+ monthly developer visits to marketplaces |
| Agensi.io Marketplaces | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 8 major marketplaces by Q2 2026; Skills.sh (Vercel-backed npm-style), ClaudeSkills.info (658+ free) |
| Claude Code Official Docs | https://code.claude.com/docs/en/skills | Anthropic's canonical skills reference |
| QCode | https://www.qcode.cc/claude-code-plugin-marketplace-2026 | Context cost transparency per plugin (v2.1.x+); dependency graph analysis |
| BrightCoding | https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers | Three official marketplace tiers overview |
| tinyhumansai/skill-registry | https://github.com/tinyhumansai/skill-registry | index.json catalog pattern for OpenHuman agent skill registry |
| SkillHub (csxchls fork) | https://github.com/csxchls/skillhub | Self-hosted enterprise skill registry with RBAC and audit logs |

---

## Stats Block

```
├─ 🟠 Reddit: 5 threads │ 5 upvotes │ 2 comments
├─ 🔵 X: 18 posts │ 1,745 likes │ 257 reposts
├─ 🟢 HN: 10 stories │ 3,362 points │ 1,699 comments
├─ 🦋 Bluesky: 13 posts │ 38 likes │ 6 reposts
├─ 🐙 GitHub: 20 items │ 1,375 reactions │ 618 comments
├─ 🌐 Web: 26 pages (9 engine + 17 WebSearch supplement)
└─ 🗣️ Top voices: @zeuuss_01, @crptAtlas, @Suryanshti777 │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube**: 0 videos returned despite three search attempts. yt-dlp encountered rate-limiting; ScrapeCreators returned HTTP 402 errors. Expected coverage of tutorial/demo content is absent. This is a meaningful gap - video tutorials on MCP server setup are likely a major channel for this topic.
- **TikTok**: 0 videos. HTTP 402 errors across all hashtag searches and keyword searches. ScrapeCreators key appears to have hit quota limits.
- **Instagram**: 0 reels. Same HTTP 402 errors.
- **Polymarket**: 0 markets. No prediction markets directly on agent skills or MCP adoption.
- **Reddit**: Only 5 threads, all from r/ClaudeAI with 1 upvote each. The subreddit targeting was correct but the month's Claude Code discussion on Reddit was dominated by model announcements (Sonnet 5, Fable 5/Mythos 5 export restrictions), not skills/plugins directly. r/LocalLLaMA, r/AI_Agents, and r/ChatGPTCoding likely have relevant threads not captured due to rate-limit on Reddit's public backend (ScrapeCreators backup also returned 402).
- **Coverage estimate**: ~65% of intended sources reached. Social (X, HN, Bluesky) is strong. Visual/video coverage absent. Reddit thin.
- **Noisy signals**: Several GitHub items (Trancendos/Tranc3 PRs, firebase-tools, openai/codex rate-limit issues) were tangential to the core topic. The engine's fallback scoring demoted these but they appear in the raw file.

---

## Key Quotes

> "the leverage isn't claude code or cursor or codex. those swap out every few months. it's the skills and files you write once that make any of them work like they already know your context." — [@closermethod](https://x.com/closermethod/status/2072084641272807449) on X

> "You're running Claude Code at half its power - there's an official Anthropic plugin that fixes that for you - it scans your project and tells you exactly which hooks, skills, MCP servers and subagents to switch on" — [@crptAtlas](https://x.com/crptAtlas/status/2072030454505726286) on X (84 likes)

> "The real upgrade isn't Claude Code itself - it's the ecosystem around it. Once you have plugins, MCP servers, hooks, and specialized agents working together, your workflow becomes far more scalable." — [@AdelDeveloperX](https://x.com/AdelDeveloperX/status/2072034395272208884) on X

> "A fake bug report can hijack your coding agent. A public Sentry key lets someone plant a fake error. Your agent reads it via MCP and runs the attacker's command. Claude Code, Cursor, Codex. 85% success." — [@elizabethfue12.bsky.social](https://bsky.app/profile/elizabethfue12.bsky.social/post/3mpbvulvgc32j) on Bluesky

> "X shipped a hosted MCP. The wall around X just came down for agents. Until now an agent could search the web, but X stayed closed." — [@Vladic_ETH](https://x.com/Vladic_ETH/status/2071974904665157682) on X

> "MCP servers update frequently. Your project A uses v2.1, project B uses v1.8. Claude Code just runs whatever the config file points at. No version pinning, no visibility into what changed." — [@TheoWtmn](https://x.com/TheoWtmn/status/2071944565058068683) on X

> "As of 2026, the Skillselion catalog tracks 84,373 AI coding-agent tools - 65,629 agent skills, 7,842 MCP servers and 8,517 marketplaces - with 116M combined installs." — [Skillselion State of AI Agent Skills 2026](https://skillselion.com/state-of-ai-agent-skills-2026)

> "v0.2.0: --config scans every MCP server you already have installed (Claude Desktop/Cursor/VS Code) at once, --url handles remote HTTP servers, --check catches rug-pulls, and a GitHub Action gates your CI." — [@ryandaaldo.bsky.social](https://bsky.app/profile/ryandaaldo.bsky.social/post/3mpfmsogaof2s) on Bluesky

> "hooked OpenClaw up to Discord and used Weftly's MCP server from a team channel to get clips from a video. This works from Claude Code, Gemini, LiteLLM, Discord. Software will become a personal UI with APIs fronted by MCP servers." — [@beckitrue.com](https://bsky.app/profile/beckitrue.com/post/3mp6yolbzfc2m) on Bluesky
