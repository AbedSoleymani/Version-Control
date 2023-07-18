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

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

then run this

`brew install git`

After completing the installation, you should be able to execute `git --version` commands from the command line. If you see the information displayed, it indicates that everything is set up correctly and you're ready to proceed!
