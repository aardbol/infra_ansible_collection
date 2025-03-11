## Overview

The `config` role is used to configure the system. It can make changes to systemd and apply mountpoints.

Features:
- set the hostname based on `inventory_hostname`
- configure systemd services
- configure mountpoints: resize, permissions, mount them and add to fstab

## Dependencies

- ansible.posix
- community.general

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: config
  vars:
    node_base_update_hostname: true
    config_systemd_configurations_blocks:
      journald.conf: |
        SystemMaxUse=250M
        Storage=persistent
        ForwardToSyslog=no
        ForwardToKMsg=no
        Audit=yes
      sleep.conf: |
        AllowSuspend=no
        AllowHybridSleep=no
        AllowHibernation=no
      resolved.conf: |
        DNS=1.1.1.1 2606:4700:4700::1111
        FallbackDNS=1.0.0.1 2606:4700:4700::1001
        DNSOverTLS=yes
        DNSSEC=no
    config_mount_points:
      - dev: /dev/nvme0n1
        type: ext4
        mount: /var/lib/docker
      - dev: /dev/nvme0n2
        type: btrfs
        mount: /mnt/thinly_provisioned_drive
        resize: false
```