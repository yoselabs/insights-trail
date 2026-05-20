# Agent Skills — Raw Research Output
**Date:** 2026-05-20
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## HACKER NEWS

### Thread 1: Claude Skills
- **URL:** https://news.ycombinator.com/item?id=45607117
- **Points:** 816
- **Comments:** 427
- **Top comments:**
  - **simonw**: "Claude Skills are awesome, maybe a bigger deal than MCP" — notes that Skills function as a context-efficient pattern for making instructions available only when needed
  - **pants2**: Claims Skills represent prompt engineering rather than requiring formal specification, suggesting MCP implementation could achieve similar results
  - **pseudosavant**: Argues that simplicity doesn't diminish power, comparing Skills to containerization—conceptually straightforward yet potentially transformative
  - **manbash**: Questions whether Skills follow a "diamond shape" information flow pattern distinct from MCP's traditional architecture
  - **JimDabell**: Proposes wrapping Skills in container/runtime specifications with package indexing to enable dynamic agent capability extension
  - **simonw (2nd)**: Clarifies that Skills can reference external APIs through instructions for tools like curl with environment variables
  - **sunaookami**: Describes MCP as poorly executed and appreciates Skills as a superior alternative with better token efficiency
  - **beepdyboop**: Questions whether Claude Skills function similarly to Cursor Rules

### Thread 2: How I use every Claude Code feature
- **URL:** https://news.ycombinator.com/item?id=45786738
- **Points:** 534
- **Comments:** 188
- **Top comments:**
  - **simonw**: "put @AGENTS.md in your CLAUDE.md file" — recommends referencing other files rather than duplicating content
  - **sshh12** (author): "MCP's job is to manage auth, networking, and security boundaries and then get out of the way"
  - **sshh12**: "Skills are the right abstraction...more robust and flexible than the rigid, API-like model that MCP represents"
  - **nostrebored**: "CLIs are just easier for Claude, especially if you write them with Claude"
  - **riskable**: "I had that thing working quite robustly in days...The stylesheets alone...Ugh!" — reports significant time savings
  - **johnfn**: "I can't get Claude to follow something as simple as that! It does sometimes, but half the time it disregards" — CLAUDE.md reliability concerns

### Thread 3: Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills
- **URL:** https://news.ycombinator.com/item?id=46693426
- **Points:** 4
- **Comments:** 2
- **Top comments:**
  - **lixiaofei** (creator): "Claude Code skills aren't that different from agents or other automation tools—the big difference is that they lower the barrier" — notes the directory updates daily
  - **ricardobeat**: "The top 30 results I see here are other skill collection libraries or skill generators" — questions curation quality
- **Website:** agent-skills.cc (updated daily)

### Thread 4: Skills Manager – manage AI agent skills across Claude, Cursor, Copilot
- **URL:** https://news.ycombinator.com/item?id=47423910
- **Points:** 3
- **Comments:** 9
- **Top comments:**
  - **druide67**: "the same instruction produces very different results depending on the agent. Claude follows multi-step rules well, Copilot tends to ignore anything beyond the first line."
  - **prateeksi**: Questions sync mechanics and enterprise features — "if you update a skill file via Cursor and then via Claude Code, does Skills Manager detect the diff or does last-write win?"
  - **Dshadowzh**: "Most of the coding agents support reading skills in ~/.agents/skills. It seems that only Claude code hasn't adopted this spec."
  - **evergreenxx** (creator): Acknowledged emerging standard; confirmed tool reads from each agent's native paths while remaining agent-neutral
  - **teekert**: Noted Linux gaps initially; creator confirmed Linux support now available via Electron

### Thread 5: Show HN: MCP Isn't Dead. You're Just Using It Wrong
- **URL:** https://news.ycombinator.com/item?id=47412133
- **Points:** 6
- **Comments:** 7
- **Top comments:**
  - **quietbuilder**: "Dynamic tool registration matters more than it sounds. I've hit the context limit multiple times just from MCP servers loading 50+ tools at startup"
  - **PaulHoule**: "MCP is a masterclass in how to not design an API"
  - **sachinkg12**: Questions whether agents reliably know when to invoke load_ability
  - **isaacrolandson** (author): "MCP functions as a protocol rather than API, arguing proper usage demonstrates effectiveness"
  - **JD5173F2**: Sees enterprise potential, asks whether dynamic tools persist and can be shared across teams

