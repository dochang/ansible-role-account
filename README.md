Account
=======

[![Ansible Galaxy](https://img.shields.io/badge/galaxy-dochang.account-blue.svg)](https://galaxy.ansible.com/list#/roles/2104)

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

**NOTE**: You must set `authorized_keys` for every user in `account_users` even
if it's empty.  In that case, set `authorized_keys` to `[]`.  This is a
technical limitation from Ansible.

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
