# Agent Skills — Raw Research Data
**Date:** 2026-05-07
**Query:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## PIPELINE NOTES

- Reddit: inaccessible (API 403 – domain blocked to crawler)
- X/Twitter: inaccessible (domain blocked to crawler)
- YouTube: not directly fetched; references appear in web sources
- TikTok / Instagram / Bluesky / Polymarket: no data returned
- Hacker News: 1 high-signal thread identified and fetched
- GitHub: 6 repositories fetched directly
- Web (WebSearch + WebFetch): 80+ URLs retrieved across 10 search queries + 8 direct fetches

---

## SEARCH QUERY 1 — "Claude Code skills plugins MCP servers 2026"

**Results:**
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — "50+ Best MCP Servers for Claude Code in 2026"
- https://nimbalyst.com/blog/claude-code-plugins-guide/ — "Claude Code Plugins: A 2026 Guide"
- https://www.morphllm.com/claude-code-skills-mcp-plugins — "Claude Code Skills vs MCP vs Plugins: Complete Guide 2026"
- https://code.claude.com/docs/en/mcp — Official Claude Code MCP docs
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers — "Best Claude Code Plugins, Skills & MCP Servers (2026)"
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 425 plugins, 2,810 skills, 200 agents; tonsofskills.com marketplace
- https://alexop.dev/posts/understanding-claude-code-full-stack/ — "Understanding Claude Code's Full Stack: MCP, Skills, Subagents, and Hooks Explained"
- https://claudemarketplaces.com/ — "Claude Code Plugins | Skills, MCP Servers & Marketplace Directory"
- https://www.claudepluginhub.com/blog/mcp-server-plugins-for-claude-code — "Claude Code MCP Servers: A Developer's Guide"
- https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 — "Best Claude Code Skills & Plugins (2026 Guide)"

**Key extracted facts:**
- As of May 6, 2026: 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces listed on aggregator
- Skills under 2,000 tokens perform best
- Skills = instructions in markdown; MCP servers = tools over standard protocol; Plugins = tighter integrations bundling both
- Skills use progressive disclosure: ~100 tokens per skill for metadata scan, full load only when relevant
- Shopify AI Toolkit: query products, orders, customers with natural language from Claude Code terminal
- Meta official MCP for Facebook/Instagram Ads launched April 29, 2026 (29 tools)

---

## SEARCH QUERY 2 — "MCP server marketplace agent tool registry 2026"

**Results:**
- https://www.truefoundry.com/blog/best-mcp-registries — "Best MCP Registries in 2026: Compared for Developers and Enterprises"
- https://registry.modelcontextprotocol.io/ — Official MCP Registry
- https://konghq.com/products/mcp-registry — Kong MCP Registry (enterprise governance)
- https://tedt.org/MCPs-2026-Roadmap/ — "MCP's 2026 Roadmap: From Agent Integration Standard to Production Connectivity Layer"
- https://machalliance.org/mach-alliance-mcp-registry — MACH Alliance MCP Registry
- https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools — Microsoft Learn MCP tools
- https://github.com/agentic-community/mcp-gateway-registry — Enterprise-ready MCP Gateway & Registry
- https://learn.microsoft.com/en-us/azure/foundry/mcp/build-your-own-mcp-server — Azure Foundry MCP build guide
- https://tokenmix.ai/blog/mcp-servers-list-2026-complete-directory — "MCP Servers List 2026: Complete Directory of 70+ Production Servers"
- https://blog.modelcontextprotocol.io/posts/2025-09-08-mcp-registry-preview/ — Official MCP Registry launch announcement

**Key extracted facts:**
- Official MCP Registry launched preview: September 8, 2025; API freeze (v0.1): October 24, 2025
- Smithery: 7,000+ MCP servers (Docker Hub equivalent for MCP)
- MCPMarket.com: 10,000+ MCP servers across 23+ categories
- Kong MCP Registry: single source of truth for enterprise AI tool governance
- agentic-community/mcp-gateway-registry: OAuth, dynamic tool discovery, Keycloak/Entra integration
- Developer question evolution: from "can my agent access external tools?" → "which MCP server for Home Assistant?"
- Discovery is the bottleneck in 2026, not the protocol itself

