# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-25
**Query type:** GENERAL
**Sources:** Hacker News, YouTube, X/Twitter, Web, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 11 threads | 743+ points, 373+ comments | Top thread: 738 pts, 370 comments |
| YouTube | 4 videos | N/A | Tutorial/guide content |
| X/Twitter | 1 post | N/A | Found via search snippet |
| Web | 80+ pages | — | Blogs, docs, news, security reports |
| Reddit | 0 | — | API blocked, no data |
| TikTok | 0 | — | No results |
| Instagram | 0 | — | No results |
| Bluesky | 0 | — | No results |
| Polymarket | 0 | — | No markets found |

---

## Synthesized Findings

### 1. The SKILL.md Standard: Anthropic's Play for Cross-Platform AI Infrastructure

The biggest structural story of the past 30 days is the normalization of SKILL.md as the de facto open standard for reusable agent capabilities across the entire AI coding tool ecosystem. On December 18, 2025, Anthropic released the Agent Skills specification as an open standard, and within weeks OpenAI, GitHub Copilot, Vercel, Cursor, Gemini CLI, Roo Code, Amp, Goose, Mistral AI, Databricks, and at least 14 others had adopted the same format — 26+ platforms total.

The format is intentionally minimal: a directory containing a SKILL.md file with YAML frontmatter (name and description at minimum) plus optional scripts, templates, and resources. The elegance is the progressive disclosure model — only metadata loads at startup, the full skill loads when relevant, and additional linked files only when invoked — keeping context footprint small across many skills.

