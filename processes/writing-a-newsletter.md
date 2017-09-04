# Writing A Newsletter

- [ ] Open up IA Writer
- [ ] Write your content in markdown
- [ ] Move it to a separate file somewhere
  - `docs/newsletter-archive` if going out on `practice`
- [ ] Edit file. Add links, fix spelling.
- [ ] Add an image. You'll need it for Medium to look good.
- [ ] Replace smart quotes if they exist
    `quotes file.md`
- [ ] Push to GitHub

## If sending by TinyLetter

- [ ] Convert Markdown to HTML
- [ ] Send preview

```sh
showdown makehtml -i file.md -o file.html
tiny --title=<title> --body=file.html
# id of letter sent
```

- [ ] Check preview in Gmail

```sh
tiny -send --id=<id>
```

## If posting to blog:
- [ ] Go to blog folder
- [ ] `rake post title=""`
- [ ] Add frontmatter to post
- [ ] Test by running `jekyll serve`
  - [ ] Go to http://localhost:4000
- [ ] Push to GitHub
- [ ] Get URL

## If posting to Medium:
- [ ] Add frontmatter to markdown file: `title`, `created`, `canonicalUrl`
- [ ] TODO Fix canonicalURL - doesn't seem to work
- [ ] Use [markdown-to-medium](https://github.com/yoshuawuyts/markdown-to-medium)
  - `markdown-to-medium ./title`
- [ ] Edit draft online
- [ ] Remove issues with markdown not checking double spaces after line

- [ ] Double check that it is sent out on twitter
