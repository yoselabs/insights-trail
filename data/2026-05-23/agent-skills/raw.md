# Agent Skills & Plugin Ecosystems — Raw Research Data
**Date:** 2026-05-23
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## HACKER NEWS

### Thread 1
- **Title:** Claude Skills
- **Author:** meetpateltech
- **Points:** 816
- **Comments:** 427
- **URL:** https://news.ycombinator.com/item?id=45607117
- **Discussion URL:** https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- **Top Comment Themes:**
  - Simon Willison characterizes skills as potentially more significant than MCP: "a paradigm for dynamically assembling context with information crossing organizational boundaries"
  - Some view skills as "a design pattern / prompt engineering trick" not requiring formal specification
  - Docker analogy emerged: conceptual simplicity doesn't diminish transformative potential
  - Skills can be toggled on/off, addressing capacity management issues in larger projects
  - Skills differ from MCP by being local, file-based, and LLM-triggered rather than user-triggered protocol implementations
  - LLMs struggle with skill discovery based solely on brief descriptions
  - External API authentication requires workarounds in cloud-based Claude environments

### Thread 2
- **Title:** Claude Skills are awesome, maybe a bigger deal than MCP
- **Author:** weinzierl
- **Points:** 738
- **Comments:** 370
- **URL:** https://news.ycombinator.com/item?id=45619537
- **Discussion URL:** https://simonwillison.net/2025/Oct/16/claude-skills/
- **Top Comment Themes:**
  - tptacek: "The actual breakthrough is 'tool calls' themselves, not MCP specifically. MCP is merely one implementation among possibilities."
  - michael1999: Context documents for AI resemble effective developer documentation but created far more readily. Three theories: immediate feedback loops, tool assistance, ego alignment ("developers feel motivated improving their 'digital goblin'")
  - causal: skills are "instructions with RAG," questioning whether rebranding merits announcement significance
  - Critics: "Rebranding existing patterns"; "Accessibility gap: average users cannot realistically configure these systems"
  - Value proposition: YAML metadata for automatic skill discovery + standardized distribution format + reduced context pollution vs. MCP's upfront loading

### Thread 3
- **Title:** Agent Skills – Open Trusted Catalog of AI Agent Skills: Claude, OpenAI, Vercel, GH
- **URL:** https://news.ycombinator.com/item?id=46692865
- **Status:** HTTP 429 (rate-limited)
- **Note:** Multiple major providers publish skills in separate repos with different formats; project aggregates from all major providers into one JSON catalog, auto-updates daily, delivers via CDN

### Thread 4
- **Title:** Show HN: Agent37 – Monetize your Claude skills with shareable links
- **Author:** vishnukool
- **Points:** 5
- **Comments:** 3
- **URL:** https://news.ycombinator.com/item?id=46422134
- **Discussion URL:** https://agent37.com
- **Key Points:**
  - "There are 1,000+ MCP skills on GitHub with zero way for creators to charge for them"
  - Platform streamlines skill monetization; users try skills via shareable links without needing Claude accounts or local config
  - Built-in Stripe payments; creators retain 80% of revenue
  - One non-technical creator earned $1,600 on the platform

### Thread 5
- **Title:** Claude Skills vs. MCP: Complementary Philosophies for AI Customization
- **URL:** https://news.ycombinator.com/item?id=45766686
- **Status:** HTTP 429 (rate-limited)

### Thread 6
- **Title:** Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks)
- **URL:** https://news.ycombinator.com/item?id=46983879
- **Status:** HTTP 429 (rate-limited)
- **Note:** The Agent Skills spec requires kebab-case names; Claude Code doesn't validate this and silently ignores incorrectly named skills

### Thread 7
- **Title:** Skillz: Use Claude Skills in Codex, Copilot, or Any Other Agent via MCP
- **URL:** https://news.ycombinator.com/item?id=45649295
- **Status:** HTTP 429 (rate-limited)

### Thread 8
- **Title:** Show HN: Almanac MCP, turn Claude Code into a Deep Research agent
- **URL:** https://news.ycombinator.com/item?id=47855284
- **Status:** Not fetched

