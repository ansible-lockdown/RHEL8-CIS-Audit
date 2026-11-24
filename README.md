# RHEL 8 Syver config

## Overview

based on CIS v4.0.0

Ability to audit a system using a lightweight binary to check the current state.

This is:

- very small
- lightweight
- self contained

It works using a set of configuration files and directories to audit RHEL 8 family servers against the CIS benchmark. These files/directories correlate to the CIS Level and CIS_ID

Tested on

- RHEL8
- Rocky8
- Alma-Linux 8
- Oracle 8

## Requirements

You must have [syver](https://github.com/krameff/syver) >= 0.20.0 available to your host you would like to test. The audit file is syver.yml.

Syver replaces goss as it is a signed fork that is regularly updated.

You must have sudo/root access to the system as some commands require privilege information.

Assuming you have already clone this repository you can run syver from where you wish.

Please refer to the audit documentation for usage.

- [readthedocs](https://ansible-lockdown.readthedocs.io/en/latest/)

This also works alongside the [Ansible Lockdown RHEL8-CIS role](https://github.com/ansible-lockdown/RHEL8-CIS)

Which will:

- install
- audit
- remediate
- audit

## Join us

On our [Discord Server](https://discord.io/ansible-lockdown) to ask questions, discuss features, or just chat with other Ansible-Lockdown users

## Contributing

Bug reports and feature requests are welcome from everyone, please raise an issue.

Pull requests are accepted from approved contributors only. To be onboarded, join the [Discord Server](https://www.lockdownenterprise.com/discord) and request contributor access. See [CONTRIBUTING.md](CONTRIBUTING.md) for the full process.

Set of configuration files and directories to run the first stages of CIS of RHEL 8 servers

This is configured in a directory structure level.

Syver is run based on the syver.yml file in the top level directory. This specifies the configuration.

## further information

- [Syver documentation](https://github.com/krameff/syver/blob/main/docs/index.md)
- [goss vs Syver](https://github.com/krameff/syver/blob/main/docs/goss-vs-syver.md)
- [CIS standards](https://www.cisecurity.org)
