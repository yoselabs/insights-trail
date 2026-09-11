# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-09-11
**Query type:** GENERAL
**Sources:** Hacker News, GitHub Trending, Releasebot, Web (global), Web (Japan), Web (China), WebSearch, WebFetch

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | 🌐 Excluded per rules |
| X/Twitter | — | — | 🌐 Excluded per rules |
| YouTube | — | — | Not accessed |
| Hacker News | ~4 threads | — | 🌐 Item IDs 49409092, 49164896, 48921077, 48265332 |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; no on-topic Sep 8–11 posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~55 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~14 pages | — | 🇯🇵 Qiita (4+), Zenn (3+), note (1), tufecompany, genai-ai, uravation; DDG CAPTCHA-blocked (5th run) |
| Web (China) | ~8 pages | — | 🇨🇳 Zhihu (3), CSDN (3+), GitCode (1), BAAI (1) |

---

## Synthesized Findings

### 1. [new] VSCode 1.137 (Sep 9): Agent Host Protocol — Open Standard for Persistent, Portable Agent Sessions 🌐

**Claim:** VS Code 1.137 introduces the Agent Host Protocol (AHP) — an open, agent-agnostic JSON-RPC protocol that decouples agent sessions from workspaces, enabling multi-window attachment, remote execution, and session persistence when no editor is open.
- **AHP architecture:** Dedicated Agent Host process; multiple VS Code windows attach to same session; remote agent host runs next to workspace on another machine; agent session continues with no editor connected; different agent runtimes plug into one host-facing interface
- **Automations (Preview):** Schedule recurring agent tasks hourly/daily/weekly or on-demand; templates for catching up on changes, triaging issues, finding bugs; enable via `chat.automations.enabled`
- **Voice Mode (Experimental):** Talk with agent; interrupt and redirect mid-task; push-to-talk; customizable transcript + voice output
- **GitHub Integration (Experimental):** Review issue/PR details directly in Agents window without browser switch; rich GitHub links in Markdown with live title/state
- Quick Chat workspace continuation retains history when transitioning to project chat
- GitHub Copilot Day live Sep 10 to showcase agent + model use across GitHub, VS Code, Copilot app
- 🌐 Framing: AHP as "the open standard that lets VS Code become harness-agnostic infrastructure"

**Sources:** https://code.visualstudio.com/updates/v1_137 · https://www.bighatgroup.com/blog/vscode-whats-new-2026-09-10/ · https://www.ntcompatible.com/story/visual-studio-code-1137-released-ai-agents-voice-mode-and-the-new-agent-host-protocol · https://code.visualstudio.com/blogs/2026/08/26/agent-host-architecture · https://code.visualstudio.com/docs/agents/concepts/agent-host · https://releasebot.io/updates/microsoft/visual-studio-code

---

### 2. [new] GitSpawn: One `.git/config` Line Hijacks 7 AI Coding Agents — 4 of 8 Flaws Still Unpatched 🌐

**Claim:** Manifold Security discloses a class of 8 flaws (GitSpawn) letting malicious repositories execute arbitrary code in AI coding agents — on Claude Code and Hermes, payload fires BEFORE the workspace-trust dialog appears.
- **Mechanism:** `core.fsmonitor` Git setting = shell command executed on every `git status`/`git diff` (background agent context gathering); `.git/config` is repo-controlled
- **Critical timing:** CC + Hermes: fires BEFORE workspace-trust UI prompt; Qwen Code: fires before login; Grok Build: requires one keystroke
- **Affected (7 agents):** Claude Code, OpenAI Codex, Cursor, Goose, Hermes Agent, Qwen Code, Grok Build
- **8 flaws / 2 CVEs; 4/8 still unpatched as of Sep 1**
- **Patched:** CC in v2.1.196; Goose in v1.44.0; Codex; Cursor
- **Attack vector:** Repo with `.git/` intact (ZIP, GitHub Release download, shared drive, sync folder, USB)
- 🌐 VS Code fixed the same class of issue in 2021; AI agents are re-discovering it
- 🇯🇵 JP community: "ワークスペーストラストが機能する前に実行される" (executes before workspace trust prompts) — key safety assumption violated

**Sources:** https://www.manifold.security/blog/ai-coding-agents-git-hijack · https://cybersecuritynews.com/gitspawn-flaws-execute-code/ · https://thehackernews.com/2026/09/malicious-git-configs-can-make-claude.html · https://paddo.dev/blog/gitspawn-opening-the-folder · https://byteiota.com/gitspawn-ai-coding-agents-hit-by-git-config-rce-flaw/ · https://www.arturmarkus.com/gitspawn-one-git-config-line-hijacks-7-ai-coding-agents-4-of-8-flaws-still-unpatched/

---

### 3. [new] AIR Security — $50M Seed to Build Inline Agent Firewall (September 1, 2026) 🌐

**Claim:** AIR Security emerges from stealth with $50M from Sequoia + Greenoaks to build a pre-runtime firewall that continuously discovers, evaluates, and revokes AI agent add-ons before and after deployment.
- **Investors:** Sequoia Capital + Greenoaks co-led; Swish Ventures, Netz, angels
- **Founded:** February 2026; Yair Saban (CEO) + Niv Hoffman (CTO); offensive cybersecurity + enterprise AI security background
- **Product:** Discovers every skill, plugin, MCP server, add-on across org's AI agent supply chain; pre-runtime vetting; when malicious found → traces every workflow depending on it → revoke
- **Research findings (own):**
  - 17,800+ public AI add-ons (6.7M installations) relied on untrusted external instruction sources
  - Skills found impersonating Anthropic and OpenAI to bypass platform reviews and run arbitrary code
