# Git Rebase
## Rebase to Remote Branch

```bash
# Fetches the latest changes from the remote branch and rebases your local commits on top of them
git pull --rebase origin <branch-name>

# You can make this behavior automatic:
git config --global pull.rebase true
```

## Rebase Current branch
```bash
# N can be any number of commits you want to update
git rebase -i HEAD~N
```

Running above command will open an editor like Below
```
# If N set to 3
pick a1b2c3 commit 1
pick d4e5f6 commit 2
pick g7h8i9 commit 3
```

**Interactive Options:**
- pick        => Keep commit
- reword   => Edit commit message
- edit        => Modify commit
- squash   => Merge with previous commit
- fixup       => Like squash but discard message
- drop        => Delete commit

---
# Efficient Git Clone for Large Repositories

```bash
git clone --filter=blob:none --no-checkout <repo-url>
cd <repo>

git sparse-checkout init --no-cone
git sparse-checkout set /* !path/to/large/file/or/directory

git checkout

# To add excluded files later
git sparse-checkout add path/to/large/file/or/directory
git sparse-checkout disable
```
- `--filter=blob:none` → Skips downloading file contents (blobs) and supports below options:
	- `--filter=blob:none` → No file contents (recommended)
	- `--filter=blob:limit=1m` → Only download files < 1MB
- `--no-checkout` → Prevents immediate file download
- `--no-cone` allows advanced patterns like exclusions (`!path`) and supports below patterns
	- `/*` → include all
	- `!path` → exclude path
	- `dir/**` → recursive include
- `git checkout` → Populates working directory based on rules and downloads only required files

---
#  Modify last commit.

```bash
git commit --amend --no-edit
git commit --amend -m "New Message to Change Last Commit Message"
# If last commit was pushed to upstream use:
git push --force
```

---
# Undo a Commit and Redo

```bash
git commit -m "Accident Commit"
git reset HEAD~
# [ edit files as necessary ]
git add .
git commit -c ORIG_HEAD
```
- commit with `-c ORIG_HEAD` will open an editor, which initially contains the log message from the old commit and allows you to edit it. If you do not need to edit the message
---
# Delete Remote and Local Branch

```bash
# Delete local branch
git branch -d <branch_name>

# Delete remote branch
git branch <remote_name>/origin --delete <branch_name>

```
---
#  Rename a Git Branch

```bash
# Rename current branch
git branch -m <new_name>

# To push the local branch and reset the upstream branch
git push origin -u <new_name>

# To delete the remote branch
git push origin --delete <old_name>

```
---
# Force "git pull" to Override Local Files.

```bash
git checkout master
git branch new-branch-to-save-current-commits
git fetch --all
git reset --hard origin/master
```