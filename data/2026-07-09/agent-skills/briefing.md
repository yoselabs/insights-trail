# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-09
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 11 threads | 358 upvotes, 380 comments | r/ClaudeWorkflows, r/UXDesign, r/claudeskills, r/ClaudeAI |
| X/Twitter | 19 posts | 532 likes, 153 reposts | Heavy ecosystem curation threads |
| Hacker News | 22 stories | 267 points, 97 comments | 12+ Show HN submissions for new tools |
| Bluesky | 5 posts | 5 likes, 1 repost | Feature announcements, plugin links |
| GitHub | 38 items | 904 reactions, 1,583 comments | anthropics/claude-code issues, community repos |
| Web | 15 pages + 13 supplements | — | Guides, registries, governance docs |
| YouTube | 0 videos | — | yt-dlp rate-limited; SC quota exceeded |
| TikTok | 0 videos | — | SC quota exceeded (HTTP 402) |
| Instagram | 0 reels | — | SC quota exceeded (HTTP 402) |

---

## Synthesized Findings

### 1. The Claude Code Plugin System Is Now a Mature Ecosystem

Claude Code's plugin architecture - launched in public beta October 2025 - has stabilized into a clear three-layer stack that practitioners are actively documenting. The key distinction the community keeps returning to: **a skill changes how Claude thinks, a subagent protects your context window, and an MCP server connects Claude to a system it cannot otherwise reach**. Per [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/), these solve three different problems, not one.

Plugins bundle all three into a single installable unit. By March 2026 Anthropic's official marketplace had 101 plugins: 33 built by Anthropic covering language servers, dev workflow, output styles, and setup, plus 68 partner plugins from GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase. The [official Claude Code docs](https://code.claude.com/docs/en/discover-plugins) now have a dedicated plugin discovery section. [UX Planet's July 2026 guide](https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda) identifies four primary plugin use cases: code review, frontend coder, release/QA automation, and team onboarding.