---

## SEARCH QUERY 3 — "Claude Code extensions reusable agent capabilities skill discovery 2026"

**Results:**
- https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview — Agent Skills docs
- https://code.claude.com/docs/en/skills — Extend Claude with skills (official docs)
- https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 — "10 Must-Have Skills for Claude in 2026"
- https://www.augmentcode.com/guides/claude-agent-sdk-skills-reusable-agent-capabilities — Augment Code SDK skills guide
- https://github.com/VoltAgent/awesome-agent-skills — 1,100+ curated skills, 20.6k GitHub stars
- https://nimbalyst.com/blog/claude-code-skills-guide/ — "Claude Code Skills: A Practical 2026 Guide"
- https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d — "Agent Skills: The Cheat Codes for Claude Code" (Apr 2026)
- https://composio.dev/content/top-claude-skills — "Top 10 Claude Code Skills Every Builder Should Know in 2026"
- https://www.firecrawl.dev/blog/best-claude-code-skills — "Best Claude Code Skills to Try in 2026"
- https://github.com/alirezarezvani/claude-skills — 232+ Claude Code skills & agent plugins

**Key extracted facts:**
- Skills are filesystem-based SKILL.md folders with YAML frontmatter + markdown instructions
- Progressive disclosure: Level 1 (metadata ~100 tokens) → Level 2 (full SKILL.md) → Level 3 (supporting files)
- Skill ecosystem hit 1,000-skill threshold early 2026
- Cross-platform: same SKILL.md works in Claude Code, Codex CLI, Gemini CLI, Cursor, GitHub Copilot
- "Building a skill for an agent is like putting together an onboarding guide for a new hire." — Anthropic engineering blog
- VoltAgent/awesome-agent-skills: 20.6k★, 1,100+ skills, official sets from Anthropic, Microsoft (133), OpenAI (29), Sentry (39), Google, Stripe, Cloudflare

---

## SEARCH QUERY 4 — "agent skills open standard cross-platform Codex Gemini CLI Cursor 2026"

**Results:**
- https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026 — Codex CLI Agent Skills guide
- https://www.agensi.io/learn/agent-skills-open-standard — "What Is the Agent Skills Open Standard? (2026 Explainer)"
- https://www.agensi.io/learn/install-skills-gemini-cli-guide — Install Skills in Gemini CLI guide
- https://www.agensi.io/learn/where-are-gemini-cli-skills-stored — Gemini CLI skills paths
- https://github.com/VoltAgent/awesome-agent-skills — (see above)
- https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ — "Agent Skills Open Standard Interoperability Guide 2026"
- https://serenitiesai.com/articles/agent-skills-guide-2026 — "AI Agent Skills Guide 2026: Build Skills for 16+ AI Tools"
- https://github.com/shinpr/sub-agents-skills — "Cross-LLM sub-agent orchestration as Agent Skills"
- https://alirezarezvani.github.io/claude-skills/guides/gemini-cli-skills-guide/ — Gemini CLI skills guide
- https://www.agensi.io/learn/best-codex-cli-skills-2026 — "Best Codex CLI Skills in 2026"

**Key extracted facts:**
- Spec published: December 18, 2025 by Anthropic
- 48 hours post-launch: Microsoft (VS Code) and OpenAI (Codex CLI) integrated
- January 20, 2026: Vercel launched skills.sh
- February 5, 2026: AWS Kiro IDE shipped support
- March 2026: 32 total adopters (Google, JetBrains, Block/Goose, Snowflake, Databricks, Mistral)
- Skills.sh top skill "find-skills" by Vercel Labs: 579,000+ installs as of March 2026
- Simon Willison: "deliciously tiny specification" — two mandatory YAML fields + Markdown
- 89,753 skills published immediately accessible across all platforms at time of cross-platform milestone

---

## SEARCH QUERY 5 — "Anthropic agent skills October 2025 launch plugin ecosystem"

