# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-14
**Query type:** GENERAL
**Sources:** X/Twitter, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 13 posts | 47 likes, 2 reposts | Mostly Japanese/Chinese practitioners; English posts on cost concerns |
| Web | ~43 pages | — | 13 via skill grounding + 30 via supplementary WebSearch |
| Reddit | 0 threads | — | 402 Payment Required errors; all queries failed |
| YouTube | 0 videos | — | 402 Payment Required; ScrapeCreators also failed |
| Hacker News | 0 stories | — | Not returned |
| TikTok | 0 videos | — | Not returned |
| Instagram | 0 reels | — | Not returned |
| Bluesky | 0 posts | — | Not returned |
| Polymarket | 0 markets | — | Not returned |
| GitHub | 0 direct results | — | No GITHUB_TOKEN configured |

---

## Synthesized Findings

### 1. The Claude Code Plugin Architecture: Skills vs Plugins vs MCP

The ecosystem has settled on a clear three-tier architecture. **Skills** are the atomic unit — individual `SKILL.md` files containing YAML frontmatter metadata and Markdown instructions that activate automatically when Claude detects relevant context, without requiring explicit slash commands. **Plugins** are the distribution format — installable packages that bundle one or more skills alongside agents, hooks, MCP server configurations, LSP servers, and background monitors. **MCP servers** are the integration layer — protocol-based tools that expose external services through a unified JSON-RPC interface, portable across all AI agent clients.

The key practical distinction: plugins are Claude Code-specific with deep hooks into the runtime; MCP servers are portable across Anthropic, OpenAI, Google, and Microsoft toolchains. Community guidance (echoed across agensi.io, nimbalyst.com, and the official docs) recommends building MCP servers for portable tools and plugins for Claude Code-specific integrations needing UI hooks or deeper session control.

- Official plugin docs: https://code.claude.com/docs/en/plugins
- Plugin vs skill explainer: https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained
- Plugins vs MCP guide: https://nimbalyst.com/blog/claude-code-plugins-guide/
- Plugin marketplace docs: https://code.claude.com/docs/en/plugin-marketplaces
- liteLLM plugin marketplace tutorial: https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace
- SKILL.md standard explainer: https://www.agensi.io/learn/what-is-skill-md

### 2. Marketplace Landscape: Scale and Diversity

The marketplace ecosystem has exploded in scale. As of May 14, 2026, **claudemarketplaces.com** — the largest aggregator directory — reports 4,200+ skills, 770+ MCP servers, 2,500+ connected marketplaces, and 150,000+ monthly visitors. The most-installed individual skill is `find-skills` with 1.1M+ installs, followed by `vercel-react-best-practices` (320k+) and `frontend-design` (299.9k+).

The **TonsOfSkills / CCPI** open-source marketplace (jeremylongshore on GitHub) is the largest standalone community repository: 425 plugins across 18 categories, 2,810 skills, 200 agents, and 16 contributors. It ships a CLI package manager (`ccpi`) for npm-style install/search/update workflows. Plugin types break down as: 309 AI Instruction plugins (SKILL.md markdown), 10 MCP Server plugins (Node.js/TypeScript), and 106 SaaS Skill Packs for platforms like Salesforce, Figma, Linear, and Notion.

**SkillsMP** (skillsmp.com) operates at a different scale entirely — 1.3M+ agent skills scraped and indexed from GitHub (minimum 2-star quality filter), covering 23 occupation groups and 867 SOC occupations. It is model-agnostic: compatible with Claude Code, OpenAI Codex CLI, and ChatGPT, all using the same SKILL.md installation directory convention.

**Anthropic's official repository** (`anthropics/claude-plugins-official`, 19.3k stars, 2.4k forks) maintains a curated directory of verified plugins, with external partner plugins in a separate `/external_plugins` directory. Submission is via a plugin-directory-submission form at clau.de.

