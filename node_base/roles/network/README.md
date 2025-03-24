## Overview

The `network` role is designed to manage firewall with nftables and SSH configuration. Iptables is not supported
because it is old and slower tech, despite unfortunately still being widely used. Nftables is the modern replacement for iptables.
As UFW can only with with iptables (or iptables-nft if available), it is also not supported.

FirewallD is also supported as an alternative for a module approach to managing firewall rules, since there's the 
ansible.posix.firewalld module. But functionality compared to nftables differs due to the flexibility limitations of firewalld's approach with zones.
This role allows you to set the default zone, which is `public` by default, which allows ssh, ipv6 and icmp(v6) by default.
For more flexibility, use nftables.

Note: as a security measure, you must explicitly define `network_allow_ssh_ipv4` to whitelist IPs/subnets for SSH connections and
`network_allow_ssh_ipv6` in case you also enable IPv6 support. 

Note 2: when using nftables, since this role flushes (resets) the firewall rules before applying the changes, which can cause issues
with the dynamic approach of docker and other services that manage their own firewall rules, it's recommended to manage those rules
manually too to avoid any issues.

You can define custom nftables rules by creating *.nft files in the /etc/nftables.d/ directory and running 
`sudo nft -f /etc/nftables.conf` (or ansible equivalent) to apply them or restarting the systemd unit.

Features:
- manage firewall rules with nftables: default policies, ICMP(v6), ssh via IPv4 and IPv6
- manage firewall rules with firewalld: default zone, ssh via IPv4 and IPv6. ICMP(v6) always enabled
- disable firewalling completely (e.g. when using AWS Security Groups instead)
- manage SSH configuration: IPv4/IPv6, allowed groups, set port number, dis/enable password authentication

See `defaults/main.yml` for more documentation on usage.

## Dependencies

- community.general
- ansible.posix

## Example Playbook

```yaml
---
- hosts: all
  roles:
    - role: network
  vars:
    network_ipv6_support: true
    network_allow_ssh_ipv4: ["0.0.0.0/0"]
    network_allow_ssh_ipv6: ["::/0"]
    network_ssh_allow_groups: ["ssh"] # Don't forget to create this group first
```