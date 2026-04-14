# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-14
**Query type:** GENERAL
**Sources:** X/Twitter, Web (skill), Web (supplementary search)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 16 posts | 144 likes, 25 reposts, 47 replies | 8 clusters detailed; 8 additional posts not itemized |
| Web | 7 pages | — | Domains: github.com, learn.microsoft.com, courses.taltech.akaver.com, developers.googleblog.com (URLs not surfaced by skill) |
| Web (supplementary) | 58 pages | — | via WebSearch across 6 targeted queries |

---

## Synthesized Findings

### 1. Anthropic Defines the Agent Skills Open Standard — Industry Follows

Anthropic's December 2025 release of the **Agent Skills specification** as an open standard is now the defining event shaping the entire ecosystem. The spec centers on `SKILL.md` — a lightweight markdown file with frontmatter that encodes reusable agent instructions. The format was rapidly adopted cross-platform: **OpenAI adopted it for Codex CLI and ChatGPT**, and tools like Cursor share compatible file formats. This interoperability is framed as Anthropic's "next bid to define AI standards" alongside the Model Context Protocol (MCP).

Skills differ from other Claude Code extension points: they use only 30–50 tokens until invoked, auto-load when relevant context is detected, and can be distributed via marketplaces or Git repositories. The full extension taxonomy for Claude Code in 2026 is: **CLAUDE.md** (persistent context), **Skills** (invocable workflows), **MCP Servers** (external tools/APIs), **Subagents** (isolated loop agents), **Agent Teams** (multi-session coordination, launched Feb 2026), and **Plugins** (bundles of all of the above).

