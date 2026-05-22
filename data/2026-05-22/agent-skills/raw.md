# Agent Skills — Raw Research Output
**Date:** 2026-05-22
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## WEB SEARCH RESULTS

### Search 1: "Claude Code skills plugins agent marketplace 2026"

Results:
- https://www.agensi.io/learn/claude-code-plugin-marketplace-guide — Claude Code Plugin Marketplace Guide (2026)
- https://claudemarketplaces.com/ — Claude Code Plugins | Skills, MCP Servers & Marketplace Directory
- https://github.com/netresearch/claude-code-marketplace — Curated Agent Skills collection, portable across Claude Code, Cursor, Copilot, Codex, Gemini CLI, and 30+ more agents. By Netresearch.
- https://code.claude.com/docs/en/discover-plugins — Discover and install prebuilt plugins through marketplaces (Claude Code Docs)
- https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers — Claude Skills Marketplace: The Essential Plugin Hub for Developers
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills — 425 plugins, 2,810 skills, 200 agents for Claude Code. Open-source marketplace at tonsofskills.com with the ccpi CLI package manager.
- https://github.com/alirezarezvani/claude-skills — 313+ Claude Code skills & agent skills & plugins for Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents
- https://github.com/daymade/claude-code-skills — Professional Claude Code skills marketplace featuring production-ready skills
- https://www.claudepluginhub.com/marketplaces/alirezarezvani-claude-code-skills — claude-code-skills Marketplace
- https://lobehub.com/skills — Agent Skills Marketplace | Claude, Codex & ChatGPT Skills · LobeHub

Key synthesis from search:
- Claude Code has built-in plugin system for browsing, installing, managing skills from terminal
- Plugins bundle one or more skills + optional hooks + MCP server configurations
- User scope: ~/.claude/skills/; Project scope: .claude/skills/ (shared via version control)
- Auto-update enabled by default for official Anthropic marketplaces
- Scale: 425 plugins, 2,810 skills, 200 agents at tonsofskills.com
- 170,000+ developers visit marketplaces every month

---

### Search 2: "MCP servers tools Claude agent extensions 2026"

Results:
- https://claudefa.st/blog/tools/mcp-extensions/best-addons — 50+ Best MCP Servers for Claude Code in 2026
- https://systemprompt.io/guides/claude-code-mcp-servers-extensions — Install and Configure MCP Servers in Claude Code (2026)
- https://platform.claude.com/docs/en/agent-sdk/mcp — Connect to external tools with MCP (Claude API Docs)
- https://www.morphllm.com/claude-code-extensions — Claude Code Extensions: MCP, Skills, Agents & Hooks Guide 2026
- https://nimbalyst.com/blog/best-claude-code-mcp-servers/ — Best Claude Code MCP Servers in 2026 (Ranked)
- https://platform.claude.com/docs/en/managed-agents/mcp-connector — MCP connector (Claude API Docs)
- https://code.claude.com/docs/en/agent-sdk/mcp — Connect to external tools with MCP (Claude Code Docs)
- https://nimbalyst.com/blog/claude-code-plugins-guide/ — Claude Code Plugins: A 2026 Guide
- https://fast.io/resources/claude-mcp-plugins/ — Best Claude MCP Plugins: Top 7 Tools for 2026

Key synthesis:
- MCP is open standard for connecting AI agents to external tools/data
- 50+ curated MCP servers available as of early 2026
- Recommended config: 3-6 MCP servers; day-one essentials = GitHub + 1-2 project-specific + Context7
- MCP Tool Search feature reduces context usage by up to 95% (lazy loading)
- SSE deprecated in favor of HTTP transport as of early 2026
- 5 servers with 58 tools = ~55,000 tokens upfront before conversation

---

### Search 3: "site:reddit.com Claude Code skills plugins MCP tools 2026"

