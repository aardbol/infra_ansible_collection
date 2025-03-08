# Packages Role

## Overview

The `packages` role is designed to manage system and pip packages.

Features:
- install, remove or purge system packages
- install or remove pip packages
- perform upgrades of all packages
- add custom APT repos securely, compared to builtin `apt_repository` module

See `defaults/main.yml` for more documentation on usage.

## Requirements

- Supported platforms: Debian, Ubuntu

## Role Variables

See `defaults/main.yml`

## Dependencies

None

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: packages
  vars:
    packages_remove:
      - ufw
    packages_purge:
      - snapd
    packages_new_repositories:
      - repo: https://download.docker.com/linux/ubuntu {{ ansible_distribution_release }} stable
        key_file: https://download.docker.com/linux/ubuntu/gpg
```