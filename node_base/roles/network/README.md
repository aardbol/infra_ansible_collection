## Overview

The `network` role is designed to manage firewall with nftables and SSH configuration.

Note: as a security measure, you must explicitly define `network_allow_ssh_ipv4` to whitelist IPs for SSH connections and
`network_allow_ssh_ipv6` in case you also enable IPv6 support. 

Features:
- manage firewall rules with nftables: default policies, icmp(v6), ssh via ipv4 and ipv6
- disable firewalling completely (e.g. when using AWS Security Groups instead)
- manage SSH configuration: ipv4/ipv6, allowed groups, set port number, dis/enable password authentication

See `defaults/main.yml` for more documentation on usage.

## Dependencies

- community.general

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: network
  vars:
    network_ipv6_support: true
    network_allow_ssh_ipv4: [0.0.0.0/0]
    network_allow_ssh_ipv6: [::/0]
    network_ssh_allow_groups: [ssh]
```