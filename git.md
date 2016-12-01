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