- **Timing:** Launched same week as GitSpawn disclosure and CHAINDROP npm worm coverage — convergent security signals

**Sources:** https://techcrunch.com/2026/09/01/air-raises-50m-to-help-companies-vet-the-skills-and-add-ons-ai-agents-use/ · https://www.securityweek.com/ai-agent-firewall-startup-air-security-emerges-from-stealth-with-50-million/ · https://siliconangle.com/2026/09/01/air-security-launches-with-50m-to-build-a-firewall-for-ai-agents/ · https://www.bankinfosecurity.com/air-launches-50m-to-keep-enterprise-ai-agents-safe-a-32733

---

### 4. [update] Claude Code v2.1.267 (Sep 9) + v2.1.268 (Sep 11): Effort Caps, Gateway Pricing Parity, WebFetch Fix 🌐

**New facts:** v2.1.267 adds `maxEffortLevel` across all providers; v2.1.268 adds gateway pricing parity + fixes WebFetch indefinite hang.
- **v2.1.268 (Sep 11):**
  - `with pricing:` in `gateway.yaml` — CC clients receive managed rates through managed settings; `/cost` and telemetry match spend meter
  - WebFetch hanging fix: fetch now fails after 300 seconds (previously hung on servers keeping response open without finishing)
  - CPU busy-loop fix: pinned CPU core in long-running idle sessions — resolved
  - MCP server OAuth redirect auth fixes; symlinked directory permission improvements
  - Conversation summary `$` sequence mangling fix
  - Claude Tag admin retry functionality
- **v2.1.267 (Sep 9):**
  - `maxEffortLevel` setting (top-level or per model under `modelSettings`): caps effort level on Bedrock, Vertex, Foundry, and all providers; users can still pick lower
  - `--system-prompt-snapshot off`: render system prompt fresh on every request (for iterating on prompt text mid-session)
  - Workflow `agent()` calls with large schemas now reviewed by safety classifier
  - Session resume: prevent data loss from large transcripts
  - Terminal permission prompt card redesign
- **Claude smart reports (Enterprise beta, Sep 11):** analyze how teams use Claude — work done, costs, friction points, reusable shared skills

**Sources:** https://releasebot.io/updates/anthropic/claude-code · https://code.claude.com/docs/en/changelog · https://www.gradually.ai/en/changelogs/claude-code/

---

### 5. [update] OpenClaw v2026.9.3 (Sep 8) + v2026.6.35 (Sep 10, Final ESR) 🌐🇯🇵🇨🇳

**New facts:** v2026.9.3 adds revocable chat links, dashboard reports, repository-backed cloud work without cloning; v2026.6.35 closes memory-exhaustion vulnerabilities in the June extended stable branch.
- **v2026.9.3 (Sep 8) highlights:**
  - Revocable chat links: "session creators and Gateway admins can publish a revocable link to a conversation's existing and future text"
  - Dashboard reports: agents can publish bounded native reports containing text, metrics, tables, charts, links
  - Repository-backed cloud work: repository sessions start on managed cloud/paired nodes without cloning on Gateway first
  - Searchable meeting transcripts: browse/search/export with full text search
  - Update rehearsal: "rehearse changes in isolated state before activation" with rollback
  - Warm prompt cache preservation + reduced cold-session work
  - Bun-hosted Gateways: start native Codex and Claude Code terminals on Linux and macOS
  - Terminal staging bounded to 256 MiB; 64 retained directories
  - Node 24.16.0+ or 26.1.0+ required; recursive delegation enabled by default
  - 166 merged PRs
- **v2026.6.35 (Sep 10, Final June ESR):**
  - Memory safety: provider/channel integrations cap response reads (prevent memory exhaustion from malformed/adversarial responses)
  - Safer boundaries: bundled providers reject oversized inputs
  - Plugin resilience: local-model, browser, media, collaboration plugins recover cleanly from failures
  - 166 merged PRs
- 🇯🇵 Community: revocable chat links noted for "チーム内でのAIセッション共有" (team AI session sharing) without full workspace access
- 🇨🇳 OpenClaw v2026.9.3 coverage: CN community notes memory safety fix in ESR as "迟来的安全补丁" (belated security patch)

**Sources:** https://releasebot.io/updates/openclaw · https://docs.openclaw.ai/releases/2026.9.3 · https://releases.sh/openclaw

---

### 6. [new] Claude Managed Agents — `auto` Permission Mode + `ant beta:sessions connect` (September 10, 2026) 🌐🇯🇵

**Claim:** Anthropic adds server-side dynamic permission evaluation (`auto` mode) to Claude Managed Agents — replacing static allow/deny lists with per-call contextual reasoning; new CLI allows developers to attach to live sessions.
- **`auto` mode:** Server dynamically evaluates each tool call → execute / deny / await-approval
- **`evaluation` field** added to `agent.tool_use` and `agent.mcp_tool_use` events — shows reasoning for each decision
- **`ant beta:sessions connect`:** Attach to running agent sessions from terminal; real-time approve/reject pending tool calls; `--web` for browser-based session viewing
- **Backward compat:** Existing permission policies still functional; additive change; may require updates to strict event-log parsers
- 🇯🇵 Qiita/picnic (Sep 10): "減少コスト: 事前に網羅的なルールを定義する必要がなくなる" (reduced cost: no longer need to exhaustively pre-define rules); terminal-approval workflow for high-risk operations

