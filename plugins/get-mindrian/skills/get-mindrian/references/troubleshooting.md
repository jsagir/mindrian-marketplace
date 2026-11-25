# MindrianOS install troubleshooting

Load this file only when a step of SKILL.md fails.
Get the exact error text first (capture it yourself with a shell, or ask the person to paste it or send a screenshot). Match the exact wording to a row below.
Fix one step at a time and check it. Then run the MindrianOS doctor (`npx --yes @mindrian_os/cli doctor` from a shell, or `/mos:doctor` inside Claude Code). Before MindrianOS is installed (before SKILL.md A4), run the A1 tool check again instead.
Consent: a row marked **Needs a yes** installs, removes or changes something. Show the exact command and get a yes first, unless the A1 yes already named that exact tool. A row without the mark only reads, retries, or runs the doctor that A1 named.

Rows give the symptom, the lane (where it happens) when it matters, the cause, the fix as single steps, the check that proves the fix, and a search query when a search can help. In a search query, replace `[OS name] [OS version]` with the result of SKILL.md section 1, and `[exact error line]` with the full error text. No fix here uses sudo; do not add sudo unless the person asks.

## Know the lane first

Most "installed but not found" problems come from two copies of a tool in two lanes.
- WSL and native Windows are two lanes with separate PATHs and separate Node.js installs. A tool installed inside WSL exists only inside WSL; a tool installed in PowerShell exists only in Windows. Keep one lane for Claude Code and MindrianOS.
- Find every copy: `which -a claude` and `which -a node` (macOS, Linux, WSL); `where.exe claude` and `where.exe node` (Windows). In WSL, a path that starts with `/mnt/c/` is a Windows program.
- Apple Silicon Mac: `uname -m` must print `arm64`. `x86_64` means the terminal runs under Rosetta; open a native terminal. `which brew` should print `/opt/homebrew/bin/brew`; `/usr/local/bin/brew` is the Intel Homebrew, and mixing the two gives "command not found".
- Windows shells: the prompt `PS C:\>` is PowerShell; a plain `C:\>` is CMD; `uname -s` printing MINGW or MSYS is Git Bash. Match the command to the shell.
- An agent's own shell does not reload the profile after an install. Use the "Agent shell prefix" in commands.md before you decide a tool is missing.

## Claude Code install methods

Source: https://code.claude.com/docs/en/setup. Which method installed Claude Code often explains a symptom.
- Native installer (recommended): updates itself; puts `claude` in `~/.local/bin` or `%USERPROFILE%\.local\bin` and does not change PATH. Typical symptom: `command not found: claude` until the PATH fix.
- Homebrew cask `claude-code` or `claude-code@latest`: does not update itself; `brew upgrade claude-code`. Typical symptom: an old version.
- WinGet `Anthropic.ClaudeCode`: does not update itself; `winget upgrade Anthropic.ClaudeCode`. Typical symptom: an old version.
- npm `@anthropic-ai/claude-code` (needs Node.js 22 or later): update with `npm install -g @anthropic-ai/claude-code@latest`, not `npm update -g`. Typical symptoms: EACCES, ENOTEMPTY, `running scripts is disabled`.
- Linux apt, dnf, apk: update through the system package manager.
- The VS Code extension and the JetBrains plugin bundle a private copy for their own panel and do not put `claude` on PATH. `command not found: claude` in the VS Code terminal means: install the standalone CLI.

### More than one copy of Claude Code (`which -a claude` or `where.exe claude` lists two or more)
- Cause: Claude Code was installed by more than one method.
- Fix (**Needs a yes**): 1. Read the paths. `~/.local/bin/claude` (Windows `%USERPROFILE%\.local\bin\claude.exe`) is the native installer; a path under `/opt/homebrew` or `/usr/local/Caskroom` is Homebrew; a copy that `npm ls -g @anthropic-ai/claude-code` lists is npm. 2. Keep the native copy. If there is no native copy, install it first (commands.md, Claude Code), check `claude --version`, then continue. 3. Remove each other copy with the command for its method:
  - Homebrew: `brew uninstall --cask claude-code` (or `brew uninstall --cask claude-code@latest`).
  - WinGet: `winget uninstall Anthropic.ClaudeCode`.
  - npm: `npm uninstall -g @anthropic-ai/claude-code`.
  - A native copy you do not keep (macOS, Linux, WSL): `rm -f ~/.local/bin/claude` and `rm -rf ~/.local/share/claude`; Windows PowerShell: `Remove-Item -Path "$env:USERPROFILE\.local\bin\claude.exe" -Force` and `Remove-Item -Path "$env:USERPROFILE\.local\share\claude" -Recurse -Force`.
  Never remove `~/.claude` or `~/.claude.json`; they hold the settings and the plugins. 4. Open a new terminal.
