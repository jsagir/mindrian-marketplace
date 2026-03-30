<div align="center">
  <img src="https://mindrianos-jsagirs-projects.vercel.app/logo_dark.svg" alt="MindrianOS" width="160" />

  # MindrianOS

  **Your project becomes your co-founder.**

  Powered by PWS -- the practical innovation methodology developed by
  [Prof. Lawrence Aronhime](https://www.linkedin.com/in/lawrence-aronhime-8363894/) over 30+ years at Johns Hopkins University.
  Built by [Jonathan Sagir](https://www.linkedin.com/in/jonathansagir/).

  [![Plugin Version](https://img.shields.io/badge/plugin-v1.4.1-blue)](https://github.com/jsagir/mindrian-os-plugin)
  [![Commands](https://img.shields.io/badge/commands-51-green)](https://github.com/jsagir/mindrian-os-plugin)
  [![MCP Tools](https://img.shields.io/badge/MCP_tools-49-teal)](https://github.com/jsagir/mindrian-os-plugin)
  [![Agents](https://img.shields.io/badge/agents-8-orange)](https://github.com/jsagir/mindrian-os-plugin)
  [![Brain Nodes](https://img.shields.io/badge/brain_nodes-23K+-purple)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrianos-jsagirs-projects.vercel.app) |
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) |
  [Brain Access](https://mindrianos-jsagirs-projects.vercel.app/brain-access) |
  [Roadmap](https://mindrianos-jsagirs-projects.vercel.app/roadmap)

</div>

---

## Quick Start

```bash
# Add the marketplace (one time)
claude plugin marketplace add jsagir/mindrian-marketplace

# Install MindrianOS
claude plugin install mos@mindrian-marketplace
```

Larry starts talking. The Room starts listening. No setup required.

**Works on all three Claude surfaces:**

| Surface | How | What You Do |
|---------|-----|-------------|
| **Claude Code CLI** | Plugin (full power) | `claude plugin install mos@mindrian-marketplace` |
| **Claude Desktop** | MCP server | Add one line to `claude_desktop_config.json` |
| **Cowork** | Shared MCP | Same config, multi-user Data Room |

---

## What Is MindrianOS?

A Claude Code plugin built on **PWS (Problems Worth Solving)** -- the practical innovation methodology that turns undefined problems into fundable ventures.

Most startups fail because they solve the wrong problem. PWS teaches you to find problems worth solving *before* you build solutions. MindrianOS puts PWS in your terminal -- with Larry as your thinking partner, a self-organizing Data Room, and an embedded knowledge graph that grows with your venture.

---

## What You Get

| Capability | What It Does |
|-----------|-------------|
| **Larry** | AI teaching agent modeled on Prof. Aronhime. Shows his thinking with visual traces. Challenges your thinking, not your confidence. |
| **51 commands** | 26 PWS frameworks + 5 Brain-powered + 7 infrastructure + 3 intelligence + 2 meeting + 2 funding + admin + rooms + act + git integration |
| **49 MCP tools** | Every command works on Desktop and Cowork via hierarchical MCP router |
| **Data Room** | Self-organizing workspace: 8 DD sections + meetings/ + team/ + opportunity-bank/ + funding/ + personas/ |
| **Multi-Room Management** | Multiple projects simultaneously. Room registry, safe switching, context lock, header canary. `/mos:rooms` |
| **Autonomous Engine** | `/mos:act` -- Brain-driven framework selection with thinking traces, subagent isolation, chain mode (3-5 frameworks), dry-run |
| **CLI UI Ruling System** | 4-zone output anatomy, 5 body shapes, 12 glyphs, session start contract. Every interaction follows the same visual grammar. |
| **Admin Panel** | Hidden `/mos:admin` for Brain API key management. Self-teaching, consequence previews. |
| **De Stijl HTML Export** | Single-file export with 4 views: Mondrian grid, document reader, intelligence, Cytoscape knowledge graph |
| **Embedded knowledge graph** | Inter-room relationships grow as you file artifacts. Natural language queries via Larry. |
| **Meeting intelligence** | File transcripts, identify speakers, classify segments, track action items, detect convergence and contradictions |
| **AI Team Personas** | 6 De Bono Thinking Hat perspectives generated from YOUR room data |
| **Opportunity Bank** | Context-driven grant discovery. Larry reads your room and finds relevant opportunities. |
| **Funding Room** | 4-stage lifecycle tracking: Discovered > Researched > Applying > Submitted |
| **8 agents** | Larry, Brain, Grading, Research, Investor, Opportunity Scanner, Persona Analyst, Framework Runner |
| **PDF export** | Thesis, summary, report, profile, Minto meeting report |
| **Brain** | 23K nodes, 170K+ relationships. Optional MCP for enriched intelligence. |
| **Two-graph architecture** | Brain (methodology intelligence) + Room Graph (venture intelligence) |
| **Git integration** | Optional git tracking for room artifacts. Automatic commits on filing. |
| **KuzuDB backbone** | Automatic embedded graph database powering cross-room detection and proactive intelligence |
| **HSI pipeline** | Human Systems Integration pipeline for venture readiness assessment |
| **Cross-room detection** | Automatic pattern and contradiction detection across multiple rooms |
| **Proactive intelligence** | Larry surfaces gaps, convergence signals, and contradictions without being asked |

---

## How To Use MindrianOS

### On Claude Code CLI (full power)

```bash
# Install
claude plugin install mos@mindrian-marketplace

# Start a venture project
/mos:new-project

# Get help -- Larry recommends commands based on your stage
/mos:help

# Diagnose your problem type
/mos:diagnose

# File a meeting
/mos:file-meeting

# Discover grant opportunities
/mos:opportunities

# Track funding lifecycle
/mos:funding

# Generate AI team personas
/mos:persona

# Query your knowledge graph
/mos:query "What contradicts my pricing model?"

# See your room status
/mos:status
```

### On Claude Desktop / Cowork (MCP)

Add to your `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "mindrian-os": {
      "command": "node",
      "args": ["/path/to/MindrianOS-Plugin/bin/mindrian-mcp-server.cjs"],
      "env": {
        "MINDRIAN_ROOM": "/path/to/your/room"
      }
    }
  }
}
```

Restart Claude Desktop. All 49 tools appear automatically. Larry's personality is identical.

### Connect the Brain (optional, paid tier)

The Brain adds 23K nodes of teaching intelligence -- framework chain suggestions, calibrated grading, cross-domain pattern discovery.

**Request access:** [mindrianos-jsagirs-projects.vercel.app/brain-access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)

After approval, add to your config:

```json
{
  "mcpServers": {
    "mindrian-brain": {
      "url": "https://mindrian-brain.onrender.com/mcp",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

| Capability | Without Brain | With Brain |
|-----------|--------------|-----------|
| Larry personality | Full | Full |
| 26 methodology commands | All | All + graph-informed recommendations |
| Data Room intelligence | Keyword-based | + framework chain suggestions |
| Grading | Basic rubric | Calibrated against 100+ real projects |
| Cross-domain connections | Manual | Automatic pattern discovery |

---

## PWS Inside MindrianOS

PWS is the building blocks. MindrianOS is the operating system that runs them.

**5 Venture Stages. 26 framework commands. One intelligent progression.**

| Stage | What You're Doing | Key Commands |
|-------|------------------|--------------|
| **Pre-Opportunity** | Still looking for problems | `/mos:beautiful-question`, `/mos:explore-domains`, `/mos:diagnose` |
| **Opportunity Identified** | Understanding the problem deeply | `/mos:analyze-needs`, `/mos:build-knowledge`, `/mos:map-unknowns` |
| **Problem Validated** | Confirmed the problem is real | `/mos:challenge-assumptions`, `/mos:validate`, `/mos:root-cause` |
| **Solution Designed** | Building and testing solutions | `/mos:lean-canvas`, `/mos:structure-argument`, `/mos:systems-thinking` |
| **Investment Ready** | Preparing for funding | `/mos:grade`, `/mos:build-thesis`, `/mos:score-innovation` |

Larry knows which stage you're in and which framework you need before you do.

---

## Two Levels of Intelligence

MindrianOS uses two knowledge layers that work together:

```
Brain (remote, optional)           Room Graph (local, always on)
Methodology intelligence           YOUR venture's relationships
Framework chains + calibration     Grows as you file artifacts
Connects via API key               Embedded, zero server

         Brain tells you HOW to think
         Room Graph tells you WHAT your data says
         Together = far more powerful than either alone
```

**Room Graph edge types:**
- **INFORMS** -- this artifact references another section
- **CONTRADICTS** -- this artifact conflicts with an existing claim
- **CONVERGES** -- themes appear across 3+ sections
- **ENABLES** -- this artifact unblocks something elsewhere
- **INVALIDATES** -- this artifact makes an assumption stale

---

## Larry's Thinking Traces

Larry shows his reasoning -- not just the answer:

> **Larry's Thinking**
> Problem -- Wicked (8/10 characteristics)
> Stage -- Pre-Opportunity
> Method -- Bono Six Hats *divergent exploration needed*
> Chain -- Bono -> JTBD -> Market Sizing
> Filing -- problem-definition/
> *3 Brain connections - 2 cross-references*

Mode-adaptive: hidden when Larry is asking questions, full when teaching.

---

## Milestones

### v1.0 MVP (shipped 2026-03-22)
One-command install. Larry talks immediately. 26 methodology commands. Data Room with 8 sections. De Stijl dashboard with knowledge graph. PDF export. Brain MCP integration. Self-update system.

### v2.0 Meeting Intelligence (shipped 2026-03-24)
Meeting filing pipeline (paste/file/audio + Velma transcription). Speaker identification with 12 roles. Team room with profiles. Cross-meeting intelligence (convergence, contradictions, action items). Three-layer knowledge graph with timeline mode. Minto meeting-report PDF.

### v3.0 MCP Platform & Intelligence Expansion (shipped 2026-03-25)
- **Phase 10:** Shared core library (mindrian-tools.cjs)
- **Phase 11:** MCP server for Desktop/Cowork (6 hierarchical tools, 5 resources, 5 prompts)
- **Phase 12:** Brain hosting with API key management
- **Phase 13:** Opportunity Bank (context-driven grant discovery) + Funding Room (4-stage lifecycle)
- **Phase 14:** AI Team Personas (De Bono Six Hats from room intelligence)
- **Phase 15:** User Knowledge Graph (embedded graph, inter-room relationships, NL queries)
- **UX:** `/mos:` prefix, thinking traces, visual confirmations, room-aware status line

---

## Plugin Structure

```text
mindrian-os-plugin/
├── .claude-plugin/plugin.json  # Plugin manifest (v0.9.0)
├── bin/
│   ├── mindrian-tools.cjs      # Shared CLI entry point
│   └── mindrian-mcp-server.cjs # MCP server (Desktop/Cowork)
├── lib/
│   ├── core/                   # Shared modules (room-ops, state-ops, graph-ops, etc.)
│   ├── mcp/                    # MCP tools, resources, prompts, Larry context
│   └── parity/                 # CLI/MCP parity check (CI gate)
├── mcp-server-brain/           # Brain hosting server
├── commands/                   # 45 commands (/mos:*)
├── skills/                     # Auto-activated (room-passive, room-proactive, larry-personality, etc.)
├── agents/                     # Larry, Brain, Grading, Research, Investor, Scanner, Persona
├── hooks/                      # SessionStart, PostToolUse, PostWrite, Stop
├── scripts/                    # compute-state, build-graph, render-pdf, analyze-room, etc.
├── references/                 # PWS frameworks, meeting protocols, personas, opportunities
├── templates/                  # PDF templates (De Stijl styled)
├── dashboard/                  # Knowledge graph viewer + chat
├── pipelines/                  # ICM stage contracts
├── tests/                      # 8 test suites, 100+ assertions
└── CLAUDE.md                   # Architecture (Simon + ICM + Wicked Problems)
```

---

## Available Plugins

| Plugin | Version | Description |
|--------|---------|-------------|
| **mos** | v1.4.1 | MindrianOS powered by PWS. 51 commands, 49 MCP tools, 8 agents. Dual delivery (CLI + Desktop/Cowork). Data Room, Meeting Intelligence, Knowledge Graph, Opportunity Bank, Funding Room, AI Personas, Brain hosting, Git integration, KuzuDB backbone, HSI pipeline, cross-room detection, proactive intelligence. |

---

## Example: A Complete Session

```bash
# 1. Start a venture project
/mos:new-project
> "I'm exploring digital twins for agricultural supply chains in East Africa"

# 2. Larry diagnoses the problem type
/mos:diagnose
> Larry's Thinking: Wicked problem, Pre-Opportunity stage
> Recommends: /mos:explore-domains, /mos:beautiful-question

# 3. Explore the domain
/mos:explore-domains
> Larry maps adjacent innovation domains, files to room/problem-definition/

# 4. File a meeting with an advisor
/mos:file-meeting --file advisor-call.txt
> Larry identifies 3 speakers, classifies 12 segments, files to 4 room sections

# 5. Discover grant opportunities
/mos:opportunities
> Larry finds 3 relevant USAID grants based on your room context
> Confirm-first: "File these?" → Yes → room/opportunity-bank/

# 6. Generate AI team perspectives
/mos:persona
> 6 De Bono hats analyze your venture from different angles
> Black Hat (Risk): "Supply chain data quality is your biggest unknown"

# 7. Query your knowledge graph
/mos:query "What connects my problem definition to the advisor's feedback?"
> Larry translates to Cypher, returns graph relationships

# 8. Grade your venture
/mos:grade
> Honest assessment calibrated against 100+ real projects (Brain-powered)
```

---

## Links

- **Website**: [mindrianos-jsagirs-projects.vercel.app](https://mindrianos-jsagirs-projects.vercel.app)
- **Plugin Repo**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Brain Access**: [Request API Key](https://mindrianos-jsagirs-projects.vercel.app/brain-access)
- **PWS LinkedIn**: [Problems Worth Solving](https://www.linkedin.com/company/problem-solving-workspace/)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/) -- PWS methodology inventor
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/) -- MindrianOS developer

---

<details>
<summary><strong>Theoretical Foundations</strong></summary>

MindrianOS is grounded in established research:

| Source | Contribution to MindrianOS |
|--------|---------------------------|
| **Simon (1962)** | Architecture of Complexity -- room sections as near-decomposable subsystems |
| **Rittel & Webber (1973)** | Wicked Problems -- the Data Room manages ventures as wicked problems |
| **Van Clief & McDermott (2026)** | ICM -- folder structure as agentic architecture |
| **Tetlock (2015)** | Superforecasting -- intelligence layer as Bayesian updating |
| **Hughes (1983)** | Reverse Salients -- LazyGraph finds where venture understanding lags |
| **Knight (1921)** | Risk vs Uncertainty -- MindrianOS navigates uncertainty |
| **Ashby (1956)** | Law of Requisite Variety -- 26 frameworks match venture complexity |
| **De Bono (1985)** | Six Thinking Hats -- AI personas as structured perspective lenses |

</details>

---

## License

Proprietary. Copyright Jonathan Sagir & PWS / Mindrian.
