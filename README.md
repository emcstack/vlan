VLAN
=========

Creates the VLAN configuration files

Requirements
------------


Role Variables
--------------

parent: name of the parent iface of the VLAN
vlans: list of VLAN IDs to create on the parent

Dependencies
------------


Example Playbook
----------------

- hosts:
  - nc-9
  roles:
  - vlan
  vars:
  - parent: bond0
  - vlans:
    - 110
    - 120
    - 130

License
-------

BSD

Author Information
------------------

John Preston [John Mille]

