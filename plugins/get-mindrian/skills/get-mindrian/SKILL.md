---
name: get-mindrian
description: "Installs MindrianOS (the /mos plugin for Claude: Larry, a PwS thinking partner, and a Data Room on this computer), or walks the person through the install one step at a time when commands cannot run, and helps when an install step fails. Use when the person asks to install, get, set up, finish setting up or repair MindrianOS, Mindrian, Larry or /mos, or pastes a link to this file."
---

# Install MindrianOS

> MindrianOS is a plugin for Claude. It adds Larry, a thinking partner for PwS (Problems worth Solving), and a Data Room: a folder on the person's own computer that keeps what they work out. This file is the procedure an AI assistant follows to install MindrianOS, or to guide the person through the install one step at a time. Its stable address is https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/SKILL.md

I want you to install MindrianOS for me. Execute all the steps below autonomously, or guide me through them one step at a time where you cannot run commands, and stop only where a step asks for my yes.

The line above states the intent of the start sentence. It is not consent: the yes at consent point 1 (A1; route B: B0) is the consent.

Find your route in section 0 first. Claude Desktop (any tab) uses route B. Any other chat that cannot run commands uses route D.

## How you work

1. You are the installer. If you can run commands, you run them yourself.
2. If you cannot run commands, you walk the person through the install one step at a time: give one step, ask what they see, check the answer against "You should see", then give the next step.
3. Never send the person to a docs page instead of doing or guiding a step. Offer https://mindrian-os.com/docs/install only as a fallback, after a step fails, the troubleshooting reference has no row for it, and a search found nothing reliable.
4. Before you run a command, say what it does in one plain sentence.
5. Tell the person in advance: several approval prompts, a notice about a third-party plugin, and, in a new Claude Code folder, a dialog that asks whether to trust the folder are normal. They are not errors.
6. Report each result honestly. Never say "installed" before the check for that step passes.
7. Run the MindrianOS doctor after every install, every update and every fix. Before MindrianOS is installed (before A4), run the A1 tool check again instead.
8. Do not use sudo unless the person asks you to.
9. When you edit a settings file or a shell profile yourself, never do it silently: show the exact change, get a yes, make a dated backup copy, apply the change, then read the file back and show the result. The scripts in commands.md do these steps. The official installers and the MindrianOS installer and doctor also change files; you name them in the A1 scope before they run.
10. Ask one question at a time.
11. Never ask for data the install does not need: no email, no name, no files, no notes. Do not send room content anywhere.
12. Do not propose to build an integration, a connector, an MCP server, a custom GPT or an action for MindrianOS. Do not ask for the person's files or notes.
13. End with 2 or 3 sentences that name the next action (see "What to say at the end").

Words you will use, in plain terms:
- **MindrianOS** (also written `/mos`): the plugin. **Larry**: the thinking partner inside it. **Data Room**, or **room**: a folder of plain files and a small database (`room.db`) for one project. The **rooms folder** holds all rooms.
- **Marketplace**: a catalog of plugins. MindrianOS lives in the marketplace `jsagir/mindrian-marketplace`.
- **mos** is the MindrianOS plugin for Claude Code in a terminal. **mos-desktop** is the MindrianOS plugin for the Claude Desktop app. They are the same product for two apps.
- **Claude Code**: Claude in a terminal. **Claude Desktop**: the Claude app for Mac and Windows. Its **Chat** tab is a normal chat; its **Cowork** tab lets Claude work with folders on this computer; its **Code** tab runs Claude Code inside the app.
- **Theo**: the remote methodology graph that Larry asks. It gets only generic method questions (a framework name or a type of problem), never room content.
- **Room registry**: the file `<rooms folder>/.rooms/registry.json`, which lists the rooms. **Console account**: a Claude account for the Claude API (console.anthropic.com).
- **Larry's sign**: every Larry reply opens with one colored square (🟦 🟥 🟨 ⬛ or ⬜) and the label `Larry | MindrianOS`; the first reply in a conversation also says "I'm Larry, MindrianOS's PwS thinking partner". A reply without the sign is the plain host, not the plugin. This holds in Claude Code, Cowork and the Code tab.
- **Onboarding**: the command `/mos:onboard`. Its Step 4 asks "who are you" and builds a persona file on this computer (`~/.mindrian-user.md`); the person may choose Skip. **The first room** is made only by `/mos:ignite`, which onboarding offers, or by `/mos:rooms new <name>`.
- **Eureka**: an optional engine that finds non-obvious links across a room. It needs uv and Python.
- **Doctor**: the MindrianOS self-check. It prints one line per check (a ✓ marks a healthy line) and a Summary line (healthy / drift / warnings). It can repair what it finds.
- **Shell** or **terminal**: the text window where commands run. **PATH**: the list of folders where the shell looks for programs. A program that is installed but not on PATH gives "command not found".
- **The start sentence**: `Read https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/SKILL.md and set up MindrianOS for me.`
- **The resume sentence**: `Read https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/SKILL.md and continue the MindrianOS install.` A new session that gets it starts at A0, finds what is done from the files on disk, and continues.

