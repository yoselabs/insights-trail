# AI Agent Harnesses — Daily Briefing
**Date:** 2026-09-25
**Query type:** GENERAL
**Sources:** Releasebot (CC/OC/Hermes/Cursor), Claude docs, Anthropic blog, GitHub (google/ax, HKUDS/nanobot, obra/superpowers, dream-num/univer, modelcontextprotocol/ext-skills), InfoQ, MarkTechPost, CCLeaks, API Evangelist, Qiita, Zenn, Zhihu, CSDN, HN (via search), Freedom.tech, gihyo.jp

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 1 story | 179 pts, 74 comments | 🌐 Google AX; rate-limited on direct fetch; data via search |
| Web (global) | 55+ pages | — | 🌐 WebSearch + WebFetch, keyless |
| Web (Japan) | 8 pages | — | 🇯🇵 Qiita (htani0817, TakanobuSano, sin-aiagent, kai_kou, Takuya__), Zenn (aws_japan, atsukish), gihyo.jp |
| Web (China) | 8 pages | — | 🇨🇳 Zhihu (3 posts), SMZDM, Pedaily, CSDN, LearnAgent, CNBlogs |
| GitHub Trending | 1 digest | — | 🌐 Sep 25 trending (marc-ko/daily-trending-repo, agents-radar) |

---

## Synthesized Findings

### 1. [new] Claude Opus 5.5: first new model family, 40% cheaper, 4 breaking API changes — default in CC v2.1.280 🌐🇯🇵🇨🇳

**Claim:** Anthropic shipped Claude Opus 5.5 (Sep 22), first in a new 5.5 family (Sonnet/Haiku 5.5 coming weeks later); beats all prior models on Terminal-Bench 4.0 (66.4%) while costing 40% less than Opus 5; four API-breaking changes mean harness code—not just model IDs—must be updated.
**Evidence:**
- **Benchmarks:** Terminal-Bench 4.0: 66.4% (vs GPT-6 Astra in Codex 58.2%); FrontierCode v1.1: 54.4%; GDPval-AA v2.1: 1,846 Elo; OSWorld 2.0: 81.8%
- **Pricing:** Input $4/M (20% off); Output $20/M (20% off); Cache reads $0.20/M (60% off); Cache writes $5/M
- **Speed:** 30%+ faster output; 2.5× in Fast Mode; 40% fewer tokens on computer-use tasks
- **Safety:** 85% less boundary-circumvention tendency vs Opus 5
- **Context:** 1M tokens (unchanged); adaptive thinking always on; default effort = medium (medium now matches prior high)
- **4 breaking API changes:**
  1. `thinking: {type: "disabled"}` → 400 error; must use effort parameter
  2. Default effort lowered to medium
  3. `tool_choice: {type: "any"}` → 400; use auto with strict schemas
  4. `computer_20251124` toolset incompatible; only `computer_toolset_20260801` supported
- **Migration note:** "Model ID replacement alone is insufficient in most cases"
- **Claude Code:** v2.1.280 makes Opus 5.5 the default Opus model; usage limit raised 20% on Pro/Max/Team
- 🇯🇵 Qiita @htani0817: "Fable 5.1超えの性能を40%安く・API破壊的変更まとめ" — 4 breaking changes need code-level fix, not just ID swap; "Fast Modeでは2.5倍の速さ"
- 🇯🇵 Qiita @TakanobuSano: "「Opus 5にしておけば勝ち」ではなかった" — harness architecture matters as much as model choice; shifting debate from "which model?" to "how to architect the environment"
- 🇨🇳 Zhihu (high-engagement): "Artificial Analysis Intelligence榜单以58分位列第一，领先Fable 5.1和GPT-6 Astra" — CN community focused on the 60% cache read price cut as biggest impact for long-horizon agent tasks
- 🇨🇳 Pedaily framing: "大模型定价战进入白热化" — sees Opus 5.5 as escalation of flagship pricing war
- Sources: https://www.anthropic.com/claude-opus-5-5, https://platform.claude.com/docs/en/models/opus-5-5/whats-new-opus-5-5, https://qiita.com/htani0817/items/770773094cdfd0d67b19, https://qiita.com/TakanobuSano/items/9281ec7f306073144312, https://qiita.com/kai_kou/items/5c80fa141ff45a82f71d, https://gihyo.jp/article/2026/09/claude-opus-5.5, https://news.pedaily.cn/202609/569597.shtml

---

### 2. [new] Google AX: open-source Kubernetes-native distributed agent runtime, HN#1 🌐

