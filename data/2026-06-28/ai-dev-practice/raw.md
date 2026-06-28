# AI Dev Practice — Raw Research Output
**Date:** 2026-06-28
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks
**Engine:** last30days v3.8.3
**Date range:** 2026-05-29 to 2026-06-28

## Engine Run Notes

The engine ran in comparison mode because "vs" was detected in the phrase "what works vs what breaks," splitting the query into two entities:
- Main entity: `vibe coding AI-assisted development Cursor Windsurf GitHub Copilot...LLMs`
- Peer entity: `what breaks` (returned irrelevant content — ignored in synthesis)

Full engine raw files:
- `vibe-coding-ai-assisted-development-cursor-windsurf-github-copilot-agent-mode-ai-pair-programming-prompt-driven-development-llms-raw.md`
- `what-breaks-raw.md` (peer entity — mostly noise, but GitHub items are relevant: rsync prompt injection controversy, Claude Code parse errors, Codex token cost explosion)

## Source Coverage (main entity)

- Reddit: 3 threads (r/vibecoding)
- X/Twitter: 19 posts | 549 likes | 31 reposts
- Hacker News: 16 stories | 402 points | 241 comments
- Bluesky: 7 posts | 29 likes | 4 reposts
- GitHub: 5 items (main) + 5 relevant items from peer entity
- Web: 10 pages (engine grounding)
- YouTube: 0 videos (yt-dlp rate-limited; ScrapeCreators HTTP 402)
- TikTok: 0 (ScrapeCreators HTTP 402)
- Instagram: 0 (ScrapeCreators HTTP 402)

---

## Key Evidence Clusters

### Vibe coding identity debate / spectrum
- @Dhruvam987 (186 likes, 64 replies): "Why do most vibe coding success stories involve web apps? You rarely see people vibe coding database engines, Linux kernels, compilers, distributed systems."
  URL: https://x.com/Dhruvam987/status/2069628513389613348
- @TheBronzOwl (reply): "Vibe coding works well for apps, dashboards, wrappers, and SaaS because failures are usually visible and easier to iterate on. Systems work punishes shallow understanding much faster."
  URL: https://x.com/TheBronzOwl/status/2070865531972764036
- @MatthewParrott (5 likes): "The word 'vibe code' precludes knowing what you're doing. Vibe coding while knowing what's going on is just AI-assisted development."
  URL: https://x.com/MatthewParrott/status/2068984651637494104
- @symonbaikov.bsky.social (Bluesky, 2 likes): "AI-assisted coding is fine when the human owns architecture and review. It becomes vibe coding when the model owns the decisions and you only inspect the demo."
  URL: https://bsky.app/profile/symonbaikov.bsky.social/post/3mnw3p5fudg2c
- @symonbaikov.bsky.social (2 likes): "For professional work the useful split is simpler: reviewed vs unreviewed. If nobody understands the diff, it's vibe coding regardless of tool."
  URL: https://bsky.app/profile/symonbaikov.bsky.social/post/3mnwcjdxyrp2c
- NCSC (UK gov cybersecurity agency) published "vibe coding spectrum" safety guidance
  URL: https://bsky.app/profile/ncsc.gov.uk/post/3moqdkwxnef22 → https://www.ncsc.gov.uk/blogs/the-vibe-coding-spectrum-approach-to-ai-assisted-software-development
- HN: "Vibe Coding Is Not Engineering" (46pts, 71 comments)
  URL: https://phroneses.com/articles/build/notes/vibe-coding-is-not-engineering.html
- Substack: "Vibe Coding in 2026: The Real Definition + Full AI Development Lexicon" (Jun 26)
  URL: https://karozieminski.substack.com/p/vibe-coding-2026-definition-ai-development-lexicon
- HN: "Is Vibe Coding Dead? Even Karpathy Is Moving On" (Forbes, 5pts)
  URL: https://www.forbes.com/sites/jodiecook/2026/06/12/is-vibe-coding-already-dead-even-karpathy-is-moving-on/
- HN: "The AI vibe shift is real: Why the backlash is growing" (Mashable, 3pts)
  URL: https://mashable.com/tech/ai-backlash-vibe-shift

### What breaks / AI coding failure modes
- @TaoYifu (3 likes): "Vibe coding breaks when the repo starts forgetting. Every AI coding agent rebuilds context, rediscovers old decisions, and repeats the same mistakes. That is the hidden tax of AI-assisted development."
  URL: https://x.com/TaoYifu/status/2068984817551622476
