# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-03
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub Trending

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 12 threads | ~1,400+ points, ~650+ comments | Several Show HN / Launch HN; QM top thread (665 pts) |
| YouTube | — | — | Not accessed this run |
| X/Twitter | — | — | Not accessed |
| Reddit | — | — | Not accessed |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | — | — | MCP Sky feed identified; direct post retrieval not performed |
| Polymarket | — | — | No markets on this topic |
| Web (global) | ~85 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~10 pages | — | 🇯🇵 Qiita (3+), Zenn (2+), note (1), Hatena (2+), Speakerdeck (1) |
| Web (China) | ~10 pages | — | 🇨🇳 Zhihu (3+), CSDN (4+), Toutiao (1), Juejin (1), Aliyun (1) |

---

## Synthesized Findings

### 1. [new] Claude Tag: Anthropic Deploys Persistent Multiplayer Slack Agent, Retires Legacy App Today

**Why this is [new]:** Not in prior state; deploys today (August 3, 2026). Claude Tag announced June 23, 2026 — replacing the original Claude in Slack app on all Team and Enterprise plans starting today with a fundamentally different architecture.

Claude Tag is not an upgraded chatbot; it is a **persistent AI agent per channel** with distinct design choices: one Claude identity per Slack channel shared across all members; **ambient mode** (monitors and acts without being @-tagged); asynchronous multi-step tasks that run for hours or days; and scoped identities per function with isolated tools and memory. The identity belongs to the channel, not to individual users — making it closer to a team member than a per-user assistant.

Governance controls for IT teams: private channels are off by default; monthly token spend limits at org and channel level; full audit logs of every action with the requesting user stamped. Enterprise customers receive $25,000 in launch credits (expires Sept 1); Team customers (10+ paid seats) receive $2,500.

Broader significance: this is Anthropic's bet on ambient agentic presence in the collaboration layer — the agent watches, learns shared context, and acts without explicit invocation, a pattern previously seen only in experimental systems.

🌐 Sources: https://www.anthropic.com/news/introducing-claude-tag · https://venturebeat.com/technology/anthropic-launches-claude-tag-replacing-its-slack-app-with-a-persistent-ai-teammate-that-learns-monitors-and-works-autonomously · https://fortune.com/2026/06/23/anthropic-claude-tag-virtual-employee-tool-slack/ · https://www.beri.net/article/anthropic-claude-tag-slack-enterprise-agent-it-guide-2026 · https://www.mindstudio.ai/blog/claude-tag-slack-enterprise-ai-agent · https://enterprisedna.co/resources/news/anthropic-claude-tag-slack-enterprise-2026/ · https://www.techrepublic.com/article/news-anthropic-claude-tag-ai-agent-slack/

---

### 2. [new] MiMo Code: Xiaomi Open-Sources Coding Agent That Claims to Beat Claude Code on 200-Step Tasks

**Why this is [new]:** Not in prior state. First Chinese hardware OEM to ship a competitive open-source coding agent harness.

Xiaomi released MiMo Code V0.1.0 on June 10, 2026 (MIT license) and it has reached **12.6k GitHub stars** with a major HN post at **557 points / 315 comments**. The harness is a fork of OpenCode (Anomaly/SST) with substantial architectural additions:

- **Three agent modes** switchable via Tab: `build` (immediate execution), `plan` (review-then-go), `compose` (specs-driven, closest to Kiro)
- **Persistent memory via SQLite FTS5** across sessions: project knowledge base, conversation checkpoints, task progress trees
- **Subagent orchestration** with parallel execution
- **Dream & Distill** self-improvement features (model refines its own task approach based on session outcomes)
- Bundled model: MiMo-V2.5 free during limited period (claimed comparable to Claude Sonnet 4.6); also supports DeepSeek, Kimi, GLM

Xiaomi's headline claim — that MiMo Code outperforms Claude Code on ultra-long 200+ step agentic tasks — was debated on HN. The top discussion theme was not the features but the broader competitive narrative: "Chinese models now match or exceed Western alternatives at a fraction of the cost" (multiple HN commenters). Privacy concerns about Chinese company telemetry were also flagged.

🇨🇳 The Chinese tech press (CSDN, Toutiao) covers this as validation of the Chinese AI stack catching up; the broader Chinese developer community views MiMo Code alongside ZCode and DeerFlow as evidence that the model+harness stack no longer requires Western infrastructure.

🌐 Sources: https://github.com/XiaomiMiMo/MiMo-Code · https://news.ycombinator.com/item?id=48490826 · https://mimo.mi.com/docs/en-US/news/latest/mimocode · https://www.developer-tech.com/news/xiaomi-mimo-code-executes-200-step-agentic-developer-workflows/ · https://www.xiaomi-mimo-ai.com/blog/mimo-code-ai-coding-agent.html · https://mimo.xiaomi.com/blog/mimo-code-long-horizon · https://www.llmreference.com/agents/mimo-code
🇨🇳 Sources: https://mcp.csdn.net/6a3a576410ee7a33f28146b0.html · https://www.cnblogs.com/aifrontiers/p/19652950

---

### 3. [new] ECC v2: 237k-Star Cross-Harness Operating System Ships Plan Canvas and Kimi Code Support

**Why this is [new]:** Not in prior state. At 237k stars, ECC is one of the largest agent infrastructure projects and represents a distinct architectural bet: a single install that makes multiple harnesses behave coherently.

ECC (Everything Coding Collective, `affaan-m/ECC`, MIT, 237k stars / 36.1k forks / 268 contributors) shipped v2.0.0 in June 2026 and v2.1 more recently, adding:
- **Plan Canvas**: browser UI for collaborative plan annotation before code runs — teams review and annotate the plan, agents see the feedback
- **Kimi Code native support**: ECC now treats Kimi Code as a first-class harness alongside Claude Code, Cursor, Codex, OpenCode, Gemini, Zed, Copilot (7 harnesses total)
- **Itô GPU self-hosted compute**: plug in your own GPU cluster for inference instead of hosted providers

What ECC ships as an "OS": 67 specialized agents, 281 reusable skills, 94 slash commands, hooks, memory systems (Memory Vault for cross-harness context), and AgentShield (security scanner for agent configs). The control-plane substrate provides harness-neutral session adapters (`ecc.session.v1`) and a normalized MCP server config view across harnesses with fragmentation/drift detection and secret redaction (`ecc.mcp.v1`).

