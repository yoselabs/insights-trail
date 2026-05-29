# AI Dev Practice — Raw Research Data
**Date:** 2026-05-29
**Query:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## REDDIT (Aggregated Community Discussions)

### Source: Morph LLM Reddit Analysis
URL: https://www.morphllm.com/reddit-vibe-coding
- Analysis of 1,000+ Reddit comments about vibe coding tools
- Top tool by Reddit consensus: Cursor (~4.9/5 rating), Claude Code, Lovable (~4.4/5), Bolt.new, Windsurf (budget Cursor alternative)
- Most common workflow: prototype fast in Lovable or Bolt, then graduate to Cursor or Claude Code for production
- Reddit consensus: "vibe coding is a prototyping methodology, not a production methodology"
- Most productive developers "stack" tools rather than pick one

### Source: Claw Mobile Reddit Analysis
URL: https://claw.mobile/blog/best-ai-coding-tool-reddit-2026
- Reddit roasts 8 AI coding tools
- r/programming, r/webdev, r/vibecoding, r/ChatGPTCoding discussions analyzed
- Budget recommendation: Windsurf ($20/mo Pro) + GitHub Copilot ($10/mo)
- For no-code/vibe coding: Replit (browser-based, multiplayer editing, one-click deploy)
- For beginners: aider (integrates with existing IDE, explains every change)
- r/programming notes Windsurf gained attention for SWE-1.5 model speed benchmark and Cascade feature

### Source: AI Tool Discovery - Cursor Reddit Analysis
URL: https://www.aitooldiscovery.com/guides/cursor-reddit

### Source: DEV Community
URL: https://dev.to/b1fe7066aefjbingbong/reddits-most-upvoted-ai-tools-of-2026-ranked-3hhl

---

## X/TWITTER (Web coverage of X discussions)

### Source: Fortune - Cursor CEO Warning
URL: https://fortune.com/2025/12/25/cursor-ceo-michael-truell-vibe-coding-warning-generative-ai-assistant/
- Cursor CEO Michael Truell defined vibe coding as a method where developers don't look at the code and just ask the AI to build things
- Likened it to "building a house by putting up four walls and a roof without knowing what's going on under the floorboards or with the wiring"
- Warned of "shaky foundations" and eventually "things start to crumble"

### Source: Daily Dev
URL: https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code/
- 92% of US developers now use AI coding tools daily
- 46% of all new code pushed to GitHub is AI-generated

### Source: Pivot to AI
URL: https://pivot-to-ai.com/2026/01/27/cursor-lies-about-vibe-coding-a-web-browser-with-ai/
- Critical coverage of Cursor's marketing claims

### Source: SiliconANGLE
URL: https://siliconangle.com/2026/04/02/cursor-refreshes-vibe-coding-platform-focus-ai-agents/
- April 2026: Cursor refreshes platform with focus on AI agents
- Cursor 3.0 shipped May 2026 with Agents Window and Design Mode

---

## YOUTUBE (Tutorial & Educational Content)

### Video: Vibe Coding Crash Course: Build Real Apps with Cursor, Copilot, MCP + more
URL: https://www.youtube.com/watch?v=HQaVFUV2AgY
- Published: January 23, 2026
- Content: Shows how to work with AI as a developer without giving up control
- Teaches: plan, prompt, test, and refine using modern AI tools
- Topic cluster: Cursor, Copilot, MCP integration

### Related YouTube Courses/Channels
- Scrimba Best Claude Code Tutorials: https://scrimba.com/articles/best-claude-code-tutorials-and-courses-in-2026/
- Udemy: AI For Developers With GitHub Copilot, Cursor AI & ChatGPT: https://www.udemy.com/course/ai-for-developers-with-github-copilot-cursor-ai-chatgpt/
- Udemy: Vibe Coding for Absolute Beginners with GitHub Copilot: https://www.udemy.com/course/vibe-coding-for-absolute-beginners-with-github-copilot/
- Udemy: AI Coder (From Vibe Coder to Agentic Engineer): https://www.udemy.com/course/ai-coder-from-vibe-coder-to-agentic-engineer/
- Udemy: Vibe Coding Camp (Copilot, Cursor, Lovable, Windsurf): https://www.udemy.com/course/vibe-coding-camp-github-copilot-cursor-lovable-windsurf/

### Key Stats from YouTube Coverage
- Claude Code has reached 40.8% adoption (4th most-used AI dev tool, behind ChatGPT, Copilot, Gemini)

