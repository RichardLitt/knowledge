# Git

### Viewing unpushed git commits

This is specifically for checking if the folder you are in has any unpushed branches. This is useful in case you have duplicate directories for some reason, and want to delete one but make sure you won't be losing any work.

If you want to see all commits on all branches that aren't pushed yet, you might be looking for something like this:

    git log --branches --not --remotes

### Random

Git commit without hooks: `git commit -n`

Git diff without folders: `git diff master..gh-pages !(build|examples)`

### Stack Overflow answers

- [How to delete a Git branch both locally and remotely?](https://stackoverflow.com/questions/2003505/how-to-delete-a-git-branch-both-locally-and-remotely)

    ```sh
    # Remotely
    $ git push origin --delete <branch_name>
    # or
    $ git push origin :<branch_name>
    # Locally
    $ git branch -d <branch_name>
    # If you see artifacts
    $ git fetch --all --rpune
    ```

### Notes from _Pro Git_

#### Git status short

```
git status -s|--short
```

This is an interesting way of only showing the modified file names in a shorthand. Worth knowing.

#### .gitignore patterns

* You can negate a previously set pattern by using `!`
* You can void recursivity for patterns by prepending a `/`
* You can have multiple .gitignore files in a repository, in subdirectories.

#### git difftool

I don't currently know anything about different difftools, available through `git difftool`. Might be worth knowing, instead of always defaulting to manual search-and-replace.

#### git rm --cached file

This will remove the file from your staging area, but keep it locally; this is the opposite of `git rm -f file`, which will straight out delete the file.

#### git mv

`git mv file_from file_to`

This is equivalent to removing and adding again. Useful for renaming a file in git.

#### git log

* `git log -p|--patch` shows you the diffs as well as the git logs.
* `git log --stat` shows you the stats on the file additions and deletions.
* `git log --relative-date` shows you time since. Try `git log --pretty=format:"%ar"`.
