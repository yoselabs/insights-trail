# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-07
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web (blogs, news, official docs, security research)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 0 threads | — | API 403 – domain blocked to crawler |
| X/Twitter | 0 posts | — | Domain blocked to crawler |
| YouTube | 0 videos | — | Referenced in web sources but not fetched |
| Hacker News | 1 story | 738 points, ~200 comments | High signal; "Claude Skills are awesome, maybe a bigger deal than MCP" |
| TikTok | 0 videos | — | No data returned |
| Instagram | 0 reels | — | No data returned |
| Bluesky | 0 posts | — | No data returned |
| Polymarket | 0 markets | — | No data returned |
| GitHub | 7 repos | 20.6k★ (top repo) | Direct fetches: VoltAgent/awesome-agent-skills, vercel-labs/skills, jeremylongshore/claude-code-plugins-plus-skills, alirezarezvani/claude-skills, shinpr/sub-agents-skills, agentic-community/mcp-gateway-registry, kenhuangus/agentic-skills-top-10 |
| Web | 80+ pages | — | 10 search queries + 8 direct fetches; blogs, news, official docs, security advisories |

---

## Synthesized Findings

### 1. The Agent Skills Open Standard: Anthropic's MCP Playbook, Replayed

On **October 16, 2025**, Anthropic announced Claude Skills. On **December 18, 2025**, it published the full open specification — a "deliciously tiny specification" (Simon Willison's phrase) requiring only two mandatory YAML fields and Markdown instructions. The intent was transparent: replicate the ecosystem dynamics that turned MCP into an industry standard, but at the application layer.

The bet paid off fast. Within **48 hours** of the open spec, Microsoft (VS Code, GitHub Copilot) and OpenAI (Codex CLI) shipped support. By **February 5, 2026**, AWS Kiro IDE joined. By **March 2026**, 32 tools from competing companies — Google Gemini CLI, JetBrains Junie, Block's Goose, Snowflake, Databricks, Mistral AI, Sourcegraph Amp — all read the same `SKILL.md` files from the same directory structure.

The core format: a directory with a `SKILL.md` containing YAML frontmatter (`name`, `description`) and markdown instructions, plus optional supporting scripts and reference files. Write a skill once; it runs unchanged in Claude Code, Codex, Gemini CLI, Cursor, GitHub Copilot, and 28+ other platforms.

Simon Willison characterized the approach as a "deliciously tiny specification — the entire format requires only two mandatory YAML fields and Markdown instructions, making implementation feasible in approximately one day for any engineering team."

**Sources:** [Anthropic engineering blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [VentureBeat announcement](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) · [Paperclipped interoperability guide](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) · [agensi.io explainer](https://www.agensi.io/learn/agent-skills-open-standard) · [AI Business](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) · [TechRadar](https://www.techradar.com/pro/anthropic-takes-the-fight-to-openai-with-enterprise-ai-tools-and-theyre-going-open-source-too) · [Subramanya N analysis](https://subramanya.ai/2025/12/18/agent-skills-the-missing-piece-of-the-enterprise-ai-puzzle/) · [Open Data Science](https://opendatascience.com/anthropic-introduces-agent-skills-making-claude-smarter-faster-and-more-specialized/) · [Off The Grid XP Substack](https://offthegridxp.substack.com/p/the-genius-of-anthropics-claude-agent-skills-2025)

**Platforms:** Web (news/blogs); Hacker News (adjacent)

---

### 2. Skills.sh: The npm Moment for Agent Capabilities

On **January 20, 2026**, Vercel launched **[skills.sh](https://skills.sh/)** — a package directory, leaderboard, and CLI for agent skill packages. The positioning was explicit: Skills are like npm, but instead of JavaScript libraries, you're installing capabilities that your AI agent can execute on your behalf.

The growth curve was steep:
- Within 6 hours of launch: top skill hit **20,000+ installs**; Stripe shipped their own skills within hours
- By February 17: Vercel Labs' `find-skills` utility: **235,000+ weekly installs**; ecosystem growing at **147 new skills daily**
- By March 2026: total ecosystem at ~4,257+ skills; `find-skills` at **579,000+ total installs** (leaderboard top slot)
- May 2026: broader aggregators count **4,200+ skills**, 770+ MCP servers, 2,500+ marketplace listings

The CLI install path: `npx skills add vercel-labs/agent-skills`. The spec homepage: [agentskills.io](https://agentskills.io). On **February 17, 2026**, Snyk joined as a security partner, integrating automated auditing into the installer so every `npx skills add` gets a security scan before execution.

**Sources:** [Vercel launch announcement](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [vercel-labs/skills GitHub](https://github.com/vercel-labs/skills) · [Vercel docs](https://vercel.com/docs/agent-resources/skills) · [skills.sh homepage](https://skills.sh/) · [find-skills package](https://skills.sh/vercel-labs/skills/find-skills) · [Snyk/Vercel security partnership](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) · [toolworthy.ai review](https://www.toolworthy.ai/tool/skills-sh) · [virtualuncle guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) · [npm package](https://www.npmjs.com/package/skills)

**Platforms:** Web (blogs/news); GitHub

---

### 3. How Skills, MCP, and Plugins Actually Fit Together

A consistent three-layer taxonomy has emerged across developer writing and official docs:

- **Skills (Layer 1 — Procedural Knowledge):** Teach Claude *how* to perform procedures. Filesystem-based `SKILL.md` files. Consume only 30-50 tokens per skill until activated (progressive disclosure). Cross-platform.
- **MCP Servers (Layer 2 — External Connectivity):** Connect Claude to external systems — databases, APIs, GitHub, Shopify. Consume substantial context (typical 5-server setup: 55,000+ tokens), though Claude Code's Tool Search feature reduces this by ~85%. Real-time data access and executable actions.
- **Plugins (Layer 3 — Distributable Bundles):** Package skills, commands, hooks, and MCP configs into one installable unit. Enable team standardization and marketplace sharing. Token cost = sum of all components.

As the devtoolpicks.com guide puts it: "MCP is the plumbing connecting Claude to the outside world; Skills are the instructions teaching Claude how to do specific things; and Plugins are the finished product bundling both together — they are three layers of the same stack."

Official Claude Code docs describe three progressive context levels for skills:
1. Metadata (name + description) loaded at startup (~100 tokens/skill)
2. Full SKILL.md loaded when Claude determines relevance
3. Supporting files (reference docs, scripts) loaded as needed

The key frontmatter fields: `name`, `description`, `context` (fork for subagent), `disable-model-invocation`, `allowed-tools`, `model`, `effort`, `hooks`, `paths`. Dynamic context injection via `!`command`` syntax runs shell commands inline before skill content reaches Claude.

**Sources:** [morphllm.com three-layer guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [Official Claude Code skills docs](https://code.claude.com/docs/en/skills) · [devtoolpicks taxonomy](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) · [alexop.dev full-stack explainer](https://alexop.dev/posts/understanding-claude-code-full-stack/) · [Augment Code SDK guide](https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities) · [Claude Agent SDK docs](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [nimbalyst.com plugins guide](https://nimbalyst.com/blog/claude-code-plugins-guide/) · [nimbalyst.com skills guide](https://nimbalyst.com/blog/claude-code-skills-guide/)

**Platforms:** Web; Hacker News (commentary)

---

### 4. The MCP Registry Ecosystem: From Wild West to Governed Infrastructure

The **official MCP Registry** ([registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io)) launched in preview on **September 8, 2025**, backed by Anthropic, GitHub, PulseMCP, and Microsoft. API freeze (v0.1) was reached October 24, 2025. The broader ecosystem at registry time:

- **Smithery**: 7,000+ MCP servers — the "Docker Hub" of MCP
- **MCPMarket.com**: 10,000+ MCP servers, 23+ categories, community-curated with web UI
- **Kong MCP Registry**: enterprise governance — single source of truth for every AI tool, integrated with existing API security/identity/observability stacks
- **MACH Alliance MCP Registry**: central directory for MACH-compliant MCP servers for discovery by AI agents and IDE plugins
- **agentic-community/mcp-gateway-registry**: OAuth, dynamic tool discovery, Keycloak/Entra/Microsoft Entra integration, audit trails for enterprise AI coding teams

The developer conversation matured from "can my agent access external tools?" to "which MCP server should I use for Home Assistant?" — a signal that the protocol has commoditized, and *discovery and governance* are the new bottlenecks.

On **April 29, 2026**, Meta launched the **Meta Ads AI Connectors** in open beta: an MCP server at `mcp.facebook.com/ads` providing 29 tools for campaigns, catalogs, benchmarks, and tracking — plus a CLI companion. Auth is direct between user and Meta (no third-party). Supported by ChatGPT and Claude at launch.

**Sources:** [Official MCP Registry](https://registry.modelcontextprotocol.io/) · [MCP Registry launch blog](https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/) · [truefoundry MCP registries comparison](https://www.truefoundry.com/blog/best-mcp-registries) · [Kong MCP Registry](https://konghq.com/products/mcp-registry) · [MACH Alliance MCP Registry](https://machalliance.org/mach-alliance-mcp-registry) · [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) · [tokenmix.ai MCP directory](https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory) · [Microsoft Learn MCP tools](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) · [Azure Foundry MCP guide](https://learn.microsoft.com/en-us/azure/foundry/mcp/build-your-own-mcp-server) · [MCP.io registry about](https://modelcontextprotocol.io/registry/about) · [MCP registry info](https://modelcontextprotocol.info/tools/registry/) · [Meta Ads MCP overview](https://mcp.directory/blog/meta-ads-cli-mcp) · [Meta official AI connectors](https://www.facebook.com/business/help/1456422242197840) · [Official Meta Ads MCP 29 tools](https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026) · [Digiday Meta MCP](https://digiday.com/marketing/meta-opens-its-ad-ecosystem-to-third-party-ai-tools/) · [commonthreadco Meta MCP](https://commonthreadco.com/blogs/coachs-corner/meta-ai-mcp-cli-ads-connectors-ecommerce) · [pipeboard-co meta-ads-mcp](https://github.com/pipeboard-co/meta-ads-mcp) · [Ryze Meta MCP guide](https://www.get-ryze.ai/blog/meta-facebook-ads-mcp-server-connector) · [best MCP for Meta Ads](https://www.get-ryze.ai/blog/best-mcp-for-meta-ads) · [meta ads official mcp cli launch](https://www.get-ryze.ai/blog/meta-ads-official-mcp-cli-launch) · [adkit.so Meta MCP](https://adkit.so/features/ads-mcp/meta) · [MCP Wikipedia](https://en.wikipedia.org/wiki/Model_Context_Protocol) · [codeongrass MCP ecosystem](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/)

**Platforms:** Web; GitHub

---

### 5. Hacker News: Skills as the Better MCP?

The HN thread "[Claude Skills are awesome, maybe a bigger deal than MCP](https://news.ycombinator.com/item?id=45619537)" (738 points, by weinzierl) was the highest-signal developer community discussion in this window. Key debate lines:

**Pro-skills argument (tptacek, simonw):** Skills solve MCP's core weakness — "context pollution." MCP frontloads tools into the context window; skills use progressive disclosure. tptacek: "tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones." Simon Willison (simonw) pushed back on the "this is just formalized markdown files" critique: "formalization matters — giving patterns names enables better discourse and enables Claude Code to auto-scan YAML metadata for skill discovery."

**Skepticism (causal, primer42):** "This simply formalizes existing practices — keeping markdown context files alongside CLI tools." emn13 offered a more nuanced read: these aren't timeless documentation but "battle-tested action plans solving acute, real concerns right away."

**Broader implications:** michael1999 identified three reasons LLM-friendly documentation now thrives: (1) immediate feedback loops (minutes vs years), (2) tooling makes it easier, (3) personal incentive ("harness a computer minion") beats altruism. TeMPOraL captured the consumer-side dynamic: "I don't want AI in your product — I want AI of my choice to use your product for me." The thread produced a sharp quote from quentindanjou: architecture and clear communication, not coding, become the human bottleneck.

**Sources:** [HN thread (738pts)](https://news.ycombinator.com/item?id=45619537) · [Developer Digest HN analysis](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) · [codewithandrea January 2026 newsletter](https://codewithandrea.com/newsletter/january-2026/) · [getbeam.dev skills ecosystem guide](https://getbeam.dev/blog/claude-code-skills-ecosystem-guide.html) · [The New Stack analysis](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)

**Platforms:** Hacker News; Web

---

### 6. Enterprise Plugin Push: Anthropic's Vertical Attack on SaaS

On **February 24, 2026**, Anthropic unveiled its enterprise agents program ([TechCrunch](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/)): 11 official Plugins covering Finance (market research, competitive analysis, financial modeling), HR (job descriptions, onboarding, offer letters), Legal, Sales, Marketing, and Data Analysis. The launch included:

- Private software marketplaces for controlled enterprise deployment
- Centralized admin controls for IT
- New enterprise connectors: Gmail, DocuSign, Clay
- Partner-built plugins at launch: Atlassian, Canva, Cloudflare, Figma, Notion, Ramp, Sentry

The strategic framing was candid. Kate Jensen (Anthropic Head of Americas): *"2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature."* Matt Piccolella (Product Officer): *"We believe that the future of work means everybody having their own custom agent."*

**April 9, 2026:** Claude Cowork went generally available on macOS and Windows — with analytics, OpenTelemetry, and RBAC for enterprise teams.
**April 14, 2026:** Anthropic introduced Routines in research preview — cloud-hosted automation that runs even when your laptop is closed.

**Sources:** [TechCrunch Feb 2026 enterprise launch](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [claudepluginhub.com MCP guide](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code) · [findskill.ai Cowork guide](https://findskill.ai/blog/claude-cowork-guide/) · [Prismatic Skills release](https://www.devopsdigest.com/prismatic-skills-for-claude-code-released) · [TurboDocx guide](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) · [claudefa.st changelog](https://claudefa.st/blog/guide/changelog) · [official changelog](https://code.claude.com/docs/en/changelog) · [releasebot Anthropic](https://releasebot.io/updates/anthropic) · [releasebot Claude Code](https://releasebot.io/updates/anthropic/claude-code)

**Platforms:** Web (news/analysis)

---

### 7. Security Crisis: The Agent Skills Supply Chain Is Under Active Attack

The maturation of the skill ecosystem created a new attack surface, and Q1–Q2 2026 saw it exploited at scale:

**ClawHavoc campaign** (first reported late January 2026): 341 malicious skills found on ClawHub (an OpenClaw skills registry) — follow-up analysis expanded to **1,184 compromised packages**. Five of the seven most-downloaded skills at peak infection were confirmed malware.

**Snyk's ecosystem audit** (February 2026, 3,984 skills analyzed):
- 36.82% of all skills contain ≥1 security flaw
- 13.4% contain ≥1 critical-level issue
- Vulnerabilities: indirect prompt injection, suspicious downloads, insecure credential handling, third-party content exposure

**OX Security's MCP architectural finding:** A critical, systemic vulnerability in the MCP core architecture enables RCE on any system running a vulnerable MCP implementation. Scale: 150M+ downloads, 7,000+ public servers, up to 200,000 vulnerable instances. Anthropic declined to modify the protocol architecture, calling the behavior "expected." Vendors issued patches; the reference implementation remains unpatched.

**Trend Micro (February 2026):** 8,000+ MCP servers on the public internet; 492 with zero auth and zero traffic encryption.

**CVE volume:** January–February 2026 alone: 30+ CVEs targeting MCP; 43% were shell injections.

**OWASP response — dual frameworks:**
- **OWASP MCP Top 10** (2025, beta): protocol layer risks
- **OWASP Agentic Skills Top 10 (AST10)** published **April 27, 2026**: skill content layer risks; incubated at OWASP Project Summit in Oslo 2026

The threat model is structurally novel. Snyk's framing: "When you run `npx skills add <package>`, you're not just installing a library...it's code *and* natural language instructions that an autonomous agent will interpret and act on." Three unique risks: (1) expanded blast radius (skills inherit agent permissions: filesystem, shell, API keys, cloud infra); (2) NLP as attack vector (prompt injection, "toxic flows"); (3) inverted trust model (agent autonomously decides execution without human decision-making in the loop).

**Sources:** [The Hacker News MCP RCE](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) · [OX Security supply chain advisory](https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/) · [OX Security "Mother of All AI Supply Chains"](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) · [VentureBeat OpenClaw backdoor](https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner) · [Snyk/Vercel security blog](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) · [Snyk top Claude skills](https://snyk.io/articles/top-claude-skills-developers/) · [CyberDesserts AI agent security](https://blog.cyberdesserts.com/ai-agent-security-risks/) · [Practical DevSecOps MCP vulns](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) · [Obot.ai supply chain](https://obot.ai/blog/mcp-security-agent-skills-supply-chain/) · [Rock Cyber Musings supply chain](https://www.rockcybermusings.com/p/agent-supply-chain-attacks-scanner-switched-sides) · [Aembit MCP security guide](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/) · [MSSP Alert OWASP MCP 10](https://www.msspalert.com/native/owasp-mcp-10-external-aiexposures-you-must-prioritize-in-2026) · [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) · [OWASP MCP Top 10](https://owasp.org/www-project-mcp-top-10/) · [OWASP Top 10 Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) · [Practical DevSecOps OWASP MCP Top 10](https://www.practical-devsecops.com/owasp-mcp-top-10/) · [DeepTeam OWASP agents](https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications) · [Gravitee OWASP review](https://www.gravitee.io/blog/owasp-top-10-for-agentic-applications-2026-a-practical-review-and-how-gravitee-supports-secure-agentic-architecture) · [SecOps OWASP analysis](https://secops.group/blog/securing-agentic-ai-the-owasp-top-10-and-beyond/) · [Agat Software CISO guide](https://agatsoftware.com/blog/owasp-agentic-top-10-2026-ciso-guide/) · [kenhuangus/agentic-skills-top-10](https://github.com/kenhuangus/agentic-skills-top-10)

**Platforms:** Web (security research); GitHub

---

### 8. GitHub: Community-Built Skill Repositories Exploding

The open standard's portability created an immediate explosion in community skill collections:

**[VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills)** (20,600★): The most-starred curated collection — "hand-picked, not AI-slop generated." 1,100+ skills. Official sets from Anthropic, Microsoft (133 skills across 6 languages), OpenAI (29), Sentry (39 for observability workflows), Google, Stripe, Cloudflare, Figma, Hugging Face, AWS, Azure, Vercel. Trail of Bits contributed 22 security-focused skills. 342 commits, 10 open PRs.

**[jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)** (2,100★): 425 plugins, 2,810 skills, 200 agents across 18 categories. Open-source marketplace at tonsofskills.com. CLI: `pnpm add -g @intentsolutionsio/ccpi && ccpi install <pack>`. 339+ npm downloads in last 30 days.

**[alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills)** (232+ skills): Engineering, marketing, product, compliance, C-level advisory coverage. Compatible with Claude Code, Codex, Gemini CLI, Cursor, 8 more agents.

**[shinpr/sub-agents-skills](https://github.com/shinpr/sub-agents-skills)**: Cross-LLM sub-agent orchestration as an Agent Skills package — routes tasks to Codex, Claude Code, Cursor, or Gemini from any compatible tool.

**[agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry)**: Enterprise MCP gateway with OAuth, dynamic tool discovery, unified access, Keycloak/Entra integration, audit trails.

**[vercel-labs/skills](https://github.com/vercel-labs/skills)**: The open agent skills CLI tool powering skills.sh.

**Sources:** [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) · [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · [shinpr/sub-agents-skills](https://github.com/shinpr/sub-agents-skills) · [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) · [vercel-labs/skills](https://github.com/vercel-labs/skills) · [Codex CLI skills guide](https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026) · [best Codex CLI skills](https://www.agensi.io/learn/best-codex-cli-skills-2026) · [Gemini CLI skills install](https://www.agensi.io/learn/install-skills-gemini-cli-guide) · [Gemini CLI skills paths](https://www.agensi.io/learn/where-are-gemini-cli-skills-stored) · [Serenitiesai 16 AI tools guide](https://serenitiesai.com/articles/agent-skills-guide-2026) · [Gemini CLI guide](https://alirezarezvani.github.io/claude-skills/guides/gemini-cli-skills-guide/)

**Platforms:** GitHub; Web

---

### 9. MCP 2026 Roadmap: Production-Scale Connectivity Layer

The MCP roadmap is shifting from "establishing the need for a standard" to "making it reliable enough for production-scale agentic systems." Key items confirmed for 2026:

- **Stateless Transport** (June 2026 target): enable MCP servers as stateless web services behind load balancers
- **Server Discovery**: "MCP Server Cards" via `.well-known` URLs — agents discover capabilities without opening connections
- **Enterprise Auth**: SSO integration (Google Workspace, Okta), audit trails, authorization propagation
- **Triggers**: webhook-like event-driven updates with ordering guarantees
- **Skills Over MCP**: domain-specific instructions bundled with tools
- **SDK v2** (Python & TypeScript): better ergonomics, conformance test suites
- **Progressive Discovery / Tool Search**: defer tool loading to reduce context bloat (building on the 85% reduction already achieved)
- **Agent-Native Server Design**: shift from API wrapping to workflow-oriented design

**Sources:** [MCP 2026 Roadmap (tedt.org)](https://tedt.org/MCPs-2026-Roadmap/) · [MCP Registry homepage](https://registry.modelcontextprotocol.io/) · [MCP Registry docs](https://registry.modelcontextprotocol.io/docs) · [MCP registry preview (InfoQ)](https://www.infoq.com/news/2025/09/introducing-mcp-registry/) · [MCP registry info blog](https://modelcontextprotocol.info/blog/mcp-registry-preview/) · [modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry)

**Platforms:** Web

---

### 10. Claude Code April–May 2026: Recent Product Changes

In the last 30 days, Claude Code shipped several skills/plugin-relevant improvements:

- `/skills` menu: type-to-filter search box for long skill lists
- `claude plugin prune`: removes orphaned auto-installed plugin dependencies
- `alwaysLoad` MCP server config option: skip tool-search deferral for always-on servers
- `claude ultrareview [target]` subcommand: run the `/ultrareview` skill non-interactively from CI/scripts
- PostToolUse hooks can now replace tool output for *all* tools via `hookSpecificOutput.updatedToolOutput`
- Windows: Git Bash no longer required; PowerShell now usable as shell tool in skills
- April 14: Routines in research preview — cloud-hosted automation running off-device
- April 9: Claude Cowork GA (macOS/Windows) with analytics, OpenTelemetry, RBAC
- Prismatic Skills for Claude Code: new open-source plugin enabling faster integration shipping

**Sources:** [releasebot Claude Code May 2026](https://releasebot.io/updates/anthropic/claude-code) · [releasebot Anthropic May 2026](https://releasebot.io/updates/anthropic) · [official Claude Code changelog](https://code.claude.com/docs/en/changelog) · [GitHub releases anthropics/claude-code](https://github.com/anthropics/claude-code/releases) · [claudefa.st changelog](https://claudefa.st/blog/guide/changelog) · [support release notes](https://support.claude.com/en/articles/12138966-release-notes) · [Prismatic Skills DevOpsDigest](https://www.devopsdigest.com/prismatic-skills-for-claude-code-released) · [mejba top 10 Claude Code tools](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026)

**Platforms:** Web

---

### 11. Popular Skills Content and Discovery Guides

A wave of "best skills" listicle/guide content appeared in the last 30 days, signaling mainstream developer interest:

- [Jonathan Fulton — "Agent Skills: The Cheat Codes for Claude Code" (Apr 2026, Medium)](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d)
- [unicodeveloper — "10 Must-Have Skills for Claude and Any Coding Agent in 2026" (Mar 2026, Medium)](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051)
- [Composio — "Top 10 Claude Code Skills Every Builder Should Know in 2026"](https://composio.dev/content/top-claude-skills)
- [Firecrawl — "Best Claude Code Skills to Try in 2026"](https://www.firecrawl.dev/blog/best-claude-code-skills)
- [claudefa.st — "50+ Best MCP Servers for Claude Code in 2026"](https://claudefa.st/blog/tools/mcp-extensions/best-addons)
- [DEV Community — "Best Claude Code Skills & Plugins (2026 Guide)"](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4)
- [Snyk — "Top 8 Claude Skills for Developers"](https://snyk.io/articles/top-claude-skills-developers/)
- [skywork.ai — "Anthropic Skills vs Custom Skills (2025): Capabilities Compared"](https://skywork.ai/blog/ai-agent/anthropic-skills-vs-custom-skills-2025-comparison/)
- [arXiv 2604.14228 — "Dive into Claude Code: The Design Space of AI Agent Systems"](https://arxiv.org/html/2604.14228v1)
- [claudemarketplaces.com](https://claudemarketplaces.com/) · [claudepluginhub.com](https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code)

**Platforms:** Web

---

## Cross-Source Patterns

### Pattern 1: Skills Are Winning the Context-Efficiency War Against MCP

**Signal strength:** Very strong (Hacker News 738pts + multiple web sources)

Skills' progressive disclosure model (30-50 tokens per skill until invoked) vs. MCP's frontloaded context (55,000+ tokens for 5 servers) is the dominant technical argument for the skills-first approach. The HN thread made this concrete and contentious. tptacek: "MCP is just one means to that end, and not one of the better ones." The Tool Search feature in Claude Code (85% context reduction for MCP) is a partial response, but developers are increasingly structuring domain knowledge as skills rather than MCP tools when they have the choice.

**Platforms:** Hacker News, Web (morphllm, devtoolpicks, getbeam)

---

### Pattern 2: Cross-Platform Portability Is the Killer Feature

**Signal strength:** Strong (32 tool adopters, multiple guides per platform)

The single "write once, works everywhere" property of SKILL.md files has driven an ecosystem response no proprietary format could have achieved. Developers writing skills for Claude Code immediately get compatibility with Codex, Gemini CLI, Cursor, and GitHub Copilot. This is the explicit strategy mirroring MCP's own success — and it's working faster. VoltAgent/awesome-agent-skills (20.6k stars) grew purely on the back of cross-platform appeal.

**Platforms:** GitHub, Web (paperclipped, serenitiesai, agensi.io)

---

### Pattern 3: The Security Debt Is Compounding

**Signal strength:** Strong — multiple independent researchers, OWASP formalization, active CVEs

The skill/MCP ecosystem has replicated npm's early-days security debt at accelerated speed. Three independent vectors converged in Q1-Q2 2026: (1) MCP architectural RCE (OX Security, April 2026); (2) ClawHavoc poisoning campaign (Jan 2026); (3) Snyk audit showing 36.82% of skills have security flaws. OWASP's response (AST10, April 27 2026) is the signal that this has reached institutional attention. The threat model is genuinely novel: skills inherit agent permissions and NLP is an attack surface, meaning a malicious skill can exfiltrate API keys through natural language manipulation.

**Platforms:** Web (security blogs, Hacker News adjacent)

---

### Pattern 4: Enterprise Is the Next Frontier

**Signal strength:** Moderate-strong (TechCrunch coverage, Anthropic exec quotes, partner names)

Anthropic's February 2026 enterprise launch (finance/HR/legal plugins + private marketplaces + Gmail/DocuSign/Clay connectors) positioned the skill/plugin stack as a SaaS replacement layer. Kate Jensen's "2025 hype was premature" quote signals Anthropic is timing this deliberately — setting up 2026 as delivery year. The private marketplace model (controlled distribution, centralized admin, RBAC) is the enterprise moat.

**Platforms:** Web (TechCrunch, TechRadar, VentureBeat)

---

### Pattern 5: Discovery Has Replaced Protocol as the Bottleneck

**Signal strength:** Moderate (multiple sources independently converging)

Multiple independent sources noted the same shift: the MCP protocol is no longer the problem — finding the right server is. This drove: the official MCP Registry, Smithery, MCPMarket, Kong MCP Registry, skills.sh leaderboard, awesome-agent-skills, tonsofskills.com. The next frontier (MCP Server Cards via .well-known URLs, Claude Code's /skills search box) is agent-native discovery — servers and skills announcing their own capabilities without human-mediated registries.

**Platforms:** Web (truefoundry, codeongrass, tedt.org)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| weinzierl | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | ~200 | "I don't want AI in your product — I want AI of my choice to use your product for me." (TeMPOraL) | [link](https://news.ycombinator.com/item?id=45619537) |

**GitHub:**
| Repo | Description | Stars | Notable Detail | URL |
|------|-------------|-------|----------------|-----|
| VoltAgent/awesome-agent-skills | 1,100+ curated cross-platform skills | 20,600★ | Official skills from Anthropic, Microsoft (133), OpenAI (29), Sentry (39), Trail of Bits (22) | [link](https://github.com/VoltAgent/awesome-agent-skills) |
| jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents — tonsofskills.com marketplace | 2,100★ | ccpi CLI package manager | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) |
| alirezarezvani/claude-skills | 232+ skills for 10+ agents | — | Engineering, marketing, compliance, C-level advisory | [link](https://github.com/alirezarezvani/claude-skills) |
| shinpr/sub-agents-skills | Cross-LLM sub-agent orchestration as Agent Skills | — | Routes to Codex/Claude/Cursor/Gemini | [link](https://github.com/shinpr/sub-agents-skills) |
| agentic-community/mcp-gateway-registry | Enterprise MCP gateway + registry | — | OAuth, Keycloak/Entra, audit trails | [link](https://github.com/agentic-community/mcp-gateway-registry) |
| vercel-labs/skills | Open agent skills CLI tool | — | Powers skills.sh; `npx skills add` | [link](https://github.com/vercel-labs/skills) |
| kenhuangus/agentic-skills-top-10 | OWASP AST10 repository | — | Published April 27, 2026 | [link](https://github.com/kenhuangus/agentic-skills-top-10) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Official launch post, Oct 16 2025; progressive disclosure model; "onboarding guide for a new hire" quote |
| Claude Code Skills Docs | [link](https://code.claude.com/docs/en/skills) | Full official spec: frontmatter fields, lifecycle, subagents, invocation control, shell injection |
| Official MCP Registry | [link](https://registry.modelcontextprotocol.io/) | Primary MCP server discovery hub |
| Vercel skills.sh launch | [link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) | Jan 20 2026 launch; npm analogy; 17+ agent platforms |
| skills.sh directory | [link](https://skills.sh/) | Agent Skills directory and leaderboard |
| Snyk/Vercel security partnership | [link](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) | Feb 17 2026; 36.82% flaw rate; threat model breakdown |
| TechCrunch enterprise launch | [link](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/) | Feb 24 2026; 11 plugins; private marketplaces; exec quotes |
| The Hacker News MCP RCE | [link](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) | April 2026; RCE vulnerability; Anthropic "expected behavior" response |
| OX Security "Mother of All AI Supply Chains" | [link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | Critical systemic MCP vulnerability analysis |
| OWASP AST10 | [link](https://owasp.org/www-project-agentic-skills-top-10/) | April 27 2026; skill content layer security framework |
| morphllm three-layer guide | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills vs MCP vs Plugins taxonomy; context token costs |
| MCP 2026 Roadmap (tedt.org) | [link](https://tedt.org/MCPs-2026-Roadmap/) | 12 roadmap items; stateless transport June 2026 |
| Paperclipped interoperability | [link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) | 32 adopters timeline; Simon Willison quote; 89k+ skills at cross-platform milestone |
| VentureBeat OpenClaw | [link](https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner) | ClawHavoc campaign; AI agent backdoor supply chain attack |
| Meta Ads AI Connectors | [link](https://digiday.com/marketing/meta-opens-its-ad-ecosystem-to-third-party-ai-tools/) | April 29 2026 launch; 29 tools; mcp.facebook.com/ads |
| truefoundry MCP registries | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Best MCP registries comparison: Smithery 7k+, MCPMarket 10k+ |
| Developer Digest HN analysis | [link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | HN developer sentiment arc 2024→2026 |
| arXiv Claude Code design space | [link](https://arxiv.org/html/2604.14228v1) | Academic: design space of AI agent systems |
| Jonathan Fulton (Medium Apr 2026) | [link](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | "Agent Skills: The Cheat Codes for Claude Code" |
| unicodeveloper (Medium Mar 2026) | [link](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | "10 Must-Have Skills for Claude and Any Coding Agent in 2026" |
| releasebot Claude Code | [link](https://releasebot.io/updates/anthropic/claude-code) | Claude Code updates April-May 2026 |
| codewithandrea Jan 2026 newsletter | [link](https://codewithandrea.com/newsletter/january-2026/) | "January 2026: AI Agents Take Over" developer summary |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ inaccessible (API 403)
├─ 🔵 X: 0 posts │ inaccessible (domain blocked)
├─ 🔴 YouTube: 0 videos │ not fetched
├─ 🟢 HN: 1 story │ 738 points │ ~200 comments
├─ 🟣 TikTok: 0 videos │ no data
├─ 🩷 Instagram: 0 reels │ no data
├─ 🦋 Bluesky: 0 posts │ no data
├─ 📊 Polymarket: 0 markets │ no data
├─ 🐙 GitHub: 7 repos │ 22,700+ combined stars
├─ 🌐 Web: 80+ pages │ 10 search queries, 8 direct fetches
└─ 🗣️ Top voices: tptacek (HN), simonw (HN/web), weinzierl (HN), TeMPOraL (HN) │ r/n/a (Reddit blocked)
```

---

## Data Gaps

- **Reddit (full blackout):** API returns 403 for crawler. All Reddit discussion about Claude Code skills, MCP, and plugins is invisible. Given how active r/ClaudeAI, r/LocalLLaMA, and r/ChatGPT are on these topics, this is a significant gap — estimate 30-40% of grassroots developer sentiment is missing.
- **X/Twitter (full blackout):** Domain blocked. No visibility into real-time developer reactions, Anthropic announcements via @AnthropicAI, or ecosystem chatter from prominent AI engineers.
- **YouTube:** Not directly fetched. Tutorial videos about Claude Code skills are abundant (referenced in multiple web sources) but content was not retrieved.
- **TikTok / Instagram / Bluesky / Polymarket:** No data returned for any of these platforms.
- **HN depth:** Only 1 thread retrieved directly. The HN discussion of the Dec 18 2025 open standard announcement (likely 400-600 points) was not fetched.
- **Noise:** Web search results included many SEO-optimized "best of" listicles (claudefa.st, turbodocx, nimbalyst) with limited original analysis. Signal was concentrated in: official docs, security advisories, the HN thread, and key news coverage.
- **Approximate coverage:** ~50% of available signal. Strong on: official ecosystem docs, security/supply-chain, GitHub repos, news coverage, HN. Weak on: social media sentiment, YouTube tutorials, community forums.

---

## Key Quotes

> "Building a skill for an agent is like putting together an onboarding guide for a new hire." — Anthropic Engineering Blog ([link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills))

> "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones." — tptacek on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "I don't want AI in your product — I want AI of my choice to use your product for me." — TeMPOraL on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Formalization matters: giving patterns names enables better discourse and enables Claude Code to auto-scan YAML metadata for skill discovery." — simonw on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Skills are like npm, but instead of JavaScript libraries, you're installing capabilities that your AI agent can execute on your behalf." — Vercel skills.sh launch ([link](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem))

> "When you run `npx skills add <package>`, you're not just installing a library...it's code *and* natural language instructions that an autonomous agent will interpret and act on." — Snyk/Vercel security blog ([link](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/))

> "2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature." — Kate Jensen, Anthropic Head of Americas ([link](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/))

> "We believe that the future of work means everybody having their own custom agent." — Matt Piccolella, Anthropic Product Officer ([link](https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/))

> "A deliciously tiny specification — the entire format requires only two mandatory YAML fields and Markdown instructions, making implementation feasible in approximately one day for any engineering team." — Simon Willison on the Agent Skills spec ([link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/))

> "MCP is the plumbing connecting Claude to the outside world; Skills are the instructions teaching Claude how to do specific things; and Plugins are the finished product bundling both together — they are three layers of the same stack." — devtoolpicks.com ([link](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026))
