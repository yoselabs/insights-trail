# AI Dev Practice — Raw Research Data
**Date:** 2026-05-21
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## NOTE: Reddit Unavailable
Reddit.com is not accessible to the WebSearch crawler (HTTP 400). No Reddit data collected.

---

## HACKER NEWS

### Thread 1: Ask HN: Cursor or Windsurf?
- **URL:** https://news.ycombinator.com/item?id=43959710
- **Score:** 316 points
- **Comments:** 398
- **Key discussion:**
  - Cursor strengths: Tab-complete is "great and better than any other I've used"; fast autocomplete that understands context; unlimited usage model after trial
  - Cursor weaknesses: Context truncation concerns for cost savings; autocomplete incorrect ~50% for complex language features
  - Windsurf strengths: Lower pricing, generous free tier, run multiple "flows" in parallel, better project awareness across files
  - Windsurf weaknesses: Restricted to reading only 50-200 lines at a time; struggles with files over 800 lines; autocomplete quality inferior to Cursor
  - Several commenters advocate for Zed as alternative; aider mentioned for Python projects

### Thread 2: Windsurf and Cursor feel like temporary stopgaps
- **URL:** https://news.ycombinator.com/item?id=43904473
- **Score:** Not captured (rate limited)
- **Key discussion:**
  - Original argument (Androider): Microsoft would replicate features within a year while delivering superior stability; both tools have implementation bugs
  - Counter: Cursor provides meaningful advantages in autocomplete and context management that VSCode hasn't matched
  - "Not sucking" became a genuine differentiator - Cursor's bracket-matching and multi-file context management exceeded GitHub Copilot
  - Skeptics question whether Microsoft can deliver: "Microsoft's development tools team has succeeded with VSCode but represents an exception rather than the rule"

### Thread 3: Ask HN: How much better are AI IDEs vs. copy pasting into chat apps?
- **URL:** https://news.ycombinator.com/item?id=43922759
- **Score:** 139 points
- **Comments:** 136
- **Key discussion:**
  - Context management advantage: "The context is already in my codebase, so the AI should pick up on it"
  - Cursor $20/month unlimited appeals to many
  - Developers distinguish use cases: chat interfaces for deep problem-solving, IDE for refactoring/boilerplate
  - One engineer: uses Cursor for "basics" but ChatGPT for "tough problems"
  - AI IDEs sometimes struggle with large codebases; automatic context selection can miss critical files

### Thread 4: How vibe coding is killing open source
- **URL:** https://news.ycombinator.com/item?id=46876455
- **Score:** 84 points
- **Comments:** 62
- **Key discussion:**
  - Optimistic: barrier to entry decreasing means more participation
  - Skeptical (arjie): LLM-generated contributions eliminate pressure to contribute upstream; verbose PRs for resume-padding
  - Contributor burnout: "I did not consent with it being a gift to a for-profit company" (dom96/honestduane)
  - Counter (nberkman): Experienced developers now shipping shelved projects; Clippy reaching 200 GitHub stars through AI assistance
  - Infrastructure challenge (pjjpo): quality projects struggle for visibility as Show HN saturated

### Thread 5: Ask HN: Client took over development by vibe coding. What to do?
- **URL:** https://news.ycombinator.com/item?id=47599303
- **Score:** 63 points
- **Comments:** 42
- **Key discussion:**
  - Client added ~10,000 lines of code in one week via AI agents; functional but degrading performance and maintainability
  - "Prepare to make absolute bank on maintenance charges when they can't debug what they built"
  - Multiple commenters shared similar experiences with clients abandoning professional developers for AI
  - Consensus: software maintenance—not initial coding—represents the true cost of development
  - "if the client stops trusting your judgment, the relationship is already broken"

### Thread 6: Ask HN: How far has "vibe coding" come?
- **URL:** https://news.ycombinator.com/item?id=46807308
- **Score:** 13 points
- **Comments:** 26
- **Key discussion:**
  - Non-technical founder built production SaaS frontend via vibe coding; focused on "system architecture, user flows, and business logic"
  - Developer launched iOS app over 4-5 months, "never reviewed or read code in detail"
  - Core tension: vibe coding breaks down with performance, security, and scalability decisions
  - "Success depends less on code volume than on understanding what to build and maintaining proper modularity"

