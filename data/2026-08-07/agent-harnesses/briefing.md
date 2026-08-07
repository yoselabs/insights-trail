# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-07
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 10 threads | ~900+ points, ~300+ comments | Show HN / discussion; Building Advanced Agentic Harness 127 pts |
| X/Twitter | — | — | Not accessed |
| Reddit | — | — | Not accessed |
| YouTube | — | — | Not accessed |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 Search attempted; no on-topic posts retrieved |
| Polymarket | 0 markets | — | No agent harness markets found |
| Web (global) | ~55 pages | — | 🌐 WebSearch + WebFetch; 14 search queries |
| Web (Japan) | ~18 pages | — | 🇯🇵 DDG HTML endpoint + WebSearch + WebFetch (Qiita, Zenn, note, claudelab.jp, hexabase.com) |
| Web (China) | ~14 pages | — | 🇨🇳 DDG HTML endpoint + WebSearch + WebFetch (Juejin, Zhihu, CSDN, IT之家, Sina, AIBase, UU AI Hub) |

---

## Synthesized Findings

### 1. [new] Meta Muse Code: Big Tech's Sixth Major Coding Agent Enters the Market

**Claim:** Meta launched Muse Code (Aug 5, 2026) — first major Big Tech coding agent outside Anthropic/Microsoft/Google/OpenAI/xAI orbit; co-trained model+harness; contributor tier drops cost ~10x.

**Evidence:**
- **Install:** `curl -fsSL https://dev.meta.ai/install.sh | bash` — macOS+Linux, beta
- **Model:** Muse Spark 1.2 — coding-focused, co-trained with harness via rejection-sampled trajectories + recipe tuning (goals/compaction/subagents)
- **Pricing:** $1.25 input / $4.25 output per MTok; **Contributor tier** (opt-in training data): $0.10/MTok input — ~10x cheaper
- **Architecture:** Parent agent spawns child per task → isolated git worktrees (no file collisions); persistent async background sub-agents; append-only local event log (model call + tool + approval + edit) → crash-safe, replay-exact restart; background context file maintained for sub-agent consultation
- **Benchmark (Terminal-Bench 2.1, vendor-run, no neutral audit):**
  - Claude Opus 5 / Claude Code: **86.7%**
  - Muse Spark 1.2 / Muse Code: **82.9%** (2nd)
  - GPT-5.6 Terra / Codex: 81.8%
  - Grok 4.5 / Grok Build: 81.6%
- **DeepSWE 1.1:** 59.3% (trails Opus 5 and GPT-5.6 Terra)
- **Analyst note (Omdia):** Co-training advantage unlikely to hold as rivals also co-train model+harness
- 🇨🇳 CN framing: "科技巨头全部到齐" ("all major tech companies have entered the arena"); "四分之一价格" ("quarter the price" in HK/TC press)
- 🇯🇵 JP coverage: 10+ articles within 24h; framing — first time all Western+Chinese+JP companies simultaneously in coding agent market
- **Zuckerberg demo:** Embervault (full-stack browser game) built live at launch

🌐 Sources: https://developer.meta.com/ai/resources/blog/build-with-muse-code/ · https://techcrunch.com/2026/08/05/meta-launches-muse-code-an-ai-agent-for-large-code-bases/ · https://venturebeat.com/orchestration/meta-enters-the-ai-coding-wars-with-muse-spark-1-2-and-muse-code-with-persistent-async-background-agents · https://www.theregister.com/ai-and-ml/2026/08/06/meta-wants-to-get-inside-your-terminal-with-its-new-coding-agent/5283717 · https://www.orcarouter.ai/blog/meta-muse-code-terminal-coding-agent · https://www.orcarouter.ai/blog/prime-agent-vs-meta-muse-code-terminal-coding-agent · https://www.cnbc.com/2026/08/05/meta-debuts-muse-code-to-take-on-anthropic-and-openai-.html · https://www.marktechpost.com/2026/08/05/meta-superintelligence-labs-releases-muse-code/ · https://www.explainx.ai/blog/meta-muse-code-coding-agent-muse-spark-1-2-launch-august-2026 · https://www.howtogeek.com/meta-muse-code-ai-vibe-coding-agent/ · https://www.infoworld.com/article/4206084/meta-launches-muse-code-for-complex-software-work-with-persistent-ai-agents.html · https://9to5mac.com/2026/08/05/meta-launches-muse-code-ai-coding-agent-for-macos-and-linux/ · https://www.ithome.com/0/986/268.htm 🌐🇨🇳 · https://www.uuaihub.com/blog/meta-muse-code-coding-agent 🇨🇳 · https://note.com/ai_driven/n/ne8a80d7f1480 🇯🇵 · https://aiagent-navi.com/news/meta-muse-code-release/ 🇯🇵

---

### 2. [new] Prime Agent: RLM Harness with Continual Self-Improvement, 95.5% ARC-AGI-3

**Claim:** Prime Intellect (Aug 5-6, 2026) released MIT-licensed Prime Agent — a Recursive Language Model harness where subagents are function calls inside a persistent IPython kernel; claims 95.5% on ARC-AGI-3 (above 95.4% human expert).

**Evidence:**
- **Model:** RLM (Recursive Language Model) — context is a variable; tools + subagents = function calls in a REPL
- **Architecture:** Persistent IPython kernel (pre-loaded with skill modules + `rlm`); subagents called via `await rlm("task")`; returns handle immediately; agents communicate via `agent_message.send()`; "nuclear family" relationships only (parent/sibling/child)
- **Continual Harness:** Harness state (prompts, skills, memory, sub-agents) is CRUD-able from agent's own trajectory; persisted as `rlm.harness` in kernel; survives turns+sessions
- **Self-improvement:** `/refine` — reads trajectory → targeted edits to prompts/skills/sub-agents (not wholesale rewrites); background planning (non-blocking) + fast apply (brief turn-boundary block)
- **Session durability:** Daemon-backed; survives terminal disconnect; full history as append-only JSONL; async compaction + GC; branch/fork via leaf pointer
- **ARC-AGI-3 results (with Opus 5):** 95.5% RHAE Best@1 (human expert baseline: 95.4%); three runs [95.0, 95.2, 95.5]; Best@3: 99.97%
- Outperforms competing harnesses on OOLONG, LongBenchPro, ManyIH Coding with fewer tokens
- **Model support:** Works with subscriptions (Claude Pro/Max, ChatGPT/Codex, Copilot) AND APIs (Anthropic, OpenAI, Google, DeepSeek, Mistral, xAI, OpenRouter, Groq, Cerebras, Fireworks, Bedrock, Azure, NVIDIA NIM, Ollama, LM Studio, vLLM)
- **Company:** Prime Intellect, $1B valuation ($130M Series A, July 2026); MIT license
- **Install:** `curl -fsSL https://app.primeintellect.ai/prime-agent/install.sh | sh`

