# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/sytax version. Don’t touch unless you know what you’re doing!
VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Variable Definitions:
  # ------------------------
  #
  GHOST_COUNT = 1

  # Guest Definitions:
  # ------------------------
  #

  # START: ghost Definition(s)
  GHOST_COUNT.times do |e|
    config.vm.define vm_name = "ghost#{e}" do |ghost|
      ghost.vm.box = "ubuntu/trusty64"
      ghost.vm.hostname = "ghost#{e}"
      # NETWORK-SETTINGS: eth1 configured in the 192.168.236.0/24 network
      ghost.vm.network "private_network", ip: "192.168.236.1#{e}"
      ghost.vm.network "forwarded_port", guest: 2368, host: 12368
      ghost.vm.provider "virtualbox" do |vb|
        vb.name = "roto_ghost#{e}"
        vb.customize ["modifyvm", :id, "--memory", "512"]
        vb.customize ["modifyvm", :id, "--cpus", "1"]
      end
      config.vm.provision :ansible do |ansible|
        ansible.playbook = "ghost-install/ghost-install.yml"
      config.vm.provision "shell", privileged: false, inline: <<-EOF
        echo "Vagrant Box provisioned!"
        echo "Ghost Address: http://192.168.236.1#{e}:2368"
        echo "Ghost app_log: /var/log/supervisor/ghost.log"
        echo "Ghost err_log: /var/log/supervisor/ghost_err.log"
        echo ""
        echo "NOTICE: If you are using a byob, you may import your backup"
        echo "using the ghost importer in the 'Labs' section of the Ghost"
        echo "management interface You will likely need to import your"
        echo "Blog Logo and Cover pictures again."
        EOF
      end
    end
  end
  # STOP: ghost Definition(s)
end
