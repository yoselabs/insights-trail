# Agent Skills — Raw Research Output
**Date:** 2026-05-19
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## Web Search Batch 1: Claude Code Skills & Plugin Marketplace

### Query: "Claude Code skills plugins agent marketplace 2026"

**Links found:**
- https://github.com/ComposioHQ/awesome-claude-skills
- https://www.agensi.io/learn/claude-code-plugin-marketplace-guide
- https://claudemarketplaces.com/
- https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers
- https://github.com/netresearch/claude-code-marketplace
- https://github.com/alirezarezvani/claude-skills
- https://nimbalyst.com/blog/claude-code-plugins-guide/
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills
- https://code.claude.com/docs/en/discover-plugins
- https://alirezarezvani.github.io/claude-skills/guides/best-claude-code-plugins/

**Summary:**
- Claude Skills are reusable instruction packages (SKILL.md files with YAML frontmatter) that teach AI agents how to handle specific task classes.
- Anthropic introduced the format in October 2025 and released it as an open standard in December 2025.
- Supported by: Claude Code, Claude.ai, Claude API, OpenAI Codex, Cursor, Gemini CLI, Antigravity, Windsurf.
- A plugin is a package that bundles one or more skills along with optional extensions like hooks and MCP server configurations.
- Major collections: alirezarezvani/claude-skills (313+ skills), jeremylongshore/claude-code-plugins-plus-skills (425 plugins, 2,810 skills, 200 agents, marketplace at tonsofskills.com with ccpi CLI package manager).

---

## Web Search Batch 2: MCP Servers & Claude Code Extensions

### Query: "MCP servers tools Claude Code extensions 2026"

**Links found:**
- https://claudefa.st/blog/tools/mcp-extensions/best-addons
- https://systemprompt.io/guides/claude-code-mcp-servers-extensions
- https://nimbalyst.com/blog/best-claude-code-mcp-servers/
- https://code.claude.com/docs/en/mcp
- https://code.visualstudio.com/docs/copilot/customization/mcp-servers
- https://www.anthropic.com/engineering/desktop-extensions
- https://nimbalyst.com/blog/claude-code-mcp-setup/
- https://www.buildfastwithai.com/blogs/claude-mcp-setup-guide-2026
- https://fast.io/resources/claude-mcp-plugins/

**Summary:**
- MCP (Model Context Protocol) launched November 2024, 2,300+ public MCP servers by May 2026.
- Adopted by Claude, Cursor, Windsurf, VS Code, and 200+ tools.
- Popular MCP servers: GitHub, Linear, Slack, Postgres, Sentry, Playwright.
- Desktop Extensions (.mcpb format) enable one-click installation, bundling server + all dependencies.
- SSE transport deprecated in early 2026; new implementations should use HTTP transport.
- Typical 5-server/58-tool setup consumes ~55,000 tokens; Anthropic's Tool Search reduces this 85%.

---

## Web Search Batch 3: Agent Skill Marketplace Ecosystem

### Query: "agent skill marketplace plugin ecosystem AI tools 2026"

**Links found:**
- https://chris-ayers.com/posts/agent-skills-plugins-marketplace/
- https://skillsmp.com/
- https://lobehub.com/skills
- https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
- https://www.agensi.io/learn/how-ai-agent-skill-marketplaces-work
- https://www.agensi.io/learn/skills-marketplace-ai-agents
- https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026
- https://www.agensi.io/learn/ai-agent-skills-explained-complete-guide
- https://claudemarketplaces.com/
- https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026

**Summary:**
- In December 2025, Anthropic released Agent Skills specification as open standard; OpenAI adopted same format.
- SKILL.md is now adopted by: OpenAI Codex CLI, Google Gemini CLI, Cursor, OpenClaw, and 20+ agents.
- Major marketplaces: SkillsMP (425,000+ skills), LobeHub (169,739 skills), skills.sh (Vercel, 87,000+ skills), Agensi (200+ curated with security scan).
- In January 2026: a few hundred skills. By April 2026: multiple marketplaces claim hundreds of thousands.
- Monthly search volume for related terms grew 19x in 2 years: 21,000 → 400,000+.