- Check: `which -a claude` (or `where.exe claude`) lists one path, and `claude --version` prints a version.
- Source: https://code.claude.com/docs/en/setup ("Uninstall Claude Code").

## Node, npm and npx

### `npx : The term 'npx' is not recognized as the name of a cmdlet, function, script file, or operable program.` (also `'npm' is not recognized`, `command not found: npx`)
- Lane: any; most often Windows PowerShell.
- Cause: Node.js is not installed, or it is installed but this terminal window is older than the install.
- Fix: 1. Run `node --version`. 2. If it is also not recognized, install Node.js (**Needs a yes**; commands.md, Node.js; on Windows the Windows Installer, with the PATH option on). 3. Close every terminal window and open a new one. 4. Run `node --version` and `npm --version` again. 5. On Windows, if `node` works but `npm` does not, run `where.exe npm`; it should list `C:\Program Files\nodejs\npm.cmd`. 6. Route B: quit Claude Desktop fully and open it again (commands.md, "Node.js for Claude Desktop").
- Check: `npx --version` prints a version.
- Search: `"npx : The term 'npx' is not recognized as the name of a cmdlet, function, script file, or operable program." [OS name] [OS version] PowerShell site:nodejs.org`

### `npm.ps1 cannot be loaded because running scripts is disabled on this system` (`PSSecurityException`)
- Lane: Windows PowerShell.
- Cause: the PowerShell execution policy blocks the `.ps1` launchers that npm makes.
- Fix: 1. Recommended, as it changes no setting: call the `.cmd` launcher, `npx.cmd --yes @mindrian_os/cli --no-eureka` (and `npm.cmd` for npm). 2. If the person wants plain `npx` to work: **Needs a yes**: run `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` (no Administrator needed), then retry. If the policy comes back, an organization policy sets it; the person needs their IT team.
- Check: the command runs without the error.
- Search: `"running scripts is disabled on this system" npm [OS name] [OS version] site:code.claude.com/docs`

### Node is older than 22.18.0 (an engine error, or `node --version` prints v22.17 or older)
- Cause: MindrianOS needs Node.js 22.18.0 or newer.
- Fix (**Needs a yes**): 1. Install the current LTS (commands.md, Node.js). 2. Open a new terminal (an agent: use the agent shell prefix). 3. With nvm, run `nvm use --lts`.
- Check: `node --version` prints v22.18.0 or newer, and it is the first entry of `which -a node` (Windows `where.exe node`).
- Search: `upgrade Node.js LTS [OS name] [OS version] site:nodejs.org`

### `EBADENGINE` warning during an npm install
- Cause: npm prints a warning when a package asks for a newer Node.js. For Claude Code installed with npm, the install completes and `claude` still runs (setup page).
- Fix: 1. Read the full output. 2. If the install completed, continue. 3. If the warning names `@mindrian_os/cli`, upgrade Node.js (row above).
- Check: the next step runs.
- Search: `"[exact error line]" [OS name] site:docs.npmjs.com`

### `EACCES: permission denied` during an npm install
- Lane: macOS, Linux, WSL.
- Cause: the global npm folder belongs to the system, not to the person.
- Fix: 1. Do not use sudo. 2. Install Node.js with nvm (**Needs a yes**; commands.md), which keeps npm under the home folder. 3. Open a new terminal and retry.
- Check: the npm install completes without EACCES.
- Search: `"[exact error line]" [OS name] [OS version] site:docs.npmjs.com`

