Setup local kubernetes clusters in Windows 10 - Using Cmd Window please
-----------------------------------------------------------------------

1. Install [Virtualbox](https://www.virtualbox.org/) and [Vagrant](https://www.vagrantup.com/)
Install vbguest plugin
```
vagrant plugin install vagrant-vbguest
```

2. Get the code and build vms for org1 and org2 first
```
  cd C:/
  git clone https://github.com/sammi/artchain.git
  cd C:/artchain/local
  vagrant destroy -f
  vagrant up
```
3. Build vm to run ansible playbook on org1 and org2 
```
  cd C:/artchain
  vagrant destroy -f
  vagrant up
```
4. Copy kube config files to local
Use cmd window, not powershell window to run the following commands.
```
rm -rf %homedrive%%homepath%/.kube/*
cd C:/artchain/local
scp -i .vagrant/machines/org1/virtualbox/private_key vagrant@192.168.56.12:/home/vagrant/.kube/config %homedrive%%homepath%/.kube/org1_config
scp -i .vagrant/machines/org2/virtualbox/private_key vagrant@192.168.56.13:/home/vagrant/.kube/config %homedrive%%homepath%/.kube/org2_config
```

5. Install [lens](https://k8slens.dev/) and connect clusters

Connect clusters for .kube/org1_config and .kube/org2_config

![Screenshot](lens_with_clusters.png)
