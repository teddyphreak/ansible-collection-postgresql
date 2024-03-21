# Ansible Collection - nephelaiio.patroni

[![Build Status](https://github.com/nephelaiio/ansible-collection-patroni/actions/workflows/molecule.yml/badge.svg)](https://github.com/nephelaiio/ansible-collection-patroni/actions/wofklows/molecule.yml)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-nephelaiio.patroni-blue.svg)](https://galaxy.ansible.com/ui/repo/published/nephelaiio/patroni/)

An [ansible collection](https://galaxy.ansible.com/ui/repo/published/nephelaiio/patroni/) to install and manage [Patroni](https://patroni.readthedocs.io/en/latest/README.html) clusters

## ToDo
* Test dataplane integration
* Add ident bootstrap entry if admin user is different from postgres

## Collection hostgroups

| Hostgroup       |           Default | Description                                               |
|:----------------|------------------:|:----------------------------------------------------------|
| patroni_cluster | 'patroni_cluster' | Patroni DBMS hosts                                        |
| patroni_consul  |  'patroni_consul' | Patroni Consul Distibuted Configuration Store (DCS) hosts |
| patroni_barman  |  'patroni_barman' | Patroni Barman hosts                                      |

## Collection variables

The following is the list of parameters intended for end-user manipulation: 

Cluster wide parameters

| Parameter                            |                         Default | Description                             | Required |
|:-------------------------------------|--------------------------------:|:----------------------------------------|:---------|
| patroni_cluster_name                 |                             n/a | Patroni cluster name                    | true     |
| patroni_cluster_api_username         |                         patroni | Patroni cluster restapi username        | false    |
| patroni_cluster_api_password         |                             n/a | Patroni cluster restapi password        | true     |
| patroni_cluster_postgres_password    |                             n/a | Patroni cluster replication  password   | true     |
| patroni_cluster_replication_username |                      replicator | Patroni cluster replication username    | false    |
| patroni_cluster_replication_password |                             n/a | Patroni cluster replication  password   | true     |
| patroni_config_hostnames             |                            true | Use hostnames for Patroni configuration | false    |
| patroni_consul_version               |                        'latest' | Consul version                          | false    |
| patroni_consul_datacenter            |                       'patroni' | Consul Datacenter name                  | false    |
| patroni_consul_backup_path           |               '/backups/consul' | Consul snapshot backup path             | false    |
| patroni_consul_backup_bin            | '/usr/local/bin/consul-snapshot | Consul snapshot backup script location  | false    |
| patroni_consul_backup_retention      |                            1440 | Consul snapshot retention in minutes    | false    |
| patroni_consul_backup_minutes        |                          '\*/5' | Consul snapshot cronjob component       | false    |
| patroni_consul_backup_hours          |                            '\*' | Consul snapshot cronjob component       | false    |
| patroni_consul_backup_days           |                            '\*' | Consul snapshot cronjob component       | false    |

## ToDo
* Bootstrap Patroni cluster
* Add feature to pin Consul packages
* Add feature to pin Patroni packages
* Refactor Consul playbook into independent collection
* Refactor all collections with Consul deployments to pull from Consul collection

## Collection playbooks

* nephelaiio.patroni.install: Install and bootstrap cluster

## Testing

Please make sure your environment has [docker](https://www.docker.com) installed in order to run role validation tests.

Role is tested against the following distributions (docker images):

  * Ubuntu Jammy
  * Ubuntu Focal
  * Rocky Linux 9

You can test the collection directly from sources using command `make test`

## License

This project is licensed under the terms of the [MIT License](/LICENSE)

