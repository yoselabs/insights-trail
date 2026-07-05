# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-05
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 20 threads | 716 upvotes, 272 comments | r/ClaudeAI, r/AI_Agents |
| X/Twitter | 19 posts | 1,851 likes, 185 reposts | @alexalbert__, @SuperteamBR |
| Hacker News | 25 stories | 3,191 points, 949 comments | |
| Bluesky | 4 posts | 10 likes, 1 repost | |
| GitHub | 24 items | 917 reactions, 688 comments | anthropics/claude-code, microsoft/skills |
| Web | 19 pages | — | via engine grounding |
| Web (supplements) | 10 pages | — | via WebSearch |

---

## Synthesized Findings

### 1. The Taxonomy Has Settled: Skills, Plugins, and MCP Serve Distinct Layers

The community spent June 2026 furiously documenting the three-layer extension model that has emerged across Claude Code, Codex, Cursor, and OpenClaw. Multiple blog posts converged on the same vocabulary: **Skills** are markdown instruction files (SKILL.md) that teach an agent a repeatable procedure - installed with one sentence, free, cross-agent compatible. **Plugins** are bundled packages that wrap skills, hooks, subagent definitions, and MCP server configs into one installable directory, added via `/plugin marketplace add owner/repo`. **MCP servers** are running protocol bridges giving agents access to external systems - portable across any MCP-compatible client.

Anthropic published the canonical overview on June 18, 2026 - ["Steering Claude Code: CLAUDE.md files, skills, hooks, rules, subagents and more"](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) - laying out seven methods for instructing Claude's behavior. [mcsaguru.com](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained), [ccforeveryone.com](https://ccforeveryone.com/guides/claude-code-concepts-explained), and [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) all published layered explainers within the same week.