### Thread 9
- **Title:** Show HN: Federal Election Commission Claude Code Plugin and Agent Skill and MCP
- **URL:** https://news.ycombinator.com/item?id=46869575
- **Status:** Not fetched

---

## GITHUB REPOSITORIES

### Repo 1
- **Name:** jeremylongshore/claude-code-plugins-plus-skills
- **URL:** https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- **Stars:** 2,200 | **Forks:** 303
- **License:** MIT
- **Stats:** 425 plugins across 19 categories, 2,810 agent skills, 200 specialized agents, 16 contributors
- **CLI:** `pnpm add -g @intentsolutionsio/ccpi`
- **Web Marketplace:** https://tonsofskills.com
- **Published npm packages:** 418 packages, 53,237 downloads in last 30 months
- **Top categories:** AI & Machine Learning (36), DevOps & Infrastructure (36), SaaS Skill Packs (106), Testing (27), Security (26), Crypto & Web3 (26)

### Repo 2
- **Name:** ComposioHQ/awesome-claude-plugins
- **URL:** https://github.com/ComposioHQ/awesome-claude-plugins
- **Stars:** 1,700 | **Forks:** 393
- **Description:** Curated list of production-ready extensions: MCP servers, Skills, custom Agents, Hooks
- **Categories:** Integrations, Frontend & Design, Git & Version Control, Code Quality & Testing, Backend & Architecture, DevOps & Performance, Documentation & Security, Developer Productivity, Companion & Personality

### Repo 3
- **Name:** alirezarezvani/claude-skills
- **URL:** https://github.com/alirezarezvani/claude-skills
- **Stars:** 5,200+
- **Description:** "Most comprehensive open-source Claude Code skills & agent plugins library"; 313+ skills for Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents

### Repo 4
- **Name:** ComposioHQ/awesome-claude-skills
- **URL:** https://github.com/ComposioHQ/awesome-claude-skills
- **Description:** 1,000+ production-ready practical Claude Skills and Plugins; cross-platform (Claude.ai, Claude Code, Codex, Cursor, Gemini CLI)

### Repo 5
- **Name:** agentskills/agentskills
- **URL:** https://github.com/agentskills/agentskills
- **Description:** Specification and documentation for the Agent Skills open standard

### Repo 6
- **Name:** anthropics/skills
- **URL:** https://github.com/anthropics/skills
- **Description:** Official Anthropic Agent Skills repository; includes marketplace.json at `.claude-plugin/marketplace.json`

### Repo 7
- **Name:** quemsah/awesome-claude-plugins
- **URL:** https://github.com/quemsah/awesome-claude-plugins
- **Description:** Automated collection of Claude Code plugin adoption metrics using n8n workflows; tracks 418 published packages in claude-code-plugins namespace

### Repo 8
- **Name:** rohunvora/x-research-skill
- **URL:** https://github.com/rohunvora/x-research-skill
- **Description:** X/Twitter research skill for Claude Code and OpenClaw; agentic search, thread following, deep-dives, sourced briefings

### GitHub Topics
- https://github.com/topics/claude-code-skills
- https://github.com/topics/claude-skills
- https://github.com/topics/claude-skills-hub

---

## WEB SOURCES

### Official Anthropic Sources
1. **Engineering Blog:** "Equipping agents for the real world with Agent Skills"
   - URL: https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
   - Authors: Barry Zhang, Keith Lazuka, Mahesh Murag
   - Date: October 16, 2025
   - Key: Skills are directories with SKILL.md + YAML frontmatter (name + description). Progressive disclosure: Level 1 = names/descriptions in system prompt; Level 2 = full SKILL.md when relevant; Level 3+ = additional bundled files contextually.

2. **Product Announcement:** "Introducing Agent Skills"
   - URL: https://www.anthropic.com/news/skills (redirects to https://claude.com/blog/skills)
   - Date: October 16, 2025
   - Key: "Skills are folders that include instructions, scripts, and resources that Claude can load when needed." "Skills stack together." "Only loads what's needed, when it's needed."
   - Available to: Claude Pro/Max/Team/Enterprise users, Messages API + /v1/skills endpoint, Claude Code via plugin marketplace, Claude Agent SDK

