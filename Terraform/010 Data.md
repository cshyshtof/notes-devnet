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

# Data


- Concepts
	- A placeholder for static resource's data
	- You can reference it in resources using `data.`
	- Available data sources are provider specific
	- The value is gathered from existing infrastructure
	- You can use filters to find a proper value
	- Does not create nor modify any resources (nullipotent)
	- Similar to `null`, but does not require a provider
	- Recommended over null

```hcl
data "type" "name" {
  filter {
    name = ""
    values = ""
  }
}

myvar = data.<type>.<local_name>.<attribute>
```
