# Agent Harnesses — Daily Briefing
**Date:** 2026-11-03
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub Trending, Security Feeds

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 stories | 207+430+180 pts, 136+~80 comments | Prospero 207pts, Memdoor 430pts, Orkas 180pts |
| Web (global) | 58 pages | — | 🌐 via WebSearch + site fetches |
| Web (Japan) | 6 pages | — | 🇯🇵 Qiita, Zenn, note |
| Web (China) | 5 pages | — | 🇨🇳 TechNode CN, Dataconomy CN, CSDN, Zhihu, Cnblogs |
| GitHub Trending | 8 repos | 7K–108K stars | Nov 1–3 trending |
| Security Feeds | 6 articles | — | BleepingComputer, HackerNews, Sophos, SCWorld, Register |

---

## Synthesized Findings

### 1. [new] DeepSeek dsh-superagent: proactive coding agent monitors GitHub/Feishu without being summoned
**Claim:** DeepSeek Harness team released dsh-superagent (MIT, TypeScript, v0.1.0, Nov 1) — a research prototype that monitors GitHub and Feishu group chats for coding tasks and accepts them without direct invocation; median completion 12.4 min.
- **Evidence:**
  - Dual-layer architecture: long-running Router dispatches to parallel isolated Worker sessions
  - Default "Observe mode" records requests agent would have accepted without executing — safe for regulated deployment
  - Monitors GitHub issues/PRs and Feishu dev channels; auto-creates PRs
  - 9,000+ stars within 24h of release; MIT; TypeScript; runs as DeepSeek Harness profile
  - 95th-pct task time: 15.7 min
  - 🇨🇳 Feishu integration heavily covered in CN press (TechNode CN, CSDN); "主动找活" (proactively finds work) framing resonates in CN enterprise
  - 🇯🇵 JP coverage in note (simizu_note_ai): Observe mode framing highlighted
- **Sources:** https://www.bloomberg.com/news/articles/2026-11-01/deepseek-drops-enhanced-coding-agent-with-aim-to-rival-anthropic | https://dataconomy.com/2026/11/02/deepseek-releases-open-source-dsh-superagent-coding-agent/ | https://cn.technode.com/post/2026-11-02/deepseek-dsh-superagent-coding-agent-prototype/ | https://devops.com/deepseek-wants-coding-agents-to-stop-waiting-for-instructions | https://note.com/simizu_note_ai/n/nbf09b1689e83
- **Platforms:** Web global, Web CN 🇨🇳, Web JP 🇯🇵, GitHub Trending

### 2. [new] Prospero: 5MB C++ native harness challenges Electron-based incumbents
**Claim:** Prospero (Oct 31, skeeto/prospero, Unlicense + paid Pro) is a native GUI coding harness using ~5MB vs "two orders of magnitude" more for alternatives; headless-detachable, subagent-capable; 207 HN pts.
- **Evidence:**
  - Languages: C++ with Dear ImGui docking; Windows (w64devkit-native), macOS, Linux
  - Features: subagents, Git worktrees, MCP, desktop GUI control for testing, headless re-attachable sessions
  - Plain INI config (not JSON); API-key required (no subscription billing)
  - HN top quote: "FIVE megabytes. Wow. What are we _doing_ everywhere else."
  - HN concern: single-developer sustainability, extensibility, API-only pricing (no CC-style sub)
  - Community Edition: Unlicense (free); Professional Edition: paid
  - Philosophy: "Never wait forever. Every operation has a deadline."
- **Sources:** https://nullprogram.com/blog/2026/10/31/ | https://news.ycombinator.com/item?id=50315226 | https://github.com/skeeto/prospero | https://munderdiffl.in/blog/agent-tools-today-2026-11-01/
- **Platforms:** HN, Web global

### 3. [new] Memdoor: 5 small models > 1 frontier on LiveCodeBench Hard
**Claim:** Memdoor (Nov 1, Apache 2.0, guregodevo/memdoor) team-solve workflow runs 5 Qwen3.8-27B models collaborating via files, scoring 9.8/10 LCBench Hard vs Fable 5's 8.0; 49/50 runs solved vs 40/50.
- **Evidence:**
  - Agent roles: planner, 2 ideators, solver, manager + repair worker
  - Communication: files on disk only (no shared memory/context)
  - 8 YAML files, zero code; based on GVS5H method
  - 430+ HN points; also beats GVS5H harness (9.6)
  - Claim: "five small models on one programming problem"
  - Demonstrates: harness design (coordination + isolation) can match frontier-model raw capability
- **Sources:** https://github.com/guregodevo/memdoor | https://aiweekly.co/alerts/memdoors-five-qwen38-27b-team-beats-fable-5-at-livecodebench | https://munderdiffl.in/blog/agent-tools-today-2026-11-02/
- **Platforms:** HN, Web global

### 4. [new] Orkas: local-first desktop AI team orchestrating 16 agents + incumbent harnesses
**Claim:** Orkas (Oct 31–Nov 1, MIT, Orkas-AI/Orkas) provides a Commander agent that decomposes goals into tasks for 16 built-in specialists plus Claude Code, Codex, OpenCode, OpenClaw, Hermes — free desktop app for macOS/Windows.
- **Evidence:**
  - Commander = goal → to-do breakdown → parallel/sequential specialist assignment
  - Specialists: researchers, writers, coders, designers, domain agents (e-commerce, video production)
  - Projects, scheduled automations, connectors
  - 7,016 stars; 1,044 new stars in first day; MIT
  - macOS 12+ (Apple Silicon + Intel); Windows 10+
- **Sources:** https://github.com/Orkas-AI/Orkas | https://orkas.ai/ | https://munderdiffl.in/blog/agent-tools-today-2026-11-01/
- **Platforms:** HN, GitHub Trending, Web global