Results:
- https://claudemarketplaces.com/ — 6,700+ skills, 2,500+ marketplaces, 840+ MCP servers
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers — Best Claude Code Plugins, Skills & MCP Servers (2026)
- https://code.claude.com/docs/en/plugins — Create plugins (Claude Code Docs)
- https://www.morphllm.com/claude-code-skills-mcp-plugins — Claude Code Skills vs MCP vs Plugins: Complete Guide 2026
- https://nimbalyst.com/blog/claude-code-plugins-guide/ (repeated)
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills (repeated)
- https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6 — 10 top Claude Code plugins to use in 2026 - DEV Community
- https://skillsplayground.com/guides/claude-code-plugins/ — Claude Code Plugins: The Complete Guide
- https://claudefa.st/blog/tools/mcp-extensions/best-addons (repeated)
- https://github.com/anthropics/claude-code/blob/main/plugins/README.md — Official Claude Code plugins README

Key synthesis:
- Skills = procedural knowledge (30-50 tokens each, loaded on-demand)
- MCP = external tool connections (can use 50k+ tokens)
- Plugins = shareable bundles of everything
- Hooks = automated actions at specific moments
- Slash Commands = prompt shortcuts
- feature-dev is most popular plugin with 89,000+ installs
- Context7 delivers version-specific library docs directly into session
- Meta MCP and CLI launched April 29, 2026 (Facebook/Instagram ads management)
- Snyk's ToxicSkills (February 2026): 13.4% of publicly available Skills had critical vulnerabilities

---

### Search 4: "reddit Claude Code skills MCP plugins discussion 2026"

Results:
- https://www.morphllm.com/claude-code-skills-mcp-plugins (repeated)
- https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026 — Claude Skills vs MCP Connectors vs Plugins

Key synthesis:
- Plugins shipped with Claude Cowork on January 30, 2026
- Bundle Skills, MCP Connectors, slash commands, and sub-agents
- Anthropic launched 11 official Plugins at release
- Plugin marketplace launched February 2026
- ToxicSkills research: 13.4% of publicly available Skills had critical vulnerabilities
- Most developers need 2-3 MCP servers (GitHub, Filesystem, one domain-specific) + few custom Skills

---

### Search 5: "Hacker News Claude Code MCP agent skills plugin ecosystem 2026"

Results:
- https://github.com/GetBindu/awesome-claude-code-and-skills — A collection of Claude Skills
- https://www.developersdigest.tech/blog/codex-vs-claude-code-april-2026 — Codex vs Claude Code in April 2026
- https://github.com/quemsah/awesome-claude-plugins — Automated collection of Claude Code plugin adoption metrics (17,826 repos as of May 20, 2026)
- https://github.com/rohitg00/awesome-claude-code-toolkit — 135 agents, 35 curated skills (+400,000 via SkillKit), 42 commands, 176+ plugins, 20 hooks, 15 rules, 7 templates, 14 MCP configs, 26 companion apps, 52 ecosystem entries
- https://mcpmarket.com/tools/skills/hacker-news-agent — Hacker News Agent Claude Code Skill
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills (repeated)
- https://pluto.security/blog/claude-extension-ecosystem-security-practitioner-guide/ — Security Practitioner's Map of the Claude Extension Ecosystem
- https://www.buildfastwithai.com/blogs/claude-skills-complete-guide-2026 — Claude Skills: The Complete 2026 Guide
- https://nimbalyst.com/blog/best-claude-code-mcp-servers/ (repeated)
- https://blog.cyberdesserts.com/ai-agent-security-risks/ — AI Agent Security Risks 2026: MCP, OpenClaw & Supply Chain

---

### Search 6: "agent skill marketplace plugin registry reusable AI tools 2026"

Results:
- https://chris-ayers.com/posts/agent-skills-plugins-marketplace/ — Agent Skills, Plugins and Marketplace: The Complete Guide
- https://claudemarketplaces.com/ (repeated)
- https://agentskillshub.dev/ — Agent Skills Hub - The Secure Marketplace for AI Agents (1,200+ verified skills)
- https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents — Top 5 Agent Skill Marketplaces
- https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026 — Every AI Skill Marketplace and Directory (2026)
- https://aitoolly.com/ai-news/article/2026-05-19-agent-skills-a-new-secure-and-verified-skill-registry-for-professional-ai-coding-agents-and-developm — Agent-Skills: Secure Registry for AI Coding Agents (May 19, 2026)
- https://skillsmp.com/ — Agent Skills Marketplace (800,000+ skills indexed from GitHub)
- https://jfrog.com/blog/agent-skills-new-ai-packages/ — Agent Skills are the New Packages of AI: It's Time to Manage Them Securely | JFrog
- https://developers.openai.com/codex/skills — Agent Skills – Codex | OpenAI Developers