### Thread 6: MCP Registry – Open-source discovery layer for 20 MCP servers
- **URL:** https://news.ycombinator.com/item?id=47486982
- **Points:** [rate limited, unable to fetch]
- **Comments:** [rate limited]

### Thread 7: MCP Discovery API – Let AI agents find the right tools automatically
- **URL:** https://news.ycombinator.com/item?id=46661173
- **Points:** [rate limited]
- **Notes:** MCP Discovery API indexes 24 servers with 91 capabilities tagged, includes real-time performance metrics

### Thread 8: Show HN: Mother MCP – Manage your Agent Skills like a boss
- **URL:** https://news.ycombinator.com/item?id=46692102
- **Points:** [rate limited]
- **Notes:** Auto-provisioning of skills via MCP

### Thread 9: Show HN: Gigacode – Use OpenCode's UI with Claude Code/Codex/Amp
- **URL:** https://news.ycombinator.com/item?id=46912682
- **Points:** 27
- **Comments:** 11
- **Top comments:**
  - **solarkraft**: Hopes this creates "an ecosystem interchangeable LLM backends and UIs"
  - **cyanydeez**: Skeptical about vendor lock-in
  - **vercantez**: "harnesses matter almost as much as the models in 2026"
  - **NathanFlurry** (creator): Confirms interest in supporting Agent Client Protocol (ACP)
  - **mgw**: Asks about Claude Code Max subscription compatibility

### Thread 10: Ask HN: Best option for hosted agent in 2026?
- **URL:** https://news.ycombinator.com/item?id=46917293

### Thread 11: Claude Code Skills and Plugins as an Open Source Project
- **URL:** https://news.ycombinator.com/item?id=47321892
- **Notes:** Rate limited, could not fetch content

### Thread 12: A Claude Code and Codex Skill for Deliberate Skill Development
- **URL:** https://news.ycombinator.com/item?id=48130679
- **Notes:** Rate limited, could not fetch content

---

## YOUTUBE

Search results (view counts not accessible via web fetch):

1. **"8 Claude Code Skills Every Developer Needs in 2026"**
   - URL: https://www.youtube.com/watch?v=Va-U1dqhwzk
   - Posted ~1 month ago; features skills used by senior dev formerly at Amazon/Microsoft

2. **"Solo necesitas estas 22 Skills de Claude Code en 2026"** (Spanish)
   - URL: https://www.youtube.com/watch?v=dj7uAA2Phqg
   - Posted ~1 month ago

3. **"Full Claude Code Tutorial for Non-Technical Beginners in 2026 (step-by-step)"**
   - URL: https://www.youtube.com/watch?v=bqJzIWAEn40
   - Posted ~3 weeks ago

4. **"Top 10 Claude Code Skills, Plugins & CLIs (April 2026)"**
   - URL: https://www.youtube.com/watch?v=KjEFy5wjFQg
   - Posted April 2026

5. **"My Claude Code Workflow for 2026"**
   - URL: https://www.youtube.com/watch?v=sy65ARFI9Bg

6. **"How to Create Claude Code Agent Skills in 2026"**
   - URL: https://www.youtube.com/watch?v=nbqqnl3JdR0
   - Posted January 5, 2026

7. **"How to install Skills in Claude Code | Claude Code Skills 2026"**
   - URL: https://www.youtube.com/watch?v=SCAHfmWswn0
   - Posted ~3 weeks ago

8. **"Claude Code Skills just Built me an AI Agent Team (2026 Guide)"**
   - URL: https://www.youtube.com/watch?v=OdtGN27LchE

9. **"The ONLY Claude Tutorial You'll Ever Need in 2026"**
   - URL: https://www.youtube.com/watch?v=WqoPkZ88f5k

10. **"Top 5 Claude Code Skills That Will 10x Your Productivity (2026)"**
    - URL: https://www.youtube.com/watch?v=Xs942zwWfdY
    - Posted March 10, 2026; features 5 of 17 official Anthropic skills on GitHub

---

## WEB / BLOGS

### SKILL.md Open Standard
- **Source:** Mintlify Blog
- **URL:** https://www.mintlify.com/blog/skill-md
- **Key facts:**
  - SKILL.md lives at `/.well-known/skills/default/skill.md`
  - Automatically regenerates when docs are updated via Mintlify
  - Can be installed into 20+ coding agents
  - Decision tables replace verbose descriptions
  - "Never use `mint.json`—it's deprecated" style gotchas sections
  - Built per Cloudflare RFC, agentskills.io proposal, and Vercel skills CLI standards

