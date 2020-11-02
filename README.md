# Hetzner Installimage Ansible Role


[![Build Status](https://travis-ci.org/mariancraciun1983/ansible-hetzner-installimage.svg?branch=master)](https://travis-ci.org/mariancraciun1983/ansible-hetzner-installimage)


Ansible role for re-installing OS on [Hetzner dedicated servers](https://www.hetzner.com/dedicated-rootserver) using [Hetzner APIs](https://robot.your-server.de/doc/webservice/en.html) and [InstallImage](https://docs.hetzner.com/robot/dedicated-server/operating-systems/installimage/)


## Introduction

Hetzner offers dedicated servers ranging from cheap i7, AMD to high performance Xeon processors. They offer a rescue system for reinstalling the OS, configure the basics like partitions, RAID and SSH keys. A webservice can be used to reboot servers, activate the rescue system, perform network setup and many others operations.

## Requirements & Dependencies

### Hetzner
- [Hetzner server](https://www.hetzner.com/dedicated-rootserver)
- SSH key added to the [Key Management](https://robot.your-server.de/key/index)
- WebService activated with user/pass (https://robot.your-server.de/preferences/index)

PS: make sure that you the default port 22 is accesible from your machine (ex: )

### Ansible
This role was tested against Ansible version 2.2 2.4 2.7 2.8 2.9


## Variables

For a full reference of the configuration variables checl [defaults/main.yml](./defaults/main.yml).
The required variables are:
```yaml
robotws_user: username
robotws_password: password

image:
  distro: ubuntu
  version: 20.04
```

## Example

inventory
```ini
[servers]
1.2.3.4 hostname=node1
node2.example.com
```

playbook.yml
```yaml
- hosts: servers
  roles:
    - mcraciun.hetzner_install_image
```

install the role
```bash
ansible-galaxy install mcraciun.hetzner_install_image
```

run the playbook
```bash
ansible-playbook -i inventory playbook.yml
```

## License
MIT License