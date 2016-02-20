# git2

Ever wanted to handle multiple git repositories in one single directory.

For example, if you deploy a software with git, you may not want to add the configuration into that repository.

Our idea: Just initialise a second git repository in the same directory and call it `.git2`.

## Usage

Use `git2` just like `git`.

For example, init a new repository:

```sh
git2 init .
```

## Options

  * Environment Variable `GITTWO_DIRNAME`: Dirname and acronym for the current (second) git repository.

## How it works

First, git2 tries to locate the git2 `.git2` repository.
Following it exchanges to .gitignore and .gitattribute files.
After that it executes the real git command (with a custom GIT_DIR environmnet). 
Finally, it reexchanges to dot git files.

To ignore files from the first git repository, all it's files are added to the `.git2/info/exclude` file.

