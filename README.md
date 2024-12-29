Ansible Role: pve_hookscript
=========

This Ansible role automates the configuration of Proxmox Virtual Environment (PVE) for managing hook scripts. It ensures compatibility with Debian systems, installs required packages, validates Proxmox VE version, and deploys custom hook scripts to designated storage paths.

```
    git clone https://github.com/lorephoenix/ansible-role-pve_hookscript pve_hookscript
```

Requirements
------------

- Ansible 2.11 or higher
- Proxmox VE 8.x or higher
- The target machine must be Debian-based
- `pvesh` command-line utility must be available on the Proxmox server

Role Variables
--------------

The following variables can be customized to suit your environment. Default values are defined in `defaults/main.yml`

| Variable               | Value                    | Data Type | Required| Description                                                |
|------------------------|--------------------------|---------|-----------|------------------------------------------------------------|
| `hookscript_username`  | `ansible`                | String  | Mandatory | Name of user                                               |
| `hookscript_groupname` | `ansible`                | String  | Mandatory | Name of group                                              |
| `hookscript_noproxy`   | `localhost,127.0.0.1/8`  | String  | Optional  | Lists domains or IP addresses that should bypass the proxy.|
| `hookscript_proxy`     | `http://localhost:8080`  | String  | Optional  | Specifies the HTTP proxy URL for outbound connections.     |
| `hookscript_pubkey`    | `undefined`              | String  | Optional  | Define a SSH public key into username/.ssh/authoried_keys. |
| `hookscript_use_proxy` | `false`                  | Boolean | Optional  | Flag to enable/disable proxy usage.                        |

Dependencies
------------

None

Example Playbook
----------------

Here’s an example of how to use this role:

```yaml
---
- name: (playbook) | Proxmox upload hookscript
  hosts: localhost
  roles:
    - role: pve_hookscript
      vars:
        hookscript_username: "ansible"
        hookscript_groupname: "ansible"
        hookscript_noproxy: "localhost,127.0.0.1/8,172.16.0/12,192.168.0.0/16"
        hookscript_proxy: "http://localhost:8081"
        hookscript_use_proxy: false
        hookscript_pubkey: null
````

License
-------

MIT

Author Information
------------------

- Christophe Vermeren | [GitHub](https://github.com/lorephoenix) | [Facebook](https://www.facebook.com/cvermeren)
