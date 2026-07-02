<div align="center">
  <img src="https://mindrian-os.com/logo_dark.svg" alt="MindrianOS" width="200" />

  # MindrianOS

  **A thinking partner that sits above your AI.**

  When you are working a problem worth solving and cannot yet name what is missing, MindrianOS sequences the right method at the right moment, pushes back when your reasoning has gaps, and remembers every decision across sessions.

  Powered by PWS (Problems Worth Solving), an innovation methodology built and tested through 20 years of teaching by Prof. Lawrence Aronhime.
  Engineered by Jonathan Sagir.

  [![Version](https://img.shields.io/badge/version-1.15.1-1E3A6E)](https://github.com/jsagir/mindrian-os-plugin/blob/main/CHANGELOG.md)
  [![License](https://img.shields.io/badge/license-BSL_1.1-C8A43C)](https://github.com/jsagir/mindrian-os-plugin/blob/main/LICENSE)
  [![Surfaces](https://img.shields.io/badge/CLI_+_Desktop_+_Cowork-2D6B4A)](https://github.com/jsagir/mindrian-os-plugin)

  [Website](https://mindrian-os.com) &middot;
  [Plugin Repo](https://github.com/jsagir/mindrian-os-plugin) &middot;
  [Brain Access](https://mindrian-os.com/brain-access)
</div>

---

## The answer first

> A structured method layer that sits above the model. You talk to Larry about what you are working on. MindrianOS turns the conversation into a structured room, sequences the right framework for where you are, pushes back when your confidence outruns your evidence, and remembers every decision so nothing you learned is lost.

You do not learn a tool. You talk. The room takes shape underneath the conversation.

---

## Four jobs it does for you

- **Find the problem.** Larry reframes what you are working on before you try to solve it, so you spend effort on the real problem, not the first one you saw.
- **Show what you missed.** Every new entry is compared against everything already in the room. Contradictions, gaps, and cross-project connections surface on their own.
- **Build what you could not alone.** The right framework at the right stage, chained intelligently, across more domains than one mind can hold.
- **Defend what you decided.** Every decision and the reason behind it becomes working memory you can stand behind weeks later.

---

## What it does

Larry is the AI thinking partner. Larry asks questions, suggests methods, and files your conversation into a Data Room organized by venture stage (problem, market, solution, team, money, IP, meetings, opportunities).

Every time you add something new, the system scans the rest and surfaces what just changed, what contradicts what, what connects to what, what is now missing. You decide: APPROVE, REJECT (with a reason), or DEFER. Your reason becomes part of the room. The next scan is smarter.

A conversation that becomes a room. A room that surfaces what you cannot see on your own.

---

## Why not just talk to Claude, ChatGPT, or Gemini directly?

You can. MindrianOS is not instead of them. It is the layer that makes one of them remember, judge, and hold you to your own reasoning. It adds the four things a raw model structurally cannot be:

- **It remembers.** Your venture lives in a room that persists across every session. The contradiction you found three weeks ago is still there, still checking today's input.
- **It knows when.** Not just which framework exists, but which one fits this stage and this problem, chained in the right order, calibrated from decades of teaching.
- **It pushes back.** It blocks you when the evidence is thin and surfaces the conflict between your pricing and your market. A co-founder tells you when you are wrong; a chatbot tells you that you are brilliant.
- **It keeps your data yours.** The teaching that travels is generic methodology. Your specifics never leave your machine. Smarter-from-the-world intelligence without becoming the product.

A raw AI is the engine. MindrianOS is the operating system around it. For a one-off question, use the engine. For a venture you carry for months, you want the OS.

---

## Install

### npm (one line, recommended)

```bash
npx @mindrian_os/cli
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

Restart Claude Code. Larry starts talking. Built for people who have never opened a terminal; full guide at [the install page](https://mindrian-os.com/docs/install).

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

The Brain is a shared teaching graph that connects your findings across projects. Two stores: one for connections, one for meanings. Connecting it makes Larry sharper. Not connecting it is fine; the system still teaches you.

The Brain never sees your room. Brain queries carry methodology questions only. Your venture stays on your machine.

Request access: [mindrian-os.com/brain-access](https://mindrian-os.com/brain-access)

---

## Pricing

Free plugin. It requires a paid Claude plan (Claude Pro, $20/mo, or higher) because it runs on top of Claude. The Brain is an optional add-on.

---

## Works everywhere Claude works

| Surface | What you do |
|---------|-------------|
| **Claude Code CLI** | `npx @mindrian_os/cli`. Full power. Hooks fire. You own the folder. |
| **Claude Desktop** | The plugin auto-registers as an MCP server. Talk to Larry, see the room. |
| **Cowork** | Same plugin, shared room, team-wide. |

---

## Links

- **Website**: [mindrian-os.com](https://mindrian-os.com)
- **Plugin Repo + Changelog**: [github.com/jsagir/mindrian-os-plugin](https://github.com/jsagir/mindrian-os-plugin)
- **Brain Access**: [Request API Key](https://mindrian-os.com/brain-access)
- **Prof. Lawrence Aronhime**: [LinkedIn](https://www.linkedin.com/in/lawrence-aronhime-8363894/)
- **Jonathan Sagir**: [LinkedIn](https://www.linkedin.com/in/jonathansagir/)

---

Install MindrianOS. Start thinking with Larry.

## License

Source-available (BSL 1.1), not open source. Copyright Jonathan Sagir and PWS / Mindrian.
