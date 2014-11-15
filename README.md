Account
=======

An ansible role to manage users & groups.

Requirements
------------

None

Role Variables
--------------

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