---

## HACKER NEWS

### HN: Show HN: Ragtoolina – MCP tool that adds codebase RAG to AI coding agents
URL: https://news.ycombinator.com/item?id=47216558
- Posted: March 2, 2026
- Key finding: RAG overhead doesn't pay off on trivial lookups, but on complex multi-file tasks savings are substantial (up to 79% token reduction)

### HN: We replaced RAG with a virtual filesystem for our AI documentation assistant
URL: https://news.ycombinator.com/item?id=47618223
- Posted: April 12, 2026
- Alternative approach to traditional RAG for documentation assistance

### HN: From zero to a RAG system: successes and failures
URL: https://news.ycombinator.com/item?id=47499356
- Posted: March 30, 2026
- Practical challenges with RAG implementation

### HN: I built an open-source tool that adds RAG context to JetBrains AI Assistant
URL: https://news.ycombinator.com/item?id=44191478
- Posted: June 5, 2025
- Local vector index of code, injecting relevant context into the LLM prompt

### HN: Context Engineering (RAG 2.0): The Next Chapter in GenAI
URL: https://news.ycombinator.com/item?id=45037205
- Posted: September 2, 2025
- Context engineering emerging as discipline

### HN: Gemini Embedding: Powering RAG and context engineering
URL: https://news.ycombinator.com/item?id=44747457

### HN: Engineering over AI
URL: https://news.ycombinator.com/item?id=41439777

### HN: Show HN: How we leapfrogged traditional vector based RAG with a 'language map'
URL: https://news.ycombinator.com/item?id=40998497

### HN: Everyone's engineering context, we're predicting it. Introducing Papr memory API
URL: https://news.ycombinator.com/item?id=45103914

### Key HN Community Themes (from Developer's Digest analysis)
URL: https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- Developers arguing less about whether tools are "real," more about how to make them economically useful
- Workflow focus: tools must preserve context over long sessions, inspect real codebases, compose with shell commands
- The core bottleneck in 2026 is no longer code generation speed—it is **verification capacity**
- HN keeps circling back: "the agent can produce code quickly, but someone still has to decide whether the output is trustworthy"
- The "Ralph Wiggum pattern": AI coding agent in autonomous loop until pre-defined completion criterion satisfied

---

## GITHUB

### Repo: humanlayer/advanced-context-engineering-for-coding-agents
URL: https://github.com/humanlayer/advanced-context-engineering-for-coding-agents/blob/main/ace-fca.md

### Repo: Zijian-Ni/awesome-ai-agents-2026
URL: https://github.com/Zijian-Ni/awesome-ai-agents-2026
- Curated list of AI Agent frameworks, tools, platforms, and resources for 2026

### Repo: microsoft/Mastering-GitHub-Copilot-for-Paired-Programming
URL: https://github.com/microsoft/Mastering-GitHub-Copilot-for-Paired-Programming
- Multi-module course on using GitHub Copilot as AI peer programming resource

---

## WEB / BLOG ARTICLES

### CURSOR vs WINDSURF

#### Windsurf.com Official Comparison
URL: https://windsurf.com/compare/windsurf-vs-cursor
- Windsurf offers plugins for 40+ IDEs (JetBrains, Vim, NeoVim, XCode)
- Cursor restricts users to VSCode fork

#### Vibe Coding Academy: Windsurf vs Cursor (2026): I Tested Both
URL: https://www.vibecodingacademy.ai/blog/windsurf-vs-cursor
- Cursor: iterative, controlled AI collaboration (AI as pair programmer)
- Windsurf: autonomous AI execution, developer describes goals (AI as autonomous agent)
- Pricing matched in March 2026: both now $20/mo Pro
- Cursor: monthly credit pool allows bursting; Windsurf: daily/weekly quotas, more predictable

#### Daily Dev: Cursor vs VS Code vs Windsurf comparison
URL: https://daily.dev/blog/cursor-vs-vs-code-vs-windsurf-ai-code-editor-comparison/

#### NxCode: Windsurf vs Cursor 2026
URL: https://www.nxcode.io/resources/news/windsurf-vs-cursor-2026-ai-ide-comparison

#### Builder.io: Windsurf vs Cursor comparison
URL: https://www.builder.io/blog/windsurf-vs-cursor

#### UI Bakery: Cursor vs Windsurf 2026
URL: https://uibakery.io/blog/cursor-vs-windsurf

