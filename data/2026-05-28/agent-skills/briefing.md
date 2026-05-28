# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-28
**Query type:** GENERAL
**Sources:** Web, Hacker News, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 threads | 402+ points, 475+ comments (top thread) | Skills vs MCP debate, emergent behavior |
| GitHub | 10+ repos | 99,900+ stars (top repo), 21,000+ (toolkit) | Curated lists, marketplaces, plugin packs |
| Web | 42 pages | — | Blogs, docs, security analyses, marketplace guides |

---

## Synthesized Findings

### 1. The Claude Code Extension Model Has Fully Standardized

The Claude Code ecosystem has converged on a clear, layered architecture. A **skill** is a reusable slash command packaged as a `SKILL.md` file with YAML frontmatter and markdown instructions. A **plugin** bundles multiple skills, MCP servers, slash commands, hooks, and agents into a shareable unit with a `plugin.json` manifest. **Extensions** is the umbrella term covering all four primitive types: MCP servers, Skills, Agents, and Hooks.

Skills live in `~/.claude/skills/` (user-global) or `.claude/skills/` (project-level, committed to the repo). The older `~/.claude/commands/` path remains functional but is now considered legacy. Project-level skills are significant because they give entire teams the same slash commands, enforcement rules, and workflow shortcuts — the skill becomes a first-class artifact of the codebase.

Official Claude Code docs confirm the separation of concerns: use `CLAUDE.md` for always-true project conventions, skills for richer on-demand invokable workflows, and slash commands for explicit repeatable terminal entry points.

