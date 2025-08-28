

- **Git** - a *version control system* for *locally* tracking changes in files.
- **GitHub** - a website to *host* Git repositories *remotely*.

---
## Configuring Git

- `git config --list`
- `git config --global user.name "name"`
- `git config --global user.email "something@email.com"`

---
## Git Commands


### Repository Setup

- `git init`: set a working directory as a git repository to track changes.
- `git remote add origin <link>`: set remote repo to which local changes will be pushed.
	- `git remote -v`: verify remote repo.
- `git clone <link>`: clone a repository locally from GitHub.

### Branches

- `git checkout -b <new-branch-name>`: create a new branch.
	- `git checkout <another-branch>`: use another branch.
- `git branch`: check current branch name.
	- `git branch -m <new-branch-name>`: modify branch name.
	- `git branch -d <branch-name>`: delete branch. Move to another branch before deleting a branch.

### Update Repositories

- `git status`: check status of files.
	1. **untracked** - new files that git does not track yet.
	2. **modified** - files with changes.
	3. **staged** - files ready to be committed.
	4. **unmodified** - unchanged files.
- `git add .`: add all untracked files & modified files to a temporary staging area called ***index***. Mention file names instead of dot to add only specific files.
- `git reset`: unstage changes. Undo git add.
- `git commit`: move contents of index to local repository.
- `git log`: check commit history.
- `git diff`: check file changes in the branch before add & commit.
- `git push origin <branch-name>`: upload contents from local repo to remote repo.
- `git pull origin <branch-name>`: download contents from remote repo and update local repo.