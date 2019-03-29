# sh

<!-- TOC -->

## Table of Contents

- [Killing background processes](#killing-background-processes)
- [Piping things through xargs](#piping-things-through-xargs)
- [How to clone all an organization's GitHub repositories](#how-to-clone-all-an-organizations-github-repositories)
- [Open last file in _posts](#open-last-file-in-_posts)
- [Wordcount for all markdown files in a directory](#wordcount-for-all-markdown-files-in-a-directory)
- [Symlinking](#symlinking)
- [Get all branches from a remote repository without cloning](#get-all-branches-from-a-remote-repository-without-cloning)

<!-- /TOC -->

#### Killing background processes

    ps -eaf | grep <process>

Example:

    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 31798     1   0  5:10PM ??         0:00.36 ipfs daemon
      501 32228 31854   0  5:10PM ttys000    0:00.00 grep ipfs
    The-Atrium-of-Time:~ richard$ kill 31798
    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 32248 31854   0  5:10PM ttys000    0:00.00 grep ipfs

#### Piping things through xargs

You like making massive lists of repos, using `github-repositories`. You should make a way to automatically get and pipe these, but until then, make a file with a list of repos newline-delimited:

```
RichardLitt/example
RichardLitt/example2
```

And then do this:

```sh
< repos.md xargs -n1 hub clone
```

This will clone. `git clone` doesn't work because _something about aliases_.

#### How to clone all an organization's GitHub repositories

```
github-repositories orbitdb -u | xargs -n1 git clone
```

#### Open last file in _posts

```sh
subl $(find `pwd`/_posts | tail -1)
subl $(ls -d -1 $PWD/_posts/** | tail -1)
```

#### Wordcount for all markdown files in a directory

	find . -type f -exec cat {} + | wc -l

#### Symlinking

Don't try and simlink to /usr/bin; you'll get an unhelpful 'Operation not permitted', even with `sudo`. Instead, use `/usr/local/bin`.

#### Get all branches from a remote repository without cloning

```sh
< repositories.md xargs -n1 -I url sh -c "printf '\n#### %s\n' url; git ls-remote url 'refs/head/*'" > repo-refs.md
```

This can also be modified to show all pulls, tags, and and refs. Repositories should be a list of remote urls.

#### Show folders in current directory which are not git folders

```sh
find . -mindepth 1 -maxdepth 1 -type d '!' -exec test -e "{}/.git/config" ';' -print
```

#### Watch and star all repositories in an org

```sh
npm i -g watch-github-repos github-star-repo github-repositories
watch-github-repos --org --watch RichardLitt --token=$WATCH_GITHUB_REPOS
github-repositories RichardLitt -u > repos.md
# Manuall clean by removing https://github.com/ ## Fix this, maybe
cat repos.md | xargs -n1 ghstar
rm repos.md
```