The architectural thesis: ECC is not a competitor to individual harnesses but a coordination layer that makes them interoperable. Teams avoid re-configuring skills, memory, and security policies each time they switch between harnesses.

🌐 Sources: https://github.com/affaan-m/ecc · https://github.com/affaan-m/ECC/releases/tag/v2.0.0 · https://www.augmentcode.com/learn/ecc-v2-cross-harness-agent-system · https://www.techtimes.com/articles/320269/20260713/agent-harness-ecc-tops-228k-stars-free-tool-turns-claude-code-full-dev-team.htm · https://multiwaresolutions.com/blog/ecc-agent-harness-system-2026 · https://pyshine.com/ECC-Everything-Claude-Code-Agentic-Operator-System/

---

### 4. [new] Cursor 3.11: Side Chats, Cloud Agent Hooks, and Transcript Search (July 10)

**Why this is [new]:** Not in prior state. Cursor 3.11 represents a meaningful architectural shift beyond autocomplete: parallel agent conversations and hook-based loop control.

Released July 10, 2026, Cursor 3.11 ships four interconnected features:

**Side Chats** (`/side` or `/btw`): durable, parallel agent conversations that run alongside the main thread. Each side chat is a full agent session; users can @-mention any side chat to pull its context into the main conversation. Default mode: read/search/answer (non-destructive). Enables asking "why did you do X?" in parallel without interrupting the primary agent.

**Agent Transcript Search**: Cmd+K in Agents Window searches actual message content (not just conversation metadata) across a local index. Handles thousands of conversations with snappy performance; in-conversation search via Cmd+F with match counters.

**Cloud Agent Hooks**: `beforeSubmitPrompt`, `afterAgentResponse`, `afterAgentThought`, `stop`, `subagentStart` — five new lifecycle events for cloud agents. Enables building self-correcting loops, observing agent reasoning in flight, and controlling subagent spawning programmatically.

**Redesigned Pickers**: "Run on" picker surfaces where an agent can run (Cloud / This Computer / Remote Machines); scoped project search; cleaner GitHub/GitLab/Azure DevOps grouping.

🌐 Sources: https://cursor.com/changelog/side-chat · https://www.digitalapplied.com/blog/cursor-3-11-side-chats-agent-transcript-search-2026 · https://byteiota.com/cursor-3-11-side-chats-team-mcp-cloud-agent-hooks/ · https://chatforest.com/builders-log/cursor-v3-11-side-chats-team-mcp-cloud-agent-hooks-builder-guide/ · https://www.developersdigest.tech/blog/cursor-3-11-side-chats-developer-guide-2026

---

### 5. [new] Kimi Code: Moonshot AI's TypeScript CLI Harness with ACP and 1M-Context K3 (June 2026)

**Why this is [new]:** Not in prior state. Moonshot AI's dedicated agent harness — separate from the Kimi chat product — is a genuine new entrant with ACP+MCP support.

Kimi Code (Moonshot AI) released June 6, 2026 (TypeScript, MIT-style). The harness supports ACP via a `kimi acp` subcommand — direct interoperability with the Agent Client Protocol ecosystem (Forge, Grok-Build, etc.). Also supports MCP. Current model is K3 with **1M context tokens**. K2.7-Code shipped June 12, 2026 with a 21.8% improvement on Kimi Code Bench v2 over K2.6.

Key capabilities: codebase analysis, multi-file refactoring, subagent spawning for parallel tasks, voice input via streaming transcription, web search built in, compose mode for specs-driven workflows. Installation: `curl -fsSL https://code.kimi.com/kimi-code/install.sh | bash`.

ECC v2.1 now treats Kimi Code as a native harness — Kimi Code configs, skills, and memory persist through ECC's cross-harness layer.

🌐 Sources: https://www.kimi.com/code · https://www.marktechpost.com/2026/06/06/moonshot-ai-releases-kimi-code-cli-a-terminal-ai-coding-agent-built-in-typescript-for-next-gen-agents/ · https://devops.com/moonshot-ais-kimi-k2-7-code-targets-token-efficiency-in-agentic-coding/ · https://lushbinary.com/blog/kimi-code-cli-developer-guide/ · https://aiidelist.com/ide/kimi-code · https://www.nxcode.io/resources/news/kimi-k3-benchmarks-coding-agent-evaluation-guide-2026

---

### 6. [new] Runtime (YC P26): Sandboxed Coding Agents for the Whole Team, Not Just Engineers

**Why this is [new]:** Not in prior state. Runtime attacks a distinct problem: making coding agents safe for non-engineers.

Runtime (YC P26, launched March 28, 2026; founders: Gus and Carlos, ex-Mentum/YC S21) is infrastructure that expands who can safely use coding agents within an organization. The core insight: "When the bottleneck is no longer 'who can code' but 'what should we build next,' the entire org moves faster."

Multi-harness support: Claude Code, Codex, Cursor, Copilot, Gemini, Devin. Snapshots full Docker Compose environments (Kafka, Redis, seeded DBs) in milliseconds. Trigger from Slack, Linear, Jira, GitHub, API, or web. RBAC, domain allow/deny lists, encrypted secrets (never touch sandbox), session-level observability. Hybrid deployment: E2B, Daytona, EC2, or self-hosted Kubernetes.

Real deployed use cases: automated on-call systems (PagerDuty + Sentry → PRs with unit tests); finance agents (Stripe + Snowflake reconciliation). Operating in 40+ countries, zero ad spend. Open source core available on GitHub and PyPI; 500 free credits for new users.

🌐 Sources: https://news.ycombinator.com/item?id=48225040 · https://www.runtm.com/blog/runtime-yc-p26/ · https://www.ycombinator.com/companies/runtime · https://www.producthunt.com/products/runtime · https://www.extruct.ai/data-room/ycombinator-companies-p26/ · https://svpost.com/articles/top-devtech-startups-yc-p26/

---

### 7. [new] NoClick: Always-On Agent Infrastructure with Your Existing AI Subscriptions

**Why this is [new]:** Not in prior state. Fresh Show HN (posted ~Aug 1).