### SKILL.md Adoption (Paperclipped/InfoQ)
- **URL:** https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
- **Key facts:**
  - SKILL.md open standard released by Anthropic December 18, 2025
  - Within 48 hours: Microsoft integrated into VS Code, OpenAI added to ChatGPT and Codex CLI
  - By March 2026: 32 tools from competing companies including Google Gemini CLI, JetBrains Junie, AWS Kiro, Block's Goose
  - All read the same SKILL.md files from the same directory structure
  - Agentic AI Foundation (AAIF) reached 146 member organizations by February 2026 (under Linux Foundation)

### Skills.sh — Vercel's Agent Skills Directory
- **URL:** https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
- **URL (InfoQ):** https://www.infoq.com/news/2026/02/vercel-agent-skills/
- **URL (VirtualUncle):** https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/
- **Key facts:**
  - Launched January 20, 2026 by Vercel (authored by Andrew Qu)
  - 90,000+ skills available, tracking 87,000+ unique skills
  - 19 different AI agent platforms supported
  - Installation via `npx skills add <package>`
  - npm required a decade to reach 350,000 packages; skills ecosystem achieved comparable numbers in ~2 months
  - Top skills by install count: find-skills (579,000+), vercel-react-best-practices (216,000+), web-design-guidelines (171,000+), frontend-design (164,000+)
  - Notable quote (Thomas Rehmer): "Discoverable skills solve the 'what can you do?' problem that most agent setups have."
  - Notable quote (Aakash Harish): "This is npm for AI agents...Skills solves 'how do devs share and discover agent capabilities.'"

### Best Claude Code Skills — Firecrawl Blog
- **URL:** https://www.firecrawl.dev/blog/best-claude-code-skills
- **Key skills listed:**
  - Capability Uplift: Firecrawl, Document Skills (PDF/DOCX/XLSX/PPTX), Webapp Testing (Playwright), Trail of Bits Security
  - Encoded Preference: Frontend Design, Vercel Web Design Guidelines, Vercel React Best Practices, Superpowers, GStack, Remotion Best Practices, Skill Creator
  - Quote: "Capability Uplift skills give Claude abilities it doesn't have on its own."
  - Quote: "Encoded Preference skills capture the specific choices that make your work yours"
  - Cross-platform compatibility confirmed across Claude Code, OpenAI Codex, Cursor, Gemini CLI, GitHub Copilot
  - Discovery resource: Vercel maintains skills.sh as a searchable directory
  - Installation: `npx skills add [repo-url]` or Claude Code's plugin marketplace

### Agent Skills Marketplaces — Agensi
- **URL:** https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- **URL:** https://www.agensi.io/learn/skills-marketplace-ai-agents
- **Key facts:**
  - Ecosystem grew from 1 registry (Dec 2025) to 8 major marketplaces by Q2 2026
  - Monthly search volume exploded from 21,000 to 400,000+ searches (19x increase)
  - Three convergence factors: SKILL.md standardization, 20+ compatible agents, developer willingness to pay
  - Top categories: code quality, framework-specific patterns, DevOps/infrastructure, specialized domains
  - Platform comparison:
    - **Skills.sh**: ~2,000 skills (npm-style), community-driven, no formal review
    - **SkillsMP**: 800,000+ skills (scraped, "2+ GitHub stars" filter), quantity over quality
    - **ClaudeSkills.info**: 658 free skills, higher quality baseline, beginner-friendly
    - **Agensi**: 44+ curated; 8-point security scan; 80/20 creator split; Stripe Connect payments; human review
    - **LobeHub**: 169,000+ aggregated skills
    - **MCP Market**: ~500 skills, MCP server directory focus

