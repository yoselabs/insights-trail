# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-21
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Releasebot, Builder Radar, Product Hunt

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Not accessed |
| YouTube | 1 video | — | 🌐 Copilot Studio Aug 2026 (URL logged) |
| Hacker News | 4 threads | ~301+ pts, ~100+ comments | OneCLI 86 pts; Hax 115 pts; HarnessRouter (429 on fetch); HN front page scan |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; 0 on-topic found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~70 pages | — | 🌐 WebSearch + WebFetch; 15+ query passes |
| Web (Japan) | ~11 pages | — | 🇯🇵 ITmedia, TechnoEdge, Qiita (1), Zenn (2), note, AI Crew School, Innovatopia, Hexabase, AI Heartland, Future Architect |
| Web (China) | ~12 pages | — | 🇨🇳 80aj, LINUX DO, jishuzhan, Zhihu, cnblogs, Tencent Cloud (2), jdon, jxxy/觉醒AI, CSDN, aitoollab, 163.com |

---

## Synthesized Findings

### 1. [new] OneCLI (YC S26): Credential-Isolation Gateway for Team AI Agents 🌐

**Claim:** OneCLI (Apache-2.0, 2.5K+ stars) is an open-source sandboxed agent harness for teams; agents see placeholder tokens, real credentials injected at network gateway per-request; launched on HN Aug 20-21 with 86 pts/27 comments.

**Evidence:**
- **Architecture:** Per-employee sandboxed personal agent + central policy enforcement at network layer (not model); credential isolation prevents leaked/compromised agents from exfiltrating real secrets
- **Integrations:** GitHub, Gmail, Notion, Dropbox, Jira, Slack, 50+ apps via OAuth
- **IdP provisioning:** provision agents from company identity provider on behalf of employee identity
- **Audit:** full audit logs; human-in-the-loop approvals for sensitive actions (email sends, deletions)
- **License:** Apache-2.0; `ee/` dirs for enterprise features (free dev/test; subscription for prod)
- **Default credential layer for:** NanoClaw
- **Security model:** policy enforced at network layer → immune to prompt injection bypasses
- **HN key quote:** "The agent never holds a real secret. It gets a placeholder. The real credential is injected at the gateway, per request, after the call is authorized."

**Sources:** https://news.ycombinator.com/item?id=49363710 · https://github.com/onecli/onecli · https://onecli.sh/ · https://lemstudio.co/yc-companies/onecli-33320

---

### 2. [new] HarnessRouter + Unified Harness Protocol (UHP): One API for All Harnesses 🌐

**Claim:** HarnessRouter open-sourced the Unified Harness Protocol (UHP, Apache-2.0) on Aug 14 — an open HTTP contract standard letting products integrate Codex, Claude Code, and Hermes through one API; single Docker container CE.

**Evidence:**
- **Components:** Gateway + Runner + Console in one Docker image; Community Edition passes full UHP conformance suite
- **UHP spec:** https://unifiedharnessprotocol.org — versioned, HTTP contract; implementable without HarnessRouter Cloud
- **Supported harnesses:** Codex, Claude Code, Hermes (extensible)
- **YC launch:** https://www.ycombinator.com/launches/Sv6-harnessrouter
- **Real-world quotes:**
  - Jack Zeng (Stanford SoM): "Work that could have taken weeks can now be done in a day, sometimes in hours."
  - Edward Tiong (Readily CEO): "We can go from a problem and a plan into an agent that is in prod within 24 hours."
  - Kuanze Ma (co-founder): "Teams that stop rebuilding this layer are shipping product and winning customers."
- **Comparable to:** Forge ACP (existing thread) but HTTP-native and Docker-native vs. CLI-native

**Sources:** https://github.com/HarnessRouter/harnessrouter · https://aijourn.com/harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol/ · https://unifiedharnessprotocol.org · https://harnessrouter.ai · https://www.financialcontent.com/article/marketersmedia-2026-8-14-harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol

---

### 3. [new] OpenAI: Codex CLI, App-Server, SDK Open-Sourced as Agent Harness Platform (Aug 19) 🌐

**Claim:** OpenAI published "Codex as a Platform" (Aug 19) — open-sources Codex CLI, app-server, and SDK as a full agent harness layer; harness design alone raised ARC-AGI-3 from 13.3% to 38.3% on GPT-5.6 Sol.

**Evidence:**
- **Three integration modes:**
  1. `codex exec` — scripts, CI/CD, one-off bounded agent workflows
  2. Codex SDK — programmatic interface for application code
  3. Codex app-server — persistent product integration (keep conversations open, stream events, interrupt, expose tools, handle approval requests)
- **Architecture:** "Your application owns product context, business rules, and tools; Codex app-server provides the agent loop and sandboxed execution."
- **Benchmark:** retained reasoning + context compaction: GPT-5.6 Sol ARC-AGI-3 13.3% → 38.3%; output tokens reduced sixfold
- **Real deployments:** Cisco Cloud Control integration; Thrive Holdings/Crete tax workflow (7,000 returns, ~33% less preparation time); GitHub/JetBrains IDE embedding
- **Open-source:** Codex CLI, app-server, official SDK; model access and managed services remain separate
- **Supporting:** https://openai.com/index/harness-engineering/ | https://openai.com/index/unlocking-the-codex-harness/

**Sources:** https://developers.openai.com/blog/codex-as-a-platform · https://www.explainx.ai/blog/codex-as-a-platform-open-agent-harness-august-2026 · https://eu.36kr.com/en/p/3948952877661575 · https://agenta.ai/docs/changelog/codex-harness

---

### 4. [new] Flue 2.0: React Hooks Model for Agent Harnesses (Fred Schott / Cloudflare) 🌐

