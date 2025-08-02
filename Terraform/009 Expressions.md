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

# Expressions

- Strings and templates
	- Use a double-quote for strings, it supports all escape sequences
	- Supports multi-line, using Linux style `<<EOT`
	- Interpolation
		- `"Hello, ${var.username}"`
	- Directive
		- `"%{ if var.name != "" }${var.name}{ else }unknown%{ endif }}"`

```jinja2
<<EOT
%{ for ip in project.*.ip ~} # strip whitespace
Server IP: ${ip}
%{ endfor ~}
EOT
```

- References
- Operators
- Function calls
	- Terraform has lots of builtin functions
	- Numeric, string, collection, encoding, file, date/time, hash, IP, conversion
- Conditionals
	- Ternary: `condition ? true : false`
- For
	- The source can be a list, set, tuple or object
	- `[for s in var.vrfs : upper(s) if s != ""]`
	- `[for k, v in var.dict : length(k) + length(v)]` - key/value
	- `[for i, v in var.list : "${i} is ${v}"]` - index
	- `[]` - returns a list
	- `{}` - returns an object
	- Maps are ordered by a key, sets are ordered by string (alphabetically)
- Splat
	- Shorter representation of the `for`
	- `[for i in var.list : i.id]` = `var.list[*].id`
- Dynamic blocks

```text
locals {
  ingress_rules = [
    {
      port = 443
      description = "SSL"
    },
    {
      port = 80
      description = "HTTP"
    }
  ]
}

resource "" "" {
  dynamic "ingress" {
    for_each = local.ingress_rules

    content {
      description = ingress.value.description
      from = ingress.value.port
      to = ingress.value.port
      protocol = "tcp"
    }
  }
}
```
