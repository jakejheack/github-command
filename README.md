1. Initializing a Repository & Adding a README 📝
These commands are used to start tracking a project with Git and prepare your README.md file.

echo "# my-web" >> README.md: This command creates or appends the text "# my-web" to a file named README.md. This is a quick way to create a basic README with a title.

Example: echo "# My Awesome Project" >> README.md

git init: This command initializes a new local Git repository in your current directory. It creates a hidden .git folder that Git uses to track your project's history.

Example: git init

git add README.md: This command stages the README.md file (or any specified file) for the next commit. Staging means telling Git that you want to include the current changes of this file in your next saved version.

Example: git add . (to stage all new/modified files)

2. Committing Changes Locally 💾
After staging, you save those changes to your local repository's history.

git commit -m "first commit": This command records the staged changes as a new commit in your local repository's history. The -m flag allows you to provide a short, descriptive message about the changes.

Example: git commit -m "Initial project setup with README"

3. Connecting to GitHub & Pushing 🌐
These commands establish the connection to your GitHub repository and upload your local changes.

git branch -M main: This command renames your current branch to main. main is the modern default branch name on GitHub, replacing the older master. The -M (or --move --force) option will rename the branch even if it already exists, or if it clashes with a remote branch of the same name.

Example: git branch -M main

git remote add origin https://github.com/jakejheack/my-web.git: This command adds a new remote repository to your local Git configuration. origin is the conventional name for the primary remote repository (usually on GitHub), and the URL points to your specific repository on GitHub.

Example: git remote add origin https://github.com/your-username/your-repo-name.git

git push -u origin main: This is the command to upload your local main branch to the origin remote on GitHub.

The -u (or --set-upstream) flag is used the first time you push a new branch. It tells Git to remember that your local main branch should track the main branch on origin. After this, you can just type git push or git pull.

Example: git push -u origin main

Summary of the process:
Initialize Git: git init

Create/Add Files: echo "# My Project" >> README.md or copy your website files.

Stage Files: git add . (or git add README.md)

Commit Changes: git commit -m "Meaningful message"

Set Branch Name: git branch -M main

Connect to GitHub: git remote add origin [your-repo-url]

Push to GitHub: git push -u origin main