#### Toolradar: Windsurf vs Cursor 2026 (6-Month Comparison)
URL: https://toolradar.com/blog/windsurf-vs-cursor-2026

#### Qodo: Windsurf vs Cursor
URL: https://www.qodo.ai/blog/windsurf-vs-cursor/

#### Neuronad: Cursor vs Windsurf (2026): The AI Code Editor Showdown
URL: https://neuronad.com/cursor-vs-windsurf/

#### Key data on Cursor:
- Cursor reached $2 billion in annualized revenue by early 2026
- 2+ million developers open Cursor every month
- Adopted by Stripe, Shopify, Uber, Spotify
- Cursor 3.0 shipped May 2026: Agents Window + Design Mode
- Bugbot auto-fixes common issues on PRs

#### Key data on Windsurf:
- SOC 2, HIPAA, FedRAMP, and ITAR certifications (Cursor only has SOC 2)
- SWE-1.5 model noted for speed
- Cascade feature popular in community discussions

### GITHUB COPILOT AGENT MODE

#### NxCode: GitHub Copilot Complete Guide 2026
URL: https://www.nxcode.io/resources/news/github-copilot-complete-guide-2026-features-pricing-agents
- Agent mode GA on VS Code and JetBrains as of March 2026
- Agent mode: autonomously plans, edits files, runs terminal commands, iterates
- Coding agent: turns GitHub Issues into PRs while you sleep

#### Developer's Digest: GitHub Copilot Coding Agent and CLI
URL: https://www.developersdigest.tech/blog/github-copilot-coding-agent-cli-2026

#### Developer's Digest: GitHub Copilot in 2026 for TypeScript
URL: https://www.developersdigest.tech/blog/github-copilot-guide
- Limitation: agent mode edits code but cannot run terminal commands or install packages
- Recommended workflow: CLI agent (Claude Code) for heavy lifting + Copilot/Cursor for moment-to-moment coding

#### Second Talent: GitHub Copilot Review 2026
URL: https://www.secondtalent.com/resources/github-copilot-review/

#### Digital Applied: GitHub Copilot Coding Agent 50% Faster
URL: https://www.digitalapplied.com/blog/github-copilot-coding-agent-50-percent-faster-semantic-search
- March 2026 performance improvements:
  - Pre-indexing, parallel context loading, session-level caching cut init time in half
  - Vector embedding-based code retrieval: 3x more useful context per task

#### NxCode: GitHub Copilot Review 2026
URL: https://www.nxcode.io/resources/news/github-copilot-review-2026-worth-10-dollars
- Pro plan at $10/month remains sweet spot (half the price of Cursor)

#### Fundesk: GitHub Copilot Agent Mode Guide 2026
URL: https://www.fundesk.io/github-copilot-agent-mode-guide-2026

#### Tossitt: GitHub Copilot Guide 2026
URL: https://tossitt.com/github-copilot-guide-2026/

#### Medium: Practical Tips for Copilot Agent Mode in Visual Studio 2026
URL: https://medium.com/@mpholoane/how-to-use-github-copilot-agent-mode-in-visual-studio-2026-practical-tips-and-lessons-learned-3e5e2d2110be

#### Vocal.media: GitHub Copilot Agent Mode Honest Review
URL: https://vocal.media/01/git-hub-copilot-agent-mode-my-honest-review-for-2026

#### Key stats:
- Developers using Copilot report up to 75% higher job satisfaction
- Up to 55% more productive at writing code
- Agentic code review (shipped March 5, 2026): full project context before analyzing PRs

### LLMs IN PRODUCTION / RAG / CONTEXT ENGINEERING

#### Meta Intelligence: Context Engineering Guide 2026
URL: https://www.meta-intelligence.tech/en/insight-context-engineering
- Context engineering defined: intentionally designing every slot in LLM's context window
- RAG is one retrieval primitive, not a complete context engineering system
- LLMs exhibit uneven attention distribution in ultra-long contexts (more attention to beginning and end)
- Research from Anthropic: contexts larger than 100k tokens can degrade reasoning quality

#### LogRocket: The LLM context problem in 2026
URL: https://blog.logrocket.com/llm-context-problem-strategies-2026/
- In 2026, teams moved past initial success into messy production reality
- Bottleneck is rarely the model — it's what you're feeding it
- Context engineering is now "information discipline"
- Successful production systems filter, rank, prune, summarize, and isolate information

