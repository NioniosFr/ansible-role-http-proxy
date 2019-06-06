Ansible Role: HTTP Proxy
=========

An ansible role to configure a proxy server for a Linux based system.

Requirements
------------

The role targets Linux systems which respect and load `/etc/profile.d/*.sh` files.

It configures a profile file for the HTTP proxy environment variables.
Optionally, a `/etc/sudoers.d/keep_proxy` file will also be created to sustain the variable on `sudo` commands.

Role Variables
--------------

No variable is required if you follow the [Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_environment.html)
closely.
If a `proxy_env` variable list is defined, with the respected `http_*` variables, the role will set these automatically.

Optional:

```yaml
# proxy_http_proxy: ''
# proxy_https_proxy: ''
# proxy_no_proxy: ''
proxy_keep_when_sudo: true # Whether to keep the proxy variables when switching users with sudo
```

If any of the above `proxy_http*` variables is set, the proxy configuration will be applied.
Otherwise the configuration will be removed.

Dependencies
------------

None

Example Playbook
----------------

```yaml
    - hosts: localhost
      roles:
        - role: nioniosfr.http_proxy # Setup proxy config
          vars:
            proxy_http_proxy: "http://my-proxy:3128"
            proxy_https_proxy: "http://my-proxy:3129"
            proxy_no_proxy: "my-net.net" # Completely Optional

    - hosts: localhost
      roles:
        - role: nioniosfr.http_proxy # Cleanup proxy config or do nothing
```

For extensive examples, see the `tests` folder.

License
-------

MIT

Author Information
------------------

[NioniosFr](https://github.com/NioniosFr)