### Thread 7: Show HN: Free local security checks for AI coding in VSCode, Cursor and Windsurf
- **URL:** https://news.ycombinator.com/item?id=44309393
- **Score:** 43 points
- **Comments:** 22
- **Tool:** Codacy Guardrails
- **Key discussion:**
  - "40% of Copilot's outputs were buggy or exploitable" (NYU research cited)
  - Uses Semgrep, Trivy against 2000+ rules; covers OWASP Top 10, hardcoded secrets
  - Operates locally without AI models using classic static analysis
  - AI assistants frequently introduce CVEs due to training data cutoffs
  - Claude Code integration planned

### Thread 8: Vibe Coding: Developer Slot Machines (Cursor, Windsurf)
- **URL:** https://news.ycombinator.com/item?id=43830198
- **Score:** Rate limited, could not fetch

### Thread 9: Ask HN: Why do Cursor, Windsurf and Claude Code dominate the conversation?
- **URL:** https://news.ycombinator.com/item?id=44635075
- **Score:** Rate limited, could not fetch
- **Summary from search:** Dominance due to mindshare; newcomers face significant inertia against major incumbents

### Thread 10: RAG Systems on HN
- **URL:** https://news.ycombinator.com/item?id=46820460 (How are people safely reusing LLM answers in production RAG systems?)
- **Score:** Rate limited, could not fetch
- **URL:** https://news.ycombinator.com/item?id=45645349 (Production RAG: what I learned from processing 5M+ documents)
- **Key summary:** SPLADE v3 models for balance of semantic and lexical retrieval; chunk re-ranking and contextual summaries major driver of performance

### Additional HN items found (not fetched):
- "2026: The Year the IDE Died and Gene Kim, Authors, Vibe Coding [video]" - https://news.ycombinator.com/item?id=46180887
- "Vibe coding is a hobby. Let me explain" - https://news.ycombinator.com/item?id=46692284
- "Vibe coding is a real job now" - https://news.ycombinator.com/item?id=47401666
- "Breaking the spell of vibe coding" - https://news.ycombinator.com/item?id=47006615
- "Vibe Coding Simulator 2026" - https://news.ycombinator.com/item?id=47052876
- "It looks vibe coding...has been challenging a few employees" - https://news.ycombinator.com/item?id=47665813
- "A practical 2026 roadmap for modern AI search and RAG systems" - https://news.ycombinator.com/item?id=46553519

---

## WEB SOURCES

### The Shift from Vibe Coding to Agentic Engineering

**Source:** AIntelligenceHub - Karpathy on AI Coding Moving from Vibe Prompts to Agent Workflows
**URL:** https://aintelligencehub.com/articles/karpathy-vibe-coding-to-agent-workflows-may-2026
- Karpathy proposed "agentic engineering" replacing "vibe coding"
- Vibe coding = describing what you want and accepting what comes back
- Agentic engineering = designing the system, specifying constraints, using AI to accelerate implementation you have already reasoned through
- Quote: "AI assistants move from autocomplete helpers to semi-autonomous execution partners"
- Quote: "Product delivery is rarely one prompt and one answer. It is loops, review, retries, and coordination."
- Key risks: invisible drift between intent and implementation; permission sprawl; agent behavior variance across context windows
- At AI Ascent 2026, Karpathy framed the shift from one-shot prompt coding toward agentic engineering workflows

**Source:** SD Times - Karpathy Has Renamed Vibe Coding
**URL:** https://sdtimes.com/ai/andrej-karpathy-has-renamed-vibe-coding-heres-what-engineering-leaders-need-to-do-about-it/

**Source:** Karpathy's Sequoia Ascent 2026 notes
**URL:** https://karpathy.bearblog.dev/sequoia-ascent-2026/

