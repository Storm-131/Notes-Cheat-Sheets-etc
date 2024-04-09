# Git / GitHub 🐈‍⬛

#### Installation

```bash
conda install -c anaconda git

git config --global user.name "..."
git config --global user.email "...@google.com"

git config --global --edit
```

---

#### Setup Repo

```bash
# Create your own folder for Git
git init

# Clone an existing repo
git clone https://...
```

---

#### Workflow (Local)

```bash
# Show current changes
git status

# Moves changes from the working directory to Git's staging area.
git add test.txt
git add -all

# Commits the snapshot from the staging area into the (official) project history
git commit -m "Text about the changes"
```

#### Clean up

```bash
# Clean up the Repo
git gc --aggressive --prune=all
```

---

#### Workflow (Online)

```bash
# Pushes the commit files from local folders into the online repository
git push origin master

# Pull the online repo into the local offline working environment
git pull --all
git fetch origin master
```

---

### Rebase (Delete old history)

```bash
# Checkout
git checkout --orphan latest_branch

# Add all the files
git add -A

# Commit the changes
git commit -am "commit message"

# Delete the branch
git branch -D main

# Rename the current branch to main
git branch -m main

# Finally, force update your repository
git push -f origin main
```

---