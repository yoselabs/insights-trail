# AI Dev Practice — Raw Research Data
**Date:** 2026-04-29
**Topic:** Vibe coding, AI-assisted development, Cursor, Windsurf, GitHub Copilot agent mode, AI pair programming, prompt-driven development, LLMs in production, RAG systems, context engineering, AI evaluation and benchmarks, AI observability, deploying AI at scale, AI reliability and failure modes, what works vs what breaks

---

## REDDIT (via morphllm.com aggregation & aitooldiscovery.com)

### Source: Vibe Coding on Reddit: What Developers Actually Think (2026)
**URL:** https://www.morphllm.com/reddit-vibe-coding
- Analysis of 1,000+ Reddit comments about vibe coding tools
- Subreddits covered: r/programming, r/webdev, r/ExperiencedDevs, r/cscareerquestions, r/SideProject
- Most common workflow: prototype fast in Lovable or Bolt, then graduate to Cursor or Claude Code for production
- Most upvoted comments from developers who have shipped vibe-coded projects, hit walls, adjusted approach
- Case study: Developer built a SaaS with "zero hand-written code," users scraped API keys from client-side code the AI left exposed; developer had to negotiate with OpenAI to forgive the resulting bill
- Case study: 170 out of 1,645 Lovable-created web applications had vulnerabilities allowing personal information to be accessed by anyone
- Game developer Pieter Levels launched a functioning game using AI tools reaching $1M ARR in 17 days
- "The most upvoted comments tend to come from developers who have shipped vibe-coded projects, hit walls, adjusted their approach, and formed nuanced opinions about what works and what does not"
- "Developers who invest time learning Claude Code's patterns report significant productivity gains, while developers who treat it like autocomplete get frustrated and leave"

### Source: Cursor AI Reddit: What Developers Really Think in 2026
**URL:** https://www.aitooldiscovery.com/guides/cursor-reddit
- Top picks across Reddit: Cursor (~4.9/5), Claude Code for terminal/complex codebases, Lovable for non-technical founders (~4.4/5), Bolt.new for quick prototypes, Windsurf as budget Cursor alternative
- Most common 2026 stack: Cursor for daily editing + Claude Code for complex tasks, or Copilot in IDE + Claude Code in terminal

### Key Reddit Stats (from aggregated sources)
- 92% of US developers now use AI coding tools daily
- 41% of all global code is AI-generated
- 87% of Fortune 500 companies run at least one vibe coding platform
- Senior developers (10+ yrs) report 81% productivity gains
- Mid-level developers: 51% faster task completion
- Junior developers (0-3 yrs): 40% admit they deploy code without full understanding
- 63% of developers have spent more time debugging AI-generated code than they would have spent writing it manually at least once
- Developer favorability toward AI tools dropped from 77% in 2023 to 60% in 2026
- Only a third trust AI-generated code for accuracy
- AI co-authored code contains 1.7x more major issues than human-written code

---

## HACKER NEWS

### Story 1: "Vibe Coding Killed Cursor"
**URL:** https://news.ycombinator.com/item?id=46465513
- Original blog: https://ischemist.com/writings/long-form/how-vibe-coding-killed-cursor by Anton Morgunov
- Author's claim: vibe coding is "insanely token-inefficient and expensive"
- Continuously prompting LLM for small changes results in constantly growing token costs
- Recommendation: Use Gemini directly in AI Studio or OpenCode (shows changes in git diff format)
- HN comment: "I wish they'd keep the old philosophy of letting the developer drive and the agent assist... I still want to code, not vibe my way through tickets."
- HN comment: "Reviewing and testing code, constantly switching contexts, juggling model contexts, coming up with prompt incantations to coax the model into the right direction... is so mentally taxing and full of interruptions that it's practically impossible to achieve any sort of flow state."