Key synthesis:
- Agent skills ecosystem grew from 1 registry (Dec 2025) to 8 major marketplaces by Q2 2026
- Skills.sh: Vercel-backed, npm-style CLI, launched January 2026, cross-platform
- SkillsMP: 800,000+ skills scraped from public GitHub repositories
- ClawHub: 20,000+ skills with richer metadata
- Agent Skills specification published December 18, 2025 by Anthropic
- OpenAI adopted same format for Codex CLI and ChatGPT within 48 hours

---

### Search 7: "ToxicSkills Snyk security agent skills vulnerability 2026"

Results:
- https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/ — Snyk Finds Prompt Injection in 36%, 1467 Malicious Payloads in ToxicSkills Study
- https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026 — ToxicSkills and ClawHavoc — The Agent Skills Security Crisis (2026)
- https://www.aicerts.ai/news/snyk-audit-finds-ai-software-vulnerabilities-in-openclaw-skills/ — Snyk Audit Finds AI Software Vulnerabilities in OpenClaw Skills
- https://arxiv.org/html/2604.06550v1 — SkillSieve: A Hierarchical Triage Framework for Detecting Malicious AI Agent Skills
- https://skillshield.dev/blog/toxicskills-snyk-research-openclaw-users/ — What Snyk's ToxicSkills Research Means for OpenClaw Users
- https://spec-weave.com/blog/toxicskills-why-your-ai-agent-skills-need-verification/ — 36% of AI Agent Skills Have Security Flaws
- https://github.com/snyk-labs/toxicskills-goof — ToxicSkills - malicious agent skills in openclaw / clawhub / agent supply chain
- https://github.com/anton-abyzov/specweave — SpecWeave docs
- https://github.com/FlorianBruniaux/claude-code-ultimate-guide — Snyk ToxicSkills evaluation
- https://obot.ai/blog/mcp-security-agent-skills-supply-chain/ — The New Supply Chain Frontier: Securing MCP Security and Agent Skills

ToxicSkills Key Stats (Snyk, Feb 2026):
- 3,984 skills scanned from ClawHub and skills.sh as of February 5, 2026
- 13.4% (534 skills) = critical security issues
- 36.82% (1,467 skills) = any vulnerability
- 76 confirmed malicious payloads (human-reviewed)
- 8 malicious skills still live on ClawHub at time of publication
- 91% of confirmed malicious skills combined prompt injection with traditional malware
- 10.9% hardcoded secrets and API keys
- 17.7% expose indirect prompt injection via third-party content
- 2.9% dynamically fetch and execute remote instructions at runtime
- Daily skill submissions jumped from <50 (mid-Jan) to >500 (early Feb) — 10x in weeks
- First coordinated malware campaign: February 2026, 30+ malicious skills via ClawHub
- Three lines of markdown in SKILL.md enough to exfiltrate SSH keys
- Threat actors: zaycv, Aslaep123, pepe276, moonshine-100rze

---

### Search 8: "news.ycombinator.com Claude Code skills plugins MCP agent tools"

Hacker News Threads Found:
- https://news.ycombinator.com/item?id=46396930 — "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..."
- https://news.ycombinator.com/item?id=45619537 — "Claude Skills are awesome, maybe a bigger deal than MCP" — 738 points, 370 comments
- https://news.ycombinator.com/item?id=47855284 — "Show HN: Almanac MCP, turn Claude Code into a Deep Research agent"
- https://news.ycombinator.com/item?id=47321892 — "Claude Code Skills and Plugins as an Open Source Project"
- https://news.ycombinator.com/item?id=48130679 — "A Claude Code and Codex Skill for Deliberate Skill Development"
- https://news.ycombinator.com/item?id=47602986 — "Show HN: Real-time dashboard for Claude Code agent teams"
- https://news.ycombinator.com/item?id=46693426 — "Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills" — 4 points, 2 comments
- https://news.ycombinator.com/item?id=45607117 — "Claude Skills" — 816 points, 427 comments
- https://news.ycombinator.com/item?id=43410866 — "Hacking Your Own AI Coding Assistant with Claude Pro and MCP"

