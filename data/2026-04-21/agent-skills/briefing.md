# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-21
**Query type:** GENERAL
**Sources:** Web, GitHub, Official Docs, YouTube, Security Research, Industry Blogs

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web | 85+ pages | — | via WebSearch across 13 queries |
| GitHub | 15+ repos | — | Official Anthropic, Vercel, community |
| YouTube | 3 videos | — | Tutorial content on SKILL.md creation |
| Official Docs | 8 pages | — | Claude Code, Vercel, Gemini CLI, OWASP |
| Security Research | 10+ reports | — | Snyk, OX Security, SecurityWeek, Hacker News |

---

## Synthesized Findings

### 1. The SKILL.md Open Standard: A New Layer of the AI Stack

The most significant structural development of early 2026 is the emergence of SKILL.md as a de facto open standard for reusable agent capabilities. Anthropic released the Agent Skills specification in December 2025, and OpenAI immediately adopted the same format for Codex CLI and ChatGPT — an unusually fast cross-company convergence.

A SKILL.md file contains YAML frontmatter (name, description, trigger conditions) followed by markdown instructions that Claude or any compatible agent follows when the skill activates. The key architectural insight is **lazy loading**: Claude scans skill names/descriptions using ~100 tokens each, only loading full instructions (up to 5k tokens) when the skill is determined relevant. This allows hundreds of skills to be installed without overwhelming context windows.

Skills now work across 14+ platforms from a single SKILL.md file — Claude Code, Cursor, Codex CLI, GitHub Copilot, Windsurf, Gemini CLI, and more. Google Cloud published an official tutorial on building skills for Gemini CLI using the same format.

