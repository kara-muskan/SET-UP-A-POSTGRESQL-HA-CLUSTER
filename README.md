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
-create a symlink of /usr/lib/postgresql/14/bin/ to /usr/sbin as it contains some tools used for Patroni
```
sudo ln -s /usr/lib/postgresql/14/bin/* /usr/sbin
```
-Install patroni on node1,node2,node3

Before installing Patroni, you will need to install Python and other dependencies on node1, node2, node3
```
sudo apt -y install python3-pip python3-dev libpq-dev
pip3 install --upgrade pip
sudo pip install patroni
sudo pip install python-etcd
sudo pip install psycopg2
```
-Install etcd on node4
```
sudo apt install etcd -y
```
-Configure Etcd

You can configure it by editing the file /etc/default/etcd
```
sudo nano /etc/default/etcd
```
and paste the configuration present in etcd file.
Save and close the file then restart the Etcd service to apply the changes and You can also verify the status of the service using given command
```
sudo systemctl restart etcd
sudo systemctl status etcd
```
-Configure Patroni







