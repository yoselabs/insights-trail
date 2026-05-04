# Agent Skills & Plugin Ecosystem — Daily Briefing
**Date:** 2026-05-04
**Query type:** GENERAL
**Sources:** Hacker News, Web, GitHub, YouTube, Polymarket

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Hacker News | 7 stories | ~880 points, ~40 comments | Key debates on Skills vs MCP |
| Web | 60+ pages | — | Blogs, news, docs, security reports |
| GitHub | 14+ repos | 20.1k+ stars (VoltAgent) | Skill collections and tooling |
| YouTube | 4 videos | 6M+ views (Remotion X demo) | Tutorials and demos |
| Polymarket | 11 markets | — | Claude-related prediction markets |

---

## Synthesized Findings

### 1. The Agent Skills Standard — Anthropic's Second Infrastructure Play

On December 18, 2025, Anthropic launched Agent Skills as an **open standard** at agentskills.io, completing a strategic one-two punch: MCP handles *what* agents can access (tools, APIs, databases), while Skills encode *how* agents should perform specific tasks. Three days earlier, on December 9, Anthropic had donated MCP governance to the Agent AI Foundation (AAIF) under the Linux Foundation, with $5M+ in annual member funding from Anthropic, OpenAI, Block, and others.

The core architecture of a Skill is deliberately minimal: a directory containing a `SKILL.md` file with YAML frontmatter (`name` and `description`). The spec is what Simon Willison called "a deliciously tiny specification" and also "quite heavily under-specified" — leaving room for platform-specific extension while ensuring portability. Progressive disclosure is the key engineering insight: Skills load only 30–50 tokens at startup (name + description), expanding to full content only when Claude determines relevance, enabling effectively unbounded bundled content without context bloat.

Partners at launch: Microsoft, OpenAI, Atlassian, Figma, Cursor, GitHub. OpenAI was conspicuously absent from initial promotion — they added Skills to Codex documentation and joined the homepage within 24 hours. By May 2026, 18 AI platforms support the open standard: Claude Code, Cursor, GitHub Copilot, Windsurf, Gemini CLI, Codex CLI, Cline, Roo, Amp, Kiro CLI, and more.

