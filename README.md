Vector role
=========

Install and configure Vector on Ubuntu 24.04 and Oracle Linux 8 (x86_64).

Requirements
------------

- Ansible Core 2.16 or higher
- `become: true` required

Role Variables
--------------

| Variable | Default | Purpose |
|---|---|---|
| vector_version | 0.60.0 | Version of package to be installed |
| vector_config | internal_logs -> console | Vector configuration |

Example Playbook
----------------

```yaml
---
- name: Install Vector
  hosts: vector
  become: true
  roles:
    - role: vector
```

License
-------

MIT

Author Information
------------------

Eugenie Kotukov

Testing
-------

The default Molecule scenario tests the role on Ubuntu 24.04 and Oracle Linux 8
using Docker containers with systemd.

The scenario checks idempotence, configuration file presence,
configuration validity, service startup, and service enablement.

Tested with Ansible Core 2.16.3, Molecule 4.0.4, and molecule-docker 2.1.0.

Run from the role root:

```bash
molecule test -s default
```
