# ansible-docker-swarm

Hosts file: 

```
exemplo: 
$ cat /etc/hosts
192.168.1.10 swarm-manager
192.168.1.11 swarm-worker-1
192.168.1.12 swarm-worker-2
```
Install Ansible:

```
$ apt install python-setuptools -y
$ easy_install pip
$ pip install ansible
```

Ensure passwordless ssh is working:

```
$ ansible -i inventory.ini -u root -m ping all
client | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
swarm-manager | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
swarm-worker-2 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
swarm-worker-1 | SUCCESS => {
    "changed": false, 
    "ping": "pong"
}
```

## Deploy Docker Swarm

```
$  ansible-playbook deploy-swarm.yml -i inventory-"env".ini --ask-sudo-pass
PLAY RECAP 

client                     : ok=11   changed=3    unreachable=0    failed=0   
swarm-manager              : ok=18   changed=4    unreachable=0    failed=0   
swarm-worker-1             : ok=15   changed=1    unreachable=0    failed=0   
