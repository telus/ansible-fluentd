# ansible-fluentd

[Fluentd](http://www.fluentd.org/) - An open source data collector for unified logging layer

[![Platforms](http://img.shields.io/badge/platforms-ubuntu-lightgrey.svg?style=flat)](#)

## Tunables
--------
- `fluentd_user` (string) - User to run nginx as.
- `fluentd_group` (string) - Group to run nginx as.
- `fluentd_runtime_root` (string) - Where Fluentd puts its PID files.
- `fluentd_pidfile_path` (string) - Where Fluentd writes its PID file.
- `fluentd_config_name` (string) - The name of the file fluentd will log to.
- `fluentd_config_root` (string) - Where Fluentd finds its config files.
- `fluentd_config_path` (string) - Where Fluentd finds its main config.
- `fluentd_config_include_root` (string) - Where Fluentd finds granular config files.
- `fluentd_posfile_path` (string) - Where Fluentd stores its position placeholder files.
- `fluentd_posfile_path` (string) - Where Fluentd stores its position placeholder files.
- `fluentd_sources` (list) - A list of sources (see example) for Fluentd to read from.
- `fluentd_plugins` (list) - A list of required 'fluent-plugin-pluginname' gems.
- `fluentd_elasticsearch_host` (string) - Where Fluentd sends data for Elasticsearch.
- `fluentd_influxdb_host` (string) - Where Fluentd sends data for InfluxDB.

## Dependencies
- [telusdigital.ruby](https://github.com/telusdigital/ansible-ruby/)
- [telusdigital.upstart](https://github.com/telusdigital/ansible-upstart/)

## Example Playbook
```
- hosts: servers
  roles:
    - role: telusdigital.fluentd
      fluentd_config_name: php
      fluentd_sources:
        - path: "/data/log/php.log"
          format: '^\[(?<date_time>(?<date>[^ ]*) (?<time>[^]]*)[^]]*)\] (?<notice>\w+): (?<message>.*)'
          tag: elasticsearch.php.service
        - path: "/data/log/php-slow.log
          format: '^.*'
          tag: elasticsearch.php.slow
      fluentd_plugins:
        - elasticsearch
```

## License
[Apache License, Version 2.0](https://tldrlegal.com/license/apache-license-2.0-(apache-2.0))

## Contributors
- [Chris Olstrom](https://colstrom.github.io/) | [e-mail](mailto:chris@olstrom.com) | [Twitter](https://twitter.com/ChrisOlstrom)
- [Aaron Pederson](https://aaronpederson.github.io) | [e-mail](mailto:aaronpederson@gmail.com) | [Twitter](https://twitter.com/GunFuSamurai)
- [Justin Scott](https://jvscott.net) | [e-mail](mailto:jvscott@gmail.com) | [Twitter](https://twitter.com/AKindlyOrc)
