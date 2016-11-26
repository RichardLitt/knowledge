# Git

### Viewing unpushed git commits

This is specifically for checking if the folder you are in has any unpushed branches. This is useful in case you have duplicate directories for some reason, and want to delete one but make sure you won't be losing any work.

If you want to see all commits on all branches that aren't pushed yet, you might be looking for something like this:

    git log --branches --not --remotes

### Random

Git commit without hooks: `git commit -n`

Git diff without folders: `git diff master..gh-pages !(build|examples)`