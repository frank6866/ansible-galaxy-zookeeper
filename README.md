# zookeeper

This role is used to deploy zookeeper cluster on CentOS/RHEL.

## Role Variables


The variables for zookeeper, as the default values listed below:

```
zk_maxClientCnxns : 50
zk_tickTime : 2000
zk_initLimit : 10
zk_syncLimit : 5
zk_dataDir : /var/lib/zookeeper
zk_data_logDir : /var/lib/zookeeper
zk_clientPort : 2181
zk_leaderPort : 2888zk_electionPort : 3888
```

## Example Inventory file

```
zk-1 ansible_ssh_host=192.168.168.201 ansible_ssh_port=22 ansible_ssh_user=centos
zk-2 ansible_ssh_host=192.168.168.202 ansible_ssh_port=22 ansible_ssh_user=centos
zk-3 ansible_ssh_host=192.168.168.203 ansible_ssh_port=22 ansible_ssh_user=centos


[cluster1]
zk-1 zk_myid=1 zk_ip=192.168.168.201
zk-2 zk_myid=2
zk-3 zk_myid=3


[zookeeper:children]
cluster1

```

If you have only one ip in the host, you can ignore the variable "zk_ip". If you have multiple ip in a host, you should specify the ip used by zookeeper through variable "zk_ip".


## Example Playbook

Playbook:

```
- hosts: zookeeper
  become: true
  roles:
    - { role: /path/to/zookeeper-role }

```


## Zookeeper Usage


```
# cli
zookeeper-client

# check status
zookeeper-server status

```


## Testing

There are 3 hosts in "Vagrantfile" in the root directory, run the "vagrant.sh" script to test.

```
# ./vagrant.sh
```

License
-------

MIT

