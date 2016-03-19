Account
=======

[![Build Status](https://travis-ci.org/dochang/ansible-role-account.svg?branch=master)](https://travis-ci.org/dochang/ansible-role-account)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-dochang.account-blue.svg)](https://galaxy.ansible.com/dochang/account/)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/dochang/ansible-role-account.svg)](http://isitmaintained.com/project/dochang/ansible-role-account "Average time to resolve an issue")
[![Percentage of issues still open](http://isitmaintained.com/badge/open/dochang/ansible-role-account.svg)](http://isitmaintained.com/project/dochang/ansible-role-account "Percentage of issues still open")

An ansible role to manage users & groups.

Requirements
------------

None

Role Variables
--------------

  - `account_groups` (default: `[]`) -- A list of groups where each group
    support all parameters from `group` module.
  - `account_users` (default: `[]`) -- A list of users where each user support
    all parameters from `user` module, plus a special parameter
    `authorized_keys`.
  - `account_users.authorized_keys` -- A list of ssh public keys where each key
    support all parameters from `authorized_key` module.

See `tasks/main.yml` for details.

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: dochang.account
          account_groups:
            - name: sudo
              system: yes
              state: present
          account_users:
            - name: foo
              createhome: yes
              groups: sudo
              authorized_keys:
                - key: 'xxxxxxxx'
                  state: present
                - key: 'yyyyyyyy'
                  state: absent
            - name: bar
              uid: 9999
              authorized_keys: []

License
-------

MIT

Author Information
------------------

Desmond O. Chang <dochang@gmail.com>
