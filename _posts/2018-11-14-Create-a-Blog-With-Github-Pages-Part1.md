# STEP 1 - Create a user page in GitHub

In the spirit of incremental improvements, we'll start with creating a simple
"Hello World" page hosted using github pages

1. Create GitHub repo with the following name: `<github-username>.github.io`
2. Clone the repo to your local machine
```
git clone https://github.com/<github-username>/<github-username>.github.io.git
cd <github-username>.github.io
```
3. Create an html file with initial contents for you site
```
echo “Hello World” > index.html
```
4. Commit and push your file to GitHub
```
git add index.html
git commit
git push
```
5. Visit `https://<github-username>.github.io` using your web browser to check out your new site.
Here is what the initial SwimmingBean page looked like
![Initially SwimmingBean user page]({{ site.baseurl }}/images/initial-hello-world-github-user-page.png)
