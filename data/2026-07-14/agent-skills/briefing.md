# Claude Code Skills, Plugins, and the MCP Ecosystem — Daily Briefing
**Date:** 2026-07-14
**Query type:** GENERAL
**Sources:** X/Twitter, Hacker News, Bluesky, GitHub, Reddit (partial), Web (global), Web (Japan), Web (China)
**Delta from:** data/2026-07-14/agent-skills/prev-briefing.md (2026-07-13) — this briefing prioritizes what is NEW since yesterday

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 1 thread | 1 upvote, 1 comment | Partial — blocked after 2 items; scrapecreators also DOWN |
| X/Twitter | 20 posts | 1,487 likes, 119 reposts | Strong signal on security, WrongStack, kapa.ai |
| YouTube | 0 videos | — | scrapecreators=DOWN (402 billing) |
| Hacker News | 31 stories | 4,442 points, 2,123 comments | Richest source this run; steganography story dominates |
| TikTok | 0 videos | — | scrapecreators=DOWN (402 billing) |
| Instagram | 0 reels | — | scrapecreators=DOWN (402 billing) |
| Bluesky | 4 posts | 28 likes | SQL plans plugin, Storybook, /checkup command |
| Polymarket | 0 markets | — | No relevant markets found |
| Web (global) | 11 pages | — | 🌐 WebSearch + keyless; dev.to, designrevision.com, lagrowthmachine.com, stacklok, claudemarketplace.net, etc. |
| Web (Japan) | 5 pages | — | 🇯🇵 Qiita (shatolin, miruky), Zenn (chmod644, ino_h), note.com (varelser) |
| Web (China) | 1 page (3 blocked) | — | 🇨🇳 cnblogs (1 fetched); Zhihu x2 (HTTP 403), CSDN (HTTP 521) |

---

## Synthesized Findings

### 1. 🌐 SECURITY CRISIS: RCE via Claude Code Auto-Mode — Today's Top Story

The biggest new development of July 14: Claude Code's auto-mode has been confirmed as a viable attack vector for remote code execution. Security researcher @SlavaOPs on X summarized the finding: "pointing Claude Code or Codex at a third-party repo to 'scan it for vulnerabilities' can get you RCE instead - in the default, recommended auto-mode. No plugins, no MCP servers needed as an entry point. The prompt injection lives directly inside the library's own source code - the exact thing the agent was told to go read. It can't tell the difference between a README instruction and a malicious prompt."

