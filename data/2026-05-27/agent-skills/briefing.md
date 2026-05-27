# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-27
**Query type:** GENERAL
**Sources:** Web, Reddit (aggregated), Hacker News, GitHub, YouTube

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | ~1 community summary | 4,200+ weekly contributors to r/ClaudeCode | Aggregated via morphllm.com; no direct thread indexing |
| Hacker News | 1 thread | High engagement (multi-page discussion) | "MCP is a fad" thread — active debate |
| GitHub | 15+ repositories | 18,543 repos indexed (plugin tracker) | MCP servers, skill collections, toolkits |
| Web | 60+ pages | — | Guides, analyses, official docs, blog posts |
| YouTube | 1 video | Not retrievable | "The Ultimate Claude Code Guide \| MCP, Skills & More" |

---

## Synthesized Findings

### 1. The Four-Layer Extension Model for Claude Code

Claude Code in 2026 has four distinct extension primitives, and the community has largely converged on understanding how they differ:

- **Skills** — Procedural knowledge in Markdown, 30–50 tokens each, loaded on-demand. Skills "teach Claude how to do something" — a custom workflow, a project style guide, a domain procedure. They work across Claude.ai, Claude Code, and the API without modification. Up to 100+ skills can be installed without context impact.
- **MCP Servers** — External tool connectivity via Anthropic's open Model Context Protocol. Connect Claude to GitHub, databases, browsers, production infrastructure. High context cost: a five-server setup with 58 tools costs 55,000+ tokens before any conversation begins. Anthropic's Tool Search feature reduces this by ~85% via on-demand discovery.
- **Plugins** — Shareable bundles that package Skills, MCP servers, Hooks, Agents, and LSP servers into a distributable unit installable via a single command. The official catalog lists 40+ plugins.
- **Hooks** — Shell commands that fire automatically at lifecycle events (pre-commit, post-response, etc.). Used for deterministic, non-negotiable actions.

Community consensus: "Use MCP when you need Claude to access external systems. Use Skills when you need Claude to know how to do something. Most workflows benefit from both: MCP for connectivity, Skills for methodology." ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

Practical minimum for most developers: 2–3 MCP servers (GitHub, Filesystem, one domain-specific) plus a handful of custom Skills.