### `npm error code ENOTEMPTY` during an update or a reinstall
- Lane: any; npm installs of Claude Code.
- Cause: an earlier interrupted run left a folder that npm cannot move.
- Fix (**Needs a yes**; these commands delete folders): 1. Read the `npm error path` line. 2. If that path is under the folder `npm root -g` prints, run (macOS, Linux, WSL) `rm -rf "$(npm root -g)/@anthropic-ai/claude-code"`, then `rm -rf "$(npm root -g)/@anthropic-ai/.claude-code-"*` (zsh may print `no matches found`; that is fine). Windows PowerShell: `Remove-Item -Recurse -Force "$(npm root -g)/@anthropic-ai/claude-code", "$(npm root -g)/@anthropic-ai/.claude-code-*"`. If the path is somewhere else, delete exactly the folder the `npm error path` line names, and nothing else. 3. Run `npm install -g @anthropic-ai/claude-code@latest`. Better: move to the native installer (commands.md, Claude Code).
- Check: the folder no longer exists, the install completes, and `claude --version` prints a version.
- Source: https://code.claude.com/docs/en/troubleshoot-install

### `exec: node: not found`, or an error from `npx` in WSL that names a Windows path (`C:\...` or `/mnt/c/...`)
- Lane: WSL.
- Cause: WSL runs the Windows Node.js or npm, which comes first on the WSL PATH.
- Fix: 1. Run `which -a node` and `which -a npx`. 2. If the first entry starts with `/mnt/c/`, install Node.js inside WSL with nvm (**Needs a yes**; commands.md). 3. Run, as one line: `. "$HOME/.nvm/nvm.sh" && nvm use --lts && hash -r && which -a npx`. The first entry must be under `$HOME/.nvm`. 4. If it is not, see "An older Node.js is still first". 5. Retry with the prefix, as one line: `. "$HOME/.nvm/nvm.sh" && npx --yes @mindrian_os/cli --no-eureka`. Do not turn off the Windows PATH import in WSL and do not remove Windows Node.js.
- Check: `. "$HOME/.nvm/nvm.sh" && which npx` prints a path under `$HOME/.nvm`, and the install runs.
- Search: `"[exact error line]" WSL Ubuntu [OS version] npx /mnt/c site:nodejs.org`

### An older Node.js is still first (a new terminal shows an old `node --version`)
- Lane: macOS, Linux, WSL.
- Cause: an older copy comes first on PATH, or nvm has no default version, or the profile has no nvm loader lines.
- Fix (**Needs a yes**): 1. Run `which -a node`. 2. With nvm: run `. "$HOME/.nvm/nvm.sh" && nvm install --lts && nvm alias default 'lts/*'`. 3. If `grep -n NVM_DIR ~/.zshrc ~/.bashrc ~/.bash_profile ~/.profile` prints nothing, add the nvm loader lines to the profile of this shell with the commands.md block "Add another line to a shell profile", once for each line: `export NVM_DIR="$HOME/.nvm"` and `[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"`. 4. On a Mac, an old copy under `/usr/local/bin`: if `which brew` prints `/usr/local/bin/brew`, it is an Intel Homebrew copy (see "Know the lane first"); else it is most often the nodejs.org installer, so install the LTS with the same installer (commands.md, "Node.js for Claude Desktop", Mac line), which replaces it. 5. Open a new terminal.
- Check: in a new terminal, `node --version` prints v22.18.0 or newer.
- Source: https://code.claude.com/docs/en/troubleshoot-install (nvm loader lines).

### No administrator rights on Windows (the Node.js installer asks for an administrator password)
- Cause: the Windows Installer installs for all users and needs an administrator.
- Fix: 1. Stop this step. 2. Ask the person to get an administrator (often the IT team) to install Node.js LTS from https://nodejs.org/en/download. Do not try to get past the prompt. 3. After the install, continue at A1 (route B: B3).
- Check: `node --version` prints v22.18.0 or newer.

## Claude Code

### `command not found: claude` or `'claude' is not recognized` after the install (also `zsh: command not found: claude`)
- Cause: the native installer put `claude` in `~/.local/bin` (Windows `%USERPROFILE%\.local\bin`) and does not change PATH; or the terminal window is older than the install; or an agent's shell did not reload the profile.
- Fix: 1. An agent: run `export PATH="$HOME/.local/bin:$PATH" && claude --version` (PowerShell: `$env:PATH = "$env:USERPROFILE\.local\bin;$env:PATH"; claude --version`). A person: open a new terminal and run `claude --version` (this helps only if a profile already adds `~/.local/bin`). 2. If still not found, check the file: `ls -la ~/.local/bin/claude` (PowerShell: `Test-Path "$env:USERPROFILE\.local\bin\claude.exe"`). 3. If the file is there, apply the PATH fix for this shell (**Needs a yes**; commands.md, PATH fix). 4. If the file is not there, install Claude Code again (commands.md).
- Check: `claude --version` prints a version in a new terminal (an agent: ask the person to open a new terminal, run it, and paste the output).
- Search: `"[exact error line]" [OS name] [OS version] site:code.claude.com/docs`

