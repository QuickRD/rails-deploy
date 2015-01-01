# Rails deploy

Ansible provisioning to setup a pre-configured Ruby/Rails server that contains the following:

- Installs ruby via rbenv
- Installs node.js for asset pipeline
- Nginx + phusion passenger for serving your app
- PostgreSQL database

Simply setup a Ubuntu 14.04 VPS server with root user and password. (Recommend at least 1GB ram)

## Usage

```sh
# Copy the example vars file
$ cp vars/example.yml vars/all.yml

# Copy the example hosts file
$ cp hosts.example hosts
```

Edit `./vars/all.yml` to meet your requirements. Replace the 127.0.0.1 IP address in `./hosts` with your servers IP

```sh
# Run the initial boostrap for your server
$ ansible-playbook -i hosts rails_deploy.yml -l bootstrap --ask-pass

# Install all the things
$ ansible-playbook -i hosts rails_deploy.yml -l appservers
```

## TODO

- SSL Support
- Memcached and redis
