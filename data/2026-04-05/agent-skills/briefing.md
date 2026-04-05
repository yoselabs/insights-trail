# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-04-05
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 29 posts | 7 likes, 1 repost | Compact output shows 15; top post 4 likes @domini_code |
| Hacker News | 22 stories | ~160 pts, ~60 comments | Compact output shows 15; top story 36 pts hn/4ppsec |
| Web | 30 pages | — | via WebSearch; 3 queries |

---

## Synthesized Findings

### 1. The Three-Layer Extension Model: Skills, Plugins, MCP Servers

The community has landed on a clear conceptual framework (per DEV Community, Nevo Systems, and multiple HN threads) that distinguishes three extension layers:

- **Skills** — filesystem-based SKILL.md instruction files that teach Claude domain-specific behavior. They activate *automatically* based on conversation context — not via `/slash` commands. Claude loads skill metadata at startup and decides when to apply them silently.
- **Plugins** — distributable packages that bundle skills, hooks, subagents, commands, and configuration into a single installable unit.
- **MCP Servers** — standardized connections to external tools and data sources via the Model Context Protocol. These run as services that Claude calls at runtime.

HN thread "Skills are quietly becoming the unit of agent knowledge" (hn/latand6, 9 pts, 13 comments) explicitly interrogated this boundary: commenters asked "Will skills replace MCP servers eventually?" and "What do you think about checking the skills directly into the repo where they are useful?" — signaling live community debate about where skills end and MCPs begin.

