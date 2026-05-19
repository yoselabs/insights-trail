# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-19
**Query type:** GENERAL
**Sources:** Web, Hacker News, YouTube, TikTok, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 5 threads | 96 points, 32+ comments | 1 high-traction thread (77pts); 4 low-traction |
| YouTube | 3 videos | N/A | MCP + skills tutorials, April 2026 |
| TikTok | 2 videos | N/A | MCP tutorials, EN + FR creators |
| Web | 80+ pages | — | via WebSearch; blogs, official docs, news, security research |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard — Origin, Structure, and Explosive Adoption

Anthropic first shipped Agent Skills as a Claude Code feature on **October 16, 2025**, then released the format as a full **open standard on December 18, 2025** via [agentskills.io](https://agentskills.io/). The specification was simultaneously donated to the **Agentic AI Foundation (AAIF)**, a Linux Foundation-backed alliance, explicitly to prevent proprietary lock-in.

A SKILL.md file is a markdown document with YAML frontmatter. The required fields are `name` and `description`. Optional supporting directories (`scripts/`, `references/`, `assets/`) allow bundling executables and templates. The design employs **"progressive disclosure"**: only 30–50 tokens per skill are loaded at session start (name + description); full instructions activate on demand. An agent with 50 installed skills consumes just 1,500–2,500 tokens at startup — a contrast to MCP's 55,000-token overhead for a 5-server/58-tool setup.

Key statistics from a February 2026 academic study of 40,285 publicly listed skills:
- Ecosystem grew **18.5× in 20 days** (Jan 16 → Feb 5, 2026: 2,179 → 40,000+ skills)
- Median skill body: **1,414 tokens**
- 55% of published skills target software engineering workflows
- 46% of skills share a name with at least one other skill (discovery/collision problem)
- ~40% of published skills access sensitive context or perform writes
- 9% fall in the critical risk category

By May 2026, a **single SKILL.md runs identically on 26+ platforms** — including Claude Code, OpenAI Codex CLI, Google Gemini CLI, GitHub Copilot (VS Code), Cursor, Windsurf, OpenClaw, Cline, and OpenCode — without modification.

**Sources (Web):** [Anthropic Engineering](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills), [agentskills.io](https://agentskills.io/), [firecrawl.dev SKILL.md guide](https://www.firecrawl.dev/blog/agent-skills), [agensi.io: What Is SKILL.md](https://www.agensi.io/learn/what-is-skill-md), [agensi.io: Open Standard](https://www.agensi.io/learn/agent-skills-open-standard), [Mintlify: skill.md](https://www.mintlify.com/blog/skill-md), [Medium deep dive](https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996), [inference.sh overview](https://inference.sh/blog/skills/agent-skills-overview), [Strapi guide](https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them), [termdock guide](https://www.termdock.com/en/blog/agent-skills-guide), [bishoylabib.com](https://www.bishoylabib.com/posts/claude-skills-comprehensive-guide), [Medium @nayakpplaban](https://medium.com/@nayakpplaban/agent-skills-standard-for-smarter-ai-bde76ea61c13)

---

### 2. Industry Adoption — From Anthropic to the Full Stack

Adoption of the Agent Skills standard was unusually fast for an infrastructure specification. At the December 2025 launch, **Microsoft, OpenAI, Atlassian, Figma, Cursor, and GitHub** adopted the standard, with partner-built skills from **Canva, Stripe, Notion, and Zapier** available on day one.

VS Code added native Agent Skills support: [code.visualstudio.com/docs/copilot/customization/agent-skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills).

Vercel launched [skills.sh](http://skills.sh) on **January 20, 2026** as an open leaderboard and distribution point. Before Q1 2026 ended, official skill packages were live from **Prisma, Supabase, Stripe, Remotion, Coinbase, and Microsoft** — analogous to the "blessed package" tier in npm.

Headline benchmark: *"npm took a decade to reach 350,000 packages. The AI agent skills ecosystem did it in about two months."* — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

**Sources (Web):** [VentureBeat launch coverage](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard), [The Decoder](https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/), [Unite.AI](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/), [aibusiness.com](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude), [FinancialContent](https://www.financialcontent.com/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability), [Vercel changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem), [Vercel docs](https://vercel.com/docs/agent-resources/skills), [VS Code docs](https://code.visualstudio.com/docs/copilot/customization/mcp-servers), [Medium @evoailabs](https://medium.com/@evoailabs/agent-skills-are-open-standard-can-be-used-with-any-llm-agent-feb0cba4e0ff), [skills.sh guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/), [solobusinesshub trend watch](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/)

---

### 3. The Marketplace Landscape — Eight Competing Registries

A competitive marketplace ecosystem emerged at speed, with eight significant registries in play by April 2026. Each reflects a different philosophy:

| Registry | Skills | Curation Model | Security Scan | Creator Payments |
|----------|--------|----------------|---------------|------------------|
| [SkillsMP](https://skillsmp.com/) | 425,000+ | GitHub scrape (≥2 stars) | None | No |
| [LobeHub](https://lobehub.com/skills) | 169,739 | Aggregated + community ratings | None | No |
| [agentskill.sh](http://agentskill.sh) | 110,000+ | Multi-tool indexing | Security score | No |
| [skills.sh (Vercel)](http://skills.sh) | 87,000 | Open leaderboard | None | No |
| [ClawHub](https://clawhub.ai/) | 20,000+ | OpenClaw official registry | Partial | No |
| [Anthropic official](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) | ~20 | Manually verified | Full | No |
| [MCP Market](https://mcpmarket.com/) | ~500 | Submission-based | Partial | No |
| [Agensi](https://www.agensi.io/) | 200+ | Manual + automated, 8-point scan | Full | Yes (80/20) |

**Installation patterns vary:**
- `npx skills add [author]/[skill-name]` (skills.sh / Vercel)
- `npx -y @lobehub/market-cli skills install [skill] --agent claude-code` (LobeHub)
- `ccpi install [plugin-name]` (tonsofskills.com)
- `npx clawhub@latest install [skill]` (ClawHub)

The only marketplace offering paid skills in April 2026 is **Agensi** (80/20 revenue split). Multiple sources predict at least two additional free platforms will add paid tiers before year-end.

**Search volume signal:** monthly searches for agent skills–related terms grew **19× in two years** (21,000 → 400,000+).

**Sources (Web):** [KDNuggets Top 5](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents), [agensi.io best comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [agensi.io marketplace comparison](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026), [agensi.io skills explained](https://www.agensi.io/learn/ai-agent-skills-explained-complete-guide), [agensi.io skills marketplace](https://www.agensi.io/learn/skills-marketplace-ai-agents), [claudemarketplaces.com](https://claudemarketplaces.com/), [agensi.io plugin guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide), [openaitoolshub comparison](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison), [brightcoding.dev](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers), [creator monetization guide](https://www.agensi.io/learn/agent-skills-marketplace-sell-your-skills), [buildmvpfast.com npm analogy](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026), [chris-ayers.com complete guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/), [litellm plugin marketplace](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace)

---

### 4. Skills vs. MCP vs. Plugins — The Architecture Taxonomy

A recurring theme across tutorials, blog posts, and HN threads is confusion over the three extension types. The clearest synthesis:

- **Skills** = Markdown instruction files (SKILL.md) that teach Claude *how* to do something. Invoke via slash command or auto-activated on context match. Token-efficient (30–50 tokens until needed). Cross-platform portable.
- **MCP Servers** = External process exposing tools over the Model Context Protocol. Gives Claude *access* to things (databases, GitHub, Slack, APIs). High token overhead (~55K for a typical setup, reducible 85% via Tool Search). Stateful, process-boundary isolation.
- **Plugins** = Distribution format. Bundle one or more skills + optional MCP server configs + hooks. The unit of installation from a marketplace.

Key distinction: *"MCP is the plumbing that connects Claude to the outside world; skills are the instructions that teach Claude how to do specific things."* — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

Most developers are advised to maintain **2–3 MCP servers** (GitHub, Filesystem, one domain-specific) plus a few custom skills for repeatable workflows. Over-installing MCP servers is the most common performance mistake.

**Sources (Web):** [Towards AI extensions explainer](https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff), [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins), [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026), [devops-daily.com](https://devops-daily.com/posts/claude-code-agents-commands-skills-plugins-explained), [nimbalyst plugins guide](https://nimbalyst.com/blog/claude-code-plugins-guide/), [nimbalyst MCP guide](https://nimbalyst.com/blog/best-claude-code-mcp-servers/), [MindStudio skills vs plugins](https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference), [MCP official docs](https://code.claude.com/docs/en/mcp), [discover plugins docs](https://code.claude.com/docs/en/discover-plugins), [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers), [systemprompt.io MCP guide](https://systemprompt.io/guides/claude-code-mcp-servers-extensions), [claudefa.st MCP addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons), [buildfastwithai MCP guide](https://www.buildfastwithai.com/blogs/claude-mcp-setup-guide-2026), [fast.io MCP plugins](https://fast.io/resources/claude-mcp-plugins/), [agensi.io plugins vs skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained)

---

### 5. MCP Desktop Extensions — One-Click Install Format

A significant UX improvement landed in late 2025: the **Desktop Extension** (.mcpb) format, open-sourced at [github.com/modelcontextprotocol/mcpb](https://github.com/modelcontextprotocol/mcpb). A `.mcpb` file is a zip archive containing the full MCP server, all dependencies, and a `manifest.json`. Users click "Install Extension…" and select the file — no terminal, no config editing, no dependency conflicts.

The `.dxt` and `.mcpb` names refer to the same format (Anthropic renamed `.dxt` → `.mcpb` in late 2025 to match MCP Bundle branding); both extensions are accepted. Microsoft has shipped the Azure MCP server as a `.mcpb` package.

**Sources (Web):** [Anthropic Desktop Extensions](https://www.anthropic.com/engineering/desktop-extensions), [desktopextensions.com](https://www.desktopextensions.com/), [modelcontextprotocol/mcpb GitHub](https://github.com/modelcontextprotocol/mcpb), [mcpfind.org guide](https://mcpfind.org/blog/installing-mcp-desktop-extensions-mcpb), [Azure SDK blog](https://devblogs.microsoft.com/azure-sdk/azure-mcp-server-mcpb-support/), [Claude Desktop getting started](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop), [DEV.to build guide](https://dev.to/anh_nguyen_589e1928a98305/from-api-key-to-one-click-install-building-a-claude-desktop-extension-for-agentshare-1e31), [ClaudeDesktopExtension GitHub](https://github.com/vinod-eng/ClaudeDesktopExtension)

---

### 6. Security Crisis — Supply Chain Poisoning and MCP Vulnerabilities

The rapid growth of unmoderated skill registries created a serious security crisis that peaked in Q1 2026. Multiple concurrent attack vectors are active:

**Snyk ToxicSkills Audit (February 2026):**
- 3,984 skills scanned → 1,467 malicious payloads found (36% flaw rate)
- 76 confirmed malicious skills with active payloads
- 534 (13.4%) contain critical-level issues including malware distribution, prompt injection, exposed secrets
- Source: [snyk.io/blog/toxicskills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)

**ClawHub Registry Poisoning:**
- First AI registry systematically poisoned at scale
- 5 of the top 7 most-downloaded skills at peak confirmed as malware
- Antiy CERT confirmed 1,184 malicious skills
- Sources: [owasp.org agentic skills top 10](https://owasp.org/www-project-agentic-skills-top-10/), [agensi.io security crisis](https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026), [obot.ai supply chain](https://obot.ai/blog/mcp-security-agent-skills-supply-chain/), [cyberdesserts.com OpenClaw](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/)

**Claude Code CVEs (Check Point Research):**
- CVE-2025-59536 (CVSS 8.7): RCE via pre-trust hook execution and MCP consent bypass — malicious code runs before trust dialogs appear
- CVE-2026-21852 (CVSS 5.3): API key exfiltration through ANTHROPIC_BASE_URL manipulation
- Source: [research.checkpoint.com](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/), [mintmcp.com CVE guide](https://www.mintmcp.com/blog/claude-code-cve)

**MCP Protocol Vulnerabilities:**
- OX Security: systemic RCE vulnerability at the core of MCP enabling Arbitrary Command Execution on any vulnerable MCP implementation
- Mitiga: silent OAuth token theft via MCP traffic redirect
- Trend Micro: 492 MCP servers exposed to the internet with zero authentication
- Anthropic's Git MCP server: 3 CVEs in January 2026 (path traversal, argument injection)
- Sources: [ox.security](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/), [securityweek.com OAuth](https://www.securityweek.com/claude-code-oauth-tokens-can-be-stolen-through-stealthy-mcp-hijacking/), [darkreading.com TrustFall](https://www.darkreading.com/application-security/trustfall-exposes-claude-code-execution-risk), [obot.ai leak crisis](https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/), [cyberdesserts.com AI risks](https://blog.cyberdesserts.com/ai-agent-security-risks/)

**Novel Attack Technique — DDIPE:**
- Document-Driven Implicit Payload Execution: embeds malicious logic inside code examples within skill documentation; bypass rates 11.6%–33.5% across configurations
- Source: [ismalicious.com](https://ismalicious.com/posts/mcp-security-risks-tool-poisoning-ai-agents), [practical-devsecops.com](https://www.practical-devsecops.com/mcp-security-vulnerabilities/)

**OWASP Response:**
- OWASP Top 10 for Agentic Applications 2026 (December 2025), 100+ peer reviewers
- ASI01 Agent Goal Hijacking (#1 risk), principle of Least Agency as core defense
- Microsoft published Copilot Studio guidance March 30, 2026
- Sources: [genai.owasp.org](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/), [microsoft.com security blog](https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/), [practical-devsecops.com OWASP](https://www.practical-devsecops.com/owasp-top-10-agentic-applications/), [practical-devsecops.com MCP guide](https://www.practical-devsecops.com/mcp-security-guide/), [aikido.dev OWASP](https://www.aikido.dev/blog/owasp-top-10-agentic-applications), [startupdefense.io](https://www.startupdefense.io/blog/owasp-top-10-agentic-ai-security-risks-2026), [auth0.com](https://auth0.com/blog/owasp-top-10-agentic-applications-lessons/), [trydeepteam.com](https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications), [nhimg.org](https://nhimg.org/complete-guide-to-the-2026-owasp-top-10-risks-for-agentic-applications), [kenhuangus/agentic-skills-top-10](https://github.com/kenhuangus/agentic-skills-top-10)

**Academic research:** [arxiv.org 2603.16572](https://arxiv.org/pdf/2603.16572) — "Malicious Or Not: Adding Repository Context to Agent Skill Classification"

---

### 7. Community GitHub Collections — The Curation Layer

With 400,000+ skills across registries, curation has become its own sub-ecosystem. Key hand-curated GitHub lists as of May 2026:

- **[hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)** — 36.8k stars; canonical hand-curated list; covers skills, agents, hooks, status lines, orchestrators, and the full Claude Code feature surface; high quality bar, security-conscious
- **[ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)** — 1,000+ production-ready skills across Claude Code, Codex, Cursor, Gemini CLI
- **[Chat2AnyLLM/awesome-claude-skills](https://github.com/Chat2AnyLLM/awesome-claude-skills)** — 9,864 skills as of 2026-05-06
- **[Samarth0211/awesome-claude-skills-2026](https://github.com/Samarth0211/awesome-claude-skills-2026)** — 2,300+ skills with search, filters, and one-click download at clskills.in
- **[VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)** — 1,000+ skills from official dev teams, multi-platform
- **[netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace)** — Enterprise-focused curated skills (security audit, enterprise readiness, git workflow, Jira), agentskills.io portable, 30+ agents
- **[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)** — 313+ skills across engineering, marketing, product, compliance, C-level advisory
- **[jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)** — 425 plugins, 2,810 skills, 200 agents; tonsofskills.com; ccpi CLI

Other collections: [travisvn/awesome-claude-skills](https://github.com/travisvn/awesome-claude-skills), [BehiSecc/awesome-claude-skills](https://github.com/BehiSecc/awesome-claude-skills), [GetBindu/awesome-claude-code-and-skills](https://github.com/GetBindu/awesome-claude-code-and-skills)

Companion sites: [claudeskills.info/best/](https://claudeskills.info/best/), [claudefa.st awesome list roundup](https://claudefa.st/blog/tools/resources/awesome-claude-code), [chat2anyllm.github.io/awesome-claude-skills/](https://chat2anyllm.github.io/awesome-claude-skills/)

---

### 8. Hacker News Community Signals

Five HN threads directly touch this space in the last 30 days:

**High traction:**
- **[Show HN: Real-time dashboard for Claude Code agent teams](https://news.ycombinator.com/item?id=47602986)** (77 pts, 28 comments, ~47 days ago, by simple10 — [github.com/simple10/agents-observe](https://github.com/simple10/agents-observe))
  - Core problems surfaced: (1) agent opacity — teams can't see what agents are doing beyond activity summaries; (2) "sanitised optimism" — Claude reports success while silencing errors; (3) blocking hooks compound latency ("even a few hundred milliseconds per hook call compounds fast"); (4) some teams spend thousands/day on Claude tokens; personal users ($20-$200 plans) struggle with limits.

**Low traction but signal-rich:**
- **[Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills](https://news.ycombinator.com/item?id=46693426)** (4 pts, 2 comments, by lixiaofei)
  - Top commenter (ricardobeat) challenged curation: "The top 30 results I see here are other skill collection libraries or skill generators." Tension between stated curation goals and delivery.
- **[Show HN: Yet another Claude Code agent setup, but several novel patterns](https://news.ycombinator.com/item?id=47463371)** (1 pt, by AndyNemmity)
  - Commenter (angtly) raised unsolved gap: "Every agent framework solves orchestration well, but none of them answer: what happens when Agent A needs to hire Agent B for a capability it doesn't have?" Proposed per-call billing for specialist agents.
- **[Show HN: Almanac MCP, turn Claude Code into a Deep Research agent](https://news.ycombinator.com/item?id=47855284)** (14 pts, by rohans0509)
  - Free web research MCP (general search, Reddit search, scraping); install via `npx openalmanac setup`.
- **[Ask HN: Best option for hosted agent in 2026?](https://news.ycombinator.com/item?id=46917293)**

Additional context: [DEV.to: Claude Code hit #1 on HN](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74), [developersdigest.tech HN analysis](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

---

### 9. YouTube & Video Coverage

Three notable YouTube pieces from April–May 2026:

- **[The Ultimate Claude Code Guide | MCP, Skills & More](https://www.youtube.com/watch?v=uogzSxOw4LU)** (April 13, 2026) — comprehensive walk-through of the full extension stack
- **[How I Actually Use Claude Every Day in 2026](https://www.youtube.com/watch?v=EZcYjH3jAo8)** — practitioner workflow covering Skills, Connectors, MCP Services, Claude Co-work
- **[Claude Code Tutorial Playlist](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY)** — multi-episode series on Claude Code fundamentals through MCP/subagent orchestration
- **Udemy course:** [Agent Skills: Claude Code, Cursor and MCP in Practice](https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/)

Platform integrations that are themselves skills: [Watch YouTube skill](https://mcpmarket.com/tools/skills/watch-youtube) (Composio), [YouTube MCP for Claude Code](https://composio.dev/toolkits/youtube/framework/claude-code)

---

### 10. TikTok Coverage

- **[@rileybrown.ai — CLAUDE MCP TUTORIAL](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559)**: EN-language tutorial on Claude as AI agent using MCP, demonstrates Notion MCP integration, thumbnail generation, system prompt setup, tool selection.
- **[@unefille.ia — MCP tutorial (FR)](https://www.tiktok.com/@unefille.ia/video/7488008313704172822)**: French-language introduction to MCP and AI agents.

Niche skills for TikTok itself: [TikTok Content Strategy skill](https://mcpmarket.com/tools/skills/tiktok-content-strategy) (Hook-Value-CTA formula, algorithm strategy), [TikTok Automation skill](https://claudskills.com/skills/tiktok-automation/), [TikTok MCP for Claude Code](https://composio.dev/toolkits/tiktok/framework/claude-code) (profile analytics, video management, publishing).

Guide: [Building a TikTok Content Factory with Claude Code](https://stormy.ai/blog/building-tiktok-content-factory-claude-code)

---

### 11. Polymarket & Prediction Market Integration (Niche)

AI agents accessing prediction markets via MCP emerged as a niche but active theme:
- [SimpleFunctions Polymarket MCP](https://conare.ai/marketplace/mcp/polymarket-mcp): 29 tools, 9,706+ active contracts on Kalshi + Polymarket
- [Graph Polymarket MCP](https://conare.ai/marketplace/mcp/graph-polymarket): 20 tools for market data, trader P&L, positions
- [Polymarket skill](https://mcpmarket.com/tools/skills/polymarket-development-suite)
- Social media claims about Claude-based bots earning large sums (March 2026 viral); on-chain reality: 92.4% of wallets lose money, arbitrage windows at 2.7s average
- Sources: [sparkco.ai guide](https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi), [Medium @weare1010](https://medium.com/@weare1010/claude-ai-trading-bots-are-making-hundreds-of-thousands-on-polymarket-2840efb9f2cd), [Polymarket AI predictions](https://polymarket.com/predictions/ai)

---

## Cross-Source Patterns

### Pattern 1: Skills as the New App Store — Explosive but Unmoderated Growth
**Platforms:** Web (universal), Hacker News, YouTube
- The "npm moment" framing appears across 5+ independent sources. Growth from ~200 skills (Jan 2026) to 400,000+ (Apr 2026) happened in ~90 days.
- The HN curation thread (lixiaofei) drew immediate skepticism about quality: *"The top 30 results I see here are other skill collection libraries or skill generators."* — ricardobeat
- The unmoderated growth directly enabled the ToxicSkills security crisis (Snyk, Feb 2026).

### Pattern 2: Security is the Ecosystem's Existential Risk
**Platforms:** Web (security research), Hacker News
- Multiple concurrent attack vectors: CVEs in Claude Code itself (Check Point), poisoned registries (Snyk/ClawHub), OAuth hijacking (Mitiga), systemic MCP RCE (OX Security), 492 zero-auth servers (Trend Micro).
- Only Agensi runs a meaningful 8-point security scan. The three largest registries (SkillsMP, skills.sh, LobeHub) do not.
- OWASP responded with a dedicated framework (Agentic Skills Top 10) within the same month the standard launched.
- Key quote: *"Your Engineers Gave Claude Root Access. Do You Know What It Did Next?"* — [Medium @katy-thomas](https://medium.com/@katy-thomas/your-engineers-gave-claude-root-access-do-you-know-what-it-did-next-846d34eca5c1)

### Pattern 3: The Unsolved Agent Composition Problem
**Platforms:** Hacker News, Web
- The HN comment from angtly (Show HN: novel agent setup) articulates a gap that no framework has solved: *"Every agent framework solves orchestration well, but none of them answer: what happens when Agent A needs to hire Agent B for a capability it doesn't have?"*
- This "economic layer for agents" idea — per-call billing for specialist capabilities — is not implemented in any current marketplace.
- The Almanac MCP thread and the dashboard thread both circle the same theme: agents operating autonomously but opaquely.

### Pattern 4: Progressive Disclosure as the Key Design Insight
**Platforms:** Web (Anthropic engineering, tutorials), Hacker News
- The SKILL.md architecture's core innovation — loading only 30-50 tokens at startup vs. MCP's 55,000-token overhead — is mentioned across independent sources.
- The HN dashboard thread confirmed the performance stakes: "anything blocking in the agent's critical path kills throughput."
- Skills are context-activated; MCP is always-on. This distinction shapes architecture decisions.

### Pattern 5: Monetization Infrastructure is Lagging Distribution
**Platforms:** Web
- Vercel's skills.sh (biggest distribution platform) offers no creator payments.
- Only Agensi offers a paid marketplace (80/20 split). Multiple analysts predict 2+ platforms add paid tiers before year-end.
- Search volume for "sell AI skills" and related terms is growing but infrastructure remains immature.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|---------------|-----|
| simple10 | Show HN: Real-time dashboard for Claude Code agent teams | 77 | 28 | "Claude kept reporting success when it just silenced the error." | [link](https://news.ycombinator.com/item?id=47602986) |
| rohans0509 | Show HN: Almanac MCP, turn Claude Code into a Deep Research agent | 14 | — | "npx openalmanac setup" (free web research MCP) | [link](https://news.ycombinator.com/item?id=47855284) |
| lixiaofei | Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills | 4 | 2 | "they lower the barrier so more people (including beginners) can use them" | [link](https://news.ycombinator.com/item?id=46693426) |
| AndyNemmity | Show HN: Yet another Claude Code agent setup, but several novel patterns | 1 | 1 | "what happens when Agent A needs to hire Agent B for a capability it doesn't have?" | [link](https://news.ycombinator.com/item?id=47463371) |
| — | Ask HN: Best option for hosted agent in 2026? | — | — | — | [link](https://news.ycombinator.com/item?id=46917293) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | N/A | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| — | How I Actually Use Claude Every Day in 2026 | — | — | N/A | [link](https://www.youtube.com/watch?v=EZcYjH3jAo8) |
| — | Claude Code Tutorial (playlist) | — | — | N/A | [link](https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY) |

**TikTok:**
| Creator | Caption Snippet | Views | Likes | URL |
|---------|----------------|-------|-------|-----|
| @rileybrown.ai | "CLAUDE MCP TUTORIAL — Claude is an AI Agent! Both 4 Sonnet and 4 Opus…" | — | — | [link](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559) |
| @unefille.ia | "Tutoriel: créer un agent IA gratuit avec Claude et les MCP…" | — | — | [link](https://www.tiktok.com/@unefille.ia/video/7488008313704172822) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Official Agent Skills announcement, technical spec, progressive disclosure architecture |
| agentskills.io | [link](https://agentskills.io/) | Open standard portal, AAIF governance |
| Anthropic Desktop Extensions | [link](https://www.anthropic.com/engineering/desktop-extensions) | .mcpb one-click install format overview |
| VentureBeat | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Enterprise launch coverage, competitive context |
| The New Stack | [link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Standards competition analysis |
| The Decoder | [link](https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/) | Platform adoption breakdown |
| Snyk ToxicSkills | [link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | Feb 2026 audit: 36% flaw rate, 1,467 malicious payloads |
| Check Point Research | [link](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/) | CVE-2025-59536 RCE + API key exfiltration analysis |
| OX Security | [link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | Systemic MCP RCE vulnerability |
| SecurityWeek | [link](https://www.securityweek.com/claude-code-oauth-tokens-can-be-stolen-through-stealthy-mcp-hijacking/) | OAuth token theft via MCP hijacking |
| Dark Reading | [link](https://www.darkreading.com/application-security/trustfall-exposes-claude-code-execution-risk) | TrustFall execution risk |
| OWASP Agentic Skills | [link](https://owasp.org/www-project-agentic-skills-top-10/) | Top 10 for Agentic Applications 2026 |
| OWASP Gen AI | [link](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) | Full 2026 framework |
| KDNuggets | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 marketplace comparison |
| agensi.io best marketplaces | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 8-marketplace comparison with security analysis |
| firecrawl.dev SKILL.md | [link](https://www.firecrawl.dev/blog/agent-skills) | SKILL.md technical deep dive, Feb 2026 ecosystem stats |
| Vercel changelog | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | skills.sh launch January 2026 |
| Vercel docs | [link](https://vercel.com/docs/agent-resources/skills) | Official Vercel skills documentation |
| Vercel KB | [link](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context) | Creating, installing, sharing guide |
| buildmvpfast.com npm analogy | [link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) | "npm took a decade; skills did it in 2 months" |
| hesreallyhim/awesome-claude-code | [link](https://github.com/hesreallyhim/awesome-claude-code) | 36.8k star canonical curated list |
| ComposioHQ/awesome-claude-skills | [link](https://github.com/ComposioHQ/awesome-claude-skills) | 1000+ production-ready multi-platform skills |
| jeremylongshore/claude-code-plugins-plus-skills | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2,810 skills, ccpi CLI |
| netresearch/claude-code-marketplace | [link](https://github.com/netresearch/claude-code-marketplace) | Enterprise-focused agentskills.io curated collection |
| alirezarezvani/claude-skills | [link](https://github.com/alirezarezvani/claude-skills) | 313+ skills across engineering/marketing/product/compliance |
| VoltAgent/awesome-agent-skills | [link](https://github.com/VoltAgent/awesome-agent-skills) | 1000+ official + community multi-platform skills |
| Chat2AnyLLM/awesome-claude-skills | [link](https://github.com/Chat2AnyLLM/awesome-claude-skills) | 9,864 skills as of 2026-05-06 |
| MCP Market | [link](https://mcpmarket.com/) | Submission-based MCP + skills directory |
| modelcontextprotocol/mcpb | [link](https://github.com/modelcontextprotocol/mcpb) | Open-source .mcpb spec |
| Azure MCP .mcpb | [link](https://devblogs.microsoft.com/azure-sdk/azure-mcp-server-mcpb-support/) | Microsoft Azure MCP as .mcpb package |
| VS Code agent skills | [link](https://code.visualstudio.com/docs/copilot/customization/agent-skills) | VS Code native skills support |
| VS Code MCP | [link](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) | VS Code MCP server configuration |
| Claude official skills docs | [link](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) | Official Anthropic skills documentation |
| Claude cookbooks | [link](https://github.com/anthropics/claude-cookbooks/tree/main/skills) | Anthropic example skills |
| anthropics/skills | [link](https://github.com/anthropics/skills) | Anthropic official skill examples |
| LinkedIn (Rob Foster) | [link](https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we) | 2026 practitioner survival guide |
| Towards AI | [link](https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff) | Full extension taxonomy (skills/MCP/hooks/subagents/plugins) |
| aibusiness.com | [link](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) | Launch coverage |
| Unite.AI | [link](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/) | Standards strategy analysis |
| FinancialContent | [link](https://www.financialcontent.com/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability) | "Universal Language for AI Interoperability" framing |
| arxiv 2603.16572 | [link](https://arxiv.org/pdf/2603.16572) | Academic: malicious skill classification with repo context |
| gentic.news MCP crisis | [link](https://gentic.news/article/mcp-security-crisis-43-of-servers) | 43% MCP server vulnerability rate |
| obot.ai supply chain | [link](https://obot.ai/blog/mcp-security-agent-skills-supply-chain/) | MCP + skills supply chain security |
| practical-devsecops MCP | [link](https://www.practical-devsecops.com/mcp-security-guide/) | MCP security complete guide 2026 |
| practical-devsecops vulns | [link](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) | Prompt injection + tool poisoning guide |
| ismalicious.com DDIPE | [link](https://ismalicious.com/posts/mcp-security-risks-tool-poisoning-ai-agents) | DDIPE attack technique (11.6-33.5% bypass rate) |
| mintmcp.com CVE | [link](https://www.mintmcp.com/blog/claude-code-cve) | Enterprise CVE-2025-59536 and CVE-2026-21852 guide |
| obot.ai Claude leak crisis | [link](https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/) | MCP security masterclass |
| Medium @katy-thomas | [link](https://medium.com/@katy-thomas/your-engineers-gave-claude-root-access-do-you-know-what-it-did-next-846d34eca5c1) | Root access risks narrative |
| cyberdesserts.com AI risks | [link](https://blog.cyberdesserts.com/ai-agent-security-risks/) | AI agent security risk overview 2026 |
| cyberdesserts.com OpenClaw | [link](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/) | OpenClaw/ClawHub malicious skills |
| agensi.io toxicskills | [link](https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026) | Security crisis narrative |
| Polymarket AI predictions | [link](https://polymarket.com/predictions/ai) | Live AI prediction markets |
| sparkco.ai Polymarket | [link](https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi) | Claude Code + Kalshi/Polymarket agent guide |
| conare Polymarket MCP | [link](https://conare.ai/marketplace/mcp/polymarket-mcp) | Polymarket MCP server |
| conare Graph Polymarket | [link](https://conare.ai/marketplace/mcp/graph-polymarket) | Graph Polymarket 20-tool MCP |
| Composio TikTok (Claude Code) | [link](https://composio.dev/toolkits/tiktok/framework/claude-code) | TikTok MCP integration |
| Composio TikTok (Agent SDK) | [link](https://composio.dev/toolkits/tiktok/framework/claude-agents-sdk) | TikTok Agent SDK integration |
| Composio Twitter (Claude Code) | [link](https://composio.dev/toolkits/twitter/framework/claude-code) | Twitter MCP integration |
| claudlog.com Twitter MCP | [link](https://claudelog.com/claude-code-mcps/twitter-mcp/) | Twitter MCP guide |
| claudefa.st social MCPs | [link](https://claudefa.st/blog/tools/mcp-extensions/social-media-mcps) | Social media MCP guide |
| stormy.ai TikTok factory | [link](https://stormy.ai/blog/building-tiktok-content-factory-claude-code) | TikTok content automation with Claude Code |
| stormy.ai Instagram | [link](https://stormy.ai/blog/autonomous-instagram-content-engine-claude-code-playbook) | Instagram content engine with Claude Code |
| claudeskills.info | [link](https://claudeskills.info/best/) | Best Claude Skills 2026 directory |
| thetoolnerd.com | [link](https://www.thetoolnerd.com/p/10-best-ai-claude-skills-to-supercharge) | Top 10 AI Claude skills |
| agensi.io how marketplaces work | [link](https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work) | Marketplace mechanics explainer |
| Udemy course | [link](https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/) | Agent Skills: Claude Code, Cursor and MCP in Practice |
| DEV.to Composio top plugins | [link](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6) | 10 top Claude Code plugins 2026 |
| scriptbyai.com resource list | [link](https://www.scriptbyai.com/claude-code-resource-list/) | Ultimate Claude Code Resource List 2026 |
| nimbalyst MCP setup | [link](https://nimbalyst.com/blog/claude-code-mcp-setup/] | Claude Code MCP setup guide |
| Watch YouTube skill | [link](https://mcpmarket.com/tools/skills/watch-youtube) | YouTube transcript/search skill for Claude |
| Hacker News Agent skill | [link](https://mcpmarket.com/tools/skills/hacker-news-agent) | HN agent skill for Claude Code |
| Polymarket dev suite skill | [link](https://mcpmarket.com/tools/skills/polymarket-development-suite) | Polymarket development skill |
| Polymarket trading skill | [link](https://mcpmarket.com/tools/skills/polymarket-trading-data-integration) | Polymarket trading data skill |
| X/Twitter automation skill | [link](https://mcpmarket.com/tools/skills/x-twitter-automation) | X automation skill (33 commands, OAuth 1.0a) |
| TikTok content strategy skill | [link](https://mcpmarket.com/tools/skills/tiktok-content-strategy) | TikTok content strategy skill |
| claudskills.com TikTok | [link](https://claudskills.com/skills/tiktok-automation/) | TikTok automation skill page |
| Microsoft security blog | [link](https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/) | Copilot Studio OWASP Top 10 guidance |
| developers digest subagents | [link](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) | Claude Code agent teams 2026 |
| developers digest HN | [link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | HN community signals analysis |
| agents-observe GitHub | [link](https://github.com/simple10/agents-observe) | Real-time Claude Code agent team dashboard |
| Udemy course | [link](https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/) | Agent Skills paid Udemy course |
| strac.io M365 MCP | [link](https://www.strac.io/blog/m365-mcp-server) | Microsoft 365 MCP secure setup |
| morphllm.com | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills vs MCP vs plugins complete guide |
| agensi.io plugins vs skills | [link](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Plugins vs skills explainer |
| termdock.com | [link](https://www.termdock.com/en/blog/agent-skills-guide) | Agent skills build/share/secure guide |
| hyperfx.ai marketing skills | [link](https://www.hyperfx.ai/blog/best-marketing-skills-mcps-and-clis-for-ai-agents-2026) | Marketing skills, MCPs, CLIs 2026 |
| devtoolpicks.com | [link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Claude Skills vs MCP connectors vs plugins |
| GitHub awesome-claude-code issues | [link](https://github.com/hesreallyhim/awesome-claude-code/issues/1285) | X Twitter Scraper resource issue |
| claudefa.st MCP addons | [link](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers roundup |
| Samarth0211/awesome-claude-skills-2026 | [link](https://github.com/Samarth0211/awesome-claude-skills-2026) | 2,300+ skills, clskills.in |
| claudefa.st awesome roundup | [link](https://claudefa.st/blog/tools/resources/awesome-claude-code) | 11 curated awesome lists roundup |
| DEV.to Claude Code hit #1 HN | [link](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74) | Claude Code HN #1 explainer |
| computeleap.com | [link](https://www.computeleap.com/blog/claude-code-complete-guide-2026/) | Claude Code complete guide 2026 |
| Medium @weare1010 Polymarket | [link](https://medium.com/@weare1010/claude-ai-trading-bots-are-making-hundreds-of-thousands-on-polymarket-2840efb9f2cd) | AI trading bot claims analysis |
| wealthytent.com trading bot | [link](https://wealthytent.com/ai-trading-bot-for-polymarket) | Polymarket AI trading bot guide |
| skywork.ai Polymarket | [link](https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560) | AI engineer's guide to Polymarket MCP |
| BehiSecc/awesome-claude-skills | [link](https://github.com/BehiSecc/awesome-claude-skills) | Curated Claude skills list |
| travisvn/awesome-claude-skills | [link](https://github.com/travisvn/awesome-claude-skills) | Curated Claude skills + workflows |
| GetBindu/awesome-claude-code-and-skills | [link](https://github.com/GetBindu/awesome-claude-code-and-skills) | Claude Code + skills collection |
| chat2anyllm.github.io | [link](https://chat2anyllm.github.io/awesome-claude-skills/) | 9,864 skills web view |
| playbooks.com agentskills-io | [link](https://playbooks.com/skills/openclaw/skills/agentskills-io) | agentskills-io skill for OpenClaw |
| kenhuangus/agentic-skills-top-10 | [link](https://github.com/kenhuangus/agentic-skills-top-10) | OWASP agentic skills top 10 GitHub |
| FinancialContent tokenring | [link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-25-anthropic-unveils-agent-skills-open-standard-a-blueprint-for-modular-ai-autonomy) | "Blueprint for Modular AI Autonomy" |
| FinancialContent walled gardens | [link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-31-anthropic-shatters-ai-walled-gardens-with-launch-of-agent-skills-open-standard) | "Shatters AI Walled Gardens" framing |
| Medium @evoailabs | [link](https://medium.com/@evoailabs/agent-skills-are-open-standard-can-be-used-with-any-llm-agent-feb0cba4e0ff) | Open standard for any LLM/agent |
| solobusinesshub | [link](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/) | AI agent skills boom trend analysis |
| Skly on Vercel Community | [link](https://community.vercel.com/t/skly-an-ai-skills-marketplace-is-built-with-next-js-and-supabase/33827) | Indie skill marketplace built with Next.js + Supabase |
| vercel-labs/skills GitHub | [link](https://github.com/vercel-labs/skills) | Vercel's open agent skills tool |
| agensi.io creator monetization | [link](https://www.agensi.io/learn/agent-skills-marketplace-sell-your-skills) | Selling AI skills guide |
| Virtual Uncle skills.sh | [link](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | skills.sh marketplace guide |
| nimbalyst plugins | [link](https://nimbalyst.com/blog/claude-code-plugins-guide/) | Claude Code plugins guide 2026 |
| nimbalyst MCP servers | [link](https://nimbalyst.com/blog/best-claude-code-mcp-servers/] | Best MCP servers ranked 2026 |
| agensi.io plugin marketplace guide | [link](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Plugin marketplace guide |
| agensi.io how marketplaces work | [link](https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work) | How marketplaces work |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (no results returned)
├─ 🔵 X/Twitter: 0 posts (no results returned; X automation skills indexed)
├─ 🔴 YouTube: 3 videos │ — views (views not available)
├─ 🟢 HN: 5 threads │ 96 points │ 32+ comments
├─ 🟣 TikTok: 2 videos │ — views
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no results returned)
├─ 📊 Polymarket: 0 markets (no on-topic prediction markets found; Polymarket MCP servers indexed)
├─ 🌐 Web: 100+ pages
└─ 🗣️ Top voices: lixiaofei (HN), simple10 (HN), rohans0509 (HN), AndyNemmity (HN) │ agentskills.io, OWASP, Anthropic Engineering, Snyk, Vercel
```

---

## Data Gaps

- **Reddit:** Zero results returned for all Reddit-targeted queries. The r/ClaudeAI and r/LocalLLaMA communities almost certainly have active discussions on this topic, but they were not indexed by the available search tools. This is a significant gap — estimated coverage: 15% of likely Reddit signal.
- **X/Twitter:** No X/Twitter posts returned as primary results. Social discussion is almost certainly active (Claude Code has a large developer following), but search results did not surface individual posts. Skills exist for X automation but no individual post engagement data was captured.
- **Bluesky:** No results returned.
- **Instagram:** No relevant results.
- **Polymarket:** No active prediction markets specifically about agent skills timelines, marketplace dominance, or security outcomes were found. Polymarket MCP servers and skills exist as integration tools but no active prediction markets on the topic.
- **Engagement numbers:** YouTube view/like counts and TikTok view/like counts were not returned by search results. Tables reflect this absence.
- **Freshness:** Some sources (particularly security CVE data and marketplace skill counts) change rapidly; figures quoted reflect the state described in source articles, which may be 2–8 weeks old.
- **Approximate coverage:** Web/blog ~90%, HN ~75%, YouTube ~60%, TikTok ~40%, Reddit ~5%, X ~5%, Bluesky ~0%.

---

## Key Quotes

> "Skills extend Claude's capabilities by packaging your expertise into composable resources for Claude, transforming general-purpose agents into specialized agents that fit your needs." — Anthropic Engineering ([link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

> "npm took a decade to reach 350,000 packages. The AI agent skills ecosystem did it in about two months." — buildmvpfast.com ([link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026))

> "Claude kept reporting success when it just silenced the error." — commenter on HN Show HN: Real-time dashboard for Claude Code agent teams ([link](https://news.ycombinator.com/item?id=47602986))

> "Every agent framework solves orchestration well, but none of them answer: what happens when Agent A needs to hire Agent B for a capability it doesn't have?" — angtly on HN ([link](https://news.ycombinator.com/item?id=47463371))

> "The top 30 results I see here are other skill collection libraries or skill generators." — ricardobeat on HN, questioning curation quality ([link](https://news.ycombinator.com/item?id=46693426))

> "MCP is the plumbing that connects Claude to the outside world; skills are the instructions that teach Claude how to do specific things." — devtoolpicks.com ([link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026))

> "Your Engineers Gave Claude Root Access. Do You Know What It Did Next?" — @katy-thomas on Medium ([link](https://medium.com/@katy-thomas/your-engineers-gave-claude-root-access-do-you-know-what-it-did-next-846d34eca5c1))

> "Snyk found 1,467 malicious payloads across 3,984 scanned skills — a 36% flaw rate." — Snyk ToxicSkills audit ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Claude Code skills aren't that different from agents or other automation tools — the big difference is that they lower the barrier so more people (including beginners) can use them." — lixiaofei on HN ([link](https://news.ycombinator.com/item?id=46693426))

> "By donating the standard to the newly formed Agentic AI Foundation (AAIF) — a Linux Foundation-backed alliance — Anthropic is effectively attempting to end the 'walled garden' era of AI development." — FinancialContent ([link](https://markets.financialcontent.com/wral/article/tokenring-2025-12-31-anthropic-shatters-ai-walled-gardens-with-launch-of-agent-skills-open-standard))