Sources: X ([@Radha_AI](https://x.com/Radha_AI/status/2043947698991350071), [@Zingylabs](https://x.com/Zingylabs/status/2043968041906798618)), Web ([thenewstack.io](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/), [code.claude.com docs](https://code.claude.com/docs/en/features-overview), [morphllm.com overview](https://www.morphllm.com/claude-code-extensions), [morphllm.com comparison](https://www.morphllm.com/claude-code-skills-mcp-plugins), [dev.to guide](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k), [Medium/Muneeb Ahmad](https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff), [explainx.ai complete guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide), [fungies.io SKILL.md guide](https://fungies.io/ai-agent-skills-skill-md-guide-2026/), [calmops.com guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/), [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/))

---

### 2. Anthropic Academy Launches 13 Free Courses — Agent Skills Has Its Own Course

Anthropic Academy launched on **March 2, 2026**, offering 13 free courses with official certificates. The course **"Introduction to Agent Skills"** is one of 13, alongside courses on Claude 101, Claude Code in Action, Building with the Claude API, and MCP. Courses are hosted on Skilljar and certificates can be added to LinkedIn. Multiple X users amplified the launch on April 14, calling it superior to paid alternatives.

**DeepLearning.AI** partnered with Anthropic for a short course titled "Agent Skills with Anthropic." A **Udemy course** ("Agent Skills: Claude Code, Cursor and MCP in Practice") and **Anthropic Certifications** platform further expand training options. The education signal is strong: Anthropic is clearly trying to canonicalize its skills spec by training the developer base directly.

Sources: X ([@Radha_AI](https://x.com/Radha_AI/status/2043947698991350071), [@Zingylabs](https://x.com/Zingylabs/status/2043968041906798618)), Web ([anthropic.skilljar.com](https://anthropic.skilljar.com/), [termdock.com guide](https://www.termdock.com/en/blog/anthropic-academy-claude-courses-guide), [pasqualepillitteri.it](https://pasqualepillitteri.it/en/news/371/anthropic-academy-free-courses-claude), [aitoolsclub.com](https://aitoolsclub.com/10-free-anthropic-academy-ai-courses-to-master-claude-claude-code-and-mcp/), [deeplearning.ai](https://www.deeplearning.ai/short-courses/agent-skills-with-anthropic/), [udemy.com](https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/), [anthropiccertifications.com](https://www.anthropiccertifications.com/courses), [fabianmiranda.com](https://fabianmiranda.com/blog/2026-03-15-anthropic-academy-free-ai-training))

---

### 3. Claude Code Plugin & Skill Ecosystem — Official vs. Community Divide

**Official**: Anthropic's [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) repo had 101 plugins as of March 2026. The [official marketplace.json](https://github.com/anthropics/claude-code/blob/main/.claude-plugin/marketplace.json) is built into Claude Code. Docs at [code.claude.com/docs/en/plugin-marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) explain the marketplace-as-git-repo pattern.

**Community**: [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) now hosts **340 plugins + 1,367 agent skills**, with a dedicated CCPI package manager (`pnpm add -g @intentsolutionsio/ccpi`). README: [github.com/jeremylongshore/…/README.md](https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md). An X user reported discovering a community registry with "11K+ plugins, 63K+ agent skills."

**Aggregators**: [claudemarketplaces.com](https://claudemarketplaces.com/) lists 2,865+ marketplaces. [ClaudePluginHub.com](https://www.claudepluginhub.com/plugins/jeremylongshore-flyio-pack-plugins-saas-packs-flyio-pack) indexes 14,083+ plugins. [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons) curates 50+ best MCP servers. [popularaitools.ai](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) and [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) publish curated lists.

**Security**: [PromptArmor documented](https://www.promptarmor.com/resources/hijacking-claude-code-via-injected-marketplace-plugins) a "Hijacking Claude Code via Injected Marketplace Plugins" attack vector — a live concern as community registries scale. [liteLLM](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) provides a managed plugin marketplace option. [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) tested 10 plugins and recommends 4.

MCP Tool Search in Claude Code now reduces context usage by up to 95% via lazy loading.

Sources: X ([@sarunkumar098](https://x.com/sarunkumar098/status/2043951290406043749))

---

### 4. Binance AI Agent Skills SDK — Crypto as a First-Mover Use Case

Binance has run the most publicly-documented skills rollout to date, moving in two waves:
- **Early March 2026**: 7 skills covering spot trading, wallet/token analytics, market rankings, meme coin tracking, smart money signals, and contract risk checks.
- **April 2, 2026**: 13 additional skills adding derivatives trading, algorithmic execution, fiat, payments, yield generation, and real-world assets (RWA).

The [binance/binance-skills-hub](https://github.com/binance/binance-skills-hub) GitHub repo is described as "an open skills marketplace that gives AI agents native access to crypto — both centralized and decentralized." Agents from OpenClaw, Claude, and others can plug in through standardized interfaces. **Binance Ai Pro** (beta, March 2026) is a one-stop agentic trading product layered on top of the skills infrastructure.

@BinanceAcademy's April 14 post promoting the 13-skill expansion was the highest-engagement X post in the cluster (23 likes, 7 replies).

Sources: X ([@BinanceAcademy](https://x.com/BinanceAcademy/status/2043932265403535683)), Web ([binance.com announcement — 13 skills](https://www.binance.com/en/support/announcement/detail/bafb9dda6cbb47d5882a4090c31d4c64), [binance.com — alpha/derivatives/margin skills](https://www.binance.com/en/academy/articles/binance-ai-agent-skills-alpha-derivatives-margin-and-assets), [binance.com — Square AI content skill](https://www.binance.com/en/support/announcement/detail/7ba0c9871b17429ba8af46f0c6ec187c), [fxnewsgroup.com](https://fxnewsgroup.com/forex-news/cryptocurrency/binance-launches-13-new-ai-agent-skills/), [banklesstimes.com](https://www.banklesstimes.com/articles/2026/04/02/binance-expands-ai-ecosystem-with-13-new-new-agent-skills/), [businessupturn.com](https://www.businessupturn.com/brand-post/binance-enhances-ai-agent-skills-with-comprehensive-trading-asset-management-and-market-intelligence-capabilities/), [mexc.co](https://www.mexc.co/news/844826), [cryptobreaking.com](https://www.cryptobreaking.com/binance-beta-launches-ai-pro/), [Medium/@gemQueenx](https://medium.com/@gemQueenx/binance-launches-7-ai-agent-skills-enabling-trading-wallet-access-and-real-time-market-data-via-dace4bcfe4fd))

---

### 5. Third-Party Registries — ClawHub, SkillsMP, ToolHive, AWS

**ClawHub** ([clawhub.ai](https://clawhub.ai/) / [clawhub.biz](https://clawhub.biz/)): Public skill registry for OpenClaw. As of February 2026: **3,286 community-built skills, 1.5M+ downloads**. Some sources cite 20,000+ skills as a larger figure. Open-source at [github.com/openclaw/clawhub](https://github.com/openclaw/clawhub). Documented at [docs.openclaw.ai/tools/clawhub](https://docs.openclaw.ai/tools/clawhub). Guides: [skywork.ai ClawHub overview](https://skywork.ai/skypage/en/clawhub-ai-skills-registry/2038574818194624512), [skywork.ai OpenClaw guide](https://skywork.ai/skypage/en/clawhub-openclaw-skill-registry/2038573559848898560), [Medium/Mehul Gupta explainer](https://medium.com/data-science-in-your-pocket/what-is-openclaw-clawhub-e123c2dd0db1), [security guide after March 2026 crisis](https://blink.new/blog/openclaw-clawhub-skills-safe-install-guide-2026). Tool space listing: [aitoolsspace.com](https://www.aitoolsspace.com/en/tools/clawhub).

**SkillsMP** ([skillsmp.com](https://skillsmp.com)): Claims **800,000+ agent skills** for Claude, Codex & ChatGPT — the largest aggregate marketplace. Intelligent filtering by occupation, author, and popularity. KDnuggets coverage: [top-5-agent-skill-marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents).

**ToolHive (Stacklok)** — [April 6, 2026 update](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates): Added agent skills support to both the CLI and Registry Server. Key: skills teach agents *when and how* to use MCP tools (not just *what* tools exist). Registry features: namespace isolation, multi-version tracking, keyword/status search, lifecycle management (active/deprecated/archived).

**AWS Agent Plugins** ([github.com/awslabs/agent-plugins](https://github.com/awslabs/agent-plugins)): Equips AI coding agents with skills to architect, deploy, and operate on AWS.

**OpenAI Codex** ([developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)): Adopted Anthropic's SKILL.md format, confirming cross-vendor standardization.

**Spring AI**: Published "Agentic Patterns (Part 1): Agent Skills — Modular, Reusable Capabilities" ([spring.io, Jan 13, 2026](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/)).

---

### 6. Scientific & Research Domain Skills (K-Dense)

K-Dense released an **updated skill for Parallel Web Systems** (@p0) as part of their "Scientific Agent Skills ecosystem" — enabling agent scientists to use the Parallel CLI for search, deep search, webpage extraction, and data enrichment. The skill is also available in K-Dense BYOK and K-Dense Web.

Sources: X ([@k_dense_ai](https://x.com/k_dense_ai/status/2043880880863908267))

---

### 7. Web3/DeFi Agent Skills — DSCVR and the On-Chain Subscription Model

**DSCVR** has launched a subscription-gated agent skills tier (Pro or Elite, paid on-chain). Their agent reads market sentiment, tracks smart money, and fires alerts pre-emptively. The April 9 teaser post ("You: refreshing Polymarket every 30 seconds. Your DSCVR-powered agent: Already Knew. Already acted.") was the highest-engagement post in the dataset (36 likes, 6 reposts, 11 replies).

**Scepter Agent** built `$SIZE` on the "official Agent Skills SDK released today" (April 14) — a meta-play DeFi agent that converts idle creator fees into leveraged positions and burns SIZE tokens.

Sources: X ([@DSCVR1 — live subscription](https://x.com/DSCVR1/status/2043940770529612269), [@DSCVR1 — teaser](https://x.com/DSCVR1/status/2042272640673730617), [@ScepterAgent](https://x.com/ScepterAgent/status/2043951423553987011))

---

## Cross-Source Patterns

### Pattern 1: SKILL.md as a Cross-Platform Standard
- **Platforms**: X + Web (thenewstack.io, explainx.ai, fungies.io, openclaw/clawhub, developers.openai.com)
- Anthropic's SKILL.md spec is now adopted by OpenAI (Codex), OpenClaw, Cursor, and others. The same file works across tools if platform-specific metadata is avoided.
- > "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — [thenewstack.io](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

### Pattern 2: Binance as a High-Profile Adopter Driving Legitimacy
- **Platforms**: X (@BinanceAcademy) + Web (binance.com, fxnewsgroup.com, banklesstimes.com, multiple crypto media outlets)
- Two waves of Binance skills (7 in March, 13 in April) are the most-documented real-world skills rollout, providing a template for enterprise SDK adoption.
- > "13 new AI agent skills just dropped on Binance. If you're building with or using AI agents on Binance, this is a significant expansion." — @BinanceAcademy ([link](https://x.com/BinanceAcademy/status/2043932265403535683))

### Pattern 3: Education Boom — Anthropic Canonicalizing Its Own Standard
- **Platforms**: X (@Radha_AI, @Zingylabs) + Web (anthropic.skilljar.com, deeplearning.ai, termdock.com, udemy.com, aitoolsclub.com)
- Free official courses + DeepLearning.AI partnership + Udemy course all launched within weeks. Signal: Anthropic wants developers trained on its spec before competing standards emerge.
- > "claude code, api, agent skills, MCP, all of it. straight from the team that built it" — @Zingylabs ([link](https://x.com/Zingylabs/status/2043968041906798618))

### Pattern 4: Community Registries Far Outpace Official Ones
- **Platforms**: X (@sarunkumar098) + Web (claudemarketplaces.com, claudepluginhub.com, jeremylongshore GitHub, SkillsMP)
- Official: 101 plugins. Community: 14,083+ indexed plugins, 340 plugins + 1,367 skills in a single repo, 800,000+ skills on SkillsMP. Security implications emerge at this scale.
- > "Discovered a community registry with: 11K+ plugins, 63K+ agent skills. Super useful for backend, DevOps, and AI workflows" — @sarunkumar098 ([link](https://x.com/sarunkumar098/status/2043951290406043749))

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @DSCVR1 | "DSCVR AI reads sentiment, tracks smart money… Agent Skills subscription is live. Pro or Elite — pay on-chain." | 12 | 2 | [link](https://x.com/DSCVR1/status/2043940770529612269) |
| @BinanceAcademy | "13 new AI agent skills just dropped on Binance… significant expansion." | 23 | 3 | [link](https://x.com/BinanceAcademy/status/2043932265403535683) |
| @k_dense_ai | "Updated skill for Parallel Web Systems… Scientific Agent Skills ecosystem… search, deep search, webpage extraction and data enrichment." | 19 | 2 | [link](https://x.com/k_dense_ai/status/2043880880863908267) |
| @Radha_AI | "Anthropic just dropped 13 AI courses… for FREE… 3 - Introduction to Agent Skills." | 5 | 3 | [link](https://x.com/Radha_AI/status/2043947698991350071) |
| @Zingylabs | "skip the $99 twitter guru courses. @AnthropicAI has dropped 13 free courses… claude code, api, agent skills, MCP, all of it." | 4 | 2 | [link](https://x.com/Zingylabs/status/2043968041906798618) |
| @DSCVR1 | "You: refreshing Polymarket every 30 seconds. Your DSCVR-powered agent: Already Knew. Already acted. Agent Skills, coming soon." | 36 | 6 | [link](https://x.com/DSCVR1/status/2042272640673730617) |
| @ScepterAgent | "$SIZE… Built on the official Agent Skills SDK released today, it's a meta-play on the ecosystem itself." | 4 | 2 | [link](https://x.com/ScepterAgent/status/2043951423553987011) |
| @sarunkumar098 | "Leveled up my Claude Code workflow… community registry with: 11K+ plugins, 63K+ agent skills." | 4 | 0 | [link](https://x.com/sarunkumar098/status/2043951290406043749) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| The New Stack | [thenewstack.io](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Frames Anthropic's Agent Skills spec as a standards play alongside MCP |
| Anthropic Skilljar | [anthropic.skilljar.com](https://anthropic.skilljar.com/) | Official Academy platform hosting all 13 free courses |
| Claude Code Docs | [code.claude.com/docs/en/features-overview](https://code.claude.com/docs/en/features-overview) | Official extension taxonomy: Skills, MCP, Plugins, Subagents, Agent Teams |
| Claude Code Docs | [code.claude.com/docs/en/plugin-marketplaces](https://code.claude.com/docs/en/plugin-marketplaces) | Official guide to creating/distributing plugin marketplaces |
| MorphLLM | [morphllm.com/claude-code-extensions](https://www.morphllm.com/claude-code-extensions) | 2026 guide to all Claude Code extension types |
| MorphLLM | [morphllm.com/claude-code-skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills vs. MCP vs. Plugins comparison guide |
| DEV Community | [dev.to/williamwangai](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | Practical install guide: Skills vs MCP; best picks in 2026 |
| Medium (Muneeb Ahmad) | [muneebsa.medium.com](https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff) | Comprehensive extension taxonomy explanation |
| ClaudeFa.st | [claudefa.st/blog/tools/mcp-extensions/best-addons](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | Curated list: 50+ best MCP servers for Claude Code 2026 |
| ClaudeMarketplaces | [claudemarketplaces.com](https://claudemarketplaces.com/) | Aggregator of 2,865+ Claude Code plugin marketplaces |
| TurboDocx | [turbodocx.com/blog](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best Claude Code skills/plugins/MCP servers curated list |
| PopularAITools | [popularaitools.ai/blog](https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026) | 2026 Claude Code skills, plugins and CLIs overview |
| GitHub (jeremylongshore) | [github.com/jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 340 plugins + 1367 skills; CCPI package manager |
| GitHub (jeremylongshore README) | [github.com/…/README.md](https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md) | Full docs for community marketplace |
| GitHub (Anthropic official) | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Official Anthropic-managed plugin directory |
| GitHub (marketplace.json) | [anthropics/claude-code marketplace.json](https://github.com/anthropics/claude-code/blob/main/.claude-plugin/marketplace.json) | Built-in marketplace registry file |
| PromptArmor | [promptarmor.com](https://www.promptarmor.com/resources/hijacking-claude-code-via-injected-marketplace-plugins) | Security: Plugin injection attack vector documentation |
| LiteLLM | [docs.litellm.ai](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) | Managed Claude Code plugin marketplace tutorial |
| ClaudePluginHub | [claudepluginhub.com](https://www.claudepluginhub.com/plugins/jeremylongshore-flyio-pack-plugins-saas-packs-flyio-pack) | Community indexer: 14,083+ plugins |
| Build To Launch | [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review) | Tested 10 plugins, recommends 4 worth keeping |
| Binance Official | [binance.com/…/detail/bafb9dda…](https://www.binance.com/en/support/announcement/detail/bafb9dda6cbb47d5882a4090c31d4c64) | Official announcement: 13 new AI Agent Skills (April 2026) |
| Binance Academy | [binance.com/en/academy/…](https://www.binance.com/en/academy/articles/binance-ai-agent-skills-alpha-derivatives-margin-and-assets) | Alpha, derivatives, margin, assets skills detail |
| Binance (Square AI skill) | [binance.com/…/detail/7ba0c987…](https://www.binance.com/en/support/announcement/detail/7ba0c9871b17429ba8af46f0c6ec187c) | Content creation AI agent skill for Binance Square |
| GitHub (Binance) | [github.com/binance/binance-skills-hub](https://github.com/binance/binance-skills-hub) | Open skills marketplace for AI agents — crypto access |
| FX News Group | [fxnewsgroup.com](https://fxnewsgroup.com/forex-news/cryptocurrency/binance-launches-13-new-ai-agent-skills/) | News coverage: Binance launches 13 new AI agent skills |
| BanklessTimes | [banklesstimes.com](https://www.banklesstimes.com/articles/2026/04/02/binance-expands-ai-ecosystem-with-13-new-new-agent-skills/) | Binance ecosystem expansion coverage |
| Business Upturn | [businessupturn.com](https://www.businessupturn.com/brand-post/binance-enhances-ai-agent-skills-with-comprehensive-trading-asset-management-and-market-intelligence-capabilities/) | Full capabilities breakdown: trading, asset management, market intelligence |
| MEXC News | [mexc.co/news/844826](https://www.mexc.co/news/844826) | Coverage of initial 7-skill Binance launch |
| CryptoBreaking | [cryptobreaking.com](https://www.cryptobreaking.com/binance-beta-launches-ai-pro/) | Binance Ai Pro beta — agentic trading product |
| Medium (@gemQueenx) | [medium.com/@gemQueenx](https://medium.com/@gemQueenx/binance-launches-7-ai-agent-skills-enabling-trading-wallet-access-and-real-time-market-data-via-dace4bcfe4fd) | First-wave 7 skills detailed coverage |
| Stacklok/ToolHive Docs | [docs.stacklok.com/toolhive/updates/2026/04/06](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) | April 6, 2026: ToolHive adds agent skills to CLI + registry |
| ClawHub | [clawhub.ai](https://clawhub.ai/) | Primary ClawHub registry site |
| ClawHub (alt) | [clawhub.biz](https://clawhub.biz/) | ClawHub: 3,286 AI agent skills listed |
| GitHub (openclaw/clawhub) | [github.com/openclaw/clawhub](https://github.com/openclaw/clawhub) | Skill directory open source repo for OpenClaw |
| OpenClaw Docs | [docs.openclaw.ai/tools/clawhub](https://docs.openclaw.ai/tools/clawhub) | Official ClawHub documentation |
| Skywork.ai (ClawHub overview) | [skywork.ai/…/clawhub-ai-skills-registry/…](https://skywork.ai/skypage/en/clawhub-ai-skills-registry/2038574818194624512) | Ultimate guide to ClawHub AI skills registry |
| Skywork.ai (OpenClaw registry) | [skywork.ai/…/clawhub-openclaw-skill-registry/…](https://skywork.ai/skypage/en/clawhub-openclaw-skill-registry/2038573559848898560) | OpenClaw skill registry guide 2026 |
| Blink Blog | [blink.new/blog/…safe-install-guide](https://blink.new/blog/openclaw-clawhub-skills-safe-install-guide-2026) | Security guide post-March 2026 ClawHub crisis |
| Medium (Mehul Gupta) | [medium.com/data-science-in-your-pocket](https://medium.com/data-science-in-your-pocket/what-is-openclaw-clawhub-e123c2dd0db1) | "What is OpenClaw ClawHub?" explainer |
| AIToolsSpace | [aitoolsspace.com/en/tools/clawhub](https://www.aitoolsspace.com/en/tools/clawhub) | ClawHub tool listing |
| Fungies.io | [fungies.io/ai-agent-skills-skill-md-guide-2026](https://fungies.io/ai-agent-skills-skill-md-guide-2026/) | Complete SKILL.md developer guide 2026 |
| KDnuggets | [kdnuggets.com/top-5-agent-skill-marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 agent skill marketplaces comparison |
| SkillsMP | [skillsmp.com](https://skillsmp.com) | 800,000+ agent skills marketplace |
| Calmops | [calmops.com/ai/ai-agent-skills-complete-guide-2026](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) | AI agent skills complete guide 2026 |
| GitHub (awslabs) | [github.com/awslabs/agent-plugins](https://github.com/awslabs/agent-plugins) | AWS agent plugins for AI coding agents |
| Spring.io | [spring.io/blog/2026/01/13/spring-ai-generic-agent-skills](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/) | Spring AI Agentic Patterns Part 1: Agent Skills (Jan 2026) |
| OpenAI Codex | [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills) | OpenAI adoption of SKILL.md format for Codex |
| Chris Ayers Blog | [chris-ayers.com/posts/agent-skills-plugins-marketplace](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Agent Skills, Plugins, and Marketplace complete guide |
| ExplainX.ai | [explainx.ai/blog/what-are-agent-skills-complete-guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | What are agent skills? Complete guide for Claude Code, Cursor & MCP |
| Termdock | [termdock.com/en/blog/anthropic-academy-claude-courses-guide](https://www.termdock.com/en/blog/anthropic-academy-claude-courses-guide) | Anthropic Academy: all 13 courses guide |
| Pasquale Pillitteri | [pasqualepillitteri.it/en/news/371](https://pasqualepillitteri.it/en/news/371/anthropic-academy-free-courses-claude) | Anthropic Academy 13 free courses announcement |
| AIToolsClub | [aitoolsclub.com](https://aitoolsclub.com/10-free-anthropic-academy-ai-courses-to-master-claude-claude-code-and-mcp/) | 10+ Free Anthropic Academy courses guide |
| DeepLearning.AI | [deeplearning.ai/short-courses/agent-skills-with-anthropic](https://www.deeplearning.ai/short-courses/agent-skills-with-anthropic/) | Official DeepLearning.AI + Anthropic agent skills short course |
| Udemy | [udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice](https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/) | Paid course: Agent Skills — Claude Code, Cursor and MCP |
| Anthropic Certifications | [anthropiccertifications.com/courses](https://www.anthropiccertifications.com/courses) | Claude SA Certification: Claude Code, Agent SDK, MCP & API |
| Fabian Miranda Blog | [fabianmiranda.com/blog/2026-03-15](https://fabianmiranda.com/blog/2026-03-15-anthropic-academy-free-ai-training) | Review: Anthropic Academy free AI training |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ 0 upvotes │ 0 comments
├─ 🔵 X: 16 posts │ 144 likes │ 25 reposts
├─ 🔴 YouTube: 0 videos │ 0 views
├─ 🟢 HN: 0 stories │ 0 points │ 0 comments
├─ 🟣 TikTok: 0 videos │ 0 views
├─ 🩷 Instagram: 0 reels │ 0 views
├─ 🦋 Bluesky: 0 posts │ 0 likes
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 65 pages (7 via skill + 58 via WebSearch)
└─ 🗣️ Top voices: @DSCVR1, @BinanceAcademy, @k_dense_ai, @sarunkumar098 │ github.com, binance.com, clawhub.ai
```

---

## Data Gaps

- **Reddit**: Completely unavailable (HTTP 402 Payment Required on ScrapeCreators, 403 on public API). No Reddit coverage for this topic — likely relevant discussions in r/ClaudeAI, r/MachineLearning, r/LocalLLaMA are missed.
- **YouTube**: Zero results. Searches timed out via both direct API and ScrapeCreators (HTTP 402). Likely tutorials and walkthroughs exist but are unindexed here.
- **Hacker News**: Zero results. High probability of relevant Show HN posts or Ask HN threads about the agent skills spec, ClawHub, or Binance skills that are not captured.
- **Bluesky, TikTok, Instagram**: No results; platforms may have coverage but aren't indexed for this topic.
- **Skill web results (7 items)**: The skill output reported 7 web items from domains github.com, learn.microsoft.com, courses.taltech.akaver.com, developers.googleblog.com — but specific URLs were not surfaced in the cluster output. These may overlap with WebSearch results.
- **8 undisclosed X posts**: The skill collected 16 X posts total but only 8 appeared in ranked clusters. Lower-scoring posts are not itemized in the output.
- **"Agent Skills" naming collision**: The search term retrieves both (a) the Anthropic/developer ecosystem meaning and (b) Web3/DeFi "agent skills" products (DSCVR, Scepter). Cross-contamination present throughout.
- **Coverage estimate**: Strong on Claude Code ecosystem, Binance, and education (Anthropic Academy). Weak on open-source community sentiment (no Reddit/HN), video content, and non-English sources. Estimated coverage: ~55% of total available signal.

---

## Key Quotes

> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — [thenewstack.io](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

> "You: refreshing Polymarket every 30 seconds. Your DSCVR-powered agent: Already Knew. Already acted. Agent Skills, coming soon." — @DSCVR1 on X ([link](https://x.com/DSCVR1/status/2042272640673730617))

> "13 new AI agent skills just dropped on Binance. If you're building with or using AI agents on Binance, this is a significant expansion." — @BinanceAcademy on X ([link](https://x.com/BinanceAcademy/status/2043932265403535683))

> "skip the $99 twitter guru courses. @AnthropicAI has dropped 13 free courses with official certificates. claude code, api, agent skills, MCP, all of it. straight from the team that built it." — @Zingylabs on X ([link](https://x.com/Zingylabs/status/2043968041906798618))

> "Leveled up my Claude Code workflow with a powerful plugins + agents ecosystem. Discovered a community registry with: 11K+ plugins, 63K+ agent skills. Super useful for backend, DevOps, and AI workflows." — @sarunkumar098 on X ([link](https://x.com/sarunkumar098/status/2043951290406043749))

> "MCP servers give agents the raw tools they can call; skills give them the knowledge of when, why, and how to use those tools effectively." — [docs.stacklok.com/toolhive](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates)

> "Skills are a markdown file… Claude can load them automatically when relevant. Skills teach Claude how to perform tasks through instructions and scripts, using only 30–50 tokens per skill until needed." — [code.claude.com docs](https://code.claude.com/docs/en/features-overview)

> "We just released an updated skill for Parallel Web Systems as part of our Scientific Agent Skills ecosystem. Now your agent scientist can use the Parallel CLI to perform search, deep search, webpage extraction and data enrichment." — @k_dense_ai on X ([link](https://x.com/k_dense_ai/status/2043880880863908267))

> "Built on the official Agent Skills SDK released today, it's a meta-play on the ecosystem itself, turning platform mechanics into a self-reinforcing loop." — @ScepterAgent on X ([link](https://x.com/ScepterAgent/status/2043951423553987011))

> "Claude Code shares the same skill file format, allowing for cross-compatibility via the Model Context Protocol (MCP)." — [fungies.io](https://fungies.io/ai-agent-skills-skill-md-guide-2026/)
