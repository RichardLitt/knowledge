# Using `hub` with GitHub enterprise

Using [hub](https://github.com/github/hub) will make using git and GitHub easier. However, setting it up to work with GitHub Enterprise can be a pain. Here is what worked for me.

### `~/.gitconfig`

First, let's use a dedicated folder for all of our GitHub Enterprise repositories for Corp. In your `.gitconfig`, set this:

```
[hub]
    host = github.corp.org
    protocol = ssh
[includeIf "gitdir:~/src/corp/**"]
    path = config.corp
```

This will automatically pull up a special config for Corp. It will also enforce the ssh protocol, if your corp needs that.

### `~/.config/hub`

Now we need to have `hub` specific settings.

```
github.com:
- user: RichardLitt
  oauth_token: <token>
github.corp.org:
- user: rlittauer
  oauth_token: <token>
```

The OAuth token should be set on GitHub, and have the `repo` permissions. You don't need more permissions than that.

### `~/.config/git/corp`

Now, make a new file for git configurations, which we referenced in `~/.gitconfig`.

```
[user]
    email = richard@corp.org
[hub]
    host = github.corp.org
[url "git@github.corp.org:"]
    insteadOf = https://github.corp.org/
```

That should do it! You ought to be all set.
