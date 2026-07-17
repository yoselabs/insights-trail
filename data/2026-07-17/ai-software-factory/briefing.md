# AI Software Factory — Daily Briefing
**Date:** 2026-07-17
**Query type:** GENERAL
**Sources:** Web (global), Web (Japan), Web (China), Hacker News, arXiv, GitHub, Juejin, Zenn, note.com

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Web (global) | 38 pages | — | 🌐 WebSearch + WebFetch; primary source set |
| Web (Japan) | 4 pages | — | 🇯🇵 Zenn, note.com (Wayne Chang, Alive Crane); 2 prior-briefing sources re-confirmed |
| Web (China) | 4 pages | — | 🇨🇳 Juejin, CSDN/GitCode; 2 Zhihu pages 403 |
| Hacker News | ~6 stories | — | 🌐 via referenced HN links and secondary coverage; HN API 429 on direct fetch |
| arXiv | 8 papers | — | 🌐 ShareLock, MCPPrivacyDetector, WebMCP, AI-Infra-Guard, new surveys |
| GitHub | 3 repos | — | 🌐 Bernstein, Microsoft Conductor, AI-Infra-Guard |
| Reddit | 0 | — | reddit.com blocked by user-agent |
| X/Twitter | 0 | — | excluded per instructions |
| YouTube | 0 | — | not queried this run |
| Bluesky | 0 | — | no topic-relevant results found in web search |
| TikTok | 0 | — | ScrapeCreators not configured |
| Instagram | 0 | — | ScrapeCreators not configured |
| Polymarket | 0 | — | no relevant markets |

---

## Synthesized Findings

### 1. [new] AI Engineer World's Fair 2026: "The Runtime Is Where Agent Trust Is Won"

The largest AI engineering conference of the year (6,000 attendees, June 29 – July 2, San Francisco) produced a definitive statement of where the field stands. Docker's post-conference writeup, published July 14, has become the canonical synthesis: **agent trust is not a policy problem or a prompt problem — it lives at the runtime layer**.

The central structural insight from Docker's EVP of Engineering Tushar Jain: "The durable fix lives one layer down, at the runtime... Agents are just the next workload." Docker's framing around Simon Willison's **"lethal trifecta"** — access to private data, exposure to untrusted content, ability to act in the outside world — resonated across the conference because all three properties exist **by design** in any useful agent. No policy, prompt, or model-level filter can resolve the combination; only runtime boundaries can.

Staff PM Rowan Christmas demonstrated this concretely: an agent with **read-only access** was shown piecing together banking activity details within minutes. "An agent doesn't have to be malicious to be dangerous. It just has to be able to see." Docker's response is microVM-based Sandboxes with defined filesystem, network, and tool boundaries.

Principal SE Jim Clark named **"Shadow MCP"** — developers installing servers faster than security can review them — as the enterprise governance gap. The answer is org-managed MCP catalogs with vetting, signing, and default-deny policies rather than per-engineer approval.

The **five consensus themes** from Latent.Space's AIEWF trends synthesis:
1. **Systems over agents** — harness engineering (memory, skills, tools, sandboxing, loops) is now the peer discipline to model selection; Lilian Weng framed her own research evolution as moving from individual agent anatomy to harness engineering
2. **Loop engineering as control** — Roland Gavrilescu (Autoresearch): "The inner loop is the primary system interacting with users...the outer loop studies and maintains the primary system." Humans operate in the outer loop, agents in the inner
3. **Forward Deployed Engineers as enterprise bridge** — Cursor's Pauline Brunet: "When we walk away...it is a strict ROI for them. They're not gonna turn things off." FDEs are now standard at Sierra, Cursor, and growing cohort of AI deployment firms
4. **Coding agents replacing IDEs** — Claude Code, Cursor, Warp now handle codebase exploration, file modification, test execution, and iteration before presenting results; the IDE as primary artifact is deprecated
5. **Skills as portable knowledge** — Philipp Schmid (Hugging Face): "Agents are just files. We write markdown files to extend capabilities." Skills encode workflows, not model weights

The Japanese note.com AIEWF report (wayne_chang) adds: "あなたたちは『プロダクトを作るためのシステム』を構築することになるのです" ("You'll be building the thing that builds the product") — Zach Lloyd (Warp). And: "顧客特有のタスクの大部分は、モデルそのものではなくオーケストレーション層で行われます" ("Most customer-specific work takes place at the orchestration layer rather than in the models themselves") — Natalie Meurer (Sierra).

**Cross-platform coverage:** 🌐 Docker blog, Latent.Space, Develeap, DEV Community, .NET Ramblings; 🇯🇵 note.com (wayne_chang)

