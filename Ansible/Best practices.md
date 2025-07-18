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

# Ansible best practices

- Inventory
	- Create a separate file for groups of hosts
	- Use dynamic inventory where possible
- Naming
	- Use meaningful, extended names for tasks
	- Use consistent names, tags, spaces, roles, directory structure
	- Add role prefix to variables used in that role
	- Add `vault_` prefix for variables stored in a vault
	- Always use full qualified name collection name in tasks, even for core modules
- Playbook
	- Do not combine tasks and variables
	- Divide tasks into smaller parts rather than using conditionals
	- Disable `gather_facts` if not required, so tasks are executed faster
	- Create separate tasks for configuration and implementation
	- Use modules whenever possible, avoid `shell`, `rest_api`, etc
	- Always verify if variables are set and are valid, use `assert` module
	- Use the same playbooks for different environments, just use different inventory
	- Do not use `vars/` in roles (hard to overwrite), better to use `defaults/`
	- Avoid `set_facts` (hard to diagnose)
- Security
	- Do not define passwords in playbooks and variable file
	- Use separate file to store passwords and add it to `.gitignore`
	- Do not use root directly, use dedicated ansible user and add it to sudoers
- Clean code
	- Avoid one-liners
	- Use native YAML (consistent syntax highlighting)
	- Use tags for better task filtering
