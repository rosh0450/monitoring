# Ansible Collection - monitoring.grafana

Ansible collection Grafana consists of roles which can be used to install, configure & manage tools provided by Grafana.

## Available roles

| Namespace | Collection | Roles | Description | Readme |
| monitoring| grafana | grafana_alloy | Role to install & configure Grafana Alloy | [monitoring.grafana.grafana_alloy](roles/grafana_alloy/README.md)

## Install Grafana collection via command line

```
$ ansible-galaxy collection install git@github.com:rosh0450/monitoring.git#grafana
```

## Install Grafana collection via `requirements.yaml`

```
# requirements.yaml
---
collections:
  - name: monitoring
    source: ssh://git@github.com:rosh0450/monitoring.git#grafana
    type: git
```

```
$ ansible-galaxy collection install -r requirements.yaml
```

## Using Grafana collection role in playbook

```
---
- hosts: servers
  collections: monitoring.grafana
  roles:
    - role: <role name>
```
