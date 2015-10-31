## So you need to change your commit

Here are your options:

* Add another commit on this branch and then push to this branch.  
* Manually fix your changes, amend, and force push.  
* Add another commit, and then squash commits.  
* Interactively checkout the previous commit, remove lines that aren't wanted, stage, amend, and force push.  
* Interactively rebase.  
* Close this PR, commit again on a new branch, open another PR.  
* Wait for someone else to do this for you, and then have them credit you.  

Make sure you're on your branch, and currently pointing to the commit that was used to make this PR.

### Option 1: Add another commit and push to your PR branch

This is normally the thing to do. 

```sh
$ echo 'these are some edits' >> your_file.md  
$ git commit -m 'Edits are the best'  
$ git push origin HEAD  
```

What this does is provide you with a very clear history of what was committed where, and anyone can see this in the PR and in the future history of the project if it is merged in. 

However, for things like spelling edits, line removals, or general small nitpicky things that the maintainers want you to do, having an extra commit may not be the best option. Some repositories like to have a very clear history, where each commit shows something meaningful that happened. A second commit removing a space, added by accident in the previous commit, isn't really useful for anyone. 

(On a side note: `git push` is enough if you're on newer git versions and the remote matches local. `git push origin HEAD` is just longhand for pushing to whatever branch you're currently on. If you're using a different naming scheme for `origin` and `upstream`, you will need to update that accordingly, of course.)

### Option 2: Manually add changes, amend, and force push

This is where force pushing comes in. While most git guides tell you that "Force pushing is the worst thing in the world, and it makes you a Sith Lord if you use them, and we will find you and hunt you down", really, it makes sense in situations where a commit on a non-merged PR should be changed. No one is going to be touching that PR, so you don't have to worry about dirtying past history. The only person likely to be touching that branch will be you.

A lot of people complain that then the comments made by the maintainers will be lost. Technically, they are saved on GitHub in outdated diffs, if anyone wants to see them, although they won't be in the git history itself (which makes them less accessible and useful). But, more relevantly, they often aren't that important. Is it important that a maintainer told you to remove a trailing space? I don't think so. Most maintainers I know would agree with me. 

So, you can manually change your file. 

```sh
$ vi your_file.md  
# Do the edits you need to, here, and then type `:wq`.  
# There's no reason you can't use your usual editor to edit the file.  
$ git add -A  
$ git commit --amend  
```

You see that we added the edits to git's staging area, with `git add -A`. (If you ever want to know what a git command flag means, type the equivalent of `man git-add`. The git manuals aren't really all that bad.) Then, we typed `git commit --amend`. `--amend` is your friend - it lets you change a commit by adding to it, editing the commit message, or even doing things like changing who made the commit and when it was committed. This only changes things locally, which means you have to be careful about pushing elsewhere or expecting anyone else to have your changes. But don't worry - git will warn you if you try to run `git push origin HEAD` at any point, as it knows that the commit has been changed, and you should know what you're doing before pushing.

`--amend` opens up the interactive commit message environment you are used to from `git commit`. Change the message as you see fit; you'll see your edits are now actually part of the commit, too. When you save (`:wq` again), it will register that a new commit has been logged. 

Now comes the part you normally shouldn't do, but since the maintainers have asked you, and since you know it is to your own branch, and since you're not too worried about being a Sith lord: `git push -f origin HEAD`. This will tell git to not care that this is a different commit. Git will overwrite the remote commit with your commit, and now you'll see that the PR has also automatically been updated on GitHub. The old comments telling you to change stuff are now in an outdated diff, the code shows the most recent version, and you're ready to merge. Everyone wins.

### Option 3: Committing and squashing

Another option you can do, which is a bit more standard and which you may be used to, is to edit your file, and then make a new commit. You can even make as many commits as you like, really. However - like we said earlier, some maintainers want a clean history. You can clean up your history by squashing commits, and then force pushing.

```sh
$ echo '1' >> your_file.md  
$ git add -A && git commit -m 'init'  
$ echo '2' >> your_file.md  
$ git add -A && git commit -m '1'  
$ echo '3' >> your_file.md  
$ git add -A && git commit -m '2'  
```

What you've just done here is made three commits, with three changes. But say you only want the initial commit to be logged, but you want all of the changes in the subsequent two? So, you want one commit for this final file:

```sh
$ cat your_file.md  
1  
2  
3  
```

This is easy. What you need to do is to find the SHA for the commit you want. Type `git log`. 

```sh
$ git log  
commit a64e0ba789c7d6a38190a87cf073de83f9e74e65  
Author: Richard Littauer <richard.littauer@gmail.com>  
Date:   Fri Oct 30 13:01:26 2015 -0400  
  
    2  
  
commit b55c3647991830ba50c12b3755ab00c8c537caab    
Author: Richard Littauer <richard.littauer@gmail.com>  
Date:   Fri Oct 30 13:01:24 2015 -0400  
  
    1  
  
commit 7bedf0d423deb3e7e81fc3ba980a92252b684a83  
Author: Richard Littauer <richard.littauer@gmail.com>  
Date:   Fri Oct 30 13:01:24 2015 -0400  
  
    init  
```

Copy the final commit SHA. As with all git SHAs, you can actually just copy the first 6 letters. Then, type this:

```sh
$ git squash 7bedf0  
```

What this will do is squash your commits down to the commit `7bedf0`, but keep all of the subsequent changes (in the staging area). Let's take a look:

