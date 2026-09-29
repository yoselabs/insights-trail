# AI Agent Harnesses — Daily Briefing
**Date:** 2026-09-29
**Query type:** GENERAL
**Sources:** Anthropic blog, TechCrunch, Simon Willison, Developers Digest, GitHub (agents-radar, openrig, hindsight, paperclip, reindent/jauvex, ext-skills, RyanAlberts/best-of-Agent-Harnesses), Releasebot (CC/OC/Cursor), GitHub Copilot Changelog, HN, Decrypt, InfoQ, Salesforce, SiliconANGLE, VentureBeat, Qiita, Zenn, note, labmemo.com, ITmedia, Publickey, Zhihu, CSDN, CNBlogs, Sohu, QQ news, Felo

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 2 threads | 855+179 pts, 585+74 comments | 🌐 Sonnet 5.5 (855/585); AX (Sep 25 carry-over) |
| Web (global) | 40 pages | — | 🌐 WebSearch + WebFetch |
| Web (Japan) | 11 pages | — | 🇯🇵 Qiita, Zenn, note, ITmedia, Publickey, labmemo |
| Web (China) | 10 pages | — | 🇨🇳 Zhihu, CSDN, CNBlogs, Sohu, QQ news, Felo, linux.do |
| GitHub Trending | 2 digests | — | 🌐 agents-radar #249 (Sep 28), #250 (Sep 29) |

---

## Synthesized Findings

### 1. [new] Claude Sonnet 5.5 (Sep 28): Terminal-Bench 70.6% — surpasses Opus 5.5, same price as Sonnet 5 🌐🇯🇵🇨🇳

**Claim:** Anthropic shipped Sonnet 5.5 Sep 28; Terminal-Bench 4.0 70.6% beats Opus 5.5's 66.4% despite costing half as much ($2/$10 vs $4/$20 per 1M tokens); 5 breaking API changes; HN 855pts/585 comments.
**Evidence:**
- **Benchmarks:** Terminal-Bench 4.0 70.6% (Sonnet 5 was 10.3% — 6.9× jump); CursorBench 55.5%; GDPval-AA 1,844 Elo; OSWorld 2.1 80.1%
- **Speed:** 30%+ faster output; per-task cost 30% lower (fewer tokens/tool calls per task at same token prices)
- **Pricing:** $2/$10 input/output; $0.20 cache reads (matches Opus 5.5 cache parity); $2.50 cache writes; 512-token cache minimum (down from 1,024)
- **Haiku 5.5** announced "in coming weeks"; completes 5.5 family
- **CC v2.1.284** (Sep 28): Sonnet 5.5 as default Sonnet; `sonnet` alias resolves to 5.5
- **Copilot:** Sonnet 5.5 available to all Pro/Pro+/Max/Business/Enterprise on Sep 28 (gradual rollout); matches Sonnet 5 on coding while using "significantly fewer steps, tokens, and tool calls"
- **claude.ai free tier** now on Sonnet 5.5 (vs ChatGPT free on Luna 5.6)
- **5 breaking API changes** — must update harness code, not just model IDs:
  1. `thinking: {type: "disabled"}` → must use `between_tools` (low/medium/high effort only)
  2. `tool_choice: any/tool` → 400 error; use auto + strict: true per tool
  3. Thinking blocks account-bound — cross-account use silently discarded (no error)
  4. `computer_20251124` toolset rejected; migrate to `computer_toolset_20260801`
  5. Advisor restrictions: only Opus 5/5.5, Sonnet 5.5, Fable/Mythos 5.x qualify
