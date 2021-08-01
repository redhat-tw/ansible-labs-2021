# Ansible Labs
This repo contains many playbooks for showing you how to use Ansible and Ansible Tower.

## What you’ll need

* 4 CPUs or more.
* 16GB of free memory.
* 100GB of free disk space.
* Internet connection.
* Vagrant v2.2.0+.
* VirtualBox v6.1.0+.

## Set up development env
The section will show you how to set up development env through Vagrant.

### Ansible Tower
For AWX Vagrant we need to install AWX by setup script:

```sh
$ vagrant up
$ vagrant ssh
```

> Access Ansible Tower dashboard from [172.16.33.10](https:\\172.16.33.10)。

Other nodes please refer to the following: 

- [Linux](linux/README.md)
- [Windows](windows/README.md)
