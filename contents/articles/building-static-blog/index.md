---
title: Static html blog
author: david
date: 2014-01-10
template: article.jade
---
After 2 years of inactivity, I decided to resurrect my blog as a place to store technical snippets.  Previously I wrote my blog using [Jekyll](http://jekyllrb.com/), but did not get on with Ruby and constant Gem updates, so am giving Wintersmith a try, it's built on top of node.js, easy to install and under active development.

Last time I ground to a halt because my laptop was stolen before I backed up the code anywhere, so I'll be pushing the source to GitHub and trying out 

The obvious place to store it was


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

template archive.jade: /Users/david/dev/spiraltechnology-website/templates/layout.jade:1
  > 1| !!! 5

Looks like the version in nom is not yet up to date

nano -w /Users/david/dev/spiraltechnology-website/templates/layout.jade
and replace !!! 5 
with doctype html
Welcome to your new blog! This is the default blog template with RSS, pagination and an archive. There are other templates available -- run `wintersmith new --help` to list them.

---
