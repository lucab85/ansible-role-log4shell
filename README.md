lucab85.ansible_role_log4shell
=========

[![CI](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/ci.yml/badge.svg)](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/ci.yml)
[![Release](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/release.yml/badge.svg)](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/release.yml)

Ansible role to scan target Linux hosts using the official Red Hat Log4j detector script RHSB-2021-009 for Log4Shell (CVE-2021-44228).

Tested with [Red Hat version 1.3 detector 2022-01-10](https://access.redhat.com/security/vulnerabilities/RHSB-2021-009).

Ansible Playbook
------------

Code also available as Ansible Playbook [lucab85/log4j-cve-2021-44228](https://github.com/lucab85/log4j-cve-2021-44228)

Requirements
------------

ansible 2.9+

Role Variables
--------------

The default variable values - `defaults/main.yml`:

```yaml
sh_detector: "cve-2021-44228--2022-01-10-1242.sh"
sh_signature: 'cve-2021-44228--2022-01-10-1242.sh.asc'
detector_baseurl: 'https://access.redhat.com/sites/default/files/'
detector_path: "/var/"
detector_dir: "/opt/cve-2021-44228/"
detector_run_dir: 'tmp'
detector_options: '-n -d --no-progress --scan {{ detector_path }}'
gpg_keyid: '7514F77D8366B0D9'
gpg_server: "pgp.mit.edu"
clean_run_before: true
delete_after: true
verify_gpg: false
```

- `sh_detector`: the filename of the detector bash script file
- `sh_signature`: the filename of the detector GPG signature file
- `detector_baseurl`: the base URL to download the previous files
- `detector_path`: the path to inspect (default `/var/`)
- `detector_dir`: the download path of the detector (default `detector_dir` - `/opt/cve-2021-44228/`) Note: volume requires exec permission!
- `detector_run_dir`: the subdirectory to create before the run (default `tmp`)
- `detector_options`: the command lines options for detector script (default `-n -d --no-progress --scan {{ detector_path }}`)
- `gpg_keyid`: the GPG public key to download for the verification (default Red Hat Product Security `7514F77D8366B0D9`)
- `gpg_server`: the GPG server where to download the GPG public key (default `pgp.mit.edu`)
- `clean_run_before`: remove the run directory and recreate before the execution - detector requires an empty directory (default `true`)
- `delete_after`: remove the _detector_dir_ after the execution (default `false`)
- `verify_gpg`: perform the GPG signature download and verification (default: `false`)


Dependencies
------------

None.

Download
------------

First download the latest version of Ansible role [lucab85.ansible_role_log4shell](https://galaxy.ansible.com/lucab85/ansible_role_log4shell) Ansible Galaxy:

```bash
ansible-galaxy install lucab85.ansible_role_log4shell

```

Example Playbook
----------------

This is an example of how to use the `lucab85.ansible_role_log4shell` role (with variables passed in as parameters):

```yaml
---
- name: run detector
  hosts: all
  become: true
  roles:
    - role: lucab85.ansible_role_log4shell
      detector_path: "/var/www"

```

License
-------

MIT / BSD

## Author Information

This role was created in 2021 by [Luca Berton](https://www.lucaberton.it/), author of [Ansible Pilot](https://www.ansiblepilot.com/).

## Ansible Pilot

More information:

- [Website](https://www.ansiblepilot.com/)
- [Ansible Pilot YouTube channel](https://www.youtube.com/channel/UC5MNbTYRHSCu9vAki3z9SmA)
- [Medium](https://ansiblepilot.medium.com/)
- [Twitter](https://twitter.com/ansiblepilot)

## Donate

Thank you for supporting me:

- [Patreon](https://patreon.com/lucaberton)
- [Buy me a pizza](https://www.buymeacoffee.com/lucab)
- [GitHub sponsor](https://github.com/sponsors/lucab85)
