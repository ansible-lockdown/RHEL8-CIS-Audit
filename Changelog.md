# Changes to RHEL8-CIS-Audit

Oct 2026
Based on 4.0.0

- 1.3.1.5 rule gate and titles corrected
- 3.3.2.4 rule gate, titles and CIS_ID corrected
- 4.1.7 title and CIS_ID corrected
- 5.1.18 config check changed to file resource
- 5.1.18 MaxAuthTries regex anchored
- 1.4.2 level gate added
- 1.5.3, 2.1.3 gated level 2
- 2.1.20, 2.2.3 gated level 1
- server/workstation meta aligned to v4.0.0 for 1.1.1.11, 1.2.1.5, 1.5.3, 1.8.4, 2.1.3, 2.1.11, 2.1.20, 2.2.5, 3.3.1.1
- 5.1.3 path, modes, title and CIS_ID corrected
- sshd -T checks made case-insensitive
- 6.2.2.3, 5.3.3.2.5, 6.3.3.22, 1.7.2 checks corrected
- 6.2.2.6, 6.2.2.7, 2.1.10, 2.1.21 gates corrected
- 3.1.1 IPv6-disabled tests gated on ipv6_required
- 5.4.1.1, 5.4.1.2 existing user checks rewritten
- 7.2.3, 5.4.2.8 process substitution removed
- 7.1.12 document marker, find command and exclude path fixed
- warning banner and system_is_log_server aligned in vars
- 1.3.1.x skipped when rhel8cis_selinux_disable is set
- 5.4.1.3 existing user check rewritten

Aug 2026
Based on 4.0.0

goss.yml updated to add missings tests
1.8.x desktop tests updated and fixed

July 2026
Based on CIS 4.0.0

- run_Audit script not at latest version
- benchmark_version updated to v
- variable naming aligned and unused tidied up
- README updates and updated contributing and contributors

Based on CIS 2.0.0

- Control 3.1.1
  - Added option to audit disable IPv6 via sysctl (original method) or via the kernel
- updated to cis 2.0.0
- many changes
  - new checks
  - reordering of content
  - httpd server  variable is now web_server

Based on CIS 1.0.1

## 0.6

- audit script improvements
- metadata consistency
- issue #20 adopted thanks @dmaraidonis

## 0.5

- fixed some typos and alignments
- 6.2.20 simplify
- renamed vars file to CIS inline with other naming

## 0.4

- fixed some typos and alignments
- added simple bash script to run goss

## 0.3

- Aligned with CIS 1.0.1 along with lockdown role

## 0.2

- updates to layout
- lint stds
- logic improvements
- general fixes
- alignment of variables with remediation role

## 0.1 initial release
