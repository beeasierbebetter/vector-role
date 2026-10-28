Vector role
=========

Install and configure Vector on Ubuntu 24.04 and Oracle Linux 8 (x86_64).

Requirements
------------

- Ansible Core 2.16 or higher for Ubuntu 24.04
- Ansible 2.10 or higher for Oracle Linux 8
- Root privileges (use `become: true` when connecting as a regular user)

Role Variables
--------------

| Variable | Default | Purpose |
|---|---|---|
| vector_version | 0.60.0 | Version of package to be installed |
| vector_config | internal_logs -> console | Vector configuration |
| vector_manage_service | true | Manage service startup, enablement, and restarts |

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

Tox
---

The compatibility Molecule scenario uses Podman and a single Oracle Linux 8
container. It checks installation, configuration validity, and idempotence

The scenario sets `vector_manage_service: false`, service startup and enablement are checked by the default Docker scenario

The Tox matrix covers all combinations of Python 3.7 and 3.9 with Ansible 2.10 and 3.0

Python dependencies are pinned in `tox-requirements.txt`, \
Ansible collection dependencies are pinned in `requirements.yml`

Start the test container from the root:

```bash
docker run --privileged=True \
  -v "$PWD:/opt/vector-role" \
  -w /opt/vector-role \
  -it aragast/netology:latest /bin/bash
```

Inside the container, run:

```bash
tox
```
