# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-28
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Releasebot, Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Not accessed |
| YouTube | — | — | Not accessed |
| Hacker News | 3 threads | partial (429 on direct fetch) | permission layer; Caspian; 2-month autonomous agent |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | ~2 posts | — | 🦋 bluesky=OK; no on-topic Aug 28 posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~70 pages | — | 🌐 WebSearch (8 passes) + WebFetch (20+ pages) |
| Web (Japan) | ~20 pages | — | 🇯🇵 Qiita (8), Zenn (3), kubell, DevelopersIO, ServerWorks, Hexabase, FIXIT, Techscore, ai-heartland, yanai-ke |
| Web (China) | ~14 pages | — | 🇨🇳 Zhihu (4), cnblogs (2), QbitAI, 36Kr (2), Sina, Tencent News, Volcengine, CSDN, GitHub CN |

---

## Synthesized Findings

### 1. [update] Claude Code v2.1.246–251 (Aug 26–28): Restricted Mode, Hook Events, Cross-Cloud Sessions 🌐🇯🇵

**New facts since Aug 25:** Six releases in three days. Major additions: --restricted mode (eval harness / shared-machine safety); PreModelSwitch + PostModelSwitch hook events; live subagent tool-call streaming to Remote Control; per-session prompt-cache stats in /cost; expanded daemon CLI (attach/logs/stop/respawn/rm); /usage-credits for Enterprise; cross-session messaging extended to Bedrock/Vertex/Foundry; symlink traversal security fix.

**Evidence:**
- **v2.1.246 (Aug 26):** startup wildcard Bash warning; auto mode tab in /permissions; turn completion timestamps; ~40–70 MB less memory via on-demand code loading
- **v2.1.247 (Aug 26):** SendFeedback tool; /claude-api cost-optimize; spellcheck in prompt input
- **v2.1.248 (Aug 28):** --restricted (CLAUDE_CODE_RESTRICTED=1) removes command tools + WebFetch; file tools sandboxed to working dir; refusals: bypassPermissions + user/project/local settings; experimental.cacheTtl in agent frontmatter; credential misupload bug fix; long-session prompt cache miss fix
- **v2.1.251 (Aug 28):** PreModelSwitch / PostModelSwitch hook events; live streaming foreground subagent tool calls to Remote Control; spend limit bar in /usage; per-session prompt-cache stats in /cost; CLI: attach / logs / stop / respawn / rm; symlink traversal security fix; plugin path validation hardened

