# Introduction to Git and Demo Workflow

### P.S. Git can be challenging to grasp initially. It's designed to be learned through hands-on experience. If you encounter difficulties or don't understand something, it's completely normal, don't hesitate to look it up onlineor ask someone.  

## What is Git?

Git is a distributed version control system that tracks changes in any set of computer files. It's primarily used for coordinating work among programmers collaboratively developing source code. Git was created by Linus Torvalds (the same person who developed the Linux kernel) in 2005.

### How Git Works

Git works by creating a snapshot of your project each time you commit. These snapshots are stored in a repository, allowing you to track changes, revert to previous versions, and collaborate with others. Git uses a branching model to enable multiple lines of development, and merging to integrate changes from different branches.  It also supports distributed workflows, meaning each developer has a complete copy of the repository, enhancing collaboration and redundancy.

## Why do we need Git for large projects?

Git is essential for large projects because it:

1. Allows multiple developers to work on the same project simultaneously
2. Tracks changes over time, enabling easy rollbacks if needed
3. Facilitates branching and merging, allowing for experimental features without affecting the main codebase
4. Provides a complete history of all changes, enhancing accountability and understanding of project evolution
5. Enables effective collaboration through features like pull requests and code reviews

## Key Git Terminology using Demo repository

Let's walk through some key Git concepts and operations using a demo project. We'll explain each term and demonstrate how to perform the associated actions using the command line, GitHub CLI (gh), and VS Code.

### Repository (Repo)

A repository, often shortened to "repo," is a directory where Git has been initialized to start version controlling your files. It's like a project's folder that contains all of your project's files and each file's revision history.

To create a new repository:

Command Line:
```
git init
```

VS Code:
1. Open the folder you want to initialize as a Git repository
2. Click on the Source Control icon in the left sidebar
3. Click on "Initialize Repository"

### Commit

A commit is a snapshot of your repository at a specific point in time. It's like saving a version of your project.

Let's create a file named hello.txt, add some text to it  and make our first commit, but before you commit, you need to stage the changed files. 

## Stage 
Staging is the process of selecting which changes you want to include in your next commit. This gives you control over what gets recorded in the repository's history.

to stage a file named hello.txt 
Command Line:
```
git add hello.txt
```

VS Code:
- In the Source Control view, click the '+' next to the file to stage it

if you make any changes to staged file, you'll have to stage it again. otherwise it will commit the last staged version of the file. 


Now that we have learnt how to stage a file, lets make our first commit 

## Making our first commit 
first, stage he changed files, you may stage any or all of them. to stage all files at once in command line use 
```
git add . 
```
this stages all changed files in the repo


to make a commit 
```
git commit -m "commit message"
```
or in VSCode click on source control view, type a commit message and commit. 
A commit message is important and you cannot commit ithout writing a commit message. It doesnt need to be unique, but should be simple and helpful to help identify the commit in later staged. 

## Viewing Commit History with `git log`

To see the history of commits in your repository, you can use the `git log` command. This command provides a detailed list of all the commits, including information such as the commit hash, author, date, and commit message.

Command Line:
```
git log 
```
This will display the commit history in the terminal. Each commit will be shown with its unique hash, author, date, and message.

to see the same in VS code, just look for the history in Source Control View.

## Time Travel: Moving Between Commits


Git allows you to move between different commits, effectively "time traveling" through your project's history.

To go back to a previous commit:

Command Line:
```
git checkout <commit-hash>
```

GitHub CLI:
```
gh checkout <commit-hash>
```

VS Code:
1. In the Source Control view, right-click on a commit in the history
2. Select "Checkout"

Remember, when you're checking out old commits, you'll be in a "detached HEAD" state. If you want to make changes, it's best to create a new branch from that point.


## A little advanced concepts 

Complete the walkthough in [this repository](https://github.com/MostlyKIGuess/Intro-to-Git-Demo) for a clear understanding of the concepts. Below notes are just for reference and can be ignored if you've understood stuff in the given linked 

### Branch

A branch is an independent line of development. It allows you to work on different features or experiments without affecting the main codebase.

To create and switch to a new branch:

Command Line:
```
git branch new-feature
git checkout new-feature
```

GitHub CLI:
```
gh branch create new-feature
```

VS Code:
1. Click on the branch name in the bottom-left corner
2. Select "Create new branch" and enter the branch name

### Merge

Merging is the process of combining different branches. Let's make a change in our new branch and merge it back to main:

Command Line:
```
echo "New feature added" >> hello.txt
git add hello.txt
git commit -m "Update hello.txt in new-feature branch"
git checkout main
git merge new-feature
```

GitHub CLI:
```
echo "New feature added" >> hello.txt
gh commit -m "Update hello.txt in new-feature branch"
gh checkout main
gh merge new-feature
```

VS Code:
1. Make changes to `hello.txt`
2. Stage and commit the changes
3. Switch to the main branch
4. Go to Source Control view, click "..." and select "Branch > Merge Branch"
5. Choose the "new-feature" branch to merge

### Remote

A remote is a common repository that all team members use to exchange their changes. GitHub is a popular platform for hosting remote repositories.

To add a remote repository:

Command Line:
```
git remote add origin https://github.com/username/repo.git
```

GitHub CLI:
```
gh repo create my-new-repo --public --source=. --remote=origin
```

VS Code:
1. Go to Source Control view
2. Click on "..." and select "Remote > Add Remote"
3. Enter the remote repository URL

### Push

Pushing is the act of sending your committed changes to a remote repository.

Command Line:
```
git push -u origin main
```

GitHub CLI:
```
gh repo sync
```

VS Code:
Click on the "Sync Changes" button in the Source Control view

### Pull

Pulling fetches changes from a remote repository and merges them into your local branch.

Command Line:
```
git pull origin main
```

GitHub CLI:
```
gh repo sync
```

VS Code:
Click on the "Sync Changes" button in the Source Control view

## Common Scenarios 
- Merging latest changes: https://learngitbranching.js.org/?gist_level_id=8a76ab5156b88c40d8778c0fd4994eea 
- Pushing latest changes (Merge workflow): https://learngitbranching.js.org/?gist_level_id=9aa3172377e9fef2f6f988c149cd5c87 
- Merging latest changes: https://learngitbranching.js.org/?gist_level_id=8a76ab5156b88c40d8778c0fd4994eea 
Pushing latest changes (Merge workflow): https://learngitbranching.js.org/?gist_level_id=9aa3172377e9fef2f6f988c149cd5c87 
Pushing latest changes (Rebase workflow): https://learngitbranching.js.org/?gist_level_id=51d417518efefdb6f5acefdfa22d7d73Pushing latest changes (Rebase workflow): https://learngitbranching.js.org/?gist_level_id=51d417518efefdb6f5acefdfa22d7d73

## Conclusion

This introduction covers the basics of Git, explaining its importance in large projects and walking through fundamental operations. As you continue to work with Git, you'll discover more advanced features and workflows that can further enhance your development process.

Remember, the key to mastering Git is practice. Don't be afraid to experiment in a test repository to better understand how these commands work!
