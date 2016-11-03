Redis
=====

[![Build Status](https://travis-ci.org/jebovic/ansible-redis.svg?branch=master)](https://travis-ci.org/jebovic/ansible-redis) [![Ansible Galaxy](https://img.shields.io/badge/galaxy-jebovic.redis-blue.svg?style=flat)](https://galaxy.ansible.com/jebovic/redis)

Install and configure Redis

This role is a part of my [OPS project](https://github.com/jebovic/ops), follow this link to see it in action. OPS provides a lot of stuff, like a vagrant file for development VMs, playbooks for roles orchestration, inventory files, examples for roles configuration, ansible configuration file, and many more.

Role Variables
--------------

```yaml
# Redis basic configuration
redis_packages:
  - redis-server
redis_daemon: redis-server
redis_conf_path: /etc/redis/redis.conf
redis_port: 6379
redis_bind_interface: 127.0.0.1
redis_unixsocket: ''
redis_timeout: 300
redis_databases: 16

# Redis service configuration
redis_loglevel: "notice"
redis_logfile: /var/log/redis/redis-server.log

# Redis custom configuration
redis_save:
  - 900 1
  - 300 10
  - 60 10000
redis_rdbcompression: "yes"
redis_dbfilename: dump.rdb
redis_dbdir: /var/lib/redis
redis_maxmemory: 0
redis_maxmemory_policy: "noeviction"
redis_maxmemory_samples: 5
redis_appendonly: "no"
redis_appendfsync: "everysec"

# Add extra include files for local configuration/overrides.
redis_includes: []
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: jebovic.redis }
```

Tags
----

* redis_config : only update config and restart service

License
-------

MIT

Author Information
------------------

Jérémy Baumgarth https://github.com/jebovic
