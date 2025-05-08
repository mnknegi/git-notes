
# Git Cheetsheet

Git is a free and open source distributed version control system.

## Difference between distributed and centralized version control system

A centralized version control system has one central server that stores all the versions of a project, and developers connnect to this server to get the latest copy or push their changes.

e.g. CVS(Concurrent Versions System), Subversion(SVN) 

Key characteristics of certralized version control system:

- Single central repository
- All operations(commit, update etc) need a connection to the central server.
- Easy to control access and permission.
- Risk of data loss if the central server fails(unless you have backups).

Workflow:

Developers -> connect to server -> checkout code -> make changes -> commit to server

A distributed version control system allows every developer to have a full local copy(clone) of the entire repository, including its complete history.
e.g. Git, Mercurial

Key characteristics of distributed version control system:

- Every developer has the full project history locally.
- Work offline without a network connection.
- Changes can be committed locally and later pushed to a shared remote repository.
- Better resilience: if the central server fails, any local copy can restore it.

Workflow:

Developers -> clone repo -> make local commits -> push/pull to/from remote repo

Summar of differences:

|           Feature          |          Centralized          |          Distributed         |
|----------------------------|-------------------------------|------------------------------|
|Repository location         |Single central server          |Each user has full local copy |
|Offline work                |Limited(needs server)          |Full support(local commits)   |
|Performance(local ops)      |Slower(depends on server)      |Faster(local history)         |
|Failure recovery            |Server failure is critical     |Any clone can restore repo    |
|Collaboration style         |Direct to central server       |Push/pull between repos       |

## SETUP commands

Configuring user information used across all local repositories.

> git config --global user.name "[firstname lastname]"

e.g. git config --global user.name "John Doe"

This command set your name in Git's configuration, which Git will then use to identify you as the author of your commits.

- git config: runs the Git configuration command.
- --global: applies this setting for all the repositories on your machine(global git config).
- user.name: the configuration key for the user's name.
- "[firstname lastname]": the name value you want git to use.

Note: this is saved in your global Git config file:

~/.gitconfig

You can check it with:

> git config --global --list

or open ~/.gitconfig

If you omit --global, the setting applies only to the current repository(local config).
This is purely for commit authorship metadata - it does not connect to GitHun accounts automatically.

> git config --global user.email "[valid-email]"

e.g. git config --global user.email "john.doe@gmail.com"


## INIT

> git init

Initialize an existing directory as a Git repository.

> git clone [url]

Retrieve an entire repository from a hosted location via URL.


## STAGE AND SNAPSHOT

> git status

Show modified files in working directory, staged for your next commit.

> git add [file]

This command is used to stage all or selected files for your next commit.

> git reset [file]

unstage a file or all files while retaining the changes in working directory.

```
git add main.swift
git reset main.swift
```

Note: `git reset [file]` unstage single file while `git reset` unstage all the files.

> git restore

This command is used to restore or discard changes in your working directory or the staging area.
