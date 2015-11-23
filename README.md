# Graphite deployment

This build is for the [Introduction to Tracking Statistics on Servers](https://www.digitalocean.com/community/tutorials/an-introduction-to-tracking-statistics-with-graphite-statsd-and-collectd) tutorial by Justin Ellingwood.

The build uses [Ansible](https://docs.ansible.com) to configure a virtual machine, created via [Vagrant](https://vagrantup.com).

# Disclaimer

This is only an example usage. Feel free to pick it apart and reuse as you see fit.

I think it goes without saying, but just in case... Use this at your own risk.

# Usage

The following instructions create an Ubuntu 14.04 LTS server with graphite installed on it.

**Note**, at the moment, I'm using OS X. Adapt the instructions to meet your own needs. :)

## Prerequisites

1. You'll need Python (>=2.7) with Ansible installed.

   ```bash
   brew install python
   pip install ansible
   ```

   I'd recommend you use virtualenv, but that's outside the scope of these instructions.

2. You'll also need to install Vagrant, which can be downloaded at [vagrantup.com](https://www.vagrantup.com/).

## Installation

Once you've got vagrant and ansible installed:

1. Checkout this repo: ``git clone https://github.com/pumazi/graphite-deploy.git``
2. Install ansible-galaxy packages (from the root of this project): ``ansible-galaxy install -r requirements.yml``
3. Flip the switch: ``vagrant up``

If you make any changes to the playbook, you can push those using: ``vagrant provision``

## Viewing the service

Graphite will be running at [http://192.168.17.34](http://192.168.17.34) and statsd will be running at the same address on the default port.

# Changes and omissions

I've done some things different from the tutorial. It's likely easier to use apache2 with graphite on debian, since it the configuration files already exist. It's been some time since I've used apache, so I've choosen to use nginx instead.

Collectd is not configured to collect stats from nginx.
