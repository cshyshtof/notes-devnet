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

# Plan

- Concepts
	- Queries the provider for current state of resources
	- Calculates the delta between the desired and the actual state
	- Does not change anything in the infrastructure
- Commands
	- `terraform plan`
	- Requires manual review
		- `+` - create
		- `~` - modifie in-place
		- `-` - delete
		- `-/+` - destroy and re-create
	- `plan -out=file`: save the plan to a binary file