- claudemarketplaces.com directory: https://claudemarketplaces.com/
- TonsOfSkills GitHub: https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- SkillsMP marketplace: https://skillsmp.com/
- SkillsMP API docs: https://skillsmp.com/docs/api
- Official Anthropic plugins repo: https://github.com/anthropics/claude-plugins-official
- Awesome Claude Plugins (ComposioHQ): https://github.com/ComposioHQ/awesome-claude-plugins
- Agensi marketplace: https://www.agensi.io/learn/claude-code-plugin-marketplace-guide
- Claude plugin hub (from skill): https://www.claudepluginhub.com
- ClaudeFast MCP extensions list: https://claudefa.st/blog/tools/mcp-extensions/best-addons
- Composio top plugins guide: https://composio.dev/content/top-claude-code-plugins
- BrightCoding skills marketplace post: https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers
- Firecrawl top 10 plugins guide: https://www.firecrawl.dev/blog/best-claude-code-plugins

### 3. MCP Has Won the Agent-to-Tool Layer

MCP (Model Context Protocol) has become the de facto integration standard for AI agents. With **97 million downloads** and native support from Anthropic, OpenAI, Google, and Microsoft, MCP has crossed from early-adopter to infrastructure. It operates as an open standard under the Linux Foundation, with production commitments from AWS, Cloudflare, and Google.

The "selection problem" has replaced the "capability problem": the bottleneck is no longer whether MCP can do something, but which of many competing MCP servers to choose. The dev.to MCP ecosystem deep-dive notes this transition as "a real maturation threshold." Production-ready servers exist for most developer tooling categories. Top servers across categories:

- **Developer Tools**: GitHub MCP (PRs, code search, issues), Sourcegraph (large codebase analysis), Linear (sprint management)
- **Productivity**: Slack, Notion, Google Drive
- **Data**: PostgreSQL, Google BigQuery
- **Search**: Brave Search, Perplexity, Tavily
- **Design**: Figma, Canva
- **Infrastructure**: Cloudflare, Shopify

The home automation story is notable: Home Assistant's official MCP integration is documented with a developer reporting Claude "basically did everything to make it functional" when autonomously configuring a dashboard.

The largest unmet demand remains **knowledge base MCP** — tools like UpNote lack public APIs, blocking community implementations. A secondary gap: no authoritative central discovery registry exists yet (though several enterprise solutions are filling this, covered in Finding 4).

- MCP ecosystem 2026 deep-dive (DEV.to): https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln
- Mirrored version: https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/
- MCP future roadmap (GetKnit): https://www.getknit.dev/blog/the-future-of-mcp-roadmap-enhancements-and-whats-next
- MCP in 2026 trends (MonkeyDigital): https://www.monkeydigital.org/future-of-ai-agents-with-mcp-in-2026-trends-predictions/
- Best MCP servers for agents (Toloka): https://toloka.ai/blog/best-mcp-servers-for-ai-agents/
- Best MCP servers for developers (Firecrawl): https://www.firecrawl.dev/blog/best-mcp-servers-for-developers
- 18 best DevOps MCP servers (k8slens/Medium): https://medium.com/k8slens/18-best-devops-mcp-servers-for-2026-the-definitive-guide-bfde04654a35
- AI agent protocol ecosystem map 2026: https://www.digitalapplied.com/blog/ai-agent-protocol-ecosystem-map-2026-mcp-a2a-acp-ucp
- Build vs buy MCP runtime (DEV.to): https://dev.to/arcade/should-you-build-or-buy-an-mcp-runtime-for-enterprise-ai-agents-in-2026-36jg
- Microsoft MCP tools guide: https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools

### 4. Enterprise MCP Registries: Governance Catching Up to Adoption

Enterprise adoption of MCP has outpaced governance tooling, and a cluster of new registry/gateway products has emerged to close the gap. Key gaps being addressed: no server-level access restrictions, no audit trail for agent tool calls, no governance at the registry layer, and data-egress risks for hosted registries.

**Kong MCP Registry** (launched February 2026) is an enterprise directory within Kong Konnect that registers, discovers, and governs MCP servers, designed to comply with the AI Alliance Interoperability Framework (AAIF). It targets platform teams managing many MCP servers across organizations.

**AWS Agent Registry** (preview since April 2026), part of Amazon Bedrock AgentCore, is a private governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources. Aimed at enterprises needing private, internal tool registries.

**IBM MCP Context Forge** (open source) is an AI Gateway and proxy that federates MCP, A2A, and REST/gRPC APIs with centralized governance, discovery, and observability. The open-source positioning differentiates it from Kong's and AWS's commercial offerings.

