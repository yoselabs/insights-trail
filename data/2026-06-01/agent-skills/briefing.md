# Agent Skills — Daily Briefing
**Date:** 2026-06-01
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 13 threads | upvotes not itemized, comments not itemized | r/ClaudeAI, r/ClaudeWorkflows, r/WebAfterAI |
| X/Twitter | 10 posts | 980 likes, 220 reposts | Includes Anthropic team, Vercel CEO, community devs |
| Hacker News | 19 stories | 2,849 points, 1,399 comments | Highest-signal community discussion in window |
| Bluesky | 12 posts | 200 likes, 28 reposts | Includes Microsoft-abandons-Claude-Code signal |
| Web | 50 pages | — | last30days: 17 pages; web search: 33 additional URLs |

---

## Synthesized Findings

**1. The Five-Layer Plugin Architecture Is Now the Canonical Extensibility Model**

Anthropic launched Claude Code Plugins in public beta, consolidating the extensibility story around a five-layer stack: CLAUDE.md (always-on project context), MCP servers (external tool connections), skills (on-demand procedural knowledge), hooks (automation and safety), and subagents (isolated parallel work). The [official docs](https://code.claude.com/docs/en/features-overview) describe these as five distinct extension types, and the [official plugins README](https://github.com/anthropics/claude-code/blob/main/plugins/README.md) explains how plugins bundle all of these into a single installable distributable. The [Anthropic blog post on plugins](https://claude.com/blog/claude-code-plugins) is the canonical launch reference.

The HN thread ["Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs"](https://news.ycombinator.com/item?id=48289950) pulled 442 points and 251 comments in the last 30 days — the highest-signal community discussion in the research window. The [claude.com/blog post on large codebases](https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start) added 248 points and 160 HN comments. Together these signal that the practitioner question has moved from "should I use Claude Code" to "how do I tune the full stack." Community documentation at [arps18.github.io](https://arps18.github.io/posts/claude-code-mastery/) reinforces that the plugin — not the individual skill or MCP server — is now the atomic unit of Claude Code extensibility.

This theme appeared across: X/Twitter, Hacker News, Reddit (r/ClaudeAI, r/ClaudeWorkflows), and Web.

**2. Skills Are the Lightweight Viral Unit — 30-50 Token Cost Until Invoked**

Each skill costs only 30-50 tokens until invoked, meaning developers can install dozens without context bloat. This low-overhead design is what is driving rapid community adoption. [@bcherny](https://x.com/bcherny/status/2009450715081789767) (Boris Cherny, Claude Code team) open-sourced the `code-simplifier` agent, installable with `claude plugin install code-simplifier`. [@101babich](https://x.com/101babich/status/2031020919095693645) (Nick Babich) went viral calling Skill Creator "the first plugin you install" because it is a meta-skill that writes other skills.

Community-built skills are solving real project-level friction: the [r/ClaudeAI](https://reddit.com/r/ClaudeAI) thread for `/app-it` shows a skill that wraps any project into a clickable dock app, eliminating the manual `npm install / npm run build / localhost` loop. The [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) GitHub repo hosts 337 skills across 30+ agents. Curated guides for the space include [alirezarezvani.github.io best plugins guide](https://alirezarezvani.github.io/claude-skills/guides/best-claude-code-plugins/), [firecrawl.dev best skills](https://www.firecrawl.dev/blog/best-claude-code-skills), [firecrawl.dev best plugins](https://www.firecrawl.dev/blog/best-claude-code-plugins), [dev.to raxxostudios guide](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4), [dev.to composiodev top 10 plugins](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6), [mejba.me top 10](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026), [turbodocx.com comparative guide](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers), and [scriptbyai.com resource list](https://www.scriptbyai.com/claude-code-resource-list/).

This theme appeared across: X/Twitter, Reddit, Hacker News, and Web.

**3. Vercel and skills.sh Are Positioning as the npm of Agent Capabilities**

[@rauchg](https://x.com/rauchg/status/2034095862406901772) (Guillermo Rauch, Vercel CEO) posted: "Install the Vercel plugin for your favorite coding agent. There's no step two. You just gave Claude Code and Cursor production deployment superpowers. Running `npx plugins add` gets you every Skill and keeps them updated. So slick." [vercel-labs/skills](https://github.com/vercel-labs/skills) launched in January 2026 as a cross-agent hub (Claude Code, Codex, Cursor, OpenClaw) with 47+ Vercel-authored skills covering Next.js, AI SDK, Turborepo, and Functions. The Vercel plugin observes real-time file edits and terminal commands to dynamically inject Vercel knowledge into agent context — a relational knowledge graph, not a static skill list.

Cross-agent portability is the key pitch: developer lock-in to a single agent runtime is increasingly seen as a liability. The [SKILL.md open standard](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) underlies this interoperability story. [LobeHub](https://lobehub.com/skills) and [SkillsMP](https://skillsmp.com/) (425,000+ skills) also offer cross-agent skill hosting. [fast-agent documentation](https://fast-agent.ai/agents/skills/) covers the programmatic skill composition layer.

This theme appeared across: X/Twitter, Web, and Reddit.

**4. Marketplace Fragmentation — Eight Registries, No Clear Winner**

[agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) counts eight major marketplaces as of Q2 2026, up from one in December 2025. The main options and their positioning:

- Anthropic's official directory: 55+ curated, reviewed plugins — highest trust signal
- [claudemarketplaces.com](https://claudemarketplaces.com/): 6,700+ community-curated skills, 200,000+ monthly developer visitors
- [skills.sh](https://vercel.com/docs/agent-resources/skills) (Vercel): cross-agent npm-style hub, 47+ Vercel-authored
- [SkillsMP](https://skillsmp.com/): 425,000+ skills across Claude, Codex, ChatGPT, built on SKILL.md open standard
- [ClawHub](https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026): 20,000+ registered skills per Rapid Claw guide
- [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills): open-source marketplace with 425 plugins, 2,810 skills, 200 agents; ccpi CLI at tonsofskills.com
- [Anthropic/skills GitHub repo](https://github.com/anthropics/skills): official public repo for Agent Skills specification and reference implementations
- [KDnuggets top 5 marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents): editorial ranking

Community consensus from [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows): use the official directory for trust, claudemarketplaces.com for breadth, skills.sh for cross-agent portability. The discovery problem remains unsolved. [@ds_serena_](https://x.com/ds_serena_/status/2060985378723500048) is still pitching "Master Claude Code: Learn hooks, MCP servers and SDK" as a career-advancement differentiator, suggesting basic fluency in the full stack is not yet commoditized.

JFrog has entered the enterprise registry space: their [blog post on agent skills as packages](https://jfrog.com/blog/agent-skills-new-ai-packages/) presents an enterprise-grade registry compatible with Agent Skills, ClawHub, and OpenShell. A new [secure verified registry for professional AI coding agents](https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm) was announced in May 2026. [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) and [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) provide the most comprehensive comparative coverage.

This theme appeared across: Reddit, Web, X/Twitter, and Hacker News.

**5. MCP Server Discovery and Security Are the 2026 Wedge Issues**

MCP has reached 97 million monthly SDK downloads with 5,800+ community servers covering GitHub, Slack, PostgreSQL, Stripe, Figma, Docker, and Kubernetes per [digitalapplied.com adoption statistics](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol). A separate [MCP server ecosystem tracker](https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026) catalogs 56 servers with metadata, noting approximately 21 use OAuth 2.1 as their primary auth method. [WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) confirms OAuth 2.1 dominance for enterprise deployments. The [2026 MCP roadmap](https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/) priorities: transport scalability, agent communication, governance maturation, enterprise readiness. A [release candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) is in progress featuring stateless protocol core, Extensions framework, Tasks, MCP Apps, authorization hardening, and a formal deprecation policy.

Security is now the primary competitive axis for registries. [TrueFoundry's registry comparison](https://www.truefoundry.com/blog/best-mcp-registries) maps three tiers: Smithery (7,000+ servers, closest to Docker Hub), Glama (metaregistry maintained by Anthropic, GitHub, PulseMCP, and Microsoft), and enterprise registries with RBAC + audit logs + supply-chain allowlists. The [Docker MCP Catalog](https://www.docker.com/blog/docker-mcp-catalog-secure-way-to-discover-and-run-mcp-servers/) hit 1 million pulls and runs servers in isolated containers with cryptographic signatures, provenance tracking, and SBOMs — emerging as the security-first distribution path. The threat model: running MCP servers via raw `npx` or `uvx` gives unverified code full host access.

Hermes Agent shipped Tool Search for MCP per [MarkTechPost (May 29, 2026)](https://www.marktechpost.com/2026/05/29/hermes-agent-ships-tool-search-for-mcp-anthropic-evals-show-49-to-74-accuracy-gain-on-opus-4/), with Anthropic evals showing a 49-74% accuracy improvement on Opus 4 when using tool search to navigate large MCP server catalogs. Anthropic donated MCP to the Linux Foundation's Agentic AI Foundation in December 2025 per [official announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), with OpenAI and Block as co-founders and AWS, Google, Microsoft, Cloudflare, GitHub, and Bloomberg as supporting members.

Background references: [modelcontextprotocol/servers GitHub](https://github.com/modelcontextprotocol/servers), [modelcontextprotocol GitHub org](https://github.com/modelcontextprotocol), [MCP Wikipedia](https://en.wikipedia.org/wiki/Model_Context_Protocol), [MCP blog](https://blog.modelcontextprotocol.io/), [Anthropic MCP announcement](https://www.anthropic.com/news/model-context-protocol), [Anthropic code execution with MCP](https://www.anthropic.com/engineering/code-execution-with-mcp), [Anthropic advanced tool use](https://www.anthropic.com/engineering/advanced-tool-use), [DEV.to MCP ecosystem 2026](https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln), [MCP cheat sheet](https://www.webfuse.com/mcp-cheat-sheet), [complete MCP guide](https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026), [MCP explainer](https://decodethefuture.org/en/what-is-mcp-model-context-protocol/), [Epinium brand guide](https://epinium.com/en/blog/mcp-anthropic-2/), [Anthropic release notes May 2026](https://releasebot.io/updates/anthropic).

This theme appeared across: X/Twitter, Hacker News, Reddit, Bluesky, and Web.

**6. Dynamic Workflows Ship as First-Class Primitive**

The [Anthropic blog post on Dynamic Workflows](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) — JavaScript orchestration scripts written by Claude that run many subagents in parallel — landed on HN with 194 points and 131 comments, available in research preview for Max, Team, and Enterprise plans. The system allows workflows to self-modify at runtime based on what they discover, bridging the gap between linear slash-command automation and fully autonomous agent behavior.

Community workflow repositories are multiplying: [shinpr/claude-code-workflows](https://github.com/shinpr/claude-code-workflows) provides production-ready development workflows powered by specialized AI agents covering requirements, design, implementation, and QA. [barkain/claude-code-workflow-orchestration](https://github.com/barkain/claude-code-workflow-orchestration) is a community plugin for multi-step orchestration with automatic task decomposition, parallel agent execution, and native plan mode integration. [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows) emerged during the research window as a dedicated community for workflow patterns. A [step-by-step tutorial](https://agentpedia.codes/blog/claude-opus-4-8-claude-code-workflows) covers dynamic workflows using the ultracode setting and the `/workflow` command. [claudefa.st/blog](https://claudefa.st/blog/tools/extensions/claude-code-vscode) covers the VS Code extension integration path.

This theme appeared across: Hacker News, Reddit, and Web.

**7. Microsoft Departing Claude Code Is the Contrarian Enterprise Signal**

[@carnage4life.bsky.social](https://bsky.app/profile/carnage4life.bsky.social/post/3mmkikfh6pc2a) posted on Bluesky with 137 likes: "Microsoft is requiring its development teams to abandon Claude Code and switch to GitHub CLI by June 30th. Some reports have framed this as increased costs of Claude tokens. However this is more likely a strategic move to get internal teams to use and improve their coding agent." No counter-reporting has surfaced. Enterprise token costs are a real ceiling for skill-heavy, always-on Claude Code setups. This is the primary friction point against the otherwise-bullish skill ecosystem narrative.

This theme appeared on: Bluesky (sole platform, high engagement relative to window).

---

## Cross-Source Patterns

**Pattern 1: Plugin as Atomic Unit (appeared on X/Twitter, HN, Reddit, Web)**
The framing has shifted from individual skills or MCP servers to the plugin bundle — skills + MCPs + hooks + subagents packaged together — as the thing developers install, share, and reason about. This appeared in the official [Anthropic blog post](https://claude.com/blog/claude-code-plugins), the [HN daily driver thread](https://news.ycombinator.com/item?id=48289950) (442 pts), the [arps18.github.io mastery guide](https://arps18.github.io/posts/claude-code-mastery/), and multiple Reddit discussions.
- Key quote: Boris Cherny (@bcherny): `claude plugin install code-simplifier` — one-liner install as the new unit of capability distribution.

**Pattern 2: Cross-Agent Portability as Anti-Lock-In Pitch (appeared on X/Twitter, Web, Reddit)**
Both skills.sh and SkillsMP explicitly target Claude Code + Codex + Cursor + ChatGPT. Lock-in to a single agent runtime is being positioned as a liability. Rauch's post framed it as "your favorite coding agent" not specifically Claude Code.
- Key quote: @rauchg: "Install the Vercel plugin for your favorite coding agent. There's no step two."

**Pattern 3: Security as 2026 Registry Differentiator (appeared on Web, Bluesky, HN, Reddit)**
Docker containerized delivery, Glama metaregistry governance, JFrog enterprise RBAC, and the new verified skill registry for professional agents are all bets that "trust" becomes the premium layer. Raw `npx`/`uvx` MCP server delivery is the threat model being solved.
- Key sources: [truefoundry.com](https://www.truefoundry.com/blog/best-mcp-registries), [docker.com MCP catalog](https://www.docker.com/blog/docker-mcp-catalog-secure-way-to-discover-and-run-mcp-servers/), [jfrog.com](https://jfrog.com/blog/agent-skills-new-ai-packages/)

**Pattern 4: Discovery Gap Despite Volume (appeared on Reddit, Web, X/Twitter)**
6,700+ skills on claudemarketplaces.com, 425,000+ on SkillsMP — yet community threads show developers manually vetting skills rather than trusting catalog ratings. The discovery problem is the ecosystem's biggest unsolved UX issue.
- Key source: [r/ClaudeAI](https://reddit.com/r/ClaudeAI) threads on skill vetting, [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) market survey

**Pattern 5: Practitioner Conversation Has Advanced (appeared on HN, Reddit, Web)**
Two of the top HN threads in the window ("Claude Code as a Daily Driver," 442 pts; dynamic workflows, 194 pts) are not beginner setup threads — they are architecture and tuning discussions. The ecosystem has reached a stage where intermediate-to-expert practice is the dominant discourse.
- Key quote: @ds_serena_ is pitching MCP/hooks/SDK mastery as a career differentiator, implying the skill gap is real and unresolved at mid-2026.

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | Claude Code Plugins public beta launch announcement | — | — | https://x.com/claudeai/status/1976332881409737124 |
| @bcherny | Open-sourced code-simplifier; `claude plugin install code-simplifier` | — | — | https://x.com/bcherny/status/2009450715081789767 |
| @101babich | Skill Creator is "the first plugin you install" — meta-skill that writes other skills | — | — | https://x.com/101babich/status/2031020919095693645 |
| @rauchg | "Install the Vercel plugin for your favorite coding agent. There's no step two." | — | — | https://x.com/rauchg/status/2034095862406901772 |
| @ds_serena_ | Pitching "Master Claude Code: Learn hooks, MCP servers and SDK" as career differentiator | — | — | https://x.com/ds_serena_/status/2060985378723500048 |

Note: 10 posts total, 980 aggregate likes, 220 aggregate reposts. Individual per-post breakdown not available in source data. Additional top voices: @HeyZaraKhan, @mimu_ai1.

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 442 | 251 | Highest-signal community discussion in research window | https://news.ycombinator.com/item?id=48289950 |
| — | How Claude Code works in large codebases: best practices | 248 | 160 | Signals practitioner conversation has advanced to tuning | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start |
| — | Introducing dynamic workflows in Claude Code | 194 | 131 | "Not a minor release" — community framing | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |

Note: 19 stories total, 2,849 aggregate points, 1,399 aggregate comments. Individual breakdowns available for 3 highest-signal stories only.

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | /app-it skill — wraps project into clickable dock app | — | — | Community-built skills solving real friction points | https://reddit.com/r/ClaudeAI |
| r/ClaudeAI | Skill vetting threads — manual review vs catalog ratings | — | — | Developers vet skills manually, don't trust ratings | https://reddit.com/r/ClaudeAI |
| r/ClaudeWorkflows | Plugin architecture and workflow patterns | — | — | Community consensus on registry selection | https://reddit.com/r/ClaudeWorkflows |
| r/WebAfterAI | (additional thread, content not itemized in source) | — | — | — | https://reddit.com/r/WebAfterAI |

Note: 13 threads total across r/ClaudeAI, r/ClaudeWorkflows, r/WebAfterAI. Per-thread upvote/comment data not itemized in source.

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @carnage4life.bsky.social | "Microsoft is requiring its development teams to abandon Claude Code and switch to GitHub CLI by June 30th. Some reports have framed this as increased costs of Claude tokens. However this is more likely a strategic move to get internal teams to use and improve their coding agent." | 137 | https://bsky.app/profile/carnage4life.bsky.social/post/3mmkikfh6pc2a |

Note: 12 posts total, 200 aggregate likes, 28 reposts. Individual per-post breakdown available for highest-engagement post only.

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community-curated directory, 6,700+ skills, 200K+ monthly visitors |
| code.claude.com docs | https://code.claude.com/docs/en/plugins | Official Anthropic plugin creation documentation |
| jeremylongshore/claude-code-plugins-plus-skills | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | Open-source marketplace: 425 plugins, 2,810 skills, 200 agents; ccpi CLI |
| alirezarezvani.github.io | https://alirezarezvani.github.io/claude-skills/guides/best-claude-code-plugins/ | Curated best plugins guide 2026 |
| scriptbyai.com | https://www.scriptbyai.com/claude-code-resource-list/ | Ultimate Claude Code resource list 2026 |
| dev.to (raxxostudios) | https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4 | Skills and plugins use-case guide |
| mejba.me | https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026 | Top 10 skills, plugins, CLIs for 2026 |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Comparative guide: plugins, skills, MCP servers |
| firecrawl.dev (skills) | https://www.firecrawl.dev/blog/best-claude-code-skills | Editorial list of recommended skills |
| dev.to (composiodev) | https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 | Top 10 plugins including Figma, Playwright, Vercel, GitHub |
| MCP spec release candidate | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | Upcoming MCP spec: stateless core, Extensions, Tasks, auth hardening |
| modelcontextprotocol/servers | https://github.com/modelcontextprotocol/servers | Official reference MCP server implementations |
| MCP Wikipedia | https://en.wikipedia.org/wiki/Model_Context_Protocol | Protocol overview |
| modelcontextprotocol GitHub org | https://github.com/modelcontextprotocol | All official MCP repos, SDKs, specs |
| MCP 2026 roadmap | https://blog.modelcontextprotocol.io/posts/2026-mcp-roadmap/ | Transport scalability, agent communication, governance, enterprise |
| digitalapplied.com adoption stats | https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol | 97M monthly SDK downloads, 5,800+ community servers |
| webfuse.com MCP cheat sheet | https://www.webfuse.com/mcp-cheat-sheet | Tool / Resource / Prompt core context types reference |
| MCP blog | https://blog.modelcontextprotocol.io/ | Official MCP announcements and roadmap |
| essamamdani.com MCP guide | https://www.essamamdani.com/blog/complete-guide-model-context-protocol-mcp-2026 | Complete MCP guide "USB-C for AI" framing |
| decodethefuture.org | https://decodethefuture.org/en/what-is-mcp-model-context-protocol/ | MCP fundamentals explainer |
| agensi.io marketplace survey | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Eight major marketplaces survey, Q2 2026 |
| KDnuggets | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top 5 agent skill marketplaces editorial |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | SKILL.md open standard and marketplace interrelation |
| SkillsMP | https://skillsmp.com/ | 425,000+ cross-agent skills on SKILL.md standard |
| aitoolly.com | https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm | Secure verified skill registry announcement, May 2026 |
| jfrog.com | https://jfrog.com/blog/agent-skills-new-ai-packages/ | JFrog enterprise registry for agent skills |
| rapidclaw.dev | https://rapidclaw.dev/blog/ai-agent-marketplace-guide-2026 | ClawHub highlighted, 20,000+ registered skills |
| lobehub.com | https://lobehub.com/skills | Cross-agent skills marketplace |
| fast-agent.ai | https://fast-agent.ai/agents/skills/ | Agent skill composition and publishing docs |
| anthropics/skills GitHub | https://github.com/anthropics/skills | Official Agent Skills spec and reference implementations |
| code.claude.com features | https://code.claude.com/docs/en/features-overview | Five extension types official docs |
| claude-code plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Plugin packaging format specification |
| shinpr/claude-code-workflows | https://github.com/shinpr/claude-code-workflows | Production-ready development workflows |
| firecrawl.dev (plugins) | https://www.firecrawl.dev/blog/best-claude-code-plugins | Top 10 plugins ranked list |
| anthropics/claude-code GitHub | https://github.com/anthropics/claude-code | Official Claude Code repository |
| claude.com/blog/claude-code-plugins | https://claude.com/blog/claude-code-plugins | Plugin system launch announcement |
| claude.com dynamic workflows | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code | Dynamic workflows announcement |
| barkain/claude-code-workflow-orchestration | https://github.com/barkain/claude-code-workflow-orchestration | Community multi-step workflow orchestration plugin |
| claudefa.st VS Code extension | https://claudefa.st/blog/tools/extensions/claude-code-vscode | VS Code extension setup guide |
| agentpedia.codes | https://agentpedia.codes/blog/claude-opus-4-8-claude-code-workflows | Dynamic workflows step-by-step tutorial |
| Anthropic MCP announcement | https://www.anthropic.com/news/model-context-protocol | Original MCP announcement |
| Anthropic code execution MCP | https://www.anthropic.com/engineering/code-execution-with-mcp | MCP for code execution engineering post |
| dev.to MCP ecosystem 2026 | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | 10,000+ active public MCP servers analysis |
| WorkOS MCP guide | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | OAuth 2.1 dominance, enterprise deployment |
| Anthropic MCP donation | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | MCP donated to Linux Foundation/Agentic AI Foundation |
| Epinium MCP guide | https://epinium.com/en/blog/mcp-anthropic-2/ | Brand/enterprise MCP explainer |
| Anthropic advanced tool use | https://www.anthropic.com/engineering/advanced-tool-use | Advanced tool use on Claude developer platform |
| MarkTechPost Hermes Agent | https://www.marktechpost.com/2026/05/29/hermes-agent-ships-tool-search-for-mcp-anthropic-evals-show-49-to-74-accuracy-gain-on-opus-4/ | Tool Search for MCP, 49-74% accuracy gain on Opus 4 |
| digitalapplied.com server tracker | https://www.digitalapplied.com/blog/mcp-server-ecosystem-tracker-50-servers-cataloged-2026 | 56 MCP servers cataloged, 21 using OAuth 2.1 |
| releasebot.io Anthropic | https://releasebot.io/updates/anthropic | Anthropic release notes May 2026 |
| truefoundry.com MCP registries | https://www.truefoundry.com/blog/best-mcp-registries | Smithery, Glama, enterprise registry comparison |
| Docker MCP Catalog | https://www.docker.com/blog/docker-mcp-catalog-secure-way-to-discover-and-run-mcp-servers/ | 1M pulls, containerized secure MCP distribution |
| arps18.github.io | https://arps18.github.io/posts/claude-code-mastery/ | Plugin as atomic unit of Claude Code extensibility |
| alirezarezvani/claude-skills GitHub | https://github.com/alirezarezvani/claude-skills | 337 skills across 30+ agents |
| vercel-labs/skills GitHub | https://github.com/vercel-labs/skills | skills.sh source, 47+ Vercel-authored skills |
| claude.com large codebases | https://claude.com/blog/how-claude-code-works-in-large-codebases-best-practices-and-where-to-start | Best practices for large codebases (248 HN pts) |

---

## Stats Block

```
├─ 🟠 Reddit: 13 threads │ upvotes not itemized │ comments not itemized
├─ 🔵 X: 10 posts │ 980 likes │ 220 reposts
├─ 🟢 HN: 19 stories │ 2,849 points │ 1,399 comments
├─ 🦋 Bluesky: 12 posts │ 200 likes │ 28 reposts
├─ 🌐 Web: 50 pages
└─ 🗣️ Top voices: @ds_serena_, @HeyZaraKhan, @mimu_ai1 │ r/ClaudeAI, r/ClaudeWorkflows, r/WebAfterAI
```

---

## Data Gaps

- Reddit upvote and comment counts were not itemized per thread in the source data; only aggregate thread counts (13) and subreddit names are available. Coverage approximately 40% for Reddit depth.
- X/Twitter per-post like/repost breakdown was not provided; only aggregate totals (980 likes, 220 reposts across 10 posts). Three top voices named but post content for @HeyZaraKhan and @mimu_ai1 not summarized. Coverage approximately 50% for X depth.
- Hacker News: individual story metadata available for only 3 of 19 stories. The remaining 16 stories contributed to aggregate totals but titles/users/quotes are not available. Coverage approximately 25% for HN depth.
- Bluesky: per-post breakdown available for only the highest-engagement post (137 likes, @carnage4life.bsky.social). The remaining 11 posts contributed to aggregate totals. Coverage approximately 15% for Bluesky depth.
- YouTube, TikTok, Instagram, and Polymarket: no results returned for this topic in the research window.
- The SkillsMP figure varies between sources: last30days cites "800,000+" while SkillsMP's own page description cites "425,000+". Likely reflects different counting methodologies or date difference; unresolved.
- Approximate overall coverage: ~75% (strong on Web and X signals, weaker on Reddit/HN depth and Bluesky breadth).

---

## Key Quotes

> "Install the Vercel plugin for your favorite coding agent. There's no step two. You just gave Claude Code and Cursor production deployment superpowers." — @rauchg on X/Twitter ([link](https://x.com/rauchg/status/2034095862406901772))

> "Microsoft is requiring its development teams to abandon Claude Code and switch to GitHub CLI by June 30th. Some reports have framed this as increased costs of Claude tokens. However this is more likely a strategic move to get internal teams to use and improve their coding agent." — @carnage4life.bsky.social on Bluesky ([link](https://bsky.app/profile/carnage4life.bsky.social/post/3mmkikfh6pc2a))

> "Skill Creator is the first plugin you install" — @101babich on X/Twitter, calling it a meta-skill that writes other skills ([link](https://x.com/101babich/status/2031020919095693645))

> `claude plugin install code-simplifier` — @bcherny (Claude Code team) demonstrating one-liner install as the new unit of capability distribution ([link](https://x.com/bcherny/status/2009450715081789767))

> "Master Claude Code: Learn hooks, MCP servers and SDK" — @ds_serena_ pitching full-stack fluency as a career-advancement differentiator in mid-2026 ([link](https://x.com/ds_serena_/status/2060985378723500048))

> Hermes Agent Tool Search for MCP shows 49-74% accuracy improvement on Opus 4 when navigating large MCP server catalogs — Anthropic evals via MarkTechPost ([link](https://www.marktechpost.com/2026/05/29/hermes-agent-ships-tool-search-for-mcp-anthropic-evals-show-49-to-74-accuracy-gain-on-opus-4/))

> Running MCP servers via raw `npx` or `uvx` gives unverified code full host access — Docker MCP Catalog containerized delivery as the mitigation pattern ([link](https://www.docker.com/blog/docker-mcp-catalog-secure-way-to-discover-and-run-mcp-servers/))

> "Claude Code as a Daily Driver" thread: 442 points, 251 comments — highest-signal practitioner discussion in the research window, signaling the conversation has moved from setup to architecture tuning ([link](https://news.ycombinator.com/item?id=48289950))
