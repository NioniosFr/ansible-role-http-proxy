Ansible Role: HTTP Proxy
=========

An ansible role to configure a proxy server for a Linux based system.

Requirements
------------

The role targets Linux systems.

It configures the proxy environment variables for network connectivity on a linux server.

Role Variables
--------------

No variable is required if the Ansible documentation convention of `proxy_env` list is followed.

Optional:

```yaml
proxy_http_proxy: ''
proxy_https_proxy: ''
proxy_no_proxy: ''
proxy_keep_when_sudo: true # Whether to keep the proxy variables when switching users with sudo
```

If one or both of `proxy_http_proxy` and `proxy_https_proxy` are set, the proxy configuration will be applied.
If none of these are set, the proxy configuration will be removed.

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

License
-------

MIT

Author Information
------------------

[NioniosFr](https://github.com/NioniosFr)
