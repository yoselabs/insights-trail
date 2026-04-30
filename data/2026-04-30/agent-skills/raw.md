# Agent Skills & Plugin Ecosystem — Raw Research Data
**Date collected:** 2026-04-30
**Skill version:** last30days v3.1.1
**Topic:** Claude Code skills and plugins, agent skill marketplaces, MCP servers and tools, Claude Code extensions, reusable agent capabilities, skill discovery and distribution, plugin ecosystems, agent tool registries, custom Claude Code workflows

---

## Skill Pipeline Output

### Pipeline Stats
```
├─ 🔵 X: 13 posts │ 1,195 likes │ 183 reposts │ 51 replies
├─ 🌐 Web: 14 pages (skill grounding) + 40+ pages (WebSearch supplemental)
├─ 🟠 Reddit: 0 results (403/402 errors across all targeted subreddits)
├─ 🔴 YouTube: 0 results (API access limitations)
├─ 🟣 TikTok: 0 results (API access limitations)
├─ 🩷 Instagram: 0 results (API access limitations)
├─ 🦋 Bluesky: 0 results (API access limitations)
├─ 📊 Polymarket: 0 results (no active markets on topic)
├─ 🟢 HN: 0 results (API access limitations)
└─ 🗣️ Top voices: @CoralOS_ai, @heynavtoor, @ranjankumar
```

---

## X/Twitter Posts (Raw)

### Post 1
**Handle:** @ranjankumar
**URL:** https://x.com/ranjankumar/status/2046094091004297421
**Date:** ~April 20, 2026
**Likes:** ~180 | **Reposts:** ~28
**Text:** "You add a subagent to fix Claude's tool choices. Now you have a subagent managing which code tool to use, and Claude still defaults wrong half the time because the subagent only fires when invoked, not on every session. You needed one line in CLAUDE.md. This is the core failure mode: reaching for the wrong layer."
**Context:** Thread on the 5-layer Claude Code extensibility model (CLAUDE.md, MCP, Skills, Subagents, Hooks)

### Post 2
**Handle:** @heynavtoor
**URL:** https://x.com/heynavtoor/status/2046476497800823280
**Date:** April 21, 2026
**Likes:** 949 | **Reposts:** 149
**Text:** "If I had to learn Claude Code in 7 days, I would not watch a single tutorial. I would study these 10 GitHub repos."
**Named repos:** Awesome Claude Code (master index of skills, hooks, commands, agents, CLAUDE.md files), Claude Code Templates (600+ agents, 200+ commands, 55+ MCPs), Claude Task Master (spec-to-task conversion), SuperClaude Framework (30+ custom commands)

### Post 3
**Handle:** @TheAIWorld22
**URL:** https://x.com/TheAIWorld22/status/2046576961632469056
**Date:** April 21, 2026
**Text:** Near-identical clone of @heynavtoor thread; posted same day; community noted Twitter clone farming behavior.

### Post 4
**Handle:** @Suryanshti777
**URL:** https://x.com/Suryanshti777/status/2046578992615235628
**Date:** April 21, 2026
**Text:** Near-identical clone of @heynavtoor thread; posted same day.

### Post 5
**Handle:** @appwrite
**URL:** https://x.com/appwrite/status/2046268569902809332
**Date:** April 20, 2026
**Likes:** 78 | **Reposts:** 7
**Text:** "With a single install, the Appwrite plugin brings skills and MCP servers into Claude Code so your agent can read, write, and operate on your project with live context and always follow the latest SDK patterns."

### Post 6
**Handle:** @CoralOS_ai
**URL:** https://x.com/CoralOS_ai/status/2048793208902332416
**Date:** April 27, 2026
**Text:** "Skills and MCP servers load in one harness format and convert automatically for whichever gets spawned next. Either harness can take the orchestrator seat. Agents talk peer-to-peer, not just up to the orchestrator."
**Context:** Demo of harness-level proxy allowing Hermes Agent to spawn Claude Code mid-task with automatic skill/MCP format conversion.

### Post 7
**Handle:** @Butler_Agent
**URL:** https://x.com/Butler_Agent/status/2042166963095654766
**Date:** April 9, 2026
**Text:** Description of proposed cross-chain identity and trust oracle for agent-to-agent coordination: "a trust oracle would allow agents to: 1. Verify identities across chains without manual overhead. 2. Establish 'reputation scores' to filter out low-quality or malicious agents. 3. Automate the handshake between agent capabilities and task requirements."

### Post 8
**Handle:** @sinedied
**URL:** https://x.com/sinedied/status/2049126546271564164
**Date:** April 28, 2026
**Text:** MCP servers can now render rich interactive UIs directly inside VS Code Copilot, Claude, and ChatGPT sessions — capability shift making MCP servers closer to apps than APIs.

