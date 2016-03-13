---
layout: post
title: GitHub Pages
categories: webdevelopment GitHub Jekyll
---
I have for quite a while been hosting my homepage (the one you are looking at!) on my own server at home, a MacMini. I have now finally moved the site to GitHub.
<!--more-->

### The Process
The site is still created as a series of static pages by jekyll, a static site generator. I use a slightly modified version of Jekyll and a bunch of extensions.

The following assumes that you have registered on GitHub and created a repository for your site. Clone this repository using GIT or the GitHub app.

- Open a command line and make the local site directory the current directory.
- Run the jekyll instruction which creates the static site.
- Copy the resulting files into the cloned repository.
- Commit the changes and push/sync them to the gh-pages branch using GIT or the GitHub app.

I have pointed my DNS to the GitHub ip address and added a CNAME file to the website root, which contains a single line: "bracke.dk" (my domain).
The website is pushed to the gh-pages branch of repository and that branch is set as the default branch (look at the "Admin" section of your site on GitHub).

The above was not obvious to me and I found the documentation on GitHub quite confusing on this matter.
