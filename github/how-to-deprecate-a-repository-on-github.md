# How To Deprecate A Repository on GitHub

Once, you had a shining, beautiful repo, full of hope and joy. But now you need to state cleanly and clearly that a repository is no longer going to be maintained, isn’t going to be looked at, and should no longer be of interest to anyone. It is kept for archival purposes.    
  
GitHub needs to get around to making a `DEPRECATED` tag. They haven’t done this yet, although there’s clearly a gross amount of interest - just look at [isaacs/github#144.](https://github.com/isaacs/github/issues/144). 

There’s a few reasons you could be deprecating a repository, and the steps you should take for them are different. For a project that no one uses, some simple documentation changes should do the trick. For a project that is actively in use which you want to step away from or deprecate entirely, there’s a bit more legwork.  
  
Note: I have made a [checklist](https://gist.github.com/RichardLitt/741cb6f2fd6c75c0c5f51958160853a9) from this article you can follow. You can edit this article on [GitHub](https://github.com/RichardLitt/knowledge/blob/master/github/how-to-deprecate-a-repository-on-github.md) or [read it on Medium](https://medium.com/maintainer-io/how-to-deprecate-a-repository-on-github-8f0ceb9155e).
    
### Deprecating a project no one uses  

Here’s what you do to deprecate an inactive repository.
  
- **Change the GitHub description**. This is often the first thing people see for the repository, and the first line that people will see if looking at the repository in the Organization view.
The most important thing to do is to add the word `DEPRECATED` at the front of the description. This clearly marks it will not be updated. You can also add an emoji to it. `⛔️ DEPRECATED <former description>` makes it pop out a bit more.  
- **Add GitHub topics**: `deprecated`, `obselete`, and `archived` are all good ones.  
- **Edit the title of the README**. Remove the current title, and instead write `# DEPRECATED`.  
- **Add a reason to the README**, at the top, stating that: “This is no longer supported, please consider using XXX instead.” If there is a reason for deprecating the repository, add it here. It should be unambiguous to anyone visiting the repository that it will not be maintained or updated again.    
- **Update any licenses or liability wavers**. By updating them, you make sure that they are legally valid, going forward. This can stop questions popping up in the years to come, if people rediscover the project and want to use it. Note: I am not your lawyer. If you have questions, seek legal counsel.  
- **Add a `no-maintenance-intended` badge.** This is another visible way of pointing out that you’re not going to keep updating this project, and the idea comes from  [unmaintained.tech](http://unmaintained.tech).

I’ve also heard of people add a large image saying `Deprecated` in some way to the README. This might be a good move, if you’re so inclined. Have fun with it.
  
### Deprecating active projects

You, as an open source contributor, are not under any moral obligation to continue the work, in most cases, even if people are using a project. You have a right to walk away from your project. However, you can still be kind, and the way you walk away from a project can determine how you remember a project. It is important to feel that you did all you could to make the project thrive, if it could have.

If you are no longer interested in maintaining the repository, but users are still actively using it, open an issue a few weeks or a month before you plan on deprecating the repo. State clearly that you are not interested in continuing maintenance of the project, and you are going to close the project down. You can do a few things: 

- **Ask people to use a different project**, which solves the same problem as yours (and hopefully has more features and better UX).  
- **Ask people to fork** the project and take over maintenance going forward.  
- **Ask contributors to step up** to become collaborators and maintainers. Offer them access to the repository, so that they can maintain it for you, while you offload your responsibilities.  

If you are interested in the project continuing, but don’t need it to be tagged with your name anymore, you can do this:

- **Move ownership** of the repository to another maintainer. If, for instance, the project was at RichardLitt/awesome-project, you could give it to someone you trust who is maintaining it. Do this in the repository settings. For instance, I could ask my friend Gregor to take it over, and move it to gr2m/awesome-project.  
- **Set up an organization** to take over the project. If the project is large, and there is an ecosystem around it, it is sometimes smart to set up an organization to take if over, so that it is clear that you are not in charge of it, but all the members of the organization. This is a similar option to moving it to another maintainer, but it stops you from needing to choose one sole maintainer to take it over.

### If it is a JavaScript project on npm

- **Use [`npm deprecate`](https://docs.npmjs.com/cli/deprecate)** to deprecate it. Don’t forget to publish.
- **Edit the description** to include the badge, as on GitHub. `⛔️ DEPRECATED <former description>` would be useful. Don’t forget to publish a patch with the new metadata.

### Other options

Until GitHub implements an archive feature publicly, there are a few other options for deprecating repositories.

- **Change the repo name**. I would not recommend changing the title of the repository to something like `<project>-deprecated`, although I have seen this before and it is something you could consider. I find it affects recall for anyone who knew of the project and wants to find it later, and it is not as useful given the above steps are done.

- **Make an archive organization**. One is to make a project-archive organization, and move all repositories there. This makes it clear in the name that the repo has been archived, but doesn’t let the old cruft stick around in your old organization. 

- **Make it private.** Another possible step is to make any deprecated repository private. This is useful if the code could be considered dangerous, or if the information in it will lead new developers astray in ways which really aren’t useful. The benefits of making a repository private is that your team - the people who are most likely to have known about the project and least likely to misunderstand it - can still see it.
  
### Anything else  

Nope, that’s it. You’ve deprecated your project. Go and enjoy your life, make new things, and don’t lose any sleep over it.
