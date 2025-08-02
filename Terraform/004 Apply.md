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

# Apply

- Concepts
	- Executes actions proposed in the terraform plan
	- Runs validation first
	- Lock
		- Creates `.terraform.tfstate.lock.info`
		- Prevent others from running `terraform apply` at the same time
		- It could corrupt infrastructure's state file
		- For remote backends, the locking is handled by the backend itself
		- You should NOT commit any state lock files to version control
		- They are temporary and specific to a single operation
- Commands
	- `terraform apply [--auto-approve]`
	- `terraform apply <file>` - uses a file created with a plan, no confirmation


