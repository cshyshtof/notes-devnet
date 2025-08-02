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

# Terraform

- Concepts
	- Platform agnostic, declarative and idempotent
	- No server-side dependencies
	- Maintains and tracks desired state (snapshot) of the infrastructure
	- Uses HCL (Hashicorp Configuration Language)
	- File extensions can be `.tf` but also `.tf.json` (rarely)
	- Written in Go and shipped as a single binary file
	- Uses automatic dependency mapping to discover the order of operation
	- Core component talks to providers and provisioners with RPC
	- Uses plugins, which are providers and modules
	- OpenTofu
		- Open-source fork from Terraform 1.5 and forward
		- Maintained as separate projects and by separate communities
		- Maintains backward compatibility for Terraform configurations
- Install
	- Terraform
		- `sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo`
		- `sudo yum -y install terraform`
		- `terraform version`
	- Terraform auto-complete
		- Optional
		- `terraform --install-autocomplete`
		- Adds `complete -C /usr/local/bin/terraform terraform` to `.bashrc`
- Workflow
	- Code - prepare files
	- Init - pull providers and modules
	- Plan - speculate what will be changed
	- Validate - validate attributes, types of values, etc.
	- Apply - execute the plan and provision the infrastructure
	- Destroy - destroy all created objects
- Structure
	- Filenames can be any, but rather try to follow community standards
	- Terraform looks for `.tf` files, but only in local directory (non-recursive)
	- All project files are combined together as one
	- `main.tf` - main entry point
	- `variables.tf` - variables' definitions
	- `terraform.tfvars` - variables' values
	- `outputs.tf`
	- `providers.tf`
	- `terraform.tfstate` and `terraform.tfstate.backup`
	- `terraform.lock.hcl`
	- `.terraform` all providers and modules are stored here, created by `init`
- Style
	- Names should be a `snake_style`
	- Align equal signs wherever possible (`terraform fmt`)
	- Use meaningful block identifiers/names
	- Comment and document your code
	- Do not hardcode values
	- Use `.terraformignore` and `.gitignore`
- Named values
	- Resources: `<resource type>.<name>[<optional index]`
	- Input variables: `var.<name>`
	- Local variables: `local.<name>`
	- Child module output: `module.<name>`
	- Data sources: `data.<data type>.<name>`
	- Paths
		- `path.module`
		- `path.root`
		- `path.cwd`
		- `terraform.workspace`
	- Block local
		- `count.index`
		- `each.key`
		- `each.value`
		- `self.attribute`
