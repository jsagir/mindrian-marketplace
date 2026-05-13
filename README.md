<div align="center">
  <img src="https://mindrianos-jsagirs-projects.vercel.app/logo_dark.svg" alt="MindrianOS" width="160" />

  # MindrianOS

  **When you are walking through a problem worth solving and you cannot yet name what is missing, MindrianOS is the thinking partner that walks beside you.**

  Powered by PWS, the practical innovation methodology developed by
  [Prof. Lawrence Aronhime](https://www.linkedin.com/in/lawrence-aronhime-8363894/) over 30+ years at Johns Hopkins University.
  Built by [Jonathan Sagir](https://www.linkedin.com/in/jonathansagir/).

  [![Version](https://img.shields.io/badge/v1.13.0-The_Closed_Loop-blue)](https://github.com/jsagir/mindrian-os-plugin)
  [![License](https://img.shields.io/badge/license-BSL_1.1-orange)](https://github.com/jsagir/mindrian-os-plugin/blob/main/LICENSE)
  [![Surfaces](https://img.shields.io/badge/works_on-CLI_+_Desktop_+_Cowork-brightgreen)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrianos-jsagirs-projects.vercel.app) |
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) |
  [Brain Access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)

</div>

---

## The job you are trying to do

You have a half-formed idea. A research direction. A venture worth building. The problem is real, but it is undefined, and most of the time you are not sure whether the thing you are pursuing is the right problem at all.

You do not need another notes app. You need someone who can ask the question that reframes the problem, point at the assumption you stopped checking, and remember what you decided last Tuesday so you do not have to.

That is what MindrianOS does.

---

## What it does

You talk to Larry. Larry is the AI thinking partner. Larry asks questions, suggests methods, and quietly files your conversation into a Data Room. The Data Room is a folder of notes organized by venture stage (problem, market, solution, team, money, IP, meetings).

Every time you add something new, the system scans the rest of the room and tells you what just changed. What contradicts what. What connects to what. What is now missing. What you stopped checking weeks ago and never came back to.

You decide what to keep. APPROVE, REJECT (with a reason), or DEFER. Your reason becomes part of the room's memory, so the system gets smarter about you.

That is the whole product. A conversation that becomes a room. A room that surfaces what you cannot see on your own.

---

## How to install

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

Restart Claude Code. Larry starts talking. The Data Room starts listening.

---

## A first session

```bash
/mos:new-project        # tell Larry what you are exploring
/mos:beautiful-question # reframe the problem as a question
/mos:file-meeting       # paste a transcript, Larry files it
/mos:query "what contradicts my pricing model?"
```

That is enough to feel what the room does. Five minutes in, the room has more structure than a folder you spent an hour organizing.

If you do not know which command to run, just talk. Larry routes you to the right one.

---

## The Brain (optional)

The Brain is a remote teaching graph: 30+ years of PWS classroom wisdom about which framework chains to which, when, and why. Connecting it makes Larry's suggestions sharper. Not connecting it is fine; the system still works.

What the Brain never sees: your room, your notes, your meetings, your decisions. Brain queries carry methodology questions only. Your venture stays on your machine.

Request access: [mindrianos-jsagirs-projects.vercel.app/brain-access](https://mindrianos-jsagirs-projects.vercel.app/brain-access)

---

## Works everywhere Claude works

| Surface | What you do |
|---------|-------------|
| **Claude Code CLI** | `npx @mindrian_os/install`. Full power. Hooks fire, room is on disk, you own it. |
| **Claude Desktop** | The plugin auto-registers as an MCP server. Talk to Larry, see the room. |
| **Cowork** | Same plugin, shared room, team-wide. |

---

## Links

- **Website**: [mindrianos-jsagirs-projects.vercel.app](https://mindrianos-jsagirs-projects.vercel.app)
- **Plugin Repo**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Changelog**: [CHANGELOG.md](https://github.com/jsagir/mindrian-os-plugin/blob/main/CHANGELOG.md)
- **Brain Access**: [Request API Key](https://mindrianos-jsagirs-projects.vercel.app/brain-access)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/)
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/)

---

## License

Source-available (BSL 1.1), not open source. Copyright Jonathan Sagir and PWS / Mindrian.
