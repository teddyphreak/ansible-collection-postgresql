# Ansible Collection - nephelaiio.patroni

[![Build Status](https://github.com/nephelaiio/ansible-collection-patroni/actions/workflows/molecule.yml/badge.svg)](https://github.com/nephelaiio/ansible-collection-patroni/actions/wofklows/molecule.yml)
[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-nephelaiio.patroni-blue.svg)](https://galaxy.ansible.com/ui/repo/published/nephelaiio/patroni/)

An [ansible collection](https://galaxy.ansible.com/ui/repo/published/nephelaiio/patroni/) to install and manage [Patroni](https://patroni.readthedocs.io/en/latest/README.html) clusters

## Collection hostgroups

| Hostgroup       |           Default | Description                                               |
|:----------------|------------------:|:----------------------------------------------------------|
| patroni_cluster | 'patroni_cluster' | Patroni DBMS hosts                                        |
| patroni_consul  |  'patroni_consul' | Patroni Consul Distibuted Configuration Store (DCS) nodes |

## Collection variables

The following is the list of parameters intended for end-user manipulation: 

Cluster wide parameters

| Parameter                  |                         Default | Type    | Description                                       | Required |
|:---------------------------|--------------------------------:|:--------|:--------------------------------------------------|:---------|
| patroni_config_hostnames   |                            true | boolean | Toggle use of hostnames for Patroni configuration | false    |
| patroni_consul_datacenter  |                       'patroni' | string  | Consul Datacenter name                            | false    |
| patroni_consul_backup_path |               '/backups/consul' | string  | Consul snapshot backup path                       | false    |
| patroni_consul_backup_bin  | '/usr/local/bin/consul-snapshot | string  | Consul snapshot backup script location            | false    |

## ToDo
* Create Consul backup bin script
* Create Consul backup cronjob
* Create Consul backup MOTD

## Collection roles

* nephelaiio.patroni.consul
* nephelaiio.patroni.pgpg
* nephelaiio.patroni.posgresql

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

