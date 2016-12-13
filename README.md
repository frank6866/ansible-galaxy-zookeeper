zookeeper
=========

This role install zookeeper cluster on CentOS/RHEL.

Role Variables
--------------

The variables for zookeeper, as the default values listed below:

        zk_maxClientCnxns : 50
        zk_tickTime : 2000
        zk_initLimit : 10
        zk_syncLimit : 5
        zk_dataDir : /var/lib/zookeeper
        zk_data_logDir : /var/lib/zookeeper
        zk_clientPort : 2181
        zk_leaderPort : 2888
        zk_electionPort : 3888


Example Playbook
----------------

If you have only one ip in the host, you can ignore the variable "zk_ip". If you have multiple ip in a host, you should specify the ip used by zookeeper through variable "zk_ip".  

> Notice: hosts should be in the group "zookeeper".

Inventory file:

```

[zookeeper]
vagrant1 zk_myid=1
vagrant2 zk_myid=2 zk_ip=192.168.168.202
vagrant3 zk_myid=3 zk_ip=192.168.168.203

```

Playbook:

```

- hosts: servers
   roles:
      - { role: frank6866.zookeeper }

```


Zookeeper Usage
---------------

```
# cli
zookeeper-client

# check status
zookeeper-server status

```


Testing
-------
There are 3 hosts in "Vagrantfile" in the root directory, run the "vagrant.sh" script to test.

```

./vagrant.sh

```



License
-------

MIT