**Source:** Multiple articles on the evolution
- https://letsdatascience.com/news/karpathy-explains-vibe-coding-to-agentic-engineering-2d34b5c2
- https://agenticmsp.substack.com/p/from-vibe-coding-to-agentic-engineering-919
- https://www.franksworld.com/2026/05/01/andrej-karpathy-on-the-evolution-from-vibe-coding-to-agentic-engineering/
- https://aiagentssimplified.substack.com/p/from-vibe-coding-to-agentic-engineering
- Karpathy's "loopy era": designing loops that keep useful work moving without a human prompting every next step

### Vibe Coding vs Agentic Coding vs Context Engineering

**Source:** QA Source
**URL:** https://www.qasource.com/blog/vibe-coding-vs-agentic-coding-vs-context-engineering
- Vibe Coding: minimal context, rapid prototyping
- Agentic Coding: autonomous AI plans, codes, tests, debugs across multiple files simultaneously
- Context Engineering: structured information architecture guiding AI toward accurate, repo-aware outputs
- Critical insight: "AI is not reducing engineering risk. It is redistributing it from code creation to code validation, governance, and system stability."
- Cortex 2026 Benchmark Report: PRs per author grew 20% annually while change failure rates climbed 30% yearly
- Key risks of vibe coding: loss of architectural awareness; context fragmentation; erosion of code ownership; technical debt accumulation; happy-path bias

**Source:** Google Cloud - What is Vibe Coding
**URL:** https://cloud.google.com/discover/what-is-vibe-coding

**Source:** dev.to - Vibe Coding in 2026
**URL:** https://dev.to/pockit_tools/vibe-coding-in-2026-the-complete-guide-to-ai-pair-programming-that-actually-works-42de

**Source:** DasRoot - Vibe Coding AI DevOps 2026
**URL:** https://dasroot.net/posts/2026/04/vibe-coding-ai-devops-2026/
- "One Prompt to Build, One Day to Fix"

### IDE Tool Landscape: Cursor vs Windsurf vs Claude Code vs Copilot

**Source:** NxCode - Best AI Code Editor 2026
**URL:** https://www.nxcode.io/resources/news/best-ai-code-editor-2026-cursor-windsurf-copilot-zed-compared

**Source:** Lushbinary - AI Coding Agents 2026 Comparison
**URL:** https://lushbinary.com/blog/ai-coding-agents-comparison-cursor-windsurf-claude-copilot-kiro-2026/
- As of May 2026: Cursor 3 with Composer 2.5 has most polished IDE-native parallel agent experience + largest community
- Windsurf 2.0 bundles Devin cloud agent directly inside editor for one-click delegation to remote VM
- 91% of engineering organizations have adopted at least one AI coding tool

**Source:** Dev.to - Cursor vs Windsurf vs Claude Code 2026
**URL:** https://dev.to/pockit_tools/cursor-vs-windsurf-vs-claude-code-in-2026-the-honest-comparison-after-using-all-three-3gof

**Source:** Vibecodingacademy - Windsurf vs Cursor
**URL:** https://www.vibecodingacademy.ai/blog/windsurf-vs-cursor

**Source:** NxCode - Windsurf vs Cursor 2026
**URL:** https://www.nxcode.io/resources/news/windsurf-vs-cursor-2026-ai-ide-comparison

**Source:** Daily.dev - Cursor vs VS Code vs Windsurf
**URL:** https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison/

**Source:** Daily.dev - Vibe Coding How AI Is Changing Developers
**URL:** https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code/
- 92% of US developers use AI coding tools daily in 2026
- Cursor represents iterative, controlled AI collaboration (AI as pair programmer)
- Windsurf represents autonomous AI execution where developer describes goals (AI as autonomous agent)

**Source:** Appwrite - Comparing vibe coding tools
**URL:** https://appwrite.io/blog/post/comparing-vibe-coding-tools

**Source:** Second Talent - Windsurf Review 2026
**URL:** https://www.secondtalent.com/resources/windsurf-review/

**Source:** Medium - Cursor, Claude Code, Windsurf AI stack
**URL:** https://medium.com/@dev_tips/cursor-claude-code-windsurf-my-ai-coding-stack-after-40-dev-experiments-e6128788f89c

### GitHub Copilot Agent Mode

**Source:** GitHub Blog - From pair to peer programmer
**URL:** https://github.blog/news-insights/product-news/from-pair-to-peer-programmer-our-vision-for-agentic-workflows-in-github-copilot/