---

## Web Search Batch 4: SKILL.md Open Standard

### Query: "SKILL.md open standard agent skill distribution discovery 2026"

**Links found:**
- https://www.termdock.com/en/blog/agent-skills-guide
- https://www.agensi.io/learn/what-is-skill-md
- https://www.agensi.io/learn/agent-skills-open-standard
- https://www.mintlify.com/blog/skill-md
- https://www.firecrawl.dev/blog/agent-skills
- https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996
- https://skillsmp.com/
- https://inference.sh/blog/skills/agent-skills-overview
- https://arxiv.org/pdf/2603.16572

**Summary:**
- SKILL.md: open file format, markdown with YAML frontmatter.
- Required fields: name, description.
- Progressive disclosure: metadata only at startup (30-50 tokens), full instructions loaded on demand.
- A February 2026 study analyzed 40,285 publicly listed skills; ecosystem grew 18.5× in 20 days.
- Distributions: ClawHub (18,412 skills as of March 9), Skills.sh (86,800), SkillsDirectory (36,109).
- arxiv.org/pdf/2603.16572: "Malicious Or Not: Adding Repository Context to Agent Skill Classification."

---

## Web Search Batch 5: Anthropic Agent Skills Announcement

### Query: "Anthropic agent skills open standard December 2025 announcement"

**Links found:**
- https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude
- https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/
- https://www.financialcontent.com/article/tokenring-2025-12-24-anthropic-launches-agent-skills-open-standard-the-new-universal-language-for-ai-interoperability
- https://markets.financialcontent.com/wral/article/tokenring-2025-12-25-anthropic-unveils-agent-skills-open-standard-a-blueprint-for-modular-ai-autonomy
- https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills
- https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard
- https://markets.financialcontent.com/wral/article/tokenring-2025-12-31-anthropic-shatters-ai-walled-gardens-with-launch-of-agent-skills-open-standard
- https://medium.com/@evoailabs/agent-skills-are-open-standard-can-be-used-with-any-llm-agent-feb0cba4e0ff

**Summary from Anthropic engineering post (fetched):**
- Agent Skills announced: October 16, 2025 (initial), open standard December 18, 2025 at agentskills.io.
- Supported platforms at launch: Claude.ai, Claude Code, Claude Agent SDK, Claude Developer Platform.
- Technical: SKILL.md with YAML frontmatter, progressive disclosure architecture.
- Quote: "Skills extend Claude's capabilities by packaging your expertise into composable resources for Claude, transforming general-purpose agents into specialized agents that fit your needs."
- URLs: https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview, https://github.com/anthropics/claude-cookbooks/tree/main/skills, https://github.com/anthropics/skills, https://agentskills.io/
- Partners adopting at launch: Canva, Notion, Figma, Atlassian.
- Donated standard to Agentic AI Foundation (AAIF), a Linux Foundation-backed alliance.
- Enterprise: organization-wide skill management for Team and Enterprise plans.

---

## Web Search Batch 6: MCP Security Vulnerabilities

### Query: "MCP server security trust agent tools Claude 2026 vulnerabilities"

**Links found:**
- https://www.mintmcp.com/blog/claude-code-cve
- https://cybersecuritynews.com/cve-mcp-server-and-claude/
- https://www.darkreading.com/application-security/trustfall-exposes-claude-code-execution-risk
- https://www.securityweek.com/claude-code-oauth-tokens-can-be-stolen-through-stealthy-mcp-hijacking/
- https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/
- https://research.checkpoint.com/2026/rce-and-api-token-exfiltration-through-claude-code-project-files-cve-2025-59536/
- https://blog.cyberdesserts.com/ai-agent-security-risks/
- https://medium.com/@katy-thomas/your-engineers-gave-claude-root-access-do-you-know-what-it-did-next-846d34eca5c1
- https://obot.ai/blog/mcp-security-masterclass-claude-leak-crisis/
- https://www.strac.io/blog/m365-mcp-server

