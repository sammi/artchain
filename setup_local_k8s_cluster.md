Setup local kubernetes clusters
-------------------------------

1. Install [Virtualbox](https://www.virtualbox.org/) and [Vagrant](https://www.vagrantup.com/)
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
  vagrant up --provision
```
4. Copy kube config files to local

You could get your local private key path by run:

```
  vagrant ssh-config
```

Run the following command in powershell:
```
cd artchain
scp -i local/.vagrant/machines/org1/virtualbox/private_key vagrant@192.168.56.12:/home/vagrant/.kube/config ~/.kube/org1_config

scp -i local/.vagrant/machines/org2/virtualbox/private_key vagrant@192.168.56.13:/home/vagrant/.kube/config ~/.kube/org2_config
```

5. Install [lens](https://k8slens.dev/) and connect clusters
Connect clusters for .kube/org1_config and .kube/org2_config

![Screenshot](lens_with_clusters.png)