**Results:**
- https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ — The New Stack analysis
- https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard — VentureBeat announcement
- https://offthegridxp.substack.com/p/the-genius-of-anthropics-claude-agent-skills-2025 — "The Genius of Anthropic's Agent Skills" (Substack)
- https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills — Official Anthropic engineering blog
- https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude — AI Business
- https://opendatascience.com/anthropic-introduces-agent-skills-making-claude-smarter-faster-and-more-specialized/ — Open Data Science
- https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/ — TechCrunch Feb 2026 enterprise launch
- https://www.techradar.com/pro/anthropic-takes-the-fight-to-openai-with-enterprise-ai-tools-and-theyre-going-open-source-too — TechRadar
- https://subramanya.ai/2025/12/18/agent-skills-the-missing-piece-of-the-enterprise-ai-puzzle/ — "Agent Skills: The Missing Piece" (Dec 18 2025)
- https://skywork.ai/blog/ai-agent/anthropic-skills-vs-custom-skills-2025-comparison/ — Anthropic Skills vs Custom Skills comparison

**Key extracted facts (from fetched content):**
- Oct 16, 2025: Anthropic announced Claude Skills
- Dec 18, 2025: Open standard published
- Launch partners directory: Atlassian, Canva, Cloudflare, Figma, Notion, Ramp, Sentry
- Microsoft adopted in VS Code and GitHub Copilot; Cursor, Goose, Amp, OpenCode followed
- Feb 24, 2026 TechCrunch: enterprise push with 11 official Plugins covering legal, sales, finance, marketing, data analysis
- Plugin marketplace launched Feb 2026
- Kate Jensen (Head of Americas): "2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature."
- Matt Piccolella (Product Officer): "We believe that the future of work means everybody having their own custom agent."
- Enterprise: private software marketplaces, centralized admin controls, new connectors: Gmail, DocuSign, Clay

---

## SEARCH QUERY 6 — "skills.sh Vercel agent skills directory leaderboard npm 2026"

**Results:**
- https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem — Vercel launch announcement
- https://github.com/vercel-labs/skills — vercel-labs/skills repo
- https://vercel.com/docs/agent-resources/skills — Vercel official docs
- https://skills.sh/vercel-labs/skills/find-skills — find-skills package on skills.sh
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ — "Agent Skills Marketplace: Skills.sh Guide"
- https://github.com/vercel-labs/skills/blob/main/skills/find-skills/SKILL.md — SKILL.md source
- https://www.toolworthy.ai/tool/skills-sh — "Skills.sh Review (2026)"
- https://skills.sh/ — The Agent Skills Directory (homepage)
- https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ — Snyk + Vercel security partnership
- https://www.npmjs.com/package/skills — npm package

**Key extracted facts (from fetched content):**
- Vercel launched skills.sh: January 20, 2026
- "Skills are like npm, but instead of JavaScript libraries, you're installing capabilities"
- Install: `npx skills add vercel-labs/agent-skills`
- Top skill reached 20,000+ installs within 6 hours of launch
- Stripe shipped their own skills within hours of launch
- find-skills by Vercel Labs: 235,000+ weekly installs (by Feb 17, 2026)
- Total ecosystem: 4,257 skills growing at 147 new skills daily
- Snyk partnership: Feb 17, 2026 — security leaderboard integrated into skills.sh
- Snyk security audit findings: 36.82% of 3,984 audited skills contain ≥1 security flaw; 13.4% critical
- Novel threat model: skills inherit agent permissions; natural language = attack vector; inverted trust model

---

## SEARCH QUERY 7 — "Hacker News Claude Code skills MCP agents plugin ecosystem discussion 2026"

**Results:**
- https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 — Developer Digest HN analysis
- https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 — "Claude Skills vs MCP Connectors vs Plugins"
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — "AI Agent Security Risks 2026: MCP, OpenClaw & Supply Chain"
- https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051
- https://codewithandrea.com/newsletter/january-2026/ — "January 2026: AI Agents Take Over" newsletter
- https://news.ycombinator.com/item?id=45619537 — HN thread: "Claude Skills are awesome, maybe a bigger deal than MCP" (738 points, weinzierl)
- https://snyk.io/articles/top-claude-skills-developers/ — "Top 8 Claude Skills for Developers"
- https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/ — "The MCP Server Ecosystem in 2026"
- https://arxiv.org/html/2604.14228v1 — "Dive into Claude Code: The Design Space of Today's and Future AI Agent Systems" (arXiv paper)
- https://getbeam.dev/blog/claude-code-skills-ecosystem-guide.html — "Claude Code Skills Ecosystem: The Complete 2026 Guide"