A [new `/checkup` command](https://bsky.app/profile/bcherny-mirr.selfhosted.social/post/7xymz2mw27w22) landed this week, per [@bcherny-mirr.selfhosted.social](https://bsky.app/profile/bcherny-mirr.selfhosted.social/post/7xymz2mw27w22) on Bluesky: "Clean up unused skills/MCPs/plugins and save context. Dedup your local CLAUDE.md against the checked in CLAUDE.md. Break up root CLAUDE.md into nested CLAUDE.md's + skills." Context bloat from loading too many skills is a real operational concern - 50 skills can consume 5,000 tokens in descriptions alone, 10 MCP servers another 10,000.

### 2. The Marketplace Explosion: From 1 Registry to 8+ in Six Months

The agent-tools distribution layer went from one registry in December 2025 to at least eight major marketplaces by Q2 2026. Scale as reported across community sources:

- [Skillselion](https://skillselion.com/state-of-ai-agent-skills-2026) tracks **87,810 AI coding-agent tools** (66,910 skills, 8,251 MCP servers, 10,264 marketplaces) with 130M combined installs
- [claudemarketplaces.com](https://claudemarketplaces.com/) reports 21,700+ skills, 12,500+ MCP servers, 300,000+ monthly developer visits
- [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) on GitHub: 337 skills, 30+ agents, 70+ custom commands, cross-compatible with Claude Code, Codex, Gemini CLI, Cursor, and 8 more agents - trending on GitHub per [@github_update](https://x.com/github_update/status/2074176588195721395)
- [ClaudeSkills.info](https://claudeskills.info) offers 658+ free skills including official Anthropic PDF, DOCX, XLSX, and MCP builder skills

The key new infrastructure is [Skills.sh](https://skills.sh), described as the "npm-style package manager for agent skills" - Vercel-backed, one-command CLI install that works across Claude Code, Codex CLI, Cursor, and OpenClaw. It also appeared in GitHub Trending as `vercel-labs/skills` per [@github_update](https://x.com/github_update/status/2073814176384921902).

[@Jeffar_AI](https://x.com/Jeffar_AI/status/2074868083731378327) (98 likes, 60 reposts) captured the moment: "Most people only use Claude Code to write code. They're missing the entire ecosystem. 54 powerful resources covering: MCP servers, AI agents, Skills, Automation, Multiplexers, Frameworks, Official docs."

### 3. MCP Registry Maturity: From Chaos to Governed Catalogs

The MCP server ecosystem has hit a governance inflection. Four major public registries now compete for developer mindshare, each with distinct positioning:

- **[Glama](https://glama.ai/mcp/servers)** - ~53,151 indexed servers, tiered "Official" (publisher-verified) vs "Claimed"; 6,000+ hosted connectors, 1M+ tool calls/month
- **[Smithery](https://smithery.ai)** - 7,000+ servers, positioned as the "Docker Hub of MCP" with CLI install or cloud-hosted remote options
- **[mcp.so](https://mcp.so)** - 19,700+ community-submitted servers, broad coverage
- **[ToolHive (Stacklok)](https://docs.stacklok.com/toolhive/guides-cli/registry)** - Enterprise-grade: verified configurations, Kubernetes/Git/API aggregation, access control

Security scrutiny arrived in parallel. Two separate HN submissions this month audited MCP servers in isolated environments: ["I ran 70 MCP servers in a sandbox and logged what they do"](https://github.com/BhaveshThapar/mcp-audit) (6pts) and ["We ran 74 popular MCP servers in microVMs to see what breaks"](https://usethrone.dev/registry) (3pts). ["A readiness scorer for MCP servers, checked against emerging standards"](https://isyourmcpready.com) appeared on HN (4pts). ["Diplomat-agent: scan Python MCP servers for unguarded tool calls"](https://github.com/Diplomat-ai/diplomat-agent) got 3pts. The pattern is clear: as MCP installs proliferate, developers are building their own quality gates.

Google Cloud's [Agent Registry](https://docs.cloud.google.com/agent-registry/register-mcp-servers) launched with automatic discovery of Google-managed MCP servers and a unified directory. [AWS published a governance blueprint](https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/) for centralizing approved MCP server lists. [JFrog called agent plugins "executable software"](https://jfrog.com/blog/introducing-agent-plugins-repositories/) arriving via uncontrolled distribution channels and introduced enterprise repository management for them.

[@mohankr47011106](https://x.com/mohankr47011106/status/2074868777058226564) on X captured the practitioner learning curve: "New Learnings - Building MCP Servers - Testing Authorization flow of the mcp server with local keycloak authorization server - testing tools with scopes and RBAC - connecting mcp servers with custom agent, claude desktop, vs code."

### 4. Cross-Agent Skill Standards Emerging

Skills are no longer Claude Code-exclusive. The [agentskills.io](https://agentskills.io) standard - adopted by 40+ products including Claude Code, Codex CLI, Hermes Agent, and OpenClaw - is making skills portable across the agent ecosystem. The [alirezarezvani/claude-skills](https://bsky.app/profile/techyonai.bsky.social/post/3mpv5xt4zzq2p) repo explicitly targets "8 more coding agents" beyond the main four.

Hermes Agent (Nous Research) implements the SKILL.md format; [@zeuuss_01](https://x.com/zeuuss_01/status/2067432401005912575) (179 likes) described how five community skills from the ecosystem turn it into "a self-running powerhouse" - including the ANTHROPIC-CYBERSECURITY-SKILLS pack with 4K stars and 753+ cybersecurity skills mapped to MITRE ATT&CK.

[Tessl.io/registry](https://tessl.io/registry) runs a public task registry used for AI coding-agent benchmarking. A [r/ClaudeAI thread](https://www.reddit.com/r/ClaudeAI/comments/1u3vyk7/tested_claude_fable_5_and_opus_48_across_917/) (103pts, 94 comments) reported Fable 5 vs Opus 4.8 tested across 917 coding-agent scenarios from the Tessl registry, evaluated both with and without relevant skills loaded - finding skills meaningfully affected scores.

[agent-shell](https://x.com/DanKornas/status/2074981587155038216) is a new Emacs-native integration for ACP (Agent Client Protocol) that works with Gemini CLI, Claude Agent, Codex, Goose, Cursor, Qwen Code, Auggie, and Mistral Vibe - another cross-agent protocol gaining traction alongside MCP.

### 5. Autonomous Skill Discovery: The Bhived MCP Pattern

The most technically interesting new workflow pattern in r/ClaudeWorkflows: using MCP servers for autonomous skill discovery itself. Two related threads ([bhived MCP workflow 1](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/), [bhived MCP workflow 2](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2j9/workflow_enhance_claude_code_agents_with_shared/)) describe how the `bhived` MCP enables shared memory across agent instances so they stop "repeatedly starting from scratch." Rated workflow value 85/100. Similarly, [archex MCP](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/) targets token efficiency for context retrieval.

[Rondoflow](https://github.com/rondoflow/rondoflow) (Show HN, 3pts) adds visual multi-agent orchestration for Claude Code. [Shipwright Harness](https://github.com/app-vitals/shipwright) (Show HN, 3pts) is an open-source autonomous delivery agent for Claude Code. The skill-as-memory and skill-as-workflow patterns are pushing toward fully autonomous agent pipelines.

### 6. Community Skepticism: "The Wrapper Doesn't Matter"

Not all discourse is bullish. The highest-signal community critique came from [r/claudeskills](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) (100pts, 65 comments): "90% claude code tutorials are waste of time. They all work the same under the hood. The wrapper doesn't matter. The MCP i[nstall pattern is the same everywhere]." The author ran "pretty much every agentic IDE and harness out there - Cursor, Claude Code, Codex" and concluded the abstractions are converging.

This maps to a GitHub issue on ghidra-mcp titled ["this is becoming a complex unmaintainable mess"](https://github.com/bethington/ghidra-mcp/issues/307) (11 reactions): "too many tools for agents" - the ghidra-mcp MCP project has too many exposed tools confusing the agent, echoing a real cognitive-load problem with MCP proliferation.

A Claude Code engineer's talk surfaced on X via [@Adea0x](https://x.com/Adea0x/status/2074931950478106789) (40 likes): Daisy Holman from the Claude Code team warned that "repo + shell is not enough. Source code shows what changed. Slack threads, emails, design docs, dashboards and meeting notes explain why it changed." The extension ecosystem helps, but skills/MCPs that don't bridge the full context gap are still leaving agents blind.

### 7. Enterprise Governance Is Professionalizing Plugin Distribution

The enterprise angle is moving fast. [JFrog's "Agent Plugins Repositories"](https://jfrog.com/blog/introducing-agent-plugins-repositories/) frames the current moment starkly: "Your developers install agent plugins every day: pulling from unmanaged GitHub repos, copying Cursor commands out of Slack, pointing Codex at a personal Git fork. Each of those is a new, uncontrolled distribution channel inside your software development lifecycle." JFrog's new Agent Plugins Repositories bring Artifactory-style governance to the plugin distribution layer.

The [Superpowers plugin](https://bsky.app/profile/foursignalsdev.bsky.social/post/3mq5f3wo3r626) on Bluesky enforces spec-first, TDD/YAGNI/DRY patterns across Claude Code, Cursor, and Codex CLI - showing how plugins are becoming the delivery mechanism for engineering practice standards, not just tool integrations.

[TS Compiler Graph MCP](https://github.com/samchon/ttsc/tree/master/packages/graph) (Show HN, 3pts) demonstrated a concrete efficiency gain: 10x fewer tokens in Claude Code and Codex by giving the agent a compiler-graph view of TypeScript projects rather than raw file dumps.

---

## Cross-Source Patterns

**Pattern 1: "Most people don't know the full stack"**
Appeared on: X (multiple high-engagement posts), Reddit, Web
The dominant X narrative this week is awareness-gap framing: 54+ resources exist, most users only use Claude Code for raw coding. [@Jeffar_AI](https://x.com/Jeffar_AI/status/2074868083731378327) (98 likes): "Most people only use Claude Code to write code. They're missing the entire ecosystem." Nearly identical posts from [@smratitiwa86867](https://x.com/smratitiwa86867/status/2075122665556521239) and [@tom_brando82808](https://x.com/tom_brando82808/status/2074899972907261967) suggest coordinated or viral sharing of the same resource hub.

**Pattern 2: Security audits of MCP servers**
Appeared on: Hacker News (4 separate submissions), Web
Two sandbox runs, a readiness scorer, and a security scanner all launched this month. The HN community is building MCP-specific security tooling rapidly as server counts scale past 50,000.

**Pattern 3: Context/token cost of the ecosystem**
Appeared on: Reddit, Hacker News, Bluesky (via /checkup), Web
Multiple threads converge on the same problem: loading too many skills and MCP servers inflates context costs severely. The new /checkup command directly addresses this. The r/claudeskills "tutorials are waste of time" thread is partly a reaction to this complexity.

**Pattern 4: Cross-agent portability**
Appeared on: X, Web, Bluesky, GitHub
Skills are no longer Claude Code-specific. The alirezarezvani/claude-skills repo, the agentskills.io standard, and multiple marketplace guides all position skills as cross-agent artifacts. Claude Code, Codex, Cursor, Hermes, OpenClaw are converging on similar formats.

**Pattern 5: Enterprise governance entering the space**
Appeared on: Web (AWS, Google, JFrog), Hacker News
Three enterprise vendors (AWS, Google Cloud, JFrog) published MCP/plugin governance guidance within the past 30 days. ToolHive (Stacklok) provides the open-source layer. This represents institutional acknowledgment that agent plugins are production infrastructure.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/UXDesign | Claude Code Has Access to My Design System, Yet the UI Output Is Still Terrible | 117 | 170 | "I've designed a full design system, connected the Figma MCP..." | https://www.reddit.com/r/UXDesign/comments/1uct2dx/ |
| r/claudeskills | 90% claude code tutorials are waste of time | 100 | 65 | "They all work the same under the hood. The wrapper doesn't matter." | https://www.reddit.com/r/claudeskills/comments/1u610hm/ |
| r/ClaudeAI | tested Claude Fable 5 and Opus 4.8 across 917 coding-agent scenarios | 103 | 94 | "Tasks came from skills in tessl.io/registry, evaluated with and without relevant skill loaded" | https://www.reddit.com/r/ClaudeAI/comments/1u3vyk7/ |
| r/ClaudeWorkflows | [Workflow] Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP | 1 | — | "Agents repeatedly start from scratch. Bhived solves shared memory across instances." | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/ |
| r/ClaudeWorkflows | [Workflow] Improve Claude Code Agent Token Efficiency with archex MCP | 1 | — | "Inefficient and token-hungry code context retrieval" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/ |
| r/softwaredevelopment | What's one developer tool that saves you hours every month? | — | — | Thread collecting tool recommendations from practitioners | https://www.reddit.com/r/softwaredevelopment/comments/1uqsbdk/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @Jeffar_AI | "Most people only use Claude Code to write code. They're missing the entire ecosystem. 54 powerful resources..." | 98 | 60 | https://x.com/Jeffar_AI/status/2074868083731378327 |
| @zeuuss_01 | "THESE 5 SKILLS TURN HERMES AGENT INTO A SELF-RUNNING POWERHOUSE" | 179 | 17 | https://x.com/zeuuss_01/status/2067432401005912575 |
| @tom_brando82808 | "Most people use Claude Code just to write code. They're missing the bigger picture. Master: MCP Servers, AI Agents, Skills..." | 49 | 33 | https://x.com/tom_brando82808/status/2074899972907261967 |
| @Adea0x | "A CLAUDE CODE ENGINEER SAID YOUR JOB NOW IS TO MAKE 'LITTLE CLONES OF YOURSELF'" | 40 | 5 | https://x.com/Adea0x/status/2074931950478106789 |
| @aibullss | "I Built an AI System With Claude Code + TradingView MCP That Makes $1,652/Day" | 36 | 22 | https://x.com/aibullss/status/2074857753286480230 |
| @smratitiwa86867 | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills." | 9 | 4 | https://x.com/smratitiwa86867/status/2075122665556521239 |
| @mohankr47011106 | "New Learnings: Building MCP Servers, Testing Authorization flow with keycloak, RBAC" | — | — | https://x.com/mohankr47011106/status/2074868777058226564 |
| @DanKornas | "agent-shell is a native Emacs shell for interacting with LLM agents through ACP" | 7 | 1 | https://x.com/DanKornas/status/2074981587155038216 |
| @github_update | "AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking" | 8 | 2 | https://x.com/github_update/status/2067259115777507386 |
| @github_update | GitHub Trending includes vercel-labs/skills, alirezarezvani/claude-skills | 3 | 1 | https://x.com/github_update/status/2074176588195721395 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kanamekun | The Making of Claude Code | 60 | 30 | Anthropic retrospective on design decisions | https://www.anthropic.com/features/making-of-claude-code |
| iacguy | The Log is the Agent | 113 | 50 | arxiv paper on agent architecture | https://arxiv.org/abs/2605.21997 |
| bthapar | Show HN: I ran 70 MCP servers in a sandbox and logged what they do | 6 | 3 | — | https://github.com/BhaveshThapar/mcp-audit |
| arhamshahrier | Show HN: Tilion – MCP for Claude Code to stop it getting blocked on the web | 5 | — | — | https://github.com/tiliondev/fortress/tree/main/mcp |
| nastynate | Show HN: Statuslin.es – community library of custom Claude Code status lines | 4 | — | — | https://statuslin.es |
| piotrgrudzien | Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | — | — | https://quickchat.ai/post/expose-ai-agent-as-mcp-server |
| arzzen | Show HN: Visual multi-agent orchestration for Claude Code (rondoflow) | 3 | — | — | https://github.com/rondoflow/rondoflow |
| jguarnelli | Show HN: Diplomat-agent scan Python MCP servers for unguarded tool calls | 3 | — | — | https://github.com/Diplomat-ai/diplomat-agent |
| selcuk | Show HN: Namecom-CLI – CLI and agent skill so Claude Code/Codex can do DNS | 4 | — | — | https://github.com/hypersocialinc/namecom-cli |
| softie123 | Show HN: A police department for your Claude Code agents | 11 | 8 | — | https://github.com/varmabudharaju/agent-pd/blob/master/README.md |
| nrengan | Show HN: A readiness scorer for MCP servers, checked against emerging standards | 4 | 1 | — | https://isyourmcpready.com |
| autobe | Show HN: I Made TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | — | — | https://github.com/samchon/ttsc/tree/master/packages/graph |
| imtaimoorkhan | Show HN: We ran 74 popular MCP servers in microVMs to see what breaks | 3 | — | — | https://usethrone.dev/registry |
| dodizzle | Shipwright Harness – open-source autonomous delivery agent for Claude Code | 3 | — | — | https://github.com/app-vitals/shipwright |
| barakolshe | Claude Code Issue management extension for VS Code | 3 | 1 | — | https://www.forq.ink/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @bcherny-mirr.selfhosted.social | "New in Claude Code: /checkup — Clean up unused skills/MCPs/plugins and save context" | 1 | https://bsky.app/profile/bcherny-mirr.selfhosted.social/post/7xymz2mw27w22 |
| @techyonai.bsky.social | "alirezarezvani/claude-skills: 337 Claude Code skills & agent skills & plugins (30+ Agents, 70+ custom commands, 330+ skills)" | 1 | https://bsky.app/profile/techyonai.bsky.social/post/3mpv5xt4zzq2p |
| @schizanon.bsky.social | "Anybody doing any Unreal Engine development with AI? Are there plugins or do you just open the project folder in Claude Code?" | 2 | https://bsky.app/profile/schizanon.bsky.social/post/3mq3sphilik2v |
| @foursignalsdev.bsky.social | "Superpowers plugin enforces spec-first, TDD/YAGNI/DRY for AI agents. Plugins for Claude Code, Cursor, Codex CLI" | 1 | https://bsky.app/profile/foursignalsdev.bsky.social/post/3mq5f3wo3r626 |
| @roxsross.bsky.social | "Personaliza Claude Code con plugins! https://claude.com/blog/claude-code-plugins" | — | https://bsky.app/profile/roxsross.bsky.social/post/3mpxkq4rct62e |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| UX Planet | https://uxplanet.org/claude-code-plugins-practical-guide-ff6343c3cbda | Plugin anatomy: Skills + Agents + Hooks + MCP servers; 4 use cases |
| Start Debugging | https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/ | Decision framework: skill vs subagent vs MCP (three different problems) |
| DesignRevision | https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents | Skills vs Plugins vs Agents vs MCP comparison guide |
| MCSA Guru | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | The nesting layers explained: plugins contain skills and MCPs |
| Google Cloud Docs | https://docs.cloud.google.com/agent-registry/register-mcp-servers | Agent Registry: register and auto-discover MCP servers |
| Google Cloud Docs | https://docs.cloud.google.com/agent-registry/manage-mcp-tools | Manage MCP tools in Agent Registry |
| Stacklok Docs | https://docs.stacklok.com/toolhive/guides-cli/registry | ToolHive registry for enterprise MCP governance |
| Stacklok Docs | https://docs.stacklok.com/toolhive/guides-registry/ | ToolHive Registry Server for team catalog governance |
| ClaudeFa.st | https://claudefa.st/blog/guide/development/dynamic-workflows | Dynamic Workflows guide; Claude Fast Code Kit 5.5 |
| ClaudeFa.st | https://claudefa.st/blog/guide/agents/custom-agents | Custom commands and agent-building for Claude Code |
| Tygart Media | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills vs MCP vs Connectors vs Plugins taxonomy |
| JFrog | https://jfrog.com/blog/introducing-agent-plugins-repositories/ | Enterprise plugin governance; plugins as "executable software" |
| AWS Open Source Blog | https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/ | MCP Gateway and Registry governance blueprint for enterprises |
| Skywork.ai | https://skywork.ai/blog/ai-bot/clawhub-skill-marketplace-ultimate-guide/ | ClawhHub skill marketplace guide for workflow automation |
| Skillselion | https://skillselion.com/state-of-ai-agent-skills-2026 | State of AI Agent Skills 2026: 87,810 tools, 130M installs |
| claudemarketplaces.com | https://claudemarketplaces.com/ | Directory: 21,700+ skills, 12,500+ MCP servers |
| Agensi | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | All major skill marketplaces compared; Skills.sh, ClaudeSkills.info, Agensi |
| Glama | https://glama.ai/mcp/servers | ~53,151 open-source MCP servers indexed |
| TrueFoundry | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries 2026: Glama, Smithery, mcp.so, ToolHive |
| Build to Launch | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | Practical review: 11 plugins tested, 4 worth keeping |

---

## Stats Block

```
├─ 🟠 Reddit: 11 threads │ 358 upvotes │ 380 comments
├─ 🔵 X: 19 posts │ 532 likes │ 153 reposts
├─ 🟡 HN: 22 stories │ 267 points │ 97 comments
├─ 🦋 Bluesky: 5 posts │ 5 likes │ 1 repost
├─ 🐙 GitHub: 38 items │ 904 reactions │ 1,583 comments
├─ 🌐 Web: 28 pages (15 engine + 13 supplements)
└─ 🗣️ Top voices: @Jeffar_AI, @zeuuss_01, @github_update │ r/claudeskills, r/ClaudeWorkflows, r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 videos** — yt-dlp was rate-limited and ScrapeCreators returned HTTP 402 (quota exceeded). This is a meaningful gap: the Claude Code skill/MCP ecosystem has active tutorial YouTube channels that would have enriched this report.
- **TikTok: 0 videos** — ScrapeCreators HTTP 402 for all hashtags (#claudecode, #mcpserver, #aiagent, #aicoding, #claudeai).
- **Instagram: 0 reels** — Same SC quota issue.
- **Reddit tier 1 (RSS) returned 0 for some queries** — ScrapeCreators backup also failed (HTTP 402). The 11 Reddit threads came via arctic-shift backfill and RSS fallbacks; deeper community discussions in r/ClaudeAI and r/LocalLLaMA may be underrepresented.
- **Engine warning: "Top evidence is highly concentrated in one source"** — X posts dominated the ranked clusters; Reddit and HN items fell below the relevance floor during ranking despite containing strong signal (r/claudeskills "tutorials are waste of time" thread, HN MCP security submissions).
- **Coverage note**: 41 of 110 dated items are from the last 7 days; the 30-day window captures the ecosystem as of early June 2026 forward but misses pre-June announcements (e.g., October 2025 plugin beta launch context).
- **Approximate coverage**: Reddit ~70%, X ~80%, HN ~85%, Bluesky ~60%, Web ~75%. TikTok/YouTube/Instagram: 0%.

---

## Key Quotes

> "Most people only use Claude Code to write code. They're missing the entire ecosystem. 54 powerful resources covering: MCP servers, AI agents, Skills, Automation, Multiplexers, Frameworks, Official docs." — [@Jeffar_AI](https://x.com/Jeffar_AI/status/2074868083731378327) on X (98 likes)

> "New in Claude Code: /checkup — Run /checkup to: 1. Clean up unused skills/MCPs/plugins and save context 2. Dedup your local CLAUDE.md against the checked in CLAUDE.md 3. Break up root CLAUDE.md into nested CLAUDE.md's + skills" — [@bcherny-mirr.selfhosted.social](https://bsky.app/profile/bcherny-mirr.selfhosted.social/post/7xymz2mw27w22) on Bluesky

> "They all work the same under the hood. The wrapper doesn't matter. The MCP install pattern is the same everywhere." — [r/claudeskills](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) (100 upvotes, 65 comments)

> "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." — [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/)

> "THESE 5 SKILLS TURN HERMES AGENT INTO A SELF-RUNNING POWERHOUSE. Hermes already writes its own skills and remembers across sessions. These 5 from the community ecosystem push it further — drop them in ~/.hermes/skills/ and go." — [@zeuuss_01](https://x.com/zeuuss_01/status/2067432401005912575) on X (179 likes)

> "Your developers install agent plugins every day: pulling from unmanaged GitHub repos, copying Cursor commands out of Slack, pointing Codex at a personal Git fork. Each of those is a new, uncontrolled distribution channel inside your software development lifecycle." — [JFrog Agent Plugins Repositories](https://jfrog.com/blog/introducing-agent-plugins-repositories/)

> "New Learnings: Building MCP Servers, Testing Authorization flow of the mcp server with local keycloak authorization server, testing tools with scopes and RBAC, connecting mcp servers with custom agent, claude desktop, vs code." — [@mohankr47011106](https://x.com/mohankr47011106/status/2074868777058226564) on X

> "Repo + shell is not enough. Source code shows what changed. Slack threads, emails, design docs, dashboards and meeting notes explain why it changed." — Daisy Holman (Claude Code team), reported via [@Adea0x](https://x.com/Adea0x/status/2074931950478106789) on X (40 likes)

> "this is becoming a complex unmaintainable mess... too many tools for agents" — [ghidra-mcp GitHub issue #307](https://github.com/bethington/ghidra-mcp/issues/307) on MCP tool proliferation

> "As of 2026, the Skillselion catalog tracks 87,810 AI coding-agent tools — 66,910 agent skills, 8,251 MCP servers and 10,264 marketplaces — with 130M combined installs." — [Skillselion State of AI Agent Skills 2026](https://skillselion.com/state-of-ai-agent-skills-2026)
