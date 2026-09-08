# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-09-08
**Query type:** GENERAL
**Sources:** Hacker News, GitHub Trending, Releasebot, Web (global), Web (Japan), Web (China), WebSearch

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | 🌐 Excluded per rules |
| X/Twitter | — | — | 🌐 Excluded per rules |
| YouTube | — | — | Not accessed |
| Hacker News | 1 thread | 190 pts, 93 comments | 🌐 OpenChamber ADE (#49233448) |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; no on-topic Sep 5–8 posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~65 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | ~12 pages | — | 🇯🇵 Qiita (5), Zenn (4), note (1), SBBit (1), Hatena (1); DDG CAPTCHA-blocked |
| Web (China) | ~9 pages | — | 🇨🇳 Zhihu (4), CSDN/AtomGit (3), Tencent Cloud (1), BAAI (1) |

---

## Synthesized Findings

### 1. [update] Claude Code v2.1.261 (Sep 5): /skill-doctor, Org Policy Diagnostics, 128K Inline Output 🌐

**New fact:** v2.1.261 ships `/skill-doctor` — shows each loaded skill, whether it was used, and its context cost — making skill bloat visible for the first time.
- **`/skill-doctor`:** identify unused skills + their context cost; actionable harness trimming
- **`bashOutputMaxChars` / `taskOutputMaxChars`:** raise inline output cap to 128K chars before saving to file
- **`--append-subagent-system-prompt-file`:** read subagent system prompt from file (composable harness config)
- **Org policy diagnostics:** `/status` and `claude doctor` now explain why an org policy failed to load
- **timeFormat / timeZone settings:** 12h, 24h, 24h UTC, or strftime pattern for turn-end clock
- Follows v2.1.260 (Sep 4): fullscreen diff `/diff`, headless `/reload-plugins`, text-based `/advisor`

**Sources:** https://releasebot.io/updates/anthropic/claude-code · https://code.claude.com/docs/en/changelog · https://www.gradually.ai/en/changelogs/claude-code/ · https://www.havoptic.com/tools/claude-code · https://clockedcode.com/blog/claude-code-changelog

---

### 2. [update] OpenClaw v2026.9.1: Mermaid in Chat, Personal Skill Libraries, Android Expansion 🌐🇯🇵🇨🇳

**New facts:** Mermaid diagrams now render in all OpenClaw surfaces; skill libraries decouple from team workspaces; 281 contributors across 1,186 PRs.
- **Mermaid diagrams:** render in Control UI + macOS/iOS/Android with enlarge preview and retry-on-fail
- **Personal skill libraries:** `openclaw skills library`; import from ZIP; share per identity on team Gateways — personal toolkit no longer tangled with shared workspace set
- **Faster onboarding:** detects existing Claude Code/Codex logins and API keys; verifies live; opens dashboard from foreground Gateway
- **Android full parity:** full-width composer, searchable model controls, native session creation + browsing
- **Safer updates:** rolls back npm candidate when post-update Doctor fails; triage agent handles failures
- **Startup recovery:** malformed legacy cron rows quarantined; migration warnings degrade instead of refusing start
- **Fable 5.1 in catalogs:** `claude-fable-5-1` now selectable; Codex shows effort levels per account
- 🇯🇵 JP community: Zenn/sbbit article argues "OpenClaw is no longer needed" — Claude Code's 9 work-agent features sufficient for business users; enterprise still adopts OC for orchestration
- 🇨🇳 CN framing: "三角博弈" (CC/OC/Hermes) persists; OC framed as most mature plugin ecosystem

**Sources:** https://releasebot.io/updates/openclaw · https://releases.sh/openclaw · https://docs.openclaw.ai/releases/2026.9.1 · https://www.gradually.ai/en/changelogs/openclaw/ · https://aisuccesslabjuliangoldie.com/blog/openclaw-2026-9-1-update/ · https://www.sbbit.jp/article/cont1/183699

---

### 3. [update] Hermes Agent v0.21.1 (v2026.9.7, Sep 7): First Patch Since 'Pantheon' 🌐

**New fact:** v0.21.1 released Sep 7 — 5,139 non-merge commits, 632 merged PRs since v0.21.0 (Aug 31).
- **Scope:** codebase modularization; file-op + startup perf; provider/model updates; desktop session controls; browser annotations; MCP auth improvements; cron fixes; delegation reliability
- v0.22.0 will carry comprehensive feature documentation; v0.21.1 is consolidation patch
- Update: `hermes update` or `pip install -U hermes-agent`

**Sources:** https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.7 · https://www.gradually.ai/en/changelogs/hermes-agent/ · https://hermesatlas.com/guide/ · https://freedom.tech/posts/2026-09-07-hermes-agent-0-21-1/

---

### 4. [update] Copilot Studio GitHub Harness GA (Sep 1 billing, Aug 3 tech): Three Harness Types + Human Approval Gates 🌐

**New facts:** Billing enforcement began Sep 1; human approval gates and Work IQ integration ship alongside GA.
- **Three harnesses in Copilot Studio:** Copilot Chat, Standard, GitHub Copilot — each suited to different use cases
- **GitHub Copilot harness:** code execution + reasoning loops + tool orchestration; requests now via OpenAI infrastructure (not MS Azure OpenAI)
- **Human approval gates:** per specific agent tool before execution — deterministic guardrail for high-stakes actions
- **Credential safety detection:** auto-prevents unsafe credential sharing by agents
- **Skills:** modular, reusable instructions shareable across agents (same SKILL.md standard)
- **Work IQ:** agents connected to org emails, calendars, files
- **Billing:** agents/workflows created before Aug 3 began consuming Copilot Credits Sep 1
- **Copilot App parallel agent sessions (Sep 3):** multiple tasks in separate Git worktrees, own context, unified monitoring view
- **GPT-6 Astra** now available in Copilot Cowork/Studio/GitHub Copilot/Foundry (joined Fable 5.1)

**Sources:** https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/new-and-improved-github-copilot-harness-agent-skills-and-richer-context/ · https://www.bighatgroup.com/blog/copilot-weekly-2026-09-07/ · https://pupuweb.com/mc1446644-microsoft-copilot-studio-github-copilot-harness-now-generally-available-for-building-autonomous-agents-and-workflows/ · https://github.blog/ai-and-ml/github-copilot/github-copilot-app-for-beginners-run-several-agents-at-once/ · https://blockchain.news/news/github-copilot-parallel-agent-sessions

---

### 5. [new] GPT-6 Astra's Provider Adapter Harness: 62.7% → 99.9% ARC-AGI-3 Gap Is Pure Harness Engineering 🌐🇯🇵

**Claim:** Same GPT-6 Astra model achieves 62.7% on standard harness vs 99.9% on OpenAI's Provider Adapter harness — the most dramatic documented evidence that harness choice outweighs model choice on benchmark outcomes.
- **What Provider Adapter does:** preserves opaque reasoning state across turns + implements context compaction — no external tools, no MCP, no retrieval
- **Terminal-Bench 4.0:** Astra 57.9% vs Fable 5.1's 55.8% (tight, same order of magnitude — model parity)
- **Standard ARC-AGI-3:** Astra 62.7% vs Claude Opus 5 30.2% — model difference
- **ARC-AGI-3 with Provider Adapter:** 99.9% — harness difference
- **JP community insight** (Qiita/sukimaengineer): "ハーネス = モデル以外のすべて"; "LLM は MCP を知らない" — LLM just decides WHAT, harness handles everything else including MCP translation; Provider Adapter demonstrates cross-turn state is a harness feature, not a model feature
- **Structured notes** for long Codex sessions: searchable requirements across extended context instead of lossy compression
- HARNESS ANGLE (not model release): the benchmark gap is the finding; the model belongs to open-models-geopolitics

**Sources:** https://openai.com/index/gpt-6-astra/ · https://simonwillison.net/2026/Sep/3/gpt6-astra/ · https://9to5mac.com/2026/09/04/openai-releasing-major-upgrade-to-chatgpt-and-codex-with-gpt-6-astra-details-here/ · https://www.datacamp.com/blog/gpt-6-astra · https://qiita.com/sukimaengineer/items/d74337e14a5c5815fa9c · https://zenn.dev/kotoda_ma/articles/07321e3dc01318

---

### 6. [new] gstack (garrytan/gstack, MIT, 132k stars): Garry Tan's 23-Skill Virtual Engineering Team for Claude Code 🌐

**Claim:** gstack turns Claude Code into a virtual software company — 23 role-specialized skills producing CEO-level product review, QA-level browser testing, and security audits in a structured sprint loop. 132k stars makes it one of the highest-starred pure-skill repos.
- **Roles:** CEO (/office-hours, /plan-ceo-review), Designer (/design-shotgun, /design-html), Eng Manager (/plan-eng-review), QA (/qa), Security (/cso: OWASP + STRIDE), Release Eng (/ship, /land-and-deploy, /canary, /document-release)
- **Sprint loop:** Think → Plan → Build → Review → Test → Ship → Reflect
- **Browser integration:** Aside browser or bundled Chromium fallback
- Garry Tan: 10K LOC + 100 PRs/week for 50 days using gstack + Claude Code
- Released March 2026; 39k stars in 11 days; trending Sep 4 (+300 stars on that day)
- Real commits to repo — teammates just run setup once

**Sources:** https://github.com/garrytan/gstack · https://gstacks.org/ · https://pub.towardsai.net/gstack-garry-tans-claude-code-setup-that-turns-one-developer-into-a-full-engineering-team-2026-02854a569730 · https://www.augmentcode.com/learn/garry-tan-gstack-claude-code

---

### 7. [new] Graphify-Labs/graphify (YC S26, 115.4k stars): /graphify Skill Converts Codebase to Queryable Knowledge Graph 🌐

**Claim:** Graphify replaces grep-and-read with a deterministic knowledge graph — 1.7k tokens answers a billing codebase question vs 123k for naive file reads.
- **Mechanism:** tree-sitter AST parsing (37+ languages, zero LLM calls, no data leaves machine) + optional semantic extraction for docs/PDFs via configurable LLM backend
- **Not a vector index:** a real labeled graph; edges tagged EXTRACTED (explicit in source) vs INFERRED (resolved by graphify)
- **Token savings:** 1.7k vs 123k tokens per complex codebase query
- **Install:** `/graphify` in Claude Code, Cursor, Codex, Gemini CLI, 20+ assistants
- **Companion:** `Graphify-Labs/code-review-graph` for self-updating review knowledge

**Sources:** https://github.com/Graphify-Labs/graphify · https://graphify.com/ · https://dev.to/terminalchai/graphify-turn-codebases-into-knowledge-graphs-to-slash-ai-token-costs-3lfb · https://www.mindstudio.ai/blog/graphify-knowledge-graph-ai-agent · https://www.alphamatch.ai/blog/graphify-knowledge-graph-ai-coding-2026

---

### 8. [new] atlas (pacifio/atlas, 3.3k stars): Source Control for Agents — Checkpoints Link Commits to Prompts 🌐

**Claim:** Atlas closes the provenance gap: every agent commit links back to the exact prompts, tool calls, reasoning, and file changes that created it — queryable months later.
- **Checkpoint system:** commits → prompt + tool calls + reasoning + file changes; semantic search via on-device HNSW
- **Shared memory:** one on-device knowledge base across Claude Code, Codex, OpenCode, and any ACP agent
- **Local-first:** accounts + syncing optional
- **@-mentions:** files, folders, notes, past sessions resolved locally before sending to agents
- **Integrated workspace:** editor + git + terminal + knowledge base + research tools
- Trending Sep 4 (+419 stars); 3.3k total

**Sources:** https://github.com/pacifio/atlas · https://www.tryatlas.cc/ · https://www.coddykit.com/pages/blog-detail?id=513051

---

### 9. [new] nodeterm (eneskirca/nodeterm, 1.8k stars): Parallel Agent Sessions on Pan/Zoom Canvas 🌐

**Claim:** nodeterm surfaces parallel AI coding sessions as draggable nodes on an infinite canvas — spatial layout instead of hidden tabs; persistent across reboots.
- **Canvas model:** terminals + agent sessions + notes + diffs as movable nodes on pan/zoom canvas
- **Status badges:** RUNNING (pulsing), NEEDS YOU (waiting on input), live subagent fan-outs, completion notifications
- **Persistence:** tmux-backed; all terminals restored after reboot including scrollback + agent sessions
- **Agents:** Claude Code, Codex, Gemini, OpenCode via their real CLIs
- **Dual view:** canvas or Trello-style kanban board per project
- **Platforms:** macOS/Linux/Windows (beta); self-hosted Server Edition (browser); iOS companion
- **Voice:** on-device Whisper transcription
- v0.3.4 (Aug 30); early access

**Sources:** https://github.com/eneskirca/nodeterm · https://nodeterm.dev/ · https://www.abdulazizahwan.com/2026/09/nodeterm-review-ai-coding-agents.html · https://www.producthunt.com/products/nodeterm-terminal-manager

---

### 10. [new] Paseo (getpaseo/paseo, 16k stars): Multi-Provider Orchestration — 31+ Agents from Anywhere 🌐

**Claim:** Paseo runs 31+ coding agents from desktop, mobile, web, and CLI — each using its native CLI and credentials — with pipeline/fan-out/supervisor orchestration patterns.
- **Model:** daemon (Node.js) manages agent processes; streams via WebSocket; clients connect locally or remotely
- **Agents:** Claude Code, Codex, OpenCode, Pi, GitHub Copilot, 31+ more
- **Multi-agent patterns:** pipeline, fan-out, supervisor with context isolation
- **Mobile:** control agents from phone
- **`/paseo-handoff`:** skill for handing work between agents
- Mentioned in OpenChamber HN thread (190 pts) as preferred alternative for multi-provider support
- 16k stars; actively maintained to Aug 17 2026

**Sources:** https://github.com/getpaseo/paseo · https://paseo.sh/ · https://vibecodinghub.org/blog/paseo-review · https://paseo.sh/alternatives/openchamber

---

### 11. [new] OpenCode v2 Beta: Bun→Node, Tauri→Electron, Published HTTP API, Parallel Sessions 🌐

**Claim:** OpenCode v2 is a ground-up rewrite with a public HTTP API client, multi-tab parallel AI sessions, and a new plugin architecture — ships as `opencode2` alongside v1.
- **Infrastructure:** Bun → Node (memory issue fix); Tauri → Electron (desktop)
- **HTTP API** (`@opencode-ai/client@next`): sessions, history, event streams, providers, permissions, PTY, shell, skills, MCP, VCS; same server backing TUI and desktop app
- **Plugin API:** `setup()` function; V1+V2 bridge for backward compat
- **Parallel AI sessions:** multiple tabs, own context per tab
- **Azure:** sign in via Azure CLI (Entra ID) — no API key required
- **v1.18.29 (Sep 4):** Codex OAuth model filter fixes gpt-6-astra not showing for OpenAI subscription users

**Sources:** https://opencode.ai/v2/docs/ · https://www.kucoin.com/news/flash/opencode-2-0-major-rewrite-api-overhaul-node-migration-and-electron-desktop-shift · https://releasebot.io/updates/sst/opencode · https://opencode.ai/changelog

---

### 12. [new] magnitude (magnitudedev/magnitude, 3.3k stars): Local Inference Server That Plugs Into Any Agent 🌐

**Claim:** magnitude profiles your hardware, recommends best-fit local models, downloads GGUF quantizations, and serves them to whichever coding agent you already use — no API costs, no data leaving machine.
- **Hardware profiling:** scans system → recommends models with estimated tokens-per-second
- **Smart downloads:** GGUF quantized formats; bounded extraction (prevents malicious archives)
- **Agent integration:** Pi, OpenCode, Hermes, OpenClaw, Codex, Claude Code, Oh My Pi, Cline
- **Latest:** @magnitudedev/cli@0.0.11 (Sep 2); GitHub Trending Sep 6 (+674 stars); 3.3k total

**Sources:** https://github.com/magnitudedev/magnitude · https://magnitude.dev/ · https://www.coddykit.com/pages/blog-detail?id=513062 · https://startupcorners.com/digest/devtools-digest-2026-09-06

---

### 13. [new] Graphify, gstack, atlas, nodeterm, Paseo — Five Trending Infrastructure Layers for Agent Harnesses 🌐

Combines findings 6-10 as a pattern: five new tools discovered this cycle all target a specific layer ABOVE the agent harness rather than replacing it.
- **gstack:** role layer (skills that add job-function discipline to Claude Code sessions)
- **Graphify:** context layer (codebase as graph; 98% token reduction vs grep-and-read)
- **atlas:** provenance layer (links every commit to the prompts+reasoning that created it)
- **nodeterm:** spatial UX layer (parallel sessions on infinite canvas)
- **Paseo:** orchestration layer (31+ agents from any device via their native CLIs)
- **Context-mode:** compression layer (98% tool output reduction; 17 platforms via MCP+hooks)
- Pattern: the harness market is bifurcating into thin runtimes + specialist infrastructure layers, not thicker monoliths

---

**Still true** (ongoing threads, no new facts Sep 5–8):

- `hermes-agent-self-improving` — v0.21.1 patch released Sep 7 (see finding 3)
- `meta-muse-code` — no new Muse Code releases Sep 5–8; Muse Spark 1.3 (Sep 3) remains latest
- `colibri-lumabri-moe-inference` — no new facts this cycle
- `omarchy-herdr-agentic-linux` — no new facts
- `agensi-skill-marketplace` — no new facts
- `kilo-code-anaconda` — no new facts
- `harness-io-agent-ready-scm` — no new facts
- `extension-economy-explosion` — claudemarketplaces.com counts unchanged (23,600+/12,800+/2,700+); anthropics/skills now 175k stars
- `addy-osmani-agent-skills` — no new facts
- `orca-ade-parallel-fleet` — stablyai/orca trending Sep 4 (+914 stars); no release news
- `ponytail-laziest-dev-skill` — no new facts
- `trueforge-open-source-harness` — no new facts
- `vscode-1135-external-agent-sessions` — no new facts (1.136 still latest)
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
- `deepseek-harness-v01` — no new facts (209k stars; may have grown further)
- `cursor-router-workspace-plugins` — no new facts
- `agent-plugins-1-standard` — Agent Plugins 1.0.0 spec detail confirmed; 9 clients
- `anthropic-managed-agents-mcp-tunnels` — see finding 1 (v2.1.261)
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
- `copilot-studio-ga-harness-billing` — see finding 4 (human approval gates, billing enforcement Sep 1)
- `microsoft-agent-governance-toolkit` — no new facts
- `tinyagents-rust-recursive` — no new facts
- `sprocket-hardware-software-agent` — no new facts
- `gambit-reliable-agent-harness` — no new facts
- `nlah-natural-language-harnesses` — no new facts
- `skills-security-prompt-injection-36pct` — no new facts
- `claude-tag-slack-agent` — no new facts
- `mimo-code-xiaomi` — no new facts
- `ecc-cross-harness-os` — no new facts
- `kimi-code-moonshot` — no new facts
- `runtime-yc-p26` — no new facts
- `noclick-always-on` — no new facts
- `nyx-offensive-testing` — no new facts
- `agentguard-security-tool` — no new facts
- `mcp-security-nsa-supply-chain` — no new facts
- `yc-qm-multiplayer-harness` — no new facts
- `mcp-stateless-spec-2026-07-28` — Agent Plugins 1.0.0 (9 clients) reinforces this thread
- `jadepuffer-agentic-security` — no new facts
- `grok-build-xai-rust-harness` — no new facts
- `self-harness-auto-optimization` — GPT-6 Astra Provider Adapter (finding 5) is new practical evidence
- `openharness-hkuds` — no new facts
- `antigravity-gemini-cli-successor` — no new facts
- `claw-code-claude-rewrite` — no new facts
- `metaharness-scaffold-generator` — no new facts
- `harness-engineering-paradigm` — GPT-6 Astra harness gap (finding 5) + gstack (finding 6) reinforce
- `deerflow-superagent-harness` — no new facts
- `omnigent-meta-harness` — no new facts
- `zot-go-coding-harness` — no new facts
- `omp-omo-pi-derivatives` — oh-my-pi trending Sep 6 (+201 stars); no release news
- `yorishiro-presence-harness` — no new facts
- `agentskills-open-standard` — anthropics/skills now 175k stars; Agent Plugins 1.0.0 detail confirmed
- `letta-agent-file-format` — no new facts
- `layered-oss-stack-over-single-framework` — findings 6-13 (gstack/Graphify/atlas/nodeterm/Paseo) reinforce the layered OSS pattern
- `macos-harness-proving-ground` — no new facts
- `ahe-automated-harness-evolution` — no new facts
- `harness-internal-external-disambiguation` — Qiita/nogataka article (JP) reinforces: inner vs outer harness terminology
- `environment-architect-new-role` — no new facts
- `warp-oz-multi-harness` — no new facts
- `mozilla-otari-llm-gateway` — no new facts
- `statewright-guardrails` — no new facts
- `headroom-token-compression` — no new facts
- `pi-minimal-agent-harness` — pi trending Sep 4 (+493) and Sep 6 (+320); no release news
- `nvidia-skillspector-security` — SkillSpector trending Sep 6 (+166 stars)
- `deepseek-harness-team` — no new facts
- `cli-anything-hkuds` — no new facts
- `forge-acp-universal-cli` — no new facts
- `github-copilot-skills-mcp-ga` — see finding 4 (Copilot Studio GitHub Harness GA)
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
- `vscode-1136-agent-merge` — no new facts (1.136 still latest)
- `sonar-vortex-inside-loop` — no new facts
- `devspace-minimal-mcp-harness` — no new facts
- `skills-over-mcp-wg-sep2640` — no new facts
- `accuknox-agentz-enterprise` — no new facts
- `harness-context-tax-problem` — GPT-6 Astra Provider Adapter harness (finding 5) is new evidence; Graphify's 1.7k vs 123k token comparison (finding 7) is new quantification

---

## Cross-Source Patterns

### Pattern 1: Harness Choice Now Dominates Model Choice on Benchmarks 🌐🇯🇵
**Platforms:** OpenAI, Qiita, Zenn, Simon Willison, DataCamp, CNBC
**Signal:** GPT-6 Astra's 62.7% vs 99.9% ARC-AGI-3 gap — same model, different harness — is the sharpest demonstration yet that harness engineering outweighs model selection at the frontier. JP community (Qiita/sukimaengineer) crystallized this: "ハーネス = モデル以外のすべて." The same pattern seen earlier with Lilian Weng's minimalist harness beating complex ones (HN 334 pts, Jul 4) now has a quantitative frontier-model datapoint: 37pp difference from cross-turn state + compaction alone.
**Quote:** "ハーネス = モデル以外のすべて" ("The harness = everything besides the model") — @sukimaengineer on Qiita ([link](https://qiita.com/sukimaengineer/items/d74337e14a5c5815fa9c)) 🇯🇵

### Pattern 2: Bifurcation Into Thin Runtimes + Specialist Infrastructure Layers 🌐
**Platforms:** GitHub Trending (Sep 4 + 6), HN, WebSearch
**Signal:** Five new infrastructure tools discovered this cycle (gstack, Graphify, atlas, nodeterm, Paseo) each target a specific layer above existing thin runtimes rather than replacing the runtime. Plus context-mode (98% output compression) and magnitude (local inference). This is distinct from the prior "monolithic harness" model — the market is organizing into a composable stack where each layer solves one problem well. Combined with the prior layered-oss-stack-over-single-framework thread (AURA, Munder Difflin, etc.), this is now the dominant structural pattern.

### Pattern 3: OpenClaw's Harness Complexity Becoming Its Own Threat 🌐🇯🇵
**Platforms:** SBBit (JP), Zenn, Qiita
**Signal:** The JP community is explicitly re-evaluating whether OpenClaw complexity is still worth it. SBBit headline: "OpenClawはもう不要？Claude Codeを最強仕事エージェントに変えた9つの神機能." This mirrors the Zenn/icare security CVE concern from prior runs but extends it: now it's not just security cost but the whole orchestration overhead. OC v2026.9.1 (personal skill libraries, safer updates) is a direct response — simplifying OC for individual developers.

### Pattern 4: 🇯🇵🇨🇳 Community Signals — Convergent Focus on Stack Economics
- 🇯🇵: GPT-6 Astra's harness gap is the main story; RIZAP breach reinforces "don't use unapproved AI tools" message for enterprises
- 🇨🇳: "三角博弈" (CC/OC/Hermes) framing stable; CN community uniquely tracks Hermes as "only harness with closed-loop self-learning"; domestic CN agents still lack model-swap + own-API-key capabilities

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| hexomancer | OpenChamber: An Agentic Development Environment | 190 | 93 | "Paseo is the better alternative — works with multiple agent harnesses" | https://news.ycombinator.com/item?id=49233448 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Claude Code Releasebot | https://releasebot.io/updates/anthropic/claude-code | v2.1.261 (Sep 5): /skill-doctor, bashOutputMaxChars |
| 🌐 | Claude Code Docs | https://code.claude.com/docs/en/changelog | Official changelog |
| 🌐 | gradually.ai Claude Code | https://www.gradually.ai/en/changelogs/claude-code/ | Sep tracker |
| 🌐 | Havoptic Claude Code | https://www.havoptic.com/tools/claude-code | Release summaries |
| 🌐 | ClockedCode Changelog | https://clockedcode.com/blog/claude-code-changelog | Plain English changelog |
| 🌐 | claudefa.st Changelog | https://claudefa.st/blog/guide/changelog | Aggregator |
| 🌐 | OpenClaw Releasebot | https://releasebot.io/updates/openclaw | v2026.9.1 details |
| 🌐 | OpenClaw releases.sh | https://releases.sh/openclaw | Full changelog |
| 🌐 | OpenClaw Docs | https://docs.openclaw.ai/releases/2026.9.1 | Official release |
| 🌐 | gradually.ai OpenClaw | https://www.gradually.ai/en/changelogs/openclaw/ | Sep tracker |
| 🌐 | AI Success Lab OC | https://aisuccesslabjuliangoldie.com/blog/openclaw-2026-9-1-update/ | What's new analysis |
| 🌐 | Hermes v0.21.1 GitHub | https://github.com/NousResearch/hermes-agent/releases/tag/v2026.9.7 | Sep 7 patch release |
| 🌐 | gradually.ai Hermes | https://www.gradually.ai/en/changelogs/hermes-agent/ | Sep tracker |
| 🌐 | Hermes Atlas guide | https://hermesatlas.com/guide/ | Beginner's guide |
| 🌐 | Freedom.tech Hermes | https://freedom.tech/posts/2026-09-07-hermes-agent-0-21-1/ | Sep 7 coverage |
| 🌐 | Copilot Weekly Sep 7 | https://www.bighatgroup.com/blog/copilot-weekly-2026-09-07/ | Harness GA + GPT-6 Astra |
| 🌐 | MS Copilot Studio blog | https://www.microsoft.com/en-us/microsoft-copilot/blog/copilot-studio/new-and-improved-github-copilot-harness-agent-skills-and-richer-context/ | GitHub Harness GA official |
| 🌐 | pupuweb MC1446644 | https://pupuweb.com/mc1446644-microsoft-copilot-studio-github-copilot-harness-now-generally-available-for-building-autonomous-agents-and-workflows/ | GA announcement |
| 🌐 | GitHub Copilot parallel | https://github.blog/ai-and-ml/github-copilot/github-copilot-app-for-beginners-run-several-agents-at-once/ | Parallel sessions Sep 3 |
| 🌐 | Blockchain.news parallel | https://blockchain.news/news/github-copilot-parallel-agent-sessions | Sep 3 coverage |
| 🌐 | OpenAI GPT-6 Astra | https://openai.com/index/gpt-6-astra/ | Official; Sep 3 |
| 🌐 | Simon Willison Astra | https://simonwillison.net/2026/Sep/3/gpt6-astra/ | Analysis |
| 🌐 | 9to5Mac Astra | https://9to5mac.com/2026/09/04/openai-releasing-major-upgrade-to-chatgpt-and-codex-with-gpt-6-astra-details-here/ | Sep 4 coverage |
| 🌐 | DataCamp Astra | https://www.datacamp.com/blog/gpt-6-astra | Features + benchmarks |
| 🌐 | CNBC Astra | https://www.cnbc.com/2026/09/03/open-ai-astra-gpt-6-cyber.html | News coverage |
| 🌐 | GitHub garrytan/gstack | https://github.com/garrytan/gstack | 132k stars; 23 skills |
| 🌐 | gstacks.org | https://gstacks.org/ | Product page |
| 🌐 | TowardsAI gstack | https://pub.towardsai.net/gstack-garry-tans-claude-code-setup-that-turns-one-developer-into-a-full-engineering-team-2026-02854a569730 | Full analysis |
| 🌐 | AugmentCode gstack | https://www.augmentcode.com/learn/garry-tan-gstack-claude-code | Analysis |
| 🌐 | GitHub Graphify | https://github.com/Graphify-Labs/graphify | 115.4k stars |
| 🌐 | graphify.com | https://graphify.com/ | Product page |
| 🌐 | DEV Graphify token costs | https://dev.to/terminalchai/graphify-turn-codebases-into-knowledge-graphs-to-slash-ai-token-costs-3lfb | 1.7k vs 123k tokens |
| 🌐 | MindStudio Graphify | https://www.mindstudio.ai/blog/graphify-knowledge-graph-ai-agent | How to use |
| 🌐 | AlphaMatch Graphify | https://www.alphamatch.ai/blog/graphify-knowledge-graph-ai-coding-2026 | Analysis |
| 🌐 | GitHub pacifio/atlas | https://github.com/pacifio/atlas | 3.3k stars; source control for agents |
| 🌐 | tryatlas.cc | https://www.tryatlas.cc/ | Product page |
| 🌐 | CoddyKit atlas | https://www.coddykit.com/pages/blog-detail?id=513051 | 888 stars in single day |
| 🌐 | GitHub nodeterm | https://github.com/eneskirca/nodeterm | 1.8k stars; node canvas |
| 🌐 | nodeterm.dev | https://nodeterm.dev/ | Product page |
| 🌐 | Abdul Aziz nodeterm review | https://www.abdulazizahwan.com/2026/09/nodeterm-review-ai-coding-agents.html | Full review |
| 🌐 | Product Hunt nodeterm | https://www.producthunt.com/products/nodeterm-terminal-manager | Launch |
| 🌐 | GitHub getpaseo/paseo | https://github.com/getpaseo/paseo | 16k stars; multi-provider |
| 🌐 | paseo.sh | https://paseo.sh/ | Product page |
| 🌐 | VibeCodeHub paseo | https://vibecodinghub.org/blog/paseo-review | Review |
| 🌐 | Paseo alternatives | https://paseo.sh/alternatives/openchamber | vs OpenChamber |
| 🌐 | HN OpenChamber | https://news.ycombinator.com/item?id=49233448 | 190 pts, 93 comments |
| 🌐 | GitHub openchamber | https://github.com/openchamber/openchamber | ADE for OpenCode |
| 🌐 | openchamber.dev | https://openchamber.dev/ | Product page |
| 🌐 | GitHub magnitude | https://github.com/magnitudedev/magnitude | 3.3k stars; local inference |
| 🌐 | magnitude.dev | https://magnitude.dev/ | Product page |
| 🌐 | CoddyKit magnitude | https://www.coddykit.com/pages/blog-detail?id=513062 | 3,300+ stars coverage |
| 🌐 | OpenCode v2 docs | https://opencode.ai/v2/docs/ | V2 rewrite documentation |
| 🌐 | KuCoin OpenCode 2.0 | https://www.kucoin.com/news/flash/opencode-2-0-major-rewrite-api-overhaul-node-migration-and-electron-desktop-shift | V2 coverage |
| 🌐 | Releasebot OpenCode | https://releasebot.io/updates/sst/opencode | Sep release tracker |
| 🌐 | GitHub ruflo | https://github.com/ruvnet/ruflo | Meta-harness; 60+ agents; 314 MCP tools |
| 🌐 | GitHub openclaude | https://github.com/Gitlawb/openclaude | 32.7k stars; 200+ backends |
| 🌐 | openclaude.gitlawb.com | https://openclaude.gitlawb.com/ | Product page |
| 🌐 | GitHub context-mode | https://github.com/mksglu/context-mode | 98% tool output reduction |
| 🌐 | claudemarketplaces.com | https://claudemarketplaces.com/ | 23,600+ skills; 12,800+ MCP |
| 🌐 | anthropics/skills | https://github.com/anthropics/skills | 175k stars; official skills repo |
| 🌐 | humanlayer/skills | https://github.com/humanlayer/skills | 3.5k stars; human-in-loop skills |
| 🌐 | GitHub Trending Sep 4 | https://startupcorners.com/digest/devtools-digest-2026-09-04 | orca +914, humanizer +1208 |
| 🌐 | GitHub Trending Sep 6 | https://startupcorners.com/digest/devtools-digest-2026-09-06 | opencode +725, magnitude +674 |
| 🌐 | explainx.ai harness top 10 | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Rankings Sep 2026 |
| 🌐 | CellCog rankings Sep | https://cellcog.ai/blog/best-ai-agent-harnesses/ | CellCog > Claude Code > Codex > Cursor |
| 🌐 | ai-boost/awesome-harness-engineering | https://github.com/ai-boost/awesome-harness-engineering | Awesome list |
| 🌐 | best-of-Agent-Harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked weekly |
| 🇯🇵 | Qiita/sukimaengineer | https://qiita.com/sukimaengineer/items/d74337e14a5c5815fa9c | GPT-6 Astra harness gap; LLM vs harness division |
| 🇯🇵 | Qiita/good-software digest | https://qiita.com/good-software/items/54b7be0aa0a402267960 | AI digest Aug 31–Sep 5 |
| 🇯🇵 | Qiita/nolanlover0527 | https://qiita.com/nolanlover0527/items/f38f36091aa35979fe61 | GPT-6 Astra coverage |
| 🇯🇵 | Qiita/y-morimatsu | https://qiita.com/y-morimatsu/items/6ab84503f4cd7efc6882 | Agent Plugins 1.0.0 explanation |
| 🇯🇵 | Qiita/nogataka | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | Inner vs outer harness terminology |
| 🇯🇵 | Qiita/axzxs2001 | https://qiita.com/axzxs2001/items/718ea9c8d5ecae732783 | 12 core modules of agent harness |
| 🇯🇵 | Zenn/kotoda_ma Astra | https://zenn.dev/kotoda_ma/articles/07321e3dc01318 | GPT-6 Astra overview; benchmark caveat |
| 🇯🇵 | Zenn/muramasa0228 | https://zenn.dev/muramasa0228/articles/2026-06-20-mcp-zenn-pipeline | Claude Code + MCP automates Zenn publishing |
| 🇯🇵 | Zenn/watany disambiguation | https://zenn.dev/watany/articles/d8b692bbca65a3 | Inner vs external harness ongoing |
| 🇯🇵 | Zenn/shunxneuro meta-harness | https://zenn.dev/shunxneuro/articles/93b32512eba7ab | Anthropic meta-harness article JP translation |
| 🇯🇵 | SBBit OpenClaw article | https://www.sbbit.jp/article/cont1/183699 | "OpenClawはもう不要？" — CC as work agent |
| 🇯🇵 | Uravation OC guide | https://uravation.com/media/openclaw-complete-guide-2026/ | Complete OC guide Sep 2026 |
| 🇯🇵 | genai-ai.co.jp | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | CC harness engineering with sub-agents |
| 🇨🇳 | Zhihu CC vs OC architecture | https://zhuanlan.zhihu.com/p/2022939363290489072 | Trust model vs. rule-based constraints |
| 🇨🇳 | Zhihu CC+OC combo guide | https://zhuanlan.zhihu.com/p/2014737146280420263 | Use both: CC writes code, OC manages rest |
| 🇨🇳 | Zhihu agent dev guide | https://zhuanlan.zhihu.com/p/2011920515531548401 | Skills→CLI→MCP three-layer stack |
| 🇨🇳 | CSDN DeepSeek Harness vs | https://blog.csdn.net/aidoudoulong/article/details/163759887 | Harness deep comparison |
| 🇨🇳 | CSDN AI three-pack | https://gitcode.csdn.net/69d9ae2354b52172bc68ab44.html | Hermes+CC+Superpowers comparison |
| 🇨🇳 | Tencent Cloud MCP maturity | https://cloud.tencent.com/developer/article/2653637 | MCP 2025→2026 maturity |
| 🇨🇳 | BAAI OpenClaw analysis | https://hub.baai.ac.cn/view/52922 | OC's explosion and code data value |
| 🇨🇳 | SegmentFault MCP guide | https://segmentfault.com/a/1190000048091574 | MCP from intro to practice 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: excluded per rules
├─ 🔵 X: excluded per rules
├─ 🔴 YouTube: not accessed
├─ 🟢 HN: 1 thread │ 190 pts │ 93 comments (OpenChamber ADE)
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: OK (per SOURCE HEALTH) │ 0 on-topic posts found
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~65 pages │ 🇯🇵 12 │ 🇨🇳 9
└─ 🗣️ Top voices: garrytan (gstack 132k stars), @sukimaengineer JP (GPT-6 harness gap crystallized), OpenAI (Provider Adapter harness 99.9%), pacifio (atlas source control), eneskirca (nodeterm canvas) │ 🇯🇵 Qiita/sukimaengineer (ハーネス=モデル以外のすべて), SBBit (OC必要なし) │ 🇨🇳 CSDN (CC+Hermes+Superpowers top 3)
```

---

## Out of Scope but Notable

- **NVIDIA acquires Hugging Face (~$12.9B, ~Sep 2026):** GPU compute monopoly expanding into model distribution; open operations maintained. Source: https://qiita.com/good-software/items/54b7be0aa0a402267960 — Belongs to open-models-geopolitics; flagged because it directly affects model serving infrastructure (magnitude et al.)

- **astrio-labs/forall (spec-driven coding agent with machine-checkable proofs):** generates spec-driven code alongside formally-verified proofs; a distinct approach from test-driven agents. Source: https://github.com/astrio-labs/forall — Belongs here if it gains traction; currently low-signal.

- **RIZAP data breach (JP, Sep 2026):** fitness company employee uploaded customer data to personal AI service account — first known breach from unapproved employee AI tool use in Japan. Source: https://qiita.com/good-software/items/54b7be0aa0a402267960 — Could belong to an ai-governance topic.

---

## Data Gaps

- **Reddit, X/Twitter, TikTok, Instagram:** excluded per rules; social layer absent (~10% gap)
- **last30days skill:** unavailable (unknown skill error); replaced with WebSearch + WebFetch multi-pass
- **DuckDuckGo HTML endpoint:** CAPTCHA-blocked (4th consecutive run); JP/CN passes used native-language WebSearch
- **Bluesky:** bluesky=OK per SOURCE HEALTH; no on-topic Sep 5–8 posts found during search
- **YouTube:** not accessed this cycle
- **Coverage estimate: 83%** — English web, GitHub Trending, changelogs well covered; JP/CN passes solid (12+9 pages via native WebSearch); HN access limited to 1 findable thread; Reddit/social absent

---

## Key Quotes

> "ハーネス = モデル以外のすべて" ("The harness = everything besides the model") — @sukimaengineer on Qiita, analyzing GPT-6 Astra's 62.7% vs 99.9% ARC-AGI-3 gap ([link](https://qiita.com/sukimaengineer/items/d74337e14a5c5815fa9c)) 🇯🇵

> "LLM は MCP を知らない" ("The LLM doesn't know MCP exists") — @sukimaengineer clarifying MCP's position in the stack: harness translates tool schemas, not the model ([link](https://qiita.com/sukimaengineer/items/d74337e14a5c5815fa9c)) 🇯🇵

> "Where does billing deduct credits?" returns the right files in about 1.7k tokens instead of the 123k a naive grep-and-read would burn — Graphify documentation ([link](https://dev.to/terminalchai/graphify-turn-codebases-into-knowledge-graphs-to-slash-ai-token-costs-3lfb)) 🌐

> "If an agent is going to access production context, call tools, and participate in incident workflows, the harness around it cannot be fragile glue code" — Henry Andrews (Mezmo) on building AURA in Rust ([link](https://www.mezmo.com/blog/builder-in-the-loop-henry-andrews-on-building-aura-like-production-software)) 🌐 (prior cycle, still most quotable on harness reliability)

> "OpenClawはもう不要？Claude Codeを最強仕事エージェントに変えた9つの神機能" ("Is OpenClaw no longer needed? 9 divine features that turn Claude Code into the strongest work agent") — SBBit headline ([link](https://www.sbbit.jp/article/cont1/183699)) 🇯🇵

> "The harness can make as much difference when improved as improvements to the model itself" — HN community discussion on agent harnesses ([link](https://news.ycombinator.com/item?id=48265332)) 🌐

> "2026年最高效的开发者不是在两者中选一个——而是同时使用：Claude Code写代码，OpenClaw管其他一切" ("The most efficient 2026 developers don't choose between them — they use both: Claude Code writes code, OpenClaw manages everything else") — Zhihu comparison guide ([link](https://zhuanlan.zhihu.com/p/2014737146280420263)) 🇨🇳
