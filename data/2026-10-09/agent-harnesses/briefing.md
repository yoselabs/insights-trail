# AI Agent Harnesses — Daily Briefing
**Date:** 2026-10-09
**Query type:** GENERAL
**Sources:** HN, Web (global), Web (Japan), Web (China), GitHub Trending (coddykit/agents-radar), Releasebot, ccleaks, Antigravity changelog, Claude Haiku 5.5 announcement, syusodo.co.jp, gihyo.jp, hexabase.com, uravation.com, zenn.dev, qiita.com, note.com, apifox.com, 80aj.com, 53ai.com, cnblogs.com, zhihu, vocus.cc

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 stories | 702+365+337+187+67+61+28+25+20+8 pts, ~900 comments | 🌐 Haiku 5.5 dominant (702/349); Docker Agent 187/85; Jotbus 28/17 |
| Web (global) | 65+ pages | — | 🌐 WebSearch + WebFetch; Releasebot, coddykit, simonwillison, techtimes |
| Web (Japan) | 10 pages | — | 🇯🇵 gihyo.jp, hexabase.com, uravation.com, syusodo.co.jp, zenn.dev, note.com, qiita.com, myclaw.ai, stork.ai, oratta/claude-harness |
| Web (China) | 12 pages | — | 🇨🇳 apifox.com, 80aj.com, easyclaude.com, 53ai.com, cnblogs.com, vocus.cc, tmtpost.com, openhumanai.cn, zhihu, KimYx0207 GitHub |
| GitHub Trending | 5 digests | — | 🌐 coddykit Oct 2026 series; agents-radar Oct 7–9 |
| last30days skill | 0 | — | Unavailable; full manual sweep performed |

---

## Synthesized Findings

### 1. [new] Claude Haiku 5.5 (Oct 7): sub-agent economics shift — $0.10/M, OSWorld 72.4%, adjustable effort 🌐🇯🇵🇨🇳

**Claim:** Anthropic shipped Claude Haiku 5.5 (Oct 7): $0.10/M input (≤100K tokens, ~75% cheaper than Haiku 4.5), 1M context, first small model to reach the human baseline on computer use (OSWorld 2.1 72.4%), and the first Haiku-class with adjustable effort (Low/Med/High/Xhigh/Max). Default Haiku in CC v2.1.293 same day. HN: 702 pts / 349 comments.

