# Learn2Earn GitHub Student Guide

Welcome to the **Learn2Earn-Ikeja-Campus-Codespace** GitHub organization.

This guide explains how to use Git and GitHub for your Learn2Earn projects. It covers everything you need to get started, including:

* Connecting your computer to GitHub
* Setting up Git
* Understanding the Learn2Earn repository structure
* Cloning an existing repository
* Creating branches
* Making and saving changes
* Pushing your work to GitHub
* Pulling the latest changes
* Creating your own repository
* Forking a repository into the Learn2Earn organization
* Creating Pull Requests
* Getting your work reviewed by an Admin
* Keeping your local repository synchronized

You do **not** need to understand everything in this guide before you begin. Follow the steps in order and use the section that applies to what you are trying to do.

---

# 1. Repository Map — Which Workflow Should I Use?

Before running any Git commands, first determine **which type of repository you are working with**.

There are two main workflows in Learn2Earn.

## Workflow A — I want to work on an existing Learn2Earn repository

Use this workflow when you want to work on a repository that already exists in the organization.

For example:

```text
Learn2Earn-Ikeja-Campus-Codespace
        │
        └── python-assignment
```

Your workflow is:

```text
Learn2Earn repository
        │
        │ clone
        ▼
Your computer
        │
        ├── create branch
        │
        ├── make changes
        │
        ├── commit
        │
        └── push
                │
                ▼
        Pull Request → main
                │
                ▼
              Admin
                │
                ▼
             Merge
```

