---
title: Static html blog
author: david
date: 2014-01-10
template: article.jade
---
After 2 years of inactivity, I decided to resurrect my blog as a place to store technical snippets.  Previously I wrote my blog using [Jekyll](http://jekyllrb.com/), but did not get on with Ruby and constant Gem updates, so am giving [Wintersmith](http://wintersmith.io/) a try, it's built on top of node.js, easy to install and under active development.

Last time I ground to a halt because my laptop was stolen before I backed up the code anywhere, so I'll be pushing the source to GitHub and trying out their pages.

<span class="more"></span>

1. Install node.js 

I chose to [download](http://nodejs.org/download/) the package and install it, but its available on  brew as well

2. Install [wintersmith](https://github.com/jnordberg/wintersmith#quick-start)

```bash
sudo npm install wintersmith -g
```

3. I decided that i'd be wanting to store the source of the website in github so I first logged on and created a new repository, then checked out the empty repository'

```bash
git clone https://github.com/davidtron/spiraltechnology-website
```

4. Create a new website, by default wintersmith will create you a basic blog structure with a plugin to render blog articles.  It complains if the directory exists, but in this case I want to populate the directory of my empty git repo, so I used the --force flag.

```bash
wintersmith new spiraltechnology-website --force
cd spiraltechnology-website
wintersmith preview
```

The first problem I had was 

```bash
template archive.jade: /Users/david/dev/spiraltechnology-website/templates/layout.jade: > 1| !!! 5
```

Looks like the version in npm is not yet up to date with the version on github.  To fix follow it's advice and *replace !!! 5* with *doctype html*

```bash
nano -w /Users/david/dev/spiraltechnology-website/templates/layout.jade
```

5. After creating some content and tweaking the layout and css, I wanted to publish my site to [github pages manually](https://help.github.com/articles/creating-project-pages-manually). Create an orphan branch of the project

```bash
cd ~/dev
git clone https://github.com/davidtron/spiraltechnology-website.git spiraltechnology-website-deploy
cd spiraltechnology-website-deploy
git checkout --orphan gh-pages
git rm -rf .
```

6. Configure wintersmith to build to the deploy directory. This is controlled by adding an output option to config.json in the root of the directory wintersmith created for us.

```javascript
{
  "locals": {
    "url": "http://www.spiraltechnology.co.uk",
    "name": "spiraltechnology",
    "owner": "David",
    "description": "simple, pragmatic, elegant code"
  },
  "output" : "../spiraltechnology-website-deploy"
  ...
}
```

7. In the source directory compile the website, it should output it into the newly created deployment directory
```bash
cd ~/dev/spiraltechnology-website
wintersmith build
```

8. Add the files in the github pages branch and push it up to the server.

```bash
cd ~/dev/spiraltechnology-website-deploy
git add *
git commit -a -m "First pages commit. WIP"
git push origin gh-pages
```
