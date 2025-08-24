# github-command
It looks like you're getting a "Repository not found" error because your local Git repository is trying to push to https://github.com/jakejheack/my-portfolio.git/, but you added the remote for https://github.com/jakejheack/my-web.git. There's a mismatch in the repository name.

To fix this, you need to change the remote URL of your local repository. Here's how you can do it using the command line:

1. Check Your Current Remote URL 🧐
First, let's confirm what remote URL your origin is currently pointing to.

Bash

git remote -v
This command will show you the URLs for your origin remote, both for fetching and pushing. You'll likely see something like:

origin  https://github.com/jakejheack/my-portfolio.git/ (fetch)
origin  https://github.com/jakejheack/my-portfolio.git/ (push)
2. Change the Remote URL 🔄
You can change the URL of an existing remote. In your case, you want to change the origin remote to point to my-web.git.

Bash

git remote set-url origin https://github.com/jakejheack/my-web.git
This command directly updates the URL associated with the remote named origin.

Alternatively, if you want to remove the old remote and add a new one (useful if you made a mistake adding it initially):

a. Remove the existing remote:

Bash

git remote rm origin
You got the error error: remote origin already exists. because you tried to git remote add origin ... again when it was already set. Removing it first would prevent that error if you were to re-add it.

b. Add the correct new remote:

Bash

git remote add origin https://github.com/jakejheack/my-web.git
3. Verify and Push Your Changes ✅
After changing the remote URL, verify it again:

Bash

git remote -v
You should now see:

origin  https://github.com/jakejheack/my-web.git (fetch)
origin  https://github.com/jakejheack/my-web.git (push)
Then, you can push your changes to the correct repository:

Bash

git push -u origin main
The -u flag sets the main branch as the upstream branch for origin, so subsequent git push or git pull commands don't need origin main.

This should resolve the "Repository not found" error and allow you to interact with your my-web GitHub repository.

It's quite a comprehensive request to list "all GitHub commands" as GitHub primarily leverages Git commands, with some additional interactions through its web interface or the GitHub CLI (gh).

Below is a breakdown of the most common and essential Git commands you'll use when working with GitHub, categorized for clarity.

1. Getting Started & Setup 🚀
These commands help you set up Git and a new repository.

git init: Initializes a new local Git repository.

Example: git init

git clone [url]: Creates a local copy of an existing remote repository.

Example: git clone https://github.com/user/repo.git

git config: Sets configuration variables (user name, email, editor, etc.).

Examples:

git config --global user.name "Your Name"

git config --global user.email "you@example.com"

git config --list (to view configurations)

2. Basic Workflow (Staging & Committing) 📝
The core commands for tracking changes and saving them.

git status: Shows the working tree status (modified, staged, untracked files).

Example: git status

git add [file]: Stages changes for the next commit.

Examples:

git add . (stages all changes)

git add index.html (stages a specific file)

git commit -m "[message]": Records the staged changes to the repository with a descriptive message.

Example: git commit -m "Add initial homepage content"

git rm [file]: Removes a file from the working tree and the index.

Example: git rm old_file.txt

git mv [old-file] [new-file]: Renames or moves a file.

Example: git mv old_name.txt new_name.txt

3. Branching and Merging 🌿
Essential for managing different lines of development and collaborative work.

git branch: Lists, creates, or deletes branches.

Examples:

git branch (list all branches)

git branch new-feature (create a new branch)

git branch -d old-branch (delete a local branch)

git checkout [branch-name]: Switches to a different branch or restores working tree files.

Example: git checkout new-feature

git checkout -b [new-branch]: Creates a new branch and switches to it.

Example: git checkout -b develop

git merge [branch]: Merges a specified branch's history into the current branch.

Example: git merge new-feature

git rebase [branch]: Reapplies commits on top of another base tip. Used for cleaning up commit history.

Example: git rebase main

4. Remote Repositories (GitHub Interaction) 🌐
How your local repository communicates with GitHub.

git remote -v: Lists all existing remote repositories.

Example: git remote -v

git remote add [name] [url]: Connects your local repository to a remote GitHub repository.

Example: git remote add origin https://github.com/user/repo.git

git remote set-url [name] [new-url]: Changes the URL for a remote repository.

Example: git remote set-url origin https://github.com/user/new-repo.git

git push [remote] [branch]: Uploads local branch commits to the remote repository.

Example: git push origin main

Initial push: git push -u origin main (sets upstream tracking)

git pull [remote] [branch]: Fetches and downloads content from a remote repository and immediately updates the local repository to match that content.

Example: git pull origin main

git fetch [remote]: Downloads objects and refs from another repository. It does not merge changes into your current branch.

Example: git fetch origin

git push --force (DANGER!): Overwrites history on the remote. Use with extreme caution.

Example: git push --force origin main

5. Inspecting History & Differences 🕰️
Commands for reviewing changes and history.

git log: Shows the commit history.

Examples:

git log --oneline (compact view)

git log --graph --oneline --all (graphical view of all branches)

git diff: Shows changes between commits, commit and working tree, etc.

Examples:

git diff (unstaged changes)

git diff --staged (staged changes)

git diff HEAD~1 (changes in the last commit)

git show [commit-hash]: Shows various types of objects (commits, tags, trees, blobs).

Example: git show abc123def

6. Undoing Changes ↩️
Commands for reverting or discarding modifications.

git restore [file]: Discards changes in the working directory (unstaged changes).

Example: git restore index.html

git reset [file]: Unstages changes from the index.

Example: git reset index.html

git reset --hard [commit-hash] (DANGER!): Resets the current branch head to a specified commit, discarding all changes since that commit.

Example: git reset --hard HEAD~1 (go back one commit)

git revert [commit-hash]: Creates a new commit that undoes the changes introduced by a specified commit. It maintains history.

Example: git revert abc123def

7. Stashing, Tagging & Cleaning ✨
More specialized but useful commands.

git stash: Temporarily shelves (or stashes) changes you've made to your working copy so you can work on something else, and then come back and re-apply them later.

Examples:

git stash save "Work in progress"

git stash pop

git stash list

git tag [name]: Creates, lists, deletes or verifies a tag object signed with GPG. Used to mark specific points in history (e.g., release versions).

Example: git tag v1.0.0

git clean -f: Removes untracked files from the working directory.

Example: git clean -fd (removes untracked files and directories)

8. GitHub-Specific Interactions (Beyond Git) 🔗
While not Git commands themselves, these are common ways to interact with GitHub:

GitHub Website: Creating pull requests, reviewing code, managing issues, configuring GitHub Pages, repository settings.

GitHub CLI (gh): A command-line tool to interact with GitHub from your terminal. It allows you to:

Create pull requests: gh pr create

Review pull requests: gh pr review

Manage issues: gh issue list, gh issue create

Manage releases: gh release create

Example: gh repo create my-new-project --public

This list covers the vast majority of commands you'll encounter and use daily when collaborating on GitHub. Git is powerful, and continuous learning will unlock more of its capabilities!