**Key extracted facts from HN thread (738 points, user: weinzierl):**
- Top commenter tptacek: "tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones."
- Skills address MCP's "context pollution" weakness — unlike MCP which frontloads context, skills load progressively
- michael1999: three theories for why LLM-friendly docs thrive: (1) immediate feedback loops, (2) tools help build them, (3) personal incentive ("harness a computer minion")
- causal/primer42 skepticism: "this simply formalizes existing practices"
- simonw counter: "formalization matters: giving patterns names enables better discourse and enables Claude Code to auto-scan YAML metadata"
- TeMPOraL: "I don't want AI in your product—I want AI of my choice to use your product for me."
- quentindanjou: architecture and clear communication, not coding, become the bottleneck for human developers
- emn13: these aren't timeless docs but "battle-tested" action plans solving "acute, real concerns" right away

**Claude Code Skills vs MCP vs Plugins taxonomy (from devtoolpicks):**
- MCP = the plumbing connecting Claude to outside world
- Skills = instructions teaching Claude how to do specific things
- Plugins = the finished product bundling both together
- "Three layers of the same stack"

---

## SEARCH QUERY 8 — "plugin ecosystem supply chain security MCP agent skills vulnerability 2026"

**Results:**
- https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html — "Anthropic MCP Design Vulnerability Enables RCE, Threatening AI Supply Chain" (The Hacker News, April 2026)
- https://www.ox.security/blog/mcp-supply-chain-advisory-rce-vulnerabilities-across-the-ai-ecosystem/ — OX Security advisory
- https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner — "OpenClaw: One command turns any repo into AI agent backdoor"
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — AI Agent Security Risks 2026
- https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ — "The Mother of All AI Supply Chains"
- https://www.practical-devsecops.com/mcp-security-vulnerabilities/ — "MCP Security Vulnerabilities: How to Prevent Prompt Injection and Tool Poisoning Attacks in 2026"
- https://obot.ai/blog/mcp-security-agent-skills-supply-chain/ — "The New Supply Chain Frontier: Securing MCP Security and Agent Skills"
- https://www.msspalert.com/native/owasp-mcp-10-external-aiexposures-you-must-prioritize-in-2026 — OWASP MCP 10
- https://www.rockcybermusings.com/p/agent-supply-chain-attacks-scanner-switched-sides — "Agent Supply Chain Attacks: Your Scanner Already Switched Sides"
- https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/ — "The Ultimate Guide to MCP Security Vulnerabilities"

**Key extracted facts:**
- ClawHavoc campaign (first reported late Jan 2026): 341 → 1,184 malicious skills on ClawHub
- 36.82% of all skills contain ≥1 security flaw; 13.4% have critical-level issues
- OX Security: critical systemic RCE vulnerability in MCP core architecture
- Anthropic declined to modify protocol architecture, citing behavior as "expected"
- Scale: 150M+ downloads, 7,000+ publicly accessible MCP servers, up to 200,000 vulnerable instances
- Feb 2026: 8,000+ MCP servers on public internet; 492 with zero auth and zero traffic encryption (Trend Micro)
- Jan–Feb 2026: 30+ CVEs filed targeting MCP; 43% were shell injections
- OWASP MCP Top 10: protocol layer framework (published 2025, in beta)
- OWASP Agentic Skills Top 10 (AST10): published April 27, 2026 — skill content layer framework; incubated at OWASP Project Summit in Oslo 2026
- ClawHub first AI agent registry systematically poisoned at scale; 5 of top 7 most-downloaded skills were confirmed malware

---

## SEARCH QUERY 9 — "Claude Code skills plugins April May 2026 new releases updates"