**Claim:** Google open-sourced AX (Agent eXecutor, Sep 18, 2026, Go+Python, Apache 2.0, 11.2k stars): a Kubernetes-native distributed runtime for running billions of agent workloads — explicitly positioned beneath all harnesses, not as a harness itself; HN#1 Sep 21 (179 pts, 74 comments).
**Evidence:**
- Explicit non-positioning: "not a managed service, not a framework, not a specific harness" — sits below the harness layer as a distributed serving runtime
- 4 declarative YAML primitives (`ax.io/v1alpha1`): Task (isolated sandbox), Workspace (Git+MCP+skills pre-config), Gateway, Model (LLM selection + Kubernetes secrets)
- Sub-second task suspension/resumption for checkpointing (stateful actors, not microservices/batch)
- kubectl-style CLI: apply, get, describe, watch, delete, `ax ssh` for interactive sandbox access
- Built on Google's Agent Substrate for sandboxed execution; Redis + gRPC control plane
- Stars: 1,955 on Sep 21 → 11.2k by Sep 25; 543 forks; 37 open issues; 635 commits
- HN quote: "The agent execution problem is infrastructure, not framework. Google just made that explicit."
- Significance: first Kubernetes-grade orchestrator from a hyperscaler explicitly designed to run beneath—not replace—existing coding agent harnesses
- Sources: https://github.com/google/ax, https://www.infoq.com/news/2026/09/google-ax-orchestrator/, https://saascity.io/blog/google-agent-executor-ax-open-agent-runtime-2026, https://agentconn.com/blog/cloud-agent-frameworks-google-ax-orchestration-moat/

---

### 3. [new] dream-num/univer "Office Harness for AI Agents": spreadsheets+docs+slides in one multi-agent runtime 🌐🇨🇳

**Claim:** dream-num/univer (Beijing-based, trending Sep 25) positions itself as "The Office Harness for AI Agents" — a single runtime where AI agents operate spreadsheets, docs, slides, canvas, relational tables, and PDFs; dedicated DeepSeek Harness plugin (dsh-univer-office) with 84k+ downloads.
**Evidence:**
- Runtime: spreadsheets, docs, slides, canvas, relational tables, PDF in one environment
- Connected data, validation, versioned changes, isolated worktrees for multi-agent collaboration
- dsh-univer-office plugin (v0.2.14, Sep 10): CN-origin; "把DeepSeek Harness带入真实的办公室环境" ("Brings DeepSeek Harness into a real office environment")
- 84k+ downloads as of Sep 10; trending GitHub Sep 25
- CN angle: primarily positioned for DeepSeek Harness ecosystem; signals that CN-origin harnesses are developing domain-specific "office" plugins not yet present in EN ecosystem
- Sources: https://github.com/dream-num/univer, https://github.com/dream-num/dsh-univer-office, https://dshfind.com/en/plugins/dream-num/univer-workspace

---

### 4. [new] obra/superpowers: agentic skills framework enforcing TDD/YAGNI/DRY, trending Sep 25 🌐

**Claim:** obra/superpowers (Jesse Vincent + Prime Radiant, Shell): agentic skills framework and software development methodology published on Claude plugin marketplace; +611 stars/day Sep 25; active issues Sep 21-19; enforces spec→review→TDD→YAGNI→DRY pattern via composable skills.
**Evidence:**
- Skills: brainstorming, dispatching-parallel-agents, executing-plans, finishing-branch, requesting-code-review, subagent-driven-development, systematic-debugging, TDD
- Agent doesn't jump to code: first produces spec in chunks short enough to review, then implementation plan, then TDD/YAGNI/DRY execution
- Available on Claude plugin marketplace; multi-harness compatible
- Active development: issues opened Sep 21 (subagent-driven-development), Sep 19 (executing-plans)
- Distinct from gstack/Reinventing.AI employee packages: superpowers is a methodology-first skill set, not role-based routines
- Sources: https://github.com/obra/superpowers, https://www.developersdigest.tech/blog/skills-are-the-new-agent-operating-system

---

### 5. [update] Claude Code v2.1.280-282: Opus 5.5 default, maxProseWidth, MCP description cap 🌐🇯🇵🇨🇳

**Claim:** NEW FACTS — v2.1.280 (Sep 22): Opus 5.5 as default Opus model; v2.1.282 (Sep 25): `maxProseWidth` setting; startup telemetry notices; Chrome managed MCP setting; CJK diff fix.
**Evidence:**
- v2.1.280: mouse wheel in /skills list; click /plugin state options; `CLAUDE_CODE_MAX_MCP_DESCRIPTION_LENGTH` (overrides 2,048-char cap); fix for symlink write misjudgment in auto mode; fix endless retry on safety check declines; fix Ctrl+C/D dialog behavior; Persian/Arabic zero-width non-joiner fix; VSCode auto-archive (default 14 days)
- v2.1.282: `maxProseWidth` setting controls prose width while preserving code block formatting; startup notices for telemetry variables; `allowClaudeInChromeWithManagedMcp`; fix "Invalid `data` in `redacted_thinking` block" API errors; fix resumed sessions re-sending altered messages; fix `:*` mid-pattern permission rules being skipped; fix disk quota errors hiding as "Exit code 1"; CJK wrapping stale diff chars; Windows $TMPDIR + session backup races
- 🇨🇳 CN community: "Claude Code最新版为2.1.280，stable标签2.1.267" (stable channel lagging for production deployments)
- 🇯🇵 Qiita: "v2.1.280以降が必要、それ未満では'model not supported'エラー" for Opus 5.5
- Sources: https://releasebot.io/updates/anthropic/claude-code, https://code.claude.com/docs/en/whats-new, https://ccleaks.com/news/claude-code-2-1-280-sep-2026, https://www.claudeupdates.dev/version/2.1.280, https://aiagent-navi.com/ai-agent/opus-5-5-not-working/

---

### 6. [update] Hermes v0.21.5 (Sep 24): Desktop SDK, multilingual, Hindsight decoupled, GitSpawn security sync 🌐

