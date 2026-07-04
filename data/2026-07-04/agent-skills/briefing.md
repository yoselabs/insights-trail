# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-04
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 15 threads | 44,648 upvotes, 2,507 comments | r/ClaudeAI dominant |
| X/Twitter | 21 posts | 5,612 likes, 382 reposts | @vivoplt, @AntonMartyniuk top voices |
| Hacker News | 15 stories | 4,045 points, 1,994 comments | steganography story dominated |
| Bluesky | 12 posts | 81 likes, 1 repost | Japanese-language coverage notable |
| GitHub | 13 items | 44 reactions, 120 comments | marketplace adapter PRs, skill registries |
| Web | 19 pages | — | via WebSearch (7 engine + 12 supplemental) |

---

## Synthesized Findings

### 1. The "Senior vs Junior Vibe Coder" Persona Is the Ecosystem's New Origin Story

The most-engaged post of the research window came from [@vivoplt](https://x.com/vivoplt/status/2072672502174925123) (588 likes, 48 reposts), who articulated a paradigm that is spreading fast across X and developer circles:

> "junior vibe coder: installs claude code/antigravity/codex/cursor, thinks about what to build, prompts Claude, begin build, generates an AI slop and debugs endlessly. senior vibe coder: installs claude code/antigravity/codex/cursor, **setup personal preferences and agent memory, setup agent skills and rules, integrate connectors and MCP servers**, test agent out, thinks about what to build..."

This framing has crystallized something the community had been circling around: skills, rules, and MCP configuration are not optional add-ons - they are the differentiation between developers who fight their AI tooling and those who multiply their output through it. The tweet's virality signals broad resonance across the Claude Code, Codex, Cursor, and Hermes Agent communities.

Reinforcing the message, [@suraj_sharma14](https://x.com/suraj_sharma14/status/2073300779767603640) published a "f*ck your weekend plans" upskilling list on July 4 that put MCP mastery ("Build your own MCP servers") and loop engineering alongside Claude Code workflows as non-negotiable skills for 2026 AI builders.

**Cross-platform signal:** Reddit (r/ClaudeAI), X, Bluesky all show active discussions about Claude Code's update velocity and agent-first paradigm shift.

### 2. The Open SKILL.md Standard Has Become Cross-Industry Infrastructure

What started as Anthropic's Claude Code skills format is now the agent industry's de facto extension standard. Per [The New Stack](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) and [DEV Community](https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg), Anthropic published SKILL.md to agentskills.io as an open standard on December 18, 2025. Within 48 hours, Microsoft integrated it into VS Code Copilot and OpenAI added support to ChatGPT and Codex CLI.

By Q2 2026, [32 tools from competing companies](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/) - including Google's Gemini CLI, JetBrains' Junie, AWS's Kiro, and Block's Goose - all read the same SKILL.md files from the same directory structure. [@Layton_Gott](https://x.com/Layton_Gott/status/2073125199030157540) captured the pitch simply: "Skills have a HUGE impact in AI coding right now... A skill is just a markdown file with a dialed in prompt essentially. They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw."

[@AntonMartyniuk](https://x.com/AntonMartyniuk/status/2072646509137363103) (294 likes, 56 reposts) broke a major story: Microsoft quietly published 99 ready-made .NET skills for AI agents - official, open-sourced, and working across Claude Code, Codex, GitHub Copilot, and Cursor. The comment: "Most .NET developers have no idea they exist."

**Sources:** X, Web (thenewstack.io, paperclipped.de, dev.to), HN

### 3. Marketplace Explosion: From 1 Registry to 8 Major Platforms in 7 Months

Per [Totalum](https://www.totalum.app/blog/agent-skills-marketplaces-2026), the agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. The five that matter:

- **Anthropic Claude Skills** - official marketplace; 101 plugins as of March 2026, 33 Anthropic-built
- **Vercel skills.sh** - went GA June 5, 2026 with 600,000 OSS skills distributed via OIDC; [TechInformed](https://techinformed.com/how-vercel-built-an-ai-agent-ecosystem-on-claudes-open-skills-standard/) covered the launch
- **OpenAI Codex plugins** - adopted open standard; agentskills.io integration per [developers.openai.com](https://developers.openai.com/codex/skills)
- **MCP ecosystem** - official registry at [registry.modelcontextprotocol.io](https://registry.modelcontextprotocol.io/) grew from September 2025 launch to ~2,000 server entries; Glama's registry hit 19,831 servers by March 2026
- **Community aggregators** - SkillsMP lists 1.9 million public skills scraped from GitHub; [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) ships 425 plugins, 2,810 skills, 200 agents with the ccpi CLI package manager

[@github_update](https://x.com/github_update/status/2067259115777507386) published "AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking" in mid-June, further cementing the ecosystem narrative.

**Sources:** X, Web (totalum.app, techinformed.com), HN

### 4. X Platform Launches Hosted MCP Servers - Breaking Development

One of the weekend's most concrete ecosystem moves came from [@Tork_Lab](https://x.com/Tork_Lab/status/2073240381802905624) (44 likes): X/Twitter now supports hosted MCP servers, connecting AI tools and agents directly to the X API and X developer docs. The announcement:

> "What's new: X MCP connects AI tools directly to X API endpoints. Docs MCP lets agents search X API documentation inside the workflow. Works with Grok Build, Cursor, Claude, VS Code, and other MCP-compatible tools."

This is a major platform-level move: X is treating MCP connectivity as a first-class developer feature. Combined with Microsoft's Windows On-device Agent Registry (ODR) and Anthropic's donation of MCP to the Agentic AI Foundation, MCP is becoming platform infrastructure rather than a developer convenience.

The [MCP Specification Release Candidate](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) was also announced with a v0.1 API freeze and new MCP Server Cards standard - a `.well-known` URL proposal for automated server discovery by browsers, crawlers, and registries.

**Sources:** X, Web (blog.modelcontextprotocol.io, workos.com)

### 5. Security Is the Underreported Risk in the Skills Ecosystem

Two signals this week point to a growing supply-chain threat. [@JDSalbego](https://x.com/JDSalbego/status/2072682302652485632) posted the question bluntly: "How many MCP servers does your AI agent connect to right now? Not how many you think. How many it actually connects to. Most developers have 3-5 they installed intentionally. Most don't know about the ones their tools installed as dependencies. Each one is a connection to an external service with access to your resources. Each one is an attack surface."

Per [Totalum](https://www.totalum.app/blog/agent-skills-marketplaces-2026), Snyk's ToxicSkills study found 36% of skills on major registries contain security flaws and 76 had confirmed malicious payloads - a sobering number given SkillsMP alone hosts 1.9M public skills.

On HN, "Claude Code is steganographically marking requests" ([thereallo.dev](https://thereallo.dev/blog/claude-code-prompt-steganography)) reached 2,432 points and 742 comments - the top story of the research window by a wide margin. A related thread, "Anthropic has embedded hidden spyware-like code in Claude Code," also circulated (56 HN points). Both reflect rising scrutiny of what Claude Code's harness does behind the scenes. Whether the steganography is a privacy issue or a legitimate request-tracking mechanism, the community is now watching.

**Sources:** X, HN, Web (totalum.app via Snyk ToxicSkills)

### 6. "Context Soup" Is the Real MCP Operational Challenge

[@goon_nguyen](https://x.com/goon_nguyen/status/2073197487880372437) captured the production gap that practitioners keep hitting:

> "Most agent prototypes fail at the same boring layer: not reasoning, but operations. The prompt looks fine. The demo works. Then production asks ugly questions: where does session state live? what can the tool call actually touch? **how do we plug in MCP servers without turning context into soup?** how do we trace the callback that failed?"

This framing - "context soup" from too many MCP servers - is the most specific technical critique of the ecosystem's current state. It also points to a product gap: no dominant tool yet handles MCP context management elegantly at scale.

[@stretchcloud](https://x.com/stretchcloud/status/2073333494126989346) pointed to LangChain's OpenWiki as a partial solution - a CLI that generates structured wiki documentation for repos and injects it into CLAUDE.md or AGENTS.md, keeping it updated via GitHub Actions. "The bottleneck shifted from writing code to grounding agents in codebase context."

On HN, "Recall - Local project memory for Claude Code" ([github.com/raiyanyahya/recall](https://github.com/raiyanyahya/recall)) reached 137 points and 85 comments as a community-built solution to the same problem. Cross-tool memory persistence (Bluesky: LoreConvo, "follows you across Claude Code, Codex, Cursor, and Hermes Agent - the same context, everywhere you work") is emerging as a distinct product category.

**Sources:** X, HN, Bluesky

### 7. The OpenCode Ecosystem Shows What "Ecosystem Formation" Looks Like at Scale

[@stretchcloud](https://x.com/stretchcloud/status/2072974880963023113) made the observation the mainstream narrative misses: "The part of the open-source coding agent story that gets underreported is the ecosystem forming around it. OpenCode hit 160,000 GitHub stars and 7.5 million monthly developers as of early 2026. But the growth signal I find more interesting is the guide structure that's emerging: agents, skills, plugins, MCP integrations, headless CI runs, custom model routing. That is the same layered architecture that Claude Code, GitHub Copilot, and others are converging on."

OpenCode's 160K stars - the most-starred open-source coding agent - is a useful data point for where community energy is concentrating. The [superpowers](https://github.com/obra/superpowers) framework hit 224K stars, per a GitHub issue in [DeepSeek-Reasonix](https://github.com/esengine/DeepSeek-Reasonix/issues/3955) - where developers are requesting nested skill directory support to be compatible with the Claude Code plugin ecosystem's "plugin pack" distribution format.

**Sources:** X, GitHub

### 8. Anthropic's Free Certification Curriculum Now Includes Agent Skills

[@aiwithjonny](https://x.com/aiwithjonny/status/2073039922202919120) (82 likes) and [@KhushiPatil25](https://x.com/KhushiPatil25/status/2072921582356578509) (55 likes) both publicized Anthropic's free course catalog - which now explicitly includes "Introduction to Agent Skills: Build, configure, and share Skills in Claude Code - reusable instructions Claude applies automatically." This is Anthropic's demand-creation play: training developers on the skills paradigm directly scales ecosystem adoption faster than any marketplace feature.

HN's "ZCode: Claude Code from the Makers of GLM" ([zcode.z.ai](https://zcode.z.ai/cn), 277 points, 15 comments) shows the pattern extending to non-Anthropic players: GLM's team built their own Claude Code-shaped coding agent, including the plugin/marketplace/hooks architecture.

[@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (558 likes) from Anthropic shared: "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." - a hint at where the agentic/multi-agent framing is headed internally.

**Sources:** X, HN

---

## Cross-Source Patterns

**Pattern 1: "Write once, run everywhere" is the skills ecosystem's core value proposition**
- X: @Layton_Gott "They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw"
- X: @AntonMartyniuk "Microsoft's 99 .NET skills work across Claude Code, Codex, GitHub Copilot, and Cursor"
- Web: paperclipped.de "32 tools from competing companies all read the same SKILL.md files"
- HN: ZCode harness adapter PR adds Claude-Code-shaped layout compatibility

**Pattern 2: Security anxiety about plugin/skill supply chain is growing**
- X: @JDSalbego "Each MCP server is an attack surface. Most devs don't know which ones their tools installed as dependencies"
- HN: steganography story (2,432 pts, 742 cmt) - community scrutinizing Claude Code's harness behavior
- Web: Snyk ToxicSkills study (36% of skills have security flaws, 76 confirmed malicious payloads)
- HN: "Anthropic embedded spyware" thread (56 pts)

**Pattern 3: Memory fragmentation across tools is the unresolved UX failure**
- Bluesky: LoreConvo "every tool walls off your memory by machine"
- HN: Recall - local project memory for Claude Code (137 pts, 85 cmt)
- X: @stretchcloud on LangChain's OpenWiki solving the codebase-context grounding problem
- Bluesky: @noah.exposed "Claude 4.8 forgets things the moment it gets distracted. If anything, it does a decent job of emulating someone with ADHD"

**Pattern 4: MCP infrastructure is being adopted at the platform layer, not just the developer tool layer**
- X: @Tork_Lab - X Platform now supports hosted MCP servers
- Web: Microsoft Windows On-device Agent Registry (ODR) uses MCP
- Web: Anthropic donated MCP to Agentic AI Foundation; adopted by OpenAI Agents SDK, Cursor, Cloudflare Agents
- Web: MCP Spec Release Candidate with v0.1 API freeze and .well-known discovery standard

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I started responding to messages from coworkers like Claude | 15,119 | 326 | "I will update the group as it goes" | https://www.reddit.com/r/ClaudeAI/comments/1tz1tzv/ |
| r/ClaudeAI | Claude Fable 5 feels less like a model launch and more like a preview of AI inequality | 5,313 | 903 | "frontier AI is turning into a gated utility" | https://www.reddit.com/r/ClaudeAI/comments/1u1fsdi/ |
| r/ClaudeAI | New Claude code update is crazy | 4,355 | 73 | (link only) | https://www.reddit.com/r/ClaudeAI/comments/1u9hp5y/ |
| r/ClaudeAI | Nothing can go wrong when you share a Claude subscription with friends... right? | 4,184 | 73 | (link only) | https://www.reddit.com/r/ClaudeAI/comments/1uejjg6/ |
| r/ClaudeAI | Any USA citizen wanna marry me? I'm tryna access Fable 5 in Claude Code | 3,020 | 394 | (link only) | https://www.reddit.com/r/ClaudeAI/comments/1u4tjef/ |
| r/ClaudeAI | Hit your Claude session limit? | 2,892 | 132 | "One of the smartest AI hacks I've seen" | https://www.reddit.com/r/ClaudeAI/comments/1ubj3fw/ |
| r/ClaudeAI | Help my claude wont say uwu | 2,316 | 200 | "He keeps saying he has standards. Hes too self aware!!!" | https://www.reddit.com/r/ClaudeAI/comments/1tyhfso/ |
| r/ClaudeAI | CONFIRMED... A NEW CLAUDE PLAN IS COMING SOON | 2,225 | 151 | (link only) | https://www.reddit.com/r/ClaudeAI/comments/1u4x5rp/ |
| r/ClaudeAI | I used Claude to fix my biggest frustration with PDFs | 2,443 | 210 | "what if I could scroll horizontally to see the pages" | https://www.reddit.com/r/ClaudeAI/comments/1ugj1bt/ |
| r/ClaudeAI | Claude Code via Microsoft Foundry - no 5-hour or weekly limits | 1 | 1 | "$200 trial credit, jumps to $2000 for students" | https://www.reddit.com/r/ClaudeAI/comments/1umx917/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @vivoplt | "senior vibe coder: setup agent skills and rules, integrate connectors and mcp servers..." | 588 | 48 | https://x.com/vivoplt/status/2072672502174925123 |
| @AntonMartyniuk | "Microsoft quietly published 99 ready-made .NET skills for AI Agents... work across Claude Code, Codex, GitHub Copilot, and Cursor" | 294 | 56 | https://x.com/AntonMartyniuk/status/2072646509137363103 |
| @vercel | "We are joining @MercedesAMGF1 as a multi-year strategic partner" | 2,057 | 108 | https://x.com/vercel/status/2072311906086551680 |
| @vercel | "Vercel Services gives your full stack app atomic deployment and rollback..." | 720 | 50 | https://x.com/vercel/status/2071951670058324353 |
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 558 | 15 | https://x.com/alexalbert__/status/2069470389391241314 |
| @aiwithjonny | "Claude is offering 18 official AI courses with certificates. 100% free: Introduction to Agent Skills..." | 82 | 24 | https://x.com/aiwithjonny/status/2073039922202919120 |
| @Tork_Lab | "BREAKING: X just made a major move for AI builders. The platform now supports hosted MCP servers" | 44 | 0 | https://x.com/Tork_Lab/status/2073240381802905624 |
| @iam_elias1 | "10 Essential Claude Code Skills to Unlock the Full Potential of Claude Code" | 51 | 20 | https://x.com/iam_elias1/status/2072625945220174062 |
| @KhushiPatil25 | "Introduction to Agent Skills Build, configure, and share Skills in Claude Code" | 55 | 15 | https://x.com/KhushiPatil25/status/2072921582356578509 |
| @Layton_Gott | "Skills have a HUGE impact in AI coding right now... just a markdown file... works in basically everything" | 6 | 1 | https://x.com/Layton_Gott/status/2073125199030157540 |
| @suraj_sharma14 | "You NEED to: Learn Claude Code + Codex workflows, Set up Hermes Agent, Set up OpenClaw, Master MCP" | 22 | 2 | https://x.com/suraj_sharma14/status/2073300779767603640 |
| @stretchcloud | "OpenCode hit 160,000 GitHub stars... guide structure emerging: agents, skills, plugins, MCP integrations" | 1 | 1 | https://x.com/stretchcloud/status/2072974880963023113 |
| @goon_nguyen | "how do we plug in MCP servers without turning context into soup?" | 1 | 0 | https://x.com/goon_nguyen/status/2073197487880372437 |
| @JDSalbego | "Each MCP server is an attack surface. Most don't know about the ones their tools installed as dependencies" | 1 | 0 | https://x.com/JDSalbego/status/2072682302652485632 |
| @github_update | "Most agent failures are not model failures. They are harness failures." | 6 | 0 | https://x.com/github_update/status/2072200713808281666 |
| @stretchcloud | "LangChain shipped OpenWiki... The bottleneck shifted from writing code to grounding agents in codebase context" | 2 | 0 | https://x.com/stretchcloud/status/2073333494126989346 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kirushik | Claude Code is steganographically marking requests | 2,432 | 742 | High scrutiny of request-tracking behavior | https://thereallo.dev/blog/claude-code-prompt-steganography |
| engmarketer | I used Claude Code to get a second opinion on my MRI | 561 | 706 | Unexpected medical use case going viral | https://antoine.fi/mri-analysis-using-claude-code-opus |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | Authenticity questions on reasoning traces | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| mateenah | Show HN: Recall - Local project memory for Claude Code | 137 | 85 | Community solution to cross-session context loss | https://github.com/raiyanyahya/recall |
| handfuloflight | ZCode: Claude Code from the Makers of GLM | 277 | 15 | GLM team built Claude-Code-shaped coding agent | https://zcode.z.ai/cn |
| emson | Show HN: Claudoro, Pomodoro timer embedded in the Claude Code statusline | 49 | 34 | Community extension creativity | https://github.com/emson/claudoro |
| engmarketer | Claude Code Just Got 5x More Expensive | 57 | 8 | Pricing scrutiny | https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/ |
| ayi | Ask HN: Anthropic banned me from using Claude Code and I don't know what to do | 81 | 94 | Enforcement/policy concerns | https://news.ycombinator.com/item?id=48641160 |
| momoraul | Show HN: Lupen - which Claude Code turn or sub-agent ran up your bill | 3 | 0 | Cost attribution tool for multi-agent workflows | https://github.com/momoraul/Lupen |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @sexabolition.blog | "Claude Code UX really reinvents the Hacker man scrolling source code experience... all the agent frameworks run in JavaScript DOM TUIs" | 27 | https://bsky.app/profile/sexabolition.blog/post/3mpjtnp4azc2k |
| @noah.exposed | "Claude 4.8 forgets things the moment it gets distracted... does a decent job of emulating someone with ADHD" | 21 | https://bsky.app/profile/noah.exposed/post/3mpc2buws4k2x |
| @richholman.com | "/design-sync converts a JS/React design system so the claude.ai/design agent can render it live" | 10 | https://bsky.app/profile/richholman.com/post/3mpl7meypoc2x |
| @gigazine.net | "Comfy MCP: ComfyUI image/video generation automation for Claude Code agents via Comfy Cloud" | 7 | https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22 |
| @wenchangyue.bsky.social | "5 working days of AI coding (Claude Code + Codex agent) = ~1 billion tokens, about $1,400 at API list price" | 3 | https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i |
| @dennisdoomen.com | "3-5 agent sessions running in parallel in JetBrains Junie, Claude Code and GitHub Copilot" | 2 | https://bsky.app/profile/dennisdoomen.com/post/3mp6bc7s7yk2x |
| @labyrinthanalyticsconsulting.com | "Every tool walls off your memory by machine. LoreConvo follows you across Claude Code, Codex, Cursor, and Hermes Agent" | 1 | https://bsky.app/profile/labyrinthanalyticsconsulting.com/post/3mpnkwhlgax2p |
| @hackmd.io | "your agents need more than prompts - they need skills. markdown is becoming agent infrastructure" | 1 | https://bsky.app/profile/hackmd.io/post/3mpgqxdcz5k2b |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| hashgraph-online/hol-guard | feat(guard): add z.ai ZCode harness adapter | 3 | 2 | https://github.com/hashgraph-online/hol-guard/pull/924 |
| ThePlenkov/gascity.ts | fix(console): address code-review findings; marketplace UI + registry-backed Marketplace | 0 | 11 | https://github.com/ThePlenkov/gascity.ts/pull/8 |
| Kilo-Org/kilocode | feat(jetbrains): add Agent Behavior settings with Agents + MCP Servers child pages | 2 | 2 | https://github.com/Kilo-Org/kilocode/pull/11553 |
| esengine/DeepSeek-Reasonix | [Bug]: Skill system enhancement - support nested directories / plugin market / hooks integration | 3 | 4 | https://github.com/esengine/DeepSeek-Reasonix/issues/3955 |
| hashgraph-online/awesome-codex-plugins | Restore ArmorCodex entry in Community Plugins | 0 | 5 | https://github.com/hashgraph-online/awesome-codex-plugins/pull/189 |
| momoraul/Lupen | Show HN: Lupen - which Claude Code turn or sub-agent ran up your bill | 0 | 0 | https://github.com/momoraul/Lupen |
| app-vitals/shipwright | Shipwright Harness - open-source autonomous delivery agent for Claude Code (MIT) | 0 | 0 | https://github.com/app-vitals/shipwright |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | https://claudemarketplaces.com/ | Community directory: 21,600+ skills, 2,500+ marketplaces, 12,500+ MCP servers as of 2026 |
| morphllm.com | https://www.morphllm.com/claude-code-marketplace | Plugin = slash commands + subagents + hooks + MCP servers bundled; /plugin marketplace add command |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Architecture guide: skills → plugins → MCP servers nesting hierarchy |
| arte.itlibra.com | https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace | 22-min comprehensive plugin marketplace guide (June 20, 2026) |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills teach Claude how; connectors expose data; MCP provides live connections; plugins bundle all |
| arsentev.ai | https://arsentev.ai/guides/plugins-marketplace | "App Store in Your Terminal" - what to install first, safety guide |
| openagentskill.com | https://www.openagentskill.com/skills/majiayu000-claude-skill-registry | Claude Skill Registry: 413 stars, quality score 83/100 |
| totalum.app | https://www.totalum.app/blog/agent-skills-marketplaces-2026 | Marketplace explosion: 1 registry Dec 2025 → 8 major platforms Q2 2026; Snyk ToxicSkills data |
| techinformed.com | https://techinformed.com/how-vercel-built-an-ai-agent-ecosystem-on-claudes-open-skills-standard/ | Vercel skills.sh GA launch June 5, 2026: 600,000 OSS skills via OIDC |
| agentman.ai | https://agentman.ai/blog/agent-skills-ecosystem-report-2026 | Agent skills ecosystem landscape report 2026 |
| dev.to | https://dev.to/nathanielc85523/skillmd-goes-multi-ecosystem-how-the-agent-skills-standard-jumped-from-anthropic-to-openai-and-3oeg | SKILL.md adoption timeline across 32+ tools after open standard launch |
| anthropic.com | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Official Anthropic engineering blog on Agent Skills |
| thenewstack.io | https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/ | "Agent Skills: Anthropic's Next Bid to Define AI Standards" |
| registry.modelcontextprotocol.io | https://registry.modelcontextprotocol.io/ | Official MCP Registry: ~2,000 entries (Sep 2025 launch); 19,831 on Glama by March 2026 |
| blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | MCP Spec Release Candidate: v0.1 API freeze + MCP Server Cards (.well-known) standard |
| workos.com | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | MCP donated to Agentic AI Foundation; adopted by OpenAI Agents SDK, Cloudflare, Microsoft |
| paperclipped.de | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | 32 tools from competing companies now read same SKILL.md files; 48-hour standard adoption |
| github.com/jeremylongshore | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; ccpi CLI package manager |
| github.com/anthropics | https://github.com/anthropics/claude-plugins-official | Official Anthropic-managed plugin directory; stable since Oct 2025 public beta |

---

## Stats Block

```
├─ 🟠 Reddit: 15 threads │ 44,648 upvotes │ 2,507 comments
├─ 🔵 X: 21 posts │ 5,612 likes │ 382 reposts
├─ 🟢 HN: 15 stories │ 4,045 points │ 1,994 comments
├─ 🦋 Bluesky: 12 posts │ 81 likes │ 1 repost
├─ 🐙 GitHub: 13 items │ 44 reactions │ 120 comments
├─ 🌐 Web: 19 pages
└─ 🗣️ Top voices: @vivoplt, @AntonMartyniuk, @alexalbert__, @stretchcloud │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube:** 0 results returned despite multiple query attempts. ScrapeCreators returned HTTP 402 (payment required). No YouTube coverage of this topic in the research window.
- **TikTok:** 0 results. All hashtag searches returned HTTP 402. No TikTok coverage captured.
- **Instagram:** 0 results. ScrapeCreators 402 errors. No Instagram coverage captured.
- **Polymarket:** 0 relevant markets found for this topic.
- **Reddit relevance:** The engine flagged "top evidence is highly concentrated in one source." Most high-upvote Reddit threads (r/ClaudeAI) were about Claude model features, pricing, and subscription limits - not specifically about plugin/skill ecosystems. On-topic Reddit signal was lighter than the upvote numbers suggest.
- **X signal concentration:** The @vivoplt "senior vs junior vibe coder" post (588 likes) dramatically outperformed all other X posts; most ecosystem-specific X posts had <10 likes, suggesting ecosystem discourse is either on Discord/Slack or not yet viral at scale.
- **Bluesky:** Substantive English-language coverage limited; several posts were in Japanese (Comfy MCP, Claude Code security VM setup), suggesting international developer interest in the ecosystem.
- **Coverage estimate:** ~65-70% of publicly visible activity on topic captured. Missing: Discord communities (likely highest-signal venue for plugin developers), Slack workspaces, private marketplaces, and paid forum discussions.

---

## Key Quotes

> "senior vibe coder: setup personal preferences and agent memory, setup agent skills and rules, integrate connectors and MCP servers, test agent out, thinks about what to build" - [@vivoplt](https://x.com/vivoplt/status/2072672502174925123) on X

> "Skills have a HUGE impact in AI coding right now... A skill is just a markdown file with a dialed in prompt essentially. They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw." - [@Layton_Gott](https://x.com/Layton_Gott/status/2073125199030157540) on X

> "how do we plug in MCP servers without turning context into soup? how do we trace the callback that failed?" - [@goon_nguyen](https://x.com/goon_nguyen/status/2073197487880372437) on X

> "Most developers have 3-5 MCP servers they installed intentionally. Most don't know about the ones their tools installed as dependencies. Each one is an attack surface." - [@JDSalbego](https://x.com/JDSalbego/status/2072682302652485632) on X

> "The bottleneck shifted from writing code to grounding agents in codebase context." - [@stretchcloud](https://x.com/stretchcloud/status/2073333494126989346) on X

> "Most agent failures are not model failures. They are harness failures." - [@github_update](https://x.com/github_update/status/2072200713808281666) on X

> "your agents need more than prompts - they need skills. markdown is becoming agent infrastructure" - [@hackmd.io](https://bsky.app/profile/hackmd.io/post/3mpgqxdcz5k2b) on Bluesky

> "Every tool walls off your memory by machine. LoreConvo follows you across Claude Code, Codex, Cursor, and Hermes Agent - the same context, everywhere you work." - [@labyrinthanalyticsconsulting.com](https://bsky.app/profile/labyrinthanalyticsconsulting.com/post/3mpnkwhlgax2p) on Bluesky

> "Microsoft quietly published 99 ready-made .NET skills for AI Agents. Most .NET developers have no idea they exist." - [@AntonMartyniuk](https://x.com/AntonMartyniuk/status/2072646509137363103) on X

> "One of my favourite things about Claude Code is that the user experience really reinvents the Hacker man scrolling source code experience for people who imagine that's what technical work entails." - [@sexabolition.blog](https://bsky.app/profile/sexabolition.blog/post/3mpjtnp4azc2k) on Bluesky
