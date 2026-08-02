# AI Agent Harnesses — Daily Briefing
**Date:** 2026-07-29
**Query type:** GENERAL
**Sources:** Hacker News, GitHub, Web (global), Web (Japan), Web (China), YouTube (referenced), Bluesky (limited), ModelContextProtocol Blog, Developer Blogs

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 7 threads | ~300+ points total | Rate-limited on direct HN fetch; HN item content via supplementary search |
| GitHub | 15+ repos | 23.3k–221k stars | Grok-Build (23.3k, new), OpenHarness (15.1k, new), OpenCode (160k) |
| Web (global) | 85+ pages | — | 🌐 15 distinct search queries + WebFetch |
| Web (Japan) | 10 pages | — | 🇯🇵 Qiita (4), Zenn (5), CodeZine (1) via DuckDuckGo JP + WebSearch JP |
| Web (China) | 8 pages | — | 🇨🇳 CSDN (3), Zhihu (1), jishuzhan (1), others via DuckDuckGo ZH + WebSearch ZH |
| YouTube | 1 video | — | Hermes Agent update coverage |
| Bluesky | 0 posts | — | No dedicated agent harness posts surfaced via search (back-channel: bluesky=OK) |
| Polymarket | 0 markets | — | None found on this topic |

---

## Synthesized Findings

**Delta note:** Prior state carries 20 threads, all first seen 2026-07-27. Any finding not matching an existing thread is `[new]`; threads with a genuine new fact since July 27 are `[update]`.

---

### 1. [new] MCP 2026-07-28 Final Specification: Protocol Goes Stateless 🌐

**Published yesterday (July 28, 2026).** The Model Context Protocol published its largest revision since launch as both a Release Candidate (locked May 21) and finalized specification (published July 28). The headline change: **MCP is now stateless at the protocol layer** — the `initialize` handshake and `Mcp-Session-Id` header are eliminated, making any server instance capable of handling any request and enabling standard round-robin load balancing without sticky sessions.

**Five major changes:**
1. **Stateless core** — client metadata travels in `_meta` fields on each request; self-contained calls
2. **Extensions framework** — `ext-*` prefix namespace; two official extensions at launch:
   - *MCP Apps*: servers deliver interactive HTML UIs in sandboxed iframes
   - *Tasks Extension*: stateless task handles driven via `tasks/get`, `tasks/update`, `tasks/cancel`
3. **Authorization hardening** — six SEPs strengthen OAuth/OpenID Connect alignment; `iss` validation per RFC 9207
4. **New headers** — `Mcp-Method`/`Mcp-Name` for header-based routing; `ttlMs`/`cacheScope` for cache freshness; W3C Trace Context for distributed tracing
5. **Deprecations** — Roots, Sampling, and Logging deprecated with 12-month runway; HTTP+SSE transport classified Deprecated

**Breaking changes:** `initialize` handshake removal; error code shift from `-32002` to `-32602` for missing resources.

Tier 1 SDK maintainers are expected to ship support within a 10-week validation window. Microsoft's Azure App Service team published immediate guidance on what the stateless change means for scaling.

