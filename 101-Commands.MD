GIT Cheat Sheet

Master the essential Git commands with this handy cheatsheet:

↳ **Initialization:**
- `git init`: Initialize a new Git repository.
- `git clone [url]`: Clone a repository from a remote URL.

↳ **Basic Commands:**
- `git add [file]`: Add file changes to the staging area.
- `git commit -m "message"`: Commit changes to the repository.
- `git status`: View the status of files in the working directory.
- `git log`: View commit history.
- `git diff`: Show changes between commits, commit and working tree, etc.

↳ **Branching:**
- `git branch`: List all branches in the repository.
- `git branch [branch-name]`: Create a new branch.
- `git checkout [branch-name]`: Switch to a different branch.
- `git merge [branch]`: Merge changes from one branch into the current branch.

↳ **Remote Repositories:**
- `git remote add [name] [url]`: Add a remote repository.
- `git push [remote] [branch]`: Push changes to a remote repository.
- `git pull [remote] [branch]`: Fetch from and integrate with another repository or a local branch.

↳ **Undoing Changes:**
- `git reset [file]`: Unstage changes.
- `git checkout -- [file]`: Discard changes in the working directory.
- `git revert [commit]`: Revert a commit.

↳ **Miscellaneous:**
- `git config --global user.name "Your Name"`: Set author name.
- `git config --global user.email "youremail@example.com"`: Set author email.
- `git stash`: Stash changes in a dirty working directory.
