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

# Resources

- Concepts
	- A resource describes one or more infrastructure object
	- The type is defined by each vendor/provider
	- Each resource has specific arguments
	- Adding it in the plan means that it must be present in the infrastructure
	- Referencing
		- Resources may point to other resources (the type and the name)
		- You can reference any internal argument
		- Ex.: `<type>.<local_name>.name`
		- Always use referencing to limit static values
- Structure

```hcl
resource "type" "local_name" {
   <arguments>
}
```

- Null
	- No specific association to an infrastructure resource
	- Requires a `null` provider

```hcl
resource "null_resource" "local_name" {
  ...
}
```

- Local
- External
- Meta arguments
	- They modify, how terraform manages resources
	- They reduce redundancy, increase scalability and simplify dependency
	- `depends_on`
		- The order of which resources are provisioned
		- Usually terraform guesses proper order
		- Explicit order may be required for complex applications (db before app)
		- `depends_on = [aws_db_instance.db]`
	- `count`
		- Define amount of resources to implement
		- Uses `count.index` within a loop, starts with 0, works similar to `for`
		- Can be an expression: `count = length(var.subnets)`
		- Reference created resource: `<type>.<name>[index]`
		- If some resource is removed, indexes are shifted
		- Be careful, as wrong resource can be deleted, better to use `for_each`
	- `for_each`
		- Iterates over map or set
		- Uses `each.key` and `each.value`
		- `for_each = toset(['rt1', 'rt2', 'rt3'])`
		- Deleting map/set elements is non-destructive, as we use specific keys
	- `provider`
		- You can use aliases for the same provider
		- Used mainly for different regions or pods
	- `lifecycle`
		- Define what happens to the resource (create, update, destroy)
		- `create_before_destroy = true` - used when replacing resource
		- `prevent_destroy`
		- `ignore_changes` - don't change whole resource if only an argument is  updated