3. **API Documentation:**
   - URL: https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview
   - URL: https://console.anthropic.com/docs/en/agents-and-tools/agent-skills/quickstart

4. **MCP Donation:**
   - URL: https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation
   - Anthropic donated MCP to Agentic AI Foundation (AAIF), directed fund under Linux Foundation; co-founded by Anthropic, Block, OpenAI; supported by Google, Microsoft, AWS, Cloudflare, Bloomberg

5. **Claude Code Plugin Docs:**
   - URL: https://code.claude.com/docs/en/plugins
   - URL: https://code.claude.com/docs/en/mcp

### Analysis & News
6. **Simon Willison Blog:**
   - URL: https://simonwillison.net/2025/Oct/16/claude-skills/
   - Date: October 16, 2025
   - Key: "While MCP requires an elaborate protocol specification covering hosts, clients, servers, and multiple transports, skills embrace simplicity: Markdown with a tiny bit of YAML metadata and some optional scripts." Predicts "Cambrian explosion" in skills adoption. Token efficiency: brief metadata summaries consume dozens of tokens per skill; MCP's GitHub official implementation consumes tens of thousands.

7. **The New Stack:**
   - URL: https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/
   - Content blocked by paywall/newsletter wall

8. **VentureBeat:**
   - URL: https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard
   - HTTP 429

9. **Medium / The Context Layer (Jannis):**
   - URL: https://medium.com/the-context-layer/anthropic-is-doing-with-agent-skills-what-it-did-with-mcp-7068a15e72da
   - Key: "Anthropic is doing with Agent Skills what it did with MCP" — using community adoption to establish de facto standards

10. **AI Business:**
    - URL: https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude

11. **KDNuggets — Top 5 Agent Skill Marketplaces:**
    - URL: https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
    - Reviewed: SkillsMP, LobeHub, agentskill.sh, skills.sh, ClawHub

12. **Inference.sh Blog:**
    - URL: https://inference.sh/blog/skills/agent-skills-overview
    - Content: Agent Skills open standard overview

13. **DEV Community — gh skill:**
    - URL: https://dev.to/om_shree_0709/gh-skill-githubs-new-cli-command-turns-agent-skills-into-installable-packages-2p82
    - Author: Om Shree | Date: April 16, 2025
    - Key: GitHub released `gh skill` CLI; `gh skill install github/awesome-copilot documentation-writer`; provenance metadata in SKILL.md frontmatter; content validation on updates; publisher-controlled immutable releases

14. **Vercel Knowledge Base:**
    - URL: https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context

15. **Paperclipped (Interoperability Guide):**
    - URL: https://www.paperclipped.de/en/blog/agent-skills-open-standard-interoperability/
    - Key: By March 2026, 32 tools from competing companies including Google Gemini CLI, JetBrains Junie, AWS Kiro, Block's Goose all read same SKILL.md files. Published: December 18, 2025 (48 hours later: VS Code + OpenAI adopted)

16. **Agent Skills Open Standard (agentskills.io):**
    - URL: https://agentskills.io/home

17. **Skills.sh (Vercel-backed):**
    - URL: http://skills.sh
    - Launch: January 20, 2026; top skill: 20,000 installs within 6 hours; 87,000-89,753 unique skills; `npx skills add` CLI; public leaderboard

18. **Agensi Learn — Marketplaces Guide:**
    - URL: https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
    - Full comparison of 8 marketplaces; security audit found 140,963 issues across 22,511 skills (avg 6.3/skill); prompt injection in 36% of skills tested; market consolidation predicted by Q4 2026

19. **Help Net Security:**
    - URL: https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/
    - Title: "One in four MCP servers opens AI agent security to code execution risk"
    - Date: May 5, 2026

20. **MorphLLM Extensions Guide:**
    - URL: https://www.morphllm.com/claude-code-extensions
    - Stats: 9,000+ community plugins, 35% faster edits with Morph FastApply, 40% context reduction via parallel search

