# Git exo — my answers

## Part 1: Setup & config
- Git version: `git --version`
- Config commands used:
  - `git config --global user.name "Lara Normand"`
  - `git config --global user.email "lara.normand29+pro@gmail.com "`

---

## Part 2: Create Your First Repository
Commands used:
```bash
mkdir OOPgit
cd OOPgit
git init
touch README.md
```

---

## Part 3: Your First Commit
1. `git status` — shows the current state of the repository
2. `git add README.md` — stages README.md for commit
3. `git commit -m "Add readme file"` — commits with the message
4. `git log` — shows the commit history

---

## Part 4: Make Changes
1. Command used to edit the file:
```bash
echo "My first change" >> README.md
```
2. `git status` now shows `README.md` under **"Changes not staged for commit"** — Git knows the file was modified since the last commit but the change hasn't been staged yet.
3. Commands used:
```bash
git add README.md
git commit -m "Update readme with new content"
```
4. I now have **2 commits**.

---

## Part 5: Exploration
- `git diff` — shows the exact line-by-line differences between my working files and the last commit. Lines with `+` are additions, lines with `-` are deletions.
- `git log --oneline` — shows the commit history in a compact format, one line per commit: short hash + message.

---

## Part 6: Working with Branches
```bash
git branch                   # list all branches
git branch feature-script    # create feature-script branch
git checkout feature-script  # switch to feature-script
git checkout -b dev          # create and switch to dev in one command
git checkout feature-script  # switch back to feature-script
git branch                   # verify current branch (* marks the active one)
```

---

## Part 7: Create a Bash Script on a Branch
```bash
touch env_install.sh
```

Content of `env_install.sh`:
```bash
#!/bin/bash
echo "Starting installation..."
sudo apt update
sudo apt install -y curl
echo "Installation complete!"
```
```bash
chmod +x env_install.sh                    # make it executable
git add env_install.sh                     # stage
git commit -m "Add install script"     # commit
git log --oneline                      # check history
```

---

## Part 8: Merge Branches
```bash
git checkout main
ls
```
- `env_install.sh` is **not present** because it was committed on `feature-script`. Each branch has its own independent history — `main` doesn't have those changes until we merge.
```bash
git merge feature-script   # merge feature-script into main
ls                         # env_install.sh now appears
git log --oneline          # commits from feature-script are now in main's history
git branch -d feature-script  # delete the merged branch
```

---

## Part 9: Push to GitHub
```bash
git remote add origin https://github.com/Lara-Normand-Pro/OOPgit.git
git push -u origin main
```
- After refreshing GitHub, I can see all my files (`README.md`, `env_install.sh`) and the full commit history.

---

## Part 10: Delete and Clone
```bash
cd ..
rm -rf OOPgit
git clone https://github.com/Lara-Normand-Pro/OOPgit.git
cd OOPgit
ls
```
- After cloning, all files are present: `README.md` and `env_install.sh`.
