# RHEL/CentOS 8 Goss config

## Overview

based on CIS 2.0.0

Ability to audit a system using a lightweight binary to check the current state.

This is:

- very small 11MB
- lightweight
- self contained

It works using a set of configuration files and directories to audit STIG of RHEL/CentOS 7 servers. These files/directories correlate to the STIG Level and STIG_ID

Tested on

- RHEL8
- CentOS8
- Rocky8
- Alma-Linux 8

## Join us

On our [Discord Server](https://discord.gg/JFxpSgPFEJ) to ask questions, discuss features, or just chat with other Ansible-Lockdown users

## Requirements

You must have [goss](https://github.com/aelsabbahy/goss/) available to your host you would like to test.

You must have sudo/root access to the system as some commands require privilege information.

Assuming you have already clone this repository you can run goss from where you wish.

Please refer to the audit documentation for usage.

- [Audit Documents](https://github.com/ansible-lockdown/RHEL8-CIS/docs/Security_remediation_and_auditing.md)

This also works alongside the [Ansible Lockdown RHEL8-CIS role](https://github.com/ansible-lockdown/RHEL8-CIS)

Which will:

- install
- audit
- remediate
- audit

## variables

These are found in vars/STIG.yml
Please refer to the file for all options and their meanings

STIG listed variable for every control/benchmark can be turned on/off or section

### The variable files

In this case installed or skipped using the standard name for a package to be installed or _skip to skip a test.

### Extra settings

Some sections can have several options in that case the skip flag maybe passed to the test or exact details relating to your requirements
e.g.

- rhel7stig_use_gui
- rhel7stig_is_router
- rhel7_stig_nameservers:
  - 8.8.8.8
  - 9.9.9.9

## Examples

- full check

```sh

# {{path to your goss binary}} --vars {{ path to the vars file }} -g {{path to your clone of this repo }}/goss.yml v

```

- example:

```sh
# /usr/local/bin/goss --vars ../vars/stig.yml -g /home/bolly/rh7_cis_goss/goss.yml validate
......FF....FF................FF...F..FF.............F........................FSSSS.............FS.F.F.F.F.........FFFFF....

Failures/Skipped:

Title: CAT_2 | RHEL-07-040641 | Must ignore Internet Protocol version 4 (IPv4) Internet Control Message Protocol (ICMP) redirect messages from being accepted.
KernelParam: net.ipv4.conf.all.accept_redirects: value:
Expected
    <string>: 1
to equal
    <string>: 0

Title: CAT_2 | RHEL-07-021000 | Must prevent files with the setuid and setgid bit set from being executed on file systems that are used with removable media.
Mount: /mnt: exists:
Expected
    <bool>: false
to equal
    <bool>: true

< ---------cut ------- >

Title: CAT_2 | RHEL-07-010280 | Must be configured so that passwords are a minimum of 15 characters in length.
File: /etc/security/pwquality.conf: contains: patterns not found: [/^minlen = 15/]

Title: CAT_2 | RHEL-07-040500 | Must for networked systems, synchronize clocks with a server that is synchronized to one of the redundant United States Naval Observatory (USNO) time servers, a time server designated for the appropriate DoD network (NIPRNet/SIPRNet), and/or the Global Positioning System (GPS).
File: /etc/chrony.conf: contains: patterns not found: [/^server.*maxpoll 10/]

Title: CAT_2 | RHEL-07-010310 | Must disable account identifiers (individuals, groups, roles, and devices) if the password expires.
File: /etc/default/useradd: contains: patterns not found: [/^INACTIVE=0/]

Total Duration: 31.127s
Count: 308, Failed: 162, Skipped: 21
```

- running a particular section of tests

```sh
# /usr/local/bin/goss -g /home/bolly/rh7_cis_goss/section_1/cis_1.1/cis_1.1.22.yml  validate
............

Total Duration: 0.033s
Count: 12, Failed: 0, Skipped: 0
```

- changing the output

```sh
# /usr/local/bin/goss -g /home/bolly/rh7_stig_goss/Cat_2/RHEL-07-010030.yml  validate -f documentation
goss -g Cat_2/RHEL-07-020240.yml  --vars vars/stig.yml v -f documentation
Title: CAT_2 | RHEL-07-020240 | Must define default permissions for all authenticated users in such a way that the user can only read and modify their own files.
File: /etc/login.defs: exists: matches expectation: [true]
File: /etc/login.defs: mode: matches expectation: ["0644"]
File: /etc/login.defs: contains: patterns not found: [/^UMASK 077]


Failures/Skipped:

Title: CAT_2 | RHEL-07-020240 | Must define default permissions for all authenticated users in such a way that the user can only read and modify their own files.
File: /etc/login.defs: contains: patterns not found: [/^UMASK 077]

Total Duration: 0.000s
Count: 3, Failed: 1, Skipped: 0
```

## further information

- [goss documentation](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#patterns)
- [CIS standards](https://www.cisecurity.org)

