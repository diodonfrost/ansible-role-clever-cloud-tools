# ansible-role-clever-cloud-tools

[![molecule](https://github.com/diodonfrost/ansible-role-clever-cloud-tools/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-clever-cloud-tools/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.clever_cloud_tools-660198.svg)](https://galaxy.ansible.com/diodonfrost/clever_cloud_tools)

This role installs [Clever Cloud CLI tools](https://www.clever-cloud.com/developers/doc/cli/) on your target host.

## Requirements

This role was developed using Ansible 2.10. Backwards compatibility is not guaranteed.
Use `ansible-galaxy install ansible-role-clever-cloud-tools` to install the role on your system.

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# Define clever-tools version to install
# Possible values: latest, or a specific version number (e.g. 3.9.0)
# Default: latest
clever_tools_version: latest

# Define where to install clever binary
# Default: use local system path defined in Ansible vars/*.yml
clever_tools_path: "{{ _clever_tools_default_path }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy clever-cloud-tools role in a localhost and installing the latest version.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.clever_cloud_tools
```

This role can also install a specific version of clever-tools.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.clever_cloud_tools
      vars:
        clever_tools_version: "3.9.0"
```

## Supported Platforms

- Linux (x86_64, aarch64)
- macOS (x86_64, arm64)
- Windows (x86_64)

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://libvirt.org/) (Windows tests only)
* [Vagrant](https://www.vagrantup.com/downloads.html) (Windows tests only)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 26.04
molecule test

# Test ansible role with ubuntu 24.04
image=ansible-ubuntu:24.04 molecule test

# Create instance
molecule create

# Apply role on instance
molecule converge

# Launch tests on instance
molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role on Linux
molecule test -s linux

# Test ansible role on Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2026 by diodonfrost.
