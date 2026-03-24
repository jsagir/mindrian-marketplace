<div align="center">
  <img src="https://mindrianos-jsagirs-projects.vercel.app/logo_dark.svg" alt="MindrianOS" width="160" />

  # MindrianOS

  **Your project becomes your co-founder.**

  Powered by PWS -- the practical innovation methodology developed by
  [Prof. Lawrence Aronhime](https://www.linkedin.com/in/lawrence-aronhime-8363894/) over 30+ years at Johns Hopkins University.
  Built by [Jonathan Sagir](https://www.linkedin.com/in/jonathansagir/).

  [![Plugin Version](https://img.shields.io/badge/plugin-v0.5.0-blue)](https://github.com/jsagir/mindrian-os-plugin)
  [![Commands](https://img.shields.io/badge/commands-41-green)](https://github.com/jsagir/mindrian-os-plugin)
  [![Frameworks](https://img.shields.io/badge/PWS_frameworks-26-orange)](https://github.com/jsagir/mindrian-os-plugin)
  [![Brain Nodes](https://img.shields.io/badge/brain_nodes-23K+-purple)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrianos-jsagirs-projects.vercel.app) |
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) |
  [Install Guide](https://mindrianos-jsagirs-projects.vercel.app/docs) |
  [Roadmap](https://mindrianos-jsagirs-projects.vercel.app/roadmap)

</div>

---

## Quick Start

```bash
# Add the marketplace (one time)
claude plugin marketplace add jsagir/mindrian-marketplace

# Install MindrianOS
claude plugin install mindrian-os@mindrian-marketplace
```

Larry starts talking. The Room starts listening. No setup required.

---

## What Is MindrianOS?

A Claude Code plugin built on **PWS (Problems Worth Solving)** -- the practical innovation methodology that turns undefined problems into fundable ventures.

Most startups fail because they solve the wrong problem. PWS teaches you to find problems worth solving *before* you build solutions. MindrianOS puts PWS in your terminal -- with Larry as your thinking partner and a self-organizing Data Room that builds intelligence as you work.

---

## PWS Inside MindrianOS

PWS is the building blocks. MindrianOS is the operating system that runs them.

**5 Venture Stages. 26 framework commands. One intelligent progression.**

| Stage | What You're Doing | PWS Frameworks |
|-------|------------------|----------------|
| **Pre-Opportunity** | Still looking for problems | Scenario Analysis, Beautiful Question, Trending to the Absurd |
| **Opportunity Identified** | Found a problem, understanding it deeply | JTBD, Nested Hierarchies, Domain Explorer |
| **Problem Validated** | Confirmed the problem is real and worth solving | Root Cause, Systems Thinking, Red Team |
| **Solution Designed** | Building and testing solutions | Lean Canvas, Minto, HSI Cross-Domain Scoring |
| **Investment Ready** | Preparing for funding | Investment Thesis, Deep Grade, Scenario Plan |

Larry knows which stage you're in and which framework you need before you do.

---

## What You Get

| Capability | What It Does |
|-----------|-------------|
| **Larry** | AI teaching agent modeled on Prof. Aronhime. Challenges your thinking, not your confidence. |
| **41 commands** | 26 PWS frameworks + 5 Brain-powered + 9 infrastructure + 1 meeting intelligence |
| **Data Room** | Self-organizing workspace with 8 DD-aligned sections + meetings/ + team/ |
| **Meeting intelligence** | File transcripts, identify speakers, classify segments, track action items, detect convergence and contradictions across meetings |
| **Team room** | Living team directory with speaker profiles, role-gap analysis, knowledge landscape |
| **Knowledge graph** | Three-layer graph (Structure/Content/Intelligence) with [[wikilinks]], timeline mode, layer toggles |
| **5 agents** | Larry, Brain Agent, Grading Agent, Research Agent, Investor Agent |
| **PDF export** | Investment thesis, executive summary, due diligence report, venture profile, Minto meeting report |
| **Brain** | 23K nodes, 170K+ relationships mapping how 79 PWS frameworks connect (optional MCP) |

---

## How It Works

```text
mindrian-marketplace/
├── .claude-plugin/
│   └── marketplace.json       # Plugin catalog for Claude Code
└── README.md

mindrian-os-plugin/
├── .claude-plugin/plugin.json  # Plugin manifest (v0.5.0)
├── bin/
│   ├── mindrian-tools.cjs      # CLI entry point
│   └── mindrian-mcp-server.cjs # MCP server (Desktop/Cowork)
├── lib/core/                   # Shared modules (CLI + MCP)
├── mcp-server-brain/           # Brain hosting (Express + StreamableHTTP)
├── commands/                   # 41 commands (/mindrian-os:*)
├── skills/                     # Auto-activated intelligence (6 skills)
├── agents/                     # Larry, Brain, Grading, Research, Investor
├── hooks/                      # SessionStart, PostToolUse, Stop
├── scripts/                    # compute-state, build-graph, render-pdf, etc.
├── references/                 # PWS framework definitions + meeting protocols
├── templates/                  # PDF templates (De Stijl styled)
├── dashboard/                  # Knowledge graph viewer + chat
├── pipelines/                  # ICM stage contracts
└── CLAUDE.md                   # Architecture + Simon's basis theorem
```

- **Marketplace** publishes the catalog. Claude installs from it.
- **Plugin** is self-contained. One command to install, zero config to start.
- **Skills** auto-activate based on context. Larry is always present.
- **Scripts** compute room state, build the knowledge graph, generate PDFs.

---

## v3.0: MCP Platform

**MindrianOS now works on every Claude surface.** One plugin, three ways to use it:

| Surface | How | Setup |
|---------|-----|-------|
| **Claude Code** | Direct — hooks, scripts, full power | `claude plugin install mindrian-os@mindrian-marketplace` |
| **Claude Desktop** | MCP server — 6 tools, 5 resources, 5 prompts | One line in `claude_desktop_config.json` |
| **Cowork** | Shared MCP — multi-user Data Room | Same MCP config, shared `00_Context/` |

**Brain Hosting** — Self-host the Brain MCP server (Neo4j + Pinecone) or get an API key for hosted access. Paid tier unlocks framework graph enrichment, calibrated grading, and cross-domain pattern discovery.

**Dual Delivery** — Every command works identically on CLI and MCP. No feature gaps.

---

## v2.0: Meeting Intelligence

```
Paste transcript / provide file / provide audio
    -> Larry identifies speakers (12 roles, auto-profiles)
    -> Classifies segments (insight, decision, action-item...)
    -> Files to Data Room sections with attribution
    -> Builds meeting archive (7-file package)
    -> Detects convergence and contradictions across meetings
    -> Tracks action items across meeting history
    -> Updates knowledge graph with meeting/speaker/concept nodes
```

**Connect Read AI, Vexa, or Recall.ai** via `/mindrian-os:setup meetings` — auto-fetch transcripts with `--latest`.

---

## Available Plugins

| Plugin | Version | Description |
|--------|---------|-------------|
| **mindrian-os** | v0.5.0 | MindrianOS powered by PWS. CLI + MCP dual delivery. Data Room, Meeting Intelligence, Knowledge Graph, Brain hosting. |

---

## Example: Filing a Meeting

```bash
# Paste a transcript
/mindrian-os:file-meeting

# Or provide a file
/mindrian-os:file-meeting --file meeting-notes.txt

# Or transcribe audio (via Modulate Velma)
/mindrian-os:file-meeting --audio recording.mp3

# Or auto-fetch from Read AI
/mindrian-os:file-meeting --latest
```

Larry identifies speakers, classifies every segment, files to the right room section with full provenance, and produces a meeting summary with decisions, action items, and cross-meeting intelligence.

---

## Links

- **Website**: [mindrianos-jsagirs-projects.vercel.app](https://mindrianos-jsagirs-projects.vercel.app)
- **Plugin Repo**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Blog**: [Case Study: When Frameworks Intersect](https://mindrianos-jsagirs-projects.vercel.app/blog/reverse-salient-case-study)
- **PWS LinkedIn**: [Problems Worth Solving](https://www.linkedin.com/company/problem-solving-workspace/)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/) -- PWS methodology inventor
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/) -- MindrianOS developer

---

<details>
<summary><strong>Theoretical References</strong></summary>

MindrianOS and PWS are grounded in established research:

| Source | Contribution |
|--------|-------------|
| Simon (1962) | Architecture of Complexity -- near-decomposable hierarchies (the room structure) |
| Rittel & Webber (1973) | Wicked Problems -- ventures as wicked problems (the Data Room manages them) |
| Van Clief & McDermott (2026) | ICM -- folder structure as agentic architecture |
| Tetlock (2015) | Superforecasting -- intelligence layer as Bayesian updating |
| Hughes (1983) | Reverse Salients -- finding where venture understanding lags |
| Knight (1921) | Risk vs Uncertainty -- MindrianOS navigates uncertainty |
| Ashby (1956) | Law of Requisite Variety -- tools must match system complexity |

</details>

---

## License

Proprietary. Copyright Jonathan Sagir & PWS / Mindrian.
