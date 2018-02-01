# -*- mode: ruby -*-
# vi: set ft=ruby :
# Install required plugins:
required_plugins = ["vagrant-hostsupdater"]
required_plugins.each do |plugin|
    exec "vagrant plugin install #{plugin}" unless Vagrant.has_plugin? plugin
end

Vagrant.configure("2") do |config|

	config.vm.define "app" do |app|
 
  		app.vm.box = "ubuntu/xenial64"
  		app.vm.network "private_network", ip: "192.168.10.100"
  		app.hostsupdater.aliases = ["dev.local"]

  	#Synced app folder
  		app.vm.synced_folder "app", "/home/ubuntu/app"
  
  	# Provision
  		app.vm.provision "shell", path: "environment/app/provision.sh"
  
	end

	# second box for db

	config.vm.define "db" do |db|

		db.vm.box = "ubuntu/xenial64"
		db.vm.network "private_network", ip: "192.168.10.150"
		db.hostsupdater.aliases = ["database.local"]

		# synced folder for db
		db.vm.synced_folder "./environment/db", "/home/ubuntu/db"

		db.vm.provision "shell", path: "environment/db/provision.sh"

		# db.vm.provider :virtualbox do |v|
  #    	v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  #    	v.customize ["modifyvm", :id, "--memory", 512]
  #    	v.customize ["modifyvm", :id, "--name", "db"]
  #  		end
	end
end