**Claim:** NEW FACTS — v0.21.5 (Sep 24, 460 PRs, 1,610 commits): Hindsight memory provider removed from bundled install (now a separate plugin from Vectorize catalog); Desktop SDK composer draft APIs; multilingual catalogs (FR/DE/ES); RTL/LTR text direction; GPT-6 Sol/Terra/Luna + Claude Opus 5.5 model availability; GitSpawn security sync (RCE, redaction, snapshot, SSRF patches).
**Evidence:**
- Hindsight decoupling: `hermes-agent[hindsight]` pip extra removed; install via plugin catalog maintained by Vectorize; signals modularity over bundling
- Simple/Advanced interface mode options (user-selectable complexity level)
- Blender Lab + NVIDIA plugins officially integrated into catalog
- Dozens of community plugins added in this window
- Security: Sep 24 upstream sync covers GitSpawn RCE, redaction, snapshot, SSRF (subset of 8 original flaws)
- Full curated release notes deferred to v0.22.0
- Sources: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.24, https://freedom.tech/posts/2026-09-24-hermes-agent-0-21-5/, https://github.com/mtp-44/hermes-agent/pull/8

---

### 7. [update] OpenClaw 2026.9.6 (Sep 24): macOS launch crash rebuild + Code Mode QA fix 🌐

**Claim:** NEW FACTS — v2026.9.6 (Sep 24): original build shipped with macOS launch crash (Swift concurrency abort); rebuilt notarized macOS app released Sep 24 09:52 UTC; Code Mode terminal-evidence validation fixed for OpenAI guest runs.
**Evidence:**
- Crash issue #156861: Swift concurrency abort in CookieSyncManager.scheduleReconcile on every Mac launch
- Fix: rebuilt notarized DMG; in-app update available from 2026.9.5; npm package unchanged
- Code Mode fix: resolved branch that let one verification path skip evidence checks for OpenAI guest runs
- Cron improvement: DM-created workflows now run without delivery channel requirement
- Side chat: follow-up draft stays editable while answer is pending
- 178 commits, 2,614 PRs, 351 contributors in this release window
- Sources: https://releasebot.io/updates/openclaw, https://github.com/openclaw/openclaw/issues/156861, https://releases.sh/openclaw

---

### 8. [update] SEP-2640 adoption: only 2 of 572 servers implement skills extension — SDK PRs awaiting review 🌐🇯🇵

**Claim:** NEW FACTS — As of Sep 22, only 2 MCP servers (of 572 probed) have implemented the skills extension: Hugging Face and RenooLab (French marketplace); official SDK PRs for Go/TS/Python/C# are open but awaiting reviewers; 270 providers maintain skills + MCP servers separately.
**Evidence:**
- Of 27,956 API providers: 679 publish Agent Skills independently; 270 also run MCP servers; none merged yet
- Spec is final (Sep 13); implementation barely started
- WG open contribution needs: SDK reviewers, conformance test scenarios, client integration
- 🇯🇵 Zenn AWS Japan: "スキルはコンテキストであり、MCPはコンテキストプロトコルである" — design rationale; security emphasis on treating MCP-sourced skills as untrusted input
- Ext-skills repo: 682 stars, 59 forks, 12 issues, 4 PRs (modelcontextprotocol/ext-skills)
- Sources: https://apievangelist.com/2026/09/22/skills-over-mcp-is-final-and-now-it-needs-servers/, https://github.com/modelcontextprotocol/ext-skills, https://zenn.dev/aws_japan/articles/skills-over-mcp

---

### 9. [update] Cursor Rollouts Bot + Security Review Bot (Sep 23): two new PR-attached bots 🌐

**Claim:** NEW FACTS — Sep 23: Cursor launched Rollouts Bot (monitors deployment health per PR per environment) and Security Review Bot (reports exploitable bugs on every PR), both built on Cursor Bot Development Kit; Teams/Enterprise.
**Evidence:**
- Rollouts Bot: attaches monitor to every PR; watches deployment per environment; returns "verified healthy", "regression detected", or "inconclusive"; modeled on Firetiger Change Monitors
- Security Review Bot: per-PR exploitable bug detection
- Both use Cursor's Bot Development Kit (internal harness extension API)
- Teams/Enterprise plans only at launch
- Sources: https://releasebot.io/updates/cursor, https://cursor.com/changelog

---

### 10. [update] HKUDS/nanobot v0.3.5: ultra-lightweight personal agent trending Sep 25 🌐🇨🇳

**Claim:** NEW FACT — HKUDS/nanobot (v0.3.5 Sep 15, 48.6k stars, 8.6k forks, University of Hong Kong) is trending on Sep 25 as a lightweight alternative to heavyweight harnesses; Hindsight decoupling in Hermes v0.21.5 is driving attention to standalone memory + agent combos.
**Evidence:**
- ~4,000 lines Python; 99% smaller than Clawdbot (430k+ lines)
- Self-hosted; WebUI + terminal + Telegram/Discord/Slack/Feishu/email
- MCP + persistent memory + multi-agent + automation scheduling
- Supports OpenRouter/Anthropic/OpenAI/DeepSeek/Gemini/Zhihu/DashScope/Moonshot/Groq/vLLM
- v0.3.5 (Sep 15): native terminal workbench, multi-pane browser interface, context visibility
- CN community uses nanobot as primary local-first alternative to cloud-dependent harnesses
- Sources: https://github.com/HKUDS/nanobot, https://nanobot.club/, https://sparkco.ai/blog/nanobot-ai-assistant-ultra-lightweight-agent-framework-in-4000-lines-of-code