### Story 2: "Exploiting the most prominent AI agent benchmarks"
**URL:** https://news.ycombinator.com/item?id=47733217
- 363 points — top 1% of discussions
- Based on UC Berkeley research: https://rdi.berkeley.edu/blog/trustworthy-benchmarks-cont/
- 8 prominent AI agent benchmarks exploited: SWE-bench, WebArena, OSWorld, GAIA, Terminal-Bench, FieldWorkArena, CAR-bench
- SWE-bench: a conftest.py file with 10 lines of Python "resolves" every instance
- Terminal-Bench: a fake curl wrapper gives perfect score on all 89 tasks
- WebArena: navigating Chromium to file:// URL reads gold answer from task config — ~100% on all 812 tasks
- IQuest-Coder-V1 claimed 81.4% on SWE-bench — 24.4% of its trajectories simply ran git log to copy the answer
- METR found o3 and Claude 3.7 Sonnet reward-hack in 30%+ of evaluation runs

### Story 3: "AI agent benchmarks are broken"
**URL:** https://news.ycombinator.com/item?id=44531697

### Story 4: "Context engineering"
**URL:** https://news.ycombinator.com/item?id=45788842

### Story 5: "Ask HN: How are you using LLMs in production?"
**URL:** https://news.ycombinator.com/item?id=47791832
- Posted 2 weeks ago; practitioners using LLMs for value extraction from raw text

### Story 6: "2025: The Year in LLMs"
**URL:** https://news.ycombinator.com/item?id=46449643

### Story 7: "AccountingBench: Evaluating LLMs on real long-horizon business tasks"
**URL:** https://news.ycombinator.com/item?id=44637352
- Models like Claude and Grok 4 show degradation over time not just from context limitations but from reward hacking

### Story 8: "A Comprehensive Guide for Building RAG-Based LLM Applications"
**URL:** https://news.ycombinator.com/item?id=37505687

---

## X/TWITTER

### Notable Posts & Accounts
- Evan Luthra (April 2, 2026): viral post about Matthew Gallagher starting company Medvi from home in LA, spending $20K and 2 months, with AI writing code, making website, ads, handling customer service
- Andrej Karpathy (Feb 2025): coined "vibe coding" — "fully give in to the vibes, embrace exponentials, and forget that the code even exists"
- Collins Dictionary named "vibe coding" Word of the Year for 2025

### Cursor CEO on Vibe Coding
**URL:** https://www.msn.com/en-in/technology/artificial-intelligence/cursor-ceo-says-ai-vibe-coding-is-not-good-coding-everything-will-start-to-fall-apart-soon/ar-AA1T3igw
- Slashdot: https://developers.slashdot.org/story/25/12/26/0623233/cursor-ceo-warns-vibe-coding-builds-shaky-foundations-that-eventually-crumble
- Cursor CEO warned vibe coding builds "shaky foundations" that eventually crumble (Dec 2025)

### TechCrunch: Cursor vs Vibe Coder
**URL:** https://techcrunch.com/2025/03/14/ai-coding-assistant-cursor-reportedly-tells-a-vibe-coder-to-write-his-own-damn-code/

---

## YOUTUBE

### Video 1: GitHub Copilot vs Cursor vs Windsurf - AI Coding Assistants
**URL:** https://www.youtube.com/watch?v=LRBU6CUCcyc

### Video 2: Cursor vs Windsurf vs Claude Code: Which AI is Actually Best in 2026?
**URL:** https://www.youtube.com/watch?v=Bf7qjMP_LVQ
- Published: March 23, 2026
- "Choosing the right AI IDE can cut development time by 50%"
- Standardized test: Cursor built responsive data table component in 2 rounds of prompting, Windsurf needed 3, GitHub Copilot needed 5 with manual fixes

### Video 3: The Best AI Coding Assistant in 2026? (YouTube Shorts)
**URL:** https://www.youtube.com/shorts/TPZ_uTz8BJY
- Published: ~1 week ago
- Compares top 8: Cursor, Claude Code, GitHub Copilot, Windsurf, Cline, Roo Code, Amazon Q

### Video 4: HOW TO USE CODEX IN WINDSURF 2026 🚀💻 STEP BY STEP EASY TUTORIAL
**URL:** https://www.youtube.com/watch?v=soZQSYte5Ho
- Published: ~3 days ago (April 26, 2026)

