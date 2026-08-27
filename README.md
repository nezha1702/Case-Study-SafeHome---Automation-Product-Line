#  Working with GitHub Collaboration & Markdown

This guide explains how to work with a **GitHub collaboration repository**, from joining the repository and cloning it to creating and editing documents using **Markdown**.

---

##  Table of Contents

* [1. What is Repository Collaboration?](#1-what-is-repository-collaboration)
* [2. Joining a Collaboration Repository](#2-joining-a-collaboration-repository)
* [3. Cloning the Repository](#3-cloning-the-repository)
* [4. Changing to the Repository](#4-changing-to-the-repository)
* [5. Working with Markdown](#5-working-with-markdown)
* [6. Adding and Editing Documents](#6-adding-and-editing-documents)
* [7. Saving Changes with Git](#7-saving-changes-with-git)
* [8. Getting the Latest Changes](#8-getting-the-latest-changes)
* [9. Basic Collaboration Workflow](#9-basic-collaboration-workflow)
* [10. Summary](#10-summary)

---

# 1. What is Repository Collaboration?

**Repository collaboration** means multiple people work together on the same GitHub repository.

For example, a team may have one repository for a university project:

```text
Project Repository
│
├── README.md
├── Diagram/
│   ├── use_case.md
│   └── class_diagram.md
│
└── SRS/
```

Each team member can:

* Clone the repository
* Create or edit files
* Write documentation
* Commit changes
* Push changes to GitHub
* Pull changes made by other team members

Git helps the team keep track of changes and prevents everyone from having to manually exchange files.

---

# 2. Joining a Collaboration Repository

Before working on another person's repository, the repository owner needs to add you as a **collaborator**.

### Repository owner

The owner can:

1. Open the GitHub repository.
2. Go to **Settings**.
3. Open **Collaborators** or **Collaborators and teams**.
4. Add the GitHub username of the team member.
5. Send the invitation.

### Team member

After receiving the invitation:

1. Open the GitHub invitation.
2. Accept the invitation.
3. You now have permission to work with the repository according to the permissions given by the owner.

>  You need permission before you can directly push changes to a repository you do not own.

---

# 3. Cloning the Repository

After joining the repository, clone it to your computer.

First, copy the repository URL from GitHub.

Example:

```bash
git clone https://github.com/username/project-name.git
```

For example:

```bash
git clone https://github.com/team-example/safehome.git
```

This downloads the repository from GitHub to your computer.

You can check that the repository was downloaded using:

```bash
ls
```

On Windows PowerShell, you can also use:

```powershell
Get-ChildItem
```

---

# 4. Changing to the Repository

After cloning, move into the repository directory using `cd`.

```bash
cd project-name
```

Example:

```bash
cd safehome
```

You can check the current directory using:

```bash
pwd
```

You can also see the files inside the repository:

```bash
ls
```

Example:

```text
safehome/
├── README.md
├── docs/
└── src/
```

---

# 5. Working with Markdown

**Markdown** is a lightweight markup language commonly used for writing documentation on GitHub.

Markdown files normally use the `.md` extension.

For example:

```text
README.md
requirements.md
design.md
testing.md
```

## 5.1 Headings

Use `#` to create headings.

```markdown
# Main Heading

## Section Heading

### Subsection Heading
```

The more `#` symbols you use, the smaller the heading becomes.

---

## 5.2 Bold and Italic Text

### Bold

```markdown
**This is bold text**
```

Result:

**This is bold text**

### Italic

```markdown
*This is italic text*
```

Result:

*This is italic text*

---

## 5.3 Lists

### Unordered List

```markdown
- Git
- GitHub
- Markdown
- Repository
```

Result:

* Git
* GitHub
* Markdown
* Repository

### Ordered List

```markdown
1. Clone the repository
2. Change to the repository
3. Edit the document
4. Commit the changes
5. Push the changes
```

Result:

1. Clone the repository
2. Change to the repository
3. Edit the document
4. Commit the changes
5. Push the changes

---

## 5.4 Code

Inline code can be written using backticks:

```markdown
Use `git status` to check your changes.
```

Result:

Use `git status` to check your changes.

For multiple lines of code, use triple backticks:

````markdown
```bash
git status
git add .
git commit -m "Update documentation"
```
````

---

## 5.5 Links

You can create a link using:

```markdown
[GitHub](https://github.com)
```

Result:

[GitHub](https://github.com)

---

## 5.6 Images

Images can be added using:

```markdown
![Description](image.png)
```

Example:

```markdown
![System Architecture](images/system-architecture.png)
```

---

## 5.7 Tables

Markdown also supports tables.

```markdown
| Member | Role |
|--------|------|
| Member 1 | Developer |
| Member 2 | Designer |
| Member 3 | Tester |
```

Result:

| Member   | Role      |
| -------- | --------- |
| Member 1 | Developer |
| Member 2 | Designer  |
| Member 3 | Tester    |

---

# 6. Adding and Editing Documents

After entering the repository, you can create or edit Markdown documents.

For example, create a requirements document:

```bash
touch requirements.md
```

Then open it with your preferred editor, such as VS Code:

```bash
code requirements.md
```

You can write something like:

```markdown
# System Requirements

## Functional Requirements

- User login
- User registration
- System monitoring
- Alarm management

## Non-Functional Requirements

- Security
- Reliability
- Performance
- Usability
```

After editing the document, save the file.

Check which files have changed:

```bash
git status
```

---

# 7. Saving Changes with Git

Git uses three main steps to save your work and send it to GitHub.

## Step 1: Add the Changes

Add a specific file:

```bash
git add requirements.md
```

Or add all changed files:

```bash
git add .
```

---

## Step 2: Commit the Changes

Create a commit with a meaningful message:

```bash
git commit -m "Add system requirements documentation"
```

A good commit message should briefly explain what you changed.

Examples:

```bash
git commit -m "Add README documentation"
```

```bash
git commit -m "Update functional requirements"
```

```bash
git commit -m "Fix Markdown formatting"
```

---

## Step 3: Push the Changes

Send your committed changes to GitHub:

```bash
git push
```

After pushing, the changes will appear in the GitHub repository.

---

# 8. Getting the Latest Changes

When working with other people, someone else may have pushed changes before you.

Use:

```bash
git pull
```

This downloads the latest changes from GitHub and updates your local repository.

A common workflow is:

```bash
git pull
```

Then work on your files:

```bash
code .
```

After finishing:

```bash
git add .
git commit -m "Update documentation"
git push
```

---

# 9. Basic Collaboration Workflow

The complete collaboration process can be represented as:

```text
        GitHub Repository
               │
               ▼
        Join Collaboration
               │
               ▼
        Clone Repository
               │
               ▼
       cd project-name
               │
               ▼
       Edit/Create Files
               │
               ▼
          git status
               │
               ▼
            git add
               │
               ▼
          git commit
               │
               ▼
           git push
               │
               ▼
        GitHub Repository
               │
               ▼
      Other Members Pull
```

### Typical Commands

```bash
# Clone the repository
git clone <repository-url>

# Enter the repository
cd <repository-name>

# Check the current status
git status

# Get the latest changes
git pull

# Edit or create documents
code .

# Add changes
git add .

# Save changes
git commit -m "Update documentation"

# Upload changes
git push
```

---

# 10. Summary

Working with a GitHub collaboration repository follows a simple workflow:

1. **Join the repository** — Accept the collaboration invitation from the repository owner.
2. **Clone the repository** — Download the repository to your computer using `git clone`.
3. **Change to the repository** — Use `cd` to enter the project directory.
4. **Work with documents** — Create or edit files such as `.md` Markdown documents.
5. **Check changes** — Use `git status` to see what has been modified.
6. **Stage changes** — Use `git add`.
7. **Commit changes** — Use `git commit` with a meaningful message.
8. **Push changes** — Use `git push` to upload your work to GitHub.
9. **Pull updates** — Use `git pull` to get changes made by other team members.

###  The Golden GitHub Workflow

```bash
git pull
# Work on your files
git add .
git commit -m "Describe your changes"
git push
```

In short:

> **Pull → Work → Add → Commit → Push**

That's basically the team-project survival kit. 

---

## Quick Reference

| Command                   | Purpose                     |
| ------------------------- | --------------------------- |
| `git clone <url>`         | Download a repository       |
| `cd <folder>`             | Enter a directory           |
| `git status`              | Check repository status     |
| `git pull`                | Get the latest changes      |
| `git add .`               | Stage all changes           |
| `git commit -m "message"` | Save changes locally        |
| `git push`                | Upload changes to GitHub    |
| `ls`                      | List files                  |
| `pwd`                     | Show current directory      |
| `code .`                  | Open the project in VS Code |

---

##  Final Idea

Git and GitHub make collaboration easier because every team member can work on the same project while keeping track of changes.

**Git** manages the project's version history locally, while **GitHub** provides an online platform for storing the repository and collaborating with other team members.

```text
                 GIT + GITHUB
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
        Git                    GitHub
   Version Control        Online Repository
          │                       │
          └───────────┬───────────┘
                      ▼
               Team Collaboration
                      │
                      ▼
             Pull → Work → Commit
                      │
                      ▼
                    Push
```
