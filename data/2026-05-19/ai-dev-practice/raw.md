# AI Dev Practice — Raw Research Data
**Date:** 2026-05-19
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## HACKER NEWS THREADS

### Ask HN: Cursor or Windsurf?
**URL:** https://news.ycombinator.com/item?id=43959710

**Key Comments:**
- **danpalmer** (316+ upvotes): "Zed is much less janky" and "feels like pretty mature software." Efficiency on M-series Macs with ~500MB RAM usage.
- Cursor praised for tab-complete autocomplete at ~95% accuracy, flat $20/month pricing
- Windsurf criticized for context limitations (100-200 line restrictions), struggles with files exceeding ~800 lines
- Aider praised for transparency and pay-as-you-go ($0.50-$2/day with Gemini)
- Cursor accused of context truncation to reduce costs
- Amazon Q ranking top-3 on SWE-Bench
- Claude Code ($100/month Max) gaining traction
- User fatigue: "the landscape changes too rapidly for definitive recommendations"

---

### Vibe Coding: Developer Slot Machines (Cursor, Windsurf)
**URL:** https://news.ycombinator.com/item?id=43830198

**Key Comments:**
- **stavros**: summarized core argument: "AIs are sometimes good for code, sometimes not so good... it's so easy to put more money in."
- **graylien** (author): "how it feels to jump from one [IDE] to the other" and "how the UI prompts you to add more credits." The slot machine metaphor describes both the non-deterministic code output and the frictionless spending experience.
- **rgoulter**: criticized the slot machine framing as lacking curiosity, suggesting developers should understand when LLMs succeed versus fail
- **okamiueru**: LLM outputs are "useful as a suggestion" but don't require factual correctness
- **Arn_Thor**: "no meaningful difference" after 30 minutes with Cursor vs VS Code + Copilot
- **zerosleep**: using "VS Code + Cline extension" as a controlled alternative to dedicated AI IDEs
- Copilot recently added model selection, narrowing the feature gap vs dedicated IDEs

---

### Ask HN: Why do Cursor, Windsurf and Claude Code dominate the conversation?
**URL:** https://news.ycombinator.com/item?id=44635075

**Key Comments:**
- **_jab**: "Three is already a lot of tools...mindshare matters." 
- Claude Code praised for "grok[ing]" complex C++ codebases better than competitors
- **daft_pink**: Claude "a lot more accurate" than Gemini, wasting less developer time
- **alwillis**: "vibe coding" videos heavily promoting Cursor and Windsurf on YouTube, while Claude Code has spawned "a cottage industry of websites, tutorials and videos"
- **poszlem**: Subscription pricing of Claude Code Max ($200/month) reduces friction vs pay-as-you-go
- GitHub Stars discrepancy: Gemini CLI (62k) and Codex (31k) more stars than Claude Code (25k), yet dominate less in discussion

---

### Tracking Copilot vs. Codex vs. Cursor vs. Devin PR Performance
**URL:** https://news.ycombinator.com/item?id=44188839

**Key Comments:**
- **Luke Hoban (GitHub)**: merge rates don't tell the complete story; different tools release PRs at different phases
- Codex: ~208K PRs vs. Cursor: ~705 — different usage patterns (async agent vs. interactive)
- Claude Code absence questioned; explained as not initially identified as autonomous agent
- "If it gets merged it is a fairly clear indicator that some value is created," but merges don't reflect partial successes
- Copyright concerns: AI-generated code ownership referencing US Copyright Office guidance

---

### Windsurf and Cursor feel like temporary stopgaps
**URL:** https://news.ycombinator.com/item?id=43904473

**Key Comments:**
- **Androider** (top comment): Microsoft will replicate features "within a year with greater stability and polish"; both tools "riddled with bugs" in context management; real future is "smarter teammates handling entire engineering tickets autonomously"
- **robinhood**: disputes "riddled with bugs" claim; six months daily Cursor use without blocking issues; Cursor tab autocompletion superior
- **kasey_junk**: VSCode with Copilot offers comparable functionality, especially with experimental reusable prompt file features
- **sanderjd**: skeptical about autonomous agents as primary development tools; "ideal UX remains contested"
- **dontlikeyoueith**: Microsoft's "greater stability and polish" seems "overly optimistic given MS's history" — Teams cited as cautionary precedent
- **dist-epoch**: Cursor $9B valuation exceeds JetBrains $7B
- Open source alternatives: Cline (1.4M downloads), Roo Code (450K downloads), Continue.dev, Aider

