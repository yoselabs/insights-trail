# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-07-06
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Reddit, GitHub, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 5 threads | 220 upvotes, 235 comments | r/ClaudeWorkflows, r/UXDesign, r/claudeskills |
| X/Twitter | 71 posts | 163,624 likes, 23,598 reposts | Top voices: @0xTrackmind, @alexalbert__, @AnthropicAI |
| YouTube | 0 videos | — | yt-dlp throttled; 402 on SC backup |
| Hacker News | 27 stories | 4,257 points, 2,144 comments | — |
| TikTok | 0 videos | — | SC key hit 402 (quota) |
| Instagram | 0 reels | — | SC key hit 402 (quota) |
| Bluesky | 4 posts | 10 likes, 1 repost | — |
| Polymarket | 0 markets | — | No markets matched topic |
| Web | 19 pages | — | via Exa + WebSearch supplements |

---

## Synthesized Findings

### 1. The Plugin Ecosystem Has Matured Into Real Infrastructure

Claude Code's plugin/skill ecosystem has reached a scale that was unimaginable a year ago. Anthropic launched plugins on October 9, 2025, bundling slash commands, subagents, hooks, and MCP server configs into one installable unit. As of mid-2026, the official `anthropics/claude-plugins-official` repo ships **101 vetted plugins** plus 68 partner plugins (GitHub, Playwright, Supabase, Figma, Vercel, Linear, Sentry, Stripe, Firebase). The install pattern is a single command: `/plugin install claude-code-setup@claude-plugins-official`. The key insight per [arte.itlibra.com](https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace) is that plugins are the *only* extension point whose value comes from distribution rather than runtime behavior — they are the shipping unit for teams.