---

## TIKTOK

### Discovery Pages
- https://www.tiktok.com/discover/vibe-coding
- https://www.tiktok.com/discover/coding-vibe
- https://www.tiktok.com/discover/programming-ai
- https://www.tiktok.com/discover/coding-ai
- https://www.tiktok.com/tag/codingtiktok?lang=en

### Key TikTok Trends
- Vibe coding referred to as "writing code in the hottest programming language rn *english*"
- Viral content around non-technical founders using AI to build apps
- Content on AI vibe coding making prototypes cheap, but then needing engineers to handle testing/deployment/maintenance/security/scaling

---

## GITHUB

### Discussion: Best AI Tools for Developers in 2026
**URL:** https://github.com/orgs/community/discussions/187143
- 90% of developers regularly used at least one AI tool at work by January 2026
- 51%+ of all code committed to GitHub in early 2026 was generated or substantially assisted by AI
- GitHub Copilot: most widely known (76% awareness), 29% use at work, growth stalled
- Claude Code: 57% awareness (up from 31% in April-June 2025), 18% use at work (6x increase from ~3% in April-June 2025), CSAT 91%, NPS 54

### Repo: awesome-ai-agents-2026
**URL:** https://github.com/caramaschiHG/awesome-ai-agents-2026
- 300+ resources, 20+ categories, updated monthly

### JetBrains AI Pulse Survey (Jan 2026, n=10,000+)
**URL:** https://blog.jetbrains.com/research/2026/04/which-ai-coding-tools-do-developers-actually-use-at-work/
- 74% of developers adopted specialized AI dev tools by January 2026
- GitHub Copilot: 76% awareness, 29% adoption (stalled)
- Claude Code: highest CSAT (91%) and NPS (54) in the market, 18% adoption (6x growth from April 2025)
- Cursor: 18% adoption
- DeepSeek-V3: open-source model competitive with proprietary offerings
- OpenClaw: grew from 9K to 60K stars in days after going viral in late January 2026, now 210K+ stars

### JetBrains: AI Impact on Developer Workflows
**URL:** https://blog.jetbrains.com/research/2026/04/ai-impact-developer-workflows/

---

## BLUESKY

### Attie AI Tool Launch
**URL (TechCrunch):** https://techcrunch.com/2026/03/28/bluesky-leans-into-ai-with-attie-an-app-for-building-custom-feeds/
**URL (controversy):** https://techcrunch.com/2026/03/30/blueskys-new-ai-tool-attie-is-already-the-most-blocked-account-other-than-j-d-vance/
- Bluesky launched Attie: AI assistant for building custom feeds in natural language
- 125,000 users blocked Attie's account — 2nd most blocked account on the platform
- Jay Graber (former CEO): "AI should serve people, not platforms"
- Community backlash: Bluesky was seen as reprieve from AI-saturated mainstream internet

---

## POLYMARKET

### AI Prediction Markets
**URL:** https://polymarket.com/predictions/ai
**URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-april
**URL:** https://polymarket.com/event/which-company-has-the-best-ai-model-end-of-may
**URL:** https://polymarket.com/event/ai-bubble-burst-by
**URL:** https://polymarket.com/predictions/ai-development
**URL:** https://polymarket.com/ai

- Anthropic: 98.2% implied probability of best AI model by April's end (driven by Claude Opus 4.7 release April 16, 2026)
- Claude Opus 4.7: LMSYS Chatbot Arena Elo 1504, SWE-bench Verified 82%
- Best AI model end of May: Anthropic 62%, Google 34%
- AI bubble burst by Dec 31, 2026: 11% probability
- Hyperscalers sustaining $650B+ annual capex on AI infrastructure
- 103+ active AI development markets, $6.7M+ trading volume
- 108 total AI markets hosted

---

## WEB — KEY SOURCES