---

### Ask HN: How are people safely reusing LLM answers in production RAG systems?
**URL:** https://news.ycombinator.com/item?id=46820460
*(Note: page returned 429 on fetch; partial data from search summary)*

**Summary from search:** January 2026 discussion; correctness risks make various approaches scary in practice when source documents change or retrieval context shifts. Community concerned about stale cached answers and retrieval context drift.

---

## WEB SOURCES

### Vibe Coding Statistics 2026
**URL:** https://www.hostinger.com/blog/vibe-coding-statistics

Key data:
- 84% of developers use or plan to use AI coding tools (up from 76% in 2024)
- 90% of developers regularly use at least one AI tool at work as of January 2026
- Nearly 80% of new GitHub developers used Copilot within their first week
- 72% of developers say vibe coding is NOT part of their professional workflow
- AI code tools market projected to reach $22.2 billion by 2030 (23.8% CAGR)
- GitHub Copilot surpassed 20 million all-time users, growing 75% year-over-year
- Cursor reached $29.3 billion valuation with ARR exceeding $1 billion by November 2025
- Google: Over 30% of new code is AI-generated; Meta: ~50% target
- 29% of Python functions in US GitHub repositories were AI-generated by end of 2024
- "55.8% faster task completion" on specific tasks (controlled study)
- 26% increase in completed tasks in large RCT study
- 67% increase in merged pull requests at Anthropic (internal)
- Experienced developers were 19% slower with AI tools on mature codebases (METR study)
- 41% more bugs documented in one observational study
- AI-generated code: 1.7x more major issues than human-written
- 45% of AI-generated code samples fail OWASP Top-10 security benchmarks
- Developer trust dropped from ~40% (2024) to 29% (2025)
- 63% of vibe coding users are non-developers
- APAC leads global adoption at 40.7%
- Junior developer employment declined nearly 20% from late 2022 peak
- **Tomas Rasymas (Head of AI at Hostinger):** "The biggest factor isn't the tool. It's the review process around it."

---

### The State of Vibe Coding in 2026: Adoption Won, Now What?
**URL:** https://hashnode.com/blog/state-of-vibe-coding-2026

Key data:
- 92% of US developers use AI coding tools daily
- 82% of global developers use them weekly
- 46% of all new code is AI-generated
- 21% of Y Combinator's Winter 2025 cohort have codebases that are 91%+ AI-generated
- Developer favorability collapsed from 77% (2023) to 60% (2026)
- Only 33% trust AI code accuracy, down from 43% in 2024
- AI co-authored code contains 1.7x more major issues
- 45% of AI-generated code samples contain OWASP Top-10 vulnerabilities
- 63% of developers spent more debugging AI code than writing it would have taken
- Code churn increased 41%; code duplication rose 4x
- **METR Study:** Developers using AI tools were measurably 19% SLOWER yet believed they were 20% FASTER
- **Andrej Karpathy** definition: "You fully give in to the vibes, embrace exponentials, and forget that the code even exists"
- Where vibe coding succeeds: Prototyping/MVPs (20-45% faster), internal tools (60% dev time reduction), senior devs (81% gains)
- Testing infrastructure hasn't kept pace with AI-native development

---

### A New Worst Coder: Vibe Coding Without Code Knowledge
**URL:** https://stackoverflow.blog/2026/01/02/a-new-worst-coder-has-entered-the-chat-vibe-coding-without-code-knowledge/

