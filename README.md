Role Name
=========

operators: Operators

[![Build Status](https://travis-ci.org/cmihai-ansible/operators.svg?branch=master)](https://travis-ci.org/cmihai-ansible/operators)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.operators](https://galaxy.ansible.com/devops-toolbox.operators)

```bash
ansible-galaxy install devops-toolbox.operators
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
operators_packages_state: present
operators_remove_packages: true
operators_enable_service: true
operators_enable_selinux: true
operators_copy_templates: true
operators_firewall_configure: true
operators_firewall_rules:
  - service: ssh
  - port: 3389
operators_users:
  - user: devops
    group: docker
operators_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install operators on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: operators is configured
      import_role:
        name: devops-toolbox.operators
      vars:
        operators_packages_state: present
        operators_remove_packages: true
        operators_enable_service: true
        operators_enable_selinux: true
        operators_copy_templates: true
        operators_firewall_configure: true
        operators_firewall_rules:
          - service: ssh
          - port: 3389
        operators_users:
          - user: devops
            group: docker
        operators_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: operators
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
