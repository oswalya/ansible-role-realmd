Realmd
==========
- [Introduction](#introduction)
- [Variables](#variables)
- [Usage](#usage)

# Introduction
Ansible role to add Windows Active Directory Authentification to Linux clients.

Following things will be done:
- Install required packages
- Configure system to use Windows Active Directory for Authentification
- Configure SSSD
- Ensure required services are running

Supported OS:
- RedHat/CentOS

# Variables
| Name | Description | Default |
|:-----|:------------|:--------|
| realmd_package_state | Package state to ensure | present |
| realmd_package_names | List of packages to install | Depends on Disribution |
| realmd_realm | Realm name to join. Must be in uppercase | EXAMPLE.COM |
| realmd_username | User used to join the system to the domain | Administrator |
| realmd_password | Password of user used to join the system to the domain | password |
| realmd_homedir | Home of directory of domain users | /home/%u |
| realmd_use_fully_qualified_names | String to define if users must use fully qualified domain names to login. If set to 'True' one must use <username>@<domain> to login. If 'False' only <username> is enough. Value must be a string!| 'False'

# Usage
```yaml
---
- hosts: workstation
  become: true
  vars:
    realmd_realm: EXAMPLE.COM
    realmd_username: maxmuster
    realmd_password: topsecret
  roles:
  - role: realmd
```

# Author
[Bjoern Jessen-Noak](mailto:oswalya@gmail.com)