> 🇯🇵 「--restrictedが追加され、共有マシンで自動実行する場面を想定している」("--restricted was added, designed for shared-machine automated execution scenarios") — Qiita/picnic ([link](https://qiita.com/picnic/items/f6c4074a99d25f780122))

> 🇯🇵 「制限モードで自作スキル47本が0本になった」("Restricted mode turned my 47 custom skills into 0") — Qiita/jqit_suwa ([link](https://qiita.com/jqit_suwa/items/4183a8e97738ba45f435)) — signals operator-vs-user customization tension

**Sources:** https://releasebot.io/updates/anthropic/claude-code · https://code.claude.com/docs/en/whats-new · https://github.com/anthropics/claude-code/releases · https://qiita.com/picnic/items/f6c4074a99d25f780122 · https://qiita.com/jqit_suwa/items/4183a8e97738ba45f435 · https://qiita.com/berrylove/items/e5df42c20e0b23b07f71

---

### 2. [new] Orca (stablyai/orca): ADE for Parallel Agent Fleets — 56k Stars, YC-Backed 🌐🇯🇵

**Claim:** Orca (MIT, YC W22, 56.1k stars, first commit March 17 2026) is an Agent Development Environment that runs multiple CLI coding agents simultaneously, each in an isolated git worktree, from a single interface — growing ~10,000 stars/month.

**Evidence:**
- **Core model:** fan one task to N parallel agents; compare diffs; merge winner — human review is the bottleneck, not model performance
- **40+ CLI agents:** Claude Code, Codex, OpenCode, Grok, Cursor CLI, Pi, Gemini, GitHub Copilot, etc.
- **Design Mode:** click live UI elements to inject HTML/CSS/screenshots into agent context
- **Mobile companion:** iOS + Android for remote monitoring
- **SSH worktrees:** headless cloud VPS agent farms; Orca CLI for scripting
- **Business model:** bring your own key (BYOK) — does not resell inference, no vendor lock-in
- **Ship daily** cadence; README says it "constantly falls behind reality"
- **JP:** 10+ dedicated Qiita/blog articles; "AIエージェント並列実行OSS、Orcaがスター数14倍で主流になった理由" — Qiita/kai_kou; 「複数AIを同時に走らせて開発効率を爆上げ」("running multiple AIs simultaneously to dramatically boost efficiency")

**Sources:** https://github.com/stablyai/orca · https://www.onorca.dev/ · https://agentconn.com/blog/orca-ade-agent-fleet-parallel-coding-agents-2026/ · https://qiita.com/kai_kou/items/0c0bb9bd38a3bf1c1084 · https://rickhigh.substack.com/p/orca-and-the-rise-of-the-agent-development · https://fixit.co.jp/tips/orca-agent-ide-guide/ · https://blog.techscore.com/entry/2026/07/15/080000

---

### 3. [new] Ponytail: 115k-Star Skill That Makes Agents "Think Like the Laziest Senior Dev" 🌐

**Claim:** DietrichGebert/ponytail (MIT, 115.3k stars) is an agent skill enforcing a strict decision ladder — skip → reuse existing → stdlib → native platform → deps → write minimal — reducing generated code by 54-94% while keeping all safety guardrails intact.

**Evidence:**
- **Decision ladder:** every LLM turn intercepted; YAGNI enforced; existing code preferred at every level
- **54-94% less code** on benchmark tasks (real Claude Code sessions on FastAPI + React repos)
- **20+ agents:** Claude Code, Codex, GitHub Copilot CLI, Cursor, Windsurf, Devin, others
- **Commands:** /ponytail, /ponytail-review, /ponytail-audit, /ponytail-debt, /ponytail-gain, /ponytail-help
- **Intensity levels:** lite / full / ultra / off
- Available in multiple plugin marketplaces as instruction files

**Why it matters:** highest-starred pure-skill repo for coding agents; signals demand for meta-skills that reshape agent *behavior*, not just add tools.

**Sources:** https://github.com/dietrichgebert/ponytail · https://www.openagentskill.com/skills/dietrichgebert-ponytail

---

### 4. [new] TrueFoundry TrueForge (Aug 19, MIT): 30–75% Cheaper Alternative to Claude Managed Agents 🌐

**Claim:** TrueFoundry (SF, ex-Meta) launched TrueForge (MIT, github.com/truefoundry/trueforge) on Aug 19 — an open-source, vendor-neutral agent harness competing directly on cost against Claude Managed Agents.

**Evidence:**
- **75% cheaper** with GLM-5.2: $2.90 vs $11.80 (Claude Managed Agents with Opus 4.8)
- **30% cheaper** same model (Opus 4.8): $8.50 vs $11.80
- **Architecture:** model calls, MCP tools, SKILL.md skills, sandboxing, human-in-loop approvals, auto context compaction (50k-token default), generative UI streaming, Tavily web search
- **3 interfaces:** chat UI, HTTP API + TypeScript SDK, embeddable UI SDK
- **40+ built-in tools**; BYOM (any OpenAI-compatible endpoint)
- **Scale:** local (SQLite) → hosted (Docker Compose/Helm, Postgres + Redis)
- **Benchmark:** 11/14 tasks on DevRev Enterprise-Bench

**Sources:** https://venturebeat.com/orchestration/truefoundrys-open-source-ai-agent-harness-trueforge-boasts-30-75-cheaper-task-completion-than-claude-managed-agents · https://github.com/truefoundry/trueforge · https://www.truefoundry.com/blog/engineering/trueforge-open-source-agent-harness/

---

### 5. [update] Hermes v0.20.6 (Aug 27): Real-Profile Browser Window + 50+ Vendor-Hosted MCP Servers 🌐

**New facts since Aug 25 (v0.20.5):** 525 merged PRs, 1,313 commits. New: separate desktop Browser window with real Chrome profile; 50+ vendor-hosted remote MCP servers out of the box; lean-tail compression now default; result caching for web operations; smoother update mechanism.

**Sources:** https://github.com/NousResearch/hermes-agent/releases · https://releasebot.io/updates/nousresearch/hermes-agent

---

### 6. [new] VSCode 1.135 (Aug 26): External Agent Sessions + Rubber Duck Second Opinion 🌐

**Claim:** VS Code 1.135 ships two novel agent-continuity features: cross-app session continuation and a built-in "second opinion" model.

**Evidence:**
- **External agent sessions:** view and continue recent Copilot or Claude sessions created in other apps directly in VS Code; 2 recent external conversations in session list
- **Rubber Duck (Experimental):** /rubber-duck command surfaces missed details and edge cases from a complementary model ("second opinion before merging")
- **Agent Host:** dedicated AHP + Copilot SDK process; multi-window session continuity
- **Agents window:** single-pane default; session info above chat with interactive pills (changes, PRs, artifacts)
- **Chat usage transparency:** per-model token breakdown per interaction

**Why it matters:** cross-app session handoff between Claude Code and VS Code removes friction in human-in-the-loop review workflows.

**Source:** https://code.visualstudio.com/updates/v1_135

---

### 7. [update] DeepSeek Harness RC.8 (Aug 19–20): Multimodal + Claude Code/Codex as Sub-Agents 🌐🇨🇳

**New facts since Aug 25:** RC.8 (Aug 19, two days after RC.7) adds native multimodal to /goal and /plan; integrates Claude Code and Codex as installable Profile Bundle sub-agents; architectural pivot toward general-purpose scheduling layer.

**Evidence:**
- **Multimodal:** DeepSeek model adapter enables native image requests; /goal and /plan accept images; @ menu: reference local files + previous sessions
- **Claude Code + Codex sub-agents:** installable as Profile Bundles; Codex gets non-interactive permission mode (automated pipelines)
- **Concurrent web search;** sub-agents trigger parent task wake-ups
- **Windows:** PowerShell session persistence in Minimal preset; simplified install
- **Architecture:** 36Kr labels DSH "becoming the core scheduling layer in the AI era" (「成为AI时代的核心调度层」)

🇨🇳 **CN reaction:** QbitAI, 36Kr, cnblogs, Sina all frame RC.8 as DSH's pivot from "DeepSeek tool" to "universal agent orchestrator."

**Sources:** https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.0-rc.8 · https://eu.36kr.com/en/p/3947852851664512 · https://www.qbitai.com/2026/08/473597.html · https://finance.sina.com.cn/tech/roll/2026-08-20/doc-ininxekc8982508.shtml

---

### 8. [new] AWS Kiro Crew (Aug 4, Apache 2.0): Orchestration Layer Open-Sourced, Core Harness Kept Closed 🌐

**Claim:** AWS open-sourced Kiro Crew (Apache 2.0) on Aug 4 — the orchestration layer coordinating multiple coding agents into long-running engineering workflows; core agent harness intentionally kept proprietary.

**Evidence:**
- **Origin:** internal project "MeshClaw"
- **Components:** DevFleets (worktree management), Task Runner (long-running execution), Issue Radar (repo triage)
- **Capabilities:** persistent memory, self-scheduled jobs (event or time triggers), parallel subagent model for discrete workstreams
- **Security:** OS sandboxing, deny-by-default commands, sensitive-path protection, credential redaction, signed audit logs
- **AgentCore prebuilt skills:** for Kiro, Claude Code, Codex, Cursor — curated AgentCore best-practices knowledge; "Kiro built-in today; CC/Codex/Cursor plugins coming soon"
- **Forbes:** "AWS open sources Kiro Crew but keeps the agent harness closed" — deliberate open-standards-not-open-implementations strategy

**Sources:** https://www.infoworld.com/article/4204961/awss-kiro-crew-aims-to-turn-ai-coding-agents-into-autonomous-engineering-teams.html · https://www.forbes.com/sites/janakirammsv/2026/08/06/aws-open-sources-kiro-crew-but-keeps-the-agent-harness-closed/ · https://dev.to/sarvar_04/introducing-kiro-crew-awss-open-source-ai-agent-orchestrator-1e63 · https://aws.amazon.com/blogs/machine-learning/get-to-your-first-working-agent-in-minutes-announcing-new-features-in-amazon-bedrock-agentcore/

---

### 9. [new] HiddenLayer Agent Harness Security (Aug 3): Runtime Protection via Native Hook Surface 🌐

**Claim:** HiddenLayer launched Agent Harness Security (Aug 3) — inline runtime protection for AI coding agents against prompt injection, secret exposure, and unsafe commands, integrating via each agent's native hook surface.

**Evidence:**
- Integrates directly into coding agent's native hook surface (not a proxy)
- **Detects/stops:** prompt injection; sensitive data before model sees it; poisoned tool responses; unsafe shell commands
- **Visibility:** security team sees all prompts, tool calls, shell commands, file edits, repo interactions
- **Purpose:** safe scaling of AI-assisted dev without slowing developers

**Sources:** https://www.hiddenlayer.com/news/hiddenlayer-unveils-agent-harness-security · https://www.prnewswire.com/news-releases/hiddenlayer-unveils-agent-harness-security-to-protect-ai-powered-software-development-at-runtime-302841271.html

---

### 10. [new] Harness.io Code Repository + AI Code Review (Aug 27): Agent-Ready SCM at PR Scale 🌐

**Claim:** Harness (DevOps platform) launched agent-ready Code Repository and AI Code Review (Aug 27) — SCM purpose-built to handle thousands of simultaneous agent-opened PRs.

**Evidence:**
- **Scale problem:** AI agents open PRs/commits at volume human repos weren't designed for
- **Code Repository:** scale-tested for thousands of simultaneous PRs; search/history/diffs at that volume; free 50 GB tier
- **AI Code Review:** operates at agent scale; team configures which AI checks are mandatory at merge
- **Agent permissions:** agents inherit from triggering human; further constrained by repo/branch/environment
- **Access:** Harness MCP + CLI cover full PR lifecycle from terminal

**Sources:** https://www.harness.io/blog/agent-ready-code-repository-ai-code-review · https://siliconangle.com/2026/08/27/harness-tackles-influx-of-agent-delivered-code-with-code-repository-and-ai-code-review/ · https://techzine.eu/news/devops/143909/harness-builds-a-code-repository-for-ai-agents/

---

### 11. [new] AMAP-ML/LongHorizon-Harness (MIT, 1.4k Stars): Computer-Use Agent with Verified Checkpoints 🌐

**Claim:** AMAP-ML/LongHorizon-Harness (MIT) is a long-horizon computer-use harness that decomposes extended desktop/CLI tasks into Plan→Execute→Verify→Checkpoint cycles with independent auditing.

**Evidence:**
- **3 roles:** Manager (planning), Executor (action), Auditor (independent verification)
- **Fresh context per action;** only verified progress becomes task state; recovery to last checkpoint on failure
- **Multi-environment:** desktop GUI + CLI in single task
- **Compatible:** Claude Code, Codex, OpenCode, DeepSeek Harness
- **Benchmarks:** WeaveBench 51.8%→80.7% (+28.9pp); OSWorld 2.0 2.8→8.3 (3.0×); Terminal-Bench 2.1 69.7%→77.2%
- Docs in English and Simplified Chinese

**Source:** https://github.com/AMAP-ML/LongHorizon-Harness

---

### 12. [update] OpenClaw: v2026.9.1-beta.1 (Aug 28) Opens September Cycle 🌐

**New facts since Aug 25:** First September-cycle beta (v2026.9.1-beta.1) announced Aug 28. Patch fixes Aug 25–27: parent approval identity separation; publish evidence preservation; Claude CLI OAuth expiry; WhatsApp lease/auth; CI matrix runner config; Windows Node pinning.

**Sources:** https://releasebot.io/updates/openclaw · https://github.com/openclaw/openclaw/releases

---

### 13. [update] OpenCode v1.18.24–25 (Aug 28): Azure Auth + Provider Compatibility Fixes 🌐

**New facts since Aug 25:** v1.18.24–25 (Aug 28) — Azure CLI sign-in without Bun; device login link fix for relative verification URLs; removed outdated first-month Go discount messaging; textVerbosity not sent to unsupporting OpenAI-compatible providers.

**Source:** https://github.com/anomalyco/opencode/releases · https://github.com/anomalyco/opencode/releases/tag/v1.18.25

---

### 14. [new] kubell/Chatwork: Specialized Tools as Whitelist Complement to Harness Blocklists 🇯🇵

**Claim:** Chatwork engineering blog (Aug 4, 2026) argues for replacing generic harness tool permissioning (blocklist) with purpose-built specialized CLIs (whitelist) — "unchosen operations become impossible, not merely forbidden."

**Evidence:**
- **Problem:** prompt rules unreliable; Bash patterns bypass-prone; MCP permissions are tool-name-only; PreToolUse hooks can't enumerate all dangerous forms
- **Solution:** specialized tool with hardcoded folder, no path traversal, no deletion — only permitted operations exist
- **Benefits:** unit-testable; token-efficient (returns only needed fields); inference-faster (built-in logic replaces multi-turn reasoning)
- **Caveat:** "safety mechanisms, not security boundaries" — IAM/database controls still required; complements, never replaces infrastructure-level

> 🇯🇵 「選ばれなかった操作は「禁止」ではなく「不可能」になる」("Unchosen operations become impossible, not merely forbidden") — kubell Creator's Note ([link](https://creators-note.chatwork.com/entry/2026/08/04/120000))

**Source:** https://creators-note.chatwork.com/entry/2026/08/04/120000

---

### 15. [new] Caspian: "Talk to Human" Tool for AI Agents (Show HN) 🌐

**Claim:** Caspian abstracts webhook, queue, and identity management behind a single SDK call — a communications infrastructure layer for agents needing human-in-the-loop checkpoints, inspired by OpenClaw deployment experience.

**Evidence:** 15%+ of issues in OpenClaw deployments involved communications; Caspian bundles this; Show HN

**Sources:** https://news.ycombinator.com/item?id=49390329

---

**Still true** (ongoing threads, no new facts this cycle):

- `block-berd-desktop-workspace` — Berd no new releases; Aug 25 launch ongoing
- `loopx-long-horizon-control-plane` — no new facts
- `cloudflare-computer-agent-runtime` — no new facts
- `cursor-google-workspace-plugins` — no new facts
- `huzzah-pseudocode-editor` — no new facts
- `addy-osmani-agent-skills` — no new facts (89.6k stars as of Aug 25)
- `paperclip-multi-agent-company-os` — no new facts
- `extension-economy-explosion` — claudemarketplaces, DSH, Orca, Ponytail all adding to ecosystem size; no new aggregated count
- `onecli-yc-s26-credential-gateway` — no new facts
- `harnessrouter-uhp-open-standard` — no new facts
- `codex-open-platform-harness` — no new facts
- `flue-2-react-hooks-harness` — no new facts
- `hax-c-minimalist-agent` — no new facts
- `copilot-autofix-dual-ai-security` — no new facts
- `bullet-yc-s26-coding-agent` — no new facts
- `book-to-skill-pdf-to-skill` — no new facts
- `cursor-origin-code-hosting` — no new facts
- `deepseek-harness-v01` — DSH RC.8 is major update (Finding #7)
- `hermes-agent-self-improving` — v0.20.6 update (Finding #5)
- `claude-code-doctor-skill-hygiene` — CC v2.1.246–251 update (Finding #1)
- `openclaw-gateway-harness` — v2026.9.1-beta.1 (Finding #12)
- `opencode-anomaly-rebrand` — v1.18.24-25 (Finding #13)
- `kiro-aws-spec-driven` — no new Kiro releases Aug 26–28; Kiro Crew (Finding #8) is related
- `penguinharness-self-improving` — no new facts
- `cloudflare-os-kitesurf` — no new facts
- `ante-antigma-single-binary` — no new facts
- `tencentdb-agent-memory` — no new facts
- `meta-muse-code` — no new facts
- `prime-agent-rlm` — no new facts
- `aq-multiplayer-harness` — no new facts
- `qwen-code-alibaba` — no new facts
- `oh-my-agent` — no new facts
- `autoharness-deepmind` — no new facts
- `hoplite-yc-s26-cloud-deploy` — no new facts
- `vercel-ai-sdk-harnessagent` — no new facts
- `copilot-studio-ga-harness-billing` — no new facts
- `microsoft-agent-governance-toolkit` — no new facts
- `tinyagents-rust-recursive` — no new facts
- `sprocket-hardware-software-agent` — no new facts
- `gambit-reliable-agent-harness` — no new facts
- `nlah-natural-language-harnesses` — no new facts
- `skills-security-prompt-injection-36pct` — CC restricted mode + kubell whitelist approach extend this; no new survey data
- `claude-tag-slack-agent` — no new facts
- `mimo-code-xiaomi` — no new facts
- `ecc-cross-harness-os` — no new facts
- `cursor-router-workspace-plugins` — Cursor no new releases Aug 26–28; Grok 4.6 added (small)
- `agent-plugins-1-standard` — no new facts; Anthropic still absent
- `vscode-1130-agent-host` — superseded by VSCode 1.135 (Finding #6)
- `mcp-security-nsa-supply-chain` — no new facts; arXiv 2607.13718 adds academic framing
- `yc-qm-multiplayer-harness` — no new facts
- `mcp-stateless-spec-2026-07-28` — MCP ecosystem now: Glama 71k+, combined 101k+
- `jadepuffer-agentic-security` — no new facts
- `grok-build-xai-rust-harness` — Cursor (Grok 4.6 added); Grok Build no new facts
- `self-harness-auto-optimization` — no new facts
- `openharness-hkuds` — no new facts
- `antigravity-gemini-cli-successor` — no new facts
- `claw-code-claude-rewrite` — no new facts
- `metaharness-scaffold-generator` — no new facts
- `harness-engineering-paradigm` — Orca/TrueForge/Kiro Crew reinforce paradigm
- `deerflow-superagent-harness` — no new facts
- `omnigent-meta-harness` — no new facts
- `zot-go-coding-harness` — no new facts
- `omp-omo-pi-derivatives` — no new facts
- `yorishiro-presence-harness` — no new facts
- `agentskills-open-standard` — no new facts (ecosystem counts in claudemarketplaces unchanged from Aug 25)
- `letta-agent-file-format` — no new facts
- `layered-oss-stack-over-single-framework` — Orca + Ponytail + TrueForge all reinforce this
- `macos-harness-proving-ground` — no new facts
- `ahe-automated-harness-evolution` — Orca ADE + AMAP LongHorizon + LLM as harness paradigm reinforce
- `harness-internal-external-disambiguation` — Zenn/renk investigation continues
- `environment-architect-new-role` — kubell article and Hexabase stats reinforce
- `warp-oz-multi-harness` — no new facts
- `mozilla-otari-llm-gateway` — no new facts
- `statewright-guardrails` — no new facts
- `headroom-token-compression` — no new facts
- `pi-minimal-agent-harness` — no new facts
- `nvidia-skillspector-security` — no new facts
- `deepseek-harness-team` — absorbed into deepseek-harness-v01
- `cli-anything-hkuds` — no new facts
- `forge-acp-universal-cli` — no new facts
- `github-copilot-skills-mcp-ga` — no new facts
- `block-buzz-workspace` — no new facts
- `zcode-zhihu-agent-ide` — no new facts
- `devin-desktop-windsurf-rebrand` — no new facts
- `devin-fusion-multimodel` — no new facts
- `ambiance-unix-harness` — no new facts
- `kore-artemis-abl` — no new facts
- `open-agent-passport-oap` — no new facts
- `code-as-agent-harness-paper` — arXiv 2607.13718 (permissions paper) complements this
- `tilde-harness-sdk` — no new facts
- `microsoft-maf-codeact` — no new facts
- `cursor-spacex-acquisition` — no new facts
- `cursor-3-11-update` — superseded

---

## Cross-Source Patterns

### Pattern 1: The "Operator Safety vs User Extensibility" Tension Is Now Concrete 🌐🇯🇵

**Platforms:** GitHub, Qiita, Releasebot

CC's --restricted mode (v2.1.248) making 47 user-custom skills disappear (Qiita/jqit_suwa) instantiates a conflict previously theoretical: operators want guardrails; power users want extensibility. The harness security layer (HiddenLayer, Caspian, kubell whitelist approach) all tackle the same problem from different angles. Qiita/berrylove explicitly frames August CC updates as "agent organization governance."

**Key quote:** "Restricted mode turned my 47 custom skills into 0" — Qiita/jqit_suwa

---

### Pattern 2: "Agent Development Environment" (ADE) Emerges as Distinct Product Category 🌐🇯🇵

**Platforms:** GitHub, Substack, Qiita, AgentConn

Orca's 56k-star growth in 5 months — framing itself as an ADE rather than an IDE or harness — signals a new naming convention for orchestration environments. 10+ JP articles specifically explaining the ADE concept. The category: not a single-agent harness but a multi-agent comparison/coordination workspace.

**Key quote:** "What an IDE looks like when it is built for a fleet" — Rickhigh Substack ([link](https://rickhigh.substack.com/p/orca-and-the-rise-of-the-agent-development))

---

### Pattern 3: DSH Pivoting from DeepSeek Tool to Universal Orchestrator 🌐🇨🇳

**Platforms:** GitHub, 36Kr, QbitAI, Sina, cnblogs

DSH RC.8's integration of Claude Code + Codex as sub-agents is not a feature add — it's an architectural repositioning. CN tech media consistently uses "core scheduling layer" (核心调度层) framing. If successful, DSH becomes an orchestrator that ingests other vendors' agents rather than competing head-on.

**Key quote:** 「成为AI时代的核心调度层」("Becoming the core scheduling layer in the AI era") — 36Kr

---

### Pattern 4: Agent SCM and CI Infrastructure Becomes a New Battleground 🌐

**Platforms:** Harness.io, GitHub, SiliconAngle, Techzine

Harness.io's Aug 27 launch targets the gap between AI coding agent productivity and existing git infrastructure capacity. The simultaneous emergence of AWS Kiro Crew (multi-agent orchestration), Orca (ADE with git worktrees), and now an agent-scale SCM from Harness signals: the entire DevOps pipeline is being redesigned around agent-generated code volume.

**Pattern:** Incumbents (Harness.io) and new entrants (Orca, Kiro Crew) converging on "agent-scale git infrastructure" as a first-class problem.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Show HN: I built a permission layer for AI agents, then spent a day breaking it | — | — | Claude Code's 6-gate permission walk: deny→ask→PreToolUse hooks→allow→mode→canUseTool | https://news.ycombinator.com/item?id=49383441 |
| — | Show HN: Caspian – Talk to Human Tool for AI Agents | — | — | "15%+ of issues in OpenClaw deployments involved communications" | https://news.ycombinator.com/item?id=49390329 |
| — | Show HN: An autonomous AI agent running one project for two months in public | — | — | Long-running autonomous agent log | https://news.ycombinator.com/item?id=49383353 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC v2.1.246–251 tracker |
| 🌐 | VSCode | https://code.visualstudio.com/updates/v1_135 | 1.135: external sessions, Rubber Duck |
| 🌐 | stablyai/orca | https://github.com/stablyai/orca | ADE: 56.1k stars, MIT, YC W22 |
| 🌐 | Orca official | https://www.onorca.dev/ | ADE site |
| 🌐 | AgentConn | https://agentconn.com/blog/orca-ade-agent-fleet-parallel-coding-agents-2026/ | Orca analysis |
| 🌐 | Substack | https://rickhigh.substack.com/p/orca-and-the-rise-of-the-agent-development | Orca/ADE category analysis |
| 🌐 | DietrichGebert/ponytail | https://github.com/dietrichgebert/ponytail | 115.3k stars; laziest-dev skill |
| 🌐 | OpenAgentSkill | https://www.openagentskill.com/skills/dietrichgebert-ponytail | Ponytail listing |
| 🌐 | VentureBeat | https://venturebeat.com/orchestration/truefoundrys-open-source-ai-agent-harness-trueforge-boasts-30-75-cheaper-task-completion-than-claude-managed-agents | TrueForge launch |
| 🌐 | truefoundry/trueforge | https://github.com/truefoundry/trueforge | MIT; BYOM; SKILL.md |
| 🌐 | TrueFoundry blog | https://www.truefoundry.com/blog/engineering/trueforge-open-source-agent-harness/ | Architecture details |
| 🌐 | Hermes releases | https://github.com/NousResearch/hermes-agent/releases | v0.20.6 Aug 27 |
| 🌐 | Releasebot Hermes | https://releasebot.io/updates/nousresearch/hermes-agent | Hermes tracker |
| 🌐 | OpenClaw | https://releasebot.io/updates/openclaw | v2026.9.1-beta.1 |
| 🌐 | OpenClaw GH | https://github.com/openclaw/openclaw/releases | Patch releases |
| 🌐 | OpenCode | https://github.com/anomalyco/opencode/releases | v1.18.24-25 |
| 🌐 | OpenCode v1.18.25 | https://github.com/anomalyco/opencode/releases/tag/v1.18.25 | Azure auth fix |
| 🌐 | HiddenLayer | https://www.hiddenlayer.com/news/hiddenlayer-unveils-agent-harness-security | Aug 3 runtime security |
| 🌐 | HiddenLayer PR | https://www.prnewswire.com/news-releases/hiddenlayer-unveils-agent-harness-security-to-protect-ai-powered-software-development-at-runtime-302841271.html | PR Newswire |
| 🌐 | Harness.io blog | https://www.harness.io/blog/agent-ready-code-repository-ai-code-review | Aug 27 launch |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/08/27/harness-tackles-influx-of-agent-delivered-code-with-code-repository-and-ai-code-review/ | Agent code flood |
| 🌐 | Techzine | https://techzine.eu/news/devops/143909/harness-builds-a-code-repository-for-ai-agents/ | Harness analysis |
| 🌐 | InfoWorld | https://www.infoworld.com/article/4204961/awss-kiro-crew-aims-to-turn-ai-coding-agents-into-autonomous-engineering-teams.html | Kiro Crew launch |
| 🌐 | Forbes | https://www.forbes.com/sites/janakirammsv/2026/08/06/aws-open-sources-kiro-crew-but-keeps-the-agent-harness-closed/ | Open-source strategy |
| 🌐 | DEV Community | https://dev.to/sarvar_04/introducing-kiro-crew-awss-open-source-ai-agent-orchestrator-1e63 | Kiro Crew guide |
| 🌐 | AWS blog | https://aws.amazon.com/blogs/machine-learning/get-to-your-first-working-agent-in-minutes-announcing-new-features-in-amazon-bedrock-agentcore/ | AgentCore prebuilt skills |
| 🌐 | AMAP-ML GitHub | https://github.com/AMAP-ML/LongHorizon-Harness | MIT; 1.4k stars; benchmarks |
| 🌐 | Security Blvd | https://securityboulevard.com/2026/08/my-take-black-hat-2026-part-2-security-shifts-to-deciding-in-advance-what-an-ai-agent-may-reach/ | Black Hat 2026 agent security |
| 🌐 | arXiv 2607.13718 | https://arxiv.org/abs/2607.13718 | User permissions for AI agents |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/claude-code-self-hosted-runners-cross-session-agent-messaging | CC cross-session analysis |
| 🌐 | MCP Market | https://mcpmarket.com/ | MCP discovery |
| 🌐 | ChatForest | https://chatforest.com/guides/mcp-ecosystem-2026-state-of-the-standard/ | Glama 71k+ MCP servers |
| 🌐 | WorkOS | https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026 | MCP for teams 2026 |
| 🌐 | WeMakeDevs | https://www.wemakedevs.org/hackathons/trueforge | TrueForge hackathon |
| 🇯🇵 | Qiita/picnic | https://qiita.com/picnic/items/f6c4074a99d25f780122 | CC v2.1.248: --restricted + cacheTtl |
| 🇯🇵 | Qiita/jqit_suwa | https://qiita.com/jqit_suwa/items/4183a8e97738ba45f435 | Restricted mode: 47 skills → 0 |
| 🇯🇵 | Qiita/berrylove | https://qiita.com/berrylove/items/e5df42c20e0b23b07f71 | August CC updates as governance |
| 🇯🇵 | Qiita/kai_kou | https://qiita.com/kai_kou/items/0c0bb9bd38a3bf1c1084 | Orca 14x star growth explained |
| 🇯🇵 | Qiita/Takashi_Masumori | https://qiita.com/Takashi_Masumori/items/e6f1678b41483943fc04 | Copilot Studio GA; harness types |
| 🇯🇵 | kubell/Chatwork | https://creators-note.chatwork.com/entry/2026/08/04/120000 | Specialized tools whitelist approach |
| 🇯🇵 | DevelopersIO | https://dev.classmethod.jp/articles/claude-code-cross-session-messaging/ | CC cross-session messaging |
| 🇯🇵 | ServerWorks | https://blog.serverworks.co.jp/2026/08/22/190000 | CC Aug 7-20 updates |
| 🇯🇵 | Zenn/renk | https://zenn.dev/renk/scraps/a6fb7cebdea333 | Harness investigation (AWS SA) |
| 🇯🇵 | Zenn/watany | https://zenn.dev/watany/articles/d8b692bbca65a3 | Internal vs external harness |
| 🇯🇵 | Hexabase | https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026 | 50→10 person teams; statistics |
| 🇯🇵 | FIXIT | https://fixit.co.jp/tips/orca-agent-ide-guide/ | Orca guide JP |
| 🇯🇵 | Techscore | https://blog.techscore.com/entry/2026/07/15/080000 | Orca practical guide JP |
| 🇯🇵 | ai-heartland | https://ai-heartland.com/agent/orca-stablyai-parallel-agents-ide/ | Orca intro JP |
| 🇯🇵 | Innovatopia | https://innovatopia.jp/ai/ai-news/116283/ | Models → agent infra shift |
| 🇨🇳 | QbitAI | https://www.qbitai.com/2026/08/473597.html | DSH plugin explosion |
| 🇨🇳 | Zhihu/DSH arch | https://zhuanlan.zhihu.com/p/2072466931421074027 | Everything-is-plugin architecture |
| 🇨🇳 | cnblogs/sing1ee | https://www.cnblogs.com/sing1ee/p/22455466 | DSH complete guide |
| 🇨🇳 | 36Kr #1 | https://eu.36kr.com/en/p/3947852851664512 | DSH: core scheduling layer |
| 🇨🇳 | 36Kr #2 | https://eu.36kr.com/en/p/3947115501845891 | DSH RC.8 multimodal |
| 🇨🇳 | Sina | https://finance.sina.com.cn/tech/roll/2026-08-20/doc-ininxekc8982508.shtml | DSH multimodal update |
| 🇨🇳 | Tencent News | https://news.qq.com/rain/a/20260820A03LEI00 | DSH multimodal |
| 🇨🇳 | Volcengine | https://developer.volcengine.com/articles/7673185253493571625 | Monthly red/black list |
| 🇨🇳 | Zhihu/top10 | https://zhuanlan.zhihu.com/p/2072698072879125245 | Top 10 DSH plugins |
| 🇨🇳 | GitHub #1477 | https://github.com/deepseek-ai/deepseek-harness/discussions/1477 | Collaborative plugin guide |
| 🇨🇳 | DSH RC.8 GH | https://github.com/deepseek-ai/deepseek-harness/releases/tag/dsh-v0.1.0-rc.8 | Official release |
| 🇨🇳 | APIS Hub | https://apis.you/news/cursor-agentic-coding-tool-2026/ | Cursor $2B ARR; agentic tools |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 3 threads │ points not retrieved (429) │ 3 Show HN agent topics
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: ~2 posts │ no on-topic Aug 28 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~70 pages │ 🇯🇵 20 │ 🇨🇳 14
└─ 🗣️ Top voices: jqit_suwa (CC restricted mode impact), berrylove (CC as governance), kai_kou (Orca), sing1ee (DSH) │ 🇯🇵 Qiita/picnic, kubell/Chatwork │ 🇨🇳 36Kr, QbitAI
```

---

## Out of Scope but Notable

- **OpenRouter "Experiential"** (github.com/experientiallabs/experiential, 206 HN pts Aug 27): "turns usage into a better model" — open router that feeds usage patterns back into model improvement. Novel human-feedback loop via routing layer; potential paradigm if it reaches production harnesses.

- **arXiv 2607.13718 "How Agents Ask for Permission"**: academic paper mapping the gap between permission UI design and enforcement; notes Claude Code's 6-gate system (deny→ask→PreToolUse→allow→mode→canUseTool) as most elaborate in the industry. Worth tracking as a regulatory citation target.

- **CN Red/Black list (Volcengine/SuperCLUE):** CN market now has monthly benchmark-based agent scoring (SuperCLUE XClaw). If this becomes a reference benchmark, it could shape CN enterprise purchasing decisions the way SWE-bench shapes EN ones.

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram:** not accessed; social signal layer absent
- **/last30days skill:** unavailable; replaced with multi-pass WebSearch + WebFetch
- **DuckDuckGo HTML endpoint:** CAPTCHA blocked (same as Aug 25 run); JP/CN passes used WebSearch in native language — lower raw coverage than direct DDG browse
- **Bluesky:** bluesky=OK; no on-topic Aug 28 posts found
- **HN rate-limiting (429):** permission layer (49383441) and Caspian (49390329) returned 429 on direct fetch; details sourced from search snippets
- **HN points for Aug 26-28 Show HN threads:** unavailable due to 429
- **Coverage estimate: 78%** — English web and GitHub well covered; JP/CN passes captured key content; social layer absent (~22% gap)

---

## Key Quotes

> 「制限モードで自作スキル47本が0本になった」("Restricted mode turned my 47 custom skills into 0") — Qiita/jqit_suwa ([link](https://qiita.com/jqit_suwa/items/4183a8e97738ba45f435)) 🇯🇵

> "What an IDE looks like when it is built for a fleet" — Rickhigh Substack on Orca ADE ([link](https://rickhigh.substack.com/p/orca-and-the-rise-of-the-agent-development)) 🌐

> 「選ばれなかった操作は「禁止」ではなく「不可能」になる」("Unchosen operations become impossible, not merely forbidden") — kubell Creator's Note on specialized tools ([link](https://creators-note.chatwork.com/entry/2026/08/04/120000)) 🇯🇵

> 「成为AI时代的核心调度层」("Becoming the core scheduling layer in the AI era") — 36Kr on DeepSeek Harness RC.8 strategy ([link](https://eu.36kr.com/en/p/3947852851664512)) 🇨🇳

> "AWS open sources Kiro Crew but keeps the agent harness closed" — Forbes ([link](https://www.forbes.com/sites/janakirammsv/2026/08/06/aws-open-sources-kiro-crew-but-keeps-the-agent-harness-closed/)) 🌐

> 「竞争从'AI能做到吗?'转向'AI能一直做到吗?'」("Competition shifts from 'can AI do this?' to 'will AI consistently do this?'") — Volcengine monthly red/black list ([link](https://developer.volcengine.com/articles/7673185253493571625)) 🇨🇳

> "Your agent needs a computer, not a container" — Cloudflare @computer (from Aug 25 briefing, still resonant) ([link](https://blog.cloudflare.com/cloudflare-computer/)) 🌐

> 「AIエージェントのハーネスを専用ツールへの置き換えで補完する」("Complementing AI Agent Harness by Replacing with Specialized Tools") — kubell Creator's Note ([link](https://creators-note.chatwork.com/entry/2026/08/04/120000)) 🇯🇵
