artchain
--------
HyperLedger Art Blockchain

## Quick start on Windows 10

1. Install Virtualbox and Vagrant
```
#Install vbguest plugin:
vagrant plugin install vagrant-vbguest
```

2. Start ansible vagrant vm and ssh into virtual box

```
  vagrant up
  vagrant ssh
```
3. Run ansible in virtual machine
```
  ansible --version
```
4. Start vms for org1 and org2
```
  cd local
  vagrant up
```
5. Check org1 and org2
```
  cd local

  #Login into org1
  vagrant org1

  #Login into org2
  vagrant org2
```