**Claim:** Fred Schott (Astro creator, now Cloudflare) shipped Flue 2.0 (July 31; Latent Space coverage Aug 15) — applies React hooks composability model to agent harness design; 16 built-in hooks enable dynamic runtime agents.

**Evidence:**
- **Core concept:** Agent Hooks — like React hooks but for agents; manage state, listen to lifecycle events, attach capabilities dynamically at runtime
- **16 built-in hooks:** `useSkill()`, `useTool()`, `useSubagent()`, `usePersistentState()`, `useAgentStart()` etc.
- **Key capability:** runtime model + sandbox upgrades; state machine workflows with `step.do()` checkpointing (durable tool execution survives crashes)
- **Infrastructure:** built-in stateless MCP server; zero-config tracing on Cloudflare Workers; Vite-based; Hono routing; conversation-scoped SDK with typed metadata
- **200+ fixes** in first stable release; Cloudflare integration: https://blog.cloudflare.com/agents-platform-flue-sdk/
- **Context:** Schott's company acquired by Cloudflare in January 2026

**Sources:** https://flueframework.com/blog/flue-2/ · https://www.latent.space/p/flue-2 · https://blog.cloudflare.com/agents-platform-flue-sdk/ · https://www.thedeepfeed.ai/posts/2026-05-02-flue-agent-harness-framework/

---

### 5. [new] Hax: Minimalist C-Written Terminal Coding Agent (115 HN pts) 🌐

**Claim:** Hax is a minimalist, terminal-native coding agent written in C; 115 HN points, mid-August 2026; mirrors the Ante (Rust, 135 pts) pattern of efficiency-first single-language harnesses.

**Evidence:**
- Written entirely in C; terminal-native
- HN discussion focused on efficiency considerations for the locally-run component
- **Pattern:** second major C/Rust efficiency-first terminal agent after Ante (AntigmaLabs, Rust, Aug 11)

**Source:** https://news.ycombinator.com/item?id=49273175

---

### 6. [update] Claude Code v2.1.234–237 (Aug 17–19): ANTHROPIC_DEFAULT_MODEL, Concise Mode, Usage Auto-Resume 🌐

**New facts since Aug 18:** Three releases in three days adding ANTHROPIC_DEFAULT_MODEL env var, Concise built-in output style, auto-resume on usage limit reset, cross-session notify_when_idle, VSCode screen reader, and prompt caching fix for gateway sessions. Earlier: CPU fix in v2.1.229.

**Evidence — v2.1.234 (Aug 17):**
- Auto-continues session when usage limits reset (no manual restart)
- Stronger credential leak protections

**Evidence — v2.1.236 (Aug 19):**
- `ANTHROPIC_DEFAULT_MODEL` env var: sets model for new sessions; `/model` overrides and persists; ignores "default"/"inherit"/"opusplan"/"haiku"
- `notify_when_idle`: macOS/Linux cross-session idle notification (one session sends notification when next idle)
- VSCode screen reader support: live announcements for responses, permissions, errors, state changes; heading navigation per turn

**Evidence — v2.1.237 (Aug 19):**
- Built-in **"Concise" output style**: "states results first, omits preambles and running commentary, while performing the work itself with the same level of care" — select via /config → Output style
- Prompt caching fix for LLM gateway/custom base URL sessions (broken since earlier release)
- 35 total changes (4 new features, 3 security updates, 11 improvements, 17 fixes)

**Earlier fix (v2.1.229, Aug 12):** p99 CPU share: 24% → 10% by switching Bun GC from fixed timer to idle-triggered scheduling

**🇯🇵 JP context (Qiita/berrylove):** Aug 2026 CC updates analyzed through "AI agent organization governance" lens — cross-session messaging, workspace trust, gateway spending visibility all introduce new checkpoints requiring ongoing governance policy reassessment

**Sources:** https://github.com/anthropics/claude-code/releases · https://code.claude.com/docs/en/changelog · https://dev.classmethod.jp/en/articles/20260820-cc-updates-v2-1-237/ · https://www.claudeupdates.dev/version/2.1.234 · https://releasebot.io/updates/anthropic/claude-code · https://changelogs.info/claude-code/ · https://qiita.com/berrylove/items/e5df42c20e0b23b07f71

---

### 7. [update] Cursor Aug 19: Event Subscriptions, /goal, Custom Modes, Isolated Subagents 🌐

**New facts since Aug 18:** Aug 19 release enables cloud agents to subscribe to event sources (PRs, Slack threads), introduces /goal long-lived objectives, any skill as a pinned Custom Mode, and per-subagent isolated VMs.

**Evidence:**
- **Subscriptions:** agents subscribe to event sources (PRs, Slack threads) and wake on events; auto-drive PRs — fix CI issues, respond to bots, without per-loop human input
- **/goal command:** long-lived objectives without step-by-step intervention (e.g., "achieve CI green" and let agent run until done)
- **Custom Modes:** any skill pinned as persistent mode ("always-on skills"); activate via keyboard shortcut or menu
- **Isolated Subagents:** independent VMs with separate project copies — parallel work without collision
- **Steering without interruption:** follow-ups wait for next tool call instead of cutting agent mid-action

**Sources:** https://cursor.com/changelog/08-19-26 · https://cursor.com/changelog · https://releasebot.io/updates/cursor

---

### 8. [update] Hermes v0.20.4 (Aug 18): NVIDIA SkillEvaluator Tier 1 Scanning on Every Skill Install 🌐

**New facts since Aug 18:** v0.20.4 adds NVIDIA SkillEvaluator Tier 1 advisory scanning (PII, unicode-smuggling, script lint, license, static security) on every hub skill install; ~1.5s per scan; desktop glass/translucency.

