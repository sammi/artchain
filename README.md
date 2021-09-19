artchain
--------
HyperLedger Art Blockchain

## Quick start on Windows 10

1. Install Virtualbox and Vagrant
```
#Install vbguest plugin:
vagrant plugin install vagrant-vbguest
```

2. Build vms for org1 and org2 first, it generates private key for org1 and org2
```
  cd local
  vagrant up
```
3. Build vm to run ansible command

```
  cd ..
  vagrant up
```
4. Run ansible in virtual machine
SSH into ansible vm:
```
  vagrant ssh
```
Run ansible command to test if ansible vm could connect to target hosts
```
  ansible -m ping all
```
Your should be able to see:
```
192.168.56.13 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
192.168.56.12 | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3"
    },
    "changed": false,
    "ping": "pong"
}
```