---

### Search 9: ""agent skills" "open standard" cross-agent portable skills specification 2026"

Results:
- https://www.agensi.io/learn/agent-skills-open-standard — What Is the Agent Skills Open Standard? (2026 Explainer)
- https://www.blog.brightcoding.dev/2026/05/18/why-top-ai-engineers-are-ditching-hardcoded-agents-for-agent-skills — Why Top AI Engineers Are Ditching Hardcoded Agents for Agent Skills (May 18, 2026)
- https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/ — Agent Skills Open Standard Explained: Adopted by Claude Code, Codex, Cursor & 32 Tools
- https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them — What Are Agent Skills and How To Use Them
- https://www.f5.com/company/blog/agent-skills-an-emerging-open-standard — Agent skills: An emerging open standard (F5)
- https://code.visualstudio.com/docs/copilot/customization/agent-skills — Use Agent Skills in VS Code
- https://www.mindstudio.ai/blog/agent-skills-open-standard-claude-openai-google — What Is Agent Skills as an Open Standard? How Claude, OpenAI, and Google Adopted the Same Format
- https://learn.microsoft.com/en-us/agent-framework/agents/skills — Agent Skills | Microsoft Learn
- https://github.com/agentskills/agentskills — Specification and documentation for Agent Skills
- https://agentskills.io/home — Agent Skills Overview

Key synthesis:
- Anthropic published Agent Skills spec December 18, 2025 at agentskills.io
- Apache 2.0 (code) + CC-BY-4.0 (docs)
- Within 48 hours: Microsoft → VS Code; OpenAI → ChatGPT + Codex CLI
- By March 2026: 32 tools adopted including Gemini CLI, JetBrains Junie, AWS Kiro, Block Goose
- Skills are portable: one build works across Claude, Codex, Cursor, Copilot, VS Code, 20+ others
- agentskills.io lists 40+ adopters in logo carousel (as of May 2026):
  JetBrains Junie, Gemini CLI, Autohand Code CLI, OpenCode, OpenHands, Mux, Cursor, Amp,
  Letta, Firebender, Goose, GitHub Copilot, VS Code, Claude Code, Claude, OpenAI Codex,
  Piebald, Factory, pi, Databricks Genie Code, Agentman, TRAE, Spring AI, Roo Code,
  Mistral Vibe, Command Code, Ona, VT Code, Qodo, Laravel Boost, Emdash,
  Snowflake Cortex Code, Kiro, Workshop, Google AI Edge Gallery, nanobot, fast-agent, bub, Tabnine, Vita, Superconductor
- Vercel's skills.sh lists 89,753 skills

---

### Search 10: "GitHub awesome-claude-code skills plugins MCP stars 2026"

Results:
- https://awesome-skills.com/ — Awesome Claude Skills - Curated Skills & Plugins
- https://github.com/ComposioHQ/awesome-claude-plugins — Composio curated plugin list
- https://github.com/rohitg00/awesome-claude-code-toolkit (repeated)
- https://claudefa.st/blog/tools/resources/awesome-claude-code — Awesome Claude Code: 11 Curated Lists Worth Bookmarking
- https://github.com/quemsah/awesome-claude-plugins (repeated - 17,826 repos May 20, 2026)
- https://github.com/hesreallyhim/awesome-claude-code — 36.8k stars (canonical hand-curated list)
- https://github.com/GetBindu/awesome-claude-code-and-skills (repeated)
- https://github.com/subinium/awesome-claude-code — Curated list of tools, skills, plugins, and MCP servers
- https://www.firecrawl.dev/blog/best-claude-code-skills
- https://github.com/BehiSecc/awesome-claude-skills

Key stats:
- hesreallyhim/awesome-claude-code: 36.8k stars (canonical, hand-curated)
- affaan-m/everything-claude-code: 141k stars (aggregator firehose)
- quemsah/awesome-claude-plugins: 17,826 total repositories indexed (as of May 20, 2026)
- 11 major curated lists dominating the 2026 ecosystem

---

### Search 11: JFrog agent skills security

