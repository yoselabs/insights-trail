# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-24
**Query type:** GENERAL
**Sources:** Web, Hacker News, GitHub, YouTube, Official Docs

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 threads | tracked via URL | Key debates on Skills vs MCP |
| GitHub | 10+ repos | stars/forks tracked | Both official Anthropic + community |
| YouTube | 1 video | — | April 2026 comprehensive guide |
| Web | 55 pages | — | via WebSearch (11 query batches) |
| Reddit | 0 | — | Excluded from web search; not captured |
| X/Twitter | 0 | — | Excluded from web search; not captured |
| TikTok | 0 | — | Not queried this run |
| Instagram | 0 | — | Not queried this run |
| Bluesky | 0 | — | Not queried this run |
| Polymarket | 0 | — | No relevant markets found |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard Has Created a Cross-Platform Ecosystem

In December 2025, Anthropic published the Agent Skills specification as an open standard centered on a simple `SKILL.md` file format: YAML frontmatter for metadata + markdown for instructions. The key insight was minimalism — a skill is just a directory containing a file. Within 48 hours, Microsoft integrated it into VS Code and OpenAI added support to both ChatGPT and Codex CLI. By March 2026, **32 tools from competing companies** — Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, Block's Goose — all read the same SKILL.md files from the same directory structure.

