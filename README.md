# Ansible Role: Tyk

[![Build Status](https://travis-ci.org/Sunnepah/ansible-role-tyk.svg?branch=master)](https://travis-ci.org/Sunnepah/ansible-role-tyk)

Installs and configures Tyk API Gateway on Debian/Ubuntu servers.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `vars/main.yml`):

	tyk_gateway_port: 8080

Tyk listening port

	tyk_secret: secured-tyk-node-secret

Tyk node secret

	hash_keys: true

Whether keys should be hashed

	tyk_dashboard_url: "http://my-tyk-instance.dev"

Tyk dashboard url

	tyk_dashboard_port: 3000

Tyk dashboard listening port

	tyk_dashboard_domain: "my-tyk-instance.dev"

Tyk dashboard domain

	redishost: localhost

Redis address

	redisport: 6379

Redis listening port

	mongodb_url: "mongodb://127.0.0.1/tyk_analytics"

MongoDB url

	license_key: node license

Get one from https://tyk.io/tyk-professional-licenses/

## Dependencies

None.

## Example Playbook

    - hosts: servers
      vars_files:
      	- vars/main.yml
      roles:
         - { role: Sunnepah.tyk}

*Inside `vars/main.yml`*:

    tyk_gateway_port: 8080
	tyk_secret: secured-tyk-node-secret
	hash_keys: true

	tyk_dashboard_url: "http://my-tyk-instance.dev"
	tyk_dashboard_port: 3000
	tyk_dashboard_domain: "my-tyk-instance.dev"

	redishost: localhost
	redisport: 6379

	mongodb_url: "mongodb://127.0.0.1/tyk_analytics"

	# Get one from https://tyk.io/tyk-professional-licenses/
	license_key: node license

*NOTE
	
	Once the playbook runs successfully login to the VM and bootsrap a user
	$ vagrant ssh
	$ /opt/tyk-dashboard/install/bootstrap.sh my-tyk-instance.dev

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Sunday Ayandokun](https://github.com/Sunnepah).