Results:
- https://finance.yahoo.com/sectors/technology/articles/jfrog-report-warns-ai-governance-200500156.html
- https://jfrog.com/blog/agent-skills-new-ai-packages/ — Agent Skills are the New Packages of AI: It's Time to Manage Them Securely
- https://www.stocktitan.net/news/FROG/
- https://www.bastillepost.com/global/article/5871268-
- https://www.businesswire.com/news/home/20260520126325/en/New-JFrog-Report-Warns-AI-Governance-Fails-as-Software-Supply-Chain-Attacks-Hit-Record-Highs
- https://jfrog.com/blog/ai-agents-jfrog-skills-mcp-tools/

JFrog 2026 Report Key Stats (published May 20, 2026):
- 969 malicious AI agent skills identified (first time JFrog tracked this category)
- 495 malicious AI models on Hugging Face
- 56 malicious extensions on OpenVSX
- 451% surge in malicious npm packages YoY (177K new malicious packages across registries in last year)
- 97% of organizations claim AI governance; 53% still pull from risky public registries
- 48,000+ new CVEs disclosed in 2025 (20% YoY increase)
- Yonatan Arbel (JFrog DevAdvocacy Lead): "Skills have emerged as the go-to, low-friction way to shape an agent's day-to-day behavior"
- "Skills can run scripts and execute instructions that may cause damage, or at the very least, violate compliance standards"
- Infrastructure for skill distribution scattered across GitHub, Vercel, specialized platforms (ClawHub) — no centralized governance

---

### Search 12: Polymarket agent skills MCP

Results:
- https://mcp.directory/skills/polymarket-agent
- https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560
- https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi
- https://mcpmarket.com/server/polymarket-4
- https://mcp.directory/skills/polymarket-trader
- https://polymarket.com/predictions/ai
- https://mcpmarket.com/tools/skills/polymarket-development-suite
- https://github.com/Polymarket/agents
- https://python.plainenglish.io/i-used-agentic-coding-to-build-a-polymarket-intelligence-app-afc56be10477
- https://ericaai.tech.blog/2026/02/25/building-ai-agents-for-polymarket/

Polymarket/prediction market angle:
- As of May 21, 2026: 20 live AI prediction markets on Polymarket at polymarket.com/predictions/ai
- Multiple Polymarket MCP servers available (GitHub: caiovicentino/polymarket-mcp-server, Polymarket/agents)
- SimpleFunctions MCP: 29 tools, 9,706+ active contracts (Kalshi + Polymarket)
- Skills for prediction market trading available cross-platform
- No direct Polymarket prediction markets about "agent skills adoption" specifically found

---

## HACKER NEWS THREAD DETAILS

### HN: "Claude Skills" (id=45607117)
- Points: 816
- Comments: 427
- Notable quotes:
  - Simon Willison: "Claude Skills are awesome, maybe a bigger deal than MCP"
  - pseudosavant: "I highly doubt we'll be talking about MCP next year. It is a pretty bad spec"
  - rafaelmn: "Fundamentally you're getting hyped over a framework to append text to your prompt?"
- Key themes: Innovation vs hype; context management; progressive loading; LLMs struggle determining when to apply skills

### HN: "Claude Skills are awesome, maybe a bigger deal than MCP" (id=45619537)
- Points: 738
- Comments: 370
- Top commenter themes:
  - Skills solve context pollution problem (less material in token window than MCP/AGENTS.md)
  - Formalizes what developers were already doing organically (markdown + YAML)
  - Automated discovery: Claude scans skill folders on startup, triggers without manual intervention
  - Documentation quality paradox: "resemble normal developer documentation, but actually useful and task-oriented"
  - Principal-agent problem solved: immediate feedback loop incentivizes writing clear docs
  - GitHub MCP consumes "tens of thousands of tokens"; skills avoid this via progressive loading
  - Critics: "just rebranded instructions" or "marketing rather than innovation"

### HN: "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more..." (id=46396930)
- Author: mergesort
- Key comments:
  - MuffinFlavored: How many users employ none of these advanced features?
  - mergesort: "there's so much invisible configuration and best practices are changing so fast"
  - mergesort calls Skills "the killer feature" due to composability; uses for code review, copy editing, parallel task execution
  - bdangubic: 75% of teaching should focus on setup to set realistic expectations