The **official MCP Registry** at registry.modelcontextprotocol.io is the community reference registry maintained by Anthropic.

- Official MCP Registry: https://registry.modelcontextprotocol.io/
- Kong MCP Registry product: https://konghq.com/products/mcp-registry
- Kong press release (Feb 2026): https://konghq.com/company/press-room/press-release/kong-introduces-mcp-registry
- Kong PR Newswire announcement: https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html
- AWS Agent Registry announcement (Apr 2026): https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/
- IBM MCP Context Forge (GitHub): https://github.com/IBM/mcp-context-forge
- Enterprise MCP Gateway Registry (community): https://github.com/agentic-community/mcp-gateway-registry
- MACH Alliance MCP Registry: https://machalliance.org/mach-alliance-mcp-registry
- Best MCP registries comparison (TrueFoundry): https://www.truefoundry.com/blog/best-mcp-registries

### 5. Agent Skills as a Cross-Platform Open Standard

The `SKILL.md` format has emerged as a cross-vendor open standard for agent capabilities. Specified at **agentskills.io** and originally developed by Anthropic, it is now adopted by Claude Code, OpenAI Codex CLI, Gemini CLI, GitHub Copilot (VS Code), Cursor, Cline, Windsurf, and OpenCode.

The specification defines: a skill directory containing a `SKILL.md` file with YAML frontmatter (name, description, optional config) and Markdown instructions; supporting directories for scripts, references, and assets; and progressive disclosure (metadata loaded first, full instructions loaded on demand to reduce token overhead).

By March 2026, the Antigravity Awesome Skills community library had cataloged 1,234+ skills compatible with 16+ agent runtimes. OpenAI's Codex Skills docs confirm the same `~/.claude/skills/` and `~/.codex/skills/` installation conventions, making the standard genuinely portable.

Claude's own platform docs and the VS Code agent skills documentation confirm the format is treated as a first-class capability by multiple vendors, reducing lock-in concerns for skill authors.

- Agent Skills specification: https://agentskills.io/specification
- What is SKILL.md (Agensi): https://www.agensi.io/learn/what-is-skill-md
- Agent Skills open standard explainer: https://www.agensi.io/learn/agent-skills-open-standard
- Claude API agent skills overview: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
- OpenAI Codex skills docs: https://developers.openai.com/codex/skills
- VS Code agent skills: https://code.visualstudio.com/docs/copilot/customization/agent-skills
- Microsoft Agent Framework skills: https://learn.microsoft.com/en-us/agent-framework/agents/skills
- Deep dive SKILL.md (Medium): https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996
- Agent Skills overview (inference.sh): https://inference.sh/blog/skills/agent-skills-overview
- Complete AI agent skills guide (The Prompt Index): https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html
- anthropics/skills public repo: https://github.com/anthropics/claude-code/tree/main/plugins
- Claude Code plugins README: https://github.com/anthropics/claude-code/blob/main/plugins/README.md

### 6. Notable Plugins and Token-Efficiency Innovations

The BrightCoding analysis of the Claude Skills Marketplace highlights a key architectural breakthrough: skills that execute Python scripts locally rather than loading entire codebases into context, achieving up to 97.6% token savings on bulk operations (50-file processing drops from ~25,000 tokens to ~600 tokens). This reframes skills from "prompt augmentation" to "execution offloading."

Notable production plugins gaining traction:
- **Superpowers** — lifecycle planning + TDD, debugging, code review, infra validation in one bundle: https://claude.com/plugins/superpowers
- **claude-mem** — session memory persistence via SQLite + Chroma vector search: https://github.com/thedotmack/claude-mem
- **local-review** — 5 parallel agents reviewing uncommitted code simultaneously
- **agent-peer-review** — multi-model Claude + Codex debate with web search escalation: https://github.com/jcputney/agent-peer-review
- **Plannotator** — structured plan annotation and sharing UI: https://plannotator.ai/
- **Shipyard** — production lifecycle with IaC validation (Terraform, Ansible, Docker, K8s, CloudFormation): https://shipyard.build/agents/claude-code/
- **dev-browser** — web testing alternative to Playwright with reduced context load: https://github.com/SawyerHood/dev-browser
- **TypeScript/Rust LSP plugins** — Language Server Protocol integration for real-time type checking: https://claude.com/plugins/typescript-lsp
- **mhattingpete/claude-skills-marketplace** — git automation, test fixing, code review with claimed 90-99% token reduction: https://github.com/mhattingpete/claude-skills-marketplace