#### Umesh Malik: RAG vs Fine-Tuning 2026 Production Guide
URL: https://umesh-malik.com/blog/rag-vs-fine-tuning-llms-2026
- Best 2026 pattern is hybrid: retrieval for facts, fine-tuning for style/policy/decision behavior

#### RAGFlow: From RAG to Context - Year End Review
URL: https://ragflow.io/blog/rag-review-2025-from-rag-to-context

#### Zilliz: Top 10 Context Engineering Techniques for Production RAG
URL: https://zilliz.com/blog/top-10-context-engineering-techniques-you-should-know-for-production-rag

#### Prompt Engineering Guide: RAG for LLMs
URL: https://www.promptingguide.ai/research/rag

#### Frontiers AI: Context-aware RAG for engineering research
URL: https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2025.1697169/full

#### Roadie: RAG vs Context Engineering in Production
URL: https://roadie.io/blog/rag-vs-context-engineering-production/
- Treating RAG as a complete context engineering system produces failures

#### MarsDevs: What Is RAG in AI? 2026 Production Guide
URL: https://www.marsdevs.com/blog/what-is-rag-in-ai-the-2026-production-guide

#### RAG About It: RAG Is Dead? 5 Enterprise Failures
URL: https://ragaboutit.com/rag-is-dead-5-enterprise-failures-say-otherwise/

#### Atlan: Context Engineering vs RAG
URL: https://atlan.com/know/context-engineering-vs-rag/
- Context failures (missing, stale, conflicting information) are a leading cause of production AI breakdowns

#### Digital Applied: RAG Anti-Patterns 7 Failure Modes 2026
URL: https://www.digitalapplied.com/blog/rag-anti-patterns-7-failure-modes-2026-engineering-guide
- 40-60% of RAG implementations fail to reach production
- 80% of RAG failures trace back to the ingestion layer, not the LLM
- Data quality and governance issues are the real culprits

#### Knolli: Why RAG Is Failing Agentic AI in Production
URL: https://www.knolli.ai/post/rag-failing-agentic-ai

#### Product Leaders Day: Context Engineering vs RAG
URL: https://productleadersdayindia.org/blogs/context-engineering-vs-prompt-engineering/context-engineering-vs-rag.html

#### Packmind: Context Engineering for Coding Agents
URL: https://packmind.com/context-engineering-ai-coding/best-context-engineering-tools/

#### Packmind: Context Engineering Best Practices 2026
URL: https://packmind.com/context-engineering-ai-coding/context-engineering-best-practices/

#### Packmind: Context Engineering for Large Codebases
URL: https://packmind.com/context-engineering-ai-coding/context-engineering-large-codebases/

#### Martin Fowler: Context Engineering for Coding Agents
URL: https://martinfowler.com/articles/exploring-gen-ai/context-engineering-coding-agents.html

#### Faros AI: Best AI Coding Agents for 2026
URL: https://www.faros.ai/blog/best-ai-coding-agents-2026

#### Anthropic Contextual Retrieval data:
- 49% reduction in failed retrievals
- 67% reduction with reranking

### AI RELIABILITY / FAILURE MODES

#### Kovil AI: Why 80% of AI Projects Fail in Production
URL: https://kovil.ai/blog/why-ai-projects-fail
- Gartner: ~85% of AI projects fail to deliver intended business outcomes through 2025
- McKinsey: failure rate closer to 80%
- Production AI requires: evals, prompt versioning, RAG architecture, cost optimization, LLM-specific failure modes

#### Confident AI: Best LLM Observability Platforms 2026
URL: https://www.confident-ai.com/knowledge-base/compare/best-llm-observability-platforms-to-improve-ai-product-reliability-2026

#### Medium: LLMOps Roadmap 2026
URL: https://medium.com/@sanjeebmeister/the-complete-mlops-llmops-roadmap-for-2026-building-production-grade-ai-systems-bdcca5ed2771

#### Build MVP Fast: LLM Error Handling and Fallback Strategies
URL: https://www.buildmvpfast.com/blog/building-with-unreliable-ai-error-handling-fallback-strategies-2026

#### Trantorinc: AI Agent Failure Modes
URL: https://www.trantorinc.com/blog/ai-agent-failure-modes-what-goes-wrong-design-resilience
- Three failure patterns: Dumb RAG (bad context management), Brittle Connectors (broken tool integrations), Compounding Error
- Authentication rot + schema drift = most common tool failures
- Agent with 85% per-step accuracy: only 20% success on 10-step workflow

