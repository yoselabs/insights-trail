# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-22
**Query type:** GENERAL
**Sources:** Hacker News, Web, GitHub, YouTube, Polymarket (tools only)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 9 threads | 1,558+ points, 799+ comments | Top 2 threads alone: 816+738 pts |
| Web | 80+ pages | — | Blogs, docs, security research, news |
| GitHub | 15+ repos | 141k + 36.8k + 17.8k repos tracked | Ecosystem repos + spec |
| YouTube | 1 video confirmed | Unknown views | April 13, 2026 guide |
| Reddit | Not directly accessible | Est. 4,200+ weekly r/ClaudeCode contributors | Domain blocked; secondary sources only |
| X/Twitter | Excluded per instructions | — | |
| TikTok | 0 videos with metrics | — | Discover page found; no video data |
| Bluesky | 0 posts with metrics | — | Community activity noted; no direct posts |
| Polymarket | 0 markets on topic | — | 20 AI markets live; none on agent skills adoption specifically |

---

## Synthesized Findings

### 1. The Agent Skills Open Standard: December 2025's Fastest Cross-Vendor Adoption

Anthropic published the **Agent Skills specification** on December 18, 2025, at [agentskills.io](https://agentskills.io/home), releasing it as an open standard under Apache 2.0 (code) + CC-BY-4.0 (docs). Within 48 hours, Microsoft integrated it into VS Code and OpenAI adopted it for both ChatGPT and Codex CLI. By March 2026, 32 tools had adopted the format. By May 2026, the agentskills.io homepage lists **40+ adopters** including Gemini CLI, JetBrains Junie, AWS Kiro, Block's Goose, GitHub Copilot, OpenHands, Cursor, Roo Code, Databricks Genie Code, Snowflake Cortex Code, Spring AI, Tabnine, ByteDance's TRAE, and many more.

The core format is intentionally minimal: a directory with a `SKILL.md` file containing YAML frontmatter (`name`, `description`) and markdown instructions, with optional `scripts/`, `references/`, and `assets/` subdirectories. Skills are loaded via **progressive disclosure**—agents load only name/description at startup (metadata pass), then pull full instructions when a task matches, keeping token cost to 30-50 tokens per skill at idle.

The portability story is the headline: a skill built for Claude Code works identically in OpenAI Codex, Gemini CLI, GitHub Copilot, Cursor, VS Code, and 35+ other platforms with no modification. [F5 called it "an emerging open standard"](https://www.f5.com/company/blog/agent-skills-an-emerging-open-standard); [MindStudio documented](https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google) how Claude, OpenAI, and Google all adopted the same format; [Paperclipped walked through the full interoperability story](https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/).

**Platforms discussed:** Web, Hacker News

---

### 2. The Marketplace Explosion: From 1 Registry to 8+ in Six Months

The agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026. Scale varies enormously depending on curation model:

| Marketplace | Skills | Model | URL |
|-------------|--------|-------|-----|
| SkillsMP | 800,000+ | GitHub scrape, no curation | https://skillsmp.com/ |
| LobeHub | 169,000+ | Aggregated, polished UI | https://lobehub.com/skills |
| Vercel skills.sh | 89,753 | npm-style CLI, community | — |
| claudemarketplaces.com | 6,700+ skills, 840+ MCPs, 2,500+ marketplace repos | Daily GitHub sync | https://claudemarketplaces.com/ |
| ClawHub | 20,000+ | Richer metadata | — |
| tonsofskills.com | 2,747 skills / 428 plugins | ccpi CLI package manager | https://tonsofskills.com/ |
| Agent Skills Hub | 1,200+ | Security-verified | https://agentskillshub.dev/ |
| ClaudeSkills.info | 658 | Community + official Anthropic | — |
| Agensi | 200+ | Manual curation, 8-pt security scan, creator payments (80/20 split) | — |
| Anthropic Official | ~20 | Anthropic-verified | https://claude.com/plugins |

170,000+ developers visit claudemarketplaces.com each month. The quemsah/awesome-claude-plugins automated tracker [indexed 17,826 Claude Code plugin repositories](https://github.com/quemsah/awesome-claude-plugins) as of May 20, 2026. The canonical hand-curated list [hesreallyhim/awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) has 36.8k stars; the aggregator [affaan-m/everything-claude-code](https://claudefa.st/blog/tools/resources/awesome-claude-code) has 141k stars.

**Platforms discussed:** Web, GitHub

---

### 3. Claude Code's Extensibility Stack: Skills vs. MCP vs. Plugins vs. Hooks

The most-discussed confusion in the community is the relationship between these four building blocks. The consensus model:

- **Skills** = procedural knowledge. A SKILL.md teaches Claude *how* to do something. 30-50 tokens at idle. Activate automatically when context is relevant. [Anthropic docs](https://code.claude.com/docs/en/skills)
- **MCP (Model Context Protocol)** = external connections. Hooks Claude into GitHub, databases, APIs, Slack, etc. Token-heavy upfront: a typical 5-server setup uses ~55,000 tokens before conversation begins. Anthropic's new [Tool Search feature reduces this by 95%](https://www.morphllm.com/claude-code-extensions) via lazy loading. SSE transport deprecated; HTTP is the new standard. [Claude API docs](https://platform.claude.com/docs/en/agent-sdk/mcp)
- **Plugins** = distribution bundles. Package skills + MCP configs + hooks + subagents into one installable unit. [Plugins shipped January 30, 2026](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026); Anthropic launched 11 official plugins at release; plugin marketplace launched February 2026. [Create plugins docs](https://code.claude.com/docs/en/plugins)
- **Hooks** = lifecycle automation. Intercept any agent event with deterministic scripts. Unlike skills (guidance), hooks *enforce* — they run invisibly whether or not you're watching. [Hooks reference](https://code.claude.com/docs/en/hooks)

The Morph guide synthesized it cleanly: ["Hooks are for actions that *must* happen. Skills are for guidance that *should* be followed."](https://www.morphllm.com/claude-code-skills-mcp-plugins)

Most developers end up with 2-3 MCP servers (GitHub, Filesystem, one domain-specific) + a handful of custom skills + hooks for enforcement.

**Platforms discussed:** Web, Hacker News

---

### 4. Hacker News Erupts: "Skills Are a Bigger Deal Than MCP"

The phrase originated with Simon Willison's comment in the October 2025 ["Claude Skills"](https://news.ycombinator.com/item?id=45607117) thread (816 points, 427 comments) and became its own thread ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) (738 points, 370 comments).

**Key arguments in favor:**
- Skills minimize context pollution — keep less in the token window than MCP or AGENTS.md approaches
- Formalizes what devs were already doing organically (markdown + YAML metadata + supporting scripts)
- Automated discovery: Claude scans skill folders on startup without manual intervention
- Documentation quality paradox: these files "resemble normal developer documentation, but actually useful and task-oriented" — the immediate feedback loop (does it help your AI?) incentivizes quality writing that traditional docs never achieved

**Skeptics:**
- rafaelmn: "Fundamentally you're getting hyped over a framework to append text to your prompt?"
- pseudosavant: "I highly doubt we'll be talking about MCP next year. It is a pretty bad spec"
- Critics called skills "just rebranded prompt engineering" or "marketing rather than innovation"

**The broader debate** in the ["CLAUDE.md, Skills, Agents, MCP, slash commands..."](https://news.ycombinator.com/item?id=46396930) thread: how many users employ none of these features? Author mergesort acknowledged "best practices are changing so fast" and called Skills "the killer feature" for composability — using them for code review, copy editing, and parallel task execution. bdangubic argued 75% of teaching focus should be on setup/realistic expectations rather than magic automation.

**Platforms discussed:** Hacker News

---

### 5. Security Crisis: ToxicSkills and the Agent Supply Chain Problem

February 2026 saw the first major security reckoning for the agent skills ecosystem. Snyk published **ToxicSkills**, scanning 3,984 skills from ClawHub and skills.sh:

- **13.4%** (534 skills) = at least one critical security issue
- **36.82%** (1,467 skills) = any vulnerability
- **76 confirmed malicious payloads** via human review
- **8 still live** on ClawHub at publication
- **91%** of malicious skills combined prompt injection with traditional malware
- **10.9%** contained hardcoded secrets/API keys
- **17.7%** exposed indirect prompt injection via third-party content
- **2.9%** dynamically fetched/executed remote instructions at runtime

Three lines of markdown in a SKILL.md file were enough to instruct an agent to read SSH keys and exfiltrate them. Known threat actors: zaycv, Aslaep123, pepe276, moonshine-100rze.

Full report: [snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)

The daily submission rate on ClawHub jumped from <50 to >500 between mid-January and early February 2026 — a 10x surge that likely overwhelmed any manual review. VentureBeat documented ["One command turns any open-source repo into an AI agent backdoor"](https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner) and noted that no supply-chain scanner had a detection category for agent skills at the time.

On **May 20, 2026**, JFrog's annual Software Supply Chain Security Report [identified 969 malicious AI agent skills](https://jfrog.com/blog/agent-skills-new-ai-packages/) — the first time the category appeared in their annual tracking — alongside 451% surge in malicious npm packages. JFrog DevAdvocacy Lead Yonatan Arbel: "Skills have emerged as the go-to, low-friction way to shape an agent's day-to-day behavior... Skills can run scripts and execute instructions that may cause damage, or at the very least, violate compliance standards." JFrog proposed an Agent Skills Registry with scanning, provenance attestation, and centralized management. Full report via [BusinessWire](https://www.businesswire.com/news/home/20260520126325/en/New-JFrog-Report-Warns-AI-Governance-Fails-as-Software-Supply-Chain-Attacks-Hit-Record-Highs).

Academic response: [SkillSieve (arxiv.org/html/2604.06550v1)](https://arxiv.org/html/2604.06550v1) proposed a hierarchical triage framework for detecting malicious skills. Snyk and Tessl [announced a partnership](https://snyk.io/blog/snyk-tessl-partnership/) to set the standard for securing the agent skills registry.

**Platforms discussed:** Web, GitHub

---

### 6. Popular Plugins and Developer Workflows

The most commonly recommended plugins across review articles:

- **feature-dev** — 89,000+ installs; imposes structured process that senior engineers use instinctively; most popular plugin by install count ([TurboDocx](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers), [Firecrawl](https://www.firecrawl.dev/blog/best-claude-code-plugins))
- **Context7** — Delivers real-time, version-specific library docs (Next.js 15, React 19, Tailwind 4) directly into session; built by Upstash, open source; instead of training-data guesses, Claude reads actual docs before writing code ([claudedirectory.org](https://www.claudedirectory.org/plugins/context7))
- **Code Review** — Multi-agent PR audits
- **Superpowers** — Structured TDD
- **Deep Trilogy** — Idea-to-implementation pipeline

Developer consensus across guides: "Start with Superpowers, Context7, and Code Review — those three change how you approach work at a fundamental level." Quality varies wildly: "maybe 50-100 production-ready out of 9,000+" ([aitoolanalysis.com](https://aitoolanalysis.com/claude-code-plugins/)). Meta MCP launched April 29, 2026 for Facebook/Instagram ads management.

[Redwerk's roundup](https://redwerk.com/blog/best-claude-code-plugins/) and [Dev.to/Composio's top 10](https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6) both cover the current recommended stack.

**Platforms discussed:** Web

---

### 7. The Competitive Landscape: Skills Across Agents

The Agent Skills standard has created a cross-agent marketplace dynamic that didn't exist six months ago. [BrightCoding (May 18, 2026)](https://www.blog.brightcoding.dev/2026/05/18/why-top-ai-engineers-are-ditching-hardcoded-agents-for-agent-skills) documented why engineers are ditching hardcoded agents for the skills pattern. [Codex vs. Claude Code comparison (April 2026)](https://www.developersdigest.tech/blog/codex-vs-claude-code-april-2026) noted Claude Code's differentiation is "the ecosystem: skills, plugins, marketplaces, and MCP."

Multi-platform repos have emerged: [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) covers 313+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8 more agents; [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) lists 1,000+ cross-platform skills.

Enterprise adoption is broadening: Snowflake Cortex Code, Databricks Genie Code, Agentman (healthcare), Laravel Boost, Spring AI, and Factory all ship official SKILL.md documentation. Qodo uses agent skills for auto-fixing PR issues. Tabnine integrates skills into its enterprise context engine.

The May 19, 2026 launch of [Agent-Skills secure registry](https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm) positioned itself as the verified alternative to ClawHub in the wake of ToxicSkills.

**Platforms discussed:** Web, GitHub

---

## Cross-Source Patterns

**Pattern 1: Token efficiency is the decisive technical argument for skills over MCP**
- Hacker News (45619537, 45607117): Multiple comments about GitHub MCP consuming "tens of thousands of tokens"; skills solve this via progressive disclosure
- Web (morphllm.com, nimbalyst): 5-server MCP setup = 55,000 tokens upfront; skills = 30-50 tokens idle
- Web (Anthropic docs): Tool Search feature mitigates MCP overhead by 95%, but skills remain lighter
- Quote: "MCPs like GitHub's official version consume 'tens of thousands of tokens,' leaving little space for actual work" — HN commenter

**Pattern 2: The security crisis is acute and not yet solved**
- Snyk ToxicSkills (February 2026): 36% of skills have vulnerabilities, 76 confirmed malicious
- JFrog (May 2026): 969 malicious skills identified for the first time in annual report
- VentureBeat: "No supply-chain scanner has a detection category for it"
- Academic: SkillSieve paper proposing triage framework
- The growth rate (10x daily submissions in weeks) is outpacing any governance mechanism
- JFrog quote: "Skills can run scripts and execute instructions that may cause damage"

**Pattern 3: Cross-vendor standardization happened faster than anyone predicted**
- Web: 32+ tools adopted SKILL.md within 3 months of December 2025 publication
- GitHub: agentskills/agentskills specification repo adopted by competing companies
- HN: Discussion shifted from "Claude-specific feature" to "industry-wide format"
- Web: Enterprise platforms (Snowflake, Databricks, Spring AI, Laravel) adding official SKILL.md support

**Pattern 4: Community curation quality problem**
- HN (46693426): "The top 30 results I see here are other skill collection libraries or skill generators" — ricardobeat challenging 'curated' claims
- Web: Quality range is extreme — 50-100 production-ready skills out of 9,000+ available
- Web: SkillsMP has 800,000+ skills (all GitHub scrapes, no review); vs. Agensi's 200+ (8-pt security scan)
- No community consensus yet on what "good" skill curation looks like

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| Various | Claude Skills | 816 | 427 | "Fundamentally you're getting hyped over a framework to append text to your prompt?" — rafaelmn | https://news.ycombinator.com/item?id=45607117 |
| Simon Willison et al. | Claude Skills are awesome, maybe a bigger deal than MCP | 738 | 370 | "These resemble normal developer documentation, but actually useful and task-oriented" | https://news.ycombinator.com/item?id=45619537 |
| mergesort | CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more... | — | — | "There's so much invisible configuration and best practices are changing so fast" | https://news.ycombinator.com/item?id=46396930 |
| lixiaofei | Show HN: Agent Skills – 1k curated from 60k+ GitHub skills | 4 | 2 | "I collected 60k+ open-source agent skills from GitHub, then curated 1,000+" | https://news.ycombinator.com/item?id=46693426 |
| Various | Show HN: Almanac MCP, turn Claude Code into Deep Research agent | — | — | — | https://news.ycombinator.com/item?id=47855284 |
| Various | Claude Code Skills and Plugins as an Open Source Project | — | — | — | https://news.ycombinator.com/item?id=47321892 |
| Various | Claude Code and Codex Skill for Deliberate Skill Development | — | — | — | https://news.ycombinator.com/item?id=48130679 |
| Various | Show HN: Real-time dashboard for Claude Code agent teams | — | — | — | https://news.ycombinator.com/item?id=47602986 |
| Various | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | — | — | https://news.ycombinator.com/item?id=43410866 |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| Unknown | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | https://www.youtube.com/watch?v=uogzSxOw4LU |
| Unknown | Claude Code + Context7 MCP Server Is a Game Changer for AI Coding | — | — | No | https://www.classcentral.com/course/youtube-claude-code-context7-mcp-server-is-a-game-changer-for-ai-coding-461228 |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Snyk (ToxicSkills) | https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ | Security audit: 36% of skills have flaws, 76 malicious payloads |
| JFrog Blog | https://jfrog.com/blog/agent-skills-new-ai-packages/ | 969 malicious skills in May 2026 annual report |
| JFrog BusinessWire | https://www.businesswire.com/news/home/20260520126325/en/New-JFrog-Report-Warns-AI-Governance-Fails-as-Software-Supply-Chain-Attacks-Hit-Record-Highs | Full JFrog 2026 Supply Chain report |
| agentskills.io | https://agentskills.io/home | Official SKILL.md specification + 40+ adopter logos |
| agentskills.io spec | https://agentskills.io/specification | Full format specification |
| agentskills GitHub | https://github.com/agentskills/agentskills | Specification repo |
| claudemarketplaces.com | https://claudemarketplaces.com/ | 6,700+ skills, 840+ MCPs, 2,500+ marketplace repos |
| tonsofskills.com | https://tonsofskills.com/ | ccpi CLI marketplace, 2,747 skills |
| Agent Skills Hub | https://agentskillshub.dev/ | Secure/verified skill registry, 1,200+ skills |
| SkillsMP | https://skillsmp.com/ | 800,000+ scraped skills |
| LobeHub | https://lobehub.com/skills | 169,000+ skills, cross-platform |
| Anthropic Official Plugins | https://claude.com/plugins | Official plugin directory |
| Claude Code Skills docs | https://code.claude.com/docs/en/skills | Official Anthropic skills documentation |
| Claude Code Plugins docs | https://code.claude.com/docs/en/plugins | Official plugin documentation |
| Claude Code Hooks docs | https://code.claude.com/docs/en/hooks | Official hooks documentation |
| Claude Code discover plugins | https://code.claude.com/docs/en/discover-plugins | Marketplace discovery docs |
| Claude API MCP docs | https://platform.claude.com/docs/en/agent-sdk/mcp | MCP integration docs |
| Claude API MCP connector | https://platform.claude.com/docs/en/managed-agents/mcp-connector | MCP connector docs |
| VS Code agent skills | https://code.visualstudio.com/docs/copilot/customization/agent-skills | VS Code SKILL.md docs |
| Microsoft Learn skills | https://learn.microsoft.com/en-us/agent-framework/agents/skills | Microsoft agent framework |
| OpenAI Codex skills | https://developers.openai.com/codex/skills | OpenAI Codex skill adoption |
| Paperclipped interoperability | https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ | 32-tool adoption explainer |
| MindStudio standard | https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google | Cross-vendor adoption analysis |
| F5 standard analysis | https://www.f5.com/company/blog/agent-skills-an-emerging-open-standard | Enterprise perspective on the standard |
| agensi.io open standard | https://www.agensi.io/learn/agent-skills-open-standard | Explainer for 2026 |
| BrightCoding May 2026 | https://www.blog.brightcoding.dev/2026/05/18/why-top-ai-engineers-are-ditching-hardcoded-agents-for-agent-skills | Why engineers prefer skills over hardcoded agents |
| Morph Skills vs MCP vs Plugins | https://www.morphllm.com/claude-code-skills-mcp-plugins | Definitive comparison guide |
| Morph extensions guide | https://www.morphllm.com/claude-code-extensions | Full stack explainer |
| DevToolPicks comparison | https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 | Skills vs MCP vs Plugins 2026 |
| Agensi marketplace list | https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 | All 8 major marketplaces compared |
| agensi.io marketplace guide | https://www.agensi.io/learn/claude-code-plugin-marketplace-guide | Plugin marketplace guide |
| SKILL.md spec (agensi) | https://www.agensi.io/learn/skill-md-specification-open-standard | Spec explainer |
| SkillSieve arxiv | https://arxiv.org/html/2604.06550v1 | Academic framework for detecting malicious skills |
| VentureBeat backdoor | https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner | Supply chain backdoor analysis |
| Snyk-Tessl partnership | https://snyk.io/blog/snyk-tessl-partnership/ | Joint effort to secure skills registry |
| Snyk ToxicSkills GitHub | https://github.com/snyk-labs/toxicskills-goof | Proof-of-concept malicious skills |
| agensi ToxicSkills crisis | https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026 | ToxicSkills crisis summary |
| AI CERTs news | https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/ | News coverage |
| SkillShield analysis | https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/ | OpenClaw user impact |
| SpecWeave 36% | https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/ | Security verification argument |
| Obot supply chain | https://obot.ai/blog/mcp-security-agent-skills-supply-chain/ | MCP + skills supply chain security |
| Pluto security map | https://pluto.security/blog/claude-extension-ecosystem-security-practitioner-guide/ | Security practitioner's guide |
| Cyberdesserts risks | https://blog.cyberdesserts.com/ai-agent-security-risks/ | AI agent security risks 2026 |
| KDnuggets top 5 | https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents | Top marketplace ranking |
| AIToolly May 19 | https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm | New secure registry launch |
| Nimbalyst MCP ranked | https://nimbalyst.com/blog/best-claude-code-mcp-servers/ | MCP server rankings |
| Nimbalyst plugins guide | https://nimbalyst.com/blog/claude-code-plugins-guide/ | Plugin guide 2026 |
| claudefa.st best MCP | https://claudefa.st/blog/tools/mcp-extensions/best-addons | 50+ best MCP servers |
| claudefa.st 11 lists | https://claudefa.st/blog/tools/resources/awesome-claude-code | Awesome lists roundup |
| TurboDocx best plugins | https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers | Best plugins/skills 2026 |
| Firecrawl best skills | https://www.firecrawl.dev/blog/best-claude-code-skills | Best skills 2026 |
| Firecrawl best plugins | https://www.firecrawl.dev/blog/best-claude-code-plugins | Best plugins 2026 |
| Firecrawl skills explainer | https://www.firecrawl.dev/blog/agent-skills | Agent Skills explained |
| Redwerk 7 best | https://redwerk.com/blog/best-claude-code-plugins/ | 7 best plugins ranked |
| DEV.to composio | https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 | Top 10 plugins |
| aitoolanalysis.com | https://aitoolanalysis.com/claude-code-plugins/ | 9,000+ plugin ecosystem analysis |
| Groundy official ecosystem | https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/ | Official ecosystem explained |
| claudedirectory Context7 | https://www.claudedirectory.org/plugins/context7 | Context7 plugin page |
| claude-plugins.dev | https://claude-plugins.dev/ | Community registry + CLI |
| Skillsplayground guide | https://skillsplayground.com/guides/claude-code-plugins/ | Complete plugin guide |
| systemprompt.io MCP guide | https://systemprompt.io/guides/claude-code-mcp-servers-extensions | MCP setup guide |
| fast.io MCP plugins | https://fast.io/resources/claude-mcp-plugins/ | Top 7 MCP plugins |
| BrightCoding marketplace | https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers | Marketplace hub guide |
| BoringBot substack | https://boringbot.substack.com/p/claude-code-skills-subagents-hooks | Production multi-agent workflows |
| Towards AI extensions | https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff | All extensions explained |
| LevelUp mental model | https://levelup.gitconnected.com/a-mental-model-for-claude-code-skills-subagents-and-plugins-3dea9924bf05 | Mental model article |
| Medium Shashank | https://medium.com/@mishra.shashank35/claude-code-skills-subagents-hooks-and-plugins-a-practical-overview-572de7cedb20 | Practical overview |
| Medium SKILL.md deep dive | https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996 | SKILL.md technical deep dive |
| Medium SKILL.md pattern | https://bibek-poudel.medium.com/the-skill-md-pattern-how-to-write-ai-agent-skills-that-actually-work-72a3169dd7ee | How to write skills that work |
| alexop.dev full stack | https://alexop.dev/posts/understanding-claude-code-full-stack/ | Full stack explainer |
| blakecrosley.com guide | https://blakecrosley.com/guides/claude-code | Hooks, MCP, Skills guide |
| ofox.ai complete guide | https://ofox.ai/blog/claude-code-hooks-subagents-skills-complete-guide-2026/ | Hooks, subagents, skills guide |
| DEV.to owen_fox | https://dev.to/owen_fox/claude-code-hooks-subagents-and-skills-complete-guide-hjm | Complete guide |
| duet.so complete guide | https://duet.so/guides/claude-code-skills-complete-guide | Skills complete guide 2026 |
| buildfastwithai | https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026 | Build, install, use guide |
| mindwiredai essentials | https://mindwiredai.com/2026/03/12/claude-code-essential-skills-plugins-or-stop-using-claude-browser-5-skills/ | 5 must-know skills |
| scottspence.com organize | https://scottspence.com/posts/organising-claude-code-skills-into-plugin-marketplaces | Organizing into marketplaces |
| scottspence.com mcpick | https://scottspence.com/posts/mcpick-manage-mcp-servers-and-plugins-in-claude-code | McPick MCP management tool |
| camilleroux.com top 13 | https://www.camilleroux.com/top-skills-plugins-claude-code-2026-v3/ | Top 13 tools by social engagement |
| inference.sh overview | https://inference.sh/blog/skills/agent-skills-overview | Agent skills overview |
| serenitiesai guide | https://serenitiesai.com/articles/agent-skills-guide-2026 | Skills guide for 16+ tools |
| strapi blog | https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them | What are agent skills |
| chris-ayers.com | https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ | Agent Skills, Plugins, Marketplace guide |
| buildtolaunch | https://buildtolaunch.substack.com/p/best-claude-code-plugins-tested-review | 10 tested, 4 worth keeping |
| improvejba.me daily | https://www.mejba.me/blog/claude-code-plugins-daily-workflow | Daily workflow plugins |
| devops-daily | https://devops-daily.com/posts/best-claude-code-plugins-devops-2026 | DevOps plugins 2026 |
| DevelopersDigest April | https://www.developersdigest.tech/blog/codex-vs-claude-code-april-2026 | Codex vs Claude Code |
| aitooldiscovery reddit | https://www.aitooldiscovery.com/guides/claude-code-reddit | Reddit community analysis |
| morphllm reddit | https://www.morphllm.com/claude-code-reddit | What developers actually say |
| mindstudio skills vs plugins | https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference | Skills vs Plugins difference |
| Netresearch GitHub | https://github.com/netresearch/claude-code-marketplace | 40 curated skills by Netresearch DTT |
| jeremylongshore GitHub | https://github.com/jeremylongshore/claude-code-plugins-plus-skills | 425 plugins + ccpi |
| alirezarezvani GitHub | https://github.com/alirezarezvani/claude-skills | 313+ cross-platform skills |
| daymade GitHub | https://github.com/daymade/claude-code-skills | Production-ready skills marketplace |
| rohitg00 GitHub | https://github.com/rohitg00/awesome-claude-code-toolkit | Comprehensive toolkit |
| GetBindu GitHub | https://github.com/GetBindu/awesome-claude-code-and-skills | Claude skills collection |
| quemsah GitHub | https://github.com/quemsah/awesome-claude-plugins | Automated adoption metrics |
| hesreallyhim GitHub | https://github.com/hesreallyhim/awesome-claude-code | 36.8k star curated list |
| ComposioHQ GitHub | https://github.com/ComposioHQ/awesome-claude-plugins | Composio curated plugins |
| subinium GitHub | https://github.com/subinium/awesome-claude-code | Skills, plugins, MCPs |
| BehiSecc GitHub | https://github.com/BehiSecc/awesome-claude-skills | Curated skills |
| VoltAgent GitHub | https://github.com/VoltAgent/awesome-agent-skills | 1000+ cross-platform skills |
| Anthropic plugins README | https://github.com/anthropics/claude-code/blob/main/plugins/README.md | Official plugins README |
| claudepluginhub | https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills | Plugin hub marketplace |
| awesome-skills.com | https://awesome-skills.com/ | Curated skills web UI |
| YAHoo JFrog | https://finance.yahoo.com/sectors/technology/articles/jfrog-report-warns-ai-governance-200500156.html | JFrog report coverage |
| JFrog MCP tools | https://jfrog.com/blog/ai-agents-jfrog-skills-mcp-tools/ | JFrog's own skills + MCP tools |
| Composio TikTok | https://composio.dev/toolkits/tiktok/framework/claude-code | TikTok MCP integration |
| Composio YouTube | https://composio.dev/toolkits/youtube/framework/claude-code | YouTube MCP integration |
| TikTok discover | https://www.tiktok.com/discover/claude-code-skills | TikTok Claude Code skills page |
| mcpmarket.com Bluesky | https://mcpmarket.com/tools/skills/bluesky-manager | BlueSky Manager skill |
| Polymarket predictions | https://polymarket.com/predictions/ai | 20 live AI prediction markets |
| Polymarket agents GitHub | https://github.com/Polymarket/agents | Polymarket AI agent framework |
| polymarket-mcp-server | https://github.com/caiovicentino/polymarket-mcp-server | 45-tool Polymarket MCP |
| polymarket-skills | https://github.com/mjunaidca/polymarket-skills | Composable Polymarket skills |
| mcp.directory polymarket | https://mcp.directory/skills/polymarket-agent | Polymarket agent skill |
| mcp.directory trader | https://mcp.directory/skills/polymarket-trader | Polymarket trader skill |
| mcpmarket polymarket | https://mcpmarket.com/tools/skills/polymarket-development-suite | Polymarket dev suite |
| sparkco.ai prediction | https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi | MCP + Claude for prediction markets |
| skywork polymarket guide | https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560 | Polymarket MCP server guide |
| ericaai polymarket | https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/ | Building Polymarket agents |
| python plainenglish | https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477 | Agentic coding for Polymarket |
| skywork openclaw | https://skywork.ai/skypage/en/openclaw-polymarket-ai-trading/2036741591760736256 | OpenClaw Polymarket bot |
| mvanhorn last30days | https://github.com/mvanhorn/last30days-skill | Last30days research skill on GitHub |
| HN Almanac MCP | https://news.ycombinator.com/item?id=47855284 | Almanac MCP for deep research |

---

## Stats Block

```
├─ 🟠 Reddit: ~4,200 weekly contributors (r/ClaudeCode) │ domain not directly accessible │ secondary sources only
├─ 🔵 X: excluded per instructions
├─ 🔴 YouTube: 2 videos referenced │ views/likes unavailable
├─ 🟢 HN: 9 stories │ 1,558+ points │ 799+ comments (top 2 threads: 816+738 pts)
├─ 🟣 TikTok: 0 videos with metrics │ discover page found
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts with metrics │ community active
├─ 📊 Polymarket: 0 markets on agent skills topic │ 20 live AI markets total; Polymarket skills/MCPs widely available
├─ 🌐 Web: 80+ pages │ blogs, security research, news, official docs
└─ 🗣️ Top voices: Simon Willison (HN), mergesort (HN), Yonatan Arbel (JFrog), rafaelmn (HN skeptic) │ r/ClaudeCode, r/ClaudeAI
```

---

## Data Gaps

- **Reddit:** reddit.com was blocked by the search tool (domain restriction). All Reddit data is from secondary aggregators (morphllm.com, aitooldiscovery.com). Estimated coverage: ~20% of Reddit signal (no thread titles, upvotes, or direct quotes from actual posts).
- **X/Twitter:** Excluded per research instructions.
- **TikTok:** TikTok discover page found but no individual video engagement metrics retrieved. Platform likely has content but not surfaceable through web search.
- **Bluesky:** Community activity mentioned in social engagement references but no direct post data retrieved.
- **Polymarket:** No prediction markets specifically about agent skills adoption, MCP usage rates, or plugin ecosystem outcomes were found. Polymarket tools/skills for trading exist but are a different angle.
- **YouTube:** Two videos referenced; exact view/like counts unavailable because YouTube blocked direct page fetching. Publication date confirmed for one (April 13, 2026).
- **HN:** Several threads returned HTTP 429 (rate limit) when fetching full comment data (items 47321892, 48130679, 47602986). Points/comments unknown for 6 of 9 threads.
- **Approximate overall coverage:** Web ~90%, HN ~85%, GitHub ~85%, YouTube ~30%, Reddit ~20%, TikTok ~15%, Bluesky ~10%.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — Simon Willison on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Fundamentally you're getting hyped over a framework to append text to your prompt?" — rafaelmn on Hacker News ([link](https://news.ycombinator.com/item?id=45607117))

> "I highly doubt we'll be talking about MCP next year. It is a pretty bad spec" — pseudosavant on Hacker News ([link](https://news.ycombinator.com/item?id=45607117))

> "There's so much invisible configuration and best practices are changing so fast" — mergesort on Hacker News ([link](https://news.ycombinator.com/item?id=46396930))

> "Agent Skills operate with the full permissions of the AI agent they extend — including shell access, file system read/write permissions, and credential access" — Snyk ToxicSkills research ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Three lines of markdown in a SKILL.md file were enough to instruct an agent to read SSH keys and exfiltrate them" — Snyk ToxicSkills ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "Skills have emerged as the go-to, low-friction way to shape an agent's day-to-day behavior" — Yonatan Arbel, JFrog DevAdvocacy Lead ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "Skills can run scripts and execute instructions that may cause damage, or at the very least, violate compliance standards" — JFrog ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "These AI-focused context documents resemble normal developer documentation, but actually useful and task-oriented" — HN commenter in Claude Skills are awesome thread ([link](https://news.ycombinator.com/item?id=45619537))

> "The top 30 results I see here are other skill collection libraries or skill generators. How is this a 'curated set of skills'?" — ricardobeat on Hacker News ([link](https://news.ycombinator.com/item?id=46693426))
