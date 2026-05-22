# AI Dev Practice — Daily Briefing
**Date:** 2026-05-22
**Query type:** GENERAL
**Sources:** Reddit (indirect), Hacker News, YouTube, Web, Stack Overflow Survey

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 2 threads | High engagement (top stories) | Direct thread analysis via fetch |
| YouTube | 7 videos | — | Comparison/tutorial content, views not retrieved |
| Web | 80+ pages | — | Blogs, news, analysis, official docs |
| Stack Overflow Survey | 1 survey | 49,000+ respondents | 2025 survey, 2026 analysis cycle |

---

## Synthesized Findings

### 1. The Vibe Coding Moment: One Year After Karpathy

Andrej Karpathy coined "vibe coding" in February 2025. One year on, it has evolved from meme to methodology — and the community is now reckoning with what that means in production. The term describes prompting AI to generate code rather than writing it manually, and has bifurcated into two camps: **AI Code Editors** (Cursor, Windsurf, Claude Code) for developers who still want control, and **AI App Builders** (Bolt.new, Lovable) for non-developers who want to skip coding entirely.

Adoption numbers are striking: 72% of developers now use AI-powered coding tools daily, and 41% of global code is estimated to be AI-generated. The Stack Overflow Developer Survey (49,000+ respondents) shows 84% use or plan to use AI tools (up from 76% in 2024), with 51% of professionals using them daily.

The community conversation has matured from "does it work?" to "what breaks and why?" DEV Community, daily.dev, and IBM have all published retrospectives framing 2026 as "year two" of vibe coding — moving past the initial enthusiasm into critical assessment.

