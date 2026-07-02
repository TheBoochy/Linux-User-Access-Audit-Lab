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
| Part 4  | Review user and group files     | Complete |
| Part 5  | Audit sudo access               | Complete |
| Part 6  | Check home folder permissions   | Complete |
| Part 7  | Create and find an access issue | Complete |
| Part 8  | Review login history            | Complete |
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
│   ├── screenshot-03b-linux-test-users-home-folders.png
│   ├── screenshot-04a-linux-passwd-file-review.png
│   ├── screenshot-04b-linux-group-file-review.png
│   ├── screenshot-04c-linux-sensitive-account-files-review.png
│   ├── screenshot-04d-linux-account-files-purpose.png
│   ├── screenshot-05a-linux-current-user-sudo-access.png
│   ├── screenshot-05b-linux-admin-groups-review.png
│   ├── screenshot-05c-linux-test-users-sudo-review.png
│   ├── screenshot-05d-linux-sudoers-files-review.png
│   ├── screenshot-06a-linux-home-folder-permissions.png
│   ├── screenshot-06b-linux-home-folder-content-review.png
│   ├── screenshot-06c-linux-home-folder-cross-access-test.png
│   ├── screenshot-06d-linux-home-folder-audit-note.png
│   ├── screenshot-07a-linux-audit-share-created.png
│   ├── screenshot-07b-linux-audit-share-test-file-created.png
│   ├── screenshot-07c-linux-audit-share-cross-user-access.png
│   ├── screenshot-07d-linux-audit-share-issue-identified.png
│   ├── screenshot-07e-linux-audit-share-finding-note.png
│   ├── screenshot-08a-linux-recent-login-history.png
│   ├── screenshot-08b-linux-test-user-login-history.png
│   ├── screenshot-08c-linux-current-login-sessions.png
│   ├── screenshot-08d-linux-lastlog-summary.png
│   └── screenshot-08e-linux-login-history-audit-note.png
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

User and group database files were reviewed. The `/etc/passwd` and `/etc/group` files were checked safely, and the lab user and group entries were reviewed with `getent`. Sensitive account files `/etc/shadow` and `/etc/gshadow` were reviewed safely by checking file ownership and permissions only, without exposing sensitive file contents.

Sudo access was reviewed. The current lab user sudo permissions were checked with `sudo -l`, admin-related groups were reviewed with `getent group`, test user sudo permissions were checked with `sudo -l -U`, and sudoers file locations were reviewed safely without displaying sensitive configuration contents.

Home folder permissions were reviewed for `audituser`, `contractor1` and `olduser`. Folder ownership and permissions were checked, home folder contents were reviewed safely, and cross-user access testing was performed with `sudo -u`.

A controlled access issue was created and identified. The `/opt/audit-share` folder and `audit-note.txt` file were configured with permissions that allowed users outside the intended `audit_team` group to read the test file. The issue was verified by testing access as multiple users and documented as a finding with risk and recommendation notes.

Successful login history was reviewed with `last`. Login history for the lab users was reviewed, current active sessions were checked with `who` and `w`, and the last login summary was reviewed with `lastlog`.

The next step is to review failed login attempts.

---

## Skills demonstrated

This project will demonstrate:

* Basic Linux administration
* Linux user review
* Linux group review
* Linux user creation
* Linux group creation
* Linux account verification
* Linux account database review
* Linux group database review
* Safe review of sensitive account files
* Account baseline documentation
* Sudo access review
* Home folder permission review
* Access auditing
* Login history review
* Failed login review
* Sudo permission review
* Admin group review
* Safe sudoers file review
* Home folder permission auditing
* Cross-user access testing
* Shared folder permission review
* Access issue identification
* Finding, risk and recommendation documentation
* Successful login history review
* Current session review
* Last login summary review
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

