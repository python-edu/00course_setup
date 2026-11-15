# Computer setup for practical courses

Prepare a separate standard user account and terminal tools for practical classes. Use the guide for your operating system.

---

# Contents

- [Setup workflow](#setup-workflow)
- [Guides](#guides)

---

# Setup workflow

<div align="center">

```mermaid
flowchart TB
    A([Start on your main account]) --> OS{Operating system?}
    OS -->|Windows 10 / 11| T[Check Teams desktop installation for new users]
    OS -->|macOS / Linux| U[Choose a course account name]
    T --> U
    U --> N[Create a standard user account]
    N --> S[Account settings]
    S --> W{Windows?}
    W -->|Yes| WG[Check / install WinGet]
    WG --> P[Install PowerShell 7]
    P --> PS[Configure PowerShell 7]
    W -->|No| SH[Configure Bash / Zsh terminal]
    PS --> M[Install micro]
    SH --> M
    M --> MS[Configure micro]
    MS --> G[Install Git]
    G --> GS[Configure Git]
    GS --> Q{Do the tools work?}
    Q -->|No| TR[Troubleshooting]
    TR --> Q
    Q -->|Yes| R([Computer ready for the course])
    R -.-> C[After the course: backup and cleanup]
```

</div>

---

# Guides

| File | Operating system |
|---|---|
| [f01_new_account_windows11.md](f01_new_account_windows11.md) | Windows 11 |
| [f02_new_account_windows10.md](f02_new_account_windows10.md) | Windows 10 |
| [f03_new_account_macos.md](f03_new_account_macos.md) | macOS |
| [f04_new_account_linux.md](f04_new_account_linux.md) | Debian / Ubuntu |
