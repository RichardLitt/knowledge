# sh

### Killing background processes

    ps -eaf | grep <process>

Example:

    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 31798     1   0  5:10PM ??         0:00.36 ipfs daemon
      501 32228 31854   0  5:10PM ttys000    0:00.00 grep ipfs
    The-Atrium-of-Time:~ richard$ kill 31798
    The-Atrium-of-Time:~ richard$ ps -eaf | grep ipfs
      501 32248 31854   0  5:10PM ttys000    0:00.00 grep ipfs

### Piping things through xargs

You like making massive lists of repos, using `github-repositories`. You should make a way to automatically get and pipe these, but until then, make a file with a list of repos newline-delimited:

```
RichardLitt/example
RichardLitt/example2
```

And then do this:

```sh
cat repos | xargs -n1 hub clone
```

This will clone. `git clone` doesn't work because _something about aliases_.

### Open last file in _posts

```sh
subl $(find `pwd`/_posts | tail -1)
subl $(ls -d -1 $PWD/_posts/** | tail -1)
```

### Wordcount for all markdown files in a directory

	find . -type f -exec cat {} + | wc -l

### Symlinking

Don't try and simlink to /usr/bin; you'll get an unhelpful 'Operation not permitted', even with `sudo`. Instead, use `/usr/local/bin`.
### Symlinking

Don't try and simlink to /usr/bin; you'll get an unhelpful 'Operation not permitted', even with `sudo`. Instead, use `/usr/local/bin`.
### Symlinking

Don't try and simlink to /usr/bin; you'll get an unhelpful 'Operation not permitted', even with `sudo`. Instead, use `/usr/local/bin`. 
