VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install -y ansible
SCRIPT

require 'yaml'

servers = YAML.load_file(File.join(File.dirname(__FILE__), 'local/servers.yaml'))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ansible"
  config.vm.box_url = "https://mirrors.tuna.tsinghua.edu.cn/ubuntu-cloud-images/bionic/current/bionic-server-cloudimg-amd64-vagrant.box"
  config.vm.network "private_network", ip: "192.168.56.11"
  config.vm.provision "file", source: "ansible", destination: "."
  config.vm.provision "file", source: "vault.service", destination: "vault.service"
  config.vm.provision "shell", inline: $script
  servers.each do |server|
    config.vm.provision "file", source: server["private_key_src"], destination: server["private_key_target"]
    config.vm.provision "shell", inline: "chmod 600 #{server["private_key_target"]}"
  end
  config.vm.provision "shell", inline: "ansible-playbook site.yaml"
end
