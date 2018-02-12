# Writing A Newsletter

## Table of Contents
- [Writing a weekly newsletter](#writing-a-weekly-newsletter)
- [If sending by TinyLetter](#if-sending-by-tinyletter)
- [If posting to blog:](#if-posting-to-blog)
- [If posting to Medium:](#if-posting-to-medium)

## Writing generically

- [ ] Open up IA Writer
- [ ] Write your content in markdown
- [ ] Move it to a separate file somewhere
  - `docs/newsletter-archive` if going out on `practice`
- [ ] Edit file briefly. Add links, fix spelling. You'll do a bette readthrough later.
- [ ] Add an image. You'll need it for Medium to look good.
- [ ] Replace smart quotes if they exist:
    `quotes file.md`
- [ ] Push to GitHub

## Writing a weekly newsletter

- [ ] Look at last newsletter
- [ ] Source material
- [ ] Copy template to new file in `docs/newsletter-archives/weekly`
- [ ] Write Newsletter in Markdown
- [ ] Name it: `Letters from Richard: item1, item2, more...`
- [ ] Convert Markdown to TinyLetter format

    showdown makehtml -i *.md -o *.html

- [ ] Manually go onto TinyLetter
- [ ] Add HTML code
  - [ ] Remove Title
- [ ] Send preview
- [ ] Accept preview, send file
- [ ] Save .md file into `docs/newsletter-archives/weekly`
- [ ] Send to RSS feed: 

    py ~/src/tiny-letter-tools/bin/mk-rss-feed.py http://tinyletter.com/richlitt/ > ~/src/burntfen.com/weekly.rss
    cd ~/src/burntfen.com/
    git k

## If sending by TinyLetter

Note: This automatically sends to the Practice newsletter.

```sh
# Convert markdown to HTML
showdown makehtml -i file.md -o file.html
# Remove the <h2> heading. You don't need it.
# Send the preview
tiny --title=<title> --body=file.html
# id of letter sent
```

- [ ] Check preview in Gmail

```sh
# Grab the ID from the previous step
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