### HN: "Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills" (id=46693426)
- Points: 4
- Comments: 2
- Original poster (lixiaofei): "I collected 60k+ open-source agent skills from GitHub, then curated 1,000+ Claude Code skills that are actually useful." Spent ~5 days on initial version.
- ricardobeat critique: "The top 30 results I see here are other skill collection libraries or skill generators. How is this a 'curated set of skills'?"

---

## YOUTUBE VIDEO

### "The Ultimate Claude Code Guide | MCP, Skills & More"
- URL: https://www.youtube.com/watch?v=uogzSxOw4LU
- Published: April 13, 2026
- Topics covered: comprehensive guide to Claude Code extensibility including MCP servers, skills, and more
- Exact view/like counts: not available (YouTube blocked fetch)
- Referenced by multiple aggregator sources as top resource

### Referenced in Class Central:
- https://www.classcentral.com/course/youtube-claude-code-context7-mcp-server-is-a-game-changer-for-ai-coding-461228
- "Claude Code + Context7 MCP Server Is a Game Changer for AI Coding"
- 13-minute tutorial

---

## GITHUB REPOSITORIES (Key Stats)

| Repo | Description | Stars/Forks |
|------|-------------|-------------|
| hesreallyhim/awesome-claude-code | Hand-curated list: skills, agents, hooks, plugins | 36.8k stars |
| affaan-m/everything-claude-code | Aggregator firehose | 141k stars |
| rohitg00/awesome-claude-code-toolkit | 135 agents, 35 curated skills (+400k via SkillKit), 176+ plugins | Unknown |
| jeremylongshore/claude-code-plugins-plus-skills | 425 plugins, 2,810 skills, 200 agents; tonsofskills.com | Unknown |
| quemsah/awesome-claude-plugins | Automated adoption metrics; 17,826 repos indexed May 20, 2026 | Unknown |
| netresearch/claude-code-marketplace | 40 curated skills, portable; by Netresearch DTT GmbH | 37 stars, 8 forks |
| agentskills/agentskills | Official Agent Skills specification | Unknown |
| snyk-labs/toxicskills-goof | ToxicSkills proof-of-concept malicious skills | Unknown |
| VoltAgent/awesome-agent-skills | 1000+ agent skills, cross-platform | Unknown |
| alirezarezvani/claude-skills | 313+ skills for 9+ coding agents | Unknown |

---

## MARKETPLACE DIRECTORY (from agensi.io research)

| Marketplace | Scale | Notable Feature |
|-------------|-------|-----------------|
| SkillsMP | 800,000+ skills | Scraped from GitHub, minimal curation |
| LobeHub | 169,000+ skills | Polished UI, broader ecosystem |
| claudemarketplaces.com | 6,700+ skills, 2,500+ marketplaces, 840+ MCPs | Daily updates, 170k+ monthly devs |
| ClawHub | 20,000+ skills | Richer metadata than most |
| skills.sh | ~2,000 skills | Vercel-backed, npm-style CLI |
| Agent Skills Hub | 1,200+ verified skills | Security analysis + usage docs |
| ClaudeSkills.info | 658 free skills | Community + official Anthropic skills |
| MCP Market | ~500 skills | MCP-server-focused |
| Anthropic Official | ~20 skills | Anthropic-verified, ships with Claude Code |
| tonsofskills.com | 2,747 skills, 428 plugins | ccpi CLI package manager |
| Agensi | 200+ skills | Manual curation, 8-pt security scan, creator payments |

---

## AGENTSKILLS.IO FULL ADOPTER LIST (from homepage, May 2026)

40+ tools supporting the SKILL.md open standard:
JetBrains Junie, Gemini CLI, Autohand Code CLI, OpenCode, OpenHands (cloud agents), Mux (Coder), Cursor, Amp (Sourcegraph), Letta, Firebender (Android-native), Goose (Block), GitHub Copilot, VS Code, Claude Code (Anthropic), Claude.ai, OpenAI Codex, Piebald, Factory, pi (badlogic), Databricks Genie Code, Agentman (healthcare), TRAE (ByteDance), Spring AI (VMware), Roo Code, Mistral Vibe, Command Code, Ona, VT Code, Qodo, Laravel Boost, Emdash, Snowflake Cortex Code, Kiro (AWS), Workshop, Google AI Edge Gallery, nanobot, fast-agent, bub, Tabnine, Vita, Superconductor