**Key vulnerabilities:**
- CVE-2025-59536 (CVSS 8.7): RCE via pre-trust hook execution and MCP consent bypass.
- CVE-2026-21852 (CVSS 5.3): API key exfiltration through ANTHROPIC_BASE_URL manipulation.
- OX Security: systemic vulnerability enabling Arbitrary Command Execution (RCE) in any MCP implementation.
- Mitiga: silent redirect of Claude Code MCP traffic, interception of OAuth tokens, persistent SaaS access.
- TrustFall convention: agents execute malicious code before trust dialogs appear.
- Trend Micro: 492 MCP servers exposed to the internet with zero authentication.
- Anthropic's Git MCP server: 3 CVEs in January 2026 (path traversal, argument injection).

---

## Web Search Batch 7: Hacker News Discussions

### Query: "Claude Code agent skills Hacker News discussion Show HN 2026"

**Links found:**
- https://dev.to/max_quimby/claude-code-just-hit-1-on-hacker-news-heres-everything-you-need-to-know-j74
- https://mcpmarket.com/tools/skills/hacker-news-agent
- https://news.ycombinator.com/item?id=46693426
- https://news.ycombinator.com/item?id=47602986
- https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026
- https://news.ycombinator.com/item?id=47463371
- https://news.ycombinator.com/item?id=47855284
- https://news.ycombinator.com/item?id=48141114
- https://news.ycombinator.com/item?id=46917293

**HN Thread Details (fetched):**

1. **Show HN: Agent Skills – 1k curated Claude Code skills from 60k+ GitHub skills**
   - URL: https://news.ycombinator.com/item?id=46693426
   - Score: 4 points | 2 comments | ~3 months ago | by lixiaofei
   - Creator: filtered 60k+ open-source GitHub skills to ~1k practical skills, daily-updated directory.
   - Quote (creator): "Claude Code skills aren't that different from agents or other automation tools—the big difference is that they lower the barrier so more people (including beginners) can use them."
   - Top comment (ricardobeat): "The top 30 results I see here are other skill collection libraries or skill generators" — questioning curation quality.

2. **Show HN: Real-time dashboard for Claude Code agent teams**
   - URL: https://news.ycombinator.com/item?id=47602986
   - Score: 77 points | 28 comments | ~47 days ago | by simple10
   - Project: https://github.com/simple10/agents-observe
   - Key findings from comments: blocking hooks kill throughput ("anything blocking in the agent's critical path kills throughput. Even a few hundred milliseconds per hook call compounds fast."); "sanitised optimism" problem — agents silently report success while suppressing errors ("Claude kept reporting success when it just silenced the error."); some teams spend thousands/day on Claude tokens.

3. **Show HN: Yet another Claude Code agent setup, but several novel patterns**
   - URL: https://news.ycombinator.com/item?id=47463371
   - Score: 1 point | 1 comment | ~59 days ago | by AndyNemmity
   - Features: intelligent router command, high-context skills reducing token usage, Architecture Documentation Records (ADRs).
   - Top comment (angtly): "Every agent framework solves orchestration well, but none of them answer: what happens when Agent A needs to hire Agent B for a capability it doesn't have?" — proposing an "economic layer" with per-call billing for specialist agents.

4. **Show HN: Almanac MCP, turn Claude Code into a Deep Research agent**
   - URL: https://news.ycombinator.com/item?id=47855284
   - Score: 14 points | ~27 days ago | by rohans0509
   - Install: `npx openalmanac setup`, free tool.
   - Capabilities: general web search, Reddit-specific search, webpage scraping. Community encyclopedia component.

