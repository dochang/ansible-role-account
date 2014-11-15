Account
=======

An ansible role to manage users & groups.

Requirements
------------

None

Role Variables
--------------

  - `account_groups` -- A list of groups where each group support all
    parameters from `group` module.
  - `account_users` -- A list of users where each user support all parameters
    from `user` module, plus a special parameter `authorized_keys`.
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

License
-------

MIT

Author Information
------------------

Desmond O. Chang <dochang@gmail.com>
