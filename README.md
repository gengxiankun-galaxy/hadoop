HADOOP
=========

通过 ansible 部署在容器下运行的 Hadoop 服务。

Installation
------------

`ansible-galaxy install gengxiankun.hadoop`

Role Variables
--------------

variable | description
------------ | -------------
CLUSTER_NAME | 集群名称，默认 test
HADOOP_VERSION | hadoop 版本
HADOOP_URL | hadoop 下载地址
DFS_NAMENODE_NAME_DIR | dfs.namenode.name.dir
DFS_DATANODE_DATA_DIR | dfs.datanode.data.dir
YARN_NODEMANAGER_REMOTE_APP_LOG_DIR | yarn.nodemanager.remote-app-log-dir
YARN_NODEMANAGER_LOG_DIRS | yarn.nodemanager.log-dirs
YARN_NODEMANAGER_LOCAL_DIRS | yarn.nodemanager.local-dirs
HOSTNAME | 节点名称
HADOOP_SOFT_NOFILE | 可打开的文件描述符的最大数(超过会警告)
HADOOP_HARD_NOFILE | 可打开的文件描述符的最大数(超过会报错)
NAMENODE_ENABLE | 是否安装 namenode 相关服务（包含 namenode、resourcemanger、jobhistry）
DATANODE_ENABLE | 是否安装 datanode 相关服务（包含 datanode、nodemanger）

Example Playbook
----------------

```
namenode-001 ansible_ssh_host=xxx.xxx.xxx.xxx HOSTNAME=namenode-001
datanode-001 ansible_ssh_host=xxx.xxx.xxx.xxx HOSTNAME=datanode-001
datanode-002 ansible_ssh_host=xxx.xxx.xxx.xxx HOSTNAME=datanode-002

[hadoop-cluster]
namenode-001 NAMENODE_ENABLE=true HIVE_ENABLE=true PRESTO_ENABLE=true
datanode-001 DATANODE_ENABLE=true
datanode-002 DATANODE_ENABLE=true
```

    - hosts: hadoop-cluster
      roles:
        - gengxiankun.hadoop

License
-------

BSD

Author Information
------------------

This role was created in 2019 by Xiankun Geng, Learn more about the author's role in [galaxy](https://galaxy.ansible.com/gengxiankun).
