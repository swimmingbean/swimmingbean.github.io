---
layout: post
title: Create A Blog With Github Pages Part1
categories: [ themakingof ]
---
## Create a User Page in GitHub

In the spirit of incremental improvements, we'll start by creating a simple "Hello World" page hosted using github pages

0. Create a [Github](https://github.com/) account if you don't already have one.
1. [Create GitHub repo](https://help.github.com/articles/create-a-repo/) with the following name: `<github-username>.github.io`
2. Clone the repo to your local machine
```bash
git clone https://github.com/<github-username>/<github-username>.github.io.git
cd <github-username>.github.io
```
3. Create an html file with initial contents for you site
```bash
echo “Hello World” > index.html
```
4. Commit and push your file to GitHub
```bash
git add index.html
git commit
git push
```
5. Visit `https://<github-username>.github.io` using your web browser to check out your new site.

Below is what the initial SwimmingBean page looked like. At this point it's not yet a blog. There are no blog posts, no RSS feeds, no
about the author pages. To set this up using Jekyll see [part 2]({{ site.baseurl }}{% post_url 2018-11-14-Create-a-Blog-With-Github-Pages-Part2 %})

![Initially SwimmingBean user page]({{ site.baseurl }}/images/Create-a-Blog-With-Github-Pages-Part1/initial-hello-world-github-user-page.png)
