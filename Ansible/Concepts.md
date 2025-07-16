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

# Ansible concepts

- Concepts
	- Ansible generates python scripts which are executed on remote host
	- First, a setup module is run (`gather_facts)`
	- Multiple `*_facts` are used, depending on remote OS
- Commands
	- `ansible`
		- Run an ad-hoc single task
	- `ansible-config`
		- View ansible configuration
	- `ansible-doc`
		- Documentation tool
	- `ansible-galaxy`
		- Perform role and collection related operations
		- Install collections
			- Collections are used to increase modularity and module distribution
			- `ansible-galaxy collection install cisco.ios`
			- `ansible-galaxy collection list`
			- Installed in `~/.ansible/collections`
	- `ansible-inventory`
		- Show Ansible inventory
	- `ansible-playbook`
		- Runs whole Ansible playbook
	- `ansible-vault`
		- Encrypt/decrypt utility for Ansible files