| Screenshot                                                | Purpose                                            |
| --------------------------------------------------------- | -------------------------------------------------- |
| `screenshot-01-project-structure.png`                     | Initial project structure                          |
| `screenshot-02a-linux-account-baseline-system-info.png`   | Linux account baseline system information          |
| `screenshot-02b-linux-account-baseline-users.png`         | Local user database review                         |
| `screenshot-02c-linux-account-baseline-groups.png`        | Local group database review                        |
| `screenshot-02d-linux-account-baseline-sudo-access.png`   | Current user sudo access review                    |
| `screenshot-02e-linux-account-baseline-home-folders.png`  | Home folder ownership and permission review        |
| `screenshot-03a-linux-test-users-and-groups-created.png`  | Test users and groups created and verified         |
| `screenshot-03b-linux-test-users-home-folders.png`        | Test user passwd entries and home folders verified |
| `screenshot-04a-linux-passwd-file-review.png`             | `/etc/passwd` file and test user entries reviewed  |
| `screenshot-04b-linux-group-file-review.png`              | `/etc/group` file and test group entries reviewed  |
| `screenshot-04c-linux-sensitive-account-files-review.png` | Sensitive account file permissions reviewed safely |
| `screenshot-04d-linux-account-files-purpose.png`          | Account file purpose summary reviewed              |
| `screenshot-05a-linux-current-user-sudo-access.png` | Current lab user sudo access reviewed |
| `screenshot-05b-linux-admin-groups-review.png` | Admin-related groups reviewed |
| `screenshot-05c-linux-test-users-sudo-review.png` | Test user sudo access reviewed |
| `screenshot-05d-linux-sudoers-files-review.png` | Sudoers file locations reviewed safely |
| `screenshot-06a-linux-home-folder-permissions.png` | Home folder permissions reviewed |
| `screenshot-06b-linux-home-folder-content-review.png` | Home folder contents reviewed safely |
| `screenshot-06c-linux-home-folder-cross-access-test.png` | Cross-user home folder access tested |
| `screenshot-06d-linux-home-folder-audit-note.png` | Home folder audit note created |
| `screenshot-07a-linux-audit-share-created.png` | Controlled audit share folder created |
| `screenshot-07b-linux-audit-share-test-file-created.png` | Audit share test file created |
| `screenshot-07c-linux-audit-share-cross-user-access.png` | Cross-user access to audit share tested |
| `screenshot-07d-linux-audit-share-issue-identified.png` | Audit share access issue identified |
| `screenshot-07e-linux-audit-share-finding-note.png` | Finding, risk and recommendation documented |
| `screenshot-08a-linux-recent-login-history.png` | Recent successful login history reviewed |
| `screenshot-08b-linux-test-user-login-history.png` | Test user login history reviewed |
| `screenshot-08c-linux-current-login-sessions.png` | Current login sessions reviewed |
| `screenshot-08d-linux-lastlog-summary.png` | Last login summary reviewed |
| `screenshot-08e-linux-login-history-audit-note.png` | Login history audit note created |

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

## Part 4 — Review user and group files

Status: Complete

This part reviewed Linux user and group database files used for local account and access management.

Files reviewed:

```text
/etc/passwd
/etc/group
/etc/shadow
/etc/gshadow
```

Commands used:

```bash
ls -l /etc/passwd
getent passwd audituser
getent passwd contractor1
getent passwd olduser

ls -l /etc/group
getent group audit_team
getent group contractors
getent group disabled_test

sudo ls -l /etc/shadow
sudo ls -l /etc/gshadow

echo "/etc/passwd stores local user account information."
echo "/etc/group stores local group information."
echo "/etc/shadow stores local password hash and password aging information."
echo "/etc/gshadow stores secure group account information."
```

Results:

* Reviewed `/etc/passwd` ownership and permissions.
* Reviewed passwd entries for `audituser`, `contractor1` and `olduser`.
* Reviewed `/etc/group` ownership and permissions.
* Reviewed group entries for `audit_team`, `contractors` and `disabled_test`.
* Reviewed `/etc/shadow` ownership and permissions safely.
* Reviewed `/etc/gshadow` ownership and permissions safely.
* Confirmed the purpose of the main Linux account database files.

Notes:

The `/etc/passwd` file stores local user account information.

The `/etc/group` file stores local group information.

The `/etc/shadow` file stores password hash and password aging information.

The `/etc/gshadow` file stores secure group account information.

Sensitive files were reviewed safely by checking file permissions only. File contents from `/etc/shadow` and `/etc/gshadow` were not displayed or documented.

The `man 5 passwd` command was not available on this system, so a safe `echo` summary was used instead for the account file purpose screenshot.

Screenshot links:

[screenshot-04a-linux-passwd-file-review.png](screenshots/screenshot-04a-linux-passwd-file-review.png)

[screenshot-04b-linux-group-file-review.png](screenshots/screenshot-04b-linux-group-file-review.png)

[screenshot-04c-linux-sensitive-account-files-review.png](screenshots/screenshot-04c-linux-sensitive-account-files-review.png)

[screenshot-04d-linux-account-files-purpose.png](screenshots/screenshot-04d-linux-account-files-purpose.png)

---

## Part 5 — Audit sudo access

Status: Complete

This part reviewed sudo access and admin-related group membership.

Commands used:

