## Overview

The `users` role is designed to manage users and groups on a system. This role allows you to create, modify, and delete user accounts and groups, ensuring that the system's user management is consistent and secure.

Features:
- manage the authorized keys for the main admin user (default root)
- pass a (system) user list via a variable or git repo containing a `users.yml` file
- manage (system) groups
- manage authorized keys for users
- set nopasswd sudo for sudo group
- enable linger for a user, so they can run systemd services without being logged in

See `defaults/main.yml` for more documentation on usage.

## Dependencies

- ansible.posix
- community.general

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: users
  vars:
    users_groups:
      - name: ssh
    users_users:
      - name: user1
        groups: ["sudo"]
        authorized_keys: |
          ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDQ...
      - name: user2
        groups: ["sudo", "ssh"]
        authorized_keys: |
          ssh-ed25519 AAAAB3NzaC1yc2EAAAADAQABAAABAQDQ...
      - name: user3
        state: absent
```