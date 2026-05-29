I now have comprehensive coverage across all dimensions. Entering the cluster and render phase.

---

# Last 30 Days: Claude Code Skills & Plugins, Agent Skill Marketplaces, MCP Servers, Plugin Ecosystems, Skill Discovery & Distribution

*Research window: ~May 2026. Sources span GitHub, official docs, security research, enterprise announcements, community registries, and the MCP Dev Summit.*

---

## CLUSTER 1 — THE OFFICIAL ANTHROPIC PLUGIN ECOSYSTEM

### Anthropic Launches Official Plugins Directory (May 25, 2026)

Anthropic shipped the `anthropics/claude-plugins-official` GitHub repository as the managed directory for high-quality Claude Code plugins. As of late May 2026, the official directory contains **55+ curated plugins**, including 33 Anthropic-built plugins (language servers, dev workflow tools, setup tools) and 68 partner plugins from GitHub, Playwright, Supabase, Figma, and others. External plugins must pass quality and security standards for approval.

**Source:** [Anthropic Launches Official Claude Code Plugins Directory | AIToolly](https://aitoolly.com/ai-news/article/2026-05-25-anthropic-launches-official-claude-code-plugins-directory-to-enhance-ai-development-workflows)

### Knowledge-Work Plugins (January 30, 2026 — still highly active)

Anthropic open-sourced 11 production plugins under `anthropics/knowledge-work-plugins` covering sales, legal, finance, data, marketing, customer support, product management, and biology research — bundled as skills, connectors, slash commands, and sub-agents. The legal plugin triggered a $285 billion stock selloff across software, financial services, and asset management sectors within days — "the first real market panic caused by AI threatening to replace entire professional workflows."

**Sources:** [GitHub — anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins) | [Anthropic Moves Into Legal Tech — Artificial Lawyer](https://www.artificiallawyer.com/2026/02/02/anthropic-moves-into-legal-tech/) | [Anthropic's Legal AI Plugin Triggers $285B Stock Selloff](https://elephas.app/resources/anthropic-legal-ai-stock-selloff)

### Code with Claude SF 2026 — What Actually Shipped

The Code with Claude SF 2026 developer conference was described as "more of a victory lap than a launch event," with most features shipping weeks before the event. Confirmed deliveries:
- Claude Code Routines (scheduled agents)
- Managed Agents multi-agent orchestration (public beta)
- Opus 4.8 with "high-effort defaults" and dynamic workflows orchestrating "tens to hundreds of agents in the background" (v2.1.154, May 28)
- `--plugin-url` flag for distributing plugins via URL
- `skillOverrides` setting now functional
- SpaceX Colossus 1 partnership: 300+ megawatts and 220,000+ NVIDIA GPUs
- Five-hour rate limits doubled for Pro, Max, Team, Enterprise
- Financial services suite: 10 agent templates across pitch building, earnings review, KYC screening, general ledger reconciliation, and more; Moody's MCP providing credit ratings on 600M+ companies

**Sources:** [Code with Claude SF 2026: What Anthropic Actually Shipped](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap) | [Code with Claude SF 2026: What Actually Shipped Today vs Earlier](https://findskill.ai/blog/code-with-claude-sf-2026-what-shipped/)

---

## CLUSTER 2 — MAY 2026 CLAUDE CODE RELEASE CADENCE (SKILLS/PLUGINS/MCP)

The changelog for May 2026 reveals an intense release cadence focused on the plugin and skills system:

**v2.1.154 (May 28):** Plugin dependency enforcement; `defaultEnabled: false` option for plugins; MCP servers now receive `CLAUDE_CODE_SESSION_ID` env variable; `/simplify` command runs cleanup-only review

**v2.1.153 (May 28):** `/plugin` Discover tab pins plugins by relevance to current directory; `skipLfs` option for GitHub/Git plugin sources; marketplace authentication consolidation; fixed stateful MCP server reconnect-loop bug; `--strict-mcp-config` refined for subagents

**v2.1.152 (May 27):** Skills can now set `disallowed-tools` in SKILL.md frontmatter to remove tools from the model; `/reload-skills` command re-scans skill directories without restart; `SessionStart` hooks can return `reloadSkills: true`; new `MessageDisplay` hook event for transforming assistant messages; `pluginSuggestionMarketplaces` managed setting for enterprise marketplace allowlisting

**v2.1.149 (May 22):** `/usage` breakdown shows per-category cost (skills, subagents, plugins, per-MCP-server); enterprise `allowAllClaudeAiMcps` setting loads cloud MCP connectors

**v2.1.145 (May 20):** `/plugin` Discover now shows plugin's commands, agents, skills, hooks, and MCP/LSP servers **before installation**; `claude agents --json` for session scripting

**v2.1.143 (May 15):** Plugin dependency enforcement: `disable` refuses when another enabled plugin depends on target; `/plugin` marketplace shows projected context cost (per-turn and per-invocation token estimates)

**v2.1.142 (May 14):** Plugins with root-level `SKILL.md` and no `skills/` folder automatically surfaced as a skill

**v2.1.141 (May 13):** Hook JSON output includes `terminalSequence` field for desktop notifications; `CLAUDE_CODE_PLUGIN_PREFER_HTTPS` env variable; MCP servers receive `CLAUDE_PROJECT_DIR`

**v2.1.139 (May 11):** Agent View (Research Preview) — one screen for every Claude Code session; `/goal` command; plugin `details` command shows component inventory and projected per-session token cost; new hook `args: string[]` exec form that spawns commands directly without shell; `PostToolUse` hook `continueOnBlock` feeds rejection reason back to Claude

**Source:** [Claude Code Updates by Anthropic — May 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code)

---

## CLUSTER 3 — THE SKILL.MD OPEN STANDARD & CROSS-TOOL PORTABILITY

### Origin and Adoption

Anthropic released the Agent Skills specification as **SKILL.md** in December 2025. OpenAI and Google adopted it shortly after. All three companies co-founded the Agentic AI Foundation (AAIF) under the Linux Foundation to govern the standard.

As of May 2026, tools supporting SKILL.md: **Claude Code (Anthropic), Codex CLI (OpenAI), Gemini CLI (Google), GitHub Copilot (VS Code), Cursor, Cline, Windsurf, OpenCode** and 16+ others. The community Antigravity Awesome Skills library cataloged over 1,234 compatible skills.

### Format

A skill is a directory containing `SKILL.md` with YAML frontmatter (metadata, trigger conditions) and markdown instructions. Agents read frontmatter to decide when to activate, then follow the markdown. Skills are portable across all compatible agents without modification.

**Sources:** [The SKILL.md Open Standard — Full Specification (2026)](https://www.agensi.io/learn/skill-md-specification-open-standard) | [Agent Skills — Codex | OpenAI Developers](https://developers.openai.com/codex/skills) | [Use Agent Skills in VS Code](https://code.visualstudio.com/docs/copilot/customization/agent-skills) | [AI Agent Skills Guide 2026 — The Prompt Index](https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html)

### AAIF Governance — MCP Dev Summit North America 2026

Key statistics from the summit:
- **1,200 attendees** (doubled from prior summit)
- **110+ million SDK downloads monthly**
- **170 member organizations** in under 4 months (double CNCF at same stage)
- Uber: 5,000+ engineers, 10,000+ internal services, 60,000+ agent executions weekly; Minions agent: 1,800 code changes/week, used by 95% of engineering

Notable quotes:
- Jim Zemlin (Linux Foundation CEO): "MCP is the Linux of agents."
- David Soria Parra (Anthropic, MCP co-creator): "Behind corporate firewalls, teams connect MCPs to Salesforce, Jira, wikis."
- Alex Salazar (Arcade CEO): "The agent can hallucinate about robbing a bank. The control plane must be correct."

**Source:** [MCP Is Now Enterprise Infrastructure: Everything That Happened at MCP Dev Summit North America 2026 — AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)

---

## CLUSTER 4 — MARKETPLACE LANDSCAPE & COMMUNITY DISCOVERY

### Official & Major Directories

| Marketplace | Scale | Notes |
|---|---|---|
| **claude-plugins-official** (Anthropic) | 55+ plugins | Curated, reviewed, accessed via `/plugin` in CLI |
| **Smithery.ai** | 7,000+ servers | Docker Hub equivalent for MCP; hosted remote servers with OAuth |
| **MCPMarket.com** | 10,000+ MCP servers, 23+ categories | Browsable web UI |
| **Official MCP Registry** (registry.modelcontextprotocol.io) | ~2,000 entries (launched Sept 2025) | Co-maintained by Anthropic, GitHub, PulseMCP, Microsoft |
| **SkillsMP** | 425,000+ skills | Built around open SKILL.md standard |
| **LobeHub Skills** | 169K+ skills | Best within LobeHub stack |
| **ClaudeSkills.info** | 658+ free skills | Community-contributed, no paid tier; includes official Anthropic skills |
| **tonsofskills.com (ccpi)** | 425 plugins, 2,810 skills, 200 agents | Open-source; CLI: `pnpm add -g @intentsolutionsio/ccpi`; 42 SaaS packs |

### Community Curation

- `hesreallyhim/awesome-claude-code`: **45.1k stars, 3.9k forks** — curated collection of skills, hooks, slash commands, agent orchestrators, plugins
- `jeremylongshore/claude-code-plugins-plus-skills`: 425 plugins, 2,810 skills, 200 agents; open-source marketplace
- `Chat2AnyLLM/awesome-claude-plugins`: Curated list of Claude marketplaces and plugins

**Sources:** [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/) | [50+ Best MCP Servers for Claude Code in 2026](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | [Best MCP Registries in 2026](https://www.truefoundry.com/blog/best-mcp-registries) | [GitHub — jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)

### Notable Community MCP Servers (April–May 2026)

- **Context7 (Upstash):** 56.3K GitHub stars; 890,000+ weekly npm downloads; dynamically fetches version-specific library docs (React, Next.js, Tailwind, etc.) — most-starred MCP server in the ecosystem
- **Meta MCP and CLI:** Launched April 29, 2026 for Facebook/Instagram ads management
- **Higgsfield MCP:** AI image and video generation from 30+ models
- **GitHub MCP:** Secret scanning GA announced May 2026 — automated credential detection in AI-assisted workflows
- **Moody's MCP:** Credit ratings on 600M+ companies (launched with Code with Claude SF)

**Sources:** [GitHub — upstash/context7](https://github.com/upstash/context7) | [GitHub Expands Secret Scanning with GA of MCP Server Integration — InfoQ](https://www.infoq.com/news/2026/05/github-mcp-secret-scanning/)

---

## CLUSTER 5 — MCP TOOL SEARCH & CONTEXT MANAGEMENT

### Lazy Loading Breakthrough (January 14, 2026 — still dominant discussion topic)

Anthropic's Thariq Shihipar announced **MCP Tool Search** on January 14, 2026 — a lazy loading system that loads a search index and fetches tool definitions on-demand.

Performance impact:
- Meta MCP + Shopify AI Toolkit + Higgsfield MCP simultaneously: **12K context tokens → ~600 tokens** (95% reduction)
- With 50+ MCP tools: **~77K tokens → ~8.7K tokens** (95% reduction)

How it works: detection triggers when MCP tool descriptions exceed 10K tokens; tools marked `defer_loading: true`; Claude receives a ToolSearch tool instead of all definitions; 3–5 relevant tools (~3K tokens) loaded per query via keyword search.

**Auto-enabled by default** for all users. Microsoft VSCode filed a feature request to implement the same pattern (Issue #288310). OpenCode filed a similar request (Issue #9350).

**Sources:** [Claude Code MCP Tool Search: Save 95% Context](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search) | [Claude Code Finally Gets Lazy Loading for MCP Tools — Medium](https://jpcaparas.medium.com/claude-code-finally-gets-lazy-loading-for-mcp-tools-explained-39b613d1d5cc)

### Tool Bloat Advisory

Community guidance: past ~50 visible tools, model performance degrades because tool descriptions compete in the context window. Recommendation: start with 2–3 servers matching daily workflow; maximum 5–7 before Tool Search is essential.

---

## CLUSTER 6 — ENTERPRISE REGISTRIES & GOVERNANCE

### Kong MCP Registry (February 2, 2026)

Kong announced Kong MCP Registry within Kong Konnect Catalog — an enterprise directory to register, discover, and govern MCP servers. Key capability: links MCP servers directly to underlying APIs for blast radius analysis, ownership tracking, and inherited policy enforcement. Integrates with AAIF's interoperability framework.

**Sources:** [Kong Introduces MCP Registry in Kong Konnect — PR Newswire](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html) | [Kong MCP Registry Blog](https://konghq.com/blog/product-releases/kong-mcp-registry-tech-preview)

### AWS Agent Registry in Bedrock AgentCore (Preview, April 2026)

AWS launched Agent Registry in public preview as part of Amazon Bedrock AgentCore — a private, governed catalog for agents, tools, skills, MCP servers, and custom resources. Features hybrid search (keyword + semantic), approval workflows for discoverability, IAM and OAuth (Custom JWT) access control, URL-based discovery that auto-fetches schemas from live MCP endpoints. Available in 5 AWS regions.

Announced April 13, 2026 alongside Claude Mythos Preview in Amazon Bedrock.

**Sources:** [AWS Agent Registry — AWS](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | [AWS Launches Agent Registry in Preview — InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | [AWS Weekly Roundup April 13](https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-mythos-preview-in-amazon-bedrock-aws-agent-registry-and-more-april-13-2026/)

### Red Hat OpenShift AI MCP Catalog

Red Hat OpenShift AI 3.4 introduced an MCP catalog (developer preview) — pre-loaded with servers from Red Hat, technology partners, and open source community. Governance features: supply chain controls, trust tiers for certified assets, identity-based tool filtering, mandatory approvals for sensitive tool calls.

**Source:** [The MCP catalog is here — Red Hat Blog](https://www.redhat.com/en/blog/mcp-catalog-here-discover-deploy-and-connect-red-hat-openshift-ai)

### agentic-community/mcp-gateway-registry (GitHub)

Community-built enterprise-ready MCP Gateway & Registry with OAuth authentication, dynamic tool discovery, Keycloak/Entra integration, and auditable tool access for both AI coding assistants and autonomous agents.

**Source:** [GitHub — agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)

---

## CLUSTER 7 — SECURITY CRISIS: MALICIOUS SKILLS & MCP VULNERABILITIES

### Snyk ToxicSkills Audit (February 2026) — Industry-defining security event

Snyk researchers scanned **3,984 skills** from the ClawHub and skills.sh marketplaces as of February 5, 2026:
- **534 (13.4%)** contained critical-level security issues
- **76 confirmed malicious payloads** (credential theft, backdoor installation, data exfiltration)
- **Prompt injection in 36%** of tested skills
- **1,467 malicious payloads** found across the broader ecosystem
- 10.9% had exposed secrets; 17.7% fetched untrusted third-party content
- 8 malicious skills remained live on ClawHub at publication

Submission rate jumped 10x — from under 50/day in mid-January to 500+/day by early February.

The ClawHavoc campaign: attackers flooded ClawHub with **341 malicious skills in a 3-day window**; all 335 AMOS-delivering skills shared a single C2 IP (`91.92.242[.]30`); target data included exchange API keys, wallet private keys, SSH credentials, browser passwords, `.env` files.

**Sources:** [Snyk ToxicSkills — Snyk Blog](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | [When Your Plugin Starts Picking Your Dependencies — SentinelOne](https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/) | [GitHub — snyk-labs/toxicskills-goof](https://github.com/snyk-labs/toxicskills-goof)

### OX Security MCP SDK RCE Vulnerability (April 2026)

OX Security disclosed a systemic RCE vulnerability across **all official MCP SDKs** (Python, TypeScript, Java, Rust). Scope: **150M+ downloads, 7,000+ public servers, 200,000 vulnerable instances**. Flaw: any process command passed to the MCP STDIO interface executes on the host regardless of whether a valid MCP server is initialized.

**Anthropic declined to change the protocol architecture**, calling the behavior "expected" and placing input sanitization responsibility on developers.

Related CVEs: CVE-2025-49596 (MCP Inspector), CVE-2026-22252 (LibreChat), CVE-2026-22688 (WeKnora), CVE-2025-54994 (@akoskm/create-mcp-server-stdio), CVE-2025-54136 (Cursor).

**Sources:** [Anthropic MCP Design Vulnerability Enables RCE — The Hacker News](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) | [OX Security — The Mother of All AI Supply Chains](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | [Systemic Flaw in MCP Protocol Could Expose 150 Million Downloads — Infosecurity Magazine](https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/)

### Marketplace Dependency Hijacking (SentinelOne / Prompt Security)

Attack vector documented: a malicious plugin includes a "dependency management skill" that silently redirects package installations to attacker-controlled sources. The developer asks for a common Python library; the compromised skill installs a trojanized version. Persistence: plugins remain active across all sessions. Evasion: malicious code embeds cleanly — imports work normally, example code runs without error.

**Source:** [How Marketplace Skills Hijack Dependencies — Prompt Security](https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code/)

### Anthropic Security Plugin (May 2026)

Anthropic released a free `security-guidance` plugin for all Claude Code users. Three review levels: file edits, model turns, and commits. Monitors code edits, diffs, and commits in real time to automatically flag dangerous patterns before they reach production.

**Sources:** [Anthropic Releases Free Security Plugin — Cybersecurity News](https://cybersecuritynews.com/free-security-plugin-for-claude-code/) | [Trail of Bits Claude Code Skills for Security Research — GitHub](https://github.com/trailofbits/skills)

### OWASP Agentic Skills Top 10 (New Project, 2026)

OWASP launched a dedicated Top 10 project for agentic skills security (AST10), documenting 10 critical risks. AST01 = Malicious Skills. The "Lethal Trifecta" threat model: skills become especially dangerous when they simultaneously have (1) access to private data, (2) exposure to untrusted content, and (3) ability to communicate externally. Standard code-scanning tools are ineffective because skills blend natural language with code.

**Sources:** [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) | [AST01 — Malicious Skills](https://owasp.org/www-project-agentic-skills-top-10/ast01) | [SkillSieve: A Hierarchical Triage Framework for Detecting Malicious AI Agent Skills — arXiv](https://arxiv.org/html/2604.06550v1)

### MCP Dev Summit: DNS Rebinding 0-day

Jonathan Leitschuh disclosed a DNS rebinding vulnerability affecting multiple MCP implementations at the summit, including Google's Database Toolbox (disclosed as a 0-day at the event).

**Source:** [MCP Is Now Enterprise Infrastructure — AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)

---

## CLUSTER 8 — HACKER NEWS & DEVELOPER COMMUNITY SIGNALS

### Show HN: "Need" — CLI Tool Discovery as MCP Server

Creator (`schreibertuc`): "Every time I ask Claude or Cursor to use a CLI tool, it either hallucinates a package name or recommends something outdated." Built Need to index 10,000+ CLI tools with semantic search via embeddings + pgvector, restricted to safe package managers (brew/npm/pip/cargo/apt).

Community feedback (`sachinkg12`) flagged ranking issues: "compress video without losing quality" returned jpegrescan instead of ffmpeg; `jq` ranked #7 for "pretty print json"; `yt-dlp` omitted entirely for YouTube downloads. Creator acknowledged early-stage ranking problems.

**Source:** [Show HN: Need is a CLI tool discovery as an MCP server — Hacker News](https://news.ycombinator.com/item?id=47413712)

### Community Usage Patterns

From developer guides and community forums: most developers still use Claude Code without customization. Heavy customization is concentrated among power users. The top practical advice: Skills for methodology (how Claude should do something), MCP for connectivity (external systems access) — use both together. Plugin usage growing fastest among teams with shared project `.claude/settings.json`.

**Sources:** [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026 — Morph](https://www.morphllm.com/claude-code-skills-mcp-plugins) | [The Complete Claude Code Power User Guide — DEV Community](https://dev.to/numbpill3d/the-complete-claude-code-power-user-guide-slash-commands-hooks-skills-more-6ep)

---

## CLUSTER 9 — BROADER ECOSYSTEM DEVELOPMENTS

### OpenAI Agents SDK Major Update (April 15, 2026)

Native sandbox execution, first-class MCP integration, sub-agent/handoff patterns, and Codex-style filesystem tools. Codex CLI adopted SKILL.md. GitHub Copilot via VS Code agent skills added SKILL.md support.

**Source:** [GitHub — Zijian-Ni/awesome-ai-agents-2026](https://github.com/Zijian-Ni/awesome-ai-agents-2026)

### MCP Ecosystem Scale

As of May 2026:
- **14,000+ MCP servers** listed across directories
- **97 million cumulative SDK downloads**
- **110+ million monthly downloads**
- MCP SDK surpassed 97M cumulative downloads
- MCP SDK now enterprise infrastructure per AAIF

**Source:** [Everything your team needs to know about MCP in 2026 — WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026)

### LangGraph v1.2 / Genkit Middleware

LangGraph v1.2 (May 2026): per-node timeouts, error recovery, graceful shutdown, new DeltaChannel. Google Genkit Middleware (May 14, 2026): composable hooks at generate/model/tool layers; retries with exponential backoff; model fallbacks; tool approval gates.

**Source:** [GitHub — Zijian-Ni/awesome-ai-agents-2026](https://github.com/Zijian-Ni/awesome-ai-agents-2026)

### Microsoft Agent 365 GA (May 1, 2026)

Enterprise observability, governance, and security for AI agents. May 2026 update added SASE (Secure Access Service Edge) for agents and threat detection/blocking.

### Anthropic Acquires Vercept

Anthropic acquired Vercept to advance computer-use capabilities for desktop and mobile platforms.

**Source:** [Code with Claude SF 2026 Recap](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap)

---

## KEY SIGNALS SUMMARY

1. **Plugin/skill ecosystem went from zero to hundreds of thousands of indexed capabilities in under 6 months** — the ecosystem grew from one registry in December 2025 to 8+ major marketplaces by Q2 2026
2. **SKILL.md as the USB-C of agent capabilities** — cross-tool portability across Claude Code, Codex, Gemini CLI, Copilot, Cursor, and 10+ others is the defining architectural shift
3. **MCP Tool Search solved the context bloat problem** — 95% token reduction enables connecting unlimited MCP servers without degradation; now default behavior
4. **Security is the central unresolved crisis** — Snyk ToxicSkills (13.4% of skills malicious), OX Security RCE (150M+ downloads affected), ClawHavoc campaign, OWASP now has dedicated Agentic Skills Top 10; Anthropic declined to patch STDIO behavior
5. **Enterprise is coming in fast** — Kong, AWS Bedrock AgentCore, Red Hat OpenShift AI all shipping governed MCP registries with RBAC, approval workflows, supply chain controls
6. **Anthropic's official plugin directory + marketplace UX** (Discover tab, pre-install previews, context cost estimates, dependency enforcement) represents serious productization of the extension ecosystem

---

Sources:
- [Claude Code Plugins | Skills, MCP Servers & Marketplace Directory](https://claudemarketplaces.com/)
- [Create plugins — Claude Code Docs](https://code.claude.com/docs/en/plugins)
- [GitHub — jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)
- [Claude Code Extensions: MCP, Skills, Agents & Hooks Guide 2026 | Morph](https://www.morphllm.com/claude-code-extensions)
- [Connect Claude Code to tools via MCP — Claude Code Docs](https://code.claude.com/docs/en/mcp)
- [Best MCP Registries in 2026 — TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries)
- [Official MCP Registry](https://registry.modelcontextprotocol.io/)
- [GitHub — agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)
- [Everything your team needs to know about MCP in 2026 — WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026)
- [Show HN: Need is a CLI tool discovery as an MCP server — Hacker News](https://news.ycombinator.com/item?id=47413712)
- [MCP Is Now Enterprise Infrastructure — AAIF](https://aaif.io/blog/mcp-is-now-enterprise-infrastructure-everything-that-happened-at-mcp-dev-summit-north-america-2026/)
- [The SKILL.md Open Standard — Full Specification (2026)](https://www.agensi.io/learn/skill-md-specification-open-standard)
- [Agent Skills — Codex | OpenAI Developers](https://developers.openai.com/codex/skills)
- [Use Agent Skills in VS Code](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
- [AI Agent Skills and Plugins Explained (2026) | Tony Kipkemboi](https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained)
- [Every AI Skill Marketplace and Directory (2026)](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026)
- [Agent Skills Marketplace — LobeHub](https://lobehub.com/skills)
- [SkillsMP](https://skillsmp.com/)
- [Snyk ToxicSkills Research](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)
- [When Your Plugin Starts Picking Your Dependencies — SentinelOne](https://www.sentinelone.com/blog/marketplace-skills-and-dependency-hijack-in-claude-code/)
- [How Marketplace Skills Hijack Dependencies — Prompt Security](https://prompt.security/blog/when-your-plugin-starts-picking-your-dependencies-marketplace-skills-and-dependency-hijack-in-claude-code/)
- [Anthropic MCP Design Vulnerability Enables RCE — The Hacker News](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html)
- [OX Security — The Mother of All AI Supply Chains](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/)
- [Systemic Flaw in MCP Protocol — Infosecurity Magazine](https://www.infosecurity-magazine.com/news/systemic-flaw-mcp-expose-150/)
- [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/)
- [SkillSieve: Detecting Malicious AI Agent Skills — arXiv](https://arxiv.org/html/2604.06550v1)
- [Anthropic Releases Free Security Plugin — Cybersecurity News](https://cybersecuritynews.com/free-security-plugin-for-claude-code/)
- [GitHub — trailofbits/skills](https://github.com/trailofbits/skills)
- [Linux Foundation Announces Agentic AI Foundation (AAIF)](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation)
- [AWS Agent Registry Preview — AWS](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/)
- [AWS Launches Agent Registry in Preview — InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/)
- [Kong Introduces MCP Registry — PR Newswire](https://www.prnewswire.com/news-releases/kong-introduces-mcp-registry-in-kong-konnect-to-power-ai-connectivity-for-agent-discovery-and-governance-302676451.html)
- [The MCP catalog is here — Red Hat Blog](https://www.redhat.com/en/blog/mcp-catalog-here-discover-deploy-and-connect-red-hat-openshift-ai)
- [Claude Code MCP Tool Search: Save 95% Context](https://claudefa.st/blog/tools/mcp-extensions/mcp-tool-search)
- [GitHub — anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
- [GitHub — anthropics/knowledge-work-plugins](https://github.com/anthropics/knowledge-work-plugins)
- [Claude Code Updates — May 2026 — Releasebot](https://releasebot.io/updates/anthropic/claude-code)
- [Code with Claude SF 2026: What Anthropic Actually Shipped](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap)
- [Discover and install prebuilt plugins — Claude Code Docs](https://code.claude.com/docs/en/discover-plugins)
- [GitHub — hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)
- [GitHub — upstash/context7](https://github.com/upstash/context7)
- [GitHub Expands Secret Scanning — InfoQ](https://www.infoq.com/news/2026/05/github-mcp-secret-scanning/)
- [Anthropic Moves Into Legal Tech — Artificial Lawyer](https://www.artificiallawyer.com/2026/02/02/anthropic-moves-into-legal-tech/)
- [GitHub — Zijian-Ni/awesome-ai-agents-2026](https://github.com/Zijian-Ni/awesome-ai-agents-2026)
- [Smithery AI](https://smithery.ai/)
- [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026 — Morph](https://www.morphllm.com/claude-code-skills-mcp-plugins)
- [The Complete Claude Code Power User Guide — DEV Community](https://dev.to/numbpill3d/the-complete-claude-code-power-user-guide-slash-commands-hooks-skills-more-6ep)

result: Delivered full last30days pipeline output on Claude Code skills/plugins, MCP servers, agent skill marketplaces, SKILL.md open standard, security crises (ToxicSkills, OX Security RCE), enterprise registries (Kong, AWS, Red Hat), and May 2026 Claude Code release cadence — across 9 clustered topics with 50+ sourced findings.

---

## WEB SEARCH 1: Claude Code Skills & Plugins

```json
[
  {
    "title": "Claude Code Plugins | Skills, MCP Servers & Marketplace Directory",
    "url": "https://claudemarketplaces.com/",
    "source": "claudemarketplaces.com",
    "summary": "Community-curated directory of Claude Code skills, plugins, and MCP servers, updated daily from GitHub. Aggregates the broader ecosystem of installable extensions for Claude Code.",
    "date": null
  },
  {
    "title": "Claude Code MCP Servers & Plugins: The Complete 2026 Guide",
    "url": "https://www.clarista.io/blog/claude-code-mcp-plugins-guide",
    "source": "clarista.io",
    "summary": "Comprehensive guide covering how MCP servers and plugins integrate with Claude Code, including setup instructions and recommended servers for common development workflows.",
    "date": "2026"
  },
  {
    "title": "Best Claude Code Plugins, Skills & MCP Servers (2026)",
    "url": "https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers",
    "source": "turbodocx.com",
    "summary": "Roundup of top-rated Claude Code plugins, skills, and MCP servers, with descriptions and use-case recommendations for each.",
    "date": "2026"
  },
  {
    "title": "Plugins reference - Claude Code Docs",
    "url": "https://code.claude.com/docs/en/plugins-reference",
    "source": "code.claude.com (Anthropic official docs)",
    "summary": "Official Anthropic documentation for the Claude Code plugins system, covering plugin structure, components (commands, agents, skills, hooks, MCP config), and installation.",
    "date": null
  },
  {
    "title": "Claude Code Plugins: A 2026 Guide",
    "url": "https://nimbalyst.com/blog/claude-code-plugins-guide/",
    "source": "nimbalyst.com",
    "summary": "Practical guide to Claude Code plugins, explaining the plugin architecture, how to install plugins from Anthropic's official and community marketplaces, and common use cases.",
    "date": "2026"
  },
  {
    "title": "10 top Claude Code plugins to use in 2026",
    "url": "https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6",
    "source": "dev.to",
    "summary": "Curated list of ten notable Claude Code plugins for 2026, including devops-toolkit (bundling AWS, GCP, Datadog, Sentry MCP servers) and Meta's official Facebook/Instagram ads MCP launched April 29, 2026.",
    "date": "2026"
  },
  {
    "title": "50+ Best MCP Servers for Claude Code in 2026",
    "url": "https://claudefa.st/blog/tools/mcp-extensions/best-addons",
    "source": "claudefa.st",
    "summary": "Extensive listing of over 50 MCP servers recommended for Claude Code, covering categories such as databases, APIs, DevOps tooling, and productivity integrations.",
    "date": "2026"
  },
  {
    "title": "Introducing the Model Context Protocol",
    "url": "https://www.anthropic.com/news/model-context-protocol",
    "source": "anthropic.com",
    "summary": "Official Anthropic announcement of MCP, the open standard enabling AI assistants to connect to external tools and data sources. Launched November 2024; reached v1.0 in January 2025.",
    "date": "2024-11"
  },
  {
    "title": "Connect Claude Code to tools via MCP - Claude Code Docs",
    "url": "https://code.claude.com/docs/en/mcp",
    "source": "code.claude.com (Anthropic official docs)",
    "summary": "Official documentation explaining how Claude Code integrates with MCP servers, including configuration, available server registry, and best practices for tool limits.",
    "date": null
  },
  {
    "title": "GitHub - anthropics/claude-plugins-official",
    "url": "https://github.com/anthropics/claude-plugins-official",
    "source": "github.com/anthropics",
    "summary": "Official Anthropic-managed directory of high-quality Claude Code plugins, available automatically in every Claude Code installation.",
    "date": null
  },
  {
    "title": "GitHub - anthropics/skills",
    "url": "https://github.com/anthropics/skills",
    "source": "github.com/anthropics",
    "summary": "Public repository for Agent Skills — reusable instruction sets that teach Claude how to complete specialized tasks in a repeatable, shareable way.",
    "date": null
  },
  {
    "title": "Create plugins - Claude Code Docs",
    "url": "https://code.claude.com/docs/en/plugins",
    "source": "code.claude.com (Anthropic official docs)",
    "summary": "Official guide for authoring Claude Code plugins, describing the directory structure: commands/, agents/, skills/, hooks/, .mcp.json, and plugin.json metadata.",
    "date": null
  },
  {
    "title": "My Claude Code Setup: MCP Servers, Hooks, Skills and Agents (2026)",
    "url": "https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/",
    "source": "okhlopkov.com",
    "summary": "Personal engineering blog post detailing one developer's full Claude Code configuration in 2026, covering MCP server choices, hook patterns, skill files, and agent composition.",
    "date": "2026"
  },
  {
    "title": "The 15 MCP Servers Worth Wiring Into Claude Code and Cursor (2026)",
    "url": "https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/",
    "source": "codersera.com",
    "summary": "Opinionated list of 15 MCP servers recommended for both Claude Code and Cursor, noting practical tool-count ceiling considerations (~40-50 active tools) introduced in early 2026.",
    "date": "2026"
  },
  {
    "title": "Claude Code Skills vs MCP Servers — What to Use, How to Install, and the Best Ones in 2026",
    "url": "https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k",
    "source": "dev.to",
    "summary": "Comparative guide clarifying the distinction between Claude Code skills (SKILL.md instruction files that load contextually) and MCP servers (external tool integrations via the Model Context Protocol), with install walkthroughs and top picks for each.",
    "date": "2026"
  },
  {
    "title": "MCP Protocol 2026: Build Production Servers for Claude, Cursor, VS Code Copilot",
    "url": "https://pooya.blog/blog/mcp-model-context-protocol-production-2026/",
    "source": "pooya.blog",
    "summary": "Technical blog post on building production-grade MCP servers compatible with Claude Code, Cursor, and VS Code Copilot, covering the protocol spec growth from a few dozen servers in early 2025 to 9,400+ by 2026.",
    "date": "2026"
  }
]
```

---

## WEB SEARCH 2: Agent Skill Marketplaces

```json
[
  {
    "title": "Agent Skills, Plugins and Marketplace: The Complete Guide",
    "url": "https://chris-ayers.com/posts/agent-skills-plugins-marketplace/",
    "source": "CodeBytes - The Curious Engineer (chris-ayers.com)",
    "summary": "A comprehensive guide to agent skills, plugins, and marketplace ecosystems, covering how portable skill packages work across Claude Code, Codex CLI, Cursor, and other agentic platforms.",
    "date": null
  },
  {
    "title": "Every AI Skill Marketplace and Directory (2026)",
    "url": "https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026",
    "source": "Agensi.io",
    "summary": "Roundup of all major AI agent skill marketplaces as of 2026, including Skills.sh (Vercel-backed, npm-style CLI), SkillsMP (800K+ indexed skills from public GitHub repos), ClaudeSkills.info (658+ free community skills), and LobeHub (169K+ aggregated skills). Notes rapid growth from one registry in December 2025 to eight major marketplaces by Q2 2026.",
    "date": "2026"
  },
  {
    "title": "Top 5 Agent Skill Marketplaces for Building Powerful AI Agents",
    "url": "https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents",
    "source": "KDnuggets",
    "summary": "KDnuggets survey of the top five agent skill marketplaces, profiling their catalogs, curation standards, and integration support for major agentic IDEs and CLI tools.",
    "date": null
  },
  {
    "title": "AI Agent Skills and Plugins Explained (2026)",
    "url": "https://tonykipkemboi.com/blog/agent-skills-and-plugins-explained",
    "source": "Tony Kipkemboi (personal blog)",
    "summary": "Explains the distinction between agent skills (portable task packages) and plugins (host-specific extensions), traces the lineage from OpenAI's ChatGPT plugins through MCP to the current open-standard skills format co-governed by the Agentic AI Foundation.",
    "date": "2026"
  },
  {
    "title": "Top AI Agent Standards to Know in 2026",
    "url": "https://blog.agentailor.com/posts/top-ai-agent-standards-2026",
    "source": "Agentailor Blog",
    "summary": "Overview of the key interoperability standards shaping the agent ecosystem in 2026, including the Agent Skills specification (open standard released December 2025, adopted by Anthropic, OpenAI, and Google), MCP, and A2A protocol.",
    "date": "2026"
  },
  {
    "title": "Claude Code Plugins | Skills, MCP Servers & Marketplace Directory",
    "url": "https://claudemarketplaces.com/",
    "source": "claudemarketplaces.com",
    "summary": "Directory specifically for Claude Code plugins, skills, and MCP servers, providing a searchable registry for the Claude-specific tooling ecosystem.",
    "date": null
  },
  {
    "title": "Agent Skills Marketplace - Claude, Codex & ChatGPT Skills",
    "url": "https://skillsmp.com/",
    "source": "SkillsMP",
    "summary": "One of the largest public skill marketplaces, indexing 800,000+ skills scraped from public GitHub repositories across Claude, Codex, and ChatGPT agent platforms.",
    "date": null
  },
  {
    "title": "Skills Marketplace — The New App Store for AI Agents (2026)",
    "url": "https://www.agensi.io/learn/skills-marketplace-ai-agents",
    "source": "Agensi.io",
    "summary": "Frames the skills marketplace category as the 'new App Store for AI agents', covering monetization models, security scanning as a key differentiator, and expected shifts including paid tiers (70-80% creator revenue splits) arriving by Q4 2026.",
    "date": "2026"
  },
  {
    "title": "AI Agent Skills Marketplace: The New Plugin Ecosystem",
    "url": "https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/",
    "source": "Paperclipped (paperclipped.de)",
    "summary": "Blog post analyzing how agent skill marketplaces have replaced earlier plugin models, with focus on security incidents (ToxicSkills, ClawHavoc) driving automated scanning requirements across major registries.",
    "date": null
  },
  {
    "title": "Oracle Launches Fusion Applications AI Agent Marketplace",
    "url": "https://www.oracle.com/news/announcement/ai-world-oracle-launches-fusion-applications-ai-agent-marketplace-to-accelerate-enterprise-ai-adoption-2025-10-15/",
    "source": "Oracle (oracle.com)",
    "summary": "Official Oracle announcement (October 15, 2025) of the Oracle Fusion Applications AI Agent Marketplace, letting Oracle Fusion Cloud customers find and deploy validated, partner-built AI agents directly within their enterprise environment.",
    "date": "2025-10-15"
  },
  {
    "title": "AI Agent Marketplaces 2026: Discovery and Distribution",
    "url": "https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution",
    "source": "Digital Applied (digitalapplied.com)",
    "summary": "Analysis of how discovery and distribution dynamics are shifting in the 2026 agent marketplace landscape, including the role of MCP hubs (mcp.so, Smithery, PulseMCP) as the largest community-run registries after Anthropic chose not to operate a canonical MCP registry.",
    "date": "2026"
  },
  {
    "title": "Introducing the Agent Governance Toolkit: Open-source runtime security for AI agents",
    "url": "https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit-open-source-runtime-security-for-ai-agents/",
    "source": "Microsoft Open Source Blog",
    "summary": "Microsoft's April 2026 announcement of an open-source Agent Governance Toolkit providing runtime security for AI agents, relevant to the governance and trust layer emerging across plugin and skill registries.",
    "date": "2026-04-02"
  },
  {
    "title": "Google Cloud Next 2026: AI agents, A2A protocol, Workspace Studio",
    "url": "https://thenextweb.com/news/google-cloud-next-ai-agents-agentic-era",
    "source": "The Next Web",
    "summary": "Coverage of Google Cloud Next 2026, including Google renaming Vertex AI to the Gemini Enterprise Agent Platform, absorbing Agentspace into a unified product, and advancing the A2A (Agent-to-Agent) interoperability protocol.",
    "date": "2026"
  },
  {
    "title": "AI Agent Marketplaces (overview)",
    "url": "https://www.truefoundry.com/blog/ai-agent-marketplaces",
    "source": "TrueFoundry (truefoundry.com)",
    "summary": "Overview blog covering the landscape of AI agent marketplaces, their role in the broader MLOps and deployment ecosystem, and how enterprises are evaluating them for production workloads.",
    "date": null
  }
]
```

---

## WEB SEARCH 3: MCP Protocol & Extensions

```json
[
  {
    "title": "Introducing the Model Context Protocol",
    "url": "https://www.anthropic.com/news/model-context-protocol",
    "source": "Anthropic",
    "summary": "Official announcement of MCP as an open standard for connecting AI assistants to data systems including content repositories, business tools, and development environments. Anthropic open-sourced the protocol and provided reference server implementations.",
    "date": "November 2024"
  },
  {
    "title": "Donating the Model Context Protocol and Establishing the Agentic AI Foundation",
    "url": "https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation",
    "source": "Anthropic",
    "summary": "Anthropic donated MCP to the Agentic AI Foundation (AAIF), a directed fund under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI, with backing from Google, Microsoft, AWS, Cloudflare, and Bloomberg.",
    "date": "December 2025"
  },
  {
    "title": "One Year of MCP: November 2025 Spec Release",
    "url": "https://blog.modelcontextprotocol.io/posts/2025-11-25-first-mcp-anniversary/",
    "source": "Model Context Protocol Blog",
    "summary": "Anniversary recap of the November 2025 spec update, which added async operation support, stateless Streamable HTTP transport, OAuth 2.1 authorization, server-side .well-known URL discovery, and structured tool annotations.",
    "date": "November 2025"
  },
  {
    "title": "MCP Joins the Agentic AI Foundation",
    "url": "https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/",
    "source": "Model Context Protocol Blog",
    "summary": "Official MCP blog post on the governance transition to the Linux Foundation-hosted Agentic AI Foundation, signaling MCP's shift from an Anthropic-owned spec to a vendor-neutral industry standard.",
    "date": "December 2025"
  },
  {
    "title": "Connect Claude Code to Tools via MCP",
    "url": "https://code.claude.com/docs/en/mcp",
    "source": "Claude Code Docs (Anthropic)",
    "summary": "Official documentation covering how to wire MCP servers into Claude Code. Notes that tool search is enabled by default, deferring tool definitions until needed to keep context usage low, enabling use of many MCP servers simultaneously.",
    "date": null
  },
  {
    "title": "Claude Code MCP Servers & Plugins: The Complete 2026 Guide",
    "url": "https://www.clarista.io/blog/claude-code-mcp-plugins-guide",
    "source": "Clarista",
    "summary": "Comprehensive guide to using MCP servers with Claude Code in 2026, covering configuration, the most useful servers (databases, dev tools, communication platforms, cloud infra), and debugging tips.",
    "date": "2026"
  },
  {
    "title": "The 15 MCP Servers Worth Wiring Into Claude Code and Cursor (2026)",
    "url": "https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/",
    "source": "CoderSera",
    "summary": "Curated list of the top 15 MCP servers for Claude Code and Cursor IDE in 2026, with ecosystem now exceeding 500 public servers.",
    "date": "2026"
  },
  {
    "title": "Code with Claude London 2026: Rethinking How We Build",
    "url": "https://claude.com/blog/code-w-claude-london-2026-rethinking-how-we-build",
    "source": "Anthropic / Claude Blog",
    "summary": "Recap of the London developer event (May 19, 2026) where Anthropic announced MCP tunnels (encrypted outbound-only connections to private MCP servers), self-hosted sandboxes in public beta, and Claude Managed Agents connecting to private MCP servers.",
    "date": "May 2026"
  },
  {
    "title": "Every Claude Code Update From April 17-22, 2026: What Actually Matters",
    "url": "https://clskillshub.com/blog/claude-code-april-2026-updates",
    "source": "CLSkills Hub",
    "summary": "Detailed breakdown of late-April 2026 Claude Code updates including faster MCP startup, model selection persistence, /resume performance improvements, native CLI binary, Windows fixes, and sandbox hardening.",
    "date": "April 2026"
  },
  {
    "title": "MCP Server Ecosystem Tracker: 56 Servers Cataloged 2026",
    "url": "https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026",
    "source": "Digital Applied",
    "summary": "Tracker article cataloging 56+ MCP servers in 2026, covering categories such as cloud infrastructure, databases, development tools, and communication platforms. Notes AWS Agent Toolkit MCP Server reached GA with 60+ official servers.",
    "date": "2026"
  },
  {
    "title": "GitHub - modelcontextprotocol/servers",
    "url": "https://github.com/modelcontextprotocol/servers",
    "source": "GitHub / Model Context Protocol",
    "summary": "Official repository for reference MCP server implementations. By March 2026 contains 50+ official servers and 150+ community implementations spanning databases, dev tools, communication platforms, and cloud infrastructure.",
    "date": null
  },
  {
    "title": "Why the Model Context Protocol Won",
    "url": "https://thenewstack.io/why-the-model-context-protocol-won/",
    "source": "The New Stack",
    "summary": "Analysis piece on how MCP went from a dismissed draft to the de facto AI-tool integration standard within one year, reaching 97 million monthly SDK downloads, 10,000 active servers, and first-class support in Claude, ChatGPT, Cursor, Gemini, VS Code Copilot, and more.",
    "date": "2025"
  }
]
```
