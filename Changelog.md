# Changes to RHEL8-CIS-Audit

Aug 2026
Based on 4.0.0

goss.yml updated to add missings tests
1.8.x desktop tests updated and fixed

July 2026
Based on CIS 4.0.0

- run_Audit script not at latest version
- benchmark_version updated to v
- variable naming aligned and unused tidied up

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