NoClick (Show HN, https://www.noclick.com/) automates the infrastructure layer for always-on agent harnesses: auto-spins sandboxes, connects tools, persists files across agent cold starts, and provides observability for every tool call. The key pitch is that it reuses existing AI subscriptions (Claude, OpenAI, etc.) rather than requiring new accounts or billing through NoClick's own inference layer.

Positioning: "heroku for always-on agent harnesses" — if you have an agent harness you want to run continuously (monitoring channels, responding to events, running scheduled tasks), NoClick handles the infrastructure without you writing any orchestration code.

🌐 Sources: https://news.ycombinator.com/item?id=49086639 · https://www.noclick.com/

---

### 8. [new] Nyx: Adaptive Multi-Turn Offensive Testing Harness for AI Agents (Fabraix, April 2026)

**Why this is [new]:** Not in prior state. Nyx is the first purpose-built red-teaming harness for AI agents (not models).

Nyx (Fabraix, YC-backed) is an autonomous offensive testing harness that probes AI agents for failure modes: logic bugs, instruction-following failures, edge cases, jailbreaks, prompt injection, and tool hijacking. Unlike static payload libraries, Nyx **adapts its attack strategies** based on the target agent's defenses across multiple turns (10,000+ attack strategies maintained).

Benchmark: **78% attack success rate** on AgentHarm (vs. 67% for GPT-5.6 Sol). Already found vulnerabilities at "dozens of Fortune 500 companies." Show HN posted April 2026.

The broader context: Nyx addresses a gap that standard model red-teaming misses — agents have long action sequences where harmful outcomes can emerge from multi-step chains rather than a single model output. This is also the gap EU AI Act Articles 9-17 compliance teams are wrestling with.

🌐 Sources: https://news.ycombinator.com/item?id=47827802 · https://www.ycombinator.com/companies/fabraix · https://appsecsanta.com/research/ai-pentesting-agents-2026

---

### 9. [new] AgentGuard: Cross-Harness PreToolUse Command Validation

**Why this is [new]:** Not in prior state. Small but notable tool that fills a cross-harness security gap.

AgentGuard (krishkumar/agentguard) intercepts shell commands before execution by registering as a PreToolUse hook in Claude Code, Cursor, and Kiro CLI's respective hook systems. It validates each command against a simple rules file, recursively unwraps nested command wrappers, and returns exit code 0 (allow) or 2 (block). Installation: `agentguard init && agentguard install claude/cursor/kiro`.

Significance: AgentGuard is a cross-harness solution (not per-harness) that addresses the command-validation problem documented in the agentjacking and OAP research — without requiring full enterprise deployment.

🌐 Sources: https://github.com/krishkumar/agentguard · https://www.claudedirectory.org/for/security · https://www.getmaxim.ai/articles/ai-coding-agent-security-governing-cursor-claude-code-and-copilot/

---

### 10. [update] OpenClaw beta.7 (August 2): Claude Opus 5, Kimi K3, GPT Live, Wear OS, Local Inference

**New fact since Aug 2:** v2026.7.2-beta.7 (August 2) adds Claude Opus 5 across catalog and runtime, Kimi K3 (1M context), and GPT Live (realtime voice) with Platform API auth — the broadest model expansion in a single OpenClaw release.

Also new in beta.7: session boards and dashboards; rewind/fork/branch across web and native; archived/visibility/draft/incognito session states; suggestion queues with typing indicators; Wear OS companion (home-screen agent/model selection, realtime Talk controls, audio-reactive playback, instant-talk tile); in-process llama.cpp GGUF inference; Baseten Model API; model discovery from live provider catalogs; model downloads from web/macOS setup.

Beta.6 context (already in prior state): quarantine store, MCP Apps ticketing, session rewind, meetings expansion. OpenClaw at 384k+ stars; by June 2026 Hermes Agent overtook it on OpenRouter by daily token usage (224B vs 186B Hermes), but OpenClaw retains the enterprise and breadth lead.

🌐 Sources: https://releasebot.io/updates/openclaw · https://github.com/openclaw/openclaw/releases/tag/v2026.7.2-beta.7 · https://openclawlaunch.com/news · https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/ · https://thenewstack.io/openclaw-hermes-agent-harness/

---

### 11. [update] Agent Security: Agentjacking via Sentry MCP — 85% Execution Rate at 2,388 Organizations

**New fact since Aug 2 state:** Agentjacking is a documented June 2026 attack class (Tenet Security) not previously captured in the mcp-security-nsa-supply-chain thread.

An attacker with only a Sentry DSN (a public, write-only credential discoverable from browser JavaScript bundles or a GitHub search) can inject malicious instructions into Sentry error events. When a developer asks their coding agent to "fix unresolved Sentry issues," the agent queries Sentry via MCP, receives the poisoned event, and executes attacker-controlled commands with the developer's full local privileges.

Tenet Security tested 2,388 organizations with usable DSNs and found an **85% execution rate** across Claude Code, Cursor, and Codex. The attack bypasses EDR, WAF, IAM, and VPN monitoring because the agent performs authorized operations under developer identity. Exfiltrated data can include environment variables, Git credentials, private repository URLs, and developer identities.

This extends the supply-chain threat model beyond malicious skills into the **tool call layer** — any MCP server that ingests external data (error tracking, issue trackers, customer feedback) becomes a potential injection vector.

CSA Research Note: https://labs.cloudsecurityalliance.org/research/csa-research-note-agentjacking-mcp-sentry-injection-20260612/
Tenet Security research: https://tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/
🌐 Sources: https://thenewstack.io/agentjacking-sentry-mcp-attack/ · https://thehackernews.com/2026/06/agentjacking-attack-tricks-ai-coding.html · https://pinggy.io/blog/agentjacking_ai_coding_agents_sentry_mcp/ · https://www.shareuhack.com/en/posts/agentjacking-mcp-security-claude-code-guide-2026

---

### 12. [update] QM Multiplayer Harness: 665 HN Points, Architecture Clarified — Central Postgres Core, Swappable Harnesses

**New facts since Aug 2:** HN thread shows 665 points / 161 comments (vs. the Aug 1 launch; this is now the top HN thread for agent infrastructure this cycle). Architecture clarified in discussion:

- Each employee/channel/project gets isolated scope: memory, files, keychain view, permissions, crons, web apps, durable sandbox
- **Central Postgres core** handles identity, policy, and audit across all agents
- **Swappable harnesses**: Pi, OpenCode, Codex, Claude Code all drive the same core — deployment not tied to any single vendor
- Three security postures: `Strict` (human approval on every tool call), `Auto` (classifier screens external data before model), `Dangerous` (screening off)
- One developer building a competing multiplayer coding harness called AQ said the release was "validating" for the market direction
- Anti-slop "Taste skill" with strict rules against AI-generated artifacts (including explicit ban on em-dashes as "the #1 visual Tell")

YC's framing: "Quartermaster is the company-wide agent harness YC has been running internally for months across accounting, legal, events, and engineering" — the public release is eating-your-own-dogfood proof-of-concept.

🌐 Sources: https://news.ycombinator.com/item?id=49126604 · https://github.com/yc-software/qm · https://qm.ycombinator.com/ · https://byteiota.com/yc-open-sources-qm-multiplayer-agent-harness-is-here/ · https://startupfortune.com/y-combinator-open-sources-qm-the-ai-agent-harness-it-uses-to-run-itself/ · https://wavect.io/blog/qm-ai-agent-harness-review/ · https://agentpedia.codes/blog/yc-qm-multiplayer-agent-workspace-deployment-guide

---

### 13. [update] Anthropic: Sonnet 5 Promotional Pricing Ends Aug 31; Opus 4.1 Retires Aug 5

**New fact since Aug 2 state:** Two Anthropic pricing/model changes imminent:
1. Sonnet 5's promotional pricing of $2/$10 per million tokens ends **August 31, 2026** — standard pricing of $3/$15 takes effect September 1
2. Opus 4.1 retires **August 5, 2026** (in 2 days from today)

Claude Code v2.1.220 is the latest (July 25, 2026). Claude Opus 5 added in v2.1.219 (July 24): 1M context, $10/$50 per MTok, 2.5× faster in fast mode at 2× base cost. Claude Tag (today's deployment) adds ambient Slack harness as covered in Finding #1.

🌐 Sources: https://code.claude.com/docs/en/changelog · https://go9x.com/blog/claude-updates · https://claudefa.st/blog/guide/changelog

---

### 14. [ongoing — Japan/Community] Harness Engineering Paradigm: JP Community Pushing "Environment Architect" as Mainstream Role

🇯🇵 Japanese developer community continues to produce the richest practical harness engineering content. New Zenn case study (aicon_kato): startup built a 21-agent autonomous pipeline over 2 months processing 57,000 lines across a monorepo — 681 PRs merged per half-month by March 2026. Human role: requirements definition and exception handling only. Key insight:

> 🇯🇵「エンジニアの主な仕事がコードを書くことからシフトした」
> ("The engineer's main job shifted from writing code to designing environments, clarifying intent, and building feedback loops for agent reliability")
> — Zenn/aicon_kato (https://zenn.dev/aicon_kato/articles/harness-engineering-startup)

Hexabase reports GMO Internet Group saving 46.9 hours/month per employee (equivalent to 1,805 staff) with agent + harness design. SoftBank Logistics: 40% delivery efficiency improvement. 82% of Japanese enterprises planning AI agent adoption in 2026.

🌐 Sources: https://zenn.dev/aicon_kato/articles/harness-engineering-startup · https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026 · https://qiita.com/kenimo49/items/d003027b8fb124c771a5 · https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 · https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps

---

**Still true** (ongoing threads, no genuinely new facts today):

- MCP 2026-07-28 final spec (stateless core, MRTR, EMA stable, ~500M monthly SDK downloads) [mcp-stateless-spec-2026-07-28]
- JADEPUFFER agentic ransomware (Sysdig July 1) + Ant Group SingGuard-NSFA guardrail (July 14) [jadepuffer-agentic-security]
- Grok-Build (xAI, Rust, 23.3k stars) with Agent Client Protocol [grok-build-xai-rust-harness]
- Self-Harness (Shanghai AI Lab, arXiv:2606.09498) — +60% Terminal-Bench 2.0, autonomous harness optimization [self-harness-auto-optimization]
- OpenHarness (HKUDS, MIT, 15.1k stars), 43 tools, 10 subsystems, ohmo built-in agent [openharness-hkuds]
- VSCode 1.130 (July 22) Agent Host Protocol — sessions decouple from window lifetime [vscode-1130-agent-host]
- Google Antigravity 2.0 (Go, May I/O 2026) — Gemini CLI sunset June 18, SKILL.md portable [antigravity-gemini-cli-successor]
- Claw Code (~195k stars): clean-room Python/Rust Claude Code rewrite from source leak [claw-code-claude-rewrite]
- Kiro CLI 2.16.0 / V3 unified harness: Tangents, /context per-tool token breakdown [kiro-aws-spec-driven]
- ruvnet/agent-harness-generator (MetaHarness, 523 stars): branded harnesses, Ed25519-signed SBOM [metaharness-scaffold-generator]
- Harness Engineering paradigm (Agent = Model + Harness): DeepSeek internal formula, Stanford HAI 3%/47% data [harness-engineering-paradigm]
- DeerFlow 2.0 (ByteDance, 77.9k stars) SuperAgent + TIAMAT cloud memory [deerflow-superagent-harness]
- Hermes Agent v0.19.0 'Quicksilver' (NousResearch): 0.9s first-turn latency, 450+ contributors [hermes-agent-self-improving]
- Microsoft MAF GA + Project Polaris default Copilot model August 2026 [microsoft-maf-codeact]
- Zot (Go single-binary coding agent, 299 stars, HN 107 points; Claude Code API spoofing controversy) [zot-go-coding-harness]
- oh-my-pi (omp, 14.7k stars) + oh-my-openagent (omo, 48k stars): Pi derivatives [omp-omo-pi-derivatives]
- Yorishiro (58 stars): macOS "Presence Harness" with 3D animated avatar + Reflex Layer [yorishiro-presence-harness]
- Extension economy: Vercel skills.sh, Copilot code review skills+MCP GA July 29, SkillSpector 1-in-4 vulnerable [extension-economy-explosion]
- agentskills.io SKILL.md standard confirmed portable across 20+ harnesses with zero modification [agentskills-open-standard]
- Claude Code /doctor, /ultrareview, /fork background sessions, depth-3 subagents, ~3 releases/week [claude-code-doctor-skill-hygiene]
- Letta Agent File (.af format, Apache 2.0, 1.2k stars) — leading open format for stateful agent serialization [letta-agent-file-format]
- Layered OSS stack (17+ specialized tools per task) consensus; star count ≠ maintenance [layered-oss-stack-over-single-framework]
- macOS as proving ground: Yorishiro, Ambiance (217 HN pts), macOS26/Agent!, Supacode [macos-harness-proving-ground]
- AHE formalization (arXiv:2604.25850) + Code as Agent Harness (arXiv:2605.18747) + Lilian Weng July 4 synthesis [ahe-automated-harness-evolution]
- MCP/skill security: SkillSpector 64 patterns, 1-in-4 of 42,447 skills vulnerable; OAP (arXiv:2603.20953) [mcp-security-nsa-supply-chain]
- Internal vs External Harness disambiguation ongoing [harness-internal-external-disambiguation]
- "Environment Architect" as new role (JP community; Speakerdeck, Qiita) [environment-architect-new-role]
- Warp Oz: multi-harness control plane live; --harness claude/codex flags [warp-oz-multi-harness]
- Mozilla Otari (July 6, 357 stars): OpenAI-compatible LLM gateway, 40+ providers, prompt injection detection [mozilla-otari-llm-gateway]
- Statewright (Rust, 373 stars, Apache 2.0): state machine guardrails, 2/10 → 10/10 SWE-bench [statewright-guardrails]
- Headroom (62k stars, Netflix engineer): content-aware context compression, 20-60% token reduction [headroom-token-compression]
- Pi (54k+ stars, MIT, Armin Ronacher): sub-1000-token system prompt minimal harness [pi-minimal-agent-harness]
- NVIDIA SkillSpector (168 stars): skill security scanner, 64 patterns, 16 categories [nvidia-skillspector-security]
- DeepSeek internal Harness team (May 2026) + Reasonix terminal agent, 60%+ cost reduction [deepseek-harness-team]
- CLI-Anything (HKUDS, 46.4k stars): auto-generated CLIs with SKILL.md; CLI-Hub package manager [cli-anything-hkuds]
- Forge (forge-agents/forge) + Adulari/forge: ACP universal CLI, 300+ model cost-tier routing [forge-acp-universal-cli]
- GitHub Copilot skills+MCP GA July 29: SKILL.md in .github/skills; read-only MCP for all paid tiers [github-copilot-skills-mcp-ga]
- OpenCode (Anomaly, 191.8k stars): v1.18.10, Discover Modal models, Scout subagent [opencode-anomaly-rebrand]
- YC QM: see update #12 above [yc-qm-multiplayer-harness]
- Cursor (SpaceX $60B acquisition, closing Q3 2026): ~$4B ARR, 50k+ enterprise clients [cursor-spacex-acquisition]
- Block Buzz (github.com/block/buzz): Nostr-based workspace with cryptographic agent identity [block-buzz-workspace]
- ZCode (Z.ai/Zhipu AI, v3.2.2): free IDE, GLM-5.2, $16.20/mo vs $200/mo incumbents [zcode-zhipu-agent-ide]
- Devin Desktop (Cognition rebrand of Windsurf, June 2): Rust-rewritten Devin Local, ACP support [devin-desktop-windsurf-rebrand]
- Devin Fusion (June 29): hybrid multi-model harness, 88% PRs from automated router, 35% cost reduction [devin-fusion-multimodel]
- Ambiance (whitematterlabs, HN 217 pts): macOS Unix/FHS-based harness watching ~/.pai filesystem [ambiance-unix-harness]
- Kore.ai Artemis (May 21): ABL compiled DSL for agent definitions, dual-brain deterministic architecture [kore-artemis-abl]
- Open Agent Passport (OAP): deterministic pre-action authorization, 53ms latency, 0% attack success [open-agent-passport-oap]
- arXiv:2605.18747 "Code as Agent Harness" (May 2026): 3-layer taxonomy of code as operational substrate [code-as-agent-harness-paper]
- Tilde (trytilde.ai): TypeScript harness SDK for cloud-deployed purpose-driven agents [tilde-harness-sdk]

---

## Cross-Source Patterns

### Pattern 1: The Harness Wars Go East — Chinese and Japanese Companies Ship Competitive Stacks
Appeared on: HN (557 pts for MiMo Code), CSDN, Zhihu, Toutiao, Qiita, Zenn 🇨🇳🇯🇵🌐

The Chinese coding agent harness ecosystem produced two meaningful entries this cycle: MiMo Code (Xiaomi, MIT fork of OpenCode, 12.6k stars, 557 HN pts) and continued momentum of ZCode (Zhihu/GLM-5.2, $16.20/mo). The HN discussion on MiMo Code was as much about the geopolitical signal as the technical features — multiple commenters noted Chinese models "match or exceed Western alternatives at a fraction of the cost." ECC v2.1 adding Kimi Code (Moonshot AI) as a native harness alongside Claude Code and Cursor signals that the extension economy is recognizing the Chinese harness ecosystem as worth targeting.

Japanese community (Zenn, Qiita) continues producing the densest practical content on harness engineering, with startups like Aicon documenting 21-agent pipeline case studies achieving 681 PRs/half-month.

> "Based solely on quality and price, OpenAI, Anthropic, and other western models just can't compete with the new generation of Chinese open models." — HN commenter on MiMo Code ([link](https://news.ycombinator.com/item?id=48490826)) 🌐

---

### Pattern 2: The Collaboration Layer as the Next Harness Frontier
Appeared on: VentureBeat, Fortune, Anthropic blog, Medium, QM HN thread 🌐

Two distinct products launched this cycle position the Slack/workspace layer as the next harness battleground: **Claude Tag** (Anthropic, ambient, multiplayer, per-channel identity) and **QM** (YC, org-scoped, per-employee scopes, Slack + web). Both bet that the harness isn't just for developers at terminals — it's for the whole organization running work asynchronously. The framing: "agent as team member" rather than "agent as tool." Block Buzz (Nostr-based, cryptographic identity) represents a third, decentralized model from the prior period. All three are incompatible but converge on the same thesis: the collaboration surface is where agent value accrues at scale.

> "Claude Tag is multiplayer: one Claude identity operates per channel and every member interacts with the same agent, so it retains shared context across people and time." — VentureBeat ([link](https://venturebeat.com/technology/anthropic-launches-claude-tag-replacing-its-slack-app-with-a-persistent-ai-teammate-that-learns-monitors-and-works-autonomously)) 🌐

---

### Pattern 3: Security Threat Surface Expands from Skills to Tool Calls
Appeared on: The New Stack, The Hacker News, CSA Research, GitHub (AgentGuard) 🌐

The agentjacking attack moves the agent security threat model beyond malicious skills (SkillSpector's domain) into **tool call data injection** — any MCP server that reads external content (Sentry errors, GitHub issues, customer tickets) becomes a potential prompt injection channel. The 85% execution rate and 2,388 confirmed vulnerable organizations make this the most concrete agentic threat documented to date. The response ecosystem is forming: AgentGuard (PreToolUse command validation), OAP (deterministic pre-action auth, 0% attack success), Statewright (state machine per-state tool allowlists), ECC AgentShield (config auditing). Each operates at a different layer; no single tool covers the full surface.

> "A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex." — The New Stack ([link](https://thenewstack.io/agentjacking-sentry-mcp-attack/)) 🌐

---

### Pattern 4: Cross-Harness Infrastructure Matures — ECC and Runtime as Evidence
Appeared on: TechTimes, Augment Code, YC/HN, GitHub Trending 🌐

Neither ECC (237k stars, cross-harness OS) nor Runtime (multi-harness sandboxed execution for teams) is a harness itself — both are infrastructure that makes multiple harnesses work better together. This "above the harness" layer is new: it did not exist 12 months ago. ECC provides unified config, skills, memory, and security across 7 harnesses; Runtime provides unified execution, permissions, and billing across Claude Code/Codex/Cursor/Copilot/Gemini/Devin. The YC QM architecture (swappable harnesses against a common Postgres core) makes the same bet at the org level. Three independent projects converging on "harness-neutral coordination layer" within the same cycle is a signal the category is forming.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| tosh | qm – Multiplayer agent harness for work | 665 | 161 | "Validating for the whole market direction" (AQ developer) | https://news.ycombinator.com/item?id=49126604 |
| apeters | MiMo Code is now released and open-source | 557 | 315 | "Chinese models match or exceed Western alternatives at fraction of cost" | https://news.ycombinator.com/item?id=48490826 |
| (staff) | Show HN: NoClick – Build always-on agents with existing AI subscriptions | — | — | Infrastructure for always-on harnesses | https://news.ycombinator.com/item?id=49086639 |
| (staff) | Launch HN: Runtime (YC P26) – Sandboxed coding agents for everyone on a team | — | — | Multi-harness, Docker snapshot, any trigger | https://news.ycombinator.com/item?id=48225040 |
| (staff) | Show HN: Nyx – multi-turn, adaptive, offensive testing harness for AI agents | — | — | 78% attack success on AgentHarm | https://news.ycombinator.com/item?id=47827802 |
| ardatasci | Towards a harness that can do anything (Ambiance) | 217 | 108 | "A harness built from things the model already knows" | https://news.ycombinator.com/item?id=48921077 |
| (staff) | Ask HN: AI Agent and harness containerization/security recommendations | — | — | Security guidance thread | https://news.ycombinator.com/item?id=48899674 |
| (staff) | Show HN: Agent-harness-kit scaffolding for multi-agent workflows | — | — | Multi-agent scaffold | https://news.ycombinator.com/item?id=48047826 |
| (staff) | Show HN: How to build and self-host a code review agent (Tilde) | — | — | Self-hosted code review via Tilde SDK | https://news.ycombinator.com/item?id=49128177 |
| (staff) | Ask HN: Best option for hosted agent in 2026? | — | — | Community guidance thread | https://news.ycombinator.com/item?id=46917293 |
| (staff) | Show HN: Harness – Manage parallel Claude Code agents across Git worktrees | — | — | Tab-based parallel agent management | https://news.ycombinator.com/item?id=47948379 |
| (staff) | 2026-08-02 HN front page | — | — | No agent-harness items on front page Aug 2 | https://news.ycombinator.com/front |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic blog | https://www.anthropic.com/news/introducing-claude-tag | Claude Tag official announcement |
| 🌐 | VentureBeat | https://venturebeat.com/technology/anthropic-launches-claude-tag-replacing-its-slack-app-with-a-persistent-ai-teammate-that-learns-monitors-and-works-autonomously | Claude Tag enterprise coverage |
| 🌐 | GitHub MiMo Code | https://github.com/XiaomiMiMo/MiMo-Code | 12.6k stars, MIT, OpenCode fork |
| 🌐 | Developer Tech | https://www.developer-tech.com/news/xiaomi-mimo-code-executes-200-step-agentic-developer-workflows/ | 200-step claims coverage |
| 🌐 | GitHub ECC | https://github.com/affaan-m/ecc | 237k stars cross-harness OS |
| 🌐 | Augment Code ECC | https://www.augmentcode.com/learn/ecc-v2-cross-harness-agent-system | ECC v2 explainer |
| 🌐 | TechTimes ECC | https://www.techtimes.com/articles/320269/20260713/agent-harness-ecc-tops-228k-stars-free-tool-turns-claude-code-full-dev-team.htm | ECC milestone coverage |
| 🌐 | Cursor changelog | https://cursor.com/changelog/side-chat | Cursor 3.11 side chats official |
| 🌐 | Digital Applied | https://www.digitalapplied.com/blog/cursor-3-11-side-chats-agent-transcript-search-2026 | Cursor 3.11 features |
| 🌐 | MarkTechPost Kimi Code | https://www.marktechpost.com/2026/06/06/moonshot-ai-releases-kimi-code-cli-a-terminal-ai-coding-agent-built-in-typescript-for-next-gen-agents/ | Kimi Code launch |
| 🌐 | Runtime blog | https://www.runtm.com/blog/runtime-yc-p26/ | Runtime YC P26 official |
| 🌐 | YC Runtime | https://www.ycombinator.com/companies/runtime | YC listing |
| 🌐 | NoClick site | https://www.noclick.com/ | Always-on agent infrastructure |
| 🌐 | Fabraix/Nyx YC | https://www.ycombinator.com/companies/fabraix | Nyx YC listing |
| 🌐 | AppSec Santa Nyx | https://appsecsanta.com/research/ai-pentesting-agents-2026 | AI pentesting 2026 survey |
| 🌐 | GitHub AgentGuard | https://github.com/krishkumar/agentguard | Cross-harness PreToolUse hook |
| 🌐 | The New Stack Agentjacking | https://thenewstack.io/agentjacking-sentry-mcp-attack/ | Primary agentjacking coverage |
| 🌐 | Tenet Security | https://tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/ | Researcher primary source |
| 🌐 | The Hacker News | https://thehackernews.com/2026/06/agentjacking-attack-tricks-ai-coding.html | Wide coverage |
| 🌐 | CSA Research Note | https://labs.cloudsecurityalliance.org/research/csa-research-note-agentjacking-mcp-sentry-injection-20260612/ | Industry body coverage |
| 🌐 | OpenClaw releases | https://releasebot.io/updates/openclaw | Beta.7 Aug 2 release notes |
| 🌐 | GitHub OpenClaw beta.7 | https://github.com/openclaw/openclaw/releases/tag/v2026.7.2-beta.7 | Official release |
| 🌐 | HN QM | https://news.ycombinator.com/item?id=49126604 | QM 665 pts discussion |
| 🌐 | GitHub QM | https://github.com/yc-software/qm | QM code + README |
| 🌐 | QM homepage | https://qm.ycombinator.com/ | YC homepage |
| 🌐 | ByteIota QM | https://byteiota.com/yc-open-sources-qm-multiplayer-agent-harness-is-here/ | QM feature breakdown |
| 🌐 | Claude changelog | https://code.claude.com/docs/en/changelog | Latest Claude Code versions |
| 🌐 | MCP spec blog | https://blog.modelcontextprotocol.io/posts/2026-07-28/ | July 28 spec reference |
| 🌐 | morphllm leaderboard | https://www.morphllm.com/best-ai-coding-agents-2026 | Aug 2 leaderboard |
| 🌐 | Firecrawl best agents | https://www.firecrawl.dev/blog/best-ai-coding-agents | Cost+accuracy comparison |
| 🌐 | OpenClaw vs Hermes | https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/ | June 2026 market share |
| 🌐 | GitHub awesome-harness | https://github.com/ai-boost/awesome-harness-engineering | 3.3k stars curated list |
| 🌐 | best-of-Agent-Harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses, weekly rescore |
| 🌐 | Harness MCP redesign | https://www.harness.io/blog/harness-mcp-server-redesign | 130→11 tools redesign |
| 🌐 | Fortune Claude Tag | https://fortune.com/2026/06/23/anthropic-claude-tag-virtual-employee-tool-slack/ | Fortune coverage |
| 🌐 | Kimi Code site | https://www.kimi.com/code | Kimi Code official |
| 🌐 | DevOps Kimi K2.7 | https://devops.com/moonshot-ais-kimi-k2-7-code-targets-token-efficiency-in-agentic-coding/ | K2.7 launch |
| 🌐 | Kimi Code LLMRef | https://www.llmreference.com/agents/mimo-code | Third-party review |
| 🌐 | ECC GitHub release | https://github.com/affaan-m/ECC/releases/tag/v2.0.0 | v2.0.0 release notes |
| 🌐 | PyShine ECC | https://pyshine.com/ECC-Everything-Claude-Code-Agentic-Operator-System/ | ECC deep dive |
| 🌐 | New Stack agentjacking | https://thenewstack.io/agentjacking-sentry-mcp-attack/ | Agentjacking primary |
| 🌐 | Pinggy agentjacking | https://pinggy.io/blog/agentjacking_ai_coding_agents_sentry_mcp/ | Technical explainer |
| 🌐 | Claude Tag IT guide | https://www.beri.net/article/anthropic-claude-tag-slack-enterprise-agent-it-guide-2026 | IT admin guide |
| 🌐 | MindStudio Claude Tag | https://www.mindstudio.ai/blog/claude-tag-slack-enterprise-ai-agent | Enterprise guide |
| 🌐 | Claude Tag TechRepublic | https://www.techrepublic.com/article/news-anthropic-claude-tag-ai-agent-slack/ | Industry coverage |
| 🌐 | Runtime YC listing | https://www.ycombinator.com/companies/runtime | Official listing |
| 🌐 | Runtime Product Hunt | https://www.producthunt.com/products/runtime | Product Hunt |
| 🌐 | Cursor 3.11 ByteIota | https://byteiota.com/cursor-3-11-side-chats-team-mcp-cloud-agent-hooks/ | Feature breakdown |
| 🌐 | ChatForest Cursor | https://chatforest.com/builders-log/cursor-v3-11-side-chats-team-mcp-cloud-agent-hooks-builder-guide/ | Builder guide |
| 🌐 | Claude go9x | https://go9x.com/blog/claude-updates | Claude pricing changes |
| 🇯🇵 | Zenn (aicon_kato) | https://zenn.dev/aicon_kato/articles/harness-engineering-startup | 21-agent pipeline case study |
| 🇯🇵 | Qiita (kenimo49) | https://qiita.com/kenimo49/items/d003027b8fb124c771a5 | Harness engineering intro |
| 🇯🇵 | Qiita (Ryu-Yanagi) | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | Complete harness guide |
| 🇯🇵 | Qiita (nogataka) | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | CLAUDE.md next paradigm |
| 🇯🇵 | Zenn (galirage) | https://zenn.dev/galirage/articles/ai-harness-engineering | Intro and overview |
| 🇯🇵 | Hexabase | https://www.hexabase.com/column/ai-agent-harness-engineering-business-automation-2026 | Enterprise ROI data |
| 🇯🇵 | note.com (aiedgerunner) | https://note.com/aiedgerunner/n/nbca11a6835f2 | Paradigm positioning (prior) |
| 🇯🇵 | Qiita (GYact) | https://qiita.com/GYact/items/dff02cf5271048629857 | Distributed systems analogy |
| 🇯🇵 | Speakerdeck (tame) | https://speakerdeck.com/tame/aiezientoshi-dai-nohanesuenziniaringutoha | Environment Architect slides |
| 🇨🇳 | Zhihu 12 frameworks | https://zhuanlan.zhihu.com/p/2026254728342905724 | 12 major framework analysis |
| 🇨🇳 | CSDN MCP market | https://mcp.csdn.net/6a3a576410ee7a33f28146b0.html | AI coding market survey 2026 |
| 🇨🇳 | Toutiao OpenClaw | https://www.toutiao.com/article/7612974883798008361/ | OpenClaw CN community |
| 🇨🇳 | Juejin Chrome DevTools | https://juejin.cn/post/7642306807269490723 | Chrome DevTools MCP CN |
| 🇨🇳 | Aliyun Agent guide | https://developer.aliyun.com/article/1707471 | 4 core architectures guide |
| 🇨🇳 | Zhihu frameworks 20 | https://zhuanlan.zhihu.com/p/1997716266094449634 | 20 framework selection (prior) |
| 🇨🇳 | Zhihu coding tools | https://zhuanlan.zhihu.com/p/2041289697675195678 | Full coding tools guide (prior) |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 12 threads │ ~1,400+ points │ ~650+ comments
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: not accessed (MCP Sky feed identified; no direct post retrieval)
├─ 📊 Polymarket: no markets found
├─ 🌐 Web: ~85 pages │ 🇯🇵 ~10 │ 🇨🇳 ~10
└─ 🗣️ Top voices: Xiaomi MiMo team (HN), tosh/YC (HN/QM), Tenet Security (agentjacking) │ zenn.dev/aicon_kato (JP case study)
```

---

## Out of Scope but Notable

- **Seedance 2.5** (ByteDance, 432 HN pts, Aug 2): new video generation model — top HN item today; not agent harness but shows ByteDance's lab output rate alongside DeerFlow/OpenClaw investments. ([link](https://news.ycombinator.com/front))
- **arXiv:2606.13643 "Recursive Agent Harnesses"**: paper on self-nesting agent harnesses where the harness itself is an agent that can spawn new harnesses — an architecturally novel direction beyond Self-Harness (arXiv:2606.09498). Not yet implemented but cited as a theoretical extension. ([link](https://arxiv.org/pdf/2606.13643))
- **NOOA (NVIDIA Labs)**: object-oriented agent framework where agents are single Python classes, with capabilities/state/prompts as methods/fields/docstrings and type annotations as enforced contracts. Novel OOP-as-harness design pattern; not yet widely covered. ([link](https://developer.nvidia.com/blog/six-agent-harness-capabilities-for-higher-model-performance/))

---

## Data Gaps

- **Reddit:** Not accessed. r/LocalLLaMA, r/MachineLearning, r/singularity discussions on MiMo Code, QM, Claude Tag are missing.
- **X/Twitter:** Not accessed. Social signal on tool launches absent.
- **YouTube/TikTok/Instagram:** Not accessed. No video tutorial metrics available.
- **Bluesky direct posts:** MCP Sky feed identified but individual post retrieval/engagement not performed.
- **YouTube transcript extraction:** Not performed this run.
- **Polymarket:** No markets active on agent harness topic.
- **Hermes Agent:** No new Hermes-specific updates found (last update v0.19.0 from prior period).
- **Toutiao/Weibo direct fetch:** Returned no content (likely bot protection).
- **VentureBeat Claude Tag article:** HTTP 403 on fetch; covered via secondary sources.
- **SOURCE HEALTH:** bluesky=OK. No backends reported DOWN.
- **Approximate coverage:** 72% — HN and English web are comprehensive; JP/CN hub pages partially reachable (several blocked by bot protection); Reddit/X/YouTube/Bluesky engagement data missing; Hermes Agent specifics not fresh this cycle.

---

## Key Quotes

> "Claude Tag is multiplayer: one Claude identity operates per channel and every member interacts with the same agent, so it retains shared context across people and time." — VentureBeat on Claude Tag ([link](https://venturebeat.com/technology/anthropic-launches-claude-tag-replacing-its-slack-app-with-a-persistent-ai-teammate-that-learns-monitors-and-works-autonomously)) 🌐

> "Based solely on quality and price, OpenAI, Anthropic, and other western models just can't compete with the new generation of Chinese open models." — HN commenter on MiMo Code ([link](https://news.ycombinator.com/item?id=48490826)) 🌐

> "A public Sentry key is all it takes to hijack Claude Code, Cursor, and Codex." — The New Stack on Agentjacking ([link](https://thenewstack.io/agentjacking-sentry-mcp-attack/)) 🌐

> "When the bottleneck is no longer 'who can code' but 'what should we build next,' the entire org moves faster." — Runtime (YC P26) ([link](https://www.runtm.com/blog/runtime-yc-p26/)) 🌐

> 🇯🇵「エンジニアの主な仕事がコードを書くことからシフトした — 環境設計・意図の明確化・フィードバックループ構築へ」
> ("The engineer's main job shifted from writing code to designing environments, clarifying intent, and building feedback loops for agent reliability") — Zenn/aicon_kato ([link](https://zenn.dev/aicon_kato/articles/harness-engineering-startup))

> "ECC functions as infrastructure rather than instruction — one install that persists capabilities across sessions, abstracts platform differences, and treats agent configuration as an auditable security surface." — PyShine on ECC ([link](https://pyshine.com/ECC-Everything-Claude-Code-Agentic-Operator-System/)) 🌐

> "Nyx dynamically adjusts its attack strategies based on your agent's defenses and responses — 78% attack success on AgentHarm vs 67% for GPT-5.6 Sol." — AppSec Santa 2026 ([link](https://appsecsanta.com/research/ai-pentesting-agents-2026)) 🌐

> 🇨🇳「OpenClaw狂揽16.3万星，社区贡献5700+技能插件」
> ("OpenClaw has amassed 163k stars; the community has contributed 5700+ skill plugins") — Toutiao ([link](https://www.toutiao.com/article/7612974883798008361/))

> "QM is YC putting its company-wide agent harness on GitHub under MIT — Slack + web, personal and shared scopes, crons, skills, sandboxes, and pluggable coding loops." — AI Weekly ([link](https://aiweekly.co/alerts/yc-open-sources-qm-a-multiplayer-agent-harness-for-slack-and-web)) 🌐
