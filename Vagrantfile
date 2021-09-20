VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-get update
sudo apt-get install -y ansible
SCRIPT

require 'yaml'

servers = YAML.load_file(File.join(File.dirname(__FILE__), 'local/servers.yaml'))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "generic/ubuntu2010"
  config.vm.network "private_network", ip: "192.168.56.11"
  config.vm.provision "shell", inline: $script
  config.vm.provision "file", source: "ansible", destination: "."
  servers.each do |server|
    config.vm.provision "file", source: server["private_key_src"], destination: server["private_key_target"]
    config.vm.provision "shell", inline: "chmod 600 #{server["private_key_target"]}"
  end
  config.vm.provision "shell", inline: "ansible-playbook site.yaml"
end