Sources: [Docker AIEWF post](https://www.docker.com/blog/ai-engineer-worlds-fair-2026-the-runtime-is-where-agent-trust-is-won/) | [Latent.Space trends](https://www.latent.space/p/aiewf26trends) | [Latent.Space loops dispatch](https://www.latent.space/p/aiewf-daily-dispatch-loops) | [Conference site](https://www.ai.engineer/worldsfair/2026) | [JP note.com report](https://note.com/wayne_chang/n/nc2815f2b07cf) | [Docker Sandboxes](https://docs.docker.com/ai/sandboxes/) | [Docker AI Governance](https://www.docker.com/blog/introducing-docker-ai-governance/)

---

### 2. [new] MCP Attack Surface Expands: ShareLock, Agentjacking, Amazon Q CVEs

Three new attack patterns represent a qualitative escalation from the supply-chain and prompt injection threats documented in the prior briefing — these are **novel attack categories**, not variants of known patterns.

**ShareLock** (arXiv [2606.27027](https://arxiv.org/abs/2606.27027)): A multi-tool threshold poisoning framework using Shamir's secret-sharing scheme to **distribute malicious instructions as benign-looking secret shares across multiple MCP tool descriptions**. No single tool description contains the malicious payload; only when the aggregated shares reconstruct does the instruction execute. The result: 90%+ attack success rate while evading all single-tool detection approaches. A covert reconstruction trigger planted during a server update triggers aggregation. This is the most sophisticated MCP attack published to date.

**Agentjacking via Sentry MCP** (Tenet Security): Attackers inject **fake Sentry error events through a public DSN**. The Sentry MCP server blindly returns these events as "trusted diagnostics" to the coding agent. Result: 85% success rate tricking coding agents into executing arbitrary commands across thousands of vulnerable organizations. The attack is notable because Sentry is a legitimate, widely-trusted developer tool. URL: [tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/](https://tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/)

**Amazon Q MCP Trust Flaw** (Wiz Research, patched June 2026): CVSS 8.5. Amazon Q auto-loaded MCP configs from workspace directories without user consent. Opening a malicious repository triggered instant code execution and AWS credential exfiltration. A second, distinct vulnerability: implicit trust of MCP tool output — agents blindly accepted MCP-returned content as executable instructions. Sources: [wiz.io/blog/amazon-q-vulnerability](https://www.wiz.io/blog/amazon-q-vulnerability) | [wiz.io/blog/amazon-q-developer-mcp-vulnerability](https://www.wiz.io/blog/amazon-q-developer-mcp-vulnerability)

**MCPPrivacyDetector** (arXiv [2606.21338](https://arxiv.org/abs/2606.21338)): Cross-language static and taint analysis across 10,000+ real-world MCP servers found credentials, API keys, and PII leaking at rates **exceeding 10%** — protocol-induced privacy leakage baked into the server implementation patterns, not requiring active attacks.

**WebMCP MSTI** (arXiv [2606.06387](https://arxiv.org/abs/2606.06387)): Mid-Session Tool Injection via AbortSignal hijacking and registration races, allowing attackers to hijack the tools a WebMCP agent uses during an active session.

Adversa AI's July 2026 roundup: [adversa.ai/blog/top-mcp-security-resources-july-2026/](https://adversa.ai/blog/top-mcp-security-resources-july-2026/) | AI-Infra-Guard framework paper: [arxiv.org/abs/2606.31227](https://arxiv.org/abs/2606.31227)

The defensive synthesis from the Docker AIEWF writeup aligns with the attacks: the answer to all three attack patterns is **hard OS-level enforcement at runtime** (microVM sandboxes), not model-level guards or command denylists. Attempting to secure agents via denylist traversal is a confirmed dead end — all three attacks bypass model-level filters entirely.

**Cross-platform coverage:** 🌐 arXiv (4 new papers), Adversa AI, Wiz, Tenet Security, Docker AIEWF

---

### 3. [new] NSA MCP Security CSI: Government-Level Architecture Requirements

The NSA Artificial Intelligence Security Center published "Security Design Considerations for AI-Driven Automation Leveraging the Model Context Protocol" (ID: U/OO/6030316-26, PP-26-1834) in May 2026. Now widely cited. PDFs: [media.defense.gov/2026/Jun/02/.../CSI_MCP_SECURITY.PDF](https://media.defense.gov/2026/Jun/02/2003943289/-1/-1/0/CSI_MCP_SECURITY.PDF)

The document's key finding: **"MCP's rapid proliferation has outpaced the development of its security model. Much like early web protocols, MCP was released with a flexible and underspecified design, allowing implementers freedom of design but also introducing ambiguity for safe usage."**

Specific gaps the NSA identified:
- MCP does not define how a session maps to a verifiable identity
- Authentication is optional rather than required
- Role-based access control is not part of the protocol
- Many production MCP server implementations ship with no authentication controls at all
- Inadequate audit logging throughout

NSA recommendations: treat every MCP session as untrusted until explicitly verified; enforce least-privilege tokens per action and tool; require signed provenance for any dynamically discovered MCP server.

Commentary from Arcade.dev: "The NSA Just Wrote the MCP Requirements Document." ([arcade.dev/blog/nsa-mcp-requirements-document/](https://www.arcade.dev/blog/nsa-mcp-requirements-document/)) — framing the CSI as the de facto technical standard for what enterprise MCP governance must now satisfy. Speakeasy: "The NSA's MCP security baseline: what it means for your gateway." ([speakeasy.com/blog/nsa-mcp-security-baseline](https://www.speakeasy.com/blog/nsa-mcp-security-baseline))

**Cross-platform coverage:** 🌐 NSA press release, Arcade.dev, AI Security Wire, Speakeasy, GetAIGovernance

---

### 4. [new] Deterministic Orchestration Stack Materializes: Microsoft Conductor + Bernstein

Two open-source tools released in 2026 represent the emergence of a **deterministic multi-agent orchestration layer** — treating agent coordination as infrastructure engineering rather than AI inference.

**Microsoft Conductor** ([github.com/microsoft/conductor](https://github.com/microsoft/conductor), MIT license, announced May 14):
YAML-defined multi-agent workflows for the GitHub Copilot SDK and Anthropic Agents SDK. The core design choice: **no LLM in the orchestration loop** — routing uses Jinja2 templates and expression evaluation, so no tokens are spent on coordination decisions. You can mix different models in a single workflow: claude-haiku-4.5 for classification, gpt-5.2 for research, claude-opus-4.6 for complex reasoning, with each agent getting its own isolated session. Features include conditional routing, human-in-the-loop gates, safety limits (max iterations + timeout), real-time web dashboard, and validation that catches stale template references before runtime. [opensource.microsoft.com blog](https://opensource.microsoft.com/blog/2026/05/14/conductor-deterministic-orchestration-for-multi-agent-ai-workflows/)

**Bernstein** ([github.com/sipyourdrink-ltd/bernstein](https://github.com/sipyourdrink-ltd/bernstein), [bernstein.run](https://bernstein.run/)):
"Audit-grade multi-agent orchestration for CLI coding agents." Bernstein decomposes a goal into tasks, spawns 42 supported CLI agents (Claude Code, Codex, OpenAI Agents SDK v2, Gemini, Cursor, Aider, Cloudflare Agents, GitHub Copilot, Droid, Crush, and more) into **isolated git worktrees**, runs tasks in parallel, then validates before merge — The Janitor runs lint, type checks, and tests; only verified work lands. The scheduler is **deterministic Python** with an HMAC-chained audit log and signed agent cards per artifact. Tagline: "The orchestrator your compliance team will sign off on." [bernstein.readthedocs.io](https://bernstein.readthedocs.io/en/latest/)

Both tools share the same architectural principle: **deterministic scheduling decisions should never consume model tokens**. The augmentcode.com survey of 9 open-source agent orchestrators ([augmentcode.com/tools/open-source-agent-orchestrators](https://www.augmentcode.com/tools/open-source-agent-orchestrators)) cites Bernstein as the production implementation of this pattern.

The tooling is now separating into two categories: (1) agent frameworks for intelligent behavior (LangGraph, CrewAI, AG2) and (2) orchestration infrastructure for deterministic coordination (Conductor, Bernstein, Kastor from prior briefing). The second category is the new infrastructure layer.

**Cross-platform coverage:** 🌐 GitHub (both repos), Microsoft Open Source Blog, Augment Code, Firecrawl, AgentConn

---

### 5. [new] McKinsey SDD + Confirmed Dead Ends: "Agents Can't Self-Orchestrate"

McKinsey QuantumBlack's post on **Spec-Driven Development (SDD)** ([medium.com/quantumblack/agentic-workflows-for-software-development-dc8e64f4a79d](https://medium.com/quantumblack/agentic-workflows-for-software-development-dc8e64f4a79d)) is the most rigorous published framework for structured agentic SDLC this period. Its most important contribution: explicit documentation of failure modes from early experiments.

**The confirmed dead end:** "Early experiments letting agents decide workflow sequencing routinely **skipped steps, created circular dependencies, or got stuck in analysis loops** on larger codebases." This is the clearest published statement yet from a major consulting firm that **agent self-orchestration is a dead end** — not a capability gap to close, but an architectural anti-pattern.

The SDD solution:
- **Deterministic orchestration layer** (no LLM in workflow decisions)
- **Bounded agent execution** within defined phases (specs: `.sdlc/context/` and `.sdlc/specs/REQ-001-*/`)
- **Frontmatter state machines** per artifact (draft → in-review → approved → complete)
- **Dual validation gates** per phase: deterministic checks (linters, structural validation) + critic agent (judgment-based, 3-5 attempt cap)
- Human entry point shifts to **post-completion review** of fully formed features, not continuous interruption

Key quote: "The handoff from requirements to design to implementation is where **context goes to die**." The SDD colocates specifications with code in Git, maintaining full traceability from business requirements through architectural decisions to implementation.

The McKinsey piece also names a cultural prerequisite that most teams miss: "If decisions live informally in Slack threads or hallway conversations, agents can't scale your output." Governance infrastructure (decision logs, documented assumptions, structured knowledge base) is a prerequisite for factory patterns to work at scale.

The AWS Summit Japan 2026 note.com report (alive_crane5316) converges on the same dead end from a practitioner angle: early AI coding tools "created rework due to incomplete specifications, unintended code modifications, false completion claims" — confirming that unstructured AI-assisted development produces the same failure modes as self-orchestrating agents. URL: [note.com/alive_crane5316/n/n08d45c8c7e4b](https://note.com/alive_crane5316/n/n08d45c8c7e4b) 🇯🇵

**Cross-platform coverage:** 🌐 McKinsey QuantumBlack (Medium); 🇯🇵 note.com (AWS Summit Japan)

---

### 6. [update] Agentic Security — New Attack Categories + NSA Standard + Microsoft Security Blog

The prior briefing covered the catalogued MCP attack surface. What's **new since July 15:**

- ShareLock (arXiv 2606.27027), Agentjacking via Sentry, Amazon Q CVSS 8.5, MCPPrivacyDetector — all documented in finding #2 above
- **NSA CSI** (May 2026, now widely cited) — documented in finding #3 above
- **Microsoft Security Blog** (June 30, 2026): "Securing AI agents: When AI tools move from reading to acting" ([microsoft.com/en-us/security/blog/2026/06/30/securing-ai-agents-ai-tools-move-from-reading-acting/](https://www.microsoft.com/en-us/security/blog/2026/06/30/securing-ai-agents-ai-tools-move-from-reading-acting/)) — positions the threat model shift as "tools that **act** rather than just **read**"
- **OX Security** "Mother of All AI Supply Chains" analysis: [ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) — CSA Research Note: [labs.cloudsecurityalliance.org/research/csa-research-note-mcp-by-design-rce-ox-security-20260420-csa/](https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-by-design-rce-ox-security-20260420-csa/)
- **Akamai**: new MCP specification security preparation guide [akamai.com/blog/security-research/new-mcp-specification-security-teams-must-prepare](https://www.akamai.com/blog/security-research/new-mcp-specification-security-teams-must-prepare)
- **Entrust Agentic AI Trust Accelerator** (July 14, per aiagentstore.ai): co-development program emphasizing identity, authorization, and cryptographic controls as foundational for regulated-industry agents
- New governance tools (July 11): Codenotary AgentMon 3, Automox MCP Server 2.2, First Recon AI Security Runtime, Attestiv DeepScan — runtime security policies and audit-ready evidence for enterprise workflows

The pattern now clear: **the attack surface is moving from static configuration (supply chain) to runtime manipulation (ShareLock, Agentjacking)**. Defense must follow: static scanning alone is insufficient; runtime enforcement is the only durable layer.

**Cross-platform coverage:** 🌐 arXiv, NSA, Adversa AI, Wiz, Microsoft, OX Security, CSA, Akamai, Entrust

---

### 7. [update] Benchmark Landscape — SWE-bench Pro and the New Agent Eval Suite

**New since July 15:** The benchmark generation question has been answered with concrete new entrants.

**SWE-bench Pro**: Successor to the compromised SWE-bench Verified. Focus: **long-horizon software engineering tasks** — multi-file refactors, cross-module debugging, architectural changes. These are harder to memorize and easier to validate via automated test suites rather than human judgment, making the benchmark contamination-resistant. Expected to dominate the conversation in H2 2026. Source: [benchmarkingagents.com/agent-benchmarks/](https://benchmarkingagents.com/agent-benchmarks/)

**Full 2026 benchmark suite** (Rapid Claw survey — [rapidclaw.dev/blog/ai-agent-benchmarks-2026](https://rapidclaw.dev/blog/ai-agent-benchmarks-2026)):
- APEX-Agents: professional workplace tasks
- TAU2-Bench: tool calling (τ-bench v2, Princeton + Sierra)
- MCP-Atlas: specifically for MCP tool coordination
- Terminal-Bench: computer use / CLI interaction
- OSWorld: GUI automation
- GAIA: general agent reasoning

**Workspace-Bench 1.0** (arXiv [2605.03596](https://arxiv.org/pdf/2605.03596)): AI agents on workspace tasks with large-scale file dependencies — addresses the gap where small-file benchmarks don't capture real codebase navigation failures.

**Key evaluation finding** (Zylos Research — [zylos.ai/research/2026-05-13-ai-agent-evaluation-benchmarking/](https://zylos.ai/research/2026-05-13-ai-agent-evaluation-benchmarking/)): The Agent Development Lifecycle (ADL) codifies a feedback loop — **observability surfaces failure modes, evaluation suites capture them as test cases, policy updates prevent recurrence**. Production traces must become regression tests, not be discarded. This is the architecture that closing the loop between eval and operations requires.

**The dead end on LLM-as-judge**: Calibration drift in LLM-as-judge models remains an open challenge ([kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough](https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough)). Truly dynamic benchmarks that maintain consistent difficulty as frontier capability increases remain an open research area.

**Cross-platform coverage:** 🌐 benchmarkingagents.com, Rapid Claw, Zylos Research, Kili Technology, arXiv

---

### 8. [update] China Enterprise AI Agent Market: 186B Yuan, 70% Multi-Agent Adoption

**New since July 15 — specific market data:**

China's enterprise AI agent market reached **186 billion yuan in 2026 with 58% annual growth rate**; top platforms hold ~75% market share (IDC data via Juejin survey [juejin.cn/post/7654244323158016038](https://juejin.cn/post/7654244323158016038)). 🇨🇳

The six enterprise selection criteria — **开发门槛** (development ease), **数据安全** (data security), **系统集成** (system integration), **幻觉抑制** (hallucination mitigation), **成本可控** (cost control), **落地效率** (deployment efficiency) — are more pragmatic than Western discourse (which focuses on orchestration patterns and observability). **Hallucination mitigation** being named explicitly as a top pain point reflects a practitioner market that has moved past demos into production operations.

**70% of enterprise AI applications will adopt multi-agent architectures by 2026** — CSDN/GitCode multi-agent guide (夜珀 — [gitcode.csdn.net/69e1d48254b52172bc6a830b.html](https://gitcode.csdn.net/69e1d48254b52172bc6a830b.html)). This figure (from Gartner data cited via Chinese source) confirms the Western multi-agent trajectory with enterprise-scale Chinese adoption data. 🇨🇳

Key quote (Chinese original + EN):
> "单个'全能实习生'式的Agent，在面对跨部门协作、长周期任务时，很容易陷入上下文窗口枯竭或规划混乱的窘境"
> ("A single 'omnipotent intern'-style Agent easily becomes trapped in context window exhaustion or planning chaos when facing cross-departmental collaboration or long-term tasks.") — 夜珀 on CSDN/GitCode 🇨🇳

Chinese platform landscape: Tencent YuanQi (WeChat integration, 30,000 yuan/yr), ByteDance Coze (Feishu native), Alibaba Bailian (multimodal, 200k-token context), Ant Agentar (finance-grade, 50-200M yuan private deploy), iFLYTEK AstronClaw (3,200+ skills), Dify (developer-flexible, open source).

**Cross-platform coverage:** 🇨🇳 Juejin, CSDN/GitCode (full content fetched); 🌐 IDC via Chinese reports

---

### 9. [update] AIEWF + Industry Confirmation: "Pilot Paralysis" Named and Data-Backed

The prior briefing cited Gartner's 40% cancellation prediction. New data since July 15 adds a starker picture of the current state:

- **80% of AI projects fail** — roughly 2× the failure rate of conventional IT projects ([pertamapartners.com](https://www.pertamapartners.com/insights/ai-project-failure-statistics-2026))
- **95% of GenAI pilots deliver no measurable return on the P&L** — MIT 2025 study, widely cited in July 2026
- **42% of companies abandoned most AI initiatives in 2025**, up from 17% the year prior

The named phenomenon: **"Pilot Paralysis"** — AI proofs-of-concept that never graduate to production. The consensus root cause from multiple sources: "AI failure is organizational, not technical. The fix is governance and scope discipline, not more model spend." ([digitalapplied.com](https://www.digitalapplied.com/blog/agentic-ai-project-cancellations-gartner-40-percent-2026))

The McKinsey SDD framework (finding #5) is a direct response to this failure mode — structured governance (state machines, deterministic gates, explicit handoffs) is what converts pilot-stage agentic experiments into production-grade factories.

The daily AI Agent News for July 16 notes PwC + OpenAI launching packaged agentic solutions that abstract factory governance — suggesting enterprise demand for pre-built governance infrastructure rather than DIY approaches.

**Cross-platform coverage:** 🌐 Pertama Partners, DigitalApplied, CIO, aiagentstore.ai

---

**Still true (from prior briefing — no new facts, not re-explained):**

- **[prior #1] GitLost**: "Additionally" keyword bypasses GitHub Agentic Workflows; "the agent's context window is also its attack surface"; no mitigation from GitHub as of prior briefing
- **[prior #2] CRISPY/HumanLayer**: RPI superseded by 7-stage CRISPY; Ralph loops for context resets; 2-3x productivity claims at Block/Uber
- **[prior #3] Microsoft Flint**: Visualization language for agent workflows (HN 348pts); Kastor: Terraform-style HCL for agents
- **[prior #4] Ploy.ai migration**: 2.2x faster, 27% cheaper, 1/3 failures from harness assumptions
- **[prior #5] Observability/eval split**: Gartner 40% cancellation; 15% instrument observability; Oodle.ai $10/M traces; Mirrors production trace replay; Boundev/Prefactor on observability ≠ evals
- **[prior #6] AI SRE + FDE patterns**: "Most dangerous employee" framing; forward deployed engineers entering enterprise
- **[prior #7] SDLC methodology papers**: arXiv 2606.20615 protocol language, 2605.14675 adoption barriers, Sogeti whitepaper, PwC 70% GenAI usage survey, Polity Network "The Factory Returns"
- **[prior #8] MCP security baseline**: CSA 200,000 instances; 30%+ server vulnerability rate; obot.ai "supply chain problem first" framing; Unreal Engine 5.8 MCP support
- **[prior #9] Practitioner reality check**: Intern turning into "prompt writer"; Amy Ko 3-month experiment; cognitive fatigue; Nodus 19-agent/5-lane community project

---

## Cross-Source Patterns

**Pattern 1: "The durable fix lives one layer down" — runtime enforcement is the convergent security architecture** 🌐
- Docker AIEWF: microVM sandbox boundaries as the only fix for the lethal trifecta
- NSA CSI: MCP sessions untrusted until runtime-verified with per-action least-privilege
- McKinsey SDD: deterministic orchestration layer prevents agent self-orchestration dead end
- Bernstein/Conductor: no LLM tokens in coordination path, hard Python/YAML control
- Platforms: AIEWF (Docker, Latent.Space), NSA, McKinsey, GitHub

**Pattern 2: "You'll be building the thing that builds the product" — the meta-engineer shift is the unanimous conference signal** 🌐🇯🇵
- AIEWF: Zach Lloyd (Warp), Tereza Tížková on factory lifecycle, Natalie Meurer on orchestration layer
- AWS Summit Japan: "code generation is merely the entry point"; role → managing AI agents
- AIEWF JP (wayne_chang): orchestration layer = competitive moat, not model
- McKinsey: human entry point shifts to post-completion review
- Platforms: AIEWF multiple speakers, note.com Japan, McKinsey

**Pattern 3: ShareLock signals a new attack generation — from static to runtime manipulation** 🌐
- ShareLock (threshold distribution): bypasses all single-tool detection
- Agentjacking (trusted-tool injection): exploits legitimate tools (Sentry) as attack vectors
- Amazon Q (auto-execution): workspace context as attack surface
- All three bypass model-level guards entirely
- NSA/Docker: only hard runtime enforcement addresses this generation of attacks
- Platforms: arXiv, Adversa AI, Wiz, Tenet Security, Docker AIEWF

**Pattern 4: Deterministic orchestration layer emerging as standard infrastructure pattern** 🌐
- Microsoft Conductor: YAML-defined, no LLM coordination, MIT license
- Bernstein: Python scheduler, HMAC audit chain, 42 CLI adapters
- McKinsey SDD: deterministic orchestration + bounded agent execution two-layer model
- Kastor (prior briefing): Terraform-style HCL for agents
- Platforms: GitHub, Microsoft Open Source Blog, Augment Code, McKinsey

**Pattern 5: 🇯🇵🇨🇳 Parallel convergence on "orchestration > model" and "specialist roles"**
- 🇯🇵 AWS Summit Japan (note.com): "competitive advantage = process design as Agent-Native, not model selection"
- 🇯🇵 AIEWF JP (note.com): "customer-specific work at orchestration layer, not models themselves"
- 🇨🇳 Juejin: top enterprise selection criteria = hallucination mitigation + cost control (pragmatic layer above model selection)
- 🇨🇳 CSDN/GitCode: "単个全能实习生" anti-pattern; multi-agent = solving with specialized minds
- Both: role bifurcation toward "meta-engineer" / "factory manager" vs. line-coder

---

## Per-Platform Tables

**Web (Global):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Docker Blog | https://www.docker.com/blog/ai-engineer-worlds-fair-2026-the-runtime-is-where-agent-trust-is-won/ | AIEWF 2026: runtime = agent trust; lethal trifecta; shadow MCP; microVM sandboxes |
| 🌐 | Latent.Space (loops) | https://www.latent.space/p/aiewf-daily-dispatch-loops | AIEWF: loopcraft, factory lifecycle, FDEs, Zach Lloyd "building the builder" |
| 🌐 | Latent.Space (trends) | https://www.latent.space/p/aiewf26trends | AIEWF 5 trends: systems > agents; loop engineering; FDEs; skills-as-files |
| 🌐 | Adversa AI (MCP) | https://adversa.ai/blog/top-mcp-security-resources-july-2026/ | July 2026 MCP CVE roundup: Amazon Q, MCPPrivacyDetector, MSTI, ShareLock, Agentjacking |
| 🌐 | NSA Press Release | https://www.nsa.gov/Press-Room/Press-Releases-Statements/Press-Release-View/Article/4496698/nsa-releases-security-design-considerations-for-ai-driven-automation-leveraging/ | NSA MCP Security CSI release |
| 🌐 | NSA CSI PDF | https://media.defense.gov/2026/Jun/02/2003943289/-1/-1/0/CSI_MCP_SECURITY.PDF | "MCP's rapid proliferation has outpaced security model"; mandatory controls |
| 🌐 | Arcade.dev | https://www.arcade.dev/blog/nsa-mcp-requirements-document/ | "The NSA Just Wrote the MCP Requirements Document" |
| 🌐 | arXiv ShareLock | https://arxiv.org/abs/2606.27027 | Shamir threshold MCP poisoning; 90%+ ASR; evades single-tool detection |
| 🌐 | arXiv MCPPrivacyDetector | https://arxiv.org/abs/2606.21338 | 10%+ credential/PII leak rate across 10,000+ MCP servers |
| 🌐 | arXiv WebMCP MSTI | https://arxiv.org/abs/2606.06387 | Mid-Session Tool Injection via AbortSignal hijacking |
| 🌐 | arXiv AI-Infra-Guard | https://arxiv.org/abs/2606.31227 | AI infrastructure guard framework |
| 🌐 | Tenet Security (Agentjacking) | https://tenetsecurity.ai/blog/agentjacking-coding-agents-with-fake-sentry-errors/ | Sentry DSN injection → 85% ASR coding agent RCE |
| 🌐 | Wiz (Amazon Q) | https://www.wiz.io/blog/amazon-q-vulnerability | Amazon Q auto-exec MCP CVSS 8.5 |
| 🌐 | Wiz (Amazon Q MCP Trust) | https://www.wiz.io/blog/amazon-q-developer-mcp-vulnerability | Amazon Q implicit MCP output trust flaw |
| 🌐 | Microsoft Security Blog | https://www.microsoft.com/en-us/security/blog/2026/06/30/securing-ai-agents-ai-tools-move-from-reading-acting/ | "AI tools move from reading to acting" threat model shift |
| 🌐 | OX Security | https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/ | "Mother of all AI supply chains" MCP systemic analysis |
| 🌐 | CSA Research (RCE) | https://labs.cloudsecurityalliance.org/research/csa-research-note-mcp-by-design-rce-ox-security-20260420-csa/ | MCP by Design: RCE |
| 🌐 | Akamai | https://www.akamai.com/blog/security-research/new-mcp-specification-security-teams-must-prepare | New MCP specification security preparation |
| 🌐 | McKinsey QuantumBlack | https://medium.com/quantumblack/agentic-workflows-for-software-development-dc8e64f4a79d | SDD framework; dead end: agent self-orchestration; "context goes to die" at handoffs |
| 🌐 | GitHub/microsoft/conductor | https://github.com/microsoft/conductor | YAML-defined multi-agent orchestration, no LLM in loop |
| 🌐 | MS Open Source Blog | https://opensource.microsoft.com/blog/2026/05/14/conductor-deterministic-orchestration-for-multi-agent-ai-workflows/ | Conductor announcement |
| 🌐 | GitHub/bernstein | https://github.com/sipyourdrink-ltd/bernstein | 42 CLI adapters, HMAC audit chain, compliance-grade |
| 🌐 | Bernstein site | https://bernstein.run/ | Bernstein landing page |
| 🌐 | Augment Code (orchestrators) | https://www.augmentcode.com/tools/open-source-agent-orchestrators | 9 open-source agent orchestrators comparison |
| 🌐 | benchmarkingagents.com | https://benchmarkingagents.com/agent-benchmarks/ | SWE-bench Pro, MCP-Atlas, TAU2-Bench, Terminal-Bench survey |
| 🌐 | Rapid Claw | https://rapidclaw.dev/blog/ai-agent-benchmarks-2026 | All 5 benchmark suites ranked |
| 🌐 | Zylos Research | https://zylos.ai/research/2026-05-13-ai-agent-evaluation-benchmarking/ | ADL: observability → eval → policy feedback loop |
| 🌐 | Kili Technology | https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough | LLM-as-judge calibration drift; dynamic benchmark gap |
| 🌐 | Pertama Partners | https://www.pertamapartners.com/insights/ai-project-failure-statistics-2026 | 80% AI project failure rate; 42% companies abandoned most AI initiatives |
| 🌐 | DigitalApplied | https://www.digitalapplied.com/blog/agentic-ai-project-cancellations-gartner-40-percent-2026 | "AI failure is organizational not technical; fix is governance" |
| 🌐 | aiagentstore.ai | https://aiagentstore.ai/ai-agent-news/this-week | PwC+OpenAI, Oracle, Entrust, governance tools week of July 16 |
| 🌐 | Arthur.ai | https://www.arthur.ai/column/agentic-ai-observability-playbook-2026 | 2026 observability playbook |
| 🌐 | AI Engineer WF site | https://www.ai.engineer/worldsfair/2026 | Conference site |
| 🌐 | Speakeasy | https://www.speakeasy.com/blog/nsa-mcp-security-baseline | NSA MCP security baseline analysis |
| 🌐 | ASDLC.io | https://asdlc.io/concepts/agentic-sdlc/ | Agentic SDLC reference framework |
| 🌐 | arXiv 2606.12986 | https://arxiv.org/pdf/2606.12986 | Rise of AI-Native Software Engineering (48 papers) |
| 🌐 | arXiv 2606.03394 | https://arxiv.org/html/2606.03394v1 | Human-AI Collaboration and SE Work Transformation |

**Web (Japan):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇯🇵 | note.com (alive_crane) | https://note.com/alive_crane5316/n/n08d45c8c7e4b | AWS Summit Japan 2026: "code generation is entry point only"; Agent-Native process redesign |
| 🇯🇵 | note.com (wayne_chang) | https://note.com/wayne_chang/n/nc2815f2b07cf | AIEWF 2026 JP report: orchestration layer > models; meta-engineer shift; open-source sovereignty |
| 🇯🇵 | Zenn/ryok | https://zenn.dev/ryok/articles/sdlc-dead-agentic-engineering-workflow | [from prior briefing] Dark Factory model; CoDD; 8 parallel agents |
| 🇯🇵 | Qiita/ryu-ki | https://qiita.com/ryu-ki/items/a70ec13e4b622a37cd6f | [from prior briefing] AWS AI-DLC Sprint→Bolt |

**Web (China):**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🇨🇳 | Juejin | https://juejin.cn/post/7654244323158016038 | Enterprise platform landscape; 186B yuan market; 58% growth; 6 selection criteria |
| 🇨🇳 | CSDN/GitCode | https://gitcode.csdn.net/69e1d48254b52172bc6a830b.html | Multi-agent guide; "omnipotent intern" anti-pattern; 70% enterprise multi-agent adoption |
| 🇨🇳 | Zhihu | https://zhuanlan.zhihu.com/p/2009989548017460811 | [from prior briefing] "智能体落地元年"; McKinsey 88%/62% data |
| 🇨🇳 | CSDN | https://devpress.csdn.net/v1/article/detail/160177165 | [from prior briefing] AI-Native SDLC reconstruction; SDD as dominant paradigm |

---

## Stats Block

```
├─ 🌐 Web (global): 38 pages (primary research source this run)
├─ 🇯🇵 Web (Japan): 4 pages │ 2 new fetches (note.com AWS Summit, AIEWF report)
├─ 🇨🇳 Web (China): 4 pages │ 2 new fetches (Juejin, CSDN/GitCode)
├─ 📄 arXiv: 8 papers (ShareLock 2606.27027, MCPPrivacy 2606.21338, MSTI 2606.06387, AI-Infra 2606.31227, and 4 prior)
├─ 🐙 GitHub: 3 repos (Bernstein, microsoft/conductor, ai-boost/awesome-harness-engineering)
├─ 🟡 HN: ~6 stories referenced (rate-limited; sourced via secondary coverage)
├─ 🟠 Reddit: 0 (user-agent blocked)
├─ 🔵 X: 0 (excluded per instructions)
├─ 🦋 Bluesky: 0 relevant results
└─ 🗣️ Top voices: Tushar Jain (Docker), Zach Lloyd (Warp), Natalie Meurer (Sierra), Roland Gavrilescu (Autoresearch), Philipp Schmid (HuggingFace) │ 夜珀 (CSDN multi-agent guide), Alive Crane (note.com AWS Summit)
```

---

## Out of Scope but Notable

- **WAIC 2026 / Gemini 3.5 Pro / China AI Conference (July 17):** Shanghai's World Artificial Intelligence Conference opened with Xi Jinping attending in person, and Gemini 3.5 Pro is expected to launch today (2-million-token context, Deep Think, ~$1.25/$10 per M tokens). Not SDLC methodology, but the geopolitical-AI signal of the day — China officially positioning itself at the frontier and in partnership with Google. URL: [buildfastwithai.com/blogs/ai-news-today-july-16-2026](https://www.buildfastwithai.com/blogs/ai-news-today-july-16-2026)

- **OpenAI physical coding keypad** (July 16 news): OpenAI launched a physical device for coding workflow integration — signals that the AI coding interface is moving beyond software UI into dedicated hardware. No deep SDLC methodology implications yet but watches the same trend of "coding agent as first-class workload." Source: [buildfastwithai.com](https://www.buildfastwithai.com/blogs/ai-news-today-july-16-2026)

- **PrismML Bonsai 27B** (July 14): A 27B-param model compressed to 3.9GB runs on iPhone 17 Pro with 90%+ full-precision performance, Apache 2.0. Not SDLC methodology but enables local agent deployment at the edge — relevant to the sovereignty/local-deployment theme raised at AIEWF.

---

## Data Gaps

**Sources unavailable or limited:**
- **Reddit:** user-agent blocked (HTTP 400) — no community discussion this run; prior briefing had 7 threads via direct fetch
- **X/Twitter:** excluded per run instructions — notable practitioner discussion will be missed
- **Hacker News direct:** HN front-page fetch returned HTTP 429 (rate-limited); HN data sourced via secondary coverage and referenced story links in search results
- **Zhihu (2 articles):** HTTP 403 — two new Zhihu articles (Coding Agent panoramic evaluation 2026, industrial agent evolution) unreadable; content estimated from search snippets
- **Mizuho DX Agent Factory article:** HTTP 403 — Mizuho's article on their "Agent Factory" mass-production approach for AI agents was inaccessible
- **Reinforz.co.jp:** Connection refused — agentic SDLC quality revolution article missed
- **YouTube, TikTok, Instagram, Bluesky:** 0 results this run

**SOURCE HEALTH:** No DOWN backends reported in the run prompt; Bluesky confirmed OK. No Bluesky topic-relevant results found despite active search.

**last30days skill:** Not registered in this environment; research conducted manually via WebSearch + WebFetch. This means the HN, Reddit, X, YouTube, Bluesky, and Polymarket platform-specific pulls were not executed by the skill's dedicated scrapers. Coverage for these platforms is estimated at 30-40% of what a full skill run would provide.

**Coverage estimate:** ~68% — strong on global web content (new security papers, AIEWF, McKinsey, benchmarks), strong on JP/CN hub synthesis, weak on community discussion depth (Reddit 0, HN partial, X 0, no video content). The three new security attack patterns (ShareLock, Agentjacking, Amazon Q) and the AIEWF consensus have fuller coverage than practitioner community reaction to them.

---

## Key Quotes

> "The durable fix lives one layer down, at the runtime... Agents are just the next workload." — Tushar Jain (Docker EVP Engineering) at AI Engineer World's Fair 2026 ([link](https://www.docker.com/blog/ai-engineer-worlds-fair-2026-the-runtime-is-where-agent-trust-is-won/))

> "An agent doesn't have to be malicious to be dangerous. It just has to be able to see." — Rowan Christmas (Docker Staff PM) at AIEWF 2026 ([link](https://www.docker.com/blog/ai-engineer-worlds-fair-2026-the-runtime-is-where-agent-trust-is-won/))

> "あなたたちは『プロダクトを作るためのシステム』を構築することになるのです" ("You'll be building the thing that builds the product.") — Zach Lloyd (Warp) at AIEWF, via note.com JP report ([link](https://note.com/wayne_chang/n/nc2815f2b07cf)) 🇯🇵

> "顧客特有のタスクの大部分は、モデルそのものではなくオーケストレーション層で行われます" ("Most customer-specific work takes place at the orchestration layer rather than in the models themselves.") — Natalie Meurer (Sierra) at AIEWF, via note.com JP report ([link](https://note.com/wayne_chang/n/nc2815f2b07cf)) 🇯🇵

> "Early experiments letting agents decide workflow sequencing routinely skipped steps, created circular dependencies, or got stuck in analysis loops." — McKinsey QuantumBlack, on confirmed agent self-orchestration dead end ([link](https://medium.com/quantumblack/agentic-workflows-for-software-development-dc8e64f4a79d))

> "The handoff from requirements to design to implementation is where context goes to die." — McKinsey QuantumBlack, on SDD rationale ([link](https://medium.com/quantumblack/agentic-workflows-for-software-development-dc8e64f4a79d))

> "MCP's rapid proliferation has outpaced the development of its security model. Much like early web protocols, MCP was released with a flexible and underspecified design." — NSA Cybersecurity Information Sheet U/OO/6030316-26 ([link](https://media.defense.gov/2026/Jun/02/2003943289/-1/-1/0/CSI_MCP_SECURITY.PDF))

> "单个'全能实习生'式的Agent，在面对跨部门协作、长周期任务时，很容易陷入上下文窗口枯竭或规划混乱的窘境" ("A single 'omnipotent intern'-style Agent easily becomes trapped in context window exhaustion or planning chaos when facing cross-departmental collaboration or long-term tasks.") — 夜珀, CSDN/GitCode multi-agent guide ([link](https://gitcode.csdn.net/69e1d48254b52172bc6a830b.html)) 🇨🇳

> "『AIを使うこと』自体を目的化するフェーズは終わりました。" ("The phase of treating 'using AI' as an end goal itself has concluded.") — AWS Summit Japan 2026, via note.com ([link](https://note.com/alive_crane5316/n/n08d45c8c7e4b)) 🇯🇵

> "Agents are just files. We write markdown files to extend capabilities." — Philipp Schmid (Hugging Face) at AIEWF 2026, via Latent.Space ([link](https://www.latent.space/p/aiewf26trends))
