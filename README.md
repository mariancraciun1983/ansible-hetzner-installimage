<h1 align="center">Hetzner Installimage Ansible Role</h1>


<div align="center">
  <a href="https://travis-ci.org/mariancraciun1983/ansible-hetzner-installimage">
    <img src="https://travis-ci.org/mariancraciun1983/ansible-hetzner-installimage.svg?branch=master" alt="Build Status" />
  </a>
  <a href="https://galaxy.ansible.com/mariancraciun1983/ansible-hetzner-installimage">
    <img src="https://img.shields.io/badge/ansible--galaxy-haproxy-blue.svg" alt="Ansible Galaxy" />
  </a>
  <a href="https://opensource.org/licenses/MIT">
    <img src="https://img.shields.io/badge/License-MIT-blue.svg" alt="MIT License" />
  </a>
</div>


Ansible role for re-installing OS on [Hetzner dedicated servers](https://www.hetzner.com/dedicated-rootserver) using [Hetzner APIs](https://robot.your-server.de/doc/webservice/en.html) and [InstallImage](https://docs.hetzner.com/robot/dedicated-server/operating-systems/installimage/)


## Introduction

Hetzner offers dedicated servers ranging from cheap i7, AMD to high performance Xeon processors. They offer a rescue system for reinstalling the OS, configure the basics like partitions, RAID and SSH keys. A webservice can be used to reboot servers, activate the rescue system, perform network setup and many others operations.

## Requirements & Dependencies

### Hetzner
- dedicated [Hetzner Root server](https://www.hetzner.com/dedicated-rootserver)
- SSH key added to the [Key Management](https://robot.your-server.de/key/index)
- WebService activated with user/pass (https://robot.your-server.de/preferences/index)

PS: make sure that you the default port 22 is accesible from your machine (ex: whitelisted in the hetzner firewall)

### Ansible
This role was tested against Ansible version 2.7 2.8 2.9 2.10


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

```ini
# inventory
[servers]
1.2.3.4 hostname=node1
node2.example.com
```

```yaml
# playbook.yml
- hosts: servers
  roles:
    - mariancraciun1983.hetzner_install_image
```

```bash
# install the role
ansible-galaxy install mariancraciun1983.hetzner_install_image
```

```bash
# run the playbook
ansible-playbook -i inventory playbook.yml
```

## License
MIT License