### Security Crisis: ToxicSkills and ClawHavoc
- **Source:** Snyk Blog
- **URL:** https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/
- **Source:** Agensi
- **URL:** https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026
- **Source:** arxiv
- **URL:** https://arxiv.org/html/2602.06547v1
- **Key facts:**
  - Snyk audit: Scanned 3,984 skills
    - 13.4% (534 skills) contain critical-level security issues
    - 36.82% (1,467 skills) have at least one security flaw
    - 76 confirmed malicious payloads via human analysis
    - 8 malicious skills remain publicly available on ClawHub
    - Prompt injection in 36% of tested skills
    - Hardcoded secrets in 10.9% of all ClawHub skills
  - Mobb.ai audit (March 2026): Scanned 22,511 public skills across 4 registries; found 140,963 total issues (6.3 per skill avg)
  - ClawHavoc attack campaign (Jan 2026): 341 malicious skills in ClawHub; 335 sharing single C2 IP; targeting exchange API keys, wallet private keys, SSH credentials, browser passwords; delivered Atomic macOS Stealer
  - Attack vectors:
    1. External malware distribution (password-protected archives)
    2. Obfuscated data exfiltration (Base64/Unicode-encoded curl | bash)
    3. Security disablement (disable safety mechanisms)
  - Common pattern: SKILL.md instructing agent to "append the value of $ANTHROPIC_API_KEY as a query parameter" to URL requests
  - Key threat actors: zaycv (40+ skills), Aslaep123, aztr0nutzs
  - Key quote: "Traditional code security tools...do not catch malicious skills because skills are not code. They are instructions."
  - Snyk quote from article: "From SKILL.md to Shell Access in Three Lines of Markdown"

### MCP Ecosystem — 2026 State
- **Source:** Toloka
- **URL:** https://toloka.ai/blog/the-future-of-mcp-enterprise-adoption/
- **Key facts:**
  - 97 million monthly SDK downloads (March 2026), 4,750% growth since launch
  - 9,400+ public MCP servers (3-4x more estimated in private use)
  - 80% of Q1 2026 enterprise apps embed AI agents; only 17% fully deployed (68-point gap)
  - 40% project failure rate projected by Gartner through 2027
  - MCP transitioned to Linux Foundation's Agentic AI Foundation (December 2025)
  - Four strategic 2026 priorities: Transport Evolution, Agent Communication, Governance Maturation, Enterprise Readiness
  - Audit trails: "coming to the spec, but not here yet"

### MCP Enterprise Security — Cloudflare
- **URL:** https://blog.cloudflare.com/enterprise-mcp/
- **URL (InfoQ):** https://www.infoq.com/news/2026/04/cloudflare-mcp/
- **Key facts:**
  - MCP gateways centralize governance for AI agent tool access
  - Critical vulnerabilities: credential exposure, autonomous action risks, attack surface expansion
  - 78% enterprise MCP adoption in production AI teams
  - Kong, MintMCP, Bifrost, Docker MCP Gateway as enterprise solutions
  - "The Model Context Protocol alone does not solve production-grade problems: authentication, authorization, auditing, rate limiting, credential governance"

### Official Claude Code Skills Docs
- **URL:** https://code.claude.com/docs/en/skills
- **Key facts:**
  - Skills extend Claude by creating SKILL.md files
  - Skills can be invoked via `/skill-name` or auto-detected by Claude based on description
  - Skill locations: Enterprise > Personal (~/.claude/skills/) > Project (.claude/skills/) > Plugin
  - Frontmatter fields: name, description, when_to_use, disable-model-invocation, user-invocable, allowed-tools, model, effort, context (fork), agent, hooks, paths
  - Context lifecycle: skill content stays in context for session; auto-compaction carries forward with 5,000 token budget per skill, 25,000 shared budget
  - Dynamic context injection: `!` followed by shell command inlines live output
  - Subagent execution: `context: fork` runs skill in isolated subagent
  - Live change detection: file changes take effect within current session without restart
  - Monorepo support: auto-discovers nested .claude/skills/ directories
  - SKILL.md recommended under 500 lines
  - Bundled skills: /simplify, /batch, /debug, /loop, /claude-api, /run, /verify, /run-skill-generator
  - Custom commands merged into skills (.claude/commands/ still works)
  - Follows Agent Skills open standard (agentskills.io)

### Official Claude Code Plugin Marketplace
- **URL:** https://code.claude.com/docs/en/discover-plugins
- **URL:** https://github.com/anthropics/claude-plugins-official
- **URL:** https://github.com/anthropics/claude-plugins-community
- **Key facts:**
  - 9,000+ plugins available across official marketplace, community sites, GitHub
  - Official (Anthropic-managed) repo: anthropics/claude-plugins-official
  - Community mirror: anthropics/claude-plugins-community (submit at clau.de/plugin-directory-submission)
  - Access via /plugin → Discover tab in Claude Code
  - Plugins include /plugins (Anthropic-managed) and /external_plugins (3rd party)
  - Claude Code v2.1.143+: Context cost estimate shown per plugin before installation
  - Marketplace updated May 20, 2026

