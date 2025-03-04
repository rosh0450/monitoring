# grafana_alloy

This role will install and configure Grafana Alloy

## Requirements

*Operating System Requirements*

| Supported OS | Major Version | Tested on |
| ------------ | ------------- | --------- |
| Almalinux    | 8, 9          | 8.4, 8.8, 9.4 |
| Centos       | 7             | 7.5, 7.6  |
| Ubuntu       | 22            | 22.04     |

*Software Requirements*

- Python >= 3.11
- Ansible version >= 2.16.11

## Role variables

| Name                                     | Type    | Default values                                                                                        | Description                                      |
|------------------------------------------|---------|-------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| `grafana_alloy_required_packages`        | List    | ['unzip', 'libuser']                                                                                  | List of required packages to be installed        |
| `grafana_alloy_validate_certs`           | Boolean | true                                                                                                  | If false, SSL certificates will not be validated |
| `grafana_alloy_version`                  | String  | 1.6.1                                                                                                 | Version of Grafana Alloy to install              |
| `grafana_alloy_pkg_url`                  | String  | https://github.com/grafana/alloy/releases/download/v{{ grafana_alloy_version }}/alloy-linux-amd64.zip | URL to download Grafana Alloy pkg                |
| `grafana_alloy_checksum_url`             | String  | https://github.com/grafana/alloy/releases/download/v{{ grafana_alloy_version }}/SHA256SUMS            | URL to download SHA256SUMS file                  |
| `grafana_alloy_install_dir`              | String  | /opt/grafana/alloy                                                                                    | Path for Grafana Alloy files and directories     |
| `grafana_alloy_user`                     | String  | grafana-alloy                                                                                         | User to run Grafana Alloy service                |
| `grafana_alloy_group`                    | String  | grafana-alloy                                                                                         | Group to run Grafana Alloy service               |
| `grafana_alloy_supported_os`             | Dict    | AlmaLinux, CentOS, Ubuntu versions                                                                    | Supported operating systems                      |
| `grafana_alloy_prechecks`                | Boolean | true                                                                                                  | Perform prechecks                                |
| `grafana_alloy_install`                  | Boolean | true                                                                                                  | Perform installation                             |
| `grafana_alloy_configure`                | Boolean | true                                                                                                  | Perform configuration                            |
| `grafana_alloy_uninstall`                | Boolean | false                                                                                                 | Perform uninstallation                           |
| `grafana_alloy_http_port`                | Number  | 9090                                                                                                  | HTTP server listen port                          |
| `grafana_alloy_integration`              | Dict    | {}                                                                                                    | Configurations for Grafana Alloy integrations    |
| `grafana_alloy_remote_write`             | Dict    | {}                                                                                                    | Configurations for Grafana Alloy remote write    |
| `grafana_alloy_scrape`                   | Dict    | {}                                                                                                    | Configurations for Grafana Alloy scraping        |
| `grafana_alloy_prometheus_scrape_config` | Dict    | {}                                                                                                    | Prometheus scrape config for Grafana Alloy       |
| `grafana_alloy_args`                     | String  | ""                                                                                                    | Extra arguments for Grafana Alloy                |
| `grafana_alloy_loglevel`                 | String  | info                                                                                                  | Log level for Grafana Alloy service              |

## Dependencies

None

## Example playbook

```
- hosts: servers
  roles:
    - role: monitoring.grafana.grafana_alloy
      vars:
        grafana_alloy_integration:
          node_exporter:
            disable_collectors: ["mdadm"]
```