5. **Ask HN: Best option for hosted agent in 2026?**
   - URL: https://news.ycombinator.com/item?id=46917293

---

## Web Search Batch 8: Skill Marketplace Monetization & Vercel

### Query: "agent skills marketplace monetization creator economy skills.sh vercel 2026"

**Links found:**
- https://github.com/vercel-labs/skills
- https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
- https://vercel.com/docs/agent-resources/skills
- https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/
- https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context
- https://www.agensi.io/learn/agent-skills-marketplace-sell-your-skills
- https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/
- https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026
- https://community.vercel.com/t/skly-an-ai-skills-marketplace-is-built-with-next-js-and-supabase/33827

**Summary:**
- Vercel launched skills.sh on January 20, 2026 as an open agent skills ecosystem / directory and leaderboard.
- npm took a decade to reach 350,000 packages; AI agent skills ecosystem did it in ~2 months.
- Official skill publishers before Q1 2026: Vercel, Prisma, Supabase, Stripe, Remotion, Coinbase, Microsoft.
- Creator monetization: niche skills sold via Agensi with 80/20 creator payments, 20-50% income boosts reported.
- Only one major marketplace (Agensi) offers paid skill sales in April 2026; others free-only.
- Prediction: at least 2 current free platforms will add paid tiers with 70-80% creator revenue splits.
- Install: `npx skills add [author]/[skill-name]`

---

## Web Search Batch 9: MCP Desktop Extensions / .mcpb Format

### Query: "MCP Desktop Extensions one-click install Claude 2026 packaging format"

**Links found:**
- https://www.anthropic.com/engineering/desktop-extensions
- https://github.com/primefaces/primeng/issues/19506
- https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop
- https://www.desktopextensions.com/
- https://github.com/modelcontextprotocol/mcpb
- https://devblogs.microsoft.com/azure-sdk/azure-mcp-server-mcpb-support/
- https://mcpfind.org/blog/installing-mcp-desktop-extensions-mcpb
- https://www.buildfastwithai.com/blogs/claude-mcp-setup-guide-2026
- https://github.com/vinod-eng/ClaudeDesktopExtension
- https://dev.to/anh_nguyen_589e1928a98305/from-api-key-to-one-click-install-building-a-claude-desktop-extension-for-agentshare-1e31

**Summary:**
- Desktop Extensions (.mcpb) = zip archive containing MCP server + all dependencies + manifest.json.
- .dxt and .mcpb are the same format; Anthropic renamed .dxt → .mcpb in late 2025 to match MCP Bundle branding; both still accepted.
- Open-sourced specification and toolchain; supported by Claude for macOS and Windows.
- Installation: click "Install Extension…" → select .mcpb file → follow prompts.
- Microsoft Azure MCP server also available as .mcpb.

---

## Web Search Batch 10: Malicious Skills & Security Crisis

### Query: "malicious skills" "skill poisoning" "prompt injection" MCP agent security 2026

**Links found:**
- https://gentic.news/article/mcp-security-crisis-43-of-servers
- https://obot.ai/blog/mcp-security-agent-skills-supply-chain/
- https://blog.cyberdesserts.com/openclaw-malicious-skills-security/
- https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/
- https://owasp.org/www-project-agentic-skills-top-10/
- https://blog.cyberdesserts.com/ai-agent-security-risks/
- https://www.practical-devsecops.com/mcp-security-guide/
- https://ismalicious.com/posts/mcp-security-risks-tool-poisoning-ai-agents
- https://www.practical-devsecops.com/mcp-security-vulnerabilities/

