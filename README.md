# Version Control

## Introduction
Version control is a system that helps manage changes to files and code over time. It tracks and records modifications, allowing you to keep a history of revisions, collaborate with others, and easily revert to previous versions if needed.

Multiple popular version control systems exist, including Git, SVN (Subversion), and Mercurial. These systems can be categorized into two main cathegories:
1. centralized models
2. distributed models.

In the centralized model, there is a single powerful central computer that hosts the project. All interactions with the project must pass through this central computer, which acts as the authoritative source of information.
In contrast, the distributed model does not rely on a central repository. Instead, each developer possesses a complete copy of the project on their own computer. This approach offers the advantage of working offline since all necessary information is available locally.

Here, we'll be using the version control system **_Git_**, which is a distributed version control system and is known for its speed, flexibility, and powerful branching and merging capabilities. It is widely adopted and has become the industry standard for version control. Git is popular for both small personal projects and large-scale collaborative development. Please keep in mind that Git and GitHub are quite different. Git, is the version control tool, while GitHub is the service that hosts Git projects!

For instance, Google Docs' Revision history page is incredibly powerful in terms of its capabilities. However, when it comes to coding, it falls short in meeting certain requirements, including:
* Lack of the ability to assign labels to changes.
* Absence of a detailed explanation feature to provide reasons for specific modifications.
* Inability to navigate seamlessly between different versions of a document.
* Lack of flexibility to undo a specific change (Change A), make subsequent edits (Edit B), and then revert back to the original state including Change A without impacting Edit B.
The version control tool, _Git_, can do all of those things and a lot more!