### Post 9
**Handle:** @mykolanesov
**URL:** https://x.com/mykolanesov/status/2046567344353222897
**Date:** April 21, 2026
**Text:** "Claude Code discovers agent tooling — skills, MCP servers, plugins — only from project root. Workspace-level agents can't see child-repo tooling. Subagents don't inherit either. (Docs describe nested auto-discovery; behavior lags — issue #40640.)"

---

## Web Grounding Pages (Skill Pipeline)

### alexop.dev — Understanding Claude Code's Full Stack
**URL:** https://alexop.dev/posts/understanding-claude-code-full-stack/
**Key content:** Five extensibility layers defined: CLAUDE.md (ambient instructions), MCP servers (external tool connectivity), Skills (procedural knowledge, 30-50 tokens until invoked), Subagents (parallel specialized agents), Hooks (lifecycle automation across 18 events).

### claudemarketplaces.com — Plugin Marketplace
**URL:** https://claudemarketplaces.com/
**Stats:** 4,200+ skills, 770+ MCP servers, 2,500+ marketplaces, 110,000+ developers monthly (as of April 29, 2026).

### jeremylongshore/claude-code-plugins-plus-skills
**URL:** https://github.com/jeremylongshore/claude-code-plugins-plus-skills
**Stats:** 423 plugins, 2,849 skills, 177 agents. `ccpi` CLI package manager at tonsofskills.com. Frontend Design plugin leads at 370K+ installs.

### my2cents.ai — Agentic Registries & Skills Discovery
**URL:** https://www.my2cents.ai/deep-dive/agentic-registries-skills-discovery/
**Key content:** Documents emerging /.well-known/agent-skills/ standard where any web server can advertise SKILL.md files without registering with a centralized marketplace. SKILL.md described as "becoming the standard way to extend AI agents."

### morphllm.com — Claude Code Skills vs MCP vs Plugins
**URL:** https://www.morphllm.com/claude-code-skills-mcp-plugins
**Key content:** Five-server setup with 58 tools previously consumed ~55,000 tokens before any conversation started. Anthropic's ToolSearch on-demand loading reduced this by 85%. Context overhead was "the silent performance killer."

### bytebridge Medium — Skills via MCP Control Plane
**URL:** https://bytebridge.medium.com/introducing-skills-via-an-mcp-control-plane-406c979d5975
**Key content:** Argument for a central MCP control plane managing skill versioning and routing across multi-agent systems — essentially an API gateway for capability distribution. Mastra confirmed upcoming MCP extension collapsing skills/MCP distinction.

### alirezarezvani/claude-skills
**URL:** https://github.com/alirezarezvani/claude-skills
**Stats:** 232+ skills working across Claude Code, Codex, Gemini CLI, Cursor, and 8 more coding agents.

### automationswitch.com — Where to Find MCP Servers 2026
**URL:** https://automationswitch.com/ai-workflows/where-to-find-mcp-servers-2026
**Key content:** Registry comparison: PulseMCP (11,840+ hand-reviewed), Smithery (7,000+, app-store UI), mcp.so (19,700+, community-submitted), Glama.ai (21,000+, largest volume).

### truefoundry.com — Best MCP Registries 2026
**URL:** https://www.truefoundry.com/blog/best-mcp-registries
**Key content:** Three discovery source types: directories (browsing), registries (building), meta-indexes (navigation). Official Anthropic registry at registry.modelcontextprotocol.io has 2,000+ vetted entries.

### microsoft/apm — Agent Package Manager
**URL:** https://github.com/microsoft/apm (1K stars)
**Key content:** Open accepted issue #676 (April 11) for URL-based marketplace registration as a discovery index standard.

---

## WebSearch Supplemental Results

### claudefa.st — 50+ Best MCP Servers
**URL:** https://claudefa.st/blog/tools/mcp-extensions/best-addons

### code.claude.com — Plugins Reference
**URL:** https://code.claude.com/docs/en/plugins-reference
**Key content:** Plugin components include skills, agents, hooks, MCP servers, LSP servers, and monitors. A plugin is a bundle of Claude Code extensions packaged as one installable unit.

### turbodocx.com — Best Claude Code Plugins, Skills & MCP Servers
**URL:** https://www.turbodocx.com/blog/best-claude-code-skills-plugins-mcp-servers

### morphllm.com — Claude Code Extensions Guide
**URL:** https://www.morphllm.com/claude-code-extensions

### dev.to/williamwangai — Skills vs MCP Servers
**URL:** https://dev.to/williamwangai/claude-code-skills-vs-mcp-servers-what-to-use-how-to-install-and-the-best-ones-in-2026-548k

