VLAN
=========

Creates the VLAN configuration files

Requirements
------------


Role Variables
--------------

| Name | Type | Required | Default | Description
|--- |--- |--- |--- |---
| parent | string |yes | None | Name of the parent interface of the VLAN
| vlans | list | yes | None | List of VLAN IDs to create on the parent
| apply | boolean | no | true | Determines if configuration files will go to the sysconfig directory or temporary one
| config_from_hostvars | boolean | no | true | Will use the host_vars properties to generate the IPv4 configuration
| el_network_sysconfig | boolean | no | /etc/sysconfig/network-scripts | Default directory for RH/CentOS
| tmp_dir | string | no | /tmp | Default temporary directory
| mtu | int | no | 1500 | MTU value for the interface
| enable_ipv4 | boolean | no | false | Determines if IPv4 settings should be in the configuration file
| manage_dns | boolean |no | true | Set the DNS servers in the configuration files
| dns_servers | list | no | ['8.8.8.8', '8.8.6.6'] | List to specify the DNS servers
| enable_ipv6| boolean | no | true | Determines if you init IPv6 for the interface
| ipv6_autoconf | boolean | no | false | Determines if you autoconfigure IPv6 for the interface

Dependencies
------------

The host_vars must be set properly to have IPv4 settings in place.
host_vars should follow the pattern:

```
v<VLAN ID>_ipaddr: IPv4 to use
v<VLAN_ID>_netmask: netmask to use
v<VLAN_ID>_gateway: (optional) gateway IPv4 to use

```

example:
```

v120_ipaddr: 192.168.0.2
v120_netmask: 255.255.255.0
v120_gateway: 192.168.0.1

v130_ipaddr: 192.168.1.2
v130_netmask: 255.255.255.0

```

Example Playbook
----------------

```

- hosts:
  - nc-9
  roles:
  - vlan
  vars:
  - parent: "bond0"
  - vlans:
    - 120
    - 130

```

License
-------

GPLv3

Author Information
------------------

John Preston [John Mille]