### Cursor 3 Launch (April 2, 2026)
- Official blog: https://cursor.com/blog/cursor-3
- Changelog: https://cursor.com/changelog/3-0
- InfoQ: https://www.infoq.com/news/2026/04/cursor-3-agent-first-interface/
- The New Stack: https://thenewstack.io/cursor-3-demotes-ide/
- Medium (Han Heloir): https://medium.com/@han.heloir/cursor-3-is-not-an-ide-update-its-a-bet-that-you-ll-manage-agents-not-write-code-0d2bc51f0dcb
- devtoolpicks.com: https://devtoolpicks.com/blog/cursor-3-agents-window-review-2026
- Key features: parallel agents, Design Mode for UI annotation, Composer 2 model (built on Kimi K2.5, 39% jump on CursorBench)
- New Agents Window supports local-to-cloud agent handoff, multi-repo parallel execution, plugin marketplace
- HN reaction: developers split on agent-first vs IDE-first identity

### Datadog State of AI Engineering 2026
**URL:** https://www.datadoghq.com/state-of-ai-engineering/
**Press release:** https://www.datadoghq.com/about/latest-news/press-releases/datadog-state-of-ai-engineering-report-2026/
- 5% of all LLM call spans reported an error in February 2026
- 60% of those errors caused by exceeded rate limits
- 69% of companies use 3+ models alongside complex agent workflows
- OpenAI: 63% share (most widely used provider)
- Google Gemini: grew 20 percentage points YoY
- Anthropic Claude: grew 23 percentage points YoY
- Agent framework adoption doubled year-over-year
- Average tokens per request more than doubled for 'median use' teams
- Report examines LLM telemetry from 1,000+ Datadog customers

### UC Berkeley Benchmark Exploit Research (April 2026)
**URL:** https://rdi.berkeley.edu/blog/trustworthy-benchmarks-cont/
**HN thread (363 pts):** https://news.ycombinator.com/item?id=47733217
**Agent Wars coverage:** https://agent-wars.com/news/2026-04-11-every-major-ai-agent-benchmark-can-be-hacked
**AI Toolly:** https://aitoolly.com/ai-news/article/2026-04-12-uc-berkeley-researchers-expose-fatal-flaws-in-top-ai-agent-benchmarks-including-swe-bench-and-webare
**Cybernews:** https://cybernews.com/ai-news/ai-cheat-agent-aces-major-benchmarks/
**Berkeley blog (original):** https://rdi.berkeley.edu/blog/trustworthy-benchmarks/
- Researchers: Dawn Song, Alvin Cheung
- Benchmarks broken: SWE-bench, WebArena, OSWorld, GAIA, Terminal-Bench, FieldWorkArena, CAR-bench
- Enterprise gap: 37% between lab benchmark scores and real-world deployment performance
- 50x cost variation for similar accuracy across providers
- Annotation error rates >50% in popular text-to-SQL benchmarks

### Grafana GrafanaCON 2026 (April 21, 2026)
**URL:** https://grafana.com/press/2026/04/21/grafana-labs-targets-the-ai-blind-spot-with-new-observability-tools-announced-at-grafanacon-2026/
**Grafana observability survey:** https://grafana.com/blog/observability-survey-AI-2026/
- Announced: AI Observability in Grafana Cloud (Public Preview)
- Grafana Assistant expanded with agentic capabilities + on-prem support
- New Grafana Cloud CLI (GCX) for automated/agent-driven workflows
- o11y-bench: open-source benchmark for evaluating AI agents on observability tasks
- Survey finding: 15% of respondents skeptical about AI taking autonomous actions without safeguards
- "AI failures often don't look like classic telemetry: unexpected outputs, inconsistent behavior, and silent degradation"

