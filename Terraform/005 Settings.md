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

# Settings

- Structure
	- Version
		- `version = "a.b.c"`: strict requirement
		- `version = ">= a.b.c"`: minimum version
		- `version = "~> a.b.c"`: only patch version (`.c`) may vary
	- Required providers
	- Backends

```hcl
terraform {
  required_version = "~> 1.10.0"
  
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "5.87.0"
    }
  }

  backend "s3" {
    bucket = ""
    key    = ""
    region = ""
  }
}
```

