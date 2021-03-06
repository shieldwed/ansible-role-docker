# shieldwed.docker

Ansible role to install, configure and manage docker and docker services.
This includes docker-compose >= 0.16.0 for version 2 manifests.

Requirements
------------

shieldwed.docker is currently only usable on systems with systemd service
manager. This could be changed easily if the destined service manager allows to
issue different commands for start up and tear down and the required files
can be generated from the variables described below.

Compatibility
-------------

This role has been working for all releases from `xenial` up to `disco` so far
and has been used on each of them, although compatibility is only really tested
with the latest release. Additionally support for Archlinux is now added too.

Role Variables
--------------

| variable | default | description |
|----------|---------|-------------|
| docker_compose_state | present | state of docker-compose in case docker only installation desired |
| docker_service_enabled | yes | whether docker service should be enabled for startup |
| docker_service_state | started | if docker service should be started (for docker only installations) |
| docker_compose_service_directory | /etc/docker-services | directory for docker compose files |


Example Playbook
----------------
```yaml
- hosts: all
  roles:
     - shieldwed.docker
```
Variables:
```yaml
docker_compose_services:
  - name: service-name
    description: service description for systemd
    compose_file: path/to/docker-compose-file.yml
    service_config: path/to/ansible-playbook-file.yml
    systemd_service_name: systemd-unit-name
```

The variable `compose_file_startup` doesn't exist anymore. Instead the variable
`docker_compose_file_initial` has been added at task level and resolves to
`true` for when the `compose_file` is rendered for the initial run and to
`false` for all subsequent runs. This allows to maintain the docker-compose
states to be kept in the same template without being required to maintain
two different templates with mostly the same content.

The variable `service_config` allows to include a play book containing
steps to be run after the initial `compose_file` has been place on
the destination system but before it is started for the first time.
This is a good opportunity to copy further required files, install packages or
change configuration files.

`systemd_service_name` specifies the name the systemd unit is saved as.
This defaults to `docker-${name}`.

License
-------

Apache 2.0 (see LICENSE file)
