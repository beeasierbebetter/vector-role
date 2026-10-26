Vector role
=========

Role install and configure Vector on Ubuntu 24.04

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
