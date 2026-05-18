# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-05-18
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web (blogs, official docs, security reports), YouTube, Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 stories | 870+ points, 460+ comments | Top thread: 816 pts, 427 comments |
| GitHub | 12 repos | 44.1k + 37.9k stars (top 2) | awesome-claude-code, antigravity-awesome-skills |
| Web | 70+ pages | — | Official docs, blogs, security reports, marketplace guides |
| YouTube | 4 videos | — | No transcript access; titles/descriptions only |
| Polymarket | 7 markets | $1.1M+ volume | Claude model performance markets, no skills-specific |
| Reddit | 0 | — | Domain blocked to crawler |
| X/Twitter | 0 | — | Domain blocked to crawler |
| TikTok | 0 | — | No results returned |
| Bluesky | 0 | — | No results returned |

---

## Synthesized Findings

### 1. SKILL.md Becomes the Universal Agent Standard — The Fastest Cross-Vendor Standardization in AI Tooling

In late 2025, Anthropic released the SKILL.md specification — a minimalist open standard (just a directory + YAML-frontmattered markdown file with `name` and `description` fields) — as the package format for AI agent skills. What happened next was described by one observer as "the fastest cross-vendor standardization event in AI tooling."

**Timeline:**
- **Sept 22, 2025:** `anthropics/skills` repo created
- **Oct 2025:** Skills ship in Claude Code
- **Dec 18, 2025:** Official open standard announcement
- **Within 48 hours:** Microsoft (VS Code) and OpenAI (ChatGPT, Codex CLI) both shipped support
- **Jan 20, 2026:** Vercel launched `skills.sh` with 89,753 skills
- **Feb 5, 2026:** AWS Kiro IDE shipped support
- **March 2026:** 32 confirmed adopters

By March 2026, 32 tools support SKILL.md including products from **Anthropic** (Claude Code), **OpenAI** (Codex CLI, ChatGPT), **Microsoft** (VS Code, GitHub Copilot), **Google** (Gemini CLI), **JetBrains** (Junie), **AWS** (Kiro), **Block** (Goose), **Sourcegraph** (Amp), Snowflake, Databricks, ByteDance (TRAE), and Mistral AI.

The key driver: cross-portability. A skill written for Claude Code can be copied into Codex's skills directory and works. Teams can standardize on SKILL.md conventions across every developer's preferred agent. As [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) noted: "the entire spec fits in a document you can read during a coffee break."

**Simon Willison's caveat:** The specification is "quite heavily under-specified," particularly around metadata fields and the experimental `allowed-tools` mechanism. [HN, 816 pts]