Key quotes and findings:
- "While it may be a powerful tool in the hands of someone who knows what they're doing, in my hands it was like one of those AI filters that makes you look like a Studio Ghibli character: fun to post, but not actually substantive."
- "For a technology that is supposedly going to make junior developers obsolete, it needed a lot of help from my friends—all of whom are junior developers."
- "The mess of my code would be a problem in any of those situations...a developer would have had to come in after the fact to clean up everything."
- 66% of developers experience "productivity tax" when using coding tools
- Security vulnerabilities: app lacked protective measures, exposing stored data
- Code quality: messy, unorganized, lacking unit tests, poor component separation
- Best use case: learning, not replacement

---

### Vibe Coding in 2026: How AI Is Changing the Way Developers Write Code
**URL:** https://daily.dev/blog/vibe-coding-2026-ai-changing-how-developers-write-code

Key findings:
- 95% of developers report feeling productive while measurably producing lower-quality code
- 74% report productivity increases, yet subjective experience and objective measurement diverge
- AI co-authored code: 1.7x more major issues, logic errors, flawed control flow, misconfigurations (75% more common), security vulnerabilities (2.74x higher)
- "Vibe coding hangover" — Fast Company September 2025 report citing "development hell" from AI-generated code
- Best teams match tool to moment: vibe for early experiments, AI-assisted for systems that need to scale

---

### Cursor AI: The Only IDE You Need in 2026
**URL:** https://www.youtube.com/watch?v=ed26g7jxAbU (YouTube)

- Cursor v3.0 released early 2026: Background Agents, Cloud Agents, Composer 2.0
- Over 1 million users, 360,000 paying customers in 16 months
- Pricing: Free, Pro ($20/month), Business ($40/user/month)
- Cursor Composer 2 scores 61.3 on CursorBench (37% improvement over Composer 1.5)
- 73.7 on SWE-bench Multilingual

---

### Cursor: Coding Agents Tutorial (2026)
**URL:** https://www.youtube.com/watch?v=kF2WQgk1LtY

- Covers building software with agents: planning new features, fixing bugs, reviewing and testing code

---

### Cursor AI Tutorial for Beginners: Build App with AI (2026)
**URL:** https://www.youtube.com/watch?v=oQDCAJnr1aU

---

### GitHub Copilot 2026: Complete Guide
**URL:** https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents

Key findings:
- Agent mode available in VS Code and JetBrains as of March 2026
- Determines which files to edit, runs terminal commands, iterates on errors without manual intervention
- Initialization phase reduced from ~40 seconds to ~20 seconds
- Semantic code search added: find conceptually related code without specifying file path
- Copilot "no longer the most powerful AI coding tool, but still the best value"
- GitHub Copilot: 81% of users notice productivity boosts for coding and testing tasks
- Surpassed 20 million all-time users, growing 75% year-over-year

---

### Windsurf Acquisition and the 2026 AI IDE Market Shakeup
**URL:** https://antigravitylab.net/en/articles/ai-tools/ai-ide-market-windsurf-acquisition-2026

Key facts:
- OpenAI announced ~$3B acquisition of Codeium/Windsurf (May 2025) — deal fell through
- Google hired Windsurf's CEO, co-founder, and ~40 senior engineers
- Cognition (maker of Devin) acquired remaining company: IP, product, brand, 210 employees, $82M ARR
- As of February 2026, Windsurf ranks #1 in LogRocket AI Dev Tool Power Rankings
- March 2026: 1M+ active users, 70M+ lines of code written by AI daily, 59% of Fortune 500 companies building with it
- Roadmap: merging Cascade IDE intelligence with Devin autonomous execution
- SWE-1.5 model integrated

---

### AI Observability: The Complete Guide 2026
**URL:** https://uptimerobot.com/knowledge-hub/observability/ai-observability-the-complete-guide/

Key insights:
- Without advanced observability, AI systems will be "effectively ungovernable at scale"
- AI systems exhibit non-deterministic behavior — predefined monitoring thresholds cannot capture variability
- Data drift and concept drift as key failure modes
- By 2026, observability increasingly serves three control functions: operational, governance, and compliance

---

### The AI Reliability Problem in Production: A 2026 Field Guide
**URL:** https://logiciel.io/blog/ai-reliability-problem-demo-vs-production-2026