**Results:**
- https://releasebot.io/updates/anthropic/claude-code — Claude Code Updates by Anthropic – May 2026
- https://claudefa.st/blog/guide/changelog — Claude Code Changelog: All Release Notes (2026)
- https://code.claude.com/docs/en/changelog — Official changelog
- https://github.com/anthropics/claude-code/releases — GitHub releases
- https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 — "Top 10 Claude Code Skills, Plugins & CLIs for 2026"
- https://www.devopsdigest.com/prismatic-skills-for-claude-code-released — Prismatic Skills for Claude Code released
- https://support.claude.com/en/articles/12138966-release-notes — Release notes
- https://github.com/alirezarezvani/claude-skills — 232+ skills repo
- https://findskill.ai/blog/claude-cowork-guide/ — "Claude Cowork Guide 2026: Skills, Plugins, Connectors"
- https://releasebot.io/updates/anthropic — Anthropic Release Notes – May 2026

**Key extracted facts (recent Claude Code changes):**
- Added type-to-filter search box to /skills (recent)
- Added `claude plugin prune` to remove orphaned plugin dependencies
- `alwaysLoad` option for MCP server config: skip tool-search deferral
- Windows: Git Bash no longer required; PowerShell now usable as shell tool
- `claude ultrareview [target]` subcommand for CI/scripts
- PostToolUse hooks can replace tool output for all tools via hookSpecificOutput.updatedToolOutput
- April 9, 2026: Claude Cowork GA on macOS and Windows (analytics, OpenTelemetry, RBAC)
- April 14, 2026: Anthropic introduced Routines in research preview (cloud-hosted automation)
- Prismatic Skills for Claude Code: new open source plugin to ship integrations faster
- 232+ skills in alirezarezvani/claude-skills covering engineering, marketing, product, compliance, C-level advisory

---

## SEARCH QUERY 10 — "OWASP Agentic Skills Top 10 April 2026 MCP security"

**Results:**
- https://owasp.org/www-project-agentic-skills-top-10/ — OWASP Agentic Skills Top 10 project
- https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/ — OWASP Top 10 for Agentic Applications 2026
- https://www.practical-devsecops.com/owasp-mcp-top-10/ — "OWASP MCP Top 10: The 10 Critical Risks Every Security Team Must Fix in 2026"
- https://owasp.org/www-project-mcp-top-10/ — OWASP MCP Top 10 project
- https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications — DeepTeam OWASP Top 10 for Agents
- https://obot.ai/blog/mcp-security-agent-skills-supply-chain/ — "The New Supply Chain Frontier"
- https://github.com/kenhuangus/agentic-skills-top-10 — AST10 GitHub repo
- https://www.gravitee.io/blog/owasp-top-10-for-agentic-applications-2026-a-practical-review-and-how-gravitee-supports-secure-agentic-architecture — Gravitee OWASP review
- https://secops.group/blog/securing-agentic-ai-the-owasp-top-10-and-beyond/ — SecOps OWASP analysis
- https://agatsoftware.com/blog/owasp-agentic-top-10-2026-ciso-guide/ — "OWASP Agentic Top 10 (2026): The CISO Guide"

**Key extracted facts:**
- AST10 published April 27, 2026 — formalizes the threat category
- OWASP MCP Top 10: protocol layer; AST10: skill content layer — complementary frameworks
- AI agent skill ecosystem under active attack as of Q1 2026
- ClawHub: first AI agent registry systematically poisoned at scale

---

## META MCP LAUNCH (SEARCH 11)

**Results:**
- https://github.com/pipeboard-co/meta-ads-mcp — community Meta Ads MCP
- https://www.facebook.com/business/help/1456422242197840 — Meta official AI connectors help
- https://www.get-ryze.ai/blog/meta-facebook-ads-mcp-server-connector — Meta MCP setup guide
- https://pasqualepillitteri.it/en/news/1707/official-meta-ads-mcp-claude-29-tools-2026 — "Official Meta Ads MCP for Claude: 29 Tools (April 2026)"
- https://mcp.directory/blog/meta-ads-cli-mcp — Meta Ads MCP and CLI breakdown
- https://commonthreadco.com/blogs/coachs-corner/meta-ai-mcp-cli-ads-connectors-ecommerce — Meta AI MCP/CLI for e-commerce
- https://digiday.com/marketing/meta-opens-its-ad-ecosystem-to-third-party-ai-tools/ — Digiday: Meta opens ad ecosystem
- https://www.get-ryze.ai/blog/best-mcp-for-meta-ads — "Best MCP for Meta Ads in 2026"
- https://www.get-ryze.ai/blog/meta-ads-official-mcp-cli-launch — Meta official MCP/CLI launch
- https://adkit.so/features/ads-mcp/meta — Meta Ads MCP feature page

