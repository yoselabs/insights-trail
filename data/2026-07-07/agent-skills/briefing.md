# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-07
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 7 threads | 6,579 upvotes, 1,196 comments | r/ClaudeAI, r/LocalLLaMA |
| X/Twitter | 20 posts | 2,459 likes, 172 reposts | @AnthropicAI, @github_update, @Durektor97 |
| Hacker News | 33 stories | 204 points, 42 comments | Heavy Show HN activity |
| Bluesky | 4 posts | 10 likes, 1 repost | |
| GitHub | 25 items | 830 reactions, 1,398 comments | anthropics/claude-code dominant |
| Web | 26 pages | — | via engine + WebSearch supplements |

---

## Synthesized Findings

### 1. The Extension Taxonomy Is Finally Clear — Skills vs MCP vs Plugins

The community has converged on a clean mental model for Claude Code's extension layers, and multiple guides published in June/July 2026 now treat this as settled architecture. **Skills** are markdown-based procedural instructions (~30-50 tokens each, loaded on-demand) that teach Claude how to do something repeatably. **MCP servers** are running processes that expose tools and external system access (GitHub, databases, browsers) — expensive in context (a five-server setup costs 50k+ tokens upfront). **Plugins** are versioned distribution bundles that package all three plus hooks, subagents, and LSP servers.

The canonical decision tree from [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/): "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." The [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) guide adds: "People treat plugins, skills, and MCP servers as three options on the same menu, then get confused when the comparison doesn't quite work."

The working pattern that has emerged: pin one MCP per external system (GitHub, Postgres, Linear, Sentry), then write thin skills that orchestrate them. Skills for methodology, MCP for connectivity.

*Discussed on: Web, HN, X/Twitter*

---

### 2. The Token Waste Problem Is Driving a New Wave of Optimization Tools

The community has identified a fundamental flaw in how agents load extensions: everything gets loaded at session start, whether it's needed or not. A r/ClaudeAI thread from June 12 put numbers on it: "I checked my session transcripts: 187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) (3 pts, 21 comments).