**Evidence:**
- **SkillEvaluator Tier 1:** deterministic + keyless; detects: leaked emails/personal paths/connection strings, unicode-smuggling, script lint, license compliance, static security via NVIDIA SkillSpector
- **Advisory only:** findings printed before install confirmation; real-credential findings (private keys, cloud tokens) highlighted red; install continues unless user aborts
- **Performance:** ~1.4-1.5s per scan; 29 passing tests; disable via `skills.tier1_advisory: false`
- **Desktop:** glass/translucency surface; tabbed sidebar for bot management; Bot Mode group-chat fixes
- **Release:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.18 (74 merged PRs)
- **Upstream context:** https://developer.nvidia.com/blog/evaluating-ai-agent-skill-performance-with-nvidia-skillevaluator/

**🇨🇳 CN signal:** jdon.com reports Hermes delegating to DeepSeek Harness as execution sub-agent ("graph structure + model routing runs through for 0.3 yuan / ~$0.04 per task") — cross-harness composition now practical at production cost

**Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.18 · https://hermesatlas.com/guide/ · https://hermes-ai.net/changelog/ · https://developer.nvidia.com/blog/evaluating-ai-agent-skill-performance-with-nvidia-skillevaluator/ · https://www.jdon.com/94021-hermes-deepseek-harness.html

---

### 9. [update] DeepSeek Harness: Plugin Ecosystem Stabilizing at ~2,000 Tested Plugins as of Aug 21 🌐🇯🇵🇨🇳

**New facts since Aug 18:** dsh-plugin.org (hub with daily professional review) lists 2,000+ plugins, 1,882 install-tested, 1,633 fully verified. Paper: 88-page architecture paper by Peking University + DeepSeek AI. CN user migration from Hermes to DSH reported as "one afternoon" switch.

**Evidence:**
- **dsh-plugin.org:** 2,000+ dsh-plugin plugins; 1,882 install-tested; 1,633 verified; professional team reviewing + updating daily
- **Architecture paper:** 88-page paper by Peking University + DeepSeek-AI; validates design on 4,000+ plugins built over four years of production use
- **🇨🇳 Migration signal (jxxy.net/觉醒AI):** 「我用了半年 Hermes，換 DeepSeek Harness 只花了一个下午」 — "After 6 months of Hermes, switching to DeepSeek Harness took only one afternoon"
- **🇨🇳 Competition framing (aitoollab.cn):** 「能否终结 Claude Code 统治？」 — "Can DSH end Claude Code's dominance?"
- **🇯🇵 Innovatopia framing:** 「AIコーディング競争は「モデル」から「エージェント基盤」へ」 — "AI coding competition shifts from 'models' to 'agent infrastructure'"
- **Ecosystem governance:** dsh-plugin.org provides quality-reviewed hub (vs. raw GitHub label self-tagging), partially addressing the governance gap noted Aug 18

**Sources:** https://dsh-plugin.org/ · https://dshpluginstore.com/ · https://dsharness.org/ · https://www.jxxy.net/ai/articles/chriswangwy-hermes-to-deepseek-harness/ · https://www.aitoollab.cn/articles/deepseek-harness-open-source-agent-framework-2026/ · https://innovatopia.jp/ai/ai-news/116283/ · https://justin3go.com/en/posts/2026/08/15-deepseek-harness-review · https://ofox.ai/blog/deepseek-harness-dsh-version-updates-stability-production-2026/

---

### 10. [update] Extension Economy: claudemarketplaces.com 23,600+ Skills; AP1.0 Absent Anthropic 🌐🇯🇵

**New facts since Aug 18:** claudemarketplaces.com grew to 23,600+ skills / 2,700+ marketplaces (up from 4,384 skills / 727 MCP servers at Aug 4). 🇯🇵 ITmedia confirms Claude Code absent from Agent Plugins 1.0 initial client list.

**Evidence:**
- **claudemarketplaces.com:** 23,600+ skills, 2,700+ marketplaces — 5.4× skills growth since Aug 4
- **MCP SDK:** 1.1B+ monthly downloads (16 months to this milestone)
- **Coding Tools MCP 0.3.0 (Aug 13):** full MCP 2026-07-28 support; exposes repo inspection, file search, structured patches, test/command running, interactive stdin, git status/diff to any MCP client
- **🇯🇵 ITmedia/TechnoEdge/AI Crew School confirm:** Claude Code absent from AP1.0 initial supporter list; JP community asking why Anthropic not in coalition
- **AP1.0 compatible clients (per ITmedia Aug 10):** VS Code, Cursor, Kiro, Hermes Agent, GitHub Copilot, OpenClaw, ChatGPT, Codex — 8 clients; Claude still missing
- **NVIDIA SkillEvaluator** Tier 1 now in Hermes v0.20.4 as advisory layer on every hub install

**Sources:** https://claudemarketplaces.com/ · https://www.80aj.com/2026/08/13/coding-tools-mcp-release/ · https://linux.do/t/topic/2748785 · https://www.itmedia.co.jp/aiplus/article/2608/10/2000000487/ · https://www.techno-edge.net/article/2026/08/10/5378.html · https://www.ai-crew-school.jp/blog/agent-plugins/ · https://jishuzhan.net/article/2086991808977846273

---

### 11. [update] Kiro Post-v2.18: Streaming Watchdog, Mouse in Spec Review, V2→Universal Migration 🌐

**New facts since Aug 18:** Post-v2.18.0 Kiro adds streaming watchdog (idle watchdog + auto-retries + 60-min timeout), mouse support in spec review, AI-generated session titles, and CLI `/upgrade-agent` for V2→universal config migration. AWS Lambda console added Kiro + Cursor IDE integration.

