lucab85.ansible_role_log4shell
=========

[![CI](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/ci.yml/badge.svg)](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/ci.yml)
[![Release](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/release.yml/badge.svg)](https://github.com/lucab85/ansible-role-log4shell/actions/workflows/release.yml)

Ansible playbook to verify target Linux hosts using the official Red Hat Log4j detector script RHSB-2021-009 for Log4Shell (CVE-2021-44228).

[Red Hat version 1.2 detector 2021-12-20](https://access.redhat.com/security/vulnerabilities/RHSB-2021-009).

Ansible Playbook
------------

Code also available as Ansible Playbook [lucab85/log4j-cve-2021-44228](https://github.com/lucab85/log4j-cve-2021-44228)

Requirements
------------

ansible 2.9+

Role Variables
--------------

default values:

```yaml
sh_detector: "cve-2021-44228--2021-12-20-1836.sh"
sh_signature: 'cve-2021-44228--2021-12-20-1836.sh.asc'
detector_baseurl: 'https://access.redhat.com/sites/default/files/'
detector_path: "/var/"
detector_dir: "/tmp/cve-2021-44228/"
detector_run_dir: 'tmp'
detector_options: '-n -d --no-progress --scan {{ detector_path }}'
gpg_keyid: '7514F77D8366B0D9'
clean_run_before: true
delete_after: true
verify_gpg: true
```

- sh_detector: the filename of the detector bash script file
- sh_signature: the filename of the detector GPG signature file
- detector_baseurl: the base URL to download the previous files
- detector_path: the path to inspect (default `/var/`)
- detector_dir: the download path of the detector (default `detector_dir`)
- detector_run_dir: the subdirectory to create before the run (default `tmp`)
- detector_options: the command lines options for detector script (default `-n -d --no-progress --scan {{ detector_path }}`)
- gpg_keyid: the GPG public key to download for the verification (default Red Hat Product Security `7514F77D8366B0D9`)
- clean_run_before: remove the run directory and recreate before the execution - detector requires empty directory (default `true`)
- delete_after: remove the _detector_dir_ the execution (default `true`)
- verify_gpg: perform the GPG signature donwload and verification (default: `true`)


Dependencies
------------

None.

Download
------------

Code also available in Ansible Galaxy role [lucab85.ansible_role_log4shell](https://galaxy.ansible.com/lucab85/ansible_role_log4shell)

```bash
ansible-galaxy install lucab85.ansible_role_log4shell

```

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lucab85.ansible_role_log4shell }

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
