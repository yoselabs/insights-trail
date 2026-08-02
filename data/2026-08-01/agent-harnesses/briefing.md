# Agent Harnesses & Extension Economy — Daily Briefing
**Date:** 2026-08-01
**Query type:** GENERAL
**Sources:** Hacker News, YouTube, Bluesky, Web (global), Web (Japan), Web (China), GitHub Trending

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 14 threads | ~940 points, ~430 comments | Several Show HN / Launch HN for new harnesses |
| YouTube | 10 videos | — | Tutorial + summit content; transcript not extracted |
| Bluesky | 8 posts | — | 🦋 MCP-focused posts; MCP Sky dedicated feed |
| Web (global) | 82 pages | — | 🌐 via WebSearch + WebFetch |
| Web (Japan) | 13 pages | — | 🇯🇵 Qiita (4), Zenn (4), note (1), Hatena (3), Speakerdeck (1) |
| Web (China) | 12 pages | — | 🇨🇳 CSDN (4), Zhihu (3), Jishuzhan (1), other CN tech blogs (4) |

*Reddit, TikTok, Instagram: not accessed (Reddit engagement stats unavailable without direct API access; TikTok/Instagram lack indexable web content for this topic).*

---

## Synthesized Findings

### 1. [update] MCP 2026-07-28 Final Spec: Now 500M Monthly Downloads, Zero-Touch OAuth, Chrome DevTools Integration