- GitHub RsyncProject/rsync: "Please Do Not Vibe Fuck Up This Software" (2,932 reactions, 347 comments)
  URL: https://github.com/RsyncProject/rsync/issues/929
- GitHub RsyncProject/rsync: "Remove all LLM generated commits before people get hurt by this nonsense." (256 reactions, 40 comments)
  URL: https://github.com/RsyncProject/rsync/issues/934
- HN: "'Please do not vibe f–- up this software': Broken backups spark AI coding row" (3pts)
  URL: https://www.theregister.com/ai-and-ml/2026/06/04/please-do-not-vibe-f-up-this-software-broken-backups-spark-ai-coding-row-in-rsync-project/5251189
- HN: "Undisclosed addition in jqwik instructed AI coding agents to delete app output" (67pts)
  URL: https://arstechnica.com/security/2026/05/fed-up-with-vibe-coders-dev-sneaks-data-nuking-prompt-injection-into-their-code/
  GitHub issue (jqwik NoAI / prompt injection): https://github.com/jqwik-team/jqwik/issues/713
- GitHub Claude Code parse error: "The model's tool call could not be parsed (retry also failed)" (110 reactions, 71 comments)
  URL: https://github.com/anthropics/claude-code/issues/63875
- GitHub OpenAI Codex: "rate-limit cost per token jumped ~10-20x since June 16, draining the 5h budget in 2-3 prompts" (522 reactions, 186 comments)
  URL: https://github.com/openai/codex/issues/28879
- HN: "GitHub Is Becoming a Giant AI Code Dump" (24pts, 24 comments)
  URL: https://maref.cc/en/blog/vibe-coding-crisis/
- @commencis: "risks of AI-assisted development, from vibe coding and AI slop to knowledge debt and misleading test coverage"
  URL: https://x.com/commencis/status/2069746816510308489
- HN: "Show HN: Fata – Spaced repetition to fight skill rot from AI coding" (124pts, 53 comments)
  URL: https://fata.dev
- @plinth_games (4 likes): "I often feel like I do not belong here, that I am unworthy primarily because I lean on AI tooling, LLMs, vibe coding, and AI assisted development."
  URL: https://x.com/plinth_games/status/2070329955263918331

### AI coding tools landscape (major industry shifts)
- Windsurf → Devin Desktop rebrand (June 2, 2026 by Cognition)
  @therobertta_: "Cognition just killed the Cursor competitor Windsurf and renamed it Devin Desktop." 
  URL: https://x.com/therobertta_/status/2071127206533984627
  @_markfenner: "Since Windsurf became Devin Desktop, the default screen isn't a file, it's an Agent Command Center."
  URL: https://x.com/_markfenner/status/2067668457269702972
  @adidogCEO: "following up on this for anyone else looking to move off copilot after the retarded price changes — devin-desktop(prev windsurf) I found to be quite clunky/buggy"
  URL: https://x.com/adidogCEO/status/2066020101418004630
  @laogui Chinese thread on history of Windsurf/Codeium: URL: https://x.com/laogui/status/2062037835226763521
  @CryptoTied Chinese thread on shift to "agent control console": URL: https://x.com/CryptoTied/status/2062171356142436778
- SpaceX acquires Cursor (June 18, 2026) — SpaceX lost $600B market cap
  HN: URL: https://www.forbes.com/sites/tylerroush/2026/06/18/spacex-stock-plunge-wipes-out-600-billion-after-cursor-deal-spooks-investors/
- Cursor announces "Origin" — git hosting competitor to GitHub
  HN: "Cursor, GitLab and Zed agree GitHub is breaking. They disagree on how to rebuild"
  URL: https://thenewstack.io/cursor-origin-github-disruption/
  HN: "Cursor's New GitHub Competitor, Origin" URL: https://twitter.com/morganlinton/status/2066958434805956937
- Cursor auto-review mode launched
  URL: https://cursor.com/changelog/auto-review
- GitHub Copilot → usage-based AI Credits billing (June 1, 2026)
  URL: https://www.agenticwire.news/article/cursor-windsurf-copilot-agents
- @MakeAI_CEO Japanese thread categorizing AI coding tools into 4 categories:
  URL: https://x.com/MakeAI_CEO/status/2069631994846380375
