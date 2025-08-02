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

# Variables

- Schema
	- Variables must be first defined (placeholder), usually in `variables.tf`
	- Structure: `variable "var_name" {}`
	- Parameters:
		- All parameters are optional
		- `sensitive`: hide a value in logs
		- `type`
		- `default`
		- `description`
		- `validation`
	- Types
		- Primitive
			- String
			- Value
			- Bool
		- List
			- Lists maintain order, index starts at 0
			- `[val, val]`
			- `list(string)`, `list(number)`
		- Set
			- No indexing, just a list of unordered, unique values
			- `set(string)`, `set(number)`
		- Map
			- Dictionary, key=value
			- `{key = val, key = val}`
		- Tuple
		- Object
		- No type
			- `null` - it's not empty value, it means use provider's default value
	- Variables can contain complex structures

```hcl
variable "var_name" {
  type = object(
    {
      a = string
      b = optional(string)
    }
  )
}
```

- Assign
	- `terraform.tfvars` is automatically loaded
	- Other files must be included with `--var-file`
	- Files named `<filename>.auto.tfvars` will be also automatically loaded
	- It can be used to split variables in multiple files
	- You can separate variables, based on usage (prod, test)
	- Environment variables `TF_VAR_<variable>` are automatically loaded
	- Order of preference (highest to lowest):
		- `-var "key=value"` and `--var-file`
		- `.auto.tfvars`
		- `.tfvars`
		- `TF_VAR_`
		- defaults
	- Reference with: `var.<var_name>`
- Output values
	- Visible in a state file for cross-reference
	- You can access those variables without a need to query the infrastructure
	- `sensitive` means no logging, but still present in a state file
	- `terraform output [-json]` - display all values in the state file
	- Output value can be complex: `https://${deploy_vm.ip_address}`

```hcl
output "host_ip" {
  value = deploy_vm.ip_address
  description = ""
  sensitive = false
}
```

- Local values
	- Used mainly as constants, which are often used in many files (names, tags)
	- You can reference local variables within local variables
	- You can reference local variable with `local.<variable>`
	- Can be many blocks

```hcl
locals {
  key = value
}

locals {
  common_tags = {
    Owner = ""
  }
}
```