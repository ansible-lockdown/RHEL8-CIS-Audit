# Changes to RHEL8-CIS-Audit

## CIS Benchmark 4.0.0
## November 2026 - QA fixes

- syver.yml replaces goss.yml, syver-version 0.20.0
- syver.yml discovery for partitions, postfix and opasswd files
- run_audit.sh minimum syver 0.20.0, default AUDIT_FILE syver.yml
- run_audit.sh: OS name and version fall back when /etc/os-release is missing
- README requires syver 0.20.0
- standalone.yml follows syver.yml, 6.2.3.x included
- CISv8 metadata removed
- .gitignore: secret, key and QA artifact patterns
- vars: rhel8cis_bootloader_password and rhel8cis_crypto_policy match the role defaults
- vars: rhel8cis_disruption_high, rhel8cis_allow_authselect_updates and rhel8cis_force_user_* skip gates
- vars: rhel8cis_sudoers_exclude_nopasswd_list, rhel8cis_system_users_shell, rhel8cis_dotperm_ansiblemanaged
- vars: rhel8cis_rsyslog_ansiblemanaged, rhel8cis_logrotate, rhel8cis_playbook_user
- 3.1.1: IPv6 enabled test skipped with a reason when rhel8cis_ipv6_required is false
- 5.1.7, 5.1.16, 5.1.19, 5.4.2.5: titles aligned to the benchmark
- 1.1.2.1.2 - 1.1.2.1.4: options read from fstab or tmp.mount
- 1.1.2.3.x - 1.1.2.7.x: mount option tests skipped with a reason when the partition is not separate
- 1.1.2.3.x: /home fstab pattern anchored
- 1.2.1.2, 1.2.1.3: repo files checked for 0, false or no
- 1.3.1.x: skipped with a reason when rhel8cis_selinux_disable is set
- 1.4.2: grub files in /boot/grub2 checked on BIOS and UEFI, /boot/efi files and fmask on UEFI
- 1.5.9, 1.5.10: effective coredump.conf value checked
- 1.6.3: weak MAC check follows the benchmark, NO-WEAKMAC module checked
- 1.6.5: chacha20-poly1305 pattern corrected
- 1.6.6: ssh_etm or etm@openssh-server checked in the current policy
- 1.7.1, 1.7.3: inverse regexes closed
- 1.7.1 - 1.7.3: escape sequences checked
- 1.8.3: dconf section headers matched literally
- 2.1.8: cyrus-imapd package name
- 2.1.19: nginx-plus package checked
- 2.1.23: runs on non mail servers, ports 25, 465, 587, postfix main.cf when installed
- 2.1.x, 2.2.x, 3.1.1, 3.1.3, 3.3.1.1: opt-outs skipped with a reason
- 2.3.3: root user check follows the benchmark
- 2.4.1.2 - 2.4.1.8: mode 0700/0600 or more restrictive
- 3.1.1: kernel method checks every boot entry with grubby
- 3.1.2: wireless check uses the benchmark module test
- 3.3.1.1: level 2 gate
- 3.3.2.x: skipped with a reason when rhel8cis_ipv6_required is false
- 4.1.6: loopback rich rules checked
- titles aligned to the benchmark for 1.1.2.2.1, 1.2.1.2, 1.2.1.4, 1.4.2, 1.5.9, 1.6.1, 1.6.5, 1.8.2
- titles aligned to the benchmark for 2.1.6, 2.1.12, 2.1.14, 2.1.23, 2.2.2, 3.1.2, 3.3.1.16, 3.3.1.18
- 5.1.4: private host keys checked with the benchmark script, ssh_keys group 0640 or root 0600
- 5.1.5: public host key variable fixed, owner checked on its own, globs quoted
- 5.1.6: sshd -T allow and deny entries checked per configured value
- 5.1.7: sshd_config.d Banner none grep reads the files
- 5.1.9: ClientAliveInterval and ClientAliveCountMax above zero, anchored
- 5.1.19: MaxSessions above 10 fails
- 5.1.20: MaxStartups config pattern anchored
- 5.2.2: !use_pty in sudoers files fails
- 5.2.3: sudo logfile check without bashism
- 5.2.4: rhel8cis_sudoers_exclude_nopasswd_list users excluded
- 5.2.5: grep pattern without stray escape
- 5.2.6: timestamp_timeout 0 to 15 accepted
- 5.2.7: pam_wheel options in any order, sugroup members checked with a file resource
- 5.3.2.1 - 5.3.2.4: skipped unless rhel8cis_disruption_high and rhel8cis_allow_authselect_updates
- 5.3.2.5: pam_unix lines matched with any control value
- 5.3.3.1.1, 5.3.3.1.2, 5.3.3.2.1, 5.3.3.2.2, 5.3.3.2.4, 5.3.3.2.5, 5.3.3.3.1: any compliant value accepted
- 5.3.3.1.3: root_unlock_time under 60 fails
- 5.4.1.1, 5.4.1.2, 5.4.1.3: existing users checked per account
- 5.4.1.1, 5.4.1.2, 5.4.1.3: existing user checks skipped unless the matching rhel8cis_force_user_* var
- 5.4.1.3: login.defs checked with a file resource
- 5.4.1.5: INACTIVE anchored, existing interactive users checked
- 5.4.1.6: password change dates compared as epoch seconds
- 5.4.2.1, 5.4.2.2, 5.4.2.3: fail on any extra UID or GID 0 entry
- 5.4.2.1, 5.4.2.2, 5.4.2.7, 5.4.2.8: skipped unless rhel8cis_disruption_high
- 5.4.2.4: locked root account accepted
- 5.4.2.5: root PATH checks for empty, current and unsafe directories
- 5.4.2.6: root umask checked in effect and in the files
- 5.4.2.7: UID_MIN, nobody and rhel8cis_system_users_shell used
- 5.4.2.7: connecting user excluded with rhel8cis_playbook_user
- 5.4.3.1: commented nologin lines ignored
- 5.4.3.2: TMOUT checked in every file, readonly and exported
- 5.4.3.3: login.defs UMASK and all shell init files checked
- 6.1.2: aide cron job matched with the benchmark regex, aidecheck timer tests render
- 6.1.3: aide.conf audit tool lines checked with a file resource
- 6.2.1.1.2: review warning check can fail
- 6.2.1.1.4 - 6.2.1.1.6: effective journald values read with systemd-analyze cat-config
- 6.2.1.2.1 - 6.2.1.2.4: skipped on log servers
- 6.2.1.2.4: systemd-journal-remote.service checked
- 6.2.2.2, 6.2.2.4 - 6.2.2.7: skipped unless rhel8cis_rsyslog_ansiblemanaged
- 6.2.2.3: effective ForwardToSyslog value checked
- 6.2.2.4: every FileCreateMode value checked
- 6.2.2.5: rsyslog rule anchors fixed
- 6.2.2.6: skipped unless rhel8cis_remote_log_server
- 6.2.2.7: skipped on log servers
- 6.2.2.8: logrotate.conf frequency and rotate checked
- 6.2.3.1: lastlog typo fixed, symlinks followed, every log file checked by class, skipped unless rhel8cis_disruption_high
- 6.3.1.2, 6.3.1.3: every boot entry checked
- 6.3.1.3: audit_backlog_limit compared as a number
- 6.3.2.2 - 6.3.2.4: auditd.conf settings anchored
- 6.3.3.3: rhel8cis_sudolog_location used
- 6.3.3.6: privileged commands checked on disk and in the running rules
- 6.3.3.20, 6.3.3.21: -c and -e 2 lines matched per the benchmark
- 6.3.4.1 - 6.3.4.4: audit log directory read from auditd.conf, every log file checked
- 6.3.4.5 - 6.3.4.7: audit config files checked with find
- 6.3.4.7: group owner checked
- 6.3.4.8 - 6.3.4.10: audit tools checked per file
- 7.1.1 - 7.1.4, 7.1.9: mode 644 or more restrictive accepted
- 7.1.10: opasswd and opasswd.old checked, skipped when absent
- 7.1.11, 7.1.12: mounts read with findmnt, benchmark prune paths
- 7.1.13: SUID and SGID files checked for package ownership and integrity
- 7.2.4 - 7.2.7: duplicates found with sort before uniq -d
- 7.2.8: home directory tests limited to local interactive users
- 7.2.9: dot file mode and owner checked, skipped unless rhel8cis_disruption_high and rhel8cis_dotperm_ansiblemanaged
- 6.x, 7.1.x: titles aligned to the benchmark

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
- LICENSE updated to 2026 MindPoint Group - A Quantum Sky Company
- vars/CIS.yml parse error fixed
- 6.2.1.1.1 CCI key fixed
- 1.8.4 path and contents fixed; 1.8.5 contents swapped back
- 7.1.10 checks /etc/security/opasswd
- 6.2.1.2.2 checks journal-upload.conf.d
- 1.2.1.2, 1.2.1.3 regexes terminated
- CIS_ID and titles corrected for 7.1.1, 3.3.1.3, 3.3.1.6, 3.3.2.6, 1.6.6, 1.1.2.7.3, 1.2.1.3, 5.3.3.3.3, 1.5.7, 5.4.2.8
- 1.5.7 conf regex fixed
- NIST800-53R4 keys renamed R5
- document markers fixed in 7 files
- vars/CIS.yml: 6 vars added, 12 unused removed, defaults aligned to role
- README describes the CIS audit

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