This has spawned a wave of optimization tools. [@mu_mash on X](https://x.com/mu_mash/status/2074120482983694509) open-sourced a fix: "paste one sentence into Claude Code or Codex → it builds a project map + feature-to-file index, trims unused MCP servers. 60-90% cheaper startups." [@Voxyz_ai](https://x.com/Voxyz_ai/status/2074092352545661435) shared a diagnostic prompt: "make claude code confess where the tokens go... which tools and MCP servers loaded this session but never got used... unused MCP servers are the easiest miss: their tool definitions take up context whether you call them or not."

The [Show HN: TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex](https://github.com/samchon/ttsc/tree/master/packages/graph) submission on July 1 (3pts) addresses the same problem from the MCP architecture side.

*Discussed on: Reddit, X/Twitter, HN*

---

### 3. MCP Has Won — It Is Now the Universal Standard

[@vbkotecha on X](https://x.com/vbkotecha/status/2074433904740889046) captured the community consensus: "The single most underrated development in AI this year is not a model. It is a protocol. MCP, Model Context Protocol, was released by Anthropic in late 2024. It got almost no press. No keynote. No product launch event. Just a GitHub repository and a specification document. 18 months later, every major AI framework supports it. OpenAI. Google. Microsoft. Cursor. Replit. Windsurf. Claude Code. Hermes. Codex. Every coding agent. Every agent framework. MCP does for AI tools what HTTP did for web."

Adoption data from [digitalapplied.com](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol): tracked server count crossed ~9,400 distinct MCP servers by mid-April 2026 (up from ~6,800 at year-end 2025, ~38% growth in four months); MCP SDKs now pull ~97 million downloads/month. The MCP protocol has been governed by the Linux Foundation since December 2025. Unreal Engine 5.8 added an MCP server for AI agents (HN, June 18, 8 pts). Databricks added MCP server support to its agent framework (June 30). Rasa added native MCP integration in v3.14 beta. AWS published an open-source blog on [Governing AI Assets at Scale with MCP Gateway and Registry](https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/).

*Discussed on: X/Twitter, HN, Web, Bluesky*

---

### 4. Architecture Ceiling: MCP Servers Start Failing Past 15 Tools

[@AlphaSignalAI](https://x.com/AlphaSignalAI/status/2074173366739534069) surfaced a concrete production finding: "Your MCP server starts failing at 15 tools. This industry study looked at 15 production and open-source MCP servers and pulled out 5 architecture patterns, 4 anti-patterns, and the numbers behind them. Claude Haiku 4.5 drops below 90% accuracy between 10 and 15 tools. Claude Sonnet 4 holds to about 20 tools, then falls by 30." The fix is scoped retrieval — exposing tools contextually rather than loading them all upfront.

The [ghidra-mcp GitHub issue](https://github.com/bethington/ghidra-mcp/issues/307) from the community shows this playing out in practice: "this is becoming a complex unmaintainable mess... too many tools for agents." The Kiro issue tracker shows MCP stdio servers spawning visible CMD windows on Windows ([Kiro/issues/9713](https://github.com/kirodotdev/Kiro/issues/9713)), pointing to ongoing cross-platform reliability gaps.

The community workaround is the "MCP gateway" pattern: a single local process that proxies all your MCP servers, manages their configs centrally, and presents a unified interface. One r/ClaudeAI user built [Toolport](https://www.reddit.com/r/ClaudeAI/comments/1uofd0i/i_got_tired_of_managing_mcp_servers_separately_in/) to solve exactly this: "If you use MCP servers in more than one place (Claude Desktop, Claude Code, Cursor, whatever else), you're maintaining separate config files with API keys sitting in plaintext JSON... Once I passed a dozen servers it got genuinely painful."

*Discussed on: X/Twitter, Reddit, GitHub*

---

### 5. The Marketplace Ecosystem Has Exploded — Eight Major Platforms by Q2 2026

The agent skills marketplace landscape went from one registry in December 2025 to eight major platforms by Q2 2026, per [agensi.io](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026). [skillselion.com](https://skillselion.com/state-of-ai-agent-skills-2026) now tracks 87,810 AI coding-agent tools (66,910 agent skills, 8,251 MCP servers, and 10,264 marketplaces) with 130 million combined installs. Smithery is the closest equivalent to Docker Hub in the MCP ecosystem with 7,000+ available servers; MCPMarket.com lists 10,000+ servers across 23+ categories.

The skill portability story — "write once, works everywhere" — has driven adoption. A skill created for Claude Code automatically works in Cursor, VS Code, GitHub Copilot, and 16+ other AI tools. [totalum.app](https://www.totalum.app/blog/agent-skills-marketplaces-2026) notes that competition is now shifting from catalog size to trust infrastructure: "distribution and portability largely solved, while open questions for the back half of 2026 are governance, verification, and quality."

[@github_update on X](https://x.com/github_update/status/2067259115777507386) tracked "AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking" in June 17 GitHub trending, confirming developer discovery interest. Today's GitHub trending included [alirezarezvani/claude-skills](https://x.com/github_update/status/2074176588195721395), per @github_update.

*Discussed on: X/Twitter, Web*

---

### 6. Security and Governance Gaps Are Growing as Adoption Outpaces Policy

[@rishiamar on X](https://x.com/rishiamar/status/2074351474537042276): "Three things happening on enterprise Mac fleets right now: Developers running Claude Code. No policy. MCP servers connecting to external services IT hasn't reviewed. #AIGovernance #CISO #EUAIAct"

[@DomJoLuna](https://x.com/DomJoLuna/status/2074239964318212216) highlighted a key Claude Code security fix this week: "`claude mcp list/get` stopped spawning repo-committed MCP servers in untrusted workspaces. thank you Anthropic a random repo should not get to self-approve the tools that inspect it." The [SentinelMCP project](https://github.com/technosiveuk-ui/SentinelMCP) on HN (June 13) bills itself as "an open-source firewall for AI agents that use MCP." [AgentSploit](https://github.com/agentsploit/agentsploit) (HN, June 9, 8pts) is a "Burp Suite for AI Agents and MCP Servers."

AWS's open-source blog explicitly addresses enterprise MCP governance: "Enterprises that onboard AI assets (MCP servers, agents, skills, and multi-step workflows) need to govern these assets and make them discoverable without blocking innovation." The [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) GitHub project offers enterprise-ready MCP gateway with OAuth authentication, dynamic tool discovery, and Keycloak/Entra integration.

*Discussed on: X/Twitter, HN, Web*

---

### 7. Claude Code Skills as Team Multipliers — The Practitioner Story

The highest-engagement practitioner content frames skills as team-of-one amplifiers. [@PrajwalTomar_](https://x.com/PrajwalTomar_/status/2074095215422705805) (59 likes, 9 reposts): "These 10 Skills Turn Claude Code Into an ENTIRE Team." [@Durektor97](https://x.com/Durektor97/status/2074219835500962140): "You are using Claude Code at 20% of what it can actually do... In this video he shows his real professional setup Skills subagents connecting to MCP servers and a much deeper understanding of how Claude Code works from the inside."

[@zaibpreneur](https://x.com/zaibpreneur/status/2074203732653285839) highlighted @cyrilXBT's tool that "suggests and auto-installs the right hooks, skills, MCP servers, and subagents for Claude Code. It upgrades a plain install into a disciplined, full-stack AI dev workspace." The community sentiment is clear: the default Claude Code setup captures a fraction of the platform's power.

[@suraj_sharma14](https://x.com/suraj_sharma14/status/2074169000486199398) (28 likes): "WHAT THE F*CK! 6 months ago we were arguing about prompts. Now people are: Running Claude Code + Codex together. Giving agents memory. Building custom MCP servers. Using AI to write PRDs. Using AI to review pull requests. Having agents debug other agents. Shipping products with teams of 1-2 people. The AI era moves ridiculously fast."

[@github_update](https://x.com/github_update/status/2072200713808281666) citing Bilgin Ibryam's breakdown: "Most agent failures are not model failures. They are harness failures... A model can be highly capable and still fail inside a weak agent system."

*Discussed on: X/Twitter*

---

### 8. Specialized MCP Servers for Memory, Cognitive State, and Cross-Agent Communication

A notable cluster of HN Show HN submissions from June 2026 focuses on MCP-powered memory and agent state persistence:

- [Katra - self-hosted cognitive memory for AI agents (MCP)](https://github.com/kolegadev/Katra-Agentic-Memory) (June 29, 4pts)
- [PMB - local-first memory for AI coding agents over MCP](https://github.com/oleksiijko/pmb/blob/main/README.md) (June 22, 7pts, 6 comments)
- [Cortex - local-first encrypted memory for AI agents (Rust, MCP)](https://github.com/gambletan/cortex) (June 13, 4pts)
- [Reference MCP - let your AI agents search each other's past sessions](https://github.com/kuberwastaken/reference) (June 29, 5pts)
- [Your self, in every light - a local-first MCP self model for AI agents](https://github.com/almakit/alma) (June 23, 4pts)

This points to memory as the next frontier after tool connectivity: agents that remember context across sessions, share knowledge with other agents, and maintain cognitive state over time.

*Discussed on: HN*

---

## Cross-Source Patterns

**Pattern 1: Context/token efficiency has become the defining technical challenge**
- Appeared on: Reddit, X/Twitter, HN, Web
- The 8K-tokens-wasted-per-session finding from r/ClaudeAI is directionally confirmed by multiple X posts (@mu_mash, @Voxyz_ai) and the TS Compiler Graph MCP "10x fewer tokens" HN submission. Guides now explicitly recommend skills-first over MCP-first precisely because of context cost.
- Key quote: "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight" — u/[r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/)

**Pattern 2: MCP is now the universal plumbing — the question is governance**
- Appeared on: X/Twitter, HN, Web, GitHub
- The "MCP does for AI tools what HTTP did for web" framing (per @vbkotecha) is the community consensus. But adoption has outpaced policy: enterprise teams now face ungoverned MCP servers connecting to unreviewed external services. AWS, GitHub, and security tools like SentinelMCP and AgentSploit are all responding to this gap.
- Key quote: "the best Claude Code changelog line this week is not the model launch. it's the bit where `claude mcp list/get` stopped spawning repo-committed MCP servers in untrusted workspaces" — [@DomJoLuna](https://x.com/DomJoLuna/status/2074239964318212216)

**Pattern 3: Default Claude Code installs are dramatically under-configured**
- Appeared on: X/Twitter, Reddit, Web
- Multiple high-engagement posts frame skills/MCP setup as a major unlock that most users miss entirely. The auto-install tooling (@cyrilXBT's tool, per @zaibpreneur), the 10-skills-for-a-full-team framing (@PrajwalTomar_), and the "20% of what it can do" narrative all converge on the same message.
- Key quote: "You are using Claude Code at 20% of what it can actually do" — [@Durektor97](https://x.com/Durektor97/status/2074219835500962140)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I built gui-tool — a zero-dependency CLI that gives Claude Code control of the desktop | 1 | 19 | "It ships an Agent Skills SKILL.md, so you drop it in ~/.cl..." | [link](https://www.reddit.com/r/ClaudeAI/comments/1uodpyi/i_built_guitool_a_zerodependency_cli_that_gives/) |
| r/ClaudeAI | I got tired of managing MCP servers separately in every app, so I had Claude Code build a free gateway | 1 | 7 | "Once I passed a dozen servers it got genuinely painful. What I built: Toolport..." | [link](https://www.reddit.com/r/ClaudeAI/comments/1uofd0i/i_got_tired_of_managing_mcp_servers_separately_in/) |
| r/ClaudeAI | Using Claude Code? You're probably wasting ~8k tokens per session on unused skills | 3 | 21 | "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) |
| r/LocalLLaMA | Effect of GLM 5.2 | 3,131 | 503 | "All hail Z.AI" | [link](https://www.reddit.com/r/LocalLLaMA/comments/1uiv8e4/effect_of_glm_52/) |
| r/LocalLLaMA | Donate your coding sessions to an open CC-BY-4.0 dataset | 1,344 | 211 | "Anthropic and OpenAI are getting so much data from Claude Code and Codex usage... I'm quite scared this will create an oligopoly" | [link](https://www.reddit.com/r/LocalLLaMA/comments/1u795pb/donate_your_coding_sessions_to_an_open_ccby40/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @PrajwalTomar_ | These 10 Skills Turn Claude Code Into an ENTIRE Team. | 59 | 9 | [link](https://x.com/PrajwalTomar_/status/2074095215422705805) |
| @suraj_sharma14 | WHAT THE F*CK! 6 months ago we were arguing about prompts. Now people are: Running Claude Code + Codex together, giving agents memory, building custom MCP servers... | 28 | 1 | [link](https://x.com/suraj_sharma14/status/2074169000486199398) |
| @AnthropicAI | The J-space lets us read, audit, and shape what Claude is actively thinking about | 720 | 51 | [link](https://x.com/AnthropicAI/status/2074185387577094398) |
| @AnthropicAI | We also partnered with Neuronpedia to create an interactive demo of our methods on open-weights models | 919 | 64 | [link](https://x.com/AnthropicAI/status/2074185390060110138) |
| @ds_fafa_ | Stop wasting hours on repetitive tasks. Automate your workflow & ship faster with Claude Code. → Extend tools with MCP servers → Automate PR reviews via GitHub → Build hooks | 8 | 2 | [link](https://x.com/ds_fafa_/status/2074045686413135902) |
| @DomJoLuna | the best Claude Code changelog line this week is not the model launch. it's the bit where `claude mcp list/get` stopped spawning repo-committed MCP servers in untrusted workspaces | 4 | 0 | [link](https://x.com/DomJoLuna/status/2074239964318212216) |
| @Durektor97 | You are using Claude Code at 20% of what it can actually do | 6 | 2 | [link](https://x.com/Durektor97/status/2074219835500962140) |
| @zaibpreneur | @cyrilXBT just dropped something wild: A system that suggests and auto-installs the right hooks, skills, MCP servers, and subagents for Claude Code | 1 | 1 | [link](https://x.com/zaibpreneur/status/2074203732653285839) |
| @AlphaSignalAI | MCP Server Architecture Patterns for LLM-Integrated Applications. Your MCP server starts failing at 15 tools. | 1 | 2 | [link](https://x.com/AlphaSignalAI/status/2074173366739534069) |
| @vbkotecha | The single most underrated development in AI this year is not a model. It is a protocol. MCP does for AI tools what HTTP did for web | 1 | 0 | [link](https://x.com/vbkotecha/status/2074433904740889046) |
| @rishiamar | Three things happening on enterprise Mac fleets right now: Developers running Claude Code. No policy. MCP servers connecting to external services IT hasn't reviewed. | 1 | 1 | [link](https://x.com/rishiamar/status/2074351474537042276) |
| @Voxyz_ai | make claude code confess where the tokens go. run /context once... unused MCP servers are the easiest miss | 3 | 0 | [link](https://x.com/Voxyz_ai/status/2074092352545661435) |
| @mu_mash | Your AI coding agent burns ~50K tokens/session just re-exploring your codebase. Open-sourced a fix... trims unused MCP servers. 60-90% cheaper startups | 0 | 1 | [link](https://x.com/mu_mash/status/2074120482983694509) |
| @github_update | Most agent failures are not model failures. They are harness failures. | 6 | 5 | [link](https://x.com/github_update/status/2072200713808281666) |
| @github_update | AI Builder 101: 20+ Agent Skills, Repos, and Marketplaces Worth Bookmarking | 8 | 2 | [link](https://x.com/github_update/status/2067259115777507386) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| nikitadvd | Show HN: Pulse - Dashboard for Claude Code, approve tool calls from your phone | 39 | 15 | — | [link](https://github.com/nikitadoudikov/claude-pulse) |
| modelorona | Show HN: CLI that helps AI agents avoid vulnerable dependencies | 26 | 5 | — | [link](https://github.com/clidey/deptrust) |
| bardonadam | Unreal Engine 5.8 adds MCP server for AI agents | 8 | 2 | — | [link](https://www.unrealengine.com/news/unreal-engine-5-8-is-now-available) |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | 0 | — | [link](https://github.com/OpenYabby/OpenYabby) |
| Dominic_P | Show HN: Web Speed - A shared web-map registry for AI agents (MCP, open source) | 7 | 4 | — | [link](https://www.getwebspeed.io/) |
| web_sensepro | WSP WordPress MCP - Connect AI Agents to WordPress | 7 | 0 | — | [link](https://github.com/bilalnaseer/wsp-wordpress-mcp) |
| piotrgrudzien | Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | 0 | — | [link](https://quickchat.ai/post/expose-ai-agent-as-mcp-server) |
| oleksiibond | Show HN: PMB - local-first memory for AI coding agents over MCP | 7 | 6 | — | [link](https://github.com/oleksiijko/pmb/blob/main/README.md) |
| GertLH | Show HN: Enola - A deterministic architecture graph for developers and AI agents | 10 | 4 | — | [link](https://github.com/enola-labs/enola/tree/main) |
| autobe | Show HN: I Made TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | 0 | — | [link](https://github.com/samchon/ttsc/tree/master/packages/graph) |
| nastynate | Show HN: Statuslin.es - a community library of custom Claude Code status lines | 4 | 0 | — | [link](https://statuslin.es) |
| arzzen | Show HN: Visual multi-agent orchestration for Claude Code | 5 | 0 | — | [link](https://github.com/rondoflow/rondoflow) |
| dodizzle | Shipwright Harness - open-source autonomous delivery agent for Claude Code (MIT) | 3 | 0 | — | [link](https://github.com/app-vitals/shipwright) |
| technsoive | SentinelMCP - An open-source firewall for AI agents that use MCP | 3 | 0 | — | [link](https://github.com/technosiveuk-ui/SentinelMCP) |
| di_desle | AgentSploit - Burp Suite for AI Agents and MCP Servers | 3 | 0 | — | [link](https://github.com/agentsploit/agentsploit) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @probbrain.bsky.social | AWS releases official MCP servers, skills, and plugins enabling AI agents to build on AWS | 1 | [link](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) |
| @uermel.bsky.social | Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting | 6 | [link](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) |
| @mikaelbuilds.bsky.social | Claude Code "still running" is not one bug. I built a no-secret packet for v2.1.179-style remote failures: status, remote vs shell, WSL2, sandbox globs, plugins | 1 | [link](https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w) |
| @toyinariyo.bsky.social | There are also many Godot AI plugins that can be used with Claude Code and Codex | 2 | [link](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| startdebugging.net | [link](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) | Canonical three-way decision guide: skills vs subagents vs MCP |
| mcsaguru.com | [link](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) | Layer-by-layer explanation of how plugins, skills, and MCP nest |
| agentforge.community | [link](https://agentforge.community/en/blog/smart-search-ai-discovery) | AI-powered MCP server discovery with semantic embeddings across 106+ options |
| skillselion.com | [link](https://skillselion.com/state-of-ai-agent-skills-2026) | State of AI Agent Skills 2026: 87,810 tools tracked, 130M combined installs |
| claudefa.st | [link](https://claudefa.st/blog/guide/development/dynamic-workflows) | Dynamic Workflows in Claude Code: patterns, harness mechanics |
| aws.amazon.com | [link](https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/) | Enterprise MCP governance framework, approved server lists |
| jsmanifest.com | [link](https://jsmanifest.com/claude-code-plugin-packaging-guide) | Plugin packaging guide: bundling skills, hooks, subagents, and MCP servers |
| dev.to | [link](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) | Extension selection decision tree: "lightest first" heuristic |
| tygartmedia.com | [link](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) | Claude Skills vs MCP vs Connectors vs Plugins: what each is |
| nimbalyst.com | [link](https://nimbalyst.com/blog/claude-code-plugins-guide/) | Official marketplace ships 101 vetted plugins as of March 2026 |
| morphllm.com | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Skills vs MCP vs Plugins guide; context cost comparison |
| digitalapplied.com | [link](https://www.digitalapplied.com/blog/mcp-adoption-statistics-2026-model-context-protocol) | MCP adoption statistics: 9,400+ servers, 97M SDK downloads/month |
| agensi.io | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Eight major skill marketplaces by Q2 2026 |
| totalum.app | [link](https://www.totalum.app/blog/agent-skills-marketplaces-2026) | Skills.sh (Vercel-backed, npm for skills); SkillsMP 800K+ skills |
| truefoundry.com | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Best MCP registries: Smithery 7K+ servers, MCPMarket 10K+ |
| calmops.com | [link](https://calmops.com/ai/ai-agent-skills-complete-guide-2026/) | Write-once-works-everywhere Agent Skills standard (Dec 2025 launch) |
| alexop.dev | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Full-stack Claude Code architecture explained |
| agentman.ai | [link](https://agentman.ai/blog/agent-skills-ecosystem-report-2026) | Agent skills ecosystem report 2026: governance/quality as next frontier |
| rasa.com | [link](https://rasa.com/docs/pro/build/mcp-integration/) | Rasa 3.14 adds native MCP server integration (beta) |
| docs.databricks.com | [link](https://docs.databricks.com/gcp/en/agents/mcp/use-mcp-in-agents) | Databricks agents now support MCP server connections (June 30) |
| docs.cloud.google.com | [link](https://docs.cloud.google.com/agent-registry/concepts) | Google Cloud Agent Registry concepts: agents defined by skills they possess |

---

## Stats Block

```
├─ 🟠 Reddit: 7 threads │ 6,579 upvotes │ 1,196 comments
├─ 🔵 X: 20 posts │ 2,459 likes │ 172 reposts
├─ 🟢 HN: 33 stories │ 204 points │ 42 comments
├─ 🦋 Bluesky: 4 posts │ 10 likes │ 1 repost
├─ 🐙 GitHub: 25 items │ 830 reactions │ 1,398 comments
├─ 🌐 Web: 26 pages
└─ 🗣️ Top voices: @AnthropicAI, @PrajwalTomar_, @suraj_sharma14, @github_update │ r/ClaudeAI, r/LocalLLaMA
```

---

## Data Gaps

- **YouTube: 0 results** — yt-dlp searches returned no results for this topic in the 30-day window; ScrapeCreators YouTube endpoint returned HTTP 402. Likely significant coverage exists (skills tutorials, MCP setup guides) but was not captured. Estimated miss: medium — practitioner video tutorials are a major vector for this topic.
- **TikTok: 0 results** — SC hashtag endpoint returned HTTP 402 for all hashtag searches (#claudecode, #mcpservers, #aiagent, #claudecodeskills). Topic likely has moderate TikTok presence given developer creator community.
- **Instagram: 0 results** — SC endpoint returned HTTP 402. Low expected coverage for this technical topic.
- **Reddit coverage is thin** — Only 7 threads despite searching r/ClaudeAI, r/ChatGPTCoding, r/LocalLLaMA, r/singularity, r/PromptEngineering, r/artificial. The dedicated ClaudeAI lane returned 0 posts from RSS. Most upvotes came from off-topic r/LocalLLaMA posts (GLM 5.2 discussion). True on-topic Reddit signal is 3 high-quality r/ClaudeAI threads.
- **Recent evidence thin**: only 37 of 105 dated items are from the last 7 days; coverage skews toward July 5-7.
- **Estimated coverage**: ~60-70% of available signal given YouTube/TikTok gaps. Core developer community (HN, X/Twitter, GitHub, Web) well-covered.

---

## Key Quotes

> "You are using Claude Code at 20% of what it can actually do. Most people open it up start chatting and never realize what they are missing." — [@Durektor97](https://x.com/Durektor97/status/2074219835500962140) on X

> "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate." — [u/r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) on Reddit

> "The single most underrated development in AI this year is not a model. It is a protocol... MCP does for AI tools what HTTP did for web." — [@vbkotecha](https://x.com/vbkotecha/status/2074433904740889046) on X

> "WHAT THE F*CK! 6 months ago we were arguing about prompts. Now people are: Running Claude Code + Codex together, giving agents memory, building custom MCP servers, using AI to write PRDs, shipping products with teams of 1-2 people." — [@suraj_sharma14](https://x.com/suraj_sharma14/status/2074169000486199398) on X

> "the best Claude Code changelog line this week is not the model launch. it's the bit where `claude mcp list/get` stopped spawning repo-committed MCP servers in untrusted workspaces. a random repo should not get to self-approve the tools that inspect it." — [@DomJoLuna](https://x.com/DomJoLuna/status/2074239964318212216) on X

> "Most agent failures are not model failures. They are harness failures. A model can be highly capable and still fail inside a weak agent system." — [@github_update](https://x.com/github_update/status/2072200713808281666) on X

> "Your MCP server starts failing at 15 tools. Claude Haiku 4.5 drops below 90% accuracy between 10 and 15 tools. Claude Sonnet 4 holds to about 20 tools, then falls by 30." — [@AlphaSignalAI](https://x.com/AlphaSignalAI/status/2074173366739534069) on X

> "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." — [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/)

> "Distribution and portability largely solved, while open questions for the back half of 2026 are governance, verification, and quality." — [agentman.ai](https://agentman.ai/blog/agent-skills-ecosystem-report-2026)

> "Once I passed a dozen servers it got genuinely painful. What I built: Toolport, a desktop app plus a local gateway that sits between your client and all your MCP servers." — [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1uofd0i/i_got_tired_of_managing_mcp_servers_separately_in/)
