# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-23
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web, X/Twitter, YouTube, TikTok

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 9 stories | 1,559+ points, 800+ comments | 2 fully retrieved; 5 rate-limited (HTTP 429) |
| GitHub | 8 repos | 5,200+ stars top repo | Topics: claude-code-skills, claude-skills |
| Web | 55 pages | — | Blogs, docs, marketplace guides, security reports |
| X/Twitter | 1+ posts | Partial | @Praiseakinlami confirmed; @simonw widely referenced |
| YouTube | 4 videos | 853K+ views (top reported) | Tutorials ranging beginner to advanced |
| TikTok | 1+ videos | Viral (exact counts unavailable) | @rileybrown.ai MCP tutorial |
| Reddit | 0 direct | 4,200+ weekly r/ClaudeCode contributors | Reddit not indexable via web search |
| Polymarket | 0 markets | — | No prediction markets found on this topic; MCP→Polymarket servers exist |

---

## Synthesized Findings

### 1. The Agent Skills Standard: Anthropic's Second Standard-Setting Move

On **October 16, 2025**, Anthropic published the Agent Skills framework alongside an engineering blog post authored by Barry Zhang, Keith Lazuka, and Mahesh Murag. The formal open standard was released **December 18, 2025**. Within 48 hours, Microsoft integrated it into VS Code and OpenAI added it to both ChatGPT and Codex CLI. By March 2026, **32 tools** from competing companies — including Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose — all read the same `SKILL.md` files from the same directory structure.

Analyst coverage framed this explicitly as Anthropic's playbook from MCP repeated: launch a useful internal format, open-source the spec, and let community adoption establish it as the de facto standard. *"Anthropic is doing with Agent Skills what it did with MCP,"* wrote Jannis in The Context Layer ([link](https://medium.com/the-context-layer/anthropic-is-doing-with-agent-skills-what-it-did-with-mcp-7068a15e72da)). The New Stack called it "Anthropic's Next Bid to Define AI Standards" ([link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/)).

**Technical spec:** A skill is a directory containing a `SKILL.md` file with YAML frontmatter specifying `name` and `description`. Progressive disclosure operates in three levels: (1) names and descriptions loaded at startup (~30–50 tokens per skill), (2) full `SKILL.md` when Claude determines relevance, (3) additional bundled files referenced contextually. Executable scripts are supported, enabling deterministic code rather than expensive token generation for algorithmic tasks ([source](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)).

