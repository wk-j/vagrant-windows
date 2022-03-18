Vagrant.configure("2") do |config|
    config.vm.box = "jacqinthebox/windows10"
    config.vm.box_version = "0.1"
    config.vm.network "forwarded_port", guest: 3389, host: 3389
    config.vm.network "private_network", ip: "192.168.56.33"

    config.winrm.username = "vagrant"
    config.winrm.password = "vagrant"

    config.vm.synced_folder "resource", "/wk"
    config.vm.synced_folder ".", "/vagrant", disabled: true

    config.vm.provider "virtualbox" do |v|
        v.memory = 4000
        v.cpus = 2
    end

    # config.vm.provision "shell", inline: "echo Hello, World"

    config.vm.provision "shell", inline: "Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All"

    config.vm.provision "shell" do |shell|
        shell.path = "config/install.ps1"
    end
end