> "MCP is the universal socket for AI agents, replacing fragmented tool integrations" (MCP是AI智能体的通用插座) — Zhihu community, 2026 ([link](https://zhuanlan.zhihu.com/p/2016572626777171185))

Sources: [MCP RC post](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/) · [Final spec](https://blog.modelcontextprotocol.io/posts/2026-07-28/) · [Stacktree changes analysis](https://stacktr.ee/blog/mcp-2026-spec-changes) · [WorkOS auth focus](https://workos.com/blog/mcp-2026-spec-agent-authentication) · [Microsoft Azure implications](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222) · [SecurityWeek](https://www.securityweek.com/new-enterprise-ready-mcp-specification-brings-new-security-challenges/) · [mcp.directory](https://mcp.directory/blog/mcp-2026-07-28-release-candidate) · [BOVO Digital](https://www.bovo-digital.tech/en/blog/mcp-2026-specification-stateless-enterprise-agents) · [AAIF maturity](https://aaif.io/blog/mcp-is-growing-up)

Platforms: Web (global), Web (China) 🌐 🇨🇳

---

### 2. [update] Agentic Security Crisis: JADEPUFFER Ransomware + Ant Group Response 🌐

**New fact since July 27:** First documented fully agentic ransomware (JADEPUFFER, Sysdig, July 1, 2026) emerged, followed by Ant Group's SingGuard-NSFA security guardrail (July 14, 2026) — events not captured in the prior mcp-security thread, which covered NSA MCP guidelines and skill supply-chain attacks.

**JADEPUFFER (July 1):** Sysdig Threat Research documented an end-to-end LLM-driven extortion campaign. Initial access via CVE-2025-3248 (exposed Langflow instance). The agent conducted reconnaissance, lateral movement, and database extortion without human operator skill: a failed login was corrected in **31 seconds**. The encryption key was generated once, printed to a log, and never stored — **data is unrecoverable even if the ransom is paid**. TechCrunch noted "the attack still needed a human" for initial access — but the autonomous execution chain is the threat model.

> "An LLM agent can chain reconnaissance, credential theft, lateral movement, persistence, and destruction without the operator possessing deep expertise in any one step." — Sysdig ([link](https://www.sysdig.com/blog/jadepuffer-agentic-ransomware-for-automated-database-extortion))

**Ant Group SingGuard-NSFA (July 14):** Open-source agent runtime guardrail released days after JADEPUFFER. Focuses on behavior during execution (not content moderation): catches prompt injection, credential theft, lateral movement, privilege escalation before the agent executes. Specs: 0.8B model (performance comparable to larger guardrail models), 9B model (~50ms latency for production), 185 operational threat scenarios, ~100,000 multilingual security test samples across 133 languages.

Sources: [Sysdig JADEPUFFER](https://www.sysdig.com/blog/jadepuffer-agentic-ransomware-for-automated-database-extortion) · [TechCrunch nuance](https://techcrunch.com/2026/07/06/the-first-ai-run-ransomware-attack-still-needed-a-human/) · [Security Magazine](https://www.securitymagazine.com/articles/102408-researchers-discover-first-documented-case-of-agentic-ransomware) · [TechRadar](https://www.techradar.com/pro/security/experts-warn-of-the-first-documented-case-of-agentic-ransomware-dangerous-jadepuffer-attack-run-entirely-by-an-llm) · [TechTimes data loss](https://www.techtimes.com/articles/319906/20260708/first-ai-agent-ransomware-destroyed-data-even-payment-could-not-recover.htm) · [Outpost24 attack reconstruction](https://outpost24.com/blog/jadepuffer-agentic-ransomware/) · [Ant Group SingGuard (TechTimes)](https://www.techtimes.com/articles/320508/20260714/ant-group-open-sources-agent-security-tool-days-after-agentic-ransomware-hit.htm) · [OpenSourceForYou](https://www.opensourceforu.com/2026/07/new-open-source-ai-security-guardrails/)

Platforms: Web (global) 🌐

---

### 3. [update] Microsoft MAF Harness Goes GA + VSCode 1.130 Agent Host Protocol 🌐

**New fact:** Microsoft Agent Framework shipped its stable, batteries-included **Harness core on July 22, 2026** — distinct from the MAF 1.0 GA (April 2) and BUILD 2026 announcements (CodeAct) already in the prior thread. The Harness GA delivers the loop, planning, memory, context management, approval workflows, and OpenTelemetry in both Python and .NET. Four features remain preview-only: Background agents, File access (now **opt-in only**, having been default-enabled in preview — principle of least privilege), Looping, and Shell tooling. The team validated with google/gemma-4-12b locally, demonstrating even 12B models can run all preview features.

🇯🇵 Japanese developer coverage (Zenn) highlighted the **File access reversal** — opt-out in preview → opt-in in GA — as a key harness design lesson: "The harness controls what the model can touch. Defaulting to less is always safer."

**Simultaneous: VSCode 1.130 (July 22)** introduced the **Agent Host Protocol (AHP)**: agent sessions now run in a dedicated process decoupled from VS Code window lifetime. Multiple windows connect to the same session; sessions survive window closure. Also: worktree isolation for all harnesses (Claude and Codex sessions can run Git worktrees for parallel features), assisted tool approvals (model evaluates tool-call risk to reduce interruptions), and compact Agents window with file-level stats.

Sources: [MAF Harness GA](https://devblogs.microsoft.com/agent-framework/the-microsoft-agent-framework-harness-is-now-released/) · [MAF at BUILD 2026](https://devblogs.microsoft.com/agent-framework/microsoft-agent-framework-at-build-2026-announce/) · [Zenn MAF Part 1](https://zenn.dev/yy7613/articles/ca60a03f4181e4) · [Zenn MAF Part 2](https://zenn.dev/yy7613/articles/0b92803c392341) · [VSCode 1.130 release](https://code.visualstudio.com/updates/v1_130) · [Neowin rearchitecting](https://www.neowin.net/news/microsoft-lands-visual-studio-code-1130-with-agent-rearchitecturing/) · [VS Magazine agent host](https://visualstudiomagazine.com/articles/2026/07/23/vs-code-1-130-expands-agent-host-and-review-tools.aspx) · [InfoWorld agents window](https://infoworld.com/article/4200970/visual-studio-code-1-130-shines-on-agents-window.html) · [ntcompatible AHP TypeScript 7](https://www.ntcompatible.com/story/visual-studio-code-1130-ships-agent-host-ai-permissions-and-typescript-7)

Platforms: Web (global), Web (Japan) 🌐 🇯🇵

---

### 4. [new] Grok-Build: SpaceXAI Open-Sources Rust Agent Harness TUI 🌐

SpaceXAI open-sourced **Grok-Build** on July 15–16, 2026 (synced from internal monorepo). 23.3k GitHub stars. Language: **Rust**, Apache 2.0. Full-screen, mouse-interactive TUI that understands codebases, edits files, executes shell commands, searches the web, and manages tasks — operates interactively, headlessly for CI, or embedded in editors via the **Agent Client Protocol (ACP)**, positioning ACP as a potential complement to LSP for agent integration.

Extension system: MCP servers, custom skills, plugins, hooks, subagents. The community immediately forked to remove telemetry. The xAI team reset usage limits for all users simultaneously with the open-source release.

> "SpaceXAI's coding agent harness and TUI. Fullscreen, mouse interactive, extensible." — xai-org/grok-build README ([link](https://github.com/xai-org/grok-build))

Sources: [GitHub repo](https://github.com/xai-org/grok-build) · [SpaceXAI announcement](https://x.ai/news/grok-build-open-source) · [MarkTechPost coverage](https://www.marktechpost.com/2026/07/15/spacexai-open-sources-grok-build-the-rust-agent-harness-tui-and-tool-layer-behind-its-coding-cli/) · [explainx guide](https://explainx.ai/blog/grok-build-open-source-spacexai-july-2026) · [Telemetry-free fork](https://github.com/yx-zero/grok-build) · [daily.dev](https://daily.dev/posts/github---xai-org-grok-build-spacexai-s-coding-agent-harness-and-tui-fullscreen-mouse-interactive--2gkjshyu6)

Platforms: Web (global) 🌐

---

### 5. [new] Self-Harness: Agents That Rewrite Their Own Operating Harness 🌐 🇨🇳

Shanghai AI Lab published **arXiv:2606.09498** ("Self-Harness: Harnesses That Improve Themselves", June 8, 2026), a paradigm where LLM agents autonomously improve their own operating harness without a human engineer or a stronger external model. Three-stage loop: **Weakness Mining** (analyze execution traces) → **Harness Proposal** (propose minimal targeted edits to system prompts, tools, memory, verification rules, policies) → **Proposal Validation** (sandboxed A/B testing).

Results on Terminal-Bench 2.0:
- MiniMax M2.5: 40.5% → 61.9% (+52.6%)
- Qwen3.5-35B-A3B: 23.8% → 38.1% (+60.1%)
- GLM-5: 42.9% → 57.1% (+33.1%)

🇨🇳 Chinese CSDN community reports "+104% performance improvement" — likely citing a specific benchmark subset or the best-case figure.

Related work at same time: Tsinghua's **SEED** self-evolving framework (+45.9pp on ALFWorld), and **COMFYCLAW** (arXiv:2607.01709), a self-evolving skill harness for image-generation workflows.

Lilian Weng synthesized this research cluster in "Harness Engineering for Self-Improvement" (July 4, 2026), arguing: "The layer between the raw model and the real-world context seems to be as important as the model's raw intelligence." She identified seven future challenges including diversity collapse in evolutionary loops and reward hacking vulnerabilities.

Sources: [arXiv:2606.09498](https://arxiv.org/pdf/2606.09498) · [alphaXiv](https://www.alphaxiv.org/overview/2606.09498v1) · [VentureBeat](https://venturebeat.com/orchestration/researchers-introduce-self-harness-a-framework-that-lets-ai-agents-rewrite-their-own-rules-boosting-performance-up-to-60/) · [NOVALOGIQ](https://novalogiq.com/2026/06/22/researchers-introduce-self-harness-a-framework-that-lets-ai-agents-rewrite-their-own-rules-boosting-performance-up-to-60/) · [roboaidigest](https://roboaidigest.com/posts/2026-06-24-self-harness-ai-agents/) · [COMFYCLAW arXiv:2607.01709](https://arxiv.org/pdf/2607.01709) · [Skill-MAS arXiv:2606.18837](https://arxiv.org/pdf/2606.18837) · [Lilian Weng blog](https://lilianweng.github.io/posts/2026-07-04-harness/) · [CSDN July 24](https://aicoding.csdn.net/6a62f28410ee7a33f291f843.html)

Platforms: Web (global), Web (China) 🌐 🇨🇳

---

### 6. [new] OpenHarness (HKUDS): Comprehensive Open Harness with Built-In Agent 🌐

**HKUDS/OpenHarness** launched April 1, 2026 (v0.1.0) but was absent from prior threads. Now at **15.1k stars** / 2.4k forks, MIT license. Implements the core Agent Harness pattern with 10 subsystems and **43+ tools** (file I/O, web search, shell, MCP integration, task management). Built-in personal agent **ohmo** operates across Feishu, Slack, Telegram, and Discord.

Providers: Anthropic-Compatible, OpenAI-Compatible, Claude Subscription, Codex Subscription, GitHub Copilot, Moonshot/Kimi (with `reasoning_content` support), GLM, MiniMax, NVIDIA NIM, Ollama. Key security additions: sensitive-path protection in PermissionChecker, hardened web_fetch URL validation. Dry-run preview: produces ready/warning/blocked verdict with concrete next-step suggestions.

Sources: [GitHub](https://github.com/HKUDS/OpenHarness) · [PyPI](https://pypi.org/project/openharness-ai/) · [knightli.com guide](https://knightli.com/en/2026/04/12/openharness-basic-functions/) · [howaiworks.ai](https://howaiworks.ai/blog/openharness-open-source-agent-infrastructure) · [toolhunter.cc](https://toolhunter.cc/tools/openharness)

Platforms: Web (global) 🌐

---

### 7. [new] Google Antigravity 2.0 / CLI: Gemini CLI Forced EOL 🌐

Google announced **Antigravity 2.0** at I/O 2026 (May 19) and forced **Gemini CLI sunset on June 18, 2026**. The migration eliminated one incumbent harness and introduced a new one — affecting all the downstream skill/plugin ecosystems built on Gemini CLI. Antigravity CLI is built in Go (faster/more responsive than JS-based Gemini CLI), shares the same harness as the Antigravity 2.0 desktop app, and runs multiple agents in parallel with background scheduling. **SKILL.md skills require zero modification** — existing Gemini CLI skills work in Antigravity, Claude Code, OpenCode, Cursor, Codex CLI, and 20+ others without changes.

Five platform components: desktop app, CLI, SDK, Managed Agents API, enterprise deployment. Default model: Gemini 3.5 Flash (4× faster than other frontier models). Enterprise/workspace Gemini CLI users received continued support.

Sources: [I/O 2026 highlights](https://blog.google/innovation-and-ai/technology/developers-tools/google-io-2026-developer-highlights/) · [Antigravity I/O blog](https://antigravity.google/blog/google-io-2026) · [Migration announcement](https://developers.googleblog.com/an-important-update-transitioning-gemini-cli-to-antigravity-cli/) · [Antigravity homepage](https://www.antigravity.google/) · [Migration guide (agensi)](https://www.agensi.io/learn/gemini-cli-to-antigravity-migration-guide) · [amux deadline guide](https://amux.io/guides/gemini-cli-to-antigravity-cli/) · [Google Cloud Medium migration](https://medium.com/google-cloud/migrating-to-antigravity-cli-a841c6964f37) · [Developers Digest](https://www.developersdigest.tech/blog/gemini-cli-to-antigravity-cli-migration-guide-2026) · [nerdleveltech guide](https://nerdleveltech.com/google-antigravity-2-agentic-coding-platform) · [GitHub discussion](https://github.com/google-gemini/gemini-cli/discussions/27274)

Platforms: Web (global) 🌐

---

### 8. [new] Kiro (AWS): Spec-Driven IDE July Updates 🌐

**Kiro** — AWS's agentic IDE launched May 7, 2026 as the official successor to Amazon Q Developer (Q EOL April 30, 2027) — absent from prior threads. July updates make it significant:

- **Jul 20:** User-level global hooks, searchable session history panel, corporate proxy hardening
- **Claude Sonnet 5 + Opus 5** now available in Kiro IDE, CLI, and Web
- **Requirements Analysis (spec-check):** Uses mathematical proofs to check whether software requirements contradict each other or leave gaps *before* agents write code — AWS's explicit answer to "AI slop"
- **Parallel Task Execution:** Independent coding tasks run concurrently, cutting implementation times ~75% for large projects
- **AWS MCP Server:** Agents access CloudWatch, S3, DynamoDB through standard IAM permissions

The spec-before-code philosophy is now implemented by both AWS Kiro (spec-check as a harness layer) and Windsurf/Devin. GeekWire framed this as "targeting AI slop" — requiring formal specs rather than vibe-coded prompts.

Sources: [Kiro changelog](https://kiro.dev/changelog/) · [Kiro IDE changelog](https://kiro.dev/changelog/ide/) · [GeekWire spec-check](https://www.geekwire.com/2026/aws-targets-ai-slop-with-new-spec-check-in-kiro-coding-tool-amid-scrutiny-of-agent-reliability/) · [Pingax launch guide](https://pingax.com/kiro-aws-launch-announcement/) · [Kiro review (aiagentsquare)](https://aiagentsquare.com/agents/kiro) · [AWS Summit NY coverage](https://www.techtimes.com/articles/318546/20260617/aws-summit-new-york-2026-kiro-brings-aerospace-spec-standards-ai-coding.htm) · [Kiro homepage](https://kiro.dev/) · [Releasebot Kiro](https://releasebot.io/updates/kiro) · [chatforest review](https://chatforest.com/reviews/amazon-kiro-aws-agentic-ide-spec-driven-review/)

Platforms: Web (global) 🌐

---

### 9. [new] Claw Code: Claude Code Clean-Room Rewrite After Source Leak 🌐

On March 31, 2026, a missing `.npmignore` shipped a 59.8 MB source map containing 512,000 lines of unobfuscated TypeScript across ~1,900 Claude Code files. Within hours, **Claw Code** — a clean-room Python/Rust rewrite by Sigrid Jin (@instructkr) — reached **50k GitHub stars in 2 hours** and **105k in 24 hours**, likely the fastest-growing repo in GitHub history. Not a copy of the leaked code — reimplements the architectural patterns without Anthropic's proprietary source. A Rust rewrite branch is active.

This created a new competitive dynamic: any developer can now study and re-implement Claude Code's harness architecture. Multiple derivative repos exist. Forks of Claw Code have continued the pattern.

Sources: [claw-code.codes](https://claw-code.codes/) · [claw-code.io](https://claw-code.io/) · [Layer5 source leak](https://layer5.io/blog/engineering/the-claude-code-source-leak-512000-lines-a-missing-npmignore-and-the-fastest-growing-repo-in-github-history/) · [Cybernews fastest repo](https://cybernews.com/tech/claude-code-leak-spawns-fastest-github-repo/) · [Eigent comparison](https://www.eigent.ai/blog/claw-code) · [WaveSpeed explainer](https://wavespeed.ai/blog/posts/what-is-claw-code/) · [Klymentiev blog](https://klymentiev.com/blog/claw-code-claude-source) · [collection-claude-code](https://github.com/chauncygu/collection-claude-code-source-code)

Platforms: Web (global) 🌐

---

### 10. [update] Hermes Agent: Native Desktop App + OpenClaw Competitive Pressure 🌐

**New fact since July 27:** Hermes Agent shipped a **native desktop app** with one-click install, in-app self-updates, drag-and-drop files, inline model picker, and concurrent multi-profile sessions. Stars now at 22k+ (note: the prior thread claimed 221k — this figure may have included all forks/mirrors). The refinement of the self-improving learning loop continues.

Community coverage (YouTube video titled "The new Hermes Agent update officially ended OpenClaw") reflects sentiment, though analysis sites note it is more nuanced — Hermes pulling ahead on usability/learning while OpenClaw leads on infrastructure/enterprise. OpenClaw opened GitHub issue #68496 to add Hermes Agent ACP harness support.

Sources: [The New Stack comparison](https://thenewstack.io/openclaw-hermes-agent-harness/) · [Flowtivity June update](https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/) · [YouTube Hermes update](https://www.youtube.com/watch?v=_LYXbI6JY5M) · [Composio comparison](https://composio.dev/content/openclaw-vs-hermes-agent) · [ACP issue](https://github.com/openclaw/openclaw/issues/68496) · [MindStudio switch case](https://www.mindstudio.ai/blog/hermes-agent-vs-openclaw-comparison-switch) · [firecrawl comparison](https://www.firecrawl.dev/blog/openclaw-vs-hermes) · [Claw4science 3-way](https://claw4science.org/blog/agent-harness-three-way)

Platforms: Web (global) 🌐

---

### 11. [update] DeerFlow (ByteDance): TIAMAT Cloud Memory Backend 🌐

**New fact:** DeerFlow 2.0 (prior thread) added **TIAMAT cloud memory backend** in April 2026 — cross-device, cross-session memory sync — signaling ByteDance's push toward enterprise-scale persistence beyond in-session memory. Also added: BytePlus InfoQuest smart search integration, progressive skill loading. Stars: 77.9k.

Sources: [GitHub deer-flow](https://github.com/bytedance/deer-flow) · [MarkTechPost 2.0 launch](https://www.marktechpost.com/2026/03/09/bytedance-releases-deerflow-2-0-an-open-source-superagent-harness-that-orchestrates-sub-agents-memory-and-sandboxes-to-do-complex-tasks/) · [tosea.ai guide](https://tosea.ai/blog/deerflow-bytedance-open-source-research-agent-guide) · [kiledjian blog](https://kiledjian.com/2026/03/06/deerflow-bytances-opensource-ai-agent.html)

Platforms: Web (global) 🌐

---

### 12. [new] MetaHarness (ruvnet): Harness Factory Scaffold Generator 🌐

**ruvnet/agent-harness-generator** (523 stars) offers a meta-factory that generates branded, npm-publishable harness packages from any GitHub repo or blank slate in under 60 seconds. **Darwin Mode** enables autonomous harness self-improvement via sandboxed testing. 19 vertical templates. Generates Ed25519-signed provenance, SBOM, and an MCP server. Supports Claude Code, Codex, pi.dev, Hermes, OpenClaw, RVM, GitHub Copilot, GitHub Actions. Router technology selects cheapest sufficient model per task.

Source: [GitHub MetaHarness](https://github.com/ruvnet/agent-harness-generator)

Platforms: Web (global) 🌐

---

### 13. [new] JP Perspective: 17-Layer OSS Harness Stack + Maintenance Warning 🇯🇵

🇯🇵 Zenn/aiwatch_jp published a comprehensive survey of the 2026 agent harness OSS ecosystem organizing tools into 17 specialized layers across three tiers (execution, state, governance), with a critical maintenance audit:

> "The era of selecting a single framework winner has ended; the age of composing harness by layer has begun."
> (「単一フレームワークの勝者を選ぶ時代は終わり、harnessをレイヤーで組む時代が始まった」)
> — Zenn/aiwatch_jp ([link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained))

**Maintenance warning:** Among ~100 repos audited, 7 had ownership transfers; 1 was archived despite 11k stars (Bytebot). Notable ownership changes: opencode → anomalyco, MetaGPT → FoundationAgents. Practical advice: "Verify via `gh api` before adopting — star count ≠ active maintenance."

Key star counts from the survey: Browser Use (~97k), Firecrawl (~128k), n8n (~191k), Langflow (~149k), Dify (~144k), anthropics/skills (~146k, YAML standard), opencode (~169k), RAGFlow (~82k), Daytona (~73k), CrewAI (~53k).

Additional JP articles: Qiita articles on harness engineering patterns from Anthropic, Google, OpenAI, and LangChain perspectives; CLAUDE.md framed as "harness spec precursor" (Qiita/nogataka). The "Environment Architect" role concept continues to circulate.

Sources: [Zenn aiwatch_jp 17-layer](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained) · [Qiita kiyotaman Agent=Model+Harness](https://qiita.com/kiyotaman/items/4af2861f550896a58081) · [Zenn LLM harness basics](https://zenn.dev/7shi/articles/20260310-llm-harness) · [Zenn MAF GA Part 1](https://zenn.dev/yy7613/articles/ca60a03f4181e4) · [Zenn MAF GA Part 2](https://zenn.dev/yy7613/articles/0b92803c392341) · [Qiita CLAUDE.md successor](https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8) · [Qiita harness design](https://qiita.com/hoge_kawamuro/items/b810f32a2f5d67ed9037) · [CodeZine agent harness internal](https://codezine.jp/article/detail/23340) · [Zenn confusion disambiguation](https://zenn.dev/watany/articles/d8b692bbca65a3)

---

### 14. [new] 🇨🇳 Chinese Harness Ecosystem: Step Star Agent OS, Avernet, Self-Harness Coverage

🇨🇳 Chinese developer community surfaced several distinct items:

**Step Star (阶跃星辰) Agent OS:** Demonstrated a new agent operating system at the 2026 World AI Conference (July, Shanghai), driven by natural-language intent + task specification:
> "Step Star demonstrates new Agent OS driven by intent+task; users express needs in natural language to complete tasks" (「阶跃星辰展示全新的Agent操作系统，以意图+任务驱动」) — CSDN ([link](https://jszn.csdn.net/6a5ddaef10ee7a33f28f5509.html))

**Avernet V0.1 (Ant Group):** Open-source multi-agent collaboration infrastructure — Python, Apache-2.0 — targeting low efficiency in multi-agent LLM coordination. Distributed agent coordination platform: "agents live, connect, coordinate, execute, and evolve together."

**OpenAI Presence (enterprise platform):** Surfaced via CSDN July 24 digest: enterprise agent platform with modeled execution, safety guardrails, human review, AI evaluation, and diagnostic optimization — positioned for customer service and workflow automation.

**Tencent CodeBuddy NPC:** Autonomous research agent reduced initial token load >90% (from ~20,000 to ~2,000 tokens) through harness-level context compression — published via CSDN July 24 digest.

Sources: [CSDN July 7](https://blog.csdn.net/ld326/article/details/162675414) · [CSDN July 24](https://aicoding.csdn.net/6a62f28410ee7a33f291f843.html) · [Ant Group GitHub](https://github.com/antgroup) · [Ant OSS projects](https://opensource.antgroup.com/en/projects) · [Zhihu MCP guide](https://zhuanlan.zhihu.com/p/2016572626777171185) · [jishuzhan.net framework deep-dive](https://jishuzhan.net/article/2066505783961022465)

---

**Still true** (ongoing threads from prior briefing):
- **harness-engineering-paradigm** — Agent=Model+Harness as dominant 2026 paradigm; 3% vs 47% performance gap claim standing; confirmed by Weng July 4 blog and JP/CN community
- **openclaw-gateway-harness** — OpenClaw at 384k+ stars; June 2026 security patches shipped; ACP support issue open
- **omnigent-meta-harness** — Databricks Omnigent in Beta (July 17 status confirmed); managed on Databricks; GEPA optimization on roadmap
- **zot-go-coding-harness** — Zot (299 stars, Go) still referenced in HN ecosystem surveys
- **omp-omo-pi-derivatives** — oh-my-pi / oh-my-openagent still referenced; no new facts
- **yorishiro-presence-harness** — no new facts; still novel as Presence Harness concept
- **extension-economy-explosion** — 600k+ skills, SkillsMP/LobeHub/GitHub Agent Apps active; MCP SDK at 97M monthly downloads; now updated by MCP spec (see Finding 1)
- **agentskills-open-standard** — SKILL.md confirmed working unchanged across Antigravity, Claude Code, OpenCode, Cursor, Codex, Kiro; 20+ harnesses
- **claude-code-doctor-skill-hygiene** — /doctor hygiene tool active; Opus 5 default with nested subagents depth 3 confirmed in v2.1.219; July release cadence ~3 releases/week; [full changelog](https://releasebot.io/updates/anthropic/claude-code)
- **anthropic-managed-agents-mcp-tunnels** — Managed Agents, self-hosted sandboxes, MCP Tunnels all active; July updates include /fork, /resume, EndConversation tool, OpenTelemetry correlation
- **letta-agent-file-format** — .af format still active; no new facts
- **layered-oss-stack-over-single-framework** — Confirmed by Zenn JP survey (17 layers); now quantified with star counts per layer
- **macos-harness-proving-ground** — macOS themes continue; no major new releases
- **ahe-automated-harness-evolution** — arXiv:2604.25850 still standing; now contextualized by Weng's Self-Harness synthesis
- **mcp-security-nsa-supply-chain** — Updated above (Finding 2) with JADEPUFFER + SingGuard-NSFA
- **harness-internal-external-disambiguation** — Zenn/watany article still active (referenced in supplementary search)
- **environment-architect-new-role** — JP community continues to articulate this role; no new primary sources

---

## Cross-Source Patterns

### Pattern 1: Harness Platform Layer Is Now Standardized Infrastructure
**Signal:** Appears across all regions and source types — HN discussions, MAF GA, VSCode AHP, Kiro spec-check, MCP stateless spec, Zenn 17-layer audit, CSDN July digests.
- MAF GA ships "batteries-included" harness (loop, planning, memory, approvals, telemetry) as stable primitives
- VSCode 1.130 Agent Host Protocol decouples agent lifetime from IDE window — same separation of concerns
- MCP stateless spec eliminates session state from the protocol entirely; state moves up to the harness layer
- JP survey: "composing harness by layer" is the new consensus; no single framework wins
> "The harness controls what the model can touch. Defaulting to less is always safer." — Zenn/yy7613, July 2026

### Pattern 2: Security as a Harness Responsibility (Not a Model Feature)
**Signal:** JADEPUFFER + SingGuard + MCP spec auth hardening + Kiro spec-check
- JADEPUFFER proved that exposed harness endpoints (Langflow) are the real attack surface
- SingGuard-NSFA positions guardrails at the harness execution layer, not the model output layer
- MCP 2026-07-28 spec adds six SEPs for OAuth/OIDC hardening — auth moves into the protocol
- Kiro spec-check catches logical contradictions before agents execute — harness prevents bad specs
Platforms: Web (global), Web (China) 🌐 🇨🇳

### Pattern 3: Self-Improving Harnesses Validated Across Research + Industry
**Signal:** Self-Harness paper (CN), Tsinghua SEED, COMFYCLAW, Lilian Weng synthesis, MetaHarness Darwin Mode, DeerFlow TIAMAT, Omnigent GEPA roadmap
- Research confirms: targeted harness edits (not model updates) yield +33%–+60% benchmark improvement
- Products shipping "Darwin Mode" (MetaHarness), GEPA optimization (Omnigent), TIAMAT memory (DeerFlow) reflect commercial adoption of the same thesis
> "Once harness design becomes an executable search space, a strong coding agent can exploit the same design space human engineers use" — Lilian Weng ([link](https://lilianweng.github.io/posts/2026-07-04-harness/))
Platforms: Web (global), Web (China) 🌐 🇨🇳

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (various) | Towards a harness that can do anything | — | — | "Can we control it, can we measure it" | https://news.ycombinator.com/item?id=48921077 |
| (various) | Ask HN: What Are You Working On? July 2026 | — | many | Claude Code 2:1 test ratio; Superpowers plugin | https://news.ycombinator.com/item?id=48884984 |
| (various) | Ask HN: AI Agent and harness containerization | — | — | Security: what can the agent read | https://news.ycombinator.com/item?id=48899674 |
| patriceckhart | Show HN: Zot – Yet another coding agent harness | 107 | 82 | "Best agent by a country mile" (airbreather) | https://news.ycombinator.com/item?id=48319524 |
| (various) | Show HN: Nyx – offensive testing harness | — | — | Probes agents to find failure modes before users do | https://news.ycombinator.com/item?id=47827802 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The new Hermes Agent update officially ended OpenClaw | — | — | No | https://www.youtube.com/watch?v=_LYXbI6JY5M |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | ModelContextProtocol Blog | https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ | MCP 2026-07-28 RC — stateless spec, extensions framework |
| 🌐 | ModelContextProtocol Blog | https://blog.modelcontextprotocol.io/posts/2026-07-28/ | MCP final specification published July 28 |
| 🌐 | Sysdig | https://www.sysdig.com/blog/jadepuffer-agentic-ransomware-for-automated-database-extortion | JADEPUFFER: first agentic ransomware disclosure |
| 🌐 | TechCrunch | https://techcrunch.com/2026/07/06/the-first-ai-run-ransomware-attack-still-needed-a-human/ | JADEPUFFER nuanced coverage |
| 🌐 | TechTimes | https://www.techtimes.com/articles/320508/20260714/ant-group-open-sources-agent-security-tool-days-after-agentic-ransomware-hit.htm | SingGuard-NSFA open-source release |
| 🌐 | Microsoft DevBlogs | https://devblogs.microsoft.com/agent-framework/the-microsoft-agent-framework-harness-is-now-released/ | MAF Harness GA July 22 |
| 🌐 | VS Code | https://code.visualstudio.com/updates/v1_130 | Agent Host Protocol, worktree isolation |
| 🌐 | GitHub xai-org | https://github.com/xai-org/grok-build | Grok-Build Rust agent harness open-source |
| 🌐 | Lilian Weng | https://lilianweng.github.io/posts/2026-07-04-harness/ | Harness Engineering for Self-Improvement (July 4) |
| 🌐 | arXiv | https://arxiv.org/pdf/2606.09498 | Self-Harness paper (Shanghai AI Lab) |
| 🌐 | VentureBeat | https://venturebeat.com/orchestration/researchers-introduce-self-harness-a-framework-that-lets-ai-agents-rewrite-their-own-rules-boosting-performance-up-to-60/ | Self-Harness +60% coverage |
| 🌐 | GitHub HKUDS | https://github.com/HKUDS/OpenHarness | OpenHarness 15.1k stars, 43 tools, ohmo agent |
| 🌐 | Google Developers | https://developers.googleblog.com/an-important-update-transitioning-gemini-cli-to-antigravity-cli/ | Gemini CLI → Antigravity migration |
| 🌐 | Antigravity | https://antigravity.google/blog/google-io-2026 | Antigravity 2.0 I/O 2026 announcement |
| 🌐 | GeekWire | https://www.geekwire.com/2026/aws-targets-ai-slop-with-new-spec-check-in-kiro-coding-tool-amid-scrutiny-of-agent-reliability/ | Kiro spec-check, anti-slop feature |
| 🌐 | AWS Kiro | https://kiro.dev/changelog/ | Kiro July 2026 changelog |
| 🌐 | Layer5 | https://layer5.io/blog/engineering/the-claude-code-source-leak-512000-lines-a-missing-npmignore-and-the-fastest-growing-repo-in-github-history/ | Claude Code source leak analysis |
| 🌐 | GitHub ruvnet | https://github.com/ruvnet/agent-harness-generator | MetaHarness scaffold generator |
| 🌐 | Releasebot | https://releasebot.io/updates/anthropic/claude-code | Claude Code July 2026 all releases |
| 🌐 | Claude Code Docs | https://code.claude.com/docs/en/whats-new/2026-w28 | Week 28 features |
| 🌐 | The New Stack | https://thenewstack.io/harness-ai-agent-dlc/ | Harness.io AI agent delivery pipelines |
| 🌐 | GitHub RyanAlberts | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ ranked harnesses, MCP server for agent consumption |
| 🌐 | GitHub ai-boost | https://github.com/ai-boost/awesome-harness-engineering | Awesome harness engineering list |
| 🌐 | htek.dev | https://htek.dev/articles/all-agent-harnesses-live-comparison | Live comparison all harnesses |
| 🌐 | explainx.ai | https://explainx.ai/blog/top-10-open-closed-source-agent-harnesses-2026 | Top 10 open vs closed 2026 |
| 🌐 | Totalum | https://www.totalum.app/blog/agent-skills-marketplaces-2026 | Skills marketplace comparison |
| 🌐 | mcpmarket.com | https://mcpmarket.com/ | MCP server discovery |
| 🌐 | agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | 7 skills marketplaces compared |
| 🌐 | agensi.io | https://www.agensi.io/learn/complete-list-ai-agent-skill-directories-2026 | Complete skills directories list |
| 🌐 | WorkOS | https://workos.com/blog/mcp-2026-spec-agent-authentication | MCP auth hardening |
| 🌐 | SecurityWeek | https://www.securityweek.com/new-enterprise-ready-mcp-specification-brings-new-security-challenges/ | MCP spec security implications |
| 🌐 | Databricks | https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents | Omnigent intro |
| 🌐 | HelpNetSecurity | https://www.helpnetsecurity.com/2026/07/06/omnigent-open-source-ai-agent-framework/ | Omnigent July 6 coverage |
| 🌐 | MarkTechPost | https://www.marktechpost.com/2026/07/15/spacexai-open-sources-grok-build-the-rust-agent-harness-tui-and-tool-layer-behind-its-coding-cli/ | Grok-Build open-source coverage |
| 🌐 | Cybernews | https://cybernews.com/tech/claude-code-leak-spawns-fastest-github-repo/ | Claw Code fastest-growing repo |
| 🌐 | arXiv | https://arxiv.org/pdf/2607.01709 | COMFYCLAW self-evolving skill harness |
| 🌐 | arXiv | https://arxiv.org/pdf/2606.18837 | Skill-MAS meta-skill for multi-agent systems |
| 🌐 | OpenCode changelog | https://opencode.ai/changelog | OpenCode July updates, 160k stars |
| 🌐 | Flowtivity | https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/ | OpenClaw vs Hermes June 2026 |
| 🌐 | GitHub openclaw issue | https://github.com/openclaw/openclaw/issues/68496 | OpenClaw adding ACP support |
| 🌐 | firecrawl.dev | https://www.firecrawl.dev/blog/openclaw-vs-hermes | OpenClaw vs Hermes which to run |
| 🌐 | Google Cloud Medium | https://medium.com/google-cloud/dialling-our-agents-to-11-agent-skills-you-need-to-be-using-ccffa51e91df | Agent skills guide June 2026 |
| 🌐 | Infosecurity Magazine | https://www.infosecurity-magazine.com/news/researchers-first-agentic/ | JADEPUFFER industry coverage |
| 🌐 | Outpost24 | https://outpost24.com/blog/jadepuffer-agentic-ransomware/ | JADEPUFFER attack reconstruction |
| 🌐 | Security Magazine | https://www.securitymagazine.com/articles/102408-researchers-discover-first-documented-case-of-agentic-ransomware | Security community coverage |
| 🌐 | OpenSourceForYou | https://www.opensourceforu.com/2026/07/new-open-source-ai-security-guardrails/ | SingGuard-NSFA coverage |
| 🌐 | Skywork | https://skywork.ai/skypage/en/ai-agent-skill-marketplace/2064628039419887616 | Skill marketplace ecosystem 2026 |
| 🌐 | alphaxiv | https://www.alphaxiv.org/overview/2606.09498v1 | Self-Harness paper overview |
| 🌐 | Apptension | https://apptension.com/blog/july-2026-why-ai-coding-teams-bet-on-tool-harnesses | Why teams bet on harnesses July 2026 |
| 🌐 | Developers Digest | https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 | HN meta-analysis |
| 🌐 | claude-world.com | https://claude-world.com/articles/ai-coding-models-tools-july-2026/ | July 2026 state of play |
| 🌐 | bestofshowhn.com | https://bestofshowhn.com/2026/7 | Best HN startups July 2026 |
| 🇯🇵 | Qiita/Ryu-Yanagi | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | Harness engineering complete guide |
| 🇯🇵 | Qiita/kiyotaman | https://qiita.com/kiyotaman/items/4af2861f550896a58081 | Agent=Model+Harness, 6× performance gap |
| 🇯🇵 | Qiita/cvusk | https://qiita.com/cvusk/items/9c3e2738eede36eb206f | Practical harness engineering guide |
| 🇯🇵 | Qiita/nogataka | https://qiita.com/nogataka/items/d1b3fcf355c630cd7fc8 | CLAUDE.md → harness engineering |
| 🇯🇵 | Qiita/hoge_kawamuro | https://qiita.com/hoge_kawamuro/items/b810f32a2f5d67ed9037 | Harness design for resilient dev |
| 🇯🇵 | Zenn/aiwatch_jp | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | 17-layer OSS stack survey + maintenance audit |
| 🇯🇵 | Zenn/7shi | https://zenn.dev/7shi/articles/20260310-llm-harness | LLM harness basics: dual-loop, sandboxing |
| 🇯🇵 | Zenn/yy7613 (Part 1) | https://zenn.dev/yy7613/articles/ca60a03f4181e4 | MAF Harness GA coverage Part 1 |
| 🇯🇵 | Zenn/yy7613 (Part 2) | https://zenn.dev/yy7613/articles/0b92803c392341 | MAF Harness GA coverage Part 2 |
| 🇯🇵 | Zenn/watany | https://zenn.dev/watany/articles/d8b692bbca65a3 | Internal vs External Harness disambiguation |
| 🇨🇳 | CSDN/ld326 | https://blog.csdn.net/ld326/article/details/162675414 | Global AI digest July 7 |
| 🇨🇳 | CSDN/aicoding | https://aicoding.csdn.net/6a62f28410ee7a33f291f843.html | Global AI digest July 24 |
| 🇨🇳 | CSDN/jszn | https://jszn.csdn.net/6a5ddaef10ee7a33f28f5509.html | 2026 World AI Conference coverage |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2016572626777171185 | MCP as universal socket for agents |
| 🇨🇳 | jishuzhan.net | https://jishuzhan.net/article/2066505783961022465 | AI Agent framework deep-dive 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (not searched per exclusion)
├─ 🔵 X: 0 posts (excluded per instructions)
├─ 🔴 YouTube: 1 video referenced │ views unknown
├─ 🟢 HN: 5 threads │ ~300 points (estimated) │ 82+ comments (Zot thread)
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts │ (backend OK; no dedicated posts surfaced)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 55 pages 🌐 │ 🇯🇵 10 │ 🇨🇳 8
└─ 🗣️ Top voices: @lilianweng (harness self-improvement synthesis) │ Zenn/aiwatch_jp (17-layer audit) │ Sysdig threat research (JADEPUFFER) │ xai-org (Grok-Build) │ Shanghai AI Lab (Self-Harness)
```

---

## Out of Scope but Notable

- **Schema Harness Framework (Berkeley, ARC-AGI-3 98.98% RHAE)** — surfaced via CSDN July 24 digest: represents world models as executable, verifiable programs with observation-inference-execution-recording loops. Achievement is model benchmark territory (paradigm-watch), but the "harness-as-formal-specification" approach is notable for harness engineering.

- **OpenAI Presence (enterprise agent platform)** — appeared in CSDN July 24: modeled execution, safety guardrails, human review, AI evaluation, diagnostic optimization for enterprise workflows. Possibly belongs to ai-software-factory topic.

- **Windsurf / Devin Desktop rebrand (Cognition)** — Windsurf rebranded to Devin Desktop (June 2026); Cascade agent EOL July 1. Belongs to ai-software-factory or open-models-geopolitics depending on framing.

- **Harness.io AI Agent Delivery Pipelines** — The DevOps company Harness (not an AI harness) launched AI agent delivery pipelines "that don't care when agent outputs change." Interesting signal that traditional CI/CD tooling is adapting to non-deterministic agent outputs. ([link](https://thenewstack.io/harness-ai-agent-dlc/))

---

## Data Gaps

- **Reddit:** Excluded per instructions (would have captured additional developer discussion threads).
- **X/Twitter:** Excluded per instructions.
- **Direct HN fetch:** Rate-limited (429) on `news.ycombinator.com/item?id=48921077` — context recovered via supplementary search coverage.
- **Bluesky:** Backend reported OK; search returned no dedicated agent harness posts in the July 2026 window. Limited harness-specific discourse on Bluesky compared to HN/X.
- **Polymarket:** No markets found on this topic.
- **TikTok/Instagram:** Not searched (low expected signal for technical harness content).
- **CSDN July 24 content:** Direct URL (HTTP 521) recovered via WebSearch search result summary — some details may be imprecise.
- **GeekWire Kiro article:** HTTP 403 — content recovered via WebSearch summary.
- **TechTimes SingGuard article:** HTTP 403 — content recovered via WebSearch summary.
- **Grok-Build MarkTechPost:** Empty page content — details recovered via GitHub direct fetch + WebSearch.
- **Noise:** Extension marketplace comparisons (8+ competing articles on agensi.io, totalum.app, remoteopenclaw.com) — all cite the same 600k+ Vercel figure; low incremental signal.

**Approximate coverage:** ~82% of an ideal full-source run. Primary gaps: Reddit, X/Twitter, and TikTok not searched; some CSDN content failed direct fetch; Bluesky surfaced nothing. JP/CN passes used free DuckDuckGo HTML endpoint as intended — reached key Qiita/Zenn/CSDN content.

---

## Key Quotes

> "MCP is now stateless at the protocol layer — any server instance can handle any request." — MCP 2026-07-28 specification ([link](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/))

> "The layer between the raw model and the real-world context seems to be as important as the model's raw intelligence." — Lilian Weng, Harness Engineering for Self-Improvement ([link](https://lilianweng.github.io/posts/2026-07-04-harness/))

> "An LLM agent can chain reconnaissance, credential theft, lateral movement, persistence, and destruction without the operator possessing deep expertise in any one step." — Sysdig on JADEPUFFER ([link](https://www.sysdig.com/blog/jadepuffer-agentic-ransomware-for-automated-database-extortion))

> "The era of selecting a single framework winner has ended; the age of composing harness by layer has begun." (「単一フレームワークの勝者を選ぶ時代は終わり、harnessをレイヤーで組む時代が始まった」) — Zenn/aiwatch_jp 17-layer OSS survey ([link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained)) 🇯🇵

> "The harness controls what the model can touch. Defaulting to less is always safer." — Zenn/yy7613, on MAF Harness GA file-access reversal ([link](https://zenn.dev/yy7613/articles/0b92803c392341)) 🇯🇵

> "Once harness design becomes an executable search space, a strong coding agent can exploit the same design space human engineers use." — Lilian Weng ([link](https://lilianweng.github.io/posts/2026-07-04-harness/))

> "Shanghai AI Lab proposes Self-Harness, allowing agents to automatically optimize their outer runtime framework; task performance improved 104%." (「上海人工智能実験室提出Self-Harness，让智能体自动优化自身外层运行框架，任务性能提升104%」) — CSDN community ([link](https://aicoding.csdn.net/6a62f28410ee7a33f291f843.html)) 🇨🇳

> "Star count doesn't guarantee active maintenance — among ~100 repos audited, 7 had ownership transfers; 1 was archived." — Zenn/aiwatch_jp maintenance audit ([link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained)) 🇯🇵

> "SpaceXAI's coding agent harness and TUI. Fullscreen, mouse interactive, extensible." — xai-org/grok-build README ([link](https://github.com/xai-org/grok-build))

> "Harness engineering investments yield faster performance gains than awaiting model updates." (「ハーネスエンジニアリングへの投資は、モデルの改善を待つよりも速いパフォーマンス向上をもたらす」) — Qiita/kiyotaman ([link](https://qiita.com/kiyotaman/items/4af2861f550896a58081)) 🇯🇵
