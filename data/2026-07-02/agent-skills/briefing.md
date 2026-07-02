# Agent Skills & MCP Ecosystem — Daily Briefing
**Date:** 2026-07-02
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Reddit, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| X/Twitter | 25 posts | 160,596 likes, 22,908 reposts | Top voices: @AnthropicAI, @claudeai, @chenzeling4 |
| Hacker News | 28 stories | 2,895 points, 843 comments | Dense Show HN activity on MCP tooling |
| Reddit | 5 threads | 206 upvotes, 159 comments | r/ClaudeWorkflows, r/claudeskills, r/ClaudeAI |
| Bluesky | 12 posts | 92 likes, 3 reposts | International discussion inc. Japanese content |
| GitHub | 9 items | 25 reactions, 87 comments | PRs across LibreChat, orpc, hol-guard, manaflow |
| Web | 18 pages | — | via WebSearch + grounding |

---

## Synthesized Findings

### 1. Anthropic Shipped an Official Plugin Directory

The biggest structural news this month: Anthropic launched [claude-plugins-official](https://github.com/anthropics/claude-plugins-official), a curated, Anthropic-managed GitHub repo that serves as the canonical plugin marketplace for Claude Code. [@chenzeling4](https://x.com/chenzeling4/status/2071051965057094088) broke it down on June 28: "Internal and external plugins, install with one slash command. Each one bundles skills, agents, MCP servers, or slash commands. The 'trust the source' version of extensibility. 31.2K stars." The plugin directory runs alongside a community marketplace (`claude-community`) where third-party submissions land after a quality review.

[@artyomx](https://x.com/artyomx/status/2065925946717168096) did a careful code audit on June 13 and pushed back on some of the hype: "What's TRUE: the marketplace is real and official → anthropics/claude-plugins-official. What's FALSE: 'sets everything up step-by-step for you' - this is the lie. The skill is explicitly, in-bold, read-only. Under the hood it's literally one SKILL.md + 5 reference markdown files." Real, but leaner than the viral threads suggested. The community noted at [lagrowthmachine.com](https://lagrowthmachine.com/claude-plugins-marketplace/) that the key mental model is: "a plugin bundles slash commands, subagents, MCP servers, hooks and skills, so you add a whole capability at once."

Anthropic also published the official blog post ["Steering Claude Code: CLAUDE.md files, skills, hooks, rules, subagents and more"](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) on June 18 and a companion post ["A harness for every task: dynamic workflows in Claude Code"](https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code) on June 2, documenting how Claude Code can now write and orchestrate its own multi-agent harnesses on the fly.

**Platforms:** X/Twitter, Web, Bluesky

### 2. The Taxonomy Wars: Skills vs. MCP vs. Plugins vs. Connectors

Confusion around the layered extension model is the dominant theme in developer discourse this month. Multiple explainers rushed to fill the gap: [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained), [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/), [morphllm.com](https://www.morphllm.com/claude-code-marketplace), [arte.itlibra.com](https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace), and [jsmanifest.com](https://jsmanifest.com/claude-code-plugin-packaging-guide) all published guides in June. The consensus model:

- **CLAUDE.md** - persistent context Claude reads every session
- **Skills** - reusable named bundles of instructions and scripts, invoked via slash commands, defined by SKILL.md frontmatter
- **MCP servers** - running processes that expose tools and live data to Claude (external databases, APIs, cloud services)
- **Plugins** - the distribution format: bundles one or more skills, subagents, hooks, and MCP server configs into one installable unit
- **Marketplaces** - GitHub repos that catalog plugins; add with `/plugin marketplace add owner/repo`

The r/claudeskills thread ["90% claude code tutorials are waste of time"](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) (100 pts, 65 comments, June 15) captured the frustration: "They all work the same under the hood. The wrapper doesn't matter. The MCP is where the real differentiation is." The thread echoes a growing practitioner consensus that skills/CLAUDE.md are table stakes, and the competitive edge lives in the MCP layer.

**Platforms:** Reddit, Web, X/Twitter

### 3. MCP as "The Real Unlock" - Enterprise and Cloud Adoption

[@CripdoeCrypto](https://x.com/CripdoeCrypto/status/2070217687247225271) on June 25, describing $15k+ spent and 2k+ hours building: "but the real unlock is the MCP layer. two servers. 42 tools. your AI agent gets the whole stack as native capabilities - no API key, no signup, no auth. paste one config line and Claude/Cursor/Windsurf can validate your startup, score your wallet, audit your code, scan DeFi bounties." This characterization - MCP as the capability multiplier that collapses all external tool integration - is a recurring pattern.

Major platforms shipped official MCP servers in June: AWS released a toolkit providing MCP servers and plugins for CDK, Lambda, and cloud tasks compatible with Claude Code, Codex, Cursor, and Kiro ([per @N0V4Dev](https://x.com/N0V4Dev/status/2070816988423700702)). Unreal Engine 5.8 added an MCP server for AI agents (HN: [unrealengine.com/news](https://www.unrealengine.com/news/unreal-engine-5-8-is-now-available)). Safari shipped [an MCP server for web developers](https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/) (HN, July 1). Google Cloud documented the [Agent Registry MCP server](https://docs.cloud.google.com/agent-registry/use-agentregistry-mcp) for dynamic agent discovery.

The MCP ecosystem now counts 16,000+ servers, up from 714 in January 2025, per WorkOS and Microsoft research. The protocol was donated to the Agentic AI Foundation and is now implemented by Anthropic, OpenAI Agents SDK, Cursor, Cloudflare Agents, and Microsoft.

[@SRLsasame](https://x.com/SRLsasame/status/2072545872265543923) captured a best-practice insight: "The MCP filesystem reference server does one thing most builders skip: every tool description names the side effect before an agent calls it. That one line of honesty is a big deal." Also notable: HN's "The SDK Is for Developers. The MCP Server Is for Agents" ([blog.bridgexapi.io](https://blog.bridgexapi.io/the-sdk-is-for-developers-the-mcp-server-is-for-agents)) crystallized a shift in API design philosophy.

**Platforms:** X/Twitter, Hacker News, Web, Bluesky

### 4. Security: The Ecosystem's Biggest Unsolved Problem

The security signal this month is alarming and multi-source. [AgentSeal scanned 1,808 MCP servers and found 66% had security findings](https://agentseal.org/blog/mcp-server-security-findings) - with no correlation between GitHub star count and security quality. [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) on June 13: "NVIDIA just built the security scanner that every developer installing AI agent skills desperately needs. And almost nobody is using it yet. Skills are the new plugins. Claude Code skills. OpenClaw tools. MCP servers. Cursor plugins. Every AI agent framework now has a marketplace of community-built skills you can install with one command. One command. That skill now runs inside your AI agent. With access to everything your agent can access."

[@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) on June 19 put it bluntly: "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?' Developers are adding MCP servers, skills, hooks, plugins, local monitors, marketplace packages, browser access, shell access, and project-specific permissions across multiple harnesses."

Community responses included a wave of new security tooling: [@AsterProinos](https://x.com/AsterProinos/status/2067992519334597089) published [Aster Guard MCP](https://t.co/MKcJ3SuY8n), a lightweight local-first security checker for MCP and Claude Code config files. HN featured [AgentSploit (Burp Suite for AI Agents)](https://github.com/agentsploit/agentsploit), [Diplomat-agent for scanning Python MCP servers](https://github.com/Diplomat-ai/diplomat-agent), and ["A police department for your Claude Code agents"](https://github.com/varmabudharaju/agent-pd/blob/master/README.md) (11 pts, 8 comments).

[@trendai_RSRCH](https://x.com/trendai_RSRCH/status/2072576002509684762) on July 2: "AI agents are only as secure as the MCP servers they connect to. TrendAI Research analyzed 9,695 of them and found no correlation between GitHub star count and security quality. Popular does not mean safe."

The Microsoft Security Blog documented [February 2026 as a crisis moment](https://techcommunity.microsoft.com/blog/microsoft-security-blog/the-state-of-mcp-security-in-2026/4531327): Claude Code RCE through repository config files, 1,184 malicious skills poisoning an agent marketplace, thousands of MCP servers exposed without authentication.

**Platforms:** X/Twitter, Hacker News, Web

### 5. Developer Tooling Explosion: Orchestrators, Debuggers, and Platform Tools

HN's Show HN section was a parade of Claude Code-adjacent tooling in June. Notable entries:

- [Rondoflow](https://github.com/rondoflow/rondoflow) - visual multi-agent orchestration for Claude Code (5 pts, June 25)
- [Boxes.dev](https://boxes.dev) - "ditch localhost; run Claude Code and Codex in the cloud" (105 pts, 79 comments - the month's second-biggest HN discussion in this space)
- [Lupen](https://github.com/momoraul/Lupen) - cost attribution tool: "which Claude Code turn or sub-agent ran up your bill"
- [TS Compiler Graph MCP](https://github.com/samchon/ttsc/tree/master/packages/graph) - "10x fewer tokens in Claude Code and Codex"
- [Shipwright Harness](https://github.com/app-vitals/shipwright) - open-source autonomous delivery agent for Claude Code (MIT)
- [GitOps-style registry for AI agent Workflows, Skills and MCP servers](https://github.com/Friz-zy/ai-capability-registry) (4 pts, June 4)
- [Comfy MCP](https://gigazine.net/news/20260630-comfy-mcp-comfyui-ai-agent/) - image/video generation automation via Claude Code and ComfyUI (Bluesky, 7 likes)
- [CC Switch](https://x.com/chenzeling4/status/2072425045394407787) - desktop manager for Claude Code, Codex, Gemini CLI, OpenCode, OpenClaw, Hermes Agent (111.8K stars)

The [GitHub PR in LibreChat](https://github.com/danny-avila/LibreChat/pull/13831) adding MCP Apps support (34 comments) shows the protocol extending beyond CLI tools - servers can now declare interactive HTML resources that render sandboxed in-chat UIs.

[@richholman.com on Bluesky](https://bsky.app/profile/richholman.com/post/3mpl7meypoc2x) noted a new `/design-sync` command in Claude Code/Design that "converts a JS/React design system so the claude.ai/design agent can render it live" - a cross-product skill bridging code and design agents.

**Platforms:** Hacker News, X/Twitter, Bluesky, GitHub

### 6. Autonomous Skill Discovery and Memory-Based Workflows

r/ClaudeWorkflows posted two highly-rated workflow patterns centered on autonomous skill discovery. The [bhived MCP workflow](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2j9/workflow_enhance_claude_code_agents_with_shared/) (June 16) describes: "Agents repeatedly start from scratch, relying on whatever skills and MCP servers are currently loaded, with no awareness of what skills the agent community has already developed." The proposed solution - shared memory via bhived MCP for skill and knowledge discovery across agent sessions - has a workflow value rating of 85/100.

The [archex MCP server workflow](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/) targets token efficiency with a skill for context retrieval, rating 85/100 for "advanced" practitioners.

The [Tessl registry benchmark](https://www.reddit.com/r/ClaudeAI/comments/1u3vyk7/tested_claude_fable_5_and_opus_48_across_917/) (r/ClaudeAI, 103 pts, 94 comments) tested Claude Fable 5 vs Opus 4.8 across 917 coding-agent scenarios from [tessl.io/registry](https://tessl.io/registry): "We scored them using our task eval framework both with and without the relevant skill loaded." Skills demonstrably affect model performance on task evals.

[HackMD on Bluesky](https://bsky.app/profile/hackmd.io/post/3mpgqxdcz5k2b) on June 29: "your agents need more than prompts - they need skills. The official HackMD Skills repo helps Claude Code, Cursor, Codex, and compatible harnesses sync work logs, publish notes, and turn plans into shareable context. Markdown is becoming agent infrastructure."

**Platforms:** Reddit, Bluesky, X/Twitter

### 7. The Steganography Controversy

The month's most-engaged HN thread (2,387 points, 725 comments) was ["Claude Code is steganographically marking requests"](https://thereallo.dev/blog/claude-code-prompt-steganography) (June 30). @claudeai acknowledged the issue on July 1 with 759 likes: "If one of your requests is mistakenly flagged in Claude Code, run /feedback to file a report." This is directionally relevant to the skill/plugin ecosystem because it touches the trust model of how extensions interact with safety classifiers - a new dimension of concern when installing third-party skills that modify Claude's system prompt or inject context.

**Platforms:** Hacker News, X/Twitter

### 8. ZCode and the Claude Code Clone Ecosystem

[ZCode from the makers of GLM](https://zcode.z.ai/cn) (HN, 274 pts, 13 comments, July 1) is a notable emerging story: a Claude Code-compatible harness built by the Z.ai team, storing config at `~/.zcode/cli/config.json` in a Claude-Code-shaped layout (`mcp.servers`, `plugins.enabledPlugins`, Claude-Code-style `hooks`). The GitHub PR in [hol-guard](https://github.com/hashgraph-online/hol-guard/pull/924) adds a ZCode harness adapter, reflecting that the Claude Code plugin/skill format is becoming a de facto standard that third-party harnesses implement for compatibility.

[@chenzeling4](https://x.com/chenzeling4/status/2072425045394407787) noted CC Switch (111.8K stars) which "puts Claude Code, Codex, Gemini CLI, OpenCode, OpenClaw, and Hermes Agent under one desktop manager" - underscoring that skills and MCP server configs are increasingly expected to be portable across harnesses.

**Platforms:** Hacker News, X/Twitter, GitHub

---

## Cross-Source Patterns

**Pattern 1: MCP is beating Skills as the "real" capability layer**
- Appeared on: Reddit, X/Twitter, Web
- Multiple practitioners with significant build experience (r/claudeskills 100 pts thread, @CripdoeCrypto's $15k build) converge on the same view: skills/CLAUDE.md are easy and useful, but MCP is where serious capability differentiation lives
- Key quote: "The wrapper doesn't matter. The MCP is where the real differentiation is." - r/claudeskills (65 comments)

**Pattern 2: Security is the ecosystem's debt coming due**
- Appeared on: X/Twitter, Hacker News, Web
- NVIDIA scanner alert, AgentSeal 66% vulnerability finding, Microsoft's February 2026 crisis documentation, and multiple new security tools all launched within weeks
- Key quote: "The risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?'" - @stretchcloud

**Pattern 3: Claude Code's plugin format is becoming a portability standard**
- Appeared on: Hacker News, GitHub, X/Twitter
- ZCode, OpenClaw, Hermes Agent, Gemini CLI, and other harnesses are implementing Claude Code-shaped configs (`mcp.servers`, `plugins.enabledPlugins`, `hooks`)
- CC Switch (111.8K stars) manages all of them under one desktop manager

**Pattern 4: Confusion between taxonomy layers is driving content production**
- Appeared on: Web, Reddit, X/Twitter
- At least 8 distinct explainer articles published in June alone covering skills vs MCP vs plugins vs connectors - the ecosystem's vocabulary has outpaced documentation

**Pattern 5: Real-world token cost is a forcing function for skill design**
- Appeared on: Bluesky, Hacker News, Reddit
- @wenchangyue.bsky.social: 1 billion tokens in 5 working days = $1,400. The TS Compiler Graph MCP claiming "10x fewer tokens." archex MCP workflow specifically targeting token efficiency. Cost is shaping skill architecture decisions.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/claudeskills | 90% claude code tutorials are waste of time | 100 | 65 | "The wrapper doesn't matter. The MCP is where the real differentiation is." | https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/ |
| r/ClaudeAI | tested Claude Fable 5 and Opus 4.8 across 917 coding-agent scenarios | 103 | 94 | "We scored them both with and without the relevant skill loaded." | https://www.reddit.com/r/ClaudeAI/comments/1u3vyk7/tested_claude_fable_5_and_opus_48_across_917/ |
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory (bhived MCP) for Skill and Knowledge Discovery | 1 | — | "Agents repeatedly start from scratch, relying on whatever skills are currently loaded, with no awareness of what skills the agent community has already developed." | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2j9/workflow_enhance_claude_code_agents_with_shared/ |
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP | 1 | — | "Workflow value: 85/100 - advanced" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/ |
| r/ClaudeWorkflows | Improve Claude Code Agent Token Efficiency with archex MCP Server and Skill for Context Retrieval | 1 | — | "Workflow value: 85/100 - advanced" | https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @AnthropicAI | Export controls lifted on Claude Fable 5 and Mythos 5 | 84,299 | 13,027 | https://x.com/AnthropicAI/status/2072106151890809341 |
| @AnthropicAI | Fable 5 restored globally + new cybersecurity classifiers | 42,752 | 6,486 | https://x.com/AnthropicAI/status/2072163884430229756 |
| @AnthropicAI | Mythos 5 redeployed to US critical infrastructure orgs | 30,639 | 3,199 | https://x.com/AnthropicAI/status/2070665903440871779 |
| @claudeai | Fable 5 access for paid plans through July 7 | 1,124 | 70 | https://x.com/claudeai/status/2072402639644766602 |
| @claudeai | Use /feedback if requests are mistakenly flagged | 759 | 37 | https://x.com/claudeai/status/2072402640907162072 |
| @ClaudeDevs | Learn features via the built-in "claude-api" skill | 88 | — | https://x.com/ClaudeDevs/status/2072058431712948563 |
| @RituWithAI | NVIDIA security scanner for AI agent skills (almost nobody using it) | 9 | 6 | https://x.com/RituWithAI/status/2065656659842842728 |
| @CripdoeCrypto | MCP layer as real unlock: 2 servers, 42 tools, one config line | 14 | 7 | https://x.com/CripdoeCrypto/status/2070217687247225271 |
| @chenzeling4 | Anthropic official plugin directory shipped (31.2K stars) | 1 | — | https://x.com/chenzeling4/status/2071051965057094088 |
| @chenzeling4 | CC Switch: one desktop manager for all AI coding agents (111.8K stars) | 5 | — | https://x.com/chenzeling4/status/2072425045394407787 |
| @N0V4Dev | AWS MCP toolkit for cloud tasks (CDK, Lambda) in Claude Code | 3 | — | https://x.com/N0V4Dev/status/2070816988423700702 |
| @stretchcloud | Risk has moved to "what is installed on the developer workstation?" | 3 | — | https://x.com/stretchcloud/status/2068096486479462549 |
| @AsterProinos | Aster Guard MCP: lightweight local-first MCP security checker | 4 | — | https://x.com/AsterProinos/status/2067992519334597089 |
| @artyomx | Fact-checking the official marketplace: real but simpler than hype | 8 | 1 | https://x.com/artyomx/status/2065925946717168096 |
| @trendai_RSRCH | 9,695 MCP servers analyzed: no correlation between stars and security | 1 | — | https://x.com/trendai_RSRCH/status/2072576002509684762 |
| @SRLsasame | MCP best practice: name side effects before agent calls the tool | 1 | — | https://x.com/SRLsasame/status/2072545872265543923 |
| @iam_elias1 | 10 Essential Claude Code Skills to Unlock the Full Potential | 3 | 1 | https://x.com/iam_elias1/status/2072625945220174062 |
| @turnkeyhq | Architecting Secure Onchain Workflows With AI Skills and MCP Servers | 15 | 1 | https://x.com/turnkeyhq/status/2065069029375541667 |
| @SaurabhDub28465 | Claude's 18 official AI courses including "Introduction to Agent Skills" | 22 | 5 | https://x.com/SaurabhDub28465/status/2072621228045586530 |
| @Xylonet_ | AI agents discovering services and making payments via x402 + MCP | 22 | 9 | https://x.com/Xylonet_/status/2072615958787621336 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kirushik | Claude Code is steganographically marking requests | 2,387 | 725 | — | https://thereallo.dev/blog/claude-code-prompt-steganography |
| nab | Boxes.dev: ditch localhost; run Claude Code and Codex in the cloud | 105 | 79 | — | https://boxes.dev |
| handfuloflight | ZCode: Claude Code from the Makers of GLM | 274 | 13 | — | https://zcode.z.ai/cn |
| pascoej | The Safari MCP server for web developers | 11 | — | — | https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/ |
| softie123 | Show HN: A police department for your Claude Code agents | 11 | 8 | — | https://github.com/varmabudharaju/agent-pd/blob/master/README.md |
| sermakarevich | Show HN: Lessons learned from running Claude Code swarms at scale | 10 | 7 | — | https://news.ycombinator.com/item?id=48407998 |
| karl_gluck | Show HN: Claireon – MCP Server for Unreal Editor | 10 | 2 | — | https://github.com/believer-oss/claireon |
| bardonadam | Unreal Engine 5.8 adds MCP server for AI agents | 8 | 2 | — | https://www.unrealengine.com/news/unreal-engine-5-8-is-now-available |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | — | — | https://github.com/OpenYabby/OpenYabby |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| gagewoodard | Norrin – Git/diff control in Claude Code | 4 | 1 | — | https://news.ycombinator.com/item?id=48619320 |
| brightmonkey | Show HN: Orchid – Local-first record and replay for AI agent debugging | 4 | 2 | — | https://github.com/mario-guerra/orchid-trace |
| barakolshe | Claude Code Issue management extension for VS Code | 3 | 1 | — | https://www.forq.ink/ |
| di_desle | AgentSploit – Burp Suite for AI Agents and MCP Servers | 3 | — | — | https://github.com/agentsploit/agentsploit |
| autobe | Show HN: TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | — | — | https://github.com/samchon/ttsc/tree/master/packages/graph |
| momoraul | Show HN: Lupen – which Claude Code turn or sub-agent ran up your bill | 3 | — | — | https://github.com/momoraul/Lupen |
| dodizzle | Shipwright Harness – open-source autonomous delivery agent for Claude Code (MIT) | 3 | — | — | https://github.com/app-vitals/shipwright |
| dhevenddra_ | Show HN: Forensic-deepdive: code knowledge graph and MCP server for AI agents | 3 | — | — | https://github.com/Dhevenddra/forensic-deepdive |
| selcuk | Show HN: Namecom-CLI – CLI and agent skill so Claude Code/Codex can do your DNS | 4 | — | — | https://github.com/hypersocialinc/namecom-cli |
| JackLau | Ratchet – BIOS flashing toolkit with a built-in MCP server for AI agents | 5 | — | — | https://github.com/jackulau/ratchet |
| imaxxs | Gemini CLI vs. Claude Code: Why agent capabilities matter more than prompts | 3 | — | — | https://imaxxs.com/behavioral-induction-capabilities-shape-execution |
| jguarnelli | Show HN: Diplomat-agent scan Python MCP servers for unguarded tool calls | 3 | — | — | https://github.com/Diplomat-ai/diplomat-agent |
| arzzen | Show HN: Visual multi-agent orchestration for Claude Code | 5 | — | — | https://github.com/rondoflow/rondoflow |
| robjampar | GraphQL MCP Server and GraphiQL Plugins | 4 | 1 | — | https://graphql-mcp.com/ |
| Bridgexapi | The SDK Is for Developers. The MCP Server Is for Agents | 3 | — | — | https://blog.bridgexapi.io/the-sdk-is-for-developers-the-mcp-server-is-for-agents |
| di_desle | QodFlow – a Kanban board AI agents can drive via MCP | 3 | 1 | — | https://www.qodflow.com |
| deathmonger5000 | Show HN: Circus Chief – Claude Code, Codex, and Gemini from Your Phone | 4 | — | — | https://github.com/ferrislucas/Circus-Chief |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @sexabolition.blog | Claude Code UX "reinvents the Hacker man scrolling source code experience for people who imagine that's what technical work entails" | 27 | https://bsky.app/profile/sexabolition.blog/post/3mpjtnp4azc2k |
| @jptreen.com | Claude Code sub-agent fork as default: "randomly decides when it wants to, which overall means it's a bad default which often works fine but can greatly increase token consumption" | 14 | https://bsky.app/profile/jptreen.com/post/3mp6th7qr4s2l |
| @richholman.com | /design-sync command bridges Claude Code and claude.ai/design agent | 10 | https://bsky.app/profile/richholman.com/post/3mpl7meypoc2x |
| @noah.exposed | "Claude 4.8 (even with the 1M context window) forgets things the moment it gets distracted. If anything, it does a decent job of emulating someone with ADHD" | 21 | https://bsky.app/profile/noah.exposed/post/3mpc2buws4k2x |
| @gigazine.net | Comfy MCP: image/video generation automation via Claude Code and ComfyUI | 7 | https://bsky.app/profile/gigazine.net/post/3mphzhakwsz22 |
| @wenchangyue.bsky.social | 5 working days of AI coding = ~1 billion tokens, $1,400 at list price | 3 | https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i |
| @dennisdoomen.com | "Not uncommon for me to have 3-5 agent sessions running in parallel in JetBrains Junie, Claude Code and GitHub Copilot" | 2 | https://bsky.app/profile/dennisdoomen.com/post/3mp6bc7s7yk2x |
| @hackmd.io | "Your agents need more than prompts - they need skills. Markdown is becoming agent infrastructure." | 1 | https://bsky.app/profile/hackmd.io/post/3mpgqxdcz5k2b |
| @rafaelabellan.bsky.social | "Claude Code running unattended? Never as root. Container isolation isn't a cage. It's permission to run fast without the cost of burning down the house." | 1 | https://bsky.app/profile/rafaelabellan.bsky.social/post/3mpfspofuef2d |
| @tech-trending.bsky.social | macOS local VM infrastructure for running Claude Code securely | 2 | https://bsky.app/profile/tech-trending.bsky.social/post/3mphur5p5wm2x |

**GitHub:**
| Repo | Title | Reactions | Comments | URL |
|------|-------|-----------|----------|-----|
| danny-avila/LibreChat | feat: MCP Apps support (interactive HTML in-chat resources) | — | 34 | https://github.com/danny-avila/LibreChat/pull/13831 |
| middleapi/orpc | feat(mcp): @orpc/mcp - serve one oRPC router as an MCP server | — | 8 | https://github.com/middleapi/orpc/pull/1604 |
| hashgraph-online/hol-guard | feat(guard): add z.ai ZCode harness adapter | 3 | 2 | https://github.com/hashgraph-online/hol-guard/pull/924 |
| manaflow-ai/cmux | Re-apply cmux hook --settings on native claude resume | — | 3 | https://github.com/manaflow-ai/cmux/pull/5430 |
| novuhq/novu | feat(shared): onboard 22 MCP providers to DCR OAuth | — | 4 | https://github.com/novuhq/novu/pull/11470 |
| kelos-dev/kanon | Add composable Kanon packs for reusable multi-setting bundles | — | 2 | https://github.com/kelos-dev/kanon/issues/35 |
| irfndi/prism-liquidity-agent | feat(mcp-server): add prism-mcp-server for Claude Desktop | 3 | 3 | https://github.com/irfndi/prism-liquidity-agent/pull/41 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claude.com | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | Official Anthropic blog: 7 methods for steering Claude Code including CLAUDE.md, skills, hooks, rules, subagents |
| claude.com | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Dynamic multi-agent harness patterns; Claude Code writing its own orchestration |
| GitHub (anthropics/claude-plugins-official) | https://github.com/anthropics/claude-plugins-official | Official curated plugin directory; 55+ plugins |
| GitHub (anthropics/skills) | https://github.com/anthropics/skills | Public Anthropic skills repository |
| lagrowthmachine.com | https://lagrowthmachine.com/claude-plugins-marketplace/ | Plugin marketplace how-to; install-in-one-command patterns |
| arte.itlibra.com | https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace | 22-minute plugin guide covering structure, build, publish |
| morphllm.com | https://www.morphllm.com/claude-code-marketplace | Plugin and marketplace install guide with verified /plugin commands |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Skills vs MCP vs Plugins layer model explained |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills vs MCP vs Connectors vs Plugins taxonomy (June 2026) |
| jsmanifest.com | https://jsmanifest.com/claude-code-plugin-packaging-guide | Plugin packaging: bundling skills, hooks, subagents, MCP servers |
| jsmanifest.com | https://jsmanifest.com/claude-code-full-stack-guide | Full extension stack: CLAUDE.md, skills, MCP, subagents, hooks |
| docs.cloud.google.com | https://docs.cloud.google.com/agent-registry/use-agentregistry-mcp | Google Cloud Agent Registry MCP server for dynamic agent discovery |
| truefoundry.com | https://www.truefoundry.com/blog/mcp-registry-and-ai-gateway | MCP Registry + AI Gateway enterprise architecture |
| agentseal.org | https://agentseal.org/blog/mcp-server-security-findings | 1,808 MCP servers scanned: 66% had security findings |
| mintmcp.com | https://www.mintmcp.com/blog/mcp-server-security-vetting | Enterprise MCP server security vetting guide |
| workos.com | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | MCP donated to Agentic AI Foundation; cross-vendor adoption |
| techcommunity.microsoft.com | https://techcommunity.microsoft.com/blog/microsoft-security-blog/the-state-of-mcp-security-in-2026/4531327 | February 2026 MCP crisis: RCE, malicious skills marketplace poisoning |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_extension_layers_decision_guide.html | Extension layer decision guide for skills vs subagents vs hooks vs plugins |

---

## Stats Block

```
├─ 🔵 X: 25 posts │ 160,596 likes │ 22,908 reposts
├─ 🟢 HN: 28 stories │ 2,895 points │ 843 comments
├─ 🟠 Reddit: 5 threads │ 206 upvotes │ 159 comments
├─ 🦋 Bluesky: 12 posts │ 92 likes │ 3 reposts
├─ 🐙 GitHub: 9 items │ 25 reactions │ 87 comments
├─ 🌐 Web: 18 pages
└─ 🗣️ Top voices: @AnthropicAI, @claudeai, @chenzeling4 │ r/ClaudeWorkflows, r/claudeskills, r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 results.** The yt-dlp search queries were too long and returned nothing. Short, focused queries ("Claude Code skills tutorial") would likely surface content; this is a search query length problem, not a content availability problem.
- **TikTok: 0 results.** ScrapeCreators returned HTTP 402 (quota exceeded) on all hashtag queries. TikTok likely has coverage given the ecosystem's growth.
- **Instagram: 0 results.** Same HTTP 402 issue.
- **Reddit: only 5 threads.** The keyless tier returned limited results. The dedicated subreddits (r/ClaudeAI, r/ClaudeCode) returned 0 posts via the dedicated lane, likely rate-limited. Actual Reddit discussion is substantially richer - the r/claudeskills and r/ClaudeWorkflows finds indicate active communities.
- **GitHub: no authenticated API.** Operating on unauthenticated tier with low rate limits, restricting to 9 items. Actual GitHub activity on MCP and skills repos is substantially higher.
- **Freshness:** Only 42 of 97 dated items are from the last 7 days. Coverage is weighted toward earlier June.
- **Approximate coverage:** 55-65% of available content captured. Security community, YouTube, TikTok, and authenticated Reddit are the main gaps.

---

## Key Quotes

> "The real unlock is the MCP layer. Two servers. 42 tools. Your AI agent gets the whole stack as native capabilities - no API key, no signup, no auth. Paste one config line." — [@CripdoeCrypto](https://x.com/CripdoeCrypto/status/2070217687247225271) on X

> "The uncomfortable part of agentic coding is that the risk has moved from 'what did the model say?' to 'what is installed on the developer workstation?'" — [@stretchcloud](https://x.com/stretchcloud/status/2068096486479462549) on X

> "NVIDIA just built the security scanner that every developer installing AI agent skills desperately needs. And almost nobody is using it yet. Skills are the new plugins." — [@RituWithAI](https://x.com/RituWithAI/status/2065656659842842728) on X

> "The marketplace is real and official → anthropics/claude-plugins-official. What's FALSE: 'sets everything up step-by-step for you' - this is the lie. Under the hood it's literally one SKILL.md + 5 reference markdown files." — [@artyomx](https://x.com/artyomx/status/2065925946717168096) on X

> "90% claude code tutorials are waste of time. They all work the same under the hood. The wrapper doesn't matter. The MCP is where the real differentiation is." — [r/claudeskills](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) (100 pts, 65 comments)

> "Your agents need more than prompts - they need skills. Markdown is becoming agent infrastructure." — [@hackmd.io](https://bsky.app/profile/hackmd.io/post/3mpgqxdcz5k2b) on Bluesky

> "We scanned 1,808 MCP servers. 66% had security findings. No correlation between GitHub star count and security quality. Popular does not mean safe." — [AgentSeal](https://agentseal.org/blog/mcp-server-security-findings)

> "AI agents are only as secure as the MCP servers they connect to. TrendAI Research analyzed 9,695 of them and found no correlation between GitHub star count and security quality." — [@trendai_RSRCH](https://x.com/trendai_RSRCH/status/2072576002509684762) on X

> "5 working days of AI coding (Claude Code + a Codex agent) = ~1 billion tokens, about $1,400 at API list price. More than a US postdoc earns in a week." — [@wenchangyue.bsky.social](https://bsky.app/profile/wenchangyue.bsky.social/post/3mpapsofxfb2i) on Bluesky

> "The MCP filesystem reference server does one thing most builders skip: every tool description names the side effect before an agent calls it. That one line of honesty is a big deal." — [@SRLsasame](https://x.com/SRLsasame/status/2072545872265543923) on X
