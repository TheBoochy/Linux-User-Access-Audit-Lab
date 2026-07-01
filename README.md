# Linux User Access Audit Lab

## Overview

Linux User Access Audit Lab is a beginner-friendly sysadmin and security portfolio project focused on Linux user access review.

The lab is designed to practice account review, group review, sudo access checks, home folder permission checks, login history review and basic access audit documentation.

Public documentation uses the name **Vulkan**.

---

## Scenario

A small organization uses a Linux server for internal work.

The goal of this lab is to act as a junior system administrator and perform a basic user access audit.

The lab focuses on safe beginner-level access review in a controlled environment. It uses test data only and does not include real personal data, passwords, secrets or production files.

---

## Lab goals

The goals of this lab are to:

* Create a clean Linux user access audit project.
* Review the Linux account baseline.
* Create test users and groups.
* Review user and group database files.
* Audit sudo access.
* Check home folder permissions.
* Create and identify an access issue.
* Review login history.
* Review failed login attempts.
* Create an access audit report.
* Document findings with screenshots.
* Track work through Git and GitHub.

---

## Planned parts

| Part    | Topic                           | Status   |
| ------- | ------------------------------- | -------- |
| Part 1  | Repository setup                | Complete |
| Part 2  | Linux account baseline          | Complete |
| Part 3  | Create test users and groups    | Complete |
| Part 4  | Review user and group files     | Planned  |
| Part 5  | Audit sudo access               | Planned  |
| Part 6  | Check home folder permissions   | Planned  |
| Part 7  | Create and find an access issue | Planned  |
| Part 8  | Review login history            | Planned  |
| Part 9  | Review failed login attempts    | Planned  |
| Part 10 | Create access audit report      | Planned  |
| Part 11 | Final README and GitHub polish  | Planned  |

---

## Project structure

```text
Linux-User-Access-Audit-Lab/
├── docs/
│   └── .gitkeep
├── results/
│   └── .gitkeep
├── screenshots/
│   ├── .gitkeep
│   ├── screenshot-01-project-structure.png
│   ├── screenshot-02a-linux-account-baseline-system-info.png
│   ├── screenshot-02b-linux-account-baseline-users.png
│   ├── screenshot-02c-linux-account-baseline-groups.png
│   ├── screenshot-02d-linux-account-baseline-sudo-access.png
│   ├── screenshot-02e-linux-account-baseline-home-folders.png
│   ├── screenshot-03a-linux-test-users-and-groups-created.png
│   └── screenshot-03b-linux-test-users-home-folders.png
├── scripts/
│   └── .gitkeep
├── logbook.md
└── README.md
```

---

## Current progress

The project structure has been created.

The Linux account baseline has been reviewed, including hostname, current user, user ID, group memberships, operating system version, kernel version, date and uptime.

Local user database entries were reviewed with `getent passwd`.

Local group database entries were reviewed with `getent group`.

Current sudo access was reviewed with `groups` and `sudo -l`.

Home folder ownership and permissions were reviewed with `ls`.

Test users and groups were created for access audit scenarios. The lab users `audituser`, `contractor1` and `olduser` were verified. The groups `audit_team`, `contractors` and `disabled_test` were also verified. The `audituser` account was added to the `audit_team` group, `contractor1` was added to the `contractors` group, and `olduser` was added to the `disabled_test` group.

The next step is to review user and group database files.

---

## Skills demonstrated

This project will demonstrate:

* Basic Linux administration
* Linux user review
* Linux group review
* Linux user creation
* Linux group creation
* Linux account verification
* Account baseline documentation
* Sudo access review
* Home folder permission review
* Access auditing
* Login history review
* Failed login review
* Markdown documentation
* Screenshot-based evidence collection
* Git and GitHub workflow

---

## Documentation and evidence

Main documentation files:

| File         | Purpose                      |
| ------------ | ---------------------------- |
| `README.md`  | Main GitHub project overview |
| `logbook.md` | Step-by-step project notes   |

Screenshot evidence is stored in the `screenshots/` folder.

Current screenshot evidence:

| Screenshot                                               | Purpose                                            |
| -------------------------------------------------------- | -------------------------------------------------- |
| `screenshot-01-project-structure.png`                    | Initial project structure                          |
| `screenshot-02a-linux-account-baseline-system-info.png`  | Linux account baseline system information          |
| `screenshot-02b-linux-account-baseline-users.png`        | Local user database review                         |
| `screenshot-02c-linux-account-baseline-groups.png`       | Local group database review                        |
| `screenshot-02d-linux-account-baseline-sudo-access.png`  | Current user sudo access review                    |
| `screenshot-02e-linux-account-baseline-home-folders.png` | Home folder ownership and permission review        |
| `screenshot-03a-linux-test-users-and-groups-created.png` | Test users and groups created and verified         |
| `screenshot-03b-linux-test-users-home-folders.png`       | Test user passwd entries and home folders verified |

