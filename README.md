<div align="center">
  <img src="https://mindrianos-jsagirs-projects.vercel.app/logo_dark.svg" alt="MindrianOS" width="160" />

  # MindrianOS

  **For the wicked navigator. Compass and map for the founder, researcher, or operator walking through a problem worth solving.**

  Powered by PWS, the practical innovation methodology developed by
  [Prof. Lawrence Aronhime](https://www.linkedin.com/in/lawrence-aronhime-8363894/) over 30+ years at Johns Hopkins University.
  Built by [Jonathan Sagir](https://www.linkedin.com/in/jonathansagir/).

  [![Plugin Version](https://img.shields.io/badge/plugin-v1.13.0_(currently_beta.12)-blue)](https://github.com/jsagir/mindrian-os-plugin)
  [![Milestone](https://img.shields.io/badge/milestone-The_Closed_Loop-success)](https://github.com/jsagir/mindrian-os-plugin/blob/main/CHANGELOG.md)
  [![Commands](https://img.shields.io/badge/commands-85-green)](https://github.com/jsagir/mindrian-os-plugin)
  [![Skills](https://img.shields.io/badge/skills-10-cyan)](https://github.com/jsagir/mindrian-os-plugin)
  [![Agents](https://img.shields.io/badge/agents-9-orange)](https://github.com/jsagir/mindrian-os-plugin)
  [![Hook surfaces](https://img.shields.io/badge/hook_surfaces-4-red)](https://github.com/jsagir/mindrian-os-plugin)
  [![Edge Types](https://img.shields.io/badge/cascade_edges-12-yellow)](https://github.com/jsagir/mindrian-os-plugin)
  [![License](https://img.shields.io/badge/license-BSL_1.1-orange)](https://github.com/jsagir/mindrian-os-plugin/blob/main/LICENSE)
  [![Surfaces](https://img.shields.io/badge/surfaces-CLI_+_Desktop_+_Cowork-brightgreen)](https://github.com/jsagir/mindrian-os-plugin)
  [![Node](https://img.shields.io/badge/node-%3E%3D22.5.0-brightgreen)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrianos-jsagirs-projects.vercel.app) |
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) |
  [Brain Access](https://mindrianos-jsagirs-projects.vercel.app/brain-access) |
  [Changelog](https://github.com/jsagir/mindrian-os-plugin/blob/main/CHANGELOG.md)

</div>

---

## v1.13.0 -- The Closed Loop

MindrianOS turns the venture from a folder you archive into a closed conversation loop you walk through. Larry leads turn 1. A local SQL graph remembers what you said. The Brain (optional remote methodology graph) reasons over typed packets and never sees your data. The first material you file kicks off a triple-filter math layer (whitespace + reverse salient + cross-domain match) and surfaces non-obvious opportunities by your next turn. Every decision becomes a typed edge in your room graph.

This release is currently shipping as `v1.13.0-beta.12`; final `v1.13.0` is imminent. Install today to track the closing capstones (Phase 121.5 terminal coherence + Phase 122 Workflow Layer, both shipped in beta.12).

---

## Quick Start

### Option A: npm one-liner (recommended for v1.13.0)

```bash
npx @mindrian_os/install
```

Runs the Claude Code plugin install end-to-end. Adds the marketplace, installs the `mos` plugin, and stamps the statusline. Restart Claude Code, Larry starts talking.

### Option B: Plugin Marketplace

```bash
claude plugin marketplace add jsagir/mindrian-marketplace
claude plugin install mos@mindrian-marketplace
```

### Option C: One-line shell install

```bash
curl -sL https://raw.githubusercontent.com/jsagir/mindrian-os-plugin/main/install.sh | bash
```

### To update or repair an existing install

```bash
mindrian-os update           # marketplace update + plugin update
mindrian-os doctor --all     # diagnose every drift class with fix suggestions
```

Both shell out to the active plugin install resolved via `lib/core/active-plugin-root.cjs` (the single resolver introduced in beta.12), so they work on any of the four installation paths.

---

## Works on All Three Claude Surfaces

| Surface | How | What you get |
|---------|-----|--------------|
| **Claude Code CLI** | Plugin (full power) | `claude plugin install mos@mindrian-marketplace`. Hooks fire, scripts run, full UI Ruling System, statusline, Data Room exports. |
| **Claude Desktop** | MCP server (auto-wired) | Plugin install registers the local MCP server. Hierarchical tools + 3 MCP Apps (dashboard, wiki, knowledge graph) inline. |
| **Cowork** | MCP + Scheduled Tasks | Same plugin, Streamable HTTP transport. Daily briefings, persistent hats, session catch-up. |

---

## What v1.13.0 Adds

| Capability | What it does |
|-----------|--------------|
| **Closed Loop** | Larry leads turn 1. Conversation produces a populated room in 45 seconds. Rooms are receipts, not setup wizards. |
| **Auto-Explore on first material** | First file you write inside a room triggers the triple-filter math layer in the background. Findings surface on your next turn via a Decision Gate (Explore / Skip / Later). |
| **Unresolved Tension Hook** | Larry remembers contradictions across sessions and re-opens them when relevant. The variable-reward closer of the closed loop. |
| **30-Second MVA + Room-as-Receipt** | A first conversation always produces a Minimum Viable Artifact and a populated room in under a minute. The room is a receipt of what the conversation produced. |
| **Workflow Layer (Phase 122)** | `data/command-registry.json` + `lib/workflow/command-resolver.cjs`. Framework-to-command becomes a CI-enforced guarantee instead of model recall. Hallucinated commands cannot be emitted. |
| **Brain Context Packet Contract** | Brain queries are typed packets, not free-form prompts. Part 8 (the Graph Boundary) is structurally enforced, not just audited. |
| **SQL Navigation Spine + Memory Event Log** | `lib/core/navigation.cjs` is the single 13-function chokepoint over `room.db`. Every navigation step writes a `memory_event`. Instrumented test asserts zero non-SQLite filesystem reads during navigation. |
| **npx installer + active-plugin-root resolver** | `npx @mindrian_os/install` is a real one-command install. `lib/core/active-plugin-root.cjs` retires the whole "wrong plugin path" bug family across doctor / update / statusline. |
| **Install-cache Windows hardening** | Skill-loop no longer halts mid-install. `core.longpaths` auto-set, statusline registered first, `.install-receipt.json` records progress, doctor class H detects and re-stamps. |
| **Terminal Coherence Capstone (Phase 121.5)** | Every UI surface across the milestone harmonized into one terminal experience: SessionStart Coordinator, four-zone body shape sweep, two-row statusline, canonical De Stijl palette. |

---

## Connect the Brain (optional)

The Brain is a remote MCP server holding 32K+ teaching-graph nodes (framework chains, calibrated grading, cross-domain pattern discovery). It enriches Larry but is never required. Your local room data never leaves your machine; the Brain only ever receives generic framework handles, phase identifiers, sha256 hashes, and enum scalars (the Brain Context Packet contract).

Request access: [mindrianos-jsagirs-projects.vercel.app/brain-access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)

| Capability | Without Brain | With Brain |
|-----------|---------------|------------|
| Larry teaching personality | Full | Full |
| 85 commands | All work | All work |
| Framework chaining | Local-Only (Navigation Engine) | Mode A (Brain-derived, with confidence-gated RECOMMENDED) |
| Grading | Rubric only | Calibrated against 100+ real projects |
| Cross-domain analogy | Local SQL + Pinecone | + Brain FEEDS_INTO traversal |

After approval, paste the provided key. The plugin's resolver picks it up from any of: `MINDRIAN_BRAIN_KEY` env var, `~/.mindrian.env`, or the per-room `.env`.

---

## First Five Moves Inside a Room

```bash
# 1. Start a venture room (Larry leads the conversation)
/mos:new-project

# 2. Pick the right next move (Brain or Local Only, your call)
/mos:suggest-next

# 3. Run methodology (one /mos: command per framework, chainable)
/mos:beautiful-question
/mos:analyze-needs

# 4. File a meeting (paste, file, or audio via Velma)
/mos:file-meeting

# 5. Ask the graph (natural language over your local room.db)
/mos:query "what contradicts my pricing model?"
```

Don't know which command? Just talk. Larry routes through the Workflow Layer registry to the right `/mos:*` command. Hallucinated commands cannot be emitted.

---

## The Two Graphs

```
Brain  (remote, optional)                    Room Graph  (local, always on)
Methodology graph                            YOUR venture's structure
Framework chains + calibrated grading        Grows as you file artifacts
~32K nodes / 65K+ relationships              ~12 cascade edge types
Connects via API key                         Embedded SQLite (room.db)
NEVER receives your data (Part 8)            Never egresses anywhere

         Brain tells you HOW to think about this kind of problem.
         Room Graph tells you WHAT your own data is saying.
         Together: more powerful than either alone.
```

**Cascade edge types** (room graph): INFORMS, CONTRADICTS, CONVERGES, ENABLES, INVALIDATES, BELONGS_TO, CAUSES, CASCADES_TO, EXTRACTED_FROM, HSI_CONNECTION, REVERSE_SALIENT, ANALOGY_MATCH.

**Part 8 Graph Boundary**: LOCAL data never reaches BRAIN. Brain queries carry only generic framework names, phase identifiers, sha256 hashes, and enum scalars. This is a constitutional property of the system, enforced at the wire by the Brain Context Packet Contract and audited at the PR layer by the brain-boundary scan.

---

## Available Plugins

| Plugin | Version | Description |
|--------|---------|-------------|
| **mos** | v1.13.0 (currently beta.12) | MindrianOS by PWS. 85 commands, 10 skills, 9 agents, 4 hook surfaces, 12 cascade edge types. v1.13.0 "The Closed Loop": Larry leads turn 1, conversation IS the front door, Workflow Layer makes framework-to-command CI-enforced, Brain Context Packet Contract structurally enforces Part 8, SQL Navigation Spine + Memory Event Log replace folder-scanning with graph navigation, auto-explore on first material, 30-second MVA, room-as-receipt invariant, terminal coherence capstone. Dual delivery (CLI + Desktop + Cowork). |

---

## Links

- **Website**: [mindrianos-jsagirs-projects.vercel.app](https://mindrianos-jsagirs-projects.vercel.app)
- **Plugin Repo**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Changelog**: [CHANGELOG.md](https://github.com/jsagir/mindrian-os-plugin/blob/main/CHANGELOG.md)
- **Brain Access**: [Request API Key](https://mindrianos-jsagirs-projects.vercel.app/brain-access)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/), PWS methodology
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/), MindrianOS developer

---

## License

Source-available (BSL 1.1), not open source. See [LICENSE](https://github.com/jsagir/mindrian-os-plugin/blob/main/LICENSE). Copyright Jonathan Sagir and PWS / Mindrian.
