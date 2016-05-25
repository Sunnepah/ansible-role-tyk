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

	tyk_dashboard_url: "http://tyk-local.com"

Tyk dashboard url

	tyk_dashboard_port: 3000

Tyk dashboard listening port

	tyk_dashboard_domain: "tyk-local.com"

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
         - { role: sunnepah.tyk}

*Inside `vars/main.yml`*:

    tyk_gateway_port: 8080
	tyk_secret: secured-tyk-node-secret
	hash_keys: true

	tyk_dashboard_url: "http://tyk-local.com"
	tyk_dashboard_port: 3000
	tyk_dashboard_domain: "tyk-local.com"

	redishost: localhost
	redisport: 6379

	mongodb_url: "mongodb://127.0.0.1/tyk_analytics"

	# Get one from https://tyk.io/tyk-professional-licenses/
	license_key: node license

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Sunday Ayandokun](https://github.com/Sunnepah).
