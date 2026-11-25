# MindrianOS install commands by system

SKILL.md says when to use each block. Never run a block without the consent step SKILL.md names (A1 for tools, A7 for settings and shortcuts).
Each block names its system, its shell and its source. No block uses sudo; do not add sudo unless the person asks.

## Git Bash on Windows

If `uname -s` prints MINGW or MSYS, you are in Git Bash on Windows. The system is Windows for every table and every choice.
- Run these in Git Bash as they are: `node`, `npx`, `claude`, the node one-liners (Status check, Settings changes) and `mkdir -p "$HOME/MindrianRooms"` (in Git Bash, `$HOME` is the Windows user folder, so this is `%USERPROFILE%\MindrianRooms`).
- Run every block marked PowerShell through PowerShell, with the block lines unchanged inside a quoted here-document. The quotes around `PS` stop Git Bash from changing `$` signs and quotes. PowerShell reads the lines from standard input and runs them one statement at a time (https://learn.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_exe, `-Command -`).

```bash
powershell.exe -NoProfile -Command - <<'PS'
irm https://claude.ai/install.ps1 | iex
PS
```

- Do not run the macOS, Linux and WSL installer lines in Git Bash.

## Node.js

MindrianOS needs Node.js 22.18.0 or newer. Install the version that nodejs.org marks LTS (26 on 2026-11-19). Source: https://nodejs.org/en/download

Before you install (macOS, Linux, WSL): run `which -a node` and pick the method by where an old copy lives.
- Under `~/.nvm`: use nvm, as one line: `. "$HOME/.nvm/nvm.sh" && nvm install --lts && nvm alias default 'lts/*' && node --version`.
- Under `/opt/homebrew`: `brew upgrade node`, then `node --version`.
- Under `/usr/local/bin` on a Mac where `uname -m` prints `arm64` and `brew` is not under `/usr/local`: it is most often the nodejs.org installer; install the LTS with the same installer (Node.js for Claude Desktop, Mac line), which replaces it.
- No old copy: the blocks below.

macOS with Homebrew already installed (`brew --version` answers), bash or zsh. Source: https://nodejs.org/en/download (Homebrew tab)

```bash
brew install node
which -a node
node --version
```

The first line of `which -a node` must be the Homebrew copy and `node --version` must print v22.18.0 or newer. If an older copy comes first, see troubleshooting, "An older Node.js is still first".

macOS without Homebrew, Linux and WSL, bash or zsh, with nvm (no sudo; installs under the home folder). The nvm installer adds its loader lines to the shell profile (`~/.bashrc`, `~/.bash_profile`, `~/.zshrc` or `~/.profile`). Back up the profiles first, then show the added lines. Source: https://nodejs.org/en/download and https://github.com/nvm-sh/nvm

```bash
for f in ~/.zshrc ~/.bashrc ~/.bash_profile ~/.profile; do [ -f "$f" ] && cp "$f" "$f.bak-$(date +%Y%m%d-%H%M%S)"; done
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.41.0/install.sh | bash
tail -n 4 ~/.zshrc ~/.bashrc ~/.bash_profile ~/.profile 2>/dev/null
. "$HOME/.nvm/nvm.sh"
nvm install --lts
node --version
```

Pass: the `tail` output shows the lines that set `NVM_DIR` in at least one profile, and `node --version` prints v22.18.0 or newer. After the restart, A0 runs `node --version` in the new terminal; if an older version shows there, see troubleshooting, "An older Node.js is still first".

Windows, a guided step (the person clicks). Source: https://nodejs.org/en/download ("On Windows, use the Windows Installer (.msi) for system-wide installations when possible.")
1. Open https://nodejs.org/en/download, pick the LTS version, Windows, and the Windows Installer (.msi), and download it. Pick x64, unless the PC has an ARM processor (Settings, System, About: the System type names ARM); then pick ARM64.
2. Run it. Keep the option that adds Node.js to PATH turned on. Accept the Windows administrator prompt. If the PC asks for an administrator password the person does not have, see troubleshooting, "No administrator rights on Windows".
3. Close every terminal window, open a new one, and run `node --version` and `npm --version`. In route A this ends the session: give the resume sentence first (SKILL.md A2).

WSL: install Node.js inside WSL with nvm (block above). Do not use the Windows Node.js from WSL; `which node` must not start with `/mnt/c/`.

## Node.js for Claude Desktop

No commands to type; the person clicks. Source: https://nodejs.org/en/download (the installer files are listed at https://nodejs.org/dist/latest-v26.x/, for example `node-v26.13.1.pkg`).
- Mac: on https://nodejs.org/en/download pick the LTS version, macOS, and the installer (.pkg). Open the downloaded file and follow it; it asks for the Mac password (the administrator prompt).
- Windows: the Windows Installer steps above.
- Then the app must restart to see Node.js: Claude Desktop reads PATH when it starts, and on Windows it does not read PowerShell profiles (https://code.claude.com/docs/en/desktop, "Session not finding installed tools"). Before the restart, tell the person to come back to this chat after it. Quit the app fully (Mac: Claude menu, Quit Claude; Windows: close the window, and quit the Claude icon near the clock if it shows one), then open it again.
- Check: in a new terminal, `node --version` prints v22.18.0 or newer; in the app, `/mos:doctor` (B9) runs.

## Python and uv

Not needed for a normal Eureka setup: `npx --yes @mindrian_os/cli --eureka --yes` runs the engine's own setup, which can install uv and Python 3.12 itself. Use these blocks only when the doctor's `Eureka engine:` line names uv or Python as missing, after a yes. Source: https://docs.astral.sh/uv/getting-started/installation/

macOS, Linux and WSL, bash or zsh. The installer may add uv to PATH in the shell profile (uv installs to `~/.local/bin`). Back up the profiles first.

```bash
for f in ~/.zshrc ~/.bashrc ~/.bash_profile ~/.profile; do [ -f "$f" ] && cp "$f" "$f.bak-$(date +%Y%m%d-%H%M%S)"; done
curl -LsSf https://astral.sh/uv/install.sh | sh
tail -n 4 ~/.zshrc ~/.bashrc ~/.bash_profile ~/.profile 2>/dev/null
uv --version
uv python install
```

Windows PowerShell:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
uv --version
uv python install
```

Source for `uv python install`: https://docs.astral.sh/uv/guides/install-python/

## Claude Code

Claude Code needs a Pro, Max, Ultra, Team, Enterprise or Console account; the free claude.ai plan does not include it. Source for every block in this section: https://code.claude.com/docs/en/setup

Native installer (recommended; updates itself; no Administrator needed on Windows). It puts `claude` in `~/.local/bin` (Windows `%USERPROFILE%\.local\bin`) and does not change PATH.

```bash
# macOS, Linux, WSL (bash or zsh)
curl -fsSL https://claude.ai/install.sh | bash
```

```powershell
# Windows PowerShell (prompt starts with PS)
irm https://claude.ai/install.ps1 | iex
```

```bat
:: Windows CMD (prompt has no PS)
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

In WSL, install and start `claude` inside the WSL terminal, not from PowerShell or CMD.

Other methods the setup page names. Use one only if the person asks; they do not update themselves:
- Homebrew (macOS): `brew install --cask claude-code`; update with `brew upgrade claude-code`.
- WinGet (Windows): `winget install Anthropic.ClaudeCode`; update with `winget upgrade Anthropic.ClaudeCode`.
- npm (needs Node.js 22 or later): `npm install -g @anthropic-ai/claude-code@latest`. Never run it with sudo.
- Linux apt, dnf and apk need administrator rights, so use the native installer instead. If the person asks for a package manager, read that section of the setup page and give its steps one at a time.

Check and update:

```bash
claude --version
claude update
```

- `claude --version` prints for example `2.1.211 (Claude Code)`.
- `claude update` prints `Claude Code is up to date (<version>)`, or a line that ends with `to version <new version>` (then run it once more). Homebrew and WinGet installs print `Claude is up to date!`.

Log in (the person does this; you cannot): "Open a terminal (Mac: press Command and Space, type Terminal, press Enter; Windows: press the Windows key, type PowerShell, press Enter), type `claude` and press Enter. A browser opens. Log in with your Claude account. When Claude Code shows its prompt, tell me, then type /exit." The person's answer is the check. In route A the person can use a second terminal window, so this session keeps running.

## Agent shell prefix

Your shell tool runs each command in a fresh shell that does not read the updated profile. Until the restart, start each later command with the prefix for each tool you installed in this session:

| Installed | Shell | Prefix |
|---|---|---|
| Node.js with nvm | bash, zsh | `. "$HOME/.nvm/nvm.sh" && ` |
| Claude Code native, or uv | bash, zsh, Git Bash | `export PATH="$HOME/.local/bin:$PATH" && ` |
| Claude Code native | PowerShell | `$env:PATH = "$env:USERPROFILE\.local\bin;$env:PATH"; ` |
| Node.js Windows Installer | PowerShell | `$env:PATH = "$env:ProgramFiles\nodejs;$env:PATH"; ` |
| Node.js Windows Installer | Git Bash | `export PATH="/c/Program Files/nodejs:$PATH" && ` |

The Windows Installer folder `%ProgramFiles%\nodejs` is its default. If a command is still not found with the prefix, give the resume sentence and ask the person to restart (SKILL.md A9).

## PATH fix

Use it when `claude` is not found in a new terminal after the native install. It edits a shell profile or the user PATH: show the lines, get a yes, then run the block. Each block backs up first and reads back after. Source: https://code.claude.com/docs/en/troubleshoot-install ("Verify your PATH")

```bash
# zsh (default on macOS). For bash on Linux or WSL use ~/.bashrc; for bash on macOS use ~/.bash_profile.
F=~/.zshrc
[ -f "$F" ] && cp "$F" "$F.bak-$(date +%Y%m%d-%H%M%S)"
grep -q '.local/bin' "$F" 2>/dev/null || echo 'export PATH="$HOME/.local/bin:$PATH"' >> "$F"
tail -n 3 "$F"
```

```powershell
# Windows PowerShell. Saves the old user PATH to a dated file, sets the new one, prints it.
$currentPath = [Environment]::GetEnvironmentVariable('PATH', 'User')
$currentPath | Out-File "$env:USERPROFILE\user-path.bak-$(Get-Date -Format yyyyMMdd-HHmmss).txt"
[Environment]::SetEnvironmentVariable('PATH', "$currentPath;$env:USERPROFILE\.local\bin", 'User')
[Environment]::GetEnvironmentVariable('PATH', 'User')
```

Then the person opens a new terminal and runs `claude --version`.

Add another line to a shell profile (for example the nvm loader lines in troubleshooting). Show the line, get a yes, then run it with the profile file and the line filled in:

```bash
F=~/.zshrc
L='export NVM_DIR="$HOME/.nvm"'
[ -f "$F" ] && cp "$F" "$F.bak-$(date +%Y%m%d-%H%M%S)"
grep -qF "$L" "$F" 2>/dev/null || echo "$L" >> "$F"
tail -n 3 "$F"
```

Git for Windows is optional on native Windows (it gives the Bash tool); WSL does not need it.

## MindrianOS

Run these from a shell. `--yes` lets npx download the installer package without a question (https://docs.npmjs.com/cli/commands/npx: "Suppress this prompt with the -y or --yes option"). Source: the MindrianOS installer, package `@mindrian_os/cli`.

```bash
npx --yes @mindrian_os/cli --no-eureka     # install or bring current, without the Eureka offer
npx --yes @mindrian_os/cli doctor --fix    # repair what it can
npx --yes @mindrian_os/cli doctor          # read-only check; report its Summary line
npx --yes @mindrian_os/cli --eureka --yes  # only after the person said yes to Eureka
npx --yes @mindrian_os/cli update          # later updates; run the doctor after it
```

Shell fallback if the install fails (you run it):

```bash
claude plugin marketplace add jsagir/mindrian-marketplace
claude plugin install mos@mindrian-marketplace
```

In-app fallback, only if the shell fallback fails too (the person types it inside Claude Code):

```
/plugin marketplace add jsagir/mindrian-marketplace
/plugin install mos@mindrian-marketplace
```

Inside Claude Code, the same jobs are `/mos:doctor --fix`, `/mos:doctor` and `/mos:update`. The doctor prints one line per check (✓ marks a healthy line) and a `Summary:` line with the counts of healthy, drift and warnings. With Eureka set up, its line starts with `Eureka engine:`.

## Status check

One read-only line for A0 and for every DONE WHEN item of route A. It works in bash, zsh, PowerShell and CMD. It writes nothing. Run it with the agent shell prefix if you installed a tool in this session.

```bash
node -e "const fs=require('fs'),os=require('os'),p=require('path'),cp=require('child_process');const H=os.homedir();const j=f=>{try{return JSON.parse(fs.readFileSync(f,'utf8'))}catch(e){return null}};const out=(n,ok,d)=>console.log((ok?'PASS ':'FAIL ')+n+(d?' ('+d+')':''));let v='';try{v=cp.execSync('claude --version',{encoding:'utf8'}).trim()}catch(e){}out('A2 claude answers',v.length>0,v);const km=j(p.join(H,'.claude','plugins','known_marketplaces.json'))||{};const mk=km['mindrian-marketplace']||{};const cat=mk.installLocation?j(p.join(mk.installLocation,'.claude-plugin','marketplace.json')):null;const want=((cat&&cat.plugins)||[]).filter(x=>x.name==='mos').map(x=>x.version)[0];let got;try{got=((JSON.parse(cp.execSync('claude plugin list --json',{encoding:'utf8'}))||[]).filter(x=>x.id==='mos@mindrian-marketplace')[0]||{}).version}catch(e){}out('A4 mos installed at catalog version',Boolean(got)&&got===want,'installed '+got+', catalog '+want);const st=j(p.join(H,'.claude','settings.json'))||{};const ek=(st.extraKnownMarketplaces||{})['mindrian-marketplace']||{};const au=typeof ek.autoUpdate==='boolean'?ek.autoUpdate:mk.autoUpdate===true;out('A7 auto-update on',au,'a FAIL is fine if the person said no');const R=(st.env||{}).MINDRIAN_ROOMS_HOME||process.env.MINDRIAN_ROOMS_HOME||p.join(H,'MindrianRooms');out('A8 rooms folder exists',fs.existsSync(R),R);const L=['larry-extended','mos:larry-extended'];const pj=j(p.join(R,'.claude','settings.json'))||{};const lp=p.join(R,'.claude','settings.local.json');const lr=fs.existsSync(lp)?j(lp):{};const lj=lr||{};const loc=typeof lj.agent==='string';const eff=loc?lj.agent:pj.agent;if(lr===null)console.log('INFO '+lp+' is not valid JSON, so the pin check below cannot see what it sets');out('A8 Larry pinned in rooms folder',L.includes(eff),(eff?'agent is '+eff+' (from '+(loc?'settings.local.json':'settings.json')+')':'no agent key in the rooms folder settings')+'; a FAIL is fine if the person said no');if(typeof st.agent==='string'&&L.indexOf(st.agent)<0)console.log('INFO user-wide agent is '+st.agent+' (left as it is; the rooms folder pin wins inside the rooms folder)');const b=p.basename(R);let xd='';try{xd=cp.execSync('xdg-user-dir DESKTOP',{encoding:'utf8',stdio:['ignore','pipe','ignore']}).trim()}catch(e){}const sc=[xd,p.join(H,'Desktop'),p.join(H,'OneDrive','Desktop')].filter(Boolean).some(d=>fs.existsSync(p.join(d,b))||fs.existsSync(p.join(d,b+'.lnk')));out('A8 shortcut',sc,'a FAIL is fine if the person said no');out('A9 onboarding marker',fs.existsSync(p.join(H,'.mindrian-onboarded')));out('A9 persona file',fs.existsSync(p.join(H,'.mindrian-user.md')),'a FAIL is fine if the person chose Skip');const reg=j(p.join(R,'.rooms','registry.json'));out('A9 first room',Boolean(reg&&reg.rooms)&&Object.keys(reg.rooms).length>0)"
```

Each line starts with PASS or FAIL. Before A4 and before the restart, the later lines fail; that is expected. `claude update` is proved by its own output (SKILL.md A3), not by this line. The shortcut line looks in the usual Desktop folders only; if it fails but the check line of the shortcut block passed, the block's check decides (a WSL shortcut is on the Windows Desktop, so in WSL only the block's check applies).

What it reads (fields measured on a real install on 2026-11-19, and named in the Claude Code docs, https://code.claude.com/docs/en/plugins/loading):
- `claude plugin list --json`: an array; the MindrianOS entry has `id` `mos@mindrian-marketplace` and a `version`.
- `~/.claude/plugins/known_marketplaces.json`: the `mindrian-marketplace` entry has `installLocation` (the local catalog copy is `<installLocation>/.claude-plugin/marketplace.json`) and, once set, `autoUpdate`.
- `~/.claude/settings.json`: `claude plugin marketplace add` writes the marketplace into `extraKnownMarketplaces`. The `/plugin` auto-update toggle writes `autoUpdate` into `known_marketplaces.json` and also into that settings entry. A settings value wins when both are set.
- `<rooms folder>/.rooms/registry.json`: its `rooms` field is an object with one key per room.
- `<rooms folder>/.claude/settings.json` and `settings.local.json`: the `agent` key. The local file wins over the shared one when both set it. `agent` is a documented Claude Code setting ("Start every session as a named subagent", https://code.claude.com/docs/en/settings-reference); a project file wins over the user file. The check passes when the value in force names Larry (`mos:larry-extended`; the short form `larry-extended` also passes), and its line names the file the value came from. Claude Code deprecated a plugin's own default agent in version 2.1.323 (https://code.claude.com/docs/en/changelog): it still applies today and warns at startup. The install writes this documented setting so that Larry does not depend on it. An `INFO` line reports an `agent` key in `~/.claude/settings.json` that names another agent; the status check and the install never change that key.

## Settings changes

Use these only after the yes of A7. Each script prints the file, the value BEFORE and the value AFTER. With `preview` it writes nothing. With `apply` it first saves a backup copy next to the file (`settings.json.bak-<date and time>`), writes the change, then reads the file back and prints it. If `settings.json` is missing: the auto-update script prints `NO ENTRY` and writes nothing; the rooms-folder script says so in `preview`, and `apply` creates the file with only this key (no backup is needed, as there was no file). If it is not valid JSON, both scripts print `NOT VALID JSON` and write nothing; then use the `/plugin` toggle for auto-update and keep the default rooms folder. Both scripts work in bash, zsh, PowerShell and CMD. Source: https://code.claude.com/docs/en/settings-reference (`extraKnownMarketplaces` with `"autoUpdate": true`; `env` applies to every session).

Auto-update for `mindrian-marketplace` (run with `preview`, show the output, get the yes, then run the same line with `apply`). `NO ENTRY` means the marketplace is not declared in this file; then use the `/plugin` toggle (SKILL.md A7, way b).

```bash
node -e "const fs=require('fs'),p=require('path'),os=require('os');const m=process.argv[1];const f=p.join(os.homedir(),'.claude','settings.json');const has=fs.existsSync(f);const raw=has?fs.readFileSync(f,'utf8'):'{}';let s;try{s=JSON.parse(raw)}catch(e){console.log('NOT VALID JSON: '+f+' (nothing written)');process.exit(2)}const e=(s.extraKnownMarketplaces||{})['mindrian-marketplace'];if(e===undefined){console.log('NO ENTRY: use the /plugin toggle instead');process.exit(1)}const n=Object.assign({},e,{autoUpdate:true});console.log('FILE '+f);console.log('BEFORE '+JSON.stringify(e));console.log('AFTER  '+JSON.stringify(n));if(m==='apply'){const b=f+'.bak-'+new Date().toISOString().replace(/[:.]/g,'-');fs.writeFileSync(b,raw);s.extraKnownMarketplaces['mindrian-marketplace']=n;fs.writeFileSync(f,JSON.stringify(s,null,2)+'\n');console.log('BACKUP '+b);console.log('READ BACK '+JSON.stringify(JSON.parse(fs.readFileSync(f,'utf8')).extraKnownMarketplaces['mindrian-marketplace']))}" preview
```

Larry pin: the running agent in the rooms folder (SKILL.md A7 item 5). Run it with `preview`, show the output, get the yes, then run the same line with `apply`. It changes one key, `"agent": "mos:larry-extended"`, in `<rooms folder>/.claude/settings.json`, and keeps every other key. Next to that file it writes a record of the change, `mindrian-pin.json`, and a backup when the settings file already existed. It touches no file outside `<rooms folder>/.claude/`. `NOTHING TO CHANGE` means the pin is already there. `NO ROOMS FOLDER` means: make the rooms folder first (for a folder in another place, set `MINDRIAN_ROOMS_HOME` first). The first line, `ROOMS FOLDER`, names the folder the script works on: check that it is the folder the person chose, and that the status check names the same one. `EFFECT` says what the pin does. `STOP` means a `settings.local.json` in the rooms folder sets an `agent` (any agent, Larry too) or cannot be read: that file wins over `settings.json`, so nothing is written; show the person that line and ask what they want. `NOT VALID JSON` means nothing is written: show the person the file path, and the pin counts as a no. Run the line with `undo` to take the pin out again. `undo` works only while `settings.json` is byte for byte what the install wrote: it saves a backup, puts back the value from before and reads the file back. `LEFT AS IT IS` means the file or the record changed since, so nothing is touched and the record is kept; the person then deletes the `agent` line by hand.

```bash
node -e "const fs=require('fs'),p=require('path'),os=require('os'),cr=require('crypto');const m=process.argv[1];const H=os.homedir();const j=f=>{try{return JSON.parse(fs.readFileSync(f,'utf8'))}catch(e){return null}};const sha=x=>cr.createHash('sha256').update(x).digest('hex');const stamp=()=>new Date().toISOString().replace(/[:.]/g,'-');const st=j(p.join(H,'.claude','settings.json'))||{};const R=(st.env||{}).MINDRIAN_ROOMS_HOME||process.env.MINDRIAN_ROOMS_HOME||p.join(H,'MindrianRooms');const d=p.join(R,'.claude'),f=p.join(d,'settings.json'),lf=p.join(d,'settings.local.json'),mf=p.join(d,'mindrian-pin.json'),V='mos:larry-extended';console.log('ROOMS FOLDER '+R);if(fs.existsSync(R)===false){console.log('NO ROOMS FOLDER: '+R+' (make it first)');process.exit(1)}const has=fs.existsSync(f);const raw=has?fs.readFileSync(f,'utf8'):'{}';let s;try{s=JSON.parse(raw)}catch(e){console.log('NOT VALID JSON: '+f+' (nothing written)');process.exit(2)}if(m==='undo'){const k=j(mf);if(k===null){console.log('NOTHING TO UNDO: no pin record in '+d);process.exit(0)}if(k.file!==f||k.key!=='agent'||k.value!==V){console.log('LEFT AS IT IS: the pin record does not match this rooms folder (record kept)');process.exit(0)}if(has===false||sha(raw)!==k.sha256){console.log('LEFT AS IT IS: '+f+' changed since the install wrote it (record kept). To take Larry out by hand, delete the agent line in that file.');process.exit(0)}const b=f+'.bak-'+stamp();fs.writeFileSync(b,raw);console.log('BACKUP '+b);if(k.before===null)delete s.agent;else s.agent=k.before;if(k.created===true&&Object.keys(s).length===0){fs.unlinkSync(f);console.log('UNDONE: removed '+f+' (this install had created it)')}else{fs.writeFileSync(f,JSON.stringify(s,null,2)+'\n');console.log('UNDONE '+f+': agent = '+(k.before===null?'(no key)':k.before));console.log('READ BACK '+JSON.stringify(j(f)))}fs.unlinkSync(mf);process.exit(0)}if(fs.existsSync(lf)){const lj=j(lf);if(lj===null){console.log('STOP: '+lf+' is not valid JSON, so its agent cannot be read (nothing written)');process.exit(3)}if(typeof lj.agent==='string'){console.log('STOP: '+lf+' sets agent = '+lj.agent+'. That file wins over settings.json, so a pin would not take effect (nothing written)');process.exit(3)}}console.log('FILE '+f+(has?'':' (missing: apply creates it)'));console.log('BEFORE agent = '+(s.agent===undefined?'(no key)':s.agent));console.log('AFTER  agent = '+V);console.log('EFFECT every Claude Code session started in '+R+' starts as Larry');if(s.agent===V){console.log('NOTHING TO CHANGE');process.exit(0)}if(m==='apply'){fs.mkdirSync(d,{recursive:true});if(has){const b=f+'.bak-'+stamp();fs.writeFileSync(b,raw);console.log('BACKUP '+b)}const before=s.agent===undefined?null:s.agent;s.agent=V;const out=JSON.stringify(s,null,2)+'\n';fs.writeFileSync(f,out);fs.writeFileSync(mf,JSON.stringify({file:f,key:'agent',value:V,before:before,created:has===false,sha256:sha(out),written_at:new Date().toISOString()},null,2)+'\n');console.log('READ BACK agent = '+j(f).agent)}" preview
```

The pin takes effect in the next Claude Code session started in the rooms folder (A9 restart). If the plugin is removed and the pin stays, Claude Code still starts in the rooms folder, and the session runs without Larry (one measurement, Claude Code 2.1.332 on Windows, 2026-11-25). Run `undo` before removing the plugin.

Rooms folder in another place (replace the last argument with the full path the person chose; on Windows a path such as `C:\Users\name\Documents\MindrianRooms` is fine). Run it with `preview`, show the output, get the yes, then run the same line with `apply`:

```bash
node -e "const fs=require('fs'),p=require('path'),os=require('os');const m=process.argv[1],v=process.argv[2];const f=p.join(os.homedir(),'.claude','settings.json');const has=fs.existsSync(f);const raw=has?fs.readFileSync(f,'utf8'):'{}';let s;try{s=JSON.parse(raw)}catch(e){console.log('NOT VALID JSON: '+f+' (nothing written)');process.exit(2)}const before=(s.env||{}).MINDRIAN_ROOMS_HOME;console.log('FILE '+f+(has?'':' (missing: apply creates it)'));console.log('BEFORE env.MINDRIAN_ROOMS_HOME = '+JSON.stringify(before));console.log('AFTER  env.MINDRIAN_ROOMS_HOME = '+JSON.stringify(v));if(m==='apply'){if(has){const b=f+'.bak-'+new Date().toISOString().replace(/[:.]/g,'-');fs.writeFileSync(b,raw);console.log('BACKUP '+b)}else{fs.mkdirSync(p.dirname(f),{recursive:true})}s.env=Object.assign({},s.env,{MINDRIAN_ROOMS_HOME:v});fs.writeFileSync(f,JSON.stringify(s,null,2)+'\n');console.log('READ BACK '+JSON.stringify(JSON.parse(fs.readFileSync(f,'utf8')).env.MINDRIAN_ROOMS_HOME))}" preview "/full/path/to/MindrianRooms"
```

The new value takes effect in the next Claude Code session (A9 restart).

Any other `env` value (for example `NODE_EXTRA_CA_CERTS` from troubleshooting). Replace the last 2 arguments with the name and the value. Run it with `preview`, show the output, get the yes, then run the same line with `apply`:

```bash
node -e "const fs=require('fs'),p=require('path'),os=require('os');const m=process.argv[1],k=process.argv[2],v=process.argv[3];const f=p.join(os.homedir(),'.claude','settings.json');const has=fs.existsSync(f);const raw=has?fs.readFileSync(f,'utf8'):'{}';let s;try{s=JSON.parse(raw)}catch(e){console.log('NOT VALID JSON: '+f+' (nothing written)');process.exit(2)}console.log('FILE '+f+(has?'':' (missing: apply creates it)'));console.log('BEFORE env.'+k+' = '+JSON.stringify((s.env||{})[k]));console.log('AFTER  env.'+k+' = '+JSON.stringify(v));if(m==='apply'){if(has){const b=f+'.bak-'+new Date().toISOString().replace(/[:.]/g,'-');fs.writeFileSync(b,raw);console.log('BACKUP '+b)}else{fs.mkdirSync(p.dirname(f),{recursive:true})}s.env=Object.assign({},s.env,{[k]:v});fs.writeFileSync(f,JSON.stringify(s,null,2)+'\n');console.log('READ BACK '+JSON.stringify(JSON.parse(fs.readFileSync(f,'utf8')).env[k]))}" preview NODE_EXTRA_CA_CERTS "/full/path/to/corporate-ca.pem"
```

## Rooms folder

Create only the empty folder. The plugin default is `~/MindrianRooms`. Do not put it in a folder that OneDrive, iCloud Drive, Dropbox or Google Drive syncs: a sync tool can copy a database while it is in use, and the copy can be corrupt (https://www.sqlite.org/howtocorrupt.html, section 1.2).

```bash
# macOS, Linux, WSL
mkdir -p "$HOME/MindrianRooms"
```

```powershell
# Windows PowerShell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\MindrianRooms"
```

```bat
:: Windows CMD (if the folder exists, it prints "already exists"; that is fine)
mkdir "%USERPROFILE%\MindrianRooms"
```

For another place, use the same commands with that path, and set `env.MINDRIAN_ROOMS_HOME` (Settings changes).

## Shortcuts

Optional. Each block starts with the rooms folder in `R`; replace it if the person chose another place. Each block ends with its check. If a block fails, use the "By hand" line for the system, one step at a time.

Windows PowerShell: a Desktop shortcut, a Quick Access pin, and the check.

```powershell
$R = "$env:USERPROFILE\MindrianRooms"
$L = Join-Path ([Environment]::GetFolderPath('Desktop')) ((Split-Path $R -Leaf) + '.lnk')
$s = (New-Object -ComObject WScript.Shell).CreateShortcut($L); $s.TargetPath = $R; $s.Save()
(New-Object -ComObject Shell.Application).Namespace($R).Self.InvokeVerb('pintohome')
Test-Path $L
```

By hand (Windows): in File Explorer, right-click the folder, choose Show more options, then Send to, then Desktop (create shortcut). For Quick Access: right-click the folder, choose Pin to Quick access.

WSL (bash): a Windows Desktop shortcut to the WSL rooms folder, and the check.

```bash
R="$HOME/MindrianRooms"
W=$(wslpath -w "$R")
powershell.exe -NoProfile -Command "\$L=[Environment]::GetFolderPath('Desktop')+'\MindrianRooms.lnk';\$s=(New-Object -ComObject WScript.Shell).CreateShortcut(\$L);\$s.TargetPath='$W';\$s.Save();Test-Path \$L"
```

macOS (bash or zsh): a Desktop alias with Finder, and the check. macOS can ask whether the terminal (or your agent) may control Finder; that prompt is normal, and the person chooses OK.

```bash
R="$HOME/MindrianRooms"
osascript -e "tell application \"Finder\" to make alias file to (POSIX file \"$R\") at (path to desktop folder)"
ls -ld "$HOME/Desktop/$(basename "$R")"
```

By hand (macOS): in Finder, select the folder, hold Option and Command, and drag it to the Desktop. For the sidebar: drag the folder into the Finder sidebar under Favorites.

Linux (bash): a link on the Desktop, and the check.

```bash
R="$HOME/MindrianRooms"
D=$(xdg-user-dir DESKTOP 2>/dev/null || echo "$HOME/Desktop")
mkdir -p "$D" && ln -s "$R" "$D/$(basename "$R")"
ls -l "$D/$(basename "$R")"
```

Linux file-manager bookmark (a separate change of a settings file: show the line, get its own yes, then run):

```bash
R="$HOME/MindrianRooms"
B=~/.config/gtk-3.0/bookmarks
[ -f "$B" ] && cp "$B" "$B.bak-$(date +%Y%m%d-%H%M%S)"
mkdir -p ~/.config/gtk-3.0 && echo "file://$R" >> "$B"
tail -n 3 "$B"
```