---

## SECURITY DEEP DIVE

### ToxicSkills (Snyk, February 5, 2026)
Full URL: https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/

Stats:
- 3,984 skills scanned
- 534 critical (13.4%)
- 1,467 any vulnerability (36.82%)
- 76 confirmed malicious payloads
- 8 still live at publication
- 91% of malicious skills combined prompt injection + traditional malware
- 10.9% hardcoded secrets
- 17.7% indirect prompt injection via external content
- 2.9% dynamically fetch/execute remote instructions
- "Agent Skills operate with the full permissions of the AI agent they extend" — shell access, filesystem R/W, credentials

Attack vectors documented:
1. External malware distribution (links to password-protected archives)
2. Obfuscated data exfiltration (Base64/Unicode encoded commands)
3. Security disablement (modifying system configs, deleting files, bypassing agent safety)

Known malicious actors: zaycv, Aslaep123, pepe276, moonshine-100rze

### JFrog Software Supply Chain Security Report (May 20, 2026)
- https://jfrog.com/blog/agent-skills-new-ai-packages/
- https://www.businesswire.com/news/home/20260520126325/en/
- 969 malicious AI agent skills (first time tracked)
- 451% surge in malicious npm packages YoY
- Proposed Agent Skills Registry: scanning, provenance attestation, centralized management, cross-platform compatibility

### VentureBeat (referenced):
- https://venturebeat.com/security/one-command-open-source-repo-ai-agent-backdoor-openclaw-supply-chain-scanner
- "One command turns any open-source repo into an AI agent backdoor"
- OpenClaw proved no supply-chain scanner has a detection category for agent skills

### SkillSieve (Academic):
- https://arxiv.org/html/2604.06550v1
- Hierarchical Triage Framework for Detecting Malicious AI Agent Skills

---

## TECHNICAL ARCHITECTURE

### Skills
- Format: directory with SKILL.md (YAML frontmatter + Markdown instructions)
- Optional: scripts/, references/, assets/ subdirectories
- Token cost: 30-50 tokens per skill (metadata only until activation)
- Loading: Progressive disclosure — discovery → activation → execution
- Install location: ~/.claude/skills/ (user) or .claude/skills/ (project)

### MCP (Model Context Protocol)
- Purpose: external tool connections (GitHub, DBs, APIs, etc.)
- Token cost: potentially 55,000+ tokens for 5 servers with 58 tools
- Tool Search feature: reduces cost by up to 95% (lazy loading)
- Transport: HTTP (SSE deprecated as of early 2026)

### Plugins
- Distribution unit bundling: skills + MCP servers + hooks + subagents + slash commands
- Install command: one-line, similar to package manager
- Scope: user (~/.claude/) or project (.claude/)
- Auto-update: enabled by default for official Anthropic marketplaces

### The CCPI Package Manager
- CLI: `pnpm add -g @intentsolutionsio/ccpi`
- Commands: search, install, manage versions
- Marketplace: tonsofskills.com

---

## REDDIT DATA NOTE
Reddit.com was not accessible via search tools (blocked domain). Secondary sources indicate:
- r/ClaudeCode: 4,200+ weekly contributors by early 2026
- Most-discussed topics: usage limits, MCP setups, plugin recommendations
- "Claude Is Dead" thread triggered by August 28, 2025 weekly cap changes
- r/ClaudeAI and r/CursorAI also active communities

---

## TIKTOK DATA NOTE
Found TikTok discover page: https://www.tiktok.com/discover/claude-code-skills
No specific video engagement metrics retrieved. Multiple TikTok integration skills/MCPs exist but no viral content identified.

---

## BLUESKY DATA NOTE
Community activity noted on Bluesky (referenced in social engagement metrics for top Claude Code tools) but no direct post data retrieved.
BlueSky Manager skill available: https://mcpmarket.com/tools/skills/bluesky-manager
