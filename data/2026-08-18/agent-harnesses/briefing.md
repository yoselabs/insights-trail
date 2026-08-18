# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-18
**Query type:** GENERAL
**Sources:** Hacker News, Web (global), Web (Japan), Web (China), GitHub, Product Hunt, Releasebot

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | — | — | Not accessed |
| X/Twitter | — | — | Not accessed |
| YouTube | — | — | Not accessed |
| Hacker News | 3 threads | ~898 pts, ~292 comments | Copilot Autofix 381 pts/146 comments; Bullet 117/88; front page scan |
| TikTok | — | — | Not accessed |
| Instagram | — | — | Not accessed |
| Bluesky | 0 posts | — | 🦋 bluesky=OK; 0 on-topic posts found |
| Polymarket | 0 markets | — | None found |
| Web (global) | ~60 pages | — | 🌐 WebSearch + WebFetch; 15+ query passes |
| Web (Japan) | ~12 pages | — | 🇯🇵 WebSearch + WebFetch: Qiita (8), Zenn (2), note (2), genai-ai.co.jp |
| Web (China) | ~16 pages | — | 🇨🇳 WebSearch: Zhihu (2), Tencent News (2), V2EX, Aliyun, openclaw.club, sspai.com, cnblogs, aitoollab.cn, runoob.com, uuaihub, ai-indeed, Electricitysheep/dsh-handbook |

---

## Synthesized Findings

### 1. [new] Copilot Autofix Introduced a Bug; Wiz's Red Agent Exploited It — Dual-AI Security Incident 🌐

**Claim:** Aug 17 — GitHub Copilot Autofix co-authored a script injection flaw into Snowflake's public repo on June 18; Wiz's autonomous Red Agent found and exploited it within 5 days of deployment, exfiltrating internal Jira credentials. HN: 381 pts/146 comments.

**Evidence:**
- **Repo:** snowflakedb/snowflake-connector-net (GitHub Actions workflow)
- **Root cause:** Copilot Autofix replaced safe pattern (environment variables + jq parsing) with direct string expansion in a `run:` block — classic script injection, but automated tooling missed it
- **GitHub Advanced Security:** did NOT detect the flaw; SAST blind to this injection pattern
- **Wiz Red Agent:** discovered and exploited it 5 days after deployment; exfiltrated token authenticating as qa@snowflake.net → access to internal Jira (engineering, security, bug bounty projects)
- **Fix:** Snowflake patched within hours of Wiz's HackerOne report (June 23); PR #1402 replaced direct expansion with env vars + jq
- **Snowflake's statement:** "no evidence of unauthorized access" (despite credential exfiltration)
- **Pattern:** The window between AI-introduced vulnerability and AI-driven exploitation is now measured in days, not months

**Sources:** https://www.wiz.io/blog/red-agent-snowflake-copilot-cicd-bug · https://news.ycombinator.com/item?id=49331423 · https://www.forbes.com/sites/timkeary/2026/08/17/github-copilot-missed-a-vulnerability-that-wizs-ai-agent-found/ · https://www.theregister.com/security/2026/08/17/an-ai-broke-snowflakes-code-then-another-ai-agent-exploited-it/5288666 · https://www.scworld.com/news/wiz-agent-finds-snowflake-repo-flaw-in-code-co-authored-by-github-copilot-autofix · https://thehackernews.com/2026/08/snowflake-github-actions-flaw-lets_0330881554.html · https://www.cyberkendra.com/2026/08/copilot-autofix-snowflake-jira-github-actions.html · https://dev.to/instasla/copilot-autofix-vs-agentic-autofix-managing-ai-driven-vulnerability-patching-4p4h

---

### 2. [new] Bullet (YC S26): "30–60% Faster" Coding Agent via Model Routing + Context Hygiene 🌐

**Claim:** Bullet (YC S26) is a new closed-source coding agent founded by AppLovin/Citadel alumni; claims 95.8% SWE-bench Verified (479/500), 119s/task average, 30–60% faster than Claude Code/Codex via model routing, targeted code search, and aggressive context hygiene.

**Evidence:**
- **HN:** https://news.ycombinator.com/item?id=49283063 — 117 pts/88 comments
- **Product Hunt:** https://www.producthunt.com/products/bullet-6
- **Architecture:** (1) model routing — selects right model/reasoning tier per prompt; (2) grep-based targeted code search (not embedding-entire-repo); (3) context hygiene — bounds tool output, removes stale screenshots, no unnecessary re-reads; (4) parallelizes independent searches/reads/commands
- **Performance claims:** 479/500 SWE-bench Verified (one attempt), avg 119s/task; 16% fewer round trips, 27% lower cost vs. comparable agents
- **Providers:** Claude, Codex, others via API/subscription
- **Skills migration:** imports from Claude Code and Codex
- **HN concerns:** (1) benchmark saturation — critics note SWE-bench Verified may not reflect real-world complexity; (2) root access requirement without visible source code; (3) differentiation longevity
- **Status:** Closed-source; founders considering open-sourcing
- **Builder Radar:** https://buttondown.com/Builder-Radar/archive/builder-radar-week-of-august-16-2026/

---

### 3. [new] book-to-skill (Leutenegger): 12k Stars — PDF Books → Portable Agent Skills 🌐

**Claim:** Leutenegger/book-to-skill (Python, MIT) turns any technical book PDF into a portable SKILL.md agent skill; 12,000+ GitHub stars (1,428 in one day trending), compatible with Claude Code, GitHub Copilot CLI, and Amp.

