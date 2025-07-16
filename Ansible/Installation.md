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

- Centos installation

```shell
dnf install -y epel-release
dnf install -y ansible
```

- Installation using pip

```shell
python -m venv venv
source venv/bin/activate
pip install ansible=2.9
```

- Useful tools

```shell
pip install yamllint
pip install ansible-lint
```