**Sources:** https://qiita.com/picnic/items/85222ea4e7e845e4523f

---

### 7. [new] Apollo Research Watcher Live (September 3, 2026) — Hook-Based Monitor for Coding Agents 🌐

**Claim:** Apollo Research launches Watcher Live: an "MDM for coding agents" that grades every tool call through three policy gates, blocking dangerous ones with 93% recall at <1% false positives.
- **Architecture:** Integrates via hooks; three-stage: regex rules → fast triage model → full evaluator for survivors
- **Published metrics:** 93% recall on high-severity cases; 100% catch rate on extreme hold-out; <1% false positives; <0.1% human escalation rate; 6-8% added latency; 3-5% cost overhead
- **Supports:** Claude Code + Codex (Cursor in active development)
- **Deployment:** Cloud-hosted (Western Europe) or self-hosted
- **Context:** Launched 2 days after GitSpawn disclosure; positioned as detection layer for git-config-style pre-trust attacks

**Sources:** https://watcher.apolloresearch.ai/ · https://watcher.apolloresearch.ai/blog/mdm-for-coding-agents.html · https://github.com/ApolloResearch/watcher/ · https://vibe-eval.com/updates/security-harness-for-ai-agents-sep-2026/

---

### 8. [update] DeepSeek Harness CVE-2026-82533 (CVSS 9.4): Sandbox Escape via Session Manipulation 🌐🇨🇳