**Key extracted facts:**
- April 29, 2026: Meta released Meta Ads AI Connectors in open beta
- MCP server: mcp.facebook.com/ads
- 29 tools callable in natural language for campaigns, catalogs, benchmarks, tracking
- Official MCP: free during beta; auth direct between user and Meta (no third-party middleman)
- Supported platforms: ChatGPT, Claude (MCP-compatible tools)
- CLI companion: same 29 commands as MCP, as local binary

---

## GITHUB REPOSITORIES

### VoltAgent/awesome-agent-skills
- URL: https://github.com/VoltAgent/awesome-agent-skills
- Stars: 20,600
- Skills: 1,100+ curated
- Description: "Hand-picked, not AI-slop generated"
- Official contributors: Anthropic, Microsoft (133 skills, 6 languages), OpenAI (29 skills), Sentry (39 skills), Google, Stripe, Cloudflare, Figma, Hugging Face, GitHub, Netlify, AWS, Azure, Vercel, fal.ai, Replicate, Trail of Bits (22 security skills)
- Recent activity: 342 commits, 10 open PRs

### jeremylongshore/claude-code-plugins-plus-skills
- URL: https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- Stars: 2,100
- Contents: 425 plugins, 2,810 skills, 200 agents (18 categories)
- Marketplace: tonsofskills.com
- CLI: `@intentsolutionsio/ccpi` (pnpm global install)
- Recent: 339+ npm downloads in last 30 days
- License: MIT

### alirezarezvani/claude-skills
- URL: https://github.com/alirezarezvani/claude-skills
- Skills: 232+
- Covers: engineering, marketing, product, compliance, C-level advisory
- Compatible: Claude Code, Codex, Gemini CLI, Cursor, 8 more agents

### shinpr/sub-agents-skills
- URL: https://github.com/shinpr/sub-agents-skills
- Description: Cross-LLM sub-agent orchestration as Agent Skills
- Routes tasks to Codex, Claude Code, Cursor, or Gemini from any compatible tool

### agentic-community/mcp-gateway-registry
- URL: https://github.com/agentic-community/mcp-gateway-registry
- Description: Enterprise-ready MCP Gateway & Registry
- Features: OAuth, dynamic tool discovery, unified access, Keycloak/Entra integration, audit trails

### vercel-labs/skills
- URL: https://github.com/vercel-labs/skills
- Description: Open agent skills tool — npx skills
- Install: `npx skills add <package>`

### kenhuangus/agentic-skills-top-10
- URL: https://github.com/kenhuangus/agentic-skills-top-10
- Description: OWASP Agentic Skills Top 10 GitHub repository

---

## OFFICIAL DOCUMENTATION FETCH: code.claude.com/docs/en/skills

Key details from full doc read:
- Skills follow the Agent Skills open standard at agentskills.io
- Custom commands merged into skills (backward compatible)
- Bundled skills include: /simplify, /batch, /debug, /loop, /claude-api, /ultrareview
- Frontmatter fields: name, description, when_to_use, argument-hint, arguments, disable-model-invocation, user-invocable, allowed-tools, model, effort, context, agent, hooks, paths, shell
- String substitutions: $ARGUMENTS, $ARGUMENTS[N], $N, $name, ${CLAUDE_SESSION_ID}, ${CLAUDE_EFFORT}, ${CLAUDE_SKILL_DIR}
- context: fork → runs skill in isolated subagent
- Skill content lifecycle: invoked skill stays in context for session; compaction carries forward up to 25,000 token budget
- disableSkillShellExecution: true — blocks !`command` shell injection in skills (enterprise safety)
- Live change detection: adding/editing skill directories takes effect mid-session
- Monorepo support: auto-discovers nested .claude/skills/ directories
- skillOverrides in settings: "on", "name-only", "user-invocable-only", "off"

---