```bash
whoami
groups
sudo -l

getent group wheel
getent group sudo
getent group adm
getent group audit_team
getent group contractors
getent group disabled_test

sudo -l -U audituser
sudo -l -U contractor1
sudo -l -U olduser

sudo ls -l /etc/sudoers
sudo ls -ld /etc/sudoers.d
sudo ls -l /etc/sudoers.d
```

Results:

* Reviewed the current logged-in user.
* Reviewed the current user’s group memberships.
* Reviewed the current user’s sudo permissions with `sudo -l`.
* Reviewed common admin-related groups such as `wheel`, `sudo` and `adm`.
* Reviewed lab groups used in this project.
* Reviewed sudo permissions for `audituser`.
* Reviewed sudo permissions for `contractor1`.
* Reviewed sudo permissions for `olduser`.
* Reviewed `/etc/sudoers` ownership and permissions safely.
* Reviewed `/etc/sudoers.d` ownership and permissions safely.
* Reviewed files inside `/etc/sudoers.d` safely.

Notes:

This part demonstrates basic sudo access auditing.

The `sudo -l` command was used to review sudo permissions for the current lab user.

The `sudo -l -U` command was used to review sudo permissions for specific test users.

The sudoers file locations were reviewed safely with `ls` commands. The contents of `/etc/sudoers` were not displayed or documented.

Screenshot links:

[screenshot-05a-linux-current-user-sudo-access.png](screenshots/screenshot-05a-linux-current-user-sudo-access.png)

[screenshot-05b-linux-admin-groups-review.png](screenshots/screenshot-05b-linux-admin-groups-review.png)

[screenshot-05c-linux-test-users-sudo-review.png](screenshots/screenshot-05c-linux-test-users-sudo-review.png)

[screenshot-05d-linux-sudoers-files-review.png](screenshots/screenshot-05d-linux-sudoers-files-review.png)

---

## Part 6 — Check home folder permissions

Status: Complete

This part reviewed home folder ownership, permissions and cross-user access behavior.

Home folders reviewed:

```text
/home/audituser
/home/contractor1
/home/olduser
```

Commands used:

```bash
ls -ld /home
ls -ld /home/audituser
ls -ld /home/contractor1
ls -ld /home/olduser

sudo ls -la /home/audituser | head -20
sudo ls -la /home/contractor1 | head -20
sudo ls -la /home/olduser | head -20

sudo -u audituser ls /home/contractor1
sudo -u contractor1 ls /home/audituser
sudo -u olduser ls /home/audituser

echo "Home folder permissions were reviewed for audituser, contractor1 and olduser."
echo "Cross-user access testing was performed using sudo -u."
echo "Any world-readable home folder permissions should be reviewed in a real environment."
```

Results:

* Reviewed `/home` ownership and permissions.
* Reviewed `/home/audituser` ownership and permissions.
* Reviewed `/home/contractor1` ownership and permissions.
* Reviewed `/home/olduser` ownership and permissions.
* Reviewed home folder contents safely with administrator access.
* Tested whether `audituser` could access `contractor1` home folder.
* Tested whether `contractor1` could access `audituser` home folder.
* Tested whether `olduser` could access `audituser` home folder.
* Created an audit note about reviewing world-readable home folder permissions.

Notes:

This part demonstrates basic home folder permission auditing.

Home folders can contain user-specific files, so ownership and permissions should be reviewed during an access audit.

Cross-user access testing helps identify whether users can access folders that may not be intended for them.

In a real environment, world-readable home folder permissions should be reviewed carefully because they may expose user files or configuration data.

Screenshot links:

[screenshot-06a-linux-home-folder-permissions.png](screenshots/screenshot-06a-linux-home-folder-permissions.png)

[screenshot-06b-linux-home-folder-content-review.png](screenshots/screenshot-06b-linux-home-folder-content-review.png)

[screenshot-06c-linux-home-folder-cross-access-test.png](screenshots/screenshot-06c-linux-home-folder-cross-access-test.png)

[screenshot-06d-linux-home-folder-audit-note.png](screenshots/screenshot-06d-linux-home-folder-audit-note.png)


---

## Part 7 — Create and identify an access issue

Status: Complete

This part created a controlled access issue and then identified it through permission review and cross-user access testing.

Test location used:

```text
/opt/audit-share
```

Commands used:

