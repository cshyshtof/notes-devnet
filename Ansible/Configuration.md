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

# Ansible configuration

- Generate `ansible.cfg` with all default options
	- `ansible-config init --disabled > ansible.cfg`
- Configuration is loaded in the following order (until the first one is found)
    - `export ANSIBLE_CONFIG=/etc/ansible/my-config.cfg`
    - `./ansible.cfg`
    - `~/.ansible.cfg`
    - `/etc/ansible/ansible.cfg`
- Display all configs, even default ones
	- `ansible-config dump [--only-changed]`
- Display `ansible.cfg` content
	- `ansible-config view`
- Which config file is used in particular directory
	- `ansible --version`