**Key findings:**
- Snyk ToxicSkills audit (Feb 2026): 1,467 malicious payloads across 3,984 scanned skills. 36% flaw rate. 76 confirmed malicious with active payloads. 534 (13.4%) contain critical-level security issues.
- Antiy CERT: 1,184 malicious skills across ClawHub (OpenClaw registry).
- ClawHub: first AI registry systematically poisoned at scale; 5 of top 7 most-downloaded skills at peak confirmed as malware.
- 43% of MCP servers vulnerable per gentic.news analysis.
- Document-Driven Implicit Payload Execution (DDIPE): embeds malicious logic in code examples within skill docs; bypass rates 11.6%–33.5%.
- OWASP Agentic Skills Top 10: released December 2025, peer-reviewed by 100+ security researchers.
- ASI01 — Agent Goal Hijacking — ranked #1 risk.
- gentic.news: MCP Security Crisis — 43% of servers vulnerable, 341 malicious skills found.

---

## Web Search Batch 11: YouTube Videos

### Query: "YouTube Claude Code MCP skills tutorial 2026"

**Links found:**
- https://www.youtube.com/watch?v=uogzSxOw4LU — "The Ultimate Claude Code Guide | MCP, Skills & More" (April 13, 2026)
- https://www.youtube.com/watch?v=EZcYjH3jAo8 — "How I Actually Use Claude Every Day in 2026" (covers Claude Skills, Connectors, MCP Services)
- https://composio.dev/toolkits/youtube/framework/claude-code
- https://mcpmarket.com/tools/skills/watch-youtube
- https://www.youtube.com/playlist?list=PL4cUxeGkcC9g4YJeBqChhFJwKQ9TRiivY — "Claude Code Tutorial" playlist
- https://www.udemy.com/course/agent-skills-claude-code-cursor-and-mcp-in-practice/ — Udemy course
- Between October 2025 and March 2026, agent skills ecosystem grew to 350,000+ published skills; Anthropic's official repo reached nearly 100,000 GitHub stars.

---

## Web Search Batch 12: TikTok Coverage

### Query: "TikTok Claude Code AI agent skills MCP tutorial creators 2026"

**Links found:**
- https://www.tiktok.com/@rileybrown.ai/video/7514157096229686559 — rileybrown.ai: "CLAUDE MCP TUTORIAL — Claude is an AI Agent!" (covers Notion MCP, Claude system prompt, tool selection)
- https://composio.dev/toolkits/tiktok/framework/claude-agents-sdk
- https://www.hyperfx.ai/blog/best-marketing-skills-mcps-and-clis-for-ai-agents-2026
- https://mcpmarket.com/tools/skills/tiktok-content-strategy
- https://composio.dev/toolkits/tiktok/framework/claude-code
- https://stormy.ai/blog/building-tiktok-content-factory-claude-code
- https://stormy.ai/blog/autonomous-instagram-content-engine-claude-code-playbook
- https://www.tiktok.com/@unefille.ia/video/7488008313704172822 — unefille.ia: French-language tutorial on MCP and AI agents
- https://claudskills.com/skills/tiktok-automation/

---

## Web Search Batch 13: X/Twitter Coverage

### Query: "X twitter Claude Code skills MCP agent plugins trending developers 2026"

**Links found:**
- https://mcpmarket.com/tools/skills/x-twitter-automation — X Automation skill: 33 commands, OAuth 1.0a, full-archive search
- https://github.com/hesreallyhim/awesome-claude-code/issues/1285 — X Twitter Scraper resource issue
- https://claudelog.com/claude-code-mcps/twitter-mcp/
- https://www.thetoolnerd.com/p/10-best-ai-claude-skills-to-supercharge
- https://github.com/VoltAgent/awesome-agent-skills — 1000+ curated agent skills
- https://www.scriptbyai.com/claude-code-resource-list/ — Ultimate Claude Code Resource List 2026
- https://composio.dev/toolkits/twitter/framework/claude-code
- https://claudefa.st/blog/tools/mcp-extensions/social-media-mcps

---

## Web Search Batch 14: agentskills.io Open Standard Cross-Platform

### Query: "agentskills.io open standard portable agent skills cross-platform"

