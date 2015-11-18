parallels-clone
===============

This role can be used to clone Parallels Desktop VMs.

Templates
---------

To clone a new VM in Parallels you need at least one template VM, which is the origin VM for your new cloned VM. Ansible will clone this VM via Parallels `prlctl` command-line utility and sets a fixed IP address in Parallels internal DHCP server (IP reservation).

Ansible will also make sure that the VM name can be looked up on your Mac OS X host (via /etc/hosts) and that the hostname of the cloned VM is updated accordingly.

Requirements
------------

* Parallels Desktop 10+
* `prlctl` - the Parallels CLI tool
* `sudo` access on Mac OS X for the update of the `/etc/hosts` file

Role Variables
--------------

### IP Address (mandatory)

You've to define the IP address of your VM by setting the `ip` parameter, for example:

```yaml
ip: 10.99.0.123
```

Please note that it makes sense to set the `ip` parameter directly in the `hosts` file or any other inventory source.

### Template (mandatory)

You've to define the template (source) VM by setting the `template` parameter, for example:

```yaml
template: debian
```

Please note that it makes sense to set the `template` parameter directly in the `hosts` file or any other inventory source.

### Parallels CLI tool (optional)

To clone a VM, Ansible will use Parallels `prlctl` tool.
By default the tool is located in `/Applications/Parallels\ Desktop.app/Contents/MacOS/prlctl`, but you can overwrite that by settings the `prlctl` variable:

```yaml
prlctl: <new path to prlctl>
```

### IP CIDR mask (optional)

The CIDR mask for the IP address is by default set to `24`, but you can overwrite that by set.
You can overwrite that by setting the `cidr_mask` variable:

```yaml
cidr_mask: <new CIDR mask>
```

Dependencies
------------

None.

Example playbook
----------------

```yaml
- hosts: server
  roles:
    - { role: parallels_clone, ip: 10.99.123, template: debian }
```