The standard is documented at [agentskills.io](https://agentskills.io/home) and the reference GitHub repository is at [agentskills/agentskills](https://github.com/agentskills/agentskills). Anthropic's official skills live at [anthropics/skills](https://github.com/anthropics/skills).

**Cross-platform:** Agent Skills are available in Claude apps (Pro/Max/Team/Enterprise), the Messages API via `/v1/skills` endpoint, Claude Code via the plugin marketplace, and the Claude Agent SDK ([claude.com/blog/skills](https://claude.com/blog/skills)).

*Platforms: Web, Hacker News, YouTube*

---

### 2. Skills vs. MCP: A Debate About Tokens, Complexity, and Philosophy

The sharpest intellectual debate in this space concerns whether Agent Skills and MCP are competitors or complements — and whether Skills represent genuine architectural progress or rebranded prompt engineering.

**Simon Willison's case for Skills:** In his October 16, 2025 post ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/)), Willison argued Skills win on token economics and conceptual simplicity: *"While MCP requires an elaborate protocol specification covering hosts, clients, servers, and multiple transports, skills embrace simplicity: Markdown with a tiny bit of YAML metadata and some optional scripts."* GitHub's official MCP implementation alone consumes tens of thousands of context tokens; each skill consumes 30–50. He predicted a "Cambrian explosion" in skills adoption potentially dwarfing MCP's initial rush.

**The HN counterarguments:** The thread "Claude Skills are awesome, maybe a bigger deal than MCP" ([HN, 738pts/370c](https://news.ycombinator.com/item?id=45619537)) saw substantive pushback. Commenter **tptacek** argued the real breakthrough is tool calls themselves, not MCP specifically: *"MCP is merely one implementation among possibilities, and perhaps not the optimal one."* Commenter **causal** called skills *"instructions with RAG,"* questioning whether the rebranding merited the announcement. Commenter **michael1999** offered a more sympathetic read: context documents for AI resemble good developer docs but are created far more readily because *"developers feel motivated improving their 'digital goblin' rather than abstract colleagues"* — solving the principal-agent problem that has historically killed internal documentation.

**The consensus resolution:** Skills and MCP are complementary. *"MCP provides the 'plumbing' for tool access, while agent skills provide the 'brain' or procedural memory for how to use those tools effectively,"* summarized Willison. MCP was simultaneously donated to the Agentic AI Foundation (AAIF) under the Linux Foundation, co-founded by Anthropic, Block, and OpenAI ([Anthropic](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation); [CIO Dive](https://www.ciodive.com/news/big-tech-develop-open-standards-agentic-ai/807608/)). By May 2026, MCP has **10,000+ active public MCP servers** and is embedded in ChatGPT, Cursor, Gemini, Microsoft Copilot, and VS Code ([Pento](https://www.pento.ai/blog/a-year-of-mcp-2025-review)).

Practical guidance from MorphLLM: *"Skills are on-demand; CLAUDE.md is always-loaded context. Most workflows benefit from both: MCP for connectivity, Skills for methodology."* ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

*Platforms: Hacker News, Web*

---

### 3. The Plugin Packaging Layer: How Skills Get Bundled and Distributed

Above the skill layer sits a **plugin packaging format** — shareable bundles containing skills, MCP servers, agents, hooks, LSP servers, and monitors, installable via a plugin.json manifest. Claude Code supports four extension types: MCP servers, Skills, custom Agents, and Hooks.

Key GitHub repositories illustrate ecosystem density:
- **alirezarezvani/claude-skills** ([GitHub](https://github.com/alirezarezvani/claude-skills)): 5,200+ stars, 313+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8 more agents
- **jeremylongshore/claude-code-plugins-plus-skills** ([GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)): 2,200 stars, 425 plugins, 2,810 skills, 200 agents; CLI: `pnpm add -g @intentsolutionsio/ccpi`; marketplace at [tonsofskills.com](https://tonsofskills.com/)
- **ComposioHQ/awesome-claude-plugins** ([GitHub](https://github.com/ComposioHQ/awesome-claude-plugins)): 1,700 stars; curated production-ready extensions
- **ComposioHQ/awesome-claude-skills** ([GitHub](https://github.com/ComposioHQ/awesome-claude-skills)): 1,000+ practical cross-platform skills

Notable extensions: The **Morph MCP server** is the most-installed Claude Code extension (35% faster edits via FastApply; 40% context reduction via WarpGrep parallel codebase search). The **feature-dev plugin** has 89,000+ installs and runs a seven-phase workflow (requirements → exploration → architecture → implementation → testing → review → documentation). The **connect-apps** plugin links Claude to Gmail, Slack, GitHub, Notion, and 500+ services.

GitHub added a first-party CLI with `gh skill install` ([DEV Community](https://dev.to/om_shree_0709/gh-skill-githubs-new-cli-command-turns-agent-skills-into-installable-packages-2p82)), embedding provenance metadata in `SKILL.md` frontmatter (source repo, ref, tree SHA) and enabling content validation on updates. Vercel launched **skills.sh** on January 20, 2026 — npm-style package manager for agent capabilities; its top skill hit 20,000 installs within 6 hours ([skills.sh](http://skills.sh); [John's blog](https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/)).

*Platforms: GitHub, Web*

---

### 4. Marketplace Fragmentation: Eight Directories, No Single Winner

The discovery layer has splintered into at least 8 distinct marketplaces, each with different curation models, size claims, and security postures:

| Marketplace | Size | Curation | Security Review | Creator Payments | URL |
|-------------|------|----------|-----------------|------------------|-----|
| SkillsMP | 1.46M skills (from GitHub) | Minimal (≥2 stars filter) | None | No | [skillsmp.com](https://skillsmp.com/) |
| LobeHub | 169,739 skills | Aggregated | None | No | [lobehub.com/skills](https://lobehub.com/skills) |
| agentskill.sh | 110,000+ | Moderate | Security scores shown | No | [agentskill.sh](http://agentskill.sh) |
| skills.sh | 87,000–89,753 | None (public leaderboard) | None | No | [skills.sh](http://skills.sh) |
| Claude Marketplaces | 6,700+ skills, 2,500+ marketplaces | Community | None | No | [claudemarketplaces.com](https://claudemarketplaces.com/) |
| ClawHub | 20,000+ | Registry | Security scan shown | No | [clawhub.ai](https://clawhub.ai/) |
| Agensi | 200+ | 8-point security scan | Yes | 80/20 split | [agensi.io](https://www.agensi.io/) |
| Anthropic Official | ~20 | Anthropic-audited | Internal | No | [anthropics/skills](https://github.com/anthropics/skills) |

Key insight: headline numbers mask quality concerns. SkillsMP's 1.46M figure includes 79% classified across occupational categories — it functions more as a skills ontology than a curated tool catalog. Agensi is the only marketplace running security scans before listing and sharing revenue with creators. Analysis projects consolidation to 3–4 dominant platforms by Q4 2026, with creator payments and security scanning becoming standard features ([Agensi guide](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026); [KDNuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents)).

*Platforms: Web, Hacker News*

---

### 5. Monetization: The Creator Payment Problem

There is no established revenue model for skill creators. The HN thread "Show HN: Agent37 – Monetize your Claude skills with shareable links" ([5pts, 3c](https://news.ycombinator.com/item?id=46422134)) surfaced the core problem: *"There are 1,000+ MCP skills on GitHub with zero way for creators to charge for them."*

Agent37 ([agent37.com](https://agent37.com)) attempts to solve this with instant skill testing (no Claude account required) + built-in Stripe payments + 80% creator revenue share. One non-technical creator reportedly earned $1,600. Agensi offers the same 80/20 split with security scanning. But both face a structural challenge: skills are Markdown files — trivially copyable once downloaded, unlike SaaS subscriptions.

This contrasts sharply with the GPT Store model: custom GPTs are sandboxed within OpenAI's interface, making monetization more viable. Agent Skills' portability — their key ecosystem advantage — is simultaneously the barrier to paywalling them.

*Platforms: Hacker News, Web*

---

### 6. Security: The Ecosystem's Growing Attack Surface

The rapid proliferation of MCP servers and agent skills has outpaced security tooling. A layered threat model has emerged:

**MCP server vulnerabilities (BlueRock Security, 2026 analysis of ~7,000 servers):**
- 36.7% vulnerable to SSRF (server-side request forgery)
- 41% require no authentication
- 53% of authenticated servers rely on static API keys
- Only 8.5% use OAuth

**Skill-level threats:**
- Agensi audit of 22,511 skills: 140,963 issues, avg 6.3 per skill; prompt injection in 36% of skills tested
- 43% of public MCP servers have at least one exploitable vulnerability
- Tool poisoning: malicious instructions in tool metadata — *"The poisoned tool doesn't even need to be called — just being loaded into context is enough for the model to follow its hidden instructions"*
- ClawHub reportedly poisoned at scale (first AI agent registry systematic poisoning)

**Claude Code–specific:**
- CVE-2025-59536 (CVSS 8.7): configuration injection via `.claude/settings.json` in a repository; remote code execution when a developer opens the project (disclosed Feb 25, 2026)
- Agnix lint tool emerged to validate Claude.md, skills, MCP, and hooks configs ([HN](https://news.ycombinator.com/item?id=46983879))

**Enterprise response:**
- AWS and Cisco AI Defense deploying MCP gateways for centralized auth, auditing, and traffic management ([AWS](https://aws.amazon.com/blogs/machine-learning/securing-ai-agents-how-aws-and-cisco-ai-defense-scale-mcp-and-a2a-deployments/))
- Help Net Security: "One in four MCP servers opens AI agent security to code execution risk" (May 5, 2026) ([link](https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/))

*Platforms: Web, Hacker News*

---

### 7. Developer Workflows and Adoption Patterns

The community has converged on pragmatic guidance: most developers need 2–3 MCP servers (GitHub, Filesystem, one domain-specific) plus a few custom Skills for repeated procedures, with Hooks added only for guaranteed execution requirements. The Tool Search feature reduces MCP overhead by ~85% through on-demand loading.

YouTube tutorials have become the primary discovery channel for non-expert users, ranging from 853K-view viral demos to 4K-view deep dives. Recent high-engagement titles include "7 Claude Code skills I use every single day" ([YouTube](https://www.youtube.com/watch?v=UpgjdQJShWg)) and "Full Claude Skills Tutorial for Beginners in 2026" ([YouTube](https://www.youtube.com/watch?v=YkpEX_jlb04)). @rileybrown.ai's Claude MCP tutorial went viral on TikTok ([TikTok](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559)), driving MCP into mainstream awareness.

Reddit's r/ClaudeCode had 4,200+ weekly contributors by early 2026 — more than triple r/Codex's 1,200 — indicating strong community gravity around Claude's extension ecosystem ([MorphLLM](https://www.morphllm.com/claude-code-reddit)).

A notable tooling gap: the Agent Skills spec requires kebab-case skill names, but Claude Code doesn't validate this and silently ignores incorrectly named skills — a footgun causing confusion for new skill authors.

*Platforms: YouTube, TikTok, Web, Reddit (indirect)*

---

## Cross-Source Patterns

### Pattern 1: Token Efficiency as the Core Differentiator
**Platforms:** Hacker News, Web (Simon Willison blog, MorphLLM, Anthropic engineering blog)
- Skills (30–50 tokens each) vs. MCP servers (50,000+ tokens) is the most-cited technical reason to prefer skills for context management
- *"GitHub's official MCP implementation famously consumes tens of thousands of context tokens alone."* — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))
- *"Skills are on-demand; CLAUDE.md is always-loaded context."* — MorphLLM ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins))

### Pattern 2: Standard-Setting as Competitive Moat
**Platforms:** Web (The New Stack, Medium/Context Layer, Paperclipped, Pento, VentureBeat), Hacker News
- Anthropic's MCP → AAIF/Linux Foundation donation mirrors the skills open-standard playbook
- 32 tools adopted SKILL.md within 3 months of release; OpenAI adoption within 48 hours
- *"Anthropic is doing with Agent Skills what it did with MCP"* — The Context Layer ([Medium](https://medium.com/the-context-layer/anthropic-is-doing-with-agent-skills-what-it-did-with-mcp-7068a15e72da))

### Pattern 3: Marketplace Fragmentation Without Quality Guarantees
**Platforms:** Web (Agensi guide, KDNuggets, multiple directories), Hacker News (Agent37)
- Every major marketplace surface reports different size numbers; most have zero security review
- Security audits consistently find >36% vulnerability rates across publicly listed skills/servers
- Creator monetization is solved individually (Agent37, Agensi) but not at the ecosystem level

### Pattern 4: Skills as Documentation That Actually Gets Written
**Platforms:** Hacker News (michael1999, multiple commenters), Web
- Multiple HN commenters independently noted that skill creation solves the perennial problem of developer documentation not getting written
- The "digital goblin" framing (developers care about their agent's effectiveness) creates intrinsic motivation absent from traditional docs
- *"Context documents for AI resemble effective developer documentation but are created far more readily"* — HN commenter michael1999 ([HN 45607117](https://news.ycombinator.com/item?id=45607117))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| meetpateltech | Claude Skills | 816 | 427 | "potentially more significant than MCP — a paradigm for dynamically assembling context" | [link](https://news.ycombinator.com/item?id=45607117) |
| weinzierl | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | tptacek: "MCP is merely one implementation among possibilities" | [link](https://news.ycombinator.com/item?id=45619537) |
| vishnukool | Show HN: Agent37 – Monetize your Claude skills with shareable links | 5 | 3 | "1,000+ MCP skills on GitHub with zero way for creators to charge for them" | [link](https://news.ycombinator.com/item?id=46422134) |
| — | Agent Skills – Open Trusted Catalog | — | — | Rate-limited | [link](https://news.ycombinator.com/item?id=46692865) |
| — | Claude Skills vs. MCP: Complementary Philosophies | — | — | Rate-limited | [link](https://news.ycombinator.com/item?id=45766686) |
| — | Show HN: Agnix – lint your AI agent configs | — | — | Rate-limited | [link](https://news.ycombinator.com/item?id=46983879) |
| — | Skillz: Use Claude Skills in Codex, Copilot via MCP | — | — | Rate-limited | [link](https://news.ycombinator.com/item?id=45649295) |
| — | Show HN: Almanac MCP, turn Claude Code into Deep Research agent | — | — | Not retrieved | [link](https://news.ycombinator.com/item?id=47855284) |
| — | FEC Claude Code Plugin and Agent Skill and MCP | — | — | Not retrieved | [link](https://news.ycombinator.com/item?id=46869575) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Praiseakinlami | "Hope you all know about Claude skills. I use it for my viral tweets and I get vitality every time." | — | — | [link](https://x.com/Praiseakinlami/status/2018359352965411097) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| — | Full Claude Skills Tutorial for Beginners in 2026! (Become a PRO) | — | — | — | [link](https://www.youtube.com/watch?v=YkpEX_jlb04) |
| — | FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step) | — | — | — | [link](https://www.youtube.com/watch?v=qYqIhX9hTQk) |
| — | 7 Claude Code skills I use every single day (Advanced Tutorial) | — | — | — | [link](https://www.youtube.com/watch?v=UpgjdQJShWg) |
| — | Full Claude Code Tutorial for Non-Technical Beginners in 2026 | — | — | — | [link](https://www.youtube.com/watch?v=bqJzIWAEn40) |

**TikTok:**
| Creator | Caption Snippet | Views | Likes | URL |
|---------|----------------|-------|-------|-----|
| @rileybrown.ai | "CLAUDE MCP TUTORIAL — Claude is an AI Agent! Insanely smart. You need to give it CONTEXT via MCP..." | Viral | — | [link](https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Primary technical spec: progressive disclosure, SKILL.md format, authors |
| claude.com/blog/skills | [link](https://claude.com/blog/skills) | Official product launch, platform availability |
| Anthropic MCP Donation | [link](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | MCP → Linux Foundation / AAIF |
| Simon Willison Blog | [link](https://simonwillison.net/2025/Oct/16/claude-skills/) | Skills vs. MCP token analysis; "Cambrian explosion" prediction |
| The New Stack | [link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Standard-setting framing |
| VentureBeat | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Enterprise Agent Skills launch |
| Medium / The Context Layer | [link](https://medium.com/the-context-layer/anthropic-is-doing-with-agent-skills-what-it-did-with-mcp-7068a15e72da) | MCP → Skills playbook analysis |
| AI Business | [link](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) | Launch coverage |
| Paperclipped (Interoperability) | [link](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) | 32-tool adoption by March 2026 |
| Subramanya.ai | [link](https://subramanya.ai/2025/12/18/agent-skills-the-missing-piece-of-the-enterprise-ai-puzzle/) | Enterprise use case analysis |
| PulseMCP | [link](https://www.pulsemcp.com/posts/openai-agent-skills-anthropic-donates-mcp-gpt-5-2-image-1-5) | OpenAI adopts Agent Skills |
| CIO Dive | [link](https://www.ciodive.com/news/big-tech-develop-open-standards-agentic-ai/807608/) | Big tech open standards context |
| Pento (Year of MCP) | [link](https://www.pento.ai/blog/a-year-of-mcp-2025-review) | 10,000+ active MCP servers milestone |
| AdwaitX | [link](https://www.adwaitx.com/anthropic-agent-skills-open-standard-ai-market/) | "$52B market shift" framing |
| agentskills.io | [link](https://agentskills.io/home) | Open standard reference documentation |
| GitHub agentskills spec | [link](https://github.com/agentskills/agentskills) | Specification and docs repo |
| GitHub anthropics/skills | [link](https://github.com/anthropics/skills) | Official Anthropic skills |
| GitHub alirezarezvani/claude-skills | [link](https://github.com/alirezarezvani/claude-skills) | 5,200+ stars; 313+ multi-platform skills |
| GitHub jeremylongshore/plugins+skills | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 2.2K stars; tonsofskills.com marketplace |
| GitHub ComposioHQ/awesome-claude-plugins | [link](https://github.com/ComposioHQ/awesome-claude-plugins) | 1.7K stars; curated extensions |
| GitHub ComposioHQ/awesome-claude-skills | [link](https://github.com/ComposioHQ/awesome-claude-skills) | 1,000+ cross-platform skills |
| GitHub quemsah/awesome-claude-plugins | [link](https://github.com/quemsah/awesome-claude-plugins) | Adoption metrics via n8n |
| GitHub rohunvora/x-research-skill | [link](https://github.com/rohunvora/x-research-skill) | X/Twitter research skill |
| GitHub topics: claude-code-skills | [link](https://github.com/topics/claude-code-skills) | Topic hub |
| GitHub topics: claude-skills | [link](https://github.com/topics/claude-skills) | Topic hub |
| DEV Community (gh skill) | [link](https://dev.to/om_shree_0709/gh-skill-githubs-new-cli-command-turns-agent-skills-into-installable-packages-2p82) | GitHub CLI `gh skill install` |
| Vercel KB | [link](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context) | Creating/installing/sharing skills |
| Skills.sh | [link](http://skills.sh) | Vercel-backed npm-style skills package manager |
| John's blog (skills.sh) | [link](https://johnoct.github.io/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/) | skills.sh overview |
| Inference.sh Blog | [link](https://inference.sh/blog/skills/agent-skills-overview) | Open standard overview |
| OpenAI Codex Skills Docs | [link](https://developers.openai.com/codex/skills) | Cross-platform adoption |
| Gemini CLI Skills Docs | [link](https://geminicli.com/docs/cli/skills/) | Cross-platform adoption |
| Microsoft Learn MCP | [link](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) | MCP in Microsoft ecosystem |
| KDNuggets (Top 5 Marketplaces) | [link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Marketplace comparison |
| Agensi Marketplace Guide | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 8-marketplace full comparison |
| SkillsMP | [link](https://skillsmp.com/) | 1.46M+ skills directory |
| LobeHub Skills | [link](https://lobehub.com/skills) | 169K+ skills directory |
| Claude Marketplaces | [link](https://claudemarketplaces.com/) | 6,700+ skills, 2,500+ marketplaces |
| Tons of Skills | [link](https://tonsofskills.com/) | 425 plugins, 2,810 skills marketplace |
| SkillHub | [link](https://www.skillhub.club/) | Marketplace directory |
| Agensi | [link](https://www.agensi.io/) | Security-scanned, paid marketplace |
| Agent37 | [link](https://agent37.com) | Monetization platform |
| MCP Market | [link](https://mcpmarket.com/) | MCP server directory |
| AI Agents List MCP | [link](https://aiagentslist.com/mcp-servers) | 593+ MCP servers |
| MorphLLM Extensions Guide | [link](https://www.morphllm.com/claude-code-extensions) | Extension type comparisons; 9,000+ plugins |
| MorphLLM Skills vs MCP | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills/MCP/plugins guide |
| MorphLLM Reddit summary | [link](https://www.morphllm.com/claude-code-reddit) | Community stats |
| Claude Code plugin docs | [link](https://code.claude.com/docs/en/plugins) | Official plugin documentation |
| Claude Code MCP docs | [link](https://code.claude.com/docs/en/mcp) | Official MCP documentation |
| Claude API Skills docs | [link](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | API documentation |
| Nimbalyst Plugin Guide | [link](https://nimbalyst.com/blog/claude-code-plugins-guide/} | 2026 plugin guide |
| Skills Playground | [link](https://skillsplayground.com/guides/claude-code-plugins/) | Plugin guide |
| Clarista MCP Guide | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | MCP + plugin guide |
| TurboDocx Skills Guide | [link](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best picks 2026 |
| Firecrawl MCP Servers | [link](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | MCP server recommendations |
| Firecrawl Claude Skills | [link](https://www.firecrawl.dev/blog/best-claude-code-skills) | Skills recommendations |
| MCP Bundles | [link](https://www.mcpbundles.com/blog/best-mcp-servers) | MCP server list |
| Analytics Vidhya MCP | [link](https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/} | Top 10 MCP servers |
| Toloka MCP | [link](https://toloka.ai/blog/best-mcp-servers-for-agents/} | Best MCP servers |
| K2View MCP | [link](https://www.k2view.com/blog/awesome-mcp-servers) | Awesome MCP list |
| ByteBridge MCP Gateways | [link](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | Top MCP gateways |
| Integrate.io MCP Security | [link](https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/} | MCP security tools |
| Help Net Security | [link](https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/) | May 5, 2026 security report |
| Aembit MCP Security | [link](https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/} | Vulnerability guide |
| Adversa AI Security | [link](https://adversa.ai/blog/top-mcp-security-resources-april-2026/} | April 2026 security resources |
| AWS ML Blog | [link](https://aws.amazon.com/blogs/machine-learning/securing-ai-agents-how-aws-and-cisco-ai-defense-scale-mcp-and-a2a-deployments/) | Enterprise MCP security |
| Camille Roux Top 13 | [link](https://www.camilleroux.com/top-skills-plugins-claude-code-2026-v3/} | Most social engagement |
| Claude World Official Skills | [link](https://claude-world.com/articles/anthropic-official-skills-complete-guide/} | 17 official skills guide |
| Nimbleway Top 10 Skills | [link](https://www.nimbleway.com/blog/anthropic-claude-agent-skills} | Top agent skills |
| Script by AI | [link](https://www.scriptbyai.com/claude-code-resource-list/} | Resource list |
| Composio TikTok MCP | [link](https://composio.dev/toolkits/tiktok/framework/claude-code) | TikTok MCP integration |
| Composio YouTube MCP | [link](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration |
| TikTok trends MCP | [link](https://github.com/trendsmcp/tiktok-trends-mcp) | Live hashtag trend MCP server |
| Polymarket Toolkit | [link](https://www.blog.brightcoding.dev/2026/05/22/polymarket-toolkit-the-secret-weapon-top-ai-agents-use-for-prediction-market-alpha) | Polymarket MCP skill |
| Polymarket MCP (mcpservers.org) | [link](https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp) | Polymarket MCP server |
| Graph Polymarket | [link](https://conare.ai/marketplace/mcp/graph-polymarket) | 20-tool Polymarket MCP |
| Sparkco Prediction Market | [link](https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi) | Claude Code + MCP + Kalshi |
| Medium ranking YouTube | [link](https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840) | 25-video ranking |
| Agensi Plugin Guide | [link](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide) | Marketplace guide |
| Agensi Install Skills | [link](https://www.agensi.io/learn/how-to-install-skills-claude-code) | Install guide |
| Agensi Plugins vs Skills | [link](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Comparison guide |
| Nocentdocent Blog | [link](https://nocentdocent.wordpress.com/2026/01/05/anthropics-agent-skills/} | January 2026 analysis |
| SmartScope SkillsMP Review | [link](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/} | 66,500+ skills review |

---

## Stats Block

```
├─ 🟠 Reddit: 0 direct threads │ 4,200+ weekly r/ClaudeCode contributors (indirect)
├─ 🔵 X: 1+ posts │ engagement unavailable
├─ 🔴 YouTube: 4 videos │ 853K+ top reported views
├─ 🟢 HN: 9 stories │ 1,559+ points │ 800+ comments (2 fully retrieved; 5 rate-limited)
├─ 🟣 TikTok: 1+ videos │ viral (exact counts unavailable)
├─ 🩷 Instagram: 0 reels │ 0 views
├─ 🦋 Bluesky: 0 posts directly retrieved │ cross-posts confirmed (Camille Roux)
├─ 📊 Polymarket: 0 markets on topic │ MCP→Polymarket tools exist
├─ 🌐 Web: 55+ pages
└─ 🗣️ Top voices: @simonw (Simon Willison), @meetpateltech, @weinzierl │ r/ClaudeCode (4,200+/wk)
```

---

## Data Gaps

- **Reddit:** Reddit threads are not indexable via web search with the tools available. The r/ClaudeCode subreddit has 4,200+ weekly contributors as of early 2026, making it a significant data gap. Estimated 20–30 highly upvoted threads on skills/MCP missed.
- **Hacker News rate-limiting:** 5 of 9 HN threads returned HTTP 429. Points and comment details for threads 46692865, 45766686, 46983879, 45649295, 47855284, and 46869575 are missing. Estimated 1,000+ additional points and 500+ additional comments not captured.
- **X/Twitter:** Only 1 confirmed post retrieved. The @simonw analysis was widely shared and referenced but tweet metrics unavailable. X search is blocked for direct crawling.
- **TikTok:** Only 1 video retrieved via URL; exact view and like counts unavailable. Creator-name searches not possible via web search.
- **YouTube:** 4 videos identified but view counts, like counts, and transcripts unavailable. The Medium ranking guide (25-video comprehensive ranking) references an 853K-view top video not directly identified.
- **Bluesky:** Cross-posting from Camille Roux's article confirmed but no direct Bluesky posts retrieved.
- **Polymarket:** No prediction markets specifically about agent skills adoption, marketplace outcomes, or Claude Code ecosystem events found.
- **Approximate coverage:** Web (~85%), HN (~45% by thread count, ~30% by engagement metrics), GitHub (~90%), YouTube (~20%), Reddit (~5%), X (~5%), TikTok (~10%).

---

## Key Quotes

> "While MCP requires an elaborate protocol specification covering hosts, clients, servers, and multiple transports, skills embrace simplicity: Markdown with a tiny bit of YAML metadata and some optional scripts." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "Skills are folders that include instructions, scripts, and resources that Claude can load when needed. Skills stack together. Only loads what's needed, when it's needed." — Anthropic ([claude.com/blog/skills](https://claude.com/blog/skills))

> "MCP is merely one implementation among possibilities, and perhaps not the optimal one." — tptacek on HN ([link](https://news.ycombinator.com/item?id=45619537))

> "There are 1,000+ MCP skills on GitHub with zero way for creators to charge for them." — vishnukool (Agent37) on HN ([link](https://news.ycombinator.com/item?id=46422134))

> "Context documents for AI resemble effective developer documentation but are created far more readily — developers feel motivated improving their 'digital goblin' rather than abstract colleagues." — michael1999 on HN ([link](https://news.ycombinator.com/item?id=45607117))

> "Anthropic is doing with Agent Skills what it did with MCP." — Jannis, The Context Layer ([Medium](https://medium.com/the-context-layer/anthropic-is-doing-with-agent-skills-what-it-did-with-mcp-7068a15e72da))

> "MCP provides the 'plumbing' for tool access, while agent skills provide the 'brain' or procedural memory for how to use those tools effectively." — Simon Willison ([simonwillison.net](https://simonwillison.net/2025/Oct/16/claude-skills/))

> "The poisoned tool doesn't even need to be called — just being loaded into context is enough for the model to follow its hidden instructions." — AI Agent Security 2026 analysis ([link](https://blog.cyberdesserts.com/ai-agent-security-risks/))

> "Expect acquisitions, shutdowns, and cross-listings to reduce the active set to three or four dominant platforms within a year." — Agensi marketplace guide ([link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026))

> "Skills are on-demand; CLAUDE.md is always-loaded context. Choose Skills for specific workflows and CLAUDE.md for foundational knowledge Claude should consistently apply." — MorphLLM ([morphllm.com](https://www.morphllm.com/claude-code-extensions))