The **html-anything** open-source project (announced on X by @tuturetom) supports 75 Skills across all code agents (Claude Code, Codex, OpenClaw, Hermes), with 9 export formats and 15,000 lines of code built in 3 days, illustrating rapid ecosystem growth: https://x.com/tuturetom/status/2054860276088860819

Production workflow templates for structured end-to-end development (requirements → design → implementation → QA via specialized subagents) are available at: https://github.com/shinpr/claude-code-workflows and via Awesome Claude Plugins: https://github.com/ComposioHQ/awesome-claude-plugins

- Scott Spence post on plugin marketplaces: https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces (returned 403)
- Claude Code agent skills guide (Agensi): https://www.agensi.io/learn/claude-code-plugin-marketplace-guide

### 7. Practitioner Signals from X: Automation, Cost, and Adoption

The X/Twitter signal, while dominated by Japanese and Chinese practitioners, reveals consistent themes. The `/goal` slash command is generating excitement as a zero-human-intervention automation loop — one user (@osuruko1977) reports writing a single achievement condition, sleeping, and returning to completed tasks: "Describe the goal, leave it alone → all tasks complete while sleeping." The `/p` (headless `claude -p`) pipeline pattern is widely adopted for automated content generation, but practitioners warn about cost surprise: one Japanese developer (@develogon0) notes users auto-generating content with `claude -p` without realizing they're accumulating large bills.

English commentary flags the cost story directly: "AI coding tools sold as cost-cutters. Reality: one developer spending $150k/month on tokens. Anthropic quietly doubled Claude Code cost estimates." (@fdevbpolymarket). A Chinese practitioner (@david1989_zhu) articulates the core value proposition more precisely than most marketing copy: "The outrageous thing about Claude Code is not that it writes better code, it's that it breaks down the barrier from idea to running result — you describe the goal, it fills in implementation, debugging, and verification."

The **Claude Code CLI 2.1.116** changelog (via @ClaudeCodeLog, 25 likes) from April 21 represents the most-engaged technical X post in the dataset — terminal rendering fixes for Devanagari/Indic scripts and Kitty keyboard protocol improvements — suggesting an active global developer base pushing the tool into non-English writing environments.

X post URLs:
- @develogon0 (claude -p cost warning): https://x.com/develogon0/status/2054860949312720919
- @osuruko1977 (/goal automation): https://x.com/osuruko1977/status/2054861352355905611
- @shota7180 (file organization use cases): https://x.com/shota7180/status/2054861716849320055
- @1osabori (Claude Code for content workflows): https://x.com/1osabori/status/2054861422103040118
- @tuturetom (html-anything 75 skills): https://x.com/tuturetom/status/2054860276088860819
- @ClaudeCodeLog (CLI 2.1.116 changelog): https://x.com/ClaudeCodeLog/status/2046404260091273354
- @david1989_zhu (core value proposition): https://x.com/david1989_zhu/status/2054860814046404724
- @fdevbpolymarket (cost concerns): https://x.com/fdevbpolymarket/status/2054860432821694598

---

## Cross-Source Patterns

**Pattern 1: Discovery is the dominant unsolved problem**
- Appeared on: Web (MCP ecosystem articles, truefoundry.com, dev.to), X (low signal here)
- Multiple sources independently identify "no authoritative central registry" as the top gap. The dev.to MCP article states it plainly; the truefoundry registry comparison exists precisely because users are choosing between 5+ competing registries. The claudemarketplaces.com directory's 150,000 monthly visitors signals real demand for a neutral aggregation layer.
- Key quote: "The bottleneck is no longer the protocol itself; it's discovery, and knowing when to build versus when to find." — dev.to MCP ecosystem article

**Pattern 2: Token efficiency through execution offloading is a competitive differentiator**
- Appeared on: Web (brightcoding.dev, tonsofskills, skillsmp)
- Across multiple marketplace/plugin write-ups, the biggest value claims are not about AI quality but about reducing token consumption: 97.6% savings (claude-skills-marketplace), 90-99% reduction (brightcoding), running 5 parallel reviewers cheaper than one full-context load. This positions skills as a cost-management layer, not just a convenience layer.