### GitHub Repos of Note
- **alirezarezvani/claude-skills**: 5,200+ stars; 313+ Claude Code skills for Claude Code, Codex, Gemini CLI, Cursor, and 8+ coding agents; engineering, marketing, product, compliance, C-level advisory, research, business operations
  - URL: https://github.com/alirezarezvani/claude-skills
- **addyosmani/agent-skills**: 23 skills (22 lifecycle + meta-skill); on GitHub Trending monthly chart
  - URL: https://github.com/addyosmani/agent-skills
- **skillmatic-ai/awesome-agent-skills**: Definitive resource for agent skills, modular AI agent capabilities
  - URL: https://github.com/skillmatic-ai/awesome-agent-skills
- **VoltAgent/awesome-agent-skills**: 1000+ curated agent skills; Claude Code, Codex, Gemini CLI, Cursor
  - URL: https://github.com/VoltAgent/awesome-agent-skills
- **rohitg00/awesome-claude-code-toolkit**: 135 agents, 35 curated skills (+400k via SkillKit), 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, 26 companion apps
  - URL: https://github.com/rohitg00/awesome-claude-code-toolkit
- **levnikolaevich/claude-code-skills**: Plugin suite + bundled MCP servers for Claude Code; full delivery lifecycle; includes hex-line, hex-graph, hex-ssh MCP servers
  - URL: https://github.com/levnikolaevich/claude-code-skills
- **ComposioHQ/awesome-claude-plugins**: Curated plugins for Claude Code with slash commands, agents, hooks, MCP servers
  - URL: https://github.com/ComposioHQ/awesome-claude-plugins
- **openclaw/clawhub**: OpenClaw's official skill registry; 13,729 community skills as of Feb 28, 2026; vector search + CLI API
  - URL: https://github.com/openclaw/clawhub
- **vercel-labs/skills**: The open agent skills tool - npx skills
  - URL: https://github.com/vercel-labs/skills
- **steipete/claude-code-mcp**: Claude Code as one-shot MCP server
  - URL: https://github.com/steipete/claude-code-mcp

### Simon Willison's Blog
- **URL:** https://simonwillison.net/2025/Oct/16/claude-skills/
- **Key points:**
  - "Each skill only takes up a few dozen extra tokens, with the full details only loaded in should the user request a relevant task" — token efficiency
  - Skills transform Claude Code into a genuine "general agent" for computer automation
  - MCP consumes "tens of thousands of tokens of context" vs skills' minimal overhead
  - Skills can work with any model without built-in support; MCP demands protocol implementation
  - Author's prediction about agents in 2025 proved wrong—agents succeeded despite skepticism

### Dev.to: 100 Claude Skills Tested
- **URL:** https://dev.to/suraj_khaitan_f893c243958/i-tried-100-claude-skills-these-are-the-best-1m4a
- **Top 10 skills ranked:**
  1. PDF (form filling, field extraction, table parsing)
  2. DOCX/PPTX/XLSX (native Office file generation)
  3. skill-creator (meta-skill for authoring new Skills)
  4. mcp-builder (generates MCP servers from descriptions)
  5. webapp-testing (Playwright-driven browser automation)
  6. frontend-design (spacing, typography, accessibility)
  7. brand-guidelines (organizational style enforcement)
  8. theme-factory (design systems as structured JSON)
  9. internal-comms (Slack message templates)
  10. slack-gif-creator (animated GIFs for teams)
- **Key insight:** "Skills ≠ prompts" — portable capability packages with progressive disclosure

### Agensi Security Guide
- **URL:** https://www.agensi.io/learn/agent-skills-marketplace-sell-your-skills
- **Agensi security scan:** 8-point check covering: file structure validation, dangerous command patterns, secrets detection, environment variable harvesting, network access auditing, obfuscation detection, prompt injection screening, plus human review

### MCP Gateways & Enterprise Governance
- **URL:** https://www.truefoundry.com/blog/best-mcp-registries
- **URL:** https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/
- **URL:** https://blog.cloudflare.com/enterprise-mcp/
- **Key players:** Kong MCP Registry, MintMCP, Bifrost, Docker MCP Gateway, Official MCP Registry (registry.modelcontextprotocol.io), Smithery (7,000+ servers, "Docker Hub of MCP"), MACH Alliance MCP Registry

