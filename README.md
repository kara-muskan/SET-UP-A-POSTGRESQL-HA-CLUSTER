# SET-UP-A-POSTGRESQL-HA-CLUSTER
Setting up a High Availability (HA) cluster for PostgreSQL typically involves configuring multiple nodes to ensure data availability and reliability. In this tutorial, I deploy 3 PostgreSQL nodes with Patroni for HA, setting up etcd for consensus, and use HAProxy to manage client connections.

**Prerequisites**:
-3 postgresql cluster node (ubuntu 22.04 minimal install) and postgres14
-1 etcd host (ubuntu 22.04 minimal install)
-1 haproxy host (ubuntu 22.04 minimal install)**

**My IP Plan**

Postgresql and patroni node1: 10.10.0.181

Postgresql and patroni node2: 10.10.0.182

Postgresql and patroni node1: 10.10.0.183

etcd node:

HAproxy:

**STEPS**

-Upgrade all nodes
```
sudo apt update
sudo apt upgrade
```
-Install Postgresql server software on node1,node2, and node3. Also, stop the Postgresql service after installation
```
sudo apt install postgresql postgresql-contrib -y
sudo systemctl stop postgresql
```