> "Something shifted quietly in late 2025. Coding agents stopped being autocomplete tools and became actual collaborators." — [artifilog.com](https://www.artifilog.com/posts/must-have-claude-code-skills)

> "Agent skills are the new npm." — [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026)

**Sources:** [Claude Code Skills Docs](https://code.claude.com/docs/en/skills) · [Claude API Agent Skills Overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) · [Vercel Skills Changelog](https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem) · [Gemini CLI Creating Skills](https://geminicli.com/docs/cli/creating-skills/) · [SKILL.md Pattern (Medium)](https://bibek-poudel.medium.com/the-skill-md-pattern-how-to-write-ai-agent-skills-that-actually-work-72a3169dd7ee)

---

### 2. Marketplace Fragmentation: Six Ecosystems in 28 Days

February 2026 saw an extraordinary marketplace explosion: Anthropic, OpenAI, Perplexity, Superhuman, Google Cloud, and Oracle each shipped or expanded an agent marketplace within 28 days. The agent skill/plugin distribution layer has fragmented into competing ecosystems with radically different philosophies:

**By scale (raw volume):**
- **SkillsMP** (skillsmp.com): 425,000–500,000+ skills aggregated from GitHub. Independent, not affiliated with Anthropic or Vercel. Filters for 2+ GitHub stars (very low bar). Best for breadth, not quality signal.
- **LobeHub Skills** (lobehub.com/skills): 169,739 skills with strong community curation, detailed ratings, and a polished product experience. Multi-agent collaboration focus.
- **Skills.sh** (Vercel, vercel.com): 83,627 skills, 8M+ total installs. Launched Jan 20, 2026. Within 6 hours of announcement, the top skill had 20,000 installs. Better signal-to-noise than SkillsMP. Full CLI package manager (npx skills).
- **Anthropic Official** (marketplace.anthropic.com / claude.com/plugins): 55+ curated plugins (started with 36 in December 2025). Installable via /plugin install `<name>`@claude-plugins-official. Community ecosystem adds 72+ more from third-party marketplaces.

**By philosophy:**
- **claude-code-plugins-plus-skills** (tonsofskills.com): 423 plugins, 2,849 skills, 177 agents with the ccpi CLI package manager. Community-run.
- **SkillsDirectory**: runs automated security analysis using 50+ rules on every skill — one of the few taking security as a first-class feature.
- **Hermes Agent**: generates its own skills autonomously from experience rather than relying on manual installs — a radically different approach.

> "Six ecosystems in 28 days. The race is on." — [agentpmt.com](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days)

**Sources:** [SkillsMP](https://skillsmp.com) · [LobeHub Skills](https://lobehub.com/skills) · [Vercel Skills Docs](https://vercel.com/docs/agent-resources/skills) · [Vercel Skills KB](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context) · [vercel-labs/skills GitHub](https://github.com/vercel-labs/skills) · [claude-plugins-official GitHub](https://github.com/anthropics/claude-plugins-official) · [anthropics/claude-plugins-official marketplace.json](https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json) · [Anthropic Plugin Docs](https://code.claude.com/docs/en/discover-plugins) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [Six Marketplaces in 28 Days](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days) · [AI Agent Marketplaces 2026](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) · [Top 5 Agent Skill Marketplaces - KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) · [Skills.sh Guide](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) · [InfoQ Vercel Skills.sh](https://www.infoq.com/news/2026/02/vercel-agent-skills/) · [Dev Genius Analysis](https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481) · [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) · [SkillsLLM](https://skillsllm.com/) · [SkillsIndex MCP Guide](https://skillsindex.dev/blog/complete-guide-mcp-servers-2026/) · [ccpi/tonsofskills GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) · [Paperclipped.de explainer](https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/)

---

### 3. MCP Protocol: Explosive Growth, Universal Compatibility, Critical Vulnerabilities

The Model Context Protocol (MCP) has become the dominant open standard for connecting AI agents to external tools and APIs. As of April 2026:
- **500+ servers** across the official ecosystem; **4,133+** indexed on SkillsIndex; **7,000+** publicly accessible servers total
- **97 million monthly SDK downloads**
- Official client support across every major editor: Claude Desktop, Cursor, Windsurf, Claude Code
- A single MCP server configured once works everywhere

**New in 2026:** MCP Tool Search (lazy loading) reduces MCP context usage by up to 95%, solving the context-bloat problem that was holding back large server deployments.

**Security crisis is severe:** A comprehensive analysis found 43% of public MCP servers vulnerable to command execution, 36.7% to SSRF attacks, 492 servers exposed to the internet with zero authentication, and 53% using static credentials. **30+ CVEs were filed in 60 days.** The vulnerability ripples through a supply chain with 150M+ downloads, affecting up to 200,000 vulnerable instances.

A "by design" flaw in MCP allows unsanitized commands to execute silently — researchers at OX Security called it "the Mother of All AI Supply Chains." Tool poisoning attacks embed malicious instructions in tool descriptions; cross-server hijacking allows a malicious server to override trusted servers' tools.

> "The current implementation of the Model Context Protocol places the entire burden of security on the downstream developer — a structural failure that guarantees vulnerability at scale." — [OX Security](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/)

**Sources:** [Claude Code MCP Docs](https://code.claude.com/docs/en/mcp) · [Anthropic Desktop Extensions](https://www.anthropic.com/engineering/desktop-extensions) · [MCP in 2026 (blog)](https://atalupadhyay.wordpress.com/2026/04/19/mcp-in-2026-building-connected-ai-agents/) · [50+ Best MCP Servers](https://claudefa.st/blog/tools/mcp-extensions/best-addons) · [MCP Basics](https://claudefa.st/blog/tools/mcp-extensions/mcp-basics) · [EvoMap MCP Setup](https://evomap.ai/blog/claude-code-mcp-setup-extensions-guide) · [systemprompt.io MCP guide](https://systemprompt.io/guides/claude-code-mcp-servers-extensions) · [MCP Integration guide](https://thoughtminds.ai/blog/claude-mcp-integration-how-to-connect-claude-code-to-tools-via-mcp) · [Top 7 MCP Plugins](https://fast.io/resources/claude-mcp-plugins/) · [15 Best MCP Servers](https://www.taskade.com/blog/mcp-servers) · [How to Use MCP Servers](https://fungies.io/how-to-use-mcp-servers-2026/) · [MCP Extensions Guide (Morph)](https://www.morphllm.com/claude-code-extensions) · [MCP Security Crisis (gentic.news)](https://gentic.news/article/mcp-security-crisis-43-of-servers) · [State of MCP Security 2026](https://pipelab.org/blog/state-of-mcp-security-2026/) · [MCP Design Vulnerability (Hacker News)](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) · [OX Security MCP Report](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) · [SecurityWeek MCP Flaw](https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/) · [MCP 30 CVEs in 60 Days](https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/) · [IT Pro MCP Supply Chain](https://www.itpro.com/security/ai-agents-using-anthropic-mcp-supply-chain-attacks-claim-researchers) · [MCP DevSecOps](https://www.practical-devsecops.com/mcp-security-vulnerabilities/) · [AI Agent Security Risks](https://blog.cyberdesserts.com/ai-agent-security-risks/) · [Kraven Security MCP CTI](https://kravensecurity.com/mcp-servers-for-cti/) · [HN MCP Server](https://mcpservers.org/servers/GeorgeNance/hackernews-mcp) · [HN Agent Skill](https://mcpmarket.com/tools/skills/hacker-news-agent) · [Top Skills April 16, 2026](https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026)

---

### 4. Security Crisis: The Skills Supply Chain Under Attack

The speed of ecosystem growth has created a severe security environment. The timeline of attacks in Q1 2026 is alarming:

**February 5, 2026 — Snyk's ToxicSkills Audit:**
Scanned 3,984 skills from ClawHub and skills.sh:
- 36.82% (1,467 skills) had at least one security flaw
- 13.4% (534 skills) had critical-level issues (malware, prompt injection, exposed secrets)
- 76 confirmed malicious payloads
- 91% of malicious skills combine prompt injection with traditional malware

**February 2026 — ClawHub/clawdhub Campaign:**
First coordinated malware campaign against Claude Code and OpenClaw users. Antiy CERT confirmed 1,184 malicious skills across ClawHub at peak — approximately 1 in 5 packages. By mid-February: 824+ malicious skills across 12 publisher accounts. Five of the top 7 most-downloaded skills were confirmed malware. Barrier to publishing: one-week-old GitHub account. No code signing, security review, or sandboxing required.

**The "Lethal Trifecta"** (OWASP terminology): skills that simultaneously have access to private data + exposure to untrusted content + ability to communicate externally. Enables full exfiltration in three lines of markdown.

**Responses:**
- Snyk launched "Agent Scan" Skill Inspector tool
- Snyk + Vercel announced partnership to secure the agent skill ecosystem
- OWASP published the Agentic Skills Top 10 security framework
- OWASP Top 10 for Agentic Applications 2026 (100+ contributors)
- Best practices: ed25519 signing before publication, pin nested dependencies to immutable hashes, minimal permission manifests, safe YAML/JSON loaders

> "From SKILL.md to Shell Access in Three Lines of Markdown" — [Snyk](https://snyk.io/articles/skill-md-shell-access/)

> "36% of AI Agent Skills Have Security Flaws — Here's What You Can Do About It" — [SpecWeave](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/)

**Sources:** [Snyk ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) · [Snyk + Vercel Partnership](https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/) · [Snyk clawdhub Campaign](https://snyk.io/articles/clawdhub-malicious-campaign-ai-agent-skills/) · [Snyk Agent Scan](https://labs.snyk.io/resources/agent-scan-skill-inspector/) · [Snyk Introducing Agent Security](https://snyk.io/blog/introducing-agent-security/) · [Snyk SKILL.md Shell Access](https://snyk.io/articles/skill-md-shell-access/) · [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/) · [OWASP GitHub](https://github.com/OWASP/www-project-agentic-skills-top-10) · [OWASP Top 10 Agentic 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) · [Palo Alto OWASP](https://www.paloaltonetworks.com/blog/cloud-security/owasp-agentic-ai-security/) · [OWASP Cheat Sheet](https://blog.alexewerlof.com/p/owasp-top-10-ai-llm-agents) · [Auth0 OWASP Lessons](https://auth0.com/blog/owasp-top-10-agentic-applications-lessons/) · [Practical DevSecOps OWASP](https://www.practical-devsecops.com/owasp-top-10-agentic-applications/) · [Nishanc OWASP blog](https://blog.nishanc.com/2026/02/owasp-top-10-for-agentic-applications.html) · [Gravitee OWASP](https://www.gravitee.io/blog/owasp-top-10-for-agentic-applications-2026-a-practical-review-and-how-gravitee-supports-secure-agentic-architecture) · [DeepTeam OWASP](https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications) · [SpecWeave ToxicSkills](https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/) · [ClawHavoc Lessons](https://www.digitalapplied.com/blog/ai-agent-plugin-security-lessons-clawhavoc-2026) · [OpenClaw Security](https://blog.cyberdesserts.com/openclaw-malicious-skills-security/)

---

### 5. Claude Code's Native Extension Model: Skills, Plugins, Hooks, and Custom Agents

Claude Code's official extension model now has four distinct mechanisms:

1. **MCP Servers** — connect Claude to external tools, databases, APIs
2. **Skills** — teach Claude custom workflows, create `/skill-name` slash commands
3. **Custom Agents** — isolate tasks in their own context window
4. **Hooks** — shell commands that fire at 12–17 distinct lifecycle events

Hooks are particularly powerful for automation. `SessionStart` and `SessionEnd` bookend every session. `SessionStart` supports matchers (startup, resume, clear, compact) for different initialization logic. March 2026 added: MCP elicitation support, `StopFailure` hook, transcript search, more hook events, better streaming behavior, subprocess credential scrubbing, session display names, and sparse worktree paths.

The official Anthropic marketplace is browsable at `claude.com/plugins` and `marketplace.anthropic.com`. Install with `/plugin install <name>@claude-plugins-official`. Publishers can host custom marketplaces by exposing a manifest at any public URL.

LiteLLM's managed skills tutorial shows how to run the plugin marketplace in managed environments. The claude-code-workflow-plugins project wraps everything into composable workflows with automatic project memory.

> "Claude Code Plugins is an open-source add-on suite that turns Claude Code into a programmable workspace — composable workflows, automatic project memory, skill packs, lifecycle hooks, sub-agents, and typed commands, all wired with minimal config." — [MacroMan5/claude-code-workflow-plugins](https://github.com/MacroMan5/claude-code-workflow-plugins)

**Sources:** [Claude Code Plugins Docs](https://code.claude.com/docs/en/plugins) · [Claude Code Discover Plugins](https://code.claude.com/docs/en/discover-plugins) · [Claude Code Skills Docs](https://code.claude.com/docs/en/skills) · [claude-code/plugins/README.md](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) · [hook-development SKILL.md](https://github.com/anthropics/claude-code/blob/main/plugins/plugin-dev/skills/hook-development/SKILL.md) · [Hooks Guide](https://claudefa.st/blog/tools/hooks/hooks-guide) · [Hooks Tutorial](https://supalaunch.com/blog/claude-code-hooks-tutorial-automate-workflows-with-lifecycle-events-guide) · [Hooks Guide 2026](https://serenitiesai.com/articles/claude-code-hooks-guide-2026) · [Claude Code March Updates](https://www.builder.io/blog/claude-code-updates) · [Anthropic Marketplace Install Guide](https://systemprompt.io/guides/getting-started-anthropic-marketplace) · [LiteLLM Plugin Marketplace](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) · [claude-code-workflow-plugins](https://github.com/MacroMan5/claude-code-workflow-plugins) · [claude-code-workflows](https://github.com/shinpr/claude-code-workflows) · [Top 10 Claude Code Plugins DEV](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6) · [Groundy Official Ecosystem](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) · [aitmpl Plugins](https://www.aitmpl.com/plugins/) · [claudemarketplaces.com anthropics](https://claudemarketplaces.com/plugins/anthropics-claude-code) · [buildwithclaude.com](https://buildwithclaude.com/) · [Pete Gypps 36 Plugins Guide](https://www.petegypps.uk/blog/claude-code-official-plugin-marketplace-complete-guide-36-plugins-december-2025) · [wshobson/agents](https://github.com/wshobson/agents)

---

### 6. Community Skill Libraries and the Creator Economy

An entire skill creator economy has emerged in Q1 2026:

**Official resources:**
- `anthropics/skills` — Anthropic's public repository for official Agent Skills
- Skill Creator v2 — Anthropic's tool for building, reviewing, and improving skills (YouTube tutorial by Anthropic)
- Plugin-dev skills inside `anthropics/claude-code` itself (meta: skills for building skills)

**Community libraries:**
- `VoltAgent/awesome-agent-skills` — 1,000+ curated skills for Claude Code, Codex, Gemini CLI, Cursor, etc.
- `heilcheng/awesome-agent-skills` — tutorials, guides, and directory links
- `alirezarezvani/claude-skills` — 232+ skills covering engineering, marketing, product, compliance, C-level advisory
- `FrancyJGLisboa/agent-skill-creator` — tool to convert any workflow into a SKILL.md for 14+ platforms

**YouTube tutorial surge:**
- "The best way to create agent skills in 2026" — [youtube.com/watch?v=XCOkCwgKwAA](https://www.youtube.com/watch?v=XCOkCwgKwAA)
- "How to Create Claude Code Agent Skills in 2026" — [youtube.com/watch?v=nbqqnl3JdR0](https://www.youtube.com/watch?v=nbqqnl3JdR0)
- "Build Better AI Agent Skills With Skill Creator v2 from Anthropic" — [youtube.com/watch?v=WplS5lycPHM](https://www.youtube.com/watch?v=WplS5lycPHM)

**Blog coverage:**
- Medium: "10 Must-Have Skills for Claude (and Any Coding Agent) in 2026" by @unicodeveloper
- Firecrawl blog: "Best Claude Code Skills to Try in 2026"
- Composio: "Top 10 Claude Code Skills Every Builder Should Know"
- Batsov.com: "Essential Claude Code Skills and Commands" (March 11, 2026)
- Google Cloud Community Medium: skills with Gemini CLI

> "As of March 2026, the Claude Code skill ecosystem includes official Anthropic skills, verified third-party skills, and thousands of community-created skills." — [artifilog.com](https://www.artifilog.com/posts/must-have-claude-code-skills)

**Sources:** [anthropics/skills GitHub](https://github.com/anthropics/skills) · [anthropics/claude-code GitHub](https://github.com/anthropics/claude-code) · [VoltAgent awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) · [heilcheng awesome-agent-skills](https://github.com/heilcheng/awesome-agent-skills) · [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) · [FrancyJGLisboa agent-skill-creator](https://github.com/FrancyJGLisboa/agent-skill-creator) · [YouTube XCOkCwgKwAA](https://www.youtube.com/watch?v=XCOkCwgKwAA) · [YouTube nbqqnl3JdR0](https://www.youtube.com/watch?v=nbqqnl3JdR0) · [YouTube WplS5lycPHM](https://www.youtube.com/watch?v=WplS5lycPHM) · [Medium unicodeveloper](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) · [Firecrawl Best Skills](https://www.firecrawl.dev/blog/best-claude-code-skills) · [Artifilog Must-Have Skills](https://www.artifilog.com/posts/must-have-claude-code-skills) · [Composio Top 10 Skills](https://composio.dev/content/top-claude-skills) · [Batsov.com Skills Guide](https://batsov.com/articles/2026/03/11/essential-claude-code-skills-and-commands/) · [Google Cloud Medium Skills](https://medium.com/google-cloud/building-agent-skills-with-skill-creator-855f18e785cf) · [scriptbyai.com Resource List](https://www.scriptbyai.com/claude-code-resource-list/) · [Awesome Claude](https://awesomeclaude.ai) · [Chris Ayers Complete Guide](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) · [Agent Skills Are New npm](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) · [SkillsMP Downloader](https://lobehub.com/skills/seankim-business-corp-system-skillsmp-downloader) · [skill-creator on LobeHub](https://lobehub.com/skills/agent-skills-hub-agent-skills-hub-skill-creator) · [universal-skills-manager](https://lobehub.com/skills/agent-arc-744-kryllax-universal-skills-manager) · [self-improve skill](https://lobehub.com/skills/different-ai-agent-bank-self-improve) · [LobeHub GitHub](https://github.com/lobehub/lobehub) · [agensi.io Marketplace Guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) · [LobeHub Top 20](https://lobehub.com/skills?category=all)

---

## Cross-Source Patterns

### Pattern 1: SKILL.md as the New Cross-Platform Lingua Franca

**Appeared on:** Official docs (Anthropic, Vercel, Gemini CLI), GitHub (15+ repos), Medium, YouTube, InfoQ, KDnuggets, Paperclipped

The SKILL.md format has achieved cross-platform consensus faster than any prior AI tooling standard. Anthropic shipped it in December 2025; Vercel launched skills.sh on January 20, 2026; OpenAI adopted it for Codex CLI; Google adopted it for Gemini CLI. The ecosystem grew from 0 to 500,000+ indexed skills within ~4 months. The "one SKILL.md, 14+ platforms" pitch is the dominant message across all tutorial content.

**Key quotes:**
- "Think of it as npm for agent behaviors." — [johnoct.github.io](https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/)
- "Within six hours of Vercel announcing skills.sh, the top skill had over 20,000 installs." — [virtualuncle.com](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/)

---

### Pattern 2: Security Is the Ecosystem's Critical Threat

**Appeared on:** Snyk (4 posts), OX Security, SecurityWeek, The Hacker News, IT Pro, Gentic.news, PipeLab, OWASP, Practical DevSecOps, cyberdesserts.com, SpecWeave, Gravitee, Palo Alto Networks

The speed of ecosystem growth has outpaced security infrastructure. The numbers are consistent across multiple independent sources: ~36% of skills have flaws, ~13% have critical issues. The ClawHub malware campaign was confirmed by Antiy CERT. The MCP protocol's design is being called structurally insecure at the protocol level (not just implementation level). This is not fringe reporting — OWASP published a dedicated framework, Snyk launched a new product line, and SecurityWeek/Hacker News covered the MCP design flaw.

**Key quotes:**
- "91% of malicious skills combine prompt injection with traditional malware — a convergence that bypasses both AI safety mechanisms and traditional security tools." — [Snyk ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)
- "Five of the top seven most-downloaded skills at peak infection confirmed as malware." — [OWASP Agentic Skills Top 10](https://owasp.org/www-project-agentic-skills-top-10/)

---

### Pattern 3: Marketplace Fragmentation vs. Consolidation Tension

**Appeared on:** KDnuggets, agentpmt.com, digitalapplied.com, virtualuncle.com, paperclipped.de, InfoQ, Dev Genius

Multiple competing marketplaces with incompatible curation philosophies (raw volume vs. quality signal vs. security-first) are serving the same underlying SKILL.md standard. The tension between fragmentation and the need for a single trusted registry is a recurring theme. Skills.sh and the official Anthropic marketplace are positioning for the "trusted canonical" role; SkillsMP is positioning for comprehensiveness.

---

### Pattern 4: The Extension Model is Becoming Standard Developer Infrastructure

**Appeared on:** Claude Code official docs, Morph, EvoMap, claudefa.st, Composio, DEV Community, builder.io, Batsov.com, systemprompt.io

Skills, hooks, MCP servers, and custom agents are no longer "power user" features — they are the standard developer workflow for Claude Code in 2026. The March 2026 update expanded the hook system significantly. The conversation has shifted from "what are skills?" to "which skills should every developer have installed?"

---

## Per-Platform Tables

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Skills Docs | https://code.claude.com/docs/en/skills | Official SKILL.md spec and lazy-loading architecture |
| Claude Code MCP Docs | https://code.claude.com/docs/en/mcp | Official MCP integration guide |
| Claude Code Plugins Docs | https://code.claude.com/docs/en/plugins | Plugin creation and hook lifecycle |
| Claude Code Discover Plugins | https://code.claude.com/docs/en/discover-plugins | Marketplace discovery guide |
| Claude API Agent Skills | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | API-level skills overview |
| Vercel Skills Changelog | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | Skills.sh launch announcement (Jan 20, 2026) |
| Vercel Skills Docs | https://vercel.com/docs/agent-resources/skills | Official Vercel skills documentation |
| Vercel Skills KB | https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context | Creating, installing, sharing skills |
| Snyk ToxicSkills | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | 36% flaw rate, 13.4% critical — the headline security audit |
| Snyk + Vercel Partnership | https://snyk.io/blog/snyk-vercel-securing-agent-skill-ecosystem/ | Joint security response for skills ecosystem |
| Snyk clawdhub Campaign | https://snyk.io/articles/clawdhub-malicious-campaign-ai-agent-skills/ | Inside the first coordinated malware campaign |
| Snyk Agent Scan | https://labs.snyk.io/resources/agent-scan-skill-inspector/ | New product: detect malicious skills instantly |
| Snyk Introducing Agent Security | https://snyk.io/blog/introducing-agent-security/ | Snyk's agent security product line launch |
| Snyk SKILL.md Shell Access | https://snyk.io/articles/skill-md-shell-access/ | Technical analysis: shell in 3 lines of markdown |
| OWASP Agentic Skills Top 10 | https://owasp.org/www-project-agentic-skills-top-10/ | Security framework specific to skills |
| OWASP GitHub | https://github.com/OWASP/www-project-agentic-skills-top-10 | OWASP framework source |
| OWASP Top 10 Agentic 2026 | https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/ | Broader agentic application security |
| OX Security MCP Report | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | "Mother of All AI Supply Chains" — MCP design flaw |
| SecurityWeek MCP Flaw | https://www.securityweek.com/by-design-flaw-in-mcp-could-enable-widespread-ai-supply-chain-attacks/ | Press coverage of MCP design vulnerability |
| The Hacker News MCP | https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html | RCE via MCP design vulnerability (April 2026) |
| IT Pro MCP | https://www.itpro.com/security/ai-agents-using-anthropic-mcp-supply-chain-attacks-claim-researchers | Supply chain attack vector via MCP |
| MCP Security Crisis | https://gentic.news/article/mcp-security-crisis-43-of-servers | 43% vulnerable, 341 malicious skills confirmed |
| State of MCP Security 2026 | https://pipelab.org/blog/state-of-mcp-security-2026/ | Comprehensive security incident analysis |
| MCP 30 CVEs | https://www.heyuan110.com/posts/ai/2026-03-10-mcp-security-2026/ | 30 CVEs in 60 days — root cause analysis |
| MCP in 2026 (blog) | https://atalupadhyay.wordpress.com/2026/04/19/mcp-in-2026-building-connected-ai-agents/ | Current state of MCP as of April 19, 2026 |
| Anthropic Desktop Extensions | https://www.anthropic.com/engineering/desktop-extensions | One-click MCP installation for Claude Desktop |
| Anthropic Official Marketplace | https://marketplace.anthropic.com | Official plugin marketplace |
| claude-plugins-official GitHub | https://github.com/anthropics/claude-plugins-official | Anthropic's curated plugin directory |
| marketplace.json | https://github.com/anthropics/claude-plugins-official/blob/main/.claude-plugin/marketplace.json | Marketplace manifest |
| anthropics/skills GitHub | https://github.com/anthropics/skills | Anthropic's public skills repository |
| vercel-labs/skills GitHub | https://github.com/vercel-labs/skills | Open agent skills tool (npx skills) |
| SkillsMP | https://skillsmp.com | 500k+ skills marketplace |
| LobeHub Skills | https://lobehub.com/skills | 169k+ skills marketplace |
| LobeHub GitHub | https://github.com/lobehub/lobehub | LobeHub platform source |
| SkillsLLM | https://skillsllm.com/ | AI skills marketplace |
| Awesome Claude | https://awesomeclaude.ai | Claude resource directory |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Plugin/skills/MCP directory |
| SkillsIndex MCP Guide | https://skillsindex.dev/blog/complete-guide-mcp-servers-2026/ | 4,133+ MCP servers indexed |
| InfoQ Vercel Skills | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Skills.sh launch coverage |
| KDnuggets Top 5 Marketplaces | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Independent analysis of top marketplaces |
| Six Marketplaces in 28 Days | https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days | February 2026 marketplace explosion |
| AI Agent Marketplaces 2026 | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | Discovery and distribution analysis |
| ClawHavoc Lessons | https://www.digitalapplied.com/blog/ai-agent-plugin-security-lessons-clawhavoc-2026 | Plugin security lessons from the attack |
| AI Agent Security Risks | https://blog.cyberdesserts.com/ai-agent-security-risks/ | MCP, OpenClaw, supply chain risk overview |
| OpenClaw Security | https://blog.cyberdesserts.com/openclaw-malicious-skills-security/ | OpenClaw ecosystem security analysis |
| DEV My Predictions MCP | https://dev.to/blackgirlbytes/my-predictions-for-mcp-and-ai-assisted-coding-in-2026-16bm | Community predictions for MCP in 2026 |
| DEV Top 10 Plugins | https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 | Developer community plugin picks |
| Medium unicodeveloper | https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 | 10 must-have skills guide (March 2026) |
| Medium SKILL.md Pattern | https://bibek-poudel.medium.com/the-skill-md-pattern-how-to-write-ai-agent-skills-that-actually-work-72a3169dd7ee | How to write SKILL.md effectively |
| Google Cloud Medium Skills | https://medium.com/google-cloud/building-agent-skills-with-skill-creator-855f18e785cf | Official Google Cloud skills tutorial |
| Dev Genius Skills Analysis | https://blog.devgenius.io/i-analysed-the-top-10-skills-on-vercels-new-ai-agent-registry-480c69e9d481 | Analysis of top skills on skills.sh |
| johnoct.github.io skills.sh | https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/ | Skills.sh as missing package manager |
| Skills.sh Guide | https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/ | Comprehensive skills.sh guide |
| Paperclipped Explainer | https://www.paperclipped.de/en/blog/ai-agent-skills-marketplace/ | SKILL.md, Skills.sh, SkillsMP explained |
| buildmvpfast.com | https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026 | Agent skills as new npm |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate Claude Code resource list |
| Hooks Guide | https://claudefa.st/blog/tools/hooks/hooks-guide | Complete guide to lifecycle hooks |
| Hooks Tutorial | https://supalaunch.com/blog/claude-code-hooks-tutorial-automate-workflows-with-lifecycle-events-guide | Lifecycle hooks automation |
| Hooks Guide 2026 | https://serenitiesai.com/articles/claude-code-hooks-guide-2026 | Hooks guide for 2026 |
| Claude Code March Updates | https://www.builder.io/blog/claude-code-updates | March 2026 Claude Code update breakdown |
| Claude Code Extensions | https://www.morphllm.com/claude-code-extensions | MCP, Skills, Agents, Hooks guide |
| EvoMap MCP Setup | https://evomap.ai/blog/claude-code-mcp-setup-extensions-guide | MCP setup and extension guide |
| systemprompt.io MCP | https://systemprompt.io/guides/claude-code-mcp-servers-extensions | MCP servers and extensions overview |
| systemprompt.io Marketplace | https://systemprompt.io/guides/getting-started-anthropic-marketplace | Anthropic marketplace getting started |
| MCP Integration | https://thoughtminds.ai/blog/claude-mcp-integration-how-to-connect-claude-code-to-tools-via-mcp | Claude Code MCP integration |
| Top 7 MCP Plugins | https://fast.io/resources/claude-mcp-plugins/ | Fastio's top MCP plugin picks |
| 15 Best MCP Servers | https://www.taskade.com/blog/mcp-servers | Taskade's tested MCP server list |
| 50+ Best MCP Servers | https://claudefa.st/blog/tools/mcp-extensions/best-addons | Comprehensive MCP server directory |
| MCP Basics | https://claudefa.st/blog/tools/mcp-extensions/mcp-basics | MCP fundamentals |
| How to Use MCP Servers | https://fungies.io/how-to-use-mcp-servers-2026/ | Developer guide to MCP servers |
| MCP CTI | https://kravensecurity.com/mcp-servers-for-cti/ | MCP for cyber threat intelligence |
| MCP DevSecOps | https://www.practical-devsecops.com/mcp-security-vulnerabilities/ | Prompt injection and tool poisoning defense |
| MCP CTI Security | https://blog.cyberdesserts.com/ai-agent-security-risks/ | Security risk overview |
| HN MCP Server | https://mcpservers.org/servers/GeorgeNance/hackernews-mcp | Hacker News MCP server |
| HN Agent Skill | https://mcpmarket.com/tools/skills/hacker-news-agent | Hacker News skill for Claude Code |
| Top Skills April 16 | https://mcpmarket.com/daily/skills/top-skill-list-april-16-2026 | mcpmarket.com daily leaderboard |
| LiteLLM Plugin Marketplace | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Managed skills via LiteLLM |
| Agensi.io Marketplace Guide | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Complete marketplace guide |
| aitmpl Plugins | https://www.aitmpl.com/plugins/ | Plugins and marketplace collections |
| Pete Gypps 36 Plugins | https://www.petegypps.uk/blog/claude-code-official-plugin-marketplace-complete-guide-36-plugins-december-2025 | December 2025 launch coverage |
| Groundy Official Ecosystem | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Anthropic official ecosystem explained |
| buildwithclaude.com | https://buildwithclaude.com/ | Build with Claude plugin marketplace |
| Firecrawl Best Skills | https://www.firecrawl.dev/blog/best-claude-code-skills | Best Claude Code skills to try |
| Artifilog Skills Guide | https://www.artifilog.com/posts/must-have-claude-code-skills | Must-have skills practical guide |
| Composio Top 10 Skills | https://composio.dev/content/top-claude-skills | Top 10 skills every builder should know |
| Batsov.com Skills | https://batsov.com/articles/2026/03/11/essential-claude-code-skills-and-commands/ | Essential skills and commands (March 2026) |
| Chris Ayers Complete Guide | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Agent skills plugins marketplace guide |
| SpecWeave ToxicSkills | https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/ | Why skills need verification |
| Palo Alto OWASP | https://www.paloaltonetworks.com/blog/cloud-security/owasp-agentic-ai-security/ | Enterprise OWASP implications |
| Auth0 OWASP Lessons | https://auth0.com/blog/owasp-top-10-agentic-applications-lessons/ | Auth lessons from OWASP agentic |
| Practical DevSecOps OWASP | https://www.practical-devsecops.com/owasp-top-10-agentic-applications/ | DevSecOps OWASP guide |
| Nishanc OWASP | https://blog.nishanc.com/2026/02/owasp-top-10-for-agentic-applications.html | OWASP agentic security guide |
| Gravitee OWASP | https://www.gravitee.io/blog/owasp-top-10-for-agentic-applications-2026-a-practical-review-and-how-gravitee-supports-secure-agentic-architecture | Practical OWASP review |
| DeepTeam OWASP | https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications | OWASP framework for red teaming |
| Awesome Claude | https://awesomeclaude.ai | Claude resource directory |
| OWASP Cheat Sheet | https://blog.alexewerlof.com/p/owasp-top-10-ai-llm-agents | OWASP agents cheat sheet |

**YouTube:**
| Channel/Creator | Title | URL |
|-----------------|-------|-----|
| Unknown Creator | The best way to create agent skills in 2026 | https://www.youtube.com/watch?v=XCOkCwgKwAA |
| Unknown Creator | How to Create Claude Code Agent Skills in 2026 | https://www.youtube.com/watch?v=nbqqnl3JdR0 |
| Anthropic/Creator | Build Better AI Agent Skills With Skill Creator v2 from Anthropic | https://www.youtube.com/watch?v=WplS5lycPHM |

**GitHub Repos:**
| Repo | Stars / Scale | URL |
|------|--------------|-----|
| anthropics/claude-plugins-official | Official, 55+ plugins | https://github.com/anthropics/claude-plugins-official |
| anthropics/skills | Official Anthropic skills | https://github.com/anthropics/skills |
| anthropics/claude-code | Official Claude Code (plugins dir) | https://github.com/anthropics/claude-code |
| vercel-labs/skills | Official Vercel skills.sh | https://github.com/vercel-labs/skills |
| jeremylongshore/claude-code-plugins-plus-skills | 423 plugins, 2,849 skills, 177 agents | https://github.com/jeremylongshore/claude-code-plugins-plus-skills |
| alirezarezvani/claude-skills | 232+ skills | https://github.com/alirezarezvani/claude-skills |
| VoltAgent/awesome-agent-skills | 1,000+ curated skills | https://github.com/VoltAgent/awesome-agent-skills |
| FrancyJGLisboa/agent-skill-creator | Workflow-to-skill converter | https://github.com/FrancyJGLisboa/agent-skill-creator |
| heilcheng/awesome-agent-skills | Tutorials and directories | https://github.com/heilcheng/awesome-agent-skills |
| wshobson/agents | Multi-agent orchestration | https://github.com/wshobson/agents |
| MacroMan5/claude-code-workflow-plugins | Composable workflow plugins | https://github.com/MacroMan5/claude-code-workflow-plugins |
| shinpr/claude-code-workflows | Production-ready agent workflows | https://github.com/shinpr/claude-code-workflows |
| lobehub/lobehub | Multi-agent collaboration platform | https://github.com/lobehub/lobehub |
| OWASP/www-project-agentic-skills-top-10 | OWASP security framework | https://github.com/OWASP/www-project-agentic-skills-top-10 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads scraped (search returned no direct Reddit threads)
├─ 🔵 X: 0 posts scraped (excluded per instructions)
├─ 🔴 YouTube: 3 videos identified │ views N/A │ 0 with transcripts
├─ 🟢 HN: 0 stories directly retrieved │ MCP/skills frequently discussed
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 85+ pages across 13 search queries │ 14 GitHub repos │ 3 YouTube
└─ 🗣️ Top voices: @unicodeveloper (Medium), Snyk Research, OX Security, Vercel Team │
     r/claudeai, r/ClaudeCode (not directly retrieved but primary community venues)
```

---

## Data Gaps

- **Reddit:** No Reddit threads were directly retrieved. Reddit discussions about Claude Code skills, MCP security, and plugin ecosystems are active (primary subreddits: r/ClaudeAI, r/ClaudeCode) but were not captured in these search queries due to reddit.com exclusion per instructions.
- **X/Twitter:** Excluded per instructions. The @AnthropicAI, @vercel, and security researcher accounts would have real-time commentary on the MCP security crisis.
- **Hacker News:** No HN story data (upvotes/comments) was directly retrieved, though the MCP design vulnerability made the front page in April 2026. HN discussions on skills.sh launch and ClawHub attacks would be significant.
- **TikTok/Instagram/Bluesky:** Not captured. Developer content on these platforms is growing but search queries did not surface structured data.
- **Polymarket:** No prediction markets found on agent skills/MCP topics.
- **Engagement metrics:** Most sources retrieved without view counts, like counts, or upvote data — only URLs and content.
- **Coverage estimate:** ~75% of the English-language written content on this topic captured; social media and forum discussions (40%+ of the conversation) are underrepresented.
- **Noise:** The term "agent skills" is sometimes used generically (human employee skills in AI context) — filtered out. "Claude skills" as job market term filtered out.

---

## Key Quotes

> "From SKILL.md to Shell Access in Three Lines of Markdown" — Snyk Security Research ([link](https://snyk.io/articles/skill-md-shell-access/))

> "The current implementation of the Model Context Protocol places the entire burden of security on the downstream developer — a structural failure that guarantees vulnerability at scale." — OX Security ([link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/))

> "91% of malicious skills combine prompt injection with traditional malware — a convergence that bypasses both AI safety mechanisms and traditional security tools." — Snyk ToxicSkills ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Within six hours of Vercel announcing skills.sh, the top skill had over 20,000 installs." — virtualuncle.com ([link](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/))

> "Something shifted quietly in late 2025. Coding agents stopped being autocomplete tools and became actual collaborators." — artifilog.com ([link](https://www.artifilog.com/posts/must-have-claude-code-skills))

> "Agent skills are the new npm." — buildmvpfast.com ([link](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026))

> "Six ecosystems in 28 days. The race is on." — agentpmt.com ([link](https://www.agentpmt.com/articles/six-agent-marketplaces-in-28-days))

> "Five of the top seven most-downloaded skills at peak infection were confirmed malware." — OWASP Agentic Skills Top 10 ([link](https://owasp.org/www-project-agentic-skills-top-10/))

> "Think of it as npm for agent behaviors — but with a security landscape closer to the early npm days." — johnoct.github.io ([link](https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/))

> "One SKILL.md, every platform." — FrancyJGLisboa/agent-skill-creator ([link](https://github.com/FrancyJGLisboa/agent-skill-creator))
