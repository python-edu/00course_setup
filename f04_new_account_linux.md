# Preparing Linux (Debian / Ubuntu)

---

# Contents

- [New account](#new-account)
- [Account settings](#account-settings)
- [Terminal](#terminal)
- [Micro installation](#micro-installation)
- [Helix](#helix)
- [Git installation](#git-installation)
- [Troubleshooting](#troubleshooting)
- [Cleanup](#cleanup)

---

# New account

On the **main administrator account**:

1. Choose the account name:

   **Account name:** `________________`

   Examples: `coding_lab`, `gis_lab`, `rs_lab`, `science_lab`.

2. Replace `COURSE_NAME` with your chosen name and run:

   ```bash
   sudo adduser COURSE_NAME
   ```

3. Enter a password when prompted.
4. Sign out and sign in to the new account.

---

# Account settings

On the **new account**, open a terminal and check:

```bash
whoami
printf '%s\n' "$HOME"
```

---

# Terminal

Open the terminal provided by your desktop environment (`bash`).

---

## Terminal setup

On the **new account**:

```bash
echo "$SHELL"
echo "$HOME"
```

---

# Micro installation

On the **main administrator account**, install micro and the clipboard utilities:

```bash
sudo apt update
sudo apt install micro xclip wl-clipboard
```

On the **new account**, check:

```bash
micro -version
```

---

## Micro setup

On the **new account**:

1. Open micro:

   ```bash
   micro
   ```

2. Press **Ctrl+E**; enter these settings one by one, pressing **Enter** after each:

   ```text
   set tabsize 4
   set tabstospaces true
   set tabmovement true
   set autoindent true
   set smartpaste false
   set clipboard external
   set syntax true
   set matchbrace true
   set hltrailingws true
   set colorcolumn 80
   set hlsearch true
   bind Alt-s SaveAs

   set relativeruler false
   bind Ctrl-j "command-edit:jump "
   ```

   - `tabsize 4` – four spaces per indentation level.
   - `tabstospaces true` – insert spaces instead of tab characters.
   - `tabmovement true` – move the cursor across indentation in groups of four spaces.
   - `autoindent true` – preserve indentation while typing.
   - `smartpaste false` – do not add extra indentation when pasting.
   - `clipboard external` – use the system clipboard.
   - `syntax true` – highlight code syntax.
   - `matchbrace true` – highlight matching brackets.
   - `hltrailingws true` – highlight trailing whitespace at the end of lines.
   - `colorcolumn 80` – display a vertical guide at column 80.
   - `hlsearch true` – highlight all search matches.
   - `bind Alt-s SaveAs` – assign **Alt+S** to Save As (**Ctrl+S** remains Save).
   - `set relativeruler false` – show **absolute** line numbers (the default). Use `set relativeruler true` to display distances from the current line instead; `false` restores absolute numbering.
   - `bind Ctrl-j "command-edit:jump "` – **Ctrl+J** opens a relative line jump; enter a number (for example, `5` down or `-5` up) and press **Enter**. The final space is required.

3. Close the editor with **Ctrl+Q**; settings are saved.
4. Set micro as the default editor **permanently** for this user:

   ```bash
   echo 'export EDITOR=micro' >> ~/.bashrc
   ```

5. Close the terminal, open it again and check:

   ```bash
   echo "$EDITOR"
   ```

   Expected output: `micro`.

---

# Helix

[Helix](https://helix-editor.com/) is a modal text editor. Start it with `hx`.

## Course build (master)

Build from commit `872b24025` (Linux x86-64).

On the **new account**:

1. Download [helix-872b24025-linux-x86_64.tar.gz](helix-872b24025-linux-x86_64.tar.gz) to `~/Downloads`.
2. Extract the archive:

   ```bash
   cd ~/Downloads
   tar -xzf helix-872b24025-linux-x86_64.tar.gz
   cd helix-872b24025-DISTRIBUTION
   ```

3. Copy the program and configuration:

   ```bash
   mkdir -p ~/.local/bin ~/.config/helix
   cp hx ~/.local/bin/hx
   cp -a helix/. ~/.config/helix/
   chmod +x ~/.local/bin/hx
   ```

4. Check the command:

   ```bash
   command -v hx
   ```

   If there is no output (Bash), add Helix to `PATH`:

   ```bash
   echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
   source ~/.bashrc
   ```

   Check again:

   ```bash
   command -v hx
   ```

## Test

```bash
hx --version
hx program.py
```

## Configuration

Configuration file: `~/.config/helix/config.toml`.

1. The course archive includes the configuration. It is copied during installation. An existing `config.toml` may be overwritten.
2. Check the configuration file:

   ```bash
   ls -l ~/.config/helix/config.toml
   ```

3. Set Helix **permanently** as the default editor for this account:

   ```bash
   echo 'export EDITOR=hx' >> ~/.bashrc
   ```

4. Close the terminal, open it again and check:

   ```bash
   echo "$EDITOR"
   ```

   Expected output: `hx`.

---

# Git installation

First check on the course account:

```bash
git --version
```

If Git is not installed, use the **administrator account**:

```bash
sudo apt install git
```

Return to the course account and verify:

```bash
git --version
```

---

## Git setup

On the **new account**, enter your own name and email address:

```bash
git config --global user.name "Name Surname"
git config --global user.email "your-address@example.com"
git config --global core.editor micro
git config --global init.defaultBranch main
```

Alternative editors (choose one instead of `micro`):

```bash
git config --global core.editor hx
git config --global core.editor nvim
git config --global core.editor vim
git config --global core.editor nano
```

Check:

```bash
git config --global --list
```

---

# Troubleshooting

If APT cannot find `micro`, check the Debian/Ubuntu release and enabled repositories. If account creation is restricted, contact the computer administrator.

---

# Cleanup

If you want to clean up the computer after the course:

1. Back up any files you want to keep from the course account.
2. Sign out of the new account.
3. On the administrator account, replace `COURSE_NAME` with the chosen name:

   ```bash
   sudo deluser --remove-home COURSE_NAME
   ```

4. Confirm the account name before running the command.

