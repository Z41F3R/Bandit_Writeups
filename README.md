<div align="center">

```text
██████╗  █████╗ ███╗   ██╗██████╗ ██╗████████╗
██╔══██╗██╔══██╗████╗  ██║██╔══██╗██║╚══██╔══╝
██████╔╝███████║██╔██╗ ██║██║  ██║██║   ██║
██╔══██╗██╔══██║██║╚██╗██║██║  ██║██║   ██║
██████╔╝██║  ██║██║ ╚████║██████╔╝██║   ██║
╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═══╝╚═════╝ ╚═╝   ╚═╝
```

**OverTheWire Bandit — Linux & Security Fundamentals**

![OverTheWire](https://img.shields.io/badge/OverTheWire-Bandit-2ea44f?style=for-the-badge\&logo=linux\&logoColor=white)
![Niveles](https://img.shields.io/badge/Niveles-33_completados-2ea44f?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Finalizado-gold?style=for-the-badge)

*33 levels. One environment. Practical problem solving.*

[Writeups](levels/) · [OverTheWire](https://overthewire.org/wargames/bandit/)

</div>

---

## Overview

This repository documents the complete progression through the **OverTheWire Bandit** wargame.

Bandit is focused on learning the basics of Linux, command-line environments, networking and security through a series of progressively challenging levels.

Rather than documenting only the final answers, each writeup focuses on the **approach used to identify, analyze and solve the problem**.

```text
TARGET
  |
  v
ENUMERATION
  |
  v
ANALYSIS
  |
  v
TECHNIQUE
  |
  v
SOLUTION
```

---

## Progress

```text
[########################################] 33 / 33

STATUS    : COMPLETED
PLATFORM  : OVER THE WIRE
TARGET    : BANDIT
LEVELS    : 33
```

| Category             | Techniques                           |
| -------------------- | ------------------------------------ |
| Linux                | Files, permissions, processes, shell |
| Enumeration          | `find`, `grep`, `nmap`               |
| Networking           | SSH, Netcat, SSL/TLS                 |
| File Analysis        | `file`, `strings`, `xxd`             |
| Encoding             | Base64, ROT13                        |
| Automation           | Shell scripting, brute force         |
| Privilege Escalation | SUID, restricted environments        |
| Git                  | Commits, tags, repositories          |

---

## Levels

|  Level  | Focus                | Technique              | Writeup                  |
| :-----: | -------------------- | ---------------------- | ------------------------ |
| 00 → 01 | SSH                  | Initial authentication | [00](levels/level-00.md) |
| 01 → 02 | Files                | Special filename       | [01](levels/level-01.md) |
| 02 → 03 | Files                | Spaces in filenames    | [02](levels/level-02.md) |
| 03 → 04 | Files                | Hidden files           | [03](levels/level-03.md) |
| 04 → 05 | Analysis             | `file`                 | [04](levels/level-04.md) |
| 05 → 06 | Enumeration          | `find`                 | [05](levels/level-05.md) |
| 06 → 07 | Enumeration          | Advanced search        | [06](levels/level-06.md) |
| 07 → 08 | Text                 | `grep`                 | [07](levels/level-07.md) |
| 08 → 09 | Text                 | `sort` / `uniq`        | [08](levels/level-08.md) |
| 09 → 10 | Analysis             | `strings`              | [09](levels/level-09.md) |
| 10 → 11 | Encoding             | Base64                 | [10](levels/level-10.md) |
| 11 → 12 | Encoding             | ROT13                  | [11](levels/level-11.md) |
| 12 → 13 | Files                | `xxd` / `gzip` / `tar` | [12](levels/level-12.md) |
| 13 → 14 | Authentication       | SSH keys               | [13](levels/level-13.md) |
| 14 → 15 | Networking           | Netcat                 | [14](levels/level-14.md) |
| 15 → 16 | Networking           | SSL/TLS                | [15](levels/level-15.md) |
| 16 → 17 | Enumeration          | Nmap                   | [16](levels/level-16.md) |
| 17 → 18 | Analysis             | `diff`                 | [17](levels/level-17.md) |
| 18 → 19 | Shell                | Restricted environment | [18](levels/level-18.md) |
| 19 → 20 | Privilege Escalation | SUID                   | [19](levels/level-19.md) |
| 20 → 21 | Networking           | Process communication  | [20](levels/level-20.md) |
| 21 → 22 | Linux                | Cron                   | [21](levels/level-21.md) |
| 22 → 23 | Linux                | Automated scripts      | [22](levels/level-22.md) |
| 23 → 24 | Linux                | Script manipulation    | [23](levels/level-23.md) |
| 24 → 25 | Automation           | Brute force            | [24](levels/level-24.md) |
| 25 → 26 | Shell                | Restricted shell       | [25](levels/level-25.md) |
| 26 → 27 | Shell                | Shell escape           | [26](levels/level-26.md) |
| 27 → 28 | Git                  | Repository analysis    | [27](levels/level-27.md) |
| 28 → 29 | Git                  | Commit history         | [28](levels/level-28.md) |
| 29 → 30 | Git                  | Information recovery   | [29](levels/level-29.md) |
| 30 → 31 | Git                  | Tags / references      | [30](levels/level-30.md) |
| 31 → 32 | Git                  | Remote repository      | [31](levels/level-31.md) |
| 32 → 33 | Shell                | Restricted shell       | [32](levels/level-32.md) |

---

## Techniques

### Linux

```text
File system
├── Navigation
├── Hidden files
├── Special filenames
├── Permissions
└── Process inspection

Shell
├── Bash
├── Restricted environments
├── Shell escapes
└── Command execution

Automation
└── Cron
```

### Networking

```text
SSH
  └── Authentication

Netcat
  └── Service interaction

Nmap
  └── Port / service enumeration

OpenSSL
  └── SSL/TLS communication
```

### File & Data Analysis

```text
grep
sort
uniq
strings
file
xxd
gzip
tar
```

### Git

```text
Repositories
├── Commits
├── History
├── Tags
├── References
└── Remote interaction
```

---

## Writeup Format

Each level follows a consistent documentation structure:

```text
┌────────────────────────────────────────────┐
│ OBJECTIVE                                  │
├────────────────────────────────────────────┤
│ What needs to be discovered?               │
├────────────────────────────────────────────┤
│ ENUMERATION                                │
├────────────────────────────────────────────┤
│ What information can be gathered?          │
├────────────────────────────────────────────┤
│ ANALYSIS                                   │
├────────────────────────────────────────────┤
│ What does the collected information mean?  │
├────────────────────────────────────────────┤
│ SOLUTION                                   │
├────────────────────────────────────────────┤
│ Commands and technique used                │
├────────────────────────────────────────────┤
│ TAKEAWAYS                                  │
└────────────────────────────────────────────┘
```

The intention is to preserve the reasoning behind each solution rather than simply provide the final credential.

---

## Repository Structure

```text
Bandit/
├── levels/
│   ├── level-00.md
│   ├── level-01.md
│   ├── level-02.md
│   ├── ...
│   └── level-32.md
│
├── image.png
└── README.md
```

---

## Toolset

```text
Linux
Bash
SSH
Netcat
Nmap
OpenSSL
Git
grep
find
strings
file
xxd
gzip
tar
cron
```

---

## Learning Path

Bandit represents the Linux and command-line foundation of a broader offensive security learning path.

```text
                 BANDIT
                   |
        +----------+----------+
        |          |          |
      Linux    Networking    Shell
        |          |          |
        +----------+----------+
                   |
                   v
              Python
                   |
                   v
             Automation
                   |
                   v
         Offensive Security
                   |
             +-----+-----+
             |           |
         Pentesting    Red Team
```

---

## Security & Ethics

This repository is intended exclusively for educational purposes.

All techniques documented here were performed within the authorized **OverTheWire Bandit** environment.

The material should not be used against systems without explicit authorization.

---

<div align="center">

**33 / 33 — COMPLETED**

```text
$ whoami
learner

$ cat /etc/motd
keep learning.
```

</div>