Sources: [Anthropic Engineering Blog](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) · [Simon Willison](https://simonwillison.net/2025/Dec/19/agent-skills/) · [The Decoder](https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/) · [VentureBeat](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) · [SiliconAngle](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/) · [AI Business](https://aibusiness.com/foundation-models/anthropic-launches-skills-open-standard-claude) · [PulseMCP](https://pulsemcp.com/posts/openai-agent-skills-anthropic-donates-mcp-gpt-5-2-image-1-5) · [Introducing Skills blog](https://claude.com/blog/skills) · [agentskills.io on MCP.io docs](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills)

---

### 2. The Skills vs. MCP Debate: HN's Central Argument

The Hacker News thread "Claude Skills are awesome, maybe a bigger deal than MCP" ([HN #45619537](https://news.ycombinator.com/item?id=45619537)) became one of the defining discussions of this period. Simon Willison's title framing sparked a heated debate across technical credibility vs. marketing narrative lines:

- **Skills' core advantage**: No running processes, no token-heavy API documentation frontloaded at startup. Skills load via progressive disclosure vs. MCP's potential 50k+ token consumption for full API schemas.
- **MCP's defenders**: tptacek (48 pts) argued "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones" — reframing the debate away from Skills/MCP as binary.
- **The skeptics**: pants2 called Skills primarily "a design pattern/prompt engineering technique rather than a hard specification, implementable within existing MCP frameworks."
- **The advocates**: pseudosavant drew the Docker analogy — conceptual simplicity doesn't diminish novelty or transformative potential.
- **Unexpected insight** (michael1999, substantial engagement): Developers now write better technical documentation because LLMs actually use it, unlike human readers who ignore docs — creating a strong feedback incentive loop.

Arize AI ran a rigorous evaluation ([MCP vs CLI Skills eval](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/)): correctness was nearly identical (LobeHub 0.826, Vault 0.833, MCP 0.834) — but **MCP cost 6x more and took 5x longer** on complex tasks. One representative task: MCP $2 / 71 calls / 8 min vs. Skills $0.19 / 7 calls / <1 min. The real conclusion: deploy both strategically. Use CLI/skills for local work with pre-configured auth; use MCP for remote, proprietary, consumer-facing apps requiring OAuth.

A critical finding buried in the evaluation: **bare Claude with no tooling matched skill performance for widely-known tools** (0.845 correctness), suggesting training data does much of the work for tools like `gh`. Skills matter most for proprietary tools absent from training data.

Sources: [HN #45619537](https://news.ycombinator.com/item?id=45619537) · [Arize AI eval](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/) · [morphllm guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [alexop.dev full stack](https://alexop.dev/posts/understanding-claude-code-full-stack/)

---

### 3. Ecosystem Scale — Plugins, Skills, and MCP Servers

The Claude Code ecosystem has reached extraordinary scale in under six months of public plugin availability:

| Metric | Count | Source |
|--------|-------|--------|
| Claude Code plugins (total) | 9,000+ (~100 prod-ready) | aitoolanalysis.com |
| Skills (claudemarketplaces.com) | 4,200+ | claudemarketplaces.com |
| MCP servers (PulseMCP) | 14,000+ daily-updated | pulsemcp.com |
| MCP servers (mcp.so) | 20,633 | mcp.so |
| MCP capabilities (Smithery) | 5,000+ | smithery.ai |
| awesome-agent-skills (GitHub stars) | 20.1k stars | VoltAgent/GitHub |
| Agent platforms supporting Skills | 18 | openaitoolshub.org |

The [VoltAgent/awesome-agent-skills](https://github.com/VoltAgent/awesome-agent-skills) repo (20.1k stars) is the primary community aggregation point, with 1,100+ skills marked "hand-picked, not AI-slop generated" from Anthropic (17), Microsoft (133), Google, Vercel, Cloudflare, Stripe, Figma, HuggingFace, Trail of Bits, Sentry, HashiCorp, and 50+ more organizations.

The [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) repo tracks 425 plugins, 2,810 skills, and 200 agents with the `ccpi` CLI package manager at tonsofskills.com. [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) claims 5,200+ stars and 232+ skills across 18 AI platforms.

Key platform developments:
- January 30, 2026: Anthropic launched 11 official plugins for Claude Cowork covering Legal, Sales, Marketing, Finance
- Claude Opus 4.7 (April 16, 2026): most capable Claude model, with new cybersecurity safeguards
- Official plugin marketplace: [claude.com/plugins](https://claude.com/plugins); [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
- Official MCP dev skill: `mcp-server-dev` plugin at [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/mcp-server-dev)

Sources: [claudemarketplaces.com](https://claudemarketplaces.com/) · [aitoolanalysis.com](https://aitoolanalysis.com/claude-code-plugins/) · [pulsemcp.com](https://www.pulsemcp.com/servers) · [mcp.so](https://mcp.so/) · [smithery.ai](https://smithery.ai/) · [VoltAgent GitHub](https://github.com/VoltAgent/awesome-agent-skills) · [alirezarezvani](https://github.com/alirezarezvani/claude-skills) · [claude.com/plugins](https://claude.com/plugins)

---

### 4. The Remotion Moment — Skills Go Viral

The single most viral moment for agent skills: On **January 20, 2026**, the Remotion team posted an X demo showing a complete animated video generated entirely from a text prompt via Claude Code and the Remotion skill. The post hit **6 million views in days**.

Results: 150,000 installs within 8 weeks, making Remotion #5 most-installed skill overall and #1 among non-platform creators. skills.sh (Vercel's directory) grew **18.5x in 20 days**, reaching 40,000+ skills by early February 2026.

Cross-platform adoption was balanced: Claude Code and Gemini CLI led at ~108K installs each, followed by Cursor/OpenCode/Codex at ~92-93K each, and Antigravity at 74.8K.

The incident surfaced a quality crisis: with the explosion to 40,000+ skills, analysis found **46.3% were duplicates and 9% carried security risks** — validating the argument that curated, maintained, expert-built skills will dominate long-term.

The skill itself turns complex React/TypeScript animation code into natural language prompts, creating a deterministic, version-controlled video production pipeline via git. Developers at [SkillsPlayground](https://skillsplayground.com/guides/claude-code-plugins/), [ngram.com](https://www.ngram.com/blog/remotion-skills-sh-ai-video-creation), [nemovideo.com](https://www.nemovideo.com/blog/remotion-agent-skills-claude-code-guide), and Medium covered the adoption story.

Sources: [ngram.com](https://www.ngram.com/blog/remotion-skills-sh-ai-video-creation) · [quickleap](https://quickleap.io/blog/remotion-claude-code-skill-review) · [startuphub.ai](https://www.startuphub.ai/ai-news/artificial-intelligence/2026/remotion-ai-video-makes-production-code-from-plain-prompts) · [dplooy](https://www.dplooy.com/blog/claude-code-video-with-remotion-best-motion-guide-2026) · [skills.sh review](https://vibecoding.app/blog/skills-sh-review)

---

### 5. Enterprise and Platform Adoption

**Microsoft** went deep on the Skills standard:
- [microsoft/skills](https://github.com/microsoft/skills): 132 skills with a Skills Explorer offering 1-click install; powers GitHub Copilot, Claude Code, and other agents
- [microsoft/azure-skills](https://github.com/microsoft/azure-skills): 25 curated Azure skills; Azure MCP Server provides 200+ structured tools across 40+ Azure services
- [microsoft/mcp](https://github.com/microsoft/mcp): official Microsoft MCP server catalog
- Context-driven development blog: [devblogs.microsoft.com](https://devblogs.microsoft.com/all-things-azure/context-driven-development-agent-skills-for-microsoft-foundry-and-azure/)

**AWS** launched Agent Registry (April 2026, preview): a private, governed catalog for agents, tools, skills, and MCP servers inside organizations. Features semantic + keyword search, IAM/OAuth authentication, CloudTrail audit trails. Available across 5 regions. [AWS announcement](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/)

**ToolHive (Stacklok)** introduced reusable agent skills across CLI and Registry (April 6, 2026): OCI artifact publishing, versioned skills with reverse-DNS namespace isolation, Registry Server for search/filter. "MCP servers give agents the raw tools; skills give them the knowledge of when, why, and how to use those tools." [Stacklok docs](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates)

**Plugin community tooling:**
- CCHub: Desktop app for managing MCP marketplace, config profiles, skills browser, workflow templates, security audit
- agr (`uvx agr add`): One-command GitHub skill installation with agr.toml dependency tracking ([HN #46685829](https://news.ycombinator.com/item?id=46685829))
- skillz CLI: Inject and sync skills across any model/agent (`skills init`, `skills sync`) ([HN #45948615](https://news.ycombinator.com/item?id=45948615))
- Noriskillsets.dev: Curated registry avoiding low-quality community skills ([HN #46721900](https://news.ycombinator.com/item?id=46721900))

Sources: [microsoft/skills](https://github.com/microsoft/skills) · [microsoft/azure-skills](https://github.com/microsoft/azure-skills) · [AWS registry](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) · [Stacklok](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) · [HN #46685829](https://news.ycombinator.com/item?id=46685829) · [HN #46721900](https://news.ycombinator.com/item?id=46721900)

---

### 6. Security — The Supply Chain Crisis

Security became the dominant unresolved problem by February 2026. Multiple concurrent incidents revealed systemic vulnerabilities:

**ToxicSkills (Snyk, February 5, 2026)**: Scan of 3,984 skills across ClawHub and skills.sh found:
- 76 confirmed malicious payloads (human-verified)
- 13.4% (534 skills) with at least one critical-level security issue
- 36.82% (1,467 skills) with any security flaw
- 91% of malicious skills employed prompt injection alongside traditional malware
- 10.9% of all ClawHub skills had hardcoded secrets; 32% of malicious ones
- 8 malicious skills remained publicly available at publication
- Root cause: publish barrier is one SKILL.md + one-week-old GitHub account; no code signing, no sandbox

The "lethal trifecta" (Simon Willison): AI agents simultaneously accessing private data + processing untrusted content + communicating externally = full system compromise via prompt injection.

**Claude Code CVEs**:
- CVE-2025-59536 (CVSS 8.7): RCE via `.claude/settings.json` and `.mcp.json` config injection — code could run before trust dialog accepted; patched in v2.0.65+
- CVE-2026-21852 (CVSS 5.3): API key theft via ANTHROPIC_BASE_URL redirect in attacker-controlled project

**MCP Infrastructure**:
- Trend Micro: 492 MCP servers exposed to internet with zero authentication
- BlueRock: 36.7% of 7,000+ analyzed MCP servers vulnerable to SSRF (demonstrated AWS credential theft from EC2 metadata)
- OX Security: architectural RCE vulnerability in MCP affecting 150M+ downloads; successful execution on six live production platforms including LiteLLM, LangChain, IBM LangFlow

**Scale of impact**:
- Pentagon designated Anthropic a "supply chain risk" in February 2026 — first time an American company received this classification
- Confirmed breach compromised Mexican government agencies: 150GB exfiltrated, 195M taxpayer records stolen via Claude-assisted social engineering
- March 31, 2026: Claude Code npm v2.1.88 accidentally included 59.8 MB source map exposing ~512K lines of TypeScript

Sources: [Snyk ToxicSkills](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) · [Snyk SKILL.md to shell](https://snyk.io/articles/skill-md-shell-access/) · [Snyk attack surface](https://snyk.io/articles/ai-skills-new-agentic-attack-surface/) · [Snyk clawdhub campaign](https://snyk.io/articles/clawdhub-malicious-campaign-ai-agent-skills/) · [cyberdesserts AI security](https://blog.cyberdesserts.com/ai-agent-security-risks/) · [OX Security MCP](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) · [Straiker source leak](https://www.straiker.ai/blog/claude-code-source-leak-with-great-agency-comes-great-responsibility) · [KiwiClaw](https://kiwiclaw.app/blog/clawhub-malicious-skills/) · [MCP security OWASP](https://mcpplaygroundonline.com/blog/mcp-security-tool-poisoning-owasp-top-10-mcp-scan)

---

### 7. Developer Workflows and Practical Insights

The community converged on four axioms (Developers Digest, [HN aggregate coverage](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026)):
1. **Workflows matter more than demos** — encoding repeatable, bounded workflows beats raw capability
2. **Verification is the bottleneck** — not generation
3. **Skills beat prompts** — pasting 200-word prompts every session is "2025 tactics"
4. **Orchestration matters more than raw autonomy** — multiple specialized instances > one general one

Practical skill design patterns from community practitioners:
- **Caveman skill**: reduces token usage ~75% by stripping verbose preambles; transforms "elaborate explanation" to "Done. Token validation updated."
- **Adversarial code review**: "actively tries to break your code" — catches issues human reviewers miss
- **Company CLI skills**: encoding proprietary tool knowledge transforms documentation-heavy workflows into natural language queries
- Best practice: 2-3 MCP servers (GitHub, Filesystem, domain-specific) + custom skills for org-specific workflows

The [Arize evaluation](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/) and [Developer community posts](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) show the biggest wins come from encoding **specific environments, team conventions, and company tools** rather than generic capabilities.

Sources: [Jonathan Fulton / Medium (Apr 2026)](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) · [Dean Blank / Level Up (Mar 2026)](https://levelup.gitconnected.com/a-mental-model-for-claude-code-skills-subagents-and-plugins-3dea9924bf05) · [Developers Digest](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) · [Composio top skills](https://composio.dev/content/top-claude-skills) · [morphllm guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) · [turbodocx](https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers)

---

### 8. Discovery and Distribution Infrastructure

**skills.sh (Vercel)**: Launched January 2026 alongside the Skills CLI. Open directory with install counts ranking ("Hot," "Trending," "Top"). Installation: `npx skills add <owner/repo>` — auto-detects agent and deploys to correct directory. Challenge: top positions dominated by Vercel/GitHub/Anthropic, not community; 80% of community skills rated low quality by developers; grew to 40,000+ skills in 20 days post-Remotion but with major duplication and quality problems.

**claudemarketplaces.com**: 4,200+ skills, 770+ MCP servers, 120,000+ monthly visitors — largest community aggregation point.

**Nori registry (noriskillsets.dev)**: Curated, hand-written skillsets; dedicated CLI; custom metadata filtering; explicitly positioned against "oversaturation of low-quality skill collections." ([HN #46721900](https://news.ycombinator.com/item?id=46721900))

**Plugin distribution challenges**: Plugin maintainers don't want to also build marketplaces — creating community-built alternatives like claudecodemarketplace.com and claudemarketplaces.com. The HN plugin discussion ([#45530150](https://news.ycombinator.com/item?id=45530150)) found SSH authentication errors in official docs; HTTPS URL format required.

Sources: [skills.sh review](https://vibecoding.app/blog/skills-sh-review) · [claudemarketplaces.com](https://claudemarketplaces.com/) · [HN #46721900](https://news.ycombinator.com/item?id=46721900) · [HN #45530150](https://news.ycombinator.com/item?id=45530150) · [HN #45544549](https://news.ycombinator.com/item?id=45544549) · [dynomapper MCP directories](https://dynomapper.com/blog/ai/mcp-server-directories/) · [apigene MCP marketplace guide](https://apigene.ai/blog/mcp-marketplace)

---

## Cross-Source Patterns

**Pattern 1: Standards-first strategy wins (Hacker News + Web + GitHub)**
Anthropic's playbook — release MCP → donate to foundation → release Skills → open-source the standard — has proven effective at achieving cross-platform adoption faster than proprietary alternatives. Both MCP and Agent Skills now have adoption from OpenAI, Microsoft, Google, and others. The governance donation to Linux Foundation removed the "Anthropic controls the standard" objection.

**Pattern 2: Quality vs. quantity crisis in marketplaces (Web + Security + GitHub)**
Every major directory surfaces the same problem: volume outpaced quality. skills.sh: 80% community skills low-quality. ToxicSkills: 36.82% have security flaws. claudemarketplaces.com: 9,000+ total plugins, ~100 production-ready. The market is bifurcating between trusted/curated collections (VoltAgent's "hand-picked, not AI-slop" approach; Nori's curated registry) and open, unverified directories with signal-to-noise problems.

**Pattern 3: The cost/latency argument drives skill adoption (Web + HN)**
Arize's numbers — MCP 6x cost, 5x slower on complex tasks — gave the Skills camp a compelling economic argument, not just a conceptual one. This appears across HN comments (context window efficiency), the MorphLLM guide, and Claude Code survival guides.

**Pattern 4: Proprietary tool knowledge is the real value (Web + HN + Medium)**
Multiple sources converge: skills beat bare Claude for proprietary/company-specific tools; encoding org-specific conventions into skills (company CLI, internal APIs, team workflows) is where transformative value emerges. Generic skills have low marginal value; organization-specific skills have high marginal value.

**Pattern 5: Security as existential risk (Security + HN + Web)**
The supply chain attack surface for agent skills is structurally worse than traditional software — skills operate with full agent permissions, combining AI safety risks (prompt injection) with traditional malware. The Snyk ToxicSkills research, OX Security MCP RCE, and government-level classification (Pentagon) all appeared within the same 2-month window, suggesting security will become a mandatory gating factor for enterprise skill adoption.

---

## Per-Platform Tables

**Hacker News:**

| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|---------------|-----|
| simonw | Claude Skills are awesome, maybe a bigger deal than MCP | ~816 pts | ~200 | "Claude Skills are awesome, maybe a bigger deal than MCP" | [link](https://news.ycombinator.com/item?id=45619537) |
| BrutalCoding | Customize Claude Code with plugins | 48 pts | ~30 | "plugin maintainers do not want to have to build a marketplace as well" | [link](https://news.ycombinator.com/item?id=45530150) |
| ritammehta | Show HN: A registry for curated, high quality Claude skills | 9 pts | 2 | "love nori!" | [link](https://news.ycombinator.com/item?id=46721900) |
| juunge | Show HN: NPM/uv for Claude Code – install skills from GitHub with one command | 1 pt | 1 | Security concern: "managing the permissions scope of 3rd party capabilities" | [link](https://news.ycombinator.com/item?id=46685829) |
| kevinslin | Show HN: Skillz – Use Claude Skills Anywhere | 2 pts | — | Plans for "public skills registry and usage tracking" | [link](https://news.ycombinator.com/item?id=45948615) |
| jungard | Claude Code Skills and Plugins as an Open Source Project | 2 pts | 1 | "reusable expertise bundles that transform AI coding agents into specialized professionals" | [link](https://news.ycombinator.com/item?id=47321892) |
| (anon) | Discover Claude Code Plugins and Marketplaces | — | — | Community-built distribution solving official gap | [link](https://news.ycombinator.com/item?id=45544549) |
| (anon) | Ask HN: Is there a market for a security-audited Claude Code skills newsletter? | — | — | Reflects emerging security awareness | [link](https://news.ycombinator.com/item?id=47333541) |
| (anon) | Claude Skills | — | — | Broader Claude Skills discussion | [link](https://news.ycombinator.com/item?id=45607117) |

**YouTube:**

| Channel | Title | Views | Likes | Transcript? | URL |
|---------|-------|-------|-------|-------------|-----|
| (unknown) | The Ultimate Claude Code Guide \| MCP, Skills & More | — | — | No | [link](https://www.youtube.com/watch?v=uogzSxOw4LU) |
| (unknown) | Top 10 Claude Code Skills, Plugins & CLIs (April 2026) | — | — | No | [link](https://www.youtube.com/watch?v=KjEFy5wjFQg) |
| (unknown) | My Claude Code System For Viral TikTok Videos | — | — | No | [link](https://www.youtube.com/watch?v=lw69SOTKRM4) |
| (unknown) | A Free Powerful WordPress MCP (Claude Code + Novamira) | — | — | No | [link](https://www.youtube.com/watch?v=vSgw2cJ8lIE) |

**Polymarket:**

| Market Title | Odds | Volume | URL |
|-------------|------|--------|-----|
| 11 active Claude-related markets | Various | — | [link](https://polymarket.com/predictions/claude) |
| Claude 4.7 released by...? | — | — | [link](https://polymarket.com/event/claude-4pt7-released-by) |
| Technology prediction markets 2026 | Various | — | [link](https://polymarket.com/tech) |

**Web:**

| Source | URL | Key Contribution |
|--------|-----|-----------------|
| Anthropic Engineering Blog | [link](https://www.anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills) | Three-level progressive disclosure architecture; Skill structure spec |
| Anthropic Official Blog | [link](https://claude.com/blog/skills) | Official launch: composable, portable, efficient, powerful |
| Simon Willison | [link](https://simonwillison.net/2025/Dec/19/agent-skills/) | "Deliciously tiny specification"; OpenAI adoption timeline |
| The Decoder | [link](https://the-decoder.com/anthropic-publishes-agent-skills-as-an-open-standard-for-ai-platforms/) | Enterprise management features; partner directory |
| VentureBeat | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Enterprise Agent Skills and open standard announcement |
| SiliconAngle | [link](https://siliconangle.com/2025/12/18/anthropic-makes-agent-skills-open-standard/) | Open standard announcement coverage |
| PulseMCP (OpenAI/MCP) | [link](https://pulsemcp.com/posts/openai-agent-skills-anthropic-donates-mcp-gpt-5-2-image-1-5) | OpenAI adoption + Anthropic MCP donation details |
| Arize AI | [link](https://arize.com/blog/mcp-vs-cli-skills-for-agents-what-our-eval-found-and-which-you-should-use/) | MCP 6x cost, 5x slower; both approaches needed |
| Snyk ToxicSkills | [link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | 36.82% of skills have security flaws; 76 confirmed malicious |
| Snyk SKILL.md to Shell | [link](https://snyk.io/articles/skill-md-shell-access/) | Attack vectors: 3 lines of markdown to shell access |
| Snyk attack surface | [link](https://snyk.io/articles/ai-skills-new-agentic-attack-surface/) | Skills as new agentic attack surface |
| Snyk clawdhub campaign | [link](https://snyk.io/articles/clawdhub-malicious-campaign-ai-agent-skills/) | 1,184 malicious skills drop reverse shells |
| cyberdesserts AI security | [link](https://blog.cyberdesserts.com/ai-agent-security-risks/) | CVE-2025-59536, ClawHavoc, Pentagon designation |
| OX Security MCP | [link](https://www.ox.security/blog/the-mother-of-all-ai-supply-chains-critical-systemic-vulnerability-at-the-core-of-the-mcp/) | Architectural RCE in MCP; 150M+ downloads affected |
| Straiker (source leak) | [link](https://www.straiker.ai/blog/claude-code-source-leak-with-great-agency-comes-great-responsibility) | 59.8 MB source map leak in npm v2.1.88 |
| ngram.com (Remotion) | [link](https://www.ngram.com/blog/remotion-skills-sh-ai-video-creation) | 150K installs in 8 weeks; 18.5x skills.sh growth |
| AWS Agent Registry | [link](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) | Enterprise-grade skill registry; 5-region preview |
| Stacklok/ToolHive | [link](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates) | OCI-based skill publishing; registry server |
| MCP.io Agent Skills docs | [link](https://modelcontextprotocol.io/docs/develop/build-with-agent-skills) | Official mcp-server-dev plugin; 4 deployment paths |
| MorphLLM guide | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Complete Skills vs MCP vs Plugins comparison |
| alexop.dev full stack | [link](https://alexop.dev/posts/understanding-claude-code-full-stack/) | Claude Code full stack architecture explained |
| KiwiClaw | [link](https://kiwiclaw.app/blog/clawhub-malicious-skills/) | 1,184 malicious skills explained |
| aitoolanalysis | [link](https://aitoolanalysis.com/claude-code-plugins/) | 9,000+ plugins; ecosystem overview |
| claudemarketplaces.com | [link](https://claudemarketplaces.com/) | 4,200+ skills, 770+ MCP servers, 120K monthly visitors |
| vibecoding.app (skills.sh) | [link](https://vibecoding.app/blog/skills-sh-review) | 80% low quality; Vercel-led but community fragmented |
| Jonathan Fulton / Medium | [link](https://medium.com/jonathans-musings/agent-skills-the-cheat-codes-for-claude-code-b8679f0c3c4d) | Caveman, adversarial review, company CLI skills; org-specific > generic |
| Developers Digest | [link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026) | Four truths HN keeps rediscovering |
| PulseMCP server directory | [link](https://www.pulsemcp.com/servers) | 14,000+ MCP servers daily updated |
| mcp.so | [link](https://mcp.so/) | 20,633 MCP servers |
| apigene MCP marketplace | [link](https://apigene.ai/blog/mcp-marketplace) | MCP marketplace comparison guide |
| VoltAgent/awesome-agent-skills | [link](https://github.com/VoltAgent/awesome-agent-skills) | 20.1k stars; 1,100+ curated skills from major orgs |
| microsoft/skills | [link](https://github.com/microsoft/skills) | 132 skills; 1-click install Skills Explorer |
| microsoft/azure-skills | [link](https://github.com/microsoft/azure-skills) | 25 Azure skills; 200+ tools across 40+ services |
| jeremylongshore plugins+skills | [link](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2,810 skills, 200 agents; ccpi CLI |
| alirezarezvani/claude-skills | [link](https://github.com/alirezarezvani/claude-skills) | 5,200+ stars; 232+ skills across 18 platforms |
| hesreallyhim/awesome-claude-code | [link](https://github.com/hesreallyhim/awesome-claude-code) | Skills, hooks, slash-commands, orchestrators |
| sickn33/antigravity-awesome-skills | [link](https://github.com/sickn33/antigravity-awesome-skills) | 1,400+ skills; installer CLI; bundles |
| snyk-labs/toxicskills-goof | [link](https://github.com/snyk-labs/toxicskills-goof) | ToxicSkills proof-of-concept repo |
| anthropics/claude-plugins-official | [link](https://github.com/anthropics/claude-plugins-official) | Official Anthropic plugin directory |
| Polymarket MCP Server | [link](https://github.com/caiovicentino/polymarket-mcp-server) | 45-tool AI trading platform for Polymarket |
| VILA-Lab/Dive-into-Claude-Code | [link](https://github.com/VILA-Lab/Dive-into-Claude-Code) | Systematic analysis of Claude Code for agent design |
| mukul975/cybersecurity-skills | [link](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) | 754 skills mapped to MITRE ATT&CK, NIST CSF 2.0 |
| claude-code-workflows | [link](https://github.com/shinpr/claude-code-workflows) | Production-ready workflows, specialized AI agents |
| YouTube MCP | [link](https://github.com/JCodesMore/youtube-mcp) | Claude Code plugin for YouTube research |
| Composio TikTok MCP | [link](https://composio.dev/toolkits/tiktok/framework/claude-code) | TikTok MCP integration with Claude Code |
| Snyk top Claude skills | [link](https://snyk.io/articles/top-claude-skills-developers/) | Top 8 Claude skills for developers |
| Medium - 10 must-have skills | [link](https://medium.com/@unicodeveloper/10-must-have-skills-for-claude-and-any-coding-agent-in-2026-b5451b013051) | 10 must-have Claude/agent skills for 2026 |
| Anthropic Academy | [link](https://pasqualepillitteri.it/en/news/371/anthropic-academy-free-courses-claude) | 13 free courses on Claude Code, API, MCP, Agent Skills |
| Claude Code Docs (MCP) | [link](https://code.claude.com/docs/en/mcp) | Official MCP documentation |
| Claude Code Docs (plugins) | [link](https://code.claude.com/docs/en/plugins) | Official plugin creation documentation |
| Claude Code Docs (skills) | [link](https://code.claude.com/docs/en/skills) | Official skills documentation |
| Claude Code Docs (sub-agents) | [link](https://code.claude.com/docs/en/sub-agents) | Official subagent documentation |
| digitalapplied AI marketplaces | [link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | AI agent marketplace landscape 2026 |

---

## Stats Block

```
├─ 🟠 Reddit: 0 threads │ — │ — (blocked by search restriction)
├─ 🔵 X/Twitter: N/A (not directly crawlable; Remotion demo: 6M views)
├─ 🔴 YouTube: 4 videos │ views N/A (YouTube blocked JS rendering) │ 0 with transcripts
├─ 🟢 HN: 9 stories │ ~880+ points │ ~275+ comments
├─ 🟣 TikTok: N/A
├─ 🩷 Instagram: N/A
├─ 🦋 Bluesky: N/A
├─ 📊 Polymarket: 11 Claude markets │ Volume N/A
├─ 🌐 Web: 60+ pages
└─ 🗣️ Top voices: simonw (816 pts HN), tptacek (HN security), joesaunderson (marketplace builder) │ r/ClaudeAI (not directly accessed)
```

---

## Data Gaps

- **Reddit**: Reddit is not directly crawlable by the search tools (blocked user agent per Anthropic search policy). All Reddit data would require the /last30days skill's ScrapeCreators integration. Estimated coverage loss: ~20-30% of developer discussion volume.
- **X/Twitter**: Not directly accessible. Known data: Remotion demo hit 6M views on X in January 2026. Other X discussion (replies, threads from @simonw, @anthropic, etc.) not captured. Estimated loss: ~30% of real-time developer sentiment.
- **TikTok/Instagram**: No meaningful technical content found for this topic; general AI coding content may exist but not relevant to agent skills specifically.
- **Bluesky**: Search returned no direct Bluesky posts; the Bluesky integration for Claude Code is itself a skill example but not a discussion source.
- **YouTube view/like counts**: YouTube page rendering blocked JavaScript-dependent view counts. Video existence confirmed but engagement metrics unavailable.
- **Polymarket volumes**: Market volumes not extracted; exists as a surface but not the primary discussion venue for this topic.
- **Noise**: The Web results contained substantial SEO-optimized content (listicles like "7 Best Claude Code Plugins," "50+ Best MCP Servers") — treated as ecosystem signals but not primary sources.
- **Approximate coverage**: ~65-70% of total relevant discourse captured. Missing: Reddit developer threads (high signal), X conversations, internal Slack/Discord communities.

---

## Key Quotes

> "Claude Skills are awesome, maybe a bigger deal than MCP" — @simonw on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "Tool calls are incredibly interesting and useful. MCP is just one means to that end, and not one of the better ones." — @tptacek on Hacker News ([link](https://news.ycombinator.com/item?id=45619537))

> "A deliciously tiny specification — but also quite heavily under-specified." — Simon Willison on Agent Skills ([link](https://simonwillison.net/2025/Dec/19/agent-skills/))

> "MCP servers give agents the raw tools they can call; skills give them the knowledge of when, why, and how to use those tools effectively." — ToolHive/Stacklok ([link](https://docs.stacklok.com/toolhive/updates/2026/04/06/updates))

> "Agent Skills operate with the full permissions of the AI agent they extend — including shell access, file system permissions, credential access, and persistent memory modification." — Snyk ToxicSkills ([link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/))

> "The barrier to publishing a new agent skill on ClawHub is only a SKILL.md Markdown file and a GitHub account that's one week old. No code signing. No security review. No sandbox by default." — Snyk ([link](https://snyk.io/articles/skill-md-shell-access/))

> "plugin maintainers do not want to have to build a marketplace as well." — @joesaunderson on Hacker News ([link](https://news.ycombinator.com/item?id=45530150))

> "Relying on giant custom prompts pasted into every session is 2025 tactics. Encode repeatable workflows as skills." — Developer community consensus ([link](https://www.developersdigest.tech/blog/what-hacker-news-gets-right-about-ai-coding-agents-2026))

> "What once took a day, we now accomplish in an hour." — Rakuten on Agent Skills ([link](https://claude.com/blog/skills))

> "The skills.sh directory grew 18.5x to 40,000+ skills in its first 20 days [post-Remotion launch] — but 46.3% were duplicates and 9% carried security risks." — ngram.com ([link](https://www.ngram.com/blog/remotion-skills-sh-ai-video-creation))