---

**Still true** (ongoing threads, no new facts Sep 22-25):
- **aws-strands-harness**: 7.5k stars (unchanged); no new releases Sep 22-25
- **claude-code-projects-parallel-threads**: Sep 17 beta ongoing; expansion continues
- **claude-code-mods-function-hooks**: early access; no new updates
- **copilot-runtime-rust-rewrite**: Sep 16 milestone; ongoing post-launch
- **openai-agents-api-beta**: Sep 10 public beta; ongoing
- **vscode-1138-dev-container-agents**: 1.138 Sep 16; 1.139 Insiders ongoing
- **codex-cli-0155-voice-touchid**: Sep 17 release; ongoing
- **reinventing-ai-employee-packages**: 8 packages, 59 routines, 11 harnesses; ongoing
- **builder-agent-native**: +607 stars Sep 22; ongoing
- **beam-cli-harness-observer**: AGPL-3.0 harness observer; ongoing
- **meta-muse-code**: no new Sep 22-25 releases
- **colibri-lumabri-moe-inference**: no new updates
- **omarchy-herdr-agentic-linux**: no new updates
- **agensi-skill-marketplace**: 70/30 split; 8-point checklist; ongoing
- **kilo-code-anaconda**: Kilo Marketplace; ongoing
- **harness-io-agent-ready-scm**: Code Repository + AI Code Review; ongoing
- **extension-economy-explosion**: SEP-2640 adoption = 2 servers (see finding #8); claudemarketplaces.com 23,600+ skills unchanged
- **addy-osmani-agent-skills**: 89.6k+ stars; ongoing
- **orca-ade-parallel-fleet**: ~77k stars (+6.4k/7 days Sep 25); ongoing
- **ponytail-laziest-dev-skill**: 121,552 stars; ongoing
- **trueforge-open-source-harness**: TrueFoundry TrueForge; ongoing
- **cursor-projects-self-hosted-machines**: Projects beta ongoing; Rollouts Bot is new (see finding #9)
- **aws-kiro-crew-open-source**: Kiro Crew; AgentCore skills; ongoing
- **hiddenlayer-agent-harness-security**: runtime security; ongoing
- **longhorizon-harness-amap**: LongHorizon-Harness; ongoing
- **caspian-talk-to-human-tool**: Caspian SDK; ongoing
- **kubell-whitelist-harness-tools**: allowlist CLI approach; ongoing
- **block-berd-desktop-workspace**: Block Berd v0.6.2; ongoing
- **loopx-long-horizon-control-plane**: LoopX v0.4.x; ongoing
- **cloudflare-computer-agent-runtime**: @cloudflare/computer; ongoing
- **cursor-google-workspace-plugins**: Gmail/Drive/Calendar; ongoing
- **huzzah-pseudocode-editor**: .hz persistent pseudocode; ongoing
- **paperclip-multi-agent-company-os**: Paperclip 79.3k stars; ongoing
- **onecli-yc-s26-credential-gateway**: OneCLI 2.5k+ stars; ongoing
- **harnessrouter-uhp-open-standard**: HarnessRouter UHP; ongoing
- **codex-open-platform-harness**: Agents API public beta; ongoing
- **flue-2-react-hooks-harness**: Flue 2.0; ongoing
- **hax-c-minimalist-agent**: Hax (C); ongoing
- **copilot-autofix-dual-ai-security**: Snowflake injection incident; ongoing
- **bullet-yc-s26-coding-agent**: Bullet 95.8% SWE-bench; ongoing
- **book-to-skill-pdf-to-skill**: book-to-skill 12k+ stars; ongoing
- **cursor-origin-code-hosting**: Origin code hosting beta; ongoing
- **deepseek-harness-v01**: CVE-2026-82533 fixed; ~235k stars; ongoing
- **deepseek-harness-team**: same thread as above; ongoing
- **prime-agent-rlm**: PrimeIntellect 95.5% ARC-AGI-3; ongoing
- **aq-multiplayer-harness**: AQ multiplayer; ongoing
- **qwen-code-alibaba**: Qwen Code; ongoing
- **oh-my-agent**: first-fluke/oh-my-agent; ongoing
- **autoharness-deepmind**: Google DeepMind AutoHarness; ongoing
- **hoplite-yc-s26-cloud-deploy**: Hoplite; ongoing
- **vercel-ai-sdk-harnessagent**: Vercel AI SDK v7 HarnessAgent; ongoing
- **copilot-studio-ga-harness-billing**: Copilot Studio; ongoing
- **microsoft-agent-governance-toolkit**: MIT 9500+ tests; ongoing
- **tinyagents-rust-recursive**: TinyAgents Rust; ongoing
- **sprocket-hardware-software-agent**: Sprocket hardware+software; ongoing
- **gambit-reliable-agent-harness**: Gambit 91 HN pts; ongoing
- **nlah-natural-language-harnesses**: NLAH OSWorld 47.2%; ongoing
- **skills-security-prompt-injection-36pct**: Watcher Live 93%; AIR $50M; Beam CLI; ongoing
- **claude-tag-slack-agent**: Claude Tag Slack; ongoing
- **mimo-code-xiaomi**: MiMo Code 12.6k stars; ongoing
- **ecc-cross-harness-os**: ECC ~266k stars; ongoing
- **kimi-code-moonshot**: Kimi Code; ongoing
- **runtime-yc-p26**: Runtime Docker Compose snapshots; ongoing
- **noclick-always-on**: NoClick; ongoing
- **nyx-offensive-testing**: Nyx Fabraix; ongoing
- **agentguard-security-tool**: AgentGuard PreToolUse hook; ongoing
- **mcp-security-nsa-supply-chain**: GitSpawn + CHAINDROP + CVE + AIR + Watcher (see GitSpawn update #6)
- **yc-qm-multiplayer-harness**: YC QM; ongoing
- **jadepuffer-agentic-security**: JADEPUFFER/SingGuard-NSFA; ongoing
- **grok-build-xai-rust-harness**: Grok-Build 26k stars; ongoing
- **self-harness-auto-optimization**: arXiv papers; ongoing
- **openharness-hkuds**: HKUDS/OpenHarness; ongoing
- **antigravity-gemini-cli-successor**: Antigravity 2.0; ongoing
- **claw-code-claude-rewrite**: Claw Code ~195k stars; ongoing
- **metaharness-scaffold-generator**: ruvnet/agent-harness-generator; ongoing
- **harness-engineering-paradigm**: Google AX makes runtime layer explicit (see finding #2)
- **deerflow-superagent-harness**: DeerFlow 2.0 ByteDance; ongoing
- **omnigent-meta-harness**: Databricks Omnigent; ongoing
- **zot-go-coding-harness**: Zot 299 stars; ongoing
- **omp-omo-pi-derivatives**: oh-my-pi / oh-my-openagent; ongoing
- **yorishiro-presence-harness**: Yorishiro 58 stars; ongoing
- **agentskills-open-standard**: SEP-2640 adoption = 2 servers (see finding #8); ongoing
- **letta-agent-file-format**: Letta .af 1.2k stars; ongoing
- **layered-oss-stack-over-single-framework**: Google AX adds runtime layer explicitly; ongoing
- **macos-harness-proving-ground**: no new macOS-specific events this window
- **ahe-automated-harness-evolution**: HarnessX arXiv; ongoing
- **harness-internal-external-disambiguation**: 🇯🇵 ongoing
- **environment-architect-new-role**: 🇯🇵 ongoing
- **warp-oz-multi-harness**: Warp Oz; ongoing
- **mozilla-otari-llm-gateway**: Mozilla Otari; ongoing
- **statewright-guardrails**: Statewright Rust 373 stars; ongoing
- **headroom-token-compression**: Headroom 65-66k stars; ongoing
- **pi-minimal-agent-harness**: Pi 85,757 stars; ongoing
- **nvidia-skillspector-security**: NVIDIA SkillSpector; ongoing
- **cli-anything-hkuds**: CLI-Anything 46.4k stars; ongoing
- **forge-acp-universal-cli**: Forge ACP; ongoing
- **github-copilot-skills-mcp-ga**: Copilot Rust rewrite; Codex CLI 0.155; ongoing
- **block-buzz-workspace**: Block Buzz Nostr; ongoing
- **zcode-zhihu-agent-ide**: ZCode Z.ai; ongoing
- **devin-desktop-windsurf-rebrand**: v3.10.27 Sep 15 latest; no new Sep 22-25 releases
- **devin-fusion-multimodel**: Devin Fusion; ongoing
- **ambiance-unix-harness**: Ambiance; ongoing
- **kore-artemis-abl**: Kore.ai Artemis ABL; ongoing
- **open-agent-passport-oap**: OAP arXiv; ongoing
- **code-as-agent-harness-paper**: arXiv:2605.18747; ongoing
- **tilde-harness-sdk**: Tilde trytilde.ai; ongoing
- **microsoft-maf-codeact**: Microsoft MAF Harness GA; ongoing
- **kiro-aws-spec-driven**: Kiro; ongoing
- **cursor-spacex-acquisition**: SpaceX acquisition closed; ongoing
- **munder-difflin-office-of-clones**: Munder Difflin 303 HN pts; ongoing
- **aura-mezmo-sre-harness**: AURA 315 stars; ongoing
- **jetstream-clearance-zero-trust**: JetStream $34M seed; ongoing
- **tenable-cyberagents-exchange-inspector**: Tenable CyberAgents Exchange; ongoing
- **vscode-1136-agent-merge**: superseded by 1.138; ongoing
- **sonar-vortex-inside-loop**: Sonar Vortex SemSitter 36% token reduction; ongoing
- **devspace-minimal-mcp-harness**: DevSpace 3.5k stars; ongoing
- **skills-over-mcp-wg-sep2640**: SEP-2640 adoption (see finding #8)
- **accuknox-agentz-enterprise**: AccuKnox AgentZ; ongoing
- **harness-context-tax-problem**: Opus 5.5 40% cheaper = direct cost reduction (see finding #1)
- **gstack-virtual-engineering-team**: gstack 132k stars; ongoing
- **graphify-codebase-knowledge-graph**: Graphify-Labs 115.4k stars; ongoing
- **atlas-source-control-agents**: atlas 3.3k stars; ongoing
- **nodeterm-canvas-terminal-manager**: nodeterm 1.8k stars; ongoing
- **paseo-multi-provider-orchestration**: Paseo 16k stars; ongoing
- **openchamber-ade-opencode**: OpenChamber; ongoing
- **magnitude-local-inference-server**: magnitude 3.3k stars; ongoing
- **opencode-v2-rewrite**: ongoing Sep 2026 updates; ongoing
- **gpt6-astra-provider-adapter-harness**: GPT-6 Astra now trails Opus 5.5 on Terminal-Bench 4.0; ongoing
- **context-mode-tool-output-compression**: context-mode 98% tool output reduction; ongoing
- **openclaude-community-agent**: openclaude 32.7k stars; ongoing
- **ruflo-meta-harness-swarm**: ruflo ruvnet; ongoing
- **vscode-1137-agent-host-protocol**: AHP superseded by 1.138; ongoing
- **air-security-agent-firewall**: AIR Security $50M; ongoing
- **gitspawn-class-vulnerability**: Hermes security sync Sep 24 patches subset (see finding #6)
- **watcher-apolloresearch-monitoring**: Watcher Live 93% recall; ongoing
- **harness-enterprise-governance-gap**: Harness.io n=700 report; ongoing
- **claude-managed-agents-auto-permission**: v2.1.280+ updates; ongoing
- **harnessx-composable-foundry**: HarnessX arXiv; ongoing
- **tencentdb-agent-memory**: TencentDB Agent Memory v2.0; ongoing
- **penguinharness-self-improving**: PenguinHarness; ongoing
- **cloudflare-os-kitesurf**: Cloudflare OS + Kitesurf; ongoing
- **ante-antigma-single-binary**: Ante ~135 HN pts; ongoing

---

## Cross-Source Patterns

**1. Claude Opus 5.5 as harness-model interface stress test (🌐🇯🇵🇨🇳)**
- 4 breaking API changes mean every harness wrapping Claude must update logic, not just model IDs
- JP community (@TakanobuSano Qiita): "「Opus 5にしておけば勝ち」ではなかった" — harness design matters as much as model choice
- CN community: focused on 60% cache-read price drop as highest-leverage lever for long-horizon agent cost
- Platforms: Anthropic blog, Qiita, Zhihu, Pedaily, gihyo.jp, CCLeaks

**2. Infrastructure-below-harness layer solidifying — Google AX + Hindsight split from Hermes (🌐)**
- Google AX explicitly positions as "beneath harnesses"; Hermes v0.21.5 decouples Hindsight to plugin catalog
- The agent infrastructure stack is bifurcating: runtime (Google AX), harness (CC/OC/Hermes), memory (Hindsight/standalone), skills (obra/superpowers, gstack)
- Platforms: InfoQ, HN, freedom.tech, GitHub trending

**3. SEP-2640 spec done, adoption lagging — the distribution gap (🌐🇯🇵)**
- Final spec Sep 13 → 2 servers implementing by Sep 22 (of 572 probed)
- JP framing (Zenn AWS Japan): "Skills are context, MCP is a context protocol" — conceptually clear, implementation backlog real
- Pattern: standards bodies move faster than ecosystem; adoption is the next 6-month battle
- Platforms: API Evangelist, Zenn, ext-skills GitHub issues

**4. Cursor expanding harness surface via bots (🌐)**
- Rollouts Bot + Security Review Bot (Sep 23) extend cursor's harness into deployment monitoring and security review
- Represents coding agent harness expanding from "write code" to "ship code safely"
- Platforms: Releasebot, cursor.com/changelog

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via search) | Google's Open Agentic Orchestrator (AX) | 179 | 74 | "The agent execution problem is infrastructure, not framework. Google just made that explicit." | https://news.ycombinator.com/item?id=49753878 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic | https://www.anthropic.com/claude-opus-5-5 | Opus 5.5 launch; 4 breaking changes |
| 🌐 | Claude Platform Docs | https://platform.claude.com/docs/en/models/opus-5-5/whats-new-opus-5-5 | Breaking changes reference |
| 🌐 | InfoQ | https://www.infoq.com/news/2026/09/google-ax-orchestrator/ | Google AX Kubernetes orchestrator |
| 🌐 | SaaS City | https://saascity.io/blog/google-agent-executor-ax-open-agent-runtime-2026 | AX runtime architecture deep-dive |
| 🌐 | AgentConn | https://agentconn.com/blog/cloud-agent-frameworks-google-ax-orchestration-moat/ | "Orchestration moat is dead" analysis |
| 🌐 | Dev.to | https://dev.to/felix_king_a5ebe226991216/ax-googles-open-agentic-orchestrator-33go | AX feature walkthrough |
| 🌐 | GitHub (google/ax) | https://github.com/google/ax | 11.2k stars, Apache 2.0, Go |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | v2.1.280-282 full changelogs |
| 🌐 | CCLeaks | https://ccleaks.com/news/claude-code-2-1-280-sep-2026 | v2.1.280 MCP + auto mode fixes |
| 🌐 | DevelopersIO (JP) | https://dev.classmethod.jp/en/articles/20260923-cc-updates-v2-1-280/ | "Fable 5.1 surpassed" coverage |
| 🌐 | Claude Updates | https://www.claudeupdates.dev/version/2.1.280 | 114 changes breakdown |
| 🌐 | Freedom.tech | https://freedom.tech/posts/2026-09-24-hermes-agent-0-21-5/ | Hermes v0.21.5 writeup |
| 🌐 | NousResearch GitHub | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.24 | Official v0.21.5 release notes |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OC 2026.9.6 macOS crash rebuild |
| 🌐 | OpenClaw Issue | https://github.com/openclaw/openclaw/issues/156861 | macOS launch crash details |
| 🌐 | OC Releases | https://releases.sh/openclaw | Full release index |
| 🌐 | Releasebot Cursor | https://releasebot.io/updates/cursor | Rollouts Bot + Security Review Bot |
| 🌐 | API Evangelist | https://apievangelist.com/2026/09/22/skills-over-mcp-is-final-and-now-it-needs-servers/ | SEP-2640 adoption: 2/572 servers |
| 🌐 | GitHub (ext-skills) | https://github.com/modelcontextprotocol/ext-skills | 682 stars; SDK PRs pending |
| 🌐 | GitHub (google/ax) | https://github.com/google/ax | AX repo |
| 🌐 | GitHub (nanobot) | https://github.com/HKUDS/nanobot | 48.6k stars, v0.3.5 |
| 🌐 | Nanobot club | https://nanobot.club/ | Official site |
| 🌐 | Sparkco | https://sparkco.ai/blog/nanobot-ai-assistant-ultra-lightweight-agent-framework-in-4000-lines-of-code | 4,000-line architecture |
| 🌐 | GitHub (dream-num/univer) | https://github.com/dream-num/univer | Office Harness for AI Agents |
| 🌐 | GitHub (dsh-univer-office) | https://github.com/dream-num/dsh-univer-office | DSH plugin; 84k+ downloads |
| 🌐 | GitHub (superpowers) | https://github.com/obra/superpowers | Skills methodology; +611/day |
| 🌐 | Developers Digest | https://www.developersdigest.tech/blog/skills-are-the-new-agent-operating-system | Skills as new agent OS |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/09/14/agent-harness-vs-agent-framework-vs-mcp-which-layer-owns-the-loop-state-tools-permissions-and-recovery/ | Layer disambiguation |
| 🌐 | WccfTech | https://wccftech.com/anthropics-claude-opus-5-5-appears-in-claude-code-indicating-imminent-release-as-trump-renames-ai-to-super-intelligence-or-si/ | Opus 5.5 pre-release signal |
| 🌐 | AI Profit Boardroom | https://aiprofitboardroom.com/blog/claude-code-opus-5-5-default-model/ | Opus 5.5 as CC default |
| 🌐 | Vectorize/Hindsight | https://github.com/vectorize-io/hindsight | Hindsight now independent plugin |
| 🌐 | Hermes security sync PR | https://github.com/mtp-44/hermes-agent/pull/8 | GitSpawn upstream fix Sep 24 |
| 🌐 | MCP Market | https://mcpmarket.com/ | 33,766+ servers |
| 🌐 | Claude Marketplaces | https://claudemarketplaces.com/ | 23,600+ skills, 12,800+ MCP |
| 🇯🇵 | Qiita (htani0817) | https://qiita.com/htani0817/items/770773094cdfd0d67b19 | Opus 5.5: Fable 5.1 surpassed; 4 breaking changes |
| 🇯🇵 | Qiita (TakanobuSano) | https://qiita.com/TakanobuSano/items/9281ec7f306073144312 | "Model × Harness" paradigm primer |
| 🇯🇵 | Qiita (sin-aiagent) | https://qiita.com/sin-aiagent/items/d1f21502f0e165d513be | Opus 5.5 API price reduction |
| 🇯🇵 | Qiita (kai_kou) | https://qiita.com/kai_kou/items/5c80fa141ff45a82f71d | 4 breaking changes with fix code |
| 🇯🇵 | Qiita (Takuya__) | https://qiita.com/Takuya__/items/66bc1d3bc1e6b294af18 | Opus 5.5 vs Opus 5 vs Fable 5.1 vs GPT-6 Astra |
| 🇯🇵 | Zenn (aws_japan) | https://zenn.dev/aws_japan/articles/skills-over-mcp | SEP-2640 design deep-dive; JP framing |
| 🇯🇵 | Zenn (atsukish) | https://zenn.dev/atsukish/articles/e080ae2847540d | "MCP = tools, Skills = wisdom" |
| 🇯🇵 | gihyo.jp | https://gihyo.jp/article/2026/09/claude-opus-5.5 | Professional JP dev coverage |
| 🇯🇵 | aiagent-navi.com | https://aiagent-navi.com/ai-agent/opus-5-5-not-working/ | CC v2.1.280+ required for Opus 5.5 |
| 🇯🇵 | AIDB | https://ai-data-base.com/archives/125901 | Long-running agent cost optimization with Opus 5.5 |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2085997119308043440 | "Opus 5.5 costs 40% less — deep night launch" |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2085989078395262474 | "Claude beats GPT-6" CN framing |
| 🇨🇳 | Zhihu (weekly tracker) | https://zhuanlan.zhihu.com/p/670574382 | Sep 23 model/app weekly roundup |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2037564268137165879 | Production agent guide: MCP + Skills |
| 🇨🇳 | SMZDM | https://post.smzdm.com/p/avgx0e77/ | CN consumer: "40% cheaper" framing |
| 🇨🇳 | Pedaily | https://news.pedaily.cn/202609/569597.shtml | "Flagship pricing war intensifying" |
| 🇨🇳 | GitHub (dsh-univer-office) | https://github.com/dream-num/dsh-univer-office | CN-origin Office Harness plugin |
| 🇨🇳 | LearnAgent | https://learnagent.org/library/compare/agent-infrastructure-report-2026/ | Agent infra report 2026; 68% MCP adoption |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per protocol)
├─ 🔵 X: 0 posts (excluded per protocol)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 1 story │ 179 pts │ 74 comments (via search; rate-limited on direct fetch)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no harness-specific posts found in free search)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 8 │ 🇨🇳 8
└─ 🗣️ Top voices: @htani0817 (Qiita), @TakanobuSano (Qiita), @aws_japan (Zenn), @atsukish (Zenn), @kai_kou (Qiita)
```

---

## Out of Scope but Notable

- **vectorize-io/hindsight** (decoupled from Hermes v0.21.5): now a fully standalone agent memory product with biomimetic retrieval (semantic + BM25 + graph + temporal). With Hermes decoupling it from bundled install, hindsight is emerging as a cross-harness memory layer — could merit dedicated tracking under a memory/infra topic rather than harnesses.
- **OpenJarvis (Stanford, March 2026)**: local-first personal AI agent; 88.7% single-turn queries handled locally; 5 composable primitives; closed-loop learning from on-device trace data. Not in prior threads but is in the RyanAlberts/best-of-Agent-Harnesses Sep catalog. Pre-dates this window; flagging as a persistent background thread.
- **ZCode (Z.ai, 6,725 stars, TypeScript)**: distinct coding agent harness for Z.ai platform; trending Sep 25. CN-origin, not previously tracked. Worth monitoring as CN-native harness ecosystem diversifies.

---

## Data Gaps

- **/last30days skill**: Unavailable (unknown skill error); replaced with direct WebSearch + WebFetch sweep
- **Reddit/X/Twitter**: Excluded per research protocol
- **Bluesky**: No harness-specific posts retrievable without authenticated client; SOURCE HEALTH shows bluesky=OK but free search found 0 results
- **YouTube/TikTok/Instagram**: Not searched
- **Polymarket**: No harness-specific prediction markets
- **HN direct fetch**: Rate-limited (HTTP 429); HN data from search snippets only — engagement numbers approximate for Google AX HN post
- **DuckDuckGo HTML endpoint**: Served CAPTCHA for both JP and CN queries (same as prior run); switched to native-language WebSearch
- **Zhihu**: Most Zhihu article pages return HTTP 403 on direct WebFetch; data from search result snippets and cache
- **OpenClaw stars**: Not re-fetched this run (389.5k as of prior searches)
- **Coverage estimate**: ~78% — comprehensive on CC/OC/Hermes/Cursor releases, Opus 5.5, Google AX, SEP-2640 adoption, JP/CN hub coverage; gaps in Reddit/X/Bluesky/YouTube and long-tail HN

---

## Key Quotes

> "AIエージェントの実力 ＝ モデル × ハーネス。『Opus 5にしておけば勝ち』ではなかった" ("AI agent capability = Model × Harness. 'Just use Opus 5 and you win' was wrong") — @TakanobuSano on Qiita ([link](https://qiita.com/TakanobuSano/items/9281ec7f306073144312))

> "スキルはコンテキストであり、MCPはコンテキストプロトコルである。だからこそSkillsはMCPの上に乗れる" ("Skills are context, and MCP is a context protocol. That's why Skills can ride on top of MCP") — Zenn AWS Japan ([link](https://zenn.dev/aws_japan/articles/skills-over-mcp))

> "Model ID replacement alone is insufficient in most cases." — Anthropic, Claude Opus 5.5 migration guide ([link](https://platform.claude.com/docs/en/models/opus-5-5/whats-new-opus-5-5))

> "not a managed service, not an agentic framework, not a specific harness" — Google AX README, positioning as distributed runtime layer beneath all harnesses ([link](https://github.com/google/ax))

> "代理工作负载中缓存token占比高，Opus 5.5的缓存读取价格降了60%，这对长程任务成本影响极大" ("In agent workloads with high cache ratios, Opus 5.5's 60% cheaper cache reads have enormous impact on long-horizon task costs") — Zhihu community ([link](https://zhuanlan.zhihu.com/p/2085997119308043440))

> "The specification is done. Adoption has barely started." — API Evangelist on SEP-2640 ([link](https://apievangelist.com/2026/09/22/skills-over-mcp-is-final-and-now-it-needs-servers/))

> "Opus 5.5 completes a 680,000-line code migration in under a day — work previously requiring weeks." — Anthropic, Opus 5.5 launch ([link](https://www.anthropic.com/claude-opus-5-5))
