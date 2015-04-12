common
======

Wrapper for common roles and settings.

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

| Name                   | Default                                                                      | Description                 |
|------------------------|------------------------------------------------------------------------------|-----------------------------|
| common_fqdn            | localhost.localdomain                                                        | Fully qualified domain name |
| common_iptables_rules  | [{protocol: tcp, source_addresses: 0.0.0.0/0, port: 22, comment: "OpenSSH"}] | Firewall rules              |
| common_dns_servers     | ['8.8.8.8']                                                                  | DNS servers                 |
| common_motd_ascii_logo | ""                                                                           | MOTD ASCII logo             |
| common_motd_message    |"Welcome to {{ fqdn }}"                                                       | MOTD welcome message        |

Dependencies
------------

kbrebanov.selinux
kbrebanov.apparmor
kbrebanov.hostname
kbrebanov.hosts_file
kbrebanov.resolv_conf
kbrebanov.iptables
kbrebanov.motd
kbrebanov.ntp
kbrebanov.rsyslog
kbrebanov.sudo
kbrebanov.openssh
kbrebanov.man
kbrebanov.unzip
kbrebanov.zip

Example Playbook
----------------

Install common roles with default settings
```
- hosts: all
  roles:
    - { role: kbrebanov.common }
```

Install common roles specyfing a FQDN
```
- hosts: all
  roles:
    - { role: kbrebanov.common, common_fqdn: host1.example.com }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