## MCP 2026 ROADMAP (from tedt.org)

Items on MCP 2026 roadmap:
1. Stateless Transport (June 2026) — hyperscale deployment, load balancers
2. Server Discovery — "MCP Server Cards" via .well-known URLs
3. Tasks Improvements — long-running async work, retry behavior
4. Enterprise Auth — SSO (Google Workspace, Okta), audit trails
5. Triggers — webhook-like notifications, ordering guarantees
6. Native Streaming & Results — incremental output, context bloat management
7. Skills Over MCP — domain-specific instructions bundled with tools
8. Extensions & MCP Apps — interactive UI patterns
9. SDK v2 (Python & TypeScript) — conformance test suites
10. Progressive Discovery & Tool Search — defer tool loading
11. Programmatic Tool Calling — code execution for tool composition
12. Agent-Native Server Design — workflow-oriented over API wrapping

Key quote: MCP shifting from "establishing need for a common standard" to "reliable enough for production-scale agentic systems"

---

## SNYK / VERCEL SECURITY PARTNERSHIP (fetched)

- Partnership announced: February 17, 2026
- Security Leaderboard integrated into skills.sh marketplace
- "When you run `npx skills add <package>`, you're not just installing a library...it's code _and_ natural language instructions that an autonomous agent will interpret and act on."
- Detection accuracy: 90-100% recall on malicious skills; 0% false positive on top 100 legitimate skills
- Analysis combines LLM-based judges with deterministic rules
- Threat model:
  1. Expanded blast radius (skills inherit agent filesystem/shell/API key permissions)
  2. Novel attack surface (NLP = attack vector; prompt injection, "toxic flows")
  3. Inverted trust model (agent autonomously decides skill execution)

---

## ANTHROPIC ENGINEERING BLOG (fetched summary)

URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- Published: October 16, 2025
- Open standard: December 18, 2025
- Progressive disclosure: 3 context levels
- Supported: Claude.ai, Claude Code, Claude Agent SDK, Claude Developer Platform
- Key quote: "Building a skill for an agent is like putting together an onboarding guide for a new hire."

---

## TECHCRUNCH ENTERPRISE LAUNCH (fetched summary)

URL: https://techcrunch.com/2026/02/24/anthropic-launches-new-push-for-enterprise-agents-with-plugins-for-finance-engineering-and-design/
- Feb 24, 2026: Anthropic unveiled enterprise agents program
- Pre-built agents for Finance (market research, competitive analysis, financial modeling), HR (job descriptions, onboarding, offer letters), Legal
- Private software marketplaces for controlled deployment
- Centralized admin controls for IT departments
- New enterprise connectors: Gmail, DocuSign, Clay
- Kate Jensen (Head of Americas): "2025 was meant to be the year agents transformed the enterprise, but the hype turned out to be mostly premature."
- Matt Piccolella (Product Officer): "We believe that the future of work means everybody having their own custom agent."
- Builds on Claude Cowork technology and January plugin infrastructure

---

## MORPHLLM THREE-LAYER FRAMEWORK (fetched)

URL: https://www.morphllm.com/claude-code-skills-mcp-plugins
- Layer 1 — Skills (Procedural Knowledge): 30-50 tokens until activated; cross-platform
- Layer 2 — MCP Servers (External Connectivity): 55,000+ tokens for typical 5-server setup; mitigated by Tool Search (85% reduction)
- Layer 3 — Plugins (Distributable Bundles): packages skills + commands + hooks + MCP configs; sum of components

---

## PAPERS / ACADEMIC

- https://arxiv.org/html/2604.14228v1 — "Dive into Claude Code: The Design Space of Today's and Future AI Agent Systems"

---

## COVERAGE NOTES

- Reddit: 0 items (API blocked)
- X/Twitter: 0 items (API blocked)
- YouTube: 0 videos directly fetched (mentioned in search snippets but not retrieved)
- TikTok/Instagram/Bluesky/Polymarket: 0 items
- Hacker News: 1 thread (738 points)
- GitHub: 7 repos directly fetched
- Web: ~80 URLs across 10+ search queries
- Total coverage: Strong on web/blog/news/GitHub, zero on social media platforms