## Files of this skill

- This file: https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/SKILL.md
- Exact commands for each system: https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/references/commands.md (open it when a step needs an exact command for this system).
- Troubleshooting: https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/references/troubleshooting.md (open it only when a step fails).

If you run as the installed get-mindrian skill, the same files sit next to this SKILL.md, in `references/`. Read them from there first.
If you cannot open these files (no browsing or fetch tool), say so. Then use route B (clicks in the app, plus one check command in a terminal that B3 spells out), or ask the person to open the commands.md address in their browser and paste the block for their system. For a failure, use the Troubleshooting table at the end of this file; if no row fits, ask the person to open the troubleshooting.md address and paste the row that matches, else give the honest unknown.

## OBJECTIVE

Get the person from nothing to MindrianOS installed, checked by the doctor, set up with their choices, and a first room made with Larry, on the app they have.

## DONE WHEN

Route A (Claude Code in a terminal), every item is true:
- `claude --version` prints a version, and `claude update` prints `Claude Code is up to date (<version>)` or `Claude is up to date!`. If it printed a line that ends with `to version <new version>`, run it once more and expect the up-to-date line.
- The status check in commands.md prints `PASS A4`: the installed `mos@mindrian-marketplace` version equals the `mos` version in the local catalog copy.
- The read-only doctor run of step A5 exits 0 and its Summary shows 0 drift and 0 warnings, or each drift or warning line left after "When a step fails" is reported to the person, by its exact line, as open. (Drift: a part of the install that differs from what MindrianOS expects; `--fix` repairs most of it.)
- The status check prints `PASS A7 auto-update on`, or the person said no.
- The status check prints `PASS A8 rooms folder exists` for the chosen folder. If it is not `~/MindrianRooms`, `env.MINDRIAN_ROOMS_HOME` in `~/.claude/settings.json` names it.
- The status check prints `PASS A8 shortcut`, or the person said no.
- If the person said yes to Eureka: the doctor line that starts with `Eureka engine:` says `ready` (for example `Eureka engine: ready for the graph tools`).
- After the restart: `PASS A9 onboarding marker`, and `PASS A9 persona file` or the person chose Skip in onboarding Step 4.
- `PASS A9 first room`: the room registry has at least one room.

Route C (Codex or another agent with a shell): every route A item up to A8 passes from your shell, and you gave the A9 hand-over. The A9 items are proved by the Claude Code session (A10), or by your status check if the person comes back.

Routes B (Claude Desktop) and D (chat with no shell): the same end state, checked by the person's answer to "what do you see":
- In Customize, Plugins, the MindrianOS entry shows as installed, and a reply in the chosen tab carries Larry's sign (B8).
- In Cowork or the Code tab, `/mos:doctor` shows a Summary line with 0 drift and 0 warnings, or each such line is reported as open (the same rule as route A).
- Updates: Sync automatically is on, or the person said no.
- Larry asked "who are you" (onboarding Step 4) and the person answered or chose Skip.
- Larry made the first room and named its folder.
- Route D on the terminal path: the person pasted the output of each route A check, and you confirmed it.

Other end states, all honest: you stopped because access was refused (see "Access refused"); the person said no to a required step, or the plan does not include Claude Code, Cowork or the Code tab (see "If the person says no"); route C handed over to Claude Code and the A9 items are not yet proved.

## TODO

