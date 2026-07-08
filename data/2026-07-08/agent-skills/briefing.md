# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-08
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 3 threads | 1,346 upvotes, 213 comments | r/ClaudeAI, r/LocalLLaMA |
| X/Twitter | 26 posts | 9,145 likes, 872 reposts | Heavy practitioner + official traffic |
| Hacker News | 23 stories | 4,315 points, 2,170 comments | Mix of ecosystem news + security stories |
| Bluesky | 4 posts | 10 likes | Light volume; niche developer audience |
| GitHub | 13 items | 813 reactions, 409 comments | anthropics/claude-plugins-official, PostHog, etc. |
| Web | 32 pages | — | Engine (20) + WebSearch supplements (12) |

---

## Synthesized Findings

### 1. Anthropic's Plugin Marketplace Has Become Infrastructure

The official Anthropic-managed directory — [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) — now has **31,606 GitHub stars**, ships 101 vetted plugins, and hosts 68 partner plugins from GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, and Firebase. The community-curated counterpart at [claudemarketplaces.com](https://claudemarketplaces.com/) claims 21,700+ skills, 2,500+ marketplaces, and 12,500+ MCP servers, with 300,000+ monthly developers. A third-party open-source list — [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) — catalogs 425 plugins, 2,810 skills, and 200 agents with the `ccpi` CLI package manager and a companion site at tonsofskills.com.

The distribution mechanism is now formalized: plugins bundle skills, hooks, MCP server configs, subagents, slash commands, and LSP definitions into one installable package with `/plugin install`. A developer writing at [perrotta.dev](https://perrotta.dev/2026/06/claude-code-ship-your-skills-as-a-plugin-marketplace/) described converting their personal dotfiles skills into a one-command installable marketplace: "Claude Code reads skills from a marketplace, which is essentially a git repo with a manifest."

Organizational plugin management is now a named Anthropic feature. [Claude's help center documents](https://support.claude.com/en/articles/13837433-manage-plugins-for-your-organization) it explicitly. Claude Code also added a `renames map` to `marketplace.json` to transparently migrate users off renamed plugin slugs rather than throwing plugin-not-found errors — a sign of ecosystem maturity and commitment to stability.

### 2. The claude-code-setup Plugin Is the Entry Point Everyone Is Talking About

A cluster of X posts on July 7-8 circled the same Anthropic-published plugin: **claude-code-setup**, which scans a project and recommends exactly which hooks, skills, MCP servers, and subagents to activate. [@ParamSiddh](https://x.com/ParamSiddh/status/2074487745897210020) put it plainly: "Claude Code without setup is half of what it can be... It analyzes your project and tells you exactly which hooks, skills, MCP servers, and subagents to activate. You no longer have to guess anything." [@jeroenvonk_](https://x.com/jeroenvonk_/status/2074750339664818453) noted the read-only advisory posture: "New official Anthropic plugin scans your codebase and recommends which Claude Code hooks, skills, MCP servers and subagents to turn on. Read-only: it advises, you decide."

This is meaningful because it signals Anthropic's position: Claude Code's default install is intentionally sparse, and the plugin layer is the intended vehicle for tailoring. The setup plugin is the onramp.

### 3. Skills Absorbed Slash Commands — Anthropic Published the Taxonomy

On June 18, Anthropic published "[Steering Claude Code: skills, hooks, subagents and more](https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more)" — the canonical seven-method breakdown of how to customize Claude Code's behavior. [ClaudeKit confirmed](https://getclaudekit.com/blog/guide/mechanics/custom-skills-vs-commands) the quiet API merge: "Custom commands have merged into skills — here's how the modern slash command works and why skills are the format to use now." Skills are now the single canonical unit for behavioral customization within context.

The community has generated a wave of decision-tree guides working out the taxonomy. The clearest formulation comes from [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) (July 5): "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." The meme formulation from [duet.so](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills): **"MCPs are verbs. Skills are playbooks."**

[@0xCristal](https://x.com/0xCristal/status/2074457104866218124) captured the wider community shift: "MOST PEOPLE USE CLAUDE CODE LIKE A CHATBOT. IT'S ACTUALLY A FULL OPERATING SYSTEM FOR AI AGENTS."

### 4. The Five MCP Servers That Practitioners Actually Install

[@GuntherWrite](https://x.com/GuntherWrite/status/2074728248848654448) published a practical stack framed as "the five things Claude Code is bad at alone" — generating the most concrete consensus signal of the week: **1. Perplexity MCP** (live web research), **2. Playwright MCP** (browser control, forms, app testing), **3. Firecrawl MCP** (turning websites into usable context), **4. Glif MCP** (image and AI workflows), **5. Chrome DevTools MCP** (page inspection and debugging). [@socialwithaayan](https://x.com/socialwithaayan/status/2074509637693403190) posted "the complete guide to claude mcp connectors" to 90 likes. [@Blum_OG](https://x.com/Blum_OG/status/2044875559059210460) listed GitHub, Sequential Thinking, Memory, Slack, and AWS as essentials.

The broader ecosystem has 14,000+ MCP servers available (up from 12,500+ in the community directory). Protocol governance moved to the Linux Foundation. The April 2026 Claude Code update raised per-result MCP tool output to 500,000 characters and enabled concurrent MCP server connections. MCP Tool Search and lazy loading — loading tool definitions on demand — reduced context usage by up to 95%.

PostHog's engineering PR "[feat(skills): Claude Code & Codex plugin marketplace + zip export](https://github.com/PostHog/posthog/pull/64385)" is a production signal: they're building internal skill stores with the observation that "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams."

### 5. Cross-Platform Reuse: Skills and MCP Servers Are No Longer Claude-Only

[@N0V4Dev](https://x.com/N0V4Dev/status/2074788240821821895) articulated the multi-client future clearly: "Packaging domain expertise into reusable containers is a great way to steer AI coding agents. Agent Plugins for AWS uses structured skills and MCP servers to handle architecture and deployment tasks. It's currently built to work with Claude Code, Codex, and Cursor." A "local-first gateway" approach discussed by [@btsouth](https://x.com/btsouth/status/2074491372497768633): a proxy that sits between AI clients and MCP servers so you "set up and authenticate each MCP server once, and every AI client (Claude, Cursor, VS Code, Codex and the rest) shares it."

[@probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) noted on Bluesky: "AWS releases official MCP servers, skills, and plugins enabling AI agents to build." The cross-client standard is solidifying: plugins are increasingly authored for the Claude Code format but running across the agentic IDE ecosystem.

### 6. Security Is the Unresolved Shadow Over the MCP Ecosystem

Two HN stories from late June dominated engagement and surfaced a trust crisis in the Claude Code ecosystem. "[Claude Code is steganographically marking requests](https://thereallo.dev/blog/claude-code-prompt-steganography)" (2,444 pts, 747 comments) and "[Anthropic has embedded hidden spyware-like code in Claude Code](https://twitter.com/IntCyberDigest/status/2071971609183678544)" (56 pts) ran days apart, followed by "[Alibaba to ban Claude Code in workplace over alleged backdoor risks, source says](https://www.reuters.com/world/china/alibaba-ban-claude-code-workplace-over-alleged-backdoor-risks-source-says-2026-07-03/)" (336 pts, 279 comments, via Reuters).

The MCP layer has its own independent security problem. A 2026 audit found that 40% of MCP servers require no authentication, 43% carry command-injection vulnerabilities, and 79% handle credentials in plaintext. In April 2026, a systemic RCE vulnerability in MCP SDK's stdio transport was disclosed, affecting Python, TypeScript, Java, and Rust SDKs, touching ~150M+ downloads across 7,000+ public servers. On GitHub, an issue "[Show HN: Diplomat-agent scan Python MCP servers for unguarded tool calls](https://github.com/Diplomat-ai/diplomat-agent)" appeared on HN as a response. [@rishiamar](https://x.com/rishiamar/status/2074351474537042276) summarized enterprise anxiety: "Developers running Claude Code. No policy. MCP servers connecting to external services IT hasn't reviewed."

From the [Ghidra MCP project](https://github.com/bethington/ghidra-mcp/issues/307): "this project is just not in an ok state... too many tools for agents." A real signal that tool sprawl in MCP servers is a quality problem the ecosystem hasn't solved.

### 7. The Economics of the Plugin Ecosystem: Free Backends, 5x Cost Hikes, Training Data Concerns

Three economic threads ran in parallel. First, the free-backend workaround: [@cyrilXBT](https://x.com/cyrilXBT/status/2074780645499486223) (48 likes, 6 reposts): "CLAUDE CODE IS FREE TO INSTALL. THE TRICK IS WHAT YOU POINT IT AT... Skills, MCP servers, subagents, hooks — identical [on free backends]." OpenRouter, Gemini free tier, and Ollama are cited. Second, cost pressure: "[Claude Code Just Got 5x More Expensive](https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/)" landed on HN (57 pts), and a competing story "[Codex rate-limit cost per token jumped ~10-20x since June 16](https://github.com/openai/codex/issues/28879)" hit GitHub (544 reactions, 201 comments), suggesting cross-platform token economics are a user pain point.

Third, a data-sovereignty concern: the top Reddit thread of the period from [r/LocalLLaMA](https://www.reddit.com/r/LocalLLaMA/comments/1u795pb/donate_your_coding_sessions_to_an_open_ccby40/) (1,344 upvotes, 211 comments) launched "Trace Commons," an initiative to donate coding sessions as CC-BY-4.0 datasets: "Anthropic and OpenAI are getting so much data from the Claude Code and Codex usage, and I'm quite scared this will create an oligopoly because only their models will be trained on it, leaving the open-weight and open source models behind."

### 8. Community Projects Showcase the Breadth of What Plugins Can Do

The "Show HN" stream in June-July demonstrates real hobbyist/practitioner creativity: [Claudoro](https://github.com/emson/claudoro) (Pomodoro timer embedded in the Claude Code statusline, 50 pts, 36 comments), [statuslin.es](https://statuslin.es) (community library of custom Claude Code status lines, low points but high novelty), [Shellular](https://shellular.dev/) (run Claude Code from your phone, 32 pts, 28 comments), [Peek-CLI](https://github.com/puffinsoft/peek-cli) (browser visibility for Claude Code), [TS Compiler Graph MCP](https://github.com/samchon/ttsc/tree/master/packages/graph) ("10x Fewer Tokens in Claude Code and Codex"), and a free [Claude/Anthropic news RAG MCP server](https://claudenews.online).

[@uermel.bsky.social](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) noted on Bluesky: "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting... Most likely older plugins could be ported over that way relatively easily." Plugin authorship itself is becoming an agentic task.

Anthropic also dropped 13 free AI courses with certificates, including "[Introduction to Agent Skills](https://x.com/AiwithDharmik/status/2074495398874624154)" and "Introduction to Model Context Protocol" — a signal that skill authorship is being normalized as a developer competency.

---

## Cross-Source Patterns

**Pattern 1: The ecosystem is maturing from experiment to infrastructure** — appearing on X, HN, Web, GitHub. The official marketplace with 31,606 stars, organizational plugin management docs, plugin slug versioning/renames, and partner plugins from Stripe/Figma/Vercel signal that Anthropic is treating this as a product surface, not a developer preview. PostHog's production PR building an internal skill store and the r/LocalLLaMA dataset concern both treat Claude Code's data gravity as already established. Key voices: [@claudeai](https://x.com/claudeai/status/2074244664199115201), [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official), [PostHog](https://github.com/PostHog/posthog/pull/64385).

**Pattern 2: Security debt is accumulating faster than the tooling can address it** — appearing on HN, X, GitHub, Web. The steganography story (2,444 HN pts), Alibaba ban (Reuters), the 40% no-auth MCP audit, the April 2026 RCE, and enterprise IT concerns from [@rishiamar](https://x.com/rishiamar/status/2074351474537042276) form a coherent warning. The community is building security tooling (Diplomat-agent, AgentSploit) but these are early. The problem is structural: MCP's permissive design and the speed of ecosystem growth outpaced security review norms. Key sources: [thereallo.dev](https://thereallo.dev/blog/claude-code-prompt-steganography), [Reuters](https://www.reuters.com/world/china/alibaba-ban-claude-code-workplace-over-alleged-backdoor-risks-source-says-2026-07-03/), [OWASP GenAI](https://genai.owasp.org/resource/a-practical-guide-for-secure-mcp-server-development/).

**Pattern 3: Cross-client portability is becoming real** — appearing on X, Bluesky, Web. Agent Plugins for AWS runs on Claude Code, Codex, and Cursor. The local MCP gateway pattern (one auth, all clients). The "Steering Claude Code" Anthropic blog explicitly covers seven customization surfaces. This is a shift from Claude-specific to agentic-IDE-standard. Key voices: [@N0V4Dev](https://x.com/N0V4Dev/status/2074788240821821895), [@btsouth](https://x.com/btsouth/status/2074491372497768633), [@probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f).

**Pattern 4: "Resource Bible" content is the most shared format** — appearing on X. [@AiwithDharmik](https://x.com/AiwithDharmik/status/2074701028499550480)'s "Claude Code Resource Bible" (73 likes, 41 reposts) — a curated list of 54 tools with three best links per section — outperformed technical deep-dives. The community appetite is for curation, not explanations: practitioners want pointers to the three best MCP servers for each use case, not another "what is MCP" post.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/LocalLLaMA | Donate your coding sessions to an open CC-BY-4.0 dataset | 1,344 | 211 | "Anthropic and Open AI are getting so much data from Claude Code and Codex usage, and I'm quite scared this will create an oligopoly" | https://www.reddit.com/r/LocalLLaMA/comments/1u795pb/donate_your_coding_sessions_to_an_open_ccby40/ |
| r/ClaudeAI | What's the point of Cowork when you have Claude Code? | 1 | 1 | "Claude Code turned out to be far more capable and flexible" | https://www.reddit.com/r/ClaudeAI/comments/1uq109i/whats_the_point_of_cowork_when_you_have_claude/ |
| r/ClaudeAI | I Built a 24/7 AI talk radio station with Claude Code | 1 | 1 | "I have a hard time falling asleep and wanted good, clean, funny talk radio" | https://www.reddit.com/r/ClaudeAI/comments/1uqfoel/i_built_a_247_ai_talk_radio_station_with_claude/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @claudeai | "We've put together a short history of how Claude Code came to be" | 4,342 | 461 | https://x.com/claudeai/status/2074244664199115201 |
| @AnthropicAI | "The J-space lets us read, audit, and shape what Claude is actively thinking about" | 889 | 66 | https://x.com/AnthropicAI/status/2074185387577094398 |
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 557 | 15 | https://x.com/alexalbert__/status/2069470389391241314 |
| @AiwithDharmik | "Claude just dropped 13 FREE AI courses (with certificates). Introduction to Agent Skills..." | 186 | 81 | https://x.com/AiwithDharmik/status/2074495398874624154 |
| @cyrilXBT | "CLAUDE CODE IS FREE TO INSTALL. THE TRICK IS WHAT YOU POINT IT AT." Skills/MCP/subagents work on free backends | 48 | 6 | https://x.com/cyrilXBT/status/2074780645499486223 |
| @AiwithDharmik | "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation." | 73 | 41 | https://x.com/AiwithDharmik/status/2074701028499550480 |
| @socialwithaayan | "the complete guide to claude mcp connectors" | 90 | 13 | https://x.com/socialwithaayan/status/2074509637693403190 |
| @0xCristal | "MOST PEOPLE USE CLAUDE CODE LIKE A CHATBOT. IT'S ACTUALLY A FULL OPERATING SYSTEM FOR AI AGENTS." | 22 | 1 | https://x.com/0xCristal/status/2074457104866218124 |
| @ParamSiddh | "Claude Code without setup is half of what it can be... install claude-code-setup" | 10 | 0 | https://x.com/ParamSiddh/status/2074487745897210020 |
| @GuntherWrite | "5 MCP Servers You Need in Claude: Perplexity, Playwright, Firecrawl, Glif, Chrome DevTools" | 8 | 0 | https://x.com/GuntherWrite/status/2074728248848654448 |
| @N0V4Dev | "Packaging domain expertise into reusable containers... Agent Plugins for AWS... works with Claude Code, Codex, and Cursor" | 0 | 0 | https://x.com/N0V4Dev/status/2074788240821821895 |
| @jeroenvonk_ | "New official Anthropic plugin scans your codebase and recommends which Claude Code hooks, skills, MCP servers and subagents to turn on. Read-only: it advises, you decide." | 1 | 0 | https://x.com/jeroenvonk_/status/2074750339664818453 |
| @rishiamar | "Developers running Claude Code. No policy. MCP servers connecting to external services IT hasn't reviewed." | 1 | 0 | https://x.com/rishiamar/status/2074351474537042276 |
| @btsouth | "local-first gateway that sits between your AI clients and your MCP servers... every AI client (Claude, Cursor, VS Code, Codex) shares it" | 1 | 0 | https://x.com/btsouth/status/2074491372497768633 |
| @ClaudeCodeLog | "Claude Code CLI 2.1.203 changelog: Added session's working directories to MCP roots/list" | 20 | 0 | https://x.com/ClaudeCodeLog/status/2074605317816463405 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kirushik | Claude Code is steganographically marking requests | 2,444 | 747 | — | https://thereallo.dev/blog/claude-code-prompt-steganography |
| engmarketer | I used Claude Code to get a second opinion on my MRI | 565 | 714 | — | https://antoine.fi/mri-analysis-using-claude-code-opus |
| nsoonhui | Alibaba to ban Claude Code in workplace over alleged backdoor risks | 336 | 279 | — | https://www.reuters.com/world/china/alibaba-ban-claude-code-workplace-over-alleged-backdoor-risks-source-says-2026-07-03/ |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 326 | 225 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| handfuloflight | ZCode: Claude Code from the Makers of GLM | 278 | 15 | — | https://zcode.z.ai/cn |
| vincent_s | Claude Code Just Got 5x More Expensive | 57 | 8 | — | https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/ |
| kanamekun | The Making of Claude Code | 55 | 28 | — | https://www.anthropic.com/features/making-of-claude-code |
| emson | Show HN: Claudoro, Pomodoro timer embedded in the Claude Code statusline | 50 | 36 | — | https://github.com/emson/claudoro |
| sherlock-holmes | Show HN: Shellular – run Claude Code, Codex, Pi from your phone | 32 | 28 | — | https://shellular.dev/ |
| muhammad-shafat | Show HN: Stop returning raw JSON from MCP servers, build rich inline UIs | 11 | 5 | — | https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3 |
| vorticotech | How to build and serve MCP servers without effort | 15 | 0 | — | https://flama.dev/blog/building_an_mcp_server_with_flama/ |
| piotrgrudzien | Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | 0 | — | https://quickchat.ai/post/expose-ai-agent-as-mcp-server |
| autobe | Show HN: I Made TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | 0 | — | https://github.com/samchon/ttsc/tree/master/packages/graph |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @probbrain.bsky.social | "AWS releases official MCP servers, skills, and plugins enabling AI agents to build..." | 1 | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @mikaelbuilds.bsky.social | "Claude Code 'still running' is not one bug. I built a no-secret packet for v2.1.179-style remote failures" | 1 | https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w |
| @toyinariyo.bsky.social | "There are also many Godot AI plugins that can be used with Claude Code and Codex." | 2 | https://bsky.app/profile/toyinariyo.bsky.social/post/3mnxdy4p6bc2d |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering | https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills | Official definition of Agent Skills; 30-50 tokens vs MCP's 50k+ |
| Claude Blog | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | Canonical 7-method customization taxonomy (June 18, 2026) |
| Claude Blog | https://claude.com/blog/skills-explained | First-party skills vs prompts vs Projects vs MCP vs subagents |
| Claude Help Center | https://support.claude.com/en/articles/13837433-manage-plugins-for-your-organization | Org-level plugin management documentation |
| anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | 31,606 stars; official Anthropic-managed plugin registry |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 21,700+ skills, 12,500+ MCP servers community directory |
| designrevision.com | https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents | Four-way decision guide (July 7) |
| startdebugging.net | https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/ | Canonical decision rule: skill vs subagent vs MCP |
| perrotta.dev | https://perrotta.dev/2026/06/claude-code-ship-your-skills-as-a-plugin-marketplace/ | How-to: turn dotfiles skills into a distributable marketplace |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_plugins_complete_guide.html | Complete guide to bundling skills/hooks/agents/MCP for team distribution |
| getclaudekit.com | https://getclaudekit.com/blog/guide/mechanics/custom-skills-vs-commands | Confirms custom slash commands merged into skills |
| arte.itlibra.com | https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace | Plugin structure, use, build, publish lifecycle |
| duet.so | https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills | "MCPs are verbs. Skills are playbooks." |
| tim-schipper.nl | https://tim-schipper.nl/en/blog/skill-subagent-hook-or-slash-command | All seven Claude Code behavior layers; teams reach for wrong one |
| levelup.gitconnected.com | https://levelup.gitconnected.com/skills-and-mcp-how-to-build-agent-capabilities-that-actually-scale-1eafff1de5e4 | How to build agent capabilities that scale |
| andrew.ooo | https://andrew.ooo/answers/claude-code-background-sub-agents-vs-skills-vs-dynamic-workflows-june-2026/ | Background sub-agents vs skills vs dynamic workflows decision guide |
| OWASP GenAI | https://genai.owasp.org/resource/a-practical-guide-for-secure-mcp-server-development/ | 40% no-auth; 43% command injection; April 2026 RCE in stdio |
| masterprompting.net | https://masterprompting.net/blog/best-mcp-servers-2026-complete-guide | The 25 best MCP servers in 2026 |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Plugins: from personal setup to org standard |
| nimbalyst.com | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | Best MCP servers for Claude Code (ranked and tested) |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | Complete 2026 MCP & plugins guide; Linux Foundation governance |
| ai-tldr.dev | https://ai-tldr.dev/learn/ai-agents/model-context-protocol/mcp-tools-resources-prompts/ | MCP's three primitives: tools, resources, prompts |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Practical extension decision framework: lightest-first |
| mcsaguru.com | https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained | Plugins/skills/MCP layering explainer |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | Skills vs MCP vs Connectors vs Plugins: what each one is |
| developersdigest.tech | https://www.developersdigest.tech/blog/claude-agents-vs-skills | Agents vs skills decision table |

---

## Stats Block

```
├─ 🟠 Reddit: 3 threads │ 1,346 upvotes │ 213 comments
├─ 🔵 X: 26 posts │ 9,145 likes │ 872 reposts
├─ 🟢 HN: 23 stories │ 4,315 points │ 2,170 comments
├─ 🦋 Bluesky: 4 posts │ 10 likes │ 1 repost
├─ 🐙 GitHub: 13 items │ 813 reactions │ 409 comments
├─ 🌐 Web: 32 pages
└─ 🗣️ Top voices: @AiwithDharmik, @AnthropicAI, @alexalbert__, @claudeai │ r/LocalLLaMA, r/ClaudeAI
```

---

## Data Gaps

- **YouTube: 0 videos** — the engine's YouTube search returned 0 results despite multiple retry strategies. SC YouTube backend also returned 402 (payment required). Tutorial and demo content about Claude Code plugins/skills/MCP servers likely exists but was not captured. This is a meaningful gap given the how-to nature of the topic.
- **TikTok: 0 videos** — ScrapeCreators returned 402 (payment required) for all hashtag queries. Short-form video about Claude Code tools is likely active but uncaptured.
- **Instagram: 0 reels** — SC v2 reels endpoint returned 402. No coverage.
- **Polymarket: 0 markets** — No prediction markets active on Claude Code plugin ecosystem topics.
- **Reddit thin** — Only 3 threads captured, likely because the primary discussion subreddits (r/ClaudeAI, r/LocalLLaMA) are high-traffic and the most relevant recent threads had low raw scores relative to the relevance floor. The r/LocalLLaMA training data thread (1,344 upvotes) is the outlier; most skill/MCP discussion on Reddit may live in daily threads or comments, not top-level posts.
- **X engagement skew** — @claudeai's history tweet (4,342 likes) and Anthropic's interpretability research posts (1,328 + 889 + 842 likes) dominated raw like counts but were off-topic. Removing those, the ecosystem-specific X signal is ~2,000 likes across ~20 posts — solid but not viral.
- **Coverage estimate** — Social sources: ~65% (strong X + HN, weak Reddit, missing YouTube/TikTok). Web/technical: ~85% (comprehensive blog/guide coverage). Overall: ~70%.

---

## Key Quotes

> "Claude Code without setup is half of what it can be... It analyzes your project and tells you exactly which hooks, skills, MCP servers, and subagents to activate. You no longer have to guess anything." — [@ParamSiddh](https://x.com/ParamSiddh/status/2074487745897210020) on X

> "This is the Claude Code Resource Bible. 54 tools. Agents. MCP servers. Skills. Automation. Most people still haven't discovered this stack." — [@AiwithDharmik](https://x.com/AiwithDharmik/status/2074701028499550480) on X

> "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems, not one." — [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/)

> "MCPs are verbs. Skills are playbooks." — [duet.so](https://duet.so/guides/agent-skills-101-tools-vs-mcp-vs-skills)

> "MOST PEOPLE USE CLAUDE CODE LIKE A CHATBOT. IT'S ACTUALLY A FULL OPERATING SYSTEM FOR AI AGENTS." — [@0xCristal](https://x.com/0xCristal/status/2074457104866218124) on X

> "Packaging domain expertise into reusable containers is a great way to steer AI coding agents... reduces context overhead by encoding guidance as versioned capabilities." — [@N0V4Dev](https://x.com/N0V4Dev/status/2074788240821821895) on X

> "Skills are the core of agent performance. The skill store exists to make collaboration on this high-value stuff easy across teams." — [PostHog engineering](https://github.com/PostHog/posthog/pull/64385), GitHub PR

> "Anthropic and Open AI are getting so much data from the Claude Code and Codex usage, and I'm quite scared this will create an oligopoly because only their models will be trained on it." — [r/LocalLLaMA](https://www.reddit.com/r/LocalLLaMA/comments/1u795pb/donate_your_coding_sessions_to_an_open_ccby40/) (1,344 upvotes)

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) on X

> "Custom commands have merged into skills — here's how the modern slash command works and why skills are the format to use now." — [ClaudeKit](https://getclaudekit.com/blog/guide/mechanics/custom-skills-vs-commands)
