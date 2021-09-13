VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-get update
sudo apt-get install -y ansible
sudo apt-get install -y net-tools
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provision "shell", inline: $script 
end