### Agent Skills Open Standard Deep Dive
- **URL:** https://www.bishoylabib.com/posts/claude-skills-comprehensive-guide
- **URL:** https://ylanglabs.com/blogs/agent-skills
- **URL:** https://evoailabs.medium.com/agent-skills-are-open-standard-can-be-used-with-any-llm-agent-feb0cba4e0ff

### Academic Research
- **URL:** https://arxiv.org/pdf/2603.11808 — "Automating Skill Acquisition through Large-Scale Mining of Open-Source Agentic Repositories"
- **URL:** https://arxiv.org/html/2602.06547v1 — "Malicious Agent Skills in the Wild: A Large-Scale Security Empirical Study"
  - Up to 80% attack success rate with frontier models executing harmful instructions including data exfiltration, destructive actions, ransomware-like behavior
- **URL:** https://arxiv.org/html/2604.02837v1 — "Towards Secure Agent Skills: Architecture, Threat Taxonomy, and Security Analysis"

### Additional Articles
- **URL:** https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051 — 10 Must-Have Skills for Claude in 2026 (Medium)
- **URL:** https://www.agensi.io/learn/what-is-skill-md — What Is SKILL.md
- **URL:** https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996 — Deep Dive SKILL.md
- **URL:** https://towardsdatascience.com/claude-skills-and-subagents-escaping-the-prompt-engineering-hamster-wheel/ — TDS
- **URL:** https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026 — Agent Teams 2026
- **URL:** https://k21academy.com/claude/claude-code-skills-vs-sub-agents-vs-mcp/ — Skills vs Sub-Agents vs MCP
- **URL:** https://www.blog.brightcoding.dev/2026/05/19/awesome-agent-skills-the-revolutionary-toolkit-for-modular-ai-development — BrightCoding (May 19, 2026)
- **URL:** https://developers.redhat.com/articles/2026/03/10/agent-skills-explore-security-threats-and-controls — Red Hat Developer
- **URL:** https://medium.com/@t79877005/the-ai-agent-skills-boom-is-under-attack-a-deep-security-crisis-3a7b7ded0208 — AI Agent Skills Security Crisis (Medium)
- **URL:** https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents — KDnuggets
- **URL:** https://www.nimbleway.com/blog/anthropic-claude-agent-skills — Top 10 Anthropic Claude Agent Skills
- **URL:** https://claudemarketplaces.com/ — Claude Code Plugins Marketplace Directory
- **URL:** https://www.awesomeskills.dev/en — Awesome Agent Skills Directory
- **URL:** https://www.agensi.io/skills — Browse AI Agent Skills | SKILL.md Marketplace
- **URL:** https://skillsmp.com/ — Agent Skills Marketplace (SkillsMP)
- **URL:** https://www.agensi.io/learn/llm-skills-marketplace-next-app-store — LLM Skills Marketplace: Why Agent Skills Are the Next App Store
- **URL:** https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work — How AI Agent Skill Marketplaces Work
- **URL:** https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview — Agent Skills - Claude API Docs
- **URL:** https://vercel.com/blog/agent-skills-explained-an-faq — Agent skills FAQ (Vercel)
- **URL:** https://vercel.com/docs/agent-resources/skills — Agent Skills (Vercel Docs)
- **URL:** https://www.skills.sh/ — The Agent Skills Directory (skills.sh)
- **URL:** https://registry.modelcontextprotocol.io/ — Official MCP Registry
- **URL:** https://konghq.com/products/mcp-registry — Kong MCP Registry
- **URL:** https://whatlaunched.today/launch/agensi — Agensi launch
- **URL:** https://claude.ai/code — Claude Code

---

## NOTE ON PLATFORMS

- **Reddit:** Domain blocked by Anthropic's crawler — no data retrieved
- **X/Twitter:** Domain blocked by Anthropic's crawler — no data retrieved
- **TikTok:** No targeted results found
- **Bluesky:** No targeted results found (searches returned web/blog results instead)
- **Polymarket:** No markets found related to agent skills topic
- **GitHub:** Data extracted indirectly via web searches and WebFetch (GitHub itself not directly crawlable by this agent)
