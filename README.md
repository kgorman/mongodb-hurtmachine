# mongodb-hurtmachine
An Ansible playbook for load testing MongoDB (and TokuMX) using sysbench-mongodb. Uses Ansible roles from Galaxy for the heavy lifting, this is just a harness to run everything from for the most part.

## Requirements
- git
- [ansible](http://docs.ansible.com/intro_installation.html)

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

- Change the [loadservers] and [mongodbservers] lines in hosts.txt to match your enviroment.
- Copy your public key over to each of the servers root account. Some cloud platforms like Rackspace and AWS handle this for you. If you are doing it manually here is a [Primer](http://docs.ansible.com/intro_getting_started.html#remote-connection-information)

```bash
ansible-playbook -i hosts.txt site.yml
```

## Running a load test

To run the load test in sysbench-mongodb.

```bash
ssh root@<loadserver ip>
bash
cd sysbench
export CLASSPATH=./mongo-java-driver-2.13.0-rc2.jar
./run.simple.bash
```
