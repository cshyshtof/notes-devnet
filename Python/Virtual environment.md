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

# Virtual environment

- `venv`
	- Newer version of `virtualenv`, but with a subset of its features
	- Included in the Python standard library since 3.3
	- `sudo apt-get install python3-venv`; Some Debian/Ubuntu distros require additional package installation
	- Creates basic environments without extra overhead
	- Officially recommended by the Python Software Foundation
	- Lacks advanced features, like dependency management from a file
	- It can't be used to install different Python versions
	- `python3 -m venv myenv` - create
- `virtualenv`
	- It was the standard before `venv` and still offers more features
	- Much faster environment creation compared to `venv`
	- Can be extended with custom scripts
	- Supports older Python versions (both 2 and 3)
	- `pip install virtualenv`
	- `virtualenv myvenv --python=python3.7` - create
- Activate
	- Linux: `source venv/bin/activate`
		- The `source` (`.` is an alias) sets variables for a shell
		- Running the `activate` directly sets variables for child process only
	- Windows: `venv\Scripts\activate`
- Deactivate
	- Use `deactivate`, as `exit` will leave a shell
