# ansible-role-host-server

An Ansible role to provision and configure a host server.

## Description

The role defines two tasks, namely

* `kvm.yml`: configure a [Kernel Virtual Machine](https://www.linux-kvm.org/)
([libvirt](https://libvirt.org/)) host server
* `lxd.yml`: configure a [Linux Containers](https://github.com/canonical/lxd/)
host server

I'd suggest running it aginst a newly installed system whose network/user
account settings can be configured in `vars/main.yml`.

The playbook creates a bridged interface and reconfigures the pysical one
before providing virtualization support.

## Compatibility

Tested under CentOS 7 and AlmaLinux 9.

## Dependencies

[`community.general`](https://docs.ansible.com/ansible/latest/collections/community/general/) Ansible collection (for `nmcli`):

```
ansible-galaxy collection install community.general
```

## Example playbook

```yaml
---
- hosts: host-server
  tasks:
  - import_role:
    name: ansible-role-host-server
    tasks_from: kvm.yml
```

## Related projects

Automating the host server configuration was useful during the development of
these Terraform projects:

* [`terraform-kvm`](https://github.com/jordibalcellss/terraform-kvm)
* [`terraform-lxd`](https://github.com/jordibalcellss/terraform-lxd)
