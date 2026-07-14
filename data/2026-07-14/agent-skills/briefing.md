# Claude Code Skills, Plugins & Agent Skill Ecosystems — Daily Briefing
**Date:** 2026-07-14
**Query type:** GENERAL
**Sources:** Reddit, X/Twitter, Hacker News, Bluesky, GitHub, Web (global), Web (Japan), Web (China)

---

## Source Inventory

| Source | Items | Engagement | Notes |
|--------|-------|------------|-------|
| Reddit | 9 threads | 2,031 upvotes, 728 comments | 🌐 partial — backup rate-limited |
| X/Twitter | 67 posts (EN) + 58 posts (JA) + 34 posts (ZH) | 3,515 + 1,083 + 559 likes | 🌐🇯🇵🇨🇳 |
| Hacker News | 23 stories (EN) + 9 stories (JA) + 2 stories (ZH) | 5,297 + 99 + 91 pts | 🌐🇯🇵🇨🇳 |
| Bluesky | 12 posts (EN) + 3 posts (JA) | 46 + 2 likes | 🌐🇯🇵 |
| GitHub | 4 items (EN) + 8 items (JA) + 6 items (ZH) | — | 🌐🇯🇵🇨🇳 |
| Web (global) | 27 pages | — | 🌐 via WebSearch + native search |
| Web (Japan) | 10 pages | — | 🇯🇵 Qiita, Zenn, note |
| Web (China) | 5 pages | — | 🇨🇳 CSDN, Zhihu, Juejin |

---

## Synthesized Findings

### 1. The Plugin/Skill/MCP Ecosystem Has Exploded in Scale

