# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-12
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 12 threads | — upvotes, — comments | All from r/ClaudeCode |
| X/Twitter | 21 posts | 605 likes, 149 reposts | Top: @ClaudeCodeLog, @chenzeling4 |
| Hacker News | 36 stories | 2,657 points, 1,480 comments | High-signal dev discussion |
| Bluesky | 13 posts | 93 likes, 6 reposts | Developer community |
| Web | 16 pages | — | GitHub repos, docs, blog posts |
| Web (supplemental) | 10 pages | — | via WebSearch |

---

## Synthesized Findings

### 1. Anthropic's Official Plugin Marketplace Quietly Landed

The biggest news of the last 30 days is Anthropic shipping `claude-plugins-official`, an official plugin directory for Claude Code. As [@chenzeling4](https://x.com/chenzeling4/status/2065071059418964069) noted on June 11: "Anthropic quietly shipped an official plugin directory for Claude Code. claude-plugins-official has both internal Anthropic-built plugins and community-submitted ones. Install with `/plugin install name@claude-plugins-official` or browse in the Discover tab. Each plugin can bundle MCP servers, slash commands, agent definitions, and skills." Per [Clarista's complete guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide), the official marketplace now lists 55+ curated plugins with 72+ more from community sources like wshobson/agents. The [Claude Marketplaces directory](https://claudemarketplaces.com/) tracks the broader ecosystem at 20,300+ skills, 2,500+ plugin sources, and 8,700+ MCP servers as of mid-2026.

Discussed on: X, Web, Hacker News

### 2. Plugin Architecture Is Maturing: CLI Tooling, Auto-Loading, and Mid-Session Reloads

Tooling for managing plugins improved significantly in recent weeks. [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2060460312457810182) documented CLI version 2.1.157 adding `claude plugin init <name>` to scaffold new plugins in `.claude/skills`, plus autocomplete for `/plugin` arguments. A subsequent release (2.1.152) added `/reload-skills` to re-scan skill directories without restarting the session, and the `pluginSuggestionMarketplaces` managed setting for org admins to allowlist approved marketplaces. Per [Simon Carter's breakdown](https://simoncarter.ai/posts/claude-code-now-auto-loads-plugins-from-local-directories-no-marketplace-require/), plugins now auto-load from local directories without a marketplace dependency - removing a major friction point for team distribution. [Releasebot's June changelog](https://releasebot.io/updates/anthropic/claude-code) also notes plugins can declare `defaultEnabled: false` so they install silently until explicitly enabled.

Discussed on: X, Web, Bluesky

### 3. The 5-Layer Mental Model Is Becoming the Community Consensus

Multiple high-signal sources across HN, Bluesky, and the web are converging on the same architectural description of Claude Code's extension surface. The canonical stack: `CLAUDE.md → hooks → skills → plugins → MCP servers`. French developer [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) put it plainly: "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet." The [arps18 HN post](https://arps18.github.io/posts/claude-code-mastery/) "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs" hit 451 points and 254 comments - by far the most engaged content in this window. [Alexop.dev's full-stack explainer](https://alexop.dev/posts/understanding-claude-code-full-stack/) and [Duet's Skills vs MCP guide](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills) both formalize this model: Skills teach Claude how, MCP gives Claude access.

Discussed on: Hacker News, Bluesky, Web, X

### 4. Community Registries and Skill Marketplaces Are Proliferating

Third-party registries are appearing across GitHub. The HN submission [CodeGuilds](https://codeguilds.dev) (June 1, 3pts) bills itself as "a community registry for Claude Code (skills, agents, MCP servers)." On the skills-distribution side, [SkillsForAgents](https://github.com/swissmarley/SkillsForAgents) offers "a distributable agent-skill marketplace for Claude Code, Codex CLI, OpenCode, Hermes - one-line installer + native Claude Code plugin support" (MIT licensed). [SkillForge](https://github.com/yvzhou1111/skillforge) is described as "an intelligent Agent-Skill dependency butler: discover, security-audit, quality-grade, and install Agent Skills into any AI coding agent." From Bluesky, [ECC was announced](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) as "63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex - a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." Personal plugin marketplace repos (chirag2653, Lizo-RoadTown, jasonm4130) are also proliferating on GitHub, suggesting developers are self-hosting their own distribution points.

Discussed on: Hacker News, Bluesky, Web, Reddit

### 5. MCP Ecosystem: Registries, Security, and Enterprise Integration

The MCP ecosystem is expanding rapidly beyond individual servers into structured registries and enterprise tooling. [Kong Inc's guide to MCP Registries](https://konghq.com/blog/learning-center/what-is-an-mcp-registry) defines MCP registries as centralized directories with structured metadata, tool discovery, allow-lists, health checks, and audit trails - analogous to npm or PyPI for agent tools. [Google Cloud](https://docs.cloud.google.com/agent-registry/use-agentregistry-mcp) launched an Agent Registry MCP server enabling agents to dynamically discover other agents and MCP servers in cloud environments. [Microsoft Azure Foundry](https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/model-context-protocol) added documentation for connecting agents to MCP server endpoints. On the security side, [@ScottAperionCTO](https://x.com/ScottAperionCTO/status/2065125218859765999) announced Aperion Shield v0.9: "a free, open-source local guardrail that operates between your AI coding agent (Cursor, Claude Code, Cline, Windsurf, Zed, etc.) and the tools it can access." [AgentSploit](https://github.com/agentsploit/agentsploit) was Show HN'd as a "Burp Suite for AI Agents and MCP Servers" (9 pts, June 9).

Discussed on: Hacker News, X, Web, Bluesky

### 6. Skill Use in the Wild: Quirky Community Builds and Real Workflows

The community is shipping weird, creative, practical skill use cases. From [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1u3jlo0/i_gave_claude_code_a_lazy_senior_dev_mode_and_it/): "I gave Claude Code a 'lazy senior dev' mode and it writes like 6x less code. I built Ponytail. It's a skill that channels the senior dev everyone knows... Before it writes anything it walks a little ladder. Does this even need to be coded?" [@m_stefanczyk](https://x.com/m_stefanczyk/status/2054969718264533016) praised the `dev-browser` plugin as "the best upgrade to my Claude Code workflow in recent weeks - it gives Claude real eyes, it drives the browser, tests what it just wrote, verifies it actually works." [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) captured the community's imagination with: "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." Dynamic Workflows (the Anthropic blog post) hit 200 pts/135 comments on HN - suggesting agentic workflow orchestration is the next major layer developers want to understand.

Discussed on: Reddit, Bluesky, X, Hacker News

### 7. Scam Content and Hype Are Polluting the Skills Ecosystem

The ecosystem is attracting low-quality get-rich-quick content. [@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385) called it out directly: "'$40,000/month from Claude skills' - no proof, no screenshot, no client, nothing. Half the install commands don't even work. /plugin marketplace add isn't real Claude Code syntax. Skills are real. MCP servers are real. The $40K is a number he typed to get follows. The only thing being printed here is engagement." Meanwhile, [@beamnxw](https://x.com/beamnxw/status/2061376802652598305) posted "How to Build Claude Code Operating Systems in 3 Hours and Sell Them for $15K/Month. FULL GUIDE" - 138 likes, 18 reposts. This pattern (authentic primitives + exaggerated monetization claims) is a consistent noise pattern in the ecosystem right now.

Discussed on: X

### 8. Agent Discovery and Distribution Infrastructure Is a New Frontier

Beyond Claude-specific tools, a broader agent-discovery infrastructure is taking shape. [AI Agent Discovery via DNS](https://dns-aid.org/) was submitted to HN (June 1). [A GitOps-style registry for AI agent Workflows, Skills and MCP servers](https://github.com/Friz-zy/ai-capability-registry) (HN, 4pts/1cmt). [VAEN - Package and import portable AI coding-agent Harnesses](https://github.com/sjhalani7/vaen) (HN, 8pts). The [openmodelsrun/mcp](https://github.com/openmodelsrun/mcp) repo describes itself as "an open-source registry of MCP servers with structured metadata, tools, resources and install configs." [@PedroChermont](https://x.com/PedroChermont/status/2065102721158468053) described using Claude Code as an orchestration hub: "Claude Code como centro de tudo. Conectores p fontes de dados via MCP servers (CVM, SEC, BigQuery). Backend GCP Cloud Run." The [Skill Flare Discover](https://github.com/Edward0l1/skill-flare-discover) project ("Best AI Agent Skill Finder 2026 - Multi-Registry Install & Security Labels") shows the community is building cross-registry discovery tooling.

Discussed on: Hacker News, X, Web

---

## Cross-Source Patterns

**Pattern 1: The official marketplace arrival shifts the distribution model**
- Platforms: X, Web, Bluesky, Hacker News
- The June 11 announcement of `claude-plugins-official` is the single most-discussed development. Prior to this, distribution was via GitHub repos and informal sharing. The official directory adds centralized discovery, version pinning, and a submission path for third-party developers.
- Key quote: "Anthropic quietly shipped an official plugin directory... They're taking submissions from third-party developers now." - [@chenzeling4](https://x.com/chenzeling4/status/2065071059418964069)

**Pattern 2: "Skills for knowledge, MCP for access" is becoming doctrine**
- Platforms: Web, Bluesky, Hacker News, X
- The Skills vs. MCP distinction - skills teach Claude how to do something, MCP gives it access to external systems - appears consistently across guides, HN submissions, and developer posts. The five-layer model (CLAUDE.md → hooks → skills → plugins → MCP) is the canonical mental model.
- Key quote: "The useful setup has five layers: CLAUDE.md for project rules, MCP servers for external tools/data, skills for reusable workflows, hooks for automation and safety checks, and subagents for isolated research/review work." - [Duet Skills Guide](https://duet.so/guides/claude-code-skills-complete-guide)

**Pattern 3: Security concerns are rising proportionally with adoption**
- Platforms: X, Hacker News
- As the MCP ecosystem grows (2,000+ servers in official registry), prompt injection and MCP server attack vectors are getting dedicated tooling. AgentSploit (Burp Suite for AI agents), Aperion Shield, and Containarium all appeared in the last 30 days.
- Key quote: "Aperion Shield serves as a free, open-source local guardrail that operates between your AI coding agent... and the tools it can access." - [@ScottAperionCTO](https://x.com/ScottAperionCTO/status/2065125218859765999)

**Pattern 4: Monetization hype is growing alongside legitimate skill ecosystems**
- Platforms: X
- The same week that genuine ecosystem development (official marketplace, registry tooling) is announced, get-rich-quick content claiming $15K-$40K/month from Claude skills is also proliferating on X. Community members are calling this out.
- Key quote: "The $40K is a number he typed to get follows. The only thing being printed here is engagement." - [@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeCode | I gave Claude Code a "lazy senior dev" mode and it writes like 6x less code | — | — | "I built Ponytail. It's a skill that channels the senior dev everyone knows." | https://www.reddit.com/r/ClaudeCode/comments/1u3jlo0/ |
| r/ClaudeCode | If you do one thing with Fable 5 access, do this ... | — | — | "I have some local commands, workflows, and skills I lean on regularly but I'm always on the hunt for improvements" | https://www.reddit.com/r/ClaudeCode/comments/1u37glf/ |
| r/ClaudeCode | Fable is really something else | — | — | "Fable is solving problems that Opus simply couldn't. I'm shipping" | https://www.reddit.com/r/ClaudeCode/comments/1u31g9f/ |
| r/ClaudeCode | My hot take: Fable is not worth the press | — | — | "By the end of both, I have hit my Max20 limit" | https://www.reddit.com/r/ClaudeCode/comments/1u3pejp/ |
| r/ClaudeCode | Fable 5 added to the Artificial Analysis Coding Agent Index... barely 1 point ahead of GPT-5.5 ??? | — | — | "Claude Code + Fable 5 (max) takes the lead with a score of 77" | https://www.reddit.com/r/ClaudeCode/comments/1u3lsrq/ |
| r/ClaudeCode | We turned Claude Code's spinner into a live newsfeed and an open ad market | — | — | — | https://www.reddit.com/r/ClaudeCode/comments/1u3r4ut/ |
| r/ClaudeCode | I made Glint: a lightweight app companion that shows what Claude Code is doing | — | — | — | https://www.reddit.com/r/ClaudeCode/comments/1u3rih1/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @chenzeling4 | "Anthropic quietly shipped an official plugin directory for Claude Code" | 1 | 2 | https://x.com/chenzeling4/status/2065071059418964069 |
| @ClaudeCodeLog | "Added claude plugin init <name> to scaffold a new plugin in .claude/skills" | 19 | 1 | https://x.com/ClaudeCodeLog/status/2060460312457810182 |
| @ClaudeCodeLog | "Added /reload-skills command to re-scan skill directories without restarting the session" | 27 | 1 | https://x.com/ClaudeCodeLog/status/2059451400338223550 |
| @sakhil_ai | "13 FREE Claude Courses from Anthropic... Introduction to Agent Skills" | 108 | 73 | https://x.com/sakhil_ai/status/2065250722699259929 |
| @makecrypto4304 | "'$40,000/month from Claude skills' — no proof, no screenshot, no client, nothing" | — | — | https://x.com/makecrypto4304/status/2065266100858708385 |
| @beamnxw | "How to Build Claude Code Operating Systems in 3 Hours and Sell Them for $15K/Month" | 138 | 18 | https://x.com/beamnxw/status/2061376802652598305 |
| @MaryamMiradi | "How AI Engineers Can Use Claude Code to Build Production AI Agents (7-Step roadmap)" | 23 | 1 | https://x.com/MaryamMiradi/status/2065119037961478247 |
| @m_stefanczyk | "Best upgrade to my Claude Code workflow: dev-browser by Sawyer Hood. Plugin gives Claude real eyes" | 3 | 2 | https://x.com/m_stefanczyk/status/2054969718264533016 |
| @ScottAperionCTO | "Aperion Shield v0.9: free open-source guardrail between AI coding agent and MCP tools" | — | — | https://x.com/ScottAperionCTO/status/2065125218859765999 |
| @turnkeyhq | "Architecting Secure Onchain Workflows With AI Skills and MCP Servers" | 14 | 1 | https://x.com/turnkeyhq/status/2065069029375541667 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| shenli3514 | How Claude Code works in large codebases | 248 | 160 | — | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| cdrnsf | A Claude Code and Codex Skill for Deliberate Skill Development | 253 | 50 | — | https://github.com/DrCatHicks/learning-opportunities |
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad |
| nab | Show HN: Boxes.dev: ditch localhost; run Claude Code and Codex in the cloud | 104 | 79 | — | https://boxes.dev |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| sjhalani7 | Show HN: VAEN – Package and import portable AI coding-agent Harnesses | 8 | 3 | — | https://github.com/sjhalani7/vaen |
| davidvgilmore | Show HN: Rayline routes Claude Code subagents to on-device and cheaper models | 11 | 9 | — | https://rayline.ai/ |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| di_desle | AgentSploit – Burp Suite for AI Agents and MCP Servers | 3 | — | — | https://github.com/agentsploit/agentsploit |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | — | — | https://github.com/OpenYabby/OpenYabby |
| krzysieknowik1 | Would you pay once (no subscription) for prebuilt Claude Code agents? | 3 | 3 | — | https://ai-specialists.vercel.app |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods... Game of Thrones-themed total conversion where all my PR's are in-character" | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | "I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @franckparienti.bsky.social | "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers" | 1 | https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o |
| @camilleroux.com | "Mon top 13 des skills et plugins Claude Code qui ont marqué 2026" | 8 | https://bsky.app/profile/camilleroux.com/post/3mm74d7ixmm2p |
| @brunopedro.com | "42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins" | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex" | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @mengli512.bsky.social | "Two MCP plugins give Claude Code a powerful brain: one for code search, one for context compression" | 3 | https://bsky.app/profile/mengli512.bsky.social/post/3mmefth45ss2p |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Marketplaces | https://claudemarketplaces.com/ | Community directory: 20,300+ skills, 8,700+ MCP servers tracked |
| Anthropic Official Plugin Marketplace | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Official marketplace.json with 55+ vetted plugins |
| Claude Code Docs - Skills | https://code.claude.com/docs/en/skills | Official skill extension documentation |
| Claude Code Docs - MCP | https://code.claude.com/docs/en/mcp | Official MCP connection documentation |
| Claude Code Docs - Plugins | https://code.claude.com/docs/en/discover-plugins | Official plugin marketplace discovery docs |
| Shrikar Archak | https://shrikar.com/writing/claude-code-skills-subagents-hooks-plugins-mcp | "A mental model that finally sticks" - axis-change explanation |
| DEV Community | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Decision framework: lightest-first extension selection |
| AI-Trove | https://ai-trove.com/en/claude-plugins-official/what-are-claude-code-plugins | Comprehensive skills/agents/hooks/MCP/LSP explainer |
| ClaudeFolio | https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers | Custom slash commands and MCP servers reference |
| Simon Carter | https://simoncarter.ai/posts/claude-code-now-auto-loads-plugins-from-local-directories-no-marketplace-require/ | Local plugin auto-loading, no marketplace required |
| Google Cloud Docs | https://docs.cloud.google.com/agent-registry/use-agentregistry-mcp | Agent Registry MCP server for dynamic agent discovery |
| Microsoft Azure Foundry | https://learn.microsoft.com/en-us/azure/foundry/agents/how-to/tools/model-context-protocol | Enterprise MCP server endpoint documentation |
| Kong Inc. | https://konghq.com/blog/learning-center/what-is-an-mcp-registry | What is an MCP Registry - centralized AI agent directory |
| SkillsForAgents | https://github.com/swissmarley/SkillsForAgents | MIT-licensed distributable skill marketplace, cross-agent |
| SkillForge | https://github.com/yvzhou1111/skillforge | Security-auditing skill dependency manager |
| openmodelsrun/mcp | https://github.com/openmodelsrun/mcp | Open-source structured MCP server registry |
| Alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full-stack: MCP, Skills, Subagents, Hooks explained |
| Duet | https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills | Skills vs MCP decision framework |
| Boring Bot | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Production multi-agent workflow architecture |

---

## Stats Block

```
├─ 🟠 Reddit: 12 threads
├─ 🔵 X: 21 posts │ 605 likes │ 149 reposts
├─ 🟢 HN: 36 stories │ 2,657 points │ 1,480 comments
├─ 🦋 Bluesky: 13 posts │ 93 likes │ 6 reposts
├─ 🌐 Web: 16 pages (engine) + 10 pages (supplemental)
└─ 🗣️ Top voices: @ClaudeCodeLog, @chenzeling4, @makecrypto4304 │ r/ClaudeCode, @jefferyharrell.bsky.social
```

---

## Data Gaps

- **YouTube:** 0 results returned. SC API returned 402 (payment required) on all retries. YouTube would likely contain tutorial/walkthrough content for skills and MCP server setup. Estimated ~15-20% additional coverage missing.
- **TikTok / Instagram:** 0 results. SC 402 errors across the board. These platforms likely have surface-level tutorials and viral clips but low-signal for this developer-focused topic.
- **Reddit keyless tier:** Public Reddit search API returned 403 (forbidden) on full-text search. Engine fell back to RSS/subreddit listing, which yielded only r/ClaudeCode items (12 threads). r/LocalLLaMA, r/ChatGPTCoding, r/AI_Agents may have relevant discussion not captured. Estimated ~20% Reddit coverage.
- **GitHub (no token):** No GITHUB_TOKEN available. GitHub project-mode search was unavailable. Many skill/plugin repos linked from HN and Web results have no star/activity data beyond what the grounding search returned.
- **Polymarket:** 0 relevant markets - expected, as this is a developer tooling topic with no obvious prediction market angle.
- **Freshness note:** Only 32 of 98 dated items are from the last 7 days per engine report. The period May 13-31 is well-covered; June 1-12 data is thinner on Reddit and Bluesky.
- **Approximate coverage:** ~75% of HN/X signal, ~50% of Reddit signal, ~80% of Web signal, 0% YouTube/TikTok/Instagram.

---

## Key Quotes

> "Anthropic quietly shipped an official plugin directory for Claude Code. claude-plugins-official has both internal Anthropic-built plugins and community-submitted ones." — [@chenzeling4](https://x.com/chenzeling4/status/2065071059418964069) on X

> "'$40,000/month from Claude skills' — no proof, no screenshot, no client, nothing. Half the install commands don't even work... Skills are real. MCP servers are real. The $40K is a number he typed to get follows." — [@makecrypto4304](https://x.com/makecrypto4304/status/2065266100858708385) on X

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "le harness de claude code en 5 couches: CLAUDE.md → hooks → skills → plugins → MCP servers. le contre-intuitif: passer de sonnet à opus apporte moins que d'activer ces 5 couches sur sonnet." — [@franckparienti.bsky.social](https://bsky.app/profile/franckparienti.bsky.social/post/3mma2blboxt2o) on Bluesky

> "I gave Claude Code a 'lazy senior dev' mode and it writes like 6x less code. I built Ponytail. It's a skill that channels the senior dev everyone knows. Long ponytail, oval glasses, seen it all. Says nothing, writes one line, it works." — [r/ClaudeCode](https://www.reddit.com/r/ClaudeCode/comments/1u3jlo0/) on Reddit

> "Added /reload-skills command to re-scan skill directories without restarting the session... Added pluginSuggestionMarketplaces managed setting: admins can allowlist org marketplaces whose plugins may be suggested via context-aware tips" — [@ClaudeCodeLog](https://x.com/ClaudeCodeLog/status/2059451400338223550) on X (CLI 2.1.152 changelog)

> "Aperion Shield v0.9: addressing a critical gap in local AI security: the potential for MCP server attacks on your agent. Shield serves as a free, open-source local guardrail that operates between your AI coding agent (Cursor, Claude Code, Cline, Windsurf, Zed, etc.) and the tools it can access." — [@ScottAperionCTO](https://x.com/ScottAperionCTO/status/2065125218859765999) on X

> "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — a free, MIT-licensed system that replaces the pile of paid plugins developers duct-tape together." — [@webuyhousesusa.bsky.social](https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c) on Bluesky

> "I'm not absolutely 100% positive but I'm pretty confident that I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." — [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22) on Bluesky
