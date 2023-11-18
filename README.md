# [Ansible role apache-php-fpm](#apache-php-fpm)

Apache 2.4+ PHP-FPM support for Linux

|GitHub|GitLab|Downloads|Version|Issues|Pull Requests|
|------|------|-------|-------|------|-------------|
|[![github](https://github.com/buluma/ansible-role-apache-php-fpm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-apache-php-fpm/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-apache-php-fpm)|[![downloads](https://img.shields.io/ansible/role/d/)](https://galaxy.ansible.com/buluma/apache-php-fpm)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-apache-php-fpm.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-apache-php-fpm.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-apache-php-fpm.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/pulls/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  vars:
    apache_listen_port_ssl: 443
    apache_create_vhosts: true
    apache_vhosts_filename: "vhosts.conf"
    apache_vhosts:
      - servername: "example.com"
        documentroot: "/var/www/vhosts/example_com"

  roles:
    - role: buluma.apache-php-fpm
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: buluma.bootstrap
    - role: geerlingguy.repo_remi
      when: ansible_os_family == 'RedHat'
    - role: geerlingguy.apache
    - role: geerlingguy.php-versions
    - role: geerlingguy.php
    - role: geerlingguy.apache-php-fpm
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/defaults/main.yml):

```yaml
---
# defaults file for ansible-role-apache-php-fpm
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[geerlingguy.repo_remi](https://galaxy.ansible.com/buluma/geerlingguy.repo_remi)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.repo_remi/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.repo_remi/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/geerlingguy.repo_remi/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/geerlingguy.repo_remi)|
|[geerlingguy.apache](https://galaxy.ansible.com/buluma/geerlingguy.apache)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.apache/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.apache/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/geerlingguy.apache/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/geerlingguy.apache)|
|[geerlingguy.php-versions](https://galaxy.ansible.com/buluma/geerlingguy.php-versions)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.php-versions/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.php-versions/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/geerlingguy.php-versions/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/geerlingguy.php-versions)|
|[geerlingguy.php](https://galaxy.ansible.com/buluma/geerlingguy.php)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.php/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.php/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/geerlingguy.php/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/geerlingguy.php)|
|[geerlingguy.apache-php-fpm](https://galaxy.ansible.com/buluma/geerlingguy.apache-php-fpm)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.apache-php-fpm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.apache-php-fpm/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/geerlingguy.apache-php-fpm/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/geerlingguy.apache-php-fpm)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-apache-php-fpm/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/repository/docker/buluma/enterpriselinux/general)|all|
|[Debian](https://hub.docker.com/repository/docker/buluma/debian/general)|all|
|[Ubuntu](https://hub.docker.com/repository/docker/buluma/ubuntu/general)|all|

The minimum version of Ansible required is 2.1, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-apache-php-fpm/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/CHANGELOG.md)

## [License](#license)

[license (Apache-2.0)](https://github.com/buluma/ansible-role-apache-php-fpm/blob/master/LICENSE).

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)

Please consider [sponsoring me](https://github.com/sponsors/buluma).

### [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
