ansible-role-log4shell
=========

Ansible playbook to verify target Linux hosts using the official Red Hat Log4j detector script RHSB-2021-009 for Log4Shell (CVE-2021-44228).

[Red Hat version 1.2 detector 2021-12-20](https://access.redhat.com/security/vulnerabilities/RHSB-2021-009).

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
gpg_public_key: 'gpg --keyserver pgp.mit.edu --recv {{ gpg_keyid }}'
clean_run_before: true
delete_after: false
verify_gpg: true
```

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: lucab85.ansible-role-log4shell }

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
