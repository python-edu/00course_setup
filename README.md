# Computer setup for practical courses

Create a separate standard user account and follow the guide for your operating system.

# Setup workflow

<div align="center">

```mermaid
flowchart TB
    OS("Operating system") -->|Windows / macOS| TEAMS("Microsoft Teams")
    OS -->|Linux| ACCOUNT("Create course account")
    TEAMS --> ACCOUNT
    ACCOUNT --> SETTINGS("Account settings")
    SETTINGS -->|Windows| WINGET("WinGet")
    WINGET --> PS("Install PowerShell 7")
    SETTINGS -->|macOS / Linux| TERMINAL("Terminal")

    PS --> J1(( ))
    TERMINAL --> J1
    J1 --> EDITORS("Install editors: micro + Helix")
    EDITORS --> J2(( ))
    J2 --> GIT("Install Git")
    GIT --> J3(( ))
    J3 --> READY("Ready for the course")
    READY -.-> CLEANUP("Cleanup after the course")

    FILESYSTEM("Filesystem exercises") -.-> J1
    MICRO("Micro exercises") -.-> J2
    HELIX("Helix exercises") -.-> J2
    GITEX("Git exercises") -.-> J3
    FILESYSTEM ~~~ MICRO ~~~ HELIX ~~~ GITEX

    classDef exercise fill:#d1d5db,stroke:#9ca3af,color:#0550ae,stroke-width:1px
    classDef junction fill:#596b80,stroke:#596b80,color:#596b80,stroke-width:0px
    class FILESYSTEM,MICRO,HELIX,GITEX exercise
    class J1,J2,J3 junction

    click FILESYSTEM "https://github.com/python-edu/exercises/tree/main/filesystem" "Filesystem exercises" _blank
    click MICRO "https://github.com/python-edu/exercises/tree/main/micro" "Micro exercises" _blank
    click HELIX "https://github.com/python-edu/exercises/tree/main/helix" "Helix exercises" _blank
    click GITEX "https://github.com/python-edu/git_intro/blob/main/git_basics.md" "Git exercises" _blank
```

</div>

Exercises: [filesystem](https://github.com/python-edu/exercises/tree/main/filesystem) · [micro](https://github.com/python-edu/exercises/tree/main/micro) · [Helix](https://github.com/python-edu/exercises/tree/main/helix) · [Git](https://github.com/python-edu/git_intro/blob/main/git_basics.md)

# Guides

| Operating system | Guide |
|---|---|
| Windows 11 | [f01_new_account_windows11.md](f01_new_account_windows11.md) |
| Windows 10 | [f02_new_account_windows10.md](f02_new_account_windows10.md) |
| macOS | [f03_new_account_macos.md](f03_new_account_macos.md) |
| Debian / Ubuntu | [f04_new_account_linux.md](f04_new_account_linux.md) |