**Sources:** [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills) · [alexop.dev post](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/) · [daviddacruz.dev](https://daviddacruz.dev/blog/claude-code-skills-agents) · [thepromptshelf.dev](https://thepromptshelf.dev/blog/claude-code-custom-slash-commands/) · [mindstudio.ai](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows)

**Platforms:** Web, GitHub

---

### 2. Marketplace Explosion: From Nothing to Hundreds of Thousands of Skills

Claude Code plugins launched in public beta in **October 2025** and are now fully stable. Since then the numbers have climbed fast:

- **tonsofskills.com** (backed by the `jeremylongshore/claude-code-plugins-plus-skills` GitHub repo): 431 plugins, 2,810 skills, 200 agents as of 2026-05-20. Includes 42 SaaS skill packs covering 1,086 skills for specific platforms (Framer, OpenEvidence, etc.). The `ccpi` CLI package manager allows install, search, list, upgrade, validate, and diagnose directly from the terminal.
- **claudemarketplaces.com**: Claims 6,700+ skills, 2,500+ marketplace entries, 840+ MCP servers.
- **agenticskills.io** (Vercel Labs): A meta-skill called "Find Skills" lets agents discover, search, and install from the entire AgenticSkills ecosystem in a single unified interface.
- **Q2 2026 landscape**: Eight distinct marketplaces now compete, with different economics, review rules, and distribution dynamics. Top agencies publish the same capability as a Skill, a GPT, an MCP server, and a Hugging Face Space simultaneously.

The broader open Agent Skills standard has driven 100,000+ installs across ecosystems with cross-platform compatibility.

**Sources:** [tonsofskills.com](https://tonsofskills.com/) · [tonsofskills.com/docs](https://tonsofskills.com/docs/) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [agenticskills.io/skills/find-skills](https://agenticskills.io/skills/find-skills) · [agensi.io marketplace guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) · [skillsplayground.com](https://skillsplayground.com/guides/best-claude-code-plugins/) · [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) · [solobusinesshub.com](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/)

**Platforms:** Web, GitHub

---

### 3. MCP Has Become the Undisputed Industry Standard

The Model Context Protocol has crossed from early-adopter phase to universal infrastructure in 2026:

- **97 million installs** as of May 2026 — the headline number that cements MCP as the industry standard.
- **Donated to the Linux Foundation's Agentic AI Foundation** in December 2025 — the governance move that signaled it belongs to no single vendor.
- **OpenAI and Google DeepMind** adopted MCP in early 2025.
- **Glama lists 22,775 MCP servers** as of May 2026 (though many are forks/abandoned).
- The **MCP Registry** (modelcontextprotocol.info/tools/registry/) launched September 2025 and grew to ~2,000 official entries within months, backed by Anthropic, GitHub, PulseMCP, and Microsoft.
- **January 2026**: Anthropic integrated Tool Search directly into Claude Code for dynamic MCP tool discovery at runtime.
- **May 2026 research preview**: MCP Tunnels, letting Managed Agents and the Messages API reach private MCP servers without public internet exposure (InfoQ coverage).

The 2026 MCP roadmap priorities: stateless transport, agent-to-agent coordination, enterprise governance, and interactive tool responses.

MCP exposes three primitives: **resources** (read-only data), **tools** (state-modifying actions), and **prompts** (reusable instruction templates).

**Sources:** [tessl.io](https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/) · [vucense.com](https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/) · [anthropic.com/news MCP donation](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) · [mcpplaygroundonline.com roadmap](https://mcpplaygroundonline.com/blog/mcp-2026-roadmap-whats-changing-for-developers) · [workos.com MCP guide](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) · [docs.anthropic.com/mcp](https://docs.anthropic.com/en/docs/agents-and-tools/mcp) · [infoq.com MCP tunnels](https://www.infoq.com/news/2026/05/claude-mcp-tunnels/) · [modelcontextprotocol.info registry](https://modelcontextprotocol.info/tools/registry/) · [tokenmix.ai changelog](https://tokenmix.ai/blog/mcp-updates-changelog-every-protocol-change-2026) · [mcpmarket.com](https://mcpmarket.com/) · [aiagentslist.com](https://aiagentslist.com/mcp-servers) · [atlan.com MCP vs API](https://atlan.com/know/when-to-use-mcp-vs-api/)

**Platforms:** Web

---

### 4. GitHub Community Has Built a Massive Curated Ecosystem

The GitHub community has responded to the plugin/skills era with a wave of curated "awesome" lists that are themselves becoming reference infrastructure:

- **"Everything Claude Code"** repo: ~99,900 GitHub stars (March 2026), 13,000 forks, 113 contributors. Contains 28 specialized subagents, 119 reusable skills, 60 slash commands, 34 rules, 20+ automated hooks, 14 MCP server configs. Approaching the symbolic 100K milestone.
- **awesome-claude-code-toolkit** (rohitg00): 21,000+ stars; 135 agents, 35 curated skills, 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, 26 companion apps, 52 ecosystem entries.
- **awesome-claude-code** (hesreallyhim): Skills, hooks, slash commands, agent orchestrators, applications, plugins.
- **awesome-claude-plugins** (ComposioHQ): Custom commands, agents, hooks, MCP servers.
- **awesome-claude-code-and-skills** (GetBindu): Skill collections.
- **Awesome-Claude-MCP-Servers** (win4r): MCP servers optimized for Claude.
- **awesome-claude-plugins** (quemsah): Automated adoption metrics via n8n workflows.
- Notable individual tools: XcodeBuildMCP (4,145 stars), claude-code-guide (4,134 stars).

**Sources:** [bridgers.agency](https://bridgers.agency/en/blog/everything-claude-code-explained) · [github.com/rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) · [github.com/hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) · [github.com/ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) · [github.com/GetBindu/awesome-claude-code-and-skills](https://github.com/GetBindu/awesome-claude-code-and-skills) · [github.com/win4r/Awesome-Claude-MCP-Servers](https://github.com/win4r/Awesome-Claude-MCP-Servers) · [github.com/quemsah/awesome-claude-plugins](https://github.com/quemsah/awesome-claude-plugins) · [awesomeclaude.ai/top-mcp-servers](https://awesomeclaude.ai/top-mcp-servers) · [rodert.github.io/awesome-mcp](https://rodert.github.io/awesome-mcp/) · [gist: 5 MCP servers](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1)

**Platforms:** Web, GitHub

---

### 5. Skills vs. MCP — The Ongoing Architecture Debate on Hacker News

HN has become the primary venue for the "what's the right abstraction?" debate:

- **HN item 45619537** — "Claude Skills are awesome, maybe a bigger deal than MCP" — framed skills as higher-leverage because they encode not just *what* to call but *how to work*, a level of abstraction MCP tools don't reach.
- **HN item 46038842** — "I definitely see the value and versatility of Claude Skills (over what MCP is to…)" — community nuancing when MCP alone is sufficient vs. when a skill wrapping multiple MCP calls is better.
- **HN item 46531794** — "Claude Code Emergent Behavior: When Skills Combine" — documenting unexpected synergies when multiple skills are installed simultaneously.
- The broader HN consensus (per Developers Digest synthesis): workflows matter more than demos; verification is the bottleneck; skills beat prompts; orchestration matters more than raw autonomy.
- Uber's AI spend story (Claude Code consumed entire 2026 AI budget in 4 months) landed with 402 points and 475 comments — the clearest signal of enterprise-scale adoption.

**Sources:** [news.ycombinator.com/item?id=45619537](https://news.ycombinator.com/item?id=45619537) · [news.ycombinator.com/item?id=46038842](https://news.ycombinator.com/item?id=46038842) · [news.ycombinator.com/item?id=46531794](https://news.ycombinator.com/item?id=46531794) · [developersdigest.tech HN piece](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) · [developersdigest.tech 2026 playbook](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026)

**Platforms:** Hacker News, Web

---

### 6. MCP Security Is a Major Emerging Crisis

The rapid growth of MCP has created a significant and largely unaddressed attack surface:

- **BlueRock Security analysis of ~7,000 public servers** (2026): 36.7% SSRF-vulnerable; 41% require no authentication at all; 53% of authenticated servers use static API keys; only 8.5% use OAuth.
- **30 CVEs in 60 days** in the first two months of 2026 — Check Point, Invariant Labs, Adversa AI, and independent researchers all filing simultaneously.
- Notable CVEs: **CVE-2026-26118** (Azure MCP Server SSRF, March 2026); **CVE-2026-32211** (missing auth in @azure-devops/mcp, CVSS 9.1, April 2026); **CVE-2026-39974** (n8n-MCP SSRF via arbitrary HTTP requests, SentinelOne).
- Classic AppSec vulnerabilities (SSRF, injection, missing auth) are re-emerging in AI infrastructure because MCP server developers aren't security-trained.
- AI Agent supply chain attacks are an emerging vector — malicious skill or plugin packages, similar to npm supply chain attacks.

**Sources:** [windowsnews.ai CVE-2026-26118](https://windowsnews.ai/article/microsoft-patches-critical-azure-mcp-ssrf-vulnerability-cve-2026-26118-in-march-2026-security-update.404636) · [heyuan110.com 30 CVEs](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) · [agent-wars.com 30 CVEs](https://agent-wars.com/news/2026-03-13-mcp-security-2026-30-cves-in-60-days-what-went-wrong) · [sentinelone.com CVE-2026-39974](https://www.sentinelone.com/vulnerability-database/cve-2026-39974/) · [dailycve.com Spring AI MCP](https://dailycve.com/spring-ai-mcp-security-ssrf-via-dcr-cve-2026-xxxx-critical/) · [pipelab.org vulnerabilities](https://pipelab.org/learn/mcp-vulnerabilities/) · [endorlabs.com AppSec](https://www.endorlabs.com/learn/classic-vulnerabilities-meet-ai-infrastructure-why-mcp-needs-appsec) · [blog.cyberdesserts.com](https://blog.cyberdesserts.com/ai-agent-security-risks/)

**Platforms:** Web

---

### 7. Developer Experience: Harness > Model in 2026

Blog posts and community guides have converged on a key insight: the *harness* around Claude Code matters more than the raw model capability. The most productive teams build systems — not just prompts.

- Morph MCP Server: most-installed Claude Code extension, delivering **35% faster edits** and **40% less context rot** through parallel codebase search.
- Best-practice stack: `CLAUDE.md` + hooks + custom skills + MCP integrations + review pipelines + CI workflows.
- MCP is the difference between an agent that edits files and one that can operate your actual workflow (JIRA → database → deploy → monitor).
- Sub-agents and orchestration patterns are now standard; Claude Code 2.0 guides explicitly cover multi-agent coordination.
- Microsoft's dotnet skills repository represents enterprise standardization: official Microsoft repository for AI coding agent capabilities.

**Sources:** [morphllm.com extensions guide](https://www.morphllm.com/claude-code-extensions) · [vld-bc.com best practices](https://vld-bc.com/blog/cli-agents-part2-claude-code-best-practices) · [sankalp.bearblog.dev Claude Code 2.0](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) · [rundatarun.io last 30 days](https://rundatarun.io/p/last-30-days-claude-code) · [medium.com/@lmpo mastering agentic coding](https://medium.com/@lmpo/mastering-agentic-coding-in-claude-a-guide-to-skills-sub-agents-slash-commands-and-mcp-servers-5c58e03d4a35) · [explainx.ai dotnet skills](https://explainx.ai/blog/dotnet-skills-ai-agents-complete-guide-2026) · [calmops.com complete guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) · [tonykipkemboi.com](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained) · [nevo.systems](https://nevo.systems/blogs/nevo-journal/what-are-ai-agent-plugins) · [chris-ayers.com marketplace guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) · [producttalk.org](https://www.producttalk.org/how-to-use-claude-code-features/) · [nimbalyst.com](https://nimbalyst.com/blog/claude-code-plugins-guide/) · [mejba.me top 10](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) · [firecrawl.dev best MCP](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) · [analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/) · [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers) · [toloka.ai](https://toloka.ai/blog/best-mcp-servers-for-ai-agents/) · [bytebridge.medium.com](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) · [learn.microsoft.com MCP tools](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) · [dev.to daviddacruz](https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865) · [code.claude.com slash commands](https://code.claude.com/docs/en/agent-sdk/slash-commands) · [mcpmarket.com HN agent skill](https://mcpmarket.com/tools/skills/hacker-news-agent) · [mcpmarket.com HN reader](https://mcpmarket.com/tools/skills/hacker-news-reader) · [mcpmarket.com daily march](https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026) · [api.market stock MCP](https://api.market/blog/magicapi/stock-market-api/best-mcp-servers-stock-market-data) · [github topics awesome-claude-code](https://github.com/topics/awesome-claude-code?o=asc&s=updated) · [dev.to max_quimby](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74)

**Platforms:** Web, GitHub

---

## Cross-Source Patterns

### Pattern 1: Skills > Raw Prompts > MCP Tools (in terms of reusability)

**Signal:** The three-tier hierarchy has stabilized: MCP tools give Claude access to external systems; skills encode *how* to use those tools for a specific workflow; CLAUDE.md encodes team conventions. Skills are the emerging "killer layer."

**Platforms:** Hacker News, Web (docs, blogs)

**Key quotes:**
- "Claude Skills are awesome, maybe a bigger deal than MCP" — HN item 45619537 ([link](https://news.ycombinator.com/item?id=45619537))
- "I definitely see the value and versatility of Claude Skills (over what MCP is to..." — HN item 46038842 ([link](https://news.ycombinator.com/item?id=46038842))
- "Instead of typing a paragraph every time you want Claude to do something, you type /deploy or /review-pr and it knows exactly what to do" — [daviddacruz.dev](https://daviddacruz.dev/blog/claude-code-skills-agents)

---

### Pattern 2: MCP Security Gap Growing Faster Than Ecosystem Maturity

**Signal:** The rapid proliferation of MCP servers has dramatically outpaced security practices. High percentages of vulnerable servers, multiple CVEs, and enterprise governance gaps are now the dominant MCP story in security-adjacent communities.

**Platforms:** Web (security blogs, CVE databases)

**Key quotes:**
- "36.7% are SSRF-vulnerable, 41% require no authentication at all, 53% of authenticated servers rely on static API keys, and only 8.5% use OAuth" — BlueRock Security analysis via [pipelab.org](https://pipelab.org/learn/mcp-vulnerabilities/)
- "30 CVEs in 60 Days — What Went Wrong" — [heyuan110.com](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/)

---

### Pattern 3: Harness Architecture Becoming Standard Practice

**Signal:** Across HN threads, developer blogs, and guides, the pattern is consistent: the system built *around* Claude Code (CLAUDE.md, hooks, MCP integrations, CI workflows) now defines team productivity more than the model itself.

**Platforms:** Hacker News, Web

**Key quotes:**
- "The harness mattering more than the model" — [developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)
- "Claude Code Emergent Behavior: When Skills Combine" — HN item 46531794 ([link](https://news.ycombinator.com/item?id=46531794))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (community) | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | "versatility of Claude Skills over what MCP is to..." | [HN 45619537](https://news.ycombinator.com/item?id=45619537) |
| (community) | I definitely see the value and versatility of Claude Skills | — | — | Skills vs. MCP nuance | [HN 46038842](https://news.ycombinator.com/item?id=46038842) |
| (community) | Claude Code Emergent Behavior: When Skills Combine | — | — | Unexpected synergies when multiple skills installed | [HN 46531794](https://news.ycombinator.com/item?id=46531794) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs (Skills) | [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills) | Official skill architecture — SKILL.md format, frontmatter spec, directory locations |
| Claude Code Docs (Slash Commands) | [code.claude.com/docs/en/agent-sdk/slash-commands](https://code.claude.com/docs/en/agent-sdk/slash-commands) | Official slash command SDK reference |
| Anthropic MCP Docs | [docs.anthropic.com/en/docs/agents-and-tools/mcp](https://docs.anthropic.com/en/docs/agents-and-tools/mcp) | Official MCP definition — three primitives (resources, tools, prompts) |
| Anthropic MCP Donation | [anthropic.com/news/donating-the-model-context-protocol](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | Governance milestone — MCP donated to Linux Foundation Agentic AI Foundation |
| InfoQ MCP Tunnels | [infoq.com/news/2026/05/claude-mcp-tunnels](https://www.infoq.com/news/2026/05/claude-mcp-tunnels/) | May 2026 research preview — private MCP server access without public internet |
| Tessl.io MCP Tool Search | [tessl.io](https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/) | Jan 2026 — dynamic tool discovery added to MCP in Claude Code |
| tonsofskills.com | [tonsofskills.com](https://tonsofskills.com/) | Largest open marketplace: 431 plugins, 2,810 skills, ccpi CLI |
| tonsofskills.com Docs | [tonsofskills.com/docs](https://tonsofskills.com/docs/) | ccpi CLI documentation |
| claudemarketplaces.com | [claudemarketplaces.com](https://claudemarketplaces.com/) | Aggregator: 6,700+ skills, 840+ MCP servers |
| MCP Registry | [modelcontextprotocol.info/tools/registry](https://modelcontextprotocol.info/tools/registry/) | Official registry — ~2,000 entries, launched Sep 2025 |
| MCP Market | [mcpmarket.com](https://mcpmarket.com/) | Searchable marketplace for MCP servers and skills |
| AgenticSkills (Vercel Labs) | [agenticskills.io/skills/find-skills](https://agenticskills.io/skills/find-skills) | Meta-skill for cross-marketplace skill discovery |
| WorkOS MCP Guide | [workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) | Enterprise MCP overview, 97M installs, governance |
| MCP 2026 Roadmap | [mcpplaygroundonline.com](https://mcpplaygroundonline.com/blog/mcp-2026-roadmap-whats-changing-for-developers) | Roadmap: stateless transport, agent-to-agent, enterprise governance |
| MCP Changelog | [tokenmix.ai](https://tokenmix.ai/blog/mcp-updates-changelog-every-protocol-change-2026) | Every protocol change since 2024 |
| Morph LLM Extensions | [morphllm.com/claude-code-extensions](https://www.morphllm.com/claude-code-extensions) | Morph MCP server: 35% faster edits, 40% less context rot |
| BlueRock / Pipelab Security | [pipelab.org/learn/mcp-vulnerabilities](https://pipelab.org/learn/mcp-vulnerabilities/) | Security: 36.7% SSRF, 41% no auth |
| 30 CVEs in 60 Days | [heyuan110.com](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) | Security: Jan–Feb 2026 CVE wave |
| CVE-2026-26118 | [windowsnews.ai](https://windowsnews.ai/article/microsoft-patches-critical-azure-mcp-ssrf-vulnerability-cve-2026-26118-in-march-2026-security-update.404636) | Azure MCP SSRF, March 2026 |
| CVE-2026-39974 | [sentinelone.com](https://www.sentinelone.com/vulnerability-database/cve-2026-39974/) | n8n-MCP SSRF, SentinelOne |
| Endor Labs AppSec | [endorlabs.com](https://www.endorlabs.com/learn/classic-vulnerabilities-meet-ai-infrastructure-why-mcp-needs-appsec) | Classic AppSec vulnerabilities in AI infrastructure |
| AI Agent Security Risks | [blog.cyberdesserts.com](https://blog.cyberdesserts.com/ai-agent-security-risks/) | MCP supply chain attacks, AI agent security 2026 |
| Developers Digest HN | [developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | HN consensus synthesis: workflows > demos |
| Developers Digest 2026 Playbook | [developersdigest.tech](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) | Agent teams + subagents + MCP patterns |
| Everything Claude Code (bridgers) | [bridgers.agency](https://bridgers.agency/en/blog/everything-claude-code-explained) | 99,900 GitHub stars context |
| Dotnet Skills (explainx.ai) | [explainx.ai](https://explainx.ai/blog/dotnet-skills-ai-agents-complete-guide-2026) | Microsoft official AI coding agent skills |
| Digital Applied Marketplaces | [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | Q2 2026 marketplace landscape: 8 competing platforms |
| AI Agent Skills Boom | [solobusinesshub.com](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/) | Skills ecosystem: nothing → hundreds of thousands in 4 months |
| Calm Ops Skills Guide | [calmops.com](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) | Reusable agent capabilities architecture |
| Tony Kipkemboi | [tonykipkemboi.com](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained) | Skill vs. plugin distinction |
| Nevo Systems | [nevo.systems](https://nevo.systems/blogs/nevo-journal/what-are-ai-agent-plugins) | AI agent plugins explained |
| Chris Ayers | [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Skills + plugins + marketplace complete guide |
| alexop.dev Customization | [alexop.dev](https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/) | CLAUDE.md + skills + subagents walkthrough |
| David Dacruz DEV | [dev.to/daviddacruz](https://dev.to/daviddacruz/claude-code-skills-agents-build-custom-slash-commands-for-real-work-3865) | Build custom slash commands for real work |
| Medium (@lmpo) | [medium.com/@lmpo](https://medium.com/@lmpo/mastering-agentic-coding-in-claude-a-guide-to-skills-sub-agents-slash-commands-and-mcp-servers-5c58e03d4a35) | Mastering agentic coding: skills + subagents + slash commands + MCP |
| VLD Best Practices | [vld-bc.com](https://vld-bc.com/blog/cli-agents-part2-claude-code-best-practices) | CLI agents Part 2 best practices |
| Prompt Shelf | [thepromptshelf.dev](https://thepromptshelf.dev/blog/claude-code-custom-slash-commands/) | Custom slash commands with skills |
| MindStudio | [mindstudio.ai](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows) | Automate repetitive workflows with skills |
| Producttalk.org | [producttalk.org](https://www.producttalk.org/how-to-use-claude-code-features/) | Guide to slash commands, agents, skills, plugins |
| Sankalp Bear Blog | [sankalp.bearblog.dev](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) | Claude Code 2.0 experience guide |
| Run Data Run | [rundatarun.io](https://rundatarun.io/p/last-30-days-claude-code) | Last 30 Days: Claude Code overview |
| Agensi.io Guide | [agensi.io](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Plugin marketplace guide |
| Nimbalyst | [nimbalyst.com](https://nimbalyst.com/blog/claude-code-plugins-guide/) | Claude Code plugins guide |
| Mejba.me Top 10 | [mejba.me](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 skills, plugins, CLIs for 2026 |
| Skills Playground | [skillsplayground.com](https://skillsplayground.com/guides/best-claude-code-plugins/) | Best Claude Code plugins 2026 |
| Firecrawl Top MCP | [firecrawl.dev](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | 10 Best MCP servers for developers |
| Analytics Vidhya | [analyticsvidhya.com](https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/) | Top 10 MCP servers for AI builders |
| MCP Bundles | [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers) | Best MCP servers definitive list (May updated) |
| Toloka.ai | [toloka.ai](https://toloka.ai/blog/best-mcp-servers-for-ai-agents/) | Best MCP servers for AI agents |
| ByteBridge Medium | [bytebridge.medium.com](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | MCP Gateways top 10 |
| Microsoft Learn | [learn.microsoft.com](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) | Using MCP Tools in Microsoft agent framework |
| MCP vs API (Atlan) | [atlan.com](https://atlan.com/know/when-to-use-mcp-vs-api/) | When to use MCP vs. API |
| Agent Wars 30 CVEs | [agent-wars.com](https://agent-wars.com/news/2026-03-13-mcp-security-2026-30-cves-in-60-days-what-went-wrong) | 30 CVEs analysis |
| DailyCVE Spring AI | [dailycve.com](https://dailycve.com/spring-ai-mcp-security-ssrf-via-dcr-cve-2026-xxxx-critical/) | Spring AI MCP critical SSRF |
| AI Agents List | [aiagentslist.com](https://aiagentslist.com/mcp-servers) | 593+ MCP server directory |
| MCP Market Daily | [mcpmarket.com/daily](https://mcpmarket.com/daily/top-mcp-server-list-march-4-2026) | Daily MCP server rankings |
| API Market | [api.market](https://api.market/blog/magicapi/stock-market-api/best-mcp-servers-stock-market-data) | Best MCP for stock market data |
| Glama Awesome Claude | [awesomeclaude.ai](https://awesomeclaude.ai/top-mcp-servers) | GitHub-star-ranked MCP servers |
| Dev.to Max Quimby | [dev.to/max_quimby](https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74) | Claude Code #1 HN moment |
| GitHub Topics | [github.com/topics/awesome-claude-code](https://github.com/topics/awesome-claude-code?o=asc&s=updated) | Ecosystem topic tracking |
| Septimlabs Gist | [gist.github.com/septimlabs-code](https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1) | 5 must-know MCP servers + configs |
| Spring AI SSRF | [dailycve.com](https://dailycve.com/spring-ai-mcp-security-ssrf-via-dcr-cve-2026-xxxx-critical/) | Spring AI MCP critical SSRF |
| MCP Vucense | [vucense.com](https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/) | 97M installs milestone |
| MCP Changelog Tokenmix | [tokenmix.ai](https://tokenmix.ai/blog/mcp-updates-changelog-every-protocol-change-2026) | Protocol change log |
| HN Skill for HN | [mcpmarket.com/tools/skills/hacker-news-agent](https://mcpmarket.com/tools/skills/hacker-news-agent) | HN agent skill on MCP Market |
| Framer Pack | [github.com/jeremylongshore/.../framer-pack](https://github.com/jeremylongshore/claude-code-plugins-plus-skills/tree/main/plugins/saas-packs/framer-pack) | Example SaaS skill pack |
| OpenEvidence SKILL.md | [github.com/jeremylongshore/.../openevidence-security-basics/SKILL.md](https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/plugins/saas-packs/openevidence-pack/skills/openevidence-security-basics/SKILL.md) | Example SKILL.md content |
| Installing Plugin Packs | [github.com/jeremylongshore/.../wiki](https://github.com/jeremylongshore/claude-code-plugins-plus-skills/wiki/Installing-Plugin-Packs) | CCPI wiki |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ — (not collected)
├─ 🔵 X: 0 posts │ — (not collected)
├─ 🔴 YouTube: 0 videos │ — (not collected)
├─ 🟢 HN: 3 threads │ 400+ points │ 475+ comments
├─ 🟣 TikTok: 0 videos │ — (not collected)
├─ 🩷 Instagram: 0 reels │ — (not collected)
├─ 🦋 Bluesky: 0 posts │ — (not collected)
├─ 📊 Polymarket: 0 markets │ — (not collected)
├─ 🌐 Web: 55 pages │ —
└─ 🗣️ Top voices: @jeremylongshore (tonsofskills), Vercel Labs (agenticskills.io) │ r/— (Reddit not collected)
```

---

## Data Gaps

- **last30days skill failed**: The skill entered a recursive invocation loop and did not execute its full pipeline (Reddit, X/Twitter, YouTube, TikTok, Instagram, Bluesky, Polymarket data not collected). This briefing relies entirely on WebSearch fallback.
- **Reddit not covered**: r/ClaudeAI, r/LocalLLaMA, r/MachineLearning, and similar communities discussing MCP/skills were not sampled.
- **X/Twitter not covered**: Developer conversation on X (likely high-volume for this topic) not collected.
- **YouTube not covered**: Tutorial and walkthrough videos for Claude Code skills/plugins not sampled.
- **Polymarket not covered**: No prediction markets data on MCP/Claude adoption.
- **Coverage estimate**: ~30-35% of likely signal (web/HN captured well; social/video completely absent).
- **Noise note**: The MCP server landscape has significant quantity noise — Glama's 22,775 count includes many forks, stubs, and abandoned projects. The 2,000 MCP Registry entries are a better signal for quality/active servers.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — Anonymous on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Instead of typing a paragraph every time you want Claude to do something, you type /deploy or /review-pr and it knows exactly what to do, how to do it, and what standards to follow." — [daviddacruz.dev](https://daviddacruz.dev/blog/claude-code-skills-agents)

> "36.7% are SSRF-vulnerable, 41% require no authentication at all, 53% of authenticated servers rely on static API keys, and only 8.5% use OAuth." — BlueRock Security 2026 analysis, via [pipelab.org](https://pipelab.org/learn/mcp-vulnerabilities/)

> "Claude Code Emergent Behavior: When Skills Combine" — Hacker News thread title ([link](https://news.ycombinator.com/item?id=46531794))

> "The harness mattering more than the model" — [Developers Digest](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

> "MCP is the difference between an agent that edits files and an agent that can operate your actual workflow." — [developersdigest.tech](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026)

> "The skills ecosystem went from nothing to hundreds of thousands of indexed skills in under four months." — [solobusinesshub.com](https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/)

> "MCP Security 2026: 30 CVEs in 60 Days — What Went Wrong" — [heyuan110.com](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/)

> "Project-specific skills can be committed to `.claude/skills/`. Now every developer on the team has the same slash commands, the same standards enforcement, and the same workflow shortcuts." — [thepromptshelf.dev](https://thepromptshelf.dev/blog/claude-code-custom-slash-commands/)

> "MCP hits 97 million installs — Anthropic's Agent Protocol Is Now the Industry Standard" — [vucense.com](https://vucense.com/ai-intelligence/ai-tools/mcp-97-million-installs-ai-agent-standard-2026/)
