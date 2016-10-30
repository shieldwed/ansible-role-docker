# shieldwed.docker

Ansible role to install, configure and manager docker service.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

| variable | default | description |
|----------|---------|-------------|
| docker_state | present | Role variable to define the overall state of docker and its configuration. Allowed values: `present`, `absent` |

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

Apache 2.0 (see LICENSE file)

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