21. **MorphLLM Reddit Summary:**
    - URL: https://www.morphllm.com/claude-code-reddit
    - Key: r/ClaudeCode had 4,200+ weekly contributors by early 2026 (vs. 1,200 on r/Codex); Claude Code 67% win rate in blind comparisons; SWE-bench 77.2%

22. **Morph — Skills vs MCP vs Plugins:**
    - URL: https://www.morphllm.com/claude-code-skills-mcp-plugins

23. **Nimbalyst Plugin Guide:**
    - URL: https://nimbalyst.com/blog/claude-code-plugins-guide/

24. **Skills Playground:**
    - URL: https://skillsplayground.com/guides/claude-code-plugins/

25. **Clarista MCP Guide:**
    - URL: https://www.clarista.io/blog/claude-code-mcp-plugins-guide

26. **Subramanya.ai — Enterprise AI Puzzle:**
    - URL: https://subramanya.ai/2025/12/18/agent-skills-the-missing-piece-of-the-enterprise-ai-puzzle/
    - Date: December 18, 2025

27. **PulseMCP — OpenAI Adopts Agent Skills:**
    - URL: https://www.pulsemcp.com/posts/openai-agent-skills-anthropic-donates-mcp-gpt-5-2-image-1-5

28. **CIO Dive — Open Standards:**
    - URL: https://www.ciodive.com/news/big-tech-develop-open-standards-agentic-ai/807608/

29. **Pento — Year of MCP:**
    - URL: https://www.pento.ai/blog/a-year-of-mcp-2025-review
    - Key: 10,000+ active public MCP servers; adopted by ChatGPT, Cursor, Gemini, Microsoft Copilot, VS Code, and others

30. **Firecrawl — Best Claude Code Skills:**
    - URL: https://www.firecrawl.dev/blog/best-claude-code-skills

31. **Camille Roux — Top 13 Skills/Plugins:**
    - URL: https://www.camilleroux.com/top-skills-plugins-claude-code-2026-v3/
    - Note: Cross-posted to X, Bluesky, Mastodon, LinkedIn; most engagement for any Claude Code tools article

32. **AdwaitX — Market Analysis:**
    - URL: https://www.adwaitx.com/anthropic-agent-skills-open-standard-ai-market/
    - Title: "Anthropic Unveils Agent Skills Standard: $52B Market Shift"

33. **Toloka — Best MCP Servers:**
    - URL: https://toloka.ai/blog/best-mcp-servers-for-agents/

34. **Firecrawl — Best MCP Servers:**
    - URL: https://www.firecrawl.dev/blog/best-mcp-servers-for-developers

35. **MCP Bundles — Best MCP Servers:**
    - URL: https://www.mcpbundles.com/blog/best-mcp-servers

36. **K2View — Awesome MCP Servers:**
    - URL: https://www.k2view.com/blog/awesome-mcp-servers

37. **Analytics Vidhya — Top 10 MCP Servers:**
    - URL: https://www.analyticsvidhya.com/blog/2026/02/top-mcp-servers/

38. **ByteBridge — MCP Gateways:**
    - URL: https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a

39. **Integrate.io — MCP Security:**
    - URL: https://www.integrate.io/blog/best-mcp-gateways-and-ai-agent-security-tools/

40. **Help Net Security — MCP Vulnerabilities:**
    - URL: https://www.helpnetsecurity.com/2026/05/05/ai-agent-security-skills-blind-spots/

41. **Adversa AI — MCP Security Resources:**
    - URL: https://adversa.ai/blog/top-mcp-security-resources-april-2026/

42. **AWS ML Blog — Securing AI Agents:**
    - URL: https://aws.amazon.com/blogs/machine-learning/securing-ai-agents-how-aws-and-cisco-ai-defense-scale-mcp-and-a2a-deployments/

43. **Aembit MCP Security Guide:**
    - URL: https://aembit.io/blog/the-ultimate-guide-to-mcp-security-vulnerabilities/

44. **TurboDocx — Best Plugins/Skills:**
    - URL: https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers

