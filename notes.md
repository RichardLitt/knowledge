# Notes
> A personal list of things that are useful to remember, code wise.

To use best, I suggest setting up this alias in `.bash_profile`:

```sh
  alias notes="subl ~/src/docs/notes.md"
```

As always, use your favorite text editor and adjust the path.

## IRC

### Tell
To remind someone later, use: `.tell <user> <message>`.

## To Do

- Install [Alex]() on everything

## Shell stuff

- Use jq to get pretty cool results.

    curl https://api.github.com/repos/ipfs/http-api-spec/pulls | jq '.[] | .title, .url'

## Markdown guide

- [ ] To Do
- [x] Done
- [+] Prioritize
- [>] Offloading until later
- [@RichardLitt] Waiting on @RichardLitt
- [~] Begun