🌐 Sources: https://www.primeintellect.ai/blog/prime-agent · https://github.com/PrimeIntellect-ai/prime-agent · https://www.marktechpost.com/2026/08/06/prime-intellect-releases-prime-agent/ · https://cryptobriefing.com/prime-intellect-prime-agent-self-improving-rlm/ · https://www.llmrumors.com/news/recursive-agent-harnesses-prime-intellect-agentic-rl · https://www.orcarouter.ai/blog/prime-agent-explained · https://digg.com/tech/ow0qdw77 · https://www.nextbigfuture.com/2026/08/self-improving-harness-self-improving-coding-and-research-agent.html · https://github.com/PrimeIntellect-ai/prime-agent/blob/main/packages/coding-agent/docs/rlm.md

---

### 3. [new] AQ: Commercial Multiplayer Coding Harness Competes with YC QM

**Claim:** AQ (aq.dev) is a commercial (non-open-source) multiplayer coding harness — runs any agent CLI in shared tmux sessions on git worktrees; positioned directly against YC QM.

**Evidence:**
- **Agents supported:** Claude Code, Codex, Cursor Agent, Kimi, Grok, Antigravity CLI, or plain shell
- **Architecture:** Each task gets isolated git worktree; agents run as real CLIs in tmux; browser-streamed live terminals + code editor + app previews
- **Execution:** Own VM (free) or AQ-managed cloud (paid)
- **Target:** Engineering teams, not solo devs; team-oriented vs. YC QM's org-wide scope
- **Context:** Developer building AQ publicly said YC QM launch was "validating for the market direction" in HN QM thread — confirms direct competition

🌐 Sources: https://aq.dev/ · https://github.com/aq-org/ · https://aq.dev/guides/git-worktrees-for-ai-coding-agents/

---

### 4. [new] Qwen Code (Alibaba/QwenLM): Open-Source Terminal Agent with Multi-Protocol LLM Support

**Claim:** Alibaba's QwenLM released Qwen Code — open-source terminal coding agent on Qwen3-Coder; supports any API/local model at runtime; OAuth free tier ended April 15.

**Evidence:**
- **Model options:** Qwen3-Coder-480B-A35B-Instruct, 30B-A3B-Instruct, Qwen3-Coder-Next; also OpenAI/Anthropic/Gemini APIs + Ollama/vLLM
- **Features:** auto-memory, skills, subagents, agent teams, multi-protocol LLM; IDE plugins; Desktop app; daemon mode; SDKs; IM bots (Telegram/DingTalk/WeChat/Feishu)
- **Recent updates:** Forked subagents isolated from siblings; chat compression reuses main prompt cache; `/summary` accepts custom path; `/review` follows configured output language
- **Business change:** OAuth free tier discontinued April 15, 2026 → requires paid Alibaba Cloud or third-party key
- Positioned in oh-my-agent, ECC lists as a first-class supported harness alongside Claude Code, Cursor, Kimi Code

🌐 Sources: https://github.com/QwenLM/qwen-code · https://qwen.ai/qwencode · https://www.alibabacloud.com/help/en/model-studio/qwen-code-coding-plan · https://github.com/QwenLM/qwen-code/releases · https://dev.to/sienna/qwen3-coder-next-the-complete-2026-guide-to-running-powerful-ai-coding-agents-locally-1k95 · https://qwenlm.github.io/qwen-code-docs/en/users/overview/ · https://aiidelist.com/ide/qwen-code

---

### 5. [new] Oh-my-agent: Portable, Vendor-Agnostic Domain-Specialist Harness for 10+ Coding Tools

**Claim:** Oh-my-agent (first-fluke/oh-my-agent, Show HN March 2026) distributes work across domain-specialist sub-agents (frontend/backend/QA/PM/DB etc.) across 10+ coding agent harnesses.

**Evidence:**
- **Design:** Each specialist agent knows its domain deeply, has own tools+checklists, stays in lane — counterpoint to single-agent-does-everything approach
- **Supported harnesses:** Antigravity, Claude Code, Codex, Cursor, Grok Build, Kimi Code, OpenCode, Pi, Qwen Code, and more
- **Portability:** Project-specific skills/workflows/agent teams aligned with codebase conventions and engineering standards
- **Architecture:** Portable; vendor-agnostic; no lock-in to any single agent CLI

🌐 Sources: https://github.com/first-fluke/oh-my-agent · https://news.ycombinator.com/item?id=47412156

---

### 6. [new] AutoHarness (Google DeepMind): LLMs That Write Their Own Constraint Harnesses

**Claim:** Google DeepMind AutoHarness (arXiv:2603.03329, March 2026) shows Gemini-2.5-Flash auto-synthesizing code harnesses via Thompson sampling, outperforming the larger Gemini-2.5-Pro.

**Evidence:**
- **Problem:** 78% of Gemini-2.5-Flash losses in Kaggle GameArena chess = illegal moves; AutoHarness eliminates ALL illegal moves
- **Method:** Harness synthesis = search over program space guided by Thompson sampling; Flash as mutation operator iterating code based on environment feedback
- **TextArena (145 games):** Flash + AutoHarness > Gemini-2.5-Pro; code-as-policy variant > Gemini-2.5-Pro AND GPT-5.2-High on 16 single-player games, at lower cost
- **Scope:** Submitted to ICLR Recursive Self Improvement Workshop 2026; March 5, 2026
- **Conceptual link:** Related to arXiv:2606.09498 (Self-Harness, Shanghai AI Lab, +60% Terminal-Bench 2.0) — different approach to same goal of auto-optimizing harness rules