45. **Agensi — Plugin Marketplace Guide:**
    - URL: https://www.agensi.io/learn/claude-code-plugin-marketplace-guide

46. **Agensi — How to Install Skills:**
    - URL: https://www.agensi.io/learn/how-to-install-skills-claude-code

47. **Agensi — Plugins vs Skills Explained:**
    - URL: https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained

48. **Script by AI — Resource List:**
    - URL: https://www.scriptbyai.com/claude-code-resource-list/

49. **Nimbleway — Top 10 Agent Skills:**
    - URL: https://www.nimbleway.com/blog/anthropic-claude-agent-skills

50. **Claude World — Official Skills Guide:**
    - URL: https://claude-world.com/articles/anthropic-official-skills-complete-guide/

51. **SkillHub:**
    - URL: https://www.skillhub.club/

52. **OpenAI Codex Skills Docs:**
    - URL: https://developers.openai.com/codex/skills

53. **Gemini CLI Skills Docs:**
    - URL: https://geminicli.com/docs/cli/skills/

54. **Microsoft Learn — MCP Tools:**
    - URL: https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools

55. **MCP Market Directory:**
    - URL: https://mcpmarket.com/

56. **AI Agents List — MCP Servers:**
    - URL: https://aiagentslist.com/mcp-servers (593+ MCP servers)

57. **MCP Servers Directory (mcpservers.org):**
    - URL: https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp

58. **Vercel — Agent Skills KB:**
    - URL: https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context

---

## X/TWITTER

### Post 1
- **Handle:** @Praiseakinlami
- **URL:** https://x.com/Praiseakinlami/status/2018359352965411097
- **Text:** "Hope you all know about Claude skills. I use it for my viral tweets and I get vitality every time."
- **Engagement:** Not retrieved

### Notable X Post Pattern
- @simonw's analysis of Claude Skills was widely shared; described as "maybe a bigger deal than MCP"
- X/Twitter posts about Claude Code skills focus heavily on workflow tutorials and monetization potential
- X users debated skills-as-rebranding vs. genuine paradigm shift

---

## TIKTOK

### Video 1
- **Creator:** @rileybrown.ai
- **URL:** https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559
- **Caption:** "CLAUDE MCP TUTORIAL — Claude is an AI Agent! Both 4 Sonnet, and 4 Opus. And they're INSANELY smart. But you need to make sure you're giving it CONTEXT. You can give it access to many tools using MCP..."
- **Engagement:** Viral (exact counts not retrieved)
- **Topics:** MCP setup, Notion integration, YouTube thumbnail generation

### TikTok General
- "3 Claude Code skills every designer needs right now" (referenced but not linked directly)
- Claude Code/MCP tutorials have become a significant TikTok genre in 2026

---

## YOUTUBE

### Video 1
- **Title:** Full Claude Skills Tutorial for Beginners in 2026! (Become a PRO)
- **URL:** https://www.youtube.com/watch?v=YkpEX_jlb04
- **Published:** March 14, 2026

### Video 2
- **Title:** FULL Claude Code Tutorial for Beginners in 2026! (Step-By-Step)
- **URL:** https://www.youtube.com/watch?v=qYqIhX9hTQk
- **Published:** March 29, 2026

### Video 3
- **Title:** 7 Claude Code skills I use every single day (Advanced Tutorial)
- **URL:** https://www.youtube.com/watch?v=UpgjdQJShWg
- **Published:** ~May 9, 2026 (2 weeks ago)

### Video 4
- **Title:** Full Claude Code Tutorial for Non-Technical Beginners in 2026 (step-by-step)
- **URL:** https://www.youtube.com/watch?v=bqJzIWAEn40
- **Published:** ~May 2, 2026 (3 weeks ago)

### YouTube General
- Popular Claude Code videos range from 853K-view viral demos to 4K-view deep dives
- 25-video ranking guide published at https://medium.com/@rentierdigital/i-watched-25-claude-code-youtube-videos-so-you-dont-have-to-the-definitive-ranking-550aa6863840

---

## POLYMARKET / PREDICTION MARKETS

