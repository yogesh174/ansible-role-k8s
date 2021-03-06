yogesh174.ansible_role_provisioning
=========

This role configures HA k8s cluster.

Role Variables
--------------

variables in vars/main.yml
- network_name : Network name which will be assigned to pods
- services : list of all services to start
- software: list of all software to install

Example Playbook
----------------

"all_nodes" task from create_k8s_cluster role which will install all the necessry software, configure them and start their respective services:

    - hosts: tag_cluster_k8s
      become: yes      
      tasks:
        - name: "Import the provisioning role"
          include_role:
            name: create_k8s_cluster
            tasks_from: all_nodes
          vars:
            network_name: "10.240.0.0/16"

"master_node" task from create_k8s_cluster role which will configure k8s on master node.

    - hosts: tag_node_master
      become: yes

      tasks:
        - name: "Import master role"
          include_role:
            name: create_k8s_cluster
            tasks_from: master_node
          vars:
            network_name: "10.240.0.0/16"

Author Information
------------------

Surapaneni Yogesh - surapaneniyogesh11@gmail.com  
Connect with me on [LinkedIN](https://www.linkedin.com/in/surapaneni-yogesh-ba7303189/)
