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

# Providers

- Concept
	- Providers are used to interact with remote systems
	- Required providers must be declared, so terraform can install them locally
	- Each provider adds a set of resource types and data sources
	- Each provider has specific configuration (ex. authentication)
	- The provider label must match the official provider name
	- Terraform registry
		- https://registry.terraform.io/
		- Official, Partner, Community
	- Aliases are used to use the same provider for different pods/regions
- Commands
	- `terraform providers` - list providers that are used by the project

```hcl
provider "aci" {
  username = var.aci.username
  password = var.aci.password
  url = var.aci.url
  alias = "labaci"
}

resource "" "" {
  provider = aci.labaci
}
```