**Evidence:**
- **GitHub:** https://github.com/Leutenegger/book-to-skill — 12,000+ stars
- **Ranked #11 in GitHub trending week 33** (Qiita weekly summary)
- **How it works:** Distills book into SKILL.md — extracts frameworks, decision rules, anti-patterns; per-chapter files loaded on-demand (don't count against skill budget until queried)
- **Compatibility:** Open Agent Skills standard (SKILL.md) — GitHub Copilot CLI, Amp, Claude Code
- **Security:** Passed SkillsLLM automated scan (no high-severity issues)
- **CoddyKit coverage:** https://www.coddykit.com/pages/blog-detail?id=512975&slug=book-to-skill-the-open-source-tool-with-12-000-github-stars-that-turns-any-techn
- **YouTube:** https://www.youtube.com/watch?v=HQqX4rF1nDM
- **SkillsLLM:** https://skillsllm.com/skill/book-to-skill

---

### 4. [update] Cursor Origin: Agent-First Code Hosting — GitHub Rival Launched During GitHub Outage 🌐

**New facts since Aug 14:** Origin code hosting (beta, Aug 17) — Cursor's own git hosting with GitHub sync; SpaceX acquisition confirmed closed Aug 14; Origin launched 3.5h before a 6h42m GitHub global degradation.

**Evidence — Origin (Aug 17):**
- **What:** Agent-first code hosting platform; beta rollout to all paid plans
- **Features:** native repos, PRs, code browsing; GitHub bi-directional sync (GitHub stays source of truth)
- **App integrations:** Vercel (preview deploys), Depot, Buildkite (CI/CD)
- **Agent-native design:** agents operate directly within Origin repos; Cursor can query code you're browsing
- **Timing:** GitHub 6h42m global degradation with ~20% error rate on PRs/Issues/API started 3.5h after Origin launch

**Evidence — Aug 17 Cloud Builds default on:**
- All new/existing environments now default to pre-built environments (no extra cost)
- Cloud Builds all-default since Aug 17 (introduced Aug 13; 3× faster startup)

**Evidence — SpaceX acquisition CLOSED:**
- Confirmed closed Aug 14 ($60B all-stock — largest VC startup acquisition ever)
- (Previously "closing Q3 2026")

**Sources:** https://cursor.com/changelog/origin-code-hosting · https://venturebeat.com/infrastructure/cursor-launches-origin-code-hosting-platform-as-github-outage-exposes-opening-in-ai-coding-race · https://siliconangle.com/2026/08/17/cursor-launches-origin-code-hosting-service-to-compete-with-github/ · https://xenospectrum.com/en/cursor-origin-code-hosting-beta/ · https://techstartups.com/2026/08/17/cursor-launches-origin-a-github-rival-built-for-ai-coding-agents/ · https://kingy.ai/blog/cursor-origin-vs-github/ · https://cursor.com/changelog

---

### 5. [update] DeepSeek Harness: 131k Stars, 6k+ Plugins in 5 Days — Ecosystem Out of Control 🌐🇯🇵🇨🇳

**New facts since Aug 14:** Stars: 52.9k → 131,165 (week 33); plugin ecosystem exploded to ~6,000 in 3 days; Oh-My-DSH directory, dshpluginstore.com; cache hit rate data from JP community; CN community reports "near out of control."

**Evidence — Star trajectory:**
- 10,000 stars in 2h; 50,000 in 12h; ~80x faster than OpenClaw (previously fastest-growing GitHub repo)
- 95,386 stars + 8,826 forks at Aug 15 (2 days post-launch)
- **131,165 stars** by week 33 end (~Aug 17, Qiita trending summary)
- https://ossinsight.io/trending/ai · https://qiita.com/keishin_nishiura/items/3f1f9ac6dc3af28ebf3a

**Evidence — Plugin ecosystem:**
- Oh-My-DSH directory: 1,117 curated plugins across 1,521 repos (301,295 combined stars) as of Aug 15
- ~6,000 community plugins in 3 days; 6-7 new plugin pushes per minute (Tencent News Aug 17)
- Ecosystem repos in GitHub week 33 trending: anywhere-labs/deepseek-harness-desktop (8,865★), awesome-dsh-plugin (5,081★), dsh-web-ui (3,420★), dsh-anchored-standard (3,019★), dsh-routing-suite (2,809★), dsh-TUI (1,542★)
- Dedicated stores: https://dshpluginstore.com/ · https://www.dshbase.com/
- Community handbook (CN+EN PDF): https://github.com/Electricitysheep/dsh-handbook
- **Governance problem:** Any repo can self-add "dsh-plugin" label; fake traffic-generation repos emerging

**Evidence — Performance data (🇯🇵 Qiita lumichy):**
- Cache hit rate: **80-85%** in testing; input cost on cache hit: **~3% of cache miss** (97% discount)
- One real execution: 89% cache hit, 36.6K input tokens + 1.3K output at 203 tok/s (deepseek-v4-flash)
- Source: https://qiita.com/lumichy/items/6a390716ab346cb2a1d5

**CN framing (🇨🇳):**
- 「近6000个插件快"失控"了」("~6,000 plugins nearly out of control") — Tencent News Aug 17
- 「安卓时刻」("Android moment") framing continues; CN competition framing: "Can DSH end Claude Code's dominance?"
- Source: https://view.inews.qq.com/a/20260817A06W5U00 · https://openclaw.club/archives/deepseek-harness-official-release · https://www.aitoollab.cn/articles/deepseek-harness-open-source-agent-framework-2026/

**Sources:** https://flowtivity.ai/blog/deepseek-harness-open-source-agent-explained/ · https://www.marktechpost.com/2026/08/17/deepseek-ai-releases-deepseek-harness-in-developer-preview/ · https://ai-engineering-trend.medium.com/community-built-plugin-store-for-deepseek-hits-1-080-plugins-on-github-25c7c7977e53 · https://www.orcarouter.ai/blog/deepseek-harness-plugins · https://www.v2ex.com/t/1234467 · https://view.inews.qq.com/a/20260815A05N3B00 · https://sspai.com/post/113434 · https://www.cnblogs.com/sing1ee/p/22455466 · https://www.uuaihub.com/blog/deepseek-harness-agent-framework

---

### 6. [update] Hermes Agent v0.20.2 + v0.20.3 (Both Aug 16): MCP 2.x Migration + Multi-Gateway Registry 🌐

**New facts since Aug 14:** Two patches shipped on Aug 16 — v0.20.2 (multi-gateway registry, MCP health monitoring, prompt caching for LiteLLM) and v0.20.3 (MCP 2.x SDK migration to 2026-07-28 stateless spec, Bot Mode bundled, session handoff data-loss fix).

**Evidence — v0.20.2 (Aug 16):**
- ~397 merged PRs, ~1,279 files, 128k+ additions
- Multi-gateway connection registry in desktop
- Profile-scoped refresh capabilities
- MCP health monitoring systems
- Persisted model routing at gateway level
- Prompt caching for LiteLLM Claude implementations
- Windows update detection + Linux/Windows installer robustness

**Evidence — v0.20.3 (Aug 16, same-day patch):**
- ~125 merged PRs, ~250 commits, ~461 files
- **MCP 2.x SDK migration**: full 2026-07-28 stateless protocol support
- Bundled Bot Mode plugin with core teammate protocol
- CommandCode provider functionality
- Python runtime ownership hardening with environment isolation
- Kanban worktree and dispatch fixes; session handoff data-loss prevention; UTF-16 file reading

**Sources:** https://github.com/NousResearch/hermes-agent/releases · https://hermesatlas.com/guide/ · https://hermes-ai.net/changelog/ · https://releasebot.io/updates/nousresearch/hermes-agent · https://the-agent-report.com/2026/08/hermes-agent-v020-herald-release-august-2026/

---

### 7. [update] Claude Code v2.1.233 (Aug 15): Self-Hosted-Runner Faster, GitLab MR in Worktree 🌐

**New facts since Aug 14:** v2.1.233 (Aug 15) — self-hosted-runner session start improved (no working tree rewrite), GitLab MR URLs in --worktree, plugin validate for SKILL.md frontmatter.

**Evidence:**
- **Self-hosted-runner:** session branch created without rewriting working tree; two server round trips removed from launch path → faster session start
- **GitLab MR support:** GitLab merge request URLs now work in `--worktree` and `claude agents view` (requires v2.1.233+)
- **Plugin validate:** `claude plugin validate` now checks bare `.claude/skills/` directory; reports SKILL.md frontmatter parse failures
- **Self-hosted runner (background context):** public beta since v2.1.224 (Aug 7); Team + Enterprise only; `claude self-hosted-runner` turns org machines/containers into execution layer; two modes: fixed and on-demand; model inference still via Anthropic API; execution environment stays on org infra

**Sources:** https://github.com/anthropics/claude-code/releases/tag/v2.1.233 · https://releasebot.io/updates/anthropic/claude-code · https://dev.classmethod.jp/en/articles/claude-code-self-hosted-runner/ · https://enterprisedna.co/resources/news/anthropic-claude-code-self-hosted-runner-enterprise-2026/ · https://claude.com/blog/run-claude-code-sessions-on-your-own-compute · https://code.claude.com/docs/en/self-hosted-environments · https://www.unite.ai/claude-code-sessions-can-now-run-on-infrastructure-your-team-controls/ · https://code.claude.com/docs/en/changelog

---

### 8. [update] OpenClaw 2026.8.1: Full GA (Not Beta) — Secret Egress Binding + SQLite Snapshots 🌐

**New fact since Aug 14:** 2026.8.1 shipped as full GA on Aug 15 (beyond the beta.1/beta.2 builds); adds secret egress host binding, atomic model/runtime switching, SQLite snapshots, and macOS app profile isolation.

**Evidence:**
- **Secret egress host binding:** Each shared-store secret bound to exact HTTPS destination hosts; unbound sentinel substitution fails closed before plaintext egress (CLI, Gateway RPC, Control UI)
- **Atomic model/runtime switching:** Sol, Terra, and Luna model support; /model and fallback selections kept atomic across OpenClaw/Codex engines
- **SQLite snapshots:** `openclaw backup sqlite create|list|verify|restore` — compact, verified global + per-agent database artifacts
- **macOS app profile isolation:** Named instances isolated across state, preferences, Keychain, Gateway services, duplicate-instance ownership
- **Plugin install security:** `--force` required for arbitrary executable plugin sources; ClawHub/bundled/official-catalog flows remain frictionless

**Sources:** https://releasebot.io/updates/openclaw · https://github.com/openclaw/openclaw/releases · https://docs.openclaw.ai/releases · https://openclawai.io/changelog

---

### 9. [update] Agent Plugins 1.0: GA Rollout to VS Code, Copilot CLI, Copilot App (Aug 12) 🌐

**New fact since Aug 14:** As of Aug 12, Agent Plugins 1.0 is GA across VS Code, GitHub Copilot CLI, and the Copilot app (all plans). Claude Code listed as supported target in plugins CLI, though Anthropic remains absent from core maintainers.

**Evidence:**
- **Build once, run everywhere:** Bundle skills + MCP in one `plugin.json` dir; platform-specific extensions go in namespaced `com.github.copilot/` (other clients ignore this)
- **Marketplace:** Awesome Copilot marketplace integrated by default into VS Code, Copilot CLI, Copilot app
- **Claude Code support:** plugins CLI translates portable format into Claude Code's native plugin system (Anthropic NOT a core maintainer or charter signer)
- **Enterprise:** existing `managed-settings.json` controls apply to all compatible clients
- **Security gap:** v1.0 contains no provenance/trust model — no cryptographic signatures, no standardized permission model, no sandboxing requirements in spec

**Sources:** https://github.blog/changelog/2026-08-12-agent-plugins-1-0-in-vs-code-copilot-cli-and-the-copilot-app/ · https://www.eesel.ai/blog/agent-plugins · https://tech.yahoo.com/ai/copilot/articles/industry-shipped-agent-plugins-1-140520546.html · https://agenticskills.io/learn/what-are-agent-plugins · https://www.digitalapplied.com/blog/agent-plugins-1-0-open-standard-portable-ai-skills · https://blakecrosley.com/blog/agent-plugins-standard · https://developers.googleblog.com/agent-plugins-package-your-skills-tools-and-more/

---

### 10. [update] Kiro v2.18.0 (Aug 12): Voice Dictation + Nested AGENTS.md + Enterprise Cloud Opt-In 🌐

**New facts since Aug 14:** v2.18.0 adds voice dictation (`/voice` on-device transcription), nested AGENTS.md steering from anywhere in workspace tree, spec review screen with line comment staging, and enterprise-admin gating for cloud sessions.

**Evidence:**
- **Voice dictation:** `/voice` — on-device transcription; talk to Kiro instead of type; reduces context-switching friction
- **Nested AGENTS.md:** Steering files load from any depth in workspace tree (not just root + ~/.kiro/steering); put AGENTS.md next to the code it describes
- **Spec review:** read phase docs in-place; stage line comments
- **Cloud sessions enterprise opt-in:** Enterprise admins must explicitly enable; removes auto-enrollment in managed deployments
- **CLI v2.18.1 (Aug 14):** patch on top of v2.18.0

**Sources:** https://kiro.dev/changelog/ · https://releasebot.io/updates/kiro · https://siliconangle.com/2026/08/04/aws-launches-kiro-crew-autonomous-agentic-orchestrator-24-7-code-development/ · https://aws.amazon.com/blogs/aws/aws-weekly-roundup-aws-heroes-summit-web-search-on-amazon-bedrock-dogwood-kiro-crew-and-more-august-10-2026/

---

### 11. [update] VSCode 1.133 (Aug 12): Multi-Window Agent Sessions + Provider Switching Between Turns 🌐

**New facts since Aug 14:** VSCode 1.133 ships multi-window agent sessions (one session, multiple windows) and between-turn provider switching (no agent host reconfiguration needed).

**Evidence:**
- **Multi-window agent sessions:** Dedicated agent host process; connect to same session from multiple VS Code windows (Agent Host Protocol + Copilot SDK)
- **Provider switching between turns:** Model picker groups Anthropic (API keys) vs. Copilot (subscriptions); switch providers per response without reconfiguring
- **Experimental no-GitHub setting:** `chat.agentHost.allowSignedOutWhenGithubUnavailable` — benefits Claude API-key users who can't reach github.com
- **Sticky scroll for prompts**; HTML auto-reload in integrated browser

**Source:** https://code.visualstudio.com/updates/v1_133

---

### 12. [update] Extension Economy: book-to-skill Trending, DSH Plugins Accelerate, Security Gap in AP1.0 🌐

**New facts since Aug 14:** book-to-skill 12k+ stars trending (week 33 #11); DeepSeek plugin ecosystem ~6k plugins in 3 days; Agent Plugins 1.0 GA but no trust model in v1.0 spec.

**Evidence:**
- **book-to-skill:** 12k+ stars; turns book PDFs into portable SKILL.md skills; chapter-level lazy loading; GitHub Copilot CLI + Amp + Claude Code compatible; SkillsLLM security scanned
- **DSH plugin ecosystem:** 6k+ plugins in 3 days; fake/traffic-generation repos emerging; quality signal needed
- **Agent Plugins 1.0 security gap:** No cryptographic signatures, no standardized permissions, no sandboxing in spec (acknowledged in spec v1.0)
- **claudemarketplace.net:** 4,384+ skills, 727+ MCP servers (ongoing context: Aug 4 data)
- **mcpmarket.com:** Best integration between servers and skills; MCP-based catalog access (live catalog via single MCP connection)

**Sources:** https://github.com/Leutenegger/book-to-skill · https://www.coddykit.com/pages/blog-detail?id=512975&slug=book-to-skill-the-open-source-tool-with-12-000-github-stars-that-turns-any-techn · https://skillsllm.com/skill/book-to-skill · https://mcpmarket.com/ · https://www.claudemarketplace.net/ · https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 · https://mcpservers.org/agent-skills

---

### 13. [update] EU AI Act (Aug 2) Driving Enterprise Harness Guardrails — JP/Global Confluence 🌐🇯🇵

**New facts since Aug 14:** EU AI Act high-risk enforcement began Aug 2; JP Zenn article documents: AI-generated code has 1.7x more problems than human code; MTTR improved 72% post-harness adoption in one fintech.

**Evidence (🇯🇵 Zenn Creationline):**
- EU AI Act Aug 2 enforcement: guardrail design now legal obligation for healthcare/finance/infrastructure software developers
- Quote: 「医療・金融・インフラに関わるソフトウェアを開発している企業にとって、ガードレールの設計は法的義務になりつつあります」 (EU AI Act compliance makes guardrail design a legal obligation for healthcare/finance/infrastructure software companies)
- AI-generated code: ~1.7x more issues than human-written (CodeRabbit analysis)
- MTTR improved 72% in fintech case study with harness implementation
- 82% of enterprises plan AI agent deployment by 2026 (Capgemini)

**Sources:** https://zenn.dev/creationline/articles/ai-harness-guardrails-enterprise-2026 · https://www.microsoft.com (Microsoft Agent Governance Toolkit ongoing)

---

**Still true** (ongoing threads, no new facts this cycle):

- `penguinharness-self-improving` — PenguinHarness (LlamaFactory team, self-improving, $0.02/RAG-app); no new facts
- `ante-antigma-single-binary` — Ante 15MB Rust binary (135 HN pts); no new release
- `tencentdb-agent-memory` — TencentDB Agent Memory v2.0; no new facts
- `meta-muse-code` — Meta Muse Code beta; no new facts
- `prime-agent-rlm` — Prime Agent (MIT); no new facts
- `aq-multiplayer-harness` — AQ multiplayer harness; no new facts
- `qwen-code-alibaba` — Qwen Code; no new facts
- `oh-my-agent` — oh-my-agent; no new facts
- `autoharness-deepmind` — AutoHarness (DeepMind); no new facts
- `hoplite-yc-s26-cloud-deploy` — Hoplite; no new facts
- `vercel-ai-sdk-harnessagent` — Vercel AI SDK v7 HarnessAgent; no new facts
- `copilot-studio-ga-harness-billing` — Copilot Studio; no new facts
- `microsoft-agent-governance-toolkit` — AGT; EU AI Act adoption ongoing
- `tinyagents-rust-recursive` — TinyAgents; no new facts
- `sprocket-hardware-software-agent` — Sprocket; no new facts
- `gambit-reliable-agent-harness` — Gambit; no new facts
- `nlah-natural-language-harnesses` — NLAH; no new facts
- `skills-security-prompt-injection-36pct` — 36% prompt injection; AP1.0 security gap adds context
- `claude-tag-slack-agent` — Claude Tag; no new facts
- `mimo-code-xiaomi` — MiMo Code; no new facts
- `ecc-cross-harness-os` — ECC; no new facts
- `cursor-3-11-update` — superseded by Origin/Cloud Builds updates
- `kimi-code-moonshot` — Kimi Code; no new facts
- `runtime-yc-p26` — Runtime; no new facts
- `noclick-always-on` — NoClick; no new facts
- `nyx-offensive-testing` — Nyx; no new facts
- `agentguard-security-tool` — AgentGuard; no new facts
- `mcp-security-nsa-supply-chain` — Agentjacking / MCP security; Copilot Autofix incident is related but distinct (separate thread)
- `yc-qm-multiplayer-harness` — YC QM; no new facts
- `mcp-stateless-spec-2026-07-28` — MCP 2026-07-28 spec; now implemented in Hermes v0.20.3
- `jadepuffer-agentic-security` — JADEPUFFER ransomware; no new facts
- `grok-build-xai-rust-harness` — Grok-Build; no new facts
- `self-harness-auto-optimization` — Self-Harness paper; no new facts
- `openharness-hkuds` — OpenHarness; no new facts
- `antigravity-gemini-cli-successor` — Antigravity 2.0; no new facts
- `claw-code-claude-rewrite` — Claw Code ~195k stars; no new facts
- `metaharness-scaffold-generator` — MetaHarness; no new facts
- `harness-engineering-paradigm` — Agent=Model+Harness paradigm; DSH 131k stars reinforces
- `deerflow-superagent-harness` — DeerFlow 2.0; no new facts
- `omnigent-meta-harness` — Omnigent; no new facts
- `zot-go-coding-harness` — Zot; no new facts
- `omp-omo-pi-derivatives` — oh-my-pi + oh-my-openagent; no new facts
- `yorishiro-presence-harness` — Yorishiro; no new facts
- `agentskills-open-standard` — SKILL.md; book-to-skill and AP1.0 rollout add context
- `letta-agent-file-format` — Letta .af; no new facts
- `layered-oss-stack-over-single-framework` — 17+ OSS layers pattern; no new facts
- `macos-harness-proving-ground` — macOS proving ground; no new facts
- `ahe-automated-harness-evolution` — AHE papers; no new facts
- `harness-internal-external-disambiguation` — Internal vs External Harness; no new facts
- `environment-architect-new-role` — 環境設計者; JP community still active
- `warp-oz-multi-harness` — Warp Oz; no new facts
- `mozilla-otari-llm-gateway` — Mozilla Otari; no new facts
- `statewright-guardrails` — Statewright; no new facts
- `headroom-token-compression` — Headroom; no new facts
- `pi-minimal-agent-harness` — Pi; no new facts
- `nvidia-skillspector-security` — SkillSpector; no new facts
- `cli-anything-hkuds` — CLI-Anything; no new facts
- `forge-acp-universal-cli` — Forge ACP; no new facts
- `github-copilot-skills-mcp-ga` — Copilot skills+MCP; AP1.0 rollout extends this
- `opencode-anomaly-rebrand` — OpenCode v1.18.18 (Aug 13); v1.18.17 also (Aug 12, session compaction improvements)
- `block-buzz-workspace` — Block Buzz; no new facts
- `zcode-zhihu-agent-ide` — ZCode; no new facts
- `devin-desktop-windsurf-rebrand` — Devin Desktop; no new facts
- `devin-fusion-multimodel` — Devin Fusion; no new facts
- `ambiance-unix-harness` — Ambiance; no new facts
- `kore-artemis-abl` — Kore.ai Artemis; no new facts
- `open-agent-passport-oap` — OAP; no new facts
- `code-as-agent-harness-paper` — arXiv:2605.18747; no new facts
- `tilde-harness-sdk` — Tilde; no new facts
- `microsoft-maf-codeact` — MAF Harness; no new facts
- `cloudflare-os-kitesurf` — no new facts
- `deepseek-harness-team` — (absorbed into deepseek-harness-v01 update above)

---

## Cross-Source Patterns

### Pattern 1: Dual-AI Attack Surface — AI Introduces Bugs, AI Exploits Them 🌐
**Platforms:** HN (381 pts), Forbes, The Register, SC Media, Wiz blog, The Hacker News, Cyber Kendra

The Copilot Autofix/Snowflake Jira incident is the clearest documented example of a compressed attack surface: an AI coding agent introduced a GitHub Actions script injection vulnerability, and an autonomous security agent (Wiz Red Agent) discovered and exploited it within 5 days. This pattern — AI-introduced vulnerability + AI-driven exploitation — is now the dominant security threat model for harness operators. GitHub Advanced Security missed the injection. The implication: SAST tooling is not keeping pace with AI-generated code patterns, and the detection-to-exploitation window is measured in days.

> "An AI broke Snowflake's code. Then another AI agent exploited it." — The Register ([link](https://www.theregister.com/security/2026/08/17/an-ai-broke-snowflakes-code-then-another-ai-agent-exploited-it/5288666))

---

### Pattern 2: DeepSeek Harness Ecosystem Velocity Is Unprecedented — and Ungoverned 🌐🇯🇵🇨🇳
**Platforms:** GitHub (131k stars), HN, Tencent News, V2EX, Qiita, Juejin, Zhihu, MarkTechPost, flowtivity.ai

DeepSeek Harness went from 0 to 131k GitHub stars in ~5 days (80x faster than OpenClaw). The ecosystem velocity is also unprecedented: ~6,000 community plugins in 3 days, 6-7 pushes/minute. But governance hasn't kept pace — any repo can self-add the "dsh-plugin" label, and fake traffic-generation repos are already appearing. The pattern mirrors early npm/Docker Hub ecosystem pollution. JP community provides quantitative performance data (80-85% cache hit rate, 97% cost reduction); CN community tracks ecosystem size and quality concerns.

> 🇨🇳「近6000个插件快"失控"了」("~6,000 plugins nearly out of control") — Tencent News, Aug 17 ([link](https://view.inews.qq.com/a/20260817A06W5U00))

---

### Pattern 3: The Stack Is Vertical-izing — Cursor Moves into Code Hosting 🌐
**Platforms:** VentureBeat, SiliconAngle, XenoSpectrum, cursor.com/changelog

Cursor's Origin launch on Aug 17 (with Cloud Builds default same day) signals that the top incumbent coding agents are no longer just IDE plugins — they're building complete developer platform stacks. Cursor now spans: IDE → cloud agents → code hosting → CI/CD integrations. SpaceX ($60B, closed Aug 14) adds corporate infrastructure. The "GitHub killer" narrative emerged immediately when Origin launched hours before GitHub's largest outage of 2026 (6h42m). The risk for smaller harnesses: platform lock-in accelerates when the harness controls hosting.

---

### Pattern 4: Extension Standard Adoption Asymmetry — AP1.0 vs SKILL.md 🌐
**Platforms:** GitHub Changelog, eesel, agenticskills.io, Yahoo Tech, book-to-skill

Agent Plugins 1.0 reached GA across all major clients (VS Code, Copilot, ChatGPT, Cursor, Kiro) on Aug 12. The same week, book-to-skill trended to 12k stars using the older SKILL.md standard. The two standards now coexist: SKILL.md (open, Anthropic origin, broadly portable, including Amp and Copilot CLI) and AP1.0 (coalition standard, broader tooling but no trust model). SKILL.md remains the dominant format for community-created skills; AP1.0 dominates enterprise client integration. Neither is winning outright.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| — | AI-Generated GitHub Copilot "Autofix" Allowed Compromise of Snowflake's Jira | 381 | 146 | "An AI broke Snowflake's code. Then another AI agent exploited it." | https://news.ycombinator.com/item?id=49331423 |
| adi_ycs26 | Launch HN: Bullet (YC S26) – A Faster Coding Agent | 117 | 88 | "30-60% faster than Claude Code and Codex"; concern: "benchmark saturation" | https://news.ycombinator.com/item?id=49283063 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Wiz Blog | https://www.wiz.io/blog/red-agent-snowflake-copilot-cicd-bug | Copilot Autofix + Wiz Red Agent Snowflake incident |
| 🌐 | Forbes | https://www.forbes.com/sites/timkeary/2026/08/17/github-copilot-missed-a-vulnerability-that-wizs-ai-agent-found/ | Forbes: Copilot missed what Wiz's agent found |
| 🌐 | The Register | https://www.theregister.com/security/2026/08/17/an-ai-broke-snowflakes-code-then-another-ai-agent-exploited-it/5288666 | Dual-AI attack surface framing |
| 🌐 | SC Media | https://www.scworld.com/news/wiz-agent-finds-snowflake-repo-flaw-in-code-co-authored-by-github-copilot-autofix | Copilot co-authored the vulnerable commit |
| 🌐 | Hacker News | https://thehackernews.com/2026/08/snowflake-github-actions-flaw-lets_0330881554.html | Technical vulnerability details |
| 🌐 | Cyber Kendra | https://www.cyberkendra.com/2026/08/copilot-autofix-snowflake-jira-github-actions.html | Copilot Autofix + Jira access details |
| 🌐 | VentureBeat | https://venturebeat.com/infrastructure/cursor-launches-origin-code-hosting-platform-as-github-outage-exposes-opening-in-ai-coding-race | Cursor Origin + GitHub outage timing |
| 🌐 | SiliconAngle | https://siliconangle.com/2026/08/17/cursor-launches-origin-code-hosting-service-to-compete-with-github/ | Cursor Origin vs GitHub |
| 🌐 | XenoSpectrum | https://xenospectrum.com/en/cursor-origin-code-hosting-beta/ | Cursor Origin agent-native design |
| 🌐 | Cursor Changelog | https://cursor.com/changelog/origin-code-hosting | Official Origin entry |
| 🌐 | Tech Startups | https://techstartups.com/2026/08/17/cursor-launches-origin-a-github-rival-built-for-ai-coding-agents/ | GitHub rival framing |
| 🌐 | kingy.ai | https://kingy.ai/blog/cursor-origin-vs-github/ | Cursor Origin vs GitHub comparison |
| 🌐 | GitHub Changelog | https://github.blog/changelog/2026-08-12-agent-plugins-1-0-in-vs-code-copilot-cli-and-the-copilot-app/ | Agent Plugins 1.0 GA rollout |
| 🌐 | eesel | https://www.eesel.ai/blog/agent-plugins | Agent Plugins 1.0 overview |
| 🌐 | agenticskills.io | https://agenticskills.io/learn/what-are-agent-plugins | Complete AP1.0 guide |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/agent-plugins-1-0-open-standard-portable-ai-skills | What AP1.0 fixes |
| 🌐 | Yahoo Tech | https://tech.yahoo.com/ai/copilot/articles/industry-shipped-agent-plugins-1-140520546.html | Industry vs standards body tension |
| 🌐 | blakecrosley.com | https://blakecrosley.com/blog/agent-plugins-standard | AP1.0 explainer |
| 🌐 | Google Dev Blog | https://developers.googleblog.com/agent-plugins-package-your-skills-tools-and-more/ | Google perspective on AP1.0 |
| 🌐 | VSCode | https://code.visualstudio.com/updates/v1_133 | VSCode 1.133: multi-window sessions, provider switching |
| 🌐 | Hermes Releases | https://github.com/NousResearch/hermes-agent/releases | v0.20.2, v0.20.3 (Aug 16) |
| 🌐 | Hermes Atlas | https://hermesatlas.com/guide/ | v0.20.3 guide |
| 🌐 | hermes-ai.net | https://hermes-ai.net/changelog/ | Changelog |
| 🌐 | Agent Report | https://the-agent-report.com/2026/08/hermes-agent-v020-herald-release-august-2026/ | v0.20.0 Herald Release context |
| 🌐 | Claude Code Docs | https://code.claude.com/docs/en/changelog | Official CC changelog |
| 🌐 | CC GitHub releases | https://github.com/anthropics/claude-code/releases/tag/v2.1.233 | v2.1.233 release |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC Aug 2026 timeline |
| 🌐 | Classmethod | https://dev.classmethod.jp/en/articles/claude-code-self-hosted-runner/ | Self-hosted runner EC2 test |
| 🌐 | EnterpriseDNA | https://enterprisedna.co/resources/news/anthropic-claude-code-self-hosted-runner-enterprise-2026/ | Enterprise self-hosted coverage |
| 🌐 | Claude Blog | https://claude.com/blog/run-claude-code-sessions-on-your-own-compute | Official self-hosted blog post |
| 🌐 | CC Docs SHE | https://code.claude.com/docs/en/self-hosted-environments | Self-hosted environments docs |
| 🌐 | Unite.AI | https://www.unite.ai/claude-code-sessions-can-now-run-on-infrastructure-your-team-controls/ | Unite.AI coverage |
| 🌐 | OpenClaw Releases | https://github.com/openclaw/openclaw/releases | 2026.8.1 GA |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OpenClaw Aug 2026 |
| 🌐 | OC Docs | https://docs.openclaw.ai/releases | Release notes |
| 🌐 | OpenClaw AI | https://openclawai.io/changelog | Changelog |
| 🌐 | Kiro Changelog | https://kiro.dev/changelog/ | v2.18.0 (Aug 12) |
| 🌐 | Releasebot Kiro | https://releasebot.io/updates/kiro | Kiro Aug 2026 |
| 🌐 | Product Hunt | https://www.producthunt.com/products/bullet-6 | Bullet 30-60% faster claim |
| 🌐 | Builder Radar | https://buttondown.com/Builder-Radar/archive/builder-radar-week-of-august-16-2026/ | Week of Aug 16 roundup |
| 🌐 | CoddyKit | https://www.coddykit.com/pages/blog-detail?id=512975&slug=book-to-skill-the-open-source-tool-with-12-000-github-stars-that-turns-any-techn | book-to-skill 12k stars |
| 🌐 | SkillsLLM | https://skillsllm.com/skill/book-to-skill | book-to-skill security scan |
| 🌐 | book-to-skill | https://github.com/Leutenegger/book-to-skill | GitHub repo |
| 🌐 | Flowtivity | https://flowtivity.ai/blog/deepseek-harness-open-source-agent-explained/ | DSH 95k stars in 2 days |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/08/17/deepseek-ai-releases-deepseek-harness-in-developer-preview/ | DSH late coverage |
| 🌐 | ai-engineering Medium | https://ai-engineering-trend.medium.com/community-built-plugin-store-for-deepseek-hits-1-080-plugins-on-github-25c7c7977e53 | 1,080+ plugins (early) |
| 🌐 | OrcaRouter | https://www.orcarouter.ai/blog/deepseek-harness-plugins | DSH plugin install guide |
| 🌐 | dshpluginstore.com | https://dshpluginstore.com/ | Community plugin store |
| 🌐 | dshbase.com | https://www.dshbase.com/ | DSH everything-is-a-plugin guide |
| 🌐 | explainx.ai DSH | https://explainx.ai/blog/deepseek-harness-v0-1-plugin-first-agent-stack-august-2026 | Plugin-first stack explainer |
| 🌐 | DigitalApplied DSH | https://www.digitalapplied.com/blog/deepseek-harness-open-source-agent-framework-2026 | DigitalApplied coverage |
| 🌐 | MCPmarket | https://mcpmarket.com/ | MCP + skills marketplace |
| 🌐 | claudemarketplace.net | https://www.claudemarketplace.net/ | 4,384+ skills, 727+ MCP servers |
| 🌐 | agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 7 marketplaces compared |
| 🌐 | ai-boost GH | https://github.com/ai-boost/awesome-harness-engineering | Awesome harness list (3.6k stars) |
| 🌐 | RyanAlberts | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses ranked |
| 🌐 | DEV community | https://dev.to/instasla/copilot-autofix-vs-agentic-autofix-managing-ai-driven-vulnerability-patching-4p4h | Autofix vs agentic autofix |
| 🇯🇵 | Qiita (lumichy) | https://qiita.com/lumichy/items/6a390716ab346cb2a1d5 | DSH 80-85% cache hit rate; 97% cost discount |
| 🇯🇵 | Qiita (keishin) | https://qiita.com/keishin_nishiura/items/3f1f9ac6dc3af28ebf3a | Week 33 GitHub trending: DSH #1 at 131k |
| 🇯🇵 | Qiita (Simon_Zhang) | https://qiita.com/Simon_Zhang/items/2759f26cb5ffcbeb2a73 | Continual Harness paper explainer |
| 🇯🇵 | Qiita (Takashi_M) | https://qiita.com/Takashi_Masumori/items/e6f1678b41483943fc04 | Copilot Studio harness/credit billing |
| 🇯🇵 | Qiita (moonwalker) | https://qiita.com/moonwalker/items/61fa726dc8473d908faa | Tencent Cloud TokenHub + DSH |
| 🇯🇵 | Qiita (engchina) | https://qiita.com/engchina/items/da538eff67a34ef8dd00 | DSH + local models (Ollama) |
| 🇯🇵 | Zenn (Creationline) | https://zenn.dev/creationline/articles/ai-harness-guardrails-enterprise-2026 | EU AI Act + guardrails 2026 |
| 🇯🇵 | note (trans_n_ai) | https://note.com/trans_n_ai/n/nf4946f5847de | DSH open-source harness explainer |
| 🇯🇵 | note (masa_cloud) | https://note.com/masa_cloud/n/n2f9450f72e90 | DSH complete guide |
| 🇯🇵 | genai-ai.co.jp | https://genai-ai.co.jp/ai-kanri/blog/cc-yt-harness-engineering-33/ | Claude Code 3-subagent harness design |
| 🇯🇵 | maasaablog | https://maasaablog.com/blog/ai-agent-harness-quality-claude-code-cursor/ | Why harnesses are essential for quality |
| 🇨🇳 | Tencent News | https://view.inews.qq.com/a/20260817A06W5U00 | ~6,000 plugins "nearly out of control" |
| 🇨🇳 | Tencent News | https://view.inews.qq.com/a/20260815A05N3B00 | 5 practical DSH plugins tested |
| 🇨🇳 | V2EX | https://www.v2ex.com/t/1234467 | Plugin store discovery discussion |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2029220210800883392 | 12 core harness modules analysis |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2035091449956545786 | 2026 Agent Harness deep tech report |
| 🇨🇳 | openclaw.club | https://openclaw.club/archives/deepseek-harness-official-release | "Android moment" framing |
| 🇨🇳 | UU AI Hub | https://www.uuaihub.com/blog/deepseek-harness-agent-framework | 40k stars in 24h analysis |
| 🇨🇳 | ai-indeed.com | https://www.ai-indeed.com/encyclopedia/29653.html | DSH timeline: internal to public |
| 🇨🇳 | aitoollab.cn | https://www.aitoollab.cn/articles/deepseek-harness-open-source-agent-framework-2026/ | "Can DSH end Claude Code dominance?" |
| 🇨🇳 | sspai.com | https://sspai.com/post/113434 | 少数派 DSH launch news |
| 🇨🇳 | runoob.com | https://www.runoob.com/ai-agent/harness-engineering.html | CN harness engineering tutorial |
| 🇨🇳 | Aliyun Dev | https://developer.aliyun.com/article/1727711 | Java AI agent harness on Alibaba Cloud |
| 🇨🇳 | Electricitysheep | https://github.com/Electricitysheep/dsh-handbook | dsh-handbook (CN+EN) |
| 🇨🇳 | cnblogs | https://www.cnblogs.com/sing1ee/p/22455466 | Complete DSH developer guide |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed
├─ 🔵 X: not accessed
├─ 🔴 YouTube: not accessed (1 URL from search results included)
├─ 🟢 HN: 2 tracked threads │ ~898 pts │ ~292 comments (+ front page scan)
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed
├─ 🦋 Bluesky: 0 posts │ 0 on-topic (bluesky=OK)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~60 pages │ 🇯🇵 ~12 │ 🇨🇳 ~16
└─ 🗣️ Top voices: wiz.io (Red Agent, Copilot Autofix), Leutenegger/book-to-skill, lumichy 🇯🇵, tonybai.com 🇨🇳
```

---

## Out of Scope but Notable

- **GPT-5.6 Sol pricing cut by 50%** (HN 479 pts/302 comments on Aug 18): OpenAI cuts GPT-5.6 Sol pricing 50% → $2/MTok input, $8/MTok output. Out-of-scope (foundation model pricing), but directly affects model routing decisions in harnesses like Bullet and Cursor Router. Source: https://openrouter.ai/openai/gpt-5.6-sol
- **VSCode 1.133 multi-window sessions** (already covered in Finding #11): also signals that IDE-layer harness orchestration is commoditizing — what required custom tooling (Warp Oz, AQ) is now in the platform by default.

---

## Data Gaps

- **Reddit, X/Twitter, YouTube, TikTok, Instagram:** not accessed — social signal layer absent. Copilot Autofix/Snowflake and Cursor Origin likely generated significant X/Reddit volume.
- **/last30days skill:** unavailable (tool not loaded) — social platforms (Reddit, X, TikTok, Instagram, YouTube, Polymarket) not collected. WebSearch + WebFetch substituted.
- **Bluesky:** bluesky=OK; 0 on-topic posts found
- **DuckDuckGo HTML endpoint:** returned CAPTCHA for both JP and CN queries; WebSearch used as substitute (reaches JP/CN content via Qiita/Zenn/Zhihu indexed results but with lower coverage than DDG HTML browse)
- **DeepSeek Harness star count:** Latest confirmed at 131,165 (week 33 Qiita summary, ~Aug 17); may be higher by Aug 18
- **Bullet:** closed-source; no GitHub metrics available; SWE-bench claim unverified independently
- **Coverage estimate: 72%** — HN and English web good coverage; JP and CN passes captured key content via indexed search (DuckDuckGo HTML CAPTCHA limited direct browse); full social layer absent.

---

## Key Quotes

> "An AI broke Snowflake's code. Then another AI agent exploited it." — The Register, Aug 17 ([link](https://www.theregister.com/security/2026/08/17/an-ai-broke-snowflakes-code-then-another-ai-agent-exploited-it/5288666)) 🌐

> "GitHub Copilot missed a vulnerability that Wiz's AI agent found." — Forbes, Aug 17 ([link](https://www.forbes.com/sites/timkeary/2026/08/17/github-copilot-missed-a-vulnerability-that-wizs-ai-agent-found/)) 🌐

> 🇨🇳「近6000个插件快"失控"了」("~6,000 plugins nearly out of control") — Tencent News, Aug 17 ([link](https://view.inews.qq.com/a/20260817A06W5U00)) 🇨🇳

> 🇯🇵「DeepSeek Harnessはキャッシュヒット率80-85%を達成、キャッシュヒット時の入力コストはキャッシュミス時の約3%（97%割引）」 ("DeepSeek Harness achieves 80-85% cache hit rate; input cost on cache hit is ~3% of cache miss — 97% discount") — lumichy on Qiita ([link](https://qiita.com/lumichy/items/6a390716ab346cb2a1d5)) 🇯🇵

> 🇨🇳「Agent时代的安卓」("Android for the Agent era") — openclaw.club on DeepSeek Harness open-ecosystem positioning ([link](https://openclaw.club/archives/deepseek-harness-official-release)) 🇨🇳

> "Build once, run across all compatible agent clients" — Agent Plugins 1.0 core promise, GitHub Changelog, Aug 12 ([link](https://github.blog/changelog/2026-08-12-agent-plugins-1-0-in-vs-code-copilot-cli-and-the-copilot-app/)) 🌐

> 🇯🇵「医療・金融・インフラに関わるソフトウェアを開発している企業にとって、ガードレールの設計は法的義務になりつつあります」 ("For companies developing software for healthcare, finance, and infrastructure, guardrail design is becoming a legal obligation") — Zenn Creationline on EU AI Act enforcement Aug 2 ([link](https://zenn.dev/creationline/articles/ai-harness-guardrails-enterprise-2026)) 🇯🇵

> "Cursor began rolling out Origin to paid users on Monday morning, and roughly three and a half hours later, GitHub experienced a six-hour-and-forty-two-minute global degradation." — VentureBeat, Aug 17 ([link](https://venturebeat.com/infrastructure/cursor-launches-origin-code-hosting-platform-as-github-outage-exposes-opening-in-ai-coding-race)) 🌐