### dev.to/raxxostudios — Best Claude Code Skills & Plugins 2026
**URL:** https://dev.to/raxxostudios/best-claude-code-skills-plugins-2026-guide-4ak4

### aws.amazon.com — AWS Agent Registry Preview
**URL:** https://aws.amazon.com/about-aws/whats-new/2026/04/aws-agent-registry-in-agentcore-preview/
**Key content:** Private, governed catalog and discovery layer for agents, tools, skills, MCP servers, and custom resources within organizations. Hybrid keyword + semantic search.

### github.com/agentic-community/mcp-gateway-registry
**URL:** https://github.com/agentic-community/mcp-gateway-registry
**Key content:** Enterprise-ready MCP Gateway & Registry with secure OAuth authentication, dynamic tool discovery, Keycloak/Entra integration.

### mcpmarket.com
**URL:** https://mcpmarket.com/

### docs.stacklok.com — ToolHive Agent Skills
**URL:** https://docs.stacklok.com/toolhive/updates/2026/04/06/updates
**Key content:** ToolHive now supports agent skills — reusable bundles teaching agents when, why, and how to use tools. Supports installing from ToolHive Registry Server, OCI registries, or Git repositories.

### digitalapplied.com — AI Agent Marketplaces 2026
**URL:** https://www.digitalapplied.com/blog/ai-agent-marketplaces-2026-discovery-distribution
**Key content:** Eight marketplaces matter: Claude Skills, GPT Store, MCP Hubs, Hugging Face Spaces, Replit Agent Market, LangChain Hub, Vercel Agent Gallery, Cloudflare AI Marketplace.

### infoq.com — AWS Agent Registry Preview
**URL:** https://www.infoq.com/news/2026/04/aws-agent-registry-preview/

### explainx.ai — What are Agent Skills?
**URL:** https://explainx.ai/blog/what-are-agent-skills-complete-guide

### modelcontextprotocol.io — Build with Agent Skills
**URL:** https://modelcontextprotocol.io/docs/develop/build-with-agent-skills

### anandtopu Medium — Future of MCP 2026
**URL:** https://anandtopu.medium.com/the-future-of-mcp-how-agents-get-connected-in-2026-ee24d62c0c43

### github.com/VoltAgent/awesome-agent-skills
**URL:** https://github.com/VoltAgent/awesome-agent-skills
**Stats:** 1,000+ agent skills compatible with Claude Code, Codex, Gemini CLI, Cursor, and more.

### itecsonline.com — Codex CLI Agent Skills Guide
**URL:** https://itecsonline.com/post/codex-cli-agent-skills-guide-install-usage-cross-platform-resources-2026

### thepromptindex.com — AI Agent Skills Guide 2026
**URL:** https://www.thepromptindex.com/how-to-use-ai-agent-skills-the-complete-guide.html

### github.com/sickn33/antigravity-awesome-skills
**URL:** https://github.com/sickn33/antigravity-awesome-skills
**Stats:** 1,400+ agentic skills for Claude Code, Cursor, Codex CLI, Gemini CLI, Antigravity, and more. Includes installer CLI.

### github.com/skillmatic-ai/awesome-agent-skills
**URL:** https://github.com/skillmatic-ai/awesome-agent-skills

### awesomeskills.dev
**URL:** https://www.awesomeskills.dev/en

### agensi.io — Claude Code Skills vs Cursor Rules vs Codex Skills
**URL:** https://www.agensi.io/learn/claude-code-skills-vs-cursor-rules-vs-codex-skills

### toolworthy.ai — Skills.sh Review
**URL:** https://www.toolworthy.ai/tool/skills-sh
**Key content:** skills.sh launched January 20, 2026. Top skills accumulated 26,000+ installs within weeks. Used with 40+ agent platforms.

### dev.to/rosgluk — Claude Skills and SKILL.md for Developers
**URL:** https://dev.to/rosgluk/claude-skills-and-skillmd-for-developers-vs-code-jetbrains-cursor-17f6

### code.visualstudio.com — Use Agent Skills in VS Code
**URL:** https://code.visualstudio.com/docs/copilot/customization/agent-skills

### agentskills.io — Specification
**URL:** https://agentskills.io/specification
**Key content:** Open Agent Skills specification originally developed by Anthropic. Format is filesystem-based, not API-dependent. Cross-platform: OpenAI Codex, Google Antigravity, Cursor, GitHub Copilot, 30+ others.

### github.com/wshobson/agents — Agent Skills Docs
**URL:** https://github.com/wshobson/agents/blob/main/docs/agent-skills.md

### developers.openai.com — Codex Skills
**URL:** https://developers.openai.com/codex/skills

