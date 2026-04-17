# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-04-17
**Query type:** GENERAL
**Sources:** Hacker News, Web, YouTube, GitHub, Reddit (blocked), Polymarket-adjacent

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 threads | multiple points/comments per thread | Skills-vs-MCP debate, Show HN submissions |
| Web | 80+ pages | — | Official docs, blogs, news, security research |
| YouTube | ~25+ videos | 4K–853K views per video | Tutorial content, ranked 2026 guides |
| GitHub | 15 repos | varies | Official + community repos |
| Reddit | — | — | Blocked by Anthropic crawler |
| X/Twitter | — | — | Excluded per instructions |
| TikTok | — | — | Skills for TikTok exist; no direct TikTok data |
| Bluesky | — | — | No direct data retrieved |
| Polymarket | 1 official repo | — | Official Polymarket agent-skills repo |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: Anthropic's Bid to Own the AI Extension Layer

On December 18, 2025, Anthropic published ["Equipping agents for the real world with Agent Skills"](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) and simultaneously launched Agent Skills as an independent open standard. The specification and reference SDK landed at agentskills.io, and the company opened a public [anthropics/skills](https://github.com/anthropics/skills) repo.

The core format is deceptively simple: a folder containing a `SKILL.md` file with YAML frontmatter (`name`, `description`, and trigger conditions) plus markdown instructions. Building a skill is described as "putting together an onboarding guide for a new hire." The key design choice was portability — the same file runs across Claude Code, Cursor, Gemini CLI, Codex CLI, and Antigravity IDE without modification.

OpenAI adopted the same SKILL.md format for Codex CLI and ChatGPT within weeks of launch. Other adopters at launch included Microsoft, Atlassian, Figma, Canva, Stripe, Notion, Zapier, and Cursor. [VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) framed it as "a strategic bet that sharing its approach... will cement the company's position in the fast-evolving enterprise software market." [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) called it "Anthropic's Next Bid to Define AI Standards."

**Enterprise use cases in production:** coding workflows, legal research, finance, accounting, data science. Claude Managed Agents also launched as an enterprise one-stop shop, though [VentureBeat flagged vendor lock-in risk](https://venturebeat.com/orchestration/anthropics-claude-managed-agents-gives-enterprises-a-new-one-stop-shop-but).

*Discussed on: Web (VentureBeat, The New Stack, TechRadar, SiliconAngle, AI Business, WebProNews), HN (#45607117, #45619537, #45610869)*

---

### 2. The Three-Layer Extension Model: Skills vs. MCP vs. Plugins

Community consensus (across [Morph](https://www.morphllm.com/claude-code-skills-mcp-plugins), [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/), [awesomeskill.ai](https://awesomeskill.ai/blog/skills-vs-mcp-vs-plugins-vs-subagents), [MindStudio](https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference), [morphllm.com extensions guide](https://www.morphllm.com/claude-code-extensions)) has settled on three distinct layers:

**Skills** — Markdown files in `~/.claude/skills/` that teach Claude procedural knowledge. Each skill uses only 30–50 tokens until invoked. Think of them as macros: write a `SKILL.md` once, call `/review-component` forever. As of 2026, slash commands and skills are unified under `.claude/skills/`.

**MCP Servers** — Protocol-based executables exposing external tools via the Model Context Protocol. A typical five-server setup with 58 tools burns ~55,000 tokens before a single word of work. GitHub's official MCP alone uses tens of thousands of tokens. MCP is the right layer for external connectivity (databases, APIs, GitHub, Figma).

**Plugins** — Packaging containers that bundle Skills, slash commands, agents, hooks, and MCP servers into a single installable unit. Plugins are the distribution layer.

Additionally: **Subagents** (isolated context windows for parallel work), **Hooks** (12 lifecycle events, deterministic execution), and **CLAUDE.md** (persistent project context, best kept under 200 lines).

**Agent Teams** launched February 5, 2026 alongside Opus 4.6: multiple independent Claude sessions that coordinate, message each other, and divide work in parallel — described as a "collaborative squad" vs. the single-boss-multiple-workers subagent model.

The practitioner recommendation across sources: "Most developers need 2–3 MCP servers (GitHub, Filesystem, one domain-specific) plus a few custom Skills for their workflow."

*Discussed on: Web (Morph, alexop.dev, morphllm.com, DEV.to, Medium, Substack), HN (#46396930)*

---

### 3. MCP Tool Search: Solving the Context Window Crisis

The biggest practical problem with MCP adoption was context poisoning. With 7+ MCP servers configured, users were losing 50–70% of their 200K context window before writing a single prompt. Anthropic's engineering team published benchmarks: 50+ MCP tools consumed ~77,000 tokens before any work began.

Anthropic's solution — **MCP Tool Search** (lazy loading) — was documented by [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search), [Medium](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc), [Atcyrus](https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide), and [Tessl.io](https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/). Instead of loading all tool definitions at session start, Claude Code loads a lightweight search index and fetches 3–5 relevant tools (~3K tokens) on-demand per query. Result: ~8,700 tokens used instead of ~77,000 — a 95% reduction.

MCP Tool Search is now **auto-enabled** for all users when MCP tools would consume more than 10% of context. No configuration needed. OpenAI's Codex team independently filed [GitHub issue #9266](https://github.com/openai/codex/issues/9266) requesting the same feature, and the community built [lazy-mcp](https://github.com/voicetreelab/lazy-mcp) as a proxy workaround. Original feature requests: [Claude Code issue #11364](https://github.com/anthropics/claude-code/issues/11364) and [issue #20421](https://github.com/anthropics/claude-code/issues/20421).

*Discussed on: Web (claudefa.st, Medium, Tessl.io, atcyrus.com), GitHub*

---

### 4. Marketplace Explosion: Scale and Fragmentation

The marketplace ecosystem scaled dramatically in early 2026:

| Marketplace | Scale | Notes |
|---|---|---|
| [mcp.so](https://mcp.so/) | 20,112 MCP servers | Largest single directory |
| [SkillsMP](https://skillsmp.com) | 66,500+–425,000+ skills | Cross-platform; NOT Anthropic-affiliated |
| [LobeHub](https://lobehub.com/skills) | 169,739 skills | Fastest-growing; polished UX |
| [MCP Market](https://mcpmarket.com/) | 318 Claude-specific MCPs | Figma, Databricks, Storybook, Ghidra |
| [claudemarketplaces.com](https://claudemarketplaces.com/) | "thousands of developers" | Sorted by installs + GitHub stars |
| [agentskills.io](https://agentskills.so/) | Open spec + validation | Canonical SKILL.md format enforcer |
| [claude-plugins.dev](https://claude-plugins.dev/) | Community registry | With CLI for discovery/install |

[KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) covered the top 5 marketplaces. [Hermesagents.net](https://hermesagents.net/blog/skills-and-agentskills-io/) chronicled how one ecosystem (Hermes) grew in four weeks. [agentpmt.com](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days) documented six agent marketplaces shipping in 28 days (February 2026): Anthropic, OpenAI, Perplexity, Superhuman, Google Cloud, Oracle.

The MCP server count grew from ~1,000 in early 2025 to 10,000+ active servers in 2026. The [antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) repo aggregates 1,400+ agentic skills installable across Claude Code, Cursor, Codex CLI, Gemini CLI, and Antigravity IDE.

*Discussed on: Web (KDnuggets, Hermesagents, agentpmt.com, paperclipped.de, chris-ayers.com), HN (#46721900, #46693426)*

---

### 5. Popular Plugins and Skills Leaderboard

The [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) repo (340 plugins + 1,367 skills) with CCPI package manager is the most comprehensive open-source collection. Install via:

```bash
pnpm add -g @intentsolutionsio/ccpi
ccpi install devops-automation-pack
ccpi validate ./your-plugin
```

Notable entries from [brightcoding.dev](https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development), [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins), [self.md](https://self.md/guides/best-claude-code-plugins/), and [composio.dev](https://composio.dev/content/top-claude-code-plugins):

- **Morph MCP** ([@morphllm/morphmcp](https://www.morphllm.com/mcp)) — [YC-backed](https://www.ycombinator.com/companies/morph). FastApply: 35% faster edits at 10,500 tok/sec. WarpGrep: 5x faster code search, 40% fewer tokens per search. Most-installed Claude Code extension per multiple sources.
- **/feature-dev skill** — 89,000+ installs. Most popular Claude Code plugin. Turns a feature brief into working code.
- **Context7** — Solves "deprecated methods" problem by fetching live API docs.
- **Context Hub** (Andrew Ng's team, open source) — Curated, versioned API specifications.
- **Claude-Mem** — Adds long-term memory across sessions.
- **connect-apps** — Connects Claude to Gmail, Slack, GitHub, Notion, and 500+ services.
- **Superpowers** — Structured lifecycle planning + skills framework.
- **Mother MCP** ([HN #46692102](https://news.ycombinator.com/item?id=46692102)) — Auto-detects tech stack, installs relevant skills.
- **Roundtable MCP** ([HN #45374908](https://news.ycombinator.com/item?id=45374908)) — Orchestrates Claude Code, Cursor, Gemini, and Codex in parallel.

Additional package managers: [CCPM](https://ccpm.dev/) (Claude Code Plugin Manager) and [Kamalnrf/claude-plugins](https://github.com/Kamalnrf/claude-plugins) lightweight registry.

*Discussed on: Web, HN (#46396930, #46692102, #46693426, #45374908)*

---

### 6. HN Debate: "Skills Are Bigger Than MCP"

Hacker News has been the primary battleground for skills-vs-MCP philosophy. Thread [#45619537](https://news.ycombinator.com/item?id=45619537) ("Claude Skills are awesome, maybe a bigger deal than MCP") generated significant debate. The [follow-up thread #45610869](https://news.ycombinator.com/item?id=45610869) continued the argument. Skills advocates point to:

1. **Context efficiency**: Skills use 30–50 tokens each; MCP servers can use 50,000+ tokens for their tool definitions.
2. **Portability**: Skills are plain markdown; MCP requires an executable runtime.
3. **Learnability**: Skills need no code — just documentation-style writing.
4. **Cross-platform**: The same SKILL.md works across Claude Code, Cursor, Codex, Gemini CLI.

Thread [#46531794](https://news.ycombinator.com/item?id=46531794) ("Claude Code Emergent Behavior: When Skills Combine") explored how combining multiple skills produces unexpected capabilities — users discovering that loading a `testing` skill + `code-review` skill together produces automated TDD loops neither skill was designed for.

Thread [#47766370](https://news.ycombinator.com/item?id=47766370) showed LangAlpha, a Claude Code fork targeting Wall Street workflows, demonstrating skills being adapted for financial analysis, compliance checking, and trade analysis — enterprise domain specialization via skills.

*Discussed on: HN (#45619537, #45610869, #46531794, #46396930, #47766370)*

---

### 7. Security Crisis: Malicious Skills in the Wild

The rapid ecosystem growth created a supply chain security emergency documented by multiple research teams:

**The threat landscape:**
- [Snyk's ToxicSkills study](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) (ClawHub marketplace): 36% prompt injection rate in analyzed skills; 1,467 malicious payloads; 76 specifically for credential theft, backdoor installation, and data exfiltration. 8 malicious skills remained publicly available at publication.
- [PromptArmor](https://www.promptarmor.com/resources/hijacking-claude-code-via-injected-marketplace-plugins): "Hijacking Claude Code via Injected Marketplace Plugins" — hooks that trigger on prompt submission to rewrite permissions files.
- [SentinelOne](https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/): Dependency hijacking — malicious skills redirect `httpx` and other common package installs to attacker-controlled sources.
- [Lasso Security](https://www.lasso.security/blog/the-hidden-backdoor-in-claude-coding-assistant): Hidden backdoors via indirect prompt injection.
- [Cymulate](https://cymulate.com/blog/cve-2025-547954-54795-claude-inverseprompt/): CVE-2025-54794 & CVE-2025-54795 — InversePrompt technique turning Claude against itself.
- [TechRadar](https://www.techradar.com/pro/that-felt-wrong-dev-uses-claude-to-expose-why-a-popular-no-code-platform-wants-to-read-all-your-prompts): Popular no-code platform plugin triggering consent prompts and collecting data in unrelated projects.

**Root cause:** ClawHub's barrier to publishing is a SKILL.md file and a GitHub account that's one week old — no code signing, security review, or sandboxing. February 2026 saw the first coordinated malware campaign: 30+ malicious skills distributed via ClawHub.

**Enterprise response:** [TrueFoundry](https://www.truefoundry.com/blog/claude-code-prompt-injection) published enterprise guidance. [Prompt Security](https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code/) documented the dependency hijack vector. Official guardrails: [Claude API docs](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/mitigate-jailbreaks).

*Discussed on: Web (Snyk, SentinelOne, PromptArmor, Lasso, TechRadar, Cymulate)*

---

### 8. YouTube and Educational Ecosystem

Claude Code skills/plugins have generated substantial YouTube content. [A Medium roundup](https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840) ranked 25 videos from viral demos (853K views) to deep dives (4K views). [claudecodeguides.com](https://claudecodeguides.com/best-claude-code-youtube-channels-to-follow/) and [developereducators.com](https://developereducators.com/best/claude-code/) aggregate 1,038+ ranked tutorial videos.

Anthropic's official learning path: [Claude Code in Action](https://anthropic.skilljar.com/claude-code-in-action) — free course on Anthropic's SkillJar platform. For community resources: [youngurbanproject.com](https://www.youngurbanproject.com/learn-claude-ai-free-youtube-videos/) lists 20 free YouTube videos from beginner to advanced.

Notable YouTube-integrated skills:
- **Watch YouTube skill** ([mcpmarket.com](https://mcpmarket.com/tools/skills/watch-youtube)): Extracts transcripts, distills videos into summaries and code snippets
- **YouTube to Markdown skill** ([mcpmarket.com](https://mcpmarket.com/tools/skills/youtube-to-markdown)): Transforms videos into searchable documentation using Whisper AI
- **YouTube Transcript MCP** ([github.com/hancengiz](https://github.com/hancengiz/youtube-transcript-mcp/blob/main/CLAUDE_CODE_AGENT_GUIDE.md)): Full MCP integration for transcript extraction

*Discussed on: Web (Medium, claudecodeguides.com, developereducators.com, scrimba.com)*

---

### 9. Domain-Specific Skills: Finance, Social Media, Prediction Markets

**Prediction markets:** Polymarket published an official [agent-skills repo](https://github.com/Polymarket/agent-skills) and [agents repo](https://github.com/Polymarket/agents). Community skills include polymarket-scanner, polymarket-analyzer, and polymarket-paper-trader — all paper-trading-first, working with Claude Code, OpenClaw, NanoClaw, Codex, and Cursor. The [mjunaidca/polymarket-skills](https://github.com/mjunaidca/polymarket-skills) repo offers composable, security-audited trading skills. See also: [agentskills.so/polymarket](https://agentskills.so/skills/axwelbrand-byte-arbibot-polymarket-prediction-market) and [aiskill.market/polymarket](https://aiskill.market/skills/polymarket).

**Social media / content creation:** MindStudio documented [content repurposing skills](https://www.mindstudio.ai/blog/claude-code-skills-social-media-content-repurposing). Composio provides [TikTok MCP integration](https://composio.dev/toolkits/tiktok/framework/claude-code). Stormy.ai documented an [autonomous Instagram content engine](https://stormy.ai/blog/autonomous-instagram-content-engine-claude-code-playbook) and the [2026 Skill Economy](https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills). A 17-skill social media manager handles 21 posts across 3 platforms ([wealthytent.com](https://wealthytent.com/claude-code-8)).

**Finance (Wall Street):** LangAlpha ([HN #47766370](https://news.ycombinator.com/item?id=47766370)) demonstrates Claude Code adapted for financial workflows.

*Discussed on: Web, GitHub, HN (#47766370)*

---

### 10. The Skill Economy: Creating and Selling Skills

[Stormy.ai's 2026 Skill Economy post](https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills) documents an emerging market for selling skills. [SmartScope's SkillsMP review](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) covers how to navigate 66,500+ skills. [Anthropic's Skill-Creator](https://medium.com/ai-software-engineer/anthropic-new-skill-creator-measures-if-your-agent-skills-work-no-more-guesswork-840a108e505f) now measures whether skills actually work — removing guesswork from skill validation. The [Complete Guide to Building Skills for Claude](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf) is Anthropic's official PDF resource.

The [agentskills.io spec](https://lobehub.com/skills/openclaw-skills-agentskills-io) enforces canonical layout (SKILL.md, scripts/, references/, assets/), strict frontmatter rules, and token/line limits to enable progressive disclosure and cross-platform portability. The [LobeHub "Convert Prompt to Skill"](https://lobehub.com/skills/plagueho-skills-convert-prompt-to-skill) skill automates turning existing prompts into standards-compliant SKILL.md files.

---

## Cross-Source Patterns

**Pattern 1: Portability is the killer feature — SKILL.md's cross-platform adoption**
- Platforms: Web (VentureBeat, The New Stack, TechRadar, SiliconAngle), HN (#45619537)
- Same SKILL.md file runs on Claude Code, Cursor, Codex, Gemini CLI, Antigravity
- Key quote (from web): "The SKILL.md format has become what package.json is to Node.js: a universal declaration file that any compatible agent can read and act on."

**Pattern 2: Context window as the central constraint driving all design decisions**
- Platforms: Web (claudefa.st, Medium, Morph, Tessl.io), GitHub (issues #11364, #20421), HN (#46396930)
- Skills (30–50 tokens) vs. MCP (50,000+ tokens) trade-off is cited in nearly every comparison guide
- Key quote (Morph blog): "Long Claude Code sessions degrade because of context rot — by 30 minutes in, Claude is reasoning over irrelevant files from earlier searches."

**Pattern 3: Supply chain security as the dark side of marketplace growth**
- Platforms: Web (Snyk, SentinelOne, PromptArmor, Lasso, TechRadar, Cymulate)
- Appeared within weeks of marketplace proliferation; multiple independent research teams
- Key quote (Snyk): "36% of analyzed skills contained prompt injection payloads"

**Pattern 4: Six-in-28-days marketplace moment — a tipping point**
- Platforms: Web (agentpmt.com, VentureBeat, IT Pro)
- Feb 2026: Anthropic, OpenAI, Perplexity, Superhuman, Google Cloud, Oracle all expanded agent marketplaces simultaneously
- Signals a platform moment similar to the App Store era for mobile

**Pattern 5: HN community debating skills > MCP as the paradigm shift**
- Platforms: HN (#45619537, #45607117, #45610869, #46531794)
- Skills advocates: simpler, more portable, context-efficient, cross-platform
- Key quote (HN #45619537 title): "Claude Skills are awesome, maybe a bigger deal than MCP"

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|---------------|-----|
| (unknown) | "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands..." | — | — | Complexity of Claude Code extension landscape | https://news.ycombinator.com/item?id=46396930 |
| (unknown) | Claude Skills are awesome, maybe a bigger deal than MCP | — | — | Skills vs MCP efficiency debate | https://news.ycombinator.com/item?id=45619537 |
| (unknown) | Show HN: LangAlpha – Claude Code built for Wall Street | — | — | Domain specialization via skills | https://news.ycombinator.com/item?id=47766370 |
| (unknown) | Show HN: Registry for curated, high quality Claude skills and skillsets | — | — | Handwritten skills > auto-generated | https://news.ycombinator.com/item?id=46721900 |
| (unknown) | Claude Skills | — | — | Original Claude Skills announcement discussion | https://news.ycombinator.com/item?id=45607117 |
| (unknown) | Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills | — | — | Curation from 60K+ raw skills | https://news.ycombinator.com/item?id=46693426 |
| (unknown) | Show HN: Mother MCP – Manage your Agent Skills like a boss | — | — | Auto-detect stack, install skills | https://news.ycombinator.com/item?id=46692102 |
| (unknown) | Show HN: Roundtable MCP – Orchestrate Claude Code, Cursor, Gemini, Codex | — | — | Multi-agent orchestration via MCP | https://news.ycombinator.com/item?id=45374908 |
| (unknown) | Claude Skills bigger deal than MCP follow-up | — | — | Skills portability as key differentiator | https://news.ycombinator.com/item?id=45610869 |
| (unknown) | Claude Code Emergent Behavior: When Skills Combine | — | — | Unexpected capabilities from skill combinations | https://news.ycombinator.com/item?id=46531794 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Official Agent Skills launch post (Dec 18, 2025) |
| VentureBeat | https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard | Enterprise launch + open standard analysis |
| The New Stack | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | Standards battle framing |
| SiliconAngle | https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/ | Open standard coverage (Dec 18, 2025) |
| TechRadar | https://www.techradar.com/pro/anthropic-takes-the-fight-to-openai-with-enterprise-ai-tools-and-theyre-going-open-source-too | OpenAI competitive framing |
| AI Business | https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude | Standard launch coverage |
| Snyk | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | ToxicSkills: 36% prompt injection, 1,467 malicious payloads |
| SentinelOne | https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/ | Dependency hijack attack vector |
| PromptArmor | https://www.promptarmor.com/resources/hijacking-claude-code-via-injected-marketplace-plugins | Plugin hijacking techniques |
| Lasso Security | https://www.lasso.security/blog/the-hidden-backdoor-in-claude-coding-assistant | Hidden backdoor via prompt injection |
| Cymulate | https://cymulate.com/blog/cve-2025-547954-54795-claude-inverseprompt/ | CVE-2025-54794/54795 InversePrompt |
| Prompt Security | https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code | Dependency picking attack |
| TechRadar | https://www.techradar.com/pro/that-felt-wrong-dev-uses-claude-to-expose-why-a-popular-no-code-platform-wants-to-read-all-your-prompts | Plugin data collection scandal |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search | MCP Tool Search 95% context savings |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP Servers 2026 |
| claudefa.st | https://claudefa.st/blog/tools/hooks/hooks-guide | 12 Claude Code lifecycle hooks |
| Morph LLM | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins guide |
| Morph LLM | https://www.morphllm.com/claude-code-extensions | Extensions comprehensive guide |
| Morph LLM | https://www.morphllm.com/mcp | Morph MCP (FastApply + WarpGrep) |
| Morph LLM | https://www.morphllm.com/blog/claude-code-mcp-servers | MCP server guide |
| alexop.dev | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full stack: MCP, Skills, Subagents, Hooks |
| alexop.dev | https://alexop.dev/posts/claude-code-customization-guide-claudemd-skills-subagents/ | Customization guide |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 marketplace comparison |
| agentpmt.com | https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days | Six marketplaces in 28 days (Feb 2026) |
| Hermesagents | https://hermesagents.net/blog/skills-and-agentskills-io/ | Ecosystem growth story in 4 weeks |
| Medium (Caparas) | https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc | MCP lazy loading explainer |
| Medium (Chen) | https://medium.com/@markchen69/claude-code-has-a-skills-marketplace-now-a-beginner-friendly-walkthrough-8adeb67cdc89 | Skills marketplace beginner walkthrough |
| Medium (ranking) | https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840 | 25 YouTube video ranking |
| DEV.to | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP practical guide |
| DEV.to | https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74 | Claude Code #1 on HN recap |
| BrightCoding | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | 270+ tools review |
| Composio | https://composio.dev/content/top-claude-code-plugins | Top Claude Code plugins |
| Composio | https://composio.dev/toolkits/tiktok/framework/claude-code | TikTok MCP with Claude Code |
| Composio | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP with Claude Code |
| Tessl.io | https://tessl.io/blog/anthropic-brings-mcp-tool-search-to-claude-code/ | MCP Tool Search coverage |
| Tessl.io | https://tessl.io/blog/8-trends-shaping-software-engineering-in-2026-according-to-anthropics-agentic-coding-report/ | 8 agentic coding trends |
| Muneeb (Medium) | https://muneebsa.medium.com/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff | Extensions comprehensive explainer |
| aiorg.dev | https://aiorg.dev/blog/claude-code-hooks | Hooks guide (20+ examples) |
| morphllm.com | https://www.morphllm.com/blog/cursor-mcps | FastApply for Cursor |
| Y Combinator | https://www.ycombinator.com/companies/morph | Morph YC listing |
| Product Hunt | https://www.producthunt.com/products/morph-apply-ai-edits-to-files-fast | Morph on Product Hunt |
| atcyrus.com | https://www.atcyrus.com/stories/mcp-tool-search-claude-code-context-pollution-guide | Context pollution guide |
| self.md | https://self.md/guides/best-claude-code-plugins/ | Best plugins 2026 |
| MindStudio | https://www.mindstudio.ai/blog/claude-code-skills-social-media-content-repurposing | Social media repurposing |
| MindStudio | https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference | Skills vs plugins difference |
| Stormy.ai | https://stormy.ai/blog/2026-skill-economy-claude-mcp-marketing-skills | 2026 Skill Economy |
| Stormy.ai | https://stormy.ai/blog/autonomous-instagram-content-engine-claude-code-playbook | Instagram content engine |
| awesomeskill.ai | https://awesomeskill.ai/blog/skills-vs-mcp-vs-plugins-vs-subagents | Complete comparison guide |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Skills, plugins, marketplace complete guide |
| WebProNews | https://www.webpronews.com/anthropic-launches-open-source-ai-agent-framework-to-rival-openai/ | Open source framework framing |
| WebProNews | https://www.webpronews.com/anthropics-agent-skills-gambit-open-standard-challenges-ai-power-players/ | Gambit analysis |
| VentureBeat | https://venturebeat.com/orchestration/anthropics-claude-managed-agents-gives-enterprises-a-new-one-stop-shop-but | Managed Agents lock-in risk |
| IT Pro | https://www.itpro.com/software/development/openais-skills-in-codex-service-aims-to-supercharge-agent-efficiency-for-developers | OpenAI Codex skills response |
| SmartScope | https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ | SkillsMP review |
| Wealthytent | https://wealthytent.com/claude-code-8 | 17-skill social media manager |
| TrueFoundry | https://www.truefoundry.com/blog/claude-code-prompt-injection | Enterprise prompt injection guide |
| Sabrina.dev | https://www.sabrina.dev/p/every-claude-code-concept-explained-beginners | Beginner concepts explainer |
| Medium (Skill-Creator) | https://medium.com/ai-software-engineer/anthropic-new-skill-creator-measures-if-your-agent-skills-work-no-more-guesswork-840a108e505f | Skill-Creator tool coverage |
| GenAI Unplugged | https://genaiunplugged.substack.com/p/claude-code-skills-commands-hooks-agents | Substack: Skills, Commands, Hooks, Agents |
| Toolradar | https://toolradar.com/blog/claude-desktop-mcp-server-setup | MCP setup guide |
| Toolradar | https://toolradar.com/blog/best-mcp-servers-vscode | MCP servers for VS Code |
| Trensee | https://www.trensee.com/en/blog/explainer-claude-code-skills-fork-subagents-2026-03-31 | Skills, Fork, Subagents advanced guide |
| paperclipped.de | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | Plugin ecosystem analysis |
| Anthropic Hub | https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf | Official skill-building guide PDF |
| Anthropic SkillJar | https://anthropic.skilljar.com/claude-code-in-action | Official Claude Code course |
| Mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills/plugins/CLIs |
| popularaitools.ai | https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026 | Skills/plugins/CLIs roundup |
| SkillsLLM | https://skillsllm.com | AI skills marketplace |
| claudeskills.cc | https://claudeskills.cc/tutorials | Claude Skills tutorials |
| Libspace (mirror) | https://www.libspace.io/a/683baa06-7fd1-4e7e-ab2b-604415e673b4/anthropic-launches-enterprise-agent-skills-and-opens-the-standard-challenging | VentureBeat mirror |
| Explainx.ai | https://explainx.ai/skills/robonet-tech/skills/trade-prediction-markets | Trade prediction markets skill |
| Solana Compass | https://solanacompass.com/skills/prediction-markets | Polymarket on Solana |
| AI Skill Market | https://aiskill.market/skills/polymarket | Polymarket on AI Skill Market |
| agentskills.so | https://agentskills.so/skills/axwelbrand-byte-arbibot-polymarket-prediction-market | Polymarket skill |
| EricaAI | https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/ | Building agents for Polymarket |
| Python in Plain English | https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477 | Polymarket app with agentic coding |
| CCPM | https://ccpm.dev/ | Claude Code Plugin Manager |
| NxCode | https://www.nxcode.io/resources/news/install-claude-code-setup-guide-2026 | Install guide 2026 |
| aitooldiscovery | https://www.aitooldiscovery.com/guides/claude-skills | Claude skills guide |
| YoungUrbanProject | https://www.youngurbanproject.com/learn-claude-ai-free-youtube-videos/ | 20 free YouTube learning videos |
| Scrimba | https://scrimba.com/articles/best-claude-code-tutorials-and-courses-in-2026/ | Best tutorials 2026 |
| claudecodeguides.com | https://claudecodeguides.com/best-claude-code-youtube-channels-to-follow/ | Best YouTube channels |
| DeveloperEducators | https://developereducators.com/best/claude-code/ | 1,038+ ranked videos |
| Anthropic Eng | https://www.anthropic.com/engineering/writing-tools-for-agents | Writing tools for agents |
| Articsledge | https://www.articsledge.com/post/skill-engineering | Skill engineering complete guide 2026 |
| Marvin-42 | https://insights.marvin-42.com/articles/anthropic-details-a-multi-agent-harness-for-frontend-design-and-long-running-software-engineering | Multi-agent harness details |
| happysathya.github.io | https://happysathya.github.io/claude-code-extensibility-guide.html | Extensibility guide |
| youngleaders.tech | https://www.youngleaders.tech/p/claude-skills-commands-subagents-plugins | Skills/Commands/Subagents/Plugins guide #95 |
| devops-daily.com | https://devops-daily.com/posts/claude-code-agents-commands-skills-plugins-explained | DevOps Daily explainer |
| openaitoolshub.org | https://www.openaitoolshub.org/en/blog/claude-code-skills-vs-plugins | Skills vs plugins comparison |
| LinkedIn (Foster) | https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we | Survival guide 2026 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Edmund Yong | 800+ hours of Learning Claude Code in 8 minutes | high (viral) | — | — | via medium.com/@rentierdigital roundup |
| Anthropic (SkillJar) | Claude Code in Action | — | — | — | https://anthropic.skilljar.com/claude-code-in-action |
| Various educators | Ranked 25 Claude Code YouTube videos | 4K–853K views range | — | — | https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840 |
| Various | Top channels to follow 2026 | — | — | — | https://claudecodeguides.com/best-claude-code-youtube-channels-to-follow/ |

**GitHub:**
| Repo | Description | Stars | URL |
|------|-------------|-------|-----|
| anthropics/skills | Official Anthropic Agent Skills repository | — | https://github.com/anthropics/skills |
| jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 skills + CCPI | — | https://github.com/jeremylongshore/claude-code-plugins-plus-skills |
| ComposioHQ/awesome-claude-plugins | Curated plugin list | — | https://github.com/ComposioHQ/awesome-claude-plugins |
| quemsah/awesome-claude-plugins | Automated adoption metrics via n8n | — | https://github.com/quemsah/awesome-claude-plugins |
| Kamalnrf/claude-plugins | Lightweight registry + CLI | — | https://github.com/Kamalnrf/claude-plugins |
| sickn33/antigravity-awesome-skills | 1,400+ agentic skills for 5 platforms | — | https://github.com/sickn33/antigravity-awesome-skills |
| morphllm/opencode-morph-plugin | Morph plugin for OpenCode | — | https://github.com/morphllm/opencode-morph-plugin |
| voicetreelab/lazy-mcp | MCP proxy with lazy loading | — | https://github.com/voicetreelab/lazy-mcp |
| Polymarket/agent-skills | Official Polymarket agent skills | — | https://github.com/Polymarket/agent-skills |
| Polymarket/agents | Polymarket autonomous trading agents | — | https://github.com/Polymarket/agents |
| mjunaidca/polymarket-skills | Composable Polymarket skills | — | https://github.com/mjunaidca/polymarket-skills |
| hancengiz/youtube-transcript-mcp | YouTube transcript MCP | — | https://github.com/hancengiz/youtube-transcript-mcp |
| AgriciDaniel/claude-youtube | YouTube creator skill | — | https://github.com/AgriciDaniel/claude-youtube |
| zerowing113/claude-youtube-skill | YouTube to markdown skill | — | https://github.com/zerowing113/claude-youtube-skill |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked by crawler
├─ 🔵 X: — posts │ excluded per instructions
├─ 🔴 YouTube: 25+ videos identified │ 4K–853K views range
├─ 🟢 HN: 10 threads │ points/comments unavailable
├─ 🟣 TikTok: — direct data │ skills for TikTok exist
├─ 🩷 Instagram: — direct data │ skills for Instagram exist
├─ 🦋 Bluesky: — posts │ no data retrieved
├─ 📊 Polymarket: 1 official repo + 4 skill marketplaces | no volume data
├─ 🌐 Web: 80+ pages across 50+ unique domains
└─ 🗣️ Top voices: morphllm.com, alexop.dev, claudefa.st, VentureBeat, Snyk/SentinelOne
```

---

## Data Gaps

- **Reddit:** Fully blocked — Anthropic's web crawler is blocked by reddit.com. Zero Reddit data retrieved. Reddit communities (r/ClaudeAI, r/MachineLearning, r/LocalLLaMA) likely have active discussions not captured here.
- **X/Twitter:** Excluded per instructions. Likely significant discussion volume given the account types active in AI tooling.
- **Bluesky:** No structured data returned. Topic may have Bluesky presence from AI practitioners.
- **TikTok:** No direct TikTok search data; Claude Code skills for TikTok content creation exist but TikTok discussion about Claude Code skills was not directly measurable.
- **Hacker News engagement metrics:** Thread point counts and comment counts were not retrievable via web search — only thread titles and URLs captured.
- **YouTube engagement:** Specific channel names, subscriber counts, and like counts largely unavailable beyond what appeared in roundup articles.
- **SkillsMP count discrepancy:** Sources cite both 66,500+ and 425,000+ skills — unclear if these are different dates or methodologies.
- **Coverage estimate:** Web content ~85% coverage; HN ~70% (titles only, no engagement); YouTube ~40% (no direct video data); Reddit/X/TikTok/Bluesky ~0%.

---

## Key Quotes

> "The SKILL.md format has become what package.json is to Node.js: a universal declaration file that any compatible agent can read and act on." — Web consensus (multiple sources)

> "Claude Skills are awesome, maybe a bigger deal than MCP" — HN thread title ([#45619537](https://news.ycombinator.com/item?id=45619537))

> "Long Claude Code sessions degrade because of context rot — by 30 minutes in, Claude is reasoning over irrelevant files from earlier searches." — Morph LLM ([morphllm.com](https://www.morphllm.com/blog/claude-code-mcp-servers))

> "36% of analyzed skills on ClawHub contained prompt injection payloads; 76 designed specifically for credential theft, backdoor installation, and data exfiltration." — Snyk ToxicSkills study ([snyk.io](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Building a skill for an agent is like putting together an onboarding guide for a new hire." — Anthropic Engineering ([anthropic.com](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

> "Skills are more than a single prompt but less than an entire agent." — HN community framing ([#46693426](https://news.ycombinator.com/item?id=46693426))

> "The best Claude Code users run 2-3 plugins max; each skill adds to the context window baseline — twenty skills fighting for attention is worse than three good ones." — self.md ([self.md/guides/best-claude-code-plugins](https://self.md/guides/best-claude-code-plugins/))

> "With 7+ MCP servers configured, users were losing 50-70% of their 200K context before writing a single prompt." — claudefa.st ([claudefa.st/blog/tools/mcp-extensions/mcp-tool-search](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search))

> "Anthropic released its Agent Skills framework as an open standard — a strategic bet that sharing its approach to making AI assistants more capable will cement the company's position." — VentureBeat ([venturebeat.com](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard))

> "Anthropic, OpenAI, Perplexity, Superhuman, Google Cloud, and Oracle each shipped or expanded an agent marketplace in February 2026 — six ecosystems in 28 days." — agentpmt.com ([agentpmt.com](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days))
