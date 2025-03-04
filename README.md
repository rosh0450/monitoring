# Monitoring

Monitoring is a central repository which consists of monitoring related Ansible collections.

## Ansible Collections

Collections are a distribution format for Ansible content taht can include playbooks, roles, modules and plugins.

| Namespace | Collection | Description | Readme |
|-----------|---------| -- |--|
|monitoring | grafana | Collections to install, configure & manage tools provided by Grafana | [monitoring.grafana](grafana/README.md)|

## Install collections via command line

```
$ ansible-galaxy collection install git@github.com:rosh0450/monitoring.git
```

## Install connections via `requirements.yaml`

```
# requirements.yaml
---
collections:
  - name: monitoring
    source: ssh://git@github.com:rosh0450/monitoring.git
    type: git
```

```
$ ansible-galaxy collection install -r requirements.yaml
```

## Using collection role in playbook

```
---
- hosts: servers
  collections: monitoring.<collection name>
  roles:
    - role: <role name>
```
