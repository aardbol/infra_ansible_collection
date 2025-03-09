## Overview

This collection is a set of roles that are used to setup a server. The roles are designed to be used together, but can be used individually as well.

Roles:
- [users](roles/users/README.md) - manage users and groups and authorized keys
- [packages](roles/packages/README.md) - manage system/pip packages and updates
- [restart](roles/restart/README.md) - restart a server (after updates)

## Requirements

- Supported platforms: Debian, Ubuntu

## Roadmap

- A role that will perform a default setup based on the roles available in this collection.
  - add `ssh` group
- (packages) add dangling kernel package removal in ubuntu