# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.5.0"

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "hashicorp/precise64"

    config.vm.box_check_update = false

    # Create a private network, which allows host-only access to the machine
    # using a specific IP.
    config.vm.network "private_network", ip: "192.168.33.30"
    config.vm.network :forwarded_port, guest: 3000, host: 3000
    config.vm.network :forwarded_port, guest: 8080, host: 9539
    config.vm.network :forwarded_port, guest: 80, host: 9540

    config.vm.provider :virtualbox do |v|
        v.memory = 4048
        v.cpus = 2
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
    end

    config.vm.provision "ansible" do |ansible|
       ansible.groups = {
       "dev" => ["default"]
       }
       ansible.playbook = "local.yml"
    end

    # Build from source
    # config.vm.provision "shell" do |s|
    #  s.inline = "echo 'deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse' >> /etc/apt/sources.list"
    #  s.inline += "&& apt-get update"
    #  s.inline += "&& apt-get install -y ansible"
    #  s.inline += "&& ansible-galaxy install sunnepah.tyk --force"
    #  s.inline += "&& ansible-playbook -i /etc/ansible/roles/sunnepah.tyk/hosts /etc/ansible/roles/sunnepah.tyk/local.yml -v"
    # end
end
