# root_colored_prompt

  * ![Last test](https://github.com/andrelohmann/ansible-role-root_colored_prompt/actions/workflows/molecule.yml/badge.svg)
  * ![Last master test](https://github.com/andrelohmann/ansible-role-root_colored_prompt/actions/workflows/molecule.yml/badge.svg?branch=master)

## Content

Simple ansible role to switch on the colored prompt for the root user

### Special purpose

This role will exeplarily showcase the perfect development environment for ansible role.

  * yamllint
  * ansible-lint
  * ansible-playbook ---syntax-check
  * molecule test
  * gitlab action
  * update ansible-galaxy
  * show build status
  * auto version-up (?)
  * test within vagrant (for development purose)
  * test with molecule (inside or outside vagrant)
  * test against docker container

### Prerequisites

https://thedatabaseme.de/2022/01/17/automated-testing-your-ansible-role-with-molecule-and-github-actions/

  * Ubuntu Server minimized installed to the server
  * User k8s is created and has sudo permissions without password
  * Add your public key for remote access
  * Install ansible

```
apt update && apt install python3-pip git -yqq
# Ansible Version 2.11 is important for kubespray
pip install --upgrade ansible-core~=2.11.0
```

Run Commands
```
molecule lint
molecule create
molecule test
```

### Installation

  * login as k8s
  * Clone the repository

## Example Playbook

    - hosts: accounts
      roles:
         - { role: andrelohmann.root_colored_prompt }

## License

MIT

## Author Information

(&copy;) Andre Lohmann (and others) 2022

https://github.com/andrelohmann

### Maintainer Contact

  * Andre Lohmann
    <lohmann.andre (at) gmail (dot) com>