#### Forgeworkflows: Why AI Agents Fail in Production
URL: https://forgeworkflows.com/blog/why-ai-agents-fail-in-production

#### Latitude: How to Monitor AI Agents in Production
URL: https://latitude.so/blog/how-to-monitor-ai-agents-in-production-guide

#### ArXiv: Beyond pass@1: Reliability Science for Long-Horizon LLM Agents
URL: https://arxiv.org/html/2603.29231v1

#### ArXiv: Failure Modes in LLM Systems Taxonomy
URL: https://arxiv.org/pdf/2511.19933

#### Medium: LLM Reliability Is Not an AI Problem (Feb 2026)
URL: https://medium.com/@Iyanudavid/llm-reliability-is-not-an-ai-problem-c5d4930bad68

#### Medium: Why AI Agents Keep Failing in Production
URL: https://medium.com/data-science-collective/why-ai-agents-keep-failing-in-production-cdd335b22219

#### Datadog: State of AI Engineering
URL: https://www.datadoghq.com/state-of-ai-engineering/
- Rate limits: 60% of LLM call errors in February caused by exceeded rate limits
- 8.4 million rate limit errors in March

#### SSRN: Taxonomy of Failure Modes in Autonomous LLM-Based Systems
URL: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6572478

#### Security:
- Prompt injection is OWASP LLM Top 10 #1 vulnerability for 2025
- In agents, successful injection can hijack entire agent goal

### AI EVALUATION / OBSERVABILITY / BENCHMARKS

#### Confident AI: Best AI Evaluation Tools 2026
URL: https://www.confident-ai.com/knowledge-base/compare/best-ai-evaluation-tools-2026

#### Gartner Peer Insights: AI Evaluation and Observability Platforms
URL: https://www.gartner.com/reviews/market/ai-evaluation-and-observability-platforms
- By 2028: 60% of software engineering teams will use AI evaluation and observability platforms (up from 18% in 2025)
- By 2028: LLM observability investments will reach 50% of GenAI deployments (up from 15%)

#### Maxim AI: Top 5 AI Evaluation Platforms 2026
URL: https://www.getmaxim.ai/articles/top-5-ai-evaluation-platforms-in-2026-comprehensive-comparison-for-production-ai-systems/
- Five leading platforms: Maxim AI, Langfuse, Comet Opik, Arize, DeepEval
- Maxim AI: end-to-end AI quality platform (experimentation, simulation, evaluation, production observability)

#### Latitude: 15 AI Agent Observability Platforms 2026
URL: https://latitude.so/blog/15-ai-agent-observability-platforms-2026-agentic-complexity

#### Deepak Gupta: AI Agent Observability Market Report 2026
URL: https://guptadeepak.com/ai-agent-observability-evaluation-governance-the-2026-market-reality-check/

#### LangChain: State of Agent Engineering 2026
URL: https://www.langchain.com/state-of-agent-engineering
- 57% of enterprises now run agents in production
- 32% cite quality as primary barrier
- Latency: second biggest challenge (20%)
- 89% have implemented observability for agents
- Only 52% do evals
- Only 1/3 satisfied with current observability solutions
- Customer service: most common agent use case (26.5%)
- Research & data analysis: second (24.4%)
- 57% are not fine-tuning models (rely on base models + prompt engineering + RAG)
- 75%+ use multiple models in production (multi-model routing)

#### Maxim AI: AI Observability Tools 2026
URL: https://www.getmaxim.ai/articles/ai-observability-tools-in-2026-top-5-platforms-compared/

#### Randal Olson: Top Tools to Evaluate and Benchmark AI Agent Performance 2026
URL: https://www.randalolson.com/2026/03/06/top-tools-to-evaluate-and-benchmark-ai-agent-performance-2026/

#### Master of Code: AI Evaluation Metrics 2026
URL: https://masterofcode.com/blog/ai-agent-evaluation

#### Medium: Top AI Evaluation Platforms 2026
URL: https://medium.com/@kamyashah2018/top-5-ai-evaluation-platforms-in-2026-comprehensive-comparison-for-production-ai-systems-2e47616dfc7a

### AI PAIR PROGRAMMING / PRODUCTIVITY

#### Accelerate Data: Future of AI Pair Programming
URL: https://acceleratedata.dev/blog/the-future-of-ai-pair-programming-and-human-collaboration-by-2026

