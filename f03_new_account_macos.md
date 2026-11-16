# Preparing macOS

---

# Contents

- [New account](#new-account)
- [Account settings](#account-settings)
- [Terminal](#terminal)
- [Terminal setup](#terminal-setup)
- [Micro installation](#micro-installation)
- [Micro setup](#micro-setup)
- [Git installation](#git-installation)
- [Git setup](#git-setup)
- [Troubleshooting](#troubleshooting)
- [Cleanup](#cleanup)

---

# New account

On the **main administrator account**:

1. Check that the **Teams desktop application** is installed in **Applications** and can be opened. If missing, download it from [Microsoft Teams](https://www.microsoft.com/en-us/microsoft-teams/download-app).
2. Choose a course account name:

   **Account name:** `________________`

   Examples: `coding_lab`, `gis_lab`, `rs_lab`, `science_lab`.

3. Open **System Settings → Users & Groups → Add User**.
4. Choose **Standard**, enter the chosen account name and a password.
5. Sign out and sign in to the new account.

---

# Account settings

On the **new account**:

1. Open **Finder → Settings → Advanced**.
2. Enable **Show all filename extensions**.

---

# Terminal

Open the macOS **Terminal** application (`zsh`).

---

# Terminal setup

On the **new account**, in Terminal:

```bash
whoami
printf '%s\n' "$HOME"
```

If Homebrew is already installed on the computer, make its programs available to the new account.

**Apple Silicon:**

```bash
eval "$(/opt/homebrew/bin/brew shellenv)"
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
```

**Intel:**

```bash
eval "$(/usr/local/bin/brew shellenv)"
echo 'eval "$(/usr/local/bin/brew shellenv)"' >> ~/.zprofile
```

Use the path corresponding to your Mac.

---

# Micro installation

On the **main account that manages Homebrew**:

1. If Homebrew is missing, install it following [brew.sh](https://brew.sh/).
2. In Terminal run:

   ```bash
   brew install micro
   ```

3. Sign in to the **new account**, open Terminal and check:

   ```bash
   micro -version
   ```

---

# Micro setup

On the **new account**, in Terminal:

1. Start micro:

   ```bash
   micro
   ```

2. Press **Ctrl+E**; enter each setting separately and press **Enter**:

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
   ```

   - `tabsize 4` – four spaces per indentation level.
   - `tabstospaces true` – insert spaces instead of tab characters.
   - `tabmovement true` – move the cursor across indentation in groups of four spaces.
   - `autoindent true` – preserve indentation while typing.
   - `smartpaste false` – do not add extra indentation when pasting.
   - `clipboard external` – use the Windows clipboard.
   - `syntax true` – highlight code syntax.
   - `matchbrace true` – highlight matching brackets.
   - `hltrailingws true` – highlight trailing whitespace at the end of lines.
   - `colorcolumn 80` – display a vertical guide at column 80.
   - `hlsearch true` – highlight all search matches.
   - `bind Alt-s SaveAs` – assign **Alt+S** to Save As (**Ctrl+S** remains Save).
   ```text

3. Press **Ctrl+Q** to exit; settings are saved.
4. Set micro as the default editor **permanently** for this user:

   ```bash
   echo 'export EDITOR=micro' >> ~/.zshrc
   ```

5. Close Terminal, open it again and check:

   ```bash
   echo "$EDITOR"
   ```

   Expected output: `micro`.

---

# Git installation

First check on the course account:

```bash
git --version
```

If Git is already available, proceed to its configuration. Otherwise, on the **main account that manages Homebrew**:

```bash
brew install git
```

Return to the course account and check:

```bash
git --version
command -v git
```

---

# Git setup

On the **new account**, replace the example identity:

```bash
git config --global user.name "Name Surname"
git config --global user.email "your-address@example.com"
git config --global core.editor micro
git config --global init.defaultBranch main
```

Alternative editors (choose one instead of `micro`):

```bash
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

**`brew`, `micro` or `git` not found:**

1. Open a new Terminal window.
2. Check where the commands are located:

   ```bash
   command -v brew
   command -v micro
   command -v git
   printf '%s\n' "$PATH"
   ```

3. If Homebrew is installed but not visible, repeat the corresponding `brew shellenv` step in **Terminal setup**.
4. If `brew install` fails on the standard account, perform it on the main account that manages Homebrew. Do not run `sudo brew`.

If account creation is blocked, ask the computer administrator.

---

# Cleanup

1. Back up any files you want to keep from the course account.
2. Sign out of the course account.
3. On the main administrator account, open **System Settings → Users & Groups**.
4. Select the course account you created and remove it, including its home directory if no longer needed.


