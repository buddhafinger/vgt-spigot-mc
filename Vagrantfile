# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrant setup for minecraft servers. For use with virtualbox

# If you plan on making your server accessible on your network, you may need
# to change this device name (works for macbooks)
$BRIDGE_DEVICE = 'en0: WiFi (AirPort)'

Vagrant.configure("2") do |config|
  #line to prevent stdin is not a tty error.
  #config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
  config.vm.box = "ubuntu/trusty64"
  
  #need to uncomment the next line when we are ready with the spigot-bootstrapfile.
  config.vm.provision :shell, :path => "spigot-mc_bootstrap"

  # We're going to increase the ram to 1.5GB. This may make it unplayable if
  # you're host doesn't have very much memory
  config.vm.provider "virtualbox" do |v|
    v.cpus = 2
    v.memory = 2056 
  end

  # This will make minecraft accessible on localhost port 25565
  config.vm.network "forwarded_port", guest: 25565, host: 25565

  # If you plan on having others join your minecraft server, comment out the
  # line above and uncomment this line, which will give your server a private
  # IP address on your local network. You may need to adjust your bridge
  # device, which is set at the top of this script.

  # See this link for more information:
  #   http://docs-v1.vagrantup.com/v1/docs/bridged_networking.html

  #config.vm.network "public_network", :bridge => "en0: Wi-Fi (AirPort)"
 config.vm.network "public_network", :bridge => $BRIDGE_DEVICE, ip: "192.168.0.90"

  config.vm.hostname = "minecraft.local"
end
