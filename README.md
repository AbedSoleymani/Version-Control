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
It would be awesome if we could see exactly _what_ those changes were.
The `git log` command has a flag that can be used to display the actual changes made to a file. The flag is `--patch` which can be shortened to just `-p`.
<br>
`git log --patch` or `git log -p`
1. displays the files that have been modified
2. displays the location of the lines that have been added/removed
3. displays the actual changes that have been made


One problem here is that we have to scrol a lot through the patch output just to get to the right commit so we could see its info.
For all of these commands `git log`, `git log --oneline`, `git log --stat`, and `git log --patch`, we can supply the first 7 characters of the SHA of a commit as the final argument and review the info starting at that commit! For example: `git log -p fdf5493`.

Finally, the `git show` command reveals the information about the most recent commit of the author (only one commit) including its author name, date, message, and the patch information. We also can add SHA as the final argument (e.g., `git show fdf5493`) to get access to the information of an specific commit. 

## Adding commits to a repository
So far, we have learned some foundations about `git` and we can do:
1. `git init` to create a new repository
2. `git clone` to copy the existing repository
3. `git log` to review existing commits
4. `git status` to get the status of a repository.
<br> From now on, we will learn to do:
1. `git add` to add files from the working directory to the staging index
2. `git commit` to take files from the staging index and save them in our local repository
3. `git diff` to display the difference between two versions of a file

The `git add` command is used to move files from the Working Directory to the staging index. The command<br>`git add <file1> <file2> … <fileN>`
<br>takes a space-separated list of file names. Alternatively, the period `.` (i.e., `git add .`) can be used in place of a list of files to tell Git to add the current directory (and all nested files) to the staging index.

Now, to create a new commit with a specified commit message, we use this command:<br>
`git commit -m "commit message"`<br>
A good commit message is short (less than 60-ish characters) and explains what the commit does (not how or why!).
A good commit message does not explain why the changes are made or does not explain how the changes are made (that's what `git log -p` is for!).<br>
**IMPORTANT** Do not use the word "and"! If you have to use "and", your commit message is probably doing too many changes. In this situation, it is professional to break the changes into separate commits to have a better track of your code for your future purposes.<br>
Good commit messages:
* `"Implemented fib(num) function to calculate Fibonacci sequence"`
* `"Fixed issue XYZ: Incorrect output data type"`

Bad commit messages:
* `"Updating main.py"`
* `"Fixed issue XYZ`

To grasp the purpose and significance of the `git diff` command, let's consider a scenario where you begin working on the next feature of your project at night but leave it unfinished before going to bed.
As a result, when you resume work the next day, there are changes in your code that haven't been committed yet.
This is understandable since you haven't completed the new feature, but now you face the challenge of recalling precisely what modifications you made since your last commit.
Although `git status` informs you about the altered files, it doesn't provide details regarding the actual content of those changes.
The `git diff` command can be used to see changes that have been made but haven't been committed, yet.<br>
To recap, `git diff` displays:
1. the files that have been modified
2. the location of the lines that have been added/removed
3. the actual changes that have been made

Now, let's assume you add a file, like a Word document, to your project's directory, but you don't want it to be added to the repository. The issue that arises here is that when you use `git add .`, it includes all files, and the Word document might accidentally be committed to the repository. To avoid this situation and keep the file within your project's directory structure without accidentally committing it, you can use a specially named file called `.gitignore` (note the dot at the beginning; it's essential!). You need to place this `.gitignore` file in the same directory as the hidden `.git` directory.

In the `.gitignore` file, you simply list the names of files that you want Git to ignore and not track. Git recognizes the contents of a file with the name `.gitignore`, and when it finds `project.docx` listed in it, it automatically ignores that file. Consequently, the ignored file won't be displayed in the output of `git status`. This way, you can maintain files in your project without worrying about them accidentally becoming part of the repository.

Suppose you add 50 images to your project, but you want Git to disregard all of them. Does this imply that you have to individually list each filename in the `.gitignore` file? Not at all! That would be quite overwhelming! Instead, you can employ a technique known as "globbing". Globbing allows you to utilize special characters to match patterns or characters. Therefore, if all the 50 images are JPEG images located in the "`images`" folder, you can add the following line to `.gitignore`, and Git will ignore all 50 images: `images/*.jpg`

## Tagging, Branching, and Merging
The `git tag` command adds tag to specific commits. The tag is an extra label for commits which indicate useful information.
