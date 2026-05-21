# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-21
**Query type:** GENERAL
**Sources:** Web, Hacker News, YouTube, X/Twitter

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 stories | 738+ points, 370+ comments | 1 major thread (738p/370c) dominates |
| X/Twitter | 2 posts | N/A | Simon Willison + HN50 bot |
| YouTube | 2 videos | N/A | View counts inaccessible (YouTube blocks scraping) |
| Web | 60+ pages | — | Blogs, docs, news, GitHub repos, security advisories |

---

## Synthesized Findings

### 1. The Taxonomy Settles: Skills vs. MCP vs. Plugins vs. Connectors

The industry converged in early 2026 on a clear four-way distinction for extending AI coding agents:

**Skills** are Markdown files (SKILL.md) that teach agents *how* to perform tasks through procedural instructions, optionally bundled with scripts and resources. Each skill consumes only 30–50 tokens with progressive loading — descriptions are brief in context and expand on demand. They are auto-triggered by intent matching, not explicit slash commands.

**MCP Servers** connect agents to *external tools and data* (APIs, databases, cloud services) via Anthropic's Model Context Protocol, an open standard released late 2024 described as "USB for AI." MCP implementations can consume anywhere from 1–50K tokens upfront; GitHub's official MCP famously consumed "tens of thousands of tokens just loading."

**Plugins** are distributable bundles packaging skills, agents, hooks, MCP configs, LSP servers, and monitors into single installable packages. They are the "shareable packaging unit" of the ecosystem.

**Connectors** (claude.ai-level) link Claude to SaaS apps (Google Drive, Gmail, Microsoft 365, QuickBooks, HubSpot) with no-code setup. On March 31, 2026, Anthropic unified Skills, Connectors, and Plugins into a single Directory at claude.ai/directory.

The cross-platform comparison table from Morph LLM:
| Aspect | Skills | MCP | Plugins |
|--------|--------|-----|---------|
| Purpose | Teach procedures | Connect external tools | Bundle & share workflows |
| Token Cost | 30–50 per skill | 1–50K tokens upfront | Sum of components |
| Loading | Progressive (on-demand) | All definitions loaded | Varies by contents |
| Scope | Internal methodology | External connectivity | Everything combined |

Anthropic's own Tool Search feature reduces MCP context overhead by ~85% through on-demand discovery. Consensus recommendation: "2–3 MCP servers (GitHub, Filesystem, one domain-specific) + a few custom Skills for your workflow."

