# RHEL/CentOS 8 Goss config 

## Overview
based on CIS 3.01

Set of configuration files and directories to run the first stages of CIS of RHEL/CentOS 8 servers

This is configured in a directory structure level.

This could do with further testing but sections 1.x should be complete

Goss is run based on the goss.yml file in the top level directory. This specifies the configuration.


## variables

these are found in vars/cis.yml
Please refer to the file for all options and their meanings

CIS listed variable for every control/benchmark can be turned on/off or section

- other controls
enable_selinux
run_heavy_tasks

- bespoke options
If a site has specific options e.g. password complexity these can also be set.
## Usage

You must have [goss](https://github.com/aelsabbahy/goss/) available to your host you would like to test.

You must have sudo/root acces sto the system as some commands require privilege information.
- Run as root not sudo due to sudo and shared memory access

Assuming you have already clone this repository you can run goss from where you wish.

- full check
```
$ sudo {{path to your goss binary}} --vars {{ path to the vars file }} -g {{path to your clone of this repo }}/goss.yml --validate
```

example:
```
$ sudo /usr/local/bin/goss --vars ../vars/cis.yml -g /home/bolly/rh8_cis_goss/goss.yml validate
......FF....FF................FF...F..FF.............F........................FSSSS.............FS.F.F.F.F.........FFFFF....

Failures/Skipped:

Title: 1.6.1 Ensure core dumps are restricted (Automated)_sysctl
Command: suid_dumpable_2: exit-status:
Expected
    <int>: 1
to equal
    <int>: 0
Command: suid_dumpable_2: stdout: patterns not found: [fs.suid_dumpable = 0]


Title: 1.4.2 Ensure filesystem integrity is regularly checked (Automated)
Service: aidecheck: enabled:
Expected
    <bool>: false
to equal
    <bool>: true
Service: aidecheck: running:
Expected
    <bool>: false
to equal
    <bool>: true

< ---------cut ------- >

Title: 1.1.22 Ensure sticky bit is set on all world-writable directories
Command: version: exit-status:
Expected
    <int>: 0
to equal
    <int>: 123

Total Duration: 5.102s
Count: 124, Failed: 21, Skipped: 5

```
- running a particular section of tests

```
$ sudo /usr/local/bin/goss -g /home/bolly/rh8_cis_goss/section_1/cis_1.1/cis_1.1.22.yml  validate
............

Total Duration: 0.033s
Count: 12, Failed: 0, Skipped: 0

```

- changing the output

```
$ sudo /usr/local/bin/goss -g /home/bolly/rh8_cis_goss/section_1/cis_1.1/cis_1.1.22.yml  validate -f documentation
Title: 1.1.20 Check for removeable media nodev
Command: floppy_nodev: exit-status: matches expectation: [0]
Command: floppy_nodev: stdout: matches expectation: [OK]
< -------cut ------- >
Title: 1.1.20 Check for removeable media noexec
Command: floppy_noexec: exit-status: matches expectation: [0]
Command: floppy_noexec: stdout: matches expectation: [OK]


Total Duration: 0.022s
Count: 12, Failed: 0, Skipped: 0
```
## Variables

### The variable files
vars/cis.yml allows you to tune it further for specific environments.
In this case installed or skipped using the standard name for a package to be installed or _skip to skip a test.


## Extra settings



Some sections can have several options in that case the skip flag maybe passed to the test.
e.g. 
- section_1/cis/1.8 - need to review the MOTD and issue files for bespoke content
- section_1/cis_1.10/cis_1.10.yml  - Has gdm either not installed or configured default to not installed and skipped configured.
## further information

- [goss documentation](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#patterns)
- [CIS standards](https://www.cisecurity.org)

## Outstanding
- To add other sections
- 1.2.2 and 1.9 have extended timeout - This maybe a new switch (ignore heavy tasks?)
- 4.1.13 needs review 
- 4.2.1.5 remote syslog server? variable? 
- 4.2.1.6 listen as syslog server?  
- create template for the restictive settings in section_6 allows for more options

- 6.1.13 & 6.1.14 does this need a default exclusion list for expected files?
- 6.2.1 to work thorugh the file and regex the answers
- 6.2.4 to test heavily