**New facts since July 31:** SDK download milestone upgraded — the four Tier 1 SDKs (TypeScript, Python, Go, C#) now collectively see **~500 million monthly downloads** (up from 400M); TypeScript and Python SDKs have each individually exceeded **1 billion total downloads**. Additionally, three new enterprise MCP integrations landed on or near August 1: Chrome DevTools MCP (Google, public preview), Azure MCP Server 2.0 (stable), and Salesforce Hosted MCP (GA); these build on the July 28 stateless core.

The 2026-07-28 specification transforms MCP from stateful bidirectional protocol into stateless request/response — removing the `initialize`/`initialized` handshake, `Mcp-Session-Id` header, and protocol-level session management. Each request is now self-describing via `_meta`, enabling round-robin load balancing without shared storage. The community response on HN (127 points, 40 comments) was largely positive: punkpeye (gateway maintainer) noted ~30% of 62,726 indexed open-source servers are actively maintained; firasd observed "tool calls are stateless anyway; results go back into the context window."

**Enterprise Managed Authorization (EMA) / Zero-Touch OAuth** (278 HN points, 103 comments) is a companion extension: IT admins provision MCP server access centrally via Okta/SSO; employees auto-connect without individual OAuth flows. The ID-JAG token format is MCP-agnostic. sean_lynch noted "isolating the auth flow outside of the agent's context window, and potentially out of the harness completely" as the key security advantage.

Simon Willison (July 31) wrote that stateless MCP "recaptured his interest" and released two tools: **mcp-explorer** (Python CLI for querying MCP servers) and **datasette-mcp** (exposing read-only SQL execution over Datasette instances). He frames stateless MCP as "a better fit for building scalable web applications."

Claude.com and AWS AgentCore Gateway have both committed to supporting the 2026-07-28 spec.

🌐 Sources: https://blog.modelcontextprotocol.io/posts/2026-07-28/ · https://news.ycombinator.com/item?id=48592163 · https://news.ycombinator.com/item?id=49088058 · https://simonwillison.net/2026/Jul/31/stateless-mcp/ · https://claude.com/blog/bringing-mcp-2026-07-28-to-claude · https://aws.amazon.com/blogs/machine-learning/how-agentcore-gateway-supports-the-mcp-2026-07-28-spec/ · https://developer.chrome.com/blog/chrome-devtools-mcp · https://github.com/ChromeDevTools/chrome-devtools-mcp · https://devblogs.microsoft.com/azure-sdk/announcing-azure-mcp-server-2-0-stable-release/ · https://venturebeat.com/infrastructure/mcp-just-got-its-biggest-update-ever-heres-what-changes-for-ai-agents · https://trilogyai.substack.com/p/mcp-grows-up-what-the-july-28-spec · https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/ · https://www.bovo-digital.tech/en/blog/mcp-2026-specification-stateless-enterprise-agents · https://nerdleveltech.com/mcp-stateless-protocol-enterprise-authorization · https://developer.mamezao-tech.com/en/blogs/2026/07/10/mcp-spec-2026-07-28-rc/

---

### 2. [update] Warp Oz: Multi-Harness Control Plane Now Fully Live

**New fact since July 31:** The `oz` CLI now accepts `--harness claude` and `--harness codex` flags, and third-party agent harnesses can report non-PR work products back to Warp. Warp has also confirmed K8s pod deployment and per-team billing controls are in production.

Warp Oz is now a live multi-harness control plane orchestrating Claude Code, Codex, and Warp Agent simultaneously. It provides: multi-agent parallel coordination for codebase-wide tasks; **Agent Memory** (research preview) — cross-harness context persistence across sessions/repos/projects; granular per-agent permissions scoped to task requirements; per-team billing and individual credit caps. SD Times: "Enterprises can compare harness effectiveness and use different harnesses for different tasks while maintaining consistent governance."

🌐 Sources: https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration · https://sdtimes.com/ai/warp-updates-oz-to-help-enterprises-orchestrate-coding-agents-across-any-model-or-harness/ · https://itsfoss.com/news/warp-oz-multi-harness-update/ · https://docs.warp.dev/changelog/2026/ · https://docs.warp.dev/agent-platform/cloud-agents/harnesses/warp-agent/

---

### 3. [update] Claude Code Week 29: Artifacts Call Your MCP Connectors + /fork Background Sessions

**New facts since July 31:** Week 29 (July 13-17, v2.1.207–v2.1.212) shipped: (1) **Artifacts call MCP connectors** — a published artifact can pull live data and take actions through each viewer's own MCP connectors when they open the page; (2) **/fork** copies your conversation into a new background session while you keep working; (3) **screen reader mode** replaces visual terminal with plain linear text for VoiceOver/NVDA; (4) Auto mode now works without opt-in variable on Amazon Bedrock, Google Cloud Agent Platform, and Microsoft Foundry.

Sonnet 5 is the default model for Pro/Team Standard/Enterprise (since Week 27, June 29-July 3): native 1M-token context, adaptive thinking on by default, $2/$10 per MTok promotional pricing through August 31. Desktop in-app browser landed in Week 28 (July 6-10) alongside /doctor (full setup checkup with diagnosis+fixes).

🌐 Sources: https://code.claude.com/docs/en/whats-new · https://claudelog.com/claude-code-changelog/ · https://claudefa.st/blog/guide/changelog · https://github.com/anthropics/claude-code/releases · https://go9x.com/blog/claude-updates

---

### 4. [update] OpenClaw July 30/28: Extended-Stable Channel + MCP Apps Ticketing

**New facts since July 31:** July 30 introduced Extended-Stable releases (2026.6.33 as first) with backported security/reliability fixes plus a feature Maturity Scorecard. The July 28 beta (v2026.7.2-beta.5) shipped **MCP Apps** — ticketed MCP connections with bound tools/resources/bounded context, manifest-declared for native plugin support, and scoped to requesting sessions only. Session **rewind and branching** across web and native apps also landed, along with durable channel delivery fixes for Telegram, Signal, Slack, QQBot, Twitch, and Discord voice.

OpenClaw is at 384k+ stars and adds a multi-model routing layer for 40-60% cost reduction on most teams.

🌐 Sources: https://releasebot.io/updates/openclaw · https://openclawlaunch.com/news · https://thenewstack.io/openclaw-hermes-agent-harness/ · https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/ · https://composio.dev/content/openclaw-vs-hermes-agent

---

### 5. [update] Kiro CLI 2.16.0: Tangent Side-Conversations + Per-Tool Token Breakdown

**New fact (July 31):** Kiro CLI 2.16.0 introduces **Tangents** — branching side-conversations that inherit full history and return to the exact starting point when done — plus **/context** which now shows per-tool token consumption. These are V3 mode features.

Preceding July updates: CLI 2.15.0 (July 27) — `/spec new` guided description step + plan auto-execution after approval; IDE 1.0.242 (July 28) — editor context menu with "Ask Kiro to Fix" quick fix + guided hook creation form + Code OSS upgraded to v1.108.2. Claude Opus 5 (July 24) added with 1M context, 2.2x credit multiplier; GPT-5.6 Sol/Terra/Luna (July 14) with 272K context. A security flaw was disclosed where a poisoned web page could rewrite Kiro config and run code — patched.

🌐 Sources: https://kiro.dev/changelog/ · https://releasebot.io/updates/kiro · https://thehackernews.com/2026/07/aws-kiro-flaw-let-poisoned-web-page.html · https://aiagentsquare.com/agents/kiro · https://builder.aws.com/content/3DlOO7A9RFAazBbwbNl2iV8WHr9/harness-engineering-with-kiro-spec-driven-development-for-the-multi-agent-era

---

### 6. [update] Extension Economy: MCP SDK at 500M Monthly, Chrome DevTools, Azure 2.0, Salesforce

**New facts since July 31:** MCP SDK hits 500M monthly (from 400M); TypeScript+Python each >1B total. Three new enterprise MCP servers this cycle: Chrome DevTools MCP (AI agents debug Chrome pages), Azure MCP Server 2.0 (stable), Salesforce Hosted MCP (Summer '26). Microsoft's .NET Agent Governance Toolkit adds policy enforcement + response sanitization to any MCP server with a single builder extension.

Context: Vercel skills.sh (600k+ skills, GA June 5), GitHub Copilot code review skills+MCP (GA July 29), NVIDIA SkillSpector (1-in-4 of 42,447 skills vulnerable), agentskills.io SKILL.md confirmed portable across 20+ harnesses. Firecrawl reports MCP usage growing ~35%/month on its own platform. MCPMarket (mcpmarket.com) operates as a live catalog with MCP-based discovery.

🌐 Sources: https://blog.modelcontextprotocol.io/posts/2026-07-28/ · https://github.blog/changelog/2026-07-29-copilot-code-review-agent-skills-and-mcp-now-generally-available/ · https://developer.chrome.com/blog/chrome-devtools-mcp · https://devblogs.microsoft.com/azure-sdk/announcing-azure-mcp-server-2-0-stable-release/ · https://devblogs.microsoft.com/dotnet/announcing-agent-governance-toolkit-mcp-extensions-for-dotnet/ · https://developer.salesforce.com/blogs/2026/06/the-salesforce-developers-guide-to-the-summer-26-release · https://mcpmarket.com/ · https://www.agensi.io/learn/ai-agent-marketplace-landscape-2026 · https://www.totalum.app/blog/agent-skills-marketplaces-2026 · https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution · https://devblogs.microsoft.com/agent-framework/discover-agent-skills-from-mcp-servers-in-net/ · https://aaif.io/blog/mcp-is-growing-up

---

### 7. [update] OpenCode (Anomaly): 191.8k Stars, v1.18.10 + Scout Subagent

**New fact since July 31:** v1.18.10 (July 30) adds Discover Modal models, desktop UI improvements; v1.18.9 restored legacy MCP SDK client compatibility, added opt-in V2 desktop sidecar (bundled CLI service), and collapsible model provider sections. Stars grew from 165k to 191.8k. Scout subagent for external docs research and auto-compact context management also shipped in July. Go tier ($10/mo for open-weight models) now available.

🌐 Sources: https://github.com/anomalyco/opencode · https://opencode.ai/changelog · https://www.gradually.ai/en/changelogs/opencode/ · https://www.developersdigest.tech/blog/opencode-developer-guide-2026 · https://www.morphllm.com/comparisons/opencode-vs-claude-code

---

### 8. [new] Juggler: GUI Coding Agent with Tree-Based CRDT Sessions (280 HN Points)

Juggler is the most-discussed new harness this cycle. Created by Jules Storer (creator of JUCE, the ubiquitous audio SDK), it attacks the UX problem of existing CLI/TUI agents: "Your conversation is an editable tree, not a chat history." Sessions are **Yjs CRDT documents** — users can create sub-threads, drill down, backtrack, compare, and edit; it is non-destructive and branching by design. Navigation uses Miller columns (Finder-style) rather than doom-scrolling.

Stars: 544 | License: AGPL-3.0 (core) / Apache-2.0 (extension SDK, so no copyleft on extensions) | Language: Go + Wails (no Electron) + plain JS | Multi-provider: Claude, OpenAI, Gemini, Ollama, OpenRouter. Multi-client: one server session accessible from desktop, browser, or mobile simultaneously.

HN top comment from anigbrowl: "Miller columns rather than a big doom-scroll — double sold." hypfer: "software made for actual productive usage instead of weird ricer clout." yowlingcat called out tree architecture, worktree support, and sandboxing as "features missing from Opencode."

🌐 Sources: https://news.ycombinator.com/item?id=48883305 · https://github.com/juggler-ai/juggler · https://juggler.studio/ · https://www.yodev.dev/t/el-creador-de-juce-construyo-el-gui-que-los-agentes-de-codigo-necesitaban/3802

---

### 9. [new] Block Buzz: Nostr-Based Workspace Where AI Agents Are Team Members

Block (Jack Dorsey's company) released Buzz on July 21, 2026 (Apache 2.0) — an open-source workspace built on Nostr where AI agents hold cryptographic identities and join channels exactly like human teammates. Every action lands as a signed event in an append-only audit log. The key innovation is that the agent's keypair belongs to the agent (and by extension the operator), not the platform — fully portable.

ACP-compatible harnesses supported: Claude Code, Codex, Goose. Teams can bring their own harness or build new ones. Self-hostable (or Block-hosted at buzz.xyz). Features: channels, threads, DMs, voice, code repositories, automated workflows. Nostr was chosen specifically to solve agent identity: "every participant, human or agent, holds a cryptographic keypair that belongs to them, not to the platform."

🌐 Sources: https://block.xyz/inside/introducing-buzz-where-humans-and-agents-work-together · https://explainx.ai/blog/jack-dorsey-block-buzz-ai-agents-team-chat-git-2026 · https://enterprisedna.co/resources/news/block-buzz-open-source-ai-agent-workspace-july-2026/ · https://www.businesstoday.in/technology/artificial-intelligence/story/jack-dorseys-block-launches-buzz-open-source-slack-rival-for-humans-and-ai-agents-544364-2026-07-22 · https://www.howdoiuseai.com/blog/2026-07-30-what-jack-dorsey-s-buzz-actually-is-and-how-to-try · https://rohitraj.tech/en/notes/block-buzz-agent-collaboration-platform-guide-2026

---

### 10. [new] Pydantic AI v2: Capabilities Architecture + Rust Sandbox

Pydantic AI v2 (June 23, 2026) restructures every extension point — tools, instructions, lifecycle hooks, model settings — into a single primitive called **capability**. Stable production code lives in core; fast-moving features (memory, guardrails, sandboxed execution) live in the separate **pydantic-ai-harness** package.

The headliner is **CodeMode**, which wraps all tools into a single `run_code` tool sandboxed by **Monty** (a Python interpreter written in Rust). The model writes Python that orchestrates multiple tools with loops, conditionals, and `asyncio.gather` in one round-trip. Monty runs only safe stdlib subsets (asyncio, json, re, math, pathlib); no third-party imports; no timing primitives. Result: a 10-item processing task that previously required 11 model calls now takes ~2.

Community extension: **Pydantic DeepAgents** combines Pydantic AI with DeepSeek reasoning models.

🌐 Sources: https://pydantic.dev/articles/pydantic-ai-v2 · https://github.com/pydantic/pydantic-ai-harness · https://pydantic.dev/docs/ai/harness/code-mode/ · https://github.com/pydantic/pydantic-ai · https://medium.com/@kacperwlodarczyk/pydantic-deepagents-an-open-agent-harness-on-pydantic-ai-251559c654dc · https://mcp.directory/blog/pydantic-ai-v2-harness-2026 · https://byteiota.com/pydantic-ai-v2-capabilities-harness/

---

### 11. [new] Amazon Bedrock AgentCore GA: Two-Call Managed Harness

Amazon Bedrock AgentCore went GA on June 18, 2026 — a fully managed harness requiring just two API calls: **CreateHarness** (define the agent) and **InvokeHarness** (run it). The harness runs the orchestration loop, executes tools, manages context, persists state across turns, and isolates each session. Configuration-based: declare the model, tools, skills, and instructions; AgentCore assembles and runs the loop.

Key capabilities: switch model providers mid-session without losing context (supports Bedrock, OpenAI, Gemini, LiteLLM); automatic semantic+summarization memory; Docker container + managed/EFS/S3 filesystem; AWS-curated skill catalog + custom from Git/S3; browser sandbox + code interpreter. Pricing: $0.0895/vCPU-hour, $0.00945/GB-hour — no harness fee. Unified CloudWatch observability. AWS AgentCore Gateway now implements the MCP 2026-07-28 spec.

🌐 Sources: https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-agentcore-harness-is-now-generally-available-go-from-idea-to-production-grade-agent-in-minutes/ · https://aws.amazon.com/about-aws/whats-new/2026/06/amazon-bedrock-agentcore-harness-generally-available/ · https://awsfundamentals.com/blog/bedrock-agentcore-harness · https://chatforest.com/builders-log/amazon-bedrock-agentcore-runtime-harness-builder-guide/ · https://dev.classmethod.jp/en/articles/20260617-amazon-bedrock-agentcore-harness-ga/ · https://aws.amazon.com/about-aws/whats-new/2026/04/agentcore-new-features-to-build-agents-faster/

---

### 12. [new] Tokenless (YC S26): Automatic Model Switching for Cost Control

Tokenless (YC S26) is an orchestration layer that automatically routes prompts across model backends based on cost and performance targets. Teams configure cost ceilings and quality tolerances; Tokenless decides when to flip from a frontier model to a cheaper alternative while maintaining perceived quality. It positions as a transparency layer over the model selection problem that most harnesses leave to the developer.

Related: Coasty (YC S26, https://news.ycombinator.com/item?id=48922706) provides an API for computer-use agents; the S26 cohort is notably heavy with agent harness infrastructure.

🌐 Sources: https://news.ycombinator.com/item?id=49099143 · https://www.promptzone.com/zuzanna_wang/does-tokenless-cut-ai-costs-with-auto-switch-1iac · https://www.extruct.ai/data-room/ycombinator-companies-s26/ · https://scouts.yutori.com/4c2d00c1-99a7-45f1-a839-b5930f60f763

---

### 13. [new] codebase-memory-mcp: 36.9k Stars, Semantic Code Intelligence as MCP Server

DeusData/codebase-memory-mcp (MIT) is now at 36.9k stars and reached v0.7.0 (Python Hybrid LSP support). It exposes **15 MCP tools** for code intelligence across **158 languages** via vendored tree-sitter parsers. The key differentiator is Hybrid LSP — a lightweight C implementation of type-resolution algorithms running alongside tree-sitter — which resolves `user.profile.display_name()` → `Profile.display_name` (semantic edges, not just syntactic). Features: architecture overview, dead code detection, semantic search via embedded embeddings, cross-service HTTP linking.

This is the #4 trending AI repo on GitHub in July 2026 (Analytics Vidhya).

🌐 Sources: https://github.com/DeusData/codebase-memory-mcp · https://www.analyticsvidhya.com/blog/2026/07/trending-ai-github-repositories/

---

### 14. [new] OmniRoute: 36.4k Stars, 290+ Providers + 12-Engine Token Compression

OmniRoute (MIT, TypeScript) is at 36.4k stars offering "one endpoint, 290+ providers (90+ free), 500+ models" with a 12-engine stacked token compression pipeline achieving 15-95% savings (avg ~89%). Engines include RTK (smart tool-result filtering), Caveman (rule-based prose compression, 65-75%), LLMLingua-2 (ML semantic pruning via MobileBERT), Session-Dedup (cross-turn deduplication). Code blocks, URLs, and structured data are always protected. 19 routing strategies including priority-based, cost-optimized, and auto-combo (12-factor live scoring); circuit breakers, model-level lockout, four-tier cascade.

Trending #8 on GitHub in July 2026.

🌐 Sources: https://github.com/diegosouzapw/OmniRoute · https://www.analyticsvidhya.com/blog/2026/07/trending-ai-github-repositories/

---

### 15. [new] Pu.sh: Full Coding Agent Harness in 400 Lines of Shell

Pu.sh (Show HN, 92 points) is a portable coding-agent harness written in ~400 lines of sh/curl/awk. It supports Anthropic and OpenAI APIs; 7 built-in tools (bash, read, write, edit, grep, find, ls — identical surface to Pi); REPL; auto-compaction; checkpoint/resume; pipe mode; 90 no-API tests. Zero dependencies beyond sh, curl, awk.

The discourse was notable: minified code drew "spaghetti" criticism; creator released an unminified version and admitted: "I cannot read most of this code. This wasn't possible for me a year ago" — a data point on AI-assisted self-bootstrapping harness development.

🌐 Sources: https://news.ycombinator.com/item?id=47968112 · https://github.com/NahimNasser/pu

---

### 16. [new] Harness Inc. Agent DLC: Enterprise AI Agent Lifecycle Platform

Harness Inc. (the SDLC platform company) launched **Agent DLC** on July 21, 2026 — extending its platform to cover the full AI Agent Development Lifecycle: build, test, deploy, operate, and govern agents through the same pipelines teams use for existing applications. The Harness CLI 3.0 (public beta July 15) also offers a single binary across pipelines, CD, code, artifacts, IaCM, feature flags, governance, and audit — designed for both human developers and deterministic AI agent execution.

EU AI Act context: Harness.io positions its AI Security module (AI discovery, risk visibility, runtime protection) as a compliance tool for the Articles 9-17 + 26 obligations now enforced as of August 2, 2026.

🌐 Sources: https://siliconangle.com/2026/07/21/harness-launches-agent-dlc-developers-deploy-ai-agents-using-familiar-processes-tools/ · https://www.prnewswire.com/news-releases/introducing-harness-agent-dlc-new-capabilities-for-the-ai-agent-development-lifecycle-302830967.html · https://www.harness.io/blog/announcing-harness-cli · https://www.harness.io/blog/prepare-for-the-eu-ai-act-with-harness-ai-security · https://developer.harness.io/docs/platform/harness-ai/harness-agents/ · https://www.devopsdigest.com/harness-releases-autonomous-worker-agents

---

### 17. [new] EU AI Act August 2 Enforcement: Harness Compliance Now a Legal Requirement

The EU AI Act's Articles 9-17 (providers) and Article 26 (deployers) for high-risk AI systems and Article 50 (generative AI transparency obligations) entered full enforcement as of **August 2, 2026**. The compliance challenge for agent harnesses is structural: harmful outcomes emerge from **action sequences** (plan → tool call → observe → revise) rather than a single model output, making traditional output-level compliance insufficient.

Key vendor positioning: Intent by Augment Code (living spec = compliance record); Prediction Guard; Harness.io AI Security (automated AI asset discovery + data flow monitoring). The EU AI Act resource site (artificialintelligenceact.eu) now tracks enforcement actions. Aguardic: "The Act was written for models. Your agents need runtime compliance."

🌐 Sources: https://www.aguardic.com/blog/eu-ai-act-agents-runtime-compliance · https://www.re-entry.ai/blog/eu-ai-act-2026-deadline-ai-coding-agents · https://www.augmentcode.com/guides/eu-ai-act-2026 · https://asanify.com/blog/news/eu-ai-act-enforcement-july-13-2026/ · https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai · https://artificialintelligenceact.eu/ · https://predictionguard.com/blog/best-eu-ai-act-compliance-tools-for-enterprise-ai-programs-in-2026 · https://kla.digital/blog/best-eu-ai-act-compliance-software-2026

---

**Still true** (ongoing threads, no new facts today):
- JADEPUFFER agentic ransomware (Sysdig, July 1) + Ant Group SingGuard-NSFA open-source guardrail (July 14) [jadepuffer-agentic-security]
- Grok-Build (xAI, Rust, 23.3k stars) open-source harness with Agent Client Protocol [grok-build-xai-rust-harness]
- Self-Harness (Shanghai AI Lab, arXiv:2606.09498) — autonomous harness optimization, +60% Terminal-Bench 2.0 [self-harness-auto-optimization]
- OpenHarness (HKUDS, MIT, 15.1k stars) with 43 tools, 10 subsystems, ohmo built-in agent [openharness-hkuds]
- VSCode 1.130 (July 22) Agent Host Protocol — sessions decouple from window lifetime, worktree isolation [vscode-1130-agent-host]
- Google Antigravity 2.0 (May I/O 2026): forced Gemini CLI sunset June 18; SKILL.md portable unchanged [antigravity-gemini-cli-successor]
- Claw Code (105k stars): clean-room Python/Rust Claude Code rewrite from source leak [claw-code-claude-rewrite]
- ruvnet/agent-harness-generator (MetaHarness, 523 stars): generates branded harnesses with Ed25519-signed SBOM [metaharness-scaffold-generator]
- Harness Engineering paradigm (Agent = Model + Harness) confirmed by Stanford HAI (3% prompt vs 28-47% harness); DeepSeek internal formula [harness-engineering-paradigm]
- DeerFlow 2.0 (ByteDance, 77.9k stars) SuperAgent harness with TIAMAT cloud memory [deerflow-superagent-harness]
- Hermes Agent (Nous Research) native desktop app; self-improving loop; Grok SuperGrok OAuth [hermes-agent-self-improving]
- Omnigent (Databricks, Apache 2.0): first meta-harness; compose/swap harnesses without rewriting [omnigent-meta-harness]
- Microsoft MAF GA + Copilot code review skills+MCP GA July 29 [microsoft-maf-codeact]
- Zot (Go single-binary coding agent, 299 stars, HN 107 points; Claude Code API spoofing controversy) [zot-go-coding-harness]
- oh-my-pi (omp, 14.7k stars) + oh-my-openagent (omo, 48k stars): Pi derivatives with Sisyphus Orchestrator [omp-omo-pi-derivatives]
- Yorishiro (58 stars): macOS "Presence Harness" with 3D animated avatar + Reflex Layer [yorishiro-presence-harness]
- agentskills.io SKILL.md standard: confirmed portable across 20+ harnesses with zero modification [agentskills-open-standard]
- Letta Agent File (.af format, Apache 2.0, 1.2k stars): leading open format for stateful agent serialization [letta-agent-file-format]
- Layered OSS stack (17+ specialized tools per task) consensus; star count ≠ maintenance [layered-oss-stack-over-single-framework]
- macOS as proving ground for novel harness forms: Yorishiro, macOS26/Agent!, Supacode [macos-harness-proving-ground]
- AHE formalization (arXiv:2604.25850) + Lilian Weng July 4 synthesis covering Self-Harness, ACE, MCE, Meta-Harness [ahe-automated-harness-evolution]
- MCP/skill security: SkillSpector 64 patterns, 16 categories; 1-in-4 of 42,447 skills vulnerable; 76% of Snyk-scanned malicious [mcp-security-nsa-supply-chain]
- Internal Harness (builder) vs External Harness (operator) disambiguation ongoing [harness-internal-external-disambiguation]
- "Environment Architect" as new role: translating domain tacit knowledge into machine-readable harness specs [environment-architect-new-role]
- Mozilla Otari (July 6, 357 stars): OpenAI-compatible LLM gateway, 40+ providers, virtual keys, prompt injection detection [mozilla-otari-llm-gateway]
- Statewright (Rust, 373 stars, Apache 2.0+FSL): state machine guardrails; 2/10 → 10/10 SWE-bench on same tasks [statewright-guardrails]
- Headroom (62k stars, Netflix engineer): 20-60% token reduction; library + MCP server + proxy [headroom-token-compression]
- Pi (54k+ stars, MIT, Armin Ronacher + Mario Zechner): sub-1000-token system prompt minimal harness [pi-minimal-agent-harness]
- NVIDIA SkillSpector (168 stars, open-source): skill security scanner, 64 patterns, 16 categories [nvidia-skillspector-security]
- DeepSeek Harness team (May 2026) + Reasonix terminal agent with 60%+ cost reduction on long sessions [deepseek-harness-team]
- CLI-Anything (HKUDS, 46.4k stars): auto-generated CLIs with SKILL.md; CLI-Hub package manager [cli-anything-hkuds]
- Forge (forge-agents/forge) + Adulari/forge: ACP universal CLI with 3-agent split + 300+ model routing [forge-acp-universal-cli]
- GitHub Copilot skills+MCP GA July 29: SKILL.md in .github/skills; read-only MCP for all paid tiers [github-copilot-skills-mcp-ga]
- OpenCode/Anomaly (191.8k stars): see update #7 above for latest; ongoing adoption [opencode-anomaly-rebrand]

---

## Cross-Source Patterns

### Pattern 1: Stateless MCP as the Protocol's Coming-of-Age Moment
Appeared on: Hacker News (127+278 points), VentureBeat, Trilogy AI, Claude.com blog, AWS blog, Simon Willison's blog, Bluesky (#MCP feed), Zenn (🇯🇵), CSDN (🇨🇳)

The July 28 spec is being treated as the moment MCP matured from a promising but operationally awkward protocol into standard web infrastructure. The phrase "runs behind a round-robin load balancer like any REST API" appears across multiple independent analyses. Enterprise Managed Authorization (EMA) fills the B2B authentication gap that had blocked large deployments. JP and CN coverage is substantial and technically rigorous.

> "The biggest changes are breaking ones, and the community has chosen to do the hard work rather than paper over the gaps." — Trilogy AI ([link](https://trilogyai.substack.com/p/mcp-grows-up-what-the-july-28-spec))

> "Stateless MCP has recaptured my interest" — Simon Willison ([link](https://simonwillison.net/2026/Jul/31/stateless-mcp/))

### Pattern 2: GUI as the New Frontier for Coding Agent UX
Appeared on: Hacker News (Juggler, 280 points), YouTube (Omnigent video, Hermes tutorials), Bluesky, GitHub Trending (Juggler studio)

The text-only TUI/CLI paradigm is being challenged from two directions: Juggler (tree-based CRDT GUI, not a chat), and Block Buzz (channels+voice workspace where agents are members). HN commenters are explicit about what's missing from incumbent CLI tools — branching, inspection, approval visibility. The creation of Juggler by Jules Storer (JUCE creator, C++ audio world) brings a different aesthetic: "software made for actual productive usage instead of weird ricer clout."

> "Miller columns rather than a big doom-scroll" — anigbrowl on HN ([link](https://news.ycombinator.com/item?id=48883305))

### Pattern 3: Infrastructure Layer Maturing (Token Compression, Provider Routing, Security Scanning)
Appeared on: GitHub Trending (codebase-memory-mcp 36.9k, OmniRoute 36.4k, Headroom 62k), Analytics Vidhya report, awesome-harness-engineering list

The "middle layer" between harness and model is industrializing: context compression (OmniRoute, Headroom), semantic codebase memory (codebase-memory-mcp), state machine guardrails (Statewright), and skill security scanning (SkillSpector). These projects are accumulating tens of thousands of stars without being harnesses themselves — they extend harnesses. OmniRoute's 290+ providers with auto-fallback suggests the provider consolidation play is as real as the harness layer.

### Pattern 4: JP/CN Convergence on "Harness Engineering" as the Term
Appeared on: Qiita (multiple posts), Zenn, note.com, Speakerdeck, CSDN, Zhihu

Both Japanese and Chinese developer communities use "ハーネスエンジニアリング" and "智能体框架工程" to describe the same paradigm: Agent = Model + Harness. The Stanford HAI "3% vs 47%" finding is independently cited in JP (note.com) and CN (CSDN) sources without referencing each other. The "AI USB-C" MCP metaphor originated on Zenn and spread globally.

> 🇯🇵 「ハーネスエンジニアリングは、単なる「プロンプトの次のトレンド」ではありません」("Harness engineering transcends trend status — it represents AI-native software engineering itself") — note.com ([link](https://note.com/aiedgerunner/n/nbca11a6835f2))

> 🇯🇵 「AIエージェントの設計は、分散システム設計と同じ問題を多く含む」("AI agent design contains many problems identical to distributed systems design") — Qiita ([link](https://qiita.com/GYact/items/dff02cf5271048629857))

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| julesrms | Show HN: Juggler – open-source GUI coding agent | 280 | 119 | "Miller columns rather than doom-scroll — double sold" | https://news.ycombinator.com/item?id=48883305 |
| (staff) | Zero-Touch OAuth for MCP (EMA) | 278 | 103 | "Isolating auth flow outside agent context window" | https://news.ycombinator.com/item?id=48592163 |
| punkpeye | MCP 2026-07-28 Spec: transport going stateless | 127 | 40 | "~30% of 62,726 servers actively maintained" | https://news.ycombinator.com/item?id=49088058 |
| (staff) | Coding Tools MCP v0.2.2 | — | — | Give any AI chat a pair of hands on your code | https://news.ycombinator.com/item?id=49086871 |
| NahimNasser | Show HN: Pu.sh – coding agent harness in 400 lines of shell | 92 | 28 | "I cannot read most of this code" | https://news.ycombinator.com/item?id=47968112 |
| (staff) | Skills are quietly becoming the unit of agent knowledge | — | — | "A skill is a tested workflow in markdown" | https://news.ycombinator.com/item?id=47475832 |
| (staff) | When does MCP make sense vs CLI? | — | — | CLI: access to local env, jq, duckdb | https://news.ycombinator.com/item?id=47208398 |
| (staff) | Launch HN: Tokenless (YC S26) – auto model switching | — | — | Cost target + performance tolerance routing | https://news.ycombinator.com/item?id=49099143 |
| frenchie4111 | Show HN: Harness – parallel Claude Code agents + Git worktrees | 3 | 1 | Status: green/yellow/red tab indicators | https://news.ycombinator.com/item?id=47948379 |
| (staff) | Show HN: Browser Harness – LLM freedom for any browser task | — | — | Browser automation harness | https://news.ycombinator.com/item?id=47890841 |
| (staff) | Show HN: Broccoli – one-shot cloud coding agent | — | — | Cloud sandbox per task; CI loop; opens PR | https://news.ycombinator.com/item?id=47865642 |
| (staff) | Show HN: How to self-host a code review agent | — | — | Self-hosted code review workflow | https://news.ycombinator.com/item?id=49128177 |
| (staff) | MCP is eating the world | — | — | Strong engagement thread | https://news.ycombinator.com/item?id=44338793 |
| (staff) | How likely are we to look back on Agent/MCP/Skills as early Netscape? | — | — | Skeptical thread | https://news.ycombinator.com/item?id=46315957 |

**YouTube:**
| Channel/Video | Title | Views | Transcript? | URL |
|--------------|-------|-------|-------------|-----|
| (various) | You Can Learn AI Agent Harness In Real Code In 20 Min | — | No | https://www.youtube.com/watch?v=rvRyBhILrls |
| Agentic AI Summit | Your Coding Agent is Your Autonomous Security Harness | — | No | https://www.youtube.com/watch?v=ayQFXbXcmvc |
| (various) | Harness Engineering: What Separates Top Agentic Engineers | — | No | https://www.youtube.com/watch?v=ulNsa0sD8N0 |
| (various) | You Can Learn Pi Minimal Coding Agent Harness In 22 Min | — | No | https://www.youtube.com/watch?v=0sI0MbCt4f4 |
| (various) | Omnigent: The New Meta-Harness for EVERY Coding Agent | — | No | https://www.youtube.com/watch?v=oGE_Dwz-rMk |
| (various) | The new Hermes Agent update officially ended OpenClaw | — | No | https://www.youtube.com/watch?v=_LYXbI6JY5M |
| (various) | FULL Hermes Agent Tutorial For Beginners in 2026 | — | No | https://www.youtube.com/watch?v=4ftONmdO9yo |
| (various) | AI Agents Full Course 2026: Master Agentic AI (2 Hours) | — | No | https://www.youtube.com/watch?v=EsTrWCV0Ph4 |
| Anthropic | Anthropic Masterclass on Building Agent Harnesses | — | No | https://www.youtube.com/watch?v=efRIrLXoOVA |
| (various) | Cursor: coding agents tutorial 2026 | — | No | https://www.youtube.com/watch?v=kF2WQgk1LtY |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| sdk.vercel.ai | Custom MCP transports now supported in AI SDK | — | https://bsky.app/profile/sdk.vercel.ai/post/3lkofluarp52r |
| sdk.vercel.ai | MCP client support for the AI SDK is here! | — | https://bsky.app/profile/sdk.vercel.ai/post/3lk6k3zrzik2s |
| langchain.bsky.social | LangChain agent harness update | — | https://bsky.app/profile/langchain.bsky.social/post/3lkodcjypgk2p |
| thenewstack.io | OpenClaw vs Hermes Agent harness comparison | — | https://bsky.app/profile/thenewstack.io/post/3ll5p7kwbb72x |
| automateyournetwork.ca | First MCP Server setup and working client | — | https://web-cdn.bsky.app/profile/automateyournetwork.ca/post/3lkmhtkgtoc2c |
| jbranchaud.bsky.social | MCP tooling update | — | https://bsky.app/profile/jbranchaud.bsky.social/post/3lkliuhkugc2n |
| brianell.in | Experimental MCP Server for Bluesky APIs | — | https://bsky.app/profile/brianell.in/post/3lkwbtv6d5c2y |
| MCP Sky Feed | Dedicated Bluesky MCP feed | — | https://bsky.app/profile/did:plc:hluqcgwbbxtglofzk53gmwbw/feed/mcp |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | MCP Spec Blog | https://blog.modelcontextprotocol.io/posts/2026-07-28/ | Definitive spec breakdown |
| 🌐 | Simon Willison | https://simonwillison.net/2026/Jul/31/stateless-mcp/ | Independent mcp-explorer + datasette-mcp tools |
| 🌐 | Juggler Studio | https://juggler.studio/ | GUI coding agent download |
| 🌐 | GitHub Juggler | https://github.com/juggler-ai/juggler | 544 stars, AGPL-3.0/Apache-2.0 |
| 🌐 | Block Buzz | https://block.xyz/inside/introducing-buzz-where-humans-and-agents-work-together | Agent-as-team-member paradigm |
| 🌐 | Pydantic AI v2 | https://pydantic.dev/articles/pydantic-ai-v2 | Capability primitive + Harness package |
| 🌐 | AgentCore AWS | https://aws.amazon.com/blogs/machine-learning/amazon-bedrock-agentcore-harness-is-now-generally-available-go-from-idea-to-production-grade-agent-in-minutes/ | Two-call managed harness GA |
| 🌐 | Kiro Changelog | https://kiro.dev/changelog/ | CLI 2.16.0 tangents |
| 🌐 | Claude Code Whats New | https://code.claude.com/docs/en/whats-new | Artifacts call MCP connectors |
| 🌐 | OpenClaw Releasebot | https://releasebot.io/updates/openclaw | July 30/28 updates |
| 🌐 | Warp Oz Blog | https://www.warp.dev/blog/multi-harness-cloud-agent-orchestration | Multi-harness live |
| 🌐 | Chrome DevTools MCP | https://developer.chrome.com/blog/chrome-devtools-mcp | Browser debugging via MCP |
| 🌐 | Azure MCP Server 2.0 | https://devblogs.microsoft.com/azure-sdk/announcing-azure-mcp-server-2-0-stable-release/ | Azure resource management via MCP |
| 🌐 | codebase-memory-mcp | https://github.com/DeusData/codebase-memory-mcp | 36.9k stars, 15 MCP tools |
| 🌐 | OmniRoute | https://github.com/diegosouzapw/OmniRoute | 36.4k stars, 290+ providers |
| 🌐 | EU AI Act deadline | https://www.aguardic.com/blog/eu-ai-act-agents-runtime-compliance | Runtime compliance for agents |
| 🌐 | Harness Agent DLC | https://siliconangle.com/2026/07/21/harness-launches-agent-dlc-developers-deploy-ai-agents-using-familiar-processes-tools/ | Enterprise agent lifecycle |
| 🌐 | Tokenless HN | https://news.ycombinator.com/item?id=49099143 | YC S26 auto model switching |
| 🌐 | OpenCode GitHub | https://github.com/anomalyco/opencode | 191.8k stars |
| 🌐 | OpenCode Changelog | https://opencode.ai/changelog | v1.18.10 |
| 🌐 | VSCode 1.130 | https://code.visualstudio.com/updates/v1_130 | Agent Host Protocol |
| 🌐 | Copilot Skills+MCP GA | https://github.blog/changelog/2026-07-29-copilot-code-review-agent-skills-and-mcp-now-generally-available/ | GA July 29 |
| 🌐 | Pu.sh GitHub | https://github.com/NahimNasser/pu | 400-line shell harness |
| 🌐 | Statewright | https://github.com/statewright/statewright | State machine guardrails |
| 🌐 | Headroom | https://github.com/headroomlabs-ai/headroom | 62k stars context compression |
| 🌐 | .NET Governance Toolkit MCP | https://devblogs.microsoft.com/dotnet/announcing-agent-governance-toolkit-mcp-extensions-for-dotnet/ | Policy enforcement for MCP |
| 🌐 | Salesforce Hosted MCP | https://developer.salesforce.com/blogs/2026/06/the-salesforce-developers-guide-to-the-summer-26-release | Salesforce org via MCP |
| 🌐 | MS Agent Skills from MCP | https://devblogs.microsoft.com/agent-framework/discover-agent-skills-from-mcp-servers-in-net/ | Dynamic skill discovery |
| 🌐 | MAF Harness Released | https://devblogs.microsoft.com/agent-framework/the-microsoft-agent-framework-harness-is-now-released/ | MAF harness details |
| 🌐 | Kiro Flaw | https://thehackernews.com/2026/07/aws-kiro-flaw-let-poisoned-web-page.html | Security disclosure |
| 🌐 | Analytics Vidhya Trending | https://www.analyticsvidhya.com/blog/2026/07/trending-ai-github-repositories/ | July 2026 top repos |
| 🌐 | VentureBeat MCP | https://venturebeat.com/infrastructure/mcp-just-got-its-biggest-update-ever-heres-what-changes-for-ai-agents | Mass coverage |
| 🌐 | VentureBeat MCP stateless | https://trilogyai.substack.com/p/mcp-grows-up-what-the-july-28-spec | Enterprise enterprise analysis |
| 🌐 | Augment EU guide | https://www.aguardic.com/blog/eu-ai-act-agents-runtime-compliance | Runtime compliance |
| 🌐 | EU AI act coding | https://www.re-entry.ai/blog/eu-ai-act-2026-deadline-ai-coding-agents | Deadline detail |
| 🌐 | Pydantic CodeMode | https://pydantic.dev/docs/ai/harness/code-mode/ | Monty sandbox docs |
| 🌐 | pydantic-ai-harness | https://github.com/pydantic/pydantic-ai-harness | Separate package |
| 🌐 | SkillSpector | https://github.com/nvidia/skillspector | Skill security scanner |
| 🌐 | awesome-harness-eng | https://github.com/ai-boost/awesome-harness-engineering | 3.3k stars; updated July 28 |
| 🌐 | best-of-harnesses | https://github.com/RyanAlberts/best-of-Agent-Harnesses | 100+ harnesses, weekly rescore |
| 🌐 | Harness CLI 3.0 | https://www.harness.io/blog/announcing-harness-cli | Single binary DevSecOps |
| 🌐 | bradAGI awesome-cli | https://github.com/bradAGI/awesome-cli-coding-agents | Curated CLI agents |
| 🌐 | mcpmarket.com | https://mcpmarket.com/ | MCP discovery platform |
| 🌐 | Warp SD Times | https://sdtimes.com/ai/warp-updates-oz-to-help-enterprises-orchestrate-coding-agents-across-any-model-or-harness/ | SD Times coverage |
| 🌐 | Classmethod AgentCore | https://dev.classmethod.jp/en/articles/20260617-amazon-bedrock-agentcore-harness-ga/ | JP English coverage |
| 🌐 | awsfundamentals AgentCore | https://awsfundamentals.com/blog/bedrock-agentcore-harness | Technical guide |
| 🌐 | block.xyz buzz | https://www.businesstoday.in/technology/artificial-intelligence/story/jack-dorseys-block-launches-buzz-open-source-slack-rival-for-humans-and-ai-agents-544364-2026-07-22 | July 22 confirmed |
| 🌐 | flowtivity hermes | https://flowtivity.ai/blog/openclaw-vs-hermes-agent-comparison/ | Cross-harness migration |
| 🌐 | itsfoss warp | https://itsfoss.com/news/warp-oz-multi-harness-update/ | FOSS angle |
| 🌐 | state CLI agents | https://blog.arcbjorn.com/state-of-cli-coding-agents-2026 | Mid-2026 state of play |
| 🌐 | mightybot coding | https://mightybot.ai/blog/coding-ai-agents-for-accelerating-engineering-workflows/ | All labs shipping model+harness |
| 🌐 | firecrawl best agents | https://www.firecrawl.dev/blog/best-ai-coding-agents | Harness cost+accuracy comparison |
| 🌐 | AAIF MCP growing up | https://aaif.io/blog/mcp-is-growing-up | Agentic AI Foundation |
| 🌐 | yodev juggler | https://www.yodev.dev/t/el-creador-de-juce-construyo-el-gui-que-los-agentes-de-codigo-necesitaban/3802 | Spanish community coverage |
| 🌐 | philschmid harness | https://www.philschmid.de/agent-harness-2026 | HuggingFace engineer view |
| 🌐 | model-agnostic harness | https://medium.com/@kacperwlodarczyk/making-an-agent-harness-actually-model-agnostic-bd2858aa8079 | Practical design |
| 🌐 | opencode vs claude | https://www.morphllm.com/comparisons/opencode-vs-claude-code | OpenCode vs Claude Code July 2026 |
| 🌐 | Databricks Omnigent | https://www.databricks.com/blog/introducing-omnigent-meta-harness-combine-control-and-share-your-agents | Meta-harness post |
| 🌐 | screenpipe YC S26 | https://explainx.ai/blog/screenpipe-yc-s26-local-work-memory-agents-july-2026 | Local work memory |
| 🌐 | Coasty YC S26 | https://news.ycombinator.com/item?id=48922706 | Computer-use API |
| 🌐 | Pydantic DeepAgents | https://medium.com/@kacperwlodarczyk/pydantic-deepagents-an-open-agent-harness-on-pydantic-ai-251559c654dc | DeepSeek+Pydantic community harness |
| 🌐 | AAIF MCP growing | https://aaif.io/blog/mcp-is-growing-up | Foundation perspective |
| 🌐 | Harness DLC PR | https://www.prnewswire.com/news-releases/introducing-harness-agent-dlc-new-capabilities-for-the-ai-agent-development-lifecycle-302830967.html | Official press release |
| 🌐 | MS Power Platform MCP | https://learn.microsoft.com/en-us/power-platform/release-plan/2026wave1/microsoft-copilot-studio/use-mcp-compliant-tools-agent-workflows | Copilot Studio MCP |
| 🌐 | OpenClaw vs Hermes | https://thenewstack.io/openclaw-hermes-agent-harness/ | The New Stack comparison |
| 🌐 | Aurora comparison | https://aurora-designs.ca/blog/hermes-vs-openclaw-vs-claude-code | Three-way comparison |
| 🌐 | Neowin VSCode | https://www.neowin.net/news/microsoft-lands-visual-studio-code-1130-with-agent-rearchitecturing/ | Agent rearchitecturing |
| 🌐 | ByteIota VSCode | https://byteiota.com/vs-code-1-130-agent-host-assisted-approvals-typescript-7/ | Assisted approvals |
| 🌐 | Copilot Changelog | https://github.blog/changelog/2026-06-22-new-features-and-claude-as-agent-provider-preview-in-jetbrains-ides/ | JetBrains Claude preview |
| 🇯🇵 | Qiita (Ryu-Yanagi) | https://qiita.com/Ryu-Yanagi/items/d7cadf768f2e5da243fb | Harness Engineering complete guide JP |
| 🇯🇵 | Qiita (GYact) | https://qiita.com/GYact/items/dff02cf5271048629857 | MCP + multi-agent architecture |
| 🇯🇵 | Qiita (backend-notes) | https://qiita.com/backend-notes/items/d0c76aa9963e43118df4 | GitHub Trending = agent ops repos |
| 🇯🇵 | Qiita (taka_yayoi) | https://qiita.com/taka_yayoi/items/2ff51f2df46cc1285ba3 | Omnigent meta-harness JP |
| 🇯🇵 | Zenn (babushkai) | https://zenn.dev/babushkai/articles/2026-01-20-agentic-ai-trends-2026 | "AI USB-C" metaphor; market data |
| 🇯🇵 | Zenn (lumichy) | https://zenn.dev/lumichy/articles/mcp-vs-skills-ai-agent-2026 | MCP vs Skills architecture |
| 🇯🇵 | Zenn (shio_shoppaize) | https://zenn.dev/shio_shoppaize/articles/shogun-harness-engineering | Critical: "just Git workflows in bash"? |
| 🇯🇵 | Zenn (aiwatch_jp) | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | OSS stack maintenance check |
| 🇯🇵 | note.com (aiedgerunner) | https://note.com/aiedgerunner/n/nbca11a6835f2 | 3% vs 47% Stanford HAI data |
| 🇯🇵 | Hatena (shimayo0218) | https://shimayo0218.hatenablog.com/entry/2026/04/01/234316 | Claude Code harness mechanics |
| 🇯🇵 | Hatena (miharimemo) | https://miharimemo.hatenablog.com/entry/2026/05/25/094129 | MCP Tunnels + Managed Agents |
| 🇯🇵 | Hatena (wasted-job) | https://wasted-job.hatenablog.com/entry/2026/05/12/091306 | Copilot Workspace guide |
| 🇯🇵 | Speakerdeck (tame) | https://speakerdeck.com/tame/aiezientoshi-dai-nohanesuenziniaringutoha | Environment Architect role slide |
| 🇨🇳 | CSDN (xh2277659985) | https://blog.csdn.net/xh2277659985/article/details/163302479 | MCP 2026 upgrade coverage |
| 🇨🇳 | CSDN (weixin) | https://blog.csdn.net/weixin_54908067/article/details/162665003 | MCP to multi-agent guide |
| 🇨🇳 | CSDN DevPress | https://devpress.csdn.net/v1/article/detail/162696573 | AI Agent + MCP essentials |
| 🇨🇳 | CSDN Agent | https://agent.csdn.net/6a61784510ee7a33f291928e.html | Multi-agent from scratch |
| 🇨🇳 | Zhihu (p/2011401752) | https://zhuanlan.zhihu.com/p/2011401752482689910 | Claude Code vs Cursor deep test |
| 🇨🇳 | Zhihu (20 frameworks) | https://zhuanlan.zhihu.com/p/1997716266094449634 | 20 framework selection guide |
| 🇨🇳 | Zhihu (coding tools) | https://zhuanlan.zhihu.com/p/2041289697675195678 | Full 2026 coding tools guide |
| 🇨🇳 | a2a-mcp.org | https://a2a-mcp.org/blog/mcp-2026-roadmap-zh | MCP 2026 roadmap in Chinese |
| 🇨🇳 | liuqi.dev | https://www.liuqi.dev/blog/mcp-2026-stateless-revolution | Stateless MCP revolution CN |
| 🇨🇳 | jishuzhan.net | https://jishuzhan.net/article/2066505783961022465 | Frameworks + MCP deep analysis |
| 🇨🇳 | clawd.org.cn | https://clawd.org.cn | OpenClaw Chinese community portal |
| 🇨🇳 | enjoy.aigemini.org | https://enjoy.aigemini.org/blogs/2026年ai编程智能体大横评... | Seven-way comparison with Antigravity |

---

## Stats Block

```
├─ 🟠 Reddit: not accessed (no API data)
├─ 🔵 X: not accessed
├─ 🔴 YouTube: 10 videos │ views not extracted
├─ 🟢 HN: 14 threads │ ~940+ points │ ~430+ comments
├─ 🟣 TikTok: not accessed
├─ 🩷 Instagram: not accessed (1 Juggler promo post found via search)
├─ 🦋 Bluesky: 8 posts │ engagement not extracted
├─ 📊 Polymarket: no markets found on this topic
├─ 🌐 Web: 82 pages │ 🇯🇵 13 │ 🇨🇳 12
└─ 🗣️ Top voices: @sdk.vercel.ai (Bluesky), @julesrms (HN/Juggler), @simonwillison (blog) │ r/localllama (not accessed)
```

---

## Out of Scope but Notable

- **Nutlope/Hallmark** (10k stars, GitHub trending #10) — a "design skill" for coding agents with 57 quality gates to reduce templated UI output. Not a harness itself, but a SKILL.md-style quality layer for design tasks. May indicate skills specializing beyond text-generation. ([link](https://github.com/Nutlope/hallmark))

- **Coasty (YC S26)** — provides an API for computer-use agents (not a harness, an infra primitive). Suggests computer-use is becoming a commodity layer distinct from the harness. ([link](https://news.ycombinator.com/item?id=48922706))

- **HKUDS/Vibe-Trading** (24k stars, GitHub trending #3) — natural language-driven backtesting with 452 pre-built alpha factors. Pure finance/quant domain; uses same HKUDS harness pattern as OpenHarness and CLI-Anything but in trading. Suggests HKUDS is building a domain-specific harness empire. ([link](https://github.com/HKUDS/Vibe-Trading))

---

## Data Gaps

- **Reddit:** Not accessed in this run. No subreddit thread engagement data (upvotes, comment counts) available. Discussions in r/LocalLLaMA, r/MachineLearning, and r/singularity are known to cover this topic but were not retrieved.
- **X/Twitter:** Not accessed. Social signal on new tool launches missing.
- **TikTok/Instagram:** Not indexed for this topic.
- **YouTube transcripts:** Video list retrieved; no transcripts extracted. View/like counts not obtained.
- **Bluesky engagement:** Post text available; like/repost counts not retrieved.
- **CSDN/Zhihu direct fetch:** Several pages returned 403/521 — identified via DuckDuckGo metadata only.
- **Tokenless HN page:** 429 Too Many Requests on direct fetch — summary from secondary sources.
- **SOURCE HEALTH:** No backends reported DOWN. All sources tested were UP (some returned 403/429 on specific pages, which is expected gating, not a backend failure).

**Approximate coverage:** 70% — English web + HN are comprehensive; JP/CN hubs identified but not all pages directly readable; Reddit/X/TikTok/YouTube metrics absent.

---

## Key Quotes

> "Stateless MCP has recaptured my interest" — Simon Willison ([link](https://simonwillison.net/2026/Jul/31/stateless-mcp/)) 🌐

> "Miller columns rather than a big doom-scroll — double sold." — anigbrowl on HN re: Juggler ([link](https://news.ycombinator.com/item?id=48883305)) 🌐

> "Isolating the auth flow outside of the agent's context window, and potentially out of the harness completely" — sean_lynch on EMA/Zero-Touch OAuth ([link](https://news.ycombinator.com/item?id=48592163)) 🌐

> "The biggest changes are breaking ones, and the community has chosen to do the hard work rather than paper over the gaps." — Trilogy AI on MCP 2026-07-28 ([link](https://trilogyai.substack.com/p/mcp-grows-up-what-the-july-28-spec)) 🌐

> 🇯🇵 "ハーネスエンジニアリングは、AIネイティブなソフトウェア工学そのものだ" ("Harness engineering IS AI-native software engineering itself") — note.com/aiedgerunner ([link](https://note.com/aiedgerunner/n/nbca11a6835f2))

> 🇯🇵 "AIエージェントの設計は、分散システム設計と同じ問題を多く含む" ("AI agent design contains many problems identical to distributed systems design") — Qiita/GYact ([link](https://qiita.com/GYact/items/dff02cf5271048629857))

> "Agents are treated as members, not bots — each holding its own cryptographic identity, joining channels exactly like a person." — Block Buzz announcement ([link](https://block.xyz/inside/introducing-buzz-where-humans-and-agents-work-together)) 🌐

> "The Act was written for models. Your agents need runtime compliance." — Aguardic on EU AI Act ([link](https://www.aguardic.com/blog/eu-ai-act-agents-runtime-compliance)) 🌐

> "I cannot read most of this code. This wasn't possible for me a year ago." — NahimNasser on Pu.sh (AI-written harness) ([link](https://news.ycombinator.com/item?id=47968112)) 🌐

> 🇨🇳 "Claude Code excels at tracking cross-layer dependencies — Cursor occasionally misses dependencies beyond 2-3 layers" — Zhihu comparison ([link](https://zhuanlan.zhihu.com/p/2011401752482689910))
