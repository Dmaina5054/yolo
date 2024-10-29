Role Name
=========
This role will 
- install dependencies that are common between vms
- clone code repository for all guests
- setup docker and docker compose for all guests

Requirements
------------



Role Variables
--------------

- docker_compose_version: "1.29.2"
- docker_user: "docker"
- vagrant_user: "ansible"
- min_ansible_version: "2.29.7"
- github_repo_url: "https://github.com/Dmaina5054/yolo"
- key_file_location: "/home/vagrant/.ssh/id_ed25519"
- git_clone_directory: "/home/vagrant/yolo"

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

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