Key quotes and data:
- "Availability without quality is not reliability for AI"
- "A system that is up but returning wrong answers is not reliable"
- "Operating discipline is the difference between fragile and reliable"
- One attribution error caused a 22% pipeline drop (real estate SaaS case study)
- Four dimensions: Availability, Quality, Detectability, Recoverability
- Failure modes: hallucinations, drift, prompt injection, partial outputs undetected by standard monitoring
- High-performing teams: continuous daily eval blocking regressions, quarterly rollback testing, weekly reliability reviews

---

### LLM Failure Modes in Production: Complete Root Cause Guide (2026)
**URL:** https://appscale.blog/en/blog/llm-failure-modes-in-production-the-complete-root-cause-guide-2026

8 core failure modes:
1. Prompt and Instruction Fragility — Sensitivity to input variations
2. Retrieval and Context Failure — Information lookup and context quality issues
3. Hallucination and Grounding Failure — Factual accuracy and reality alignment problems
4. Latency, Throughput, and Rate-Limit Instability — Performance and scaling challenges
5. Tool, Agent, and Workflow Orchestration Failure — Multi-step process breakdown
6. Safety, Policy, and Guardrail Failure — Security and compliance violations
7. Observability and Evaluation Blind Spots — Monitoring and assessment gaps
8. Cost Escalation and Reliability Tradeoff Failure — Economic sustainability issues

Core insight: "Why do LLM systems that work in demos fail in production?" — System-level architecture, not model capability, determines real-world success.

---

### The LLM Context Problem in 2026
**URL:** https://blog.logrocket.com/llm-context-problem-strategies-2026/

4 Critical Context Failure Modes:
1. **Context Poisoning**: False information reinforced over time
2. **Context Distraction**: Models degrade when context exceeds ~100k tokens
3. **Context Confusion**: Irrelevant information skews responses — models fail 46-tool tasks but succeed with 19 tools
4. **Context Clash**: OpenAI's o3 fell from 98.1% to 64.1% accuracy with contradictory multi-turn context

6 Evidence-Based Techniques:
- RAG Still Works despite larger context windows
- Dynamic Tool Selection: Limit to ~30 tools max; 44% performance gains achieved
- Context Quarantine: Isolated subagents prevent information pollution
- Intelligent Pruning: Compress documents up to 95% while retaining relevance
- Conversation Summarization at 32k–100k token thresholds
- Scratchpad Pattern: 54% benchmark improvement from intermediate reasoning offloading

---

### Effective Context Engineering for AI Agents (Anthropic)
**URL:** https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents

Key quotes and principles:
- "As the number of tokens in the context window increases, the model's ability to accurately recall information from that context decreases."
- "For an LLM, examples are the 'pictures' worth a thousand words."
- "Find the smallest set of high-signal tokens that maximize the likelihood of your desired outcome."
- Three complementary long-horizon strategies: Compaction (summarize/reset), Structured Note-Taking (persistent memory), Sub-Agent Architectures
- Transformer architecture's n² pairwise token relationships create inherent attention scarcity
- Tools should be self-contained, clearly defined, efficient at returning token-light information

---

### AI Context Engineering in 2026: Why Prompt Engineering Is No Longer Enough
**URL:** https://sombrainc.com/blog/ai-context-engineering-guide

Key insights:
- Context engineering emerged mid-2025 as evolutionary successor to prompt engineering
- Discipline split: casual prompting (accessible to anyone) vs. production context engineering (genuine engineering skill)
- Best practice: "treat context as infrastructure, not a prompt file"
- Log which documents were retrieved, or which profile data was injected, for each answer
- Good context engineering: "smallest possible set of high-signal tokens that maximize the likelihood of some desired outcome"
- Pin production apps to specific model snapshots (e.g., gpt-5-2025-08-07) — router behaviour changes between versions

---

### Context Engineering: The Next Frontier Beyond Prompt Engineering (deepset)
**URL:** https://www.deepset.ai/blog/context-engineering-the-next-frontier-beyond-prompt-engineering