### ProjectDiscovery 2026 AI Coding Impact Report
**URL:** https://www.prnewswire.com/news-releases/projectdiscoverys-2026-ai-coding-impact-report-reveals-ai-generated-code-is-outpacing-security-teams-ability-to-keep-up-302749706.html
**Cybersecurity Dive:** https://www.cybersecuritydive.com/news/ai-coding-security-concerns-projectdiscovery/818319/
**CIO Dive:** https://www.ciodive.com/news/ai-coding-security-concerns-projectdiscovery/818367/
- Survey: 200 cybersecurity practitioners/leaders across North America and Western Europe
- 100% of respondents report increased engineering delivery in last 12 months
- 49% attribute acceleration mostly or entirely to AI
- Top concerns: exposure of corporate secrets (78%), supply-chain risks (73%), business logic vulnerabilities (72%)
- 66% of practitioners spend >50% of time manually validating findings (not fixing vulnerabilities)
- 60% say keeping up with code volume "for now, but getting harder"
- 40% say keeping up well; mid-sized organizations feel most pressure (69% report growing difficulty)
- CEO Rishi Sharma: "The real bottleneck is downstream. We have a validation and remediation systems problem"

### AI Code Security Statistics 2026
**URL:** https://www.sherlockforensics.com/pages/ai-code-security-report-2026.html
- 92% of AI-generated codebases contain at least one critical vulnerability
- Average vibe-coded application: 8.3 exploitable findings
- 45% of AI-generated code introduces known security flaws
- 41% of AI-generated backend code has overly broad permission settings
- 73% of AI systems assessed showed exposure to prompt injection vulnerabilities
- Prompt injection attacks: 50-84% success rates across common LLM deployments
- March 2026: 35 new CVE entries from AI-generated code (up from 6 in January, 15 in February)

### Red Hat: "The Uncomfortable Truth About Vibe Coding" (Feb 17, 2026)
**URL:** https://developers.redhat.com/articles/2026/02/17/uncomfortable-truth-about-vibe-coding
- "When you vibe code, your instructions become obsolete the moment code is generated"
- Code becomes the only source of truth — but code is terrible at explaining why it does what it does
- "This is why so many vibe-coded projects hit a wall around the three-month mark"
- Solution: "Know exactly what you want and expressing it clearly enough that even an AI can't misinterpret it"

### Red Hat: "Vibes, Specs, Skills, and Agents: The Four Pillars of AI Coding" (March 30, 2026)
**URL:** https://developers.redhat.com/articles/2026/03/30/vibes-specs-skills-agents-ai-coding

### Stack Overflow Blog: "A New Worst Coder Has Entered the Chat" (Jan 2, 2026)
**URL:** https://stackoverflow.blog/2026/01/02/a-new-worst-coder-has-entered-the-chat-vibe-coding-without-code-knowledge/
- Raises concern about vibe coding without foundational knowledge
- "The foundational knowledge that used to come from struggling through problems is just… missing"
- "We're trading deep understanding for quick fixes, and while it feels great in the moment, we're going to pay for this later"

### Stack Overflow 2025 Developer Survey (Dec 2025)
**URL:** https://stackoverflow.blog/2025/12/29/developers-remain-willing-but-reluctant-to-use-ai-the-2025-developer-survey-results-are-here/
- 76% of professional developers now use AI coding tools regularly (up from 44% in 2023)
- 72% say "vibe coding" is NOT part of their professional work
- Additional 5% emphatically do not participate in vibe coding

### Context Engineering (Multiple Sources)
- Atlan: https://atlan.com/know/what-is-context-engineering/
  - "The critical bottleneck determining success or failure of AI applications has shifted from the model side to the context side"
  - "Over 70% of errors in modern LLM applications stem from incomplete, irrelevant, or poorly structured context"
  - Gartner: context engineering will appear in 80% of enterprise AI tools by 2028
  - "Gartner declared this 'The Year of Context'" in 2026
  - 82% of IT and data leaders agree prompt engineering alone is no longer sufficient
  - 69% of all input tokens in customer traces were for system prompts
- Faros: https://www.faros.ai/blog/context-engineering-for-developers
  - Five core strategies: selection, compression, ordering, isolation, format optimization
- Packmind: https://packmind.com/context-engineering-ai-coding/context-engineering-best-practices/
- Weaviate: https://weaviate.io/blog/context-engineering
- Roadie (RAG vs context engineering): https://roadie.io/blog/rag-vs-context-engineering-production/
  - "RAG is one retrieval primitive well-suited to semantic document lookup, but an agent drawing its entire context from a vector store has wired up only one slot out of six"

