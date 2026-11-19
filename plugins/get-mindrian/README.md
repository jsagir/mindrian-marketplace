# Get MindrianOS

You want MindrianOS (Larry, a thinking partner for Problems worth Solving, and a Data Room on your own computer) and you do not want to work out the install yourself. This plugin carries one skill that does the install for you, or walks you through it one step at a time when it cannot run commands, and helps when a step fails.

## Install

In Claude Code (one step, Claude Code 2.1.275 or later):

```
/plugin install get-mindrian --marketplace jsagir/mindrian-marketplace
```

From a terminal (Claude Code 2.1.292 or later; on an older version run `claude plugin marketplace add jsagir/mindrian-marketplace` first):

```bash
claude plugin install get-mindrian --marketplace jsagir/mindrian-marketplace
```

The CLI form with the marketplace already added is `claude plugin install get-mindrian@mindrian-marketplace`.

Then say: set up MindrianOS

In Claude Desktop: open Customize, then Plugins, add the marketplace `jsagir/mindrian-marketplace`, install Get MindrianOS, then say: set up MindrianOS

## No install at all

Paste this sentence into any AI assistant (Claude, ChatGPT, Gemini, Codex and others):

```
Read https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/SKILL.md and set up MindrianOS for me.
```

An assistant that can run commands installs MindrianOS. An assistant that cannot run commands walks you through it one step at a time.

## For maintainers

`skills/get-mindrian/SKILL.md` is the one source of the MindrianOS install procedure. Its path never moves, because the sentence above and the website copy it by URL. The plugin repo `AGENT-INSTALL.md` only points to it. The catalog entry for this plugin is written by `scripts/release-lib/get-mindrian-entry.cjs` in the plugin repo, never by hand.