- [ ] Find your route (section 0).
- [ ] Know the system (section 1).
- [ ] Get the yes at consent point 1 (scope and missing tools).
- [ ] Install or update the tools and MindrianOS, and prove it with the doctor.
- [ ] Get the yes at consent point 2 and set the choices: updates, rooms folder, shortcut, Eureka.
- [ ] Hand over: restart, onboarding with the persona, the first room.

Routes B and D map the same list: section 1 comes before B0, consent point 1 is B0, the doctor is B9, the choices are B7 (rooms folder) and B11 (updates). Route B offers no shortcut and no Eureka.

## 0. Find your route

You can run commands if you have a shell or terminal tool and `echo ok` prints `ok`.

| You are | Route |
|---|---|
| Claude Code in a terminal (also the VS Code or JetBrains panel: A1 then installs the standalone `claude`) | A |
| Claude Desktop: Chat, Cowork or the Code tab, also when you run as the get-mindrian skill inside Desktop | B (in the Code tab, if `echo ok` prints `ok`, run the B3 check yourself) |
| Codex, Cursor or another agent with a shell | C |
| ChatGPT, Gemini or any other chat with no shell | D |

If the person pasted the resume sentence, start at A0 (route A or C), or ask which step they last saw (route B or D) and continue from there.

## 1. Know the system

You must know the system and its version before the first install command. Keep the result for every later command and every search.

With a shell, detect it yourself:
- macOS, Linux and WSL: `uname -s` (Darwin is macOS), `uname -m` (arm64 or x86_64; on a Mac, x86_64 means the terminal runs under Rosetta), `sw_vers -productVersion` (macOS version), `cat /etc/os-release` (Linux name and version), `grep -i microsoft /proc/version` (a match means WSL: Linux inside Windows, with its own PATH and its own Node), `cmd.exe /c ver` (the Windows version, from WSL), `echo $SHELL`.
- Windows PowerShell: `$PSVersionTable.PSVersion`, `[System.Environment]::OSVersion.VersionString`, `$env:PROCESSOR_ARCHITECTURE`.
- Git Bash on Windows: `uname -s` prints MINGW or MSYS. Claude Code on native Windows often runs its own shell in Git Bash. Then the system is Windows for every table and every choice; follow commands.md, "Git Bash on Windows".
- The prompt `PS C:\>` is PowerShell. A plain `C:\>` is CMD.

Without a shell, ask once, in plain words, with a hint, and ask for the version in the same question: "Which computer are you on, and which version? On a Mac (apple logo in the top-left corner), click the apple, then About This Mac: it shows for example macOS 15. On Windows (a Start button with four squares), press the Windows key, type winver and press Enter: it shows Windows 10 or Windows 11. If you cannot find the version, just tell me Mac or Windows." If there is no answer, assume Windows and add the one-line Mac and Linux variant to each step. Never ask twice. If the version is still unknown, leave it out of a search query and say so.

## 2. Look things up the right way

Use your own web search or browsing tool, if you have one, for dependency and platform questions: how to get Claude Code on this system, Node.js, Python, uv, Git, the terminal, PATH, the current Claude Desktop labels, and any exact error string. Typical triggers: install, update, error, not recognized, command not found, PATH, npm, npx, node, Claude Code, PowerShell, terminal, shell, CMD, Windows, macOS, Linux, WSL, Homebrew, Xcode, Gatekeeper, permission, EACCES, ENOTEMPTY, execution policy, EBADENGINE, version, VS Code, JetBrains, WinGet.
- Search when the step of the matching troubleshooting row fails, or when no row matches.
- Prefer the official sources: code.claude.com/docs (Claude Code), claude.com/docs (Claude Desktop, Cowork and plugins), nodejs.org, docs.astral.sh/uv, python.org, and git-scm.com for Git.
- Put the system and its version from section 1 in the query, and quote the exact error text. Example: `"npx : The term 'npx' is not recognized as the name of a cmdlet, function, script file, or operable program." Windows 11 PowerShell site:nodejs.org`.
- MindrianOS facts come only from this skill and its reference files, never from the open web.
- A command you found by search still needs a yes before you run it, the same as the A1 and A7 consent points.
- If you have no search tool, say so in one sentence, give the best known step from the troubleshooting reference, and tell the person to paste the exact error line into a search engine.

## Route A: Claude Code in a terminal