**Source:** .NET Blog - Ten Months with Copilot Coding Agent in dotnet/runtime
**URL:** https://devblogs.microsoft.com/dotnet/ten-months-with-cca-in-dotnet-runtime/
- 878 total CCA PRs over 10 months (May 2025–March 2026)
- 535 merged (67.9% success rate), ~95,000 lines added, 31,000 removed
- Human PRs: 87.1% merge rate; community contributors: 79.7%
- Success climbed from 41.7% in May 2025 to 71-72% by January 2026
- By task type: Removal/Cleanup 84.7%; Testing 75.6%; Refactoring 69.7%; Bug Fixes 69.4%; Performance 54.5%
- Critical finding: Setup with .github/copilot-instructions.md jumped success from 38.1% to 69%
- 52.3% of merged CCA PRs received direct commits from humans (vs 10.3% for human PRs)
- Merged CCA PRs: avg 16.5 review comments vs 12.4 for human PRs
- Revert rate for CCA PRs: 0.6% vs 0.8% for non-CCA
- Key pattern: One lead contributor shifted from 95% personal PRs to 77% CCA-authored by year-end
- Quote: "Instead of spending hours implementing fixes myself, I spend minutes triaging issues, reviewing CCA's output."

**Source:** Tossitt - GitHub Copilot Guide 2026
**URL:** https://tossitt.com/github-copilot-guide-2026/
- Agent mode is the headline 2026 feature: picks files itself, runs terminal commands, watches test suite, re-prompts itself when things break

**Source:** GitHub Copilot CLI combines model families
**URL:** https://github.blog/ai-and-ml/github-copilot/github-copilot-cli-combines-model-families-for-a-second-opinion/
- Claude Sonnet + Rubber Duck makes up 74.7% of the performance gap between Sonnet and Opus

**Source:** Beginners in AI - GitHub Copilot Review 2026
**URL:** https://beginnersinai.org/github-copilot-review/

**Source:** Fundesk - GitHub Copilot Agent Mode Guide 2026
**URL:** https://www.fundesk.io/github-copilot-agent-mode-guide-2026

### Context Engineering Best Practices

**Source:** Packmind - Context Engineering Best Practices
**URL:** https://packmind.com/context-engineering-ai-coding/context-engineering-best-practices/
- Human-written context files improve task resolution by avg 4%
- LLM-generated context files reduce performance by 3% AND increase inference cost 20%+
- Use H2/H3 structure; bullet lists for rules; code blocks with preferred vs avoided patterns
- Metadata block at top helps AI decide whether content is worth reading
- Minimum viable starter pack: tech stack, 3-5 critical conventions, build/test commands, one non-obvious architectural decision

**Source:** Faros.ai - Context Engineering for Developers
**URL:** https://www.faros.ai/blog/context-engineering-for-developers

**Source:** Packmind - Context Engineering Large Codebases
**URL:** https://packmind.com/context-engineering-ai-coding/context-engineering-large-codebases/

**Source:** Vibehackers - Context Engineering Guide
**URL:** https://vibehackers.io/blog/context-engineering-guide

**Source:** Instinctools - Context Engineering
**URL:** https://www.instinctools.com/blog/context-engineering/

**Source:** MLMastery - Effective Context Engineering for AI Agents
**URL:** https://machinelearningmastery.com/effective-context-engineering-for-ai-agents-a-developers-guide/
- What breaks: Context drift (outdated files), Prompt-only approaches, Lack of governance
- AI-generated PRs wait 4.6x longer in review without governance frameworks
- AI-generated code introduces 15-18% more security vulnerabilities as autonomy expands

### AI Productivity Research

**Source:** METR - Measuring Self-Reported Impact of AI on Technical Worker Productivity (May 2026)
**URL:** https://metr.org/blog/2026-05-11-ai-usage-survey/
- 349 technical workers surveyed
- Median self-reported 1.4–2x value change from AI tools; 3x speed change
- Temporal trend: 1.3x in March 2025 → 2x currently → anticipated 2.5x by March 2027
- Caveat: "survey results are not necessarily grounded in reality"; previous findings showed 40-point overestimation
- METR staff reported lowest value gains of all groups