- HN: "Show HN: Command Center, the AI coding env for people who care about quality" (69pts, 32 comments)
  URL: https://www.cc.dev/
- Developers Digest comparison: Cursor vs Devin Desktop 2026
  URL: https://www.developersdigest.tech/blog/cursor-vs-devin-desktop-2026
- ToolNav comparison: URL: https://toolnav.io/compare/cursor-vs-windsurf/
- AgenticWire comparison: URL: https://www.agenticwire.news/article/cursor-windsurf-copilot-agents
- ValueAddVC comparison (Cursor $9B valuation, $500M+ ARR; Copilot 20M+ users): URL: https://valueaddvc.com/blog/cursor-vs-github-copilot-vs-windsurf-which-ai-code-editor-wins-in-2026
- DevToolLab ranking: URL: https://devtoollab.com/blog/best-ai-coding-assistants

### Real-world AI coding applications
- r/vibecoding: "Built an app completely with vibe coding. Now have 7k+ downloads in 1 month."
  URL: https://www.reddit.com/r/vibecoding/comments/1uhobey/built_an_app_completely_with_vibe_coding_now_have/
- r/vibecoding: "Vibe coded website to take you to vibe coded websites"
  URL: https://www.reddit.com/r/vibecoding/comments/1uhr8cx/vibe_coded_website_to_take_you_to_vibe_coded/
- r/vibecoding: "Built with Claude Code: I gave an AI agent its own wallet and blockchain"
  URL: https://www.reddit.com/r/vibecoding/comments/1uhhw2a/built_with_claude_code_i_gave_an_ai_agent_its_own/
- HN: "Bain tests software takeover targets by vibecoding AI replicas" (32pts, 50 comments) — enterprise M&A use case
  URL: https://www.ft.com/content/e5bac4d1-b1f8-43a4-bd54-b182d5357af0
- HN: "Linux developers are using AI vibe coding to keep vintage AMD GPUs alive" (r600 driver cleaned up with GitHub Copilot)
  URL: https://www.tomshardware.com/software/linux/linux-developers-are-using-ai-vibe-coding-to-keep-vintage-amd-gpus-alive-r600-driver-cleaned-up-with-github-copilot-gives-hd-2000-to-hd-6000-series-a-new-lease-of-life
- GitHub "Ship AI batteries" PRs (CLAUDE.md + skills for vibe coding):
  URL: https://github.com/padosoft/laravel-rebel-sessions/pull/3
  URL: https://github.com/padosoft/laravel-rebel-email-otp/pull/2
- GitHub AI engineering learning guide (context engineering, RAG, LangGraph, evaluation):
  URL: https://github.com/domenicodigangi/AIEC1/pull/1
- @f18-dev.bsky.social (4 likes): "Not vibe coding. Senior engineering, AI-assisted. We use LLMs to move faster, not to lower the bar on product quality, maintainability or handover."
  URL: https://bsky.app/profile/f18-dev.bsky.social/post/3mnrrwboogp2f
- @scrapandsprouts.bsky.social (8 likes): "vibe coding completely brought back my spark!"
  URL: https://bsky.app/profile/scrapandsprouts.bsky.social/post/3mnorq3vag22a
- @samtechcoded: "I feel like maybe I am the only dev who has been coding for 20+ years who has adopted AI assisted coding and loves it"
  URL: https://x.com/samtechcoded/status/2068671662086889594
- DDS Vibe Academy – 49 free AI coding classes (HN, 3pts)
  URL: https://ddsboston.com/pages/dds-vibe-academy
- @MaxApexHosting: Oracle APEX 26.1 adds AI-assisted Vibe Coding
  URL: https://x.com/MaxApexHosting/status/2070462073675370794
- @voxy.space (Bluesky, 9 likes): "they indeed have merged PRs with AI disclosures, which are thus AI-assisted or contain LLM-generated code"
  URL: https://bsky.app/profile/voxy.space/post/3mouhu33esk2q
- @oldstackjournal.bsky.social: "Trying to find more WordPress, PHP, LAMP, AI-assisted coding, and vibe coding people. Especially people building practical things, not just posting launch theatre."
  URL: https://bsky.app/profile/oldstackjournal.bsky.social/post/3mpcq5epvnm2v
