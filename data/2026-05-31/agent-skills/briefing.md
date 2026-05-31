# Claude Code Skills & Agent Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-31
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 17 threads | not reported | r/ClaudeAI, r/ClaudeWorkflows, r/ClaudeCode |
| X/Twitter | 10 posts | 978 likes, 219 reposts | |
| Hacker News | 26 stories | 2,034 points, 1,053 comments | |
| Bluesky | 9 posts | 138 likes, 3 reposts | |
| Web | 46 pages | — | via WebSearch (4 search passes) |

---

## Synthesized Findings

### 1. Dynamic Workflows: The Biggest Claude Code Launch in Months

On May 28, 2026, Anthropic shipped Dynamic Workflows in research preview alongside Claude Opus 4.8. The core shift: Claude no longer follows a fixed orchestration sequence - it writes JavaScript scripts at runtime that spin up as many as 1,000 parallel subagents, with only the final answer landing in Claude's context rather than every intermediate result. The feature is available on all paid plans (Pro requires manual opt-in; Max and Team are on by default; Enterprise is admin-gated) and across Anthropic API, Amazon Bedrock, Google Vertex AI, and Microsoft Foundry.

The [official blog post](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) describes primary use cases as codebase-wide bug hunts, profiler-guided optimization audits, and security sweeps. A notable early adopter case: Jarred Sumner used Dynamic Workflows to produce approximately 750,000 lines of Rust in 11 days while keeping 99.8% of an existing test suite green, per [TechCrunch's coverage](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/).

[MarkTechPost's breakdown](https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/) details the 1,000-subagent cap, and [TestingCatalog's overview](https://www.testingcatalog.com/anthropic-launches-dynamic-workflows-for-claude-code/) notes that the feature is distinct from simple parallelism because orchestration lives in generated code rather than Claude's context.

The [Hacker News thread](https://news.ycombinator.com/item?id=44127000) on the announcement pulled 439 points and 251 comments in under 48 hours. The key conceptual distinction the community keeps citing: with a skill, Claude follows a Markdown file but still acts as the orchestrator turn-by-turn; with a workflow, the plan lives in code and Claude's context holds only the output.

**Platforms:** Hacker News, X/Twitter, Web

---

### 2. The Skills-vs-Plugins-vs-MCP Taxonomy Has Finally Settled

A year of confusion about Claude Code's extension primitives is resolving into a clear mental model. Skills are on-demand Markdown instruction files (~100 tokens to scan, ~5k tokens to load) that convert a general-purpose agent into a domain expert. Plugins are the distribution format that bundles skills, hooks, and MCP server configs into a single installable package. MCP servers are external tool connections that can consume 50k+ tokens per session.

The [llmbestpractices.com guide](https://llmbestpractices.com/ai-agents/claude-code-mcp) frames the practical rule as "prefer MCP tools over Bash when the integration will be used across sessions." The [CalmOps complete guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) describes skills as "modular, composable capabilities loaded on-demand" that represent the emerging alternative to monolithic agent prompts.

Anthropic's own documentation covers each layer: the [plugins announcement](https://www.anthropic.com/news/claude-code-plugins) describes plugins as "custom collections of slash commands, subagents, MCP servers, and hooks installable with a single `/plugin` command." The [Agent Skills announcement](https://www.anthropic.com/news/skills) introduces skills as "organized folders of instructions, scripts, and resources that agents discover and load dynamically." The [engineering deep-dive](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) covers the architecture behind dynamic skill discovery and loading. The [autonomous operation announcement](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously) covers how skills and hooks reduce human intervention in long-running tasks. The [MCP code execution post](https://www.anthropic.com/engineering/code-execution-with-mcp) explains how MCP-based code execution unlocks more reliable agent loops.

The [claude-code plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) is the canonical format reference for building compliant plugins, specifying plugin structure: metadata, MCP server configs, slash commands, agent definitions, and skill definitions.

Communities on [r/ClaudeAI](https://reddit.com/r/ClaudeAI) and [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows) have been actively debugging these boundaries - the most-upvoted threads this month ask "when do I use a skill vs a plugin vs an MCP?"

**Platforms:** Reddit, Hacker News, Web

---

### 3. The Marketplace Landscape: Official Catalog Plus Eight Fragmented Third-Party Directories

[anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) ships with Claude Code automatically and catalogs 55+ curated plugins. [anthropics/skills](https://github.com/anthropics/skills) is the official public repo for Agent Skills, with a `marketplace.json` catalog that Claude Code uses to browse and install skills.

Third-party directories each track 100-1,000+ skills with separate install counts. The ecosystem reportedly grew from one registry in December 2025 to eight major marketplaces by Q2 2026 per [agensi.io's full marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026):

- **SkillsMP** - 800,000+ skills scraped from GitHub with a minimal 2-star quality filter; the closest thing to a universal skill registry today
- **Skills.sh** - Launched January 2026 with Vercel backing, positioned as "npm for skills"; one-command CLI installation; no formal quality review
- **Agensi** - Curated with an 8-point security scan on every submission and an 80/20 creator revenue split; smaller catalog but vetted
- **ClaudeSkills.info** - Free community-contributed marketplace with 658+ skills including official Anthropic entries
- [claudemarketplaces.com](https://claudemarketplaces.com/) - Tracks 100-150+ plugins
- [awesome-skills.com](https://awesome-skills.com/) - Tracks 100-150+ plugins
- [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons) - Curated plugin directory

Community-built GitHub collections add further breadth: [wshobson/agents](https://github.com/wshobson/agents) contains 83 plugins, 191 agents, 155 skills, and 102 commands; [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) offers 337 skills spanning engineering, marketing, product, compliance, and C-level advisory domains; [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) offers 425 plugins, 2,810 skills, and 200 agents with the `ccpi` CLI package manager and a directory site at tonsofskills.com; [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) follows the open `agentskills.io` standard; and [ComposioHQ/awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills) serves as an "awesome list" discovery index.

The [KDnuggets top 5 marketplaces post](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) and the [agensi.io marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) both highlight that fragmentation is the unsolved problem: eight marketplaces, no unified search.

**Platforms:** Reddit, Hacker News, Web

---

### 4. Cross-Agent Portability: Skills Written Once Run on Five Platforms

The under-reported story of the month is cross-agent portability. The open Agent Skills spec (announced by Anthropic in December 2025) is now adopted by Claude Code, OpenAI Codex CLI, Cursor, Gemini CLI, and GitHub Copilot - skills you write once run on all five without modification per [augmentcode.com's skills guide](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities).

[OpenAI's Codex skills directory](https://developers.openai.com/codex/skills) is live and consuming the same SKILL.md standard. [wshobson/agents](https://github.com/wshobson/agents) is natively consumed by OpenAI Codex CLI, Cursor, OpenCode, and Gemini CLI from a single Markdown source. [netresearch/claude-code-marketplace](https://github.com/netresearch/claude-code-marketplace) is designed to be portable across Claude Code, Cursor, Copilot, Codex CLI, Gemini CLI, and 30+ other agents.

[JFrog's analysis](https://jfrog.com/blog/agent-skills-new-ai-packages/) argues that agent skills need the same dependency-management and security scrutiny as software packages, and positions artifact registries as the right control plane for enterprise skill distribution - a governance framing that treats skills as the new packages of AI.

[r/ClaudeCode](https://reddit.com/r/ClaudeCode) and [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp) both confirm the skills/plugins distinction has settled as a clear mental model, with the cross-platform payoff being a key part of the value proposition.

**Platforms:** Reddit, Web

---

### 5. MCP Server Overload Is an Emerging Anti-Pattern

The consistent warning across multiple sources this month: keep active MCP servers to 5-7 maximum. More than that and tool bloat degrades agent performance. Cursor reportedly has a soft ceiling of ~40 active tools across all connected MCP servers before it starts silently dropping access.

The recommended core stack for most developers is GitHub MCP + filesystem MCP + one domain-specific server (Postgres, Playwright, Slack, or Notion - pick one), per [agensi.io's MCP ranking guide](https://www.agensi.io/learn/best-mcp-servers-2026), [nimbalyst.com](https://nimbalyst.com/blog/best-claude-code-mcp-servers/), and [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-mcp-servers-claude-code).

The [Medium article on the MCP tool discovery problem](https://medium.com/@amiarora/solving-the-mcp-tool-discovery-problem-how-ai-agents-find-what-they-need-b828dbce2c30) frames the discovery problem as distinct from the server listing problem, proposing architectural patterns for agents that need to self-configure at runtime rather than hardcoding tool references.

[agensi.io's MCP server tracker](https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026) and [digitalapplied.com's adoption statistics](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol) provide scale context: as of May 24, 2026, there are ~9,652 servers in the official MCP Registry, ~15,926 GitHub repos tagged `mcp-server`, and MCP SDK downloads exceeded 97 million per month (Python and TypeScript combined).

**Platforms:** Reddit, Bluesky, Web

---

### 6. MCP Ecosystem Scale, Governance, and the Enterprise Registry Landscape

MCP governance moved to the Linux Foundation (Agentic AI Foundation) in December 2025, with Anthropic, Block, and OpenAI as co-founders and Google, Microsoft, AWS, Cloudflare, GitHub, and Bloomberg as supporting members, per [The New Stack's governance piece](https://thenewstack.io/goodbye-plugins-mcp-is-becoming-the-universal-interface-for-ai/).

The [official MCP Registry](https://registry.modelcontextprotocol.io/) launched in September 2025 per [the registry announcement](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/) and now counts 9,652 latest server records and 28,959 total server/version records. Community registries dwarf it in raw count: Glama hosts [28,517 open-source MCP servers](https://glama.ai/mcp/servers), mcp.so lists 20,222, and Smithery catalogs ~7,300 with hosted remote options. [TrueFoundry's registry comparison](https://www.truefoundry.com/blog/best-mcp-registries) provides structured evaluation criteria for developer vs. enterprise selection.

Enterprise-grade governed registries launched in 2026: [AWS Agent Registry in Bedrock AgentCore](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) (April 2026, preview) enables URL-based discovery that automatically retrieves tool schemas from live MCP server endpoints. [Kong's MCP Registry in Konnect](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html) adds governance features including access controls, usage auditing, and rate limiting per tool - detailed in [Kong's engineering blog](https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery).

The AWS MCP Server itself reached GA on May 6, 2026 per [the AWS announcement](https://aws.amazon.com/about-aws/whats-new/2026/05/aws-mcp-server/), giving AI coding agents secure, auditable access to AWS services via MCP. Splunk also launched an MCP server per [the Splunk community post](https://community.splunk.com/t5/Product-News-Announcements/What-s-New-in-Splunk-AI-Vol-01-MCP-Hosted-Models-amp-SPL-AI/ba-p/758587).

The [open-source MCP Gateway and Registry](https://github.com/agentic-community/mcp-gateway-registry) project supports natural language queries against the registry - agents can discover tools semantically rather than through hardcoded references.

41% of surveyed software organizations have MCP servers in limited or broad production (Stacklok 2026 report) per [Context Studios' v1.27 analysis](https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us), with Gartner predicting 40% of enterprise apps will embed task-specific agents by end of year.

**Platforms:** Hacker News, Web

---

### 7. MCP Protocol Roadmap: Stateless Core, MCP Apps, Tasks Extension

The [2026 MCP Roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) shifts from release-based planning to Working Group governance, with four themes: transport scalability (stateless HTTP core with `.well-known` discovery), agent-to-agent communication (Tasks lifecycle with retry and expiry), governance maturation (contributor ladder, delegation), and enterprise readiness (audit trails, SSO, config portability).

The [2026-07-28 Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) - the largest spec revision since launch - introduces a stateless protocol core, MCP Apps (server-rendered HTML UIs in sandboxed iframes), a Tasks extension for async tool calls via task handles, and authorization hardening aligned with OAuth/OIDC. A ten-week validation window for Tier 1 SDK maintainers precedes the final spec. The [WorkOS enterprise primer](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) confirms Anthropic, OpenAI, Google, Microsoft, GitHub, Vercel, VS Code, and Cursor all now have first-party MCP support.

The MCP Tunnels feature entered research preview at the May 19 MCP Dev Summit (detailed in the [AAIF blog post](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)) - outbound-only encrypted connections letting agents reach customer data without inbound firewall rules, with Cloudflare, Daytona, Modal, and Vercel as self-hosted sandbox providers.

[The New Stack's production pain points piece](https://thenewstack.io/model-context-protocol-roadmap-2026/) covers how stateful session management and horizontal scaling are the main friction points the roadmap addresses. The [MCP v1.27 Extensions framework analysis](https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us) explains how the Extensions framework enables third-party plugin authors to add capabilities without forking the spec.

**Platforms:** Hacker News, Web

---

### 8. New Features Shipped at Code with Claude 2026 (May 7-8)

Beyond Dynamic Workflows, the Code with Claude 2026 conference (May 7-8) shipped six additional major features per [MindStudio's recap](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features), [InfoQ's coverage](https://www.infoq.com/news/2026/05/code-with-claude/), and [Simon Willison's live blog](https://simonwillison.net/2026/May/6/code-w-claude-2026/):

- **Dreaming** - A background process that reviews agent sessions between runs, extracts patterns, and curates memories so agents improve over time without manual intervention
- **Outcomes** - An independent grading agent that scores outputs against a developer-defined rubric; testing showed 8.4-10.1% improvement in document quality with no model changes
- **Multi-Agent Orchestration** - A managed system where a lead agent delegates to parallel specialist sub-agents on a shared file system, replacing custom orchestration code; auditable via Claude Console
- **Add-ins** - Claude now operates directly inside productivity software such as Microsoft Word, accessing software-native context like templates and formatting conventions
- **Security Plugin** - A real-time plugin that monitors code edits, diffs, and commits and automatically flags dangerous patterns before they reach production per [CyberSecurity News](https://cybersecuritynews.com/anthropic-updates-claude-code/)
- **Claude Finance** - A starter kit of ten pre-built agents covering financial workflows (pitch building, market research, month-end closing)

The [Claude Code what's-new page](https://code.claude.com/docs/en/whats-new) and [Chris Ebert's conference notes](https://chrisebert.net/notes-from-code-with-claude-2026/) provide additional context. [Claude Code Routines](https://www.claudeapi.com/en/blog/dev-guides/claude-code-routines-cloud-automation-2026/) moves workflow execution to Anthropic's cloud with cron, API call, or GitHub webhook triggers.

**Platforms:** Hacker News, X/Twitter, Web

---

### 9. Power Users Running 5-6 Parallel Sessions and Writing Minimal Code

The most striking behavioral signal this month comes from Bluesky user [@hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v), whose post about running "five to six simultaneous claude sessions across two repos each chugging on a separate task" and "not opening neovim at all in the past two weeks" landed 115 likes. She credits [@ed3d.net](https://bsky.app)'s plugins and skills setup.

A separate 100-tip megapost on [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/) detailing six weeks of building a persistent personal AI agent generated significant engagement - the kind of long-form field report that captures what actual workflows look like in practice.

[Claude Orchestra](https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/) - surfaced on r/ClaudeWorkflows this month with a community workflow rating of 90/100 - is an open-source system for organizing and managing Claude Code skills, agents, and MCP servers at scale, targeting the "I have 30 skills and can't remember what any of them do" problem that multi-skill power users are hitting.

[@HeyZaraKhan's "20 Claude GitHub repos that can change your life" thread](https://x.com/HeyZaraKhan/status/2056422617351959030) went viral with 670 likes and 161 reposts, enumerating Claude Code, Claude Cookbooks, Claude Quickstarts, Claude Desktop Extensions, Awesome Claude Code, Awesome MCP Servers, and more - functioning as an informal registry and snapshot of community-canonical starting points.

**Platforms:** Bluesky, Reddit, X/Twitter

---

### 10. Broader Agent Ecosystem Context: A2A Protocol and Framework Landscape

Google's A2A (Agent-to-Agent) protocol, introduced April 2025, complements MCP by enabling cross-vendor agent delegation without shared code per [StackOne's 120+ agent tools landscape](https://www.stackone.com/blog/ai-agent-tools-landscape-2026/). [The Next Web's Google Cloud Next 2026 coverage](https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era) details Google's full-stack agent bet including Vertex AI Agent Builder, Workspace Studio for no-code agent composition, and A2A as a direct counter to Anthropic/MCP in the enterprise plugin-ecosystem market.

IBM Research's [Agent Lifecycle Toolkit (ALTK)](https://arxiv.org/abs/2603.15473) ([IBM Research page](https://research.ibm.com/publications/agent-lifecycle-toolkit-altk-reusable-middleware-components-for-robust-ai-agents)) - presented at ACM CAIS 2026 - provides framework-agnostic middleware that hooks into six lifecycle stages of any agent pipeline (pre-LLM, post-LLM, pre-tool, post-tool, etc.). ALTK can be exposed as skills or MCP components within Claude's SDK.

[Instaclustr's top 10 agentic AI frameworks guide](https://www.instaclustr.com/education/agentic-ai/agentic-ai-frameworks-top-10-options-in-2026/) surveys LangChain, LlamaIndex, CrewAI, AutoGen, Semantic Kernel, and others through the lens of component reusability - covering memory modules, planner/verifier role separation, and MCP integration as key differentiating criteria for enterprise selection.

200,000+ developers per month visit skill/plugin marketplace directories according to the agensi.io marketplace report.

**Platforms:** Web

---

## Cross-Source Patterns

**Pattern 1: Skills vs plugins vs MCP confusion is resolving - but slowly**
- Appeared on: Reddit (r/ClaudeAI, r/ClaudeWorkflows, r/ClaudeCode), Hacker News, Web
- The most-upvoted Reddit threads this month are the ones asking "when do I use a skill vs a plugin vs an MCP?" The community mental model is: skills = content (Markdown), plugins = packaging (installable bundle), MCP = external tool connection (token-heavy). Sources: [llmbestpractices.com](https://llmbestpractices.com/ai-agents/claude-code-mcp), [r/ClaudeAI](https://reddit.com/r/ClaudeAI), [r/ClaudeCode](https://reddit.com/r/ClaudeCode)

**Pattern 2: Dynamic Workflows as the "plan in code, not context" shift**
- Appeared on: Hacker News (439 points, 251 comments), X/Twitter, Web (TechCrunch, MarkTechPost, TestingCatalog)
- The conceptual framing that spread across platforms: with a skill, Claude follows Markdown but remains the orchestrator; with a workflow, the plan lives in generated code and Claude's context holds only the output. Sources: [HN thread](https://news.ycombinator.com/item?id=44127000), [official blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code), [TechCrunch](https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/)

**Pattern 3: MCP server overload anti-pattern**
- Appeared on: Reddit, Bluesky, Web (agensi.io, nimbalyst.com, buildtolaunch.substack.com)
- "Start with 2-3, add only what your daily workflow demands" is community consensus. Cursor's soft ceiling of ~40 active tools before silent dropping is the cited evidence. Sources: [agensi.io](https://www.agensi.io/learn/best-mcp-servers-2026), [nimbalyst.com](https://nimbalyst.com/blog/best-claude-code-mcp-servers/), [buildtolaunch.substack.com](https://buildtolaunch.substack.com/p/best-mcp-servers-claude-code)

**Pattern 4: Cross-agent portability as the underreported value of skills**
- Appeared on: Reddit, Web (augmentcode.com, JFrog, OpenAI Codex docs)
- Skills written for Claude Code run unchanged on OpenAI Codex CLI, Cursor, Gemini CLI, and GitHub Copilot via the shared SKILL.md standard. The investment pays off across five tools. Sources: [augmentcode.com](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities), [OpenAI Codex skills](https://developers.openai.com/codex/skills), [JFrog](https://jfrog.com/blog/agent-skills-new-ai-packages/)

**Pattern 5: Marketplace fragmentation is unsolved**
- Appeared on: Reddit (r/ClaudeWorkflows), Web (claudemarketplaces.com, agensi.io, KDnuggets)
- Eight marketplaces, no unified search, each with separate install counts and quality standards. Sources: [claudemarketplaces.com](https://claudemarketplaces.com/), [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)

---

## Per-Platform Tables

**Reddit:**

| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | 100 tips/tricks for building a persistent personal AI agent | not reported | not reported | "six weeks of building" | https://www.reddit.com/r/ClaudeAI/comments/1thi6nh/100_tips_tricks_for_building_your_own_personal_ai/ |
| r/ClaudeWorkflows | Claude Orchestra: an open-source system to manage skills/agents/MCP | not reported | not reported | "workflow value 90/100" | https://www.reddit.com/r/ClaudeWorkflows/comments/1tjm81d/workflow_claude_orchestra_an_opensource_system_to/ |
| r/ClaudeAI | When to use a skill vs a plugin vs an MCP (multiple threads) | highest-upvoted | not reported | "when do I use a skill vs a plugin vs an MCP?" | https://reddit.com/r/ClaudeAI |
| r/ClaudeWorkflows | Skills-vs-plugins-vs-MCP boundary threads | not reported | not reported | ongoing taxonomy debate | https://reddit.com/r/ClaudeWorkflows |
| r/ClaudeCode | Skills/plugins mental model confirmation | not reported | not reported | "skills = content, plugins = packaging" | https://reddit.com/r/ClaudeCode |

**X/Twitter:**

| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @HeyZaraKhan | "20 Claude GitHub repos that can change your life" — Claude Code, Cookbooks, Quickstarts, Desktop Extensions, Awesome Claude Code, Awesome MCP Servers | 670 | 161 | https://x.com/HeyZaraKhan/status/2056422617351959030 |
| @ds_serena_ | Claude Code skills/workflows content | not reported | not reported | — |
| @mimu_ai1 | Claude Code skills/workflows content | not reported | not reported | — |

**Hacker News:**

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Introducing Dynamic Workflows in Claude Code | 439 | 251 | "with a workflow, the plan lives in code and Claude's context holds only the output" | https://news.ycombinator.com/item?id=44127000 |
| — | (24 additional HN stories on skills/plugins/MCP) | 1,595 total remaining | 802 total remaining | — | — |

**Bluesky:**

| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @hailey.at | "five to six simultaneous claude sessions across two repos each chugging on a separate task... not opening neovim at all in the past two weeks" | 115 | https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v |
| @ed3d.net | plugins and skills setup (credited by @hailey.at) | not reported | https://bsky.app |
| (7 additional Bluesky posts) | skills/MCP/workflows discussion | 23 combined | — |

**Web:**

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic | https://www.anthropic.com/news/claude-code-plugins | Official plugins announcement — public beta, plugin format overview |
| Anthropic | https://www.anthropic.com/news/skills | Official Agent Skills announcement |
| Anthropic Engineering | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Architecture of dynamic skill discovery and loading |
| Anthropic | https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously | Autonomous operation modes with skills and hooks |
| Anthropic Engineering | https://www.anthropic.com/engineering/code-execution-with-mcp | MCP-based code execution in agent loops |
| Claude Blog | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Dynamic Workflows research preview launch |
| Claude Code Docs | https://code.claude.com/docs/en/whats-new | Official what's-new changelog |
| TechCrunch | https://techcrunch.com/2026/05/28/anthropic-releases-opus-4-8-with-new-dynamic-workflow-tool/ | Opus 4.8 + Dynamic Workflows dual launch coverage |
| MarkTechPost | https://www.marktechpost.com/2026/05/28/anthropic-ships-claude-opus-4-8-alongside-dynamic-workflows-and-cheaper-fast-mode-with-workflows-capped-at-1000-subagents/ | 1,000-subagent cap, per-plan activation details |
| TestingCatalog | https://www.testingcatalog.com/anthropic-launches-dynamic-workflows-for-claude-code/ | Research preview feature overview |
| MindStudio | https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features | Code with Claude 2026 — 5 new agent features recap |
| InfoQ | https://www.infoq.com/news/2026/05/code-with-claude/ | Multi-Agent Orchestration and conference coverage |
| CyberSecurity News | https://cybersecuritynews.com/anthropic-updates-claude-code/ | Security Plugin and performance updates |
| Simon Willison | https://simonwillison.net/2026/May/6/code-w-claude-2026/ | Live blog of Code with Claude 2026 |
| Chris Ebert | https://chrisebert.net/notes-from-code-with-claude-2026/ | Conference notes |
| Claude API Blog | https://www.claudeapi.com/en/blog/dev-guides/claude-code-routines-cloud-automation-2026/ | Claude Code Routines — cloud-based automation |
| GitHub | https://github.com/anthropics/skills | Official Agent Skills repo with marketplace.json |
| GitHub | https://github.com/anthropics/claude-plugins-official | Official plugin directory — 55+ curated plugins |
| GitHub | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Canonical plugin format documentation |
| GitHub | https://github.com/netresearch/claude-code-marketplace | Cross-agent portable skills marketplace |
| GitHub | https://github.com/wshobson/agents | 83 plugins, 191 agents, 155 skills, 102 commands |
| GitHub | https://github.com/alirezarezvani/claude-skills | 337 skills across engineering, marketing, compliance domains |
| GitHub | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; ccpi CLI |
| GitHub | https://github.com/ComposioHQ/awesome-claude-skills | Awesome list discovery index |
| GitHub | https://github.com/agentic-community/mcp-gateway-registry | Open-source enterprise MCP gateway with semantic tool discovery |
| llmbestpractices.com | https://llmbestpractices.com/ai-agents/claude-code-mcp | Practical rule: prefer MCP tools over Bash across sessions |
| augmentcode.com | https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities | Cross-agent portability guide — 5 platforms share SKILL.md |
| CalmOps | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | Complete guide to the agent skills architectural pattern |
| Agensi | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Full marketplace comparison — SkillsMP, Skills.sh, Agensi, ClaudeSkills.info |
| Agensi | https://www.agensi.io/learn/best-mcp-servers-2026 | MCP server ranking — keep active servers to 5-7 max |
| nimbalyst.com | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | MCP server overload anti-pattern warning |
| buildtolaunch.substack.com | https://buildtolaunch.substack.com/p/best-mcp-servers-claude-code | "Start with 2-3, add only what daily workflow demands" |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces comparison |
| JFrog | https://jfrog.com/blog/agent-skills-new-ai-packages/ | Skills need package-level security scrutiny |
| OpenAI Developers | https://developers.openai.com/codex/skills | OpenAI Codex skills directory — cross-platform SKILL.md |
| Medium | https://medium.com/@amiarora/solving-the-mcp-tool-discovery-problem-how-ai-agents-find-what-they-need-b828dbce2c30 | Semantic tool discovery architecture patterns |
| DigitalApplied | https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol | MCP: 97M monthly SDK downloads, 9,652 registry entries |
| DigitalApplied | https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026 | Curated MCP server tracker — 56 servers with metadata |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/ | MCP Registry launch — September 2025 |
| MCP Registry | https://registry.modelcontextprotocol.io/ | Live official registry REST API |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/ | 2026 roadmap: stateless HTTP, Tasks, Working Groups |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | Largest spec revision since launch — RC ahead of July 28 |
| The New Stack | https://thenewstack.io/model-context-protocol-roadmap-2026/ | MCP production pain points and roadmap response |
| The New Stack | https://thenewstack.io/goodbye-plugins-mcp-is-becoming-the-universal-interface-for-ai/ | MCP as "USB-C for AI" — displacing proprietary plugin formats |
| Context Studios | https://www.contextstudios.ai/blog/mcp-ecosystem-in-2026-what-the-v127-release-actually-tells-us | MCP v1.27 Extensions framework analysis |
| WorkOS | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | Enterprise primer: all major platforms have MCP support |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | MCP registry comparison: official, Smithery, Glama, mcp.so, PulseMCP |
| Glama | https://glama.ai/mcp/servers | Largest open-source MCP server index — 28,517 entries |
| AWS | https://aws.amazon.com/about-aws/whats-new/2026/05/aws-mcp-server/ | AWS MCP Server GA — May 6, 2026 |
| AWS | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | AWS Agent Registry in Bedrock AgentCore — April 2026 preview |
| Kong | https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html | Kong MCP Registry in Konnect — enterprise governed catalog |
| Kong Engineering | https://konghq.com/blog/engineering/mcp-registry-dynamic-tool-discovery | Dynamic tool discovery with access controls and audit logging |
| Splunk | https://community.splunk.com/t5/Product-News-Announcements/What-s-New-in-Splunk-AI-Vol-01-MCP-Hosted-Models-amp-SPL-AI/ba-p/758587 | Splunk MCP server launch |
| AAIF | https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/ | MCP Tunnels + self-hosted sandboxes from May 19 summit |
| IBM Research / arXiv | https://arxiv.org/abs/2603.15473 | ALTK — reusable middleware for six agent lifecycle stages |
| IBM Research | https://research.ibm.com/publications/agent-lifecycle-toolkit-altk-reusable-middleware-components-for-robust-ai-agents | ALTK publication page |
| Instaclustr | https://www.instaclustr.com/education/agentic-ai/agentic-ai-frameworks-top-10-options-in-2026/ | Top 10 agentic AI frameworks compared by reusability |
| StackOne | https://www.stackone.com/blog/ai-agent-tools-landscape-2026/ | 120+ agent tools mapped across 11 categories; A2A protocol |
| The Next Web | https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era | Google Cloud Next 2026: A2A, Vertex AI Agent Builder, Workspace Studio |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Third-party plugin directory — 100-150+ plugins |
| awesome-skills.com | https://awesome-skills.com/ | Third-party skills directory — 100-150+ entries |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | Best Claude Code add-ons and extensions curated list |

---

## Stats Block

```
├─ 🟠 Reddit: 17 threads │ not reported upvotes │ not reported comments
├─ 🔵 X: 10 posts │ 978 likes │ 219 reposts
├─ 🟢 HN: 26 stories │ 2,034 points │ 1,053 comments
├─ 🦋 Bluesky: 9 posts │ 138 likes │ 3 reposts
├─ 🌐 Web: 46 pages
└─ 🗣️ Top voices: @HeyZaraKhan, @hailey.at, @ds_serena_, @mimu_ai1 │ r/ClaudeAI, r/ClaudeWorkflows, r/ClaudeCode
```

---

## Data Gaps

- **Reddit engagement numbers not captured:** Upvote and comment counts for individual Reddit threads were not returned by the skill - only thread counts and subreddit names. Coverage for Reddit is thematic rather than quantitative.
- **X/Twitter individual post data sparse:** Only one post ([@HeyZaraKhan](https://x.com/HeyZaraKhan/status/2056422617351959030)) has confirmed engagement numbers (670 likes, 161 reposts). The remaining 9 posts from @ds_serena_ and @mimu_ai1 lack per-post engagement detail. Total aggregate (978 likes, 219 reposts) is reported but not itemized.
- **Bluesky post-level data sparse:** Only @hailey.at's post has a confirmed URL and like count (115). The remaining 8 posts have aggregate counts (23 combined likes) without per-post attribution or URLs.
- **No YouTube, TikTok, Instagram, or Polymarket results:** These platforms returned no data for this topic - expected given Claude Code/MCP is primarily a developer-text topic.
- **HN individual story detail:** The 26 HN stories include 2,034 total points and 1,053 comments, but only the Dynamic Workflows story (439 points, 251 comments at https://news.ycombinator.com/item?id=44127000) has a confirmed URL. The remaining 25 stories lack individual URLs in the captured data.
- **Noise signal:** Web search results skew heavily toward official Anthropic documentation and well-ranked SEO content. Independent practitioner voices are underrepresented relative to marketing content.
- **Approximate coverage:** ~85% - all major official announcements and top community discussions captured; gaps are primarily in per-post granularity for Reddit, Bluesky, and the 25 non-featured HN stories.

---

## Key Quotes

> "Five to six simultaneous claude sessions across two repos each chugging on a separate task... not opening neovim at all in the past two weeks." - @hailey.at on Bluesky ([link](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v))

> "With a workflow, the plan lives in code and Claude's context holds only the output." - community framing on Hacker News ([link](https://news.ycombinator.com/item?id=44127000))

> "Prefer MCP tools over Bash when the integration will be used across sessions." - llmbestpractices.com ([link](https://llmbestpractices.com/ai-agents/claude-code-mcp))

> "Eight marketplaces, no unified search." - community summary on r/ClaudeWorkflows and claudemarketplaces.com ([link](https://claudemarketplaces.com/))

> "Agent skills need the same dependency-management and security scrutiny as software packages." - JFrog ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "Skills are content, plugins are packaging." - community consensus distilled from r/ClaudeCode and r/ClaudeAI ([link](https://reddit.com/r/ClaudeCode))

> "Claude now constructs orchestration at runtime rather than following a fixed sequence - it writes JavaScript scripts that spin up as many as 1,000 parallel subagents." - official Claude blog ([link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code))

> "Start with 2-3 MCP servers, add only what your daily workflow demands." - community consensus via agensi.io and buildtolaunch.substack.com ([link](https://buildtolaunch.substack.com/p/best-mcp-servers-claude-code))

> "MCP is USB-C for AI: write a tool server once and any compliant client can call it." - The New Stack ([link](https://thenewstack.io/goodbye-plugins-mcp-is-becoming-the-universal-interface-for-ai/))

> "Testing showed 8.4-10.1% improvement in document quality with no model changes" - on Outcomes grading agent, MindStudio ([link](https://www.mindstudio.ai/blog/code-with-claude-2026-new-agent-features))
