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

This role is working at least on **Ubuntu Xenial (16.04) and Yakkety (16.10)**.
In the ansible manifest only Xenial is listed since Yakkety is not recognized
yet.

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
    compose_file_startup: path/to/docker-compose-file/for/initial/startup.yml
```

License
-------

Apache 2.0 (see LICENSE file)
