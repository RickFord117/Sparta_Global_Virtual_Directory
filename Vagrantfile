# Install required plugins
required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|

    config.vm.define :ricardo do |ricardo|
      ricardo.vm.box = "ubuntu/xenial64"
      ricardo.vm.network "private_network", ip: "192.168.10.100"
      ricardo.hostsupdater.aliases = ["ricardo.local"]
      ricardo.vm.synced_folder ".", "/home/ubuntu/ricardo"
    end

    config.vm.define :example do |example|
    example.vm.box = "ubuntu/xenial64"
    example.vm.network "private_network", ip: "192.168.10.101"
    example.hostsupdater.aliases = ["example.local"]

  end
  config.vm.provision "shell", path: "environment/app/provision.sh", privileged: false
end