### `The token '&&' is not a valid statement separator`, `'irm' is not recognized`, `'bash' is not recognized as the name of a cmdlet`, or `A parameter cannot be found that matches parameter name 'fsSL'`
- Lane: Windows.
- Cause: the command for one shell was pasted into another shell.
- Fix: 1. Look at the prompt: `PS C:\>` is PowerShell, `C:\>` is CMD. 2. Use the matching line from commands.md.
- Check: the installer runs.
- Search: `"[exact error line]" Claude Code install Windows site:code.claude.com/docs`

### Running `claude` opens the Claude Desktop app instead of the CLI
- Lane: Windows.
- Cause: an older Claude Desktop registers a `Claude.exe` that comes first on PATH.
- Fix (**Needs a yes**; it updates the app): 1. Update Claude Desktop (Help, Check for Updates). 2. Open a new terminal and run `claude --version`.
- Check: `claude --version` prints `(Claude Code)`.

### `Claude Code access has not been granted for this account`, `403 Forbidden` after login, or "model not available"
- Cause: the account or plan does not include Claude Code. The free claude.ai plan does not include it.
- Fix: 1. Confirm the plan is Pro, Max, Ultra, Team, Enterprise or Console. 2. Run `claude` and log in again with that account.
- Check: a first prompt in `claude` gets an answer.
- Search: `"[exact error line]" site:code.claude.com/docs`

### The browser login opens but the terminal seems to hang
- Cause: the login flow did not return to the terminal.
- Fix: 1. Wait 2 minutes. 2. If it does not return, close the terminal, open a new one, and run `claude` again.
- Check: `claude` starts a session.

## Windows

### The banner or box characters look garbled
- Cause: the console is not in UTF-8.
- Fix: 1. Run `chcp 65001`. 2. Prefer Windows Terminal or PowerShell over the old CMD window.
- Check: the banner shows clean lines.

### `git is not found` on Windows
- Cause: Git for Windows is not installed. It is optional for Claude Code on native Windows: without it, Claude Code uses PowerShell as its shell tool. WSL does not need it.
- Fix: 1. If the step that failed needs Git, install Git for Windows from https://git-scm.com/downloads/win (**Needs a yes**; a guided step). 2. Open a new terminal.
- Check: `git --version` prints a version.

