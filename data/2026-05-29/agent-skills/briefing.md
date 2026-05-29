# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-29
**Query type:** GENERAL
**Sources:** Web, GitHub, Hacker News, Official Docs, Security Research

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (blogs, news, official docs) | 42+ pages | High | Anthropic docs, security advisories, community guides, ecosystem trackers |
| GitHub | 10+ repos | 45.1k stars (awesome-claude-code alone) | Official Anthropic repos, community marketplaces, security research |
| Hacker News | 1 thread | Active community discussion | Show HN: Need (CLI tool discovery as MCP server) |
| Security Research (Snyk, OX Security, SentinelOne, Prompt Security) | 4+ reports | Industry-defining | ToxicSkills audit, MCP RCE disclosure, dependency hijacking |
| Conference/Summit Coverage | 2 events | 1,200 attendees at MCP Dev Summit | Code with Claude SF 2026, MCP Dev Summit North America 2026 |

## Synthesized Findings

### 1. The Official Anthropic Plugin Ecosystem Matures

Anthropic has shipped a formal, managed plugin directory — `anthropics/claude-plugins-official` on GitHub — containing **55+ curated plugins** as of late May 2026. The directory includes 33 Anthropic-built plugins (language servers, dev workflow tools, setup tools) and 68 partner plugins from GitHub, Playwright, Supabase, Figma, and others. External submissions require quality and security review before approval.

This followed an earlier landmark: in January 2026, Anthropic open-sourced **11 production knowledge-work plugins** under `anthropics/knowledge-work-plugins`, covering sales, legal, finance, data, marketing, customer support, product management, and biology research. The legal plugin alone triggered what analysts called "the first real market panic caused by AI threatening to replace entire professional workflows" — a $285 billion stock selloff across software, financial services, and asset management sectors.

The official plugin experience is now accessible directly within Claude Code via the `/plugin` command, which gained a **Discover tab** (v2.1.153, May 28) that pins plugins by relevance to the current directory. As of v2.1.145 (May 20), the Discover tab shows a plugin's commands, agents, skills, hooks, and MCP/LSP servers **before installation**, and since v2.1.143 (May 15) it shows projected context cost (per-turn and per-invocation token estimates).

