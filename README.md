# Ansible Cassandra

This is a Ansible role to install Apache Cassandra (Support Ubuntu14/16, CentOS7)

## Requirements

Ansible 2.1

## Role Variables

|Variable|Default Value|Description|
|---|---|---|
```cassandra_ver```|3.10|version of cassandra that you wnat to install.
```cassandra_cluster_name```|Cassandra Cluster|cassandra cluster name.
```cassandra_seeds```|127.0.0.1|cassandra seeds.
```cassandra_hosts```|['localhost']|cassandra listen ip address list.
```cassandra_storage_listen_port```|7000|cassandra storage listen port.
```cassandra_is_start_rpc```|true|enable rpc or not.
```cassandra_rpc_listen_port```|9160|cassandra rpc listen port.

## Example
```
### create a requirements.yml
- src: git+https://github.com/willyhutw/ansible-role-cassandra.git
  name: ansible-role-cassandra

### create a playbook.yml
- hosts: all
  become: yes
  roles:
    - roles/ansible-role-cassandra

### install this role
ansible-galaxy install -r requirements.yml -p ./roles

### run it!
ansible-playbook -i '192.168.33.101,' playbook.yml \
-e "ansible_ssh_user=willyhu ansible_ssh_pass=secret ansible_become_pass=secret" \
-e "cassandra_seeds=192.168.33.101" \
-e "{'cassandra_hosts':['192.168.33.101']}"

ansible-playbook -i '192.168.33.101,192.168.33.102,192.168.33.103,' playbook-cassandra.yml \
-e "ansible_ssh_user=vagrant ansible_ssh_pass=vagrant ansible_become_pass=vagrant" \
-e "cassandra_seeds=192.168.33.101,192.168.33.102 \
-e {'cassandra_hosts':['192.168.33.101','192.168.33.102','192.168.33.103']}"
```

## License

MIT / BSD

## Author Information

willyhu.tw@gmail.com