**Pattern 3: Cross-vendor standardization is real and accelerating**
- Appeared on: Web (agentskills.io, agensi.io, inference.sh, openai docs, microsoft docs, VS Code docs)
- The SKILL.md format is now documented in official Microsoft, OpenAI, and Google materials alongside Anthropic's. With 16+ agent runtimes supporting the format and 1.3M+ indexed skills on SkillsMP, the ecosystem has reached the scale where vendor-neutral skill authorship is a genuine option.

**Pattern 4: Cost anxiety is a real adoption friction point**
- Appeared on: X (@develogon0, @fdevbpolymarket)
- Two independent X posts on the same day raise cost concerns around Claude Code: one warning about `claude -p` pipeline costs, another referencing a $150k/month developer case. This matches the broader narrative that Anthropic "quietly doubled Claude Code cost estimates." This friction is not reflected in the marketing-oriented web content but surfaces clearly in practitioner social media.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @ClaudeCodeLog | Claude Code CLI 2.1.116 changelog: Fixed Devanagari rendering, Ctrl+- undo, Cmd+Left/Right line nav | 25 | 1 | https://x.com/ClaudeCodeLog/status/2046404260091273354 |
| @develogon0 | Claude Code articles/content auto-gen uses claude -p; watch your bills | 5 | 1 | https://x.com/develogon0/status/2054860949312720919 |
| @osuruko1977 | /goal command: write one condition, sleep, wake to completed tasks | 5 | 0 | https://x.com/osuruko1977/status/2054861352355905611 |
| @shota7180 | File organization, meeting minutes, document management now delegatable to Claude Code | 3 | 0 | https://x.com/shota7180/status/2054861716849320055 |
| @1osabori | Power users: account design, post drafting (5-10/day), competitor analysis, script research | 3 | 0 | https://x.com/1osabori/status/2054861422103040118 |
| @tuturetom | html-anything open source: 75 Skills, 9 export formats, supports claude code/codex/openclaw/hermes | 2 | 0 | https://x.com/tuturetom/status/2054860276088860819 |
| @david1989_zhu | Claude Code's real breakthrough: eliminates friction from idea to running result | 1 | 0 | https://x.com/david1989_zhu/status/2054860814046404724 |
| @fdevbpolymarket | One dev: $150k/month on tokens. Anthropic doubled cost estimates. Math isn't mathing. | 1 | 0 | https://x.com/fdevbpolymarket/status/2054860432821694598 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Aggregator: 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces |
| GitHub (jeremylongshore) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | TonsOfSkills: 425 plugins, 2,810 skills, 200 agents, CCPI CLI tool |
| skillsmp.com | https://skillsmp.com/ | 1.3M+ agent skills; cross-vendor SKILL.md index |
| github.com/anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | Official Anthropic-curated plugin directory (19.3k stars) |
| agensi.io (marketplace guide) | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Plugin scoping, /plugin command, marketplace anatomy |
| agensi.io (plugins vs skills) | https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained | Definitive taxonomy: skills=content, plugins=distribution |
| agensi.io (SKILL.md) | https://www.agensi.io/learn/what-is-skill-md | SKILL.md format reference |
| agensi.io (open standard) | https://www.agensi.io/learn/agent-skills-open-standard | Cross-vendor adoption status |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Plugin components, install methods, MCP vs plugin guidance |
| brightcoding.dev | https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers | Token efficiency: 97.6% savings via execution offloading |
| composio.dev | https://composio.dev/content/top-claude-code-plugins | Top 10 plugins with descriptions and URLs |
| github.com/ComposioHQ | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin registry, 500+ SaaS integrations |
| github.com/mhattingpete | https://github.com/mhattingpete/claude-skills-marketplace | git-pushing, test-fixing, architecture diagram skills |
| github.com/shinpr | https://github.com/shinpr/claude-code-workflows | Production-ready multi-agent dev workflow |
| code.claude.com (plugins) | https://code.claude.com/docs/en/plugins | Official plugin creation docs |
| code.claude.com (marketplaces) | https://code.claude.com/docs/en/plugin-marketplaces | Official marketplace distribution docs |
| platform.claude.com | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Claude API agent skills reference |
| claude.com/plugins/superpowers | https://claude.com/plugins/superpowers | Superpowers plugin (lifecycle + TDD + code review) |
| claude.com/plugins/typescript-lsp | https://claude.com/plugins/typescript-lsp | TypeScript LSP plugin |
| github.com/thedotmack/claude-mem | https://github.com/thedotmack/claude-mem | Session memory persistence (SQLite + Chroma) |
| github.com/jcputney/agent-peer-review | https://github.com/jcputney/agent-peer-review | Multi-model Claude + Codex review |
| github.com/SawyerHood/dev-browser | https://github.com/SawyerHood/dev-browser | Lightweight web testing plugin |
| plannotator.ai | https://plannotator.ai/ | Structured plan annotation/sharing |
| shipyard.build | https://shipyard.build/agents/claude-code/ | IaC validation lifecycle plugin |
| agentskills.io | https://agentskills.io/specification | Agent Skills open specification |
| inference.sh | https://inference.sh/blog/skills/agent-skills-overview | Agent Skills ecosystem overview |
| dev.to/sahil_kat (MCP 2026) | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | MCP ecosystem maturity analysis |
| codeongrass.com | https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/ | Mirror of MCP ecosystem article |
| toloka.ai | https://toloka.ai/blog/best-mcp-servers-for-ai-agents/ | Curated MCP server categories |
| firecrawl.dev (MCP) | https://www.firecrawl.dev/blog/best-mcp-servers-for-developers | Best MCP servers by use case |
| firecrawl.dev (plugins) | https://www.firecrawl.dev/blog/best-claude-code-plugins | Top 10 Claude Code plugins |
| medium.com/k8slens | https://medium.com/k8slens/18-best-devops-mcp-servers-for-2026-the-definitive-guide-bfde04654a35 | 18 best DevOps MCP servers |
| getknit.dev | https://www.getknit.dev/blog/the-future-of-mcp-roadmap-enhancements-and-whats-next | MCP roadmap and future features |
| monkeydigital.org | https://www.monkeydigital.org/future-of-ai-agents-with-mcp-in-2026-trends-predictions/ | MCP trends and predictions |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-protocol-ecosystem-map-2026-mcp-a2a-acp-ucp | Protocol landscape: MCP vs A2A vs ACP vs UCP |
| dev.to/arcade (MCP runtime) | https://dev.to/arcade/should-you-build-or-buy-an-mcp-runtime-for-enterprise-ai-agents-in-2026-36jg | Build vs buy MCP runtime analysis |
| registry.modelcontextprotocol.io | https://registry.modelcontextprotocol.io/ | Official MCP server registry |
| konghq.com (registry) | https://konghq.com/products/mcp-registry | Kong enterprise MCP registry product |
| konghq.com (press) | https://konghq.com/company/press-room/press-release/kong-introduces-mcp-registry | Kong MCP registry launch announcement |
| prnewswire.com | https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html | Kong PR Newswire announcement |
| aws.amazon.com | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry (Bedrock AgentCore) preview |
| github.com/IBM/mcp-context-forge | https://github.com/IBM/mcp-context-forge | IBM open-source MCP gateway + registry |
| github.com/agentic-community | https://github.com/agentic-community/mcp-gateway-registry | Community enterprise MCP gateway |
| machalliance.org | https://machalliance.org/mach-alliance-mcp-registry | MACH Alliance MCP registry |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries comparison |
| learn.microsoft.com (MCP tools) | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Microsoft agent framework MCP tools |
| learn.microsoft.com (skills) | https://learn.microsoft.com/en-us/agent-framework/agents/skills | Microsoft agent framework skills |
| developers.openai.com | https://developers.openai.com/codex/skills | OpenAI Codex skills documentation |
| code.visualstudio.com | https://code.visualstudio.com/docs/copilot/customization/agent-skills | VS Code agent skills |
| medium.com/abvijaykumar | https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996 | Deep dive: SKILL.md format internals |
| thepromptindex.com | https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html | AI Agent Skills complete guide |
| docs.litellm.ai | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | liteLLM plugin marketplace tutorial |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers for Claude Code |
| skillsmp.com/docs/api | https://skillsmp.com/docs/api | SkillsMP REST API (OpenAPI 3.0) |
| scottspence.com | https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces | Organizing skills into marketplaces (403 at time of access) |