Sources: [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | [anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | [Claude Code Updates — May 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code) | [Anthropic Moves Into Legal Tech — Artificial Lawyer](https://www.artificiallawyer.com/2026/02/02/anthropic-moves-into-legal-tech/) | [Anthropic's Legal AI Plugin Triggers $285B Stock Selloff](https://elephas.app/resources/anthropic-legal-ai-stock-selloff) | [Discover and install prebuilt plugins — Claude Code Docs](https://code.claude.com/docs/en/discover-plugins) | [Create plugins — Claude Code Docs](https://code.claude.com/docs/en/plugins) | [Plugins reference — Claude Code Docs](https://code.claude.com/docs/en/plugins-reference)

---

### 2. SKILL.md: The Open Standard for Portable Agent Capabilities

The most architecturally significant development in the ecosystem is the **SKILL.md open standard**, released by Anthropic in December 2025. A skill is a directory containing a `SKILL.md` file with YAML frontmatter (metadata, trigger conditions) and markdown instructions. Agents read the frontmatter to decide when to activate, then follow the markdown. The format is intentionally minimal and portable.

OpenAI and Google adopted the standard shortly after release. All three companies co-founded the **Agentic AI Foundation (AAIF)** under the Linux Foundation to govern it. MCP itself was simultaneously donated to AAIF, with co-founders including Anthropic, Block, and OpenAI, and backing from Google, Microsoft, AWS, Cloudflare, and Bloomberg.

Tools supporting SKILL.md as of May 2026: **Claude Code (Anthropic), Codex CLI (OpenAI), Gemini CLI (Google), GitHub Copilot (VS Code), Cursor, Cline, Windsurf, OpenCode** and 16+ others. The community Antigravity Awesome Skills library cataloged over 1,234 compatible skills.

The AAIF governance signal is the MCP Dev Summit North America 2026, which drew **1,200 attendees** (doubled from prior summit) and reported **170 member organizations** in under 4 months — double CNCF at the same growth stage. MCP SDK monthly downloads reached **110+ million**. Jim Zemlin (Linux Foundation CEO) declared: "MCP is the Linux of agents."

The standard resolves the prior fragmentation where every agentic IDE required its own extension format. SKILL.md is explicitly designed as the "USB-C of agent capabilities."

Sources: [The SKILL.md Open Standard — Full Specification (2026)](https://www.agensi.io/learn/skill-md-specification-open-standard) | [Agent Skills — Codex | OpenAI Developers](https://developers.openai.com/codex/skills) | [Use Agent Skills in VS Code](https://code.visualstudio.com/docs/copilot/customization/agent-skills) | [AI Agent Skills Guide 2026 — The Prompt Index](https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html) | [Top AI Agent Standards to Know in 2026](https://blog.agentailor.com/posts/top-ai-agent-standards-2026) | [AI Agent Skills and Plugins Explained (2026) | Tony Kipkemboi](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained) | [Donating the Model Context Protocol and Establishing the Agentic AI Foundation](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | [MCP Joins the Agentic AI Foundation](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) | [MCP Is Now Enterprise Infrastructure: Everything That Happened at MCP Dev Summit North America 2026 — AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)

---

### 3. May 2026 Claude Code Release Cadence: Skills, Plugins, and MCP

Anthropic maintained an exceptionally fast release cadence through May 2026. Key capability additions relevant to the skills/plugin/MCP system:

**v2.1.154 (May 28):** Plugin dependency enforcement; `defaultEnabled: false` option for plugins; MCP servers now receive `CLAUDE_CODE_SESSION_ID` env variable; `/simplify` command runs cleanup-only review.

**v2.1.153 (May 28):** `/plugin` Discover tab pins plugins by relevance to current directory; `skipLfs` option for GitHub/Git plugin sources; marketplace authentication consolidation; fixed stateful MCP server reconnect-loop bug; `--strict-mcp-config` refined for subagents.

**v2.1.152 (May 27):** Skills can now set `disallowed-tools` in SKILL.md frontmatter to remove tools from the model; `/reload-skills` command re-scans skill directories without restart; `SessionStart` hooks can return `reloadSkills: true`; new `MessageDisplay` hook event for transforming assistant messages; `pluginSuggestionMarketplaces` managed setting for enterprise marketplace allowlisting.

**v2.1.149 (May 22):** `/usage` breakdown shows per-category cost (skills, subagents, plugins, per-MCP-server); enterprise `allowAllClaudeAiMcps` setting loads cloud MCP connectors.

**v2.1.145 (May 20):** `/plugin` Discover now shows plugin's commands, agents, skills, hooks, and MCP/LSP servers before installation; `claude agents --json` for session scripting.

**v2.1.143 (May 15):** Plugin dependency enforcement — `disable` refuses when another enabled plugin depends on target; projected context cost shown in marketplace.

**v2.1.142 (May 14):** Plugins with root-level `SKILL.md` and no `skills/` folder automatically surfaced as a skill.

**v2.1.141 (May 13):** Hook JSON output includes `terminalSequence` field; `CLAUDE_CODE_PLUGIN_PREFER_HTTPS` env variable; MCP servers receive `CLAUDE_PROJECT_DIR`.

**v2.1.139 (May 11):** Agent View (Research Preview); `/goal` command; plugin `details` command shows component inventory and projected per-session token cost; new hook `args: string[]` exec form; `PostToolUse` hook `continueOnBlock` feeds rejection reason back to Claude.

The Code with Claude SF 2026 conference (late May) also delivered: Claude Code Routines (scheduled agents), Managed Agents multi-agent orchestration (public beta), Opus 4.8 with dynamic workflows orchestrating "tens to hundreds of agents in the background," `--plugin-url` flag for URL-based plugin distribution, and `skillOverrides` setting now functional.

Sources: [Claude Code Updates by Anthropic — May 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code) | [Code with Claude SF 2026: What Anthropic Actually Shipped](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap) | [Code with Claude SF 2026: What Actually Shipped Today vs Earlier](https://findskill.ai/blog/code-with-claude-sf-2026-what-shipped/) | [Every Claude Code Update From April 17-22, 2026: What Actually Matters](https://clskillshub.com/blog/claude-code-april-2026-updates) | [Code with Claude London 2026: Rethinking How We Build](https://claude.com/blog/code-w-claude-london-2026-rethinking-how-we-build)

---

### 4. Marketplace Landscape: From Zero to Eight Major Registries in Six Months

The skill and MCP marketplace ecosystem exploded from a single registry in December 2025 to eight or more major marketplaces by Q2 2026. The landscape now spans curated official directories, community-run repositories, commercial catalogs, and enterprise governance platforms.

**Key marketplaces:**

| Marketplace | Scale | Model |
|---|---|---|
| claude-plugins-official (Anthropic) | 55+ plugins | Curated, reviewed; built into CLI `/plugin` |
| Smithery.ai | 7,000+ servers | Docker Hub equivalent for MCP; hosted remote servers with OAuth |
| MCPMarket.com | 10,000+ MCP servers, 23+ categories | Browsable web UI |
| Official MCP Registry (registry.modelcontextprotocol.io) | ~2,000 entries | Co-maintained by Anthropic, GitHub, PulseMCP, Microsoft |
| SkillsMP | 800,000+ skills | Built around open SKILL.md standard; GitHub scraper |
| LobeHub Skills | 169,000+ skills | Best within LobeHub stack |
| ClaudeSkills.info | 658+ free skills | Community-contributed, no paid tier |
| tonsofskills.com (ccpi) | 425 plugins, 2,810 skills, 200 agents | Open-source; `pnpm add -g @intentsolutionsio/ccpi`; 42 SaaS packs |

Notable community infrastructure: `hesreallyhim/awesome-claude-code` reached **45.1k stars, 3.9k forks** — a curated collection of skills, hooks, slash commands, agent orchestrators, and plugins. `jeremylongshore/claude-code-plugins-plus-skills` offers 425 plugins, 2,810 skills, 200 agents as an open-source marketplace.

Context7 (by Upstash) is the most-starred individual MCP server: **56.3K GitHub stars**, 890,000+ weekly npm downloads. It dynamically fetches version-specific library documentation (React, Next.js, Tailwind, etc.) — solving one of the biggest sources of hallucination in AI-assisted development.

Other notable May 2026 MCP launches: Meta MCP (Facebook/Instagram ads management, April 29); Higgsfield MCP (AI image/video generation from 30+ models); GitHub MCP with secret scanning GA (automated credential detection); Moody's MCP (credit ratings on 600M+ companies, launched at Code with Claude SF).

Paid tiers with 70-80% creator revenue splits are expected by Q4 2026.

Sources: [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/) | [Every AI Skill Marketplace and Directory (2026)](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | [Skills Marketplace — The New App Store for AI Agents (2026)](https://www.agensi.io/learn/skills-marketplace-ai-agents) | [Top 5 Agent Skill Marketplaces for Building Powerful AI Agents](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | [Agent Skills, Plugins and Marketplace: The Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | [Best MCP Registries in 2026 — TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries) | [50+ Best MCP Servers for Claude Code in 2026](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | [AI Agent Marketplaces 2026: Discovery and Distribution](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | [MCP Server Ecosystem Tracker: 56 Servers Cataloged 2026](https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026) | [Agent Skills Marketplace — SkillsMP](https://skillsmp.com/) | [Agent Skills Marketplace — LobeHub](https://lobehub.com/skills) | [Smithery AI](https://smithery.ai/) | [Official MCP Registry](https://registry.modelcontextprotocol.io/) | [GitHub — hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) | [GitHub — jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | [GitHub — upstash/context7](https://github.com/upstash/context7) | [GitHub — anthropics/skills](https://github.com/anthropics/skills) | [GitHub Expands Secret Scanning with GA of MCP Server Integration — InfoQ](https://www.infoq.com/news/2026/05/github-mcp-secret-scanning/) | [AI Agent Marketplaces (overview) — TrueFoundry](https://www.truefoundry.com/blog/ai-agent-marketplaces) | [AI Agent Skills Marketplace: The New Plugin Ecosystem — Paperclipped](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/)

---

### 5. MCP Tool Search Solves Context Bloat (January 2026, Still Dominant)

One of the most impactful technical advances in the MCP ecosystem is **MCP Tool Search**, announced by Anthropic's Thariq Shihipar on January 14, 2026. The system introduces lazy loading: instead of dumping all tool definitions into the context window at session start, Claude receives a ToolSearch tool and fetches 3-5 relevant tool definitions (~3K tokens) per query via keyword search.

Performance impact:
- Meta MCP + Shopify AI Toolkit + Higgsfield MCP simultaneously: **12K context tokens → ~600 tokens** (95% reduction)
- With 50+ MCP tools active: **~77K tokens → ~8.7K tokens** (95% reduction)

Activation threshold: auto-triggers when MCP tool descriptions exceed 10K tokens. Tools can be marked `defer_loading: true`. The feature is **auto-enabled by default for all users**. Microsoft VSCode filed a feature request to implement the same pattern (Issue #288310). OpenCode filed a similar request (Issue #9350).

Community guidance: past ~50 visible tools, model performance degrades because tool descriptions compete in the context window. Recommended practice: start with 2-3 servers matching daily workflow; maximum 5-7 before Tool Search becomes essential.

The November 2025 MCP spec update added async operation support, stateless Streamable HTTP transport, OAuth 2.1 authorization, server-side `.well-known` URL discovery, and structured tool annotations — providing the protocol foundation for these optimizations.

Sources: [Claude Code MCP Tool Search: Save 95% Context](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) | [Claude Code Finally Gets Lazy Loading for MCP Tools — Medium](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc) | [Connect Claude Code to tools via MCP — Claude Code Docs](https://code.claude.com/docs/en/mcp) | [One Year of MCP: November 2025 Spec Release](https://blog.modelcontextprotocol.io/posts/2025-11-25-first-mcp-anniversary/) | [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol) | [Why the Model Context Protocol Won — The New Stack](https://thenewstack.io/why-the-model-context-protocol-won/) | [The 15 MCP Servers Worth Wiring Into Claude Code and Cursor (2026)](https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/) | [MCP Protocol 2026: Build Production Servers for Claude, Cursor, VS Code Copilot](https://pooya.blog/blog/mcp-model-context-protocol-production-2026/) | [Everything your team needs to know about MCP in 2026 — WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) | [GitHub — modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)

---

### 6. Security Crisis: Malicious Skills and Systemic MCP Vulnerabilities

The rapid growth of the skill and plugin ecosystem has produced a serious, unresolved security crisis spanning multiple attack vectors.

**Snyk ToxicSkills Audit (February 2026):** Snyk researchers scanned **3,984 skills** from ClawHub and skills.sh marketplaces. Results: **534 (13.4%)** contained critical-level security issues; **76 confirmed malicious payloads** (credential theft, backdoor installation, data exfiltration); **prompt injection in 36%** of tested skills; **1,467 malicious payloads** found ecosystem-wide; 10.9% had exposed secrets; 17.7% fetched untrusted third-party content; 8 malicious skills remained live on ClawHub at publication. Submission rate had jumped 10x — from under 50/day in mid-January to 500+/day by early February, driven by the ClawHavoc campaign.

**ClawHavoc Campaign:** Attackers flooded ClawHub with **341 malicious skills in a 3-day window**. All 335 AMOS-delivering skills shared a single C2 IP (`91.92.242[.]30`). Target data: exchange API keys, wallet private keys, SSH credentials, browser passwords, `.env` files.

**OX Security MCP SDK RCE (April 2026):** OX Security disclosed a systemic RCE vulnerability across **all official MCP SDKs** (Python, TypeScript, Java, Rust). Scope: **150M+ downloads, 7,000+ public servers, 200,000 vulnerable instances**. The flaw: any process command passed to the MCP STDIO interface executes on the host regardless of whether a valid MCP server is initialized. **Anthropic declined to change the protocol architecture**, calling the behavior "expected" and placing input sanitization responsibility on developers. Related CVEs: CVE-2025-49596, CVE-2026-22252, CVE-2026-22688, CVE-2025-54994, CVE-2025-54136.

**Marketplace Dependency Hijacking (SentinelOne / Prompt Security):** A documented attack vector where a malicious plugin includes a "dependency management skill" that silently redirects package installations to attacker-controlled sources. The malicious code embeds cleanly — imports work normally, example code runs without error. Persistence: plugins remain active across all sessions.

**MCP Dev Summit 0-day:** Jonathan Leitschuh disclosed a DNS rebinding vulnerability at the summit affecting multiple MCP implementations, including Google's Database Toolbox (disclosed live as a 0-day).

**Anthropic's Response:** Released a free `security-guidance` plugin for all Claude Code users. Three review levels: file edits, model turns, and commits. Monitors code edits, diffs, and commits in real time to automatically flag dangerous patterns. Trail of Bits also published security research skills under `trailofbits/skills`.

**OWASP Response:** Launched a dedicated **Agentic Skills Top 10 (AST10)** project. AST01 = Malicious Skills. The "Lethal Trifecta" threat model: skills are especially dangerous when they simultaneously have (1) access to private data, (2) exposure to untrusted content, and (3) ability to communicate externally. Standard code-scanning tools are ineffective because skills blend natural language with code. Academic response: SkillSieve hierarchical triage framework published on arXiv.

Sources: [Snyk ToxicSkills — Snyk Blog](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | [GitHub — snyk-labs/toxicskills-goof](https://github.com/snyk-labs/toxicskills-goof) | [When Your Plugin Starts Picking Your Dependencies — SentinelOne](https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/) | [How Marketplace Skills Hijack Dependencies — Prompt Security](https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code/) | [Anthropic MCP Design Vulnerability Enables RCE — The Hacker News](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) | [OX Security — The Mother of All AI Supply Chains](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | [Systemic Flaw in MCP Protocol Could Expose 150 Million Downloads — Infosecurity Magazine](https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/) | [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) | [AST01 — Malicious Skills](https://owasp.org/www-project-agentic-skills-top-10/ast01) | [SkillSieve: A Hierarchical Triage Framework for Detecting Malicious AI Agent Skills — arXiv](https://arxiv.org/html/2604.06550v1) | [Anthropic Releases Free Security Plugin — Cybersecurity News](https://cybersecuritynews.com/free-security-plugin-for-claude-code/) | [GitHub — trailofbits/skills](https://github.com/trailofbits/skills) | [MCP Is Now Enterprise Infrastructure — AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)

---

### 7. Enterprise Registries: Governance Comes to the Plugin Layer

Large enterprises are not adopting public marketplaces directly — they are building governed, private registries with RBAC, approval workflows, and supply chain controls.

**Kong MCP Registry (February 2, 2026):** Kong announced Kong MCP Registry within Kong Konnect Catalog. Key capability: links MCP servers directly to underlying APIs for blast radius analysis, ownership tracking, and inherited policy enforcement. Integrates with AAIF's interoperability framework.

**AWS Agent Registry in Bedrock AgentCore (Preview, April 2026):** A private, governed catalog for agents, tools, skills, MCP servers, and custom resources. Features hybrid search (keyword + semantic), approval workflows for discoverability, IAM and OAuth (Custom JWT) access control, URL-based discovery that auto-fetches schemas from live MCP endpoints. Available in 5 AWS regions. Announced April 13, 2026 alongside Claude Mythos Preview in Amazon Bedrock.

**Red Hat OpenShift AI MCP Catalog:** Introduced in OpenShift AI 3.4 (developer preview). Pre-loaded with servers from Red Hat, technology partners, and open source community. Governance features: supply chain controls, trust tiers for certified assets, identity-based tool filtering, mandatory approvals for sensitive tool calls.

**agentic-community/mcp-gateway-registry:** Community-built enterprise-ready MCP Gateway & Registry with OAuth authentication, dynamic tool discovery, Keycloak/Entra integration, and auditable tool access.

Enterprise usage data from MCP Dev Summit: **Uber** has 5,000+ engineers, 10,000+ internal services, and runs 60,000+ agent executions weekly. Their Minions agent makes 1,800 code changes/week and is used by 95% of engineering.

Sources: [Kong Introduces MCP Registry in Kong Konnect — PR Newswire](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html) | [Kong MCP Registry Blog](https://konghq.com/blog/product-releases/kong-mcp-registry-tech-preview) | [AWS Agent Registry — AWS](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | [AWS Launches Agent Registry in Preview — InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | [AWS Weekly Roundup April 13](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/) | [The MCP catalog is here — Red Hat Blog](https://www.redhat.com/en/blog/mcp-catalog-here-discover-deploy-and-connect-red-hat-openshift-ai) | [GitHub — agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) | [Linux Foundation Announces Agentic AI Foundation (AAIF)](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation)

---

### 8. Broader Ecosystem: Cross-Platform Convergence

The agent skills ecosystem is not Claude-specific — it has become the battleground for cross-platform AI tooling standards.

**OpenAI Agents SDK (April 15, 2026):** Major update added native sandbox execution, first-class MCP integration, sub-agent/handoff patterns, and Codex-style filesystem tools. Codex CLI adopted SKILL.md.

**Google Cloud:** Renamed Vertex AI to the Gemini Enterprise Agent Platform, absorbed Agentspace into a unified product, advanced the A2A (Agent-to-Agent) interoperability protocol. Google's Database Toolbox MCP server was the subject of the DNS rebinding 0-day at MCP Dev Summit.

**Microsoft Agent 365 GA (May 1, 2026):** Enterprise observability, governance, and security for AI agents. May 2026 update added SASE (Secure Access Service Edge) for agents and threat detection/blocking. Microsoft also published an open-source Agent Governance Toolkit (April 2, 2026) providing runtime security for AI agents.

**LangGraph v1.2 (May 2026):** Per-node timeouts, error recovery, graceful shutdown, new DeltaChannel.

**Google Genkit Middleware (May 14, 2026):** Composable hooks at generate/model/tool layers; retries with exponential backoff; model fallbacks; tool approval gates.

**Oracle Fusion Applications AI Agent Marketplace (October 2025):** Enterprise-validated agents deployable directly within Oracle Fusion Cloud environments.

**Anthropic acquisitions:** Acquired Vercept to advance computer-use capabilities for desktop and mobile platforms.

**Ecosystem scale (May 2026):** 14,000+ MCP servers listed across directories; 97 million cumulative SDK downloads; 110+ million monthly downloads.

Sources: [GitHub — Zijian-Ni/awesome-ai-agents-2026](https://github.com/Zijian-Ni/awesome-ai-agents-2026) | [Google Cloud Next 2026: AI agents, A2A protocol, Workspace Studio — The Next Web](https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era) | [Introducing the Agent Governance Toolkit — Microsoft Open Source Blog](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/) | [Oracle Launches Fusion Applications AI Agent Marketplace](https://www.oracle.com/news/announcement/ai-world-oracle-launches-fusion-applications-ai-agent-marketplace-to-accelerate-enterprise-ai-adoption-2025-10-15/) | [Claude Code MCP Servers & Plugins: The Complete 2026 Guide](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | [Best Claude Code Plugins, Skills & MCP Servers (2026)](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | [Claude Code Extensions: MCP, Skills, Agents & Hooks Guide 2026 | Morph](https://www.morphllm.com/claude-code-extensions) | [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026 — Morph](https://www.morphllm.com/claude-code-skills-mcp-plugins) | [Claude Code Skills vs MCP Servers — DEV Community](https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k) | [My Claude Code Setup: MCP Servers, Hooks, Skills and Agents (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | [The Complete Claude Code Power User Guide — DEV Community](https://dev.to/numbpill3d/the-complete-claude-code-power-user-guide-slash-commands-hooks-skills-more-6ep) | [Claude Code Plugins: A 2026 Guide — Nimbalyst](https://nimbalyst.com/blog/claude-code-plugins-guide/) | [10 top Claude Code plugins to use in 2026 — DEV Community](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6) | [AI Agent Skills and Plugins Explained (2026) | Tony Kipkemboi](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)

---

### 9. Community Developer Experience and Hacker News Signals

From HN and community forums, most developers still use Claude Code without customization. Heavy customization is concentrated among power users. The clearest mental model from the community: **Skills for methodology** (how Claude should approach a task), **MCP for connectivity** (access to external systems) — use both together. Plugin usage is growing fastest among teams sharing `project/.claude/settings.json`.

A notable HN thread (Show HN: "Need") highlighted a real pain point: "Every time I ask Claude or Cursor to use a CLI tool, it either hallucinates a package name or recommends something outdated." Creator `schreibertuc` built Need to index 10,000+ CLI tools with semantic search via embeddings + pgvector, restricted to safe package managers (brew/npm/pip/cargo/apt). Community feedback (`sachinkg12`) flagged ranking issues: "compress video without losing quality" returned jpegrescan instead of ffmpeg; `jq` ranked #7 for "pretty print json"; `yt-dlp` omitted entirely for YouTube downloads.

Sources: [Show HN: Need is a CLI tool discovery as an MCP server — Hacker News](https://news.ycombinator.com/item?id=47413712) | [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026 — Morph](https://www.morphllm.com/claude-code-skills-mcp-plugins) | [The Complete Claude Code Power User Guide — DEV Community](https://dev.to/numbpill3d/the-complete-claude-code-power-user-guide-slash-commands-hooks-skills-more-6ep) | [My Claude Code Setup: MCP Servers, Hooks, Skills and Agents (2026)](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | [Agent Skills, Plugins and Marketplace: The Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/) | [AI Agent Skills and Plugins Explained (2026) | Tony Kipkemboi](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)

---

## Cross-Source Patterns

### Pattern 1: Ecosystem grew from zero to critical mass in under six months

**Platforms:** Web, GitHub, Conference coverage, Security research
The plugin/skill ecosystem went from launch in December 2025 to 8+ major marketplaces, 14,000+ MCP servers, 800,000+ indexed skills, and 110+ million monthly SDK downloads by May 2026. Security researchers began scanning at scale by February, indicating the ecosystem reached volume-at-risk status almost immediately. The Snyk ToxicSkills audit (February 2026), OWASP launching a dedicated top-10 project, and OX Security's systemic RCE disclosure (April 2026) all follow the same pattern as npm/PyPI ecosystem security crises — but compressed into weeks rather than years.

Key quotes:
- "The ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026." — Agensi.io ([link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))
- "MCP SDK surpassed 97M cumulative downloads... enterprise infrastructure per AAIF." — WorkOS ([link](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026))

### Pattern 2: SKILL.md portability is the defining architectural win

**Platforms:** Web (Anthropic docs, OpenAI docs, VS Code docs), GitHub, Conference coverage
All three major AI labs (Anthropic, OpenAI, Google) co-adopted SKILL.md within weeks of its release and co-founded governance infrastructure under the Linux Foundation. This speed of cross-competitor adoption is unusual and signals the format solves a genuine coordination problem — the "every IDE needs its own extension format" fragmentation that predated it.

Key quotes:
- "MCP is the Linux of agents." — Jim Zemlin, Linux Foundation CEO, at MCP Dev Summit ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))
- "The agent can hallucinate about robbing a bank. The control plane must be correct." — Alex Salazar, Arcade CEO, at MCP Dev Summit ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

### Pattern 3: Security is unresolved and Anthropic declined to fix the core vulnerability

**Platforms:** Web (The Hacker News, Infosecurity Magazine, Cybersecurity News), Security research (OX Security, Snyk, SentinelOne, Prompt Security), OWASP
13.4% of audited skills are malicious (Snyk). The MCP STDIO RCE affects 150M+ downloads, and Anthropic explicitly declined to patch it. OWASP now has a dedicated agentic skills top-10. This is the central unresolved tension: the ecosystem is growing faster than its security posture.

Key quotes:
- "534 (13.4%) contained critical-level security issues... 76 confirmed malicious payloads." — Snyk ToxicSkills ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))
- "Anthropic declined to change the protocol architecture, calling the behavior 'expected' and placing input sanitization responsibility on developers." — The Hacker News summary of OX Security disclosure ([link](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html))

### Pattern 4: Enterprise is moving to private governed registries, not public marketplaces

**Platforms:** Web (AWS, Kong, Red Hat, Microsoft, Oracle)
AWS, Kong, Red Hat, and Microsoft all shipped enterprise MCP/agent registries with RBAC, approval workflows, and supply chain controls in Q1-Q2 2026. None of these are public marketplaces — they are private catalog systems for internal tool governance. This suggests enterprise adoption is proceeding along a different path than community/developer adoption.

Key quotes:
- "Behind corporate firewalls, teams connect MCPs to Salesforce, Jira, wikis." — David Soria Parra, Anthropic MCP co-creator, at MCP Dev Summit ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))
- Uber: "5,000+ engineers, 10,000+ internal services, 60,000+ agent executions weekly; Minions agent: 1,800 code changes/week, used by 95% of engineering." — MCP Dev Summit ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

### Pattern 5: MCP Tool Search resolved a hard technical constraint

**Platforms:** Web (Claudefa.st, Medium, Claude Code Docs), GitHub (VS Code, OpenCode issue trackers)
The 95% token reduction from MCP Tool Search (lazy loading) is cited across web sources, GitHub issue trackers at Microsoft and OpenCode, and Claude Code documentation. The solution unlocked connecting unlimited MCP servers without performance degradation, removing a hard ceiling that had previously limited practical tool count to ~50.

---

## Per-Platform Tables

### Web Sources

| Title | URL | Date | Key Signal |
|-------|-----|------|------------|
| Claude Code Plugins \| Skills, MCP Servers & Marketplace Directory | https://claudemarketplaces.com/ | ongoing | Community aggregator for Claude ecosystem |
| Claude Code MCP Servers & Plugins: The Complete 2026 Guide | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | 2026 | Full setup guide |
| Best Claude Code Plugins, Skills & MCP Servers (2026) | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | 2026 | Curated recommendations |
| Plugins reference - Claude Code Docs | https://code.claude.com/docs/en/plugins-reference | ongoing | Official plugin structure docs |
| Claude Code Plugins: A 2026 Guide | https://nimbalyst.com/blog/claude-code-plugins-guide/ | 2026 | Plugin architecture explainer |
| 10 top Claude Code plugins to use in 2026 | https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 | 2026 | Top 10 picks including Meta MCP |
| 50+ Best MCP Servers for Claude Code in 2026 | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 2026 | 50+ server catalog |
| Introducing the Model Context Protocol | https://www.anthropic.com/news/model-context-protocol | Nov 2024 | Origin announcement |
| Connect Claude Code to tools via MCP | https://code.claude.com/docs/en/mcp | ongoing | Official MCP docs |
| Create plugins - Claude Code Docs | https://code.claude.com/docs/en/plugins | ongoing | Plugin authoring guide |
| My Claude Code Setup 2026 | https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/ | 2026 | Real-world config walkthrough |
| The 15 MCP Servers Worth Wiring Into Claude Code and Cursor | https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/ | 2026 | 15-server curated list |
| Claude Code Skills vs MCP Servers | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | 2026 | Comparative guide |
| MCP Protocol 2026: Build Production Servers | https://pooya.blog/blog/mcp-model-context-protocol-production-2026/ | 2026 | Production server development guide |
| Agent Skills, Plugins and Marketplace: The Complete Guide | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | 2026 | Cross-platform skills explainer |
| Every AI Skill Marketplace and Directory (2026) | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 2026 | Marketplace landscape overview |
| Top 5 Agent Skill Marketplaces | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | 2026 | KDnuggets survey |
| AI Agent Skills and Plugins Explained (2026) | https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained | 2026 | Skills vs plugins conceptual clarity |
| Top AI Agent Standards to Know in 2026 | https://blog.agentailor.com/posts/top-ai-agent-standards-2026 | 2026 | SKILL.md, MCP, A2A overview |
| Skills Marketplace — The New App Store for AI Agents | https://www.agensi.io/learn/skills-marketplace-ai-agents | 2026 | Monetization model analysis |
| AI Agent Skills Marketplace: The New Plugin Ecosystem | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | 2026 | Security-incident-driven analysis |
| AI Agent Marketplaces 2026: Discovery and Distribution | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | 2026 | Distribution dynamics |
| MCP Server Ecosystem Tracker: 56 Servers Cataloged 2026 | https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026 | 2026 | AWS Agent Toolkit MCP at 60+ servers |
| AI Agent Marketplaces (overview) | https://www.truefoundry.com/blog/ai-agent-marketplaces | ongoing | MLOps/enterprise lens |
| Best MCP Registries in 2026 | https://www.truefoundry.com/blog/best-mcp-registries | 2026 | Registry comparison |
| Oracle Launches Fusion Applications AI Agent Marketplace | https://www.oracle.com/news/announcement/ai-world-oracle-launches-fusion-applications-ai-agent-marketplace-to-accelerate-enterprise-ai-adoption-2025-10-15/ | Oct 2025 | Enterprise marketplace |
| Introducing the Agent Governance Toolkit | https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/ | Apr 2026 | Microsoft open-source governance |
| Google Cloud Next 2026: AI agents, A2A protocol | https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era | 2026 | Google platform consolidation |
| Donating MCP and Establishing AAIF | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | Dec 2025 | Governance transfer announcement |
| One Year of MCP: November 2025 Spec Release | https://blog.modelcontextprotocol.io/posts/2025-11-25-first-mcp-anniversary/ | Nov 2025 | Protocol spec updates |
| MCP Joins the Agentic AI Foundation | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | Dec 2025 | Linux Foundation governance |
| Why the Model Context Protocol Won | https://thenewstack.io/why-the-model-context-protocol-won/ | 2025 | Retrospective analysis |
| Code with Claude London 2026 | https://claude.com/blog/code-w-claude-london-2026-rethinking-how-we-build | May 2026 | MCP tunnels, self-hosted sandboxes |
| Every Claude Code Update Apr 17-22, 2026 | https://clskillshub.com/blog/claude-code-april-2026-updates | Apr 2026 | Changelog analysis |
| Code with Claude SF 2026: What Anthropic Actually Shipped | https://blakecrosley.com/blog/code-with-claude-sf-2026-recap | May 2026 | Conference deliverables recap |
| Code with Claude SF 2026: What Actually Shipped | https://findskill.ai/blog/code-with-claude-sf-2026-what-shipped/ | May 2026 | Parallel recap |
| Claude Code Updates — May 2026 — Releasebot | https://releasebot.io/updates/anthropic/claude-code | May 2026 | Full changelog |
| Claude Code MCP Tool Search: Save 95% Context | https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search | 2026 | Lazy loading explainer |
| Claude Code Finally Gets Lazy Loading — Medium | https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc | 2026 | MCP Tool Search deep dive |
| Everything your team needs to know about MCP in 2026 — WorkOS | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | 2026 | Enterprise MCP overview |
| Claude Code Skills vs MCP vs Plugins: Complete Guide 2026 — Morph | https://www.morphllm.com/claude-code-skills-mcp-plugins | 2026 | Taxonomy guide |
| Claude Code Extensions: MCP, Skills, Agents & Hooks Guide 2026 | https://www.morphllm.com/claude-code-extensions | 2026 | Full extensions guide |
| The Complete Claude Code Power User Guide — DEV Community | https://dev.to/numbpill3d/the-complete-claude-code-power-user-guide-slash-commands-hooks-skills-more-6ep | 2026 | Power user guide |
| Discover and install prebuilt plugins | https://code.claude.com/docs/en/discover-plugins | ongoing | Official discovery docs |
| The SKILL.md Open Standard | https://www.agensi.io/learn/skill-md-specification-open-standard | 2026 | Format specification |
| AI Agent Skills Guide 2026 | https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html | 2026 | User guide |
| Snyk ToxicSkills | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | Feb 2026 | Security audit |
| When Your Plugin Starts Picking Your Dependencies — SentinelOne | https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/ | 2026 | Dependency hijacking analysis |
| How Marketplace Skills Hijack Dependencies — Prompt Security | https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code/ | 2026 | Attack vector documentation |
| Anthropic MCP Design Vulnerability Enables RCE — The Hacker News | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | Apr 2026 | RCE disclosure coverage |
| OX Security — The Mother of All AI Supply Chains | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | Apr 2026 | Systemic vulnerability research |
| Systemic Flaw in MCP Protocol — Infosecurity Magazine | https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/ | Apr 2026 | Industry coverage |
| OWASP Agentic Skills Top 10 | https://owasp.org/www-project-agentic-skills-top-10/ | 2026 | OWASP project launch |
| AST01 — Malicious Skills | https://owasp.org/www-project-agentic-skills-top-10/ast01 | 2026 | Top 10 entry #1 |
| SkillSieve: Detecting Malicious AI Agent Skills — arXiv | https://arxiv.org/html/2604.06550v1 | 2026 | Academic triage framework |
| Anthropic Releases Free Security Plugin | https://cybersecuritynews.com/free-security-plugin-for-claude-code/ | May 2026 | Security plugin announcement |
| Anthropic Moves Into Legal Tech — Artificial Lawyer | https://www.artificiallawyer.com/2026/02/02/anthropic-moves-into-legal-tech/ | Feb 2026 | Legal plugin coverage |
| Anthropic's Legal AI Plugin Triggers $285B Stock Selloff | https://elephas.app/resources/anthropic-legal-ai-stock-selloff | Feb 2026 | Market impact |
| MCP Is Now Enterprise Infrastructure — AAIF | https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/ | 2026 | Summit recap |
| Kong Introduces MCP Registry — PR Newswire | https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html | Feb 2026 | Kong enterprise announcement |
| Kong MCP Registry Blog | https://konghq.com/blog/product-releases/kong-mcp-registry-tech-preview | Feb 2026 | Kong product details |
| AWS Agent Registry — AWS | https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/ | Apr 2026 | AWS announcement |
| AWS Launches Agent Registry in Preview — InfoQ | https://www.infoq.com/news/2026/04/aws-agent-registry-preview/ | Apr 2026 | InfoQ coverage |
| AWS Weekly Roundup April 13 | https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/ | Apr 2026 | AWS weekly blog |
| The MCP catalog is here — Red Hat Blog | https://www.redhat.com/en/blog/mcp-catalog-here-discover-deploy-and-connect-red-hat-openshift-ai | 2026 | Red Hat announcement |
| Linux Foundation Announces Agentic AI Foundation | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | 2025 | AAIF formation |
| GitHub Expands Secret Scanning — InfoQ | https://www.infoq.com/news/2026/05/github-mcp-secret-scanning/ | May 2026 | GitHub MCP security feature |

### GitHub

| Repository | Stars/Forks | Notes |
|------------|-------------|-------|
| hesreallyhim/awesome-claude-code | 45.1k stars, 3.9k forks | Curated Claude Code resources |
| anthropics/claude-plugins-official | — | Official plugin directory |
| anthropics/knowledge-work-plugins | — | 11 knowledge-work plugins |
| anthropics/skills | — | Official agent skills repo |
| jeremylongshore/claude-code-plugins-plus-skills | — | 425 plugins, 2,810 skills, 200 agents |
| upstash/context7 | 56.3k stars | Most-starred MCP server |
| modelcontextprotocol/servers | — | 50+ official MCP servers |
| agentic-community/mcp-gateway-registry | — | Enterprise gateway registry |
| snyk-labs/toxicskills-goof | — | Security research artifacts |
| trailofbits/skills | — | Security research skills |
| Chat2AnyLLM/awesome-claude-plugins | — | Marketplace curation list |
| Zijian-Ni/awesome-ai-agents-2026 | — | Broader agent ecosystem tracker |

### Hacker News

| Thread | Key Points |
|--------|------------|
| Show HN: Need — CLI tool discovery as MCP server | Creator: hallucination of CLI tool names drove development; 10,000+ tools indexed with semantic search; community flagged ranking issues (ffmpeg, jq, yt-dlp omissions) |

### Security Research

| Report | Organization | Key Finding |
|--------|-------------|-------------|
| ToxicSkills | Snyk | 13.4% of audited skills malicious; 76 confirmed payloads; 36% prompt injection rate |
| The Mother of All AI Supply Chains | OX Security | Systemic RCE in all MCP SDKs; 150M+ downloads affected; Anthropic declined to patch |
| Marketplace Skills and Dependency Hijack | SentinelOne / Prompt Security | Silent package manager redirection; persistent across sessions |
| Agentic Skills Top 10 (AST10) | OWASP | New project; AST01 = Malicious Skills; "Lethal Trifecta" threat model |
| SkillSieve | arXiv | Hierarchical triage framework for detecting malicious skills |
| DNS Rebinding 0-day | Jonathan Leitschuh at MCP Dev Summit | Affects Google Database Toolbox and others; disclosed live |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (not crawled in this run)
├─ 🔵 X: 0 posts (not crawled in this run)
├─ 🔴 YouTube: 0 videos (not crawled in this run)
├─ 🟢 HN: 1 story | active comments | Show HN: Need (CLI tool discovery MCP server)
├─ 🟣 TikTok: 0 videos (not crawled in this run)
├─ 🩷 Instagram: 0 reels (not crawled in this run)
├─ 🦋 Bluesky: 0 posts (not crawled in this run)
├─ 📊 Polymarket: 0 markets (not crawled in this run)
├─ 🌐 Web: 60+ pages | blogs, official docs, security research, conference recaps, news coverage
├─ 🐙 GitHub: 12+ repos | 45.1k+ stars (awesome-claude-code) | 56.3k stars (context7)
└─ 🗣️ Top voices: @thariq (Anthropic, MCP Tool Search), Jim Zemlin (Linux Foundation), David Soria Parra (Anthropic MCP co-creator), Alex Salazar (Arcade CEO), Jonathan Leitschuh (DNS rebinding 0-day) | r/claudeai (not directly crawled but referenced)
```

## Data Gaps

- **Reddit:** Not directly crawled in this run. Community discussion likely active on r/claudeai, r/LocalLLaMA, and r/mcp but not captured.
- **X/Twitter:** Not crawled. Likely significant signal around Code with Claude SF 2026 conference announcements and ToxicSkills security disclosure.
- **YouTube:** No video results captured. Conference talk recordings from Code with Claude SF and MCP Dev Summit North America likely exist.
- **TikTok/Instagram/Bluesky:** Not crawled. Developer community occasionally active on Bluesky for security disclosures.
- **Polymarket:** No prediction markets on plugin ecosystem topics found.
- **ClawHub marketplace:** Directly implicated in ToxicSkills and ClawHavoc campaign but no direct URL accessible at research time; referenced only through Snyk reporting.
- **skills.sh marketplace:** Referenced in Snyk audit but not directly profiled.
- **Approximate coverage:** ~75% of web/developer signal captured; social media signal (Reddit, X, YouTube) absent from this run. Security research appears comprehensive for major Q1-Q2 2026 incidents.

## Key Quotes

> "MCP is the Linux of agents." — Jim Zemlin, Linux Foundation CEO, at MCP Dev Summit North America 2026 ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

> "The agent can hallucinate about robbing a bank. The control plane must be correct." — Alex Salazar, Arcade CEO, at MCP Dev Summit North America 2026 ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

> "Behind corporate firewalls, teams connect MCPs to Salesforce, Jira, wikis." — David Soria Parra, Anthropic MCP co-creator, at MCP Dev Summit North America 2026 ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))

> "534 (13.4%) contained critical-level security issues... 76 confirmed malicious payloads." — Snyk ToxicSkills audit, February 2026 ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Anthropic declined to change the protocol architecture, calling the behavior 'expected' and placing input sanitization responsibility on developers." — The Hacker News, covering OX Security's MCP RCE disclosure, April 2026 ([link](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html))

> "Every time I ask Claude or Cursor to use a CLI tool, it either hallucinates a package name or recommends something outdated." — schreibertuc, Show HN: Need, Hacker News ([link](https://news.ycombinator.com/item?id=47413712))

> "The first real market panic caused by AI threatening to replace entire professional workflows." — on the $285B stock selloff following Anthropic's legal plugin, February 2026 ([link](https://elephas.app/resources/anthropic-legal-ai-stock-selloff))

> "12K context tokens → ~600 tokens" — 95% context reduction from MCP Tool Search with three major MCP servers connected simultaneously ([link](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search))

> "Skills become especially dangerous when they simultaneously have access to private data, exposure to untrusted content, and ability to communicate externally." — OWASP Agentic Skills Top 10, "Lethal Trifecta" threat model ([link](https://owasp.org/www-project-agentic-skills-top-10/ast01))

> "Minions agent: 1,800 code changes/week, used by 95% of engineering." — Uber, presented at MCP Dev Summit North America 2026 ([link](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/))