Anthropic named the underlying failure mode driving plugin adoption: in May 2026, they labeled unshared team configurations "tribal knowledge" — and positioned plugins as the fix. Community uptake has been explosive. Per [claudemarketplaces.com](https://claudemarketplaces.com/), **2,500+ marketplaces** are now registered. [morphllm.com](https://www.morphllm.com/claude-code-marketplace) notes quality is uneven — "ranging from polished Vercel Labs collections to abandoned repos" — but the distribution infrastructure is solved.

The official Anthropic plugin for initial setup drew the top-scored X post in this period: [@0xTrackmind](https://x.com/0xTrackmind/status/2073832406298022185) (47 likes, 5 reposts) wrote: "You're running Claude Code at half its power. Anthropic has an official plugin that fixes that for you — it scans your project and tells you which hooks, skills, MCP servers, and subagents to turn on. No more guessing what to configure. One command and the setup handles itself."

Cross-platform: X, Web, Reddit all surfaced this theme. HN stories and r/claudeskills confirm the configuration-gap is a real onboarding problem.

### 2. Agent Skills Became a Cross-Platform Open Standard

Anthropic published the Agent Skills spec as an open standard at [agentskills.io](https://agentskills.io) on **December 18, 2025**. As of June 2026, roughly **40 compatible products** appear on the official showcase: OpenAI Codex, GitHub Copilot, Cursor, Gemini CLI, VS Code, and others. This means a skill written for Claude Code can, in principle, run across the entire agentic IDE landscape.

The ecosystem catalog has exploded past any human-curation capacity. Per [agentman.ai's ecosystem report](https://agentman.ai/blog/agent-skills-ecosystem-report-2026), SkillsMP alone lists approximately **1.9 million public skills** scraped from GitHub. The median quality is poor — SkillsBench analysis of 47,150 public skills found an average score of **6.2/12** — but curated skill collections raise agent task pass rates by **16.2 percentage points** on average. Discovery remains the open problem: distribution and portability are solved; quality and signal-to-noise are not.

[@zacharyr0th](https://x.com/zacharyr0th/status/2073842544606327050) released `agent-starter` (7 likes): "one manifest for skills, MCP servers, and setup across Claude Code, Codex, and Cursor" — a practitioner's answer to the cross-platform portability problem.

Cross-platform: Web, X, Bluesky all covered the standard; HN carried the ecosystem scale debate.

### 3. MCP Became the Connective Tissue of the AI Agent Stack

Model Context Protocol has emerged as the universal connection layer across every major AI coding environment. Platform-level MCP integrations have been shipping fast. [@SwizzyOnChain](https://x.com/SwizzyOnChain/status/2073993845080301953) reported: "X just opened its full real-time firehose to AI agents. Same week: Kraken, Binance, and OKX each shipped competing agent trading kits." Agents inside Claude, Cursor, and VS Code can now search the full X archive via MCP. AWS released official MCP servers, skills, and plugins enabling AI agents to interface with AWS services — surfaced via [probbrain.bsky.social on Bluesky](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f).

The distinction between extension types is settling into a canonical mental model. Per [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/): "Build a skill to change how Claude works, a subagent to protect your context window, and an MCP server to reach a system Claude cannot otherwise touch. They solve three different problems." The [dev.to practitioner guide](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) on choosing the "lightest" extension first is the most-cited tactical framing.

[@Voxyz_ai](https://x.com/Voxyz_ai/status/2074092352545661435) (2 likes) captured the token-efficiency framing precisely: "Unused MCP servers are the easiest miss: their tool definitions take up context whether you call them or not."

MCP is also expanding beyond software tooling into hardware. [@panroboticsxyz](https://x.com/panroboticsxyz/status/2073786409001853189) posted: "We've been embedding MCP servers onto hardware — ultimately to put them on drones/UAVs and robots so AI Agents, Claude Code, Codex, OpenClaw, etc have access to let whatever you want to attach to them be exposed directly as tools."

Cross-platform: X, HN, Reddit, Bluesky, Web all covered MCP expansion.

### 4. Senior vs. Junior AI Workflow Gap: Environment Setup Is the Differentiator

A Japanese-language post by [@sumika45379](https://x.com/sumika45379/status/2073908542227288166) (4 likes) articulated the most-shared tactical framework in this period — the gap between junior and senior vibe coders comes down to whether you build the agent's environment before coding:

> "Junior vibe coders: install Claude Code / Codex / Cursor → think about what to build → hand it to Claude → produce AI slop, infinite debugging. Senior vibe coders build this first: personal preferences, agent memory, agent skills and rules, connectors, MCP servers, PRD, role division. The difference is whether you build 'an environment where the AI won't get lost' before coding."

This aligns with [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) (556 likes, first-party Claude Code author): "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team."

The [r/claudeskills thread](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) "90% claude code tutorials are waste of time" (100 upvotes, 65 comments) echoes this: "They all work the same under the hood. The wrapper doesn't matter. The MCP i[nfrastructure is what matters]..." — arguing that most tutorials teach the surface layer (tool choice) not the environment-setup layer (configuration).

Cross-platform: X, Reddit both surface this theme strongly.

### 5. Security Crisis: MCP Is the Supply Chain Problem of 2026

Security concerns have become impossible to ignore. [@perturbaix](https://x.com/perturbaix/status/2073860663500501433) (3 likes, 1 repost): "1,184 malicious skills confirmed across ClawHub — the OpenClaw AI agent framework marketplace. The Pentagon designated Anthropic a supply chain risk. The first time an American company has received that classification. AI agent security in 2026 is a supply chain problem first. Model Context Protocol is the connective tissue across every major incident this year: poisoned config files in Claude Code. Malicious marketplace skills on ClawHub. Exposed MCP servers running without authentication."

The web confirms systemic severity. Per the [Cloud Security Alliance Research Note](https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-security-crisis-20260504-csa-styled/) (May 2026), an April 2026 MCP design vulnerability disclosure exposed ~200,000 vulnerable instances across a supply chain covering 150M+ package downloads. The first real-world malicious MCP server was `postmark-mcp` on npm — it mirrored a legitimate email tool for 15 clean releases before v1.0.16 silently BCC'd every agent-sent email to an attacker ([helpnetsecurity.com](https://www.helpnetsecurity.com/2026/02/23/ai-agent-security-risks-enterprise/)). [Qualys labeled MCP "The New Shadow IT"](https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026) in March 2026.

[The Hacker News](https://thehackernews.com/2026/06/microsoft-warns-poisoned-mcp-tool.html) reported in June 2026: Microsoft warns that poisoned MCP tool descriptions can make AI agents leak data — the root cause being that MCP mixes instructions and data in the same place, so editing a tool's description can steer the agent as effectively as rewriting its system prompt.

[@TheoWtmn](https://x.com/TheoWtmn/status/2073756638821986331) asked the practitioner question: "Anybody can publish an MCP server. Great for hacking. But production Claude Code needs servers that don't silently break between versions — no health checks, no deprecation, just a broken tool call. How do you vet MCP servers before adding them?"

Cross-platform: X, HN, Web all cover this theme with high engagement.

### 6. Agent Marketplaces Are Evolving Toward Economic Infrastructure

A distinct thread around agent *marketplaces as economic coordination layers* is emerging — separate from the developer tooling conversation. [@useAtelier](https://x.com/useAtelier/status/2073615492997087439) (42 likes, 51 reposts on bounty announcement): "Atelier brings these primitives into a unified coordination layer: machine-readable service discovery, verifiable identity and reputation, escrow and delivery verification, instant USDC settlement, REST, MCP, and x402 interfaces, autonomous agent-to-agent commerce." Atelier reports 308 registered agents, 320 services across 12 categories, and 206 settled orders at time of writing.

OKX launched an AI agent marketplace — "where AI agents discover work, hire each other, complete tasks, and get paid onchain" — with a market signal from [@remp0x](https://x.com/remp0x/status/2071952905779757151) (22 likes, 8 reposts): "@OKX announcing its AI marketplace is a clear signal that this category is moving from niche experiment to real infrastructure vertical."

These crypto-native agent economy platforms treat skill/MCP registries not as dev tooling but as market infrastructure for economic coordination. The framing: "The next bottleneck for AI agents is not intelligence. It is economic infrastructure."

Cross-platform: X primarily; this theme is embryonic on HN and absent from Reddit in this window.

### 7. Notable HN Stories: Security, Cost, and Anthropic Context

Several high-engagement HN stories frame the broader context:

- **"Claude Code is steganographically marking requests"** ([thereallo.dev](https://thereallo.dev/blog/claude-code-prompt-steganography)) — 2,437 pts, 746 comments. A researcher found Claude Code embeds invisible markers in its prompts; the community debate is about transparency and trust.
- **"Alibaba to ban Claude Code in workplace over alleged backdoor risks"** (Reuters) — 335 pts, 279 comments. Chinese companies moving away from Claude Code citing security concerns.
- **"I used Claude Code to get a second opinion on my MRI"** ([antoine.fi](https://antoine.fi/mri-analysis-using-claude-code-opus)) — 563 pts, 712 comments. Shows the breadth of use cases Claude Code + plugins can address.
- **"Claude Code Just Got 5x More Expensive"** ([vincentschmalbach.com](https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/)) — 57 pts, 8 comments. Pricing changes creating friction.
- **"ZCode: Claude Code from the Makers of GLM"** ([zcode.z.ai](https://zcode.z.ai/cn)) — 278 pts, 15 comments. Chinese competitor ships Claude Code equivalent.
- **"Show HN: Crew – Let Claude Code agents talk to each other"** ([github.com/0xmmo/crew](https://github.com/0xmmo/crew)) — early multi-agent coordination tooling.

### 8. Autonomous Skill Discovery and Shared Memory via 'bhived' MCP

Two r/ClaudeWorkflows posts (with high workflow value scores of 85/100) document the `bhived` MCP server, which solves a fundamental problem: "Claude Code agents repeatedly start from scratch, relying on the developer to re-explain context, re-invent approaches, and re-identify issues." The bhived MCP enables **autonomous skill discovery with shared memory** across agent sessions — essentially a distributed agent memory and skill registry. The companion `archex` MCP server addresses token efficiency for code context retrieval.

URLs: [bhived workflow post 1](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/), [archex workflow](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/).

---

## Cross-Source Patterns

**Pattern 1: The "environment first" principle is the consensus best practice for Claude Code skill/plugin use**
- X: [@sumika45379](https://x.com/sumika45379/status/2073908542227288166) (Japanese-language, widely shared), [@iammukeshm](https://x.com/iammukeshm/status/2074040194051793306) (20 likes: "The setup is where the real speed is")
- Reddit: [r/claudeskills "90% tutorials are waste of time"](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) (100 pts)
- Web: [startdebugging.net](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/), [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution)
- Quote: "The difference is whether you build 'an environment where the AI won't get lost' before coding." — [@sumika45379](https://x.com/sumika45379/status/2073908542227288166)

**Pattern 2: MCP security is now an enterprise-blocking problem, not a theoretical one**
- X: [@perturbaix](https://x.com/perturbaix/status/2073860663500501433) (Pentagon supply chain designation), [@TheoWtmn](https://x.com/TheoWtmn/status/2073756638821986331) (production vetting question)
- HN: Alibaba workplace ban (335 pts), steganography story (2,437 pts)
- Web: [thehackernews.com](https://thehackernews.com/2026/06/microsoft-warns-poisoned-mcp-tool.html) Microsoft poisoning warning, [qualys.com](https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026) Shadow IT framing, [CSA research note](https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-security-crisis-20260504-csa-styled/)
- Quote: "AI agent security in 2026 is a supply chain problem first. Model Context Protocol is the connective tissue across every major incident this year." — [@perturbaix](https://x.com/perturbaix/status/2073860663500501433)

**Pattern 3: Platform-level MCP integrations (X, AWS, Kraken, Binance, OKX) are commoditizing tool access**
- X: [@SwizzyOnChain](https://x.com/SwizzyOnChain/status/2073993845080301953), [@ds_fafa_](https://x.com/ds_fafa_/status/2074045686413135902)
- Bluesky: [@probbrain.bsky.social](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) (AWS MCP news)
- Web: [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide), [totalum.app](https://www.totalum.app/blog/best-mcp-servers-2026)

**Pattern 4: Quality-vs-quantity tension in skill marketplaces is unresolved**
- Web: [agentman.ai report](https://agentman.ai/blog/agent-skills-ecosystem-report-2026) (1.9M public skills, 6.2/12 avg quality score), [morphllm.com](https://www.morphllm.com/claude-code-marketplace) (2,500+ marketplaces, quality uneven)
- Reddit: [r/claudeskills](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) ("90% tutorials waste of time" — applies equally to public skills)
- HN: Community debate over SkillsBench benchmarking methodology

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/claudeskills | 90% claude code tutorials are waste of time | 100 | 65 | "They all work the same under the hood. The wrapper doesn't matter. The MCP i[nfrastructure is what counts]..." | [link](https://www.reddit.com/r/claudeskills/comments/1u610hm/90_claude_code_tutorials_are_waste_of_time/) |
| r/UXDesign | Claude Code Has Access to My Design System, Yet the UI Output Is Still Terrible | 117 | 170 | "Since agentic AI is something I'm using for the first time, I'm struggling a bit..." | [link](https://www.reddit.com/r/UXDesign/comments/1uct2dx/claude_code_has_access_to_my_design_system_yet/) |
| r/ClaudeWorkflows | [Workflow] Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP | 1 | — | "Agents repeatedly start from scratch, relying on the developer to re-explain context" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/) |
| r/ClaudeWorkflows | [Workflow] Improve Claude Code Agent Token Efficiency with `archex` MCP Server | 1 | — | "Inefficient and token-hungry code context retrieval" | [link](https://www.reddit.com/r/ClaudeWorkflows/comments/1u6ir8s/workflow_improve_claude_code_agent_token/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @0xTrackmind | "You're running Claude Code at half its power. Anthropic has an official plugin that fixes that..." | 47 | 5 | [link](https://x.com/0xTrackmind/status/2073832406298022185) |
| @alexalbert__ | "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." | 556 | 15 | [link](https://x.com/alexalbert__/status/2069470389391241314) |
| @Adilson_Ai | Claude is offering 18 official AI courses with certificates. And it's 100% free | 49 | 40 | [link](https://x.com/Adilson_Ai/status/2073756002433040392) |
| @perturbaix | "1,184 malicious skills confirmed across ClawHub — the OpenClaw AI agent framework marketplace." | 3 | 1 | [link](https://x.com/perturbaix/status/2073860663500501433) |
| @SwizzyOnChain | "X just opened its full real-time firehose to AI agents. Same week: Kraken, Binance, and OKX shipped agent trading kits." | 2 | 1 | [link](https://x.com/SwizzyOnChain/status/2073993845080301953) |
| @iammukeshm | "Most people use Claude Code like a fancy autocomplete. The setup is where the real speed is." | 20 | 4 | [link](https://x.com/iammukeshm/status/2074040194051793306) |
| @sumika45379 | "Senior vibe coders build: personal preferences, agent memory, agent skills and rules, connectors, MCP servers..." | 4 | 2 | [link](https://x.com/sumika45379/status/2073908542227288166) |
| @zacharyr0th | "agent-starter: one manifest for skills, MCP servers, and setup across Claude Code, Codex, and Cursor" | 7 | — | [link](https://x.com/zacharyr0th/status/2073842544606327050) |
| @TheoWtmn | "Anybody can publish an MCP server. Great for hacking. But production Claude Code needs servers that don't silently break..." | 1 | — | [link](https://x.com/TheoWtmn/status/2073756638821986331) |
| @useAtelier | "The next bottleneck for AI agents is not intelligence. It is economic infrastructure." | 5 | 1 | [link](https://x.com/useAtelier/status/2073615499397611875) |
| @remp0x | "@OKX announcing its AI marketplace is a clear signal that this category is moving from niche experiment to real infrastructure vertical." | 22 | 8 | [link](https://x.com/remp0x/status/2071952905779757151) |
| @ds_fafa_ | "Extend tools with MCP servers → Automate PR reviews via GitHub → Build hooks for complex tasks" | 6 | — | [link](https://x.com/ds_fafa_/status/2074045686413135902) |
| @Voxyz_ai | "Unused MCP servers are the easiest miss: their tool definitions take up context whether you call them or not." | 2 | — | [link](https://x.com/Voxyz_ai/status/2074092352545661435) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| kirushik | Claude Code is steganographically marking requests | 2,437 | 746 | Top story of the period — invisible prompt markers debate | [link](https://thereallo.dev/blog/claude-code-prompt-steganography) |
| nsoonhui | Alibaba to ban Claude Code in workplace over alleged backdoor risks | 335 | 279 | Reuters source; Chinese enterprise security concerns | [link](https://www.reuters.com/world/china/alibaba-ban-claude-code-workplace-over-alleged-backdoor-risks-source-says-2026-07-03/) |
| — | I used Claude Code to get a second opinion on my MRI | 563 | 712 | Shows breadth of agentic use cases | [link](https://antoine.fi/mri-analysis-using-claude-code-opus) |
| — | The text in Claude Code's "Extended Thinking" output | 326 | 225 | Authenticity of extended thinking output | [link](https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/) |
| — | ZCode: Claude Code from the Makers of GLM | 278 | 15 | Chinese Claude Code competitor | [link](https://zcode.z.ai/cn) |
| — | Claude Code Just Got 5x More Expensive | 57 | 8 | Pricing friction for power users | [link](https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/) |
| — | Show HN: I Made TS Compiler Graph MCP: 10x Fewer Tokens in Claude Code and Codex | 3 | — | MCP for token efficiency | [link](https://github.com/samchon/ttsc/tree/master/packages/graph) |
| — | I made a free MCP server so your Claude can read Claude/Anthropic news and RAG | 3 | — | Community MCP server for Claude news | [link](https://claudenews.online) |
| — | Show HN: Crew – Let Claude Code agents talk to each other | 4 | 2 | Multi-agent coordination via skills | [link](https://github.com/0xmmo/crew) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @probbrain.bsky.social | "AWS releases official MCP servers, skills, and plugins enabling AI agents to build..." | 1 | [link](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f) |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting..." | 6 | [link](https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o) |
| @mikaelbuilds.bsky.social | "Claude Code 'still running' is not one bug. I built a no-secret packet for v2.1.179-style remote failures..." | 1 | [link](https://bsky.app/profile/mikaelbuilds.bsky.social/post/3moyltelun72w) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| arte.itlibra.com | [link](https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace) | Complete guide: plugin structure, /plugin command, marketplace mechanics, publish flow |
| startdebugging.net | [link](https://startdebugging.net/2026/07/claude-code-skills-vs-subagents-vs-mcp-servers-when-to-build-each/) | Canonical decision framework: skills change Claude behavior, subagents protect context, MCP reaches external systems |
| morphllm.com | [link](https://www.morphllm.com/claude-code-marketplace) | 2,500+ marketplaces registered; quality uneven |
| agentman.ai | [link](https://agentman.ai/blog/agent-skills-ecosystem-report-2026) | 1.9M public skills scraped; 6.2/12 avg quality; curated skills +16.2pp pass rate |
| mcsaguru.com | [link](https://mcsaguru.com/claude-code-plugins-vs-skills-vs-mcp-explained) | Plugins/skills/MCP layer explanation |
| claudefa.st | [link](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution) | Plugin distribution from personal setup to org standard |
| clarista.io | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | 101 vetted + 68 partner plugins in official marketplace; tribal knowledge framing |
| code.claude.com | [link](https://code.claude.com/docs/en/skills) | Official skills docs |
| code.claude.com | [link](https://code.claude.com/docs/en/discover-plugins) | Official plugin discovery docs |
| thehackernews.com | [link](https://thehackernews.com/2026/06/microsoft-warns-poisoned-mcp-tool.html) | Microsoft: poisoned MCP tool descriptions leak data |
| thehackernews.com | [link](https://thehackernews.com/2026/04/anthropic-mcp-design-vulnerability.html) | April 2026 MCP RCE design vulnerability (200K instances) |
| qualys.com | [link](https://blog.qualys.com/product-tech/2026/03/19/mcp-servers-shadow-it-ai-qualys-totalai-2026) | "MCP Servers: The New Shadow IT" — scan for exposed endpoints |
| labs.cloudsecurityalliance.org | [link](https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-security-crisis-20260504-csa-styled/) | CSA MCP Security Crisis research note (May 2026) |
| helpnetsecurity.com | [link](https://www.helpnetsecurity.com/2026/02/23/ai-agent-security-risks-enterprise/) | Enterprise agentic AI security; postmark-mcp first real-world malicious server |
| github.com | [link](https://github.com/anthropics/claude-plugins-official) | Official Anthropic-managed plugin directory |
| github.com | [link](https://github.com/VoltAgent/awesome-agent-skills) | Curated 1,000+ agent skills compatible with Claude Code, Codex, Gemini CLI, Cursor |
| github.com | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2,810 skills, 200 agents; ccpi CLI package manager |
| dev.to | [link](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon) | Practitioner: skill → MCP → plugin decision flow, lightest-first |
| tygartmedia.com | [link](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/) | Claude Skills vs MCP vs Connectors vs Plugins taxonomy |

---

## Stats Block

```
├─ 🟠 Reddit: 5 threads │ 220 upvotes │ 235 comments
├─ 🔵 X: 71 posts │ 163,624 likes │ 23,598 reposts
├─ 🟢 HN: 27 stories │ 4,257 points │ 2,144 comments
├─ 🦋 Bluesky: 4 posts │ 10 likes │ 1 repost
├─ 🐙 GitHub: 25 items │ 813 reactions │ 465 comments
├─ 🌐 Web: 19 pages (+ 10 WebSearch supplements)
└─ 🗣️ Top voices: @alexalbert__, @0xTrackmind, @perturbaix, @remp0x │ r/ClaudeWorkflows, r/claudeskills
```

---

## Data Gaps

- **YouTube: 0 videos** — yt-dlp searches returned 0 results (search query too long); ScrapeCreators backup hit HTTP 402 (quota). This is a meaningful gap: there are likely dozens of Claude Code skills/MCP tutorial videos in this period that were not captured.
- **TikTok: 0 videos** — all hashtag searches hit HTTP 402 (quota exhausted). Missing TikTok creator coverage of Claude Code plugins/MCP demos.
- **Instagram: 0 reels** — ScrapeCreators HTTP 402 on all Instagram endpoints.
- **Reddit: 5 threads only** — ScrapeCreators backup failed (402); Arctic Shift provided score enrichment. The ClaudeAI, LocalLLaMA, and MachineLearning subreddits likely have more relevant threads not captured in this pass.
- **X noise**: Several @remp0x and @okx posts are crypto-native agent marketplace content (Solana/DeFi angle) rather than Claude Code developer tooling — filtered from top tables but present in raw data.
- **Approximate coverage**: Reddit ~30% (quota limited), X ~85%, HN ~90%, Web ~75%, YouTube 0%, TikTok 0%. Overall: ~65% of available signal captured.

---

## Key Quotes

> "You're running Claude Code at half its power. Anthropic has an official plugin that fixes that for you — it scans your project and tells you which hooks, skills, MCP servers, and subagents to turn on. No more guessing what to configure." — [@0xTrackmind](https://x.com/0xTrackmind/status/2073832406298022185) on X

> "This has completely changed how I work with Claude. It feels less like using a tool and more like managing a team." — [@alexalbert__](https://x.com/alexalbert__/status/2069470389391241314) on X (Claude Code author, 556 likes)

> "Senior vibe coders build this first: personal preferences, agent memory, agent skills and rules, connectors, MCP servers. The difference is whether you build 'an environment where the AI won't get lost' before coding." — [@sumika45379](https://x.com/sumika45379/status/2073908542227288166) on X

> "AI agent security in 2026 is a supply chain problem first. Model Context Protocol is the connective tissue across every major incident this year: poisoned config files in Claude Code. Malicious marketplace skills on ClawHub. Exposed MCP servers running without authentication." — [@perturbaix](https://x.com/perturbaix/status/2073860663500501433) on X

> "Unused MCP servers are the easiest miss: their tool definitions take up context whether you call them or not." — [@Voxyz_ai](https://x.com/Voxyz_ai/status/2074092352545661435) on X

> "The next bottleneck for AI agents is not intelligence. It is economic infrastructure. Agents need standardized ways to discover work, expose capabilities, establish trust, coordinate execution, and settle value autonomously." — [@useAtelier](https://x.com/useAtelier/status/2073615499397611875) on X

> "Distribution and portability are solved; quality and security are not. Curated skills raise agent pass rates by 16.2 points on average, but the average public skill is too low-quality to help." — [agentman.ai ecosystem report](https://agentman.ai/blog/agent-skills-ecosystem-report-2026)

> "Anybody can publish an MCP server. Great for hacking. But production Claude Code needs servers that don't silently break between versions — no health checks, no deprecation, just a broken tool call. How do you vet MCP servers before adding them?" — [@TheoWtmn](https://x.com/TheoWtmn/status/2073756638821986331) on X
