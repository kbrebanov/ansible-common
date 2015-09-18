common
======

[![Ansible Role](https://img.shields.io/ansible/role/3927.svg)](https://galaxy.ansible.com/list#/roles/3927)

Wrapper for common roles.

Requirements
------------

This role requires Ansible 1.4 or higher.

Role Variables
--------------

None

Dependencies
------------

- kbrebanov.selinux
- kbrebanov.apparmor
- kbrebanov.hostname
- kbrebanov.hosts_file
- kbrebanov.resolv_conf
- kbrebanov.iptables
- kbrebanov.motd
- kbrebanov.timezone
- kbrebanov.ntp
- kbrebanov.rsyslog
- kbrebanov.rsync
- kbrebanov.sudo
- kbrebanov.openssh
- kbrebanov.man
- kbrebanov.unzip
- kbrebanov.zip
- kbrebanov.open_vm_tools

Example Playbook
----------------

Install common roles
```
- hosts: all
  roles:
    - { role: kbrebanov.common }
```

Install common roles specifying some variables
```
- hosts: all
  vars:
    hostname_name: test-server
    domain_name: example.com
    hosts_file_local_fqdn: "{{ hostname_name }}.{{ domain_name }}"
    hosts_file_local_hostname: "{{ hostname_name }}"
    resolv_conf_nameservers:
      - "8.8.8.8"
      - "8.8.4.4"
    resolv_conf_search_domains:
      - "{{ domain_name }}"
    motd_message: "Welcome to {{ hostname_name }}.{{ domain_name }}"
    iptables_icmp_enabled: true
    iptables_rules:
      - protocol: tcp
        source_addresses: 0.0.0.0/0
        port: 22
        comment: "OpenSSH"
    timezone_name: "America/Toronto"
  roles:
    - { role: kbrebanov.common }
```

License
-------

BSD

Author Information
------------------

Kevin Brebanov