*Sources:* [Morph LLM](https://www.morphllm.com/claude-code-skills-mcp-plugins), [Claude Code Docs: Discover Plugins](https://code.claude.com/docs/en/discover-plugins), [Claude.ai Directory](https://www.anthropic.com/news/claude-for-small-business), [Nimbalyst: Claude Code Plugins Guide](https://nimbalyst.com/blog/claude-code-plugins-guide/), [Morph LLM Extensions Guide](https://www.morphllm.com/claude-code-extensions)

---

### 2. Ecosystem Explosion: From Zero to 350K+ Skills in Two Months

The agent skills ecosystem's growth rate has been extraordinary. npm required a decade to accumulate 350,000 packages. The AI agent skills ecosystem achieved comparable scale in roughly two months (January–March 2026).

Key milestones:
- **October 16, 2025**: Simon Willison publishes "Claude Skills are awesome, maybe a bigger deal than MCP" — the post that crystalized developer awareness and hit 738 points / 370 comments on Hacker News
- **December 2025**: Only 1 major skills registry exists
- **January 20, 2026**: Vercel launches skills.sh — "the npm of AI agents" — with 18-agent cross-platform support; top skill reaches 20,000 installs within 6 hours
- **February 4, 2026**: Vercel officially announces skills.sh open ecosystem; Snyk partnership begins on supply chain security
- **March 2026**: Ecosystem crosses 351,000 published skills across three main marketplaces; Anthropic opens official claude-plugins-official GitHub repo with 55+ curated plugins
- **March 31, 2026**: Anthropic unifies Skills/Connectors/Plugins into claude.ai/directory
- **April 16, 2026**: GitHub launches `gh skill` CLI in public preview — cross-agent package manager
- **May 12, 2026**: Anthropic publishes claude-for-legal suite: 12 plugins, 80+ agents, ~20 MCP connectors; 882 GitHub stars in 24 hours
- **May 20–21, 2026**: claudemarketplaces.com reports 6,700+ skills, 840+ MCP servers, 170,000+ monthly visitors

The top community-discovered skills on claudemarketplaces.com: "find-skills" (1.5M installs), "frontend-design" (418K installs), "caveman" (145K installs).

*Sources:* [Simon Willison blog](https://simonwillison.net/2025/Oct/16/claude-skills/), [HN thread 738p](https://news.ycombinator.com/item?id=45619537), [Vercel changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem), [InfoQ: Vercel Agent Skills](https://www.infoq.com/news/2026/02/vercel-agent-skills/), [ClaudeMarketplaces](https://claudemarketplaces.com/), [Anthropic claude-plugins-official](https://github.com/anthropics/claude-plugins-official), [Releasebot Claude Code May 2026](https://releasebot.io/updates/anthropic/claude-code), [Claude for Legal](https://pasqualepillitteri.it/en/news/2484/claude-for-legal-anthropic-legal-plugin-suite-open-source), [TechRadar: claude-for-legal](https://www.anthropic.com/news/finance-agents), [BuildMVPFast: Skills as npm](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

---

### 3. Cross-Agent Standardization: SKILL.md Becomes a Universal Open Standard

The most significant structural development of the past 30 days is SKILL.md cross-agent convergence. Anthropic introduced SKILL.md in October 2025 and open-sourced the format in December 2025. Within weeks, OpenAI adopted the same spec for Codex and ChatGPT. The standard is now maintained under the **Linux Foundation Agentic AI Foundation**, co-founded by Anthropic, Block, and OpenAI.

A single `.github/skills/` directory is now read by:
- Visual Studio 2026
- VS Code (GitHub Copilot)
- Claude Code
- GitHub Copilot CLI
- Cursor, Codex, Gemini CLI, Antigravity, Windsurf, Cline, and 10+ others

GitHub's `gh skill` CLI (April 16, 2026 public preview) installs skills cross-agent, automatically routing to the correct directory per agent (`.agents/skills/` for Copilot/Cursor, `.claude/skills/` for Claude Code). Security metadata (source, ref, tree SHA) is written into installed files for audit trails.

The Visual Studio May 2026 update shipped Agent Skills for VS IDE itself, with Copilot loading skills only when task context matches the skill trigger — not globally, avoiding context bloat. Microsoft's `microsoft/skills` repository contains 128 skills with 1,158 test scenarios. Their `.NET Skills` (March 9, 2026) made the dotnet/skills repo installable via `/plugin marketplace add dotnet/skills`.

Developer reaction (Discord quote on .NET Skills): "The skill just worked with the log that I've with me...it was smarter than me and found the correct debug symbol."

*Sources:* [GitHub microsoft/skills](https://github.com/microsoft/skills), [VS Blog: Agent Skills](https://devblogs.microsoft.com/visualstudio/agent-skills-in-visual-studio/), [.NET Blog: Skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/), [Big Hat Group: gh skill](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/), [VS Magazine: VS 2026 Insiders Skills](https://visualstudiomagazine.com/articles/2026/05/15/building-a-custom-copilot-skill-a-hands-on-guide-to-agent-mode-in-visual-studio-2026.aspx), [VoltAgent awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills), [Termdock: Cross-Agent Skills](https://www.termdock.com/blog/cross-agent-skills-new-npm), [MicrosoftDocs/Agent-Skills](https://github.com/MicrosoftDocs/Agent-Skills)

---

### 4. Registry Fragmentation: Eight Competing Marketplaces, Each with Different Trade-offs

The ecosystem went from one registry (December 2025) to eight major marketplaces by Q2 2026, creating a "developers now spend more time comparing marketplaces than finding skills" problem. The landscape by scale:

| Platform | Skills/Servers | Curation Level | Notes |
|----------|---------------|----------------|-------|
| MCP.so | 19,000+ MCP servers | None | Community submissions via GitHub issues |
| MCP Market | 10,000+ MCP servers | Light | 23+ categories, no API |
| SkillsMP | 800,000+ skills | Minimal | Scraped GitHub (≥2 stars filter) |
| LobeHub | 169,000+ skills | Moderate | Polished UI |
| Smithery | 7,000+ MCP servers | Moderate | OAuth support, hosted or local; Docker Hub equivalent |
| Glama | 6,000+ MCP listings | Community meta | Anthropic/GitHub/PulseMCP/Microsoft backed, preview |
| ClaudeMarketplaces | 6,700+ skills, 840+ MCPs | Community | 170K+ monthly visitors |
| ClaudeSkills.info | 658 skills | High (human) | Free, community-vetted, official Anthropic skills included |
| Anthropic Official | ~20 plugins | Maximum | Built into Claude Code |
| Agensi | 200+ skills | Automated 8-pt | Security-scanned, 80/20 revenue split |
| skills.sh (Vercel) | ~2,000 skills | Community | npm-style CLI, 18 agents |

Official registries: `registry.modelcontextprotocol.io` (metadata only, Anthropic+GitHub+PulseMCP+Microsoft, still in preview). The GitHub MCP Registry (launched September 16, 2025) currently has 44 servers with one-click VS Code install; Figma, Postman, HashiCorp, and Dynatrace were featured at launch.

MCP-based marketplace access is becoming the preferred delivery model: an agent connects once to a marketplace MCP server and can search the full live catalog, load skills on demand, and automatically receive new skills — no downloads or version management.

*Sources:* [Agensi: Best AI Marketplaces](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [TrueFoundry: Best MCP Registries](https://www.truefoundry.com/blog/best-mcp-registries), [GitHub MCP Registry blog](https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/), [DevOps.com: GitHub Registry](https://devops.com/github-mcp-registry-launches-as-central-hub-for-ai-development-tools/), [InfoWorld: GitHub Registry](https://www.infoworld.com/article/4061244/github-introduces-registry-for-finding-mcp-servers.html), [Smithery](https://smithery.ai/), [MCP Market](https://mcpmarket.com/tools/skills), [Agensi: Marketplace Guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide), [Medium: MCP Marketplaces](https://medium.com/@airabbitX/mcp-marketplaces-you-didnt-know-existed-but-really-should-5ea0afcc9584)

---

### 5. Security Crisis: ToxicSkills, ClawHavoc, and the Supply Chain Problem

The speed of ecosystem growth created a serious security gap. Snyk's **ToxicSkills study** (published February 5, 2026) was the first comprehensive audit of the agent skills supply chain, scanning 3,984 skills from ClawHub and skills.sh:

- **36.82%** of skills have at least one security flaw (1,467 skills)
- **13.4%** contain critical-level issues (534 skills)
- **76 confirmed malicious payloads** (human-reviewed)
- **8 malicious skills** remained publicly available on ClawHub at publication
- **91%** of confirmed malicious skills combine prompt injection + traditional malware
- **10.9%** contain hardcoded secrets or API keys
- Daily new skill submissions jumped **10x** in weeks (from <50/day in mid-Jan to 500+/day by early Feb)

The **ClawHavoc incident** (February 2026): 341 malicious skills found in ClawHub's registry after passing initial screening, downloaded by developers before detection. A subsequent Mobb.ai audit of 22,511 skills found 140,963 security issues (6.3 per skill average).

The fundamental reason skills are harder to secure than MCP: *"There is no code to scan. No binary payload. No known signature."* Skills operate as English-language instructions inside the model's reasoning context. MCP tool calls are observable and loggable; skills operate where attribution is "nearly impossible."

Help Net Security (May 5, 2026): 1 in 4 MCP servers exposes organizations to code execution vulnerabilities. Attack names documented: ContextCrush, ForcedLeak, DockerDash.

CVE-2025-59536 (CVSS 8.7, disclosed Feb 25, 2026 by Check Point Research): configuration injection via `.claude/settings.json` Hooks enables RCE when a developer opens a malicious project repository.

"Line jumping" attack: malicious MCP server tool descriptions contain hidden prompt payloads that execute before any legitimate tool is invoked.

Security partnerships forming: Snyk+Vercel (skills.sh ecosystem), Snyk+Tessl (registry security standard), GitHub's `gh skill` adds audit-trail metadata to all installs.

*Sources:* [Snyk ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/), [Agensi: ToxicSkills/ClawHavoc](https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026), [Help Net Security: 1 in 4 MCP](https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/), [Snyk/agent-scan HN post](https://news.ycombinator.com/item?id=47999709), [SkillSieve arxiv](https://arxiv.org/html/2604.06550v1), [Spec-Weave: 36% flaws](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/), [Practical DevSecOps: MCP security](https://www.practical-devsecops.com/mcp-security-vulnerabilities/), [Elastic Security Labs MCP](https://www.elastic.co/security-labs/mcp-tools-attack-defense-recommendations), [Snyk+Vercel](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/), [Snyk+Tessl](https://snyk.io/blog/snyk-tessl-partnership/), [ToxicSkills goof repo](https://github.com/snyk-labs/toxicskills-goof), [OX Security: MCP STDIO RCE](https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/), [Prompt Injection arxiv](https://arxiv.org/html/2601.17548v1), [Palo Alto Unit42: MCP attack vectors](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/)

---

### 6. Anthropic's Deepening Official Plugin Infrastructure

Anthropic has been actively building out official infrastructure around the plugin/skill ecosystem:

**Official plugin directory** (`anthropics/claude-plugins-official`): 55+ curated plugins split into `/plugins` (Anthropic-developed) and `/external_plugins` (vetted third-party: Supabase, Firebase, Discord, Telegram).

**Claude Code v2.1.137–2.1.145 (May 2026)** key plugin/skill updates:
- Pre-install "Will install" pane showing all components + context cost estimate + last-updated timestamp
- Plugin dependency enforcement (refuses to break deps)
- Standalone skills surfaced when root-level SKILL.md exists without skills/ subdir
- MCP stdio servers now receive `CLAUDE_PROJECT_DIR` env var
- Bug fix: paginated MCP `tools/list` responses previously silently dropped tools beyond page 1
- Marketplace auto-refresh on plugin-not-found before erroring

**claude-code-setup plugin**: scans project and recommends hooks, skills, MCP servers, subagents, and automations.

**claude-for-legal** (May 12, 2026): open-source suite with 12 legal practice plugins, 80+ specialized agents, ~20 MCP connectors; 882 stars and 165 forks in 24 hours — demonstrating strong appetite for domain-specific plugin bundles.

**Community marketplace** (`anthropics/claude-plugins-community`): automated validation + safety screening, plugins pinned to SHA.

*Sources:* [Anthropic claude-plugins-official](https://github.com/anthropics/claude-plugins-official), [Releasebot May 2026](https://releasebot.io/updates/anthropic/claude-code), [Releasebot Anthropic](https://releasebot.io/updates/anthropic), [Claude Code Discover Plugins](https://code.claude.com/docs/en/discover-plugins), [Groundy: Official Plugin Ecosystem](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/), [Claude for Legal news](https://pasqualepillitteri.it/en/news/2484/claude-for-legal-anthropic-legal-plugin-suite-open-source), [TechRadar: Legal Tools](https://www.anthropic.com/news/finance-agents), [Blockchain News: 2026 launches](https://blockchain.news/ainews/anthropic-claude-2026-launches-microsoft-365-connectors-1m-context-marketplace-and-claude-code-upgrades-latest-analysis), [Systemprompt.io: Marketplace Guide](https://systemprompt.io/guides/getting-started-anthropic-marketplace)

---

### 7. Community-Built Distribution Infrastructure: npm-Style Package Management for Skills

Beyond official channels, a rich community distribution infrastructure has emerged:

- **skills.sh** (`npx skills add <package>`): Vercel's npm-style CLI for agent skills; 18 agents; official partner skills from Prisma, Supabase, Stripe, Remotion, Coinbase, Microsoft
- **ccpi** (`@intentsolutionsio/ccpi`): npm package manager for tonsofskills.com; 425 plugins, 2,810 skills, 200 agents; `ccpi install [plugin-name]`
- **skills-npm** (Anthony Fu): discovers agent skills inside npm packages, symlinks for coding agent
- **Paks** (paks.stakpak.dev): AI Agent Skills Package Manager
- **agent-skills-manager**: dashboard for managing skills across Cursor, Claude, and Agents
- **VoltAgent/awesome-agent-skills**: curated list of 1,000+ skills for Claude Code, Codex, Gemini CLI, Cursor

The SkillFlow marketplace (skillflow.builders) exposes itself as an MCP server (`npx skillflow-mcp-server`), letting agents search, retrieve, and browse the catalog directly through tool calls — listed on the official Anthropic MCP Registry.

DEV.to blueprint post (March 5, 2026) by Jan Luca Sandmann described turning Claude Code into a full "AI OS" with: 12+ custom skills, 8 MCP servers, hooks for automation, scheduled/webhook execution, saving "~18 hours/week."

*Sources:* [Vercel Skills Docs](https://vercel.com/docs/agent-resources/skills), [Vercel KB: Agent Skills](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context), [tonsofskills/ccpi](https://github.com/jeremylongshore/claude-code-plugins-plus-skills), [Paks](https://paks.stakpak.dev), [SkillFlow dev.to](https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g), [agent-skills-manager](https://github.com/umutbozdag/agent-skills-manager), [VoltAgent awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills), [DEV.to: Claude Code AI OS](https://dev.to/jan_lucasandmann_bb9257c/claude-code-to-ai-os-blueprint-skills-hooks-agents-mcp-setup-in-2026-46gg), [npx skills guide](https://dev.to/toyama0919/managing-ai-agent-skills-with-npx-skills-a-practical-guide-2an8), [GetBindu awesome skills](https://github.com/GetBindu/awesome-claude-code-and-skills)

---

### 8. Critical Debate: Are MCP and Skills Just Hype?

The highest-engagement Hacker News thread on this topic (738 points, 370 comments) surfaced serious skepticism alongside enthusiasm:

**Pro-skills camp:**
- Context efficiency: GitHub's official MCP alone consumes tens of thousands of tokens; skills solve "context pollution"
- Skills formalize patterns developers were already using ("markdown plus CLI patterns")
- Immediate feedback loops explain why documentation quality is suddenly improving: "minutes vs. years" incentive realignment

**Skeptics:**
- Skills are "renamed instructions or system prompts" with better marketing
- "I've been using equivalent approaches with markdown files for over a year"
- tptacek: "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones."
- HN thread ID 46315957 asked: "How likely are we to look back on Agent/MCP/Skills as some early Netscape peculiarity?"

**cra.mr analysis** pushed back against exclusivity: "X is all you need. Please, please, please can we stop with that kind of thinking." The author characterized MCP as "an over-engineered protocol that does a lot of things that no one uses" but acknowledged it excels at network service exposure via OAuth. Sub-agents follow a "map/reduce" pattern. Skills are "reusable prompts with optional artifacts."

*Sources:* [HN: Skills bigger than MCP](https://news.ycombinator.com/item?id=45619537), [HN: Agents as MCP servers](https://news.ycombinator.com/item?id=44053754), [HN: Netscape peculiarity](https://news.ycombinator.com/item?id=46315957), [HN: Mother MCP](https://news.ycombinator.com/item?id=46692102), [HN: MCP Playground](https://news.ycombinator.com/item?id=46815786), [HN: Managing MCP servers](https://news.ycombinator.com/item?id=45695556), [HN: MCP Apps](https://news.ycombinator.com/item?id=46020502), [HN: Mcp-Agent](https://news.ycombinator.com/item?id=42867050), [HN: MCP-C cloud](https://news.ycombinator.com/item?id=45735886), [cra.mr: MCP Skills Agents](https://cra.mr/mcp-skills-and-agents/), [Simon Willison blog](https://simonwillison.net/2025/Oct/16/claude-skills/)

---

## Cross-Source Patterns

**Pattern 1: "Skills = new npm" narrative dominates framing**
- Platforms: Web (multiple blogs), Hacker News, X/Twitter
- Every commentary site is framing agent skills as infrastructure-layer, not feature-layer
- Key quotes: "This is npm for AI agents" — Aakash Harish on InfoQ; "npm took a decade to reach 350K packages. The AI agent skills ecosystem did it in about two months." — BuildMVPFast; "Discoverable skills solve the 'what can you do?' problem" — Thomas Rehmer
- The `gh skill` CLI launch (April 2026) cemented this with explicit package-manager semantics (pin, preview, publish)

**Pattern 2: Security anxiety is the counter-narrative, growing fast**
- Platforms: Web (security blogs, advisories), Hacker News (snyk/agent-scan post), Academic (arxiv)
- ToxicSkills study + ClawHavoc incident + 1-in-4 MCP server stat appeared within 90-day window
- Shared concern: skills operate inside model reasoning (unobservable), creating a governance blind spot vs. MCP's traceable tool calls
- Industry response: Snyk partnerships (Vercel, Tessl), SkillSieve academic framework, `gh skill` audit metadata

**Pattern 3: Cross-vendor standardization accelerating around SKILL.md**
- Platforms: Web (Microsoft blog, VS Magazine, Vercel docs), HN
- SKILL.md spec went from Anthropic-only (Oct 2025) → Linux Foundation standard (early 2026) → supported by all major coding agents by May 2026
- Represents a "USB-C moment" — one standard, many tools, many clients — mirroring MCP's own origin story

**Pattern 4: Enterprise verticalization of skills/plugins**
- Platforms: Web (Anthropic announcements, TechRadar)
- General-purpose marketplace → domain bundles (claude-for-legal 882 stars in 24h; Claude for Small Business; Microsoft Azure Skills; .NET Skills)
- Pattern: domain-specific skill bundles outperform general skill discovery on adoption metrics

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| simonw (linked) | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones." — tptacek | [link](https://news.ycombinator.com/item?id=45619537) |
| (unknown) | Show HN: Mother MCP – Auto provision agent skills | N/A | N/A | Skills+MCP auto-detect tech stack, install relevant coding skills | [link](https://news.ycombinator.com/item?id=46692102) |
| (unknown) | Show HN: Playground to Test Skills and MCP | N/A | N/A | — | [link](https://news.ycombinator.com/item?id=46815786) |
| (unknown) | How likely are we to look back on Agent/MCP/Skills as some early Netscape peculiarity | N/A | N/A | Skeptic framing of entire paradigm | [link](https://news.ycombinator.com/item?id=46315957) |
| (unknown) | Show HN: Representing Agents as MCP Servers | N/A | N/A | Agents themselves become MCP-orchestratable | [link](https://news.ycombinator.com/item?id=44053754) |
| (unknown) | Show HN: Mcp-Agent — Build effective agents with MCP | N/A | N/A | — | [link](https://news.ycombinator.com/item?id=42867050) |
| (unknown) | Show HN: MCP-C — cloud platform for MCP agents | N/A | N/A | — | [link](https://news.ycombinator.com/item?id=45735886) |
| (unknown) | Ask HN: How do you manage MCP servers across multiple agents? | N/A | N/A | Pain point: multi-agent MCP coordination | [link](https://news.ycombinator.com/item?id=45695556) |
| (unknown) | MCP Apps: Extending servers with interactive UIs | N/A | N/A | — | [link](https://news.ycombinator.com/item?id=46020502) |
| lirantal | Show HN: Security Scanner for Agent Skills and MCP (snyk/agent-scan) | 7 | N/A | Posted ~May 4, 2026 | [link](https://news.ycombinator.com/item?id=47999709) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @simonw | "Claude Skills are awesome, maybe a bigger deal than MCP" | N/A | N/A | [link](https://x.com/simonw/status/1978935386496995811) |
| @betterhn50 | "Claude Skills are awesome, maybe a bigger deal than MCP" (HN link) | N/A | N/A | [link](https://x.com/betterhn50/status/1979266538130804924) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | N/A | N/A | No | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| (unknown) | Claude Code Tutorial: Installation, Agents, MCP, Skills, Hooks & Plugins (Deutsch) | N/A | N/A | No | [link](https://www.youtube.com/watch?v=mfg2G1cNfnc) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Simon Willison blog | [link](https://simonwillison.net/2025/Oct/16/claude-skills/) | Original "Skills > MCP" argument; seeded 738p HN thread |
| Snyk ToxicSkills | [link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | 36.82% skill vulnerability rate; 76 confirmed malicious payloads |
| Agensi: Security Crisis | [link](https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026) | ClawHavoc 341 malicious skills; Mobb.ai 140K issues across 22K skills |
| Help Net Security | [link](https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/) | 1 in 4 MCP servers = code execution risk (May 5, 2026) |
| Claude Code Docs: Plugins | [link](https://code.claude.com/docs/en/discover-plugins) | Official Anthropic marketplace architecture, v2.1.143–145 features |
| Claude Marketplaces | [link](https://claudemarketplaces.com/) | 6,700+ skills, 840+ MCPs, 170K monthly visitors; top installs data |
| Vercel changelog | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh open skills ecosystem launch |
| InfoQ: Vercel | [link](https://www.infoq.com/news/2026/02/vercel-agent-skills/) | Developer reactions; "npm for AI agents" framing |
| GitHub MCP Registry | [link](https://github.blog/ai-and-ml/github-copilot/meet-the-github-mcp-registry-the-fastest-way-to-discover-mcp-servers/) | Registry launch Sept 16, 2025; 44 servers; Figma/Postman/HashiCorp |
| TrueFoundry: Registries | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Registry landscape: Smithery 7K, Glama 6K, MCP Market 10K, MCP.so 19K |
| Big Hat Group: gh skill | [link](https://www.bighatgroup.com/blog/gh-skill-github-cli-agent-skills-management/) | April 16, 2026 launch; cross-agent install; audit metadata |
| VS Blog: Agent Skills | [link](https://devblogs.microsoft.com/visualstudio/agent-skills-in-visual-studio/) | Visual Studio 2026 Agent Skills; .github/skills/ standard |
| .NET Blog: Skills | [link](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | March 9, 2026 .NET skills launch; Developer Discord quote |
| microsoft/skills | [link](https://github.com/microsoft/skills) | 128 skills, 1,158 test scenarios; Azure + Foundry MCP integration |
| Releasebot Claude Code May | [link](https://releasebot.io/updates/anthropic/claude-code) | v2.1.137–145 changelogs; plugin/skill/MCP improvements |
| cra.mr | [link](https://cra.mr/mcp-skills-and-agents/) | "X is all you need — please stop that thinking"; MCP as map/reduce |
| DEV.to: AI OS Blueprint | [link](https://dev.to/jan_lucasandmann_bb9257c/claude-code-to-ai-os-blueprint-skills-hooks-agents-mcp-setup-in-2026-46gg) | "Claude Code becomes the OS for the agentic era" |
| SkillFlow dev.to | [link](https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g) | MCP-as-marketplace; "USB-C of AI integrations" |
| Agensi: Marketplaces | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | April 2026 marketplace landscape; security scan metrics |
| BuildMVPFast: Skills=npm | [link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) | 350K skills in 2 months vs npm's decade |
| Morph LLM: Complete Guide | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Definitive skills/MCP/plugins comparison table |
| tonsofskills.com / ccpi | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2,810 skills, 200 agents; ccpi npm CLI |
| Anthropic claude-for-legal | [link](https://github.com/anthropics/claude-plugins-official) | 882 stars in 24h; 12 plugins + 80 agents |
| Practical DevSecOps: MCP | [link](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | Prompt injection + tool poisoning attack vectors |
| Elastic Security Labs | [link](https://www.elastic.co/security-labs/mcp-tools-attack-defense-recommendations) | Attack/defense guide for MCP tools |
| SkillSieve arxiv | [link](https://arxiv.org/html/2604.06550v1) | Hierarchical triage framework for malicious skills detection |
| Prompt Injection arxiv | [link](https://arxiv.org/html/2601.17548v1) | Systematic analysis of agentic coding assistant vulnerabilities |
| OX Security: MCP RCE | [link](https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/) | MCP STDIO command injection advisory |
| Palo Alto Unit42 | [link](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/) | MCP sampling attack vectors |
| DevOps.com: Registry | [link](https://devops.com/github-mcp-registry-launches-as-central-hub-for-ai-development-tools/) | GitHub MCP Registry launch coverage |
| InfoWorld: Registry | [link](https://www.infoworld.com/article/4061244/github-introduces-registry-for-finding-mcp-servers.html) | GitHub MCP Registry introduction |
| Sparkco: Prediction Markets | [link](https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi) | Claude Code + MCP for Polymarket/Kalshi trading |
| VoltAgent awesome-skills | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1,000+ cross-agent skills curated list |
| GetBindu awesome-claude | [link](https://github.com/GetBindu/awesome-claude-code-and-skills) | Claude-specific skills collection |
| Duet.so: Skills Guide | [link](https://duet.so/guides/claude-code-skills-complete-guide) | SKILL.md, MCP, Subagents & Teams reference |
| Duet.so: Skills vs Tools | [link](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills) | Agent skills taxonomy guide |
| Snyk+Tessl partnership | [link](https://snyk.io/blog/snyk-tessl-partnership/) | Registry security standard setting |
| Snyk+Vercel partnership | [link](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) | skills.sh supply chain security |
| Spec-Weave: 36% flaws | [link](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/) | Skill verification argument |
| Obot.ai: Supply Chain | [link](https://obot.ai/blog/mcp-security-agent-skills-supply-chain/) | MCP + skills supply chain frontier |
| Nimbalyst: Skills Guide | [link](https://nimbalyst.com/blog/claude-code-skills-guide/) | Claude Code skills practical guide |
| Nimbalyst: MCP Setup | [link](https://nimbalyst.com/blog/claude-code-mcp-setup/) | MCP setup practical guide |
| Nimbalyst: Best MCPs | [link](https://nimbalyst.com/blog/best-claude-code-mcp-servers/) | Best Claude Code MCP servers ranked |
| Clarita: MCP Guide | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Complete 2026 MCP guide |
| Skillsplayground | [link](https://skillsplayground.com/guides/claude-code-plugins/) | Complete Claude Code plugins guide |
| Systemprompt.io: MCP | [link](https://systemprompt.io/guides/claude-code-mcp-servers-extensions) | Install/configure MCP guide |
| Arcade.dev: Routines | [link](https://www.arcade.dev/blog/claude-code-routines-mcp-setup/) | 5 production workflows + MCP setup |
| Beginners in AI | [link](https://beginnersinai.org/claude-skills-connectors-plugins/) | Skills vs Connectors vs Plugins comparison |
| Groundy: Official Plugins | [link](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | Anthropic official plugin ecosystem explainer |
| MCP Directory: Polymarket | [link](https://mcp.directory/skills/polymarket-agent) | Polymarket agent skill |
| Polymarket skills repo | [link](https://github.com/mjunaidca/polymarket-skills) | Composable Polymarket agent skills |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ 0 upvotes │ 0 comments   (no indexed results found)
├─ 🔵 X: 2 posts │ N/A likes │ N/A reposts
├─ 🔴 YouTube: 2 videos │ N/A views                (view counts inaccessible)
├─ 🟢 HN: 10 stories │ 738+ points │ 370+ comments (1 major thread dominates)
├─ 🟣 TikTok: 0 videos │ 0 views                   (no relevant results found)
├─ 🩷 Instagram: 0 reels │ 0 views                  (no results)
├─ 🦋 Bluesky: 0 posts │ 0 likes                   (no indexed results)
├─ 📊 Polymarket: 0 markets │ $0 volume             (skills for trading Polymarket exist; no markets about skills)
├─ 🌐 Web: 60+ pages
└─ 🗣️ Top voices: @simonw (Simon Willison) │ lirantal (Snyk) │ tptacek (HN) │ Jan Luca Sandmann (DEV.to)
```

---

## Data Gaps

- **Reddit**: Zero indexed results for r/ClaudeAI or r/programming threads about skills/MCP/plugins from the past 30 days. Reddit's content is poorly indexed by external search engines; likely active discussions exist but are not surfaced. Estimated coverage: ~5% of actual Reddit engagement.
- **X/Twitter**: Only two tweets found via web search (Simon Willison's original post). X's search wall means the broader X discussion on this topic (likely significant given the HN thread engagement) is largely invisible. Estimated coverage: ~5%.
- **YouTube**: Two videos found but view counts/likes not accessible — YouTube returns only footer HTML to WebFetch. Actual tutorial viewership for Claude Code skills/MCP content is likely substantial but unmeasured here.
- **TikTok**: No TikTok content found. This topic likely has minimal short-form video coverage; or it exists but is unsearchable via web.
- **Bluesky**: No Bluesky posts found. The developer community there may discuss this but not indexed.
- **Polymarket**: No prediction markets found specifically about agent skills/MCP adoption outcomes. (Polymarket-related content that *did* surface: agent skills for *trading on* Polymarket.)
- **HN comment counts**: Only the top HN thread (45619537) had detailed engagement data (738p/370c); the other 9 stories had point/comment counts rate-limited or not available.
- **Approximate overall coverage**: Web ~85%, HN ~70%, X/Twitter ~10%, Reddit ~5%, YouTube metadata ~20%, other platforms ~0%.

---

## Key Quotes

> "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones." — tptacek on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Skills are mainly just a formalization of the markdown plus CLI patterns that people have been using already." — @simonw on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "This is npm for AI agents...Skills solves 'how do devs share and discover agent capabilities.'" — Aakash Harish, quoted in InfoQ ([link](https://www.infoq.com/news/2026/02/vercel-agent-skills/))

> "Discoverable skills solve the 'what can you do?' problem that most agent setups have." — Thomas Rehmer, quoted in InfoQ ([link](https://www.infoq.com/news/2026/02/vercel-agent-skills/))

> "100% of confirmed malicious skills contain malicious code patterns, while 91% simultaneously employ prompt injection techniques." — Snyk ToxicSkills study ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "There is no code to scan. No binary payload. No known signature." — Agensi on malicious skills ([link](https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026))

> "Claude Code was never meant to stay in the terminal. With this skills + hooks + agents + MCP blueprint, it becomes the operating system for the agentic era." — Jan Luca Sandmann on DEV.to ([link](https://dev.to/jan_lucasandmann_bb9257c/claude-code-to-ai-os-blueprint-skills-hooks-agents-mcp-setup-in-2026-46gg))

> "X is all you need. Please, please, please can we stop with that kind of thinking?" — cra.mr blog on MCP vs Skills vs Agents ([link](https://cra.mr/mcp-skills-and-agents/))

> "MCP is an over-engineered protocol that does a lot of things that no one uses." — cra.mr blog ([link](https://cra.mr/mcp-skills-and-agents/))

> "npm took a decade to reach 350,000 packages. The AI agent skills ecosystem did it in about two months." — BuildMVPFast ([link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026))
