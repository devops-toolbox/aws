Role Name
=========

aws: Aws

[![Build Status](https://travis-ci.org/cmihai-ansible/aws.svg?branch=master)](https://travis-ci.org/cmihai-ansible/aws)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.aws](https://galaxy.ansible.com/devops-toolbox.aws)

```bash
ansible-galaxy install devops-toolbox.aws
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
aws_packages_state: present
aws_remove_packages: true
aws_enable_service: true
aws_enable_selinux: true
aws_copy_templates: true
aws_firewall_configure: true
aws_firewall_rules:
  - service: ssh
  - port: 3389
aws_users:
  - user: devops
    group: docker
aws_selinux_booleans:
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
- name: Install aws on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: aws is configured
      import_role:
        name: devops-toolbox.aws
      vars:
        aws_packages_state: present
        aws_remove_packages: true
        aws_enable_service: true
        aws_enable_selinux: true
        aws_copy_templates: true
        aws_firewall_configure: true
        aws_firewall_rules:
          - service: ssh
          - port: 3389
        aws_users:
          - user: devops
            group: docker
        aws_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: aws
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
