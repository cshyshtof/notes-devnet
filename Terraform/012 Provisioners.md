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

# Provisioners

- Concepts
	- Should be used as a last resort
	- The result is not included in terraform state
- Local-exec
	- You can run local commands
	- `command`: required
	- `working_dir`
	- `interprater`
	- `environment`

```hcl
resource "null_resource" "example" {
  provisioner "local-exec" {
    command = "Get-Date > completed.txt"
    interpreter = ["Powershell", "-Command"]
  }

  provisioner "local-exec" {
    command = "echo ${self.private_ip}"
  }
  
  provisioner "local-exec" {
    command = "echo $KEY"
    environment = {
      KEY = "ergwergwergewrg"
    }
  }
}
```

- Remote-exec
	- `script`
	- `scripts`
	- `inline`: set of direct commands

```hcl
resource "null_resource" "example" {
  provisioner "remote-exec" {
    scripts = [
      "./setup.sh",
      "./bootstrap.py"
    ]
  }
}
```

- File
	- `source`
	- `destination`
	- `content`

```hcl
resource "null_resource" "example" {
  provisioner "file" {
	source = "hosts"
	destination = "/etc/hosts"
  }
}
```

- Connection
	- Tells the provisioner how to connect

```hcl
resource "null_resource" "example" {
  provisioner "file" {
	source = "hosts"
	destination = "/etc/hosts"
  }

  connection {
    type = "ssh"
    user = "root"
    password = "${var.root_password}"
    host = "${var.host}"
  }
}
```