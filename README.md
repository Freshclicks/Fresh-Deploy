# LEMP (Nginx, MariaDB, php7.1) Deployment Playbook for Ubuntu 16.04

## Introduction

This Ansible Playbook is designed to setup a highly optimized environment on a production server without the configuration hassle. I modified and mixed several deployment scripts to get create the optimized system ready for Wordpress installs.
It includes the ability to install multiple hostnames on a single server.

I recommend using Digital Ocean servers, and if you use this link https://m.do.co/c/a42a15eb0b65 you'll get $10 in credit and I'll get a little something too. Win - Win!

*Note: Please review this playbook to ensure I'm not installing malicious software.*

This Playbook will setup:

- **MariaDB** (A drop in replacement for MySQL)
- **PHP** (Native php7.1.2 from the official Ubuntu 16.04 repo)
- **Nginx**
- **Memcached**
- **Fail2Ban**
- **Ferm** (Firewall iptable management)
- **sSMTP**
- **WP-CLI**

#### This playbook will run on Ubuntu 16.04 LTS

## Installation

1. SSH onto a newly created server
1.5. Add necessary Apt package (if not already installed) with `sudo apt-get install software-properties-common`
2. Add Ansible with `sudo add-apt-repository ppa:ansible/ansible`
3. Update Apt with `sudo apt-get update && sudo apt-get dist-upgrade`
4. Install Git and Ansible with `sudo apt-get install ansible git`
5. Clone this repository with `git clone https://github.com/Freshclicks/fresh-deploy.git`
6. Move into `cd fresh-deploy`
7. Edit the `sudo nano hosts` file and your host name. If you have more than one website that you want to install on this server add each on a new line.
8. Edit the `sudo nano group_vars/all` file and include your SMTP settings.
9. Run Ansible with `sudo ansible-playbook -i hosts playbook.yml -c local`. If you have any errors please open a new issue in this repository. (It may fail the first time. Just run it again and you should be good to go)
10. Remove the cloned git directory from your server with `rm -rf fresh-deploy/`
11. Run `/usr/bin/mysql_secure_installation` to secure MariaDB. Your root password will be root by default
12. Restart Nginx with: `sudo service nginx restart`
13. You're good to go!

## Issues

Please report any issues through GitHub or email me at lary@freshclicks.net and I'll do my best to get back to you!