**Evidence:**
- **Price:** $0.10/M input (≤100K), $0.50/M (>100K); $0.50/M output (≤100K), $2.50/M (>100K); ~75% cheaper overall
- **Context/output:** 1M token context; up to 128K output tokens
- **OSWorld 2.1:** 72.4% (human baseline = 72.4%); prior Haiku 4.5 = 15.7%; first small model at human level on this benchmark
- **Terminal-Bench 4.0:** 39.2% (was 0.0% for Haiku 4.5); Humanity's Last Exam: 45.9% / 57.4% (tools)
- **Effort settings:** first Haiku-class model with adjustable effort — enables cost/capability tradeoff within sub-agent tiers
- **CC v2.1.293:** Haiku 5.5 auto-promoted to default Haiku model (same-day deploy)
- **Cognition Devin Fusion demo:** Haiku 5.5 "sidekick" + Opus 5.5 lead planner → FrontierCode 1.1 = 66.2 at lower cost+latency than single-model
- **Asana:** 30%+ latency reduction; up to 2.5x faster inference per agent turn
- **Harness pattern:** recommended to put Explore/compaction/summarization tasks on Haiku 5.5; complex planning stays on Sonnet/Opus
- **JP:** myclaw.ai review; note.com/iam_lima head-to-head vs Opus 5.5; penchan.co pricing analysis ([link](https://penchan.co/ai/claude/haiku-5-5/)) 🇯🇵
- **CN:** apifox.com "sub-agent engine swap" framing; vocus.cc "low-cost agent explosion October 2026"; 80aj.com sub-agents + browsers; easyclaude.com "CC sub-agent cost cut 75%" 🇨🇳
- **Sources:** [Anthropic](https://www.anthropic.com/claude-haiku-5-5), [HN](https://news.ycombinator.com/item?id=49996437), [Beam.ai sub-agent analysis](https://beam.ai/agentic-insights/claude-haiku-5-5-subagents), [TechTimes](https://www.techtimes.com/articles/328793/20261009/claude-haiku-55-becomes-viable-sub-agent-human-level-computer-use-ninety-percent-lower-cost.htm), [developersdigest Haiku vs Luna](https://www.developersdigest.tech/blog/haiku-5-5-vs-gpt-6-luna-subagent), [simonwillison](https://simonwillison.net/2026/Oct/7/claude-haiku-5-5/), [80aj.com](https://www.80aj.com/2026/10/08/claude-haiku-55-subagents/), [apifox.com](https://apifox.com/apiskills/claude-haiku-5-5-subagent-pricing/), [easyclaude.com](https://easyclaude.com/post/claude-haiku-5-5-release-ai-coding-subagent-cost-cut), [vocus.cc](https://vocus.cc/article/6ac7870cfd89780001022325)

---

### 2. [update] Claude Code v2.1.292–293 (Oct 6–7): plugin marketplace install, sub-agent effort control, Haiku 5.5 default 🌐

**Claim:** NEW FACTS — v2.1.292 (Oct 6) adds `--marketplace` flag to `claude plugin install` and an `effort` parameter for the Agent tool (sub-agent performance level); closes 6 sandbox/permission security holes. v2.1.293 (Oct 7) promotes Haiku 5.5 as default Haiku model and adds `isDeferred` for mod tool schema control.

**Evidence:**
- **v2.1.292 new capabilities:** `claude plugin install --marketplace` (adds marketplace source + installs under same policy); `effort` param for Agent tool (low/medium/high/xhigh/max per sub-agent call); `prompt.autocomplete` event hook; prompt caching in `$.model.complete` for mods
- **v2.1.292 security:** sandbox vuln (reads of staged file copies) closed; mid-session symlink swap exploit fixed; auto-mode permission bypass for network paths blocked — six holes total
- **v2.1.292 perf:** faster large file rendering; improved `-p` / SDK startup skipping MCP resource checks
- **v2.1.293 additions:** Haiku 5.5 as default; `agentType` in subagent status payloads; `isDeferred` for mods; OpenTelemetry caps agent/MCP-resource events at 100 each; reduced idle skill sync polling (10→40 min)
- **v2.1.293 fixes:** context compaction retraction bug; HTTP MCP connection memory leak; `/model` effort wrapping saving wrong default; `/tui` Chrome disconnection; Remote Control upload loop
- **Stars:** 149,532 (prior count; Oct 9 unconfirmed)
- **Sources:** [releasebot](https://releasebot.io/updates/anthropic/claude-code), [v2.1.292 release](https://github.com/anthropics/claude-code/releases/tag/v2.1.292), [ccleaks](https://ccleaks.com/news/claude-code-2-1-292-oct-2026), [havoptic](https://www.havoptic.com/tools/claude-code), [clockedcode](https://clockedcode.com/blog/claude-code-changelog), [gradually.ai](https://www.gradually.ai/en/changelogs/claude-code/)

---

### 3. [new] OpenHuman: Rust agent harness — 500 agents on $10 VPS, 2.6x fewer tokens 🌐🇯🇵🇨🇳

**Claim:** tinyhumansai/OpenHuman (41.7k stars, GPL-3.0, Rust) is the breakout general-purpose agent harness of this period: 500 live agents in one process fit in 1,393 MiB; 2.6x fewer tokens per task vs typical tools; 8x less memory; TokenJuice = up to 80% compression of tool outputs.

**Evidence:**
- **Architecture:** single in-process Rust bus; agents don't require separate daemons; Tauri shell + React UI
- **Scale:** 500 agents settle at 1,393 MiB total = 1,770 KiB marginal cost per additional agent; runs on $10 VPS
- **TokenJuice:** 80% token reduction via tool output + web scrape compression
- **Jev tool search:** routes from 1,215+ tools accurately
- **Integrations:** 14 messaging channels (Telegram, Discord, iMessage, email, etc.); 119 OAuth integrations (Composio); 5,000+ MCP servers; 26 LLM providers (local + BYOK)
- **Memory:** auto-fetch every 20 min; SQLite + Obsidian-compatible Markdown; auditable local memory — "You can't trust a memory you can't read"
- **JP coverage:** syusodo.co.jp full architecture analysis; official JP README ([docs/README.ja-JP.md](https://github.com/tinyhumansai/openhuman/blob/main/docs/README.ja-JP.md)); stork.ai evaluation 🇯🇵
- **CN coverage:** tmtpost.com "topped GitHub, makes ordinary people gods"; cnblogs.com/itech detailed intro; openhumanai.cn tutorial site 🇨🇳
- **Caveat (JP/Starlog):** LLM calls, OAuth, TTS traverse OpenHuman's backend by default (not fully local despite claims); backend data routing is a concern for privacy-sensitive deployments
- **Sources:** [GitHub](https://github.com/tinyhumansai/openhuman), [openhumanterminal.tech](https://openhumanterminal.tech/), [syusodo.co.jp](https://syusodo.co.jp/tech-blog/articles/repo-tinyhumansai-openhuman), [pasqualepillitteri.it](https://pasqualepillitteri.it/en/news/2704/openhuman-open-source-ai-agent-local-memory), [starlog.is critical](https://starlog.is/articles/ai-agents/tinyhumansai-openhuman), [cnblogs](https://www.cnblogs.com/itech/p/20046824), [tmtpost.com](https://www.tmtpost.com/7987326.html)

---

### 4. [new] nanoMuse 1.0.0 Keel (Oct 9): cross-device personal agent — arXiv paper, HF Daily Papers #3 🌐🇨🇳

**Claim:** nanoMuse (nano-muse/nanoMuse, GPL-3.0) released v1.0.0 Keel on October 9, 2026: a personal AI agent for Android/iOS/desktop/browser with background execution, Markdown file memory, and a Sentinel security layer; arXiv:2610.08699 (Zhejiang University); HF Daily Papers #3 (Oct 8).

**Evidence:**
- **Cross-device:** Android app, iOS (TestFlight), macOS/Windows/Linux desktop, web app; self-hostable relay (nanoMuse Cloud) for cross-device sync
- **v1.0.0 Keel (Oct 9):** upgrades over prior version preserving user data; full release notes provided
- **Background execution:** keeps working while app is closed; stops to ask before irreversible actions (Sentinel layer = scoped approvals)
- **Memory:** Markdown file memory; phone screen + desktop as "hands"
- **Desktop harness backend:** plugin of DeepSeek Harness (Python runtime for screen operations)
- **arXiv:2610.08699:** "nanoMuse: An Open-Source Personal Agent for Every Device You Own" — Guangyi Liu, Yong Liu, Jiangning Zhang (Zhejiang University); HF Daily Papers #3 Oct 8
- **Notable:** DeepSeek Harness adoption as desktop plugin backend signals growing third-party harness ecosystem
- **CN:** nanomuse.cn CN landing page active 🇨🇳
- **Sources:** [GitHub](https://github.com/nano-muse/nanoMuse), [arXiv](https://arxiv.org/abs/2610.08699), [nano-muse.github.io](https://nano-muse.github.io/), [nanomuse.cn](https://nanomuse.cn/), [techbytes.app](https://techbytes.app/posts/nanomuse-an-open-source-personal-agent-for-every-device-you-own/), [dev.to analysis](https://dev.to/prabhakar_chaudhary_7afe4/nanomuse-is-a-system-not-a-model-building-a-personal-agent-across-your-devices-47fj)

---

### 5. [new] Jotbus (Show HN Oct 7, 28 pts): E2EE shared scratchpad across agents via MCP 🌐

**Claim:** Jotbus (Launchable-AI-Inc, Show HN Oct 7, 28 pts/17c): E2EE shared workspace for coding agents; `npx jotbus` creates a 60-minute encrypted workspace across CC/Codex/Cursor/12+ harnesses via MCP; keys never leave the client.

**Evidence:**
- **E2EE:** encryption happens locally; hosted relay stores only ciphertext; workspace key never reaches Jotbus
- **Use case:** transient work (logs, partial implementations, screenshots) not ready for Git history; agent hand-off across machines
- **Setup:** `npx jotbus` (no login/signup); configures connected agents via MCP; 60-minute encrypted workspace
- **Supported harnesses (12+):** CC, Codex, Cursor, Gemini CLI, GitHub Copilot CLI, OpenCode, Windsurf, Claude Desktop, Qwen Code, Amp, Augment, Kiro, JetBrains Junie
- **HN discussion:** tinthedev questions advantage vs private Git; creator (shake-n-fries) distinguishes transient vs persistent work; whalesalad mentions similar tool agentdrop.lol
- **Sources:** [HN](https://news.ycombinator.com/item?id=49978401), [jotbus.com](https://jotbus.com/), [GitHub](https://github.com/Launchable-AI-Inc/jotbus)

---

### 6. [new] cmux: Ghostty-based macOS terminal for parallel AI agent sessions (28.1k stars) 🌐🇯🇵

**Claim:** manaflow-ai/cmux (28.1k stars, GPL-3.0) is a macOS terminal built on libghostty designed for multi-agent parallel coding sessions: notification rings alert when an agent needs attention; sidebar shows per-pane git branch, PR status, port; Claude Code Teams integration; scriptable socket API.

**Evidence:**
- **Architecture:** libghostty (Ghostty terminal library); vertical + horizontal tabs; programmable CLI + socket API
- **Notification rings:** highlight specific panes/tabs when agents need attention (not relying on sound or polling)
- **Sidebar:** git branches, PR status, working dirs, ports per split
- **Built-in browser:** scriptable automation API; SSH support for remote workspaces
- **CC Teams integration:** multi-agent orchestration with visual status
- **Session restoration:** persists across app restarts; nightly update channel
- **Harness compatibility:** all terminal agents (CC, Codex, OpenCode, Gemini CLI, Aider, etc.)
- **Stars trending:** 27,731 (coddykit Oct 9 digest); appears in coddykit "Ghostty-Based Terminals" trending article
- **Sources:** [GitHub](https://github.com/manaflow-ai/cmux), [coddykit trending](https://www.coddykit.com/pages/blog-detail?id=5129963&slug=github-trending-october-2026-from-102k-star-agent-skills-to-ghostty-based-termin)

---

### 7. [new] agency-agents: 230+ specialized AI agents for 15+ harnesses (158.5k stars) 🌐

**Claim:** msitarzewski/agency-agents (158.5k stars, MIT, Shell) provides 230+ specialized AI agents in a "division" structure (Engineering 60+, Design, Sales, Marketing, PM, Security, etc.) with unified format transpiling across 15+ harnesses including CC, Copilot, Cursor, Antigravity, OpenCode, OpenClaw, Hermes, DeepSeek.

**Evidence:**
- **230+ agents** with unique personality, domain expertise, deliverable-focused workflows, and measurable success metrics
- **15+ harnesses:** CC, GitHub Copilot, Cursor, Antigravity, OpenCode, Windsurf, Aider, OpenClaw, Qwen, Kimi, Codex, Osaurus, Hermes, DeepSeek, others
- **Division structure:** functional teams (Engineering, Security, Finance, Game Dev, GIS, Healthcare, etc.)
- **Transpilation:** unified format for cross-harness agent personality portability
- **Recent additions:** sovereign health systems agents, knowledge graph engineers, privacy engineers, multi-agent orchestration specialists
- **Sources:** [GitHub](https://github.com/msitarzewski/agency-agents), [coddykit analysis](https://www.coddykit.com/pages/blog-detail?id=5129960&slug=github-trending-october-2026-from-157k-star-agent-agencies-to-sandboxed-ai-opera)

---

### 8. [new] trycua/cua: Computer-Use 2.0 fleet platform — cross-OS, CUA-S1 models, fleet benchmarking 🌐

**Claim:** trycua/cua (29.2k stars, MIT) is a comprehensive computer-use agent infrastructure in Rust: cross-platform drivers (macOS/Windows/Linux), Cua Spaces virtual desktops, CUA-S1 specialized models, and Cua Bench for evaluation and training trajectory generation.

**Evidence:**
- **Cua Spaces:** full virtual desktops on macOS/Linux; teleportation of signed-in apps; multiplayer collaboration
- **Cua Driver:** inspect + operate native desktop apps cross-platform; background delivery support
- **Lume:** local VM mgmt on Apple Silicon via Virtualization.Framework
- **CUA-S1:** specialized System 1 models for computer-use decisions (especially form-filling)
- **Cua Bench:** create tasks, test agents, generate training trajectories
- **SDKs:** Python, TypeScript, Swift, Kotlin; unified interface for sandboxes, containers, remote machines
- **Positioning:** "Computer-Use 2.0" — fluid transition between code, APIs, and graphical interfaces within single tasks
- **Sources:** [GitHub](https://github.com/trycua/cua), [coddykit](https://www.coddykit.com/pages/blog-detail?id=5129963&slug=github-trending-october-2026-from-102k-star-agent-skills-to-ghostty-based-termin)

---

### 9. [new] Docker Agent (4.3k stars): declarative YAML multi-agent runtime — HN 187 pts 🌐

**Claim:** Docker shipped docker/docker-agent (4.3k stars, Apache 2.0), a declarative YAML multi-agent runtime as a Docker CLI plugin; multi-agent orchestration, MCP tool ecosystem, 10+ provider support, OCI registry for packaging/sharing agents; HN 187 pts / 85 comments (Oct 8).

**Evidence:**
- **CLI:** `docker agent` — builds on Docker's existing infrastructure
- **YAML config:** define multi-agent teams without code; automatic task delegation across agents
- **MCP integration:** local, remote, Docker-based MCP servers; rich tool ecosystem
- **Providers:** OpenAI, Anthropic, Gemini, AWS Bedrock, Mistral, xAI, and more
- **OCI registry:** package + share agents as OCI artifacts
- **HN reception:** 187 pts / 85 comments; strong community interest; Docker's brand accelerates adoption
- **Sources:** [GitHub](https://github.com/docker/docker-agent), [HN Oct 8 digest](https://github.com/yaojiejia/agents-radar/issues/266)

---

### 10. [update] OpenClaw v2026.10.1-beta.2 (Oct 7): P0 memory leak still unresolved; beta progression 🌐

**Claim:** NEW FACT — v2026.10.1-beta.2 released Oct 7 (second beta iteration); SQLite WAL P0 memory leak (~4-5GB/hour) still unresolved; v2026.8.34 LTS still recommended for production; 391,453 stars.

**Evidence:**
- v2026.10.1-beta.2 (Oct 7): continued beta work; limited changelog details available
- v2026.10.1 core fixes (Oct 3–6): session state + memory preservation; workspace worker attachments; continuation signatures; embedding cache migration in bounded batches
- Two deprecation removals: agent-harness-terminal-result-aliases and official-plugin-export-aliases both reached 2026-10-01 removal target
- P0 still active: SQLite WAL leaks ~4-5GB/hour; clawstat.us advisory remains; LTS v2026.8.34 still recommended
- **Sources:** [releasebot OC](https://releasebot.io/updates/openclaw), [openclawlaunch.com/changelog](https://openclawlaunch.com/changelog), [clawstat.us](https://clawstat.us/)

---

### 11. [update] Hermes v0.21.6 (Oct 8): patch release; ~2,100 PRs since v0.21.5; v0.22.0 still deferred 🌐

**Claim:** NEW FACT — Hermes v0.21.6 released Oct 8; approximately 2,100 PRs merged since v0.21.5; full curated notes still deferred to v0.22.0.

**Evidence:**
- v0.21.6 (Oct 8): patch release; specific changelog items deferred to v0.22.0 comprehensive notes
- ~2,100 PRs merged since v0.21.5 (Sep 24); v0.22.0 remains the next release with full notes
- 251,464 stars (prior count)
- **Sources:** [hermes-ai.net/changelog](https://hermes-ai.net/changelog/), [gradually.ai Hermes](https://www.gradually.ai/en/changelogs/hermes-agent/), [GitHub releases](https://github.com/NousResearch/hermes-agent/releases)

---

### 12. [update] Antigravity CLI v1.3.1-1.3.2 (Oct 7–8): subagent messaging syntax, CJK fixes, headless improvements 🌐

**Claim:** NEW FACTS — Antigravity v1.3.1 (Oct 7) adds direct subagent messaging syntax and Vim numeric count multipliers; v1.3.2 (Oct 8) fixes /resume crash on narrow terminals and CJK character truncation.

**Evidence:**
- **v1.3.1 (Oct 7):** direct subagent messaging syntax; Vim numeric count multipliers; headless lifecycle handling + concurrency fixes; images scaled to max 2576px (was 4096) for Claude models
- **v1.3.2 (Oct 8):** `/resume` conversation picker crash on narrow terminals fixed; CJK character mid-character cut-off fixed; plugin manifests / mcp_config.json / hooks.json UTF-8 BOM load fix
- **Sources:** [antigravity changelog](https://antigravity.google/docs/changelog/), [releasebot Antigravity](https://releasebot.io/updates/google/antigravity), [GitHub releases](https://github.com/google-antigravity/antigravity-cli/releases)

---

### 13. [update] Cursor Remote Control for iOS (Oct 6): view + message local agents from iPhone 🌐

**Claim:** NEW FACT — Cursor shipped Remote Control on Oct 6: iOS app can monitor and message local agents running on a desktop; no cloud required; agent execution, files, and env stay on the paired computer.

**Evidence:**
- **How it works:** sign in to Cursor on iPhone → select computer in app → approve pairing on desktop → choose an agent to view + message
- **No cloud dependency:** doesn't move work to cloud agents; requires computer awake + online
- **Availability:** default on for most users; off for Enterprise orgs
- **Also:** 7% token efficiency cut (trimmed system prompts, dynamic tool loading, cache reuse, compressed file reads, subagent tuning) — separate from iOS feature
- **Sources:** [alphasignal.ai](https://alphasignal.ai/news/cursor-ships-remote-control-so-developers-run-local-agents-from-iphone), [releasebot Cursor](https://releasebot.io/updates/cursor), [superpowerdaily](https://superpowerdaily.com/posts/cursor-adds-ios-remote-control-for-coding-agents-running-on-a-computer)

---

### 14. [new] Pinrail (Show HN Oct 7–8, ~20 pts): human-in-the-loop desktop inbox for coding agents 🌐

**Claim:** forgeplane/Pinrail (34 stars, Apache 2.0) is a local-only desktop app providing structured review interfaces for coding agent actions; agents pause and submit decisions to Pinrail before proceeding; compatible with CC, Codex, Cursor, OpenCode.

**Evidence:**
- **5 plugin types:** code-review, list, feedback, markdown, image — each with a specialized review UI
- **Local-only:** API on loopback; reviews stored locally; no telemetry
- **Integration:** `pinrail` CLI command + skill teaches agents how to use it
- **HN Oct 7–8:** 20–25 pts / 4 comments; praised for safety; called "niche" by community
- **agentdrop.lol:** HN commenter mentions similar tool with file sharing + UI viewing
- **Sources:** [GitHub](https://github.com/forgeplane/pinrail), [HN](https://news.ycombinator.com/item?id=49995778)

---

### 15. [update] Cloudflare OS managed cloud waitlist opens (Oct 1): GitHub repo integration, Gadgets + Gatekeepers 🌐

**Claim:** NEW FACT — Cloudflare OS opened fully managed deployment waitlist Oct 1; added GitHub repo integration; agents can explore, fix bugs, open PRs directly.

**Evidence:**
- **Managed cloud:** waitlist opened Oct 1, 2026; previously open-source only
- **GitHub integration (new):** connect existing repos; agents can explore codebase, fix bugs, add features, open PRs
- **Gadgets:** sandboxed per-user apps (Durable Object Facets, isolated SQLite); shareable via Blueprints
- **Gatekeepers:** capability-based security for agents + apps; async human approval queue
- **Stars:** 11,300; Apache 2.0
- **Sources:** [cloudflare blog](https://blog.cloudflare.com/cloudflare-os/), [GitHub](https://github.com/cloudflare/cloudflare-os), [noise.getoto.net](https://noise.getoto.net/2026/10/01/cloudflare-os-your-companys-agent-workspace-managed-for-you/), [cloudflare.net press release](https://www.cloudflare.net/news/news-details/2026/Cloudflare-OS-Is-the-First-AI-Workspace-Built-Around-How-Companies-Actually-Work/default.aspx)

---

### 16. [update] JP harness engineering paradigm: gihyo.jp Oct 2026 article formalizes "Agentic Coding" 🇯🇵

**Claim:** NEW FACT — gihyo.jp published "Agentic Coding とハーネスエンジニアリング" (Oct 2026, Yohei Watanabe): formalizes Agentic Coding vs Vibe Coding distinction and internal/external harness framework; becomes a key JP reference.

**Evidence:**
- **Agentic Coding vs Vibe Coding:** Agentic = automated checks + rule files + sandboxing + verification hooks; Vibe = trusts generated code without validation
- **Internal vs External harness:** internal = agent product scaffolding; external = user-built environment
- **Key insight:** "Instructions to an agent disappear when the session ends; harness elements in the repository remain shared knowledge" (「エージェントへの直接指示はセッション終了とともに消えるが、リポジトリ内のハーネス要素は共有知識として残る」)
- **JP JP companion articles:** hexabase.com guide for CC/Cursor users; uravation.com Oct 2026 CC features guide; zenn.dev/ytksato bringing harness engineering to CC
- **Sources:** [gihyo.jp](https://gihyo.jp/article/2026/10/agentic-coding-and-harness-engineering), [hexabase.com](https://www.hexabase.com/column/harness-engineering-claude-code-cursor-guide), [zenn.dev ytksato](https://zenn.dev/ytksato/articles/1e4a5e6e033ddb), [uravation.com features](https://uravation.com/media/claude-code-features-20-2026/)

---

**Still true** (ongoing threads, no new facts Oct 7–9):
- **pi-minimal-agent-harness**: Pi 1.0 ongoing; v1.0.4 patch Oct 4 was last confirmed; no new releases Oct 7-9
- **offrun-multi-agent-workspace**: ongoing; no new updates
- **headlong-microharness-bash**: ongoing; no new releases
- **television-agent-gui-sidecar**: ongoing; low engagement
- **skills-security-prompt-injection-36pct**: ongoing; 157 malicious skills; STSS/skilltrust active
- **deepseek-harness-v01**: nanoMuse uses DSH as desktop backend (new adoption signal, but not a DSH release)
- **qwen-code-alibaba**: v0.25.0 still current; 28,375 stars Oct 9 confirmed
- **openclaw-gateway-harness**: (see finding #10 for update)
- **microsoft-maf-codeact**: v1.20.0 Oct 2 still current
- **antigravity-gemini-cli-successor**: (see finding #12 for update)
- **codex-cli-0155-voice-touchid**: no new releases Oct 7-9
- **codex-open-platform-harness**: ongoing
- **copilot-runtime-rust-rewrite**: no new releases Oct 7-9
- **github-copilot-skills-mcp-ga**: ongoing
- **harness-engineering-paradigm**: gihyo.jp new article (finding #16)
- **environment-architect-new-role**: gihyo.jp + hexabase.com reinforce (finding #16)
- **anthropic-managed-agents-mcp-tunnels**: CC v2.1.292–293 (finding #2)
- **claude-managed-agents-auto-permission**: CC v2.1.292 security fixes active
- **claude-code-mods-v2-1-287**: CC v2.1.292 adds isDeferred for mods
- **claude-code-mods-function-hooks**: CC v2.1.292 prompt caching in mods
- **extension-economy-explosion**: addyosmani/agent-skills now 102,488; obra/superpowers 294,967; mattpocock/skills 275,451 (potential update from coddykit data, not separately confirmed)
- **hermes-agent-self-improving**: (see finding #11)
- **sep-2640-mcp-skills-final**: still no mainstream default adoption
- **harness-context-tax-problem**: OpenHuman TokenJuice 80% compression new data point
- **nvidia-openshell-agent-runtime**: ongoing
- **weave-router-model-routing**: ongoing
- **mattpocock-skills-135k**: 275,451 stars (coddykit Oct 9, possible significant update but not independently confirmed)
- **openai-devday-2026-gpt61-dots**: ongoing
- **cn-miit-claude-code-notice**: ongoing; CN CC tutorials active (KimYx0207 CN subagent guide)
- **claude-sonnet-5-5**: ongoing
- **salesforce-enterprise-ai-harness**: ongoing
- **openrig-multi-agent-harness**: ongoing
- **hindsight-standalone-memory**: ongoing
- **jauvex-voice-multi-agent**: ongoing
- **claude-opus-5-5**: ongoing
- **google-ax-agentic-runtime**: ongoing
- **cursor-rollout-security-bots**: (see finding #13 for Remote Control iOS)
- **univer-office-harness**: 🇨🇳 ongoing
- **obra-superpowers-skills**: 294,967 stars (coddykit Oct 9; significant growth from prior)
- **hkuds-nanobot-personal-agent**: ongoing
- **gitspawn-class-vulnerability**: ongoing; 4 flaws unpatched
- **layered-oss-stack-over-single-framework**: ongoing
- **gpt6-astra-provider-adapter-harness**: ongoing
- **paperclip-multi-agent-company-os**: ongoing
- **aws-strands-harness**: ongoing
- **claude-code-projects-parallel-threads**: ongoing
- **openai-agents-api-beta**: ongoing
- **vscode-1138-dev-container-agents**: ongoing
- **cursor-router-workspace-plugins**: Remote Control iOS (finding #13)
- **cursor-projects-self-hosted-machines**: ongoing
- **reinventing-ai-employee-packages**: ongoing
- **builder-agent-native**: ongoing; **beam-cli-harness-observer**: ongoing; **meta-muse-code**: ongoing; **colibri-lumabri-moe-inference**: ongoing; **omarchy-herdr-agentic-linux**: ongoing; **agensi-skill-marketplace**: ongoing; **kilo-code-anaconda**: ongoing; **harness-io-agent-ready-scm**: ongoing
- **addy-osmani-agent-skills**: 102,488 stars (update from 89.6k; coddykit Oct 9 data)
- **orca-ade-parallel-fleet**: ongoing; **ponytail-laziest-dev-skill**: ongoing; **trueforge-open-source-harness**: ongoing; **aws-kiro-crew-open-source**: ongoing; **hiddenlayer-agent-harness-security**: ongoing; **longhorizon-harness-amap**: ongoing; **caspian-talk-to-human-tool**: ongoing; **kubell-whitelist-harness-tools**: ongoing; **block-berd-desktop-workspace**: ongoing; **loopx-long-horizon-control-plane**: ongoing; **cloudflare-computer-agent-runtime**: ongoing; **cursor-google-workspace-plugins**: ongoing; **huzzah-pseudocode-editor**: ongoing; **onecli-yc-s26-credential-gateway**: ongoing; **harnessrouter-uhp-open-standard**: ongoing
- **flue-2-react-hooks-harness**: ongoing; **hax-c-minimalist-agent**: ongoing; **copilot-autofix-dual-ai-security**: ongoing; **bullet-yc-s26-coding-agent**: ongoing; **book-to-skill-pdf-to-skill**: ongoing; **cursor-origin-code-hosting**: ongoing
- **prime-agent-rlm**: ongoing; **aq-multiplayer-harness**: ongoing; **oh-my-agent**: ongoing; **autoharness-deepmind**: ongoing; **hoplite-yc-s26-cloud-deploy**: ongoing; **vercel-ai-sdk-harnessagent**: ongoing; **copilot-studio-ga-harness-billing**: ongoing; **microsoft-agent-governance-toolkit**: ongoing; **tinyagents-rust-recursive**: ongoing; **sprocket-hardware-software-agent**: ongoing; **gambit-reliable-agent-harness**: ongoing; **nlah-natural-language-harnesses**: ongoing
- **claude-tag-slack-agent**: ongoing; **mimo-code-xiaomi**: 🇨🇳 ongoing; **ecc-cross-harness-os**: 272,365 stars (coddykit Oct 9); **kimi-code-moonshot**: 🇨🇳 ongoing; **runtime-yc-p26**: ongoing; **noclick-always-on**: ongoing; **nyx-offensive-testing**: ongoing; **agentguard-security-tool**: ongoing; **mcp-security-nsa-supply-chain**: ongoing; **yc-qm-multiplayer-harness**: ongoing; **jadepuffer-agentic-security**: ongoing; **grok-build-xai-rust-harness**: ongoing; **self-harness-auto-optimization**: ongoing; **openharness-hkuds**: ongoing
- **antigravity-gemini-cli-successor**: (see finding #12)
- **claw-code-claude-rewrite**: 🇨🇳 ongoing; **metaharness-scaffold-generator**: ongoing; **deerflow-superagent-harness**: 🇨🇳 ongoing; **omnigent-meta-harness**: ongoing; **zot-go-coding-harness**: ongoing; **omp-omo-pi-derivatives**: ongoing; **yorishiro-presence-harness**: ongoing; **agentskills-open-standard**: ongoing; **letta-agent-file-format**: ongoing; **macos-harness-proving-ground**: ongoing; **ahe-automated-harness-evolution**: ongoing; **harness-internal-external-disambiguation**: 🇯🇵 ongoing
- **warp-oz-multi-harness**: ongoing; **mozilla-otari-llm-gateway**: ongoing; **statewright-guardrails**: ongoing; **headroom-token-compression**: ongoing
- **nvidia-skillspector-security**: ongoing; **cli-anything-hkuds**: ongoing; **forge-acp-universal-cli**: ongoing
- **github-copilot-skills-mcp-ga**: ongoing
- **block-buzz-workspace**: ongoing; **zcode-zhihu-agent-ide**: 🇨🇳 ongoing; **devin-desktop-windsurf-rebrand**: ongoing; **devin-fusion-multimodel**: ongoing; **ambiance-unix-harness**: ongoing; **kore-artemis-abl**: ongoing; **open-agent-passport-oap**: ongoing; **code-as-agent-harness-paper**: ongoing; **tilde-harness-sdk**: ongoing; **kiro-aws-spec-driven**: ongoing; **cursor-spacex-acquisition**: ongoing; **munder-difflin-office-of-clones**: ongoing; **aura-mezmo-sre-harness**: ongoing; **jetstream-clearance-zero-trust**: ongoing; **tenable-cyberagents-exchange-inspector**: ongoing; **vscode-1136-agent-merge**: ongoing; **sonar-vortex-inside-loop**: ongoing; **devspace-minimal-mcp-harness**: ongoing; **skills-over-mcp-wg-sep2640**: ongoing; **accuknox-agentz-enterprise**: ongoing; **gstack-virtual-engineering-team**: ongoing; **graphify-codebase-knowledge-graph**: ongoing; **atlas-source-control-agents**: ongoing; **nodeterm-canvas-terminal-manager**: ongoing; **paseo-multi-provider-orchestration**: ongoing; **openchamber-ade-opencode**: ongoing; **magnitude-local-inference-server**: ongoing; **opencode-v2-rewrite**: ongoing; **context-mode-tool-output-compression**: ongoing; **openclaude-community-agent**: ongoing; **ruflo-meta-harness-swarm**: ongoing; **vscode-1137-agent-host-protocol**: ongoing; **air-security-agent-firewall**: ongoing; **watcher-apolloresearch-monitoring**: ongoing; **harness-enterprise-governance-gap**: ongoing
- **harnessx-composable-foundry**: ongoing; **tencentdb-agent-memory**: 🇨🇳 ongoing; **penguinharness-self-improving**: ongoing; **cloudflare-os-kitesurf**: managed cloud waitlist Oct 1 (finding #15); **ante-antigma-single-binary**: ongoing
- **deepseek-harness-team**: nanoMuse desktop uses DSH as plugin runtime (new third-party adoption)

---

## Cross-Source Patterns

**1. Haiku 5.5 reshapes multi-tier sub-agent economics (🌐🇯🇵🇨🇳)**
- 702 HN pts (highest story of the period); massive JP/CN coverage Oct 7–8
- Pattern: "small model becomes viable sub-agent at 1/10th the cost" shifts how harnesses tier their model calls
- Harnesses that previously used Sonnet as sub-agent now move Explore/compaction/summarization → Haiku 5.5; Sonnet/Opus stays as planner
- CC v2.1.293 immediately deploys Haiku 5.5 as default (same-day); first harness with effort-parameterized sub-agents
- Platforms: HN, Anthropic, Releasebot, developersdigest, beam.ai, apifox.com (CN), vocus.cc (TW), note.com (JP)

**2. New harness wave prioritizes scale/efficiency over features (🌐)**
- OpenHuman: 500 agents/$10 VPS, 2.6x token reduction → efficiency framing beats "more tools"
- cmux: notification rings for attention management → ergonomics for parallel agent sessions
- Docker Agent: YAML-declarative → "harness without framework overhead"
- trycua/cua: fleet benchmarking at Computer-Use 2.0 → infrastructure not just wrapper
- All 4 are NOT in the incumbent list (Cursor/Claude Code/Codex/Copilot/OpenCode/Windsurf/Cline/OpenClaw/Hermes)
- Pattern: incumbents add features; new entrants compete on efficiency, scale, or UX for running many agents at once

**3. Human-in-the-loop tooling becoming a distinct harness category (🌐)**
- Pinrail: structured review inbox — agents pause and submit decisions for human approval
- Jotbus: encrypted cross-agent scratchpad — humans read and coordinate across agent sessions
- Cloudflare OS Gatekeepers: async human approval queue; agent proceeds, action queued for later review
- Television (prior week): visual artifact workspace as human oversight surface
- Pattern: as agents run more autonomously, "human gate" tooling emerges as a distinct class alongside pure orchestration
- Platforms: HN Show HN pattern; GitHub trending; Cloudflare blog

**4. JP/CN framing converges on "sub-agent tier economics" as the harness story of the week (🇯🇵🇨🇳)**
- JP: gihyo.jp formalizes Agentic Coding methodology; myclaw.ai and note.com practical Haiku 5.5 reviews
- CN: vocus.cc frames Oct 2026 as "low-cost agent explosion"; apifox.com "sub-agent engine swap"; easyclaude.com "Claude Code sub-agent cost cut 75%"
- Both regions track the same story but frame it differently: JP = methodology/architecture, CN = economics/ROI
- Platforms: gihyo.jp, note.com, myclaw.ai (JP); apifox.com, 80aj.com, vocus.cc, 53ai.com (CN)

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via digest) | Claude Haiku 5.5 | 702 | 349 | "First small model at human baseline for computer use" | https://www.anthropic.com/claude-haiku-5-5 |
| (via digest) | Docker Agent | 187 | 85 | Multi-agent YAML runtime as Docker CLI plugin | https://github.com/docker/docker-agent |
| shake-n-fries | Show HN: Jotbus | 28 | 17 | "Handles transient work not ready for Git history" | https://news.ycombinator.com/item?id=49978401 |
| (via digest) | nanoMuse – open-source personal AI agent | 61 | — | "Does things instead of answering questions" | https://nano-muse.github.io/ |
| (via digest) | Meta and Microsoft slash internal Claude AI budgets | 365 | — | Meta/MS shifting to in-house coding assistants | https://zeli.app/digest/2026-10-07 |
| (via digest) | Pinrail – desktop inbox for coding agent reviews | 20 | 4 | "Niche but the right bet for safety" (HN community) | https://news.ycombinator.com/item?id=49995778 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic | https://www.anthropic.com/claude-haiku-5-5 | Haiku 5.5: $0.10/M, OSWorld 72.4%, effort settings |
| 🌐 | HN (Haiku 5.5) | https://news.ycombinator.com/item?id=49996437 | 702 pts / 349c; sub-agent economics discussion |
| 🌐 | TechTimes | https://www.techtimes.com/articles/328793/20261009/claude-haiku-55-becomes-viable-sub-agent-human-level-computer-use-ninety-percent-lower-cost.htm | "Viable Sub-Agent: Human-Level Computer Use at 90% Lower Cost" |
| 🌐 | beam.ai | https://beam.ai/agentic-insights/claude-haiku-5-5-subagents | Devin Fusion demo: Haiku 5.5 + Opus 5.5 combo |
| 🌐 | developersdigest | https://www.developersdigest.tech/blog/haiku-5-5-vs-gpt-6-luna-subagent | Haiku 5.5 vs GPT-6 Luna for sub-agent routing |
| 🌐 | releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC v2.1.292–293 changelogs |
| 🌐 | v2.1.292 release | https://github.com/anthropics/claude-code/releases/tag/v2.1.292 | Official --marketplace + effort param release |
| 🌐 | ccleaks | https://ccleaks.com/news/claude-code-2-1-292-oct-2026 | CC v2.1.292: marketplace + effort param explanation |
| 🌐 | gradually.ai CC | https://www.gradually.ai/en/changelogs/claude-code/ | CC Oct 2026 plain English changelogs |
| 🌐 | simonwillison | https://simonwillison.net/2026/Oct/7/claude-haiku-5-5/ | Simon Willison's Haiku 5.5 analysis |
| 🌐 | OpenHuman GitHub | https://github.com/tinyhumansai/openhuman | Rust harness; 41.7k stars; 500 agents/$10 VPS |
| 🌐 | openhumanterminal.tech | https://openhumanterminal.tech/ | OpenHuman landing + Rust quickstart |
| 🌐 | pasqualepillitteri.it | https://pasqualepillitteri.it/en/news/2704/openhuman-open-source-ai-agent-local-memory | OpenHuman local memory analysis |
| 🌐 | starlog.is | https://starlog.is/articles/ai-agents/tinyhumansai-openhuman | OpenHuman backend data routing caveat |
| 🌐 | agency-agents GitHub | https://github.com/msitarzewski/agency-agents | 158.5k stars; 230+ agents; 15+ harnesses |
| 🌐 | cmux GitHub | https://github.com/manaflow-ai/cmux | 28.1k stars; Ghostty macOS terminal for agents |
| 🌐 | trycua/cua GitHub | https://github.com/trycua/cua | 29.2k stars; Computer-Use 2.0 fleet in Rust |
| 🌐 | docker/docker-agent | https://github.com/docker/docker-agent | 4.3k stars; YAML multi-agent; OCI registry |
| 🌐 | nanoMuse GitHub | https://github.com/nano-muse/nanoMuse | GPL-3.0; v1.0.0 Keel Oct 9; cross-device |
| 🌐 | arXiv nanoMuse | https://arxiv.org/abs/2610.08699 | nanoMuse paper: Zhejiang Univ; HF Daily Papers #3 |
| 🌐 | nano-muse.github.io | https://nano-muse.github.io/ | nanoMuse landing page |
| 🌐 | Jotbus | https://jotbus.com/ | E2EE cross-agent scratchpad |
| 🌐 | Jotbus GitHub | https://github.com/Launchable-AI-Inc/jotbus | Open-source Jotbus client |
| 🌐 | HN Jotbus | https://news.ycombinator.com/item?id=49978401 | Show HN: 28 pts / 17c |
| 🌐 | Pinrail GitHub | https://github.com/forgeplane/pinrail | 34 stars; human-in-the-loop inbox; Apache 2.0 |
| 🌐 | cloudflare-os GitHub | https://github.com/cloudflare/cloudflare-os | 11.3k stars; Gadgets + Gatekeepers; managed waitlist |
| 🌐 | cloudflare blog | https://blog.cloudflare.com/cloudflare-os/ | Cloudflare OS: open platform for agents, apps, work |
| 🌐 | cloudflare managed | https://noise.getoto.net/2026/10/01/cloudflare-os-your-companys-agent-workspace-managed-for-you/ | Cloudflare OS managed cloud Oct 1 |
| 🌐 | microsoft/intelligent-terminal | https://github.com/microsoft/intelligent-terminal | 2,042 stars; Windows Terminal + agent integration |
| 🌐 | alphasignal Cursor iOS | https://alphasignal.ai/news/cursor-ships-remote-control-so-developers-run-local-agents-from-iphone | Cursor Remote Control for iOS (Oct 6) |
| 🌐 | releasebot Cursor | https://releasebot.io/updates/cursor | Cursor Oct 2026 changelog |
| 🌐 | releasebot OC | https://releasebot.io/updates/openclaw | OpenClaw v2026.10.1-beta.2 (Oct 7) |
| 🌐 | hermes changelog | https://hermes-ai.net/changelog/ | Hermes v0.21.6 (Oct 8) |
| 🌐 | antigravity changelog | https://antigravity.google/docs/changelog/ | Antigravity v1.3.1–1.3.2 (Oct 7–8) |
| 🌐 | coddykit trending 1 | https://www.coddykit.com/pages/blog-detail?id=5129963&slug=github-trending-october-2026-from-102k-star-agent-skills-to-ghostty-based-termin | addyosmani 102k; cmux 27k; trycua 28k |
| 🌐 | coddykit trending 2 | https://www.coddykit.com/pages/blog-detail?id=5129956&slug=github-trending-october-2026-5-open-source-repos-that-are-redefining-ai-agent-ar | superpowers 294k; mattpocock 275k; ECC 272k |
| 🌐 | coddykit trending 3 | https://www.coddykit.com/pages/blog-detail?id=5129960&slug=github-trending-october-2026-from-157k-star-agent-agencies-to-sandboxed-ai-opera | agency-agents 157k; cloudflare-os 11k |
| 🌐 | yaojiejia digest Oct 8 | https://github.com/yaojiejia/agents-radar/issues/266 | Oct 8 HN digest: Haiku 5.5 702pts; Docker 187pts |
| 🌐 | kouweizhu digest Oct 7 | https://github.com/kouweizhu/agents-radar/issues/374 | Oct 7 HN digest: Meta/MS 365pts; Jotbus 28pts |
| 🌐 | VibeCodingProgram Oct 9 | https://github.com/Wndall/VibeCodingProgram/issues/145 | Oct 9 digest: OpenHuman 41.7k stars; nanoMuse Keel |
| 🌐 | zeli.app Oct 7 | https://zeli.app/digest/2026-10-07 | HN stories Oct 7 full list |
| 🌐 | bradagi/awesome-cli | https://github.com/bradagi/awesome-cli-coding-agents | Curated terminal AI coding agent directory |
| 🌐 | agentconn.com | https://agentconn.com/blog/agent-skills-marketplace-land-grab-2026/ | GitHub trending as skills marketplace land grab |
| 🌐 | zeke/skills-over-mcp | https://github.com/zeke/skills-over-mcp | SEP-2640 harness support research |
| 🌐 | agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 7 AI Agent Skills Marketplaces 2026 |
| 🌐 | clawstat.us | https://clawstat.us/ | OpenClaw stability advisory |
| 🌐 | gradually.ai Hermes | https://www.gradually.ai/en/changelogs/hermes-agent/ | Hermes Oct 2026 changelog |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/10/agentic-coding-and-harness-engineering | "Agentic Coding and Harness Engineering" Yohei Watanabe 🇯🇵 |
| 🇯🇵 | hexabase.com | https://www.hexabase.com/column/harness-engineering-claude-code-cursor-guide | Harness engineering intro guide for CC/Cursor 🇯🇵 |
| 🇯🇵 | syusodo.co.jp | https://syusodo.co.jp/tech-blog/articles/repo-tinyhumansai-openhuman | OpenHuman architecture + adoption criteria JP 🇯🇵 |
| 🇯🇵 | uravation.com | https://uravation.com/media/cursor-vs-claude-code-complete-comparison-2026/ | Cursor vs CC Oct 2026 comparison 🇯🇵 |
| 🇯🇵 | uravation.com CC features | https://uravation.com/media/claude-code-features-20-2026/ | Claude Code 25 features Oct 2026 🇯🇵 |
| 🇯🇵 | zenn.dev ytksato | https://zenn.dev/ytksato/articles/1e4a5e6e033ddb | Harness engineering for CC: OpenAI method in JP repo 🇯🇵 |
| 🇯🇵 | note.com iam_lima | https://note.com/iam_lima/n/nbabc7c2b3217 | Haiku 5.5 vs Opus 5.5 hands-on 🇯🇵 |
| 🇯🇵 | myclaw.ai | https://myclaw.ai/ja/blog/claude-haiku-5-5 | Haiku 5.5 price + benchmarks + use cases JP 🇯🇵 |
| 🇯🇵 | openhuman JP README | https://github.com/tinyhumansai/openhuman/blob/main/docs/README.ja-JP.md | Official JP README for OpenHuman 🇯🇵 |
| 🇯🇵 | oratta/claude-harness | https://github.com/oratta/claude-harness/issues/717 | Epic tracking CC 2026 features for harness 🇯🇵 |
| 🇨🇳 | apifox.com | https://apifox.com/apiskills/claude-haiku-5-5-subagent-pricing/ | Haiku 5.5: "sub-agent engine swap"; 90% price cut 🇨🇳 |
| 🇨🇳 | 80aj.com Haiku 5.5 | https://www.80aj.com/2026/10/08/claude-haiku-55-subagents/ | Haiku 5.5 for sub-agents + browser use 🇨🇳 |
| 🇨🇳 | easyclaude.com | https://easyclaude.com/post/claude-haiku-5-5-release-ai-coding-subagent-cost-cut | "CC sub-agent cost cut 75%" 🇨🇳 |
| 🇨🇳 | vocus.cc | https://vocus.cc/article/6ac7870cfd89780001022325 | "2026年10月「低價代理」爆發" low-cost agent explosion 🇨🇳 |
| 🇨🇳 | 53ai.com Haiku 5.5 | https://www.53ai.com/news/LargeLanguageModel/2026100874650.html | "Price cut 90%" CN analysis 🇨🇳 |
| 🇨🇳 | explore.n1n.ai | https://explore.n1n.ai/zh/blog/claude-haiku-55-denglu-aws-chaogaosu-yu-jizhi-xingjiabi-llm-quanmian-pingce-yu-shizhan-zhinan-2026-10-08 | Haiku 5.5 on AWS CN guide 🇨🇳 |
| 🇨🇳 | penchan.co | https://penchan.co/ai/claude/haiku-5-5/ | Haiku 5.5 pricing + adjustable effort 🇨🇳 (TW) |
| 🇨🇳 | tmtpost.com | https://www.tmtpost.com/7987326.html | OpenHuman "topped GitHub" 🇨🇳 |
| 🇨🇳 | cnblogs.com OpenHuman | https://www.cnblogs.com/itech/p/20046824 | OpenHuman detailed CN intro 🇨🇳 |
| 🇨🇳 | openhumanai.cn | https://openhumanai.cn/ | OpenHuman CN tutorial site 🇨🇳 |
| 🇨🇳 | nanomuse.cn | https://nanomuse.cn/ | nanoMuse CN landing page 🇨🇳 |
| 🇨🇳 | zhihu OpenClaw | https://zhuanlan.zhihu.com/p/2007957826014819829 | OpenClaw complete guide CN 🇨🇳 |
| 🇨🇳 | CSDN OpenClaw+CC | https://blog.csdn.net/2301_81073317/article/details/160209722 | OpenClaw + CC plugin integration guide 🇨🇳 |
| 🇨🇳 | CSDN 6 frameworks | https://blog.csdn.net/promsing/article/details/158380316 | Six AI coding tools comparison 🇨🇳 |
| 🇨🇳 | KimYx0207 CC guide | https://github.com/KimYx0207/AI-Coding-Guide-Zh/blob/main/docs/claude-code/06-Subagent子代理完整指南.md | CN CC subagent complete guide 🇨🇳 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per protocol)
├─ 🔵 X: 0 posts (excluded per protocol)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 10 stories │ ~1,793 pts │ ~900 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (SOURCE HEALTH bluesky=OK; not queried this run)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~65 pages │ 🇯🇵 10 │ 🇨🇳 12
└─ 🗣️ Top voices: Yohei Watanabe (gihyo.jp JP), shake-n-fries (Jotbus), @iam_lima (note.com JP), tinyhumansai (OpenHuman), vocus.cc 低價代理
```

---

## Out of Scope but Notable

- **Meta + Microsoft cutting internal Claude AI budgets** (HN 365 pts Oct 7): enterprise orgs restricting Claude use and shifting to in-house coding assistants. This is a demand-side signal for the harness market, not a harness release — but it indicates enterprise adoption patterns are shifting. Belongs to an enterprise-AI-signals topic if one exists.
- **Agent.reviews** (HN 67 pts Oct 7): platform where AI agents read and write reviews of developer tools — AI agents rating their own tools. Novel UX/epistemics pattern; unclear topic fit.
- **AI Circuit Breaker** (HN 8 pts Oct 7, circuit-breaker-sage.vercel.app): reverse proxy that stops agent infinite loops. Safety tooling with a specific harness concern (runaway loops); small but pointed at a real harness failure mode.
- **agentistics/agentistics #925** (Oct 4): "full bundle with engine — native harness, tools, live, TUI" — an emerging harness with its own TUI; https://github.com/agentistics/agentistics — possibly worth tracking.
- **OpenTPU** (HN 337 pts / 393 comments Oct 8, FeSens/openTPU): open-source AI accelerator developed by AI. Out of scope for harnesses but notable: AI-developed hardware for AI inference is a paradigm boundary event.

---

## Data Gaps

- **last30days skill:** unavailable; full manual sweep via WebSearch + WebFetch performed
- **DuckDuckGo HTML endpoint:** CAPTCHA on both JP and CN queries (consistent with prior run); fallback to native WebSearch was complete
- **Bluesky:** SOURCE HEALTH bluesky=OK; not queried this run (low ROI in prior runs; content not reliably accessible without auth)
- **Reddit / X/Twitter:** excluded per protocol
- **YouTube / TikTok / Instagram / Polymarket:** not searched
- **Cursor changelog Oct 7–9:** no new entries found beyond Remote Control iOS (Oct 6); changelog page shows only Cursor 3.0 (April 2026)
- **OpenCode Oct 7–9 releases:** not confirmed
- **Hermes v0.22.0:** still deferred; v0.21.6 is current
- **Zhihu direct fetch:** HTTP 403; data from search snippets only
- **nanoMuse star count:** not confirmed from digest (repo is new; stars not yet tracked in major digests)
- **mattpocock/skills star count (275,451):** sourced from coddykit only; significant jump from prior 135k; not independently verified
- **Coverage estimate:** ~85% — strong on Haiku 5.5 (dominant story), CC v2.1.292–293, new harnesses (OpenHuman, cmux, trycua/cua, Docker Agent, agency-agents), Jotbus, Pinrail, nanoMuse; JP/CN coverage solid via search fallback; gaps in Bluesky, YouTube, Hermes v0.22 details, Cursor changelog specifics

---

## Key Quotes

> "Haiku 5.5 Becomes Viable Sub-Agent: Human-Level Computer Use at Ninety Percent Lower Cost" — TechTimes headline ([link](https://www.techtimes.com/articles/328793/20261009/claude-haiku-55-becomes-viable-sub-agent-human-level-computer-use-ninety-percent-lower-cost.htm)) 🌐

> "The same instruction given directly to an agent disappears when the session ends; but harness elements in the repository remain shared knowledge." (「エージェントへの直接指示はセッション終了とともに消えるが、リポジトリ内のハーネス要素は共有知識として残る」) — Yohei Watanabe, gihyo.jp ([link](https://gihyo.jp/article/2026/10/agentic-coding-and-harness-engineering)) 🇯🇵

> "2026年10月「低價代理」爆發，Claude重排分工" ("Low-cost agent explosion in October 2026; Claude reorganizing agent division of labor") — vocus.cc ([link](https://vocus.cc/article/6ac7870cfd89780001022325)) 🇨🇳

> "Handles transient work like logs, partial implementations, screenshots — not ready for Git history." — shake-n-fries (Jotbus creator), HN ([link](https://news.ycombinator.com/item?id=49978401)) 🌐

> "The fastest, cheapest, most efficient open-source agent harness. Run more than 500 agents on a $10 VPS." — OpenHuman README ([link](https://github.com/tinyhumansai/openhuman)) 🌐

> "You can't trust a memory you can't read." — OpenHuman design philosophy ([link](https://openhumanterminal.tech/)) 🌐

> "Claude Haiku 5.5 subagent engine swap: 価格最高降90%，编码子代理换引擎" ("Sub-agent engine swap: price cut up to 90%") — apifox.com ([link](https://apifox.com/apiskills/claude-haiku-5-5-subagent-pricing/)) 🇨🇳

> "One agent with a name and a look of its own that does things, keeps working while the app is closed, remembers you, and asks before anything you cannot undo." — nanoMuse README ([link](https://github.com/nano-muse/nanoMuse)) 🌐
