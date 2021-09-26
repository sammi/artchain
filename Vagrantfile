VAGRANTFILE_API_VERSION = "2"

$script = <<-SCRIPT
sudo apt-get update
sudo apt-get install -y ansible
wget https://releases.hashicorp.com/vault/1.8.2/vault_1.8.2_linux_amd64.zip
unzip vault_1.8.2_linux_amd64.zip
chmod a+x vault
sudo mv vault /usr/bin/.
complete -C /usr/bin/vault vault
sudo setcap cap_ipc_lock=+ep /usr/local/bin/vault
sudo mv vault.service /etc/systemd/system/vault.service
sudo useradd --system --home /etc/vault.d --shell /bin/false vault
SCRIPT

require 'yaml'

servers = YAML.load_file(File.join(File.dirname(__FILE__), 'local/servers.yaml'))

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ansible"
  config.vm.box_url = "file://./ansible_abovetheborg_ubuntu-focal.box"
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
