# Ansible Role: prometheus-ipsec-exporter

An Ansible role that installs Prometheus IPSec Exporter on Ubuntu|Debian|Redhat-based machines with systemd|Upstart|sysvinit.

## Requirements

All needed packages will be installed with this role.

## Role Variables

| Variable                               | Type   | Choices                          | Default                                                            | Comment                                                               |
|----------------------------------------|--------|----------------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------|
| prometheus_ipsec_exporter_version      | string | See [ipsec_exporter][1] releases | v0.1.2.1                                                           | Version of ipsec_exporter that will be installed.                     |
| prometheus_ipsec_exporter_release_name | string |                                  | ipsec_exporter-{{ prometheus_ipsec_exporter_version }}.linux-amd64 | Name of the binary that will be download from the [releases][1]) page |
| prometheus_ipsec_exporter_config_flags | dict   |                                  |                                                                    | Dict of key, value options to add to the start command line           |


## Dependencies

- UnderGreen.prometheus-exporters-common

## Example Playbook

```yaml
- hosts: ipsec-exporters
  roles:
    - role: alexey-medvedchikov.prometheus-ipsec-exporter
      prometheus_ipsec_exporter_version: v0.1.2.1
      prometheus_ipsec_exporter_config_flags:
        'web.listen-address': '0.0.0.0:9101'
        'collector.ipsec.conf': '/etc/ipsec.conf'
```

## License

GPLv2

[1]: https://github.com/dennisstritzke/ipsec_exporter/releases
