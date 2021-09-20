artchain
--------
HyperLedger Art Blockchain

## Quick start

1. Install Virtualbox and Vagrant
```
#Install vbguest plugin:
vagrant plugin install vagrant-vbguest
```

2. Build vms for org1 and org2 first
```
  cd local
  vagrant up
```
3. Build vm to run ansible playbook on org1 and org2 
```
  cd ..
  vagrant up
```