Per [nevo.systems](https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp) and [dev.to/phil-whittaker](https://dev.to/phil-whittaker/mcp-vs-agent-skills-why-theyre-different-not-competing-2bc1): the answer is that they are complementary, not competing — skills modify agent *behavior*, MCP servers extend agent *reach*.

---

### 2. Skill Ecosystem Scale: Marketplaces and Package Managers

The skill/plugin ecosystem has reached meaningful scale. Sources across web search confirm:

- **2,300+ skills** and **770+ MCP servers** available across community registries
- **90,000+ publicly listed skills** in AgentSkillOS ([github.com/ynulihao/AgentSkillOS](https://github.com/ynulihao/AgentSkillOS)) via retrieval and orchestration
- **1,600+ curated skills** in structured repos discoverable via MCP-based search

Active marketplaces and registries:

| Platform | URL | Scope |
|----------|-----|-------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | 150+ Claude Code skills, ratings, March 2026 |
| skillsmp.com | https://skillsmp.com/ | Cross-platform: Claude, Codex & ChatGPT |
| buildwithclaude.com | https://buildwithclaude.com/ | Claude plugin marketplace |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 skills + CCPI CLI |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 220+ skills for 8+ coding agents |
| awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated: commands, agents, hooks, MCP |
| awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | Skills, hooks, slash-commands, orchestrators |
| awesome-claude-plugins (metrics) | https://github.com/quemsah/awesome-claude-plugins | Automated adoption metrics via n8n |

The **CCPI package manager** (from jeremylongshore) introduced npm-style distribution for Claude skills:
```
pnpm add -g @intentsolutionsio/ccpi
ccpi install devops-automation-pack
ccpi update
```

The [liteLLM tutorial](https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace) covers plugin marketplace setup for teams. The [DEV Community 2026 guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) and [Calmops complete guide](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) provide onboarding resources.

On X, @openapexmarket reported shipping 35 AI agent skills to Apex Market — crypto connectors to SEO tools, 6 free to start — and is watching early adoption patterns with zero revenue yet. @BetaList listed ClawSkills (versioned skill publishing with vector search). @sujantiwari08 published a structured 4-week learning path where Agent Skills appear in Week 3 alongside MCP.

---

### 3. Cross-Agent Interoperability: SKILL.md as Open Standard

In December 2025, Anthropic released the Agent Skills specification as an open standard; OpenAI adopted the same SKILL.md format for Codex CLI and ChatGPT (per [jeremylongshore repo](https://github.com/jeremylongshore/claude-code-plugins-plus-skills), [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills), and [SkillsMP](https://skillsmp.com/)).

This means:
- A skill written for Claude Code (`~/.claude/skills/`) works in OpenAI Codex CLI (`~/.codex/skills/`) without modification
- Vercel's **Skills.sh** ([vercel-labs/skills](https://github.com/vercel-labs/skills), `npx skills`) works across Claude Code, Cursor, GitHub Copilot, Aider, OpenCode, and 30+ other agents ([InfoQ coverage](https://www.infoq.com/news/2026/02/vercel-agent-skills/), [johnoct.com blog](https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/))
- Microsoft published a [skills repo with MCP servers, custom agents, and Agents.md](https://github.com/microsoft/skills) for grounding coding agents across SDKs
- VS Code Copilot natively supports agent skills: [code.visualstudio.com/docs/copilot/customization/agent-skills](https://code.visualstudio.com/docs/copilot/customization/agent-skills)
- Spring AI adopted the pattern for the Java ecosystem ([spring.io blog](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/))

The [DEV Community post on the rise of reusable AI agent skills](https://dev.to/dmgjdagooc/the-rise-of-reusable-ai-agent-skills-how-skillssh-and-anthropic-are-changing-the-way-we-build-242d) frames this as the "skills.sh + Anthropic" moment for the ecosystem.

@domini_code (4 likes, highest-engagement X post) highlighted Addy Osmani's Agent Skills for Claude Code applying Lighthouse and Core Web Vitals to developer workflows — pre-configured performance targets (LCP ≤ 2.5s, INP ≤ 200ms, bundle < 300KB) shipped as skills.

---

### 4. MCP Infrastructure: 97M Downloads, Linux Foundation Governance

The Model Context Protocol is the tool-connectivity substrate powering all of this. Key facts from web research:

- **97 million monthly SDK downloads** (Python + TypeScript combined)
- **10,000+ active MCP servers** deployed
- **75+ connectors** in Claude alone
- First-class client support: ChatGPT, Claude, Cursor, Gemini, Microsoft Copilot, VS Code

On **December 9, 2025**, Anthropic donated MCP to the **Linux Foundation's Agentic AI Foundation (AAIF)**:
- Founding contributions: Anthropic's MCP, Block's goose, OpenAI's AGENTS.md
- AAIF Platinum members: AWS, Anthropic, Block, Bloomberg, Cloudflare, Google, Microsoft, OpenAI
- [Official Anthropic announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | [Linux Foundation press release](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation) | [PR Newswire](https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agentsmd-302636897.html) | [OpenAI statement](https://openai.com/index/agentic-ai-foundation/) | [GitHub Blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation)

The **MCP Dev Summit North America 2026** (April 2-3, NYC, 95+ sessions) just concluded, convening MCP co-founders, maintainers, and production users — [LF events schedule](https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/) | [LF press](https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule) | [Yahoo Finance](https://finance.yahoo.com/news/agentic-ai-foundation-unveils-140000965).

Solo.io analyzed the implications in [Why the AAIF Changes Everything for MCP](https://www.solo.io/blog/aaif-announcement-agentgateway).

MCP server discovery: major directories include [mcpservers.org/agent-skills](https://mcpservers.org/agent-skills), [pulsemcp.com](https://www.pulsemcp.com/servers/mrsimpson-agent-skills), [glama.ai](https://glama.ai/mcp/servers/pinkpixel-dev/agentskills-mcp), and [gofastmcp.com](https://gofastmcp.com/servers/providers/skills). Enterprise guidance: [Microsoft Learn on local MCP tools](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools).

Progressive tool discovery (per [dev.to/phil-whittaker](https://dev.to/phil-whittaker/mcp-vs-agent-skills-why-theyre-different-not-competing-2bc1)): Anthropic applied the same context-efficiency trick from skills to MCP — tools load name+description (~20-50 tokens) first; full schema only fetches when the agent decides to invoke.

---

### 5. Security: Supply Chain Attacks and Enterprise Governance

Security emerged as the sharpest HN discussion thread this cycle. **HN1** — "Agent Skills – Open Security Database" (hn/4ppsec, 36 pts, 9 comments, March 16) — covered a new public database cataloguing security risks in agent skills. Top HN comment: "if your engineers are installing and running random 'skills' found online it's the same as if you had engineers running random npm packages."

On X, @PixelFamiliar raised an urgent warning: "Supply chain attacks in agent skills are already happening. ClawForce certifies skills for malware, credential theft, data exfiltration." — referencing a skill certification service.

JFrog framed this definitively: ["Agent Skills are the New Packages of AI: It's Time to Manage Them Securely"](https://jfrog.com/blog/agent-skills-new-ai-packages/) — treating skills as a software supply chain problem requiring the same artifact management used for npm and Docker.

Qualys warned in March 2026: ["MCP Servers: The New Shadow IT for AI in 2026"](https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026) — ungoverned MCP connections in enterprise environments create invisible attack surfaces.

Microsoft responded with the **Agent Governance Toolkit** (April 2, 2026): [opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit](https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit) — open-source runtime security for AI agents.

JFrog's registry (compatible with Agent Skills, ClawHub, and OpenShell) enables centralized governance of skills across enterprise environments.

---

### 6. Production Deployment: Pinterest, Vertical Skill Packs, On-Device Skills

**Pinterest at scale** (InfoQ, April 2026): Pinterest deployed a full internal MCP ecosystem — production MCP servers, a central skill registry, and agent integrations across developer tooling — replacing ad hoc integrations with a standardized substrate. One of the first documented production-scale internal agent registries. [Full coverage: infoq.com/news/2026/04/pinterest-mcp-ecosystem](https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/).

**Vertical skill packs**: A March 2026 [Medium post](https://medium.com/product-powerhouse/33-claude-skills-for-pms-are-now-in-the-claude-code-marketplace-heres-how-to-install-them-7968ab6bb1e1) documented 33 PM-specific skills in the Claude Code marketplace. The alirezarezvani skills repo spans engineering, marketing, product, compliance, and C-level advisory domains.

**On-device skills**: @AiwithZoaina highlighted AI Edge Gallery's Agent Skills with the E4B model — complex on-device tasks (booking, multi-source search, combining info) without server round-trips. @Kushagrat15 noted Google shipped on-device agent skills for Gemma 4 within 48 hours of the model's release. The E2B variant runs fully offline at 2.5 GB.

**Blockchain skills**: Solana Foundation launched Solana Agent Skills — prebuilt skill components for AI tools to interact with the Solana ecosystem. @neon_artival's skeptical reply: "vendor lock-in in agent skills is the new npm left-pad."

HN featured domain-specific skill projects this cycle: [Golang Agent Skills collection](https://news.ycombinator.com/item?id=47487741), [PySpark one-shot CLI skill](https://news.ycombinator.com/item?id=47534936), [affiliate marketing skills](https://news.ycombinator.com/item?id=47632530), [BrowserHawk QA skill for Claude Code](https://news.ycombinator.com/item?id=47574095), and [Orca executable skills for agent workflows](https://news.ycombinator.com/item?id=47584819).

---

### 7. Skill Chaining, Custom Workflows, and Developer Education

For multi-step workflows, skills are **chained** via an orchestrator pattern (per [MindStudio](https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows)):

> Orchestrator reads shared state file → determines next skill → invokes → updates state → loops until workflow complete

Each skill writes structured output consumed by the next, making skills independently testable and composable. Resources: [first-principles deep dive](https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/), [Claude Code Handbook](https://nikiforovall.blog/claude-code-rules/fundamentals/agent-skills/), [fazm.ai workflow guide](https://fazm.ai/t/custom-claude-code-skills-workflow), [CodeSignal course on visualization skills](https://codesignal.com/learn/courses/customizing-claude-code-for-reusable-visualization-workflows/lessons/modular-visualization-skills), [DevOps.com overview](https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/), [official sub-agents docs](https://code.claude.com/docs/en/sub-agents).

HN project shows this week: [Ink – deploy full-stack apps from AI agents via MCP or Skills](https://news.ycombinator.com/item?id=47337028) (32 pts), [n8n workflow → OpenClaw-compatible skills](https://news.ycombinator.com/item?id=47561083), [package manager for agent skills](https://news.ycombinator.com/item?id=47489570), [Skills Manager across Claude/Cursor/Copilot](https://news.ycombinator.com/item?id=47423910), [production-ready Agent Skills + orchestration protocol](https://news.ycombinator.com/item?id=47363984), ["What Claude Code Leak Teaches Us About Agent Skills"](https://news.ycombinator.com/item?id=47605341).

Official documentation: [code.claude.com/docs/en/discover-plugins](https://code.claude.com/docs/en/discover-plugins) | [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview).

@sujantiwari08 published a free 4-week curriculum: Week 1 Claude 101, Week 2 API + Claude Code, Week 3 Intro MCP + Agent Skills, Week 4 MCP Advanced + Vertex AI. @CMonk40079 debated with @ThePrimeagen about OpenClaw's skills auto-routing and sub-agent delegation as differentiators.

---

## Cross-Source Patterns

**Pattern 1: Open SKILL.md standard is converging across all major agents**
- Platforms: X (@domini_code on Addy Osmani skills, @sujantiwari08 curriculum), HN (Skills Manager across Claude/Cursor/Copilot), Web (skillsmp.com, vercel skills.sh, OpenAI Codex skills docs, Microsoft skills repo)
- Claude Code, Codex CLI, ChatGPT, Cursor, GitHub Copilot, Gemini CLI, and VS Code Copilot all support SKILL.md. Skills.sh (Vercel) works with 30+ agents. A skill written once runs everywhere.

**Pattern 2: Security/governance is the ecosystem's next forcing function**
- Platforms: HN (hn/4ppsec "Agent Skills – Open Security Database," 36 pts, top story this cycle), X (@PixelFamiliar on supply chain attacks, ClawForce certification)
- "Installing random skills is the same as installing random npm packages" — the npm analogy is how HN framed the risk. JFrog and Microsoft are both treating this as a supply chain problem requiring artifact registries and runtime governance.

**Pattern 3: Scale is already here — 90K+ skills, but discovery is unsolved**
- Platforms: HN ("Skills are quietly becoming the unit of agent knowledge," 13 comments), Web (AgentSkillOS 90K skills, claudemarketplaces.com, skillsmp.com, CCPI CLI)
- Multiple registries, package managers, and marketplaces exist but are fragmented. JetBrains ACP Registry (IDE-integrated), CCPI (CLI), skillsmp.com (web), claudemarketplaces.com (community curated) all solve discovery differently. No single canonical registry.

**Pattern 4: Vendor lock-in in skills mirrors npm left-pad anxieties**
- Platforms: X (@neon_artival reply to Solana Agent Skills)
- "Install in one line" convenience carries dependency risk. When skills phone home to external infrastructure (Solana, cloud APIs), they create the same single-point-of-failure risks as small npm packages. Offline/local skill execution is a real concern.

**Pattern 5: On-device agent skills signal edge AI maturation**
- Platforms: X (@AiwithZoaina on AI Edge Gallery E4B skills, @Kushagrat15 on Gemma 4 → skills in 48 hours)
- Agent skills are moving from cloud-dependent to on-device, with complex task execution (booking, multi-source search) happening without server round-trips. Gemma 4's rapid skills adoption signals this is a hardware maturity story, not just software.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @domini_code | Addy Osmani published Agent Skills for Claude Code applying Lighthouse + Core Web Vitals | 4 | 1 | https://x.com/domini_code/status/2040678792520188280 |
| @PixelFamiliar | Supply chain attacks in agent skills are already happening; ClawForce certifies skills for malware/credential theft | 0 | 0 | https://x.com/PixelFamiliar/status/2040702393889776001 |
| @BetaList | ClawSkills: publish and discover versioned agent skills with vector search | 0 | 0 | https://x.com/BetaList/status/2040703746037158254 |
| @openapexmarket | Shipped 35 AI agent skills to Apex Market; crypto connectors to SEO tools, 6 free | 0 | 0 | https://x.com/openapexmarket/status/2040701874702340320 |
| @LDNCryptoClub | Solana Foundation launched Solana Agent Skills for embedding prebuilt skill components into AI tools | 0 | 0 | https://x.com/LDNCryptoClub/status/2040701221552480553 |
| @neon_artival | Vendor lock-in in agent skills is the new npm left-pad | 0 | 0 | https://x.com/neon_artival/status/2040686394377461790 |
| @AiwithZoaina | AI Edge Gallery Agent Skills with E4B model: complex tasks on-device without hitting a server | 1 | 0 | https://x.com/AiwithZoaina/status/2040688282628157514 |
| @Kushagrat15 | Google shipped on-device agent skills for Gemma 4 within 48 hours of release; E2B runs offline at 2.5 GB | 0 | 0 | https://x.com/Kushagrat15/status/2040678178776375554 |
| @Kushagrat15 | Speed of Gemma 4 adoption into agent skills is the real story | 0 | 0 | https://x.com/Kushagrat15/status/2040679174231466391 |
| @sujantiwari08 | Free 4-week AI curriculum: Week 3 = Intro MCP + Agent Skills | 1 | 0 | https://x.com/sujantiwari08/status/2040696804992544956 |
| @sujantiwari08 | Course 9 — Intro to Agent Skills: build, configure, share reusable Skills in Claude Code | 1 | 0 | https://x.com/sujantiwari08/status/2040696752488280176 |
| @chenzeling4 | Lark CLI: 200+ commands, 20 AI Agent Skills for Messenger/Docs/Sheets/Calendar/Meetings | 0 | 0 | https://x.com/chenzeling4/status/2040686067037196684 |
| @CMonk40079 | OpenClaw: skills auto-routing, sub-agent delegation, multi-channel, persistent memory | 0 | 0 | https://x.com/CMonk40079/status/2040702169439928785 |
| @savaldeveloper | Developer without AI skills is losing the battle; vibe coding ≠ agent building | 0 | 0 | https://x.com/savaldeveloper/status/2040705285518471498 |
| @arvin17x | Project best-practice skills template for agent self-discovery of patterns (Chinese) | 0 | 0 | https://x.com/arvin17x/status/2040694631617396933 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| hn/4ppsec | Agent Skills – Open Security Database | 36 | 9 | "Installing random skills is the same as installing random npm packages" | https://news.ycombinator.com/item?id=47402118 |
| hn/chenxi9649 | Agent Skills: One-Shot PySpark from the CLI | 22 | 4 | "agent 'build me a churn model from this data' = YES PLEASE" | https://news.ycombinator.com/item?id=47534936 |
| hn/samber | Show HN: Ink – Deploy full-stack apps from AI agents via MCP or Skills | 32 | 6 | "Is Okta supported for auth, and how does bring your own cloud work?" | https://news.ycombinator.com/item?id=47337028 |
| hn/latand6 | Skills are quietly becoming the unit of agent knowledge | 9 | 13 | "Will skills replace MCP servers eventually?" | https://news.ycombinator.com/item?id=47475832 |
| hn/marioskales | Show HN: Skales – I built a desktop AI agent a 6-year-old can use | 12 | 6 | — | https://news.ycombinator.com/item?id=47613527 |
| hn/dev_chad | What Claude Code Leak Teaches Us About Agent Skills | 5 | 0 | — | https://news.ycombinator.com/item?id=47605341 |
| hn/evergreenxx | Skills Manager – manage AI agent skills across Claude, Cursor, Copilot | 3 | 9 | — | https://news.ycombinator.com/item?id=47423910 |
| hn/sonpiaz | Show HN: AI agent skills for affiliate marketing (Markdown, works with any LLM) | 3 | 0 | — | https://news.ycombinator.com/item?id=47632530 |
| hn/samber | A collection of 35 Golang Agent Skills | 3 | 2 | — | https://news.ycombinator.com/item?id=47487741 |
| hn/eterer | I built a package manager for agent skills | 3 | 1 | — | https://news.ycombinator.com/item?id=47489570 |
| hn/just-claw-it | Show HN: Built tool to turn n8n workflows into OpenClaw-compatible agent skills | 3 | 0 | — | https://news.ycombinator.com/item?id=47561083 |
| hn/gfernandf | Orca – Executable skills and capabilities for AI agent workflows | 3 | 1 | — | https://news.ycombinator.com/item?id=47584819 |
| hn/jungard | Production-ready Agent Skills, 17 agents, and an orchestration protocol | 3 | 1 | — | https://news.ycombinator.com/item?id=47363984 |
| hn/JakubKontra | BrowserHawk – Open-source autonomous QA agent skill for Claude Code | 3 | 0 | — | https://news.ycombinator.com/item?id=47574095 |
| hn/tadwork | Show HN: A small app that ships with AI agent skills to extend and audit it | 3 | 0 | — | https://news.ycombinator.com/item?id=47442521 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs — Plugins | https://code.claude.com/docs/en/discover-plugins | Official plugin discovery and installation guide |
| Claude API Docs — Agent Skills | https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview | Canonical agent skills spec |
| Claude Code Docs — Sub-agents | https://code.claude.com/docs/en/sub-agents | Custom subagent creation reference |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 150+ community skills with ratings |
| skillsmp.com | https://skillsmp.com/ | Cross-platform skills marketplace (Claude, Codex, ChatGPT) |
| buildwithclaude.com | https://buildwithclaude.com/ | Claude plugin marketplace |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 340 plugins + 1,367 skills + CCPI CLI |
| alirezarezvani/claude-skills | https://github.com/alirezarezvani/claude-skills | 220+ multi-agent skills (8+ coding agents) |
| ComposioHQ/awesome-claude-plugins | https://github.com/ComposioHQ/awesome-claude-plugins | Curated plugin list |
| quemsah/awesome-claude-plugins | https://github.com/quemsah/awesome-claude-plugins | Automated adoption metrics |
| hesreallyhim/awesome-claude-code | https://github.com/hesreallyhim/awesome-claude-code | Skills, hooks, slash-commands, orchestrators |
| liteLLM | https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace | Plugin marketplace tutorial for teams |
| DEV Community — skills guide | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Best skills & plugins 2026 guide |
| DEV Community — MCP vs Skills | https://dev.to/phil-whittaker/mcp-vs-agent-skills-why-theyre-different-not-competing-2bc1 | MCP vs Skills conceptual clarity |
| DEV Community — Skills.sh rise | https://dev.to/dmgjdagooc/the-rise-of-reusable-ai-agent-skills-how-skillssh-and-anthropic-are-changing-the-way-we-build-242d | Skills.sh + Anthropic ecosystem analysis |
| Nevo Systems | https://nevo.systems/blogs/nevo-journal/ai-agent-skill-vs-plugin-vs-mcp | Skills vs Plugins vs MCPs: three-layer taxonomy |
| InfoQ — Vercel Skills.sh | https://www.infoq.com/news/2026/02/vercel-agent-skills/ | Vercel launches Skills.sh open ecosystem |
| vercel-labs/skills | https://github.com/vercel-labs/skills | npx skills CLI repo |
| johnoct.com | https://johnoct.com/blog/2026/02/12/skills-sh-open-agent-skills-ecosystem/ | Skills.sh: the missing package manager |
| JFrog | https://jfrog.com/blog/agent-skills-new-ai-packages/ | Agent skills as software supply chain |
| OpenAI Codex Skills | https://developers.openai.com/codex/skills | Official Codex skills documentation |
| AgentSkillOS | https://github.com/ynulihao/AgentSkillOS | 90,000+ skills via retrieval + orchestration |
| Chris Ayers blog | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete guide: skills, plugins, marketplace |
| Calmops | https://calmops.com/ai/ai-agent-skills-complete-guide-2026/ | AI Agent Skills Complete Guide 2026 |
| Spring AI | https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/ | Skills in Java/Spring ecosystem |
| PulseMCP — Agent Skills MCP | https://www.pulsemcp.com/servers/mrsimpson-agent-skills | Agent Skills MCP Server listing |
| PulseMCP — Skills MCP | https://www.pulsemcp.com/servers/skills-mcp-skills | Skills MCP Server listing |
| Glama — agentskills-mcp | https://glama.ai/mcp/servers/pinkpixel-dev/agentskills-mcp | Agent Skills MCP on Glama |
| FastMCP | https://gofastmcp.com/servers/providers/skills | Skills provider for FastMCP |
| mcpservers.org | https://mcpservers.org/agent-skills | Agent Skills Library |
| microsoft/skills | https://github.com/microsoft/skills | Microsoft skills, MCP servers, Agents.md |
| Qualys | https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026 | MCP servers as new shadow IT |
| Duende Software | https://duendesoftware.com/blog/20260402-give-your-ai-coding-assistant-duende-expertise-with-agent-skills-and-mcp-server | Identity framework as agent skill + MCP |
| VS Code Docs | https://code.visualstudio.com/docs/copilot/customization/agent-skills | Agent skills in VS Code Copilot |
| Anthropic News | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | MCP donation to Linux Foundation / AAIF |
| MCP Blog | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | MCP joins AAIF |
| Linux Foundation | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | AAIF formation press release |
| PR Newswire | https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agentsmd-302636897.html | Full AAIF formation release |
| OpenAI — AAIF | https://openai.com/index/agentic-ai-foundation/ | OpenAI co-founds AAIF |
| GitHub Blog — MCP | https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation | MCP → Linux Foundation |
| LF Events — MCP Summit | https://events.linuxfoundation.org/2026/02/24/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule/ | MCP Dev Summit NA 2026 schedule |
| LF Press — MCP Summit | https://www.linuxfoundation.org/press/agentic-ai-foundation-unveils-mcp-dev-summit-north-america-2026-schedule | Summit press release |
| Yahoo Finance | https://finance.yahoo.com/news/agentic-ai-foundation-unveils-140000965 | Summit coverage |
| Solo.io | https://www.solo.io/blog/aaif-announcement-agentgateway | AAIF implications for MCP |
| InfoQ — Pinterest MCP | https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/ | Pinterest production MCP ecosystem |
| Microsoft Agent Governance | https://opensource.microsoft.com/blog/2026/04/02/introducing-the-agent-governance-toolkit | Agent Governance Toolkit launch |
| Microsoft Learn — MCP | https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools | Local MCP tools in agent framework |
| MindStudio | https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows | Skill chaining into end-to-end workflows |
| Lee Hanchung | https://leehanchung.github.io/blogs/2025/10/26/claude-skills-deep-dive/ | First-principles deep dive on Claude skills |
| Claude Code Handbook | https://nikiforovall.blog/claude-code-rules/fundamentals/agent-skills/ | Custom agent skills guide |
| fazm.ai | https://fazm.ai/t/custom-claude-code-skills-workflow | One-shot to reliable custom skills |
| CodeSignal | https://codesignal.com/learn/courses/customizing-claude-code-for-reusable-visualization-workflows/lessons/modular-visualization-skills | Visualization skills course |
| DevOps.com | https://devops.com/claude-introduces-agent-skills-for-custom-ai-workflows/ | Agent skills for custom workflows |
| Medium — PM skills | https://medium.com/product-powerhouse/33-claude-skills-for-pms-are-now-in-the-claude-code-marketplace-heres-how-to-install-them-7968ab6bb1e1 | 33 PM skills in Claude Code marketplace |

---

## Stats Block

```
├─ 🔵 X: 29 posts │ 7 likes │ 1 repost
├─ 🟢 HN: 22 stories │ ~160 points │ ~60 comments
├─ 🌐 Web: 30 pages — claudemarketplaces.com, skillsmp.com, JFrog, InfoQ, Qualys, Linux Foundation, MindStudio, Spring.io, DEV Community, Calmops
└─ 🗣️ Top voices: @domini_code (4 likes), @PixelFamiliar, @Kushagrat15 │ hn/4ppsec (36 pts), hn/samber (32 pts)
```

---

## Data Gaps

- **Reddit:** API returned HTTP 402 Payment Required — zero Reddit data this cycle. Developer subreddits (r/ClaudeAI, r/LocalLLaMA, r/MachineLearning, r/programming) likely have active discussions about MCP and agent skills not captured here.
- **YouTube:** Script returned 0 videos in the date range. Developer tutorial channels are producing skills and MCP content not captured this cycle.
- **TikTok / Instagram:** No relevant content expected for this developer-focused topic.
- **X/Twitter:** 29 posts captured but engagement is low (7 total likes). The query "agent-skills" may have limited direct matches; searches for "Claude Code skills", "MCP marketplace", "SKILL.md" would surface more targeted developer discourse.
- **Polymarket:** No prediction markets found for this topic — expected for a tooling category.
- **Approximate coverage:** Documentation/announcement coverage ~90% comprehensive. Community sentiment/discussion (Reddit, HN comment threads, YouTube developer commentary) ~40% — HN story titles captured but comment depth is limited. True practitioner friction and debate not fully represented.

---

## Key Quotes

> "Installing random agent skills is the same as installing and running random npm packages — the risk calculus is identical." — hn/4ppsec on HN ([link](https://news.ycombinator.com/item?id=47402118))

> "Supply chain attacks in agent skills are already happening. ClawForce certifies skills for malware, credential theft, data exfiltration. You can't afford to trust unaudited code in an AI pipeline." — @PixelFamiliar on X ([link](https://x.com/PixelFamiliar/status/2040702393889776001))

> "Will skills replace MCP servers eventually? How are skills different from prompts/commands/tools?" — hn/latand6 community discussion on HN ([link](https://news.ycombinator.com/item?id=47475832))

> "Vendor lock-in in agent skills is the new npm left-pad." — @neon_artival on X ([link](https://x.com/neon_artival/status/2040686394377461790))

> "Google went from Gemma 4 release to on-device agent skills in under 48 hours. The speed of adoption is the real story." — @Kushagrat15 on X ([link](https://x.com/Kushagrat15/status/2040679174231466391))

> "Agent Skills are the new npm packages of AI — and they need the same supply chain security." — JFrog ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "MCP is the universal standard protocol for connecting AI models to tools, data and applications. In one year, it has become one of the fastest-growing open-source projects in AI." — MCP Blog ([link](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/))

> "Pinterest deployed a full internal MCP ecosystem — production servers, a central registry, and agent integrations across developer tools — replacing ad hoc integrations with a standardized, scalable substrate." — InfoQ ([link](https://www.infoq.com/news/2026/04/pinterest-mcp-ecosystem/))

> "Each skill in the chain is independently testable and reusable. Composability is the design goal." — MindStudio ([link](https://www.mindstudio.ai/blog/claude-code-skill-collaboration-chaining-workflows))

> "agent 'build me a churn model from this data' = YES PLEASE" — hn/chenxi9649 on one-shot PySpark agent skills ([link](https://news.ycombinator.com/item?id=47534936))