**Source:** METR - Changing Developer Productivity Experiment Design (Feb 2026)
**URL:** https://metr.org/blog/2026-02-24-uplift-update/
- Original 2025 RCT: 16 developers, 19% slower with AI (while believing 20% faster)
- 2026 update: 30-50% of invited developers declined to participate without AI access (selection bias)
- Newer cohort (800+ tasks, 57 developers): -4% slowdown, CI of -15% to +9%
- METR believes developers are more sped up by AI tools in early 2026 vs. early 2025

**Source:** Faros.ai - The AI Productivity Paradox
**URL:** https://www.faros.ai/blog/ai-software-engineering

**Source:** Index.dev - Developer Productivity Statistics 2026
**URL:** https://www.index.dev/blog/developer-productivity-statistics-with-ai-tools
- 92% of developers use AI in some part of workflow
- Average productivity increase reported: 31.4%
- 41% of code written in 2025 is AI-generated

**Source:** MIT Technology Review - AI coding is now everywhere
**URL:** https://www.technologyreview.com/2025/12/15/1128352/rise-of-ai-coding-developers-2026/

**Source:** Panto.ai - AI Coding Productivity Statistics 2026
**URL:** https://www.getpanto.ai/blog/ai-coding-productivity-statistics
- Market projected from $5.5B in 2024 to $47.3B by 2034

**Source:** JetBrains Research - AI Impact on Developer Workflows (April 2026)
**URL:** https://blog.jetbrains.com/research/2026/04/ai-impact-developer-workflows/

### The AI Coding Hangover / Technical Debt

**Source:** InfoWorld - The AI Coding Hangover
**URL:** https://www.infoworld.com/article/4141358/the-ai-coding-hangover.html
- Quote: "Software will soon be free...enterprises can shed developers, point an LLM at a backlog, and crank out custom business systems"
- Quote: "They didn't eliminate cost or complexity. They just moved it, multiplied it, and buried it under layers of unmaintainable generated code."
- Quote: "AI-generated code is often inefficient...over-allocates, over-abstracts, duplicates logic, and misses optimization opportunities"
- Operational costs (cloud compute, storage, incident response) exceed payroll savings
- Organizations quietly rehiring developers as platform/AI engineers

**Source:** InfoWorld - Is vibe coding the new gateway to technical debt?
**URL:** https://www.infoworld.com/article/4098925/is-vibe-coding-the-new-gateway-to-technical-debt.html

**Source:** InfoWorld - Vibe coding or spec-driven development?
**URL:** https://www.infoworld.com/article/4166817/vibe-coding-or-spec-driven-development-how-to-choose.html

**Source:** InfoWorld - The reckless temptation of AI code generation
**URL:** https://www.infoworld.com/article/4154587/the-reckless-temptation-of-ai-code-generation.html

**Source:** Pixelmojo - The AI Coding Technical Debt Crisis: 2026-2027
**URL:** https://www.pixelmojo.io/blogs/vibe-coding-technical-debt-crisis-2026-2027
- Vibe coding: 84% adoption, 29% trust, 45% vulnerabilities

**Source:** CIO - Vibe coding goes enterprise
**URL:** https://www.cio.com/article/4166672/vibe-coding-goes-enterprise-what-you-need-to-know-about-ai-driven-legacy-modernization.html

**Source:** Elektor Magazine - 2026 AI Odyssey Hangover
**URL:** https://www.elektormagazine.com/articles/2026-an-ai-odyssey-vibe-coding-hangover

**Source:** Developer Tech - Curing the AI Party Hangover
**URL:** https://www.developer-tech.com/news/software-development-in-2026-curing-ai-party-hangover/

### LLMs in Production & RAG

**Source:** MarsDevs - What Is RAG in AI 2026 Production Guide
**URL:** https://www.marsdevs.com/blog/what-is-rag-in-ai-the-2026-production-guide
- RAG reduces hallucinations 60-80% in well-built systems, but not to zero
- Hallucinations still occur when retrieved context is ambiguous, LLM extrapolates beyond data, or retrieval fails silently
- LangChain and LlamaIndex remain dominant RAG orchestration frameworks
- LangChain's 2026 State of AI Agents report: 57% of organizations have agents in production; quality cited as top barrier by 32%

