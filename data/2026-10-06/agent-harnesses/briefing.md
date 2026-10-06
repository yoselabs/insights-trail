# AI Agent Harnesses — Daily Briefing
**Date:** 2026-10-06
**Query type:** GENERAL
**Sources:** HN, Web (global), Web (Japan), Web (China), GitHub Trending (agents-radar), Bluesky (profile-level only), aicoder.com, releasebot.io, ccleaks, alternativeto.net, explainx.ai, developersdigest.tech, gigazine.net, Zenn, Qiita, note.com, 80aj.com, Zhihu (snippets), cnblogs.com

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 3 stories | 1,645+125+78 pts, 573+56+66 comments | 🌐 Pi 1.0 (1,645/573); Headlong (125/56); Offrun (78/66) |
| Web (global) | 54 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 9 pages | — | 🇯🇵 Zenn, Qiita, note.com (npaka), Gigazine, dev.classmethod.jp |
| Web (China) | 8 pages | — | 🇨🇳 Zhihu (snippet), 80aj.com, QQ Tech/Tencent, cnblogs, agents-radar CN |
| GitHub Trending | 4 digests | — | 🌐🇨🇳 kouweizhu/stevenko2002/yaojiejia agents-radar Oct 4-6 |
| last30days skill | 0 | — | Unavailable (same as prior run) |

---

## Synthesized Findings

### 1. [new] Pi 1.0: minimalist harness reverses on MCP, ships Pi Durable — HN #1, 1,645 pts 🌐🇯🇵🇨🇳

**Claim:** Earendil shipped Pi 1.0 (Oct 1, MIT, 111.8k stars) — the coding agent that spent a year rejecting MCP now ships it natively via Codemode; companion Pi Durable adds crash-resistant long-running agents. HN #1 with 1,645 pts / 573 comments.

