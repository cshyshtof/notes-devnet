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

# State

- Concepts
	- The state knows what is configured vs desired end-state (terraform's memory)
	- Contains a mapping of resource instances to remote objects
	- Allows to automatically destroy and recreate resources
	- Terraform updates the state automatically during plan and apply
	- Stored locally in `terraform.tfstate` (json)
	- Backup file is automatically created and cannot be disabled (by design)
	- The state can be stored locally or on remote backend
- Commands
	- `terraform state list`: list locally stored resources
	- `terraform state show <resource_address>`
	- `terraform state mv <src name> <dst name>`
		- Mainly used to rename existing resources
		- Move a resource into a module and vice versa
		- Does not re-create any physical resources
	- `terraform state pull` - pull current state and output to stdout
	- `terraform state push` - update remote state with local state
	- `terraform state replace-provider` - replace provider in the state
	- `terraform state rm` - remove instances from the state