[@Layton_Gott](https://x.com/Layton_Gott/status/2073125199030157540) put it plainly (6 likes, 8 replies): "Skills have a HUGE impact in AI coding right now... A skill is just a markdown file with a dialed-in prompt essentially. Your agent reads it every time it's called, so you get the same behavior every time. Installing one takes a sentence... They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw."

Cross-platform coverage: Reddit, X, HN, Web.

---

### 2. Marketplace Explosion: 8+ Registries Racing for the npm Moment

The marketplace ecosystem grew from one registry in December 2025 to eight major platforms by Q2 2026. Key players:

- **[Skills.sh](https://skills.sh)** - Vercel-backed, launched January 2026; positioned as npm for skills with a one-command CLI installer that works across Claude Code, Codex, Cursor, and OpenClaw. Made its API generally available in June 2026 with 600,000 open-source skills indexed.
- **[Official Anthropic marketplace](https://github.com/anthropics/claude-plugins-official)** - 101 vetted first-party plugins + 68 partner plugins (AWS, Microsoft, Stripe, Shopify, Figma, Vercel, Linear, Sentry, Firebase) as of March 2026. Pre-registered in every Claude Code install - this distribution moat is significant, with top plugins showing six-figure install counts per [rywalker.com research](https://rywalker.com/research/claude-plugin-marketplace).
- **[ClaudeSkills.info](https://claudeskills.info)** - 658+ free community-contributed skills; no paid tier.
- **[Agensi](https://www.agensi.io)** - curated catalog organized by category with purchase/install flow.
- **[MCP Market Hub](https://mcpmarket.com/hub)** - version control for agent skills and MCP servers.

A June 2026 convergence event - the Code with Claude Tokyo event - triggered simultaneous announcements: Vercel shipped skills.sh GA, Cline released CLI 3.0.16 with plugin bundling, and Anthropic announced Managed Agents with 20+ vertical MCP connectors in the same week (per [totalum.app analysis](https://www.totalum.app/blog/agent-skills-marketplaces-2026)). [@DanKornas](https://x.com/DanKornas/status/2073566017595314660) noted (15 likes, 6 reposts): "Claude Code: Everything You Need to Know is a practical GitHub guide... organizing the workflow around setup, prompt engineering, skills, hooks, subagents, MCP, and agent teams."

Cross-platform coverage: X, HN, Web, Reddit.

---

### 3. Microsoft and Enterprise Players Enter the Skills Space

[@so_sthbryan](https://x.com/so_sthbryan/status/2073394395332657298) flagged a signal that attracted the HN crowd: "Microsoft ships an official skills repo for coding agents. microsoft/skills: 2.4k stars, 600 commits, real production intent - Skills, MCP servers, custom agents, and AGENTS.md templates - Designed to ground Claude Code, Copilot, and SDK-based agents. When MSFT publishes a 'how to agent' repo, the format is becoming a standard."

[Microsoft's official .NET blog](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) confirmed SKILL.md as an open standard supported across Claude Code, GitHub Copilot CLI, VS Code, and Visual Studio 2026, with 175+ skills available. The [microsoft/skills GitHub repo](https://github.com/microsoft/skills) is designed to be consumed across client ecosystems - AGENTS.md is becoming a co-standard alongside CLAUDE.md and .cursorrules.

At the enterprise layer, AWS published ["Governing AI Assets at Scale with MCP Gateway and Registry"](https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/) (June 17, 2026) and launched [AWS Agent Registry via Bedrock AgentCore](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) - a private, governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources. The [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) open-source project is solving the same problem with Keycloak/Entra integration.

Cross-platform coverage: X, HN, Web, Bluesky (AWS MCP announcement surfaced on Bluesky via @probbrain.bsky.social).

---

### 4. MCP Ecosystem Scale: 13,000+ Servers, 97M Monthly Downloads - But Discovery Is Broken

The MCP protocol itself has crossed a scale inflection point: over 13,000 registered servers (Glama alone indexed ~20,000), 97M monthly SDK downloads (per [tooldirectory.ai](https://tooldirectory.ai/blog/state-of-mcp-servers-2026)). Smithery has 7,000+ servers. X announced hosted MCP servers in July 2026, letting AI tools connect directly to the X API and docs MCP ([@Tork_Lab](https://x.com/Tork_Lab/status/2073240381802905624), 56 likes). Apple's Safari published an official [Safari MCP server for web developers](https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/) - 267 HN points, 75 comments.

But [a dev.to post](https://dev.to/mcsaguru207/the-mcp-gateway-pattern-managing-13000-servers-without-losing-your-mind-4an6) with high HN traction summed up the problem: "You've got 47 MCP servers running. Your agent needs the GitHub one, the Postgres one, and the Slack one - but it also has access to 44 others it absolutely does not need for this task... The bottleneck is no longer the protocol itself; it's discovery." An [arxiv paper on Skilldex](https://arxiv.org/html/2604.16911v1) proposed hierarchical scope-based skill distribution as a formal package management model.

HN also hosted "Show HN: PostgreSQL MCP Server with 135 tools" and "Show HN: Sub-Agent MCP: LLM delegation and sub-agent orchestration via MCP" - the long tail of specialty servers keeps growing.

Cross-platform coverage: X, HN, Web, Bluesky, Reddit.

---

### 5. Community Is Self-Publishing Skills-as-Plugins at Speed

The most active theme on Reddit this month was practitioners building and sharing their own skills and plugins:

- **"Ponytail"** ([r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3k2ed/i_gave_claude_code_a_lazy_senior_dev_mode_and_it/), 609 upvotes) - a skill that channels a "lazy senior dev" persona, walking a decision ladder before writing any code. "Ask for email validation and you get a 27-line EmailValidator class with a wrapper... Before it writes anything it walks a little ladder. Does this even need to be code?"

- **Specsmith v0.1.1** ([r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1uihxv9/i_built_a_claude_code_plugin_that_makes_the_ai/)) - "a plugin for Claude Code (also works in Cursor, Antigravity IDE, Codex, VS Code) that enforces a full development lifecycle on your AI agent."

- **Eigenwise Toolshed** ([r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1ukh79y/the_first_thing_i_install_in_every_claude_code/)) - "The First Thing I Install in Every Claude Code Project" - `/plugin marketplace add Eigenwise/eigenwise-toolshed /plugin install codebase-mapper@eigenwise-toolshed`

- **Nexus Memory MCP** ([r/AI_Agents](https://www.reddit.com/r/AI_Agents/comments/1u7ob9k/i_gave_my_ai_agents_a_shared_memory_via_mcp_heres/)) - shared agent memory via MCP: "the same `remember()` and `recall()` that works in Hermes also works in Claude Code, Cursor, Cline, and every other MCP-compatible agent. No per-agent plugins."

A [Reddit post](https://www.reddit.com/r/ClaudeAI/comments/1uluzt4/im_claude_my_human_had_me_refactor_my_own_config/) written as Claude described refactoring a 700-line global config into a "routing core + on-demand skills," then packaging the approach as a free open-source plugin: "We rebuilt my global config from a 700-line rules file into a routing core + on-demand skills, put the whole thing under git, and then extracted the generic lessons into a free, open-source Claude Code plugin."

[perrotta.dev documented](https://perrotta.dev/2026/06/claude-code-ship-your-skills-as-a-plugin-marketplace/) turning a personal dotfiles skill collection into an installable marketplace repo - "my Claude Code skills lived in my .dotfiles, usable only on the machine that cloned them."

Cross-platform coverage: Reddit, X, Web, Bluesky.

---

### 6. The Context Efficiency Crisis: Skills Overload Is a Real Problem

[@suraj_sharma14](https://x.com/suraj_sharma14/status/2073300779767603640)'s weekend wishlist (247 likes, the highest-engagement post in this corpus) included "Learn Claude Code + Codex workflows, Set up Hermes Agent, Set up OpenClaw, Learn loop engineering, Master MCP, Build your own MCP servers, Experiment with AI agent swarms..." - but the community pushed back on maximalism.

A [Reddit thread](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) surfaced a real cost: "At initiation, it blindly loads dozens of skill descriptions, MCP server configs, and custom rules into the prompt. I checked my session transcripts: 187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight." The poster built a CLI to selectively load skills on demand.

HN's top-engagement piece on this topic: ["Bad MCP design costs your agent 5x more tokens"](https://news.ycombinator.com/item?id=48407391) - 17 points. And [r/AI_Agents](https://www.reddit.com/r/AI_Agents/comments/1ud5qs7/maybe_your_agent_should_just_stay_simple/) bluntly: "Maybe Your Agent Should Just Stay Simple... from my experience, a poorly designed MCP can be a disaster. Token usage and execution efficiency both become worrying very quickly. Every time I consider adding a new MCP, I ask Claude to review whether the same thing can be done with a plain script instead."

[@goon_nguyen](https://x.com/goon_nguyen/status/2073197487880372437) articulated the production failure pattern: "Most agent prototypes fail at the same boring layer: not reasoning, but operations... how do we plug in MCP servers without turning context into soup?"

Cross-platform coverage: Reddit, X, HN.

---

### 7. Harness Patterns Are Becoming the Core Skill

[@github_update](https://x.com/github_update/status/2072200713808281666) (6 likes, 5 replies): "Most agent failures are not model failures. They are harness failures... A model can be highly capable and still fail inside a weak agent system." The linked piece analyzed 12 agentic harness patterns from Claude Code. Builders are shipping harnesses as reusable tools: [Shipwright Harness](https://github.com/app-vitals/shipwright) (autonomous delivery agent for Claude Code, HN 3 pts), [RondoFlow](https://github.com/rondoflow/rondoflow) (visual multi-agent orchestration, HN 5 pts), [Aharness](https://github.com/Alfredvc/aharness) (enforce coding-agent workflows as state machines on Codex), [OpenYabby](https://github.com/OpenYabby/OpenYabby) (voice-controlled multi-agent orchestrator).

[@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (558 likes, Claude Code's product lead) summed up the transformation: "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team."

Cross-platform coverage: X, HN, GitHub.

---

### 8. Security and Governance Concerns Emerging as the Ecosystem Scales

A [r/AI_Agents thread](https://www.reddit.com/r/AI_Agents/comments/1udn0jn/are_ai_agent_stacks_creating_a_new_supplychain/) surfaced what is becoming a real architectural concern: "normal SCA tools see packages, but they usually don't understand the agent composition around those packages... a scanner may tell you that a package in a lockfile has a CVE. But it usually can't say: [whether a Claude Code plugin, MCP server, or skill transitively loads it]."

The HN community spawned dedicated security tooling this month: [AgentSploit](https://github.com/agentsploit/agentsploit) ("Burp Suite for AI Agents and MCP Servers"), [agent-pd](https://github.com/varmabudharaju/agent-pd) ("A police department for your Claude Code agents," 11 pts, 8 comments), and [Diplomat-agent](https://github.com/Diplomat-ai/diplomat-agent) for scanning Python MCP servers for unguarded tool calls.

The Ghidra-MCP maintainer on GitHub ([issue #307](https://github.com/bethington/ghidra-mcp/issues/307)) wrote: "this is becoming a complex unmaintainable mess... too many tools for agents." A production bug on [Kiro](https://github.com/kirodotdev/Kiro/issues/9713): "MCP stdio servers spawn visible CMD windows on Windows" - 13 reactions, 25 comments.

Cross-platform coverage: Reddit, HN, GitHub.

---

### 9. First-Party Signal: Anthropic Shipping and Communicating Fast

[@alexalbert__](https://x.com/alexalbert__/status/2072404717490360727) celebrated (591 likes): "Welcome back to the world Fable!!" - the Fable model's return. Anthropic's formal blog post on skills/hooks/subagents (June 18) was the most-cited piece in the Web corpus. [@ameliahazelai](https://x.com/ameliahazelai/status/2073345751892062531) (165 likes, 95 reposts, 69 replies) highlighted 18 official Anthropic AI courses including "Introduction to Agent Skills" - signaling Anthropic treating skills literacy as a product education priority.

[@alexalbert__](https://x.com/alexalbert__/status/2065494053379293447) replied to a user reporting Claude Code bugs (27 likes): "We're working on a few potential fixes for this in the prompt and in future models. This is more of a stopgap until those land" - showing active iteration on behavior-level issues that skills/hooks are currently papering over.

HN flagged a notable incident: ["Claude Code is steganographically marking requests"](https://thereallo.dev/blog/claude-code-prompt-steganography) - 2,435 points, 745 comments, the highest-engagement HN thread in this corpus by far. The trust and transparency angle is intensifying as Claude Code becomes infrastructure.

Cross-platform coverage: X, HN, Web.

---

## Cross-Source Patterns

**Pattern 1: The SKILL.md format is converging as a cross-agent open standard**
- Appeared on: X, Web, GitHub, HN
- @Layton_Gott: "They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw." Microsoft's devblogs confirm SKILL.md across VS Code, Visual Studio 2026, GitHub Copilot CLI, Claude Code. An arxiv paper (Skilldex) is now formalizing the package management model.
- Key quotes: "When MSFT publishes a 'how to agent' repo, the format is becoming a standard." - [@so_sthbryan](https://x.com/so_sthbryan/status/2073394395332657298)

**Pattern 2: Context bloat from unused skills/MCP servers is a top practitioner complaint**
- Appeared on: Reddit, X, HN
- "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted." (r/ClaudeAI). "Bad MCP design costs your agent 5x more tokens." (HN). "How do we plug in MCP servers without turning context into soup?" (@goon_nguyen)
- Key quotes: "Maybe Your Agent Should Just Stay Simple" - r/AI_Agents

**Pattern 3: The harness layer is the actual product differentiator**
- Appeared on: X, HN, GitHub, Reddit
- Community is shipping reusable harness tools (Shipwright, RondoFlow, Aharness) faster than individual skills. The "agent failure" conversation has shifted from model capability to infrastructure reliability.
- Key quotes: "Most agent failures are not model failures. They are harness failures." - [@github_update](https://x.com/github_update/status/2072200713808281666)

**Pattern 4: Enterprise governance is the unsolved layer**
- Appeared on: Web (AWS blog), HN, Reddit, GitHub
- AWS, Microsoft, and open-source projects are all solving the same problem: centralized discovery and governance for scattered MCP servers and skills. No authoritative central registry exists yet.
- Key quotes: "Transform scattered MCP server chaos into governed, auditable tool access" - agentic-community/mcp-gateway-registry

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | I gave Claude Code a "lazy senior dev" mode and it writes like 6x less code | 609 | 87 | "Ask for email validation and you get a 27-line EmailValidator class..." | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3k2ed/i_gave_claude_code_a_lazy_senior_dev_mode_and_it/) |
| r/ClaudeAI | Using Claude Code? You're probably wasting ~8k tokens per session on unused skills | — | — | "187 items loaded, but I only used 4 actively" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) |
| r/ClaudeAI | I'm Claude. My human had me refactor my own config into a discipline system, then package it as a free plugin | — | 6 | "routing core + on-demand skills, put the whole thing under git" | [link](https://www.reddit.com/r/ClaudeAI/comments/1uluzt4/im_claude_my_human_had_me_refactor_my_own_config/) |
| r/ClaudeAI | Going back to work after a break. Where do I start with Claude Code? | 2 | 11 | "my team has switched to using Claude Code for almost all of their tasks" | [link](https://www.reddit.com/r/ClaudeAI/comments/1ufu1hj/going_back_to_work_after_a_break_where_do_i_start/) |
| r/ClaudeAI | I built a Claude Code plugin that makes the AI follow a real dev lifecycle | 7 | 6 | "Specsmith v0.1.1 — enforces a full development lifecycle" | [link](https://www.reddit.com/r/ClaudeAI/comments/1uihxv9/i_built_a_claude_code_plugin_that_makes_the_ai/) |
| r/ClaudeAI | The First Thing I Install in Every Claude Code Project | 1 | 5 | "/plugin marketplace add Eigenwise/eigenwise-toolshed" | [link](https://www.reddit.com/r/ClaudeAI/comments/1ukh79y/the_first_thing_i_install_in_every_claude_code/) |
| r/AI_Agents | Are AI agent stacks creating a new supply-chain blind spot? | 1 | 5 | "SCA tools see packages, but don't understand the agent composition" | [link](https://www.reddit.com/r/AI_Agents/comments/1udn0jn/are_ai_agent_stacks_creating_a_new_supplychain/) |
| r/AI_Agents | Maybe Your Agent Should Just Stay Simple | 5 | 7 | "a poorly designed MCP can be a disaster" | [link](https://www.reddit.com/r/AI_Agents/comments/1ud5qs7/maybe_your_agent_should_just_stay_simple/) |
| r/AI_Agents | I gave my AI agents a shared memory via MCP | — | 20 | "the same remember() and recall() that works in Hermes also works in Claude Code" | [link](https://www.reddit.com/r/AI_Agents/comments/1u7ob9k/i_gave_my_ai_agents_a_shared_memory_via_mcp_heres/) |
| r/AI_Agents | We're building an agent marketplace. But we got wrong about agents first | — | — | "what kinds of agents do people actually need?" | [link](https://www.reddit.com/r/AI_Agents/comments/1u1350w/were_building_an_agent_marketplace_but_we_got/) |
| r/ClaudeAI | I built an MCP for HuggingFace publish workflows | 1 | 5 | "unsure about how to do proper model cards, tagging, etc." | [link](https://www.reddit.com/r/ClaudeAI/comments/1uii9u8/i_built_an_mcp_for_huggingface_publish_workflows/) |
| r/AI_Agents | When you build a killer custom agent but none of your friends know what an agent is | 2 | 5 | "They don't run Claude Code or CodeX, and they refuse to install anything" | [link](https://www.reddit.com/r/AI_Agents/comments/1u3ul9r/when_you_build_a_killer_custom_agent_but_none_of/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 558 | 15 | [link](https://x.com/alexalbert__/status/2069470389391241314) |
| @alexalbert__ | "Welcome back to the world Fable!!" | 591 | 10 | [link](https://x.com/alexalbert__/status/2072404717490360727) |
| @suraj_sharma14 | "f*ck your weekend plans. You NEED to: Learn Claude Code, Set up Hermes, Master MCP, Build your own MCP servers..." | 247 | 22 | [link](https://x.com/suraj_sharma14/status/2073300779767603640) |
| @ameliahazelai | "Claude is offering 18 official AI courses with certificates. And it's 100% free" | 165 | 95 | [link](https://x.com/ameliahazelai/status/2073345751892062531) |
| @SuperteamBR | "Our beloved solana-claude is now Solana AI Kit - 18 expert skill submodules, 15 agents + 29 commands" | 131 | 25 | [link](https://x.com/SuperteamBR/status/2067364640401789399) |
| @Tork_Lab | "BREAKING: X just made a major move for AI builders. The platform now supports hosted MCP servers" | 56 | — | [link](https://x.com/Tork_Lab/status/2073240381802905624) |
| @DanKornas | "Claude Code: Everything You Need to Know - practical GitHub guide organizing around skills, hooks, subagents, MCP" | 15 | 6 | [link](https://x.com/DanKornas/status/2073566017595314660) |
| @coder_surya | "13 Free Courses by Anthropic - 100% free" | 16 | 4 | [link](https://x.com/coder_surya/status/2073670716466008415) |
| @so_sthbryan | "Microsoft ships an official skills repo. When MSFT publishes a 'how to agent' repo, the format is becoming a standard." | — | — | [link](https://x.com/so_sthbryan/status/2073394395332657298) |
| @stretchcloud | "The part of the open-source coding agent story that gets underreported is the ecosystem forming around it. OpenCode hit 160,000 GitHub stars" | 1 | 1 | [link](https://x.com/stretchcloud/status/2072974880963023113) |
| @Layton_Gott | "Skills have a HUGE impact in AI coding right now... A skill is just a markdown file with a dialed-in prompt essentially" | 6 | 1 | [link](https://x.com/Layton_Gott/status/2073125199030157540) |
| @goon_nguyen | "Most agent prototypes fail at the same boring layer: not reasoning, but operations" | 1 | — | [link](https://x.com/goon_nguyen/status/2073197487880372437) |
| @github_update | "Most agent failures are not model failures. They are harness failures." | 6 | — | [link](https://x.com/github_update/status/2072200713808281666) |
| @alexalbert__ | "@NeroHSN We're working on a few potential fixes for this in the prompt and in future models" | 27 | — | [link](https://x.com/alexalbert__/status/2065494053379293447) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| nastynate | Claude Code is steganographically marking requests | 2,435 | 745 | — | [link](https://thereallo.dev/blog/claude-code-prompt-steganography) |
| handfuloflight | ZCode: Claude Code from the Makers of GLM | 277 | 15 | — | [link](https://zcode.z.ai/cn) |
| coloneltcb | The Safari MCP server for web developers | 267 | 75 | — | [link](https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/) |
| kirushik | Claude Code is steganographically marking requests | 2,435 | 745 | — | [link](https://thereallo.dev/blog/claude-code-prompt-steganography) |
| ayi | Ask HN: Anthropic banned me from using Claude Code | 82 | 94 | — | [link](https://news.ycombinator.com/item?id=48641160) |
| muhammad-shafat | Show HN: Stop returning raw JSON from MCP servers, build rich inline UIs | 11 | 5 | — | [link](https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3) |
| softie123 | Show HN: A police department for your Claude Code agents | 11 | 8 | — | [link](https://github.com/varmabudharaju/agent-pd/blob/master/README.md) |
| JohnnyZhang483 | Bad MCP design costs your agent 5x more tokens | 17 | 1 | — | [link](https://news.ycombinator.com/item?id=48407391) |
| vorticotech | How to build and serve MCP servers without effort | 15 | — | — | [link](https://flama.dev/blog/building_an_mcp_server_with_flama/) |
| arzzen | Show HN: Visual multi-agent orchestration for Claude Code (RondoFlow) | 5 | — | — | [link](https://github.com/rondoflow/rondoflow) |
| idovmamane | Show HN: OpenYabby, voice-controlled multi-agent orchestrator for Claude Code | 8 | — | — | [link](https://github.com/OpenYabby/OpenYabby) |
| pjungwir | My Claude Code Setup | 11 | 1 | — | [link](https://illuminatedcomputing.com/posts/2026/06/my-claude-code-setup/) |
| dodizzle | Shipwright Harness - open-source autonomous delivery agent for Claude Code | 3 | — | — | [link](https://github.com/app-vitals/shipwright) |
| selcuk | Show HN: Namecom-CLI - CLI and agent skill so Claude Code/Codex can do your DNS | 4 | — | — | [link](https://github.com/hypersocialinc/namecom-cli) |
| barakolshe | Claude Code Issue management extension for VS Code | 3 | 1 | — | [link](https://www.forq.ink/) |
| Bridgexapi | The SDK Is for Developers. The MCP Server Is for Agents | 3 | — | — | [link](https://blog.bridgexapi.io/the-sdk-is-for-developers-the-mcp-server-is-for-agents) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @probbrain.bsky.social | "AWS releases official MCP servers, skills, and plugins enabling AI agents to bu..." | 1 | [link](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! Most likely older plugins could be ported over relatively easily." | 6 | [link](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) |
| @mikaelbuilds.bsky.social | "Claude Code 'still running' is not one bug. I built a no-secret packet for v2.1.179-style remote failures..." | 1 | [link](https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w) |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | [link](https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claude.com | [Steering Claude Code: skills, hooks, rules, subagents and more](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more) | Official Anthropic overview of all 7 extension methods (June 18, 2026) |
| mcsaguru.com | [Claude Code Plugins vs Skills vs MCP Explained](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) | Three-layer taxonomy; which layer to use when |
| mcsaguru.com | [Install Claude Code Plugins + Add a Marketplace](https://mcsaguru.com/install-claude-code-plugins-marketplace-guide) | Step-by-step plugin install and marketplace setup |
| ccforeveryone.com | [Claude Code Skills vs Agents, MCP, and Plugins, Explained](https://ccforeveryone.com/guides/claude-code-concepts-explained) | Plain-English definitions of all four extension types |
| tygartmedia.com | [Claude Skills vs MCP vs Connectors vs Plugins: What Each One Is](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) | AI strategy perspective on the taxonomy |
| dev.to | [The MCP Gateway Pattern: Managing 13,000+ Servers Without Losing Your Mind](https://dev.to/mrclaw207/the-mcp-gateway-pattern-managing-13000-servers-without-losing-your-mind-4an6) | Gateway pattern for enterprise MCP governance |
| dev.to | [Skill, MCP, Plugin, or just a CLI: how I pick a Claude Code extension, lightest first](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) | Decision framework; nested tool logic and security pitfalls |
| dev.to | [Build Your Own Claude Code Marketplace](https://dev.to/nagell/build-your-own-claude-code-marketplace-scaffold-structure-and-auto-updates-4n3f) | How to scaffold and publish a Claude Code marketplace |
| explainx.ai | [How to Build Your First Agent Skill (SKILL.md Tutorial, 2026)](https://explainx.ai/blog/how-to-build-your-first-agent-skill-step-by-step-2026) | Step-by-step SKILL.md tutorial |
| getclaudekit.com | [Claude Skills: Reusable Workflows](https://getclaudekit.com/blog/guide/mechanics/claude-skills-guide) | Anatomy of a skill; auto-activation frontmatter |
| hidekazu-konishi.com | [Claude Code Skills Complete Guide - Creating, Testing, and Distributing](https://hidekazu-konishi.com/entry/claude_code_skills_complete_guide.html) | Deep dive: create, test, and distribute skills |
| claudecodeclub.ai | [Claude Code Skills, Subagents, MCP, and Hooks: When to Use Each](https://www.claudecodeclub.ai/blog/claude-code-skills-subagents-mcp-hooks-when-to-use) | Decision tree for choosing extension type |
| perrotta.dev | [claude code: ship your skills as a plugin marketplace](https://perrotta.dev/2026/06/claude-code-ship-your-skills-as-a-plugin-marketplace/) | Personal dotfiles to shareable marketplace walkthrough |
| morphllm.com | [Claude Code Plugins and Marketplaces: Install, Build, and Publish](https://www.morphllm.com/claude-code-marketplace) | Plugin structure, marketplace.json, publish workflow |
| rywalker.com | [Claude Plugin Marketplace research](https://rywalker.com/research/claude-plugin-marketplace) | 222 plugin entries as of June 11; distribution moat analysis |
| solana.garden | [LLM Agent MCP Tool Server Integration Production Systems Explained](https://solana.garden/guides/llm-agent-mcp-tool-server-integration-production-systems-explained/) | Connection pools, capability registry, tenant-scoped auth |
| aws.amazon.com | [Governing AI Assets at Scale with MCP Gateway and Registry](https://aws.amazon.com/blogs/opensource/governing-ai-assets-at-scale-with-mcp-gateway-and-registry/) | Enterprise governance of MCP assets via AWS |
| morphllm.com | [Claude Code Skills vs MCP vs Plugins: Complete Guide 2026](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Most cited comparison guide |
| agensi.io | [Every AI Agent Skills Marketplace and Directory in 2026](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Comprehensive marketplace landscape review |
| totalum.app | [Agent Skills Marketplace in 2026: Anthropic vs Vercel vs OpenAI vs Cline vs MCP Compared](https://www.totalum.app/blog/agent-skills-marketplaces-2026) | June 2026 convergence event analysis |
| github.com/microsoft/skills | [microsoft/skills](https://github.com/microsoft/skills) | 2.4k stars; AGENTS.md + Skills + MCP for Copilot, Claude Code, SDK agents |
| arxiv.org | [Skilldex: Package Manager and Registry for Agent Skill Packages](https://arxiv.org/html/2604.16911v1) | Academic proposal for hierarchical scope-based skill distribution |
| devblogs.microsoft.com | [Extend your coding agent with .NET Skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/) | SKILL.md as open standard across VS 2026, GitHub Copilot, Claude Code |
| aws.amazon.com | [AWS Agent Registry preview announcement](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | Private governed catalog for agents, skills, MCP servers via Bedrock AgentCore |
| tooldirectory.ai | [The state of MCP servers in 2026](https://tooldirectory.ai/blog/state-of-mcp-servers-2026) | 13,000+ servers, 97M monthly downloads; discovery is the bottleneck |
| medium.com/@amiarora | [Solving the MCP Tool Discovery Problem](https://medium.com/@amiarora/solving-the-mcp-tool-discovery-problem-how-ai-agents-find-what-they-need-b828dbce2c30) | Semantic search as solution for MCP tool discovery |
| rywalker.com | [Claude Plugin Marketplace research](https://rywalker.com/research/claude-plugin-marketplace) | 222 plugin entries; six-figure installs for top plugins |

---

## Stats Block

```
├─ 🟠 Reddit: 20 threads │ 716 upvotes │ 272 comments
├─ 🔵 X: 19 posts │ 1,851 likes │ 185 reposts
├─ 🟢 HN: 25 stories │ 3,191 points │ 949 comments
├─ 🦋 Bluesky: 4 posts │ 10 likes │ 1 repost
├─ 🐙 GitHub: 24 items │ 917 reactions │ 688 comments
├─ 🌐 Web: 29 pages (19 engine + 10 WebSearch)
└─ 🗣️ Top voices: @alexalbert__, @suraj_sharma14, @SuperteamBR │ r/ClaudeAI, r/AI_Agents
```

---

## Data Gaps

- **YouTube/TikTok/Instagram**: Zero results from all three sources due to HTTP 402 errors from ScrapeCreators (payment required). These platforms likely have walkthrough content on skills and MCP setup that is not represented in this briefing.
- **Polymarket**: No prediction markets found for this topic area.
- **Bluesky**: Only 4 posts - low coverage; the Bluesky developer community is likely more active on X.
- **Freshness**: Only 30 of 111 dated engine items are from the last 7 days; most content is from mid-June 2026. Coverage is biased toward the June 10-18 "taxonomy documentation" wave rather than the most recent July 2026 developments.
- **Approximate coverage**: 5/5 core sources (Reddit, X, HN, GitHub, Web). Bonus sources (TikTok, Instagram, YouTube, Polymarket) returned 0 items. Bluesky returned 4. Estimated overall coverage: ~65-70% of public English-language discussion.
- **Noise**: GitHub items include some off-topic PRs (WebKit shared-memory, unrelated repo maintenance) due to keyword matching on "agent" and "MCP" without GitHub auth to filter more precisely.

---

## Key Quotes

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." - [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) on X (558 likes)

> "Most agent failures are not model failures. They are harness failures." - [@github_update](https://x.com/github_update/status/2072200713808281666) on X (6 likes)

> "Skills have a HUGE impact in AI coding right now... A skill is just a markdown file with a dialed-in prompt essentially. They work in basically everything. Claude Code, Codex, Cursor, Hermes, OpenClaw." - [@Layton_Gott](https://x.com/Layton_Gott/status/2073125199030157540) on X (6 likes)

> "Most agent prototypes fail at the same boring layer: not reasoning, but operations. The prompt looks fine. The demo works. Then production asks ugly questions: where does session state live? How do we plug in MCP servers without turning context into soup?" - [@goon_nguyen](https://x.com/goon_nguyen/status/2073197487880372437) on X

> "187 items loaded, but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate." - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) thread on unused skills

> "When MSFT publishes a 'how to agent' repo, the format is becoming a standard." - [@so_sthbryan](https://x.com/so_sthbryan/status/2073394395332657298) on X, on microsoft/skills

> "a poorly designed MCP can be a disaster. Token usage and execution efficiency both become worrying very quickly. Every time I consider adding a new MCP, I ask Claude to review whether the same thing can be done with a plain script instead." - [r/AI_Agents](https://www.reddit.com/r/AI_Agents/comments/1ud5qs7/maybe_your_agent_should_just_stay_simple/)

> "The part of the open-source coding agent story that gets underreported is the ecosystem forming around it. OpenCode hit 160,000 GitHub stars... the guide structure that's emerging: agents, skills, plugins, MCP integrations, headless CI runs, custom model routing - that is the same layered architecture that Claude Code, GitHub Copilot, and Cursor are building toward." - [@stretchcloud](https://x.com/stretchcloud/status/2072974880963023113) on X

> "my Claude Code skills lived in my .dotfiles, usable only on the machine that cloned them. I wanted them to be installable anywhere with one command, so that my teammates could easily adopt them." - [perrotta.dev](https://perrotta.dev/2026/06/claude-code-ship-your-skills-as-a-plugin-marketplace/) on the distribution problem that drove marketplace creation

> "We rebuilt my global config from a 700-line rules file into a routing core + on-demand skills, put the whole thing under git, and then extracted the generic lessons into a free, open-source Claude Code plugin for people who build software by prompting AI but have no dev background." - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1uluzt4/im_claude_my_human_had_me_refactor_my_own_config/) (written as Claude)
