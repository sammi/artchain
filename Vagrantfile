VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT

sudo apt-get update
sudo apt-get install -y ansible

#Install network tools, such as ifconfig.
sudo apt-get install -y net-tools

#Install step
wget https://github.com/smallstep/cli/releases/download/v0.17.2/step-cli_0.17.2_amd64.deb
sudo dpkg -i step-cli_0.17.2_amd64.deb

#Install step-ca
wget https://github.com/smallstep/certificates/releases/download/v0.17.2/step-ca_0.17.2_amd64.deb
sudo dpkg -i step-ca_0.17.2_amd64.deb

SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provision "shell", inline: $script 
end