**Sources:** [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins), [code.claude.com/docs/en/mcp](https://code.claude.com/docs/en/mcp), [code.claude.com/docs/en/features-overview](https://code.claude.com/docs/en/features-overview), [morphllm.com/claude-code-extensions](https://www.morphllm.com/claude-code-extensions), [k21academy.com](https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/), [duet.so](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills), [verdent.ai](https://www.verdent.ai/guides/claude-skills-vs-mcp-agents-comparison)

---

### 2. The SKILL.md Open Standard: The "REST of Agents"

The single most significant structural event of the last 30 days in this space is the rapid cross-industry adoption of Anthropic's Agent Skills open standard, published December 18, 2025.

Within **48 hours** of publication, Microsoft integrated it into VS Code and OpenAI added it to ChatGPT and Codex CLI. By March 2026 — 12 weeks later — **32 tools** from competing companies were reading the same SKILL.md files from the same directory structure. Adopters include Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose.

The specification defines:
- File structure: a directory with a `SKILL.md` file
- YAML frontmatter: required `name` and `description` fields
- Instruction format: Markdown below the frontmatter
- Supporting files: `scripts/`, `references/`, `assets/` directories
- Progressive disclosure: metadata loaded first, full instructions on demand

As one analyst put it: *"SKILL.md Is Becoming the REST of Agents. Nobody Told You Yet."* ([Medium/@automation.labs](https://medium.com/@automation.labs/skill-md-is-becoming-the-rest-of-agents-nobody-told-you-yet-f5de9a5859c3))

A skill written for Claude Code can be dropped into Codex's skills directory and it works. Teams can standardize on one skill set regardless of which agent individual developers prefer.

Launch partners included Atlassian, Figma, Canva, Stripe, Notion, and Zapier. Vercel's skills.sh marketplace already lists **89,753 skills**.

Cross-agent skill collections are emerging rapidly: [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) (1,000+), [sickn33/antigravity-awesome-skills](https://github.com/sickn33/antigravity-awesome-skills) (1,400+), [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) (754 skills mapped to MITRE ATT&CK, NIST CSF 2.0, MITRE ATLAS).

**Sources:** [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/), [agensi.io/learn/agent-skills-open-standard](https://www.agensi.io/learn/agent-skills-open-standard), [mintlify.com/blog/skill-md](https://www.mintlify.com/blog/skill-md), [markets.financialcontent.com](https://markets.financialcontent.com/wral/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability), [medium.com/@automation.labs](https://medium.com/@automation.labs/skill-md-is-becoming-the-rest-of-agents-nobody-told-you-yet-f5de9a5859c3), [agentskills.io](https://agentskills.io/home), [f5.com](https://www.f5.com/company/blog/agent-skills-an-emerging-open-standard), [qcode.cc](https://qcode.cc/en/anthropic-agent-skills-standard-guide), [toknow.ai](https://toknow.ai/posts/superpowers-mattpocock-skills-cross-platform-agent-framework/)

---

### 3. Marketplace Explosion — and the Fragmentation Problem

The agent skills marketplace landscape grew from **one registry** in December 2025 to **eight major marketplaces** by Q2 2026. By March 2026, 351,000+ published skills existed across three competing registries.

**Current major players:**

| Marketplace | Skills Count | Revenue Model | Security Scanning |
|---|---|---|---|
| SkillsMP | 800,000+ (scraped, low curation) | None | None |
| Vercel Skills.sh | 89,753 | npm-style, no payments | None |
| LobeHub | 169,000+ (aggregated) | LobeHub ecosystem | None |
| ClaudeSkills.info | 658 (vetted) | Community | None |
| MCP Market | ~500 | Submission-based | None |
| Anthropic Official | ~20 | Manual curation | Internal audit |
| Agensi | 200+ | 80/20 creator revenue split | 8-point automated scan |
| claudemarketplaces.com | 6,700+ skills, 840+ MCP | Free directory | Community votes |

The fragmentation is the primary complaint: *"developers now spend more time comparing marketplaces than they spend finding skills."* ([agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

The **registry consolidation** problem maps tightly to npm's early era. The [Termdock analysis](https://www.termdock.com/blog/cross-agent-skills-new-npm) notes:
- No unified versioning system
- No lock files
- Seven competing directory conventions (`.claude/skills/`, `.agents/skills/`, `.github/skills/`, etc.)
- Community tools (`skillpm`, `skills-npm`) attempting to bridge gaps
- Skills.sh generated 20,000 installs in its first 6 hours — demand is real

**Predicted convergence:** Registry consolidation, standardization on `.agents/skills/`, and tighter npm integration within 12 months.

**MCP-based discovery model** is emerging as an alternative: agents connect once to a marketplace's MCP server and get live catalog access — no downloads, no version management.

**Sources:** [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [termdock.com](https://www.termdock.com/blog/cross-agent-skills-new-npm), [claudemarketplaces.com](https://claudemarketplaces.com/), [claudelog.com](https://claudelog.com/claude-code-mcps/reddit-mcp/), [digitalapplied.com](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution), [rapidclaw.dev](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026)

---

### 4. Security Crisis: The Cost of a Permissionless Ecosystem

The rapid growth has a dark side: **the agent skills ecosystem has a serious, unresolved security problem**.

**Key incidents:**
- **April 16, 2026** — Ox Research disclosed an MCP design flaw (STDIO transport) putting ~200,000 servers at risk of arbitrary OS command execution. Four attack types: unauthenticated command injection, hardening bypass, zero-click prompt injection in AI IDEs, supply chain poisoning via MCP marketplaces. Affected: LangFlow, GPT Researcher, Flowise, Upsonic, Windsurf, Cursor. 150M+ downloads affected. **Anthropic declined to change the protocol architecture**, updating only policy guidance. ([The Register](https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/))

- **February 2026** — Check Point Research disclosed **CVE-2025-59536** (MCP consent bypass) and **CVE-2026-21852** (API key exfiltration) in Claude Code. Attack vectors: malicious `.claude/settings.json` hooks executing shell commands without confirmation; `enableAllProjectMcpServers` bypass enabling auto-MCP init; `ANTHROPIC_BASE_URL` redirect intercepting API keys before trust dialogs. Anthropic patched all three before public disclosure. ([Check Point Research](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/))

- **Skill Audit** — A security scan of 22,511 skills across skills.sh, ClawHub, GitHub, and Tessl found **140,963 issues — averaging 6.3 per skill, with 36% containing prompt injection vulnerabilities.** ([agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

- **March 2026** — Oasis Security's "Claudy Day" attack chained invisible prompt injection with data exfiltration to steal conversation history from a default claude.ai session. ([Oasis Security](https://www.oasis.security/blog/claude-ai-prompt-injection-data-exfiltration-vulnerability))

The HN "MCP is a fad" thread crystallized the security debate: *"easy to create MCP server with data exfil loopholes"* (falloutx) vs. *"teams that already handle HTTP APIs safely can apply the same basics"* (fxj). ([news.ycombinator.com/item?id=46552254](https://news.ycombinator.com/item?id=46552254))

**Sources:** [theregister.com](https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/), [research.checkpoint.com](https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/), [oasis.security](https://www.oasis.security/blog/claude-ai-prompt-injection-data-exfiltration-vulnerability), [ox.security](https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/), [lasso.security](https://www.lasso.security/blog/the-hidden-backdoor-in-claude-coding-assistant), [truefoundry.com](https://www.truefoundry.com/blog/claude-code-prompt-injection), [mintmcp.com](https://www.mintmcp.com/blog/claude-cowork-promt-injection), [github.com/efij/awesome-claude-code-security](https://github.com/efij/awesome-claude-code-security)

---

### 5. Microsoft Doubles Down: Enterprise Skills Infrastructure

Microsoft has built one of the most comprehensive skills ecosystems outside Anthropic itself, with multiple official repositories targeting enterprise and developer audiences:

- **[microsoft/skills](https://github.com/microsoft/skills)** — core repository covering Skills, MCP servers, Custom Agents, Agents.md for SDKs
- **[microsoft/azure-skills](https://github.com/microsoft/azure-skills)** — 200+ structured tools across 40+ Azure services (listing resources, checking prices, querying logs, diagnosing issues)
- **[microsoft/skills-for-fabric](https://github.com/microsoft/skills-for-fabric)** — Microsoft Fabric operation skills
- **[MicrosoftDocs/Agent-Skills](https://github.com/MicrosoftDocs/Agent-Skills)** — Curated agent skills grounded in Microsoft Learn docs
- **[MicrosoftDocs/mcp](https://github.com/MicrosoftDocs/mcp)** — Official Microsoft Learn MCP Server; built into Visual Studio 2026

The .NET Blog published a guide on extending coding agents with .NET Skills. All of these follow the SKILL.md open standard, meaning they work with Claude Code, Codex CLI, Cursor, and 29+ other tools.

The [rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit) collects 135 agents, 35 curated skills, 42 commands, 176+ plugins, 20 hooks, 15 rules, and 14 MCP configs in a single repository.

**Sources:** [microsoft.github.io/skills/](https://microsoft.github.io/skills/), [devblogs.microsoft.com/dotnet](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/), [itecsonline.com](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026), [serenitiesai.com](https://serenitiesai.com/articles/agent-skills-guide-2026)

---

### 6. Real Developer Workflows: What Actually Ships

Two detailed first-person accounts provide ground truth on how practitioners assemble these capabilities:

**Daniil Okhlopkov** ([okhlopkov.com](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/)) — 4 months of daily use:
- Eliminated context-switching across SQL editors, terminals, browsers, documentation
- *"Now I sit in one terminal and describe what I need"*
- MCP stack: Coolify (deployment/self-redeployment), Telegram (messaging), Codex (dual-model verification)
- Custom Skills: `ton-analyst` (200-line blockchain SQL guide), `ton-profiler`, `crosspost` (multi-language publishing)
- Pre-commit hooks blocking `.env`, `.key`, `.pem` files
- 24/7 autonomous server agent on Hetzner VPS
- Philosophy: *"put stable rules in CLAUDE.md, long workflows in skills"*
- Claude Max ($100/month) became essential after hitting Pro limits in two weeks

**Sankalp** ([sankalp.bearblog.dev](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/)) — Claude Code 2.0 guide:
- Uses Claude for execution, GPT-5.2-Codex for verification/review
- Skills: load domain expertise on-demand; avoids bloating system prompts
- Skeptical of MCP as defaults: *"inflate context windows with upfront tool definitions"*
- Hook for notification sounds when Claude finishes — even small customizations matter
- `frontend-design` plugin guides aesthetic decisions, avoids "AI slop"
- Context engineering insight: effective context window is 50–60% of stated capacity

The [CLAUDE.md community consensus](https://www.morphllm.com/claude-code-reddit) (r/ClaudeCode, 4,200+ weekly contributors): keep under 200 lines, use hierarchical files in nested directories, add rules iteratively from recurring mistakes.

---

### 7. Platform Expansion: Agents Moving Into SaaS

The most recent development (May 25, 2026): **Notion opened its workspace to Claude Code, Cursor, and Codex as native AI agents.** ([TechTimes](https://www.techtimes.com/articles/317092/20260525/notion-opens-workspace-claude-code-cursor-codex-native-ai-agents.htm))

This represents a pattern of SaaS platforms adopting MCP as the integration layer for agent access — turning their products into skill-capable environments. Meta's official MCP for Facebook and Instagram ads launched April 29, 2026, and devops-toolkit bundles AWS, GCP, Datadog, and Sentry with slash commands like `/incident`, `/deploy`, `/rollback`.

The [SkillFlow architecture](https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g) demonstrates the business model: aggregate MCP servers into a marketplace, operate the marketplace itself as an MCP server, provide free creator listings with analytics. *"The MCP protocol is becoming the USB-C of AI integrations — a universal standard that lets any AI model connect to any tool."*

**Sources:** [techtimes.com](https://www.techtimes.com/articles/317092/20260525/notion-opens-workspace-claude-code-cursor-codex-native-ai-agents.htm), [dev.to/rafsilva85](https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g), [composio.dev/toolkits/github](https://composio.dev/toolkits/github/framework/claude-code), [github.com/github/github-mcp-server](https://github.com/github/github-mcp-server)

---

## Cross-Source Patterns

**Pattern 1: Context Tax Is the Defining Tradeoff**
- Platforms: Reddit, HN, Web (morphllm, sankalp blog, okhlopkov blog)
- MCP servers extract a severe token toll. 5-server setup: 55,000 tokens; 7-server real-world: 67,000 tokens before typing a word. This cost shapes architecture decisions.
- r/ClaudeCode: *"MCP servers cost 67,000 tokens before writing a single prompt"*
- Sankalp: MCP servers *"inflate context windows with upfront tool definitions"*
- Resolution: Tool Search feature (85% reduction), Skills as a lighter-weight alternative

**Pattern 2: SKILL.md as the New HTTP**
- Platforms: Web (multiple analyses), GitHub (adoption metrics), industry press
- The standard is being compared to REST, USB-C, and npm simultaneously
- Cross-vendor adoption in 12 weeks puts it on pace with rapid developer tooling standardizations
- Risk: fragmented directory conventions still exist (7 competing paths)
- Key quote (Medium): *"SKILL.md Is Becoming the REST of Agents. Nobody Told You Yet."*

**Pattern 3: Security Is Lagging Severely Behind Adoption**
- Platforms: HN, Web (security research blogs, The Register)
- 36% of community skills contain prompt injection vulnerabilities
- MCP design flaw (200K servers at risk) went unpatched at protocol level
- Anthropic's posture: patch exploits in the product, don't change the protocol
- Community response: best-practice guides, hooks for credential protection, security-scanned marketplace (Agensi) gaining traction
- HN: *"easy to create MCP server with data exfil loopholes"* (falloutx)

**Pattern 4: The Pro Plan Rate Limit Wall**
- Platforms: Reddit (dominant complaint), personal blogs
- *"Claude Code is the best coding tool I've ever used, for the 45 minutes a day I can actually use it"*
- Forces skill/MCP efficiency optimization as an economic necessity
- Claude Max ($100/month) becoming the de facto developer tier

---

## Per-Platform Tables

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | #1 directory: 200K monthly visitors, 6,700 skills, 840 MCP servers |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Authoritative Skills vs MCP vs Plugins comparison; token math |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Security audit of 22,511 skills; marketplace comparison |
| termdock.com | https://www.termdock.com/blog/cross-agent-skills-new-npm | "Skills are the new npm" analysis; fragmentation critique |
| The Register | https://www.theregister.com/2026/04/16/anthropic_mcp_design_flaw/ | MCP design flaw: 200K servers at risk |
| Check Point Research | https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/ | CVE-2025-59536, CVE-2026-21852 |
| okhlopkov.com | https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/ | Real-world 4-month daily use config |
| sankalp.bearblog.dev | https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/ | Claude Code 2.0 workflow guide |
| paperclipped.de | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | SKILL.md standard adoption timeline |
| mintlify.com | https://www.mintlify.com/blog/skill-md | Official SKILL.md specification explainer |
| ice-ice-bear.github.io | https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/ | Plugin marketplace architecture deep dive |
| dev.to (rafsilva85) | https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g | SkillFlow MCP marketplace architecture |
| medium.com/@automation.labs | https://medium.com/@automation.labs/skill-md-is-becoming-the-rest-of-agents-nobody-told-you-yet-f5de9a5859c3 | "SKILL.md Is Becoming the REST of Agents" |
| TechTimes | https://www.techtimes.com/articles/317092/20260525/notion-opens-workspace-claude-code-cursor-codex-native-ai-agents.htm | Notion opens to Claude Code/Cursor/Codex (May 25, 2026) |
| morphllm.com (Reddit) | https://www.morphllm.com/claude-code-reddit | Reddit community sentiment aggregate |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | Complete 2026 MCP plugins guide |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Plugin guide 2026 |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best plugins/skills/MCP 2026 |
| buildtolaunch.substack.com | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | 10 tested, 4 worth keeping |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers 2026 |
| truefoundry.com | https://www.truefoundry.com/blog/best-mcp-servers-for-claude-code | Best MCP servers for Claude Code |
| nimbalyst.com (MCP) | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | Best Claude Code MCP servers |
| codersera.com | https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/ | 15 MCP servers worth wiring in |
| f5.com | https://www.f5.com/company/blog/agent-skills-an-emerging-open-standard | F5 analysis of agent skills standard |
| agentskills.io | https://agentskills.io/home | Agent Skills open standard hub |
| qcode.cc | https://qcode.cc/en/anthropic-agent-skills-standard-guide | Cross-vendor guide to agent skills |
| toknow.ai | https://toknow.ai/posts/superpowers-mattpocock-skills-cross-platform-agent-framework/ | Cross-platform skills frameworks |
| developersdigest.tech | https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026 | Agent teams/subagents 2026 playbook |
| developersdigest.tech (HN) | https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 | HN recurring themes on AI coding |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide to agent skills/plugins/marketplace |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | AI agent marketplace discovery landscape |
| rapidclaw.dev | https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026 | AI agent marketplace guide |
| serenitiesai.com | https://serenitiesai.com/articles/agent-skills-guide-2026 | Agent skills guide for 16+ AI tools |
| towardsdatascience.com | https://towardsdatascience.com/claude-skills-and-subagents-escaping-the-prompt-engineering-hamster-wheel/ | Escaping the prompt engineering hamster wheel |
| freecodecamp.org | https://www.freecodecamp.org/news/how-to-build-software-factory-with-claude-code/ | Software factory with Claude Code |
| cloudzero.com | https://www.cloudzero.com/blog/claude-code-agents/ | Claude Code agents, subagents, teams, costs |
| ramlit.com | https://www.ramlit.com/blog/custom-ai-agents-agentic-workflows-claude-code-2026-guide | Custom agents and agentic workflows guide |
| medium.com/@mohit15856 | https://medium.com/@mohit15856/10-claude-plugins-you-actually-need-in-2026-with-full-setup-guides-136f7d879c37 | 10 plugins with setup guides |
| oasis.security | https://www.oasis.security/blog/claude-ai-prompt-injection-data-exfiltration-vulnerability | "Claudy Day" prompt injection attack |
| lasso.security | https://www.lasso.security/blog/the-hidden-backdoor-in-claude-coding-assistant | Indirect prompt injection in Claude Code |
| ox.security | https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ | MCP STDIO RCE supply chain advisory |
| truefoundry.com (sec) | https://www.truefoundry.com/blog/claude-code-prompt-injection | Enterprise prompt injection guide |
| mintmcp.com | https://www.mintmcp.com/blog/claude-cowork-promt-injection | Prompt injection risks guide |
| composio.dev | https://composio.dev/toolkits/github/framework/claude-code | GitHub MCP with Claude Code |
| composio.dev (tiktok) | https://composio.dev/toolkits/tiktok/framework/claude-code | TikTok MCP with Claude Code |
| portermetrics.com | https://portermetrics.com/en/tutorial/claude/chat-tiktok-organic/ | Connect TikTok to Claude |
| agent-wars.com | https://www.agent-wars.com/news/2026-04-04-travel-hacking-toolkit-ai-agents-award-flights | Travel Hacking Toolkit skill |
| LinkedIn (Rob Foster) | https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we | Claude Code survival guide 2026 |
| duet.so | https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills | Agent skills 101 guide |
| verdent.ai | https://www.verdent.ai/guides/claude-skills-vs-mcp-agents-comparison | Skills vs MCP vs Agents comparison |
| markets.financialcontent.com | https://markets.financialcontent.com/wral/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability | Agent Skills open standard launch |
| k21academy.com | https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/ | Skills vs sub-agents vs MCP |
| itecsonline.com | https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 | Codex CLI agent skills guide |
| nayakpplaban.medium.com | https://nayakpplaban.medium.com/agent-skills-standard-for-smarter-ai-bde76ea61c13 | Agent Skills standard analysis |
| nimbalyst.com (skills) | https://nimbalyst.com/blog/claude-code-skills-guide/ | Claude Code skills practical guide |
| mcpmarket.com (HN) | https://mcpmarket.com/tools/skills/hacker-news-agent | Hacker News agent skill |
| mcpmarket.com (tiktok) | https://mcpmarket.com/tools/skills/tiktok-content-strategy | TikTok content strategy skill |
| claudskills.com | https://claudskills.com/skills/tiktok-automation/ | TikTok automation skill |
| groundy.com | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Official Anthropic plugin ecosystem |
| hermesatlas.com | https://hermesatlas.com/projects/mukul975/Anthropic-Cybersecurity-Skills | Cybersecurity skills for Claude Code |
| claudelog.com | https://claudelog.com/claude-code-mcps/reddit-mcp/ | Claude Code MCPs and Reddit |
| morphllm.com (ext) | https://www.morphllm.com/claude-code-extensions | Claude Code extensions guide |
| code.claude.com | https://code.claude.com/docs/en/security | Claude Code security docs |
| gist.github.com | https://gist.github.com/septimlabs-code/1f52e699a4a6fbe9c29621b670b958d1 | 5 MCP servers every user should know |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (multiple) | MCP is a fad | High | Multi-page | "easy to create MCP server with data exfil loopholes" — falloutx; "write once, support every AI client" — kburman | https://news.ycombinator.com/item?id=46552254 |

**GitHub:**
| Repo | Description | URL |
|------|-------------|-----|
| modelcontextprotocol/servers | Official MCP servers (Linux Foundation) | https://github.com/modelcontextprotocol/servers |
| anthropics/claude-plugins-official | Official Anthropic plugin marketplace | https://github.com/anthropics/claude-plugins-official |
| anthropics/claude-ai-mcp | Anthropic MCP issue tracker | https://github.com/anthropics/claude-ai-mcp |
| microsoft/skills | Skills, MCP servers, Custom Agents, Agents.md | https://github.com/microsoft/skills |
| microsoft/azure-skills | Azure Skills (200+ tools, 40+ services) | https://github.com/microsoft/azure-skills |
| microsoft/skills-for-fabric | Microsoft Fabric skills | https://github.com/microsoft/skills-for-fabric |
| MicrosoftDocs/Agent-Skills | Microsoft Learn grounded skills | https://github.com/MicrosoftDocs/Agent-Skills |
| MicrosoftDocs/mcp | Microsoft Learn MCP Server | https://github.com/MicrosoftDocs/mcp |
| VoltAgent/awesome-agent-skills | 1,000+ cross-platform skills | https://github.com/VoltAgent/awesome-agent-skills |
| sickn33/antigravity-awesome-skills | 1,400+ agentic skills with installer CLI | https://github.com/sickn33/antigravity-awesome-skills |
| mukul975/Anthropic-Cybersecurity-Skills | 754 cybersecurity skills (MITRE ATT&CK) | https://github.com/mukul975/Anthropic-Cybersecurity-Skills |
| rohitg00/awesome-claude-code-toolkit | 135 agents, 35 skills, 176+ plugins | https://github.com/rohitg00/awesome-claude-code-toolkit |
| GetBindu/awesome-claude-code-and-skills | Collection of Claude Skills | https://github.com/GetBindu/awesome-claude-code-and-skills |
| quemsah/awesome-claude-plugins | 18,543 repos indexed (adoption metrics) | https://github.com/quemsah/awesome-claude-plugins |
| VILA-Lab/Dive-into-Claude-Code | Systematic Claude Code analysis | https://github.com/VILA-Lab/Dive-into-Claude-Code |
| CloudAI-X/claude-workflow-v2 | Universal Claude Code workflow plugin | https://github.com/CloudAI-X/claude-workflow-v2 |
| github/github-mcp-server | GitHub's official MCP Server | https://github.com/github/github-mcp-server |
| efij/awesome-claude-code-security | Security resources for Claude Code | https://github.com/efij/awesome-claude-code-security |
| Seym0n/tiktok-mcp | TikTok MCP integration | https://github.com/Seym0n/tiktok-mcp |
| JCodesMore/youtube-mcp | YouTube research plugin for Claude Code | https://github.com/JCodesMore/youtube-mcp |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | N/A | N/A | No | https://www.youtube.com/watch?v=uogzSxOw4LU |

---

## Stats Block

```
├─ 🟠 Reddit: 1 community summary │ 4,200+ weekly r/ClaudeCode contributors │ aggregated
├─ 🔵 X: 0 posts │ (not retrieved directly)
├─ 🔴 YouTube: 1 video │ views N/A │ 0 with transcripts
├─ 🟢 HN: 1 thread │ high engagement │ multi-page MCP debate
├─ 🟣 TikTok: 0 videos │ (skills/MCP integrations found, no direct posts)
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ (not retrieved)
├─ 📊 Polymarket: 0 markets │ (no agent skills markets found)
├─ 🌐 Web: 60+ pages │ guides, analyses, official docs, security research
└─ 🗣️ Top voices: @kburman (HN, pro-MCP), @falloutx (HN, anti-MCP), @the_mitsuhiko (HN, skeptic) │ r/ClaudeCode
```

---

## Data Gaps

- **Reddit:** Direct Reddit indexing unavailable. Community sentiment aggregated via third-party morphllm.com digest and claudelog.com. Specific thread URLs, upvote counts, and usernames not retrievable. Approximate coverage: 30% of actual Reddit volume.
- **X/Twitter:** Excluded per instructions. No X data collected.
- **TikTok:** No TikTok creator content about agent skills found directly. TikTok MCP integration tools documented, but no TikTok posts on the topic retrieved.
- **Bluesky:** No Bluesky posts on this topic retrieved; search queries returned no direct Bluesky results.
- **Polymarket:** No prediction markets found related to MCP adoption, agent skills standards, or plugin ecosystems.
- **YouTube:** Only one video title found; YouTube content not retrievable due to authentication/rendering limitations. Likely significant video content on the topic not captured.
- **Hacker News:** One thread directly retrieved. The HN "AI coding agents" discussion corpus likely contains additional relevant threads not surfaced in this run.
- **Approximate total coverage:** ~50–60% of the full signal landscape, weighted heavily toward web content. Reddit and social are underrepresented.

---

## Key Quotes

> "SKILL.md Is Becoming the REST of Agents. Nobody Told You Yet." — Automation Labs on Medium ([link](https://medium.com/@automation.labs/skill-md-is-becoming-the-rest-of-agents-nobody-told-you-yet-f5de9a5859c3))

> "Claude Code is the best coding tool I've ever used, for the 45 minutes a day I can actually use it." — r/ClaudeCode (top upvoted complaint) ([link](https://www.morphllm.com/claude-code-reddit))

> "Now I sit in one terminal and describe what I need." — Daniil Okhlopkov on eliminating context-switching ([link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/))

> "Put stable rules in CLAUDE.md, long workflows in skills." — Daniil Okhlopkov on configuration philosophy ([link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/))

> "The MCP protocol is becoming the USB-C of AI integrations — a universal standard that lets any AI model connect to any tool." — SkillFlow (dev.to) ([link](https://dev.to/rafsilva85/building-an-ai-skills-marketplace-how-skillflow-connects-mcp-servers-with-business-teams-4i9g))

> "easy to create MCP server with data exfil loopholes" — falloutx on HN ([link](https://news.ycombinator.com/item?id=46552254))

> "write once, support every AI client" — kburman on MCP's value proposition ([link](https://news.ycombinator.com/item?id=46552254))

> "a security audit of 22,511 skills found 140,963 issues — averaging 6.3 per skill, with 36% containing prompt injection vulnerabilities." — agensi.io marketplace analysis ([link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

> "A five-server setup with 58 tools can use 55,000+ tokens before any conversation starts." — morphllm.com on MCP context overhead ([link](https://www.morphllm.com/claude-code-skills-mcp-plugins))

> "The 'skills are the new npm' line started as a convenient analogy...But the analogy has become literal infrastructure." — Termdock analysis ([link](https://www.termdock.com/blog/cross-agent-skills-new-npm))