**Evidence:**
- **Codemode:** QuickJS sandbox where model writes JS to organize/parallelize tool calls; replaces multi-round LLM trips with scripted orchestration; ~40% token reduction (5,300→3,300 prompt tokens)
- **Pi Durable:** experimental; checkpoints every model/tool call; survives crashes; forked conversations; multiple clients steer one conversation; SQLite or JSONL storage
- **MCP:** deferred tool loading — servers only load when needed (reduces idle resource drain); virtual model routing (switch Opus/GPT-6 Luna etc.); Anthropic cache warming
- **Fullscreen TUI** now default; mid-conversation system edits; `curl -fsSL https://pi.dev/install.sh | sh`
- **Patches:** v1.0.3 (Oct 4): Azure Foundry Chat Completions; v1.0.4: MCP tool wildcard filtering, --no-mcp switch
- **JP:** npaka on note.com day-1 quickstart ([link](https://note.com/npaka/n/nc6ace5304805)); Gigazine covered it ([link](https://gigazine.net/gsc_news/en/20261002-pi-1-0/)); The Register: "Pi coding agent pulls a 180" ([link](https://www.theregister.com/ai-and-ml/2026/10/02/pi-coding-agent-pulls-a-180-and-adds-mcp-support/5300678)) 🇯🇵
- **CN:** 80aj.com two-article coverage Oct 2 + Oct 5 ([link](https://www.80aj.com/2026/10/02/ai-pi-mcp-durable/), [link](https://www.80aj.com/2026/10/05/pi-mcp-codemode-ai-programming/)); QQ News/Tencent ([link](https://news.qq.com/rain/a/20261002A064DT00?ptag=ima)); Zhihu: "极简主义黑马" (minimalist dark horse) framing; hubwiz.com: "Pi：编程代理的终局" ("Pi: The Endgame of Coding Agents") ([link](https://www.hubwiz.com/blog/pi-the-endgame-of-coding-agents/)) 🇨🇳
- **Sources:** [aicoder](https://aicoder.com/news/news-20261003-earendil-pi-1-0-agent-harness), [alternativeto](https://alternativeto.net/news/2026/10/pi-1-0-brings-native-mcp-support-and-pi-durable-for-long-running-crash-resistant-ai-agents/), [developersdigest](https://www.developersdigest.tech/blog/pi-1-0-release-guide-mcp-codemode-pi-durable), [HN](https://news.ycombinator.com/item?id=49428882 — wrong, Headlong), [note.com npaka](https://note.com/npaka/n/nc6ace5304805), [explainx.ai](https://explainx.ai/blog/earendil-pi-1-durable-minimal-harness-2026), [ai-tldr.dev](https://ai-tldr.dev/releases/earendil-pi-1-0/), [redreamality](https://redreamality.com/blog/pi-1-0-codemode-mcp-minimal-harness/), [techzine](https://www.techzine.eu/news/devops/144715/pi-1-0-will-include-mcp-and-a-dedicated-layer-for-long-running-ai-agents/)

---

### 2. [update] Claude Code v2.1.288-291 (Oct 1-6): agent.spawn, managed-agents onboarding, mod safety enforcement 🌐🇯🇵

**Claim:** NEW FACTS — 4 releases in 6 days: `agent.spawn` for subagent delegation added; v2.1.290 lands managed-agents onboarding with richer plugin/hook metadata; v2.1.291 fixes two regressions; deny/ask enforcement added for user-installed mods.

**Evidence:**
- **v2.1.288 (Oct 1):** broad reliability + UX; smarter resume/recovery; strengthened plugin/MCP handling; permission/auto mode fixes; cloud/SDK/terminal session issues resolved
- **v2.1.289 (Oct 2):** `agent.spawn` for teammates + agent state support; deny/ask rule enforcement for user-installed mods; plugin/terminal/shell-command safety fixes; large file rendering performance
- **v2.1.290 (Oct 6):** managed agents onboarding; richer plugin + hook metadata; `claude attach` / `claude logs` shortcuts; VS Code agent mapping + permission rules dialogs; "large wave of stability fixes across sessions, sandboxing, cloud use"
- **v2.1.291 (Oct 6):** fixes v2.1.290 regression (cloud sessions dropping permission prompt answers); fixes v2.1.288 regression (last messages lost on quit)
- **Community (Oct 6):** SubagentStart/SubagentStop event counting mismatch; Remote Control session restart reconnection failures; silent transcript deletion after 30 days (#69411)
- **Stars:** 149,532 (Oct 6 digest)
- **Sources:** [releasebot](https://releasebot.io/updates/anthropic/claude-code), [cc.bruniaux.com](https://cc.bruniaux.com/releases/), [claudeupdates.dev](https://www.claudeupdates.dev/), [agents-radar Oct 6](https://github.com/stevenko2002/agents-radar/issues/1640)

---

### 3. [new] Headlong: 10K-line Bash microharness for persistent RLM agents — 125 HN pts 🌐

**Claim:** Laude Institute + MIT shipped Headlong — a ~10K line Bash microharness where the agent never sleeps, runs a continuous self-guided inner monologue loop, and interacts with Slack/Telegram/mobile with no per-user sessions.

**Evidence:**
- **Architecture:** "Of bash, by bash, for bash" — tools/framework/memory/skills = executables + files; shellm tool is Bash recursive language model (RLM)
- **Persistence:** agent thinks continuously between inputs; single shared thought stream; memory compression by recency; "turn → FINAL → schedule wake-up" cycle
- **Multi-user limitation:** no data isolation between users — agent "will often just tell you" secrets shared by other users; critic: "major vulnerability dismissed in three sentences"
- **HN:** 125 pts / 56 comments; security concern dominant thread; Unix-philosophy praise from supporters
- **Sources:** [HN](https://news.ycombinator.com/item?id=49428882), [GitHub](https://github.com/laude-institute/headlong), [Laude](https://www.laude.org/updates/headlong-a-microharness-for-persistent-agents), [mer.vin comparison](https://mer.vin/2026/09/headlong-vs-reactive-harnesses-persistent-agents-bash/)

---

### 4. [new] Offrun: multi-agent workspace Mac app (Show HN, 78 pts) — git worktree isolation per agent 🌐

**Claim:** Offrun (Mac-only, free, no server) manages CC/Codex/AGY/Grok Build side-by-side; each agent gets its own git worktree; auto-switches accounts on quota; keys go direct to providers.

**Evidence:**
- **Worktree isolation:** 2 agents in same repo never touch same files; prevents collision
- **Quota management:** when agent hits limit, Offrun moves to login with remaining quota; carries full conversation
- **Privacy:** no Offrun server in the key path; code goes Mac → provider directly
- **Planned:** cloud version; mobile; integrations with Herdr/Pi/OpenCode/custom harnesses
- **HN comment:** "need a meta-orchestrator for all these agent orchestrators" (irony re: 68+ competing tools)
- **Differentiator vs Paseo/Orca:** focus on "managing multiple agents" vs "routing tasks"
- **Sources:** [HN](https://news.ycombinator.com/item?id=49942434), [offrun.dev](https://offrun.dev/)

---

### 5. [update] Agent skill trust crisis: 157 malicious skills confirmed, social impersonation actor dominates, signing tools emerge 🌐

**Claim:** NEW FACTS — Empirical study confirmed 157 malicious skills across 42,447 analyzed (6.3 issues/skill average); single actor = 54.1% of cases via brand impersonation; Claude Code Skills community issue #492 (43 comments): "Social skills misidentified as official"; STSS and skilltrust signing tools shipping.

**Evidence:**
- **Scale:** agentskill.sh now 200,000+ skills (up from 42k MCP servers in Aug 2026); security scanning cannot keep pace
- **Attack archetypes:** "Data Thieves" (credential exfil via supply chain) and "Agent Hijackers" (instruction manipulation); 93.6% removal rate validates responsiveness, not prevention
- **CC community:** GitHub issue #492 (43 comments): "social skills misidentified as official" — community-authored skills impersonating Anthropic official skills; demand for signing mechanism
- **ATR-2026-00430:** threat rule for natural-language trust-escalation / authority impersonation in skills
- **STSS** (kenhuangus/stss): open-source; cryptographic attestation between registries and execution; scan→evaluate→sign pipeline ([link](https://github.com/kenhuangus/stss))
- **skilltrust** (random1st/skilltrust): notarization + revocation for Agent Skills ([link](https://github.com/random1st/skilltrust))
- **NVIDIA** scan→evaluate→sign pipeline; detached `skill.oms.sig` signatures documented ([link](https://docs.nvidia.com/skills/agent-skill-trust-pipeline))
- **Sources:** [arxiv malicious skills](https://arxiv.org/html/2602.06547v1), [kenhuangus substack](https://kenhuangus.substack.com/p/agent-skill-trust-and-signing-service), [ATR rule](https://agentthreatrule.org/en/rules/ATR-2026-00430), [LLMSecurity awesome](https://github.com/LLMSecurity/awesome-agent-skills-security), [Medium crisis analysis](https://medium.com/@t79877005/the-ai-agent-skills-boom-is-under-attack-a-deep-security-crisis-3a7b7ded0208)

---

### 6. [update] DeepSeek Harness Desktop (Oct 2 worldwide preview): Cordis-bundled macOS/Windows app 🌐🇨🇳

**Claim:** NEW FACT — DeepSeek Harness opened worldwide public preview of standalone desktop app Oct 2; bundles Cordis plugin engine + web UI + sandboxing; eliminates CLI daemon management; in-app plugin creation.

**Evidence:**
- **What changed:** previously CLI-only; now native macOS/Windows app
- **Cordis integration:** all layers (model adapter, tools, filesystem, sandbox, agent loop, orchestration, interface) are Cordis services with temporal + spatial composability
- **Features:** visual trajectory playback; arbitrary session branching; multi-model sub-agent delegation
- **MIT license; community plugins invited**
- **CN coverage:** dominant in CN developer ecosystem (~241k stars)
- **Sources:** [aicoder](https://aicoder.com/news/news-20260925-deepseek-harness-desktop-standalone-release), [mpost.io](https://mpost.io/deepseek-releases-harness-v0-2-preview-for-macos-and-windows-with-in-app-plugin-creation/), [DSH repo](https://github.com/deepseek-ai/deepseek-harness)

---

### 7. [update] Qwen Code v0.25.0 (Oct 6): durable workspace-agent collaboration, A2A sharing 🇨🇳

**Claim:** NEW FACTS — Qwen Code v0.25.0 ships durable workspace-agent state layer (workspace-scoped identities, threads, runs, filesystem locking) plus A2A agent sharing and Mem0 bundled with CLI.

**Evidence:**
- **Broker provider:** generic controls with versioned worker contract (manifest/turn prep/tool approval/preflight/file history)
- **Durable state:** workspace-scoped identities + threads + messages + runs + token/turn accounting + stranded-run reconciliation
- **A2A:** agent sharing across workspaces; hosted tool approval flows; durable remote Shell result delivery
- **Mem0:** bundled with CLI
- **28,323 stars** (Oct 6 digest)
- **Critical bug:** "Tool repeated errors cause session dead-end loops consuming 5-14M tokens" (#10887 — 46 comments)
- **Sources:** [release](https://github.com/QwenLM/qwen-code/releases/tag/v0.25.0), [yaojiejia digest](https://github.com/yaojiejia/agents-radar/issues/256)

---

### 8. [update] OpenClaw v2026.10.1-beta.1 (Oct 6): stability work continues; P0 memory leak persists 🌐

**Claim:** NEW FACT — OpenClaw v2026.10.1-beta.1 released Oct 6 (102 merged PRs); session state preservation and workspace attachment reliability improved; SQLite WAL memory leak (~4-5GB/hour) still unresolved; 391,453 stars.

**Evidence:**
- **v2026.10.1-beta.1 fixes:** session state + memory preservation across registry changes; reliable remote workspace worker attachments; queued cancellation/transcript alias stalls resolved
- **P0 still active:** model catalog worker leaks ~4-5GB/hour; 200+ critical OOM events/day; SQLite WAL still problematic (1.4-2.8GB on Windows #143524)
- **v2026.9.8:** "update with caution" per clawstat.us Oct 5; v2026.8.34 LTS still recommended for production
- **Derivatives active:** ZeroClaw (50 issues/PRs), QwenPaw (image/session bugs), IronClaw (credential backend macOS)
- **Sources:** [releases.sh](https://releases.sh/openclaw), [clawstat.us](https://clawstat.us/), [OC Oct 4 digest](https://github.com/kouweizhu/agents-radar/issues/337)

---

### 9. [update] Microsoft Agent Framework v1.20.0 (Oct 2): native computer-use, stream-gated sessions, Foundry redesign 🌐

**Claim:** NEW FACTS — MAF v1.20.0 adds native computer-use to Responses clients (GUI operation), response-stream gates, session-scoped file isolation, DuckDB/SQL Server vector stores, and a breaking Foundry hosting redesign.

**Evidence:**
- **Computer-use:** added to Responses clients + Foundry project embeddings
- **Stream gates:** response-stream gates + buffering; AgentExecutor checkpoint-state TypedDict
- **Session isolation:** session-scoped file-access isolation
- **Storage:** DuckDB + SQL Server native vector-store connectors; TypeSafe AI connector
- **Foundry redesign (breaking):** request-scoped agent factories; persistent sandbox-isolated sessions; parsed/durable Invocations runs; configurable Responses history + background execution
- **Sources:** [MS AF releases](https://github.com/microsoft/agent-framework/releases), [releasebot MS](https://releasebot.io/updates/microsoft)

---

### 10. [update] JP harness engineering methodology crystallizes: 5-layer CC stack, hooks → skills → MCP 🇯🇵

**Claim:** NEW FACTS — New Oct 2026 Zenn articles by @ignission and @shintaroamaike formalize CC harness patterns: 4-layer CI/CD harness (hooks/Lefthook/skills/Actions); CLAUDE.md = permanent rules, Skills = on-demand workflow rules; "articulate team values first" as foundation.

**Evidence:**
- **@ignission ("狩りから稲作へ" — "From Hunting to Farming"):** Layer 1: CC hooks (pre-bash-guard blocks "implement later" procrastination, post-edit-lint runs Clippy); Layer 2: Lefthook + ast-grep (prevents architectural violations); Layer 3: CC skills (/pre-push-review parallel 4 agents, /merge-and-cleanup); Layer 4: CI + CodeRabbit ([link](https://zenn.dev/ignission/articles/f1c15646c990f1))
- **@shintaroamaike ("ルール自動生成"):** CLAUDE.md for permanent project-wide rules; Skill.md for workflow-specific on-demand rules; auto-generates rules from agent experience → continuous improvement loop ([link](https://zenn.dev/shintaroamaike/articles/df3ecc0ddee047))
- **JP consensus stack:** CLAUDE.md → hooks → skills → sub-agents → MCP (5-layer model solidifying across multiple authors)
- **@nogataka series continues:** "CC Source Code Leak Teaches 10 Harness Patterns from 500K TypeScript lines" ([link](https://qiita.com/nogataka/items/ebbbe74649eb441a34db))
- **dev.classmethod.jp:** OpenCode vs Pi vs DSH model-agnostic harness comparison ([link](https://dev.classmethod.jp/en/articles/reona-coding-harness-opencode-pi-dsh/))
- **"Environment Architect" role** continuing to emerge as JP specialization

---

**Still true** (ongoing threads, no new facts Oct 2–6):
- **nvidia-openshell-agent-runtime**: 14.3k+ stars; Oct 3+ no new releases; ongoing deployment
- **claude-code-mods-v2-1-287**: v2.1.289 adds deny/ask enforcement for user mods (partial update)
- **weave-router-model-routing**: ~4.2k stars; no new release; ongoing
- **mattpocock-skills-135k**: +751 Oct 4 trending; ongoing
- **openai-devday-2026-gpt61-dots**: no new facts Oct 2-6; ongoing
- **cn-miit-claude-code-notice**: ongoing; CN compliance workarounds active
- **claude-sonnet-5-5**: ongoing; still top coding benchmark
- **salesforce-enterprise-ai-harness**: ongoing; FY28 rollout
- **openrig-multi-agent-harness**: ongoing
- **hindsight-standalone-memory**: 40.5k+ stars; ongoing
- **jauvex-voice-multi-agent**: ongoing
- **claude-opus-5-5**: ongoing; still trails Sonnet 5.5 on Terminal-Bench
- **google-ax-agentic-runtime**: 11.2k+ stars; no new release
- **cursor-rollout-security-bots**: Cursor subscriptions/cloud agents still active (Aug launch); no new Oct changelog entries
- **univer-office-harness**: 🇨🇳 ongoing
- **obra-superpowers-skills**: +577 Oct 4 trending; ongoing
- **hkuds-nanobot-personal-agent**: ongoing
- **hermes-agent-self-improving**: v0.21.5 still current; v0.22.0 deferred; 251,464 stars
- **sep-2640-mcp-skills-final**: no new harness adoptions Oct 2-6; CC disabled flag still not enabled
- **cursor-router-workspace-plugins**: subscriptions/event-driven agents ongoing; no new Oct releases
- **gitspawn-class-vulnerability**: ongoing; 4 flaws unpatched
- **harness-context-tax-problem**: ongoing; caveman (109.9k stars) top token-reduction skill
- **layered-oss-stack-over-single-framework**: ongoing
- **anthropic-managed-agents-mcp-tunnels**: CC v2.1.290 managed-agents onboarding (finding #2)
- **gpt6-astra-provider-adapter-harness**: ongoing; Codex v0.160.1
- **paperclip-multi-agent-company-os**: ongoing
- **aws-strands-harness**: ongoing
- **claude-code-projects-parallel-threads**: ongoing
- **claude-code-mods-function-hooks**: v2.1.289 deny/ask rule enforcement for user mods added
- **copilot-runtime-rust-rewrite**: Copilot CLI v1.0.92 (Oct 5), v1.0.93-1 (Oct 6) (finding #9-adjacent)
- **openai-agents-api-beta**: ongoing; Agents API GA
- **vscode-1138-dev-container-agents**: ongoing
- **codex-cli-0155-voice-touchid**: v0.160.0 Oct 2, v0.160.1 Oct 6
- **cursor-projects-self-hosted-machines**: ongoing
- **reinventing-ai-employee-packages**: ongoing
- **builder-agent-native**: ongoing; **beam-cli-harness-observer**: ongoing; **meta-muse-code**: ongoing; **colibri-lumabri-moe-inference**: ongoing; **omarchy-herdr-agentic-linux**: ongoing; **agensi-skill-marketplace**: ongoing; **kilo-code-anaconda**: ongoing; **harness-io-agent-ready-scm**: ongoing
- **extension-economy-explosion**: agentskill.sh 200k+ skills; malicious skills crisis (finding #5)
- **addy-osmani-agent-skills**: 89.6k+ stars; 25 skills / 7 slash commands; ongoing
- **orca-ade-parallel-fleet**: ongoing; **ponytail-laziest-dev-skill**: 154,896 stars +1,894 Oct 5; **trueforge-open-source-harness**: ongoing; **aws-kiro-crew-open-source**: ongoing; **hiddenlayer-agent-harness-security**: ongoing; **longhorizon-harness-amap**: ongoing; **caspian-talk-to-human-tool**: ongoing; **kubell-whitelist-harness-tools**: ongoing; **block-berd-desktop-workspace**: ongoing; **loopx-long-horizon-control-plane**: ongoing; **cloudflare-computer-agent-runtime**: ongoing; **cursor-google-workspace-plugins**: ongoing; **huzzah-pseudocode-editor**: ongoing; **onecli-yc-s26-credential-gateway**: ongoing; **harnessrouter-uhp-open-standard**: ongoing
- **codex-open-platform-harness**: Codex v0.160.1 Oct 6
- **flue-2-react-hooks-harness**: ongoing; **hax-c-minimalist-agent**: ongoing; **copilot-autofix-dual-ai-security**: ongoing; **bullet-yc-s26-coding-agent**: ongoing; **book-to-skill-pdf-to-skill**: ongoing; **cursor-origin-code-hosting**: ongoing
- **deepseek-harness-v01**: Desktop preview Oct 2 (finding #6)
- **prime-agent-rlm**: ongoing; **aq-multiplayer-harness**: ongoing; **qwen-code-alibaba**: v0.25.0 Oct 6 (finding #7); **oh-my-agent**: ongoing; **autoharness-deepmind**: ongoing; **hoplite-yc-s26-cloud-deploy**: ongoing; **vercel-ai-sdk-harnessagent**: ongoing; **copilot-studio-ga-harness-billing**: ongoing; **microsoft-agent-governance-toolkit**: ongoing; **tinyagents-rust-recursive**: ongoing; **sprocket-hardware-software-agent**: ongoing; **gambit-reliable-agent-harness**: ongoing; **nlah-natural-language-harnesses**: ongoing
- **skills-security-prompt-injection-36pct**: 157 malicious confirmed; social impersonation crisis (finding #5)
- **claude-tag-slack-agent**: ongoing; **mimo-code-xiaomi**: 🇨🇳 ongoing; **ecc-cross-harness-os**: 272,984 stars ongoing; **kimi-code-moonshot**: 🇨🇳 ongoing; **runtime-yc-p26**: ongoing; **noclick-always-on**: ongoing; **nyx-offensive-testing**: ongoing; **agentguard-security-tool**: ongoing; **mcp-security-nsa-supply-chain**: ongoing; **yc-qm-multiplayer-harness**: ongoing; **jadepuffer-agentic-security**: ongoing; **grok-build-xai-rust-harness**: ongoing; **self-harness-auto-optimization**: ongoing; **openharness-hkuds**: ongoing
- **antigravity-gemini-cli-successor**: preview-09-2026 live; preview-05-2026 deprecated Oct 5 (finding #9-adjacent)
- **claw-code-claude-rewrite**: 🇨🇳 ongoing; **metaharness-scaffold-generator**: ongoing; **deerflow-superagent-harness**: 🇨🇳 ongoing; **omnigent-meta-harness**: ongoing; **zot-go-coding-harness**: ongoing; **omp-omo-pi-derivatives**: ongoing; **yorishiro-presence-harness**: ongoing; **agentskills-open-standard**: ongoing; **letta-agent-file-format**: ongoing; **macos-harness-proving-ground**: ongoing; **ahe-automated-harness-evolution**: ongoing; **harness-internal-external-disambiguation**: 🇯🇵 ongoing
- **environment-architect-new-role**: new Oct Zenn/Qiita articles (finding #10)
- **warp-oz-multi-harness**: ongoing; **mozilla-otari-llm-gateway**: ongoing; **statewright-guardrails**: ongoing; **headroom-token-compression**: ongoing
- **pi-minimal-agent-harness**: Pi 1.0 release — see finding #1 (thread upgraded to update)
- **nvidia-skillspector-security**: ongoing; **cli-anything-hkuds**: ongoing; **forge-acp-universal-cli**: ongoing
- **github-copilot-skills-mcp-ga**: Copilot CLI v1.0.92 Oct 5; v1.0.93-1 Oct 6
- **block-buzz-workspace**: ongoing; **zcode-zhihu-agent-ide**: 🇨🇳 ongoing; **devin-desktop-windsurf-rebrand**: ongoing; **devin-fusion-multimodel**: ongoing; **ambiance-unix-harness**: ongoing; **kore-artemis-abl**: ongoing; **open-agent-passport-oap**: ongoing; **code-as-agent-harness-paper**: ongoing; **tilde-harness-sdk**: ongoing
- **microsoft-maf-codeact**: v1.20.0 Oct 2 (finding #9)
- **kiro-aws-spec-driven**: ongoing; **cursor-spacex-acquisition**: ongoing; **munder-difflin-office-of-clones**: ongoing; **aura-mezmo-sre-harness**: ongoing; **jetstream-clearance-zero-trust**: ongoing; **tenable-cyberagents-exchange-inspector**: ongoing; **vscode-1136-agent-merge**: ongoing; **sonar-vortex-inside-loop**: ongoing; **devspace-minimal-mcp-harness**: ongoing; **skills-over-mcp-wg-sep2640**: ongoing; **accuknox-agentz-enterprise**: ongoing; **gstack-virtual-engineering-team**: ongoing; **graphify-codebase-knowledge-graph**: ongoing; **atlas-source-control-agents**: ongoing; **nodeterm-canvas-terminal-manager**: ongoing; **paseo-multi-provider-orchestration**: ongoing; **openchamber-ade-opencode**: ongoing; **magnitude-local-inference-server**: ongoing; **opencode-v2-rewrite**: OpenCode 211,896 stars; ongoing; **context-mode-tool-output-compression**: ongoing; **openclaude-community-agent**: ongoing; **ruflo-meta-harness-swarm**: ongoing; **vscode-1137-agent-host-protocol**: ongoing; **air-security-agent-firewall**: ongoing; **watcher-apolloresearch-monitoring**: ongoing; **harness-enterprise-governance-gap**: ongoing
- **claude-managed-agents-auto-permission**: v2.1.290 managed-agents onboarding (finding #2)
- **harnessx-composable-foundry**: ongoing; **tencentdb-agent-memory**: 🇨🇳 ongoing; **penguinharness-self-improving**: ongoing; **cloudflare-os-kitesurf**: ongoing; **ante-antigma-single-binary**: ongoing
- **deepseek-harness-team**: Desktop preview Oct 2 (finding #6)
- **gpt6-astra-provider-adapter-harness**: ongoing; **paperclip-multi-agent-company-os**: ongoing

---

## Cross-Source Patterns

**1. Pi 1.0 as the week's dominant story across all regions (🌐🇯🇵🇨🇳)**
- HN #1 with 1,645 pts — highest-engagement harness story since NVIDIA OpenShell (228 pts)
- JP: Gigazine, note.com, The Register JP, syusodo covered same day
- CN: 80aj.com dual coverage + QQ News/Tencent + Zhihu "minimalist dark horse" framing
- Narrative: the minimalist philosophy wins by refusing features — then shipping them when ready (MCP reversal = strength not weakness)
- Platforms: HN, aicoder.com, alternativeto, explainx.ai, note.com, Gigazine, 80aj.com, QQ, Zhihu

**2. Trust and identity for skills becomes a standalone infrastructure problem (🌐)**
- Scale: 200k+ skills, 6.3 vulnerabilities/skill average, 54.1% of malicious cases from single impersonator
- Community: CC Skills #492 (43 comments) on official-vs-community impersonation
- Tools shipping: STSS (cryptographic attestation), skilltrust (notarization + revocation), NVIDIA pipeline (scan→evaluate→sign)
- Pattern: skill ecosystems growing faster than security infrastructure; signing infrastructure now a market
- Platforms: HN digests, arxiv, GitHub community issues, kenhuangus substack, NVIDIA docs

**3. Agent spawn/delegation becoming a first-class harness primitive (🌐🇯🇵)**
- CC v2.1.289: `agent.spawn` for teammates with agent state support
- CC v2.1.290: managed agents onboarding
- Qwen Code v0.25.0: A2A agent sharing + Broker provider
- Pi Durable: multiple clients steer one agent
- JP: @ignission harness: /pre-push-review spawns 4 parallel agents; @shintaroamaike on-demand skill delegation
- Pattern: harnesses competing on inter-agent coordination as a core feature, not just tool dispatch
- Platforms: releasebot, QwenLM releases, aicoder.com, Zenn

**4. OpenClaw reliability crisis persists despite beta release; ecosystem fractures into derivatives (🌐)**
- v2026.10.1-beta.1 released Oct 6 (102 PRs) but P0 memory leak (~4-5GB/hour) still active
- Derivatives active: ZeroClaw, QwenPaw, IronClaw — fragmentation signal
- clawstat.us advisory: v2026.9.8 "update with caution"; LTS v2026.8.34 still recommended
- Quote pattern from Hermes/OpenClaw discourse: "They agree on what an agent is; they disagree on what controls it"
- Platforms: releases.sh, clawstat.us, agents-radar digests, composio.dev, thenewstack.io

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via digest) | Earendil ships Pi 1.0: stable minimal agent harness with Codemode+MCP; ~111.8k★ | 1,645 | 573 | "The agent that hated MCP now ships it" (DEV.to title) | https://aicoder.com/news/news-20261003-earendil-pi-1-0-agent-harness |
| andyk | Show HN: Headlong, a microharness for persistent agents | 125 | 56 | "Of bash, by bash, for bash; it's shells all the way down" | https://news.ycombinator.com/item?id=49428882 |
| (creator) | Show HN: Offrun | 78 | 66 | "need a meta-orchestrator for all these agent orchestrators" (comment) | https://news.ycombinator.com/item?id=49942434 |
| (creator) | Show HN: Television – open source GUI for your agent harness | 8 | 1 | "The future of personal computer interfaces isn't just chat" | https://news.ycombinator.com/item?id=49939817 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | aicoder.com | https://aicoder.com/news/news-20261003-earendil-pi-1-0-agent-harness | Pi 1.0: HN 1645 pts; MCP reversal; Codemode; Pi Durable |
| 🌐 | alternativeto.net | https://alternativeto.net/news/2026/10/pi-1-0-brings-native-mcp-support-and-pi-durable-for-long-running-crash-resistant-ai-agents/ | Pi 1.0 MCP + Pi Durable feature breakdown |
| 🌐 | developersdigest.tech | https://www.developersdigest.tech/blog/pi-1-0-release-guide-mcp-codemode-pi-durable | Full Pi 1.0 guide |
| 🌐 | The Register | https://www.theregister.com/ai-and-ml/2026/10/02/pi-coding-agent-pulls-a-180-and-adds-mcp-support/5300678 | "Pi coding agent pulls a 180 and adds MCP support" |
| 🌐 | Laude Institute | https://www.laude.org/updates/headlong-a-microharness-for-persistent-agents | Headlong: persistent agency microharness |
| 🌐 | GitHub headlong | https://github.com/laude-institute/headlong | 10K Bash; RLM; no per-user sessions |
| 🌐 | offrun.dev | https://offrun.dev/ | Offrun: git worktree per agent, quota management |
| 🌐 | television.run | https://television.run/ | Visual artifact GUI for any harness |
| 🌐 | releasebot CC | https://releasebot.io/updates/anthropic/claude-code | CC v2.1.288-291 changelogs |
| 🌐 | claudeupdates.dev | https://www.claudeupdates.dev/ | CC changelog plain English |
| 🌐 | agents-radar Oct 6 | https://github.com/stevenko2002/agents-radar/issues/1640 | Full Oct 6 community digest; all harness stars |
| 🌐 | yaojiejia digest Oct 6 | https://github.com/yaojiejia/agents-radar/issues/256 | Ecosystem star counts + key releases |
| 🌐 | kouweizhu Oct 4 | https://github.com/kouweizhu/agents-radar/issues/328 | Trending: ECC/superpowers/mattpocock/Pi |
| 🌐 | kouweizhu Oct 5 | https://github.com/kouweizhu/agents-radar/issues/340 | Trending: ponytail/claude-mem/addyosmani |
| 🌐 | DSH release | https://aicoder.com/news/news-20260925-deepseek-harness-desktop-standalone-release | DSH Desktop: Cordis-bundled app |
| 🌐 | DSH mpost | https://mpost.io/deepseek-releases-harness-v0-2-preview-for-macos-and-windows-with-in-app-plugin-creation/ | DSH v0.2 in-app plugin creation |
| 🌐 | Qwen Code v0.25.0 | https://github.com/QwenLM/qwen-code/releases/tag/v0.25.0 | Workspace-agent collaboration; A2A; Mem0 |
| 🌐 | releases.sh OpenClaw | https://releases.sh/openclaw | OpenClaw v2026.10.1-beta.1 release |
| 🌐 | clawstat.us | https://clawstat.us/ | v2026.9.8 update advisory |
| 🌐 | MS AF releases | https://github.com/microsoft/agent-framework/releases | MAF v1.20.0: computer-use + Foundry redesign |
| 🌐 | kenhuangus STSS | https://kenhuangus.substack.com/p/agent-skill-trust-and-signing-service | STSS: skill signing infrastructure |
| 🌐 | STSS repo | https://github.com/kenhuangus/stss | Cryptographic attestation for skill ecosystems |
| 🌐 | skilltrust | https://github.com/random1st/skilltrust | Notarization + revocation for Agent Skills |
| 🌐 | arxiv malicious skills | https://arxiv.org/html/2602.06547v1 | 157 malicious skills confirmed; 6.3 issues/skill |
| 🌐 | ATR rule | https://agentthreatrule.org/en/rules/ATR-2026-00430 | Trust-escalation threat rule for skills |
| 🌐 | NVIDIA skill trust pipeline | https://docs.nvidia.com/skills/agent-skill-trust-pipeline | scan→evaluate→sign pipeline |
| 🌐 | LLMSecurity awesome | https://github.com/LLMSecurity/awesome-agent-skills-security | Curated agent skills security resources |
| 🌐 | Copilot CLI changelog | https://github.com/github/copilot-cli/blob/main/changelog.md | v1.0.92 Oct 5; v1.0.93-1 Oct 6 |
| 🌐 | Codex releasebot | https://releasebot.io/updates/openai/codex | Codex v0.160.0-v0.160.1 |
| 🌐 | Antigravity changelog | https://antigravity.google/docs/changelog/ | preview-09-2026 live; preview-05-2026 deprecated |
| 🌐 | Antigravity CLI repo | https://github.com/google-antigravity/antigravity-cli | Antigravity CLI Go-based harness |
| 🌐 | Cursor changelog | https://cursor.com/changelog | No Oct entries; Sep 23 latest |
| 🌐 | Hermes changelog | https://hermes-ai.net/changelog/ | v0.21.5 current; v0.22.0 deferred |
| 🌐 | OpenClaw Oct 4 digest | https://github.com/kouweizhu/agents-radar/issues/337 | P0 bugs; derivative harnesses |
| 🌐 | aiskill.market comparison | https://aiskill.market/blog/openclaw-vs-hermes-vs-claude-code-three-runtimes-2026 | Three-way harness comparison |
| 🌐 | thenewstack.io OpenClaw/Hermes | https://thenewstack.io/openclaw-hermes-agent-harness/ | "agree on what an agent is; disagree on what controls it" |
| 🌐 | best-of-Agent-Harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 167 harnesses ranked |
| 🌐 | HN Offrun | https://news.ycombinator.com/item?id=49942434 | 78 pts; multi-agent workspace mgmt |
| 🌐 | caveman repo | https://github.com/juliusbrussee/caveman | 109.9k stars; 65% output token reduction |
| 🌐 | SEP-2640 charter | https://modelcontextprotocol.io/community/working-groups/skills-over-mcp | Skills over MCP working group |
| 🌐 | MCP ext-skills | https://github.com/modelcontextprotocol/experimental-ext-skills | SEP-2640 experimental extension |
| 🌐 | Skills Over MCP host | https://www.skillsovermcp.com/ | Host any GitHub repo as MCP server |
| 🌐 | agentskill.sh | (ref via search) | 200,000+ skills across 20+ harnesses |
| 🌐 | addyosmani/agent-skills | https://github.com/addyosmani/agent-skills | 89.6k+ stars; 25 skills; 6 lifecycle phases |
| 🌐 | mer.vin Headlong | https://mer.vin/2026/09/headlong-vs-reactive-harnesses-persistent-agents-bash/ | Headlong vs reactive harnesses comparison |
| 🌐 | explainx.ai Pi | https://explainx.ai/blog/earendil-pi-1-durable-minimal-harness-2026 | Pi 1.0 + Durable: Minimal vs Fullscreen |
| 🌐 | ai-tldr Pi | https://ai-tldr.dev/releases/earendil-pi-1-0/ | Pi 1.0 summary |
| 🌐 | redreamality Pi | https://redreamality.com/blog/pi-1-0-codemode-mcp-minimal-harness/ | Pi 1.0: Folding MCP into Codemode |
| 🌐 | Medium skills crisis | https://medium.com/@t79877005/the-ai-agent-skills-boom-is-under-attack-a-deep-security-crisis-3a7b7ded0208 | "AI Agent Skills Boom Is Under Attack" |
| 🌐 | SkillSentry arxiv | https://arxiv.org/pdf/2608.03485 | Adaptive Honey Worlds for dynamic skills safety testing |
| 🌐 | composio OC vs Hermes | https://composio.dev/content/openclaw-vs-hermes-agent | OpenClaw 2.0 vs Hermes comparison |
| 🌐 | HN digest Oct 4 | https://github.com/stevenko2002/agents-radar/issues/1600 | Offrun 72 pts; Television; Pi pod |
| 🇯🇵 | note.com / npaka | https://note.com/npaka/n/nc6ace5304805 | Pi 1.0 quickstart: Codemode/MCP/Skills guide 🇯🇵 |
| 🇯🇵 | Gigazine | https://gigazine.net/gsc_news/en/20261002-pi-1-0/ | Pi 1.0 JP mass-media coverage 🇯🇵 |
| 🇯🇵 | Zenn @ignission | https://zenn.dev/ignission/articles/f1c15646c990f1 | 4-layer harness: hooks→Lefthook→skills→CI 🇯🇵 |
| 🇯🇵 | Zenn @shintaroamaike | https://zenn.dev/shintaroamaike/articles/df3ecc0ddee047 | CLAUDE.md=permanent; Skills=on-demand 🇯🇵 |
| 🇯🇵 | Qiita @hisaho | https://qiita.com/hisaho/items/3e1a29bc8b265616614f | 7-axis CC harness optimization guide 🇯🇵 |
| 🇯🇵 | Qiita @nogataka (extended) | https://qiita.com/nogataka/items/ebbbe74649eb441a34db | 10 harness patterns from CC source 🇯🇵 |
| 🇯🇵 | dev.classmethod.jp | https://dev.classmethod.jp/en/articles/reona-coding-harness-opencode-pi-dsh/ | OpenCode vs Pi vs DSH model-agnostic comparison 🇯🇵 |
| 🇯🇵 | The Register (JP reach) | https://www.theregister.com/ai-and-ml/2026/10/02/pi-coding-agent-pulls-a-180-and-adds-mcp-support/5300678 | "Pi coding agent pulls a 180 and adds MCP support" 🇯🇵 |
| 🇨🇳 | 80aj.com (Oct 2) | https://www.80aj.com/2026/10/02/ai-pi-mcp-durable/ | Pi 1.0: MCP + Pi Durable CN coverage 🇨🇳 |
| 🇨🇳 | 80aj.com (Oct 5) | https://www.80aj.com/2026/10/05/pi-mcp-codemode-ai-programming/ | Pi 1.0 Codemode practical guide 🇨🇳 |
| 🇨🇳 | QQ News / Tencent | https://news.qq.com/rain/a/20261002A064DT00?ptag=ima | Pi 1.0: "为何接纳MCP" CN mainstream 🇨🇳 |
| 🇨🇳 | hubwiz.com | https://www.hubwiz.com/blog/pi-the-endgame-of-coding-agents/ | "Pi：编程代理的终局" bold CN framing 🇨🇳 |
| 🇨🇳 | cnblogs.com | https://www.cnblogs.com/itech/p/19964192 | 六大框架横评：Skills/MCP 支持比较 🇨🇳 |
| 🇨🇳 | agents-radar Oct 6 CN | https://github.com/stevenko2002/agents-radar/issues/1640 | Daily digest: all star counts + new issues 🇨🇳 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per protocol)
├─ 🔵 X: 0 posts (excluded per protocol)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 4 stories │ 1,856 pts │ 696 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (not searched this run; SOURCE HEALTH bluesky=OK but not queried)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~54 pages │ 🇯🇵 9 │ 🇨🇳 8
└─ 🗣️ Top voices: andyk/@laude-institute (Headlong), earendil-works (Pi 1.0), @ignission/@shintaroamaike (Zenn), kenhuangus (STSS), @npaka (note.com JP)
```

---

## Out of Scope but Notable

- **Pi pod (pipod.dev)** — RBAC sandbox execution for Pi coding agent; self-hosted; composable environments; native iOS/Android. Fits agent-harnesses scope fully. Noted here as a distinct emerging product layered on Pi 1.0 that may deserve its own thread.
- **Television (television.run)** — low engagement (8 HN pts) but interesting pattern: visual artifact UI as a harness sidecar. "Artifacts" as a paradigm beyond chat could belong to an AI-UX topic if one exists.
- **caveman (JuliusBrussee/caveman, 109.9k stars)** — skill that makes AI "talk like a caveman" for 65% output token reduction; viral; also has a proxy for 33% input token reduction. Not a harness but a paradigm: token reduction as a skill, not a harness feature.
- **CopilotKit/CopilotKit (37,747 stars)** — AG-UI Protocol frontend stack for agents; React/Angular/mobile. Fits harnesses topic broadly but is primarily a frontend SDK; may belong to an AI-frontend topic.
- **OpenMontage (calesthio/OpenMontage, 24k stars)** — first open-source agentic video production system; 12 pipelines / 700+ skills; works with CC/Cursor/Copilot. Out-of-scope (not coding/general-purpose agent harness) but notable as skills-over-domain-expertise pattern.

---

## Data Gaps

- **last30days skill:** unavailable (same as Oct 2 run); full manual sweep via WebSearch + WebFetch
- **DuckDuckGo HTML endpoint:** CAPTCHA on both JP and CN queries; fallback to native WebSearch was complete
- **Bluesky:** SOURCE HEALTH bluesky=OK; not queried this run (low ROI in prior run; Bluesky post content not reliably accessible without auth)
- **Reddit / X/Twitter:** excluded per protocol
- **YouTube / TikTok / Instagram:** not searched
- **Polymarket:** no agent harness-specific markets active
- **Zhihu direct fetch:** HTTP 403; data from search snippets only
- **Hermes v0.22:** not yet released; canary only; no release notes
- **Cursor Oct 2026 changelog:** no entries found; latest Sep 23
- **OpenCode major release:** no Oct 2-6 releases found; GitLab provider bump only
- **Coverage estimate:** ~83% — strong on Pi 1.0 (dominant story), CC v2.1.288-291, DeepSeek Harness Desktop, Qwen Code, OpenClaw beta, MAF v1.20.0, Headlong, Offrun, skill trust crisis; JP/CN coverage solid via search fallback; gaps in Bluesky, YouTube, long-tail HN discussion, Cursor (no new Oct entries verified separately from changelog direct fetch)

---

## Key Quotes

> "Pi 1.0 just hit #1 on Hacker News: The Agent That Hated MCP Now Ships It." — DEV Community headline ([link](https://dev.to/ashraf_chowdury09/pi-10-just-hit-1-on-hacker-news-the-agent-that-hated-mcp-now-ships-it-1nkp)) 🌐

> "Of bash, by bash, for bash; it's shells all the way down." — andyk, Headlong README / Show HN ([link](https://news.ycombinator.com/item?id=49428882)) 🌐

> "The future of personal computer interfaces isn't just chat, any more than it's MS-DOS. Artifacts are an early first step beyond chat." — Television Show HN creator ([link](https://news.ycombinator.com/item?id=49939817)) 🌐

> "Pi：编程代理的终局" ("Pi: The Endgame of Coding Agents") — hubwiz.com CN framing ([link](https://www.hubwiz.com/blog/pi-the-endgame-of-coding-agents/)) 🇨🇳

> "STSS is the missing security layer between skill registries and skill execution, treating every skill as untrusted code and requiring proof via a cryptographically signed attestation before that skill is allowed to load." — kenhuangus, STSS announcement ([link](https://kenhuangus.substack.com/p/agent-skill-trust-and-signing-service)) 🌐

> "ハーネス設計の基盤は'チームが何を大事にするか'の言語化" ("The foundation of harness design is articulating what the team values") — @ignission, Zenn ([link](https://zenn.dev/ignission/articles/f1c15646c990f1)) 🇯🇵

> "OpenClaw and Hermes agree on what an agent is. They disagree on what controls it." — The New Stack ([link](https://thenewstack.io/openclaw-hermes-agent-harness/)) 🌐

> "need a meta-orchestrator for all these agent orchestrators" — HN commenter on Offrun Show HN ([link](https://news.ycombinator.com/item?id=49942434)) 🌐
