﻿# Robbie's First Pass at adapting a Vagrant image

## About

This repository manages Robbie's development virtual server. It has a number of
tools that Robbie enforces that others use to help build Drupal sites. Drush is included
as well as Drush Fetcher which is a tool used to sync copies of Drupal sites between
environments. There are also other useful features such as a solr server for
Drupal search integration.

## Installation

You must have [Vagrant](http://vagrantup.com) and [VirtualBox](https://www.virtualbox.org/) installed first.

This repository has several git submodules that you will need before the
installation will complete. Run "git submodule update --init" from within this
directory to get the required sub-projects.

Once the repositories have been downloaded run "vagrant up" from within this
directory. This will build the virtual server and provision it. You can change
some settings such as the IP address of the server and the server's name in the
VagrantFile.

After the server has been built it is a good idea to update the packages. Log in
to the server over SSH. The username and password are both "vagrant". Run
"sudo apt-get update && sudo apt-get upgrade" to update the server's packages.
When this is completed back on the command line in this directory run
"vagrant provision" to finish the build.

You should now have a working Virtual Server.

The default server hostname is `local` and the default IP is `33.33.33.40`.

## Issues

Vagrant tries to mount a shared NFS directory to the host machine (the physical
computer). This has been known to fail in some cases. If you receive errors
about a failed mount remove the virtual machine with "vagrant destroy" then
comment out the line that sets this up in the VagrantFile by placing a # at the
beginning of the line:

    #config.vm.share_folder("web", "/var/www", "www", :nfs => true)
    
Liberated from [Zivtech](https://github.com/zivtech/vagrant-development-vm) Thanks friends :-) 