**Source:** Maxim.ai - 5 Best RAG Evaluation Tools 2026
**URL:** https://www.getmaxim.ai/articles/the-5-best-rag-evaluation-tools-you-should-know-in-2026/

**Source:** BuildFastWithAI - LLMOps & RAG Evaluation Tools 2026
**URL:** https://www.buildfastwithai.com/blogs/collection/llmops-rag-evaluation

### AI Observability & LLMOps

**Source:** Confident AI - Top 7 LLM Observability Tools
**URL:** https://www.confident-ai.com/knowledge-base/compare/top-7-llm-observability-tools

**Source:** Confident AI - 10 LLM Observability Tools 2026
**URL:** https://www.confident-ai.com/knowledge-base/compare/10-llm-observability-tools-to-evaluate-and-monitor-ai-2026

**Source:** Cekura - What Is LLM Observability Complete Guide 2026
**URL:** https://www.cekura.ai/blogs/llm-observability
- LLM observability market: $2.69B in 2026, projected $9.26B by 2030 at 36.2% CAGR
- Quote: "The response can be fast, on-brand, and still wrong — hallucinated, unsafe, or faithful to the wrong context."
- Quote: "Without observability that scores behavior, not just traffic, you are monitoring infrastructure while your product quality drifts in silence."
- Gartner: LLM observability investments will account for 50% of GenAI deployments by 2028 (vs 15% in early 2026)

**Source:** Rootly - Top AI Observability Trends 2026
**URL:** https://rootly.com/sre/top-ai-observability-trends-shaping-2026-ops-teams-c8456

**Source:** Nallas - LLMOps Strategy from AI Demos to Production
**URL:** https://nallas.com/llmops-strategy-explained/

**Source:** OneReach - LLMOps for AI Agents
**URL:** https://onereach.ai/blog/llmops-for-ai-agents-in-production/

**Source:** LangWatch - 4 Best Tools for Monitoring LLM Applications
**URL:** https://langwatch.ai/blog/4-best-tools-for-monitoring-llm-agentapplications-in-2026

**Source:** TrueFoundry - 10 Best AI Observability Platforms 2026
**URL:** https://www.truefoundry.com/blog/best-ai-observability-platforms-for-llms-in-2026

**Source:** LevelUp.gitconnected - What is LLM Observability Complete Guide 2026
**URL:** https://levelup.gitconnected.com/what-is-llm-observability-the-complete-guide-2026-e2fd2969b036

### AI Evaluation & Benchmarks

**Source:** Kili Technology - AI Benchmarks Guide 2026
**URL:** https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough
- MMLU and MMLU-Pro saturated above 88% for frontier models
- 37% gap between lab benchmark scores and real-world deployment performance
- Enterprise AI agents: accuracy drops from 60% on single run to 25% across 8 consecutive runs
- Annotation error rates in popular benchmarks exceed 50%
- Over 70% of computer vision datasets reused content from other domains
- Models sometimes game evaluations (timer rewriting example)
- Humanity's Last Exam: top models at 37.5% while human domain experts average 90%
- Production-ready eval requires: automated metrics + LLM-as-a-judge + human expert review

**Source:** arXiv - Towards a Science of AI Agent Reliability
**URL:** https://arxiv.org/pdf/2602.16666
- 12 metrics across four dimensions: consistency, robustness, predictability, and safety
- Recent capability gains yield only small improvements in reliability

**Source:** arXiv - When AI Benchmarks Plateau
**URL:** https://arxiv.org/pdf/2602.16763
- Saturation analyzed across 60 LLM benchmarks

**Source:** arXiv - Failure Modes in LLM Systems: A System-Level Taxonomy
**URL:** https://arxiv.org/pdf/2511.19933

**Source:** arXiv - ReliabilityBench
**URL:** https://arxiv.org/pdf/2601.06112
- Evaluates agent reliability across consistency under repeated execution, robustness to task perturbations, fault tolerance under infrastructure failures
- Systematic evaluation reduces failures by 60%

