# Agent Skills & Plugin Ecosystems — Daily Briefing
**Date:** 2026-05-08
**Query type:** GENERAL
**Sources:** Hacker News, YouTube, Web, GitHub

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 8 stories | 818+ points, 430+ comments | Claude Skills thread: 816 pts / 427 comments; 3 Show HN entries |
| YouTube | 4 videos | — | No transcript data; titles extracted from search |
| Web | 53 pages | — | Official docs, blogs, marketplace directories, news |
| Reddit | 0 | — | Domain inaccessible to crawler |
| X/Twitter | 0 | — | Excluded per research parameters |
| TikTok | 0 | — | No results |
| Instagram | 0 | — | No results |
| Bluesky | 0 | — | No results |
| Polymarket | 0 | — | No relevant markets found |

---

## Synthesized Findings

### 1. The Claude Code Extension Taxonomy: Skills, Plugins, MCP, Hooks

The most-discussed topic across Hacker News, developer blogs, and official documentation in the past 30 days is the **correct mental model for Claude Code's five extension types** and when to use each. Multiple practitioner guides converged on the same architecture:

- **Skills** (30–50 token overhead, progressive loading): procedural instructions in a `SKILL.md` file; Claude invokes them via semantic matching when relevant to the task. Token-efficient — they add only names and descriptions to context at startup, with full instructions loading on demand.
- **Plugins**: shareable, versioned bundles that combine skills, agents, hooks, MCP server configs, LSP servers, and background monitors. Skills in plugins are namespaced (`/plugin-name:skill-name`). Distributed via marketplace catalog repos hosted on GitHub.
- **MCP Servers** (1–50k tokens upfront): external tool connectivity via the Model Context Protocol. Use MCP when Claude needs real-time access to external systems — GitHub, databases, browsers, APIs. Unlike skills, all tools load upfront, making a 5-server, 58-tool setup consume ~55,000 tokens before a single conversation turn.
- **Hooks**: event handlers (e.g., PostToolUse) for automation with minimal overhead.
- **Agents/Slash Commands**: orchestration primitives, now supporting multiagent delegation.

