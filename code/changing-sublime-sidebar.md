# Changing Sublime's Sidebar

Sublime is awesome! However, for presentations, sometimes we want to have the sidebar be a bit bigger for presentations, so people can see what files there are. 

Here's the trick. Add this code:

```json
[
    {
        "class": "sidebar_label",
        "color": [0, 0, 0],
        "font.bold": false,
        "font.size": 30
    },
    {
        "class": "sidebar_tree",
        "row_padding": [5,15]
    }
]
```

Change `font.size` or `row_padding` as needed.

To this file: `~/Library/Application Support/Sublime Text 3/Packages/User/Default.sublime-theme`.

If it doesn't exist, create `Default.sublime-theme`.
