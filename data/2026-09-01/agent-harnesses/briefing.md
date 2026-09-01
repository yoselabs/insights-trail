# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-09-01
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web (global), Web (Japan), Web (China), Releasebot, Bluesky

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Excluded per rules |
| YouTube | — | — | Not accessed |
| Hacker News | 3 threads | 429 on direct fetch | "What Is a Harness?" (49409092); "Towards a harness that can do anything" (48921077); August Ask HN |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | — | — | bluesky=OK; no on-topic Sep 1 posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~80 pages | — | 🌐 via WebSearch + WebFetch (last30days skill unavailable) |
| Web (Japan) | ~18 pages | — | 🇯🇵 Qiita (6), Zenn (5), note (1), blog (6); DDG HTML CAPTCHA-blocked |
| Web (China) | ~12 pages | — | 🇨🇳 CSDN (7), Zhihu (3), cnblogs (1), TW/aiposthub (2) |

---

## Synthesized Findings

### 1. [update] OpenClaw 2.0 (v2026.8.1, Aug 31): 16,000-PR "Platform" Pivot — 388k Stars 🌐🇯🇵🇨🇳

**New facts since Aug 28:** GA release (not beta); 933 contributors (569 first-time), 16,000+ merged PRs across installation/agents/plugins/credentials/browser/messaging/automation/memory/native apps. Gateway startup 575ms (from 1.6s). 647 security+quality items addressed.
- **Conversation branching:** rewind/fork from persisted user messages; retain and switch among transcript branches; durable progress cards across all clients
- **Cloud & Remote:** cloud session lifecycle management (idle suspension, auto provisioning); paired devices / cloud worker session mobility; Portals — authenticated dev preview server tunnels without manual port opening
- **Credentials:** private credential requests (masked values, never in chat/model context); 1Password broker (per-secret approval, value-free audit); "approve recurring work once" with revoke+re-approve-on-change
- **Skill Workshop:** end-to-end validation pipeline for reusable agent capabilities (replaces brittle add-on mgmt)
- **Experimental Fleet:** provision/manage separate OpenClaw cells on local Docker/Podman (per-cell resources, logs, diagnostics, backup/restore)
- **Session permission modes:** filesystem access anchored to recorded workspace; team operator roles; optional sandboxed execution; plugin trust review showing capabilities/source/version
- **Messaging:** Telegram Mini App dashboard, Discord voice, first-class Slack, more stable WhatsApp auth
- **Breaking:** OpenProse removed (`openclaw doctor --fix`); OpenAI routes `codex/*` → `openai/*`; SDK imports restructured (Sept 1)
- **CellCog analysis:** "persistent memory, self-learning skills, approvals that outlive a single chat, and sessions a whole team shares" — converging toward colleague-grade behavior
- 🇯🇵 JP Qiita: multiple articles framing OC 2.0 as validation of "AgentController" category (orchestrating multiple coding agents); articles on 9-agent company OS builds
- 🇨🇳 CN CSDN/Zhihu: "OpenClaw 2.0 史诗级更新" (epic update); multiplayer sessions specifically highlighted for enterprise; 3-way comparison with Hermes + Harness Engineering now dominant CN framework

**Sources:** https://github.com/openclaw/openclaw/releases/tag/v2026.8.1 · https://docs.openclaw.ai/releases/2026.8.1 · https://cellcog.ai/blog/openclaw-2-0/ · https://cybersecuritynews.com/openclaw-2-0-released/ · https://www.open-claw.sh/blog/openclaw-2-0-whats-new · https://shattered.io/openclaw-2-0-ai-assistant-release-2026/ · https://www.progressiverobot.com/2026/09/01/openclaw-2-0-multiplayer-ai-coding-enterprises/ · https://qiita.com/sescore/items/f42658a32bfc896669f8 · https://blog.csdn.net/zxc18344522713/article/details/160375133 · https://zhuanlan.zhihu.com/p/2029953897662505928

---

### 2. [update] Hermes v0.21.0 "Pantheon" (Aug 31): Bot Mode + Agent-to-Agent Communications 🌐🇯🇵🇨🇳

**New facts since Aug 28 (v0.20.6):** Named "Pantheon." ~5,800 commits, ~2,475 merged PRs, ~2,100 issues closed, 760+ contributors since v0.20.0.
- **Bot Mode (default-on):** agents get names, deterministic avatar faces, group chats; @-mention any bot in composer; Discord-style rooms with multiple agents + humans; society-of-agents UX vs toolbox-of-agents UX
- **`hermes peer` command:** direct A2A messaging across profiles and gateways; conversations durable + inspectable in canonical Bot Chat (not ephemeral)
- **Cron job intelligence:** "continuity=true" carries output forward; scheduled agents deduplicate against prior runs without redundant LLM calls; monitoring agents learn between runs
- **Live subagent steering:** `delegate_task` gains mid-flight correction; list running children, correct course, halt early preserving partial results; JSON-schema validation + per-delegation cost tracking
- **MCP Command Center:** unified desktop dashboard; drag-in server imports; 30-day cost/usage overlays; background health checks; `hermes://` deep links for one-click server install
- **Browser automation:** in-app browser now agent-driven (navigate/click/read pages directly, pop to system browser); previously observation-only
- **Provider wave:** Meta Model API (Muse Spark), CommandCode, Tencent TokenPlan, Nebius Token Factory, Ramp Router, Actual Computer; model catalog: GLM-5.3-Flash, qwen3.8-max/flash, Gemini 3.7 Flash, MiniMax M3 free, Nemotron 3.5 Lightning
- **Security:** instruction files now require write approval (blocks prompt-injected agents rewriting standing orders); comprehensive redaction across terminal errors/env reads/checkpoints/logs
- 🇯🇵 Zenn/komlock_lab: "after 20+ self-generated skills, similar tasks complete 40% faster"; growing JP guide community (VPS hosting for $6/month Telegram 24/7 access)
- 🇨🇳 aiposthub: 「可以分出不同職能的 Agent Bot 一起工作，還能操作電腦！」("bots with different job functions work together and can operate the computer!")

**Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.31 · https://releasebot.io/updates/nousresearch/hermes-agent · https://digg.com/tech/3wdiuxfn · https://www.marktechpost.com/2026/08/17/nous-research-hermes-bot-mode/ · https://zenn.dev/komlock_lab/articles/ai-agent-hermes-openclaw-claude · https://www.aiposthub.com/hermes-introduces-bot-mode-multi-agent-collaboration/ · https://www.tao.media/nous-research-adds-bot-mode-to-hermes-desktop-for-persistent-ai-teammates/

---

### 3. [update] Muse Code GA (Meta, Aug 31): Workflows Engine + TypeScript SDK (MSP) 🌐

**New facts since Aug 21 (beta):** Graduated to GA. Inter-session messaging, workflow orchestration, rewind, and TypeScript SDK now available.
- **Workflows engine:** decomposes complex tasks across multiple focused subagents; carries intermediate work between stages; single result returned; triggered by "use a workflow"; /workflows for monitoring/stop/restart/cancel
- **SDK (Developer Preview):** TypeScript library; operates over Muse Session Protocol (MSP) — open stdio-based protocol, no server/network, local-only; spawn sessions, stream responses, manage permissions, embed in apps, connect custom tools
- **Inter-session messaging:** Unix sockets; sessions pass warnings/answers to each other non-blocking; one session blocks waiting → another sends answer
- **Rewind:** double-Esc rolls back conversation history to safe rewind points; selective undo
- **Three subscription tiers:** for predictable pricing + increased usage; rolling out now
- Zuckerberg: "Muse Code is out of beta and now built to handle bigger, more complex engineering tasks"
- Install: macOS + Linux via single curl; docs at dev.meta.ai

**Sources:** https://developer.meta.com/ai/resources/blog/muse-code-new-plans-and-features/ · https://www.neowin.net/news/meta-graduates-muse-code-out-of-beta-with-new-features/ · https://cryptobriefing.com/meta-muse-code-paid-plans-sdk-launch/ · https://developer.meta.com/ai/products/muse-code/

---

### 4. [update] Claude Code v2.1.252 (Sep 1): Mac + Remote Control Stability Fixes 🌐

**New facts since Aug 28 (v2.1.251):** Bug-fix release shipped Sep 1.
- Fixes Bash commands failing with "task output swap refused (tasks dir moved or linked)" on some Macs
- Fixes "always allow" not saving in projects without `.claude/settings.local.json`
- Fixes Remote Control sessions stalling for minutes after degraded connections
- Fixes background task notifications with very large failure output exceeding API request size limit
- Prior (v2.1.251 Aug 28) major additions: PreModelSwitch/PostModelSwitch hooks, live subagent streaming to Remote Control, spend-limit bar

**Sources:** https://releasebot.io/updates/anthropic/claude-code · https://code.claude.com/docs/en/changelog · https://www.havoptic.com/tools/claude-code

---

### 5. [new] JustVugg/colibri + lumabri: Pure C MoE Engine Runs 744B Model on 25GB RAM 🌐

**Claim:** colibri (JustVugg/colibri, pure C, zero deps, 26.5k stars) streams 744B GLM-5.2 MoE from disk, enabling frontier-class local inference on consumer hardware; lumabri extends it to distributed peer swarms.
- **Core technique:** dense portion (~9.9GB at int4) resident in RAM; 21,504 routed experts (~370GB total) streamed from disk via per-layer LRU cache; only accessed experts loaded on demand
- **8 model families:** GLM-5.2 (744B), GLM-5.3-Flash (321B, vision), Inkling (975B), Kimi K3 (2.8T), DeepSeek V4 Flash (284B), Qwen3.8-Flash-Next, Qwen3.6, OLMoE
- **Interface:** coli chat / coli serve / coli web — same front end for all models; one C file per model family
- **lumabri** (134 stars, Apache 2.0, pure C): swarm-based distributed inference; byte-for-byte consistent with local (spot-checkable); latency-weighted peer selection + automatic failover; SHA256+ed25519 verification; ChaCha20-Poly1305 transport; NAT compatibility via relay tunnels
- **GitHub Trending #3 on Sep 1, 2026** — first purely local MoE engine to reach this scale

**Why it matters:** colibri decouples frontier model access from cloud cost and hardware scarcity — potentially enables local agent harnesses with 744B+ parameter models on commodity machines.

