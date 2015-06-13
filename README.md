elasticsearch
=============

An Ansible role designed to help deploy and manage Elasticsearch clusters.

Requirements
------------

We assume nginx is your web proxy frontend for Elasticsearch, and will be installed on the system by this role.

Role Variables
--------------

Right now the only variables are:

  * `elasticsearch_group_name`  - used by the role to find your elasticsearch nodes and also will be the name of the elasticsearch cluster that will be set up.
  * `elasticsearch_do_firewall` - set to true if you want the role to handle blocking outside traffic to your cluster on the ES internal transport ports
  * `elasticsearch_http_password` - use this to set the password for write operation access to the Elasticsearch HTTP APIs
  * `elasticsearch_is_master` - this will need to be True on at least one of your nodes in the cluster, otherwise they become data nodes only


Examples
--------

Example playbook file - elasticsearch.yaml

    - hosts: my_elasticsearch_cluster
      vars:
        elasticsearch_group_name: my_elasticsearch_cluster
      roles:
        - { role: elasticsearch, elasticsearch_do_firewall: true }

Example hosts file - elcluster

    [my_elasticsearch_cluster]
    elsearch01 elasticsearch_is_master=true
    elsearch02
    elsearch03


License
-------

Apache 2
