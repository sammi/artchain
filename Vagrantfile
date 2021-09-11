VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-get install -y ansible
sudo apt-get install -y net-tools
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "public_network", use_dhcp_assigned_default_route: true
  config.vm.provision "shell", inline: $script 
end