---

## Stats Block

```
├─ 🔵 X: 13 posts │ 47 likes │ 2 reposts
├─ 🌐 Web: ~43 pages │ claudemarketplaces.com, github.com, skillsmp.com, agensi.io, nimbalyst.com, agentskills.io, konghq.com, aws.amazon.com, registry.modelcontextprotocol.io, and 30+ more
├─ 🟠 Reddit: 0 threads │ API 402 errors (all queries failed)
├─ 🔴 YouTube: 0 videos │ API 402 errors
├─ 🟢 HN: 0 stories
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
└─ 🗣️ Top voices: @ClaudeCodeLog, @tuturetom, @develogon0 │ claudemarketplaces.com, agensi.io, agentskills.io
```

---

## Data Gaps

- **Reddit**: All queries returned HTTP 402 Payment Required. Zero Reddit coverage — this is the highest-traffic community for Claude Code discussions (r/ClaudeAI, r/LocalLLaMA, r/MachineLearning) and its absence is a significant gap.
- **YouTube**: ScrapeCreators API returned HTTP 402. No video tutorials, walkthroughs, or demonstrations of plugin installation or MCP server setup captured.
- **Hacker News**: No results returned. HN regularly has threads on MCP and Claude Code tooling; absence likely reflects timing (no major launch in the window) rather than API failure.
- **GitHub direct results**: No GITHUB_TOKEN configured; GitHub API unavailable. Star counts and commit activity for specific repos were inferred from web-fetched GitHub pages, not direct API queries.
- **X coverage**: 13 posts, majority non-English (Japanese/Chinese). English-language technical discourse on X about this topic was sparse on the day of collection. The most technical X post (CLI changelog) is 23 days old (April 21).
- **Skill web grounding**: The skill's internal web search surfaced claudepluginhub.com as a top domain but the specific articles/pages from that domain were not individually retrievable in the evidence.
- **Coverage estimate**: Web (~43 pages) is strong; practitioner community voice (Reddit, YouTube) is near-zero. Overall coverage approximately 50-60% of what full API access would yield.

