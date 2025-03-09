## Overview

The `restart` role checks whether a system restart is required after packages where updated and performs it after 
confirmation.

Features:
- check if a system restart is required
- perform a system restart after confirmation
- switch to force a restart or only do it when updates require one
- non-interactive mode, e.g. for in pipelines

See `defaults/main.yml` for more documentation on usage.

## Dependencies

None

## Example command

```bash
ansible-playbook playbook.yml -t check-restart
ansible-playbook playbook.yml -t restart
```