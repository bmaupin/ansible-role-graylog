Ansible role for Graylog

**Note:** If you just need to spin up a local Graylog instance for development or testing, you may want to consider
using Docker Compose instead: [https://github.com/Graylog2/docker-compose/](https://github.com/Graylog2/docker-compose/)

### Features

- Installs and configures dependencies for Graylog (Java, MongoDB, Elasticsearch)
- Installs Graylog 3.x
- Configures Graylog web interface to run on 0.0.0.0


### Requirements

- CentOS/RHEL 6+ ([http://docs.graylog.org/en/latest/pages/installation/operating_system_packages.html](http://docs.graylog.org/en/latest/pages/installation/operating_system_packages.html))


### Instructions

Include the role and define any variables as described below


### Variables

- `graylog_password_secret` (required)
    - Graylog password_secret (see https://docs.graylog.org/en/3.0/pages/getting_started/configure.html#general-properties)
- `graylog_root_password_sha2` (required)
    - Graylog root_password_sha2 (see https://docs.graylog.org/en/3.0/pages/getting_started/configure.html#general-properties)
- `proxy_env`
    - Proxy configuration (see https://docs.ansible.com/ansible/latest/user_guide/playbooks_environment.html)


### Sample playbook

    - hosts: graylog-servers
      roles:
        - graylog
      vars:
        graylog_password_secret: "{{ vault_graylog_password_secret }}"
        graylog_root_password_sha2: "{{ vault_graylog_root_password_sha2 }}"
