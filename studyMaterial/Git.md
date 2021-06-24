# Git

Git is distributed version control software. Version control is a way to save changes over time without overwriting previous versions. Being distributed means that every developer working with a Git repository has a copy of that entire repository - every commit, every branch, every file. 

It helps you track different versions of your code and collaborate with other developers.

If you are working on a project over time, you may want to keep track of which changes were made, by whom, and when those changes were made. This becomes increasingly important if you end up having a bug in your code! Git can help you with this.

## Some important definitions: 

**Repository:** The repository is the .git folder inside our project folder. It will track all the changes made to the files in our project and record that history over time. The repository that we have on our computer is referred to as the local repository.

**Commit:** A commit is a version of your project. It represents a standalone version of your project and has a reference to all the files and folders that are a part of that version.

**Branch:** A branch is a pointer to a commit. The default branch in Git is called master or main.

### Basic Git commands

To use Git, developers use specific commands to copy, create, change, and combine code. Here are some common commands for using Git:

- `git init` initializes a brand new Git repository and begins tracking an existing directory. It adds a hidden subfolder within the existing directory that houses the internal data structure required for version control.
- `git clone` creates a local copy of a project that already exists remotely. The clone includes all the project’s files, history, and branches.
- `git add` stages a change. Git tracks changes to a developer’s codebase, but it’s necessary to stage and take a snapshot of the changes to include them in the project’s history. This command performs staging, the first part of that two-step process. Any changes that are staged will become a part of the next snapshot and a part of the project’s history. Staging and committing separately gives developers complete control over the history of their project without changing how they code and work.
- `git commit` saves the snapshot to the project history and completes the change-tracking process. In short, a commit functions like taking a photo. Anything that’s been staged with `git add` will become a part of the snapshot with `git commit`.
- `git status` shows the status of changes as untracked, modified, or staged.
- `git branch` shows the branches being worked on locally.
- `git merge` merges lines of development together. This command is typically used to combine changes made on two distinct branches. For example, a developer would merge when they want to combine changes from a feature branch into the main branch for deployment.
- `git pull` updates the local line of development with updates from its remote counterpart. Developers use this command if a teammate has made commits to a branch on a remote, and they would like to reflect those changes in their local environment.
- `git push` updates the remote repository with any commits made locally to a branch.

## Tagging

Like most VCSs, Git has the ability to tag specific points in a repository’s history as being important. Typically, people use this functionality to mark release points (v1.0, v2.0 and so on). 
Git supports two types of tags: lightweight and annotated.

A lightweight tag is very much like a branch that doesn’t change — it’s just a pointer to a specific commit.

Annotated tags, however, are stored as full objects in the Git database. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG). 

**Annotated Tags**

Specify -a when you run the git tag command: $ git tag -a v1.4 -m "my version 1.4"
The -m specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

**Lightweight Tags**

This is basically the commit checksum stored in a file — no other information is kept. To create a lightweight tag, don’t supply any of the -a, -s, or -m options, just provide a tag name: $ git tag v1.4-lw

**Listing Your Tags** 

Just type git tag: $ git tag

**Tagging Later**

You can also tag commits after you’ve moved past them. To tag that commit, you specify the commit checksum (or part of it) at the end of the command: $ git tag -a v1.2 9fceb02

**Sharing Tags**

By default, the git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them. This process is just like sharing remote branches — you can run git push origin <tagname>.

**Deleting Tags**

To delete a tag on your local repository, you can use git tag -d <tagname>.

## Stashing

Often, when you’ve been working on part of your project, things are in a messy state and you want to switch branches for a bit to work on something else. The problem is, you don’t want to do a commit of half-done work just so you can get back to this point later. Stashing takes the dirty state of your working directory — that is, your modified tracked files and staged changes — and saves it on a stack of unfinished changes that you can reapply at any time (even on a different branch).

- **Push a new stash:** run *git stash* or *git stash push*. At this point, you can switch branches and do work elsewhere; your changes are stored on your stack. 
- **See which stashes you’ve stored:** use *git stash list.*

- **Reapply the one you just stashed** by using the command *git stash apply*. If you want to apply one of the older stashes, you can specify it by naming it, like this: git stash apply. If you want to apply one of the older stashes, you can specify it by naming it, like this: git stash apply stash@{2}. If you don’t specify a stash, Git assumes the most recent stash and tries to apply it.

- **To remove a stash**, you can run *git stash drop* with the name of the stash to remove. You can also run *git stash pop* to apply the stash and then immediately drop it from your stack.

### Creating a Branch from a Stash

You stash some work, leave it there for a while, and continue on the branch from which you stashed the work, you may have a problem reapplying the work. If the apply tries to modify a file that you’ve since modified, you’ll get a merge conflict and will have to try to resolve it. If you want an easier way to test the stashed changes again, you can run *git stash branch <new branchname>*, which creates a new branch for you with your selected branch name, checks out the commit you were on when you stashed your work, reapplies your work there, and then drops the stash if it applies successfully.

## Hooks

Git hooks are scripts that Git executes before or after events such as: commit, push, and receive. Git hooks are a built-in feature - no need to download anything. Git hooks are run locally.

Every Git repository has a .git/hooks folder with a script for each hook you can bind to. When you initialize a new repository with git init, Git populates the hooks directory with a bunch of example scripts, many of which are useful by themselves; but they also document the input values of each script. 

You're free to change or update these scripts as necessary, and Git will execute them when those events occur.

To enable a hook script, put a file in the hooks subdirectory of your .git directory that is named appropriately (without any extension) and is executable. From that point forward, it should be called.

Here's a list of hooks you can attach scripts to:

-  [applypatch-msg](https://github.com/git/git/blob/master/templates/hooks--applypatch-msg.sample)
- [pre-applypatch](https://github.com/git/git/blob/master/templates/hooks--pre-applypatch.sample)
- [post-applypatch](https://www.git-scm.com/docs/githooks#_post_applypatch)
- [pre-commit](https://github.com/git/git/blob/master/templates/hooks--pre-commit.sample)
- [prepare-commit-msg](https://github.com/git/git/blob/master/templates/hooks--prepare-commit-msg.sample)
- [commit-msg](https://github.com/git/git/blob/master/templates/hooks--commit-msg.sample)
- [post-commit](https://www.git-scm.com/docs/githooks#_post_commit)
- [pre-rebase](https://github.com/git/git/blob/master/templates/hooks--pre-rebase.sample)
- [post-checkout](https://www.git-scm.com/docs/githooks#_post_checkout)
- [post-merge](https://www.git-scm.com/docs/githooks#_post_merge)
- [pre-receive](https://www.git-scm.com/docs/githooks#pre-receive)
- [update](https://github.com/git/git/blob/master/templates/hooks--update.sample)
- [post-receive](https://www.git-scm.com/docs/githooks#post-receive)
- [post-update](https://github.com/git/git/blob/master/templates/hooks--post-update.sample)
- [pre-auto-gc](https://www.git-scm.com/docs/githooks#_pre_auto_gc)
- [post-rewrite](https://www.git-scm.com/docs/githooks#_post_rewrite)
- [pre-push](https://www.git-scm.com/docs/githooks#_pre_push)

Git Cheat Sheet: https://training.github.com/downloads/github-git-cheat-sheet/

Git Manuals:

https://git-scm.com/book/en/v2

https://guides.github.com/introduction/git-handbook/

https://github.com/git-guides/

Writing and formatting on HitHub: https://docs.github.com/es/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax

Life-saver: https://ohshitgit.com/



