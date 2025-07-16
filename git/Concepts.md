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

# Concepts

- Working directory
	- This is a directory that git controls
	- Git tracks differences between:
		- Working directory and local repository
		- Local repository and the remote repository
- Staging area, index, cache
	- Staging area is being deprecated, use index instead
	- This is where all the changes, that you want to perform, are placed
	- It's a binary file describing what user wishes to change, next commit
- Master, main
	- The main branch
- Origin
	- Default local name of remote repo
- Commit
	- Metadata for all the changes in particular file
	- It's a repo state, with unique sha-1 hash
	- Contains parent, data, author and a message
- Chunk
	- Single change declared for commit
- head
	- Last commit (sha) in particular branch
	- Each branch has own head in repo
- HEAD
	- Current commit, which is the source of the current index
	- Last sha is a head, but when we do a checkout, it becomes out HEAD
- Detached HEAD
	- Happens when we do a checkout of a commit, which is not a head
	- HEAD does not point to any branch
	- You can checkout such commit, but just to review, avoid doing commits
	- Changes are not shown in a log, and are hard to recover
	- Garbage collection will remove such phantom checkout
- Basic operations

```text
[Working]     [Index]      [ Local ]     [Remote]
    ----- add --->
                  -- commit -->
                               --- push --->
                               <-- fetch ---
    <------- checkout ---------
    -------- commit -a ------->
    <------- merge ------------
```
