# Git Hooks

This repository provides useful hooks for automating and simplifying working with `Git` and can be used as a `template-directory` for new and already existing Git repositories.

## Available Hooks

### prepare-commit-msg

This hook automatically prepends all commit messages with the (*Jira*) ticket number when working on a feature branch. Commit messages on branches that don't follow the naming syntax (e.g. *main*) are not modified and skipped by the hook.

#### See the following example of feature branch names and the resulting commit message prefixes

|Branch Name|Commit Prefix|
|---|---|
|ticket-123-some-feature|[TICKET-123]|
|feature/ticket-456-some-other-feature|[TICKET-456]|
|bugfix/ticket-789|[TICKET-789]|
|123_some_feature|[123]|

#### Commit Message Example

```shell
git checkout -b ticket-123_new_feature
git add new_file.txt
git commit -m "Add new file"

[TICKET-123] Add new file
 1 file changed, 0 insertions(+), 0 deletions(-)
```

## Setup

Clone the repository into a local folder anywhere on your machine and configure Git. After globally setting up the Git `template-directory`, each new repository that is created by `git init` will have the hooks automatically installed.

```shell
# 1. Clone repository to a local folder
git clone https://github.com/devholland/git-template.git ~/.git-template

# 2. Specify the folder as the `templatedir` for Git
git config --global init.templatedir '~/.git-template'
```

### Use with already existing repositories

The hooks can easily be installed in an already existing Git repository by executing `git init` in the repository's folder:

```shell
# 1. Change into the already existing repository
cd /path/to/repository

# 2. Reinitialize the Git repository
git init

Reinitialized existing Git repository...
```

After reinitialization the hooks immediately work for the already existing Git repository.