> "By March 2026, 32 tools from competing companies, including Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose, all read the same SKILL.md files from the same directory structure." — [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

The specification is hosted at [agentskills.io/specification](https://agentskills.io/specification) and officially documented at [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview). Anthropic maintains a public repo at [github.com/anthropics/skills](https://github.com/anthropics/skills).

**Platforms discussing this:** Web, Hacker News, GitHub

---

### 2. Three-Layer Architecture: Skills vs MCP vs Plugins

The community has converged on a clear taxonomy that confused developers early on:

- **Skills** = instructional layer. A SKILL.md file teaches an agent *how* to do something using only 30-50 tokens per skill until activated. Pure markdown, no runtime required.
- **MCP (Model Context Protocol)** = connectivity layer. MCP servers give agents access to external systems: GitHub, databases, Stripe, filesystems. The "plumbing" that connects Claude to the outside world.
- **Plugins** = distribution layer. A plugin bundles one or more skills + optional hooks + MCP server configurations into a single installable package.

> "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

> "A typical five-server setup with 58 tools uses approximately 55,000 tokens before any conversation starts, though Anthropic's Tool Search feature reduces this by 85% through on-demand tool discovery." — [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)

The practical recommendation across most guides: most developers need 2-3 MCP servers (GitHub, Filesystem, one domain-specific) plus a few custom Skills. A Plugin is only needed when distributing to a team.

**Sources:** [morphllm.com](https://www.morphllm.com/claude-code-extensions), [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026), [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/), [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide), [tonykipkemboi.com](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)

---

### 3. Marketplace Explosion: From One Registry to Eight in Six Months

The ecosystem grew from one registry (December 2025) to eight major marketplaces by Q2 2026. Scale varies enormously by philosophy:

| Marketplace | Scale | Curation | Notes |
|-------------|-------|----------|-------|
| SkillsMP | 800,000+ skills | Minimal (2+ GitHub stars) | Scraped; quality varies |
| Skills.sh | ~2,000 skills | High (hand-curated) | Launched Jan 20, 2026; 20,000 installs in 6 hours |
| ClawHub | Part of 490k+ combined | Moderate | — |
| Claude.ai/settings/plugins | Official only | Anthropic-reviewed | Curated, quality-gated |
| MCP Market (mcpmarket.com) | Broad | Moderate | MCP-specific directory |
| Glama.ai | 22,775 MCP servers | Low | Fork/variant-heavy |
| MCPBundles | 10,000+ tools, 700+ providers | Production-grade | OAuth-first, credentials encrypted |
| agentskills.io | Reference/spec | Authoritative | Open trusted catalog |

> "SkillsMP's 800,000 number sounds impressive until you realize it's indexed public GitHub repos with no quality filter beyond 'has 2 stars.'" — [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/)

The top skill on Skills.sh is `find-skills` by Vercel Labs with **579,000+ installs** — a meta-skill for discovering other skills from within the agent.

**Sources:** [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [skills.sh](https://www.skills.sh/), [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/), [paperclipped.de](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/), [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

---

### 4. MCP Security Crisis — Production Readiness in Question

BlueRock Security's 2026 analysis of ~7,000 public MCP servers revealed alarming numbers:
- **36.7%** are SSRF-vulnerable
- **41%** require no authentication at all
- **53%** of authenticated servers rely solely on static API keys
- Only **8.5%** use OAuth

MCP Gateways have emerged as a response — an intermediary that sits between AI agents and MCP servers providing centralized auth, authorization, auditing, and traffic management. Notable gateway platforms: **MintMCP**, **ContextForge**, **Bifrost**. MCPBundles positions itself as a production-grade solution with credentials encrypted at rest and per-workspace scoping.

Separately, Anthropic announced **MCP Tunnels** (Research Preview, May 2026) — allowing Managed Agents to connect to private MCP servers without internet exposure via a lightweight gateway deploying an outbound encrypted connection.

> "MCP Tunnels are now available as a Research Preview, allowing you to connect to MCP servers in your private network." — [infoq.com](https://infoq.com/news/2026/05/claude-mcp-tunnels/)

**Sources:** [integrate.io](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/), [infoq.com](https://infoq.com/news/2026/05/claude-mcp-tunnels/), [bytebridge.medium.com](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a), [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers), [thenewstack.io](https://thenewstack.io/model-context-protocol-roadmap-2026/)

---

### 5. Anthropic Donates MCP to Open Governance Foundation

In a significant structural move, Anthropic donated the Model Context Protocol to an independent governance body — the Agentic AI Foundation. This signals that MCP's governance is intentionally being separated from any single vendor, mirroring how other foundational web standards are managed.

> [anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)

The Thomson Reuters + Anthropic partnership expansion (May 2026) connects Claude directly with CoCounsel Legal via MCP, illustrating enterprise adoption of the protocol beyond developer tooling.

**Sources:** [anthropic.com](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), [thomsonreuters.com](https://www.thomsonreuters.com/en/press-releases/2026/may/thomson-reuters-and-anthropic-expand-partnership-to-connect-claude-with-cocounsel-legal), [wikipedia.org/Model_Context_Protocol](https://en.wikipedia.org/wiki/Model_Context_Protocol)

---

### 6. Community-Built Tooling: CCPI, Awesome Lists, SaaS Packs

The community toolchain around skills/plugins has become substantial:

**CCPI (Claude Code Plugin CLI)** — npm package `@intentsolutionsio/ccpi` by jeremylongshore. Install with `pnpm add -g @intentsolutionsio/ccpi`. Marketplace: [tonsofskills.com](https://tonsofskills.com) with 425 plugins, 2,810 skills, 200 agents. Key commands: `ccpi search devops`, `ccpi install devops-automation-pack`, `ccpi validate ./your-plugin`. Supports Ollama compatibility for air-gapped/local model use. 42 SaaS skill packs covering 1,086 skills for specific platforms.

**Notable GitHub repositories:**
- [anthropics/skills](https://github.com/anthropics/skills) — Official Anthropic skills
- [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) — Curated official plugins
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) — 329 skills for Claude Code, Codex, Gemini CLI, Cursor + 8 more agents
- [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) — 1,000+ curated skills
- [ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) — Curated plugins list
- [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills) — Community-curated
- [skillmatic-ai/awesome-agent-skills](https://github.com/skillmatic-ai/awesome-agent-skills) — Cross-agent skills

**Sources:** [npmjs.com/ccpi](https://www.npmjs.com/package/@intentsolutionsio/ccpi), [blog.brightcoding.dev](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development), [github.com/jeremylongshore](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)

---

### 7. Hacker News: Skills "Maybe a Bigger Deal Than MCP"

HN has hosted the core debate — with multiple high-traction threads:

- [**"Claude Skills are awesome, maybe a bigger deal than MCP"**](https://news.ycombinator.com/item?id=45619537) — generated significant discussion comparing the two approaches
- [**"You don't need MCP. You need Claude Skills."**](https://news.ycombinator.com/item?id=45948490) — contrarian take driving debate
- [**"You've got your CLAUDE.md, Skills, Agents, MCP, slash commands..."**](https://news.ycombinator.com/item?id=46396930) — developer complexity/fatigue thread
- [**"Show HN: Agent37 – Monetize your Claude skills"**](https://news.ycombinator.com/item?id=46422134) — skills monetization via shareable links
- [**"Show HN: 1k curated Claude Code skills from 60k+ GitHub"**](https://news.ycombinator.com/item?id=46693426) — curation-as-value-add
- [**"I'm kind of in stitches... Skills are dependent on developer participation"**](https://news.ycombinator.com/item?id=45611559) — skeptical take on skills requiring active maintenance
- [**"Claude Managed Agents"**](https://news.ycombinator.com/item?id=47693047) — May 2026 announcement thread
- [**"Claude Skills"**](https://news.ycombinator.com/item?id=45607117) — original launch thread
- [**"Agent Skills – Open Trusted Catalog"**](https://news.ycombinator.com/item?id=46692865) — cross-provider catalog announcement
- [**"Show HN: Registry for curated, high quality Claude skills"**](https://news.ycombinator.com/item?id=46721900) — quality-filtered registry

---

### 8. Discovery as the Unsolved Problem

Despite explosive growth in skill counts, discovery remains the hard problem:

> "Shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." — [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

The meta-skill `find-skills` by Vercel Labs (579k+ installs) — a skill that helps you find other skills from within the agent — having the highest install count on Skills.sh is a telling signal. Discovery is being solved *through* the agents themselves, not through traditional search interfaces.

**Sources:** [agensi.io/how-marketplaces-work](https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work), [virtualuncle.com](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)

---

## Cross-Source Patterns

### Pattern 1: Skills gaining parity with MCP as primary extension mechanism
- **Platforms:** Hacker News, Web (multiple blogs), GitHub
- HN threads title themselves "Skills are a bigger deal than MCP" and "You don't need MCP. You need Claude Skills."
- Blog consensus: use MCP for external system access, Skills for behavioral/procedural knowledge
- Key quote: *"MCP is the plumbing; Skills are the instructions."* — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

### Pattern 2: Curation quality > raw catalog size
- **Platforms:** Web (smartscope.blog, agensi.io, inference.sh), HN (curated registries getting Show HN traction)
- SkillsMP's 800k+ unfiltered vs Skills.sh's 2k curated — community favoring curated
- Vercel's `find-skills` (579k installs) as the most-installed skill on the curated marketplace
- Key quote: *"SkillsMP's 800,000 number sounds impressive until you realize it's indexed public GitHub repos with no quality filter beyond 'has 2 stars.'"* — [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/)

### Pattern 3: MCP security is a genuine production blocker
- **Platforms:** Web (integrate.io, thenewstack.io, infoq.com)
- 41% no auth, 36.7% SSRF-vulnerable — consistent security audit findings
- Anthropic's MCP Tunnels + gateway products (MCPBundles, MintMCP) emerging as response
- Key quote: *"36.7% are SSRF-vulnerable, 41% require no authentication at all"* — BlueRock Security via [integrate.io](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/)

### Pattern 4: SKILL.md interoperability is real and happening fast
- **Platforms:** Web (paperclipped.de, agensi.io, thepromptindex.com), GitHub
- 32 competing tools now share the same format — OpenAI, Google, JetBrains, AWS, Block
- Anthropic donating MCP governance accelerating ecosystem trust
- Key quote: *"Within 48 hours [of publishing the spec], Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI."* — [agensi.io](https://www.agensi.io/learn/agent-skills-open-standard)

---

## Per-Platform Tables

**Hacker News:**
| User/Thread | Title | Points | Comments | Notable Quote | URL |
|-------------|-------|--------|----------|---------------|-----|
| Multiple | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | Widely cited in other articles | https://news.ycombinator.com/item?id=45619537 |
| Multiple | You don't need MCP. You need Claude Skills. | — | — | Contrarian pivot driving debate | https://news.ycombinator.com/item?id=45948490 |
| Multiple | You've got your CLAUDE.md, Skills, Agents, MCP... | — | — | Complexity fatigue signal | https://news.ycombinator.com/item?id=46396930 |
| Multiple | Show HN: Agent37 – Monetize your Claude skills | — | — | Skills monetization via shareable links | https://news.ycombinator.com/item?id=46422134 |
| Multiple | Agent Skills – Open Trusted Catalog | — | — | Cross-provider open catalog | https://news.ycombinator.com/item?id=46692865 |
| Multiple | Show HN: 1k curated Claude Code skills from 60k+ GitHub | — | — | Curation-as-moat | https://news.ycombinator.com/item?id=46693426 |
| Multiple | Show HN: Registry for curated, high quality Claude skills | — | — | Quality-filtered registry launch | https://news.ycombinator.com/item?id=46721900 |
| Multiple | I'm in stitches. Skills depend on developer participation | — | — | Skeptic of ecosystem sustainability | https://news.ycombinator.com/item?id=45611559 |
| Multiple | Claude Managed Agents | — | — | May 2026 managed agents launch | https://news.ycombinator.com/item?id=47693047 |
| Multiple | Claude Skills (original launch) | — | — | Original launch thread | https://news.ycombinator.com/item?id=45607117 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Unknown | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | — | https://www.youtube.com/watch?v=uogzSxOw4LU |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | 6,700+ skills, 840+ MCP servers indexed |
| Claude Code Docs (skills) | https://code.claude.com/docs/en/skills | Official skill documentation |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Plugin system overview |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| agensi.io (plugin marketplace guide) | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Official + community marketplaces breakdown |
| morphllm.com (extensions) | https://www.morphllm.com/claude-code-extensions | Skills/MCP/Plugins decision guide |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, CCPI CLI |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Community resource aggregator |
| anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | Official Anthropic plugin directory |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 tools rankings |
| toloka.ai | https://toloka.ai/blog/best-mcp-servers-for-ai-agents/ | 22,775 MCP servers on Glama (May 2026) |
| Microsoft Learn | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Microsoft MCP agent integration |
| mcpmarket.com | https://mcpmarket.com/ | MCP server directory |
| aiagentslist.com | https://aiagentslist.com/mcp-servers | 593+ curated MCP servers |
| analyticsvidhya.com | https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/ | Top 10 MCP servers for builders |
| bytebridge.medium.com | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | Top MCP gateway platforms |
| mcpbundles.com | https://www.mcpbundles.com/blog/best-mcp-servers | 10,000+ tools, OAuth-first, encrypted creds |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-mcp-servers-for-developers | Developer MCP server rankings |
| k2view.com | https://www.k2view.com/blog/awesome-mcp-servers | Top 15 MCP servers |
| integrate.io | https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/ | MCP security stats (36.7% SSRF-vuln) |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | 8 key marketplaces, discovery challenges |
| paperclipped.de (skills marketplace) | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | Marketplace comparison, 490k+ combined |
| calmops.com | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | Complete skills guide 2026 |
| tonykipkemboi.com | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | Skills vs plugins distinction |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Skills/plugins/marketplace complete guide |
| agensi.io (marketplace comparison) | https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026 | Marketplace head-to-head |
| explainx.ai | https://www.explainx.ai/blog/dotnet-skills-ai-agents-complete-guide-2026 | Microsoft Dotnet skills repo |
| agensi.io (open standard) | https://www.agensi.io/learn/agent-skills-open-standard | Anthropic published spec Dec 18, 2025 |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official API docs for agent skills |
| agensi.io (SKILL.md spec) | https://www.agensi.io/learn/skill-md-specification-open-standard | Full SKILL.md specification |
| paperclipped.de (interoperability) | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | 32 tools now support SKILL.md (March 2026) |
| thepromptindex.com | https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html | Security guide for skills |
| agentskills.io/specification | https://agentskills.io/specification | Official specification |
| medium.com/@unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | Top skills list |
| buildfastwithai.com | https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026 | Build, install & use guide |
| jeremylongshore SKILL.md wiki | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/wiki/SKILL-md-Specification | Community spec docs |
| releasebot.io (Anthropic) | https://releasebot.io/updates/anthropic | Anthropic release notes tracker |
| thomsonreuters.com | https://www.thomsonreuters.com/en/press-releases/2026/may/thomson-reuters-and-anthropic-expand-partnership-to-connect-claude-with-cocounsel-legal | TR+Anthropic MCP partnership |
| tokenmix.ai | https://tokenmix.ai/blog/mcp-updates-changelog-every-protocol-change-2026 | MCP changelog |
| releasebot.io (Claude Code) | https://releasebot.io/updates/anthropic/claude-code | Claude Code May 2026 updates |
| anthropic.com (donate MCP) | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | MCP donated to Agentic AI Foundation |
| ainetizens.com | https://ainetizens.com/anthropic-mcp-model-context-protocol-explained-2026/ | 7 key MCP shifts in 2026 |
| anthropic.com (original MCP) | https://www.anthropic.com/news/model-context-protocol | Original MCP announcement |
| infoq.com | https://infoq.com/news/2026/05/claude-mcp-tunnels/ | MCP Tunnels Research Preview (May 2026) |
| wikipedia.org | https://en.wikipedia.org/wiki/Model_Context_Protocol | MCP overview |
| thenewstack.io | https://thenewstack.io/model-context-protocol-roadmap-2026/ | MCP roadmap 2026 |
| devtoolpicks.com | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | "MCP is plumbing; Skills are instructions" |
| morphllm.com (comparison) | https://www.morphllm.com/claude-code-skills-mcp-plugins | 55k tokens for 5-server MCP setup |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | MCP + plugins complete guide |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Curated recommendations |
| sankalp.bearblog.dev | https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/ | First-person Claude Code 2.0 experience |
| mcpmarket.com (HN skill) | https://mcpmarket.com/tools/skills/hacker-news-agent | Example skill listing |
| GetBindu/awesome-claude-code-and-skills | https://github.com/GetBindu/awesome-claude-code-and-skills | Community skills collection |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 329 cross-agent skills |
| anthropics/claude-code (plugins README) | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Official plugin docs |
| anthropics/skills | https://github.com/anthropics/skills | Official Anthropic skills repo |
| levnikolaevich/claude-code-skills | https://github.com/levnikolaevich/claude-code-skills | Plugin suite with custom MCP servers |
| daymade/claude-code-skills | https://github.com/daymade/claude-code-skills/blob/main/CLAUDE.md | 53 production-ready skills |
| ComposioHQ/awesome-claude-skills | https://github.com/ComposioHQ/awesome-claude-skills | 1,000+ production skills |
| travisvn/awesome-claude-skills | https://github.com/travisvn/awesome-claude-skills | Community-curated list |
| Jamie-BitFlight/claude_skills | https://github.com/Jamie-BitFlight/claude_skills | Plugin dev skills |
| agensi.io (best marketplaces) | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | All major marketplaces 2026 |
| agentskills.io/home | https://agentskills.io/home | Official specification home |
| smartscope.blog | https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ | SkillsMP review (800k+ skills) |
| virtualuncle.com | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | Skills.sh guide |
| agensi.io (how marketplaces work) | https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work | Marketplace mechanics |
| termdock.com | https://www.termdock.com/en/blog/agent-skills-guide | Build, share & secure guide |
| skillmatic-ai/awesome-agent-skills | https://github.com/skillmatic-ai/awesome-agent-skills | Cross-agent skills resource |
| paperclipped.de (marketplace) | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | 490k+ skills across 3 marketplaces |
| skills.sh | https://www.skills.sh/ | Live curated skills directory |
| inference.sh | https://inference.sh/blog/skills/agent-skills-overview | Open standard overview |
| npmjs.com/ccpi | https://www.npmjs.com/package/@intentsolutionsio/ccpi | CCPI npm package |
| blog.brightcoding.dev | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | Claude Code Plugins Plus (Feb 7, 2026) |
| code.claude.com/docs/en/plugins | https://code.claude.com/docs/en/plugins | Official plugin creation docs |
| YouTube guide | https://www.youtube.com/watch?v=uogzSxOw4LU | The Ultimate Claude Code Guide (Apr 13, 2026) |
| composio.dev | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP integration |
| code.claude.com/docs/en/agent-sdk/mcp | https://code.claude.com/docs/en/agent-sdk/mcp | Official MCP docs |
| blakecrosley.com | https://blakecrosley.com/guides/claude-code | Claude Code CLI complete guide |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full stack architecture explanation |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded from query)
├─ 🔵 X: 0 posts (excluded from query)
├─ 🔴 YouTube: 1 video | views unknown
├─ 🟢 HN: 10 threads | points/comments not scraped
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 55+ pages
└─ 🗣️ Top voices: @unicodeveloper (Medium), @jeremylongshore (GitHub) │ r/ClaudeAI (not captured)
```

---

## Data Gaps

- **Reddit not captured:** Reddit was excluded from WebSearch queries per research instructions. The last30days skill was launched but the Reddit/X/TikTok/Instagram/Bluesky/Polymarket pipeline components did not produce structured platform-specific outputs in this run. Community discussion on r/ClaudeAI, r/LocalLLaMA, r/programming is likely highly active given the topic relevance.
- **X/Twitter not captured:** Excluded per instructions. Developer influencers on X are major amplifiers for skills/MCP content.
- **YouTube limited:** Only 1 video found via web search; dedicated YouTube search via API would surface more tutorials.
- **HN engagement numbers missing:** Thread points and comment counts not scraped — only URLs captured.
- **Skill install numbers limited:** Only Skills.sh top-skill data found; SkillsMP/ClawHub install counts not available.
- **Approximate coverage:** ~75% of web/docs/GitHub surface covered; ~10% of social signal captured (HN threads only).

---

## Key Quotes

> "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

> "By March 2026, 32 tools from competing companies, including Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose, all read the same SKILL.md files from the same directory structure." — [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

> "Within 48 hours [of publishing the spec], Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI." — [agensi.io](https://www.agensi.io/learn/agent-skills-open-standard)

> "SkillsMP's 800,000 number sounds impressive until you realize it's indexed public GitHub repos with no quality filter beyond 'has 2 stars.'" — [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/)

> "A typical five-server setup with 58 tools uses approximately 55,000 tokens before any conversation starts, though Anthropic's Tool Search feature reduces this by 85%." — [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)

> "Shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." — [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

> "36.7% are SSRF-vulnerable, 41% require no authentication at all, 53% of authenticated servers rely on static API keys, and only 8.5% use OAuth." — BlueRock Security via [integrate.io](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/)

> "Shipping the agent is solved; getting it surfaced in a marketplace is the hard part." — [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

> "MCP Tunnels are now available as a Research Preview, allowing you to connect to MCP servers in your private network without exposing them to the public internet." — [infoq.com](https://infoq.com/news/2026/05/claude-mcp-tunnels/)

> "Claude Skills are awesome — maybe a bigger deal than MCP." — [Hacker News](https://news.ycombinator.com/item?id=45619537)
