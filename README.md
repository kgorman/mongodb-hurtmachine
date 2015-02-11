# mongodb-hurtmachine
An Ansible playbook for load testing MongoDB (and TokuMX) using sysbench-mongodb. Uses Ansible roles from Galaxy for the heavy lifting, this is just a harness to run everything from for the most part.

## Installation

- Clone this repo
- Install the roles
- Hack up the hosts.txt file to match your environment
- Run the playbook

```bash
git clone https://github.com/kgorman/mongodb-hurtmachine.git
cd mongodb-hurtmachine
ansible-galaxy install kgorman.mongodb
ansible-galaxy install kgorman.TokuMX-Install
ansible-galaxy install kgorman.sysbench-mongodb
```

Change the [loadservers] and [mongodbservers] lines in hosts.txt to match your enviroment.

```bash
ansible-playbook -i hosts.txt site.yml
```
