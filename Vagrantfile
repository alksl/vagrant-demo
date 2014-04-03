# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

   # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "base"

  # The url from where the 'config.vm.box' box will be fetched if it
  # doesn't already exist on the user's system.
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # config.vm.network :forwarded_port, guest: 80, host: 8080

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network :private_network, ip: "192.168.33.10"

  # Use onmibus chef
  config.omnibus.chef_version = :latest

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network :public_network

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  # config.ssh.forward_agent = true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Enable provisioning with chef solo, specifying a cookbooks path, roles
  # path, and data_bags path (all relative to this Vagrantfile), and adding
  # some recipes and/or roles.
  #
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "./berks-cookbooks"
    chef.add_recipe "apt"
    chef.add_recipe "zsh"
    chef.add_recipe "git"
    chef.add_recipe "vim"
    chef.add_recipe "dotfiles"

    chef.json = {
      "dotfiles" => {
        "users" => ["vagrant"]
      },
      "vim" => {
        "extra_packages" => ["vim-nox"]
      }
    }
  end

  # Install swedish locale
  config.vm.provision :shell, inline: "locale-gen sv_SE.UTF-8; update-locale LANG=sv_SE.UTF-8"

  # Change shell for vagrant user
  config.vm.provision :shell, inline: "chsh -s /bin/zsh vagrant"

  # Install tmux
  config.vm.provision :shell, inline: "apt-get install tmux"

  config.vm.provision :shell, inline: "chsh -s /bin/zsh vagrant"
end