- LangChain breaks context engineering into four buckets: Write, Select, Compress, Isolate
- Three types of agent context: Domain knowledge (RAG), Tool Data (MCP), functional tools
- Agentic RAG flips the relationship — model actively decides what to look up, when, and how to combine it
- "Separates hobby chatbots from reliable AI products" in 2026

---

### RAG at Scale: How to Build Production AI Systems in 2026
**URL:** https://redis.io/blog/rag-at-scale/

Key findings:
- RAG prototypes that work with small test sets break at millions of vectors and thousands of concurrent queries
- Combining 5 hallucination reduction techniques can reduce hallucinations from 20% to 2–5%
- Graceful degradation options: full RAG, lite RAG, direct LLM, cached response
- NVIDIA's RULER benchmark: models reliably use only 50-65% of advertised context window

---

### LLM Failure Modes (RAG-specific): I Discovered RAG Has Exactly 6 Failure Modes
**URL:** https://javarevisited.substack.com/p/why-rag-has-exactly-6-failure-modes

---

### Long-Context Models vs. RAG: When the 1M-Token Window Is the Wrong Tool
**URL:** https://tianpan.co/blog/2026-04-09-long-context-vs-rag-production-decision-framework

---

### SWE-bench Leaderboard 2026
**URL:** https://benchlm.ai/benchmarks/sweVerified
**URL:** https://www.codeant.ai/blogs/swe-bench-scores

Key data (as of May 13, 2026):
- Claude Mythos Preview: 93.9% (leads)
- Claude Opus 4.7 (Adaptive): 87.6%
- GPT-5.3 Codex: 85%
- Claude Opus 4.6 (SWE-bench Verified): 80.8%
- GPT-5.2: 80.0%
- Average across 83 evaluated models: 63.4%
- 37% gap between lab benchmark scores and real-world deployment performance
- 50x cost variation for similar accuracy

Terminal-Bench (May 2026):
- GPT-5.5: 82.7%
- Claude Opus 4.7: 69.4%

SWE-bench Pro:
- Claude Opus 4.7: 64.3% (leads on long-horizon work)
- GPT-5.5: 58.6%

---

### AI Benchmarks 2026: Top Evaluations and Their Limits
**URL:** https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough

Key findings:
- 15 major benchmarks in active use in 2026
- Only 4 reliably predict real production outcomes
- MMLU and MMLU-Pro functionally saturated above 88% for frontier models
- Humanity's Last Exam: AI models ~35% vs human domain experts ~90%

---

### Top AI Pair Programming Statistics 2026
**URL:** https://www.index.dev/blog/ai-pair-programming-statistics

Key data:
- 92% of US developers use AI as a "daily companion"
- 82% agree AI helps code faster; 71% say it helps solve complex problems more efficiently
- 96% of developers don't fully trust AI-generated code is functionally correct
- 11.4 hours/week reviewing AI-generated code vs. 9.8 hours writing new code (reversed pattern from 2024)
- Claude Code (28%) and Cursor (24%) account for 52% of primary-tool selections
- Most developers run a three-tool stack rather than committing to one

---

### State of Code Developer Survey 2026
**URL:** https://www.sonarsource.com/state-of-code-developer-survey-report.pdf

Referenced in searches; covers AI coding tool adoption patterns.

---

### GitHub Trending Repositories 2026
**URLs:** https://blog.bytebytego.com/p/top-ai-github-repositories-in-2026, https://ossinsight.io/trending/ai

Key trending repos:
- **OpenClaw**: Surged from 9k to 210k+ stars after going viral (Jan 2026) — personal AI agent platform
- **Karpathy's CLAUDE.md**: 110k+ stars in 3 months — seventy-line file from Andrej Karpathy's X post (Jan 26, 2026)
- **mattpocock/skills**: +1,618 stars in one week (May 9-15, 2026)
- **Langflow** (146k stars), **Dify** (136k), **Flowise** (51k) — visual AI agent builders dominate
- **Ollama**: Lightweight Go framework for running LLMs locally
- **awesome-ai-agents-2026**: Multiple repos with curated AI agent lists
- Everything Claude Code repo (built at Cerebral Valley x Anthropic hackathon, Feb 2026)