### 5. [new] Factory Droid 1.0: Script Mode collapses hundreds of tool calls to one model request
**Claim:** Factory Droid 1.0 (Oct 30) makes programmatic tool calling default via Script Mode; model-agnostic; factory claims 17% fewer tokens than Claude Code; available as desktop/TUI/SDK.
- **Evidence:**
  - Script Mode: agent writes a program calling up to hundreds of tools; one model request executes them
  - Model-agnostic (not locked to one provider)
  - Example: 151 Linear issue cleanup → 2 model requests, 61K tokens
  - Available: macOS + Windows desktop, terminal UI, Droid SDK
  - Leads native harnesses on Terminal-Bench 4 (Factory's own benchmarks)
  - Efficiency claim: 17% fewer tokens vs CC; 51x cost reduction vs cited comparison (independent verification pending)
- **Sources:** https://www.marktechpost.com/2026/10/31/factory-droid-1-0-frontier-harness/ | https://aicoder.com/news/news-20261029-factory-droid-1-0-programmatic-tool-calling-terminal-bench-4-harness | https://fourweekmba.com/ai-factory-says-droid-beats-claude-code-using-17-fewer-tokens/
- **Platforms:** Web global

### 6. [new] Vercel Labs agent-desktop: accessibility-tree computer use without screenshot guessing
**Claim:** agent-desktop 1.0.2 (Oct 31, Rust CLI + C library) lets any shell-capable agent read/operate native desktop apps via OS accessibility tree; headless by default; ~120ms per snapshot; no pointer movement.
- **Evidence:**
  - Reads Finder/Slack/any native app as JSON structured tree; acts by stable element refs
  - "agent-browser, for your whole computer" framing
  - Platforms: Windows (UI Automation), macOS (Accessibility API), Linux (AT-SPI)
  - 4,500+ stars (Nov 1)
  - Built by Lahfir (@mdlahfir) who joined Vercel Labs
  - Extends agent-browser token-efficient approach to full OS
- **Sources:** https://github.com/vercel-labs/agent-desktop/releases/tag/v1.0.2 | https://dev.to/gabrielanhaia/vercels-agent-desktop-lets-coding-agents-click-native-apps-without-moving-your-mouse-38p1 | https://creatorstoolbox.com/blog/vercel-labs-agent-desktop-computer-use-for-coding-agents
- **Platforms:** Web global, GitHub Trending

### 7. [new] Uncut: lossless 7MB Go harness with no context truncation guarantee
**Claim:** Uncut (Nov 1, MIT, Balanov/uncut) is a 7MB static Go binary with 4 tools; never truncates file/command output; errors with exit code 3 instead of partial answers on provider truncation.
- **Evidence:**
  - Single statically-linked Go binary; no runtime or third-party Go deps
  - No TUI, no telemetry; plain stdin/stdout
  - Use case: shell pipelines, CI jobs, containers, agent experiments
  - Discovered Nov 2 (repo ~1 day old at time of discovery)
- **Sources:** https://github.com/Balanov/uncut | https://munderdiffl.in/blog/agent-tools-today-2026-11-02/
- **Platforms:** Web global

### 8. [new] Mika: on-device Android agent with cross-agent MCP handoff
**Claim:** Mika (Kotlin, wangzan101/Mika, 1,500+ stars Oct 31) drives Android apps on a hidden background screen while user keeps their phone; MCP integration lets desktop agents (Claude Code, Codex) hand off tasks to Android device.
- **Evidence:**
  - Built-in desktop-class browser, local Linux sandbox, encrypted on-device memory
  - New (Oct 30): screen handover from browser to AI; pauses when human touches screen
  - MCP: desktop agents can assign tasks to Mika on Android device
  - Android 11+ (basic), 12+ (app automation), 14+ recommended
  - 🇨🇳 CN coverage; Feishu dev workflow integration
- **Sources:** https://github.com/wangzan101/Mika | https://www.opensourceforu.com/2026/11/mika-ai-agent-android-automation/ | https://note.com/simizu_note_ai/n/nbf09b1689e83
- **Platforms:** GitHub Trending, Web global, Web JP 🇯🇵

### 9. [new] LangChain DeepAgents: batteries-included harness with managed beta
**Claim:** LangChain DeepAgents (langchain-ai/deepagents) is a "batteries-included" harness on LangGraph; Python SDK + TypeScript port + terminal coding agent (deepagents-code v0.2.4); Managed Deep Agents public beta launched Oct 7.
- **Evidence:**
  - Ships: write_todos planning, filesystem ops (read/write/edit/ls/glob/grep), shell access (sandboxed), sub-agents (isolated context windows), skills
  - Enterprise skill registries up to 50+ skills per agent
  - Python SDK + deepagents.js (TypeScript) + deepagents-code terminal agent
  - Updated Nov 1, 2026
- **Sources:** https://github.com/langchain-ai/deepagents | https://github.com/langchain-ai/deepagentsjs | https://dev.to/mech_app_ai/deep-agents-how-langchains-batteries-included-harness-wires-sub-agents-filesystem-backends-and-4i2d
- **Platforms:** Web global

### 10. [update] Claude Code v2.1.314–317: subagent effort control, write hardening, idle compaction
**Claim:** New: `CLAUDE_CODE_SUBAGENT_EFFORT` and `CLAUDE_CODE_DISABLE_ULTRATHINK` env vars (v2.1.316); write-blocking outside working dirs; idle compaction for VS Code; Opus 4.8 fast mode removal Nov 30.
- **Evidence:**
  - `CLAUDE_CODE_SUBAGENT_EFFORT`: sets default effort for subagents independently of session effort
  - `CLAUDE_CODE_DISABLE_ULTRATHINK`: prevents the ultrathink keyword from triggering effort boosts
  - `blockWritesOutsideWorkingDirectories`: critical safety for unattended automation
  - Idle compaction: sessions >200K tokens auto-summarize during idle (v2.1.314+)
  - 6 security fixes in v2.1.316: --restricted session write escape, gateway model enforcement, PowerShell hook validation
  - v2.1.317 (Nov 3): MCP server disconnect fix (desktop sessions), cloud task safety checks, cost reporting for admins
  - Opus 4.8 fast mode: deprecated Oct 30; removed Nov 30; after removal → error (not fallback)
  - 🇯🇵 JP coverage: Qiita (NaokiIshimura, picnic, Sidejob) with enterprise gateway focus
- **Sources:** https://dev.classmethod.jp/en/articles/20261031-cc-updates-v2-1-316/ | https://www.gradually.ai/en/changelogs/claude-code/ | https://qiita.com/NaokiIshimura/items/d74fc44a0aa8ee403e21 | https://qiita.com/Sidejob/items/1b17bb4cc959b97cfcfb
- **Platforms:** Web global, Web JP 🇯🇵

### 11. [new] Anthropic Message Threads: 35% latency cut for 500K–1M token sessions
**Claim:** Anthropic launched Messages API message threads public beta (Nov 2); agents send only new messages after initial request; 35% median TTFT reduction for 500K–1M token sessions; token billing unchanged.
- **Evidence:**
  - API: add `thread` parameter + `message-threads-2026-08-12` beta header
  - SDK thread helper handles header, keeps conversation in memory, replays on continuation errors
  - Threads expire 5 min after last request (restart timer on each API response)
  - Available: Claude Platform, AWS, Microsoft Foundry, Google Cloud Anthropic-managed
  - NOT eligible: zero data retention, HIPAA, Token Counting API
  - Already default for most Claude Code users; Claude Code immediately benefits
  - Quote: "threads materially reduce latency and request sizes without changing model billing"
- **Sources:** https://www.unite.ai/anthropic-launches-message-threads-beta-for-long-running-agents/ | https://claude.com/resources/articles/message-threads | https://cellcog.ai/blog/claude-message-threads/
- **Platforms:** Web global

### 12. [update] GitHub Copilot: Fusion GA + Cloud Sessions + MCP Connectors
**Claim:** Copilot Fusion GA (Oct 28, GitHub Universe): per-request multi-model routing (Single/Cascade/Critique); Cloud Sessions: persistent cross-device agent work; 26-service MCP Connectors preview.
- **Evidence:**
  - Copilot Fusion: available on all plans; VS Code, GitHub app, CLI, JetBrains
  - Cloud Sessions (Oct 28): start on phone, continue in VS Code, check on web — same session
  - Automations: self-improving workflows; team can approve/reject suggested improvements
  - MCP Connectors (public preview): Slack, Figma, Notion, Sentry, Linear, Cloudflare, Vercel; single sign-in
  - Fusion quote: "beats Claude Code for half the API cost" (The New Stack, independent claim)
- **Sources:** https://www.unite.ai/github-makes-copilot-fusion-generally-available-at-universe-2026/ | https://thenewstack.io/github-copilot-fusion/ | https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent | https://aiagentstore.ai/ai-agent-news/this-week
- **Platforms:** Web global

### 13. [update] Cursor Agent SDK GA + Origin Marketplace
**Claim:** Cursor Agent SDK GA (Oct 20): agents-as-project-folders, deploy to Cursor or self-hosted infra, GitHub/GitLab/Bitbucket/Slack/webhook triggers; Origin Marketplace: 20+ service integrations.
- **Evidence:**
  - Agent defined as project folder: instructions + tools + skills; deployable code
  - Cloud agents can create shareable interactive canvases (links) (Oct 16)
  - Environments API beta: up to 300 repos, 5x faster loading for large codebases
  - Origin Marketplace: Cloudflare, Linear, Sentry, Socket Security; agents write check runs + PR comments
- **Sources:** https://releases.sh/cursor | https://cursor.com/docs/release-notes
- **Platforms:** Web global

### 14. [new] Android Studio Rabbit 2 BYOA: 40+ ACP agents inside the IDE
**Claim:** Android Studio Rabbit 2 (stable Oct 28) supports Bring Your Own Agent (BYOA) over open Agent Client Protocol (ACP); 40+ agents including Claude Agent, Codex, Antigravity; IDE passes full project graph + build diagnostics to agent.
- **Evidence:**
  - ACP: open protocol; agents get project graph, build diagnostics, Compose Preview, Emulator, Logcat
  - Install from Android Studio marketplace; Settings > Tools > AI > Agents
  - Android CLI plugins released for Claude Code and Codex
  - Agents can run tests, trigger emulator, interpret build errors — without screenshot workarounds
- **Sources:** https://android-developers.googleblog.com/2026/09/build-your-way-use-any-ai-agent-in-android-studio.html | https://dev.to/paullovelace/android-studio-just-opened-to-40-ai-agents-claude-codex-and-antigravity-in-one-ide-explained-28gb | https://aiagentstore.ai/ai-agent-news/this-week
- **Platforms:** Web global

### 15. [update] OpenCode v2.2.3–2.2.5: built-in Claude Agent provider, artifact pipeline
**Claim:** OpenCode 2.2.x (Oct 30–Nov 3) adds built-in Claude Agent provider via CC credentials, experimental artifact pipeline with 4 tools, and persistent terminal PTY sessions.
- **Evidence:**
  - v2.2.3: Claude Agent provider built in (no separate CC install needed); compaction.buffer accepts context %
  - v2.2.4: experimental.artifacts flag → artifact_create/read/update/delete + local static-file provider
  - v2.2.5: MCP stdio >10MiB stays connected; keyboard shortcuts for worktree/shell mode
  - Persistent PTY sessions: scrollback survives restart; synchronized across TUI + desktop windows
- **Sources:** https://opencode.ai/changelog | https://freedom.tech/posts/2026-10-30-opencode-2-2-4/ | https://freedom.tech/posts/2026-10-29-opencode-2-2-1/
- **Platforms:** Web global

### 16. [update] Hermes v0.22.6 / v0.22.0 "Threshold Release"
**Claim:** Hermes v0.22.0 "Threshold Release" (Oct 13): 600-plugin catalog, one-click local model install, guided onboarding, signed packages; v0.22.6 (Nov 2) adds webapp access, per-skill locks, resumable downloads.
- **Evidence:**
  - v0.22.0: app connectors requiring no account; llama.cpp one-click local install; stable SemVer; ~24,200 commits, ~6,080 PRs
  - v0.22.6: ~776 PRs; webapp access; model reset; per-skill locks; resumable downloads in package manager
  - "The Threshold Release" framing: Nous Research positions harness engineering as "the real unlock in 2026"
  - v0.22.5 (Oct 22): pluggable delegation backends, plugin slash commands with options
- **Sources:** https://github.com/NousResearch/hermes-agent/releases | https://hermesatlas.com/guide/
- **Platforms:** Web global

### 17. [new] Malicious CC Extension on Cursor Marketplace: SSH backdoor on ~5,000 machines
**Claim:** Trojaned Claude Code extensions v2.1.312-313 available in Cursor marketplace Oct 29 (2:27 AM–1:35 PM PT); executed on load; planted SSH backdoor; ~5,000 users affected; uninstalling does NOT remove backdoor.
- **Evidence:**
  - Malicious JS loader injected into extension.js; executes immediately on extension load
  - Attacker SSH key added to authorized_keys; reverse tunnel to 134.209.82.225; persistence mechanism; credential exfil
  - Not developed by Anthropic; Anthropic.claude-code namespace on Cursor's marketplace
  - Cursor response: removed extension, shut down entire marketplace for audit, rotated all access keys
  - Remediation: manually remove SSH key + persistence + tunnel processes + rotate all credentials from affected machine
  - Uninstalling extension leaves backdoor in place
- **Sources:** https://www.bleepingcomputer.com/news/security/malicious-claude-code-extension-on-cursor-planted-ssh-backdoors/ | https://thehackernews.com/2026/10/official-claude-code-vs-code-extension.html | https://www.sophos.com/en-us/blog/malicious-claude-code-extension-distributed-through-cursor-marketplace | https://www.helpnetsecurity.com/2026/10/30/claude-code-extension-ssh-backdoor/ | https://www.ox.security/blog/malicious-claude-code-extension-cursor-ssh-backdoor/
- **Platforms:** Web global, Security feeds

### 18. [new] Trigger.dev breach: agent workflow env vars exposed to attacker
**Claim:** Trigger.dev disclosed Nov 1 that an attacker accessed environment variables (API keys, cloud credentials) for a subset of organizations; affects agents running production background jobs.
- **Evidence:**
  - Trigger.dev runs production background jobs + AI agents; env vars include Stripe/Slack/Supabase credentials
  - Exploit blocked; impacted account owners emailed; no public list of affected orgs
  - Pattern: agent workflow orchestrators are high-value targets (credentials span all connected services)
  - Pattern with Cursor CC extension attack: agent harness supply chain is under active attack Nov 2026
- **Sources:** https://trigger.dev/blog/security-incident-nov-2026 | https://www.scworld.com/brief/trigger-dev-discloses-security-incident-involving-exposed-environment-variables | https://www.theregister.com/security/2026/11/02/thieves-pilfer-environment-variables-from-trigger-ai-workflow-tool/5306998
- **Platforms:** Web global, Security feeds

---

**Still true** (prior threads with no new facts this week):
- `opencode-2-shared-service`: OpenCode 2.0 background service architecture stable; 2.2.x builds on it [ongoing]
- `cc-mcp-tasks-elicitations`: MCP Tasks/Elicitations early access still rolling out [ongoing]
- `claude-duet-proactive-agent`: Claude Duet waitlist still active [ongoing]
- `aaif-agent-skills-four-projects`: AAIF 10-project foundation stable [ongoing]
- `entire-agent-native-git-forge`: Entire forge operating [ongoing]
- `t3-code-harness-control-surface`: T3 Code 38K+ stars, continued growth [ongoing]
- `agent-relay-agent-communication-layer`: Agent Relay available [ongoing]
- `cccskills-jp-marketplace`: cccskills operational [ongoing]
- `openvlharness-visual-agent`: OpenVLHarness paper continuing citations [ongoing]
- `agent-bom-governance-layer`: ABOM tooling in progress [ongoing]
- `hermes-agent-self-improving`: now updated above as `hermes-agent-self-improving` [see finding 16]
- `claude-code-doctor-skill-hygiene`: see finding 10 [update]
- `anthropic-managed-agents-mcp-tunnels`: see finding 11 [update]
- `extension-economy-explosion`: ecosystem growing; now T3 Code 38K, Orkas new entrant [update in findings above]
- `sep-2640-mcp-skills-final`: SEP-2640 in production; Copilot MCP Connectors adds 26 services [update]
- `google-harness2-recursive`: Harness² ongoing citations [ongoing]
- `reason-network-multi-pc-p2p`: Reason Network operating [ongoing]
- `reticle-agent-self-verify`: Reticle available [ongoing]
- `hy-memory-tencent-dual-system`: Hy Memory operational [ongoing]
- `opencode-console-breach`: prior Oct breach resolved; unrelated to CC Cursor extension attack Nov 2026 [ongoing]
- `aoki-infostealer-coding-agent-creds`: ongoing threat; compounded by Nov 2026 supply chain attacks [ongoing]
- `langflow-mcp-cve-stdio`: CVE-2026-105740 still unpatched on affected versions [ongoing]
- `leanrea-8kb-skill-replacement`: LeanREA available [ongoing]
- `skills-hub-v1-desktop-app`: Skills Hub v1 operating [ongoing]
- `anthropics-claude-plugins-official`: plugin ecosystem growing [ongoing]
- `cursor-plugins-marketplace-official`: Cursor plugins + Origin Marketplace update [see finding 13]
- `longhorizon-harness-update`: LongHorizon-Harness operating [ongoing]
- `harness-context-tax-problem`: Factory Droid Script Mode + Message Threads address same tax [update in findings 5, 11]
- `agentskills-open-standard`: AAIF standard stable [ongoing]
- `skills-over-mcp-wg-sep2640`: Copilot MCP Connectors (26 services) extends SEP-2640 reach [update]
- `obra-superpowers-skills`: obra/superpowers ~305K stars [ongoing]
- `self-harness-auto-optimization`: Harness² ongoing [ongoing]
- `harness-engineering-paradigm`: JP "harness year" consensus reaffirmed [ongoing]
- `antigravity-gemini-cli-successor`: Antigravity in Android Studio BYOA [update]
- `vscode-1138-agent-host-protocol`: VS Code AHP stable [ongoing]
- `github-copilot-skills-mcp-ga`: see finding 12 [update]
- `codex-cli-0155-voice-touchid`: Codex in Android Studio BYOA [update]
- `devin-desktop-windsurf-rebrand`: Devin Desktop operating [ongoing]
- `workday-agent-harness-ga`: Workday Harness operating [ongoing]
- `harness-io-acquires-cosmos`: Cosmos in Harness.io Oct 150-features ship [update]
- `corbenic-galahad-memory`: Galahad operating [ongoing]
- `vercel-labs-skills-universal-cli`: vercel-labs/skills + agent-desktop now both Vercel Labs [update in finding 6]
- `lexmount-moli-rust-browser`: lexmount/moli operating [ongoing]
- `cloudflare-sep2640-production-server`: Cloudflare MCP server operating [ongoing]
- `claude-haiku-5-5-subagent-economics`: Haiku 5.5 default subagent [ongoing]
- `openhuman-rust-harness`: OpenHuman operating [ongoing]
- `nanomuse-cross-device-agent`: nanoMuse operating [ongoing]
- `jotbus-e2ee-cross-agent-scratchpad`: Jotbus operating [ongoing]
- `cmux-ghostty-agent-terminal`: cmux operating [ongoing]
- `agency-agents-harness-library`: agency-agents 162.7K+ stars [ongoing]
- `trycua-computer-use-fleet`: trycua/cua operating [ongoing]
- `docker-agent-yaml-runtime`: docker/docker-agent operating [ongoing]
- `pinrail-human-in-loop-inbox`: Pinrail operating [ongoing]
- `pi-minimal-agent-harness`: Pi operating [ongoing]
- `offrun-multi-agent-workspace`: Offrun operating [ongoing]
- `headlong-microharness-bash`: Headlong operating [ongoing]
- `television-agent-gui-sidecar`: Television operating [ongoing]
- `skills-security-prompt-injection-36pct`: threat compounded by Cursor backdoor attack [update in finding 17]
- `deepseek-harness-team`: DeepSeek dsh-superagent extends the ecosystem [see finding 1]
- `nvidia-openshell-agent-runtime`: OpenShell operating [ongoing]
- `weave-router-model-routing`: Weave Router operating [ongoing]
- `mattpocock-skills-135k`: ~307K stars (Zenn analysis) [ongoing]
- `openai-devday-2026-gpt61-dots`: Codex in Android Studio BYOA [update]
- `cn-miit-claude-code-notice`: MIIT stance unchanged; CN devs favor OpenCode [ongoing]
- `claude-sonnet-5-5`: Sonnet 5.5 in Copilot Fusion routing [ongoing]
- `salesforce-enterprise-ai-harness`: Salesforce Harness FY28 rollout [ongoing]
- `openrig-multi-agent-harness`: openrig operating [ongoing]
- `hindsight-standalone-memory`: hindsight operating [ongoing]
- `jauvex-voice-multi-agent`: jauvex operating [ongoing]
- `claude-opus-5-5`: Opus 5.5 recommended migration target from Opus 4.8 fast mode [update]
- `google-ax-agentic-runtime`: Google AX operating [ongoing]
- `cursor-projects-self-hosted-machines`: Cursor Agent SDK now GA [update in finding 13]
- `univer-office-harness`: Univer operating [ongoing]
- `hkuds-nanobot-personal-agent`: nanobot operating [ongoing]
- `gitspawn-class-vulnerability`: 4/8 GitSpawn vulns still unpatched; CC Cursor backdoor adds new vector [ongoing]
- `layered-oss-stack-over-single-framework`: Android Studio ACP + Copilot Fusion extend layering [update]
- `gpt6-astra-provider-adapter-harness`: Codex in Android Studio BYOA [update]
- `paperclip-multi-agent-company-os`: paperclip operating [ongoing]
- `aws-strands-harness`: Strands operating [ongoing]
- `claude-code-projects-parallel-threads`: CC Projects operating [ongoing]
- `openai-agents-api-beta`: Codex GA [ongoing]
- `vscode-1137-agent-host-protocol`: VS Code AHP + Copilot Fusion [update]
- `reinventing-ai-employee-packages`: gstack operating [ongoing]
- `builder-agent-native`: BuilderIO operating [ongoing]
- `beam-cli-harness-observer`: Beam CLI operating [ongoing]
- `meta-muse-code`: Meta Muse Code operating [ongoing]
- `environment-architect-new-role`: JP harness engineering paradigm continuing [ongoing]
- `addy-osmani-agent-skills`: ~110K+ stars [ongoing]
- `harness-internal-external-disambiguation`: JP community distinction active [ongoing]
- `copilot-runtime-rust-rewrite`: Copilot v1.0.106-2 session resume [update]
- `codex-open-platform-harness`: Codex in Android Studio BYOA [update]
- `harness-io-agent-ready-scm`: Harness.io 150 features shipped [update]
- `colibri-lumabri-moe-inference`: Colibri operating [ongoing]
- `omarchy-herdr-agentic-linux`: herdr operating [ongoing]
- `agensi-skill-marketplace`: Agensi operating [ongoing]
- `kilo-code-anaconda`: Kilo Code operating [ongoing]
- `orca-ade-parallel-fleet`: Orca v1.4.246 (Nov 2) [update]
- `ponytail-laziest-dev-skill`: ~154K stars [ongoing]
- `trueforge-open-source-harness`: TrueForge operating [ongoing]
- `aws-kiro-crew-open-source`: Kiro Crew operating [ongoing]
- `hiddenlayer-agent-harness-security`: HiddenLayer operating [ongoing]
- `longhorizon-harness-amap`: LongHorizon operating [ongoing]
- `caspian-talk-to-human-tool`: Caspian operating [ongoing]
- `kubell-whitelist-harness-tools`: Kubell operating [ongoing]
- `block-berd-desktop-workspace`: Berd operating [ongoing]
- `loopx-long-horizon-control-plane`: LoopX operating [ongoing]
- `cloudflare-computer-agent-runtime`: @cloudflare/computer operating [ongoing]
- `cursor-google-workspace-plugins`: Cursor Google Workspace plugins operating [ongoing]
- `huzzah-pseudocode-editor`: Huzzah operating [ongoing]
- `onecli-yc-s26-credential-gateway`: OneCLI operating [ongoing; CC extension backdoor attack reinforces value]
- `harnessrouter-uhp-open-standard`: UHP operating [ongoing]
- `flue-2-react-hooks-harness`: Flue 2.0 operating [ongoing]
- `hax-c-minimalist-agent`: Hax operating [ongoing]
- `copilot-autofix-dual-ai-security`: Copilot Autofix operating [ongoing]
- `bullet-yc-s26-coding-agent`: Bullet operating [ongoing]
- `book-to-skill-pdf-to-skill`: book-to-skill operating [ongoing]
- `prime-agent-rlm`: Prime Agent operating [ongoing]
- `aq-multiplayer-harness`: AQ operating [ongoing]
- `oh-my-agent`: oh-my-agent operating [ongoing]
- `autoharness-deepmind`: AutoHarness operating [ongoing]
- `hoplite-yc-s26-cloud-deploy`: Hoplite operating [ongoing]
- `vercel-ai-sdk-harnessagent`: Vercel AI SDK HarnessAgent operating [ongoing]
- `copilot-studio-ga-harness-billing`: Copilot Studio operating [ongoing]
- `microsoft-agent-governance-toolkit`: Microsoft toolkit operating [ongoing]
- `tinyagents-rust-recursive`: TinyAgents operating [ongoing]
- `sprocket-hardware-software-agent`: Sprocket operating [ongoing]
- `gambit-reliable-agent-harness`: Gambit operating [ongoing]
- `nlah-natural-language-harnesses`: NLAH operating [ongoing]
- `claude-tag-slack-agent`: Claude Tag Slack operating [ongoing]
- `mimo-code-xiaomi`: MiMo Code operating [ongoing]
- `ecc-cross-harness-os`: ECC ~272K stars [ongoing]
- `kimi-code-moonshot`: Kimi Code operating [ongoing]
- `runtime-yc-p26`: Runtime operating [ongoing]
- `noclick-always-on`: NoClick operating [ongoing]
- `nyx-offensive-testing`: Nyx operating [ongoing]
- `agentguard-security-tool`: AgentGuard relevant given CC extension backdoor [ongoing]
- `yc-qm-multiplayer-harness`: YC QM operating [ongoing]
- `jadepuffer-agentic-security`: JADEPUFFER operating [ongoing]
- `grok-build-xai-rust-harness`: Grok-Build operating [ongoing]
- `openharness-hkuds`: OpenHarness operating [ongoing]
- `claw-code-claude-rewrite`: Claw Code ~195K stars [ongoing]
- `metaharness-scaffold-generator`: ruvnet operating [ongoing]
- `deerflow-superagent-harness`: DeerFlow 2.0 operating [ongoing]
- `zot-go-coding-harness`: Zot operating [ongoing]
- `omp-omo-pi-derivatives`: oh-my-pi/oh-my-openagent operating [ongoing]
- `yorishiro-presence-harness`: Yorishiro operating [ongoing]
- `letta-agent-file-format`: Letta .af operating [ongoing]
- `macos-harness-proving-ground`: macOS proving ground continuing [ongoing]
- `warp-oz-multi-harness`: Warp Oz operating [ongoing]
- `mozilla-otari-llm-gateway`: Otari operating [ongoing]
- `statewright-guardrails`: Statewright operating [ongoing]
- `headroom-token-compression`: Headroom operating [ongoing]
- `nvidia-skillspector-security`: SkillSpector operating; relevant given CC backdoor [ongoing]
- `cli-anything-hkuds`: CLI-Anything operating [ongoing]
- `forge-acp-universal-cli`: Forge ACP operating [ongoing]
- `block-buzz-workspace`: Block Buzz v1.0 due mid-Nov [ongoing]
- `zcode-zhihu-agent-ide`: ZCode operating [ongoing]
- `devin-fusion-multimodel`: Devin Fusion operating [ongoing]
- `ambiance-unix-harness`: Ambiance operating [ongoing]
- `kore-artemis-abl`: Kore Artemis operating [ongoing]
- `open-agent-passport-oap`: OAP operating [ongoing]
- `code-as-agent-harness-paper`: arXiv:2605.18747 ongoing citations [ongoing]
- `tilde-harness-sdk`: Tilde operating [ongoing]
- `kiro-aws-spec-driven`: AWS Kiro operating [ongoing]
- `cursor-spacex-acquisition`: Cursor acquired by SpaceX Aug 14 [ongoing]
- `munder-difflin-office-of-clones`: Munder Difflin desktop app active [ongoing]
- `aura-mezmo-sre-harness`: AURA operating [ongoing]
- `jetstream-clearance-zero-trust`: JetStream operating [ongoing]
- `tenable-cyberagents-exchange-inspector`: Tenable operating [ongoing]
- `sonar-vortex-inside-loop`: Sonar Vortex operating [ongoing]
- `devspace-minimal-mcp-harness`: DevSpace operating [ongoing]
- `accuknox-agentz-enterprise`: AgentZ operating [ongoing]
- `gstack-virtual-engineering-team`: gstack 132K stars [ongoing]
- `graphify-codebase-knowledge-graph`: Graphify-Labs operating [ongoing]
- `atlas-source-control-agents`: atlas operating [ongoing]
- `nodeterm-canvas-terminal-manager`: nodeterm operating [ongoing]
- `paseo-multi-provider-orchestration`: Paseo operating [ongoing]
- `openchamber-ade-opencode`: OpenChamber operating [ongoing]
- `magnitude-local-inference-server`: magnitude operating [ongoing]
- `opencode-v2-rewrite`: OpenCode 2.0/2.2.x [see finding 15]
- `context-mode-tool-output-compression`: context-mode operating [ongoing]
- `openclaude-community-agent`: openclaude 32.7K stars [ongoing]
- `ruflo-meta-harness-swarm`: ruflo operating [ongoing]
- `vscode-1136-agent-merge`: superseded by AHP [ongoing]
- `air-security-agent-firewall`: AIR Security operating [ongoing]
- `watcher-apolloresearch-monitoring`: Watcher Live operating [ongoing]
- `harness-enterprise-governance-gap`: gap persists; CC extension supply-chain attack validates it [ongoing]
- `harnessx-composable-foundry`: HarnessX operating [ongoing]
- `tencentdb-agent-memory`: TencentDB operating [ongoing]
- `penguinharness-self-improving`: PenguinHarness operating [ongoing]
- `ante-antigma-single-binary`: Ante operating [ongoing]
- `microsoft-intelligent-terminal`: intelligent-terminal operating [ongoing]
- `dexto-yaml-agent-harness`: Dexto operating [ongoing]
- `aidlc-workflows-v211-aws`: aidlc-workflows operating [ongoing]
- `omnigent-meta-harness`: Omnigent operating [ongoing]
- `morluto-rea-reverse-engineering-mcp`: REA 6.6.0 operating [ongoing]
- `skills-hub-v1-desktop-app`: Skills Hub operating [ongoing]
- `reason-agent-1-1-beats-codex`: Reason Agent 1.1 operating [ongoing]
- `reason-network-multi-pc-p2p`: Reason Network operating [ongoing]
- `mcp-security-nsa-supply-chain`: CC Cursor backdoor + Trigger.dev breach compound [see findings 17, 18]
- `harmony-harness-google-cmu`: Harmony Harness ongoing citations [ongoing]
- `openclaw-gateway-harness`: OpenClaw v2026.10.9-10 security patches [update]

---

## Cross-Source Patterns

### Pattern 1: Supply Chain Under Active Attack
- **Signal:** Two independent attacks in Nov 2026 week: (a) Trojaned CC extension via Cursor marketplace; (b) Trigger.dev env var breach exposing agent credentials.
- **Platforms:** Web global, Security feeds, GitHub
- **Key quote:** "Trusted Tool, Malicious Build: What the Trojanized Claude Code Extension Means for Developer Endpoints" (Morphisec)
- Both attacks exploit the same surface: the agent harness supply chain is a single point of compromise for developer machines + all downstream credentials.

### Pattern 2: Harness-Designed Coordination > Frontier Model Raw Power
- **Signal:** Memdoor (5× Qwen3.8-27B) beats Fable 5 on LiveCodeBench Hard; Factory Droid 1.0 claims 17% fewer tokens vs Claude Code on same tasks; Prospero gets HN praise for 5MB efficiency vs "slopware."
- **Platforms:** HN, Web global
- **Key quote:** "five small models on one programming problem" (Memdoor README) | "FIVE megabytes. Wow. What are we _doing_ everywhere else." (HN on Prospero)
- Three separate projects in the same week demonstrating harness design as a performance lever independent of model choice.

### Pattern 3: Proactive / Ambient Agent Mode Emerging
- **Signal:** DeepSeek dsh-superagent (monitors group chats without being summoned); Mika (operates Android apps in background while user uses phone); Copilot Automations (self-improving workflows).
- **Platforms:** Web global, Web CN 🇨🇳, Web JP 🇯🇵
- **Key quote:** "Take as little human attention as possible, and give as much value as possible" (DeepSeek dsh-superagent design doc)
- Convergence across three independent products toward ambient/proactive execution model.

### Pattern 4: Latency as First-Class Harness Feature
- **Signal:** Anthropic Message Threads (35% TTFT reduction for 1M-token sessions); Factory Droid Script Mode (hundreds of tool calls in one model request); Memdoor file-only comms (eliminates inter-agent message overhead).
- **Platforms:** Web global
- Message passing overhead and round-trip latency are now explicit optimization targets in harness design.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (skeeto) | Prospero: a new coding harness for a more civilized age | 207 | 136 | "FIVE megabytes. Wow. What are we _doing_ everywhere else." | https://news.ycombinator.com/item?id=50315226 |
| (PferdOne) | Memdoor: five Qwen3.8-27B models tie Fable 5 on LiveCodeBench Hard | 430+ | ~80 | "five small models on one programming problem" | https://daily.dev/posts/memdoor-a-team-of-5-qwen3-8-27b-models-beats-fable-5-on-livecodebench-hard-ghdvz1p3j |
| (Orkas-AI) | Orkas: local-first AI team desktop | 180+ | — | "a Commander turns your goal into to-dos" | https://github.com/Orkas-AI/Orkas |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Bloomberg | https://www.bloomberg.com/news/articles/2026-11-01/deepseek-drops-enhanced-coding-agent-with-aim-to-rival-anthropic | dsh-superagent announcement |
| 🌐 | munderdiffl.in (Nov 2) | https://munderdiffl.in/blog/agent-tools-today-2026-11-02/ | Memdoor, Uncut, dsh-superagent daily digest |
| 🌐 | munderdiffl.in (Nov 1) | https://munderdiffl.in/blog/agent-tools-today-2026-11-01/ | Prospero, Orkas, agent-desktop 1.0.2 |
| 🌐 | munderdiffl.in (Oct 31) | https://munderdiffl.in/blog/agent-tools-today-2026-10-31/ | CC 2.1.316, CC extension backdoor, T3 Code |
| 🌐 | aiagentstore.ai | https://aiagentstore.ai/ai-agent-news/this-week | Copilot Cloud Sessions, Message Threads, Android Studio BYOA |
| 🌐 | nullprogram.com | https://nullprogram.com/blog/2026/10/31/ | Prospero original post |
| 🌐 | dev.classmethod.jp | https://dev.classmethod.jp/en/articles/20261031-cc-updates-v2-1-316/ | CC v2.1.316 deep dive |
| 🌐 | gradually.ai (CC) | https://www.gradually.ai/en/changelogs/claude-code/ | CC v2.1.314-317 changelog |
| 🌐 | gradually.ai (OC) | https://www.gradually.ai/en/changelogs/openclaw/ | OpenClaw Oct changelog |
| 🌐 | cellcog.ai (harnesses) | https://cellcog.ai/blog/best-ai-agent-harnesses/ | Nov 2026 harness rankings |
| 🌐 | marktechpost.com | https://www.marktechpost.com/2026/10/31/factory-droid-1-0-frontier-harness/ | Factory Droid 1.0 analysis |
| 🌐 | unite.ai (threads) | https://www.unite.ai/anthropic-launches-message-threads-beta-for-long-running-agents/ | Message Threads beta |
| 🌐 | thenewstack.io | https://thenewstack.io/github-copilot-fusion/ | Copilot Fusion technical analysis |
| 🌐 | bleepingcomputer | https://www.bleepingcomputer.com/news/security/malicious-claude-code-extension-on-cursor-planted-ssh-backdoors/ | CC backdoor |
| 🌐 | thehackernews | https://thehackernews.com/2026/10/official-claude-code-vs-code-extension.html | CC trojanized |
| 🌐 | sophos | https://www.sophos.com/en-us/blog/malicious-claude-code-extension-distributed-through-cursor-marketplace | Supply chain analysis |
| 🌐 | helpnetsecurity | https://www.helpnetsecurity.com/2026/10/30/claude-code-extension-ssh-backdoor/ | SSH backdoor |
| 🌐 | trigger.dev | https://trigger.dev/blog/security-incident-nov-2026 | Env var breach disclosure |
| 🌐 | theregister | https://www.theregister.com/security/2026/11/02/thieves-pilfer-environment-variables-from-trigger-ai-workflow-tool/5306998 | Trigger.dev breach |
| 🌐 | android-developers | https://android-developers.googleblog.com/2026/09/build-your-way-use-any-ai-agent-in-android-studio.html | BYOA ACP |
| 🌐 | coddykit.com | https://www.coddykit.com/pages/blog-detail?id=5130012 | GitHub Trending Nov coverage |
| 🌐 | releases.sh/cursor | https://releases.sh/cursor | Cursor Agent SDK GA changelog |
| 🌐 | github.com/NousResearch | https://github.com/NousResearch/hermes-agent/releases | Hermes releases |
| 🌐 | hermesatlas.com | https://hermesatlas.com/guide/ | Hermes guide |
| 🌐 | opencode.ai | https://opencode.ai/changelog | OpenCode changelog |
| 🌐 | freedom.tech | https://freedom.tech/posts/2026-10-30-opencode-2-2-4/ | OpenCode 2.2.4 |
| 🌐 | harness.io | https://www.harness.io/blog/shipped-in-october-2026 | Harness 150 features |
| 🌐 | langchain-ai/deepagents | https://github.com/langchain-ai/deepagents | DeepAgents repo |
| 🌐 | o16g.com | https://o16g.com/updates/2026-11-01-0601/ | Containment gap analysis |
| 🌐 | aiweekly.co | https://aiweekly.co/alerts/memdoors-five-qwen38-27b-team-beats-fable-5-at-livecodebench | Memdoor benchmark |
| 🇯🇵 | Qiita (NaokiIshimura) | https://qiita.com/NaokiIshimura/items/d74fc44a0aa8ee403e21 | 5 key CC updates JP analysis |
| 🇯🇵 | Qiita (miruky) | https://qiita.com/miruky/items/32314a0d9eb8c154dc95 | MCP vs Skills comparison |
| 🇯🇵 | Qiita (picnic) | https://qiita.com/picnic/items/ecdeca5775da6348c87b | Opus 4.8 migration |
| 🇯🇵 | Qiita (Sidejob) | https://qiita.com/Sidejob/items/1b17bb4cc959b97cfcfb | Enterprise gateway operators guide |
| 🇯🇵 | Zenn (tabayashi) | https://zenn.dev/tabayashi/articles/github-2026-stars-agent-harness | 2026 top repos analysis |
| 🇯🇵 | note (simizu_note_ai) | https://note.com/simizu_note_ai/n/nbf09b1689e83 | Mika + dsh-superagent JP |
| 🇨🇳 | TechNode CN | https://cn.technode.com/post/2026-11-02/deepseek-dsh-superagent-coding-agent-prototype/ | dsh-superagent CN coverage |
| 🇨🇳 | Dataconomy CN | https://cn.dataconomy.com/2026/11/02/deepseek-发布开源-dsh-superagent-编程智能体/ | dsh-superagent CN |
| 🇨🇳 | Cnblogs (AI-Frontiers) | https://www.cnblogs.com/aifrontiers/p/19692571 | MCP/Skills/OpenClaw CN guide |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2037210736296998486 | CN coding tool rankings |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded by scope)
├─ 🔵 X: 0 posts (excluded by scope)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 stories │ 817+ points │ 210+ comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 43 pages │ 🇯🇵 6 │ 🇨🇳 5
└─ 🗣️ Top voices: skeeto (Prospero), guregodevo (Memdoor), Orkas-AI, DeepSeek Harness team
```

---

## Out of Scope but Notable

- **THU-MAIC/OpenMAIC** (42,318 stars): multi-agent classroom harness (AI teachers + AI classmates + whiteboard + TTS); trending GitHub Nov 1–3. Might belong to `ai-software-factory` if it gains enterprise traction, but its multi-agent coordination architecture is genuinely novel. https://github.com/THU-MAIC/OpenMAIC
- **Snowflake Cortex `thinking_effort` + `instructions.system` + `stage_mounts`** (Oct 28): reasoning depth control + safe constraint injection + versioned data access for agents — moves Cortex closer to a full harness API surface. Belongs to `ai-software-factory` but notable harness API evolution. https://aiagentstore.ai/ai-agent-news/this-week
- **Akamai Inference + Agent Sandbox (Beta)**: managed model-serving at edge with isolated runtime + default outbound blocks. Edge inference harness layer. Belongs to `ai-software-factory`/infra. https://aiagentstore.ai/ai-agent-news/this-week

---

## Data Gaps

- **Reddit / X / Bluesky:** excluded per topic scope; bluesky=OK per SOURCE HEALTH but no agent-harness content surfaced
- **YouTube / TikTok / Instagram / Polymarket:** not checked; unlikely to add material here
- **DuckDuckGo HTML endpoint (JP + CN):** blocked by CAPTCHA; fell back to native-language WebSearch — likely missed some Qiita/Zenn/CSDN articles indexed only via DuckDuckGo
- **eguweb.jp/ai/81683/:** HTTP 403; content inferred from search snippet only
- **CSDN/blog.csdn.net/aidoudoulong:** connection reset; DeepSeek dsh-superagent CN coverage partial
- **Juejin:** JS-rendered; content not extractable via WebFetch; search snippets used
- **Releasebot full version history:** only checked for CC, OpenClaw; Codex CLI Nov updates not independently verified
- **Coverage estimate:** ~75% — English and JP passes solid; CN pass limited by site access issues; no social platforms searched

---

## Key Quotes

> "FIVE megabytes. Wow. What are we _doing_ everywhere else." — HN commenter on Prospero ([link](https://news.ycombinator.com/item?id=50315226))

> "In the current era of slopware...this is giving me damn near an emotional reaction." — HN commenter on Prospero ([link](https://news.ycombinator.com/item?id=50315226))

> "Take as little human attention as possible, and give as much value as possible." — DeepSeek dsh-superagent design doc ([link](https://devops.com/deepseek-wants-coding-agents-to-stop-waiting-for-instructions))

> "five small models on one programming problem" — Memdoor README, describing 5×Qwen3.8-27B beating Fable 5 ([link](https://github.com/guregodevo/memdoor))

> "threads materially reduce latency and request sizes without changing model billing" — Anthropic on Message Threads ([link](https://claude.com/resources/articles/message-threads))

> "Uninstalling the extension leaves the backdoor in place" — BleepingComputer on Cursor CC extension attack ([link](https://www.bleepingcomputer.com/news/security/malicious-claude-code-extension-on-cursor-planted-ssh-backdoors/))

> "2025年はエージェントの年、2026年はハーネスの年" ("2025 was the year of agents; 2026 is the year of harnesses") — JP community consensus on Qiita/Zenn ([link](https://qiita.com/miruky/items/32314a0d9eb8c154dc95))

> "The 30 most-starred repositories created in 2026 were almost entirely agent harnesses" — Zenn (tabayashi) GitHub stars analysis ([link](https://zenn.dev/tabayashi/articles/github-2026-stars-agent-harness))

> "beats Claude Code for half the API cost" — The New Stack on Copilot Fusion ([link](https://thenewstack.io/github-copilot-fusion/))