**Start with [Section 5 — Join the Learn2Earn GitHub Organization](#5-join-the-learn2earn-github-organization), then continue to cloning the repository.**

---

## Workflow B — I have my own project and need a Learn2Earn organization copy

Use this workflow when you are creating your own project, such as a group presentation, assignment, or personal project.

The recommended structure is:

```text
Your personal GitHub repository
        │
        │ Fork
        ▼
Learn2Earn-Ikeja-Campus-Codespace
        │
        ▼
Organization repository
```

For example:

```text
github.com/YOUR-USERNAME/group-3-presentation
                │
                │ fork
                ▼
github.com/Learn2Earn-Ikeja-Campus-Codespace/group-3-presentation
```

In this workflow:

* **You own the original personal repository.**
* **The Learn2Earn organization owns the fork.**
* Your GitHub account remains associated with your work and commits.
* The organization has its own copy of the project.
* Changes are managed through Git and Pull Requests.

**Start with [Section 27 — Creating Your Own Personal Repository](#27-creating-your-own-personal-repository).**

---

## Quick Decision Guide

| If...                                                    | Use...                                      |
| -------------------------------------------------------- | ------------------------------------------- |
| An Admin gives you an existing organization repository   | **Workflow A — Clone**                      |
| You are working on an existing Learn2Earn project        | **Workflow A — Clone**                      |
| You have created your own project                        | **Workflow B — Personal Repository → Fork** |
| Your group has a presentation/project that you own       | **Workflow B — Personal Repository → Fork** |
| You need to submit changes to an organization repository | **Branch → Push → Pull Request**            |

### The key idea

You will normally work in this cycle:

```text
GET THE REPOSITORY
       ↓
CREATE A BRANCH
       ↓
MAKE YOUR CHANGES
       ↓
COMMIT
       ↓
PUSH
       ↓
OPEN/UPDATE PULL REQUEST
       ↓
ADMIN REVIEWS
       ↓
ADMIN MERGES
```

---

# 2. Understanding Git and GitHub

Before working with the repositories, it is important to understand the difference between Git and GitHub.

## Git

**Git** is a version-control system installed on your computer.

It keeps track of changes to your files.

For example:

```text
Your computer
    │
    ├── project.py
    ├── README.md
    └── data/
```

Git can keep a history of the changes you make to these files.

## GitHub

**GitHub** is an online service where Git repositories can be stored and shared.

Think of it this way:

```text
Git
↓
Tracks your work on your computer

GitHub
↓
Stores and shares your Git repository online
```

You use Git commands on your computer to communicate with repositories hosted on GitHub.

---

# 3. The Basic Git Workflow

Most of your work will follow this pattern:

```text
Create or clone repository
        ↓
Create a branch
        ↓
Make changes
        ↓
Check your changes
        ↓
Commit changes
        ↓
Push branch to GitHub
        ↓
Open Pull Request
        ↓
Admin reviews your work
        ↓
Admin merges the Pull Request
```

You will frequently use these commands:

```bash
git status
git add .
git commit -m "Describe your changes"
git push
git pull
```

You should become comfortable with these commands.

---

# 4. Requirements

Before working with Learn2Earn repositories, make sure Git is installed.

Open your terminal and run:

```bash
git --version
```

You should see something similar to:

```text
git version 2.x.x
```

If Git is not installed, install it using the instructions for your operating system.

### Ubuntu/Debian Linux

```bash
sudo apt update
sudo apt install git
```

Then verify:

```bash
git --version
```

---

# 5. Join the Learn2Earn GitHub Organization

You must be a member of the **Learn2Earn-Ikeja-Campus-Codespace** GitHub organization before you can access organization repositories that have been assigned to you.

After receiving your invitation:

1. Sign in to GitHub.
2. Accept the organization invitation.
3. Confirm that you can access the required repository.

If you cannot access a repository you have been instructed to use, contact an **Admin**.

---

# 6. Create a GitHub Account

You need a GitHub account to participate in Learn2Earn GitHub projects.

Your GitHub username is important.

For example:

```text
github.com/your-username
```

You will use your GitHub username when working with Learn2Earn repositories.

---

# 7. Configure Git on Your Computer

You should configure your name and email address before making commits.

Run:

```bash
git config --global user.name "Your Full Name"
```

Then:

```bash
git config --global user.email "your-email@example.com"
```

For example:

```bash
git config --global user.name "Chidiebere Micah"
git config --global user.email "you@example.com"
```

Check your configuration:

```bash
git config --global --list
```

You should see your name and email.

---

# 8. Connect Your Computer to GitHub

Git needs a way to authenticate you when communicating with GitHub.

The recommended method for this course is **SSH**.

## 8.1 Check whether you already have an SSH key

Run:

```bash
ls ~/.ssh
```

You may see files such as:

```text
id_ed25519
id_ed25519.pub
```

If you already have an SSH key that you use with GitHub, you may be able to use it.

If you do not have one, continue below.

---

# 9. Create an SSH Key

Generate an Ed25519 SSH key:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

When asked where to save the key, you can normally press **Enter** to accept the default location.

You may also be asked for a passphrase.

A passphrase is recommended for additional security.

---

# 10. Start the SSH Agent

Run:

```bash
eval "$(ssh-agent -s)"
```

Then add your SSH key:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

# 11. Add Your SSH Key to GitHub

Display your public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output.

It will look similar to:

```text
ssh-ed25519 AAAAC3... your-email@example.com
```

Go to your GitHub account and open:

**Settings → SSH and GPG keys → New SSH key**

Give the key a recognizable title, such as:

```text
My Laptop
```

Paste the public key and save it.

> **Important:** Never give anyone your private key.
>
> Your private key is:
>
> ```text
> ~/.ssh/id_ed25519
> ```
>
> Your public key is:
>
> ```text
> ~/.ssh/id_ed25519.pub
> ```
>
> Only the `.pub` key should be added to GitHub.

---

# 12. Test Your GitHub Connection

Run:

```bash
ssh -T git@github.com
```

The first time you connect, GitHub may ask whether you trust the host.

Type:

```text
yes
```

A successful connection will give you a message indicating that you have authenticated with GitHub.

If this does not work, contact an Admin before continuing.

---

# 13. Understanding a Repository

A Git repository is a project that Git is tracking.

A repository can exist:

* On your computer
* On GitHub
* In both places

For example:

```text
GitHub
   │
   │ clone
   ▼
Your computer
```

When you clone a repository, Git creates a local copy on your computer.

---

# 14. Clone an Existing Learn2Earn Repository

If an Admin gives you an existing Learn2Earn repository to work with, you normally **clone** it.

Open your terminal and move to the folder where you keep your projects.

For example:

```bash
cd ~/projects
```

Then clone the repository:

```bash
git clone git@github.com:Learn2Earn-Ikeja-Campus-Codespace/REPOSITORY-NAME.git
```

Replace:

```text
REPOSITORY-NAME
```

with the actual repository name.

For example:

```bash
git clone git@github.com:Learn2Earn-Ikeja-Campus-Codespace/python-project.git
```

Git will create a directory containing the project.

Enter the directory:

```bash
cd python-project
```

Check the repository:

```bash
git status
```

---

# 15. Check Which Repository You Are Connected To

Inside a repository, run:

```bash
git remote -v
```

You should see something similar to:

```text
origin  git@github.com:Learn2Earn-Ikeja-Campus-Codespace/python-project.git (fetch)
origin  git@github.com:Learn2Earn-Ikeja-Campus-Codespace/python-project.git (push)
```

This tells you which GitHub repository your local repository is connected to.

---

# 16. Always Check Your Status

One of the most important Git commands is:

```bash
git status
```

Run it frequently.

It tells you:

* Which branch you are on
* Which files have changed
* Which files are staged
* Whether your local branch is ahead or behind the remote repository

---

# 17. Do Not Work Directly on `main`

For Learn2Earn projects, you should normally work on a **branch** instead of making changes directly on `main`.

Create a branch:

```bash
git switch -c feature/my-work
```

For example:

```bash
git switch -c feature/student-registration
```

Check your branch:

```bash
git branch
```

You should see:

```text
* feature/student-registration
  main
```

The `*` indicates your current branch.

---

# 18. Make Your Changes

Now edit the project files normally.

When finished, check your changes:

```bash
git status
```

---

# 19. Review Your Changes

Before committing, inspect what changed:

```bash
git diff
```

This shows the differences between your current files and the last committed version.

Take a moment to review your changes.

Make sure you did not accidentally modify files that you did not intend to change.

---

# 20. Stage Your Changes

Tell Git which changes you want to include in your next commit.

For all changed files:

```bash
git add .
```

Or add a specific file:

```bash
git add filename.py
```

Then check:

```bash
git status
```

The files should now appear under **Changes to be committed**.

---

# 21. Commit Your Changes

Create a commit:

```bash
git commit -m "Describe what you changed"
```

For example:

```bash
git commit -m "Add student registration function"
```

A commit is a saved point in your project's history.

Good commit messages should explain what changed.

### Good

```bash
git commit -m "Add login validation"
```

### Not useful

```bash
git commit -m "stuff"
```

```bash
git commit -m "changes"
```

---

# 22. Push Your Branch to GitHub

The first time you push a new branch:

```bash
git push -u origin feature/student-registration
```

After that, you can normally use:

```bash
git push
```

Your branch will now exist on GitHub.

---

# 23. Create a Pull Request

After pushing your branch:

1. Open the repository on GitHub.
2. GitHub should show your recently pushed branch.
3. Select **Compare & pull request**.
4. Make sure the target branch is `main`.
5. Give the Pull Request a clear title.
6. Explain what you changed.
7. Submit the Pull Request.

Your Pull Request will be reviewed by an **Admin**.

---

# 24. Understand the Learn2Earn Pull Request Process

The `main` branch is protected.

Students should therefore expect this workflow:

```text
Student
   │
   ▼
Create branch
   │
   ▼
Make changes
   │
   ▼
Commit
   │
   ▼
Push branch
   │
   ▼
Open Pull Request
   │
   ▼
Admin reviews
   │
   ├── Changes requested
   │       │
   │       └── Student makes changes
   │               ↓
   │           Push again
   │
   └── Approved
           │
           ▼
       Admin merges
```

Do not try to bypass the Pull Request process.

The purpose of the process is to allow your work to be reviewed before it becomes part of the project's `main` branch.

---

# 25. Responding to Review Comments

An Admin may request changes.

Do not create a completely new Pull Request just because changes were requested.

Instead:

1. Make the requested changes on your existing branch.
2. Check your changes:

```bash
git status
```

3. Review them:

```bash
git diff
```

4. Stage them:

```bash
git add .
```

5. Commit them:

```bash
git commit -m "Address review feedback"
```

6. Push:

```bash
git push
```

Your existing Pull Request will automatically update.

---

# 26. Keep Your Local `main` Up to Date

Other people may make changes to the repository while you are working.

Before starting new work, update your local repository.

First switch to `main`:

```bash
git switch main
```

Then:

```bash
git pull
```

Now create your new branch:

```bash
git switch -c feature/my-new-work
```

A common workflow is therefore:

```bash
git switch main
git pull
git switch -c feature/my-new-work
```

---

# 27. Creating Your Own Personal Repository

Use this workflow when you are creating your own project.

For example:

```text
group-3-presentation
```

Create the repository under **your personal GitHub account**, not directly under the Learn2Earn organization.

To create a personal repository:

1. Sign in to GitHub.
2. Select **New repository**.
3. Enter the repository name.
4. Choose whether the repository should be public or private according to the project instructions.
5. Create the repository.

---

# 28. Connect an Existing Local Project to Your Personal Repository

Suppose you already have this project on your computer:

```text
group-3-presentation/
```

Enter the directory:

```bash
cd group-3-presentation
```

Initialize Git if it is not already a Git repository:

```bash
git init
```

Add the files:

```bash
git add .
```

Create your first commit:

```bash
git commit -m "Initial project commit"
```

Connect your local repository to your GitHub repository:

```bash
git remote add origin git@github.com:YOUR-USERNAME/group-3-presentation.git
```

Replace:

```text
YOUR-USERNAME
```

with your actual GitHub username.

For example:

```bash
git remote add origin git@github.com:your-username/group-3-presentation.git
```

Verify:

```bash
git remote -v
```

Then push:

```bash
git branch -M main
git push -u origin main
```

Your local project is now connected to your personal GitHub repository.

---

# 29. Fork Your Repository into Learn2Earn

Once your personal repository is ready:

1. Open your personal repository on GitHub.
2. Select **Fork**.
3. Choose **Learn2Earn-Ikeja-Campus-Codespace** as the organization.
4. Give the repository the appropriate name.
5. Create the fork.

You should now have:

```text
Personal repository

github.com/YOUR-USERNAME/group-3-presentation


Learn2Earn organization fork

github.com/Learn2Earn-Ikeja-Campus-Codespace/group-3-presentation
```

---

# 30. Important: A Fork Is Not a Two-Way Mirror

A fork does **not** mean that changes automatically synchronize in both directions.

Think of it as two connected repositories:

```text
Personal repository
        │
        │
        ▼
Learn2Earn organization fork
```

Changes made in one repository do not automatically appear in the other.

You must use Git to synchronize changes when necessary.

---

# 31. Clone the Learn2Earn Fork

If you want to work primarily with the Learn2Earn repository, clone it:

```bash
git clone git@github.com:Learn2Earn-Ikeja-Campus-Codespace/group-3-presentation.git
```

Then:

```bash
cd group-3-presentation
```

Check the remote:

```bash
git remote -v
```

You should see:

```text
origin  git@github.com:Learn2Earn-Ikeja-Campus-Codespace/group-3-presentation.git
```

---

# 32. Working with Your Personal Repository and the Learn2Earn Fork

If you need to work with both repositories, you can configure two remotes.

For example:

```text
origin
↓
Learn2Earn repository

personal
↓
Your personal repository
```

Inside your local repository:

```bash
git remote -v
```

You may initially have:

```text
origin  git@github.com:Learn2Earn-Ikeja-Campus-Codespace/group-3-presentation.git
```

Add your personal repository:

```bash
git remote add personal git@github.com:YOUR-USERNAME/group-3-presentation.git
```

Check:

```bash
git remote -v
```

You should now have two remotes.

---

# 33. Push to a Specific Repository

Because you now have two remotes, you can choose where to push.

Push to Learn2Earn:

```bash
git push origin main
```

Push to your personal repository:

```bash
git push personal main
```

For branches:

```bash
git push origin feature/my-work
```

or:

```bash
git push personal feature/my-work
```

---

# 34. Pulling Changes

To get changes from your current remote:

```bash
git pull
```

If you want to explicitly specify a remote and branch:

```bash
git pull origin main
```

If you have two remotes:

```bash
git pull origin main
```

gets changes from Learn2Earn.

```bash
git pull personal main
```

gets changes from your personal repository.

---

# 35. Fetch vs Pull

You will eventually encounter:

```bash
git fetch
```

and:

```bash
git pull
```

They are not exactly the same.

### `git fetch`

Downloads information about changes from the remote repository but does not automatically change your current branch.

```bash
git fetch
```

### `git pull`

Fetches changes and then integrates them into your current branch.

```bash
git pull
```

For beginners, `git pull` is usually what you need when you simply want to update your local branch.

---

# 36. Useful Git Commands

### Check repository status

```bash
git status
```

### Show branches

```bash
git branch
```

### Create a branch

```bash
git switch -c feature/name
```

### Switch branches

```bash
git switch main
```

```bash
git switch feature/name
```

### See your changes

```bash
git diff
```

### Stage changes

```bash
git add .
```

### Commit

```bash
git commit -m "Describe your changes"
```

### Push

```bash
git push
```

### Pull

```bash
git pull
```

### See remote repositories

```bash
git remote -v
```

### See commit history

```bash
git log --oneline
```

---

# 37. A Complete Example

Suppose you are working on a Learn2Earn repository called:

```text
python-assignment
```

Clone it:

```bash
git clone git@github.com:Learn2Earn-Ikeja-Campus-Codespace/python-assignment.git
```

Enter it:

```bash
cd python-assignment
```

Update `main`:

```bash
git switch main
git pull
```

Create your branch:

```bash
git switch -c feature/my-solution
```

Make your changes.

Check them:

```bash
git status
```

Review them:

```bash
git diff
```

Stage them:

```bash
git add .
```

Commit:

```bash
git commit -m "Implement assignment solution"
```

Push:

```bash
git push -u origin feature/my-solution
```

Then open a Pull Request on GitHub.

After your Admin reviews your work, respond to any requested changes and push again:

```bash
git add .
git commit -m "Address review feedback"
git push
```

The Pull Request will update automatically.

---

# 38. What You Should NOT Do

## Do not commit passwords or secrets

Never put passwords, API keys, tokens, SSH private keys, or other secrets into a repository.

Do not commit files such as:

```text
.env
```

if they contain secrets.

## Do not share your private SSH key

Never share:

```text
id_ed25519
```

You may share your public key:

```text
id_ed25519.pub
```

but your private key must remain private.

## Do not work directly on `main`

Use a feature branch unless an Admin explicitly tells you otherwise.

## Do not force-push to shared branches

Avoid:

```bash
git push --force
```

especially when working with shared repositories.

## Do not delete branches or files you do not understand

If you are unsure, ask an Admin.

---

# 39. Common Problems

## "Permission denied (publickey)"

Your computer could not authenticate with GitHub using SSH.

Check:

```bash
ssh -T git@github.com
```

Also check whether your SSH key is loaded:

```bash
ssh-add -l
```

If necessary:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## "Repository not found"

Check that:

1. The repository name is correct.
2. You have access to the repository.
3. Your GitHub account is the correct account.
4. Your SSH authentication is working.

Check the remote:

```bash
git remote -v
```

---

## "Your branch is behind"

Someone has pushed changes that you do not have locally.

Usually:

```bash
git pull
```

will update your branch.

If Git reports a conflict, **do not panic**. Stop and ask an Admin for help if you are unsure how to resolve it.

---

# 40. Recommended Daily Workflow

When starting work:

```bash
git switch main
git pull
git switch -c feature/my-work
```

Work on your project.

Then:

```bash
git status
git diff
git add .
git commit -m "Describe your changes"
git push -u origin feature/my-work
```

Open or update your Pull Request.

If an Admin requests changes:

```bash
# Make the requested changes

git status
git diff
git add .
git commit -m "Address review feedback"
git push
```

---

# 41. The Most Important Commands to Remember

If you remember nothing else, remember these:

```bash
git status
```

**What am I currently doing?**

```bash
git pull
```

**Get the latest changes.**

```bash
git switch -c feature/my-work
```

**Create a branch for my work.**

```bash
git add .
```

**Prepare my changes for a commit.**

```bash
git commit -m "Describe my changes"
```

**Save my changes in Git history.**

```bash
git push
```

**Send my committed changes to GitHub.**

```bash
git remote -v
```

**Which GitHub repository am I connected to?**

---

# 42. The Learn2Earn Rule

The most important principle is:

> **Work on a branch, push your branch, and use a Pull Request to submit your work for review.**

Do not be afraid of Git.

Git becomes much easier when you understand the basic cycle:

```text
CHANGE
  ↓
STATUS
  ↓
ADD
  ↓
COMMIT
  ↓
PUSH
  ↓
PULL REQUEST
  ↓
REVIEW
  ↓
MERGE
```

When you are unsure about what a Git command will do, **stop and ask an Admin before running it**, especially if the command involves deleting files, deleting branches, resetting commits, or force-pushing.

Welcome to the **Learn2Earn-Ikeja-Campus-Codespace** GitHub workflow. 🚀
