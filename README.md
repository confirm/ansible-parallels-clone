parallels-clone
===============

This role can be used to clone a VM in Parallels via `prlctl`.

Requirements
------------

* Parallels Desktop 10+
* `prlctl` - the Parallels CLI tool

Role Variables
--------------

### Parallels CLI tool

To clone a VM, Ansible will use Parallels `prlctl` tool.  
By default the tool is located in `/Applications/Parallels\ Desktop.app/Contents/MacOS/prlctl`, but you can overwrite that by settings the `prlctl` variable:

```yaml
prlctl: <new path to prlctl>
```

### IP CIDR mask

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
    - parallels-clone
```
