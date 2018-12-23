---
layout: post
title: Blog Asthetics v3
---

# v1
I started this blog with the minima theme that comes default with github pages.
Minima looks something like this:
![]({{ site.baseurl }}/images/blog-design-v3/minima-theme.png)

# v2
For the first customization I added a navigation sidebar and updated the fonts, font colors and background colors based on font combinations and color palettes put together by [Niki Ram](https://nikiworks.wordpress.com/author/nikiram95/).
![]({{ site.baseurl }}/images/blog-design-v3/niki-color-palettes.png)

![]({{ site.baseurl }}/images/blog-design-v3/v2-home-page.png)

![]({{ site.baseurl }}/images/blog-design-v3/v2-sample-post.png)

### What I like about this format
* The sidebar allows me the opportunity to a big solid block of color
* The blog title is good opportunity to add an accent color.
* I found a icons for bullet points and horizontal rule that match the yellow accent color

### What I dont like about this format
* The way that I kludged together the sidebar is not correctly responsive. Try changing the width of the browser window. In full monitor width screens it looks ok. In phone width screens the sidebar correctly disappears and becomes a top banner. In middle widths the sidebar overlaps with the main content window and obscures half the content. This needs to be fixed, if I decide to keep the sidebar

* More than 70% of the time content is viewed on a mobile device. In this screen width the sidebar is not constantly visible and no longer provides the same pop of color.

* The yellow bullets I'm using disappear into the background color

# v3 - What's next?
* Get rid of the sidebar in favor of header and footer navbars / nav links
* Find a different way to add color and style
  * One option is to place my post content on a card. In this case I have the background, card background and possibly a card shadow to play with in addition to font color.
  * I've poked around a few other blogs to see what other people are doing. One that stood out for me (as always :) ) is [Julia Evans' blog](https://jvns.ca/).
    * I like that her content is on a panel that doesn't fill the screen width. This allows her to use the background behind the panel as one source of color.
    * I also like the orange vertical ribbon. Unlike the page header this ribbon continues to be visible as you scroll down the page and is a source of color even as you scroll down. This ribbon shows up in all screen widths except the narrowest ones. Lastly I like that the ribbon is a pattern instead of a solid color. I think this adds a lot of subtle depth and interest.
* Spend more time coming up with color and format of elements within the post content such as:
  * code snippet boxes background color and syntax highlighting colors
  * tables: format, color of alternate row highlighting
  * icon used for bullet points
  * horizontal rule
* Experiment with a wide variety of color palettes and how the color palette is applied to various elements of the blog.
  * See [my next post]({{ site.baseurl }}{% post_url 2018-12-22-experiments-with-color-palettes %})
* Look at [different options]({{ site.baseurl }}{% post_url 2018-12-22-landing-page-ideas %}) for layout of the blog landing page.