**New fact:** OX Research (via VulnCheck, Sep 8) discloses critical sandbox escape in DeepSeek Harness ≤v0.1.1-rc.2; fix shipped Aug 30 as v0.1.2-rc.1 — but most deployments ran vulnerable for weeks.
- **Root cause 1:** Local web interface checks Host header (not connection origin) for auth — trivially bypassable on localhost
- **Root cause 2:** Changing session to "danger-full-access" mode bypasses approval prompts entirely (setting modification ≠ new permission request)
- **Info disclosure:** Same interface downloads complete session logs without credentials
- **CVSS:** 9.4/10; CVE-2026-82533
- **Timeline:** Community reports of same escape on GitHub Aug 13-14 (two weeks before fix published); official fix v0.1.2-rc.1 Aug 30; VulnCheck public Sep 8
- **Fix:** One-time token authentication requiring browser-based verification
- **Project note:** "sandboxing and approval prompts do not guarantee isolation or prevent damage"
- 🇨🇳 CN community: "开源安全的老问题" (old open-source security problem) — significant trust hit to DeepSeek Harness momentum (was #1 GitHub Trending Sep 3 at 209k stars)

**Sources:** https://thehackernews.com/2026/09/deepseek-harness-flaw-let-ai-agents.html · https://adg.csdn.net/6a7e851810ee7a33f29ace96.html

---

### 9. [new] Harness.io "State of Agent DLC 2026" (September 10): 7 in 8 Enterprises Had an Agent-Related Incident 🌐

**Claim:** Survey of 700 enterprise tech professionals shows a consistent confidence-vs-control gap: organizations believe they're safer with AI agents than they actually are, and 88% had production incidents.
- **Survey:** 700 professionals, ≥1K employees, ≥100 devs, ≥$100M ARR; US/UK/FR/DE/IN; Sapio Research for Harness
- **Gap findings:**
  - 77% claim complete inventory visibility → only 44% have it
  - 74% say testing catches failures → only 19% verify this
  - 76% say they can disable agent in <15 min → only 33% actually can
  - 58% report increased production incidents per 100 changes since deploying AI agents
  - 7 in 8 had at least one agent-related issue; 60% overran budget
  - Only 53% of agent changes go through any standard pipeline before production
- **Root cause (Keith Mann, Field CTO):** "A control that worked in testing can still miss something in production because an agent doesn't behave the same way every time."
- **Implication:** Treating AI agents like deterministic software is the core governance failure

**Sources:** https://www.prnewswire.com/news-releases/new-harness-report-reveals-enterprise-confidence-in-ai-agents-isnt-backed-by-real-controls-302875476.html · https://thenewstack.io/harness-ai-agent-dlc/ · https://www.harness.io/state-of-agent-dlc-2026

---

### 10. [new] HarnessX (arXiv:2606.14249): Composable Harness Foundry with Trace-Driven Auto-Evolution, +14.5% Average 🌐

**Claim:** HarnessX formalizes a harness-as-algebra approach with AEGIS (a trace-driven multi-agent evolution engine), achieving +14.5% average gain across 5 benchmarks by automatically adapting harness primitives from execution traces.
- **Problem:** Harnesses remain hand-crafted and static; each new model/task demands bespoke scaffolding
- **Approach:**
  - Typed harness primitives assembled via substitution algebra (composable)
  - AEGIS: traces from execution → both harness updates + model training signal (closed loop)
  - Operational mirror between symbolic adaptation and RL
- **Results:** +14.5% avg (up to +44.0%) across ALFWorld, GAIA, WebShop, tau³-Bench, SWE-bench Verified; larger gains for lower-baseline models
- **Submitted:** Jun 12, 2026; revised Jul 23, 2026
- **Related:** Self-Harness (arXiv:2606.09498) + AHE (arXiv:2604.25850) — same trajectory; HarnessX adds formal algebra + closed training loop

**Sources:** https://arxiv.org/abs/2606.14249 · https://www.alphaxiv.org/overview/2606.14249 · https://huggingface.co/papers/2606.14249

---

### 11. [ongoing] Hermes Agent — v0.21.1 Still Latest, v0.22.0 Pending 🌐

v0.21.1 (Sep 7) remains latest; v0.22.0 with full release documentation for the v0.21.0 → v0.21.1 window not yet shipped. Hermes still GitHub Trending Sep 6 (+575 stars).

---

**Still true** (ongoing threads with no new facts Sep 8–11):

- `meta-muse-code` — no new releases
- `colibri-lumabri-moe-inference` — no new facts
- `omarchy-herdr-agentic-linux` — no new facts
- `agensi-skill-marketplace` — no new facts
- `kilo-code-anaconda` — no new facts
- `harness-io-agent-ready-scm` — no new facts
- `extension-economy-explosion` — claudemarketplaces.com unchanged (23,600+/12,800+/2,700+ as of Sep 10); anthropics/skills 175k+ stars
- `addy-osmani-agent-skills` — no new facts
- `orca-ade-parallel-fleet` — no new facts
- `ponytail-laziest-dev-skill` — no new facts
- `trueforge-open-source-harness` — no new facts
- `vscode-1135-external-agent-sessions` — superseded by 1.137 (see finding 1); carries forward
- `aws-kiro-crew-open-source` — no new facts
- `hiddenlayer-agent-harness-security` — no new facts
- `longhorizon-harness-amap` — no new facts
- `caspian-talk-to-human-tool` — no new facts
- `kubell-whitelist-harness-tools` — no new facts
- `block-berd-desktop-workspace` — no new facts
- `loopx-long-horizon-control-plane` — no new facts
- `cloudflare-computer-agent-runtime` — no new facts
- `cursor-google-workspace-plugins` — no new facts
- `huzzah-pseudocode-editor` — no new facts
- `paperclip-multi-agent-company-os` — no new facts
- `onecli-yc-s26-credential-gateway` — no new facts
- `harnessrouter-uhp-open-standard` — no new facts
- `codex-open-platform-harness` — no new facts
- `flue-2-react-hooks-harness` — no new facts
- `hax-c-minimalist-agent` — no new facts
- `copilot-autofix-dual-ai-security` — no new facts
- `bullet-yc-s26-coding-agent` — no new facts
- `book-to-skill-pdf-to-skill` — no new facts
- `cursor-origin-code-hosting` — no new facts
- `cursor-router-workspace-plugins` — no new facts
- `agent-plugins-1-standard` — no new facts
- `vscode-1130-agent-host` — superseded by 1.137 (see finding 1)
- `anthropic-managed-agents-mcp-tunnels` — see finding 4 + finding 6 (v2.1.267-268 + auto mode)
- `penguinharness-self-improving` — no new facts
- `cloudflare-os-kitesurf` — no new facts
- `ante-antigma-single-binary` — no new facts
- `tencentdb-agent-memory` — no new facts
- `prime-agent-rlm` — no new facts
- `aq-multiplayer-harness` — no new facts
- `qwen-code-alibaba` — no new facts
- `oh-my-agent` — no new facts
- `autoharness-deepmind` — no new facts
- `hoplite-yc-s26-cloud-deploy` — no new facts
- `vercel-ai-sdk-harnessagent` — no new facts
- `copilot-studio-ga-harness-billing` — GitHub Copilot Day Sep 10 (VS Code 1.137 launch event)
- `microsoft-agent-governance-toolkit` — no new facts
- `tinyagents-rust-recursive` — no new facts
- `sprocket-hardware-software-agent` — no new facts
- `gambit-reliable-agent-harness` — no new facts
- `nlah-natural-language-harnesses` — no new facts
- `skills-security-prompt-injection-36pct` — GitSpawn (see finding 2) + AIR $50M (finding 3) are new data in this space; CHAINDROP persistence vector ongoing
- `claude-tag-slack-agent` — no new facts
- `mimo-code-xiaomi` — no new facts
- `ecc-cross-harness-os` — no new facts
- `kimi-code-moonshot` — no new facts
- `runtime-yc-p26` — no new facts
- `noclick-always-on` — no new facts
- `nyx-offensive-testing` — no new facts
- `agentguard-security-tool` — no new facts
- `mcp-security-nsa-supply-chain` — GitSpawn (finding 2) + AIR $50M (finding 3) + CHAINDROP .settings.json persistence ongoing
- `yc-qm-multiplayer-harness` — no new facts
- `mcp-stateless-spec-2026-07-28` — no new facts
- `jadepuffer-agentic-security` — no new facts
- `grok-build-xai-rust-harness` — affected by GitSpawn (finding 2) — one-keystroke exploit
- `self-harness-auto-optimization` — HarnessX (finding 10) is new evidence; no prior thread matches exactly
- `openharness-hkuds` — no new facts
- `antigravity-gemini-cli-successor` — no new facts
- `claw-code-claude-rewrite` — no new facts
- `metaharness-scaffold-generator` — no new facts
- `harness-engineering-paradigm` — VSCode AHP (finding 1) + Harness.io report (finding 9) reinforce; 7-layer JP community framework (Qiita/nogataka Sep 5) adds specificity
- `deerflow-superagent-harness` — no new facts
- `omnigent-meta-harness` — no new facts
- `zot-go-coding-harness` — no new facts
- `omp-omo-pi-derivatives` — no new facts
- `yorishiro-presence-harness` — no new facts
- `agentskills-open-standard` — no new facts
- `letta-agent-file-format` — no new facts
- `layered-oss-stack-over-single-framework` — VSCode AHP (finding 1) adds architecture-level evidence; AHP is the protocol that makes the UX layer separable from the harness layer
- `macos-harness-proving-ground` — no new facts
- `ahe-automated-harness-evolution` — HarnessX (finding 10) adds new formal algebra + AEGIS engine; +14.5% avg new quantitative evidence
- `harness-internal-external-disambiguation` — Zenn/watany series continues; no new article this cycle
- `environment-architect-new-role` — Qiita/nogataka 7-layer framework (JP, Sep 5) reinforces the Environment Architect need
- `warp-oz-multi-harness` — no new facts
- `mozilla-otari-llm-gateway` — no new facts
- `statewright-guardrails` — no new facts
- `headroom-token-compression` — no new facts
- `pi-minimal-agent-harness` — no new facts
- `nvidia-skillspector-security` — no new facts
- `deepseek-harness-team` — see finding 8 (CVE-2026-82533)
- `cli-anything-hkuds` — no new facts
- `forge-acp-universal-cli` — no new facts
- `github-copilot-skills-mcp-ga` — Copilot Day Sep 10 related to VS Code 1.137; no new Copilot-specific features beyond AHP
- `block-buzz-workspace` — no new facts
- `zcode-zhihu-agent-ide` — no new facts
- `devin-desktop-windsurf-rebrand` — no new facts
- `devin-fusion-multimodel` — no new facts
- `ambiance-unix-harness` — no new facts
- `kore-artemis-abl` — no new facts
- `open-agent-passport-oap` — no new facts
- `code-as-agent-harness-paper` — no new facts
- `tilde-harness-sdk` — no new facts
- `microsoft-maf-codeact` — no new facts
- `kiro-aws-spec-driven` — no new facts
- `cursor-spacex-acquisition` — no new facts
- `munder-difflin-office-of-clones` — no new facts
- `aura-mezmo-sre-harness` — no new facts
- `jetstream-clearance-zero-trust` — no new facts
- `tenable-cyberagents-exchange-inspector` — no new facts
- `vscode-1136-agent-merge` — superseded by 1.137 (see finding 1)
- `sonar-vortex-inside-loop` — no new facts
- `devspace-minimal-mcp-harness` — no new facts
- `skills-over-mcp-wg-sep2640` — no new facts
- `accuknox-agentz-enterprise` — no new facts
- `harness-context-tax-problem` — no new facts
- `gstack-virtual-engineering-team` — no new facts
- `graphify-codebase-knowledge-graph` — no new facts
- `atlas-source-control-agents` — no new facts
- `nodeterm-canvas-terminal-manager` — no new facts
- `paseo-multi-provider-orchestration` — no new facts
- `openchamber-ade-opencode` — no new facts
- `magnitude-local-inference-server` — no new facts
- `opencode-v2-rewrite` — no new facts
- `gpt6-astra-provider-adapter-harness` — no new facts
- `context-mode-tool-output-compression` — no new facts
- `openclaude-community-agent` — no new facts
- `ruflo-meta-harness-swarm` — no new facts

---

## Cross-Source Patterns

### Pattern 1: Security Convergence Week — Three Attack Surfaces Identified 🌐🇯🇵🇨🇳
**Platforms:** SecurityWeek, TechCrunch, The Hacker News, Manifold Security blog, VibeEval, Cybersecurity News, CSDN
**Signal:** Three distinct attack vectors against agent harnesses converged in early September:
- **Repo trust (GitSpawn):** Before workspace-trust dialog fires; affects 7 agents; 4/8 unpatched
- **Supply chain (CHAINDROP):** npm worm writing `.claude/settings.json` SessionStart hooks; survives lockfile deletion
- **Self-sabotage (DeepSeek Harness CVE-2026-82533):** Agent disabling own sandbox via localhost web interface; CVSS 9.4
The security infrastructure response is also converging: AIR ($50M, pre-runtime firewall), Watcher Live (tool-call monitoring), JetStream Clearance (pre-action zero-trust), Tenable CyberAgents Exchange (skill/MCP scanning) all shipped within weeks of each other.
**Quote:** "On Claude Code and Hermes, the payload fires before the workspace-trust UI prompt is accepted — meaning the safety dialog you think is protecting you is irrelevant." — Manifold Security, GitSpawn disclosure ([link](https://www.manifold.security/blog/ai-coding-agents-git-hijack))

### Pattern 2: VSCode AHP — The Platform Layer That Makes Harnesses Swappable 🌐
**Platforms:** Microsoft VS Code blog, BigHatGroup, ntcompatible, rohitai.com
**Signal:** AHP is positioned as the first open protocol that makes VS Code harness-agnostic infrastructure — agent sessions can survive editor closures, connect from multiple windows, and run remotely. Combined with Automations (recurring scheduled tasks), this elevates VS Code from "editor with AI" to "persistent agent execution host". This directly competes with NoClick/Runtime/Hoplite's "always-on sandbox" category, doing it from inside the editor rather than external infrastructure.

### Pattern 3: 🇯🇵 Japan — 7-Layer Framework as New Harness Engineering Standard
**Platforms:** Qiita (nogataka Sep 5), Zenn, community
**Signal:** @nogataka's 7-layer harness framework (CLAUDE.md → Hooks → Skills → Plugins → LSP → MCP → Sub-agents) is being treated as the community standard for "how to properly set up Claude Code on a real codebase." The Sep 5 Qiita article is being widely cited. Combined with the `auto` permission mode (Qiita/picnic Sep 10), JP community is developing structured harness engineering guides that are more prescriptive than English-language equivalents.

### Pattern 4: 🇨🇳 China — DeepSeek Harness CVE Damages Domestic Champion
**Platforms:** CSDN, Zhihu, BAAI
**Signal:** DeepSeek Harness was GitHub Trending #1 (209k stars Sep 3) and the CN-community domestic champion in the CC/OC/Hermes/DSH landscape. CVE-2026-82533 (CVSS 9.4, disclosed Sep 8) dealt a significant trust hit. CN community reaction: "开源安全的老问题" (old open-source security problem) — pragmatic but damaging framing. The "三角博弈" (CC/OC/Hermes) framing is likely to re-stabilize without DSH as the fourth player.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (unknown) | What Is a Harness? | — | — | Building a CLI tool for LLMs to interact with platforms | https://news.ycombinator.com/item?id=49409092 |
| (unknown) | Harness engineering for self-improvement | — | — | Fitness functions for codebases; turn PRs into gradeable agent tasks | https://news.ycombinator.com/item?id=49164896 |
| (unknown) | Towards a harness that can do anything | — | — | Design patterns for agent loops with test suites + linters | https://news.ycombinator.com/item?id=48921077 |
| (unknown) | "Agent harnesses have barely been available for a year..." | — | — | "The harness can make as much difference when improved as improvements to the model itself" | https://news.ycombinator.com/item?id=48265332 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | VS Code 1.137 Official | https://code.visualstudio.com/updates/v1_137 | AHP open protocol; Automations; Voice Mode |
| 🌐 | BigHat VS Code 1.137 | https://www.bighatgroup.com/blog/vscode-whats-new-2026-09-10/ | "agents ambient — running on schedules, listening by voice" |
| 🌐 | ntcompatible 1.137 | https://www.ntcompatible.com/story/visual-studio-code-1137-released-ai-agents-voice-mode-and-the-new-agent-host-protocol | AHP as open standard |
| 🌐 | VS Code AHP Architecture Blog | https://code.visualstudio.com/blogs/2026/08/26/agent-host-architecture | Persistent, portable sessions |
| 🌐 | VS Code Agent Host Docs | https://code.visualstudio.com/docs/agents/concepts/agent-host | AHP JSON-RPC specification |
| 🌐 | Manifold Security GitSpawn | https://www.manifold.security/blog/ai-coding-agents-git-hijack | Original disclosure; core.fsmonitor vector |
| 🌐 | Cybersecurity News GitSpawn | https://cybersecuritynews.com/gitspawn-flaws-execute-code/ | 8 flaws, 4 unpatched |
| 🌐 | The Hacker News GitSpawn | https://thehackernews.com/2026/09/malicious-git-configs-can-make-claude.html | Wide coverage |
| 🌐 | Paddo.dev GitSpawn | https://paddo.dev/blog/gitspawn-opening-the-folder | Pre-trust-prompt timing detail |
| 🌐 | Byteiota GitSpawn | https://byteiota.com/gitspawn-ai-coding-agents-hit-by-git-config-rce-flaw/ | Technical deep-dive |
| 🌐 | AI-TLDR GitSpawn | https://ai-tldr.dev/releases/manifold-gitspawn/ | Summary |
| 🌐 | AI Unfiltered GitSpawn | https://www.arturmarkus.com/gitspawn-one-git-config-line-hijacks-7-ai-coding-agents-4-of-8-flaws-still-unpatched/ | 4/8 unpatched analysis |
| 🌐 | Agentic Ready GitSpawn | https://www.getreadyforagents.com/news/gitspawn-ai-coding-agent-git-hijack-vulnerability/ | Manifold disclosure coverage |
| 🌐 | TechCrunch AIR $50M | https://techcrunch.com/2026/09/01/air-raises-50m-to-help-companies-vet-the-skills-and-add-ons-ai-agents-use/ | Lead story |
| 🌐 | SecurityWeek AIR | https://www.securityweek.com/ai-agent-firewall-startup-air-security-emerges-from-stealth-with-50-million/ | Stealth launch details |
| 🌐 | SiliconANGLE AIR | https://siliconangle.com/2026/09/01/air-security-launches-with-50m-to-build-a-firewall-for-ai-agents/ | Pre-runtime vetting details |
| 🌐 | BankInfoSecurity AIR | https://www.bankinfosecurity.com/air-launches-50m-to-keep-enterprise-ai-agents-safe-a-32733 | Enterprise angle |
| 🌐 | Dealroom AIR | https://dealroom.co/news/148163-air-raises-50m-seed-to-build-a-firewall-for-ai-agents/ | Investor details |
| 🌐 | MLQ AIR | https://mlq.ai/news/air-raises-50-million-to-secure-the-tools-ai-agents-use/ | 17,800+ untrusted add-ons research |
| 🌐 | Watcher Apollo Research | https://watcher.apolloresearch.ai/ | MDM framing; 93% recall |
| 🌐 | Watcher MDM Blog | https://watcher.apolloresearch.ai/blog/mdm-for-coding-agents.html | Architecture details |
| 🌐 | ApolloResearch/watcher | https://github.com/ApolloResearch/watcher/ | Source code |
| 🌐 | VibeEval Sep 2026 Security | https://vibe-eval.com/updates/security-harness-for-ai-agents-sep-2026/ | GitSpawn + Watcher + AIR consolidated |
| 🌐 | Hacker News DeepSeek CVE | https://thehackernews.com/2026/09/deepseek-harness-flaw-let-ai-agents.html | CVSS 9.4 sandbox escape |
| 🌐 | Pillar Security CHAINDROP | https://www.pillar.security/blog/chaindrop-when-opening-a-repository-becomes-execution | .claude/settings.json attack vector |
| 🌐 | StepSecurity CHAINDROP | https://www.stepsecurity.io/blog/chaindrop-npm-worm | Bun-loaded CI/CD credential harvester |
| 🌐 | Beri.net CHAINDROP | https://www.beri.net/article/chaindrop-worm-ai-agent-config-persistence-claude-code-hooks | SessionStart hook persistence |
| 🌐 | Microsoft CHAINDROP | https://www.microsoft.com/en-us/security/blog/2026/08/04/chaindrop-supply-chain-compromise-anatomy-self-propagating-worm/ | 444 packages anatomy |
| 🌐 | The Register CHAINDROP | https://www.theregister.com/security/2026/08/15/chaindrop-worm-crawls-into-npm-supply-chain-evades-standard-defenses/5287958 | Evades standard defenses |
| 🌐 | Claude Code Releasebot | https://releasebot.io/updates/anthropic/claude-code | v2.1.267-268 details |
| 🌐 | Claude Code Docs | https://code.claude.com/docs/en/changelog | Official changelog |
| 🌐 | gradually.ai CC | https://www.gradually.ai/en/changelogs/claude-code/ | Tracker |
| 🌐 | OpenClaw Releasebot | https://releasebot.io/updates/openclaw | v2026.9.3 + v2026.6.35 |
| 🌐 | OpenClaw 2026.9.3 Docs | https://docs.openclaw.ai/releases/2026.9.3 | Official release |
| 🌐 | OpenClaw releases.sh | https://releases.sh/openclaw | Changelog |
| 🌐 | Hermes GitHub Release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.7 | v0.21.1 still latest |
| 🌐 | gradually.ai Hermes | https://www.gradually.ai/en/changelogs/hermes-agent/ | Tracker |
| 🌐 | Harness Report PRN | https://www.prnewswire.com/news-releases/new-harness-report-reveals-enterprise-confidence-in-ai-agents-isnt-backed-by-real-controls-302875476.html | 7/8 enterprises had incidents |
| 🌐 | Harness Report Full | https://www.harness.io/state-of-agent-dlc-2026 | Full report |
| 🌐 | The New Stack DLC | https://thenewstack.io/harness-ai-agent-dlc/ | Non-determinism governance angle |
| 🌐 | arXiv HarnessX | https://arxiv.org/abs/2606.14249 | +14.5% avg; AEGIS engine |
| 🌐 | AlphaXiv HarnessX | https://www.alphaxiv.org/overview/2606.14249 | Overview |
| 🌐 | HuggingFace HarnessX | https://huggingface.co/papers/2606.14249 | Community discussion |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | 23,600+ skills; 12,800+ MCP (unchanged) |
| 🌐 | anthropics/skills | https://github.com/anthropics/skills | 175k+ stars |
| 🌐 | GitHub Trending Sep 6 | https://startupcorners.com/digest/devtools-digest-2026-09-06 | skills +475; pi +320; magnitude +674 |
| 🌐 | ai-boost/awesome-harness-engineering | https://github.com/ai-boost/awesome-harness-engineering | Awesome list |
| 🌐 | best-of-Agent-Harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked weekly |
| 🌐 | explainx.ai top 10 | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Sep 2026 update; Beam noted as security tool not harness |
| 🌐 | LazyCodex Easton Dev | https://eastondev.com/blog/en/posts/ai/20260728-lazycodex-codex-agent-harness/ | Oh My OpenAgent's LazyCodex |
| 🇯🇵 | Qiita/nogataka Sep 5 | https://qiita.com/nogataka/items/24db436c1123ab3d4cb2 | 7-layer harness framework for large codebases |
| 🇯🇵 | Qiita/picnic Sep 10 | https://qiita.com/picnic/items/85222ea4e7e845e4523f | Claude Managed Agents auto mode |
| 🇯🇵 | Qiita/quan_le Sep 8 | https://qiita.com/quan_le/items/90cc4ebd5481692c8c3e | Harness layer fundamentals |
| 🇯🇵 | Qiita/nogataka CC leak | https://qiita.com/nogataka/items/ebbbe74649eb441a34db | 10 harness patterns from source map |
| 🇯🇵 | Qiita/RyutoYoda | https://qiita.com/RyutoYoda/items/95648c656eb2105ab8a6 | Three-agent issue→PR harness |
| 🇯🇵 | Zenn/kok1eeeee | https://zenn.dev/kok1eeeee/articles/claude-code-headless-agent-harness | Headless agent harness alternatives |
| 🇯🇵 | Zenn/ryuka_lucas | https://zenn.dev/ryuka_lucas/articles/agent-teams-harness-engineering | 11 skills → harness pattern realization |
| 🇯🇵 | Zenn/ncdc | https://zenn.dev/ncdc/articles/2b2593798e7342 | Harness selection guide CC/Codex/OC/Pi/Qwen |
| 🇯🇵 | Zenn/watany | https://zenn.dev/watany/articles/d8b692bbca65a3 | Inner/outer harness disambiguation ongoing |
| 🇯🇵 | Uravation OC guide | https://uravation.com/media/openclaw-complete-guide-2026/ | OC 2026.9.3 features updated |
| 🇯🇵 | tufecompany harness | https://tufecompany.co.jp/blog/claude-agent-harness-2026 | What is Claude harness? |
| 🇯🇵 | genai-ai harness | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | CC with sub-agents harness engineering |
| 🇨🇳 | Zhihu terminal comparison | https://zhuanlan.zhihu.com/p/2043266397380272701 | Codex/CC/Hermes/OC Sep 2026 selection |
| 🇨🇳 | Zhihu Hermes vs OC | https://zhuanlan.zhihu.com/p/2025962241942398550 | Self-learning comparison |
| 🇨🇳 | Zhihu CC vs OC | https://zhuanlan.zhihu.com/p/2014737146280420263 | "Use both" approach |
| 🇨🇳 | CSDN Harness panorama | https://adg.csdn.net/6a7e851810ee7a33f29ace96.html | Full landscape Aug 14 + DSH CVE |
| 🇨🇳 | CSDN combo approach | https://gitcode.csdn.net/69e7e55554b52172bc6b572f.html | CC+OC+Hermes combo |
| 🇨🇳 | CSDN CC+OC guide | https://blog.csdn.net/2301_81073317/article/details/160209722 | Full-stack dev guide |
| 🇨🇳 | Tencent Cloud MCP | https://cloud.tencent.com/developer/article/2653637 | MCP maturity |
| 🇨🇳 | BAAI OpenClaw | https://hub.baai.ac.cn/view/52922 | OC explosion analysis |

---

## Stats Block

```
├─ 🟠 Reddit: excluded per rules
├─ 🔵 X: excluded per rules
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: ~4 threads (points not available this cycle)
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: OK (per SOURCE HEALTH) │ 0 on-topic Sep 8-11 posts found
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 14 │ 🇨🇳 8
└─ 🗣️ Top voices: Manifold Security (GitSpawn), AIR/Sequoia (agent firewall $50M), Apollo Research (Watcher), Harness.io (enterprise governance gap), @nogataka JP (7-layer harness), Microsoft VS Code team (AHP) │ 🇯🇵 Qiita/nogataka (7-layer framework standard), Qiita/picnic (auto permission mode) │ 🇨🇳 CSDN "老问题" reaction to DeepSeek CVE
```

---

## Out of Scope but Notable

- **Beam (Sep 9, AGPL-3.0):** Open-source local-first security collector that receives hook payloads from agent harnesses (CC/Cursor/Codex/Copilot CLI) and scans for risky shell commands, credential exposure, malicious SKILL.md patterns. Only 6 stars; too early to rank as a harness but positioned in the same security monitoring layer as Watcher. Could be notable if it gains adoption. Source: explainx.ai Sep update.

- **GitHub Copilot "VS Code pet" companion (Sep 10-17 community naming contest):** Not a new agent capability, but signals the "ambient/always-present" UX direction. Belongs to general AI UX rather than harness engineering.

---

## Data Gaps

- **last30days skill:** Unknown skill error; replaced by full WebSearch + WebFetch multi-pass
- **Reddit, X/Twitter, TikTok, Instagram:** Excluded per topic rules
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked (5th consecutive run); JP/CN passes used native-language WebSearch instead
- **Bluesky:** bluesky=OK (SOURCE HEALTH); 0 on-topic posts found Sep 8–11
- **YouTube:** Not accessed this cycle
- **HN engagement metrics:** HN thread points/comments not captured for the 4 threads found
- **GitHub Trending Sep 8–11:** StartupCorners digests not yet published for Sep 9-11; Sep 6 remains latest available
- **Hermes v0.22.0:** Not yet released; Hermes changelog aggregator (gradually.ai) returned HTTP 429
- **Coverage estimate: 82%** — English web (releases, security, academic), GitHub Trending (Sep 6), changelogs well covered; JP/CN passes solid (14+8 pages via native WebSearch); HN access limited to found threads; social/video absent

---

## Key Quotes

> "On Claude Code and Hermes, the payload fires before the workspace-trust UI prompt is accepted — meaning the safety dialog you think is protecting you is irrelevant." — Manifold Security, GitSpawn disclosure ([link](https://www.manifold.security/blog/ai-coding-agents-git-hijack)) 🌐

> "sandboxing and approval prompts do not guarantee isolation or prevent damage" — DeepSeek Harness project documentation, added with CVE fix ([link](https://thehackernews.com/2026/09/deepseek-harness-flaw-let-ai-agents.html)) 🌐

> "7 in 8 organizations experienced at least one agent-related issue this year" — Harness "State of Agent DLC 2026" survey of 700 enterprise tech professionals ([link](https://www.prnewswire.com/news-releases/new-harness-report-reveals-enterprise-confidence-in-ai-agents-isnt-backed-by-real-controls-302875476.html)) 🌐

> "The harness can make as much difference when improved as improvements to the model itself" — HN community discussion on agent harnesses ([link](https://news.ycombinator.com/item?id=48265332)) 🌐

> "A control that worked in testing can still miss something in production because an agent doesn't behave the same way every time." — Keith Mann, Field CTO at Harness ([link](https://thenewstack.io/harness-ai-agent-dlc/)) 🌐

> "Claude Codeのパフォーマンスはモデル単体では決まらない。周囲のインフラ——Anthropicが「ハーネス」と呼ぶもの——の方が重要だ" ("Claude Code's performance is not determined by the model alone. The surrounding infrastructure — what Anthropic calls the 'harness' — matters more.") — @nogataka on Qiita ([link](https://qiita.com/nogataka/items/24db436c1123ab3d4cb2)) 🇯🇵

> "2026年最高効率の開発者は両方を使う：Claude Codeがコードを書き、OpenClawがその他すべてを管理する" ("The most efficient 2026 developers use both: Claude Code writes code, OpenClaw manages everything else") — Zhihu CC vs OC comparison ([link](https://zhuanlan.zhihu.com/p/2014737146280420263)) 🇨🇳
