# AI Agent Harnesses — Daily Briefing
**Date:** 2026-10-02
**Query type:** GENERAL
**Sources:** GitHub Trending (agents-radar: stevenko2002 #1537/#1557, kouweizhu #296, howe12 #633, duanyytop #3583), Hacker News, NVIDIA press/developer blog, Anthropic blog, Releasebot (CC/Codex/Cursor/Hermes/OpenClaw), Zenn, Qiita, Speakerdeck, mynavi.jp, Impress Watch, Gigazine, Zhihu, CSDN, GitHub CN trending, agensi.io, MCP Market, AI Weekly, mixed-news, Pluto Security, Dash Security, ccleaks, aicoder.com, benchlm, InfoQ, Dataconomy, Emergent, weaveos, vibecodinghub, Cellcog, explainx.ai, eesel.ai, tech-insider.org, kucoin.com, unite.ai

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 stories | 228+109+55 pts, 299+37+51 comments | 🌐 OpenShell (228/299); Weave Router 2.0 (109/37); Raven (55/51) |
| Web (global) | 52 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 11 pages | — | 🇯🇵 Zenn, Qiita, Speakerdeck, mynavi, Impress Watch, Gigazine |
| Web (China) | 9 pages | — | 🇨🇳 GitHub CN trending, Zhihu, CSDN, CNBlogs, aiposthub, unwire.pro |
| GitHub Trending | 5 digests | — | 🌐🇨🇳 Oct 1-2 multiple agents-radar forks |

---

## Synthesized Findings

### 1. [new] NVIDIA OpenShell (Sep 28): kernel-level secure agent runtime, 14.3k stars, 100+ firm coalition 🌐🇯🇵🇨🇳

**Claim:** NVIDIA launched OpenShell at GTC San Jose Sep 28 — Apache 2.0, deny-by-default agent sandbox that runs CC/Codex/OpenClaw/Hermes unmodified; HN 228 pts/299 comments; Anthropic, Cisco, Salesforce, SpaceXAI among 100+ partners.
**Evidence:**
- **Architecture:** 3-layer: Gateway (manages agent/sandbox lifecycles) + Supervisor (validates against policies from OUTSIDE sandbox) + Sandbox (kernel isolation via Landlock LSM + seccomp BPF)
- **Policy Prover:** formal methods mathematically verify permissions before applying; detects dangerous combinations when multiple agents collaborate
- **Privacy Router:** routes to frontier models only when policy permits; sensitive data stays local otherwise
- **Hardware complement:** NVIDIA Sentry on BlueField-4 DPU — monitors from outside execution environment; isolates agents in milliseconds; independent of host OS
- **Zero-mod install:** `openshell sandbox create --remote spark --from openclaw`; agents run unmodified
- **Anthropic integration:** Claude Managed Agents now leverages OpenShell; Rakuten + Notion first enterprise adopters
- **Partners:** Anthropic, Cisco, CrowdStrike, Dell, HPE, Hugging Face, JPMorganChase, Microsoft, Palantir, Palo Alto Networks, Perplexity, Red Hat, Salesforce, SAP, Scale AI, ServiceNow, SpaceXAI
- **GitHub:** 14.3k stars, 1,611 commits, 1.6k open issues/PRs
- **Stars:** +2,503 Oct 2 (GitHub trending #1); +1,280 Oct 1
- **HN 228 pts/299 comments:** skepticism: "A chip manufacturer proposes to sell more chips"; "The Sentry chip has to get it right every time; the contained ASI only has to be lucky once"; debate on whether agents can be usefully sandboxed
- 🇯🇵 mynavi.jp: "外部通信は、モデルに遠慮させるのではなく、技術的に不可能にすべきだ" ("External communication should be technically impossible, not merely discouraged by the model") — https://news.mynavi.jp/techplus/article/20260928-5041984/
- 🇨🇳 CN trending: "大厂进入Agent安全层" ("major tech firm enters agent security layer"); framing as maturation signal
- **Sources:** https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Launches-Open-Agent-Safety-Platform-to-Secure-Agents-From-Testing-to-Deployment/default.aspx, https://developer.nvidia.com/blog/run-autonomous-self-evolving-agents-more-safely-with-nvidia-openshell/, https://news.ycombinator.com/item?id=49879883, https://github.com/NVIDIA/OpenShell, https://www.eesel.ai/blog/nvidia-open-agent-safety-platform, https://www.unite.ai/anthropic-adds-nvidia-openshell-controls-to-claude-managed-agents/, https://www.explainx.ai/blog/nvidia-open-agent-safety-platform-openshell-sentry-2026, https://tech-insider.org/nvidia-openshell-sentry-ai-agent-safety-2026/, https://www.kucoin.com/news/flash/nvidia-launches-openshell-an-open-source-runtime-for-securing-autonomous-ai-agents, https://news.mynavi.jp/techplus/article/20260928-5041984/, https://www.watch.impress.co.jp/docs/news/2144232.html, https://gigazine.net/gsc_news/en/20260929-nvidia-open-agent-safety-platform/, https://unwire.pro/2026/09/29/nvidiaagentsafety/news/, https://www.aiposthub.com/nvidia-open-agent-safety-platform-openshell-sentry/

---

### 2. [new] Claude Mods (v2.1.287, Oct 1): TypeScript plugins that run inside CC process — unsandboxed; security research: 45% of public mods can exec host processes 🌐🇨🇳

**Claim:** Anthropic shipped Claude Mods in v2.1.287 (Oct 1): small TypeScript functions that run inside the CC process with full machine access; not sandboxed; can rewrite prompts, intercept tool calls, modify UI, approve permissions; Pluto Security found 14/31 public mods (45%) can execute host processes.
**Evidence:**
- **What mods can do:** rewrite prompts; intercept/block/rewrite/retry tool calls; approve or deny permission requests; redact data from tool output; modify interface; add buttons/inputs
- **Multiple mods stack** in load order; ship inside plugins; install via `/plugin` CLI or desktop
- **NOT sandboxed:** run with full machine permissions; processes spawned by a mod run OUTSIDE sandbox even if sandbox is enabled; can "read your secrets: environment variables and settings files, including an API key"
- **sec-default mod:** Team/Enterprise only — stops installed mods from overriding permission deny rules; personal plans unprotected
- **"You Should Know" built-in mod:** session watcher that flags missed items (first-party; requires telemetry; enable: `/plugin enable cc-plugin-you-should-know@builtin`)
- **Security research (Pluto Security):** 14 of 31 public mods can execute host processes; PoC demonstrated: malicious mod silently exfiltrates credentials + 834KB prompt history; fake credential dialog renders inside trusted CC client UI
- **Anthropic mitigation:** `claude plugin validate` to check capabilities before install; safe mode / config flag to disable; one hard boundary: mods cannot alter permission prompts themselves
- 🌐 New Stack headline: "No reason why everyone should have an identical Claude experience"
- 🇨🇳 CN CSDN/Zhihu reaction: impressed by extensibility; security concern noted in AI HOT digest
- **Sources:** https://claude.com/blog/claude-code-mods, https://ccleaks.com/news/claude-code-2-1-287-oct-2026, https://aicoder.com/news/news-20261002-claude-code-2-1-287-mods-you-should-know, https://mixed-news.com/en/claude-code-2-1-287-mods-not-sandboxed-api-key/, https://pluto.security/blog/claude-code-function-hooks-security/, https://dash.security/blog/claude-mods-the-new-attack-surface-built-in, https://aiweekly.co/alerts/anthropic-launches-claude-code-mods-typescript-agent-hooks, https://nerdschalk.com/are-claude-code-mods-sandboxed-what-they-can-access/, https://github.com/fu512647662-ai/AI-hot-news/issues/117

---

### 3. [new] Weave Router 2.0: open-source per-request model routing for CC/Codex/Cursor — Astra quality at 52% cost, HN 109 pts 🌐

**Claim:** Weave Router 2.0 (Apache 2.0, ~4.2k stars) is a drop-in proxy that routes each agent request to the optimal model; matches GPT-6 Astra on Terminal Bench 4.0 at 52% cost and 2.2x speed; HN Show HN 109 pts/37 comments.
**Evidence:**
- **Integration:** drop-in proxy for CC/Codex/Cursor/opencode/API clients; no agent code changes needed
- **HMM routing architecture:** traces session state history to distinguish similar-looking sessions; intelligent bucketing avoids 10^100 decision paths; cache-eviction optimization prevents unnecessary model switches
- **Benchmarks:** Terminal Bench 4.0 — Astra-equivalent pass rate at 52% cost, 2.2x faster; SWE Atlas — 54% cost, 2.5x faster
- **License:** Apache 2.0 (from router-v0.2.24 Sept 2026; previously Elastic 2.0)
- **HN comments:** "Different frontier models are good at different things! We'll be the ones combining them optimally" (adchurch); failure mode flagged: "models seem to convince each other about capabilities" (devmor)
- **LangChain parallel:** LangChain's own model router in OSS Agent Harness got 64% cost reduction on coding tasks (973 threads; PR merge rate parity)
- **Sources:** https://news.ycombinator.com/item?id=49911500, https://weaveos.com/blog/introducing-weave-router-2-0, https://vibecodinghub.org/tools/weave-router, https://remio.ai/post/weave-launches-intelligent-model-routing-tool-for-claude-code-codex-and-cursor, https://ai-tldr.dev/tools/weave-router/

---

### 4. [new] mattpocock/skills: 135k-star engineer-grade skill collection hits GitHub trending (+908/+883 two days running) 🌐🇨🇳

**Claim:** mattpocock/skills (Matt Pocock, TypeScript educator) reached 135k+ stars / 11,700 forks with 38 production-ready skills; SKILL.md-compatible; +908 Oct 1, +883 Oct 2 — sustained multi-day trending signal.
**Evidence:**
- **Skills:** planning (PRD writing, issue breakdown, interface design), development (TDD loops, architecture improvement, bug triage), tooling (pre-commit hooks, git guardrails), knowledge management (Obsidian vault, ubiquitous language)
- **Harness coverage:** Claude Code, Cursor, Codex, GitHub Copilot, Gemini CLI, OpenCode — any SKILL.md-compatible harness
- **Install:** `npx skills@latest add mattpocock/skills`; `/setup-matt-pocock-skills` once per repo; individual skills: `npx skills@latest add mattpocock/skills/tdd`
- **DSH plugin:** dsh-mattpocock-skills available for DeepSeek Harness ecosystem (CN reach)
- 🇨🇳 CN trending: framed as "Skills-as-Code paradigm" exemplar
- **Sources:** https://github.com/mattpocock/skills, https://aitoolly.com/ai-news/article/2026-09-27-matt-pocock-releases-open-source-ai-agent-skills-for-real-software-engineers-directly-from-agents-di, https://explainx.ai/blog/matt-pocock-agent-skills-real-engineers, https://geekbye.com/blog/mattpocock-skills-claude-code, https://skillsmp.com/creators/mattpocock/skills, https://dshfind.com/en/plugins/NmouZh/dsh-mattpocock-skills

---

### 5. [update] Claude Code v2.1.285-287 (Sep 29 – Oct 1): allowedProviders, Mods, permission counters, background time limits 🌐🇯🇵

**Claim:** NEW FACTS — 3 releases in 4 days: v2.1.285 adds `allowedProviders` managed setting + background command time limits; v2.1.286 adds SEP-2640 skills client (disabled flag `tengu_mcp_skills`) + permission counters; v2.1.287 ships Claude Mods (see finding #2).
**Evidence:**
- **v2.1.285 (Sep 28-29):** `allowedProviders` — restricts which API providers per machine; `CLAUDE_CODE_DISABLE_WEB_FETCH` env var; background Bash/PowerShell: 30min default limit, 2h max; `/desktop` command; `claude plugin configure`
- **v2.1.286 (Sep 30):** `tengu_mcp_skills` disabled flag — first internal SEP-2640 client (reads SKILL.md name/uri/digest; caps at 100 skills/server); permission prompt counters ("2 of 5" style); mouse support in fullscreen; credential expiry fix; parallel tool crash recovery
- **v2.1.287 (Oct 1):** Claude Mods (see finding #2); URL prompts for MCP auth; Remote Control reliability; Windows safety measures
- 🇯🇵 Qiita: "v2.1.285でallowedProviders設定が追加、組織向けプロバイダー制御が可能に" — enterprise governance feature noted by JP community
- **Sources:** https://releasebot.io/updates/anthropic/claude-code, https://code.claude.com/docs/en/whats-new, https://dev.classmethod.jp/en/articles/20260930-cc-updates-v2-1-285/, https://qiita.com/Takuya__/items/cd99e4c9c4bf01994d6c

---

### 6. [update] OpenAI DevDay (Sep 29): GPT-6.1 Sol in Codex, Dots always-on agents, Agents API computer use + multi-agent GA 🌐

**Claim:** NEW FACTS — DevDay Sep 29: GPT-6.1 Sol (Astra-quality at 1/5 price) default in Codex CLI v0.159.1+; Dots (always-on personal agents, GPT-6 Astra-powered, 4,000+ app integrations); Agents API expands to computer use + multi-agent + tool search + context compaction.
**Evidence:**
- **GPT-6.1 Sol:** ~matches GPT-6 Astra on agentic coding at 1/5 price; DeepSWE v1.1 parity; OSWorld 2.0 within 2pts; factual error rate 11.4% → 7.7% at low effort; available API as `gpt-6.1-sol`
- **Codex CLI v0.159.1:** GPT-6.1 Sol as default in bundled + Amazon Bedrock catalogs
- **Codex CLI v0.160.0 (Oct 2):** agent command center history browsing; X11 middle-click paste; projectless sessions; Guardian review (retrieves earlier user instructions + agent handoff context); Windows sandbox fixes
- **Dots:** always-on ChatGPT agents; own cloud computer; 4,000+ app connections; Custom Rules (what dots may do autonomously, must-ask-first, must-never); ChatGPT Space for human+dots collaboration; Pro/Business Premium first
- **Agents API:** computer use (GUI operation) + multi-agent coordination + tool search + context compaction now GA
- Paperclip PR #14942: added gpt-6.1-sol to shared coding harness pins
- **Sources:** https://benchlm.ai/blog/posts/openai-devday-2026, https://emergent.sh/news/openai-devday-2026, https://dataconomy.com/2026/09/30/openai-launches-gpt-6-1-sol-at-devday/, https://www.infoq.com/news/2026/10/openai-devday-2026/, https://releasebot.io/updates/openai/codex, https://betanews.com/article/openai-dots-agents-chatgpt/

---

### 7. [update] SEP-2640 (Skills over MCP): first disabled client landed in CC v2.1.286; Go SDK passes conformance; HyprPilot first harness to merge PR 🌐

**Claim:** NEW FACTS — CC v2.1.286 ships disabled `tengu_mcp_skills` flag (first internal prototype); Go SDK passes conformance suite; HyprPilot PR merged; still no mainstream harness shipping skills by default.
**Evidence:**
- **CC v2.1.286 client:** reads SKILL.md frontmatter (name, uri, digest); caps server at 100 skills; behind disabled flag
- **Server implementations shipping:** Hugging Face (v1), RenooLab (shipped week spec went Final), HyprPilot (PR #270 merged)
- **SDK status:** Go — passing conformance suite; TypeScript/Python/C# — open PRs
- **Community workaround:** many MCP servers wrap SKILL.md convention as MCP tools/resources (works today with CC/Cursor/VS Code)
- **Still** no mainstream IDE/CLI harness shipping skills/list by default; FastMCP has pre-v1 `skill://` shape
- **Sources:** https://github.com/zeke/skills-over-mcp, https://apievangelist.com/2026/09/22/skills-over-mcp-is-final-and-now-it-needs-servers/, https://modelcontextprotocol.io/community/working-groups/skills-over-mcp, https://github.com/modelcontextprotocol/experimental-ext-skills, https://github.com/hyprpilot/hyprpilot/pull/270

---

### 8. [update] OpenClaw: P0 stability regressions; user trust erosion; Hosted Gateway in final testing; no new feature release Sep 29 – Oct 2 🌐

**Claim:** NEW FACT — duanyytop ecosystem digest flags user trust erosion from regressions; P0 unresolved: SQLite WAL 2.8GB (Windows), event loop starvation, memory leaks, Windows session failures; stability now priority over features.
**Evidence:**
- OpenClaw v2026.8.34 (LTS equivalent); no feature release this window
- Current at v2026.9.7 per aiskill.market comparison
- **P0 unresolved:** SQLite WAL 2.8GB growth (Windows, #143524); event loop starvation (#149538); memory leaks in model catalog (#159662); Windows session creation failures (#161953)
- **User sentiment:** message loss, crash loops, config corruption flagged in ecosystem digest
- **Pipeline:** Hosted Gateway on bundled Bun (macOS): PR #161709 final testing; External backup (Cloudflare R2, external disks): PR #161913
- **Sources:** https://github.com/duanyytop/agents-radar/issues/3583, https://releasebot.io/updates/openclaw, https://aiskill.market/blog/openclaw-vs-hermes-vs-claude-code-three-runtimes-2026

---

**Still true** (ongoing threads, no new facts Sep 29 – Oct 2):
- **claude-sonnet-5-5**: CC v2.1.285+ default; still top Terminal-Bench agentic coding score (Coding Agent Index 68pts); ongoing
- **salesforce-enterprise-ai-harness**: FY28 rollout; no new updates
- **openrig-multi-agent-harness**: +640 Oct 2 trending; ongoing
- **hindsight-standalone-memory**: 40.5k+ stars; ongoing
- **jauvex-voice-multi-agent**: ongoing
- **claude-opus-5-5**: still trails Sonnet 5.5 on Terminal-Bench; no change
- **google-ax-agentic-runtime**: 11.2k+ stars; no new release
- **cursor-rollout-security-bots**: no new Cursor releases Sep 29 – Oct 2; Sep 23 releases ongoing
- **univer-office-harness**: 🇨🇳 ongoing
- **obra-superpowers-skills**: +455 Oct 2 trending; ongoing
- **hkuds-nanobot-personal-agent**: ongoing
- **hermes-agent-self-improving**: v0.21.5 still; v0.22.0 prep underway (abandoned RC found); canary only
- **openclaw-gateway-harness**: stability regressions (see finding #8)
- **sep-2640-mcp-skills-final**: first CC client landed (finding #7); still early adoption
- **cursor-router-workspace-plugins**: no new Cursor releases; ongoing
- **gitspawn-class-vulnerability**: ongoing; 4 flaws unpatched; OpenShell (finding #1) addresses some patterns at infrastructure level
- **harness-context-tax-problem**: Weave Router 2.0 (finding #3) addresses at routing layer; ongoing
- **harness-engineering-paradigm**: 🇯🇵 JP Zenn/Qiita harness engineering articles continue; ongoing
- **layered-oss-stack-over-single-framework**: OpenShell adds security layer beneath harnesses; ongoing
- **anthropic-managed-agents-mcp-tunnels**: OpenShell integration now announced (finding #1); ongoing
- **aws-strands-harness**: ongoing
- **claude-code-projects-parallel-threads**: ongoing
- **claude-code-mods-function-hooks**: Claude Mods expand this substantially (finding #2)
- **copilot-runtime-rust-rewrite**: Copilot CLI v1.0.91 Oct 1 (Windows sandbox + certs); ongoing
- **openai-agents-api-beta**: Agents API expanded at DevDay (finding #6)
- **vscode-1138-dev-container-agents**: ongoing
- **codex-cli-0155-voice-touchid**: v0.160.0 Oct 2 (finding #6)
- **cursor-projects-self-hosted-machines**: ongoing; computer use on Linux/Mac
- **reinventing-ai-employee-packages**: ongoing
- **builder-agent-native**: ongoing
- **beam-cli-harness-observer**: ongoing
- **meta-muse-code**: ongoing
- **colibri-lumabri-moe-inference**: ongoing
- **omarchy-herdr-agentic-linux**: ongoing
- **agensi-skill-marketplace**: ongoing
- **kilo-code-anaconda**: ongoing
- **harness-io-agent-ready-scm**: Harness Agent DLC (Jul 21) — AgentTrace, AI Evals, AIBOM; ongoing
- **extension-economy-explosion**: MCP Market 44,810+ servers; ongoing
- **addy-osmani-agent-skills**: ongoing
- **orca-ade-parallel-fleet**: ongoing
- **ponytail-laziest-dev-skill**: +1,194 Oct 2 trending; ongoing
- **trueforge-open-source-harness**: ongoing
- **aws-kiro-crew-open-source**: ongoing
- **hiddenlayer-agent-harness-security**: ongoing
- **longhorizon-harness-amap**: ongoing
- **caspian-talk-to-human-tool**: ongoing
- **kubell-whitelist-harness-tools**: ongoing
- **block-berd-desktop-workspace**: ongoing
- **loopx-long-horizon-control-plane**: ongoing
- **cloudflare-computer-agent-runtime**: ongoing
- **cursor-google-workspace-plugins**: ongoing
- **huzzah-pseudocode-editor**: ongoing
- **onecli-yc-s26-credential-gateway**: ongoing
- **harnessrouter-uhp-open-standard**: ongoing
- **codex-open-platform-harness**: Agents API expanded; ongoing
- **flue-2-react-hooks-harness**: ongoing
- **hax-c-minimalist-agent**: ongoing
- **copilot-autofix-dual-ai-security**: ongoing
- **bullet-yc-s26-coding-agent**: ongoing
- **book-to-skill-pdf-to-skill**: ongoing
- **cursor-origin-code-hosting**: ongoing
- **deepseek-harness-v01**: 🇨🇳 ~241k stars trending Oct 2; ongoing
- **prime-agent-rlm**: ongoing
- **aq-multiplayer-harness**: ongoing
- **qwen-code-alibaba**: 🇨🇳 ongoing
- **oh-my-agent**: ongoing
- **autoharness-deepmind**: ongoing
- **hoplite-yc-s26-cloud-deploy**: ongoing
- **vercel-ai-sdk-harnessagent**: ongoing
- **copilot-studio-ga-harness-billing**: ongoing
- **microsoft-agent-governance-toolkit**: ongoing
- **tinyagents-rust-recursive**: ongoing
- **sprocket-hardware-software-agent**: ongoing
- **gambit-reliable-agent-harness**: ongoing
- **nlah-natural-language-harnesses**: ongoing
- **skills-security-prompt-injection-36pct**: Mods surface now adds new injection vector (see finding #2)
- **claude-tag-slack-agent**: ongoing
- **mimo-code-xiaomi**: 🇨🇳 ongoing
- **ecc-cross-harness-os**: 270,665+ stars; ongoing
- **kimi-code-moonshot**: 🇨🇳 ongoing
- **runtime-yc-p26**: ongoing
- **noclick-always-on**: ongoing
- **nyx-offensive-testing**: ongoing
- **agentguard-security-tool**: ongoing
- **mcp-security-nsa-supply-chain**: NVIDIA/Anthropic OpenShell addresses supply-chain attack surface at infra level; ongoing
- **yc-qm-multiplayer-harness**: ongoing
- **jadepuffer-agentic-security**: ongoing
- **grok-build-xai-rust-harness**: ongoing
- **self-harness-auto-optimization**: ongoing
- **openharness-hkuds**: ongoing
- **antigravity-gemini-cli-successor**: ongoing
- **claw-code-claude-rewrite**: 🇨🇳 ongoing; CN dev MIIT compliance context (see CN findings)
- **metaharness-scaffold-generator**: ongoing
- **deerflow-superagent-harness**: 🇨🇳 ongoing
- **omnigent-meta-harness**: ongoing
- **zot-go-coding-harness**: ongoing
- **omp-omo-pi-derivatives**: ongoing
- **yorishiro-presence-harness**: ongoing
- **agentskills-open-standard**: ongoing
- **letta-agent-file-format**: ongoing
- **macos-harness-proving-ground**: ongoing
- **ahe-automated-harness-evolution**: ongoing
- **harness-internal-external-disambiguation**: 🇯🇵 ongoing
- **environment-architect-new-role**: 🇯🇵 Zenn/Qiita harness engineering articles continuing; ongoing
- **warp-oz-multi-harness**: ongoing
- **mozilla-otari-llm-gateway**: ongoing
- **statewright-guardrails**: ongoing
- **headroom-token-compression**: headroom 74,238 stars (Oct 2); ongoing
- **pi-minimal-agent-harness**: earendil-works/pi +298 Oct 2; ongoing
- **nvidia-skillspector-security**: OpenShell now extends NVIDIA's security surface; ongoing
- **cli-anything-hkuds**: ongoing
- **forge-acp-universal-cli**: ongoing
- **github-copilot-skills-mcp-ga**: Copilot CLI v1.0.91 Oct 1; ongoing
- **block-buzz-workspace**: ongoing
- **zcode-zhihu-agent-ide**: 🇨🇳 ongoing
- **devin-desktop-windsurf-rebrand**: no new release; ongoing
- **devin-fusion-multimodel**: ongoing
- **ambiance-unix-harness**: ongoing
- **kore-artemis-abl**: ongoing
- **open-agent-passport-oap**: ongoing
- **code-as-agent-harness-paper**: ongoing
- **tilde-harness-sdk**: ongoing
- **microsoft-maf-codeact**: ongoing
- **kiro-aws-spec-driven**: ongoing
- **cursor-spacex-acquisition**: ongoing
- **munder-difflin-office-of-clones**: ongoing
- **aura-mezmo-sre-harness**: ongoing
- **jetstream-clearance-zero-trust**: ongoing
- **tenable-cyberagents-exchange-inspector**: ongoing
- **vscode-1136-agent-merge**: ongoing
- **sonar-vortex-inside-loop**: ongoing
- **devspace-minimal-mcp-harness**: ongoing
- **skills-over-mcp-wg-sep2640**: see finding #7
- **accuknox-agentz-enterprise**: ongoing
- **gstack-virtual-engineering-team**: ongoing
- **graphify-codebase-knowledge-graph**: ongoing
- **atlas-source-control-agents**: ongoing
- **nodeterm-canvas-terminal-manager**: ongoing
- **paseo-multi-provider-orchestration**: ongoing
- **openchamber-ade-opencode**: ongoing
- **magnitude-local-inference-server**: ongoing
- **opencode-v2-rewrite**: ongoing
- **context-mode-tool-output-compression**: mksglu/context-mode +357 Oct 2; ongoing
- **openclaude-community-agent**: ongoing
- **ruflo-meta-harness-swarm**: ongoing
- **vscode-1137-agent-host-protocol**: ongoing
- **air-security-agent-firewall**: ongoing
- **watcher-apolloresearch-monitoring**: ongoing
- **harness-enterprise-governance-gap**: ongoing
- **claude-managed-agents-auto-permission**: OpenShell integration announced (finding #1); ongoing
- **harnessx-composable-foundry**: ongoing
- **tencentdb-agent-memory**: 🇨🇳 ongoing
- **penguinharness-self-improving**: ongoing
- **cloudflare-os-kitesurf**: ongoing
- **ante-antigma-single-binary**: ongoing
- **deepseek-harness-team**: 🇨🇳 ~241k stars Oct 2 CN trending; ongoing
- **gpt6-astra-provider-adapter-harness**: GPT-6.1 Sol now makes Codex harness cost competitive at Astra quality (finding #6); ongoing
- **paperclip-multi-agent-company-os**: PR #14942 adds GPT-6.1 Sol; ongoing

---

## Cross-Source Patterns

**1. Security layer below the harness is the new battleground (🌐🇯🇵🇨🇳)**
- OpenShell: hardware vendor entering with kernel-level enforcement (deny-by-default, formal policy verification)
- Claude Mods: simultaneously OpenED a new attack surface (unsandboxed TypeScript in the harness process); 14/31 public mods can exec host processes
- Tension: harnesses are becoming more extensible (Mods) AND more secured at the infrastructure level (OpenShell) simultaneously
- JP press: framed as determinism vs probabilism — "technically impossible, not merely discouraged"
- CN community: "大厂进入Agent安全层" signals maturation of agentic infrastructure
- Platforms: NVIDIA press, Anthropic blog, HN, mynavi.jp, Impress Watch, Gigazine, Zhihu/CSDN CN trending, Pluto Security, Dash Security

**2. Model routing as harness-layer cost optimization matures (🌐)**
- Weave Router 2.0 (Apache 2.0): 52% of Astra cost, 2.2x speed at equivalent quality (HN 109pts)
- LangChain's in-OSS-harness router: 64% cost reduction (973-thread study); PR merge rate parity
- Pattern: the model choice is becoming a dynamic routing decision inside the harness, not a static per-project config
- Platforms: HN, weaveos.com, vibecodinghub, GitHub CN trending

**3. Skills explosion: engineer-grade collections reaching mainstream (🌐🇨🇳)**
- mattpocock/skills: 135k+ stars, +908/+883 two days running — sustained trending, not a spike
- obra/superpowers: +455 Oct 2 trending; ponytail: +1,194 Oct 2 trending
- SEP-2640 first CC client (disabled flag) signals Anthropic commitment
- CN community: framing as "Skills-as-Code paradigm"; DSH plugin available
- Platforms: GitHub trending (multiple forks), skillsmp.com, explainx.ai, CSDN CN trending

**4. CN developer ecosystem under regulatory pressure (🇨🇳)**
- MIIT security notice covers Claude Code v2.1.91-v2.1.196 (data telemetry concerns)
- free-claude-code proxy project active on CSDN/Zhihu — CN developers routing CC to local/alternative models
- shareAI-lab/learn-claude-code (77.8k stars): CN self-built CC-like harness educational content
- Parallel: DSH (~241k stars) and Claw Code remain dominant CN-origin harness choices
- Platforms: Zhihu, CSDN, GitHub CN trending

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via search) | Nvidia wants to put a watchdog chip next to every AI agent | 228 | 299 | "The Sentry chip has to get it right every time; the contained ASI only has to be lucky once" | https://news.ycombinator.com/item?id=49879883 |
| adchurch | Show HN: Open-source model routing for coding agents (Weave Router 2.0) | 109 | 37 | "Different frontier models are good at different things! We'll be the ones combining them optimally" | https://news.ycombinator.com/item?id=49911500 |
| (via search) | Show HN: Raven (meta-orchestration harness) | 55 | 51 | "One prompt in, one result out is not practical for real products" (julesrms) | https://news.ycombinator.com/item?id=49890647 |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @anthropicbot.bsky.social | CC Mods announcement post | — | https://bsky.app/profile/anthropicbot.bsky.social/post/3mt33klm5t623 |
| @aidive.bsky.social | Visual breakdowns of Claude Code agent workflows | — | https://bsky.app/profile/aidive.bsky.social |
| @stealthdevtools.bsky.social | MCP + Claude Code dev tools discussion | — | https://bsky.app/profile/stealthdevtools.bsky.social |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | NVIDIA press release | https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Launches-Open-Agent-Safety-Platform-to-Secure-Agents-From-Testing-to-Deployment/default.aspx | OpenShell launch; 100+ partners |
| 🌐 | NVIDIA Dev Blog | https://developer.nvidia.com/blog/run-autonomous-self-evolving-agents-more-safely-with-nvidia-openshell/ | Gateway/Supervisor/Sandbox/Policy Prover architecture |
| 🌐 | Anthropic Blog | https://claude.com/blog/claude-code-mods | Claude Mods official announcement |
| 🌐 | ccleaks | https://ccleaks.com/news/claude-code-2-1-287-oct-2026 | v2.1.287 full changelog + Mods details |
| 🌐 | aicoder.com | https://aicoder.com/news/news-20261002-claude-code-2-1-287-mods-you-should-know | 1M context default on gateways; You Should Know mod |
| 🌐 | mixed-news | https://mixed-news.com/en/claude-code-2-1-287-mods-not-sandboxed-api-key/ | Mods API key access warning |
| 🌐 | Pluto Security | https://pluto.security/blog/claude-code-function-hooks-security/ | 14/31 public mods can exec host processes; credential theft PoC |
| 🌐 | Dash Security | https://dash.security/blog/claude-mods-the-new-attack-surface-built-in | Mods as new attack surface |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | v2.1.285-287 changelogs |
| 🌐 | ClassMethod | https://dev.classmethod.jp/en/articles/20260930-cc-updates-v2-1-285/ | v2.1.285: allowedProviders + background time limits |
| 🌐 | Releasebot Codex | https://releasebot.io/updates/openai/codex | Codex v0.159.1-v0.160.0 |
| 🌐 | benchlm | https://benchlm.ai/blog/posts/openai-devday-2026 | DevDay: GPT-6.1 Sol + Dots + Agents API |
| 🌐 | Dataconomy | https://dataconomy.com/2026/09/30/openai-launches-gpt-6-1-sol-at-devday/ | GPT-6.1 Sol details |
| 🌐 | InfoQ | https://www.infoq.com/news/2026/10/openai-devday-2026/ | DevDay developer recap |
| 🌐 | betanews | https://betanews.com/article/openai-dots-agents-chatgpt/ | Dots always-on agents |
| 🌐 | Weave Router blog | https://weaveos.com/blog/introducing-weave-router-2-0 | Weave Router 2.0 announcement |
| 🌐 | vibecodinghub | https://vibecodinghub.org/tools/weave-router | Router review; source-available |
| 🌐 | HN Show HN Weave | https://news.ycombinator.com/item?id=49911500 | 109 pts / 37 comments |
| 🌐 | HN Show HN Raven | https://news.ycombinator.com/item?id=49890647 | 55 pts / 51 comments; meta-orchestration |
| 🌐 | HN OpenShell | https://news.ycombinator.com/item?id=49879883 | 228 pts / 299 comments |
| 🌐 | mattpocock/skills | https://github.com/mattpocock/skills | 135k+ stars; 38 real-engineer skills |
| 🌐 | geekbye | https://geekbye.com/blog/mattpocock-skills-claude-code | Skills install guide + harness coverage |
| 🌐 | skillsmp.com | https://skillsmp.com/creators/mattpocock/skills | Marketplace listing |
| 🌐 | agents-radar #1557 | https://github.com/stevenko2002/agents-radar/issues/1557 | Oct 2 trending: OpenShell +2,503 |
| 🌐 | agents-radar #1537 | https://github.com/stevenko2002/agents-radar/issues/1537 | Oct 1 trending: OpenShell +1,280 |
| 🌐 | agents-radar #296 | https://github.com/kouweizhu/agents-radar/issues/296 | Oct 2: ECC 270k+, ponytail +1,194 |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OpenClaw stability regressions |
| 🌐 | OC ecosystem digest | https://github.com/duanyytop/agents-radar/issues/3583 | P0 bugs; user trust erosion |
| 🌐 | aiskill.market | https://aiskill.market/blog/openclaw-vs-hermes-vs-claude-code-three-runtimes-2026 | Three-way harness comparison Oct 2026 |
| 🌐 | SEP-2640 research | https://github.com/zeke/skills-over-mcp | CC v2.1.286 disabled flag discovery |
| 🌐 | MCP working group | https://modelcontextprotocol.io/community/working-groups/skills-over-mcp | Skills over MCP charter |
| 🌐 | HyprPilot PR | https://github.com/hyprpilot/hyprpilot/pull/270 | First harness SEP-2640 PR merged |
| 🌐 | Harness Agent DLC | https://www.prnewswire.com/news-releases/introducing-harness-agent-dlc-new-capabilities-for-the-ai-agent-development-lifecycle-302830967.html | AgentTrace + AI Firewall + AIBOM |
| 🌐 | Cellcog rankings | https://cellcog.ai/blog/best-ai-agent-harnesses/ | Oct 2026 rankings; CC top at 68pts |
| 🌐 | explainx.ai | https://www.explainx.ai/blog/nvidia-open-agent-safety-platform-openshell-sentry-2026 | OpenShell + Sentry explainer |
| 🌐 | eesel.ai | https://www.eesel.ai/blog/nvidia-open-agent-safety-platform | OpenShell cost/architecture |
| 🌐 | tech-insider.org | https://tech-insider.org/nvidia-openshell-sentry-ai-agent-safety-2026/ | 100+ firms join |
| 🌐 | kucoin | https://www.kucoin.com/news/flash/nvidia-launches-openshell-an-open-source-runtime-for-securing-autonomous-ai-agents | Anthropic + NVIDIA partnership |
| 🌐 | unite.ai | https://www.unite.ai/anthropic-adds-nvidia-openshell-controls-to-claude-managed-agents/ | Claude Managed Agents + OpenShell |
| 🌐 | emergent.sh | https://emergent.sh/news/openai-devday-2026 | All DevDay announcements |
| 🇯🇵 | mynavi.jp | https://news.mynavi.jp/techplus/article/20260928-5041984/ | OpenShell JP coverage; millisecond isolation |
| 🇯🇵 | Impress Watch | https://www.watch.impress.co.jp/docs/news/2144232.html | Open Agent Safety Platform JP |
| 🇯🇵 | Gigazine | https://gigazine.net/gsc_news/en/20260929-nvidia-open-agent-safety-platform/ | OpenShell announce JP |
| 🇯🇵 | Zenn @76hata | https://zenn.dev/76hata/articles/claude-code-customization-ecosystem | 4-layer CC customization strategy |
| 🇯🇵 | Qiita @nogataka | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | Harness engineering paradigm intro |
| 🇯🇵 | Qiita @shatolin | https://qiita.com/shatolin/items/ca1810e419fee5fd963b | 2026 CC plugins/MCP/tools summary |
| 🇯🇵 | Zenn @sasadango28 | https://zenn.dev/sasadango28/articles/claude-code-harness-engineering-20260415 | 5-layer harness design pattern |
| 🇯🇵 | Qiita @daisuke-nagata | https://qiita.com/daisuke-nagata/items/8f82bb7e2d51343657fd | Build harness stack bottom-up |
| 🇯🇵 | Zenn @kok1eeeee | https://zenn.dev/kok1eeeee/articles/claude-code-headless-agent-harness | Headless/non-interactive harness alternatives |
| 🇯🇵 | Zenn @lumichy | https://zenn.dev/lumichy/articles/openharness-agent-architecture-2026 | OpenHarness: 11.1k-line educational CC-like harness |
| 🇯🇵 | Qiita @Takuya__ | https://qiita.com/Takuya__/items/cd99e4c9c4bf01994d6c | Codex harness components Oct 1 |
| 🇯🇵 | Speakerdeck | https://speakerdeck.com/tame/aiezientoshi-dai-nohanesuenziniaringu-claude-codeshi-zhuang-bian | Conference slides: harness engineering |
| 🇨🇳 | agents-radar #633 | https://github.com/howe12/agents-radar/issues/633 | Oct 2 CN trending: OpenShell, shareAI-lab, agent-lightning |
| 🇨🇳 | AI HOT digest | https://github.com/fu512647662-ai/AI-hot-news/issues/117 | Claude Mods, LangChain router, OpenRouter |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2058338520884891698 | MIIT notice on CC; CN dev alternatives |
| 🇨🇳 | CSDN free-claude-code | https://blog.csdn.net/feiniao_coding/article/details/160628939 | CN proxy workaround for CC compliance |
| 🇨🇳 | CNBlogs MCP 2.0 | https://www.cnblogs.com/itech/p/22433542 | MCP 2.0 six features; Agent Skills native support |
| 🇨🇳 | TechFlowPost | https://www.techflowpost.com/en-US/newsletter/138053 | OpenShell 0.1.0 release CN coverage |
| 🇨🇳 | aiposthub | https://www.aiposthub.com/nvidia-open-agent-safety-platform-openshell-sentry/ | OpenShell + Sentry TC/CN explanation |
| 🇨🇳 | unwire.pro | https://unwire.pro/2026/09/29/nvidiaagentsafety/news/ | "圈養失控AI Agent" framing |
| 🇨🇳 | shareAI-lab/learn-claude-code | https://github.com/shareAI-lab/learn-claude-code | 77.8k stars; CN DIY CC harness |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per protocol)
├─ 🔵 X: 0 posts (excluded per protocol)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 3 stories │ 392 pts │ 387 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 3 profiles identified │ post content unavailable (Bluesky fetch returned minimal text)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~52 pages │ 🇯🇵 11 │ 🇨🇳 9
└─ 🗣️ Top voices: @adchurch (HN/Weave), @nogataka (Qiita), @76hata (Zenn), @kok1eeeee (Zenn), @lumichy (Zenn)
```

---

## Out of Scope but Notable

- **OpenAI Dots** — always-on personal AI agents with own cloud computers (DevDay Sep 29); Custom Rules permission model; ChatGPT Space human+agent collaboration. Fits general-purpose autonomous agent harnesses scope but Dots is primarily a consumer product, not a developer harness. Covered above under finding #6; mentioned here for paradigm note: "ambient agent with its own computer" crosses from developer tooling into personal computing.
- **microsoft/agent-lightning** (18.5k stars in CN trending Oct 2) — Microsoft RL-based agent TRAINING infrastructure (not a harness per se); signals that agent training pipelines are becoming next infra concern; may fit ai-software-factory topic.
- **MIIT (工信部) security notice on Claude Code** — CN government regulatory pressure on foreign coding agent harnesses; free-claude-code proxy ecosystem emerging as compliance workaround. This is a geopolitical/regulatory signal that may fit open-models-geopolitics topic as well.

---

## Data Gaps

- **/last30days skill**: unavailable (unknown skill error); full manual sweep via WebSearch + WebFetch
- **Reddit / X/Twitter**: excluded per protocol
- **Bluesky**: SOURCE HEALTH bluesky=OK; 3 profiles found but post content returned minimal text on WebFetch (Bluesky serves limited content without auth); no engagement metrics recoverable
- **YouTube / TikTok / Instagram**: not searched this run
- **Polymarket**: no agent harness-specific markets found
- **DuckDuckGo HTML endpoint**: CAPTCHA on both JP and CN queries; fallback to native WebSearch was complete
- **Zhihu direct fetch**: HTTP 403 on article page; data from search snippets only
- **HN Claude Mods discussion thread**: no direct HN thread ID found for Mods launch announcement; likely spread across multiple threads
- **Hermes v0.22 details**: only canary builds found; no stable release or release notes in this window
- **Cursor Oct 1-2 changes**: no changelog entries found for this window; changelog ends Sep 23
- **Coverage estimate**: ~82% — strong on NVIDIA OpenShell (major new finding), Claude Mods, CC v2.1.285-287, DevDay/GPT-6.1 Sol, Weave Router 2.0, mattpocock/skills, SEP-2640 update; JP + CN coverage solid via search fallback; gaps in Bluesky engagement, YouTube, long-tail HN discussion

---

## Key Quotes

> "外部通信は、モデルに遠慮させるのではなく、技術的に不可能にすべきだ。" ("External communication should be technically impossible, not merely discouraged by the model.") — mynavi.jp on NVIDIA OpenShell's design philosophy ([link](https://news.mynavi.jp/techplus/article/20260928-5041984/)) 🇯🇵

> "The Sentry chip has to get it right every time; the contained ASI only has to be lucky once." — HN commenter on NVIDIA OpenShell/Sentry ([link](https://news.ycombinator.com/item?id=49879883)) 🌐

> "A mod can rewrite a prompt, add new UI, replace a built-in feature, or add entirely new functionality." — Anthropic, Claude Code Mods announcement ([link](https://claude.com/blog/claude-code-mods)) 🌐

> "Treat that as a privileges bump for shared images: review which plugins you allow before you turn the new surface on for a whole fleet." — ccleaks.com on Claude Mods security implications ([link](https://ccleaks.com/news/claude-code-2-1-287-oct-2026)) 🌐

> "Different frontier models are good at different things! We'll be the ones combining them optimally." — adchurch, HN Weave Router 2.0 thread ([link](https://news.ycombinator.com/item?id=49911500)) 🌐

> "社区焦点已从'造Agent'转向'让一堆Agent安全、高效地协同工作'" ("Community focus shifted from 'building agents' to 'making agent fleets work safely and efficiently'") — howe12 CN agents-radar Oct 2 digest ([link](https://github.com/howe12/agents-radar/issues/633)) 🇨🇳

> "馬具なしの馬は、どこに走るかわからない。馬具ありの馬は、全力で正しい方向に走れる。" ("A horse without harness is unpredictable; with harness, it runs full-speed correctly.") — @nogataka on Qiita, harness engineering paradigm ([link](https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8)) 🇯🇵

> "大厂进入Agent安全层" ("Major tech firm enters agent security layer") — CN developer framing of NVIDIA OpenShell significance ([link](https://github.com/howe12/agents-radar/issues/633)) 🇨🇳
