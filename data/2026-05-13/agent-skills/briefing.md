# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-13
**Query type:** GENERAL
**Sources:** Web, Hacker News, YouTube, Reddit (blocked), X/Twitter (blocked)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 threads | High points, active comment threads | Includes Show HN posts for skills/plugins |
| YouTube | 7 videos | High views | Tutorials, complete guides |
| Web | 60+ pages | — | Blogs, official docs, GitHub repos, news articles |
| Reddit | N/A | N/A | Domain blocked during research |
| X/Twitter | N/A | N/A | Domain blocked during research |
| Bluesky | N/A | N/A | No direct data returned |
| Polymarket | 2 markets | Active | Claude prediction markets; Polymarket MCP server documented |
| TikTok | N/A | N/A | No data returned |

---

## Synthesized Findings

### 1. The Agent Skills Open Standard: Anthropic's SKILL.md Goes Industry-Wide

On December 18, 2025, Anthropic released the Agent Skills open specification, defining a universal format for packaging procedural knowledge for AI coding agents. The core unit is a directory containing a `SKILL.md` file with YAML frontmatter (required `name` and `description` fields, plus optional fields) and Markdown instructions below the frontmatter. Skills can also bundle supporting scripts, templates, and reference materials.

What started as a Claude Code feature became an industry-wide standard at extraordinary speed. Simon Willison wrote about it on [December 19, 2025](https://simonwillison.net/2025/Dec/19/agent-skills/). When Vercel launched [skills.sh](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) in January 2026, the top skill hit 20,000 installs within six hours. Within 48 hours, Microsoft had integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI. By March 2026, **32 tools from competing companies** — including Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose — all read the same `SKILL.md` files. The specification is published at [agentskills.io](https://agentskills.io/home) and has been called one of the fastest standardization events in AI tooling history.

> "Skills are portable: build once, use across agents. Most skills that stick to the core format (SKILL.md with standard frontmatter and markdown instructions) work everywhere without modification." — Agent Skills Open Standard Explainer, [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

**Platforms discussing this:** Hacker News ([item 45607117](https://news.ycombinator.com/item?id=45607117), [item 47321892](https://news.ycombinator.com/item?id=47321892)), Web (InfoQ, Vercel, Simon Willison, agensi.io)

---

### 2. The Claude Code Plugin Ecosystem: Scale and Structure

Claude Code distinguishes between **skills** (single instruction sets) and **plugins** (bundles of multiple skills, MCP servers, or commands). The plugin system launched in public beta in October 2025 and is now stable. Key management commands: `/plugin install`, `/plugin enable/disable`, `/plugin marketplace`.

The community-built ecosystem has grown rapidly:
- **tonsofskills.com**: 2,778 skills across 427 plugins, curated by Jeremy Longshore. CLI: `pnpm add -g @intentsolutionsio/ccpi`, then `ccpi install <pack-name>`. Includes 42 SaaS skill packs covering 1,086 skills for specific platforms. All MIT-licensed, no monetization. ([GitHub repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills), [marketplace](https://tonsofskills.com/))
- **claudemarketplaces.com**: Directory of Claude Code plugins, skills, MCP servers ([link](https://claudemarketplaces.com/))
- **anthropics/claude-plugins-official**: Official Anthropic-managed directory ([GitHub](https://github.com/anthropics/claude-plugins-official))
- **ComposioHQ/awesome-claude-plugins**: Curated list of plugins (custom commands, agents, hooks, MCP servers) ([GitHub](https://github.com/ComposioHQ/awesome-claude-plugins))
- **alirezarezvani/claude-skills**: 245+ Claude Code skills & agent plugins ([GitHub](https://github.com/alirezarezvani/claude-skills))

As of May 11, 2026, the broader community has created **4,200+ skills** and **770+ MCP servers** for Claude Code.

> "The winning pattern in 2026 is a control stack: project rules, reusable skills, bounded sub-agents, and deterministic tools around the model." — Developers Digest, [developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

**Platforms discussing this:** Hacker News ([item 45530150](https://news.ycombinator.com/item?id=45530150), [item 46396930](https://news.ycombinator.com/item?id=46396930)), Web (DEV Community, BrightCoding blog, tonsofskills.com)

---

### 3. MCP Ecosystem Explosion: From Reference Implementations to Thousands of Servers

The Model Context Protocol ecosystem grew from a handful of reference implementations to thousands of servers in just over a year. Multiple specialized marketplaces now manage this growth:

- **MCPBundles** ([mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers)): 10,000+ tools across 700+ providers for production SaaS integrations
- **MCP Market** ([mcpmarket.com](https://mcpmarket.com/)): Searchable directory of MCP servers and skills
- **Glama** (glama.ai/mcp/servers): Searchable marketplace with previews
- **claudefa.st**: Listing of 50+ best MCP servers for Claude Code ([link](https://claudefa.st/blog/tools/mcp-extensions/best-addons))

Top MCP servers in 2026 by category: Figma (design), Playwright (browser automation/testing), Vercel (deployment), PostgreSQL (databases), GitHub (repo management), HubSpot, Salesforce, Ahrefs, Jira, Docker Hub, Slack, Notion, Google Workspace.

**Claude Code's MCP Tool Search** enables lazy loading for MCP servers, reducing context usage by up to 95%, allowing users to run all MCP servers without worrying about context limits.

A notable signal: Meta launched an official MCP for Facebook and Instagram ads on April 29, 2026, indicating major platform vendors are now shipping official MCP integrations. Polymarket also has an [MCP server](https://conare.ai/marketplace/mcp/polymarket-mcp) with 29 tools covering 9,706+ active contracts.

**Platforms discussing this:** Web (Toloka AI, Firecrawl, K2view, mcpbundles, skyvia), Hacker News ([item 43410866](https://news.ycombinator.com/item?id=43410866))

---

### 4. Enterprise Agent Registries: AWS, Microsoft, Google Enter the Space

With agent sprawl becoming a real enterprise problem, cloud providers launched governed registries in Q1/Q2 2026:

**AWS Agent Registry** (via Amazon Bedrock AgentCore, Preview since April 2026): A private, governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources within an organization. Features:
- Combines semantic understanding with keyword matching for discovery
- Accessible via AgentCore Console UI, APIs, or directly as an MCP server queryable from IDEs
- Approval workflow: drafts → pending approval → discoverable
- IAM-based access control, versioning, deprecation
- Cloud-agnostic: indexes agents regardless of hosting (AWS, other clouds, on-premises)

The Register quoted AWS: ["Agents shouldn't be secret, so we built a registry"](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/) — framing the problem as agent invisibility in large organizations.

Microsoft has Entra Agent Registry and Azure Agent Registry. Google Cloud has its own Agent Registry. This convergence signals that enterprise governance of agent capabilities is now a product category.

> "The registry combines semantic understanding with keyword matching so that both natural language queries and exact name lookups return relevant results." — AWS documentation, [docs.aws.amazon.com](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html)

**Platforms discussing this:** Web (InfoQ, SiliconANGLE, Dataconomy, TechBriefly, The Register, AWS blogs)

---

### 5. MCP Gateways: The Security and Governance Layer

A new product category emerged in 2026: **MCP Gateways** — intermediaries between AI agents and MCP servers providing a single governed entry point for all tool access. They centralize authentication, authorization, auditing, and traffic management, acting as smart brokers routing requests to appropriate tools while enforcing security policies.

Key gateway platforms:
- **MintMCP Gateway**: The industry's first SOC 2 Type II certified MCP platform ([integrate.io guide](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/))
- Microsoft provides MCP gateway functionality via its Learn docs ([learn.microsoft.com](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools))

ByteBridge identified the [Top 10 MCP Gateways in 2026](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a).

**Platforms discussing this:** Web (ByteBridge/Medium, Integrate.io, Microsoft Learn)

---

### 6. The Security Crisis: ToxicSkills, ClawHavoc, and Supply Chain Vulnerabilities

The rapid growth of agent skill ecosystems created a serious security crisis. Snyk conducted the first comprehensive security audit of the AI Agent Skills supply chain, scanning **3,984 skills** from ClawHub and skills.sh as of February 5, 2026:

- **1,467 malicious payloads** across 3,984 skills scanned — 36% flaw rate
- **534 skills (13.4%)** contained at least one critical-level security issue (malware distribution, prompt injection, exposed secrets)
- **76 confirmed malicious skills** with active payloads; 8 remained publicly available at publication
- Daily submissions jumped from under 50 in mid-January to over 500 by early February 2026 (10x increase in weeks)

The **ClawHavoc** attack campaign distributed hundreds of malicious skills through ClawHub using typosquatted names. These skills contained hidden scripts establishing reverse shells and exfiltrating SSH keys, API tokens, and browser session cookies.

VentureBeat reported: ["One command turns any open-source repo into an AI agent backdoor. OpenClaw proved no supply-chain scanner has a detection category for it."](https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner)

Snyk's threat modeling article title says it all: ["From SKILL.md to Shell Access in Three Lines of Markdown"](https://snyk.io/articles/skill-md-shell-access/)

**Response:** Snyk and Vercel launched a security partnership to audit skill submissions at scale. The [ToxicSkills-goof GitHub repo](https://github.com/snyk-labs/toxicskills-goof) provides reference examples for testing scanners.

**Platforms discussing this:** Web (Snyk, VentureBeat, obot.ai, agensi.io, AI Certs, cyberdesserts.com), GitHub

---

### 7. ClawHub and OpenClaw: The Largest Open Skill Registry

ClawHub ([clawhub.ai](https://clawhub.ai/)) is the public skill registry for OpenClaw. As of February 28, 2026, it hosts **13,729 community-built skills**, growing daily. The OpenClaw ecosystem has grown to over **5,700 community-contributed skills** in the VoltAgent curated list.

DigitalOcean published a [2026 Developer's Guide to OpenClaw Skills](https://www.digitalocean.com/resources/articles/what-are-openclaw-skills). DataCamp published a [Best ClawHub Skills guide](https://www.datacamp.com/blog/best-clawhub-skills). The platform is covered by Tencent Cloud and lobehub.com as well, indicating international distribution.

Skills distribution comparison: [agentskillexchange.com](https://agentskillexchange.com/openclaw-vs-claude-code-vs-codex-skill-distribution/) analyzed OpenClaw vs. Claude Code vs. Codex skill distribution approaches.

**Platforms discussing this:** Web (DigitalOcean, DataCamp, Tencent Cloud, VoltAgent GitHub, skywork.ai)

---

### 8. Vercel's Skills.sh Marketplace: 89,753 Skills and Growing

Vercel's open agent skills ecosystem ([skills.sh](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem)) has become a central hub:
- **89,753 skills** listed on the marketplace
- Growing at an average of **147 new skills per day**
- Installation: `npx skills add`
- InfoQ covered the launch: [Vercel Introduces Skills.sh, an Open Ecosystem for Agent Commands](https://www.infoq.com/news/2026/02/vercel-agent-skills/)
- Official Vercel documentation at [vercel.com/docs/agent-resources/skills](https://vercel.com/docs/agent-resources/skills)
- Official skill collection at [github.com/vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills)
- Third-party browser: [agentskills.to](https://www.agentskills.to/vercel-labs/skills/find-skills)

Security partnership with Snyk provides automated auditing of skill submissions at scale.

> "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." — digitalapplied.com, [AI Agent Marketplaces 2026](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution)

**Platforms discussing this:** Web (InfoQ, Vercel, Snyk, agentskills.to, agentskill.work)

---

### 9. Skills vs. MCP vs. Subagents: The Mental Model Debate

A key conceptual debate in the community is how to choose between skills, MCP servers, and subagents:

- **Skill**: Instructions telling the agent *how to do something*; modifies main agent behavior; loaded on demand based on context; stored as filesystem directories with SKILL.md
- **MCP Server**: Provides tools giving the agent *new things it can do*; connects Claude to external systems (APIs, databases); runs as separate process
- **Subagent**: A separate agent the main one delegates to; has its own context window, custom system prompts, specific tool permissions; introduces autonomy and reasoning

Hacker News discussion [item 45619537](https://news.ycombinator.com/item?id=45619537): "Claude Skills are awesome, maybe a bigger deal than MCP"

Hacker News Show HN [item 45642911](https://news.ycombinator.com/item?id=45642911): "Playwright Skill for Claude Code – Less context than playwright-MCP" — demonstrating skills can outperform MCP servers for some use cases because Claude can write and run code directly, receiving screenshots and console output, using fewer instruction lines.

Practical production setup consensus: ~5-10 skills for common workflows (code review, commits, docs, testing) + 2-3 MCP servers for daily-use services (database, CI/CD, monitoring).

MindStudio documented [5 Claude Code Workflow Patterns](https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns): sequential, operator, split-and-merge, agent teams, and headless.

**Platforms discussing this:** Hacker News ([item 45619537](https://news.ycombinator.com/item?id=45619537), [item 45642911](https://news.ycombinator.com/item?id=45642911)), Web (morphllm, k21academy, duet.so, nimbalyst)

---

### 10. Tooling for Managing Skills at Scale: GUIs, Apps, and Harnesses

As skill collections grow, developers need management tooling beyond manual file editing:

- **Ensemble** ([github.com/O0000-code/Ensemble](https://github.com/O0000-code/Ensemble)): macOS desktop app for managing Claude Code Skills, MCP Servers, and CLAUDE.md files. Features "Scenes" (bundles of related Skills, MCPs, and CLAUDE.md files). Released February 7, 2026. [Show HN discussion](https://news.ycombinator.com/item?id=46922223).
- **Claude Code Tool Manager** ([github.com/tylergraydev/claude-code-tool-manager](https://github.com/tylergraydev/claude-code-tool-manager)): GUI for managing MCP servers, Commands, Skills, Sub-Agents, and Hooks with visual toggle per project.
- **everything-claude-code** ([github.com/affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)): Agent harness performance optimization system (skills, instincts, memory, security, research-first development).
- **awesome-claude-code-toolkit** ([github.com/rohitg00/awesome-claude-code-toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit)): 135 agents, 35 curated skills (+400,000 via SkillKit), 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, 26 companion apps.

The [Anatomy of the .claude/ folder](https://news.ycombinator.com/item?id=47543139) HN thread reflects developer interest in understanding the complete configuration system.

**Platforms discussing this:** Hacker News ([item 46922223](https://news.ycombinator.com/item?id=46922223), [item 47543139](https://news.ycombinator.com/item?id=47543139)), GitHub, Web

---

### 11. Cross-Framework Adoption: Spring AI, LangGraph4j, IntelliJ

The Agent Skills standard has spread beyond CLI tools into backend frameworks:

- **Spring AI** ([spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/)): January 2026 blog post on Agentic Patterns using Agent Skills as modular, reusable capabilities for Java applications. Followed by [Anthropic Agent Skills Support in Spring AI](https://spring.io/blog/2026/01/28/apring-ai-anthropic-agentic-skills) (Jan 28, 2026). Library available at [spring-ai-community/spring-ai-agent-utils](https://github.com/spring-ai-community/spring-ai-agent-utils).
- **LangGraph4j + Spring AI**: [Skill-Based Sub-Agents with LangGraph4j and Spring AI](https://earezki.com/ai-news/2026-05-04-skill-based-sub-agents-with-langgraph4j-and-spring-ai/) (May 4, 2026) — building modular multi-agent systems.
- **IntelliJ IDEA**: JetBrains published [AI-Assisted Java Application Development with Agent Skills](https://blog.jetbrains.com/idea/2026/03/ai-assisted-java-application-development-with-agent-skills/) in March 2026.

**Platforms discussing this:** Web (spring.io, JetBrains blog, DEV Community, earezki.com)

---

### 12. Discovery and Monetization: Marketplace Fragmentation

Eight marketplaces now compete for agent skill distribution:
1. **Claude Skills** (Anthropic ecosystem, tonsofskills.com, claudemarketplaces.com) — free distribution
2. **GPT Store** — revenue share on usage
3. **MCP Hubs** (mcpmarket.com, mcpbundles.com, glama.ai)
4. **Hugging Face Spaces**
5. **Replit Agent Market** — direct-sale model
6. **LangChain Hub**
7. **Vercel Agent Gallery** (skills.sh, 89,753 skills)
8. **Cloudflare AI Marketplace** — bills on inference

Third-party aggregators/comparisons: [agensi.io marketplace comparison](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026), [agentskillexchange.com](https://agentskillexchange.com/openclaw-vs-claude-code-vs-codex-skill-distribution/), [skillsmp.com](https://skillsmp.com/).

skills.sh leaderboard: [agentskills.to](https://www.agentskills.to/vercel-labs/skills/find-skills) and [inference.sh/blog/skills](https://inference.sh/blog/skills/agent-skills-overview) provide discovery and ranking. [CalmOps complete guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) and [agensi.io open standard explainer](https://www.agensi.io/learn/agent-skills-open-standard) provide navigation guides.

**Platforms discussing this:** Web (digitalapplied.com, agensi.io, inference.sh, skillsmp.com)

---

## Cross-Source Patterns

**Pattern 1: Open Standard Convergence is Real and Fast**
- Appeared on: Web (20+ sources), Hacker News, YouTube tutorials
- The SKILL.md spec was adopted by 32 competing tools in ~90 days. This is the fastest cross-vendor AI tooling standardization on record. All major AI coding agents (Claude Code, Codex, Gemini CLI, Cursor, VS Code Copilot, Kiro, Goose) now read the same file format.
- Key quote: *"Within 48 hours [of Vercel launching skills.sh], Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI."* — paperclipped.de ([link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/))

**Pattern 2: Security Lag is Severe**
- Appeared on: Web (Snyk, VentureBeat, obot.ai, agensi.io, cyberdesserts.com, aicerts.ai)
- The supply chain threat is real and documented: 36% of scanned skills on major registries contain flaws; 76 confirmed malicious skills with active payloads (ClawHavoc campaign). No existing supply-chain scanner had a detection category for AI agent skill backdoors when VentureBeat reported.
- Key quote: *"From SKILL.md to Shell Access in Three Lines of Markdown"* — Snyk ([link](https://snyk.io/articles/skill-md-shell-access/))

**Pattern 3: Enterprise Governance is Now a Product Category**
- Appeared on: Web (AWS, Microsoft, Google, InfoQ, SiliconANGLE, The Register, Dataconomy)
- AWS, Microsoft, and Google all launched agent registries in Q1-Q2 2026. AWS positioned its registry as cloud-agnostic, indexing agents regardless of where they're built. The term "agent sprawl" now appears in enterprise product marketing.
- Key quote: *"Agents shouldn't be secret, so we built a registry"* — AWS via The Register ([link](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/))

**Pattern 4: Skills Beat MCP in Context Efficiency for Procedural Tasks**
- Appeared on: Hacker News (multiple threads), Web (morphllm, k21academy, duet.so)
- The HN post "Claude Skills are awesome, maybe a bigger deal than MCP" [item 45619537](https://news.ycombinator.com/item?id=45619537) sparked a community discussion that Skills can replace some MCP use cases by letting Claude write and execute code directly, using far fewer tokens. Claude Code's lazy-loading MCP Tool Search reduces context usage by up to 95%.
- Key quote: *"A skill is instructions that tells the agent what to do, while an MCP server provides tools that give it new things it can do."* — nimbalyst.com ([link](https://nimbalyst.com/blog/claude-code-skills-vs-mcp-plugins/))

**Pattern 5: Discovery Remains the Ecosystem's Weakest Link**
- Appeared on: Web (digitalapplied.com, developersdigest.tech, HN discussions)
- Despite massive ecosystem growth (89,753+ skills on skills.sh, 13,700+ on ClawHub, 2,700+ on tonsofskills.com), discovery tooling is lagging. Multiple community curations (awesome-agent-skills, awesome-openclaw-skills, awesome-claude-code-toolkit) exist because platform-native search is inadequate.
- Key quote: *"Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction."* — digitalapplied.com ([link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (community) | Claude Skills are awesome, maybe a bigger deal than MCP | — | High | "Skills allow Claude to write code and run it directly" | https://news.ycombinator.com/item?id=45619537 |
| (community) | Claude Skills | — | Active | Core spec discussion | https://news.ycombinator.com/item?id=45607117 |
| (community) | Customize Claude Code with plugins | — | Active | Plugin system launch discussion | https://news.ycombinator.com/item?id=45530150 |
| (community) | Show HN: Playwright Skill for Claude Code – Less context than playwright-MCP | — | Active | "Significantly fewer lines of instructions" | https://news.ycombinator.com/item?id=45642911 |
| O0000 | Show HN: Ensemble – macOS App to Manage Claude Code Skills, MCPs, and Claude.md | — | Active | macOS UI for skill management | https://news.ycombinator.com/item?id=46922223 |
| (community) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | Active | Early MCP hacking discussion | https://news.ycombinator.com/item?id=43410866 |
| (community) | Anatomy of the .claude/ folder | — | High | Deep-dive on config structure | https://news.ycombinator.com/item?id=47543139 |
| (community) | Claude Code Skills and Plugins as an Open Source Project | — | Active | Open source ecosystem | https://news.ycombinator.com/item?id=47321892 |
| (community) | CLAUDE.md, Skills, Agents, MCP, slash commands | — | Active | "So much more than just prompts" | https://news.ycombinator.com/item?id=46396930 |
| (community) | Claude Code Emergent Behavior: When Skills Combine | — | Active | Emergent capabilities from skill composition | https://news.ycombinator.com/item?id=46531794 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (various) | How I Actually Use Claude Every Day in 2026 | High | — | — | https://www.youtube.com/watch?v=EZcYjH3jAo8 |
| (various) | The Ultimate Claude Code Guide \| MCP, Skills & More | High | — | — | https://www.youtube.com/watch?v=uogzSxOw4LU |
| (various) | The ONLY Claude Code Tutorial You'll Ever Need in 2026 | High | — | — | https://www.youtube.com/watch?v=LlFgLsffbBs |
| (various) | Full Claude Code Tutorial for Non-Technical Beginners in 2026 | High | — | — | https://www.youtube.com/watch?v=bqJzIWAEn40 |
| (various) | Claude Code Tutorial Playlist (MCP, Skills, Subagents) | High | — | — | https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic (official docs) | https://code.claude.com/docs/en/skills | Canonical skills specification and usage |
| Anthropic (official docs) | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Agent Skills API overview |
| Vercel changelog | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | skills.sh launch announcement |
| Vercel docs | https://vercel.com/docs/agent-resources/skills | Official skills documentation |
| vercel-labs/skills (GitHub) | https://github.com/vercel-labs/skills | Open source skills CLI tool |
| vercel-labs/agent-skills (GitHub) | https://github.com/vercel-labs/agent-skills | Official Vercel skill collection |
| Simon Willison | https://simonwillison.net/2025/Dec/19/agent-skills/ | First major community writeup of Agent Skills (Dec 19, 2025) |
| InfoQ | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Vercel skills.sh launch coverage |
| InfoQ | https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ | AWS Agent Registry launch coverage |
| agentskills.io | https://agentskills.io/home | Official spec home |
| paperclipped.de | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | Deep dive on 32-tool adoption |
| tonsofskills.com | https://tonsofskills.com/ | Largest Claude Code skills marketplace |
| tonsofskills (docs) | https://tonsofskills.com/docs/ | Plugin installation documentation |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Skills, MCP Servers & marketplace directory |
| GitHub (jeremylongshore) | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents |
| GitHub (anthropics) | https://github.com/anthropics/claude-plugins-official | Official Anthropic plugin directory |
| GitHub (ComposioHQ) | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| GitHub (alirezarezvani) | https://github.com/alirezarezvani/claude-skills | 245+ skills & agent plugins |
| GitHub (VoltAgent) | https://github.com/VoltAgent/awesome-agent-skills | 1000+ cross-compatible agent skills |
| GitHub (skillmatic-ai) | https://github.com/skillmatic-ai/awesome-agent-skills | Definitive agent skills resource |
| GitHub (rohitg00) | https://github.com/rohitg00/awesome-claude-code-toolkit | Comprehensive Claude Code toolkit |
| GitHub (O0000-code) | https://github.com/O0000-code/Ensemble | Ensemble macOS manager app |
| GitHub (wshobson) | https://github.com/wshobson/agents | Multi-agent orchestration for Claude Code |
| GitHub (shinpr) | https://github.com/shinpr/claude-code-workflows | Production-ready Claude Code workflows |
| GitHub (ruvnet) | https://github.com/ruvnet/claude-flow | Leading agent orchestration platform for Claude |
| GitHub (affaan-m) | https://github.com/affaan-m/everything-claude-code | Agent harness performance optimization |
| GitHub (tylergraydev) | https://github.com/tylergraydev/claude-code-tool-manager | GUI for MCP/skill management |
| GitHub (spring-ai-community) | https://github.com/spring-ai-community/spring-ai-agent-utils | Spring AI agent utils library |
| GitHub (openclaw) | https://github.com/openclaw/clawhub | ClawHub skill directory |
| GitHub (VoltAgent) | https://github.com/VoltAgent/awesome-openclaw-skills | 5,400+ OpenClaw skills curated |
| clawhub.ai | https://clawhub.ai/ | OpenClaw public skill registry |
| Snyk | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | ToxicSkills study (36% flaw rate) |
| Snyk | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Snyk-Vercel security partnership |
| Snyk | https://snyk.io/articles/skill-md-shell-access/ | Threat modeling: SKILL.md to shell access |
| GitHub (snyk-labs) | https://github.com/snyk-labs/toxicskills-goof | ToxicSkills reference examples |
| VentureBeat | https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner | AI agent backdoor via skills |
| obot.ai | https://obot.ai/blog/mcp-security-agent-skills-supply-chain/ | MCP security & agent skills supply chain |
| agensi.io | https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026 | ToxicSkills/ClawHavoc security crisis |
| agensi.io | https://www.agensi.io/learn/agent-skills-open-standard | Open standard explainer |
| agensi.io | https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026 | Marketplace comparison guide |
| AWS (news) | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry launch |
| AWS (blog) | https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/ | AWS ML blog on agent registry |
| AWS (docs) | https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html | AWS Agent Registry documentation |
| AWS (blog) | https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | AWS weekly roundup (April 13, 2026) |
| The Register | https://www.theregister.com/2026/04/09/aws_ai_agent_registry/ | "Agents shouldn't be secret" |
| SiliconANGLE | https://siliconangle.com/2026/04/09/aws-previews-cloud-agnostic-registry-managing-agentic-fleets-scale/ | AWS cloud-agnostic registry coverage |
| Dataconomy | https://dataconomy.com/2026/04/14/aws-launches-agent-registry-to-centralize-ai-agent-governance/ | AWS Agent Registry governance angle |
| TechBriefly | https://techbriefly.com/2026/04/14/aws-launches-agent-registry-to-manage-enterprise-ai-agents/ | Enterprise AI agent management |
| Medium (heeki) | https://heeki.medium.com/integrating-aws-agent-registry-into-your-agent-platform-for-discovery-and-governance-3350920204a4 | Integration guide for AWS registry |
| spring.io | https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/ | Spring AI Agent Skills pattern |
| spring.io | https://spring.io/blog/2026/01/28/apring-ai-anthropic-agentic-skills | Spring AI Anthropic skills support |
| JetBrains | https://blog.jetbrains.com/idea/2026/03/ai-assisted-java-application-development-with-agent-skills/ | IntelliJ + Agent Skills |
| DEV Community | https://dev.to/bsorrentino/skill-based-sub-agents-with-langgraph4j-and-spring-ai-52b0 | LangGraph4j + Spring AI skills |
| earezki.com | https://earezki.com/ai-news/2026-05-04-skill-based-sub-agents-with-langgraph4j-and-spring-ai/ | Skill-based sub-agents (May 4, 2026) |
| DEV Community | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best Claude Code Skills & Plugins guide |
| DEV Community | https://dev.to/muhammad_moeed/claude-code-skills-a-practical-guide-for-2026-3f6p | Practical guide to Claude Code skills |
| OpenAI Developers | https://developers.openai.com/codex/skills | Agent Skills in Codex CLI |
| DigitalOcean | https://www.digitalocean.com/resources/articles/what-are-openclaw-skills | What are OpenClaw Skills? |
| DataCamp | https://www.datacamp.com/blog/best-clawhub-skills | Best ClawHub Skills guide |
| mcpmarket.com | https://mcpmarket.com/ | MCP Market directory |
| mcpbundles.com | https://www.mcpbundles.com/blog/best-mcp-servers | 10,000+ tools, 700+ providers |
| k2view.com | https://www.k2view.com/blog/awesome-mcp-servers | Awesome MCP servers directory |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-mcp-servers-for-developers | Best MCP servers for developers |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code Skills to try |
| skyvia.com | https://skyvia.com/blog/best-mcp-servers/ | Top 12 MCP servers complete guide |
| integrate.io | https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/ | MCP Gateways and AI Agent security tools |
| ByteBridge/Medium | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | Top 10 MCP Gateways in 2026 |
| Microsoft Learn | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Using MCP Tools (Microsoft) |
| toloka.ai | https://toloka.ai/blog/best-mcp-servers-for-ai-agents/ | Best MCP servers for AI agents |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ Best MCP Servers for Claude Code |
| MindStudio | https://www.mindstudio.ai/blog/claude-code-agentic-workflow-patterns | 5 Claude Code Workflow Patterns |
| augmentcode.com | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Claude Agent SDK Skills guide |
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins comparison |
| k21academy.com | https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/ | Skills vs Sub-Agents vs MCP guide |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Claude Code Plugins guide |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-skills-guide/ | Claude Code Skills guide |
| okhlopkov.com | https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/ | Real-world setup after 4 months |
| duet.so | https://duet.so/guides/claude-code-skills-complete-guide | Complete guide: SKILL.md, MCP, Subagents & Teams |
| calmops.com | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI Agent Skills Complete Guide 2026 |
| inference.sh | https://inference.sh/blog/skills/agent-skills-overview | Agent Skills open standard overview |
| agentskillexchange.com | https://agentskillexchange.com/openclaw-vs-claude-code-vs-codex-skill-distribution/ | Skills distribution comparison |
| digitalapplied.com | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | AI Agent Marketplaces 2026 |
| skillsmp.com | https://skillsmp.com/ | Agent Skills Marketplace (Claude, Codex, ChatGPT) |
| agentskills.to | https://www.agentskills.to/vercel-labs/skills/find-skills | Skill browser/discovery |
| thepromptindex.com | https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html | Complete guide: SKILL.md and security |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 Claude Code Skills, Plugins & CLIs |
| self.md | https://self.md/guides/best-claude-code-plugins/ | Best claude code plugins 2026 |
| brightcoding.dev | https://www.blog.brightcoding.dev/2026/02/07/claude-code-plugins-plus-270-ai-agent-tools-that-transform-development | Claude Code Plugins Plus: 270+ AI Agent Tools |
| GitHub (netresearch) | https://github.com/netresearch/claude-code-marketplace | Netresearch curated agent skills |
| GitHub (FlorianBruniaux) | https://github.com/FlorianBruniaux/claude-code-ultimate-guide/blob/main/docs/resource-evaluations/snyk-toxicskills-evaluation.md | ToxicSkills evaluation notes |
| Udemy | https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/ | Claude Code 2026: Subagents, MCP, Skills Bootcamp |
| codewithandrea.com | https://codewithandrea.com/newsletter/january-2026/ | January 2026 newsletter: AI agents, Claude Code |
| developersdigest.tech | https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 | HN developer sentiment analysis |
| developersdigest.tech | https://www.developersdigest.tech/blog/best-claude-code-skills-2026 | Best Claude Code Skills directory |
| Polymarket | https://polymarket.com/predictions/claude | Claude prediction markets |
| Polymarket | https://polymarket.com/predictions/ai | AI prediction markets |
| conare.ai | https://conare.ai/marketplace/mcp/polymarket-mcp | Polymarket MCP Server |
| conare.ai | https://conare.ai/marketplace/mcp/graph-polymarket | Graph Polymarket MCP |
| GitHub (caiovicentino) | https://github.com/caiovicentino/polymarket-mcp-server | Polymarket MCP Server (45 tools) |
| sparkco.ai | https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi | Prediction market agents via MCP |
| MCPMarket (Watch YouTube) | https://mcpmarket.com/tools/skills/watch-youtube | YouTube Claude Code Skill |
| Composio | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP Integration with Claude Code |
| aitooldiscovery.com | https://www.aitooldiscovery.com/guides/claude-code-reddit | Claude Code Reddit usage guide |
| aicerts.ai | https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/ | Snyk audit findings |
| cyberdesserts.com | https://blog.cyberdesserts.com/ai-agent-security-risks/ | AI Agent Security Risks 2026 |
| articsledge.com | https://www.articsledge.com/post/agent-skills | What Are Agent Skills? Complete 2026 Guide |
| agensi.io (config guide) | https://www.agensi.io/learn/ai-agent-configuration-guide-2026 | AI Agent Configuration Guide 2026 |
| Medium (rentierdigital) | https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840 | 25 Claude Code YouTube videos ranked |
| databar.ai | https://databar.ai/blog/article/best-mcp-servers-for-sales-teams-in-2026 | Best MCP Servers for Sales Teams |
| Tencent Cloud | https://www.tencentcloud.com/techpedia/140807 | OpenClaw Application Marketplace |
| lobehub.com | https://lobehub.com/skills/openclaw-skills-openclaws | OpenClaw skills on LobeHub |
| aimakers.co | https://www.aimakers.co/blog/openclaw-skills-guide/ | Best OpenClaw Skills guide |
| skywork.ai | https://skywork.ai/skypage/en/clawhub-openclaw-skills-marketplace/2036713669543198720 | ClawHub marketplace guide |
| sparkco.ai | https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi | AI Agents for Prediction Markets |
| Augment Code | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Claude Agent SDK Skills |
| dev.to (jan_lucasandmann) | https://dev.to/jan_lucasandmann_bb9257c/claude-code-to-ai-os-blueprint-skills-hooks-agents-mcp-setup-in-2026-46gg | Claude Code to AI OS Blueprint |
| amontalenti.com | https://amontalenti.com/2026/02/15/a-weird-year | It's official: 2026 is a weird year for tech |

---

## Stats Block

```
├─ 🟠 Reddit: blocked during research
├─ 🔵 X/Twitter: blocked during research
├─ 🔴 YouTube: 5 videos identified | very high views
├─ 🟢 HN: 10 threads | multiple high-engagement discussions
├─ 🟣 TikTok: no data returned
├─ 🩷 Instagram: no data returned
├─ 🦋 Bluesky: no data returned
├─ 📊 Polymarket: 2 markets | active (Claude predictions page + AI page) | plus Polymarket MCP server
├─ 🌐 Web: 100+ pages | broad coverage across official docs, GitHub, security research, enterprise news
└─ 🗣️ Top voices: Simon Willison (simonwillison.net), Jeremy Longshore (tonsofskills.com), @snyk-labs, @vercel-labs | GitHub: alirezarezvani, VoltAgent, skillmatic-ai, rohitg00
```

---

## Data Gaps

1. **Reddit blocked**: Could not access reddit.com directly. Community discussion on r/ClaudeAI, r/LocalLLaMA, r/programming likely contains rich practitioner sentiment.
2. **X/Twitter blocked**: Direct X/Twitter posts not accessible. Community reactions from @AnthropicAI, developer tweets about skills/MCP use cases not captured.
3. **TikTok**: No TikTok data returned. Some developer tutorial content likely exists.
4. **Bluesky**: No direct Bluesky data. Developer community on Bluesky (many ex-Twitter devs) likely has relevant discussions.
5. **Engagement metrics**: Most HN stories returned without specific point/comment counts (would require fetching individual pages). YouTube view counts not captured from search results alone.
6. **GitHub issue/PR discussions**: The real-time developer discourse happening in GitHub issues for skills repos (vercel-labs/skills, anthropics/claude-plugins-official) not deeply captured.
7. **Approximate coverage**: ~65% of the ecosystem breadth captured. Strong coverage of: open standard, security, enterprise registries, community marketplaces, key tooling. Weaker coverage: individual practitioner workflows, specific skill quality comparisons, international community (non-English).

---

## Key Quotes

> "Within 48 hours [of Vercel launching skills.sh], Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI. By March 2026, 32 tools from competing companies all read the same SKILL.md files." — [paperclipped.de](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/)

> "Agents shouldn't be secret, so we built a registry." — AWS, via The Register ([link](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/))

> "From SKILL.md to Shell Access in Three Lines of Markdown." — Snyk, threat modeling article ([link](https://snyk.io/articles/skill-md-shell-access/))

> "Skills are how you stop copy-pasting the same workflow into Claude Code every session. A skill is a small folder of markdown and helper scripts that Claude Code loads on demand." — Developers Digest, [developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

> "The winning pattern in 2026 is a control stack: project rules, reusable skills, bounded sub-agents, and deterministic tools around the model." — Developers Digest ([link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026))

> "Discovery is the real bottleneck: shipping the agent is solved; getting it surfaced in a marketplace with thousands of competing listings is where most agency-built agents fail to gain traction." — digitalapplied.com ([link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution))

> "Snyk scanned 3,984 skills from ClawHub and skills.sh and found 1,467 malicious payloads — a 36% flaw rate, with 76 confirmed malicious skills with active payloads." — Snyk ToxicSkills study ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "One command turns any open-source repo into an AI agent backdoor. OpenClaw proved no supply-chain scanner has a detection category for it." — VentureBeat ([link](https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner))

> "Skills are portable: build once, use across agents. Most skills that stick to the core format (SKILL.md with standard frontmatter and markdown instructions) work everywhere without modification." — Agent Skills Open Standard Explainer ([link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/))

> "The ecosystem has gone from empty to flooded in about six months, with a lot of noise." — Developer community sentiment, via Developers Digest ([link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026))
