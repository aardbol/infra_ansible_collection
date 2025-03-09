# infra_ansible_collection

This repository contains collections for devops/infra people to configure and manage servers consistently and securely.

## Collections and roles

- [node_base](node_base/README.md) - a set of roles that are used to setup a server. The roles are designed to be used together, but can be used individually as well.
  - [users](node_base/roles/users/README.md) - manage users and groups and authorized keys
  - [packages](node_base/roles/packages/README.md) - manage system/pip packages and updates
  - [restart](node_base/roles/restart/README.md) - restart a server (after updates)
  - [config](node_base/roles/config/README.md) - configure systemd and mountpoints