**Links found:**
- https://www.bishoylabib.com/posts/claude-skills-comprehensive-guide
- https://playbooks.com/skills/openclaw/skills/agentskills-io
- https://inference.sh/blog/skills/agent-skills-overview
- https://medium.com/@nayakpplaban/agent-skills-standard-for-smarter-ai-bde76ea61c13
- https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them
- https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/
- https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/
- https://code.visualstudio.com/docs/copilot/customization/agent-skills

**Summary:**
- Open standard published December 18, 2025 at agentskills.io.
- Partners adopting at launch: Microsoft, OpenAI, Atlassian, Figma, Cursor, GitHub.
- Partner-built skills from: Canva, Stripe, Notion, Zapier.
- VS Code added native agent skills support.
- Donated to Agentic AI Foundation (AAIF), Linux Foundation-backed.

---

## Web Search Batch 15: ccpi / tonsofskills.com CLI Package Manager

### Query: "ccpi CLI package manager agent skills install tonsofskills.com"

**Links found:**
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills (425 plugins, 2,810 skills, 200 agents)
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/wiki/Installing-Plugin-Packs
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/tree/main/plugins/saas-packs/flyio-pack
- https://github.com/jeremylongshore/claude-code-plugins-plus-skills/blob/main/README.md

**Summary:**
- ccpi install: `pnpm add -g @intentsolutionsio/ccpi`
- Commands: `ccpi install devops-automation-pack`, `ccpi search devops`, `ccpi list --installed`, `ccpi update`
- 42 SaaS skill packs covering 1,086 skills for specific platforms.
- Agent Skills activate automatically when Claude detects relevant context (unlike /slash commands which require explicit invocation).

---

## Web Search Batch 16: Marketplace Security Comparison

### Query: "Claude Code plugin marketplace skills registry comparison SkillsMP LobeHub skills.sh agensi 2026"

**Links found:**
- https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026
- https://lobehub.com/skills
- https://www.openaitoolshub.org/en/blog/claude-skills-marketplace-comparison
- https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained
- https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026
- https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents
- https://claudemarketplaces.com/
- https://skillsmp.com/
- https://docs.litellm.ai/docs/tutorials/claude_code_plugin_marketplace
- https://www.agensi.io/learn/toxicskills-clawhavoc-agent-skills-security-crisis-2026

**KDNuggets Top 5 Marketplaces (fetched):**