The Anthropic engineering blog post ([published October 2025](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)) frames this explicitly as infrastructure for "equipping agents for the real world" — enabling them to manipulate PDFs, orchestrate external services, and execute deterministic code without the agent having to improvise every time. The spec itself lives at [agentskills.io](https://agentskills.io/home) and [anthropics/skills GitHub](https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md).

The Hacker News thread "[Claude Skills are awesome, maybe a bigger deal than MCP](https://news.ycombinator.com/item?id=45619537)" (738 points, 370 comments) captured this shift: consensus in the top comments is that Skills represent "a simpler, more elegant pattern than MCP's complexity." Skeptics pushed back that this formalizes what developers already do with markdown files, but the counter-argument — that immediate feedback loops (testing documentation with Claude provides instant validation) plus self-interest motivation drive adoption differently — won the thread.

The [DEV Community piece](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg) tracking cross-ecosystem adoption calls this Anthropic's "next bid to define AI standards" (echoed by [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)).

**Platforms discussing this:** Hacker News, Web (Anthropic Engineering, DEV.to, InfoQ, New Stack, Strapi)

---

### 2. Marketplace Explosion: From Zero to npm-Scale in Two Months

The growth numbers are striking enough to be the clearest signal in the data. npm took a decade to reach 350,000 packages; the agent skills ecosystem reached the same scale in approximately two months after the open standard dropped. By April 2026:

- **[skills.sh](https://skills.sh/)** (Vercel, launched January 20, 2026): 83,627 skills, 8M+ total installs, 18 AI agents supported. Install via `npx skills add <package>`. Partners with Snyk for supply chain security. ([Vercel changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem), [InfoQ coverage](https://www.infoq.com/news/2026/02/vercel-agent-skills/), [Snyk blog](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/))
- **[SkillsMP](https://skillsmp.com)**: 66,541+ skills, built around the open SKILL.md standard. ([SmartScope review](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/))
- **[agentskill.sh](https://agentskills.io/home)**: 110,000+ skills across 20+ AI tools, two-layer security scanning, /learn installer.
- **[tonsofskills.com](https://tonsofskills.com/)** (by [jeremylongshore](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)): 423 plugins, 2,849 skills, 177 agents; ccpi CLI package manager (`ccpi install devops-automation-pack`).
- **[claudemarketplaces.com](https://claudemarketplaces.com/)**: 150+ skills as of March 2026.

Major enterprise players shipped official skills before Q1 ended: Vercel, Prisma, Supabase, Stripe, Remotion, Coinbase, and Microsoft. The [anthropics/skills repo](https://github.com/anthropics/skills) hit ~73,000 GitHub stars.

The [KDNuggets piece](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) and [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) both frame this as "Agent Skills Are the New npm" — a comparison that's becoming conventional wisdom across the developer community.

**Platforms discussing this:** Web (InfoQ, KDNuggets, SmartScope, BuildMVPFast, Termdock), Hacker News

---

### 3. The Three-Layer Architecture: Skills vs. MCP vs. Plugins

A recurring theme across HN, DEV.to, and content guides is educating developers on when to use each of the three extension types that now define the Claude Code ecosystem:

- **Skills** (SKILL.md files): "Code generation" layer. Markdown instructions dropped into `.claude/skills/` or `~/.claude/skills/`. Low complexity, no server, no dependencies. Activate automatically when Claude detects relevance. Best for: solo developers, project conventions, repeated workflows.
- **MCP Servers**: "Knowledge and connectivity" layer. Standalone programs exposing tools, resources, prompts over a standardized protocol. Medium-to-high complexity. Best for: connecting Claude to external services (GitHub, Figma, Playwright, PostgreSQL, Vercel).
- **Plugins**: Bundled packages that combine all of the above — slash commands, subagents, MCP configurations, hooks, and skills — into a single installable unit. The Plugin marketplace formally launched February 2026. Best for: teams and enterprises wanting consistent tooling.

The [devtoolpicks.com guide](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) distills it: "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." The [Morph guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) and [DEV.to piece by williamwangai](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) make the same three-layer distinction.

The HN thread "[Claude Skills vs. MCP: Complementary Philosophies for AI Customization](https://news.ycombinator.com/item?id=45766686)" frames them as non-competing: Skills handle procedural knowledge with filesystem-based progressive disclosure; MCP handles runtime connectivity to external services.

**Platforms discussing this:** Hacker News, Web (Morph, DEV.to, DevToolPicks, TurboDocx, Composio)

---

### 4. Official Plugin Marketplace and Enterprise Push (February 2026)

On February 24, 2026, Anthropic's [enterprise Cowork announcement](https://claude.com/blog/cowork-plugins-across-enterprise) formalized the enterprise plugin strategy:

- **Private plugin marketplaces**: Organizations create curated catalogs with admin controls over plugins, connectors, and skills across teams.
- **Unified Customize menu**: Consolidates plugins, skills, and connectors in one place.
- **Private GitHub repository support** (beta) for enterprise skills.
- **Per-user provisioning + auto-install** for org-wide rollout.
- **OpenTelemetry support** for usage, cost, and tool activity tracking.
- **12+ new enterprise connectors**: Google Workspace (Calendar, Drive, Gmail), Docusign, Apollo, Clay, Outreach, and others.
- **Cross-app orchestration**: Multi-step tasks across Excel and PowerPoint (research preview).
- **9 industry-specific plugins**: HR, Design, Engineering, Operations, Financial Analysis, Investment Banking, Equity Research, Private Equity, Wealth Management, Brand Voice (by Tribe AI).

PwC's Sanjay Subramanian: "Agentic AI [is reshaping] how finance teams operate, making them more strategic by enabling ambitious work."

The official Anthropic-managed plugin catalog ([claude-plugins-official](https://github.com/anthropics/claude-plugins-official)) auto-loads when starting Claude Code; browse via `/plugin` → Discover tab or [claude.com/plugins](https://code.claude.com/docs/en/discover-plugins). Additional community catalogs: [buildwithclaude.com](https://buildwithclaude.com/), [claudemarketplaces.com/marketplaces](https://claudemarketplaces.com/marketplaces), [aitmpl.com/plugins](https://www.aitmpl.com/plugins/).

**Platforms discussing this:** Web (Anthropic blog, Claude docs, LiteLLM, Composio)

---

### 5. Security Crisis: 30 CVEs in 60 Days, Supply Chain Under Attack

The skills/plugin/MCP ecosystem now has a serious and widely-documented security problem. The first two months of 2026 saw an unprecedented wave:

**Structural vulnerabilities in MCP:**
- BlueRock Security scan of 7,000+ public MCP servers: **36.7% SSRF vulnerable, 43% unsafe command execution, 41% zero authentication** in the official registry. ([TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries))
- OX Security disclosed an **architectural RCE vulnerability** in MCP's design affecting 150M+ downloads — Cursor, VS Code, Windsurf, Claude Code, and Gemini-CLI all affected. ([OX Security](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/), [The Hacker News April 2026](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html))
- Palo Alto Unit 42 documented new attack vectors via MCP Sampling for prompt injection. ([Unit 42](https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/))
- Microsoft published defensive guidance on indirect injection through tool metadata. ([Microsoft Dev Blog](https://developer.microsoft.com/blog/protecting-against-indirect-injection-attacks-mcp))

**Specific CVEs and incidents:**
- **Check Point CVE-2025-59536 (CVSS 8.7)**: Configuration injection exploiting Claude Code Hooks — attackers gain RCE when a developer opens a project. ([PipeLab](https://pipelab.org/blog/state-of-mcp-security-2026/))
- **Postmark supply chain attack (September 2025)**: Backdoored MCP server published to the official registry.
- **ClawHub malware campaign (January 2026)**: 335 malicious skills targeting API keys, wallet credentials, and browser passwords.
- **9 out of 11 MCP registries** successfully poisoned in a security trial balloon.
- **30 CVEs filed in first 60 days of 2026.** ([heyuan110.com](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/))

**Audit tools emerging:**
- [mcpserver-audit](https://github.com/ModelContextProtocol-Security/mcpserver-audit) (Cloud Security Alliance project)
- [mcp-security-audit](https://github.com/qianniuspace/mcp-security-audit) (npm package dependency auditor)
- Cisco YARA-based mcp-scanner
- MCPTox and MindGuard for tool poisoning detection

Vercel's skills.sh partnership with Snyk ([snyk.io blog](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/)) and Apigene's 251+ vendor-verified, OWASP-scanned servers ([Apigene](https://apigene.ai/blog/mcp-marketplace)) are the clearest security-differentiating moves in the marketplace space.

**Platforms discussing this:** Web (Hacker News, Practical DevSecOps, Aembit, OX Security, Pipelab, DEV.to, Security Boulevard, Palo Alto, Marmelab, AppSecSanta)

---

### 6. Hooks as Lifecycle Automation and Attack Surface

Claude Code's Hooks system enables user-defined shell commands at specific lifecycle points — providing deterministic automation rather than LLM-chosen actions. Official docs at [hooks-guide](https://code.claude.com/docs/en/hooks-guide); configure via `~/.claude/settings.json`; browse/manage via `/hooks` command.

Use cases driving adoption: enforcing project conventions, automated pre-commit checks, integrating external CI tools, building the "spec-driven workflow + TDD enforcement" patterns popularized by Claude CodePro (Max Ritter) and the [ClaudoPro Directory](https://www.claudedirectory.org/blog/claude-code-cheat-sheet).

The security flip side: Check Point's CVE-2025-59536 specifically exploits Hooks as the attack vector — if an attacker can inject malicious configuration into a project, the deterministic shell execution that makes Hooks powerful becomes an RCE path. This is the clearest example of how Claude Code's extensibility features create structural attack surface.

Community resources: [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) (hooks, slash commands, agent orchestrators), [awesomeclaude.ai cheatsheet](https://awesomeclaude.ai/code-cheatsheet), [skillsplayground.com slash commands guide](https://skillsplayground.com/guides/claude-code-slash-commands/).

**Platforms discussing this:** Web (Claude Docs, Morph, SkillsPlayground, Builder.io, Practical DevSecOps)

---

### 7. Monetization: The Missing Layer

Agent37's Show HN ([item #46422134](https://news.ycombinator.com/item?id=46422134)) surfaced a real gap: 1,000+ MCP skills on GitHub with zero way for creators to charge for them. The core friction is distribution: "Selling Claude skills today means asking customers to download your skill, set up Claude Code on their laptops, configure MCP servers, and pray it works."

Agent37's answer: upload a skill, share a link, anyone can try it instantly without a Claude account. Built-in Stripe, creators keep 80%. The creator reported one user making $1,600+ already. The thread was small (5 pts, 3 comments) but the problem it identifies — no native monetization infrastructure in the main marketplaces — is a genuine gap that's drawing indie developer attention.

The custom GPTs parallel is obvious and repeatedly drawn in discussion: skills marketplaces risk replicating the OpenAI GPT Store's discovery and monetization failures if the main platforms don't build first-party monetization tools.

**Platforms discussing this:** Hacker News

---

### 8. Multi-Agent Orchestration and "Representing Agents as MCP Servers"

Two HN threads signal a frontier beyond simple skill installation:

- "[Show HN: Representing Agents as MCP Servers](https://news.ycombinator.com/item?id=44053754)": Wrapping entire agents as MCP servers, allowing Claude to delegate to specialized sub-agents via the same protocol used for tool calls.
- "[24 Simultaneous Claude Code agents on local hardware](https://news.ycombinator.com/item?id=47099597)" (February 2026): Tokio-native LLM orchestration pipeline in Rust routing through local Mistral 7B on RTX 4070 — demonstrating scalable multi-agent locally.
- "[Show HN: Roundtable MCP](https://news.ycombinator.com/item?id=45374908)" (September 2025): MCP server that orchestrates Claude Code alongside Cursor, Gemini, and Codex simultaneously.

These threads represent a layer above skill installation — architectural patterns for composing multiple agents and skills into coordinated pipelines. The [levnikolaevich/claude-code-skills](https://github.com/levnikolaevich/claude-code-skills) project bundles custom MCP servers (hex-line for hash-verified editing, hex-graph for code knowledge graphs, hex-ssh for remote SSH) alongside skills into an integrated development environment.

**Platforms discussing this:** Hacker News, GitHub

---

## Cross-Source Patterns

### Pattern 1: "Skills > MCP for simplicity" is the dominant developer narrative
**Platforms:** Hacker News (738-pt thread), Web (Morph, DevToolPicks, DEV.to, TurboDocx, Composio)
> "Skills are essentially markdown files with YAML metadata and supporting scripts — lightweight context management avoiding token bloat that plagues MCP implementations." — HN consensus, [item #45619537](https://news.ycombinator.com/item?id=45619537)
> "MCP is the plumbing. Skills are the instructions." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)

### Pattern 2: Ecosystem scale vs. security preparedness are running on different timelines
**Platforms:** Web (OX Security, Hacker News, The Hacker News, Palo Alto, Security Boulevard, PipeLab, Marmelab)
> "36.7% of 8,000+ public MCP servers had SSRF vulnerabilities, 43% unsafe command execution, 41% zero authentication in the official registry." — BlueRock Security via [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries)
> "9 out of 11 MCP registries were successfully poisoned." — [PipeLab](https://pipelab.org/blog/state-of-mcp-security-2026/)

### Pattern 3: Cross-platform portability as competitive advantage
**Platforms:** Web (InfoQ, DEV.to, GitHub Changelog, VS Magazine, Strapi, agentskills.io)
> "In December 2025, Anthropic released the Agent Skills specification as an open standard, and OpenAI adopted the same format for Codex CLI and ChatGPT." — [agentskills.io](https://agentskills.io/home)
> Skills you create are portable and work across any skills-compatible agent." — [GitHub Docs](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)

### Pattern 4: "Agent skills as the new npm" framing is becoming conventional wisdom
**Platforms:** Web (BuildMVPFast, KDNuggets, InfoQ, Vercel Changelog, SkillsMP, SmartScope)
> "npm took a decade to reach 350,000 packages — the AI agent skills ecosystem did it in about two months." — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

---

## Per-Platform Tables

### Hacker News

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (simonwillison.net) | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | "documentation that allows you to better harness a computer minion to your will is attractive" | https://news.ycombinator.com/item?id=45619537 |
| various | Claude Skills vs. MCP: Complementary Philosophies for AI Customization | — | — | "Skills are filesystem-based procedural knowledge; MCP handles runtime connectivity" | https://news.ycombinator.com/item?id=45766686 |
| vishnukool | Show HN: Agent37 – Monetize your Claude skills with shareable links | 5 | 3 | "One of them has made more than $1600 so far, so I think she's happy." | https://news.ycombinator.com/item?id=46422134 |
| various | Show HN: Roundtable MCP, Orchestrate Claude Code, Cursor, Gemini and Codex | — | — | — | https://news.ycombinator.com/item?id=45374908 |
| various | 24 Simultaneous Claude Code agents on local hardware | — | — | Tokio-native Rust LLM orchestration on RTX 4070 | https://news.ycombinator.com/item?id=47099597 |
| various | Show HN: Agent37 – Monetize your Claude skills | 5 | 3 | "Selling Claude skills today means asking customers to… pray it works." | https://news.ycombinator.com/item?id=46422134 |
| various | Tengu – An MCP server that turns Claude into a pentester's copilot | — | — | 80 tools, 20 resources, 35 prompts | https://news.ycombinator.com/item?id=47296367 |
| various | Claude Code Skills and Plugins as an Open Source Project | — | — | — | https://news.ycombinator.com/item?id=47321892 |
| various | Which MCP servers are Claude Code must-adds for coding | — | — | — | https://news.ycombinator.com/item?id=44347116 |
| various | Show HN: UI and MCP server for analyzing Claude Code history | — | — | — | https://news.ycombinator.com/item?id=46500801 |
| various | Show HN: Representing Agents as MCP Servers | — | — | — | https://news.ycombinator.com/item?id=44053754 |
| various | Trading with Claude, and writing your own MCP server | — | — | — | https://news.ycombinator.com/item?id=44061614 |

### YouTube

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | N/A | N/A | No | https://www.youtube.com/watch?v=KjEFy5wjFQg |
| (unknown) | FULL Claude Tutorial For Beginners in 2026! (FULL COURSE) | N/A | N/A | No | https://www.youtube.com/watch?v=Xg55nTrbYYY |
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | N/A | N/A | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| (unknown) | FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step) | N/A | N/A | No | https://www.youtube.com/watch?v=qYqIhX9hTQk |

### X/Twitter

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Praiseakinlami | "Hope you all know about Claude skills. I use it for my viral tweets and I get vitality every time." | N/A | N/A | https://x.com/Praiseakinlami/status/2018359352965411097 |

### Web

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Official Agent Skills announcement (Oct 2025); progressive disclosure design explained |
| Anthropic Blog (Enterprise) | https://claude.com/blog/cowork-plugins-across-enterprise | Feb 24 enterprise plugin marketplace launch; private orgs, OpenTelemetry, 12+ connectors |
| Claude Code Docs – Plugins | https://code.claude.com/docs/en/plugins | Official plugin creation documentation |
| Claude Code Docs – Discover Plugins | https://code.claude.com/docs/en/discover-plugins | Plugin discovery and installation docs |
| Claude Code Docs – Hooks | https://code.claude.com/docs/en/hooks-guide | Official hooks automation guide |
| anthropics/skills GitHub | https://github.com/anthropics/skills | 73k stars; official Agent Skills repo + spec |
| Agent Skills Spec | https://github.com/anthropics/skills/blob/main/spec/agent-skills-spec.md | The SKILL.md specification source |
| agentskills.io | https://agentskills.io/home | Agent Skills hub; 110k+ skills |
| skills.sh (Vercel) | https://skills.sh/ | Vercel's directory; 83k+ skills, 8M installs |
| Vercel Changelog | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | Jan 20, 2026 launch announcement |
| Vercel Docs | https://vercel.com/docs/agent-resources/skills | Skills documentation |
| vercel-labs/skills GitHub | https://github.com/vercel-labs/skills | CLI source repo |
| Snyk + Vercel | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Security partnership for skills.sh |
| SkillsMP | https://skillsmp.com | 66k+ skills marketplace |
| SmartScope SkillsMP Review | https://smartscope.blog/en/blog/skillsmp-marketplace-guide/ | 66,500+ skills detailed review |
| tonsofskills.com | https://tonsofskills.com/ | 423 plugins, 2,849 skills, 177 agents; ccpi CLI |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | ccpi package manager source + catalog |
| MCPMarket.com | https://mcpmarket.com/ | 10,000+ MCP servers; 23+ categories |
| Official MCP Registry | https://registry.modelcontextprotocol.io/ | Anthropic/GitHub/PulseMCP/Microsoft backed METAREGISTRY |
| MCP Registry Blog | https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/ | Sep 2025 preview announcement |
| modelcontextprotocol/registry GitHub | https://github.com/modelcontextprotocol/registry | Registry source |
| Glama MCP Registry | https://glama.ai/mcp/servers | 22,111 open-source MCP servers |
| mcp.so | https://mcp.so/ | 5,000+ MCP server directory |
| TrueFoundry MCP Registries | https://www.truefoundry.com/blog/best-mcp-registries | Comparison of registries; security scan stats |
| Apigene MCP Marketplace | https://apigene.ai/blog/mcp-marketplace | 251+ OWASP-scanned verified servers |
| OX Security (architectural RCE) | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | Critical MCP design flaw, 150M+ downloads affected |
| OX Security (supply chain) | https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ | MCP Supply Chain Advisory |
| The Hacker News (RCE April 2026) | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | April 2026: MCP design vulnerability enables RCE |
| PipeLab MCP Security State | https://pipelab.org/blog/state-of-mcp-security-2026/ | 30 CVEs, incidents, attack patterns 2026 |
| heyuan110 30 CVEs | https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/ | MCP Security 2026: 30 CVEs in 60 days |
| DEV.to MCP Security 118 findings | https://dev.to/ecap0/the-state-of-mcp-server-security-in-2026-118-findings-across-68-packages-4fkd | 118 findings across 68 packages |
| Marmelab MCP Security | https://marmelab.com/blog/2026/02/16/mcp-security-vulnerabilities.html | Feb 2026 MCP vulnerability deep dive |
| Practical DevSecOps | https://www.practical-devsecops.com/mcp-security-vulnerabilities/ | Prevent prompt injection and tool poisoning |
| Aembit MCP Security | https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ | Ultimate guide to MCP vulnerabilities |
| AppSecSanta YARA audit | https://appsecsanta.com/research/mcp-server-security-audit-2026 | YARA scanning of 33 MCP servers |
| Security Boulevard | https://securityboulevard.com/2026/01/mcp-security-how-to-prevent-prompt-injection-and-tool-poisoning-attacks/ | Jan 2026 prompt injection + tool poisoning |
| Palo Alto Unit 42 | https://unit42.paloaltonetworks.com/model-context-protocol-attack-vectors/ | MCP Sampling attack vectors |
| Microsoft Dev Blog (MCP injection) | https://developer.microsoft.com/blog/protecting-against-indirect-injection-attacks-mcp | Microsoft defensive guidance |
| Cyber Desserts AI Agent Risks | https://blog.cyberdesserts.com/ai-agent-security-risks/ | MCP, OpenClaw & supply chain risks |
| mcpserver-audit GitHub | https://github.com/ModelContextProtocol-Security/mcpserver-audit | Cloud Security Alliance audit tool |
| mcp-security-audit GitHub | https://github.com/qianniuspace/mcp-security-audit | npm dependency security audit MCP tool |
| GitHub Copilot Agent Skills Changelog | https://github.blog/changelog/2025-12-18-github-copilot-now-supports-agent-skills/ | Dec 18, 2025 Copilot adopts SKILL.md |
| GitHub Docs – Agent Skills | https://docs.github.com/en/copilot/concepts/agents/about-agent-skills | About agent skills (GitHub Docs) |
| GitHub Docs – Create Skills | https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills | Adding agent skills for Copilot |
| VS Code Docs – Agent Skills | https://code.visualstudio.com/docs/copilot/customization/agent-skills | Official VS Code agent skills guide |
| VS Magazine (Copilot Skills) | https://visualstudiomagazine.com/articles/2026/01/11/hand-on-with-new-github-copilot-agent-skills-in-vs-code.aspx | Hands-on review Jan 2026 |
| vscode-docs GitHub | https://github.com/microsoft/vscode-docs/blob/main/docs/copilot/customization/agent-skills.md | VS Code docs source |
| DEV.to Copilot Agent Skills 2026 | https://dev.to/incomplete_developer/agent-skills-example-github-copilot-visual-studio-2026-4jik | Agent Skills example Copilot VS 2026 |
| Medium – Copilot Skills | https://medium.com/@mpholoane/agent-skills-in-github-copilot-for-visual-studio-2026-stop-repeating-yourself-d0b5a0209f48 | Stop repeating yourself with Copilot skills |
| InfoQ Vercel Skills.sh | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Feb 2026 InfoQ coverage of Vercel launch |
| KDNuggets Marketplaces | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 skill marketplaces comparison |
| BuildMVPFast Agent Skills = npm | https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026 | "Agent Skills Are the New npm" |
| VirtualUncle Skills.sh Guide | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | Skills.sh detailed guide |
| Toolworthy Skills.sh Review | https://www.toolworthy.ai/tool/skills-sh | Skills.sh independent review |
| Termdock Agent Skills Guide | https://www.termdock.com/en/blog/agent-skills-guide | Build, share, and secure skills 2026 |
| The New Stack | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | Anthropic's bid to define AI standards |
| DEV.to SKILL.md Multi-Ecosystem | https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg | How SKILL.md crossed from Anthropic to OpenAI |
| Strapi What Are Agent Skills | https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them | Developer explainer |
| Calmops Complete Guide 2026 | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | Comprehensive guide |
| ArticleSledge Agent Skills | https://www.articsledge.com/post/agent-skills | What are Agent Skills? 2026 Guide |
| OpenAI Codex Skills | https://developers.openai.com/codex/skills | Official OpenAI Codex skills docs |
| LobeHub Skills Marketplace | https://lobehub.com/skills | Multi-agent skills marketplace |
| skillmatic-ai/awesome-agent-skills | https://github.com/skillmatic-ai/awesome-agent-skills | Definitive resource for Agent Skills |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated Claude Code plugins list |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 232+ Claude Code skills across 9 agents |
| quemsah/awesome-claude-plugins | https://github.com/quemsah/awesome-claude-plugins | n8n-powered adoption metrics tracker |
| hesreallyhim/awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | Curated Claude Code hooks/commands/skills |
| levnikolaevich/claude-code-skills | https://github.com/levnikolaevich/claude-code-skills | Plugin suite + hex-line/hex-graph/hex-ssh MCPs |
| anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | Official Anthropic plugin directory |
| ananddtyagi/cc-marketplace | https://github.com/ananddtyagi/cc-marketplace | Community Claude Code marketplace |
| Composio Top Claude Plugins | https://composio.dev/content/top-claude-code-plugins | Top 10 Claude Code plugins 2026 |
| Composio Twitter MCP | https://composio.dev/toolkits/twitter/framework/claude-code | Twitter MCP with Claude Code |
| Morph Extensions Guide | https://www.morphllm.com/claude-code-extensions | MCP, Skills, Agents & Hooks guide |
| Morph Skills vs MCP vs Plugins | https://www.morphllm.com/claude-code-skills-mcp-plugins | Three-layer comparison |
| DEV.to Best Skills 2026 | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills and plugins guide |
| DEV.to Skills vs MCP | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Comparison guide |
| TurboDocx Best Skills | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Claude Code Plugins & Skills 2026 |
| DevToolPicks Comparison | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | Skills vs MCP vs Plugins breakdown |
| self.md Best Plugins | https://self.md/guides/best-claude-code-plugins/ | Best claude code plugins guide 2026 |
| Firecrawl Top Plugins | https://www.firecrawl.dev/blog/best-claude-code-plugins | Top 10 Claude Code Plugins 2026 |
| Mejba Top 10 | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 Claude Code Skills/Plugins/CLIs |
| Producttalk How to Use Claude Code | https://www.producttalk.org/how-to-use-claude-code-features/ | Slash commands, agents, skills, plug-ins |
| Builder.io Claude Code Tips | https://www.builder.io/blog/claude-code | How I use Claude Code + best tips |
| SkillsPlayground Slash Commands | https://skillsplayground.com/guides/claude-code-slash-commands/ | Custom commands guide 2026 |
| AwesomeClaude Cheatsheet | https://awesomeclaude.ai/code-cheatsheet | Developer cheatsheet |
| Claude Directory Cheatsheet | https://www.claudedirectory.org/blog/claude-code-cheat-sheet | Claude Code Cheat Sheet 2026 |
| SmartScope Command Reference | https://smartscope.blog/en/generative-ai/claude/claude-code-reference-guide/ | Complete command reference 2026 |
| ScriptByAI Cheat Sheet | https://www.scriptbyai.com/claude-code-commands-cheat-sheet/ | Commands cheat sheet |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Claude Plugins & Skills marketplace |
| claudemarketplaces marketplaces dir | https://claudemarketplaces.com/marketplaces | Directory of plugin marketplaces |
| buildwithclaude.com | https://buildwithclaude.com/ | Build with Claude Plugin Marketplace |
| aitmpl.com plugins | https://www.aitmpl.com/plugins/ | Claude Code Plugins & Marketplaces |
| LiteLLM Plugin Marketplace | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Managed Skills via LiteLLM |
| awesome-skills.com | https://awesome-skills.com/ | Curated Claude skills directory |
| popularaitools.ai | https://popularaitools.ai/blog/claude-code-skills-plugins-clis-2026 | Skills/Plugins/CLIs guide |
| ClaudeLog Twitter MCP | https://claudelog.com/claude-code-mcps/twitter-mcp/ | Twitter/X MCP integration guide |
| MCPMarket X automation | https://mcpmarket.com/tools/skills/x-twitter-automation | X Twitter automation skill |
| MCPMarket X writing | https://mcpmarket.com/tools/skills/writing-x-posts | X posts writing skill |
| Medium Vercel Skills | https://medium.com/@natanael280198/how-vercels-new-agent-skills-library-can-help-improve-your-work-flow-4a2fb4e592f3 | Vercel skills workflow improvement |
| Dev Journal Vercel Skills | https://earezki.com/ai-news/2026-02-04-vercel-introduces-skillssh-an-open-ecosystem-for-agent-commands/ | Vercel skills.sh release notes |
| Ry Walker Research | https://rywalker.com/research/anthropic-skills | Anthropic skills research |
| Securing MCP Servers Medium | https://medium.com/@instatunnel/securing-mcp-servers-the-2026-guide-to-ai-tool-tunneling-aafa113b08db | MCP tunneling security guide |
| JetBrains Claude Code Plugin | https://plugins.jetbrains.com/plugin/27310-claude-code-beta- | Claude Code IntelliJ IDE Plugin |
| IPFoxy AI Agent Skills Guide | https://www.ipfoxy.com/blog/ideas-inspiration/5874 | Top 10 AI Agent Skills for 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ blocked by API
├─ 🔵 X: 1 post found │ N/A likes │ N/A reposts
├─ 🔴 YouTube: 4 videos │ views N/A
├─ 🟢 HN: 12 stories │ 743+ points │ 373+ comments
├─ 🟣 TikTok: 0 videos │ 0 views
├─ 🩷 Instagram: 0 reels │ 0 views
├─ 🦋 Bluesky: 0 posts │ 0 likes
├─ 📊 Polymarket: 0 markets │ $0 volume
├─ 🌐 Web: 80+ pages
└─ 🗣️ Top voices: simonwillison.net (HN) │ OX Security, Palo Alto Unit 42 (security)
   Top repos: anthropics/skills (73k⭐), hesreallyhim/awesome-claude-code, skillmatic-ai/awesome-agent-skills
```

---

## Data Gaps

- **Reddit blocked**: The Reddit API returned a 400 error blocking crawling; zero Reddit discussion data captured. This is a significant gap — Reddit's r/ClaudeAI, r/LocalLLaMA, and r/programming likely have substantial discussion of MCP servers and skills. Estimated coverage loss: ~20%.
- **X/Twitter limited**: Only 1 organic X post found via search snippets; the X MCP integration links dominated results. Real-time Twitter discussion of new skill releases and security incidents is largely absent. Estimated coverage loss: ~15%.
- **YouTube views/likes unavailable**: 4 videos found but engagement metrics (views, likes, transcripts) were not accessible from search metadata alone.
- **TikTok/Instagram/Bluesky**: Zero results from any of these platforms. Topic appears primarily developer-focused, concentrated in HN and web blogs.
- **Polymarket**: No prediction markets found for this topic space.
- **HN point/comment counts**: Only the top thread (738 pts, 370 comments) and Agent37 (5 pts, 3 comments) had confirmed counts; remaining 10 HN threads lack confirmed engagement data.
- **Approximate coverage**: ~70% of likely available signal captured (strong on web, HN, GitHub; weak on Reddit, X, social video).

---

## Key Quotes

> "Skills are essentially markdown files with YAML metadata and supporting scripts — lightweight context management avoiding token bloat that plagues MCP implementations." — HN consensus on [Claude Skills are awesome, maybe a bigger deal than MCP](https://news.ycombinator.com/item?id=45619537)

> "Selling Claude skills today means asking customers to download your skill, set up Claude Code on their laptops, configure MCP servers, and pray it works." — @vishnukool (Agent37 creator) on [Hacker News](https://news.ycombinator.com/item?id=46422134)

> "npm took a decade to reach 350,000 packages — the AI agent skills ecosystem did it in about two months." — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

> "36.7% of 8,000+ public MCP servers had SSRF vulnerabilities, 43% had unsafe command execution paths, and 41% in the official registry had zero authentication." — BlueRock Security via [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries)

> "9 out of 11 MCP registries were successfully poisoned with a malicious trial balloon." — [PipeLab](https://pipelab.org/blog/state-of-mcp-security-2026/)

> "Agentic AI [is reshaping] how finance teams operate, making them more strategic by enabling ambitious work." — PwC's Sanjay Subramanian, via [Anthropic Enterprise Blog](https://claude.com/blog/cowork-plugins-across-enterprise)

> "documentation that allows you to better harness a computer minion to your will is attractive" — Anonymous HN commenter explaining why developers document for AI when they won't document for humans ([item #45619537](https://news.ycombinator.com/item?id=45619537))

> "One of them has made more than $1600 so far, so I think she's happy." — @vishnukool on early Agent37 creator revenue ([HN](https://news.ycombinator.com/item?id=46422134))

> "Hope you all know about Claude skills. I use it for my viral tweets and I get vitality every time." — @Praiseakinlami on [X](https://x.com/Praiseakinlami/status/2018359352965411097)

> "MCP is the plumbing that connects Claude to the outside world, while Skills are the instructions that teach Claude how to do specific things." — [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026)
