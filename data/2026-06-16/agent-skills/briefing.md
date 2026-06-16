# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-06-16
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, Web

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 8 threads | — | r/ClaudeAI (7), r/ChatGPTCoding (1) |
| X/Twitter | 25 posts | 1,592 likes, 357 reposts | High share/repost ratio on resource lists |
| Hacker News | 20 stories | 1,308 points, 897 comments | "Claude Code as a Daily Driver" top post at 451pts |
| Bluesky | 12 posts | 302 likes, 7 reposts | Developer commentary + skeptical takes |
| Web | 10 pages | — | via engine grounding + 10 WebSearch supplements |

---

## Synthesized Findings

### 1. The Plugin Marketplace Architecture Is Now Canonical

The Claude Code plugin ecosystem has consolidated around a clear three-layer model: **Skills** (a `SKILL.md` file + optional scripts that teach Claude one repeatable workflow), **Plugins** (installable bundles that package one or more skills along with hooks, MCP server configs, and agents), and **MCP Servers** (protocol-based external tool connectors that expose databases, APIs, and services). This architecture is now widely documented and discussed across HN, Reddit, and web guides.

The [r/ClaudeAI](https://reddit.com/r/ClaudeAI) community thread "Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs" ([HN, 451pts, 254 comments](https://arps18.github.io/posts/claude-code-mastery/)) became the canonical reference post of the month. [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368) put the distinction cleanly on X: "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit."

[DEV Community](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) documented the concrete effect: "The first plugin I installed did something I had been doing by hand for nine months. It was a skill called `frontend-design`. I added it, asked Claude to build a landing page, and watched it ignore every default React-and-Tailwind cliché it usually reaches for."

### 2. A Micro-Marketplace Explosion Is Underway

The discovery problem is now spawning its own ecosystem. Multiple competing registries have launched in the last 30 days:

- [skills.2389.ai](https://skills.2389.ai/) - 2389 Research's open-source plugin marketplace with `npx skills add` CLI
- [claudemarketplaces.com](https://claudemarketplaces.com/) - Directory indexing 300k+ monthly developer visits
- [claude-plugins.dev](https://claude-plugins.dev/skills) - Community skill discovery site
- [codeguilds.dev](https://codeguilds.dev) - Community registry for skills, agents, MCP servers (Show HN, [HN](https://news.ycombinator.com/item?id=48357494))
- [tonsofskills.com](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) - 2,810 skills with `ccpi` CLI package manager
- **SkillsMP** - 800,000+ skills scraped from public GitHub repos
- **Skills.sh** - Vercel-backed npm-style package manager for skills, launched January 2026

A Redditor in [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) articulated the problem driving all of this: "Discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer: Is this maintained? What does it install? Does it use hooks or MCP servers? Are people actually using it?"

[@polsia](https://x.com/polsia/status/2064450681856200753) built an open directory covering Claude Code, Cursor, and Windsurf with 2,000+ skills, MCP servers, and rules ranked by stars: "The space is getting crowded. Time to stand out."

### 3. Role-Specific and Domain Skill Packs Are Emerging

Beyond general-purpose skill collections, domain-specific packs are being built and announced. [@oliviscusAI](https://x.com/oliviscusAI/status/2066838637375861063) highlighted a PM Skills marketplace with 68 skills and 42 chained workflows across 9 plugins covering discovery, PRD writing, strategy, GTM planning, and growth metrics - installable in one command: `claude plugin marketplace add phuryn/pm-skills`.

[@izag82161](https://x.com/izag82161/status/2066652208888955121) announced Anthropic's own open-source role-based specialist marketplace for sales, marketing, PM, finance, legal, data, and support teams.

[@LandingAI](https://x.com/LandingAI/status/2066831209112752255) released Agentic Document Extraction (ADE) skills for AI coding agents: "Install them in Claude Code, Cursor, or any AI coding agent that supports the Agent Skills convention." The cross-agent compatibility is significant - the Agent Skills format now has support from 30+ platforms including Claude Code, Cursor, GitHub Copilot, VS Code, Codex CLI, Roo Code, and Goose per [explainx.ai](https://explainx.ai/blog/what-are-agent-skills-complete-guide).

### 4. MCP Servers: Practical Integration Is the Dominant Conversation

MCP is where the most high-engagement Reddit discussion is happening. An [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tkec4e/which_mcp_servers_are_actually_changing_your/) thread asked "Which MCP servers are actually changing your Claude workflow?" and surfaced real-world setups: filesystem server for docs, GitHub server for PR workflows, database MCP for production queries.

One of the most creative examples came from [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1tvefqd/i_wired_claude_code_into_a_database_of_every/): "I wired Claude Code into a database of every Polymarket wallet and trades via MCP. 1.3 Billion trades and 2.7M wallets - I just ask it anything in plain English and it writes + runs the query itself. Only ~1 in 5 wallets are net positive."

Another practitioner in [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1thabze/i_gave_claude_access_to_my_m365_account_using/) built an M365 integration: "I gave Claude access to my M365 account using Power Automate + a small MCP server - read my inbox, send drafts, check calendar, save notes to OneDrive, write Excel rows, fill Word templates."

On the MCP architecture front, [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550) cited David Soria Parra (Anthropic, co-creator of MCP): "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together."

[Clarista](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) summarized the framing: "Think of MCP as USB for AI: one protocol, many tools, many clients."

Show HN posts filled out the long tail: [a GitOps-style registry for AI agent Workflows, Skills and MCP servers](https://github.com/Friz-zy/ai-capability-registry), [86 MCP tools driving an AI video generator](https://github.com/openclaw-easy/ViralMint), [MCP for the ChatGPT Ads API](https://github.com/HYPD-AI/openai-ads-mcp), and "[Stop returning raw JSON from MCP servers, build rich inline UIs](https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3)" ([HN, 11pts](https://news.ycombinator.com/item?id=48449489)).

### 5. Dynamic Workflows and Agent Teams Are the Next Frontier

Anthropic shipped [Dynamic Workflows in Claude Code](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) ([HN, 200pts, 135 comments](https://news.ycombinator.com/item?id=48311705)), enabling parallel subagents. [The New Stack on Bluesky](https://bsky.app/profile/thenewstack.io/post/3mo7yf7mjvo2v) tested them: "Anthropic's dynamic workflows in Claude Code let Claude run parallel subagents. We tested them against a single agent to see if they beat the hype."

The orchestration analogy struck a chord. [@ssp.sh](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w) drew the parallel plainly: "Data engineering spent fifteen years building orchestrators - Airflow, Dagster, Prefect, Kestra. We are now doing the same thing for AI agents. Agor from Max the original creator of Airflow. Agent Teams from Anthropic, native to Claude Code. Omnigent from Databricks."

[@hikikomorphism.bsky.social](https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d) argued for heterogeneous agent teams: "Yes mythos/fable as planner, but there's no need to burn Opus tokens on medium sized tasks when you can just have mythos manage a team of DeepSeek/Gemini agents."

A cautionary tale: [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u5d02w/til_claude_code_spawned_339_subagents_from_a/) documented Claude Code spawning 339 sub-agents from a single research prompt, burning the user's entire MAX 5-hour quota in minutes.

### 6. Token Overhead and the "Too Many Plugins" Backlash

A significant counter-narrative is building around plugin bloat. An [r/ClaudeAI](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) thread got notable traction: "I checked my session transcripts: 187 items loaded [at startup], but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache." The poster built a CLI to fix it.

[@regent0x_](https://x.com/regent0x_/status/2057419591618302029) posted "Stop Installing Plugins on Claude Code - The Ultimate Guide" (315 likes, 43 reposts, 14 replies) - the highest-engagement skeptical post in the dataset. A follow-up from the same account became the most-shared funny take of the month: "his dad built a $2M company on a 1986 macintosh plus - no drivers, no plugins, no setup - just worked. 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free." ([@regent0x_](https://x.com/regent0x_/status/2058079320405332047), 49 likes)

[@martindotnet.bsky.social](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i) added: "I find it hilarious that engineers will spend days, weeks even, curating their token dashboard for their claude code session, when they'll spend practically zero time adding telemetry to their apps to make it better. Claude Code: here's 72 graphs and dashboards. Production: install agent, go home."

### 7. Security Risks in Skill Distribution Are Getting Serious Academic Attention

Two academic papers surfaced on arxiv about security in agent skill ecosystems: "Malicious Agent Skills in the Wild: A Large-Scale Security Empirical Study" ([2602.06547](https://arxiv.org/pdf/2602.06547)) and "Formal Analysis and Supply Chain Security for Agentic AI Skills" ([2603.00195](https://arxiv.org/pdf/2603.00195)).

The supply chain concern is real and current. [@fpl9000.bsky.social](https://bsky.app/profile/fpl9000.bsky.social/post/3moayr5qg5c2v) raised the issue directly: "I'm considering installing the Pi agent (pi.dev), which is written in TypeScript and installs with npm. Given recent news about npm-based supply chain attacks, I asked Claude about the risk of malware." [@alex_prompter](https://x.com/alex_prompter/status/2059548217285713933) noted Perplexity open-sourced "Bumblebee," a security scanner covering infected editor extensions, VS Code, Cursor, Windsurf, and MCP server configs.

### 8. The Broader Vibe Coding Ecosystem Around Claude Code

[@ssp.sh](https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q) captured the macro shift: "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category. Claude Code, OpenCode, Amp, Crush, Pi, aichat, Deer-flow. Each one is an agent harness that runs mostly autonomously in the terminal, against your repo, with permission rails you set."

[@moomanibe.bsky.social](https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226) put adoption plainly: "people keep asking me this question and my answer is that it is functionally irrelevant because no one is doing this and absolutely everyone is using Claude Code and Midjourney. Like there's zero nuance in the actual practical expression here."

---

## Cross-Source Patterns

**Pattern 1: Discovery is the unsolved problem** - The explosion of skills and plugins has created a fragmentation problem that is now spawning its own ecosystem of directories, registries, and package managers. This appears on Reddit (the directory-builder thread), X (@polsia's open directory), HN (CodeGuilds Show HN), and Web (claudemarketplaces.com, SkillsMP, Skills.sh). Every platform has discussion about how to find good skills.

- Reddit: r/ClaudeAI directory thread
- X: [@polsia](https://x.com/polsia/status/2064450681856200753) building the open directory
- HN: [CodeGuilds community registry](https://codeguilds.dev)
- Web: [agensi.io marketplace list](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), claudemarketplaces.com

> "Discovery is scattered across GitHub, Discord threads, blog posts, and individual repos." - r/ClaudeAI

**Pattern 2: Token overhead backlash** - A consistent counter-narrative argues that plugin accumulation creates token waste and complexity. Appears on Reddit (8k token waste thread), X (regent0x_ posts with 315+49 likes), and Bluesky (martindotnet.bsky.social).

- X: [@regent0x_](https://x.com/regent0x_/status/2057419591618302029) "Stop Installing Plugins"
- Reddit: [r/ClaudeAI token waste thread](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/)
- Bluesky: [@martindotnet.bsky.social](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i)

> "23 plugins, 8 skills, 5 MCP servers... no drivers, no plugins, no setup - just worked." - [@regent0x_](https://x.com/regent0x_/status/2058079320405332047)

**Pattern 3: Cross-agent skill portability is becoming real** - The Agent Skills format (SKILL.md convention) is now supported beyond Claude Code alone. Appears on X (LandingAI releasing cross-agent skills), Web (explainx.ai documenting 30+ platform support), and HN (skills-for-humanity Show HN aimed at multiple agents).

- X: [@LandingAI](https://x.com/LandingAI/status/2066831209112752255) releasing cross-agent ADE skills
- Web: [explainx.ai 30+ platform guide](https://explainx.ai/blog/what-are-agent-skills-complete-guide)
- HN: [skills-for-humanity](https://github.com/human-avatar/skills-for-humanity) (28pts)

---

## Per-Platform Tables

**Reddit:**
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/ClaudeAI | Claude Code as a Daily Driver | 451 | 254 | (canonical HN crosspost) | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| r/ClaudeAI | Which MCP servers are actually changing your Claude workflow? | — | — | "It really does feel like a whole new product" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tkec4e/which_mcp_servers_are_actually_changing_your/) |
| r/ClaudeAI | I built a searchable directory for Claude Code plugins | — | — | "Discovery is scattered across GitHub, Discord..." | [link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/) |
| r/ClaudeAI | Using Claude Code? You're wasting ~8k tokens per session on unused skills | — | — | "187 items loaded, but I only used 4 actively" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/) |
| r/ClaudeAI | TIL Claude Code spawned 339 sub-agents from a single research prompt | — | — | "Burned my entire MAX 5-hour quota in minutes" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u5d02w/til_claude_code_spawned_339_subagents_from_a/) |
| r/ClaudeAI | I wired Claude Code into every Polymarket trade via MCP | — | — | "Just ask it anything in plain English" | [link](https://www.reddit.com/r/ClaudeAI/comments/1tvefqd/i_wired_claude_code_into_a_database_of_every/) |
| r/ClaudeAI | I gave Claude access to my M365 account using MCP | — | — | "Feels genuinely useful instead of cool demo" | [link](https://www.reddit.com/r/ClaudeAI/comments/1thabze/i_gave_claude_access_to_my_m365_account_using/) |
| r/ClaudeAI | I got tired of Claude Code building the same generic site (MCP + critique loop) | — | — | "Model returning the average of the web it trained on" | [link](https://www.reddit.com/r/ClaudeAI/comments/1u74zc6/i_got_tired_of_claude_code_building_me_the_same/) |

**X/Twitter:**
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @regent0x_ | "Stop Installing Plugins on Claude Code - The Ultimate Guide" | 315 | 43 | [link](https://x.com/regent0x_/status/2057419591618302029) |
| @regent0x_ | "his dad built a $2M company on a 1986 macintosh plus - no drivers, no plugins..." | 49 | 2 | [link](https://x.com/regent0x_/status/2058079320405332047) |
| @HeyZaraKhan | "20 Claude GitHub Repos that can completely change your life" | 666 | 163 | [link](https://x.com/HeyZaraKhan/status/2056422617351959030) |
| @0xluffy_eth | "20个Claude GitHub仓库能完全改变你的人生" (Chinese resource list) | 144 | 53 | [link](https://x.com/0xluffy_eth/status/2057719369137037793) |
| @alex_prompter | "Perplexity just open-sourced Bumblebee - scans for malicious MCP server configs" | 95 | 19 | [link](https://x.com/alex_prompter/status/2059548217285713933) |
| @pauliusztin_ | "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together" | 51 | 7 | [link](https://x.com/pauliusztin_/status/2063236967987298550) |
| @cherry_mx_reds | "OneNote Desktop Agent - free, open-source Claude Code + Codex plugin" | 9 | — | [link](https://x.com/cherry_mx_reds/status/2066564455929168096) |
| @LandingAI | "We just released Agentic Document Extraction (ADE) skills for AI coding agents" | 4 | 1 | [link](https://x.com/LandingAI/status/2066831209112752255) |
| @oliviscusAI | "Someone built a PM Skills marketplace for Claude. 68 skills and 42 chained workflows" | 1 | 1 | [link](https://x.com/oliviscusAI/status/2066838637375861063) |
| @polsia | "Built the open directory for Claude Code, Cursor, and Windsurf extensions. 2,000+ skills" | — | — | [link](https://x.com/polsia/status/2064450681856200753) |
| @iphonegalaxymd | "Claude Code excels at docs & code but weak on Reddit, GitHub, StackOverflow - Keiro MCP fills the gap" | 2 | 1 | [link](https://x.com/iphonegalaxymd/status/2066858080936067178) |
| @AndrewK404 | "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." | 2 | 1 | [link](https://x.com/AndrewK404/status/2059732591222096368) |

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| arps18 | Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs | 451 | 254 | Canonical reference post | [link](https://arps18.github.io/posts/claude-code-mastery/) |
| mil22 | Dynamic Workflows in Claude Code | 200 | 135 | Anthropic's parallel subagent announcement | [link](https://claude.com/blog/introducing-dynamic-workflows-in-claude-code) |
| robertkarl | Microsoft starts canceling Claude Code licenses | 493 | 466 | — | [link](https://www.theverge.com/tech/930447/microsoft-claude-code-discontinued-notepad) |
| finnworks | Show HN: skills-for-humanity – 171 structured reasoning skills for Claude Code | 28 | 7 | Cross-agent skill library | [link](https://github.com/human-avatar/skills-for-humanity) |
| fabianlindfors | Anthropic pauses credit change for Claude Code | 29 | 7 | — | [link](https://news.ycombinator.com/item?id=48546618) |
| muhammad-shafat | Show HN: Stop returning raw JSON from MCP servers, build rich inline UIs | 11 | 5 | — | [link](https://medium.com/towards-artificial-intelligence/mcp-apps-build-interactive-apps-directly-inside-your-ai-agents-chat-c571678099e3) |
| samuelstros | AgentCRM – Headless CRM for Claude Code | 17 | — | — | [link](https://github.com/cluster-software/agent-crm) |
| haimm | CodeGuilds – community registry for Claude Code (skills, agents, MCP servers) | 3 | — | — | [link](https://codeguilds.dev) |
| arturo | Show HN: A GitOps-style registry for AI agent Workflows, Skills and MCP servers | 4 | 1 | — | [link](https://github.com/Friz-zy/ai-capability-registry) |
| motola23 | Show HN: Claude Soul – cross-session learning engine for Claude Code | 10 | 4 | — | [link](https://news.ycombinator.com/item?id=48184763) |
| sermakarevich | Show HN: Lessons learned from running Claude Code swarms at scale | 10 | 7 | — | [link](https://news.ycombinator.com/item?id=48407998) |

**Bluesky:**
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @why.bsky.team | "Making an agent based procedural city sim, something I've always wanted to play around with but never had the time to code. Claude is a lot of fun." | 153 | [link](https://bsky.app/profile/why.bsky.team/post/3mnxaspuefk22) |
| @hikikomorphism.bsky.social | "The trick is heterogenous agent teams - no need to burn Opus tokens on medium sized tasks when mythos can manage a team of DeepSeek/Gemini agents" | 52 | [link](https://bsky.app/profile/hikikomorphism.bsky.social/post/3mnuw5kfhrc2d) |
| @moomanibe.bsky.social | "no one is doing this and absolutely everyone is using Claude Code and Midjourney" | 24 | [link](https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226) |
| @fpl9000.bsky.social | "I'm considering installing the Pi agent... Given recent news about npm-based supply chain attacks..." | 18 | [link](https://bsky.app/profile/fpl9000.bsky.social/post/3moayr5qg5c2v) |
| @hexacode.bsky.social | "Claude Code vs Cursor vs Copilot vs Codex - which AI coding agent is best in 2026?" | 14 | [link](https://bsky.app/profile/hexacode.bsky.social/post/3mnv76mjbtk2f) |
| @ssp.sh | "Data engineering spent fifteen years building orchestrators. We are now doing the same for AI agents." | 8 | [link](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w) |
| @martindotnet.bsky.social | "engineers will spend days curating their token dashboard... practically zero time adding telemetry to their apps" | 7 | [link](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i) |
| @ssp.sh | "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category." | 5 | [link](https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q) |
| @thenewstack.io | "Anthropic's dynamic workflows in Claude Code let Claude run parallel subagents. We tested them." | 3 | [link](https://bsky.app/profile/thenewstack.io/post/3mo7yf7mjvo2v) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| claudemarketplaces.com | [link](https://claudemarketplaces.com/) | Official + community plugin directory; 300k+ monthly devs |
| clarista.io | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | Complete MCP guide; "USB for AI" framing |
| dev.to (alexcloudstar) | [link](https://dev.to/alexcloudstar/the-claude-code-plugin-marketplace-how-skills-mcp-servers-and-plugins-actually-fit-together-in-5532) | Narrative walkthrough of plugin architecture; first-hand install experience |
| explainx.ai | [link](https://explainx.ai/blog/what-are-agent-skills-complete-guide) | 30+ platforms supporting Agent Skills format; 280k+ public skills |
| agensi.io | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Complete list of every AI skill marketplace in 2026 |
| groundy.com | [link](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | Official marketplace: 101 vetted + 68 partner plugins |
| skills.2389.ai | [link](https://skills.2389.ai/) | 2389 Research plugin marketplace with npx CLI |
| okhlopkov.com | [link](https://okhlopkov.com/claude-code-setup-mcp-hooks-skills-2026/) | Practitioner 5-layer setup guide |
| arxiv.org | [link](https://arxiv.org/pdf/2602.06547) | "Malicious Agent Skills in the Wild" security study |
| smithhorngroup.substack.com | [link](https://smithhorngroup.substack.com/p/choosing-between-skills-subagents) | Decision guide: when to use skills vs subagents vs MCP |
| developertoolkit.ai | [link](https://developertoolkit.ai/en/claude-code/quick-start/mcp-setup/) | MCP setup: connecting Sentry, GitHub, DB, Jira in one session |
| computingforgeeks.com | [link](https://computingforgeeks.com/claude-code-mcp-servers-setup/) | MCP server setup guide |
| claudefolio.com | [link](https://claudefolio.com/guides/custom-slash-commands-and-mcp-servers) | Skills vs MCP explainer |
| llmbestpractices.com | [link](https://llmbestpractices.com/ai-agents/claude-code-mcp) | Rule: prefer MCP over Bash when integration is cross-session |
| github.com/human-avatar/skills-for-humanity | [link](https://github.com/human-avatar/skills-for-humanity) | 171 structured reasoning skills for Claude Code |
| github.com/Friz-zy/ai-capability-registry | [link](https://github.com/Friz-zy/ai-capability-registry) | GitOps-style registry for agent workflows, skills, and MCP servers |
| github.com/swissmarley/SkillsForAgents | [link](https://github.com/swissmarley/SkillsForAgents) | Cross-agent skill marketplace (Claude Code, Codex, OpenCode, Hermes) |
| github.com/chirag2653/public-claude-code-plugins | [link](https://github.com/chirag2653/public-claude-code-plugins) | Personal plugin marketplace template |
| github.com/anyshift-io/claude-plugins | [link](https://github.com/anyshift-io/claude-plugins) | Anyshift's community plugin marketplace |
| github.com/steipete/claude-code-mcp | [link](https://github.com/steipete/claude-code-mcp) | Claude Code as one-shot MCP server (agent-in-agent pattern) |

---

## Stats Block

```
├─ 🟠 Reddit: 8 threads
├─ 🔵 X: 25 posts │ 1,592 likes │ 357 reposts
├─ 🟢 HN: 20 stories │ 1,308 points │ 897 comments
├─ 🦋 Bluesky: 12 posts │ 302 likes │ 7 reposts
├─ 🌐 Web: 20 pages (engine: developertoolkit.ai, computingforgeeks.com, llmbestpractices.com, GitHub, skills.2389.ai, claudefolio.com, clarista.io, dev.to + 10 WebSearch supplements)
└─ 🗣️ Top voices: @regent0x_, @ssp.sh, @oliviscusAI, @LandingAI │ r/ClaudeAI, r/ChatGPTCoding
```

---

## Data Gaps

- **YouTube: 0 results** - YouTube search returned zero results for this topic despite multiple query attempts; SC YouTube API returned HTTP 402 (Payment Required). Video tutorials on Claude Code skills/MCP are likely plentiful but not captured this run.
- **TikTok/Instagram: 0 results** - Both returned zero results; SC API HTTP 402. Short-form video content about Claude Code plugins is uncaptured.
- **GitHub: 0 items from engine** - No GitHub token was available, so the engine could not fetch star counts, README content, or issue data from the listed repos. GitHub data came from the Web/grounding source instead.
- **Reddit coverage is thin** - Only 8 threads captured due to Reddit public API 403 errors on the primary search endpoint; RSS fallback retrieved minimal results. The actual Reddit discussion volume on this topic is almost certainly much higher.
- **34 of 75 dated items are from the last 7 days** - Coverage of older discussions in the 30-day window is thinner.
- **Approximate coverage:** 60-65% of actual discussion volume given the Reddit and video source gaps.

---

## Key Quotes

> "Discovery is scattered across GitHub, Discord threads, blog posts, and individual repos. Even when I found something useful, it was hard to answer: Is this maintained? What does it install? Does it use hooks or MCP servers?" - r/ClaudeAI ([link](https://www.reddit.com/r/ClaudeAI/comments/1tognh0/i_built_a_searchable_directory_for_claude_code/))

> "his dad built a $2M company on a 1986 macintosh plus - no drivers, no plugins, no setup - just worked. 40 years later his son needs 5 MCP servers and 14,000 tokens of overhead to do what /compact does for free" - [@regent0x_](https://x.com/regent0x_/status/2058079320405332047)

> "187 items loaded [at session start], but I only used 4 actively. That's ~8,000 tokens per session completely wasted on dead weight, hurting the prompt cache hit rate" - r/ClaudeAI ([link](https://www.reddit.com/r/ClaudeAI/comments/1u3unj7/using_claude_code_youre_probably_wasting_8k/))

> "Connectivity is not one thing. The best agents use all of it - skills, CLI, MCP - together." - David Soria Parra, Anthropic (co-creator of MCP), per [@pauliusztin_](https://x.com/pauliusztin_/status/2063236967987298550)

> "Data engineering spent fifteen years building orchestrators - Airflow, Dagster, Prefect, Kestra. We are now doing the same thing for AI agents." - [@ssp.sh](https://bsky.app/profile/ssp.sh/post/3mof7666sqw2w)

> "Skill = teach Claude one workflow. Plugin = package and share a broader toolkit." - [@AndrewK404](https://x.com/AndrewK404/status/2059732591222096368)

> "I find it hilarious that engineers will spend days, weeks even, curating their token dashboard for their Claude Code session, when they'll spend practically zero time adding telemetry to their apps to make it better." - [@martindotnet.bsky.social](https://bsky.app/profile/martindotnet.bsky.social/post/3moanuy537k2i)

> "no one is doing this and absolutely everyone is using Claude Code and Midjourney. Like there's zero nuance in the actual practical expression here." - [@moomanibe.bsky.social](https://bsky.app/profile/moomanibe.bsky.social/post/3mobt7xh3u226)

> "A year ago, vibe coding meant one CLI in one terminal. Now it is a whole category. Claude Code, OpenCode, Amp, Crush, Pi, aichat, Deer-flow. Each one is an agent harness that runs mostly autonomously in the terminal." - [@ssp.sh](https://bsky.app/profile/ssp.sh/post/3modnqls3fx2q)

> "The model context protocol is like USB for AI: one protocol, many tools, many clients." - [Clarista](https://www.clarista.io/blog/claude-code-mcp-plugins-guide)
