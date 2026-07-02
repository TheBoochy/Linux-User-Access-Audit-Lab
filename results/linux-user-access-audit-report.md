# Linux User Access Audit Report

## Report metadata

| Field       | Detail                      |
| ----------- | --------------------------- |
| Project     | Linux User Access Audit Lab |
| Host        | srv-linuxops01              |
| Public user | Vulkan                      |
| Environment | Local lab                   |
| Report type | User access audit           |
| Date        | 2026-07-02                  |

---

## Scope

This report summarizes a local Linux user access audit performed in a safe lab environment.

The audit covered:

* Linux account baseline review.
* Local user review.
* Local group review.
* User and group database file review.
* Sudo access review.
* Home folder permission review.
* Controlled access issue identification.
* Successful login history review.
* Failed login attempt review.

No real personal data, production files, passwords, SSH keys, tokens or secrets were used.

---

## Systems and accounts reviewed

### System reviewed

```text
srv-linuxops01
```

### Main lab user

```text
vulkan
```

### Test users reviewed

```text
audituser
contractor1
olduser
```

### Groups reviewed

```text
audit_team
contractors
disabled_test
auditors
wheel
sudo
adm
```

---

## Summary of work performed

The Linux system baseline was reviewed before access audit scenarios were created. This included hostname, operating system version, kernel version, current user, group memberships, date, uptime and home folder structure.

Local user and group information was reviewed with `getent passwd` and `getent group`.

Test users and groups were created or verified for the lab scenario.

User and group database files were reviewed safely. Sensitive files such as `/etc/shadow` and `/etc/gshadow` were checked by reviewing ownership and permissions only.

Sudo access was reviewed for the current user and test users. Sudoers file locations were reviewed safely without displaying sensitive configuration contents.

Home folder ownership and permissions were reviewed. Cross-user access testing was performed with `sudo -u`.

A controlled access issue was created in `/opt/audit-share`, identified through permission checks and documented as a finding.

Successful login history was reviewed with `last`, `who`, `w` and `lastlog`.

Failed login review was performed with `faillock` and `journalctl`.

---

## Findings

### Finding 1 — Controlled audit share readable by users outside `audit_team`

| Field          | Detail                                                                                                                                                                 |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Severity       | Medium                                                                                                                                                                 |
| Location       | `/opt/audit-share/audit-note.txt`                                                                                                                                      |
| Issue          | Users outside the intended `audit_team` group could read the test file.                                                                                                |
| Evidence       | `screenshot-07c-linux-audit-share-cross-user-access.png`, `screenshot-07d-linux-audit-share-issue-identified.png`, `screenshot-07e-linux-audit-share-finding-note.png` |
| Risk           | Users who are not intended audit team members may access shared audit content.                                                                                         |
| Recommendation | Restrict folder and file permissions to the intended group only.                                                                                                       |

#### Finding explanation

The folder `/opt/audit-share` was configured with permission `775`.

This allowed users outside the owning group to enter the folder.

The file `/opt/audit-share/audit-note.txt` was configured with permission `664`.

This allowed users outside the owning group to read the file.

The issue was confirmed by testing access as multiple users and reviewing each user’s group memberships.

---

## Observations

### Observation 1 — Sudo access reviewed safely

Sudo access was reviewed with `sudo -l` and `sudo -l -U`.

Sudoers file locations were reviewed with `ls` commands only. The contents of `/etc/sudoers` were not displayed or documented.

### Observation 2 — Home folder permissions reviewed

Home folder ownership and permissions were reviewed for the lab users.

Cross-user access testing was performed to identify whether users could access home folders that may not be intended for them.

### Observation 3 — Successful login history reviewed

Successful login history was reviewed with `last`.

Current login sessions were reviewed with `who` and `w`.

Last login information was reviewed with `lastlog`.

### Observation 4 — Failed login attempts reviewed

Failed login records were reviewed with `faillock`.

SSH authentication logs were reviewed with `journalctl`.

Unexpected or repeated failed logins should be investigated in a real environment.

---

## Recommended actions

For a real environment, the following actions would be recommended:

* Review group membership regularly.
* Remove users from groups they no longer require.
* Review sudo access regularly.
* Keep sudo access limited to users who need administrative privileges.
* Review home folder permissions for excessive access.
* Restrict shared folders to intended users or groups.
* Review successful login history for unexpected access.
* Review failed login attempts for signs of password guessing or unauthorized access attempts.
* Disable or remove unused accounts.
* Document findings, risks and recommendations during access reviews.

---

## Evidence list

| Evidence                                                 | Description                               |
| -------------------------------------------------------- | ----------------------------------------- |
| `screenshot-02a-linux-account-baseline-system-info.png`  | System baseline information reviewed.     |
| `screenshot-03a-linux-test-users-and-groups-created.png` | Test users and groups verified.           |
| `screenshot-04a-linux-passwd-file-review.png`            | User database file reviewed.              |
| `screenshot-05a-linux-current-user-sudo-access.png`      | Current user sudo access reviewed.        |
| `screenshot-06a-linux-home-folder-permissions.png`       | Home folder permissions reviewed.         |
| `screenshot-07c-linux-audit-share-cross-user-access.png` | Cross-user access issue tested.           |
| `screenshot-07d-linux-audit-share-issue-identified.png`  | Access issue identified.                  |
| `screenshot-08a-linux-recent-login-history.png`          | Recent successful login history reviewed. |
| `screenshot-09a-linux-failed-login-summary.png`          | Failed login summary reviewed.            |

---

## Conclusion

The Linux User Access Audit Lab demonstrated a structured beginner-level access audit workflow.

The audit reviewed accounts, groups, sudo access, home folder permissions, shared folder permissions, successful login history and failed login attempts.

A controlled access issue was created and identified to demonstrate how permission problems can be detected and documented.

The project provides practical evidence of Linux access review, basic security auditing, Markdown documentation, screenshot evidence collection and GitHub-based portfolio workflow.