- **Cyber safeguards:** same level as Opus 5.5; first Sonnet with distillation-prevention classifiers
- Simon Willison: at max effort, 128k tokens ($1.28) before budget exhaustion; xhigh more practical ($0.0574, 41s)
- 🇯🇵 Qiita @picnic: "思考ブロックはクロスアカウントでサイレントに無効化される" ("Thinking blocks are silently invalidated cross-account") — migration risk beyond just breaking changes; [source](https://qiita.com/picnic/items/874ab4adee5e33f34bd6)
- 🇯🇵 labmemo.com: "Terminal-Bench 4.0で70.6%を達成し、Opus 5.5の66.4%を上回る驚異的な数値" ("A remarkable figure surpassing Opus 5.5") — [source](https://labmemo.com/claude-sonnet-5-5-announcement-benchmarks-breaking-changes-2026-09/)
- 🇨🇳 CN community framing: "半价追平Opus 5.5" ("half price, matches Opus") — CN developer reaction focused on cost-performance ratio; third-party routes (Felo Search) providing access; [Sohu source](https://www.sohu.com/a/1082094341_120824542)
- **Sources:** https://www.anthropic.com/claude-sonnet-5-5, https://techcrunch.com/2026/09/28/anthropic-releases-sonnet-5-5-which-it-calls-a-significantly-cheaper-faster-work-partner/, https://simonwillison.net/2026/Sep/28/claude-sonnet-5-5/, https://www.developersdigest.tech/blog/claude-sonnet-5-5-release-guide-2026, https://github.blog/changelog/2026-09-28-claude-sonnet-5-5-in-github-copilot/, https://news.ycombinator.com/item?id=49881850

---

### 2. [new] Salesforce Trusted Enterprise AI Harness (Sep 10): 6-capability governance layer for multi-platform agent fleets 🌐

**Claim:** Salesforce announced Trusted Enterprise AI Harness at Dreamforce Sep 10 — a unified governance layer over Salesforce + third-party agents (enterprises average 3 platforms); 6 capabilities; AI Control Plane; FY28 (Feb 2027) rollout.
**Evidence:**
- **6 capabilities:** Trusted Context, Trusted Agency, Trusted Action, Trusted Governance, Trusted Security, Trusted Models
- **Trusted Context:** integrates customer records and real-time signals; data lineage tool; data quality controls
- **Trusted Models:** intelligent model routing across multiple LLMs to optimize cost
- **AI Control Plane:** discover, register, govern, observe, and cost-control Salesforce AND third-party agents under one roof
- VentureBeat framing: "Companies already run 3 agent platforms — Salesforce's new harness wants to govern all of them"
- Most underlying components already in Salesforce cloud services; full rollout from FY28 (Feb 2027)
- Distinct from coding-agent harnesses: governance layer intended for enterprise CRM/workflow agents, not dev tools
- **Sources:** https://www.salesforce.com/news/stories/enterprise-ai-harness/, https://siliconangle.com/2026/09/10/salesforce-introduces-enterprise-ai-harness-ai-control-plane/, https://venturebeat.com/orchestration/companies-already-run-3-agent-platforms-salesforces-new-enterprise-ai-harness-wants-govern-all-them, https://thelettertwo.com/2026/09/10/salesforce-trusted-enterprise-ai-harness-dreamforce-2026

---

### 3. [new] mvschwarz/openrig: multi-agent harness co-orchestrating Claude Code + Codex (+734 Sep 29 trending) 🌐

**Claim:** openrig (Apache 2.0, 2.2k stars, +734 Sep 29) is a new open-source harness that runs Claude Code and Codex as a persistent, unified team under a single YAML-based RigSpec topology.
**Evidence:**
- YAML RigSpec: declarative agent topology definition; starter configs: first-project, conveyor, product-team
- Terminal UI dashboard: team state, topology graphs, individual agent status
- Persistent sessions: snapshot + restore by name
- Cross-agent messaging: broadcasts between agents
- MCP integration: agents can manage their own topology via MCP tools
- Works with herdr + cmux for multi-agent terminal display
- Node.js 22/24 only; macOS/Linux; Apache 2.0
- Significance: first open-source harness explicitly designed to orchestrate both CC and Codex as co-equal team members
- **Source:** https://github.com/mvschwarz/openrig

---

### 4. [new] vectorize-io/hindsight: #1 GitHub trending, 40.5k stars — agent memory as a category breaks out 🌐

**Claim:** Hindsight (formerly bundled in Hermes, now standalone) hit #1 GitHub trending Sep 26, +4,561 stars on Sep 28 alone, 40.5k total — signals agent memory becoming first-class infrastructure concern distinct from harness itself.
**Evidence:**
- **Architecture:** biomimetic — 4 distinct networks (world facts, experiences, observations, opinions); separates evidence from inference
- **Three operations:** retain() / recall() / reflect() — not a flat vector store
- **Knowledge Pages:** living wiki per agent, reachable over MCP; portable between instances
- **Images/files as first-class** retain content with citation provenance
- Temporal window support for explicit time-range queries
- **19 official integrations** + 2 community: Claude Code, LangGraph, CrewAI, Pydantic AI, Agno, Strands Harness, and more
- Fully Hermes-independent since v0.21.5 (Sep 24 decoupling); available from Vectorize catalog
- Pattern: agent memory is bifurcating from the harness layer — specialized memory infrastructure emerging as separate component
- **Sources:** https://github.com/vectorize-io/hindsight, https://hindsight.vectorize.io/blog/2026/09/18/what-hindsight-learned-this-summer, https://trendshift.io/repositories/15603

---

### 5. [new] reindent/jauvex: voice-first multi-agent harness (Claude + Codex + Grok + Jev) 🌐

**Claim:** jauvex is an open-source desktop harness unifying voice interaction across Claude Code, Codex, Grok, and Jev with a wake-phrase system and in-process MCP server.
**Evidence:**
- Wake phrase ("Hey Jauvex") for hands-free invocation while muted
- In-process MCP server using Agent SDK; models use `mcp__jauvex__message_agent` and `mcp__jauvex__list_agents` tools to address each other
- Board-based task management with voice + text input
- Sessions pinned per project folder; acts as entry point for agent lifecycle management
- Significance: first published harness treating all four major coding agents (CC/Codex/Grok/Jev) as equals in a voice-first interface
- **Source:** https://github.com/reindent/jauvex

---

### 6. [update] Claude Code v2.1.283-284: /doctor prompt-audit, Sonnet 5.5 default, AGENTS.md 🌐🇯🇵

**Claim:** NEW FACTS — v2.1.283 (Sep 25): `/doctor prompt-audit` for auditing CLAUDE.md and skills; v2.1.284 (Sep 28): Sonnet 5.5 as default Sonnet, `/mcp reconnect all`, dollar-amount spend displays, "Yes but ask again" permission option.
**Evidence:**
- v2.1.283: `/doctor prompt-audit` audits CLAUDE.md files and skills against best practices; MCP tool results can save images; click-to-expand truncated fullscreen messages; plugin validation fixes
- v2.1.284: Sonnet 5.5 as default Sonnet (replaces Sonnet 5); "Yes, but ask again next time" for auto-mode file reads; dollar amount displays in usage/gateway; `/mcp reconnect all` bulk reconnect; extended thinking preservation fix; response stream error fix
- AGENTS.md support since v2.1.277 (built on Claude Code Mods)
- maxEffortLevel managed setting caps effort per provider across all agent runs
- 5-minute WebFetch timeout (fails instead of hanging)
- 🇯🇵 Qiita: "v2.1.284以降が必要、それ未満ではSonnet 5.5が利用不可" — explicit version requirement for Sonnet 5.5
- **Sources:** https://releasebot.io/updates/anthropic/claude-code, https://code.claude.com/docs/en/whats-new, https://www.gradually.ai/en/changelogs/claude-code/

---

### 7. [update] paperclipai/paperclip v2026.916.1 (Sep 21): AgentMail, multi-harness adapters, Connections 🌐

**Claim:** NEW FACTS — v2026.916.1 (Sep 21): Connections feature (credential governance), AgentMail (agents get email addresses), experimental Slack/Discord/Teams connectors; +3,197 stars trending Sep 29.
**Evidence:**
- **Connections:** AI runtime credentials under same grants + permission boundaries as all other accounts; no secrets in model context
- **AgentMail:** each agent gets its own email address for async communication
- Experimental chat connectors: Slack, Discord, Telegram, Microsoft Teams → tasks
- Built-in adapters for CC, Codex, Gemini CLI, Cursor, Pi, OpenCode, OpenClaw; @paperclipai/mcp-server
- Task checkout + budget enforcement atomic; hard-stop pauses agent + cancels queued work
- Multi-org isolation: one deployment, many companies, separate audit trails
- **Sources:** https://github.com/paperclipai/paperclip, https://paperclip.ing/, https://github.com/paperclipai/paperclip/releases/tag/v2026.916.0

---

### 8. [update] Claude Opus 5.5 harness context: Sonnet 5.5 outperforms it on agentic coding — harness cost model shifts 🌐

**Claim:** NEW FACT — Sonnet 5.5's Terminal-Bench 70.6% (vs Opus 5.5's 66.4%) fundamentally changes the harness cost model: default model for coding tasks should now be Sonnet 5.5, not Opus 5.5.
**Evidence:**
- Same cache-read cost ($0.20/M) eliminates cache-read pricing advantage of Opus 5.5
- Opus 5.5 still leads on FrontierCode (54.4% vs 46.2%) and HLE (67.7% vs 64.5%) — stronger on breadth/reasoning tasks
- Developers Digest: at high effort, pricing overlap undermines "half-price Opus" narrative; real advantage at medium effort
- Harness recommendation: Sonnet 5.5 as default executor; Opus 5.5 for advisor/reviewer roles (where reasoning breadth matters more than agentic coding speed)
- **Sources:** https://www.anthropic.com/claude-sonnet-5-5, https://www.developersdigest.tech/blog/claude-sonnet-5-5-release-guide-2026

---

### 9. [update] Cursor Sep 23: +7% token efficiency, Rollouts Bot + Security Review Bot 🌐

**Claim:** NEW FACT — Sep 23 also added "Improved Token Efficiency for Longer Agent Runs": 7% token reduction via trimmed system prompts, dynamic tool loading, enhanced cache reuse, compressed file reads, optimized subagent behavior. (Rollouts + Security Review bots were already in prior briefing.)
**Evidence:**
- 7% reduction maintains quality; approach: trimmed system prompts + dynamic tool loading + enhanced cache reuse + compressed file reads
- Rollouts Bot: PR-to-production health monitoring (per prior run)
- Security Review Bot: per-PR exploitable bug detection (per prior run)
- Teams/Enterprise only for both bots
- **Source:** https://releasebot.io/updates/cursor, https://cursor.com/changelog

---

### 10. [update] OpenClaw 2.0 (v2026.8.1): 16k PRs, multiplayer cloud sessions, rebuilt UI 🌐

**Claim:** NEW FACTS — OpenClaw 2.0 (v2026.8.1, Aug 31, shipped ~1 week before Sep 25 run but not captured): 16k+ PRs, 933 contributors, multiplayer shared agent sessions, rebuilt chat-centric UI, 575ms startup.
**Evidence:**
- Multiplayer: shared cloud sessions; colleagues join ongoing agent tasks mid-run with full context retained
- Rebuilt UI: files/Git diffs/PRs/browser/terminal panels around the chat (not separate dashboard)
- Startup: 575ms (from 1.6s); initial JS requests 45 (from 140)
- Security hardened: request-specific approvals; argument-level command scoping; Docker/Podman sandboxing; role-enforced execution; team-scoped credentials (secrets never in model context)
- Auto-detects existing Claude/ChatGPT subscriptions, API keys, local Ollama models on first run
- Narrows security gap vs Hermes while maintaining ecosystem breadth advantage
- Latest patch v2026.9.6 (Sep 24): macOS Swift concurrency crash fix (per prior run, carries forward)
- **Sources:** https://decrypt.co/377135/openclaw-2-0-is-here-whats-new, https://www.infoq.com/news/2026/09/openclaw-2-release/

---

**Still true** (ongoing threads, no new facts Sep 25-29):
- **google-ax-agentic-runtime**: 11.2k+ stars; no new release; HN #1 (179pts) ongoing discussion
- **sep-2640-mcp-skills-final**: still 2/572 servers implementing; SDK PRs awaiting review; claudemarketplace.net new domain shows 4,537 skills/948 servers (vs claudemarketplaces.com 23,600+ — may be different marketplace)
- **obra-superpowers-skills**: on Claude marketplace; ongoing development
- **univer-office-harness**: +1,099 Sep 29 trending; ongoing 🇨🇳
- **cursor-router-workspace-plugins**: Projects beta; Rollouts/Security bots (see finding #9); ongoing
- **hermes-agent-self-improving**: v0.21.5 ongoing; no v0.22.0 yet; Hindsight fully decoupled
- **gitspawn-class-vulnerability**: 4 flaws still unpatched across ecosystem; AIR Security ongoing
- **harness-context-tax-problem**: Sonnet 5.5 further lowers cost (see finding #8)
- **harness-engineering-paradigm**: Software Design Oct 2026 JP magazine devotes feature to harness design; paradigm normalizing 🇯🇵
- **layered-oss-stack-over-single-framework**: memory layer (Hindsight) now also splitting out (see finding #4)
- **anthropic-managed-agents-mcp-tunnels**: self-hosted sandboxes in beta (May 19), MCP tunnels in research preview; ongoing
- **aws-strands-harness**: covered in JP press Sep 29; no new code release found; ongoing 🇯🇵
- **claude-code-projects-parallel-threads**: Projects beta ongoing
- **claude-code-mods-function-hooks**: AGENTS.md now built on Mods (v2.1.277+); ongoing
- **copilot-runtime-rust-rewrite**: Sonnet 5.5 added to Copilot Sep 28; ongoing
- **openai-agents-api-beta**: Codex v0.156.0 Sep 23 patch; ongoing
- **vscode-1138-dev-container-agents**: 1.138 ongoing
- **codex-cli-0155-voice-touchid**: v0.156.0 patch Sep 23; ongoing
- **cursor-projects-self-hosted-machines**: ongoing
- **reinventing-ai-employee-packages**: ongoing
- **builder-agent-native**: ongoing
- **beam-cli-harness-observer**: complete guide updated Sep 14; ongoing
- **meta-muse-code**: Muse Code out of beta Sep 1 (inter-session messaging, multi-agent workflows, SDK preview); ongoing
- **agensi-skill-marketplace**: 70/30 split; ongoing
- **kilo-code-anaconda**: ongoing
- **harness-io-agent-ready-scm**: ongoing
- **extension-economy-explosion**: ongoing
- **addy-osmani-agent-skills**: ongoing
- **orca-ade-parallel-fleet**: ongoing
- **ponytail-laziest-dev-skill**: ongoing
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
- **codex-open-platform-harness**: ongoing
- **flue-2-react-hooks-harness**: ongoing
- **hax-c-minimalist-agent**: ongoing
- **copilot-autofix-dual-ai-security**: ongoing
- **bullet-yc-s26-coding-agent**: ongoing
- **book-to-skill-pdf-to-skill**: ongoing
- **cursor-origin-code-hosting**: ongoing
- **deepseek-harness-v01**: no new release; ~235k stars; ongoing 🇨🇳
- **prime-agent-rlm**: ongoing
- **aq-multiplayer-harness**: ongoing
- **qwen-code-alibaba**: ongoing
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
- **skills-security-prompt-injection-36pct**: ongoing
- **claude-tag-slack-agent**: ongoing
- **mimo-code-xiaomi**: ongoing 🇨🇳
- **ecc-cross-harness-os**: ~266k stars; ongoing
- **kimi-code-moonshot**: ongoing 🇨🇳
- **runtime-yc-p26**: ongoing
- **noclick-always-on**: ongoing
- **nyx-offensive-testing**: ongoing
- **agentguard-security-tool**: ongoing
- **mcp-security-nsa-supply-chain**: ongoing
- **yc-qm-multiplayer-harness**: ongoing
- **jadepuffer-agentic-security**: ongoing
- **grok-build-xai-rust-harness**: ongoing
- **self-harness-auto-optimization**: ongoing
- **openharness-hkuds**: ongoing
- **antigravity-gemini-cli-successor**: Sonnet 5.5 now in Gemini's antigravity-preview-09-2026 harness; ongoing
- **claw-code-claude-rewrite**: ongoing 🇨🇳
- **metaharness-scaffold-generator**: ongoing
- **deerflow-superagent-harness**: ongoing 🇨🇳
- **omnigent-meta-harness**: ongoing
- **zot-go-coding-harness**: ongoing
- **omp-omo-pi-derivatives**: ongoing
- **yorishiro-presence-harness**: ongoing
- **agentskills-open-standard**: ongoing
- **letta-agent-file-format**: ongoing
- **macos-harness-proving-ground**: no new incidents; ongoing
- **ahe-automated-harness-evolution**: ongoing
- **harness-internal-external-disambiguation**: 🇯🇵 ongoing
- **environment-architect-new-role**: 🇯🇵 ongoing; Software Design Oct 2026 feature on harness design normalizes the role
- **warp-oz-multi-harness**: ongoing
- **mozilla-otari-llm-gateway**: ongoing
- **statewright-guardrails**: ongoing
- **headroom-token-compression**: ongoing
- **pi-minimal-agent-harness**: ongoing
- **nvidia-skillspector-security**: ongoing
- **cli-anything-hkuds**: ongoing
- **forge-acp-universal-cli**: ongoing
- **github-copilot-skills-mcp-ga**: Sonnet 5.5 added Sep 28 (see finding #1)
- **block-buzz-workspace**: ongoing
- **zcode-zhihu-agent-ide**: ongoing 🇨🇳
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
- **skills-over-mcp-wg-sep2640**: ongoing
- **accuknox-agentz-enterprise**: ongoing
- **gstack-virtual-engineering-team**: ongoing
- **graphify-codebase-knowledge-graph**: ongoing
- **atlas-source-control-agents**: ongoing
- **nodeterm-canvas-terminal-manager**: ongoing
- **paseo-multi-provider-orchestration**: ongoing
- **openchamber-ade-opencode**: ongoing
- **magnitude-local-inference-server**: ongoing
- **opencode-v2-rewrite**: ongoing
- **context-mode-tool-output-compression**: ongoing
- **openclaude-community-agent**: ongoing
- **ruflo-meta-harness-swarm**: ongoing
- **vscode-1137-agent-host-protocol**: ongoing
- **air-security-agent-firewall**: ongoing
- **watcher-apolloresearch-monitoring**: ongoing
- **harness-enterprise-governance-gap**: ongoing
- **claude-managed-agents-auto-permission**: Sonnet 5.5 in Claude Managed Agents; ongoing
- **harnessx-composable-foundry**: ongoing
- **tencentdb-agent-memory**: ongoing 🇨🇳
- **penguinharness-self-improving**: ongoing
- **cloudflare-os-kitesurf**: ongoing
- **ante-antigma-single-binary**: ongoing
- **deepseek-harness-team**: ongoing 🇨🇳
- **gpt6-astra-provider-adapter-harness**: GPT-6 Astra now trails both Opus 5.5 and Sonnet 5.5 on Terminal-Bench; ongoing
- **hkuds-nanobot-personal-agent**: ongoing
- **claude-opus-5-5**: now trails Sonnet 5.5 on Terminal-Bench 4.0 (66.4% vs 70.6%); ongoing

---

## Cross-Source Patterns

**1. Sonnet 5.5 inverts the model hierarchy for coding agents (🌐🇯🇵🇨🇳)**
- Sonnet 5.5 outperforms Opus 5.5 specifically on agentic coding (Terminal-Bench 70.6% vs 66.4%) while costing half as much
- JP community: surprise at benchmark inversion — "価格据え置き、GPT-6 Astra超え"; harness code update urgency (5 breaking changes, silent failures)
- CN community: "半价追平Opus 5.5" framing; focused on third-party access routes
- HN (855pts): community consensus forming that newer Sonnet is better-suited than Opus for agent loops; Opus reserved for breadth/reasoning tasks
- Platforms: Anthropic blog, TechCrunch, Simon Willison, Qiita, labmemo, Sohu, QQ news, HN, GitHub Copilot Changelog

**2. Agent memory bifurcating from the harness layer (🌐)**
- Hindsight: +4,561 stars Sep 28, #1 GitHub trending — biomimetic memory now independent of any single harness (19 integrations)
- Pattern: memory layer emerging as a distinct infrastructure component alongside runtime (Google AX), harness (CC/OC/Hermes), skills (obra/gstack)
- openrig (new) treats Claude Code + Codex as orchestrable peers, not competitors — harness level above individual tools is the new design space
- Platforms: GitHub Trending (agents-radar), Zenn, Hindsight blog

**3. Enterprise governance layer arriving (🌐)**
- Salesforce Enterprise AI Harness (Sep 10): first major enterprise CRM vendor offering cross-platform agent governance with AI Control Plane
- Paperclip meta-harness (v2026.916.1): Connections feature + AgentMail = enterprise-grade agent identity/credential management
- Pattern: governance (who can run which agent with what tools on what data) is the next harness battleground after capability
- Platforms: Salesforce, SiliconANGLE, VentureBeat, GitHub (paperclip)

**4. JP harness engineering discipline formalizing (🇯🇵)**
- Software Design Oct 2026 (major JP dev magazine) devotes full feature to harness design
- Harness Engineering Meetup Tokyo #1 drew 1,700 attendees; AWS sample-long-running-app-harness published as canonical reference pattern
- JP advice crystallizing: avoid single-framework lock-in; verify repo health before dependency; invest in durable concepts (state management, idempotency, A2A, MCP), not specific frameworks
- Platforms: Zenn, Qiita, ITmedia, prtimes

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (via search) | Sonnet 5.5 | 855 | 585 | "every new generation of model goes and cleans up the slop in my code bases" (drewnick) | https://news.ycombinator.com/item?id=49881850 |
| (prior run) | Google's Open Agentic Orchestrator (AX) | 179 | 74 | "The agent execution problem is infrastructure, not framework" | https://news.ycombinator.com/item?id=49753878 |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | Anthropic | https://www.anthropic.com/claude-sonnet-5-5 | Sonnet 5.5: benchmarks, pricing, 5 breaking changes |
| 🌐 | TechCrunch | https://techcrunch.com/2026/09/28/anthropic-releases-sonnet-5-5-which-it-calls-a-significantly-cheaper-faster-work-partner/ | Sonnet 5.5 launch coverage |
| 🌐 | Simon Willison | https://simonwillison.net/2026/Sep/28/claude-sonnet-5-5/ | Token budget exhaustion at max effort; practical effort guidance |
| 🌐 | Developers Digest | https://www.developersdigest.tech/blog/claude-sonnet-5-5-release-guide-2026 | Full benchmark table, 5 breaking changes detail |
| 🌐 | GitHub Copilot | https://github.blog/changelog/2026-09-28-claude-sonnet-5-5-in-github-copilot/ | Sonnet 5.5 availability in Copilot Sep 28 |
| 🌐 | HN | https://news.ycombinator.com/item?id=49881850 | 855 pts, 585 comments; community reaction |
| 🌐 | Releasebot CC | https://releasebot.io/updates/anthropic/claude-code | v2.1.283-284 changelogs |
| 🌐 | Claude Code Docs | https://code.claude.com/docs/en/whats-new | Official changelog; AGENTS.md support |
| 🌐 | Gradually.ai | https://www.gradually.ai/en/changelogs/claude-code/ | Structured changelog Sep 2026 |
| 🌐 | Anthropic | https://claude.com/blog/claude-managed-agents-updates | Managed Agents: self-hosted sandboxes + MCP tunnels |
| 🌐 | Claude Platform Docs | https://platform.claude.com/docs/en/managed-agents/overview | Managed Agents overview |
| 🌐 | Decrypt | https://decrypt.co/377135/openclaw-2-0-is-here-whats-new | OpenClaw 2.0: multiplayer, rebuilt UI, 16k PRs |
| 🌐 | InfoQ | https://www.infoq.com/news/2026/09/openclaw-2-release/ | OpenClaw 2.0 analysis |
| 🌐 | Releasebot OC | https://releasebot.io/updates/openclaw | OC release history Sep 2026 |
| 🌐 | Releasebot Cursor | https://releasebot.io/updates/cursor | Cursor Sep 23: +7% token efficiency, bots |
| 🌐 | cursor.com | https://cursor.com/changelog | Cursor official changelog |
| 🌐 | GitHub (openrig) | https://github.com/mvschwarz/openrig | openrig: CC+Codex unified harness |
| 🌐 | GitHub (hindsight) | https://github.com/vectorize-io/hindsight | Hindsight: 40.5k stars, #1 trending |
| 🌐 | Hindsight blog | https://hindsight.vectorize.io/blog/2026/09/18/what-hindsight-learned-this-summer | What Hindsight Learned This Summer |
| 🌐 | Trendshift | https://trendshift.io/repositories/15603 | Hindsight star history |
| 🌐 | GitHub (jauvex) | https://github.com/reindent/jauvex | jauvex: voice CC+Codex+Grok+Jev |
| 🌐 | GitHub (paperclip) | https://github.com/paperclipai/paperclip | paperclip v2026.916.1; AgentMail |
| 🌐 | Paperclip | https://paperclip.ing/ | Paperclip official site |
| 🌐 | Salesforce | https://www.salesforce.com/news/stories/enterprise-ai-harness/ | Enterprise AI Harness announcement |
| 🌐 | SiliconANGLE | https://siliconangle.com/2026/09/10/salesforce-introduces-enterprise-ai-harness-ai-control-plane/ | AI Control Plane details |
| 🌐 | VentureBeat | https://venturebeat.com/orchestration/companies-already-run-3-agent-platforms-salesforces-new-enterprise-ai-harness-wants-govern-all-them | Multi-platform governance framing |
| 🌐 | agents-radar #250 | https://github.com/kouweizhu/agents-radar/issues/250 | Sep 29 trending: hindsight +4,561, paperclip +3,197 |
| 🌐 | agents-radar #249 | https://github.com/kouweizhu/agents-radar/issues/249 | Sep 28 trending digest |
| 🌐 | RyanAlberts catalog | https://github.com/RyanAlberts/best-of-Agent-Harnesses/releases/tag/list-2026-09-2 | 167 harnesses; Prime Agent, QM, OpenJarvis added |
| 🌐 | HN HarnessTax | https://news.ycombinator.com/item?id=49733726 | Harness design = primary outcome differentiator |
| 🌐 | Firecrawl blog | https://www.firecrawl.dev/blog/best-ai-coding-agents | Claude Code deepest harness (30 lifecycle hooks) |
| 🌐 | Arena.ai | https://arena.ai/blog/coding-agents-harness-tax | Harness vs model variance analysis |
| 🌐 | ext-skills | https://github.com/modelcontextprotocol/ext-skills | SEP-2640 reference impl (ongoing) |
| 🌐 | Cursor Marketplace | https://cursor.com/marketplace | MCP one-click install (Sep 25 documentation) |
| 🇯🇵 | Qiita (picnic) | https://qiita.com/picnic/items/874ab4adee5e33f34bd6 | Sonnet 5.5: 5 breaking changes; silent failure risk |
| 🇯🇵 | labmemo.com | https://labmemo.com/claude-sonnet-5-5-announcement-benchmarks-breaking-changes-2026-09/ | Terminal-Bench 70.6% analysis; budget_tokens deprecated |
| 🇯🇵 | note.com | https://note.com/yasuhitoo/n/nc745c7a7ee73 | Sonnet 5.5 timing vs OpenAI DevDay framing |
| 🇯🇵 | ai-jitan-hub | https://www.ai-jitan-hub.com/news/claude-sonnet-5-5-release | "価格据え置き、GPT-6 Astra超え" |
| 🇯🇵 | ITmedia | https://www.itmedia.co.jp/news/article/2609/29/2000001837/ | AWS Strands Harness open-source coverage |
| 🇯🇵 | Publickey | https://www.publickey1.jp/blog/26/awsaistrandsllm.html | Strands Harness architecture |
| 🇯🇵 | Zenn (aiwatch_jp) | https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained | 17-layer OSS harness assembly; repo health checks |
| 🇯🇵 | Zenn (naomine) | https://zenn.dev/naomine_egawa/articles/harness-engineering-meetup-and-agent-harness | Harness Engineering Meetup Tokyo #1 |
| 🇯🇵 | Zenn (atsukish) | https://zenn.dev/atsukish/articles/e080ae2847540d | MCP=tools, Skills=wisdom (ongoing) |
| 🇯🇵 | Qiita (ennagara128) | https://qiita.com/ennagara128/items/f09e622a5069f34b89c5 | Sep 29 Qiita trending: Sonnet 5.5 dominates |
| 🇨🇳 | Sohu | https://www.sohu.com/a/1082094341_120824542 | "半价追平Opus 5.5" CN framing |
| 🇨🇳 | 163.com | https://www.163.com/dy/article/L804DI7F0511AQHO.html | CN mainstream Sonnet 5.5 coverage |
| 🇨🇳 | QQ news | https://news.qq.com/rain/a/20260929A02VVA00 | Sonnet 5.5 performance/pricing |
| 🇨🇳 | CNBlogs | https://www.cnblogs.com/vibecodinghuanzhe/p/23151727 | Sonnet 5.5 "thinking mechanism evolved" framing |
| 🇨🇳 | CSDN | https://blog.csdn.net/python_yjys/article/details/166642416 | 1M context; Terminal-Bench 70.6% practical guide |
| 🇨🇳 | DataLearner | https://www.datalearner.com/ai-models/pretrained-models/claude-sonnet-5-5 | CN ML community spec comparison |
| 🇨🇳 | Felo | https://felo.ai/zh-Hans/blog/claude-sonnet-5-5-in-felo-search/ | Sonnet 5.5 access route for CN developers |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads (excluded per protocol)
├─ 🔵 X: 0 posts (excluded per protocol)
├─ 🔴 YouTube: 0 videos
├─ 🟢 HN: 2 stories │ 1,034 pts │ 659 comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts (no harness-specific posts found in free search; bluesky=OK per health check)
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: ~40 pages │ 🇯🇵 11 │ 🇨🇳 10
└─ 🗣️ Top voices: @simonwillison (Willison Weblog), @picnic (Qiita), @aiwatch_jp (Zenn), @yasuhitoo (note), @naomine_egawa (Zenn)
```

---

## Out of Scope but Notable

- **Anthropic IPO prospectus filed** — referenced in HN Sonnet 5.5 thread; not harness-specific but signals Anthropic entering commercialization phase that will affect harness pricing, SLAs, and enterprise feature roadmap. Belongs under a business/strategy topic.
- **Google RRSI** (mentioned in HN digest Sep 29): "framework for safe, iterative agent self-improvement" from Google Research — may overlap with AutoHarness/self-optimizing harness threads but framing is safety-first self-improvement, not harness engineering per se. Possible paradigm-watch item.
- **Jauvex YouTube video** (https://www.youtube.com/watch?v=yNiQTV_Be0c): voice harness demo; included as thread in this run but the YouTube surface itself wasn't searched.
- **JP MCP 2.0 book** (Sep 24): first JP commercial book on MCP agent infrastructure — sign that MCP/harness engineering is reaching mass-market technical publishing stage in Japan.

---

## Data Gaps

- **/last30days skill**: unavailable (unknown skill error); replaced with full direct WebSearch + WebFetch sweep
- **Reddit/X/Twitter**: excluded per protocol
- **Bluesky**: SOURCE HEALTH bluesky=OK; search returned zero harness-specific posts (likely requires authenticated Bluesky search)
- **YouTube/TikTok/Instagram**: not searched
- **Polymarket**: no harness-specific markets
- **HN direct fetch**: rate-limited for some threads; engagement numbers from search snippets
- **DuckDuckGo HTML endpoint**: CAPTCHA on both JP and CN queries; fallback to native WebSearch worked
- **Zhihu direct fetch**: HTTP 403 on most article pages; data from search snippets
- **linux.do**: HTTP 403 on fetch
- **Hermes v0.21.5 further updates**: no post-Sep-25 Hermes releases found in this window
- **Codex CLI v0.156.0**: minimal data (diary sweep reference only)
- **Coverage estimate**: ~82% — comprehensive on Sonnet 5.5, CC updates, OpenClaw 2.0, new harnesses (openrig, hindsight, jauvex, paperclip), Salesforce, JP/CN coverage; gaps in Bluesky/YouTube/long-tail HN/Hermes details

---

## Key Quotes

> "Terminal-Bench 4.0で70.6%を達成し、Opus 5.5の66.4%を上回る驚異的な数値" ("Achieving 70.6% on Terminal-Bench 4.0, surpassing Opus 5.5's 66.4% — a remarkable figure") — labmemo.com ([link](https://labmemo.com/claude-sonnet-5-5-announcement-benchmarks-breaking-changes-2026-09/)) 🇯🇵

> "every new generation of model goes and cleans up the slop...in my code bases, and it has turned out to be quite effective." — drewnick, HN Sonnet 5.5 thread ([link](https://news.ycombinator.com/item?id=49881850)) 🌐

> "Companies already run 3 agent platforms. Salesforce's new Enterprise AI Harness wants to govern all of them." — VentureBeat headline ([link](https://venturebeat.com/orchestration/companies-already-run-3-agent-platforms-salesforces-new-enterprise-ai-harness-wants-govern-all-them)) 🌐

> "半価追平Opus 5.5" ("Half price, matches Opus 5.5") — CN community framing for Sonnet 5.5 on Sohu/163.com 🇨🇳

> "思考ブロックはクロスアカウントでサイレントに無効化される" ("Thinking blocks are silently invalidated cross-account") — Qiita @picnic, on the most dangerous migration footgun in Sonnet 5.5 ([link](https://qiita.com/picnic/items/874ab4adee5e33f34bd6)) 🇯🇵

> "runs 30%+ faster, and costs up to 30% less for most work" — Simon Willison on Sonnet 5.5 ([link](https://simonwillison.net/2026/Sep/28/claude-sonnet-5-5/)) 🌐

> "Avoid deep dependencies on specific managed services, particular frameworks (ADK, LangGraph, CrewAI), or model-specific API optimization" — Harness Engineering Meetup Tokyo #1 recommendation ([link](https://zenn.dev/naomine_egawa/articles/harness-engineering-meetup-and-agent-harness)) 🇯🇵

> "Before following summary article links, run `gh api repos/<owner>/<repo>` to verify final push dates and migration status." — Zenn aiwatch_jp, on 17-layer OSS harness health ([link](https://zenn.dev/aiwatch_jp/articles/agent-harness-oss-2026-maintained)) 🇯🇵