**A0. Resume check.** Run `node --version` and `claude --version`. If `node` is not found or is older than 22.18.0, go to A1 (the status check needs Node). Else run the status check from commands.md. All are read-only. Only if the status check prints `PASS A4`, also run the read-only doctor (`npx --yes @mindrian_os/cli doctor`). Skip every step whose check passes. Only if the person pasted the resume sentence, or `PASS A4` already shows: for each FAIL line that allows a "no" (auto-update, shortcut, and the persona file once `PASS A9 onboarding marker` shows), ask once whether they said no before; a "no" counts as done. Tell the person which steps are left. If the only FAIL lines left are A9 lines or the auto-update line (way b), go to A10 (route C: go to route C step 4).

**A1. Consent point 1.** Use the A0 results, or run the read-only tool checks: `node --version` (MindrianOS needs 22.18.0 or newer) and `claude --version` (Claude Code must be on PATH). uv and Python are only for the optional Eureka engine: do not check or install them now; A7 asks about Eureka.
Then show the scope in 3 lines and the list of missing tools with the command for each, from commands.md. Get one yes. The scope:
- It changes: Claude Code itself (`claude update`), Claude Code's plugin list (it adds the marketplace `jsagir/mindrian-marketplace`, which Claude Code also records in `~/.claude/settings.json`, and the plugin `mos@mindrian-marketplace`), files under `~/.claude/` that the MindrianOS installer and its doctor manage, and the missing tools you list.
- It never: edits the person's projects, sends room content anywhere, uses sudo, or applies a choice of A7 without its separate yes.
- Profiles and admin prompts: nvm and uv add their folder to PATH in the shell profile, and the PATH fix for Claude Code may add one line (each backed up first). On Windows the Node.js Installer shows an administrator prompt (on macOS, Homebrew and nvm show none). Name each one that applies.
Claude Code needs a paid Claude plan (Pro, Max, Ultra, Team or Enterprise) or a Console account. The free claude.ai plan does not include it. Say this before you install Claude Code.

**A2. Install the missing tools.** Use the exact command for the system from section 1, from commands.md:
- Node.js: first run `which -a node` and pick the method by where an old copy lives (commands.md, "Before you install"). Else Homebrew on a Mac that has it, else nvm on macOS, Linux and WSL; the Windows Installer on Windows (a guided step: the person runs it). After the install, `which -a node` (Windows: `where.exe node`) must list the new install first. No administrator rights on Windows: see troubleshooting.
- Claude Code: the official native installer. If its output says that `~/.local/bin` is not in your PATH, offer the PATH fix (commands.md) with its own yes now, before the login. Then the person logs in once (commands.md, "Log in") and tells you when Claude Code shows its prompt; that answer is the check. You cannot do the login for them. Do the login before A4.
Your shell tool does not reload the shell profile. Until the restart in A9, start each later command with the prefix from commands.md, "Agent shell prefix", for each tool you installed. Then run the check again. Continue only when Node and `claude` both pass.
Windows Installer for Node.js: it asks the person to close every terminal window, which ends this session. Before they close it, give them the resume sentence and tell them to paste it into Claude Code in a new terminal.

**A3. Update Claude Code.** Run `claude update` and show the version line. If it ends with `to version <new version>`, run it once more and expect the up-to-date line.

**A4. Install MindrianOS.** Run `npx --yes @mindrian_os/cli --no-eureka`. It adds the marketplace, refreshes it, installs `mos@mindrian-marketplace` and brings it to the current build. `--yes` lets npx download the installer without a question; the A1 yes covers it. `--no-eureka` keeps the optional engine out of this step. "Already installed" is fine. Then run the status check and confirm `PASS A4`. If it prints `FAIL A4` with an installed version that differs from the catalog, run `npx --yes @mindrian_os/cli update`, then the status check again.
If the install fails, run the fallback yourself from the shell: `claude plugin marketplace add jsagir/mindrian-marketplace`, then `claude plugin install mos@mindrian-marketplace`. Only if that also fails, ask the person to type inside Claude Code: `/plugin marketplace add jsagir/mindrian-marketplace`, then `/plugin install mos@mindrian-marketplace`.

**A5. Repair and verify.** Run `npx --yes @mindrian_os/cli doctor --fix`, then `npx --yes @mindrian_os/cli doctor`. The first run repairs what it can. The second run is read-only, and it is the result you report: read out its Summary line in plain words. If a line has no ✓ or the Summary shows a warning, go to "When a step fails". Do not patch plugin files by hand.