### github.com/cloudflare/agent-skills-discovery-rfc
**URL:** https://github.com/cloudflare/agent-skills-discovery-rfc
**Key content:** Maintained by Cloudflare. Specifies /.well-known/agent-skills/ URI (RFC 8615-compliant). Index contains $schema field, skills array with name/type/description/url/digest. Renamed from /.well-known/skills/. Security: allowlist trusted domains before loading.

### platform.claude.com — Agent Skills Docs
**URL:** https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview

### learn.microsoft.com — Agent Skills (Microsoft)
**URL:** https://learn.microsoft.com/en-us/agent-framework/agents/skills

### deepwiki.com — SKILL.md Specification
**URL:** https://deepwiki.com/agentskills/agentskills/2.2-skill.md-specification

### opencode.ai — Skills
**URL:** https://opencode.ai/docs/skills/

### abvijaykumar Medium — Deep Dive SKILL.md
**URL:** https://abvijaykumar.medium.com/deep-dive-skill-md-part-1-2-09fc9a536996

### automationswitch.com — Where to Find MCP Servers 2026 (duplicate)
**URL:** https://automationswitch.com/ai-workflows/where-to-find-mcp-servers-2026

### dev.to/toolstem — Building MCP Server (Greg Isenberg Playbook)
**URL:** https://dev.to/toolstem/i-built-the-mcp-server-greg-isenberg-recommends-in-his-2026-distribution-playbook-heres-day-7-3c33

### composio.dev — Best Smithery Alternatives 2026
**URL:** https://composio.dev/blog/smithery-alternative

### dynomapper.com — MCP Server Directories Complete List
**URL:** https://dynomapper.com/blog/ai/mcp-server-directories/

### popularaitools.ai — 50 Best MCP Servers 2026
**URL:** https://popularaitools.ai/blog/50-best-mcp-servers-2026

### apigene.ai — MCP Marketplace Guide
**URL:** https://apigene.ai/blog/mcp-marketplace

### taskade.com — 15 Best MCP Servers 2026
**URL:** https://www.taskade.com/blog/mcp-servers

### smithery.ai
**URL:** https://smithery.ai (7,000+ servers)
**URL:** https://smithery.ai/server/@orliesaurus/pulsemcp-server/api

### github.com/modelcontextprotocol/servers
**URL:** https://github.com/modelcontextprotocol/servers

---

## Ecosystem Size Reference Data (as of April 2026)

| Registry | Server Count | Notes |
|----------|-------------|-------|
| Glama.ai/mcp | 21,000+ | Largest volume, daily updates |
| mcp.so | 19,700+ | Community-submitted |
| PulseMCP | 11,840+ | Hand-reviewed daily |
| Smithery | 7,000+ | App-store UI, hosted remote servers |
| Official (registry.modelcontextprotocol.io) | 2,000+ | Vetted entries |
| MCPMarket | varies | — |

| Platform | Count | Notes |
|----------|-------|-------|
| claudemarketplaces.com | 4,200+ skills, 770+ MCPs | 110K+ devs/month |
| tonsofskills.com (jeremylongshore) | 2,849 skills, 423 plugins | ccpi CLI |
| alirezarezvani/claude-skills | 232+ skills | 10+ agents compatible |
| VoltAgent/awesome-agent-skills | 1,000+ skills | — |
| sickn33/antigravity-awesome-skills | 1,400+ skills | Installer CLI |
| skills.sh | 26,000+ installs | 40+ agent platforms |

---

## Timeline

- **Late 2025:** Anthropic introduces Skills mechanism in Claude Code; SKILL.md format emerges
- **Late 2025:** Claude Code plugins launch in public beta (October 2025)
- **Late 2025–Early 2026:** OpenAI adopts SKILL.md format for Codex CLI within weeks
- **January 2026:** Google integrates Agent Skills standard into Antigravity
- **January 20, 2026:** skills.sh launches as dedicated package manager
- **April 2026:** AWS Agent Registry launches in preview (Amazon Bedrock AgentCore)
- **April 6, 2026:** ToolHive adds agent skills support
- **April 9, 2026:** @Butler_Agent proposes cross-chain trust oracle for agent discovery
- **April 11, 2026:** microsoft/apm issue #676 — URL-based marketplace registration standard
- **April 20, 2026:** Appwrite plugin for Claude Code launches
- **April 21, 2026:** @heynavtoor "10 GitHub repos" thread goes viral (949 likes)
- **April 27, 2026:** @CoralOS_ai demonstrates cross-harness skill portability
- **April 28, 2026:** @sinedied notes MCP servers now serve interactive UIs in agent sessions
- **April 29, 2026:** claudemarketplaces.com reports 110K+ monthly developers
