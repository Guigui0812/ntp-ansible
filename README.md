NTP Role
=========

This role installs and configures chrony as either a client or a server. It comes with basic security settings to prevent abuse of the NTP server.

Requirements
------------

- [Ansible](https://www.ansible.com/) - Ansible must be installed to execute the playbook.

Role Variables
--------------

| Variable | Description | Default |
|----------|-------------|---------|
| `ntp_servers` | A list of NTP servers to sync with | `time.cloudflare.com`, `time.google.com`, `time.facebook.com` |
| `ntp_logdir` | The directory to store chrony logs | `/var/log/chrony` |
| `ntp_driftfile` | The file to store the drift of the system clock (client only) | `/var/lib/chrony/drift` |
| `ntp_stratum` | The stratum of the NTP server (server only) | `10` |
| `ntp_allow_subnets` | A list of subnets that are allowed to sync with the NTP server (server only) | `192.168.0.0/24` |

Dependencies
------------

None.

Example Playbook
----------------

File `inventory/hosts_vars/host` for server example :

```
ntp_flavor: "server"
ntp_servers:
  - time.cloudflare.com
  - time.google.com
  - time.apple.com
  - time.facebook.com
```

Playbook example : 
```
- hosts: servers
  roles:
    - ntp
```

License
-------

BSD