---

### Polymarket: Which Company Has Best Coding AI Model End of April 2026?
**URL:** https://polymarket.com/event/which-company-has-the-best-coding-ai-model-end-of-april

- **Resolved market**: Anthropic won at 100% implied probability
- Volume: $266,154
- Resolution: Claude Opus 4.7 achieved top ranking on Chatbot Arena Coding leaderboard (April 30, 2026)
- All other companies (OpenAI, Google, xAI, DeepSeek, etc.) at <1%

---

### 2026 Prediction: Observability Becomes the Control Plane for AI
**URL:** https://www.efficientlyconnected.com/2026-predictions-observability-becomes-the-control-plane-for-ai-operations/

- Agentic AI introducing "exponential complexity" — single customer interaction may trigger hundreds of background agent conversations
- Observability increasingly serves: operational control, governance, compliance control functions
- Automated actions from telemetry: throttling, rollback, isolation, escalation when AI behavior deviates

---

### Building Production RAG Systems in 2026
**URL:** https://brlikhon.engineer/blog/building-production-rag-systems-in-2026-complete-tutorial-with-langchain-pinecone

- RAG architecture decisions across 10+ layers: embedding models, chunking, retrieval, reranking, observability
- 5 hallucination reduction techniques combined: reduce from 20% to 2–5%

---

### AGENTS.md: The De Facto Standard for AI Coding Agents
**URL:** https://blog.buildbetter.ai/agents-md-complete-guide-for-engineering-teams-in-2026/

- Read natively by Claude Code, OpenAI Codex CLI, Cursor, Aider, Devin, GitHub Copilot, Gemini CLI, Windsurf, Amazon Q
- Provides structure for instructing AI coding agents at the project level

---

### Claude Code vs Cursor (2026)
**URL:** https://emergent.sh/learn/claude-code-vs-cursor

- Claude Code: terminal-first, project-level autonomous agent
- Cursor: IDE-native, deep editing integration
- Pattern: pair IDE assistant with terminal agent for big jobs; most heavy users combine two tools

---

### Best AI Coding Assistants 2026: Cursor vs Copilot vs Claude Code
**URL:** https://scrimba.com/articles/best-ai-coding-assistants-2026/

---

### AI Coding Tool Adoption 2026: Developer Survey Results
**URL:** https://www.digitalapplied.com/blog/ai-coding-tool-adoption-2026-developer-survey

- Claude Code reached 40.8% in 2025 Stack Overflow survey (went from launch to mainstream in under a year)

---

### DeveloperWeek 2026: Making AI Tools That Are Actually Good
**URL:** https://stackoverflow.blog/2026/03/05/developerweek-2026/

---

### Bluesky: Attie AI App for Custom Feeds
**URL:** https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/

- Attie: Bluesky AI assistant powered by Anthropic's Claude (agentic social app on ATProto)
- Users write natural-language prompts to create social feeds without coding
- Plan: allow Attie's users to "vibe-code" their own social apps

---

### Beyond the Commit: Developer Perspectives on Productivity with AI Coding Assistants
**URL:** https://arxiv.org/html/2602.03593v1

Academic paper; covers developer experiences with AI coding tools in production contexts.

---

### From RAG to Context: 2025 Year-End Review
**URL:** https://ragflow.io/blog/rag-review-2025-from-rag-to-context

- RAG evolving from specific pattern to "Context Engine" with intelligent retrieval as core capability
- Context engineering became "hottest technical exploration" in H2 2025
- Focus: dynamically and intelligently assembling effective context for different tasks at different moments

---

## NOTES ON DATA COLLECTION
- Reddit.com: blocked (API Error 400, not accessible to Anthropic crawler)
- X/Twitter: not searched per instructions
- TikTok: no direct data retrieved
- Instagram: no direct data retrieved
- YouTube: Confirmed titles/URLs but could not extract view counts/likes (YouTube page rendering issue)
- Polymarket: One resolved market retrieved with full data
- GitHub: Trending repo data retrieved via third-party sources (OSSInsight, ByteByteGo)
