---
type: zettel
---

```meta-bind-button
label: Set next review
hidden: false
id: review
style: primary
actions:
  - type: command
    command: review-obsidian:future-review
  - type: input
    str: "next 7 days"
```

# Ansible installation

## Install on Centos

```shell
dnf install -y epel-release
dnf install -y ansible
```

## Install using pip

- Install the core ansible and some builtin collections

```shell
python -m venv venv
source venv/bin/activate
pip install ansible=11.4.0
```

- You can also install only the core, without any collections:

```shell
pip install ansible-core
```

## Install collections

- `cisco.aci.aci_bd`:
	- `cisco` - namespace
	- `aci` - collection
	- `aci_bd` - module

```bash
ansible-galaxy collection install cisco.aci
ansible-galaxy collection list
```

## Useful tools

```shell
pip install yamllint
pip install ansible-lint
```

