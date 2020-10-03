Ansible Role: install-docker
=========

Installing latest Docker CE on Ubuntu. 

Requirements
------------

None

Role Variables
--------------

```
# defaults file for install-docker
pre_packages:
  - apt-transport-https
  - ca-certificates
  - curl
  - gnupg-agent
  - software-properties-common

packages:
  - docker-ce
  - docker-ce-cli
  - containerd.io

docker_volume_netshare_type: nfs
docker_volume_netshare_params: ""
```

```
# vars file for install-docker
docker_user: 
  - vagrant

```

Dependencies
------------

None

Example Playbook
----------------

See `tests/test.yml`

```
- hosts: all
  become: yes
  roles:
  - install-docker
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
