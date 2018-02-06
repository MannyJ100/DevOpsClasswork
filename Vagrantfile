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
      app.vm.provision "chef_solo" do |chef|
          chef.add_recipe "node::default"
      end
  		
      # Sync templates folder
  		# app.vm.synced_folder "./environment/app/templates", "/home/ubuntu/templates"
  	# Provision
  		# app.vm.provision "shell", path: "environment/app/provision.sh"
 
	end

	# second box for db

	config.vm.define "db" do |db|

		db.vm.box = "ubuntu/xenial64"
		db.vm.network "private_network", ip: "192.168.10.150"
		db.hostsupdater.aliases = ["database.local"]
    db.vm.provision "chef_solo" do |chef|
         chef.add_recipe "db::default"
     end
  end
end
		# synced folder for db
		# db.vm.synced_folder "./environment/db", "/home/ubuntu/db"

		# db.vm.provision "shell", path: "environment/db/provision.sh"