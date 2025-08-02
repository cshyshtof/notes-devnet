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

# Backends

- Concepts
	- Specifies where and how operations are performed and states are stored
- Standard
	- Store only a state
	- Third party providers (ex. AWS S3 bucket, Consul, etc.)
- Enhanced
	- Can perform terraform operations
	- Local
	- Remote
		- Has own runtime environment
		- Terraform Cloud, Terraform Enterprise

```hcl
# Local
terraform {
  backend "local" {
    path = ".${path.module}/states/terraform.tfstate"
  }
}

# Retrieves the root module output values from another configuration
data "terraform_remote_state" "networking" {
  backend = "local"
  
  config = {
    path = ".${path.module}/networking/terraform.tfstate"
  }
}

resource "" "" {
  subnet_id = data.terraform_remote_state.mydc.outputs.subnet_id
}
```