- No specific prediction markets found about agent skills or Claude Code ecosystem outcomes
- Multiple MCP servers enable AI agents to query Polymarket data (not direct Polymarket markets about the topic)
  - Polymarket MCP (berlinbra): https://mcpservers.org/servers/fernandezpablo85/polymarket-mcp
  - Graph Polymarket: https://conare.ai/marketplace/mcp/graph-polymarket (20 tools)
  - SimpleFunctions: 29 tools covering 9,706+ contracts on Polymarket + Kalshi
  - Polymarket Toolkit: https://www.blog.brightcoding.dev/2026/05/22/polymarket-toolkit-the-secret-weapon-top-ai-agents-use-for-prediction-market-alpha

---

## KEY STATISTICS COMPILATION

### Ecosystem Scale
- 22,775 MCP servers listed on Glama (as of May 2026, many forks/abandoned)
- 10,000+ active public MCP servers (Pento / Anthropic data)
- 32 tools from competing companies adopted Agent Skills standard by March 2026
- 9,000+ community Claude Code plugins in active use
- r/ClaudeCode: 4,200+ weekly contributors (early 2026)

### Marketplace Sizes
- SkillsMP: 1,463,795 skills (aggregated from GitHub)
- LobeHub: 169,739 skills
- skills.sh: 87,000-89,753 skills
- agentskill.sh: 110,000+ skills
- ClawHub: 20,000+ skills
- Anthropic Official: ~20 skills (curated)
- feature-dev plugin: 89,000+ installs

### Security Findings
- BlueRock Security: 36.7% of ~7,000 MCP servers SSRF-vulnerable; 41% require no authentication; 53% of authenticated servers use static API keys; only 8.5% use OAuth
- Agensi audit: 140,963 issues across 22,511 skills (avg 6.3/skill); prompt injection in 36%
- 43% of public MCP servers have at least one vulnerability
- CVE-2025-59536 (CVSS 8.7): configuration injection flaws in Claude Code (disclosed Feb 25, 2026)
- ClawHub reportedly systematically poisoned at scale

### Token Efficiency
- Skills: 30-50 tokens each (loaded on-demand)
- MCP servers: can use 50,000+ tokens
- GitHub official MCP implementation: tens of thousands of context tokens alone
- Morph FastApply: 35% faster edits; 40% context reduction via WarpGrep

---

## KEY QUOTES

1. Simon Willison: "While MCP requires an elaborate protocol specification covering hosts, clients, servers, and multiple transports, skills embrace simplicity: Markdown with a tiny bit of YAML metadata and some optional scripts."

2. Anthropic (claude.com/blog/skills): "Skills are folders that include instructions, scripts, and resources that Claude can load when needed." "Skills stack together." "Only loads what's needed, when it's needed."

3. Barry Zhang et al. (engineering blog): "As agent capabilities expand, 'more composable, scalable, and portable ways' become necessary to equip agents with specialized expertise."

4. HN commenter michael1999: Context documents for AI "resemble effective developer documentation but are created far more readily" — developers feel motivated improving their "digital goblin" rather than abstract colleagues

5. HN commenter tptacek: "The actual breakthrough is 'tool calls' themselves, not MCP specifically. MCP is merely one implementation among possibilities."

6. HN commenter causal: Skills are "instructions with RAG," questioning whether rebranding merits announcement significance

7. vishnukool (Agent37): "There are 1,000+ MCP skills on GitHub with zero way for creators to charge for them"

8. Simon Willison: Predicts "Cambrian explosion" in skills adoption, potentially dwarfing MCP's initial rush

9. MorphLLM: "Skills are on-demand" while "CLAUDE.md is always-loaded context." Choose Skills for specific workflows and CLAUDE.md for foundational knowledge.

10. Simon Willison: "MCP provides the 'plumbing' for tool access, while agent skills provide the 'brain' or procedural memory for how to use those tools effectively"

11. Om Shree (DEV Community): GitHub's gh skill addresses "a critical gap in the emerging agent skills ecosystem by providing version control, integrity checking, and centralized distribution"