- @AyahaMio (116 likes): Taiwan AI engineer discussing best AI coding stacks (Dify, Coze, n8n, Flowise, Cursor, Lovable, Replit, Bolt)
  URL: https://x.com/AyahaMio/status/2068548563987206632
- GitHub sleepy-zone daily AI trend report: URL: https://github.com/sleepy-zone/daily-report/issues/160
- GitHub GLM-5 co-authorship feature request: URL: https://github.com/zai-org/GLM-5/issues/75

### Vibe coding guides / definitions
- zoer.ai: "What Is Vibe Coding and How Does It Work?" URL: https://zoer.ai/posts/zoer/what-is-vibe-coding-5223
- tech.grahammiranda.com: "Vibe Coding in 2026: Complete Guide" URL: https://tech.grahammiranda.com/vibe-coding-2026-complete-guide/
- tokenade.net: "What Is Vibe Coding?" URL: https://tokenade.net/en/articles/vibe-coding
- dev.to: "Vibe Coding Guide: How to Build Full-Stack Apps Without Losing Control" URL: https://dev.to/codegeeks_solutions/vibe-coding-guide-how-to-build-full-stack-apps-without-losing-control-57p5
- HN: "Show HN: Appaca – AI Workspace for Operators" (5pts) URL: https://www.appaca.ai/
- @TheCyphere: "The 'vibe coding spectrum' approach to AI-assisted software development"
  URL: https://x.com/TheCyphere/status/2069678146178384008
- @MundoTheGame1: "The difference between vibe coding and AI assisted software development is if you know what you're doing, is the second option."
  URL: https://x.com/MundoTheGame1/status/2070896611580936256

---

## WebSearch Supplemental Results

- **AgenticWire** (agenticwire.news) — "Cursor vs Windsurf vs Copilot: 2026 Coding Agent Guide": Cursor fits teams wanting diff-by-diff control; Devin Desktop for workflow-driven autonomy; Copilot for GitHub-centric orgs now on usage-based AI Credits; Claude Code/Codex for terminal-native teams.
- **VibecodingAcademy** (vibecodingacademy.ai) — Best AI Coding Assistants 2026: Cursor ranked #1 for professional devs (70% reduction in PR review comments reported); Copilot at ~42% market share and enterprise default.
- **LushBinary** (lushbinary.com) — AI Coding Agents 2026 comparison: Claude Code vs Antigravity 2.0 vs Codex vs Cursor vs Kiro vs Copilot vs Windsurf — pricing and features matrix.
- **Trantorinc** (trantorinc.com) — "AI Agent Failure Modes: What Goes Wrong in Production": main LLM failure modes = prompt fragility, retrieval degradation, hallucination, latency, agent safety, guardrails, observability gaps, cost governance.
- **TeacherAndTask** (teacherandtask.com) — "Your RAG Is Lying to You: 7 Failure Modes + 2026 Production Patterns": Naive RAG silently fails under 800-token budget constraints; hybrid search + reranking + GraphRAG + agentic RAG are the 2026 production patterns.
- **ShareUHack** (shareuhack.com) — "Context Engineering Guide 2026: Beyond Prompting": accuracy drops measurably above ~10k tokens in practice despite million-token vendor claims; "lost in the middle" phenomenon persists across model generations.
- **AppScale Blog** (appscale.blog) — "LLM Failure Modes in Production: Complete Root Cause Guide 2026": 85% per-step agent accuracy → only ~20% 10-step workflow success rate; silent failures most dangerous.
- **MachineLearningMastery** (machinelearningmastery.com) — "Mastering LLMOps in 2026": CI gates + production observability running same metrics against live traces is the new baseline for teams shipping AI.
- **Kili Technology** (kili-technology.com) — "AI Benchmarks 2026": traditional benchmarks (MMLU, MMLU-Pro) saturated above 88% for frontier models; 37% gap between lab benchmarks and real-world production performance; annotation error rates above 50% undermine static evaluations.
- **MorphLLM** (morphllm.com) — "AI Agent Evaluation 2026": majority of observability tools trace what happened without evaluating whether it was correct; 2026 is the year teams are forced to invest in evaluation.
- **Confident AI** (confident-ai.com) — "Best LLM Observability Platforms 2026": DeepEval covers 50+ metrics across RAG, agents, multi-turn, MCP, safety; TruLens uses OpenTelemetry-based tracing with per-span evaluation; CI gates prevent regressions before deployment.