**Sources:** [Wikipedia: Vibe Coding](https://en.wikipedia.org/wiki/Vibe_coding) | [DEV: One Year from Karpathy's Tweet](https://dev.to/h1gbosn/what-is-vibe-coding-in-2026-one-year-from-karpathys-tweet-5f43) | [IBM: What is Vibe Coding?](https://www.ibm.com/think/topics/vibe-coding) | [daily.dev: Vibe Coding in 2026](https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code/) | [Stack Overflow Survey 2025](https://survey.stackoverflow.co/2025) | [Cadence: SO Survey 2026 Highlights](https://cadence.withremote.ai/blog/stack-overflow-survey-2026)

---

### 2. The AI Coding Tool Wars: Cursor vs Windsurf vs Copilot vs Claude Code

The competitive landscape has consolidated around four serious contenders, all converging on $20/month.

**Cursor** (valued at $29.3B) launched Cursor 3 on April 2, 2026 — described as "the biggest interface overhaul since Anysphere shipped the product in 2023." The move to an agent-first interface (Agents Window, Composer 2, Cursor Cloud) generated a sharply divided reaction on Hacker News and developer forums. A top comment 30 minutes after the announcement: *"I wish they'd keep the old philosophy of letting the developer drive and the agent assist."* May 2026 shipped Security Review beta, cloud agent dev environments with parallel agent support, and Cursor 3.5 on May 20. The Opsera-Cursor partnership and Cursor-Chainguard security partnership were both announced in early May.

**Windsurf** completed a watershed moment: acquired by Cognition AI for ~$250M in December 2025 — the biggest AI dev tools M&A to date. At acquisition it had $82M ARR with enterprise revenue doubling quarter-over-quarter. Google secured a separate licensing deal; OpenAI was also in the bidding. Post-acquisition: Devin AI embedded directly for background agent dispatch, SWE-1.5 model deployed. As of February 2026, Windsurf ranked #1 in the LogRocket AI Dev Tool Power Rankings, and reports 59% of Fortune 500 companies as customers. Pricing moved to $20/month parity with Cursor in March 2026.

**GitHub Copilot** agent mode reached GA in VS Code (March 2026), with JetBrains and Visual Studio still in preview. The cloud-based coding agent turns issues into PRs autonomously. Initialization time cut from ~40s to ~20s. Credit-based pricing is shifting to usage-based in June 2026.

**Claude Code** leads the Pragmatic Engineer survey (906 devs) as most-loved AI coding tool at 46% vs Cursor's 19%. Independent testing shows Claude Code uses 5.5x fewer tokens than Cursor for identical tasks, with stronger performance on complex multi-file autonomous tasks. Many power users run both ("Claude Code on CLI + Cursor as the IDE").

Comparative benchmarks: Cursor's Composer 2 scores 61.7 on Terminal-Bench 2.0 (vs. Opus 4.6 at 58.0, GPT-5.4 at 75.1). In a 5-tool test building the same app, Cursor completed in 2 rounds, Windsurf in 3, Copilot in 5.

**Sources:** [CNBC: Cursor major update Feb 2026](https://www.cnbc.com/2026/02/24/cursor-announces-major-update-as-ai-coding-agent-battle-heats-up.html) | [Cursor Blog: Cursor 3](https://cursor.com/blog/cursor-3) | [InfoQ: Cursor 3 Agent-First](https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/) | [Cognition: Windsurf Acquisition](https://cognition.ai/blog/windsurf) | [NxCode: Windsurf Acquisition](https://www.nxcode.io/resources/news/cognition-windsurf-acquisition-swe-1-5-codemaps-2026) | [Axios: Cursor-Chainguard](https://www.axios.com/2026/04/21/cursor-chainguard-ai-code-security) | [SD Times May 8 2026](https://sdtimes.com/ai/may-8-2026-ai-updates-from-the-past-week-coder-agents-launch-snyk-claude-partnership-opsera-cursor-partnership-and-more/) | [GitHub Copilot Docs](https://docs.github.com/en/copilot/get-started/features) | [NxCode: Copilot Guide 2026](https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents) | [Builder.io: Claude Code vs Cursor](https://www.builder.io/blog/cursor-vs-claude-code) | [DEV: I Built the Same App 5 Ways](https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2) | [Artificial Analysis: Coding Agents](https://artificialanalysis.ai/agents/coding) | [Cursor Changelog](https://cursor.com/changelog) | [Developer-Tech: Cursor Agent Workflows](https://www.developer-tech.com/news/cursorlaunches-agent-based-coding-workflows-amid-ai-agent-growth/) | [Tossitt: Copilot Guide 2026](https://tossitt.com/github-copilot-guide-2026/) | [Verdent: Windsurf vs Cursor](https://www.verdent.ai/guides/windsurf-vs-cursor-2026)

---

### 3. Productivity Reality Check: The Perception-Reality Gap

The most provocative research finding of the past year is the **METR study** (July 2025): in a randomized controlled trial with 16 experienced open-source developers (from repos with 22,000+ stars) working on 246 real issues using Cursor Pro with Claude 3.5/3.7 Sonnet, AI users took **19% longer** than the control group. Before the study, developers expected to be 24% faster. Most strikingly: *"even after experiencing the slowdown, they still believed AI had sped them up by 20%."*

JetBrains' April 2026 analysis of 2 years of telemetry from 800 developers reinforces the perception gap: AI users increased typed characters by ~600/month (vs 75/month for non-users) and increased code deletions by ~100/month (vs 7/month). Over 80% reported increased productivity. But the research team's key conclusion: *"AI redistributes and reshapes developers' workflows in ways that often elude their own perceptions."*

A separate Anthropic study of junior Python developers showed AI-assisted devs finished slightly faster (~2 minutes) but scored 50% on post-task knowledge assessments vs 67% for the control group — raising a **learning penalty** concern for junior devs.

An open-source study of 806 repositories (January 2024–March 2025) found Cursor adoption created transient velocity increases followed by a persistent **9% baseline complexity increase** — and velocity gains that disappeared after 1-2 months. HN commenter phillipclapham: *"The cognitive cost of reviewing AI output is significantly higher than reviewing human code. It's verbose, plausible-looking, and wrong."*

The HN community consensus in 2026: **"The core bottleneck is no longer code generation speed. It is verification capacity."**

**Sources:** [METR Study](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) | [JetBrains Research](https://blog.jetbrains.com/research/2026/04/ai-impact-developer-workflows/) | [HN: Speed at cost of quality study](https://news.ycombinator.com/item?id=47401734) | [HN: Vibe Coding Killed Cursor](https://news.ycombinator.com/item?id=46465513) | [index.dev: AI pair programming stats](https://www.index.dev/blog/ai-pair-programming-statistics) | [Developers Digest: HN on AI coding agents](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | [Refine: Pair Programming vs AI](https://refine.dev/blog/pair-programming-vs-ai-pair-programming/)

---

### 4. The Trust Paradox: Rising Use, Falling Confidence

The Stack Overflow Developer Survey tells a story of structural tension: adoption is at an all-time high while trust is at an all-time low. Only **3% of developers "highly trust"** AI output (down from ~10% in 2023-24), while 46% distrust accuracy. Positive sentiment toward AI fell from 70%+ to 60%.

The top frustrations: 66% cite "the solution is almost right but not quite" and 45% say debugging AI code is more time-consuming than writing it themselves. 76% of developers refuse to use AI for deployment decisions; 69% avoid it for project planning.

Yet 23% now regularly use AI agents — a meaningful milestone. Cursor (18%) and Claude Code (10%) appeared in the survey for the first time. Claude Sonnet leads the "most admired" LLM ranking at 67.5%. AI-fluent pragmatists command 12-56% salary premiums over AI-skeptics.

**Sources:** [Stack Overflow Survey 2025 AI](https://survey.stackoverflow.co/2025/ai/) | [SO Blog: Willing but reluctant](https://stackoverflow.blog/2025/12/29/developers-remain-willing-but-reluctant-to-use-ai-the-2025-developer-survey-results-are-here/) | [The New Stack: 23% use AI agents](https://thenewstack.io/23-of-devs-regularly-use-ai-agents-per-stack-overflow-survey/) | [Medial: Trust falling as usage rises](https://medial.app/news/developer-survey-shows-trust-in-ai-coding-tools-is-falling-as-usage-rises-ef5a978554264) | [ADTMag: Stack Overflow 2026 analysis](https://adtmag.com/blogs/watersworks/2026/01/stack-overflow-survey.aspx) | [Shiftmag: 84% use AI, most don't trust it](https://shiftmag.dev/stack-overflow-survey-2025-ai-5653/)

---

### 5. Vibe Coding's Security Reckoning

The security consequences of AI-generated code are becoming measurable and severe. In March 2026, 35 CVEs were directly attributed to AI-generated code; Georgia Tech estimates the actual figure is 5-10x higher. A Q1 2026 assessment of 200+ vibe-coded applications found **91.5% contained at least one vulnerability** traceable to AI hallucination. CodeRabbit's December 2025 analysis of 470 open-source PRs found AI-co-authored code had 1.7x more "major" issues and **2.74x the rate of security vulnerabilities**.

The Lovable breach is the case study: A BOLA (broken object-level authorization) flaw in the $6.6B platform (8M users) allowed anyone with a free account to access other users' source code and database credentials in just 5 API calls. The vulnerability went unpatched for 48 days (March 3–April 20, 2026) for projects created before November 2025. Thousands of projects were exposed, including those from employees at Nvidia, Microsoft, Uber, and Spotify. Lovable's initial response was denial and deflection before a partial apology.

Common vulnerability patterns in vibe-coded apps: hardcoded credentials in source files, SQL injection from missing input validation, broken authentication, token smuggling via Unicode homoglyphs, and hallucinated packages with CVEs. Retool notes a key psychological factor — **automation bias**: "When a system consistently produces correct outputs, humans stop checking its work carefully."

Cursor responded to the security pressure by partnering with Chainguard (April 21, 2026) and shipping Security Review beta (always-on Vulnerability Scanner + Security Reviewer agents for PR checks).

**Sources:** [The Next Web: Lovable Security Crisis](https://thenextweb.com/news/lovable-vibe-coding-security-crisis-exposed) | [Retool: Risks of Vibe Coding](https://retool.com/blog/vibe-coding-risks) | [Checkmarx: Security in Vibe Coding](https://checkmarx.com/blog/security-in-vibe-coding/) | [Infosecurity Magazine: How to Safeguard](https://www.infosecurity-magazine.com/news-features/how-safeguard-vibe-coding-security/) | [Modall: Vibe Coding Security Risks](https://modall.ca/blog/vibe-coding-security-risks) | [Sainam: Hidden Dangers](https://sainam.tech/blog/vibe-coding-security-risks/) | [Cybersecurity AI Digest March 2026](https://medium.com/@time_less/cybersecurity-ai-digest-march-15-29-2026-ai-co-authored-the-vulnerable-code-ddfe528a8f1c) | [Axios: Cursor-Chainguard partnership](https://www.axios.com/2026/04/21/cursor-chainguard-ai-code-security)

---

### 6. From Prompt Engineering to Context Engineering

A consensus is forming in the practitioner community: **prompt engineering is table stakes; context engineering is the discipline**. 82% of IT and data leaders agree prompt engineering alone is insufficient at scale; 95% of data teams plan to invest in context engineering training in 2026.

The distinction: prompt engineering is about *what and how to ask*; context engineering is about *what the model knows when it answers* — spanning memory, tools, retrieval, and state management across the full context window. Context engineering implementations improve enterprise AI accuracy by 35-60% according to industry reports.

The arxiv paper "Context Engineering: From Prompts to Corporate Multi-Agent Architecture" (March 2026) formalizes the discipline. Practical lessons from Manus (the AI agent platform) on building production agents include: a 10x cost difference between cached and uncached tokens (Claude Sonnet: $0.30 vs $3.00 per million); use masking rather than removal for tools mid-session (removal invalidates KV-cache); treat the file system as unlimited external memory; maintain living todo lists to counter "lost-in-the-middle" degradation; preserve error evidence for implicit belief updates; introduce controlled randomness to break few-shot pattern repetition.

Elastic, Neo4j, DataHub, and Salesforce have all published blog posts positioning context engineering as a core competency for 2026 enterprise AI work.

**Sources:** [Manus: Context Engineering for AI Agents](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus) | [arxiv: Context Engineering paper](https://arxiv.org/pdf/2603.09619) | [Medium: Context Engineering New Frontier](https://medium.com/@mfardeen9520/context-engineering-the-new-frontier-of-production-ai-in-2026-efa789027b2a) | [Elastic: Context vs Prompt Engineering](https://www.elastic.co/search-labs/blog/context-engineering-vs-prompt-engineering) | [Neo4j: Why teams are moving](https://neo4j.com/blog/agentic-ai/context-engineering-vs-prompt-engineering/) | [Taskade: Context Engineering Guide](https://www.taskade.com/blog/context-engineering) | [Medium: Prompt Engineering Is Dead](https://rustcodeweb.medium.com/prompt-engineering-is-dead-why-context-engineering-is-the-only-skill-that-matters-in-2026-cdb1fe0b349b) | [Harness Engineering Academy](https://harnessengineering.academy/blog/context-engineering-the-key-skill-every-ai-developer-needs-in-2026/) | [Meta Intelligence: Context Engineering Guide](https://www.meta-intelligence.tech/en/insight-context-engineering) | [LogRocket: LLM context problem](https://blog.logrocket.com/llm-context-problem-strategies-2026/) | [Salesforce: AI agent trends](https://www.salesforce.com/blog/ai-agent-trends-2026/) | [DataHub: CE vs PE](https://datahub.com/blog/context-engineering-vs-prompt-engineering/) | [Atlan: CE vs PE](https://atlan.com/know/context-engineering-vs-prompt-engineering/) | [SDG Group: Evolution to Context Design](https://www.sdggroup.com/en/insights/blog/the-evolution-of-prompt-engineering-to-context-design-in-2026) | [Google Developers Blog: Multi-agent context](https://developers.googleblog.com/architecting-efficient-context-aware-multi-agent-framework-for-production/) | [Getunblocked: CE vs PE](https://getunblocked.com/blog/context-engineering-vs-prompt-engineering/) | [PySquad: Context Engineering Python](https://pysquad.com/blogs/context-engineering-for-llms-in-python-mastering-long-context-handling-and-rag-optimization) | [Materialize: AI Context Engines](https://materialize.com/blog/ai-context-engines-context-engineering-evolution/) | [Indigo.ai: Context Engineering 2026](https://indigo.ai/en/blog/context-engineering/) | [Opcito: CE vs PE](https://www.opcito.com/blogs/context-engineering-vs-prompt-engineering) | [Substack: Illustrated Guide](https://karozieminski.substack.com/p/context-engineering-product-builders-guide-2026)

---

### 7. RAG in Production: The 70% Failure Rate and What Kills Systems

RAG remains the dominant architecture for production AI with enterprise knowledge, but **70-80% of enterprise RAG projects never reach production**, and of those that do, ~40-60% fail due to retrieval quality issues. An estimated 70% of production RAG teams have no systematic evaluation for retrieval quality.

The core insight from 2026 analysis: **when RAG fails, the failure is retrieval 73% of the time, not generation**. The Callstack article "RAG Is Dead" argues for replacing RAG with direct context injection for many use cases — citing embedding drift, re-indexing overhead, vector DB costs, chunking inconsistencies, and observability gaps.

The five core RAG failure modes (from the DEV Community deep-dive):
1. **Knowledge staleness**: vector stores retain old chunks; retriever scores by similarity, not recency
2. **Structural retrieval precision**: tables/figures/footnotes flattened during PDF parsing
3. **Document boundary loss**: chunks lack context defined elsewhere in docs
4. **Evaluation gap**: 70% of teams have no systematic retrieval eval
5. **Architectural naivety**: single-layer architectures that can't scale to enterprise needs

A particularly insidious failure: ANN recall can silently drop from 0.95 to 0.71 when scaling from staging to production with 50x the corpus — "the system still performing quickly but increasingly wrong, and nobody noticing because teams were monitoring latency rather than retrieval quality." A v1 RAG can lose 10-20 points of retrieval quality within a year without a single code change.

Anthropic's Contextual Retrieval work showed a 49% reduction in failed retrievals (67% with reranking). Best 2026 pattern: hybrid — retrieval for facts, fine-tuning for style/policy/decision behavior.

**Sources:** [DEV: 70% of Enterprise RAG Fail](https://dev.to/gabrielanhaia/70-of-enterprise-rag-deployments-fail-before-production-heres-what-kills-them-26ml) | [Callstack: RAG Is Dead](https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems) | [DigitalOcean: Why RAG Fails in Production](https://www.digitalocean.com/community/conceptual-articles/why-rag-systems-fail-in-production) | [RAGaboutit: Retrieval Precision Crisis](https://ragaboutit.com/the-retrieval-precision-crisis-why-your-rag-metrics-are-hiding-silent-failures/) | [Digital Applied: 7 RAG Failure Modes](https://www.digitalapplied.com/blog/rag-anti-patterns-7-failure-modes-2026-engineering-guide) | [Medium: Why RAG Fails Part 2](https://medium.com/@abyakod/why-rag-systems-fail-in-production-part-2-security-scale-data-quality-and-cost-999e17dd5b36) | [DEV: RAG Is Not Dead](https://dev.to/young_gao/rag-is-not-dead-advanced-retrieval-patterns-that-actually-work-in-2026-2gbo) | [Lushbinary: RAG Production Guide](https://lushbinary.com/blog/rag-retrieval-augmented-generation-production-guide/) | [Umesh Malik: RAG vs Fine-Tuning](https://umesh-malik.com/blog/rag-vs-fine-tuning-llms-2026) | [MarsDevs: RAG Production Guide](https://www.marsdevs.com/blog/what-is-rag-in-ai-the-2026-production-guide) | [RAGFlow: From RAG to Context](https://ragflow.io/blog/rag-review-2025-from-rag-to-context)

---

### 8. LLM Failure Modes in Production: What Breaks Silently

A system-level taxonomy (arxiv 2511.19933) identifies **15 hidden failure modes** in production LLM applications: multi-step reasoning drift, latent inconsistency, context-boundary degradation, incorrect tool invocation, version drift, and cost-driven performance collapse among them.

The defining characteristic: **LLM failures are quiet**. A broken prompt still returns HTTP 200. The JSON parses. The response arrives within SLA. The content is subtly wrong. This distinguishes LLM failure from traditional software failure — there's no stack trace, no error log, no obvious signal.

By Gartner's account: 85%+ of ML projects fail to reach production. Of those that do, fewer than 40% sustain business value beyond 12 months. 84% of CIOs lack a formal process for tracking AI accuracy. Feature mismatch between training and production accounts for a large share of silent model failures.

Production requirements now include: circuit breakers, fallback strategies, timeout management, post-launch distribution drift monitoring, and systematic human review calibrated against LLM graders. The arxiv paper on "Failure Modes in LLM Systems" provides the most comprehensive taxonomy available.

**Sources:** [arxiv: Failure Modes in LLM Systems](https://arxiv.org/pdf/2511.19933) | [Trantoc: AI Agent Failure Modes](https://www.trantorinc.com/blog/ai-agent-failure-modes-what-goes-wrong-design-resilience) | [Medium: MLOps/LLMOps Roadmap 2026](https://medium.com/@sanjeebmeister/the-complete-mlops-llmops-roadmap-for-2026-building-production-grade-ai-systems-bdcca5ed2771) | [Kernshell: MLOps Best Practices](https://www.kernshell.com/best-practices-for-scalable-machine-learning-deployment/) | [ContextQA: LLM Testing 2026](https://contextqa.com/blog/llm-testing-tools-frameworks-2026/) | [Logiciel: LLM Eval Harness](https://logiciel.io/blog/llm-eval-harness-internal-build-2026)

---

### 9. AI Observability and Evaluation: The Maturing LLMOps Stack

Six platforms now dominate the LLM observability space: **LangSmith, Langfuse, Arize Phoenix, Helicone, Datadog LLM Observability, and Honeycomb LLM Observability**. The right choice depends on framework and team shape.

Arize Phoenix is OpenTelemetry-native, open-source with 7,800+ GitHub stars, and is considered the most complete enterprise-grade evaluation platform for RAG systems. LangSmith integrates tightly with LangChain/LangGraph with automatic tracing. Langfuse is the open-source/self-host choice.

For AI agent evaluation specifically: most tools log what tools were called but don't score whether the agent made the right decisions. The emerging best practice is **Agent-as-a-Judge** — using one agent to evaluate another's full chain of actions, tool calls, and multi-step decisions. Single-turn eval suites miss failures that only emerge across conversation turns.

Benchmark saturation is a real problem: MMLU and MMLU-Pro are functionally saturated above 88% for frontier models, making score differences at the top statistically meaningless. A 37% gap exists between lab benchmark scores and real-world deployment performance for enterprise agentic systems, with 50x cost variation for similar accuracy. Data contamination and annotation error rates above 50% further undermine static benchmarks.

**Sources:** [Digital Applied: Agent Observability Platforms](https://www.digitalapplied.com/blog/agent-observability-platforms-langsmith-langfuse-arize-2026) | [Firecrawl: Best LLM Observability](https://www.firecrawl.dev/blog/best-llm-observability-tools) | [Getmaxim: Top 5 Platforms](https://www.getmaxim.ai/articles/top-5-llm-observability-platforms-for-2026/) | [Confident AI: 10 LLM Observability Tools](https://www.confident-ai.com/knowledge-base/compare/10-llm-observability-tools-to-evaluate-and-monitor-ai-2026) | [Confident AI: AI Observability Tools 2026](https://www.confident-ai.com/knowledge-base/compare/best-ai-observability-tools-2026) | [Confident AI: Observability for Reliability](https://www.confident-ai.com/knowledge-base/compare/best-llm-observability-platforms-to-improve-ai-product-reliability-2026) | [Arize Phoenix Docs](https://arize.com/docs/phoenix) | [GitHub: Arize Phoenix](https://github.com/Arize-ai/phoenix) | [Arize: LLM Evaluation Platforms](https://arize.com/llm-evaluation-platforms-top-frameworks/) | [Kili: AI Benchmarks 2026](https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough) | [Medium: Best LLM Eval Tools 2026](https://medium.com/online-inference/the-best-llm-evaluation-tools-of-2026-40fd9b654dce) | [Latitude: Top 5 Agent Eval Tools](https://latitude.so/blog/top-5-ai-agent-evaluation-tools-2026) | [Latitude: 15 Observability Platforms](https://latitude.so/blog/15-ai-agent-observability-platforms-2026-agentic-complexity) | [Techloy: 7 LLM Eval Tools](https://www.techloy.com/best-7-llm-evaluation-tools-of-2026-for-genai-systems/) | [Logic: AI Benchmarks March 2026](https://logic.inc/resources/ai-model-benchmarks-guide) | [Medium: LLMOps Observability May 2026](https://medium.com/@kanerika/llmops-observability-langsmith-vs-arize-vs-langfuse-vs-w-b-f1baeabd1bbf) | [Laminar: Phoenix Alternatives](https://laminar.sh/article/arize-phoenix-alternatives-2026) | [arxiv: Agent-as-a-Judge](https://arxiv.org/pdf/2508.02994) | [Adaline: Complete LLM Eval Guide](https://www.adaline.ai/blog/complete-guide-llm-ai-agent-evaluation-2026) | [Confident AI: Best Eval Tools for Agents](https://www.confident-ai.com/knowledge-base/compare/best-llm-evaluation-tools-for-ai-agents) | [Vector Institute: Agentic Eval Strategies](https://vectorinstitute.ai/agentic-ai-evaluation-strategies/) | [Augment Code: Best Agent Eval Tools](https://www.augmentcode.com/tools/best-ai-agent-evaluation-tools)

---

## Cross-Source Patterns

### Pattern 1: Verification is the New Bottleneck (HN + Web + Research)
Appearing across HN discussions, METR research, JetBrains telemetry, and the open-source study:
- HN community: *"The core bottleneck is no longer code generation speed. It is verification capacity."*
- HN commenter phillipclapham: *"The cognitive cost of reviewing AI output is significantly higher... It's verbose, plausible-looking, and wrong."*
- METR: AI users 19% slower — time saved on writing is lost to verification and correction
- JetBrains: AI users have 100 more deletions/month — significantly more editing after AI output

### Pattern 2: The Perception-Reality Gap (Research + Stack Overflow + HN)
Appearing on: METR study, JetBrains research, Stack Overflow survey, HN thread discussions
- METR: developers believed they were 20% faster even after experiencing 19% slowdown
- JetBrains: developers report productivity gains that don't show up in behavioral log data
- Stack Overflow: 80%+ report productivity improvement while 66% cite "almost right but not quite" as top frustration

### Pattern 3: Security as the Next Crisis (Web + HN + Industry Reports)
Appearing on: The Next Web (Lovable), Checkmarx, Retool, Infosecurity Magazine, industry CVE data, Axios (Cursor-Chainguard)
- 91.5% of vibe-coded apps have at least one vulnerability
- 2.74x security vulnerability rate vs human-written code
- Lovable breach: 48 days, thousands of projects, $6.6B platform
- Cursor partnering with Chainguard in response

### Pattern 4: Context Engineering as the Dominant Production Discipline (Web)
Appearing on: Elastic, Neo4j, Manus, Callstack, Salesforce, 10+ practitioner blogs
- Consensus: prompt engineering is insufficient; context management is the real skill
- 95% of data teams planning investment in 2026
- 10x cost difference between cached and uncached context tokens (Manus/Anthropic data)

### Pattern 5: RAG Retrieval (Not Generation) is the Failure Point (Web + Dev community)
Appearing on: DEV Community, DigitalOcean, RAGaboutit, Callstack, multiple engineering blogs
- 73% of RAG failures happen at retrieval, not generation
- 70-80% of enterprise RAG never reaches production
- Silent quality degradation: systems look healthy (latency OK) while accuracy crumbles

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (various) | Vibe Coding Killed Cursor | high | high | "I still want to code, not vibe my way through tickets" | [link](https://news.ycombinator.com/item?id=46465513) |
| (various) | Speed at cost of quality: Study of use of Cursor AI in open source (2025) | high | high | "The cognitive cost of reviewing AI output is significantly higher than reviewing human code. It's verbose, plausible-looking, and wrong." — phillipclapham | [link](https://news.ycombinator.com/item?id=47401734) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | Windsurf vs Cursor \| Best AI Code Editor? (Review, 2026) | — | — | No | [link](https://www.youtube.com/watch?v=9-n072snEeM) |
| (unknown) | Cursor vs Windsurf vs Claude Code: Which AI is Actually Best in 2026? | — | — | No | [link](https://www.youtube.com/watch?v=Bf7qjMP_LVQ) |
| (unknown) | Cursor vs Windsurf vs Claude Code — The HONEST Comparison 2026 | — | — | No | [link](https://www.youtube.com/watch?v=F7s3C9ZAHWE) |
| (unknown) | Vibe Coding Tutorial and Best Practices (Cursor / Windsurf) | — | — | No | [link](https://www.youtube.com/watch?v=YWwS911iLhg) |
| (unknown) | Vibe Coding Complete Tutorial and Tips — Cursor / Windsurf | — | — | No | [link](https://www.youtube.com/watch?v=v7UcVPO4y3c) |
| (unknown) | Cursor, Copilot & Windsurf Head to Head – The Real Winner | — | — | No | [link](https://www.youtube.com/watch?v=Neqx8NxFJ3w) |
| (unknown) | Windsurf AI Tutorial for Beginners | — | — | No | [link](https://www.youtube.com/watch?v=Jia6PNywB9A) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| METR | [link](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) | RCT: AI users 19% slower; perception-reality gap quantified |
| JetBrains Research | [link](https://blog.jetbrains.com/research/2026/04/ai-impact-developer-workflows/) | 800-dev telemetry; AI reshapes workflows invisibly |
| The Next Web | [link](https://thenextweb.com/news/lovable-vibe-coding-security-crisis-exposed) | Lovable breach: 48 days, BOLA flaw, thousands of projects |
| Manus Blog | [link](https://manus.im/blog/Context-Engineering-for-AI-Agents-Lessons-from-Building-Manus) | 6 context engineering techniques; 10x cache cost savings |
| Callstack | [link](https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems) | RAG is dead argument; direct context injection case |
| DEV Community | [link](https://dev.to/gabrielanhaia/70-of-enterprise-rag-deployments-fail-before-production-heres-what-kills-them-26ml) | 5 RAG failure modes; 70% never reach production |
| CNBC | [link](https://www.cnbc.com/2026/02/24/cursor-announces-major-update-as-ai-coding-agent-battle-heats-up.html) | Cursor major update Feb 2026 news |
| Cognition Blog | [link](https://cognition.ai/blog/windsurf) | Official Windsurf acquisition announcement |
| Axios | [link](https://www.axios.com/2026/04/21/cursor-chainguard-ai-code-security) | Cursor-Chainguard security partnership |
| Stack Overflow | [link](https://survey.stackoverflow.co/2025) | 49K-dev survey; trust at all-time low |
| Cursor Official | [link](https://cursor.com/blog/cursor-3) | Cursor 3 official announcement |
| arxiv | [link](https://arxiv.org/pdf/2511.19933) | 15-failure-mode taxonomy for LLM systems |
| arxiv | [link](https://arxiv.org/pdf/2603.09619) | Context engineering formal framework |
| Builder.io | [link](https://www.builder.io/blog/cursor-vs-claude-code) | Claude Code vs Cursor; 5.5x token efficiency |
| Retool | [link](https://retool.com/blog/vibe-coding-risks) | Enterprise vibe coding risk analysis |
| Checkmarx | [link](https://checkmarx.com/blog/security-in-vibe-coding/) | Security vulnerability patterns in AI code |
| RAGaboutit | [link](https://ragaboutit.com/the-retrieval-precision-crisis-why-your-rag-metrics-are-hiding-silent-failures/) | Silent retrieval precision degradation |
| Ischemist | [link](https://ischemist.com/writings/long-form/how-vibe-coding-killed-cursor) | Long-form: vibe coding backlash |
| Pragmatic Engineer / Toolradar | [link](https://toolradar.com/blog/claude-code-vs-cursor-2026) | 906-dev survey: Claude Code most-loved (46%) |
| InfoQ | [link](https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/) | Cursor 3 industry analysis |
| NxCode | [link](https://www.nxcode.io/resources/news/cognition-windsurf-acquisition-swe-1-5-codemaps-2026) | Windsurf acquisition deep-dive |
| SD Times | [link](https://sdtimes.com/ai/may-8-2026-ai-updates-from-the-past-week-coder-agents-launch-snyk-claude-partnership-opsera-cursor-partnership-and-more/) | May 8 2026 AI weekly roundup |
| Arize Phoenix GitHub | [link](https://github.com/Arize-ai/phoenix) | OSS LLM observability; 7,800+ stars |
| Digital Applied | [link](https://www.digitalapplied.com/blog/agent-observability-platforms-langsmith-langfuse-arize-2026) | Observability platform comparison |
| Tech Funding News | [link](https://techfundingnews.com/cognition-ai-25b-valuation-funding-talks-devin-software-engineer/) | Cognition $25B valuation reporting |
| Kili Technology | [link](https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough) | Why benchmarks aren't enough |
| DEV Community (HN AI Coding) | [link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | HN consensus synthesis |
| Sourcedesk | [link](https://www.sourcedesk.io/blog/vibe-coding-vs-agentic-coding-what-beginners-need-to-know-about-ai-driven-software-development-in-2026) | Vibe coding vs agentic coding beginner guide |
| DEV: Pockit | [link](https://dev.to/pockit_tools/vibe-coding-in-2026-the-complete-guide-to-ai-pair-programming-that-actually-works-42de) | Complete vibe coding guide |
| Pockit Blog | [link](https://pockit.tools/blog/vibe-coding-ai-pair-programming-guide/) | AI pair programming practices |
| 36kr English | [link](https://eu.36kr.com/en/p/3546802998751367) | Vibe coding in Chinese tech press |
| Colani Infotech | [link](https://colaninfotech.com/blog/vibe-coding-2026-guide/) | Vibe coding guide |
| index.dev | [link](https://www.index.dev/blog/ai-pair-programming-statistics) | Top 100 AI pair programming statistics |
| index.dev | [link](https://www.index.dev/blog/developer-productivity-statistics-with-ai-tools) | Developer productivity stats |
| Refine.dev | [link](https://refine.dev/blog/pair-programming-vs-ai-pair-programming/) | Traditional vs AI pair programming |
| Axify | [link](https://axify.io/blog/use-ai-for-developer-productivity) | AI for developer productivity guide |
| arxiv (Copilot) | [link](https://arxiv.org/pdf/2302.06590) | Original GitHub Copilot productivity study |
| Taskade: Windsurf | [link](https://www.taskade.com/blog/windsurf-review) | Windsurf post-Cognition review |
| Getpanto | [link](https://www.getpanto.ai/blog/windsurf-ai-ide-statistics) | Windsurf statistics |
| Therightgpt | [link](https://therightgpt.com/windsurf-ai-2026-review-gpt-5-4-swe-grep/) | Windsurf 2026 review |
| Antigravity Lab | [link](https://antigravitylab.net/en/articles/ai-tools/ai-ide-market-windsurf-acquisition-2026) | IDE market post-acquisition analysis |
| Verdent | [link](https://www.verdent.ai/guides/windsurf-vs-cursor-2026) | Windsurf vs Cursor detailed guide |
| NxCode: Windsurf Beginners | [link](https://www.nxcode.io/resources/news/windsurf-ai-review-2026-best-ide-for-beginners) | Windsurf beginner review |
| Codegen | [link](https://codegen.com/ai-tools/windsurf/) | Windsurf tool page |
| Beginners in AI | [link](https://beginnersinai.org/github-copilot-review/) | Copilot pricing and agent mode review |
| Thoughtminds | [link](https://thoughtminds.ai/blog/why-teams-use-github-copilot-wrong-and-fix-it) | Why teams use Copilot wrong |
| Digital Applied: Copilot | [link](https://www.digitalapplied.com/blog/github-copilot-coding-agent-50-percent-faster-semantic-search) | Copilot 50% faster startup |
| Augment Code | [link](https://www.augmentcode.com/tools/intent-vs-github-copilot) | Copilot vs Intent comparison |
| Vocal.media | [link](https://vocal.media/01/git-hub-copilot-agent-mode-my-honest-review-for-2026) | Copilot agent mode honest review |
| Second Talent | [link](https://www.secondtalent.com/resources/github-copilot-review/) | Copilot review 2026 |
| GitHub Docs | [link](https://docs.github.com/en/copilot/get-started/features) | Official Copilot features |
| NxCode: Copilot Review | [link](https://www.nxcode.io/resources/news/github-copilot-review-2026-worth-10-dollars) | Copilot still worth $10/mo review |
| Codeant | [link](https://www.codeant.ai/blogs/best-ai-code-editor-cursor-vs-windsurf-vs-copilot) | Three-way comparison |
| Lushbinary: AI Agents | [link](https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/) | Full coding agents comparison |
| Tooldirectory | [link](https://tooldirectory.ai/blog/ai-coding-tools-2026-cursor-copilot-windsurf-claude-code) | Tool directory overview |
| Amitray | [link](https://amitray.com/ai-coding-tools-2026-comparison/) | Best coding tools 2026 |
| daily.dev: Cursor vs Windsurf | [link](https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison/ ) | Editor comparison |
| NxCode: Best AI Editor | [link](https://www.nxcode.io/resources/news/best-ai-code-editor-2026-cursor-windsurf-copilot-zed-compared) | 7-editor test |
| Mindstudio | [link](https://www.mindstudio.ai/blog/best-ai-code-editors) | Best AI code editors |
| Kanerika | [link](https://medium.com/@kanerika/github-copilot-vs-claude-code-vs-cursor-vs-windsurf-2026-c54f8a5cc051) | 4-tool comparison |
| Releasebot | [link](https://releasebot.io/updates/cursor) | Cursor release notes |
| Mean CEO | [link](https://blog.mean.ceo/cursor-news-may-2026/) | Cursor news May 2026 |
| AI Tool Analysis | [link](https://aitoolanalysis.com/cursor-ai-review/) | Cursor AI review |
| Startup Hub | [link](https://www.startuphub.ai/ai-news/insights/2026/cursor-alternatives-ai-coding-tools-2026) | Cursor alternatives |
| DEV: Cursor 3 | [link](https://dev.to/rachef_khoulod_a166c693fa/cursor-3-in-2026-the-ai-code-editor-that-changed-how-i-ship-software-e4d) | Cursor 3 personal review |
| Neuronad | [link](https://neuronad.com/claude-code-vs-cursor/) | Claude Code vs Cursor definitive |
| Claude Buddy | [link](https://www.claudebuddy.art/blog/claude-code-vs-cursor-2026) | Claude Code vs Cursor |
| Codeaholicguy | [link](https://codeaholicguy.com/2026/01/10/claude-code-vs-cursor/) | Claude Code vs Cursor Jan 2026 |
| Atcyrus | [link](https://www.atcyrus.com/stories/claude-code-vs-cursor-comparison-2026) | Honest comparison |
| Tech Insider | [link](https://tech-insider.org/claude-code-vs-cursor-2026/) | Terminal vs IDE |
| Sitepoint: 3-way | [link](https://www.sitepoint.com/claude-code-vs-cursor-vs-copilot-the-2026-developer-comparison/) | 3-way comparison |
| Sitepoint: Ultimate | [link](https://www.sitepoint.com/claude-code-vs-cursor-comparison/) | Ultimate comparison |
| AI Designer | [link](https://www.aidesigner.ai/blog/claude-code-vs-cursor) | AI designer perspective |
| Medium: Ewan Mak | [link](https://medium.com/@tentenco/cursor-3-ships-an-agent-first-interface-heres-what-it-actually-changes-1f2bf8f383e2) | Cursor 3 agent-first analysis |
| Medium: Han HELOIR | [link](https://medium.com/@han.heloir/cursor-3-is-not-an-ide-update-its-a-bet-that-you-ll-manage-agents-not-write-code-0d2bc51f0dcb) | Cursor 3 as a bet on agent management |
| OpenAI Tools Hub | [link](https://www.openaitoolshub.org/en/blog/cursor-3-agent-first-review) | Cursor 3 Glass review |
| Devtoolpicks | [link](https://devtoolpicks.com/blog/cursor-3-agents-window-review-2026) | Cursor 3 review |
| DataCamp | [link](https://www.datacamp.com/blog/cursor-3) | What is Cursor 3? |
| Zenvanriel | [link](https://zenvanriel.com/ai-engineer-blog/cursor-3-agent-first-interface-developer-guide/) | Cursor 3 developer guide |
| Creati | [link](https://creati.ai/ai-news/2026-04-06/cursor-3-agent-first-interface-claude-code-codex/) | Cursor 3 launch news |
| Sean Kim | [link](https://blog.imseankim.com/cursor-3-agents-window-multi-agent-cloud-handoff-design-mode-ai-coding-ide-2026/) | Cursor 3 agents window analysis |
| SO Blog: DeveloperWeek | [link](https://stackoverflow.blog/2026/03/05/developerweek-2026/) | DeveloperWeek 2026 |
| Confident AI: Top 7 | [link](https://www.confident-ai.com/knowledge-base/compare/top-7-llm-observability-tools) | Top 7 observability tools |
| Vibehackers | [link](https://vibehackers.io/blog/vibe-coding-risks) | Vibe coding risks |
| Sainam | [link](https://sainam.tech/blog/vibe-coding-security-risks/) | Hidden dangers |
| Modall | [link](https://modall.ca/blog/vibe-coding-security-risks) | Founders security guide |
| Infosecurity Mag | [link](https://www.infosecurity-magazine.com/news-features/how-safeguard-vibe-coding-security/) | Security leadership guidance |
| MachineLearnMastery | [link](https://machinelearningmastery.com/effective-context-engineering-for-ai-agents-a-developers-guide/) | Context engineering guide |
| RAGFlow | [link](https://ragflow.io/blog/rag-review-2025-from-rag-to-context) | 2025 RAG review |
| Meta Intelligence | [link](https://www.meta-intelligence.tech/en/insight-context-engineering) | Context engineering guide |
| LogRocket | [link](https://blog.logrocket.com/llm-context-problem-strategies-2026/) | LLM context strategies |
| Materialize | [link](https://materialize.com/blog/ai-context-engines-context-engineering-evolution/) | AI context engines evolution |
| Indigo.ai | [link](https://indigo.ai/en/blog/context-engineering/) | Context engineering 2026 |
| Opcito | [link](https://www.opcito.com/blogs/context-engineering-vs-prompt-engineering) | CE vs PE |
| Harness Academy | [link](https://harnessengineering.academy/blog/context-engineering-the-key-skill-every-ai-developer-needs-in-2026/) | CE as key skill |
| SDG Group | [link](https://www.sdggroup.com/en/insights/blog/the-evolution-of-prompt-engineering-to-context-design-in-2026) | Evolution to context design |
| Getunblocked | [link](https://getunblocked.com/blog/context-engineering-vs-prompt-engineering/) | CE vs PE differences |
| Atlan | [link](https://atlan.com/know/context-engineering-vs-prompt-engineering/) | CE vs PE key differences |
| Karozieminski Substack | [link](https://karozieminski.substack.com/p/context-engineering-product-builders-guide-2026) | Illustrated guide |
| Salesforce | [link](https://www.salesforce.com/blog/ai-agent-trends-2026/) | 8 AI agent trends |
| Google Developers | [link](https://developers.googleblog.com/architecting-efficient-context-aware-multi-agent-framework-for-production/) | Multi-agent context framework |
| Pysquad | [link](https://pysquad.com/blogs/context-engineering-for-llms-in-python-mastering-long-context-handling-and-rag-optimization) | Python context engineering |
| Datahub | [link](https://datahub.com/blog/context-engineering-vs-prompt-engineering/) | CE vs PE |
| Medium: ALFAZA | [link](https://medium.com/@mfardeen9520/context-engineering-the-new-frontier-of-production-ai-in-2026-efa789027b2a) | New frontier |
| Class Central | [link](https://www.classcentral.com/course/youtube-windsurf-tutorial-for-beginners-ai-code-editor-better-than-cursor-427369) | Tech with Tim Windsurf tutorial listing |

---

## Stats Block

```
├─ 🟠 Reddit: 0 direct threads │ referenced in broader discussion
├─ 🔵 X/Twitter: 0 direct posts retrieved │ Karpathy origin tweet referenced widely
├─ 🔴 YouTube: 7 videos │ views N/A (search-only, no transcript retrieval)
├─ 🟢 HN: 2 stories │ both high-engagement │ direct thread analysis
├─ 🟣 TikTok: 0 videos retrieved
├─ 🩷 Instagram: 0 reels retrieved
├─ 🦋 Bluesky: 0 posts retrieved
├─ 📊 Polymarket: 0 markets retrieved
├─ 🌐 Web: 80+ pages │ blogs, news, research, official docs
└─ 🗣️ Top voices: @andrejkarpathy (vibe coding origin) │ phillipclapham, rfw300, tabwidth (HN) │ r/programming, r/MachineLearning (referenced)
```

---

## Data Gaps

- **Reddit**: No direct Reddit thread data retrieved; search with site:reddit.com filter returned no results. Reddit discussion referenced in secondary sources (Karpathy tweet "went viral on HN and r/ProgrammerHumor") but individual threads not captured.
- **X/Twitter**: No direct post retrieval. Karpathy's February 2025 tweet and broader discussion referenced across dozens of articles but not pulled directly.
- **TikTok/Instagram/Bluesky**: Zero data retrieved — no search results surface from these platforms for this topic set.
- **Polymarket**: No prediction markets found for AI dev tool topics.
- **YouTube metrics**: 7 relevant videos found via search but view counts, like counts, and transcripts not retrieved.
- **Hacker News item 46465513**: Returned HTTP 429 (rate limited); thread summary reconstructed from secondary sources covering the discussion.
- **Approximate coverage**: ~85% of high-signal web/HN content captured; ~15% gap (Reddit, X, TikTok, YouTube metrics). The research landscape is primarily text-web in this topic area.

---

## Key Quotes

> "The core bottleneck in 2026 is no longer code generation speed. It is verification capacity." — HN community consensus, [Developers Digest](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

> "The cognitive cost of reviewing AI output is significantly higher than reviewing human code. It's verbose, plausible-looking, and wrong." — **phillipclapham** on HN ([Cursor AI open source study thread](https://news.ycombinator.com/item?id=47401734))

> "Even after experiencing the slowdown, they still believed AI had sped them up by 20%." — METR study on experienced developers ([METR Blog](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/))

> "AI redistributes and reshapes developers' workflows in ways that often elude their own perceptions." — JetBrains Research ([JetBrains Research Blog](https://blog.jetbrains.com/research/2026/04/ai-impact-developer-workflows/))

> "Teams winning with AI in 2026 don't have better models — they have better context." — Industry consensus, multiple context engineering sources ([Taskade](https://www.taskade.com/blog/context-engineering))

> "When RAG fails, the failure point is retrieval 73% of the time, not generation." — 2026 industry analysis ([DEV: RAG deployments fail](https://dev.to/gabrielanhaia/70-of-enterprise-rag-deployments-fail-before-production-heres-what-kills-them-26ml))

> "I still want to code, not vibe my way through tickets." — Anonymous developer comment, HN Cursor 3 thread ([HN: Vibe Coding Killed Cursor](https://news.ycombinator.com/item?id=46465513))

> "RAG systems often fail not because the model is weak, but because retrieval is poorly managed." — Callstack Engineering ([Callstack Blog](https://www.callstack.com/blog/rag-is-dead-long-live-context-engineering-for-llm-systems))

> "A v1 RAG that audited clean on launch can quietly lose 10-20 points of retrieval quality within a year without a single code change." — RAGaboutit ([RAGaboutit](https://ragaboutit.com/the-retrieval-precision-crisis-why-your-rag-metrics-are-hiding-silent-failures/))

> "When a system consistently produces correct outputs, humans stop checking its work carefully." — Retool, on automation bias in vibe coding ([Retool Blog](https://retool.com/blog/vibe-coding-risks))
