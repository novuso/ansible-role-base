# Ansible Role: Base

[![MIT License](http://img.shields.io/badge/license-MIT-003399.svg)](http://opensource.org/licenses/MIT)

An Ansible role that manages general packages on Ubuntu 14.04

## Requirements

None

## Role Variables

Ansible variables are listed here along with their default values:

`base_repositories` is a list of Ubuntu PPA repositories that are managed for
this role. Each entry in the list may designate:

* **repo** *required* (ppa: is prepended)
* **state** (default is present)
* **update_cache** (default is yes)
* **validate_certs** (default is yes)

By default, no repositories are used:

    base_repositories: []

`base_packages` is a list of utilities and other common packages that are
managed for this role. Each entry in the list may designate:

* **name** *required*
* **state** (default is present)
* **update_cache** (default is yes)
* **cache_valid_time** (default is 3600 seconds)
* **force** if `yes`, force installs/removes (default is omitted)
* **install_recommends** (default is yes)
* **purge** if `yes`, forces purging of config files when state is `absent` (default is omitted)

By default, the following packages are used:

    base_packages:
    - name: "curl"
    - name: "git"
    - name: "wget"
    - name: "unzip"
    - name: "ack-grep"
    - name: "build-essential"
    - name: "software-properties-common"
    - name: "debconf-utils"
    - name: "keychain"

## Dependencies

None

## Example Playbook

    ---
    - hosts: all
      vars:
      base_repositories:
      - repo: "ansible/ansible"
      base_packages:
      - name: "curl"
      - name: "git"
      - name: "wget"
      - name: "unzip"
      - name: "ack-grep"
      - name: "build-essential"
      - name: "software-properties-common"
      - name: "ansible"

## License

This is released under the [MIT license](http://opensource.org/licenses/MIT).
