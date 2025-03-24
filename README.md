# infra_ansible_collection

This repository contains collections for DevOps and infrastructure professionals to configure and manage servers consistently and securely.

## Collections and Roles

### [node_base](node_base/README.md)
A set of roles used to set up a server. The roles are designed to be used together but can also be utilized individually.

#### Roles within node_base:

- **[users](node_base/roles/users/README.md)**: 
  - Manage users, groups, and authorized keys.
  
- **[packages](node_base/roles/packages/README.md)**: 
  - Manage system and pip packages, as well as updates.
  
- **[restart](node_base/roles/restart/README.md)**: 
  - Restart a server after updates.
  
- **[config](node_base/roles/config/README.md)**: 
  - Configure systemd and mount points.
  
- **[network](node_base/roles/network/README.md)**: 
  - Manage the firewall and SSH configuration.
