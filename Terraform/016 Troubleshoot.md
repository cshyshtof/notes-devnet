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

# Troubleshoot

- State drift
	- Replace
		- `terraform {plan | apply} -replace="resource"`
	- Import
	- Refresh
		- `terraform apply --refresh-only --auto-approve`
		- Modifies local terraform state
- Diagnostics
	- `terraform <command> --help`
	- Language errors
		- `terraform validate` - validates syntax
		- `terraform console` - run interactive shell for local project (reads all files)
		- `terraform fmt` - format using best practices
	- State errors
		- Use refresh, apply or replace
	- Core and provider errors
		- Logs, bugs list
- Graph
	- Draws a dependency graph (requires `graphviz`)
	- `terraform graph | dot -Tpng > graph.png`
- Logging
	- TRACE, DEBUG, INFO, WARN, ERROR
	- JSON displays TRACE or higher as JSON
	- `export TF_LOG_CORE=DEBUG`
	- `export TF_LOG_PROVIDER=DEBUG`
	- `export TF_LOG_PATH="./logs/"`
- Crash
	- `crash.log`
- Display variable value

```hcl
terraform console <<EOF
var.test
EOF
```