**Sources:** https://github.com/JustVugg/colibri · https://github.com/JustVugg/lumabri · https://gigazine.net/gsc_news/en/20260710-colibri-glm/ · https://daily.dev/posts/github---justvugg-colibri-run-glm-5-2-744b-moe-on-a-25gb-ram-consumer-machine-pure-c-zero-deps-ydgrbzoqs

---

### 6. [new] Omarchy 4 Quattro (DHH/omacom, Aug 14): Agentic Linux with Coding Agents as OS Citizens 🌐

**Claim:** Omarchy 4 Quattro treats coding agents as system citizens, not applications — crash dumps route to agents, status bars show burn rates, and the OS multiplexer tracks agent state.
- **Full Quickshell desktop rewrite** (bar, launcher, menus, notifications, OSDs, panels, lock screen, polkit — one Quickshell process)
- **Agent as OS citizen:** Setup > Defaults > Agent selects among 9 options (Claude, Codex, Gemini, Grok, Copilot, etc.); crash diagnosis (segfault core dump sent to default agent); Claude Code weekly burn rate in status bar
- **Ships Herdr** as base package multiplexer; OpenCode + Claude Code as default coding agents
- **Omacom Foundation** reached $12.6M (Aug 31); 1Password + 37signals fund patron model
- Community project AgenticArch: "agentic Arch" distro for those wanting agent harness without Omarchy opinions

**Sources:** https://codetocloud.io/blog/omarchy-4-quattro-whats-new/ · https://byteiota.com/omarchy-4-quattro-linux-ai-agents/ · https://itsfoss.com/news/omarchy-ai-agent-focus/ · https://www.kucoin.com/news/flash/omarchy-4-0-released-with-ai-coding-agent-integration · https://www.techtimes.com/articles/326089/20260831/omacom-foundation-hits-126m-1password-37signals-fund-linux-patron-model.htm

---

### 7. [new] Herdr (herdrdev/herdr, Rust, ~29k Stars): Agent-Aware Terminal Multiplexer 🌐

**Claim:** Herdr makes agent state (idle/working/blocked/done) a first-class terminal property — replacing tmux for agent-heavy workflows; adopted by Omarchy 4 as base multiplexer.
- **State tracking:** per-pane agent status (idle/working/blocked/done); tmux has no awareness of what an agent is doing
- **Auto-detects 15+ coding agents:** zero-config setup; 4-color status indicators; native mouse support
- **Unix Socket API** for autonomous orchestration; pre-1.0 with high release cadence
- **Origin:** herdrdev/herdr, Apache-2.0, Rust, first committed March 2026; not a 37signals project despite Omarchy adoption
- Resource: Monitor Claude Code + Codex in one terminal; ~29k stars

**Sources:** https://mer.vin/2026/07/herdr-explained-terminal-multiplexer-for-running-multiple-ai-coding-agents/ · https://www.besthub.dev/articles/herdr-the-github-trending-ai-agent-multiplexer-that-replaces-tmux-ef9169aa9f82 · https://agmazon.com/blog/articles/technology/202608/herdr-terminal-agent-guide-en.html · https://www.shareuhack.com/en/posts/herdr-terminal-agent-multiplexer-guide-2026

---

### 8. [new] Agensi: Curated SKILL.md + MCP Marketplace with 70/30 Creator Revenue Split 🌐

**Claim:** Agensi launched a curated marketplace for SKILL.md skills and MCP servers with security scanning and a creator-friendly revenue model — the only platform covering both artifact types together.
- **70/30 revenue split** (creator keeps 70%); Agensi handles distribution + payment processing
- **8-point automated security checklist** on every listing: prompt injection, data exfiltration, secret detection, dangerous commands, obfuscation, external fetches, credential access, privilege escalation
- Pricing: individual skills $3–$10; bundles $15–$25
- SKILL.md portability: skills work across Claude Code, Codex CLI, Cursor, Gemini CLI, and all compatible agents
- Quality-over-quantity positioning vs. claudemarketplaces (23,600+ items) and Glama (71k+)

**Sources:** https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 · https://www.agensi.io/learn/sell-ai-agent-skills-creator-guide · https://www.agensi.io/learn/complete-list-ai-agent-skill-directories-2026 · https://www.agensi.io/learn/how-to-monetize-skill-md-skills-developer-guide-2026

---

### 9. [new] Kilo Code (Anaconda Acquisition, July 15): Curated Marketplace + Kilo CLI for VS Code Ecosystem 🌐