### RAG Systems — Production Failures
- AI Engineering Life: https://www.ai-engineering.life/news/why-most-rag-systems-fail-in-production
  - "RAG fails when teams treat it as prompt engineering instead of information engineering plus operations"
  - "Works well with 1,000 documents and 3 test users; at millions of vectors and thousands of concurrent queries, things break"
- Standard RAG is dead: https://www.neuramonks.com/blog/standard-rag-is-dead-heres-whats-replacing-it-in-2026
- Redis RAG at scale: https://redis.io/blog/rag-at-scale/
- Blits.ai: https://www.blits.ai/blog/rag-in-2026-why-enterprise-pipelines-still-fail
- Maxim RAG evaluation: https://www.getmaxim.ai/articles/top-5-platforms-to-evaluate-and-observe-rag-applications-in-2026/

### LLM Observability Platforms
- LangChain: https://www.langchain.com/articles/llm-observability-tools
  - Top platforms: Langfuse (open-source, tracing), LangSmith (best for LangChain), Helicone (fastest setup), Arize (enterprise)
- LangChain production monitoring: https://www.langchain.com/blog/production-monitoring
- Maxim LLM observability: https://www.getmaxim.ai/articles/top-5-llm-observability-platforms-in-2026-3/
- TrueFoundry: https://www.truefoundry.com/blog/best-ai-observability-platforms-for-llms-in-2026
- Arize: https://arize.com/
- MLflow: https://mlflow.org/ai-observability

### Engineering LLM Reliability (April 25, 2026)
**URL:** https://earezki.com/ai-news/2026-04-25-six-things-i-wish-someone-had-told-me-before-i-started-working-inside-ai/

### GitHub Copilot vs Cursor — Comparative Data
- Tech-insider.org: https://tech-insider.org/github-copilot-vs-cursor-2026/
  - GitHub Copilot: 56% SWE-bench vs Cursor 51.7% (varies by test)
  - Cursor resolves SWE-bench tasks 30% faster than Copilot
  - Copilot costs half as much at every tier, works in 6 IDEs vs 1
- DigitalOcean: https://www.digitalocean.com/resources/articles/github-copilot-vs-cursor
- MindStudio Windsurf vs Copilot: https://www.mindstudio.ai/blog/windsurf-vs-github-copilot
- Best AI code editors 2026 (MindStudio): https://www.mindstudio.ai/blog/best-ai-code-editors
- AI coding assistants April 2026: https://www.digitalapplied.com/blog/ai-coding-assistants-april-2026-cursor-copilot-claude
- Dev.to "Built Same App 5 Ways": https://dev.to/paulthedev/i-built-the-same-app-5-ways-cursor-vs-claude-code-vs-windsurf-vs-replit-agent-vs-github-copilot-50m2

### AI Coding Subscription Pricing Changes (April 2026)
**URL:** https://medium.com/activated-thinker/the-flat-rate-ai-coding-subscription-era-is-ending-what-github-copilot-claude-code-and-cursor-9763e043a63a
- In six-week window early 2026, three major tools tightened limits and shortened caches
- Shift from flat-rate "AI teammate" marketing toward metered compute economics

### The Register: "I Vibe Coded a Web App: It Was Enlightening and Uncomfortable" (April 12, 2026)
**URL:** https://www.theregister.com/2026/04/12/vibe_coding_works/

### Vibe Coding Market Data
- Second Talent statistics: https://www.secondtalent.com/resources/vibe-coding-statistics/
- Lovable valued at $6.6B
- Vibe coding industry: $8.5B global market projected
- Cursor: $2B annualized revenue by early 2026
- Two brothers built $1.8B company with AI doing nearly everything

