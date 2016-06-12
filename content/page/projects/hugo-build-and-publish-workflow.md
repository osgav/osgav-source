+++
author = "osgav"
date = "2016-06-11T20:10:08Z"
draft = false
share = true
slug = "hugo-build-and-publish-workflow"
title = "Hugo Build and Publish Workflow"

+++

[< back to projects](/page/projects)

---

### building

To make building and previewing changes locally easier, I wrote a couple of short scripts. For context, I run the `hugo` commands inside a vagrant virtual machine (linux) and access the site using a web browser on the host machine (windows).

In the source for my hugo site, I have a `hugo` folder for these scripts. This makes running them similar to invoking the `hugo` command itself:

```
$ ls -1 osgav
archetypes
config.toml
content
data
hugo
layouts
public
static
themes

$ tree osgav/hugo/
osgav/hugo/
├── build-public
├── serve
└── serve-withdrafts

$ ./hugo/serve
$ ./hugo/build-public
```

As mentioned in [Hugo Markdown Cheatsheet](/page/hugo-markdown-cheatsheet), if you run `hugo server` with the parameter `--buildDrafts` then any posts or pages where `draft = true` will also be published to the blog on the local hugo server.

The `--buildDrafts` parameter is the only difference between the `serve` and `serve-withdrafts` scripts.

Both the `serve` and `build-public` scripts ignore drafts, so I can use `serve` first to preview what will be generated after I run `build-public`.

Until I take a look at live reloading, this let's me do the following to make changes and preview them - my ***build workflow:***

```
$ vi content/page/hugo-build-and-publish-workflow.md
<make edits>
$ ./hugo/serve-withdrafts
...
Press Ctrl+C to stop
<preview changes>
<ctrl+c to stop hugo server>

repeat
```
With live reload I shouldn't need to stop the server to make changes - simply saving changes <s>and refreshing the page in the browser</s> will be enough.

I use a mixture of `vi` and [Sublime](https://www.sublimetext.com/) - <s>I suspect I may use Sublime more once I configure live reload...</s> *Wrong! LiveReload is already enabled by default, but `hugo server` only seems to be able to detect changes to files made from inside my virtual machine - using Sublime on the host isn't detected, so the page is not reloaded...*

##### what's in the scripts?

**`./hugo/serve`**<br />
The `serve` scripts also use the `hugo server` parameters `--port` `--bind` & `--baseURL` which let me correctly serve the site from my vagrant virtual machine and make it accessible to the host (`1313` is actually the default port, `192.168.56.2` is required or else its only accessible inside the virtual machine - this is the virtual machine's IP on a Host-only Network that the host is also connected to. `http://192.168.56.2:1313/` overrides the value specified in `config.toml` that contains the site's public domain).

```
#!/bin/bash
hugo server --theme=casper \
--port=1313 \
--bind=192.168.56.2 \
--baseURL="http://192.168.56.2:1313/"
```

**`./hugo/serve-withdrafts`**<br />
The only difference is `--buildDrafts \`

```
...
hugo server --theme=casper \
--buildDrafts \
--port=1313 \
...
```

**`./hugo/build-public`**<br />
The `build-public` script also adds a `CNAME` file to the root of the output directory `public`. This file contains `osgav.run` which enables GitHub Pages to serve from a custom domain once its being served from the correct place in GitHub.

```
#!/bin/bash
hugo --theme=casper

# add CNAME file to public
touch public/CNAME
echo "osgav.run" > public/CNAME
```

---

### publishing

I haven't scripted the publishing steps yet - need to rename some things for better structuring - *like cleanly deploying another hugo site in another repo's `gh-pages` branch or simply not messing up this site...*

---

[< back to projects](/page/projects)