The distinction clarified most clearly by [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins) and [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026): *"Skills are for procedural knowledge; MCP is for external connectivity."* The official [Claude Code docs](https://code.claude.com/docs/en/plugins) now provide a full plugin authoring guide, including `--plugin-dir` for local dev, `--plugin-url` (added in v2.1.126) for URL-distributed `.zip` archives, and submission paths to the official marketplace.

Sources: Web ([code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins), [morphllm.com](https://www.morphllm.com/claude-code-skills-mcp-plugins), [devtoolpicks.com](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026), [alexop.dev](https://alexop.dev/posts/understanding-claude-code-full-stack/), [agensi.io](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained), [nimbalyst.com](https://nimbalyst.com/blog/claude-code-plugins-guide/)), HN (#45607117)

---

### 2. Marketplace Scale: The Ecosystem Exploded

The Claude Code plugin/skill ecosystem has grown to measurable scale in early 2026. As of May 7, 2026, [claudemarketplaces.com](https://claudemarketplaces.com/) — a third-party directory — tracks:

- **4,200+ skills**
- **770+ MCP servers**
- **2,500+ marketplaces**
- **140,000+ monthly visitors**

Top skills by install count on that directory:
1. `find-skills` — 1,100,000+ installs
2. `vercel-react-best-practices` — 320,400+ installs
3. `frontend-design` — 299,900+ installs
4. `web-design-guidelines` — 256,200+ installs
5. `agent-browser` — 186,700+ installs

Anthropic's **official plugin directory** ([github.com/anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)) has earned 18.8k GitHub stars, 2.3k forks, and 602 open issues — indicating heavy community engagement. The official plugin marketplace launched in **February 2026**. Plugins can be submitted via [claude.ai/settings/plugins/submit](https://claude.ai/settings/plugins/submit) or [platform.claude.com/plugins/submit](https://platform.claude.com/plugins/submit).

The community-built **jeremylongshore/claude-code-plugins-plus-skills** ([GitHub](https://github.com/jeremylongshore/claude-code-plugins-plus-skills)) offers 425 plugins, 2,810 skills, and 200 agents with a CLI package manager (`@intentsolutionsio/ccpi`) and a web interface at [tonsofskills.com](https://tonsofskills.com). It has 2.1k stars and 16 contributors.

Notably, [self.md](https://self.md/guides/best-claude-code-plugins/) estimated that while 250+ skill packages exist on GitHub, only ~30 are worth installing — a signal-to-noise concern that is also surfaced in multiple HN comments.

Cross-platform skill repositories are emerging, too: [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) offers 232+ skills that work across Claude Code, Codex, Gemini CLI, Cursor, and 8 other agents.

Sources: Web ([claudemarketplaces.com](https://claudemarketplaces.com/), [self.md](https://self.md/guides/best-claude-code-plugins/), [blog.brightcoding.dev](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers), [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers)), GitHub ([anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official), [jeremylongshore](https://github.com/jeremylongshore/claude-code-plugins-plus-skills), [alirezarezvani](https://github.com/alirezarezvani/claude-skills), [ComposioHQ](https://github.com/ComposioHQ/awesome-claude-plugins), [quemsah](https://github.com/quemsah/awesome-claude-plugins), [daymade](https://github.com/daymade/claude-code-skills), [netresearch](https://github.com/netresearch/claude-code-marketplace))

---

### 3. MCP Becomes Universal Infrastructure via Linux Foundation

The Model Context Protocol trajectory in the past 30 days is defined by its institutional ascent:

- **November 2024**: Anthropic launches MCP
- **Early 2025**: OpenAI and Google DeepMind adopt MCP
- **December 9, 2025**: Anthropic donates MCP to the Linux Foundation's newly formed **Agentic AI Foundation (AAIF)** — co-founded with Block (contributing *goose*) and OpenAI (contributing *AGENTS.md*). AAIF supporters include Google, Microsoft, AWS, Cloudflare, and Bloomberg.
- **By January 2026**: 97 million monthly SDK downloads, 10,000+ active servers, first-class client support across Claude Code, ChatGPT, Cursor, Gemini, Microsoft Copilot, VS Code, and many more.

[mcp.so](https://mcp.so/) now indexes **20,756 MCP servers**. [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers) tracks 10,000+ tools across 700+ providers. MCP gateways — intermediary proxies that centralize authentication, authorization, and auditing across multiple MCP servers — are a growing category as of early 2026.

The significance: MCP is now **client-agnostic infrastructure**. One MCP server works with Claude Code, Cursor, Windsurf, VS Code, and any compliant host — unlike Claude-specific plugins. [Microsoft](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) has integrated MCP into its Agent Framework; remote MCP support in Claude Code drew its own [HN thread](https://news.ycombinator.com/item?id=44312363).

Sources: Web ([anthropic.com/news](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation), [blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/), [linuxfoundation.org](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation), [aaif.io](https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/), [github.blog](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/), [openai.com/index/agentic-ai-foundation](https://openai.com/index/agentic-ai-foundation/), [techcrunch.com](https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/), [thenewstack.io](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/), [infoq.com](https://www.infoq.com/news/2025/12/agentic-ai-foundation/), [mcp.so](https://mcp.so/), [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers), [lobehub.com/mcp](https://lobehub.com/mcp), [mcpmarket.com](https://mcpmarket.com/)), HN ([#44312363](https://news.ycombinator.com/item?id=44312363))

---

### 4. AWS Launches Agent Registry — Enterprise Governance for Agent Sprawl

AWS entered the agent skill governance space in **April 2026**, launching the **AWS Agent Registry** (preview) as part of Amazon Bedrock AgentCore. It is a private, governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources within an organization.

Key features per [AWS blog](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/):
- **Hybrid search**: semantic + keyword, supporting both natural language and exact-name lookups
- **Approval workflow**: draft → pending → discoverable; ensures governance before sharing
- **Access methods**: AgentCore Console UI, AWS CLI/SDK, or as an MCP server from any IDE
- **Supported resource types**: MCP servers, agents, skills, custom resources (with JSON Schema validation for MCP and agent records)
- **Available in 5 AWS regions**: US West (Oregon), Asia Pacific (Tokyo, Sydney), Europe (Ireland), US East (N. Virginia)

This drew coverage from [InfoQ](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/), [The Register](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/) ("AWS: Agents shouldn't be secret, so we built a registry"), [SiliconAngle](https://siliconangle.com/2026/04/09/aws-previews-cloud-agnostic-registry-managing-agentic-fleets-scale/), and [DEV Community](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91).

JFrog also positioned its **Agent Skills Registry** as a governance solution, with advanced scanning, cryptographic signing, and provenance attestation — [blog.jfrog.com](https://jfrog.com/blog/agent-skills-new-ai-packages/). JFrog author Yonatan Arbel argues that proprietary marketplaces (Claude Code, Cursor) create "walled gardens" that force governance infrastructure rebuilds when switching AI vendors — making a vendor-neutral governance layer essential for enterprises.

Sources: Web ([aws.amazon.com/about-aws/whats-new](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/), [aws.amazon.com/blogs/machine-learning](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/), [docs.aws.amazon.com](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html), [infoq.com/2026/04](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/), [theregister.com](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/), [siliconangle.com](https://siliconangle.com/2026/04/09/aws-previews-cloud-agnostic-registry-managing-agentic-fleets-scale/), [dev.to/aws-builders](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91), [heeki.medium.com](https://heeki.medium.com/integrating-aws-agent-registry-into-your-agent-platform-for-discovery-and-governance-3350920204a4), [dev.classmethod.jp](https://dev.classmethod.jp/en/articles/aws-agent-registry-preview/), [jfrog.com/blog](https://jfrog.com/blog/agent-skills-new-ai-packages/))

---

### 5. Developer Debate: Are Skills Actually Novel? (HN Thread, 816 Points)

The largest community discussion in this period was the [**"Claude Skills"**](https://news.ycombinator.com/item?id=45607117) Hacker News thread (816 points, 427 comments). A parallel post by Simon Willison — ["Claude Skills are awesome, maybe a bigger deal than MCP"](https://news.ycombinator.com/item?id=45619537) — sparked the debate.

**The core dispute:**
- *Skeptics*: Skills are "a design pattern / prompt engineering trick" that could be implemented via MCP or system prompts. Not a breakthrough.
- *Defenders*: "Like Docker — Docker/containers are also just shell scripts for kernel features; conceptually simple but transformative." The simplicity is the feature.

**Concerns raised:**
- Claude starts "from ground zero" with each interaction, unable to accumulate expertise like humans do through practice.
- Overlap with AGENTS.md files, Cursor Rules, system prompts — questioned as "UX upgrade vs. fundamental innovation."
- Quote capturing wider sentiment: *"All these things are designed to create lock in."*

A companion [HN thread on agent skill configs](https://news.ycombinator.com/item?id=46396930) surfaced the complexity problem: "You've got your CLAUDE.md, Skills, Agents, MCP, slash commands, and so much more" — implying configuration sprawl.

The [Agnix linter project](https://news.ycombinator.com/item?id=46983879) addressed this: a Rust-based tool with 156 validation rules across 28 categories for 11 AI platforms. The creator's motivation: a skill named `Review-Code` failed silently because the spec requires kebab-case (`review-code`). *"None of these tools validate their own configuration files."*

The [Skillz project](https://news.ycombinator.com/item?id=45649295) tackled lock-in: it exposes Claude Skills to Codex, GitHub Copilot, and any other agent via MCP — a cross-vendor portability layer.

Developer consensus extracted from [Developers Digest's HN synthesis](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026): (1) workflow > model selection; (2) skills outperform raw prompting; (3) orchestration beats autonomy; (4) verification is the bottleneck; (5) economic value > spectacle.

Sources: HN ([#45607117](https://news.ycombinator.com/item?id=45607117), [#45619537](https://news.ycombinator.com/item?id=45619537), [#46983879](https://news.ycombinator.com/item?id=46983879), [#45649295](https://news.ycombinator.com/item?id=45649295), [#46396930](https://news.ycombinator.com/item?id=46396930)), Web ([developersdigest.tech](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026))

---

### 6. Security Risks: Skills and Plugins as Attack Vectors

A notable April 2026 [Medium post by Philip Nakhleh](https://medium.com/@philipnakhleh/the-hidden-dangers-of-claude-code-how-cyber-attackers-are-using-ai-skills-plugins-62fa891bfd30) detailed four attack vectors specific to Claude Code skills and plugins:

1. **Malicious skills/plugins**: seemingly benign tools (e.g., "CSV Analyzer") that execute hidden commands, deploy ransomware, steal API keys.
2. **Supply chain compromise**: malicious `.claude/settings.json` or Hook files in public repos enable arbitrary code execution without user interaction.
3. **Autonomous cyberattacks**: threat actors decompose malicious objectives into small steps, letting Claude handle "80–90% of the attack chain."
4. **Prompt injection**: hidden instructions in files or web content manipulate Claude into data exfiltration.

Core vulnerability: *"Once you install and approve one, it can run real code on your machine. Attackers love that trust."* Multiple CVEs were patched in late 2025. No built-in malware scanning exists in the plugin system. State-sponsored groups reportedly use these chains at scale.

Recommended mitigations: install only from official/verified sources, use sandbox execution (Docker/VMs or Anthropic's sandbox runtime), disable auto-execution, and centralize skill approval for organizations.

This theme also runs through the [JFrog blog](https://jfrog.com/blog/agent-skills-new-ai-packages/) (fragmented distribution makes governance impossible at scale) and the [Agnix linter](https://news.ycombinator.com/item?id=46983879) (silent misconfigurations as the configuration attack surface).

Sources: Web ([medium.com/@philipnakhleh](https://medium.com/@philipnakhleh/the-hidden-dangers-of-claude-code-how-cyber-attackers-are-using-ai-skills-plugins-62fa891bfd30), [jfrog.com/blog](https://jfrog.com/blog/agent-skills-new-ai-packages/)), HN ([#46983879](https://news.ycombinator.com/item?id=46983879))

---

### 7. Agent Skills as the New npm: A Cross-Platform Packaging Standard

A converging framing across multiple independent sources: **agent skills are becoming the package manager layer of AI**, analogous to npm for JavaScript or pip for Python.

Key data points:
- **December 2025**: Anthropic released the Agent Skills specification as an open standard; OpenAI adopted the same format for Codex CLI and ChatGPT — enabling cross-platform skills.
- **Spring AI** (Jan 13, 2026) [documented](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/) skills as LLM-portable: same skill works on OpenAI, Anthropic, Google Gemini, and others without rewriting.
- **SkillsMP** aggregates 500,000+ skills from GitHub (66,541+ as of Jan 2026); raw numbers include low-quality entries filtered by 2-star minimum.
- Five major marketplaces per [KDnuggets](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents): SkillsMP (425k+), LobeHub ([lobehub.com/skills](https://lobehub.com/skills), 169k+), agentskill.sh (110k+), skills.sh (87k+), ClawHub (20k+).
- [AgentSkillsHub.dev](https://agentskillshub.dev/) curates 1,200+ verified skills with security analysis.
- [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) framing: *"Agent Skills Are the New npm."*
- [KDnuggets framing](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents): *"what GitHub is for code and Hugging Face is for ML models."*

The [fast-agent framework](https://fast-agent.ai/agents/skills/) and [DavidGraca's open catalog](https://news.ycombinator.com/item?id=46692865) (aggregating Anthropic, OpenAI, GitHub, Vercel skills into a unified JSON + MCP server) further reinforce the cross-provider portability push. The catalog uses TOON format to reduce payload size ~40%.

Sources: Web ([spring.io/blog](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/), [skillsmp.com](https://skillsmp.com/), [kdnuggets.com](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents), [lobehub.com/skills](https://lobehub.com/skills), [agentskillshub.dev](https://agentskillshub.dev/), [agentskills.io](https://agentskills.io/home), [fast-agent.ai](https://fast-agent.ai/agents/skills/), [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026), [termdock.com](https://www.termdock.com/en/blog/agent-skills-guide), [agensi.io marketplace comparison](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026), [agensi.io 2026 comparison](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026), [virtualuncle.com](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/), [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/), [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/)), HN ([#46692865](https://news.ycombinator.com/item?id=46692865))

---

### 8. Code with Claude SF 2026 & Recent Release Activity

The **Code with Claude SF 2026** event ([blakecrosley.com recap](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap)) delivered a cluster of platform announcements:

- **Rate limits doubled** across Pro, Max, Team, Enterprise; peak-hours throttling removed for Pro/Max
- **SpaceX Colossus 1 partnership**: 300MW, 220,000+ NVIDIA GPUs added
- **Financial services plugin templates**: 10 templates shipped for pitch builders, earnings reviewers, reconciliation tools
- **Microsoft 365 add-in integration** (Excel, PowerPoint, Word, Outlook)
- **Moody's MCP app**: proprietary credit ratings and data on 600M+ companies
- **Managed Agents features**: *Dreaming* (memory extraction from sessions, research preview), *Outcomes* (rubric-based grading, public beta, +8.4%/+10.1% task success on docx/pptx), *Multiagent Orchestration* (public beta)
- **Vercept acquisition**: computer-use capabilities for desktop/mobile
- **Claude Code v2.1.126–v2.1.131** (May 1–6): `--plugin-url` flag, working `skillOverrides`, `claude project purge`, stability fixes

Additional recent tooling: [Almanac MCP](https://news.ycombinator.com/item?id=47855284) turns Claude Code into a Deep Research agent; [OpenTimelineEngine MCP](https://news.ycombinator.com/item?id=47187858) provides shared local memory across Claude Code and Codex.

Sources: Web ([blakecrosley.com](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap), [releasebot.io/claude-code](https://releasebot.io/updates/anthropic/claude-code), [releasebot.io/anthropic](https://releasebot.io/updates/anthropic), [releasebot.io/claude](https://releasebot.io/updates/anthropic/claude), [github.com/anthropics/claude-code/releases](https://github.com/anthropics/claude-code/releases), [support.claude.com](https://support.claude.com/en/articles/12138966-release-notes), [claudefa.st/changelog](https://claudefa.st/blog/guide/changelog), [aimaker.substack.com](https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide)), HN ([#47855284](https://news.ycombinator.com/item?id=47855284), [#47187858](https://news.ycombinator.com/item?id=47187858))

---

## Cross-Source Patterns

**Pattern 1: Skills > Raw Prompting — Confirmed Across All Developer Sources**
Appearing on: HN (816-pt thread), Developers Digest synthesis, morphllm.com guide, BrightCoding, self.md, Mejba's top-10 list
Signal: Every practitioner source agrees that encoding workflows as skills or equivalent local instructions outperforms ad-hoc prompting. "If you are still relying on giant custom prompts pasted into every session, you are using 2025 tactics in a 2026 environment." Teams benefit from standardized, repo-local guidance.

**Pattern 2: Quality Over Quantity in Skill Selection**
Appearing on: HN comments, self.md, SkillsMP review, KDnuggets
Signal: Ecosystem scale (500k+ skills) does not mean quality. Self.md: ~30 of 250+ GitHub skill packages are worth installing. SkillsMP's 2-star filter is "basically no bar at all." Security-conscious users are directed to platforms with multi-layer scanning (agentskill.sh, ClawHub). Best practice: 2-3 MCP servers + a few custom skills.

**Pattern 3: Governance Crisis as Fragmentation Scales**
Appearing on: JFrog blog, AWS Agent Registry launch, Agnix HN thread, Philip Nakhleh security article
Signal: Multiple independent actors (JFrog, AWS, Agnix, security researchers) converged on the same conclusion: skill distribution is highly fragmented, lacks governance, and creates meaningful security and operational risk. This is the dominant enterprise storyline in the past 30 days.

**Pattern 4: Cross-Platform Portability as Strategic Goal**
Appearing on: alirezarezvani/claude-skills (8+ agents), Spring AI blog, Skillz HN thread, Agent Skills open catalog, SkillsMP
Key quotes: "LLM portability — skills work across OpenAI, Anthropic, Google Gemini and other supported models without rewriting" (Spring AI). The open Agent Skills spec (released Dec 2025, adopted by both Anthropic and OpenAI) enables skills to work across Claude Code, Codex, and ChatGPT.

**Pattern 5: MCP as the Winner of the Tool Connectivity Layer**
Appearing on: MCP.so (20,756 servers), AAIF announcement, Microsoft Azure docs, AWS AgentCore, Code with Claude SF announcements
Signal: MCP's Linux Foundation donation and universal adoption have cemented it as the connectivity standard. Plugins remain Claude-specific; MCP is infrastructure. Even Anthropic's own plugin system uses `.mcp.json` inside plugins.

---

## Per-Platform Tables

**Hacker News:**
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (Anthropic post) | Claude Skills | 816 | 427 | "All these things are designed to create lock in" | [link](https://news.ycombinator.com/item?id=45607117) |
| simonw (Willison) | Claude Skills are awesome, maybe a bigger deal than MCP | ~816 | — | Called skills "maybe a bigger deal than MCP" | [link](https://news.ycombinator.com/item?id=45619537) |
| DavidGraca | Agent Skills – Open Trusted Catalog: Claude, OpenAI, Vercel, GH | 1 | 1 | "If you're building an MCP server or AI agent, you need to scrape each one individually" | [link](https://news.ycombinator.com/item?id=46692865) |
| anotherCodder | Show HN: Agnix – lint your AI agent configs (Claude.md, skills, MCP, hooks) | 1 | 1 | "None of these tools validate their own configuration files." | [link](https://news.ycombinator.com/item?id=46983879) |
| (Skillz author) | Skillz: Use Claude Skills in Codex, Copilot, or Any Other Agent via MCP | — | — | Cross-vendor portability via MCP wrapper | [link](https://news.ycombinator.com/item?id=45649295) |
| (author) | Show HN: Almanac MCP, turn Claude Code into a Deep Research agent | — | — | — | [link](https://news.ycombinator.com/item?id=47855284) |
| (author) | Remote MCP Support in Claude Code | — | — | — | [link](https://news.ycombinator.com/item?id=44312363) |
| (author) | Hacking Your Own AI Coding Assistant with Claude Pro and MCP | — | — | — | [link](https://news.ycombinator.com/item?id=43410866) |

**YouTube:**
| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (French creator) | Top 10 des Skills, plugins sur Claude Code (mai 2026) | — | — | No | [link](https://www.youtube.com/watch?v=YcX4VcGBIiU) |
| Nimbalyst | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| (creator) | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | — | — | No | [link](https://www.youtube.com/watch?v=KjEFy5wjFQg) |
| (creator) | How to Disable Plugins in Claude Code CLI (2026) | — | — | No | [link](https://www.youtube.com/watch?v=qO3CzLmENsc) |

**Web:**
| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Claude Code Docs | [code.claude.com/docs/en/plugins](https://code.claude.com/docs/en/plugins) | Full plugin authoring guide, structure, `--plugin-url` flag |
| Claude Code Docs | [code.claude.com/docs/en/discover-plugins](https://code.claude.com/docs/en/discover-plugins) | How to install plugins from marketplaces |
| Claude API Docs | [platform.claude.com/docs/en/agents-and-tools/agent-skills/overview](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) | Agent Skills API overview |
| claudemarketplaces.com | [claudemarketplaces.com](https://claudemarketplaces.com/) | 4,200+ skills, 770+ MCP, 140k monthly visitors |
| MCP.so | [mcp.so](https://mcp.so/) | 20,756 MCP servers indexed |
| MCPMarket | [mcpmarket.com](https://mcpmarket.com/) | MCP server directory |
| MCPBundles | [mcpbundles.com](https://www.mcpbundles.com/blog/best-mcp-servers) | 10k+ tools, 700+ providers |
| LobeHub Skills | [lobehub.com/skills](https://lobehub.com/skills) | 169,739 indexed skills |
| LobeHub MCP | [lobehub.com/mcp](https://lobehub.com/mcp) | MCP marketplace |
| SkillsMP | [skillsmp.com](https://skillsmp.com/) | 66,541+ skills; broad aggregation |
| AgentSkillsHub | [agentskillshub.dev](https://agentskillshub.dev/) | 1,200+ verified skills with security analysis |
| AgentSkills.io | [agentskills.io/home](https://agentskills.io/home) | Open skills directory |
| fast-agent | [fast-agent.ai/agents/skills](https://fast-agent.ai/agents/skills/) | Framework skills documentation |
| JFrog | [jfrog.com/blog/agent-skills-new-ai-packages](https://jfrog.com/blog/agent-skills-new-ai-packages/) | Agent skills governance; walled gardens critique |
| Spring AI | [spring.io/blog/2026/01/13](https://spring.io/blog/2026/01/13/spring-ai-generic-agent-skills/) | Agent skills as modular reusable capabilities; LLM-portable |
| Medium / Nakhleh | [medium.com/@philipnakhleh](https://medium.com/@philipnakhleh/the-hidden-dangers-of-claude-code-how-cyber-attackers-are-using-ai-skills-plugins-62fa891bfd30) | Security risks; attack vectors; state-sponsored exploitation |
| KDnuggets | [kdnuggets.com/top-5-agent-skill-marketplaces](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents) | Top 5 marketplaces comparison |
| Code with Claude SF | [blakecrosley.com](https://blakecrosley.com/blog/code-with-claude-sf-2026-recap) | Event recap; rate limits, financial plugins, Vercept acquisition |
| Developers Digest (HN) | [developersdigest.tech/hacker-news](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | 5 HN-derived truths about agent skills in 2026 |
| Developers Digest (skills) | [developersdigest.tech/skills](https://www.developersdigest.tech/blog/best-claude-code-skills-2026) | Best Claude Code skills 2026 curated list |
| Developers Digest (teams) | [developersdigest.tech/teams](https://www.developersdigest.tech/blog/claude-code-agent-teams-subagents-2026) | Claude Code agent teams and subagents 2026 playbook |
| morphllm.com (skills) | [morphllm.com/skills-mcp-plugins](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Token cost comparison; when to use each type |
| morphllm.com (extensions) | [morphllm.com/extensions](https://www.morphllm.com/claude-code-extensions) | Claude Code full extension system guide |
| Nimbalyst (plugins) | [nimbalyst.com/plugins](https://nimbalyst.com/blog/claude-code-plugins-guide/) | 2026 plugins guide |
| Nimbalyst (MCP) | [nimbalyst.com/mcp](https://nimbalyst.com/blog/claude-code-mcp-setup/) | MCP setup guide |
| devtoolpicks.com | [devtoolpicks.com/skills-vs-mcp](https://devtoolpicks.com/blog/claude-skills-vs-mcp-connectors-vs-plugins-2026) | Skills vs MCP vs Plugins comparison |
| alexop.dev | [alexop.dev/claude-code-full-stack](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Full stack explanation: MCP, Skills, Subagents, Hooks |
| BrightCoding | [blog.brightcoding.dev](https://www.blog.brightcoding.dev/2026/04/26/claude-skills-marketplace-the-essential-plugin-hub-for-developers) | 97.6% token savings example; marketplace adoption |
| agensi.io (plugins vs skills) | [agensi.io/plugins-vs-skills](https://www.agensi.io/learn/claude-code-plugins-vs-skills-explained) | Plugins vs Skills explainer |
| agensi.io (best marketplaces) | [agensi.io/best-marketplaces](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | Best AI agent skills marketplaces 2026 |
| agensi.io (comparison) | [agensi.io/comparison](https://www.agensi.io/learn/ai-agent-skills-marketplace-comparison-2026) | Marketplace comparison |
| ice-ice-bear | [ice-ice-bear.github.io](https://ice-ice-bear.github.io/posts/2026-04-03-claude-code-plugin-marketplace/) | Deep dive on Claude Code plugin marketplace |
| TurboDocx | [turbodocx.com](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers) | Best Claude Code plugins, skills & MCP servers |
| claudefa.st (MCP) | [claudefa.st/mcp](https://claudefa.st/blog/tools/mcp-extensions/best-addons) | 50+ best MCP servers for Claude Code |
| claudefa.st (changelog) | [claudefa.st/changelog](https://claudefa.st/blog/guide/changelog) | Claude Code changelog 2026 |
| self.md | [self.md/best-plugins](https://self.md/guides/best-claude-code-plugins/) | Quality signal: only 30/250 GitHub skill repos worth installing |
| Mejba | [mejba.me/top-10](https://www.mejba.me/blog/top-10-claude-code-skills-plugins-clis-2026) | Top 10 Claude Code skills, plugins & CLIs 2026 |
| buildmvpfast | [buildmvpfast.com](https://www.buildmvpfast.com/blog/agent-skills-npm-ai-package-manager-2026) | "Agent Skills Are the New npm" |
| aimaker substack | [aimaker.substack.com](https://aimaker.substack.com/p/anthropic-claude-updates-q1-2026-guide) | Complete guide to Claude Q1 2026 updates |
| termdock | [termdock.com](https://www.termdock.com/en/blog/agent-skills-guide) | Agent skills guide 2026 |
| virtualuncle | [virtualuncle.com](https://virtualuncle.com/agent-skills-marketplace-skills-sh-2026/) | Skills.sh marketplace guide |
| smartscope | [smartscope.blog](https://smartscope.blog/en/blog/skillsmp-marketplace-guide/) | SkillsMP review 2026 |
| chris-ayers | [chris-ayers.com](https://chris-ayers.com/posts/agent-skills-plugins-marketplace/) | Agent skills, plugins and marketplace complete guide |
| Anthropic AAIF | [anthropic.com/news/mcp-donation](https://www.anthropic.com/news/donating-the-model-context-protocol-and-establishing-of-the-agentic-ai-foundation) | Official MCP donation announcement |
| MCP Blog | [blog.modelcontextprotocol.io](https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/) | MCP joins AAIF announcement |
| Linux Foundation | [linuxfoundation.org/AAIF](https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation) | AAIF formation press release |
| AAIF | [aaif.io](https://aaif.io/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation-aaif-anchored-by-new-project-contributions-including-model-context-protocol-mcp-goose-and-agents-md/) | AAIF official site |
| GitHub Blog | [github.blog/MCP-LF](https://github.blog/open-source/maintainers/mcp-joins-the-linux-foundation-what-this-means-for-developers-building-the-next-era-of-ai-tools-and-agents/) | MCP joins Linux Foundation: what it means |
| OpenAI | [openai.com/AAIF](https://openai.com/index/agentic-ai-foundation/) | OpenAI AAIF announcement |
| TechCrunch | [techcrunch.com/AAIF](https://techcrunch.com/2025/12/09/openai-anthropic-and-block-join-new-linux-foundation-effort-to-standardize-the-ai-agent-era/) | AAIF coverage |
| The New Stack | [thenewstack.io](https://thenewstack.io/anthropic-donates-the-mcp-protocol-to-the-agentic-ai-foundation/) | MCP donation coverage |
| InfoQ (AAIF) | [infoq.com/2025/12/AAIF](https://www.infoq.com/news/2025/12/agentic-ai-foundation/) | AAIF InfoQ coverage |
| AWS what's new | [aws.amazon.com/whats-new/agent-registry](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | AWS Agent Registry preview announcement |
| AWS ML Blog | [aws.amazon.com/blogs/ml/agent-registry](https://aws.amazon.com/blogs/machine-learning/the-future-of-managing-agents-at-scale-aws-agent-registry-now-in-preview/) | AWS Agent Registry deep-dive |
| AWS Docs | [docs.aws.amazon.com/bedrock-agentcore](https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/registry.html) | AWS Agent Registry docs |
| InfoQ (AWS) | [infoq.com/2026/04/AWS-agent-registry](https://www.infoq.com/news/2026/04/aws-agent-registry-preview/) | AWS Agent Registry InfoQ coverage |
| The Register | [theregister.com/AWS-agent-registry](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/) | "Agents shouldn't be secret, so we built a registry" |
| SiliconAngle | [siliconangle.com/AWS-agent-registry](https://siliconangle.com/2026/04/09/aws-previews-cloud-agnostic-registry-managing-agentic-fleets-scale/) | Cloud-agnostic registry coverage |
| DEV Community | [dev.to/aws-builders](https://dev.to/aws-builders/aws-agent-registry-a-private-catalog-to-stop-agent-sprawl-c91) | "Agent Registry: stop agent sprawl" |
| Heeki Medium | [heeki.medium.com](https://heeki.medium.com/integrating-aws-agent-registry-into-your-agent-platform-for-discovery-and-governance-3350920204a4) | Integrating AWS Agent Registry |
| Classmethod | [dev.classmethod.jp](https://dev.classmethod.jp/en/articles/aws-agent-registry-preview/) | AWS Agent Registry update |
| Releasebot | [releasebot.io/claude-code](https://releasebot.io/updates/anthropic/claude-code) | Claude Code release history |
| Releasebot | [releasebot.io/anthropic](https://releasebot.io/updates/anthropic) | Anthropic release history |
| Releasebot | [releasebot.io/claude](https://releasebot.io/updates/anthropic/claude) | Claude release history |
| GitHub releases | [github.com/anthropics/claude-code/releases](https://github.com/anthropics/claude-code/releases) | Claude Code GitHub releases |
| Claude Help | [support.claude.com/release-notes](https://support.claude.com/en/articles/12138966-release-notes) | Official Claude release notes |
| Microsoft Docs | [learn.microsoft.com/mcp-tools](https://learn.microsoft.com/en-us/agent-framework/agents/tools/local-mcp-tools) | Microsoft MCP tools in Agent Framework |
| Toloka AI | [toloka.ai/mcp-servers](https://toloka.ai/blog/best-mcp-servers-for-ai-agents/) | Best MCP servers for AI agents 2026 |
| Firecrawl | [firecrawl.dev/mcp-servers](https://www.firecrawl.dev/blog/best-mcp-servers-for-developers) | 10 best MCP servers for developers |
| ByteBridge | [bytebridge.medium.com](https://bytebridge.medium.com/mcp-gateways-in-2026-top-10-tools-for-ai-agents-and-workflows-d98f54c3577a) | MCP gateways 2026 |
| SegmentStream | [segmentstream.com/mcp-marketers](https://segmentstream.com/blog/articles/best-mcp-servers-for-marketers) | MCP servers for marketers |
| K2View | [k2view.com/mcp-servers](https://www.k2view.com/blog/awesome-mcp-servers) | Awesome MCP servers 2026 |
| Composio | [composio.dev/youtube-mcp](https://composio.dev/toolkits/youtube/framework/claude-code) | YouTube MCP integration with Claude Code |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ inaccessible to crawler
├─ 🔵 X: 0 posts │ excluded per parameters
├─ 🔴 YouTube: 4 videos │ 0 views retrieved │ 0 with transcripts
├─ 🟢 HN: 8 stories │ 818+ points │ 430+ comments
├─ 🟣 TikTok: 0 videos
├─ 🩷 Instagram: 0 reels
├─ 🦋 Bluesky: 0 posts
├─ 📊 Polymarket: 0 markets
├─ 🌐 Web: 53 pages
└─ 🗣️ Top voices: simonw (HN/Willison), @philipnakhleh (Medium), @yonatan_arbel (JFrog) │ GitHub: jeremylongshore, alirezarezvani, anthropics
```

---

## Data Gaps

- **Reddit**: Domain inaccessible to the search crawler (HTTP 400 blocked). r/ClaudeAI, r/LocalLLaMA, r/MachineLearning likely have active discussions — 0% coverage.
- **X/Twitter**: Excluded per parameters. Active conversation likely around Willison's posts on Skills, AAIF announcements, Code with Claude SF.
- **TikTok/Instagram/Bluesky**: No results found; platform-level data gaps.
- **Polymarket**: No prediction markets identified on this topic.
- **YouTube**: 4 videos identified by title/URL but no view counts, like counts, or transcript data retrievable via search alone. Actual video catalog on this topic is certainly larger.
- **HN 429 rate limits**: Two threads (id 45619537 "bigger deal than MCP", id 45649295 "Skillz") returned 429 errors during fetch; engagement data for these is estimated/inferred.
- **Marketplace data freshness**: claudemarketplaces.com data is as of May 7, 2026; SkillsMP figure (66,541) is from January 2026. Live counts likely higher.
- **Estimated coverage**: ~65–70% of available developer discourse. Missing: Reddit (large gap), X/Twitter, TikTok, platform-internal discussions.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP." — Simon Willison, Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Skills are just a bunch of files with instructions — the context-efficient organization is the feature, not a breakthrough." — HN commenter ([link](https://news.ycombinator.com/item?id=45607117))

> "All these things are designed to create lock in." — HN commenter ([link](https://news.ycombinator.com/item?id=45607117))

> "Once you install and approve one, it can run real code on your machine. Attackers love that trust." — Philip Nakhleh, Medium ([link](https://medium.com/@philipnakhleh/the-hidden-dangers-of-claude-code-how-cyber-attackers-are-using-ai-skills-plugins-62fa891bfd30))

> "Without governance, scaling agents becomes exceedingly difficult, bordering on impossible." — Yonatan Arbel, JFrog ([link](https://jfrog.com/blog/agent-skills-new-ai-packages/))

> "None of these tools validate their own configuration files." — anotherCodder, Hacker News ([link](https://news.ycombinator.com/item?id=46983879))

> "AWS: Agents shouldn't be secret, so we built a registry." — The Register ([link](https://www.theregister.com/2026/04/09/aws_ai_agent_registry/))

> "If you are still relying on giant custom prompts pasted into every session, you are using 2025 tactics in a 2026 environment." — Developers Digest ([link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026))

> "Agent skills are becoming for artificial intelligence agents what GitHub is for code and Hugging Face is for machine learning models." — KDnuggets ([link](https://www.kdnuggets.com/top-5-agent-skill-marketplaces-for-building-powerful-ai-agents))

> "If you're building an MCP server or AI agent, you need to scrape each one individually." — DavidGraca, Hacker News ([link](https://news.ycombinator.com/item?id=46692865))
