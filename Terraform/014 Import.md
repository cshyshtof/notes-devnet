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

# Import

- Concepts
	- You can import resources, which are already implemented
	- Not all resources can be imported, check documentation
	- `to`: what resource block in terraform will this be mapped to
	- `id`: what is the existing infrastructure resource
	- You need to create a resource block that will manage imported resource
	- `terraform plan -generate-config-out=PATH`: creates a resource block
	- Once a resource is imported into a state file, you can delete the `import` block

```hcl
import {
  to = ""
  id = ""
}
```
