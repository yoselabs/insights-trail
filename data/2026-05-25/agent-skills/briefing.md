# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-25
**Query type:** GENERAL
**Sources:** Hacker News, Web, GitHub, YouTube, Polymarket, X/Twitter

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 8 stories | 1,751 points, 846+ comments | Top posts from Oct 2025–Feb 2026 window |
| Web | 40+ pages | — | Via WebSearch + WebFetch; docs, blogs, announcements |
| GitHub | 5+ repos | 2.2k–81.1k stars per repo | Key marketplaces and skill collections |
| YouTube | 3 videos + 1 course | 6M+ views (Remotion launch) | Tutorial content and bootcamps |
| Polymarket | 4 markets | $2.3M+ total Claude volume | Claude benchmark/release markets; no direct skills markets |
| X/Twitter | 2 posts | N/A | Mentions captured via search |
| Reddit | 0 threads | — | No indexed results found; likely in r/ClaudeAI but not captured |
| TikTok | 0 videos | — | No results |
| Bluesky | 0 posts | — | Mentioned as engagement source by camilleroux.com but no direct captures |

---

## Synthesized Findings

### 1. The Claude Skills vs. MCP Debate: A Platform-Wide Conversation

The single biggest discussion of late 2025–early 2026 is whether Claude Skills represent genuine architectural innovation or simply formalize existing prompt-engineering practice. The Hacker News post "Claude Skills are awesome, maybe a bigger deal than MCP" ([HN 45619537](https://news.ycombinator.com/item?id=45619537), 738 points, 370 comments) generated a companion thread "Claude Skills" ([HN 45607117](https://news.ycombinator.com/item?id=45607117), 816 points, 427 comments) that together form one of the most-discussed Claude topics in recent memory.

Simon Willison framed Skills as "custom instructions that are unlimited in size," while commenter `pants2` pushed back: "a design pattern / prompt engineering trick." `pseudosavant` countered with the Docker analogy—"conceptually simple, but…novel and could transform things." `JimDabell` argued for wrapping Skills in container/runtime specs with package indices, essentially previewing what the marketplace ecosystem would build.

The technical consensus: Skills solve MCP's most painful real-world problem—token bloat. A 5-server MCP setup with 58 tools consumes ~55,000 tokens before any conversation starts ([morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins)). Skills by contrast load only ~30-50 tokens of metadata per skill until invoked. Anthropic's Tool Search feature reduced MCP overhead by 85%, and internal testing showed accuracy jumping from 49% to 74% on Opus 4 when using Tool Search with large tool libraries.

Cross-platform: Hacker News, Web, X/Twitter all discussed this theme.

---

### 2. Marketplace Explosion: From Zero to Eight in Six Months

The agent skills marketplace landscape went from one registry (December 2025) to eight major platforms by Q2 2026, with wildly different approaches to curation and quality:

| Marketplace | Catalog Size | Model | Notable |
|---|---|---|---|
| SkillsMP | 800,000+ | GitHub-scraped, minimal curation | Largest but lowest signal |
| LobeHub | 169,000+ | Aggregated ecosystem | Cross-platform (Claude, ChatGPT, Codex) |
| ClaudeSkills.info | 658 | Free, community-vetted | Official Anthropic skills included |
| claudemarketplaces.com | 6,700+ skills / 840+ MCPs | Community-curated | 170,000 monthly visitors |
| tonsofskills.com (CCPI) | 2,754 skills / 431 plugins | Open-source, MIT | 53,237 monthly downloads; CLI package manager |
| Agensi | 200+ | Security-scanned, paid | 80/20 creator revenue split |
| Anthropic Official | ~20 | Manually reviewed | Highest trust |
| Agent37 | Varies | Monetized skills via shareable links | Non-technical creators |

Sources: [agensi.io marketplaces guide](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [claudemarketplaces.com](https://claudemarketplaces.com/), [tonsofskills.com](https://tonsofskills.com/), [claude code docs](https://code.claude.com/docs/en/plugin-marketplaces)

The critical caveat flagged by agensi.io's analysis: "Catalog size is the most misleading metric in this category." A security audit found 6.3 issues per skill on average, with prompt injection vulnerabilities in 36% of tested skills. The analysis predicts consolidation from eight platforms to three or four within a year.

The open-source leader, [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills), released version 4.32.0 on May 24, 2026 with 425 plugins, 2,810 skills, 200 agents, 2.2k stars, and 309 forks.

---

### 3. MCP Protocol Governance: From Anthropic to Linux Foundation

The defining governance event of late 2025: on December 9, 2025, Anthropic donated MCP to the Linux Foundation's newly formed Agentic AI Foundation (AAIF). Founding contributions included MCP (Anthropic), goose (Block), and AGENTS.md (OpenAI). Platinum members: AWS, Anthropic, Block, Bloomberg, Cloudflare, Google, Microsoft, OpenAI.

By the numbers at donation time:
- 97 million monthly SDK downloads (March 2026)
- 10,000 active servers
- First-class client support: ChatGPT, Claude, Cursor, Gemini, Microsoft Copilot, VS Code

AGENTS.md—OpenAI's parallel effort for project-level agent guidance—has been adopted by 60,000+ open source projects and frameworks including Amp, Codex, Cursor, Devin, Factory, Gemini CLI, GitHub Copilot, Jules, VS Code.

Sources: [Linux Foundation announcement](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation), [MCP blog](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/), [Anthropic announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), [GitHub blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/), [The New Stack](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/), [AAIF](https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/), [OpenAI](https://openai.com/index/agentic-ai-foundation/), [CData](https://www.cdata.com/blog/anthropic-donates-mcp)

---

### 4. Enterprise MCP: Databricks Marketplace and Vertical Integrations

On May 8, 2026, Databricks launched an MCP Marketplace for enterprise agentic applications—the most significant enterprise platform move of the period. Launch partners: You.com (real-time web + market sentiment), Moody's (institutional credit), Cotality (real estate/mortgage). Additional partners: Glean, S&P Global, Factset, Dun & Bradstreet.

The core premise: "Agents built solely on internal data can't truly think." The MCP Marketplace bridges agents to live external data sources while maintaining Unity Catalog governance, lineage tracking, and compliance.

Companion announcements:
- LSEG launched an MCP Server in Databricks Marketplace ([Traders Magazine](https://www.tradersmagazine.com/xtra/lseg-launches-mcp-server-in-databricks-marketplace/))
- AtScale delivers semantic intelligence to Databricks MCP Marketplace ([BigDATAwire](https://www.hpcwire.com/bigdatawire/this-just-in/atscale-delivers-semantic-intelligence-to-databricks-mcp-marketplace/))
- MCP-powered financial AI workflows on Databricks ([Databricks blog](https://www.databricks.com/blog/mcp-powered-financial-ai-workflows-databricks))

Sources: [Databricks MCP Marketplace blog](https://www.databricks.com/blog/mcp-marketplace-brings-real-time-intelligence-agentic-applications), [Databricks Agent Bricks](https://www.databricks.com/blog/accelerate-ai-development-databricks-discover-govern-and-build-mcp-and-agent-bricks), [StartupHub](https://www.startuphub.ai/ai-news/technology/2026/databricks-adds-real-time-data-to-ai-agents), [TipRanks](https://www.tipranks.com/news/private-companies/databricks-highlights-marketplace-integrations-for-real-time-agentic-ai)

---

### 5. MCP Gateway Layer: The Emerging Infrastructure Tier

As the MCP server count crossed 13,000, a new architectural pattern emerged: the MCP Gateway. Rather than connecting agents directly to many MCP servers (with cumulative context costs), a gateway aggregates tool descriptions, manages auth centrally, and injects tools on demand—reducing context overhead from 40-50% to 5-15%.

Perplexity's CTO noted MCP tool descriptions "consume 40-50% of context window" in large-scale deployments. Cursor has a soft ceiling of ~40 active tools; past ~50 visible tools, models start picking the wrong one.

Top MCP Gateway tools ([bytebridge.medium.com](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a)):
1. ContextForge MCP Gateway (IBM) — open-source federation
2. Peta — security-focused with human-in-the-loop approval
3. Portkey MCP Gateway — enterprise RBAC
4. TrueFoundry — sub-3ms latency overhead
5. Docker MCP Gateway — container-based isolation
6. Microsoft Azure APIM + Kubernetes
7. WSO2 AI Gateway — data compliance
8. Tyk AI Studio — policy-driven controls
9. Zapier MCP — 8,000+ app integrations
10. MintMCP — SOC 2 compliance, one-click deployment

---

### 6. Skill Tooling Ecosystem: Builders, Linters, and Monetization

Beyond publishing skills, a meta-layer of tooling has emerged for creating, validating, and monetizing them:

**Creation tools:**
- SkillBuilder agent skill (HN [48130679](https://news.ycombinator.com/item?id=48130679)): interactive skill generation built into Claude Code harnesses
- Skill Creator (firecrawl.dev list): interactive skill generation tool

**Validation/Linting:**
- Agnix (HN [46983879](https://news.ycombinator.com/item?id=46983879)): 156 validation rules across 28 categories, 11 tools; 57 auto-fixable; sub-10ms Rust validation; LSP integration; prompted by silent failure where `Review-Code` skill never triggered (spec requires kebab-case)

**Cross-platform portability:**
- Skillz (HN [45649295](https://news.ycombinator.com/item?id=45649295), [github.com/intellectronica](https://github.com/intellectronica/skillz)): uses MCP to make Claude Skills runnable in Codex, Copilot, or any other agent

**Monetization:**
- Agent37 (HN [46422134](https://news.ycombinator.com/item?id=46422134)): upload skill, share link, Stripe payments, 80% creator revenue; one creator earned $1,600+; targets non-technical creators

**Discovery:**
- Open Agent Skills Catalog (HN [46692865](https://news.ycombinator.com/item?id=46692865)): aggregates skills from Anthropic, OpenAI, GitHub, Vercel into a unified JSON catalog, auto-updated daily

---

### 7. What's Actually Popular: The Skills That Broke Through

Based on GitHub stars, install counts, and social engagement data:

**By GitHub stars:**
- Karpathy Guidelines: 144,000 stars (fastest-growing skill repo)
- Superpowers multi-agent skill: 40,900 stars, 3,100 forks
- gstack (full engineering team workflow): 68,200 stars
- Marketing Skills (Corey Haines): 12,900 stars
- find-skills skill: 1.5M+ installs (most-installed)

**By tonsofskills.com download rank:**
- caveman skill: 145,600 installs
- frontend-design: 418,100 installs
- CCPI CLI manager: 346 package downloads

**By social engagement (camilleroux.com list):**
- Universal CLAUDE.md (63% token reduction), claude-hud (real-time session monitoring), code-review-graph (6.8× fewer tokens), claude-subconscious (persistent memory), CodeBurn (token usage dashboard)

Remotion skill: 6M+ views on launch demo, 25k+ installs in first week (January 2026) — the single biggest skill launch of the period ([claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/best-addons)).

Sources: [firecrawl.dev skills list](https://www.firecrawl.dev/blog/best-claude-code-skills), [claudemarketplaces.com](https://claudemarketplaces.com/), [tonsofskills.com](https://tonsofskills.com/), [camilleroux.com](https://www.camilleroux.com/top-skills-plugins-claude-code-2026-v3/), [GitHub rohitg00 toolkit](https://github.com/rohitg00/awesome-claude-code-toolkit)

---

### 8. Developer Mindset Shift: Skills > Prompts, Orchestration > Autonomy

The Hacker News meta-analysis ([developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)) captures five truths that recur across HN threads:

1. **Workflow > model selection**: winning products fit real development loops, not benchmarks
2. **Skills > generic prompting**: reusable instructions stored near codebases beat "heroic prompting"
3. **Orchestration > autonomy**: parallel bounded agents with explicit handoffs outperform full-autonomy claims
4. **Verification is the bottleneck**: code generation speed is no longer the limiting factor
5. **Payoff > spectacle**: market shifted from capability demos to measuring economic returns

Claude Code 2.0 features (sankalp.bearblog.dev): checkpointing (Esc+Esc or /rewind), AI-powered prompt suggestions (v2.0.73), Ctrl+R prompt history (v2.0.74), Explore subagent (read-only codebase search), Plan subagent (architecture).

---

### 9. Open Ecosystem Standards: SKILL.md Goes Cross-Platform

The open SKILL.md standard is now shared across Claude Code, GitHub Copilot, Codex, Gemini CLI, Cursor, and others. Same file, multiple clients. Discovery paths include `.github/skills/`, `.claude/skills/`, `.codex/skills/` depending on the agent.

AGENTS.md (OpenAI, August 2025) parallels this at the project level: 60,000+ repos adopted it within months. The architecture emerging ([chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)):
- **Skills** teach specific tasks (SKILL.md)
- **Agents** provide specialized personas
- **Plugins** package everything for distribution
- **Marketplaces** enable discovery via marketplace.json

Official Claude Code plugin docs: [create plugins](https://code.claude.com/docs/en/plugins), [plugin marketplaces](https://code.claude.com/docs/en/plugin-marketplaces), [extend with skills](https://code.claude.com/docs/en/skills)

---

## Cross-Source Patterns

**Pattern 1: Token Efficiency as the Central Design Constraint**
- Platforms: HN (multiple threads), Web (morphllm, qcode.cc, dev.to), GitHub
- Every architectural decision in the skills/MCP ecosystem traces back to context window costs. Skills emerged specifically because MCP is too expensive for discovery-phase tool access. MCP Gateways emerged because 10+ MCP servers overwhelm context. Tool Search emerged to reduce MCP overhead 85%.
- Key quotes: "MCP tool descriptions consume 40-50% of context window" (Perplexity CTO, via qcode.cc) | "A typical five-server setup...uses approximately 55,000 tokens before any conversation starts" (morphllm.com)

**Pattern 2: The Curation/Quality Crisis**
- Platforms: HN, Web (agensi.io), GitHub
- At 800,000+ skills (SkillsMP) and 13,000+ MCP servers, discovery and quality validation are the actual bottleneck, not supply. Security audits find 6.3 issues/skill; 36% have prompt injection vulnerabilities. The ecosystem needs its npm-style provenance layer.
- Key quote: "Catalog size is the most misleading metric in this category" (agensi.io)

**Pattern 3: Skills Trigger Better Documentation**
- Platforms: HN (two major threads), Web
- Multiple commenters independently discovered that writing skills/context files produces dramatically better docs than traditional documentation—because the author gets immediate feedback on quality through their own LLM interactions.
- michael1999 (HN 45619537): short feedback loops | 7thpower: "strong and immediate incentive" when docs enhance your own AI | emn13: skills are "tested immediately against acute problems"

**Pattern 4: Governance Institutionalization**
- Platforms: Web (multiple major outlets), GitHub
- MCP moved from Anthropic proprietary → Linux Foundation AAIF in December 2025, with all major AI labs as members. This mirrors how HTTP, TCP/IP, and other foundational protocols left single-vendor control as they became critical infrastructure.
- Sources: LF announcement, Anthropic blog, GitHub blog, The New Stack

**Pattern 5: Monetization Remains Immature**
- Platforms: HN (Agent37 thread), Web
- Despite 800,000+ skills in some catalogs, monetization is rudimentary. Agent37 launched in January 2026 to address a gap—1,000+ MCP skills on GitHub with no payment mechanism. The 80% creator revenue model is market-standard but adoption is still nascent. One creator at $1,600 is the reported traction benchmark.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (simonwillison.net) | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | "custom instructions that are unlimited in size" — @simonw | https://news.ycombinator.com/item?id=45619537 |
| (anthropic.com) | Claude Skills | 816 | 427 | "conceptually simple, but...novel and could transform things" — pseudosavant | https://news.ycombinator.com/item?id=45607117 |
| syntax-sherlock | Show HN: Playwright Skill for Claude Code | 189 | 45 | "314 lines of instructions vs a persistent MCP server" | https://news.ycombinator.com/item?id=45642911 |
| vishnukool | Show HN: Agent37 – Monetize your Claude skills | 5 | 3 | "over 1,000 MCP skills on GitHub with no monetization mechanism" | https://news.ycombinator.com/item?id=46422134 |
| anotherCodder | Show HN: Agnix – lint your AI agent configs | 1 | 1 | Skill named `Review-Code` never triggered; spec requires kebab-case | https://news.ycombinator.com/item?id=46983879 |
| intellectronica | Skillz: Use Claude Skills in Codex, Copilot via MCP | 2 | — | Removes platform lock-in for Claude Skills | https://news.ycombinator.com/item?id=45649295 |
| (multi-provider) | Agent Skills – Open Trusted Catalog | — | — | Aggregates Anthropic/OpenAI/GitHub/Vercel skills; daily auto-update | https://news.ycombinator.com/item?id=46692865 |
| (harness team) | Claude Code and Codex Skill for Deliberate Skill Development | — | — | SkillBuilder: interactive skill generation within Claude Code | https://news.ycombinator.com/item?id=48130679 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (German creator) | Claude Code Tutorial: Installation, Agents, MCP, Skills, Hooks & Plugins (Deutsch) | — | — | No | https://www.youtube.com/watch?v=mfg2G1cNfnc |
| (unknown) | How I Use Claude Code With Skills, MCP, Agents & Plugins | — | — | No | https://www.youtube.com/watch?v=jzf7DQa2CAc |
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| Udemy | Claude Code 2026: Subagents, MCP, Skills and Plugins Bootcamp | — | — | No | https://www.udemy.com/course/claude-code-for-agentic-ai-build-ai-agents-10x-faster/ |

Note: YouTube metadata not extractable via WebFetch (returned only footer HTML). Remotion skill launch demo: 6M+ views reported by claudefa.st.

**Polymarket:**
| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| Claude Code Commits hit ___  by May 31? | 50% for ↑600.0k | $24.7K | https://polymarket.com/predictions/claude |
| Claude Mythos released by…? | 22% for June 30 | $389K | https://polymarket.com/predictions/claude |
| Will Claude go down on __ days in May? | 63% for 9-11 days | $36.5K | https://polymarket.com/predictions/claude |
| Claude score on Humanity's Last Exam by June 30? | 21% for 45%+ | — | https://polymarket.com/predictions/claude |

Note: No prediction markets specifically targeting MCP adoption rates, marketplace growth, or skill ecosystem milestones. Markets are focused on Claude model performance/release/availability.

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @milesdeutscher | "Claude Code is going mega viral on X. You probably feel overwhelmed with all the content. Don't read it all - instead, just read this one article. I filtered down the 1% of content/tools/resources that are actually worth your time" | — | — | https://x.com/milesdeutscher/status/2012237674409796036 |
| @Praiseakinlami | "Hope you all know about Claude skills. I use it for my viral tweets and I get vitality every time." | — | — | https://x.com/Praiseakinlami/status/2018359352965411097 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| morphllm.com | https://www.morphllm.com/claude-code-skills-mcp-plugins | Token cost comparison: 55k tokens for 5-server MCP setup; 85% reduction via Tool Search; 49→74% accuracy gain |
| qcode.cc | https://www.qcode.cc/mcp-servers-ecosystem-2026 | 13,000+ MCP servers; 97M monthly downloads; 40-50% context window usage per Perplexity CTO |
| agensi.io | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | Marketplace landscape; 6.3 issues/skill; 36% prompt injection; consolidation forecast |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 170k monthly visitors; 6,700+ skills; 840+ MCP servers; find-skills #1 at 1.5M installs |
| tonsofskills.com | https://tonsofskills.com/ | 2,754 skills; 431 plugins; 53,237 monthly downloads; CCPI CLI |
| firecrawl.dev | https://www.firecrawl.dev/blog/best-claude-code-skills | Karpathy Guidelines: 144k stars; two skill categories: Capability Uplift vs Encoded Preference |
| camilleroux.com | https://www.camilleroux.com/top-skills-plugins-claude-code-2026-v3/ | Social-engagement ranked top 13; token-reduction skills dominate |
| dev.to | https://dev.to/sahil_kat/the-mcp-server-ecosystem-in-2026-integration-layer-for-ai-agents-2mln | Production MCP patterns; build vs. find framework |
| databricks.com | https://www.databricks.com/blog/mcp-marketplace-brings-real-time-intelligence-agentic-applications | Enterprise MCP Marketplace launch May 8, 2026 |
| linuxfoundation.org | https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation | AAIF formation; MCP governance transfer Dec 9, 2025 |
| github.blog | https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/ | Developer implications of MCP joining LF |
| developersdigest.tech | https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026 | HN meta-analysis: 5 truths about AI coding agents |
| zircote.com | https://zircote.com/blog/2026/02/friday-roundup-week-9/ | Week 9 roundup; Remote Control preview; MCP infra threshold; agent reliability research |
| sankalp.bearblog.dev | https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/ | Claude Code 2.0 guide; checkpointing; subagents; "Neo downloads Kung Fu" metaphor |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Open Skills standard; cross-platform architecture; plugin manifest format |
| bytebridge.medium.com | https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a | Top 10 MCP Gateway tools; gateway architecture explained |
| builder.io | https://www.builder.io/blog/best-mcp-servers-2026 | Comprehensive MCP server taxonomy by use case |
| anthropic.com | https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation | Official MCP donation announcement |
| anthropic.com | https://www.anthropic.com/news/finance-agents | Finance agents as plugins on paid plans |
| code.claude.com | https://code.claude.com/docs/en/plugin-marketplaces | Official plugin marketplace creation guide |
| code.claude.com | https://code.claude.com/docs/en/plugins | Official plugin creation guide |
| code.claude.com | https://code.claude.com/docs/en/skills | Official skills extension guide |
| nimbalyst.com | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Claude Code plugins 2026 guide |
| nimbalyst.com | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | Best MCP servers ranked |
| nimbalyst.com | https://nimbalyst.com/blog/best-mcp-clients-2026/ | Best MCP clients comparison |
| agensi.io | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Plugin marketplace installation and management |
| agensi.io | https://www.agensi.io/learn/best-mcp-servers-2026 | 15 MCP servers worth wiring in |
| codersera.com | https://codersera.com/blog/best-mcp-servers-claude-code-cursor-2026/ | Best MCP servers for Claude Code and Cursor |
| dev.to | https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k | Skills vs MCP: practical guide |
| clarista.io | https://www.clarista.io/blog/claude-code-mcp-plugins-guide | Complete 2026 guide to MCP and plugins |
| skillsplayground.com | https://skillsplayground.com/guides/claude-code-plugins/ | Complete guide to skills, MCP, extensions |
| agent-wars.com | https://www.agent-wars.com/news/2026-04-04-travel-hacking-toolkit-ai-agents-award-flights | Travel Hacking Toolkit: multi-API agent coordination |
| huryn.medium.com | https://huryn.medium.com/claude-cowork-the-complete-guide-for-pms-e45e7cf0f52d | Claude Cowork complete guide for PMs |
| mcpmarket.com | https://mcpmarket.com/leaderboards | Top 100 MCP servers leaderboard |
| linkedin.com | https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we | Claude Code survival guide 2026 |
| medium.com | https://medium.com/@vikrampatel5/trending-mcp-servers-in-2026-the-ultimate-ai-superpowers-every-developer-is-obsessed-with-right-1451bd168013 | Trending MCP servers roundup |
| turbodocx.com | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best Claude Code skills, plugins, MCP servers |
| claudefa.st | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers; Remotion 6M views stat |
| sparkco.ai | https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi | Prediction market agents with MCP + Claude Code |
| hpcwire.com | https://www.hpcwire.com/bigdatawire/this-just-in/atscale-delivers-semantic-intelligence-to-databricks-mcp-marketplace/ | AtScale in Databricks MCP Marketplace |
| tradersmagazine.com | https://www.tradersmagazine.com/xtra/lseg-launches-mcp-server-in-databricks-marketplace/ | LSEG MCP Server in Databricks Marketplace |
| startuphub.ai | https://www.startuphub.ai/ai-news/technology/2026/databricks-adds-real-time-data-to-ai-agents | Databricks real-time data for agents |
| tipranks.com | https://www.tipranks.com/news/private-companies/databricks-highlights-marketplace-integrations-for-real-time-agentic-ai | Databricks marketplace integrations |
| thenewstack.io | https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation | Anthropic MCP donation analysis |
| openai.com | https://openai.com/index/agentic-ai-foundation/ | OpenAI co-founds AAIF |
| cdata.com | https://www.cdata.com/blog/anthropic-donates-mcp | MCP donation key takeaways |
| prnewswire.com | https://www.prnewswire.com/news-releases/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md-302636897.html | AAIF press release |
| aaif.io | https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/ | AAIF official press release |
| erp.today | https://erp.today/anthropic-set-to-donate-mcp-to-new-linux-foundation-agentic-ai-foundation/ | MCP donation coverage |
| blog.modelcontextprotocol.io | https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/ | MCP joins AAIF official blog |
| analyticsvidhya.com | https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/ | Top 10 MCP servers for AI builders |
| codeongrass.com | https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/ | MCP ecosystem as integration layer |
| shareuhack.com | https://www.shareuhack.com/en/posts/best-mcp-servers-guide-2026 | Best MCP servers guide by use case |
| javascriptdoctor.blog | https://www.javascriptdoctor.blog/2026/05/why-awesome-mcp-servers-is-exploding-on.html | Why awesome-mcp-servers is exploding on GitHub |
| cafeai.home.blog | https://cafeai.home.blog/2026/05/11/mcp-marketplace-brings-real-time-intelligence-to-agentic-applications/ | Databricks MCP Marketplace coverage |
| databricks.com | https://www.databricks.com/blog/mcp-powered-financial-ai-workflows-databricks | MCP-powered financial AI workflows |
| mcpmarket.com | https://mcpmarket.com/tools/skills/polymarket-development-suite | Polymarket Skill for Claude Code |
| mcp.directory | https://mcp.directory/skills/polymarket-agent | Polymarket Agent Skill |
| mcp.directory | https://mcp.directory/skills/polymarket-trader | Polymarket Trader Skill |

**GitHub:**
| Repo | Stars | Forks | Description | URL |
|------|-------|-------|-------------|-----|
| punkpeye/awesome-mcp-servers | 81,100 | — | Curated MCP server collection | https://github.com/punkpeye/awesome-mcp-servers |
| jeremylongshore/claude-code-plugins-plus-skills | 2,200 | 309 | 425 plugins, 2,810 skills, 200 agents; tonsofskills.com + ccpi | https://github.com/jeremylongshore/claude-code-plugins-plus-skills |
| rohitg00/awesome-claude-code-toolkit | 1,800 | 573 | 135 agents, 176+ plugins, 14 MCP configs, 400k skills via SkillKit | https://github.com/rohitg00/awesome-claude-code-toolkit |
| GetBindu/awesome-claude-code-and-skills | — | — | Collection of Claude Skills | https://github.com/GetBindu/awesome-claude-code-and-skills |
| intellectronica/skillz | — | — | Claude Skills via MCP for Codex/Copilot | https://github.com/intellectronica/skillz |
| mjunaidca/polymarket-skills | — | — | Composable skills for Polymarket trading; security-audited | https://github.com/mjunaidca/polymarket-skills |
| wilwaldon/Claude-Code-Video-Toolkit | — | — | Skills + MCP for video production (Remotion, Manim, FFmpeg) | https://github.com/wilwaldon/Claude-Code-Video-Toolkit |
| tolkonepiu/best-of-mcp-servers | — | — | Weekly-updated ranked MCP server list | https://github.com/tolkonepiu/best-of-mcp-servers |
| wong2/awesome-mcp-servers | — | — | Curated MCP server list (400 servers, 1M stars grouping) | https://github.com/wong2/awesome-mcp-servers |
| nobrainer-tech/nobrainer-claude-skills | — | — | Security auditing and hardening skills | https://github.com/nobrainer-tech/nobrainer-claude-skills |
| hesreallyhim/awesome-claude-code | — | — | Comprehensive Claude Code resource list | https://github.com/hesreallyhim/awesome-claude-code/issues/1285 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ — │ — (not captured)
├─ 🔵 X: 2 posts │ — likes │ — reposts
├─ 🔴 YouTube: 3 videos + 1 course │ 6M+ views (Remotion launch) │ — transcript data
├─ 🟢 HN: 8 stories │ 1,751 points │ 846+ comments
├─ 🟣 TikTok: 0 videos │ —
├─ 🩷 Instagram: 0 reels │ —
├─ 🦋 Bluesky: 0 posts (referenced as engagement source only) │ —
├─ 📊 Polymarket: 4 Claude markets │ $2.3M+ total volume (no skills-specific markets)
├─ 🌐 Web: 55+ pages
└─ 🗣️ Top voices: @simonw (simonwillison.net), @milesdeutscher │ HN: michael1999, pseudosavant, pants2, 7thpower, emn13 | jeremylongshore, rohitg00 (GitHub)
```

---

## Data Gaps

- **Reddit**: Multiple search attempts returned zero results for r/ClaudeAI, r/LocalLLaMA, r/MachineLearning threads. Reddit's indexing of this topic appears fragmented or uses different terminology than queries attempted. Likely significant discussion exists on Reddit but was not captured. Estimated Reddit coverage: ~5%.
- **TikTok/Instagram**: Zero results. These platforms almost certainly have tutorial/demo content for Claude Code but are not web-indexed in a way that standard search captures. Estimated coverage: 0%.
- **Bluesky**: Referenced by camilleroux.com as a source of social engagement signals, but no direct posts captured. Estimated coverage: ~5%.
- **X/Twitter direct content**: Only 2 posts captured (via web snippet references, not direct X API). The @milesdeutscher and @Praiseakinlami posts suggest large X discussion volumes not captured. Estimated coverage: <10%.
- **YouTube metadata**: WebFetch of YouTube video URLs returns only footer HTML, not video metadata. View counts, like counts, and channel details unavailable for 3 tutorial videos. Remotion launch figure (6M views) sourced from claudefa.st, not verified directly.
- **HN rate limits**: Items 48130679 and 46396930 and 46692865 returned HTTP 429. Key themes for those posts sourced from secondary search descriptions rather than direct fetches.
- **Estimated overall coverage**: ~60-65% of relevant web discussion; ~10-15% of social discussion.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — Simon Willison (simonwillison.net) via [Hacker News](https://news.ycombinator.com/item?id=45619537)

> "Conceptually simple, but...novel and could transform things." — `pseudosavant` on HN comparing Skills to Docker ([link](https://news.ycombinator.com/item?id=45607117))

> "Catalog size is the most misleading metric in this category." — [agensi.io skills marketplaces guide](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), on SkillsMP's 800,000+ skills vs. 6.3 security issues/skill average

> "MCP tool descriptions consume 40-50% of context window." — Perplexity CTO, cited in [qcode.cc](https://www.qcode.cc/mcp-servers-ecosystem-2026)

> "Agentic applications need real-time intelligence — Agents built on static internal data can't truly reason or make autonomous decisions at scale." — [Databricks MCP Marketplace blog](https://www.databricks.com/blog/mcp-marketplace-brings-real-time-intelligence-agentic-applications) (May 8, 2026)

> "AI agents are a new layer in the software production stack. They need context, supervision, reusable operating rules, and deterministic systems around them." — [developersdigest.tech HN meta-analysis](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)

> "In The Matrix, Neo downloads Kung Fu" — [sankalp.bearblog.dev](https://sankalp.bearblog.dev/my-experience-with-claude-code-20-and-how-to-get-better-at-using-coding-agents/) on Skills loading domain expertise on demand

> "Donating MCP to the Linux Foundation as part of the AAIF ensures it stays open, neutral, and community-driven as it becomes critical infrastructure for AI." — [Anthropic announcement](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation)

> "Don't install everything; too many skills can slow down session startup and cause false activations." — [agensi.io plugin marketplace guide](https://www.agensi.io/learn/claude-code-plugin-marketplace-guide)

> "The awesome-mcp-servers directory reached 81,100 stars, suggesting the protocol stops being experimental when five-figure community curation directories form around it." — [zircote.com Week 9 roundup](https://zircote.com/blog/2026/02/friday-roundup-week-9/)