**Source:** ContextQA - LLM Testing Tools and Frameworks 2026
**URL:** https://contextqa.com/blog/llm-testing-tools-frameworks-2026/

**Source:** LXT.ai - LLM Benchmarks in 2026
**URL:** https://www.lxt.ai/blog/llm-benchmarks/

**Source:** SWE-bench Leaderboard data (May 2026):
- **URL:** https://localaimaster.com/models/best-ai-coding-models
- **URL:** https://www.codeant.ai/blogs/swe-bench-scores
- **URL:** https://evolink.ai/blog/swe-bench-verified-2026-claude-vs-gpt
- **URL:** https://benchlm.ai/benchmarks/sweVerified
- Claude Mythos Preview: 93.9% on SWE-bench Verified (announced April 7, 2026)
- Claude Opus 4.7 (Adaptive): 87.6%
- GPT-5.3 Codex: 85%
- GPT-5.5: 82.7% on Terminal-Bench 2.0
- Gemini 3.1 Pro: 80.6%
- CRITICAL: On Feb 23, 2026, OpenAI stopped reporting SWE-bench scores; auditors found 59.4% of hardest problems had flawed test cases and models could reproduce gold patches verbatim (training contamination)

**Source:** MarkTechPost - Best AI Agents for Software Development Ranked
**URL:** https://www.marktechpost.com/2026/05/15/best-ai-agents-for-software-development-ranked-a-benchmark-driven-look-at-the-current-field/

### Polymarket

**Source:** Polymarket - Which company has the best Coding AI model end of May?
**URL:** https://polymarket.com/event/which-company-has-the-best-coding-ai-model-end-of-may
- Anthropic: 96.5%, Z.ai: 1.6%, OpenAI: <1%, Google: 1%
- Total volume: $52,259
- Resolution: May 31, 2026

**Source:** Polymarket - Which company has the best AI model end of May?
**URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-may

### Open Source Landscape

**Source:** ByteByteGo - Top AI GitHub Repositories 2026
**URL:** https://blog.bytebytego.com/p/top-ai-github-repositories-in-2026
- OpenClaw: fastest growing open-source project, 9K → 210K+ stars
- n8n: 180,000+ stars
- AutoGPT: 182K stars
- Over 4.3 million AI-related repositories on GitHub (178% YoY jump in LLM-focused projects)

**Source:** Agentic.ai - Best Open-Source Coding Agents 2026
**URL:** https://agentic.ai/best/open-source-coding-agents
- Aider: strongest all-around open-source coding agent; multi-file editing, git integration, supports any LLM
- Cline: autonomous coding agent in VSCode; creates, edits, deletes files, runs terminal commands

**Source:** SolvedByCode - GitHub AI Coding Explosion
**URL:** https://solvedbycode.ai/blog/github-ai-coding-explosion-january-2026

### Security Concerns

- 40% of Copilot outputs buggy or exploitable (NYU research, cited in HN thread 44309393)
- 45% of vibe-coded projects have vulnerabilities (Pixelmojo research)
- AI-generated code introduces 15-18% more security vulnerabilities as autonomy expands
- AI assistants frequently introduce CVEs due to training data cutoffs

### AI Pair Programming Research

**Source:** Refine.dev - Pair Programming vs AI Pair Programming
**URL:** https://refine.dev/blog/pair-programming-vs-ai-pair-programming/
- Saarland University 2025: human-AI sessions had fewer "broad" conversations; developers question AI less than human partners; accept suggestions more readily even when subtly wrong
- Tasks completed 20-50% faster on average with Copilot

**Source:** Dave Patten (Medium) - State of AI Coding Agents 2026
**URL:** https://medium.com/@dave-patten/the-state-of-ai-coding-agents-2026-from-pair-programming-to-autonomous-ai-teams-b11f2b39232a

**Source:** InfoWorld - The AI Coding Hangover
**URL:** https://www.infoworld.com/article/4141358/the-ai-coding-hangover.html
- "AI pair-programmers should be thought of as junior developers: they can handle routine tasks and give you a draft, but a senior dev must oversee the work"
