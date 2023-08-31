# root_colored_prompt

  * ![Last test](https://github.com/andrelohmann/ansible-role-root_colored_prompt/actions/workflows/molecule.yml/badge.svg)
  * ![Last master test](https://github.com/andrelohmann/ansible-role-root_colored_prompt/actions/workflows/molecule.yml/badge.svg?branch=master)

## Content

Simple ansible role to switch on the colored prompt for the root user

### Special purpose

This role will exemplarily showcase the perfect development environment for ansible role.

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

  * Virtualbox + Vagrant installed (only necessary, if the role should be tested with vargant as well)
  * Docker Desktop
  * VisualStudioCode + remote extensionpack (dependencies are defined within .vscode/extensions.json)

### Development-Setup

This ansible role is developed using molecule for testing. It's development is based on visual studio code and a regarding development container, solving all dependencies in terms of necessary tools (ansible, linter, molecule).

The role will be tested on three ubuntu containers (bionic, focal, jammy).

To startup the molecule test containers from within the development container, the docker socket needs to be bind mounted into the development container.

#### Important folders and files

##### .devcontainer

  * Defines the Dockerfile for the development container
  * Configures the development container startup (e.g. bind mount docker socket)

##### molecule/default/Dockerfile.js

  * used as a template for all platforms defined in molecule/default/molecule.yml
  * prepares the environments to support systemd services (necessary for some ansible roles acting on systemd)
  * installs all requirements to run ansible against the derived container
  * the file is aligned with the attributes of the platforms in molecule/default/molecule.yml
  * for more information - study the molecule documentation

### Usage

  * change to the root directory of your role and start vscode
```
code .
```
  * from within the development container you can use the following run commands
```
yamllint .
ansible-lint .
molecule create
molecule test
```

### Build and Release process

The ansible role defines a bunch of github workflows to run molecule test and release management.

The release management requires a handful of settings.

#### Protecting the master/main branch

  * Settings -> Branches -> Add branch protection rule
  * Branch pattern name -> main or mster (depending on your default branch)
  * Protect matching branches -> chek "Require a pull request before merging"
  * "Require approvals" can be individually handled as required

#### Give read and write permissions to GITHUB_TOKEN

  * Settings -> Actions -> General -> Workflow permissions -> read and write permissions

#### Commit messages

Commit messages should follow a special format to achieve a patch, minor or major semantic versioning update.

##### patch

0.0.x

```
fix(single_word): description
```

##### minor

0.x.0

```
feat(single_word): description
```

##### major

x.0.0

```
perf(single_word): description
BREAKING CHANGE: describing the breaking change
```

It's absolutely important, that "BREAKING CHANGE: " is mentioned in the second+ line. On single line commit messages, the major version update will be ignored.

## Reusing the template

Reusing the template for new roles:

  * Align the workflows (branches)
  * Align meta/main.yml
  * Align molecule/default/converge.yml
  * Align molecule/default/requirements.yml
  * Align molecule/default/verify.yml (write ansible verification code to test the results of the role)
  * Align vagrant/config.yaml (rolename)
  * Align vagrant/playbook.yml
  * Align vagrant/README.md
  * Align vagrant/requirements.yml
  * Align LICENSE
  * Align README.md
  * requirements.yml

## Example Playbook

    - hosts: accounts
      roles:
         - { role: andrelohmann.root_colored_prompt }

## License

MIT

## Author Information

&copy; Andre Lohmann (and others) 2022

https://github.com/andrelohmann

### Maintainer Contact

  * Andre Lohmann
    <lohmann.andre (at) gmail (dot) com>
