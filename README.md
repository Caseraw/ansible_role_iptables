# Ansible role iptables

Manage the installation and configuration of the host based firewall with **iptables**.

[![Build Status](https://travis-ci.org/Caseraw/ansible_role_iptables.svg?branch=master)](https://travis-ci.org/Caseraw/ansible_role_iptables) [<img src="https://img.shields.io/ansible/role/46812">](https://galaxy.ansible.com/caseraw/ansible_role_iptables) [<img src="https://img.shields.io/ansible/role/d/46812">](https://galaxy.ansible.com/caseraw/ansible_role_iptables) [<img src="https://img.shields.io/ansible/quality/46812">](https://galaxy.ansible.com/caseraw/ansible_role_iptables)

- [Ansible role iptables](#ansible-role-iptables)
  - [License](#license)
  - [Author Information](#author-information)
  - [Requirements](#requirements)
  - [Dependencies](#dependencies)
  - [Compatibility](#compatibility)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Useful shell commands](#useful-shell-commands)
  - [Additional documentation resources](#additional-documentation-resources)
  - [Testing with Molecule](#testing-with-molecule)
  - [CI/CD with Travis CI](#cicd-with-travis-ci)
  - [Useful links](#useful-links)

## License

MIT / BSD

## Author Information

- Made and maintained by: [Kasra Amirsarvari](https://www.linkedin.com/in/caseraw)
- Ansible Galaxy community author: <https://galaxy.ansible.com/caseraw>
- Dockerhub community user: <https://hub.docker.com/u/caseraw>

## Requirements

- Ensure a package manager is available and configured with the correct package sources and repositories.
- Ensure privileged permissions are set for the user executing this role to:
  - Install and uninstall.
  - Edit files provided by the package itself.
  - Manage `systemd` services for `iptables` and `firewalld`.

## Dependencies

N/A

## Compatibility

Compatible with the following list of operating systems:

- CentOS 7
- CentOS 8
- RHEL 7.x
- RHEL 8.x

## Role Variables

| Variable name | Description |
|---------------|-------------|
| role_iptables_required_packages | List of required packages. |
| role_iptables_remote_path_iptables | Path to the remote iptables rules configuration file. |
| role_iptables_remote_path_ip6tables | Path to the remote ip6tables rules configuration file. |
| role_iptables_rule_list | Combined list of other lists that start with the name `role_iptables_rule_list_`. Examples at: [molecule/default/vars/vars_firewalld_rules.yml](molecule/default/vars/vars_iptables_rules.yml) |

## Example Playbook

```yaml
---
- name: Manage the installation and configuration of the host based firewall with iptables
  become: True
  gather_facts: False
  roles:
   - role: ansible_role_iptables

...
```

## Useful shell commands

```shell
iptables -xnL
lsof -RPni
```

## Additional documentation resources

N/A

## Testing with Molecule

This role is locally tested with the use of [Molecule](https://molecule.readthedocs.io/en/stable/), the configuration is located at: [molecule/default](molecule/default).  
The Molecule tests are run (using the [docker driver](https://molecule.readthedocs.io/en/stable/configuration.html#docker)) on [Dockerhub images](https://hub.docker.com/u/caseraw) built for this purpose:

- [CentOS](https://hub.docker.com/r/caseraw/ansible-molecule-centos)
- [Fedora](https://hub.docker.com/r/caseraw/ansible-molecule-fedora)

Some specific configurations might require a full OS instead of a minimal container image. In these use-cases make use of [molecule driver for vagrant](https://molecule.readthedocs.io/en/stable/configuration.html#vagrant) with the [libvirt provider](https://molecule.readthedocs.io/en/stable/configuration.html#molecule-vagrant-module). The Molecule driver and platform configuration part could look something like this:

```yaml
driver:
  name: vagrant
  provider:
    name: libvirt
platforms:
  - name: ansible_role_chrony-ansible-molecule-centos-7
    box: centos/7
    imemory: 1024
    cpus: 1
```

## CI/CD with Travis CI

This role uses [Travis CI](https://travis-ci.org/) to run online tests with the use of [Molecule](https://molecule.readthedocs.io/en/stable/) and pushes notifications to import the role into [Ansible Galaxy](https://galaxy.ansible.com/) once the tests are successful. The Travis CI configuration is located at the root of the Ansible role [.travis.yml](.travis.yml)

## Useful links

- GitHub repository: <https://github.com/Caseraw/ansible_role_iptables>
- Travis CI build status: <https://travis-ci.org/Caseraw/ansible_role_iptables>
- Ansible Galaxy role: <https://galaxy.ansible.com/caseraw/ansible_role_iptables>
