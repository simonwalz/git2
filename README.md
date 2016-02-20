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

The `.gitignore` and `.gitattribute` files for the second git repository are named `.gitignore_git2` and `.gitiattributes_git2`. When the git2 command is running, the files are renamed to their original names (without _git2).

### Addional commands

To see the current git2 base dir, just run
```sh
git2
```

To add an exclude file into the first git repository run:

```sh
git2 git2_exclude
```

## Options

  * Environment Variable `GITTWO_DIRNAME`: Dirname and acronym for the current (second) git repository. Default: `.git2`

## How it works

First, git2 tries to locate the git2 `.git2` repository.
Following the script exchanges the .gitignore and .gitattribute files.
After that it executes the real git command (with a custom GIT_DIR and GIT_WORK_TREE environment).
Finally, it reexchanges to dot git files.

To ignore files from the first git repository, all it's files are added to the `.git2/info/exclude` file.