The numbers are staggering and arrived largely in the last six months. The community-maintained [`claude-code-plugins-plus-skills`](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) repo lists 425 plugins, 2,810 skills, and 200 agents, browsable at [tonsofskills.com](https://tonsofskills.com/) and installable via the `ccpi` CLI (`pnpm add -g @intentsolutionsio/ccpi`). Anthropic's own [claude-plugins-official](https://github.com/anthropics/claude-plugins-official) curates 55+ high-quality plugins. Community directories like [claudemarketplaces.com](https://claudemarketplaces.com/) index 425 packages with a weekly quality grade (Grade A as of July 10, 2026). The MCP layer is even larger - estimates range from [9,400 distinct servers by mid-April 2026](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/) growing +38% in four months, to Glama alone indexing close to 20,000 servers.

The taxonomy that has crystallized across all communities: **skills are markdown instruction files** (teaching Claude Code specific behaviors), **plugins are versioned bundles** (shipping skills + hooks + MCP definitions + slash commands together as a distributable package), and **MCP servers are integration bridges** (connecting external apps like databases, Figma, GitHub, deployment pipelines). As one widely-shared [morphllm.com guide](https://www.morphllm.com/claude-code-skills-mcp-plugins) puts it: "A skill is a cheat sheet, a plugin is a toolkit, and an MCP server is a bridge to another application."

One r/AppBusiness [thread](https://www.reddit.com/r/AppBusiness/comments/1usio9p/my_ios_app_is_4_months_old_and_does_944_mrr_every/) exemplifies practical adoption: "My iOS app is 4 months old and does $944 MRR. Every 'department' is a Claude Code skill." The author treats customer support, analytics, and marketing as separate Claude Code skills, each with domain-specific instructions and tool access.

### 2. Agent Skills Is Becoming a Cross-Platform Open Standard

The most structurally significant development of the month: **Agent Skills has emerged as a vendor-neutral open standard**, not just an Anthropic-owned format. The GitHub trending bot on Bluesky flagged `google-labs-code/stitch-skills` (["Google Stitch向けのエージェントスキルとプラグインのコレクション。Agent Skills オープン標準に準拠"](https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mqem2w2ssw22) - "A collection of agent skills and plugins for Google Stitch. Compliant with the Agent Skills open standard, aimed at use in coding agents such as Codex, Claude Code, Cursor, and Gemini CLI"). 🇯🇵

[VentureBeat reported](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) Anthropic's formal launch of enterprise "Agent Skills" alongside opening the standard. [The New Stack called it](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) "Anthropic's Next Bid to Define AI Standards."

The biggest single move: [Vercel's skills.sh went GA on June 5, 2026](https://www.totalum.app/blog/agent-skills-marketplaces-2026) with 600,000 OSS skills distributed via Vercel OIDC. skills.sh's core differentiator is a single CLI installer that works across Claude Code, Codex CLI, Cursor, and OpenClaw - positioning Vercel as the cross-platform distribution layer while Anthropic, OpenAI, and Cline remain host-specific publishers.

Anthropic donated MCP to the **Linux Foundation / Agentic AI Foundation** in December 2025, making it a vendor-neutral community-governed standard. Per [WorkOS](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026), six canonical host surfaces now speak native MCP: Claude Desktop, Claude Code, Cursor, Codex CLI, Windsurf, and VS Code with GitHub Copilot agent mode.

### 3. Security Is the New Dominant Concern - and It's Serious

This theme crossed from niche concern to mainstream alarm in June-July 2026, driven by concrete audit findings.

[Snyk's ToxicSkills study](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) - a scan of 3,984 skills from ClawHub and skills.sh - found **13.4% contain critical-level security issues** including credential theft, backdoor installation, and data exfiltration. A broader analysis of 42,447 skills found 26.1% carry at least one vulnerability. 280+ skills were documented leaking API keys through over-permissioned file and network access.

The [Cloud Security Alliance's June 25 post](https://cloudsecurityalliance.org/blog/2026/06/25/5-claude-agent-skills-risks-every-ciso-should-know) identified the structural root cause: "skills run with host-level access rather than inside sandboxes." In February 2026, researchers documented the first coordinated malware campaign targeting Claude Code and OpenClaw users, using 30+ malicious skills distributed via ClawHub. **OWASP formalized risks into the Agentic Skills Top 10 (AST10)** in March 2026.

[@RohanArun on X](https://x.com/RohanArun/status/2075774470330212782) surfaced the community's hunger for tooling to address this: "@crptAtlas Hey Super, build a website that audits Claude Code extensions. Let users choose project type, compare hooks, skills, MCP servers, subagents, and commands, run a scan, and review risks before enabling tools." The [Skill Security Auditor plugin](https://www.claudedirectory.org/skills/claude-skills-skill-security-auditor) from [Trail of Bits](https://github.com/trailofbits/skills) addresses exactly this gap - auditing skill directories and git repo URLs for malicious code as a pre-install gate.

### 4. Discovery and Distribution Remain Fragmented - but Tools Are Emerging

[@lukashanren1 on X](https://x.com/lukashanren1/status/2071900526564831679) captured the core problem: "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code - unless you use MCP. Here's how to plug them all in without touching the core. The extensibility problem: Building every integration directly into Claude Code would be impossible to maintain, a security nightmare, and inflexible for organizations with internal tools."

The registry landscape remains fragmented: Smithery has 7,000+ servers, the official MCP Registry ~800, and Glama ~20,000. [Per truefoundry](https://www.truefoundry.com/blog/best-mcp-registries), "there is no authoritative central registry yet" and the hard problem is "knowing which are real, maintained, and safe to hand credentials to."

The `ccpi` package manager on tonsofskills.com is the closest to a unified CLI layer - `ccpi search devops`, `ccpi install devops-automation-pack`, `ccpi update`. One [Bluesky thread](https://bsky.app/profile/acedatacloud.bsky.social/post/3mqict4biat2c) promoted the Nano Banana MCP as the integration model: "Generate/edit images, try product shots, or mock creative assets from Claude, VS Code, or Cursor. One API token, free credits, no context switching."

A key technical fix landed in early 2026: **MCP lazy loading reduces context usage by up to 95%** per [clarista.io](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) - skills and MCP servers only load when needed, not all at once. This addressed a major pain point where heavy MCP configurations degraded Claude Code's ability to handle complex tasks.

### 5. Anthropic's Official Tooling for Managing the Ecosystem

The `claude-code-setup` official plugin generated the most engagement in the Japanese community this month. [@kingdom314159 on X](https://x.com/kingdom314159/status/2070295299856502860) [🇯🇵] described it:

> "Anthropicが、公式プラグイン 'claude-code-setup' をひっそり公開しました。このプラグインは、プロジェクト全体をスキャンして、フック、スキル、MCPサーバー、サブエージェント、自動化設定まで、必要な構成を提案してくれます。" ("Anthropic quietly released the official plugin 'claude-code-setup.' This plugin scans the entire project and suggests the necessary configuration including hooks, skills, MCP servers, subagents, and automation settings.")

The plugin operates read-only (no automatic file rewriting), which [@engineer_num1](https://x.com/engineer_num1/status/2076794618516238490) called out as a key trust feature: "Claude Codeの強さは、モデル..." ("Claude Code's strength lies not in the model alone...").

Also new: `/checkup` (alias `/doctor`). [@oikon48's tweet](https://x.com/oikon48/status/2075042015092559907) got 227 likes [🇯🇵] explaining the feature: (1) clean up unused skills/MCP/plugins to save context, (2) deduplicate CLAUDE.md, (3) split root CLAUDE.md into nested CLAUDE.md + skills, (4) disable slow hooks, (5) update Claude Code, (6) enable auto mode by default, (7) pre-approve frequently-rejected read-only commands. The feature uses `AskUserQuestion` interactively rather than silently mutating files.

Anthropic's admin analytics dashboard now shows usage and cost by group and by user, with output like artifacts created, files edited, skills and connectors used, displayed next to their cost - per [marktechpost.com](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/). Enterprise MCP connector access started with Okta, enabling zero-touch provisioning.

### 6. Japan: Practical Guides and Memory Solutions Dominate 🇯🇵

The Japanese community on Qiita, Zenn, and note is producing the most detailed practical guides in the ecosystem. Key pieces this month:

- [Zenn (@ino_h)](https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking): "Claude Codeプラグインおすすめ2026 — 公式マーケットプレイスから入れるべきプラグイン & MCPサーバー" (recommended plugins from the official marketplace)
- [Qiita (@shatolin)](https://qiita.com/shatolin/items/ca1810e419fee5fd963b): "【2026年版】Claude Codeを最強にするプラグイン・MCP・ツール総まとめ" (total guide to making Claude Code the strongest)
- [Qiita (@kai_kou)](https://qiita.com/kai_kou/items/71ee39f27fc09d451cf8): Complete guide for sharing Skills, Hooks, and MCPs as team plugins
- [Qiita (@kamome_susume)](https://qiita.com/kamome_susume/items/33a34935707d2be1361a): Recommended MCP server list for Claude Code
- [Zenn (@goyle0)](https://zenn.dev/goyle0/articles/claude-code-mcp-plugins): CLI-recommended MCP plugins with focus on hallucination prevention
- [Zenn (@chmod644)](https://zenn.dev/chmod644/articles/claude-code-official-plugins-guide): Complete explanation of all 59 official Claude Code plugins
- [note (@ai_jissennkai)](https://note.com/ai_jissennkai/n/nc9ebedadd1f2): What is Claude Code MCP? Configuration methods and 5 real-world servers

**Key JP finding:** "Context loss between sessions" is the #1 pain point. As of 2026, memory-related plugins have gained significant popularity. The official plugin directory had 160 plugins with 32 from Anthropic as of April 2026.

The [@ai_hakase_ Hermes vs Claude Code thread](https://x.com/ai_hakase_/status/2074418416367087689) [🇯🇵, 5 likes] articulated the design philosophy debate: Hermes (universal agent runtime) can run many MCP servers and plugins but suffers from context bloat and precision degradation with small models; Claude Code (specialized CLI) maintains tight tool-use discipline but has narrower scope. This is the central tradeoff the ecosystem is navigating.

### 7. China: Competitive Intelligence and GitHub Trending Watch 🇨🇳

Chinese tech communities are tracking the Claude Code vs Codex competitive battle closely. [@yupi996](https://x.com/yupi996/status/2076484625959092453) [🇨🇳, 56 likes, 42 replies] reported: "Codex杀疯了，移除了5小时使用限制！... 另一边，Claude Fable 5 又延期了" ("Codex went wild, removed the 5-hour usage limit! ... On the other side, Claude Fable 5 was delayed again.") The OpenAI move and Fable 5 delays generated significant discussion.

A GitHub AI CLI tools daily digest ([zx0828/big_model_radar](https://github.com/zx0828/big_model_radar/issues/242)) [🇨🇳] covering July 12 tracked: Claude Code, OpenAI Codex, Gemini CLI, GitHub Copilot CLI - showing China's developer community treats these as a competitive category. Another digest ([loxehate/loxehate.github.io](https://github.com/loxehate/loxehate.github.io/issues/10)) [🇨🇳] from July 6 noted: "GitHub Trending榜被Claude Code / Codex相关技能、插件和Agent管理工具占据" ("GitHub Trending dominated by Claude Code/Codex related skills, plugins, and agent management tools").

Key CN hub content:
- [掘金 (Juejin)](https://juejin.cn/post/7633351194199244819): "卸掉那些没用的插件！Claude Code生态祛魅完全指南（2026最新）" ("Remove those useless plugins! Complete demystification guide for the Claude Code ecosystem 2026") - memory-type plugins like claude-mem, mcp-memory-keeper
- [CSDN](https://blog.csdn.net/weixin_46984554/article/details/160860809): "Claude Code十大必装MCP排行榜（2026年最新版）" ("Top 10 Must-Install MCPs for Claude Code 2026") - MCP ecosystem has 1000+ servers; 7 plugin categories covering docs, UI design, frontend dev, Chinese writing
- [知乎 (Zhihu)](https://zhuanlan.zhihu.com/p/1971872808159141982): Detailed Claude Code MCP command reference (add, delete, list, test)
- [CSDN tutorial](https://blog.csdn.net/champaignwolf/article/details/160913544): Claude Code + MCP hands-on tutorial

The "Making of Claude Code" [HN thread](https://www.anthropic.com/features/making-of-claude-code) (61pts, 31 comments) and a [transcript deletion bug report](https://github.com/anthropics/claude-code/issues/62476) (30pts, 37 comments: "Beware, Claude Code deletes >30 day old transcripts. Anthropic won't fix it") both generated CN-adjacent discussion.

### 8. MCP Security Deep Dives Continue

[@bilaltariq01 on Bluesky](https://bsky.app/profile/bilaltariq01.bsky.social/post/3mqjerirnt42a) shared a "Claude Code, Beyond the Prompt - Hardening an MCP Database Tool (Part 4 Deep Dive)" series, illustrating that security hardening of MCP connections is now a multi-part content genre. [Checkmarx](https://checkmarx.com/learn/ai-security/claude-code-security-top-6-risks-controls-and-best-practices/) published "Claude Code Security: Top 6 Risks, Controls, and Best Practices" and [Harmonic Security](https://www.harmonic.security/resources/security-lessons-from-claude-codes-first-year) released "Security Lessons from Claude Code's First Year."

---

## Cross-Source Patterns

**Pattern 1: Plugin sprawl creates management overhead** - Appeared on X (EN/JA), Reddit, Bluesky, Web. The /checkup feature, claude-code-setup plugin, and MCP lazy loading all address the same symptom: too many capabilities loaded, degrading performance. [@oikon48's /checkup announcement](https://x.com/oikon48/status/2075042015092559907) got 227 likes in Japan. r/AppBusiness's $944 MRR thread shows the flip side: purposeful skill design creates leverage.

**Pattern 2: Security is now a shipping concern, not a research one** - Appeared on X, HN, Web, CN GitHub digests. Snyk's ToxicSkills study, OWASP AST10, Checkmarx guides, and Trail of Bits' auditor skill all landed within the last 30 days. @RohanArun's call for an extension auditor got cross-platform traction.

**Pattern 3: Cross-platform standardization via Agent Skills** - Appeared on Bluesky (JA), Web, X. google-labs-code/stitch-skills, Vercel skills.sh, and VentureBeat's coverage all point to skills becoming a vendor-neutral format like npm packages. Vercel's 600K-skill launch is the clearest evidence.

**Pattern 4: Memory/context persistence is the #1 Japanese use case** - Appeared on Zenn, Qiita, note (JP), X (JP). The "context loss between sessions" problem drives plugin selection in Japan more than any other factor; memory plugins (claude-mem, mcp-memory-keeper) are the top-recommended category.

**Pattern 5: China tracks Codex vs Claude Code as a competition** - Appeared on X (ZH), GitHub (ZH). Chinese developers treat these as competing products; Codex's removal of usage limits generated as much discussion as Claude Code plugin news.

---

## Per-Platform Tables

**Reddit:** 🌐
| Subreddit | Title | Upvotes | Comments | Top Quote | URL |
|-----------|-------|---------|----------|-----------|-----|
| r/AppBusiness | My iOS app is 4 months old and does $944 MRR. Every "department" is a Claude Code skill | 152 | 48 | "Every 'department' is a Claude Code skill. Full stack with the actual workflows and costs" | [link](https://www.reddit.com/r/AppBusiness/comments/1usio9p/my_ios_app_is_4_months_old_and_does_944_mrr_every/) |

**X/Twitter:** 🌐🇯🇵🇨🇳
| Handle | Text Snippet | Likes | Reposts | URL |
|--------|-------------|-------|---------|-----|
| @RohanArun | "@crptAtlas Hey Super, build a website that audits Claude Code extensions..." | — | — | [link](https://x.com/RohanArun/status/2075774470330212782) |
| @lukashanren1 | "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code — unless you use MCP..." | 3 | 3 | [link](https://x.com/lukashanren1/status/2071900526564831679) |
| @AnthropicAI | "The values Claude expresses also vary with the language of the conversation..." | 315 | 23 | [link](https://x.com/AnthropicAI/status/2076719546954825769) |
| @oikon48 🇯🇵 | "Claude Code の新機能 /checkup (=/doctor)...未使用のスキル/MCP/プラグインをクリーンアップ..." | 227 | 28 | [link](https://x.com/oikon48/status/2075042015092559907) |
| @kingdom314159 🇯🇵 | "Anthropicが、公式プラグイン 'claude-code-setup' をひっそり公開しました..." | 13 | 1 | [link](https://x.com/kingdom314159/status/2070295299856502860) |
| @ai_hakase_ 🇯🇵 | "Hermes vs Claude Code！コード生成エージェントの設計思想と最適化戦略..." | 5 | 2 | [link](https://x.com/ai_hakase_/status/2074418416367087689) |
| @yupi996 🇨🇳 | "刚刚 Codex 杀疯了，移除了5小时使用限制！另一边，Claude Fable 5 又延期了" | 56 | 4 | [link](https://x.com/yupi996/status/2076484625959092453) |

**Hacker News:** 🌐🇯🇵🇨🇳
| User | Title | Points | Comments | Notable Quote | URL |
|------|-------|--------|----------|--------------|-----|
| (HN) | The Making of Claude Code | 61 | 31 | — | [link](https://www.anthropic.com/features/making-of-claude-code) |
| (HN) | Beware, Claude Code deletes >30 day old transcripts. Anthropic won't fix it | 30 | 37 | "Beware, Claude Code deletes >30 day old transcripts. Anthropic won't fix it" | [link](https://github.com/anthropics/claude-code/issues/62476) |

**Bluesky:** 🌐🇯🇵
| Handle | Text | Likes | URL |
|--------|------|-------|-----|
| @acedatacloud.bsky.social | "Nano Banana + MCP = image tools inside your IDE. Generate/edit images, try product shots..." | 7 | [link](https://bsky.app/profile/acedatacloud.bsky.social/post/3mqict4biat2c) |
| @acedatacloud.bsky.social | "Claude Code can edit images from your terminal. Add NanoBanana MCP..." | 7 | [link](https://bsky.app/profile/acedatacloud.bsky.social/post/3mqdzdfv4wr26) |
| @acedatacloud.bsky.social | "Claude Code doesn't have to live in one IDE. Use it from VS Code, Cursor, terminal, or GitHub Actions..." | 5 | [link](https://bsky.app/profile/acedatacloud.bsky.social/post/3mqexjhqhjx2w) |
| @bilaltariq01.bsky.social | "Claude Code, Beyond the Prompt — Hardening an MCP Database Tool (Part 4 Deep Dive)" | 4 | [link](https://bsky.app/profile/bilaltariq01.bsky.social/post/3mqjerirnt42a) |
| @dailygithubtrends.bsky.social 🇯🇵 | "今日のGitHubトレンド: google-labs-code/stitch-skills...Agent Skills オープン標準に準拠" | 1 | [link](https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mqem2w2ssw22) |

**GitHub:** 🌐🇯🇵🇨🇳
| Region | Repo | Key Contribution |
|--------|------|-----------------|
| 🌐 | [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Official Anthropic directory, 55+ curated plugins |
| 🌐 | [jeremylongshore/claude-code-plugins-plus-skills](https://github.com/jeremylongshore/claude-code-plugins-plus-skills) | 425 plugins, 2810 skills; ccpi CLI |
| 🌐 | [cased/claude-code-plugins](https://github.com/cased/claude-code-plugins) | Community marketplace |
| 🌐 | [trailofbits/skills](https://github.com/trailofbits/skills) | Security research/audit skills |
| 🌐 | [netresearch/security-audit-skill](https://github.com/netresearch/security-audit-skill) | PHP security audit skill |
| 🌐 | [skillmatic-ai/awesome-agent-skills](https://github.com/skillmatic-ai/awesome-agent-skills) | Definitive resource for Agent Skills |
| 🌐 | [google-labs-code/stitch-skills](https://github.com/google-labs-code/stitch-skills) | Google's Agent Skills open standard implementation |
| 🇨🇳 | [zx0828/big_model_radar](https://github.com/zx0828/big_model_radar) | AI CLI tools community digest; tracks Claude Code, Codex, Gemini CLI |
| 🇨🇳 | [loxehate/loxehate.github.io](https://github.com/loxehate/loxehate.github.io) | AI open source trends daily digest (CN) |

**Web:**
| Region | Source | URL | Key Contribution |
|--------|--------|-----|-----------------|
| 🌐 | morphllm.com | [link](https://www.morphllm.com/claude-code-skills-mcp-plugins) | Definitive taxonomy: skill vs plugin vs MCP |
| 🌐 | tonsofskills.com | [link](https://tonsofskills.com/) | 3,050+ skills, 463 plugins catalog; ccpi hub |
| 🌐 | claudemarketplaces.com | [link](https://claudemarketplaces.com/) | 425 packages, weekly quality grade |
| 🌐 | claudemarketplace.net | [link](https://www.claudemarketplace.net/) | Community-curated; 150+ skills with ratings |
| 🌐 | codeongrass.com | [link](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/) | MCP ecosystem: 9,400+ servers, +38% in 4 months |
| 🌐 | truefoundry.com | [link](https://www.truefoundry.com/blog/best-mcp-registries) | Registry comparison: Smithery 7K+, no central authority |
| 🌐 | snyk.io | [link](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/) | ToxicSkills: 13.4% critical issues; first malware campaign |
| 🌐 | cloudsecurityalliance.org | [link](https://cloudsecurityalliance.org/blog/2026/06/25/5-claude-agent-skills-risks-every-ciso-should-know) | CISO risks; OWASP AST10; host-level access problem |
| 🌐 | totalum.app | [link](https://www.totalum.app/blog/agent-skills-marketplaces-2026) | 5-way marketplace comparison; Vercel skills.sh 600K skills |
| 🌐 | venturebeat.com | [link](https://venturebeat.com/technology/anthropic-launches-enterprise-agent-skills-and-opens-the-standard) | Anthropic launches + opens Agent Skills standard |
| 🌐 | thenewstack.io | [link](https://thenewstack.io/agent-skills-anthropics-next-bid-to-define-ai-standards/) | Agent Skills: Anthropic's standards play |
| 🌐 | workos.com | [link](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026) | Enterprise MCP; Okta connector; 6 canonical hosts |
| 🌐 | clarista.io | [link](https://www.clarista.io/blog/claude-code-mcp-plugins-guide) | MCP lazy loading: 95% context reduction |
| 🌐 | claudedirectory.org | [link](https://www.claudedirectory.org/skills/claude-skills-skill-security-auditor) | Skill Security Auditor plugin |
| 🌐 | marktechpost.com | [link](https://www.marktechpost.com/2026/06/14/claude-code-guide-2026-25-features-with-examples-demo/) | Admin analytics dashboard; cost tracking per skill |
| 🌐 | releasebot.io | [link](https://releasebot.io/updates/anthropic/claude-code) | July 2026 changelog: MCP OAuth fixes, plugin dependency fixes |
| 🌐 | dev.to | [link](https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4) | Best skills/plugins guide; ecosystem size estimates |
| 🌐 | medium.com | [link](https://medium.com/@reliabledataengineering/the-claude-code-plugin-stack-that-actually-makes-you-ship-faster-ec4bd90b14d3) | Plugin stack for shipping faster |
| 🌐 | agensi.io | [link](https://www.agensi.io/learn/best-ai-agent-skills-marketplaces-2026) | 7 AI Agent Skills Marketplaces compared |
| 🌐 | digitalapplied.com | [link](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) | Discovery and distribution analysis |
| 🌐 | groundy.com | [link](https://groundy.com/articles/claude-code-plugins-anthropic-s-official-plugin-ecosystem/) | Linux Foundation donation; MCP governance |
| 🌐 | checkmarx.com | [link](https://checkmarx.com/learn/ai-security/claude-code-security-top-6-risks-controls-and-best-practices/) | Top 6 Claude Code security risks |
| 🌐 | harmonic.security | [link](https://www.harmonic.security/resources/security-lessons-from-claude-codes-first-year) | Security lessons from first year |
| 🇯🇵 | zenn.dev (@ino_h) | [link](https://zenn.dev/ino_h/articles/2026-04-23-claude-code-plugins-ranking) | Plugin/MCP ranking from official marketplace |
| 🇯🇵 | qiita.com (@shatolin) | [link](https://qiita.com/shatolin/items/ca1810e419fee5fd963b) | Total guide to Claude Code plugins/MCP/tools |
| 🇯🇵 | qiita.com (@kai_kou) | [link](https://qiita.com/kai_kou/items/71ee39f27fc09d451cf8) | Team plugin sharing guide |
| 🇯🇵 | qiita.com (@kamome_susume) | [link](https://qiita.com/kamome_susume/items/33a34935707d2be1361a) | Recommended MCP server list |
| 🇯🇵 | zenn.dev (@goyle0) | [link](https://zenn.dev/goyle0/articles/claude-code-mcp-plugins) | MCP plugins for hallucination prevention |
| 🇯🇵 | zenn.dev (@chmod644) | [link](https://zenn.dev/chmod644/articles/claude-code-official-plugins-guide) | All 59 official plugins explained |
| 🇯🇵 | zenn.dev (@chmod644) | [link](https://zenn.dev/chmod644/articles/claude-code-plugins-all-59) | All 59 official plugins (full guide) |
| 🇯🇵 | note.com (@ai_jissennkai) | [link](https://note.com/ai_jissennkai/n/nc9ebedadd1f2) | Claude Code MCP: config, 5 real servers, DIY |
| 🇯🇵 | note.com (@ozzzagen) | [link](https://note.com/ozzzagen/n/n41d0be21a019) | 5 MCP Servers that transform Claude Code |
| 🇯🇵 | zenn.dev (@nanananano) | [link](https://zenn.dev/nanananano/articles/df5802334d999e) | MCP setup guide (June 2026 state) |
| 🇨🇳 | juejin.cn | [link](https://juejin.cn/post/7633351194199244819) | Claude Code ecosystem demystification guide |
| 🇨🇳 | csdn.net | [link](https://blog.csdn.net/weixin_46984554/article/details/160860809) | Top 10 must-install MCPs for Claude Code |
| 🇨🇳 | zhihu.com | [link](https://zhuanlan.zhihu.com/p/1971872808159141982) | Complete Claude Code guide; MCP commands |
| 🇨🇳 | csdn.net | [link](https://blog.csdn.net/champaignwolf/article/details/160913544) | Claude Code + MCP hands-on tutorial |

---

## Stats Block

```
├─ 🟠 Reddit: 9 threads │ 2,031 upvotes │ 728 comments │ ⚠ partial (backup rate-limited)
├─ 🔵 X: 159 posts total │ 5,157 likes │ 312 reposts │ 🌐 67 + 🇯🇵 58 + 🇨🇳 34
├─ 🟡 HN: 34 stories total │ 5,487 pts │ 2,895 comments │ 🌐 23 + 🇯🇵 9 + 🇨🇳 2
├─ 🦋 Bluesky: 15 posts total │ 48 likes │ 🌐 12 + 🇯🇵 3
├─ 🐙 GitHub: 18 items total │ 🌐 4 + 🇯🇵 8 + 🇨🇳 6
├─ 🌐 Web: 27 pages │ 🇯🇵 10 (Qiita, Zenn, note) │ 🇨🇳 5 (Juejin, CSDN, Zhihu)
└─ 🗣️ Top voices: @RohanArun, @oikon48 🇯🇵, @yupi996 🇨🇳, @lukashanren1, @acedatacloud.bsky.social │ r/AppBusiness, r/ClaudeAI
```

---

## Data Gaps

- **YouTube (errored all three passes):** yt-dlp rate-limited/auth issue (HTTP 402 from ScrapeCreators). YouTube likely has substantial Claude Code plugin tutorial content not captured here. Run `brew upgrade yt-dlp` to fix.
- **TikTok / Instagram / Threads / LinkedIn (all 402):** ScrapeCreators API billing limit hit this run. TikTok in particular likely has #claudecode #mcpserver viral content not captured.
- **Reddit (partial):** Only 9 threads captured (backup also 402). r/ClaudeAI, r/LocalLLaMA likely have significant plugin/MCP discussion threads beyond what was retrieved. Dedicated subreddit lane returned 0 posts.
- **Chinese social platforms (Weibo, Bilibili):** Not searched by the engine; CN coverage relies on X (ZH handles), GitHub (CN repos), and WebSearch for Zhihu/CSDN/Juejin.
- **`--web-backend keyless`** flag (DuckDuckGo) does not exist in this skill version (v3.14.0 valid values: auto, brave, exa, serper, parallel, none). JP/CN passes used `--web-backend none` supplemented by native WebSearch targeting specific JP/CN domains. JP/CN web coverage may underrepresent content not indexed by Exa/native search.
- **Coverage estimate:** ~65-70% of likely discussion captured. YouTube and TikTok gaps are the most significant omissions.

---

## Key Quotes

> "Every 'department' is a Claude Code skill. Full stack with the actual workflows and costs" - r/AppBusiness ([link](https://www.reddit.com/r/AppBusiness/comments/1usio9p/my_ios_app_is_4_months_old_and_does_944_mrr_every/))

> "Your team's database, internal wiki, and deployment pipeline are invisible to Claude Code - unless you use MCP. Here's how to plug them all in without touching the core." - [@lukashanren1](https://x.com/lukashanren1/status/2071900526564831679) on X 🌐

> "Hey Super, build a website that audits Claude Code extensions. Let users choose project type, compare hooks, skills, MCP servers, subagents, and commands, run a scan, and review risks before enabling tools." - [@RohanArun](https://x.com/RohanArun/status/2075774470330212782) on X 🌐

> "Anthropicが、公式プラグイン 'claude-code-setup' をひっそり公開しました。このプラグインは、プロジェクト全体をスキャンして...必要な構成を提案してくれます。" ("Anthropic quietly released the official plugin 'claude-code-setup.' This plugin scans the entire project and suggests the necessary configuration.") - [@kingdom314159](https://x.com/kingdom314159/status/2070295299856502860) on X 🇯🇵

> "Codex杀疯了，移除了5小时使用限制！... 另一边，Claude Fable 5 又延期了。" ("Codex went wild, removed the 5-hour usage limit! On the other side, Claude Fable 5 was delayed again.") - [@yupi996](https://x.com/yupi996/status/2076484625959092453) on X 🇨🇳

> "Agent Skills open standard: Google Stitch向けのエージェントスキルとプラグインのコレクション。Codex、Claude Code、Cursor、Gemini CLIなどのコーディングエージェントでの利用を目的としています。" ("A collection of agent skills and plugins for Google Stitch. Compliant with the Agent Skills open standard, aimed at use in coding agents such as Codex, Claude Code, Cursor, and Gemini CLI.") - [@dailygithubtrends.bsky.social](https://bsky.app/profile/dailygithubtrends.bsky.social/post/3mqem2w2ssw22) on Bluesky 🇯🇵

> "13.4% of all skills (534 of 3,984) contain critical-level security issues, including credential theft, backdoor installation, and data exfiltration." - [Snyk ToxicSkills Study](https://snyk.io/blog/toxicskills-malicious-ai-agent-skills-clawhub/)

> "Nano Banana + MCP = image tools inside your IDE. Generate/edit images, try product shots, or mock creative assets from Claude, VS Code, or Cursor. One API token, free credits, no context switching." - [@acedatacloud.bsky.social](https://bsky.app/profile/acedatacloud.bsky.social/post/3mqict4biat2c) on Bluesky 🌐

> "The bottleneck is no longer the protocol itself; it's discovery, and knowing when to build versus when to find." - [codeongrass.com on MCP ecosystem](https://codeongrass.com/blog/mcp-server-ecosystem-integration-layer-ai-agents-2026/) 🌐

> "GitHub Trending榜被Claude Code / Codex相关技能、插件和Agent管理工具占据" ("GitHub Trending dominated by Claude Code/Codex related skills, plugins, and agent management tools.") - [AI open source trends daily digest](https://github.com/loxehate/loxehate.github.io/issues/10) 🇨🇳
