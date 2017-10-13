# Prerequisites validation

## Vagrant version
Vagrant.require_version ">= 2.0.0"

## Plugins
unless Vagrant.has_plugin?("vagrant-hostsupdater")
  raise 'Missing vagrant-docker-compose plugin! Make sure to install it by `vagrant plugin install vagrant-hostsupdater`.'
end
unless Vagrant.has_plugin?("vagrant-docker-compose")
  raise 'Missing vagrant-docker-compose plugin! Make sure to install it by `vagrant plugin install vagrant-docker-compose`.'
end

## Variables
$app_name = "vagrant-docker-compose-nginx-example"
$vm_ip = "192.168.3.10"
$vm_memory = 512
$vm_cpu = 1
$host_entry = "127.0.0.1\tmyfirstpage.com\n127.0.0.1\tmysecondpage.com\n127.0.0.1\tmythirdpage.com"

# Definitions	
Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vm.hostname = $app_name
  config.vm.network "forwarded_port", guest: 80, host: 80
  config.vm.network "private_network", ip: $vm_ip
  config.vm.synced_folder "docker", "/home/centos/docker"

  config.vm.provider "virtualbox" do |vb|
    vb.name = $app_name
    vb.customize ['modifyvm', :id, '--memory', $vm_memory, '--cpus', $vm_cpu]
  end

  config.vm.provision "shell", inline: <<-SHELL
    cp /home/centos/docker/nginx-container.service /etc/systemd/system/
  SHELL

  config.vm.provision "docker" do |docker|
    docker.post_install_provision "shell", inline:'echo -e "%s" >> /etc/hosts;' % $host_entry
    docker.build_image "/home/centos/docker/", args: "-t %s" % $app_name
  end

  config.vm.provision :docker_compose,
    yml: "/home/centos/docker/docker-compose.yml",
    rebuild: false,
    run: "always"

  config.vm.define :config_systemctl do |config_system|
    config_system.vm.provision :shell, inline: "systemctl enable nginx-container.service;systemctl start nginx-container.service"
  end

end
