<div align="center">
  <img src="https://mindrianos-jsagirs-projects.vercel.app/logo_dark.svg" alt="MindrianOS" width="200" />

  # MindrianOS

  **When you are walking through a problem worth solving and you cannot yet name what is missing, MindrianOS is the thinking partner that walks beside you.**

  Powered by PWS (Problems Worth Solving), an innovation methodology built and tested through 20 years of teaching by Prof. Lawrence Aronhime.
  Engineered by Jonathan Sagir.

  [![Version](https://img.shields.io/badge/v1.13.0-The_Closed_Loop-1E3A6E)](https://github.com/jsagir/mindrian-os-plugin)
  [![License](https://img.shields.io/badge/license-BSL_1.1-C8A43C)](https://github.com/jsagir/mindrian-os-plugin/blob/main/LICENSE)
  [![Surfaces](https://img.shields.io/badge/CLI_+_Desktop_+_Cowork-2D6B4A)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrianos-jsagirs-projects.vercel.app) ·
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) ·
  [Brain Access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)
</div>

---

## The answer first

> When you talk to Larry about what you are working on, MindrianOS turns the conversation into a structured room, remembers your decisions across sessions, and surfaces the contradictions you would otherwise miss.

You do not learn a tool. You talk. The room takes shape underneath the conversation.

---

## What it does

Larry is the AI thinking partner. Larry asks questions, suggests methods, and files your conversation into a Data Room organized by venture stage (problem, market, solution, team, money, IP, meetings, opportunities).

Every time you add something new, the system scans the rest and surfaces what just changed, what contradicts what, what connects to what, what is now missing. You decide: APPROVE, REJECT (with a reason), or DEFER. Your reason becomes part of the room. The next scan is smarter.

A conversation that becomes a room. A room that surfaces what you cannot see on your own.

---

## What v1.13.0 delivers (The Closed Loop)

- **Larry leads turn one.** Conversation, not a command menu.
- **Your first sentence becomes a populated room** in about 30 seconds.
- **Tensions persist across sessions.** Larry remembers what was unresolved.
- **Every conversation produces a real artifact.**
- **Decisions teach the system.** Your reasons become working memory.

---

## Install

### npm (one line, recommended)

```bash
npx @mindrian_os/install
```

### Plugin marketplace

```bash
claude plugin marketplace add jsagir/mindrian-marketplace
claude plugin install mos@mindrian-marketplace
```

### Shell

```bash
curl -sL https://raw.githubusercontent.com/jsagir/mindrian-os-plugin/main/install.sh | bash
```

Restart Claude Code. Larry starts talking.

---

## A first session

```bash
/mos:new-project        # tell Larry what you are exploring
/mos:beautiful-question # reframe the problem as a question
/mos:file-meeting       # paste a transcript, Larry files it
/mos:query "what contradicts my pricing model?"
```

Five minutes in, the room has more structure than a folder you spent an hour organizing. If you do not know which command to run, just talk. Larry routes you.

---

## The Brain (optional)

The Brain is a methodology repository that suggests connections, contradictions, and gaps no single mind can hold. Connecting it makes Larry sharper. Not connecting it is fine; the system still teaches you.

The Brain never sees your room. Brain queries carry methodology questions only. Your venture stays on your machine.

Request access: [mindrianos-jsagirs-projects.vercel.app/brain-access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)

---

## Works everywhere Claude works

| Surface | What you do |
|---------|-------------|
| **Claude Code CLI** | `npx @mindrian_os/install`. Full power. Hooks fire. You own the folder. |
| **Claude Desktop** | The plugin auto-registers as an MCP server. Talk to Larry, see the room. |
| **Cowork** | Same plugin, shared room, team-wide. |

---

## Links

- **Website**: [mindrianos-jsagirs-projects.vercel.app](https://mindrianos-jsagirs-projects.vercel.app)
- **Plugin Repo + Changelog**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Brain Access**: [Request API Key](https://mindrianos-jsagirs-projects.vercel.app/brain-access)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/)
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/)

---

## License

Source-available (BSL 1.1), not open source. Copyright Jonathan Sagir and PWS / Mindrian.
