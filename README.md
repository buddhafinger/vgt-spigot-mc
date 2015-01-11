
Spigot Minecraft in Vagrant instance.

IMPORTANT NOTES:
Vagrant file contains my local netork IP range and interface, you will need to update for local network and interface.

Make sure you take backups of persistent_files directory (linked to /opt/mc) before making any major changes..

This is for local development and internal use, not recommended for production/public servers.

When using port forwarding to expose the server to a public network, forward the traffic on 25565 to the IP address of your local host machine NOT the virtualbox instance.


What do I need to actually play minecraft on this server once it's running?

- A PC with a 64bit O/S, if your OS is not 64 bit you will need to update the vagrant file to use a 32bit Ubuntu instance.

- Virtualbox installed (ideally recent and up to date)

- Vagrant (again latest version prefered) 

- A copy of Minecraft and working Minecraft account.


INSTALL: 

Short version for those with experience using Virtualbox, Vagrant and general system administration.

- Download repo

- Update Vagrant file for local network interface and network range.

- Vagrant up 

- SSH to server as user vagrant password vagrant and ensure the spigot service is running and if not restart it (sudo service spitgot (status|stop|start|restart)

- Play.




EXTENDED INSTALLED NOTE: 

- Download and install Virtualbox  https://www.virtualbox.org/wiki/Downloads - VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use
- Download and install Vagrant - https://www.vagrantup.com/downloads.html - Vagrant is computer software for creating and configuring virtual development environments. It can be seen as a wrapper around virtualization software such as VirtualBox, KVM, VMware and around configuration management software such as Ansible, Chef, Salt or Puppet.

- Clone this repo 

- Enter into the repo dir and update the file named Vagrantfile to be compatible with your local enviroment. This will generally only require updating the line starting with "$BRIDGE_DEVICE =" to make your local network interface alias.  On boot if the alias does not match it will prompt you to select one of your available aliases.

You may also need to modify the IP address in the config.vm.network line to match your intenral network IP address range (obviously ensuring any specfied IP address is available).  

Once you've updated the file with your local settings, open a command prompt, enter into the vgt-spigot-mc folder run the command 'vagrant up'.

Connect to the instance via ssh as user 'vagrant' with the password vagrant (you should change this) and ensure the spigot jvm is running.  

To manage the spigot service:  'sudo service spigot status' (check status)  'sudo service spigot start' (startup spitgot)  'sudo service spitgot restart' (restart) and 'sudo service spitgot stop' (stop).

Initial load will unpack and create the required files to run the server under /opt/mc.

Once the server is up and running

Play.



Notes: THIS IS WORK IN PROGRESS / EARLY STAGES.

CREDITS:

Forked from Stephen Woods repo: https://github.com/stephen-mw/vagrant_minecraft - which uses standard MC.

More info here: http://www.heystephenwood.com/2014/09/vagrant-minecraft.html

Massive shout to Spigot team - great crew.


TO DO:
Still getting my head around the basics - pluggins, building, permissions, commands, ops etc.

Aim to maintain a 'vanilla' flavor of this repo.

Create branches for a pre-modded version, World Edit, Essentials etc.

Add in more useful commands and some example configs for pluggins.

Lock down permissions on server - a little too open for my liking.

Set spigot server to start on boot once it's installed.  Doesn't appear to be workign at the moment.