### A step fails on a path that is too long (about 260 characters)
- Cause: the Windows path length limit.
- Fix (**Needs a yes**; it changes the person's Git settings): 1. Run `git config --global core.longpaths true`. 2. Retry.
- Check: the step completes.
- Search: `"[exact error line]" git Windows [OS version] site:git-scm.com`

## macOS

### `xcode-select: error: command line tools are not installed`, or a dialog offers to install the command line developer tools
- Cause: a tool such as git or `python3` needs the Apple command line tools.
- Fix (**Needs a yes**): 1. Run `xcode-select --install`, or click Install in the dialog. 2. Wait until it finishes. 3. Retry.
- Check: `xcode-select -p` prints a path.
- Search: `"[exact error line]" macOS [OS version] site:developer.apple.com`

### `"claude" cannot be opened because it is from an unidentified developer` (Gatekeeper)
- Cause: a one-time macOS security check.
- Fix (**Needs a yes**; it allows this one program): 1. Confirm the blocked item is `claude` from the official installer. 2. Open System Settings, Privacy & Security. 3. Click Allow Anyway next to the blocked item. 4. Retry.
- Check: `claude --version` prints a version.
- Search: `"[exact error line]" macOS [OS version] site:support.apple.com`

### `dyld: cannot load`, `dyld: Symbol not found` or `Abort trap`
- Cause: the binary does not match the Mac (architecture or macOS version; Claude Code needs macOS 13.0 or newer).
- Fix: 1. Run `uname -m` and `sw_vers -productVersion`. 2. **Needs a yes**: open a native terminal (not Rosetta) and reinstall with the native installer.
- Check: `claude --version` prints a version.
- Search: `"[exact error line]" Claude Code macOS [OS version] site:code.claude.com/docs`

## Linux and WSL

### `Killed` during the install
- Cause: the machine ran out of memory.
- Fix: 1. Close other programs. 2. Retry the installer. Adding swap space needs administrator rights; do not do it unless the person asks.
- Check: the installer completes.

### `cannot execute binary file: Exec format error` in WSL
- Cause: WSL 1 cannot run this binary.
- Fix: 1. In PowerShell, run `wsl -l -v` and read the NAME and VERSION columns. 2. If VERSION is 1, run `wsl --set-version <NAME> 2` in PowerShell (**Needs a yes**; it converts the distribution to WSL 2 and can take some minutes). 3. Open the WSL terminal again.
- Check: `wsl -l -v` shows VERSION 2, and `claude --version` prints a version inside WSL.
- Source: https://code.claude.com/docs/en/troubleshoot-install ("Exec format error on WSL1").

## Network, proxy and TLS

### `ETIMEDOUT`, `ECONNREFUSED`, or the install hangs for many minutes
- Cause: a company network, VPN or proxy blocks the package registry or the download host.
- Fix: 1. Run `npm ping`. 2. Behind a proxy, ask the person for the proxy address from their IT team, then run `npm config set proxy <address>` and `npm config set https-proxy <address>` (**Needs a yes**). 3. Retry.
- Check: `npm ping` answers.
- Search: `"[exact error line]" npm proxy [OS name] site:docs.npmjs.com`

### `unable to get local issuer certificate`, `unable to verify the first certificate`, `SELF_SIGNED_CERT_IN_CHAIN`, or `TLS connect error`
- Cause: the network inspects TLS with a company certificate.
- Fix: 1. Ask the person for the company root certificate file (a PEM file) from their IT team. 2. macOS, Linux, WSL, for this terminal: `export CURL_CA_BUNDLE=/path/to/corporate-ca.pem` and `export NODE_EXTRA_CA_CERTS=/path/to/corporate-ca.pem`, then rerun the failed install line in the same terminal. Windows PowerShell: the IT team adds the certificate to the Windows certificate store, then rerun `irm https://claude.ai/install.ps1 | iex`. 3. For npm (**Needs a yes**): `npm config set cafile /path/to/corporate-ca.pem`. 4. For Claude Code itself in every session (**Needs a yes**): set `NODE_EXTRA_CA_CERTS` with the commands.md script "Any other `env` value" (preview, yes, apply). Do not turn off certificate checks.
- Check: the install completes.
- Source: https://code.claude.com/docs/en/troubleshoot-install ("TLS or SSL connection errors").

## MindrianOS

### Any MindrianOS problem: start with the doctor
- Fix: 1. Run `npx --yes @mindrian_os/cli doctor --fix` (or `/mos:doctor --fix` inside Claude Code). 2. Run `npx --yes @mindrian_os/cli doctor` and read each line without a ✓ and the Summary line. 3. Report those lines exactly as printed. Do not patch plugin files by hand. The doctor exits 0 even when it shows a warning, so read the Summary.
- Check: the Summary shows 0 warnings, or each warning that stays is reported to the person as open.

### Many approval prompts, or a notice about a third-party plugin
- Cause: Claude Code asks before it runs tools, and it shows a safety notice for every plugin that does not come from Anthropic. This is normal. In Claude Code the plugin's hooks and status line run in every session; room content stays on this computer.
- Fix: 1. Approve the prompts. The person may choose always-allow for the ones they trust.
- Check: the step continues.

### `Marketplace not found`, or `mos@mindrian-marketplace` cannot be found
- Cause: the marketplace is not added, or the local catalog is old.
- Fix (**Needs a yes** if A1 did not cover it): 1. Run `claude plugin marketplace add jsagir/mindrian-marketplace`. 2. Run `claude plugin marketplace update`. 3. Run `claude plugin install mos@mindrian-marketplace`.
- Check: `claude plugin list --json` lists `mos@mindrian-marketplace`.

### `FAIL A4` with an installed version that differs from the catalog
- Cause: the plugin is installed but older than the catalog, so the install step reported "already installed".
- Fix: 1. Run `npx --yes @mindrian_os/cli update`. 2. Run the status check again.
- Check: `PASS A4`.

### Commands are missing, or the plugin looks disabled, after an update
- Cause: an update can leave the plugin disabled, or the session still runs the old copy.
- Fix: 1. Run `/mos:doctor --fix`. 2. Start a fresh Claude Code session (in Desktop: a new Cowork task or Code tab session).
- Check: typing `/mos:` lists the commands.

### No `⬡ MindrianOS` status line after the restart
- Cause: the status line is not set up yet. Claude Desktop and Cowork have no status line by design.
- Fix: 1. Run `/mos:doctor --statusline-visibility`. 2. Run `/mos:doctor --fix`. 3. Restart Claude Code. If it is still missing, note it and continue: the line is not needed for Larry or the rooms.
- Check: the line shows at the bottom of the terminal.

### Claude Code answers without Larry's sign (no colored square, no `Larry | MindrianOS`)
- Cause: Larry is not the running agent of this session. The session was started outside the rooms folder, the Larry pin is not in the rooms folder, or a `settings.local.json` in the rooms folder names another agent.
- Fix: 1. Start Claude Code in the rooms folder (SKILL.md A9 has the line for each shell). 2. Run the status check. On `FAIL A8 Larry pinned in rooms folder`, run the pin script in commands.md (**Needs a yes**), then restart Claude Code. 3. For one session in any folder: `claude --agent mos:larry-extended`. 4. To take the pin out again: the same pin script with `undo`; if it prints `LEFT AS IT IS`, delete the `agent` line in `<rooms folder>/.claude/settings.json` by hand.
- Check: the status check prints `PASS A8 Larry pinned in rooms folder`, and a reply opens with Larry's sign.

### A room is "missing"
- Cause: rooms live in the rooms folder (`~/MindrianRooms`, Windows `%USERPROFILE%\MindrianRooms`, or the folder that `MINDRIAN_ROOMS_HOME` names), not in the folder the terminal was in.
- Fix: 1. Run `/mos:rooms` to list the rooms. 2. Open the rooms folder.
- Check: the room shows in the list.

### Larry says the methodology graph (Theo) is unreachable, or a red `MCP server failed` line at the start
- Cause: the connection to Theo, the methodology graph, failed; or the plugin tools did not start because Node.js 22.18.0 or newer is missing (most often in Claude Desktop); or the first call after a quiet time is slow.
- Fix: 1. In Claude Desktop, check Node.js first (SKILL.md B3). 2. Run `/mos:doctor --brain-smoke`. 3. Run `/mos:doctor --fix`. 4. Restart Claude Code (in Desktop: start a new task or session). Larry does not invent a method answer while Theo is unreachable.
- Check: `/mos:doctor --brain-smoke` passes.

### A message says a key or an entitlement is missing, invalid or refused
- Go to "Access refused" in SKILL.md. Do not try a workaround.

### Claude Desktop: no Customize and no Plugins in the app (for example only Settings)
- Cause: the app is an older version, or the person looks at a menu, not the sidebar.
- Fix: 1. If you run as the get-mindrian skill, ask where the person clicked to install get-mindrian; use that same path for B5. 2. Ask the person to look at the left sidebar of the main window. 3. If Customize is not there (**Needs a yes**; it updates the app): update the app with Help, Check for Updates (Windows) or Claude, Check for Updates (macOS); if the person cannot find the Help or Claude menu, ask for a screenshot of the top-left corner of the app; or download it again from https://claude.ai/download. 4. Before the restart, tell the person to come back to this chat after it (it stays in the sidebar). Restart the app and look again. 5. If the labels still differ, ask for the app version (Help, About Claude on Windows; Claude, About Claude on macOS) and search the current labels (SKILL.md section 2).
- Check: the person sees Customize, then Plugins.
- Search: `Claude Desktop [app version] Customize Plugins add marketplace [OS name] [OS version] site:claude.com/docs`

## The honest unknown

If nothing here matches and a search finds nothing reliable: say that you have not seen this error. Tell the person to copy the exact error line (not a summary) and paste it into a search engine; an exact error string is a good lookup key. Never invent a fix, a flag or a command.