Command results and verification output may be stored in:

```text
results/
```

Scripts may be stored in:

```text
scripts/
```

---

## Part 2 — Linux account baseline

Status: Complete

This part reviewed the Linux account baseline before creating test users, groups or access audit scenarios.

Commands used:

```bash
hostnamectl
whoami
id
cat /etc/os-release
uname -r
date
uptime

getent passwd | head -20
getent passwd | tail -20

getent group | head -20
getent group | tail -20

groups
sudo -l

ls -ld /home
ls -l /home
```

Results:

* Reviewed hostname and system identity.
* Verified the current logged-in user.
* Reviewed user ID and group membership information.
* Reviewed the Linux operating system version.
* Reviewed the kernel version.
* Reviewed current date and uptime.
* Reviewed local user database entries.
* Reviewed local group database entries.
* Reviewed current user group membership.
* Reviewed current user sudo privileges.
* Reviewed `/home` directory ownership and permissions.
* Reviewed existing home folders.

Notes:

This baseline check gives the project a clear starting point before access audit scenarios are created.

The commands used in this part are common Linux account review commands and are useful for helpdesk, junior sysadmin and beginner security work.

Screenshot links:

[screenshot-02a-linux-account-baseline-system-info.png](screenshots/screenshot-02a-linux-account-baseline-system-info.png)

[screenshot-02b-linux-account-baseline-users.png](screenshots/screenshot-02b-linux-account-baseline-users.png)

[screenshot-02c-linux-account-baseline-groups.png](screenshots/screenshot-02c-linux-account-baseline-groups.png)

[screenshot-02d-linux-account-baseline-sudo-access.png](screenshots/screenshot-02d-linux-account-baseline-sudo-access.png)

[screenshot-02e-linux-account-baseline-home-folders.png](screenshots/screenshot-02e-linux-account-baseline-home-folders.png)

---

## Part 3 — Create test users and groups

Status: Complete

This part created and verified safe lab users and groups for access audit testing.

The groups used were:

```text
audit_team
contractors
disabled_test
```

The test users used were:

```text
audituser
contractor1
olduser
```

Commands used:

```bash
sudo groupadd audit_team
sudo groupadd contractors
sudo groupadd disabled_test

sudo useradd -m -G audit_team audituser
sudo useradd -m -G contractors contractor1
sudo useradd -m -G disabled_test olduser

sudo usermod -aG audit_team audituser

sudo passwd audituser
sudo passwd contractor1
sudo passwd olduser

id audituser
id contractor1
id olduser

getent group audit_team
getent group contractors
getent group disabled_test

getent passwd audituser
getent passwd contractor1
getent passwd olduser

ls -ld /home/audituser
ls -ld /home/contractor1
ls -ld /home/olduser
```

Results:

* Created or verified the `audit_team` group.
* Created or verified the `contractors` group.
* Created or verified the `disabled_test` group.
* Verified the `audituser` test account.
* Created and verified the `contractor1` test account.
* Created and verified the `olduser` test account.
* Added `audituser` to the `audit_team` group.
* Added `contractor1` to the `contractors` group.
* Added `olduser` to the `disabled_test` group.
* Set safe lab passwords for the test users.
* Verified user IDs and group memberships with `id`.
* Verified group membership with `getent group`.
* Verified passwd database entries with `getent passwd`.
* Verified home folder ownership and permissions with `ls -ld`.

Notes:

The test users and groups are safe lab accounts used only for access audit practice.

The `audituser` account already existed in the lab environment, so its group membership was updated and verified instead of treating it as a newly created account.

The `audituser` account also had membership in the `auditors` group. This is useful for later access review because it gives the audit scenario an account with multiple group memberships.

Screenshot links:

[screenshot-03a-linux-test-users-and-groups-created.png](screenshots/screenshot-03a-linux-test-users-and-groups-created.png)

[screenshot-03b-linux-test-users-home-folders.png](screenshots/screenshot-03b-linux-test-users-home-folders.png)

---

## Notes

This is a lab environment and not a production system.

The project is created for learning, documentation and portfolio demonstration.

Only safe test data should be used in this lab.

No real personal data, passwords, SSH keys, tokens, production configuration files or sensitive business files should be included in screenshots or public documentation.