#### Index.dev: Top 100 AI Pair Programming Statistics 2026
URL: https://www.index.dev/blog/ai-pair-programming-statistics
- 84% of developers use ChatGPT, Copilot, and more tools to code faster
- ~70% of all development workflows predicted to use AI by 2026

#### Refine: Pair Programming vs AI Pair Programming
URL: https://refine.dev/blog/pair-programming-vs-ai-pair-programming/

#### DevX: AI Coding Assistants 2026: Productivity Gains
URL: https://www.devx.com/uncategorized/ai-coding-assistants-2026-productivity-developer-workflow/
- 55% faster task completion with AI
- Developers using Copilot: 53.2% more likely to pass all unit tests
- But: Anthropic 2026 study found AI users scored 17% lower on post-task quizzes
- Tasks sometimes take 19% longer overall despite more code written (end-to-end including review/debug)

#### ArXiv: Impact of GitHub Copilot on developer productivity
URL: https://arxiv.org/pdf/2302.06590

#### METR: Changing Developer Productivity Experiment Design (Feb 2026)
URL: https://metr.org/blog/2026-02-24-uplift-update/

#### ACM: Impact of AI-Pair Programmers on Code Quality (TiMi studio)
URL: https://dl.acm.org/doi/fullHtml/10.1145/3665348.3665383

### SECURITY CONCERNS

#### ICAEW: Cyber Dangers of Agents and Vibe Coding (Feb 2026)
URL: https://www.icaew.com/insights/viewpoints-on-the-news/2026/feb-2026/cyber-dangers-of-agents-and-vibe-coding

#### HackerNoon: AI Coding Agents Are Turning Vibe Coding Into a Production Risk
URL: https://hackernoon.com/ai-coding-agents-are-turning-vibe-coding-into-a-production-risk

#### Medium: Cybersecurity AI Digest (March 15-29, 2026): AI Co-Authored the Vulnerable Code
URL: https://medium.com/@time_less/cybersecurity-ai-digest-march-15-29-2026-ai-co-authored-the-vulnerable-code-ddfe528a8f1c

#### Future AGI: LLM Stress Testing in 2026
URL: https://futureagi.com/blog/stress-test-llm-2025/

### VIBE CODING GENERAL

#### Vibe Coding Academy: AI Coding Tools Comparison 2026
URL: https://www.vibecodingacademy.ai/blog/ai-coding-tools-comparison-2026

#### ALM Corp: Vibe Coding Complete Guide
URL: https://almcorp.com/blog/vibe-coding-complete-guide/

#### UseLEarnAI: Vibe Coding Tutorial 2026
URL: https://www.uselearnai.com/blog/vibe-coding-tutorial-beginners-guide-2026

#### ICAEW Feb 2026 notable case: ForexFlow
- 200,000-line forex trading platform developed by Ben Marshall in March 2026
- 840 TypeScript files across five sub-apps (Next.js + Node.js)
- Built using vibe coding methodology

#### Know Your Meme: Vibe Coding
URL: https://knowyourmeme.com/memes/vibe-coding
- Origins: Andrej Karpathy coined the term February 2025

---

## KEY STATISTICS SUMMARY

- 92% of US developers use AI coding tools daily (daily.dev)
- 46% of all new code pushed to GitHub is AI-generated (daily.dev)
- 84% of developers use AI tools to code faster (index.dev)
- Cursor: $2B ARR, 2M+ monthly active developers (Fortune/SiliconANGLE)
- Claude Code: 40.8% adoption (4th most-used AI dev tool)
- LangChain 2026: 57% enterprises have agents in production
- LangChain 2026: 32% cite quality as top barrier
- LangChain 2026: 89% implement observability, only 52% do evals
- LangChain 2026: only 1/3 satisfied with observability
- RAG failure rate: 40-60% of implementations never reach production
- 80% of RAG failures trace to ingestion layer, not LLM
- Datadog: 60% of LLM errors = rate limit errors; 8.4M rate limit errors in March
- Agent compounding: 85% per-step accuracy → 20% success at 10 steps
- Productivity: 55% faster coding, but 17% lower quiz scores (Anthropic study)
- Gartner: By 2028, 60% of software teams will use AI eval/observability platforms (from 18% in 2025)
- GitHub Copilot March 2026: 50% faster agent init, 3x better context retrieval
