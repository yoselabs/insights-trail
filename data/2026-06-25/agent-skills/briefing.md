# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-25
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 6 threads | — | r/ClaudeAI, r/ChatGPTCoding |
| X/Twitter | 59 posts | 1,278 likes, 186 reposts | Top voices: @xmyttle, @DanKornas, @cyberfeng |
| YouTube | 0 videos | — | ScrapeCreators payment error; yt-dlp returned no results |
| Hacker News | 26 stories | 1,163 points, 668 comments | Multiple "Show HN" submissions |
| Bluesky | 12 posts | 83 likes, 6 reposts | @jefferyharrell.bsky.social most active |
| GitHub | 14 items | 845 reactions, 300 comments | anthropics/claude-code dominant |
| Web | 17 pages | — | via grounding + WebSearch supplements |

---

## Synthesized Findings

### 1. The Skills vs. MCP vs. Plugins Taxonomy Has Crystallized

The dominant content theme this month is educators and practitioners settling on a clear mental model for Claude Code's extension layers - a question that was genuinely murky six months ago. The consensus, per [tygartmedia.com](https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/), [claudskills.com](https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/), and [jsmanifest.com](https://jsmanifest.com/claude-code-full-stack-guide): **Skills teach Claude how to do something** (30-50 tokens of context overhead, loaded on demand), **MCP servers give Claude access to external systems** (50k+ tokens upfront per server), and **plugins bundle both together** into one installable. [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u6f7cr/what_i_learned_writing_an_eval_harness_for_my_own/) produced a standout post - "What I learned writing an eval harness for my own SKILL.md files (it caught two real bugs)" - documenting that skills need testing like code. The practical heuristic circulating on [dev.to](https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon): try a skill first, add MCP only when the integration will be used across sessions.

### 2. Discovery is the Ecosystem's Biggest Unsolved Problem