```bash
sudo mkdir -p /opt/audit-share
sudo chown root:audit_team /opt/audit-share
sudo chmod 775 /opt/audit-share
ls -ld /opt/audit-share

echo "This is a safe lab audit test file." | sudo tee /opt/audit-share/audit-note.txt
sudo chown root:audit_team /opt/audit-share/audit-note.txt
sudo chmod 664 /opt/audit-share/audit-note.txt
ls -l /opt/audit-share

sudo -u audituser cat /opt/audit-share/audit-note.txt
sudo -u contractor1 cat /opt/audit-share/audit-note.txt
sudo -u olduser cat /opt/audit-share/audit-note.txt

ls -ld /opt/audit-share
ls -l /opt/audit-share/audit-note.txt
id audituser
id contractor1
id olduser

echo "Finding: /opt/audit-share allows users outside audit_team to read audit-note.txt."
echo "Risk: Users who are not intended audit team members may access shared audit content."
echo "Recommendation: Restrict folder and file permissions to the intended group only."
```

Results:

* Created the `/opt/audit-share` test folder.
* Set folder ownership to `root:audit_team`.
* Set folder permissions to `775`.
* Created the safe test file `audit-note.txt`.
* Set file ownership to `root:audit_team`.
* Set file permissions to `664`.
* Tested file access as `audituser`.
* Tested file access as `contractor1`.
* Tested file access as `olduser`.
* Reviewed folder permissions, file permissions and user group memberships.
* Identified that users outside the intended `audit_team` group could read the test file.
* Documented the finding, risk and recommendation.

Notes:

This part demonstrates how an access issue can be created and identified in a controlled lab environment.

The issue was caused by permissive folder and file permissions. The folder permission `775` allowed other users to enter the folder, and the file permission `664` allowed other users to read the file.

The test data was safe lab content only. No real personal data, credentials, secrets or production files were used.

In a real environment, shared folders and files should be reviewed to confirm that access is limited to the intended users or groups.

Screenshot links:

[screenshot-07a-linux-audit-share-created.png](screenshots/screenshot-07a-linux-audit-share-created.png)

[screenshot-07b-linux-audit-share-test-file-created.png](screenshots/screenshot-07b-linux-audit-share-test-file-created.png)

[screenshot-07c-linux-audit-share-cross-user-access.png](screenshots/screenshot-07c-linux-audit-share-cross-user-access.png)

[screenshot-07d-linux-audit-share-issue-identified.png](screenshots/screenshot-07d-linux-audit-share-issue-identified.png)

[screenshot-07e-linux-audit-share-finding-note.png](screenshots/screenshot-07e-linux-audit-share-finding-note.png)


---

## Part 8 — Review login history

Status: Complete

This part reviewed successful login history, current sessions and last login information.

Commands used:

```bash
last | head -20

last audituser | head -10
last contractor1 | head -10
last olduser | head -10

who
w

lastlog | head -20

echo "Successful login history was reviewed with last."
echo "Current active sessions were reviewed with who and w."
echo "Last login summary was reviewed with lastlog."
echo "Unused or unexpected accounts should be reviewed in a real environment."
```

Results:

* Reviewed recent successful login history with `last`.
* Reviewed login history for `audituser`.
* Reviewed login history for `contractor1`.
* Reviewed login history for `olduser`.
* Reviewed currently logged-in users with `who`.
* Reviewed active sessions and activity with `w`.
* Reviewed last login summary with `lastlog`.
* Created an audit note about login history review.
* Confirmed that private internal lab IP addresses may appear in login history output.

Notes:

This part demonstrates basic Linux login history review.

The `last` command shows successful login history from system login records.

The `who` and `w` commands show currently logged-in users and active sessions.

The `lastlog` command shows the most recent login status for local accounts.

Private internal lab addresses, such as addresses in the `192.168.x.x` range, may appear in login history when using a local VM, NAT or lab network.

In a real environment, unexpected login times, unknown source addresses, unused accounts with recent logins, or abandoned accounts should be reviewed.

Screenshot links:

[screenshot-08a-linux-recent-login-history.png](screenshots/screenshot-08a-linux-recent-login-history.png)

[screenshot-08b-linux-test-user-login-history.png](screenshots/screenshot-08b-linux-test-user-login-history.png)

[screenshot-08c-linux-current-login-sessions.png](screenshots/screenshot-08c-linux-current-login-sessions.png)

[screenshot-08d-linux-lastlog-summary.png](screenshots/screenshot-08d-linux-lastlog-summary.png)

[screenshot-08e-linux-login-history-audit-note.png](screenshots/screenshot-08e-linux-login-history-audit-note.png)


## Notes

This is a lab environment and not a production system.

The project is created for learning, documentation and portfolio demonstration.

Only safe test data should be used in this lab.

No real personal data, passwords, SSH keys, tokens, production configuration files or sensitive business files should be included in screenshots or public documentation.