1. **SkillsMP** (https://skillsmp.com/) — Largest discovery platform. 425,000+ skills aggregated from GitHub (≥2 stars). AI-powered search. One-click install compatible with Claude Code, ChatGPT, Codex CLI.

2. **LobeHub Skills** (https://lobehub.com/skills) — 169,739 skills indexed. Quality checks + community ratings. Sample: `npx -y @lobehub/market-cli skills install davila7-claude-code-templates-humanizer --agent claude-code`

3. **agentskill.sh** (http://agentskill.sh) — 110,000+ skills across 20+ AI tools. Security scoring + audit details. Claude Code plugin compatible.

4. **skills.sh** (http://skills.sh) — Vercel-backed. 87,000 unique skills. Public leaderboard, activity tracking. `npx skills add https://github.com/vercel-labs/agent-skills --skill vercel-react-best-practices`

5. **ClawHub** (https://clawhub.ai/) — OpenClaw's official registry. 20,000+ registered skills. Rich metadata, security scanning, license/version details.

**Security comparison:**
- SkillsMP, skills.sh, LobeHub: NO automated security scans.
- Agensi: 8-point security scan covering prompt injection, data exfiltration, dangerous shell commands, secret detection, obfuscation patterns, external fetches, credential access, privilege escalation.

---

## Web Search Batch 17: Polymarket MCP Integration

### Query: "Polymarket prediction market AI agents MCP Claude Code 2026"

**Links found:**
- https://sparkco.ai/blog/prediction-market-agent-claude-code-mcp-kalshi
- https://conare.ai/marketplace/mcp/graph-polymarket
- https://conare.ai/marketplace/mcp/polymarket-mcp
- https://polymarket.com/predictions/ai
- https://mcpmarket.com/tools/skills/polymarket-development-suite
- https://mcpmarket.com/tools/skills/polymarket-trading-data-integration
- https://medium.com/@weare1010/claude-ai-trading-bots-are-making-hundreds-of-thousands-on-polymarket-2840efb9f2cd
- https://wealthytent.com/ai-trading-bot-for-polymarket
- https://skywork.ai/skypage/en/ai-engineer-guide-polymarket-server/1978282237843394560

**Summary:**
- SimpleFunctions MCP: 29 tools, real-time Kalshi + Polymarket data, 9,706+ active contracts.
- Graph Polymarket MCP: 20 tools (market data, trader P&L, positions, orderbook).
- Social media flooded with AI trading bot claims (March 2026). On-chain data: 92.4% of Polymarket wallets lose money; average arbitrage window compressed from 12.3s (2024) to 2.7s (2026).

---

## Web Search Batch 18: Awesome Claude Code / GitHub Collections

### Query: "awesome-claude-code GitHub skills community curated list 2026"

**Links found:**
- https://github.com/ComposioHQ/awesome-claude-skills
- https://github.com/BehiSecc/awesome-claude-skills
- https://github.com/travisvn/awesome-claude-skills
- https://github.com/GetBindu/awesome-claude-code-and-skills
- https://github.com/hesreallyhim/awesome-claude-code (36.8k stars — canonical hand-curated)
- https://claudefa.st/blog/tools/resources/awesome-claude-code
- https://github.com/Chat2AnyLLM/awesome-claude-skills (9,864 skills, updated 2026-05-06)
- https://claudeskills.info/best/
- https://chat2anyllm.github.io/awesome-claude-skills/
- https://github.com/Samarth0211/awesome-claude-skills-2026 (2,300+ skills, clskills.in)

**Key:**
- hesreallyhim/awesome-claude-code: 36.8k stars, canonical, hand-curated, covers skills/agents/hooks/status lines/orchestrators.
- ComposioHQ/awesome-claude-skills: 1000+ production-ready skills, multi-agent (Claude Code, Codex, Cursor, Gemini CLI).
- Chat2AnyLLM/awesome-claude-skills: 9,864 total skills as of 2026-05-06.

---

## Web Search Batch 19: OWASP Agentic Applications

### Query: "OWASP agentic skills top 10 security risks 2026"

**Links found:**
- https://owasp.org/www-project-agentic-skills-top-10/
- https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/
- https://www.startupdefense.io/blog/owasp-top-10-agentic-ai-security-risks-2026
- https://github.com/kenhuangus/agentic-skills-top-10
- https://www.trydeepteam.com/docs/frameworks-owasp-top-10-for-agentic-applications
- https://www.microsoft.com/en-us/security/blog/2026/03/30/addressing-the-owasp-top-10-risks-in-agentic-ai-with-microsoft-copilot-studio/
- https://www.aikido.dev/blog/owasp-top-10-agentic-applications
- https://nhimg.org/complete-guide-to-the-2026-owasp-top-10-risks-for-agentic-applications
- https://auth0.com/blog/owasp-top-10-agentic-applications-lessons/
- https://www.practical-devsecops.com/owasp-top-10-agentic-applications/

**Summary:**
- OWASP Top 10 for Agentic Applications 2026 released December 2025, peer-reviewed by 100+ researchers.
- Catalogs 10 critical risks for systems that act autonomously (API calls, code execution, file operations).
- ASI01: Agent Goal Hijacking (top risk — attacker manipulates agent objectives via poisoned inputs).
- Principle of Least Agency: agents should have minimum autonomy, tool access, and credential scope required.
- Microsoft published March 30, 2026 blog on addressing OWASP Top 10 risks in Copilot Studio.
- Active Q1 2026 threat: ClawHub registry systematically poisoned; 5 of top 7 most-downloaded skills confirmed as malware at peak.

---

## Fetched Key URLs

### Anthropic Engineering: equipping-agents-for-the-real-world-with-agent-skills
- Skills first published: October 16, 2025
- Open standard at agentskills.io: December 18, 2025
- Quote: "Skills extend Claude's capabilities by packaging your expertise into composable resources for Claude, transforming general-purpose agents into specialized agents that fit your needs."
- Skills docs: https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview
- Skills cookbook: https://github.com/anthropics/claude-cookbooks/tree/main/skills
- Example skill repo: https://github.com/anthropics/skills
- Portal: https://agentskills.io/

### firecrawl.dev/blog/agent-skills (fetched)
- SKILL.md structure: folder with SKILL.md (required), scripts/ (optional), references/ (optional), assets/ (optional).
- YAML frontmatter: required name + description; individual skill body capped at 5,000 tokens; full dir limited to 500 lines.
- Progressive disclosure: 30-50 tokens per skill at startup; 50 skills installed ≈ 1,500-2,500 tokens at session start.
- Ecosystem: February 2026 study — 40,285 publicly listed skills, 18.5× growth in 20 days.
- Median skill body: 1,414 tokens.
- Web search/retrieval skills most installed: avg 1,268 installs/skill.
- 46% of marketplace skills share names with ≥1 other skill.
- 55% of all published skills focus on software engineering workflows.
- Nearly 40% of published skills access sensitive context or perform writes.
- 9% fall in critical risk category.
- Cross-platform: 26+ platforms support SKILL.md without modification.
- Install: `npx skills add [author]/[skill-name]`

---

## Additional Notable Sources

- https://pub.towardsai.net/claude-code-extensions-explained-skills-mcp-hooks-subagents-agent-teams-plugins-9294907e84ff
- https://devops-daily.com/posts/claude-code-agents-commands-skills-plugins-explained
- https://www.morphllm.com/claude-code-skills-mcp-plugins
- https://www.mindstudio.ai/blog/claude-code-skills-vs-plugins-difference
- https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026
- https://www.linkedin.com/pulse/claude-code-survival-guide-2026-skills-agents-mcp-servers-rob-foster-lq9we
- https://dev.to/composiodev/10-top-claude-code-plugins-to-use-in-2026-4gn6
- https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers
- https://github.com/VoltAgent/awesome-agent-skills (1000+ curated, multi-platform)
- https://github.com/netresearch/claude-code-marketplace (curated, agentskills.io portable, 30+ agents)
- https://mcpmarket.com/ (MCP Market, submission-based, ~500 skills)
- https://claudmarketplaces.com/ (directory)
- https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview (official docs)
- https://www.anthropic.com/engineering/desktop-extensions (Desktop Extensions .mcpb)
- https://github.com/modelcontextprotocol/mcpb (open-source .mcpb spec)
- https://devblogs.microsoft.com/azure-sdk/azure-mcp-server-mcpb-support/ (Azure MCP as .mcpb)
- https://vercel.com/changelog/introducing-skills-the-open-agent-skills-ecosystem
- https://vercel.com/docs/agent-resources/skills
- https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context
- https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude
- https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/
- https://www.unite.ai/anthropic-opens-agent-skills-standard-continuing-its-pattern-of-building-industry-infrastructure/
- https://medium.com/@evoailabs/agent-skills-are-open-standard-can-be-used-with-any-llm-agent-feb0cba4e0ff
- https://strapi.io/blog/what-are-agent-skills-and-how-to-use-them
- https://inference.sh/blog/skills/agent-skills-overview
- https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026
- https://www.solobusinesshub.com/trend-watch/ai-agent-skills-boom-2026/