The loudest signal in the data: skill and plugin discovery is broken. [@DanKornas](https://x.com/DanKornas/status/2070014365294588191) put it bluntly with 26 likes and 6 reposts: "Claude Skills are useful. Finding the right ones is the messy part." His post promoted `awesome-claude-skills`, a curated GitHub list of 50+ agent skills grouped by task. Meanwhile [@chenzeling4](https://x.com/chenzeling4/status/2069494704589418744) noted that `claude-plugins-official`, Anthropic's own vetted directory, has **30,759 GitHub stars** - "it's literally just a list" - implying the demand for structure is enormous and the supply of discovery tooling still lags. [claudemarketplaces.com](https://claudemarketplaces.com/) claims 21,600+ skills and 12,500+ MCP servers now exist, but fragmentation means most developers still don't know what's out there. Multiple HN submissions this month targeted the discovery gap directly: [CodeGuilds](https://codeguilds.dev) (community registry for skills, agents, MCP servers) and [a GitOps-style registry](https://github.com/Friz-zy/ai-capability-registry) that versions workflows, skills, and MCP server configs together.

### 3. MCP Has Become Cross-Industry Infrastructure

MCP is no longer just Anthropic's protocol - it is governed by the **Linux Foundation** with stated support from OpenAI, Google, Microsoft, AWS, and Cloudflare, per [@Tipwotip](https://x.com/Tipwotip/status/2070037488836792497) (29 likes, 22 replies). The MCP server registry at modelcontextprotocol.io passed 800 listed servers in April 2026, and community estimates now put total MCP deployments (including private) at 13,000+ per [qcode.cc](https://www.qcode.cc/mcp-servers-ecosystem-2026). [@stretchcloud](https://x.com/stretchcloud/status/2069861617454469432) captured the emerging infrastructure pattern: "Every team building more than one agent hits the same infrastructure problem. You wire up credentials for the first agent, then repeat for the second... One MCP endpoint. Any tool your stack uses, configured once. Claude Code, Cursor, Codex all speak MCP natively." AWS released official MCP servers, skills, and plugins this week for AI agents to build on AWS services, per [Bluesky trending](https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f).

### 4. Dynamic Workflows Shipped - Loop Design is the New Paradigm

Anthropic's May 2026 launch of **Dynamic Workflows** - Claude Code writing and orchestrating its own multi-agent harness on the fly - generated 200 HN points and 135 comments at [claude.com/blog](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code). The post [covered by InfoQ](https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/) describes Claude parallelizing subtasks, validating results, and presenting a final synthesized answer. [@xmyttle](https://x.com/xmyttle/status/2069427440896651468), the thread's most engaged X voice (116 likes), unpacked Boris Cherny's position: "he built Claude Code and now he says the job is moving again - not from coding to prompting - from prompting to loop design." The practical implication per [@MaryamMiradi](https://x.com/MaryamMiradi/status/2069807885568086085) (11 likes): make Claude plan, structure, isolate, test, remember, and evaluate *before* writing a line of code. [@Lucy_love_AI](https://x.com/Lucy_love_AI/status/2069956002905194843) observed that Codex and Claude Code now have functionally identical component stacks (Automations/loop, worktree, SKILL.md, MCP connectors/servers, subagents) - "once you see the shape is the same, stop arguing about tools and just design the loop."

### 5. Distribution and Monetization of Skills Remains Unsolved

[@cyberfeng](https://x.com/cyberfeng/status/2069837102892921329) named the distribution problem precisely: "You already built a great agent inside Claude Code/Codex/Hermes. It's just trapped: skills, MCP servers, and instructions scattered across config files you can't share, secure, or sell. You can't sell a markdown file. You can sell a Gem." Multiple entrepreneurial efforts circling the same gap: the [gaal CLI](https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/) keeps CLAUDE.md, slash commands, MCP servers, and skills in sync across machines; [vercel-labs/skills #1329](https://github.com/vercel-labs/skills/issues/1329) is a feature request to resolve remote plugin sources so skills can live in domain repos rather than being copied into marketplace repos (where they drift). On June 2, 2026, OpenAI shipped Codex plugins bundling skills, app integrations, and MCP server configurations into one installable - a direct competitive move. The skills marketplace ecosystem itself grew from one registry in December 2025 to eight major platforms by Q2 2026 per [agensi.io](https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026).

### 6. Security and Observability Tooling Emerging Around the Stack

Two orthogonal signals: (1) agent-firewall, per [@Artie_Martello](https://x.com/Artie_Martello/status/2069839733073793046), sits in front of any coding agent and "before a tool call touches your system, it summarizes the real side effect: a diff for file writes, the exact command for shell, method + URL + body for HTTP." (2) [Show HN: Lupen](https://github.com/momoraul/Lupen) - "which Claude Code turn or sub-agent ran up your bill" - addresses cost attribution in multi-agent loops. The 451-point HN post ["Claude Code as a Daily Driver"](https://arps18.github.io/posts/claude-code-mastery/) (254 comments) and the 325-point post about [extended thinking output](https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/) suggest that production Claude Code deployments have matured enough that practitioners are now focused on observability, cost control, and access governance rather than basic setup.

---

## Cross-Source Patterns

**Pattern 1: Discovery is the critical unlock** - Appeared on X (multiple posts), HN (CodeGuilds Show HN, GitOps registry), Reddit (eval harness post about organizing skills), and Web (multiple "best skills" roundup articles). The gap between "skills exist" and "skills are findable and composable" is the dominant practitioner complaint.

**Pattern 2: Skills-first, MCP-second architecture** - Consistent across X, Web guides (dev.to, claudskills.com, jsmanifest.com), and Reddit. The cost asymmetry (30-50 tokens vs 50k+ tokens) is becoming the canonical reason practitioners prefer skills over MCP servers wherever possible, using MCP only for external system bridges.

**Pattern 3: Cross-agent portability** - Appeared on X (Codex/Claude Code component convergence post), Bluesky (Godot AI plugins for both Claude Code and Codex), and HN (Show HN: Namecom-CLI, agent skill for both Claude Code and Codex). The agent-agnostic SKILL.md standard is being referenced across the ecosystem, not just within Anthropic's tools.

**Pattern 4: Loop design over prompt engineering** - Boris Cherny's framing (prompting → loop design) resonated across X and HN. The "Dynamic Workflows" launch reinforced it from the product side. The subagent-as-memory-management framing from r/ClaudeAI adds a second dimension.

**Pattern 5: MCP governance maturation** - Appeared on X (Linux Foundation governance cheat sheet), Bluesky (AWS MCP servers), and Web. MCP is no longer optional infrastructure - it has broad industry commitment and is moving toward standardized discovery and security tooling.

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | What I learned writing an eval harness for my own SKILL.md files | — | — | "The skill failed its own gate." | https://www.reddit.com/r/ClaudeAI/comments/1u6f7cr/what_i_learned_writing_an_eval_harness_for_my_own/ |
| r/ClaudeAI | Subagents in Claude Code aren't a speed trick. They're a memory trick | — | — | "A subagent buys you a clean main context." | https://www.reddit.com/r/ClaudeAI/comments/1u71d27/subagents_in_claude_code_arent_a_speed_trick/ |
| r/ClaudeAI | We built a free CLI to keep CLAUDE.md, slash commands, MCP servers, and skills in sync across machines | — | — | "Claude Code wants CLAUDE.md. Codex wants AGENTS.md." | https://www.reddit.com/r/ClaudeAI/comments/1u17l8j/we_built_a_free_cli_to_keep_claudemd_slash/ |
| r/ClaudeAI | Understand what Claude did, instantly | — | — | "Everyone is shipping 10x faster with their own team of agents" | https://www.reddit.com/r/ClaudeAI/comments/1uct6vf/understand_what_claude_did_instantly/ |
| r/ClaudeAI | I built a free practice exam for the Claude Certified Architect cert | — | — | "60 scenario questions across the four areas the exam covers" | https://www.reddit.com/r/ClaudeAI/comments/1ucvi19/i_built_a_free_practice_exam_for_the_claude/ |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @xmyttle | "STOCK CLAUDE IS NOT THE PRODUCT - the setup is... those are saved jobs Claude can recognize and run again" | 71 | 5 | https://x.com/xmyttle/status/2069734529426772128 |
| @xmyttle | "BORIS CHERNY DOES NOT PROMPT CLAUDE LIKE YOU DO... the job is moving from prompting to loop design" | 116 | 11 | https://x.com/xmyttle/status/2069427440896651468 |
| @DanKornas | "Claude Skills are useful. Finding the right ones is the messy part." | 26 | 6 | https://x.com/DanKornas/status/2070014365294588191 |
| @Tipwotip | "The Ultimate MCP Server Cheat Sheet - MCP now governed by Linux Foundation with OpenAI, Google, Microsoft, AWS and Cloudflare" | 29 | 2 | https://x.com/Tipwotip/status/2070037488836792497 |
| @cyberfeng | "You already built a great agent... It's just trapped: skills, MCP servers, and instructions scattered across config files you can't share, secure, or sell." | 0 | 1 | https://x.com/cyberfeng/status/2069837102892921329 |
| @chenzeling4 | "30,759 stars and it's literally just a list. claude-plugins-official is Anthropic's own directory of vetted Claude Code plugins." | 1 | 0 | https://x.com/chenzeling4/status/2069494704589418744 |
| @xiaoying_eth | "20 GitHub repos to master Claude - Awesome MCP Servers, SuperClaude Framework, Claude Code Router..." | 40 | 12 | https://x.com/xiaoying_eth/status/2069673894966177918 |
| @stretchcloud | "Every agent re-solves tool connectivity from scratch. One MCP endpoint. Any tool your stack uses, configured once." | 0 | 1 | https://x.com/stretchcloud/status/2069861617454469432 |
| @cloudinary | "Built an agent loop with Claude Code + Cloudinary MCP servers to cut image weight 20%." | 0 | 0 | https://x.com/cloudinary/status/2069843052839969147 |
| @Lucy_love_AI | "Codex and Claude Code now have these five components... once you see the shape is the same, stop arguing about tools and design the loop" | 1 | 1 | https://x.com/Lucy_love_AI/status/2069956002905194843 |
| @MaryamMiradi | "How to Use Claude Code to Build Production AI Agents — make it plan, structure, isolate, test, remember, and evaluate first." | 11 | 2 | https://x.com/MaryamMiradi/status/2069807885568086085 |
| @RupaTiwari82008 | "MCP Agent Studio now supports GLM 5.2, Kimi K2.7 Code — compare MCP workflows across multiple models" | 2 | 0 | https://x.com/RupaTiwari82008/status/2069825757422223453 |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | — | https://arps18.github.io/posts/claude-code-mastery/ |
| 0o_MrPatrick_o0 | The text in Claude Code's "Extended Thinking" output | 325 | 223 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | — | https://claude.com/blog/introducing-dynamic-workflows-in-claude-code |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 36 | 12 | — | https://news.ycombinator.com/item?id=48546618 |
| nikitadoudikov | Show HN: Pulse – Dashboard for Claude Code, approve tool calls from your phone | 39 | 15 | — | https://github.com/nikitadoudikov/claude-pulse |
| muhammad-shafat | Show HN: Stop returning raw JSON from MCP servers, build rich inline UIs | — | — | — | https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3 |
| sermakarevich | Show HN: Lessons learned from running Claude Code swarms at scale | 10 | 7 | — | https://news.ycombinator.com/item?id=48407998 |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | https://codeguilds.dev |
| frizzy | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | https://github.com/Friz-zy/ai-capability-registry |
| selcuk | Show HN: Namecom-CLI – CLI and agent skill so Claude Code/Codex can do your DNS | 4 | — | — | https://github.com/hypersocialinc/namecom-cli |
| softie123 | Show HN: A police department for your Claude Code agents | 11 | 8 | — | https://github.com/varmabudharaju/agent-pd/blob/master/README.md |
| momoraul | Show HN: Lupen – which Claude Code turn or sub-agent ran up your bill | 3 | — | — | https://github.com/momoraul/Lupen |
| laxmena | Why Claude Code's Agent Loop Is over 1,400 Lines | 7 | — | — | https://internals.laxmena.com/p/why-claude-codes-agent-loop-is-over |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @jefferyharrell.bsky.social | "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list..." | 35 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22 |
| @jefferyharrell.bsky.social | "I'm pretty confident I can port Alpha from a bunch of Claude Code ad-hockery to a single plugin. Plugins are pretty powerful." | 11 | https://bsky.app/profile/jefferyharrell.bsky.social/post/3mnif47wktc22 |
| @coolhand.bsky.social | "I saw so many problems that I built plugins anyway for Claude and OpenClaw and the rest" | 12 | https://bsky.app/profile/coolhand.bsky.social/post/3mn2txuibns2y |
| @viriditax.bsky.social | "making VST plugins was the first thing I tried to do with [Claude Code] to flex it — made a bass octaver combined with an autopan" | 9 | https://bsky.app/profile/viriditax.bsky.social/post/3mnfnjua3v227 |
| @uermel.bsky.social | "Claude Code is pretty good at writing ChimeraX plugins! This one is almost entirely good context and some prompting" | 6 | https://bsky.app/profile/uermel.bsky.social/post/3moix2ipci22o |
| @webuyhousesusa.bsky.social | "ECC drops 63 specialized agents and 240+ ready-made skills straight into Claude Code, Cursor, and Codex — MIT-licensed" | 4 | https://bsky.app/profile/webuyhousesusa.bsky.social/post/3mmz7yn7ezd2c |
| @brunopedro.com | "42Crunch announced a breakthrough integration with Anthropic's Claude Code, introducing dedicated AI coding plugins for Agentic DevSecOps" | 1 | https://bsky.app/profile/brunopedro.com/post/3mnca64xtzs2z |
| @probbrain.bsky.social | "AWS releases official MCP servers, skills, and plugins enabling AI agents to build on AWS services" | — | https://bsky.app/profile/probbrain.bsky.social/post/3mp4awknuaw2f |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Blog | https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code | Dynamic Workflows launch — Claude writes its own multi-agent harness on the fly |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 21,600+ skills, 2,500+ marketplaces, 12,500+ MCP servers as of Q2 2026 |
| codersera.com | https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/ | Practitioner guide: pin one MCP per external system, write thin skills to orchestrate |
| claudskills.com | https://claudskills.com/learn/claude-code-skills-vs-mcp-servers-vs-plugins/ | Canonical 3-layer model: Skills teach / MCP connects / Plugins bundle |
| tygartmedia.com | https://tygartmedia.com/claude-skills-vs-mcp-vs-connectors-vs-plugins/ | "Skills teach Claude how, MCP gives access, Plugins package both" |
| jsmanifest.com | https://jsmanifest.com/claude-code-full-stack-guide | "Most Claude Code integration failures stem from misunderstanding the four-layer extension stack" |
| dev.to | https://dev.to/rapls/skill-mcp-plugin-or-just-a-cli-how-i-pick-a-claude-code-extension-lightest-first-3hon | Lightest-first decision framework for extension type selection |
| dev.to | https://dev.to/nagell/build-your-own-claude-code-marketplace-scaffold-structure-and-auto-updates-4n3f | A marketplace is just a GitHub repo with specific folder structure + two install commands |
| agensi.io | https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 | Ecosystem grew from 1 registry (Dec 2025) to 8 major platforms by Q2 2026 |
| qcode.cc | https://www.qcode.cc/mcp-servers-ecosystem-2026 | MCP registry passed 800 listed servers April 2026; ~13,000+ total deployments |
| deepwiki.com | https://deepwiki.com/anthropics/claude-code/4.1-plugin-marketplace-and-discovery | Plugin Marketplace & Discovery internals from anthropics/claude-code |
| deepwiki.com | https://deepwiki.com/anthropics/skills/2.3-marketplace-and-plugin-system | Marketplace.json structure, plugin skill bundles, strict resolution mode |
| hidekazu-konishi.com | https://hidekazu-konishi.com/entry/claude_code_skills_complete_guide.html | Complete guide to creating, testing, and distributing agent skills |
| llmbestpractices.com | https://llmbestpractices.com/ai-agents/claude-code-mcp | MCP integration best practices: prefer MCP over Bash for cross-session tool access |
| openaitoolshub.org | https://www.openaitoolshub.org/en/blog/claude-code-mcp-cli-integration-guide | Wire custom CLI tools as MCP servers for cross-session access |
| infoq.com | https://www.infoq.com/news/2026/06/dynamic-workflows-claude-code/ | InfoQ coverage of Dynamic Workflows launch and parallel agent coordination |
| computingforgeeks.com | https://computingforgeeks.com/claude-code-mcp-servers-setup/ | Step-by-step MCP server setup guide with scope and token management |

---

## Stats Block

```
├─ 🟠 Reddit: 6 threads
├─ 🔵 X: 59 posts │ 1,278 likes │ 186 reposts
├─ 🟡 HN: 26 stories │ 1,163 points │ 668 comments
├─ 🦋 Bluesky: 12 posts │ 83 likes │ 6 reposts
├─ 🐙 GitHub: 14 items │ 845 reactions │ 300 comments
├─ 🌐 Web: 17 pages (engine) + 10 WebSearch supplements
└─ 🗣️ Top voices: @xmyttle, @DanKornas, @cyberfeng, @Tipwotip │ r/ClaudeAI
```

---

## Data Gaps

- **YouTube**: Zero results. yt-dlp returned no matches; ScrapeCreators returned HTTP 402 (payment required). This is a meaningful gap - tutorial/walkthrough content about Claude Code skills and MCP setup is popular on YouTube but not captured here.
- **TikTok / Instagram**: HTTP 402 errors from ScrapeCreators across all hashtag and keyword searches. Short-form video content not represented.
- **Reddit**: Public JSON API returning 403 errors; only 6 threads captured via RSS fallback. r/ClaudeAI has active daily discussion that likely contains more on-topic threads than captured.
- **Polymarket**: No prediction markets found for this topic.
- **Bluesky**: Keyword searches returned 0 posts for most queries; only 12 posts captured from a broader crawl. Coverage is incomplete.
- **Approximate coverage**: 60-70%. Strong on HN and X (both complete), weak on Reddit and social video.

---

## Key Quotes

> "Claude Skills are useful. Finding the right ones is the messy part." - [@DanKornas](https://x.com/DanKornas/status/2070014365294588191) on X

> "30,759 stars and it's literally just a list. claude-plugins-official is Anthropic's own directory of vetted Claude Code plugins. MCP servers, slash commands, agent definitions, skills, all with a standard structure so one install command handles it." - [@chenzeling4](https://x.com/chenzeling4/status/2069494704589418744) on X

> "You already built a great agent inside Claude Code/Codex/Hermes. It's just trapped: skills, MCP servers, and instructions scattered across config files you can't share, secure, or sell. You can't sell a markdown file. You can sell a Gem." - [@cyberfeng](https://x.com/cyberfeng/status/2069837102892921329) on X

> "STOCK CLAUDE IS NOT THE PRODUCT. The setup is. Those are not 'better prompts.' They are saved jobs Claude can recognize and run again." - [@xmyttle](https://x.com/xmyttle/status/2069734529426772128) on X

> "Claude Code has 'plugins' but what it really needs is mods. I wanna spend six hours meticulously curating a mod list that lets me boot up a Game of Thrones-themed total conversion where all my PR's are in-character." - [@jefferyharrell.bsky.social](https://bsky.app/profile/jefferyharrell.bsky.social/post/3mniamr3x4c22) on Bluesky

> "He built Claude Code and now he says the job is moving again - not from coding to prompting - from prompting to loop design." - [@xmyttle](https://x.com/xmyttle/status/2069427440896651468) on X, about Boris Cherny

> "Subagents in Claude Code aren't a speed trick. They're a memory trick." - [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u71d27/subagents_in_claude_code_arent_a_speed_trick/) on Reddit

> "Every team building more than one agent hits the same infrastructure problem. You wire up credentials for the first agent, then repeat for the second, then again for the third. Every agent re-solves tool connectivity from scratch." - [@stretchcloud](https://x.com/stretchcloud/status/2069861617454469432) on X

> "Codex and Claude Code now have these five components - once you see the shape is the same, stop arguing about tools and just design the loop." - [@Lucy_love_AI](https://x.com/Lucy_love_AI/status/2069956002905194843) on X

> "MCP stands for Model Context Protocol - a plug-in system for AI - created by Anthropic, now governed by the Linux Foundation with support from OpenAI, Google, Microsoft, AWS and Cloudflare." - [@Tipwotip](https://x.com/Tipwotip/status/2070037488836792497) on X
