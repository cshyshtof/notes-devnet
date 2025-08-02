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

# Modules

- Concepts
	- Group configurations files to provide some specific functionality
	- Reduce the amount of code and enforce best practices
	- Rely on a provider
	- You can create own modules and share them with a team
- Call
	- Source
		- Public module: `namespace/name/provider`
		- Private module: `host/namespace/name/provider`
		- Local module: `./modules/name`
	- You can pass variables to the module
	- You can call a module multiple times with different values
	- Module name has a local meaning
	- You can use returning value with `module.<name>.<variable>`

```hcl
module "vpc" {
  source = "namespace/name/provider"
  version = ""

  key = value
}
```

- Directory structure
	- `variables.tf`
	- `main.tf`: entry point
	- `outputs.tf`
	- `README.md`