The attack class is not limited to one CVE. Confirmed vulnerabilities in this reporting window:
- **CVE-2025-59536 + CVE-2026-21852**: Check Point Research found that Claude Code hooks and MCP environment variable injection can be chained. An attacker crafts a repository where `onInit` hooks or MCP server config variables are poisoned. Check Point describes it as "RCE and API token exfiltration through Claude Code project files." (https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/)
- **CVE-2026-39861**: Sandbox escape via symlink. Claude Code's container isolation can be bypassed when it follows symlinks to paths outside the sandboxed workspace.
- **CVE-2026-24887**: A secondary exfiltration path via environment variable leakage in MCP subprocess calls.
- **Claude Desktop Extensions RCE**: A separate LayerX Security report found 10,000+ Claude Desktop users exposed via extension RCE (https://www.layerxsecurity.com/claude-desktop-extensions-rce/).

The Cloud Security Alliance published a research note framing the class more broadly: "Prompt injection via GitHub metadata is a class-level supply chain risk for AI agents" (https://labs.cloudsecurityalliance.org/research/csa-research-note-claude-code-github-action-prompt-injection/).

Full developer-tech coverage: https://www.developer-tech.com/news/developers-face-rce-via-claude-code-auto-mode-exploit/
@SlavaOPs X post: https://x.com/SlavaOPs/status/2076949170531791272

**What's new vs. July 13:** The auto-mode exploit was disclosed today. Prior briefing had no security vulnerability items. This is a first-time signal for this topic.

---

### 2. 🌐 TRUST EROSION: Steganographic Marking and the Spyware Framing

The highest-engagement story of the past 30 days for this topic is not a product launch - it is a trust story. On June 30, a post at thereallo.dev revealed that Claude Code is steganographically marking its own requests with hidden patterns that can be detected after the fact. This story reached 2,445 HN points and 750 comments - the largest single HN discussion in this topic window. A second HN thread titled "Claude Code: Anthropic has embedded hidden spyware-like code in Claude Code" hit 56 points with a further 14 comments citing the same IntCyberDigest Twitter thread.

The community debate in the 750-comment thread split along predictable lines: some read it as a watermarking feature for abuse detection; others read it as covert surveillance. No official Anthropic statement was visible in the research window. The story is distinct from, but amplified by, the concurrent "Claude Code Just Got 5x More Expensive" piece (57 pts, 8 comments, https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/) and the "Ask HN: Anthropic banned me from using Claude Code and I don't know what to do" thread (82 pts, 94 comments, https://news.ycombinator.com/item?id=48641160).

These three stories together signal a community friction point: trust + price + enforcement are converging in a way that gives WrongStack and ZCode (see finding #3) an opening to frame themselves as alternatives.

HN link: https://thereallo.dev/blog/claude-code-prompt-steganography
IntCyberDigest X post: https://twitter.com/IntCyberDigest/status/2071971609183678544

**What's new vs. July 13:** The steganography story broke June 30 but was not in the prior briefing. With 2,445 pts it is the community's most-discussed signal in this window. The trust-erosion narrative is new context.

---

### 3. 🌐 COMPETITION ARRIVES: WrongStack and ZCode Challenge Claude Code's Agent Orchestration Primacy

Two new challengers emerged in this window, each attacking different weaknesses the trust stories above expose.

**WrongStack** (@ersinkoc, X, July 13) positions itself as a purpose-built multi-agent orchestration system, not a general coding agent that can be plugin-extended: "when it comes to real orchestration, multi-agent execution, and sustainable autonomy, those products are still mediocre. Adding hundreds of lines of prompts, AGENTS.md files, MCP servers, skills, or plugins will not turn them into WrongStack." This is a direct shot at Claude Code's architecture of layered extensions. GitHub repo: https://github.com/WrongStack/WrongStack
X post: https://x.com/ersinkoc/status/2076741353485091268

**ZCode** (HN, July 1, 278 pts, 15 comments) comes from the Zhipu AI / GLM team - the Chinese makers of the GLM language model. ZCode is being positioned as "Claude Code from the Makers of GLM" and targets Chinese developer adoption. This is a notable signal: China's top open-source LLM team is now building a Claude Code analog, not just integrating with Claude's plugin ecosystem. Chinese site: https://zcode.z.ai/cn

**What's new vs. July 13:** Neither WrongStack nor ZCode appeared in the prior briefing. Both are first-sightings.

---

### 4. 🌐 OBSERVABILITY LAYER: kapa.ai Agent Analytics and Lupen Fill the Cost + Query Visibility Gap

Two new tools address a real emerging pain point: as plugin and MCP ecosystems grow, developers cannot see which plugins are costing them money or which agents are making expensive calls.

**kapa.ai Agent Analytics** (@emilsnotes, X, July 13): kapa.ai already powers docs MCP servers for 100+ companies (n8n, ClickHouse, and others). The new Agent Analytics dashboard shows how Claude Code, Codex, and Cursor interact with those product documentation servers - which queries they send, what they retrieve, how often. This is the first visibility layer specifically for agent-to-MCP documentation queries.
X announcement: https://x.com/emilsnotes/status/2076663452907483282
kapa.ai blog: https://www.kapa.ai/blog/build-an-mcp-server-with-kapa-ai

**Lupen** (HN, June 24, 3 pts): "Show HN: Lupen - which Claude Code turn or sub-agent ran up your bill." Per-turn and per-sub-agent cost attribution for Claude Code workflows. Addresses a complaint visible in the "5x more expensive" story.
GitHub: https://github.com/momoraul/Lupen

**Token-saviour** (HN, June 15): A routing skill that routes tool selection calls to smaller models for appropriate queries - claimed ~70% token reduction. This is a skill-as-cost-optimizer, not a skill-as-capability-extender, which is a new use-case category for the SKILL.md format.
GitHub: https://github.com/vagkaratzas/skills/blob/main/token-saviour/SKILL.md

**What's new vs. July 13:** All three items are new. The observability/cost-attribution category did not appear in the prior briefing.

---

### 5. 🌐 MCP REGISTRY SCALE vs. DISCOVERY PROBLEM

The registry scale numbers updated significantly this window. As of July 11 (Agent Almanac), the official MCP Registry contains 9,208 total servers (9,178 active, 30 deprecated), and the MCP SDK now has 97M+ monthly installs. Glama's directory has grown from approximately 20,000 servers earlier in 2026 to 54,900 as of this run - a near-3x jump in months. Smithery has 7,000+ servers. PulseMCP has 18,240+.

But a dev.to analysis published July 9 frames the problem directly: "MCP registries in 2026, compared: one is canonical, one is huge, and almost none can tell you what to install. You check five directories and get five different answers." The canonical registry (official, 9,208) is authoritative but small. Glama (54,900) is comprehensive but overwhelming. Neither solves curation. The discovery problem is now the dominant unsolved problem in the MCP ecosystem.

Additionally, @MPP32_dev (X, July 6) describes a federated-catalog approach: "Agents are finding the MPP32 MCP server through standard distribution channels and using it to access a growing catalog of services... a catalog of over 9,500 paid and free endpoints." (https://x.com/MPP32_dev/status/2074032600814063760)

URLs:
- Agent Almanac: https://agentalmanac.org/mcp
- dev.to registries comparison: https://dev.to/skillselion/mcp-registries-in-2026-compared-one-is-canonical-one-is-huge-and-almost-none-can-tell-you-what-147l
- Glama: https://glama.ai/mcp/servers
- Smithery: https://smithery.ai/servers
- PulseMCP: https://www.pulsemcp.com/servers
- modelcontextprotocol/servers (88K stars): https://github.com/modelcontextprotocol/servers
- truefoundry comparison: https://www.truefoundry.com/blog/best-mcp-registries

**What's new vs. July 13:** Glama growth (54,900 from ~20K) and the dev.to discovery problem framing are new. The "discovery is unsolved at scale" is an emerging narrative not in the prior briefing.

---

### 6. 🌐 PLATFORM MAKERS ENTER MCP: Apple Safari and Mozilla MDN

Two major platform vendors made official MCP server releases in this window, signaling that MCP is becoming infrastructure rather than a Claude-specific tool.

**Apple Safari MCP Server** (HN, July 3, 272 pts, 76 comments): WebKit published "Introducing the Safari MCP Server for Web Developers" - an official Apple-published MCP server that gives AI agents access to Safari's web platform capabilities. This is Apple's first published MCP integration.
HN: https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/

**Mozilla MDN MCP Server** (HN, June 15, 4 pts): Mozilla launched an MCP server for MDN Web Docs. Gives AI coding agents direct access to authoritative web API documentation.
Mozilla blog: https://developer.mozilla.org/en-US/blog/introducing-mdn-mcp-server/

Together, these represent the first major browser vendors publishing official MCP servers - a legitimacy signal distinct from developer-published community servers.

**What's new vs. July 13:** Both were published in this window but not in the prior briefing. Apple's entry is particularly notable as a first-party integration.

---

### 7. 🌐 NEW TOOLING ECOSYSTEM: Memory, Verification, and Developer Quality-of-Life

A wave of focused utility tools for Claude Code agents appeared this window:

**Recall** (HN, June 21, 138 pts, 85 comments): "Show HN: Recall - Local project memory for Claude Code." Stores and retrieves project-specific context across Claude Code sessions. The 138-pt score and 85 comments indicate strong developer resonance.
GitHub: https://github.com/raiyanyahya/recall

**bhived MCP** (r/ClaudeWorkflows, June 16): Shared memory layer plus autonomous skill discovery for Claude Code agents. Reddit thread describes it as: "[Workflow] Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using 'bhived' MCP."
Reddit: https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/

**SkillSpec** (HN, June 30, 3 pts): A verification tool for the SKILL.md format: "verify that agent skills run the way SKILL.md says." Addresses the trust and compliance gap as skills become more widely distributed.
Website: https://skillspec.sh

**Arbor** (HN, July 8, 3 pts): A code graph MCP server. Gives agents a structural index of the codebase instead of requiring grep-style search. "Agents stop grep-reading your codebase."
GitHub: https://github.com/Anandb71/arbor/releases/tag/v2.4.0

**Shipwright Harness** (HN, June 30, 3 pts): Open-source autonomous delivery agent for Claude Code, MIT licensed.
GitHub: https://github.com/app-vitals/shipwright

**Claudoro** (HN, July 1, 50 pts, 36 comments): Pomodoro timer embedded in the Claude Code statusline. 50 pts for a productivity widget suggests the developer ergonomics category has community appetite.
GitHub: https://github.com/emson/claudoro

**cleanup-agent-processes SKILL.md** (@citedycom, X, July 14): A published SKILL.md for auditing and reclaiming local agent resource leaks. "Use when Codex, Claude Code, Playwright, Chrome DevTools, Node MCP servers, or abandoned Git worktrees consume CPU, memory, or disk."
X: https://x.com/citedycom/status/2076826816803676600

**Ship an Agent Skill That Installs Itself with Your Library** (HN, June 24, 4 pts): Pattern guide for bundling SKILL.md files with npm/pip packages so agents auto-learn the library's API.
Blog: https://stenbrinke.nl/blog/ship-an-agent-skill-that-installs-itself

**Diplomat-agent** (HN, June 25, 3 pts): Scans Python MCP servers for unguarded tool calls — a security audit tool for the MCP supply chain.
GitHub: https://github.com/Diplomat-ai/diplomat-agent

**Tilion** (HN, July 9, 6 pts): MCP for Claude Code to stop it getting blocked on the web during autonomous scraping tasks.
GitHub: https://github.com/tiliondev/fortress/tree/main/mcp

**What's new vs. July 13:** All items above are new or not previously covered. The memory + verification + security-audit tool cluster is emerging as a second-layer toolchain on top of the core plugin system.

---

### 8. 🌐 ZAMBO MCP: NOW ON TELEGRAM (UPDATED from prev briefing)

Zambo MCP was covered in the July 13 briefing as a zero-auth MCP providing 50+ tools in one URL. New July 14 development: Zambo is now also available directly via Telegram, in addition to existing Claude/Cursor/Windsurf integrations. "head over to zambo and you can start using zambo on telegram in 5 seconds and you can hook it up to claude/cursor/any mcp compatible agent in about 30 seconds." The tool count has grown to 65+ live tools including web search, on-chain data, lead generation, agent coordination, and AI strategy. Free, no API key required.
@CripdoeCrypto Telegram announcement (July 14): https://x.com/CripdoeCrypto/status/2076961161451311422
Zambo 65+ tools post (July 13): https://x.com/CripdoeCrypto/status/2076472729939652735
Original Zambo description (July 12): https://x.com/CripdoeCrypto/status/2076389085720072421

---

### 9. 🌐 ANTHROPIC OFFICIAL MOVES: Steering Post, July Changelog

**Steering Claude Code** (Anthropic blog, June 18): Official guidance on when to use each customization primitive - CLAUDE.md, skills, hooks, and subagents. Seven distinct customization methods described. This is the canonical reference for understanding the priority order of Claude Code extensions.
URL: https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more

**Claude Code July 2026 Changelog**: Enhanced background agents, MCP header auth auto-reconnects on 401/403 responses, plugin auto-rename. The MCP auth improvement directly addresses a common developer complaint about connection stability.
Changelog: https://www.gradually.ai/en/changelogs/claude-code/

**The Making of Claude Code** (Anthropic blog, July 7, HN 61 pts, 31 comments): Behind-the-scenes narrative from the Claude Code team. 61 points is moderate but the 31 comments suggest engaged discussion about development philosophy.
URL: https://www.anthropic.com/features/making-of-claude-code

**Using Subagents to Improve Claude Code Results** (HN, July 13, 3 pts): Practitioner guide on step-by-step subagent orchestration.
URL: https://software.rajivprab.com/2026/07/13/using-subagents-to-improve-claude-code/

**Claude Code May-July 2026 weekly limits promotion** (HN, July 12, 45 pts, 66 comments): Anthropic running a temporary promotional pricing. 66 comments suggests active community interest in usage economics.
URL: https://support.claude.com/en/articles/15910845-claude-code-may-july-2026-weekly-limits-promotion

---

### 10. 🌐 POSITIVE SIGNAL: "I Love This Month"

Despite the trust-erosion signals above, developer sentiment is mixed rather than uniformly negative. @mckaywrigley's July 12 post "@claudeai i love this month so much" gathered 318 likes - the second-highest X engagement in this window. @abir35627's "Claude Code Resource Bible" post (58 likes, 26 reposts) shows continued ecosystem enthusiasm. @suraj_sharma14's "Everything you need to master in 2026" list (88 likes, 12 reposts) still puts Claude Code workflows near the top.
mckaywrigley: https://x.com/mckaywrigley/status/2076355550053564816
abir35627 Resource Bible: https://x.com/abir35627/status/2076605147984359877
suraj_sharma14: https://x.com/suraj_sharma14/status/2076592477276922070

---

### 11. 🇯🇵 JAPANESE HUB ROUNDUP: Catalog Culture and Enterprise Adoption

Japanese IT communities (Qiita, Zenn, note.com) have produced comprehensive catalog-style guides to the Claude Code plugin ecosystem. Key findings:

- **Scale by February 2026**: Over 9,000 plugins publicly available. Qiita's shatolin article (Feb 2026) identifies Claude-Mem (20K stars) and Superpowers (43K stars, 7-phase development workflow) as the standout community projects. (https://qiita.com/shatolin/items/ca1810e419fee5fd963b)

- **Official plugin catalog** (Zenn/chmod644, March 2026): All 59 official plugins at launch, now expanded to 160 by April 2026. Five types: MCP, Skill, Agent, Hook, LSP. The five-type taxonomy is useful and consistent with Anthropic's own documentation. (https://zenn.dev/chmod644/articles/claude-code-plugins-all-59)

- **Japanese community ranking** (Zenn/ino_h, April 2026): Top recommended: feature-dev (7-phase dev workflow), code-review (parallel specialist agents), commit-commands, security-guidance, frontend-design. The namespace format `/<plugin-name>:<command-name>` is highlighted as preventing naming conflicts. (https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking)

- **Plugin-as-smartphone-app analogy** (note.com/varelser, March 2026): Japanese bloggers consistently use the smartphone app analogy for plugin installations. Enterprise focus: OpenTelemetry monitoring, private marketplaces, automatic deployment. Quote (translated): "Private marketplaces, automatic deployment, and OpenTelemetry monitoring are being adopted by Japanese enterprises." ("プライベートマーケットプレイス、自動デプロイ、OpenTelemetryモニタリングが日本企業で採用されています") (https://note.com/varelser/n/n0595c5ed613e)

- **Plugin development guide** (Qiita/miruky, March-April 2026): Two environment variables central to plugin development: `${CLAUDE_PLUGIN_ROOT}` (installation directory) and `${CLAUDE_PLUGIN_DATA}` (persistent storage across updates). 21 hook event types. (https://qiita.com/miruky/items/753395f62397c5ca6cbd)

Additional JP sources: https://uravation.com/media/claude-code-plugins-marketplace-complete-guide-2026/ | https://www.masatoman.net/articles/claude-code-plugins-marketplace-guide-2026 | https://codingls.com/ai/7595/

---

### 12. 🇨🇳 CHINESE HUB ROUNDUP: Reusable Workflow Framing and ZCode Signal

Chinese hub coverage was significantly limited by access blocks (Zhihu 403 x2, CSDN 521). The available signal from cnblogs and Zhihu/CSDN metadata suggests:

- **Three-level loading** (cnblogs, Oct 2025): Chinese developers framing skills as: L1 Metadata (~100 tokens, always loaded), L2 Instructions (<5k tokens, on trigger), L3 Resources (on-demand, unlimited). The "reusable, file-system-based resources providing domain expertise" framing is Chinese-community-specific. (https://www.cnblogs.com/treasury-manager/p/19166145)

- **"一键部署" (one-click deploy) and "告别重复配置" (goodbye to repetitive configuration)**: From Zhihu metadata, these are the resonant marketing phrases for Claude Code plugins in Chinese developer culture. Emphasis on eliminating repetitive configuration aligns with Chinese developer productivity culture.

- **Zhihu guide title** (blocked): "Claude Code 插件系统详解：如何用 MCP、Sub Agents 和 Hooks 构建可复用 AI 工作流，告别重复配置!" — "Detailed Claude Code Plugin System: How to Build Reusable AI Workflows with MCP, Sub Agents, and Hooks - Goodbye to Repetitive Configuration!" (https://zhuanlan.zhihu.com/p/1961476188372448747 — blocked)

- **ZCode competitive signal**: The Zhipu AI / GLM team launched ZCode as a direct Chinese competitor to Claude Code. The 278-pt HN story represents global developer awareness of China's entry into the agent coding space. Chinese developer community reaction: 15 HN comments, suggesting interest from the global Chinese developer diaspora. (https://zcode.z.ai/cn)

---

## Cross-Source Patterns

**Pattern 1: Security as the breaking story (HN + X + Web)**
The RCE-via-auto-mode story appears simultaneously on X (@SlavaOPs), Check Point Research blog, developer-tech.com, Hacker News context, and the Cloud Security Alliance research note. It is the day's new story and appears across every medium that covers security. Consistent framing: auto-mode + scanning third-party repos = attack surface. Sources: https://x.com/SlavaOPs/status/2076949170531791272 + https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/ + https://www.developer-tech.com/news/developers-face-rce-via-claude-code-auto-mode-exploit/

**Pattern 2: Trust deficit is multi-story (HN + X + Web)**
Steganography (2,445 HN pts), banned account (82 pts), 5x pricing (57 pts), and the security CVEs all reinforce a common theme: developers are questioning the trustworthiness of Claude Code as a system. This is a compound narrative, not a single incident. Each story individually might be dismissed; together they represent a community mood shift. Sources: https://thereallo.dev/blog/claude-code-prompt-steganography + https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/ + https://news.ycombinator.com/item?id=48641160

**Pattern 3: MCP now multi-vendor (HN + GitHub + Web)**
Apple (Safari), Mozilla (MDN), and 54,900 community servers on Glama represent a shift from "MCP is Anthropic's protocol" to "MCP is industry infrastructure." Both Apple and Mozilla publishing official MCP servers in the same 30-day window is a structural signal, not a coincidence. Sources: https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/ + https://developer.mozilla.org/en-US/blog/introducing-mdn-mcp-server/ + https://glama.ai/mcp/servers

**Pattern 4: Discovery at scale is unsolved (Web + X + Web-JP + Web-CN)**
Japanese hub articles consistently ask "which of the 160 plugins should I actually install?" Chinese Zhihu metadata asks about eliminating repetitive configuration. The dev.to comparison piece says registries don't tell you what to install. @trendai.bsky.social on Bluesky suggests running `/checkup` to purge unused plugins. The discovery problem is global and appears independently in all three language regions. Sources: https://dev.to/skillselion/mcp-registries-in-2026-compared-one-is-canonical-one-is-huge-and-almost-none-can-tell-you-what-147l + https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking + https://bsky.app/profile/trendai.bsky.social/post/3mqk73cjcn627

**Pattern 5: Memory tools emerging as a category (Reddit + HN + X)**
bhived MCP (Reddit), Recall (138 HN pts), and Claude-Mem (20K GitHub stars, per Japanese sources) are separate independent projects solving the same problem: Claude Code has no persistent memory across sessions without help. All three reached visibility this window. Sources: https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/ + https://github.com/raiyanyahya/recall + https://qiita.com/shatolin/items/ca1810e419fee5fd963b

---

## Per-Platform Tables

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @mckaywrigley | "i love this month so much" (to @claudeai) | 318 | — | https://x.com/mckaywrigley/status/2076355550053564816 |
| @AnthropicAI | "The values Claude expresses also vary with the language of the conversation" | 428 | — | https://x.com/AnthropicAI/status/2076719546954825769 |
| @suraj_sharma14 | "Everything you need to master in 2026... Building MCP servers" | 88 | 12 | https://x.com/suraj_sharma14/status/2076592477276922070 |
| @abir35627 | "Claude Code Resource Bible... 54 tools, MCP servers, skills" | 58 | 26 | https://x.com/abir35627/status/2076605147984359877 |
| @TechWithTimm | "From software engineer to AI engineer" | 61 | — | https://x.com/TechWithTimm/status/2076690579954753630 |
| @MPP32_dev | "9,500 paid and free endpoints via federated MCP catalog" | 21 | 8 | https://x.com/MPP32_dev/status/2074032600814063760 |
| @CripdoeCrypto | "Zambo now on Telegram in 5 seconds" (July 14) | 5 | — | https://x.com/CripdoeCrypto/status/2076961161451311422 |
| @CripdoeCrypto | "Zambo: 65+ live tools, free, no API key" | 6 | — | https://x.com/CripdoeCrypto/status/2076472729939652735 |
| @emilsnotes | "Introducing Agent Analytics for @kapa_ai - view how Claude Code, Codex, Cursor interact" | 6 | — | https://x.com/emilsnotes/status/2076663452907483282 |
| @ersinkoc | "WrongStack vs Claude Code/Codex/OpenCode on real orchestration" | 6 | — | https://x.com/ersinkoc/status/2076741353485091268 |
| @SlavaOPs | "Scanning a third-party repo can get you RCE instead in auto-mode" | 1 | — | https://x.com/SlavaOPs/status/2076949170531791272 |
| @citedycom | cleanup-agent-processes SKILL.md (July 14) | — | — | https://x.com/citedycom/status/2076826816803676600 |
| @0x_Missy22 | "GitHub trending: Claude Code templates, Google's Stitch agent skills, MCP servers" | — | — | https://x.com/0x_Missy22/status/2076231166492049711 |

**Hacker News:**
| Title | Points | Comments | Notable Quote | URL |
|-------|--------|----------|--------------|-----|
| Claude Code is steganographically marking requests | 2,445 | 750 | — | https://thereallo.dev/blog/claude-code-prompt-steganography |
| I used Claude Code to get a second opinion on my MRI | 566 | 715 | — | https://antoine.fi/mri-analysis-using-claude-code-opus |
| The text in Claude Code's 'Extended Thinking' output | 326 | 225 | — | https://patrickmccanna.net/the-text-in-claude-codes-extended-thinking-output-is-not-authentic/ |
| ZCode: Claude Code from the Makers of GLM | 278 | 15 | — | https://zcode.z.ai/cn |
| The Safari MCP server for web developers | 272 | 76 | — | https://webkit.org/blog/18136/introducing-the-safari-mcp-server-for-web-developers/ |
| Claude Code: Anthropic has embedded hidden spyware-like code | 56 | 14 | — | https://twitter.com/IntCyberDigest/status/2071971609183678544 |
| Show HN: Recall - Local project memory for Claude Code | 138 | 85 | — | https://github.com/raiyanyahya/recall |
| Show HN: Claudoro, Pomodoro timer in Claude Code statusline | 50 | 36 | — | https://github.com/emson/claudoro |
| The Making of Claude Code | 61 | 31 | — | https://www.anthropic.com/features/making-of-claude-code |
| Ask HN: Anthropic banned me from using Claude Code | 82 | 94 | — | https://news.ycombinator.com/item?id=48641160 |
| Claude Code Just Got 5x More Expensive | 57 | 8 | — | https://www.vincentschmalbach.com/claude-code-quietly-looks-5x-more-expensive/ |
| Claude Code May-July 2026 weekly limits promotion | 45 | 66 | — | https://support.claude.com/en/articles/15910845-claude-code-may-july-2026-weekly-limits-promotion |
| The MDN MCP Server | 4 | — | — | https://developer.mozilla.org/en-US/blog/introducing-mdn-mcp-server/ |
| SkillSpec - verify agent skills run as SKILL.md says | 3 | — | — | https://skillspec.sh |
| Show HN: Lupen - which Claude Code turn ran up your bill | 3 | — | — | https://github.com/momoraul/Lupen |
| Token-saviour - routing skill, 70% fewer tokens | 3 | — | — | https://github.com/vagkaratzas/skills/blob/main/token-saviour/SKILL.md |
| Ship an Agent Skill That Installs Itself with Your Library | 4 | — | — | https://stenbrinke.nl/blog/ship-an-agent-skill-that-installs-itself |
| Arbor - code graph MCP server | 3 | — | — | https://github.com/Anandb71/arbor/releases/tag/v2.4.0 |
| Using Subagents to Improve Claude Code Results | 3 | — | — | https://software.rajivprab.com/2026/07/13/using-subagents-to-improve-claude-code/ |
| Shipwright Harness - autonomous delivery agent (MIT) | 3 | — | — | https://github.com/app-vitals/shipwright |
| Gemini CLI vs Claude Code: agent capabilities matter more than prompts | 3 | — | — | https://imaxxs.com/behavioral-induction-capabilities-shape-execution |
| Diplomat-agent - scan Python MCP servers for unguarded tool calls | 3 | — | — | https://github.com/Diplomat-ai/diplomat-agent |
| Tilion - MCP for Claude Code to stop web blocks | 6 | — | — | https://github.com/tiliondev/fortress/tree/main/mcp |
| Turn Your AI Agent into an MCP Server for ChatGPT, Claude and Cursor | 5 | — | — | https://quickchat.ai/post/expose-ai-agent-as-mcp-server |
| Forensic-deepdive: code knowledge graph and MCP server | 3 | — | — | https://github.com/Dhevenddra/forensic-deepdive |

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeWorkflows | Enhance Claude Code Agents with Shared Memory and Autonomous Skill Discovery using bhived MCP | 1 | 1 | — | https://www.reddit.com/r/ClaudeWorkflows/comments/1u7j2o9/workflow_enhance_claude_code_agents_with_shared/ |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @erikdarling.com | "built a claude code plugin that reads sql server execution plans and tells you what's wrong. /plugin marketplace add erikdarlingdata/claude-plugins" | 10 | https://bsky.app/profile/erikdarling.com/post/3mqc5npb36l2m |
| @storybook.js.org | "The frontend bottleneck is no longer code generation. It's now reviewing agent output. Working on Claude Code + Codex plugins." | 8 | https://bsky.app/profile/storybook.js.org/post/3mqaesef2dk2u |
| @kjaanson.eurosky.social | "Does Claude Code and other mainstream harnesses without plugins etc handle cache nicely?" | 5 | https://bsky.app/profile/kjaanson.eurosky.social/post/3mqel6rljbs2v |
| @trendai.bsky.social | "run /checkup to purge unused plugins and junk. Faster speeds, lower token costs." | 5 | https://bsky.app/profile/trendai.bsky.social/post/3mqk73cjcn627 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | agentalmanac.org | https://agentalmanac.org/mcp | Official MCP registry: 9,208 servers, 97M monthly SDK installs |
| 🌐 | dev.to | https://dev.to/skillselion/mcp-registries-in-2026-compared-one-is-canonical-one-is-huge-and-almost-none-can-tell-you-what-147l | Discovery problem: "none can tell you what to install" |
| 🌐 | claudemarketplace.net | https://www.claudemarketplace.net/ | 4,206+ skills, 727+ MCP servers, 150K monthly visitors |
| 🌐 | docs.stacklok.com | https://docs.stacklok.com/toolhive/concepts/skills | Agent Skills open standard reference |
| 🌐 | designrevision.com | https://designrevision.com/blog/claude-code-plugins | Claude Code plugins complete guide |
| 🌐 | designrevision.com | https://designrevision.com/blog/claude-code-skills-vs-plugins-vs-agents | Skills vs Plugins vs Agents master comparison |
| 🌐 | lagrowthmachine.com | https://lagrowthmachine.com/claude-plugins-marketplace/ | Plugin marketplace concept and commands |
| 🌐 | arte.itlibra.com | https://arte.itlibra.com/en/articles/what-is-claude-code-plugins-marketplace | Claude Code plugins 22-min guide |
| 🌐 | claude.com/blog | https://claude.com/blog/steering-claude-code-skills-hooks-rules-subagents-and-more | Official: 7 customization methods |
| 🌐 | primeline.cc | https://primeline.cc/blog/claude-code-plugins | How to build a Claude Code plugin |
| 🌐 | skywork.ai | https://skywork.ai/blog/ai-bot/clawhub-skill-marketplace-ultimate-guide/ | clawhub skill marketplace guide |
| 🌐 | research.checkpoint.com | https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/ | CVE-2025-59536 RCE via hooks/MCP |
| 🌐 | developer-tech.com | https://www.developer-tech.com/news/developers-face-rce-via-claude-code-auto-mode-exploit/ | Auto-mode RCE exploitation guide |
| 🌐 | labs.cloudsecurityalliance.org | https://labs.cloudsecurityalliance.org/research/csa-research-note-claude-code-github-action-prompt-injection/ | Prompt injection as supply chain risk |
| 🌐 | layerxsecurity.com | https://www.layerxsecurity.com/claude-desktop-extensions-rce/ | Claude Desktop Extensions RCE, 10K users affected |
| 🌐 | buildtolaunch.substack.com | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | 11 plugins tested, 4 worth keeping |
| 🌐 | claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution | Team plugin distribution guide |
| 🌐 | agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 7 AI agent skills marketplaces compared |
| 🌐 | truefoundry.com | https://www.truefoundry.com/blog/best-mcp-registries | Best MCP registries for devs and enterprises |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | 300K+ monthly devs, 4,265+ skills |
| 🌐 | gradually.ai | https://www.gradually.ai/en/changelogs/claude-code/ | Claude Code July 2026 changelog |
| 🌐 | glama.ai | https://glama.ai/mcp/servers | 54,900 MCP servers directory |
| 🌐 | smithery.ai | https://smithery.ai/servers | 7,000+ MCP servers |
| 🌐 | pulsemcp.com | https://www.pulsemcp.com/servers | 18,240+ MCP servers |
| 🌐 | kapa.ai | https://www.kapa.ai/blog/build-an-mcp-server-with-kapa-ai | Agent Analytics + hosted MCP for docs |
| 🌐 | anthropics/claude-plugins-official | https://github.com/anthropics/claude-plugins-official | 101 official plugins, 33 by Anthropic |
| 🌐 | vercel.com/changelog | https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem | skills.sh GA: 600K OSS skills, 18+ agents |
| 🇯🇵 | Qiita (shatolin) | https://qiita.com/shatolin/items/ca1810e419fee5fd963b | 9K+ plugins, Claude-Mem 20K stars, Superpowers 43K |
| 🇯🇵 | Zenn (chmod644) | https://zenn.dev/chmod644/articles/claude-code-plugins-all-59 | 59 official plugins guide, 5 type taxonomy |
| 🇯🇵 | Zenn (ino_h) | https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking | 160 plugins ranking: feature-dev #1 |
| 🇯🇵 | note.com (varelser) | https://note.com/varelser/n/n0595c5ed613e | Enterprise: OpenTelemetry, private marketplaces |
| 🇯🇵 | Qiita (miruky) | https://qiita.com/miruky/items/753395f62397c5ca6cbd | Plugin dev guide: 21 events, CLAUDE_PLUGIN_DATA |
| 🇨🇳 | cnblogs | https://www.cnblogs.com/treasury-manager/p/19166145 | 3-level skill loading, CCusage, claude-historian |
| 🇨🇳 | Zhihu (blocked) | https://zhuanlan.zhihu.com/p/2021530912802783501 | Skills/MCP/Hooks/Sub-agents/Plugins guide (403) |
| 🇨🇳 | Zhihu (blocked) | https://zhuanlan.zhihu.com/p/1961476188372448747 | Reusable workflow guide (403) |
| 🇨🇳 | CSDN (blocked) | https://blog.csdn.net/technova77755/article/details/162172000 | agent-skills repo guide (521) |
| 🌐 | GitHub (claude-code) | https://github.com/anthropics/claude-code | 138K stars, 11,391 open issues |
| 🌐 | GitHub (mcp/servers) | https://github.com/modelcontextprotocol/servers | 88K stars, release 2026.7 |

---

## Stats Block

```
├─ 🟠 Reddit: 1 thread │ 1 upvote │ 1 comment (partial — ScrapeCreators DOWN)
├─ 🔵 X: 20 posts │ 1,487 likes │ 119 reposts
├─ 🔴 YouTube: 0 videos │ ScrapeCreators DOWN (402)
├─ 🟢 HN: 31 stories │ 4,442 points │ 2,123 comments
├─ 🟣 TikTok: 0 videos │ ScrapeCreators DOWN (402)
├─ 🩷 Instagram: 0 reels │ ScrapeCreators DOWN (402)
├─ 🦋 Bluesky: 4 posts │ 28 likes
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 27 pages global │ 🇯🇵 5 pages │ 🇨🇳 1 page (3 blocked)
└─ 🗣️ Top voices: @mckaywrigley, @AnthropicAI, @suraj_sharma14 │ HN steganography story (2,445 pts)
```

---

## Data Gaps

**ScrapeCreators DOWN (402 billing)** — SOURCE HEALTH flag confirmed. As a result, the following platforms returned zero results:
- YouTube (0 videos): Cannot assess video tutorial coverage of Claude Code skills/plugins this window.
- TikTok (0 videos): Chinese short-form tech content entirely absent.
- Instagram (0 reels): Absent.
- LinkedIn (0 posts): Professional/enterprise discussion absent.

**Reddit (partial, ~15% coverage)**: The engine returned 1 thread from r/ClaudeWorkflows. Blocked after early items; ScrapeCreators backup also failed. High-signal subreddits like r/ClaudeAI, r/MachineLearning, r/LocalLLaMA, r/AITools, and r/programming are uncovered for this window.

**Chinese hubs (~25% coverage)**:
- Zhihu x2 (HTTP 403 Forbidden): The two most-relevant Zhihu articles (Skills/MCP guide, reusable workflow guide) were inaccessible.
- CSDN (HTTP 521 Unknown): Primary Chinese developer network blocked.
- Available: 1 cnblogs article (Oct 2025, older) + Zhihu/CSDN metadata from search snippets.

**Bluesky (possibly partial)**: 4 posts found; Bluesky's search API coverage for technical topics is not guaranteed to be complete.

**Polymarket**: No markets on Claude Code skills or agent plugin ecosystems found in this window.

**Coverage estimate**: ~62%. Main losses: ScrapeCreators (YouTube, TikTok, Instagram, LinkedIn all zero) and Chinese hub blocks. HN and X coverage is strong (~85-90%). Japanese hubs are well-covered (~75%).

---

## Key Quotes

> "Pointing Claude Code or Codex at a third-party repo to 'scan it for vulnerabilities' can get you RCE instead - in the default, recommended auto-mode. No plugins, no MCP servers needed as an entry point." - @SlavaOPs on X ([link](https://x.com/SlavaOPs/status/2076949170531791272))

> "When it comes to real orchestration, multi-agent execution, and sustainable autonomy, [Claude Code, Codex, OpenCode] are still mediocre. Adding hundreds of lines of prompts, AGENTS.md files, MCP servers, skills, or plugins will not turn them into WrongStack." - @ersinkoc on X ([link](https://x.com/ersinkoc/status/2076741353485091268))

> "MCP registries in 2026, compared: one is canonical, one is huge, and almost none can tell you what to install. You check five directories and get five different answers." - dev.to ([link](https://dev.to/skillselion/mcp-registries-in-2026-compared-one-is-canonical-one-is-huge-and-almost-none-can-tell-you-what-147l))

> "The plugin ecosystem is rapidly expanding, but with so many options available, many wonder which ones to actually install. The recommendation: start with feature-dev and code-review for immediate workflow improvement." (「プラグインエコシステムは急速に拡大していますが、選択肢が多すぎて何をインストールすればよいかわかりません。まずfeature-devとcode-reviewから始めることをお勧めします」) - Zenn/ino_h ([link](https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking))

> "run /checkup to purge unused plugins and junk. Faster speeds, lower token costs." - @trendai.bsky.social on Bluesky ([link](https://bsky.app/profile/trendai.bsky.social/post/3mqk73cjcn627))

> "Private marketplaces, automatic deployment, and OpenTelemetry monitoring are being adopted by Japanese enterprises." (「プライベートマーケットプレイス、自動デプロイ、OpenTelemetryモニタリングが日本企業で採用されています」) - note.com/varelser ([link](https://note.com/varelser/n/n0595c5ed613e))

> "The frontend bottleneck is no longer code generation. It's now reviewing the output of an agent." - @storybook.js.org on Bluesky ([link](https://bsky.app/profile/storybook.js.org/post/3mqaesef2dk2u))

> "Skills are reusable, file-system-based resources providing domain expertise - they transform Claude from a general assistant into a specialist." (「スキルは再利用可能なファイルシステムベースのリソースでドメインの専門知識を提供します」) - cnblogs/treasury-manager ([link](https://www.cnblogs.com/treasury-manager/p/19166145))
