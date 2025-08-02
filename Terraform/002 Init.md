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

# Init

- Concepts
	- Initializes `.terraform` directory, can be changes with `-plugin-dir=path`
	- Downloads all plugin dependencies (providers, modules)
	- Lock
		- Creates a dependency lock (`.terraform.lock.hcl`)
		- The purpose is to record the specific versions of providers and modules
		- This guarantees consistent and predictable plans and applies
		- This file should be comitted to git
- Commands
	- `terraform init`
	- `terraform init -upgrade`: upgrade plugins
	- `terraform get`
		- Get module into local directory without initializing
		- Used usually for developing own modules