## Terminology
1. **Version Control System/Source Code Manager:**
Version control systems (VCS) are tools designed to effectively manage and track various versions of source code. They are also referred to as source code managers (SCM). Git, being an SCM, is an example of a powerful VCS.
2. **Commit:**
In Git, a commit is akin to capturing snapshots of a mini filesystem. When you commit changes, Git creates a record of how your files appear at that particular moment and maintains a reference to that snapshot. This process is similar to saving progress in a game, as it captures your project's files and associated information. Commits serve as the foundational building blocks in Git, guiding all actions taken to support the creation of these snapshots.
3. **Repository / repo:**
A repository is a folder that holds your project work and includes certain files (typically hidden on Mac OS X) that facilitate communication with Git. Repositories can be located either on your local computer or as a remote copy on another machine. They consist of commits, which represent the individual changes made to the project over time.
4. **Working Directory:**
The Working Directory refers to the collection of files visible in your computer's file system. When you access your project files using a code editor, you are interacting with the files within the Working Directory.
It is important to distinguish the Working Directory from the files that have been saved and recorded in the repository through commits.
In the context of Git, the Working Directory is distinct from the command line's notion of the current working directory. The current working directory in the command line represents the directory that your shell is currently focused on.
5. **Checkout:**
A checkout occurs when the contents of a repository are copied to the Working Directory, allowing you to access and work with the files locally.
6. **Staging Index (Staging Area or Index):**
It is a component within the Git directory that holds important information regarding the content that will be included in your next commit. It can be visualized as a preparation table where Git organizes the upcoming commit. The files residing in the Staging Index are ready to be added to the repository as part of the next commit.
7. **SHA:**
A commit's SHA serves as a unique identification number (ID), representing the contents of a file or directory structure in Git. It consists of a 40-character string composed of hexadecimal characters (0-9 and a-f). The SHA, which stands for "Secure Hash Algorithm," is essentially an ID assigned to each commit, enabling precise tracking and referencing of changes made in Git.
8. **Branch:**
A branch is created when a new path of code development is established, branching off from the main line of progress. This separate path allows for independent work without affecting the main line.
To illustrate with a gaming analogy, imagine creating a save point in a game and then attempting a risky move. If the move doesn't yield the desired outcome, you can easily revert back to the save point. The significant advantage of branches lies in their ability to create save points on different paths, enabling you to switch between branches and have distinct save points on each of them. This flexibility amplifies the effectiveness and versatility of branches.
![areas](https://github.com/AbedSoleymani/Version-Control/assets/72225265/4316bffb-1cd6-482a-8929-62891fac6b26)
## Installation (Mac M1)
Install homebrew by running this in your terminal:
<br>
`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
<br>
then run this
<br>
`brew install git`
<br>
After completing the installation, you should be able to execute `git --version` commands from the command line. If you see the information displayed, it indicates that everything is set up correctly and you're ready to proceed!

Now, we have to configure our git:
<br>
`git config --global user.name "<AbedSoleymani>"`
<br>
`git config --global user.email "<zsoleymani@ualberta.ca>"`
<br>
To make sure that Git output is colored and the Git displays the original state in a conflict, run these commands:
`git config --global color.ui auto`
<br>
`git config --global merge.conflictstyle diff3`
<br>
Now, run `git config --list` to see all of your applied configurations.
<br>
Since I am using VS Code, I have to get Git working with this particular code editor by running this command:
<br>
`git config --global core.editor "code --wait"`
## Creating a Git repository
To initialize a new Git repository or reinitialize an existing one in your current working directory within VS Code, execute the command `git init` in the VS Code terminal.
This command creats a hidden directory called `.git` which serves as the central storage/brain and configuration center for the repository.
Inside the `.git` directory, you'll find all the necessary files and directories that store configuration settings and maintain a history of commits.

Sometimes, it can be convenient to download and execute projects shared by others on GitHub, allowing you to run them locally on your machine.
Additionally, initiating a new project often involves repetitive setup steps that can become laborious.
In such cases, a practical approach is to create a starter project as a reference point.
By doing so, whenever you start a new project, you can simply duplicate the starter project from GitHub, providing you with a consistent and ready-to-go foundation.
In such situations, the `git clone` command is used to create an identical copy of an existing repository on GitHub.
<br>
To do so, open a terminal in the folder or navigate to the folder that you want to clone the project and run this command: <br>
`git clone <repository_url>`<br>
If you want to use a different repository name instead of the default one on GitHub, run this command:<br>
`git clone <repository_url> <desired_name>`

`git clone` performs the following actions:
* Takes the path to an existing repository as input.
* By default, it generates a directory with a name identical to the repository being cloned.
* Alternatively, it can accept a second argument to specify a custom name for the directory.
* The new repository is created within the current working directory.

Wondering when it's appropriate to execute specific Git commands?
Need confirmation that Git is ready for a command?
Concerned about command success?
The answer to all of these questions is the `git status` command!
`git status` provides essential information, including:
* Branch details: It reveals the current branch and indicates if it's synchronized with the remote branch or if there are pending commits to push or pull.
* Staged changes: It lists modified files that have been staged (added) for the upcoming commit. These changes are ready for repository inclusion.
* Untracked files: It shows files in the working directory that Git hasn't started tracking yet. These files are excluded from commits by default.
* Unstaged changes: It displays modifications made to tracked files that haven't been staged. These changes aren't queued for the next commit.

During initial stages, frequent use of the `git status` command is highly recommended! It ensures a clear understanding of the repository status.

In addition to `git status`, the `git log` command is used to display a chronological list of commit history in a Git repository. When you run `git log`, it shows a list of commits in reverse chronological order, starting with the most recent commit and going backward in time.
<br>
The information displayed by git log typically includes:
<br>
1. **Commit Hash:** A unique identifier for each commit.
2. **Author:** The name and email of the person who made the commit.
3. **Date:** The date and time when the commit was made.
4. **Commit Message:** A brief description of the changes made in the commit.
<br>
You can navigate between log information by scroling up and down and press `q` to quit out of the log.
<br>
While `git log` provides a more detailed and multiline output with commit hashes, author information, dates, and commit messages displayed across multiple lines, `git log --oneline` offers a more condensed view with just the first 7 characters of the commit's SHA and the commit message, all on a single line, making it easier to get an overview of the commit history at a glance.

The `git log` command includes a flag that allows you to view the altered files in a commit, along with the count of inserted and deleted lines. This flag is `--stat` (derived from "statistics"), and you can use it as follows: `git log --stat`.