**Claim:** Kilo Code — open-source agentic VS Code extension + CLI — now under Anaconda ownership with its own curated marketplace of SKILL.md skills, MCP servers, and agent Modes.
- **Kilo Marketplace** (https://github.com/Kilo-Org/kilo-marketplace): curated SKILL.md skills, MCP servers, Modes for Kilo Code VS Code extension + Kilo CLI + compatible agents
- Skills follow open Agent Skills spec (interoperable across all compatible agents)
- 500+ models; MCP server marketplace built-in
- Kilo CLI launched Feb 2026; Anaconda acquisition July 15, 2026
- Positions as open-source Cursor alternative with marketplace-first approach

**Sources:** https://github.com/Kilo-Org/kilo-marketplace · https://www.explainx.ai/blog/kilo-code-ai-coding-agent-guide-2026 · https://kilo.ai/articles/coding-agents-for-vscode

---

### 10. [update] Harness.io Security Agents (Aug 19): Zero-Day Agent Closes Window from 50 Days to Minutes 🌐

**New facts since Aug 28 (Code Repository + AI Code Review):** Security agent suite launched Aug 19, preceding and extending the Aug 27 Code Repository launch.
- **Zero-Day Agent:** monitors 24/7 for new disclosures; identifies all affected pipelines/artifacts instantly; generates validated fix often within minutes of threat going public
- **Context:** attackers now move from disclosure to exploit in ~6 hours; industry average fix time still 50+ days
- **AI SAST:** deterministic scanning + AI noise filter (catches complex vulns like IDOR that traditional tools miss, while cutting false positives)
- **Triage Agent + Remediation Agent** for automated vuln response pipeline
- **Virtual patching** (shield-right): protection in place while fix is developed
- **Harness Agent DLC** (July 21): AI Evals, Agent Deployments (Bedrock AgentCore/Google Agent Runtime with canary releases), AI Configs (prompt + LLM change management), AI Asset Catalog, AgentTrace (end-to-end tracing/auditing)

**Sources:** https://www.harness.io/press-and-news/harness-launches-ai-agents-for-machine-speed-vulnerability-response · https://siliconangle.com/2026/08/19/harness-launches-ai-agents-triage-patch-vulnerabilities/ · https://www.harness.io/blog/harness-announces-capabilities-that-enable-security-at-machine-speed · https://www.harness.io/press-and-news/introducing-harness-agent-dlc · https://siliconangle.com/2026/07/21/harness-launches-agent-dlc-developers-deploy-ai-agents-using-familiar-processes-tools/

---

### 11. [update] Extension Economy (Sep 1): Agensi + Kilo Add Curation Layer; Counts Stable 🌐

**New facts since Aug 28:** Two new curated entrants (Agensi, Kilo Marketplace) competing on quality/security vs. volume. Registry counts stable.
- claudemarketplaces.com: 23,600+ skills / 12,800+ MCP servers / 2,700+ plugins — unchanged from Aug 28
- Glama: 71k+ MCP servers — unchanged
- Agensi: new entrant; curated quality + security scanning + 70/30 revenue split model
- Kilo Marketplace (Anaconda): new open-source curated marketplace for VS Code/CLI ecosystem
- SpaceXAI (Grok): skills/plugins/marketplaces docs published — signals Grok ecosystem forming
- Cosmic JS plugin model: vendor plugin = remote MCP server + skills + auth token, one-time connection
- Trend: marketplace consolidation from fragmented directories to curated, security-scanned stores

**Sources:** https://claudemarketplaces.com/ · https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 · https://github.com/Kilo-Org/kilo-marketplace · https://docs.x.ai/build/features/skills-plugins-marketplaces · https://www.cosmicjs.com/blog/agent-plugin-marketplace · https://mcpmarket.com/ · https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution

---

### 12. [update] addy-osmani-agent-skills: O'Reilly Book Published (Aug 2026) 🌐

**New facts since Aug 25:** Addy Osmani published O'Reilly book on AI-assisted and agentic engineering (August 2026), covering specs, harnesses, evals, context, and production shipping. Extends the agent-skills repo (89.6k+ stars) into formal text.

**Sources:** https://addyosmani.com/blog/agent-harness-engineering/

---

**Still true** (ongoing threads, no new facts this cycle):

- `orca-ade-parallel-fleet` — Orca still growing; no new release since Aug 28 cycle
- `ponytail-laziest-dev-skill` — Ponytail 118,297 stars (up from 115.3k Aug 28); still GitHub Trending #2
- `trueforge-open-source-harness` — no new facts
- `vscode-1135-external-agent-sessions` — no new facts
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
- `deepseek-harness-v01` — no new facts since Aug 28 RC.8; DSH now 206k stars (up from ~135k over prior month; trending #1 Sep 1)
- `cursor-router-workspace-plugins` — no new facts
- `agent-plugins-1-standard` — no new facts
- `anthropic-managed-agents-mcp-tunnels` — see claude-code-doctor-skill-hygiene (v2.1.252 update)
- `penguinharness-self-improving` — no new facts
- `cloudflare-os-kitesurf` — no new facts
- `ante-antigma-single-binary` — no new facts
- `tencentdb-agent-memory` — no new facts
- `prime-agent-rlm` — no new facts
- `aq-multiplayer-harness` — no new facts
- `qwen-code-alibaba` — no new facts; qwen-audio-agent (voice runtime) is adjacent
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
- `skills-security-prompt-injection-36pct` — Hermes instruction file write protection is a new defense mechanism (adjacent)
- `claude-tag-slack-agent` — no new facts
- `mimo-code-xiaomi` — no new facts
- `ecc-cross-harness-os` — no new facts
- `kimi-code-moonshot` — no new facts (K3 model now running in colibri)
- `runtime-yc-p26` — no new facts
- `noclick-always-on` — no new facts
- `nyx-offensive-testing` — no new facts
- `agentguard-security-tool` — no new facts
- `mcp-security-nsa-supply-chain` — Hermes instruction-file write approval adds new defense dimension
- `yc-qm-multiplayer-harness` — no new facts
- `mcp-stateless-spec-2026-07-28` — no new spec facts; ecosystem counts stable
- `jadepuffer-agentic-security` — no new facts
- `grok-build-xai-rust-harness` — still GitHub Trending #4 (26.3k stars); no new release
- `self-harness-auto-optimization` — no new facts
- `openharness-hkuds` — no new facts
- `antigravity-gemini-cli-successor` — no new facts
- `claw-code-claude-rewrite` — no new facts
- `metaharness-scaffold-generator` — no new facts
- `harness-engineering-paradigm` — Muse Code GA + OC 2.0 + Hermes Pantheon all reinforce Agent=Model+Harness
- `deerflow-superagent-harness` — no new facts
- `omnigent-meta-harness` — no new facts
- `zot-go-coding-harness` — no new facts
- `omp-omo-pi-derivatives` — no new facts
- `yorishiro-presence-harness` — no new facts
- `agentskills-open-standard` — Kilo Marketplace + Agensi reinforce SKILL.md portability
- `letta-agent-file-format` — no new facts
- `layered-oss-stack-over-single-framework` — Hermes Pantheon + OC 2.0 + Muse Code SDK all reinforce OSS-stack layering
- `macos-harness-proving-ground` — Omarchy/Herdr add Linux as proving ground alongside macOS
- `ahe-automated-harness-evolution` — no new facts
- `harness-internal-external-disambiguation` — OC 2.0 session permission modes and team operator roles clarify this
- `environment-architect-new-role` — Qiita/ishisaka: developer stopped writing code; role now "architectural design + test requirement definition"
- `warp-oz-multi-harness` — no new facts
- `mozilla-otari-llm-gateway` — no new facts
- `statewright-guardrails` — no new facts
- `headroom-token-compression` — no new facts
- `pi-minimal-agent-harness` — no new facts
- `nvidia-skillspector-security` — no new facts
- `deepseek-harness-team` — absorbed into deepseek-harness-v01 (ongoing)
- `cli-anything-hkuds` — no new facts
- `forge-acp-universal-cli` — Zed ACP registry live; ACP momentum continues
- `github-copilot-skills-mcp-ga` — no new facts
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

---

## Cross-Source Patterns

### Pattern 1: "Triple Release Day" — Aug 31 Convergence of Three Major Platform Updates 🌐🇯🇵🇨🇳

**Platforms:** GitHub, Releasebot, tech press, JP Zenn, CN CSDN/Zhihu

OpenClaw 2.0, Hermes v0.21.0, and Muse Code GA all shipped Aug 31, 2026 — the same day. The convergence is not coordinated but signals the harness ecosystem is entering a production-maturity phase simultaneously across three different architectural bets: distributed control plane (OC), persistent multi-agent workbench (Hermes), and purpose-built SDK platform (Muse Code). All three add: multiplayer/collaboration, persistent memory/continuity, and developer programmability — suggesting these features are now table-stakes for harness platforms rather than differentiators.

**Key signal:** OC 2.0 added team sessions; Hermes added Bot Mode group chats; Muse Code added inter-session messaging. Three independent teams converged on "agents communicating with agents and teams" as the next unlock.

---

### Pattern 2: Harness-as-OS Is a Real Design Stance — Omarchy + Herdr Validate It 🌐

**Platforms:** GitHub, CodeToCloud, itsfoss, DevOps Daily

Omarchy 4 Quattro treats coding agents as operating system citizens — not applications that run alongside your OS. Herdr (29k stars) makes agent state a first-class property in the terminal. This is distinct from "run an agent" or "use an agent tool" — it's "the OS knows whether your agent is idle, blocked, or done." The Linux community is cautious (itsfoss: "Omarchy Bets Its Future on AI Agents While the Linux World Stays Cautious") but Omarchy is shipping.

**Quote:** "Omarchy 4 ships Herdr as a second multiplexer in its base package set" — the OS-level agent state awareness is now a distribution choice, not a configuration.

---

### Pattern 3: Marketplace Curation War — Quality vs. Volume 🌐

**Platforms:** Agensi, Kilo-Org, claudemarketplaces.com, DigitalApplied, Cosmic JS

claudemarketplaces (23,600+ skills) and Glama (71k+ servers) compete on volume; Agensi and Kilo Marketplace compete on curation + security scanning. Agensi's 8-point checklist (prompt injection, secret detection, privilege escalation, etc.) and 70/30 revenue split signal a shift from "discover anything" to "trust the store." This parallels the iOS App Store vs. web market transition. SpaceXAI publishing skills/plugins docs adds a third major harness ecosystem with marketplace dynamics.

---

### Pattern 4: JP Community Signals Role Shift Concretely 🇯🇵

**Platforms:** Qiita, Zenn, note.com

Qiita/ishisaka (Sep 1): "It's been 6 months since I stopped writing code." Agent role has expanded beyond coding to bug investigation, security testing, deployment monitoring. Developers moving to "architectural design and test requirement definition." This is the most concrete first-person testimony of the "Environment Architect" role transition documented in prior JP coverage. JP community is also generating Claude Code → Hermes migration guides — first signal of competitive pressure on Claude Code in the JP market.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | What Is a Harness? | — | — | 429 rate-limited on fetch | https://news.ycombinator.com/item?id=49409092 |
| — | Towards a harness that can do anything | — | — | Agent coordination + verification | https://news.ycombinator.com/item?id=48921077 |
| — | Ask HN: What are you working on? (August 2026) | — | — | Developer agent workflow adoption | https://news.ycombinator.com/item?id=49233423 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | OpenClaw GH | https://github.com/openclaw/openclaw/releases/tag/v2026.8.1 | OC 2.0: 388k stars, 933 contributors, 16k PRs |
| 🌐 | OpenClaw docs | https://docs.openclaw.ai/releases/2026.8.1 | Full feature list |
| 🌐 | CellCog OC 2.0 | https://cellcog.ai/blog/openclaw-2-0/ | Analysis: colleague-grade convergence |
| 🌐 | open-claw.sh | https://www.open-claw.sh/blog/openclaw-2-0-whats-new | Official explainer |
| 🌐 | shattered.io | https://shattered.io/openclaw-2-0-ai-assistant-release-2026/ | 933 coders stat |
| 🌐 | progressiverobot | https://www.progressiverobot.com/2026/09/01/openclaw-2-0-multiplayer-ai-coding-enterprises/ | Enterprise multiplayer |
| 🌐 | cybersecuritynews | https://cybersecuritynews.com/openclaw-2-0-released/ | Security hardening detail |
| 🌐 | Hermes GH release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.31 | v0.21.0 full changelog |
| 🌐 | Digg Hermes | https://digg.com/tech/3wdiuxfn | Pantheon overview |
| 🌐 | MarkTechPost Hermes | https://www.marktechpost.com/2026/08/17/nous-research-hermes-bot-mode/ | Bot Mode announcement |
| 🌐 | Releasebot Hermes | https://releasebot.io/updates/nousresearch/hermes-agent | Release tracker |
| 🌐 | tao.media Hermes | https://www.tao.media/nous-research-adds-bot-mode-to-hermes-desktop-for-persistent-ai-teammates/ | Persistent AI teammates framing |
| 🌐 | Meta Muse Code blog | https://developer.meta.com/ai/resources/blog/muse-code-new-plans-and-features/ | GA features: workflows, SDK, MSP |
| 🌐 | Neowin Muse Code | https://www.neowin.net/news/meta-graduates-muse-code-out-of-beta-with-new-features/ | Aug 31 GA coverage |
| 🌐 | Crypto Briefing | https://cryptobriefing.com/meta-muse-code-paid-plans-sdk-launch/ | Paid plans detail |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | v2.1.252 tracker |
| 🌐 | colibri GitHub | https://github.com/JustVugg/colibri | Pure C, 26.5k stars, GLM-5.2 on 25GB |
| 🌐 | lumabri GitHub | https://github.com/JustVugg/lumabri | Swarm MoE inference, Apache 2.0 |
| 🌐 | Gigazine colibri | https://gigazine.net/gsc_news/en/20260710-colibri-glm/ | Consumer MoE inference |
| 🌐 | daily.dev colibri | https://daily.dev/posts/github---justvugg-colibri-run-glm-5-2-744b-moe-on-a-25gb-ram-consumer-machine-pure-c-zero-deps-ydgrbzoqs | Community reception |
| 🌐 | Omarchy CodeToCloud | https://codetocloud.io/blog/omarchy-4-quattro-whats-new/ | Full Quattro breakdown |
| 🌐 | Omarchy byteiota | https://byteiota.com/omarchy-4-quattro-linux-ai-agents/ | Agentic Linux |
| 🌐 | Omarchy itsfoss | https://itsfoss.com/news/omarchy-ai-agent-focus/ | Linux community reaction |
| 🌐 | Omarchy KuCoin | https://www.kucoin.com/news/flash/omarchy-4-0-released-with-ai-coding-agent-integration | Aug 14 date |
| 🌐 | Omacom Foundation | https://www.techtimes.com/articles/326089/20260831/omacom-foundation-hits-126m-1password-37signals-fund-linux-patron-model.htm | $12.6M patron model |
| 🌐 | Herdr mer.vin | https://mer.vin/2026/07/herdr-explained-terminal-multiplexer-for-running-multiple-ai-coding-agents/ | Herdr mechanics |
| 🌐 | Herdr besthub.dev | https://www.besthub.dev/articles/herdr-the-github-trending-ai-agent-multiplexer-that-replaces-tmux-ef9169aa9f82 | Herdr vs tmux |
| 🌐 | Herdr agmazon | https://agmazon.com/blog/articles/technology/202608/herdr-terminal-agent-guide-en.html | Mastering guide |
| 🌐 | Agensi marketplace | https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 | 70/30 rev split, curated |
| 🌐 | Agensi creator | https://www.agensi.io/learn/sell-ai-agent-skills-creator-guide | Monetization guide |
| 🌐 | Kilo Marketplace GH | https://github.com/Kilo-Org/kilo-marketplace | SKILL.md + MCP + Modes |
| 🌐 | Kilo Code explainx | https://www.explainx.ai/blog/kilo-code-ai-coding-agent-guide-2026 | Anaconda acq. July 15 |
| 🌐 | claudemarketplaces | https://claudemarketplaces.com/ | 23,600+ skills, 12,800+ MCP, 2,700+ plugins |
| 🌐 | SpaceXAI skills docs | https://docs.x.ai/build/features/skills-plugins-marketplaces | Grok ecosystem |
| 🌐 | Cosmic JS plugins | https://www.cosmicjs.com/blog/agent-plugin-marketplace | Vendor plugin model |
| 🌐 | Harness security PR | https://www.harness.io/press-and-news/harness-launches-ai-agents-for-machine-speed-vulnerability-response | Zero-Day Agent |
| 🌐 | Harness sec blog | https://www.harness.io/blog/harness-announces-capabilities-that-enable-security-at-machine-speed | 6hr window / 50-day avg |
| 🌐 | SiliconAngle Harness | https://siliconangle.com/2026/08/19/harness-launches-ai-agents-triage-patch-vulnerabilities/ | Triage+remediation agents |
| 🌐 | Harness DLC | https://www.harness.io/press-and-news/introducing-harness-agent-dlc | AI Evals, AgentTrace |
| 🌐 | GitHub Trending digest | https://dev.to/muildev/github-trending-digest-2026-09-01-4pik | Sep 1 trending repos |
| 🌐 | qwen-audio-agent | https://github.com/QwenAudio/qwen-audio-agent | Voice runtime for coding agents |
| 🌐 | Winder.ai comparison | https://winder.ai/ai-agent-harness-comparison/ | 100+ harnesses compared |
| 🌐 | RyanAlberts best-of | https://github.com/RyanAlberts/best-of-Agent-Harnesses | Ranked list 100+ harnesses |
| 🌐 | Faros harness eng | https://www.faros.ai/blog/harness-engineering | "Mistake → engineer a solution" |
| 🌐 | Addy O blog | https://addyosmani.com/blog/agent-harness-engineering/ | O'Reilly book Aug 2026 |
| 🌐 | ExplainX Top 10 | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Open vs closed ranking |
| 🌐 | Boaoai phase | https://www.boaoai.cn/en/news/2026-08-25-ai-agent-harness-engineering-new-phase/ | Harness engineering phase signal |
| 🌐 | Zed ACP | https://zed.dev/acp | ACP registry |
| 🌐 | Zed ACP registry | https://zed.dev/blog/acp-registry | Registry is live |
| 🌐 | ACP danilchenko | https://www.danilchenko.dev/posts/agent-client-protocol/ | ACP in JetBrains + Zed |
| 🌐 | DigitalApplied mktpl | https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution | Marketplace landscape |
| 🇯🇵 | Qiita/rino_yume | https://qiita.com/rino_yume/items/9cbf9497295fa3eb8690 | Sep 1 pricing comparison table |
| 🇯🇵 | Qiita/ishisaka | https://qiita.com/ishisaka/items/d2a70e614b97695aea12 | "6 months without writing code" |
| 🇯🇵 | Qiita/sescore | https://qiita.com/sescore/items/f42658a32bfc896669f8 | 9-agent company OS on OpenClaw |
| 🇯🇵 | Qiita/nogataka | https://qiita.com/nogataka/items/34cfbee988a9cd873c91 | OpenClaw in Japanese env |
| 🇯🇵 | Zenn/komlock_lab | https://zenn.dev/komlock_lab/articles/ai-agent-hermes-openclaw-claude | Hermes: 40% faster after 20+ skills |
| 🇯🇵 | Zenn/alexkyo | https://zenn.dev/alexkyo/articles/5ef5e16536fd49 | Hermes on $6/mo VPS + Telegram |
| 🇯🇵 | Zenn/yukikato | https://zenn.dev/yukikato/articles/openclaw-vs-hermes-agent-architecture | Design philosophy comparison |
| 🇯🇵 | Zenn/mkj | https://zenn.dev/mkj/articles/9431e342db202f | OpenClaw vs Hermes conceptual |
| 🇯🇵 | Zenn/kai_kou | https://zenn.dev/kai_kou/articles/200-claude-code-third-party-policy-guide | Claude Code 3rd-party limits |
| 🇯🇵 | note/kudoucraft | https://note.com/kudoucraft/n/nccfb87156423 | Hermes as "growing AI employee" |
| 🇯🇵 | blog.lai.so | https://blog.lai.so/hermes-agent/ | OpenClaw boom retrospective |
| 🇯🇵 | fyve.co.jp migration | https://fyve.co.jp/ai-agents/hermes-agent/articles/claude-code-to-hermes-agent-migration | Claude Code → Hermes migration guide |
| 🇨🇳 | CSDN/weixin_43882318 | https://blog.csdn.net/weixin_43882318/article/details/160158346 | Three-way CN tech stack framing |
| 🇨🇳 | CSDN/zxc | https://blog.csdn.net/zxc18344522713/article/details/160375133 | Ultimate CN guide: OC vs Hermes vs HE |
| 🇨🇳 | CSDN/xx_nm98 | https://blog.csdn.net/xx_nm98/article/details/161777384 | Three-path framework comparison |
| 🇨🇳 | CSDN/RickyIT | https://blog.csdn.net/RickyIT/article/details/161147168 | Theory → full-chain analysis |
| 🇨🇳 | CSDN/hermes_han | https://blog.csdn.net/hermes_han/article/details/160475778 | Hermes vs OpenClaw architecture |
| 🇨🇳 | Zhihu ultimate guide | https://zhuanlan.zhihu.com/p/2029953897662505928 | OC vs Hermes vs HE, enterprise ROI |
| 🇨🇳 | Zhihu research report | https://zhuanlan.zhihu.com/p/2026622473097978502 | Hermes research report + OC compare |
| 🇨🇳 | Zhihu self-learning | https://zhuanlan.zhihu.com/p/2025962241942398550 | Self-learning agents depth compare |
| 🇨🇳 | cnblogs/ybmj | https://www.cnblogs.com/ybmj/p/19977318 | Battle framing; developer sentiment |
| 🇨🇳 | aiposthub Hermes Bot | https://www.aiposthub.com/hermes-introduces-bot-mode-multi-agent-collaboration/ | Bot Mode TW/CN coverage |
| 🇨🇳 | aiposthub OC 2.0 | https://www.aiposthub.com/openclaw-2-ai-agent-platform/ | OC 2.0 features + upgrade risks |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: excluded per rules
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 3 threads │ rate-limited (429) on direct fetch │ points not retrieved
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: bluesky=OK │ no on-topic Sep 1 posts found
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~80 pages │ 🇯🇵 18 │ 🇨🇳 12
└─ 🗣️ Top voices: ishisaka (JP: "6 months without writing code"), komlock_lab (JP: Hermes 40% faster), rino_yume (JP: Sep 1 pricing table), Teknium/NousResearch (Hermes Pantheon), JustVugg (colibri), DHH (Omarchy 4) │ CSDN: weixin_43882318, zxc; Zhihu: enterprise ROI guides
```

---

## Out of Scope but Notable

- **qwen-audio-agent (QwenAudio, v1.11.0 Aug 20):** Full-duplex voice runtime driving coding agents (Claude Code, Codex, OpenCode, Kimi Code) over ACP — frontend conversation + background tasks in parallel, barge-in, local wake word. (https://github.com/QwenAudio/qwen-audio-agent) — potentially paradigm-shifting for ambient/voice agent workflows; fits agent-harnesses but voice-first angle is novel enough to flag; may belong in a future "voice interface" topic if that emerges.

- **colibri/lumabri** (Finding #5 above) — the pattern of streaming 744B MoE experts from disk is architecturally distinct from prior local inference approaches (bundled llama.cpp / Ante). If generalized, this is a different class of local model access — could eventually change the cost structure of local-first agent harnesses dramatically.

- **Google Agentic Resource Discovery** (June 2026, open spec) — published specification for publishing, discovering, and verifying AI capabilities across the web. No dedicated thread yet; could be foundational if it spreads. Source: mentioned in Faros.ai harness engineering blog (https://www.faros.ai/blog/harness-engineering).

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram:** not accessed; social signal layer absent (~15% coverage gap)
- **last30days skill:** unavailable in this CI environment; replaced with WebSearch + WebFetch multi-pass
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked again (third consecutive run); JP/CN passes used native-language WebSearch — lower raw coverage than direct DDG browse
- **Bluesky:** bluesky=OK per SOURCE HEALTH; no on-topic Sep 1 posts found
- **HN rate-limiting (429):** "What Is a Harness?" (49409092) and "Towards a harness" (48921077) inaccessible on direct fetch; only search-snippet context available
- **HN points unavailable** for Sep 1 threads
- **Coverage estimate: 80%** — English web and GitHub well covered (major releases confirmed from official sources); JP/CN passes good (18+12 pages, key communities reached); social layer absent (~20% gap)

---

## Key Quotes

> "persistent memory, self-learning skills, approvals that outlive a single chat, and sessions a whole team shares" — CellCog analysis of OpenClaw 2.0 converging on colleague-grade behavior ([link](https://cellcog.ai/blog/openclaw-2-0/)) 🌐

> 「コードを書かなくなって6か月経った」("It's been 6 months since I stopped writing code") — Qiita/ishisaka, Sep 1, 2026 ([link](https://qiita.com/ishisaka/items/d2a70e614b97695aea12)) 🇯🇵

> 「育つAI従業員」("Growing AI Employee") — note.com/kudoucraft on Hermes Agent as persistent self-improving agent ([link](https://note.com/kudoucraft/n/nccfb87156423)) 🇯🇵

> 「Hermes 推出「Bot Mode」，可以分出不同職能的 Agent Bot 一起工作，還能操作電腦！」("Hermes launches Bot Mode — bots with different job functions work together and can operate the computer!") — aiposthub.com ([link](https://www.aiposthub.com/hermes-introduces-bot-mode-multi-agent-collaboration/)) 🇨🇳

> "Omarchy 4 ships Herdr as a second multiplexer in its base package set" — Omarchy is now making agent state awareness a distribution choice, not a configuration ([link](https://codetocloud.io/blog/omarchy-4-quattro-whats-new/)) 🌐

> "OpenClaw 2.0 史诗级更新" ("OpenClaw 2.0 epic update") — consensus framing across multiple CN sources (CSDN, Zhihu, cnblogs) 🇨🇳

> "Muse Code is out of beta and now built to handle bigger, more complex engineering tasks" — Mark Zuckerberg ([link](https://developer.meta.com/ai/resources/blog/muse-code-new-plans-and-features/)) 🌐

> "Attackers are using frontier AI models to find and chain vulnerabilities faster than ever, going from disclosure to first exploit in as little as six hours" — Harness Zero-Day Agent launch ([link](https://www.harness.io/blog/harness-announces-capabilities-that-enable-security-at-machine-speed)) 🌐
