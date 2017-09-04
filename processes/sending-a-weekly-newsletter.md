## Newsletter Process

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