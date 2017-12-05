### Ansible playbook for deploying ceph cluster in vagrant

Setup your ceph cluster with vagrant and ansible for testing purposes.

Probably i will use this repository as skeleton for future production-ready ansible deployment of ceph cluster. (Or may be i will use official ceph playbook, who knows... )
### Usage
Generate and put ssh key pair in variables
```
ceph_admin_user_pubkey: "ENTER SSH PUBLIC KEY HERE"
ceph_admin_user_privkey: "SSH PRIVATE KEY HERE" # PUT THIS VARIABLE IN DEDICATED FILE ENCRYPTED WITH ANSIBLE-VAULT
```
Then run
```vagrant up```

### Variables
```yaml
release_name: "xenial"
ceph_admin_user: "cephadm"
# ceph-deploy needs to establish passwordless ssh connection to nodes
ceph_admin_user_pubkey: "ENTER SSH PUBLIC KEY HERE"
ceph_admin_user_privkey: "SSH PRIVATE KEY HERE" # PUT THIS VARIABLE IN DEDICATED FILE ENCRYPTED WITH ANSIBLE-VAULT
nodes:
  node1:
    ip: 192.168.33.20
    hostname: machine2
    disk: sdc
  node2:
    ip: 192.168.33.30
    hostname: machine3
    disk: sdc
  node3:
    ip: 192.168.33.40
    hostname: machine4
    disk: sdc

monitor_instances:
  - machine2
  - machine3
  - machine4
```
### Tested with
```
$ vagrant --version
Vagrant 2.0.0
$ ansible --version
ansible 2.4.1.0
```