**Evidence:**
- **Streaming recovery:** idle watchdog + auto-retries with backoff + 60-minute timeout → dropped connections no longer hang or terminate turns
- **Spec review:** mouse support (scroll + click + 'm' toggle); AI-generated titles in V3 session picker
- **CLI `/upgrade-agent`:** migrates V2 custom agent configurations to the universal format
- **AWS Lambda integration:** console now extends to Kiro and Cursor alongside existing IDEs
- **Sources:** https://kiro.dev/changelog/ · https://releasebot.io/updates/kiro · https://aws.amazon.com/about-aws/whats-new/2026/08/aws-lambda-ide-kiro-cursor/

---

### 12. [update] OpenClaw Post-GA: Crash-Resilient Storage, Session Rewind, GPT-5.6 Ultra 🌐

**New facts since Aug 18:** Post-2026.8.1-GA OpenClaw adds quarantine store (survives primary DB damage), crash-recoverable SQLite, schema-upgrade data-loss rejection, session rewind/branching, and GPT-5.6 Ultra runtime support (Sol/Terra/Luna).

**Evidence:**
- **State safety:** quarantine store; crash-recoverable SQLite snapshots; schema-upgrade data-loss rejection; rollback-writer snapshot recovery
- **Session rewind and branching:** revisit and fork prior session state
- **GPT-5.6 Ultra:** support for Sol, Terra, Luna across OpenClaw and Codex engines
- **Richer MCP apps:** improved MCP application layer
- **Sources:** https://github.com/openclaw/openclaw/releases · https://releasebot.io/updates/openclaw · https://docs.openclaw.ai/releases

---

**Still true** (ongoing threads, no new facts this cycle):

