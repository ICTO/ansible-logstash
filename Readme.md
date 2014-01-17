# Readme

## Description

*ansible-logstash* is an [Ansible](http://ansible.cc) role.
The role contains tasks to install Logstash.

## Provides

1. Logstash

## Requires

1. Ansible 1.4 or higher
2. Debian 7.3 (other deb-based distros should work too)
3. Vagrant (optional)

## Usage

### Get the code

```bash
$ git clone git@github.com:ICTO/ansible-logstash.git
```

### Create the playbook file

```
---
- name: Logstash
  hosts: logstash
  roles:
    - ansible-logstash
```

### Run the playbook

Use *ansible.host* as inventory. Run the playbook only for the remote host *logstash*. Use *vagrant* as the SSH user to connect to the remote host. *-k* enables the SSH password prompt.

```bash
$ ansible-playbook -k -i ansible.host logstash.yml -u vagrant
```

### Example output

```
SSH password: 

PLAY [Logstash] ************************************************************* 

TASK: [ansible-logstash | Install Logstash dependencies] ********************** 
ok: [127.0.0.1] => (item=openjdk-6-jre)
ok: [127.0.0.1] => (item=openjdk-6-jdk)

TASK: [ansible-logstash | Create Logstash directories] ************************ 
ok: [127.0.0.1] => (item=/opt/logstash)
ok: [127.0.0.1] => (item=/opt/logstash/bin)
ok: [127.0.0.1] => (item=/opt/logstash/etc)

TASK: [ansible-logstash | Install Logstash indexer init script] *************** 
changed: [127.0.0.1]

TASK: [ansible-logstash | Install Logstash shipper init script] *************** 
changed: [127.0.0.1]

TASK: [ansible-logstash | Install Logstash indexer config] ******************** 

ok: [127.0.0.1]

TASK: [ansible-logstash | Install Logstash shipper config] ******************** 
ok: [127.0.0.1]
```