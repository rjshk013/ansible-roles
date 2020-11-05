Ansible Role: Cassandra_cluster
=========

[![Opstree Solutions][opstree_avatar]][opstree_homepage]<br/>[Opstree Solutions][opstree_homepage] 

  [opstree_homepage]: https://opstree.github.io/
  [opstree_avatar]: https://img.cloudposse.com/150x150/https://github.com/opstree.png
An ansible role to install cassandra cluster & standalone cassandra.

Version History
------------------
|**Date**| **Version**| **Description**| **Changed By** |
|----------|---------|---------------|-----------------|
|**27 June 2020** | v0.0.1 | Initial draft | Shweta Tyagi |

Supported OS
------------
  * Ubuntu:bionic
  * Ubuntu:xenial

Requirements
------------
  * Java 1.8

Role Variables
--------------
|**Variables**| **Default Values**| **Possible Values** | **Description** |
|----------|---------|---------------|-----------|
| cassandra_version | 3.11.6 | Any cassandra version as required | Exact cassandra version which we need to install |
| cluster_name | MyCluster | Cluster name | Cluster name |
| user_name | cassandra | Any user name | Cassandra user name from which we want to run role |
| group_name | cassandra | Any group name | Cassandra group name from which we want to run role |
| cassandra_home | /opt/cassandra | Any home path | Cassandra home path |
| cassandra_path | /opt/cassandra/bin | Any path | Cassandra path |
| cassandra_data_directory | /var/lib/cassandra/data | data dir path | Cassandra data directory path |
| cassandra_hints_directory | /var/lib/cassandra/data/hints | hints dir path | Cassandra hints directory path |
| cassandra_commitlog_directory | /var/lib/cassandra/data/commitlogs | commit log directory path | Cassandra commit log directory path |
| cassandra_saved_caches_directory | /var/lib/cassandra/data/saved_caches | Caches directory path | Cassandra saved caches directory path |
| broadcast_address | node ipv4 ip | node ipv4 ip | Address to broadcast to other Cassandra nodes |
| listen_address | node ipv4 ip | node ipv4/ipv6 ip | If you choose to specify the interface by name and the interface has an ipv4 and an ipv6 address you can specify which should be chosen using listen_interface_prefer_ipv6. If false the first ipv4 address will be used. If true the first ipv6 address will be used. Defaults to false preferring ipv4. If there is only one address it will be selected regardless of ipv4/ipv6 |
| broadcast_rpc_address | node ipv4 ip | node ipv4 ip | RPC address to broadcast to drivers and other Cassandra nodes. This cannot be set to 0.0.0.0. If left blank, this will be set to the value of rpc_address. If rpc_address is set to 0.0.0.0, broadcast_rpc_address must be set. |
| rpc_address | node ipv4 ip | node ipv4/ipv6 ip | If you choose to specify the interface by name and the interface has an ipv4 and an ipv6 address you can specify which should be chosen using rpc_interface_prefer_ipv6. If false the first ipv4 address will be used. If true the first ipv6 address will be used. Defaults to false preferring ipv4. If there is only one address it will be selected regardless of ipv4/ipv6. |
| cassandra_local_hostname | node ipv4 ip | node ipv4 ip | Node ipv4 address from which we connect db using shell  |
| cassandra_admin_user | admin | Any admin user | New cassandra admin user |
| cassandra_admin_password | admin | Any admin password |New cassandra admin password |
| cassandra_old_admin_password | cassandra | cassandra | Default cassandra password |
| cassandra_old_admin_user | cassandra | cassandra | Default Cassandra user |
| authorization_enable | yes | yes or no | Enabled, when we want to change default username or password |
| cassandra_port | 9042 | Any Linux port | Assign a port to connect with cassandra |
| rpc_port | 9160 | Any Linux port | Port for Thrift to listen for clients on |
| storage_port | 7000 | Any Linux port | TCP port, for commands and data |
| ssl_storage_port | 7001 | Any Linux port | SSL port, for encrypted communication |

Directory Layout
----------------
```
osm_cassandra
.
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── README.md
├── tasks
│   ├── authorization.yml
│   ├── cluster_status.yml
│   ├── main.yml
│   └── swap.yml
├── templates
│   ├── cassandra.sh
│   └── cassandra.yaml.j2
└── vars
    └── main.yml

5 directories, 10 files

```
Future changes
----------------
* support for CentOS
* create service file

Example Playbook
----------------
```
- name: It will automate Cassandra setup
  hosts: seed-nodes
  become: true
  roles:
    - role: osm_cassandra
```

Inventory
----------
For cluster: An inventory should look like this:-
```ini
[seed-nodes]                 
seed1 192.xxx.x.xxx  ansible_user=ubuntu
seed2 192.xxx.x.xxx  ansible_user=ubuntu 
seed3 192.xxx.x.xxx  ansible_user=ubuntu 
```
where, The seed-nodes group contains the details of the nodes we want to cluster.

For standalone: An inventory should look like this:-
```ini
[seed-nodes]                 
seed1 192.xxx.x.xxx  ansible_user=ubuntu
```

License
-------

BSD

Author Information
------------------

[![Shweta Tyagi][shweta_avatar]][shweta_homepage]<br/>[Shweta Tyagi][shweta_homepage] 

  [shweta_homepage]: https://github.com/shwetatyagi-ot
  [shweta_avatar]: https://img.cloudposse.com/75x75/https://github.com/shwetatyagi-ot.png