---

## Key Quotes

> "A plugin is a bundle of Claude Code extensions — skills, MCP servers, commands, hooks, or agents — packaged as one installable unit." — [code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins)

> "The transition — from capability question to selection question — marks a real maturation threshold." — Sahil Kat on [DEV.to MCP ecosystem in 2026](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln)

> "The bottleneck is no longer the protocol itself; it's discovery, and knowing when to build versus when to find." — [MCP ecosystem analysis](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln)

> "97.6% savings on bulk operations — processing 50 files drops from ~25,000 tokens to ~600 tokens." — [BrightCoding Claude Skills Marketplace review](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers)

> "Claude Code（以及同类 coding agent）真正的'离谱'点不是更会写代码，而是把'从想法到可运行结果'的门槛打穿了" ("The outrageous thing about Claude Code is not that it writes better code, but that it eliminates the friction from idea to running result.") — @david1989_zhu on [X](https://x.com/david1989_zhu/status/2054860814046404724)

> "AI coding tools sold as cost-cutters. Reality: one developer spending $150k/month on tokens." — @fdevbpolymarket on [X](https://x.com/fdevbpolymarket/status/2054860432821694598)

> "By March 2026, the community Antigravity Awesome Skills library had cataloged over 1,234 skills compatible with 16+ different agents across the ecosystem." — [agentskills.io](https://agentskills.io/specification)

> "MCP currently operates on an honor system — there's no signed or attested responses for sensitive operations." — commenter quoted in [MCP ecosystem article](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln)

> "A plugin can include hooks...and MCP servers...This is more powerful than a SKILL.md skill — and requires more trust." — [agensi.io plugins vs skills guide](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained)

> "ヤバい！！！Claude Code /goal で人間の作業時間が0分になる時代きた！！！" ("Claude Code /goal has brought the era of zero human work time!") — @osuruko1977 on [X](https://x.com/osuruko1977/status/2054861352355905611)
