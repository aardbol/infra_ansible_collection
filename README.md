# infra_ansible_collection

This repository contains collections for devops/infra people to configure servers consistently and securely.

## Collections and roles

- [node_base](collections/node_base/README.md) - a set of roles that are used to setup a server. The roles are designed to be used together, but can be used individually as well.
  - [users](collections/node_base/roles/users/README.md) - manage users and groups and authorized keys
  - [packages](collections/node_base/roles/packages/README.md) - manage system/pip packages and updates