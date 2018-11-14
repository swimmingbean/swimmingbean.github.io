# Create a Blog With GitHub Pages - Part 2

In [part 1]({{ site.baseurl }}{% post_url 2018-11-14-Create-a-Blog-With-Github-Pages-Part1 %}) we setup a basic html page to be hosted using Github pages. Now we
will upgrade that basic page to have more blog functionality like blog posts,
RSS feed, landing page etc. We will use **Jekyll** to auto-generate most of this
for us.

## What is Jekyll?
[Jekyll](https://jekyllrb.com/) is a static site generator. It generates HTML
pages based on content written in Markdown syntax. It is intended as a blogging
platform and has the ability to auto-generate a static HTML site with whole
bunch of blog functionality. It can also be used to generate static sites that
are not blogs.

## Steps to setup blog
0. Ensure your machine has some basics pre-requisites to support installing Jekyll
```bash
gcc -v
ruby -v
```

1. Install Jekyll
```bash
sudo gem install bundler
sudo gem install github-pages
```

2. Remove the Hello World page
Remove the html page created in part 1 so we can replace it with something better
```bash
cd <github-username>.github.io
git rm index.html
git commit
git push
```

3. Use Jekyll to generate initial blog
In the <github-username>.github.io git repo directory:
```bash
jekyll new .
```

4. Serve this initial blog locally so we can preview it
In the <github-username>.github.io git repo directory:
```bash
jekyll serve
```
Note: See Troubleshooting section below if you have port clashing errors

5. Preview blog by opening `http://127.0.0.1:4000` in your browser.
If like me you needed to change the port used, then use whatever port you
 specified in the `_config.yml` file in the URL. Eg: `http://127.0.0.1:4400`

6. Customize blog content by editing `_config.yml`. I made the following changes to start with:
  * Updated the `url:` to https://swimmingbean.github.io
  * Updated the `description:`
  * Updated the `title:`
  * Updated the `github_username:`
  * Removed `email:` because I didnt want this posted on the blog
  * Removed `twitter:` because I didnt want this posted on the blog
  * Excerpt from my `_config.yml`
   ```yaml
# Site settings
# These are used to personalize your new site. If you look in the HTML files,
# you will see them accessed via {{ site.title }}, {{ site.email }}, and so on.
# You can create any custom variable you would like, and they will be accessible
# in the templates via {{ site.myvariable }}.
title: Swimming Bean
description: >- # this means to ignore newlines until "baseurl:"
  Swimming Bean Blog
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://swimmingbean.github.io" # the base hostname & protocol for your site, e.g. http://example.com
github_username:  swimmingbean
```
  ![SwimmingBean First Cut Blog]({{ site.baseurl }}/images/Create-a-Blog-With-Github-Pages-Part2/initial-blog-landing-page.png)

7. Make separate config files for dev and production. The main difference between these is the URL
```bash
cp _config.yml _config_dev.yml
```
Edit the `_config.yml` file and remove the `port: ` parameter if you added it and update the `url: ` parameter.
```yaml
baseurl: "" # the subpath of your site, e.g. /blog
url: "https://swimmingbean.github.io" # the base hostname & protocol for your site, e.g. http://example.com
```
Edit the URLs `_config_dev.yml` file
```yaml
baseurl: "" # the subpath of your site, e.g. /blog
url: "" # the base hostname & protocol for your site, e.g. http://example.com
port: 4400
```

8. Preview your blog using the dev configurations
   Restart Jekyll. Then navigate to `http://127.0.0.1:4400` in your web browser
```
jekyll serve --config _config_dev.yml
```
9. Push changes to GitHub
In the top level directory for your repo, eg: swimmingbean.github.io
```
git add .
git commit
git push
```

10. Check out your live in-production blog at `https://<github-username`.github.io/

## Troubleshooting
### Port already in use
Error message:
```bash
$ jekyll serve
Configuration file: /Users/mraj/dev/repos/swimmingbean.github.io/_config.yml
            Source: /Users/mraj/dev/repos/swimmingbean.github.io
       Destination: /Users/mraj/dev/repos/swimmingbean.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating...
       Jekyll Feed: Generating feed for posts
                    done in 0.604 seconds.
 Auto-regeneration: enabled for '/Users/mraj/dev/repos/swimmingbean.github.io'
jekyll 3.7.4 | Error:  Address already in use - bind(2) for 127.0.0.1:4000
```
Check to see what process is already using port 4000.
```bash
sudo lsof -nP -i4TCP:4000
```
You can either kill the process that is using port 4000 or change the Jekyll
configurations to use a different port.

Change the port by editing the `_config.yml` file and adding the following line.
```yaml
port: 4400
```

Re-try `jekyll serve` after you finish changing the port or making the original
 port (4000) available