**A6. Key check.** Today the installer asks for no key. If any output of A4, A5 or a later update says that a key or an entitlement is missing, invalid or refused, go to "Access refused".

**A7. Consent point 2: the choices card.** Show one card with these recommended defaults. The person accepts the choices with one word ("yes"), or changes any line. The card yes picks the choices. For each settings change you then show the exact change (the `preview` output of the script) and get one more yes before you write it.
1. Auto-update on. Third-party marketplaces do not auto-update by default. Two ways: (a) you apply `"autoUpdate": true` to the `mindrian-marketplace` entry in `~/.claude/settings.json` with the settings script in commands.md; or (b) after the restart, the person types `/plugin`, opens the Marketplaces tab, selects `mindrian-marketplace` and turns auto-update on. Use (a) first. If the script prints `NO ENTRY`, use (b) at A10.
2. Rooms folder: `~/MindrianRooms` (Windows: `%USERPROFILE%\MindrianRooms`). This is the plugin default, so there is nothing else to set. Warn: do not pick a folder that OneDrive, iCloud Drive, Dropbox or Google Drive syncs; a sync tool can copy a room's database while it is in use, and that copy can be corrupt. On a Mac, Desktop and Documents are synced when the iCloud Drive option for Desktop and Documents folders is on. If the person wants Documents, ask whether that option is on (Apple menu, System Settings, the person's name, iCloud, iCloud Drive); if it is on or they do not know, recommend `~/MindrianRooms`. If the person still wants another place after the warning, it is their choice: use a folder named `MindrianRooms` inside it (for example `~/Documents/MindrianRooms`), set `env.MINDRIAN_ROOMS_HOME` with the settings script, and name the sync risk again in the end summary.
3. A shortcut to the rooms folder on the Desktop (also Quick Access on Windows; on a Mac the Finder sidebar is an optional by-hand step). Commands per system are in commands.md.
4. Eureka engine: no (the default). "Do you want the optional Eureka engine now? Its setup downloads a model and installs Python packages, and it can install uv and Python itself. You can add it later."

