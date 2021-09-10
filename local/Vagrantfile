VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-get install -y ansible
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.provision "shell", inline: $script 
end

