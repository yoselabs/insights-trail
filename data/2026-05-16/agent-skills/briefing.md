# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-16
**Query type:** GENERAL
**Sources:** Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web | 80 pages | — | via WebSearch (9 queries) |

*Note: /last30days platform pipeline (Reddit, X, YouTube, TikTok, HN, Bluesky, Polymarket, GitHub) did not return scraped data this run — skill returned pipeline instructions instead of results. All findings are from supplementary WebSearch.*

---

## Synthesized Findings

### 1. Anthropic Launches Agent Skills as an Open Standard (Dec 2025 – Feb 2026)

Anthropic published the Agent Skills specification in December 2025 at [agentskills.io](https://agentskills.io/specification), releasing both a formal spec and reference SDK for any AI platform to adopt. The commercial enterprise push followed on **February 24, 2026** ([TechCrunch](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/)), with Anthropic unveiling pre-built enterprise plug-ins targeting finance, legal, HR, and engineering departments. The [Anthropic Engineering blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) framed skills as "reusable, filesystem-based resources that provide Claude with domain-specific expertise: workflows, context, and best practices that transform general-purpose agents into specialists."

Skills work across all Claude surfaces — Claude Code, Claude Agent SDK, and claude.ai — and are included in Max, Pro, Team, and Enterprise plans at no additional cost ([Claude API Docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)).

Key characterization: *"A skill tells Claude how to think about a class of problems"* — not just what to do. Compared to plain commands or prompts, skills inject reasoning patterns rather than instructions.

Coverage: [VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) · [Unite.AI](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/) · [Open Data Science](https://opendatascience.com/anthropic-introduces-agent-skills-making-claude-smarter-faster-and-more-specialized/) · [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) · [DevOps.com](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/)

---

### 2. SKILL.md: The Cross-Agent Open Format

The SKILL.md spec (formalized March 2026) is the key standardization event that made the current marketplace boom possible. A skill is a directory containing a `SKILL.md` file with YAML frontmatter (`name`, `description`, `when_to_use`, `allowed-tools`) and prose instructions beneath it. Optional subdirectories: `scripts/`, `references/`, `assets/`. ([Mintlify](https://www.mintlify.com/blog/skill-md) · [DeepWiki spec](https://deepwiki.com/agentskills/agentskills/2.2-skill.md-specification))

**Progressive disclosure** is a core design choice: metadata loads first, full instructions load on demand — critical for keeping context windows lean when many skills are installed.

As of early 2026, the following coding agents support SKILL.md natively:
- Claude Code (Anthropic)
- Codex CLI (OpenAI)
- Gemini CLI (Google)
- GitHub Copilot (VS Code agent skills, via Microsoft adoption)
- Cursor (manual placement)
- Cline, Windsurf, OpenCode (community tools)

Microsoft's adoption ([Microsoft Learn](https://learn.microsoft.com/en-us/agent-framework/agents/skills)) is notable — it signals SKILL.md becoming the dominant cross-agent interoperability layer, analogous to what OpenAPI did for REST APIs. [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) called Agent Skills "Anthropic's Next Bid to Define AI Standards."

The [Anthropic/skills GitHub repo](https://github.com/anthropics/skills) is the official public repository for Agent Skills.

Coverage: [agensi.io explainer](https://www.agensi.io/learn/what-is-skill-md) · [Firecrawl blog](https://www.firecrawl.dev/blog/agent-skills) · [Plaban Nayak / Medium](https://nayakpplaban.medium.com/agent-skills-standard-for-smarter-ai-bde76ea61c13) · [AB Vijay Kumar / Medium deep dive](https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996)

---

### 3. Skill Marketplace Explosion: Scale, Speed, and Fragmentation

A **February 2026 academic study** by Bosch Research and Carnegie Mellon documented the ecosystem grew **18.5× in 20 days** — from 2,179 publicly listed skills on January 16 to over 40,285 by February 5. By May 2026, the largest scrapers (SkillsMP) claim 800,000+ entries, though that figure is contested ([SmartScope](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) puts it at 66,500+ in their review). Monthly search volume for skill marketplace terms grew **19× over two years**: from 21,000 to 400,000+ queries/month ([agensi.io](https://www.agensi.io/learn/skills-marketplace-ai-agents)).

**Major marketplaces (as of May 2026):**

| Platform | Scale | Model | CLI |
|----------|-------|-------|-----|
| [SkillsMP](https://skillsmp.com/) | 800K+ (scraped GitHub, 2-star min filter) | Aggregator, no curation | Download ZIP only |
| [LobeHub Skills](https://lobehub.com/skills) | 169,739 skills | Curated, polished UX | LobeHub stack |
| [Skills.sh](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Large, community-driven | Vercel-backed, Jan 2026 | npm-style cross-agent CLI |
| [tonsofskills.com / ccpi](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 2,810 skills, 425 plugins, 200 agents | Claude Code focus, CCPI CLI | `ccpi install <pack>` |
| [ClaudeMarketplaces](https://claudemarketplaces.com/) | 400+ plugins, growing | Curated, voting/commenting | `/plugin install` in Claude Code |

**Quality and security concerns:** SkillsMP and Skills.sh have the largest catalogs but require developer-side auditing. SkillsMP's 800K figure includes scraped GitHub repos with minimal filtering. Security risk is real — a malicious SKILL.md can instruct the agent to make unsafe calls. ([agensi.io comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) · [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents))

Coverage: [CodeBytes complete guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) · [agensi.io marketplace comparison](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026) · [OpenAIToolsHub 6-platform side-by-side](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison) · [Tony Kipkemboi](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)

---

### 4. Claude Code Plugin System: Plugins vs. Skills vs. MCP Servers

A conceptual clarification has become important as the ecosystem matures:

- **Skill** = single instruction set (a SKILL.md directory) — the atomic unit
- **Plugin** = bundle of skills + MCP servers + hooks + commands — the distribution format
- **MCP Server** = external tool provider exposing functions over the Model Context Protocol

The official Claude Code `/plugin` command allows browsing, installing, and managing extensions from marketplaces. The [Create plugins docs](https://code.claude.com/docs/en/plugins) provide the canonical guide. The Anthropic-official marketplace (`claude-plugins-official`) ships pre-vetted plugins.

**ccpi** (Claude Code Plugin Installer) is the community CLI package manager:
- Install: `pnpm add -g @intentsolutionsio/ccpi` ([npm](https://www.npmjs.com/package/@intentsolutionsio/ccpi), v2.0.0)
- Commands: `ccpi search devops` / `ccpi install devops-automation-pack` / `ccpi validate ./your-plugin`
- Backed by the [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) repo: 425 plugins, 2,810 skills, 200 agents

Community curation efforts: [ComposioHQ/awesome-claude-plugins](https://github.com/ComposioHQ/awesome-claude-plugins) · [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) (263+ skills for Claude Code, Codex, Gemini, Cursor, and 8+ others)

Coverage: [Nimbalyst 2026 guide](https://nimbalyst.com/blog/claude-code-plugins-guide/) · [agensi.io plugins vs skills explainer](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) · [DEV Community guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) · [Mejba Ahmed Top 10](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) · [ScriptByAI resource list](https://www.scriptbyai.com/claude-code-resource-list/) · [Blake Crosley complete guide](https://blakecrosley.com/guides/claude-code) · [BrightCoding overview](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development)

---

### 5. MCP Tool Search: Solving Context Pollution at Scale

As MCP grew into the dominant tool-connection standard, a scaling crisis emerged: users with 50+ MCP tools were consuming 77K–144K tokens before doing any actual work. One user reported MCP_DOCKER alone consuming 125,964 tokens across 135 tools ([GitHub issue #11364](https://github.com/anthropics/claude-code/issues/11364)).

**MCP Tool Search** (announced January 14, 2026) solves this with lazy loading:
1. Claude Code checks if MCP tool descriptions exceed 10K tokens
2. If yes, tools are marked `defer_loading: true`
3. Claude receives a `ToolSearch` tool instead of all definitions
4. When Claude needs a tool, it searches by keyword → 3–5 relevant tools (~3K tokens) load per query
5. Result: **85% token overhead reduction** — from ~77K tokens to ~8.7K tokens per query

The feature is now **enabled by default** for all users. ([claudefa.st explainer](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) · [atcyrus.com guide](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide) · [Medium by JP Caparas](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc))

The pattern is spreading: OpenAI Codex ([issue #9266](https://github.com/openai/codex/issues/9266)) and OpenCode ([issue #9350](https://github.com/anomalyco/opencode/issues/9350)) both have active feature requests for the same capability. The lazy-loading feature request also has a GitHub issue asking to extend the ToolSearch pattern to *all* context components, not just MCP tools ([issue #44536](https://github.com/anthropics/claude-code/issues/44536)).

Coverage: [gopubby/AI Advances article](https://ai.gopubby.com/mcp-tools-are-eating-82-of-your-context-window-the-10-minute-fix-for-claude-code-1619733d00dc) · [daily.dev community post](https://app.daily.dev/posts/claude-code-new-lazy-mcp-loading-they-finally-fixed-the-biggest-issue-of-claude-code--wwzicivi3) · [GitHub #23787](https://github.com/anthropics/claude-code/issues/23787)

---

### 6. MCP Server Ecosystem: Official Integrations Arriving

MCP has moved from community-only to official vendor integrations:

- **Meta Ads MCP** (April 29, 2026): Meta's official MCP covering all 29 Facebook/Instagram Ads tools — campaign creation, audience management, A/B analysis from terminal ([full guide](https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026))
- **Google Ads MCP**: Google's official MCP for ad campaign search, bid adjustments, keyword performance reports
- **Higgsfield MCP**: AI image/video generation across 30+ models (motion, lip sync, consistent characters)
- **Polymarket MCP**: Prediction market access from Claude ([LobeHub](https://lobehub.com/mcp/amolkodan-polymarket-claude-mcp))
- Classic servers: Figma, Playwright, Vercel, PostgreSQL, GitHub (all listed in [claudefa.st's 50+ best MCP servers](https://claudefa.st/blog/tools/mcp-extensions/best-addons))

Discovery platforms: [MCP Market](https://mcpmarket.com/) (connects Claude and Cursor to tools like Figma, Databricks, Storybook, Ghidra) · [claudemarketplaces.com/mcp](https://claudemarketplaces.com/mcp) · [official remote MCP docs](https://platform.claude.com/docs/en/agents-and-tools/remote-mcp-servers) · [Data-Mania marketing MCP guide](https://www.data-mania.com/blog/top-10-claude-mcp-servers-for-marketing/)

---

### 7. Workflow Composition: The Three-Layer Claude Code Architecture

As skills and plugins have matured, a canonical three-layer architecture has emerged for Claude Code workflows:

```
CLAUDE.md       → ongoing project context (persistent)
Skills          → reusable reasoning playbooks (domain expertise)
Subagents       → isolated task execution (context-sandboxed)
```

MCP calls, skills, and subagents compose into repeatable multi-step workflow pipelines. A canonical example from the community: *code review workflow* → pull diff via MCP → inject code-review skill → spawn subagent per file → aggregate findings → post structured comment. ([Ranjan Kumar guide](https://ranjankumar.in/claude-code-guide-agentic-workflows))

Each subagent runs in its own context window with custom system prompt, specific tool access, and independent permissions ([Claude Code subagent docs](https://code.claude.com/docs/en/sub-agents) · [builder.io guide](https://www.builder.io/blog/claude-code-subagents)). Key principle: *"Chaining skills into multi-step workflows works best when each skill is atomic, outputs are written to explicit file paths, and handoffs between steps are clearly defined."*

Coverage: [Augment Code SDK guide](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities) · [MindStudio automate workflows](https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows) · [MindStudio 5 workflow patterns](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns) · [aimaker.substack Cowork review](https://aimaker.substack.com/p/claude-cowork-review-agentic-ai-guide) · [chatprd.ai workflows](https://www.chatprd.ai/how-i-ai/workflows/tool/claude)

---

### 8. Upcoming: Anthropic Subscription Restructuring (June 15, 2026)

Anthropic is splitting Claude subscriptions on **June 15, 2026**, with changes to Agent SDK credits that will affect indie hackers and developers running agentic workflows. ([DevToolPicks](https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026)) Full May 2026 release notes tracked at [Releasebot](https://releasebot.io/updates/anthropic).

---

## Cross-Source Patterns

**Pattern 1: Standardization enables scale (Web, GitHub, news)**
The SKILL.md open standard — first from Anthropic, adopted by Microsoft, OpenAI, Google — is the single biggest driver of the marketplace explosion. Every marketplace (SkillsMP, LobeHub, Skills.sh, ccpi) is built on top of SKILL.md compatibility. The Bosch/CMU study (18.5× growth in 20 days) makes this concrete. Sources: [agentskills.io spec](https://agentskills.io/specification) · [Mintlify](https://www.mintlify.com/blog/skill-md) · [Microsoft Learn](https://learn.microsoft.com/en-us/agent-framework/agents/skills) · [unite.ai](https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/)

**Pattern 2: Context window is the scarce resource (GitHub issues, blogs)**
Both MCP Tool Search (85% token reduction) and SKILL.md's progressive disclosure are direct responses to context window scarcity. As agent capabilities grow (more tools, more skills), managing what's in context becomes the core engineering challenge. The pattern is spreading: Codex and OpenCode are implementing the same lazy-loading feature. Sources: [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) · [GitHub #11364](https://github.com/anthropics/claude-code/issues/11364) · [gopubby article](https://ai.gopubby.com/mcp-tools-are-eating-82-of-your-context-window-the-10-minute-fix-for-claude-code-1619733d00dc)

**Pattern 3: Marketplace quality/security gap (comparison blogs, news)**
The same tension that plagued early npm and app stores is appearing: catalog size vs. quality. SkillsMP's 800K+ count looks impressive but is largely unfiltered GitHub scraping. Both [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) and [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) explicitly warn that malicious SKILL.md files can instruct agents to make unsafe calls. Curation (Anthropic's official marketplace, ClaudeMarketplaces, ClaudeSkills.info) is positioned as the quality differentiator. Sources: [smartscope review](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) · [openaitoolshub comparison](https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison)

**Pattern 4: Official vendor MCP integrations accelerating (news, docs)**
Meta (April 2026) and Google both launched official MCP servers — signaling MCP has crossed the threshold from developer curiosity to enterprise infrastructure. The pattern of major platforms releasing official MCPs is new in 2026 and likely to continue. Sources: [Meta Ads MCP guide](https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026) · [remote MCP docs](https://platform.claude.com/docs/en/agents-and-tools/remote-mcp-servers)

---

## Per-Platform Tables

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Primary source: skills design philosophy and architecture |
| Claude API Docs (Skills) | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Official skill spec, pricing, platform availability |
| Claude API Docs (MCP) | https://platform.claude.com/docs/en/agent-sdk/mcp | Official MCP connection docs |
| Claude API Docs (Remote MCP) | https://platform.claude.com/docs/en/agents-and-tools/remote-mcp-servers | Remote MCP server documentation |
| Claude Code Docs (Plugins) | https://code.claude.com/docs/en/plugins | Official plugin creation guide |
| Claude Code Docs (Subagents) | https://code.claude.com/docs/en/sub-agents | Official subagent documentation |
| TechCrunch | https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/ | Enterprise plug-in launch announcement (Feb 24, 2026) |
| VentureBeat | https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard | Enterprise Agent Skills + open standard coverage |
| The New Stack | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | Industry standards framing |
| Unite.AI | https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/ | Open standard ecosystem adoption |
| agentskills.io specification | https://agentskills.io/specification | SKILL.md formal specification |
| Mintlify blog | https://www.mintlify.com/blog/skill-md | SKILL.md format overview |
| Microsoft Learn | https://learn.microsoft.com/en-us/agent-framework/agents/skills | Microsoft VS Code/GitHub adoption |
| GitHub - anthropics/skills | https://github.com/anthropics/skills | Official Anthropic skills repo |
| Firecrawl blog | https://www.firecrawl.dev/blog/agent-skills | SKILL.md file structure explained |
| DeepWiki spec | https://deepwiki.com/agentskills/agentskills/2.2-skill.md-specification | SKILL.md specification deep-dive |
| agensi.io (open standard) | https://www.agensi.io/learn/agent-skills-open-standard | Open standard explainer |
| agensi.io (what is SKILL.md) | https://www.agensi.io/learn/what-is-skill-md | SKILL.md definition guide |
| agensi.io (skills explained) | https://www.agensi.io/learn/ai-agent-skills-explained-complete-guide | Complete skills explainer |
| agensi.io (plugins vs skills) | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Plugins vs. skills distinction |
| agensi.io (marketplace comparison) | https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026 | 2026 marketplace comparison |
| agensi.io (best marketplaces) | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Honest marketplace ranking |
| agensi.io (how marketplaces work) | https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work | Developer guide to marketplace mechanics |
| agensi.io (skills marketplace) | https://www.agensi.io/learn/skills-marketplace-ai-agents | "New App Store for AI Agents" framing |
| SkillsMP | https://skillsmp.com/ | Largest skills aggregator (800K+ claimed) |
| LobeHub Skills | https://lobehub.com/skills | 169K+ skills marketplace |
| LobeHub (skillsmp-downloader) | https://lobehub.com/skills/seankim-business-corp-system-skillsmp-downloader | Cross-marketplace skill download tool |
| LobeHub (Polymarket MCP) | https://lobehub.com/mcp/amolkodan-polymarket-claude-mcp | Polymarket MCP server listing |
| ClaudeMarketplaces | https://claudemarketplaces.com/ | Curated Claude-specific marketplace (150K monthly devs) |
| ClaudeMarketplaces (MCP) | https://claudemarketplaces.com/mcp | MCP server directory |
| MCP Market | https://mcpmarket.com/ | General MCP server discovery |
| MCP Market (Claude) | https://mcpmarket.com/businesses/claude | Claude-specific MCP servers |
| Skills.sh guide | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | Vercel skills.sh guide |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 marketplaces (with security warning) |
| SmartScope SkillsMP review | https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ | Independent SkillsMP size audit (66,500+ vs 800K+) |
| OpenAIToolsHub comparison | https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison | 6-platform side-by-side comparison |
| claudefa.st (50+ MCP servers) | https://claudefa.st/blog/tools/mcp-extensions/best-addons | Best MCP servers directory |
| claudefa.st (MCP Tool Search) | https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search | MCP Tool Search 95% context saving |
| atcyrus.com | https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide | MCP Tool Search context pollution explainer |
| JP Caparas / Medium | https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc | Lazy-loading MCP explainer |
| daily.dev | https://app.daily.dev/posts/claude-code-new-lazy-mcp-loading-they-finally-fixed-the-biggest-issue-of-claude-code--wwzicivi3 | Community reaction to lazy-loading launch |
| gopubby / AI Advances | https://ai.gopubby.com/mcp-tools-are-eating-82-of-your-context-window-the-10-minute-fix-for-claude-code-1619733d00dc | "82% of context window" framing |
| GitHub - claude-code #11364 | https://github.com/anthropics/claude-code/issues/11364 | Lazy-load MCP tool definitions feature request |
| GitHub - claude-code #23787 | https://github.com/anthropics/claude-code/issues/23787 | Lazy-load MCP tool schemas feature request |
| GitHub - claude-code #44536 | https://github.com/anthropics/claude-code/issues/44536 | Extend ToolSearch to all context components |
| GitHub - openai/codex #9266 | https://github.com/openai/codex/issues/9266 | Codex MCP lazy-load feature request |
| GitHub - opencode #9350 | https://github.com/anomalyco/opencode/issues/9350 | OpenCode MCP Tool Search feature request |
| Meta Ads MCP guide | https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026 | Meta official MCP launch (April 29, 2026) |
| Data-Mania marketing MCP | https://www.data-mania.com/blog/top-10-claude-mcp-servers-for-marketing/ | Top 10 MCP servers for marketing |
| jeremylongshore repo | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | ccpi marketplace repo (425 plugins, 2810 skills) |
| ccpi npm package | https://www.npmjs.com/package/@intentsolutionsio/ccpi | ccpi v2.0.0 on npm |
| ccpi wiki | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/wiki/Installing-Plugin-Packs | Plugin pack installation guide |
| jeremylongshore README (main) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md | Main README |
| jeremylongshore README (tree) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/tree/main?tab=readme-ov-file | README (340 plugins + 1367 skills count) |
| BrightCoding | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | Early ccpi coverage (270+ tools) |
| ccpi flyio-pack | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/tree/main/plugins/saas-packs/flyio-pack | Fly.io SaaS plugin example |
| ccpi clari SKILL.md | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/plugins/saas-packs/clari-pack/skills/clari-core-workflow-b/SKILL.md | Clari workflow skill example |
| ccpi intercom SKILL.md | https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/plugins/saas-packs/intercom-pack/skills/intercom-sdk-patterns/SKILL.md | Intercom SDK patterns skill |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 263+ skills for 10+ agents |
| Blake Crosley guide | https://blakecrosley.com/guides/claude-code | Claude Code complete guide (Hooks, MCP, Skills) |
| Augment Code guide | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Agent SDK skills reusable capabilities |
| builder.io subagents | https://www.builder.io/blog/claude-code-subagents | Subagent creation and debugging |
| Ranjan Kumar workflows | https://ranjankumar.in/claude-code-guide-agentic-workflows | Agentic workflow composition guide |
| MindStudio automate | https://www.mindstudio.ai/blog/claude-code-skills-automate-workflows | Skills for repetitive workflow automation |
| MindStudio patterns | https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns | 5 Claude Code workflow patterns |
| aimaker.substack | https://aimaker.substack.com/p/claude-cowork-review-agentic-ai-guide | Agentic AI workflow guide |
| chatprd.ai workflows | https://www.chatprd.ai/how-i-ai/workflows/tool/claude | Claude AI workflow examples |
| DevOps.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | Enterprise workflow framing |
| Plaban Nayak / Medium | https://nayakpplaban.medium.com/agent-skills-standard-for-smarter-ai-bde76ea61c13 | SKILL.md standards article |
| AB Vijay Kumar / Medium | https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996 | SKILL.md deep dive (March 2026) |
| Chris Ayers / CodeBytes | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide: skills + plugins + marketplaces |
| Tony Kipkemboi | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | Skills and plugins explained |
| Open Data Science | https://opendatascience.com/anthropic-introduces-agent-skills-making-claude-smarter-faster-and-more-specialized/ | Anthropic skills announcement coverage |
| Nimbalyst | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Claude Code plugins 2026 guide |
| DEV Community | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills & plugins guide |
| Mejba Ahmed | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills, plugins & CLIs |
| ScriptByAI | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate Claude Code resource list |
| Releasebot | https://releasebot.io/updates/anthropic | Anthropic May 2026 release notes tracker |
| DevToolPicks | https://devtoolpicks.com/blog/anthropic-splits-claude-subscriptions-agent-sdk-credit-june-2026 | June 15 subscription split announcement |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ n/a (skill pipeline did not execute)
├─ 🔵 X: 0 posts │ n/a
├─ 🔴 YouTube: 0 videos │ n/a
├─ 🟢 HN: 0 stories │ n/a
├─ 🟣 TikTok: 0 videos │ n/a
├─ 🩷 Instagram: 0 reels │ n/a
├─ 🦋 Bluesky: 0 posts │ n/a
├─ 📊 Polymarket: 0 markets │ n/a
├─ 🌐 Web: 80 pages │ 9 search queries
└─ 🗣️ Top sources: anthropic.com, agentskills.io, agensi.io, claudemarketplaces.com, skillsmp.com
```

---

## Data Gaps

- **Platform data missing:** The `/last30days` skill returned pipeline instructions rather than scraped platform data. Reddit, X/Twitter, YouTube, TikTok, HN, Bluesky, Polymarket, and GitHub trend data were not retrieved. ~0% coverage from social/community platforms; ~100% of this briefing is from web search.
- **Social signal unknown:** Community sentiment on Reddit (r/ClaudeAI, r/LocalLLaMA, etc.) and X discourse around skill marketplace quality, security concerns, and SKILL.md adoption is unverified.
- **HN discussion absent:** Hacker News likely has significant threads on Anthropic's open standard move and marketplace security concerns — not captured.
- **SkillsMP size discrepancy:** One source claims 800K+ skills; SmartScope independently measured 66,500+. True size unknown without direct scraping.
- **Skills.sh coverage:** Limited data on Vercel's skills.sh platform — its launch and growth trajectory are mentioned but not deeply covered.
- **Approximate web coverage:** Given 80+ URLs from 9 queries, web coverage is broad but not exhaustive. Estimated 70% of major published content captured.

---

## Key Quotes

> "A skill tells Claude how to think about a class of problems — not just what to do." — [Anthropic Engineering blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

> "The ecosystem grew 18.5× in just 20 days — from 2,179 skills on January 16 to over 40,000 by February 5." — Bosch Research / CMU February 2026 study, via [agensi.io](https://www.agensi.io/learn/skills-marketplace-ai-agents)

> "MCP tools are eating 82% of your context window." — [gopubby / AI Advances](https://ai.gopubby.com/mcp-tools-are-eating-82-of-your-context-window-the-10-minute-fix-for-claude-code-1619733d00dc)

> "They FINALLY FIXED the BIGGEST ISSUE of CLAUDE CODE!" — [daily.dev community](https://app.daily.dev/posts/claude-code-new-lazy-mcp-loading-they-finally-fixed-the-biggest-issue-of-claude-code--wwzicivi3) on MCP lazy loading

> "SkillsMP's 800,000 number is impressive until you realize it's indexed public GitHub repos with no quality filter beyond 'has 2 stars.'" — [agensi.io marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)

> "Microsoft has already adopted Agent Skills within VS Code and GitHub; so have popular coding agents like Cursor, Goose, Amp, OpenCode, and more." — [Anthropic/VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard)

> "CLAUDE.md holds ongoing project context, skills store reusable playbooks, and subagents handle isolated tasks where the main session only needs the result." — [Ranjan Kumar agentic workflows guide](https://ranjankumar.in/claude-code-guide-agentic-workflows)

> "Monthly search volume for skill marketplace terms grew 19x in two years: from 21,000 to over 400,000." — [agensi.io](https://www.agensi.io/learn/skills-marketplace-ai-agents)

> "Agent Skills: Anthropic's Next Bid to Define AI Standards" — [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

> "Chaining skills into multi-step workflows works best when each skill is atomic, outputs are written to explicit file paths, and handoffs between steps are clearly defined." — [Ranjan Kumar](https://ranjankumar.in/claude-code-guide-agentic-workflows)
