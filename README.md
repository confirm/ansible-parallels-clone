parallels-clone
===============

This role can be used to clone a VM in Parallels via `prlctl`.

Requirements
------------

* Parallels Desktop 10+
* `prlctl` - the Parallels CLI tool

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