**A8. Apply each choice and prove it.**
- Auto-update: run the settings script with `preview`, show it, get the yes, run it with `apply`. Confirm `PASS A7 auto-update on`.
- Rooms folder: create only the empty folder (commands.md, "Rooms folder"). Never create a room, a ROOM.md or a registry entry yourself; the first room comes only from `/mos:ignite` or `/mos:rooms new <name>` in A10. Confirm `PASS A8 rooms folder exists`.
- Shortcut: run the block for the system with the chosen folder, then its check line; the block's check line decides. If the block fails, guide the person to make it by hand (commands.md). It is optional.
- Eureka yes: run `npx --yes @mindrian_os/cli --eureka --yes` (the second `--yes` answers the installer's Eureka question; the A7 yes covers it). The engine setup prints a card and can install uv and Python itself, so do not check `python3` first. Then run the doctor and check the `Eureka engine:` line. Eureka no: tell the person they can add it later inside Claude Code with `/mos:eureka enable engine --setup`.
- Run the doctor again (A5) after the choices.

**A9. Restart hand-over.** Plugins load when a session starts. This session ends at the restart, so this step gives one instruction that survives it. Say, in one message:
1. "Copy this sentence now: [the resume sentence, written out in full]."
2. "Quit Claude Code (type /exit). Open a new terminal and run [the line for the shell]. When Claude Code starts, paste the sentence as your first message. The new session checks what is done and walks you through the last steps."
The line for the shell: macOS, Linux, WSL and Git Bash `cd ~/MindrianRooms && claude`; PowerShell `cd "$env:USERPROFILE\MindrianRooms"; claude`; CMD `cd /d "%USERPROFILE%\MindrianRooms" && claude`. Use the chosen folder if it is not the default.

**A10. In the new session.** The person pasted the resume sentence, and A0 found only A9 lines or the auto-update line left (any other FAIL: do that step first). Guide one step at a time, and check each answer:
1. Ask whether a line that starts with `⬡ MindrianOS` shows at the bottom of the terminal. If not, ask the person to type `/mos:doctor --statusline-visibility`, then `/mos:doctor --fix`. The line is not required for the rest of the steps.
2. If `A7 auto-update on` is FAIL and the person did not say no, run the auto-update script with `preview`; on `NO ENTRY`, ask once whether they want the `/plugin` toggle (way b), guide it, then run the status check.
3. Ask the person to type `/mos:onboard`. In Step 4, Larry asks "who are you"; the person answers or chooses Skip.
4. When Larry offers to start a room, the person picks it. That runs `/mos:ignite`, which makes the first room. The person can also type `/mos:rooms new <name>` at any time.
5. Run the status check and confirm every DONE WHEN item.

## Route B: Claude Desktop

You cannot click the app for the person. Guide one step at a time. After each step, ask what they see, and compare it with "You should see". If the person sees labels that differ, first follow the troubleshooting row "Claude Desktop: no Customize and no Plugins in the app", then search (section 2) before you guess. In the Code tab, if `echo ok` prints `ok`, run the B3 check yourself. Before any step that restarts the app, tell the person to come back to this chat after the restart (it stays in the sidebar; in route D: this browser tab), or to paste the resume sentence.

- **B0. Scope.** Say in 3 lines: this adds the MindrianOS plugin to the Claude app and a rooms folder on this computer; if they are missing, it also installs the Claude app and Node.js 22.18.0 or newer (the Node.js installer shows an administrator prompt); nothing leaves the computer except generic method questions to Theo. Larry and the rooms need Cowork or the Code tab, which need a paid plan (Pro or higher); a person with no Claude account makes one on the app's sign-in page. Tell the person that approval prompts and a notice about a third-party plugin are normal. Get one yes.
- **B1. App and plan.** Open the Claude Desktop app and sign in with the Claude account. No app yet: download it from https://claude.ai/download, install it, sign in. The Code tab needs a Pro, Max, Ultra, Team or Enterprise plan; if Cowork or the Code tab shows a prompt to upgrade, the plan does not include it (the upgrade prompt decides for both tabs). If neither Cowork nor the Code tab is in the plan, follow "If the person says no" (plan case). You should see: the app with a sidebar on the left.
- **B2. Plugins page.** In the sidebar, click **Customize**, then **Plugins**. You should see: a Plugins page with an **Add** button.
- **B3. Node.js.** The MindrianOS plugin runs its tools with Node.js 22.18.0 or newer on this computer. Ask the person to open a terminal (Windows: press the Windows key, type PowerShell, press Enter; Mac: press Command and Space, type Terminal, press Enter), type `node --version` and press Enter. You should see: v22.18.0 or a higher number. On Windows, also ask them to type `[System.Environment]::OSVersion.VersionString` and paste it, for later searches. If the version is missing or older: on https://nodejs.org/en/download, pick the LTS version, the system, and the installer (.pkg on a Mac, .msi on Windows), run it, then quit Claude Desktop fully and open it again (details: commands.md, "Node.js for Claude Desktop"), then check again.
- **B4. Marketplace.** Click **Add**, then **Add marketplace**, enter `jsagir/mindrian-marketplace`, and confirm. If `mindrian-marketplace` already shows in the list (it does when the get-mindrian skill came from it), skip this step. You should see: `mindrian-marketplace` in the list, with its plugins.
- **B5. Install.** Find **MindrianOS** (the `mos-desktop` entry) and click **Install**. Do not install `mos` here; `mos` is for Claude Code in a terminal. Ask the person to describe the entry now. You should see: an installed state, for example an Installed label or a toggle that is on.
- **B6. Where it works.** Larry and the room tools work in **Cowork** and in the **Code** tab. **Chat** gets the skills and commands. Hooks and the `⬡ MindrianOS` status line exist only in Claude Code in a terminal. Ask the person to pick one: the Code tab (recommended) or Cowork, and to use it for B7 to B10. They start a new session there, so the plugin loads, and come back to this chat after each step to tell you what they see. You should see: a new, empty session in the chosen tab.
- **B7. Rooms folder.** In the Code tab, click the environment selector under the prompt box and pick the top entry in the **Local** group. Local means Claude works on this computer, where the rooms are. Do not pick a cloud environment: a cloud session starts from a fresh copy of a code repository, cannot see the folders on this computer, and cannot use plugins installed from the app. Then use the folder control, **Open folder…**, and pick `MindrianRooms` in the home folder (Windows: `C:\Users\<your name>\MindrianRooms`; Mac: the folder with the house icon). If it is missing, the person makes it in that dialog with the New Folder button. In Cowork, start a project with **Use an existing folder** and pick the same folder. Same sync warning as A7. Route B uses only this default folder: the app does not read the Claude Code setting that moves it. You should see: `MindrianRooms` in the folder control.
- **B8. First use.** Ask the person to type this first message in the chosen tab: `Hi Larry, are you there?` The plugin installs its own packages once; a short "installing" answer is normal, so they send the same message again after it finishes. You should see: a reply that opens with one colored square and `Larry | MindrianOS`, and says "I'm Larry, MindrianOS's PwS thinking partner" (Larry's sign). A reply without the sign means the plugin did not load: go to "When a step fails". B9 is the second check.
- **B9. Doctor.** In the chosen tab, type `/mos:doctor`, and ask the person to paste the Summary line exactly. You should see: 0 warnings. If not, go to "When a step fails".
- **B10. Onboarding.** Type `/mos:onboard`. Larry asks "who are you" in Step 4; the person may choose Skip. When Larry offers to start a room, pick it (that runs `/mos:ignite`), or type `/mos:rooms new <name>`. You should see: Larry names the new room folder.
- **B11. Updates and the end check.** Ask: "Do you want MindrianOS to update by itself? (recommended)" If yes, in Customize, Plugins, click `mindrian-marketplace` in the list of marketplaces (or its menu) and turn on **Sync automatically**; if the person does not see it, follow the troubleshooting row "Claude Desktop: no Customize and no Plugins in the app". If no, they can use **Check for updates** later. You should see: Sync automatically is on. Then confirm each DONE WHEN item for route B with the person's answers.

Desktop says "Marketplace sync failed" when you add `jsagir/mindrian-marketplace`: it is often already added. Ask the person to look for `mindrian-marketplace` in the plugin list. If it is there, select **Check for updates** and install MindrianOS from it. Do not add it again.

## Route C: Codex or another agent with a shell

MindrianOS runs inside Claude Code. You install Claude Code and MindrianOS from your shell, then the person continues in Claude Code.
1. Run section 1, then A0 to A8 in your shell. Use the "Agent shell prefix" from commands.md after each install.
2. If `claude` is missing, install it with the A2 lines after the A1 yes, and offer the PATH fix first if the installer says `~/.local/bin` is not in your PATH. Then guide the login with the words in commands.md, "Log in".
3. If your sandbox blocks a command or asks for approval, ask the person to approve it. Do not work around the sandbox. If the person says no, follow "If the person says no".
4. You cannot run `/mos:` commands; they run inside Claude Code. For the hand-over, give the A9 message with the route C words: "Open a new terminal and run [the line for the shell]. When Claude Code starts, paste the sentence as your first message." The new Claude Code session does A10. Add: "After the first room, come back here and tell me, so I can check it."
5. If the person comes back to you, run the status check (with the agent shell prefix) and confirm the A9 lines. If they do not come back, the honest end state is: handed over to Claude Code, A9 items not yet proved.

## Route D: a chat with no shell

Say this in your own words, in 2 sentences: "I cannot install MindrianOS from this chat, and it does not run inside this app; it is a plugin for Claude. I will walk you through it one step at a time, and I will check each step with you."

- Keep rule 12 of "How you work": no integration, no connector, no custom GPT, no request for files or notes.
- Run section 1 by asking once.
- Then ask: "Do you want the Claude app (clicks, and one check command), or Claude Code in a terminal (you type commands I give you)? Most people pick the app; it needs only one check command." If there is no answer, use the app.
- The app: follow route B, one step per message. It has one terminal check (B3), with the exact keys to press. The download page is https://claude.ai/download.
- Claude Code in a terminal: follow route A. The person runs each command and pastes the output back. You check the output before you give the next step. Give the A1 scope and the A7 card as questions and wait for each yes. Remind them that Claude Code needs a paid plan (A1). If section 1 gave no version, the first command is the version line for their shell (section 1). After each install, the person opens a new terminal before the next command. At A9, the new Claude Code session does A10; ask the person to come back and tell you what Larry showed. If they do not, the end state is: handed over, A9 items not yet proved.
- After each step, ask what they see. If it differs from "You should see", open the troubleshooting reference or search (section 2), then give the fix for that case.
- Never paste the whole procedure in one message and leave the person with it.

## If the person says no

- No at consent point 1, or no to a required tool (Node.js or Claude Code): stop the install. Say what is not installed and the one step they can run later (the start sentence). Do not retry.
- No to the PATH fix: in every line the person types, use the full path `~/.local/bin/claude` (Windows: `%USERPROFILE%\.local\bin\claude.exe`) in place of `claude`, and name it at the end.
- No to a choice in A7 (auto-update, another rooms folder, shortcut, Eureka): skip that choice, keep the default, and continue. Name it at the end.
- The plan does not include Claude Code (route A or C), or neither Cowork nor the Code tab (route B): stop. Say that Larry and the rooms need one of them, that Chat alone gets only the skills and commands, and that a paid plan (Pro or higher) opens them. Give the start sentence for later.
- A denied approval prompt (Claude Code or a sandbox): the step did not run. Ask once whether they want to approve it. If no, treat it as a no to that step, as above.

## Access refused

Today the installer asks for no key. If a step reports that a key or an entitlement is missing, invalid or refused:
1. Stop the install.
2. Quote the exact message.
3. Say plainly that MindrianOS cannot run its methodology without access. Then run the status check (route B or D: ask what the person sees), and tell the person what is installed and what is not.
4. Name where to get access: the URL the message prints; if it prints none, https://mindrian-os.com.
5. Never invent a key, never edit settings to get past it, and never retry in a loop.

## When a step fails

1. Get the real evidence first. With a shell, capture the exact output yourself. Without one, ask the person to paste the exact error text, or to send a screenshot.
2. Open references/troubleshooting.md (next to this file in an installed skill, else https://raw.githubusercontent.com/jsagir/mindrian-marketplace/master/plugins/get-mindrian/skills/get-mindrian/references/troubleshooting.md).
3. Match the exact wording to a row. Give one step, check it again, then run the doctor (before A4: the A1 tool check; route B before B5: the step's "You should see").
4. If no row matches, or the row's step fails, search (section 2).
5. If the search finds nothing reliable either, give the honest unknown: say you have not seen this error, and tell the person to paste the exact error line into a search engine. Never invent a fix, a flag or a command.
6. Only then, as a fallback, offer https://mindrian-os.com/docs/install.

## Troubleshooting

The most common cases. The reference file has more rows and the check for each.

| What you see | What to do | Check |
|---|---|---|
| `command not found: claude` or `'claude' is not recognized` | An agent: use the "Agent shell prefix". A person: the PATH fix in the reference (Needs a yes), then a new terminal. | `claude --version` prints a version |
| `npx` or `node` is not recognized | Node.js is missing, or the terminal is older than the install. Install Node.js (Needs a yes; A2 rules), open a new terminal. | `node --version` prints v22.18.0 or newer |
| An engine or version error from `npx` | Node.js is older than 22.18.0. Install the current LTS (Needs a yes; A2 rules), retry A4. | `node --version` prints v22.18.0 or newer |
| "already installed" during A4 | Fine. The installer updates it next. Continue to A5. | `PASS A4` |
| The doctor still shows a warning after `--fix` | Report the line exactly as printed. Do not patch files by hand. Open the reference. | the Summary shows 0 warnings, or the warning is reported as open |
| Desktop: "Marketplace sync failed" | See the note at the end of route B. | `mindrian-marketplace` is in the plugin list |
| No `⬡ MindrianOS` line after the restart | `/mos:doctor --statusline-visibility`, then `/mos:doctor --fix`, then restart. Desktop has no status line by design. | the line shows at the bottom of the terminal |
| A sandbox blocks a command (route C) | Ask the person to approve it. Do not work around it. | the command runs |

## What to say at the end

Say 2 or 3 sentences: what is now installed and checked, any choice the person declined, and the one next action (route A: "Paste the resume sentence into Claude Code in your MindrianRooms folder."; route B: "Open a Code tab session in your MindrianRooms folder and talk to Larry."). Do not list paths, ids or logs unless the person asks.

EXECUTE NOW: Find your route in section 0, then complete the TODO list for that route until every DONE WHEN item for it is true.
