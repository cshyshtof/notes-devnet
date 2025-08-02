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

# Workspaces

- Concepts
	- Virtual instance of local project
	- You can implement different resources based on a workspace
	- A default workspace is always present and cannot be deleted
	- Local workspaces are stored in `terraform.tfstate.d`
- Commands
	- `terraform workspace`
		- `list` - list all workspaces
		- `show` - show current workspace
		- `select` - switch to other workspace
		- `new` - create new workspace
		- `delete` - delete workspace

```hcl
resource "" "" {
  count = "${terraform.workspace == "default" ? 5 : 1}"
}
```

