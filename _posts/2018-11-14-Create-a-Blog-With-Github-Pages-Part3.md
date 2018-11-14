# Create a Blog With GitHub Pages - Part 3

Add posts to the blog created in [Create a Blog With GitHub Pages - Part 2]({{ site.baseurl }}{% post_url 2018-11-14-Create-a-Blog-With-Github-Pages-Part2 %})

1. First I’m going to remove the initial boilerplate post created by Jekyll
```
git rm _posts/2018-11-14-welcome-to-jekyll.markdown
git commit
```

2. Create first post
   See also: [Jekyll documentation on creating posts](https://jekyllrb.com/docs/posts/)
   ```
   mkdir _posts
   echo "My first post" > _posts/2018-11-14-Create-a-Blog-With-Github-Pages-Part1.md
   git add _posts
   git commit
   git push
   ```

3. Edit post contents by editing the file you just created in the _posts directory
   I'm trying out [Atom](https://atom.io/) as a markdown editor.