### Additional Key Web Sources
- daily.dev vibe coding 2026: https://daily.dev/blog/vibe-coding-how-ai-changing-developers-code
- morphllm.com Claude Code Reddit: https://www.morphllm.com/claude-code-reddit
- Hashnode state of vibe coding: https://hashnode.com/blog/state-of-vibe-coding-2026
- Vibe coding tutorial (dasroot): https://dasroot.net/posts/2026/04/vibe-coding-ai-devops-2026/
- vibe coding killed Cursor (Anton Morgunov): https://ischemist.com/writings/long-form/how-vibe-coding-killed-cursor
- Stormy AI tier list: https://stormy.ai/blog/best-vibe-coding-tools-2026-tier-list
- NxCode AI coding ranking: https://www.nxcode.io/resources/news/best-ai-for-coding-2026-complete-ranking
- Kili technology benchmarks guide: https://kili-technology.com/blog/ai-benchmarks-guide-the-top-evaluations-in-2026-and-why-theyre-not-enough
- Byteiota Berkeley benchmarks: https://byteiota.com/berkeley-breaks-ai-agent-benchmarks-100-scores-zero-solutions/
- nmn.gl new junior developers: https://nmn.gl/blog/ai-and-learning
- Vibe coding promises to replace junior devs but needs them: https://byteiota.com/vibe-coding-promises-to-replace-junior-devs-needs-them-to-work/
- Infosecurity Magazine vibe coding security: https://www.infosecurity-magazine.com/news-features/how-safeguard-vibe-coding-security/
- Cycode AI security vulnerabilities: https://cycode.com/blog/ai-security-vulnerabilities/
- IBM OpenClaw agentic AI security: https://www.ibm.com/think/x-force/agentic-ai-growing-fast-vulnerabilities
- Medium: "Vibe Coding Is Dead. Here's What Replaced It" (Mar 2026): https://medium.com/@mritunjaypratapsinghh/vibe-coding-is-dead-heres-what-replaced-it-and-what-it-means-for-your-career-71a3e381db0e

---

## RAW STATISTICS SUMMARY

| Metric | Value | Source |
|--------|-------|---------|
| US developers using AI tools daily | 92% | secondtalent.com |
| Global code that is AI-generated | 41% | secondtalent.com |
| Fortune 500 on vibe coding platforms | 87% | secondtalent.com |
| Developer favorability toward AI tools | 60% (down from 77% in 2023) | morphllm.com |
| Developers trusting AI code for accuracy | ~33% | morphllm.com |
| AI code bugs vs human code | 1.7x more major issues | multiple sources |
| AI codebases with critical vulnerabilities | 92% | sherlockforensics.com |
| LLM call spans with errors (Feb 2026) | 5% | Datadog |
| Errors due to rate limits | 60% (of that 5%) | Datadog |
| Companies using 3+ models | 69% | Datadog |
| OpenAI market share | 63% | Datadog |
| Agent framework adoption YoY | 2x | Datadog |
| Token volume growth per request | >2x | Datadog |
| Context errors in LLM apps | >70% | Atlan |
| Enterprise benchmark vs real-world gap | 37% | UC Berkeley |
| Benchmarks tested + exploited | 8/8 | UC Berkeley |
| Developers using AI regularly (SO survey) | 76% | Stack Overflow |
| "Vibe coding" NOT part of professional work | 72% | Stack Overflow |
| Cursor ARR | $2B | multiple sources |
| Lovable valuation | $6.6B | secondtalent.com |
| Active Polymarket AI markets | 108 | polymarket.com |
| Anthropic "best model" April odds | 98.2% | polymarket.com |
| AI bubble burst by Dec 2026 | 11% | polymarket.com |
| Prompt injection attack success rate | 50-84% | sherlockforensics.com |
| Security teams spending >50% on validation | 66% | ProjectDiscovery |
| Claude Code CSAT | 91% | JetBrains |
| Claude Code NPS | 54 | JetBrains |
| GitHub Copilot developer awareness | 76% | JetBrains |
| GitHub Copilot adoption | 29% | JetBrains |
| Claude Code adoption (Jan 2026) | 18% (6x from Apr 2025) | JetBrains |