- `copilot-autofix-dual-ai-security` — Copilot Autofix/Snowflake/Wiz Red Agent (Aug 17 incident); covered in prior briefing; no new facts
- `bullet-yc-s26-coding-agent` — Bullet (YC S26); no new facts since Aug 18
- `book-to-skill-pdf-to-skill` — book-to-skill 12k+ stars; no new facts
- `cursor-origin-code-hosting` — Cursor Origin beta (Aug 17); no significant new facts
- `cursor-spacex-acquisition` — SpaceX acquisition closed Aug 14; no new facts
- `cursor-router-workspace-plugins` — Cursor now updated above (Finding #7)
- `agent-plugins-1-standard` — AP1.0 GA (Aug 12); Anthropic still absent; JP community confirms
- `kiro-aws-spec-driven` — now updated above (Finding #11)
- `vscode-1130-agent-host` — VSCode 1.133; no new facts
- `extension-economy-explosion` — now updated above (Finding #10)
- `anthropic-managed-agents-mcp-tunnels` — CC v2.1.234-237 updates now in Finding #6
- `openclaw-gateway-harness` — now updated above (Finding #12)
- `deepseek-harness-v01` — updated above (Finding #9)
- `hermes-agent-self-improving` — updated above (Finding #8)
- `penguinharness-self-improving` — PenguinHarness; no new facts
- `cloudflare-os-kitesurf` — no new facts
- `ante-antigma-single-binary` — Ante; Hax (Finding #5) is a parallel data point
- `tencentdb-agent-memory` — TencentDB Agent Memory v2.0; no new facts
- `meta-muse-code` — Meta Muse Code; no new facts (Muse Glimmer is out-of-scope model)
- `prime-agent-rlm` — Prime Agent; no new facts
- `aq-multiplayer-harness` — AQ; no new facts
- `qwen-code-alibaba` — Qwen Code; no new facts
- `oh-my-agent` — oh-my-agent; no new facts
- `autoharness-deepmind` — AutoHarness; no new facts
- `hoplite-yc-s26-cloud-deploy` — Hoplite; no new facts
- `vercel-ai-sdk-harnessagent` — Vercel AI SDK v7 HarnessAgent; no new facts
- `copilot-studio-ga-harness-billing` — Copilot Studio GA; no new facts
- `microsoft-agent-governance-toolkit` — AGT; no new facts
- `tinyagents-rust-recursive` — TinyAgents; no new facts
- `sprocket-hardware-software-agent` — Sprocket; no new facts (AI CAD Harness "Adam" also in same HN batch)
- `gambit-reliable-agent-harness` — Gambit; no new facts
- `nlah-natural-language-harnesses` — NLAH; no new facts
- `skills-security-prompt-injection-36pct` — skill security; NVIDIA SkillEvaluator Tier 1 in Hermes adds context
- `claude-tag-slack-agent` — Claude Tag; no new facts
- `mimo-code-xiaomi` — MiMo Code; no new facts
- `ecc-cross-harness-os` — ECC 240k stars (up from 238.9k Aug 14; minor growth)
- `cursor-3-11-update` — superseded by Aug 19 Cursor update
- `kimi-code-moonshot` — Kimi Code; no new facts
- `runtime-yc-p26` — Runtime (YC P26); no new facts
- `noclick-always-on` — NoClick; no new facts
- `nyx-offensive-testing` — Nyx; no new facts
- `agentguard-security-tool` — AgentGuard; no new facts
- `mcp-security-nsa-supply-chain` — MCP/agent security; no new facts beyond prior briefing
- `yc-qm-multiplayer-harness` — YC QM; no new facts
- `mcp-stateless-spec-2026-07-28` — MCP spec; Coding Tools MCP 0.3.0 is a consumer-level adoption signal
- `jadepuffer-agentic-security` — JADEPUFFER; no new facts
- `grok-build-xai-rust-harness` — Grok-Build; no new facts
- `self-harness-auto-optimization` — Self-Harness paper; no new facts
- `openharness-hkuds` — OpenHarness; no new facts
- `antigravity-gemini-cli-successor` — Antigravity 2.0; no new facts
- `claw-code-claude-rewrite` — Claw Code; no new facts
- `metaharness-scaffold-generator` — MetaHarness; no new facts
- `harness-engineering-paradigm` — Agent=Model+Harness; Codex harness engineering post + DSH reinforce
- `deerflow-superagent-harness` — DeerFlow 2.0; no new facts
- `omnigent-meta-harness` — Omnigent (8,899 stars per Builder Radar); no new facts
- `zot-go-coding-harness` — Zot; no new facts
- `omp-omo-pi-derivatives` — oh-my-pi + oh-my-openagent; no new facts
- `yorishiro-presence-harness` — Yorishiro; no new facts
- `agentskills-open-standard` — SKILL.md; CN domestic MCP wave adds context
- `letta-agent-file-format` — Letta .af; no new facts
- `layered-oss-stack-over-single-framework` — 17+ OSS layers; no new facts
- `macos-harness-proving-ground` — macOS proving ground; Flue 2.0 is macOS-adjacent via Cloudflare Workers
- `ahe-automated-harness-evolution` — AHE papers; Codex harness engineering post is a practitioner confirmation
- `harness-internal-external-disambiguation` — Internal vs External; no new facts
- `environment-architect-new-role` — 環境設計者; JP community still producing content
- `warp-oz-multi-harness` — Warp Oz; no new facts
- `mozilla-otari-llm-gateway` — Mozilla Otari; no new facts
- `statewright-guardrails` — Statewright; no new facts
- `headroom-token-compression` — Headroom 66,478 stars (Builder Radar)
- `pi-minimal-agent-harness` — Pi; no new facts
- `nvidia-skillspector-security` — SkillSpector now embedded in Hermes v0.20.4 Tier 1 scan
- `deepseek-harness-team` — (absorbed into deepseek-harness-v01 above)
- `cli-anything-hkuds` — CLI-Anything; no new facts
- `forge-acp-universal-cli` — Forge ACP; HarnessRouter/UHP is a parallel/competing approach
- `github-copilot-skills-mcp-ga` — Copilot skills+MCP; no new facts
- `opencode-anomaly-rebrand` — OpenCode Aug 20: config parsing fixes; right-click project menu; Simplified Chinese token labels
- `block-buzz-workspace` — Block Buzz; no new facts
- `zcode-zhihu-agent-ide` — ZCode; no new facts
- `devin-desktop-windsurf-rebrand` — Devin Desktop; no new facts
- `devin-fusion-multimodel` — Devin Fusion; no new facts
- `ambiance-unix-harness` — Ambiance; no new facts
- `kore-artemis-abl` — Kore.ai Artemis; no new facts
- `open-agent-passport-oap` — OAP; no new facts
- `code-as-agent-harness-paper` — arXiv:2605.18747; Codex harness engineering post is an applied practitioner confirmation
- `tilde-harness-sdk` — Tilde; no new facts
- `microsoft-maf-codeact` — MAF Harness; no new facts

---

## Cross-Source Patterns

### Pattern 1: Harness-as-Protocol Is Normalizing — Three Independent Approaches in One Week 🌐

**Platforms:** HN, AI Journal, YC, GitHub

Three separate new projects this week address the same problem (one interface for many harnesses) from different angles:
- **HarnessRouter + UHP** (Aug 14): open HTTP protocol standard + single Docker container CE
- **Cursor Subscriptions + /goal** (Aug 19): event-driven orchestration that treats agents as persistent services
- **OneCLI** (Aug 20): credential isolation as the core harness contract layer

Convergence signal: the ecosystem is standardizing not just on skill packaging (AP1.0) but on harness-as-infrastructure. This mirrors how Kubernetes abstracted compute: multiple compatible implementations of the same protocol.

---

### Pattern 2: Efficiency-First Minimalist Agents Continue Arriving 🌐

**Platforms:** HN

Hax (C, ~115 pts) follows Ante (Rust, 135 pts, Aug 11) as another efficiency-motivated rewrite:

| Agent | Language | HN Pts | Key Claim |
|-------|----------|--------|-----------|
| Ante | Rust | 135 | 15MB binary, offline, 7-9× less resource use |
| Hax | C | ~115 | Minimalist, terminal-native |

Pattern: developer distrust of bloated harnesses driving exploration of minimal implementations. Counter-pressure to the rising complexity of multi-window (VSCode 1.133) and event-subscription (Cursor) architectures.

---

### Pattern 3: Cross-Harness Composition Now Practical at Production Cost 🌐🇨🇳

**Platforms:** jdon.com (CN), GitHub (Hermes + DSH)

- **Hermes delegating to DeepSeek Harness:** graph structure + model routing for ~0.3 yuan (~$0.04) per task execution (jdon.com)
- **HarnessRouter:** standardizes this at the protocol layer
- **Codex app-server:** "Your application owns context; Codex provides the loop" — same separation of concerns
- **🇨🇳 Migration:** CN users reporting Hermes → DSH migration in "one afternoon" — suggests harnesses are now composable enough that switching/delegating is no longer a major engineering effort

---

### Pattern 4: Japan Focuses on Governance Dimension; China on Ecosystem Dynamics 🇯🇵🇨🇳

- **🇯🇵 JP:** Qiita/berrylove analyzes Claude Code August updates as organizational governance; ITmedia covers AP1.0 through Anthropic's absence lens; AI Crew School asks why Claude Code is not in AP coalition
- **🇨🇳 CN:** Tracking DSH plugin ecosystem count daily; framing DSH vs Claude Code as competitive displacement; migration guides from Hermes to DSH; DingTalk/Feishu/Yonyou racing to publish native MCP Servers
- **Divergence:** JP community intellectualizing harness governance; CN community executing harness switching

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Hax – minimalist, terminal-native coding agent written in C | ~115 | — | "Efficiency considerations for locally-run component" | https://news.ycombinator.com/item?id=49273175 |
| guyb3 | Launch HN: OneCLI (YC S26) – OSS sandboxed agent harness for teams | 86 | 27 | "The agent never holds a real secret. It gets a placeholder." | https://news.ycombinator.com/item?id=49363710 |
| — | Show HN: HarnessRouter: Unified interface for agent harnesses | — | — | "Teams that stop rebuilding this layer are shipping product" | https://news.ycombinator.com/item?id=49335595 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | OpenAI Developers Blog | https://developers.openai.com/blog/codex-as-a-platform | Codex as open agent harness platform (Aug 19) |
| 🌐 | OpenAI | https://openai.com/index/harness-engineering/ | Harness engineering for Codex |
| 🌐 | OpenAI | https://openai.com/index/unlocking-the-codex-harness/ | App Server architecture |
| 🌐 | Explainx | https://www.explainx.ai/blog/codex-as-a-platform-open-agent-harness-august-2026 | Codex harness guide |
| 🌐 | 36kr | https://eu.36kr.com/en/p/3948952877661575 | CN/EN Codex open-source coverage |
| 🌐 | Agenta | https://agenta.ai/docs/changelog/codex-harness | Agenta Codex integration |
| 🌐 | Cursor Changelog | https://cursor.com/changelog/08-19-26 | Aug 19: subscriptions, /goal, Custom Modes, isolated subagents |
| 🌐 | Releasebot Cursor | https://releasebot.io/updates/cursor | Cursor August tracker |
| 🌐 | AI Journal | https://aijourn.com/harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol/ | HarnessRouter announcement details |
| 🌐 | Financial Content | https://www.financialcontent.com/article/marketersmedia-2026-8-14-harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol | HarnessRouter PR |
| 🌐 | UHP Spec | https://unifiedharnessprotocol.org | UHP protocol spec |
| 🌐 | HarnessRouter | https://harnessrouter.ai | Product docs |
| 🌐 | YC Launch | https://www.ycombinator.com/launches/Sv6-harnessrouter | HarnessRouter YC launch |
| 🌐 | OneCLI | https://onecli.sh/ | OneCLI product |
| 🌐 | OneCLI GitHub | https://github.com/onecli/onecli | 2.5K+ stars |
| 🌐 | OneCLI YC | https://lemstudio.co/yc-companies/onecli-33320 | YC S26 profile |
| 🌐 | Flue 2 Blog | https://flueframework.com/blog/flue-2/ | Flue 2.0 release |
| 🌐 | Latent Space | https://www.latent.space/p/flue-2 | Latent Space coverage Aug 15 |
| 🌐 | Cloudflare + Flue | https://blog.cloudflare.com/agents-platform-flue-sdk/ | Cloudflare integration |
| 🌐 | DeepFeed Flue | https://www.thedeepfeed.ai/posts/2026-05-02-flue-agent-harness-framework/ | Flue 1.0 background |
| 🌐 | CC GitHub Releases | https://github.com/anthropics/claude-code/releases | v2.1.234-237 |
| 🌐 | CC Changelog | https://code.claude.com/docs/en/changelog | Official CC changelog |
| 🌐 | DevelopersIO CC | https://dev.classmethod.jp/en/articles/20260820-cc-updates-v2-1-237/ | CC v2.1.236-237 EN article |
| 🌐 | Claude Updates | https://www.claudeupdates.dev/version/2.1.234 | v2.1.234 51 changes |
| 🌐 | Havoptic | https://www.havoptic.com/tools/claude-code | v2.1.234 summary |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC August 2026 tracker |
| 🌐 | Changelogs.info | https://changelogs.info/claude-code/ | CC changelog archive |
| 🌐 | Hermes v0.20.4 | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.18 | NVIDIA SkillEvaluator Tier 1 |
| 🌐 | Hermes Atlas | https://hermesatlas.com/guide/ | v0.20.4 guide |
| 🌐 | Hermes Changelog | https://hermes-ai.net/changelog/ | Official changelog |
| 🌐 | NVIDIA SkillEvaluator | https://developer.nvidia.com/blog/evaluating-ai-agent-skill-performance-with-nvidia-skillevaluator/ | SkillEvaluator tech blog |
| 🌐 | Hermes + NemoClaw | https://developer.nvidia.com/blog/deploy-self-evolving-agents-for-faster-more-secure-research-with-a-hermes-agent-and-nvidia-nemoclaw/ | Hermes + NVIDIA collaboration |
| 🌐 | Releasebot Hermes | https://releasebot.io/updates/nousresearch/hermes-agent | Hermes August tracker |
| 🌐 | awesome-hermes-skills | https://github.com/ZeroPointRepo/awesome-hermes-skills | 82+115+161 skills directory |
| 🌐 | OpenClaw Releases | https://github.com/openclaw/openclaw/releases | Post-GA updates |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OC August tracker |
| 🌐 | OC Docs | https://docs.openclaw.ai/releases | Release notes |
| 🌐 | OC gradually | https://www.gradually.ai/en/changelogs/openclaw/ | OpenClaw changelog |
| 🌐 | Kiro Changelog | https://kiro.dev/changelog/ | Post-v2.18 updates |
| 🌐 | Kiro IDE | https://kiro.dev/changelog/ide/ | IDE-specific |
| 🌐 | Kiro CLI | https://kiro.dev/changelog/cli/ | CLI /upgrade-agent |
| 🌐 | Releasebot Kiro | https://releasebot.io/updates/kiro | Kiro August tracker |
| 🌐 | AWS Lambda/Kiro | https://aws.amazon.com/about-aws/whats-new/2026/08/aws-lambda-ide-kiro-cursor/ | Lambda IDE integration |
| 🌐 | OpenCode Releases | https://github.com/anomalyco/opencode/releases | Aug 20 release |
| 🌐 | Releasebot OCode | https://releasebot.io/updates/sst/opencode | OpenCode August tracker |
| 🌐 | claudemarketplaces | https://claudemarketplaces.com/ | 23,600+ skills, 2,700+ marketplaces |
| 🌐 | dsh-plugin.org | https://dsh-plugin.org/ | 2,000+ plugins, 1,882 install-tested |
| 🌐 | dshpluginstore | https://dshpluginstore.com/ | DSH plugin store |
| 🌐 | DSHarness.org | https://dsharness.org/ | Plugin directory |
| 🌐 | Coding Tools MCP | https://www.80aj.com/2026/08/13/coding-tools-mcp-release/ | Coding Tools MCP 0.3.0 |
| 🌐 | morphllm | https://www.morphllm.com/claude-code-skills-mcp-plugins | Skills vs MCP vs Plugins taxonomy |
| 🌐 | MCP Agent Skills docs | https://modelcontextprotocol.io/docs/2026-07-28/develop/build-with-agent-skills | Official MCP + skills |
| 🌐 | azure-skills | https://github.com/microsoft/azure-skills | Microsoft official Azure skills plugin |
| 🌐 | enchanter.gg | https://enchanter.gg/en/blog/agent-plugins-open-standard-skills-mcp | AP1.0 deep dive |
| 🌐 | getclaudeskills | https://www.getclaudeskills.com/blog/agent-plugins-explained | AP1.0 explainer |
| 🌐 | chris-ayers | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Complete AP1.0 guide |
| 🌐 | Builder Radar | https://buttondown.com/Builder-Radar/archive/builder-radar-week-of-august-16-2026/ | Week Aug 16 roundup |
| 🌐 | RyanAlberts best-of | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked |
| 🌐 | ai-boost awesome | https://github.com/ai-boost/awesome-harness-engineering | Awesome harness engineering |
| 🌐 | caramaschiHG | https://github.com/caramaschiHG/awesome-ai-agents-2026 | 300+ agent resources |
| 🌐 | explainx top10 | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Top 10 open/closed 2026 |
| 🌐 | cellcog rankings | https://cellcog.ai/blog/best-ai-agent-harnesses/ | August 2026 rankings |
| 🌐 | flowtivity DSH | https://flowtivity.ai/blog/deepseek-harness-open-source-agent-explained/ | DSH 95k stars analysis |
| 🌐 | aitoolarchive HR | https://aitoolarchive.com/harnessrouter-community-edition-review/ | HarnessRouter CE review |
| 🌐 | justint3go DSH | https://justin3go.com/en/posts/2026/08/15-deepseek-harness-review | DSH critical review |
| 🌐 | ofox DSH | https://ofox.ai/blog/deepseek-harness-dsh-version-updates-stability-production-2026/ | DSH stability assessment |
| 🌐 | moclaw DSH | https://moclaw.ai/blog/what-is-deepseek-harness | DSH explainer |
| 🇯🇵 | ITmedia | https://www.itmedia.co.jp/aiplus/article/2608/10/2000000487/ | AP1.0 without Claude (Aug 10) |
| 🇯🇵 | TechnoEdge | https://www.techno-edge.net/article/2026/08/10/5378.html | AP1.0 coalition without Anthropic |
| 🇯🇵 | AI Crew School | https://www.ai-crew-school.jp/blog/agent-plugins/ | AP1.0 explainer; Claude absent |
| 🇯🇵 | Innovatopia | https://innovatopia.jp/ai/ai-news/116283/ | DSH: model → agent infra shift |
| 🇯🇵 | Qiita (berrylove) | https://qiita.com/berrylove/items/e5df42c20e0b23b07f71 | CC Aug updates as governance |
| 🇯🇵 | Zenn (harness) | https://zenn.dev/harness/articles/claude-code-harness-layer-map | 5-layer CC harness framework |
| 🇯🇵 | Zenn (atsukish) | https://zenn.dev/atsukish/articles/e080ae2847540d | MCP + Agent Skills strategy |
| 🇯🇵 | Zenn (tokium_dev) | https://zenn.dev/tokium_dev/articles/843968b5474998 | Skill-first harness construction |
| 🇯🇵 | genai-ai.co.jp | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | CC 3-subagent harness design |
| 🇯🇵 | Hexabase | https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps | Harness engineering complete guide |
| 🇯🇵 | AI Heartland | https://ai-heartland.com/ | JP portal: CC/MCP/OSS security |
| 🇯🇵 | Future Architect | https://future-architect.github.io/articles/20260622a/ | Agent skill evaluation mechanisms |
| 🇨🇳 | 80aj.com | https://www.80aj.com/2026/08/13/coding-tools-mcp-release/ | Coding Tools MCP 0.3.0 |
| 🇨🇳 | LINUX DO | https://linux.do/t/topic/2748785 | Coding Tools MCP community discussion |
| 🇨🇳 | jishuzhan | https://jishuzhan.net/article/2086991808977846273 | Agent Plugins 1.0 + MCP dev guide |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/1925591741496550319 | 7 open-source MCP projects |
| 🇨🇳 | cnblogs/aifrontiers | https://www.cnblogs.com/aifrontiers/p/19652950 | 2026 best open-source AI coding tools |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2632836 | 2026 coding tools (mirror) |
| 🇨🇳 | Tencent Cloud | https://cloud.tencent.com/developer/article/2589986 | 5 top MCP projects |
| 🇨🇳 | jdon | https://www.jdon.com/94021-hermes-deepseek-harness.html | Hermes delegates to DSH (0.3 yuan) |
| 🇨🇳 | jxxy/觉醒AI | https://www.jxxy.net/ai/articles/chriswangwy-hermes-to-deepseek-harness/ | Hermes → DSH migration: one afternoon |
| 🇨🇳 | CSDN | https://blog.csdn.net/qq_43701370/article/details/163780932 | DSH tutorial |
| 🇨🇳 | aitoollab | https://www.aitoollab.cn/articles/deepseek-harness-open-source-agent-framework-2026/ | DSH vs Claude Code |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/L438C40L05199NPP.html | DeepSeek major release coverage |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: 1 URL logged (Copilot Studio) │ not transcribed
├─ 🟢 HN: 3 threads directly tracked │ ~301+ pts │ ~100+ comments │ + front page scan
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: 0 posts │ 0 on-topic (bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~70 pages │ 🇯🇵 11 │ 🇨🇳 12
└─ 🗣️ Top voices: guyb3/OneCLI, Kuanze Ma/HarnessRouter, Fred Schott/Flue │ 🇨🇳 jdon.com/觉醒AI (DSH migration) │ 🇯🇵 berrylove/Qiita (CC governance)
```

---

## Out of Scope but Notable

- **Meta Muse Glimmer** (Aug 10, Apache 2.0, 30B): open-weight local agentic model; 1,203 HN points/638 comments (highest week); runs on 24/32GB GPU; distilled from Muse Spark; 4-bit quant under 20GB; llama.cpp/MLX/ExecuTorch. Scope: foundation model (belongs to open-models-geopolitics). Why notable for harnesses: first major open-weight model purpose-built for always-on local agent workflows — directly competes with the local execution tier of Claude Code self-hosted runner and OpenClaw local mode. https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model | https://huggingface.co/meta-models/Muse-Glimmer-30B | https://www.infoq.com/news/2026/08/meta-muse-glimmer/

- **Discovered Materials (YC P26)**: AI agents applied to materials science discovery; 160 HN pts/35 comments; claims "first published material discovery" — vertical domain application pattern (same harness layer, specialized domain). https://news.ycombinator.com/front (Builder Radar Aug 16 ref)

- **cc-switch** (farion1231/cc-switch, Rust, 127,487 stars): desktop all-in-one agent switcher — extreme star count for a switching utility; if growth is organic, signals massive pent-up demand for harness-level switching. Otherwise may be coordinated. Builder Radar noted: "growth mechanism unclear." https://github.com/farion1231/cc-switch

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram:** not accessed; social signal layer absent. OneCLI, Codex platform, Flue 2 likely generated X/Reddit discussion not captured
- **last30days skill:** unavailable; social platform data (Reddit, X, YouTube/TikTok/Instagram, Polymarket) not collected. WebSearch + WebFetch substituted for all passes
- **DuckDuckGo HTML endpoint:** returned CAPTCHA for both JP and CN queries; WebSearch used as substitute (reaches JP/CN indexed content via Qiita/Zenn/Zhihu but with lower raw coverage than DuckDuckGo HTML browse)
- **Bluesky:** bluesky=OK; 0 on-topic posts found
- **HarnessRouter HN post** (item 49335595): returned 429 on direct fetch; details sourced from AI Journal + YC launch instead
- **Flue 2.0 GitHub stats:** not available from fetched pages (stars/forks not listed in blog post)
- **Coverage estimate: 74%** — HN tracked well; English web good coverage via multi-pass search; JP/CN passes captured key content via indexed search (DuckDuckGo HTML CAPTCHA limited direct browse); social layer absent; estimated ~26% gap from missing social + Reddit

---

## Key Quotes

> "The agent never holds a real secret. It gets a placeholder. The real credential is injected at the gateway, per request, after the call is authorized." — guyb3 (OneCLI), Hacker News ([link](https://news.ycombinator.com/item?id=49363710)) 🌐

> "Teams that stop rebuilding this layer are shipping product and winning customers." — Kuanze Ma, HarnessRouter co-founder ([link](https://aijourn.com/harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol/)) 🌐

> "Your application owns product context, business rules, and tools; Codex app-server provides the agent loop and sandboxed execution." — OpenAI, Codex as a Platform ([link](https://developers.openai.com/blog/codex-as-a-platform)) 🌐

> 🇯🇵「AIコーディング競争は「モデル」から「エージェント基盤」へ」 ("The AI coding competition shifts from 'models' to 'agent infrastructure'") — Innovatopia on DeepSeek Harness ([link](https://innovatopia.jp/ai/ai-news/116283/)) 🇯🇵

> 🇨🇳「我用了半年 Hermes，換 DeepSeek Harness 只花了一个下午」 ("After 6 months of Hermes, switching to DeepSeek Harness took only one afternoon") — jxxy.net/觉醒AI ([link](https://www.jxxy.net/ai/articles/chriswangwy-hermes-to-deepseek-harness/)) 🇨🇳

> 🇨🇳「Hermes委托DeepSeek Harness干活：图结构加模型路由三毛钱跑通」 ("Hermes delegates to DeepSeek Harness: graph structure + model routing runs through for 0.3 yuan") — jdon.com ([link](https://www.jdon.com/94021-hermes-deepseek-harness.html)) 🇨🇳

> "Retained reasoning and context compaction raised GPT-5.6 Sol's score from 13.3% to 38.3% while reducing output tokens sixfold." — OpenAI, Codex as a Platform ([link](https://developers.openai.com/blog/codex-as-a-platform)) 🌐

> 🇯🇵「Claude Codeは初期リスト不在」 ("Claude Code is absent from the initial list") — AI Crew School on Agent Plugins 1.0 ([link](https://www.ai-crew-school.jp/blog/agent-plugins/)) 🇯🇵

> "Work that could have taken weeks can now be done in a day, sometimes in hours." — Jack Zeng (Stanford SoM), HarnessRouter customer ([link](https://aijourn.com/harnessrouter-open-sources-the-worlds-first-unified-interface-for-agent-harnesses-and-the-unified-harness-protocol/)) 🌐
