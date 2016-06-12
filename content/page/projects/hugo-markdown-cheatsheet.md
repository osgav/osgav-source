+++
author = "osgav"
comments = false
date = "2016-06-11T16:40:05Z"
draft = false
share = true
slug = "hugo-markdown-cheatsheet"
title = "Hugo Markdown Cheatsheet"

+++

[< back to projects](/page/projects)

---

**TL;DR** there is a cheatsheet for Hugo Markdown available in my github (actually not yet, but will be soon), transcribed from https://sourceforge.net/p/hugo-generator/wiki/markdown_syntax/ (not all of it - and a couple of bits from gohugo docs)

You can make this particularly handy by doing something like this:

```
$ tree osgav/content
osgav/content
├── page
│   ├── hugo-markdown-cheatsheet.md
│   └── projects.md
└── post
    ├── cheatsheet.md
    ├── whois-osgav.md
    └── zerodots.md
```

Keep a copy of `cheatsheet.md` as a draft post, with a date in the future - this will make it the most recent post in your blog, so it will be the first post you see when testing locally with `hugo server` (and passing in the `--buildDrafts` parameter).

```
$ head content/post/cheatsheet.md
+++
author = "osgav"
date = "2070-01-01T00:00:00Z"
draft = true
slug = "cheatsheet"
tags = ["formatting-cheatsheet-dont-undraft"]
title = "cheatsheet"

+++
```
![hugo cheatsheet draft](/images/hugo_cheatsheet_draft.png)
![hugo cheatsheet](/images/hugo_cheatsheet.png)

---

[< back to projects](/page/projects)

