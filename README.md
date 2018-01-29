# Devops

## Starter Guide for Virtual Machines

### Step 1: Installation
Vagrant starts and controls virtual machines for you using VirtualBox. This project has been setup to create two virtual machines in a 2 tier structure. One for the app and another for the database. It will install all the necessary sofware on both. To use this setup you need to install VirtualBox, Vagrant and Chef for your machine.

-  [Virtual Box](https://www.virtualbox.org/wiki/Downloads) 
-  [Vagrant](https://www.vagrantup.com/downloads.html)
-  [ChefDK](https://downloads.chef.io/chefdk)

### Step 2: Documentation

Create a folder for your app/repository in the terminal. Move to that folder. You can clone the repository from GITHUB here onto your terminal (git clone "": [DevOps](https://github.com/MannyJ100/DevOpsClasswork)

### Step 3: Initiating startup

Enter your folder or directory.
To start the machine type:

1. vagrant up 

Then to access the Ubuntu CLI, type:

1. vagrant ssh

### Step 4: Update sources list and install nginx from Virtual Machine:

1. sudo apt-get update -y
2. sudo apt-get install nginx -y

### Step 5: Accessing the site

Access the site at: [http://dev.local/](http://dev.local/)

### Step 6: Leaving the Virtual Machine

In the Virtial machine type:

- exit

Then if you wish to save gem files or states, type into the terminal

- vagrant suspend 

if you wish to destroy the file, type into the terminal:

- vagrant destroy

