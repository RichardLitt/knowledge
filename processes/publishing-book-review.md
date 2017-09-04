# How to publish a book review

### The Fun Bit

- [ ] Read book.
- [ ] Create markdown file:

```
cd ~/docs/book-notes
sh ./new-book.sh "Author" "Title"
```

- [ ] Transcribe notes.
- [ ] Write review

### Adding to the Litt Review website

- [ ] Make a file in website

```
cd ~/src/burntfen.com
rake review title="title" author="author"
```

- [ ] Copy markdown from review to `_drafts/<title>.md`
- [ ] Save image
  - [ ] Find image on wikipedia
  - [ ] Save to `src/img/review/.`
  - [ ] Rename file in <title>.md to match filename
- [ ] Move file from `_drafts` to `_reviews`
- [ ] Preview file on local

```
jekyll serve
# Open localhost:4000/the-litt-review
```

- [ ] Commit to master, or to feature branch if saving
- [ ] Edit date to match current date (if later)
- [ ] Read once to check for spelling and grammar
- [ ] Push to master
- [ ] Copy HTML from markdown to clipboard

```
marky-markdown <file> | pb
## Attempt to automaticall get only relevant parts
# sed -e '1,/include JB/d' <file
```

### Sending the Newsletter

- [ ] Open Mailchimp and sign in
- [ ] Create new Campaign, title: `The Litt Review: <title>`
- [ ] Fill in metadata
  - [ ] Email subject: `The Litt Review: <title>`
  - [ ] Preview text: `Wherein I review <author>'s book`
- [ ] Select Simple text format
- [ ] Fill in content
  - [ ] Title: `<author> _<title>_`
  - [ ] Content: copy in html
  - [ ] Copy link from https://burntfen.com/the-litt-review
  - [ ] Bottom of content: `Original published [here](link)`
- [ ] Top right: Send preview email
  - [ ] Check preview email
- [ ] Send email
