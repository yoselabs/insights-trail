Now synthesizing per the SKILL.md voice contract (LAWs 1-8):

---

🌐 last30days v3.3.1 · synced 2026-05-30

What I learned:

**Anthropic launched its own official plugin directory on May 22 - and it hit 20,000 stars in days** - The [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) GitHub repo is now Anthropic's curated, company-maintained index of Claude Code plugins. Per [Tech Times](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm), the launch came with an explicit warning from Anthropic about unverified MCP server security risks - a signal that the ecosystem's explosive growth (9,400+ registered servers by mid-April) has created a trust problem alongside the supply problem. There are now two official surfaces: claude-plugins-official (auto-installed, Anthropic-curated) and claude-community (third-party, review-gated, added via `/plugin marketplace add`).

**The MCP registry landscape fragmented into competing hubs - and nobody's in charge** - Per [TrueFoundry](https://www.truefoundry.com/blog/best-mcp-registries), the four registries that matter in 2026 are mcp.so (20,222 servers listed), smithery.ai (7,000+ installable servers, closest thing to a Docker Hub), glama.ai/mcp, and the punkpeye/awesome-mcp-servers GitHub list. Anthropic deliberately does not operate a canonical registry, per [Digital Applied](https://www.digitalapplied.com/blog/mcp-ecosystem-h1-2026-retrospective-adoption-data-points) - which means discovery friction is the community's to solve. That same report notes the agent skills ecosystem grew from one registry in December 2025 to eight major marketplaces by Q2 2026 - creating an irony where "developers now spend more time comparing marketplaces than finding skills."

**Plugins are the packaging layer - skills, MCPs, and hooks bundled for one-command org rollout** - Per [claudefa.st](https://claudefa.st/blog/tools/mcp-extensions/plugins-distribution) (May 27), the mental model solidifying in the community is: skills teach Claude Code custom workflows, MCPs connect it to external APIs, hooks automate behavior on events, and plugins bundle all three into a single installable unit. [r/ClaudeWorkflows](https://reddit.com/r/ClaudeWorkflows) is the highest-traffic subreddit in the engine's Reddit corpus for this topic. Hacker News surfaced a 437-point, 249-comment thread - ["Claude Code as a Daily Driver: Claude.md, Skills, Subagents, Plugins, and MCPs"](https://arps18.github.io/posts/claude-code-mastery/) - as the canonical community explainer for this mental model.

**DeepClaude - running DeepSeek V4 Pro inside Claude Code's agent loop - went viral on HN** - [DeepClaude](https://github.com/aattaran/deepclaude) posted 678 points and 281 comments on [Hacker News](https://news.ycombinator.com) (May 3), showing that the plugin/extension model is being used not just for tool integrations but for swapping the underlying model within Claude Code's orchestration layer. This is a pattern: Claude Code as a durable agent shell, with the model and tools both treated as hot-swappable plugins.

**Cross-tool skill portability is the emerging standard** - The [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) repo (337 skills, 30+ agents, 70+ custom commands) is compatible with Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents. Per the [WorkOS MCP guide](https://workos.com/blog/everything-your-team-needs-to-know-about-mcp-in-2026), the 2026 roadmap includes MCP Server Cards - a `.well-known` URL standard for capability metadata discovery without connecting, and stateless Streamable HTTP for scaling. HashiCorp now ships official Claude Code skills for Terraform and Packer encoding their own best practices. [@hailey.at](https://bsky.app/profile/hailey.at/post/3ml5jd6xlvc2v) on Bluesky (115 likes) noted she runs five to six simultaneous Claude sessions across two repos without writing code herself, crediting [@ed3d.net](https://bsky.app)'s plugins and skills.

**Enterprise MCP governance is now a product category** - Per [Digital Applied](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) and the [agentic-community/mcp-gateway-registry](https://github.com/agentic-community/mcp-gateway-registry) GitHub project, enterprise-focused gateway solutions include Lunar.dev MCPX, MCP Context Forge, and MCP Jungle. AWS launched its own [Agent Registry via Amazon Bedrock AgentCore](https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/) in April 2026 preview - a private, governed catalog for agents, tools, skills, and MCP servers within organizations. Kong also entered with an [MCP Server Registry product](https://konghq.com/products/mcp-registry).

KEY PATTERNS from the research:
1. The official plugin directory launching in May 2026 is the single biggest structural event - Anthropic ceded the registry space to the market, then stepped back in with curated certification per [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official)
2. Skills are cross-agent artifacts now, not Claude Code-exclusive - per [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills) and the SKILL.md open standard across Codex, Gemini CLI, Cursor
3. MCP security is the friction point people talk about most - Anthropic's own official directory announcement explicitly flagged unverified MCP risks, per [Tech Times](https://www.techtimes.com/articles/317139/20260525/claude-code-plugins-get-official-directory-anthropic-flags-unverified-mcp-risks.htm)
4. The "eight marketplaces by Q2 2026" stat from [Digital Applied](https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution) crystallizes the distribution paradox - more supply surfaces, more discovery friction
5. Model-swapping within the Claude Code agent shell (DeepClaude pattern) shows skills and plugins are being used for deeper architectural substitution, not just tool wrapping - per [Hacker News 678-point thread](https://github.com/aattaran/deepclaude)

---
✅ All agents reported back!
├─ 🟠 Reddit: 15 threads
├─ 🔵 X: 13 posts │ 13 likes │ 1 reposts
├─ 🟡 HN: 12 storys │ 1,414 points │ 715 comments
├─ 🦋 Bluesky: 8 posts │ 137 likes │ 3 reposts
├─ 🌐 Web: 10 pages - claudefa.st, GitHub, dev.to, clarista.io, p.rst.im, techtimes.com, refactix.com, theaiarchitects.com
├─ 🗣️ Top voices: @1999_eth, @RoundtableSpace, @_0xpainn │ r/ClaudeWorkflows, r/ClaudeAI, r/ClaudeCode
└─ 📎 Raw results saved to ~/Documents/Last30Days/claude-code-skills-and-plugins-agent-skill-marketplaces-mcp-servers-and-tools-claude-code-extensions-reusable-agent-capabilities-skill-discovery-and-distribution-plugin-ecosystems-agent-tool-registries-custom-claude-code-workflows-raw-v3.md
---

I'm now an expert on Claude Code skills, plugins, MCP servers, and the agent skill ecosystem. Some things I can help with:
- Deep dive into the security implications of Anthropic's unverified MCP warning and what to audit before installing
- Break down how the SKILL.md open standard enables cross-agent portability (Claude Code vs Codex vs Cursor)
- Explore the DeepClaude model-swapping pattern and what it means for building on top of Claude Code as a shell
- Compare the top MCP registries (mcp.so vs smithery.ai vs glama.ai) for a specific use case

I have all the links to the 15 Reddit threads, 13 X posts, 12 HN stories, 8 Bluesky posts, and 10 web pages I pulled from. Just ask.
