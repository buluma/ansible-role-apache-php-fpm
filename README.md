# [apache-php-fpm](#apache-php-fpm)

Apache 2.4+ PHP-FPM support for Linux

|GitHub|GitLab|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-apache-php-fpm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/actions)|[![gitlab](https://gitlab.com/buluma/ansible-role-apache-php-fpm/badges/main/pipeline.svg)](https://gitlab.com/buluma/ansible-role-apache-php-fpm)|[![quality](https://img.shields.io/ansible/quality/)](https://galaxy.ansible.com/buluma/apache-php-fpm)|[![downloads](https://img.shields.io/ansible/role/d/)](https://galaxy.ansible.com/buluma/apache-php-fpm)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-apache-php-fpm.svg)](https://github.com/buluma/ansible-role-apache-php-fpm/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: true

  vars:
    apache_listen_port_ssl: 443
    apache_create_vhosts: true
    apache_vhosts_filename: "vhosts.conf"
    apache_vhosts:
      - servername: "example.com"
        documentroot: "/var/www/vhosts/example_com"

  roles:
    - role: geerlingguy.repo-remi
      when: ansible_os_family == 'RedHat'
    - role: geerlingguy.apache
    - role: geerlingguy.php-versions
    - role: geerlingguy.php
    - role: geerlingguy.apache-php-fpm
```

The machine needs to be prepared. In CI this is done using `molecule/default/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: buluma.bootstrap
    - role: geerlingguy.repo-remi
    - role: geerlingguy.apache
    - role: geerlingguy.php-versions
    - role: geerlingguy.php
    - role: geerlingguy.apache-php-fpm
```


## [Role Variables](#role-variables)

The default values for the variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for ansible-role-apache-php-fpm
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-apache-php-fpm/blob/main/requirements.txt).

## [Status of used roles](#status-of-requirements)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/ansible-role-bootstrap/badges/main/pipeline.svg)](https://gitlab.com/buluma/ansible-role-bootstrap)|
|[geerlingguy.apache](https://galaxy.ansible.com/buluma/geerlingguy.apache)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.apache/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.apache/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/geerlingguy.apache/badges/main/pipeline.svg)](https://gitlab.com/buluma/geerlingguy.apache)|
|[geerlingguy.repo-remi](https://galaxy.ansible.com/buluma/geerlingguy.repo-remi)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.repo-remi/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.repo-remi/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/geerlingguy.repo-remi/badges/main/pipeline.svg)](https://gitlab.com/buluma/geerlingguy.repo-remi)|
|[geerlingguy.php-versions](https://galaxy.ansible.com/buluma/geerlingguy.php-versions)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.php-versions/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.php-versions/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/geerlingguy.php-versions/badges/main/pipeline.svg)](https://gitlab.com/buluma/geerlingguy.php-versions)|
|[geerlingguy.php](https://galaxy.ansible.com/buluma/geerlingguy.php)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.php/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.php/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/geerlingguy.php/badges/main/pipeline.svg)](https://gitlab.com/buluma/geerlingguy.php)|
|[geerlingguy.apache-php-fpm](https://galaxy.ansible.com/buluma/geerlingguy.apache-php-fpm)|[![Build Status GitHub](https://github.com/buluma/geerlingguy.apache-php-fpm/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/geerlingguy.apache-php-fpm/actions)|[![Build Status GitLab ](https://gitlab.com/buluma/geerlingguy.apache-php-fpm/badges/main/pipeline.svg)](https://gitlab.com/buluma/geerlingguy.apache-php-fpm)|

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- geerlingguy.apache
## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.co.ke/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-apache-php-fpm/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|el|6, 7|
|debian|wheezy, jessie, stretch|
|ubuntu|precise, trusty, xenial|

The minimum version of Ansible required is 2.1, tests have been done to:

- The previous version.
- The current version.
- The development version.



If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-apache-php-fpm/issues)

## [License](#license)

license (BSD, MIT)

## [Author Information](#author-information)

[Michael Buluma](https://buluma.github.io/)