```sh
$ git log  
commit 7bedf0d423deb3e7e81fc3ba980a92252b684a83  
Author: Richard Littauer <richard.littauer@gmail.com>  
Date:   Fri Oct 30 13:01:24 2015 -0400  

init  
$ cat your_file.md   
1  
2  
3  
```

Sweet! You now have one commit, but `your_file.md` looks like you want it to. However, if we run `git diff --cached`, we can see the staged edits:

```sh
$ git diff --cached  
diff --git a/your_file.md b/your_file.md  
index d00491f..01e79c3 100644  
--- a/your_file.md  
+++ b/your_file.md  
@@ -1 +1,3 @@  
1  
+2  
+3  
```

Looks like the changes in the second two commits are staged, but not committed. Well, now we just do `git commit --amend`, save, and then force push. Easy as pie.

But what if you don't want to edit your file manually, like we did in `vi your_file.md`? Say there are a lot of small changes you have to make, or it's just tedious work.

### Option 4: Interactively checkout and amend

Well, here you can do some cool stuff.

```sh
$ git checkout -p HEAD~1  
```

What this does is to compare your current commit (your `HEAD`) to your last commit (`HEAD~1`). It diffs the two commits, and adds the previous commits lines which are different, removing lines from your current commit. This is like applying the inverse of your current commit. `-p` means patch, and it interactively selects hunks from the diff. This is useful, because it means you can choose which lines you want to keep, and which you don't.

When you type `git checkout -p HEAD~1`, it will give you an option for each hunk in the file. This looks like this: `Apply this hunk to index and worktree [y,n,q,a,d,/,e,?]?`. I would suggest pressing `e`, which opens up your editor. There, it gives you these options:

```vi
8 # To remove '-' lines, make them ' ' lines (context).  
9 # To remove '+' lines, delete them.  
10 # Lines starting with # will be removed.  
```

If you would like a line to stay in your commit, replace the `-` in front of it with a space. If you would like a line that was deleted to be removed, simply delete it (in vi, you can do this by typing `dd` while on that line). This might take a bit of mental work to get used to, as removing a line while checking out a previous commit is the same as effectively keeping the line in the current commit. If you ever have any difficulty, you can restart the process by doing `git reset --hard`.

Once you have removed the lines which you wanted to - say, for instance, lines which where you had accidentally changed a word - add the new changes to the staging area by typing `git add -A`. Then, commit them using the amend function we mentioned prior, and finally, force push them. It might be smart to look at the commit diff from the previous commit before force pushing: do this by diffing the two commits with `git diff HEAD~1..`. Then:

```sh
$ git add -A  
$ git commit --amend  
$ git push -f origin HEAD  
```

If you don't want the commit command to open up the editor because you're not changing anything, you can also use `git commit --amend --no-edit`, but that's a bit more dangerous.

### Option 5: Interactively Rebase

Another option is to interactively rebase. Normally, you'll want to do this if the branch you forked off of has changed, and you're being asked to update your commit, especially if there are changes. Rebasing is a bit more complicated, and I think you'd appreciate graphs for this, so take a look at [this short post](https://www.atlassian.com/git/tutorials/rewriting-history/git-rebase-i) on it. A good way to think of rebasing is as a merge and a squash, rolled into one, while also using the hunk methods we saw in `git checkout -p`.

If you have conflicts, this might get a bit hairy. That's OK though! Everything will eventually be alright. I'm not going to go into how to do this here, because I think the post above does it very clearly. Feel free to message me if you would like me to fill this out.

### Option 6: Open a new PR

This is frowned upon by most maintainers, because it creates more work for the maintainer, and quickly leads to a lot of random PRs being opened for what might have been a very simple problem. This is also work for you. You need to delete your old branch, close the PR, edit your commit manually in whatever way you see fit, and then push to a new branch, and reopen the PR. That's a lot of effort. 

**This should be your last resort** - only do this if the maintainer of the repository says it is OK. An example of where this might happen is if the PR has moved away significantly from the original solution it provided. 

### Option 7: Wait for someone else to help

Of course, for some fixes, maintainers can help you, too. This often happens when a maintainer wants to close a PR, but there's a small thing that needs to be changed, and the original filer of the PR has moved to Ethiopia. What a maintainer can do in these situations is this: they checkout your branch, and pull down your changes onto your local machine. Then, they manually edit the file, and edit your commit message, amending it, before merging it into their up-to-date main branch and pushing. This will make the PR look like it has a conflict, but your code and your attribution will still be in the git history for that repository. Sometimes, people do this and then let you know in the PR comment thread by saying `Landed in <commit_sha>`, where the commit_sha is the merge.

```sh
$ git checkout -b your-username-master master  
$ git pull https://github.com/your-username/repo.git master  
$ echo 'This PR needs this line' >> your_file.md  
$ git commit --amend --no-edit  
$ git checkout master  
$ git merge your-username-master  
$ git push origin master  
```

Another thing maintainers can do is to actually add content in a new commit, and then make it look like you made it. They can do this by using this command:

```sh
$ git commit --amend --author \"Your Name <your_email@email_provider.com>\"  
```

Don't worry - it'll say on GitHub and in the commit, when they push, that they pushed a commit that you made, so in a sense, you are dual attributors.

If you got this far, though, it's likely they didn't need to do that, and that you were able to fix your PR yourself. I hope so!

Let me know if any of this is confusing. I'm happy to edit it and make things more clear, or to fix the inevitable errors I made describing this process.