🌐 Sources: https://arxiv.org/pdf/2603.03329 · https://arxiv.org/html/2603.03329v1 · https://openreview.net/forum?id=g9rEYVNn5T · https://agent-wars.com/news/2026-03-14-autoharness-llm-agent-code-constraints · https://understandingdata.com/posts/auto-harness-synthesis/

---

### 7. [update] Hermes Agent v0.20.0: Tool Call Limit 90→500 + Auto-Import from Claude Code/Codex

**New facts:** Tool call iteration limit raised 90→500; `hermes import-agent` command auto-migrates Claude Code or Codex CLI settings in one command (resolves issue #514, longest-standing feature request).

**Evidence:**
- Limit increase: 90 → **500** confirmed in release notes and JP analysis (tech-noisy.com); enables much longer autonomous operation without human re-intervention
- `hermes import-agent`: brings Claude Code or Codex CLI settings to Hermes in one command; eliminates manual migration friction
- New CLI commands: `!` (shell exec), `/init` (project scan), `/diff` (change display)
- 🇯🇵 JP editorial: 「Claude CodeまたはCodexのCLI設定を1コマンドでHermes側に取り込むことができ、移行コストが大幅に下がった」 ("You can bring in Claude Code or Codex CLI settings to Hermes with a single command, dramatically reducing migration cost") — tech-noisy.com
- Frame shift: JP community says this moves evaluation from "whether to try Hermes" to "trying before choosing"
- Previously captured in thread: voice+barge-in, A2A v1.0 plugin, signed webhooks, grounded citations, native desktop app, 650+ contributors, 3,650 commits

🌐 Sources: https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.3 · https://the-agent-report.com/2026/08/hermes-agent-v020-herald-release-august-2026/ · https://tech-noisy.com/2026/08/04/claude-code-codex-migration-hermes-agent/ 🇯🇵 · https://releasebot.io/updates/nousresearch/hermes-agent · https://hermesatlas.com/guide/

---

### 8. [update] Claude Code v2.1.224 (Aug 7): 200-Subagent Cap Removed, Self-Hosted Environments

**New facts:** v2.1.224 (Aug 7) removes 200-subagent spawn cap entirely; adds self-hosted environments (Team/Enterprise); v2.1.222 removed Ultraplan; multiple security fixes across v2.1.222-223.

**Evidence:**
- **v2.1.224 (Aug 7):**
  - Removed 200-subagent spawn cap → "long-running sessions no longer refuse new agents"
  - Self-hosted environments: Claude Code sessions run on user machines/containers (Team/Enterprise)
  - Archive plugin source: zip install over HTTPS with optional SHA-256 pinning
  - Sandbox credential-masking: JWT-aware masking + AWS SigV4 re-signing
  - Fixed: project path resolution (cross-project access prevention); sandbox filesystem deny bypass on Linux/macOS; MCP tools deferring without announced names
- **v2.1.223 (Aug 6):**
  - Owner wildcard entries for marketplace controls (`"owner/*"`)
  - `/teleport` hint for moving cloud sessions locally
  - Fixed: Bash permission bypass via crafted command hiding; invisible Unicode permission bypass
- **v2.1.222 (Aug 4):**
  - **Ultraplan removed**
  - Stronger worktree isolation (prevents destructive git commands vs. main checkout)
  - Fixed: PreToolUse auto-allow hooks bypassing tool restrictions

🌐 Sources: https://code.claude.com/docs/en/changelog · https://releasebot.io/updates/anthropic/claude-code · https://www.havoptic.com/tools/claude-code · https://github.com/anthropics/claude-code/releases

---

### 9. [update] Cursor Router: Auto Intelligence Now 68% Cheaper (vs Prior "60% Savings")

**New fact:** Refreshed A/B test numbers — Auto Intelligence 68% lower cost (previously "60% savings in A/B tests"), Auto Balance 41% lower cost vs Opus 4.8 with +3% user satisfaction.

**Evidence:**
- **Auto Intelligence:** Delivers above Fable-level user satisfaction at **68% lower cost** (prior claim: "60% savings")
- **Auto Balance:** Outperforms Opus 4.8 at **41% lower cost** while increasing user satisfaction by 3%
- On by default for Teams plans; available across desktop, web, iOS, CLI, SDK
- Google Workspace plugins (Aug 3): 6 services — Gmail, Drive, Calendar, Docs, Sheets, Chat
- Google Workspace install: Cursor Marketplace or Customize page

🌐 Sources: https://cursor.com/changelog · https://cursor.com/changelog/google-workspace-plugins · https://releasebot.io/updates/cursor

---

### 10. [update] Copilot Studio GitHub Copilot Harness: $200/mo = 25,000 Credits, Charges from First Build

**New fact:** Billing specifics now confirmed: 1 capacity pack = $200/mo = 25,000 credits; charges begin at authoring (not just runtime); pre-Aug 3 agents get Sept 1 grace period.

**Evidence:**
- 1 Copilot Studio capacity pack = $200/month = 25,000 credits
- Equivalence: ~80–250 light tasks OR ~50–80 medium tasks per month per pack
- **Charges from first test:** Natural language authoring, previewing, testing, and generating evaluations all consume credits — not just runtime agent execution
- **Grace period:** Agents created before Aug 3 begin consuming credits under new billing Sept 1, 2026
- Three harness types remain: GitHub Copilot Harness (credit-based), Standard, Chat (prior billing unchanged)

🌐 Sources: https://techcommunity.microsoft.com/blog/copilot-studio-blog/more-powerful-agents-and-workflows-for-autonomous-business-processes-introducing/4542969 · https://rajeevpentyala.com/2026/08/05/copilot-studio-harnesses-understanding-the-github-copilot-harness/ · https://windowsforum.com/windows-news.4/copilot-studio-github-copilot-harness-bills-credits-from-first-test.441648/ · https://www.hubsite365.com/en-ww/crm-pages/copilot-studios-new-github-copilot-harness-explained.htm

---

**Still true** (ongoing threads, no genuinely new facts this cycle):

- `hermes-agent-self-improving` — see update #7 above
- `hoplite-yc-s26-cloud-deploy` — Hoplite (YC S26): ports local sessions+MCP to cloud sandboxes; Slack/Linear/iMessage/Sentry triggers; no new Aug 5-7 facts
- `vercel-ai-sdk-harnessagent` — Vercel AI SDK v7 HarnessAgent: swap harnesses without rewriting; sessions park+resume; no new facts
- `cursor-router-workspace-plugins` — see update #9 above
- `copilot-studio-ga-harness-billing` — see update #10 above
- `microsoft-agent-governance-toolkit` — 7 packages, sub-0.1ms enforcement, 9500+ tests; no new facts
- `tinyagents-rust-recursive` — TinyAgents: Rust recursive harness, .rag/.ragsh; no new facts
- `sprocket-hardware-software-agent` — Sprocket: hardware+software AI agent; no new facts
- `gambit-reliable-agent-harness` — Gambit: LLM-decides-throughout, type-safe decks, automated graders; no new facts
- `nlah-natural-language-harnesses` — NLAH: harness logic in NL, 30.4%→47.2% OSWorld success; no new facts
- `skills-security-prompt-injection-36pct` — Agensi 36% prompt injection rate, 8-point security scan; no new facts
- `claude-code-doctor-skill-hygiene` — see update #8 above
- `openclaw-gateway-harness` — OpenClaw: npm singleton fix, extended-stable channel; no Aug 5-7 new release found
- `microsoft-maf-codeact` — MAF GA (Jul 22): FileAccess opt-in, planning, file memory, skills from MCP; no new facts
- `extension-economy-explosion` — 23,600+ skills, 12,700+ MCP servers on claudemarketplaces.com; Skills vs. MCP role differentiation ("MCP for live tool calls, Skills for reusable knowledge") — confirmed ongoing
- `claude-tag-slack-agent` — Claude Tag deployed Aug 3; ambient per-channel Slack agent; no new facts
- `mimo-code-xiaomi` — MiMo Code: OpenCode fork, SQLite FTS5, Dream+Distill, 12.6k stars; no new facts
- `ecc-cross-harness-os` — ECC: 237k stars, 281 skills, 67 agents, 7 harnesses, Plan Canvas, Kimi Code support; no new facts
- `cursor-3-11-update` — Cursor 3.11: Side Chats, Agent Transcript Search, Cloud Agent Hooks; no new facts
- `kimi-code-moonshot` — Kimi Code: ACP+MCP, K3 1M context, K2.7-Code +21.8%; no new facts
- `runtime-yc-p26` — Runtime: Docker Compose snapshot, 6 harnesses, Slack/Linear/Jira triggers; no new facts
- `noclick-always-on` — NoClick: always-on agent infra reusing existing AI subscriptions; no new facts
- `nyx-offensive-testing` — Nyx (Fabraix): 78% attack success on AgentHarm; no new facts
- `agentguard-security-tool` — AgentGuard: cross-harness PreToolUse hook; no new facts
- `mcp-security-nsa-supply-chain` — Agentjacking 85% execution rate; SkillSpector 1-in-4 of 42,447 vulnerable; no new facts
- `yc-qm-multiplayer-harness` — QM: 665 HN pts, Postgres core, swappable harnesses; no new facts
- `anthropic-managed-agents-mcp-tunnels` — Claude Tag deployed; Opus 5 (Jul 24); Sonnet 5 promo pricing ends Aug 31; no new facts
- `mcp-stateless-spec-2026-07-28` — MCP 2026-07-28 final spec: stateless core, MRTR, EMA stable; no new facts
- `jadepuffer-agentic-security` — JADEPUFFER agentic ransomware; SingGuard-NSFA guardrail; no new facts
- `grok-build-xai-rust-harness` — Grok-Build: Rust TUI, ACP for editor embedding, 23.3k stars; no new facts
- `self-harness-auto-optimization` — Self-Harness (Shanghai AI Lab): +60% Terminal-Bench 2.0; no new facts
- `openharness-hkuds` — OpenHarness: 43 tools, 10 subsystems, ohmo agent; no new facts
- `vscode-1130-agent-host` — VSCode 1.130 Agent Host Protocol: sessions decouple from window; no new facts
- `antigravity-gemini-cli-successor` — Antigravity 2.0: Windsurf codebase, SKILL.md portable; no new facts
- `claw-code-claude-rewrite` — Claw Code: ~195k stars, Python/Rust rewrite; no new facts
- `kiro-aws-spec-driven` — Kiro CLI v2.13.0: introspect subagent, global hooks, tangents; no new facts
- `metaharness-scaffold-generator` — MetaHarness: 523 stars, 19 vertical templates, Ed25519-signed SBOM; no new facts
- `harness-engineering-paradigm` — Agent = Model + Harness paradigm; up to 6x perf diff from harness alone; no new facts
- `deerflow-superagent-harness` — DeerFlow 2.0: ByteDance, 77.9k stars, TIAMAT cloud memory; no new facts
- `omnigent-meta-harness` — Databricks Omnigent: meta-harness, swap harnesses without rewriting; no new facts
- `zot-go-coding-harness` — Zot: Go single-binary, 299 stars, Claude Code API spoofing controversy; no new facts
- `omp-omo-pi-derivatives` — oh-my-pi (14.7k) + oh-my-openagent (48k): Pi derivatives; no new facts
- `yorishiro-presence-harness` — Yorishiro: macOS 3D avatar Presence Harness; no new facts
- `agentskills-open-standard` — SKILL.md: portable across 20+ harnesses; no new facts
- `letta-agent-file-format` — Letta .af format: stateful agent serialization; no new facts
- `layered-oss-stack-over-single-framework` — 17+ specialized OSS layers per task consensus; no new facts
- `macos-harness-proving-ground` — macOS proving ground: Yorishiro, Ambiance, macOS26/Agent!; no new facts
- `ahe-automated-harness-evolution` — arXiv:2604.25850 AHE + arXiv:2605.18747 Code as Harness; no new facts
- `harness-internal-external-disambiguation` — Internal vs External Harness concept confusion; no new facts
- `environment-architect-new-role` — "Environment Architect" new engineering role; 🇯🇵 JP community: "環境設計" dominant framing confirmed this cycle
- `warp-oz-multi-harness` — Warp Oz: orchestrates Claude Code/Codex/Warp Agent; no new facts
- `mozilla-otari-llm-gateway` — Mozilla Otari: 40+ providers, prompt injection detection; no new facts
- `statewright-guardrails` — Statewright: state machine guardrails; 2/10→10/10 SWE-bench; no new facts
- `headroom-token-compression` — Headroom: 62k stars, 20-60% token reduction; no new facts
- `pi-minimal-agent-harness` — Pi: 54k+ stars, sub-1000-token system prompt; no new facts
- `nvidia-skillspector-security` — SkillSpector: 64 vulnerability patterns, 1-in-4 of 42,447 skills vulnerable; no new facts
- `deepseek-harness-team` — DeepSeek Harness team (May 2026) + Reasonix 60%+ cost reduction; no new facts
- `cli-anything-hkuds` — CLI-Anything: 46.4k stars, SKILL.md auto-generated CLIs; no new facts
- `forge-acp-universal-cli` — Forge: ACP universal CLI, 300+ model cost-tier routing; no new facts
- `github-copilot-skills-mcp-ga` — Copilot skills+MCP GA July 29: SKILL.md in .github/skills; no new facts
- `opencode-anomaly-rebrand` — OpenCode (Anomaly, 193k+ stars): Scout subagent, background subagents; no new facts
- `cursor-spacex-acquisition` — SpaceX $60B acquisition, closing Q3 2026; no new facts
- `block-buzz-workspace` — Block Buzz: Nostr-based ACP workspace; no new facts
- `zcode-zhipu-agent-ide` — ZCode (Z.ai): GLM-5.2, $16.20/mo, mobile steering; no new facts
- `devin-desktop-windsurf-rebrand` — Devin Desktop: ACP support, Rust-rewritten Devin Local; no new facts
- `devin-fusion-multimodel` — Devin Fusion: hybrid multi-model, 35% lower cost; no new facts
- `ambiance-unix-harness` — Ambiance: ~/.pai filesystem, Unix philosophy; no new facts
- `kore-artemis-abl` — Kore.ai Artemis: ABL compiled DSL, dual-brain; no new facts
- `open-agent-passport-oap` — OAP: 0% attack success, 53ms latency; no new facts
- `code-as-agent-harness-paper` — arXiv:2605.18747: 3-layer taxonomy; no new facts
- `tilde-harness-sdk` — Tilde: TypeScript SDK, Vercel-deployable; no new facts

---

## Cross-Source Patterns

### Pattern 1: Aug 5 Twin Launch — Muse Code (Closed/Co-Trained) vs Prime Agent (Open/RLM) 🌐
Appeared on: TechCrunch, VentureBeat, The Register, MarkTechPost, OrcaRouter, Digg

Both launched Aug 5, 2026 — representing two opposing bets on the future of coding agent harnesses:
- **Muse Code:** Closed, per-token, co-trained with model — maximum first-party synergy, deepest integration, but tied to Meta infrastructure
- **Prime Agent:** Open-source (MIT), model-agnostic, RLM-powered — any model, self-improving harness state, runs wherever

Terminal-Bench 2.1 (vendor-run): Claude Code leads 86.7%; Muse Code 2nd at 82.9%; Codex 81.8%; Grok Build 81.6% — four incumbents benchmarked in a 5-point window shows harness commoditization; differences shrinking.

> "Prime Agent is an open-source, MIT-licensed self-improving harness — a framework you install locally and point at whatever model you already pay for." — OrcaRouter ([link](https://www.orcarouter.ai/blog/prime-agent-vs-meta-muse-code-terminal-coding-agent)) 🌐

---

### Pattern 2: Extension Economy Evolves — Skills Cannibalizing MCP for Some Jobs 🌐
Appeared on: MCP docs, claudemarketplaces.com, Kotrotsos/Medium, Copilot Studio blog

The skills/MCP landscape is entering a second phase. claudemarketplaces.com now indexes 23,600+ skills, 12,700+ MCP servers. The emerging distinction: MCP for live tool calls against external systems; Skills for reusable packaged knowledge. "Packaged knowledge that once shipped as an MCP server migrating to Agent Skills." Meanwhile Copilot Studio billing confirms skills economy has real revenue stakes ($200/mo = 25k credits).

🌐 Sources: https://claudemarketplaces.com/ · https://kotrotsos.medium.com/skills-mcp-and-tool-calling-the-three-layers-of-agent-extension-6620c9d7710e · https://modelcontextprotocol.io/docs/2026-07-28/develop/build-with-agent-skills

---

### Pattern 3: JP Community — Harness Audit Frameworks Maturing 🇯🇵
Appeared on: Qiita (hisaho 7-axis framework), hexabase.com, claudelab.jp, zenn.dev

Japanese developer community this cycle shifted from "what is harness engineering" tutorials to structured audit frameworks. Qiita/hisaho published a 7-axis, 70-point harness audit (Tool Coverage, Context Efficiency, Quality Gates, Memory Persistence, Eval Coverage, Security Guardrails, Cost Efficiency). Dominant term: 「環境設計」(environment design). Key insight: 「エージェントの完了品質を向上させるには、プロダクトコードではなくHarness設定を改善する」("optimize the environment, not the product code").

> 🇯🇵「2026年の新常識は、モデル性能差1点より、ハーネス設計22点の方が開発生産性を決める」
> ("The new common sense of 2026: harness design quality determines development productivity more than model performance differences") — tech-noisy.com ([link](https://tech-noisy.com/2026/08/04/claude-code-codex-migration-hermes-agent/)) 🇯🇵

---

### Pattern 4: CN Developer Protocol Convergence Anxiety — MCP+A2A+AG-UI 🇨🇳
Appeared on: Juejin, pengjiyuan.github.io, CSDN, aibotgo.net

Chinese developer community tracking three competing inter-agent protocols as a real problem: MCP (Anthropic/ecosystem), A2A (Google/OpenAI), AG-UI (LangChain). Article title: "AI Agent 协议生态全景 2026：MCP、A2A、AG-UI 与智能体互联基础设施" ("AI Agent Protocol Landscape 2026: MCP, A2A, AG-UI and Agent Interconnection Infrastructure"). Juejin frames MCP as "AI时代的HTTP协议" ("HTTP of the AI era") but notes interoperability between the three is unresolved. CN community sees this as the main infrastructure bottleneck for multi-agent deployments.

🇨🇳 Sources: https://juejin.cn/post/7651426279837171764 · https://pengjiyuan.github.io/articles/agent-protocol-ecosystem-2026/ · https://aibotgo.net/blog/mcp-protocol-ecosystem-2026/

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | Building an Advanced Agentic Harness | 127 | 43 | "Minimalist 'smol' system benchmarks cheaper + faster than orchestrated frameworks" | https://news.ycombinator.com/item?id=49182946 |
| tosh | qm – Multiplayer agent harness for work | 665 | 161 | AQ dev: "validating for the market direction" | https://news.ycombinator.com/item?id=49126604 |
| — | Show HN: Implement-spec – harness-agnostic spec-to-verified-PR skill | (deleted) | — | Post inaccessible | https://news.ycombinator.com/item?id=49168675 |
| — | Show HN: Oh-my-agent – structural harness for real projects | ~50 | — | Domain-specialist agent teams across 10+ harnesses | https://news.ycombinator.com/item?id=47412156 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Meta developer blog | https://developer.meta.com/ai/resources/blog/build-with-muse-code/ | Muse Code official launch |
| 🌐 | TechCrunch | https://techcrunch.com/2026/08/05/meta-launches-muse-code-an-ai-agent-for-large-code-bases/ | Meta Muse Code launch coverage |
| 🌐 | VentureBeat | https://venturebeat.com/orchestration/meta-enters-the-ai-coding-wars-with-muse-spark-1-2-and-muse-code-with-persistent-async-background-agents | Muse Code architecture |
| 🌐 | The Register | https://www.theregister.com/ai-and-ml/2026/08/06/meta-wants-to-get-inside-your-terminal-with-its-new-coding-agent/5283717 | Critical analysis |
| 🌐 | CNBC | https://www.cnbc.com/2026/08/05/meta-debuts-muse-code-to-take-on-anthropic-and-openai-.html | Business coverage |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/prime-agent-vs-meta-muse-code-terminal-coding-agent | Head-to-head comparison |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/meta-muse-code-terminal-coding-agent | Muse Code deep review |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/05/meta-superintelligence-labs-releases-muse-code/ | Launch + model details |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/06/prime-intellect-releases-prime-agent/ | Prime Agent launch |
| 🌐 | Prime Intellect blog | https://www.primeintellect.ai/blog/prime-agent | Prime Agent official |
| 🌐 | GitHub Prime Agent | https://github.com/PrimeIntellect-ai/prime-agent | Code + RLM docs |
| 🌐 | CryptoBriefing | https://cryptobriefing.com/prime-intellect-prime-agent-self-improving-rlm/ | ARC-AGI-3 results |
| 🌐 | LLM Rumors | https://www.llmrumors.com/news/recursive-agent-harnesses-prime-intellect-agentic-rl | RLM analysis |
| 🌐 | AQ website | https://aq.dev/ | Multiplayer harness |
| 🌐 | GitHub first-fluke/oh-my-agent | https://github.com/first-fluke/oh-my-agent | Oh-my-agent |
| 🌐 | arXiv AutoHarness | https://arxiv.org/pdf/2603.03329 | DeepMind paper |
| 🌐 | Agent-Wars AutoHarness | https://agent-wars.com/news/2026-03-14-autoharness-llm-agent-code-constraints | AutoHarness coverage |
| 🌐 | Hermes GitHub release | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.8.3 | v0.20.0 official |
| 🌐 | The Agent Report | https://the-agent-report.com/2026/08/hermes-agent-v020-herald-release-august-2026/ | Herald Release analysis |
| 🌐 | Claude Code changelog | https://code.claude.com/docs/en/changelog | v2.1.224 features |
| 🌐 | Havoptic | https://www.havoptic.com/tools/claude-code | Claude Code release summary |
| 🌐 | Cursor changelog | https://cursor.com/changelog | Router numbers |
| 🌐 | Cursor Workspace plugins | https://cursor.com/changelog/google-workspace-plugins | 6 Google services |
| 🌐 | Microsoft Tech Community | https://techcommunity.microsoft.com/blog/copilot-studio-blog/more-powerful-agents-and-workflows-for-autonomous-business-processes-introducing/4542969 | Copilot Studio billing |
| 🌐 | Rajeev Pentyala | https://rajeevpentyala.com/2026/08/05/copilot-studio-harnesses-understanding-the-github-copilot-harness/ | Billing breakdown |
| 🌐 | QwenLM/qwen-code | https://github.com/QwenLM/qwen-code | Alibaba terminal agent |
| 🌐 | Qwen Code site | https://qwen.ai/qwencode | Official |
| 🌐 | data4sci blog | https://data4sci.com/blog/building-an-advanced-agentic-harness | HN 127-pt post |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | 23,600+ skills index |
| 🌐 | MCP build with skills | https://modelcontextprotocol.io/docs/2026-07-28/develop/build-with-agent-skills | Official skills spec |
| 🌐 | explainx.ai Muse Code | https://www.explainx.ai/blog/meta-muse-code-coding-agent-muse-spark-1-2-launch-august-2026 | Review |
| 🌐 | HowToGeek | https://www.howtogeek.com/meta-muse-code-ai-vibe-coding-agent/ | Consumer coverage |
| 🌐 | InfoWorld | https://www.infoworld.com/article/4206084/meta-launches-muse-code-for-complex-software-work-with-persistent-ai-agents.html | Enterprise angle |
| 🌐 | 9to5Mac | https://9to5mac.com/2026/08/05/meta-launches-muse-code-ai-coding-agent-for-macos-and-linux/ | macOS/Linux coverage |
| 🌐 | Forbes | https://www.forbes.com/sites/jonmarkman/2026/08/06/meta-launches-muse-code-a-new-ai-coding-agent-powered-by-spark-12/ | Market analysis |
| 🌐 | Technology.org | https://www.technology.org/2026/08/07/meta-muse-code-muse-spark-1-2-coding-agent/ | Aug 7 coverage |
| 🌐 | NextBigFuture | https://www.nextbigfuture.com/2026/08/self-improving-harness-self-improving-coding-and-research-agent.html | Prime Agent |
| 🌐 | kingy.ai | https://kingy.ai/blog/prime-agent-review-self-improving-rlm-harness/ | Prime Agent review |
| 🌐 | OrcaRouter Prime Agent | https://www.orcarouter.ai/blog/prime-agent-explained | RLM explanation |
| 🌐 | Digg ARC-AGI-3 | https://digg.com/tech/ow0qdw77 | Prime Agent ARC results |
| 🌐 | Windows Forum Copilot | https://windowsforum.com/windows-news.4/copilot-studio-github-copilot-harness-bills-credits-from-first-test.441648/ | Billing from first build |
| 🌐 | HN Building harness | https://news.ycombinator.com/item?id=49182946 | 127-pt discussion |
| 🌐 | RyanAlberts/best-of-harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked |
| 🌐 | ai-boost/awesome-harness | https://github.com/ai-boost/awesome-harness-engineering | 3.3k stars curated |
| 🌐 | bradAGI/awesome-cli | https://github.com/bradAGI/awesome-cli-coding-agents | CLI agents curated |
| 🌐 | majiayu000/harness | https://github.com/majiayu000/harness | Rust fleet governance |
| 🌐 | OrcaRouter Terminal-Bench | https://www.orcarouter.ai/blog/prime-agent-vs-meta-muse-code-terminal-coding-agent | Benchmark table |
| 🌐 | totalum MCP servers | https://www.totalum.app/blog/best-mcp-servers-2026 | Best MCP 2026 |
| 🌐 | codersera Claude Skills | https://codersera.com/blog/claude-skills-mcp-servers-practitioner-guide-2026/ | Skills+MCP guide |
| 🌐 | Kotrotsos medium | https://kotrotsos.medium.com/skills-mcp-and-tool-calling-the-three-layers-of-agent-extension-6620c9d7710e | Three-layer extension model |
| 🌐 | Agensi marketplaces | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 7 marketplaces compared |
| 🌐 | MCP Market | https://mcpmarket.com/ | MCP discovery hub |
| 🌐 | aiidelist Qwen Code | https://aiidelist.com/ide/qwen-code | Qwen Code review |
| 🌐 | tech-noisy.com Hermes | https://tech-noisy.com/2026/08/04/claude-code-codex-migration-hermes-agent/ | JP: import-agent detail |
| 🇯🇵 | Qiita (hisaho) | https://qiita.com/hisaho/items/3e1a29bc8b265616614f | 7-axis harness audit framework |
| 🇯🇵 | Qiita (nogataka) | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | Harness Engineering intro |
| 🇯🇵 | Hexabase harness guide | https://www.hexabase.com/column/harness-engineering-complete-guide-ai-agent-3-elements-practical-steps | Enterprise harness ROI |
| 🇯🇵 | Hexabase CC+Cursor | https://www.hexabase.com/column/harness-engineering-claude-code-cursor-guide | Practitioner guide |
| 🇯🇵 | Zenn (sasadango28) | https://zenn.dev/sasadango28/articles/claude-code-harness-engineering-20260415 | 5-layer design patterns |
| 🇯🇵 | claudelab.jp guide | https://claudelab.jp/articles/716 | CLAUDE.md, Hooks, MCP, Skills |
| 🇯🇵 | note.com (ai_driven) | https://note.com/ai_driven/n/ne8a80d7f1480 | Muse Code JP launch |
| 🇯🇵 | note.com (aiglobal) | https://note.com/aiglobal/n/n06473905d1fc | Muse Code JP |
| 🇯🇵 | aiagent-navi.com | https://aiagent-navi.com/news/meta-muse-code-release/ | Muse Code JP |
| 🇯🇵 | innovatopia.jp | https://innovatopia.jp/ai/ai-news/115277/ | Muse Code JP |
| 🇯🇵 | labmemo.com | https://labmemo.com/meta-muse-code-muse-spark-1-2-terminal-coding-agent-2026/ | Muse Code JP |
| 🇯🇵 | genai-ai.co.jp | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | Harness Engineering July 2026 |
| 🇯🇵 | claudelab.jp main | https://claudelab.jp/articles/716 | CC Harness Design Patterns |
| 🇨🇳 | Juejin AI Agent dev | https://juejin.cn/post/7651426279837171764 | 2026 frameworks + MCP |
| 🇨🇳 | UU AI Hub Muse Code | https://www.uuaihub.com/blog/meta-muse-code-coding-agent | CN: Muse Code analysis |
| 🇨🇳 | IT之家 | https://www.ithome.com/0/986/268.htm | CN tech: Muse Code |
| 🇨🇳 | Sina Finance CN | https://finance.sina.com.cn/stock/usstock/c/2026-08-06/doc-inimkfvc3067450.shtml | CN: Meta coding agent |
| 🇨🇳 | AIBase News | https://news.aibase.com/zh/news/30139 | CN AI news: Muse Code |
| 🇨🇳 | pengjiyuan.github.io | https://pengjiyuan.github.io/articles/agent-protocol-ecosystem-2026/ | MCP+A2A+AG-UI ecosystem |
| 🇨🇳 | aibotgo.net MCP | https://aibotgo.net/blog/mcp-protocol-ecosystem-2026/ | 800+ MCP servers |
| 🇨🇳 | CSDN MCP | https://blog.csdn.net/qq_61629028/article/details/160774998 | MCP ecosystem 2026 |
| 🇨🇳 | sshmac.com (CN) | https://sshmac.com/zh/blog/articles/meta-muse-code-ai-coding-agent-rukou/ | Muse Code install guide CN |
| 🇨🇳 | Zhihu Muse Code | https://zhuanlan.zhihu.com/p/2068600594906997994 | CN hands-on review (403 on fetch) |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 10 threads │ ~900+ points │ ~300+ comments
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: 0 on-topic posts retrieved (search attempted, no direct post access)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~55 pages │ 🇯🇵 ~18 │ 🇨🇳 ~14
└─ 🗣️ Top voices: Meta AI (Muse Code launch), Prime Intellect (Prime Agent), tech-noisy.com 🇯🇵, UU AI Hub 🇨🇳
```

---

## Out of Scope but Notable

- **majiayu000/harness** (GitHub): Rust control plane for fleets of parallel Claude Code + Codex agents — governance, orchestration, policy, cross-agent review, observability. Not a standalone agent harness (it governs other harnesses), but close to this topic boundary. ([link](https://github.com/majiayu000/harness))
- **smol minimalist system** mentioned in HN "Building Advanced Agentic Harness" (127 pts) thread: unnamed ("smol") counter-framing where minimalist systems benchmark cheaper+faster than orchestrated harnesses on same tasks. May be a new project; couldn't find separate repo. ([link](https://news.ycombinator.com/item?id=49182946))
- **DemoEvolve** (arXiv:2605.24539): overcoming sparse feedback in agentic harness evolution with demonstrations — adjacent to AutoHarness; found during AutoHarness search. Potential paradigm drift: auto-harness synthesis from demonstration rather than environment feedback. ([link](https://arxiv.org/pdf/2605.24539))
- **CN developer concern:** Three competing inter-agent protocols (MCP, A2A, AG-UI) with no interoperability plan — this is a genuine new structural risk to the harness ecosystem that no single briefing topic owns. ([link](https://pengjiyuan.github.io/articles/agent-protocol-ecosystem-2026/)) 🇨🇳

---

## Data Gaps

- **Reddit/X/TikTok/Instagram:** Not accessed — social signal on Meta Muse Code and Prime Agent launches missing
- **Bluesky:** SOURCE HEALTH bluesky=OK, but no on-topic posts retrieved via DDG search; MCP Sky feed not directly accessed
- **YouTube:** Not accessed — Meta Muse Code demo video and Prime Agent walkthroughs unavailable
- **Polymarket:** No markets on this topic
- **Zhihu Muse Code hands-on review:** 403 Forbidden on fetch (https://zhuanlan.zhihu.com/p/2068600594906997994)
- **AQ (aq.dev):** Limited public info; no launch post found; commercial product with minimal documentation
- **Implement-spec HN post (49168675):** Deleted/inaccessible — content lost
- **OpenClaw latest release:** No Aug 5-7 specific release found; last known was v2026.7.2-beta.7 (Aug 2) from prior cycle
- **Prime Agent pricing:** Not disclosed in official materials
- **No SOURCE HEALTH DOWN backends** reported in topic prompt — all passes attempted
- **Approximate coverage:** 72% — HN + English web comprehensive; JP/CN passes good coverage on Muse Code; social signals (Reddit/X/Bluesky) absent; Prime Agent CN/JP coverage not yet developed (too new for deep localization)

---

## Key Quotes

> "Long-running sessions no longer refuse new agents." — Claude Code v2.1.224 release note, on removal of 200-subagent spawn cap ([link](https://code.claude.com/docs/en/changelog)) 🌐

> "Meta co-trained the model with Muse Code itself, using rejection-sampled harness trajectories — meaning the model was explicitly tuned to perform best inside this particular tool." — VentureBeat ([link](https://venturebeat.com/orchestration/meta-enters-the-ai-coding-wars-with-muse-spark-1-2-and-muse-code-with-persistent-async-background-agents)) 🌐

> "Prime Agent is an open-source, MIT-licensed self-improving harness — a framework you install locally and point at whatever model you already pay for." — OrcaRouter ([link](https://www.orcarouter.ai/blog/prime-agent-vs-meta-muse-code-terminal-coding-agent)) 🌐

> "The Continual Harness treats the harness's own state — prompts, skills, memory, and sub-agents — as something the agent can create, read, update, and delete from its own trajectory." — Prime Intellect blog ([link](https://www.primeintellect.ai/blog/prime-agent)) 🌐

> 🇯🇵「Claude CodeまたはCodexのCLI設定を1コマンドでHermes側に取り込むことができ、移行コストが大幅に下がった」
> ("You can bring in Claude Code or Codex CLI settings to Hermes with a single command, dramatically reducing migration cost") — tech-noisy.com ([link](https://tech-noisy.com/2026/08/04/claude-code-codex-migration-hermes-agent/)) 🇯🇵

> 🇯🇵「エージェントの完了品質を向上させるには、プロダクトコードではなくHarness設定を改善する」
> ("To improve agent output quality, optimize the surrounding environment rather than the product code") — Qiita/hisaho ([link](https://qiita.com/hisaho/items/3e1a29bc8b265616614f)) 🇯🇵

> 🇨🇳「科技巨头全部到齐」
> ("All major tech companies have entered the arena") — UU AI Hub on Muse Code launch ([link](https://www.uuaihub.com/blog/meta-muse-code-coding-agent)) 🇨🇳

> 🇨🇳「MCP协议从2025年的新概念发展为2026年AI开发的事实标准」
> ("MCP protocol evolved from a new concept in 2025 to the de facto standard for AI development in 2026") — Juejin ([link](https://juejin.cn/post/7651426279837171764)) 🇨🇳

> "Copilot Studio GitHub Copilot Harness bills credits from the first test." — Windows Forum ([link](https://windowsforum.com/windows-news.4/copilot-studio-github-copilot-harness-bills-credits-from-first-test.441648/)) 🌐