**Sources:** [Anthropic Engineering Blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [paperclipped.de open standard](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) · [agensi.io open standard explainer](https://www.agensi.io/learn/agent-skills-open-standard) · [HN: Claude Skills](https://news.ycombinator.com/item?id=45607117)

---

### 2. The Plugin System: Skills Are Content, Plugins Are Distribution

A critical conceptual distinction emerged clearly this cycle: **skills are the content; plugins are the distribution format.** Claude Code now supports a formal plugin system where a plugin is a directory with `.claude-plugin/plugin.json` that can bundle any combination of: skills, custom agents, hooks, MCP servers, LSP servers, background monitors, and executables.

**What a plugin can contain:**

| Component | Purpose |
|-----------|---------|
| `skills/` | SKILL.md files — model-invoked capabilities |
| `agents/` | Custom sub-agent definitions |
| `hooks/hooks.json` | Event handlers (pre-commit, post-tool-use, etc.) |
| `.mcp.json` | MCP server configurations |
| `.lsp.json` | LSP code intelligence |
| `monitors/monitors.json` | Background log/file watchers |
| `bin/` | Executables added to Bash PATH |
| `settings.json` | Default settings when plugin is enabled |

**Ecosystem scale as of May 2026:**
- 6,700+ skills, 9,000+ plugins, 840+ MCP servers across major directories
- SkillsMP alone indexes 1.4M+ skills from GitHub (quality-filtered)

**Plugin lifecycle:**
```
/plugin install → /plugin enable/disable → /reload-plugins
```

The official Anthropic marketplace is pre-configured; submit via `claude.ai/settings/plugins/submit`. Community can build private marketplaces hosted in any GitHub repo.

**Community reaction:** When the plugin system launched (v2.0.12, ~48 points HN), developers immediately noted that "distribution is going to be key" — independent marketplace builders appeared within hours. One developer shipped `claudecodemarketplace.com` the same day, arguing plugin maintainers shouldn't be forced to build their own distribution infrastructure.

**Sources:** [Official Plugin Docs](https://code.claude.com/docs/en/plugins) · [agensi.io plugins vs skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [HN: Customize Claude Code with plugins](https://news.ycombinator.com/item?id=45530150) · [morphllm.com comparison](https://www.morphllm.com/claude-code-plugins-vs-skills) · [claudemarketplaces.com](https://claudemarketplaces.com/)

---

### 3. Progressive Disclosure Architecture: The Technical Innovation Behind Skills

The most architecturally notable aspect of Agent Skills is their **progressive disclosure** loading model, which resolves the fundamental tension between rich context and token cost.

**Three loading levels:**

| Level | When Loaded | Token Cost | Content |
|-------|-------------|------------|---------|
| 1: Metadata | Always (startup) | ~100 tokens/skill | `name` + `description` from YAML frontmatter |
| 2: Instructions | When skill triggered | Under 5k tokens | Full SKILL.md body |
| 3+: Resources | As needed | Effectively unlimited | Bundled files executed via bash (code never enters context) |

The key insight: when Claude runs a script (`fill_form.py`), the script code never loads into the context window — only the output does. This makes scripts far more efficient than Claude generating equivalent code on-the-fly.

This architecture enables "effectively unlimited" bundled content without context penalty. A skill can include comprehensive API documentation, large datasets, extensive examples — only loaded when accessed.

**At the HN "Claude Skills" thread (816 pts, 427 comments):** Simon Willison described this as "maybe a bigger deal than MCP," emphasizing dynamic context assembly. Skeptics countered it's "just prompt engineering" and "a framework to append text to your prompt." The productive middle ground: Skills solve real problems around context window limitations for large projects and enable organizational skill-sharing at scale.

**Sources:** [Official Agent Skills Overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Anthropic Engineering Blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [HN: Claude Skills discussion](https://news.ycombinator.com/item?id=45607117)

---

### 4. The Marketplace Explosion: Competing Platforms, Different Models

The skills marketplace ecosystem has grown from zero to substantial scale in under 6 months. Monthly search volume for agent skills terms has grown **19x** over two years (21,000 → 400,000+ searches/month). Eight major marketplace categories have emerged:

**Major platforms:**

| Platform | Scale | Model | Quality Filter |
|----------|-------|-------|---------------|
| [SkillsMP](https://skillsmp.com/) | 1,419,713+ skills | Free, community | Min 2 GitHub stars |
| [claudemarketplaces.com](https://claudemarketplaces.com/) | Aggregates 2,500+ marketplaces | Free | Aggregator only |
| [tonsofskills.com](https://tonsofskills.com/) | 427 plugins (curated) | Free, curated | Human review |
| [Agensi](https://www.agensi.io/) | Unknown | 80/20 revenue split | Security scanned |
| [skills.sh (Vercel)](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | 89,753 skills | Free | Unknown |
| [LobeHub Skills](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 169,739 skills | Unknown | Unknown |

**Community GitHub repos as distribution:**
- [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills): 37.9k stars, 1,460+ skills, `npx` installer, 200+ contributors with official partnerships (Anthropic, Google, Microsoft, etc.)
- [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code): 44.1k stars, currently reorganizing for scale
- [claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills): 425 plugins, 2,810 skills, `ccpi` CLI package manager

**Key gap identified:** Most marketplaces list skills without quality ranking — alphabetical or category browsing only. "The single biggest gap across the category."

**The App Store analogy:** From [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/): "Every major computing platform eventually gets a marketplace. PCs got software stores. Smartphones got the App Store and Google Play. Browsers got extension stores. AI agents are getting skills marketplaces."

**Sources:** [SkillsMP](https://skillsmp.com/) · [tonsofskills.com](https://tonsofskills.com/) · [agensi.io marketplace guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) · [openaitoolshub.org comparison](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison) · [authority.md guide](https://authority.md/guides/best-places-to-buy-claude-skills) · [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) · [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)

---

### 5. MCP Ecosystem: 9,400+ Servers, 110M Downloads/Month, Enterprise Infrastructure

The Model Context Protocol ecosystem has matured from "experiment" to enterprise infrastructure since its open-source release in late 2024.

**Growth numbers (April 2026):**
- Public registry: 9,400+ servers (from 1,200 in Q1 2025 — **7.8x YoY**, still +18% MoM in Q1 2026)
- SDK downloads: **97–110 million/month** (David Soria Parra, MCP co-creator, at MCP Dev Summit NA 2026)
- Enterprise teams with MCP in production: **78%** (up from 31% a year prior)
- 300+ MCP clients; 80% of top servers offer remote deployment

**Top MCP servers (from community rankings):**
GitHub, Vercel, Stripe, Notion, Linear, Tavily (real-time search), Playwright (browser automation), PostgreSQL, Figma, Coolify

**Architecture distinction:**
- MCP servers: processes exposing tools over a documented protocol; any compatible client can use them
- Plugins: Claude Code-specific packages that can bundle MCP + Claude-native pieces (skills, agents, hooks)

**MCP vs Skills — complementary, not competing:**
From Anthropic's blog: Skills "complement MCP servers by teaching agents more complex workflows that involve external tools." MCP provides the integration; Skills provide the procedural knowledge of how to use it.

**Sources:** [effloow.com 97M installs](https://effloow.com/articles/mcp-ecosystem-growth-100-million-installs-2026) · [digitalapplied.com MCP stats](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol) · [aaif.io MCP Dev Summit](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/) · [analyticsvidhya.com top MCP](https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/) · [dev.to MCP ecosystem](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln) · [mcpmarket.com](https://mcpmarket.com/) · [aiagentslist.com](https://aiagentslist.com/mcp-servers)

---

### 6. Security Crisis: 30 CVEs in 60 Days, 9/11 Registries Poisonable

The rapid growth of MCP and the skill ecosystem has outpaced security infrastructure. A major security wave hit in early 2026:

**MCP database vulnerabilities (The Register, May 13, 2026):**
- **CVE-2025-66335** (Apache Doris): SQL injection via unvalidated `db_name` parameter — patched Dec 2025
- **Apache Pinot**: HTTP without auth, unauthenticated remote query execution — StarTree added OAuth option, Apache opened issue
- **Alibaba RDS MCP**: No auth before RAG tool invocation, exposes table names/schemas — **UNPATCHED**, Alibaba declined to fix

**Systemic vulnerabilities:**
- Only **8.5% of MCP servers use OAuth**; rest use static API keys or no auth
- **9 of 11 MCP registries** successfully "poisoned" with malicious trial balloon
- **30+ CVEs filed Jan-Feb 2026** targeting MCP infrastructure
- **CVE-2026-26118** (Microsoft MCP server): AI tool hijacking vulnerability
- Attack vectors: prompt injection, tool poisoning, version drift, supply chain attacks

Tomer Peled (Akamai): *"There is missing or faulty security validation between the MCP server and its back end...these security gaps will become high-value targets for attackers."*

**Skills-specific security risks** (per official Anthropic docs): Malicious skills can invoke tools (file ops, bash, code execution) in harmful ways; skills with external URL dependencies can be compromised even if originally trustworthy. Treat skills like installing software.

**Sources:** [The Register: MCP flaws](https://www.theregister.com/security/2026/05/13/bug-hunter-tracks-down-three-serious-mcp-database-flaws-one-left-unpatched/5238916) · [OX Security supply chain](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) · [heyuan110.com 30 CVEs](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) · [Palo Alto Networks](https://live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed-what-you-need-to-know-now/ba-p/1227143) · [aembit.io guide](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) · [practical-devsecops.com](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) · [pointguardai.com CVE-2026-26118](https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118) · [composio.dev vulnerabilities](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know) · [nimblebrain.ai security state](https://nimblebrain.ai/blog/state-of-mcp-security-2026/)

---

### 7. Tooling Fragmentation: The Multi-Agent Skills Management Problem

As developers use multiple AI coding agents simultaneously (Claude Code, Cursor, GitHub Copilot, Gemini CLI, Windsurf, Goose, Codex), skill management has become fragmented:

- Each agent stores skills in different locations and formats
- "The same instruction produces very different results depending on the agent"
- Claude handles multi-step rules effectively; Copilot ignores anything beyond initial instructions

A developer built **Skills Manager** (https://sm.idoevergreen.me) — a free, open-source desktop app to unify skill management across 7 agents with a single interface. The HN discussion (3 pts, 9 comments) surfaced a key insight: "We need a unified skill marketplace for different agents."

Most coding agents use `~/.agents/skills` as a standard path; **Claude Code diverges** with `~/.claude/skills/`. This divergence was noted as a friction point.

The broader ecosystem has also seen **`agentskills.io`** emerge as a formal specification site for the open standard.

**Sources:** [HN: Skills Manager](https://news.ycombinator.com/item?id=47423910) · [HN: Best hosted agent 2026](https://news.ycombinator.com/item?id=46917293) · [Claude Code docs: sub-agents](https://docs.anthropic.com/en/docs/claude-code/sub-agents)

---

### 8. Real-World Production Workflows: What Power Users Are Actually Building

From a detailed personal workflow post ([okhlopkov.com](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/)), the pattern that emerges for heavy Claude Code users:

**The stack:**
- 3 MCP servers: Coolify (deployment), Telegram (async notifications), Codex (dual-model review)
- 3 custom skills: domain-specific SQL generation, relationship graph building, cross-platform content distribution
- 1 critical hook: pre-commit file filter blocking .env/.key/.pem from ever being committed

**The workflow:** Voice notes → transcription → agent handles SQL writing, data formatting, chart generation, report assembly. Hours of analytical work → ~20 minutes review. Cost: $100/month Claude Max.

**DEV.to recommendations:**
- Top paid skills (5-15 EUR): Git Dojo, Component Builder, Design System Auditor
- Skill size best practice: under 2,000 tokens
- 10 skills at 2,000 tokens each = ~5% context window usage
- "Custom skills > generic ones" — project-specific configurations provide greater ROI

**Multi-agent architectures:** The [mnzralee/claude-multi-agent-architecture](https://github.com/mnzralee/claude-multi-agent-architecture) repo provides a production-ready template: 185 specialized agents, 16 workflow orchestrators, 153 skills, 100 commands in 80 plugins. The [claude-code-ultimate-guide](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md) details a git-based agent team coordination system where agents claim tasks, merge continuously, and resolve conflicts automatically.

**Sources:** [okhlopkov.com setup](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) · [dev.to guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) · [claude-multi-agent-architecture](https://github.com/mnzralee/claude-multi-agent-architecture) · [agent-teams workflow](https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/guide/workflows/agent-teams.md) · [wshobson agents](https://github.com/wshobson/agents)

---

## Cross-Source Patterns

### Pattern 1: "Skills as a Bigger Deal Than MCP" — Debated Across Platforms
- **Appeared on:** Hacker News (816 pts thread), multiple web blogs, official Anthropic engineering blog
- Simon Willison's framing ("maybe a bigger deal than MCP") generated significant debate
- Proponents: progressive disclosure solves real context window problems; enables organizational knowledge sharing
- Skeptics: "just prompt engineering," "a framework to append text to your prompt"
- Resolution: Practical consensus is that Skills and MCP are **complementary** — MCP provides integration, Skills provide procedural knowledge
- **Quote:** *"an interesting shift in thinking how to work with these tools"* — HN commenter ([link](https://news.ycombinator.com/item?id=45607117))

### Pattern 2: Security as the Ecosystem's Achilles Heel
- **Appeared on:** Web (The Register, Palo Alto Networks, OX Security, Akamai, Aembit), Official Anthropic docs
- The rapid growth of MCP has dramatically outpaced security tooling
- 30 CVEs in 60 days, 9/11 registries poisonable, 91.5% of servers without OAuth
- One unpatched vulnerability (Alibaba RDS) with vendor declining to fix
- Official docs explicitly warn: "treat skills like installing software"
- **Quote:** *"There is missing or faulty security validation between the MCP server and its back end...these security gaps will become high-value targets for attackers."* — Tomer Peled, Akamai ([source](https://www.theregister.com/security/2026/05/13/bug-hunter-tracks-down-three-serious-mcp-database-flaws-one-left-unpatched/5238916))

### Pattern 3: Distribution Infrastructure Lags Capability
- **Appeared on:** Hacker News (plugin launch thread), multiple marketplace comparison sites, Skills Manager HN thread
- Plugin system gave Claude Code capabilities but not distribution — community immediately filled the gap
- Multiple independent marketplaces built within days of plugin launch
- The multi-agent path divergence (Claude Code's `~/.claude/skills/` vs. standard `~/.agents/skills`) adds friction
- "We need a unified skill marketplace for different agents" — HN commenter ([link](https://news.ycombinator.com/item?id=47423910))

### Pattern 4: The App Store Historical Parallel
- **Appeared on:** Multiple blogs (chris-ayers.com, agensi.io, paperclipped.de, digitalapplied.com)
- Consistent framing: agent skill marketplaces follow the same arc as PC software stores → mobile app stores → browser extension stores → AI agent skills
- 19x search volume growth (21K → 400K/month) validates early market formation
- Question now: which marketplace wins? Curation vs. scale vs. revenue share are the differentiating axes

---

## Per-Platform Tables

**Hacker News:**
| User/Title | Points | Comments | Notable Quote | URL |
|-----------|--------|----------|--------------|-----|
| Claude Skills | 816 | 427 | "maybe a bigger deal than MCP" (Simon Willison) | [link](https://news.ycombinator.com/item?id=45607117) |
| Customize Claude Code with plugins | 48 | — | "distribution is going to be key" | [link](https://news.ycombinator.com/item?id=45530150) |
| Claude Code Skills and Plugins as an Open Source Project | — | — | — | [link](https://news.ycombinator.com/item?id=47321892) |
| Show HN: Agent Skills – 1k curated from 60k+ GitHub skills | — | — | — | [link](https://news.ycombinator.com/item?id=46693426) |
| Skills Manager – manage AI agent skills across agents | 3 | 9 | "We need a unified skill marketplace" | [link](https://news.ycombinator.com/item?id=47423910) |
| Ask HN: Best option for hosted agent in 2026? | 3 | 2 | Recommends Claude Agent SDK | [link](https://news.ycombinator.com/item?id=46917293) |
| A Claude Code and Codex Skill for Deliberate Skill Dev | — | — | — | [link](https://news.ycombinator.com/item?id=48130679) |
| Show HN: Real-time dashboard for Claude Code agent teams | — | — | — | [link](https://news.ycombinator.com/item?id=47602986) |
| How I use every Claude Code feature | — | — | — | [link](https://news.ycombinator.com/item?id=45786738) |
| Superwhisper now integrates with Claude Code | — | — | — | [link](https://news.ycombinator.com/item?id=47936169) |

**GitHub:**
| Repo | Stars | Forks | Description | URL |
|------|-------|-------|-------------|-----|
| hesreallyhim/awesome-claude-code | 44.1k | 3.8k | Curated skills, hooks, slash-commands, plugins | [link](https://github.com/hesreallyhim/awesome-claude-code) |
| sickn33/antigravity-awesome-skills | 37.9k | 6.2k | 1,460+ skills, npx installer, 9 agents supported | [link](https://github.com/sickn33/antigravity-awesome-skills) |
| jeremylongshore/claude-code-plugins-plus-skills | — | — | 425 plugins, 2,810 skills, ccpi CLI | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) |
| rohitg00/awesome-claude-code-toolkit | — | — | 135 agents, 176+ plugins, 14 MCP configs | [link](https://github.com/rohitg00/awesome-claude-code-toolkit) |
| VoltAgent/awesome-agent-skills | — | — | 1,000+ skills, multi-agent compatible | [link](https://github.com/VoltAgent/awesome-agent-skills) |
| ComposioHQ/awesome-claude-plugins | — | — | Plugins with agents, hooks, MCP | [link](https://github.com/ComposioHQ/awesome-claude-plugins) |
| alirezarezvani/claude-skills | — | — | 263+ skills across 8 domains | [link](https://github.com/alirezarezvani/claude-skills) |
| mnzralee/claude-multi-agent-architecture | — | — | 185 agents, 153 skills, 80 plugins | [link](https://github.com/mnzralee/claude-multi-agent-architecture) |
| Blink-h/agent-startup-kit | — | — | Reusable workflows for auth/billing/landing pages | [link](https://github.com/Blink-h/agent-startup-kit) |
| anthropics/skills | — | — | Official Anthropic skills repo | [link](https://github.com/anthropics/skills) |
| atompilot/polymarket-skill | — | — | Claude Code skill for Polymarket API | [link](https://github.com/atompilot/polymarket-skill) |
| mjunaidca/polymarket-skills | — | — | Composable Polymarket trading skills | [link](https://github.com/mjunaidca/polymarket-skills) |

**YouTube:**
| Channel | Title | Upload | URL |
|---------|-------|--------|-----|
| — | The Ultimate Claude Code Guide \| MCP, Skills & More | April 2026 | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| — | Máster Claude Code 2026: Agentes IA, MCP, Skills y Comandos | ~1 month ago | [link](https://www.youtube.com/watch?v=roPfcQHdUtY) |
| — | How I Actually Use Claude Every Day in 2026 | 2 weeks ago | [link](https://www.youtube.com/watch?v=EZcYjH3jAo8) |
| — | Full Claude Code Tutorial for Non-Technical Beginners in 2026 | 3 weeks ago | [link](https://www.youtube.com/watch?v=bqJzIWAEn40) |

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Claude Mythos released by June 30? | 20% | $375K | [link](https://polymarket.com/predictions/claude) |
| Claude score on Humanity's Last Exam by June 30? | 20% | $283K | [link](https://polymarket.com/predictions/claude) |
| Anthropic Claude score on FrontierMath by June 30? | 54% | $62.9K | [link](https://polymarket.com/predictions/claude) |
| Will Claude go down on __ days in May? | 45% | $33.9K | [link](https://polymarket.com/predictions/claude) |
| Anthropic valued higher than OpenAI in 2026? | 90% | $81.4K | [link](https://polymarket.com/predictions/claude) |
| Will Anthropic make a deal with the Pentagon? | 23% | $132K | [link](https://polymarket.com/predictions/claude) |
| Trump orders federal review of AI model releases? | 17% | $66.2K | [link](https://polymarket.com/predictions/claude) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Official progressive disclosure architecture, security guidance |
| Claude Code Plugin Docs | [link](https://code.claude.com/docs/en/plugins) | Full plugin system specification |
| Claude API Agent Skills Docs | [link](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | API integration, pre-built skills, limitations |
| Claude Agent SDK Blog | [link](https://claude.com/blog/building-agents-with-the-claude-agent-sdk) | SDK architecture, agent loop, MCP integration |
| paperclipped.de (open standard) | [link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) | SKILL.md adoption timeline, 32 adopters, Simon Willison quote |
| The Register (security) | [link](https://www.theregister.com/security/2026/05/13/bug-hunter-tracks-down-three-serious-mcp-database-flaws-one-left-unpatched/5238916) | 3 CVEs: Apache Doris, Pinot, Alibaba RDS (unpatched) |
| heyuan110.com (30 CVEs) | [link](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) | 30 CVEs in 60 days analysis |
| OX Security (supply chain) | [link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | 9/11 MCP registries poisonable |
| effloow.com (97M installs) | [link](https://effloow.com/articles/mcp-ecosystem-growth-100-million-installs-2026) | MCP growth trajectory, 97M SDK downloads/month |
| aaif.io (MCP Dev Summit) | [link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/) | 110M downloads/month, 78% enterprise adoption |
| digitalapplied.com (MCP stats) | [link](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol) | 7.8x YoY growth, 9,400 servers |
| digitalapplied.com (marketplaces) | [link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | Discovery & distribution analysis |
| okhlopkov.com (personal setup) | [link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | Real-world production workflow, 3 MCP + 3 custom skills |
| agensi.io (plugins vs skills) | [link](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Security comparison, installation methods |
| agensi.io (marketplace guide) | [link](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Plugin marketplace ecosystem overview |
| agensi.io (skills marketplace) | [link](https://www.agensi.io/learn/skills-marketplace-ai-agents) | App Store historical parallel, 19x search growth |
| agensi.io (open standard) | [link](https://www.agensi.io/learn/agent-skills-open-standard) | SKILL.md specification overview |
| agensi.io (marketplace comparison) | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Platform comparison |
| agensi.io (how marketplaces work) | [link](https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work) | Developer mechanics guide |
| chris-ayers.com (complete guide) | [link](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | End-to-end ecosystem overview, App Store analogy |
| kdnuggets.com (top 5 marketplaces) | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Eight marketplaces that matter |
| dev.to (best guide) | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Top skills by category, pricing, optimization tips |
| dev.to (MCP ecosystem) | [link](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln) | MCP integration layer analysis |
| nimbalyst.com (plugins guide) | [link](https://nimbalyst.com/blog/claude-code-plugins-guide/) | Plugin system walkthrough |
| nimbalyst.com (MCP servers) | [link](https://nimbalyst.com/blog/best-claude-code-mcp-servers/) | Ranked MCP servers |
| composio.dev (top plugins) | [link](https://composio.dev/content/top-claude-code-plugins) | Curated plugin list |
| composio.dev (MCP vulnerabilities) | [link](https://composio.dev/content/mcp-vulnerabilities-every-developer-should-know) | Vulnerability guide |
| morphllm.com (plugins vs skills) | [link](https://www.morphllm.com/claude-code-plugins-vs-skills) | Comparison guide |
| morphllm.com (plugins) | [link](https://www.morphllm.com/claude-code-plugins) | Best plugins 2026 |
| paperclipped.de (marketplace) | [link](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/) | New plugin ecosystem analysis |
| tonykipkemboi.com | [link](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained) | Skills and plugins explained |
| buildfastwithai.com | [link](https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026) | Complete skills guide 2026 |
| termdock.com (SKILL.md vs CLAUDE.md) | [link](https://www.termdock.com/blog/skill-md-vs-claude-md-vs-agents-md) | Comparison of instruction file formats |
| scriptbyai.com (resource list) | [link](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate resource list 2026 |
| mejba.me (top 10) | [link](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 skills/plugins/CLIs |
| firecrawl.dev (Claude skills) | [link](https://www.firecrawl.dev/blog/best-claude-code-skills) | Best Claude Code skills |
| firecrawl.dev (MCP devs) | [link](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | Best MCP for developers |
| medium.com/@unicodeveloper | [link](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 must-have skills |
| medium.com (MCP rise) | [link](https://medium.com/mcp-server/the-rise-of-mcp-protocol-adoption-in-2026-and-emerging-monetization-models-cb03438e985c) | Monetization models |
| medium.com (MCP gateways) | [link](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | MCP gateway tools |
| medium.com (7 MCP servers) | [link](https://medium.com/@docat0209/7-mcp-servers-every-claude-user-should-know-about-2026-9d17a0f5db73) | Must-know MCP servers |
| openaitoolshub.org | [link](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison) | 6-platform marketplace comparison |
| authority.md | [link](https://authority.md/guides/best-places-to-buy-claude-skills) | Best places to buy/find skills |
| smartscope.blog (SkillsMP) | [link](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) | SkillsMP guide |
| virtualuncle.com (skills.sh) | [link](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Vercel skills.sh guide |
| analyticsvidhya.com (top MCP) | [link](https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/) | Top 10 MCP servers |
| k2view.com (awesome MCP) | [link](https://www.k2view.com/blog/awesome-mcp-servers) | Awesome MCP directory |
| toloka.ai (best MCP) | [link](https://toloka.ai/blog/best-mcp-servers-for-ai-agents/) | Best MCP for agents |
| mcpbundles.com | [link](https://www.mcpbundles.com/blog/best-mcp-servers) | Updated MCP list April 2026 |
| databar.ai (sales) | [link](https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026) | MCP for sales teams |
| codeless.co | [link](https://codeless.co/best-claude-mcp-servers/) | Best Claude MCP servers |
| codeongrass.com | [link](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/) | MCP integration layer overview |
| nimblebrain.ai (MCP security) | [link](https://nimblebrain.ai/blog/state-of-mcp-security-2026/) | State of MCP security March 2026 |
| paloaltonetworks.com | [link](https://live.paloaltonetworks.com/t5/community-blogs/mcp-security-exposed-what-you-need-to-know-now/ba-p/1227143) | MCP security exposure |
| aembit.io (MCP security) | [link](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) | Ultimate MCP security guide |
| practical-devsecops.com | [link](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | Prompt injection and tool poisoning |
| pointguardai.com (CVE-2026-26118) | [link](https://www.pointguardai.com/ai-security-incidents/microsoft-mcp-server-vulnerability-opens-door-to-ai-tool-hijacking-cve-2026-26118) | Microsoft MCP CVE |
| blog.cyberdesserts.com | [link](https://blog.cyberdesserts.com/ai-agent-security-risks/) | AI agent security risks 2026 |
| blakecrosley.com | [link](https://blakecrosley.com/guides/claude-code) | Complete Claude Code CLI guide |
| claude-plugins.dev | [link](https://claude-plugins.dev/) | Community registry with CLI |
| claudeskills.info | [link](https://claudeskills.info/skills/) | Free Claude skills directory |
| findskill.ai (Cowork) | [link](https://findskill.ai/blog/claude-cowork-guide/) | Claude Cowork guide |
| gist.github.com (MCP config) | [link](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) | 5 MCP servers + debugging tips |
| learn.microsoft.com | [link](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) | Microsoft MCP tools documentation |
| deepwiki.com (microsoft skills) | [link](https://deepwiki.com/microsoft/agent-skills/4-plugins) | Microsoft agent skills plugins |
| resources.anthropic.com (PDF) | [link](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf) | Official Anthropic PDF guide |
| udemy.com (course) | [link](https://www.udemy.com/course/claude-course-prompt-skills-mcp-claude-code-cowork-etc/) | Claude skills/MCP/Code course |
| chainstack.com (Polymarket) | [link](https://docs.chainstack.com/docs/polygon-creating-a-polymarket-trading-openclaw-skill) | Polymarket OpenClaw skill tutorial |
| docs.anthropic.com (sub-agents) | [link](https://docs.anthropic.com/en/docs/claude-code/sub-agents) | Official subagents docs |
| agentskills.in | [link](https://www.agentskills.in/marketplace/@Jamie-BitFlight/claude-plugins-reference-2026) | Plugin reference marketplace |

---

## Stats Block

```
├─ 🟢 HN: 10 stories │ 870+ points │ 460+ comments
├─ 💻 GitHub: 12 repos │ 82k+ stars (top 2) │ 10k+ forks
├─ 🌐 Web: 70+ pages │ — │ official docs + blogs + security
├─ 🔴 YouTube: 4 videos │ views unknown (no transcript access)
├─ 📊 Polymarket: 7 markets │ $1.1M+ volume │ Claude model performance focus
├─ 🟠 Reddit: 0 │ domain blocked to crawler
├─ 🔵 X/Twitter: 0 │ domain blocked to crawler
├─ 🟣 TikTok: 0 │ no results
├─ 🦋 Bluesky: 0 │ no results
└─ 🗣️ Top voices: Simon Willison, Tomer Peled (Akamai), David Soria Parra (MCP co-creator) │ r/[not available]
```

---

## Data Gaps

- **Reddit:** Domain blocked to Anthropic crawler; zero Reddit threads retrieved. Reddit discussion of Claude Code skills/plugins is likely substantial but absent from this briefing entirely.
- **X/Twitter:** Domain blocked; no tweets retrieved. Significant discourse about agent skills on X is not represented.
- **TikTok/Instagram/Bluesky:** No results returned for this topic.
- **YouTube:** Video metadata only (no transcript access). View/like counts not retrieved. 4 relevant videos identified but content depth is limited to titles/descriptions.
- **Hacker News rate limiting:** HN returned 429 errors for several threads (`/item?id=47321892`, `/item?id=48130679`, `/item?id=46693426`); only thread titles and high-level summaries retrieved, not full comment content.
- **Polymarket:** No prediction markets specifically about agent skills/plugins found. The 7 Claude-related markets are all about model capabilities/releases, not the plugin ecosystem.
- **Skill/plugin engagement metrics:** Most GitHub repos beyond the top 2 did not return star/fork counts; marketplace skill counts vary significantly (SkillsMP self-reports 1.4M but uses 2-star GitHub filter; quality varies widely).
- **Coverage estimate:** ~65% — strong web/official docs coverage, good GitHub/HN signal, zero social media signal.

---

## Key Quotes

> *"Maybe a bigger deal than MCP"* — Simon Willison on Claude Skills, on Platform (now Hacker News) ([link](https://news.ycombinator.com/item?id=45607117))

> *"You're getting hyped over a framework to append text to your prompt"* — HN skeptic on Claude Skills ([link](https://news.ycombinator.com/item?id=45607117))

> *"Distribution is going to be key — plugin maintainers shouldn't have to build marketplaces themselves"* — Developer on Hacker News at plugin launch ([link](https://news.ycombinator.com/item?id=45530150))

> *"We need a unified skill marketplace for different agents"* — HN commenter on Skills Manager thread ([link](https://news.ycombinator.com/item?id=47423910))

> *"There is missing or faulty security validation between the MCP server and its back end...these security gaps will become high-value targets for attackers."* — Tomer Peled, Akamai security analyst ([link](https://www.theregister.com/security/2026/05/13/bug-hunter-tracks-down-three-serious-mcp-database-flaws-one-left-unpatched/5238916))

> *"Every major computing platform eventually gets a marketplace. PCs got software stores. Smartphones got the App Store and Google Play. Browsers got extension stores. AI agents are getting skills marketplaces."* — chris-ayers.com ([link](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/))

> *"The same instruction produces very different results depending on the agent"* — HN commenter on multi-agent fragmentation ([link](https://news.ycombinator.com/item?id=47423910))

> *"An interesting shift in thinking how to work with these tools"* — HN commenter on Skills' UX value ([link](https://news.ycombinator.com/item?id=45607117))

> *"This is the fastest cross-vendor standardization event in AI tooling, and it happened because the entire spec fits in a document you can read during a coffee break."* — paperclipped.de on SKILL.md adoption ([link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/))

> *"Custom skills > generic ones — project-specific configurations providing greater ROI than marketplace downloads"* — dev.to author on skill strategy ([link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4))
