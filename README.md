# Assorted Ansible scripts ('roles')

- Swap file configuration (e.g. for DigitalOcean)

- Ruby on Rails via nginx + passenger

- Source code deployment from GitHub (public repos + private repos)

- Nginx + SSL

- JRE via OpenJDK

- Jetty servlet container

- Play framework (OBSOLETE)


## Warning

Some of these scripts include code or paths from specific projects and need to be modified to be parametrised.
These are included for reference.

## Requirements

- Server(s) running Debian-based Linux distribution (tested mostly on Ubuntu, but should work on Debian as well)

- Root (or sudo) access to those servers via password. Will not work out of the box with key-based authentication, 
  see http://docs.ansible.com/intro_getting_started.html

- Control machine running Linux or OS X

- Ansible v1.7.1 and up (http://ansible.com)

## Notes (and TODO)

- Host key checking is disabled by default, edit ansible.cfg to enable it if you're paranoid.

- Designed for manually provisioned VMs, will need additional work to use with automated provisioning.

- Currently queries the password for deploy user from command-line, this needs to be changed to
  passwordless sudo because some operations hang (e.g. rvm trying to install C/C++ compiler)

## Usage

1. Generate a key pair and a password for the deployment user. See roles/deploy-user/files/README.md
   Make sure that this directory contains deploy_id_rsa, deploy_id_rsa.pub, deploy_password

2. Edit 'init-hosts' and add the new server(s)

3. Run 'digitalocean-init'

  (designed for manually provisioned instances on DigitalOcean, edit as required for a different provider)

  This will ask you for your root password and create a new user account called 'deploy'. This user will
  have full sudo access and will be used by all deployment scripts. This only needs to be done once for 
  every new server (the deloy user's credentials will be shared across servers).

  This will also add a swapfile (DigitalOcean VMs have no swap enabled by default).

4. See example playbooks for specific installation examples.
