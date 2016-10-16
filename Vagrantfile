

Vagrant.configure(2) do |config|

  # Falls vbguest-plugin bitte Guest nachladen
  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = true
  end

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    # vb.gui = true
    # Customize the amount of memory on the VM:
    vb.memory = "768"
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    vb.linked_clone = true
  end

  config.vm.box = "ubuntu_de_201610051341"

  config.vm.hostname = "docker"
  # Bitte in hosts eintragen.
  # 192.168.5.60 ubuntu_ais ubuntu_ais
  # Somit kann mit ping ubuntu_ais bzw. http://ubuntu_ais
  # aufgerufen werden.
  config.vm.network "private_network",
   ip: "192.168.6.20"

  # DHCP und WWW über das lokale Netz
  # Die DHCP Einstellungen werden übernommen
  config.vm.network "public_network",
   use_dhcp_assigned_default_route: true

  config.vm.provider "virtualbox" do |vb|
    vb.name = "ubuntu_ais_docker.rdf"
  end
  config.vm.synced_folder "projects/", "/home/vagrant/projects"
  config.vm.provision "shell", inline: <<-SHELL
     sudo pip install --upgrade ansible
     sudo apt-get update && sudo apt-get autoremove -y && sudo apt-get dist-upgrade -y
  SHELL
  # Falls vbguest-plugin bitte Guest nachladen
  if Vagrant.has_plugin?("vagrant-reload") then
    config.vm.provision :reload
  end
end
